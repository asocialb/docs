# Smart Erasing Event Notification

This document primarily elucidates the callback notification fields transmitted by Tencent Cloud Streaming Services (CSS) to users upon triggering the smart erasing event.

## Note

You need to understand how to configure callbacks and how you will receive messages via Tencent Cloud CSS before reading this document. For more information, see [How to Receive Event Notifications](https://intl.cloud.tencent.com/document/product/267/38080).

## Event Message Notification Protocol

**Network Protocols**

- **Request**: Utilize an HTTP POST request with the body content in JSON format. The specific body content for each message type is detailed in the subsequent sections.
- **Response**: The HTTP status code is 200. While the server disregards the specific content of the response packet, for protocol compatibility, it is recommended that the client includes a JSON payload in the response: `{"code":0}`.

**Message Reliability**

The Event Notification Service incorporates a retry mechanism with a total of 3 attempts. To prevent potential impact on your server performance and network bandwidth due to retries, please ensure proper response packets are returned. The conditions triggering retries are as follows:

- No response packet received for an extended duration.
- The HTTP status code returned is not 200.

## Smart Erasing Event Parameters

### Event Type Parameter

| Event Type | Field Value Description |
| --- | --- |
| Smart erase | event_type = 347 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the UNIX timestamp when the event notification signature expires.The default validity period of a message notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a message notification has elapsed, then this notification is considered invalid, thereby preventing network replay attacks.The format of `t` is a decimal UNIX timestamp, i.e., the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Event notification security signature sign = MD5(key + t).Note: Tencent Cloud concatenates the encryption **key**and `t`, calculates the `sign` value through MD5, and places it in the notification message. When your backend server receives the notification message, it can confirm whether the `sign` is correct based on the same algorithm and then determine whether the message is indeed from the Tencent Cloud backend. |

> **Note：**You can set the callback key in **Event Center** > [**Live Stream Callback**](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.Callback message parameters.![](https://staticintl.cloudcachetci.com/cms/backend-cms/800c12f0cb6711f0a4a55254001c06ec.png)

### Callback message parameters

| Parameter | Type | Description |
| --- | --- | --- |
| appid | int | User [APPID](https://console.tencentcloud.com/developer). |
| stream_id | string | Live stream name. |
| channel_id | string | Same as the live stream name. |
| task_id | string | Task ID for Smart Erasing. |
| data | [Struct of data](#256eda27-74c0-4c1a-ad2c-79b78212b426) | Process the results. |

#### **data**

| Parameter | Type | Description |
| --- | --- | --- |
| subtitle_tmp_res | [Array of subtitle_tmp_res](#7a55029a-406c-48a4-b967-09ece9df22ad) |  Text results. |

#### **subtitle_tmp_res**

| Parameter | Type | Description |
| --- | --- | --- |
| src_txt | string | Original audio recognition text. |
| start_pts | int64 | src_txt corresponds to the timestamp starting point of the audio stream, in milliseconds (ms). |
| end_pts | int64 | src_txt corresponds to the timestamp end point of the audio stream, in milliseconds (ms). |
| start_unix_time | int64 | src_txt corresponds to the UNIX time starting point of the live broadcast. |
| end_unix_time | int64 | src_txt corresponds to the UNIX time end point of the live broadcast. |
| keywords_info | [Array of keywords_info](#c52f8023-60ce-4059-9e68-8fcbc275d7a0) | List of keywords that silence hits. |

#### **keywords_info**

| Parameter | Type | Description |
| --- | --- | --- |
| word | string | Hit keywords. |
| begin_time | int64 | The keyword corresponds to the timestamp starting point of the audio stream, in milliseconds (ms). |
| end_time | int64 | The keyword corresponds to the end point of the audio stream timestamp in milliseconds (ms). |

### Sample callback

```
{  "event_type": 347,  "stream_id": "teststream",  "channel_id": "teststream",  "task_id": "7735333",  "data": {    "subtitle_tmp_res": [      {				"end_pts": 964464,				"end_unix_time": 1750402597,				"keywords_info": [					{						"begin_time": 957759,						"end_time": 959424,						"word": "Central Commission for Discipline Inspection"					}				],				"src_txt": "The list of alternate members for the Central Committee and candidates for the Central Commission for Discipline Inspection was carefully deliberated.",				"start_pts": 954864,				"start_unix_time": 1750402588,		      }    ]  },  "sign": "ca3e25e5dc17a6f9909a9ae7281e300d",  "t": 1754623810}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/73169](https://www.tencentcloud.com/document/product/267/73169)*
