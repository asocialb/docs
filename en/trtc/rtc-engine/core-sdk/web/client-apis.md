# Client APIs

## API Details

### TRTC

1. [TRTC](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html) is the main entry for TRTC SDK, providing APIs such as create trtc instance([TRTC.create](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.create)), [TRTC.getCameraList](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.getCameraList), [TRTC.getMicrophoneList](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.getMicrophoneList),  [TRTC.isSupported](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.isSupported).
2. [trtc](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html) instance, provides the core capability for real-time audio and video calls.
  - Enter room [trtc.enterRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom)
  - Exit room [trtc.exitRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#exitRoom)
  - Turn on camera [trtc.startLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo)
  - Turn on microphone [trtc.startLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalAudio)
  - Turn off camera [trtc.stopLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalVideo)
  - Turn off microphone [trtc.stopLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalAudio)
  - Play remote video [trtc.startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo)
  - Stop playing remote video [trtc.stopRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopRemoteVideo)
  - Mute/unmute remote audio [trtc.muteRemoteAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#muteRemoteAudio)

### TRTC Static Methods

| Name | Description |
| --- | --- |
| [create](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.create) | Create a TRTC object for implementing functions such as entering a room, previewing, pushing, and pulling streams. |
| [setLogLevel](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.setLogLevel) | Set the log output level It is recommended to set the DEBUG level during development and testing, which includes detailed prompt information. The default output level is INFO, which includes the log information of the main functions of the SDK. |
| [isSupported](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.isSupported) | Check if the TRTC Web SDK is supported by the current browser |
| [getCameraList](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.getCameraList) | Returns the list of camera devices Note |
| [getMicrophoneList](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.getMicrophoneList) | Returns the list of microphone devices Note |
| [getSpeakerList](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.getSpeakerList) | Returns the list of speaker devices For security reasons, the label and deviceId fields may be empty before the user authorizes access to the camera or microphone. Therefore, it is recommended to call this interface to obtain device details after the user authorizes access. |
| [setCurrentSpeaker](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#.setCurrentSpeaker) | Set the current speaker for audio playback |

### TRTC Methods

| Name | Description |
| --- | --- |
| [enterRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enterRoom) | Enter a video call room. |
| [exitRoom](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#exitRoom) | Exit the current audio and video call room. |
| [switchRole](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#switchRole) | Switches the user role, only effective in TRTC.TYPE.SCENE_LIVE interactive live streaming mode. |
| [destroy](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#destroy) | Destroy the TRTC instance |
| [startLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalAudio) | Start collecting audio from the local microphone and publish it to the current room. |
| [updateLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalAudio) | Update the configuration of the local microphone. |
| [stopLocalAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalAudio) | Stop collecting and publishing the local microphone. |
| [startLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) | Start collecting video from the local camera, play the camera's video on the specified HTMLElement tag, and publish the camera's video to the current room. |
| [updateLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalVideo) | Update the local camera configuration. |
| [stopLocalVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopLocalVideo) | Stop capturing, previewing, and publishing the local camera. |
| [startScreenShare](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startScreenShare) | Start screen sharing. |
| [updateScreenShare](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateScreenShare) | Update screen sharing configuration |
| [stopScreenShare](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopScreenShare) | Stop screen sharing. |
| [startRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startRemoteVideo) | Play remote video |
| [updateRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateRemoteVideo) | Update remote video playback configuration |
| [stopRemoteVideo](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopRemoteVideo) | Used to stop remote video playback. |
| [muteRemoteAudio](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#muteRemoteAudio) | Mute a remote user and stop pulling audio data from that user. Only effective for the current user, other users in the room can still hear the muted user's voice. |
| [setRemoteAudioVolume](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#setRemoteAudioVolume) | Used to control the playback volume of remote audio. |
| [enableAudioVolumeEvaluation](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#enableAudioVolumeEvaluation) | Enables or disables the volume callback. |
| [on](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#on) | Listen to the [TRTC events](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html) |
| [off](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#off) | Remove event listener |
| [getVideoSnapshot](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#getVideoSnapshot) | Get video snapshot |
| [getVideoTrack](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#getVideoTrack) | Get video track |
| [getAudioTrack](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#getAudioTrack) | Get audio track |
| [sendSEIMessage](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#sendSEIMessage) | Send SEI message |
| [sendCustomMessage](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#sendCustomMessage) | Send custom message |
| [startPlugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startPlugin) | Start plugin |
| [updatePlugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updatePlugin) | Update plugin |
| [stopPlugin](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#stopPlugin) | Stop plugin |

> **Note**For FAQs, see [Web](https://www.tencentcloud.com/document/product/647/37340).

## Error Code

TRTC SDK defines 8 types of error codes. TRTC will throws error in the APIs and [TRTC.EVENT.ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-EVENT.html#.ERROR) event and you can get the [RtcError](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/RtcError.html) object for handling error.

| Key | Code | Description |
| --- | --- | --- |
| [INVALID_PARAMETER](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.INVALID_PARAMETER) | 5000 | The parameters passed in when calling the interface do not meet the API requirements.  **Handling suggestion**: Please check whether the passed-in parameters comply with the API specifications, such as whether the parameter type is correct. |
| [INVALID_OPERATION](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.INVALID_OPERATION) | 5100 | The prerequisite requirements of the API are not met when calling the interface.  **Handling suggestion**: Please check whether the calling logic complies with the API prerequisite requirements according to the corresponding API document.  For example: Switching roles before entering the room successfully.The remote user and stream being played do not exist. |
| [ENV_NOT_SUPPORTED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.ENV_NOT_SUPPORTED) | 5200 | The current environment does not support this function, indicating that the current browser does not support calling the corresponding API.  **Handling suggestion**: Usually, TRTC.isSupported can be used to perceive which capabilities the current browser supports. If the browser does not support it, you need to guide the user to use a browser that supports this capability. Reference: [Detect Capabilities](https://www.tencentcloud.com/document/product/647/59656) |
| [DEVICE_ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.DEVICE_ERROR) | 5300 | Capturing media devices failed.  The following interfaces will throw this error code when an exception occurs: startLocalVideo, updateLocalVideo, startLocalAudio, updateLocalAudio, startScreenShare, updateScreenShare **Handling suggestion**: Guide the user to check whether the device has a camera and microphone, whether the system has authorized the browser, and whether the browser has authorized the page. It is recommended to increase the device detection process before entering the room to confirm whether the microphone and camera exist and can be captured normally before proceeding to the next call operation. Usually, this exception can be avoided after the device check.  Implementation reference: [Detect Capabilities](https://www.tencentcloud.com/document/product/647/59656) If you need to distinguish more detailed exception categories, you can process according to the [extraCode](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.DEVICE_ERROR) |
| [SERVER_ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.SERVER_ERROR) | 5400 | Got server error. Reasons: expired userSig, Tencent Cloud account arrears, TRTC service not enabled, etc.  **Handling suggestion**: Refer to the [extraCode](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.SERVER_ERROR). |
| [OPERATION_FAILED](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.OPERATION_FAILED) | 5500 | The exception that the SDK cannot solve after multiple retries under the condition of meeting the API call requirements, usually caused by browser or network problems.  The following interfaces will throw this error code when an exception occurs: enterRoom, startLocalVideo, startLocalAudio, startScreenShare, startRemoteVideo, switchRole  **Handling suggestions**:Confirm whether the domain name and port required for communication meet your network environment requirements, refer to [Handle Firewall Restriction](https://www.tencentcloud.com/document/product/647/59667).Other issues need to be handled by engineers. [Submit an issue in github](https://github.com/LiteAVSDK/TRTC_Web/issues). |
| [OPERATION_ABORT](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.OPERATION_ABORT) | 5998 | The error code thrown when the API execution is aborted.  When the API is called or repeatedly called without meeting the [API lifecycle](https://trtc.io/document/41664#33599d2d-ad9e-42e1-81af-907ab6acb5bb), the API will abort execution to avoid meaningless operations.  For example: Call enterRoom, startLocalVideo continuously, and call exitRoom without entering the room.  The following interfaces will throw this error code when an exception occurs: enterRoom, startLocalVideo, startLocalAudio, startScreenShare, startRemoteVideo, switchRole  **Handling suggestions**: Capture and identify this error code, then avoid unnecessary calls in business logic, or you can do nothing, because the SDK has done side-effect-free processing, you only need to identify and ignore this error code when catching it. |
| [UNKNOWN_ERROR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-ERROR_CODE.html#.OPERATION_ABORT) | 5999 | Unknown error. Handling suggestions: [Submit an issue in github](https://github.com/LiteAVSDK/TRTC_Web). |

## Contact Us

- [Submit an issue in github](https://github.com/LiteAVSDK/TRTC_Web).
- Contact us on [telegram](https://t.me/+EPk6TMZEZMM5OGY1).


---
*Source: [https://trtc.io/document/41664](https://trtc.io/document/41664)*
