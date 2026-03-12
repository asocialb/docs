# Error Codes

Copyright (c) 2021 Tencent. All rights reserved.

Module:   TRTC ErrorCode

Function: Used to notify customers of warnings and errors that occur during the use of TRTC

**ErrorCode**

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXLiteAVError](https://www.tencentcloud.com/document/product/647/40140#bb60aec5429af9dd69df09c23f924e96) | Error Codes. |

## TXLiteAVError

**TXLiteAVError**

#### Error Codes.

| Enum | Value | DESC |
| --- | --- | --- |
| ERR_NULL | 0 | No error. |
| ERR_CAMERA_START_FAIL | -1301 | Failed to turn the camera on. After authorization, calling the system interface to open the camera was abnormal on mobile. This may occur when there is a problem with the camera configuration program (driver) on Windows or macOS. Disable and reenable the camera, restart the camera, or update the configuration program. |
| ERR_CAMERA_NOT_AUTHORIZED | -1314 | No permission to access to the camera. This usually occurs on mobile devices and may be because the user denied access. |
| ERR_CAMERA_SET_PARAM_FAIL | -1315 | Incorrect camera parameter settings (unsupported values or others). |
| ERR_CAMERA_OCCUPY | -1316 | The camera is being used. Try another camera. |
| ERR_VIDEO_ENCODE_FAIL | -1303 | Failed to encode video frames. Encoder exception caused encoding failure. |
| ERR_UNSUPPORTED_RESOLUTION | -1305 | Unsupported video resolution. |
| ERR_PIXEL_FORMAT_UNSUPPORTED | -1327 | Custom video capturing: Unsupported pixel format. |
| ERR_BUFFER_TYPE_UNSUPPORTED | -1328 | Custom video capturing: Unsupported buffer type. |
| ERR_MIC_START_FAIL | -1302 | Failed to turn the mic on. This may occur when there is a problem with the mic configuration program (driver) on Windows or macOS. Disable and reenable the mic, restart the mic, or update the configuration program. |
| ERR_MIC_NOT_AUTHORIZED | -1317 | No permission to access to the mic. This usually occurs on mobile devices and may be because the user denied access. |
| ERR_MIC_OCCUPY | -1319 | The mic is being used. The mic cannot be turned on when, for example, the user is having a call on the mobile device. |
| ERR_MIC_STOP_FAIL | -1320 | Failed to turn the mic off. |
| ERR_SPEAKER_START_FAIL | -1321 | Failed to turn the speaker on. This may occur when there is a problem with the speaker configuration program (driver) on Windows or macOS. Disable and reenable the speaker, restart the speaker, or update the configuration program. |
| ERR_SPEAKER_SET_PARAM_FAIL | -1322 | Failed to set speaker parameters. |
| ERR_SPEAKER_STOP_FAIL | -1323 | Failed to turn the speaker off. |
| ERR_AUDIO_PLUGIN_START_FAIL | -1330 | Failed to record computer audio, which may be because the audio driver is unavailable. |
| ERR_AUDIO_PLUGIN_INSTALL_NOT_AUTHORIZED | -1331 | No permission to install the audio driver. |
| ERR_AUDIO_PLUGIN_INSTALL_FAILED | -1332 | Failed to install the audio driver. |
| ERR_AUDIO_PLUGIN_INSTALLED_BUT_NEED_RESTART | -1333 | The virtual sound card is installed successfully, but due to the restrictions of macOS, you cannot use it right after installation. Ask users to restart the app upon receiving this error code. |
| ERR_AUDIO_ENCODE_FAIL | -1304 | Failed to encode audio frames. This may occur if the SDK could not process the custom audio data passed in. |
| ERR_UNSUPPORTED_SAMPLERATE | -1306 | Unsupported audio sample rate. |
| ERR_ROOM_ENTER_FAIL | -3301 | Failed to enter the room. For the reason, refer to the error message for -3301 in ` onError `. |
| ERR_ROOM_REQUEST_ENTER_ROOM_TIMEOUT | -3308 | Room entry request timed out. Check your network connection and whether VPN is used. You can also switch to 4G to run a test. |
| ERR_ENTER_ROOM_PARAM_NULL | -3316 | Empty room entry parameters. Please check whether valid parameters were passed in to the ` enterRoom:appScene: ` API. |
| ERR_SDK_APPID_INVALID | -3317 | Incorrect room entry parameter. Check whether ` TRTCParams.sdkAppId ` is empty. |
| ERR_ROOM_ID_INVALID | -3318 | Incorrect room entry parameter. Check whether ` TRTCParams.roomId ` or ` TRTCParams.strRoomId ` is empty. Note that you cannot set both parameters. |
| ERR_USER_ID_INVALID | -3319 | Incorrect room entry parameter. Check whether ` TRTCParams.userId ` is empty. |
| ERR_USER_SIG_INVALID | -3320 | Incorrect room entry parameter. Check whether ` TRTCParams.userSig ` is empty. |
| ERR_SERVER_INFO_SERVICE_SUSPENDED | -100013 | The service is unavailable. Check if you have used up your package or whether your Tencent Cloud account has overdue payments. |
| ERR_SERVER_INFO_ECDH_GET_TINYID | -100018 | Failed to verify ` UserSig `. Check whether ` TRTCParams.userSig ` is correct or valid.For details, see [UserSig Generation and Verification](https://intl.cloud.tencent.com/document/product/647/39074). |
| WARNING_HW_ENCODER_START_FAIL | 1103 | Failed to start the hardware encoder. Switched to software encoding. |
| WARNING_VIDEO_ENCODER_SW_TO_HW | 1107 | Insufficient CPU for software encoding. Switched to hardware encoding. |
| WARNING_INSUFFICIENT_CAPTURE_FPS | 1108 | The capturing frame rate of the camera is insufficient. This error occurs on some Android phones with built-in beauty filters. |
| WARNING_SW_ENCODER_START_FAIL | 1109 | Failed to start the software encoder. |
| WARNING_REDUCE_CAPTURE_RESOLUTION | 1110 | The capturing frame rate of the camera was reduced for balance between frame rate and performance. |
| WARNING_CAMERA_DEVICE_EMPTY | 1111 | No available camera found. |
| WARNING_CAMERA_NOT_AUTHORIZED | 1112 | The user didnât grant the application camera permission. |
| WARNING_CAMERA_IS_OCCUPIED | 1114 | The camera is occupied. |
| WARNING_CAMERA_DEVICE_ERROR | 1115 | The camera device is error. |
| WARNING_CAMERA_DISCONNECTED | 1116 | The camera is disconnected. |
| WARNING_CAMERA_START_FAILED | 1117 | The camera is started failed. |
| WARNING_CAMERA_SERVER_DIED | 1118 | The camera sever is died. |
| WARNING_SCREEN_CAPTURE_NOT_AUTHORIZED | 1206 | The user didnât grant the application screen recording permission. |
| WARNING_VIDEO_FRAME_DECODE_FAIL | 2101 | Failed to decode the current video frame. |
| WARNING_HW_DECODER_START_FAIL | 2106 | Failed to start the hardware decoder. The software decoder is used instead. |
| WARNING_VIDEO_DECODER_HW_TO_SW | 2108 | The hardware decoder failed to decode the first I-frame of the current stream. The SDK automatically switched to the software decoder. |
| WARNING_SW_DECODER_START_FAIL | 2109 | Failed to start the software decoder. |
| WARNING_VIDEO_RENDER_FAIL | 2110 | Failed to render the video. |
| WARNING_MICROPHONE_DEVICE_EMPTY | 1201 | No available mic found. |
| WARNING_SPEAKER_DEVICE_EMPTY | 1202 | No available speaker found. |
| WARNING_MICROPHONE_NOT_AUTHORIZED | 1203 | The user didnât grant the application mic permission. |
| WARNING_MICROPHONE_DEVICE_ABNORMAL | 1204 | The audio capturing device is unavailable (which may be because the device is used by another application or is considered invalid by the system). |
| WARNING_SPEAKER_DEVICE_ABNORMAL | 1205 | The audio playback device is unavailable (which may be because the device is used by another application or is considered invalid by the system). |
| WARNING_BLUETOOTH_DEVICE_CONNECT_FAIL | 1207 | The bluetooth device failed to connect (which may be because another app is occupying the audio channel by setting communication mode). |
| WARNING_MICROPHONE_IS_OCCUPIED | 1208 | The audio capturing device is occupied. |
| WARNING_AUDIO_FRAME_DECODE_FAIL | 2102 | Failed to decode the current audio frame. |
| WARNING_AUDIO_RECORDING_WRITE_FAIL | 7001 | Failed to write recorded audio into the file. |
| WARNING_MICROPHONE_HOWLING_DETECTED | 7002 | Detect capture audio howling |
| WARNING_IGNORE_UPSTREAM_FOR_AUDIENCE | 6001 | The current user is an audience member and cannot publish audio or video. Please switch to an anchor first. |
| WARNING_UPSTREAM_AUDIO_AND_VIDEO_OUT_OF_SYNC | 6006 | The audio or video sending timestamps are abnormal, which may cause audio and video synchronization issues. |
| WARNING_RECONNECT_ON_SERVER_STATUS_ABNORMAL | 6007 | The server status is abnormal and reconnecting is in progress |


---
*Source: [https://trtc.io/document/40140](https://trtc.io/document/40140)*
