# LiveCoreView

## API Overview

LiveCoreView is a fundamental control developed for our video live streaming UIKit. This core control provides rich APIs such as preview before broadcasting, start video live streaming, stop video live streaming, live streaming room connection with audience, and cross-room connection with other anchors.

## API Overview

| API | Description |
| --- | --- |
| [LiveCoreView](https://www.tencentcloud.com/document/product/647/66145#d147f174-e55a-4ba2-bbaf-2792c9419650) | Create LiveCoreView object, supporting both code creation and XML loading methods. |
| [startCamera](https://www.tencentcloud.com/document/product/647/66145#c6f79ba4-2dc1-4d65-82b3-e52d3ef28f2f) | Start camera capture and display the captured video on LiveCoreView. |
| [startMicrophone](https://www.tencentcloud.com/document/product/647/66145#1032095a-ba39-4820-aac9-6399f497ec6d) | Turn on the local microphone |
| [muteMicrophone](https://www.tencentcloud.com/document/product/647/66145#b866f4a7-1951-41b8-8629-dd613a030fd5) | Pause publishing local audio stream? |
| [stopCamera](https://www.tencentcloud.com/document/product/647/66145#61a3e2e3-2780-4f16-bdc4-9fae002c48e5) | Turns the local camera off |
| [stopMicrophone](https://www.tencentcloud.com/document/product/647/66145#c739e487-b83b-4a78-b432-3f84d867ffa2) | Turn off the local microphone |
| [startLiveStream](https://www.tencentcloud.com/document/product/647/66145#fa10462e-e188-4879-9be5-2c2d6a222b6d) | Anchor creates a live streaming room and starts streaming |
| [stopLiveStream](https://www.tencentcloud.com/document/product/647/66145#89f1f933-1771-4f4e-81af-5e0d38dce48e) | Anchor stops streaming and destroys the live room |
| [joinLiveStream](https://www.tencentcloud.com/document/product/647/66145#8c23ef17-5f8a-4ddd-b803-f78bd3a18f17) | Audience member joins an anchor's live streaming room |
| [leaveLiveStream](https://www.tencentcloud.com/document/product/647/66145#cdba89b2-1d72-4603-9077-c97d158e2fef) | Audience member leaves an anchor's live streaming room |
| [requestIntraRoomConnection](https://www.tencentcloud.com/document/product/647/66145#db8d3b1f-26b4-4e79-896a-dc00cc32caac) | Audience member requests to connect with the anchor |
| [cancelIntraRoomConnection](https://www.tencentcloud.com/document/product/647/66145#dedaef30-7e34-4d1d-87d3-7cad0c60a2d6) | Audience member cancels the request to connect with the anchor |
| [respondIntraRoomConnection](https://www.tencentcloud.com/document/product/647/66145#00371c4a-dda3-4035-8bd2-318591fa7d0f) | Anchor responds to the audience member's request for connection |
| [disconnectUser](https://www.tencentcloud.com/document/product/647/66145#c771b29e-ad6c-4cc6-beb6-10a0e2206b11) | Anchor disconnects the connected audience member |
| [terminateIntraRoomConnection](https://www.tencentcloud.com/document/product/647/66145#e8cad683-cd01-44ec-bf4b-4ce647f138fd) | Audience member stops the connection with the anchor themselves |
| [requestCrossRoomConnection](https://www.tencentcloud.com/document/product/647/66145#fa324f97-fad6-45ac-ba1b-a85032038645) | Anchor requests to connect with another anchor in a different live room |
| [cancelCrossRoomConnection](https://www.tencentcloud.com/document/product/647/66145#ff06ff0c-cd0f-4cc2-9491-e228c98eb569) | Anchor cancels the request to connect with another anchor in a different live room |
| [respondToCrossRoomConnection](https://www.tencentcloud.com/document/product/647/66145#95b1d9e0-7929-4029-b55c-c914ab70bb18) | Anchor responds to the connection request |
| [terminateCrossRoomConnection](https://www.tencentcloud.com/document/product/647/66145#5630e92d-5e13-4c2b-b588-3d684046e828) | Anchor disconnects the connection |
| [registerConnectionObserver](https://www.tencentcloud.com/document/product/647/66145#bc6933f2-783a-4059-8164-d4566dbebe06) | Register a connection event callback |
| [unregisterConnectionObserver](https://www.tencentcloud.com/document/product/647/66145#b0de0bf4-56d2-4b8d-baa3-165e2dab8a3c) | Unregister a connection event callback |
| [setLayoutMode](https://www.tencentcloud.com/document/product/647/66145#c69ad7f9-71ab-4b3b-8529-8e1a10abebd1) | Set the layout mode of the connected broadcaster's video screen |
| [setVideoViewAdapter](https://www.tencentcloud.com/document/product/647/66145#58713969-f561-4dd1-aa5d-f188888358dd) | Set a view adapter for adding widgets to the broadcaster's video screen |

## API Details

### LiveCoreView

Create an instance of the LiveCoreView object. Supports both code creation and XML loading methods.

```
public LiveCoreView(Context context)
```

**Parameters:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| context | Context | Android context object |

**Return value: LiveCoreView**

### startCamera

Start camera capture and display the captured video on the LiveCoreView view.

```
public void startCamera(boolean useFrontCamera, ActionCallback callback)
```

**Parameters:**

| Parameters | Type | Meaning |
| --- | --- | --- |
| useFrontCamera | boolean | true: use front camera, false: use rear camera |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### startMicrophone

Enable the local microphone.

```
void startMicrophone(ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### muteMicrophone

Pause publishing the local audio stream.

```
void muteMicrophone(boolean mute)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| mute | boolean | true: Pause video stream publishing, false: Normal video stream publishing |

**Returned value:**void

### stopCamera

Turns the local camera off.

```
void stopCamera()
```

**Parameters:**

**Returned value:**void

### stopMicrophone

Turn off the local microphone.

```
void stopMicrophone()
```

**Parameters:**

**Returned value:**void

### startLiveStream

Anchor creates a live streaming room and starts streaming.

```
void startLiveStream(RoomInfo roomInfo, GetRoomInfoCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomInfo | RoomInfo | Create live room information |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### stopLiveStream

Anchor stops streaming and destroys the live room.

```
void stopLiveStream(ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### joinLiveStream

Audience member joins an anchor's live streaming room.

```
void joinLiveStream(String roomId, GetRoomInfoCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | Live room ID |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### leaveLiveStream

Audience member leaves an anchor's live streaming room.

```
void leaveLiveStream(ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### requestIntraRoomConnection

Audience member requests to connect with the anchor.

```
void requestIntraRoomConnection(String userId, int timeout, boolean openCamera, ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID. If left blank, it represents the anchor's user ID. |
| timeout | int | Request timeout duration, unit: seconds. |
| openCamera | boolean | Whether to turn on the camera after a successful mic connection. true: video mic connect, false: voice mic connect. |
| callback | ActionCallback | Callback of operations. |

**Returned value:**void

### cancelIntraRoomConnection

Audience member cancels the request to connect with the anchor.

```
void cancelIntraRoomConnection(String userId, ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID of the user who cancels the mic connection. If left blank, it represents the anchor's user ID. |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### respondIntraRoomConnection

The anchor responds to the audience's request for connection.

```
void respondIntraRoomConnection(String userId, boolean isAccepted, ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | Responding user's User ID |
| isAccepted | isAccepted | Whether to accept the mic connection request. true: accept the mic connection request, false: reject the mic connection request |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### disconnectUser

The anchor disconnects the connected audience member.

```
void disconnectUser(String userId, ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| userId | String | The anchor needs to disconnect the co-anchoring user's ID |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### terminateIntraRoomConnection

The audience member stops the connection with the anchor themselves.

```
void terminateIntraRoomConnection()
```

**Parameters: None**

**Returned value:**void

### requestCrossRoomConnection

Anchor requests to connect with another anchor in a different live room.

```
void requestCrossRoomConnection(String roomId, int timeout, ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | Room ID of the cross-room connection request. |
| timeout | int | Request timeout duration, unit: seconds. |
| callback | ActionCallback | Callback of operations. |

**Returned value:**void

### cancelCrossRoomConnection

Anchor cancels the request to connect with another anchor in a different live room.

```
void cancelCrossRoomConnection(String roomId, ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | Room ID to cancel the connection |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### respondToCrossRoomConnection

The anchor responds to the connection request.

```
void respondToCrossRoomConnection(String roomId, boolean isAccepted, ActionCallback callback)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| roomId | String | Room ID for the response to the connection |
| isAccepted | boolean | Whether to agree to the connection, true: agree to the connection, false: reject the connection |
| callback | ActionCallback | Callback of the operation |

**Returned value:**void

### terminateCrossRoomConnection

The anchor disconnects the connection.

```
void terminateCrossRoomConnection()
```

**Parameters: None**

**Returned value:**void

### registerConnectionObserver

Register a connection event callback.

```
void registerConnectionObserver(ConnectionObserver observer)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| observer | [ConnectionObserver](https://www.tencentcloud.com/document/product/647/66145#d8860caf-d045-431b-becc-d4f8b4e152b1) | Callback object for connection events |

**Returned value:**void

### unregisterConnectionObserver

Unregister a connection event callback.

```
void unregisterConnectionObserver(ConnectionObserver observer)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| observer | [ConnectionObserver](https://www.tencentcloud.com/document/product/647/66145#d8860caf-d045-431b-becc-d4f8b4e152b1) | Callback object for connection events |

**Returned value:**void

### setLayoutMode

Set the layout mode of the connected broadcaster's video screen.

```
void setLayoutMode(LayoutMode layoutModel, String layoutJson)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| layoutModel | [LayoutMode](https://www.tencentcloud.com/document/product/647/66145#9054f6cd-8773-447d-9139-3a65d2e9a42f) | Layout mode during connection, supporting grid layout, floating window layout, and custom layout. |
| layoutJson | String | Layout JSON string |

**Returned value:**void

### setVideoViewAdapter

Set a view adapter for adding widgets to the broadcaster's video screen.

```
void setVideoViewAdapter(LiveCoreViewDefine.VideoViewAdapter viewAdapter)
```

**Parameters:**

| Parameter | Type | Meaning |
| --- | --- | --- |
| viewAdapter | [VideoViewAdapter](https://www.tencentcloud.com/document/product/647/66145#43c7b85d-9c84-4111-a3a3-b2c2e3271e17) | View adapter for adding widgets to the broadcaster's video screen |

**Returned value:**void

## Type Definition

| Type | Description |
| --- | --- |
| [ConnectionObserver](https://www.tencentcloud.com/document/product/647/66145#d8860caf-d045-431b-becc-d4f8b4e152b1) | Set callback events for core control connections. |
| [LayoutMode](https://www.tencentcloud.com/document/product/647/66145#9054f6cd-8773-447d-9139-3a65d2e9a42f) | Layout mode during connection, supporting grid layout, floating window layout, and custom layout. |
| [VideoViewAdapter](https://www.tencentcloud.com/document/product/647/66145#43c7b85d-9c84-4111-a3a3-b2c2e3271e17) | Connection view adapter interface, which allows you to add widgets to each audio and video stream view by implementing this interface. |

### ConnectionObserver

| Type | Description |
| --- | --- |
| [onConnectedUsersUpdated](https://www.tencentcloud.com/document/product/647/66145#698b164e-c775-48f1-88b7-85ea8c18e94c) | Callback for changes in the list of connected users. |
| [onUserConnectionRequest](https://www.tencentcloud.com/document/product/647/66145#485a04e9-742d-4cbb-901d-cf1018cc71e5) | Callback for receiving a connection request. |
| [onUserConnectionCancelled](https://www.tencentcloud.com/document/product/647/66145#2b9086aa-a2d0-4cad-962e-b35e6e29dc95) | Callback for receiving a request to cancel the connection. |
| [onUserConnectionAccepted](https://www.tencentcloud.com/document/product/647/66145#51b2b526-d288-48b4-96bb-abb28bf03186) | Callback for connection request approval. |
| [onUserConnectionRejected](https://www.tencentcloud.com/document/product/647/66145#8f985ad2-a119-49d1-b66d-a775730a04bf) | Callback for connection request rejection. |
| [onUserConnectionTimeout](https://www.tencentcloud.com/document/product/647/66145#0619d6ab-e8d0-4594-89a3-4c58b6a63659) | Callback for connection request timeout. |
| [onUserConnectionTerminated](https://www.tencentcloud.com/document/product/647/66145#c97e43b0-87e5-4cb1-8256-cb27613f1616) | Callback for the host disconnecting the mic connection with this viewer. |
| [onUserConnectionExited](https://www.tencentcloud.com/document/product/647/66145#844be3c0-8638-4dce-aed6-01786eb8ab5d) | Callback for the viewer actively disconnecting. |
| [onConnectedRoomsUpdated](https://www.tencentcloud.com/document/product/647/66145#4c10617c-5a25-4e81-8d19-06608d28d82b) | Callback for changes in the cross-room connection room list. |
| [onCrossRoomConnectionRequest](https://www.tencentcloud.com/document/product/647/66145#2a1ef273-7b94-4cdf-b263-84bd0072914b) | Callback for receiving a cross-room connection request. |
| [onCrossRoomConnectionCancelled](https://www.tencentcloud.com/document/product/647/66145#e8e761fe-e391-4987-a90a-a1eeff2ea04c) | Callback for receiving a request to cancel the cross-room connection. |
| [onCrossRoomConnectionAccepted](https://www.tencentcloud.com/document/product/647/66145#10bfc883-124d-4cff-8f8f-2ac231c12b2a) | Received callback for consent to cross-room connection |
| [onCrossRoomConnectionRejected](https://www.tencentcloud.com/document/product/647/66145#185047be-2bde-42aa-ac94-50b6ce3d4243) | Received callback for cross-room connection rejection |
| [onCrossRoomConnectionTimeout](https://www.tencentcloud.com/document/product/647/66145#de5d609d-132a-4bb0-b73f-c93906a9035a) | Received callback for cross-room connection timeout. |
| [onCrossRoomConnectionExited](https://www.tencentcloud.com/document/product/647/66145#b8ab1647-b00e-4b9d-ac70-d069257a1c3f) | Received callback for cross-room disconnection. |
| [onRoomDismissed](https://www.tencentcloud.com/document/product/647/66145#8aa11fb4-f463-4aa7-a581-f67239f57757) | Received callback for room termination. |

### LayoutMode

Layout mode during connection

| Type | Description |
| --- | --- |
| GRID_LAYOUT | Grid Layout. |
| FLOAT_LAYOUT | Floating Window Layout. |
| FREE_LAYOUT | Custom Layout. |

### VideoViewAdapter

Connection view adapter interface, which allows you to add widgets to each audio and video stream view by implementing this interface.

| API | Description |
| --- | --- |
| [createCoGuestView](https://www.tencentcloud.com/document/product/647/66145#47d95d62-30bd-498f-b28d-1374aa6bc1aa) | Callback when creating a connected audience view. The View created through this API will be displayed on the connected audience's view. |
| [updateCoGuestView](https://www.tencentcloud.com/document/product/647/66145#23b3931d-345f-4193-82ed-f9ff8c9890cf) | Callback when updating the connected audience view. |
| [createCoHostView](https://www.tencentcloud.com/document/product/647/66145#a4508d98-522b-4cc6-83f3-e1d2e2ee8bda) | Callback when creating a connected host view, the View created through this API will be displayed on the connected host's view. |
| [updateCoHostView](https://www.tencentcloud.com/document/product/647/66145#283e2cca-68b0-48b4-92f6-cc15b40db7f2) | Callback when updating the connected host view. |

## Callback Event Details

### onConnectedUsersUpdated

Callback for changes in the list of connected users.

```
void onConnectedUsersUpdated(List<UserInfo> userList, List<UserInfo> joinList, List<UserInfo> leaveList);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userList | List<UserInfo> | List of connected users |
| joinList | List<UserInfo> | Newly connected users |
| leaveList | List<UserInfo> | Users who have left the connection |

**Returned value:**void

### onUserConnectionRequest

Callback for receiving a connection request.

```
void onUserConnectionRequest(UserInfo inviterUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| inviterUser | UserInfo | Information of the user applying for connection |

**Returned value:**void

### onUserConnectionCancelled

Callback for receiving a request to cancel the connection.

```
void onUserConnectionCancelled(UserInfo inviterUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| inviterUser | UserInfo | Information of the user canceling the connection |

**Returned value:**void

### onUserConnectionAccepted

Callback for connection request approval.

```
void onUserConnectionAccepted(UserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | Information of users who agreed to the mic connection |

**Returned value:**void

### onUserConnectionRejected

Callback for connection request rejection.

```
void onUserConnectionRejected(UserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | Information of users who rejected the mic connection |

**Returned value:**void

### onUserConnectionTimeout

Callback for connection request timeout.

```
void onUserConnectionTimeout(UserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | Information of users whose mic connection request timed out |

**Returned value:**void

### onUserConnectionTerminated

Callback for the host disconnecting the mic connection with this viewer.

```
vvoid onUserConnectionTerminated();
```

**Parameter: None**

**Returned value:**void

### onUserConnectionExited

Callback for disconnecting a connected user.

```
void onUserConnectionExited(UserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | User information |

**Returned value:**void

### onConnectedRoomsUpdated

Callback for changes in the connected room list.

```
void onConnectedRoomsUpdated(List<RoomInfo> roomList);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomList | List<RoomInfo> | Room list |

**Returned value:**void

### onCrossRoomConnectionRequest

Callback for receiving a cross-room connection request.

```
void onCrossRoomConnectionRequest(RoomInfo roomInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomInfo | RoomInfo | Information of the live room applying for connection |

**Returned value:**void

### onCrossRoomConnectionCancelled

Callback for receiving a request to cancel the cross-room connection.

```
void onCrossRoomConnectionCancelled(RoomInfo roomInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomInfo | RoomInfo | Information of the live room cancelling the connection application |

**Returned value:**void

### onCrossRoomConnectionAccepted

Callback for receiving the cross-room connection approval.

```
void onCrossRoomConnectionAccepted(RoomInfo roomInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomInfo | RoomInfo | Information of the live room agreeing to the connection |

**Returned value:**void

### onCrossRoomConnectionRejected

Callback for receiving the cross-room connection rejection.

```
void onCrossRoomConnectionRejected(RoomInfo roomInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomInfo | RoomInfo | Information of the live room rejecting the connection |

**Returned value:**void

### onCrossRoomConnectionTimeout

Received callback for room connection request timeout.

```
void onCrossRoomConnectionTimeout(RoomInfo inviter, RoomInfo invitee);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| inviter | RoomInfo | Information of the live room applying for connection |
| invitee | RoomInfo | Information of the live room invited for connection |

**Returned value:**void

### onCrossRoomConnectionExited

Callback for changes in the list of connected users.

```
void onCrossRoomConnectionExited(RoomInfo roomInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomInfo | RoomInfo | Information of the live room exiting the connection |

**Returned value:**void

### onRoomDismissed

Received callback for live room termination.

```
void onRoomDismissed(String roomId);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |

**Returned value:**void

### createCoGuestView

Create an overlay view for audience mic connection. This view will be added to the user's video stream.

```
View createCoGuestView(TUIRoomDefine.UserInfo userInfo);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | Information of the user connected to the mic |

**Returned value: View**

### updateCoGuestView

Callback for updating the overlay view. Generally, you donât need to concern yourself with this callback; you can update your overlay view according to the state of your overlay data, unless your overlay depends on the change in userInfo.

```
void updateCoGuestView(TUIRoomDefine.UserInfo userInfo, View coGuestView);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| userInfo | UserInfo | Information of the user connected to the mic |
| coGuestView | View | The widget view created by you through the [createCoGuestView](https://www.tencentcloud.com/document/product/647/66145#47d95d62-30bd-498f-b28d-1374aa6bc1aa) API |

**Returned value:**void

### createCoHostView

Create the widget view for the connected host, which will be added to the video stream of the connected host.

```
View createCoHostView(TUILiveConnectionManager.ConnectionUser connectionUser);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| connectionUser | ConnectionUser | Information of the connected host |

**Returned value: View**

### updateCoHostView

Callback for updating the widget view. Generally, you do not need to worry about this callback. You can update the widget view you set based on the status of your own widget data, unless your widget relies on changes in connectionUser.

```
void updateCoHostView(TUILiveConnectionManager.ConnectionUser connectionUser, View coHostView);
```

**Parameters:**

| Parameter | Type | Description |
| --- | --- | --- |
| connectionUser | ConnectionUser | Information of the connected host |
| coHostView | View | The widget view created by you through the [createCoHostView](https://www.tencentcloud.com/document/product/647/66145#a4508d98-522b-4cc6-83f3-e1d2e2ee8bda) API |

**Returned value:**void


---
*Source: [https://trtc.io/document/66145](https://trtc.io/document/66145)*
