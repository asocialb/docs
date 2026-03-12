# Callback After Reminding a Chatbot in a Group

## Feature Description

After the "chatbot event callback" is enabled in the console, the App backend will receive the callback of a reminder message when a user reminds a chatbot in a group.

## Must-Knows

- To enable this callback, you need to configure the callback URL and turn on the switch corresponding to this callback. For the configuration method, see [Webhook Configuration](https://www.tencentcloud.com/document/product/1047/34520).
- The direction of the callback is that the Chat backend sends HTTP POST requests to the App backend.
- After receiving a callback request, the App backend needs to verify whether the value of the SDKAppID parameter in the request URL is its own SDKAppID.
- For other security-related matters, see Security Considerations in [Webhook Overview](https://www.tencentcloud.com/document/product/1047/34354#security-considerations).

## Callback Triggering Scenarios

A user reminds a chatbot in a group. (The callback is not triggered if all group members are reminded.)

## Callback Triggering Timing

The callback is triggered after a user reminds a chatbot in a group.

## API Description

### Sample Request URL

In the following example, the callback URL configured for the App is `https://www.example.com`.

**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json&ClientIP=$ClientIP&OptPlatform=$OptPlatform
```

### Request Parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST. |
| www.example.com | Callback URL. |
| SdkAppid | SDKAppID assigned to an application when the application is created in the Chat console. |
| CallbackCommand | The value is fixed as Bot.OnGroupMessage. |
| contenttype | The value is fixed as json. |
| ClientIP | Client IP address. For example, 127.0.0.1. |
| OptPlatform | Client platform. For the valid values, see the description of the OptPlatform parameter in Webhook Protocol in [Webhook Overview](https://www.tencentcloud.com/document/product/1047/34354#webhook-protocol). |

### Sample Request Packet

```
{    "CallbackCommand": "Bot.OnGroupMessage", // Callback command.    "GroupId": "@TGS#2J4SZEAEL", // Group ID.    "Type": "Public", // Group type.    "From_Account": "jared", // Sender.    "Operator_Account":"admin", // Initiator of the request.    "Random": 123456, // Random number.    "MsgSeq": 123, // Message serial number.    "MsgTime": 1490686222, // Message sending timestamp.    "OnlineOnlyFlag": 1, // Online message. 1: yes; 0: no. For live streaming groups, this attribute is ignored, and the default value 0 is used.    "MsgBody": [ // Message body. See the message object TIMMessage.        {            "MsgType": "TIMTextElem", // Text.            "MsgContent": {                "Text": "@@RBT#001 hello"            }        }    ],    "AtRobots_Account": [ "@RBT#001" ], // List of reminded chatbots. Users can remind more than one chatbot if multiple chatbots exist in the group.    "CloudCustomData": "your cloud custom data",    "EventTime": 1670574414123// Event trigger timestamp, in milliseconds.        }
```

### Request Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Callback command. |
| GroupId | String | ID of the group with the group message. |
| Type | String | Type of the group with the group message. For example, Public. See Group Types in [Group System](https://www.tencentcloud.com/document/product/1047/33529#differences-in-basic-group-capabilities) for details. |
| From_Account | String | User ID of the message sender. |
| Operator_Account | String | User ID of the request initiator, which can be used to determine whether the request is initiated by the administrator. |
| Random | Integer | 32-bit random number in the message request. |
| MsgSeq | Integer | Message serial number, which uniquely identifies a message. Group messages are sorted by MsgSeq. A message is sent more recently if its MsgSeq value is larger. |
| MsgTime | Integer | Message sending timestamp, corresponding to the backend server time. |
| OnlineOnlyFlag | Integer | Online message. 1: yes; 0: no. For live streaming groups, this attribute is ignored, and the default value 0 is used. |
| MsgBody | Array | Message body. See [Message Formats](https://www.tencentcloud.com/document/product/1047/33527) for details. |
| AtRobots_Account | Array | List of reminded chatbots. Users can remind more than one chatbot if multiple chatbots exist in the group. |
| CloudCustomData | String | Custom message data. (It is saved on the cloud and will be sent to the recipient. It can still be obtained after Chat is uninstalled and then reinstalled.) |
| TopicId | String | Topic ID. If this parameter is used, messages are related to the topic. This parameter applies only to community groups that support topics. |
| EventTime | Integer | Event trigger timestamp, in milliseconds. |

### Sample Response Packet

The response packet is returned after the App backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore the callback result.}
```

### Response Packet Fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Required | Request processing result. OK: processing successful; FAIL: processing failed. |
| ErrorCode | Integer | Required | Error code. The value 0 indicates that the callback result is ignored. |
| ErrorInfo | String | Required | Error message. |

## References

- [Webhook Overview](https://www.tencentcloud.com/document/product/1047/34354)
- REST API: [Sending Ordinary Messages in a Group](https://www.tencentcloud.com/document/product/1047/34959)


---
*Source: [https://trtc.io/document/68953](https://trtc.io/document/68953)*
