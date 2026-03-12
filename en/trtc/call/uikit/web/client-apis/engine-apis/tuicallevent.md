# TUICallEvent

## TUICallEvent API Introduction

TUICallEvent API is the **Event Interface** of the Audio and Video Call Components.

## Event List

| EVENT | Description |
| --- | --- |
| [TUICallEvent.ERROR](#error) | An error occurred during the call. |
| [TUICallEvent.KICKED_OUT](#kicked_out) | Receiving this event after a duplicate sign-in indicates that the user has been removed from the room |
| [TUICallEvent.USER_ACCEPT](#user_accept) | If a user answers, this event will be received.**v4.x.x is deprecated** |
| [TUICallEvent.USER_ENTER](#user_enter) | A user joined the call. |
| [TUICallEvent.USER_LEAVE](#user_leave) | A user left the call. |
| [TUICallEvent.REJECT](#reject) | A user declined the call. |
| [TUICallEvent.NO_RESP](#no_resp) | A user didn't respond. |
| [TUICallEvent.LINE_BUSY](#line_busy) | A user was busy. |
| [TUICallEvent.USER_VIDEO_AVAILABLE](#user_video_available) | Whether a user has a video stream. |
| [TUICallEvent.USER_AUDIO_AVAILABLE](#user_audio_available) | Whether a user has an audio stream. |
| [TUICallEvent.USER_VOICE_VOLUME](#user_voice_volume) | The volume levels of all users. |
| [TUICallEvent.ON_CALL_BEGIN](#on_call_begin) | Call connected event. |
| [TUICallEvent.ON_CALL_RECEIVED](#on_call_received) | Call request event. |
| [TUICallEvent.ON_CALL_NOT_CONNECTED](#on_call_canceled) | Call not connected event. |
| [TUICallEvent.ON_CALL_END](#calling_end) | The call ended. |
| [TUICallEvent.DEVICED_UPDATED](#deviced_updated) | Device list update, this event will be received. |
| [TUICallEvent.ON_USER_NETWORK_QUALITY_CHANGED](#on_user_network_quality_changed) | All user network quality events. |

### ERROR

Error event during the call. You can capture internal errors during the call by monitoring this event.

```
let onError = function(error) {  console.log(error.code, error.msg);};tuiCallEngine.on(TUICallEvent.ERROR, onError);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| code | Number | [Error Code](https://web.sdk.qcloud.com/component/trtccalling/doc/TUICallEngine/web/tutorial-ERROR_CODE.html) |
| msg | String | Error message |

### KICKED_OUT

The current user was kicked offlineï¼At this time, you can prompt the user with a UI message and then invoke `login`again.

```
let handleOnKickedOut = function(event) {  console.log(event);};tuiCallEngine.on(TUICallEvent.KICKED_OUT, handleOnKickedOut);
```

### USER_ACCEPT

> **Attentionï¼****v4.x.x is deprecated**

If a user answers, all other users will receive this event, where `userID` is the user who answered.

1. In a 1v1 call: when the callee answers, the caller will throw this event.
2. In group calls: if A calls B and C, and B answers, both A and C will throw this event, with the event's `userID` being B. Similarly, if C answers, both A and B will throw this event, with the event's `userID` being C.

```
let handleUserAccept = function(event) {  console.log(event.userID);};tuiCallEngine.on(TUICallEvent.USER_ACCEPT, handleUserAccept);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userID | String | Answering User ID |

### USER_ENTER

If a user enters the call, other users will throw this event, and userID is the user name who entered the call.

```
let handleUserEnter = function(event) {  console.log(event.userID);};tuiCallEngine.on(TUICallEvent.USER_ENTER, handleUserEnter);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userID | String | Entering User ID |

### USER_LEAVE

When a user leaves the call, this event will be thrown by other users in the call. The userID is the name of the user who left the call.

```
let handleUserLeave = function(event) {  console.log(event.userID);};tuiCallEngine.on(TUICallEvent.USER_LEAVE, handleUserLeave);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userID | String | Exiting User ID |

### REJECT

This event is thrown when the call is rejected

1. In a 1v1 call, only the calling party will receive the rejection event, and userID is the called username.
2. In a group call, when an invitee refuses the call, this event will be thrown by other people in the group call. The userID is the name of the user who refused the call.

```
let handleInviteeReject = function(event) {  console.log(event.userID);};tuiCallEngine.on(TUICallEvent.REJECT, handleInviteeReject);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userID | String | Rejecting User ID |

### NO_RESP

This event will be thrown by other calling users when the callee does not respond.

- In a 1v1 call, only the initiator will receive the event of no answer. For example, A invites B, B does not answer, A can receive this event.
- In a group call, when an invitee does not respond, this event will be thrown by everyone else in the group call. For example, if A invites B and C to join the call, but B does not respond, both A and C will throw this event.

```
let handleNoResponse = function(event) {console.log(event.sponsor, event.userIDList);};tuiCallEngine.on(TUICallEvent.NO_RESP, handleNoResponse);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| sponsor | String | Caller's User ID |
| userIDList | Array<String> | List of Users Who Triggered Timeout Due to No Response |

### LINE_BUSY

Call busy event. For example: when B is on a call, and A calls B, A will throw an event.

```
let handleLineBusy = function(event) {  console.log(event);};tuiCallEngine.on(TUICallEvent.LINE_BUSY, handleLineBusy);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userID | String | Busy User ID |

### USER_VIDEO_AVAILABLE

If a user turns on/off the camera during a video call, this event will be thrown by other users in the call. For example: A and B are on a video call, A turns on/off the camera, and B will throw this event.

```
let handleUserVideoChange = function(event) {  console.log(event.userID, event.isVideoAvailable);};tuiCallEngine.on(TUICallEvent.USER_VIDEO_AVAILABLE, handleUserVideoChange);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userID | String | Remote User ID |
| isVideoAvailable | Boolean | true: Remote User turns Camera On; false: Remote User turns Camera Off |

### USER_AUDIO_AVAILABLE

If a user turns on/off the microphone during an audio or video call, this event will be thrown by other users on the call. For example: A and B are having an audio and video call, and A turns on/off the microphone, and B will throw this event.

```
let handleUserAudioChange = function(event) {  console.log(event.userID, event.isAudioAvailable);};tuiCallEngine.on(TUICallEvent.USER_AUDIO_AVAILABLE, handleUserAudioChange);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userID | String | User ID to turn microphone on/off |
| isAudioAvailable | Boolean | true the user turns on the microphone; false the user turns off the microphone |

### USER_VOICE_VOLUME

When the user's volume changes during an audio or video call, this event will be thrown by other users on the call. For example: A and B are having an audio and video call, and if A's volume changes, B will throw this event.

```
let handleUserVoiceVolumeChange = function(event) {  console.log(event.volumeMap);};tuiCallEngine.on(TUICallEvent.USER_VOICE_VOLUME, handleUserVoiceVolumeChange);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| volumeMap | Array<Object> | Volume meter, the corresponding volume can be obtained according to each userid, volume range: [0, 100] |

### ON_CALL_RECEIVED

Receiving a new incoming call event, the called party will be notified. By listening to this event, you can decide whether to display the call answering interface.

```
let handleOnCallReceived = function(event) {    console.log(event);};tuiCallEngine.on(TUICallEvent.ON_CALL_RECEIVED, handleOnCallReceived);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| sponsor | String | Inviter |
| userIDList | Array<String> | Also Invited Persons |
| isFromGroup | Boolean | Is it a Group Call |
| inviteData | Object | Call Data |
| inviteID | String | Invitation ID, identifying one invitation |
| userData | String | Extended field: Utilized for amplifying details in the invitation signaling |
| callId | String | Unique ID for this call |
| roomID | Number | Audio-Video Room ID for this call |
| callMediaType | Number | Media Type of the call, Video Call, Voice Call |
| callRole | String | role, Enumeration Type: Caller, Called |

### ON_CALL_NOT_CONNECTED

**If the call is not established, this event will be thrown**.

```
let handleOnCallCanceled = function(event) {  console.log(event.userID);};tuiCallEngine.on(TUICallEvent.ON_CALL_NOT_CONNECTED, handleOnCallCanceled);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| userID | String | Cancelled User ID |
| callId | String | Unique ID for this call |
| roomID | Number | Audio-Video Room ID for this call |
| callMediaType | Number | Media Type of the call, Video Call, Voice Call |
| callRole | String | Role, Enumeration Type: Caller, Called |

### ON_CALL_BEGIN

Indicates call connection. Both caller and called can receive it. You can start cloud recording, content review, etc., by listening to this event.

```
let handleOnCallBegin = function(event) {    console.log(event);};tuiCallEngine.on(TUICallEvent.ON_CALL_BEGIN, handleOnCallBegin);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| callId | String | Unique ID for this call |
| roomID | Number | Audio-Video Room ID for this call |
| callMediaType | Number | Media Type of the call, Video Call, Voice Call |
| callRole | String | Role, Type: Caller, Called |

### ON_CALL_END

Indicates call termination. Both caller and called can trigger this event. You can display information such as call duration, call type, or stop the cloud recording process by listening to this event.

```
let handleCallingEnd = function(event) {  console.log(event.userID, event.);};tuiCallEngine.on(TUICallEvent.ON_CALL_END, handleCallingEnd);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomID | Number | Audio-Video Room ID for this call, currently only supports numeric room number, future versions will support character string room numbers |
| callMediaType | Number | Media Type of the call, Video Call, Voice Call |
| callRole | String | role, Enumeration Type: Caller ('inviter'), Called ('invitee'), Unknown ('') |
| totalTime | Number | The duration of this call in seconds |
| userID | String | UserID of the call termination. |
| callId | String | The unique ID for this call. |

### DEVICED_UPDATED

Device list update, this event will be received.

```
let handleDeviceUpdated = function({ microphoneList, cameraList, currentMicrophoneID, currentCameraID }) {  console.log(microphoneList, cameraList, currentMicrophoneID, currentCameraID)};tuiCallEngine.on(TUICallEvent.DEVICED_UPDATED, handleDeviceUpdated);
```

### ON_USER_NETWORK_QUALITY_CHANGED

All user network quality events

```
let handleOnUserNetworkQualityChange = function(event) {  console.log(event.networkQualityList);};tuiCallEngine.on(TUICallEvent.ON_USER_NETWORK_QUALITY_CHANGED, handleOnUserNetworkQualityChange);
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| networkQualityList | Array<Object> | Network status, according to userID, you can get the current network quality of the corresponding user (only local uplink and downlink). For example:  `networkQualityList: [{ userId: quality }]`ã **Network Quality Description:** quality = 0, Network state is unknown quality = 1, Network state is excellent quality = 2, Network state is good quality = 3, Network state is average quality = 4, Network state is poor quality = 5, Network state is very poor quality = 6, Network connection is disconnected |


---
*Source: [https://trtc.io/document/51017](https://trtc.io/document/51017)*
