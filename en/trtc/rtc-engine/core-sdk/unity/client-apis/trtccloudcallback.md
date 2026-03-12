# TRTCCloudCallback

Copyright (c) 2021 Tencent. All rights reserved.

Module:   ITRTCCloudCallback @ TXLiteAVSDK

Function: event callback APIs for TRTCâs video call feature

**TRTCCloudCallback**

## ITRTCCloudCallback

| FuncList | DESC |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/72271#6f511ead5c28ad64656c4f7079058ca1) | Error event callback. |
| [onWarning](https://www.tencentcloud.com/document/product/647/72271#bea748a1e3eae80c31dd55797e4bae8c) | Warning event callback. |
| [onEnterRoom](https://www.tencentcloud.com/document/product/647/72271#ecf6c19003040ecf66fdb70f6159e053) | Whether room entry is successful. |
| [onExitRoom](https://www.tencentcloud.com/document/product/647/72271#41f110aa6e3e428ef20c7a42438774ff) | Room exit. |
| [onSwitchRole](https://www.tencentcloud.com/document/product/647/72271#5211599910e3f28b6027ff709c4c6da2) | Role switching. |
| [onSwitchRoom](https://www.tencentcloud.com/document/product/647/72271#bf836794907c5657850bfcdd6ace0ff5) | Result of room switching. |
| [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/72271#225107b993ed84f6fab7f8950df71b81) | Result of requesting cross-room call. |
| [onDisconnectOtherRoom](https://www.tencentcloud.com/document/product/647/72271#93c0a71cb16ed504e8cf83788be0a9b8) | Result of ending cross-room call. |
| [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/72271#e9e7285ae781e911819119428962771c) | A user entered the room. |
| [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/72271#93b04345737c8d8674810f1f65af77f9) | A user exited the room. |
| [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/72271#59380ac1827201d40a1795e59f2f894a) | A remote user published/unpublished primary stream video. |
| [onUserSubStreamAvailable](https://www.tencentcloud.com/document/product/647/72271#54d7d082393b211026a3f97b2e34450f) | A remote user published/unpublished substream video. |
| [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/72271#6d7c1afbfcb241ccb76adf4fcd2a4999) | A remote user published/unpublished audio. |
| [onFirstVideoFrame](https://www.tencentcloud.com/document/product/647/72271#7506c0166d59556803da3620d8bed4fb) | The SDK started rendering the first video frame of the local or a remote user. |
| [onFirstAudioFrame](https://www.tencentcloud.com/document/product/647/72271#f76d09e8839f1e759ddb804ee66c0402) | The SDK started playing the first audio frame of a remote user. |
| [onSendFirstLocalVideoFrame](https://www.tencentcloud.com/document/product/647/72271#c25b70379aaa68a2e6f8ae46708c3123) | The first local video frame was published. |
| [onSendFirstLocalAudioFrame](https://www.tencentcloud.com/document/product/647/72271#93f1fb68946e876bc39e81fdce019267) | The first local audio frame was published. |
| [onNetworkQuality](https://www.tencentcloud.com/document/product/647/72271#7f1d64147b2c7be914e6f8b3d2251624) | Real-time network quality statistics. |
| [onStatistics](https://www.tencentcloud.com/document/product/647/72271#b883ac307d230c975302daf2d83f863a) | Real-time statistics on technical metrics. |
| [onSpeedTestResult](https://www.tencentcloud.com/document/product/647/72271#26c5998975d4345045a64db9077f9cdc) | Callback of network speed test. |
| [onConnectionLost](https://www.tencentcloud.com/document/product/647/72271#6dbf39e800623f5767ee3a8717b29fd6) | The SDK was disconnected from the cloud. |
| [onTryToReconnect](https://www.tencentcloud.com/document/product/647/72271#2f7d312ce48ce84c53e5722fe26143d5) | The SDK is reconnecting to the cloud. |
| [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/72271#5f280bc90c0c5b053b1c5a80406ab086) | The SDK is reconnected to the cloud. |
| [onCameraDidReady](https://www.tencentcloud.com/document/product/647/72271#90375668a82423df166c37219e0f9235) | The camera is ready. |
| [onMicDidReady](https://www.tencentcloud.com/document/product/647/72271#bbaef371de51d0d37e3e9bcef2875aa0) | The mic is ready. |
| [onAudioRouteChanged](https://www.tencentcloud.com/document/product/647/72271#3d6f8015b95d13935f1e2ddd540bf7b8) | The audio route changed (for mobile devices only). |
| [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/72271#12c009f500ddcfac4dc9bbf142bf68cb) | Volume feedback callback. |
| [onDeviceChange](https://www.tencentcloud.com/document/product/647/72271#987b4f925048ad8e8828cb73a3c53741) | The status of a local device changed (for desktop OS only). |
| [onAudioDeviceCaptureVolumeChanged](https://www.tencentcloud.com/document/product/647/72271#e837f097b798e89c60334741f5c514dd) | The capturing volume of the mic changed. |
| [onAudioDevicePlayoutVolumeChanged](https://www.tencentcloud.com/document/product/647/72271#2cf9e1d8086384944ecb0f770479e5ed) | The playback volume changed. |
| [onTestMicVolume](https://www.tencentcloud.com/document/product/647/72271#b855284cfd07eba7f932c5154e8fc7b1) | Volume during mic test. |
| [onTestSpeakerVolume](https://www.tencentcloud.com/document/product/647/72271#bae0f0de188afbda074f833529d18c97) | Volume during speaker test. |
| [onRecvCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72271#abee69b3e1b20e82428c88cf5368724f) | Receipt of custom message. |
| [onMissCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72271#edc697fcde48b5c1aa120eb403909bad) | Loss of custom message. |
| [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/72271#10bd0c1f0010a55c27922dadd2723042) | Receipt of SEI message. |
| [onStartPublishing](https://www.tencentcloud.com/document/product/647/72271#1432443068529ef616c6d77881f8b5a7) | Started publishing to Tencent Cloud CSS CDN. |
| [onStopPublishing](https://www.tencentcloud.com/document/product/647/72271#0a735fd800e315ad0ee2fcce68eb8372) | Stopped publishing to Tencent Cloud CSS CDN. |
| [onSetMixTranscodingConfig](https://www.tencentcloud.com/document/product/647/72271#fe47548d376e9ee6fffb53e46e6c06b1) | Set the layout and transcoding parameters for On-Cloud MixTranscoding. |
| [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/72271#8c314542e34620ecf64a2310577b34ba) | Callback for starting to publish. |
| [onUpdatePublishMediaStream](https://www.tencentcloud.com/document/product/647/72271#bcf82ef6d725006ac3a7809b2785ca33) | Callback for modifying publishing parameters. |
| [onStopPublishMediaStream](https://www.tencentcloud.com/document/product/647/72271#03f8b47cb4a7b44add30592f67135993) | Callback for stopping publishing. |
| [onCdnStreamStateChanged](https://www.tencentcloud.com/document/product/647/72271#ea85c7c8efb4d60bd23d2105e941b4bd) | Callback for change of RTMP/RTMPS publishing status. |
| [onScreenCaptureStarted](https://www.tencentcloud.com/document/product/647/72271#b26b8c809b65cfa9d8be14e24df9a422) | Screen sharing started. |
| [onScreenCapturePaused](https://www.tencentcloud.com/document/product/647/72271#ddf5029605bbf37aafba5d7984662a29) | Screen sharing was paused. |
| [onScreenCaptureResumed](https://www.tencentcloud.com/document/product/647/72271#fed28e1166fc1e43445d061fbec59c94) | Screen sharing was resumed. |
| [onScreenCaptureStoped](https://www.tencentcloud.com/document/product/647/72271#08b6d8555bcf5148eb5828bf1fdfd0c2) | Screen sharing stopped. |

## ITRTCVideoRenderCallback

| FuncList | DESC |
| --- | --- |
| [onRenderVideoFrame](https://www.tencentcloud.com/document/product/647/72271#94d1af7ce1227213593378ddf2cdae5f) | Custom video rendering. |

## ITRTCVideoFrameCallback

| FuncList | DESC |
| --- | --- |
| [onGLContextCreated](https://www.tencentcloud.com/document/product/647/72271#e9cdbfe822913f9cef0f8356858a9505) | An OpenGL context was created in the SDK. |
| [onProcessVideoFrame](https://www.tencentcloud.com/document/product/647/72271#ba7227b30a2ffaffd691b55adaba408f) | Video processing by third-party beauty filters. |
| [onGLContextDestroy](https://www.tencentcloud.com/document/product/647/72271#080e6f959852e803bbb0fa5589be6b21) | The OpenGL context in the SDK was destroyed. |

## ITRTCAudioFrameCallback

| FuncList | DESC |
| --- | --- |
| [onCapturedRawAudioFrame](https://www.tencentcloud.com/document/product/647/72271#ecddf94eedf355f42d922b134dfbc5e2) | Audio data captured by the local mic and pre-processed by the audio module. |
| [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/72271#7013577cbc775c66b7d94a1299b86a64) | Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed. |
| [onPlayAudioFrame](https://www.tencentcloud.com/document/product/647/72271#e5b854ddfd36ca3dec95c5ec30a381e2) | Audio data of each remote user before audio mixing. |
| [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/72271#9e10a31ea56497b681f9c8fa7b36c52b) | Data mixed from each channel before being submitted to the system for playback. |

## ITRTCLogCallback

| FuncList | DESC |
| --- | --- |
| [onLog](https://www.tencentcloud.com/document/product/647/72271#f816c715e1faded8b0c1e71eb3f5faff) | Printing of local log. |

## onError

**onError**

| void onError | (TXLiteAVError errCode |
| --- | --- |
|  | String errMsg |
|  | IntPtr arg) |

#### Error event callback.

Error event, which indicates that the SDK threw an irrecoverable error such as room entry failure or failure to start device

For more information, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| errCode | Error code |
| errMsg | Error message |
| extInfo | Extended field. Certain error codes may carry extra information for troubleshooting. |

## onWarning

**onWarning**

| void onWarning | (TXLiteAVWarning warningCode |
| --- | --- |
|  | String warningMsg |
|  | IntPtr arg) |

#### Warning event callback.

Warning event, which indicates that the SDK threw an error requiring attention, such as video lag or high CPU usage

For more information, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| extInfo | Extended field. Certain warning codes may carry extra information for troubleshooting. |
| warningCode | Warning code |
| warningMsg | Warning message |

## onEnterRoom

**onEnterRoom**

| void onEnterRoom | (int result) |
| --- | --- |

#### Whether room entry is successful.

After calling the [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b) API in ` TRTCCloud ` to enter a room, you will receive the ` onEnterRoom(result) ` callback from ` TRTCCloudDelegate `.

- If room entry succeeded, ` result ` will be a positive number (` result ` > 0), indicating the time in milliseconds (ms) the room entry takes.
- If room entry failed, ` result ` will be a negative number (result < 0), indicating the error code for the failure.

For more information on the error codes for room entry failure, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| result | If ` result ` is greater than 0, it indicates the time (in ms) the room entry takes; if ` result ` is less than 0, it represents the error code for room entry. |

> **Note**1. In TRTC versions below 6.6, the ` onEnterRoom(result) ` callback is returned only if room entry succeeds, and the [onError](https://www.tencentcloud.com/document/product/647/72271#6f511ead5c28ad64656c4f7079058ca1) callback is returned if room entry fails.2. In TRTC 6.6 and above, the ` onEnterRoom(result) ` callback is returned regardless of whether room entry succeeds or fails, and the [onError](https://www.tencentcloud.com/document/product/647/72271#6f511ead5c28ad64656c4f7079058ca1) callback is also returned if room entry fails.

## onExitRoom

**onExitRoom**

| void onExitRoom | (int reason) |
| --- | --- |

#### Room exit.

Calling the [exitRoom](https://www.tencentcloud.com/document/product/647/72270#8e2de8da4b60ce0e19d385897ed77888) API in ` TRTCCloud ` will trigger the execution of room exit-related logic, such as releasing resources of audio/video devices and codecs.

After all resources occupied by the SDK are released, the SDK will return the ` onExitRoom() ` callback.

If you need to call [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b) again or switch to another audio/video SDK, please wait until you receive the ` onExitRoom() ` callback.

Otherwise, you may encounter problems such as the camera or mic being occupied.

| Param | DESC |
| --- | --- |
| reason | Reason for room exit. ` 0 `: the user called ` exitRoom ` to exit the room; ` 1 `: the user was removed from the room by the server; ` 2 `: the room was dismissed; ` 3 `: the server status was abnormal. |

## onSwitchRole

**onSwitchRole**

| void onSwitchRole | (TXLiteAVError errCode |
| --- | --- |
|  | String errMsg) |

#### Role switching.

You can call the [switchRole](https://www.tencentcloud.com/document/product/647/72270#a2f85cd8f74124a8d0ec0c8b34d94b01) API in ` TRTCCloud ` to switch between the anchor and audience roles. This is accompanied by a line switching process.

After the switching, the SDK will return the ` onSwitchRole() ` event callback.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates a successful switch. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onSwitchRoom

**onSwitchRoom**

| void onSwitchRoom | (TXLiteAVError errCode |
| --- | --- |
|  | string errMsg) |

#### Result of room switching.

You can call the [switchRoom](https://www.tencentcloud.com/document/product/647/72270#9f8d51bf4f02a354b060068482db62e8) API in ` TRTCCloud ` to switch from one room to another.

After the switching, the SDK will return the ` onSwitchRoom() ` event callback.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates a successful switch. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35124). |
| errMsg | Error message |

## onConnectOtherRoom

**onConnectOtherRoom**

| void onConnectOtherRoom | (string userId |
| --- | --- |
|  | TXLiteAVError errCode |
|  | string errMsg) |

#### Result of requesting cross-room call.

You can call the [connectOtherRoom](https://www.tencentcloud.com/document/product/647/72271#93c0a71cb16ed504e8cf83788be0a9b8) API in ` TRTCCloud ` to establish a video call with the anchor of another room. This is the âanchor competitionâ feature.

The caller will receive the ` onConnectOtherRoom() ` callback, which can be used to determine whether the cross-room call is successful.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that cross-room connection is established successfully. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |
| userId | The user ID of the anchor (in another room) to be called |

## onDisconnectOtherRoom

**onDisconnectOtherRoom**

| void onDisconnectOtherRoom | (TXLiteAVError errCode |
| --- | --- |
|  | string errMsg) |

#### Result of ending cross-room call.

You can call the disConnectOtherRoom API in ` TRTCCloud ` to end a video call with the anchor of another room. This is the âanchor competitionâ feature.

The caller will receive the ` onDisconnectOtherRoom() ` callback to determine whether the cross-room call has been successfully disconnected.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that the cross-room call has been successfully disconnected. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onRemoteUserEnterRoom

**onRemoteUserEnterRoom**

| void onRemoteUserEnterRoom | (String userId) |
| --- | --- |

#### A user entered the room.

Due to performance concerns, this callback works differently in different scenarios (i.e., ` AppScene `, which you can specify by setting the second parameter when calling [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b)).

- Live streaming scenarios ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1)): in live streaming scenarios, a user is either in the role of an anchor or audience. The callback is returned only when an anchor enters the room.
- Call scenarios ([TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1)): in call scenarios, the concept of roles does not apply (all users can be considered as anchors), and the callback is returned when any user enters the room.

| Param | DESC |
| --- | --- |
| userId | User ID of the remote user |

> **Note**1. The ` onRemoteUserEnterRoom ` callback indicates that a user entered the room, but it does not necessarily mean that the user enabled audio or video.2. If you want to know whether a user enabled video, we recommend you use the [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/72271#59380ac1827201d40a1795e59f2f894a) callback.

## onRemoteUserLeaveRoom

**onRemoteUserLeaveRoom**

| void onRemoteUserLeaveRoom | (String userId |
| --- | --- |
|  | int reason) |

#### A user exited the room.

As with [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/72271#e9e7285ae781e911819119428962771c), this callback works differently in different scenarios (i.e., ` AppScene `, which you can specify by setting the second parameter when calling [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b)).

- Live streaming scenarios ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1)): the callback is triggered only when an anchor exits the room.
- Call scenarios ([TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1)): in call scenarios, the concept of roles does not apply, and the callback is returned when any user exits the room.

| Param | DESC |
| --- | --- |
| reason | Reason for room exit. ` 0 `: the user exited the room voluntarily; ` 1 `: the user exited the room due to timeout; ` 2 `: the user was removed from the room; ` 3 `: the anchor user exited the room due to switch to audience. |
| userId | User ID of the remote user |

## onUserVideoAvailable

**onUserVideoAvailable**

| void onUserVideoAvailable | (String userId |
| --- | --- |
|  | bool available) |

#### A remote user published/unpublished primary stream video.

The primary stream is usually used for camera images. If you receive the ` onUserVideoAvailable(userId, true) ` callback, it indicates that the user has available primary stream video.

You can then call [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) to subscribe to the remote userâs video. If the subscription is successful, you will receive the ` onFirstVideoFrame(userid) ` callback, which indicates that the first video frame of the user is rendered.

If you receive the ` onUserVideoAvailable(userId, false) ` callback, it indicates that the video of the remote user is disabled, which may be because the user called [muteLocalVideo](https://www.tencentcloud.com/document/product/647/72270#b56b309b0223256eac598cb305d37270) or [stopLocalPreview](https://www.tencentcloud.com/document/product/647/72270#e379630cda7e794574b00d549b64a815).

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) primary stream video. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

## onUserSubStreamAvailable

**onUserSubStreamAvailable**

| void onUserSubStreamAvailable | (String userId |
| --- | --- |
|  | bool available) |

#### A remote user published/unpublished substream video.

The substream is usually used for screen sharing images. If you receive the ` onUserSubStreamAvailable(userId, true) ` callback, it indicates that the user has available substream video.

You can then call [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) to subscribe to the remote userâs video. If the subscription is successful, you will receive the ` onFirstVideoFrame(userid) ` callback, which indicates that the first frame of the user is rendered.

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) substream video. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

> **Note**The API used to display substream images is [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7), not startRemoteSubStreamView, startRemoteSubStreamView is deprecated.

## onUserAudioAvailable

**onUserAudioAvailable**

| void onUserAudioAvailable | (String userId |
| --- | --- |
|  | bool available) |

#### A remote user published/unpublished audio.

If you receive the ` onUserAudioAvailable(userId, true) ` callback, it indicates that the user published audio.

- In auto-subscription mode, the SDK will play the userâs audio automatically.
- In manual subscription mode, you can call [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/72270#b9f7792974d2df2e3922f2ed1e06ea39)(userid, false) to play the userâs audio.

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) audio. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

> **Note**The auto-subscription mode is used by default. You can switch to the manual subscription mode by calling [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/72270#f796890d9df3075ba7ce0cfa3b8a77a3), but it must be called before room entry for the switch to take effect.

## onFirstVideoFrame

**onFirstVideoFrame**

| void onFirstVideoFrame | (String userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
|  | int width |
|  | int height) |

#### The SDK started rendering the first video frame of the local or a remote user.

The SDK returns this event callback when it starts rendering your first video frame or that of a remote user. The ` userId ` in the callback can help you determine whether the frame is yours or a remote userâs.

- If ` userId ` is empty, it indicates that the SDK has started rendering your first video frame. The precondition is that you have called [startLocalPreview](https://www.tencentcloud.com/document/product/647/72270#38628a2c12121285b0ab3c24eba211dc) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/72270#62ca4f19707f9c5046ee470b2034ec5d).
- If ` userId ` is not empty, it indicates that the SDK has started rendering the first video frame of a remote user. The precondition is that you have called [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) to subscribe to the userâs video.

| Param | DESC |
| --- | --- |
| height | Video height |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | The user ID of the local or a remote user. If it is empty, it indicates that the first local video frame is available; if it is not empty, it indicates that the first video frame of a remote user is available. |
| width | Video width |

> **Note**1. The callback of the first local video frame being rendered is triggered only after you call [startLocalPreview](https://www.tencentcloud.com/document/product/647/72270#38628a2c12121285b0ab3c24eba211dc) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/72270#62ca4f19707f9c5046ee470b2034ec5d).2. The callback of the first video frame of a remote user being rendered is triggered only after you call [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) or startRemoteSubStreamView.

## onFirstAudioFrame

**onFirstAudioFrame**

| void onFirstAudioFrame | (String userId) |
| --- | --- |

#### The SDK started playing the first audio frame of a remote user.

The SDK returns this callback when it plays the first audio frame of a remote user. The callback is not returned for the playing of the first audio frame of the local user.

| Param | DESC |
| --- | --- |
| userId | User ID of the remote user |

## onSendFirstLocalVideoFrame

**onSendFirstLocalVideoFrame**

| void onSendFirstLocalVideoFrame | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType) |
| --- | --- |

#### The first local video frame was published.

After you enter a room and call [startLocalPreview](https://www.tencentcloud.com/document/product/647/72270#38628a2c12121285b0ab3c24eba211dc) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/72270#62ca4f19707f9c5046ee470b2034ec5d) to enable local video capturing (whichever happens first),

the SDK will start video encoding and publish the local video data via its network module to the cloud.

It returns the ` onSendFirstLocalVideoFrame ` callback after publishing the first local video frame.

| Param | DESC |
| --- | --- |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |

## onSendFirstLocalAudioFrame

**onSendFirstLocalAudioFrame**

#### The first local audio frame was published.

After you enter a room and call [startLocalAudio](https://www.tencentcloud.com/document/product/647/72270#126e2ce82ad449e5aafe277315896806) to enable audio capturing (whichever happens first),

the SDK will start audio encoding and publish the local audio data via its network module to the cloud.

The SDK returns the ` onSendFirstLocalAudioFrame ` callback after sending the first local audio frame.

## onNetworkQuality

**onNetworkQuality**

| void onNetworkQuality | ([TRTCQualityInfo](https://www.tencentcloud.com/document/product/647/72275#008511ed00730a2ef603fd62f64ca33c) localQuality |
| --- | --- |
|  | [TRTCQualityInfo](https://www.tencentcloud.com/document/product/647/72275#008511ed00730a2ef603fd62f64ca33c)[] remoteQuality |
|  | UInt32 remoteQualityCount) |

#### Real-time network quality statistics.

This callback is returned every 2 seconds and notifies you of the upstream and downstream network quality detected by the SDK.

The SDK uses a built-in proprietary algorithm to assess the current latency, bandwidth, and stability of the network and returns a result.

If the result is ` 1 ` (excellent), it means that the current network conditions are excellent; if it is ` 6 ` (down), it means that the current network conditions are too bad to support TRTC calls.

| Param | DESC |
| --- | --- |
| localQuality | Upstream network quality |
| remoteQuality | Downstream network quality, it refers to the data quality finally measured on the local side after the data flow passes through a complete transmission link of "remote ->cloud ->local". Therefore, the downlink network quality here represents the joint impact of the remote uplink and the local downlink. |

> **Note**The uplink quality of remote users cannot be determined independently through this interface.

## onStatistics

**onStatistics**

| void onStatistics | ([TRTCStatistics](https://www.tencentcloud.com/document/product/647/72272#dc3354e15492d5bac4a773a6e230c9eb) statis) |
| --- | --- |

#### Real-time statistics on technical metrics.

This callback is returned every 2 seconds and notifies you of the statistics on technical metrics related to video, audio, and network. The metrics are listed in [TRTCStatistics](https://www.tencentcloud.com/document/product/647/72272#dc3354e15492d5bac4a773a6e230c9eb):

- Video statistics: video resolution (` resolution `), frame rate (` FPS `), bitrate (` bitrate `), etc.
- Audio statistics: audio sample rate (` samplerate `), number of audio channels (` channel `), bitrate (` bitrate `), etc.
- Network statistics: the round trip time (` rtt `) between the SDK and the cloud (SDK -> Cloud -> SDK), package loss rate (` loss `), upstream traffic (` sentBytes `), downstream traffic (` receivedBytes `), etc.

| Param | DESC |
| --- | --- |
| statistics | Statistics, including local statistics and the statistics of remote users. For details, please see [TRTCStatistics](https://www.tencentcloud.com/document/product/647/72272#dc3354e15492d5bac4a773a6e230c9eb). |

> **Note**If you want to learn about only the current network quality and do not want to spend much time analyzing the statistics returned by this callback, we recommend you use [onNetworkQuality](https://www.tencentcloud.com/document/product/647/72271#7f1d64147b2c7be914e6f8b3d2251624).

## onSpeedTestResult

**onSpeedTestResult**

| void onSpeedTestResult | ([TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/72275#25124dd8b486afcaeaabe326bfe10288) result) |
| --- | --- |

#### Callback of network speed test.

The callback is triggered by [startSpeedTest](https://www.tencentcloud.com/document/product/647/72270#ecb445c9cc990d87be9fd5b11877af87).

| Param | DESC |
| --- | --- |
| result | Speed test data, including loss rates, rtt and bandwidth rates, please refer to [TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/72275#25124dd8b486afcaeaabe326bfe10288) for details. |

## onConnectionLost

**onConnectionLost**

#### The SDK was disconnected from the cloud.

The SDK returns this callback when it is disconnected from the cloud, which may be caused by network unavailability or change of network, for example, when the user walks into an elevator.

After returning this callback, the SDK will attempt to reconnect to the cloud, and will return the [onTryToReconnect](https://www.tencentcloud.com/document/product/647/72271#2f7d312ce48ce84c53e5722fe26143d5) callback. When it is reconnected, it will return the [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/72271#5f280bc90c0c5b053b1c5a80406ab086) callback.

In other words, the SDK proceeds from one event to the next in the following order:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d7032d3666f011f0b5365254001c06ec.png)

## onTryToReconnect

**onTryToReconnect**

#### The SDK is reconnecting to the cloud.

When the SDK is disconnected from the cloud, it returns the [onConnectionLost](https://www.tencentcloud.com/document/product/647/72271#6dbf39e800623f5767ee3a8717b29fd6) callback. It then attempts to reconnect and returns this callback ([onTryToReconnect](https://www.tencentcloud.com/document/product/647/72271#2f7d312ce48ce84c53e5722fe26143d5)). After it is reconnected, it returns the [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/72271#5f280bc90c0c5b053b1c5a80406ab086) callback.

## onConnectionRecovery

**onConnectionRecovery**

#### The SDK is reconnected to the cloud.

When the SDK is disconnected from the cloud, it returns the [onConnectionLost](https://www.tencentcloud.com/document/product/647/72271#6dbf39e800623f5767ee3a8717b29fd6) callback. It then attempts to reconnect and returns the [onTryToReconnect](https://www.tencentcloud.com/document/product/647/72271#2f7d312ce48ce84c53e5722fe26143d5) callback. After it is reconnected, it returns this callback ([onConnectionRecovery](https://www.tencentcloud.com/document/product/647/72271#5f280bc90c0c5b053b1c5a80406ab086)).

## onCameraDidReady

**onCameraDidReady**

#### The camera is ready.

After you call [startLocalPreview](https://www.tencentcloud.com/document/product/647/72270#38628a2c12121285b0ab3c24eba211dc), the SDK will try to start the camera and return this callback if the camera is started.

If it fails to start the camera, itâs probably because the application does not have access to the camera or the camera is being used.

You can capture the [onError](https://www.tencentcloud.com/document/product/647/72271#6f511ead5c28ad64656c4f7079058ca1) callback to learn about the exception and let users know via UI messages.

## onMicDidReady

**onMicDidReady**

#### The mic is ready.

After you call [startLocalAudio](https://www.tencentcloud.com/document/product/647/72270#126e2ce82ad449e5aafe277315896806), the SDK will try to start the mic and return this callback if the mic is started.

If it fails to start the mic, itâs probably because the application does not have access to the mic or the mic is being used.

You can capture the [onError](https://www.tencentcloud.com/document/product/647/72271#6f511ead5c28ad64656c4f7079058ca1) callback to learn about the exception and let users know via UI messages.

## onAudioRouteChanged

**onAudioRouteChanged**

| void onAudioRouteChanged | ([TRTCAudioRoute](https://www.tencentcloud.com/document/product/647/72275#aaca0d57f6f9d9c6a6425485464b0877) newRoute |
| --- | --- |
|  | [TRTCAudioRoute](https://www.tencentcloud.com/document/product/647/72275#aaca0d57f6f9d9c6a6425485464b0877) oldRoute) |

#### The audio route changed (for mobile devices only).

Audio route is the route (speaker or receiver) through which audio is played.

- When audio is played through the receiver, the volume is relatively low, and the sound can be heard only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.
- When audio is played through the speaker, the volume is relatively high, and there is no need to put the phone near the ear. This mode enables the "hands-free" feature.
- When audio is played through the wired earphone.
- When audio is played through the bluetooth earphone.
- When audio is played through the USB sound card.

| Param | DESC |
| --- | --- |
| fromRoute | The audio route used before the change |
| route | Audio route, i.e., the route (speaker or receiver) through which audio is played |

## onUserVoiceVolume

**onUserVoiceVolume**

| void onUserVoiceVolume | ([TRTCVolumeInfo](https://www.tencentcloud.com/document/product/647/72275#6895db8871ff30fc996e931a213e2b0c)[] userVolumes |
| --- | --- |
|  | UInt32 userVolumesCount |
|  | UInt32 totalVolume) |

#### Volume.

The SDK can assess the volume of each channel and return this callback on a regular basis. You can display, for example, a waveform or volume bar on the UI based on the statistics returned.

You need to first call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/72270#e47cf2e48182962b7afde88a8f31fbbd) to enable the feature and set the interval for the callback.

Note that the SDK returns this callback at the specified interval regardless of whether someone is speaking in the room.

| Param | DESC |
| --- | --- |
| totalVolume | The total volume of all remote users. Value range: [0, 100] |
| userVolumes | An array that represents the volume of all users who are speaking in the room. Value range: [0, 100] |

> **Note**` userVolumes ` is an array. If ` userId ` is empty, the elements in the array represent the volume of the local userâs audio. Otherwise, they represent the volume of a remote userâs audio.

## onDeviceChange

**onDeviceChange**

| void onDeviceChange | (String deviceId |
| --- | --- |
|  | TRTCDeviceType type |
|  | TRTCDeviceState state) |

#### The status of a local device changed (for desktop OS only).

The SDK returns this callback when a local device (camera, mic, or speaker) is connected or disconnected.

| Param | DESC |
| --- | --- |
| deviceId | Device ID |
| deviceType | Device type. ` 0 `: microphone; ` 1 `: speak; ` 2 `: camera |
| state | Device status. ` 0 `: connected; ` 1 `: disconnected; ` 2 `: started |

## onAudioDeviceCaptureVolumeChanged

**onAudioDeviceCaptureVolumeChanged**

| void onAudioDeviceCaptureVolumeChanged | (int volume |
| --- | --- |
|  | bool muted) |

#### The capturing volume of the mic changed.

On desktop OS such as macOS and Windows, users can set the capturing volume of the mic in the audio control panel.

The higher volume a user sets, the higher the volume of raw audio captured by the mic.

On some keyboards and laptops, users can also mute the mic by pressing a key (whose icon is a crossed out mic).

When users set the mic capturing volume via the UI or a keyboard shortcut, the SDK will return this callback.

| Param | DESC |
| --- | --- |
| muted | Whether the mic is muted. ` true `: muted; ` false `: unmuted |
| volume | System audio capturing volume, which users can set in the audio control panel. Value range: [0, 100] |

> **Note**You need to call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/72270#e47cf2e48182962b7afde88a8f31fbbd) and set the callback interval (` interval ` > 0) to enable the callback. To disable the callback, set ` interval ` to ` 0 `.

## onAudioDevicePlayoutVolumeChanged

**onAudioDevicePlayoutVolumeChanged**

| void onAudioDevicePlayoutVolumeChanged | (int volume |
| --- | --- |
|  | bool muted) |

#### The playback volume changed.

On desktop OS such as macOS and Windows, users can set the systemâs playback volume in the audio control panel.

On some keyboards and laptops, users can also mute the speaker by pressing a key (whose icon is a crossed out speaker).

When users set the systemâs playback volume via the UI or a keyboard shortcut, the SDK will return this callback.

| Param | DESC |
| --- | --- |
| muted | Whether the speaker is muted. ` true `: muted; ` false `: unmuted |
| volume | The system playback volume, which users can set in the audio control panel. Value range: 0-100 |

> **Note**You need to call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/72270#e47cf2e48182962b7afde88a8f31fbbd) and set the callback interval (` interval ` > 0) to enable the callback. To disable the callback, set ` interval ` to ` 0 `.

## onTestMicVolume

**onTestMicVolume**

| void onTestMicVolume | (int volume) |
| --- | --- |

#### Volume during mic test.

When you call startMicDeviceTest to test the mic, the SDK will keep returning this callback. The ` volume ` parameter represents the volume of the audio captured by the mic.

If the value of the ` volume ` parameter fluctuates, the mic works properly. If it is ` 0 ` throughout the test, it indicates that there is a problem with the mic, and users should be prompted to switch to a different mic.

| Param | DESC |
| --- | --- |
| volume | Captured mic volume. Value range: [0, 100] |

## onTestSpeakerVolume

**onTestSpeakerVolume**

| void onTestSpeakerVolume | (int volume) |
| --- | --- |

#### Volume during speaker test.

When you call startSpeakerDeviceTest to test the speaker, the SDK will keep returning this callback.

The ` volume ` parameter in the callback represents the volume of audio sent by the SDK to the speaker for playback. If its value fluctuates but users cannot hear any sound, the speaker is not working properly.

| Param | DESC |
| --- | --- |
| volume | The volume of audio sent by the SDK to the speaker for playback. Value range: [0, 100] |

## onRecvCustomCmdMsg

**onRecvCustomCmdMsg**

| void onRecvCustomCmdMsg | (String userId |
| --- | --- |
|  | int cmdID |
|  | int seq |
|  | byte[] message |
|  | int messageSize) |

#### Receipt of custom message.

When a user in a room uses [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72270#20d4d41de96d8e2e6d2cf6499ea55171) to send a custom message, other users in the room can receive the message through the ` onRecvCustomCmdMsg ` callback.

| Param | DESC |
| --- | --- |
| cmdID | Command ID |
| message | Message data |
| seq | Message serial number |
| userId | User ID |

## onMissCustomCmdMsg

**onMissCustomCmdMsg**

| void onMissCustomCmdMsg | (String userId |
| --- | --- |
|  | int cmdID |
|  | int errCode |
|  | int missed) |

#### Loss of custom message.

When you use [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72270#20d4d41de96d8e2e6d2cf6499ea55171) to send a custom UDP message, even if you enable reliable transfer (by setting ` reliable ` to ` true `), there is still a chance of message loss. Reliable transfer only helps maintain a low probability of message loss, which meets the reliability requirements in most cases.

If the sender sets ` reliable ` to ` true `, the SDK will use this callback to notify the recipient of the number of custom messages lost during a specified time period (usually 5s) in the past.

| Param | DESC |
| --- | --- |
| cmdID | Command ID |
| errCode | Error code |
| missed | Number of lost messages |
| userId | User ID |

> **Note**The recipient receives this callback only if the sender sets ` reliable ` to ` true `.

## onRecvSEIMsg

**onRecvSEIMsg**

| void onRecvSEIMsg | (String userId |
| --- | --- |
|  | Byte[] message |
|  | UInt32 msgSize) |

#### Receipt of SEI message.

If a user in the room uses [sendSEIMsg](https://www.tencentcloud.com/document/product/647/72270#2d918c3d0ef54d41bd5f5adcb62f63d6) to send an SEI message via video frames, other users in the room can receive the message through the ` onRecvSEIMsg ` callback.

| Param | DESC |
| --- | --- |
| message | Data |
| userId | User ID |

## onStartPublishing

**onStartPublishing**

| void onStartPublishing | (int errCode |
| --- | --- |
|  | String errMsg) |

#### Started publishing to Tencent Cloud CSS CDN.

When you call startPublishing to publish streams to Tencent Cloud CSS CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStopPublishing

**onStopPublishing**

| void onStopPublishing | (int errCode |
| --- | --- |
|  | String errMsg) |

#### Stopped publishing to Tencent Cloud CSS CDN.

When you call stopPublishing to stop publishing streams to Tencent Cloud CSS CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onSetMixTranscodingConfig

**onSetMixTranscodingConfig**

| void onSetMixTranscodingConfig | (int errCode |
| --- | --- |
|  | String errMsg) |

#### Set the layout and transcoding parameters for On-Cloud MixTranscoding.

When you call setMixTranscodingConfig to modify the layout and transcoding parameters for On-Cloud MixTranscoding, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStartPublishMediaStream

**onStartPublishMediaStream**

| void onStartPublishMediaStream | (string taskID |
| --- | --- |
|  | int code |
|  | string message |
|  | string extraInfo) |

#### Callback for starting to publish.

When you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4) to publish a stream to the TRTC backend, the SDK will immediately update the command to the cloud server.

The SDK will then receive the publishing result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues. |
| message | : The callback information. |
| taskId | : If a request is successful, a task ID will be returned via the callback. You need to provide this task ID when you call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#dad88b0322dc59b7e5dbf084b963782e) to modify publishing parameters or [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#5d9c082fb84a8784246a729663df1ac4) to stop publishing. |

## onUpdatePublishMediaStream

**onUpdatePublishMediaStream**

| void onUpdatePublishMediaStream | (string taskID |
| --- | --- |
|  | int code |
|  | string message |
|  | string extraInfo) |

#### Callback for modifying publishing parameters.

When you call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#dad88b0322dc59b7e5dbf084b963782e) to modify publishing parameters, the SDK will immediately update the command to the cloud server.

The SDK will then receive the modification result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues. |
| message | : The callback information. |
| taskId | : The task ID you pass in when calling [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#dad88b0322dc59b7e5dbf084b963782e), which is used to identify a request. |

## onStopPublishMediaStream

**onStopPublishMediaStream**

| void onStopPublishMediaStream | (string taskID |
| --- | --- |
|  | int code |
|  | string message |
|  | string extraInfo) |

#### Callback for stopping publishing.

When you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#5d9c082fb84a8784246a729663df1ac4) to stop publishing, the SDK will immediately update the command to the cloud server.

The SDK will then receive the modification result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues. |
| message | : The callback information. |
| taskId | : The task ID you pass in when calling [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#5d9c082fb84a8784246a729663df1ac4), which is used to identify a request. |

## onCdnStreamStateChanged

**onCdnStreamStateChanged**

| void onCdnStreamStateChanged | (string cdnURL |
| --- | --- |
|  | int status |
|  | int code |
|  | string message |
|  | string extraInfo) |

#### Callback for change of RTMP/RTMPS publishing status.

When you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4) to publish a stream to the TRTC backend, the SDK will immediately update the command to the cloud server.

If you set the publishing destination ([TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49)) to the URL of Tencent Cloud or a third-party CDN, you will be notified of the RTMP/RTMPS publishing status via this callback.

| Param | DESC |
| --- | --- |
| cdnUrl | : The URL you specify in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49) when you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4). |
| code | : The publishing result. ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues. |
| message | : The publishing information. |
| status | : The publishing status. 0: The publishing has not started yet or has ended. This value will be returned after you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#5d9c082fb84a8784246a729663df1ac4). 1: The TRTC server is connecting to the CDN server. If the first attempt fails, the TRTC backend will retry multiple times and will return this value via the callback (every five seconds). After publishing succeeds, the value ` 2 ` will be returned. If a server error occurs or publishing is still unsuccessful after 60 seconds, the value ` 4 ` will be returned. 2: The TRTC server is publishing to the CDN. This value will be returned if the publishing succeeds. 3: The TRTC server is disconnected from the CDN server and is reconnecting. If a CDN error occurs or publishing is interrupted, the TRTC backend will try to reconnect and resume publishing and will return this value via the callback (every five seconds). After publishing resumes, the value ` 2 ` will be returned. If a server error occurs or the attempt to resume publishing is still unsuccessful after 60 seconds, the value ` 4 ` will be returned. 4: The TRTC server is disconnected from the CDN server and failed to reconnect within the timeout period. In this case, the publishing is deemed to have failed. You can call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#dad88b0322dc59b7e5dbf084b963782e) to try again. 5: The TRTC server is disconnecting from the CDN server. After you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#5d9c082fb84a8784246a729663df1ac4), the SDK will return this value first and then the value ` 0 `. |

## onScreenCaptureStarted

**onScreenCaptureStarted**

#### Screen sharing started.

The SDK returns this callback when you call [startScreenCapture](https://www.tencentcloud.com/document/product/647/72270#62ca4f19707f9c5046ee470b2034ec5d) and other APIs to start screen sharing.

## onScreenCapturePaused

**onScreenCapturePaused**

| void onScreenCapturePaused | (int reason) |
| --- | --- |

#### Screen sharing was paused.

The SDK returns this callback when you call [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/72270#d7f9ad7b108c98e919f5f1cca757e72d) to pause screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user paused screen sharing. ` 1 `: screen sharing was paused because the shared window became invisible(Mac). screen sharing was paused because setting parameters(Windows). ` 2 `: screen sharing was paused because the shared window became minimum(only for Windows). ` 3 `: screen sharing was paused because the shared window became invisible(only for Windows). ` 4 `: screen sharing was paused because the system operation(only for iOS). |

## onScreenCaptureResumed

**onScreenCaptureResumed**

| void onScreenCaptureResumed | (int reason) |
| --- | --- |

#### Screen sharing was resumed.

The SDK returns this callback when you call [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/72270#1924263011bb92fba1642ad3e139629f) to resume screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user resumed screen sharing. ` 1 `: screen sharing was resumed automatically after the shared window became visible again(Mac). screen sharing was resumed automatically after setting parameters(Windows). ` 2 `: screen sharing was resumed automatically after the shared window became minimize recovery(only for Windows). ` 3 `: screen sharing was resumed automatically after the shared window became visible again(only for Windows). ` 4 `: screen sharing was resumed because the system operation(only for iOS). |

## onScreenCaptureStoped

**onScreenCaptureStoped**

| void onScreenCaptureStoped | (int reason) |
| --- | --- |

#### Screen sharing stopped.

The SDK returns this callback when you call [stopScreenCapture](https://www.tencentcloud.com/document/product/647/72270#2a667ba75e08183bd5f764374a6de7ba) to stop screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user stopped screen sharing; ` 1 `: screen sharing stopped because the shared window was closed. |

## onRenderVideoFrame

**onRenderVideoFrame**

| void onRenderVideoFrame | (string userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
|  | [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/72275#9233a1b1573333abc70e53b51bd89740) frame) |

#### Custom video rendering.

If you have configured the callback of custom rendering for local or remote video, the SDK will return to you via this callback video frames that are otherwise sent to the rendering control, so that you can customize rendering.

| Param | DESC |
| --- | --- |
| frame | Video frames to be rendered |
| streamType | Stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | ` userId ` of the video source. This parameter can be ignored if the callback is for local video (setLocalVideoRenderDelegate). |

## onGLContextCreated

**onGLContextCreated**

#### An OpenGL context was created in the SDK.

## onProcessVideoFrame

**onProcessVideoFrame**

| int onProcessVideoFrame | ([TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/72275#9233a1b1573333abc70e53b51bd89740) srcFrame |
| --- | --- |
|  | [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/72275#9233a1b1573333abc70e53b51bd89740) dstFrame) |

#### Video processing by third-party beauty filters.

If you use a third-party beauty filter component, you need to configure this callback in ` TRTCCloud ` to have the SDK return to you video frames that are otherwise pre-processed by TRTC.

You can then send the video frames to the third-party beauty filter component for processing. As the data returned can be read and modified, the result of processing can be synced to TRTC for subsequent encoding and publishing.

Case 1: the beauty filter component generates new textures

If the beauty filter component you use generates a frame of new texture (for the processed image) during image processing, please set ` dstFrame.textureId ` to the ID of the new texture in the callback function.

```
int onProcessVideoFrame(TRTCVideoFrame srcFrame, TRTCVideoFrame dstFrame);
```

Case 2: you need to provide target textures to the beauty filter component

If the third-party beauty filter component you use does not generate new textures and you need to manually set an input texture and an output texture for the component, you can consider the following scheme:

```
int onProcessVideoFrame(TRTCVideoFrame srcFrame, TRTCVideoFrame dstFrame);
```

| Param | DESC |
| --- | --- |
| dstFrame | Used to receive video images processed by third-party beauty filters |
| srcFrame | Used to carry images captured by TRTC via the camera |

> **Note**Currently, only the OpenGL texture scheme is supported(PC supports TRTCVideoBufferType_Buffer format Only)

## onGLContextDestroy

**onGLContextDestroy**

#### The OpenGL context in the SDK was destroyed.

## onCapturedRawAudioFrame

**onCapturedRawAudioFrame**

| void onCapturedRawAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/72275#ac73b0af225be99342eab0db97c8ee5b) frame) |
| --- | --- |

#### Audio data captured by the local mic and pre-processed by the audio module.

After you configure the callback of custom audio processing, the SDK will return via this callback the data captured and pre-processed (ANS, AEC, and AGC) in PCM format.

- The audio returned is in PCM format and has a fixed frame length (time) of 0.02s.
- The formula to convert a frame length in seconds to one in bytes is **sample rate * frame length in seconds * number of sound channels * audio bit depth**.
- Assume that the audio is recorded on a single channel with a sample rate of 48,000 Hz and audio bit depth of 16 bits, which are the default settings of TRTC. The frame length in bytes will be **48000 * 0.02s * 1 * 16 bits = 15360 bits = 1920 bytes**.

| Param | DESC |
| --- | --- |
| frame | Audio frames in PCM format |

> **Note**1. Please avoid time-consuming operations in this callback function. The SDK processes an audio frame every 20 ms, so if your operation takes more than 20 ms, it will cause audio exceptions.2. The audio data returned via this callback can be read and modified, but please keep the duration of your operation short.3. The audio data is returned via this callback after ANS, AEC and AGC, but it **does not include** pre-processing effects like background music, audio effects, or reverb, and therefore has a short delay.

## onLocalProcessedAudioFrame

**onLocalProcessedAudioFrame**

| void onLocalProcessedAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/72275#ac73b0af225be99342eab0db97c8ee5b) frame) |
| --- | --- |

#### Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed.

After you configure the callback of custom audio processing, the SDK will return via this callback the data captured, pre-processed (ANS, AEC, and AGC), effect-processed and BGM-mixed in PCM format, before it is submitted to the network module for encoding.

- The audio data returned via this callback is in PCM format and has a fixed frame length (time) of 0.02s.
- The formula to convert a frame length in seconds to one in bytes is **sample rate * frame length in seconds * number of sound channels * audio bit depth**.
- Assume that the audio is recorded on a single channel with a sample rate of 48,000 Hz and audio bit depth of 16 bits, which are the default settings of TRTC. The frame length in bytes will be **48000 * 0.02s * 1 * 16 bits = 15360 bits = 1920 bytes**.

Instructions:

You could write data to the ` TRTCAudioFrame.extraData ` filed, in order to achieve the purpose of transmitting signaling.

Because the data block of the audio frame header cannot be too large, we recommend you limit the size of the signaling data to only a few bytes when using this API. If extra data more than 100 bytes, it won't be sent.

Other users in the room can receive the message through the ` TRTCAudioFrame.extraData ` in ` onRemoteUserAudioFrame ` callback in TRTCAudioFrameDelegate.

| Param | DESC |
| --- | --- |
| frame | Audio frames in PCM format |

> **Note**1. Please avoid time-consuming operations in this callback function. The SDK processes an audio frame every 20 ms, so if your operation takes more than 20 ms, it will cause audio exceptions.2. The audio data returned via this callback can be read and modified, but please keep the duration of your operation short.3. Audio data is returned via this callback after ANS, AEC, AGC, effect-processing and BGM-mixing, and therefore the delay is longer than that with onCapturedAudioFrame.

## onPlayAudioFrame

**onPlayAudioFrame**

| void onPlayAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/72275#ac73b0af225be99342eab0db97c8ee5b) frame |
| --- | --- |
|  | string userId) |

#### Audio data of each remote user before audio mixing.

After you configure the callback of custom audio processing, the SDK will return via this callback the raw audio data (PCM format) of each remote user before mixing.

- The audio data returned via this callback is in PCM format and has a fixed frame length (time) of 0.02s.
- The formula to convert a frame length in seconds to one in bytes is **sample rate * frame length in seconds * number of sound channels * audio bit depth**.
- Assume that the audio is recorded on a single channel with a sample rate of 48,000 Hz and audio bit depth of 16 bits, which are the default settings of TRTC. The frame length in bytes will be **48000 * 0.02s * 1 * 16 bits = 15360 bits = 1920 bytes**.

| Param | DESC |
| --- | --- |
| frame | Audio frames in PCM format |
| userId | User ID |

> **Note**The audio data returned via this callback can be read but not modified.

## onMixedPlayAudioFrame

**onMixedPlayAudioFrame**

| void onMixedPlayAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/72275#ac73b0af225be99342eab0db97c8ee5b) frame) |
| --- | --- |

#### Data mixed from each channel before being submitted to the system for playback.

After you configure the callback of custom audio processing, the SDK will return to you via this callback the data (PCM format) mixed from each channel before it is submitted to the system for playback.

- The audio data returned via this callback is in PCM format and has a fixed frame length (time) of 0.02s.
- The formula to convert a frame length in seconds to one in bytes is **sample rate * frame length in seconds * number of sound channels * audio bit depth**.
- Assume that the audio is recorded on a single channel with a sample rate of 48,000 Hz and audio bit depth of 16 bits, which are the default settings of TRTC. The frame length in bytes will be **48000 * 0.02s * 1 * 16 bits = 15360 bits = 1920 bytes**.

| Param | DESC |
| --- | --- |
| frame | Audio frames in PCM format |

> **Note**1. Please avoid time-consuming operations in this callback function. The SDK processes an audio frame every 20 ms, so if your operation takes more than 20 ms, it will cause audio exceptions.2. The audio data returned via this callback can be read and modified, but please keep the duration of your operation short.3. The audio data returned via this callback is the audio data mixed from each channel before it is played. It does not include the in-ear monitoring data.

## onLog

**onLog**

| void onLog | (string log |
| --- | --- |
|  | [TRTCLogLevel](https://www.tencentcloud.com/document/product/647/72275#3b7ff44175cba4dd48e97aa8ac7b0b98) level |
|  | string module) |

#### Printing of local log.

If you want to capture the local log printing event, you can configure the log callback to have the SDK return to you via this callback all logs that are to be printed.

| Param | DESC |
| --- | --- |
| level | Log level. For more information, please see TRTC_LOG_LEVEL. |
| log | Log content |
| module | Reserved field, which is not defined at the moment and has a fixed value of ` TXLiteAVSDK `. |


---
*Source: [https://trtc.io/document/72271](https://trtc.io/document/72271)*
