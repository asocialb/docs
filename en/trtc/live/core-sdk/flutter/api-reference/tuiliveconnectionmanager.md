# TUILiveConnectionManager

Copyright (c) 2024 Tencent. All rights reserved.

Module:   TUILiveConnectionManager @ TUIKitEngine

Functions: Relevant APIs for Live Connection. The functions on this page are only supported for live room type ([TUIRoomTypeLive](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

**TUILiveConnectionManager**

## TUILiveConnectionObserver

| Function List | Description |
| --- | --- |
| [onConnectionUserListChanged](https://www.tencentcloud.com/document/product/647/69265#7be00604bd4d27805a839b743954a95c) | Received that the connected user list has changed. |
| [onConnectionRequestReceived](https://www.tencentcloud.com/document/product/647/69265#1b2ccc6866435842e1ef670ad196739f) | Callback that the recipient receives the connection invitation |
| [onConnectionRequestCancelled](https://www.tencentcloud.com/document/product/647/69265#703c0713cd90cb0fa60f2ddc91ce7555) | Invitation cancellation callback |
| [onConnectionRequestAccept](https://www.tencentcloud.com/document/product/647/69265#c99794669422490e9e678a12455f6ee9) | Invitation accepted callback |
| [onConnectionRequestReject](https://www.tencentcloud.com/document/product/647/69265#70326770790d9053e5eb46ed3b3d797a) | Invitation rejected callback |
| [onConnectionRequestTimeout](https://www.tencentcloud.com/document/product/647/69265#ad2ca9383794b28927e2ed7d46d56c2e) | Invitation timeout callback |

## TUILiveConnectionManager

| Function List | Description |
| --- | --- |
| [addObserver](https://www.tencentcloud.com/document/product/647/69265#0d177d4d2cc08cb4127697f20321d2b1) | Add event callback |
| [removeObserver](https://www.tencentcloud.com/document/product/647/69265#e327b25415e3471f7989f04d3660833f) | Remove event callback |
| [requestConnection](https://www.tencentcloud.com/document/product/647/69265#21dada6328cc57d6ace44a695445f85c) | Initiate a connection request |
| [cancelConnectionRequest](https://www.tencentcloud.com/document/product/647/69265#cba46056186507a80a12a048324a378b) | Cancel a connection request |
| [acceptConnection](https://www.tencentcloud.com/document/product/647/69265#2f98de3bbbf0d38fc9360c1b6046444c) | Accept a connection invitation |
| [rejectConnection](https://www.tencentcloud.com/document/product/647/69265#c34f51562701b317ca5bddc81e09c035) | Reject a connection invitation |
| [disconnect](https://www.tencentcloud.com/document/product/647/69265#ca0b949411f91ee15345ee889c08f8c9) | Leave the room connecting line |

## Structure Data Type

| Function List | Description |
| --- | --- |
| [TUIConnectionUser](https://www.tencentcloud.com/document/product/647/69265#ce98cb6cc271975f063e0469f66ffcce) | Connected User Information |
| [TUIConnectionRequestResult](https://www.tencentcloud.com/document/product/647/69265#4140d6d8-4c42-454e-9236-379c72421e1c) | Connection request result |

## Enumeration Types

| Enumeration Types | Description |
| --- | --- |
| [TUIConnectionCode](https://www.tencentcloud.com/document/product/647/69265#92daac9cd74ffae905ec2f0dbd85a61e) | Connection invitation status |

## onConnectionUserListChanged

**Received that the connected user list has changed.**

```
  OnConnectionUserListChanged onConnectionUserListChanged =         (List<TUIConnectionUser> connectedList,          List<TUIConnectionUser> joinedList,          List<TUIConnectionUser> leavedList) {};
```

| Parameter | Description |
| --- | --- |
| connectedList | List of connected users. |
| joinedList | List of newly joined users. |
| leavedList | List of users who have exited the connection. |

## onConnectionRequestReceived

**Callback that the recipient receives the connection invitation**

```
OnConnectionRequestReceived onConnectionRequestReceived =         (TUIConnectionUser inviter,           List<TUIConnectionUser> inviteeList,          String extensionInfo) {};
```

| Parameter | Description |
| --- | --- |
| inviter | Inviter information. |
| inviteeList | List of invited users for connection. |
| extensionInfo | Transparent transmission of information. |

## onConnectionRequestCancelled

**Invitation cancellation callback**

```
OnConnectionRequestCancelled onConnectionRequestCancelled =      (TUIConnectionUser inviter) {};
```

| Parameter | Description |
| --- | --- |
| inviter | Inviter information. |

## onConnectionRequestAccept

**Invitation accepted callback**

```
OnConnectionRequestAccept onConnectionRequestAccept =      (TUIConnectionUser invitee) {};
```

| Parameter | Description |
| --- | --- |
| invitee | Invitee user information. |

## onConnectionRequestReject

**Invitation rejected callback**

```
  OnConnectionRequestReject onConnectionRequestReject =      (TUIConnectionUser invitee) {};
```

| Parameter | Description |
| --- | --- |
| invitee | Invitee user information. |

## onConnectionRequestTimeout

**Invitation timeout callback**

```
OnConnectionRequestTimeout onConnectionRequestTimeout =      (TUIConnectionUser inviter,       TUIConnectionUser invitee) {};
```

| Parameter | Description |
| --- | --- |
| inviter | Inviter information. |
| invitee | Invitee user information. |

## addObserver

**Add event callback**

```
void addObserver(TUILiveConnectionObserver observer);
```

| Parameter | Description |
| --- | --- |
| observer | Instances being listened to. |

## removeObserver

**Remove event callback**

```
 void removeObserver(TUILiveConnectionObserver observer);
```

| Parameter | Description |
| --- | --- |
| observer | Instances being listened to. |

## requestConnection

**Initiate a connection request**

```
Future<TUIValueCallBack<TUIConnectionRequestResult>> requestConnection      (List<String> roomIdList,       int timeout,        String extensionInfo);
```

| Parameter | Description |
| --- | --- |
| roomIdList | List of room IDs to be invited for connection. |
| timeout | Timeout Time |
| extensionInfo | Extended information. |

## cancelConnectionRequest

**Cancel a connection request**

```
Future<TUIActionCallback> cancelConnectionRequest(List<String> roomIdList);
```

| Parameter | Description |
| --- | --- |
| roomIdList | List of room IDs for which the connection request has been canceled. |

## acceptConnection

**Accept a connection invitation**

```
Future<TUIActionCallback> acceptConnection(String roomId);
```

| Parameter | Description |
| --- | --- |
| roomId | room ID. |

## rejectConnection

**Reject a connection invitation**

```
Future<TUIActionCallback> rejectConnection(String roomId);
```

| Parameter | Description |
| --- | --- |
| roomId | room ID. |

## disconnect

**Leave the room connecting line**

```
 Future<TUIActionCallback> disconnect();
```

> **Note:**Calling this API will exit the room connecting line status. It can only be called in the connected status.

## TUIConnectionUser

**Connected User Information**

| Enumeration Types | Description |
| --- | --- |
| roomId | Connecting room id. |
| userId | id of the connected user. |
| userName | User nickname of the connected user. |
| avatarUrl | User Avatar Address of the connected user. |
| joinConnectionTime | Mark the timestamp when the connection starts. |

## TUIConnectionRequestResult

| Enumeration Types | Description |
| --- | --- |
| requestMap | Connection request result Map |

## TUIConnectionCode

**Connection invitation status**

| Error Example | Value | Description |
| --- | --- | --- |
| unknown | -1 | Default status. |
| success | 0 | Connection request sent successfully. |
| roomNotExists | 1 | The room for the connection invitation does not exist. |
| connecting | 2 | The room invited for connection is already in the invitation list or has been connected. |
| connectingOtherRoom | 3 | The invited room is connecting with other rooms. |
| connetionFull | 4 | The current number of connections has reached the maximum limit. |
| retry | 5 | Internal error, recommend retry once. |


---
*Source: [https://trtc.io/document/69265](https://trtc.io/document/69265)*
