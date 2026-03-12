# UI Customization

This document describes how to customize the UI of `TUICallKit` and provides two schemes for customization: **slight UI adjustment** and **custom UI implementation**.

## Scheme 1. Slight UI Adjustment

You can adjust the UI of `TUICallKit` by directly modifying the UI source code in the `Android/tuicallkit-kt` folder in [tencentyun/TUICallKit](https://github.com/Tencent-RTC/TUICallKit/tree/main/Android).

### Replacing icons

You can directly replace the icons in the `tuicallkit-kt/src/main/res/drawable-xxhdpi` folder to customize the color tone and style of all the icons in your application. When you replace an icon, make sure the filename is the same as the original icon.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b223f5e11e5411efbef6525400a8a0fb.png)

### Replacing ringtones

You can replace ringtones by replacing the three audio files in the `tuicallkit-kt/src/main/res/raw` folder.

| Filename | Description |
| --- | --- |
| phone_dialing.mp3 | The sound of making a call |
| phone_hangup.mp3 | The sound of being hung up |
| phone_ringing.mp3 | The ringtone for incoming calls |

### Replacing text

You can modify the strings on the video call UI by modifying the `strings.xml` file in `tuicallkit-kt/src/main/res/values-**/`.

## Scheme 2. Custom UI Implementation

The entire call feature of `TUICallKit` is implemented based on the UI-less component `TUICallEngine`. You can delete the `tuicallkit` folder and implement your own UIs based entirely on `TUICallEngine`.

### TUICallEngine

`TUICallEngine` is the underlying API of the entire `TUICallKit` component. It provides key APIs such as APIs for making, answering, declining, and hanging up one-to-one audio/video and group calls and device operations.

| API | Description |
| --- | --- |
| [createInstance](https://www.tencentcloud.com/document/product/647/51006#createInstance) | Creates a `TUICallEngine` instance (singleton mode). |
| [destroyInstance](https://www.tencentcloud.com/document/product/647/51006#destroyInstance) | Terminates a `TUICallEngine` instance (singleton mode). |
| [Init](https://www.tencentcloud.com/document/product/647/51006#Init) | Authenticates the basic audio/video call capabilities. |
| [addObserver](https://www.tencentcloud.com/document/product/647/51006#addObserver) | Registers an event listener. |
| [removeObserver](https://www.tencentcloud.com/document/product/647/51006#removeObserver) | Unregisters an event listener. |
| [calls](https://www.tencentcloud.com/document/product/647/51006#calls) | Initiate a one-to-one or multi-person call. |
| [join](https://www.tencentcloud.com/document/product/647/51006#join) | Proactively join a call. |
| [accept](https://www.tencentcloud.com/document/product/647/51006#accept) | Accepts a call. |
| [reject](https://www.tencentcloud.com/document/product/647/51006#reject) | Rejects a call. |
| [hangup](https://www.tencentcloud.com/document/product/647/51006#hangup) | Ends a call. |
| [ignore](https://www.tencentcloud.com/document/product/647/51006#ignore) | Ignores a call. |
| [inviteUser](https://www.tencentcloud.com/document/product/647/51006#inviteuser) | Invites users to the current group call. |
| [startRemoteView](https://www.tencentcloud.com/document/product/647/51006#startRemoteView) | Subscribes to the video stream of a remote user. |
| [stopRemoteView](https://www.tencentcloud.com/document/product/647/51006#stopRemoteView) | Unsubscribes from the video stream of a remote user. |
| [openCamera](https://www.tencentcloud.com/document/product/647/51006#openCamera) | Turns the camera on. |
| [closeCamera](https://www.tencentcloud.com/document/product/647/51006#closeCamera) | Turns the camera off. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/51006#switchCamera) | Switches between the front and rear cameras. |
| [openMicrophone](https://www.tencentcloud.com/document/product/647/51006#openMicrophone) | Turns the mic on. |
| [closeMicrophone](https://www.tencentcloud.com/document/product/647/51006#closeMicrophone) | Turns the mic off. |
| [selectAudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/51006#selectAudioPlaybackDevice) | Selects the audio playback device (receiver or speaker). |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/51006#setSelfInfo) | Sets the alias and profile photo. |
| [enableMultiDeviceAbility](https://www.tencentcloud.com/document/product/647/51006#enableMultiDeviceAbility) | Sets whether to enable multi-device login for `TUICallEngine` (supported by the [Group Call package](https://trtc.io/document/54632?platform=android&product=call&menulabel=web)). |
| [setVideoRenderParams](https://www.tencentcloud.com/document/product/647/51006#setVideoRenderParams) | Set the rendering mode of video image. |
| [setVideoEncoderParams](https://www.tencentcloud.com/document/product/647/51006#setVideoEncoderParams) | Set the encoding parameters of video encoder. |
| [getTRTCCloudInstance](https://www.tencentcloud.com/document/product/647/51006#getTRTCCloudInstance) | Advanced features. |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/51006#setBeautyLevel) | Set beauty level, support turning off default beauty. |

### TUICallObserver

`TUICallObserver` is the callback event class of `TUICallEngine`. You can use it to listen on the desired callback events.

| API | Description |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/51007#onError) | A call occurred during the call. |
| [onCallReceived](https://www.tencentcloud.com/document/product/647/51007#onCallReceived) | A call invitation was received. |
| [onCallBegin](https://www.tencentcloud.com/document/product/647/51007#onCallBegin) | The call was connected. |
| [onCallEnd](https://www.tencentcloud.com/document/product/647/51007#onCallEnd) | The call ended. |
| [onCallNotConnected](https://www.tencentcloud.com/document/product/647/51007#onCallNotConnected) | The call not connected. |
| [onUserReject](https://www.tencentcloud.com/document/product/647/51007#onUserReject) | A user declined the call. |
| [onUserNoResponse](https://www.tencentcloud.com/document/product/647/51007#onUserNoResponse) | A user didn't respond. |
| [onUserLineBusy](https://www.tencentcloud.com/document/product/647/51007#onUserLineBusy) | A user was busy. |
| [onUserInviting](https://www.tencentcloud.com/document/product/647/51007#onUserInviting) | A user is invited to join a call. |
| [onUserJoin](https://www.tencentcloud.com/document/product/647/51007#onUserJoin) | A user joined the call. |
| [onUserLeave](https://www.tencentcloud.com/document/product/647/51007#onUserLeave) | A user left the call. |
| [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/51007#onUserVideoAvailable) | Whether a user had a video stream. |
| [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/51007#onUserAudioAvailable) | Whether a user had an audio stream. |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/51007#onUserVoiceVolumeChanged) | The volume levels of all users. |
| [onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/51007#onUserNetworkQualityChanged) | The network quality of all users. |
| [onKickedOffline](https://www.tencentcloud.com/document/product/647/51007#onKickedOffline) | The current user was kicked offline. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/51007#onUserSigExpired) | The user sig is expired. |

## Definitions of Key Types

| API | Description |
| --- | --- |
| [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call media type. Enumeration: Video call and audio call. |
| [TUICallDefine.Role](https://www.tencentcloud.com/document/product/647/54900#Role) | The call role. Enumeration: Caller and callee. |
| [TUICallDefine.Status](https://www.tencentcloud.com/document/product/647/54900#Status) | The call status. Enumeration: Idle, waiting, and answering. |
| [TUICommonDefine.RoomId](https://www.tencentcloud.com/document/product/647/54900#RoomId) | The audio/video room ID, which can be a number or string. |
| [TUICommonDefine.Camera](https://www.tencentcloud.com/document/product/647/54900#Camera) | The camera type. Enumeration: Front camera and rear camera. |
| [TUICommonDefine.AudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/54900#AudioPlaybackDevice) | The audio playback device type. Enumeration: Speaker and receiver. |
| [TUICommonDefine.NetworkQualityInfo](https://www.tencentcloud.com/document/product/647/54900#NetworkQualityInfo) | The information of the current network quality. |


---
*Source: [https://trtc.io/document/50995](https://trtc.io/document/50995)*
