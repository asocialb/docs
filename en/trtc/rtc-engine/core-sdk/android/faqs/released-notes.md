# Released Notes

This page includes the version history of TRTC SDK and All-In-One SDK. Please choose the ideal SDK according to your function needs.

#### TRTC SDK 13.1 Released on Jan 29, 2026

#### New features

- All Platforms: Supported AI real-time transcription and translation capabilities.
- Android & iOS: Camera capture now supports video stabilization capability.
- Mac: The C++ custom sending interface now supports CVPixelBuffer data type.

#### Bug fixing

- Mac: Fixed screen sharing issue where sharing WPS with a PDF open would cause black screen flickering.
- Mac: Fixed speaker mode failure issue when sharing on secondary screen.
- Android: Fixed hardware decoding compatibility issue for certain MediaTek chipset devices with small resolutions.

#### Interface behavior adjustment

- All Platforms: Added the AITranscriberManager interface for AI real-time transcription and translation

#### TRTC SDK 13.0 Released on Dec 18, 2025

#### New features

- iOS & Mac: Changed to dynamic library for iOS/Mac SDK.
- OHOS: Support system audio mixing capability.
- ITXLocalMediaTranscoding supports macOS systems.

#### Improvements

- All Platforms: Optimize the AI noise reduction speech protection model to address issues related to the loss of initial characters and characters in low signal-to-noise ratio environments.
- All platforms: Encode output width and height shall be 2-byte aligned by default.

#### Bug fixing

- Android: The issue of playing silently in the background for a long time on Xiaomi models.
- Android: Fixed the issue where the Bluetooth headset becomes unusable after the call function is disabled in the system settings.
- Mac: Fixed screen sharing failure in Presenter Mode.
- iOS: Fixed occasional beauty effect anomaly when toggling between foreground and background repeatedly with custom preprocessing enabled.

#### TRTC SDK 12.9 Released on Nov 13, 2025

#### Improvements

- Windows: Improve the success rate of professional sound card recognition to over 90%.
- Windowsï¼After adding a video source, ITXLocalMediaTranscoding will report the playback progress through the onVideoFilePlayProgress callback, and supports seeking operations on the video source.

#### Bug fixing

- Android: Optimized the issue where camera interruptions on specific devices could not be restored.
- Android: Fixed abnormal screen sharing display during landscape-portrait switching.
- Windows: Improved the screen sharing feature to automatically track full-screen PPT windows.

#### TRTC SDK 12.8 Released on Sep 25, 2025

#### New features

- ITXLocalMediaTranscoding supports video files and live streaming sources as inputs for video composition.
- Ohos: HarmonyOS supports the Picture-in-Picture mode feature.

#### Improvements

- Full platform: Implement a version of the reverberation effect algorithm to enhance the overall auditory experience of reverberation effects.
- Full platform: Optimize the issue of excessive memory allocation in the bgm module, which is prone to triggering out-of-memory (oom) issues.
- Full platform: Optimize the mixing effect of background music (BGM) and on-screen voice.
- Windows: Optimized the overall CPU performance of the uplink D3D pipeline for Windows.

#### Bug fixing

- Full platform: When optimizing the uneven timestamps of custom audio capture, the time jitter of upstream audio frames causes stuttering in playback streams on some browsers.
- Windows: Fixed the crash issue of the streaming library supporting AI capabilities on low-end chips.
- Ohos: Fixed rendering-related bugs on the HarmonyOS platform.
- Windows: Fixed low-end GPU compatibility on Windows.

#### Interface behavior adjustment

- Desktop: Optimize the callback content of the audio data monitoring interface onMixedAllAudioFrame to make it consistent between macOS and Windows.

#### TRTC SDK 12.7 Released on Aug 13, 2025

#### New features

- Windows: The ITXLocalMediaTranscoding interface adds the setMixedVideoRenderFillMode method, used to configure the fill mode for mixed video rendering.
- Windows: When rendering, the ITXLocalMediaTranscoding interface displays the distance between input sources and borders.
- Mobile terminal: Support KTV scenarios, with a focus on optimizing the sound quality and effect of KTV and chorus.
- Mobile: If the camera is interrupted after a customer sets a placeholder, the SDK will default to pushing the placeholder stream internally.

#### Improvements

- Full platform: Optimize the sound card to use stereo sound in a connected microphone environment without echo.
- Android: Optimize the aliasing effect issue on small-resolution screens.

#### Bug fixing

- Full platform: Fixed the issue of uneven timestamp correction during audio custom capture jitter
- iOS: Fixed an issue where frequent switching between foreground and background during screen recording on iOS 18.5 caused sharing to fail without triggering a callback event.

#### Interface behavior adjustment

- Android: Remove the enumeration values of TXAudioRouteWiredHeadset and TXAudioRouteBluetoothHeadset from TXAudioRoute.

#### TRTC SDK 12.6 Released on Jul 01, 2025

#### New features

- Full platform: The voice changing library supports the effects of Hulk and Pigsy.

#### Improvements

- Android: Supports the ability to switch between headphones, external speakers, and earpiece at low call volume.
- iOS: After the system phone is interrupted and restored, the device recovery speed is increased to within 2 seconds.
- Windowsï¼Optimize the problem of residual log in log view.
- Android & iOS: Supports gesture zoom functionality.
- Windows: Optimizes NVIDIA GPU encoding mode to improve encoding efficiency.

#### Bug fixing

- Fixed the issue of external placement when switching the Xiaomi 11pro wired earphones to Bluetooth earphones.

#### TRTC SDK 12.5 Released on May 12, 2025

#### Improvements

- Full platform: Reduce the frequent creation of large blocks of memory, and reduce the crash rate by 50% in low-memory scenarios.
- Android: optimize stereo sound quality.
- iOS: Improve the sound card recognition rate.

#### Bug fixing

- Android: Fixed black screen issues caused by adjusting screen sharing resolution between landscape and portrait modes on certain devices.
- Android: Fixed abnormal local preview display when setting landscape mode via Activity.
- Windows: Fixed black screen issues caused by D3D11 pixel format conversion failures.

#### Interface behavior adjustment

1. Behavior Adjustment for setLocalRenderMode Interface.
- VIDEO_MIRROR_MODE_AUTO (0) (Auto Mode): If the front-facing camera is in use, mirroring is enabled by default for both local and remote views.If the rear-facing camera is in use, mirroring is disabled for both local and remote views (Applies only to mobile devices).
- VIDEO_MIRROR_MODE_ENABLED (1) (Force Enable Mirroring): Mirroring is forcibly enabled for both local and remote views, regardless of whether the front or rear camera is used.
- VIDEO_MIRROR_MODE_DISABLED (2) (Force Disable Mirroring): Mirroring is forcibly disabled for both local and remote views, regardless of whether the front or rear camera is used.
2. SetVideoEncoderMirror is no longer recommended for use. If called, it will only affect the remote video stream and will no longer affect the local preview.
3. In custom video capture and screen-sharing scenarios:the setVideoEncoderMirror and setVideoEncoderRotation interfaces will no longer take effect.

#### TRTC SDK 12.4 Released on Apr 01, 2025

#### New features

Local media transcoding support setting border color.

#### Improvements

- All Platforms: Optimize VAD precision in TRTCVolumeInfo status parameters.
- Android: Supports Low Energy Bluetooth (BLE) connection.
- Mac: Full-screen capture with highlighted border filtering.

#### Bug fixing

- Android: Fixed an issue where some devices would switch to speaker mode when changing headphones while the microphone was activeã
- All Platforms: Fixed the 'Cold Voice' sound effect muting issueã
- Android & iOS: Camera supports a Long-Time No-Frame Detection Strategyã

#### Interface behavior adjustment

1. Custom Preprocessing Format Matching Logic Adjustment.
- The TRTCVideoPixelFormat_Texture_2D format is internally mapped to RGBA32.
- TRTCVideoBufferType_Texture only supports combination with TRTCVideoPixelFormat_Texture_2D.
2. iOSï¼Screen Sharing Updates System Triggered Pause/Resume Reason.
- Pause Event: When screen sharing is active and the user taps the system's stop Screen Recording button, onScreenCapturePaused Callback reason code: -4.
- Resume Event: When screen sharing is paused and the user taps the system's start Screen Recording button, onScreenCaptureResumed Callback reason code: -4.

#### TRTC SDK 12.3 Released on Jan 22, 2025

#### New features

Android:

- Separate the screen sharing function into an independent aar named LiteAVSDK_VideoScreenCapture.
- If you integrate it through local aar, you need to integrate the new aar into the project synchronously.
- If you integrate it through Maven, it can be automatically downloaded without modification. If you do not need the screen sharing function, please remove LiteAVSDK_VideoScreenCapture in the gradle configuration file by excluding it.

#### Improvements

- Windows: Optimize decoding performance when enabling custom rendering mode.
- Windows: Improve the multi-GPU selection strategy.
- Android: Implement a restart strategy when no frames are captured.
- All Platforms: Optimize the volume range from 100~150 and adjust the upper limit of gain from 8dB to 12dB.
- All Platforms: Enhance weak network resilience in pure audio scenarios.
- All Platforms: Optimize the alignment effect of vocals and BGM in KTV scenarios.

#### Bug fixing

- iOS: Optimize the stuck of video hardware encoding issue on iOSã
- Mac: Resolve the issue where the microphone switch causes Loopback to produce no sound.
- Mac: Fix the problem of not automatically switching to newly connected headphones.
- Windows: Fix the issue where switching microphones causes the app to freeze on Windows 7.
- All Platforms: Fix the issue where BGM stutters for the remote side when the BGM volume is extremely low.

#### TRTC SDK 12.2 Released on Nov 27, 2024

#### New features

- Android: Support for 16K page sizes on Android 15.
- All Platforms: Detect network link quality in real time and automatically switch to a better link.

#### Improvements

- Android: Hardware monitor support for more phone brands: Xiaomi, OPPO, OnePlus, Honor.
- iOS: Optimize focus effects under automatic exposure.
- iOS: Optimize image quality after video zoom.
- Full platform: Optimize sound effects under Speech audio quality.

#### Bug fixing

- Fixed the audio loopback capture failure issue on macOS 15.
- Fixed the issue where the screen capture authorization window fails to pop up on Android.
- Fixed several compatibility issues with Windows hardware encoders.

#### Interface behavior adjustment

- iOS & Android: API TRTCCloud::generateCustomPTS adjusted to a static interface.
- Android & iOS & Windows: Add rendering mode TRTCVideoFillMode_ScaleFill mode, see TRTCVideoFillMode.

#### TRTC SDK 12.1 Released on Oct 8, 2024

#### New features

- Windows: Intel GPUs now support H.265 encoding and B-frame encoding.
- Windows: Nvidia GPUs support ROI (Region of Interest) capability.

#### Improvements

- All Platforms: Optimize noise reduction and echo cancellation algorithms to enhance audio quality.
- All Platforms: Optimize the AGC (Automatic Gain Control) volume curve to prevent audio clipping.
- All Platforms: Enhance weak network resistance in pure video scenarios.
- Android: Optimized device initialization parameters, significantly enhancing audio capture stability.
- iOS: Improve call volume and audio quality.

#### Bug fixing

- Android: Fixed the issue where custom-captured video frames rotation angles were not effective.
- Android: Fixed the occasional failure of screen sharing in Android 14.
- Android: Fixed the black screen issue caused by failed video capture on Android devices.
- Windows: Fixed the issue where the system audio loopback stereo effect is ineffective.
- Windows: Fixed the issue of silent capture on specific devices.
- Fixed the issue of noise in earpiece feedback when Bluetooth headsets are used on iOS/Mac.

#### TRTC SDK 12.0 Released on Aug 20, 2024

#### New features

- Improving video encoding quality on iOS.
- Support for custom reverb parameters.

#### Improvements

- Support for gravity sensing in UIFixLayout mode on mobile devices.
- Optimized audio and video transmission performance under extremely poor network conditions.
- Protect the speaker's voice with AI noise reduction.
- The callbacks for the current audio routing type are also available on mobile platforms.
- Intelligent encoding for different speech materials to save bandwidth.
- Android now supports professional sound card recognition and reduces audio quality loss for broadcasters.
- Supports excluding the mixing of a specific process with the system audio loopback on Windows.

#### Bug fixing

- Android: Fixed the issue where the GLContextDestroy callback was missed when stopping local capture..
- Android: Fixed the issue where setting ResolutionMode on part of learning devices was ineffective.
- Full platform: Fixed the issue where setting the sample point frame length in onMixedPlayAudioFrame caused noise.
- iOS: Fixed the issue where calling stopLocalAudio during the microphone prompt resulted in no sound.

#### Interface behavior adjustment

- Documentation update: Changes in the usage of the screen capture interface on Android 14 , please refer to the API documentation for details on startScreenCapture.
- If you need to use the screen sharing feature, you will need to fill out the declaration in the Play Console as per Google's requirements. Please refer to the following documentation for more information.

#### TRTC SDK 11.9 Released on June 12, 2024

#### New features

- Full platform: Optimized AI denoise effect, significantly improving performance in internet bars, meetings, and other scenarios.
- Full platform: Supports the APE BGM file.
- Full platform: Improved the accuracy of existing operational events, enhancing troubleshooting efficiency for silent or low-volume abnormal scenarios.
- iOS & Android: Support for high-definition screenshot.
- iOS: TXDeviceManager adds a new API setCameraCapturerParam (API url) for setting capture parameters.

#### Bug fixing

- Android: Resolved the occasional electronic noise issue during microphone capture.
- Full platform: Fixed stability issues caused by specific BGM formats and illegal data.
- Android: Resolved the occasional low volume issue in speaker mode.
- Windows: Fixed the issue of occasionally retrieving the incorrect current camera.

#### TRTC SDK 11.8 Released on May 10, 2024

#### New features

iOS: Supports picture-in-picture feature.

#### Improvements

- Android: Optimized audio compatibility issues and added support for more comprehensive device selection routes.
- Windows: Optimized AI noise reduction performance.
- Windows: Improved upstream video quality in single anchor scenarios.
- Full platform: Optimized BGM error message prompts.
- Windows: Optimizing the display scaling effect.

#### Bug fixing

- Android: Optimized the issue of low speaker volume.
- Mac: Fixed the issue of no sound when killing the process with Loopback open.
- Mac: Fixed the issue of no sound when connecting to HDMI or DisplayPort.
- Windows: Fixed the issue where switching between different audio quality types caused AGC to fail.
- Android: Screen sharing adapted for high TargetVersion.

#### Interface behavior adjustment

Full platform: The C++ interface supports the onMixedAllAudioFrame callback.

#### TRTC SDK 11.7 Released on Mar 4, 2024

#### New features

- Full platform: Add new Warning codes for camera capture.
- Full platform: Adjust the gravity sensing API, see setGravitySensorAdaptiveMode .
- Full platform: Support callback for local voice volume information, see enableAudioVolumeEvaluation.

#### Improvements

- Full platform: Optimize room entry process to significantly reduce the time taken for secondary room entry.
- Full platform: Dashboard monitors the maximum number of end-to-end call quality for a single user, increasing from 16 to 50 channels.
- Android: Optimize the parameters and calling order of the system capture audio API to reduce the probability of capturing only noise and improve the sound capture effect.
- iOS: Optimize the capture restart logic after system interruption to reduce the probability of capturing silence.
- iOS: Optimize Unity 3D engine compatibility issues.
- iOS: Improve the focusing effect of rear triple and dual camera capture, increasing the focusing speed.

#### Bug fixing

- Android: Fix some echo leakage cases.
- Android: Fix some Bluetooth interruptions causing external playback issues.

#### Interface behavior adjustment

- Full platform: When the API switchRole is frequently called, only the last call result is returned in onSwitchRole.
- Full platform: Add camera capture warning codes.

| Warning Code | Description |
| --- | --- |
| WARNING_CAMERA_IS_OCCUPIED = 1114 | The camera is occupied by other process |
| WARNING_CAMERA_DEVICE_ERROR = 1115 | The camera device is error |
| WARNING_CAMERA_DISCONNECTED = 1116 | The camera is disconnected |
| WARNING_CAMERA_START_FAILED = 1117 | The camera is started failed |
| WARNING_CAMERA_SERVER_DIED = 1118 | The camera sever is died |

- Full platform: Adjust the default frame rate for the setVideoMuteImage interface from 0fps to 5fps, and limit the maximum frame rate to 10fps.
- iOS: Change the behavior of the API setSubStreamEncoderParam from setting screen sharing encoding parameters to setting auxiliary stream encoding parameters.
- Windows: Change the default highlight color (highLightColor) in the selectScreenCaptureTarget from green to yellow.
- Full platform: Adjust the gravity sensing API:

| New API | (void)setGravitySensorAdaptiveMode:(TRTCGravitySensorAdaptiveMode)mode; | See Doc |
| --- | --- | --- |
| Deprecated API | setVideoEncoderRotation | Deprecated |
|  | setVideoEncoderMirror | Deprecated |
|  | setGSensorMode | Deprecated |

#### TRTC SDK 11.6 Released on Jan 15, 2024

#### New features

- iOSï¼Added Picture-in-Picture support for `TXLivePlayer`.
- Windows: Added support for capturing audio from specific application. For more details, see startSystemAudioLoopback.

#### Improvements

- Android & iOS: Optimized the success rate of playing BGM with URL.
- Windows: Optimized and adapted to Intel HEVC software decoder (Quick Sync Video).
- Full platform: Optimized poor network performance of audio in low-bandwidth conditions.
- Full platform: Optimized poor network performance of video in low-bandwidth conditions.
- Full platform: Optimized poor network audio quality under high packet loss and high latency conditions.
- Full platform: Optimized SDK overall stability.

#### Bug fixing

- Android: Fixed occasional slow decoding of the first frame when `switchRoom` is called frequently..
- Android: Fixed occasional incorrect screen scaling when trying to `startScreenCapture` again in a single session.Windows: Fixed the issue that some virtual cameras fail to capture when setting vertical resolution.

#### TRTC SDK 11.5 Released on Nov 27, 2023

#### Improvements

- Full platform: Optimized the performance and stability of the video engine.
- Full platform: Optimized the stability of the audio engine.
- Full platform: Optimized the behavior strategy of some APIs, see the adjustment of interface behavior for details.
- Full platform: Optimized the strategy and performance of the background music module (BGM module), reducing the occurrence of BGM playback exceptions.
- Windows: Optimized HEVC hardware decoding compatibility with AMD and Nvidia graphics cards.
- Windows: Optimized the overall performance of screen sharing, improved screen capture frame rate and stability.
- Android: Optimized the playback effect of TRTC with VODPlayer.
- iOS & Mac: Optimized the performance of pre-processing and rendering using Metal.

#### Adjustment of Interface Behavior

- Full platform: When the video resolution is set to vertical 540P (expecting 540x960), the specific resolution for processing is adjusted from 544x960 to 536x960.
- Full platform: The callback interval of BGM progress callback `onPlayProgress` is adjusted from 200ms to 300ms.
- Full platform: The internal implementation of the BGM module is adjusted to a singleton, and the musicID needs to be globally unique in multiple instances. When developers use sub-instances to play BGM, please make sure that different instances use different musicIDs.
- Full platform: Local recording event status codes are adjusted to be returned asynchronously. The default return is 0 after the related interface is called, and the specific status code is obtained through the corresponding event callback.
- Full platform: Adjust the following status codes for the `onLocalRecordBegin` callback for starting recording events.

| Event | Status code before v11.5 | Status code in v11.5 |
| --- | --- | --- |
| Recording has started, stop previous recording first | -1 | -6 |
| Directory has no write permission, please check directory permissions | -2 | -8 |
| Incorrect file extension (e.g. unsupported recording format) | -3 | -2 |

- iOS & Android: Optimized the continuity of mobile screen sharing, retaining the last frame sent during sharing pause, with a frame rate of 1-2 fps.
- iOS & Android: Adjusted the response behavior of gravity sensor, only responding to gravity sensor on or off.

### TRTC SDK 11.4 Released on Sep 14, 2023

#### New features

- Full platform: `TRTCLocalRecordingParams` adds a new parameter `max_duration_per_file` to control the duration of segmented recording. The path of the segmented file can be obtained through the `onLocalRecordFragment` callback.
- Android & iOS: V2TXLivePusher adds a rendering mode setting API `setRenderFillMode` for local preview streaming.
- Mac: Added `enableCrashMonitoring` to support capturing crash information and storing it locally. You need to add `TXCCrashMonitor.framework` to your project when using this feature.

#### Improvements

- Cross-platform: Optimized performance in IPv6 network environments.
- Cross-platform: Optimized lyric alignment in the online singing scenario.
- Cross-platform: Optimized AI noise suppression algorithm for better experience.
- Cross-platform: Optimized the smoothness of pure audio playback.
- Â Cross-platform: Optimized the speed of `switchRoom`.
- Android & iOS: Optimized and improve the live streaming playback startup speed.
- Android & iOS: Optimized audio capture processing strategies to reduce the probability of no audio issue caused by abnormal capture devices.
- Android: Optimized callback notifications when the microphone is muted by the system.
- Android: Optimized the adaptation of gravity sensor for specific customized Android devices that were providing incorrect screen rotation angles.
- Android: Optimized the rendering process to support closely following pinch-to-zoom, which means the view undergoes simultaneous scales and moves, closely following the movements of the fingers during pinch-to-zoom. Improving the user experience during floating window playback.
- iOS: Optimized the audio capture strategy when app in the background state to reduce the probability of no audio issue caused by system interruption.
- iOS: Optimized the speed of audio device restarts.

### TRTC SDK 11.3 Released on July 7, 2023

#### New features

- All Platforms: Added trapezoid correction for video (only supported by the Professional version) for manual correction of perspective distortion. See `setPerspectiveCorrectionPoints` for details.
- All Platforms: Added audio spectrum callback, which can be used for sound wave animation or volume spectrum display. See `enableAudioVolumeEvaluation` and `TRTCVolumeInfo` for details.
- All Platforms: Added a new reverb effect "Studio 2". See `TXVoiceReverbType` for details.
- All Platforms: Added SEI parameter settings for mixed stream, used for transport SEI information when publishing stream to CDN. See `TRTCTranscodingConfig` for details.
- Windows: Added real-time music scoring for Yinsuda Authorized Music, which can be used for real-time scoring of online singing. See `createSongScore` for details.
- iOS & Android: Added support for .ogg format music files in `startPlayMusic`.
- Flutter: Added `setSystemAudioLoopbackVolume`(iOS).

#### Improvements

- Full platform: Optimized adaptive digital gain algorithm to improve listening experience.
- Full platform: Optimized the loading speed of the first video frame after entering the room.
- Full platform: Optimized weak network resistance for single user streaming to improve smoothness under network delay and jitter.
- Android: Optimized audio capture and playback feature to avoid abnormal sound issues on some Android devices.
- Android: Optimized video sub-stream hardware encoding performance, improving quality of screen sharing.
- iOS: Optimized audio device restart strategy to reduce the occurrence of sound interruptions.
- iOS & Android: Removed on-demand related interfaces from `TXLivePlayer`. For on-demand video playback, please use `TXVodPlayer`.

#### Bug fixing

- Android: Fixed the issue where some locally recorded videos on Android 12 and above system versions cannot be played on Apple's Safari.

### TRTC SDK 11.2 Released on June 5, 2023

### TRTC

#### New features

- Cross-platform: Supports seamless switching between instrumentals and original vocals of BGM in duet scenes. See `setMusicTrack` for details.
- Android: To be compatible with the foreground service launch restrictions on Android 12 and above, a foreground service is initiated during screen capture. See `enableForegroundService` for details.
- iOS: Supports use in the Xcode simulator running on Apple chip hardware.
- Mac: `TRTCScreenSourceInfo` adds property value width and height.

#### Improvements

- Cross-platform: Optimized sound quality in duet scenes, and reduced end-to-end latency.
- Cross-platform: Optimized performance when turning on/off microphone, providing a smoother experience.
- Cross-platform: Optimized audio experience under extremely bad networks.
- Cross-platform: Optimized weak network experience when broadcast live stream only.
- Cross-platform: Optimized the smoothness of switching high-quality and low-quality remote video streams.
- Android & iOS: Optimized audio quality in music scenes.
- Android & iOS: Optimized the experience with Bluetooth headphones.
- Android: Optimized hardware decoder latency, improving the speed of rendering the first video image.
- Android: Optimized the in-ear monitoring feature, enhancing the experience when switching on/off in-ear monitoring.
- Android: Optimized the audio devices capture compatibility.
- iOS: Optimized quality of video, enhancing image clarity.

#### Bug fixing

- Windows: Fixed the occasional screen flickering issue during window sharing.
- Mac: Fixed the occasional periodic blurring when using camera with Intel chip hardware encoder.

## TRTC SDK 10.8 Released on October 27, 2022

### TRTC

#### New features

Full platform: Added the DJ scratch effect and improved the karaoke experience. For details, see `TXAudioEffectManager.setMusicScratchSpeedRate`.

#### Improvements

Android: Sped up video decoding, which reduces the time to first frame to as short as 50 ms.

Full platform: Improved the accuracy of NTP time. For details, see `TXLiveBase.updateNetworkTime`.

#### Bug fixing

- Full platform: Fixed the occasional issue where, when the streams of a room are mixed and pushed to another TRTC room that does not have upstream audio or video, playback fails and callbacks stop working.
- Full platform: Fixed the occasional issue where, after an audience member changes their role upon room entry, they fail to publish audio and video due to network type change.
- Full platform: Fixed the issue where, after a disconnection, audio quality cannot be changed during reconnection.
- Full platform: Fixed the issue where, after a disconnection, there is sometimes no audio in the published stream during reconnection.
- Android & iOS: Fixed the issue where `muteRemoteVideoStream` removes the last video frame.

## TRTC SDK 10.7 Released on September 20, 2022

### TRTC

#### New features

- Full platform: You can now independently adjust the audio volume of each stream in On-Cloud MixTranscoding. For details, see `TRTCMixUser.soundLevel`.
- Full platform: Added the `onRemoteAudioStatusUpdated` API, which is used to monitor the audio status of remote streams.

#### Improvements

- Full platform: Upgraded the encoding engine, improving the video quality of screen sharing streams.
- Full platform: Improved rate control for encoding under poor network conditions.

#### Bug fixing

- iOS: Fixed the issue of low capturing volume on some iPad devices.
- Android: Fixed the occasional issue where Bluetooth earphones are connected, but audio is played from the deviceâs speaker.
- Full platform: Fixed the issue where the SDK occasionally crashes if a user enters and leaves the room repeatedly.

## TRTC SDK 10.6 Released on September 9, 2022

### TRTC

#### Improvements

- Full platform: Sped up room entry in IPv6 networks.
- Full platform: Improved the audio recovery performance and audio-to-video synchronization under bad network conditions, enhancing user experience.
- Full platform: Improved the ability to maintain connection under poor network conditions, reducing disconnections.
- Full platform: Fixed the issue where the volume is low in the music mode (which is specified when `startLocalAudio` is called).
- macOS: Improved call experiences when Bluetooth earphones are used, reducing noise and delivering clearer audio.
- Android: Supported stereo audio capturing for more devices.
- Android: Fixed occasional echoes, improving call experience.

#### Bug fixing

- Android & iOS: Fixed the issue of audio loss in the speech mode (which is specified when `startLocalAudio` is called).
- macOS: Fixed the issue where echo cancellation occasionally fails to work after the mic is changed.

## All-in-One SDK 10.5 Released on August 24, 2022

### MLVB

#### Improvements

- Android: Optimized memory management for video decoding, preventing the accumulation of memory leaks.
- Windows: Optimized noise suppression for the built-in mic, especially in the music mode.
- macOS: Fixed the frequent noise issue when the mic is turned on.

#### Bug fixing

- Full platform: Fixed the issue where, in the LEB scenario with V2TXLivePlayer, SEI messages are sometimes not received.
- Full platform: Fixed the issue where, in the LEB scenario with V2TXLivePlayer, audio is missing because the timestamp moves backward.

### UGSV

#### Bug fixing

- Android: Fixed the green screen issue in videos made from pictures on HarmonyOS.
- Android: Fixed the issue of incorrect length for edited videos.
- Android: Fixed failure to play or re-encode videos with multiple audio tracks.
- Android: Fixed the issue where the ârock lightâ effect is applied only once during the selected time period.
- Android & iOS: Fixed the issue where, after a video segment is deleted during shooting, the playback progress of the background music does not match.

### TRTC

#### Improvements

- Full platform: Optimized the QoS control policy, enhancing user experience under poor network conditions.
- iOS & Android: Reduced end-to-end latency and improved in-ear monitoring experience.
- Android: Optimized memory management for video decoding, preventing the accumulation of memory leaks.
- Windows: Optimized noise suppression for the built-in mic, especially in the music mode.
- macOS: Fixed the frequent noise issue when the mic is turned on.

#### Bug fixing

Full platform: Fixed occasional errors for the [OnUserVideoAvailable](https://liteav.sdk.qcloud.com/doc/api/en/group__TRTCCloudListener__android.html#ac1a0222f5b3e56176151eefe851deb05) and [OnUserAudioAvailable](https://liteav.sdk.qcloud.com/doc/api/en/group__TRTCCloudListener__android.html#ac1a0222f5b3e56176151eefe851deb05) callbacks when a user enters and leaves different rooms consecutively.

### Player

#### Bug fixing

Android & iOS: Fixed failure to play URLs that do not include video formats at the end.

## All-in-One SDK 10.4 Released on July 25, 2022

### MLVB

#### New features

iOS & Android: V2TXLivePlayer can now freeze the last frame after playback ends.

#### Improvements

- Full platform: Fixed the issue of high memory usage when TXLivePlayer\\V2TXLivePlayer plays FLV streams.
- Android: Fixed occasional playback stutter with TXLivePlayer\\V2TXLivePlayer.
- Android: Improved the compatibility of low-latency in-ear monitoring and dual-channel capturing.
- Android: Optimized the policy for switching from hardware to software decoding.
- iOS: Fixed the issue of low capturing volume on iPad.

#### Bug fixing

Android: Fixed the issue where TXLivePlayer\\V2TXLivePlayer occasionally switches to software decoding when playing streams.

### UGSV

#### Improvements

Android: Added the `setBGMLoop` API for video editing.

#### Bug fixing

- Android: Fixed the issue of `setWaterMark` not working.
- Android: Fixed the issue where, when videos are previewed, TXVideoEditor fails to use the specified rendering mode.

### TRTC

#### New features

- iOS & Android: Added support for the RGBA32 format for custom capturing. For details, see `sendCustomVideoData`.
- Windows & macOS: Added support for watermark preview after configuration. For details, see `setWaterMark`.

#### Improvements

- Android: Improved the compatibility of low-latency in-ear monitoring and dual-channel capturing.
- Android: Optimized the policy for switching from hardware to software decoding.
- iOS: Fixed the issue of low capturing volume on iPad.

#### Bug fixing

- Full platform: Fixed occasional room entry/exit callback errors.
- Windows: Fixed the issue where, after the window shared changes, the new window is not displayed in full.

### Player

#### Improvements

Android & iOS: Added support for adaptive bitrate HLS playback.

#### Bug fixing

- Android: Fixed abnormal intervals for the `onNetStatus` callback and the progress callback.
- Android: Fixed the null pointer exception caused by failure to call `setConfig`.
- iOS: Fixed the stuttering issue when videos are replayed in some scenarios.

## All-in-One SDK 10.3 Released on July 8, 2022

### MLVB

**New features:**

Full platform: TXLivePlayer\\V2TXLivePlayer added support for HLS playback.

**Improvement:**

- Full platform: Improved audio quality in the music mode.
- Full platform: Optimized the SEI parsing logic. TXLivePlayer\\V2TXLivePlayer can parse some non-standard SEI messages now.
- Full platform: Fixed the issue of audio and video being out of sync as a result of the timestamp moving backward when TXLivePlayer\\V2TXLivePlayer plays FLV or RTMP streams.

**Bug fixing:**

- Full platform: Fixed the abnormal audio that occurs when TXLivePlayer\\V2TXLivePlayer plays some AAC-HEv2 streams in the LEB scenario.
- Full platform: Fixed incorrect cache calculation with TXLivePlayer.

### UGSV

**Bug fixing:**

- Android: Fixed the issue of `setZoom` not working during video shooting.
- Android: Fixed failure to shoot videos with Samsung Galaxy S22.
- iOS: Fixed failure to trigger the callback for custom video pre-processing.

### TRTC

**New features:**

- Windows: Added support for recording live streaming sessions and audio/video calls to local storage. For details, see the description of `ITXLiteAVLocalRecord`.
- Windows & macOS: Added a parameter to `startMicDeviceTest`, which allows you to specify whether to play the audio captured during mic testing. For details, see the description of `startMicDeviceTest`.

**Improvement:**

Full platform: Improved audio quality in the music mode.

**Bug fixing:**

- Full platform: Fixed occasional errors for the user list callback.
- Windows: Fixed the issue where videos sometimes freeze during playback.
- Windows: Fixed occasional video playback failure.
- Windows: Fixed the echo issue for custom audio capturing.

### Player

**New features:**
iOS: Added support for picture-in-picture playback.

**Bug fixing:**

- Android: Fixed the issue where, when hardware decoding is used and a video playlist is played in the background, the player fails to automatically play the next video when one video is finished.
- Android & iOS: Fixed failure to trigger the callback when seeking is completed.

## All-in-One SDK 10.2 Released on June 26, 2022

### MLVB

**New features:**

- Full platform: Added support for license authentication for playback with TXLivePlayer\\V2TXLivePlayer.
- Full platform: Added support for HTTP header configuration for FLV playback with V2TXLivePlayer.
- Full platform: Allowed changing audio encoding parameters dynamically when pushing RTMP streams with TXLivePusher\\V2TXLivePusher.

**Improvement:**

- Full platform: Optimized the adaptive bitrate API of V2TXLivePlayer for LEB.
- Full platform: Fixed the issue where V2TXLivePlayer takes a long time to reconnect in the LEB scenario.
- Full platform: Fixed the issue of small local cache size when TXLivePlayer\\V2TXLivePlayer plays FLV or RTMP streams.
- Android: Sped up the loading of the first frame for playback with TXLivePlayer\\V2TXLivePlayer.
- iOS: Reduced the size of the iOS SDK package.
- iOS: Packaged `TXLiveBase.h` into the MLVB SDK.

**Bug fixing:**

- Full platform: Fixed the issue where the stutter rate limit configured for TXLivePlayer does not take effect.
- Full platform: Fixed abnormal timing of the callback for the first audio/video frame when V2TXLivePusher pushes RTC streams.
- Android: Fixed the black screen issue that occurs when TXLivePlayer\\V2TXLivePlayer stops and starts playback within a short period of time.

### UGSV

**New features:**

Android: Added support for editing videos without audio tracks.

**Improvement:**

Android: Sped up the loading of the first frame for short video playback.

**Bug fixing:**

- Android: Fixed the issue where the wrong section of video is cropped during video shooting.
- Android: Fixed incorrect aspect ratio for H.265 videos decoded with hardware.
- iOS: Fixed the issue of incorrect video clipping time.
- iOS: Fixed occasional noise that occurs in videos shot with devices with OS later than iOS 14.
- iOS: Fixed the issue where the SDK occasionally crashes when the user returns to the shooting view after finishing video shooting.

### TRTC

**New features:**

- Full platform: Launched a new API for stream mixing and relaying, which offers more powerful features and greater flexibility. For details, see the description of `startPublishMediaStream`.
- Full platform: Added support for 3D spatial audio. For details, see the description of `enable3DSpatialAudioEffect`.
- Full platform: Added support for voice activity detection. This feature works even when local audio is muted (`muteLocalAudio`) or the capturing volume is set to zero (`setAudioCaptureVolume`). It allows you to remind users when they are talking but have not turned their mics on. For details, see the description of `enableAudioVolumeEvaluation`.
- Full platform: Added support for checking a userâs permission when they switch roles. For details, see the description of `switchRole(TRTCRoleType role, const char* privateMapKey)`.
- iOS & macOS: The C++ API for custom pre-processing supported using textures for video processing.

**Improvement:**

- Android: Optimized in-ear monitoring, reducing latency.
- Android: Optimized audio capturing, fixing the issue of noise on some devices.
- iOS: Optimized the processing of upstream video data, reducing CPU and GPU usage.
- Windows & macOS: Improved encoding for screen sharing. The height and width of the output video are no longer limited by the window size.
- Windows: Reduced memory fragmentation and performance overhead.

**Bug fixing:**

- Full platform: Fixed the issue where push occasionally fails after changing to a different type of network.
- iOS: Fixed the issue of noise in recording files saved locally on some devices with iOS 14.

### Player

**Improvement:** 
Android & iOS: Optimized the callback of information including cached bytes and IP address during playback.

**Bug fixing:**

- Android & iOS: Fixed failure to play H.265 videos when hardware decoding is used.
- Android & iOS: Fixed HLS playback errors.
- iOS: Fixed failure to get `supportedBitrates` in some scenarios.


---
*Source: [https://trtc.io/document/39426](https://trtc.io/document/39426)*
