# TUIRoomEngineObserver

## TUIRoomEngine event callback

### onError

Triggered when an error event occurs, indicating that the SDK encounters an irrecoverable error, such as a failure of entering a room or a device startup failure.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnError onError = (TUIError errorCode, String message) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| errorCode | [TUIError](https://www.tencentcloud.com/document/product/647/67259#NetworkQuality) | Error Codes onLiveRoomInfoChanged |
| message | String | Error Message |

### onKickedOffLine

Triggered when the user is kicked offline.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnKickedOffLine onKickedOffLine = (String message) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| message | String | Description of removed from service |

### onUserSigExpired

`userSig` expiration event, triggered when the user's credential expires.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnUserSigExpired onUserSigExpired = () {}
```

### onRoomNameChanged

Triggered when the room name changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRoomNameChanged onRoomNameChanged = (String roomId, String roomName) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| roomName | String | Room Name |

### onAllUserMicrophoneDisableChanged

Triggered when the microphone disable status of all users changes.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnAllUserMicrophoneDisableChanged onAllUserMicrophoneDisableChanged = (String roomId, bool isDisable) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| isDisable | bool | Whether disabled or not |

### onAllUserCameraDisableChanged

Triggered when the camera disable status of all users changes.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnAllUserCameraDisableChanged onAllUserCameraDisableChanged = (String roomId, bool isDisable) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| isDisable | bool | Whether disabled or not |

### onSendMessageForAllUserDisableChanged

Triggered when the message sending permission of all users changes.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnSendMessageForAllUserDisableChanged onSendMessageForAllUserDisableChanged = (String roomId, bool isDisable) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| isDisable | bool | Whether disabled or not |

### onScreenShareForAllUserDisableChanged

Triggered when the screen sharing permissions of all users change.

> **Note:**This function is only applicable to conference room type ([conference](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnScreenShareForAllUserDisableChanged onScreenShareForAllUserDisableChanged =(String roomId, bool isDisable) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| isDisable | bool | Whether disabled or not |

### onRoomDismissed

Triggered when the room is dissolved.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRoomDismissed onRoomDismissed = (String roomId, TUIRoomDismissedReason reason) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| reason | TUIRoomDismissedReason | Dissolution reason |

### onKickedOutOfRoom

Triggered when the user is kicked out of the room by the host/administrator.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnKickedOutOfRoom onKickedOutOfRoom = (String roomId, String message) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| message | String | Description of removed from room |

### onRoomSeatModeChanged

Triggered when the microphone mode of the room changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRoomSeatModeChanged onRoomSeatModeChanged =(String roomId, TUISeatMode seatMode) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| seatMode | [TUISeatMode](https://www.tencentcloud.com/document/product/647/67259#TUISeatMode) | Microphone Mode |

### onRoomUserCountChanged

Triggered when the number of people in the room changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRoomUserCountChanged onRoomUserCountChanged =(String roomId, int userCount) {};
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| userCount | int | Room Occupancy |

### onRemoteUserEnterRoom

Triggered when a remote user enters the room.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRemoteUserEnterRoom onRemoteUserEnterRoom = (String roomId, TUIUserInfo userInfo) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | User Information |

### onRemoteUserLeaveRoom

Triggered when a remote user leaves the room.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRemoteUserLeaveRoom onRemoteUserLeaveRoom = (String roomId, TUIUserInfo userInfo) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | User Information |

### onUserInfoChanged

Triggered when user information in the room changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnUserInfoChanged onUserInfoChanged = (TUIUserInfo userInfo, List<TUIUserInfoModifyFlag> modifyFlagList) {};
```

| Parameters | Type | Description |
| --- | --- | --- |
| userInfo | TUIUserInfo | User Information |
|  |  |  |
| modifyFlagList | List<TUIUserInfoModifyFlag> | TUIUserInfo change flag list |

### onUserVideoStateChanged

Triggered when the user's video status changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnUserVideoStateChanged onUserVideoStateChanged = (String userId, TUIVideoStreamType streamType, bool hasVideo, TUIChangeReason reason) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/67259#VideoStreamType) | Video stream type |
| hasVideo | bool | Has video stream |
| reason | [TUIChangeReason](https://www.tencentcloud.com/document/product/647/67259#ChangeReason) | Reason for video stream change |

### onUserAudioStateChanged

Triggered when the user's audio status changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnUserAudioStateChanged onUserAudioStateChanged = (String userId, bool hasAudio, TUIChangeReason reason) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| hasAudio | bool | Is there an audio stream |
| reason | [TUIChangeReason](https://www.tencentcloud.com/document/product/647/67259#ChangeReason) | Reason for video stream change |

### onUserVoiceVolumeChanged

Triggered when the user's volume changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnUserVoiceVolumeChanged onUserVoiceVolumeChanged = (Map<String, int> volumeMap) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| volumeMap | Map | User volume mapkey: userIdvalue: Used to carry the volume levels of all speaking users. Range: 0 - 100 |

### onSendMessageForUserDisableChanged

Triggered when the user's message sending permissions change.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnSendMessageForUserDisableChanged onSendMessageForUserDisableChanged = (String roomId, String userId, bool isDisable) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| userId | String | User ID |
| isDisable | bool | Whether sending text messages is forbidden |

### onUserNetworkQualityChanged

Triggered when the user's network quality changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnUserNetworkQualityChanged onUserNetworkQualityChanged = (Map<String, TUINetwork> networkMap) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| networkMap | Map | User network status mapkeyï¼userIdvalue: Network condition |

### onUserScreenCaptureStopped

Triggered when the user's screen sharing stops.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnUserScreenCaptureStopped onUserScreenCaptureStopped = (int reason) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| reason | int | Stop reason0: User stopped voluntarily1: Stop due to screen window being closed2: Indicates screen sharing display state change (e.g., interface unplugged, projection mode change, etc.) |

### onRoomMaxSeatCountChanged

Maximum number of microphones in room changed event (only in meeting type rooms).

```
OnRoomMaxSeatCountChanged onRoomMaxSeatCountChanged = (String roomId, int maxSeatCount) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| maxSeatCount | int | Maximum number of microphone positions in the room |

### onSeatListChanged

Triggered when the microphone list changes.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnSeatListChanged onSeatListChanged = (List<TUISeatInfo> seatList, List<TUISeatInfo> seatedList, List<TUISeatInfo> leftList) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| seatList | List<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/67259#SeatInfo)> | The latest list of users currently on the microphone, including newly joined users |
| seatedList | List<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/67259#SeatInfo)> | List of newly joined users on the microphone |
| leftList | List<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/67259#SeatInfo)> | List of users who left the microphone |

### onKickedOffSeat

Triggered when the user is kicked off the microphone.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnKickedOffSeat onKickedOffSeat = (int seatIndex, TUIUserInfo operateUser) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| seatIndex | int | Microphone slot number |
| operateUser | TUIUserInfo | Operator's information |

### onRequestReceived

Triggered when a request from another user is received.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRequestReceived onRequestReceived = (TUIRequest request) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| request | [TUIRequest](https://www.tencentcloud.com/document/product/647/67259#Request) | Request content |

### onRequestCancelled

Triggered when another user cancels the request.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRequestCancelled onRequestCancelled = (TUIRequest request, TUIUserInfo operateUser) {}
```

| Parameters | Type | Description |
| --- | --- | --- |
| request | TUIRequest | Request Information |
| operateUser | TUIUserInfo | User information of the canceled signal |

### onRequestProcessed

Triggered when the request is handled by another **admin/host**.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

```
OnRequestProcessed onRequestProcessed = (TUIRequest request, TUIUserInfo operateUser) {};
```

| Parameters | Type | Description |
| --- | --- | --- |
| request | TUIRequest | Request Information |
| operateUser | TUIUserInfo | User information of the canceled signal |


---
*Source: [https://trtc.io/document/67262](https://trtc.io/document/67262)*
