# Released Notes

A version number is in the format of `major.minor.patch`.

- `major`: Major version number. If there is major version refactoring, this field will be incremented. Generally, the APIs of different major versions are not compatible with each other.
- `minor`: Minor version number. The APIs of different minor versions are compatible with each other. If there is a new or optimized API, this field will be incremented.
- `patch`: Patch number. If there is a feature improvement or bug fix, this field will be incremented.

> **Note:**Please update to the latest version in a timely manner for service stability and better online support.For version upgrade precautions, please refer to: [Upgrade Guide](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-00-info-update-guideline.html).

## Version 5.15.0 @2026.01.14

**Feature**

- Added support for [Real-time Transcriber and Translation Plugin](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-42-advanced-realtime-transcriber.html).
- Added support for [Face Detection Plugin](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-43-advanced-face-detection.html).
- Support for full-screen and Picture-in-Picture video playback. Refer to the `fullScreen` and `pictureInPicture` parameters in [trtc.updateRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/TRTC.html#updateRemoteVideo). Compared to browser's native APIs, the SDK provides a better compatibility experience.
- Added support for capturing system audio in screen sharing with the [VideoMixer](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-40-advanced-video-mixer.html#screensource) plugin.

**Improvement**

- Added the `reason` field to the [REMOTE_USER_EXIT](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/module-EVENT.html#.REMOTE_USER_EXIT) event to identify the reason for the remote user's exit.
- Added the `isReconnecting` field to the [CONNECTION_STATE_CHANGED](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/module-EVENT.html#.CONNECTION_STATE_CHANGED) event to indicate whether the SDK is currently reconnecting.

**Bug Fixed**

- Fixed occasional audio playback issue on iOS 26 WeChat.
- Fixed audio-video sync issue on remote end that may occur when frequently toggling microphone.
- Fixed issue where remote video `first-video-frame` event only triggered once.

## Version 5.14.1 @2025.11.14

**Bug Fixed**

- Fix the issue that weak network conditions may emit error event with encoding failed.

## Version 5.14.0 @2025.11.07

**Feature**

- Supports alpha channel rendering, suitable for scenarios requiring transparent backgrounds like digital humans. For integration, please contact [Technical Support](https://trtc.io/contact).

**Improvement**

- Optimized auto-play logic to reduce the probability of auto-play popups.

**Bug Fixed**

- Fixed occasional mute failure issue under poor network conditions.
- Fixed occasional streaming failure issue in specific scenarios.
- Fixed issue where microphone removal might not automatically resume collection.
- Fixed issue where Google Pixel phones might capture infrared camera feed.
- Fixed an issue where the switchRoom + cross-room scenario might fail to subscribe to the new anchor's stream after switching rooms.

## Version 5.13.1 @2025.10.10

**Feature**

- Added two experimental APIs: [pauseRemotePlayer & resumeRemotePlayer](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#callExperimentalAPI), supporting pausing and resuming remote stream playback.

**Improvement**

- Optimized the compatibility of beauty and virtual background plugins on Electron 22.
- Improve the success rate of media capture.
- Avoided the issue where the browser's default play button might appear when playing videos on some Android devices.

**Bug Fixed**

- Fixed occasional no sound issue in Firefox.
- Fixed occasional unmute audio failure issue.
- Fixed CDN plugin pure audio relay failure issue.

## Version 5.13.0 @2025.09.08

**Feature**

- Support for chorus plugin. For integration, please contact [technical support](https://trtc.io/contact).
- Support for [AI Denoiser](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-35-advanced-ai-denoiser.html#h2-5) far-field elimination mode to improve recognition accuracy in ASR scenarios.
- Add new API: [TRTC.getPermissions](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.getPermissions), which can be used to get the current user's camera and microphone authorization status.
- Add new event: [VIDEO_SIZE_CHANGED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.VIDEO_SIZE_CHANGED), which can be used to detect video resolution changes.

**Improvement**

- Optimized the callback timing of [PUBLISH_STATE_CHANGED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.PUBLISH_STATE_CHANGED) `started` state, changed from `when SDK streaming succeeds` to `when server receives the first frame of data`.
- Added virtual background post-processing technology (experimental) to reduce black edges and jagged edges around characters. Currently only supported on PC. Refer to: [enableEffectOptimization parameter](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-36-advanced-virtual-background.html#h2-5) to enable this feature.
- Optimized AI noise reduction plugin performance to avoid occasional brief silence issues on low-end devices.
- Optimized audio mixing plugin resource loading logic to improve resource loading success rate.
- Avoided the issue where Huawei browsers might switch to telephoto lens when switching to rear camera.
- Improved switchRoom success rate.

**Bug Fixed**

- Fixed the issue where screen sharing capture was not terminated after closing screen sharing when capturing system audio.
- Fixed the issue where DEVICE_CHANGED event callback parameters were incorrect after switching to rear camera on some Android devices.
- Fixed the issue where enabling virtual background plugin failed in Electron.

## Version 5.12.1 @2025.08.18

**Improvement**

- Support [setRemoteAudioVolume](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#setRemoteAudioVolume) call caching, eliminating the need to recall this interface when remote users rejoin the room.

**Bug Fixed**

- Fixed a low probability issue of no sound when AI-Denoiser plugin is enabled in Safari.
- Fixed a low probability issue of no video when playing remote video streams in specific scenarios.
- Fixed an issue where turning off the camera would incorrectly close the custom captured track during custom capture.

## Version 5.12.0 @2025.07.24

**Breaking Changes**

- Removed built-in CDN addresses and reduced the size of the virtual background plugin resources. If you fall into any of the following scenarios, you need to redeploy the assets from the npm package and specify the path in `TRTC.create({ assetPath })` when upgrading:
  - Using the virtual background plugin.
  - Using the AI noise reduction plugin but have not deployed the assets from the npm package before.

**Features**

- Added support for the [Local Video Mixer Plugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-40-advanced-video-mixer.html), which allows mixing multiple input sources such as camera feeds, screen sharing, text, images, and videos.
- Added support for pulling PSTN audio.
- Added support for muting system audio via `trtc.updateScreenShare({ muteSystemAudio: true })`.

**Improvements**

- The [TRTC.EVENT.ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.ERROR) event now includes notifications for audio/video codec failures.
- Improved compatibility of the [device detection plugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-23-advanced-support-detection.html#h2-3) and added support for specifying languages (Chinese/English).
- Enhanced compatibility with older iOS versions.

**Bug Fixed**

- Fixed an issue where the microphone capture was not released after calling stopLocalAudio when using the AI Denoiser plugin.
- Fixed an occasional issue where the camera preview might display with incorrect aspect ratio after rotating the screen orientation on mobile devices.

## Version 5.11.1 @2025.06.27

**Improvement**

- Added `allowSkip` parameter to the device detection plugin to control whether users can skip the device detection process.
- Added `floatVolume` parameter to [AUDIO_VOLUME](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.AUDIO_VOLUME) event.

**Bug Fixed**

- Fixed an issue where controlling remote video mirroring would affect the upstream video mirroring.
- Fixed an issue where upgrading from v4 to v5 occasionally resulted in missing TRTC.isSupported detection fields.
- Fixed an issue where enabling the basic beauty plugin reported an error.

## Version 5.11.0 @2025.06.13

**Feature**

- Support for [trtc.switchRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#switchRoom) API, reducing room switching time by up to 40% in weak network scenarios for the 'audience' role in 'live' scene.
- Support for setting the `rotate` parameter in [trtc.startLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) to control camera rotation angle.
- Support for [Local Video Mixer Plugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-40-advanced-video-mixer.html), allowing local mixing of camera and screen sharing before publishing.
- [Virtual Background Plugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-36-advanced-virtual-background.html#h2-5) now supports automatic face centering.
- Automatic switching between big and small streams based on downlink network conditions. See: [Enable Small Stream](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-27-advanced-small-stream.html#h2-3).
- [AUDIO_FRAME](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.AUDIO_FRAME) event now supports getting remote audio data.
- [STATISTICS](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.STATISTICS) event now supports getting end-to-end latency.

**Improvement**

- Improved small stream performance and stability (SDK will automatically switch to big stream if small stream playback fails).
- Avoid the Chrome 137 (some versions) screen sharing system audio echo [issue](https://issues.chromium.org/issues/422611724). To do so:
  - Activate the AI noise suppression [package](https://trtc.io/document/56025?platform=web&product=rtcengine&menulabel=coresdk).
  - Deploy the `assets` directory from the npm package; the SDK requires `audioProcessor-wasm.js`.
  - Pass your CDN resource path to `TRTC.create({ assetsPath })`.

**Bug Fixed**

- Fixed an occasional issue where publishing did not resume after reconnection.
- Fixed an issue where muting or unmuting the camera caused a black video issue when played by a remote user.
- Fixed an issue where trtc multi-instance event notifications were abnormal in specific scenarios.
- Fixed an issue where camera rendering was abnormal after interruption by the iOS system.
- Fixed an issue where some Android phones could not encode 120p small streams.

## Version 5.10.1 @2025.05.15

**Bug Fixed**

- Fixed an issue where switching cameras occasionally caused a black screen after enabling small stream, beauty effects, or virtual background.
- Fixed an issue where updating camera resolution failed when used with the WebAR SDK.
- Fixed an issue where streams could not be played in iPad Chrome when accessing the desktop website.
- Fixed an occasional black screen issue when using the `receiveWhenViewVisible` parameter.

## Version 5.10.0 @2025.04.17

**Breaking Changed**

- The plugin format has been changed from `iife` to `umd`, supporting more integration environments. If you load plugins via the `<script>` tag, please note that you need to update the plugin file name during the upgrade.
- The wasm resource files in the npm package have been unified and moved to the `assets` directory. You can directly deploy the `assets` directory during deployment.

**Feature**

- Support [Voice Changer Plugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-37-advanced-voice-changer.html).

**Improvement**

- Optimized the downgrade strategy for the TRTCVideoDecoder plugin.
- Optimized Android H264 detection logic.
- Optimized the ear return logic to play the processed audio.

**Bug Fixed**

- Fixed an error that occurred when reusing WebSocket and switching userId to enter a room.
- Fixed an issue where the video frame was cropped during 360p capture on PC Chrome. To avoid this, specify the parameter: `TRTC.startLocalVideo({ option: { avoidCropping: true }})`.

## Version 5.9.2 @2025.04.10

**Improvement**

- [trtc.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo) added poster parameter.
- Improved call quality under poor network conditions.

## Version 5.9.1 @2025.03.07

**Bug Fixed**

- Fixed an issue where audio was lost on iOS after being interrupted by other apps playing sound.
- Fixed uneven audio callback frequency after the page was moved to the background.
- Fixed an issue where dynamically updating the resolution could cause the virtual background to fail.

## Version 5.9.0 @2025.02.17

**Feature**

- Added [Video Decoder Plugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-39-advanced-video-decoder.html) to improve decoding success rate.
- Added audio route switching between headset and speaker for Android devices. See:[TRTC.setCurrentSpeaker](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.setCurrentSpeaker).
- Added video first frame callback event. See: [FIRST_VIDEO_FRAME](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.FIRST_VIDEO_FRAME).

**Improvement**

- Reduced ultra-fast startup time. For optimal quick launch experience, contact technical support.
- Optimized volume calculation logic to support volume retrieval under HTTP protocol.
- Add resume method for the callback parameter of [AUTOPLAY_FAILED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.AUTOPLAY_FAILED).

**Bug Fixed**

- Fixed low-probability no-audio issue in iOS.
- Fixed SEI message loss issue in Safari & Firefox.
- Fixed untriggered autoplay failed event in specific scenarios.
- Fixed occasional issue that muteRemoteAudio does not working.
- Fixed audio-only call failures in environments without H.264 support.

## Version 5.8.6 @2024.12.27

**Improvement**

- Optimize the reconnection logic to improve the success rate of reconnection.
- Optimize the setRemoteAudioVolume interface to support setting the volume before playing the audio stream.
- Avoid the issue of no audio on some Honor devices.
- Avoid the issue of memory leakage caused by enabling watermark in iOS 16&18.

**Bug Fixed**

- Fix the issue of no audio when screen sharing + system audio.
- Fix the issue of occasional rendering distortion after dynamically updating the resolution in iOS 16.
- Fix the issue of occasional AudioContext error in iOS WKWebView.
- Fix the issue of empty pcm data in audio-frame event after switching microphone.

## Version 5.8.5 @2024.12.03

**Breaking Changed**

The Debug plugin becomes a built-in plugin and does not need to be imported externally. Reference [Debug plugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-18-basic-debug.html).

**Feature**

- Support screen sharing on main stream.
- The Debug plugin supports to dump audio & video.

**Improvement**

Improved volume callback accuracy and compatibility.

**Bug Fixed**

- Fixed the no audio issue after occasionally sharing system audio.
- Fixed the loading SDK error in Android X5 kernel.
- Fixed compatibility issues with WebAR SDK in iOS 16.
- Fixed the no audio issue with frequent enterRoom & exitRoom.
- Fixed the video lag issue when using CrossRoom plugin.
- Fixed the video rendering issue with enabling virtual background when switching between front and background.

## Version 5.8.3 @2024.10.25

**Feature**

Add [AUDIO_FRAME](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.AUDIO_FRAME) event. You can get the microphone pcm data from this event.

**Improvement**

Improve the rendering performance in Safari.

**Bug Fixed**

- Fixed the issue that the non-specified device may be captured when capturing device.
- Fixed an issue of CDNStreaming plugin that the mixing stream may be failed when the roomId is not fill in.

## Version 5.8.2 @2024.10.11

**Improvement**

- Reduce the time taken to enter the room.
- Improve the stability of the virtual background plugin.

**Bug Fixed**

- Fixed an no audio issue when calling trtc.stopScreenShare.
- Fixed an occasional issue that CrossRoom plugin cannot start again.
- Fixed an occasional issue that the custom messages being lost.

## Version 5.8.1 @2024.09.12

**Feature**

- Support sending and receiving SEI messages in Safari and Firefox.
- Add [VirtualBackground.isSupported](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-36-advanced-virtual-background.html) method to detect whether the current browser supports VirtualBackground plugin.

**Improvement**

- Optimize type declaration files.
- Improve the browser compatibility(Firefox and Safari) of VirtualBackground plugin.

**Bug Fixed**

- Fix the occasional issue of custom message loss.
- Fixed the occasional issue that the remote video was not playing in Firefox.
- Fixed the issue that cannot publish video with 15fps+ in Safari.
- Fixed the issue that removing the camera view would cause the stream to stop publishing in Safari 16.

## Version 5.8.0 @2024.08.23

**Feature**

- Support [CrossRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-30-advanced-cross-room-link.html) Plugin.
- Support [DeviceDetector](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-23-advanced-support-detection.html) Plugin.
- Support [Debug](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-18-basic-debug.html) Plugin.

**Bug Fixed**

- Fix the issue that publishing video failed after enableSEI occasionally.
- Fix the issue that the resolution of screen sharing is higher than setting in Firefox.

## Version 5.7.1 @2024.08.07

**Bug Fixed**

- Fix the issue of remote video rendering in iOS 17.
- Fix the issue that the unifiedProxy does not work.

## Version 5.7.0 @2024.07.19

**Feature**

Support sending & receiving SEI message in sub stream.

**Improvement**

- The preview box will only display the current page when screen sharing using the captureElement parameter.
- Avoid the [Chrome issue](https://issues.chromium.org/issues/330055211) that unplug the headset will cause no audio issue in Android Webview.
- Improve the detection logic of h264 capability.

**Bug Fixed**

- Fix the issue that cannot see remote video in the browser that support h264 decoding, but not h264 encoding.

## Version 5.6.3 @2024.06.28

**Feature**

- Support listening to audio playback progress events in AudioMixer plugin.
- Support set blur level in VirtualBackground plugin

**Improvement**

- Improve the success rate of resuming normal calls after interrupting iOS calls.
- Improve the success rate of audio autoplay in iOS.

**Bug Fixed**

- Fixed the occasional reconnection issue in Chrome M91-.
- Fixed the audio lag issue after remote user mute & unmute microphone.
- Fixed the issue that remote publishing screen share event was mistakenly thrown in certain scenarios.

## Version 5.6.2 @2024.06.07

**Improvement**

- Reduce the video or audio lag for the audience.
- Improve the success rate of reconnection.

**Bug Fixed**

- Fixed the issue that capturing camera 1920 * 1280 failed in Mac Safari.
- Fixed an occasional issue that cannot resume audio after autoplay failed in mobile chrome.
- Fixed an occasional issue that cannot receive remote audio.
- Fixed an occasional issue that muteRemoteAudio throws an abort error.

## Version 5.6.1 @2024.05.23

**Bug Fixed**

Fixed a no audio issue when autoReceiveAudio disabled.

## Version 5.6.0 @2024.05.17

**Breaking Changed**

Set the default value of `autoReceiveVideo` to false, refer to: [Upgrade Guide](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-00-info-update-guideline.html).

**Feature**

Support [trtc.sendCustomMessage](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#sendCustomMessage).

**Bug Fixed**

- Fixed the issue that startRemoteVideo got error in Chrome 123.
- Fixed the issue that enter room failed in iOS 12.0.
- Fixed the issue that the encoding mirror occasionally fails.
- Fixed the issue that the AudioMixer plugin loop would not work.

## Version 5.5.2 @2024.04.29

**Improvement**

- Speed up loading by deploying model files yourself, refer to: [Enable Visual Background](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-36-advanced-virtual-background.html).
- Avoid the video flicker issue in iOS 17, refer to: [WebKit bug](https://bugs.webkit.org/show_bug.cgi?id=230532).

**Bug Fixed**

- Fixed the issue that getting error occasionally when subscribing remote small video in Chrome M123+.
- Fixed the issue that playing remote video failed occasionally.

## Version 5.5.1 @2024.04.12

**Improvement**

- Improve the success rate of reconnection.
- Improve the success rate of recapturing.

**Bug Fixed**

- Fix the issue that video was not playing in iOS 15.1.
- Fix the issue that screen sharing was publishing on the main stream but not sub stream after calling `trtc.updateScreenShare({ publish: true })`
- Fix the issue that the bitrate was not 128kbps when setting the audio profile to `TRTC.TYPE.AUDIO_PROFILE_HIGH`.
- Fix the issue that the base64 imageUrl was unable to set to the WaterMark plugin.

## Version 5.5.0 @2024.03.29

**Feature**

- Add [Beauty](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-28-advanced-beauty.html) plugin.

**Improvement**

- Optimize the capability of the AI Denoiser plugin in mobile phone.
- Improve the success rate of media recapturing.

**Bug Fixed**

- Fixed the issue that the preview of local video is black in iOS 16.
- Fixed the issue that the user cannot hear the sound of remote audio occasionally in iOS 14.
- Fixed the issue that startLocalAudio throws TypeError occasionally.

## Version 5.4.3 @2024.03.15

**Feature**

- Added support for passing MediaStreamTrack to the [AudioMixer](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-22-advanced-audio-mixer.html) plugin.
- Added support for calling [trtc.getAudioTrack](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#getAudioTrack) to obtain the screen sharing audio MediaStreamTrack.

**Bug Fixed**

- Fixed the occasional issue where setting setRemoteAudioVolume to 0 did not work.
- Fixed the issue that screen sharing audio was not published after calling updateScreenShare({ publish: true }).
- Fixed the issue where virtual backgrounds could not be enabled in Safari.

## Version 5.4.2 @2024.03.01

**Bug Fixed**

- Fixed the issue that startRemoteVideo failed occasionally.
- Fixed the issue that unpublish failed occasionally.
- Fixed the issue that audio & video are not synchronized.
- Fixed the issue that enterRoom failed when using nginx proxy.

## Version 5.4.1 @2024.02.05

**Improvement**

Optimize the reconnection logic to improve the success rate of reconnection.

**Bug Fixed**

- Fixed the issue that mirror is reset by calling updateLocalVideo.
- Fixed the issue that CONNECTING state is not emitted by CONNECTION_STATE_CHANGED event.

## Version 5.4.0 @2024.01.16

**Feature**

- Support obtaining video snapshot. Refer to: [getVideoSnapshot()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#getVideoSnapshot).
- Support setting an image after mute video. Refer to: the mute parameter of [startLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo).
- Support publishing the video streams only when the view is visible. Refer to: [Multi-Person Video Calls](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-27-advanced-small-stream.html).
- Support screen sharing to capture a certain DOM element on the page. Refer to: [startScreenShare()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startScreenShare).

**Improvement**

- Optimize the logic of enterRoom and reduce the time cost of enterRoom.
- Optimize the reconnection logic of laptop closed and reopened.

**Bug Fixed**

- Fix the issue that publish failed on the version before Chrome 69.
- Fix the issue that publish 1080p video failed on iOS 13 & 14.

## Version 5.3.2 @2023.12.26

**Feature**

- Support watermark plugin, refer to: [Enable Watermark](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-29-advance-water-mark.html).
- Support encoding mirror, refer to: [startLocalVideo() 's mirror parameter](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo).

**Improvement**

- Improve audio and video encoding stability and quality.

**Bug Fixed**

- Fix known issues with the CDNStreaming plugin.
- Fix the issue where the volume value returned by the volume event is 0 after setting remoteAudioVolume to 0.
- Fix the issue of occasional vocals dropping words when AI denoiser is enabled on some external microphones.

## Version 5.3.1 @2023.12.08

**Bug Fixed**

- Fix the abnormal issue with the mixing plugin.
- Fix the inability to enter the room in earlier versions of Chrome 74.
- Fix the issue that some audio interfaces do not perform as expected with AI noise reduction open.
- Fix the issue that in multiple TRTC instance scenarios, the destruction of one instance prevents the others from receiving the DEVICE_CHANGED event.

## Version 5.3.0 @2023.12.01

**Feature**

- Support SEI messaging, which can be used for functions such as lyric synchronization and live quiz. For more details, please refer to [sendSEIMessage](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/TRTC.html#sendSEIMessage).
- Enable dynamic switching of large and small streams. For more details, please refer to the **option.small** parameter in [updateLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/TRTC.html#updateLocalVideo).
- Support mute pushing. For more details, please refer to the **mute** parameter in [startLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/TRTC.html#startLocalVideo).
- Enable role switching with updated **privateMapKey**. For more details, please refer to the **privateMapKey** parameter in [switchRole](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/TRTC.html#switchRole).
- Add [TRTC.EVENT.TRACK](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/module-EVENT.html#.TRACK) event.

**Improvement**

- Improve the room entry process to reduce the time consuming.
- Improve the encoding quality for high-resolution call scenarios and earlier devices of Android Chrome.
- Improve device acquisition logic. With media access unauthorized, the SDK may temporarily request media permissions to ensure normal access to media devices, which will then be released.
- Improve the parsing logic of the **url** parameter in the mixing plugin.
- Improve the noise reduction effect of the AI noise reduction plugin.

**Bug Fixed**

- Fix the issue of Android Chrome being unable to encode 120p.
- Fix the issue where stopping screen sharing in non-pushing scenarios would cause the camera pushing to stop.
- Fix the issue of the invalid **CDN mixing plugin** parameter.

## Version 5.2.1 @2023.11.08

**Feature**

- Add 'captureVolume' parameter to API [startLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) & [updateLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalAudio).
- Support [TRTC.EVENT.DEVICE_CHANGED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.DEVICE_CHANGED) event on mobile phone. You can implement the feature that auto switch to new microphone when a new headset is connected based on this event. Refer to [Handle Device Change](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-25-advanced-device-change.html).

**Bug Fixed**

- Fix the issue that local microphone is muted after switching microphone.
- Fix the issue that the mediaType of [TRTC.EVENT.PUBLISH_STATE_CHANGED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.PUBLISH_STATE_CHANGED) is wrong after [stopScreenShare](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopScreenShare).

## Version 5.2.0 @2023.10.31

**Feature**

- Add [TRTC.EVENT.STATISTICS](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.STATISTICS) event.

**Improvement**

- Improve the success rate of device capture.
- Optimize the mirror processing logic of "Picture-in-Picture mode".
- When the user's system rejects the browser permission, RtcError.handler() can be called to jump to the system authorization settings and guide the user to turn on the permission quickly. Refer to [5302](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.ENV_NOT_SUPPORTED).

**Bug Fixed**

- Fixed an occasional issue that remote audio is not playing in low version of Chrome.

## Version 5.1.3 @2023.09.11

**Feature**

- [trtc.setRemoteAudioVolume](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#setRemoteAudioVolume) supports setting the volume higher than 100 to gain the remote playback volume.

**Improvement**

- Avoided [iOS 15.1 bug](https://bugs.webkit.org/show_bug.cgi?id=232006) that caused page crash when switching camera.

**Bug Fixed**

- Fix the issue that Firefox stopLocalVideo and then restart startLocalVideo failed.
- Fix the issue that Firefox fails to capture camera with certain resolution, e.g. 640 * 360.
- Fix the issue of remote video not playing occasionally.

## Version 5.1.2 @2023.08.25

**Improvement**

- Reduce time cost to enter a room.

**Bug Fixed**

- Fix the issue that webpack package build of trtc.esm.js occasionally reporting errors.
- Fix the issue that startLocalAudio passing in custom capture audioTrack does not work.

## Version 5.1.1 @2023.08.18

**Improvement**

- Default video profile changed to 480p_2 to reduce uplink bandwidth consumption.
- Avoid the [Chrome Bug](https://bugs.chromium.org/p/chromium/issues/detail?id=1469318) that Android Chrome 115 occasionally fails to encode at resolutions lower than 360p.

**Bug Fixed**

- Fix the issue that cannot enter room or startLocalVideo on Windows Chrome 57 and iOS Safari 12.
- Fix the issue that the video bitrate is abnormal on Dashboard.

## Version 5.1.0 @2023.08.11

**Breaking Change**

- Restrict the roomId parameter of the [trtc.enterRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom) interface to be of number type and no longer support passing in string type. If you want to use a string roomId, please use the strRoomId parameter. When upgrading, please pay attention, see [Upgrade Guide](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/tutorial-00-info-update-guideline.html) for details.

**Feature**.

- Support background music plugin, refer to the tutorial: [Implement Background Music](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/tutorial-22-advanced-audio-mixer.html).
- Support AI noise reduction plugin, refer to tutorial: [Implement AI Denoise](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/zh-cn/tutorial-35-advanced-ai-denoiser.html).

**Bug Fixed**.

- Fix the issue that setting screen sharing capture resolution does not work.
- Fix the issue of occasional playback failure of remote screen sharing.

## Version 5.0.3 @2023.07.31

**Improvement**

- Optimize the reconnection mechanism to improve the stability of network connection.

**Bug Fixed**

- Fix the issue that when calling trtc.stopRemoteVideo to stop the main video, the sub video is also stopped.

## Version 5.0.2 @2023.07.21

**Improvement**

- Optimize the performance and weak network resistance in multi-person call.
- Optimize device capture logic to avoid the issue that some Lenovo devices cannot turn on the camera.
- Optimize the capture parameters of screen sharing to avoid the issue of occasional frame dropping in long-time screen sharing.

**Bug Fixed**

- Fix the issue that the small stream bit rate setting does not take effect.
- Fix the issue that systemAudio parameter does not work.
- Fix the issue that video tag is not destroyed after remote user screen sharing stopped.

## Version 5.0.1 @2023.06.25

**Feature**

- Support playing video with multiple view at the same time.

**Bug Fixed**

- Fix the issue that screen sharing cannot be restarted after clicking the browser hover window to close screen sharing.

## Version 5.0.0 @2023.05.26

The new architecture version of the TRTC Web SDK provides a flat interface that dramatically simplifies the API and reduces access costs. Features of the new API:

- Flatter APIs that are easier to access.
- Better stability.
- Better performance.


---
*Source: [https://trtc.io/document/53626](https://trtc.io/document/53626)*
