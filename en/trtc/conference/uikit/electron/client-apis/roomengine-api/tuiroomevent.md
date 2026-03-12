# TUIRoomEvent

## TUIRoomEvent API Introduction

TUIRoomEvent API is the Event Interface for Multiplayer Component.

## Event list

| EVENT | Description |
| --- | --- |
| [TUIRoomEvents.onError](https://www.tencentcloud.com/document/product/647/54884#onError) | Error Event |
| [TUIRoomEvents.onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/54884#onKickedOutOfRoom) | Kicked out of room event |
| [TUIRoomEvents.onKickedOffLine](https://www.tencentcloud.com/document/product/647/54884#onKickedOffLine) | Current user Kicked off line event |
| [TUIRoomEvents.onUserSigExpired](https://www.tencentcloud.com/document/product/647/54884#onUserSigExpired) | UserSig Expiration Event |
| [TUIRoomEvents.onRoomDismissed](https://www.tencentcloud.com/document/product/647/54884#onRoomDismissed) | Host Destroy Room Event |
| [TUIRoomEvents.onRoomNameChanged](https://www.tencentcloud.com/document/product/647/54884#onRoomNameChanged) | Room Name Change Event |
| [TUIRoomEvents.onRoomSpeechModeChanged](https://www.tencentcloud.com/document/product/647/54884#onRoomSpeechModeChanged) | Room Speech Mode Change Event |
| [TUIRoomEvents.onAllUserCameraDisableChanged](https://www.tencentcloud.com/document/product/647/54884#onAllUserCameraDisableChanged) | All members Camera Usage Permission Change Event |
| [TUIRoomEvents.onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/54884#onAllUserMicrophoneDisableChanged) | All members Mic Usage Permission Change Event |
| [TUIRoomEvents.onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54884#onSendMessageForAllUserDisableChanged) | All members Send Message Status Change Event |
| [TUIRoomEvents.onRoomMaxSeatCountChanged](https://www.tencentcloud.com/document/product/647/54884#onRoomMaxSeatCountChanged) | Room Maximum Seat Count Change Event |
| [TUIRoomEvents.onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54884#onRemoteUserEnterRoom) | Remote User Entered Room Event |
| [TUIRoomEvents.onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/54884#onRemoteUserLeaveRoom) | Remote User Leave Room Event |
| [TUIRoomEvents.onUserRoleChanged](https://www.tencentcloud.com/document/product/647/54884#onUserRoleChanged) | User Role Change Event |
| [TUIRoomEvents.onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54884#onUserVideoStateChanged) | User Video Status Change Event |
| [TUIRoomEvents.onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54884#onUserAudioStateChanged) | User Audio Status Change Event |
| [TUIRoomEvents.onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/54884#onSendMessageForUserDisableChanged) | User Send Message Status Event |
| [TUIRoomEvents.onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/54884#onUserVoiceVolumeChanged) | User Volume Change Event |
| [TUIRoomEvents.onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/54884#onUserNetworkQualityChanged) | User Network Quality Change Event |
| [TUIRoomEvents.onSeatListChanged](https://www.tencentcloud.com/document/product/647/54884#onSeatListChanged) | Seat List Change Event |
| [TUIRoomEvents.onKickedOffSeat](https://www.tencentcloud.com/document/product/647/54884#onKickedOffSeat) | User Kicked off Seat Event |
| [TUIRoomEvents.onRequestReceived](https://www.tencentcloud.com/document/product/647/54884#onRequestReceived) | Request Received Event |
| [TUIRoomEvents.onRequestCancelled](https://www.tencentcloud.com/document/product/647/54884#onRequestCancelled) | Request Cancelled Event |
| [TUIRoomEvents.onReceiveTextMessage](https://www.tencentcloud.com/document/product/647/54884#onReceiveTextMessage) | Receive Text Message Event |
| [TUIRoomEvents.onReceiveCustomMessage](https://www.tencentcloud.com/document/product/647/54884#onReceiveCustomMessage) | Receive Custom Message Event |
| [TUIRoomEvents.onDeviceChange](https://www.tencentcloud.com/document/product/647/54884#onDeviceChange) | Device Change Event |
| [TUIRoomEvents.onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/54884#onUserScreenCaptureStopped) | Screen Sharing Stopped Event When the user uses the built-in browser stop sharing button to end screen sharing, the user will receive the 'onUserScreenCaptureStopped' event to modify the screen sharing status. |

## onError

Error Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onError, (error) => { console.log('TUIRoomError error', error);})
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| code | number | Error Code |
| message | string | Error Information |

## onKickedOutOfRoom

Kicked out of room event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onKickedOutOfRoom, ({ roomId, message }) => {  console.log('roomEngine.onKickedOutOfRoom', roomId, message);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room ID |
| message | string | Kicked out of room information |

## onKickedOffLine

Current user Kicked off line event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onKickedOffLine, ({ message }) => {  console.log('roomEngine.onKickedOffLine', message);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room ID |
| message | string | User logged in on other end information |

## onUserSigExpired

UserSig Expiration Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserSigExpired, () => {  console.log('roomEngine.onUserSigExpired');});
```

## onRoomDismissed

Host Destroy Room Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRoomDismissed, ({ roomId }) => {  console.log('roomEngine.onRoomDismissed', roomId);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room ID |

## onRoomNameChanged

Room ID Modification Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRoomNameChanged, ({ roomId, roomName }) => {  console.log('roomEngine.onRoomNameChanged', roomId, roomName);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room ID |
| roomName | string | Room Name |

## onRoomSpeechModeChanged

Room Name Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRoomSpeechModeChanged, ({ roomId, speechMode }) => {  console.log('roomEngine.onRoomSpeechModeChanged', roomId, speechMode);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room ID |
| speechMode | [TUISpeechMode](https://www.tencentcloud.com/document/product/647/54886#TUISpeechMode) | Speech Mode |

## onAllUserCameraDisableChanged

All members Camera Usage Permission Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onAllUserCameraDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onAllUserCameraDisableChanged', isDisable);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| isDisable | boolean | Allow Camera Usage |

## onAllUserMicrophoneDisableChanged

All members Mic Usage Permission Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onAllUserMicrophoneDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onAllUserMicrophoneDisableChanged', isDisable);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| isDisable | boolean | Allow Mic Usage |

## onSendMessageForAllUserDisableChanged

All members Send Message Permission Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onSendMessageForAllUserDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onSendMessageForAllUserDisableChanged', isDisable);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| isDisable | boolean | Allow Sending Text Message |

## onRoomMaxSeatCountChanged

Room Maximum Seat Count Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRoomMaxSeatCountChanged, ({ maxSeatNumber }) => {  console.log('roomEngine.onRoomMaxSeatCountChanged', maxSeatNumber);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| maxSeatNumber | number | Maximum Seat Count |

## onRemoteUserEnterRoom

Remote User Entered Room Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRemoteUserEnterRoom, ({ roomId, userInfo }) => {  console.log('roomEngine.onRemoteUserEnterRoom', roomId, userInfo);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room ID |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/54886#TUIUserInfo) | User Information |

## onRemoteUserLeaveRoom

Remote User Leave Room Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRemoteUserLeaveRoom, ({ roomId, userInfo }) => {  console.log('roomEngine.onRemoteUserLeaveRoom', roomId, userInfo);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room ID |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/54886#TUIUserInfo) | User Information |

## onUserRoleChanged

User Role Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserRoleChanged, ({ userId, userRole }) => {  console.log('roomEngine.onUserRoleChanged', userId, userRole);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | string | User Id |
| userRole | [TUIRole](https://www.tencentcloud.com/document/product/647/54886#TUIRole) | User Changed Role |

## onUserVideoStateChanged

User Video Status Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserVideoStateChanged, ({ userId, streamType, hasVideo, reason }) => {  console.log('roomEngine.onUserVideoStateChanged', userId, streamType, hasVideo, reason);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | string | User Id |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/54886#TUIVideoStreamType) | User Stream Type |
| hasVideo | boolean | Has Video streams |
| reason | [TUIChangeReason](https://www.tencentcloud.com/document/product/647/54886#TUIChangeReason) | Change Reason, Self-operation/Host-operation |

## onUserAudioStateChanged

User Audio Status Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserAudioStateChanged, ({ userId, hasAudio, reason }) => {  console.log('roomEngine.onUserAudioStateChanged', userId, hasAudio, reason);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | string | User Id |
| hasVideo | boolean | Has Audio streams |
| reason | [TUIChangeReason](https://www.tencentcloud.com/document/product/647/54886#TUIChangeReason) | Change Reason, Self-operation/Host-operation |

## onSendMessageForUserDisableChanged

Member Camera Usage Permission Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onSendMessageForAllUserDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onSendMessageForAllUserDisableChanged', isDisable);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| isDisable | boolean | Allow Sending Text Message |

## onUserVoiceVolumeChanged

User Volume Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserVoiceVolumeChanged, ({ userVolumeList }) => {  userVolumeList.forEach(userVolume => {    console.log('roomEngine.onUserVoiceVolumeChanged', userVolume.userId, userVolume.volume);  })});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userVolumes | Array.<[TRTCVolumeInfo](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCVolumeInfo.html)> | Volume of all users in the room, including userId and volume information, volume range is 1-100 |

## onUserNetworkQualityChanged

User Network Quality Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserNetworkQualityChanged, ({ userNetworkList }) => {  userNetworkList.forEach(userNetwork => {    console.log('roomEngine.onUserNetworkQualityChanged', userNetwork.userId, userNetwork.volume);  })});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| networkMap | [TUINetworkQuality](https://www.tencentcloud.com/document/product/647/54886#TUINetworkQuality) | Traverse Network Quality Level |

## onSeatListChanged

Seat List Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onSeatListChanged, ({ seatList, seatedList, leftList }) => {  console.log('roomEngine.onSeatListChanged',seatList, seatedList, leftList);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatList | Array.<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/54886#TUISeatInfo)> | Seat List |
| seatedList | Array.<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/54886#TUISeatInfo)> | New Seat Information |
| leftList | Array.<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/54886#TUISeatInfo)> | Left Seat Information |

## onKickedOffSeat

Seat List Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onKickedOffSeat, ({ userId }) => {  console.log('roomEngine.onKickedOffSeat', userId);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | Kicked off Seat User Id |

## onRequestReceived

Error Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRequestReceived, ({ request }) => {  console.log('roomEngine.onRequestReceived', request);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| request | [TUIRequest](https://www.tencentcloud.com/document/product/647/54886#TUIRequest) | Request Received |

## onRequestCancelled

Request Cancelled Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRequestCancelled, ({ requestId, userId }) => {  console.log('roomEngine.onRequestCancelled', requestId, userId);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| requestId | string | Request Id |
| userId | string | User Id of Cancelled Request |

## onReceiveTextMessage

Receive Text Message Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onReceiveTextMessage, ({ roomId, message }) => {  console.log('roomEngine.onReceiveTextMessage', roomId, message);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room Id |
| message | [TUIMessage](https://www.tencentcloud.com/document/product/647/54886#TUIMessage) | Receive Text Message |

## onReceiveCustomMessage

Receive Custom Message Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onReceiveCustomMessage, ({ roomId, message }) => {  console.log('roomEngine.onReceiveCustomMessage', roomId, message);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room Id |
| message | [TUIMessage](https://www.tencentcloud.com/document/product/647/54886#TUIMessage) | Receive Text Message |

## onDeviceChange

Device Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onDeviceChange, ({ deviceId, type, state }) => {  console.log('roomEngine.onReceiveCustomMessage', deviceId, type, state);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| deviceId | string | Device Id |
| type | [TRTCDeviceType](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/global.html#TRTCDeviceType) | Device Type |
| state | [TRTCDeviceState](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/global.html#TRTCDeviceState) | Device Change Status |

## onUserScreenCaptureStopped

Screen Sharing Stopped Event, when the user uses the built-in browser stop sharing button to end screen sharing, the user will receive the '`onUserScreenCaptureStopped`' event to modify the screen sharing status.

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserScreenCaptureStopped, () => {  console.log('roomEngine.onReceiveCustomMessage', deviceId, type, state);});
```


---
*Source: [https://trtc.io/document/54884](https://trtc.io/document/54884)*
