# TUICallObserver

## TUICallObserver APIs

`TUICallObserver` is the callback class of `TUICallEngine`. You can use it to listen for events.

## Overview

| API | Description |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/51007#onError) | A call occurred during the call. |
| [onCallReceived](https://www.tencentcloud.com/document/product/647/51007#onCallReceived) | A call invitation was received. |
| [onCallBegin](https://www.tencentcloud.com/document/product/647/51007#onCallBegin) | The call was connected. |
| [onCallEnd](https://www.tencentcloud.com/document/product/647/51007#onCallEnd) | The call ended. |
| [onCallNotConnected](https://www.tencentcloud.com/document/product/647/51007#onCallNotConnected) | The call not connected. |
| [onUserReject](https://www.tencentcloud.com/document/product/647/51007#onUserReject) | A user declined the call. |
| [onUserNoResponse](https://www.tencentcloud.com/document/product/647/51007#onUserNoResponse) | A user didn't respond. |
| [onUserLineBusy](https://www.tencentcloud.com/document/product/647/51007#onUserLineBusy) | A user was busy. |
| [onUserInviting](https://www.tencentcloud.com/document/product/647/51007#onUserInviting) | A user is invited to join a call. |
| [onUserJoin](https://www.tencentcloud.com/document/product/647/51007#onUserJoin) | A user joined the call. |
| [onUserLeave](https://www.tencentcloud.com/document/product/647/51007#onUserLeave) | A user left the call. |
| [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/51007#onUserVideoAvailable) | Whether a user had a video stream. |
| [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/51007#onUserAudioAvailable) | Whether a user had an audio stream. |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/51007#onUserVoiceVolumeChanged) | The volume levels of all users. |
| [onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/51007#onUserNetworkQualityChanged) | The network quality of all users. |
| [onKickedOffline](https://www.tencentcloud.com/document/product/647/51007#onKickedOffline) | The current user was kicked offline. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/51007#onUserSigExpired) | The user Sig is expired. |

## Details

### onError

An error occurred.

> **Note:**This callback indicates that the SDK encountered an unrecoverable error. Such errors must be listened for, and UI reminders should be sent to users if necessary.

```
void onError(int code, String message);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| code | int | The error code. |
| message | String | The error message. |

### onCallReceived

. This callback is received by an invitee. You can listen for this event to determine whether to display the incoming call view.

```
void onCallReceived(String callId, String callerId, List<String> calleeIdList,                     TUICallDefine.MediaType mediaType, TUICallDefine.CallObserverExtraInfo info);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | Unique ID of this call |
| callerId | String | Caller ID |
| calleeIdList | List<String> | Callee ID List |
| mediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |
| info | [TUICallDefine.CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54900#tuicallobserverextrainfo) | Extended information |

### onCallBegin

The call was connected. This callback is received by both the inviter and invitees. You can listen for this event to determine whether to start on-cloud recording, content moderation, or other tasks.

```
void onCallBegin(String callId, TUICallDefine.MediaType mediaType, TUICallDefine.CallObserverExtraInfo info);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | Unique ID of this call |
| mediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |
| info | [TUICallDefine.CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54900#tuicallobserverextrainfo) | Extended information |

### onCallEnd

The call ended. This callback is received by both the inviter and invitees. You can listen for this event to determine when to display call information such as call duration and call type, or stop on-cloud recording.

```
void onCallEnd(String callId, TUICallDefine.MediaType mediaType, TUICallDefine.CallEndReason reason,                String userId, long totalTime, TUICallDefine.CallObserverExtraInfo info);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | Unique ID of this call |
| mediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |
| reason | [TUICallDefine.CallEndReason](https://www.tencentcloud.com/document/product/647/54900#tuicallendreason) | Call end reason |
| userId | String | ââEnded by user ID |
| totalTime | long | The call duration. |
| info | [TUICallDefine.CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54900#tuicallobserverextrainfo) | Extended information |

> **Note:**Client-side callbacks are often lost when errors occur, for example, when the process is closed. If you need to measure the duration of a call for billing or other purposes, we recommend you use the RESTful API.

### onCallNotConnected

The call was canceled by the inviter or timed out. This callback is received by an invitee. You can listen for this event to determine whether to show a missed call message.

This indicates that the call was canceled by the caller, timed out by the callee, rejected by the callee, or the callee was busy. There are multiple scenarios involved. You can listen to this event to achieve UI logic such as missed calls and resetting UI status.

- Call cancellation by the caller: The caller receives the callback (userId is himself); the callee receives the callback (userId is the ID of the caller)
- Callee timeout: the caller will simultaneously receive the [onUserNoResponse](https://www.tencentcloud.com/document/product/647/51007#onusernoresponse) and onCallNotConnected callbacks (userId is his own ID); the callee receives the onCallNotConnected callback (userId is his own ID)
- Callee rejection: The caller will simultaneously receive the [onUserReject](https://www.tencentcloud.com/document/product/647/51007#onuserreject) and onCallNotConnected callbacks (userId is his own ID); the callee receives the onCallNotConnected callback (userId is his own ID)
- Callee busy: The caller will simultaneously receive the [onUserLineBusy](https://www.tencentcloud.com/document/product/647/51007#onuserlinebusy) and onCallNotConnected callbacks (userId is his own ID);
- Abnormal interruption: The callee failed to receive the call ï¼he receives this callback (userId is his own ID).

```
void onCallNotConnected(String callId, TUICallDefine.MediaType mediaType, TUICallDefine.CallEndReason reason,                         String userId, TUICallDefine.CallObserverExtraInfo info);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | Unique ID of this call |
| mediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |
| reason | [TUICallDefine.CallEndReason](https://www.tencentcloud.com/document/product/647/54900#tuicallendreason) | Call end reason |
| userId | String | ââNot connected by user ID |
| info | [TUICallDefine.CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54900#tuicallobserverextrainfo) | Extended information |

### onUserReject

ected. In a one-to-one call, only the inviter will receive this callback. In a group call, all invitees will receive this callback.

```
void onUserReject(String userId);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID of the invitee who rejected the call. |

### onUserNoResponse

```
void onUserNoResponse(String userId);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID of the invitee who did not answer. |

### onUserInviting

A user is invited to join a call.

```
void onUserInviting(String userId);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID of the invite. |

### onUserLineBusy

```
void onUserLineBusy(String userId);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID of the invitee who is busy. |

### onUserJoin

A user joined the call.

```
void onUserJoin(String userId);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The ID of the user who joined the call. |

### onUserLeave

A user left the call.

```
void onUserLeave(String userId);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The ID of the user who left the call. |

### onUserVideoAvailable

Whether a user is sending video.

```
void onUserVideoAvailable(String userId, boolean isVideoAvailable);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID. |
| isVideoAvailable | boolean | Whether the user has video. |

### onUserAudioAvailable

Whether a user is sending audio.

```
void onUserAudioAvailable(String userId, boolean isAudioAvailable);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID. |
| isAudioAvailable | boolean | Whether the user has audio. |

### onUserVoiceVolumeChanged

The volumes of all users.

```
void onUserVoiceVolumeChanged(Map<String, Integer> volumeMap);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| volumeMap | Map | The volume table, which includes the volume of each user (`userId`). Value range: 0-100. |

### onUserNetworkQualityChanged

The network quality of all users.

```
void onUserNetworkQualityChanged(List<TUICallDefine.NetworkQualityInfo> networkQualityList);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| networkQualityList | List | The current network conditions for all users (`userId`). |

### onKickedOffline

The current user was kicked offline: At this time, you can prompt the user with a UI message and then invoke `init` again.

```
void onKickedOffline();
```

### onUserSigExpired

The user sig is expired: At this time, you need to generate a newÂ `userSig`, and then invoke `init` again.

```
void onUserSigExpired();
```

## Deprecated Interface

### onCallCancelled

This indicates that the call was canceled by the caller, timed out by the callee, rejected by the callee, or the callee was busy. There are multiple scenarios involved. You can listen to this event to achieve UI logic such as missed calls and resetting UI status.

- Call cancellation by the caller: The caller receives the callback (userId is himself); the callee receives the callback (userId is the ID of the caller)
- Callee timeout: The caller will simultaneously receive the [onUserNoResponse](https://www.tencentcloud.com/document/product/647/51007#onusernoresponse) and onCallCancelled callbacks (userId is his own ID); the callee receives the onCallCancelled callback (userId is his own ID)
- Callee rejection: The caller will simultaneously receive the [onUserReject](https://www.tencentcloud.com/document/product/647/51007#onuserreject) and onCallCancelled callbacks (userId is his own ID); the callee receives the onCallCancelled callback (userId is his own ID)
- Callee busy: The caller will simultaneously receive the [onUserLineBusy](https://www.tencentcloud.com/document/product/647/51007#onuserlinebusy) and onCallCancelled callbacks (userId is his own ID);
- Abnormal interruption: The callee failed to receive the call ï¼he receives this callback (userId is his own ID).

```
void onCallCancelled(String userId);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID of the inviter. |

### onCallMediaTypeChanged

The call type changed.

```
void onCallMediaTypeChanged(TUICallDefine.MediaType oldCallMediaType,TUICallDefine.MediaType newCallMediaType);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| oldCallMediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type before the change. |
| newCallMediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type after the change. |


---
*Source: [https://trtc.io/document/51007](https://trtc.io/document/51007)*
