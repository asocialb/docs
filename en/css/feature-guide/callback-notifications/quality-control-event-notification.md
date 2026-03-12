# Quality Control Event Notification

If you have configured a Quality Control callback address, during the Quality Control process, the backend will send the results in JSON format to your callback URL. You may utilize the callback content to perform subsequent processing operations.

This document primarily elucidates the callback notification fields transmitted by Tencent Cloud Streaming Services (CSS) to users upon triggering the quality control event.

## Note

This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).

## Quality Control Event Parameters

### Event type

| Event Type | Value |
| --- | --- |
| Quality Control callback | event_type = 343 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal Unix timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. sign = MD5(key + t). Note: Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note:**You can set the callback **key** in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/65519e84cb6711f0a93d52540044a08e.png)

### Callback parameters

| Parameter | Data Types | Description |
| --- | --- | --- |
| appid | int | Application ID. |
| appname | string | Push stream path. |
| stream_id | string | Stream ID. |
| domain | string | Push domain name. |
| event_time | int64 | Request timestamp, UNIX epoch time (in seconds). |
| transcode_template_id | int | Transcoding template ID. |
| watermark_template_id | int | Watermark template ID. |
| score | float | The actual score value. |
| function | string | Function category: QualityControl. |
| class | string |  Quality Control exception type. |

### Quality Control Exception Types

#### Format Exception Types

| Category | Abnormal phenomenon |  Abnormal cause |  Abnormal diagram |  Possible causes and troubleshooting suggestions |
| --- | --- | --- | --- | --- |
| VideoResolutionChanged | The video resolution changes. | The video resolution changes. | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/1271f6857dab11f0bd33525400454e06.png) | This is usually caused by re-streaming after switching the screen from landscape to portrait. We recommend checking the video input device (such as a camera). |
| AudioSampleRateChanged | Audio playback is abnormal. | Audio sampling rate changes. | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/125a82607dab11f09cab525400bf7822.png) | This usually occurs because the audio encoder parameters have been reset on the streaming side. We recommend checking the audio input device (such as a microphone) and streaming software settings. |
| AudioChannelsChanged | Audio playback is abnormal. | The number of audio channels changes. | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/1213efba7dab11f09e56525400e889b2.png) | This is usually because the audio encoder parameters have been reset on the streaming side. We recommend checking the audio input device (such as a microphone) and streaming software settings. |
| ParameterSetsChanged | Video playback is abnormal. | For example, the VPS/SPS/PPS changes of H265/H264 and the decoder information changes of AAC. | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/122ea92e7dab11f0960452540044a08e.png) | This is usually because the audio and video encoder parameters have been reset on the streaming side. It is recommended to use Tencent Cloud's live streaming transcoding function. |
| DarOrSarInvalid | The video has an unusual aspect ratio. | The video has an unusual aspect ratio. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/86237f998e2111f0ae9d5254001c06ec.png) | This is usually caused by an internal error in the encoder. It is recommended to use the Tencent Cloud Live Streaming (CSS) transcoding function. |
| TimestampFallback | Video playback is slow or distorted. | DTS timestamp fallback. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/2ec8d6d28e2811f0bd05525400454e06.png) | This is usually caused by an internal error in the encoder. It is recommended to use the Tencent Cloud Live Streaming (CSS) transcoding function. |
| DtsJitter | Video playback is stuck. | DTS has too much jitter. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/51eab5708e2811f0974b52540044a08e.png) | This is usually caused by an internal error in the encoder. It is recommended to use the Tencent Cloud Live Streaming (CSS) transcoding function. |
| PtsJitter | Video playback is stuck. | PTS jitter is too large. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/597ee8bf8e2811f0818a52540099c741.png) | This is usually caused by an internal error in the encoder. It is recommended to use the Tencent Cloud Live Streaming (CSS) transcoding function. |
| AACDurationDeviation | Audio playback is choppy. | The AAC frame timestamp interval is unreasonable.The AAC frame timestamp interval is 1024/48 kHz = 21.3 ms. If the frame interval is much smaller or larger than this value, the AAC frame timestamp distribution is uneven. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/3750383b8e2311f084bd5254007c27c5.png) | This is usually caused by an internal error in the encoder. It is recommended to use the Tencent Cloud Live Streaming (CSS) transcoding function. |
| AudioDroppingFrames | Audio playback is choppy. | Audio Frame Loss:For AAC streams, similar to AACDurationDeviation, when the difference between the timestamps of two adjacent frames is greater than twice the theoretical frame interval (for example, 21.3ms at 48KHz), it can be determined that a frame may have been lost.For other streams, if no audio frames are received within 1 second, it is considered frame loss, which may cause audio playback abnormalities. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/708789d38e2311f0814e525400bf7822.png) | This is usually caused by an unstable network. It is recommended to check the network stability. |
| VideoDroppingFrames | Video playback is stuck. | Video frame loss (no video frame is received for more than 1 second). |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/978937d18e2311f0974b52540044a08e.png) | This is usually caused by an unstable network. It is recommended to check the network stability. |
| AVTimestampInterleave | The audio and video playback are not synchronized. | The audio and video interweaving is unreasonable. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/d66b47938e2311f088af5254005ef0f7.png) | This is usually caused by asynchrony of audio and video interleaving timestamps. It is recommended to first check whether the audio and video sources are complete, and then check whether the container encapsulation is abnormal. |
| FpsJitter | Audio and video playback is choppy. | The stream frame rate jitter calculated using PTS is too large. | - | This is usually caused by insufficient encoder performance or network jitter. It is recommended to first check the encoder machine load and then check the network stability. |
| StreamOpenFailed | The video cannot be played. | Stream open failed. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/ae3f57908e2811f0ae9d5254001c06ec.png) | This is usually caused by abnormal streaming network, invalid streaming address, failed streaming authentication, etc. It is recommended to check the streaming software settings. |
| StreamParseFailed | The video cannot be played. | Stream parsing failed. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/d482e6f58e2811f0ae9d5254001c06ec.png) | This is usually caused by corrupted streaming data. We recommend checking the streaming software status and network stability. |
| VideoFirstFrameNotIdr | The video cannot be played. | The first frame is not an IDR frame. |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/0501d92b8e2411f0814e525400bf7822.png) | This is usually caused by abnormal encoding or data transmission. It is recommended to first check whether the file can be played normally after encoding and before streaming, and then check whether the data transmitted by streaming is complete. |

#### Content exception type

| Category | Abnormal phenomenon | Exception example | Abnormal causes and troubleshooting suggestions |
| --- | --- | --- | --- |
|  Mosaic | Mosaic | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/127ecbfc7dab11f080fb5254005ef0f7.jpeg) | There may be a problem with the encoder during encoding, or data may be lost during transmission. |
|  CrashScreen | Crash screen | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/12485b387dab11f09cab525400bf7822.jpeg) | Check whether the video source data is damaged. |
|  Blur | Blur | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/12306f857dab11f09cab525400bf7822.jpeg) | It may be due to inaccurate focusing, lens covered with dust and moisture, or artificial smearing and obstruction. |
|  VideoNoise | Video noise | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/122c83b87dab11f0914f52540099c741.jpeg) |  It may be due to a camera malfunction. |
| VideoJitter | Video jitter | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/12734c017dab11f09a9a5254001c06ec.png) | It may be due to the instability of the camera or gimbal, or it may be caused by the shooting technique. |
|  LowLight | Low light | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/127d5e507dab11f0bda35254007c27c5.jpeg) | There may be a camera malfunction or the shooting environment may be dim. |
| Overexposure | Overexposure | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/121c62777dab11f0914f52540099c741.jpeg) | There may be a camera failure or the shooting environment may be too bright. |
|  BlackWhiteEdge | Black edges, white edges, black screen, white screen | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/122b31007dab11f0bd33525400454e06.jpeg) | The automatic filling may be caused by the inconsistency between the edited video resolution and the actual resolution. |
| SolidColorScreen | Solid color screen |  ![](https://staticintl.cloudcachetci.com/cms/backend-cms/1253a56a7dab11f09e56525400e889b2.jpeg) | The video may be blocked or erroneous. |
| QRCode/Barcode/AppletCode |  QR code/Barcode/Applet code | ![](https://staticintl.cloudcachetci.com/cms/backend-cms/1276975d7dab11f09a9a5254001c06ec.png) | Check whether the video content is normal. |
| Silence | Audio Muting | - | Check whether the audio recording is normal. |
| LowVoice | Audio volume is too low | - | Check whether the audio recording is normal. |
| HighVoice | Audio clipping | - | Check whether the audio recording is normal. |

### Sample callback

```
{    "event_type": 343,    "appid": 12345678,    "appname": "live",    "stream_id": "test",    "domain": "abc.record.test.org",    "event_time": 1747818881,    "score": 44.15314104741461,    "transcode_template_id": 123456,    "watermark_template_id": 123457,    "function": "QualityControl",    "class": "Blur"}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/73166](https://www.tencentcloud.com/document/product/267/73166)*
