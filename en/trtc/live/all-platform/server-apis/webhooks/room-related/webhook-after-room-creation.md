# Webhook After Room Creation

## Feature Overview

The app backend can use this webhook to view real-time information about users creating rooms, including when the app backend receives a notification of successful room creation, allowing for data synchronization and other operations.

## Notes

- To enable the webhook, a webhook URL must be configured and the switch corresponding to this webhook protocol activated. For configuration methods, see [Third-party Webhook Configuration](https://www.tencentcloud.com/document/product/647/64420#) document.
- During this webhook, the Live backend initiates an HTTP POST request to the app backend.
- After receiving the webhook request, the app backend must check whether the SDKAppID contained in the request URL is consistent with its own SDKAppID.

## Scenarios that may trigger this webhook

- App users successfully create a room through the client
- App administrators successfully create a room via the REST API

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
| https | The request protocol is HTTPS, and the request method is POST |
| www.example.com | Webhook URL |
| SdkAppid | SDKAppID assigned by the Instant Messaging console when an application is created |
| CallbackCommand | Fixed as Live.CallbackAfterCreateRoom |
| contenttype | Fixed value: JSON |
| ClientIP | Client IP, such as 127.0.0.1 |
| OptPlatform | Client Platform, for value reference see [Webhook Overview: Webhook Protocol](https://www.tencentcloud.com/document/product/647/64412#d8e83f91-15ef-46e9-b370-9ba6c93a6ada) for the meaning of the OptPlatform parameter |

### Sample request packets

```
{    "CallbackCommand":"Live.CallbackAfterCreateRoom",    "Operator_Account":"admin",    "RoomInfo":{        "RoomId":"tandy-test-rest",        "RoomName":"tandy-test-rest",        "RoomType":"Live",        "Owner_Account":"user3",        "MaxMemberCount":300,        "IsMessageDisabled":true,        "CustomInfo":"custom123",        "IsSeatEnabled":true,        "TakeSeatMode":"ApplyToTake",        "MaxSeatCount":16,        "CreateTime":1703589922,        "IsPublicVisible":true,        "CoverURL":"cover url",        "Category":[1,2]    }}
```

### Request packet fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Webhook command |
| Operator_Account | String | Operator UserID initiating group creation request |
| RoomId | String | Room ID |
| RoomName | String | Room Name |
| RoomType | String | Room Type: Meeting (Meeting Room) |
| Owner_Account | String | Host ID |
| MaxMemberCount | Integer | Maximum number of room members |
| IsMessageDisabled | Bool | Prohibit all members from sending text messages |
| CustomInfo | String | Custom Definition Fields |
| IsSeatEnabled | Bool | Is microphone support available? |
| MaxSeatCount | Integer | Maximum Number of Microphones |
| TakeSeatMode | String | Seat Mode: None (Off), FreeToTake (Free to Join the Podium), ApplyToTake (Apply to join the microphone) |
| CreateTime | Integer | Scheduled meeting start time |
| IsPublicVisible | Bool | Room is public or not |
| CoverURL | String | Room cover URL |
| Category | Array | Room Type Identification, Integer array type |
| EventTime | Integer | Event trigger timestamp in milliseconds |

### Response packet example

A webhook response packet is sent after the app backend synchronizes the data.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore webhook result}
```

### Response Packet Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Mandatory | The result of the request process: OK indicates success; FAIL indicates failure |
| ErrorCode | Integer | Mandatory | Error Code, here 0 means to ignore the response result |
| ErrorInfo | String | Mandatory | Error message |

## Reference

- [Webhook Overview](https://www.tencentcloud.com/document/product/647/64412#)
- REST API:[Create Room](https://www.tencentcloud.com/document/product/647/63401#)


---
*Source: [https://trtc.io/document/64422](https://trtc.io/document/64422)*
