# Stream Pushing Notification

The stream pushing callback informs you whether stream pushing is successful or interrupted. You need to configure a server address for the callback in a callback template and bind the template with your push domain name. After push starts via a URL generated under the domain, the Tencent Cloud backend will send the callback to the server you set.

This document describes the parameters in a stream pushing callback notification sent to you by CSS.

## Note

This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).

## Stream Pushing Event Parameters

### Event type

| Event Type | Value |
| --- | --- |
| Successful push | event_type = 1 |
| Push interrupted | event_type = 0 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal Unix timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. sign = MD5(key + t). Note: Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note:**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/35a19253cb6711f0a93d52540044a08e.png)

### Callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| appid | int | User [APPID](https://console.tencentcloud.com/developer) |
| app | string | Push domain name |
| appname | string | Push path |
| stream_id | string | Live stream name |
| channel_id | string | Same as the live stream name |
| event_time | int64 | UNIX timestamp when the event message is generated |
| sequence | string | Message sequence number, which identifies a push. The notifications for a push, whether they are for successful push or stream interruption, have the same sequence number. |
| node | string | IP of the live stream access point |
| user_ip | string | User push IP |
| stream_param | string | User push URL parameters |
| push_duration | string | Push duration of the interrupted stream in milliseconds |
| errcode | int | Stream pushing error code |
| errmsg | string | Stream pushing error message |
| set_id | int | Whether the push is from inside the Chinese mainland. 1-6: yes; 7-200: no. |
| width | int | Video width. The value of this parameter may be `0` if the video header information is missing at the beginning of a push. |
| height | int | Video height. The value of this parameter may be `0` if the video header information is missing at the beginning of a push. |

### Causes of stream interruption

For a list of the causes of stream interruption, see [Stream Interruption Records](https://intl.cloud.tencent.com/document/product/267/31083).

### Sample callback

#### Live Stream Push Callback Message Example

```
{
    "app":"test.domain.com",
    "appid":12345678,
    "appname":"live",
    "channel_id":"test_stream",
    "errcode":0,
    "errmsg":"ok",
    "event_time":1703731478,
    "event_type":1,
    "height":0,
    "idc_id":34,
    "node":"42.81.194.37",
    "sequence":"2210464508206756938",
    "set_id":2,
    "sign":"df49************************f5d4",
    "stream_id":"test_stream",
    "stream_param":"stream_param=test",
    "t":1703732078,
    "user_ip":"1.1.1.1",
    "width":0
}
```

#### Live Stream Interruption Callback Message Example

```
{
    "app":"test.domain.com",
    "appid":12345678,
    "appname":"live",
    "channel_id":"test_stream",
    "errcode":1,
    "errmsg":"The push client actively stopped the push",
    "event_time":1703731606,
    "event_type":0,
    "height":0,
    "idc_id":34,
    "node":"42.81.194.37",
    "push_duration":"128581",
    "sequence":"2210464508206756938",
    "set_id":2,
    "sign":"3485************************56ae",
    "stream_id":"test_stream",
    "stream_param":"stream_param=test",
    "t":1703732206,
    "user_ip":"1.1.1.1",
    "width":0
}
```

### Stream Pushing Error Code

| Error Code |  | Description |
| --- | --- | --- |
| 1 |  | The push client actively stopped the push.Note: The different error codes are only distinguished internally by the system and users do not need to pay attention to them. |
| 2 |  |  |
| 3 |  |  |
| 4 |  |  |
| 35 |  |  |
| 5 |  | The live streaming system has an internal error. |
| 9 |  |  |
| 11 |  |  |
| 24 |  |  |
| 10 |  |  |
| 6 |  | Abnormal RTMP protocol content. |
| 7 |  | The size of a single RTMP frame exceeds the maximum value allowed by the configuration. |
| 8 |  | The system actively stopped the push with no data for a long time. |
| 20 |  |  |
| 12 |  | Abnormal stream pushing link network. |
| 13 |  |  |
| 14 |  |  |
| 15 |  |  |
| 16 |  |  |
| 17 |  |  |
| 19 |  | Third-party authentication failure. |
| 23 |  | Abnormal RTMP protocol content. |
| 33 |  | Abnormal RTMP AMF data. |
| 0 |  | Unknown reason. Please contact us by [submitting a ticket](https://console.tencentcloud.com/workorder/category). |
| 22 |  |  |
| 25 |  |  |
| 26 |  |  |
| 27 |  |  |
| 28 |  |  |
| 29 |  |  |
| 30 |  |  |
| 31 |  |  |
| 32 |  |  |
| 34 |  |  |
| Other unknown values |  |  |


---
*Source: [https://www.tencentcloud.com/document/product/267/38081](https://www.tencentcloud.com/document/product/267/38081)*
