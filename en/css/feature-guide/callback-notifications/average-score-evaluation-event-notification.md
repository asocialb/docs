# Average Score Evaluation Event Notification

If you have configured an Average Score Evaluation callback URL, the system will automatically send the evaluation results in JSON format to your designated callback address during the assessment process. You may then utilize this callback data for subsequent processing

This document primarily elucidates the callback notification fields transmitted by Tencent Cloud Streaming Services (CSS) to users upon triggering the average score evaluation event.

## Note

This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).

## Average Score Evaluation Event Parameters

### Event type

| Event Type | Value |
| --- | --- |
| Average Score Evaluation | event_type = 345 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the UNIX timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal UNIX timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. sign = MD5(key + t). Note: Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note:**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/72960661cb6711f09e745254007c27c5.png)

### Callback parameters

| Parameter | Data Type | Description |
| --- | --- | --- |
| appid | int | Business ID. |
| appname | string | Push stream path. |
| stream_id | string | Stream ID. |
| domain | string | Push domain name. |
| event_time | int64 | The time the request was sent, in UNIX timestamp (seconds). |
| transcode_template_id | int | Transcoding template ID. |
| watermark_template_id | int | Watermark template ID. Reference evaluation (PSNR/SSIM/VMAF) only evaluates transcoded streams. No watermark template ID is provided. |
| frames | Array of [Frame](#labelresult) | The score and time of each frame during the evaluation period. |
| average_score | float | The average score during the evaluation period. |
| max_score | float | The maximum score within the evaluation period. |
| min_score | float | The minimum score within the evaluation period. |
| function | string | Function category: Assessment. |
| class | string | Specific evaluation types:PSNRSSIMVMAFScoring Without Reference(VQA) |

#### Frame

Single frame evaluation score and time.

| Name | Type | Description |
| --- | --- | --- |
| score | float | Score. |
| time | int64 | UNIX timestamp in milliseconds. |

### Sample callback

```
{    "event_type": 344,    "appid": 1234576,    "appname": "live",    "domain": "abc.record.test.org",    "stream_id": "livestream1",    "transcode_template_id": 12345,    "event_time": 1752130787,    "frames": [        {            "score": 22.78,            "time": 1752130785280        },        {            "score": 32.75,            "time": 1752130786281        }    ],    "average_score": 27.765,    "max_score": 32.75,    "min_score": 22.78,    "function": "Assessment",    "class": "PSNR"}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/73168](https://www.tencentcloud.com/document/product/267/73168)*
