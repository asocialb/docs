# API Overview

## TUICallKit (UI Included)

TUICallKit is an audio/video call component that **includes UI elements**. You can use its APIs to quickly implement an audio/video call application similar to WeChat.

| API | Description |
| --- | --- |
| [login](https://www.tencentcloud.com/document/product/647/54906#login) | Log in |
| [logout](#logout) | Sign out |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54906#setSelfInfo) | Sets the user nickname and profile photo. |
| [calls](https://www.tencentcloud.com/document/product/647/54906#calls) | Start a call. |
| [join](https://www.tencentcloud.com/document/product/647/54906#join) | Join the call. |
| [enableMuteMode](https://www.tencentcloud.com/document/product/647/54906#enableMuteMode) | Sets whether to turn on the mute mode. |
| [enableFloatWindow](https://www.tencentcloud.com/document/product/647/54906#enableFloatWindow) | Sets whether to enable floating windows. |
| [setCallingBell](https://www.tencentcloud.com/document/product/647/54906#setCallingBell) | Custom ringtone. |
| [enableVirtualBackground](https://www.tencentcloud.com/document/product/647/54906#6f0d0f68-18bd-4a16-a074-6d7288dcd6dd) | Turn On/Off the Virtual Background feature |

## TUICallEngine (No UI)

`TUICallEngine` is an audio/video call component that **does not include UI elements**. If `TUICallKit` does not meet your requirements, you can use the APIs of `TUICallEngine` to customize your project.

| API | Description |
| --- | --- |
| [init](https://www.tencentcloud.com/document/product/647/54907#init) | Authenticates the basic audio/video call capabilities. |
|  |  |
| [unInit](https://www.tencentcloud.com/document/product/647/54907#unInit) | The destructor function, which releases resources used by TUICallEngine. |
| [addObserver](https://www.tencentcloud.com/document/product/647/54907#addobserver) | Registers an event listener. |
| [removeObserver](https://www.tencentcloud.com/document/product/647/54907#removeobserver) | Unregisters an event listener. |
| [calls](https://www.tencentcloud.com/document/product/647/54907#calls) | Start a call. |
| [accept](https://www.tencentcloud.com/document/product/647/54907#accept) | Accepts a call. |
| [reject](https://www.tencentcloud.com/document/product/647/54907#reject) | Rejects a call. |
| [hangup](https://www.tencentcloud.com/document/product/647/54907#hangup) | Ends a call. |
| [ignore](https://www.tencentcloud.com/document/product/647/54907#ignore) | Ignores a call. |
| [inviteUser](https://www.tencentcloud.com/document/product/647/54907#inviteuser) | Invite others to join the call. |
| [join](https://www.tencentcloud.com/document/product/647/54907#join) | Join the call. |
| [switchCallMediaType](https://www.tencentcloud.com/document/product/647/54907#switchcallmediatype) | Changes the call type, for example, from video call to audio call. |
| [startRemoteView](https://www.tencentcloud.com/document/product/647/54907#startremoteview) | Subscribes to the video stream of a remote user. |
| [stopRemoteView](https://www.tencentcloud.com/document/product/647/54907#stopremoteview) | Unsubscribes from the video stream of a remote user. |
| [openCamera](https://www.tencentcloud.com/document/product/647/54907#opencamera) | Turns the camera on. |
| [closeCamera](https://www.tencentcloud.com/document/product/647/54907#closecamera) | Turns the camera off. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/54907#switchcamera) | Switches between the front and rear cameras. |
| [openMicrophone](https://www.tencentcloud.com/document/product/647/54907#openmicrophone) | Turns the mic on. |
| [closeMicrophone](https://www.tencentcloud.com/document/product/647/54907#closemicrophone) | Turns the mic off. |
| [selectAudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/54907#selectaudioplaybackdevice) | Selects the audio playback device (receiver or speaker). |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54907#setselfinfo) | Sets the alias and profile photo. |
| [enableMultiDeviceAbility](https://www.tencentcloud.com/document/product/647/54907#enablemultideviceability) | Sets whether to enable multi-device login for TUICallEngine (supported by the premium package). |
| [setVideoRenderParams](https://www.tencentcloud.com/document/product/647/54907#setVideoRenderParams) | Set the rendering mode of video image. |
| [setVideoEncoderParams](https://www.tencentcloud.com/document/product/647/54907#setVideoEncoderParams) | Set the encoding parameters of video encoder. |
| [queryRecentCalls](https://www.tencentcloud.com/document/product/647/54907#queryRecentCalls) | Query call record. |
| [deleteRecordCalls](https://www.tencentcloud.com/document/product/647/54907#deleteRecordCalls) | Delete call record. |
| [setBlurBackground](https://www.tencentcloud.com/document/product/647/54907#a84f7a0a-6a2a-47be-9a2b-dba02873f43a) | Set Blurry Video Effect |
| [setVirtualBackground](https://www.tencentcloud.com/document/product/647/54907#9f5e78e9-0d3b-4534-b8db-3435db17d448) | Set Virtual Background Image |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/54907#setBeautyLevel) | Set beauty level, support turning off default beauty. |

## TUICallObserver

`TUICallObserver` is the callback class of `TUICallEngine`. You can use it to listen for events.

| API | Description |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/54908#onError) | An error occurred during the call. |
| [onUserInviting](https://www.tencentcloud.com/document/product/647/54908#onUserInviting) | Callback when a user is invited to join a call. |
| [onCallReceived](https://www.tencentcloud.com/document/product/647/54908#onCallReceived) | A call invitation was received. |
| [onCallNotConnected](https://www.tencentcloud.com/document/product/647/54908#onCallNotConnected) | Callback for call cancellation |
| [onCallBegin](https://www.tencentcloud.com/document/product/647/54908#onCallBegin) | The call was connected. |
| [onCallEnd](https://www.tencentcloud.com/document/product/647/54908#onCallEnd) | The call ended. |
| [onCallMediaTypeChanged](https://www.tencentcloud.com/document/product/647/54908#onCallMediaTypeChanged) | The call type changed. |
| [onUserReject](https://www.tencentcloud.com/document/product/647/54908#onUserReject) | A user declined the call. |
| [onUserNoResponse](https://www.tencentcloud.com/document/product/647/54908#onUserNoResponse) | A user didn't respond. |
| [onUserLineBusy](https://www.tencentcloud.com/document/product/647/54908#onUserLineBusy) | A user was busy. |
| [onUserJoin](https://www.tencentcloud.com/document/product/647/54908#onUserJoin) | A user joined the call. |
| [onUserLeave](https://www.tencentcloud.com/document/product/647/54908#onUserLeave) | A user left the call. |
| [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/54908#onUserVideoAvailable) | Whether a user has a video stream. |
| [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/54908#onUserAudioAvailable) | Whether a user has an audio stream. |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/54908#onUserVoiceVolumeChanged) | The volume levels of all users. |
| [onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/54908#onUserNetworkQualityChanged) | The network quality of all users. |
| [onKickedOffline](https://www.tencentcloud.com/document/product/647/54908#onKickedOffline) | The current user is kicked offline |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/54908#onUserSigExpired) | Ticket expires while online |

## Key Type Definitions

| Type | Description |
| --- | --- |
| [VideoEncoderParams](https://www.tencentcloud.com/document/product/647/54909#VideoEncoderParams) | Video encoding parameters. |
| [VideoRenderParams](https://www.tencentcloud.com/document/product/647/54909#VideoRenderParams) | Video render parameters. |
| [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Call media type. |
| [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams) | Call extension parameters. |
| [TUICamera](https://www.tencentcloud.com/document/product/647/54909#TUICamera) | Camera type. |
| [TUIAudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/54909#TUIAudioPlaybackDevice) | Audio playback device. |
| [TUIRoomId](https://www.tencentcloud.com/document/product/647/54909#TUIRoomId) | Room ID for audio and video in a call. |


---
*Source: [https://trtc.io/document/54905](https://trtc.io/document/54905)*
