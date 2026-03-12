# Webhook After Room Metadata Deleted

## Feature Description

The app server can use this webhook to monitor the deletion of room metadata.

## Must-Knows

- To enable a webhook, you must configure the webhook URL and turn on the switch corresponding to this webhook protocol. For configuration methods, see [Third-Party Webhook Configuration](https://www.tencentcloud.com/document/product/647/64420#) document.
- The direction of the webhook is that the live server initiates an HTTP POST request to the app server.
- After receiving the webhook request, the app server must verify whether the parameter SDKAppID in the request URL is its own SDKAppID.

## Scenarios That May Trigger This Webhook

- App users delete metadata through the client.
- App admin deletes metadata via REST API.

## Timing Of Webhook Occurrence

After the room metadata data is deleted successfully.

## API Description

### Request URL Sample:

In the following example, the webhook URL configured for the App is `https://www.example.com`.

**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json&ClientIP=$ClientIP&OptPlatform=$OptPlatform
```

### Description Of Request Parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST |
| www.example.com | Webhook URL |
| SdkAppid | The SDKAppID assigned in the Chat console when creating an application |
| CallbackCommand | Fixed as `Live.CallbackAfterSetMetadata` |
| contenttype | The fixed value is `json` |
| ClientIP | Client IP, format as: `127.0.0.1` |
| OptPlatform | Client platform, see [Introduction to Third-Party Webhook](https://www.tencentcloud.com/document/product/647/64412#) for the meaning of OptPlatform parameter values |

### Request Packet Sample:

```
{    "CallbackCommand": "Live.CallbackAfterDelMetadata",    "Operator_Account": "brennanli",    "RoomId": "live-room1111",    "Keys": [        "key1", "key2"    ],    "EventTime": 1739966441121}
```

### Request Packet Field Description

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Webhook command |
| Operator_Account | String | Operator UserID who initiates the room destruction request |
| RoomId | String | Room ID |
| Keys | Array | The corresponding Key in the metadata data |
| EventTime | Integer | Millisecond-level timestamp triggered by the event |

### Response Packet Example

After the app synchronizes data in the background, it sends a webhook response packet.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore webhook result}
```

### Response Packet Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Required | The result of request processing. OK indicates success and FAIL indicates failure. |
| ErrorInfo | String | Required | Error message. |
| ErrorCode | Integer | Required | Error code. |

## Reference

- [Introduction to Third-Party Webhook](https://www.tencentcloud.com/document/product/647/64412#)
- [Delete Room Metadata](https://www.tencentcloud.com/document/product/647/64376#)


---
*Source: [https://trtc.io/document/68223](https://trtc.io/document/68223)*
