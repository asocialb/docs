# Before Group Message Is Sent

## Feature Overview

This webhook event is used by the app backend to check users' room messages in real time, including:

- Records room messages in real time, for example, by recording a log or synchronizing the messages to other systems.
- Blocks users' requests to send messages in a room.

> **Note:**The timeout period of the webhook before message sending is two seconds by default, and we recommend you not adjust it. This webhook may time out when used for text moderation. If you need to moderate text, use the content webhook.

## Limits

- To enable this webhook, you must configure a webhook URL and enable the corresponding switch for this webhook. For more information on the configuration method, see [Webhook Configuration](https://www.tencentcloud.com/document/product/647/74157).
- During this webhook event, the Chat backend initiates an HTTP POST request to the app backend.
- After receiving the webhook request, the app backend must check whether the `SDKAppID` contained in the request URL is the `SDKAppID` of the app.
- For more security considerations, see the **Security Considerations** section in [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412#security-considerations).

## Webhook Triggering Scenarios

- An app user sends a room message on the client.
- The app admin sends a room message via RESTful APIs.

## Webhook Triggering Timing

The webhook is triggered before the Live backend sends a room message to room members.

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
| CallbackCommand | Fixed value: `Group.CallbackBeforeSendMsg`. |
| contenttype | Fixed value: `json`. |
| ClientIP | Client IP, such as 127.0.0.1 |
| OptPlatform | Client platform. For valid values, see the description of `OptPlatform` in the **Webhook Protocols** section of [Webhook Callback Overview](https://www.tencentcloud.com/document/product/647/64412#d8e83f91-15ef-46e9-b370-9ba6c93a6ada). |

### Sample requests

```
{    "CallbackCommand": "Group.CallbackBeforeSendMsg", // Webhook command    "GroupId": "@TGS#2J4SZEAEL", // Room ID    "Type": "Live", // Room type    "From_Account": "jared", // Sender    "Operator_Account":"admin", // Request initiator    "Random": 123456, // Random number    "MsgId": "144115233406643804-1727580296-4026038328", // Unique identifier of the message on the client    "MsgBody": [ // Message body. For more information, see the `TIMMessage` message object.        {            "MsgType": "TIMTextElem", // Text            "MsgContent":{                "Text": "red packet"            }        }    ],    "CloudCustomData": "your cloud custom data",    "EventTime":"1670574414123"// Event trigger timestamp in milliseconds		}
```

### Request fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Webhook command. |
| GroupId | String | ID of the room that generates room messages. |
| Type | String | Type of the room that generates room messages, Fixed`Live`. |
| From_Account | String | `UserID` of the message sender. |
| Operator_Account | String | `UserID` of the request initiator, based on which the system can identify whether the request is initiated by the admin. |
| Random | Integer | A 32-bit random number in the request. |
| MsgId | String | Unique identifier of the message on the client. |
| MsgBody | Array | Message body. The content is related to the message request, as detailed in [Send Normal Message](https://www.tencentcloud.com/document/product/647/74353#f1db57c4-02dd-47ff-ae52-19e4e91d9c25) and [Send Custom Message](https://www.tencentcloud.com/document/product/647/74354#f1db57c4-02dd-47ff-ae52-19e4e91d9c25). |
| CloudCustomData | String | Custom message data. It is saved in the cloud and will be sent to the receiver. Such data can be pulled after the app is uninstalled and reinstalled. The content is related to the message request, as detailed in [Send Normal Message](https://www.tencentcloud.com/document/product/647/74353#f1db57c4-02dd-47ff-ae52-19e4e91d9c25). |
| EventTime | Integer | Event trigger timestamp in milliseconds. |

> **Note:**Before speaking in the room, reuse the callback capability of IM group messages. In the callback, `MsgBody` and `CloudCustomData` are the results of packaging the message send request. For details, see [Send Normal Message](https://www.tencentcloud.com/document/product/647/74353#f1db57c4-02dd-47ff-ae52-19e4e91d9c25) and [Send Custom Message](https://www.tencentcloud.com/document/product/647/74354#f1db57c4-02dd-47ff-ae52-19e4e91d9c25).

### Sample response

#### Allowing room message sending

The user is allowed to send room messages, and the content of the message is not modified.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // `0` indicates the user is allowed to send messages.}
```

#### Forbidding room message sending

The user is not allowed to send room messages. In this case, the message is not sent, and the error code `10016` is returned to the caller.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 1 // `1` indicates that the user is not allowed to send messages.}
```

#### Discarding messages silently

The user is not allowed to send room messages. In this case, the message is not sent, but a success message will be returned to the caller.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 2 // The value `2` indicates the message is silently discarded.}
```

#### Modifying the message content

In the following response sample, the room message sent by the user is modified (a custom message is added), and the Chat backend will send the modified message. With this feature, the app backend can add special content, such as the user level and title, to the message sent by the user.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0, // This field must be set to `0` so that the modified message can be sent normally.    "MsgBody": [ // Message modified by the app backend. If the app backend does not modify the message, the message sent by the user is delivered.        {            "MsgType": "TIMTextElem", // Text            "MsgContent":{                "Text": "red packet"            }        },        {            "MsgType": "TIMCustomElem", // Custom message            "MsgContent":{                "Desc": "CustomElement.MemberLevel", // Description                "Data": "LV1" // Data            }        }    ],    "CloudCustomData": "your cloud custom data"}
```

### Response fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Yes | Request result. `OK`: Successful; `FAIL`: Failed. |
| ErrorCode | Integer | Yes | Error code returned. `0`: allows message sending; `1`: forbids  message sending; `2`: discards the message silently. If the business side wants to forbid a user to send  messages and send` ErrorCode` and `ErrorInfo` to the client, ensure that the value of `ErrorCode` is set within the range of [10100, 10200]. |
| ErrorInfo | String | Yes | Error information. |
| MsgBody | Array | No | Message body modified by the app backend. The Live backend sends the modified message to the room. For more information on the format, see [Message Formats](https://www.tencentcloud.com/document/product/647/74355). |
| CloudCustomData | String | No | Custom message data. It is saved in the cloud and will be sent to the peer end. Such data can be pulled after the app is uninstalled and reinstalled. |

## References

- [Webhook Callback Overview](https://www.tencentcloud.com/document/product/647/64412)


---
*Source: [https://trtc.io/document/74347](https://trtc.io/document/74347)*
