# Smart Highlight Event Notification

If you have configured the Live Streaming Smart Highlight Callback address, upon clip generation completion, the backend will transmit the generated clip information in JSON format to your designated callback URL. You may subsequently process this callback data for further operations.

This document primarily introduces the callback message notification fields sent by Tencent Cloud Streaming Services (CSS) to users upon triggering the Smart Highlight Callback event.

## Note

This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://www.tencentcloud.com/document/product/267/38080).

## Smart Highlight Event Parameters

### Event type

| Event Type | Value |
| --- | --- |
| Smart Highlight | event_type = 349 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal UNIX timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. sign = MD5(key + t). Note: Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note****：**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/00aedfaac9ca11f0a93d52540044a08e.png)

### Smart Highlight Callback message parameters

| Parameter | Type | Description |
| --- | --- | --- |
| appid | int | User [APPID](https://console.tencentcloud.com/developer). |
| domain | string | Push domain name. |
| path | string | Push stream path. |
| stream_id | string | Stream ID. |
| items | Array of [Smart Highlight information](#00214027-0c90-4052-bb2e-2a221d0b15df) | Smart Highlight information |

### Smart Highlight information

| Parameter | Type | Description |
| --- | --- | --- |
| begin_time | int64 | Smart Highlight start time, in UNIX timestamp (seconds). |
| end_time | int64 | Smart Highlight end time, in UNIX timestamp (seconds). |
| title | string | Title. |
| summary | string | Summary. |
| video_store_url | string | Smart Highlight video URL. |
| cov_img_store_url | string | Smart Highlight video cover URL. |
| key_words | Array of string | Keywords. |

### Sample callback

```
{    "event_type": 349,    "appid": 1234,    "domain": "your.livepush.myqcloud.com",    "path": "highlight",    "stream_id": "test1820",    "items": [        {            "begin_time": 1761128808,            "end_time": 1761128834,            "title": "Bed sheets on flash sale, price reduced by 25 yuan!",            "summary": "The live streamer bargained down the price, reducing the price of XX Province coarse cloth bed sheets from 60 yuan/meter to 25 yuan. The 2×2.5 meter edged version is available for a limited time only through link number one.",            "video_store_url": "http://your.cos.ap-nanjing.myqcloud.com/SmartHighlights/your.livepush.myqcloud.com/highlight/test1820/LIVE_0269433B4282FE8263010F7AF99BA792BC-1761128792340/2025-10-22_18-32-16_16666.mp4",            "cov_img_store_url": "",            "key_words": [                "25 yuan",                "Link number one",                "XX Province Coarse Cloth",                "Bed sheet flash sale",                "Limited time"                ]        }    ]}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/74672](https://www.tencentcloud.com/document/product/267/74672)*
