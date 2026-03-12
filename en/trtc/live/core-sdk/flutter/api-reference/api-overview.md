# API Overview

## Overview

TUIRoomEngine ([rtc_room_engine](https://pub.dev/packages/rtc_room_engine)) is a component designed for scenarios involving**corporate meetings, webinars, online education**, etc., supporting multi-person audio and video conversations. It offers room management, multi-person TRTC interactions, member management, screen sharing, and other meeting control features, and supports various video qualities including standard definition, high definition, and ultra-high definition. By integrating this component, you can add multi-person audio and video conversation features to your application.

### **Integration method:**

In your project's `pubspec.yaml`, add the following code to integrate TUIRoomEngine:

```
dependencies:       rtc_room_engine: latest version
```

Run the following command to install the component:

```
flutter pub get
```

## TUIRoomEngine API List

TUIRoomEngine API is a no UI interface for multi-person audio and video rooms, you can use these APIs to perform custom encapsulation based on your business needs.

TUIRoomEngine

### TUIRoomEngine Core Methods

| API | Description |
| --- | --- |
| [sharedInstance](https://www.tencentcloud.com/document/product/647/67263#sharedInstance) | Create TUIRoomEngine Instance. |
| [destroyISharedinstance](https://www.tencentcloud.com/document/product/647/67263#a3b428a8-fc46-4927-abcb-642cfed08e0f) | Destroy TUIRoomEngine Instance. |
| [login](https://www.tencentcloud.com/document/product/647/67263#login) | Login Interface, you need to initialize user information first to enter the room and perform a series of operations. |
| [logout](https://www.tencentcloud.com/document/product/647/67263#4955bdc1-5a79-4eb4-8f86-2fb73923bcb8) | Logout Interface, which includes proactively leaving the room and destroying resources. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/67263#setSelfInfo) | Set Local Username and Avatar. |
| [setLoginUserInfo](https://www.tencentcloud.com/document/product/647/67263#setLoginUserInfo) | Set Login User Information. |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/67263#getSelfInfo) | Obtain Basic Information of Local User Login. |
| [addObserver](https://www.tencentcloud.com/document/product/647/67263#addObserver) | Set event callbacks. |
| [removeObserver](https://www.tencentcloud.com/document/product/647/67263#removeObserver) | Remove event callbacks. |

### Room-related proactive interface

| API | Description |
| --- | --- |
| [createRoom](https://www.tencentcloud.com/document/product/647/67263#createRoom) | Create Room. |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/67263#destroyRoom) | Dissolve Room. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/67263#enterRoom) | Enter the room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/67263#exitRoom) | Leave the room. |
| [connectOtherRoom](https://www.tencentcloud.com/document/product/647/67263#connectOtherRoom) | Connect to Other Rooms. |
| [disconnectOtherRoom](https://www.tencentcloud.com/document/product/647/67263#disconnectOtherRoom) | Disconnect from Other Rooms. |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/67263#fetchRoomInfo) | Obtain room information. |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/67263#updateRoomNameByAdmin) | Update Room Name (only administrators or group owners can invoke). |
| [updateRoomSeatModeByAdmin](https://www.tencentcloud.com/document/product/647/67263#updateRoomSeatModeByAdmin) | Set Room Management Mode (only administrators or group owners can invoke). |

### Local User View Rendering, Video Management

| API | Description |
| --- | --- |
| [setLocalVideoView](https://www.tencentcloud.com/document/product/647/67263#setLocalVideoView) | Set control for local user video rendering. |
| [openLocalCamera](https://www.tencentcloud.com/document/product/647/67263#openLocalCamera) | Turns the local camera on. |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/67263#closeLocalCamera) | Turns the local camera off. |
| [updateVideoQuality](https://www.tencentcloud.com/document/product/647/67263#updateVideoQuality) | Update local video encoding quality settings. |
| [updateVideoQualityEx](https://www.tencentcloud.com/document/product/647/67263#updateVideoQualityEx) | Set encoding parameters for the video encoder |
| [setVideoResolutionMode](https://www.tencentcloud.com/document/product/647/67263#setVideoResolutionMode) | Set the resolution mode for the video encoder |
| [enableGravitySensor](https://www.tencentcloud.com/document/product/647/67263#enableGravitySensor) | Enable gravity sensing mode |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/67263#startPushLocalVideo) | Start pushing local video. |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/67263#stopPushLocalVideo) | Stop pushing local video. |
| [startScreenSharing](https://www.tencentcloud.com/document/product/647/67263#startScreenSharing) | Starting Screen Sharing |
| [stopScreenSharing](https://www.tencentcloud.com/document/product/647/67263#stopScreenSharing) | End Screen Sharing |

### Local User Audio Management

| API | Description |
| --- | --- |
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/67263#openLocalMicrophone) | Enable the local mic. |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/67263#closeLocalMicrophone) | Disable the local mic. |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/67263#updateAudioQuality) | Update local audio encoding quality settings. |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/67263#startPushLocalAudio) | Stop pushing local audio. |
| [unMuteLocalAudio](https://www.tencentcloud.com/document/product/647/67263#stopPushLocalAudio) | Start pushing local audio. |

### Remote user view rendering, Video Management

| API | Description |
| --- | --- |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/67263#setRemoteVideoView) | Set control for remote user video rendering. |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/67263#124ff5a0-beaa-4d55-b30d-9703290ab5c7) | Start playing remote user video. |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/67263# stopPlayRemoteVideo) | Stop playing remote user video. |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/67263#muteRemoteAudioStream) | Mute remote user. |

### Inside the Room User Information

| API | Description |
| --- | --- |
| [getUserList](https://www.tencentcloud.com/document/product/647/67263#getUserList) | Obtain the member list inside the room. |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/67263#getUserInfo) | Obtain member information. |

### In-room User Management

| API | Description |
| --- | --- |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/67263#changeUserRole) | Modify User Role (only administrators or group owners can invoke). |
| [changeUserNameCard](https://www.tencentcloud.com/document/product/647/67263#changeUserNameCard) | Modify User Nickname. |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/67263#kickRemoteUserOutOfRoom) | Remove Remote User from Room (only administrators or group owners can invoke). |
| [addCategoryTagForUsers](https://www.tencentcloud.com/document/product/647/67263#addCategoryTagForUsers) | Add a label to a user (only homeowners can call) |
| [removeCategoryTagForUsers](https://www.tencentcloud.com/document/product/647/67263#removeCategoryTagForUsers) | Remove a label from a user (only homeowners can call) |
| [getUserListByTag](https://www.tencentcloud.com/document/product/647/67263#getUserListByTag) | Get user information in the room based on labels |
| [setCustomInfoForUser](https://www.tencentcloud.com/document/product/647/67263#setCustomInfoForUser) | Set customized information for members in the room |

### User speaking management in the room

| API | Description |
| --- | --- |
| [disableDeviceForAllUserByAdmin](https://www.tencentcloud.com/document/product/647/67263#disableDeviceForAllUserByAdmin) | Control whether all users in the current room can enable audio stream, video stream capture devices. For example: prohibit everyone from turning on the microphone, camera, or screen sharing (currently available only in meeting scenarios, and only administrators or group owners can invoke). |
| [openRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/67263#63833efa-43b7-4e56-81dc-4417774b1b07) | Request Remote User to Enable Media Devices (only administrators or group owners can invoke). |
| [closeRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/67263#closeRemoteDeviceByAdmin) | Turn Off Remote User Media Devices (only administrators or group owners can invoke). |
| [applyToAdminToOpenLocalDevice](https://www.tencentcloud.com/document/product/647/67263#applyToAdminToOpenLocalDevice) | Request to Enable Local Media Devices (available for regular users). |

### Microphone Position Management within the Rooms

| API | Description |
| --- | --- |
| [setMaxSeatCount](https://www.tencentcloud.com/document/product/647/67263#setMaxSeatCount) | Set Maximum Number of Microphones (can only be set before entering or creating a room). |
| [getSeatList](https://www.tencentcloud.com/document/product/647/67263#getSeatList) | Get the microphone position list. |
| [getSeatApplicationList](https://www.tencentcloud.com/document/product/647/67263#getSeatApplicationList) | Host/Administrator gets the request list of users applying for the microphone in the room. |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/67263#lockSeatByAdmin) | Lock Microphone Position (only administrators or group owners can invoke, including position lock, audio status lock, and video status lock). |
| [takeSeat](https://www.tencentcloud.com/document/product/647/67263#takeSeat) | Apply to join the microphone (no need to apply in free speaking mode). |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/67263#leaveSeat) | Apply to leave the microphone (no need to apply in free speaking mode). |
| [moveToSeat](https://www.tencentcloud.com/document/product/647/67263#moveToSeat) | Disconnect Mic |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/67263#takeUserOnSeatByAdmin) | Host/Administrator invites users to go on stage. |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/67263#kickUserOffSeatByAdmin) | Host/Administrator removes users from the microphone. |

### Signaling Management

| API | Description |
| --- | --- |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/67263#cancelRequest) | Cancel Request. |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/67263#responseRemoteRequest) | Reply Request. |

### Sending Message

| API | Description |
| --- | --- |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/67263#disableSendingMessageByAdmin) | Disable the remote user's ability to send text messages (only administrators or group owners can call this). |
| [disableSendingMessageForAllUser](https://www.tencentcloud.com/document/product/647/67263#disableSendingMessageForAllUser) | Disable all users' ability to send text messages (only administrators or group owners can call this). |

### Advanced Features

| API | Description |
| --- | --- |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/67263#setBeautyLevel) | Set beauty filter effect level |
| [setWhitenessLevel](https://www.tencentcloud.com/document/product/647/67263#setWhitenessLevel) | Set brightening filter effect level |
| [getExtension](https://www.tencentcloud.com/document/product/647/67263#getExtension) | Get plugins |
| [getMediaDeviceManager](https://www.tencentcloud.com/document/product/647/67263#getMediaDeviceManager) | Get device management class |

### Debugging related

| API | Description |
| --- | --- |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/67263#callExperimentalAPI) | Calls an experimental API. |

## TUIRoomObserver Callback Event

TUIRoomObserver is the callback event class corresponding to TUIRoomEngine. You can use this callback to listen to the events you need.

TUIRoomObserver

## TUIRoomObserver

### Error Callback

| API | Description |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/67262#onError) | Error event callback |

### Callback for login status event

| API | Description |
| --- | --- |
| [onKickedOffLine](https://www.tencentcloud.com/document/product/647/67262#onKickedOffLine) | Kicked offline by another client during terminal login. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/67262#onUserSigExpired) | User credentials timeout event. |

### Room Event Callback

| API | Description |
| --- | --- |
| [onRoomNameChanged](https://www.tencentcloud.com/document/product/647/67262#onRoomNameChanged) | Room name change event. |
| [onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/67262#0343c6f5-0de0-4d03-ac6c-c4796f9b6434) | All users' microphones in the room have been disabled event. |
| [onAllUserCameraDisableChanged](https://www.tencentcloud.com/document/product/647/67262#802c03d5-7144-428a-b332-51e63793e5db) | All users' cameras in the room have been disabled event. |
| [onScreenShareForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/67262#onScreenShareForAllUserDisableChanged) | All users' screen sharing in the room has been disabled event. |
| [onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/67262#40a909c8-b39c-412d-aa58-e038e77ba856) | All users' ability to send text messages in the room has been disabled event. |
| [onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/67262#onKickedOutOfRoom) | Removed from the room event. |
| [onRoomDismissed](https://www.tencentcloud.com/document/product/647/67262#onRoomDismissed) | Room dissolved event. |
| [onRoomSeatModeChanged](https://www.tencentcloud.com/document/product/647/67262#onRoomSeatModeChanged) | Room Microphone Mode Change |
| [onRoomUserCountChanged](https://www.tencentcloud.com/document/product/647/67262#7c8a0a9e-1f60-4e14-8a11-fa72dc7221e4) | Room population changed |

### User Event Callback Inside the Room

| API | Description |
| --- | --- |
| [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/67262#onRemoteUserEnterRoom) | Remote user entered room event. |
| [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/67262#onRemoteUserLeaveRoom) | Remote user left room event. |
| [onUserRoleChanged](https://www.tencentcloud.com/document/product/647/67262#onUserRoleChanged) | User role changed event. |
| [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/67262#onUserVideoStateChanged) | User video status changed event. |
| [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/67262#onUserAudioStateChanged) | Event of User Audio Status Changed |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/67262#onUserVoiceVolumeChanged) | User volume changed event. |
| [onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/67262#onSendMessageForUserDisableChanged) | User text message sending capability changed event. |
| [onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/67262#onUserNetworkQualityChanged) | User network status changed event. |
| [onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/67262#onUserScreenCaptureStopped) | Screen sharing ended. |

### Room microphone position event callback

| API | Description |
| --- | --- |
| [onRoomMaxSeatCountChanged](https://www.tencentcloud.com/document/product/647/67262#onRoomMaxSeatCountChanged) | Maximum number of microphones in room changed event (only in meeting type rooms). |
| [onSeatListChanged](https://www.tencentcloud.com/document/product/647/67262#onSeatListChanged) | Microphone position list changed event. |
| [onKickedOffSeat](https://www.tencentcloud.com/document/product/647/67262#4c91dcc7-f9ed-4e50-8948-763b420b0662) | User removed from microphone event received. |

### Request signaling event callback

| API | Description |
| --- | --- |
| [onRequestReceived](https://www.tencentcloud.com/document/product/647/67262# onRequestReceived) | Request message event received. |
| [onRequestCancelled](https://www.tencentcloud.com/document/product/647/67262#510d9829-0e77-421f-abd5-4323d8bb456c) | Request cancellation event received. |
| [onRequestProcessed](https://www.tencentcloud.com/document/product/647/67262#onRequestProcessed) | Received request handled by another administrator/homeowner event |


---
*Source: [https://trtc.io/document/67264](https://trtc.io/document/67264)*
