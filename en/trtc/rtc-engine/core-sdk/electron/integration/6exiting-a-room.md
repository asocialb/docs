# 6.Exiting a Room

This document describes how to actively exit the current TRTC room and in which cases will a user be forced to exit a room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/50a4185337fb11ed8088525400463ef7.png)

## Call Guide

### Step 1. Perform prerequisite steps

2. Implement the room entry process as instructed in Electron.

### Step 2. Actively exit the current room

```
import TRTCCloud from 'trtc-electron-sdk';const trtcCloud = new TRTCCloud();// Exit the current roomtrtcCloud.exitRoom();
```

After the `exitRoom` API is called, the SDK will enter the room exit process, where two key tasks need to be completed:

- **1. Notify the exit of the current user**
Notify other users in the room of the upcoming room exit, and they will receive the **onRemoteUserLeaveRoom** callback from the current user; otherwise, other users may think the current user's video image is simply frozen.
- **2. Revoke device permissions**
If the current user is publishing an audio/video stream before exiting the room, the user needs to turn off the camera and mic and release the device permissions during the room exit process.

Therefore, we recommend you release the `TRTCCloud` instance after receiving the `onExitRoom` callback.

### Step 3. Be forced to exit the current room

- **Case 1. A user is kicked out of the room**
You can use the [RemoveUser](https://intl.cloud.tencent.com/document/product/647/34268) or [RemoveUserByStrRoomId](https://intl.cloud.tencent.com/document/product/647/39630) API to kick a user out of a TRTC room. After being kicked out, the user will receive the `onExitRoom(1)` callback.
- **Case 2. The current room is closed**
You can call the [DismissRoom](https://intl.cloud.tencent.com/document/product/647/34269) or [DismissRoomByStrRoomId](https://intl.cloud.tencent.com/document/product/647/39631) API to close a TRTC room. After the room is closed, all users in the room will receive the `onExitRoom(2)` callback.

```
// Listen for the `onExitRoom` callback to get the reason for room exitfunction onExitRoom(reason) {  console.log(`onExitRoom reason: ${reason}`);}trtcCloud.on('onExitRoom', onExitRoom);
```


---
*Source: [https://trtc.io/document/47638](https://trtc.io/document/47638)*
