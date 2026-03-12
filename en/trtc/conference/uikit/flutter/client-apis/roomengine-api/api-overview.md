# API Overview

## Overview

TUIRoomEngine ([rtc_room_engine](https://pub.dev/packages/rtc_room_engine)) is a component designed for scenarios involving corporate meetings, webinars, online education, etc., supporting multi-person audio and video conversations. It offers room management, multi-person TRTC interactions, member management, screen sharing, and other meeting control features, and supports various video qualities including standard definition, high definition, and ultra-high definition. By integrating this component, you can add multi-person audio and video conversation features to your application.

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

TUIRoomEngine API is the Audio/Video call Component's No UI Interface, you can use this set of API to customize packaging according to your business needs.

TUIRoomEngine

### TUIRoomEngine Core Methods

| API | Description |
| --- | --- |
| [createInstance](https://www.tencentcloud.com/document/product/647/57514#createInstance) | Create TUIRoomEngine Instance |
| [destroyInstance](https://www.tencentcloud.com/document/product/647/57514#destroyInstance) | Destroy TUIRoomEngine Instance |
| [login](https://www.tencentcloud.com/document/product/647/57514#login) | Login interface, you need to initialize user information before entering the room and perform a series of operations. |
| [logout](https://www.tencentcloud.com/document/product/647/57514#logout) | Logout interface, there will be actively leave room operation, destroy resources |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/57514#setSelfInfo) | Set local user name and avatar |
| [setLoginUserInfo](https://www.tencentcloud.com/document/product/647/57514#setLoginUserInfo) | Set login user information |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/57514#getSelfInfo) | Get local user basic information |
| [addObserver](https://www.tencentcloud.com/document/product/647/57514#addObserver) | Set event callback |
| [removeObserver](https://www.tencentcloud.com/document/product/647/57514#removeObserver) | Remove event callback |

### Room Related Active Interface

| API | Description |
| --- | --- |
| [createRoom](https://www.tencentcloud.com/document/product/647/57514#createRoom) | Create room |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/57514#destroyRoom) | Close the room |
| [enterRoom](https://www.tencentcloud.com/document/product/647/57514#enterRoom) | Entered room |
| [exitRoom](https://www.tencentcloud.com/document/product/647/57514#exitRoom) | Leave room |
| [connectOtherRoom](https://www.tencentcloud.com/document/product/647/57514#connectOtherRoom) | Connect to other room |
| [disconnectOtherRoom](https://www.tencentcloud.com/document/product/647/57514#disconnectOtherRoom) | Disconnect from other room |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/57514#fetchRoomInfo) | Get room data |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/57514#updateRoomNameByAdmin) | Update room name |
| [updateRoomSpeechModeByAdmin](https://www.tencentcloud.com/document/product/647/57514#updateRoomSpeechModeByAdmin) | Set room management mode (only administrator or group owner can call) |

### Local User View Rendering, Video Management

| API | Description |
| --- | --- |
| [setLocalVideoView](https://www.tencentcloud.com/document/product/647/57514#setLocalVideoView) | Set the view control for local user video rendering |
| [openLocalCamera](https://www.tencentcloud.com/document/product/647/57514#openLocalCamera) | Open local camera |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/57514#closeLocalCamera) | Close local camera |
| [updateVideoQuality](https://www.tencentcloud.com/document/product/647/57514#updateVideoQuality) | Update local video codec quality settings |
| [updateVideoQualityEx](https://www.tencentcloud.com/document/product/647/57514#updateVideoQualityEx) | Set the encoding parameters of video encoder |
| [setVideoResolutionMode](https://www.tencentcloud.com/document/product/647/57514#setVideoResolutionMode) | Set the  resolution mode of video encoder |
| [enableGravitySensor](https://www.tencentcloud.com/document/product/647/57514#enableGravitySensor) | Enable the gravity sensor |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/57514#startPushLocalVideo) | Start pushing local video |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/57514#stopPushLocalVideo) | Stop pushing local video |
| [startScreenSharing](https://www.tencentcloud.com/document/product/647/57514#startScreenSharing) | Start screen sharing |
| [stopScreenSharing](https://www.tencentcloud.com/document/product/647/57514#stopScreenSharing) | Stop screen sharing |

### Local User Audio Management

| API | Description |
| --- | --- |
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/57514#openLocalMicrophone) | Open local microphone |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/57514#closeLocalMicrophone) | Close local microphone |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/57514#updateAudioQuality) | Update local audio codec quality settings |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/57514#muteLocalAudio) | Mute local audio |
| [unMuteLocalAudio](https://www.tencentcloud.com/document/product/647/57514#unMuteLocalAudio) | UnMute local audio |

### Remote User View Rendering, Video Management

| API | Description |
| --- | --- |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/57514#setRemoteVideoView) | Set the view control for remote user video rendering |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/57514#startPlayRemoteVideo) | Start playing remote user video |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/57514#stopPlayRemoteVideo) | Stop playing remote user video |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/57514#muteRemoteAudioStream) | Mute remote user |

### Room User Information

| API | Description |
| --- | --- |
| [getUserList](https://www.tencentcloud.com/document/product/647/57514#getUserList) | Get the member list in the room |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/57514#getUserInfo) | Get member information |

### Room User Management

| API | Description |
| --- | --- |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/57514#changeUserRole) | Modify user role (only administrator or group owner can call) |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/57514#kickRemoteUserOutOfRoom) | Kick Remote User out of the Room (Only Administrator or Group Owner can call) |
| [addCategoryTagForUsers](https://www.tencentcloud.com/document/product/647/57514#addCategoryTagForUsers) | Add category tags to users (Only Administrator or Group Owner can call) |
| [removeCategoryTagForUsers](https://www.tencentcloud.com/document/product/647/57514#removeCategoryTagForUsers) | Remove category tags to users (Only Administrator or Group Owner can call) |
| [getUserListByTag](https://www.tencentcloud.com/document/product/647/57514#getUserListByTag) | Get user information in the room based on tags |

### Speech Management in Room

| API | Description |
| --- | --- |
| [disableDeviceForAllUserByAdmin](https://www.tencentcloud.com/document/product/647/57514#disableDeviceForAllUserByAdmin) | Control the permission status of whether all users in the current room can open Audio and Video streams capturing devices, such as: Prohibit all from turning on the mic, Prohibit all from turning on the Camera, Prohibit all from turning on Screen Sharing (currently only available in meeting scenes, and only administrators or group owners can invoke). |
| [openRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/57514#openRemoteDeviceByAdmin) | Request Remote User to Open Media Device (Only Administrator or Group Owner can call) |
| [closeRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/57514#closeRemoteDeviceByAdmin) | Close Remote User's Media Device (Only Administrator or Group Owner can call) |
| [applyToAdminToOpenLocalDevice](https://www.tencentcloud.com/document/product/647/57514#applyToAdminToOpenLocalDevice) | Request to Open Local Media Device (Available for Ordinary Users) |

### Microphone Seat Management in Room

| API | Description |
| --- | --- |
| [setMaxSeatCount](https://www.tencentcloud.com/document/product/647/57514#setMaxSeatCount) | Set Maximum Number of Microphone Seats (Only supported when entering the room and creating the room) |
| [getSeatList](https://www.tencentcloud.com/document/product/647/57514#getSeatList) | Get Microphone Seat List |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/57514#lockSeatByAdmin) | Lock Microphone Seat (Including Position Lock, Audio State Lock, Video State Lock) |
| [takeSeat](https://www.tencentcloud.com/document/product/647/57514#takeSeat) | Apply to Go Live (Not Required in Free Speech Mode) |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/57514#leaveSeat) | Apply to leave the live (Not Required in Free Speech Mode) |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/57514#takeUserOnSeatByAdmin) | Host/Administrator invites user to go live |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/57514#kickUserOffSeatByAdmin) | Host/Administrator kicks user off the microphone seat |

### Signaling Management

| API | Description |
| --- | --- |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/57514#cancelRequest) | Cancel Request |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/57514#responseRemoteRequest) | Reply to Request |

### Send Message

| API | Description |
| --- | --- |
| [sendTextMessage](https://www.tencentcloud.com/document/product/647/57514#sendTextMessage) | Send Text Message |
| [sendCustomMessage](https://www.tencentcloud.com/document/product/647/57514#sendCustomMessage) | Send Custom Message |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/57514#disableSendingMessageByAdmin) | Disable Remote User's Text Message Sending Ability (Only Administrator or Group Owner can call) |
| [disableSendingMessageForAllUser](https://www.tencentcloud.com/document/product/647/57514#disableSendingMessageForAllUser) | Disable All Users' Text Message Sending Ability (Only Administrator or Group Owner can call) Advanced Feature: Get TRTC Instance |

### Advanced Features

| API | Description |
| --- | --- |
| [switchCamera](https://www.tencentcloud.com/document/product/647/57514#switchCamera) | Switch front/rear camera |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/57514#setBeautyLevel) | Set beauty level |
| [setWhitenessLevel](https://www.tencentcloud.com/document/product/647/57514#setWhitenessLevel) | Set whiteness level |

### Debugging related

| API | Description |
| --- | --- |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/57514#callExperimentalAPI) | Call experimental api |

## TUIRoomObserver Callback Event

TUIRoomObserver is the Callback Event class corresponding to TUIRoomEngine. You can monitor the Callback Events you need through this Callback.

TUIRoomObserver

## TUIRoomObserver

### Error Callback

| API | Description |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/57513#onError) | Error Callback Event |

### Login Status Event Callback

| API | Description |
| --- | --- |
| [onKickedOffLine](https://www.tencentcloud.com/document/product/647/57513#onKickedOffLine) | User Kicked Offline Event |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/57513#onUserSigExpired) | User Credential Timeout Event |

### Room Event Callback

| API | Description |
| --- | --- |
| [onRoomNameChanged](https://www.tencentcloud.com/document/product/647/57513#onRoomNameChanged) | Room Name Change Event |
| [onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/57513#onAllUserMicrophoneDisableChanged) | All Users' Microphones Disabled in Room Event |
| [onAllUserCameraDisableChanged](https://www.tencentcloud.com/document/product/647/57513#onAllUserCameraDisableChanged) | All Users' Cameras Disabled in Room Event |
| [onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/57513#onSendMessageForAllUserDisableChanged) | All Users' Text Message Sending Disabled in Room Event |
| [onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/57513#onKickedOutOfRoom) | Room Dismissed Event |
| [onRoomDismissed](https://www.tencentcloud.com/document/product/647/57513#onRoomDismissed) | Kicked Out of Room Event |
| [onRoomSpeechModeChanged](https://www.tencentcloud.com/document/product/647/57513#onRoomSpeechModeChanged) | Room Microphone Control Mode Change |

### Room User Event Callback

| API | Description |
| --- | --- |
| [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/57513#onRemoteUserEnterRoom) | Remote User Entering Room Event |
| [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/57513#onRemoteUserLeaveRoom) | Remote User Leaving Room Event |
| [onUserRoleChanged](https://www.tencentcloud.com/document/product/647/57513#onUserRoleChanged) | User Role Change Event |
| [onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/57513#onUserVideoStateChanged) | User Video State Change Event |
| [onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/57513#onUserAudioStateChanged) | User Audio State Change Event |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/57513#onUserVoiceVolumeChanged) | User Volume Change Event |
| [onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/57513#onSendMessageForUserDisableChanged) | User Text Message Sending Ability Change Event |
| [onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/57513#onUserNetworkQualityChanged) | User Network Status Change Event |
| [onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/57513#onUserScreenCaptureStopped) | Screen Sharing End Event |

### Room Microphone Seat Event Callback

| API | Description |
| --- | --- |
| [onRoomMaxSeatCountChanged](https://www.tencentcloud.com/document/product/647/57513#onRoomMaxSeatCountChanged) | Room Maximum Microphone Seat Number Change Event (Only effective in conference type rooms) |
| [onSeatListChanged](https://www.tencentcloud.com/document/product/647/57513#onSeatListChanged) | Microphone Seat List Change Event |
| [onKickedOffSeat](https://www.tencentcloud.com/document/product/647/57513#onKickedOffSeat) | Received User Kicked Off Microphone Event |

### Request Signaling Event Callback

| API | Description |
| --- | --- |
| [onRequestReceived](https://www.tencentcloud.com/document/product/647/57513#onRequestReceived) | Received Request Message Event |
| [onRequestCancelled](https://www.tencentcloud.com/document/product/647/57513#onRequestCancelled) | Received Request Cancellation Event |

### Room Message Event Callback

| API | Description |
| --- | --- |
| [onReceiveTextMessage](https://www.tencentcloud.com/document/product/647/57513#onReceiveTextMessage) | Received Normal Text Message Event |
| [onReceiveCustomMessage](https://www.tencentcloud.com/document/product/647/57513#onReceiveCustomMessage) | Received Custom Message Event |


---
*Source: [https://trtc.io/document/57512](https://trtc.io/document/57512)*
