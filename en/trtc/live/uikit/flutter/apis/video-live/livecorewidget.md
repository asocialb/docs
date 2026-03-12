# LiveCoreWidget

## API Introduction

LiveCoreWidget is a basic control we developed for the video live streaming UIKit. This core control provides various APIs, including preview before broadcasting, start video live streaming, stop video live streaming, live streaming room connection with audience, and cross-room connection with other anchors.

## API Overview

| **API** | **Description** |
| --- | --- |
| [LiveCoreController](https://www.tencentcloud.com/document/product/647/71717#9dc179ef-0d86-4141-9977-7ff13303e767) | Create a LiveCoreController object |
| [LiveCoreWidget](https://www.tencentcloud.com/document/product/647/71717#LiveCoreView) | Create a LiveCoreWidget object. |
| [startCamera](https://www.tencentcloud.com/document/product/647/71717#startCamera) | Start camera capture and display the screen on LiveCoreView. |
| [startMicrophone](https://www.tencentcloud.com/document/product/647/71717#startMicrophone) | Open local microphone |
| [muteMicrophone](https://www.tencentcloud.com/document/product/647/71717#muteMicrophone) | Pause publishing local audio stream |
| [unmuteMicrophone](https://www.tencentcloud.com/document/product/647/71717#f31392be-e46b-4485-a3a3-902a9049d6e7) | Resume publishing suspended local audio stream |
| [stopCamera](https://www.tencentcloud.com/document/product/647/71717#stopCamera) | Turn the local camera off |
| [stopMicrophone](https://www.tencentcloud.com/document/product/647/71717#stopMicrophone) | Close local microphone |
| [startLiveStream](https://www.tencentcloud.com/document/product/647/71717#startLiveStream) | Anchor create live room and start streaming |
| [stopLiveStream](https://www.tencentcloud.com/document/product/647/71717#stopLiveStream) | Anchor stop streaming and destroy live room |
| [joinLiveStream](https://www.tencentcloud.com/document/product/647/71717#joinLiveStream) | Audience joins a certain live streaming room |
| [leaveLiveStream](https://www.tencentcloud.com/document/product/647/71717#leaveLiveStream) | Audience leaves a certain live streaming room |
| [requestIntraRoomConnection](https://www.tencentcloud.com/document/product/647/71717#requestIntraRoomConnection) | Audience requests to connect with the anchor |
| [cancelIntraRoomConnection](https://www.tencentcloud.com/document/product/647/71717#cancelIntraRoomConnection) | Cancel the request to connect with the anchor |
| [respondIntraRoomConnection](https://www.tencentcloud.com/document/product/647/71717#respondIntraRoomConnection) | Anchor responds to the audience's request for connection |
| [disconnectUser](https://www.tencentcloud.com/document/product/647/71717#disconnectUser) | Anchor disconnects the audience |
| [terminateIntraRoomConnection](https://www.tencentcloud.com/document/product/647/71717#terminateIntraRoomConnection) | Audience disconnects from the anchor |
| [requestCrossRoomConnection](https://www.tencentcloud.com/document/product/647/71717#requestCrossRoomConnection) | Anchor requests cross-room connection with another anchor |
| [cancelCrossRoomConnection](https://www.tencentcloud.com/document/product/647/71717#cancelCrossRoomConnection) | Cancel the request for cross-room connection with another anchor |
| [respondToCrossRoomConnection](https://www.tencentcloud.com/document/product/647/71717#respondToCrossRoomConnection) | Anchor responds to the connection request |
| [terminateCrossRoomConnection](https://www.tencentcloud.com/document/product/647/71717#terminateCrossRoomConnection) | Anchor disconnects |
| [registerConnectionObserver](https://www.tencentcloud.com/document/product/647/71717#registerConnectionObserver) | Register a callback for connection event |
| [unregisterConnectionObserver](https://www.tencentcloud.com/document/product/647/71717#unregisterConnectionObserver) | Unregister a callback for connection event |
| [requestBattle](https://www.tencentcloud.com/document/product/647/71717#5a298e69-e93d-4986-8406-9cdc0e994b54) | Initiate a battle request |
| [cancelBattle](https://www.tencentcloud.com/document/product/647/71717#0228de17-fcaa-49ca-8dc5-a046020dd232) | Cancel a battle request |
| [respondToBattle](https://www.tencentcloud.com/document/product/647/71717#93c6c3bb-5e1d-46d6-bd91-ce6e43d17be9) | Respond to battle request |
| [terminateBattle](https://www.tencentcloud.com/document/product/647/71717#95c773bf-2602-42d0-82f9-d4759045b0ed) | End PK |
| [registerBattleObserver](https://www.tencentcloud.com/document/product/647/71717#18d3b663-c086-4e7c-875c-6b6508bd0de1) | Register a callback for PK event |
| [unregisterBattleObserver](https://www.tencentcloud.com/document/product/647/71717#565c44fe-d5f9-4d13-998d-b4ed4c54c111) | Unregister a callback for PK event |
| [setLayoutMode](https://www.tencentcloud.com/document/product/647/71717#setLayoutMode) | Set the layout mode for the connected host's video image |
| [startPreloadVideoStream](#ba916442-759a-4d6a-b7d0-7b2bc25607a1) | Start room video stream preview. |
| [stopPreloadVideoStream](#dae12088-a34a-441b-8cf9-363ea3282097) | Stop room video stream preview. |

## API Details

### LiveCoreController

Create a LiveCoreController object instance.

```
LiveCoreController()
```

**Return value:** LiveCoreController

### LiveCoreWidget

Create a LiveCoreWidget object instance.

```
LiveCoreWidget(    {super.key,    required this.controller,    this.videoWidgetBuilder});
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| key | Key? | Flutter controls how to replace an old widget with a new one using parameters |
| controller | [LiveCoreController](https://www.tencentcloud.com/document/product/647/71717#9dc179ef-0d86-4141-9977-7ff13303e767) | LiveCoreWidget controller, responsible for providing live streaming scenario APIs |
| videoWidgetBuilder | [VideoWidgetBuilder](https://www.tencentcloud.com/document/product/647/71717#c80fba60-cd47-4c93-afbe-64caf4428951) | Custom view widget constructor |

**Return value:** LiveCoreWidget

### startCamera

Start camera capture and display the screen on LiveCoreWidget.

```
Future<TUIActionCallback> startCamera(bool useFrontCamera)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| useFrontCamera | bool | true: use the front camera; false: use the rear-facing camera |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### startMicrophone

Open local microphone.

```
Future<TUIActionCallback> startMicrophone()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### muteMicrophone

Pause publishing local audio stream.

```
void muteMicrophone()
```

**Return Value:** void

### unmuteMicrophone

Resume publishing suspended local audio stream.

```
Future<TUIActionCallback> unmuteMicrophone()
```

**Return Value:** void

### stopCamera

Turn the local camera off.

```
void stopCamera()
```

**Return Value:** void

### stopMicrophone

Close local microphone.

```
void stopMicrophone()
```

**Return Value:** void

### startLiveStream

Anchor create live room and start streaming.

```
Future<TUIValueCallBack<TUIRoomInfo>> startLiveStream(TUIRoomInfo roomInfo)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomInfo | [TUIRoomInfo](https://www.tencentcloud.com/document/product/647/67259#RoomInfo) | Create live streaming room info |

**Return Value:** Future<[TUIValueCallBack](https://www.tencentcloud.com/document/product/647/67259#TUIValueCallBack%3CT%3E)<[TUIRoomInfo](https://www.tencentcloud.com/document/product/647/67259#RoomInfo)>>

### stopLiveStream

Anchor stop streaming and destroy live room.

```
Future<TUIActionCallback> stopLiveStream()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### joinLiveStream

Audience joins a certain live streaming room.

```
Future<TUIValueCallBack<TUIRoomInfo>> joinLiveStream(String roomId)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomId | String | Live streaming room ID |

**Return Value:** Future<[TUIValueCallBack](https://www.tencentcloud.com/document/product/647/67259#TUIValueCallBack%3CT%3E)<[TUIRoomInfo](https://www.tencentcloud.com/document/product/647/67259#RoomInfo)>>

### leaveLiveStream

Audience leaves a certain live streaming room.

```
Future<TUIActionCallback> leaveLiveStream()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### requestIntraRoomConnection

Audience requests to connect with the anchor.

```
Future<TUIActionCallback> requestIntraRoomConnection(    String userId,    int timeout,     bool openCamera)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| userId | String | User ID. If the input is the anchor ID, it signifies the audience requests to connect with the anchor (defaults to the anchor's user ID if the input is an empty string). For other user IDs, it represents the anchor inviting the corresponding user to connect. |
| timeout | int | Request timeout duration, in seconds. |
| openCamera | bool | Whether to open the camera upon success. true: video communication, false: audio mic connection. |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### cancelIntraRoomConnection

Cancel the request to connect with the anchor.

```
Future<TUIActionCallback> cancelIntraRoomConnection(String userId)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| userId | String | The user ID for canceling mic connection. If the input is the anchor ID, it signifies the audience cancels the request to connect with the anchor (an empty string defaults to the anchor's user ID). For other user IDs, it signifies the anchor cancels the invitation to connect with the corresponding user. |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### respondIntraRoomConnection

The anchor responds to the audience's request for connection.

```
Future<TUIActionCallback> respondIntraRoomConnection(String userId, bool isAccepted)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| userId | String | Anchor response to the audience user ID in live streaming room connection. If the anchor's user ID is imported, it signifies the audience response to the anchor's invitation (defaults to the anchor's user ID when an empty string is input). |
| isAccepted | bool | Whether to accept the mic connection request. true: grant the request, false: reject the request. |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### disconnectUser

Anchor disconnects the audience.

```
Future<TUIActionCallback> disconnectUser(String userId)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| userId | String | Anchor needs to disconnect the user ID |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### terminateIntraRoomConnection

Audience disconnects from the anchor.

```
Future<TUIActionCallback> terminateIntraRoomConnection()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### requestCrossRoomConnection

Anchor requests cross-room connection with another anchor.

```
Future<TUIValueCallBack<TUIConnectionCode?>> requestCrossRoomConnection(String roomId, int timeout)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomId | String | Room ID for cross-room connection request. |
| timeout | int | Request timeout duration, in seconds. |

**Return Value:** Future<[TUIValueCallBack](https://www.tencentcloud.com/document/product/647/67259#TUIValueCallBack%3CT%3E)<[TUIConnectionCode](https://www.tencentcloud.com/document/product/647/69265#92daac9cd74ffae905ec2f0dbd85a61e)?>>

### cancelCrossRoomConnection

Cancel the request for cross-room connection with another anchor.

```
Future<TUIActionCallback> cancelCrossRoomConnection(String roomId)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomId | String | Room ID for canceling the connection |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### respondToCrossRoomConnection

The anchor responds to the connection request.

```
Future<TUIActionCallback> respondToCrossRoomConnection(String roomId, bool isAccepted)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomId | String | Room ID for connection response |
| isAccepted | bool | Whether to agree to connection. true: agree to connection, false: reject connection. |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### terminateCrossRoomConnection

Anchor disconnects.

```
Future<TUIActionCallback> terminateCrossRoomConnection()
```

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### registerConnectionObserver

Register a callback for connection event.

```
void registerConnectionObserver(ConnectionObserver observer)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| observer | [ConnectionObserver](https://www.tencentcloud.com/document/product/647/71717#4749ed20-b069-4691-98be-b39e4d477478) | callback object for connection event |

**Return Value:** void

### unregisterConnectionObserver

Unregister a callback for connection event.

```
void unregisterConnectionObserver(ConnectionObserver observer)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| observer | [ConnectionObserver](https://www.tencentcloud.com/document/product/647/71717#4749ed20-b069-4691-98be-b39e4d477478) | callback object for connection event |

**Return Value:** void

### requestBattle

Initiate a battle request.

```
Future<TUIValueCallBack<BattleRequestCallback>> requestBattle(    TUIBattleConfig config,     List<String> userIdList,     int timeout)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| config | [TUIBattleConfig](https://www.tencentcloud.com/document/product/647/69266#6ca8b8898efedde803c17d8513bbcae7) | PK parameter configuration, including PK duration and extended information. PK currently supports a maximum duration of 300 seconds. |
| userIdList | List<String> | Invite the room owner's userId for PK |
| timeout | int | PK request timeout duration, in seconds |

**Return Value:** Future<[TUIValueCallBack](https://www.tencentcloud.com/document/product/647/67259#TUIValueCallBack%3CT%3E)<[BattleRequestCallback](https://www.tencentcloud.com/document/product/647/71717#c6cb7126-6f5a-40d7-af7d-1dbf39971e27)>>

### cancelBattle

Cancel the battle request.

```
Future<TUIActionCallback> cancelBattle(String battleId, List<String> userIdList)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| battleId | String | PK unique representation |
| userIdList | List<String> | Cancel the room owner's userId invitation for PK |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### respondToBattle

Respond to a battle request.

```
Future<TUIActionCallback> respondToBattle(String battleId, bool isAccepted)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| battleId | String | PK unique representation |
| isAccepted | bool | Grant PK invitation |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### terminateBattle

End PK.

```
Future<TUIActionCallback> terminateBattle(String battleId)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| battleId | String | PK unique representation |

**Return Value:** Future<[TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback)>

### registerBattleObserver

Register a callback for PK event.

```
void registerBattleObserver(BattleObserver observer)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| observer | [BattleObserver](https://www.tencentcloud.com/document/product/647/71717#5ae5500d-fffd-4088-b14c-f5e7977fe7db) | callback object for PK event |

**Return Value:** void

### unregisterBattleObserver

Unregister a callback for connection event.

```
void unregisterBattleObserver(BattleObserver observer)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| observer | [BattleObserver](https://www.tencentcloud.com/document/product/647/71717#5ae5500d-fffd-4088-b14c-f5e7977fe7db) | callback object for PK event |

**Return Value:** void

### setLayoutMode

Set the layout mode for the connected host's video image.

```
void setLayoutMode(    LayoutMode layoutMode,     bool showEmptySeat,    String? layoutJson)
```

**Parameters:**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| layoutMode | LayoutMode | The layout mode when connecting supports grid layout, floating window layout, and custom layout. |
| showEmptySeat | bool | Whether to display empty mic slots (unavailable) |
| layoutJson | String? | The json string for the layout. For specific usage, see [Set Custom Layout](https://www.tencentcloud.com/document/product/647/69844#c8b2a34d-a77c-43cc-aede-5de27fe4e42b). |

**Return Valueï¼**void

### startPreloadVideoStream

Start room video stream preview.

```
void startPreloadVideoStream(    String roomId,    bool isMuteAudio,     int viewId,    TUIPlayCallback? playCallback)
```

**Parametersï¼**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomId | String | Preview the room number for video streaming |
| isMuteAudio | bool | Whether to mute the preview video str |
| viewId | int | View ID returned when creating a VideoVie |
| playCallback | TUIPlayCallback? | Preview video stream callback function |

**Return Valueï¼**void

### stopPreloadVideoStream

Stop room video stream preview.

```
void stopPreloadVideoStream(String roomId)
```

**Parametersï¼**

| **Parameter** | **Type** | **Meaning** |
| --- | --- | --- |
| roomId | String | Stop previewing the video stream of the room numbe |

**Return Valueï¼**void

## Type Definition

| Type | Description |
| --- | --- |
| [LayoutMode](https://www.tencentcloud.com/document/product/647/71717#9054f6cd-8773-447d-9139-3a65d2e9a42f) | The layout mode when connecting |
| [CoHostUser](https://www.tencentcloud.com/document/product/647/71717#c6cb7126-6f5a-40d7-af7d-1dbf39971e27) | Connected user data |
| [BattleUserWidgetModel](https://www.tencentcloud.com/document/product/647/71717#c0172cf5-a08d-4749-b91f-baab3b1a8566) | PK user view location data |
| [BattleRequestCallback](https://www.tencentcloud.com/document/product/647/71717#c6cb7126-6f5a-40d7-af7d-1dbf39971e27) | Battle request result callback |
| [CoGuestWidgetBuilder](https://www.tencentcloud.com/document/product/647/71717#2059fa21-01e7-4767-a658-f813872e6de1) | View widget constructor for live co-streaming |
| [CoHostWidgetBuilder](https://www.tencentcloud.com/document/product/647/71717#5bd38bde-fe02-401a-b32e-b65fc5c12c92) | View widget constructor for connecting |
| [BattleWidgetBuilder](https://www.tencentcloud.com/document/product/647/71717#a532d664-4ce5-4018-afe9-8ed4bf15ee9c) | View widget constructor for host video during PK |
| [BattleContainerWidgetBuilder](https://www.tencentcloud.com/document/product/647/71717#0310762a-6c8a-4c27-a600-b60fad1ac6c3) | Full-screen view widget constructor for PK |
| [VideoWidgetBuilder](https://www.tencentcloud.com/document/product/647/71717#c80fba60-cd47-4c93-afbe-64caf4428951) | Custom view widget constructor |
| [OnConnectedUsersUpdated](https://www.tencentcloud.com/document/product/647/71717#92c1c3a0-a443-409f-8387-d9a919bc126a) | Callback for changes in the list of users in mic-connection |
| [OnUserConnectionRequest](https://www.tencentcloud.com/document/product/647/71717#27bbd67b-3219-4eab-bc33-6cfe2fbf22d8) | Callback for received mic connection request |
| [OnUserConnectionCancelled](https://www.tencentcloud.com/document/product/647/71717#599f86a6-6279-4661-a354-d1ddc048e29e) | Callback for received mic connection cancellation request |
| [OnUserConnectionAccepted](https://www.tencentcloud.com/document/product/647/71717#9b5cc9e7-e550-40cb-8813-e0adca8b52bd) | Callback for approved mic connection request |
| [OnUserConnectionRejected](https://www.tencentcloud.com/document/product/647/71717#54471d34-a295-4a2a-aa00-f6c3c5d11097) | Callback for rejected mic connection request |
| [OnUserConnectionTimeout](https://www.tencentcloud.com/document/product/647/71717#851ba2a3-31ef-4bea-92d0-552368ca32c4) | Callback for mic connection request timeout |
| [OnUserConnectionTerminated](https://www.tencentcloud.com/document/product/647/71717#54471d34-a295-4a2a-aa00-f6c3c5d11097) | Callback for anchor disconnecting the audience mic connection |
| [OnUserConnectionExited](https://www.tencentcloud.com/document/product/647/71717#79e4d128-82a8-4bd4-9b64-aedb26b2ea57) | Callback for audience proactive disconnection of the connecting line |
| [OnConnectedRoomsUpdated](https://www.tencentcloud.com/document/product/647/71717#d78f13c7-6557-4d24-8dfe-9d1e36a1d17c) | Callback for changes in the cross-room connection room list |
| [OnCrossRoomConnectionRequest](https://www.tencentcloud.com/document/product/647/71717#7a392403-d3be-4428-a77d-31cc07f73ffe) | Callback for received cross-room connection request |
| [OnCrossRoomConnectionCancelled](https://www.tencentcloud.com/document/product/647/71717#0164d32d-6a49-4496-8936-e7fe81c069c6) | Callback for received cancellation of cross-room connection request |
| [OnCrossRoomConnectionAccepted](https://www.tencentcloud.com/document/product/647/71717#6fc2fd8a-df82-4f5e-ad65-609323b2a60b) | Callback for received consent to cross-room connection |
| [OnCrossRoomConnectionRejected](https://www.tencentcloud.com/document/product/647/71717#25bdeb8d-af4d-412b-8e34-cad7837a52d4) | Callback for received deny of cross-room connection |
| [OnCrossRoomConnectionTimeout](https://www.tencentcloud.com/document/product/647/71717#8d9a17f2-80df-4bfb-b038-01f989dcc328) | Callback for received cross-room connection timeout |
| [OnCrossRoomConnectionExited](https://www.tencentcloud.com/document/product/647/71717#ee1a8a6e-d66a-49c9-b2b2-c634ab68b034) | Callback for received cross-room disconnection |
| [OnBattleStarted](https://www.tencentcloud.com/document/product/647/71717#96f38127-6750-4dfb-ac60-ff42cdfd2a51) | Callback for received PK start |
| [OnBattleEnded](https://www.tencentcloud.com/document/product/647/71717#1da99d71-00fc-4745-9b06-b8d87cfcf9c5) | Callback for received PK end |
| [OnUserJoinBattle](https://www.tencentcloud.com/document/product/647/71717#d35cc67e-0b73-4374-9772-e4eb938b1622) | Callback for received participant join PK end |
| [OnUserExitBattle](https://www.tencentcloud.com/document/product/647/71717#9e88ed31-4c7c-4daf-8e04-5c7769740cfe) | Callback for received participant leave PK end |
| [OnBattleScoreChanged](https://www.tencentcloud.com/document/product/647/71717#46d6b97c-accc-41a8-8450-ce96817fef17) | Callback for received PK score change |
| [OnBattleRequestReceived](https://www.tencentcloud.com/document/product/647/71717#863b2120-dd82-452c-91ff-376dd49b6fc3) | Callback for received battle request |
| [OnBattleRequestCancelled](https://www.tencentcloud.com/document/product/647/71717#2cecedfe-013c-4a73-b1b2-d94dbd7e00c0) | Received cancellation of battle request |
| [OnBattleRequestTimeout](https://www.tencentcloud.com/document/product/647/71717#259bb7a6-e30d-4737-9621-7529b3563c1e) | Callback for received PK request timeout |
| [OnBattleRequestAccept](https://www.tencentcloud.com/document/product/647/71717#a7b081c3-ed02-45c9-9951-258c78c9da92) | Received callback for battle request approval |
| [OnBattleRequestReject](https://www.tencentcloud.com/document/product/647/71717#8e6c5bd9-dbe3-4d89-b57f-c880df745a4f) | Callback for received reject PK request |
| [OnRoomDismissed](https://www.tencentcloud.com/document/product/647/71717#fc7dafdc-c27d-4768-9d81-1ac3ff48ee40) | Callback for received room termination |

### LayoutMode

Layout mode of the microphone position list

| Enumeration Value | Description |
| --- | --- |
| focus | Focus layout |
| grid | grid layout |
| vertical | vertical layout |
| free | custom layout |

### CoHostUser

Connected user data

| Attribute | Type | Description |
| --- | --- | --- |
| connectionUser | [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connected user personal information |
| hasAudioStream | bool | Connected user audio stream information |
| hasVideoStream | bool | Connected user video stream information |

### BattleUserWidgetModel

| Attribute | Type | Description |
| --- | --- | --- |
| battleUser | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK user personal information |
| rect | Rect | PK user view location info |

### BattleRequestCallback

Battle request result callback

| Attribute | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| requestedUserList | List<[TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5)> | PK invite list of users |
| onError | void Function([TUIError](https://www.tencentcloud.com/document/product/647/67259#NetworkQuality) error, String message) | PK invite error result |

### CoGuestWidgetBuilder

View widget `widget` constructor for live co-streaming

```
typedef CoGuestWidgetBuilder = Widget Function(    BuildContext context,     TUIUserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| context | BuildContext | Context |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Mic-connecting user information |

### CoHostWidgetBuilder

View widget `widget` constructor for live co-streaming

```
typedef CoHostWidgetBuilder = Widget Function(    BuildContext context,     CoHostUser userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| context | BuildContext | Context |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Connected user data |

### BattleWidgetBuilder

View widget constructor for host video during PK

```
typedef BattleWidgetBuilder = Widget Function(    BuildContext context,     TUIBattleUser userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| context | BuildContext | Context |
| userInfo | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK user information |

### BattleContainerWidgetBuilder

Full-screen view widget `widget` constructor for PK

```
typedef BattleContainerWidgetBuilder = Widget Function(    BuildContext context,     List<BattleUserWidgetModel> battleModels);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| context | BuildContext | Context |
| battleModels | List<[BattleUserWidgetModel](https://www.tencentcloud.com/document/product/647/71717#c0172cf5-a08d-4749-b91f-baab3b1a8566)> | PK user view position layout info |

### VideoWidgetBuilder

Custom view widget constructor

```
typedef OnSeatWidgetTap = void Function(TUISeatInfo seatInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| seatInfo | [TUISeatInfo](https://www.tencentcloud.com/document/product/647/67259#SeatInfo) | seat information |

### OnConnectedUsersUpdated

Callback for changes in the list of users in mic-connection

```
typedef OnConnectedUsersUpdated = void Function(    List<TUIUserInfo> userList,    List<TUIUserInfo> joinList,     List<TUIUserInfo> leaveList);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userList | List<[TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo)> | co-broadcasting user list |
| joinList | List<[TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo)> | list of users who joined co-broadcasting |
| leaveList | List<[TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo)> | List of users who left co-broadcasting |

### OnUserConnectionRequest

Callback for received mic connection request

```
typedef OnUserConnectionRequest = void Function(TUIUserInfo inviterUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| inviterUser | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Mic-connecting user information |

### OnUserConnectionCancelled

Callback for received mic connection cancellation request

```
typedef OnUserConnectionCancelled = void Function(TUIUserInfo inviterUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| inviterUser | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Mic-connecting user information |

### OnUserConnectionAccepted

Callback for approved mic connection request

```
typedef OnUserConnectionAccepted = void Function(TUIUserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Mic-connecting user information |

### OnUserConnectionRejected

Callback for rejected mic connection request

```
typedef OnUserConnectionRejected = void Function(TUIUserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Mic-connecting user information |

### OnUserConnectionTimeout

Callback for mic connection request timeout

```
typedef OnUserConnectionTimeout = void Function(TUIUserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Mic-connecting user information |

### OnUserConnectionTerminated

Callback for anchor disconnecting the audience mic connection

```
typedef OnUserConnectionRejected = void Function();
```

### OnUserConnectionExited

Callback for audience proactive disconnection of the connecting line

```
typedef OnUserConnectionExited = void Function(TUIUserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Mic-connecting user information |

### OnConnectedRoomsUpdated

Callback for changes in the cross-room connection room list

```
typedef OnConnectedRoomsUpdated = void Function(List<TUIConnectionUser> hostUserList);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| hostUserList | List<[TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce)> | Connected user list |

### OnCrossRoomConnectionRequest

Callback for received cross-room connection request

```
typedef OnCrossRoomConnectionRequest = void Function(TUIConnectionUser hostUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| hostUser | [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connected user |

### OnCrossRoomConnectionCancelled

Callback for received cancellation of cross-room connection request

```
typedef OnCrossRoomConnectionCancelled = void Function(TUIConnectionUser hostUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| hostUser | [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connected user |

### OnCrossRoomConnectionAccepted

Callback for received consent to cross-room connection

```
typedef OnCrossRoomConnectionAccepted = void Function(TUIConnectionUser hostUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| hostUser | [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connected user |

### OnCrossRoomConnectionRejected

Callback for received deny of cross-room connection

```
typedef OnCrossRoomConnectionRejected = void Function(TUIConnectionUser hostUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| hostUser | [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connected user |

### OnCrossRoomConnectionTimeout

Callback for received cross-room connection timeout

```
typedef OnCrossRoomConnectionTimeout = void Function(    TUIConnectionUser inviter,     TUIConnectionUser invitee);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| inviter | [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connecting line request initiator |
| invitee | [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connection invitation recipient |

### OnCrossRoomConnectionExited

Callback for received cross-room disconnection

```
typedef OnCrossRoomConnectionExited = void Function(TUIConnectionUser hostUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| hostUser | [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connected user |

### OnBattleStarted

Callback for received PK start

```
typedef OnBattleStarted = void Function(TUIBattleInfo battleInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleInfo | [TUIBattleInfo](https://www.tencentcloud.com/document/product/647/69266#6b40e91c64a0a1ddbc355f14e0882d07) | PK info |

### OnBattleEnded

Callback for received PK end

```
typedef OnBattleEnded = void Function(TUIBattleInfo battleInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleInfo | [TUIBattleInfo](https://www.tencentcloud.com/document/product/647/69266#6b40e91c64a0a1ddbc355f14e0882d07) | PK info |

### OnUserJoinBattle

Callback for received participant join PK end

```
typedef OnUserJoinBattle = void Function(    String battleId,     TUIBattleUser battleUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| battleUser | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK user |

### OnUserExitBattle

Callback for received participant leave PK end

```
typedef OnUserExitBattle = void Function(    String battleId,     TUIBattleUser battleUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| battleUser | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK user |

### OnBattleScoreChanged

Callback for received PK score change

```
typedef OnBattleScoreChanged = void Function(    String battleId,     List<TUIBattleUser> battleUserList);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| battleUserList | List<[TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5)> | PK list of users |

### OnBattleRequestReceived

Callback for received battle request

```
typedef OnBattleRequestReceived = void Function(    String battleId,     TUIBattleUser inviter,     TUIBattleUser invitee);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| inviter | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invite initiator |
| invitee | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invitee |

### OnBattleRequestCancelled

Received cancellation of battle request

```
typedef OnBattleRequestCancelled = void Function(    String battleId,     TUIBattleUser inviter,     TUIBattleUser invitee);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| inviter | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invite initiator |
| invitee | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invitee |

### OnBattleRequestTimeout

Callback for received PK request timeout

```
typedef OnBattleRequestTimeout = void Function(    String battleId,     TUIBattleUser inviter,     TUIBattleUser invitee);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| inviter | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invite initiator |
| invitee | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invitee |

### OnBattleRequestAccept

Received callback for battle request approval

```
typedef OnBattleRequestAccept = void Function(    String battleId,     TUIBattleUser inviter,    TUIBattleUser invitee);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| inviter | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invite initiator |
| invitee | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invitee |

### OnBattleRequestReject

Callback for received reject PK request

```
typedef OnBattleRequestReject = void Function(    String battleId,     TUIBattleUser inviter,     TUIBattleUser invitee);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| battleId | String | PK unique identifier |
| inviter | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invite initiator |
| invitee | [TUIBattleUser](https://www.tencentcloud.com/document/product/647/69266#e079d942f7b568a2a1d6eaef6a3a31b5) | PK invitee |

### OnRoomDismissed

Callback for received room termination

```
typedef OnRoomDismissed = void Function(String roomId);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room Id |

## ConnectionObserver Event Definition

| Event list | Type | Description |
| --- | --- | --- |
| onConnectedUsersUpdated | [OnConnectedUsersUpdated](https://www.tencentcloud.com/document/product/647/71717#92c1c3a0-a443-409f-8387-d9a919bc126a) | Callback for changes in the list of users in mic-connection |
| onUserConnectionRequest | [OnUserConnectionRequest](https://www.tencentcloud.com/document/product/647/71717#27bbd67b-3219-4eab-bc33-6cfe2fbf22d8) | Callback for received mic connection request |
| onUserConnectionCancelled | [OnUserConnectionCancelled](https://www.tencentcloud.com/document/product/647/71717#599f86a6-6279-4661-a354-d1ddc048e29e) | Callback for received mic connection cancellation request |
| onUserConnectionAccepted | [OnUserConnectionAccepted](https://www.tencentcloud.com/document/product/647/71717#9b5cc9e7-e550-40cb-8813-e0adca8b52bd) | Callback for approved mic connection request |
| onUserConnectionRejected | [OnUserConnectionRejected](https://www.tencentcloud.com/document/product/647/71717#54471d34-a295-4a2a-aa00-f6c3c5d11097) | Callback for rejected mic connection request |
| onUserConnectionTimeout | [OnUserConnectionTimeout](https://www.tencentcloud.com/document/product/647/71717#851ba2a3-31ef-4bea-92d0-552368ca32c4) | Callback for mic connection request timeout |
| onUserConnectionTerminated | [OnUserConnectionTerminated](https://www.tencentcloud.com/document/product/647/71717#54471d34-a295-4a2a-aa00-f6c3c5d11097) | Callback for anchor disconnecting the audience mic connection |
| onUserConnectionExited | [OnUserConnectionExited](https://www.tencentcloud.com/document/product/647/71717#79e4d128-82a8-4bd4-9b64-aedb26b2ea57) | Callback for audience proactive disconnection of the connecting line |
| onConnectedRoomsUpdated | [OnConnectedRoomsUpdated](https://www.tencentcloud.com/document/product/647/71717#d78f13c7-6557-4d24-8dfe-9d1e36a1d17c) | Callback for changes in the cross-room connection room list |
| onCrossRoomConnectionRequest | [OnCrossRoomConnectionRequest](https://www.tencentcloud.com/document/product/647/71717#7a392403-d3be-4428-a77d-31cc07f73ffe) | Callback for received cross-room connection request |
| onCrossRoomConnectionCancelled | [OnCrossRoomConnectionCancelled](https://www.tencentcloud.com/document/product/647/71717#0164d32d-6a49-4496-8936-e7fe81c069c6) | Callback for received cancellation of cross-room connection request |
| onCrossRoomConnectionAccepted | [OnCrossRoomConnectionAccepted](https://www.tencentcloud.com/document/product/647/71717#6fc2fd8a-df82-4f5e-ad65-609323b2a60b) | Callback for received consent to cross-room connection |
| onCrossRoomConnectionRejected | [OnCrossRoomConnectionRejected](https://www.tencentcloud.com/document/product/647/71717#25bdeb8d-af4d-412b-8e34-cad7837a52d4) | Callback for received deny of cross-room connection |
| onCrossRoomConnectionTimeout | [OnCrossRoomConnectionTimeout](https://www.tencentcloud.com/document/product/647/71717#8d9a17f2-80df-4bfb-b038-01f989dcc328) | Callback for received cross-room connection timeout |
| onCrossRoomConnectionExited | [OnCrossRoomConnectionExited](https://www.tencentcloud.com/document/product/647/71717#ee1a8a6e-d66a-49c9-b2b2-c634ab68b034) | Callback for received cross-room disconnection |
| onRoomDismissed | [OnRoomDismissed](https://www.tencentcloud.com/document/product/647/71717#fc7dafdc-c27d-4768-9d81-1ac3ff48ee40) | Callback for received room termination |

## BattleEvent Definition for BattleObser>

| Event list | Type | Description |
| --- | --- | --- |
| onBattleStarted | [OnBattleStarted](https://www.tencentcloud.com/document/product/647/71717#96f38127-6750-4dfb-ac60-ff42cdfd2a51) | Callback for received PK start |
| onBattleEnded | [OnBattleEnded](https://www.tencentcloud.com/document/product/647/71717#1da99d71-00fc-4745-9b06-b8d87cfcf9c5) | Callback for received PK end |
| onUserJoinBattle | [OnUserJoinBattle](https://www.tencentcloud.com/document/product/647/71717#d35cc67e-0b73-4374-9772-e4eb938b1622) | Callback for received participant join PK end |
| onUserExitBattle | [OnUserExitBattle](https://www.tencentcloud.com/document/product/647/71717#9e88ed31-4c7c-4daf-8e04-5c7769740cfe) | Callback for received participant leave PK end |
| onBattleScoreChanged | [OnBattleScoreChanged](https://www.tencentcloud.com/document/product/647/71717#46d6b97c-accc-41a8-8450-ce96817fef17) | Callback for received PK score change |
| onBattleRequestReceived | [OnBattleRequestReceived](https://www.tencentcloud.com/document/product/647/71717#863b2120-dd82-452c-91ff-376dd49b6fc3) | Callback for received battle request |
| onBattleRequestCancelled | [OnBattleRequestCancelled](https://www.tencentcloud.com/document/product/647/71717#2cecedfe-013c-4a73-b1b2-d94dbd7e00c0) | Received cancellation of battle request |
| onBattleRequestTimeout | [OnBattleRequestTimeout](https://www.tencentcloud.com/document/product/647/71717#259bb7a6-e30d-4737-9621-7529b3563c1e) | Callback for received PK request timeout |
| onBattleRequestAccept | [OnBattleRequestAccept](https://www.tencentcloud.com/document/product/647/71717#a7b081c3-ed02-45c9-9951-258c78c9da92) | Received callback for battle request approval |
| onBattleRequestReject | [OnBattleRequestReject](https://www.tencentcloud.com/document/product/647/71717#8e6c5bd9-dbe3-4d89-b57f-c880df745a4f) | Callback for received reject PK request |


---
*Source: [https://trtc.io/document/71717](https://trtc.io/document/71717)*
