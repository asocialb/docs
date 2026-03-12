# SDK Integration

As a lower-latency version of LVB, LEB provides superb **live streaming** experience with millisecond playback latency, far lower than that of live stream playback using traditional protocols.
Before you use LEB, please read [LEB Billing Overview](https://intl.cloud.tencent.com/document/product/267/39969) to learn about its billable items and pricing.

> **Note:**LEB uses the WebRTC protocol to ensure low latency. It adopts the Opus codec and does not support B-frames. If the original stream contains B-frames or the codec is not Opus, the CSS backend will remove the B-frames and transcode the stream to Opus format, which will incur [standard transcoding fees](https://intl.cloud.tencent.com/document/product/267/39604).

## Integration into Application

### Directions

- **Live push**: Capture from the camera or phone screen and push the stream to CSS using the RTMP protocol. For details, see [Publishing (Camera)](https://www.tencentcloud.com/document/product/1071/38157) and [Publishing (Screen Recording)](https://www.tencentcloud.com/document/product/1071/41878).
- **Live playback**: Play streams using WebRTC with ultra-low latency. For details, see [Playback > LEB](https://www.tencentcloud.com/document/product/1071/41875).

> **Note:**The MLVB SDK leverages the capabilities of CSS, IM, TRTC, and other services to implement low-latency audio/video communication for multiple parties, allowing participants to interact with each other while others watch. For details, see [Mic Connect](https://www.tencentcloud.com/document/product/1071/42210).

### Free demo

TCToolkit is an open-source and comprehensive audio/video solution developed by Tencent Cloud. You can use it to try out LEB’s capability to play live streams with millisecond latency.

| Platform | Demo | Push Demonstration (Android) | Playback Demonstration (Android) |
| --- | --- | --- | --- |
| Android | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/f2ab2891374411eeb231525400c56988.png) | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/01a83b0a374511ee96d3525400088f3a.png)  | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/0fff49fe374511ee96d3525400088f3a.png)   |
|  |  | iOS | Under maintenance |

## Integration into Webpage

### Directions

- **Live push on web**: The push component is designed and packaged according to the WebRTC standard, which is supported by most browsers. You can enable the live push feature simply by importing the code we provide. For details, see [WebRTC Push](https://intl.cloud.tencent.com/document/product/267/41620).

> **Note:**The Opus audio codec is used for the push of WebRTC streams. Therefore, if you use an LVB protocol (RTMP, HTTP-FLV, or HLS) for playback, the CSS backend will automatically convert the audio to AAC format to ensure successful playback, which will incur audio transcoding fees. For details, see [Live Transcoding > Audio Transcoding](https://intl.cloud.tencent.com/document/product/267/39604). If you publish and play streams using the LEB protocol, CSS will not transcode the audio.With WebRTC, each push domain can be used for up to **1,000 concurrent streams** by default. If you want to push more streams, please [submit a ticket](https://console.tencentcloud.com/workorder/category).

- **Live playback on web**: We recommend you use our web player SDK [TCPlayerLite](https://www.tencentcloud.com/document/product/266/33977), which supports playing **WebRTC streams** on mobile and desktop browsers and delivers a superb streaming experience with millisecond latency, far lower than that of playback using traditional live streaming protocols.

> **Note:**If a browser does not support WebRTC, a WebRTC URL passed into the player will be converted to better support playback. By default, WebRTC is converted to HLS on mobile browsers and HTTP-FLV on desktop browsers.

### Free demo

- **Live push on web**: You can test the web push feature in [Web Push](https://console.tencentcloud.com/live/tools/webpush) of the CSS console.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4fc6582e52ad11eeabd75254005810a4.png)

- **Live playback on web**: You can use the [TCPlayer demo](https://www.tencentcloud.com/document/product/266/33977) to test playback on web.

> **Note:**Both live push and playback on web use the standard WebRTC protocol. Web push does not generate B-frames, and audio is encoded in Opus format, so there will be no costs of audio transcoding or B-frame removal.

## Implementing WebRTC Push Using OBS

LEB (ultra-low-latency live streaming) uses WebRTC to push live audio/video or video files to the CSS server. The following describes how to use OBS to push WebRTC streams.

OBS supports WebRTC protocol live streaming, which means you can easily and quickly push live streams to Tencent Cloud CSS using the WebRTC protocol on PC (Windows/Mac/Ubuntu), just like using the RTMP protocol. The following content mainly introduces how to use the OBS tool to implement WebRTC protocol live streaming functionality.

> **Note：****There are two schemes, new and old, to choose from when integrating OBS with WebRTC protocol live streaming**:New Scheme - OBS WebRTC Live Streaming (OBS v30.0 Beta 1 or higher): This scheme does **not require a plugin**, making the integration process more convenient. For specific operation guidance, please refer to:[OBS WebRTC live streaming](https://www.tencentcloud.com/document/product/267/57042#).Old Scheme - Using OBS Plugin for WebRTC Live Streaming: If you are using an OBS version lower than v30.0 Beta 1 and cannot directly use the WebRTC protocol for live streaming, Tencent Cloud CSS provides an integrated OBS plugin solution for WebRTC live streaming. For specific operation guidance, please refer to: [OBS Plugin for WebRTC Live Streaming](https://www.tencentcloud.com/document/product/267/57042#a1ac1dab-cad0-4ebf-ad2f-9a20d82a0057).

Based on your actual requirements and OBS version, you can choose the appropriate WebRTC live streaming solution. Please note that the actual streaming performance may be affected by factors such as device performance, network conditions, and player buffering. During the usage process, you can adjust the streaming parameters and tools according to your needs to optimize the live streaming experience.

### LEB playback

For how to use the MLVB SDK for LEB playback, see [Playback > (LEB)](https://www.tencentcloud.com/document/product/1071/41875).


---
*Source: [https://www.tencentcloud.com/document/product/267/42131](https://www.tencentcloud.com/document/product/267/42131)*
