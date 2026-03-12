# API Overview

## TUIRoomEngine (No UI interface)

#### **TUIRoomEngine Static method**

| API | Description |
| --- | --- |
| [once](https://www.tencentcloud.com/document/product/647/54883#once) | **Listen to TUIRoomEngine ready event. Note: All methods except TUIRoomEngine.init must be executed after listening to the TUIRoomEngine ready event and the TUIRoomEngine.init method is executed successfully.** |
| [login](https://www.tencentcloud.com/document/product/647/54883#login) | Login to TUIRoomEngine |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54883#setSelfInfo) | Set the current user's basic information (username, user avatar) |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/54883#getSelfInfo) | Get the current user's basic information (username, user avatar) |
| [logout](https://www.tencentcloud.com/document/product/647/54883#logout) | Logout from TUIRoomEngine |

#### **RoomEngine Room Management API**

| API | Description |
| --- | --- |
| [createRoom](https://www.tencentcloud.com/document/product/647/54883#createRoom) | Create room |
| [enterRoom](https://www.tencentcloud.com/document/product/647/54883#enterRoom) | Entered room |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/54883#destroyRoom) | Close the room |
| [exitRoom](https://www.tencentcloud.com/document/product/647/54883#exitRoom) | Leave room |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/54883#fetchRoomInfo) | Get room data |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/54883#updateRoomNameByAdmin) | Update the room's name (Only group owner or administrator can call) |
| [updateRoomSpeechModeByAdmin](https://www.tencentcloud.com/document/product/647/54883#updateRoomSpeechModeByAdmin) | Update the room's speech mode (Only group owner or administrator can call) |
| [getUserList](https://www.tencentcloud.com/document/product/647/54883#getUserList) | Get the current room user list |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/54883#getUserInfo) | Get user Learn more |

#### **roomEngine Audio Video API**

| API | Description |
| --- | --- |
| [setLocalVideoView](https://www.tencentcloud.com/document/product/647/54883#setLocalVideoView) | Set the view control for local user video rendering |
| [openLocalCamera](https://www.tencentcloud.com/document/product/647/54883#openLocalCamera) | Open local camera |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/54883#closeLocalCamera) | Close local camera |
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/54883#openLocalMicrophone) | Open local microphone |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/54883#closeLocalMicrophone) | Close local microphone |
| [updateVideoQuality](https://www.tencentcloud.com/document/product/647/54883#updateVideoQuality) | Update local video codec quality settings |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/54883#updateAudioQuality) | Update local audio codec quality settings |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/54883#startPushLocalVideo) | Start pushing local video |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/54883#stopPushLocalVideo) | Stop pushing local video |
| [startPushLocalAudio](https://www.tencentcloud.com/document/product/647/54883#startPushLocalAudio) | Start pushing local audio |
| [stopPushLocalAudio](https://www.tencentcloud.com/document/product/647/54883#stopPushLocalAudio) | Stop pushing local audio |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/54883#setRemoteVideoView) | Set the view control for remote user video rendering |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54883#startPlayRemoteVideo) | Start playing remote user video |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/54883#stopPlayRemoteVideo) | Stop playing remote user video |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/54883#muteRemoteAudioStream) | Mute remote user |

#### **roomEngine Member Management API**

| API | Description |
| --- | --- |
| [openRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54883#openRemoteDeviceByAdmin) | Request remote user to open media device |
| [applyToAdminToOpenLocalDevice](https://www.tencentcloud.com/document/product/647/54883#applyToAdminToOpenLocalDevice) | Participant applies to the host to open the device |
| [closeRemoteDeviceByAdmin](https://www.tencentcloud.com/document/product/647/54883#closeRemoteDeviceByAdmin) | Close remote user's media device |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/54883#cancelRequest) | Cancel the sent request |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/54883#responseRemoteRequest) | Reply to remote user's request |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/54883#changeUserRole) | Change user's role |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/54883#kickRemoteUserOutOfRoom) | Kick user out of the room |
| [disableDeviceForAllUserByAdmin](https://www.tencentcloud.com/document/product/647/54883#disableDeviceForAllUserByAdmin) | Disable/Enable all users' media devices |
| [disableSendingMessageForAllUser](https://www.tencentcloud.com/document/product/647/54883#disableSendingMessageForAllUser) | Disable/Enable all users to send messages |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/54883#disableSendingMessageByAdmin) | Disable/Enable a user to send messages |

#### roomEngine Screen Sharing API

| API | Description |
| --- | --- |
| [startScreenSharingElectron](https://www.tencentcloud.com/document/product/647/54883#startScreenSharingElectron) | Start screen sharing |
| [stopScreenSharingElectron](https://www.tencentcloud.com/document/product/647/54883#stopScreenSharingElectron) | End screen sharing |
| [getScreenSharingTarget](https://www.tencentcloud.com/document/product/647/54883#getScreenSharingTarget) | Get Screen Sharing List |
| [selectScreenSharingTarget](https://www.tencentcloud.com/document/product/647/54883#selectScreenSharingTarget) | Switch Screen Sharing Window |

#### roomEngine Microphone Management API

| API | Description |
| --- | --- |
| [setMaxSeatCount](https://www.tencentcloud.com/document/product/647/54883#setMaxSeatCount) | Set Room Microphone Maximum |
| [getSeatList](https://www.tencentcloud.com/document/product/647/54883#getSeatList) | Get Microphone Information |
| [takeSeat](https://www.tencentcloud.com/document/product/647/54883#takeSeat) | Get Microphone |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/54883#leaveSeat) | Release Microphone |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/54883#takeUserOnSeatByAdmin) | Invite Others to Go Live (Only the Host and Administrator can call this method) |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/54883#kickUserOffSeatByAdmin) | Kick Off Microphone (Only the Host and Administrator can call this method) |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/54883#lockSeatByAdmin) | Lock a Microphone Status (Only the Host and Administrator can call this method) |

#### **roomEngine Message Sending API**

| API | Description |
| --- | --- |
| [sendTextMessage](https://www.tencentcloud.com/document/product/647/54883#sendTextMessage) | Send text message |
| [sendCustomMessage](https://www.tencentcloud.com/document/product/647/54883#sendCustomMessage) | Send custom message |

#### **roomEngine Device Management API**

| API | Description |
| --- | --- |
| [getCameraDevicesList](https://www.tencentcloud.com/document/product/647/54883#getCameraDevicesList) | Get camera device list |
| [getMicDevicesList](https://www.tencentcloud.com/document/product/647/54883#getMicDevicesList) | Get mic device list |
| [getSpeakerDevicesList](https://www.tencentcloud.com/document/product/647/54883#getSpeakerDevicesList) | Get speaker device list |
| [setCurrentCameraDevice](https://www.tencentcloud.com/document/product/647/54883#setCurrentCameraDevice) | Set the camera device to use |
| [setCurrentMicDevice](https://www.tencentcloud.com/document/product/647/54883#setCurrentMicDevice) | Set the mic device to use |
| [setCurrentSpeakerDevice](https://www.tencentcloud.com/document/product/647/54883#setCurrentSpeakerDevice) | Set the speaker device to use |
| [getCurrentCameraDevice](https://www.tencentcloud.com/document/product/647/54883#getCurrentCameraDevice) | Get the currently used camera device |
| [getCurrentMicDevice](https://www.tencentcloud.com/document/product/647/54883#getCurrentMicDevice) | Get the currently used mic device |
| [getCurrentSpeakerDevice](https://www.tencentcloud.com/document/product/647/54883#getCurrentSpeakerDevice) | Get the currently used speaker device |
| [startCameraDeviceTest](https://www.tencentcloud.com/document/product/647/54883#startCameraDeviceTest) | Start camera device test |
| [stopCameraDeviceTest](https://www.tencentcloud.com/document/product/647/54883#stopCameraDeviceTest) | Stop camera device test |

#### **roomEngine Event Listening API**

| API | Description |
| --- | --- |
| [on](https://www.tencentcloud.com/document/product/647/54883#on) | Listen to [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/54886#) event |
| [off](https://www.tencentcloud.com/document/product/647/54883#off) | Cancel listening to [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/54886#) event |

#### r**oomEngine Other API**

| API | Description |
| --- | --- |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/54883#getTRTCCloud) | Get trtcCloud instance |
| [getTIM](https://www.tencentcloud.com/document/product/647/54883#getTIM) | Get tim instance |

## Event Type Definition

TUIRoomEvent is the Callback Event class corresponding to TUIRoomEngine. You can listen to Callback Events of interest through this callback.

| EVENT | Description |
| --- | --- |
| [TUIRoomEvents.onError](https://www.tencentcloud.com/document/product/647/54884#onError) | Error Event |
| [TUIRoomEvents.onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/54884#onKickedOutOfRoom) | Kick out of room event |
| [TUIRoomEvents.onKickedOffLine](https://www.tencentcloud.com/document/product/647/54884#onKickedOffLine) | User Kicked Offline Event |
| [TUIRoomEvents.onUserSigExpired](https://www.tencentcloud.com/document/product/647/54884#onUserSigExpired) | User Credential Timeout Event |
| [TUIRoomEvents.onRoomDismissed](https://www.tencentcloud.com/document/product/647/54884#onRoomDismissed) | Room Dismissed Event |
| [TUIRoomEvents.onRoomNameChanged](https://www.tencentcloud.com/document/product/647/54884#onRoomNameChanged) | Room Name Change Event |
| [TUIRoomEvents.onRoomSpeechModeChanged](https://www.tencentcloud.com/document/product/647/54884#onRoomSpeechModeChanged) | Room Microphone Control Mode Change |
| [TUIRoomEvents.onAllUserCameraDisableChanged](https://www.tencentcloud.com/document/product/647/54884#onAllUserCameraDisableChanged) | All Users' Cameras Disabled in Room Event |
| [TUIRoomEvents.onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/54884#onAllUserMicrophoneDisableChanged) | All Users' Microphones Disabled in Room Event |
| [TUIRoomEvents.onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/54884#onSendMessageForAllUserDisableChanged) | All Users' Text Message Sending Disabled in Room Event |
| [TUIRoomEvents.onRoomMaxSeatCountChanged](https://www.tencentcloud.com/document/product/647/54884#onRoomMaxSeatCountChanged) | Maximum number of microphone slots in the room modification event |
| [TUIRoomEvents.onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/54884#onRemoteUserEnterRoom) | Remote user Entered room event |
| [TUIRoomEvents.onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/54884#onRemoteUserLeaveRoom) | Remote user leaving room event |
| [TUIRoomEvents.onUserRoleChanged](https://www.tencentcloud.com/document/product/647/54884#onUserRoleChanged) | Role change event |
| [TUIRoomEvents.onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/54884#onUserVideoStateChanged) | Video Status change event |
| [TUIRoomEvents.onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/54884#onUserAudioStateChanged) | Audio Status change event |
| [TUIRoomEvents.onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/54884#onSendMessageForUserDisableChanged) | Send message status event |
| [TUIRoomEvents.onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/54884#onUserVoiceVolumeChanged) | Volume change event |
| [TUIRoomEvents.onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/54884#onUserNetworkQualityChanged) | Network quality change event |
| [TUIRoomEvents.onSeatListChanged](https://www.tencentcloud.com/document/product/647/54884#onSeatListChanged) | Mic position list change event |
| [TUIRoomEvents.onKickedOffSeat](https://www.tencentcloud.com/document/product/647/54884#onKickedOffSeat) | Kicked off the mic event |
| [TUIRoomEvents.onRequestReceived](https://www.tencentcloud.com/document/product/647/54884#onRequestReceived) | Request received event |
| [TUIRoomEvents.onRequestCancelled](https://www.tencentcloud.com/document/product/647/54884#onRequestCancelled) | Request cancelled event |
| [TUIRoomEvents.onReceiveTextMessage](https://www.tencentcloud.com/document/product/647/54884#onReceiveTextMessage) | Receive text message event |
| [TUIRoomEvents.onReceiveCustomMessage](https://www.tencentcloud.com/document/product/647/54884#onReceiveCustomMessage) | Receive custom message event |
| [TUIRoomEvents.onDeviceChange](https://www.tencentcloud.com/document/product/647/54884#onDeviceChange) | Device change event |
| [TUIRoomEvents.onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/54884#onUserScreenCaptureStopped) | Screen sharing stopped event When a user uses the built-in browser's stop sharing button to end Screen Sharing, the user will receive the 'onUserScreenCaptureStopped' event to modify the Sharing status. |


---
*Source: [https://trtc.io/document/54882](https://trtc.io/document/54882)*
