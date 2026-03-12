# API Document

XMagic.h, the core interface class of the Tencent Effect SDK, is used to initialize the SDK, update the beautification value, call the animation effect and other functions.

## Static method

| API | Description |
| --- | --- |
| version | The SDK version number |
| [getDeviceLevel](#1e1ecd0f-0767-442a-aeb1-fb988e39fd84) | Get the device level. Added in V3.7.0. You can [enable or disable relevant SDK features](https://www.tencentcloud.com/document/product/1143/60202#setFeatureEnableDisable) based on the device level, or [set high-performance mode](https://www.tencentcloud.com/document/product/1143/73786) on lower-level devices. |

## Instance method

| API | Description |
| --- | --- |
| [initWithRenderSize](#initwithrendersize) | Initialization API |
| [initWithGlTexture](#initwithgltexture) | Initialization API |
| [setEffect](#setEffect) | Configuration of various beauty filter effects (Added in 3.5.0.2) |
| [emitBlurStrengthEvent](#emitblurstrengthevent) | Setting post-processing blur strength (Applies to all blur components) |
| [setRenderSize](#setrendersize) | Sets the render size. |
| [deinit](#deinit) | Releases resources. |
| [process:](https://www.tencentcloud.com/document/product/1143/60202#process) | Image data processing interface: inputs image before beautification, returns image after beautification. |
| [process:withOrigin:withOrientation:](#process:withOrigin:withOrientation:) | Image data processing interface: inputs image before beautification, returns image after beautification. This interface has two additional parameters compared to the previous one. |
| [exportCurrentTexture](https://www.tencentcloud.com/document/product/1143/60202#3649a4a0-5955-4625-8283-23167f6e2aa7) | Export the current image. After processing the beauty effects using the interfaces process and process:withOrigin:withOrientation:, you can use this interface to obtain the current image. |
| [processUIImage](#processuiimage) | Processes an image. |
| [getConfigPropertyWithName](#getconfigpropertywithname) | Gets effect information. |
| [registerLoggerListener](#registerloggerlistener) | Registers a log listener. |
| [registerSDKEventListener](#registersdkeventlistener) | Register a listener for SDK events. |
| [clearListeners](#clearlisteners) | Removes listeners. |
| [getCurrentGlContext](#getcurrentglcontext) | Gets the current OpenGL context. |
| [onPause](#onpause) | Pauses the SDK. |
| [onResume](#onresume) | Resumes the SDK. |
|  [setAudioMute](#setAudioMute) | Whether to turn on mute when the dynamic effect material is used (new in V2.5.0)Parameters: YES means mute, NO means no mute |
| [setFeatureEnableDisable](#setFeatureEnableDisable) | Set the enablement or disablement of a specific feature. |
| [setSyncMode](https://www.tencentcloud.com/document/product/1143/60202#4f214122-0081-4831-9336-5d067338b905) | Set up synchronized video frame processing. |
| [Overlaying of materials](https://www.tencentcloud.com/document/product/1143/60202#Materialoverlay) | If you want to overlay a certain animation/beauty/segmentation material on the current material, when setting up the material, set 'mergeWithCurrentMotion' to true in the dictionary of 'withExtraInfo' |
| EffectMode | Refer to the [EffectMode](https://www.tencentcloud.com/document/product/1143/73786). |

### getDeviceLevel

Added in V3.7.0. You can [enable or disable relevant SDK features](https://www.tencentcloud.com/document/product/1143/60202#setFeatureEnableDisable) based on the device level, or [set high-performance mode](https://www.tencentcloud.com/document/product/1143/73786) on lower-level devices.

```
typedef NS_ENUM(NSInteger, DeviceLevel) {    DEVICE_LEVEL_VERY_LOW = 1,    DEVICE_LEVEL_LOW = 2,    DEVICE_LEVEL_MIDDLE = 3,    DEVICE_LEVEL_MIDDLE_HIGH = 4,    DEVICE_LEVEL_HIGH = 5};+ (DeviceLevel)getDeviceLevel;
```

### initWithRenderSize

This API is used to configure effects.

```
- (instancetype _Nonnull)initWithRenderSize:(CGSize)renderSize                        assetsDict:(NSDictionary* _Nullable)assetsDict;
```

Parameters

| Parameter | Description |
| --- | --- |
| renderSize | The render size. |
| assetsDict | The resource dictionary. |

### initWithGlTexture

This API is used to configure effects.

```
- (instancetype _Nonnull)initWithGlTexture:(unsigned)textureID                        width:(int)width                        height:(int)height                        flipY:(bool)flipY                        assetsDict:(NSDictionary* _Nullable)assetsDict;
```

**Parameters**

| Parameter | Description |
| --- | --- |
| textureID | The texture ID. |
| width | The render size. |
| height | The render size. |
| flipY | Whether to flip the image. |
| assetsDict | The resource dictionary. |

### setEffect (Added in 3.5.0.2)

For the configuration of various beauty effects, see [Effect Parameters](https://www.tencentcloud.com/document/product/1143/60207) for specific usage examples.

```
- (void)setEffect:(NSString * _Nullable)effectName      effectValue:(int)effectValue     resourcePath:(NSString * _Nullable)resourcePath        extraInfo:(NSDictionary * _Nullable)extraInfo;
```

**Parameter**

| Parameter | Meaning |
| --- | --- |
| effectName | Effect type. |
| effectValue | Effect value. |
| resourcePath | Material path. |
| extraInfo | Reserved for expansion and additional configuration. |

### emitBlurStrengthEvent

Setting post-processing blur intensity (which applies to all blur components).

```
- (void)emitBlurStrengthEvent:(int)strength;
```

**Parameter**

| Parameter | Meaning |
| --- | --- |
| strength | Effect value. |

### setRenderSize

This API is used to set the render size.

```
- (void)setRenderSize:(CGSize)size;
```

**Parameters**

| Parameter | Description |
| --- | --- |
| size | The render size. |

### deinit

This API is used to release resources.

```
- (void)deinit;
```

### process

Processing data interface, the input data formats include `YTImagePixelData,YTTextureData,YTImageRawData,YTUIImageData`, outputting the corresponding data formats. The pixel format in `YTImagePixelData` is `RGBA`, and the texture format in `YTTextureData` is `OpenGL 2D`.

```
/// @brief Process input 4 choose 1@interface YTProcessInput : NSObject/// Camera data object@property (nonatomic, strong) YTImagePixelData * _Nullable pixelData;/// Texture object@property (nonatomic, strong) YTTextureData * _Nullable textureData;/// Raw data object@property (nonatomic, strong) YTImageRawData * _Nullable rawData;/// UIImage object@property (nonatomic, strong) YTUIImageData * _Nullable UIImageData;/// Input data type@property (nonatomic) enum YTProcessDataType dataType;@end/// @brief Process output@interface YTProcessOutput : NSObject/// Texture output object (always guaranteed)@property (nonatomic, strong) YTTextureData * _Nullable textureData;/// Camera output object (if the input is camera acquisition data)@property (nonatomic, strong) YTImagePixelData * _Nullable pixelData;/// Raw output object (if the input is raw data)@property (nonatomic, strong) YTImageRawData * _Nullable rawData;/// UIImage output object (if the input is a UIImage object)@property (nonatomic, strong) YTUIImageData * _Nullable UIImageData;/// Output data type@property (nonatomic) enum YTProcessDataType dataType;@end- (YTProcessOutput* _Nonnull)process:(YTProcessInput * _Nonnull)input;
```

**Parameter**

| Parameter | Meaning |
| --- | --- |
| input | Input data processing information, one of four input formats can be chosen from (YTImagePixelData, YTTextureData, YTImageRawData, YTUIImageData). |

#### YTProcessInput Input data types and descriptions

When invoking the [process](https://www.tencentcloud.com/document/product/1143/60202#process) interface, the output data type matches the input data type, YTTextureData type is always output.

| Type | Meaning |
| --- | --- |
| YTImagePixelData | Camera data object, with the pixel format, is RGBA. |
| YTTextureData | Texture object, with the texture format, is OpenGL 2D. |
| YTImageRawData | Raw data object. |
| YTUIImageData | UIImage object. |

### process:withOrigin:withOrientation:

Data processing interface. The input and output data formats match [process](https://www.tencentcloud.com/document/product/1143/60202#process). withOrigin: Setting whether to flip the image vertically. withOrientation: Setting the image rotation direction.

```
- (YTProcessOutput* _Nonnull)process:(YTProcessInput* _Nonnull)input withOrigin:(YtLightImageOrigin)origin withOrientation:(YtLightDeviceCameraOrientation)orientation;
```

**Parameter**

| Parameter | Meaning |
| --- | --- |
| input | Input data processing information. |
| withOrigin | Enumeration value (YtLightImageOriginTopLeft and YtLightImageOriginBottomLeft), when set to YtLightImageOriginBottomLeft, the image is flipped vertically. |
| withOrientation | Enumeration value: Image rotation angle, setting the angle will change the output image angle. |

### exportCurrentTexture

Export the current image. After processing the beauty effects using the interfaces process and process:withOrigin:withOrientation: you can use this interface to obtain the current image.

```
/// Export a picture of the current image- (void)exportCurrentTexture:(nullable void (^)(UIImage *_Nullable image))callback;
```

### TEImageTransform tool class

Image Process tool class, input/output data formats include CVPixelBufferref and texture id. It supports mutually converting CVPixelBufferref data's bgra<-->yuv format, rotation, and vertical/horizontal mirroring. It also supports rotation and vertical/horizontal mirroring of the input in texture id format.

```
/// @param context If you are using the OpenGL interface of this class, we recommend using this method to initialize. You can pass [xMgiac getCurrentGlContext].- (instancetype)initWithEAGLContext:(EAGLContext *)context;
```

| Parameter | Meaning |
| --- | --- |
| context | Using the context environment of OpenGLES, you can pass [xMagic getCurrentGlContext]. |

```
/// @brief CVPixelBufferRef yuv/rgb interconversion interface, currently, only supports converting the three types within TEPixelFormatType. CVPixelBufferRef yuv/rgb transfor interface/// @param pixelBuffer Input pixelBuffer     input pixelBuffer/// @param outputFormat Specify the type of output pixelBuffer    output pixelBuffer format- (CVPixelBufferRef)transformCVPixelBufferToBuffer:(CVPixelBufferRef)pixelBuffer outputFormat:(TEPixelFormatType)outputFormat;
```

| Parameter | Meaning |
| --- | --- |
| pixelBuffer | Input pixelBuffer data |
| outputFormat | Output pixelBuffer format, supports BGRA, NV12F(kCVPixelFormatType_420YpCbCr8BiPlanarFullRange), and NV12V(kCVPixelFormatType_420YpCbCr8BiPlanarVideoRange). |

```
/// Convert yuv/rgb pixelBuffer to bgra format texture id/// @param pixelBuffer Input pixelBuffer- (GLuint)transformPixelBufferToBGRATexture:(CVPixelBufferRef)pixelBuffer;
```

| Parameter | Meaning |
| --- | --- |
| pixelBuffer | Input pixelBuffer data, supports BGRA, NV12F(kCVPixelFormatType_420YpCbCr8BiPlanarFullRange), and NV12V(kCVPixelFormatType_420YpCbCr8BiPlanarVideoRange). |

```
/// Rotate the CVPixelBufferRef and flip it. If you pass rotation and flipping at the same time, the processing logic is to mirror first and then rotate.- (CVPixelBufferRef)convertCVPixelBuffer:(CVPixelBufferRef)pixelBuffer rotaion:(YtLightDeviceCameraOrientation)rotation flip:(TEFlipType)flipType;
```

| Parameter | Meaning |
| --- | --- |
| pixelBuffer | Input pixelBuffer data |
| rotation | The counterclockwise rotation angle, supports 0 degree, 90 degrees, 180 degrees, and 270 degrees. |
| flipType | Mirror type, horizontal mirroring, or vertical mirroring. If both rotation and flipping are passed, the processing logic is to mirror first and then rotate. |

```
/// Rotate/flip the texture Id, if both rotation and flipping are passed, the processing logic is to mirror first and then rotate.- (GLuint)convert:(GLuint)srcId width:(int)width height:(int)height rotaion:(YtLightDeviceCameraOrientation)rotation flip:(TEFlipType)flipType;
```

| Parameter | Meaning |
| --- | --- |
| srcId | Input Texture ID. |
| width | Texture width. |
| height | Texture height. |
| rotation | The Counterclockwise rotation angle, supports 0 degree, 90 degrees, 180 degrees, and 270 degrees. |
| flipType | Mirror type, horizontal mirroring, or vertical mirroring. If both rotation and flipping are passed, the processing logic is to mirror first and then rotate. |

### processUIImage

This API is used to process an image.

```
- (UIImage* _Nullable)processUIImage:(UIImage* _Nonnull)inputImage needReset:(bool)needReset;
```

**Parameters**

| Parameter | Description |
| --- | --- |
| inputImage | The input image. If your image is larger than 2160 x 4096, we recommend you reduce its size before passing it in; otherwise, face recognition may fail or may be inaccurate. It may also cause an OOM error. |
| needReset | This parameter must be set to true in the following cases:The image processed is changedThe first time a keying effect is usedThe first time an animated effect is usedThe first time a makeup effect is used |

### getConfigPropertyWithName

This API is used to get effect information.

```
- (YTBeautyPropertyInfo * _Nullable)getConfigPropertyWithName:(NSString *_Nonnull)propertyName;
```

Parameters

| Parameter | Description |
| --- | --- |
| propertyName | The effect name. |

### registerLoggerListener

This API is used to register a log listener.

```
- (void)registerLoggerListener:(id<YTSDKLogListener> _Nullable)listener withDefaultLevel:(YtSDKLoggerLevel)level;
```

**Parameters**

| Parameter | Description |
| --- | --- |
| listener | The log callback. |
| level | The log output level, which is ERROR by default. |

### registerSDKEventListener

This API is used to register a listener for SDK events.

```
- (void)registerSDKEventListener:(id<YTSDKEventListener> _Nullable)listener;
```

**Parameters**

| Parameter | Description |
| --- | --- |
| listener | The listener for SDK events, including AI events, tips, and resource events. |

### clearListeners

This API is used to remove listeners.

```
- (void)clearListeners;
```

### getCurrentGlContext

This API is used to get the current OpenGL context.

```
- (nullable EAGLContext*)getCurrentGlContext;
```

### onPause

This API is used to pause the SDK.

```
/// @brief When your app is switched to the background, you need to call this API to pause the SDK- (void)onPause;
```

### onResume

This API is used to resume the SDK.

```
/// @brief When your app is switched back to the foreground, you need to call this API to resume the SDK- (void)onResume;
```

### setAudioMute

Whether to turn on mute when the dynamic effect material is used (new in V2.5.0)

```
/// @brief set mute- (void)setAudioMute:(BOOL)isMute;
```

### setFeatureEnableDisable

Set the enablement or disablement of a specific feature.

```
/// @brief Set a feature on or off/// @param featureName TEDefine FeatureName/// @param enable on or off- (void)setFeatureEnableDisable:(NSString *_Nonnull)featureName enable:(BOOL)enable;
```

**Parameters**

| Parameter | Description |
| --- | --- |
| featureName | Name of the atomic capabilityValid values:`XmagicConstant.FeatureName.SEGMENTATION_SKIN` Skin Segmentation Capability, after enabling, can make the skin smoothing and whitening areas more accurate.`XmagicConstant.FeatureName.SEGMENTATION_FACE_BLOCK` Face Occlusion Detection Capability, after enabling, can avoid makeup being applied to occluded areas.`XmagicConstant.FeatureName.WHITEN_ONLY_SKIN_AREA ` Whitening only works on skin`XmagicConstant.FeatureName.SMART_BEAUTY` Intelligent Beauty (reduces beauty and makeup effects for men and babies)`XmagicConstant.FeatureName.ANIMOJI_52_EXPRESSION` Face Expression Capability`XmagicConstant.FeatureName.BODY_3D_POINT` Body Point Capability`XmagicConstant.FeatureName.HAND_DETECT` Gesture Detection Capability |
| enable | true indicates to enable this capability, false indicates to disable this capability |

### setSyncMode

Some recognition and rendering logic inside the SDK is processed asynchronously. By calling this interface, you can make the SDK process the input images synchronously for the next `syncFrameCount` frames to meet specific requirements in certain scenarios. For example, before processing the first frame, calling this interface allows the SDK to process several frames synchronously, which can prevent unfiltered images from being displayed. However, this may increase the black screen duration before the first frame is rendered, so please use it as needed.

```
- (void)setSyncMode:(BOOL)isSync syncFrameCount:(int)syncFrameCount;
```

| Parameter | Meaning |
| --- | --- |
| isSync | Whether to process image frames synchronously. |
| syncFrameCount | The number of frames to be processed synchronously. The value must be >= 0. If set to -1, it indicates an unlimited number of frames. |

## Callback

| API | Description |
| --- | --- |
| [YTSDKEventListener](https://www.tencentcloud.com/document/product/1143/60202#ytsdkeventlistener) | The SDK event callback. |
| [YTSDKLogListener](https://www.tencentcloud.com/document/product/1143/60202#ytsdkloglistener) | The log callback. |

### YTSDKEventListener

The callback for the internal events of the SDK.

```
@protocol YTSDKEventListener <NSObject>
```

Member callback APIs

| Return Type | Callback |
| --- | --- |
| void | [onAIEvent](#onaievent) |
| void | [onTipsEvent](#ontipsevent) |
| void | [onAssetEvent](#onassetevent) |

#### Callback description

##### onAIEvent

The YTDataUpdate event callback.

```
/// @param event Callback in dict format- (void)onAIEvent:(id _Nonnull)event;
```

The information of up to five faces is returned as JSON strings.

```
{ "face_info":[{  "trace_id":5,  "face_256_point":[    180.0,    112.2,    ...  ],  "face_256_visible":[    0.85,    ...  ],  "out_of_screen":true,  "left_eye_high_vis_ratio":1.0,  "right_eye_high_vis_ratio":1.0,  "left_eyebrow_high_vis_ratio":1.0,  "right_eyebrow_high_vis_ratio":1.0,  "mouth_high_vis_ratio":1.0 }, ... ]}
```

**Field Description**

| Field | Type | Value Range | Remarks |
| --- | --- | --- | --- |
| trace_id | int | [1,INF) | The face ID. If the faces obtained continuously from a video stream have the same face ID, they belong to the same person. |
| face_256_point | float | [0,screenWidth] or [0,screenHeight] | 512 values in total for 256 facial keypoints. (0,0) is the top-left corner of the screen. |
| face_256_visible | float | [0,1] | The visibility of the 256 facial keypoints. |
| out_of_screen | bool | true/false | Whether only part of the face is captured. |
| left_eye_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the left eye. |
| right_eye_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the right eye. |
| left_eyebrow_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the left eyebrow. |
| right_eyebrow_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the right eyebrow. |
| mouth_high_vis_ratio | float | [0,1] | The percentage of keypoints with high visibility for the mouth. |

#### onAIEvent

The callback for AI events.

```
/// @param event: Callback in dict format- (void)onAIEvent:(id _Nonnull)event;
```

##### onTipsEvent

The callback for tips.

```
/// @param event: Callback in dict format- (void)onTipsEvent:(id _Nonnull)event;
```

##### onAssetEvent

The callback for resource events.

```
/// @param event: Callback in string format- (void)onAssetEvent:(id _Nonnull)event;
```

### YTSDKLogListener

The log callback.

```
@protocol YTSDKLogListener <NSObject>
```

#### Member callback APIs

| Return Type | API |
| --- | --- |
| void | onLog |

#### Callback description

##### onLog

The log callback.

```
/// @param loggerLevel: The current log level./// @param logInfo: The log information.- (void)onLog:(YtSDKLoggerLevel) loggerLevel withInfo:(NSString * _Nonnull) logInfo;
```

### Material overlay (added in version 3.0.1.5)

If you want to overlay a certain animation/beauty/segmentation material on the current material, when setting up the material, set 'mergeWithCurrentMotion' to true in the dictionary of 'withExtraInfo', An example is shown below:

```
NSString *key = _xmagicUIProperty.property.Id;NSString *value = [[NSBundle mainBundle] pathForResource:@"makeupMotionRes" ofType:@"bundle"];NSDictionary* extraInfo = @{@"mergeWithCurrentMotion":@(true)}; [self.beautyKitRef configPropertyWithType:@"motion" withName:key withData:[NSString stringWithFormat:@"%@",value] withExtraInfo:extraInfo];
```

> **The precautions for material overlay are:**The client needs to manage whether the materials are suitable for overlaying. Here are two examples:Example 1: Effect A is to turn into a noblewoman's face, and effect B is to turn into a fairytale face. Overlaying these two effects may      result in a very awkward image.Example 2: Effect A is a pair of rabbit ears, and effect B is a pair of pig ears. Overlaying these two effects will result in two types of ears.These two cases are not suitable for overlaying. If effect A is a pair of rabbit ears and effect B is blowing a kiss, these two effects will not conflict and are suitable for overlaying.Only simple materials can be overlaid. Simple materials refer to those with only one animation effect, makeup effect, or background removal effect, while complex materials refer to those that contain multiple effects. There is no clear boundary between simple and complex materials, so it is recommended that clients fully test and manage which materials can be overlaid and which cannot.When overlaying, effects triggered by actions (such as triggering an effect by reaching out or smiling) are complex effects and need to be placed in front, with simple effects overlaid on top.Usage example: The anchor uses effect A, and then the audience sends gift effect B, which needs to be overlaid on A. After a period of time, B disappears and returns to effect A. The settings are as follows:4.1. Set effect A, and set mergeWithCurrentMotion to false.4.2. Set effect B, and set mergeWithCurrentMotion to true.4.3. After a short period of time, set A again, and set mergeWithCurrentMotion to false.

## Deprecated method

| API | Description |
| --- | --- |
| [configPropertyWithType](#configpropertywithtype) | Configure various beauty effects. Deprecated, it is recommended to use setEffect. |
| [High performance mode](#High-performance-mode) | Deprecated, it is recommended to [EffectMode (High-Performance Mode) Usage Guide](https://www.tencentcloud.com/document/product/1143/73786). |
| [enableEnhancedMode](#enableEnhancedMode) | Deprecated, it is recommended to [Enhanced Mode User Guide](https://www.tencentcloud.com/document/product/1143/73785). |
| [isBeautyAuthorized](#isBeautyAuthorized) | This API is used to get the authorization information of the effect parameter |

### configPropertyWithType

This API is used to configure effects.Deprecated, it is recommended to use setEffect.

```
- (int)configPropertyWithType:(NSString *_Nonnull)propertyType withName:(NSString *_Nonnull)propertyName withData:(NSString*_Nonnull)propertyValue withExtraInfo:(id _Nullable)extraInfo;
```

**Parameters**

| Parameter | Description |
| --- | --- |
| propertyType | The effect type. |
| propertyName | The effect name. |
| propertyValue | The effect value. |
| extraInfo | A reserved parameter, which can be used for dictionary configuration. |

**Examples**

- **Beautification**: Configuring the skin brightening effect

```
NSString *propertyType = @"beauty";        //Set the effect type, take beauty as an example.NSString *propertyName = @"beauty.whiten"; //Specify the effect name, take the skin brightening effect as an example.NSString *propertyValue = @"60";           //Set the effect value.[self.xmagicApi configPropertyWithType:propertyType withName:propertyName withData:propertyValue withExtraInfo:nil];traInfo:nil];
```

- **Filter**: Configuring the Allure filter

```
NSString *propertyType = @"lut";        //Set the effect type, take filter as an example.NSString *propertyName = [@"lut.bundle/" stringByAppendingPathComponent:@"xindong_lf.png"]; //Specify the effect name, take the Allure filter as an example.NSString *propertyValue = @"60";           //Set the effect value.[self.xmagicApi configPropertyWithType:propertyType withName:propertyName withData:propertyValue withExtraInfo:nil];
```

- **Body retouch**: Configuring the long leg effect

```
NSString *propertyType = @"body";        //Set the effect type, take body retouch as an example.NSString *propertyName = @"body.legStretch"; //Specify the effect name, take the long leg effect as an example.NSString *propertyValue = @"60";           //Set the effect value.[self.xmagicApi configPropertyWithType:propertyType withName:propertyName withData:propertyValue withExtraInfo:nil];
```

- **Animated effect**: Configuring the animated 2D cute effect

```
 NSString *motion2dResPath = [[NSBundle mainBundle] pathForResource:@"2dMotionRes" ofType:@"bundle"];//The absolute path of the `2dMotionRes` folderNSString *propertyType = @"motion";        //Set the effect type, take animated effect as an example.NSString *propertyName = @"video_keaituya"; //Specify the effect name, take animated 2D cute effect as an example.NSString *propertyValue = motion2dResPath;  //Set the path of the animated effect.[self.xmagicApi configPropertyWithType:propertyType withName:propertyName withData:propertyValue withExtraInfo:nil];
```

- **Makeup**: Configuring the girl group makeup effect

```
NSString *motionMakeupResPath = [[NSBundle mainBundle] pathForResource:@"makeupMotionRes" ofType:@"bundle"];//The absolute path of the `makeupMotionRes` folderNSString *propertyType = @"motion";        //Set the effect type, take makeup as an example.NSString *propertyName = @"video_nvtuanzhuang"; //Specify the effect name, take the girl group makeup effect as an example.NSString *propertyValue = motionMakeupResPath;  //Set the path of the animated effect.[self.xmagicApi configPropertyWithType:propertyType withName:propertyName withData:propertyValue withExtraInfo:nil];//Below are settings for the makeup effect (you only need to configure the above parameters once and can change the following settings multiple times).NSString *propertyTypeMakeup = @"custom";         //Set the effect type, take makeup as an example.NSString *propertyNameMakeup = @"makeup.strength"; //Specify the effect name, take the girl group makeup effect as an example.NSString *propertyValueMakeup = @"60";             //Set the effect value.[self.xmagicApi configPropertyWithType:propertyTypeMakeup withName:propertyNameMakeup withData:propertyValueMakeup withExtraInfo:nil];
```

- **Keying**: Configuring the background blurring effect (strong)

```
segmentMotionRes
```

- **Custom background**:

```
NSString *motionSegResPath = [[NSBundle mainBundle] pathForResource:@"segmentMotionRes" ofType:@"bundle"];//The absolute path of the `segmentMotionRes` folderNSString *propertyType = @"motion";         //Set the effect type, take keying as an exampleNSString *propertyName = @"video_empty_segmentation"; //Specify the effect name, take custom background as an exampleNSString *propertyValue = motionSegResPath;  //Set the path of the animated effectNSString *imagePath = @"/var/mobile/Containers/Data/Application/06B00BBC-9060-450F-8D3A-F6028D185682/Documents/MediaFile/image.png"; //The absolute path of the background image or video (after compression).int bgType = 0;//The background type. 0: image; 1: video.int timeOffset = 0;//The duration. If an image is used as the background, its value is 0; if a video is used, its value is the video length.NSDictionary *dic = @{@"bgName":imagePath, @"bgType":@(bgType), @"timeOffset": @(timeOffset)},@"icon":@"segmentation.linjian.png"};//Configure the reserved parameter.[self.xmagicApi configPropertyWithType:propertyType withName:propertyName withData:propertyValue withExtraInfo:dic];
```

### High performance modeï¼V3.1.0.1ï¼

With high performance mode enabled, the beauty feature will consume less system CPU/GPU resources, reducing overheating and lagging on the phone, making it more suitable for long-term use on low-end devices.

**Note that the following beauty options will be unavailable when high performance mode is enabled:**

- Eye: Eye width, Eye height, Eye bags.
- Eyebrow: Eyebrow angle, Eyebrow distance, Eyebrow Height, Eyebrow Length, Eyebrow Thickness, Eyebrow ridge.
- Mouth: Smile face.
- Facial: Thin face (Natural, Woman, Man), Slim jaw, Wrinkles, Smile lines. It is recommended to use Face shape to achieve a comprehensive effect of big eyes and thin "face".

```
NSDictionary *assetsDict = @{@"core_name":@"LightCore.bundle",                             @"root_path":[[NSBundle mainBundle] bundlePath],                             @"setDowngradePerformance":@(YES) //Enable high performance mode.    };    self.beautyKit = [[XMagic alloc] initWithRenderSize:previewSize assetsDict:assetsDict];
```

### enableEnhancedMode

```
/// @brief Activate the beautification enhancing pattern- (void)enableEnhancedMode;
```

Enable enhanced beauty filter pattern (Added in V2.5.1). By default, it is not activated.

- When it's disabled, the application layer can set the intensity range of each beauty option from 0 to 1 or -1 to 1. If it exceeds this range, the SDK will take the boundary value. For example, if the application layer sets the face-slimming component to 1.2, SDK will limit it to the maximum value of 1.0, then it corrects the face-slimming value to 1.0 internally.
- After enabling the enhanced pattern, the application layer can set a larger range of values. For example, if you want greater face slimming, you can set the face slimming value to 1.2. The SDK will accept and use this value and will not correct it to 1.0.

After enabling the enhanced pattern, the application layer needs to manage the maximum value that each beauty item can set, and let users adjust the value within this range. We provide a set of reference values, which you can adjust according to product requirements. However, we do not recommend exceeding our recommended values, otherwise the beauty effect may worsen. See the reference values below:

| Beauty Item Name | In enhanced pattern, recommended maximum value (magnification factor) |
| --- | --- |
| Whitening, shortening the face, V-face, eye distance, nose position, removal of laugh lines, lipstick, three-dimensional appearance | 1.3 |
| Eye lightening | 1.5 |
| Blush | 1.8 |
| Other | 1.2 |
|  |  |
|  |  |
|  |  |

### isBeautyAuthorized

This API is used to get the authorization information of the effect parameter (only supports the parameter of beauty and body retouch).

```
/// @param featureId: The effect parameter./// @return: The authorization information of the effect parameter.+ (BOOL)isBeautyAuthorized:(NSString * _Nullable)featureId;setsert
```


---
*Source: [https://trtc.io/document/60202](https://trtc.io/document/60202)*
