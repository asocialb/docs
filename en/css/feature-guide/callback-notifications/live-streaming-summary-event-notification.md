# Live Streaming Summary Event Notification

If you have configured a Live Streaming Summary Callback address, upon summary generation, the backend will deliver the created summary in JSON format to your designated callback URL. You may subsequently process this callback content as needed.

This document primarily describes the callback notification fields transmitted by Tencent Cloud Streaming Services (CSS) to users upon triggering the Live Streaming Summary Callback event.

## Note

This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://www.tencentcloud.com/document/product/267/38080).

## Live Streaming Summary  Event Parameters

### Event type

| Event Type | Value |
| --- | --- |
| Live Streaming Summary | event_type = 348 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the UNIX timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal UNIX timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. sign = MD5(key + t). Note: Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note****：**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/f987ffa8c9c911f0a4a55254001c06ec.png)

### Live Streaming Summary Information

| Parameter | Type | Description |
| --- | --- | --- |
| appid | int | User [APPID](https://console.tencentcloud.com/developer). |
| domain | string | Push domain name. |
| path | string | Push stream path. |
| stream_id | string | Stream ID. |
| begin_time | int64 | Summary start time, in UNIX timestamp (seconds). |
| end_time | int64 | Summary end time, in UNIX timestamp (seconds). |
| title | string | Summary title. |
| summary | string | Summary. |
| key_words | array of string | Summary keyword. |
| key_points | array of string | Summary points. |

### Sample callback

```
{    "event_type": 348,    "appid": 1234,    "domain": "your.livepush.myqcloud.com",    "path": "live",    "stream_id": "test1820",    "begin_time": 1761211980,    "end_time": 1761212541,    "title": "Live broadcast promoting coarse cloth bedding from XX province",    "summary": "This live broadcast mainly introduced the promotional activities of traditional coarse cloth bedding products from XX Province, including sheets, duvet covers, pillowcases and other products. It emphasized the characteristics of Xinjiang cotton material, breathability and moisture absorption, no pilling and no fading, and offered significant price discounts.",    "key_points": [        "Product Features and Material Introduction",        "Promotional activities and price discounts"    ],    "key_words": [        "three piece set",        "Shandong coarse cloth",        "bedding promotion",        "Xinjiang cotton"    ]}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/74671](https://www.tencentcloud.com/document/product/267/74671)*
