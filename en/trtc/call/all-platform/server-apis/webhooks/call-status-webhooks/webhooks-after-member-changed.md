# Webhooks after Member Changed

## Feature Description

The App backend can view call member status changes in real time through this callback.

## Must-Knows

- To enable the callback, you must configure the callback URL via the REST API and turn on the switch corresponding to this callback protocol. For the configuration method, see [Callback Configuration Settings](https://www.tencentcloud.com/document/product/647/68938#).
- The direction of the callback is that the Call backend initiates an HTTP POST request to the App backend.
- After receiving a callback request, the App backend needs to verify whether the value of the SDKAppID parameter in the request URL is its own SDKAppID.

## Callback Triggering Scenarios

Status changes of members caused by operations such as connect, hang up, etc. performed by App users through the client will trigger this callback.

## Callback Triggering Timing

After the call member status changes.

## API Description

### Sample Request URL

In the following example, the callback URL configured for the App is `https://www.example.com`.

**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json&ClientIP=$ClientIP&OptPlatform=$OptPlatform
```

### Request Parameters

| Parameters | Overview |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST. |
| www.example.com | Callback URL |
| SdkAppid | Assigned SDKAppID in the Chat console when creating an application |
| CallbackCommand | Fixed as `Call.CallbackAfterMemberChanged` |
| contenttype | The value is fixed as `json` |
| ClientIP | Client IP address, in the format of `127.0.0.1` |
| OptPlatform | Client platform. For the parameter values, see the description of the OptPlatform parameter in the [Third-Party Callback Overview: Callback Protocol](https://www.tencentcloud.com/zh/document/product/1047/34354#.E5.9B.9E.E8.B0.83.E5.8D.8F.E8.AE.AE) |

### Sample Request Packet

```
{    "CallbackCommand":"Call.CallbackAfterMemberChanged",    "CallId":"055662e1-bc8a-469c-a334-1126c8c17d58",    "UserList":[        {            "User_Account":"user1",            "Status":"Calling"        },        {            "User_Account":"user2",            "Status":"Calling"        }    ],    "ChangedUserList":[        {            "User_Account":"user2",            "ActionType":"Answer"  // Answer: Answer; Reject: Reject; NotAnswer: Unanswered; Hangup: Hang up; Join: Proactively Join; Offline: Offline (heartbeat expiry); Invite: Invite; Cancel_Invite: Cancel invitation;        }    ]    "EventTime":1740464128807}
```

### Request Packet Fields

| Field | Type | Overview |
| --- | --- | --- |
| CallbackCommand | String | Callback command |
| CallId | String | Call ID |
| UserList | Array | Call Member List |
| User_Account | String | Calling User ID |
| Status | String | Call status: `Calling` : on a call `Waiting` : waiting for connection |
| ChangedUserList | Array | Member list |
| ChangedUserList.User_Account | String | User ID of the member whose status has changed |
| ActionType | String | Change operation that causes changes`Accept`:  Answer`Reject`:  Deny`NotAnswer`:  Unanswered`Hang Up`:  Hang up`Join`:  Join in Call`Offline`:  Offline`Invited`:   Invite to join a call by caller`Canncel_Invite`:  Cancel Invite by caller |
| EventTime | Integer | Event-triggered timestamp in milliseconds |

### Sample Response Packet

The response packet is returned after the App backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore callback result}
```

### Response Packet Fields

| Field | Type | Required | Overview |
| --- | --- | --- | --- |
| ActionStatus | String | Required | Request processing result. OK: processing successful; FAIL: processing failed. |
| ErrorInfo | String | Required | Error message. |
| ErrorCode | Integer | Required | Error code. Enter 0 here to ignore the callback result. |

## References

- [Webhook Overview](https://www.tencentcloud.com/document/product/647/68933#)
- REST API: [Retrieve real-time call status](https://www.tencentcloud.com/document/product/647/68932#)


---
*Source: [https://trtc.io/document/69215](https://trtc.io/document/69215)*
