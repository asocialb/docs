# Webhook After Ending Battle

## Feature Description

The app server can use this webhook to monitor battle ended.

## Must-Knows

- To enable webhook, configuration is required.
- URL, and turn on the switch corresponding to this webhook protocol. For detailed configuration methods, see [Third-Party Webhook Configuration](https://www.tencentcloud.com/document/product/647/64420#) Document.
- The direction of the webhook is that the live backend initiates an HTTP POST request to the app backend.
- After receiving the webhook request, the app server must verify whether the parameter SDKAppID in the request URL is its own SDKAppID.

## Scenarios That May Trigger This Webhook

- The battle ends normally when the time is up.
- During the battle, all room owners exit the battle.
- After the battle is created, it ends directly when all the called room owners do not agree to join the battle.

## Timing Of Webhook Occurrence

After the battle ends.

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
| www.example.com | webhook URL |
| SdkAppid | The SDKAppID assigned in the Chat console when creating an application |
| CallbackCommand | Fixed as `Live.CallbackAfterEndBattle` |
| contenttype | The fixed value is `json` |
| ClientIP | Client IP, format as: `127.0.0.1` |
| OptPlatform | Client platform. For the value, see [Introduction to Third-Party Webhook](https://www.tencentcloud.com/document/product/647/64412#) for the parameter meaning of OptPlatform |

### Request Packet Sample:

```
{    "CallbackCommand": "Live.CallbackAfterEndBattle",    "BattleId": "4siHsNsWN/T3aub9zKraqPfGQAimPhdFoe6VWhtz9lY=",    "Duration": 30000,    "CreateTime": 1739956115,    "StartTime": 1739956115,    "EndTime": 1739956145,    "OpType": 0, // 0 indicates normal completion when time is up; 1 indicates completion caused by all streamers exiting after the battle starts; 2 indicates that the battle was created but ended directly without starting because no streamers joined.    "FromRoomInfo": {  //Caller information        "RoomId": "pk-3",        "Score": 0,        "Owner_Account": 144115245353757792    },    "ToRoomList": [ // Called party information        {            "RoomId": "pk-5",            "Score": 0,            "Owner_Account": 144115245442327522        }    ],    "EventTime": 1739956146119}
```

### Description Of Request Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| CallbackCommand | String | Callback command |
| BattleId | String | Battle Id |
| Duration | Integer | Duration of the battle |
| CreateTime | Integer | Creation time of the battle |
| StartTime | Integer | Start time of the battle |
| EndTime | Integer | Termination time of the battle |
| OpType | Integer | 0 indicates normal completion when time is up;1 indicates completion caused by all room owners exiting after the battle starts;2 indicates that the battle was created but ended directly without starting because no room owners joined. |
| FromRoomInfo | String | Caller information of the battle |
| ToRoomList | Array | Callee information of the battle |
| RoomId | String | Room Id |
| Score | Integer | The room score in battle |
| Owner_Account | String | The room owner in battle |
| EventTime | Integer | Millisecond-level timestamp triggered by the event |

### Response Packet Example

After the app synchronizes data in the background, it sends a webhook response packet.

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0 // Ignore webhook result}
```

### Response Packet Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| ActionStatus | String | Required | The result of request processing. OK indicates successful processing, FAIL indicates failure |
| ErrorInfo | String | Required | Error message |
| ErrorCode | Integer | Required | Error code |

## Reference

- [Introduction to Third-Party Webhook](https://www.tencentcloud.com/document/product/647/64412#)


---
*Source: [https://trtc.io/document/68261](https://trtc.io/document/68261)*
