# Webhook After Room Member Status Changed

## Feature Overview

The app backend can view users' online and offline status changes in the room in real time through this webhook.

## Notes

- To enable this webhook, you must configure the webhook URL and toggle on the corresponding protocol. For more information on the configuration method, see [Third-Party Webhook Configuration](https://www.tencentcloud.com/document/product/647/64412) documentation.
- During this webhook, the Live backend initiates an HTTP POST request to the app backend.
- After receiving the webhook request, the app backend must check whether the SDKAppID contained in the request URL is consistent with its own SDKAppID.
- This callback terminates immediately upon room dissolution.

## Scenarios that may trigger this Webhook

- Users call SDK interfaces to enter or leave a room.
- User room heartbeat timeout and heartbeat recovery.

## Webhook Trigger Time

After the room is created successfully.

## API description

### Sample request URL

In the following example, the webhook URL configured in the app is `https://www.example.com`.
**Example:**

```
https://www.example.com?SdkAppid=$SDKAppID&CallbackCommand=$CallbackCommand&contenttype=json&ClientIP=$ClientIP&OptPlatform=$OptPlatform
```

### Request parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS, and the request method is POST. |
| www.example.com | Webhook URL. |
| SdkAppid | SDKAppID assigned by the Instant Messaging console when an application is created. |
| CallbackCommand | Fixed as Live.CallbackMemberStateChanged. |
| contenttype | Fixed value: JSON. |

### Sample request packets

```
{    "CallbackCommand":"Live.CallbackAfterMemberStateChanged",    "RoomId":"room_id",    "EventType":"Online", // Online or Offline    "EventCause":"Enter", // Four types: Enter (enter room), Leave (leave room), HeartbeatInterrupt, HeartbeatRecover    "MemberList":[        {            "Member_Account": "jared"        },        {            "Member_Account": "tommy"        }    ],    "EventTime":1703589922780}
```

### Request packet fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Webhook command. |
| RoomId | String | Room ID. |
| EventType | String | Event type: divided into two types, user online and offline, Online, Offline. |
| EventCause | String | Event Cause, divided into the following four types: Enter (enter room), Leave (check-out), HeartbeatInterrupt, HeartbeatRecover. |
| MemberList | Array | Involved Member List. |
| EventTime | Integer | Event trigger timestamp in milliseconds. |

### Response packet example

A webhook response packet is sent after the app backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore webhook result}
```

### Response Packet Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Mandatory | The result of the request process: OK indicates success; FAIL indicates failure. |
| ErrorCode | Integer | Mandatory | Error Code, here 0 means to ignore the response result. |
| ErrorInfo | String | Mandatory | Error message. |

## Reference

- [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412)


---
*Source: [https://trtc.io/document/64424](https://trtc.io/document/64424)*
