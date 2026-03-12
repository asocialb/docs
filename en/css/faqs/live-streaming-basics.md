# Live Streaming Basics

### What are push, live streaming, and video on demand?

- **Push**: the process of hosts pushing local video and audio to Tencent Video Cloud servers. It is called "RTMP publishing" in some scenarios.
- **Live streaming**: during live streaming, video streams are generated in real time. It works only if someone is pushing. A live streaming URL becomes invalid the moment the host stops pushing. As live streams are played back in real time, viewers cannot see a progress bar during live streaming.
- **Video on demand (VOD)**: VOD allows you to play files in the cloud. A file can be played at any time unless it is deleted by its provider (e.g., Tencent Video). Because videos are already stored in the server, viewers can see a progress bar during playback.

### What are the requirements for a playback domain name in CSS?

The domain name can contain up to 45 characters and cannot contain uppercase letters. For more information, please see [Adding Domain Name](https://www.tencentcloud.com/document/product/267/35970).

### Can I use the same domain name for playback and push? Can I use second-level domain names?

You must use different domain names for playback and push, but you can use the same second-level domain to indicate that the stream is the same.
For example, you can use `123.abc.com` for push, and `456.abc.com` for playback.

### What push protocols are supported?

The push streaming protocols supported by CSS include: RTMP, SRT, WebRTC, and RTMP over SRT.

- **RTMP protocol:**RTMP is gradually being replaced by other low-latency protocols in the live streaming field, but it is the most common protocol used for stream pushing (pushing data from hosts to servers). Currently, domestic video cloud services use RTMP as their main push protocol, and the push streaming SDK (such as TXLivePusher) is also called RTMP SDK.
- **SRT protocol:** TS over SRT directly transmits TS streams containing audio/video data using SRT protocol, The existing live streaming system is used for playback. TS over SRT is used as the standard push format for Haivision hardware and OBS.
- **WebRTC protocol:** The TXLivePusher SDK is used to push streams for CSS. It can push audio/video the browser captures from the camera, screen sharing, or a local file to live streaming servers via WebRTC. Concurrently, it allows for local stream mixing of the collected content before pushing it to the backend server. You can use the WebRTC protocol for live streaming on the web. On the PC side, you can also use the OBS tool for WebRTC live streaming. For more information, please refer to the [OBS WebRTC live streaming](https://www.tencentcloud.com/document/product/267/57042). The advantage of using Web for WebRTC live streaming is that there is no need to install additional software, and you can operate directly in the browser.
- **RTMP over SRT**: The transport layer replaces TCP with SRT. Through SRT's low latency and high resistance to packet loss, it greatly reduces the impact of RTMP on transmission quality when the network is poor and fluctuates, improving the overall live broadcast viewing experience.

### What playback protocols are supported?

Common live streaming protocols include RTMP, HTTP-FLV, HLS and WebRTC.

- **RTMP** can be used for both live push and live playback. It works by splitting long video and audio chunks into short fragments and transporting them as small data packets over the internet. RTMP supports encryption and therefore ensures privacy. However, the complicated splitting and splicing processes add uncertainty to the stability of data transmission in high concurrency scenarios.
- **HTTP-FLV** is developed by Adobe Systems and is a rather simple video format. It works by adding a header to large video and audio data chunks. This simplicity makes it superb in delay control and high-concurrency performance. The only drawback is that HTTP-FLV is poorly supported on mobile browsers, but it is an ideal option for mobile apps.
- **HLS** is released by Apple. It splits video streams into segments of 5-10s and manages them using M3U8 playlists. The protocol ensures smooth playback as clients download data chunks of 5-10s. However, it comes with high latency of about 10-30s. Unlike HTTP-FLV, HLS is well supported on iPhone and most Android browsers and is therefore often used for URL sharing on QQ and WeChat Moments.
- **WebRTC** is short for Web Real-Time Communication. It is an API that allows real-time audio/video calls on web browsers. Supported by Google, Mozilla, and Opera, WebRTC specifications were published by the World Wide Web Consortium (W3C) on June 1, 2011. WebRTC is adopted by LEB, which is an ultra-low-latency version of LVB and offers streaming with millisecond latency. It is suitable for scenarios with high requirements on latency, such as online education, sports streaming, and online quizzes.

| Protocol | Pro | Con | Playback Latency |
| --- | --- | --- | --- |
| HTTP-FLV | Mature, suited for high-concurrency scenarios | SDK integration is required. | 2-3s |
| RTMP | Relatively low latency | Poor performance in high-concurrency scenarios | 1-3s |
| HLS (M3U8) | Well supported on mobile browsers | High latency | 10-30s |
| WebRTC | Lowest latency | SDK integration is required. | < 1s |

### What is the format of a playback URL?

```
rtmp://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)http://domain/AppName/StreamName.m3u8?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)http://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)https://domain/AppName/StreamName.m3u8?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)https://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)webrtc://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)
```

- **Prefix**
RTMP: **rtmp://**
HTTP-FLV: **http://** or **https://**
HLS: **http://** or **https://**
WebRTC: **webrtc://**
- **Application name (**`AppName`**)**
Application name specifies the storage path of a live streaming file. It is **live** by default.
- **stream name (**`StreamName`**)**
Stream name (`StreamName`) uniquely identifies a live stream.
- **Authentication key and other custom parameters**
Authentication key: **txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)**.

### What are the common push methods?

- **Camera on Android/iOS devices**: use third-party software or the [MLVB SDK](https://www.tencentcloud.com/products/mlvb) to capture camera video and push the video stream to your push URL.
- **Camera or screen recorder on PCs**: use third-party software to capture camera video or record the screen and then push the data to your push URL. Such third-party software includes [OBS (recommended)](https://www.tencentcloud.com/document/product/267/31569), XSplit, FMLE, etc.
- **Video capturing device**: connect an HD camcorder with HDMI or SDI output to an encoder and push RTMP streams to live streaming applications. You need to set the RTMP publishing address of the encoder to your push URL.
If you use a webcam that supports RTMP, you can also set the RTMP publishing address of the webcam to your push URL.
- **Converting video files to video streams**: read video files and push them as RTMP streams to your RTMP push URL. This can be achieved using the `FFmpeg` command, which works on Windows, Linux, and macOS.

### What are the differences between stream interruption and stream disabling?

- **Stream interruption**: if a live stream is interrupted, the push will stop, and viewers will be unable to watch the stream. However, the host can start the push again to resume the live streaming.
- **Stream disabling**: if a live stream is disabled, the push will stop, and viewers will be unable to watch the stream. The host cannot start the push again. You can disable a stream on the stream management page of the CSS console. Disabled streams can be found in the list of disabled streams. You can click **Enable** to enable a disabled stream.

### Can I enable text chat for live streaming?

Yes. You can use the Instant Messaging (IM) component to realize text chat for live streaming. In addition, IM provides on-screen comments, likes, gifts, repeat notifications and other interactive features. You can also use the room management feature to realize co-anchoring, manage user identities and the permission to mute members, among others.

### Is CSS a software?

No. CSS provides APIs for you to develop live streaming applications.

### How do I get the number of live streaming viewers?

You can call the CSS v3.0 API [DescribeStreamPlayInfoList](https://www.tencentcloud.com/document/product/267/37297) to get the number of online viewers.

### What streaming protocols are supported for interconversion and relay access?

Interconversion and relay access are supported for common streaming protocols such as RTP, SRT, RTMP, and UDP.


---
*Source: [https://www.tencentcloud.com/document/product/267/7968](https://www.tencentcloud.com/document/product/267/7968)*
