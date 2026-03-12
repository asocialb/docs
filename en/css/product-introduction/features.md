# Features

This document provides a list of what you can do with CSS. You can find more information about each feature by reading their documents.

### Push

| Feature | Description |
| --- | --- |
| [Push protocol support](https://intl.cloud.tencent.com/document/product/267/7968) | Supports RTMP, SRT, WebRTC, and RTMP over SRT protocols for push. |
| [Push tool support](https://intl.cloud.tencent.com/document/product/267/31558) | Supports Tencent Cloud’s MLVB SDK (which comes in iOS, Android, and web editions) or third-party streaming software such as OBS, XSplit, and FMLE. |
| Push device support | Supports common third-party RTMP streaming devices, encoders, and set-top boxes. |

### Playback

| Feature | Description |
| --- | --- |
| [Playback protocol support](https://intl.cloud.tencent.com/document/product/267/7968) | Supports RTMP, FLV, HLS, and WebRTC playback protocols. |
| [Playback tool support](https://intl.cloud.tencent.com/document/product/267/31559) | Supports Tencent Cloud’s MLVB SDK (which comes in iOS, Android, and web editions) or third-party FLV, RTMP, or HLS players. |
| Playback control | Plays the original stream or a stream transcoded in real time. |

### Live Streaming Management

| Feature | Description |
| --- | --- |
| Management | Manages live streams graphically in the console or using APIs. |

### CSS console

| Section | Description |
| --- | --- |
| [Overview](https://intl.cloud.tencent.com/document/product/267/31054) | Displays data such as traffic package usage or real-time bandwidth and traffic usage. |
| [Domain Management](https://intl.cloud.tencent.com/document/product/267/35970) | Supports adding, modifying, disabling and deleting push and playback domains, as well as configuring CNAME, HTTPS certificates, and push and playback authentication. |
| [Stream Management](https://intl.cloud.tencent.com/document/product/267/31068) | Query online streams, primary and secondary streams, historical streams, and blocked streams for live stream information. |
| [Scenario-Specific Services](https://intl.cloud.tencent.com/document/product/267/34223) | Query or modify the [Live Watermark](https://www.tencentcloud.com/document/product/267/31073), [Live Transcoding](https://www.tencentcloud.com/document/product/267/31071), [Live Recording](https://www.tencentcloud.com/document/product/267/34223), [Live Time Shift](https://www.tencentcloud.com/document/product/267/53312), [Live Screenshot](https://www.tencentcloud.com/document/product/267/31072), [Live Audit](https://www.tencentcloud.com/document/product/267/58265), [Live Adaptive Bitrate](https://www.tencentcloud.com/document/product/267/50271), [Live Padding](https://www.tencentcloud.com/document/product/267/53400), [Live Subtitle](https://www.tencentcloud.com/document/product/267/58144), [Live Callback](https://www.tencentcloud.com/document/product/267/31074) and [DRM Encryption Configuration](https://www.tencentcloud.com/document/product/267/48068) configuration information. |
| [Data Center](https://intl.cloud.tencent.com/document/product/267/31076) | Supports querying usage statistics including bandwidth, traffic, requests, concurrent connections, screenshots, push channels, and recording channels. |

### Security

| Feature | Description |
| --- | --- |
| [Push authentication](https://intl.cloud.tencent.com/document/product/267/31059) | Generates hotlink protection push URLs (you can use your own key and specify the expiration time). |
| [Playback authentication](https://intl.cloud.tencent.com/document/product/267/31060) | Generates hotlink protection playback URLs using IP allowlist/blocklist or the referer field; supports remote playback authentication. |
| [DRMencryption](https://www.tencentcloud.com/document/product/267/48068) | Encrypts videos based on DRM schemes including Widevine, FairPlay, or NormalAES to prevent unauthorized recording and hotlinking. |

### APIs

| API Category | Description |
| --- | --- |
| [Domain management APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Add, delete, query, enable, and disable push and playback domains, as well as modify playback domains. |
| [Delayed Playback management APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Delay playback, query delayed playbacks, and resume real-time playback. |
| [Recording management APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Create, delete, and end recording tasks, create, delete, query, and modify recording templates, as well as create, delete, and query recording rules. |
| [Screencapturing and Porn Detection APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Create, delete, and query recording rules, as well as create, delete, query, and modify recording templates. |
| [Watermark management APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Add, delete, query, and modify watermarks, as well as create, delete, and query watermark rules. |
| [Live callback APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Create, delete, and query callback rules, as well as create, delete, query, and modify callback templates. |
| [Stream pulling APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Add, delete, query, and modify pull configurations. |
| [Live stream management API](https://intl.cloud.tencent.com/document/product/267/30760) | Query disabled, ongoing, and historical streams, query push interruptions and stream status, stop streams, block streams, and resume streams. |
| [Live transcoding APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Create, delete, and query transcoding rules, as well as create, delete, query, and modify transcoding templates. |
| [Billing data query APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Query billable bandwidth and traffic usage, query playback data by region and ISP, query HTTP status codes for playback requests, query domain-level playback data in real time, and query packages. |
| [Certificate management APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Add, delete, bind, unbind, and query certificates, as well as query and change the domains bound with a certificate. |
| [Authentication management APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Query and modify authentication keys for playback and push. |
| [Time shifting APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Create, delete, query, and modify time shifting templates, create, delete, and query time shifting rules, as well as query time-shifted streams. |
| [Live stream mix APIs](https://intl.cloud.tencent.com/document/product/267/30760) | Mix streams and cancel stream mixing. |

### Value-added services

| Feature | Description |
| --- | --- |
| [Live transcoding](https://intl.cloud.tencent.com/document/product/267/31561) | Transcodes a stream into different specifications. |
| [Live recording](https://intl.cloud.tencent.com/document/product/267/31563) | Records live streams (by calling an API) and saves the recording files to Tencent Cloud VOD or COS. |
| [Live screencapturing](https://intl.cloud.tencent.com/document/product/267/31562) | Takes screenshots of a live stream (by calling an API) and saves them to Tencent Cloud VOD or COS. |
| [Exciting Live Clips](https://www.tencentcloud.com/document/product/267/57261) | Supports the exciting live clip feature. Relying on the live time shift capability, you can select an exciting clip during or after the live streaming process to generate a time-shifted playback URL for easy secondary distribution of the exciting live clip. |
| [Porn detection](https://intl.cloud.tencent.com/document/product/267/31564) | Recognizes pornographic content in live streams. |
| [RTC-based communication](https://www.tencentcloud.com/document/product/1071/42210) | Supports communication among participants with ultra-low latency (powered by Tencent Cloud TRTC). |
| [Time shifting (new)](https://www.tencentcloud.com/document/product/267/31565) | Plays ongoing streams from earlier time points. |
| [Overseas Live Acceleration](https://www.tencentcloud.com/document/product/267/31567) | Supports the use of Tencent CSS services outside the Chinese Mainland. |

### SDKs

| SDK | Description |
| --- | --- |
| [MLVB SDK](https://intl.cloud.tencent.com/document/product/1071) | Offers capabilities including stream pushing, basic beautification, filters, playback, and time shifting. |
| [Tencent Effect SDK](https://www.tencentcloud.com/document/product/1143) | Offers capabilities including filters, beautification, stickers, and gesture recognition for different shooting scenarios (the SDK is a video processing solution developed jointly by Tencent Cloud, Pitu, and YouTu). |

### LVC

| Feature | Description |
| --- | --- |
| [LVC](https://www.tencentcloud.com/document/product/267/58532) | Cloud switching of live streams, multi-screen custom layout with mixed streaming, and synchronous audio and video switching, enriching online service scenarios. |

### Relay

| Feature | Description |
| --- | --- |
| [Relay](https://www.tencentcloud.com/document/product/267/42524) | Offer a feature for pulling video live streams or on-demand files from third-party platforms and pushing them to CSS, enabling direct operations such as stream mixing and recording on the audio and video content, and easily achieving cross-platform distribution and VOD to live streaming capabilities. |


---
*Source: [https://www.tencentcloud.com/document/product/267/2823](https://www.tencentcloud.com/document/product/267/2823)*
