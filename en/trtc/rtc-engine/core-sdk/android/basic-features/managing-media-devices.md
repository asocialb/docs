# Managing Media Devices

TRTC needs to support the control of multiple media devices in live streaming scenario to meet various user needs during the live streaming process. This tutorial mainly introduces how to:

- [Turn on/off the microphone and camera](https://www.tencentcloud.com/document/product/647/64696#fa66e138-2cc2-443e-9c53-e7790b9cb68d)
- [Control the camera](https://www.tencentcloud.com/document/product/647/64696#03a81fd6-9066-48cf-9803-1bfcf03db37d)
- [Turn on/off the flash](https://www.tencentcloud.com/document/product/647/64696#920198bc-8e98-4bcc-866b-d34cbfe98048)
- [Enable/disable the face focus feature](https://www.tencentcloud.com/document/product/647/64696#31a9097d-f94f-4740-a602-a026ab82d2f5)
- [Detect if the user is speaking after mute](https://www.tencentcloud.com/document/product/647/64696#46c149f7-a707-46a0-85cf-f04a75346cf9)
- [Detect the status of the remote user's microphone/camera](https://www.tencentcloud.com/document/product/647/64696#2836e22e-eaec-4ce1-a773-9f5983f9e24e)

## Turn on/off the microphone and camera

TRTC provides two methods to turn on/off the microphone/camera. It is recommended to use **Option 1** for microphone/camera operations.

### Turn on/off the microphone

- **Option 1:**Call [muteLocalAudio](https://trtc.io/document/50762#8f14edc25b55deaceece6e48c8ccdd9b)

This interface is different from [stopLocalAudio](https://trtc.io/document/50762#8fafafeb80fe86f9fc0d893c9c35bd4e). Calling `muteLocalAudio(true)` does not release the microphone permission but continues to send very low bit rate silent packets. This is very suitable for scenarios that require **Cloud Recording**, because video files in formats like MP4 have high requirements for the continuity of audio data. Using [stopLocalAudio](https://trtc.io/document/50762#8fafafeb80fe86f9fc0d893c9c35bd4e) will make the recorded MP4 files hard to play.

Android

iOS

Mac

Windows

```
// Turn the mic onmCloud.muteLocalAudio(false);// Turn the mic offmCloud.muteLocalAudio(true);
```

```
// Turn the mic on[self.trtcCloud muteLocalAudio:NO];// Turn the mic off[self.trtcCloud muteLocalAudio:YES];
```

```
// Turn the mic on[self.trtcCloud muteLocalAudio:NO];// Turn the mic off[self.trtcCloud muteLocalAudio:YES];
```

```
// Turn the mic ontrtc_cloud_->muteLocalAudio(false);// Turn the mic offtrtc_cloud_->muteLocalAudio(true);
```

- **Option 2:** Call `startLocalAudio`/`stopLocalAudio`

Android

iOS

Mac

Windows

```
// Turn the mic on
mCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_SPEECH);// Turn the mic offmCloud.stopLocalAudio();
```

```
// Turn the mic on[self.trtcCloud startLocalAudio:TRTCAudioQualitySpeech];// Turn the mic off[self.trtcCloud stopLocalAudio];
```

```
// Turn the mic on[self.trtcCloud startLocalAudio:TRTCAudioQualitySpeech];// Turn the mic off[self.trtcCloud stopLocalAudio];
```

```
// Turn the mic ontrtc_cloud_->startLocalAudio(TRTCAudioQualitySpeech);// Turn the mic offtrtc_cloud_->stopLocalAudio();
```

### Turn the camera on/off

- **Option 1:** Call [muteLocalVideo](https://trtc.io/document/50762#3b9dab7aed0816028e9e593bce4525a9)

This interface is equivalent to the two interfaces `start/stopLocalPreview` when specifying **TRTC_VIDEO_STREAM_TYPE_BIG**, but has better response speed. This is because `start/stopLocalPreview` requires turning the camera on and off, and these operations are related to hardware devices, making them very time-consuming. In contrast, `muteLocalVideo` only needs to pause or release the data flow at the software level, thus being more efficient and more suitable for scenarios that require frequent on/off operations.

Android

iOS

Mac

Windows

```
// Turn the camera onmCloud.muteLocalVideo(TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, false);// Turn the camera offmCloud.muteLocalVideo(TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, true);
```

```
// Turn the camera on[self.trtcCloud muteLocalVideo:TRTCVideoStreamTypeBig mute:NO];// Turn the camera off[self.trtcCloud muteLocalVideo:TRTCVideoStreamTypeBig mute:YES];
```

```
// Turn the camera on[self.trtcCloud muteLocalVideo:TRTCVideoStreamTypeBig mute:NO];// Turn the camera off[self.trtcCloud muteLocalVideo:TRTCVideoStreamTypeBig mute:YES];
```

```
// Turn the camera ontrtc_cloud_->muteLocalVideo(TRTCVideoStreamTypeBig, false);// Turn the camera offtrtc_cloud_->muteLocalVideo(TRTCVideoStreamTypeBig, true);
```

- **Option 2:** Call `startLocalPreview`/`stopLocalPreview`

Android

iOS

Mac

Windows

```
// Turn the camera onTXCloudVideoView cameraVideo = findViewById(R.id.txcvv_main_local);
mCloud.startLocalPreview(true, cameraVideo);// Turn the camera offmCloud.stopLocalPreview();
```

```
// Turn the camera on[self.trtcCloud startLocalPreview:YES view:self.view];// Turn the camera off[self.trtcCloud stopLocalPreview];
```

```
// Turn the camera on[self.trtcCloud startLocalPreview:YES view:self.view];// Turn the camera off[self.trtcCloud stopLocalPreview];
```

```
// Turn the camera ontrtc_cloud_->startLocalPreview(true, local_view);// Turn the camera offtrtc_cloud_->stopLocalPreview();
```

## Control the camera

- **Switch between front and rear cameras:** For mobile devices, you can call `switchCamera` to switch between front and rear cameras.

Android

iOS

```
// Default to front camera, switch to rear cameraTXDeviceManager manager = mCloud.getDeviceManager();if(manager.isFrontCamera()) {    manager.switchCamera(false);}// Switch to front cameraTXDeviceManager manager = mCloud.getDeviceManager();manager.switchCamera(true);
```

```
// Default to front camera, switch to rear cameraTXDeviceManager * deviceManager = [self.trtcCloud getDeviceManager];if([deviceManager isFrontCamera]) {    [deviceManager switchCamera:false];}// Switch to front cameraTXDeviceManager * deviceManager = [self.trtcCloud getDeviceManager];[deviceManager switchCamera:true];
```

- **Set camera zoom factor:** For mobile devices, you can call `setCameraZoomRatio` to set the camera's zoom factor.

Android

iOS

```
TXDeviceManager deviceManager = mCloud.getDeviceManager();float msg = deviceManager.getCameraZoomMaxRatio(); // Get the camera's maximum zoom factor
deviceManager.setCameraZoomRatio(5); // Set the camera's zoom factor to 5
```

```
TXDeviceManager *deviceManager = [self.trtcCloud getDeviceManager];float cameraZoomMaxRatio = [deviceManager getCameraZoomMaxRatio]; // Get the camera's maximum zoom factor[deviceManager setCameraZoomRatio:5]; // Set the camera's zoom factor to 5
```

## Turn on/off the flash

For mobile devices, after turning on the rear-facing camera, you can call `enableCameraTorch` to turn the flash on/off.

Android

iOS

```
// Turn on the flash when switching to the rear-facing cameraTXDeviceManager manager = mCloud.getDeviceManager();manager.enableCameraTorch(true);// Turn the flash offTXDeviceManager manager = mCloud.getDeviceManager();manager.enableCameraTorch(false);
```

```
// Turn on the flash when switching to the rear-facing cameraTXDeviceManager * deviceManager = [self.trtcCloud getDeviceManager];if(![deviceManager isFrontCamera]) {    [deviceManager enableCameraTorch:true];}// Turn off the flashTXDeviceManager * deviceManager = [self.trtcCloud getDeviceManager];[deviceManager enableCameraTorch:false];
```

## Enable/Disable Face Focus

Calling `isAutoFocusEnabled` can check if the current mobile device supports automatic face position recognition. If the result is true, it indicates that the device supports this feature. At this point, calling `enableCameraAutoFocus` can enable the face auto-focus feature.

Android

iOS

```
// If the device supports automatic face position recognition, enable the auto-focus featureTXDeviceManager manager = mCloud.getDeviceManager();if (manager.isAutoFocusEnabled()) {    manager.enableCameraAutoFocus(true); }// Turn off the auto-focus featureTXDeviceManager manager = mCloud.getDeviceManager();manager.enableCameraAutoFocus(false);
```

```
// If the device supports automatic face position recognition, enable the auto-focus featureTXDeviceManager * deviceManager = [self.trtcCloud getDeviceManager];if([deviceManager isAutoFocusEnabled]) {    [deviceManager enableCameraAutoFocus:true];}// Turn off the auto-focus featureTXDeviceManager * deviceManager = [self.trtcCloud getDeviceManager];[deviceManager enableCameraAutoFocus:false];
```

## Detect if the user is speaking after mute

Invoke [enableAudioVolumeEvaluation](https://trtc.io/document/50762#a4342e2f3b540f5ecad64bbacb738787) to enable audio volume indication. After enabling this feature, the SDK will provide feedback on audio volume evaluation information for local or remote users in the [TRTCCloudListener](https://trtc.io/document/50763#3ac99d5f5509a822ae68d6d0fff9bde0)'s [onUserVoiceVolume](https://trtc.io/document/50763#2ec23470e2480bd26d91353c0998d019)  callback, including volume level, voice detection, audio spectrum, etc.

Android

iOS

Mac

Windows

```
private TRTCCloud mCloud;mCloud = TRTCCloud.sharedInstance(getApplicationContext());mCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_SPEECH); // Turn on the microphonemCloud.muteLocalAudio(true); // Turn off the microphone// Create a new TRTC instance to detect microphone volumeprivate TRTCCloud mNewCloud;mNewCloud = TRTCCloud.sharedInstance(getApplicationContext());mNewCloud.setListener(new TRTCCloudListener() {    // Obtain mCloud's audio volume evaluation information through the onUserVoiceVolume callback
    @Override
    public void onUserVoiceVolume(ArrayList<TRTCCloudDef.TRTCVolumeInfo> userVolumes, int totalVolume) {
        super.onUserVoiceVolume(userVolumes, totalVolume);        // Update the UI here, for example, update the height of the sound column
    }
});// Set the TRTCAudioVolumeEvaluateParams parametersTRTCCloudDef.TRTCAudioVolumeEvaluateParams audioVolumeEvaluateParams = new TRTCCloudDef.TRTCAudioVolumeEvaluateParams();
audioVolumeEvaluateParams.enablePitchCalculation = false; // Whether to enable local voice frequency calculation
audioVolumeEvaluateParams.enableSpectrumCalculation = false; // Whether to enable sound spectrum calculation
audioVolumeEvaluateParams.enableVadDetection = false; // Whether to enable local voice detection
audioVolumeEvaluateParams.interval = 100; // Set the trigger interval for the onUserVoiceVolume callback to 100 ms// Turn on the volume level prompt
mNewCloud.enableAudioVolumeEvaluation(true, audioVolumeEvaluateParams);
```

```
// AppDelegate.h@interface AppDelegate : UIResponder <UIApplicationDelegate, TRTCCloudDelegate> // Add TRTCCloudDelegate interface declaration@property (nonatomic, strong) TRTCCloud *trtcCloud; // Declare the trtcCloud instance@property (nonatomic, strong) TRTCCloud *newTRTCCloud; // Declare the newTRTCCloud instance// AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance];_trtcCloud.delegate = self;[self.trtcCloud startLocalAudio:TRTCAudioQualitySpeech]; // Turn the mic on[self.trtcCloud muteLocalAudio:YES]; // Turn off the mic// Initialize a new TRTC instance_newTRTCCloud = [TRTCCloud sharedInstance];_newTRTCCloud.delegate = self;// Set the TRTCAudioVolumeEvaluateParams parametersTRTCAudioVolumeEvaluateParams *trtcAudioVolumeEvaluateParams = [[TRTCAudioVolumeEvaluateParams alloc] init];trtcAudioVolumeEvaluateParams.enablePitchCalculation = NO; // Enable local voice frequency calculationtrtcAudioVolumeEvaluateParams.enableSpectrumCalculation = NO; // Enable sound spectrum calculationtrtcAudioVolumeEvaluateParams.enableVadDetection = NO; // Enable local voice detectiontrtcAudioVolumeEvaluateParams.interval = 100; // Set the trigger interval of the onUserVoiceVolume callback to 100 ms// Enable volume level prompt[self.newTRTCCloud enableAudioVolumeEvaluation:YES withParams:trtcAudioVolumeEvaluateParams];// Implement TRTCCloudDelegate callback method- (void)onUserVoiceVolume:(NSArray<TRTCVolumeInfo *> *)userVolumes totalVolume:(NSInteger)totalVolume {    // Process user volume information    for (TRTCVolumeInfo *volumeInfo in userVolumes) {        NSLog(@"User ID: %@, Volume: %ld", volumeInfo.userId, (long)volumeInfo.volume);        // Update the UI here, such as updating the height of the volume bar    }}
```

```
// AppDelegate.h@interface AppDelegate : NSObject <NSApplicationDelegate, TRTCCloudDelegate> // Add TRTCCloudDelegate interface declaration@property (nonatomic, strong) TRTCCloud *trtcCloud; // Declare the trtcCloud instance@property (nonatomic, strong) TRTCCloud *newTRTCCloud; // Declare the newTRTCCloud instance// AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance];_trtcCloud.delegate = self;[self.trtcCloud startLocalAudio:TRTCAudioQualitySpeech]; // Turn the mic on[self.trtcCloud muteLocalAudio:YES]; // Turn off the mic// Initialize a new TRTC instance_newTRTCCloud = [TRTCCloud sharedInstance];_newTRTCCloud.delegate = self;// Set the TRTCAudioVolumeEvaluateParams parametersTRTCAudioVolumeEvaluateParams *trtcAudioVolumeEvaluateParams = [[TRTCAudioVolumeEvaluateParams alloc] init];trtcAudioVolumeEvaluateParams.enablePitchCalculation = NO; // Enable local voice frequency calculationtrtcAudioVolumeEvaluateParams.enableSpectrumCalculation = NO; // Enable sound spectrum calculationtrtcAudioVolumeEvaluateParams.enableVadDetection = NO; // Enable local voice detectiontrtcAudioVolumeEvaluateParams.interval = 100; // Set the trigger interval of the onUserVoiceVolume callback to 100 ms// Enable volume level prompt[self.newTRTCCloud enableAudioVolumeEvaluation:YES withParams:trtcAudioVolumeEvaluateParams];// Implement TRTCCloudDelegate callback method- (void)onUserVoiceVolume:(NSArray<TRTCVolumeInfo *> *)userVolumes totalVolume:(NSInteger)totalVolume {    // Process user volume information    for (TRTCVolumeInfo *volumeInfo in userVolumes) {        NSLog(@"User ID: %@, Volume: %ld", volumeInfo.userId, (long)volumeInfo.volume);        // Update the UI here, such as updating the height of the volume bar    }}
```

```
// .h filepublic:     ITRTCCloud* trtc_cloud_;    ITRTCCloud* new_trtc_cloud;public:     virtual void onUserVoiceVolume(TRTCVolumeInfo* userVolumes, uint32_t userVolumesCount, uint32_t totalVolume) override;// .cpp filetrtc_cloud_ = getTRTCSharedInstance();trtc_cloud_ -> addCallback(this); trtc_cloud_ -> startLocalAudio(TRTCAudioQualitySpeech); // Turn the mic ontrtc_cloud_ -> muteLocalAudio(true); // Turn off the mic// Create a new TRTC instance to detect microphone volumenew_trtc_cloud_ = getTRTCSharedInstance();new_trtc_cloud_ -> addCallback(this); TRTCAudioVolumeEvaluateParams trtcAudioVolumeEvaluteParams;trtcAudioVolumeEvaluateParams.enablePitchCalculation = false; // Enable local voice frequency calculationtrtcAudioVolumeEvaluateParams.enableSpectrumCalculation = false; // Enable sound spectrum calculationtrtcAudioVolumeEvaluateParams.enableVadDetection = false; // Enable local voice detectiontrtcAudioVolumeEvaluateParams.interval = 100; // Set the trigger interval of the onUserVoiceVolume callback to 100 ms// Enable volume level promptnew_trtc_cloud_ -> enableAudioVolumeEvaluation(true, trtcAudioVolumeEvaluateParams);// Implement TRTCCloudDelegate callback method, replace CLASSNAME with your class namevoid CLASSNAME::onUserVoiceVolume(TRTCVolumeInfo* userVolumes, uint32_t userVolumesCount, uint32_t totalVolume) {    // Update the UI here, such as updating the height of the volume bar}
```

## Detect the status of the remote user's microphone/camera

This feature is typically used to confirm the on/off status of a remote user's microphone and camera.

Assuming there are currently two users, A and B.

1. When A successfully enters the room, and B also successfully enters the room, A will receive the [onRemoteUserEnterRoom](https://trtc.io/document/50763#a5bd4299b42d86c93067c2b8f581e959) event notification.
2. At this time, A assumes that B has not yet turned on their microphone or camera.
3. When A receives [onUserAudioAvailable(userId, true)](https://trtc.io/document/50763#cb979bbb36c24acc891ce2115ff2b6c6) or [onUserVideoAvailable(userId, true)](https://trtc.io/document/50763#448623ba3ddafa44cdb425bea100c2d8) from B, it indicates that Remote User B has published their audio/main video stream.
4. When A receives [onUserAudioAvailable(userId, false)](https://trtc.io/document/50763#cb979bbb36c24acc891ce2115ff2b6c6) or [onUserVideoAvailable(userId, false)](https://trtc.io/document/50763#448623ba3ddafa44cdb425bea100c2d8) from B, it indicates that Remote User B has canceled the publication of their audio/main video stream.

## Contact us

If you have any suggestions or feedback, please contact `info_rtc@tencent.com`.


---
*Source: [https://trtc.io/document/64696](https://trtc.io/document/64696)*
