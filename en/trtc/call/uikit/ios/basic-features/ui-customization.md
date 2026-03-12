# UI Customization

This document describes how to customize the UI of `TUICallKit` and provides two schemes for customization: **slight UI adjustment** and **custom UI implementation**.

## Scheme 1. Slight UI Adjustment

You can adjust the UI of `TUICallKit` by directly modifying the UI source code in the `iOS/TUICallKit-Swift` folder in [tencentyun/TUICallKit](https://github.com/tencentyun/TUICalling).

**Replacing icons:** You can directly replace the icons in the `Resources\\Assets.xcassets` folder to customize the color tone and style of all the icons in your application. When you replace an icon, make sure the filename is the same as the original icon.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ecdc97aa0a9611eea359525400088f3a.png)

**Replacing ringtones:** You can replace ringtones by replacing the three audio files in the `Resources\\AudioFile` folder.

| Filename | Description |
| --- | --- |
| phone_dialing.m4a | The sound of making a call. |
| phone_hangup.mp3 | The sound of being hung up. |
| phone_ringing.flac | The ringtone for incoming calls. |

**Replacing text:** You can modify the strings on the video call UI by modifying the `Localized.strings` file in `zh-Hans.lproj ` and `en.lproj`.

## Scheme 2. Custom UI Implementation

The entire call feature of `TUICallKit` is implemented based on the UI-less component `TUICallEngine`. You can delete the `tuicallkit` folder and implement your own UIs based entirely on `TUICallEngine`.

### TUICallEngine

`TUICallEngine` is the underlying API of the entire `TUICallKit` component. It provides key APIs such as APIs for making, answering, declining, and hanging up one-to-one audio/video and group calls and device operations.

| API | Description |
| --- | --- |
| [createInstance](https://www.tencentcloud.com/document/product/647/51012#createInstance) | Create a TUICallEngine instance (singleton). |
| [destroyInstance](https://www.tencentcloud.com/document/product/647/51012#destroyInstance) | Destroy TUICallEngine instance (singleton). |
| [Init](https://www.tencentcloud.com/document/product/647/51012#Init) | Authenticates the basic audio/video call capabilities. |
| [addObserver](https://www.tencentcloud.com/document/product/647/51012#addObserver) | Add listener. |
| [removeObserver](https://www.tencentcloud.com/document/product/647/51012#removeObserver) | Remove listener. |
| [calls](https://www.tencentcloud.com/document/product/647/51012#calls) | Initiate a one-to-one or multi-person call |
| [join](https://www.tencentcloud.com/document/product/647/51012#join) | Proactively join a call |
| [accept](https://www.tencentcloud.com/document/product/647/51012#accept) | Accept call. |
| [reject](https://www.tencentcloud.com/document/product/647/51012#reject) | Reject call. |
| [hangup](https://www.tencentcloud.com/document/product/647/51012#hangup) | Hang up call. |
| [ignore](https://www.tencentcloud.com/document/product/647/51012#hangup) | Ignore call. |
| [inviteUser](https://www.tencentcloud.com/document/product/647/51012#inviteUser) | Invite users to the current call. |
| [switchCallMediaType](https://www.tencentcloud.com/document/product/647/51012#switchCallMediaType) | Switch the call media type, such as from video call to audio call. |
| [startRemoteView](https://www.tencentcloud.com/document/product/647/51012#startRemoteView) | Subscribe to the video stream of a remote user. |
| [stopRemoteView](https://www.tencentcloud.com/document/product/647/51012#stopRemoteView) | Unsubscribe from the video stream of a remote user. |
| [openCamera](https://www.tencentcloud.com/document/product/647/51012#openCamera) | Turn on the camera. |
| [closeCamera](https://www.tencentcloud.com/document/product/647/51012#closeCamera) | Turn off the camera. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/51012#switchCamera) | Switch camera. |
| [openMicrophone](https://www.tencentcloud.com/document/product/647/51012#openMicrophone) | Enable microphone. |
| [closeMicrophone](https://www.tencentcloud.com/document/product/647/51012#closeMicrophone) | Disable the microphone. |
| [selectAudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/51012#selectAudioPlaybackDevice) | Select the audio playback device (Earpiece/Speakerphone). |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/51012#setSelfInfo) | Set the user's profile picture and nickname. |
| [enableMultiDeviceAbility](https://www.tencentcloud.com/document/product/647/51012#enableMultiDeviceAbility) | Sets whether to enable multi-device login for TUICallEngine (supported by the [Group Call package](https://trtc.io/document/54632?platform=ios&product=call&menulabel=web)). |
| [setVideoRenderParams](https://www.tencentcloud.com/document/product/647/51012#setVideoRenderParams) | Set the rendering mode of video. |
| [setVideoEncoderParams](https://www.tencentcloud.com/document/product/647/51012#setVideoEncoderParams) | Set the encoding parameters of video encoder. |
| [getTRTCCloudInstance](https://www.tencentcloud.com/document/product/647/51012#getTRTCCloudInstance) | Advanced features. |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/51012#setBeautyLevel) | Set beauty level, support turning off default beauty. |

### TUICallObserver

`TUICallObserver` is the callback even class of `TUICallEngine`. You can use it to listen on the desired callback events.

| API | Description |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/51013#onError) | An error occurred during the call. |
| [onCallReceived](https://www.tencentcloud.com/document/product/647/51013#onCallReceived) | A call was received. |
| [onCallCancelled](https://www.tencentcloud.com/document/product/647/51013#onCallCancelled) | The call was canceled. |
| [onCallBegin](https://www.tencentcloud.com/document/product/647/51013#onCallBegin) | The call was connected. |
| [onCallEnd](https://www.tencentcloud.com/document/product/647/51013#onCallEnd) | The call ended. |
| [onCallMediaTypeChanged](https://www.tencentcloud.com/document/product/647/51013#onCallMediaTypeChanged) | The call type changed. |
| [onUserReject](https://www.tencentcloud.com/document/product/647/51013#onUserReject) | A user declined the call. |
| [onUserNoResponse](https://www.tencentcloud.com/document/product/647/51013#onUserNoResponse) | A user didn't respond. |
| [onUserLineBusy](https://www.tencentcloud.com/document/product/647/51013#onUserLineBusy) | A user was busy. |
| [onUserJoin](https://www.tencentcloud.com/document/product/647/51013#onUserJoin) | A user joined the call. |
| [onUserLeave](https://www.tencentcloud.com/document/product/647/51013#onUserLeave) | A user left the call. |
| [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/51013#onUserVideoAvailable) | Whether a user has a video stream. |
| [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/51013#onUserAudioAvailable) | Whether a user has an audio stream. |
| [onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/51013#onUserVoiceVolumeChanged) | The volume levels of all users. |
| [onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/51013#onUserNetworkQualityChanged) | The network quality of all users. |
| [onKickedOffline](https://www.tencentcloud.com/document/product/647/51013#onKickedOffline) | The current user was kicked offline. |
| [onUserSigExpired](https://www.tencentcloud.com/document/product/647/51013#onUserSigExpired) | The user sig is expired. |

### Definitions of key classes

| API | Description |
| --- | --- |
| [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54902#TUICallMediaType) | Call media type, Enumeration type: Unknown, Video, and Audio. |
| [TUICallRole](https://www.tencentcloud.com/document/product/647/54902#TUICallRole) | Call role, Enumeration type: None, Call, and Called. |
| [TUICallStatus](https://www.tencentcloud.com/document/product/647/54902#TUICallStatus) | Call status, Enumeration type: None, Waiting, and Accept. |
| [TUIRoomId](https://www.tencentcloud.com/document/product/647/54902#TUIRoomId) | The room ID, which can be a number or string. |
| [TUICamera](https://www.tencentcloud.com/document/product/647/54902#TUICamera) | The camera type. Enumeration type: Front camera and Back camera. |
| [TUIAudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/54902#TUIAudioPlaybackDevice) | The audio playback device type. Enumeration type: Earpiece and Speakerphone. |
| [TUINetworkQualityInfo](https://www.tencentcloud.com/document/product/647/54902#TUINetworkQualityInfo) | The current network quality. |


---
*Source: [https://trtc.io/document/50996](https://trtc.io/document/50996)*
