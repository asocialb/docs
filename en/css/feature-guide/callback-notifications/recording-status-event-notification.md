# Recording Status Event Notification

The live recording feature records live streams in real time according to the recording template bound to the push domain name, and then stores the recording files in VOD. A recording status callback notifies you of the status of a recording task, including whether it started or ended successfully, when it is paused and resumed successfully, and if any recording errors occur. To receive recording callbacks, you need to configure a callback template, specify a server address for the callback, and bind the template to your push domain name. When a recording event occurs, the CSS backend will send the recording file information to the specified server.

This document describes the fields in a callback notification sent by CSS after a recording status event occurs.

## Notes

- This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).
- In the relay recording callback, the stream ID refers to the Task ID of the relay task.

## Description of recording status callback parameters

### Event type

| Event Type | Explanation of Field Value |
| --- | --- |
| Live Recording | event_type = 332 |

### Common callback parameters

| Field Name | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration Time: UNIX timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. After the time specified by the **t** value elapses, a notification will be considered invalid. This can prevent network replay attacks.The value of **t** is a decimal UNIX timestamp, which is the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | The security signature, **sign = MD5(key + t)**. Note: Tencent Cloud splices the encryption **key** and **t**, generates an MD5 hash of the spliced string, and embeds it in callback notifications. Your backend server performs the same calculation when it receives a callback, and if the signature matches, it indicates that the notification is from Tencent Cloud. |

> **Note:**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.intl.cloud.tencent.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/479e3f5ccb6711f084a45254005ef0f7.png)

### Recording status callback message parameters

| Field Name | Type | Description |
| --- | --- | --- |
| appid | int | User [APPID](https://console.intl.cloud.tencent.com/developer) |
| appname | string | Push path |
| domain | string | Push domain name |
| event_time | int | Event time |
| event_type | int | Event type |
| record_detail | string | file_format:1: FLV2: HLS3: MP44: AAC5: MP3record_bps:Bitratestart_model:Task initiation method1: Initiation via recording template rules5: Initiation via API callrecord_content: Recording content1: Original stream2: Watermarked stream3: Transcoding streamsource_type: Recording stream type1: Live recording2: Relay recordingcodec_temp_id: Transcoding template ID |
| record_event | string | record_start_succeeded : Successful recording startuprecord_start_failed: Failed recording startuprecord_paused : Recording pauserecord_resumed : Successful recording continuationrecord_error : Recording anomaliesrecord_ended : Ended recording |
| task_id | string | Recording task ID. This is only valid for recording tasks created by the API, that is, the task ID returned by [CreateRecordTask](https://www.tencentcloud.com/document/product/267/37309?lang=en&pg=). |
| seq | string | Message sequence number |
| session_id | string | Recording task ID |
| stream_id | string | Live stream name |

### Sample callback message

```
{            "appid":123456789,    "appname": "live",    "domain":"****.livepush.myqcloud.com",    "event_time":1700207929,    "event_type":332,    "record_detail":"{\\\\"file_format\\\\":2,\\\\"record_bps\\\\":0,\\\\"start_model\\\\":1,\\\\"record_content\\\\":1,\\\\"source_type\\\\":2,\\\\"codec_temp_id\\\\":0}",    "record_event":"record_ended",    "seq": "3266441426274648065",    "session_id":"2918085116267032069",    "stream_id":"2991615887188599295",    "sign": "ca3e25e5dc17a6f9909a9ae7281e300d",    "t": 1754623810}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/58590](https://www.tencentcloud.com/document/product/267/58590)*
