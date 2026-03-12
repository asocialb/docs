# Live subtitles Event Notification

This document mainly describes the callback notification fields sent to users when Tencent Cloud Streaming Service (CSS) triggers a live subtitle event.

## Note

- This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).
- Callback information is only returned when pulling subtitle streams.

## Event Message Notification Protocol

**Network Protocols**

- **Request**: Utilize an HTTP POST request with the body content in JSON format. The specific body content for each message type is detailed in the subsequent sections.
- **Response**: The HTTP status code is 200. While the server disregards the specific content of the response packet, for protocol compatibility, it is recommended that the client includes a JSON payload in the response: `{"code":0}`.

**Message Reliability**

The Event Notification Service incorporates a retry mechanism with a total of 3 attempts. To prevent potential impact on your server performance and network bandwidth due to retries, please ensure proper response packets are returned. The conditions triggering retries are as follows:

- No response packet received for an extended duration.
- The HTTP status code returned is not 200.

## Live subtitles Event Parameters

### Event type

| Event Type | Value |
| --- | --- |
| Live subtitles | event_type = 338 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal Unix timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. sign = MD5(key + t). Tencent Cloud splices the encryption **key** and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note:**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/9884fd08cb6711f084a45254005ef0f7.png)

### Callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| appid | int | User [APPID](https://console.tencentcloud.com/developer). |
| stream_id | string | Live stream name. |
| channel_id | string | Same as the live stream name. |
| task_id | string | Subtitle task ID. |
| data | [Struct of data](#data) | Process the results. |

| Parameter | Type | Description |
| --- | --- | --- |
| subtitle_tmp_res | [Array of subtitle_tmp_res](#subtitle_tmp_res) | Subtitle text results. |

| Parameter | Type | Description |
| --- | --- | --- |
| src_txt | string | Original audio recognition text. |
| dst_txt | string | The translated text. If no translation is configured, this value is not returned. |
| start_pts | int64 | src_txt corresponds to the timestamp starting point of the audio stream, in milliseconds (ms). |
| end_pts | int64 | src_txt corresponds to the timestamp end point of the audio stream, in milliseconds (ms). |
| start_unix_time | int64 | src_txt corresponds to the UNIX time starting point of the live broadcast. |
| end_unix_time | int64 | src_txt corresponds to the UNIX time end point of the live broadcast. |
| steady_state | bool | Steady state flag: When true, it indicates that the sentence has entered a stable state and the text will no longer be revised. |

### Sample callback

```
{  "event_type": 338,  "stream_id": "teststream",  "channel_id": "teststream",  "task_id": "7735333",  "data": {    "subtitle_tmp_res": [      {        "src_txt": "Today we shall delve into the study of linear equations in one variable.",        "start_pts": 123000,        "end_pts": 126333,		"stead_state": bool      }    ]  },  "sign": "ca3e25e5dc17a6f9909a9ae7281e300d",  "t": 1754623810}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/73170](https://www.tencentcloud.com/document/product/267/73170)*
