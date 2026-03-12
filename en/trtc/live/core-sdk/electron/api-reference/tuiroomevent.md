# TUIRoomEvent

## TUIRoomEvent API

TUIRoom Engine **events interface**ã

## Room Events

| EVENT | Description |
| --- | --- |
| [TUIRoomEvents.onError](#onerror) | Error event |
| [TUIRoomEvents.onKickedOutOfRoom](#onkickedoutofroom) | Kicked out of room event |
| [TUIRoomEvents.onKickedOffLine](#onkickedoffline) | Current user is kicked offline |
| [TUIRoomEvents.onUserSigExpired](#onusersigexpired) | userSig expiration event |
| [TUIRoomEvents.onRoomDismissed](#onroomdismissed) | Room owner terminates the room event |
| [TUIRoomEvents.onRoomNameChanged](#onroomnamechanged) | Room name change event |
| [TUIRoomEvents.onRoomSeatModeChanged](#onroomseatmodechanged) | Seat mode change event |
| [TUIRoomEvents.onAllUserMicrophoneDisableChanged](#onallusermicrophonedisablechanged) | All members' microphone permissions change event |
| [TUIRoomEvents.onSendMessageForAllUserDisableChanged](#onsendmessageforalluserdisablechanged) | All members' message sending status change event |
| [TUIRoomEvents.onRoomMaxSeatCountChanged](#onroommaxseatcountchanged) | Room maximum seat count change event |
| [TUIRoomEvents.onRemoteUserEnterRoom](#onremoteuserenterroom) | Remote user enters room event |
| [TUIRoomEvents.onRemoteUserLeaveRoom](#onremoteuserleaveroom) | Remote user leaves room event |
| [TUIRoomEvents.onUserRoleChanged](#onuserrolechanged) | User role change event |
| [TUIRoomEvents.onUserVideoStateChanged](#onuservideostatechanged) | User video status change event |
| [TUIRoomEvents.onUserAudioStateChanged](#onuseraudiostatechanged) | User audio status change event |
| [TUIRoomEvents.onSendMessageForUserDisableChanged](#onsendmessageforuserdisablechanged) | User message sending status event |
| [TUIRoomEvents.onUserVoiceVolumeChanged](#onuservoicevolumechanged) | User volume change event |
| [TUIRoomEvents.onUserNetworkQualityChanged](#onusernetworkqualitychanged) | User network quality change event |
| [TUIRoomEvents.onSeatListChanged](#onseatlistchanged) | Seats list change event |
| [TUIRoomEvents.onKickedOffSeat](#onkickedoffseat) | User is kicked off the seat event |
| [TUIRoomEvents.onRequestReceived](#onrequestreceived) | Request received event |
| [TUIRoomEvents.onRequestProcessed](#onrequestprocessed) | Request processed event |
| [TUIRoomEvents.onRequestCancelled](#onrequestcancelled) | Request cancellation event |
| [TUIRoomEvents.onDeviceChange](#ondevicechange) | Device change event |
| [TUIRoomEvents.onUserScreenCaptureStopped](#onuserscreencapturestopped) | Screen sharing stopped event |
| [TUIRoomEvents.onScreenShareForAllUserDisableChanged](#onscreenshareforalluserdisablechanged) | Screen sharing disabled for all users in the room event |

## onError

Error event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onError, (error) => { console.log('TUIRoomError error', error);})
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| code | number | Error code |
| message | string | Error message |

## onKickedOutOfRoom

Kicked out of room event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onKickedOutOfRoom, ({ roomId, reason, message }) => {  console.log('roomEngine.onKickedOutOfRoom', roomId, message);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | string | Room ID |
| reason | [TUIKickedOutOfRoomReason](https://www.tencentcloud.com/document/product/647/64351#tuikickedoutofroomreason) | Reason to kick user out |
| message | string | Message |

## onKickedOffLine

Current user is kicked offline

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onKickedOffLine, ({ message }) => {  console.log('roomEngine.onKickedOffLine', message);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | string | Room ID |
| message | string | User enter room on other device |

## onUserSigExpired

userSig expiration event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserSigExpired, () => {  console.log('roomEngine.onUserSigExpired');});
```

## onRoomDismissed

Room owner terminates the room event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRoomDismissed, ({ roomId }) => {  console.log('roomEngine.onRoomDismissed', roomId);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | string | Room ID |

## onRoomNameChanged

Room name change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRoomNameChanged, ({ roomId, roomName }) => {  console.log('roomEngine.onRoomNameChanged', roomId, roomName);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | string | Room ID |
| roomName | string | Room name |

## onRoomSeatModeChanged

Seat mode change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRoomSeatModeChanged, ({ roomId, seatMode }) => {  console.log('roomEngine.onRoomSeatModeChanged', roomId, seatMode);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | string | Room ID |
| seatMode | [TUISeatMode](https://www.tencentcloud.com/document/product/647/64351#tuiseatmode) | Room microphone seat mode |

## onAllUserCameraDisableChanged

All members' camera permissions change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onAllUserCameraDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onAllUserCameraDisableChanged', isDisable);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| isDisable | boolean | Whether to allow user open camera |

## onAllUserMicrophoneDisableChanged

All members' microphone permissions change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onAllUserMicrophoneDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onAllUserMicrophoneDisableChanged', isDisable);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| isDisable | boolean | Whether to allow user open microphone |

## onSendMessageForAllUserDisableChanged

All members' message sending status change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onSendMessageForAllUserDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onSendMessageForAllUserDisableChanged', isDisable);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| isDisable | boolean | Whether to allow user sending message |

## onRoomMaxSeatCountChanged

Room maximum seats count change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRoomMaxSeatCountChanged, ({ maxSeatNumber }) => {  console.log('roomEngine.onRoomMaxSeatCountChanged', maxSeatNumber);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| maxSeatNumber | number | Maximum seats number |

## onRemoteUserEnterRoom

Remote user enters room event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRemoteUserEnterRoom, ({ roomId, userInfo }) => {  console.log('roomEngine.onRemoteUserEnterRoom', roomId, userInfo);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | string | Room ID |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/64351#tuiuserinfo) | Remote user information |

## onRemoteUserLeaveRoom

Remote user leaves room event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRemoteUserLeaveRoom, ({ roomId, userInfo }) => {  console.log('roomEngine.onRemoteUserLeaveRoom', roomId, userInfo);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | string | Room ID |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/64351#tuiuserinfo) | Remote user information |

## onUserRoleChanged

User role change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserRoleChanged, ({ userId, userRole }) => {  console.log('roomEngine.onUserRoleChanged', userId, userRole);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | string | User ID |
| userRole | [TUIRole](https://www.tencentcloud.com/document/product/647/64351#tuirole) | New user role value |

## onUserVideoStateChanged

User video status change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserVideoStateChanged, ({ userId, streamType, hasVideo, reason }) => {  console.log('roomEngine.onUserVideoStateChanged', userId, streamType, hasVideo, reason);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | string | User ID |
| streamType | [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/64351#tuivideostreamtype) | User video stream type |
| hasVideo | boolean | Whether the video stream exists or not |
| reason | [TUIChangeReason](https://www.tencentcloud.com/document/product/647/64351#tuichangereason) | Change reason, self-operation or room owner/administrator operation |

## onUserAudioStateChanged

User audio status change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserAudioStateChanged, ({ userId, hasAudio, reason }) => {  console.log('roomEngine.onUserAudioStateChanged', userId, hasAudio, reason);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | string | User ID |
| hasVideo | boolean | Whether the audio stream exists or not |
| reason | [TUIChangeReason](https://www.tencentcloud.com/document/product/647/64351#tuichangereason) | Change reason, self-operation or room owner/administrator operation |

## onSendMessageForUserDisableChanged

User message sending status event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onSendMessageForAllUserDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onSendMessageForAllUserDisableChanged', isDisable);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| isDisable | boolean | Whether to all user sending message |

## onUserVoiceVolumeChanged

User volume change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserVoiceVolumeChanged, ({ userVolumeList }) => {  userVolumeList.forEach(userVolume => {    console.log('roomEngine.onUserVoiceVolumeChanged', userVolume.userId, userVolume.volume);  })});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| userVolumes | Array<[TRTCVolumeInfo](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/TRTCVolumeInfo.html)> | The volume of all users in the room, including userId and volume information. The volume range is 1 to 100. |

## onUserNetworkQualityChanged

User network quality change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserNetworkQualityChanged, ({ userNetworkList }) => {  userNetworkList.forEach(userNetwork => {    console.log('roomEngine.onUserNetworkQualityChanged', userNetwork.userId, userNetwork.quality, userNetwork.upLoss, userNetwork.downLoss, userNetwork.delay);  })});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| networkMap | Array<[TUINetwork](https://www.tencentcloud.com/document/product/647/64351#tuinetwork)> | The network quality information of all users in the room |

## onSeatControlEnabled

Seat control mode change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onSeatControlEnabled, ({ enabled, maxSeatNumber }) => {  console.log('roomEngine.onSeatControlEnabled', enabled, maxSeatNumber);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| enabled | boolean | Whether to enabled |
| maxSeatNumber | number | Maximum seats number |

## onSeatListChanged

Seats list change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onSeatListChanged, ({ seatList, seatedList, leftList }) => {  console.log('roomEngine.onSeatListChanged',seatList, seatedList, leftList);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| seatList | Array<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/64351#tuiseatinfo)> | Seats list |
| seatedList | Array<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/64351#tuiseatinfo)> | Seats taken by users |
| leftList | Array<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/64351#tuiseatinfo)> | Seats released by users |

## onKickedOffSeat

User is kicked off the seat event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onKickedOffSeat, ({ userId }) => {  console.log('roomEngine.onKickedOffSeat', userId);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | User ID |

## onRequestReceived

Request received event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRequestReceived, ({ request }) => {  console.log('roomEngine.onRequestReceived', request);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| request | [TUIRequest](https://www.tencentcloud.com/document/product/647/64351#tuirequest) | Request information |

## onRequestProcessed

Request processed event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRequestProcessed, ({ request }) => {  console.log('roomEngine.onRequestProcessed', request);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| request | [TUIRequest](https://www.tencentcloud.com/document/product/647/64351#tuirequest) | Request information |

## onRequestCancelled

Request cancellation event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onRequestCancelled, ({ requestId, userId }) => {  console.log('roomEngine.onRequestCancelled', requestId, userId);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| requestId | string | Request ID |
| userId | string | User ID who cancelled the request |

## onDeviceChange

Device change event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onDeviceChange, ({ deviceId, type, state }) => {  console.log('roomEngine.onDeviceChange', deviceId, type, state);});
```

Parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| deviceId | string | Device ID |
| type | [TRTCDeviceType](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/global.html#TRTCDeviceType) | Device type |
| state | [TRTCDeviceState](https://web.sdk.qcloud.com/trtc/electron/doc/zh-cn/trtc_electron_sdk/global.html#TRTCDeviceState) | Device status |

## onUserScreenCaptureStopped

Screen sharing stopped event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onUserScreenCaptureStopped, () => {  console.log('roomEngine.onUserScreenCaptureStopped', deviceId, type, state);});
```

## onScreenShareForAllUserDisableChanged

Screen sharing disabled for all users in the room event

```
const roomEngine = new TUIRoomEngine();roomEngine.on(TUIRoomEvents.onScreenShareForAllUserDisableChanged, ({ isDisable }) => {  console.log('roomEngine.onScreenShareForAllUserDisableChanged', isDisable);});
```


---
*Source: [https://trtc.io/document/64350](https://trtc.io/document/64350)*
