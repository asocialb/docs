# API Overview

## TUIRoomKit (UI included Component)

### TUIRoomKit API List

| API | Description |
| --- | --- |
| [getRoomEngine](https://www.tencentcloud.com/document/product/647/54880#b3295cfe-067f-4193-96f6-4a829dcfcc15) | Get the roomEngine instance. If the roomEngine does not exist, return null. |
| [on](https://www.tencentcloud.com/document/product/647/54880#54e35df8-f2db-4796-81ea-10f775e92e4c) | Listen for events of a specified type. When the event occurs, the callback function will be called. |
| [off](https://www.tencentcloud.com/document/product/647/54880#fd92a726-7469-46ca-af7c-5a36636a2782) | Stop listening for events of a specified type. |
| [login](https://www.tencentcloud.com/document/product/647/54880#5a429689-e07a-4c01-bfc6-bfb67f7f5b7f) | Log in to the conference system. |
| [logout](https://www.tencentcloud.com/document/product/647/54880#40f8261a-7135-4739-8149-9984c105678b) | Log out of the meeting system. |
| [start](https://www.tencentcloud.com/document/product/647/54880#b0bf2a3b-428c-474f-9a0e-271c7c3b6bfd) | Start a new meeting. |
| [join](https://www.tencentcloud.com/document/product/647/54880#b08d0951-c1f4-4db4-a84d-8414b853d0f1) | Join an existing meeting. |
| [leave](https://www.tencentcloud.com/document/product/647/54880#ffc266fb-4207-4e59-b664-82ce6046758b) | Leave the current meeting. |
| [dismiss](https://www.tencentcloud.com/document/product/647/54880#31e2d7df-1c4d-449f-80fa-e6e50ebe0f6f) | Dismiss the current meeting. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54880#949c2101-7f9f-435a-8a60-294df8545620) | Set your user information. |
| [setLanguage](https://www.tencentcloud.com/document/product/647/54880#51991a76-0777-4773-a2dd-91ce51b92b18) | Set the interface language. |
| [setTheme](https://www.tencentcloud.com/document/product/647/54880#5bb291c2-edb5-48b0-968a-db52ed2252ae) | Set the interface topic. |
| [disableTextMessaging](https://www.tencentcloud.com/document/product/647/54880#9ed81bb6-73a0-4b75-878e-22cc641b43bc) | Disable the text messaging feature in the application. After invoking this function, users will not be able to send or receive text messages. |
| [disableScreenSharing](https://www.tencentcloud.com/document/product/647/54880#833fce4f-6e77-45bf-bea0-33a618b540fb) | Disable the screen sharing feature in the application. After invoking this function, users will not be able to share their screen with others. |
| [hideFeatureButton](https://www.tencentcloud.com/document/product/647/54880#49c62018-9bc4-4117-bf68-aa985b868890) | Hide specific feature buttons in the application. By invoking this function and passing in the appropriate [FeatureButton](https://www.tencentcloud.com/document/product/647/54880#6f28a0a9-c315-400e-a73f-b1fbd0b039eb) enumerated values, the corresponding buttons will be hidden from the user interface. |

## TUIRoomEngine (No UI interface)

### TUIRoomEngine API List

**TUIRoomEngine Static method**

| API | Description |
| --- | --- |
| [once](https://www.tencentcloud.com/document/product/647/54878#once) | Listen to TUIRoomEngine ready event.**Note: All methods except TUIRoomEngine.init must be executed after listening to the TUIRoomEngine ready event and the TUIRoomEngine.init method is executed successfully.** |
| [login](https://www.tencentcloud.com/document/product/647/54878#login) | Login to TUIRoomEngine |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54878#setSelfInfo) | Set the current user's basic information (username, user avatar) |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/54878#getSelfInfo) | Get the current user's basic information (username, user avatar) |
| [logout](https://www.tencentcloud.com/document/product/647/54878#logout) | Logout from TUIRoomEngine |

**RoomEngine Room Management API**

| API | Description |
| --- | --- |
| [createRoom](https://www.tencentcloud.com/document/product/647/54878#createRoom) | Create room |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54878#enterRoom) | Entered room |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/54878#destroyRoom) | Close the room |
| [exitRoom](https://www.tencentcloud.com/document/product/647/54878#exitRoom) | Leave room |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/54878#fetchRoomInfo) | Get room data |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/54878#updateRoomNameByAdmin) | Update the room's name (Only group owner or administrator can call) |
| [updateRoomSpeechModeByAdmin](https://www.tencentcloud.com/document/product/647/54878#updateRoomSpeechModeByAdmin) | Update the room's speech mode (Only group owner or administrator can call) |
| [getUserList](https://www.tencentcloud.com/document/product/647/54878#getUserList) | Get the current room user list |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/54878#getUserInfo) | Get user Learn more |

**roomEngine Audio Video API**

| API | Description |
| --- | --- |
| [setLocalVideoView](https://www.tencentcloud.com/document/product/647/54878#setLocalRenderView) | Set the view control for local user video rendering |
| [openLocalCamera](https://www.tencentcloud.com/document/product/647/54878#openLocalCamera) | Open local camera |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/54878#closeLocalCamera) | Close local camera |
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/54878#openLocalMicrophone) | Open local microphone |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/54878#closeLocalMicrophone) | Close local microphone |
| [updateVideoQuality](https://www.tencentcloud.com/document/product/647/54878#updateVideoQuality) | Update local video codec quality settings |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/54878#updateAudioQuality) | Update local audio codec quality settings |
| [startScreenSharing](https://www.tencentcloud.com/document/product/647/54878#startScreenSharing) | Start screen sharing |
| [stopScreenSharing](https://www.tencentcloud.com/document/product/647/54878#stopScreenSharing) | End screen sharing |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/54878#startPushLocalVideo) | Start pushing local video |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/54878#stopPushLocalVideo) | Stop pushing local video |
| [startPushLocalAudio](https://www.tencentcloud.com/document/product/647/54878#startPushLocalAudio) | Start pushing local audio |
| [stopPushLocalAudio](https://www.tencentcloud.com/document/product/647/54878#stopPushLocalAudio) | Stop pushing local audio |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/54878#setRemoteVideoView) | Set the view control for remote user video rendering |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54878#startPlayRemoteVideo) | Start playing remote user video |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54878#stopPlayRemoteVideo) | Stop playing remote user video |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/54878#muteRemoteAudioStream) | Mute remote user |

**roomEngine Member Management API**

| API | Description |
| --- | --- |
| [openRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54878#openRemoteDeviceByAdmin) | Request remote user to open media device |
| [applyToAdminToOpenLocalDevice](https://www.tencentcloud.com/document/product/647/54878#applyToAdminToOpenLocalDevice) | Participant applies to the host to open the device |
| [closeRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54878#closeRemoteDeviceByAdmin) | Close remote user's media device |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/54878#cancelRequest) | Cancel the sent request |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/54878#responseRemoteRequest) | Reply to remote user's request |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/54878#changeUserRole) | Change user's role |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/54878#kickRemoteUserOutOfRoom) | Kick user out of the room |
| [disableDeviceForAllUserByAdmin](https://www.tencentcloud.com/document/product/647/54878#disableDeviceForAllUserByAdmin) | Disable/Enable all users' media devices |
| [disableSendingMessageForAllUser](https://www.tencentcloud.com/document/product/647/54878#disableSendingMessageForAllUser) | Disable/Enable all users to send messages |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/54878#disableSendingMessageByAdmin) | Disable/Enable a user to send messages |

**roomEngine Microphone Management API**

| API | Description |
| --- | --- |
| [setMaxSeatCount](https://www.tencentcloud.com/document/product/647/54878#setMaxSeatCount) | Set room microphone position maximum value |
| [getSeatList](https://www.tencentcloud.com/document/product/647/54878#getSeatList) | Get microphone position information |
| [takeSeat](https://www.tencentcloud.com/document/product/647/54878#takeSeat) | Get microphone position |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/54878#leaveSeat) | Release microphone position |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/54878#takeUserOnSeatByAdmin) | Invite others to go live (only room host and administrator can call this method) |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/54878#kickUserOffSeatByAdmin) | Kick others off the microphone position (only room host and administrator can call this method) |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/54878#lockSeatByAdmin) | Lock a microphone position status (only room host and administrator can call this method) |

**roomEngine Message Sending API**

| API | Description |
| --- | --- |
| [sendTextMessage](https://www.tencentcloud.com/document/product/647/54878#sendTextMessage) | Send text message |
| [sendCustomMessage](https://www.tencentcloud.com/document/product/647/54878#sendCustomMessage) | Send custom message |

**roomEngine Device Management API**

| API | Description |
| --- | --- |
| [getCameraDevicesList](https://www.tencentcloud.com/document/product/647/54878#getCameraDevicesList) | Get camera device list |
| [getMicDevicesList](https://www.tencentcloud.com/document/product/647/54878#getMicDevicesList) | Get mic device list |
| [getSpeakerDevicesList](https://www.tencentcloud.com/document/product/647/54878#getSpeakerDevicesList) | Get speaker device list |
| [setCurrentCameraDevice](https://www.tencentcloud.com/document/product/647/54878#setCurrentCameraDevice) | Set the camera device to use |
| [setCurrentMicDevice](https://www.tencentcloud.com/document/product/647/54878#setCurrentMicDevice) | Set the mic device to use |
| [setCurrentSpeakerDevice](https://www.tencentcloud.com/document/product/647/54878#setCurrentSpeakerDevice) | Set the speaker device to use |
| [getCurrentCameraDevice](https://www.tencentcloud.com/document/product/647/54878#getCurrentCameraDevice) | Get the currently used camera device |
| [getCurrentMicDevice](https://www.tencentcloud.com/document/product/647/54878#getCurrentMicDevice) | Get the currently used mic device |
| [getCurrentSpeakerDevice](https://www.tencentcloud.com/document/product/647/54878#getCurrentSpeakerDevice) | Get the currently used speaker device |
| [startCameraDeviceTest](https://www.tencentcloud.com/document/product/647/54878#startCameraDeviceTest) | Start camera device test |
| [stopCameraDeviceTest](https://www.tencentcloud.com/document/product/647/54878#stopCameraDeviceTest) | Stop camera device test |

**roomEngine Event Listening API**

| API | Description |
| --- | --- |
| [on](https://www.tencentcloud.com/document/product/647/54878#on) | Listen to [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/54876#) event |
| [off](https://www.tencentcloud.com/document/product/647/54878#off) | Cancel listening to [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/54876#) event |

**roomEngine Other API**

| API | Description |
| --- | --- |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/54878#getTRTCCloud) | Get trtcCloud instance |
| [getTIM](https://www.tencentcloud.com/document/product/647/54878#getTIM) | Get tim instance |

### TUIRoomEngine Event Type

TUIRoomEvent is the Callback Event class corresponding to TUIRoomEngine. You can listen to the Callback Events you are interested in through this callback.

| EVENT | Description |
| --- | --- |
| [TUIRoomEvents.onError](https://www.tencentcloud.com/document/product/647/54879#onError) | Error Event |
| [TUIRoomEvents.onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/54879#onKickedOutOfRoom) | Kick out of room event |
| [TUIRoomEvents.onKickedOffLine](https://www.tencentcloud.com/document/product/647/54879#onKickedOffLine) | User Kicked Offline Event |
| [TUIRoomEvents.onUserSigExpired](https://www.tencentcloud.com/document/product/647/54879#onUserSigExpired) | User Credential Timeout Event |
| [TUIRoomEvents.onRoomDismissed](https://www.tencentcloud.com/document/product/647/54879#onRoomDismissed) | Room Dismissed Event |
| [TUIRoomEvents.onRoomNameChanged](https://www.tencentcloud.com/document/product/647/54879#onRoomNameChanged) | Room Name Change Event |
| [TUIRoomEvents.onRoomSpeechModeChanged](https://www.tencentcloud.com/document/product/647/54879#onRoomSpeechModeChanged) | Room Microphone Control Mode Change |
| [TUIRoomEvents.onAllUserCameraDisableChanged](https://www.tencentcloud.com/document/product/647/54879#onAllUserCameraDisableChanged) | All Users' Cameras Disabled in Room Event |
| [TUIRoomEvents.onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/54879#onAllUserMicrophoneDisableChanged) | All Users' Microphones Disabled in Room Event |
| [TUIRoomEvents.onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54879#onSendMessageForAllUserDisableChanged) | All Users' Text Message Sending Disabled in Room Event |
| [TUIRoomEvents.onRoomMaxSeatCountChanged](https://www.tencentcloud.com/document/product/647/54879#onRoomMaxSeatCountChanged) | Maximum number of microphone slots in the room modification event |
| [TUIRoomEvents.onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54879#onRemoteUserEnterRoom) | Remote user Entered room event |
| [TUIRoomEvents.onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/54879#onRemoteUserLeaveRoom) | Remote user leaving room event |
| [TUIRoomEvents.onUserRoleChanged](https://www.tencentcloud.com/document/product/647/54879#onUserRoleChanged) | Role change event |
| [TUIRoomEvents.onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54879#onUserVideoStateChanged) | Video Status change event |
| [TUIRoomEvents.onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54879#onUserAudioStateChanged) | Audio Status change event |
| [TUIRoomEvents.onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/54879#onSendMessageForUserDisableChanged) | Send message status event |
| [TUIRoomEvents.onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/54879#onUserVoiceVolumeChanged) | Volume change event |
| [TUIRoomEvents.onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/54879#onUserNetworkQualityChanged) | Network quality change event |
| [TUIRoomEvents.onSeatListChanged](https://www.tencentcloud.com/document/product/647/54879#onSeatListChanged) | Mic position list change event |
| [TUIRoomEvents.onKickedOffSeat](https://www.tencentcloud.com/document/product/647/54879#onKickedOffSeat) | Kicked off the mic event |
| [TUIRoomEvents.onRequestReceived](https://www.tencentcloud.com/document/product/647/54879#onRequestReceived) | Request received event |
| [TUIRoomEvents.onRequestCancelled](https://www.tencentcloud.com/document/product/647/54879#onRequestCancelled) | Request cancelled event |
| [TUIRoomEvents.onReceiveTextMessage](https://www.tencentcloud.com/document/product/647/54879#onReceiveTextMessage) | Receive text message event |
| [TUIRoomEvents.onReceiveCustomMessage](https://www.tencentcloud.com/document/product/647/54879#onReceiveCustomMessage) | Receive custom message event |
| [TUIRoomEvents.onDeviceChange](https://www.tencentcloud.com/document/product/647/54879#onDeviceChange) | Device change event |
| [TUIRoomEvents.onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/54879#onUserScreenCaptureStopped) | Screen sharing stopped eventWhen a user uses the built-in browser's **stop sharing** button to end Screen Sharing, the user will receive the 'onUserScreenCaptureStopped' event to modify the Sharing status. |


---
*Source: [https://trtc.io/document/54877](https://trtc.io/document/54877)*
