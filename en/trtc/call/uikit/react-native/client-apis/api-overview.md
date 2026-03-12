# API Overview

## TUICallKit (including UI Interface)

## TUICallKit APIs

UICallKit API, you can quickly implement a WeChat-like audio and video call scenario through simple interfaces.

| API | Description |
| --- | --- |
| [login](https://www.tencentcloud.com/document/product/647/66842#93b6b48b-6ced-41f6-9efe-3c99ac82a7cc) | Login. |
| [logout](https://www.tencentcloud.com/document/product/647/66842#34205667-e433-4e42-80fb-ca9d0fc256c7) | Logout. |
| [calls](https://www.tencentcloud.com/document/product/647/66842#184a66f0-1280-4575-89a1-409f4f64aa3b) | Initiate a one-to-one or multi-person call. |
| [call](https://www.tencentcloud.com/document/product/647/66842#call_param) | To make a one-on-one call, supports custom room ID, call timeout, offline push content, and more. |
| [groupCall](https://www.tencentcloud.com/document/product/647/66842#groupcall) | To make a group call, supports custom room ID, call timeout, offline push content, and more. |
| [joinInGroupCall](https://www.tencentcloud.com/document/product/647/66842#joiningroupcall) | Join a group call. |
| [setCallingBell](https://www.tencentcloud.com/document/product/647/66842#93d9981e-20e0-4619-b01b-ae0b9edc85a5) | Customize user's ringtone. |
| [enableMuteMode](https://www.tencentcloud.com/document/product/647/66842#f437b400-a478-4446-a060-ae2283af3a38) | Enable/Disable Ringtone. |
| [enableVirtualBackground](https://www.tencentcloud.com/document/product/647/66842#48143cfb-18bc-4b06-b4bc-6fd8214f15d4) | Enable/disable blurry background feature. |
| [setScreenOrientation](https://www.tencentcloud.com/document/product/647/66842#1f6205a6-9ef8-42aa-9143-697476ad4478) | Set Screen Orientation. |
| [on](https://www.tencentcloud.com/document/product/647/66842#41ad2909-fce1-4b6e-8a0c-2a4a982bc6ae) | Listen to TUICallKit events. |
| [off](https://www.tencentcloud.com/document/product/647/66842#ce43fcef-252e-4ab2-bd0e-175fc4847b54) | Cancel listening to TUICallKit events. |

## TUICallEvent

TUICallEvent is the callback event class corresponding to TUICallKit. Through this callback, you can listen to the callback events you are interested in.

| Event | Description |
| --- | --- |
| [TUICallEvent.onError](https://www.tencentcloud.com/document/product/647/66841#error) | Error Callback during Call. |
| [TUICallEvent.onCallReceived](https://www.tencentcloud.com/document/product/647/66841#6b3c4385-acfb-478f-ad96-fe5310133b08) | Callback for a Call Request. |
| [TUICallEvent.onCallCancelled](https://www.tencentcloud.com/document/product/647/66841#06a7a696-ca1b-4b4e-ba01-ee9e2efeb732) | Callback for Call Cancellation. |
| [TUICallEvent.onCallBegin](https://www.tencentcloud.com/document/product/647/66841#9918ea17-7900-4d01-9672-1f0e06f5e260) | Callback for Call Connection. |
| [TUICallEvent.onCallEnd](https://www.tencentcloud.com/document/product/647/66841#0f575468-4d5e-4c27-9d6e-0ce85de0c77a) | Callback for Call Termination. |
| [TUICallEvent.onUserReject](https://www.tencentcloud.com/document/product/647/66841#095f6da9-4668-4084-b44a-a2a59314d249) | xxxx User declines the call Callback. |
| [TUICallEvent.onUserNoResponse](https://www.tencentcloud.com/document/product/647/66841#2586c3d6-3902-4948-b988-74789b5a4759) | xxxx User Non-response Callback. |
| [TUICallEvent.onUserLineBusy](https://www.tencentcloud.com/document/product/647/66841#fa1c55d7-48a2-4cd3-a38c-9e81f082e68e) | xxxx User Busy Line Callback. |
| [TUICallEvent.onUserJoin](https://www.tencentcloud.com/document/product/647/66841#7b551600-44c5-4683-90b7-25a3b243d12e) | xxxx User Joins Call Callback. |
| [TUICallEvent.onUserLeave](https://www.tencentcloud.com/document/product/647/66841#fc8bb8d0-7665-4962-acc9-eea9bd1fe7db) | A user left the call. |
| [TUICallEvent.onCallMediaTypeChanged](https://www.tencentcloud.com/document/product/647/66841#31432c9e-4801-427f-b9de-64af29bb132d) | Callback for a change in the Call's Media Type. |
| [TUICallEvent.onKickedOffline](https://www.tencentcloud.com/document/product/647/66841#f690f3cf-5ce7-4322-9310-f5b099e97b0c) | Current user kicked offline. |
| [TUICallEvent.onUserSigExpired](https://www.tencentcloud.com/document/product/647/66841#b648078a-9d21-4b8e-bfe7-5d530d7af018) | Ticket expired while online. |
| [TUICallEvent.onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/66841#b3e6f255-610d-405c-8b78-0619941be48d) | Whether a user has a video stream. |
| [TUICallEvent.onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/66841#3ca13720-a03e-4fb6-9fd0-de547be0ff4f) | Whether a user has an audio stream. |
| [TUICallEvent.onUserVoiceVolumeChanged](https://www.tencentcloud.com/document/product/647/66841#e613c8b7-1114-4471-a8cd-54001c4ce2fb) | The volume levels of all users. |
| [TUICallEvent.onUserNetworkQualityChanged](https://www.tencentcloud.com/document/product/647/66841#dc08307d-9fe7-4b95-9ca8-431730d1f60d) | The network quality of all users. |

## TUICallEngine (No UI)

`TUICallEngine` is an audio/video call component that **does not include UI elements**. If `TUICallKit` does not meet your requirements, you can use the APIs of `TUICallEngine` to customize your project.

| API | Description |
| --- | --- |
| [createInstance](https://www.tencentcloud.com/document/product/647/67600#b7284179-8663-4c7d-89a7-6f094af16616) | Creates a `TUICallEngine` instance (singleton mode). |
| [destroyInstance](https://www.tencentcloud.com/document/product/647/67600#de1c7b92-0a92-49b8-99ab-785e36c9e64a) | Terminates a `TUICallEngine` instance (singleton mode). |
| [login](https://www.tencentcloud.com/document/product/647/67600#dc857e4b-4458-4046-ab13-2da3cd59b7a8) | Authenticates the basic audio/video call capabilities. |
| [on](https://www.tencentcloud.com/document/product/647/67600#481db1ba-bb8c-4298-a692-281c0b4471a6) | Registers an event listener. |
| [off](https://www.tencentcloud.com/document/product/647/67600#8dee85b0-3967-464a-b4e9-cd594164f81a) | Unregisters an event listener. |
| [call](https://www.tencentcloud.com/document/product/647/67600#ae7d1ece-ba62-426d-9a33-42b2e21def3e) | Makes a one-to-one call. |
| [accept](https://www.tencentcloud.com/document/product/647/67600#59e19c12-1f02-43e6-991e-e86471c67f41) | Accepts a call. |
| [reject](https://www.tencentcloud.com/document/product/647/67600#737fb419-4944-4adc-96c0-d18ed4a429c5) | Rejects a call. |
| [ignore](https://www.tencentcloud.com/document/product/647/67600#73d1e436-238f-47ac-a07d-e0db3b029f5e) | Ignores a call. |
| [hangup](https://www.tencentcloud.com/document/product/647/67600#d8a7dd6b-3b95-403a-97fe-ed68eb6f225d) | Ends a call. |
| [switchCallMediaType](https://www.tencentcloud.com/document/product/647/67600#417d1d5b-da7d-48d1-b935-39f2083f37d8) | Changes the call type, for example, from video call to audio call. |
| [startRemoteView](https://www.tencentcloud.com/document/product/647/67600#35dae00f-9958-461c-a2e1-fee9c46f7a5f) | Subscribes to the video stream of a remote user. |
| [stopRemoteView](https://www.tencentcloud.com/document/product/647/67600#0491e355-52fb-4f31-89d4-4a927666c91d) | Unsubscribes from the video stream of a remote user. |
| [openCamera](https://www.tencentcloud.com/document/product/647/67600#c5c6d48f-e43b-4783-9f6a-66f3463799ef) | Turns the camera on. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/67600#2de922a4-584f-40c7-aa31-be722cfc36e6) | Switches between the front and rear cameras. |
| [closeCamera](https://www.tencentcloud.com/document/product/647/67600#856c0993-1baa-4fc4-b030-e92dd981c927) | Turns the camera off. |
| [openMicrophone](https://www.tencentcloud.com/document/product/647/67600#0b0d9f9f-bf30-4a4d-a04a-740ee893f333) | Turns the mic on. |
| [closeMicrophone](https://www.tencentcloud.com/document/product/647/67600#44408d8a-5a20-46b3-9113-769ee604fd23) | Turns the mic off. |
| [selectAudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/67600#754db95b-b121-441c-824d-e2b843549858) | Selects the audio playback device (receiver or speaker). |
| [setVideoRenderParams](https://www.tencentcloud.com/document/product/647/67600#593170ad-f21c-46fb-ad11-e2cd46c3c119) | Set the rendering mode of video image. |
| [setVideoEncoderParams](https://www.tencentcloud.com/document/product/647/67600#e3c90891-f93a-431e-8b16-2fbfc31b5f4f) | Set the encoding parameters of video encoder. |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/67600#353aabf6-bf08-4bc2-a396-8c5820898bd2) | Set beauty level, support turning off default beauty. |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/67600#8ed81cdd-05c9-4c46-ae3d-ba6055dcfc68) | Sets the alias and profile photo. |
| [enableMultiDeviceAbility](https://www.tencentcloud.com/document/product/647/67600#a6408ab6-9e50-4dea-9c26-cf3d9b552084) | Sets whether to enable multi-device login for `TUICallEngine` . |


---
*Source: [https://trtc.io/document/66843](https://trtc.io/document/66843)*
