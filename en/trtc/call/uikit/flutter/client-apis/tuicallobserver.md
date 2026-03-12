# TUICallObserver

## TUICallObserver API

`TUICallObserver` is the callback class of `TUICallEngine`. You can use it to listen for events.

## Overview

| API | Description |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/54908#onError) | A call occurred during the call. |
| [onUserInviting](https://www.tencentcloud.com/document/product/647/54908#onUserInviting) | Callback when a user is invited to join a call. |
| [onCallReceived](https://www.tencentcloud.com/document/product/647/54908#onCallReceived) | A call invitation was received. |
| [onCallNotConnected](https://www.tencentcloud.com/document/product/647/54908#onCallNotConnected) | Callback for call cancellation |
| [onCallBegin](https://www.tencentcloud.com/document/product/647/54908#onCallBegin) | The call was connected. |
| [onCallEnd](https://www.tencentcloud.com/document/product/647/54908#onCallEnd) | The call ended. |
| [onCallMediaTypeChanged](https://www.tencentcloud.com/document/product/647/54908#onCallMediaTypeChanged) | The call type changed. |
| [onUserReject](https://www.tencentcloud.com/document/product/647/54908#onUserReject) | A user declined the call. |
| [onUserNoResponse](https://www.tencentcloud.com/document/product/647/54908#onUserNoResponse) | A user didn't respond. |
| [onUserLineBusy](https://www.tencentcloud.com/document/product/647/54908#onUserLineBusy) | A user was busy. |
| [onUserJoin](https://www.tencentcloud.com/document/product/647/54908#onUserJoin) | A user joined the call. |
| [onUserLeave](https://www.tencentcloud.com/document/product/647/54908#onUserLeave) | A user left the call. |
| [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/54908#onUserVideoAvailable) | Whether a user had a video stream. |
| [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/54908#onUserAudioAvailable) | Whether a user had an audio stream. |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/54908#onUserVoiceVolumeChanged) | The volume levels of all users. |
| [onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/54908#onUserNetworkQualityChanged) | The network quality of all users. |
| [onKickedOffline](https://www.tencentcloud.com/document/product/647/54908#onKickedOffline) | The current user was kicked offline. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/54908#onUserSigExpired) | The user sig is expired. |

## Details

Listen to the events thrown by the Flutter plugin through addObserver.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onError: (int code, String message) {          },onCallCancelled: (String callerId) {           }, onCallBegin: (TUIRoomId roomId, TUICallMediaType callMediaType, TUICallRole callRole) {           }, onCallEnd: (TUIRoomId roomId, TUICallMediaType callMediaType, TUICallRole callRole, double totalTime) {           }, onCallMediaTypeChanged: (TUICallMediaType oldCallMediaType, TUICallMediaType newCallMediaType) {         }, onUserReject: (String userId) {        }, onUserNoResponse: (String userId) {         }, onUserLineBusy: (String onUserLineBusy) {        }, onUserJoin: (String userId) {      }, onUserLeave: (String userId) {           }, onUserVideoAvailable: (String userId, bool isVideoAvailable) {              }, onUserAudioAvailable: (String userId, bool isAudioAvailable) {             }, onUserNetworkQualityChanged: (List<TUINetworkQualityInfo> networkQualityList) {      }, onCallReceived: (String callerId, List<String> calleeIdList, String groupId, TUICallMediaType callMediaType) {      }, onUserVoiceVolumeChanged: (Map<String, int> volumeMap) {        }, onKickedOffline: () {        }, onUserSigExpired: () {         }  ));
```

### onError

An error occurred.

> **Note:**This callback indicates that the SDK encountered an unrecoverable error. Such errors must be listened for, and UI reminders should be sent to users if necessary.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onError: (int code, String message) {    }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| code | int | The error code. |
| message | String | The error message. |

### onUserInviting

Callback when a user is invited to join a call.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserInviting: (String userId) {      // TODO    }));
```

The parameters are listed in the table below.

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | ID of the invited user |

### onCallReceived

Received a new incoming call request callback, the callee will receive it. You can listen to this event to determine whether to display the call answering interface.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onCallReceived: (String callId, String callerId, List<String> calleeIdList, TUICallMediaType mediaType, CallObserverExtraInfo info) {      // TODO    }));
```

The parameters are listed in the table below.

| Parameter | Type | Meaning |
| --- | --- | --- |
| callId | String | Unique ID of this call |
| callerId | String | Calling ID (inviter) |
| calleeIdList | List<String> | Called ID list (invitees) |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Media type of the call. For example: `TUICallMediaType.video` or `TUICallMediaType.audio` |
| info | [CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54909#CallObserverExtraInfo) | Extended information |

### onCallNotConnected

Callback for call cancellation.

```
TUICallEngine.instance.addObserver(TUICallObserver(  onCallNotConnected: (String callId, TUICallMediaType mediaType, CallEndReason reason,    String userId, CallObserverExtraInfo info) {    // TODO  }));
```

The parameters are listed in the table below.

| Parameter | Type | Meaning |
| --- | --- | --- |
| callId | String | Unique ID of this call |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Media type of the call. For example: `TUICallMediaType.video` or `TUICallMediaType.audio` |
| reason | [CallEndReason](https://www.tencentcloud.com/document/product/647/54909#CallEndReason) | The causes for call termination |
| userId | String | User ID ending the call |
| info | [CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54909#CallObserverExtraInfo) | Extended information |

### onCallBegin

Indicates that the call is connected, and both the caller and callee can receive it. You can listen to this event to start processes such as cloud recording and content review.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onCallBegin: (String callId, TUICallMediaType mediaType, CallObserverExtraInfo info) {    // TODO  }));
```

The parameters are listed in the table below.

| Parameter | Type | Meaning |
| --- | --- | --- |
| callId | String | Unique ID of this call |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Media type of the call. For example: `TUICallMediaType.video` or `TUICallMediaType.audio` |
| info | [CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54909#CallObserverExtraInfo) | Extended information |

### onCallEnd

Indicates that the call is connected, and both the caller and callee can receive it. You can listen to this event to display information such as call duration and call type, or to stop the cloud recording process.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onCallEnd: (String callId, TUICallMediaType mediaType, CallEndReason reason,        String userId, double totalTime, CallObserverExtraInfo info) {    // TODO  }));
```

The parameters are listed in the table below.

| Parameter | Type | Meaning |
| --- | --- | --- |
| callId | String | Unique ID of this call |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Media type of the call. For example: `TUICallMediaType.video` or `TUICallMediaType.audio` |
| reason | [CallEndReason](https://www.tencentcloud.com/document/product/647/54909#CallEndReason) | The causes for call termination |
| userId | String | User ID ending the call |
| totalTime | double | Duration of this call, unit ms |
| info | [CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54909#CallObserverExtraInfo) | Extended information |

> **Note:**Events on the client side are generally lost due to exceptions such as process termination. If you need to complete billing logic by monitoring call duration, it is recommended to use REST API to complete such processes.

### onCallMediaTypeChanged

The call type changed.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onCallMediaTypeChanged: (TUICallMediaType oldCallMediaType, TUICallMediaType newCallMediaType) {      }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| oldCallMediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | The call type before the change. |
| newCallMediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | The call type after the change. |

### onUserReject

The call was rejected. In a one-to-one call, only the inviter will receive this callback. In a group call, all invitees will receive this callback.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserReject: (String userId) {        }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| res.userId | String | The user ID of the invitee who rejected the call. |

### onUserNoResponse

A user did not respond.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserNoResponse: (String userId) {     }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID of the invitee who did not answer. |

### onUserLineBusy

A user is busy.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserLineBusy: (String onUserLineBusy) {       },));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID of the invitee who is busy. |

### onUserJoin

A user joined the call.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserJoin: (String userId) {      }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The ID of the user who joined the call. |

### onUserLeave

A user left the call.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserLeave: (String userId) {         }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The ID of the user who left the call. |

### onUserVideoAvailable

Whether a user is sending video.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserVideoAvailable: (String userId, bool isVideoAvailable) {       }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID. |
| isVideoAvailable | bool | Whether the user has video. |

### onUserAudioAvailable

Whether a user is sending audio.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserAudioAvailable: (String userId, bool isAudioAvailable) {           }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID. |
| isAudioAvailable | bool | Whether the user has audio. |

### onUserVoiceVolumeChanged

The volumes of all users.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserVoiceVolumeChanged: (Map<String, int> volumeMap) {      }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| volumeMap | Map<String, int> | The volume table, which includes the volume of each user (userId). Value range: 0-100. |

### onUserNetworkQualityChanged

The network quality of all users.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserNetworkQualityChanged: (List<TUINetworkQualityInfo> networkQualityList) {    }));class TUINetworkQualityInfo {        String userId;      TUINetworkQuality quality;      TUINetworkQualityInfo({required this.userId, required this.quality});}enum TUINetworkQuality {    unknown,    excellent,  good,    poor,    bad,    vBad,    down}
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| networkQualityList | List<[TUINetworkQualityInfo](https://www.tencentcloud.com/document/product/647/54909#89efd105-cdee-4f3f-bde1-5db01af79d56)> | The current network conditions for all users (userId). |

### onKickedOffline

The current user was kicked offlineï¼At this time, you can prompt the user with a UI message and then invoke `init`again.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onKickedOffline: () {     }));
```

### onUserSigExpired

The user sig is expiredï¼At this time, you need to generate a newÂ `userSig`, and then invoke `init`again.

```
TUICallEngine.instance.addObserver(TUICallObserver(    onUserSigExpired: () {        }  ));
```

## Deprecated interfaces

### onCallCancelled

The call was canceled by the inviter or timed out. This callback is received by an invitee. You can listen for this event to determine whether to show a missed call message.

This indicates that the call was canceled by the caller, timed out by the callee, rejected by the callee, or the callee was busy. There are multiple scenarios involved. You can listen to this event to achieve UI logic such as missed calls and resetting UI status.

- Call cancellation by the caller: The caller receives the callback (userId is himself); the callee receives the callback (userId is the ID of the caller) .
- Callee timeout: the caller will simultaneously receive the [onUserNoResponse](https://www.tencentcloud.com/document/product/647/54908#onUserNoResponse) and onCallCancelled callbacks (userId is his own ID); the callee receives the onCallCancelled callback (userId is his own ID) .
- Callee rejection: The caller will simultaneously receive the [onUserReject](https://www.tencentcloud.com/document/product/647/54908#onUserReject) and onCallCancelled callbacks (userId is his own ID); the callee receives the onCallCancelled callback (userId is his own ID) .
- Callee busy: The caller will simultaneously receive the [onUserLineBusy](https://www.tencentcloud.com/document/product/647/54908#onUserLineBusy) and onCallCancelled callbacks (userId is his own ID);
- Abnormal interruption: The callee failed to receive the call ï¼he receives this callback (userId is his own ID).

```
TUICallEngine.instance.addObserver(TUICallObserver(    onCallCancelled: (String userId) {        }));
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The user ID of the inviter. |


---
*Source: [https://trtc.io/document/54908](https://trtc.io/document/54908)*
