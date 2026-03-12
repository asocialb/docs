# TUICallEvent

## TUICallEvent APIs

TUICallEvent API is the **Event Interface** of the Audio and Video Call Components.

| Event | Description |
| --- | --- |
| [TUICallEvent.onError](https://www.tencentcloud.com/document/product/647/66841#error) | Error Callback during Call |
| [TUICallEvent.onCallReceived](https://www.tencentcloud.com/document/product/647/66841#6b3c4385-acfb-478f-ad96-fe5310133b08) | Callback for a Call Request |
| [TUICallEvent.onCallCancelled](https://www.tencentcloud.com/document/product/647/66841#06a7a696-ca1b-4b4e-ba01-ee9e2efeb732) | Callback for Call Cancellation |
| [TUICallEvent.onCallBegin](https://www.tencentcloud.com/document/product/647/66841#9918ea17-7900-4d01-9672-1f0e06f5e260) | Callback for Call Connection |
| [TUICallEvent.onCallEnd](https://www.tencentcloud.com/document/product/647/66841#0f575468-4d5e-4c27-9d6e-0ce85de0c77a) | Callback for Call Termination |
| [TUICallEvent.onUserReject](https://www.tencentcloud.com/document/product/647/66841#095f6da9-4668-4084-b44a-a2a59314d249) | xxxx User declines the call Callback |
| [TUICallEvent.onUserNoResponse](https://www.tencentcloud.com/document/product/647/66841#2586c3d6-3902-4948-b988-74789b5a4759) | xxxx User Non-response Callback |
| [TUICallEvent.onUserLineBusy](https://www.tencentcloud.com/document/product/647/66841#fa1c55d7-48a2-4cd3-a38c-9e81f082e68e) | xxxx User Busy Line Callback |
| [TUICallEvent.onUserJoin](https://www.tencentcloud.com/document/product/647/66841#7b551600-44c5-4683-90b7-25a3b243d12e) | xxxx User Joins Call Callback |
| [TUICallEvent.onUserLeave](https://www.tencentcloud.com/document/product/647/66841#fc8bb8d0-7665-4962-acc9-eea9bd1fe7db) | A user left the call. |
| [TUICallEvent.onCallMediaTypeChanged](https://www.tencentcloud.com/document/product/647/66841#31432c9e-4801-427f-b9de-64af29bb132d) | Callback for a change in the Call's Media Type |
| [TUICallEvent.onKickedOffline](https://www.tencentcloud.com/document/product/647/66841#f690f3cf-5ce7-4322-9310-f5b099e97b0c) | Current user kicked offline |
| [TUICallEvent.onUserSigExpired](https://www.tencentcloud.com/document/product/647/66841#b648078a-9d21-4b8e-bfe7-5d530d7af018) | Ticket expired while online |
| [TUICallEvent.onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/66841#b3e6f255-610d-405c-8b78-0619941be48d) | Whether a user has a video stream. |
| [TUICallEvent.onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/66841#3ca13720-a03e-4fb6-9fd0-de547be0ff4f) | Whether a user has an audio stream. |
| [TUICallEvent.onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/66841#e613c8b7-1114-4471-a8cd-54001c4ce2fb) | The volume levels of all users. |
| [TUICallEvent.onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/66841#dc08307d-9fe7-4b95-9ca8-431730d1f60d) | The network quality of all users. |

### TUICallEvent details

### onError

Error callback.

```
TUICallKit.on(TUICallEvent.onError, (res: any) => {  console.log('onError code=' + res.code + ',message=' + res.message);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| code | Number | Error Code |
| message | String | Error message |

### onCallReceived

Received a callback for a new incoming call request.

```
TUICallKit.on(TUICallEvent.onCallReceived, (res: any) => {  console.log('onCallReceived callerId=' + res.callerId);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| callerId | String | Caller ID (inviter) |
| calleeIdList | Array<String> | List of called IDs (invitees) |
| groupId | String | Group Call ID |
| callMediaType | Number | The media type of the call, such as video call, voice call.params.callMediaType = 0 : Voice Call.params.callMediaType = 1 : Video Call. |
| userData | String | User-added extension fields. |

### onCallCancelled

Indicates the call was canceled by the caller, missed by the callee, rejected, etc., covering multiple scenarios.

- Caller Cancellation: The caller receives this callback (callerId is oneself); the callee receives this callback (callerId is **the caller's ID**)
- Callee Timeout: The caller receives both onUserNoResponse and onCallCancelled callbacks (callerId is their own ID); the callee receives the onCallCancelled callback (callerId is their own ID)
- Call rejected: The caller will receive both onUserReject and onCallCancelled callbacks (callerId is your own ID); the callee receives the onCallCancelled callback (callerId is your own ID)
- Call busy: The caller will receive both onUserLineBusy and onCallCancelled callbacks (callerId is your own ID)
- Unexpected interruption: The callee fails to receive the call and gets this callback (callerId is your own ID)

```
TUICallKit.on(TUICallEvent.onCallCancelled, (res: any) => {  console.log('onCallCancelled userId=' + res.callerId);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| callerId | String | Caller ID (inviter) |

### onCallBegin

Indicates call connection. Both caller and called can receive it. You can start cloud recording, content review, etc., by listening to this event.

```
TUICallKit.on(TUICallEvent.onCallBegin, (res: any) => {  console.log('onCallBegin strRoomId=' + res.roomId.strRoomId + ', callMediaType=' + res.callMediaType + ',callRole=' + res.callRole);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | [RoomId](https://www.tencentcloud.com/document/product/647/66840#280a991e-d6a9-4194-9c98-ab703173227f) | roomId.intRoomId: The audio and video room ID for this call (int type)roomId.strRoomId: The audio and video room ID for this call (String type) |
| callMediaType | Number | Media Type of the call, Video Call, Voice Callparams.callMediaType = 0ï¼Voice Callparams.callMediaType = 1ï¼Video Call |
| callRole | Number | Role, Enum Type: Caller, Called.params.callRole = 0: Unknown Type.params.callRole = 1: Caller (inviter).params.callRole = 2: Called (invitee). |

### onCallEnd

Indicates call disconnection. Both the caller and the called can receive it. You can listen to this event to display call duration, call type, etc., or to stop the cloud recording process.

```
TUICallKit.on(TUICallEvent.onCallEnd, (res: any) => {  console.log('onCallEnd strRoomId=' + res.roomId.strRoomId   + ',callMediaType=' + res.callMediaType   + ',callRole=' + res.callRole  + ',totalTime=' + res.totalTime);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | [RoomId](https://www.tencentcloud.com/document/product/647/66840#280a991e-d6a9-4194-9c98-ab703173227f) | roomId.intRoomId: The audio and video room ID for this call (int type)roomId.strRoomId: The audio and video room ID for this call (String type) |
| callMediaType | Number | Media Type of the call, Video Call, Voice Callparams.callMediaType = 0: Voice Callparams.callMediaType = 1: Video Call |
| callRole | Number | role, Enumeration Type: Caller, Calledparams.callRole = 0: Unknown Type.params.callRole = 1: Caller (inviter).params.callRole = 2: Called (invitee). |
| totalTime | Number | The duration of this call, Unit: second |

### onUserReject

Callback for call rejection, in 1v1 calls, only the caller will receive the rejection callback; in group calls, all invitees can receive this callback.

```
TUICallKit.on(TUICallEvent.onUserReject, (res: any) => {  console.log('onUserReject userId=' + res.userId);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | ID of rejecting user |

### onUserNoResponse

Callback for no response from the other party.

```
TUICallKit.on(TUICallEvent.onUserNoResponse, (res: any) => {  console.log('onUserNoResponse userId=' + res.userId);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | User ID with no response |

### onUserLineBusy

Callback for call busy.

```
TUICallKit.on(TUICallEvent.onUserLineBusy, (res: any) => {  console.log('onUserLineBusy userId=' + res.userId);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | ID of rejecting user |

### onUserJoin

Callback for a user joining this call.

```
TUICallKit.on(TUICallEvent.onUserJoin, (res: any) => {  console.log('onUserJoin userId=' + res.userId);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | User ID joining the current call |

### onUserLeave

A user left the call.

```
TUICallKit.on(TUICallEvent.onUserLeave, (res: any) => {  console.log('onUserLeave userId=' + res.userId);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target userId |

### onCallMediaTypeChanged

Indicates a change in the call's media type.

```
TUICallKit.on(TUICallEvent.onCallMediaTypeChanged, (res: any) => {  console.log('onCallMediaTypeChanged oldCallMediaType=' + res.oldCallMediaType + ',newCallMediaType=' + res.newCallMediaType);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| oldCallMediaType | [MediaType](https://www.tencentcloud.com/document/product/647/66840#fb7a5c31-59f7-421a-a743-a08ac55305d8) | Previous call type |
| newCallMediaType | [MediaType](https://www.tencentcloud.com/document/product/647/66840#fb7a5c31-59f7-421a-a743-a08ac55305d8) | New call type |

### onKickedOffline

Current user kicked offline: You can notify the user on the UI and reinitialize.

```
TUICallKit.on(TUICallEvent.onKickedOffline, (res: any) => {  console.log('onKickedOffline');});
```

### onUserSigExpired

Ticket expires when online: You need to generate a new userSig and reinitialize.

```
TUICallKit.on(TUICallEvent.onUserSigExpired, (res: any) => {  console.log('onUserSigExpired');});
```

### onUserVideoAvailable

Whether a user is sending video.

```
TUICallKit.on(TUICallEvent.onUserVideoAvailable, (res: any) => {  console.log('onUserVideoAvailable userId=' + res.userId + 'isVideoAvailable=' + res.isVideoAvailable);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID. |
| isVideoAvailable | boolean | Whether the user has video. |

### onUserAudioAvailable

Whether a user is sending audio.

```
TUICallKit.on(TUICallEvent.onUserAudioAvailable, (res: any) => {  console.log('onUserAudioAvailable userId=' + res.userId + 'isAudioAvailable=' + res.isAudioAvailable);});
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID. |
| isAudioAvailable | boolean | Whether the user has audio. |

### onUserVoiceVolumeChanged

The volume levels of all users.

```
TUICallKit.on(TUICallEvent.onUserVoiceVolumeChanged, (res: any) => {  console.log('onUserVoiceVolumeChanged', res)});
```

| Parameter | Type | Description |
| --- | --- | --- |
| volumeMap | any | The volume table, which includes the volume of each user (userId). Value range: 0-100. |

### onUserNetworkQualityChanged

The network quality of all users.

```
TUICallKit.on(TUICallEvent.onUserNetworkQualityChanged, (networkQuality: any) => { for (const [key, value] of networkQuality) {    console.log(`onUserNetworkQualityChanged userId: ${key}, network quality: ${value}`);  }});
```

| Parameter | Type | Description |
| --- | --- | --- |
| networkQuality | any | The key represents the userId, and the value represents the network quality of the user.value = Unknownvalue = Excellentvalue = Goodvalue = Poorvalue = Badvalue = Vbadvalue = Down |


---
*Source: [https://trtc.io/document/66841](https://trtc.io/document/66841)*
