# After a Group Message Extension Is Configured

## Feature Overview

This webhook allows your app backend to monitor user message extension operations in group chats in real-time.

## Notes

- To receive this webhook, you must configure the callback URL and turn on the corresponding switch. For detailed configuration steps, see [Webhook Overview](https://www.tencentcloud.com/document/product/1047/34354).
- The Chat backend sends HTTPS POST requests to your app backend. After receiving a webhook request, verify that the `SDKAppID` parameter matches your application's SDKAppID. For additional security considerations, see [Webhook Overview: Security Considerations](https://www.tencentcloud.com/document/product/1047/34354#security-considerations).

## Webhook Triggering Scenarios

This webhook is triggered when message extensions are set for group chats through either:

- **Client SDK:** Users configure message extensions via the client.
- **REST API:** Admins configure message extensions using the [Set Group Message Extension](https://www.tencentcloud.com/document/product/1047/52170).

## Webhook Triggering Timing

The webhook fires **after** a group message extension is successfully set.

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
| SDKAppID | The SDKAppID assigned in the chat console when creating an application. |
| CallbackCommand | Fixed as: `Group.CallbackAfterGroupMsgExtension`. |
| contenttype | Request body fixed as `JSON`. |
| ClientIP | Client IP address (e.g., `127.0.0.1`). |
| OptPlatform | Client platform. For the valid values, see the description of the OptPlatform parameter in [Webhook Protocol](https://www.tencentcloud.com/document/product/1047/34354#webhook-protocol). |

### Sample request

```
// Set Message Extension KV{  "CallbackCommand": "Group.CallbackAfterGroupMsgExtension",  "GroupId":"test",  "MsgSeq":10,  "OperateType":1,  "ExtensionList":[    {"Key":"key2","Value":"value2","Seq":56},  // Version number of a single KV    {"Key":"key3","Value":"12122","Seq":56}  ],  "Seq":56, // Represents the latest version number of the entire message  "EventTime":1764688294360}// Delete Message Extension KV{  "CallbackCommand": "Group.CallbackAfterGroupMsgExtension",  "GroupId":"test",  "MsgSeq":10,  "OperateType":2,  "ExtensionList":[    {"Key":"key2","Value":"","Seq":57},    {"Key":"key3","Value":"","Seq":57}  ],  "Seq":57, // Represents the latest version number of the entire message  "EventTime":1764688312045}// Clear Message Extension KV{  "CallbackCommand": "Group.CallbackAfterGroupMsgExtension",  "GroupId":"test",  "MsgSeq":10,  "OperateType":3,  "ExtensionList":[],  "Seq":58, // Represents the latest version number of the entire message  "EventTime":1764688329047}
```

### Request fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Callback command. |
| GroupId | String | Group ID. |
| MsgSeq | Integer | Group message Seq. |
| OperateType | Integer | 1: Set message extension key-value(KV) pairs.2: Delete message extension KV.3: Clear all message extension KV. |
| ExtensionList | Array | Array of message extension key-value pairs. |
| Seq | Integer | Version number. |
| EventTime | Integer | Event trigger timestamp, in milliseconds. |

### Sample response

```
{  "ActionStatus": "OK",  "ErrorInfo": "",  "ErrorCode": 0 // 0: callback successful; 1: callback error.}
```

### Response fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Required | Request processing result:OK: Successfully processed.FAIL: Processing failed. |
| ErrorCode | Integer | Required | Error Code:0: Callback processed successfully.1: Callback processing error. |
| ErrorInfo | String | Required | Error Message. |

## References

- [Webhook Overview](https://www.tencentcloud.com/document/product/1047/34354)
- REST API: [Set Group Message Extension](https://www.tencentcloud.com/document/product/1047/52170)


---
*Source: [https://trtc.io/document/76007](https://trtc.io/document/76007)*
