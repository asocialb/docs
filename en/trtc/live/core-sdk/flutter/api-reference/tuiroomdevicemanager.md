# TUIRoomDeviceManager

**TUIRoomDeviceManager**

## TUIRoomDeviceManager

| Function List | Description |
| --- | --- |
| [isFrontCamera](https://www.tencentcloud.com/document/product/647/67261#isFrontCamera) | Determine whether the current camera is front-facing (only for mobile terminal) |
| [switchCamera](https://www.tencentcloud.com/document/product/647/67261#switchCamera) | Switch between front and rear cameras (only for mobile terminal) |
| [isAutoFocusEnabled](https://www.tencentcloud.com/document/product/647/67261#isAutoFocusEnabled) | Check if automatic face position recognition is supported (only for mobile terminal) |
| [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/67261#enableCameraAutoFocus) | Enable autofocus feature (only for mobile terminal) |
| [enableCameraTorch](https://www.tencentcloud.com/document/product/647/67261#enableCameraTorch) | Turn the flash on/off, also known as flashlight mode (only for mobile terminal) |
| [setAudioRoute](https://www.tencentcloud.com/document/product/647/67261#setAudioRoute) | Set audio routing (only for mobile terminal) |

## Enumeration Types

| Enumeration Types | Description |
| --- | --- |
| [AudioRoute](https://www.tencentcloud.com/document/product/647/67261#AudioRoute) | Audio routing (i.e., sound playback mode) |

## isFrontCamera

**isFrontCamera**

#### Determine whether the current camera is front-facing (only for mobile terminal)

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

## switchCamera

**switchCamera**

| void switchCamera | (boolean frontCamera) |
| --- | --- |

#### Switch between front and rear cameras (only for mobile terminal)

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

## isAutoFocusEnabled

**isAutoFocusEnabled**

#### Check if automatic face position recognition is supported (only for mobile terminal)

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

## enableCameraAutoFocus

**enableCameraAutoFocus**

| void enableCameraAutoFocus | (boolean enabled) |
| --- | --- |

#### Enable autofocus feature (only for mobile terminal)

Once enabled, the SDK will automatically detect the face position in the frame and keep the camera focus on the face position.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

## enableCameraTorch

**enableCameraTorch**

| void enableCameraTorch | (boolean enable) |
| --- | --- |

#### Turn the flash on/off, also known as flashlight mode (only for mobile terminal)

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

## setAudioRoute

**setAudioRoute**

| void setAudioRoute | ([TUIAudioRoute](https://www.tencentcloud.com/document/product/647/67261#AudioRoute) route) |
| --- | --- |

#### Set audio routing (only for mobile terminal)

A phone has two audio playback devices: one is the earpiece at the top of the phone, and the other is the stereo speaker at the bottom of the phone.

When the audio routing is set to the earpiece, the sound is relatively low, and you need to bring your ear close to hear it clearly, ensuring better privacy. It is suitable for phone calls.

When the audio routing is set to the speaker, the sound is relatively loud. You can hear it clearly without holding the phone to your face, thus enabling the "hands-free" feature.

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).

## TUIAudioRoute

**TUIAudioRoute**

#### Audio routing (i.e., sound playback mode)

Audio routing, that is, whether the sound is played through the phone's speaker or earpiece. Therefore, this interface is only applicable to mobile devices.

A mobile phone has two speakers: one is the earpiece located at the top of the phone, and the other is the stereo speaker located at the bottom.

- When the audio routing is set to the earpiece, the sound is relatively low, and you need to bring your ear close to hear it clearly, ensuring better privacy. It is suitable for phone calls.
- When the audio routing is set to the speaker, the sound is relatively loud. You can hear it clearly without holding the phone to your face, thus enabling the "hands-free" feature.

| Enumeration | Value | Description |
| --- | --- | --- |
| speakerphone | 0 | Speakerphone: Play sound through the speaker (i.e., "hands-free"), which is located at the bottom of the phone. The volume tends to be loud, suitable for playing music out loud. |
| earpiece | 1 | Earpiece: Plays through the earpiece, the earpiece is located at the top of the phone, the sound is small, suitable for privacy-protected call scenarios. |

> **Note:**This function applies to conference room type and live room type ([conference & livingRoom](https://www.tencentcloud.com/document/product/647/67259#RoomType)).


---
*Source: [https://trtc.io/document/67261](https://trtc.io/document/67261)*
