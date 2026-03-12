# After Group Message Is Sent

## Feature Overview

This webhook event is used by the app backend to check users' messages in real time. The app backend can be notified when a  message is sent successfully and can synchronize the data as required.

## Limits

- To enable this webhook, you must configure a callback URL and enable the corresponding switch for this webhook. For more information on the configuration method, see [Webhook Configuration](https://www.tencentcloud.com/document/product/647/74157).
- During this webhook event, the Chat backend initiates an HTTP POST request to the app backend.
- After receiving the webhook request, the app backend must check whether the `SDKAppID` contained in the request URL is the `SDKAppID` of the app.
- For more security considerations, see the **Security Considerations** section in [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412#security-considerations).

## Webhook Triggering Scenarios

- An app user sends a room message on the client.
- The app admin sends a room message via RESTful APIs.

## Webhook Triggering Timing

The webhook is triggered after a room message is sent successfully.

## API Calling Description

### Sample request URL

In the following sample, the webhook URL configured in the app is `https://www.example.com`.

**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json&ClientIP=$ClientIP&OptPlatform=$OptPlatform
```

### Request parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST. |
| www.example.com | Webhook URL |
| SdkAppid | The `SDKAppID` assigned by the Chat console when the app is created |
| CallbackCommand | Fixed value: `Group.CallbackAfterSendMsg`. |
| contenttype | Fixed value:` json`. |
| ClientIP | Client IP, such as 127.0.0.1 |
| OptPlatform | Client platform. For valid values, see the description of `OptPlatform` in the **Callback Protocols** section of [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412#d8e83f91-15ef-46e9-b370-9ba6c93a6ada). |

### Sample requests

```
{    "CallbackCommand": "Group.CallbackAfterSendMsg", // Webhook command    "GroupId": "@TGS#2J4SZEAEL", // Room ID    "Type": "Live", // Room type    "From_Account": "jared", // Sender    "Operator_Account":"admin", // Request initiator    "Random": 123456, // Random number    "MsgId": "144115233406643804-1727580296-4026038328", // Unique identifier of the message on the client    "MsgSeq": 123, // Sequence number of the message    "MsgTime": 1490686222, // Time of the message    "MsgBody": [ // Message body. For more information, see the `TIMMessage` message object.        {            "MsgType": "TIMTextElem", // Text            "MsgContent":{                "Text": "red packet"            }        }    ],    "CloudCustomData": "your cloud custom data",    "EventTime":"1670574414123"// Event trigger timestamp in milliseconds		}
```

### Request fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Webhook command. |
| GroupId | String | ID of the room that generates room messages. |
| Type | String | Type of the room that generates room messages, Fixed to `Live`. |
| From_Account | String | `UserID` of the message sender. |
| Operator_Account | String | `UserID` of the request initiator, based on which the system can identify whether the request is initiated by the admin. |
| Random | Integer | A 32-bit random number in the request. |
| MsgId | String | Unique identifier of the message on the client. |
| MsgSeq | Integer | Message sequence number, which uniquely identifies a message.Room messages are sorted by `MsgSeq`. The larger the `MsgSeq` value, the lower a message ranks. |
| MsgTime | Integer | Message sending timestamp, corresponding to the backend server time. |
| MsgBody | Array | Message body. The content is related to the message request, as detailed in [Send Normal Message](https://www.tencentcloud.com/document/product/647/74353#f1db57c4-02dd-47ff-ae52-19e4e91d9c25) and [Send Custom Message](https://www.tencentcloud.com/document/product/647/74354#f1db57c4-02dd-47ff-ae52-19e4e91d9c25). |
| CloudCustomData | String | Custom message data. It is saved in the cloud and will be sent to the receiver. Such data can be pulled after the app is uninstalled and reinstalled. The content is related to the message request, as detailed in [Send Normal Message](https://www.tencentcloud.com/document/product/647/74353#f1db57c4-02dd-47ff-ae52-19e4e91d9c25). |
| EventTime | Integer | Event trigger timestamp in milliseconds. |

> **Note:**After speaking in the room, reuse the callback capability of IM group messages. In the callback, `MsgBody` and `CloudCustomData` are the results of packaging the message send request. For details, see [Send Normal Message](https://www.tencentcloud.com/document/product/647/74353#f1db57c4-02dd-47ff-ae52-19e4e91d9c25) and [Send Custom Message](https://www.tencentcloud.com/document/product/647/74354#f1db57c4-02dd-47ff-ae52-19e4e91d9c25).

### Sample response

A response is sent after the app backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 //The value `0` indicates that the webhook result is ignored.}
```

### Response fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Yes | Request result. `OK`: Successful; `FAIL`: Failed. |
| ErrorCode | Integer | Yes | Error code. The value `0` indicates that the webhook result is ignored. |
| ErrorInfo | String | Yes | Error information. |

## References

- [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412)


---
*Source: [https://trtc.io/document/74348](https://trtc.io/document/74348)*
