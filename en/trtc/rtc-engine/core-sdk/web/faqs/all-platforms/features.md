# Features

### What is Tencent Real-Time Communication?

Leveraging Tencent's many years of experience in network and audio/video technologies, Tencent Real-Time Communication (TRTC) offers solutions for group audio/video calls and low-latency interactive live streaming. With TRTC, you can quickly develop cost-effective, low-latency, and high-quality interactive audio/video communication apps with a wide range of features. To learn more, see [Product Introduction > Overview](https://www.tencentcloud.com/document/product/647/35078).

### How can I experience TRTC demos?

You can go to the [Free Demo](https://www.tencentcloud.com/document/product/647/35076) page to find TRTC demos for different platforms.

### How can I quickly get started with TRTC?

TRTC provides you with demo source code for various platforms that you can use to quickly build your own applications. For more information, see [User Tutorial](https://www.tencentcloud.com/document/product/647/39386).

### What is `RoomID` in TRTC? What is its value range?

`RoomID` uniquely identifies a room and can range from 1 to 4294967295. You are responsible for maintaining and assigning the room IDs of your applications.

### What is `UserID` in TRTC? What is its value range?

`UserID` uniquely identifies a user in a TRTC application. It can contain letters (case sensitive), digits, and underscores, preferably not longer than 32 bytes.

### How long is the lifecycle of a TRTC room?

- **In call modes**, TRTC closes a room when all users exit the room.
- **In live streaming modes**, if the last user who exits a room is an anchor, TRTC will close the room immediately; if the user is an audience member, TRTC will close the room after 10 minutes.
- A user is removed from a room 90 seconds after an unexpected disconnection occurs. If all users are disconnected, the room is closed after 90 seconds. **The waiting time after a disconnection occurs is also billed**.
- If a user attempts to enter a room that does not exist, TRTC will automatically create a room with the ID entered.

### Can users not subscribe to audio/video streams?

To enable instant streaming, TRTC subscribes users to audio/video streams by default upon room entry. You can call the `setDefaultStreamRecvMode` API to switch to the manual subscription mode.

### How can I make it so users are not automatically subscribed to audio/video streams upon room entry?

Yes. You can specify a `streamId` via `TRTCParams` of `enterRoom` or call the `startPublishing` API to pass in the `streamId`.

### What roles are supported during live streaming in TRTC? How do they differ from each other?

The live streaming scenarios (`TRTCAppSceneLIVE` and `TRTCAppSceneVoiceChatRoom`) support two roles: `TRTCRoleAnchor` (anchor) and `TRTCRoleAudience` (audience). An anchor can both send and receive audio/video data, but audience members can only receive and play others' data. You can call `switchRole()` to switch roles.

### What application scenarios are supported in TRTC rooms?

- TRTCAppSceneVideoCall: The video call scenario is suitable for one-to-one video calls, video conferences with up to 300 participants, online medical consultation, video chat, and video interviews.
- TRTCAppSceneLIVE: The interactive video streaming scenario is suitable for low-latency live video streaming, interactive classroom for up to 100,000 participants, live video competition, video dating, remote training, and mega conferences.
- TRTCAppSceneAudioCall: The audio call scenario is suitable for one-to-one audio calls, audio conferences with up to 300 participants, audio chat, and online party games.
- TRTCAppSceneVoiceChatRoom: The interactive audio streaming scenario is suitable for low-latency audio streaming, live audio co-anchoring, audio chat rooms, karaoke, and radio.

### What platforms does TRTC support?

TRTC supports platforms including iOS, Android, Windows (C++), Unity, macOS, web, and Electron. For more information, see [Supported Platforms](https://intl.cloud.tencent.com/document/product/647/35078).

### What are the differences between TRTC Lite and TRTC Professional?

See [Edition Comparison](https://intl.cloud.tencent.com/document/product/647/34615).

### Does TRTC support co-anchoring during live streaming?

- [Live Streaming Mode (iOS and macOS)](https://intl.cloud.tencent.com/document/product/647/35107)
- [Live Streaming Mode (Android)](https://intl.cloud.tencent.com/document/product/647/35108)
- [Live Streaming Mode (Windows)](https://intl.cloud.tencent.com/document/product/647/35109)
- [Live Streaming Mode (Electron)](https://intl.cloud.tencent.com/document/product/647/36070)
- [Live Streaming Mode (Web)](https://intl.cloud.tencent.com/document/product/647/35110)

### How many rooms can there be in TRTC at the same time?

There can be up to 4,294,967,294 concurrent rooms in TRTC. There is no limit to the number of non-concurrent rooms.

### How do I create a room?

- [iOS & macOS > enterRoom](https://liteav.sdk.qcloud.com/doc/api/en/group__TRTCCloud__ios.html#a96152963bf6ac4bc10f1b67155e04f8d)
- [Android > enterRoom](https://liteav.sdk.qcloud.com/doc/api/en/group__TRTCCloud__android.html#abfc1841af52e8f6a5f239a846a1e5d5c)
- Windowsï¼C++ï¼ > enterRoom
- [Windows (C#) > enterRoom](https://liteav.sdk.qcloud.com/doc/api/zh-cn/group__ITRTCCloud__csharp.html#afbb3a1e6f73f339d47368a7d620a995f)
- [Electron > enterRoom](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCCloud.html#enterRoom)
- [Web > join](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/Client.html#join)

### What is the upper limit on the bandwidth used for the video service of TRTC?

There isnât a limit.

### Can TRTC be deployed on-premises?

Private deployment of TRTC is not commercially available yet. If you have questions about it or want to use it, please contact us at info_rtc@tencent.com.

### To enable relay to CDN in TRTC, do I need to register my domain name with an ICP filing number?

Yes, according to relevant regulations, playback domains must be registered.

### How long is the average latency in TRTC?

The average end-to-end latency of TRTC around the globe is less than 300 milliseconds.

### Does TRTC support active calling?

You can enable this feature using signaling channels. For example, you can use the custom message feature of [Chat](https://intl.cloud.tencent.com/product/im) to enable active calling. For more information, see the scenario-specific demos in the [SDK](https://intl.cloud.tencent.com/document/product/647/34615) source code.

### Can I use Bluetooth earphones when having one-to-one video calls in TRTC?

Yes, you can.

### Does TRTC support screen sharing on PCs?

- [Real-Time Screen Sharing (Windows)](https://intl.cloud.tencent.com/document/product/647/37335)
- [Real-Time Screen Sharing (macOS)](https://intl.cloud.tencent.com/document/product/647/37336)
- [Real-Time Screen Sharing (Web)](https://intl.cloud.tencent.com/document/product/647/35163)

For more information on the screen sharing APIs, see [Client APIs > All Platforms (C++)](https://intl.cloud.tencent.com/document/product/647/35131). You can also use [Electron APIs](https://intl.cloud.tencent.com/document/product/647/35141).

### Can I share local video files in TRTC?

Yes. You can achieve this using the [Custom Capturing and Rendering](https://intl.cloud.tencent.com/document/product/647/35158) feature.

### Can I record live streaming sessions and save the recording files locally on my phone?

You cannot save recording files directly to your phone. Recording files are saved to VOD. You can download them from VOD and save them to your phone.

### Does TRTC support audio-only streams?

Yes, it does.

### Can there be more than one screen sharing image in the same room?

Currently, only one screen sharing substream is allowed in a room.

### When a specified window is shared (`SourceTypeWindow`), if the window size changes, will the resolution of the video stream change accordingly?

By default, the SDK automatically adjusts encoding parameters according to the size of the shared window.
If you want a fixed resolution, call the `setSubStreamEncoderParam` API to set encoding parameters for screen sharing or specify the parameters when calling the `startScreenCapture` API.

### Does TRTC support 1080p videos?

Yes. You can set the resolution through `setVideoEncoderParam`, the video encoding parameter of the SDK.

### Can I customize data capturing in TRTC?

You can on some platforms. For details, see [Custom Capture and Rendering](https://intl.cloud.tencent.com/document/product/647/35158).

### Is communication between TRTC and the ILVB SDK possible?

No, it's not.

### Is communication between TRTC and MLVB possible?

TRTC and MLVB have different backend architectures and therefore cannot communicate with each other. However, you can relay streams from TRTC to CDNs.

### How do different room entry modes (`AppScene`) vary from one another in TRTC?

TRTC has four room entry modes. Video call (`VideoCall`) and audio call (`VoiceCall`) are the call modes, and interactive video live streaming (`Live`) and interactive audio live streaming (`VoiceChatRoom`) are the live streaming modes.

- The call modes allow a maximum of 300 users in each TRTC room, and up to 50 of them can speak at the same time. The call modes are suitable for scenarios such as one-to-one video calls, video conferences with up to 300 participants, online medical consultation, video interviews, video customer service, and online party games.
- The live streaming modes support a maximum of 100,000 concurrent users in each room and allow smooth mic on/off. Co-anchoring latency is kept below 300 milliseconds and viewing latency below 1,000 milliseconds. The live streaming modes are suitable for scenarios such as low-latency interactive live streaming, interactive classrooms for up to 100,000 participants, video dating, online education, remote training, and mega conferences.

### Can I use the hands-free mode during video calls in TRTC?

Yes. You can enable the hands-free mode by setting audio routes. In a native SDK, use the `setAudioRoute ` API to switch routes.

### Does TRTC support volume reminders?

Yes. You can call the `enableAudioVolumeEvaluation` API to enable volume reminders.

### Does TRTC support mirror images?

Yes. You can call the `setLocalViewMirror` API to set the mirroring mode for the preview image of the local camera or call `setVideoEncoderMirror` to set the mirroring mode for encoded images.

### Can I record the audio of a TRTC call and save the recording file locally?

Yes. You can call `startAudioRecording` to record all audios of a call, including that of the local user, remote users and the background music, into a single file in the format of PCM, WAV, or AAC.

### Can I record the video of a TRTC call into a file?

TRTC supports audio/video recording on a local server. To use this feature, please [submit a ticket](https://console.tencentcloud.com/workorder/category) for the SDK and instructions.
You can also use the on-cloud recording feature to record videos.

### Does TRTC support floating windows (like those in WeChat) or switching between a big and small window?

These features are part of UI design, for which the TRTC SDK sets no restrictions. Our official demo provides sample code for image overlaying and the grid layout and supports floating windows, big/small window switch, and window dragging. For more information, see the [TUICalling demo](https://github.com/tencentyun/TUICalling).

### How do I make an audio-only call in TRTC?

TRTC does not use separate channels for audio and video. You can make an audio-only call by calling only `startLocalAudio` and not `startLocalPreview.

### How do I enable relay to CDN and recording for an audio-only call in TRTC?

- In TRTC SDK 6.9 or later, just set the scene parameter to `TRTCAppSceneAudioCall` or `TRTCAppSceneVoiceChatRoom` during room entry.

### Can I kick a user out, forbid a user to speak, or mute a user in a TRTC room?

- To enable the features through simple signaling operations, use `sendCustomCmdMsg`, the custom signaling API of TRTC, to define your own control signaling, and users who receive the message will perform the action expected. For example, to kick out a user, just define a kick-out signaling, and the user receiving it will exit the room.
- If you want to implement a more comprehensive operation logic, we recommend that you use [Tencent Cloud Chat](https://www.tencentcloud.com/document/product/1047) to map the TRTC room to a Chat group and enable the features via the sending/receiving of custom messages in the group.

### Can TRTC pull and play back RTMP/FLV streams?

Yes. The TRTC SDK has integrated TXLivePlayer. If you need more player features, consider using the full-featured LiteAVSDK_Professional.

### How many people can there be in a TRTC call?

- In live streaming scenarios, each room can accommodate up to 100,000 concurrent users, and up to 50 of them can be assigned the anchor role and turn on their cameras or mics at the same time.

### How do I start a live streaming session in TRTC?

TRTC offers a dedicated low-latency interactive live streaming solution that allows up to 100,000 participants. Co-anchoring latency is kept as low as 200 milliseconds, and viewing latency is below one second. It adapts excellently to poor network conditions and is optimized for complex mobile network environments.

For more information, see [Live Streaming Mode](https://intl.cloud.tencent.com/document/product/647/35107).

### Can I use the custom message sending API of TRTC to implement features such as chat and on-screen comments?

No. Custom message sending is intended for simple and low-frequency signaling scenarios. For details, see [Sending Custom Messages > Use Limits](https://intl.cloud.tencent.com/document/product/647/35159).

### Can I loop background music in TRTC? Can I adjust the playback progress of background music?

> **Note**`setBGMPosition()` of `TXAudioEffectManager` has been replaced with `seekMusicToPosInMS` since version 7.3.

### Can I listen for the entry/exit of users through callbacks in TRTC? Can I use `onUserEnter` or `onUserExit`?

> **Note**`onUserEnter` and `onUserExit` have been replaced with `onRemoteUserEnterRoom` and `onRemoteUserLeaveRoom` since version 6.8.

### How do I listen for network disconnection and reconnection in TRTC?

- `onConnectionLost`: The SDK is disconnected from the server.
- `onTryToReconnect`: The SDK is reconnecting t to the server.
- `onConnectionRecovery`: The SDK is reconnected to the server.

### Does the TRTC SDK support automatic reconnection?

The SDK reconnects a user automatically after a disconnection. If it fails to reconnect the user within 30 minutes, it will remove the user from the room and return the -3301 error.The figure below shows the callbacks triggered when `Userid1` enters a room, is disconnected from the SDK, and re-enters the room:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/333bbc3f2c5211ee818e525400088f3a.png)

**Description**:

- T1: The user calls the `enterRoom` API to enter a room.
- T2: `Userid1` receives the `onEnterRoom` callback, and `Userid2` receives the `onRemoteUserEnterRoom` callback after about 300 milliseconds (latency).
- T3: `Userid1` is disconnected due to a network problem, and the SDK tries to reconnect the user.
- T4: If `Userid1` is not reconnected within the first eight seconds, the user will receive the `onConnectionLost` callback.
- T5: If three more seconds elapse and `Userid1` is still not reconnected, the user will receive the `onTryToReconnect` callback.
- T6: `Userid1` will then receive `onTryToReconnect` callback every 24 seconds.
- T7: 90 seconds after the `onConnectionLost` callback, `Userid2` receives the `onRemoteUserLeaveRoom` callback, which indicates that `Userid1` is offline.
- T8: If reconnection succeeds at any point during the 90 seconds, `Userid1` will receive the `onConnectionRecovery` callback.

### Is there a callback for first frame rendering? Can I listen for the start of image rendering or audio playback?

Yes. You can use `onFirstVideoFrame` and `onFirstAudioFrame` to listen for the events.

### Can I take a screenshot of a video in TRTC?

Currently, you can call `snapshotVideo()` on iOS and Android to take screenshots of local and remote videos.

### Why do I fail to connect peripheral devices such as Bluetooth earphones to TRTC?

Currently, TRTC supports mainstream Bluetooth earphones and peripherals, but for some devices, there are still compatibility issues. We recommend that you use our official demos and QQ audio/video calls to test the compatibility of a device.

### How do I get information such as the upstream/downstream bitrate, resolution, packet loss rate, and audio sample rate of a TRTC audio/video call?

You can call the `onStatistics()` API of the SDK to get the statistics.

### Does TRTCâs background music API `playBGM()` support online music?

No. Currently, it supports only local music. You can download an online music file and then call `playBGM()` to play it.

### Can I set the local audio capturing volume or the playback volume of each remote user?

Yes. You can call `setAudioCaptureVolume()` to set the audio capturing volume of the SDK and `setRemoteAudioVolume()` to set the playback volume of a remote user.

### What are the differences between `stopLocalPreview` and `muteLocalVideo`?

- `muteLocalVideo` is used to stop the sending of local video images. If you call this API, other users will not see your image, but you can still preview your own image.

### What are the differences between `stopLocalAudio` and `muteLocalAudio`?

- When `muteLocalAudio` is called, TRTC does not stop the sending of audio/video data. It continues to send muted data packets at extremely low bitrate.

### What resolutions does the TRTC SDK support?

We recommend that you set the resolution as instructed in [Setting Video Quality](https://intl.cloud.tencent.com/document/product/647/35153) for better image quality.

### How do I set the upstream video bitrate, resolution, and frame rate in the TRTC SDK?

Call the `setVideoEncoderParam()` API of `TRTCCloud` and set `videoResolution` (resolution), `videoFps` (frame rate), and `videoBitrate` (bitrate) in `TRTCVideoEncParam`.

### How do I rotate videos in the TRTC SDK?

See [Rotating Videos](https://intl.cloud.tencent.com/document/product/647/35154).

### How do I make a video call in the landscape mode?

See [Rotating Videos](https://intl.cloud.tencent.com/document/product/647/35154).

### How do I match the rotation of the local and remote videos if they are different?

See [Rotating Videos](https://intl.cloud.tencent.com/document/product/647/35154).

### What image quality-related settings (bitrate, resolution, and frame rate) does TRTC recommend?

See [Setting Video Quality > Recommended Configuration](https://intl.cloud.tencent.com/document/product/647/35153#.E6.8E.A8.E8.8D.90.E7.9A.84.E9.85.8D.E7.BD.AE).

### Can I test my network speed in TRTC? How?

Yes, you can. For details, see [Testing Network Quality](https://intl.cloud.tencent.com/document/product/647/35156).

### Can I control access to a TRTC room to allow only authorized users to enter the room?

Yes. For details, please see [Enabling Advanced Permission Control](https://intl.cloud.tencent.com/document/product/647/35157).

### Can TRTC pull and play back RTMP/FLV streams?

Yes.

### What formats does TRTC support for custom rendering?

- iOS: I420, NV12, and BGRA.
- Android: I420 and Texture2D.

### How do I enable on-cloud recording and playback in TRTC?

Please see [On-Cloud Recording and Playback](https://www.tencentcloud.com/document/product/647/35426#).

### Does TRTC support beauty filters?

- To use beauty filters on web, see [Enabling Beauty Filters](https://web.sdk.qcloud.com/trtc/webrtc/doc/en/tutorial-28-advanced-beauty.html).
- The AI beauty filters in native TRTC SDKs are a value-added service which is charged by Tencent Effect SDK.

> **Note**Currently, only TRTC Professional for iOS and Android support AI beauty filters.

### Can I use TRTC outside the Chinese mainland?

> **Note**TRTC offers reliable and secure network connection across the globe. It uses Tencent Cloudâs proprietary multi-level addressing algorithm and can connect to nodes across the entire network. Abundant high-bandwidth resources and globally distributed edge servers allow it to keep its average end-to-end latency below 300 milliseconds globally.International connection may be subject to actual local conditions and application scenarios.

### Does TRTC support detecting inappropriate content in images?

TRTC blocks pornographic, politically sensitive, and other inappropriate content during live streaming.

### How do I query the information of all users in a room?

You can view the currently online rooms and users through Console - Monitoring Dashboard - [Real-Time Monitoring](https://console.tencentcloud.com/trtc/realtime-monitor).

### Can TRTC receive other RTSP streams?

No, it canât, but it does support RTMP streaming. For details, see [Publishing over RTMP](https://www.tencentcloud.com/document/product/647/52171#).

### Does TRTC support dual-channel encoding?

Yes, TRTC supports dual-channel audio.

### When publishing streams, does TRTC package or encode streams first?

After data capturing, TRTC encodes streams first before packaging.

### Does the TRTC SDK use Swift?

The model layer uses Objective-C and the UI layer uses Swift.

### Can I use TRTC if my account is a personal account?

Yes, you can.

### Does TRTC SDK support IPv6?

Yes, it is recommended to upgrade to version 10.6 and above for further optimization of IPv6 room entry speed.

### How to use the Region of Interest video codec feature in TRTC Monthly Package?

To use the Region of Interest video codec feature, you need to call the experimental interface ([callExperimentalAPI](https://www.tencentcloud.com/document/product/647/50762), taking Android as an example) to set the region of interest. Here is an example:

```
//Set ROI parameters{    "api":"UpdateRoiConfig",    "params":{          "roiConfigArray":[              {                    "stream":1,                    "x":0,                    "y":0,                    "width":100,                    "height":100,                    "level":2               },               {                    "stream":1,                    "x":20,                    "y":200,                    "width":100,                    "height":100,                    "level":2               }           ]     }}
```

| Field Name | Description |
| --- | --- |
| stream | Stream Type: 0 for main stream, 1 for substream, 2 for auxiliary stream. |
| x,y,w,h | ROI coordinate points, with the codec output resolution as a reference. |
| level | [0, 12], which is the intensity of the ROI. The higher the value, the more obvious the effect in the ROI area, but the non-ROI area may be more blurry. |


---
*Source: [https://trtc.io/document/36057](https://trtc.io/document/36057)*
