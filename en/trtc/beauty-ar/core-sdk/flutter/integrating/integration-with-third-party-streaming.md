# Integration With Third-party Streaming

Because the Flutter OpenGL environment is isolated from a native environment, you cannot integrate the BeautyAR SDK directly into Flutter. You need to establish connections between them at the native side.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b6bcc3f1bf1e11ee8c36525400bb593a.png)

## How It Works

1. Create an API abstraction layer and implement the API at the BeautyAR SDK side.
2. When the application is launched, register the API with the third-party publisher so that the third-party publisher can use it to create, use, and terminate an effect instance.
3. The third-party publisher exposes the capabilities of creating and terminating effect instances to the Flutter side.
4. Use the BeautyAR Flutter SDK to configure effects.

### Android

#### Example (TRTC)

BeautyAR SDK API:

```
public interface ITXCustomBeautyProcesserFactory {    /**     * Create an instance     * @return     */    ITXCustomBeautyProcesser createCustomBeautyProcesser();    /**     * Terminate an instance (this API must be called in the OpenGL thread)     */    void destroyCustomBeautyProcesser();}public interface ITXCustomBeautyProcesser {   // Get the pixel formats supported for video frames. Tencent Effect supports OpenGL 2D textures.    TXCustomBeautyPixelFormat getSupportedPixelFormat();    // Get the container formats supported for video frames. Tencent Effect supports V2TXLiveBufferTypeTexture, which delivers the best performance and has the smallest impact on video quality.    TXCustomBeautyBufferType getSupportedBufferType();   // Call this API in the OpenGL thread (`srcFrame` must include RGBA textures and the width and height). After processing, the texture object will be included in `texture.textureId` of `dstFrame`.    void onProcessVideoFrame(TXCustomBeautyVideoFrame srcFrame, TXCustomBeautyVideoFrame dstFrame);}
```

1. TRTC offers a registration method. When the application is launched, register `com.tencent.effect.tencent_effect_flutter.XmagicProcesserFactory`, the implementation class of `ITXCustomBeautyProcesserFactory` with TRTC (at the native side).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b6aff8bebf1e11ee9976525400c26da5.png)

2. At the `Flutter` layer, provide `Future<V2TXLiveCode> enableCustomVideoProcess(bool enable)`, which is used to enable or disable custom effects.
3. Enable or disable effects at the TRTC native side.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b6d394eabf1e11ee9976525400c26da5.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b6b7c2b2bf1e11ee9000525400461a83.png)

#### Appendix

**The abstraction layer dependency provided by BeautyAR**

```
///implementation 'com.tencent.liteav:custom-video-processor:latest.release'
```

### **iOS**

BeautyAR SDK APIï¼

```
@objc public protocol ITXCustomBeautyProcesserFactory {    /// Create a beauty effect instance    func createCustomBeautyProcesser() -> ITXCustomBeautyProcesser    /// Terminate a beauty effect instance    func destroyCustomBeautyProcesser()}@objc public protocol ITXCustomBeautyProcesser {    /// Get third-party beauty feature PixelFormat    func getSupportedPixelFormat() -> ITXCustomBeautyPixelFormat    /// Get third-party beauty feature BufferType    func getSupportedBufferType() -> ITXCustomBeautyBufferType    /// Callback for NativeSDK video custom processing    /// - Returns: Returns the video frame object processed by the third-party beauty feature SDK    func onProcessVideoFrame(srcFrame: ITXCustomBeautyVideoFrame, dstFrame: ITXCustomBeautyVideoFrame) -> ITXCustomBeautyVideoFrame}
```

1. TRTC provides a method of registration. During application startup, the implementation class `com.tencent.effect.tencent_effect_flutter.XmagicProcesserFactory` of the beauty effect ITXCustomBeautyProcesserFactory API needs to be registered into TRTC (perform on the native end).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8c8e9919c5011f0930a5254007c27c5.png)

2. At the `Flutter` layer, the `Future<V2TXLiveCode> enableCustomVideoProcess(bool enable)` API is provided to enable or disable the custom beauty interface.
3. TRTC implements the beauty effect toggle method on the native end.

```
/// Enable/disable custom video processing.    @objc    func enableCustomVideoProcess(call: FlutterMethodCall, result: @escaping FlutterResult) {        let key = "enable"        guard let enable = MethodUtils.getMethodParams(call: call, key: key, resultType: NSNumber.self)?.boolValue else {            FlutterResultUtils.handleMethod(code: .paramNotFound, methodName: call.method, paramKey: key, result: result)            return        }        guard let customBeautyInstance = TXLivePluginManager.getBeautyInstance() else {            FlutterResultUtils.handleMethod(code: .valueIsNull, methodName: call.method, paramKey: key, result: result)            return        }        customBeautyQueue.async { [weak self] in            guard let `self` = self else {                FlutterResultUtils.handleMethod(code: .valueIsNull, methodName: call.method, paramKey: key, result: result)                return            }            if (enable && self.beautyInstance == nil) {                self.beautyInstance = customBeautyInstance.createCustomBeautyProcesser()            }            guard let beautyInstance = self.beautyInstance else {                FlutterResultUtils.handleMethod(code: .valueIsNull, methodName: call.method, paramKey: key, result: result)                return            }            let pixelFormat = beautyInstance.getSupportedPixelFormat()            let bufferType = beautyInstance.getSupportedBufferType()            let v2PixelFormat = ConvertBeautyFrame.convertToV2LivePixelFormat(beautyPixelFormat: pixelFormat)            let v2BufferType = ConvertBeautyFrame.convertToV2LiveBufferType(beautyBufferType: bufferType)            let code = self.pusher.enableCustomVideoProcess(enable,                                                            pixelFormat:v2PixelFormat,                                                            bufferType:v2BufferType)            DispatchQueue.main.async {                result(NSNumber(value: code.rawValue))            }        }    }
```

```
public static func convertToV2LivePixelFormat(beautyPixelFormat: ITXCustomBeautyPixelFormat) -> V2TXLivePixelFormat {        switch beautyPixelFormat {        case .Unknown:            return .unknown        case .I420:            return .I420        case .Texture2D:            return .texture2D        case .BGRA:            return .BGRA32        case .NV12:            return .NV12        }    }public static func convertToV2LiveBufferType(beautyBufferType: ITXCustomBeautyBufferType) -> V2TXLiveBufferType {        switch beautyBufferType {        case .Unknown:            return .unknown        case .PixelBuffer:            return .pixelBuffer        case .Data:            return .nsData        case .Texture:            return .texture        }    }
```

#### Appendix

**The beauty effect's abstraction layer depends.**

```
///s.dependency 'TXCustomBeautyProcesserPlugin','1.0.2'
```


---
*Source: [https://trtc.io/document/60192](https://trtc.io/document/60192)*
