# After a Room Is Entered

## Feature Overview

The App backend can view room member joining messages in real time through this callback, including: notifying the app backend of a member joining a group, allowing the app to perform necessary data synchronization.

## Notes

- To enable the callback, a callback URL must be configured and the switch corresponding to this callback protocol activated. For configuration methods, see [Third-party Callback Configuration](https://www.tencentcloud.com/document/product/1047/34520) document.
- The direction of the callback is from the Room backend to the App backend via an HTTP POST request.
- After receiving the callback request, the app backend must check whether the SDKAppID contained in the request URL is consistent with its own SDKAppID.

## Scenarios

- App users actively join a room through the client.

## Callback Trigger Time

After users successfully join a room.

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
| SdkAppid | The SDKAppID assigned by the Chat console when an application is created |
| CallbackCommand | Set as Room.CallbackAfterMemberEnter |
| contenttype | Fixed value: JSON |
| ClientIP | Client IP, format such as 127.0.0.1 |
| OptPlatform | Client platform. For the value, refer to the meaning of the OptPlatform parameter of [Webhook Overview: Callback Protocol](https://www.tencentcloud.com/document/product/1047/34354#.E5.9B.9E.E8.B0.83.E5.8D.8F.E8.AE.AE). |

### Sample Request Packets

```
{    "CallbackCommand":"Room.CallbackAfterMemberEnter",    "Operator_Account":"user1",    "RoomId":"rid-123",    "MemberCount":20,    "Type":"Enter", // Method of joining a room: Enter (join by oneself)    "MemberList_Account":["user1"],    "EventTime":1670574414123// Millisecond level, event trigger timestamp}
```

### Request Packet Field Description

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Callback command |
| Operator_Account | String | UserID of the requester |
| RoomId | String | Room ID |
| MemberCount | Integer | Room capacity |
| Type | String | Method of joining the room: Enter (join by self) |
| MemberList_Account | Array | List of room members |
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


---
*Source: [https://trtc.io/document/60735](https://trtc.io/document/60735)*
