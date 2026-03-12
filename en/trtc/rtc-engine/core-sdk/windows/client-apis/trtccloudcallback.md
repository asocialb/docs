# TRTCCloudCallback

Copyright (c) 2021 Tencent. All rights reserved.

Module:   ITRTCCloudCallback @ TXLiteAVSDK

Function: event callback APIs for TRTCâs video call feature

**TRTCCloudCallback**

## ITRTCCloudCallback

| FuncList | DESC |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/50771#3df71ff9905826c3d788593557c7f40b) | Error event callback. |
| [onWarning](https://www.tencentcloud.com/document/product/647/50771#972f298b26035f643d3512b8bbbe1ce6) | Warning event callback. |
| [onEnterRoom](https://www.tencentcloud.com/document/product/647/50771#6f9dcce089ddf638dac51f9789f44224) | Whether room entry is successful. |
| [onExitRoom](https://www.tencentcloud.com/document/product/647/50771#a80925fbd52d416a44f8c29f48d08c7a) | Room exit. |
| [onSwitchRole](https://www.tencentcloud.com/document/product/647/50771#bbf6926ae04d54d63c770cd13f03d828) | Role switching. |
| [onSwitchRoom](https://www.tencentcloud.com/document/product/647/50771#7d4de775235d838da1c216caddf074aa) | Result of room switching. |
| [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50771#69534513bb766ecb024b4b7e475d5ddd) | Result of requesting cross-room call. |
| [onDisconnectOtherRoom](https://www.tencentcloud.com/document/product/647/50771#2554839cf7be6599f136a98bb6b5625b) | Result of ending cross-room call. |
| [onUpdateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50771#943a6c15c33a5977cc718bba24af923b) | Result of changing the upstream capability of the cross-room anchor. |
| [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/50771#37486e9a6b528f6dde9ff3bed604226f) | A user entered the room. |
| [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/50771#8afca198f4d52b72c44846f3e15f3a06) | A user exited the room. |
| [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/50771#6d1cb6b1fcf292ac6f34cd8baa647937) | A remote user published/unpublished primary stream video. |
| [onUserSubStreamAvailable](https://www.tencentcloud.com/document/product/647/50771#28e89779f40ffc0ea9c44d6992c45458) | A remote user published/unpublished substream video. |
| [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50771#2efaaf0cd5c69f4857c4c40f6cec038f) | A remote user published/unpublished audio. |
| [onFirstVideoFrame](https://www.tencentcloud.com/document/product/647/50771#8da71f3fa431f74bbc902324abc2a5ff) | The SDK started rendering the first video frame of the local or a remote user. |
| [onFirstAudioFrame](https://www.tencentcloud.com/document/product/647/50771#02073fb0d33d281b9f7c55bb12f8bcb0) | The SDK started playing the first audio frame of a remote user. |
| [onSendFirstLocalVideoFrame](https://www.tencentcloud.com/document/product/647/50771#b74a98009771081a326c303ba6f613ab) | The first local video frame was published. |
| [onSendFirstLocalAudioFrame](https://www.tencentcloud.com/document/product/647/50771#3891c8671637c4237e872746bbb03233) | The first local audio frame was published. |
| [onRemoteVideoStatusUpdated](https://www.tencentcloud.com/document/product/647/50771#5bbff72b60e2594437034a4a0e66afc6) | Change of remote video status. |
| [onRemoteAudioStatusUpdated](https://www.tencentcloud.com/document/product/647/50771#a3fd06abb8c4921e7feebd1cbe4fa882) | Change of remote audio status. |
| [onUserVideoSizeChanged](https://www.tencentcloud.com/document/product/647/50771#e0b4fa102e736bfa6d59fe5ba4fedca8) | Change of remote video size. |
| [onNetworkQuality](https://www.tencentcloud.com/document/product/647/50771#7faad64d9fbb7d65876027eaa7d60b3d) | Real-time network quality statistics. |
| [onStatistics](https://www.tencentcloud.com/document/product/647/50771#3a8ca1601794ca5ab8aac596447684b8) | Real-time statistics on technical metrics. |
| [onSpeedTestResult](https://www.tencentcloud.com/document/product/647/50771#3f01ebf391cbb16fe1b9b9b3e983bb6c) | Callback of network speed test. |
| [onConnectionLost](https://www.tencentcloud.com/document/product/647/50771#6f1f6ac255f4027285ade6528d7fd80a) | The SDK was disconnected from the cloud. |
| [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50771#f4c4e0fc1d93660732758709d477efcc) | The SDK is reconnecting to the cloud. |
| [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50771#ddabb835fc7f8359827e33ba72514ec8) | The SDK is reconnected to the cloud. |
| [onCameraDidReady](https://www.tencentcloud.com/document/product/647/50771#3b6a1052f3ebc8180b5b3e20f868574f) | The camera is ready. |
| [onMicDidReady](https://www.tencentcloud.com/document/product/647/50771#de984d512b37c74620bbaa517ea637f8) | The mic is ready. |
| [onAudioRouteChanged](https://www.tencentcloud.com/document/product/647/50771#63c0bc774fcebca4b65b2f68d1ca2b3e) | The audio route changed (for mobile devices only). |
| [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/50771#454923f2ebbf576be5048238c2908e1f) | Volume. |
| [onDeviceChange](https://www.tencentcloud.com/document/product/647/50771#531042a7b093dbac07fa6d518c0e3334) | The status of a local device changed (for desktop OS only). |
| [onAudioDeviceCaptureVolumeChanged](https://www.tencentcloud.com/document/product/647/50771#bbcfc287c7dba77f6c5d4ccf58bbd561) | The capturing volume of the mic changed. |
| [onAudioDevicePlayoutVolumeChanged](https://www.tencentcloud.com/document/product/647/50771#b43f3492c6b78534a006ba3f38edf8a3) | The playback volume changed. |
| [onSystemAudioLoopbackError](https://www.tencentcloud.com/document/product/647/50771#866e125dcc16636c378bc5463ed3a99b) | Whether system audio capturing is enabled successfully (for desktop OS only). |
| [onTestMicVolume](https://www.tencentcloud.com/document/product/647/50771#c7ee87eb065b5832ef947095e1b936e1) | Volume during mic test. |
| [onTestSpeakerVolume](https://www.tencentcloud.com/document/product/647/50771#6305023aa76e326fe663fd26d8bc161f) | Volume during speaker test. |
| [onRecvCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50771#4cd82f4edb24992a15a25187089e1565) | Receipt of custom message. |
| [onMissCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50771#b86ff5635dd07db269779d9a3f751f8b) | Loss of custom message. |
| [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/50771#567707ef1f7ff43f79cfaf84e1bc2368) | Receipt of SEI message. |
| [onStartPublishing](https://www.tencentcloud.com/document/product/647/50771#80c4449085b648a0455de90f7a88640c) | Started publishing to Tencent Cloud CSS CDN. |
| [onStopPublishing](https://www.tencentcloud.com/document/product/647/50771#d314b918b62a270f1a1883ce9e71647f) | Stopped publishing to Tencent Cloud CSS CDN. |
| [onStartPublishCDNStream](https://www.tencentcloud.com/document/product/647/50771#4590b3a88275cb60c936b8fcd35c9c0d) | Started publishing to non-Tencent Cloudâs live streaming CDN. |
| [onStopPublishCDNStream](https://www.tencentcloud.com/document/product/647/50771#94cff50ac97c175da6aa02499d25edfc) | Stopped publishing to non-Tencent Cloudâs live streaming CDN. |
| [onSetMixTranscodingConfig](https://www.tencentcloud.com/document/product/647/50771#3dc61d7293745439dd34e0233f105047) | Set the layout and transcoding parameters for On-Cloud MixTranscoding. |
| [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#886b2dee59842d22542b673febbd5549) | Callback for starting to publish. |
| [onUpdatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#3a50d286d7cfe0c1f7f029e6d5b3206f) | Callback for modifying publishing parameters. |
| [onStopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#7a152f00d4f86489acb724138f2b8c66) | Callback for stopping publishing. |
| [onCdnStreamStateChanged](https://www.tencentcloud.com/document/product/647/50771#121f67d094d49a08d83ef0adda327578) | Callback for change of RTMP/RTMPS publishing status. |
| [onScreenCaptureStarted](https://www.tencentcloud.com/document/product/647/50771#fbf1f7083f4f4583a7d691a40ae55d9c) | Screen sharing started. |
| [onScreenCapturePaused](https://www.tencentcloud.com/document/product/647/50771#a8f341fb34c2a0969929f34ceb8b3a92) | Screen sharing was paused. |
| [onScreenCaptureResumed](https://www.tencentcloud.com/document/product/647/50771#609d1cc7606416b0e5a7186bdf90c135) | Screen sharing was resumed. |
| [onScreenCaptureStoped](https://www.tencentcloud.com/document/product/647/50771#6d61c99d694a71721431581ed1b1c0bd) | Screen sharing stopped. |
| [onScreenCaptureCovered](https://www.tencentcloud.com/document/product/647/50771#f5caba5a01c2574e2ae4ab0a5d0593ab) | The shared window was covered (for Windows only). |
| [onLocalRecordBegin](https://www.tencentcloud.com/document/product/647/50771#48421ae254e0029b6eadfe4b4810f57a) | Local recording started. |
| [onLocalRecording](https://www.tencentcloud.com/document/product/647/50771#b14c8492fe7f42893135a23434f243e0) | Local media is being recorded. |
| [onLocalRecordFragment](https://www.tencentcloud.com/document/product/647/50771#352e01c2315eca3649522dba34060de5) | Record fragment finished. |
| [onLocalRecordComplete](https://www.tencentcloud.com/document/product/647/50771#d9754b34c3638694eaf68c3ffdc183e9) | Local recording stopped. |
| [onSnapshotComplete](https://www.tencentcloud.com/document/product/647/50771#66ddc64d69b21230bd3523a78fdbb993) | Finished taking a local screenshot. |
| [onUserEnter](https://www.tencentcloud.com/document/product/647/50771#58e09a2f3f342339d38a2249150c2a45) | An anchor entered the room (disused). |
| [onUserExit](https://www.tencentcloud.com/document/product/647/50771#47d0fe4edc3978f6431931ff1331e3c7) | An anchor left the room (disused). |
| [onAudioEffectFinished](https://www.tencentcloud.com/document/product/647/50771#05a9c8f50d403a735ba04ff953c96830) | Audio effects ended (disused). |
| [onPlayBGMBegin](https://www.tencentcloud.com/document/product/647/50771#ba9e2cd78ef9abbe4c5017aea4f8334f) | Started playing background music (disused). |
| [onPlayBGMProgress](https://www.tencentcloud.com/document/product/647/50771#06c3ce9c30d9aa17cdc6a863ffd8e8bd) | Playback progress of background music (disused). |
| [onPlayBGMComplete](https://www.tencentcloud.com/document/product/647/50771#786cda61957e9bc05b2f4f3f6034ed36) | Background music stopped (disused). |
| [onSpeedTest](https://www.tencentcloud.com/document/product/647/50771#895ad42d5607c1ec46cec2f7d8e73e5c) | Result of server speed testing (disused). |

## ITRTCVideoRenderCallback

| FuncList | DESC |
| --- | --- |
| [onRenderVideoFrame](https://www.tencentcloud.com/document/product/647/50771#eeb9ee31869141d9c8d56407d8cd02a9) | Custom video rendering. |

## ITRTCVideoFrameCallback

| FuncList | DESC |
| --- | --- |
| [onGLContextCreated](https://www.tencentcloud.com/document/product/647/50771#e5d9a2200de15bc024ae70f8365aadfb) | An OpenGL context was created in the SDK. |
| [onProcessVideoFrame](https://www.tencentcloud.com/document/product/647/50771#1617c3b2b01565bb6f5dd34bdd0c6e98) | Video processing by third-party beauty filters. |
| [onGLContextDestroy](https://www.tencentcloud.com/document/product/647/50771#18827408d6e4c449f341b875ced98d48) | The OpenGL context in the SDK was destroyed. |

## ITRTCAudioFrameCallback

| FuncList | DESC |
| --- | --- |
| [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2012baeb6789e1eaabc97764626fd101) | Audio data captured by the local mic and pre-processed by the audio module. |
| [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2a3a126d62184e1cd093e47562f54774) | Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed. |
| [onPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50771#25988e5cee8c6ab0ed83c8be752fd9a6) | Audio data of each remote user before audio mixing. |
| [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50771#59235444572469f2b1458f0a5265676c) | Data mixed from each channel before being submitted to the system for playback. |
| [onMixedAllAudioFrame](https://www.tencentcloud.com/document/product/647/50771#181f1e18e56e79c8614ebc86fe63380b) | Data mixed from all the captured and to-be-played audio in the SDK. |

## ITRTCLogCallback

| FuncList | DESC |
| --- | --- |
| [onLog](https://www.tencentcloud.com/document/product/647/50771#0c0a3b56332927e19453b32de532e2d0) | Printing of local log. |

## onError

**onError**

| void onError | ([TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode |
| --- | --- |
|  | const char* errMsg |
|  | void* extraInfo) |

**Error event callback.**

Error event, which indicates that the SDK threw an irrecoverable error such as room entry failure or failure to start device

For more information, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| errCode | Error code |
| errMsg | Error message |
| extInfo | Extended field. Certain error codes may carry extra information for troubleshooting. |

## onWarning

**onWarning**

| void onWarning | ([TXLiteAVWarning](https://www.tencentcloud.com/document/product/647/35135#f29be1160857221275e6fc415e54100e) warningCode |
| --- | --- |
|  | const char* warningMsg |
|  | void* extraInfo) |

**Warning event callback.**

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

**Whether room entry is successful.**

After calling the [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) API in ` TRTCCloud ` to enter a room, you will receive the ` onEnterRoom(result) ` callback from ` TRTCCloudDelegate `.

- If room entry succeeded, ` result ` will be a positive number (` result ` > 0), indicating the time in milliseconds (ms) the room entry takes.
- If room entry failed, ` result ` will be a negative number (result < 0), indicating the error code for the failure.

For more information on the error codes for room entry failure, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| result | If ` result ` is greater than 0, it indicates the time (in ms) the room entry takes; if ` result ` is less than 0, it represents the error code for room entry. |

> **Note**1. In TRTC versions below 6.6, the ` onEnterRoom(result) ` callback is returned only if room entry succeeds, and the [onError](https://www.tencentcloud.com/document/product/647/50771#3df71ff9905826c3d788593557c7f40b) callback is returned if room entry fails.2. In TRTC 6.6 and above, the ` onEnterRoom(result) ` callback is returned regardless of whether room entry succeeds or fails, and the [onError](https://www.tencentcloud.com/document/product/647/50771#3df71ff9905826c3d788593557c7f40b) callback is also returned if room entry fails.

## onExitRoom

**onExitRoom**

| void onExitRoom | (int reason) |
| --- | --- |

**Room exit.**

Calling the [exitRoom](https://www.tencentcloud.com/document/product/647/50770#3cdc249ad1953cdbfa83c93733f952fa) API in ` TRTCCloud ` will trigger the execution of room exit-related logic, such as releasing resources of audio/video devices and codecs.

After all resources occupied by the SDK are released, the SDK will return the ` onExitRoom() ` callback.

If you need to call [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) again or switch to another audio/video SDK, please wait until you receive the ` onExitRoom() ` callback.

Otherwise, you may encounter problems such as the camera or mic being occupied.

| Param | DESC |
| --- | --- |
| reason | Reason for room exit. ` 0 `: the user called ` exitRoom ` to exit the room; ` 1 `: the user was removed from the room by the server; ` 2 `: the room was dismissed; ` 3 `: the server status was abnormal. |

## onSwitchRole

**onSwitchRole**

| void onSwitchRole | ([TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode |
| --- | --- |
|  | const char* errMsg) |

**Role switching.**

You can call the [switchRole](https://www.tencentcloud.com/document/product/647/50770#97e4bd705285a3846d2dc78e21b27508) API in ` TRTCCloud ` to switch between the anchor and audience roles. This is accompanied by a line switching process.

After the switching, the SDK will return the ` onSwitchRole() ` event callback.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates a successful switch. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onSwitchRoom

**onSwitchRoom**

| void onSwitchRoom | ([TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode |
| --- | --- |
|  | const char* errMsg) |

**Result of room switching.**

You can call the [switchRoom](https://www.tencentcloud.com/document/product/647/50770#c1f8ee70eb0df8f09cc410243a5b86af) API in ` TRTCCloud ` to switch from one room to another.

After the switching, the SDK will return the ` onSwitchRoom() ` event callback.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates a successful switch. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35124). |
| errMsg | Error message |

## onConnectOtherRoom

**onConnectOtherRoom**

| void onConnectOtherRoom | (const char* userId |
| --- | --- |
|  | [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode |
|  | const char* errMsg) |

**Result of requesting cross-room call.**

You can call the [connectOtherRoom](https://www.tencentcloud.com/document/product/647/50771#2554839cf7be6599f136a98bb6b5625b) API in ` TRTCCloud ` to establish a video call with the anchor of another room. This is the âanchor competitionâ feature.

The caller will receive the ` onConnectOtherRoom() ` callback, which can be used to determine whether the cross-room call is successful.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that cross-room connection is established successfully. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |
| userId | The user ID of the anchor (in another room) to be called |

## onDisconnectOtherRoom

**onDisconnectOtherRoom**

| void onDisconnectOtherRoom | ([TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode |
| --- | --- |
|  | const char* errMsg) |

**Result of ending cross-room call.**

You can call the disConnectOtherRoom API in ` TRTCCloud ` to end a video call with the anchor of another room. This is the âanchor competitionâ feature.

The caller will receive the ` onDisconnectOtherRoom() ` callback to determine whether the cross-room call has been successfully disconnected.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that the cross-room call has been successfully disconnected. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onUpdateOtherRoomForwardMode

**onUpdateOtherRoomForwardMode**

| void onUpdateOtherRoomForwardMode | ([TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode |
| --- | --- |
|  | const char* errMsg) |

**Result of changing the upstream capability of the cross-room anchor.**

You can call the [updateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50770#9d234f56d6bfdca31ec9390aa5ddc055) API in ` TRTCCloud ` to limit the upstream capability of the cross-room anchor in the current room, and prohibit or allow the cross-room anchor to publish audio/video/sub-stream. This behavior will affect all users in the room.

The caller will receive the ` onUpdateOtherRoomForwardMode() ` callback to determine whether the changing upstream capability of the cross-room anchor is successful.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that upstream capability of the cross-room anchor is changed successfully. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onRemoteUserEnterRoom

**onRemoteUserEnterRoom**

| void onRemoteUserEnterRoom | (const char* userId) |
| --- | --- |

**A user entered the room.**

Due to performance concerns, this callback works differently in different scenarios (i.e., ` AppScene `, which you can specify by setting the second parameter when calling [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d)).

- Live streaming scenarios ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)): in live streaming scenarios, a user is either in the role of an anchor or audience. The callback is returned only when an anchor enters the room.
- Call scenarios ([TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)): in call scenarios, the concept of roles does not apply (all users can be considered as anchors), and the callback is returned when any user enters the room.

| Param | DESC |
| --- | --- |
| userId | User ID of the remote user |

> **Note**1. The ` onRemoteUserEnterRoom ` callback indicates that a user entered the room, but it does not necessarily mean that the user enabled audio or video.2. If you want to know whether a user enabled video, we recommend you use the [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/50771#6d1cb6b1fcf292ac6f34cd8baa647937) callback.

## onRemoteUserLeaveRoom

**onRemoteUserLeaveRoom**

| void onRemoteUserLeaveRoom | (const char* userId |
| --- | --- |
|  | int reason) |

**A user exited the room.**

As with [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/50771#37486e9a6b528f6dde9ff3bed604226f), this callback works differently in different scenarios (i.e., ` AppScene `, which you can specify by setting the second parameter when calling [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d)).

- Live streaming scenarios ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)): the callback is triggered only when an anchor exits the room.
- Call scenarios ([TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)): in call scenarios, the concept of roles does not apply, and the callback is returned when any user exits the room.

| Param | DESC |
| --- | --- |
| reason | Reason for room exit. ` 0 `: the user exited the room voluntarily; ` 1 `: the user exited the room due to timeout; ` 2 `: the user was removed from the room; ` 3 `: the anchor user exited the room due to switch to audience. |
| userId | User ID of the remote user |

## onUserVideoAvailable

**onUserVideoAvailable**

| void onUserVideoAvailable | (const char* userId |
| --- | --- |
|  | bool available) |

**A remote user published/unpublished primary stream video.**

The primary stream is usually used for camera images. If you receive the ` onUserVideoAvailable(userId, true) ` callback, it indicates that the user has available primary stream video.

You can then call [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) to subscribe to the remote userâs video. If the subscription is successful, you will receive the ` onFirstVideoFrame(userid) ` callback, which indicates that the first video frame of the user is rendered.

If you receive the ` onUserVideoAvailable(userId, false) ` callback, it indicates that the video of the remote user is disabled, which may be because the user called [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50770#fbe283b224cacea70a96e4e445bebb43) or [stopLocalPreview](https://www.tencentcloud.com/document/product/647/50770#57cfe4af12b1160ae4a904e65246d70f).

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) primary stream video. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

## onUserSubStreamAvailable

**onUserSubStreamAvailable**

| void onUserSubStreamAvailable | (const char* userId |
| --- | --- |
|  | bool available) |

**A remote user published/unpublished substream video.**

The substream is usually used for screen sharing images. If you receive the ` onUserSubStreamAvailable(userId, true) ` callback, it indicates that the user has available substream video.

You can then call [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) to subscribe to the remote userâs video. If the subscription is successful, you will receive the ` onFirstVideoFrame(userid) ` callback, which indicates that the first frame of the user is rendered.

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) substream video. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

> **Note**The API used to display substream images is [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea), not startRemoteSubStreamView, startRemoteSubStreamView is deprecated.

## onUserAudioAvailable

**onUserAudioAvailable**

| void onUserAudioAvailable | (const char* userId |
| --- | --- |
|  | bool available) |

**A remote user published/unpublished audio.**

If you receive the ` onUserAudioAvailable(userId, true) ` callback, it indicates that the user published audio.

- In auto-subscription mode, the SDK will play the userâs audio automatically.
- In manual subscription mode, you can call [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/50770#457b7fc9a9cec63b20e3ab012848d235)(userid, false) to play the userâs audio.

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) audio. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

> **Note**The auto-subscription mode is used by default. You can switch to the manual subscription mode by calling [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/50770#1bd891d9afeb9021c825ab3d39da6fe7), but it must be called before room entry for the switch to take effect.

## onFirstVideoFrame

**onFirstVideoFrame**

| void onFirstVideoFrame | (const char* userId |
| --- | --- |
|  | const [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | const int width |
|  | const int height) |

**The SDK started rendering the first video frame of the local or a remote user.**

The SDK returns this event callback when it starts rendering your first video frame or that of a remote user. The ` userId ` in the callback can help you determine whether the frame is yours or a remote userâs.

- If ` userId ` is empty, it indicates that the SDK has started rendering your first video frame. The precondition is that you have called [startLocalPreview](https://www.tencentcloud.com/document/product/647/50770#66bab4d115291cba164b192ccb3c23a6) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50770#94be1579f497befa5e6450725b4f1a5c).
- If ` userId ` is not empty, it indicates that the SDK has started rendering the first video frame of a remote user. The precondition is that you have called [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) to subscribe to the userâs video.

| Param | DESC |
| --- | --- |
| height | Video height |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | The user ID of the local or a remote user. If it is empty, it indicates that the first local video frame is available; if it is not empty, it indicates that the first video frame of a remote user is available. |
| width | Video width |

> **Note**1. The callback of the first local video frame being rendered is triggered only after you call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50770#66bab4d115291cba164b192ccb3c23a6) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50770#94be1579f497befa5e6450725b4f1a5c).2. The callback of the first video frame of a remote user being rendered is triggered only after you call [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) or startRemoteSubStreamView.

## onFirstAudioFrame

**onFirstAudioFrame**

| void onFirstAudioFrame | (const char* userId) |
| --- | --- |

**The SDK started playing the first audio frame of a remote user.**

The SDK returns this callback when it plays the first audio frame of a remote user. The callback is not returned for the playing of the first audio frame of the local user.

| Param | DESC |
| --- | --- |
| userId | User ID of the remote user |

## onSendFirstLocalVideoFrame

**onSendFirstLocalVideoFrame**

| void onSendFirstLocalVideoFrame | (const [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType) |
| --- | --- |

**The first local video frame was published.**

After you enter a room and call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50770#66bab4d115291cba164b192ccb3c23a6) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50770#94be1579f497befa5e6450725b4f1a5c) to enable local video capturing (whichever happens first),

the SDK will start video encoding and publish the local video data via its network module to the cloud.

It returns the ` onSendFirstLocalVideoFrame ` callback after publishing the first local video frame.

| Param | DESC |
| --- | --- |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |

## onSendFirstLocalAudioFrame

**onSendFirstLocalAudioFrame**

**The first local audio frame was published.**

After you enter a room and call [startLocalAudio](https://www.tencentcloud.com/document/product/647/50770#37f11bf81ac7eef6af030790d31bc86d) to enable audio capturing (whichever happens first),

the SDK will start audio encoding and publish the local audio data via its network module to the cloud.

The SDK returns the ` onSendFirstLocalAudioFrame ` callback after sending the first local audio frame.

## onRemoteVideoStatusUpdated

**onRemoteVideoStatusUpdated**

| void onRemoteVideoStatusUpdated | (const char*  userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | [TRTCAVStatusType](https://www.tencentcloud.com/document/product/647/50775#8ff0fad63c24db1b35490152f56d5bb3) status |
|  | [TRTCAVStatusChangeReason](https://www.tencentcloud.com/document/product/647/50775#37616803ec0eec21697bb3c20f20ca0d) reason |
|  | void *extrainfo) |

**Change of remote video status.**

You can use this callback to get the status (` Playing `, ` Loading `, or ` Stopped `) of the video of each remote user and display it on the UI.

| Param | DESC |
| --- | --- |
| extraInfo | Extra information |
| reason | Reason for the change of status |
| status | Video status, which may be ` Playing `, ` Loading `, or ` Stopped ` |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | User ID |

## onRemoteAudioStatusUpdated

**onRemoteAudioStatusUpdated**

| void onRemoteAudioStatusUpdated | (const char*  userId |
| --- | --- |
|  | [TRTCAVStatusType](https://www.tencentcloud.com/document/product/647/50775#8ff0fad63c24db1b35490152f56d5bb3) status |
|  | [TRTCAVStatusChangeReason](https://www.tencentcloud.com/document/product/647/50775#37616803ec0eec21697bb3c20f20ca0d) reason |
|  | void *extrainfo) |

**Change of remote audio status.**

You can use this callback to get the status (` Playing `, ` Loading `, or ` Stopped `) of the audio of each remote user and display it on the UI.

| Param | DESC |
| --- | --- |
| extraInfo | Extra information |
| reason | Reason for the change of status |
| status | Audio status, which may be ` Playing `, ` Loading `, or ` Stopped ` |
| userId | User ID |

## onUserVideoSizeChanged

**onUserVideoSizeChanged**

| void onUserVideoSizeChanged | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | int newWidth |
|  | int newHeight) |

**Change of remote video size.**

If you receive the ` onUserVideoSizeChanged(userId, streamType, newWidth, newHeight) ` callback, it indicates that the user changed the video size. It may be triggered by [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50770#0450f3674968a78b9a53a17865aa5277) or [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50770#dd9e46a8eafd30b0f054a2c1e720868c).

| Param | DESC |
| --- | --- |
| newHeight | Video height |
| newWidth | Video width |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | User ID |

## onNetworkQuality

**onNetworkQuality**

| void onNetworkQuality | ([TRTCQualityInfo](https://www.tencentcloud.com/document/product/647/50775#008511ed00730a2ef603fd62f64ca33c) localQuality |
| --- | --- |
|  | [TRTCQualityInfo](https://www.tencentcloud.com/document/product/647/50775#008511ed00730a2ef603fd62f64ca33c)* remoteQuality |
|  | uint32_t remoteQualityCount) |

**Real-time network quality statistics.**

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

| void onStatistics | (const [TRTCStatistics](https://www.tencentcloud.com/document/product/647/50772#dc3354e15492d5bac4a773a6e230c9eb)& statistics) |
| --- | --- |

**Real-time statistics on technical metrics.**

This callback is returned every 2 seconds and notifies you of the statistics on technical metrics related to video, audio, and network. The metrics are listed in [TRTCStatistics](https://www.tencentcloud.com/document/product/647/50772#dc3354e15492d5bac4a773a6e230c9eb):

- Video statistics: video resolution (` resolution `), frame rate (` FPS `), bitrate (` bitrate `), etc.
- Audio statistics: audio sample rate (` samplerate `), number of audio channels (` channel `), bitrate (` bitrate `), etc.
- Network statistics: the round trip time (` rtt `) between the SDK and the cloud (SDK -> Cloud -> SDK), package loss rate (` loss `), upstream traffic (` sentBytes `), downstream traffic (` receivedBytes `), etc.

| Param | DESC |
| --- | --- |
| statistics | Statistics, including local statistics and the statistics of remote users. For details, please see [TRTCStatistics](https://www.tencentcloud.com/document/product/647/50772#dc3354e15492d5bac4a773a6e230c9eb). |

> **Note**If you want to learn about only the current network quality and do not want to spend much time analyzing the statistics returned by this callback, we recommend you use [onNetworkQuality](https://www.tencentcloud.com/document/product/647/50771#7faad64d9fbb7d65876027eaa7d60b3d).

## onSpeedTestResult

**onSpeedTestResult**

| void onSpeedTestResult | (const [TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/50775#25124dd8b486afcaeaabe326bfe10288)& result) |
| --- | --- |

**Callback of network speed test.**

The callback is triggered by [startSpeedTest](https://www.tencentcloud.com/document/product/647/50770#ad6d84be7e3d8b20fae6b5f6f56d65f0).

| Param | DESC |
| --- | --- |
| result | Speed test data, including loss rates, rtt and bandwidth rates, please refer to [TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/50775#25124dd8b486afcaeaabe326bfe10288) for details. |

## onConnectionLost

**onConnectionLost**

**The SDK was disconnected from the cloud.**

The SDK returns this callback when it is disconnected from the cloud, which may be caused by network unavailability or change of network, for example, when the user walks into an elevator.

After returning this callback, the SDK will attempt to reconnect to the cloud, and will return the [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50771#f4c4e0fc1d93660732758709d477efcc) callback. When it is reconnected, it will return the [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50771#ddabb835fc7f8359827e33ba72514ec8) callback.

In other words, the SDK proceeds from one event to the next in the following order:

![](https://qcloudimg.tencent-cloud.cn/raw/fb3c40a4fca55b0010d385cf3b2472cd.png)

## onTryToReconnect

**onTryToReconnect**

**The SDK is reconnecting to the cloud.**

When the SDK is disconnected from the cloud, it returns the [onConnectionLost](https://www.tencentcloud.com/document/product/647/50771#6f1f6ac255f4027285ade6528d7fd80a) callback. It then attempts to reconnect and returns this callback ([onTryToReconnect](https://www.tencentcloud.com/document/product/647/50771#f4c4e0fc1d93660732758709d477efcc)). After it is reconnected, it returns the [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50771#ddabb835fc7f8359827e33ba72514ec8) callback.

## onConnectionRecovery

**onConnectionRecovery**

**The SDK is reconnected to the cloud.**

When the SDK is disconnected from the cloud, it returns the [onConnectionLost](https://www.tencentcloud.com/document/product/647/50771#6f1f6ac255f4027285ade6528d7fd80a) callback. It then attempts to reconnect and returns the [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50771#f4c4e0fc1d93660732758709d477efcc) callback. After it is reconnected, it returns this callback ([onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50771#ddabb835fc7f8359827e33ba72514ec8)).

## onCameraDidReady

**onCameraDidReady**

**The camera is ready.**

After you call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50770#66bab4d115291cba164b192ccb3c23a6), the SDK will try to start the camera and return this callback if the camera is started.

If it fails to start the camera, itâs probably because the application does not have access to the camera or the camera is being used.

You can capture the [onError](https://www.tencentcloud.com/document/product/647/50771#3df71ff9905826c3d788593557c7f40b) callback to learn about the exception and let users know via UI messages.

## onMicDidReady

**onMicDidReady**

**The mic is ready.**

After you call [startLocalAudio](https://www.tencentcloud.com/document/product/647/50770#37f11bf81ac7eef6af030790d31bc86d), the SDK will try to start the mic and return this callback if the mic is started.

If it fails to start the mic, itâs probably because the application does not have access to the mic or the mic is being used.

You can capture the [onError](https://www.tencentcloud.com/document/product/647/50771#3df71ff9905826c3d788593557c7f40b) callback to learn about the exception and let users know via UI messages.

## onAudioRouteChanged

**onAudioRouteChanged**

| void onAudioRouteChanged | ([TRTCAudioRoute](https://www.tencentcloud.com/document/product/647/50775#aaca0d57f6f9d9c6a6425485464b0877) newRoute |
| --- | --- |
|  | [TRTCAudioRoute](https://www.tencentcloud.com/document/product/647/50775#aaca0d57f6f9d9c6a6425485464b0877) oldRoute) |

**The audio route changed (for mobile devices only).**

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

| void onUserVoiceVolume | ([TRTCVolumeInfo](https://www.tencentcloud.com/document/product/647/50775#1def2d8caf1114940341ba89a751d79d)* userVolumes |
| --- | --- |
|  | uint32_t userVolumesCount |
|  | uint32_t totalVolume) |

**Volume.**

The SDK can assess the volume of each channel and return this callback on a regular basis. You can display, for example, a waveform or volume bar on the UI based on the statistics returned.

You need to first call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50770#1e7a0c85189378920f2e2a446d897907) to enable the feature and set the interval for the callback.

Note that the SDK returns this callback at the specified interval regardless of whether someone is speaking in the room.

| Param | DESC |
| --- | --- |
| totalVolume | The total volume of all remote users. Value range: [0, 100] |
| userVolumes | An array that represents the volume of all users who are speaking in the room. Value range: [0, 100] |

> **Note**` userVolumes ` is an array. If ` userId ` is empty, the elements in the array represent the volume of the local userâs audio. Otherwise, they represent the volume of a remote userâs audio.

## onDeviceChange

**onDeviceChange**

| void onDeviceChange | (const char* deviceId |
| --- | --- |
|  | TRTCDeviceType type |
|  | TRTCDeviceState state) |

**The status of a local device changed (for desktop OS only).**

The SDK returns this callback when a local device (camera, mic, or speaker) is connected or disconnected.

| Param | DESC |
| --- | --- |
| deviceId | Device ID |
| deviceType | Device type. ` 0 `: microphone; ` 1 `: speak; ` 2 `: camera |
| state | Device status. ` 0 `: connected; ` 1 `: disconnected; ` 2 `: started |

## onAudioDeviceCaptureVolumeChanged

**onAudioDeviceCaptureVolumeChanged**

| void onAudioDeviceCaptureVolumeChanged | (uint32_t volume |
| --- | --- |
|  | bool muted) |

**The capturing volume of the mic changed.**

On desktop OS such as macOS and Windows, users can set the capturing volume of the mic in the audio control panel.

The higher volume a user sets, the higher the volume of raw audio captured by the mic.

On some keyboards and laptops, users can also mute the mic by pressing a key (whose icon is a crossed out mic).

When users set the mic capturing volume via the UI or a keyboard shortcut, the SDK will return this callback.

| Param | DESC |
| --- | --- |
| muted | Whether the mic is muted. ` true `: muted; ` false `: unmuted |
| volume | System audio capturing volume, which users can set in the audio control panel. Value range: [0, 100] |

> **Note**You need to call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50770#1e7a0c85189378920f2e2a446d897907) and set the callback interval (` interval ` > 0) to enable the callback. To disable the callback, set ` interval ` to ` 0 `.

## onAudioDevicePlayoutVolumeChanged

**onAudioDevicePlayoutVolumeChanged**

| void onAudioDevicePlayoutVolumeChanged | (uint32_t volume |
| --- | --- |
|  | bool muted) |

**The playback volume changed.**

On desktop OS such as macOS and Windows, users can set the systemâs playback volume in the audio control panel.

On some keyboards and laptops, users can also mute the speaker by pressing a key (whose icon is a crossed out speaker).

When users set the systemâs playback volume via the UI or a keyboard shortcut, the SDK will return this callback.

| Param | DESC |
| --- | --- |
| muted | Whether the speaker is muted. ` true `: muted; ` false `: unmuted |
| volume | The system playback volume, which users can set in the audio control panel. Value range: 0-100 |

> **Note**You need to call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50770#1e7a0c85189378920f2e2a446d897907) and set the callback interval (` interval ` > 0) to enable the callback. To disable the callback, set ` interval ` to ` 0 `.

## onSystemAudioLoopbackError

**onSystemAudioLoopbackError**

| void onSystemAudioLoopbackError | ([TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode) |
| --- | --- |

**Whether system audio capturing is enabled successfully (for desktop OS only).**

On macOS, you can call [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50770#792556646f98fdbb0eb9e4b7fb12c42b) to install an audio driver and have the SDK capture the audio played back by the system.

On Windows systems, you can use [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50770#792556646f98fdbb0eb9e4b7fb12c42b) to have the SDK capture the audio played back by the system.

In use cases such as video teaching and music live streaming, the teacher can use this feature to let the SDK capture the sound of the video played by his or her computer, so that students in the room can hear the sound too.

The SDK returns this callback after trying to enable system audio capturing. To determine whether it is actually enabled, pay attention to the error parameter in the callback.

| Param | DESC |
| --- | --- |
| err | If it is ` ERR_NULL `, system audio capturing is enabled successfully. Otherwise, it is not. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |

## onTestMicVolume

**onTestMicVolume**

| void onTestMicVolume | (uint32_t volume) |
| --- | --- |

**Volume during mic test.**

When you call [startMicDeviceTest](https://www.tencentcloud.com/document/product/647/50774#174b1e8a4204caace366f2731d49efb7) to test the mic, the SDK will keep returning this callback. The ` volume ` parameter represents the volume of the audio captured by the mic.

If the value of the ` volume ` parameter fluctuates, the mic works properly. If it is ` 0 ` throughout the test, it indicates that there is a problem with the mic, and users should be prompted to switch to a different mic.

| Param | DESC |
| --- | --- |
| volume | Captured mic volume. Value range: [0, 100] |

## onTestSpeakerVolume

**onTestSpeakerVolume**

| void onTestSpeakerVolume | (uint32_t volume) |
| --- | --- |

**Volume during speaker test.**

When you call [startSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50774#172044ecaba3934d3056dc14dd5a4306) to test the speaker, the SDK will keep returning this callback.

The ` volume ` parameter in the callback represents the volume of audio sent by the SDK to the speaker for playback. If its value fluctuates but users cannot hear any sound, the speaker is not working properly.

| Param | DESC |
| --- | --- |
| volume | The volume of audio sent by the SDK to the speaker for playback. Value range: [0, 100] |

## onRecvCustomCmdMsg

**onRecvCustomCmdMsg**

| void onRecvCustomCmdMsg | (const char* userId |
| --- | --- |
|  | int32_t cmdID |
|  | uint32_t seq |
|  | const uint8_t* message |
|  | uint32_t messageSize) |

**Receipt of custom message.**

When a user in a room uses [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50770#b39e25426586d217f2fdf44b7777b47c) to send a custom message, other users in the room can receive the message through the ` onRecvCustomCmdMsg ` callback.

| Param | DESC |
| --- | --- |
| cmdID | Command ID |
| message | Message data |
| seq | Message serial number |
| userId | User ID |

## onMissCustomCmdMsg

**onMissCustomCmdMsg**

| void onMissCustomCmdMsg | (const char* userId |
| --- | --- |
|  | int32_t cmdID |
|  | int32_t errCode |
|  | int32_t missed) |

**Loss of custom message.**

When you use [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50770#b39e25426586d217f2fdf44b7777b47c) to send a custom UDP message, even if you enable reliable transfer (by setting ` reliable ` to ` true `), there is still a chance of message loss. Reliable transfer only helps maintain a low probability of message loss, which meets the reliability requirements in most cases.

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

| void onRecvSEIMsg | (const char* userId |
| --- | --- |
|  | const uint8_t* message |
|  | uint32_t messageSize) |

**Receipt of SEI message.**

If a user in the room uses [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50770#419654e5edfe1587ac98d7d43a47c744) to send an SEI message via video frames, other users in the room can receive the message through the ` onRecvSEIMsg ` callback.

| Param | DESC |
| --- | --- |
| message | Data |
| userId | User ID |

## onStartPublishing

**onStartPublishing**

| void onStartPublishing | (int err |
| --- | --- |
|  | const char *errMsg) |

**Started publishing to Tencent Cloud CSS CDN.**

When you call startPublishing to publish streams to Tencent Cloud CSS CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStopPublishing

**onStopPublishing**

| void onStopPublishing | (int err |
| --- | --- |
|  | const char *errMsg) |

**Stopped publishing to Tencent Cloud CSS CDN.**

When you call stopPublishing to stop publishing streams to Tencent Cloud CSS CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStartPublishCDNStream

**onStartPublishCDNStream**

| void onStartPublishCDNStream | (int errCode |
| --- | --- |
|  | const char* errMsg) |

**Started publishing to non-Tencent Cloudâs live streaming CDN.**

When you call startPublishCDNStream to start publishing streams to a non-Tencent Cloudâs live streaming CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

> **Note**If you receive a callback that the command is executed successfully, it only means that your command was sent to Tencent Cloudâs backend server. If the CDN vendor does not accept your streams, the publishing will still fail.

## onStopPublishCDNStream

**onStopPublishCDNStream**

| void onStopPublishCDNStream | (int errCode |
| --- | --- |
|  | const char* errMsg) |

**Stopped publishing to non-Tencent Cloudâs live streaming CDN.**

When you call stopPublishCDNStream to stop publishing to a non-Tencent Cloudâs live streaming CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onSetMixTranscodingConfig

**onSetMixTranscodingConfig**

| void onSetMixTranscodingConfig | (int err |
| --- | --- |
|  | const char* errMsg) |

**Set the layout and transcoding parameters for On-Cloud MixTranscoding.**

When you call setMixTranscodingConfig to modify the layout and transcoding parameters for On-Cloud MixTranscoding, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStartPublishMediaStream

**onStartPublishMediaStream**

| void onStartPublishMediaStream | (const char* taskId |
| --- | --- |
|  | int code |
|  | const char* message |
|  | void* extraInfo) |

**Callback for starting to publish.**

When you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a) to publish a stream to the TRTC backend, the SDK will immediately update the command to the cloud server.

The SDK will then receive the publishing result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server failed to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended actions are as follows: 2000: Parameter error. Check the request parameters. 2001: Live streaming service is not enabled. Enable it in the Live streaming console. 2021: Third-party retweet service is not enabled. Contact product support to enable it. 3000: Internal server error. Retry is recommended. 4006: Concurrency conflict with the same task. The server is still processing the previous startPublishMediaStream task. Retry after a delay is recommended. 4007: The same task has already been successfully started using startPublishMediaStream. Use the returned taskId to call the updatePublishMediaStream API to update the task. 5001: Resource constraints. Retry after a delay is recommended. |
| message | : The callback information. |
| taskId | : If a request is successful, a task ID will be returned via the callback. You need to provide this task ID when you call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#311979ce8f747d30ba68eb412789fffd) to modify publishing parameters or [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#f4d187c5e85084e1f96efcea1b5e076a) to stop publishing. |

## onUpdatePublishMediaStream

**onUpdatePublishMediaStream**

| void onUpdatePublishMediaStream | (const char* taskId |
| --- | --- |
|  | int code |
|  | const char* message |
|  | void* extraInfo) |

**Callback for modifying publishing parameters.**

When you call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#311979ce8f747d30ba68eb412789fffd) to modify publishing parameters, the SDK will immediately update the command to the cloud server.

The SDK will then receive the modification result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server failed to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended solutions are as follows: 2000: Parameter error. Check the request parameters. 2001: Live streaming service is not enabled. Enable it in the Live Streaming Console. 2002: Task not found. Restart the task by calling the startPublishMediaStream API. 2018: Concurrent requests are out of order. Retry with the latest streaming parameters. 2021: Third-party retweet service is not enabled. Contact product support to enable it. 3000: Internal server error. Retry. 4003: Task is exiting. Stop the task by calling the stopPublishMediaStream API first, then restart it by calling the startPublishMediaStream API. |
| message | : The callback information. |
| taskId | : The task ID you pass in when calling [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#311979ce8f747d30ba68eb412789fffd), which is used to identify a request. |

## onStopPublishMediaStream

**onStopPublishMediaStream**

| void onStopPublishMediaStream | (const char* taskId |
| --- | --- |
|  | int code |
|  | const char* message |
|  | void* extraInfo) |

**Callback for stopping publishing.**

When you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#f4d187c5e85084e1f96efcea1b5e076a) to stop publishing, the SDK will immediately update the command to the cloud server.

The SDK will then receive the modification result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server was unable to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended actions are as follows: 2000: Parameter error. Please check the request parameters. 2002: Task not found. No action required. 3000: Internal server error. Please retry. 4003: Task is exiting. No action required. |
| message | : The callback information. |
| taskId | : The task ID you pass in when calling [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#f4d187c5e85084e1f96efcea1b5e076a), which is used to identify a request. |

## onCdnStreamStateChanged

**onCdnStreamStateChanged**

| void onCdnStreamStateChanged | (const char* cdnUrl |
| --- | --- |
|  | int status |
|  | int code |
|  | const char* msg |
|  | void* extraInfo) |

**Callback for change of RTMP/RTMPS publishing status.**

When you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a) to publish a stream to the TRTC backend, the SDK will immediately update the command to the cloud server.

If you set the publishing destination ([TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50775#e106259cbc7f1cff297f52931b7e7c49)) to the URL of Tencent Cloud or a third-party CDN, you will be notified of the RTMP/RTMPS publishing status via this callback.

| Param | DESC |
| --- | --- |
| cdnUrl | : The URL you specify in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50775#e106259cbc7f1cff297f52931b7e7c49) when you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a). |
| code | : The publishing result. ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues. |
| message | : The publishing information. |
| status | : The publishing status. 0: The publishing has not started yet or has ended. This value will be returned after you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#f4d187c5e85084e1f96efcea1b5e076a). 1: The TRTC server is connecting to the CDN server. If the first attempt fails, the TRTC backend will retry multiple times and will return this value via the callback (every five seconds). After publishing succeeds, the value ` 2 ` will be returned. If a server error occurs or publishing is still unsuccessful after 60 seconds, the value ` 4 ` will be returned. 2: The TRTC server is publishing to the CDN. This value will be returned if the publishing succeeds. 3: The TRTC server is disconnected from the CDN server and is reconnecting. If a CDN error occurs or publishing is interrupted, the TRTC backend will try to reconnect and resume publishing and will return this value via the callback (every five seconds). After publishing resumes, the value ` 2 ` will be returned. If a server error occurs or the attempt to resume publishing is still unsuccessful after 60 seconds, the value ` 4 ` will be returned. 4: The TRTC server is disconnected from the CDN server and failed to reconnect within the timeout period. In this case, the publishing is deemed to have failed. You can call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#311979ce8f747d30ba68eb412789fffd) to try again. 5: The TRTC server is disconnecting from the CDN server. After you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#f4d187c5e85084e1f96efcea1b5e076a), the SDK will return this value first and then the value ` 0 `. |

## onScreenCaptureStarted

**onScreenCaptureStarted**

**Screen sharing started.**

The SDK returns this callback when you call [startScreenCapture](https://www.tencentcloud.com/document/product/647/50770#94be1579f497befa5e6450725b4f1a5c) and other APIs to start screen sharing.

## onScreenCapturePaused

**onScreenCapturePaused**

| void onScreenCapturePaused | (int reason) |
| --- | --- |

**Screen sharing was paused.**

The SDK returns this callback when you call [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/50770#1403f1a194ad64c9c1edefe09758990e) to pause screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user paused screen sharing. ` 1 `: screen sharing was paused because the shared window became invisible(Mac). screen sharing was paused because setting parameters(Windows). ` 2 `: screen sharing was paused because the shared window became minimum(only for Windows). ` 3 `: screen sharing was paused because the shared window became invisible(only for Windows). ` 4 `: screen sharing was paused because the system operation(only for iOS). |

## onScreenCaptureResumed

**onScreenCaptureResumed**

| void onScreenCaptureResumed | (int reason) |
| --- | --- |

**Screen sharing was resumed.**

The SDK returns this callback when you call [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/50770#d8717bb76a81445b956b856befa37a2a) to resume screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user resumed screen sharing. ` 1 `: screen sharing was resumed automatically after the shared window became visible again(Mac). screen sharing was resumed automatically after setting parameters(Windows). ` 2 `: screen sharing was resumed automatically after the shared window became minimize recovery(only for Windows). ` 3 `: screen sharing was resumed automatically after the shared window became visible again(only for Windows). ` 4 `: screen sharing was resumed because the system operation(only for iOS). |

## onScreenCaptureStoped

**onScreenCaptureStoped**

| void onScreenCaptureStoped | (int reason) |
| --- | --- |

**Screen sharing stopped.**

The SDK returns this callback when you call [stopScreenCapture](https://www.tencentcloud.com/document/product/647/50770#f509d7682570422562b2dce3dca474be) to stop screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user stopped screen sharing; ` 1 `: screen sharing stopped because the shared window was closed. |

## onScreenCaptureCovered

**onScreenCaptureCovered**

**The shared window was covered (for Windows only).**

The SDK returns this callback when the shared window is covered and cannot be captured. Upon receiving this callback, you can prompt users via the UI to move and expose the window.

## onLocalRecordBegin

**onLocalRecordBegin**

| void onLocalRecordBegin | (int errCode |
| --- | --- |
|  | const char* storagePath) |

**Local recording started.**

When you call [startLocalRecording](https://www.tencentcloud.com/document/product/647/50770#addffbd3c894aca3c6a8efa01936a086) to start local recording, the SDK returns this callback to notify you whether recording is started successfully.

| Param | DESC |
| --- | --- |
| errCode | status.  0: successful. -1: failed. -2: unsupported format. -6: recording has been started. Stop recording first. -7: recording file already exists and needs to be deleted. -8: recording directory does not have the write permission. Please check the directory permission. |
| storagePath | Storage path of recording file |

## onLocalRecording

**onLocalRecording**

| void onLocalRecording | (long duration |
| --- | --- |
|  | const char* storagePath) |

**Local media is being recorded.**

The SDK returns this callback regularly after local recording is started successfully via the calling of [startLocalRecording](https://www.tencentcloud.com/document/product/647/50770#addffbd3c894aca3c6a8efa01936a086).

You can capture this callback to stay up to date with the status of the recording task.

You can set the callback interval when calling [startLocalRecording](https://www.tencentcloud.com/document/product/647/50770#addffbd3c894aca3c6a8efa01936a086).

| Param | DESC |
| --- | --- |
| duration | Cumulative duration of recording, in milliseconds |
| storagePath | Storage path of recording file |

## onLocalRecordFragment

**onLocalRecordFragment**

| void onLocalRecordFragment | (const char* storagePath) |
| --- | --- |

**Record fragment finished.**

When fragment recording is enabled, this callback will be invoked when each fragment file is finished.

| Param | DESC |
| --- | --- |
| storagePath | Storage path of the fragment. |

## onLocalRecordComplete

**onLocalRecordComplete**

| void onLocalRecordComplete | (int errCode |
| --- | --- |
|  | const char* storagePath) |

**Local recording stopped.**

When you call [stopLocalRecording](https://www.tencentcloud.com/document/product/647/50770#2e45348447589f72e1c44ae10e0f4de1) to stop local recording, the SDK returns this callback to notify you of the recording result.

| Param | DESC |
| --- | --- |
| errCode | status  0: successful. -1: failed. -2: Switching resolution or horizontal and vertical screen causes the recording to stop. -3: recording duration is too short or no video or audio data is received. Check the recording duration or whether audio or video capture is enabled. |
| storagePath | Storage path of recording file |

## onSnapshotComplete

**onSnapshotComplete**

| void onSnapshotComplete | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) type |
|  | char* data |
|  | uint32_t length |
|  | uint32_t width |
|  | uint32_t height |
|  | [TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) format) |

**Finished taking a local screenshot.**

| Param | DESC |
| --- | --- |
| bmp | Screenshot result. If it is ` null `, the screenshot failed to be taken. |
| data | Screenshot data. If it is ` nullptr `, it indicates that the SDK failed to take the screenshot. |
| format | Screenshot data format. Only [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) is supported now. |
| height | Screenshot height |
| length | Screenshot data length. In BGRA32 format, ` length = width * height * 4 `. |
| type | Video stream type |
| userId | User ID. If it is empty, the screenshot is a local image. |
| width | Screenshot width |

> **Note**The parameters of the full-platform C++ interface and the Java interface are different. The C++ interface uses 7 parameters to describe a screenshot, while the Java interface uses only one Bitmap to describe a screenshot.

## onUserEnter

**onUserEnter**

| void onUserEnter | (const char* userId) |
| --- | --- |

**An anchor entered the room (disused).**

@deprecated This callback is not recommended in the new version. Please use [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/50771#37486e9a6b528f6dde9ff3bed604226f) instead.

## onUserExit

**onUserExit**

| void onUserExit | (const char* userId |
| --- | --- |
|  | int reason) |

**An anchor left the room (disused).**

@deprecated This callback is not recommended in the new version. Please use [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/50771#8afca198f4d52b72c44846f3e15f3a06) instead.

## onAudioEffectFinished

**onAudioEffectFinished**

| void onAudioEffectFinished | (int effectId |
| --- | --- |
|  | int code) |

**Audio effects ended (disused).**

@deprecated This callback is not recommended in the new version. Please use TXAudioEffectManager instead.

Audio effects and background music can be started using the same API ([startPlayMusic](https://www.tencentcloud.com/document/product/647/50773#aacead5ce840018e0505825e2b942052)) now instead of separate ones.

## onPlayBGMBegin

**onPlayBGMBegin**

| void onPlayBGMBegin | ([TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode) |
| --- | --- |

**Started playing background music (disused).**

@deprecated This callback is not recommended in the new version. Please use [ITXMusicPlayObserver](https://www.tencentcloud.com/document/product/647/50773#8bc42ffc210c9d2b244908a2c914e2d8) instead.

Audio effects and background music can be started using the same API ([startPlayMusic](https://www.tencentcloud.com/document/product/647/50773#aacead5ce840018e0505825e2b942052)) now instead of separate ones.

## onPlayBGMProgress

**onPlayBGMProgress**

| void onPlayBGMProgress | (uint32_t progressMS |
| --- | --- |
|  | uint32_t durationMS) |

**Playback progress of background music (disused).**

@deprecated This callback is not recommended in the new version. Please use [ITXMusicPlayObserver](https://www.tencentcloud.com/document/product/647/50773#8bc42ffc210c9d2b244908a2c914e2d8) instead.

Audio effects and background music can be started using the same API ([startPlayMusic](https://www.tencentcloud.com/document/product/647/50773#aacead5ce840018e0505825e2b942052)) now instead of separate ones.

## onPlayBGMComplete

**onPlayBGMComplete**

| void onPlayBGMComplete | ([TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) errCode) |
| --- | --- |

**Background music stopped (disused).**

@deprecated This callback is not recommended in the new version. Please use [ITXMusicPlayObserver](https://www.tencentcloud.com/document/product/647/50773#8bc42ffc210c9d2b244908a2c914e2d8) instead.

Audio effects and background music can be started using the same API ([startPlayMusic](https://www.tencentcloud.com/document/product/647/50773#aacead5ce840018e0505825e2b942052)) now instead of separate ones.

## onSpeedTest

**onSpeedTest**

| void onSpeedTest | (const [TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/50775#25124dd8b486afcaeaabe326bfe10288)& currentResult |
| --- | --- |
|  | uint32_t finishedCount |
|  | uint32_t totalCount) |

**Result of server speed testing (disused).**

@deprecated This callback is not recommended in the new version. Please use onSpeedTestResult: instead.

## onRenderVideoFrame

**onRenderVideoFrame**

| void onRenderVideoFrame | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50775#9233a1b1573333abc70e53b51bd89740)* frame) |

**Custom video rendering.**

If you have configured the callback of custom rendering for local or remote video, the SDK will return to you via this callback video frames that are otherwise sent to the rendering control, so that you can customize rendering.

| Param | DESC |
| --- | --- |
| frame | Video frames to be rendered |
| streamType | Stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | ` userId ` of the video source. This parameter can be ignored if the callback is for local video (setLocalVideoRenderDelegate). |

## onGLContextCreated

**onGLContextCreated**

**An OpenGL context was created in the SDK.**

## onProcessVideoFrame

**onProcessVideoFrame**

| int onProcessVideoFrame | ([TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50775#9233a1b1573333abc70e53b51bd89740) *srcFrame |
| --- | --- |
|  | [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50775#9233a1b1573333abc70e53b51bd89740) *dstFrame) |

**Video processing by third-party beauty filters.**

If you use a third-party beauty filter component, you need to configure this callback in ` TRTCCloud ` to have the SDK return to you video frames that are otherwise pre-processed by TRTC.

You can then send the video frames to the third-party beauty filter component for processing. As the data returned can be read and modified, the result of processing can be synced to TRTC for subsequent encoding and publishing.

Case 1: the beauty filter component generates new textures

If the beauty filter component you use generates a frame of new texture (for the processed image) during image processing, please set ` dstFrame.textureId ` to the ID of the new texture in the callback function.

```
int onProcessVideoFrame(TRTCVideoFrame * srcFrame, TRTCVideoFrame *dstFrame) {    dstFrame->textureId = mFURenderer.onDrawFrameSingleInput(srcFrame->textureId);    return 0;}
```

Case 2: you need to provide target textures to the beauty filter component

If the third-party beauty filter component you use does not generate new textures and you need to manually set an input texture and an output texture for the component, you can consider the following scheme:

```
int onProcessVideoFrame(TRTCVideoFrame *srcFrame, TRTCVideoFrame *dstFrame) {    thirdparty_process(srcFrame->textureId, srcFrame->width, srcFrame->height, dstFrame->textureId);    return 0;}
```

| Param | DESC |
| --- | --- |
| dstFrame | Used to receive video images processed by third-party beauty filters |
| srcFrame | Used to carry images captured by TRTC via the camera |

> **Note**Currently, only the OpenGL texture scheme is supported(PC supports TRTCVideoBufferType_Buffer format Only)

## onGLContextDestroy

**onGLContextDestroy**

**The OpenGL context in the SDK was destroyed.**

## onCapturedAudioFrame

**onCapturedAudioFrame**

| void onCapturedAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a) *frame) |
| --- | --- |

**Audio data captured by the local mic and pre-processed by the audio module.**

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

| void onLocalProcessedAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a) *frame) |
| --- | --- |

**Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed.**

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

> **Note**1. Please avoid time-consuming operations in this callback function. The SDK processes an audio frame every 20 ms, so if your operation takes more than 20 ms, it will cause audio exceptions.2. The audio data returned via this callback can be read and modified, but please keep the duration of your operation short.3. Audio data is returned via this callback after ANS, AEC, AGC, effect-processing and BGM-mixing, and therefore the delay is longer than that with [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2012baeb6789e1eaabc97764626fd101).

## onPlayAudioFrame

**onPlayAudioFrame**

| void onPlayAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a) *frame |
| --- | --- |
|  | const char* userId) |

**Audio data of each remote user before audio mixing.**

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

| void onMixedPlayAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a) *frame) |
| --- | --- |

**Data mixed from each channel before being submitted to the system for playback.**

After you configure the callback of custom audio processing, the SDK will return to you via this callback the data (PCM format) mixed from each channel before it is submitted to the system for playback.

- The audio data returned via this callback is in PCM format and has a fixed frame length (time) of 0.02s.
- The formula to convert a frame length in seconds to one in bytes is **sample rate * frame length in seconds * number of sound channels * audio bit depth**.
- Assume that the audio is recorded on a single channel with a sample rate of 48,000 Hz and audio bit depth of 16 bits, which are the default settings of TRTC. The frame length in bytes will be **48000 * 0.02s * 1 * 16 bits = 15360 bits = 1920 bytes**.

| Param | DESC |
| --- | --- |
| frame | Audio frames in PCM format |

> **Note**1. Please avoid time-consuming operations in this callback function. The SDK processes an audio frame every 20 ms, so if your operation takes more than 20 ms, it will cause audio exceptions.2. The audio data returned via this callback can be read and modified, but please keep the duration of your operation short.3. The audio data returned via this callback is the audio data mixed from each channel before it is played. It does not include the in-ear monitoring data.

## onMixedAllAudioFrame

**onMixedAllAudioFrame**

| void onMixedAllAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a) *frame) |
| --- | --- |

**Data mixed from all the captured and to-be-played audio in the SDK.**

After you configure the callback of custom audio processing, the SDK will return via this callback the data (PCM format) mixed from all captured and to-be-played audio in the SDK, so that you can customize recording.

- The audio data returned via this callback is in PCM format and has a fixed frame length (time) of 0.02s.
- The formula to convert a frame length in seconds to one in bytes is **sample rate * frame length in seconds * number of sound channels * audio bit depth**.
- Assume that the audio is recorded on a single channel with a sample rate of 48,000 Hz and audio bit depth of 16 bits, which are the default settings of TRTC. The frame length in bytes will be **48000 * 0.02s * 1 * 16 bits = 15360 bits = 1920 bytes**.

| Param | DESC |
| --- | --- |
| frame | Audio frames in PCM format |

> **Note**1. This data returned via this callback is mixed from all audio in the SDK, including local audio after pre-processing (ANS, AEC, and AGC), special effects application, and music mixing, as well as all remote audio, but it does not include the in-ear monitoring data.2. The audio data returned via this callback cannot be modified.

## onLog

**onLog**

| void onLog | (const char* log |
| --- | --- |
|  | [TRTCLogLevel](https://www.tencentcloud.com/document/product/647/50775#3b7ff44175cba4dd48e97aa8ac7b0b98) level |
|  | const char* module) |

**Printing of local log.**

If you want to capture the local log printing event, you can configure the log callback to have the SDK return to you via this callback all logs that are to be printed.

| Param | DESC |
| --- | --- |
| level | Log level. For more information, please see TRTC_LOG_LEVEL. |
| log | Log content |
| module | Reserved field, which is not defined at the moment and has a fixed value of ` TXLiteAVSDK `. |


---
*Source: [https://trtc.io/document/50771](https://trtc.io/document/50771)*
