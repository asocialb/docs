# After a Room Is Destroyed

## Feature Overview

The App backend can view the destroy dynamics of the room in real time through this callback, including: real-time recording of the room destroy (for example, recording logs or synchronization to other systems).

## Notes

- To enable the callback, a callback URL must be configured and the switch corresponding to this callback protocol activated. For configuration methods, see [Third-party Callback Configuration](https://www.tencentcloud.com/document/product/1047/34520) document.
- The direction of the callback is from the Room backend to the App backend via an HTTP POST request.
- After receiving the callback request, the App backend must check whether the SDKAppID contained in the request URL is consistent with its own SDKAppID.

## Scenarios

- App users successfully destroy the room through the client.
- App administrators successfully destroy the room through the RESTful API.

## Callback Trigger Time

After the room is successfully destroyed.

## API Description

### Sample Request URL

In the following example, the callback URL configured in the app is `https://www.example.com`.
**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json&ClientIP=$ClientIP&OptPlatform=$OptPlatform
```

### Request Parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST |
| www.example.com | Callback URL |
| SdkAppid | The SDKAppID assigned by the Chat console when an app is created |
| CallbackCommand | Fixed as Room.CallbackAfterDestroyRoom |
| contenttype | Fixed value: JSON |
| ClientIP | Client IP, format such as 127.0.0.1 |
| OptPlatform | Client platform. For the value, refer to the meaning of the OptPlatform parameter of [Webhook Overview: Callback Protocol](https://www.tencentcloud.com/document/product/1047/34354#.E5.9B.9E.E8.B0.83.E5.8D.8F.E8.AE.AE). |

### Sample Request Packets

```
{    "CallbackCommand":"Room.CallbackAfterDestroyRoom",    "Operator_Account":"admin",    "RoomId":"tandy-test-rest",    "EventTime":1703589922780}
```

### Request Packet Field Description

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Callback command |
| Operator_Account | String | UserID of the operator initiating the request to destroy a room |
| RoomId | String | Room ID |
| EventTime | Integer | Event trigger timestamp in milliseconds |

### Sample Response Packets

A callback response packet is sent after the app backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore callback result}
```

### Response Packet Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Mandatory | The result of the request process. OK for success, FAIL for failure. |
| ErrorCode | Integer | Mandatory | Error code, 0 means to ignore the response result |
| ErrorInfo | String | Mandatory | Error message |

## Reference

- [Webhook Overview](https://www.tencentcloud.com/document/product/647/60722#)
- RESTful API:[Destroy a Room](https://www.tencentcloud.com/document/product/647/60706#)


---
*Source: [https://trtc.io/document/60732](https://trtc.io/document/60732)*
