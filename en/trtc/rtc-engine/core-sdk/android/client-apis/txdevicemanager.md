# TXDeviceManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: audio/video device management module

Description: manages audio/video devices such as camera, mic, and speaker.

**TXDeviceManager**

## TXDeviceManager

| FuncList | DESC |
| --- | --- |
| [isFrontCamera](https://www.tencentcloud.com/document/product/647/50767#71820ed8e774434ec01d6dc6a44dfe3d) | Querying whether the front camera is being used. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/50767#98743c4b46e3baea8308a8e27cf44c8a) | Switching to the front/rear camera (for mobile OS). |
| [getCameraZoomMaxRatio](https://www.tencentcloud.com/document/product/647/50767#c792f2cefe9b867591a00071f673da52) | Getting the maximum zoom ratio of the camera (for mobile OS). |
| [setCameraZoomRatio](https://www.tencentcloud.com/document/product/647/50767#de6f0bc85a439308d2bca3f5a338e3f7) | Setting the camera zoom ratio (for mobile OS). |
| [isAutoFocusEnabled](https://www.tencentcloud.com/document/product/647/50767#f3c9fb1db152e2ef198256dcf992fc30) | Querying whether automatic face detection is supported (for mobile OS). |
| [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/50767#5bb9ad6ffa0c173d8864188d143a6332) | Enabling auto focus (for mobile OS). |
| [setCameraFocusPosition](https://www.tencentcloud.com/document/product/647/50767#c50deb76ecaed735d7a7571ae9e1e719) | Adjusting the focus (for mobile OS). |
| [enableCameraTorch](https://www.tencentcloud.com/document/product/647/50767#b71d15b7be8cd6fa6f4cf6435d7548be) | Enabling/Disabling flash, i.e., the torch mode (for mobile OS). |
| [setAudioRoute](https://www.tencentcloud.com/document/product/647/50767#bd5eb5475f6b3cf2e2881fe4c4dee818) | Setting the audio route (for mobile OS). |
| [setExposureCompensation](https://www.tencentcloud.com/document/product/647/50767#260167d6608887a70694ee2983fefc10) | Set the exposure parameters of the camera, ranging from - 1 to 1. |
| [setCameraCapturerParam](https://www.tencentcloud.com/document/product/647/50767#3a720bdf065f7984d709180bdd28cd02) | Set camera acquisition preferences. |
| [setSystemVolumeType](https://www.tencentcloud.com/document/product/647/50767#d4219ee8b3e722282cd8e564f79d4cd8) | Setting the system volume type (for mobile OS). |

## StructType

| FuncList | DESC |
| --- | --- |
| [TXCameraCaptureParam](https://www.tencentcloud.com/document/product/647/50767#654f738285ec7c055a692afa6ed803ea) | Camera acquisition parameters. |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXSystemVolumeType](https://www.tencentcloud.com/document/product/647/50767#9e22ac3a1dd66fee5bed02bc61c5e58b) | System volume type. |
| [TXAudioRoute](https://www.tencentcloud.com/document/product/647/50767#39c508dc7c357c2feda25e56f2d729c1) | Audio route (the route via which audio is played). |
| [TXCameraCaptureMode](https://www.tencentcloud.com/document/product/647/50767#aede0b6f9c933df04f1b4e096ced41e6) | Camera acquisition preferences. |

## isFrontCamera

**isFrontCamera**

**Querying whether the front camera is being used.**

## switchCamera

**switchCamera**

| int switchCamera | (boolean frontCamera) |
| --- | --- |

**Switching to the front/rear camera (for mobile OS).**

## getCameraZoomMaxRatio

**getCameraZoomMaxRatio**

**Getting the maximum zoom ratio of the camera (for mobile OS).**

## setCameraZoomRatio

**setCameraZoomRatio**

| int setCameraZoomRatio | (float zoomRatio) |
| --- | --- |

**Setting the camera zoom ratio (for mobile OS).**

| Param | DESC |
| --- | --- |
| zoomRatio | Value range: [1, 5]. 1 indicates the widest angle of view (original), and 5 the narrowest angle of view (zoomed in).The maximum value is recommended to be 5. If the value exceeds 5, the video will become blurred. |

## isAutoFocusEnabled

**isAutoFocusEnabled**

**Querying whether automatic face detection is supported (for mobile OS).**

## enableCameraAutoFocus

**enableCameraAutoFocus**

| int enableCameraAutoFocus | (boolean enabled) |
| --- | --- |

**Enabling auto focus (for mobile OS).**

After auto focus is enabled, the camera will automatically detect and always focus on faces.

## setCameraFocusPosition

**setCameraFocusPosition**

| int setCameraFocusPosition | (int x |
| --- | --- |
|  | int y) |

**Adjusting the focus (for mobile OS).**

This API can be used to achieve the following:

1. A user can tap on the camera preview.

2. A rectangle will appear where the user taps, indicating the spot the camera will focus on.

3. The user passes the coordinates of the spot to the SDK using this API, and the SDK will instruct the camera to focus as required.

| Param | DESC |
| --- | --- |
| position | The spot to focus on. Pass in the coordinates of the spot you want to focus on. |

> **Note**Before using this API, you must first disable auto focus using [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/50767#5bb9ad6ffa0c173d8864188d143a6332).

**Return Desc:**

0: operation successful; negative number: operation failed.

## enableCameraTorch

**enableCameraTorch**

| boolean enableCameraTorch | (boolean enable) |
| --- | --- |

**Enabling/Disabling flash, i.e., the torch mode (for mobile OS).**

## setAudioRoute

**setAudioRoute**

| int setAudioRoute | ([TXAudioRoute](https://www.tencentcloud.com/document/product/647/50767#39c508dc7c357c2feda25e56f2d729c1) route) |
| --- | --- |

**Setting the audio route (for mobile OS).**

A mobile phone has two audio playback devices: the receiver at the top and the speaker at the bottom.

If the audio route is set to the receiver, the volume is relatively low, and audio can be heard only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.

If the audio route is set to the speaker, the volume is relatively high, and there is no need to put the phone near the ear. This mode enables the "hands-free" feature.

## setExposureCompensation

**setExposureCompensation**

| int setExposureCompensation | (float value) |
| --- | --- |

**Set the exposure parameters of the camera, ranging from - 1 to 1.**

## setCameraCapturerParam

**setCameraCapturerParam**

| void setCameraCapturerParam | ([TXCameraCaptureParam](https://www.tencentcloud.com/document/product/647/50767#654f738285ec7c055a692afa6ed803ea) params) |
| --- | --- |

**Set camera acquisition preferences.**

## setSystemVolumeType

**setSystemVolumeType**

| int setSystemVolumeType | ([TXSystemVolumeType](https://www.tencentcloud.com/document/product/647/50767#9e22ac3a1dd66fee5bed02bc61c5e58b) type) |
| --- | --- |

**Setting the system volume type (for mobile OS).**

@deprecated This API is not recommended after v9.5. Please use the ` startLocalAudio(quality) ` API in ` TRTCCloud ` instead, which param ` quality ` is used to decide audio quality.

## TXSystemVolumeType(Deprecated)

**TXSystemVolumeType(Deprecated)**

**System volume type.**

| Enum | Value | DESC |
| --- | --- | --- |
| TXSystemVolumeTypeAuto | Not Defined | Auto |
| TXSystemVolumeTypeMedia | Not Defined | Media volume |
| TXSystemVolumeTypeVOIP | Not Defined | Call volume |

## TXAudioRoute

**TXAudioRoute**

**Audio route (the route via which audio is played).**

Audio route is the route (speaker or receiver) via which audio is played. It applies only to mobile devices such as mobile phones.

A mobile phone has two speakers: one at the top (receiver) and the other the bottom.

- If the audio route is set to the receiver, the volume is relatively low, and audio can be heard only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.
- If the audio route is set to the speaker, the volume is relatively high, and there is no need to put the phone near the ear. This mode enables the "hands-free" feature.

| Enum | Value | DESC |
| --- | --- | --- |
| TXAudioRouteSpeakerphone | Not Defined | Speakerphone: the speaker at the bottom is used for playback (hands-free). With relatively high volume, it is used to play music out loud. |
| TXAudioRouteEarpiece | Not Defined | Earpiece: the receiver at the top is used for playback. With relatively low volume, it is suitable for call scenarios that require privacy. |

## TXCameraCaptureMode

**TXCameraCaptureMode**

**Camera acquisition preferences.**

This enum is used to set camera acquisition parameters.

| Enum | Value | DESC |
| --- | --- | --- |
| TXCameraResolutionStrategyAuto | Not Defined | Auto adjustment of camera capture parameters.SDK selects the appropriate camera output parameters according to the actual acquisition device performance and network situation, and maintains a balance between device performance and video preview quality. |
| TXCameraResolutionStrategyPerformance | Not Defined | Give priority to equipment performance.SDK selects the closest camera output parameters according to the user's encoder resolution and frame rate, so as to ensure the performance of the device. |
| TXCameraResolutionStrategyHighQuality | Not Defined | Give priority to the quality of video preview.SDK selects higher camera output parameters to improve the quality of preview video. In this case, it will consume more CPU and memory to do video preprocessing. |
| TXCameraCaptureManual | Not Defined | Allows the user to set the width and height of the video captured by the local camera. |

## TXCameraCaptureParam

**TXCameraCaptureParam**

**Camera acquisition parameters.**

This setting determines the quality of the local preview image.

| EnumType | DESC |
| --- | --- |
| height | Field description:  height of acquired image |
| mode | Field description: camera acquisition preferences,please see [TXCameraCaptureMode](https://www.tencentcloud.com/document/product/647/50767#aede0b6f9c933df04f1b4e096ced41e6) |
| width | Field description: width of acquired image |


---
*Source: [https://trtc.io/document/50767](https://trtc.io/document/50767)*
