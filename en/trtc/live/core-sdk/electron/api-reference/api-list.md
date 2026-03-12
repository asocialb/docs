# API List

## TUIRoomEngine (non-UI API)

### TUIRoomEngine Static Methods

| API | Description |
| --- | --- |
| [once](https://www.tencentcloud.com/document/product/647/64342#once) | Listen for the TUIRoomEngine ready event.**Note: All methods other than TUIRoomEngine.init must be executed after the TUIRoomEngine ready event is received and the TUIRoomEngine.init method is successfully executed.** |
| [login](https://www.tencentcloud.com/document/product/647/64342#login) | Log in to TUIRoomEngine |
| [logout](https://www.tencentcloud.com/document/product/647/64342#logout) | Log out of TUIRoomEngine |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/64342#setSelfInfo) | Set basic information of the current user (user name, user avatar) |
| [getSelfInfo](https://www.tencentcloud.com/document/product/647/64342#getSelfInfo) | Get basic information of the current user (user name, user avatar) |
| [getDeviceManager](https://www.tencentcloud.com/document/product/647/64342#getDeviceManager) | Get device manager |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/64342#getAudioEffectManager) | Get audio effect manager |
| [getMediaMixingManager](https://www.tencentcloud.com/document/product/647/64342#getMediaMixingManager) | Get media source mixing manager |
| [getVideoEffectPluginManager](https://www.tencentcloud.com/document/product/647/64342#getVideoEffectPluginManager) | Get video effect plugin manager |

### roomEngine Room Management API

| API | Description |
| --- | --- |
| [createRoom](https://www.tencentcloud.com/document/product/647/64342#createRoom) | Create a room |
| [enterRoom](https://www.tencentcloud.com/document/product/647/64342#enterRoom) | Enter a room |
| [destroyRoom](https://www.tencentcloud.com/document/product/647/64342#destroyRoom) | Destroy a room |
| [exitRoom](https://www.tencentcloud.com/document/product/647/64342#exitRoom) | Exit a room |
| [fetchRoomInfo](https://www.tencentcloud.com/document/product/647/64342#fetchRoomInfo) | Fetch room information |
| [updateRoomNameByAdmin](https://www.tencentcloud.com/document/product/647/64342#updateRoomNameByAdmin) | Update room name (Only available to room owners or administrators) |
| [updateRoomSeatModeByAdmin](https://www.tencentcloud.com/document/product/647/64342#updateRoomSeatModeByAdmin) | Update room seat mode (Only available to room owners or administrators) |

### roomEngine Audio and Video API

| API | Description |
| --- | --- |
| [setLocalVideoView](https://www.tencentcloud.com/document/product/647/64342#setLocalVideoView) | Set the HTML element where to play local camera video stream |
| [openLocalCamera](https://www.tencentcloud.com/document/product/647/64342#openLocalCamera) | Open local camera |
| [closeLocalCamera](https://www.tencentcloud.com/document/product/647/64342#closeLocalCamera) | Close local camera |
| [startPushLocalVideo](https://www.tencentcloud.com/document/product/647/64342#startPushLocalVideo) | Start pushing the local video stream to the remote end |
| [stopPushLocalVideo](https://www.tencentcloud.com/document/product/647/64342#stopPushLocalVideo) | Stop pushing the local video stream to the remote end |
| [updateVideoQuality](https://www.tencentcloud.com/document/product/647/64342#updateVideoQuality) | Set local video parameters |
| [updateVideoQualityEx](https://www.tencentcloud.com/document/product/647/64342#updateVideoQualityEx) | Set local video encoding parameters |
| [setVideoResolutionMode](https://www.tencentcloud.com/document/product/647/64342#setVideoResolutionMode) | Set the resolution mode of the local video stream |
| [openLocalMicrophone](https://www.tencentcloud.com/document/product/647/64342#openLocalMicrophone) | Open local microphone |
| [closeLocalMicrophone](https://www.tencentcloud.com/document/product/647/64342#closeLocalMicrophone) | Close local microphone |
| [updateAudioQuality](https://www.tencentcloud.com/document/product/647/64342#updateAudioQuality) | Set local audio parameters |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/64342#muteLocalAudio) | Stop pushing the local audio stream to the remote end |
| [unmuteLocalAudio](https://www.tencentcloud.com/document/product/647/64342#unmuteLocalAudio) | Start pushing the local audio stream to the remote end |
| [setRemoteVideoView](https://www.tencentcloud.com/document/product/647/64342#setRemoteVideoView) | Set the HTML element where to play the remote video stream |
| [startPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/64342#startPlayRemoteVideo) | Start playing the remote user's video stream |
| [stopPlayRemoteVideo](https://www.tencentcloud.com/document/product/647/64342#stopPlayRemoteVideo) | Stop playing the remote user's video stream |
| [muteRemoteAudioStream](https://www.tencentcloud.com/document/product/647/64342#muteRemoteAudioStream) | Stop the remote user's audio stream |

### roomEngine Screen/Window Sharing API

| API | Description |
| --- | --- |
| [startScreenSharingElectron](https://www.tencentcloud.com/document/product/647/64342#startScreenSharingElectron) | Start screen or window sharing |
| [stopScreenSharingElectron](https://www.tencentcloud.com/document/product/647/64342#stopScreenSharingElectron) | Stop screen or window sharing |
| [getScreenSharingTarget](https://www.tencentcloud.com/document/product/647/64342#getScreenSharingTarget) | Get the screens and windows to be shared |
| [selectScreenSharingTarget](https://www.tencentcloud.com/document/product/647/64342#selectScreenSharingTarget) | Select the screen or window to share |

### roomEngine Member Management API

| API | Description |
| --- | --- |
| [getUserList](https://www.tencentcloud.com/document/product/647/64342#getUserList) | Get users list |
| [getUserInfo](https://www.tencentcloud.com/document/product/647/64342#getUserInfo) | Get user detail information |
| [changeUserRole](https://www.tencentcloud.com/document/product/647/64342#changeUserRole) | Change user role |
| [kickRemoteUserOutOfRoom](https://www.tencentcloud.com/document/product/647/64342#kickRemoteUserOutOfRoom) | Kick user out of current room |
| [cancelRequest](https://www.tencentcloud.com/document/product/647/64342#cancelRequest) | Cancel a request already sent |
| [responseRemoteRequest](https://www.tencentcloud.com/document/product/647/64342#responseRemoteRequest) | Response to remote user request |
| [disableSendingMessageByAdmin](https://www.tencentcloud.com/document/product/647/64342#disableSendingMessageByAdmin) | Disable/Enable instant message chat |

### roomEngine Seat Management API

| API | Description |
| --- | --- |
| [getSeatList](https://www.tencentcloud.com/document/product/647/64342#getSeatList) | Get seats information |
| [lockSeatByAdmin](https://www.tencentcloud.com/document/product/647/64342#lockSeatByAdmin) | Lock a seat (only available to room owner and administrators) |
| [takeSeat](https://www.tencentcloud.com/document/product/647/64342#takeSeat) | Take a seat |
| [leaveSeat](https://www.tencentcloud.com/document/product/647/64342#leaveSeat) | Release a seat |
| [takeUserOnSeatByAdmin](https://www.tencentcloud.com/document/product/647/64342#takeUserOnSeatByAdmin) | Invite someone else to speak (only available to room owner and administrators) |
| [kickUserOffSeatByAdmin](https://www.tencentcloud.com/document/product/647/64342#kickUserOffSeatByAdmin) | Kick someone off the seat (only available to room owner and administrators) |
| [getSeatApplicationList](https://www.tencentcloud.com/document/product/647/64342#getSeatApplicationList) | Get the list of speaking requests |

### roomEngine Event Listening API

| API | Description |
| --- | --- |
| [on](https://www.tencentcloud.com/document/product/647/64342#on) | Add [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/64350) event listener |
| [off](https://www.tencentcloud.com/document/product/647/64342#off) | Remove [TUIRoomEvents](https://www.tencentcloud.com/document/product/647/64350) evnet listener |

### roomEngine Malicious API

| API | Description |
| --- | --- |
| [getTRTCCloud](https://www.tencentcloud.com/document/product/647/64342#getTRTCCloud) | Get TRTCCloud instance |
| [getTIM](https://www.tencentcloud.com/document/product/647/64342#getTIM) | Get TIM/Chat instance |

## Event Name Definition

TUIRoomEvent is an enum type of all the events supported by TUIRoomEngine.

| EVENT | Description |
| --- | --- |
| [TUIRoomEvents.onError](https://www.tencentcloud.com/document/product/647/64350#onerror) | Error event |
| [TUIRoomEvents.onKickedOutOfRoom](https://www.tencentcloud.com/document/product/647/64350#onkickedoutofroom) | Kick out of room event |
| [TUIRoomEvents.onKickedOffSeat](https://www.tencentcloud.com/document/product/647/64350#onkickedoffseat) | Kick off seat event |
| [TUIRoomEvents.onKickedOffLine](https://www.tencentcloud.com/document/product/647/64350#onkickedoffline) | Kick off line event |
| [TUIRoomEvents.onUserSigExpired](https://www.tencentcloud.com/document/product/647/64350#onusersigexpired) | userSig expired |
| [TUIRoomEvents.onRoomDismissed](https://www.tencentcloud.com/document/product/647/64350#onroomdismissed) | Room owner destroying room event |
| [TUIRoomEvents.onRoomNameChanged](https://www.tencentcloud.com/document/product/647/64350#onroomnamechanged) | Room name changed event |
| [TUIRoomEvents.onRoomInfoChanged](https://www.tencentcloud.com/document/product/647/64350#onroominfochanged) | Room information changed event |
| [TUIRoomEvents.onRoomSeatModeChanged](https://www.tencentcloud.com/document/product/647/64350#onroomseatmodechanged) | Seat mode change event |
| [TUIRoomEvents.onAllUserMicrophoneDisableChanged](https://www.tencentcloud.com/document/product/647/64350#onallusermicrophonedisablechanged) | Disable/Enable all user microphone event |
| [TUIRoomEvents.onSendMessageForAllUserDisableChanged](https://www.tencentcloud.com/document/product/647/64350#onsendmessageforalluserdisablechanged) | Disable/Enable all user instant message sending event |
| [TUIRoomEvents.onRoomMaxSeatCountChanged](https://www.tencentcloud.com/document/product/647/64350#onroommaxseatcountchanged) | The maximize seats number change event |
| [TUIRoomEvents.onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/64350#onremoteuserenterroom) | Remote user enter room event |
| [TUIRoomEvents.onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/64350#onremoteuserleaveroom) | Remote user leave room event |
| [TUIRoomEvents.onUserRoleChanged](https://www.tencentcloud.com/document/product/647/64350#onuserrolechanged) | User role changed event |
| [TUIRoomEvents.onUserVideoStateChanged](https://www.tencentcloud.com/document/product/647/64350#onuservideostatechanged) | User video stream changed event |
| [TUIRoomEvents.onUserAudioStateChanged](https://www.tencentcloud.com/document/product/647/64350#onuseraudiostatechanged) | User audio stream changed event |
| [TUIRoomEvents.onSendMessageForUserDisableChanged](https://www.tencentcloud.com/document/product/647/64350#onsendmessageforuserdisablechanged) | Disable/Enable a user instant message sending event |
| [TUIRoomEvents.onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/64350#onuservoicevolumechanged) | User voice volume changed event |
| [TUIRoomEvents.onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/64350#onusernetworkqualitychanged) | User network quality changed event |
| [TUIRoomEvents.onSeatControlEnabled](https://www.tencentcloud.com/document/product/647/64350#onseatcontrolenabled) | Seat control enabled/disabled event |
| [TUIRoomEvents.onSeatListChanged](https://www.tencentcloud.com/document/product/647/64350#onseatlistchanged) | Seats information changed event |
| [TUIRoomEvents.onRequestReceived](https://www.tencentcloud.com/document/product/647/64350#onrequestreceived) | Request received event |
| [TUIRoomEvents.onRequestProcessed](https://www.tencentcloud.com/document/product/647/64350#onrequestprocessed) | Request processed event |
| [TUIRoomEvents.onRequestCancelled](https://www.tencentcloud.com/document/product/647/64350#onrequestcancelled) | Request cancelled event |
| [TUIRoomEvents.onDeviceChange](https://www.tencentcloud.com/document/product/647/64350#ondevicechange) | Device changed event |
| [TUIRoomEvents.onUserScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/64350#onuserscreencapturestopped) | Screen sharing stopped event. |


---
*Source: [https://trtc.io/document/64341](https://trtc.io/document/64341)*
