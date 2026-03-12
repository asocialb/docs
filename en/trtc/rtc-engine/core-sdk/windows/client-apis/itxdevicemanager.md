# ITXDeviceManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: audio/video device management module

Description: manages audio/video devices such as camera, mic, and speaker.

**ITXDeviceManager**

## ITXDeviceManager

| FuncList | DESC |
| --- | --- |
| [isFrontCamera](https://www.tencentcloud.com/document/product/647/50774#0f9d6b1396b1cafc2fe0e9e6995eaff1) | Querying whether the front camera is being used. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/50774#643e0deb4a02eccd7b1fa9e186353481) | Switching to the front/rear camera (for mobile OS). |
| [getCameraZoomMaxRatio](https://www.tencentcloud.com/document/product/647/50774#3622c34b4499a12757e052a502f27408) | Getting the maximum zoom ratio of the camera (for mobile OS). |
| [setCameraZoomRatio](https://www.tencentcloud.com/document/product/647/50774#1200e0cde542f5e3cbf5ae703d68167b) | Setting the camera zoom ratio (for mobile OS). |
| [isAutoFocusEnabled](https://www.tencentcloud.com/document/product/647/50774#a9c12dfcdb51f9d45f8bee002b55d4f7) | Querying whether automatic face detection is supported (for mobile OS). |
| [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/50774#30fe7ff8b3ca773e2084b7b99bd43e2a) | Enabling auto focus (for mobile OS). |
| [setCameraFocusPosition](https://www.tencentcloud.com/document/product/647/50774#f3d30dbe5d65b2454d10635083051fa6) | Adjusting the focus (for mobile OS). |
| [enableCameraTorch](https://www.tencentcloud.com/document/product/647/50774#41656f5fe1011c59544c8a20f45d5c39) | Enabling/Disabling flash, i.e., the torch mode (for mobile OS). |
| [setAudioRoute](https://www.tencentcloud.com/document/product/647/50774#e8877bbaaefb9beed5afc17f536202d1) | Setting the audio route (for mobile OS). |
| [getDevicesList](https://www.tencentcloud.com/document/product/647/50774#514e123e8955eb408ba2fddd704ad2ee) | Getting the device list (for desktop OS). |
| [setCurrentDevice](https://www.tencentcloud.com/document/product/647/50774#a6ce23ec66c6d809518d37600b58eede) | Setting the device to use (for desktop OS). |
| [getCurrentDevice](https://www.tencentcloud.com/document/product/647/50774#7b89a49457ca9796d778501b820dc76c) | Getting the device currently in use (for desktop OS). |
| [setCurrentDeviceVolume](https://www.tencentcloud.com/document/product/647/50774#74ebb73b17e8b373ce7414955c26f745) | Setting the volume of the current device (for desktop OS). |
| [getCurrentDeviceVolume](https://www.tencentcloud.com/document/product/647/50774#dd96184a23fa00d84ca80afd1652ff6b) | Getting the volume of the current device (for desktop OS). |
| [setCurrentDeviceMute](https://www.tencentcloud.com/document/product/647/50774#f552e7fc52cd86ec3cb6c4207bba2677) | Muting the current device (for desktop OS). |
| [getCurrentDeviceMute](https://www.tencentcloud.com/document/product/647/50774#3726402fd265556feca2db4841bae145) | Querying whether the current device is muted (for desktop OS). |
| [enableFollowingDefaultAudioDevice](https://www.tencentcloud.com/document/product/647/50774#a288cca0ea46d34c494f3dc277e7ba25) | Set the audio device used by SDK to follow the system default device (for desktop OS). |
| [startCameraDeviceTest](https://www.tencentcloud.com/document/product/647/50774#cf9fcee895f531fee24cbf313ac56d90) | Starting camera testing (for desktop OS). |
| [stopCameraDeviceTest](https://www.tencentcloud.com/document/product/647/50774#2f26ea999b1d98de3f5f67816d1d31fc) | Ending camera testing (for desktop OS). |
| [startMicDeviceTest](https://www.tencentcloud.com/document/product/647/50774#174b1e8a4204caace366f2731d49efb7) | Starting mic testing (for desktop OS). |
| [startMicDeviceTest](https://www.tencentcloud.com/document/product/647/50774#776b50823f9bd88f9164c4ff10dee85c) | Starting mic testing (for desktop OS). |
| [stopMicDeviceTest](https://www.tencentcloud.com/document/product/647/50774#cd9086b5a20cf68057c2f74541781028) | Ending mic testing (for desktop OS). |
| [startSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50774#172044ecaba3934d3056dc14dd5a4306) | Starting speaker testing (for desktop OS). |
| [stopSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50774#f8ae44f6c8b4a34c2d0152009ed0447a) | Ending speaker testing (for desktop OS). |
| [startCameraDeviceTest](https://www.tencentcloud.com/document/product/647/50774#2900f3321c02eb7a4eaff1609303e416) | Starting camera testing (for desktop OS). |
| [setApplicationPlayVolume](https://www.tencentcloud.com/document/product/647/50774#2c64c587956888b01d42a98f3f6b4920) | Setting the volume of the current process in the volume mixer (for Windows). |
| [getApplicationPlayVolume](https://www.tencentcloud.com/document/product/647/50774#b174ef28c2d73868d18900a880e6fb5a) | Getting the volume of the current process in the volume mixer (for Windows). |
| [setApplicationMuteState](https://www.tencentcloud.com/document/product/647/50774#066978eb11cac8c3fb5381262d22c05f) | Muting the current process in the volume mixer (for Windows). |
| [getApplicationMuteState](https://www.tencentcloud.com/document/product/647/50774#3c79d03fa504902dd6a7dbc6f820bbe7) | Querying whether the current process is muted in the volume mixer (for Windows). |
| [setCameraCapturerParam](https://www.tencentcloud.com/document/product/647/50774#72bae8b9c2f0e059caccfee5984c5088) | Set camera acquisition preferences. |
| [setDeviceObserver](https://www.tencentcloud.com/document/product/647/50774#cd81927639621556c20a5be90371b8c0) | set onDeviceChanged callback. |
| [setSystemVolumeType](https://www.tencentcloud.com/document/product/647/50774#9356758d7c8374559bd2e82f5a23a383) | Setting the system volume type (for mobile OS). |

## StructType

| FuncList | DESC |
| --- | --- |
| [TXCameraCaptureParam](https://www.tencentcloud.com/document/product/647/50774#654f738285ec7c055a692afa6ed803ea) | Camera acquisition parameters. |
| [ITXDeviceInfo](https://www.tencentcloud.com/document/product/647/50774#f55bf48d14e276018af1339206295b6a) | Audio/Video device information (for desktop OS). |
| [ITXDeviceCollection](https://www.tencentcloud.com/document/product/647/50774#312a6009954927a114d23bee272e02b5) | Device information list (for desktop OS). |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXSystemVolumeType](https://www.tencentcloud.com/document/product/647/50774#9e22ac3a1dd66fee5bed02bc61c5e58b) | System volume type. |
| [TXAudioRoute](https://www.tencentcloud.com/document/product/647/50774#39c508dc7c357c2feda25e56f2d729c1) | Audio route (the route via which audio is played). |
| [TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) | Device type (for desktop OS). |
| [TXMediaDeviceState](https://www.tencentcloud.com/document/product/647/50774#0e59520d0b5cd9b6826a30ea0dbba8f7) | Device operation. |
| [TXCameraCaptureMode](https://www.tencentcloud.com/document/product/647/50774#aede0b6f9c933df04f1b4e096ced41e6) | Camera acquisition preferences. |

## isFrontCamera

**isFrontCamera**

**Querying whether the front camera is being used.**

## switchCamera

**switchCamera**

| int switchCamera | (bool frontCamera) |
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

| int enableCameraAutoFocus | (bool enabled) |
| --- | --- |

**Enabling auto focus (for mobile OS).**

After auto focus is enabled, the camera will automatically detect and always focus on faces.

## setCameraFocusPosition

**setCameraFocusPosition**

| int setCameraFocusPosition | (float x |
| --- | --- |
|  | float y) |

**Adjusting the focus (for mobile OS).**

This API can be used to achieve the following:

1. A user can tap on the camera preview.

2. A rectangle will appear where the user taps, indicating the spot the camera will focus on.

3. The user passes the coordinates of the spot to the SDK using this API, and the SDK will instruct the camera to focus as required.

| Param | DESC |
| --- | --- |
| position | The spot to focus on. Pass in the coordinates of the spot you want to focus on. |

> **Note**Before using this API, you must first disable auto focus using [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/50774#30fe7ff8b3ca773e2084b7b99bd43e2a).

**Return Desc:**

0: operation successful; negative number: operation failed.

## enableCameraTorch

**enableCameraTorch**

| int enableCameraTorch | (bool enabled) |
| --- | --- |

**Enabling/Disabling flash, i.e., the torch mode (for mobile OS).**

## setAudioRoute

**setAudioRoute**

| int setAudioRoute | ([TXAudioRoute](https://www.tencentcloud.com/document/product/647/50774#39c508dc7c357c2feda25e56f2d729c1) route) |
| --- | --- |

**Setting the audio route (for mobile OS).**

A mobile phone has two audio playback devices: the receiver at the top and the speaker at the bottom.

If the audio route is set to the receiver, the volume is relatively low, and audio can be heard only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.

If the audio route is set to the speaker, the volume is relatively high, and there is no need to put the phone near the ear. This mode enables the "hands-free" feature.

## getDevicesList

**getDevicesList**

| ITXDeviceCollection* getDevicesList | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) type) |
| --- | --- |

**Getting the device list (for desktop OS).**

| Param | DESC |
| --- | --- |
| type | Device type. Set it to the type of device you want to get. For details, please see the definition of [TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b). |

> **Note** To ensure that the SDK can manage the lifecycle of the ` ITXDeviceCollection ` object, after using this API, please call the ` release ` method to release the resources. Do not use ` delete ` to release the Collection object returned as deleting the ITXDeviceCollection* pointer will cause crash. The valid values of ` type ` are ` TXMediaDeviceTypeMic `, ` TXMediaDeviceTypeSpeaker `, and ` TXMediaDeviceTypeCamera `. This API can be used only on macOS and Windows.

## setCurrentDevice

**setCurrentDevice**

| int setCurrentDevice | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) type |
| --- | --- |
|  | const char* deviceId) |

**Setting the device to use (for desktop OS).**

| Param | DESC |
| --- | --- |
| deviceId | Device ID. You can get the ID of a device using the [getDevicesList](https://www.tencentcloud.com/document/product/647/50774#514e123e8955eb408ba2fddd704ad2ee) API. |
| type | Device type. For details, please see the definition of ` TXMediaDeviceType `. |

**Return Desc:**

0: operation successful; negative number: operation failed.

## getCurrentDevice

**getCurrentDevice**

| ITXDeviceInfo* getCurrentDevice | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) type) |
| --- | --- |

**Getting the device currently in use (for desktop OS).**

## setCurrentDeviceVolume

**setCurrentDeviceVolume**

| int setCurrentDeviceVolume | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) type |
| --- | --- |
|  | uint32_t volume) |

**Setting the volume of the current device (for desktop OS).**

This API is used to set the capturing volume of the mic or playback volume of the speaker, but not the volume of the camera.

| Param | DESC |
| --- | --- |
| volume | Volume. Value range: [0, 100]; default: 100 |

## getCurrentDeviceVolume

**getCurrentDeviceVolume**

| uint32_t getCurrentDeviceVolume | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) type) |
| --- | --- |

**Getting the volume of the current device (for desktop OS).**

This API is used to get the capturing volume of the mic or playback volume of the speaker, but not the volume of the camera.

## setCurrentDeviceMute

**setCurrentDeviceMute**

| int setCurrentDeviceMute | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) type |
| --- | --- |
|  | bool mute) |

**Muting the current device (for desktop OS).**

This API is used to mute the mic or speaker, but not the camera.

## getCurrentDeviceMute

**getCurrentDeviceMute**

| bool getCurrentDeviceMute | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) type) |
| --- | --- |

**Querying whether the current device is muted (for desktop OS).**

This API is used to query whether the mic or speaker is muted. Camera muting is not supported.

## enableFollowingDefaultAudioDevice

**enableFollowingDefaultAudioDevice**

| int enableFollowingDefaultAudioDevice | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b) type |
| --- | --- |
|  | bool enable) |

**Set the audio device used by SDK to follow the system default device (for desktop OS).**

This API is used to set the microphone and speaker types. Camera following the system default device is not supported.

| Param | DESC |
| --- | --- |
| enable | Whether to follow the system default audio device. true: following. When the default audio device of the system is changed or new audio device is plugged in, the SDK immediately switches the audio device. falseï¼not following. When the default audio device of the system is changed or new audio device is plugged in, the SDK doesn't switch the audio device. |
| type | Device type. For details, please see the definition of ` TXMediaDeviceType `. |

## startCameraDeviceTest

**startCameraDeviceTest**

| int startCameraDeviceTest | (void* view) |
| --- | --- |

**Starting camera testing (for desktop OS).**

> **Note**You can use the [setCurrentDevice](https://www.tencentcloud.com/document/product/647/50774#a6ce23ec66c6d809518d37600b58eede) API to switch between cameras during testing.

## stopCameraDeviceTest

**stopCameraDeviceTest**

**Ending camera testing (for desktop OS).**

## startMicDeviceTest

**startMicDeviceTest**

| int startMicDeviceTest | (uint32_t interval) |
| --- | --- |

**Starting mic testing (for desktop OS).**

This API is used to test whether the mic functions properly. The mic volume detected (value range: [0, 100]) is returned via a callback.

| Param | DESC |
| --- | --- |
| interval | Interval of volume callbacks, in milliseconds. |

> **Note**When this interface is called, the sound recorded by the microphone will be played back to the speakers by default.

## startMicDeviceTest

**startMicDeviceTest**

| int startMicDeviceTest | (uint32_t interval |
| --- | --- |
|  | bool playback) |

**Starting mic testing (for desktop OS).**

This API is used to test whether the mic functions properly. The mic volume detected (value range: [0, 100]) is returned via a callback.

| Param | DESC |
| --- | --- |
| interval | Interval of volume callbacks, in milliseconds. |
| playback | Whether to play back the microphone sound. The user will hear his own sound when testing the microphone if ` playback ` is true. |

## stopMicDeviceTest

**stopMicDeviceTest**

**Ending mic testing (for desktop OS).**

## startSpeakerDeviceTest

**startSpeakerDeviceTest**

| int startSpeakerDeviceTest | (const char* filePath) |
| --- | --- |

**Starting speaker testing (for desktop OS).**

This API is used to test whether the audio playback device functions properly by playing a specified audio file. If users can hear audio during testing, the device functions properly.

| Param | DESC |
| --- | --- |
| filePath | Path of the audio file |

## stopSpeakerDeviceTest

**stopSpeakerDeviceTest**

**Ending speaker testing (for desktop OS).**

## startCameraDeviceTest

**startCameraDeviceTest**

| int startCameraDeviceTest | ([ITRTCVideoRenderCallback](https://www.tencentcloud.com/document/product/647/50771#fce7830c6c3adc13fe5fa5da776a9da3)* callback) |
| --- | --- |

**Starting camera testing (for desktop OS).**

This API supports custom rendering, meaning that you can use the callback API ` ITRTCVideoRenderCallback ` to get the images captured by the camera for custom rendering.

## setApplicationPlayVolume

**setApplicationPlayVolume**

| int setApplicationPlayVolume | (int volume) |
| --- | --- |

**Setting the volume of the current process in the volume mixer (for Windows).**

## getApplicationPlayVolume

**getApplicationPlayVolume**

**Getting the volume of the current process in the volume mixer (for Windows).**

## setApplicationMuteState

**setApplicationMuteState**

| int setApplicationMuteState | (bool bMute) |
| --- | --- |

**Muting the current process in the volume mixer (for Windows).**

## getApplicationMuteState

**getApplicationMuteState**

**Querying whether the current process is muted in the volume mixer (for Windows).**

## setCameraCapturerParam

**setCameraCapturerParam**

| void setCameraCapturerParam | (const [TXCameraCaptureParam](https://www.tencentcloud.com/document/product/647/50774#654f738285ec7c055a692afa6ed803ea)& params) |
| --- | --- |

**Set camera acquisition preferences.**

## setDeviceObserver

**setDeviceObserver**

| void setDeviceObserver | (ITXDeviceObserver* observer) |
| --- | --- |

**set onDeviceChanged callback.**

## setSystemVolumeType

**setSystemVolumeType**

| int setSystemVolumeType | ([TXSystemVolumeType](https://www.tencentcloud.com/document/product/647/50774#9e22ac3a1dd66fee5bed02bc61c5e58b) type) |
| --- | --- |

**Setting the system volume type (for mobile OS).**

@deprecated This API is not recommended after v9.5. Please use the ` startLocalAudio(quality) ` API in ` TRTCCloud ` instead, which param ` quality ` is used to decide audio quality.

## TXSystemVolumeType(Deprecated)

**TXSystemVolumeType(Deprecated)**

**System volume type.**

| Enum | Value | DESC |
| --- | --- | --- |
| TXSystemVolumeTypeAuto | 0 | Auto |
| TXSystemVolumeTypeMedia | 1 | Media volume |
| TXSystemVolumeTypeVOIP | 2 | Call volume |

## TXAudioRoute

**TXAudioRoute**

**Audio route (the route via which audio is played).**

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

**Device type (for desktop OS).**

This enumerated type defines three types of audio/video devices, namely camera, mic and speaker, so that you can use the same device management API to manage three types of devices.

| Enum | Value | DESC |
| --- | --- | --- |
| TXMediaDeviceTypeUnknown | -1 | undefined device type |
| TXMediaDeviceTypeMic | 0 | microphone |
| TXMediaDeviceTypeSpeaker | 1 | speaker or earpiece |
| TXMediaDeviceTypeCamera | 2 | camera |

## TXMediaDeviceState

**TXMediaDeviceState**

**Device operation.**

This enumerated value is used to notify the status change of the local device onDeviceChanged.

| Enum | Value | DESC |
| --- | --- | --- |
| TXMediaDeviceStateAdd | 0 | The device has been plugged in |
| TXMediaDeviceStateRemove | 1 | The device has been removed |
| TXMediaDeviceStateActive | 2 | The device has been enabled |
| TXMediaDefaultDeviceChanged | 3 | system default device changed |

## TXCameraCaptureMode

**TXCameraCaptureMode**

**Camera acquisition preferences.**

This enum is used to set camera acquisition parameters.

| Enum | Value | DESC |
| --- | --- | --- |
| TXCameraResolutionStrategyAuto | 0 | Auto adjustment of camera capture parameters.SDK selects the appropriate camera output parameters according to the actual acquisition device performance and network situation, and maintains a balance between device performance and video preview quality. |
| TXCameraResolutionStrategyPerformance | 1 | Give priority to equipment performance.SDK selects the closest camera output parameters according to the user's encoder resolution and frame rate, so as to ensure the performance of the device. |
| TXCameraResolutionStrategyHighQuality | 2 | Give priority to the quality of video preview.SDK selects higher camera output parameters to improve the quality of preview video. In this case, it will consume more CPU and memory to do video preprocessing. |
| TXCameraCaptureManual | 3 | Allows the user to set the width and height of the video captured by the local camera. |

## TXCameraCaptureParam

**TXCameraCaptureParam**

**Camera acquisition parameters.**

This setting determines the quality of the local preview image.

| EnumType | DESC |
| --- | --- |
| height | Field description:  height of acquired image |
| mode | Field description: camera acquisition preferences,please see [TXCameraCaptureMode](https://www.tencentcloud.com/document/product/647/50774#aede0b6f9c933df04f1b4e096ced41e6) |
| width | Field description: width of acquired image |

## TXMediaDeviceInfo

**TXMediaDeviceInfo**

**Audio/Video device information (for desktop OS).**

This structure describes key information (such as device ID and device name) of an audio/video device, so that users can choose on the UI the device to use.

| EnumType | DESC |
| --- | --- |
| getDeviceName() | device name (UTF-8) |
| getDevicePID() | device id (UTF-8) |

## ITXDeviceCollection

**ITXDeviceCollection**

**Device information list (for desktop OS).**

This structure functions as std::vector<ITXDeviceInfo> does. It solves the binary compatibility issue between different versions of STL containers.

| EnumType | DESC |
| --- | --- |
| getCount() | Size of this list. return Size of this list. |
| index) | device properties (json format)**Note**  examples: {"SupportedResolution":[{"width":640,"height":480},{"width":320,"height":240}]}param index value in [0,getCount),return device properties formatted by json |
| release() | release function, don't use delete!!! |


---
*Source: [https://trtc.io/document/50774](https://trtc.io/document/50774)*
