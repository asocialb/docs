# SeatGridView

## API Introduction

SeatGridView is a basic control we developed for the Voice Chat Room UIKit. This core control provides rich APIs such as opening/closing the voice chat room, managing seat positions within the live room like applying to join the seat, inviting to take seat, moving seat positions, and kicking someone off the seat.

## API Overview

| **API** | **Description** |
| --- | --- |
| [SeatGridView](https://www.tencentcloud.com/document/product/647/66793#d147f174-e55a-4ba2-bbaf-2792c9419650) | Create a SeatGridView object, supporting **code creation** and **XML loading**. |
| [startMicrophone](https://www.tencentcloud.com/document/product/647/66793#1032095a-ba39-4820-aac9-6399f497ec6d) | Enable local microphone |
| [stopMicrophone](https://www.tencentcloud.com/document/product/647/66793#c739e487-b83b-4a78-b432-3f84d867ffa2) | Disable local microphone |
| [muteMicrophone](https://www.tencentcloud.com/document/product/647/66793#b866f4a7-1951-41b8-8629-dd613a030fd5) | Pause publishing local audio stream |
| [unmuteMicrophone](https://www.tencentcloud.com/document/product/647/66793#33b60d36-7ebe-4691-918a-7973122f6cb0) | Resume publishing local audio stream |
| [startVoiceRoom](https://www.tencentcloud.com/document/product/647/66793#fa10462e-e188-4879-9be5-2c2d6a222b6d) | Anchor creates live room and starts streaming |
| [stopVoiceRoom](https://www.tencentcloud.com/document/product/647/66793#89f1f933-1771-4f4e-81af-5e0d38dce48e) | Anchor stops streaming and destroys live room |
| [joinVoiceRoom](https://www.tencentcloud.com/document/product/647/66793#8c23ef17-5f8a-4ddd-b803-f78bd3a18f17) | Audience joins an anchor's live room |
| [leaveVoiceRoom](https://www.tencentcloud.com/document/product/647/66793#cdba89b2-1d72-4603-9077-c97d158e2fef) | Audience leaves an anchor's live room |
| [updateRoomSeatMode](https://www.tencentcloud.com/document/product/647/66793#db8d3b1f-26b4-4e79-896a-dc00cc32caac) | Update Room Mic Mode |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/66793#00371c4a-dda3-4035-8bd2-318591fa7d0f) | Anchor Responds to Microphone Application/Audience Responds to Microphone Invitation |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/66793#dedaef30-7e34-4d1d-87d3-7cad0c60a2d6) | Anchor Cancels Microphone Invitation/Audience Cancels Microphone Application |
| [takeSeat](https://www.tencentcloud.com/document/product/647/66793#c771b29e-ad6c-4cc6-beb6-10a0e2206b11) | Connect Mic |
| [moveToSeat](https://www.tencentcloud.com/document/product/647/66793#680e8c90-7f4e-4918-aeaf-a6a25fe24ebd) | Disconnect Mic |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/66793#012b0c17-e336-42c1-9b8f-065981ba626e) | Disconnect Mic |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/66793#087189d3-5cf1-4aa3-b465-4f48454c46bf) | Anchor Invites User to Connect Mic |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/66793#f1ff3b22-c3e2-47ce-8f62-4447149f4148) | Anchor Kicks User off Mic |
| [lockSeat](https://www.tencentcloud.com/document/product/647/66793#f538dc5d-6dda-4597-863a-8f771d6ba296) | Anchor Locks Mic Position (including position lock, audio status lock, and video status lock) |
| [setLayoutMode](https://www.tencentcloud.com/document/product/647/66793#c69ad7f9-71ab-4b3b-8529-8e1a10abebd1) | Anchor Sets Layout Mode for Mic List |
| [setSeatViewAdapter](https://www.tencentcloud.com/document/product/647/66793#58713969-f561-4dd1-aa5d-f188888358dd) | Set the adapter for the seat view |
| [addObserver](https://www.tencentcloud.com/document/product/647/66793#bc6933f2-783a-4059-8164-d4566dbebe06) | Set event callbacks |
| [removeObserver](https://www.tencentcloud.com/document/product/647/66793#b0de0bf4-56d2-4b8d-baa3-165e2dab8a3c) | Remove event callbacks |

## API Details

### SeatGridView

Create a SeatGridView object instance. Supports **code creation** and **XML loading**.

```
public SeatGridView(Context context)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| context | Context | Android context object |

**Return Value:**SeatGridView

### startMicrophone

Enable the local mic.

```
void startMicrophone(ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### stopMicrophone

Disable the local mic.

```
void stopMicrophone()
```

**Return Value:**void

### muteMicrophone

Pause publishing local audio stream.

```
void muteMicrophone()
```

**Return Value:**void

### unmuteMicrophone

Resume publishing local audio stream.

```
void unmuteMicrophone(ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### startVoiceRoom

Anchor creates live room and starts streaming.

```
void startVoiceRoom(RoomInfo roomInfo, GetRoomInfoCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomInfo | RoomInfo | Information for creating a live streaming room |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### stopVoiceRoom

Anchor stops streaming and destroys live room.

```
void stopVoiceRoom(ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### joinVoiceRoom

Audience joins an anchor's live room.

```
void joinVoiceRoom(String roomId, GetRoomInfoCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomId | String | Live Streaming Room ID |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### leaveVoiceRoom

Audience leaves an anchor's live room.

```
void leaveVoiceRoom(ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### updateRoomSeatMode

Update Room Mic Mode.

```
void updateRoomSeatMode(SeatMode seatMode, ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| seatMode | SeatMode | FREE_TO_TAKE: Free seat mode, audience can join the seat freely without application;APPLY_TO_TAKE: Apply to join the seat mode, audience needs the anchor's consent to join the seat. |
| callback | ActionCallback | Callback of the operation. |

**Return Value:**void

### responseRemoteRequest

Anchor Responds to Microphone Application/Audience Responds to Microphone Invitation.

```
void responseRemoteRequest(String userId, boolean agree, ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| userId | String | Responding user's user ID, if the current role is an audience member, the ID can be left blank |
| agree | boolean | Whether to accept the request, true: accept the request, false: reject the request |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### cancelRequest

Anchor Cancels Microphone Invitation/Audience Cancels Microphone Application

```
void cancelRequest(String userId, ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| userId | String | Cancelled user's ID, if the current role is an audience member, the ID can be left blank |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### takeSeat

Request to Speak (In speaking mode, application is required)

```
void takeSeat(int index, int timeout, VoiceRoomDefine.RequestCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| index | int | Mic position number for connecting |
| timeout | int | Timeout period, unit: seconds. If set to 0, the SDK will not perform a timeout check or trigger a timeout callback |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### moveToSeat

Move Mic (only users who are already on the seat can call this function)

```
void moveToSeat(int index, ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| index | int | Mic position number to move to |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### leaveSeat

Proactively leave seat

```
void leaveSeat(ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### takeUserOnSeatByAdmin

Anchor Invites User to Connect Mic

```
void takeUserOnSeatByAdmin(int index, String userId, int timeout, VoiceRoomDefine.RequestCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| index | int | Invited Mic position number |
| userId | String | Invited user ID |
| timeout | int | Timeout period, unit: seconds. If set to 0, the SDK will not perform a timeout check or trigger a timeout callback |
| callback | VoiceRoomDefine.RequestCallback | Callback of the operation |

**Return Value:**void

### kickUserOffSeatByAdmin

Anchor Kicks User off Mic

```
void kickUserOffSeatByAdmin(String userId, ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| userId | String | User ID kicked off the Mic |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### lockSeat

Microphone Mute, Anchor locks Mic Position (including position lock, audio status lock, and video status lock)

```
void lockSeat(int seatIndex, TUIRoomDefine.SeatLockParams params, ActionCallback callback)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| seatIndex | int | Mic position number to be locked |
| params | TUIRoomDefine.SeatLockParams | Microphone Mute Parameters. See details: TUIRoomDefine.SeatLockParams |
| callback | ActionCallback | Callback of the operation |

**Return Value:**void

### setLayoutMode

Set the layout mode for the mic list.

```
void setLayoutMode(LayoutMode layoutModel, SeatViewLayoutConfig layoutConfig)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| layoutModel | [LayoutMode](https://www.tencentcloud.com/document/product/647/66793#9054f6cd-8773-447d-9139-3a65d2e9a42f) | Mic list layout modes, support element layout, grid layout, vertical layout, custom layout. |
| layoutConfig | [SeatViewLayoutConfig](https://www.tencentcloud.com/document/product/647/66793#005ea306-be1d-4523-aff0-b8cb65853266) | Layout configuration information, effective only in custom layout mode |

**Return Value:**void

### setSeatViewAdapter

Set the adapter for the mic view.

```
void setSeatViewAdapter(VoiceRoomDefine.SeatViewAdapter adapter)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| adapter | [SeatViewAdapter](https://www.tencentcloud.com/document/product/647/66793#293c3d02-4706-45e4-b1f1-64e9eae8fb57) | Seat view adapter |

**Return Value:**void

### addObserver

Set event callbacks.

```
void addObserver(SeatGridViewObserver observer)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| observer | [SeatGridViewObserver](https://www.tencentcloud.com/document/product/647/66793#4749ed20-b069-4691-98be-b39e4d477478) | Callback object of core component |

**Return Value:**void

### removeObserver

Remove event callbacks.

```
void removeObserver(SeatGridViewObserver observer)
```

**Parameter:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| observer | [SeatGridViewObserver](https://www.tencentcloud.com/document/product/647/66793#4749ed20-b069-4691-98be-b39e4d477478) | Callback object of core component |

**Return Value:**void

## Type Definition

| Type | Description |
| --- | --- |
| [LayoutMode](https://www.tencentcloud.com/document/product/647/66793#9054f6cd-8773-447d-9139-3a65d2e9a42f) | Layout modes of the seat position list support element layout, grid layout, vertical layout, and custom layout |
| [SeatViewLayoutRowAlignment](https://www.tencentcloud.com/document/product/647/66793#b22ba27c-695a-4ea9-9739-7d18450a39b1) | Alignment of seat position layout |
| [RequestType](https://www.tencentcloud.com/document/product/647/66793#f1f2b39d-2e01-49d4-a5eb-402564d7f0c4) | Request type (apply to speak and invite to speak) |
| [Size](https://www.tencentcloud.com/document/product/647/66793#287537f0-ad04-4e6a-b22a-4e7cea633be3) | Size of the seat position layout |
| [SeatViewLayoutConfig](https://www.tencentcloud.com/document/product/647/66793#005ea306-be1d-4523-aff0-b8cb65853266) | Microphone position layout configuration information |
| [SeatViewLayoutRowConfig](https://www.tencentcloud.com/document/product/647/66793#a2174da5-9786-4f90-a09e-01b3d9a99a2f) | Seating Layout Row Configuration Information |
| [RequestCallback](https://www.tencentcloud.com/document/product/647/66793#43c7b85d-9c84-4111-a3a3-b2c2e3271e17) | Request Callback |
| [SeatViewAdapter](https://www.tencentcloud.com/document/product/647/66793#293c3d02-4706-45e4-b1f1-64e9eae8fb57) | Seat view adapter |

### LayoutMode

Layout modes of the seat position list

| Type | Description |
| --- | --- |
| FOCUS | Element Layout |
| GRID | Grid Layout |
| VERTICAL | Vertical layout |
| FREE | Customized Layout |

### SeatViewLayoutRowAlignment

Alignment of seat position layout

| Type | Description |
| --- | --- |
| START | Seat position near the start |
| END | Seat position near the end |
| CENTER | Seat position near the middle |
| SPACE_BETWEEN | No space before the first and after the last seat positions, evenly distribute the remaining space between other seat positions |
| SPACE_AROUND | Distribute half of the space before the first and after the last seat positions, evenly distribute the remaining space between other seat positions |
| SPACE_EVENLY | Evenly distribute the remaining space between all seat positions |

### RequestType

Request type

| Type | Description |
| --- | --- |
| APPLY_TO_TAKE_SEAT | Apply to speak |
| INVITE_TO_TAKE_SEAT | Invite to speak |

### Size

Size of the seat position layout

| Type | Description |
| --- | --- |
| width | Layout width |
| height | Layout height |

### SeatViewLayoutConfig

Microphone position layout configuration information

| Type | Description |
| --- | --- |
| rowConfigs | List of all row configuration information in the seat layout, refer to [SeatViewLayoutRowConfig](https://www.tencentcloud.com/document/product/647/66793#a2174da5-9786-4f90-a09e-01b3d9a99a2f) for content. |
| rowSpacing | Seat row spacing |

### SeatViewLayoutRowConfig

Seating Layout Row Configuration Information

| Type | Description |
| --- | --- |
| count | Number of seats displayed in this row |
| seatSpacing | Horizontal spacing of each seat in this row (effective only when the alignment is START, END, or CENTER) |
| seatSize | Size of the seat layout in this row |
| alignment | Alignment of the layout in this row ([SeatViewLayoutRowAlignment](https://www.tencentcloud.com/document/product/647/66793#b22ba27c-695a-4ea9-9739-7d18450a39b1)) |

### RequestCallback

Request to speak/Invite to speak callback

| API | Description |
| --- | --- |
| [onAccepted](https://www.tencentcloud.com/document/product/647/66793#47d95d62-30bd-498f-b28d-1374aa6bc1aa) | Request accepted |
| [onRejected](https://www.tencentcloud.com/document/product/647/66793#e11ca47d-e1a2-4262-93f5-3a47314b075f) | Request rejected |
| [onCancelled](https://www.tencentcloud.com/document/product/647/66793#cfb3a227-6b8a-46ef-81ee-403888140d27) | Request canceled |
| [onTimeout](https://www.tencentcloud.com/document/product/647/66793#7f4dfc89-27fa-4d20-abcc-f32bcf91b443) | Request timeout |
| [onError](https://www.tencentcloud.com/document/product/647/66793#bf674805-17b7-4113-b166-6beaa22cb695) | Request Exception |

### SeatViewAdapter

Seat View Adapter Interface, you can customize the display UI of each seat by implementing this interface.

| API | Description |
| --- | --- |
| [createSeatView](https://www.tencentcloud.com/document/product/647/66793#23b3931d-345f-4193-82ed-f9ff8c9890cf) | Callback when creating a single seat layout. |
| [updateSeatView](https://www.tencentcloud.com/document/product/647/66793#a4508d98-522b-4cc6-83f3-e1d2e2ee8bda) | Callback when updating the seat view. |
| [updateUserVolume](https://www.tencentcloud.com/document/product/647/66793#283e2cca-68b0-48b4-92f6-cc15b40db7f2) | Callback when updating user volume. |

## Event Callback Details

### onAccepted

Application to speak/invite to speak request accepted.

```
void onAccepted(TUIRoomDefine.UserInfo userInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | Response to the current request's user information |

**Returned value: void**

### onRejected

Application to speak/invite to speak request rejected.

```
void onRejected(TUIRoomDefine.UserInfo userInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | Response to the current request's user information |

**Returned value: void**

### onCancelled

Application to speak/invite to speak request canceled.

```
void onCancelled(TUIRoomDefine.UserInfo userInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | User information for the canceled request |

**Returned value: void**

### onTimeout

Application to speak/invite to speak request timed out.

```
void onTimeout(TUIRoomDefine.UserInfo userInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | User information for the initiated request |

**Returned value: void**

### onError

Application to speak/invite to speak request error.

```
void onError(TUIRoomDefine.UserInfo userInfo, TUICommonDefine.Error error, String message);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | User information for the initiated request |
| error | TUICommonDefine.Error | Error code |
| message | String | Error message |

**Returned value: void**

### createSeatView

Callback when creating a single seat layout, you need to return your custom view, and the core view will help you create the view.

```
View createSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| seatGridView | SeatGridView | Core components of voice chat room |
| seatInfo | SeatInfo | Seat information |

**Returned value: View**

### updateSeatView

Callback when updating the seat view, you can update your seat view based on the seatInfo information returned by the callback.

```
void updateSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo, View seatView);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| seatGridView | SeatGridView | Core components of voice chat room |
| seatInfo | SeatInfo | Seat information |
| seatView | View | Current updated seat view |

**Return Value:**void

### updateUserVolume

Callback when updating user volume, you can update your seat view based on the returned volume.

```
void updateUserVolume(SeatGridView seatGridView, int volume, View seatView);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| seatGridView | SeatGridView | Core components of voice chat room |
| volume | int | Volume level |
| seatView | View | Current seat layout view with volume changes |

**Return Value:**void

## SeatGridViewObserver Overview

| Function List | Description |
| --- | --- |
| [onRoomDismissed](https://www.tencentcloud.com/document/product/647/66793#00a13207-98ef-4cba-8e0a-6641a965048a) | Event of Room Termination Received |
| [onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/66793#698b164e-c775-48f1-88b7-85ea8c18e94c) | Event of Being Kicked Out of the Room Received |
| [onSeatRequestReceived](https://www.tencentcloud.com/document/product/647/66793#485a04e9-742d-4cbb-901d-cf1018cc71e5) | Event of Request for Speaking/Invitation to Speak Received |
| [onSeatRequestCancelled](https://www.tencentcloud.com/document/product/647/66793#6fc11c74-e851-465c-bbe1-8d06fc8aa6cf) | Event of Request for Speaking/Invitation to Speak Canceled |
| [onKickedOffSeat](https://www.tencentcloud.com/document/product/647/66793#2b9086aa-a2d0-4cad-962e-b35e6e29dc95) | Event of User Kicked Off Seat Received |
| [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/66793#51b2b526-d288-48b4-96bb-abb28bf03186) | Event of User Audio Status Changed |
| [onSeatViewClicked](https://www.tencentcloud.com/document/product/647/66793#8f985ad2-a119-49d1-b66d-a775730a04bf) | Seat View Click Event |

## SeatGridViewObserver Details

### onRoomDismissed

Event of Live Room Destroyed

```
void onRoomDismissed(String roomId);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |

**Return Value:**void

### onKickedOutOfRoom

Event of Being Kicked Out of the Room

```
void onKickedOutOfRoom(String roomId, TUIRoomDefine.KickedOutOfRoomReason reason, String message);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| reason | KickedOutOfRoomReason | Reason for Being Kicked Out |
| message | String | Description of Being Kicked Out |

**Return Value:**void

### onSeatRequestReceived

Event of Request for Speaking/Invitation to Speak Received

```
void onSeatRequestReceived(VoiceRoomDefine.RequestType type, TUIRoomDefine.UserInfo userInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| type | [RequestType](https://www.tencentcloud.com/document/product/647/66793#f1f2b39d-2e01-49d4-a5eb-402564d7f0c4) | Request type (Request for Speaking, Invitation to Speak) |
| userInfo | UserInfo | Information of the user who sent the request |

**Return Value:**void

### onSeatRequestCancelled

Event of Request for Speaking/Invitation to Speak Canceled

```
void onSeatRequestCancelled(VoiceRoomDefine.RequestType type, TUIRoomDefine.UserInfo userInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| type | [RequestType](https://www.tencentcloud.com/document/product/647/66793#f1f2b39d-2e01-49d4-a5eb-402564d7f0c4) | Request type (Request for Speaking, Invitation to Speak) |
| userInfo | UserInfo | Information of the user who canceled the request |

**Return Value:**void

### onKickedOffSeat

Event of User Kicked Off Seat

```
void onKickedOffSeat(UserInfo userInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | Information of the host who kicked the user off the seat |

**Return Value:**void

### onUserAudioStateChanged

Event of User Audio Status Changed

```
void onUserAudioStateChanged(UserInfo userInfo, boolean hasAudio, TUIRoomDefine.ChangeReason reason);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | User Information |
| hasAudio | boolean | Is there an audio stream |
| reason | ChangeReason | Reason for audio stream change |

**Return Value:**void

### onSeatViewClicked

Seat View Click Event

```
void onSeatViewClicked(View seatView, TUIRoomDefine.SeatInfo seatInfo);
```

**Parameter:**

| Parameter | Type | Description |
| --- | --- | --- |
| seatView | View | Currently clicked seat view object |
| seatInfo | SeatInfo | Seat information |

**Return Value:**void


---
*Source: [https://trtc.io/document/66793](https://trtc.io/document/66793)*
