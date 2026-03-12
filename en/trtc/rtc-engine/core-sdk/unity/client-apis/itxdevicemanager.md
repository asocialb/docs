# ITXDeviceManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: audio/video device management module

Description: manages audio/video devices such as camera, mic, and speaker.

**ITXDeviceManager**

## ITXDeviceObserver

| FuncList | DESC |
| --- | --- |
| [onDeviceChanged](https://www.tencentcloud.com/document/product/647/72274#145ac4d9fb6637d63b132d42ba458e22) | The status of a local device changed (for desktop OS only). |

## ITXDeviceManager

| FuncList | DESC |
| --- | --- |
| [isFrontCamera](https://www.tencentcloud.com/document/product/647/72274#9543ad265abb9ffbe26d50cf56e82f21) | Querying whether the front camera is being used (for mobile OS). |
| [switchCamera](https://www.tencentcloud.com/document/product/647/72274#cc3d2f9b4dd914d70115b322c1d8b648) | Switching to the front/rear camera (for mobile OS). |
| [getCameraZoomMaxRatio](https://www.tencentcloud.com/document/product/647/72274#3cf349343e4fa09806e7757ab3f7c056) | Getting the maximum zoom ratio of the camera (for mobile OS). |
| [setCameraZoomRatio](https://www.tencentcloud.com/document/product/647/72274#e61285838deaccc253276f840283a92b) | Setting the camera zoom ratio (for mobile OS). |
| [isAutoFocusEnabled](https://www.tencentcloud.com/document/product/647/72274#a11df91d58ba4606d640229e3c574c9e) | Querying whether automatic face detection is supported (for mobile OS). |
| [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/72274#6786f243b9354cf0163d5e37a45125e0) | Enabling auto focus (for mobile OS). |
| [setCameraFocusPosition](https://www.tencentcloud.com/document/product/647/72274#0027745b8da75bf19ddc84f8266c67e5) | Adjusting the focus (for mobile OS). |
| [enableCameraTorch](https://www.tencentcloud.com/document/product/647/72274#d21c0adb35f5b25221814ee9b392a88c) | Enabling/Disabling flash, i.e., the torch mode (for mobile OS). |
| [setAudioRoute](https://www.tencentcloud.com/document/product/647/72274#5bfe3b787bb300630f3bdd577d284d8a) | Setting the audio route (for mobile OS). |
| [setCurrentDevice](https://www.tencentcloud.com/document/product/647/72274#b2e3b568fe9237d3aeee70d2c171fd77) | Setting the device to use (for desktop OS). |
| [getCurrentDevice](https://www.tencentcloud.com/document/product/647/72274#70877e751be615f122a299ce8b762726) | Getting the device currently in use (for desktop OS). |
| [setSystemVolumeType](https://www.tencentcloud.com/document/product/647/72274#4c853ff41ffa2c100401035df3480848) | Setting the system volume type (for mobile OS). |

## StructType

| FuncList | DESC |
| --- | --- |
| [TXCameraCaptureParam](https://www.tencentcloud.com/document/product/647/72274#654f738285ec7c055a692afa6ed803ea) | Camera acquisition parameters. |
| [TXDeviceInfo](https://www.tencentcloud.com/document/product/647/72274#d61e674cb437d6cef97ec8660a96b405) | Audio/Video device information (for desktop OS). |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXSystemVolumeType](https://www.tencentcloud.com/document/product/647/72274#9e22ac3a1dd66fee5bed02bc61c5e58b) | System volume type (for mobile OS). |
| [TXAudioRoute](https://www.tencentcloud.com/document/product/647/72274#39c508dc7c357c2feda25e56f2d729c1) | Audio route (the route via which audio is played). |
| [TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/72274#f023a4d94be317eb399df83a25af6b2b) | Device type (for desktop OS). |
| [TXMediaDeviceState](https://www.tencentcloud.com/document/product/647/72274#0e59520d0b5cd9b6826a30ea0dbba8f7) | Device operation. |
| [TXCameraCaptureMode](https://www.tencentcloud.com/document/product/647/72274#aede0b6f9c933df04f1b4e096ced41e6) | Camera acquisition preferences. |

## onDeviceChanged

**onDeviceChanged**

| void onDeviceChanged | (String deviceId |
| --- | --- |
|  | [TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/72274#f023a4d94be317eb399df83a25af6b2b) type |
|  | [TXMediaDeviceState](https://www.tencentcloud.com/document/product/647/72274#0e59520d0b5cd9b6826a30ea0dbba8f7) state) |

#### The status of a local device changed (for desktop OS only).

The SDK returns this callback when a local device (camera, mic, or speaker) is connected or disconnected.

| Param | DESC |
| --- | --- |
| deviceId | Device ID |
| state | Device status. ` 0 `: connected; ` 1 `: disconnected; ` 2 `: started |
| type | Device type |

## isFrontCamera

**isFrontCamera**

#### Querying whether the front camera is being used (for mobile OS).

## switchCamera

**switchCamera**

| int switchCamera | (bool frontCamera) |
| --- | --- |

#### Switching to the front/rear camera (for mobile OS).

## getCameraZoomMaxRatio

**getCameraZoomMaxRatio**

#### Getting the maximum zoom ratio of the camera (for mobile OS).

## setCameraZoomRatio

**setCameraZoomRatio**

| int setCameraZoomRatio | (double zoomRatio) |
| --- | --- |

#### Setting the camera zoom ratio (for mobile OS).

| Param | DESC |
| --- | --- |
| zoomRatio | Value range: [1, 5]. 1 indicates the widest angle of view (original), and 5 the narrowest angle of view (zoomed in).The maximum value is recommended to be 5. If the value exceeds 5, the video will become blurred. |

## isAutoFocusEnabled

**isAutoFocusEnabled**

#### Querying whether automatic face detection is supported (for mobile OS).

## enableCameraAutoFocus

**enableCameraAutoFocus**

| int enableCameraAutoFocus | (bool enabled) |
| --- | --- |

#### Enabling auto focus (for mobile OS).

After auto focus is enabled, the camera will automatically detect and always focus on faces.

## setCameraFocusPosition

**setCameraFocusPosition**

| int setCameraFocusPosition | (int x |
| --- | --- |
|  | int y) |

#### Adjusting the focus (for mobile OS).

This API can be used to achieve the following:

1. A user can tap on the camera preview.

2. A rectangle will appear where the user taps, indicating the spot the camera will focus on.

3. The user passes the coordinates of the spot to the SDK using this API, and the SDK will instruct the camera to focus as required.

| Param | DESC |
| --- | --- |
| position | The spot to focus on. Pass in the coordinates of the spot you want to focus on. |

> **Note**Before using this API, you must first disable auto focus using [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/72274#6786f243b9354cf0163d5e37a45125e0).

#### Return Desc:

0: operation successful; negative number: operation failed.

## enableCameraTorch

**enableCameraTorch**

| int enableCameraTorch | (bool enabled) |
| --- | --- |

#### Enabling/Disabling flash, i.e., the torch mode (for mobile OS).

## setAudioRoute

**setAudioRoute**

| int setAudioRoute | ([TXAudioRoute](https://www.tencentcloud.com/document/product/647/72274#39c508dc7c357c2feda25e56f2d729c1) route) |
| --- | --- |

#### Setting the audio route (for mobile OS).

A mobile phone has two audio playback devices: the receiver at the top and the speaker at the bottom.

If the audio route is set to the receiver, the volume is relatively low, and audio can be heard only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.

If the audio route is set to the speaker, the volume is relatively high, and there is no need to put the phone near the ear. This mode enables the "hands-free" feature.

## setCurrentDevice

**setCurrentDevice**

| int setCurrentDevice | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/72274#f023a4d94be317eb399df83a25af6b2b) type |
| --- | --- |
|  | String deviceId) |

#### Setting the device to use (for desktop OS).

| Param | DESC |
| --- | --- |
| deviceId | Device ID. You can get the ID of a device using the getDevicesList API. |
| type | Device type. For details, please see the definition of ` TXMediaDeviceType `. |

#### Return Desc:

0: operation successful; negative number: operation failed.

## getCurrentDevice

**getCurrentDevice**

| TXDeviceInfo getCurrentDevice | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/72274#f023a4d94be317eb399df83a25af6b2b) type) |
| --- | --- |

#### Getting the device currently in use (for desktop OS).

## setSystemVolumeType

**setSystemVolumeType**

| int setSystemVolumeType | ([TXSystemVolumeType](https://www.tencentcloud.com/document/product/647/72274#9e22ac3a1dd66fee5bed02bc61c5e58b) type) |
| --- | --- |

#### Setting the system volume type (for mobile OS).

@deprecated This API is not recommended after v9.5. Please use the ` startLocalAudio(quality) ` API in ` TRTCCloud ` instead, which param ` quality ` is used to decide audio quality.

## TXSystemVolumeType(Deprecated)

**TXSystemVolumeType(Deprecated)**

#### System volume type (for mobile OS).

@deprecated It is not recommended to use since version v9.5.

Modern smartphones generally have two system volume types, namely "call volume" and "media volume".

- Call volume: The volume type designed specifically for making and receiving calls. It has built-in echo cancellation (AEC) function and supports picking up sound through the microphone on the Bluetooth headset. The disadvantage is that the sound quality is average.

When you use the volume button on the side of the phone to turn down the volume of the phone, if it cannot be adjusted to zero (that is, it cannot be completely muted), it means that your phone is currently in call volume.

- Media volume: The volume type designed specifically for music scenes on the phone cannot use the system's AEC function and does not support picking up sound through the microphone of the Bluetooth headset, but has better music playback effect.

When you use the volume button on the side of the phone to turn down the volume of the phone, if the phone volume can be adjusted to completely mute, it means that your phone is currently in media volume.

The SDK currently provides three control modes for system volume types: Auto, Media volume, and Call volume mode.

| Enum | Value | DESC |
| --- | --- | --- |
| TXSystemVolumeTypeAuto | 0 | Auto |
| TXSystemVolumeTypeMedia | 1 | Media volume |
| TXSystemVolumeTypeVOIP | 2 | Call volume |

## TXAudioRoute

**TXAudioRoute**

#### Audio route (the route via which audio is played).

Audio route is the route (speaker or receiver) via which audio is played. It applies only to mobile devices such as mobile phones.

A mobile phone has two speakers: one at the top (receiver) and the other the bottom.

- If the audio route is set to the receiver, the volume is relatively low, and audio can be heard only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.
- If the audio route is set to the speaker, the volume is relatively high, and there is no need to put the phone near the ear. This mode enables the "hands-free" feature.

| Enum | Value | DESC |
| --- | --- | --- |
| TXAudioRouteSpeakerphone | 0 | Speakerphone: the speaker at the bottom is used for playback (hands-free). With relatively high volume, it is used to play music out loud. |
| TXAudioRouteEarpiece | 1 | Earpiece: the receiver at the top is used for playback. With relatively low volume, it is suitable for call scenarios that require privacy. |

## TXMediaDeviceType

**TXMediaDeviceType**

#### Device type (for desktop OS).

This enumerated type defines three types of audio/video devices, namely camera, mic and speaker, so that you can use the same device management API to manage three types of devices.

| Enum | Value | DESC |
| --- | --- | --- |
| TXMediaDeviceTypeUnknown | -1 | undefined device type |
| TXMediaDeviceTypeMic | 0 | microphone |
| TXMediaDeviceTypeSpeaker | 1 | speaker or earpiece |
| TXMediaDeviceTypeCamera | 2 | camera |

## TXMediaDeviceState

**TXMediaDeviceState**

#### Device operation.

This enumerated value is used to notify the status change of the local device [onDeviceChanged](https://www.tencentcloud.com/document/product/647/72274#145ac4d9fb6637d63b132d42ba458e22).

| Enum | Value | DESC |
| --- | --- | --- |
| TXMediaDeviceStateAdd | 0 | The device has been plugged in |
| TXMediaDeviceStateRemove | 1 | The device has been removed |
| TXMediaDeviceStateActive | 2 | The device has been enabled |
| TXMediaDefaultDeviceChanged | 3 | system default device changed |

## TXCameraCaptureMode

**TXCameraCaptureMode**

#### Camera acquisition preferences.

This enum is used to set camera acquisition parameters.

| Enum | Value | DESC |
| --- | --- | --- |
| TXCameraResolutionStrategyAuto | 0 | Auto adjustment of camera capture parameters.SDK selects the appropriate camera output parameters according to the actual acquisition device performance and network situation, and maintains a balance between device performance and video preview quality. |
| TXCameraResolutionStrategyPerformance | 1 | Give priority to equipment performance.SDK selects the closest camera output parameters according to the user's encoder resolution and frame rate, so as to ensure the performance of the device. |
| TXCameraResolutionStrategyHighQuality | 2 | Give priority to the quality of video preview.SDK selects higher camera output parameters to improve the quality of preview video. In this case, it will consume more CPU and memory to do video preprocessing. |
| TXCameraCaptureManual | 3 | Allows the user to set the width and height of the video captured by the local camera. |

## TXCameraCaptureParam

**TXCameraCaptureParam**

#### Camera acquisition parameters.

This setting determines the quality of the local preview image.

| EnumType | DESC |
| --- | --- |
| height | Field description:  height of acquired image |
| mode | Field description: camera acquisition preferences,please see [TXCameraCaptureMode](https://www.tencentcloud.com/document/product/647/72274#aede0b6f9c933df04f1b4e096ced41e6) |
| width | Field description: width of acquired image |

## TXMediaDeviceInfo

**TXMediaDeviceInfo**

#### Audio/Video device information (for desktop OS).

This structure describes key information (such as device ID and device name) of an audio/video device, so that users can choose on the UI the device to use.

| EnumType | DESC |
| --- | --- |
| deviceName | device name (UTF-8) |
| devicePID | device id (UTF-8) |
| deviceProperties | device properties |


---
*Source: [https://trtc.io/document/72274](https://trtc.io/document/72274)*
