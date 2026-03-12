# TXDeviceManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: audio/video device management module

Description: manages audio/video devices such as camera, mic, and speaker.

**TXDeviceManager**

## TXDeviceObserver

| FuncList | DESC |
| --- | --- |
| [onDeviceChanged:type:state:](https://www.tencentcloud.com/document/product/647/50759#dfd15b3a97c8d91d85618afb47ea252f) | The status of a local device changed (for desktop OS only). |

## TXDeviceManager

| FuncList | DESC |
| --- | --- |
| [isFrontCamera](https://www.tencentcloud.com/document/product/647/50759#6d3ec289d7e2325835e0d1da358103a6) | Querying whether the front camera is being used. |
| [switchCamera:](https://www.tencentcloud.com/document/product/647/50759#a6c41b29145df78c75f83db394a5757d) | Switching to the front/rear camera (for mobile OS). |
| [isCameraZoomSupported](https://www.tencentcloud.com/document/product/647/50759#3d221dfef2379ff2d7465873b190d279) | Querying whether the current camera supports zooming (for mobile OS). |
| [getCameraZoomMaxRatio](https://www.tencentcloud.com/document/product/647/50759#36e2b33316fc8b7a9d4ba089594c77ff) | Getting the maximum zoom ratio of the camera (for mobile OS). |
| [setCameraZoomRatio:](https://www.tencentcloud.com/document/product/647/50759#aa61befc4a161b72e2a3eb9703e8ab8a) | Setting the camera zoom ratio (for mobile OS). |
| [isAutoFocusEnabled](https://www.tencentcloud.com/document/product/647/50759#a8d8a4fa66b628c21a080177204744b2) | Querying whether automatic face detection is supported (for mobile OS). |
| [enableCameraAutoFocus:](https://www.tencentcloud.com/document/product/647/50759#b73d99629f1936b786b6ada790e458dd) | Enabling auto focus (for mobile OS). |
| [setCameraFocusPosition:](https://www.tencentcloud.com/document/product/647/50759#2f2ceca9ad0f46650334e6b5aa813633) | Adjusting the focus (for mobile OS). |
| [isCameraTorchSupported](https://www.tencentcloud.com/document/product/647/50759#0f67ffd852a08dc7735f51d3b3f0f163) | Querying whether flash is supported (for mobile OS). |
| [enableCameraTorch:](https://www.tencentcloud.com/document/product/647/50759#bf86fe99b08324c7114c2da6875baca9) | Enabling/Disabling flash, i.e., the torch mode (for mobile OS). |
| [setAudioRoute:](https://www.tencentcloud.com/document/product/647/50759#669f49baa33336be868377f8bc8e6f32) | Setting the audio route (for mobile OS). |
| [setExposureCompensation:](https://www.tencentcloud.com/document/product/647/50759#da0dea11c433416dc2b20e27937bc92f) | Set the exposure parameters of the camera, ranging from - 1 to 1. |
| [getDevicesList:](https://www.tencentcloud.com/document/product/647/50759#cf4514b579d88cadae56a424baeb110f) | Getting the device list (for desktop OS). |
| [setCurrentDevice:deviceId:](https://www.tencentcloud.com/document/product/647/50759#1c0a01aa96ce0aa6c596c654041fbee6) | Setting the device to use (for desktop OS). |
| [getCurrentDevice:](https://www.tencentcloud.com/document/product/647/50759#c56fd31ac73ceda8a28d9f4bfe834bbd) | Getting the device currently in use (for desktop OS). |
| [setCurrentDeviceVolume:deviceType:](https://www.tencentcloud.com/document/product/647/50759#aefc135c5b1cf942a4d7445274fa2465) | Setting the volume of the current device (for desktop OS). |
| [getCurrentDeviceVolume:](https://www.tencentcloud.com/document/product/647/50759#1fc1b55bc7722cc70a07302e46507467) | Getting the volume of the current device (for desktop OS). |
| [setCurrentDeviceMute:deviceType:](https://www.tencentcloud.com/document/product/647/50759#647a252eb815bae8854023af3717a79f) | Muting the current device (for desktop OS). |
| [getCurrentDeviceMute:](https://www.tencentcloud.com/document/product/647/50759#7b46a3e3052b4b59e685fb8365c3955d) | Querying whether the current device is muted (for desktop OS). |
| [enableFollowingDefaultAudioDevice:enable:](https://www.tencentcloud.com/document/product/647/50759#f1a3e4a48a4a2e81e7d0eee4c9f37bb7) | Set the audio device used by SDK to follow the system default device (for desktop OS). |
| [startCameraDeviceTest:](https://www.tencentcloud.com/document/product/647/50759#e2d8e209071fef8bbf78f16971bae39f) | Starting camera testing (for desktop OS). |
| [stopCameraDeviceTest](https://www.tencentcloud.com/document/product/647/50759#30be4cfa94699be138130c1919b3af68) | Ending camera testing (for desktop OS). |
| [startMicDeviceTest:](https://www.tencentcloud.com/document/product/647/50759#3dce7bfcf95708a5ce69f5ce7baad6f4) | Starting mic testing (for desktop OS). |
| [startMicDeviceTest:playback:](https://www.tencentcloud.com/document/product/647/50759#f4002f97005e59258de6fe5088ae75b8) | Starting mic testing (for desktop OS). |
| [stopMicDeviceTest](https://www.tencentcloud.com/document/product/647/50759#d0adbc1fbeae9620cf4c78d06b24d26e) | Ending mic testing (for desktop OS). |
| [startSpeakerDeviceTest:](https://www.tencentcloud.com/document/product/647/50759#e4ac7cc2a6dbecee30b0b4a9a17ce3b3) | Starting speaker testing (for desktop OS). |
| [stopSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50759#d9f52ca878aa99ec873170b4bc394f11) | Ending speaker testing (for desktop OS). |
| [setObserver:](https://www.tencentcloud.com/document/product/647/50759#e277523e1a2b2426d66ef6fdecae1fb8) | set onDeviceChanged callback (for Mac). |
| [setCameraCapturerParam:](https://www.tencentcloud.com/document/product/647/50759#0d4167b17f3b52529be4b7a04f648a0d) | Set camera acquisition preferences. |
| [setSystemVolumeType:](https://www.tencentcloud.com/document/product/647/50759#632301e178fc664876e5888669368049) | Setting the system volume type (for mobile OS). |

## StructType

| FuncList | DESC |
| --- | --- |
| [TXCameraCaptureParam](https://www.tencentcloud.com/document/product/647/50759#654f738285ec7c055a692afa6ed803ea) | Camera acquisition parameters. |
| [TXMediaDeviceInfo](https://www.tencentcloud.com/document/product/647/50759#39885544680b92cd423ccc7141a3fe96) | Audio/Video device information (for desktop OS). |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXSystemVolumeType](https://www.tencentcloud.com/document/product/647/50759#9e22ac3a1dd66fee5bed02bc61c5e58b) | System volume type. |
| [TXAudioRoute](https://www.tencentcloud.com/document/product/647/50759#39c508dc7c357c2feda25e56f2d729c1) | Audio route (the route via which audio is played). |
| [TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b) | Device type (for desktop OS). |
| [TXMediaDeviceState](https://www.tencentcloud.com/document/product/647/50759#0e59520d0b5cd9b6826a30ea0dbba8f7) | Device operation. |
| [TXCameraCaptureMode](https://www.tencentcloud.com/document/product/647/50759#aede0b6f9c933df04f1b4e096ced41e6) | Camera acquisition preferences. |

## onDeviceChanged:type:state:

**onDeviceChanged:type:state:**

| - (void)onDeviceChanged: | (NSString*)deviceId |
| --- | --- |
| type: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))mediaType |
| state: | ([TXMediaDeviceState](https://www.tencentcloud.com/document/product/647/50759#0e59520d0b5cd9b6826a30ea0dbba8f7))mediaState |

**The status of a local device changed (for desktop OS only).**

The SDK returns this callback when a local device (camera, mic, or speaker) is connected or disconnected.

| Param | DESC |
| --- | --- |
| deviceId | Device ID |
| state | Device status. ` 0 `: connected; ` 1 `: disconnected; ` 2 `: started |
| type | Device type |

## isFrontCamera

**isFrontCamera**

**Querying whether the front camera is being used.**

## switchCamera:

**switchCamera:**

| - (NSInteger)switchCamera: | (BOOL)frontCamera |
| --- | --- |

**Switching to the front/rear camera (for mobile OS).**

## isCameraZoomSupported

**isCameraZoomSupported**

**Querying whether the current camera supports zooming (for mobile OS).**

## getCameraZoomMaxRatio

**getCameraZoomMaxRatio**

**Getting the maximum zoom ratio of the camera (for mobile OS).**

## setCameraZoomRatio:

**setCameraZoomRatio:**

| - (NSInteger)setCameraZoomRatio: | (CGFloat)zoomRatio |
| --- | --- |

**Setting the camera zoom ratio (for mobile OS).**

| Param | DESC |
| --- | --- |
| zoomRatio | Value range: [1, 5]. 1 indicates the widest angle of view (original), and 5 the narrowest angle of view (zoomed in).The maximum value is recommended to be 5. If the value exceeds 5, the video will become blurred. |

## isAutoFocusEnabled

**isAutoFocusEnabled**

**Querying whether automatic face detection is supported (for mobile OS).**

## enableCameraAutoFocus:

**enableCameraAutoFocus:**

| - (NSInteger)enableCameraAutoFocus: | (BOOL)enabled |
| --- | --- |

**Enabling auto focus (for mobile OS).**

After auto focus is enabled, the camera will automatically detect and always focus on faces.

## setCameraFocusPosition:

**setCameraFocusPosition:**

| - (NSInteger)setCameraFocusPosition: | (CGPoint)position |
| --- | --- |

**Adjusting the focus (for mobile OS).**

This API can be used to achieve the following:

1. A user can tap on the camera preview.

2. A rectangle will appear where the user taps, indicating the spot the camera will focus on.

3. The user passes the coordinates of the spot to the SDK using this API, and the SDK will instruct the camera to focus as required.

| Param | DESC |
| --- | --- |
| position | The spot to focus on. Pass in the coordinates of the spot you want to focus on. |

> **Note**Before using this API, you must first disable auto focus using [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/50759#b73d99629f1936b786b6ada790e458dd).

**Return Desc:**

0: operation successful; negative number: operation failed.

## isCameraTorchSupported

**isCameraTorchSupported**

**Querying whether flash is supported (for mobile OS).**

## enableCameraTorch:

**enableCameraTorch:**

| - (NSInteger)enableCameraTorch: | (BOOL)enabled |
| --- | --- |

**Enabling/Disabling flash, i.e., the torch mode (for mobile OS).**

## setAudioRoute:

**setAudioRoute:**

| - (NSInteger)setAudioRoute: | ([TXAudioRoute](https://www.tencentcloud.com/document/product/647/50759#39c508dc7c357c2feda25e56f2d729c1))route |
| --- | --- |

**Setting the audio route (for mobile OS).**

A mobile phone has two audio playback devices: the receiver at the top and the speaker at the bottom.

If the audio route is set to the receiver, the volume is relatively low, and audio can be heard only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.

If the audio route is set to the speaker, the volume is relatively high, and there is no need to put the phone near the ear. This mode enables the "hands-free" feature.

## setExposureCompensation:

**setExposureCompensation:**

| - (NSInteger)setExposureCompensation: | (CGFloat)value |
| --- | --- |

**Set the exposure parameters of the camera, ranging from - 1 to 1.**

## getDevicesList:

**getDevicesList:**

| - (NSArray<TXMediaDeviceInfo *> * _Nullable)getDevicesList: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))type |
| --- | --- |

**Getting the device list (for desktop OS).**

| Param | DESC |
| --- | --- |
| type | Device type. Set it to the type of device you want to get. For details, please see the definition of [TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b). |

> **Note** To ensure that the SDK can manage the lifecycle of the ` ITXDeviceCollection ` object, after using this API, please call the ` release ` method to release the resources. Do not use ` delete ` to release the Collection object returned as deleting the ITXDeviceCollection* pointer will cause crash. The valid values of ` type ` are ` TXMediaDeviceTypeMic `, ` TXMediaDeviceTypeSpeaker `, and ` TXMediaDeviceTypeCamera `. This API can be used only on macOS and Windows.

## setCurrentDevice:deviceId:

**setCurrentDevice:deviceId:**

| - (NSInteger)setCurrentDevice: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))type |
| --- | --- |
| deviceId: | (NSString *)deviceId |

**Setting the device to use (for desktop OS).**

| Param | DESC |
| --- | --- |
| deviceId | Device ID. You can get the ID of a device using the [getDevicesList](https://www.tencentcloud.com/document/product/647/50759#cf4514b579d88cadae56a424baeb110f) API. |
| type | Device type. For details, please see the definition of ` TXMediaDeviceType `. |

**Return Desc:**

0: operation successful; negative number: operation failed.

## getCurrentDevice:

**getCurrentDevice:**

| - (TXMediaDeviceInfo * _Nullable)getCurrentDevice: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))type |
| --- | --- |

**Getting the device currently in use (for desktop OS).**

## setCurrentDeviceVolume:deviceType:

**setCurrentDeviceVolume:deviceType:**

| - (NSInteger)setCurrentDeviceVolume: | (NSInteger)volume |
| --- | --- |
| deviceType: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))type |

**Setting the volume of the current device (for desktop OS).**

This API is used to set the capturing volume of the mic or playback volume of the speaker, but not the volume of the camera.

| Param | DESC |
| --- | --- |
| volume | Volume. Value range: [0, 100]; default: 100 |

## getCurrentDeviceVolume:

**getCurrentDeviceVolume:**

| - (NSInteger)getCurrentDeviceVolume: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))type |
| --- | --- |

**Getting the volume of the current device (for desktop OS).**

This API is used to get the capturing volume of the mic or playback volume of the speaker, but not the volume of the camera.

## setCurrentDeviceMute:deviceType:

**setCurrentDeviceMute:deviceType:**

| - (NSInteger)setCurrentDeviceMute: | (BOOL)mute |
| --- | --- |
| deviceType: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))type |

**Muting the current device (for desktop OS).**

This API is used to mute the mic or speaker, but not the camera.

## getCurrentDeviceMute:

**getCurrentDeviceMute:**

| - (BOOL)getCurrentDeviceMute: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))type |
| --- | --- |

**Querying whether the current device is muted (for desktop OS).**

This API is used to query whether the mic or speaker is muted. Camera muting is not supported.

## enableFollowingDefaultAudioDevice:enable:

**enableFollowingDefaultAudioDevice:enable:**

| - (NSInteger)enableFollowingDefaultAudioDevice: | ([TXMediaDeviceType](https://www.tencentcloud.com/document/product/647/50759#f023a4d94be317eb399df83a25af6b2b))type |
| --- | --- |
| enable: | (BOOL)enable |

**Set the audio device used by SDK to follow the system default device (for desktop OS).**

This API is used to set the microphone and speaker types. Camera following the system default device is not supported.

| Param | DESC |
| --- | --- |
| enable | Whether to follow the system default audio device. true: following. When the default audio device of the system is changed or new audio device is plugged in, the SDK immediately switches the audio device. falseï¼not following. When the default audio device of the system is changed or new audio device is plugged in, the SDK doesn't switch the audio device. |
| type | Device type. For details, please see the definition of ` TXMediaDeviceType `. |

## startCameraDeviceTest:

**startCameraDeviceTest:**

| - (NSInteger)startCameraDeviceTest: | (NSView *)view |
| --- | --- |

**Starting camera testing (for desktop OS).**

> **Note**You can use the [setCurrentDevice](https://www.tencentcloud.com/document/product/647/50759#1c0a01aa96ce0aa6c596c654041fbee6) API to switch between cameras during testing.

## stopCameraDeviceTest

**stopCameraDeviceTest**

**Ending camera testing (for desktop OS).**

## startMicDeviceTest:

**startMicDeviceTest:**

| - (NSInteger)startMicDeviceTest: | (NSInteger)interval |
| --- | --- |

**Starting mic testing (for desktop OS).**

This API is used to test whether the mic functions properly. The mic volume detected (value range: [0, 100]) is returned via a callback.

| Param | DESC |
| --- | --- |
| interval | Interval of volume callbacks, in milliseconds. |

> **Note**When this interface is called, the sound recorded by the microphone will be played back to the speakers by default.

## startMicDeviceTest:playback:

**startMicDeviceTest:playback:**

| - (NSInteger)startMicDeviceTest: | (NSInteger)interval |
| --- | --- |
| playback: | (BOOL)playback |

**Starting mic testing (for desktop OS).**

This API is used to test whether the mic functions properly. The mic volume detected (value range: [0, 100]) is returned via a callback.

| Param | DESC |
| --- | --- |
| interval | Interval of volume callbacks, in milliseconds. |
| playback | Whether to play back the microphone sound. The user will hear his own sound when testing the microphone if ` playback ` is true. |

## stopMicDeviceTest

**stopMicDeviceTest**

**Ending mic testing (for desktop OS).**

## startSpeakerDeviceTest:

**startSpeakerDeviceTest:**

| - (NSInteger)startSpeakerDeviceTest: | (NSString *)audioFilePath |
| --- | --- |

**Starting speaker testing (for desktop OS).**

This API is used to test whether the audio playback device functions properly by playing a specified audio file. If users can hear audio during testing, the device functions properly.

| Param | DESC |
| --- | --- |
| filePath | Path of the audio file |

## stopSpeakerDeviceTest

**stopSpeakerDeviceTest**

**Ending speaker testing (for desktop OS).**

## setObserver:

**setObserver:**

| - (void)setObserver: | (nullable id<[TXDeviceObserver](https://www.tencentcloud.com/document/product/647/50759#57dea2455f64baf02792e6d2d227e200)>) observer |
| --- | --- |

**set onDeviceChanged callback (for Mac).**

## setCameraCapturerParam:

**setCameraCapturerParam:**

| - (void)setCameraCapturerParam: | ([TXCameraCaptureParam](https://www.tencentcloud.com/document/product/647/50759#654f738285ec7c055a692afa6ed803ea) *)params |
| --- | --- |

**Set camera acquisition preferences.**

## setSystemVolumeType:

**setSystemVolumeType:**

| - (NSInteger)setSystemVolumeType: | ([TXSystemVolumeType](https://www.tencentcloud.com/document/product/647/50759#9e22ac3a1dd66fee5bed02bc61c5e58b))type |
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
| TXMediaDeviceTypeAudioInput | 0 | microphone |
| TXMediaDeviceTypeAudioOutput | 1 | speaker or earpiece |
| TXMediaDeviceTypeVideoCamera | 2 | camera |

## TXMediaDeviceState

**TXMediaDeviceState**

**Device operation.**

This enumerated value is used to notify the status change of the local device [onDeviceChanged](https://www.tencentcloud.com/document/product/647/50759#dfd15b3a97c8d91d85618afb47ea252f).

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
| mode | Field description: camera acquisition preferences,please see [TXCameraCaptureMode](https://www.tencentcloud.com/document/product/647/50759#aede0b6f9c933df04f1b4e096ced41e6) |
| width | Field description: width of acquired image |

## TXMediaDeviceInfo

**TXMediaDeviceInfo**

**Audio/Video device information (for desktop OS).**

This structure describes key information (such as device ID and device name) of an audio/video device, so that users can choose on the UI the device to use.

| EnumType | DESC |
| --- | --- |
| deviceId | device id (UTF-8) |
| deviceName | device name (UTF-8) |
| deviceProperties | device properties |
| type | device type |


---
*Source: [https://trtc.io/document/50759](https://trtc.io/document/50759)*
