# Seat Management

This document mainly introduces the seat management capabilities of `SeatGridView`.

`SeatGridView` supports the following seat management capabilities:

| [Take seat](https://www.tencentcloud.com/document/product/647/67502#494143bf-42cb-4a08-b04f-d74da39f1727) | [Leave Seat](https://www.tencentcloud.com/document/product/647/67502#3b3251b9-edc9-4d46-89f8-24f400db4a80) | [Move seat](https://www.tencentcloud.com/document/product/647/67502#f24a7800-7b1c-4c82-8fcd-cde610488e0e) |
| --- | --- | --- |
| [Invite to take seat](https://www.tencentcloud.com/document/product/647/67502#f1da6aac-0b50-4b81-866a-09f10de69f9c) | [Kick off seat](https://www.tencentcloud.com/document/product/647/67502#27702725-1726-4864-a61d-7b75bcd5c69b) | [Lock seat](https://www.tencentcloud.com/document/product/647/67502#da05ecbd-24b9-467b-a704-4ec8a52e0ebf) |

## Prerequisites

Before using `SeatGridView`, you need to [integrate and log in](https://www.tencentcloud.com/document/product/647/67506#) to SeatGridView to ensure the subsequent features work properly.

## Usage guide

### Step 1: Adding SeatGridView to the View

You need to import the `SeatGridView` module first, then create a SeatGridView object and add it to your view.

iOS

Android

```

```

```

```

### Step 2: Managing Seats

> **Note:**Note: When using seat management, you need to ensure that you have started broadcasting or entered the live room.

#### Take seat

The behavior of applying to speak is related to the speaking mode.

When the speaking mode of the live room is "apply to speak mode (`applyToTake`)", applying to speak requires the room owner's approval.

When the speaking mode of the live room is "free to speak mode (`freeToTake`)", applying to speak does not require the room owner's approval and can be done directly.

When you want to speak, call the `takeSeat` API and pass in two parameters: seat index and timeout duration.

iOS

Android

```
let index = 1    // Please replace this with the seat number you want to apply for (context: code line content)let timeout = 30 // Please replace this with the timeout duration for your speaking request, in seconds. If set to 0, the SDK will not perform timeout detection or trigger timeout callbacks.self.seatGridView.takeSeat(index: index, timeout: timeout) { userInfo in    // Speaking request accepted} onRejected: { userInfo in    // Speaking request rejected} onCancelled: { userInfo in    // Speaking request canceled} onTimeout: { userInfo in    // Speaking request timed out} onError: { userInfo, code, message in    // Speaking request error}
```

```
int index = 1;    // Please replace this with the seat number you want to apply for (context: code line content)int timeout = 30; // Replace this with the timeout duration for requesting to speak, in seconds. If set to 0, the SDK will not perform timeout detection or trigger timeout callbacksseatGridView.takeSeat(index, timeout, new TUIRoomDefine.RequestCallback() {    @Override    public void onAccepted(String requestId, String userId) {        // Speaking request accepted    }    @Override    public void onRejected(String requestId, String userId, String message) {        // Speaking request rejected    }    @Override    public void onCancelled(String requestId, String userId) {        // Speaking request canceled    }    @Override    public void onTimeout(String requestId, String userId) {        // Speaking request timed out    }    @Override    public void onError(String requestId, String userId, TUICommonDefine.Error error, String message) {        // Speaking request error    }});
```

When you are the host and someone requests to speak, you will receive the `onSeatRequestReceived` callback. You can call `responseRemoteRequest` to accept/reject the speaking request.

iOS

Android

```
func onSeatRequestReceived(type: SGRequestType, userInfo: TUIUserInfo) {    if type == .applyToTakeSeat {        let agree = true // true means        self.seatGridView.responseRemoteRequest(userId: userInfo.userId, agree: true) {            // Agreed to speak successfully        } onError: { code, message in             // Failed to agree to speak        }    }}
```

```
void onSeatRequestReceived(VoiceRoomDefine.RequestType type, TUIRoomDefine.UserInfo userInfo) {    if (type == APPLY_TO_TAKE_SEAT) {        boolean agree = true;    // true: agree to connect, false: refuse to connect        seatGridView.seatGridView.responseRemoteRequest(userInfo.userId, agree, new TUIRoomDefine.ActionCallback() {            @Override            public void onSuccess () {                // Agreed to speak successfully            }            @Override            public void onError (TUICommonDefine.Error error, String message) {                // Agreed to speak successfully            }        });    }}
```

#### Leave Seat

When you are speaking and want to leave, you can call the `leaveSeat` API.

iOS

Android

```
self.seatGridView.leaveSeat {   // Left the seat successfully} onError: { code, message in   // Failed to leave the seat}
```

```
seatGridView.leaveSeat(new TUIRoomDefine.ActionCallback {    @Override    public void onSuccess () {        // Left the seat successfully    }    @Override    public void onError (TUICommonDefine.Error error, String message) {        // Failed to leave the seat    }});
```

#### Move Seat

When you are on seat 1 and want to switch to seat 2, you can call the `moveToSeat` API and pass in the index of the seat to switch to.

iOS

Android

```
let index = 2self.seatGridView.moveToSeat(index: destinationIndex) {    // Successfully moved the seat} onError: { code, message in     // Failed to move the seat}
```

```
int index = 2;seatGridView.moveToSeat(index, new TUIRoomDefine.ActionCallback {    @Override    public void onSuccess () {        // Successfully moved the seat    }    @Override    public void onError (TUICommonDefine.Error error, String message) {        // Failed to move the seat    }});
```

#### Invite to take seat

When you are the host and want to invite someone not on the mic to seat 4, you can call the `takeUserOnSeatByAdmin` API, passing three parameters: the seat index to invite to, the timeout period, and the user ID of the person being invited.

iOS

Android

```
let tartgetIndex = 4let timeout = 30let targetUserId = "100002"  // Please replace this with the user ID of the host you want to remove from the mic.self.takeUserOnSeatByAdmin(index: targetIndex, timeout: timeout, userId: targetUserId) {     // Speaking invitation accepted} onRejected: { userInfo in     // Speaking invitation rejected} onTimeout: { userInfo in     // Speaking invitation timed out} onCancelled: { userInfo in     // Speaking invitation canceled} onError: { userInfo, code, message in     // Speaking invitation error}
```

```
int tartgetIndex = 4;int timeout = 30;String targetUserId = "100002";  // Please replace this with the user ID of the host you want to remove from the mic.seatGridView.takeUserOnSeatByAdmin(targetIndex, timeout, targetUserId, new new TUIRoomDefine.RequestCallback() {    @Override    public void onAccepted(String requestId, String userId) {        // Speaking invitation accepted    }    @Override    public void onRejected(String requestId, String userId, String message) {        // Speaking invitation rejected    }    @Override    public void onCancelled(String requestId, String userId) {        // Speaking invitation canceled    }    @Override    public void onTimeout(String requestId, String userId) {        // Speaking invitation timed out    }    @Override    public void onError(String requestId, String userId, TUICommonDefine.Error error, String message) {        // Speaking invitation error    }});
```

When someone invites you to speak, you will receive the onSeatRequestReceived callback. You can call `responseRemoteRequest` to accept/reject the speaking invitation.

iOS

Android

```
func onSeatRequestReceived(type: SGRequestType, userInfo: TUIUserInfo) {    if type == .inviteToTakeSeat {        let isAccepted = true // true means accepting the invitation, false means rejecting the invitation        self.seatGridView.responseRemoteRequest(userId: userInfo.userId, agree: isAccepted) {            // Agreed to speak invitation successfully        } onError: { code, message in             // Failed to agree to speak invitation        }    }}
```

```
void onSeatRequestReceived(VoiceRoomDefine.RequestType type, TUIRoomDefine.UserInfo userInfo) {    if (type == INVITE_TO_TAKE_SEAT) {        boolean isAccepted = true; // true means accepting the invitation, false means rejecting the invitation        seatGridView.responseRemoteRequest(userInfo.userId, isAccepted,  new TUIRoomDefine.ActionCallback {            @Override            public void onSuccess () {                // Agreed to speak invitation successfully            }            @Override            public void onError (TUICommonDefine.Error error, String message) {                // Failed to agree to speak invitation            }        });    }}
```

#### Kick off seat

When you are the host and want to remove the speaker on seat 3, you can call the `kickUserOffSeatByAdmin` API and pass in the user ID of the speaker you want to remove.

iOS

Android

```
String targetUserId = "100002"; // Please replace this with the user ID of the host you want to remove from the mic.seatGridView.kickUserOffSeatByAdmin(targetUserId,  new TUIRoomDefine.ActionCallback {    @Override    public void onSuccess () {        // Successfully removed a speaker    }    @Override    public void onError (TUICommonDefine.Error error, String message) {        // Failed to remove a speaker    }});
```

```
String targetUserId = "100002"; // Please replace this with the user ID of the host you want to remove from the mic.self.seatGridView.kickUserOffSeatByAdmin(targetUserId,  new TUIRoomDefine.ActionCallback {    @Override    public void onSuccess () {        // Successfully removed a speaker    }    @Override    public void onError (TUICommonDefine.Error error, String message) {        // Failed to remove a speaker    }});
```

#### Lock Seat

When you are the host and want to lock the empty seat at position 5 to prevent others from taking it, or mute the host on seat 6, you can call the `lockSeat` API, passing in two parameters: the index of the seat to be locked and the lock mode.

The structure of the lock mode (`TUISeatLockParams`) is as follows:

| Property Name | Field Description | Additional Notes | Data Type | Example |
| --- | --- | --- | --- | --- |
| lockSeat |  Lock Microphone Position | Locking the corresponding seat prevents applications to take that seat. | Boolean value | True when the seat is locked. |
| lockVideo | Lock the seat camera. | Locking the corresponding seat camera will stop the seat from publishing video streams. | Boolean value | false |
| lockAudio | Lock the seat microphone. | Locking the corresponding seat camera will stop the seat from publishing audio streams.  | Boolean value | True when the seat microphone is locked. |

iOS

Android

```
// Lock a seat.let lockSeatIndex = 5let lockSeatParam = TUISeatLockParams()lockSeatParam.lockSeat = trueself.seatGridView.lockSeat(index: lockSeatIndex, lockMode: lockSeatParam) {   // Lock the seat successfully} onError: { code, message in    // Failed to lock the seat}// Lock the seat microphonelet lockSeatAudioIndex = 6let lockSeatAudioParam = TUISeatLockParams()lockSeatAudioParam.lockAudio = trueself.seatGridView.lockSeat(index: lockSeatAudioIndex, lockMode: lockSeatAudioParam) {    // Lock the seat microphone successfully} onError: { code, message in     // Failed to lock the seat microphone}
```

```
// Lock a seat.int lockSeatIndex = 5;TUIRoomDefine.SeatLockParams lockSeatParam = new TUIRoomDefine.SeatLockParams();lockSeatParam.lockSeat = true;seatGridView.lockSeat(lockSeatIndex, lockSeatParam, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Lock the seat successfully    }    @Override    public void onError(TUICommonDefine.Error error, String message) {       // Failed to lock the seat    }});// Lock the seat microphoneint lockSeatIndex = 6;TUIRoomDefine.SeatLockParams lockSeatAudioParam = new TUIRoomDefine.SeatLockParams();lockSeatAudioParam.lockAudio = true;seatGridView.lockSeat(lockSeatIndex, lockSeatAudioParam, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {        // Lock the seat microphone successfully    }    @Override    public void onError(TUICommonDefine.Error error, String message) {        // Failed to lock the seat microphone    }});
```


---
*Source: [https://trtc.io/document/67502](https://trtc.io/document/67502)*
