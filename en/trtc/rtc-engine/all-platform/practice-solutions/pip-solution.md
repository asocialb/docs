# PIP Solution

In interactive live streaming and other video scenarios, audiences on mobile devices may need to temporarily operate other apps while watching a live stream of an anchor for an extended period. Enabling the live stream to continue playing without interruption while the audiences use other apps can enhance the viewing experience. Picture-in-Picture (PIP) is a solution designed for such scenarios. The implementation effect is shown in the figure below. This document introduces how to implement PIP on iOS, Android, and Flutter.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/01fd2c31b05611ef8b1b525400f69702.png)

PIP relies on system capabilities provided by iOS and Android. It can be divided into the anchor end (which requires the collection of camera and upstream data) and the audience end (which only requires downstream data). Due to stricter permission controls on iOS, PIP is supported only for the audience end on iOS, while Android supports PIP for both the anchor end and the audience end. For video playback, two modes are generally available, that is, Real-Time Communication Engine (RTC Engine) playback and live streaming playback. The PIP solution covers both modes.

## Implementing PIP for Audiences on iOS

### Enabling Corresponding Permissions

You need to enable the following permissions in the **Signing & Capabilities** section of the iOS project:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/01ee9243b05611ef8c01525400fdb830.png)

### Calling the SDK for Implementation

The iOS SDK provides APIs for implementing PIP. By calling these APIs, you can easily enable PIP (for relevant APIs, see the example code below). However, the SDK only supports viewing the video of a single anchor in PIP mode. If you want to view the PK videos of multiple anchors in PIP mode, you need to call system APIs. For details, see [Calling System APIs for Implementation](https://www.tencentcloud.com/document/product/1228/73992#36552de9-d60c-4408-8314-81b4a46a321c).

#### RTC Engine Playback

> **Note:**The RTC Engine SDK should be version 12.1 or later.

Call the following API on the audience end to enable PIP.

objectivec

swift

```
NSDictionary *param = @{    @"api" : @"enablePictureInPictureFloatingWindow",    @"params" : @{        @"enable" : @(true)    }};NSError *err = nil;NSData *jsonData = [NSJSONSerialization dataWithJSONObject:param options:0 error:&err];if (err) {    NSLog(@"error: %@", err);}NSString *paramJsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[self.trtcCloud callExperimentalAPI:paramJsonString];
```

```
let param: [String : Any] = ["api": "enablePictureInPictureFloatingWindow", "params": ["enable":true]]if let jsonData = try? JSONSerialization.data(withJSONObject: param, options: .fragmentsAllowed) {    let paramJsonString = String.init(data: jsonData, encoding: .utf8) ?? ""    trtcCloud.callExperimentalAPI(paramJsonString)}
```

To disable PIP, pass **false** in the corresponding parameter.

### Calling System APIs for Implementation

PIP is a capability provided by the iOS system. By calling system APIs, you can implement PIP in complex scenarios. The iOS system supports PIP, but with considerable limitations. You cannot directly use a video rendering UIView to implement PIP. Instead, you need to use custom rendering to render the video to be displayed in PIP mode onto a component that meets the necessary requirements. The following example introduces how to implement PIP by calling system APIs in a 2-anchor PK scenario.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/42684611b2b811ef96e55254002693fd.PNG)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f39f640b2e511ef9d2952540055f650.png)

> **Note:**For scenarios with 1 or more than 2 anchors, PIP can still be implemented as follows. Here, only the 2-anchor PK scenario is described.

1. Define the components required for PIP.

Since the iOS system only allows specific components for PIP rendering, AVSampleBufferDisplayLayer is used here. This component should directly render the corresponding video. Therefore, a combinedPixelBuffer is defined for merging the video data of two anchors.

```
import UIKitimport AVKitimport CoreFoundationimport TXLiteAVSDK_Professionalclass PipVC: UIViewController {    let trtcCloud = TRTCCloud()    var pipController: AVPictureInPictureController?    var combinedPixelBuffer: CVPixelBuffer?    let pixelBufferLock = DispatchQueue(label: "com.demo.pip")    var pipDisplayLayer: AVSampleBufferDisplayLayer!}
```

2. Enter the RTC Engine room.

```
func enterTrtcRoom() {    let params = TRTCParams()    params.sdkAppId = UInt32(SDKAppID)    params.roomId = UInt32(roomId)    params.userId = userId    params.role = .audience    params.userSig = GenerateTestUserSig.genTestUserSig(identifier: userId) as String    trtcCloud.addDelegate(self)    trtcCloud.enterRoom(params, appScene: .LIVE)   }
```

3. Set up the audio session and enable background decoding.

```
func setupAudioSession() {    do {        try AVAudioSession.sharedInstance().setCategory(.playback)    } catch let error {        print("+> error: \\(error)")        return    }    do {        try AVAudioSession.sharedInstance().setActive(true)    } catch let error {        print("+> error: \\(error)")        return    }}func enableBGDecode() {    let param: [String : Any] = ["api": "enableBackgroundDecoding",                                 "params": ["enable":true]]    if let jsonData = try? JSONSerialization.data(withJSONObject: param, options: .fragmentsAllowed) {        let paramJsonString = String.init(data: jsonData, encoding: .utf8) ?? ""        trtcCloud.callExperimentalAPI(paramJsonString)    }}
```

4. Initialize the PIP component.

```
func setupPipController() {    let screenWidth = UIScreen.main.bounds.width    let videoHeight = screenWidth / 2 / 9 * 16        pipDisplayLayer = AVSampleBufferDisplayLayer()    pipDisplayLayer.frame = CGRect(x: 0, y: 0, width: screenWidth, height: videoHeight) // Adjust size as needed    pipDisplayLayer.videoGravity = .resizeAspect    pipDisplayLayer.isOpaque = true    pipDisplayLayer.backgroundColor = CGColor(red: 0, green: 0, blue: 0, alpha: 1)    view.layer.addSublayer(pipDisplayLayer)    if AVPictureInPictureController.isPictureInPictureSupported() {        let contentSource = AVPictureInPictureController.ContentSource(            sampleBufferDisplayLayer: pipDisplayLayer,            playbackDelegate: self        )        pipController = AVPictureInPictureController(contentSource: contentSource)        pipController?.delegate = self        pipController?.canStartPictureInPictureAutomaticallyFromInline = true    } else {        print("+> error")    }}
```

5. Enable custom rendering.

> **Note:**When you enable custom rendering, the specified format `._NV12` is related to the method used in `Step 6: Concatenate left and right frames`. Different formats require different concatenation methods. This example code only shows left-right concatenation in the `._NV12` format.

```
extension PipVC: TRTCCloudDelegate {    func onUserVideoAvailable(_ userId: String, available: Bool) {        if available {            trtcCloud.startRemoteView(userId, streamType: .big, view: nil)            trtcCloud.setRemoteVideoRenderDelegate(userId, delegate: self, pixelFormat: ._NV12, bufferType: .pixelBuffer);        }else{            trtcCloud.stopRemoteView(userId, streamType: .big)        }    }}
```

6. Concatenate left and right frames.

When you concatenate the video data of two anchors, the SDK callbacks for video data may arrive asynchronously. Therefore, each time the video data from an anchor is received, you need to update the corresponding data and lock access. For multiple anchors, use a similar approach. The following code demonstrates a layout where the two anchors are arranged side by side, each occupying half of the screen. For other layouts, arrange the videos according to your business requirements. The layout logic here is independent of the SDK.

```
func createCombinedPixelBuffer(from sourceBuffer: CVPixelBuffer) {    let width = CVPixelBufferGetWidth(sourceBuffer) * 2    let height = CVPixelBufferGetHeight(sourceBuffer)    let pixelFormat = CVPixelBufferGetPixelFormatType(sourceBuffer)    let attributes: [CFString: Any] = [        kCVPixelBufferWidthKey: width,        kCVPixelBufferHeightKey: height,        kCVPixelBufferPixelFormatTypeKey: pixelFormat,        kCVPixelBufferIOSurfacePropertiesKey: [:]        ]    CVPixelBufferCreate(kCFAllocatorDefault, width, height, pixelFormat, attributes as CFDictionary, &combinedPixelBuffer)}func updateCombinedPixelBuffer(with sourceBuffer: CVPixelBuffer, forLeft: Bool) {    guard let combinedBuffer = combinedPixelBuffer else { print("+> error"); return}        CVPixelBufferLockBaseAddress(combinedBuffer, [])    CVPixelBufferLockBaseAddress(sourceBuffer, [])    // Plane 0: Y/luma plane    let combinedLumaBaseAddress = CVPixelBufferGetBaseAddressOfPlane(combinedBuffer, 0)!    let sourceLumaBaseAddress = CVPixelBufferGetBaseAddressOfPlane(sourceBuffer, 0)!    let combinedLumaBytesPerRow = CVPixelBufferGetBytesPerRowOfPlane(combinedBuffer, 0)    let sourceLumaBytesPerRow = CVPixelBufferGetBytesPerRowOfPlane(sourceBuffer, 0)    let widthLuma = CVPixelBufferGetWidthOfPlane(sourceBuffer, 0)    let heightLuma = CVPixelBufferGetHeightOfPlane(sourceBuffer, 0)    // Plane 1: UV/chroma plane    let combinedChromaBaseAddress = CVPixelBufferGetBaseAddressOfPlane(combinedBuffer, 1)!    let sourceChromaBaseAddress = CVPixelBufferGetBaseAddressOfPlane(sourceBuffer, 1)!    let combinedChromaBytesPerRow = CVPixelBufferGetBytesPerRowOfPlane(combinedBuffer, 1)    let sourceChromaBytesPerRow = CVPixelBufferGetBytesPerRowOfPlane(sourceBuffer, 1)    let widthChroma = CVPixelBufferGetWidthOfPlane(sourceBuffer, 1)    let heightChroma = CVPixelBufferGetHeightOfPlane(sourceBuffer, 1)    for row in 0..<heightLuma {        let combinedRow = combinedLumaBaseAddress.advanced(by: row * combinedLumaBytesPerRow + (forLeft ? 0 : widthLuma))        let sourceRow = sourceLumaBaseAddress.advanced(by: row * sourceLumaBytesPerRow)        memcpy(combinedRow, sourceRow, widthLuma)    }        // ._nv12 the chroma plane is subsampled 2:1 horizontally and vertically    for row in 0..<heightChroma {        let combinedRow = combinedChromaBaseAddress.advanced(by: row * combinedChromaBytesPerRow + (forLeft ? 0 : 2 * widthChroma))        let sourceRow = sourceChromaBaseAddress.advanced(by: row * sourceChromaBytesPerRow)        memcpy(combinedRow, sourceRow, 2 * widthChroma)    }    CVPixelBufferUnlockBaseAddress(sourceBuffer, [])    CVPixelBufferUnlockBaseAddress(combinedBuffer, [])}
```

7. Render the merged frame onto the corresponding component.

```
func displayPixelBuffer(_ pixelBuffer: CVPixelBuffer, in layer: AVSampleBufferDisplayLayer) {    var timing = CMSampleTimingInfo.init(duration: .invalid,                                         presentationTimeStamp: .invalid,                                         decodeTimeStamp: .invalid)    var videoInfo: CMVideoFormatDescription? = nil    var result = CMVideoFormatDescriptionCreateForImageBuffer(allocator: nil,                                                              imageBuffer: pixelBuffer,                                                              formatDescriptionOut: &videoInfo)    if result != 0 {        return    }    guard let videoInfo = videoInfo else {        return    }    var sampleBuffer: CMSampleBuffer? = nil    result = CMSampleBufferCreateForImageBuffer(allocator: kCFAllocatorDefault,                                                imageBuffer: pixelBuffer,                                                dataReady: true,                                                makeDataReadyCallback: nil,                                                refcon: nil,                                                formatDescription: videoInfo,                                                sampleTiming: &timing,                                                sampleBufferOut: &sampleBuffer)    if result != 0 {        return    }    guard let sampleBuffer = sampleBuffer else {        return    }    guard let attachments = CMSampleBufferGetSampleAttachmentsArray(sampleBuffer,                                                                    createIfNecessary: true) else {        return    }    CFDictionarySetValue(        unsafeBitCast(CFArrayGetValueAtIndex(attachments, 0), to: CFMutableDictionary.self),        Unmanaged.passUnretained(kCMSampleAttachmentKey_DisplayImmediately).toOpaque(),        Unmanaged.passUnretained(kCFBooleanTrue).toOpaque())        layer.enqueue(sampleBuffer)    if layer.status == .failed {        if let error = layer.error as? NSError {            if error.code == -11847 {                print("+> error")            }        }    }    }
```

8. Obtain the video data from the remote user, concatenate the data, and render the concatenated data onto the specified component.

The example code uses left to identify the anchor ID to be displayed on the left. In actual business scenarios, modify this setting according to your business needs.

```
extension PipVC: TRTCVideoRenderDelegate {    func onRenderVideoFrame(_ frame: TRTCVideoFrame, userId: String?, streamType: TRTCVideoStreamType) {        guard let newPixelBuffer = frame.pixelBuffer else { print("+> error"); return}        pixelBufferLock.sync {            if combinedPixelBuffer == nil {                createCombinedPixelBuffer(from: newPixelBuffer)            }            if userId == "left" {                updateCombinedPixelBuffer(with: newPixelBuffer, forLeft: true)            } else {                updateCombinedPixelBuffer(with: newPixelBuffer, forLeft: false)            }        }        if let combinedBuffer = combinedPixelBuffer {            DispatchQueue.main.async {                self.displayPixelBuffer(combinedBuffer, in: self.pipDisplayLayer)            }        }    }}
```

9. Implement related protocols.

```
extension PipVC: AVPictureInPictureControllerDelegate {    func pictureInPictureControllerWillStartPictureInPicture(_ pictureInPictureController: AVPictureInPictureController) {    }    func pictureInPictureControllerDidStartPictureInPicture(_ pictureInPictureController: AVPictureInPictureController) {    }    func pictureInPictureControllerDidStopPictureInPicture(_ pictureInPictureController: AVPictureInPictureController) {    }    func pictureInPictureController(_ pictureInPictureController: AVPictureInPictureController, restoreUserInterfaceForPictureInPictureStopWithCompletionHandler completionHandler: @escaping (Bool) -> Void) {        completionHandler(true)    }    func pictureInPictureController(_ pictureInPictureController: AVPictureInPictureController, failedToStartPictureInPictureWithError error: any Error) {    } }extension PipVC: AVPictureInPictureSampleBufferPlaybackDelegate {    func pictureInPictureControllerTimeRangeForPlayback(_ pictureInPictureController: AVPictureInPictureController) -> CMTimeRange {        return CMTimeRange.init(start: .zero, duration: .positiveInfinity)    }    func pictureInPictureControllerIsPlaybackPaused(_ pictureInPictureController: AVPictureInPictureController) -> Bool {        return false    }    func pictureInPictureController(_ pictureInPictureController: AVPictureInPictureController, setPlaying playing: Bool) {    }    func pictureInPictureController(_ pictureInPictureController: AVPictureInPictureController, didTransitionToRenderSize newRenderSize: CMVideoDimensions) {    }    func pictureInPictureController(_ pictureInPictureController: AVPictureInPictureController, skipByInterval skipInterval: CMTime) async {    }}
```

10. Enable/Disable PIP.

```
// Disable PIP.pipController?.stopPictureInPicture()// Enable PIP.pipController?.startPictureInPicture()
```

> **Notes:**Here, only the implementation solution is described. In actual business scenarios, you also need to handle various possible exceptions.Handling the PIP overlay control buttons is a system-level capability provided by iOS and is not managed by the SDK. No explanation is provided here. Business personnel should implement the buttons based on actual needs.

## Implementing PIP on Android

Starting from Android 8.0 (API level 26), Android allows activities to launch in PIP mode. PIP is a special type of multi-window mode that is mostly used for video playback. In this mode, users can watch a video in a small window pinned to a corner of the screen while navigating between apps or browsing content on the home screen. The RTC Engine SDK does not further encapsulate the Android PIP API. The PIP feature is implemented by directly calling the Android API. For details, see the Android documentation [Add videos using picture-in-picture (PiP)](https://developer.android.google.cn/develop/ui/views/picture-in-picture).

On Android, when you enter the PIP mode, the system performs re-measurement and re-layout based on the PIP window size according to the XML layout rules. Therefore, both the anchor end and audience end can implement PIP following these rules.

### Implementing PIP

The following shows how to implement PIP according to the Android documentation [Add videos using picture-in-picture (PiP)](https://developer.android.google.cn/develop/ui/views/picture-in-picture).

1. Declare the PIP attributes for <activity> in AndroidManifest.xml.

```
<activity    android:name="com.tencent.trtc.pictureinpicture.PictureInPictureActivity"    android:theme="@style/Theme.AppCompat.Light.NoActionBar"    android:configChanges="screenSize|smallestScreenSize|screenLayout|orientation"    android:supportsPictureInPicture="true"
```

  - `android:supportsPictureInPicture="true"` declares that the activity supports PIP.
  - If layout changes occur during PIP mode transitions and you do not want the activity to restart, you need to configure the corresponding values in the android:configChanges attribute.
2. Enter the PIP mode.

```
private void startPictureInPicture() {    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {        PictureInPictureParams.Builder pictureInPictureBuilder = new PictureInPictureParams.Builder();        Rational aspectRatio = new Rational(mVideoView.getWidth(), mVideoView.getHeight());        pictureInPictureBuilder.setAspectRatio(aspectRatio);        // Enter the PIP mode.        enterPictureInPictureMode(pictureInPictureBuilder.build());    } else {        Toast.makeText(this, R.string.picture_in_picture_not_supported, Toast.LENGTH_SHORT).show();    }}
```

  - `pictureInPictureBuilder.setAspectRatio(aspectRatio); ` sets the aspect ratio of the PIP window. Here, set the value to the aspect ratio of the video playback view.
  - `enterPictureInPictureMode(pictureInPictureBuilder.build()); ` enters the PIP mode.
3. Obtain callbacks for entering and exiting the PIP mode.

```
@Overridepublic void onPictureInPictureModeChanged(boolean isInPictureInPictureMode, Configuration configuration) {    super.onPictureInPictureModeChanged(isInPictureInPictureMode, configuration);    if (isInPictureInPictureMode) {       // Hide the view when entering the PIP mode.    } else{       // Display the view after exiting the PIP mode.    }}
```

### Displaying Multiple Video Views in PIP Mode

To display multiple video views, you can set a fixed width and height for View A when entering the PIP mode. The other views will be displayed according to the layout rules or a percentage-based layout.

> **Note:**Displaying multiple video views in PIP mode is not an officially supported Android behavior. This implementation currently works on Android 12, but may change with future Android system updates. You need to test system compatibility across different versions before release.

#### Effect Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/746c66e6c36f11f08c0e52540044a08e.jpg)

```
// mTRTCCloud corresponds to the left video view (TXCloudVideoView), and TRTC_VIDEO_RENDER_MODE_FIT is set.TRTCCloudDef.TRTCRenderParams param = new TRTCCloudDef.TRTCRenderParams();param.fillMode      = TRTCCloudDef.TRTC_VIDEO_RENDER_MODE_FIT;mTRTCCloud.setRemoteRenderParams(remoteUserIdA,TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, param);mTRTCCloud.startRemoteView(remoteUserIdA, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, mTXCloudRemoteView);// mTRTCCloud corresponds to the right video view (TXCloudVideoView).mTRTCCloud.startRemoteView(remoteUserIdB, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, mTXCloudRemoteView);
```

After entering the PIP mode, you can calculate and manually set the width and height of TXCloudVideoView or configure the filling mode to ensure the complete display of the video view. Call the [setRemoteRenderParams](https://trtc.io/document/50762?platform=android&product=rtcengine&menulabel=core%20sdk#bfce08bf4cac4decd14d800b69d0ee8e) method of mTRTCCloud (TRTCCloud object) to set the filling mode for the video view.

- The left TXCloudVideoView in PIP is set up with the TRTC_VIDEO_RENDER_MODE_FIT effect.
- The right TXCloudVideoView in PIP is set up with the TRTC_VIDEO_RENDER_MODE_FILL effect.

In this example, only 2 video views (TXCloudVideoView) are involved. Set the width and height for the left TXCloudVideoView, and the right TXCloudVideoView will be displayed according to the layout rules. If you have multiple TXCloudVideoView instances, you can properly adjust the layout to achieve the desired effect.

#### Implementation Steps

1. Add 2 TXCloudVideoView instances to display them side by side in activity_picture_in_picture.xml.

```
<com.tencent.rtmp.ui.TXCloudVideoView    android:id="@+id/video_view"    android:layout_width="192dp"    android:layout_height="108dp"    android:layout_alignParentStart="true"    android:background="#00BCD4"/><com.tencent.rtmp.ui.TXCloudVideoView    android:id="@+id/video_view2"    android:layout_width="192dp"    android:layout_height="108dp"    android:layout_alignTop="@+id/video_view"    android:layout_toEndOf="@+id/video_view"    android:background="#3F51B5"/>
```

2. Set the width and height of video_view when entering and exiting the PIP mode.

```
@Overridepublic void onPictureInPictureModeChanged(boolean isInPictureInPictureMode, Configuration configuration) {    super.onPictureInPictureModeChanged(isInPictureInPictureMode, configuration);    if (isInPictureInPictureMode) {        // Set the width of mVideoView to 100dp.        RelativeLayout.LayoutParams layoutParams = (RelativeLayout.LayoutParams) mVideoView.getLayoutParams();        layoutParams.width = (int) TypedValue.applyDimension(TypedValue.COMPLEX_UNIT_DIP, 100, getResources().getDisplayMetrics());    } else {        // When exiting the PIP mode, restore the width of video_view.        RelativeLayout.LayoutParams layoutParams = (RelativeLayout.LayoutParams) mVideoView.getLayoutParams();        layoutParams.width = (int) TypedValue.applyDimension(TypedValue.COMPLEX_UNIT_DIP, 192, getResources().getDisplayMetrics());    }}
```

## Implementing PIP for Audiences in Flutter

Enabling PIP in Flutter varies across different platforms. The following describes the implementations for iOS and Android, separately.

### Releasing to iOS Devices

#### Calling the SDK for Implementation

In Flutter, you can also easily enable PIP by calling the APIs provided by the SDK. As with the native iOS implementation, the SDK only supports PIP for viewing the video of a single anchor. To display the videos of multiple anchors in PIP mode, see [Calling System APIs for Implementation](https://www.tencentcloud.com/document/product/1228/73992#3426344d-ebad-4b50-ae4d-a73b465db2bd).

> **Note:**Likewise, you need to enable the corresponding permissions in the iOS project generated by Flutter. See the [Enabling Corresponding Permissions](https://www.tencentcloud.com/document/product/1228/73992#1008adfd-eee2-41d2-90d3-5a31e2b7445f) section in this document.

##### RTC Engine Playback

The Flutter SDK should be version 2.9.1 or later. Call the following API on the audience end to enable PIP.

```
trtcCloud.callExperimentalAPI(jsonEncode({    "api": "enablePictureInPictureFloatingWindow",    "params": {"enable": true}}));
```

To disable PIP, pass **false** in the corresponding parameter.

##### Live Streaming Playback

Call the following API on the audience end to enable PIP.

```
var pipCode = await _livePlayer!.enablePictureInPicture(true);if (pipCode != V2TXLIVE_OK) {  print("error: $pipCode");}
```

To disable PIP, pass **false** in the corresponding parameter.

#### Calling System APIs for Implementation

To implement complex PIP capabilities, such as displaying the videos of multiple anchors in PIP mode, you need to call iOS system APIs. See [Implementing PIP for Audiences on iOS - Calling System APIs for Implementation](https://www.tencentcloud.com/document/product/1228/73992#36552de9-d60c-4408-8314-81b4a46a321c). The following describes how Flutter call iOS system APIs.

1. Flutter uses MethodChannel to send messages to the native iOS end.

```
final channel = MethodChannel('flutter_ios_pip_demo');await channel.invokeMethod('enablePip', {                            'marginTop': appBarHeight + topSafeAreaHeight,                            'pkLeft': pkLeftUserId,                            'pkRight': pkRightUserId,                          });
```

2. The messages are received and processed accordingly in the iOS project packaged by Flutter.

When calling system APIs to enable PIP in a multi-anchor PK scenario, Flutter actually calls the iOS system API. The iOS native code uses custom capture to redraw the PK frames of 2 anchors and displays the resulting frame above the Flutter layer. Therefore, the window size and position drawn by the iOS system API should match those in Flutter. Flutter passes the corresponding layout parameters and anchor IDs through MethodChannel.

```
var channel: FlutterMethodChannel?let pipListener = PipRender()guard let controller = window?.rootViewController as? FlutterViewController else {    fatalError("Invalid root view controller")}channel = FlutterMethodChannel(name: "flutter_ios_pip_demo", binaryMessenger: controller.binaryMessenger)channel?.setMethodCallHandler({ [weak self] call, result in    guard let self = self else { return }    switch (call.method) {    case "enablePip":        if let arg = call.arguments as? [String: Any] {            let marginTop = arg["marginTop"] as? CGFloat ?? 0            let pkLeft = arg["pkLeft"] as? String ?? ""            let pkRight = arg["pkRight"] as? String ?? ""            pipListener.enablePip(mainView: vc.view, mt: mt, pkLeft: pkLeft, pkRight: pkRight)        }        result(nil)        break    case "disablePip":        pipListener.disablePip()        result(nil)        break    default:        break    }})
```

3. Define a class to handle PIP.

When enabling PIP, switch the stream of the corresponding anchor to custom rendering, and insert the rendered frame into the root view for display.

```
import UIKitimport AVKitimport TXLiteAVSDK_Professionalclass PipRender: NSObject {    // For other variables, see the Calling System APIs for Implementation section for the native iOS end.    var mainView: UIView?    var mt: CGFloat?        // Since trtcCloud is single-instance, you can obtain it this way in your code.    let trtcCloud = TRTCCloud.sharedInstance()    func disablePip() {        pipDisplayLayer?.removeFromSuperlayer()        pipController?.stopPictureInPicture()    }    func enablePip(mainView: UIView, mt: CGFloat, pkLeft: String, pkRight: String) {        self.mainView = mainView        self.mt = mt        trtcCloud.addDelegate(self)        enableBGDecode()        setupAudioSession()        setupPipController()        pipController?.startPictureInPicture()        if pkLeft.count > 0 {            trtcCloud.startRemoteView(pkLeft, streamType: .big, view: nil)            trtcCloud.setRemoteVideoRenderDelegate(pkLeft, delegate: self, pixelFormat: ._NV12, bufferType: .pixelBuffer);        }        if pkRight.count > 0 {            trtcCloud.startRemoteView(pkRight, streamType: .big, view: nil)            trtcCloud.setRemoteVideoRenderDelegate(pkRight, delegate: self, pixelFormat: ._NV12, bufferType: .pixelBuffer);        }    }        // In this method, the PIP display position needs to be adjusted according to business needs to ensure that the position is the same as the display position in Flutter.    func setupPipController() {        let screenWidth = UIScreen.main.bounds.width        let videoHeight = screenWidth / 2 / 9 * 16        pipDisplayLayer = AVSampleBufferDisplayLayer()        // Adjust the PIP display position here based on your actual needs.        let tsa = self.mainView?.safeAreaInsets.top ??         let vmt = tsa + (self.mt ?? 0)        pipDisplayLayer.frame = CGRect(x: 0, y: vmt, width: screenWidth, height: videoHeight) // Adjust size as needed        pipDisplayLayer.videoGravity = .resizeAspect        pipDisplayLayer.isOpaque = true        pipDisplayLayer.backgroundColor = CGColor(red: 0, green: 0, blue: 0, alpha: 1)        // Use the mainView passed in by enablePIP to add a PIP frame.        mainView?.layer.addSublayer(pipDisplayLayer)                if AVPictureInPictureController.isPictureInPictureSupported() {            let contentSource = AVPictureInPictureController.ContentSource(                sampleBufferDisplayLayer: pipDisplayLayer,                playbackDelegate: self            )            pipController = AVPictureInPictureController(contentSource: contentSource)            pipController?.delegate = self            pipController?.canStartPictureInPictureAutomaticallyFromInline = true        } else {            print("+> PiP not supported")        }    }    // All other methods follow the implementation in the Calling System APIs for Implementation section for the native iOS end.}
```

4. When stopping PIP in Flutter, you need to re-pull the stream of the corresponding anchor to restore Flutter-side rendering.

```
// Trigger the PIP stop according to business needs.trtcCloud.startRemoteView(pkLeftUserId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, pkLeftId);trtcCloud.startRemoteView(pkRightUserId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, pkRightId);await channel.invokeMethod('disablePip');
```

5. When destroying the current page in Flutter, you need to stop PIP.

Enabling PIP actually calls the iOS system API to redraw a view above the Flutter view. Therefore, when destroying the current page, you need to stop PIP to remove the corresponding view from the root view.

```
@overridedispose() {    channel.invokeMethod('disablePip');    super.dispose();}
```

### Implementing PIP on Android via Flutter

Implementing PIP in Flutter requires calling the Android PIP API. After PIP is enabled, the Flutter UI is displayed according to existing widget layout rules. You can hide certain widgets and reasonably set the width and height of the video widget based on your own business rules.

Use [Platform Channels to Call Android Code](https://docs.flutter.dev/platform-integration/platform-channels). A channel consists of the client end (Flutter) and the host end (Android). The following shows the detailed implementation of PIP:

1. Code on the Flutter client end: Use the channel name "samples.flutter.dev" to call the channel method "pictureInPicture". The detailed implementation of this method is handled on the Android host end.

```
MethodChannel _channel = MethodChannel('samples.flutter.dev');final int? result = await _channel.invokeMethod('pictureInPicture');
```

2. Code on the Android host end.
  2.1. Implement PIP in the Activity that inherits FlutterActivity:

```
private void startPictureInPicture() {    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {        PictureInPictureParams.Builder pictureInPictureBuilder = new PictureInPictureParams.Builder();        // Set the specified PIP size based on specific business requirements.        Rational aspectRatio = new Rational(100, 100);        pictureInPictureBuilder.setAspectRatio(aspectRatio);        // Enter the PIP mode.        enterPictureInPictureMode(pictureInPictureBuilder.build());    } else {        Toast.makeText(this, R.string.picture_in_picture_not_supported, Toast.LENGTH_SHORT).show();    }}@Overridepublic void configureFlutterEngine(@NonNull FlutterEngine flutterEngine) {    super.configureFlutterEngine(flutterEngine);    MethodChannel channel = new MethodChannel(flutterEngine.getDartExecutor().getBinaryMessenger(), "samples.flutter.dev");    channel.setMethodCallHandler(            (call, result) -> {                if (call.method.equals("pictureInPicture")) {                    startPictureInPicture();                } else {                    result.notImplemented();                }            }    );}
```

  2.2. Configure the PIP parameter `android:supportsPictureInPicture="true"` for the activity in AndroidManifest.xml, as follows:

```
<activity    android:name="example.android.app.src.main.java.com.tencent.live.example.MainActivity"    android:supportsPictureInPicture="true"    android:configChanges="orientation|keyboardHidden|keyboard|screenSize|smallestScreenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"    >    ...</activity>
```

To display two video frames in PIP mode, such as in an anchor PK scenario, you can reasonably set the layout rules and size.


---
*Source: [https://trtc.io/document/74577](https://trtc.io/document/74577)*
