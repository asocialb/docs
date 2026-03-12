# Adjusting Volume

This article will explain how to:

- [Detect the volume level of local and remote microphones](https://www.tencentcloud.com/document/product/647/64697#bbfd3c08-5812-45b9-9f27-f24d6634e277)
- [Detect if remote users are speaking after being muted](https://www.tencentcloud.com/document/product/647/64697#57aa3c4a-e857-425f-8751-af043ea15911)
- [Adjust the volume level of local and remote microphones](https://www.tencentcloud.com/document/product/647/64697#f3bb6cc8-c6b6-478d-b9ea-47d1f3b87206)

## Detect volume levels

Call [enableAudioVolumeEvaluation](https://trtc.io/document/50762#a4342e2f3b540f5ecad64bbacb738787) to enable audio volume indication. After enabling this feature, the SDK will provide feedback on audio volume evaluation information for local or remote users in the [TRTCCloudListener](https://trtc.io/document/50763#3ac99d5f5509a822ae68d6d0fff9bde0)'s [onUserVoiceVolume](https://trtc.io/document/50763#2ec23470e2480bd26d91353c0998d019) callback, including volume level, voice detection, audio spectrum, etc.

Android

iOS

Mac

Windows

```
private TRTCCloud mCloud;mCloud = TRTCCloud.sharedInstance(getApplicationContext());mCloud.setListener(new TRTCCloudListener() {    // Get audio volume evaluation information through the onUserVoiceVolume callback
    @Override
    public void onUserVoiceVolume(ArrayList<TRTCCloudDef.TRTCVolumeInfo> userVolumes, int totalVolume) {
        super.onUserVoiceVolume(userVolumes, totalVolume);        // Update the UI here, for example, update the height of the sound column
    }
});// Set the TRTCAudioVolumeEvaluateParams parametersTRTCCloudDef.TRTCAudioVolumeEvaluateParams audioVolumeEvaluateParams = new TRTCCloudDef.TRTCAudioVolumeEvaluateParams();
audioVolumeEvaluateParams.enablePitchCalculation = false; // Whether to enable local voice frequency calculation
audioVolumeEvaluateParams.enableSpectrumCalculation = false; // Whether to enable sound spectrum calculation
audioVolumeEvaluateParams.enableVadDetection = false; // Whether to enable local voice detection
audioVolumeEvaluateParams.interval = 100; // Set the trigger interval for the onUserVoiceVolume callback to 100 ms// Turn on the volume level prompt
mNewCloud.enableAudioVolumeEvaluation(true, audioVolumeEvaluateParams);// Turn off the volume level prompt
mNewCloud.enableAudioVolumeEvaluation(false, audioVolumeEvaluateParams);
```

```
// AppDelegate.h@interface AppDelegate : UIResponder <UIApplicationDelegate, TRTCCloudDelegate> // Add TRTCCloudDelegate interface declaration@property (nonatomic, strong) TRTCCloud *trtcCloud; // Declare the trtcCloud instance// AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance];_trtcCloud.delegate = self;// Set the TRTCAudioVolumeEvaluateParams parametersTRTCAudioVolumeEvaluateParams *trtcAudioVolumeEvaluateParams = [[TRTCAudioVolumeEvaluateParams alloc] init];trtcAudioVolumeEvaluateParams.enablePitchCalculation = NO; // Enable local voice frequency calculationtrtcAudioVolumeEvaluateParams.enableSpectrumCalculation = NO; // Enable sound spectrum calculationtrtcAudioVolumeEvaluateParams.enableVadDetection = NO; // Enable local voice detectiontrtcAudioVolumeEvaluateParams.interval = 100; // Set the trigger interval of the onUserVoiceVolume callback to 100 ms// Enable volume level prompt[self.trtcCloud enableAudioVolumeEvaluation:YES withParams:trtcAudioVolumeEvaluateParams];// Implement TRTCCloudDelegate callback method- (void)onUserVoiceVolume:(NSArray<TRTCVolumeInfo *> *)userVolumes totalVolume:(NSInteger)totalVolume {    // Process user volume information    for (TRTCVolumeInfo *volumeInfo in userVolumes) {        NSLog(@"User ID: %@, Volume: %ld", volumeInfo.userId, (long)volumeInfo.volume);        // Update the UI here, such as updating the height of the volume bar    }}// Turn off the volume level prompt[self.trtcCloud enableAudioVolumeEvaluation:NO withParams:trtcAudioVolumeEvaluateParams];
```

```
// AppDelegate.h@interface AppDelegate : NSObject <NSApplicationDelegate, TRTCCloudDelegate> // Add TRTCCloudDelegate interface declaration@property (nonatomic, strong) TRTCCloud *trtcCloud; // Declare the trtcCloud instance// AppDelegate.m_trtcCloud = [TRTCCloud sharedInstance];_trtcCloud.delegate = self;// Set the TRTCAudioVolumeEvaluateParams parametersTRTCAudioVolumeEvaluateParams *trtcAudioVolumeEvaluateParams = [[TRTCAudioVolumeEvaluateParams alloc] init];trtcAudioVolumeEvaluateParams.enablePitchCalculation = NO; // Enable local voice frequency calculationtrtcAudioVolumeEvaluateParams.enableSpectrumCalculation = NO; // Enable sound spectrum calculationtrtcAudioVolumeEvaluateParams.enableVadDetection = NO; // Enable local voice detectiontrtcAudioVolumeEvaluateParams.interval = 100; // Set the trigger interval of the onUserVoiceVolume callback to 100 ms// Enable volume level prompt[self.trtcCloud enableAudioVolumeEvaluation:YES withParams:trtcAudioVolumeEvaluateParams];// Implement TRTCCloudDelegate callback method- (void)onUserVoiceVolume:(NSArray<TRTCVolumeInfo *> *)userVolumes totalVolume:(NSInteger)totalVolume {    // Process user volume information    for (TRTCVolumeInfo *volumeInfo in userVolumes) {        NSLog(@"User ID: %@, Volume: %ld", volumeInfo.userId, (long)volumeInfo.volume);        // Update the UI here, such as updating the height of the volume bar    }}// Turn off the volume level prompt[self.trtcCloud enableAudioVolumeEvaluation:NO withParams:trtcAudioVolumeEvaluateParams];
```

```
// .h filepublic:     ITRTCCloud* trtc_cloud_;public:     virtual void onUserVoiceVolume(TRTCVolumeInfo* userVolumes, uint32_t userVolumesCount, uint32_t totalVolume) override;// .cpp filetrtc_cloud_ = getTRTCSharedInstance();trtc_cloud_ -> addCallback(this); TRTCAudioVolumeEvaluateParams trtcAudioVolumeEvaluteParams;trtcAudioVolumeEvaluateParams.enablePitchCalculation = false; // Enable local voice frequency calculationtrtcAudioVolumeEvaluateParams.enableSpectrumCalculation = false; // Enable sound spectrum calculationtrtcAudioVolumeEvaluateParams.enableVadDetection = false; // Enable local voice detectiontrtcAudioVolumeEvaluateParams.interval = 100; // Set the trigger interval of the onUserVoiceVolume callback to 100 ms// Enable volume level prompttrtc_cloud_ -> enableAudioVolumeEvaluation(true, trtcAudioVolumeEvaluateParams);// Implement TRTCCloudDelegate callback method, replace CLASSNAME with your class namevoid CLASSNAME::onUserVoiceVolume(TRTCVolumeInfo* userVolumes, uint32_t userVolumesCount, uint32_t totalVolume) {    // Update the UI here, such as updating the height of the volume bar}// Turn off the volume level prompttrtc_cloud_ -> enableAudioVolumeEvaluation(false, trtcAudioVolumeEvaluateParams);
```

## Detect if remote users are speaking after being muted

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

## Adjust volume level

- **Local Audio:** The local microphone capture volume is set to 100 by default. You can call [setAudioCaptureVolume](https://trtc.io/document/50762#8326d139f429c00b542151923d12d579) to set the local audio capture volume.

Android

iOS

Mac

Windows

```
// Reduce the local microphone capture volume to 50mCloud.setAudioCaptureVolume(50);// Increase the local microphone capture volume to 100mCloud.setAudioCaptureVolume(100);
```

```
// Reduce the local microphone capture volume to 50[self.trtcCloud setAudioCaptureVolume:50];// Increase the local microphone capture volume to 100[self.trtcCloud setAudioCaptureVolume:100];
```

```
// Reduce the local microphone capture volume to 50[self.trtcCloud setAudioCaptureVolume:50];// Increase the local microphone capture volume to 100[self.trtcCloud setAudioCaptureVolume:100];
```

```
// Reduce the local microphone capture volume to 50trtc_cloud_ -> setAudioCaptureVolume(50);// Increase the local microphone capture volume to 100trtc_cloud_ -> setAudioCaptureVolume(100);
```

- **Remote Audio:**The remote user volume playback size is set to 100 by default. You can call [setRemoteAudioVolume](https://trtc.io/document/50762#dbc906d4b03074487cbd71cc4e7ff326) to set the playback volume of a specific remote user.

Android

iOS

Mac

Windows

```
// Reduce Tom's playback volume to 50mCloud.setRemoteAudioVolume("Tom", 50);// Increase Tom's playback volume to 100mCloud.setRemoteAudioVolume("Tom", 100);
```

```
// Reduce Tom's playback volume to 50[self.trtcCloud setRemoteAudioVolume:@"Tom" volume:50];// Increase Tom's playback volume to 100[self.trtcCloud setRemoteAudioVolume:@"Tom" volume:100];
```

```
// Reduce Tom's playback volume to 50[self.trtcCloud setRemoteAudioVolume:@"Tom" volume:50];// Increase Tom's playback volume to 100[self.trtcCloud setRemoteAudioVolume:@"Tom" volume:100];
```

```
// Reduce Tom's playback volume to 50trtc_cloud_ -> setRemoteAudioVolume("Tom", 50);// Increase Tom's playback volume to 100trtc_cloud_ -> setRemoteAudioVolume("Tom", 100);
```

> **Note:**The recommended value range for **volume** is 0 - 100. If the volume still feels too low after setting it to 100, you can set the maximum volume to 150. However, setting the volume above 100 carries the risk of distortion. Please proceed with caution.

## Contact Us

If you have any requirements or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/64697](https://trtc.io/document/64697)*
