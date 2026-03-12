# Push Error Event Notifications

Push error callbacks notify you of the details of push errors. You need to configure a callback address in the CSS console, and CSS will send push error callbacks to the server you configured.
This document describes the fields in a callback notification sent by CSS after a push error occurs.

## Must-Knows

This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).

## Push Error Callback Parameters

### Event type

| Event Type | Parameter Value |
| --- | --- |
| Push errors | event_type = 321 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires.The default validity period of a callback notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a notification has elapsed, then this notification is considered invalid. This prevents network replay attacks.The value of `t` is a decimal Unix timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. **sign = MD5(key + t)**. Note: Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note:**You can set the callback key in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/9f60336dcb6711f0a4a55254001c06ec.png)

### Callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| appid | int | The user’s [APPID](https://console.tencentcloud.com/developer). |
| user_ip | string | User push IP. |
| data_time | int | Push event callback time (unit: ms). |
| domain | string | Push domain name. |
| path | string | Push path. |
| report_interval | int | Reporting interval (in ms) when an abnormal event occurs. |
| sequence | string | Message sequence number, identifying a streaming activity. |
| stream_id | string | The stream ID. |
| stream_param | string | Push URL parameters. |
| timeout | int | Callback request timeout (in ms). |
| abnormal_event | json | [Detailed Abnormal Event Group](https://www.tencentcloud.com/document/product/267/53310#.60abnormal_event.60-parameters). |

#### `abnormal_event` parameters

| Parameter | Type | Description |
| --- | --- | --- |
| count | int | The number of times the error occurred between two reports (within the reporting interval). |
| customer_visible | string | Whether the exception event is visible to the customer, fixed to "true". |
| detail | json | desc: The error description.occur_time: UNIX timestamp of the exception event. |
| event_key | string | Supplementary Chinese descriptions of abnormal events. |
| type | int | [Error types](#2d78c98a-ab47-4f29-b4f8-4511dedf2ffa). |
| type_desc_cn | string | The error description in Chinese. |
| type_desc_en | string | The error description in English. |

#### Error types

| Type | Description |
| --- | --- |
| 1 | The video timestamp moved backwards. |
| 2 | The audio timestamp moved backwards. |
| 3 | The video timestamp increased notably (by more than 1000 milliseconds). |
| 4 | The audio timestamp increased notably (by more than 1000 milliseconds). |
| 5 | Chunk size too big (bigger than 8,192). |
| 6 | Two consecutive video frames arrived late (by more than 3000 milliseconds). |
| 7 | Two consecutive audio frames arrived late (by more than 1000 milliseconds). |
| 8 | The video codec changed. |
| 9 | The audio codec changed. |
| 10 | No codec header before a video frame arrived. |
| 11 | No codec header before an audio frame arrived. |
| 12 | The interval between audio frame timestamps is too long. |
| 13 | Audio/Video codec formats are uncommon. |
| 14 | The video header cannot be parsed. |
| 15 | The video frame rate is too low. |
| 16 | The GOP size is too large. Currently, if it exceeds 10s, it is considered too large. |

> **Note:**Currently, you cannot configure callbacks for a specific type of push error. A push error callback includes the information of all push errors that occurred during the reporting interval. If no push errors occur, no callbacks will be sent.A push error callback only collects data for push errors in the current reporting cycle. The system will not handle the errors.

### Sample callback

```
{    "abnormal_event":[        {            "count":2,            "detail":[                {                    "desc":"video frame arrive interval too long, interval=3046(msec)",                    "occur_time":1670588070569                },                {                    "desc":"video frame arrive interval too long, interval=2953(msec)",                    "occur_time":1670588073522                }            ],            "event_key":"",            "type":6,            "type_desc_cn":" ",            "type_desc_en":"video frame arrive interval bigger than 1000(ms)"        },        {            "count":2,            "customer_visible":"true",            "detail":[                {                    "desc":"audio frame arrive interval too long, interval=3009(msec)",                    "occur_time":1670588070532                },                {                    "desc":"audio frame arrive interval too long, interval=2917(msec)",                    "occur_time":1670588073486                }            ],            "event_key":"",            "type":7,            "type_desc_cn":" ",            "type_desc_en":"audio frame arrive interval bigger than 1000(ms)"        }    ],    "appid":12345678,    "user_ip":"1.1.1.1"    "data_time":1670588074971,    "domain":"example.push.com",    "event_type":321,    "interface":"general_callback",    "path":"live",    "report_interval":5000,    "sequence":"000000000000000000",    "stream_id":"teststream",    "stream_param":"stream_param=test",    "timeout":5000,    "sign": "ca3e25e5dc17a6f9909a9ae7281e300d",    "t": 1754623810}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/53310](https://www.tencentcloud.com/document/product/267/53310)*
