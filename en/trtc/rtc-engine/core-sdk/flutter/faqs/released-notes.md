# Released Notes

## Version 2.8.6 @ Aug 12, 2024

### Dependency Update

MacOS SDK update to 12.0.16292.

### New features

- MacOS: Newly added [enableFollowingDefaultAudioDevice](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/tx_device_manager/TXDeviceManager/enableFollowingDefaultAudioDevice.html) API.
- MacOS: Newly added [startSystemAudioLoopback](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/startSystemAudioLoopback.html) interface, supporting system audio capture, such as third-party music players.
- Android&iOS&Windows&MacOS: Newly added [startSpeedTestWithParams](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/startSpeedTestWithParams.html) API and [onSpeedTestResult](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud_listener/TRTCCloudListener.html#onSpeedTestResult) callback.

### Defect repair

iOS: The [onStatistics](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud_listener/TRTCCloudListener.html#onStatistics) callback parameter parsing field on iOS is aligned with Android, and *receivedBytes* is changed to *receiveBytes*.

## Version 2.8.5 @ Aug 2, 2024

### Dependency Update

Windows SDK update to 12.0.1.6002.

## Version 2.8.4 @ Aug 1, 2024

### Dependency Update

Windows SDK update to 12.0.0.15124.

### New features

Windows: Newly added [enableFollowingDefaultAudioDevice](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/tx_device_manager/TXDeviceManager/enableFollowingDefaultAudioDevice.html) API.

## Version 2.8.3 @ Jul 22, 2024

### Dependency Update

- Android SDK update to 11.9.0.14466
- iOS SDK update to 11.9.15963

## Version 2.8.2 @ Jun 20, 2024

### New features

- Android&iOS: Newly added [onAudioRouteChanged](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud_listener/TRTCCloudListener.html#onAudioRouteChanged) callback.
- Added new audio route such as `TRTC_AUDIO_ROUTE_WIREDHEADSET`, see [TRTCCloudDef](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud_def/TRTCCloudDef-class.html) for details.

### Defect repair

Windows: Fixed [onDeviceChange](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud_listener/TRTCCloudListener.html#onDeviceChange) callback not triggered.

## Version 2.8.1 @ Jun 14, 2024

### New features

- Android&iOS: Newly added [setVoicePitch](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/tx_audio_effect_manager/TXAudioEffectManager/setVoicePitch.html) API
- Added new reverb effects such as `Studio 2`, see [TXVoiceReverbType](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud_def/TXVoiceReverbType-class.html) for details.

## Version 2.8.0 @ May 21, 2024

### New features

Windows: Newly added [getScreenCaptureSources](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/getScreenCaptureSources.html) and [selectScreenCaptureTarget](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/selectScreenCaptureTarget.html) API to support Windows screen sharing.

## Version 2.7.9 @ May 20, 2024

### Dependency Update

- Android SDK update to 11.8.0.14188
- iOS SDK update to 11.8.15687

## Version 2.7.8 @ Apr 18, 2024

### Dependency Update

- Windows SDK updated to 11.7.0.14863.
- MacOS SDK updated to 11.7.15304.
- Android SDK updated to 11.7.0.13910.
- iOS SDK updated to 11.7.15343.

### New features

Android&iOS: Added [createSubCloud](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/createSubCloud.html) and [destroySubCloud](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/destroySubCloud.html) API.

### Defect repair

Windows: Fixed a data parsing error in the [onRecvCustomCmdMsg](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud_listener/TRTCCloudListener.html#onRecvCustomCmdMsg) callback.

## Version 2.7.7 @ Apr 03, 2024

### Defect repair

Web: Fixed an issue where invoking switchRole was ineffective.

## Version 2.7.6 @ Feb 29, 2024

### Defect repair

Windows: Fixed a data upload issue in the Window library.

## Version 2.7.5 @ Feb 29, 2024

### New features

Windows: Updated [startSystemAudioLoopback](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/startSystemAudioLoopback.html) interface to support the collection of audio from specific applications.

## Version 2.7.4 @ Feb 29, 2024

### New features

Windows: Added [startSystemAudioLoopback](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/startSystemAudioLoopback.html) interface to support system audio capture, such as from third-party music players.

## Version 2.7.3 @ Jan 15, 2024

### Defect repair

Web: Fixed a compilation failure issue on the Web platform due to the introduction of dart:ffi.

## Version 2.7.2 @ Jan 11, 2024

### Dependency Update

Window: Upgraded Client SDK version to 11.4.0.

## Version 2.7.1 @ Dec 28, 2023

### Defect repair

macOS: Fixed an occasional crash issue that occurred during the TexTure rendering process.

### New features

Android&iOS: Added [setAudioFrameListener](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/setAudioFrameListener.html) API.

## Version 2.7.0 @ Dec 13, 2023

### New features

Web: Upgraded Web TRTC SDK to the latest version (v5) to achieve a more stable feature.

### Defect repair

Web: Fixed an issue where screen sharing from Android and iOS devices could not be viewed in the Web version.

## Version 2.6.0 @ Nov 21, 2023

### Defect repair

Web: Fixed an issue that occurred when calling the [getCurrentDevice](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/tx_device_manager/TXDeviceManager/getCurrentDevice.html) and [getDevicesList](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/tx_device_manager/TXDeviceManager/getDevicesList.html) APIs.

## Version 2.5.9 @ Sep 28, 2023

### New features

- Android&iOS: Added [startPublishMediaStream](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/startPublishMediaStream.html) API.
- Android&iOS: Added [updatePublishMediaStream](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/updatePublishMediaStream.html) API.
- Android&iOS: Added [stopPublishMediaStream](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/stopPublishMediaStream.html) API.

## Version 2.5.8 @ Sep 13, 2023

### New features

Replaced document jump links with International Site.

## Version 2.5.7 @ Sep 11, 2023

### Dependency Update

- Android SDK updated to 11.4.0.13189.
- iOS SDK updated to 11.4.14445.
- macOS SDK updated to 11.4.14445.

## Version 2.5.6 @ Aug 09, 2023

### Defect repair

Windows: Optimized Dart code style.

## Version 2.5.5 @ Aug 02, 2023

### Dependency Update

- Android SDK updated to 11.3.0.13200.
- iOS SDK updated to 11.3.14354.
- macOS SDK updated to 11.3.14333.

## Version 2.5.4 @ Jul 10, 2023

### Dependency Update

- Android SDK updated to 11.3.0.13176.
- iOS SDK updated to 11.3.14333.

## Version 2.5.3 @ Jun 27, 2023

### Dependency Update

- Android SDK updated to 11.2.13145.
- iOS SDK updated to 11.2.14217.

## Version 2.5.2 @ Jun 16, 2023

### Defect repair

- Windows: Fixed the issue where the [startSpeedTest](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/startSpeedTest.html) function returned excessively long Data Events and had No Response.
- Web: Marked [setAudioPlayoutVolume](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/setAudioPlayoutVolume.html) and [getAudioPlayoutVolume](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/getAudioPlayoutVolume.html) as unavailable.

## Version 2.5.1 @ Jun 02, 2023

### New features

- Windows&Mac&Web: Restored support for the Windows&Mac&Web platforms.
- iOS: Added the [setSystemAudioLoopbackVolume](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/setSystemAudioLoopbackVolume.html) API, supporting System Volume adjustment during Screen Sharing.

### Defect repair

iOS: Fixed occasional memory leak issues with [TRTCCloudVideoView](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud_video_view/TRTCCloudVideoView-class.html) in specific scenarios.

### Dependency Update

Windows&Mac: Upgraded Client SDK version to 11.1.0.

## Version 2.5.0 @ May 04, 2023

### Feature optimization

Temporarily removed support for Web, MacOS, and Windows platforms.

## Version 2.4.6 @ May 04, 2023

### Dependency Update

- Android SDK updated to 11.1.0.13111.
- iOS SDK updated to 11.1.14143.

## Version 2.4.5 @ Mar 14, 2023

### New features

Android: Added [startSystemAudioLoopback](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/startSystemAudioLoopback.html) feature.

## Version 2.4.4 @ Mar 06, 2023

### Feature optimization

Optimized part of the code.

## Version 2.4.2 @ Jan 09, 2023

### Dependency Update

Android SDK updated to 10.9.0.24004.

## Version 2.4.2 @ Jan 09, 2023

### Defect repair

Fixed the issue where [snapshotVideo](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/snapshotVideo.html) was empty on the iOS platform.

## Version 2.4.1 @ Dec 01, 2022

### Dependency Update

- Android SDK updated to 10.8.0.13065.
- iOS SDK updated to 10.8.12025.

## Version 2.4.0 @ Oct 31, 2022

### Feature optimization

Optimized part of the code.

## Version 2.3.9 @ Oct 18, 2022

### Dependency Update

- Android SDK updated to 10.7.0.13053.
- iOS SDK updated to 10.7.11936.

## Version 2.3.8 @ Sep 20, 2022

### Feature optimization

Optimization for Windows Platform, automatically add related DLL files.

## Version 2.3.7 @ Sep 16, 2022

### Defect repair

Repair the issue with "Can't use 'Function' as a name" on Web Platform.

## Version 2.3.6 @ Sep 05, 2022

### Feature optimization

Optimized part of the code.

## Version 2.3.5 @ Aug 23, 2022

### Dependency Update

- Android SDK updated to 10.3.0.11196.
- iOS SDK updated to 10.3.12231.

## Version 2.3.4 @ Jul 21, 2022

### New features

- Updated Windows, MacOS, and Web platforms to support Pure Video Mode.
- [setMixTranscodingConfig](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/setMixTranscodingConfig.html): Only supports Mixed Video.

## Version 2.3.2 @ Jul 14, 2022

### Dependency Update

Android/iOS SDK updated to 10.3.

## Version 2.3.1 @ Jun 23, 2022

### Feature optimization

Optimized part of the code.

## Version 2.3.0 @ Jun 20, 2022

### Dependency Update

Android/iOS SDK updated to version 10.1 of LiteAVSDK_Professional.

### New features

Support for Third-Party Beauty Filters.

## Version 2.2.4 @ May 11, 2022

### Feature optimization

Optimization of the [setMixTranscodingConfig](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/setMixTranscodingConfig.html) interface.

## Version 2.2.3 @ May 07, 2022

### Dependency Update

- Android SDK set to 9.9.0.11820.
- iOS SDK set to 9.5.11346.

## Version 2.2.2 @ May 05, 2022

### Feature optimization

Update Log Module.

## Version 2.2.1 @ Apr 21, 2022

### Feature optimization

PlatformView supports the 'onTap' event.

## Version 2.2.0 @ Mar 30, 2022

### Dependency Update

Update Android/iOS SDK to TXLiteAVSDK_Live.

## Version 2.1.7 @ Mar 22, 2022

### Defect repair

Repair the issue with iOS video rendering in version 2.1.6.

## Version 2.1.6 @ Mar 17, 2022

### Feature optimization

Optimize iOS texture.

## Version 2.1.5 @ Mar 11, 2022

### Feature optimization

Update remoteView to adjust the parameter order.

## Version 2.1.4 @ Mar 10, 2022

### Feature optimization

Update documents.

## Version 2.1.3 @ Mar 10, 2022

### Feature optimization

Update documents.

## Version 2.1.2 @ Mar 07, 2022

### Dependency Update

- Android SDK updated to 9.5.11207.
- iOS SDK updated to 9.5.11207.

## Version 2.1.1 @ Feb 15, 2022

### Defect repair

Repair the issue with incorrect callback data in onSpeedTest.

## Version 2.1.0 @ Jan 25, 2022

### Feature optimization

Optimize initialization timing.

## Version 2.0.9 @ Jan 13, 2022

### Defect repair

Repair the issue where the web folder was not found.

### Dependency Update

Android & iOS SDK updated to 9.5.

## Version 2.0.7 @ Jan 10, 2022

### Feature optimization

Resolve warning.

## Version 2.0.6 @ Jan 10, 2022

### Feature optimization

Delete web folder.

## Version 2.0.5 @ Jan 10, 2022

### Feature optimization

Optimize document display.

## Version 2.0.1 @ Jan 07, 2022

### Feature optimization

Encapsulate video texture rendering into PlatformView.

## Version 2.0.0 @ Jan 04, 2022

### Feature optimization

Support smooth web.

## Version 1.3.1 @ Jan 04, 2022

### Feature optimization

Optimize part of the documents.

## Version 1.3.0 @ Nov 22, 2021

### Feature optimization

Android video rendering changed from SurfaceView to GLSurfaceView.

## Version 1.2.9 @ Nov 15, 2021

### Dependency Update

The underlying Android SDK version has been updated to 9.3.10765.

## Version 1.2.8 @ Nov 15, 2021

### Feature optimization

The underlying GLSurfaceView in Android has been replaced with TextureView, updateView only supports TextureView.

## Version 1.2.7 @ Nov 05, 2021

### Feature optimization

Screen sharing supports streams of specified sizes.

## Version 1.2.6 @ Nov 01, 2021

### Defect repair

Fixed the iOS video rendering issue caused by the previous version.

## Version 1.2.5 @ Oct 27, 2021

### New features

Android video rendering supports hybrid integration mode. The default mode is the virtual display mode. The view mode of TRTCCloudVideoView is passed to TRTCCloudDef.TRTC_VideoView_Mode_Hybrid.

## Version 1.2.4 @ Sep 29, 2021

### Feature optimization

- Fluent's Windows platform supports texture rendering.
- Fluent English documentation is available online.

## Version 1.2.3 @ Sep 28, 2021

### New features

Android supports [updateLocalView](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/updateLocalView.html) and [updateRemoteView](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/updateRemoteView.html) interfaces.

## Version 1.2.2 @ Sep 10, 2021

### Defect repair

Fix Android texture rendering memory growth issue with multiple video switches.

## Version 1.2.1 @ Sep 10, 2021

### Feature optimization

Optimize certain features.

## Version 1.2.0 @ Sep 10, 2021

### New features

Specify the return value of the Beauty Filter, Equipment, and Sound management module.

## Version 1.1.9 @ Aug 19, 2021

### Defect repair

Fix issues such as Screenshot failure on iOS and MacOS.

## Version 1.1.8 @ Aug 12, 2021

### Feature optimization

Android Texture Rendering compatibility with meglhelper.

## Version 1.1.7 @ Aug 10, 2021

### Defect repair

Fix the issue of missing businessInfo field on Android.

## Version 1.1.6 @ Aug 03, 2021

### Feature optimization

Optimize certain features.

## Version 1.1.5 @ Aug 03, 2021

### Defect repair

Fix the crash issue caused by special string parameters when playing music in publication mode on iOS and MacOS.

## Version 1.1.4 @ Aug 03, 2021

### Defect repair

Fix the crash issue caused by special string parameters on iOS and MacOS.

## Version 1.1.3 @ Jul 27, 2021

### Defect repair

- Fix the issue with no network quality data in the onspeedtest callback on iOS and MacOS.
- Fix the issue with meglcore being null in Android texture rendering.

## Version 1.1.2 @ Jul 23, 2021

### Defect repair

Fixed an issue where iOS and macOS did not support auxiliary stream rendering.

## Version 1.1.1 @ Jul 21, 2021

### New features

New form of texture rendering.

## Version 1.1.0 @ Jul 14, 2021

### Defect repair

Fixed an issue where video could not be rendered after restarting remote view on Android.

## Version 1.0.9 @ Jun 30, 2021

### New features

Android and iOS support local recording [startLocalRecording](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/startLocalRecording.html).

## Version 1.0.8 @ Jun 28, 2021

### New features

Support for Windows and macOS. Currently, only audio-related interfaces are supported, video rendering is not supported.

## Version 1.0.5 @ Jun 09, 2021

### Defect repair

Fixed platform exception error appearing after Android video view termination.

## Version 1.0.4 @ Jun 02, 2021

### New features

iOS adds [updateLocalView](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/updateLocalView.html) and [updateRemoteView](https://liteav.sdk.qcloud.com/doc/product/trtc/dart/api/en/trtc_cloud/TRTCCloud/updateRemoteView.html) interfaces.

## Version 1.0.3 @ Jun 01, 2021

### Defect repair

Fixed the issue where setting the audio routing was ineffective after closing the microphone on Android.

## Version 1.0.2 @ May 27, 2021

### Feature optimization

Modify document comments.

## Version 1.0.1 @ Apr 28, 2021

### Defect repair

Fixed the problem that Android could not enter the room when room ID exceeded 2147483647. Supported value range: 1 - 4294967294.

## Version 1.0.0 @ Apr 23, 2021

### Feature optimization

Upgrade to Flutter 2.0, support Zero Security.


---
*Source: [https://trtc.io/document/60459](https://trtc.io/document/60459)*
