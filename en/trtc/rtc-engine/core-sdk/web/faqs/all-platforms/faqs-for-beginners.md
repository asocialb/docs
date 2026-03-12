# FAQs for Beginners

### What is UserSig?

`UserSig` is a security signature designed by Tencent Cloud to prevent attackers from accessing your Tencent Cloud account.
Currently, Tencent Cloud services including TRTC, Chat, and MLVB all use this security mechanism. Whenever you want to use these services, you must provide three key pieces of information, i.e. `SDKAppID`, `UserID`, and `UserSig` in the initialization or login function of the corresponding SDK.
`SDKAppID` is used to identify your application, and `UserID` your user. `UserSig` is a security signature calculated based on the two parameters using the **HMAC SHA256** encryption algorithm. Attackers cannot use your Tencent Cloud traffic without authorization as long as they cannot forge a `UserSig`.
See the figure below for how `UserSig` is calculated. Basically, it involves hashing crucial information such as `SDKAppID`, `UserID`, and `ExpireTime`.

```
// UserSig formula, in which `secretkey` is the key used to calculate UserSigusersig = hmacsha256(secretkey, (userid + sdkappid + currtime + expire +                                  base64(userid + sdkappid + currtime + expire)))
```

> **Note:**`currtime` is the current system time and `expire` the expiration time of the signature.For detailed directions on how to calculate and get `UserSig`, please see [UserSig](https://intl.cloud.tencent.com/document/product/647/35166).

### How many rooms can there be in TRTC at the same time?

### How long is the average delay in TRTC?

### Does TRTC support screen sharing on PCs?

- [Real-Time Screen Sharing (Windows)](https://intl.cloud.tencent.com/document/product/647/37335)
- [Real-Time Screen Sharing (macOS)](https://intl.cloud.tencent.com/document/product/647/37336)
- [Real-Time Screen Sharing (Web)](https://intl.cloud.tencent.com/document/product/647/35163)

For more information on the screen sharing APIs, please see [Client APIs > All Platforms (C++) > Overview](https://intl.cloud.tencent.com/document/product/647/35131) or [Client APIs > Electron > Overview](https://intl.cloud.tencent.com/document/product/647/35141).

### What platforms does TRTC support?

### How many people can there be in a TRTC call?

- In live streaming scenarios, each room can accommodate up to 100,000 concurrent users, and up to 50 of them can be assigned the anchor role and turn on their cameras or mics.

### How do I start a live streaming session in TRTC?

TRTC offers a dedicated low-latency interactive live streaming solution that allows up to 100,000 participants with co-anchoring latency kept as low as 200 ms and watch latency below 1s. It adapts excellently to poor network conditions and is optimized for the complicated mobile network environments.

For detailed directions, please see [Live Streaming Mode](https://trtc.io/zh/document/47858?product=rtcengine&menulabel=serverfeaturesapis#plan1).

### What roles are supported during live streaming in TRTC? How do they differ from each other?

### Can I kick a user out, forbid a user to speak, or mute a user in a TRTC room?

- To enable the features through simple signaling operations, use `sendCustomCmdMsg`, the custom signaling API of TRTC, to define your own control signaling, and users who receive the message will perform the action expected. For example, to kick out a user, just define a kick-out signaling, and the user receiving it will exit the room.
- If you want to implement a more comprehensive operation logic, we recommend that you use [Tencent RTC Chat](https://trtc.io/zh/document/50061) to map the TRTC room to an Chat group and enable the features via the sending/receiving of custom messages in the group.

### Can TRTC pull and play back streams through CDN?

Yes. For details, please see [CDN Relayed Live Streaming](https://trtc.io/zh/document/47858?product=rtcengine&menulabel=serverfeaturesapis#plan1).

### Does TRTC support Swift integration on iOS?

### What browsers does the SDK for web support?

### What do the errors `NotFoundError`, `NotAllowedError`, `NotReadableError`, `OverConstrainedError`, and `AbortError` found in the log of TRTC SDK for web mean?

| Error | Description | Suggested Solution |
| --- | --- | --- |
| NotFoundError | The media (audio, video, or screen sharing) of the request parameters are not found. For example, this error occurs if the PC has no cameras but the browser requests a video stream. | Remind users to check devices such as cameras and mics before making a call. |
| NotAllowedError | The user has rejected the request of the current browser instance to access the camera/mic or share screens. | Remind the user that audio/video calls are not possible without camera/mic access. |
| NotReadableError | The user has granted access to the requested device, but it is still inaccessible due to a hardware, browser or webpage error. | Handle the error according to the error message returned, and send this message to the user: âThe camera/mic cannot be accessed. Please make sure that no other applications are requesting access and try again.â |
| OverConstrainedError | The `cameraId/microphoneId` value is invalid. | Make sure that the `cameraId/microphoneId` value passed in is valid. |
| AbortError | The device cannot be accessed due to an unknown reason. | - |

For more information, please see [initialize](https://web.sdk.qcloud.com/trtc/webrtc/doc/zh-cn/LocalStream.html?#initialize).

### How do I check whether TRTC SDK for web can get the device (camera/mic) list?

  - Normally, a promise containing an array of `MediaDeviceInfo` objects will be returned, each object corresponding to an available media device.
  - If the SDK fails to enumerate the devices, a rejected promise will be returned, indicating that the browser fails to detect any devices. You need to check the browser or devices.
2. If the device list can be obtained, enter `navigator.mediaDevices.getUserMedia({ audio: true, video: true })` to see if the `MediaStream` object can be returned. If it is not returned, it indicates that the browser failed to obtain any data. You need to check your browser configuration.

### How do live streaming, interactive live streaming, TRTC, and relayed live streaming differ from and relate to each other?

- **Interactive live streaming** (keywords: co-anchoring, anchor competition)
 In interactive live streaming, audience can co-anchor with anchors and anchors from different rooms can compete with each other.
- **Real-time communication** (keywords: multi-person interaction, UDP-based proprietary protocol, low latency)
 The main application scenarios for TRTC (Tencent Real-Time Communication) are audio/video interaction and low-latency live streaming. It uses a UDP-based proprietary protocol and can keep the latency as low as 100 ms. Typical applications include zoom meeting, FaceTime, and online group classes. TRTC is supported by mainstream platforms including iOS, Android, and Windows and can communicate over WebRTC. It supports relaying streams to CDNs through on-cloud stream mixing.
- **Relayed live streaming** (keywords: on-cloud stream mixing, RTC relayed live streaming, CDN)
 The relayed live streaming technology replicates multiple streams in a low-latency co-anchoring room and mixes them into one stream in the cloud before pushing it to a live streaming CDN for delivery and playback.

### How do I view my call duration and usage?

### How do I fix stutter?

- Check the send and receive statistics from the recipientâs perspective.
- Check the send and receive packet loss. High packet loss suggest that the stutter may be caused by unstable network connections.
- Check the frame rate and CPU usage. Both low frame rates and high CPU usage can cause stutter.

### How do I fix low-quality, blurry and pixelated videos?

- TRTC dynamically adjusts bitrate and resolution based on network conditions according to its on-cloud QoS control policy. It reduces the bitrate in case of poor network connections, which leads to decreased definition.
- Check whether the `VideoCall` or `Live` mode is used during room entry. As the `VideoCall` mode is designed for calls and features low latency and smoothness, it tends to sacrifice video quality for smoothness when network connections are poor. We recommend that you use the `Live` mode for application scenarios with high requirements on video quality.

### How do I view the latest version number of the SDK?

- You can find the latest version number of the SDK on the release notes page.
  - For iOS & Android, please see [Release Notes (App)](https://intl.cloud.tencent.com/document/product/647/39426).
  - For web, please see [Release Notes (Web)](https://www.tencentcloud.com/document/product/647/53626#).
  - For Electron, please see [Release Notes (Electron)](https://intl.cloud.tencent.com/document/product/647/38702).


---
*Source: [https://trtc.io/document/38104](https://trtc.io/document/38104)*
