# SeatGridWidget

## API Introduction

SeatGridWidget is a basic control we developed for the voice chat room UIKit. This core control provides various APIs such as enabling/disabling the voice chat room, managing microphone positions in the live streaming room, including applying for microphone mode, inviting speakers, moving microphone positions, and kicking someone off the mic.

## API Overview

| API | Description |
| --- | --- |
| [SeatGridController](https://www.tencentcloud.com/document/product/647/69245#de18fda1-4686-42a1-9592-3be78342b946) | Create a SeatGridController object |
| [SeatGridWidget](https://www.tencentcloud.com/document/product/647/69245#d147f174-e55a-4ba2-bbaf-2792c9419650) | Create a SeatGridWidget object |
| [startMicrophone](https://www.tencentcloud.com/document/product/647/69245#1032095a-ba39-4820-aac9-6399f497ec6d) | Open the local microphone |
| [stopMicrophone](https://www.tencentcloud.com/document/product/647/69245#c739e487-b83b-4a78-b432-3f84d867ffa2) | Close the local microphone |
| [muteMicrophone](https://www.tencentcloud.com/document/product/647/69245#b866f4a7-1951-41b8-8629-dd613a030fd5) | Pause publishing local audio stream |
| [unmuteMicrophone](https://www.tencentcloud.com/document/product/647/69245#33b60d36-7ebe-4691-918a-7973122f6cb0) | Resume publishing local audio stream |
| [startVoiceRoom](https://www.tencentcloud.com/document/product/647/69245#fa10462e-e188-4879-9be5-2c2d6a222b6d) | Anchor creates a live room and starts streaming. |
| [stopVoiceRoom](https://www.tencentcloud.com/document/product/647/69245#c739e487-b83b-4a78-b432-3f84d867ffa2) | Anchor stops streaming and destroys the live room. |
| [joinVoiceRoom](https://www.tencentcloud.com/document/product/647/69245#8c23ef17-5f8a-4ddd-b803-f78bd3a18f17) | Audience joins an anchor's live streaming room. |
| [leaveVoiceRoom](https://www.tencentcloud.com/document/product/647/69245#cdba89b2-1d72-4603-9077-c97d158e2fef) | Audience leaves an anchor's live streaming room. |
| [updateRoomSeatMode](https://www.tencentcloud.com/document/product/647/69245#db8d3b1f-26b4-4e79-896a-dc00cc32caac) | Update the seat mode of the room. |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/69245#00371c4a-dda3-4035-8bd2-318591fa7d0f) | Anchor responds to microphone application / Audience responds to microphone invitation |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/69245#dedaef30-7e34-4d1d-87d3-7cad0c60a2d6) | Anchor cancels microphone invitation / Audience cancels microphone application |
| [takeSeat](https://www.tencentcloud.com/document/product/647/69245#c771b29e-ad6c-4cc6-beb6-10a0e2206b11) | Become a speaker. |
| [moveToSeat](https://www.tencentcloud.com/document/product/647/69245#680e8c90-7f4e-4918-aeaf-a6a25fe24ebd) | Move the seat. |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/69245#012b0c17-e336-42c1-9b8f-065981ba626e) | Leave the seat. |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/69245#087189d3-5cf1-4aa3-b465-4f48454c46bf) | Anchor invites users to speak. |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/69245#f1ff3b22-c3e2-47ce-8f62-4447149f4148) | Anchor removes a user from the seat. |
| [lockSeat](https://www.tencentcloud.com/document/product/647/69245#f538dc5d-6dda-4597-863a-8f771d6ba296) | Anchor locks the seat (including position lock, audio status lock and video status lock) |
| [setLayoutMode](https://www.tencentcloud.com/document/product/647/69245#c69ad7f9-71ab-4b3b-8529-8e1a10abebd1) | Anchor sets the layout mode of the seat list. |
| [addObserver](https://www.tencentcloud.com/document/product/647/69245#bc6933f2-783a-4059-8164-d4566dbebe06) | Set event callback |
| [removeObserver](https://www.tencentcloud.com/document/product/647/69245#b0de0bf4-56d2-4b8d-baa3-165e2dab8a3c) | Remove event callback |

## API Details

### SeatGridController

Create an object instance of `SeatGridController`. `SeatGridController` is responsible for providing APIs for the voice chat room scenario.

```
SeatGridController()
```

**Return Value:** SeatGridController

### SeatGridWidget

Create an instance of `SeatGridWidget`. `SeatGridWidget` is responsible for rendering the seat UI.

```
SeatGridWidget(    {super.key,    required this.controller,    this.seatWidgetBuilder,    this.onSeatWidgetTap});
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| key | Key? | How does Flutter control replacing the parameters of an old widget with a new widget |
| controller | [SeatGridController](https://www.tencentcloud.com/document/product/647/69245#de18fda1-4686-42a1-9592-3be78342b946) | Controller of SeatGridWidget, responsible for providing APIs in the live voice room scenario |
| seatWidgetBuilder | [SeatWidgetBuilder](https://www.tencentcloud.com/document/product/647/69245#2f992991-4d2d-4690-a145-203464cec215) | Constructor of the custom seat widget |
| onSeatWidgetTap | [OnSeatWidgetTap](https://www.tencentcloud.com/document/product/647/69245#5a80a5d2-86ad-4ec7-8a28-85d9163cc5ed) | Callback for seat click event |

**Return Value:** SeatGridWidget

### startMicrophone

Open the local microphone.

```
Future<TUIActionCallback> startMicrophone()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### stopMicrophone

Close the local microphone.

```
void stopMicrophone()
```

**Return Value:** void

### muteMicrophone

Pause publishing local audio stream.

```
Future<TUIActionCallback> muteMicrophone()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### unmuteMicrophone

Resume publishing local audio stream.

```
Future<TUIActionCallback> unmuteMicrophone()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### startVoiceRoom

Anchor creates a live room and starts streaming.

```
Future<TUIValueCallBack<TUIRoomInfo>> startVoiceRoom(TUIRoomInfo roomInfo)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomInfo | [TUIRoomInfo](https://www.tencentcloud.com/document/product/647/69251#RoomInfo) | Information of creating a live streaming room |

**Return Value:** Future<[TUIValueCallBack](https://www.tencentcloud.com/document/product/647/69251#TUIValueCallBack%3CT%3E)<[TUIRoomInfo](https://www.tencentcloud.com/document/product/647/69251#RoomInfo)>>

### stopVoiceRoom

Anchor stops streaming and destroys the live room.

```
Future<TUIActionCallback> stopVoiceRoom()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### joinVoiceRoom

Audience joins an anchor's live streaming room.

```
Future<TUIValueCallBack<TUIRoomInfo>> joinVoiceRoom(String roomId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | Live Streaming Room ID |

**Return Value:** Future<[TUIValueCallBack](https://www.tencentcloud.com/document/product/647/69251#TUIValueCallBack%3CT%3E)<[TUIRoomInfo](https://www.tencentcloud.com/document/product/647/69251#RoomInfo)>>

### leaveVoiceRoom

Audience leaves an anchor's live streaming room.

```
Future<TUIActionCallback> leaveVoiceRoom()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### updateRoomSeatMode

Update the seat mode of the room.

```
Future<TUIActionCallback> updateRoomSeatMode(TUISeatMode seatMode)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatMode | [TUISeatMode](https://www.tencentcloud.com/document/product/647/69251#TUISeatMode) | Free to Take: In free-speaking mode, the audience can freely join the podium without applying.applyToTake: Audience become speakers only after the broadcaster agrees. |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### responseRemoteRequest

Anchor responds to microphone application / Audience responds to microphone invitation.

```
Future<TUIActionCallback> responseRemoteRequest(String userId, bool agree)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID that responds to the user. If the current identity is an audience, the ID can be left blank. |
| agree | bool | Whether to accept requests: true for accept, false for deny requests |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### cancelRequest

Anchor cancels microphone invitation / Audience cancels microphone application

```
Future<TUIActionCallback> cancelRequest(String userId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID to be cancelled. If the current identity is an audience, the ID can be left blank. |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### takeSeat

Request to speak (application required in speaking mode)

```
Future<RequestCallback> takeSeat(int seatIndex, int timeout)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| index | int | Microphone position ID for speaking |
| timeout | int | Timeout period, in seconds. If set to 0, the SDK will not perform timeout detection or trigger a timeout callback. |

**Return Value:** Future<[RequestCallback](https://www.tencentcloud.com/document/product/647/69245#1080ad78-303e-457f-897a-8f7e6ca60450)>

### moveToSeat

Remove seat (this function can only be invoked by the user already in the seat)

```
Future<TUIActionCallback> moveToSeat(int index)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| index | int | Microphone position ID that needs to be moved to |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### leaveSeat

Become a listener.

```
Future<TUIActionCallback> leaveSeat()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### takeUserOnSeatByAdmin

Anchor invites users to speak.

```
Future<RequestCallback> takeUserOnSeatByAdmin(int seatIndex, String userId, int timeout)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| index | int | Invited microphone position ID |
| userId | String | ID of the invited user |
| timeout | int | Timeout period, in seconds. If set to 0, the SDK will not perform timeout detection or trigger a timeout callback. |

**Return Value:** Future<[RequestCallback](https://www.tencentcloud.com/document/product/647/69245#1080ad78-303e-457f-897a-8f7e6ca60450)>

### kickUserOffSeatByAdmin

Anchor removes a user from the seat.

```
Future<TUIActionCallback> kickUserOffSeatByAdmin(String userId)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID of the kicked-off user |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### lockSeat

Mute a speaker. Anchor locks the seat (including position lock, audio status lock and video status lock)

```
Future<TUIActionCallback> lockSeat(int index, TUISeatLockParams lockMode)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatIndex | int | The microphone position ID that needs to be locked. |
| lockMode | [TUISeatLockParams](https://www.tencentcloud.com/document/product/647/69251#080212f8-d6ce-4430-b745-2fdd5ef8c330) | Microphone Mute Parameters |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/69251#TUIActionCallback)>

### setLayoutMode

Set the layout mode of the seat list.

```
void setLayoutMode(LayoutMode layoutMode, SeatWidgetLayoutConfig? layoutConfig)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| layoutMode | [LayoutMode](https://www.tencentcloud.com/document/product/647/69245#9054f6cd-8773-447d-9139-3a65d2e9a42f) | The layout mode of the seat position list supports focus layout, grid layout, vertical layout, and free layout. |
| layoutConfig | [SeatWidgetLayoutConfig](https://www.tencentcloud.com/document/product/647/69245#005ea306-be1d-4523-aff0-b8cb65853266) | Layout configuration information only takes effect in free layout mode. |

**Return Value:** void

### addObserver

Set event callback.

```
void addObserver(SeatGridWidgetObserver observer)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| observer | [SeatGridWidgetObserver](https://www.tencentcloud.com/document/product/647/69245#7bf5d75e-dd5a-4b3e-b462-3a31a3cefc22) | Callback object of the core component |

**Return Value:** void

### removeObserver

Remove event callback.

```
void removeObserver(SeatGridWidgetObserver observer)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| observer | [SeatGridWidgetObserver](https://www.tencentcloud.com/document/product/647/69245#7bf5d75e-dd5a-4b3e-b462-3a31a3cefc22) | Callback object of the core component |

**Return Value:** void

## Type Definition

| **Type** | **Meaning** |
| --- | --- |
| [SeatWidgetBuilder](https://www.tencentcloud.com/document/product/647/69245#2f992991-4d2d-4690-a145-203464cec215) | Custom seat widget constructor |
| [OnSeatWidgetTap](https://www.tencentcloud.com/document/product/647/69245#5a80a5d2-86ad-4ec7-8a28-85d9163cc5ed) | Seat click event |
| [OnRoomDismissed](https://www.tencentcloud.com/document/product/647/69245#7fafce42-c335-4cc0-9aca-72a2702a7160) | Received room destruction event |
| [OnKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/69245#b0c03cac-652f-421a-ab6a-e72eb99473f1) | Received event of being removed from room |
| [OnSeatRequestReceived](https://www.tencentcloud.com/document/product/647/69245#b4b4436b-4301-4cc9-8e9f-d6a1daefc34b) | Received request event to speak / Received invitation to speak event |
| [OnSeatRequestCancelled](https://www.tencentcloud.com/document/product/647/69245#bf52fbac-61ab-47dc-8989-d86e78eb58ef) | Event of request to speak / invitation to speak being canceled |
| [OnKickedOffSeat](https://www.tencentcloud.com/document/product/647/69245#2c5e6f5d-a92d-4bf5-aeb5-feb62cfa4d77) | Received event of user removed from microphone |
| [OnUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/69245#62acca5b-e203-47bb-9e26-4a44ac22975e) | User audio status change event. |
| [LayoutMode](https://www.tencentcloud.com/document/product/647/69245#9054f6cd-8773-447d-9139-3a65d2e9a42f) | The layout mode of the seat position list supports focus layout, grid layout, vertical layout, and custom layout. |
| [SeatWidgetLayoutRowAlignment](https://www.tencentcloud.com/document/product/647/69245#b22ba27c-695a-4ea9-9739-7d18450a39b1) | Alignment mode of seat layout |
| [RequestType](https://www.tencentcloud.com/document/product/647/69245#f1f2b39d-2e01-49d4-a5eb-402564d7f0c4) | Request type (apply for microphone mode and invitation to speak) |
| [RequestResultType](https://www.tencentcloud.com/document/product/647/69245#43c7b85d-9c84-4111-a3a3-b2c2e3271e17) | Request result type |
| [RequestCallback](https://www.tencentcloud.com/document/product/647/69245#1080ad78-303e-457f-897a-8f7e6ca60450) | Request result callback |
| [SeatWidgetLayoutConfig](https://www.tencentcloud.com/document/product/647/69245#005ea306-be1d-4523-aff0-b8cb65853266) | Seat layout configuration information |
| [SeatWidgetLayoutRowConfig](https://www.tencentcloud.com/document/product/647/69245#a2174da5-9786-4f90-a09e-01b3d9a99a2f) | Seating layout row layout configuration information |

### SeatWidgetBuilder

Constructor of the custom seat `widget`

```
typedef SeatWidgetBuilder = Widget Function(    BuildContext context,    ValueNotifier<TUISeatInfo> seatInfoNotifier,    ValueNotifier<int> volumeNotifier);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| context | BuildContext | Context |
| seatInfoNotifier | ValueNotifier<[TUISeatInfo](https://www.tencentcloud.com/document/product/647/69251#SeatInfo)> | Seat information notifier |
| volumeNotifier | ValueNotifier<int> | Volume information notifier |

### OnSeatWidgetTap

Seat click event

```
typedef OnSeatWidgetTap = void Function(TUISeatInfo seatInfo);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| seatInfo | [TUISeatInfo](https://www.tencentcloud.com/document/product/647/69251#SeatInfo) | Microphone position information |

### OnRoomDismissed

Received room destruction event

```
typedef OnRoomDismissed = void Function(String roomId);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | room ID |

### OnKickedOutOfRoom

Received event of being removed from room

```
typedef OnKickedOutOfRoom = void Function(String roomId, TUIKickedOutOfRoomReason reason, String message);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | room ID |
| reason | TUIKickedOutOfRoomReason | Reason for being kicked out |
| message | String | Kicked-out info |

### OnSeatRequestReceived

Received request event to speak / Received invitation to speak event

```
typedef OnSeatRequestReceived = void Function(RequestType type, TUIUserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| type | [RequestType](https://www.tencentcloud.com/document/product/647/69245#f1f2b39d-2e01-49d4-a5eb-402564d7f0c4) | Request Type |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/69251#UserInfo) | Requester Information |

### OnSeatRequestCancelled

Event of request to speak / invitation to speak being canceled

```
typedef OnSeatRequestCancelled = void Function(RequestType type, TUIUserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| type | [RequestType](https://www.tencentcloud.com/document/product/647/69245#f1f2b39d-2e01-49d4-a5eb-402564d7f0c4) | Request Type |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/69251#UserInfo) | Operator Information |

### OnKickedOffSeat

Received event of user removed from microphone

```
typedef OnKickedOffSeat = void Function(TUIUserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/69251#UserInfo) | Operator Information |

### OnUserAudioStateChanged

User audio status change event

```
typedef OnUserAudioStateChanged = void Function(TUIUserInfo userInfo, bool hasAudio, TUIChangeReason reason);
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/69251#UserInfo) | Operator Information |
| hasAudio | bool | Whether there is an audio stream |
| reason | [TUIChangeReason](https://www.tencentcloud.com/document/product/647/69251#ChangeReason) | Reason for audio stream change |

### LayoutMode

Layout mode of the seat position list

| Enumeration Value | Meaning |
| --- | --- |
| focus | Focus on layout |
| grid | Grid layout |
| vertical | Vertical layout |
| free | Custom Layout |

### SeatWidgetLayoutRowAlignment

Alignment mode of seat layout

| Enumeration Value | Meaning |
| --- | --- |
| start | Move the seat closer to the starting position |
| end | Move the seat closer to the ending position |
| center | Move the seat closer to the intermediate position |
| spaceBetween | Do not leave space before the first seat and after the last seat. Evenly distribute the remaining space between other seats. |
| spaceAround | Distribute half of the space before the first seat and after the last seat. Evenly distribute the remaining space between other seats. |
| spaceEvenly | Evenly distribute the remaining space between all seats. |

### RequestType

Request Type

| Enumeration Value | Meaning |
| --- | --- |
| applyToTakeSeat | Request to speak |
| inviteToTakeSeat | Invitation to speak |

### RequestResultType

Request to speak / Invitation to speak callback

| Enumeration Value | Meaning |
| --- | --- |
| onAccepted | The request is accepted. |
| onRejected | Request rejected. |
| onCancelled | The request is canceled. |
| onTimeout | Request timeout |
| onError | Request anomaly |

### RequestCallback

Request result callback

| Attribute | Type | Meaning |
| --- | --- | --- |
| code | [TUIError](https://www.tencentcloud.com/document/product/647/69251#NetworkQuality) | Error Code Enumeration |
| message | String | Error code information |
| type | [RequestResultType](https://www.tencentcloud.com/document/product/647/69245#43c7b85d-9c84-4111-a3a3-b2c2e3271e17) | Request result type |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/69251#UserInfo) | Request Processor |

### SeatWidgetLayoutRowConfig

Seating layout row layout configuration information

| Attribute | Type | Meaning |
| --- | --- | --- |
| count | int | Microphone Quantity Displayed in This Row |
| seatSpacing | double | Seat Horizontal Spacing in This Row (This Parameter Is Valid Only When the Alignment Mode Is START, END, and CENTER) |
| seatSize | Size | Seat Layout Size in This Row |
| alignment | [SeatWidgetLayoutRowAlignment](https://www.tencentcloud.com/document/product/647/69245#b22ba27c-695a-4ea9-9739-7d18450a39b1) | Alignment mode of layout in this row |

### SeatWidgetLayoutConfig

Seat layout configuration information

| Required | Type | Description |
| --- | --- | --- |
| rowConfigs | List<[SeatWidgetLayoutRowConfig](https://www.tencentcloud.com/document/product/647/69245#a2174da5-9786-4f90-a09e-01b3d9a99a2f)> | Configuration information list of all rows in seat layout |
| rowSpacing | double | Line Spacing in Seat Layout |

## Event Definition

### SeatGridWidgetObserver

| Event List | Type | Meaning |
| --- | --- | --- |
| onRoomDismissed | [OnRoomDismissed](https://www.tencentcloud.com/document/product/647/69245#7fafce42-c335-4cc0-9aca-72a2702a7160) | Received room destruction event |
| onKickedOutOfRoom | [OnKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/69245#b0c03cac-652f-421a-ab6a-e72eb99473f1) | Received event of being removed from room |
| onSeatRequestReceived | [OnSeatRequestReceived](https://www.tencentcloud.com/document/product/647/69245#b4b4436b-4301-4cc9-8e9f-d6a1daefc34b) | Received request event to speak / Received invitation to speak event |
| onSeatRequestCancelled | [OnSeatRequestCancelled](https://www.tencentcloud.com/document/product/647/69245#bf52fbac-61ab-47dc-8989-d86e78eb58ef) | Event of request to speak / invitation to speak being canceled |
| onKickedOffSeat | [OnKickedOffSeat](https://www.tencentcloud.com/document/product/647/69245#2c5e6f5d-a92d-4bf5-aeb5-feb62cfa4d77) | Received event of user removed from microphone |
| onUserAudioStateChanged | [OnUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/69245#62acca5b-e203-47bb-9e26-4a44ac22975e) | User audio status change event |


---
*Source: [https://trtc.io/document/69245](https://trtc.io/document/69245)*
