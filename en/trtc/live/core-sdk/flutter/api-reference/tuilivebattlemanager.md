# TUILiveBattleManager

Copyright (c) 2024 Tencent. All rights reserved.

Module:   TUILiveBattleManager @ TUIKitEngine

Live stream Battle relevant APIs

**TUILiveBattleManager**

## TUILiveBattleObserver

| Function List | Description |
| --- | --- |
| [onBattleStarted](https://www.tencentcloud.com/document/product/647/69266#7a0cc7db9328b7ed901d596edba5c6ec) | Notification received for the start of Battle |
| [onBattleEnded](https://www.tencentcloud.com/document/product/647/69266#2e3d364b388a92476d657e2d28ddcf8b) | Notification received for the end of Battle |
| [onUserJoinBattle](https://www.tencentcloud.com/document/product/647/69266#a7837241acd6fa7baf2b4fd14e437847) | Notification received for user joined Battle |
| [onUserExitBattle](https://www.tencentcloud.com/document/product/647/69266#8d6695e3a5bd6703073a5decc2ef0a86) | Notification received for user logout from Battle |
| [onBattleScoreChanged](https://www.tencentcloud.com/document/product/647/69266#b644272d9d1d0d3ce2726c6991ad2f97) | Notification received for user's Battle score update |
| [onBattleRequestReceived](https://www.tencentcloud.com/document/product/647/69266#bce652dfde53919487fd7b88e0ba002a) | Callee receives the Battle invitation notification |
| [onBattleRequestCancelled](https://www.tencentcloud.com/document/product/647/69266#69b7c2f7116d6eb875949bb948a10bc3) | Callee receives the Battle cancellation notification |
| [onBattleRequestTimeout](https://www.tencentcloud.com/document/product/647/69266#67668637eacf189329cbece2638a56e5) | Notification received for Battle processing timeout |
| [onBattleRequestAccept](https://www.tencentcloud.com/document/product/647/69266#c36eb33aea066c55ca692bff5b1baabe) | Caller receives callee's agreement notification |
| [onBattleRequestReject](https://www.tencentcloud.com/document/product/647/69266#097d2c0b5a506d72c28b8060e5b75762) | Caller receives callee's rejection notification |

## TUILiveBattleManager

| Function List | Description |
| --- | --- |
| [addObserver](https://www.tencentcloud.com/document/product/647/69266#bb2be01f092eca743c1bda28810cf314) | Add event callback |
| [removeObserver](https://www.tencentcloud.com/document/product/647/69266#5dcc0f73f5a5d0587fe1706b50025cc8) | Remove event callback |
| [requestBattle](https://www.tencentcloud.com/document/product/647/69266#cb5a6c657ac328bc81310dbbde6f11ba) | Initiate a Battle request |
| [cancelBattleRequest](https://www.tencentcloud.com/document/product/647/69266#7cce082bea8a3aa9478b69abc6a7cdd1) | Cancel a Battle request |
| [acceptBattle](https://www.tencentcloud.com/document/product/647/69266#2ade6de883b4c32df3b8125803c758e4) | Accept a Battle request |
| [rejectBattle](https://www.tencentcloud.com/document/product/647/69266#0476a8497fca375ae3e2540e2a810c73) | Deny a Battle request |
| [exitBattle](https://www.tencentcloud.com/document/product/647/69266#f86e8b8f25f9e4b7ed523588e149e315) | Logout of Battle |

## Structure Data Type

| Function List | Description |
| --- | --- |
| [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | Battle user information |
| [TUIBattleConfig](https://www.tencentcloud.com/document/product/647/69266#6ca8b8898efedde803c17d8513bbcae7) | Battle Configuration |
| [TUIBattleInfo](https://www.tencentcloud.com/document/product/647/69266#6b40e91c64a0a1ddbc355f14e0882d07) | Battle info |
| [TUIBattleRequestResult](https://www.tencentcloud.com/document/product/647/69266#490d4a56-5cea-4b36-918e-7fac96672c75) | Battle request result |

## Enumeration Types

| Enumeration Types | Description |
| --- | --- |
| [TUIBattleCode](https://www.tencentcloud.com/document/product/647/69266#7fb9c27105c7f9ca9ccb3d560ac3017d) | Battle invitation status |
| [TUIBattleStoppedReason](https://www.tencentcloud.com/document/product/647/69266#e162b34537d4a7e02e70c1a11d9c0e41) | The causes for the end of Battle |

## onBattleStarted

**Notification received for the start of Battle**

```
OnBattleStarted onBattleStarted = (TUIBattleInfo battleInfo) {};
```

| Parameter | Description |
| --- | --- |
| battleInfo | Battle info. |

## onBattleEnded

**Notification received for the end of Battle**

```
OnBattleEnded onBattleEnded = (TUIBattleInfo battleInfo, TUIBattleStoppedReason reason) {};
```

| Parameter | Description |
| --- | --- |
| battleInfo | Battle info. |
| reason | The causes for the end of Battle. |

## onUserJoinBattle

**Notification received for user joined Battle**

```
OnUserJoinBattle onUserJoinBattle = (String battleId, TUIBattleUser battleUser) {};
```

| Parameter | Description |
| --- | --- |
| battleId | Battle ID. |
| battleUser | Battle user information. |

## onUserExitBattle

**Notification received for user logout from Battle**

```
OnUserExitBattle onUserExitBattle = (String battleId, TUIBattleUser battleUser) {};
```

| Parameter | Description |
| --- | --- |
| battleId | Battle ID. |
| battleUser | Battle user information. |

## onBattleScoreChanged

**Notification received for user's Battle score update**

```
OnBattleScoreChanged onBattleScoreChanged = (String battleId, List<TUIBattleUser> battleUserList) {};
```

| Parameter | Description |
| --- | --- |
| battleId | Battle ID. |
| battleUserList | Battle user information. |

## onBattleRequestReceived

**Callee receives the Battle invitation notification**

```
OnBattleRequestReceived onBattleRequestReceived =     (TUIBattleInfo battleInfo,      TUIBattleUser inviter,      TUIBattleUser invitee) {};
```

| Parameter | Description |
| --- | --- |
| battleInfo | Battle info. |
| inviter | User information that initiates an invitation. |
| invitee | User information that receives an invitation. |

## onBattleRequestCancelled

**Callee receives the Battle cancellation notification**

```
OnBattleRequestCancelled onBattleRequestCancelled =     (TUIBattleInfo battleInfo,      TUIBattleUser inviter,      TUIBattleUser invitee) {};
```

| Parameter | Description |
| --- | --- |
| battleInfo | Battle info. |
| inviter | User information that initiates an invitation. |
| invitee | User information that receives an invitation. |

## onBattleRequestTimeout

**Notification received for Battle processing timeout**

```
OnBattleRequestTimeout onBattleRequestTimeout =     (TUIBattleInfo battleInfo,      TUIBattleUser inviter,      TUIBattleUser invitee) {};
```

| Parameter | Description |
| --- | --- |
| battleInfo | Battle info. |
| inviter | User information that initiates an invitation. |
| invitee | User information that receives an invitation. |

## onBattleRequestAccept

**Caller receives callee's agreement notification**

```
OnBattleRequestAccept onBattleRequestAccept =     (TUIBattleInfo battleInfo,      TUIBattleUser inviter,      TUIBattleUser invitee) {};
```

| Parameter | Description |
| --- | --- |
| battleInfo | Battle info. |
| inviter | User information that initiates an invitation. |
| invitee | User information that receives an invitation. |

## onBattleRequestReject

**Caller receives callee's rejection notification**

```
OnBattleRequestReject onBattleRequestAccept =     (TUIBattleInfo battleInfo,      TUIBattleUser inviter,      TUIBattleUser invitee) {};
```

| Parameter | Description |
| --- | --- |
| battleInfo | Battle info. |
| inviter | User information that initiates an invitation. |
| invitee | User information that receives an invitation. |

## addObserver

**Add event callback**

```
 void addObserver(TUILiveBattleObserver observer);
```

| Parameter | Description |
| --- | --- |
| observer | The instances being listened to. |

## removeObserver

**Remove event callback**

```
void removeObserver(TUILiveBattleObserver observer);
```

| Parameter | Description |
| --- | --- |
| observer | The instances being listened to. |

## requestBattle:userIdList

**Initiate a Battle request**

```
Future<TUIValueCallBack<TUIBattleRequestResult>> requestBattle    (TUIBattleConfig config,      List<String> userIdList,      int timeout);
```

| Parameter | Description |
| --- | --- |
| config | Battle Configuration Information. |
| userIdList | User ID List to be invited. |
| timeout | Timeout Time |

## cancelBattleRequest

**Cancel a Battle request**

```
Future<TUIActionCallback> cancelBattleRequest(String battleId, List<String> userIdList);
```

| Parameter | Description |
| --- | --- |
| battleId | Battle ID. |
| userIdList | User ID List to be cancelled. |

## acceptBattle

**Accept a Battle request**

```
Future<TUIActionCallback> acceptBattle(String battleId);
```

| Parameter | Description |
| --- | --- |
| battleId | Battle ID. |

## rejectBattle

**Deny a Battle request**

```
Future<TUIActionCallback> rejectBattle(String battleId);
```

| Parameter | Description |
| --- | --- |
| battleId | Battle ID. |

## exitBattle

**Logout of Battle**

```
Future<TUIActionCallback> exitBattle(String battleId);
```

| Parameter | Description |
| --- | --- |
| battleId | Battle ID. |

## TUIBattleUser

**Battle user information**

| Enumeration Types | Description |
| --- | --- |
| roomId | Battle room ID. |
| userId | Battle user ID. |
| userName | Battle user nickname. |
| avatarUrl | Battle user avatar address. |
| score | Battle score. |

## TUIBattleConfig

**<Battle Configuration>**

| Enumeration Types | Description |
| --- | --- |
| duration | Maximum duration of Battle (unit: seconds). |
| needResponse | Whether the invited user needs to reply with consent or refusal. |
| extensionInfo | Extended information of Battle. |

## TUIBattleInfo

**Battle info**

| Enumeration Types | Description |
| --- | --- |
| battleId | Battle ID. |
| config | Battle Configuration. |
| inviter | Battle initiator. |
| inviteeList | Invite Battle members. |
| startTime | Mark the start time stamp of Battle (unit: seconds). |
| endTime | Mark the end time stamp of Battle (unit: seconds). |

## TUIBattleRequestResult

| Enumeration Types | Description |
| --- | --- |
| battleInfo | Battle info. |
| requestMap | Battle request result |

## TUIBattleCode

**<Battle Invitation Status>**

| Error Example | Value | Description |
| --- | --- | --- |
| unknown | -1 | Default status. |
| success | 0 | Battle request sent successfully. |
| roomNotExists | 1 | The invited room does not exist. |
| battling | 2 | The invited room is already in the Battle. |
| battlingOtherRoom | 3 | The invited room is already in a Battle with another room. |
| roomExit | 4 | The room has exited. |
| retry | 5 | Internal error, recommend retry once. |

## TUIBattleStoppedReason

**The causes for the end of Battle**

| Error Example | Value | Description |
| --- | --- | --- |
| timeOver | 0 | Battle reaches the maximum duration and ends due to overtime. |
| otherExit | 1 | Other users in Battle have all logged out. |


---
*Source: [https://trtc.io/document/69266](https://trtc.io/document/69266)*
