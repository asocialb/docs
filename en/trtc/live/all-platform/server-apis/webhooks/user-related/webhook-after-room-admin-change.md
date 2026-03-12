# Webhook After Room Admin Change

## Feature Description

The App backend can view room administrator modification information through this callback.

## Note

- To enable this callback, you need to configure the callback URL and turn on the switch corresponding to this callback. For the configuration method, see [Webhook Configuration](https://www.tencentcloud.com/document/product/647/64418).
- The callback direction is from the Live backend to the App backend via an HTTP POST request.
- After receiving a callback request, the App backend needs to verify whether the value of the SDKAppID parameter in the request URL is its own SDKAppID.

## Callback Triggering Scenarios

- App user modified admin through the client successfully.
- App admin modified administrator via REST API successfully.

## Callback Triggering Timing

Room modification by admin after success.

## API Description

### Sample Request URL

In the following example, the callback URL configured for the App is `https://www.example.com`.

**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json
```

### Request Parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST. |
| www.example.com | Callback URL |
| SdkAppid | The SDKAppID assigned in the Chat console when creating an application |
| CallbackCommand | Fixed as Live.CallbackAfterModifyAdmin |
| contenttype | The value is fixed as JSON. |

### Sample Request Packet

```
{    "CallbackCommand":"Live.CallbackAfterModifyAdmin",    "RoomId":"room_id",    "EventTime":1703589922780,    "Operator_Account":"admin",    "Admin_Account": ["user1", "user2"],    "opType": "add"}
```

### Request Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Callback command |
| RoomId | String | room ID |
| Admin_Account | Array | Modified Administrator List |
| opType | String | Operation type, add means add administrator, delete means delete management |
| Operator_Account | String | Operator |
| EventTime | Interger | Event trigger timestamp, in milliseconds. |

### Sample Response Packet

The response packet is returned after the App backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore the callback result}
```

### Response Packet Fields

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Required | Request processing result. OK: processing successful; FAIL: processing failed. |
| ErrorCode | Integer | Required | Error code. Fill in 0 here to ignore the callback result. |
| ErrorInfo | String | Required | Error Message |

## References

- [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412)


---
*Source: [https://trtc.io/document/72554](https://trtc.io/document/72554)*
