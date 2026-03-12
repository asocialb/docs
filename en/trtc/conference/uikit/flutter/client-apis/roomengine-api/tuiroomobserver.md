# TUIRoomObserver

## TUIRoomEngine Event Callback

### onError

Error Event.

```
OnError onError = (TUIError errorCode, String message) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| errorCode | [TUIError](/document/product/647/57515#TUIError) | Error Code |
| message | String | Error Message |

### onKickedOffLine

Other terminals login and get kicked off event.

```
OnKickedOffLine onKickedOffLine = (String message) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| message | String | Kicked out description |

### onUserSigExpired

User credential timeout event.

```
OnUserSigExpired onUserSigExpired = () {}
```

### onRoomNameChanged

Room name change event.

```
OnRoomNameChanged onRoomNameChanged = (String roomId, String roomName) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| roomName | String | Room Name |

### onAllUserMicrophoneDisableChanged

Inside the room, all users' mic is disabled event.

```
OnAllUserMicrophoneDisableChanged onAllUserMicrophoneDisableChanged = (String roomId, bool isDisable) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| isDisable | bool | Whether it is disabled |

### onAllUserCameraDisableChanged

All users' Camera in the Room are disabled event.

```
OnAllUserCameraDisableChanged onAllUserCameraDisableChanged = (String roomId, bool isDisable) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| isDisable | bool | Whether it is disabled |

### onSendMessageForAllUserDisableChanged

Inside the room, all users' text message sending is disabled event.

```
OnSendMessageForAllUserDisableChanged onSendMessageForAllUserDisableChanged = (String roomId, bool isDisable) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| isDisable | bool | Whether it is disabled |

### onRoomDismissed

Room dissolution event.

```
OnRoomDismissed onRoomDismissed = (String roomId) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |

### onKickedOutOfRoom

Kick out of the room event

```
OnKickedOutOfRoom onKickedOutOfRoom = (String roomId, String message) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| message | String | Description of being kicked out |

### onRoomSpeechModeChanged

Mic control mode changes in the room.

```
OnRoomSpeechModeChanged onRoomSpeechModeChanged = (String roomId, TUISpeechMode speechMode) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| speechMode | [TUISpeechMode](/document/product/647/57515#SpeechMode) | Mic control mode |

### onRemoteUserEnterRoom

Remote user enters the room event.

```
OnRemoteUserEnterRoom onRemoteUserEnterRoom = (String roomId, TUIUserInfo userInfo) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| userInfo | [TUIUserInfo](/document/product/647/57515#UserInfo) | User information |

### onRemoteUserLeaveRoom

Remote user leaves the room event.

```
OnRemoteUserLeaveRoom onRemoteUserLeaveRoom = (String roomId, TUIUserInfo userInfo) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| userInfo | [TUIUserInfo](/document/product/647/57515#UserInfo) | User information |

### onUserRoleChanged

User role changes event.

```
OnUserRoleChanged onUserRoleChanged = (String userId, TUIRole role) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| role | [TUIRole](/document/product/647/57515#Role) | User Role |

### onUserVideoStateChanged

User Video status changes event.

```
OnUserVideoStateChanged onUserVideoStateChanged = (String userId, TUIVideoStreamType streamType, bool hasVideo, TUIChangeReason reason) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| streamType | [TUIVideoStreamType](/document/product/647/57515#VideoStreamType) | Streams type |
| hasVideo | bool | Whether there are streams |
| reason | [TUIChangeReason](/document/product/647/57515#ChangeReason) | Reason for streams change |

### onUserAudioStateChanged

User Audio status changes event.

```
OnUserAudioStateChanged onUserAudioStateChanged = (String userId, bool hasAudio, TUIChangeReason reason) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| hasAudio | bool | Whether there are Audio streams |
| reason | [TUIChangeReason](/document/product/647/57515#ChangeReason) | Reason for Audio streams change |

### onUserVoiceVolumeChanged

User volume change event.

```
OnUserVoiceVolumeChanged onUserVoiceVolumeChanged = (Map<String, int> volumeMap) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| volumeMap | Map | User Volume Mapkey: userIdvalue: Used for carrying the volume size of all speaking users, Value range 0 - 100 |

### onSendMessageForUserDisableChanged

User text message sending ability changes event.

```
OnSendMessageForUserDisableChanged onSendMessageForUserDisableChanged = (String roomId, String userId, bool isDisable) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| userId | String | User ID |
| isDisable | bool | Whether it is prohibited to send text messages. |

### onUserNetworkQualityChanged

User network status change event.

```
OnUserNetworkQualityChanged onUserNetworkQualityChanged = (Map<String, TUINetwork> networkMap) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| networkMap | Map | User Network Status Mapkey: userIdvalue: Network Condition |

### onUserScreenCaptureStopped

Screen Sharing stopped Callback event.

```
OnUserScreenCaptureStopped onUserScreenCaptureStopped = (int reason) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| reason | int | Stop reason:0: User actively stops1: Screen window closing causes the stop2: Screen Sharing display screen status change (such as interface being unplugged, Projection mode change, etc.) |

### onRoomMaxSeatCountChanged

Maximum number of mic slots changes event in the room (only effective in meeting type rooms).

```
OnRoomMaxSeatCountChanged onRoomMaxSeatCountChanged = (String roomId, int maxSeatCount) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| maxSeatCount | int | Maximum number of mic slots in the room |

### onSeatListChanged

Mic slot list changes event.

```
OnSeatListChanged onSeatListChanged = (List<TUISeatInfo> seatList, List<TUISeatInfo> seatedList, List<TUISeatInfo> leftList) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| seatList | List<[TUISeatInfo](/document/product/647/57515#SeatInfo)> | The latest user list on the mic, including newly on mic users |
| seatedList | List<[TUISeatInfo](/document/product/647/57515#SeatInfo)> | Newly on mic user list |
| leftList | List<[TUISeatInfo](/document/product/647/57515#SeatInfo)> | Newly off mic user list |

### onKickedOffSeat

Received the event of user being kicked off mic.

```
OnKickedOffSeat onKickedOffSeat = (String userId) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | Operate Kick-out of the (Host/Administrator) User ID |

### onRequestReceived

Received request message event.

```
OnRequestReceived onRequestReceived = (TUIRequest request) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| request | [TUIRequest](/document/product/647/57515#Request) | Request content |

### onRequestCancelled

Received request cancellation event.

```
OnRequestCancelled onRequestCancelled = (String requestId, String userId) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| requestId | String | Request ID |
| userId | String | Cancel signaling user ID |

### onReceiveTextMessage

Received ordinary text message event.

```
OnReceiveTextMessage onReceiveTextMessage = (String roomId, TUIMessage message) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| message | [TUIMessage](/document/product/647/57515#Message) | Message content |

### onReceiveCustomMessage

Received custom message event.

```
OnReceiveCustomMessage onReceiveCustomMessage = (String roomId, TUIMessage message) {}
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| message | [TUIMessage](/document/product/647/57515#Message) | Message content |


---
*Source: [https://trtc.io/document/57513](https://trtc.io/document/57513)*
