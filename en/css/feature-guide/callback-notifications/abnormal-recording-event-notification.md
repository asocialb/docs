# Abnormal Recording Event Notification

The abnormal recording event callback is mainly used to call back the specific information on abnormal events that occurred during the recording process. You need to configure a URL for receiving abnormal recording event callback notifications. The Tencent CSS backend will call back the results and send them to the target server you set.

This document describes fields in callback notifications sent by Tencent CSS to users after the abnormal recording event callback is triggered.

## Must-Knows

Before reading this document, you should know how to configure the callback feature of Tencent CSS and how to receive callback notifications. For details, see [How to Receive Event Notifications](https://www.tencentcloud.com/document/product/267/38080).

## Abnormal Recording Event Parameters

### Event Type

| Event Type | Value |
| --- | --- |
| Abnormal recording event | event_type = 341 |

### Common Callback Parameter

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal Unix timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. **sign = MD5(key + t).** Note: Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note:**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/a5f3c96ccb6711f08942525400e889b2.png)

### Callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| appid | int | User [APPID](https://console.tencentcloud.com/developer). |
| stream_id | string | Live stream name. |
| session_id | string | ID of the live streaming recording session. It is used to distinguish different recording tasks. |
| file_format | string | Recording file format, including FLV, TS, MP4, and AAC. |
| timestamp | int | Callback time of an abnormal recording event (unit: seconds). |
| exception_level | string | Exception level, including info, warning, and error. |
| exception | json | Detailed abnormal event description. |

### Parameters of exception

| Parameter | Type | Description |
| --- | --- | --- |
| type | int | [Abnormal event type](#b1208801-ad7a-4e79-8c36-b2ca1fce9e5a). |
| occurs | int | Number of occurrences within the statistical cycle of abnormal events. |
| desc | string | Abnormal event description. |

#### Abnormal event type.

| Type | Description |
| --- | --- |
| -8 | The audio timestamp changes greatly. |
| -9 | The video timestamp changes greatly. |
| -10 | The audio and video timestamps differ greatly. |
| -11 | The video timestamp is invalid. |
| -16 | Failed to pull the stream. |
| -17 | No audio is pushed when audio recording is set for streaming. |
| -18 | No video is pushed when video recording is set for streaming. |
| -22 | The audio timestamp does not change. |
| -23 | The video timestamp does not change. |
| -24 | The audio timestamp is invalid. |
| -100 | The resolution for streaming pushing has changed. |
| -104 | An error occurred while writing audio/video frames to containers (files). |
| -120 | The recording file is truncated due to a video encoding method change. |
| -130 | Abnormal video frames are dropped. |
| -131 | Abnormal audio frames are dropped. |
| -132 | The GOP length is abnormal. |
| -200 | The audio timestamp does not increase evenly. |
| -201 | The video timestamp does not increase evenly. |

> **Note:**Currently, the abnormal recording event callback does not support configuration for individual events and only performs callbacks for currently occurring abnormal events. If no abnormal event occurs, no callback is performed.The abnormal recording event callback performs statistics only on current abnormal recording events. To avoid frequent callbacks, the same abnormal events occurred in a short time will be merged for processing. Therefore, abnormal event callbacks may have a delay (not exceeding 2 minutes). No other operations will be performed in the recording backend except abnormal event detection and abnormal event callback.

### Callback Example

```
{    "interface":"general_callback",    "event_type":341,    "appid":1234567,    "domain":"1234567.livepush.myqcloud.com",    "path":"live",    "stream_id":"test_stream_35b4a6e6d4261",    "session_id":"1855245773800540059",    "file_format":"ts",    "timestamp":1739934527,    "exception_level":"info",    "exception":    {        "type":-201,        "desc":"video ts deviation: 100.000000",        "occurs":4    },    "sign": "ca3e25e5dc17a6f9909a9ae7281e300d",  "t": 1754623810}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/68622](https://www.tencentcloud.com/document/product/267/68622)*
