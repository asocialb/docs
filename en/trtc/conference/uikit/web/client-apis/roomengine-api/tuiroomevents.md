# TUIRoomEvents

## TUIRoomEvent API Introduction

TUIRoomEvent API is the Event Interface for Audio/Video call Component.

## Event list

| EVENT | Description |
| --- | --- |
| [TUIRoomEvents.onError](/document/product/647/54879#onError) | Error Event |
| [TUIRoomEvents.onKickedOutOfRoom](/document/product/647/54879#onKickedOutOfRoom) | Kicked out of room event |
| [TUIRoomEvents.onKickedOffLine](/document/product/647/54879#onKickedOffLine) | Current user Kicked off line event |
| [TUIRoomEvents.onUserSigExpired](/document/product/647/54879#onUserSigExpired) | UserSig Expiration Event |
| [TUIRoomEvents.onRoomDismissed](/document/product/647/54879#onRoomDismissed) | Host Destroy Room Event |
| [TUIRoomEvents.onRoomNameChanged](/document/product/647/54879#onRoomNameChanged) | Room Name Change Event |
| [TUIRoomEvents.onRoomSpeechModeChanged](/document/product/647/54879#onRoomSpeechModeChanged) | Room Speech Mode Change Event |
| [TUIRoomEvents.onAllUserCameraDisableChanged](/document/product/647/54879#onAllUserCameraDisableChanged) | All members Camera Usage Permission Change Event |
| [TUIRoomEvents.onAllUserMicrophoneDisableChanged](/document/product/647/54879#onAllUserMicrophoneDisableChanged) | All members Mic Usage Permission Change Event |
| [TUIRoomEvents.onSendMessageForAllUserDisableChanged](/document/product/647/54879#onSendMessageForAllUserDisableChanged) | All members Send Message Status Change Event |
| [TUIRoomEvents.onRoomMaxSeatCountChanged](/document/product/647/54879#onRoomMaxSeatCountChanged) | Room Maximum Seat Count Change Event |
| [TUIRoomEvents.onRemoteUserEnterRoom](/document/product/647/54879#onRemoteUserEnterRoom) | Remote User Entered Room Event |
| [TUIRoomEvents.onRemoteUserLeaveRoom](/document/product/647/54879#onRemoteUserLeaveRoom) | Remote User Leave Room Event |
| [TUIRoomEvents.onUserRoleChanged](/document/product/647/54879#onUserRoleChanged) | User Role Change Event |
| [TUIRoomEvents.onUserVideoStateChanged](/document/product/647/54879#onUserVideoStateChanged) | User Video Status Change Event |
| [TUIRoomEvents.onUserAudioStateChanged](/document/product/647/54879#onUserAudioStateChanged) | User Audio Status Change Event |
| [TUIRoomEvents.onSendMessageForUserDisableChanged](/document/product/647/54879#onSendMessageForUserDisableChanged) | User Send Message Status Event |
| [TUIRoomEvents.onUserVoiceVolumeChanged](/document/product/647/54879#onUserVoiceVolumeChanged) | User Volume Change Event |
| [TUIRoomEvents.onUserNetworkQualityChanged](/document/product/647/54879#onUserNetworkQualityChanged) | User Network Quality Change Event |
| [TUIRoomEvents.onSeatListChanged](/document/product/647/54879#onSeatListChanged) | Seat List Change Event |
| [TUIRoomEvents.onKickedOffSeat](/document/product/647/54879#onKickedOffSeat) | User Kicked off Seat Event |
| [TUIRoomEvents.onRequestReceived](/document/product/647/54879#onRequestReceived) | Request Received Event |
| [TUIRoomEvents.onRequestCancelled](/document/product/647/54879#onRequestCancelled) | Request Cancelled Event |
| [TUIRoomEvents.onReceiveTextMessage](/document/product/647/54879#onReceiveTextMessage) | Receive Text Message Event |
| [TUIRoomEvents.onReceiveCustomMessage](/document/product/647/54879#onReceiveCustomMessage) | Receive Custom Message Event |
| [TUIRoomEvents.onDeviceChange](/document/product/647/54879#onDeviceChange) | Device Change Event |
| [TUIRoomEvents.onUserScreenCaptureStopped](/document/product/647/54879#onUserScreenCaptureStopped) | Screen Sharing Stopped EventWhen the user uses the built-in browser stop sharing button to end screen sharing, the user will receive the 'onUserScreenCaptureStopped' event to modify the screen sharing status. |

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
| speechMode | [TUISpeechMode](/document/product/647/54876#TUISpeechMode) | Speech Mode |

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
| userInfo | [TUIUserInfo](/document/product/647/54876#6dd99cf1-05fd-4ef5-a4b9-d56f2b9f20ea) | User Information |

## onRemoteUserLeaveRoom

Remote User Leave Room Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRemoteUserLeaveRoom, ({ roomId, userInfo }) => {  console.log('roomEngine.onRemoteUserLeaveRoom', roomId, userInfo);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room ID |
| userInfo | [TUIUserInfo](/document/product/647/54876#6dd99cf1-05fd-4ef5-a4b9-d56f2b9f20ea) | User Information |

## onUserRoleChanged

User Role Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserRoleChanged, ({ userId, userRole }) => {  console.log('roomEngine.onUserRoleChanged', userId, userRole);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | string | User Id |
| userRole | [TUIRole](/document/product/647/54876#ca95b9a1-9ce7-4f90-9d05-caef5616592d) | User Changed Role |

## onUserVideoStateChanged

User Video Status Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserVideoStateChanged, ({ userId, streamType, hasVideo, reason }) => {  console.log('roomEngine.onUserVideoStateChanged', userId, streamType, hasVideo, reason);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | string | User Id |
| streamType | [TUIVideoStreamType](/document/product/647/54876#d129c5f7-80b8-4768-9394-e22b9af3f868) | User Stream Type |
| hasVideo | boolean | Has Video streams |
| reason | [TUIChangeReason](/document/product/647/54876#eec18716-f777-4fb6-998b-5f6a68634d62) | Change Reason, Self-operation/Host-operation |

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
| reason | [TUIChangeReason](/document/product/647/54876#eec18716-f777-4fb6-998b-5f6a68634d62) | Change Reason, Self-operation/Host-operation |

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
| userVolumeList | Array.<object> | Volume of all users in the room, including userId and volume information, volume range is 1-100 |

## onUserNetworkQualityChanged

User Network Quality Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserNetworkQualityChanged, ({ userNetworkList }) => {  userNetworkList.forEach(userNetwork => {    console.log('roomEngine.onUserNetworkQualityChanged', userNetwork.userId, userNetwork.volume);  })});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| networkMap | [TUINetworkQuality](/document/product/647/54876#TUIVideoQuality) | Traverse Network Quality Level |

## onSeatListChanged

Seat List Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onSeatListChanged, ({ seatList, seatedList, leftList }) => {  console.log('roomEngine.onSeatListChanged',seatList, seatedList, leftList);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatList | Array.<[TUISeatInfo](/document/product/647/54876#68f5131a-e77f-440b-a648-8d50d5470c6e)> | Seat List |
| seatedList | Array.<[TUISeatInfo](/document/product/647/54876#68f5131a-e77f-440b-a648-8d50d5470c6e)> | New Seat Information |
| leftList | Array.<[TUISeatInfo](/document/product/647/54876#68f5131a-e77f-440b-a648-8d50d5470c6e)> | Left Seat Information |

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
| request | [TUIRequest](/document/product/647/54876#45decc78-6a19-446a-b2ef-cd3c72064e2f) | Request Received |

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
| message | [TUIMessage](/document/product/647/54876#d05698a2-f725-4f2e-aec5-5bbd72fae55b) | Receive Text Message |

## onReceiveCustomMessage

Receive Custom Message Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onReceiveCustomMessage, ({ roomId, message }) => {  console.log('roomEngine.onReceiveCustomMessage', roomId, message);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | string | Room Id |
| message | [TUIMessage](/document/product/647/54876#d05698a2-f725-4f2e-aec5-5bbd72fae55b) | Receive Text Message |

## onDeviceChange

Device Change Event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onDeviceChange, ({ deviceId, type, state }) => {  console.log('roomEngine.onDeviceChange', deviceId, type, state);});
```

The parameters are shown in the table below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| deviceId | string | Device Id |
| type | [TRTCDeviceType](https://web.sdk.qcloud.com/trtc/webrtc/trtcCloud/doc/global.html#TRTCDeviceType) | Device Type |
| state | [TRTCDeviceState](https://web.sdk.qcloud.com/trtc/webrtc/trtcCloud/doc/global.html#TRTCDeviceState) | Device Change Status |

## onUserScreenCaptureStopped

Screen Sharing Stopped Event, when the user uses the built-in browser stop sharing button to end screen sharing, the user will receive the '`onUserScreenCaptureStopped`' event to modify the screen sharing status.

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserScreenCaptureStopped, () => {  console.log('roomEngine.onUserScreenCaptureStopped', deviceId, type, state);});
```


---
*Source: [https://trtc.io/document/54879](https://trtc.io/document/54879)*
