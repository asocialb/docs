# RoomKit API

Module:   TUIRoomKit

Function: Multi-person audio and video main function interface

Version: 2.1.0

**TUIRoomKit**

## TUIRoomKit

| function list | describe |
| --- | --- |
| [createInstance](https://www.tencentcloud.com/document/product/647/54865#2a6a582a44072feeed27e5ac25531025) | Create a TUIRoomKit instance (singleton mode). |
| [destroyInstance](https://www.tencentcloud.com/document/product/647/54865#a07b9445-798a-4128-95d8-5eec3893dd63) | Destroy the TUIRoomKit instance. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54865#9bd21648a95d07aa95e1b808cab6479b) | Set up personal information, including username and avatar. |
| [createRoom](https://www.tencentcloud.com/document/product/647/54865#6df5c9d6843d0aa619ef4e732b704cc4) | Create a room. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54865#1ba05215-2559-4df2-ba80-04de67a39f27) | Enter the room. |

## createInstance

Initialize the TUIRoomKit singleton object.

```
public static TUIRoomKit createInstance();
```

### destroyInstance

Destroy the TUIRoomKit instance.

```
public static void destroyInstance();
```

## setSelfInfo

Set up personal information, including username and avatar.

```
public abstract void setSelfInfo(String userName, String avatarURL,                                  TUIRoomDefine.ActionCallback callback);
```

| parameter | describe |
| --- | --- |
| userName | The individual's username. |
| avatarURL | Personal avatar link. |
| callback | Callback for success in setting personal information. |

## createRoom

Create a room.

```
public abstract void createRoom(TUIRoomDefine.RoomInfo roomInfo, TUIRoomDefine.ActionCallback callback);
```

| parameter | describe |
| --- | --- |
| roomInfo | Parameters for creating a room, including room number, room name, etc., where roomId is required and the rest can be default values. |
| callback | Callback to determine whether the room is successfully created. |

## enterRoom

Enter the room.

```
public abstract void enterRoom(String roomId,                                boolean enableAudio,                                boolean enableVideo,                                boolean isSoundOnSpeaker,
                               TUIRoomDefine.GetRoomInfoCallback callback);
```

| parameter | describe |
| --- | --- |
| roomId | Room number to enter the room. |
| enableAudio | true: When entering the room, turn on the microphone and push local audio data to the remote end. Other members can hear the local sound normally;false: When entering the room, only the microphone is turned on and local audio data is not pushed to the remote end. Other members cannot hear the local sound. |
| enableVideo | true: Enter the room, turn on the camera, and push the local video data to the remote end. Other members can see the local picture normally;false: When entering the room, the camera will not be turned on and local video data will not be pushed to the remote end. Other members will not be able to see the local video. |
| isSoundOnSpeaker | Whether to use the speaker to play sound, true to use the speaker, false to use the earpiece. |
| callback | Callback whether the room entry is successful. |


---
*Source: [https://trtc.io/document/54865](https://trtc.io/document/54865)*
