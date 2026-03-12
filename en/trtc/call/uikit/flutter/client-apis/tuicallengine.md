# TUICallEngine

## TUICallEngine APIs

`TUICallEngine` is an audio/video call component that **does not include UI elements**. If `TUICallKit` does not meet your requirements, you can use the APIs of `TUICallEngine` to customize your project.

## Overview

| API | Description |
| --- | --- |
| [init](https://www.tencentcloud.com/document/product/647/54907#init) | Authenticates the basic audio/video call capabilities. |
|  |  |
| [unInit](#unInit) | The destructor function, which releases resources used by TUICallEngine. |
| [addObserver](https://www.tencentcloud.com/document/product/647/54907#addObserver) | Registers an event listener. |
| [removeObserver](https://www.tencentcloud.com/document/product/647/54907#removeObserver) | Unregisters an event listener. |
| [calls](https://www.tencentcloud.com/document/product/647/54907#calls) | Start a call. |
| [accept](https://www.tencentcloud.com/document/product/647/54907#accept) | Accepts a call. |
| [reject](https://www.tencentcloud.com/document/product/647/54907#reject) | Rejects a call. |
| [hangup](https://www.tencentcloud.com/document/product/647/54907#hangup) | Ends a call. |
| [ignore](https://www.tencentcloud.com/document/product/647/54907#ignore) | Ignores a call. |
| [inviteUser](https://www.tencentcloud.com/document/product/647/54907#inviteUser) | Invite others to join the call. |
| [join](https://www.tencentcloud.com/document/product/647/54907#join) | Join the call. |
| [startRemoteView](https://www.tencentcloud.com/document/product/647/54907#startRemoteView) | Subscribes to the video stream of a remote user. |
| [stopRemoteView](https://www.tencentcloud.com/document/product/647/54907#stopRemoteView) | Unsubscribes from the video stream of a remote user. |
| [openCamera](https://www.tencentcloud.com/document/product/647/54907#openCamera) | Turns the camera on. |
| [closeCamera](https://www.tencentcloud.com/document/product/647/54907#closeCamera) | Turns the camera off. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/54907#switchCamera) | Switches between the front and rear cameras. |
| [openMicrophone](https://www.tencentcloud.com/document/product/647/54907#openMicrophone) | Turns the mic on. |
| [closeMicrophone](https://www.tencentcloud.com/document/product/647/54907#closeMicrophone) | Turns the mic off. |
| [selectAudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/54907#selectAudioPlaybackDevice) | Selects the audio playback device (receiver or speaker). |
| [setSelfInfo](#setSelfInfo) | Sets the alias and profile photo. |
| [enableMultiDeviceAbility](https://www.tencentcloud.com/document/product/647/54907#enableMultiDeviceAbility) | Sets whether to enable multi-device login for TUICallEngine (supported by the premium package). |
| [setVideoRenderParams](https://www.tencentcloud.com/document/product/647/54907#setVideoRenderParams) | Set the rendering mode of video image. |
| [setVideoEncoderParams](https://www.tencentcloud.com/document/product/647/54907#setVideoEncoderParams) | Set the encoding parameters of video encoder. |
| [setBlurBackground](https://www.tencentcloud.com/document/product/647/54907#setBlurBackground) | Set Blurry Video Effect |
| [setVirtualBackground](https://www.tencentcloud.com/document/product/647/54907#setVirtualBackground) | Set Virtual Background Image |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/54907#setBeautyLevel) | Set beauty level, support turning off default beauty. |

## Details

### init

This API is used to initialize `TUICallEngine`. Call it to authenticate the call service and perform other required actions before you call other APIs.

```
Future<TUIResult> init(int sdkAppID, String userId, String userSig)
```

### unInit

The destructor function, which releases resources used by TUICallEngine.

```
Future<TUIResult> unInit()
```

### addObserver

This API is used to register an event listener to listen for `TUICallObserver` events.

```
Future<void> addObserver(TUICallObserver observer)
```

### removeObserver

This API is used to unregister an event listener.

```
Future<void> removeObserver(TUICallObserver observer)
```

### calls

Initiate a call. **Supported by v2.9+.**

```
Future<TUIResult> calls(List<String> userIdList, TUICallMediaType mediaType, TUICallParams params)
```

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | List<String> | The target user IDs. |
| callMediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | The call type, which can be video or audio. |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams) | An additional parameter. such as roomID, call timeout, offline push info, etc |

### accept

This API is used to accept a call. After receiving the `onCallReceived()` callback, you can call this API to accept the call.

```
Future<TUIResult> accept()
```

### reject

This API is used to reject a call. After receiving the `onCallReceived()` callback, you can call this API to reject the call.

```
Future<TUIResult> reject()
```

### ignore

This API is used to ignore a call. After receiving the `onCallReceived()`, you can call this API to ignore the call. The caller will receive the `onUserLineBusy` callback.

Note: If your project involves live streaming or conferencing, you can also use this API to implement the âin a meetingâ or âon airâ feature.

```
Future<TUIResult> ignore()
```

### hangup

This API is used to end a call.

```
Future<TUIResult> hangup()
```

### inviteUser

This API is used to invite users to the current group call.

This API is called by a participant of a group call to invite new users.

```
Future<void> iniviteUser(List<String> userIdList, TUICallParams params, TUIValueCallback callback)
```

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | List<String> | The target user IDs. |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams) | An additional parameter. such as roomID, call timeout, offline push info, etc. |

### join

Actively join the call. **Supported by v2.9+.**

```
Future<void> join(String callId)
```

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | Unique ID for this call. |

### startRemoteView

This API is used to set the view object to display a remote video.

```
Future<void> startRemoteView(String userId, intviewId)
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |
| intviewId | int | The ID of the widget in the video rendering screen |

### stopRemoteView

This API is used to unsubscribe from the video stream of a remote user.

```
Future<void> stopRemoteView(String userId)
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |

### openCamera

This API is used to turn the camera on.

```
Future<TUIResult> openCamera(TUICamera camera, int? viewId)
```

| Parameter | Type | Description |
| --- | --- | --- |
| camera | [TUICamera](https://www.tencentcloud.com/document/product/647/54909#TUICamera) | The front or rear camera. |
| viewId | int | The ID of the widget in the video rendering screen |

### closeCamera

This API is used to turn the camera off.

```
Future<void> closeCamera()
```

### switchCamera

This API is used to switch between the front and rear cameras.

```
Future<void> switchCamera(TUICamera camera)
```

| Parameter | Type | Description |
| --- | --- | --- |
| camera | [TUICamera](https://www.tencentcloud.com/document/product/647/54909#TUICamera) | The front or rear camera. |

### openMicrophone

This API is used to turn the mic on.

```
Future<TUIResult> openMicrophone()
```

### closeMicrophone

This API is used to turn the mic off.

```
Future<void> closeMicrophone()
```

### selectAudioPlaybackDevice

This API is used to select the audio playback device (receiver or speaker). In call scenarios, you can use this API to turn on/off hands-free mode.

```
Future<void> selectAudioPlaybackDevice(TUIAudioPlaybackDevice device)
```

| Parameter | Type | Description |
| --- | --- | --- |
| device | [TUIAudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/54909#TUIAudioPlaybackDevice) | The speaker or receiver. |

### setSelfInfo

This API is used to set the alias and profile photo. The alias cannot exceed 500 bytes, and the profile photo is specified by a URL.

```
Future<TUIResult> setSelfInfo(String nickname, String avatar)
```

### enableMultiDeviceAbility

This API is used to set whether to enable multi-device login for `TUICallEngine` (supported by the premium package).

```
Future<TUIResult> enableMultiDeviceAbility(bool enable)
```

### setVideoRenderParams

Set the rendering mode of video image.

```
Future<TUIResult> setVideoRenderParams(String userId, VideoRenderParams params)
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |
| params | [VideoRenderParams](https://www.tencentcloud.com/document/product/647/54909#VideoRenderParams) | Video render parameters. |

### setVideoEncoderParams

Set the encoding parameters of video encoder.

This setting can determine the quality of image viewed by remote users, which is also the image quality of on-cloud recording files.

```
Future<TUIResult> setVideoEncoderParams(VideoEncoderParams params)
```

| Parameter | Type | Description |
| --- | --- | --- |
| params | [VideoEncoderParams](https://www.tencentcloud.com/document/product/647/54909#VideoEncoderParams) | Video encoding parameters |

### setBeautyLevel

Set beauty level, support turning off default beauty.

```
Future<TUIResult> setBeautyLevel(double level)
```

| Parameter | Type | Description |
| --- | --- | --- |
| level | double | Beauty level, range 0.0 to 9.0. |

### setBlurBackground

Setting Blurry Video Effect.

```
void setBlurBackground(int level, Function(int code, String message)? errorCallback)
```

The parameters are described below:

| Parameter | Type | Meaning |
| --- | --- | --- |
| level | int | 0: Off, 1: Low, 2: Medium, 3: High. |

### setVirtualBackground

Setting Virtual Background Image.

```
void setVirtualBackground(String imagePath, Function(int code, String message)? errorCallback)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| imagePath | String | Image Filename. The file needs to be added to the assets of the main project. |

## Deprecated interfaces

### call

This API is used to make a (one-to-one) call.

> **Noteï¼**This interface has been deprecated in v2.9+. It is recommended to use the calls interface instead.

```
Future<TUIResult> call(String userId, TUICallMediaType mediaType, TUICallParams params)
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | The call type, which can be video or audio. |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams) | An additional parameter, such as roomID, call timeout, offline push info, etc. |

### groupCall

This API is used to make a group call.

Before making a group call, you need to create an IM group first.

> **Noteï¼**This interface has been deprecated in v2.9+. It is recommended to use the calls interface instead.

```
Future<TUIResult> groupCall(String groupId, List<String> userIdList, TUICallMediaType mediaType, TUICallParams params)
```

| Parameter | Type | Description |
| --- | --- | --- |
| groupId | String | The group ID. |
| userIdList | List<String> | The target user IDs. |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | The call type, which can be video or audio. |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams) | An additional parameter. such as roomID, call timeout, offline push info, etc. |

### joinInGroupCall

This API is used to join a group call.

This API is called by a group member to join the groupâs call.

> **Noteï¼**This interface has been deprecated in v2.9+. It is recommended to use the join interface instead.

```
Future<TUIResult> joinInGroupCall(TUIRoomId roomId, String groupId, TUICallMediaType mediaType)
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | [TUIRoomId](https://www.tencentcloud.com/document/product/647/54909#TUIRoomId) | The room ID. |
| groupId | String | The group ID. |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | The call type, which can be video or audio. |

### switchCallMediaType

This API is used to change the call type.

```
Future<void> switchCallMediaType(TUICallMediaType mediaType)
```

| Parameter | Type | Description |
| --- | --- | --- |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | The call type, which can be video or audio. |


---
*Source: [https://trtc.io/document/54907](https://trtc.io/document/54907)*
