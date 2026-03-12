# Evaluation Threshold Event Notification

If you have configured an evaluation threshold callback URL, during the assessment process, the backend will automatically send results meeting the threshold criteria to your callback address in JSON format. You may utilize this callback data for subsequent processing operations.

This document primarily elucidates the callback notification fields transmitted by Tencent Cloud Streaming Services (CSS) to users upon triggering the evaluation threshold event.

## Note

This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).

## Evaluation Threshold Event Parameters

### Event type

| Event Type | Value |
| --- | --- |
|  Evaluation threshold | event_type = 344 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal Unix timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. sign = MD5(key + t). Note: Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note:**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/6bf88bd0cb6711f0aedb525400454e06.png)![](https://staticintl.cloudcachetci.com/cms/backend-cms/2a581f76840a11f0b321525400e889b2.png)

### Callback message parameters

| Parameter | Data Type | Description |
| --- | --- | --- |
| appid | int | Business ID. |
| appname | string | Push stream path. |
| stream_id | string | Stream ID. |
| domain | string | Push domain name. |
| event_time | int64 | The time the request was sent, in UNIX timestamp (seconds). |
| transcode_template_id | int | Transcoding template ID. |
| watermark_template_id | int | Watermark template ID. Reference evaluation (PSNR/SSIM/VMAF) only evaluates transcoded streams. No watermark template ID is provided. |
| frames | Array of [Frame](#labelresult) | The score and time below the threshold during the evaluation period. |
| function | string | Function category: Assessment. |
| class | string | Specific evaluation types:PSNRSSIMVMAFScoring Without Reference(VQA) |

#### Frame

Single frame evaluation score and time.

| Name | Type | Description |
| --- | --- | --- |
| score | float | score. |
| time | int64 | UNIX timestamp in milliseconds. |

### Sample callback

```
{    "event_type": 344,    "appid": 1234576,    "appname": "live",    "domain": "abc.record.test.org",    "stream_id": "livestream1",    "transcode_template_id": 12345,    "event_time": 1752130787,    "frames": [        {            "score": 22.78,            "time": 1752130785280        },        {            "score": 32.75,            "time": 1752130786281        }    ],    "function": "Assessment",    "class": "PSNR"}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/73167](https://www.tencentcloud.com/document/product/267/73167)*
