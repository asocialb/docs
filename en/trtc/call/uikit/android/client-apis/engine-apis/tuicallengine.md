# TUICallEngine

## TUICallEngine APIs

`TUICallEngine` is an audio/video call component that **does not include UI elements**. If `TUICallKit` does not meet your requirements, you can use the APIs of `TUICallEngine` to customize your project.

## Overview

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

## Details

### createInstance

This API is used to create a `TUICallEngine` singleton.

```
TUICallEngine createInstance(Context context)
```

### destroyInstance

This API is used to terminate a `TUICallEngine` singleton.

```
void destroyInstance();
```

### Init

This API is used to initialize `TUICallEngine`. Call it to authenticate the call service and perform other required actions before you call other APIs.

```
void init(int sdkAppId, String userId, String userSig, TUICommonDefine.Callback callback)
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| sdkAppId | int | You can view `SDKAppID` in [Application Management](https://console.trtc.io/app) > **Application Info** of the TRTC console. |
| userId | String | The ID of the current user, which is a string that can contain only letters (a-z and A-Z), digits (0-9), hyphens (-), and underscores (_). |
| userSig | String | Tencent Cloud's proprietary security signature. For how to calculate and use it, see [UserSig](https://www.tencentcloud.com/document/product/647/35166). |
| callback | TUICommonDefine.Callback | The initialization callback. `onSuccess` indicates initialization is successful. |

### addObserver

This API is used to register an event listener to listen for `TUICallObserver` events.

```
void addObserver(TUICallObserver observer);
```

### removeObserver

This API is used to unregister an event listener.

```
void removeObserver(TUICallObserver observer);
```

### calls

Initiate a one-to-one or multi-person call.

```
void calls(List<String> userIdList, TUICallDefine.MediaType mediaType,            TUICallDefine.CallParams params, TUICommonDefine.Callback callback)
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | List<String> | The target user IDs. |
| callMediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |
| params | [TUICallDefine.CallParams](https://www.tencentcloud.com/document/product/647/54900#CallParams) | An additional parameter. such as roomID, call timeout, offline push info,etc |

### accept

This API is used to accept a call. After receiving the `onCallReceived()` callback, you can call this API to accept the call.

```
void accept(TUICommonDefine.Callback callback);
```

### reject

This API is used to reject a call. After receiving the `onCallReceived()` callback, you can call this API to reject the call.

```
void reject(TUICommonDefine.Callback callback);
```

### ignore

This API is used to ignore a call. After receiving the `onCallReceived()`, you can call this API to ignore the call. The caller will receive the `onUserLineBusy` callback.

Note: If your project involves live streaming or conferencing, you can also use this API to implement the âin a meetingâ or âon airâ feature.

```
void ignore(TUICommonDefine.Callback callback);
```

### hangup

This API is used to end a call.

```
void hangup(TUICommonDefine.Callback callback);
```

### inviteUser

This API is used to invite users to the current group call.

This API is called by a participant of a group call to invite new users.

```
void inviteUser(List<String> userIdList, TUICallDefine.CallParams params,                 TUICommonDefine.ValueCallback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | List | The target user IDs. |
| params | [TUICallDefine.CallParams](https://www.tencentcloud.com/document/product/647/54900#CallParams) | An additional parameter. such as roomID, call timeout, offline push info,etc |

### join

Proactively join a call.

```
void join(String callId, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | Unique ID for this call |

### startRemoteView

This API is used to subscribe to the video stream of a remote user. For it to work, make sure you call it after `setRenderView`.

```
void startRemoteView(String userId, TUIVideoView videoView, TUICommonDefine.PlayCallback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |
| videoView | TUIVideoView | The view to be rendered. |

### stopRemoteView

This API is used to unsubscribe from the video stream of a remote user.

```
void stopRemoteView(String userId);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |

### openCamera

This API is used to turn the camera on.

```
void openCamera(TUICommonDefine.Camera camera, TUIVideoView videoView, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| camera | [TUICommonDefine.Camera](https://www.tencentcloud.com/document/product/647/54900#Camera) | The front or rear camera. |
| videoView | TUIVideoView | The view to be rendered. |

### closeCamera

This API is used to turn the camera off.

```
void closeCamera();
```

### switchCamera

This API is used to switch between the front and rear cameras.

```
void switchCamera(TUICommonDefine.Camera camera);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| camera | [TUICommonDefine.Camera](https://www.tencentcloud.com/document/product/647/54900#Camera) | The front or rear camera. |

### openMicrophone

This API is used to turn the mic on.

```
void openMicrophone(TUICommonDefine.Callback callback);
```

### closeMicrophone

This API is used to turn the mic off.

```
void closeMicrophone();
```

### selectAudioPlaybackDevice

This API is used to select the audio playback device (receiver or speaker). In call scenarios, you can use this API to turn on/off hands-free mode.

```
void selectAudioPlaybackDevice(TUICommonDefine.AudioPlaybackDevice device);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| device | [TUICommonDefine.AudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/54900#AudioPlaybackDevice) | The speaker or receiver. |

### setSelfInfo

This API is used to set the alias and profile photo. The alias cannot exceed 500 bytes, and the profile photo is specified by a URL.

```
void setSelfInfo(String nickname, String avatar, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| nickname | String | The alias. |
| avatar | String | The URL of the profile photo. |

### enableMultiDeviceAbility

This API is used to set whether to enable multi-device login for `TUICallEngine` (supported by the [Group Call package](https://trtc.io/document/54632?platform=android&product=call&menulabel=web)).

```
void enableMultiDeviceAbility(boolean enable, TUICommonDefine.Callback callback);
```

### setVideoRenderParams

Set the rendering mode of video image.

```
void setVideoRenderParams(String userId, TUICommonDefine.VideoRenderParams params, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |
| params | [TUICommonDefine.VideoRenderParams](https://www.tencentcloud.com/document/product/647/54900#VideoRenderParams) | Video render parameters. |

### setVideoEncoderParams

Set the encoding parameters of video encoder.

This setting can determine the quality of image viewed by remote users, which is also the image quality of on-cloud recording files.

```
void setVideoEncoderParams(TUICommonDefine.VideoEncoderParams params, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| params | [TUICommonDefine.VideoEncoderParams](https://www.tencentcloud.com/document/product/647/54900#VideoEncoderParams) | Video encoding parameters |

### getTRTCCloudInstance

Advanced features.

```
TRTCCloud getTRTCCloudInstance();
```

### setBeautyLevel

Set beauty level, support turning off default beauty.

```
void setBeautyLevel(float level, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| level | float | Beauty levelï¼range: 0 - 9ï¼ 0 means turning off the effect, 9 means the most obvious effect. |

## Deprecated Interface

### call

This API is used to make a (one-to-one) call. **Note:  it is recommended to use the calls API.**

```
void call(String userId, TUICallDefine.MediaType callMediaType,          TUICallDefine.CallParams params, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |
| callMediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |
| params | [TUICallDefine.CallParams](https://www.tencentcloud.com/document/product/647/54900#CallParams) | An additional parameter, such as roomID, call timeout, offline push info,etc |

### groupCall

This API is used to make a group call. **Note:  it is recommended to use the calls API.**

> **Noteï¼**Before making a group call, you need to create an Chat group first.

```
void groupCall(String groupId, List<String> userIdList, TUICallDefine.MediaType callMediaType,                TUICallDefine.CallParams params, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| groupId | String | The group ID. |
| userIdList | List | The target user IDs. |
| callMediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |
| params | [TUICallDefine.CallParams](https://www.tencentcloud.com/document/product/647/54900#CallParams) | An additional parameter. such as roomID, call timeout, offline push info,etc |

### joinInGroupCall

This API is used to join a group call. **Note:  it is recommended to use the join API.**

This API is called by a group member to join the groupâs call.

```
void joinInGroupCall(TUICommonDefine.RoomId roomId, String groupId,                      TUICallDefine.MediaType callMediaType, TUICommonDefine.Callback callback);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | [TUICommonDefine.RoomId](https://www.tencentcloud.com/document/product/647/54900#RoomId) | The room ID. |
| groupId | String | The group ID. |
| callMediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |

### switchCallMediaType

This API is used to change the call type.

```
void switchCallMediaType(TUICallDefine.MediaType callMediaType);
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| callMediaType | [TUICallDefine.MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | The call type, which can be video or audio. |


---
*Source: [https://trtc.io/document/51006](https://trtc.io/document/51006)*
