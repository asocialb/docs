# Signaling Management

## Overview

Signaling APIs are a set of invitation process control APIs based on Chat messages. They can be used to implement a variety of real-time features, including:

- Audio-video chat rooms: mic on or mic off
- Chatting: audio/video calls
- Education: control of the process for teachers to invite students to "raise hands"

## Features

Signaling APIs support the following features:

### One-to-one chat invitation

You can use the [invite](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_signaling_manager/V2TIMSignalingManager/invite.html) signaling API to make an point-to-point call. When receiving the invitation notification [onReceiveNewInvitation](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimSignalingListener/V2TimSignalingListener/onReceiveNewInvitation.html), the invitee can choose to accept the invitation, reject, or wait until the invitation times out.

### Group chat invitation

Members of the group can initiate a group call invitation via [inviteInGroup](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_signaling_manager/V2TIMSignalingManager/inviteInGroup.html) within the group. When receiving the invitation [onReceiveNewInvitation](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimSignalingListener/V2TimSignalingListener/onReceiveNewInvitation.html), an invitee can choose to accept, reject, or wait until the invitation times out.

### Canceling an invitation

Before an invitation times out and the invitee processes the invitation, the inviter can cancel the invitation via [cancel](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_signaling_manager/V2TIMSignalingManager/cancel.html). After the inviter cancels the invitation, an invitee will receive a cancellation notification [onInvitationCancelled](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimSignalingListener/V2TimSignalingListener/onInvitationCancelled.html), and the invitation process ends.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2532342b18bd11efb8185254005ac0ca.png)

### Accepting an invitation

When receiving an invitation `onReceiveNewInvitation`, an invitee can accept the invitation via [accept](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_signaling_manager/V2TIMSignalingManager/accept.html) before the invitation times out and the inviter cancels the invitation. If the invitee accepts the invitation, the inviter will receive an invitation acceptance notification [onInviteeAccepted](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimSignalingListener/V2TimSignalingListener/onInviteeAccepted.html). After the processing (including acceptance, rejection, and timeout) at the invitee side ends, the invitation process ends.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/25301ebf18bd11efb8185254005ac0ca.png)

### Rejecting an invitation

When receiving an invitation notification `onReceiveNewInvitation`, an invitee can reject the invitation via [reject](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_signaling_manager/V2TIMSignalingManager/reject.html) before the invitation times out and the inviter cancels the invitation. If the invitee rejects the invitation, the inviter will receive an invitation rejection notification [onInviteeRejected](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimSignalingListener/V2TimSignalingListener/onInviteeRejected.html). After the processing (including acceptance, rejection, and timeout) at the invitee side ends, the invitation process ends.

### Invitation timeout

If the timeout duration of the invitation API is greater than 0 and an invitee does not respond within the timeout duration, the invitation times out, and the inviter and invitee will receive a timeout notification [onInvitationTimeout](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimSignalingListener/V2TimSignalingListener/onInvitationTimeout.html). After the processing (including acceptance, rejection, and timeout) at the invitee side ends, the invitation process ends. If the timeout duration of the invitation API is 0, there will be no timeout notification.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2534641518bd11efb24e52540019e87e.png)

## Use Cases

### Audio/Video call

In the open-source project [TRTCFlutterScenesDemo](https://github.com/tencentyun/TRTCFlutterScenesDemo), we developed an audio/video call solution suitable for one-to-one and multi-person chatting based on [TRTC](https://intl.cloud.tencent.com/document/product/647/41691). You can directly modify the demo for adaptation. The following takes the one-to-one video call process as an example to introduce how signaling APIs work with the TRTC SDK.

**One-to-one video call process:**

1. The inviter enters the TRTC room based on the room ID generated at the service layer and calls the signaling invitation API `invite` to initiate an audio/video call request, including the room ID in the custom field of the invitation API.
2. The invitee receives the signaling invitation notification `onReceiveNewInvitation` and gets the room ID based on the custom data. The invitee's phone begins to ring.
3. The invitee processes the invitation notification:
  - Accepting the invitation: the invitee calls the `accept` signaling API and enters the TRTC room based on the room ID, and calls the `openCamera()` function to enable the local camera. The inviter and invitee receive the `onRemoteUserEnterRoom` callback from the TRTC SDK, and the systems of the two parties record the start time of the call.
  - Rejecting the invitation: the invitee calls the `reject` signaling API to end the call.
  - If the invitee is on the phone with someone else, the invitee calls the `reject` signaling API to reject the invitation and specify the rejection reason (busy local line) in the custom data.
4. After the invitee answers the call and the audio/video channel between the inviter and invitee is established, both the inviter and invitee will receive the `onUserVideoAvailable` event notification from the TRTC SDK, which indicates that they have received each other's video image. At this point, they can call the `startRemoteView` API of the TRTC SDK to display the remote video image, and the remote audio will be played back by default.
5. After the call ends (either the inviter or invitee hangs up), the party who hangs up exits the TRTC room. The other party receives the `onRemoteUserLeaveRoom` callback from the TRTC SDK, and its system calculates the total duration of the call and initiates an invitation again, including the call end event and call duration in the custom data to facilitate UI display.

**Flowchart**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/25218f6c18bd11efb5a45254002977b6.png)

### Education: teacher inviting students to "raise hands"

In this scenario, the teacher asks students to "raise hands" and then chooses one of the students to speak. The process is as follows:

1. The teacher calls the `inviteInGroup` API to invite students to "raise hands", specifying the "hand raising" operation in the custom field `data`. The students receive the `onReceiveNewInvitation` callback.
2. Based on the `inviteeList` and `data` fields in `onReceiveNewInvitation`, a student determines that he/she is one of the invitees and the operation is hand raising. Then the student calls the `accept` API to raise her/his hand.
3. If a student raises her/his hand, others can receive the `onInviteeAccepted` callback. The system determines that the `data` field is hand raising and displays the list of students who raise hands.
4. The teacher calls the `inviteInGroup` API to invite one of the students who raise their hands to speak. At this time, the system specifies the "speaking" operation in the custom field `data`. The students receive the `onReceiveNewInvitation` callback.
5. Based on the `inviteeList` and `data` fields in the `onReceiveNewInvitation` callback, a student determines that he/she is one of the invitees and the operation is speaking. Then the student calls the `accept` API to speak.
6. If a student speaks, others can receive the `onInviteeAccepted` callback, and their systems determine that the data field is speaking and display the list of students who speak.


---
*Source: [https://trtc.io/document/46309](https://trtc.io/document/46309)*
