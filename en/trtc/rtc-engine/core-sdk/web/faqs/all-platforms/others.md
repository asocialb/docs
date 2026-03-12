# Others

### How do live streaming, interactive live streaming, TRTC, and relayed live streaming differ from and relate to each other?

- **Interactive live streaming** (keywords: co-anchoring, cross-room communication)
 In interactive live streaming, audience can co-anchor with anchors and anchors from different rooms can compete with each other.
- **Tencent real-time communication** (keywords: multi-person interaction, UDP-based proprietary protocol, low latency)
 The main capabilities of TRTC are audio/video interaction and low-latency live streaming. It uses a UDP-based proprietary protocol and can keep the latency as low as 100 ms. Typical applications include QQ calls, VooV Meeting, and online group classes. TRTC offers solutions for mainstream platforms including iOS, Android, and Windows, allows communication with WebRTC, and supports mixing streams in the cloud and relaying them to CDNs.
- **Relayed live streaming** (keywords: on-cloud stream mixing, RTC relayed live streaming, CDN)
 The relayed live streaming technology replicates multiple streams in a low-latency co-anchoring room and mixes them into one stream in the cloud before pushing it to a live streaming CDN for distribution and playback.

### The demo is running on two devices, but why can't they display the images of each other?

### When there is only one user in a room, why is CDN playback stuttering and blurry?

### Why can't I enter any online room?

### How do I view TRTC logs?

- iOS/macOS: `Documents/log` of the application sandbox
- Android:
  - v6.7 or earlier: `/sdcard/log/tencent/liteav`
  - v6.8-8.5: `/sdcard/Android/data/package name/files/log/tencent/liteav/`
  - Later than v8.5: `/sdcard/Android/data/package name/files/log/liteav/`
- Windows:
  - Earlier than v8.8: `%appdata%/tencent/liteav/log`
  - v8.8 and later: `%appdata%/liteav/log`
- Web: Open the browser console or use vConsole to log printed SDK information.

> **Note**You need to download a decryption tool to view an XLOG file. Place the tool in the same directory as the XLOG file in Python 2.7 and run `python decode_mars_log_file.py`.You can download the log decryption tool at `dldir1.qq.com/hudongzhibo/log_tool/decode_mars_log_file.py`.

### What should I do if a 10006 error occurs?

If the "Join room failed result: 10006 error: service is suspended, if charge is overdue, renew it" occurs, check whether your TRTC application service is available.
Log in to the TRTC console, click

Application Management

, find the application you created, and click

**Application Info**

to view the service status.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2e2df6a13a7c11ed8e47525400463ef7.png)

### Why is the error code â-100018â returned during room entry?

- The `SDKAppID` parameter passed in is incorrect. You can log in to the TRTC console and click [Application Management](https://console.tencentcloud.com/trtc/app) to view the `SDKAppID`.
- The `UserSig` passed in, which should match the `UserID`, is incorrect. To verify your `UserSig`, log in to the TRTC console and click **Development Assistance** > [UserSig Generation & Verification](https://console.tencentcloud.com/trtc/usersigtool).

### How do I make a cross-room call?

You can make a cross-room call by using the `connectOtherRoom` API. Anchor A calls `connectOtherRoom()` to connect to anchor B and gets the result via the `onConnectOtherRoom` callback. All users in anchor Aâs room will be notified via the `onUserEnter` callback that anchor B has entered the room, and all users in anchor Bâs room will be notified via the `onUserEnter` callback that anchor A has entered the room.

### Do I have to call the `exitRoom()` API?

### What are the formats of the recording files generated in different relayed recording scenarios?

### How do I know whether a stream is published successfully in a video call?

### How do I know whether a stream is published successfully in an audio call?

### Can I query all `UserID` values?

### Can users with the same `UserID` be in the same room at the same time?

### Why doesn't the audio route (receiver/speaker) configured via the `setAudioRoute` API take effect?

### Can I manually enable recording for a call?

1. In the TRTC console, click [Application Management](https://console.tencentcloud.com/trtc/app) > **Function Configuration**, enable **Relay to CDN**, and disable **On-Cloud Recording**.
2. After a user (`userid`) enters the room, splice the userâs `streamid` according to the stream ID generation rule.
3. Use the [CreateRecordTask](https://intl.cloud.tencent.com/document/product/267/37309) API of CSS to start a recording task for the `streamid`.
- Set `DomainName` to `[bizid].livepush.myqcloud.com`.
- Set `AppName` to `trtc_[sdkappid]`.
- Set `StreamName` to `streamid`.
4. After the recording task is completed, CSS will save the file in VOD and notify you via the [recording callback](https://intl.cloud.tencent.com/document/product/267/38080).

### How does TRTC verify `UserSig`? How do I troubleshoot the â-3319â or â-3320â error during room entry?

### How do I view my call duration and usage?

### How do I maintain the user list and count the number of users in a TRTC room?

If you have integrated [Chat](https://intl.cloud.tencent.com/document/product/1047) into your project, you can use the Chat group user counting API to calculate the number of users in a room. However, such calculation is not always accurate. You may use this method if you donât have a high requirement on accuracy.
If you do have a high requirement on the accuracy of the calculation, we recommend you implement the following calculation logic:

1. Increase the user count (client -> server): Whenever a user enters the room, increase the user count by 1. To achieve this, you can make the userâs client send a count increasing request to the server upon room entry.
2. Decrease the user count (client -> server): When a user leaves a room, decrease the user count by 1. To achieve this, you can make the userâs client send a count decreasing request to the server during room exit.

### A â-100013â error is reported during room entry, with the error message âERR_SERVER_INFO_SERVICE_SUSPENDEDâ. What should I do?

- Whether you have used up your package
- Whether your Tencent Cloud account has overdue payment

### What should I do if I have enabled on-cloud recording but no recording files are generated?

2. TRTC starts recording only if there is a user publishing audio/video data in a room.
3. A recording file will be generated only if CDN pull is successful.
4. If there is only audio in a room at first before video is published, depending on the recording template configured, the recording file generated may contain only the video segment or the audio-only segment.

### How do I give the room ID to the co-anchor I invite?

### Is it possible to start audio recording only when there are two or more users in a room?

### How do I capture the audio of a shared application on Windows?

### How to implement the feature that allows anchors to invite audience members to co-anchor in conference scenarios on Windows?

You need to use another Tencent Cloud product, [Chat](https://intl.cloud.tencent.com/document/product/1047/33996), to implement the feature.

This is how it works: A sends a custom message X (you can determine how the message is displayed) to B, and the calling page is shown; B receives X and the called page is shown; B uses [enterRoom](https://liteav.sdk.qcloud.com/doc/api/zh-cn/group__TRTCCloud__cplusplus.html#a0fab3ea6c23c6267112bd1c0b64aa50b) to enter the room and sends a custom message X1 to A; A receives X1 (you can determine whether to display the message) and uses `enterRoom` to enter the room. The messages are sent via Chat.

### How do audience members watch the videos of co-anchors in a room?

In live streaming scenarios, audience get the `userid` of anchors in a room via the onUserVideoAvailable callback in `TRTCCloudDelegate` (co-anchoring users enter the room by calling [enterRoom](https://liteav.sdk.qcloud.com/doc/api/zh-cn/group__TRTCCloud__cplusplus.html#a0fab3ea6c23c6267112bd1c0b64aa50b) and are also anchors for the audience). They then call [startRemoteView](https://liteav.sdk.qcloud.com/doc/api/zh-cn/group__TRTCCloud__cplusplus.html#a5c5ea936418b106c2e801db57938dde9) to play the videos of the anchors.
For more information, see [Live Streaming Mode > Windows](https://intl.cloud.tencent.com/document/product/647/35109).

### Is there a TRTC SDK for Linux?

### Does TRTC support screen sharing during video calls or interactive live streaming?


---
*Source: [https://trtc.io/document/36058](https://trtc.io/document/36058)*
