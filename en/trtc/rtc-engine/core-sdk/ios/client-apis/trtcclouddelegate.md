# TRTCCloudDelegate

Copyright (c) 2021 Tencent. All rights reserved.

Module:   TRTCCloudDelegate @ TXLiteAVSDK

Function: event callback APIs for TRTCâs video call feature

**TRTCCloudDelegate**

## TRTCCloudDelegate

| FuncList | DESC |
| --- | --- |
| [onError:errMsg:extInfo:](https://www.tencentcloud.com/document/product/647/50755#98036f82055fc2396135d65f53b5352e) | Error event callback. |
| [onWarning:warningMsg:extInfo:](https://www.tencentcloud.com/document/product/647/50755#d5e4b51436cb24c1729e800ba4e14fc7) | Warning event callback. |
| [onEnterRoom:](https://www.tencentcloud.com/document/product/647/50755#1301efa2e0717a4563b73173dc0c6e57) | Whether room entry is successful. |
| [onExitRoom:](https://www.tencentcloud.com/document/product/647/50755#95c38564f6c910cbb33746046da9cb8d) | Room exit. |
| [onSwitchRole:errMsg:](https://www.tencentcloud.com/document/product/647/50755#ac3151ae1495107f0e7f03f0d9542bc1) | Role switching. |
| [onSwitchRoom:errMsg:](https://www.tencentcloud.com/document/product/647/50755#999e808efabcd529554d107b1c6cd87b) | Result of room switching. |
| [onConnectOtherRoom:errCode:errMsg:](https://www.tencentcloud.com/document/product/647/50755#b18062a114b045be21872948fdf4dbad) | Result of requesting cross-room call. |
| [onDisconnectOtherRoom:errMsg:](https://www.tencentcloud.com/document/product/647/50755#5abe6df6e800adb198a270f3562718ce) | Result of ending cross-room call. |
| [onUpdateOtherRoomForwardMode:errMsg:](https://www.tencentcloud.com/document/product/647/50755#b1dd7c7bc5eea79931e0b8c67f055832) | Result of changing the upstream capability of the cross-room anchor. |
| [onRemoteUserEnterRoom:](https://www.tencentcloud.com/document/product/647/50755#1b20627cfd00c47657937af805b0900f) | A user entered the room. |
| [onRemoteUserLeaveRoom:reason:](https://www.tencentcloud.com/document/product/647/50755#a4a563fa63b76a6766dbe18b93deb3e7) | A user exited the room. |
| [onUserVideoAvailable:available:](https://www.tencentcloud.com/document/product/647/50755#36daf607f51a906ea0b48b33fc628161) | A remote user published/unpublished primary stream video. |
| [onUserSubStreamAvailable:available:](https://www.tencentcloud.com/document/product/647/50755#9d1c0a62bea15ec5f15dc77ee36b1232) | A remote user published/unpublished substream video. |
| [onUserAudioAvailable:available:](https://www.tencentcloud.com/document/product/647/50755#e9535d2e80eb01b4d671dcbd7dfa8c8f) | A remote user published/unpublished audio. |
| [onFirstVideoFrame:streamType:width:height:](https://www.tencentcloud.com/document/product/647/50755#0494183885d1acf579b02e489b9e6607) | The SDK started rendering the first video frame of the local or a remote user. |
| [onFirstAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#9c1883e6345f04c763b250d62492bde2) | The SDK started playing the first audio frame of a remote user. |
| [onSendFirstLocalVideoFrame:](https://www.tencentcloud.com/document/product/647/50755#122082d120990a140caf688151fa4c20) | The first local video frame was published. |
| [onSendFirstLocalAudioFrame](https://www.tencentcloud.com/document/product/647/50755#1ae310a244fab10309eb56dd6a4ea9ef) | The first local audio frame was published. |
| [onRemoteVideoStatusUpdated:streamType:streamStatus:reason:extrainfo:](https://www.tencentcloud.com/document/product/647/50755#3fc14b1f61ac5181ba409680253a94ac) | Change of remote video status. |
| [onRemoteAudioStatusUpdated:streamStatus:reason:extrainfo:](https://www.tencentcloud.com/document/product/647/50755#14a1af9bc033da63cf962cb3fcf9ce3f) | Change of remote audio status. |
| [onUserVideoSizeChanged:streamType:newWidth:newHeight:](https://www.tencentcloud.com/document/product/647/50755#3fe3a5372766f8f7fc20f7f2832da274) | Change of remote video size. |
| [onNetworkQuality:remoteQuality:](https://www.tencentcloud.com/document/product/647/50755#bed8fae237b70d2eb41ef79fcd80cc39) | Real-time network quality statistics. |
| [onStatistics:](https://www.tencentcloud.com/document/product/647/50755#93a0b2ea899a43e082cf11a8f1f156b1) | Real-time statistics on technical metrics. |
| [onSpeedTestResult:](https://www.tencentcloud.com/document/product/647/50755#c7e95e341056e89e96ca3ee422a64fbb) | Callback of network speed test. |
| [onConnectionLost](https://www.tencentcloud.com/document/product/647/50755#02f8b3e9b8f7e4c2880664873a5e5ebf) | The SDK was disconnected from the cloud. |
| [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50755#4adcb84c3609b674d8fa21c85afe3822) | The SDK is reconnecting to the cloud. |
| [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50755#531b03dfa5421c4cf58840304294c4e1) | The SDK is reconnected to the cloud. |
| [onCameraDidReady](https://www.tencentcloud.com/document/product/647/50755#ec5a558dd75524fad4cd432fa67fed42) | The camera is ready. |
| [onMicDidReady](https://www.tencentcloud.com/document/product/647/50755#4b77128c829032d35c7a0aa00b079e67) | The mic is ready. |
| [onAudioRouteChanged:fromRoute:](https://www.tencentcloud.com/document/product/647/50755#a9a145e262beb35b8e9185df3a4e67b0) | The audio route changed (for mobile devices only). |
| [onUserVoiceVolume:totalVolume:](https://www.tencentcloud.com/document/product/647/50755#c28a692ba631a72b910e17b042d6f293) | Volume. |
| [onDevice:type:stateChanged:](https://www.tencentcloud.com/document/product/647/50755#6d014ddf887fb42b6b1bcb09c421ac77) | The status of a local device changed (for desktop OS only). |
| [onAudioDeviceCaptureVolumeChanged:muted:](https://www.tencentcloud.com/document/product/647/50755#de2fa988c26d3d9a9cc2567ef876920e) | The capturing volume of the mic changed. |
| [onAudioDevicePlayoutVolumeChanged:muted:](https://www.tencentcloud.com/document/product/647/50755#6f2d12e81ddcdba1fb0d2fc2d59ff17d) | The playback volume changed. |
| [onSystemAudioLoopbackError:](https://www.tencentcloud.com/document/product/647/50755#fd5d382c0ddacab5a7d80671cbf1832d) | Whether system audio capturing is enabled successfully (for desktop OS only). |
| [onRecvCustomCmdMsgUserId:cmdID:seq:message:](https://www.tencentcloud.com/document/product/647/50755#667629e70997daf22ff61a07545c66b4) | Receipt of custom message. |
| [onMissCustomCmdMsgUserId:cmdID:errCode:missed:](https://www.tencentcloud.com/document/product/647/50755#6b1a0dd8786abac4e6a9c313a570cf11) | Loss of custom message. |
| [onRecvSEIMsg:message:](https://www.tencentcloud.com/document/product/647/50755#ca85eadea7896e29f377476dc2827dc9) | Receipt of SEI message. |
| [onStartPublishing:errMsg:](https://www.tencentcloud.com/document/product/647/50755#17672fd0fbc3c4d85470d3464ae8ff5a) | Started publishing to Tencent Cloud CSS CDN. |
| [onStopPublishing:errMsg:](https://www.tencentcloud.com/document/product/647/50755#197b5d3744d2c49a1e2777c454eabb21) | Stopped publishing to Tencent Cloud CSS CDN. |
| [onStartPublishCDNStream:errMsg:](https://www.tencentcloud.com/document/product/647/50755#10dac4ffc70848883357a40d4595f387) | Started publishing to non-Tencent Cloudâs live streaming CDN. |
| [onStopPublishCDNStream:errMsg:](https://www.tencentcloud.com/document/product/647/50755#a02ff3be93fe002dd85e24f6d526ef0b) | Stopped publishing to non-Tencent Cloudâs live streaming CDN. |
| [onSetMixTranscodingConfig:errMsg:](https://www.tencentcloud.com/document/product/647/50755#ae934629ed64d447aae708d44d21380f) | Set the layout and transcoding parameters for On-Cloud MixTranscoding. |
| [onStartPublishMediaStream:code:message:extraInfo:](https://www.tencentcloud.com/document/product/647/50755#7793cc61deebd412cb1f1b8c4762cb3e) | Callback for starting to publish. |
| [onUpdatePublishMediaStream:code:message:extraInfo:](https://www.tencentcloud.com/document/product/647/50755#f346d805a3514f0e4d64b3833124645e) | Callback for modifying publishing parameters. |
| [onStopPublishMediaStream:code:message:extraInfo:](https://www.tencentcloud.com/document/product/647/50755#a21c1d4f01b00f2e6a01ea1975358902) | Callback for stopping publishing. |
| [onCdnStreamStateChanged:status:code:msg:extraInfo:](https://www.tencentcloud.com/document/product/647/50755#6d9f289cca801ada27b66f274d855223) | Callback for change of RTMP/RTMPS publishing status. |
| [onScreenCaptureStarted](https://www.tencentcloud.com/document/product/647/50755#f8f5dcda1fa11da88aacd50e441ba279) | Screen sharing started. |
| [onScreenCapturePaused:](https://www.tencentcloud.com/document/product/647/50755#bda29151f45073c1d972b8236b301a49) | Screen sharing was paused. |
| [onScreenCaptureResumed:](https://www.tencentcloud.com/document/product/647/50755#c2c14200a63c8dcbf69c691738deca8d) | Screen sharing was resumed. |
| [onScreenCaptureStoped:](https://www.tencentcloud.com/document/product/647/50755#13c882d11cf67b8b87b6387b7da7741c) | Screen sharing stopped. |
| [onLocalRecordBegin:storagePath:](https://www.tencentcloud.com/document/product/647/50755#4ec87a51e74a97ee8e58fea261081bb0) | Local recording started. |
| [onLocalRecording:storagePath:](https://www.tencentcloud.com/document/product/647/50755#c41ae5ce2e56dc0c63718ebc8963bb85) | Local media is being recorded. |
| [onLocalRecordFragment:](https://www.tencentcloud.com/document/product/647/50755#7c3216a760663566d5a04c620a153afa) | Record fragment finished. |
| [onLocalRecordComplete:storagePath:](https://www.tencentcloud.com/document/product/647/50755#d1f747d79e07579f09a0e2358399321e) | Local recording stopped. |
| [onUserEnter:](https://www.tencentcloud.com/document/product/647/50755#a92c91b0ff3b5baa530f08e8d5dad494) | An anchor entered the room (disused). |
| [onUserExit:reason:](https://www.tencentcloud.com/document/product/647/50755#f6cb1c4f996bfe8565865f68e8f66a4e) | An anchor left the room (disused). |
| [onAudioEffectFinished:code:](https://www.tencentcloud.com/document/product/647/50755#a46a76f2cf33b96a7d5e25725d828e5f) | Audio effects ended (disused). |

## TRTCVideoRenderDelegate

| FuncList | DESC |
| --- | --- |
| [onRenderVideoFrame:userId:streamType:](https://www.tencentcloud.com/document/product/647/50755#2554116174a810d42ab22ec89eb5c0ac) | Custom video rendering. |

## TRTCVideoFrameDelegate

| FuncList | DESC |
| --- | --- |
| [onGLContextCreated](https://www.tencentcloud.com/document/product/647/50755#e8f3ba7f5571f4974658a599c50787ec) | An OpenGL context was created in the SDK. |
| [onProcessVideoFrame:dstFrame:](https://www.tencentcloud.com/document/product/647/50755#b8d844b62eb629ec92eeb49f31ce7d14) | Video processing by third-party beauty filters. |
| [onGLContextDestory](https://www.tencentcloud.com/document/product/647/50755#1887ebbbea32eba8584032e3e40f4d68) | The OpenGL context in the SDK was destroyed. |

## TRTCAudioFrameDelegate

| FuncList | DESC |
| --- | --- |
| [onCapturedAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#da380be77fec333b97a6955b2d33b496) | Audio data captured by the local mic and pre-processed by the audio module. |
| [onLocalProcessedAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#4e466d2653ea24dd48f363dd82c85110) | Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed. |
| [onRemoteUserAudioFrame:userId:](https://www.tencentcloud.com/document/product/647/50755#7373aa620f0c23297ec72825c1d4f79a) | Audio data of each remote user before audio mixing. |
| [onMixedPlayAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#4c17d629cda95c9a635cceffa1bf28fd) | Data mixed from each channel before being submitted to the system for playback. |
| [onMixedAllAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#c0a618f0068e7cd9f922bcc43d9e940a) | Data mixed from all the captured and to-be-played audio in the SDK. |
| [onVoiceEarMonitorAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#eb7453a97f1bffad68271c27fffbd167) | In-ear monitoring data. |

## TRTCLogDelegate

| FuncList | DESC |
| --- | --- |
| [onLog:LogLevel:WhichModule:](https://www.tencentcloud.com/document/product/647/50755#0a6cc600612002ebc150de8f563777c9) | Printing of local log. |

## onError:errMsg:extInfo:

**onError:errMsg:extInfo:**

| - (void)onError: | (TXLiteAVError)errCode |
| --- | --- |
| errMsg: | (nullable NSString *)errMsg |
| extInfo: | (nullable NSDictionary*)extInfo |

**Error event callback.**

Error event, which indicates that the SDK threw an irrecoverable error such as room entry failure or failure to start device

For more information, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| errCode | Error code |
| errMsg | Error message |
| extInfo | Extended field. Certain error codes may carry extra information for troubleshooting. |

## onWarning:warningMsg:extInfo:

**onWarning:warningMsg:extInfo:**

| - (void)onWarning: | (TXLiteAVWarning)warningCode |
| --- | --- |
| warningMsg: | (nullable NSString *)warningMsg |
| extInfo: | (nullable NSDictionary*)extInfo |

**Warning event callback.**

Warning event, which indicates that the SDK threw an error requiring attention, such as video lag or high CPU usage

For more information, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| extInfo | Extended field. Certain warning codes may carry extra information for troubleshooting. |
| warningCode | Warning code |
| warningMsg | Warning message |

## onEnterRoom:

**onEnterRoom:**

| - (void)onEnterRoom: | (NSInteger)result |
| --- | --- |

**Whether room entry is successful.**

After calling the [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) API in ` TRTCCloud ` to enter a room, you will receive the ` onEnterRoom(result) ` callback from ` TRTCCloudDelegate `.

- If room entry succeeded, ` result ` will be a positive number (` result ` > 0), indicating the time in milliseconds (ms) the room entry takes.
- If room entry failed, ` result ` will be a negative number (result < 0), indicating the error code for the failure.

For more information on the error codes for room entry failure, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| result | If ` result ` is greater than 0, it indicates the time (in ms) the room entry takes; if ` result ` is less than 0, it represents the error code for room entry. |

> **Note**1. In TRTC versions below 6.6, the ` onEnterRoom(result) ` callback is returned only if room entry succeeds, and the [onError](https://www.tencentcloud.com/document/product/647/50755#98036f82055fc2396135d65f53b5352e) callback is returned if room entry fails.2. In TRTC 6.6 and above, the ` onEnterRoom(result) ` callback is returned regardless of whether room entry succeeds or fails, and the [onError](https://www.tencentcloud.com/document/product/647/50755#98036f82055fc2396135d65f53b5352e) callback is also returned if room entry fails.

## onExitRoom:

**onExitRoom:**

| - (void)onExitRoom: | (NSInteger)reason |
| --- | --- |

**Room exit.**

Calling the [exitRoom](https://www.tencentcloud.com/document/product/647/50754#812a3ac0ad44e274ef4c9213ab0d4a54) API in ` TRTCCloud ` will trigger the execution of room exit-related logic, such as releasing resources of audio/video devices and codecs.

After all resources occupied by the SDK are released, the SDK will return the ` onExitRoom() ` callback.

If you need to call [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) again or switch to another audio/video SDK, please wait until you receive the ` onExitRoom() ` callback.

Otherwise, you may encounter problems such as the camera or mic being occupied.

| Param | DESC |
| --- | --- |
| reason | Reason for room exit. ` 0 `: the user called ` exitRoom ` to exit the room; ` 1 `: the user was removed from the room by the server; ` 2 `: the room was dismissed; ` 3 `: the server status was abnormal. |

## onSwitchRole:errMsg:

**onSwitchRole:errMsg:**

| - (void)onSwitchRole: | (TXLiteAVError)errCode |
| --- | --- |
| errMsg: | (nullable NSString *)errMsg |

**Role switching.**

You can call the [switchRole](https://www.tencentcloud.com/document/product/647/50754#fd719f2e52ce49aea7a6c3796ed582cd) API in ` TRTCCloud ` to switch between the anchor and audience roles. This is accompanied by a line switching process.

After the switching, the SDK will return the ` onSwitchRole() ` event callback.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates a successful switch. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onSwitchRoom:errMsg:

**onSwitchRoom:errMsg:**

| - (void)onSwitchRoom: | (TXLiteAVError)errCode |
| --- | --- |
| errMsg: | (nullable NSString *)errMsg |

**Result of room switching.**

You can call the [switchRoom](https://www.tencentcloud.com/document/product/647/50754#10ebaed6c26e9f5d83938499b9f6be71) API in ` TRTCCloud ` to switch from one room to another.

After the switching, the SDK will return the ` onSwitchRoom() ` event callback.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates a successful switch. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35124). |
| errMsg | Error message |

## onConnectOtherRoom:errCode:errMsg:

**onConnectOtherRoom:errCode:errMsg:**

| - (void)onConnectOtherRoom: | (NSString*)userId |
| --- | --- |
| errCode: | (TXLiteAVError)errCode |
| errMsg: | (nullable NSString *)errMsg |

**Result of requesting cross-room call.**

You can call the [connectOtherRoom](https://www.tencentcloud.com/document/product/647/50755#5abe6df6e800adb198a270f3562718ce) API in ` TRTCCloud ` to establish a video call with the anchor of another room. This is the âanchor competitionâ feature.

The caller will receive the ` onConnectOtherRoom() ` callback, which can be used to determine whether the cross-room call is successful.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that cross-room connection is established successfully. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |
| userId | The user ID of the anchor (in another room) to be called |

## onDisconnectOtherRoom:errMsg:

**onDisconnectOtherRoom:errMsg:**

| - (void)onDisconnectOtherRoom: | (TXLiteAVError)errCode |
| --- | --- |
| errMsg: | (nullable NSString *)errMsg |

**Result of ending cross-room call.**

You can call the disConnectOtherRoom API in ` TRTCCloud ` to end a video call with the anchor of another room. This is the âanchor competitionâ feature.

The caller will receive the ` onDisconnectOtherRoom() ` callback to determine whether the cross-room call has been successfully disconnected.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that the cross-room call has been successfully disconnected. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onUpdateOtherRoomForwardMode:errMsg:

**onUpdateOtherRoomForwardMode:errMsg:**

| - (void)onUpdateOtherRoomForwardMode: | (TXLiteAVError)errCode |
| --- | --- |
| errMsg: | (nullable NSString *)errMsg |

**Result of changing the upstream capability of the cross-room anchor.**

You can call the [updateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50754#a02fd6197c5d4a240becc4c8349c2f9c) API in ` TRTCCloud ` to limit the upstream capability of the cross-room anchor in the current room, and prohibit or allow the cross-room anchor to publish audio/video/sub-stream. This behavior will affect all users in the room.

The caller will receive the ` onUpdateOtherRoomForwardMode() ` callback to determine whether the changing upstream capability of the cross-room anchor is successful.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that upstream capability of the cross-room anchor is changed successfully. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onRemoteUserEnterRoom:

**onRemoteUserEnterRoom:**

| - (void)onRemoteUserEnterRoom: | (NSString *)userId |
| --- | --- |

**A user entered the room.**

Due to performance concerns, this callback works differently in different scenarios (i.e., ` AppScene `, which you can specify by setting the second parameter when calling [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689)).

- Live streaming scenarios ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)): in live streaming scenarios, a user is either in the role of an anchor or audience. The callback is returned only when an anchor enters the room.
- Call scenarios ([TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)): in call scenarios, the concept of roles does not apply (all users can be considered as anchors), and the callback is returned when any user enters the room.

| Param | DESC |
| --- | --- |
| userId | User ID of the remote user |

> **Note**1. The ` onRemoteUserEnterRoom ` callback indicates that a user entered the room, but it does not necessarily mean that the user enabled audio or video.2. If you want to know whether a user enabled video, we recommend you use the [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/50755#36daf607f51a906ea0b48b33fc628161) callback.

## onRemoteUserLeaveRoom:reason:

**onRemoteUserLeaveRoom:reason:**

| - (void)onRemoteUserLeaveRoom: | (NSString *)userId |
| --- | --- |
| reason: | (NSInteger)reason |

**A user exited the room.**

As with [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/50755#1b20627cfd00c47657937af805b0900f), this callback works differently in different scenarios (i.e., ` AppScene `, which you can specify by setting the second parameter when calling [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689)).

- Live streaming scenarios ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)): the callback is triggered only when an anchor exits the room.
- Call scenarios ([TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)): in call scenarios, the concept of roles does not apply, and the callback is returned when any user exits the room.

| Param | DESC |
| --- | --- |
| reason | Reason for room exit. ` 0 `: the user exited the room voluntarily; ` 1 `: the user exited the room due to timeout; ` 2 `: the user was removed from the room; ` 3 `: the anchor user exited the room due to switch to audience. |
| userId | User ID of the remote user |

## onUserVideoAvailable:available:

**onUserVideoAvailable:available:**

| - (void)onUserVideoAvailable: | (NSString *)userId |
| --- | --- |
| available: | (BOOL)available |

**A remote user published/unpublished primary stream video.**

The primary stream is usually used for camera images. If you receive the ` onUserVideoAvailable(userId, YES) ` callback, it indicates that the user has available primary stream video.

You can then call [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) to subscribe to the remote userâs video. If the subscription is successful, you will receive the ` onFirstVideoFrame(userid) ` callback, which indicates that the first video frame of the user is rendered.

If you receive the ` onUserVideoAvailable(userId, NO) ` callback, it indicates that the video of the remote user is disabled, which may be because the user called [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50754#dd2e6e6669e44947ac869fa038462588) or [stopLocalPreview](https://www.tencentcloud.com/document/product/647/50754#39a28f132a6e183cb05d4ffd15fec991).

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) primary stream video. ` YES `: published; ` NO `: unpublished |
| userId | User ID of the remote user |

## onUserSubStreamAvailable:available:

**onUserSubStreamAvailable:available:**

| - (void)onUserSubStreamAvailable: | (NSString *)userId |
| --- | --- |
| available: | (BOOL)available |

**A remote user published/unpublished substream video.**

The substream is usually used for screen sharing images. If you receive the ` onUserSubStreamAvailable(userId, YES) ` callback, it indicates that the user has available substream video.

You can then call [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) to subscribe to the remote userâs video. If the subscription is successful, you will receive the ` onFirstVideoFrame(userid) ` callback, which indicates that the first frame of the user is rendered.

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) substream video. ` YES `: published; ` NO `: unpublished |
| userId | User ID of the remote user |

> **Note**The API used to display substream images is [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3), not startRemoteSubStreamView, startRemoteSubStreamView is deprecated.

## onUserAudioAvailable:available:

**onUserAudioAvailable:available:**

| - (void)onUserAudioAvailable: | (NSString *)userId |
| --- | --- |
| available: | (BOOL)available |

**A remote user published/unpublished audio.**

If you receive the ` onUserAudioAvailable(userId, YES) ` callback, it indicates that the user published audio.

- In auto-subscription mode, the SDK will play the userâs audio automatically.
- In manual subscription mode, you can call [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/50754#323bb92ad3d884c6c01d9842e3e350a3)(userid, NO) to play the userâs audio.

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) audio. ` YES `: published; ` NO `: unpublished |
| userId | User ID of the remote user |

> **Note**The auto-subscription mode is used by default. You can switch to the manual subscription mode by calling [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/50754#b2a93b2135b0d8a1a91bd2770b761fb1), but it must be called before room entry for the switch to take effect.

## onFirstVideoFrame:streamType:width:height:

**onFirstVideoFrame:streamType:width:height:**

| - (void)onFirstVideoFrame: | (NSString*)userId |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| width: | (int)width |
| height: | (int)height |

**The SDK started rendering the first video frame of the local or a remote user.**

The SDK returns this event callback when it starts rendering your first video frame or that of a remote user. The ` userId ` in the callback can help you determine whether the frame is yours or a remote userâs.

- If ` userId ` is empty, it indicates that the SDK has started rendering your first video frame. The precondition is that you have called [startLocalPreview](https://www.tencentcloud.com/document/product/647/50754#95dba5aea272e22271bc4602cd5c99fa) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194).
- If ` userId ` is not empty, it indicates that the SDK has started rendering the first video frame of a remote user. The precondition is that you have called [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) to subscribe to the userâs video.

| Param | DESC |
| --- | --- |
| height | Video height |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | The user ID of the local or a remote user. If it is empty, it indicates that the first local video frame is available; if it is not empty, it indicates that the first video frame of a remote user is available. |
| width | Video width |

> **Note**1. The callback of the first local video frame being rendered is triggered only after you call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50754#95dba5aea272e22271bc4602cd5c99fa) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194).2. The callback of the first video frame of a remote user being rendered is triggered only after you call [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) or startRemoteSubStreamView.

## onFirstAudioFrame:

**onFirstAudioFrame:**

| - (void)onFirstAudioFrame: | (NSString*)userId |
| --- | --- |

**The SDK started playing the first audio frame of a remote user.**

The SDK returns this callback when it plays the first audio frame of a remote user. The callback is not returned for the playing of the first audio frame of the local user.

| Param | DESC |
| --- | --- |
| userId | User ID of the remote user |

## onSendFirstLocalVideoFrame:

**onSendFirstLocalVideoFrame:**

| - (void)onSendFirstLocalVideoFrame: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| --- | --- |

**The first local video frame was published.**

After you enter a room and call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50754#95dba5aea272e22271bc4602cd5c99fa) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194) to enable local video capturing (whichever happens first),

the SDK will start video encoding and publish the local video data via its network module to the cloud.

It returns the ` onSendFirstLocalVideoFrame ` callback after publishing the first local video frame.

| Param | DESC |
| --- | --- |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |

## onSendFirstLocalAudioFrame

**onSendFirstLocalAudioFrame**

**The first local audio frame was published.**

After you enter a room and call [startLocalAudio](https://www.tencentcloud.com/document/product/647/50754#df3c633d8a6277d5271813f9fac58cb9) to enable audio capturing (whichever happens first),

the SDK will start audio encoding and publish the local audio data via its network module to the cloud.

The SDK returns the ` onSendFirstLocalAudioFrame ` callback after sending the first local audio frame.

## onRemoteVideoStatusUpdated:streamType:streamStatus:reason:extrainfo:

**onRemoteVideoStatusUpdated:streamType:streamStatus:reason:extrainfo:**

| - (void)onRemoteVideoStatusUpdated: | (NSString *)userId |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| streamStatus: | ([TRTCAVStatusType](https://www.tencentcloud.com/document/product/647/50760#8ff0fad63c24db1b35490152f56d5bb3))status |
| reason: | ([TRTCAVStatusChangeReason](https://www.tencentcloud.com/document/product/647/50760#37616803ec0eec21697bb3c20f20ca0d))reason |
| extrainfo: | (nullable NSDictionary *)extrainfo |

**Change of remote video status.**

You can use this callback to get the status (` Playing `, ` Loading `, or ` Stopped `) of the video of each remote user and display it on the UI.

| Param | DESC |
| --- | --- |
| extraInfo | Extra information |
| reason | Reason for the change of status |
| status | Video status, which may be ` Playing `, ` Loading `, or ` Stopped ` |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | User ID |

## onRemoteAudioStatusUpdated:streamStatus:reason:extrainfo:

**onRemoteAudioStatusUpdated:streamStatus:reason:extrainfo:**

| - (void)onRemoteAudioStatusUpdated: | (NSString *)userId |
| --- | --- |
| streamStatus: | ([TRTCAVStatusType](https://www.tencentcloud.com/document/product/647/50760#8ff0fad63c24db1b35490152f56d5bb3))status |
| reason: | ([TRTCAVStatusChangeReason](https://www.tencentcloud.com/document/product/647/50760#37616803ec0eec21697bb3c20f20ca0d))reason |
| extrainfo: | (nullable NSDictionary *)extrainfo |

**Change of remote audio status.**

You can use this callback to get the status (` Playing `, ` Loading `, or ` Stopped `) of the audio of each remote user and display it on the UI.

| Param | DESC |
| --- | --- |
| extraInfo | Extra information |
| reason | Reason for the change of status |
| status | Audio status, which may be ` Playing `, ` Loading `, or ` Stopped ` |
| userId | User ID |

## onUserVideoSizeChanged:streamType:newWidth:newHeight:

**onUserVideoSizeChanged:streamType:newWidth:newHeight:**

| - (void)onUserVideoSizeChanged: | (NSString *)userId |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| newWidth: | (int)newWidth |
| newHeight: | (int)newHeight |

**Change of remote video size.**

If you receive the ` onUserVideoSizeChanged(userId, streamType, newWidth, newHeight) ` callback, it indicates that the user changed the video size. It may be triggered by [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50754#2add5add2f68df49f042ff400571ae48) or [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50754#8b9ac12176384adfb56850af375ece28).

| Param | DESC |
| --- | --- |
| newHeight | Video height |
| newWidth | Video width |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | User ID |

## onNetworkQuality:remoteQuality:

**onNetworkQuality:remoteQuality:**

| - (void)onNetworkQuality: | ([TRTCQualityInfo](https://www.tencentcloud.com/document/product/647/50760#008511ed00730a2ef603fd62f64ca33c)*)localQuality |
| --- | --- |
| remoteQuality: | (NSArray<[TRTCQualityInfo](https://www.tencentcloud.com/document/product/647/50760#008511ed00730a2ef603fd62f64ca33c)*>*)remoteQuality |

**Real-time network quality statistics.**

This callback is returned every 2 seconds and notifies you of the upstream and downstream network quality detected by the SDK.

The SDK uses a built-in proprietary algorithm to assess the current latency, bandwidth, and stability of the network and returns a result.

If the result is ` 1 ` (excellent), it means that the current network conditions are excellent; if it is ` 6 ` (down), it means that the current network conditions are too bad to support TRTC calls.

| Param | DESC |
| --- | --- |
| localQuality | Upstream network quality |
| remoteQuality | Downstream network quality, it refers to the data quality finally measured on the local side after the data flow passes through a complete transmission link of "remote ->cloud ->local". Therefore, the downlink network quality here represents the joint impact of the remote uplink and the local downlink. |

> **Note**The uplink quality of remote users cannot be determined independently through this interface.

## onStatistics:

**onStatistics:**

| - (void)onStatistics: | ([TRTCStatistics](https://www.tencentcloud.com/document/product/647/50756#1d6d431e74a86078f2fd05bf4f3efb7a) *)statistics |
| --- | --- |

**Real-time statistics on technical metrics.**

This callback is returned every 2 seconds and notifies you of the statistics on technical metrics related to video, audio, and network. The metrics are listed in [TRTCStatistics](https://www.tencentcloud.com/document/product/647/50756#1d6d431e74a86078f2fd05bf4f3efb7a):

- Video statistics: video resolution (` resolution `), frame rate (` FPS `), bitrate (` bitrate `), etc.
- Audio statistics: audio sample rate (` samplerate `), number of audio channels (` channel `), bitrate (` bitrate `), etc.
- Network statistics: the round trip time (` rtt `) between the SDK and the cloud (SDK -> Cloud -> SDK), package loss rate (` loss `), upstream traffic (` sentBytes `), downstream traffic (` receivedBytes `), etc.

| Param | DESC |
| --- | --- |
| statistics | Statistics, including local statistics and the statistics of remote users. For details, please see [TRTCStatistics](https://www.tencentcloud.com/document/product/647/50756#1d6d431e74a86078f2fd05bf4f3efb7a). |

> **Note**If you want to learn about only the current network quality and do not want to spend much time analyzing the statistics returned by this callback, we recommend you use [onNetworkQuality](https://www.tencentcloud.com/document/product/647/50755#bed8fae237b70d2eb41ef79fcd80cc39).

## onSpeedTestResult:

**onSpeedTestResult:**

| - (void)onSpeedTestResult: | ([TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/50760#25124dd8b486afcaeaabe326bfe10288) *)result |
| --- | --- |

**Callback of network speed test.**

The callback is triggered by [startSpeedTest](https://www.tencentcloud.com/document/product/647/50754#9446ef81737de395b79baa311622f04e).

| Param | DESC |
| --- | --- |
| result | Speed test data, including loss rates, rtt and bandwidth rates, please refer to [TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/50760#25124dd8b486afcaeaabe326bfe10288) for details. |

## onConnectionLost

**onConnectionLost**

**The SDK was disconnected from the cloud.**

The SDK returns this callback when it is disconnected from the cloud, which may be caused by network unavailability or change of network, for example, when the user walks into an elevator.

After returning this callback, the SDK will attempt to reconnect to the cloud, and will return the [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50755#4adcb84c3609b674d8fa21c85afe3822) callback. When it is reconnected, it will return the [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50755#531b03dfa5421c4cf58840304294c4e1) callback.

In other words, the SDK proceeds from one event to the next in the following order:

![](https://qcloudimg.tencent-cloud.cn/raw/fb3c40a4fca55b0010d385cf3b2472cd.png)

## onTryToReconnect

**onTryToReconnect**

**The SDK is reconnecting to the cloud.**

When the SDK is disconnected from the cloud, it returns the [onConnectionLost](https://www.tencentcloud.com/document/product/647/50755#02f8b3e9b8f7e4c2880664873a5e5ebf) callback. It then attempts to reconnect and returns this callback ([onTryToReconnect](https://www.tencentcloud.com/document/product/647/50755#4adcb84c3609b674d8fa21c85afe3822)). After it is reconnected, it returns the [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50755#531b03dfa5421c4cf58840304294c4e1) callback.

## onConnectionRecovery

**onConnectionRecovery**

**The SDK is reconnected to the cloud.**

When the SDK is disconnected from the cloud, it returns the [onConnectionLost](https://www.tencentcloud.com/document/product/647/50755#02f8b3e9b8f7e4c2880664873a5e5ebf) callback. It then attempts to reconnect and returns the [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50755#4adcb84c3609b674d8fa21c85afe3822) callback. After it is reconnected, it returns this callback ([onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50755#531b03dfa5421c4cf58840304294c4e1)).

## onCameraDidReady

**onCameraDidReady**

**The camera is ready.**

After you call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50754#95dba5aea272e22271bc4602cd5c99fa), the SDK will try to start the camera and return this callback if the camera is started.

If it fails to start the camera, itâs probably because the application does not have access to the camera or the camera is being used.

You can capture the [onError](https://www.tencentcloud.com/document/product/647/50755#98036f82055fc2396135d65f53b5352e) callback to learn about the exception and let users know via UI messages.

## onMicDidReady

**onMicDidReady**

**The mic is ready.**

After you call [startLocalAudio](https://www.tencentcloud.com/document/product/647/50754#df3c633d8a6277d5271813f9fac58cb9), the SDK will try to start the mic and return this callback if the mic is started.

If it fails to start the mic, itâs probably because the application does not have access to the mic or the mic is being used.

You can capture the [onError](https://www.tencentcloud.com/document/product/647/50755#98036f82055fc2396135d65f53b5352e) callback to learn about the exception and let users know via UI messages.

## onAudioRouteChanged:fromRoute:

**onAudioRouteChanged:fromRoute:**

| - (void)onAudioRouteChanged: | ([TRTCAudioRoute](https://www.tencentcloud.com/document/product/647/50760#aaca0d57f6f9d9c6a6425485464b0877))route |
| --- | --- |
| fromRoute: | ([TRTCAudioRoute](https://www.tencentcloud.com/document/product/647/50760#aaca0d57f6f9d9c6a6425485464b0877))fromRoute |

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

## onUserVoiceVolume:totalVolume:

**onUserVoiceVolume:totalVolume:**

| - (void)onUserVoiceVolume: | (NSArray<[TRTCVolumeInfo](https://www.tencentcloud.com/document/product/647/50760#6895db8871ff30fc996e931a213e2b0c) *> *)userVolumes |
| --- | --- |
| totalVolume: | (NSInteger)totalVolume |

**Volume.**

The SDK can assess the volume of each channel and return this callback on a regular basis. You can display, for example, a waveform or volume bar on the UI based on the statistics returned.

You need to first call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50754#b8cb5a5ac09c8e46fcdf98f0acb2e792) to enable the feature and set the interval for the callback.

Note that the SDK returns this callback at the specified interval regardless of whether someone is speaking in the room.

| Param | DESC |
| --- | --- |
| totalVolume | The total volume of all remote users. Value range: [0, 100] |
| userVolumes | An array that represents the volume of all users who are speaking in the room. Value range: [0, 100] |

> **Note**` userVolumes ` is an array. If ` userId ` is empty, the elements in the array represent the volume of the local userâs audio. Otherwise, they represent the volume of a remote userâs audio.

## onDevice:type:stateChanged:

**onDevice:type:stateChanged:**

| - (void)onDevice: | (NSString *)deviceId |
| --- | --- |
| type: | (TRTCMediaDeviceType)deviceType |
| stateChanged: | (NSInteger)state |

**The status of a local device changed (for desktop OS only).**

The SDK returns this callback when a local device (camera, mic, or speaker) is connected or disconnected.

| Param | DESC |
| --- | --- |
| deviceId | Device ID |
| deviceType | Device type |
| state | Device status. ` 0 `: disconnected; ` 1 `: connected |

## onAudioDeviceCaptureVolumeChanged:muted:

**onAudioDeviceCaptureVolumeChanged:muted:**

| - (void)onAudioDeviceCaptureVolumeChanged: | (NSInteger)volume |
| --- | --- |
| muted: | (BOOL)muted |

**The capturing volume of the mic changed.**

On desktop OS such as macOS and Windows, users can set the capturing volume of the mic in the audio control panel.

The higher volume a user sets, the higher the volume of raw audio captured by the mic.

On some keyboards and laptops, users can also mute the mic by pressing a key (whose icon is a crossed out mic).

When users set the mic capturing volume via the UI or a keyboard shortcut, the SDK will return this callback.

| Param | DESC |
| --- | --- |
| muted | Whether the mic is muted. ` YES `: muted; ` NO `: unmuted |
| volume | System audio capturing volume, which users can set in the audio control panel. Value range: [0, 100] |

> **Note**You need to call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50754#b8cb5a5ac09c8e46fcdf98f0acb2e792) and set the callback interval (` interval ` > 0) to enable the callback. To disable the callback, set ` interval ` to ` 0 `.

## onAudioDevicePlayoutVolumeChanged:muted:

**onAudioDevicePlayoutVolumeChanged:muted:**

| - (void)onAudioDevicePlayoutVolumeChanged: | (NSInteger)volume |
| --- | --- |
| muted: | (BOOL)muted |

**The playback volume changed.**

On desktop OS such as macOS and Windows, users can set the systemâs playback volume in the audio control panel.

On some keyboards and laptops, users can also mute the speaker by pressing a key (whose icon is a crossed out speaker).

When users set the systemâs playback volume via the UI or a keyboard shortcut, the SDK will return this callback.

| Param | DESC |
| --- | --- |
| muted | Whether the speaker is muted. ` YES `: muted; ` NO `: unmuted |
| volume | The system playback volume, which users can set in the audio control panel. Value range: 0-100 |

> **Note**You need to call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50754#b8cb5a5ac09c8e46fcdf98f0acb2e792) and set the callback interval (` interval ` > 0) to enable the callback. To disable the callback, set ` interval ` to ` 0 `.

## onSystemAudioLoopbackError:

**onSystemAudioLoopbackError:**

| - (void)onSystemAudioLoopbackError: | (TXLiteAVError)err |
| --- | --- |

**Whether system audio capturing is enabled successfully (for desktop OS only).**

On macOS, you can call [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50754#755f9f590bf398deb0c538b32a2aede2) to install an audio driver and have the SDK capture the audio played back by the system.

On Windows systems, you can use [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50754#755f9f590bf398deb0c538b32a2aede2) to have the SDK capture the audio played back by the system.

In use cases such as video teaching and music live streaming, the teacher can use this feature to let the SDK capture the sound of the video played by his or her computer, so that students in the room can hear the sound too.

The SDK returns this callback after trying to enable system audio capturing. To determine whether it is actually enabled, pay attention to the error parameter in the callback.

| Param | DESC |
| --- | --- |
| err | If it is ` ERR_NULL `, system audio capturing is enabled successfully. Otherwise, it is not. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |

## onRecvCustomCmdMsgUserId:cmdID:seq:message:

**onRecvCustomCmdMsgUserId:cmdID:seq:message:**

| - (void)onRecvCustomCmdMsgUserId: | (NSString *)userId |
| --- | --- |
| cmdID: | (NSInteger)cmdID |
| seq: | (UInt32)seq |
| message: | (NSData *)message |

**Receipt of custom message.**

When a user in a room uses [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50754#65a0ef621d0fdc876f649fc8b20ca117) to send a custom message, other users in the room can receive the message through the ` onRecvCustomCmdMsg ` callback.

| Param | DESC |
| --- | --- |
| cmdID | Command ID |
| message | Message data |
| seq | Message serial number |
| userId | User ID |

## onMissCustomCmdMsgUserId:cmdID:errCode:missed:

**onMissCustomCmdMsgUserId:cmdID:errCode:missed:**

| - (void)onMissCustomCmdMsgUserId: | (NSString *)userId |
| --- | --- |
| cmdID: | (NSInteger)cmdID |
| errCode: | (NSInteger)errCode |
| missed: | (NSInteger)missed |

**Loss of custom message.**

When you use [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50754#65a0ef621d0fdc876f649fc8b20ca117) to send a custom UDP message, even if you enable reliable transfer (by setting ` reliable ` to ` YES `), there is still a chance of message loss. Reliable transfer only helps maintain a low probability of message loss, which meets the reliability requirements in most cases.

If the sender sets ` reliable ` to ` YES `, the SDK will use this callback to notify the recipient of the number of custom messages lost during a specified time period (usually 5s) in the past.

| Param | DESC |
| --- | --- |
| cmdID | Command ID |
| errCode | Error code |
| missed | Number of lost messages |
| userId | User ID |

> **Note**The recipient receives this callback only if the sender sets ` reliable ` to ` YES `.

## onRecvSEIMsg:message:

**onRecvSEIMsg:message:**

| - (void)onRecvSEIMsg: | (NSString *)userId |
| --- | --- |
| message: | (NSData*)message |

**Receipt of SEI message.**

If a user in the room uses [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50754#f1c4a686a1e513f8dce8b8d57cc5bbe8) to send an SEI message via video frames, other users in the room can receive the message through the ` onRecvSEIMsg ` callback.

| Param | DESC |
| --- | --- |
| message | Data |
| userId | User ID |

## onStartPublishing:errMsg:

**onStartPublishing:errMsg:**

| - (void)onStartPublishing: | (int)err |
| --- | --- |
| errMsg: | (NSString*)errMsg |

**Started publishing to Tencent Cloud CSS CDN.**

When you call startPublishing to publish streams to Tencent Cloud CSS CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStopPublishing:errMsg:

**onStopPublishing:errMsg:**

| - (void)onStopPublishing: | (int)err |
| --- | --- |
| errMsg: | (NSString*)errMsg |

**Stopped publishing to Tencent Cloud CSS CDN.**

When you call stopPublishing to stop publishing streams to Tencent Cloud CSS CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStartPublishCDNStream:errMsg:

**onStartPublishCDNStream:errMsg:**

| - (void)onStartPublishCDNStream: | (int)err |
| --- | --- |
| errMsg: | (NSString *)errMsg |

**Started publishing to non-Tencent Cloudâs live streaming CDN.**

When you call startPublishCDNStream to start publishing streams to a non-Tencent Cloudâs live streaming CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

> **Note**If you receive a callback that the command is executed successfully, it only means that your command was sent to Tencent Cloudâs backend server. If the CDN vendor does not accept your streams, the publishing will still fail.

## onStopPublishCDNStream:errMsg:

**onStopPublishCDNStream:errMsg:**

| - (void)onStopPublishCDNStream: | (int)err |
| --- | --- |
| errMsg: | (NSString *)errMsg |

**Stopped publishing to non-Tencent Cloudâs live streaming CDN.**

When you call stopPublishCDNStream to stop publishing to a non-Tencent Cloudâs live streaming CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onSetMixTranscodingConfig:errMsg:

**onSetMixTranscodingConfig:errMsg:**

| - (void)onSetMixTranscodingConfig: | (int)err |
| --- | --- |
| errMsg: | (NSString*)errMsg |

**Set the layout and transcoding parameters for On-Cloud MixTranscoding.**

When you call setMixTranscodingConfig to modify the layout and transcoding parameters for On-Cloud MixTranscoding, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStartPublishMediaStream:code:message:extraInfo:

**onStartPublishMediaStream:code:message:extraInfo:**

| - (void)onStartPublishMediaStream: | (NSString*)taskId |
| --- | --- |
| code: | (int)code |
| message: | (NSString*)message |
| extraInfo: | (nullable NSDictionary *)extraInfo |

**Callback for starting to publish.**

When you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e) to publish a stream to the TRTC backend, the SDK will immediately update the command to the cloud server.

The SDK will then receive the publishing result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server failed to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended actions are as follows: 2000: Parameter error. Check the request parameters. 2001: Live streaming service is not enabled. Enable it in the Live streaming console. 2021: Third-party retweet service is not enabled. Contact product support to enable it. 3000: Internal server error. Retry is recommended. 4006: Concurrency conflict with the same task. The server is still processing the previous startPublishMediaStream task. Retry after a delay is recommended. 4007: The same task has already been successfully started using startPublishMediaStream. Use the returned taskId to call the updatePublishMediaStream API to update the task. 5001: Resource constraints. Retry after a delay is recommended. |
| message | : The callback information. |
| taskId | : If a request is successful, a task ID will be returned via the callback. You need to provide this task ID when you call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#fc8a7778d8fc91d7dff4c3801b5e5cfe) to modify publishing parameters or [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e) to stop publishing. |

## onUpdatePublishMediaStream:code:message:extraInfo:

**onUpdatePublishMediaStream:code:message:extraInfo:**

| - (void)onUpdatePublishMediaStream: | (NSString*)taskId |
| --- | --- |
| code: | (int)code |
| message: | (NSString*)message |
| extraInfo: | (nullable NSDictionary *)extraInfo |

**Callback for modifying publishing parameters.**

When you call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#fc8a7778d8fc91d7dff4c3801b5e5cfe) to modify publishing parameters, the SDK will immediately update the command to the cloud server.

The SDK will then receive the modification result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server failed to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended solutions are as follows: 2000: Parameter error. Check the request parameters. 2001: Live streaming service is not enabled. Enable it in the Live Streaming Console. 2002: Task not found. Restart the task by calling the startPublishMediaStream API. 2018: Concurrent requests are out of order. Retry with the latest streaming parameters. 2021: Third-party retweet service is not enabled. Contact product support to enable it. 3000: Internal server error. Retry. 4003: Task is exiting. Stop the task by calling the stopPublishMediaStream API first, then restart it by calling the startPublishMediaStream API. |
| message | : The callback information. |
| taskId | : The task ID you pass in when calling [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#fc8a7778d8fc91d7dff4c3801b5e5cfe), which is used to identify a request. |

## onStopPublishMediaStream:code:message:extraInfo:

**onStopPublishMediaStream:code:message:extraInfo:**

| - (void)onStopPublishMediaStream: | (NSString*)taskId |
| --- | --- |
| code: | (int)code |
| message: | (NSString*)message |
| extraInfo: | (nullable NSDictionary *)extraInfo |

**Callback for stopping publishing.**

When you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e) to stop publishing, the SDK will immediately update the command to the cloud server.

The SDK will then receive the modification result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server was unable to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended actions are as follows: 2000: Parameter error. Please check the request parameters. 2002: Task not found. No action required. 3000: Internal server error. Please retry. 4003: Task is exiting. No action required. |
| message | : The callback information. |
| taskId | : The task ID you pass in when calling [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e), which is used to identify a request. |

## onCdnStreamStateChanged:status:code:msg:extraInfo:

**onCdnStreamStateChanged:status:code:msg:extraInfo:**

| - (void)onCdnStreamStateChanged: | (NSString*)cdnUrl |
| --- | --- |
| status: | (int)status |
| code: | (int)code |
| msg: | (NSString*)msg |
| extraInfo: | (nullable NSDictionary *)info |

**Callback for change of RTMP/RTMPS publishing status.**

When you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e) to publish a stream to the TRTC backend, the SDK will immediately update the command to the cloud server.

If you set the publishing destination ([TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50760#11c06c485af4d4bd3b60bc0c883a9a32)) to the URL of Tencent Cloud or a third-party CDN, you will be notified of the RTMP/RTMPS publishing status via this callback.

| Param | DESC |
| --- | --- |
| cdnUrl | : The URL you specify in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50760#11c06c485af4d4bd3b60bc0c883a9a32) when you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e). |
| code | : The publishing result. ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues. |
| message | : The publishing information. |
| status | : The publishing status. 0: The publishing has not started yet or has ended. This value will be returned after you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e). 1: The TRTC server is connecting to the CDN server. If the first attempt fails, the TRTC backend will retry multiple times and will return this value via the callback (every five seconds). After publishing succeeds, the value ` 2 ` will be returned. If a server error occurs or publishing is still unsuccessful after 60 seconds, the value ` 4 ` will be returned. 2: The TRTC server is publishing to the CDN. This value will be returned if the publishing succeeds. 3: The TRTC server is disconnected from the CDN server and is reconnecting. If a CDN error occurs or publishing is interrupted, the TRTC backend will try to reconnect and resume publishing and will return this value via the callback (every five seconds). After publishing resumes, the value ` 2 ` will be returned. If a server error occurs or the attempt to resume publishing is still unsuccessful after 60 seconds, the value ` 4 ` will be returned. 4: The TRTC server is disconnected from the CDN server and failed to reconnect within the timeout period. In this case, the publishing is deemed to have failed. You can call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#fc8a7778d8fc91d7dff4c3801b5e5cfe) to try again. 5: The TRTC server is disconnecting from the CDN server. After you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e), the SDK will return this value first and then the value ` 0 `. |

## onScreenCaptureStarted

**onScreenCaptureStarted**

**Screen sharing started.**

The SDK returns this callback when you call [startScreenCapture](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194) and other APIs to start screen sharing.

## onScreenCapturePaused:

**onScreenCapturePaused:**

| - (void)onScreenCapturePaused: | (int)reason |
| --- | --- |

**Screen sharing was paused.**

The SDK returns this callback when you call [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/50754#77ba0ef5a41b95cf46da6cd0a539279e) to pause screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user paused screen sharing. ` 1 `: screen sharing was paused because the shared window became invisible(Mac). screen sharing was paused because setting parameters(Windows). ` 2 `: screen sharing was paused because the shared window became minimum(only for Windows). ` 3 `: screen sharing was paused because the shared window became invisible(only for Windows). ` 4 `: screen sharing was paused because the system operation(only for iOS). |

## onScreenCaptureResumed:

**onScreenCaptureResumed:**

| - (void)onScreenCaptureResumed: | (int)reason |
| --- | --- |

**Screen sharing was resumed.**

The SDK returns this callback when you call [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/50754#34bdf61c283c09fd3c12fdab1d07f4c1) to resume screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user resumed screen sharing. ` 1 `: screen sharing was resumed automatically after the shared window became visible again(Mac). screen sharing was resumed automatically after setting parameters(Windows). ` 2 `: screen sharing was resumed automatically after the shared window became minimize recovery(only for Windows). ` 3 `: screen sharing was resumed automatically after the shared window became visible again(only for Windows). ` 4 `: screen sharing was resumed because the system operation(only for iOS). |

## onScreenCaptureStoped:

**onScreenCaptureStoped:**

| - (void)onScreenCaptureStoped: | (int)reason |
| --- | --- |

**Screen sharing stopped.**

The SDK returns this callback when you call [stopScreenCapture](https://www.tencentcloud.com/document/product/647/50754#f07463b8a6a3ee03680356b3fb07364c) to stop screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user stopped screen sharing; ` 1 `: screen sharing stopped because the shared window was closed. |

## onLocalRecordBegin:storagePath:

**onLocalRecordBegin:storagePath:**

| - (void)onLocalRecordBegin: | (NSInteger)errCode |
| --- | --- |
| storagePath: | (NSString *)storagePath |

**Local recording started.**

When you call [startLocalRecording](https://www.tencentcloud.com/document/product/647/50754#622793b0e472c04351886ba0a6826140) to start local recording, the SDK returns this callback to notify you whether recording is started successfully.

| Param | DESC |
| --- | --- |
| errCode | status.  0: successful. -1: failed. -2: unsupported format. -6: recording has been started. Stop recording first. -7: recording file already exists and needs to be deleted. -8: recording directory does not have the write permission. Please check the directory permission. |
| storagePath | Storage path of recording file |

## onLocalRecording:storagePath:

**onLocalRecording:storagePath:**

| - (void)onLocalRecording: | (NSInteger)duration |
| --- | --- |
| storagePath: | (NSString *)storagePath |

**Local media is being recorded.**

The SDK returns this callback regularly after local recording is started successfully via the calling of [startLocalRecording](https://www.tencentcloud.com/document/product/647/50754#622793b0e472c04351886ba0a6826140).

You can capture this callback to stay up to date with the status of the recording task.

You can set the callback interval when calling [startLocalRecording](https://www.tencentcloud.com/document/product/647/50754#622793b0e472c04351886ba0a6826140).

| Param | DESC |
| --- | --- |
| duration | Cumulative duration of recording, in milliseconds |
| storagePath | Storage path of recording file |

## onLocalRecordFragment:

**onLocalRecordFragment:**

| - (void)onLocalRecordFragment: | (NSString *)storagePath |
| --- | --- |

**Record fragment finished.**

When fragment recording is enabled, this callback will be invoked when each fragment file is finished.

| Param | DESC |
| --- | --- |
| storagePath | Storage path of the fragment. |

## onLocalRecordComplete:storagePath:

**onLocalRecordComplete:storagePath:**

| - (void)onLocalRecordComplete: | (NSInteger)errCode |
| --- | --- |
| storagePath: | (NSString *)storagePath |

**Local recording stopped.**

When you call [stopLocalRecording](https://www.tencentcloud.com/document/product/647/50754#4fe2c8c6efe048db10a347ac226bef34) to stop local recording, the SDK returns this callback to notify you of the recording result.

| Param | DESC |
| --- | --- |
| errCode | status  0: successful. -1: failed. -2: Switching resolution or horizontal and vertical screen causes the recording to stop. -3: recording duration is too short or no video or audio data is received. Check the recording duration or whether audio or video capture is enabled. |
| storagePath | Storage path of recording file |

## onUserEnter:

**onUserEnter:**

| - (void)onUserEnter: | (NSString *)userId |
| --- | --- |

**An anchor entered the room (disused).**

@deprecated This callback is not recommended in the new version. Please use [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/50755#1b20627cfd00c47657937af805b0900f) instead.

## onUserExit:reason:

**onUserExit:reason:**

| - (void)onUserExit: | (NSString *)userId |
| --- | --- |
| reason: | (NSInteger)reason |

**An anchor left the room (disused).**

@deprecated This callback is not recommended in the new version. Please use [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/50755#a4a563fa63b76a6766dbe18b93deb3e7) instead.

## onAudioEffectFinished:code:

**onAudioEffectFinished:code:**

| - (void)onAudioEffectFinished: | (int) effectId |
| --- | --- |
| code: | (int) code |

**Audio effects ended (disused).**

@deprecated This callback is not recommended in the new version. Please use [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

Audio effects and background music can be started using the same API ([startPlayMusic](https://www.tencentcloud.com/document/product/647/50757#3e6d92e47d6770c50e0e4ca4df429c31)) now instead of separate ones.

## onRenderVideoFrame:userId:streamType:

**onRenderVideoFrame:userId:streamType:**

| - (void) onRenderVideoFrame: | ([TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50760#9233a1b1573333abc70e53b51bd89740) * _Nonnull)frame |
| --- | --- |
| userId: | (NSString* __nullable)userId |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |

**Custom video rendering.**

If you have configured the callback of custom rendering for local or remote video, the SDK will return to you via this callback video frames that are otherwise sent to the rendering control, so that you can customize rendering.

| Param | DESC |
| --- | --- |
| frame | Video frames to be rendered |
| streamType | Stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | ` userId ` of the video source. This parameter can be ignored if the callback is for local video ([setLocalVideoRenderDelegate](https://www.tencentcloud.com/document/product/647/50754#942d950756d625549380fe112550e0eb)). |

## onGLContextCreated

**onGLContextCreated**

**An OpenGL context was created in the SDK.**

## onProcessVideoFrame:dstFrame:

**onProcessVideoFrame:dstFrame:**

| - (uint32_t)onProcessVideoFrame: | ([TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50760#9233a1b1573333abc70e53b51bd89740) * _Nonnull)srcFrame |
| --- | --- |
| dstFrame: | ([TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50760#9233a1b1573333abc70e53b51bd89740) * _Nonnull)dstFrame |

**Video processing by third-party beauty filters.**

If you use a third-party beauty filter component, you need to configure this callback in ` TRTCCloud ` to have the SDK return to you video frames that are otherwise pre-processed by TRTC.

You can then send the video frames to the third-party beauty filter component for processing. As the data returned can be read and modified, the result of processing can be synced to TRTC for subsequent encoding and publishing.

Case 1: the beauty filter component generates new textures

If the beauty filter component you use generates a frame of new texture (for the processed image) during image processing, please set ` dstFrame.textureId ` to the ID of the new texture in the callback function.

```
uint32_t onProcessVideoFrame(TRTCVideoFrame * _Nonnull)srcFrame dstFrame:(TRTCVideoFrame * _Nonnull)dstFrame{    self.frameID += 1;    dstFrame.pixelBuffer = [[FURenderer shareRenderer] renderPixelBuffer:srcFrame.pixelBuffer                                                             withFrameId:self.frameID                                                                   items:self.renderItems                                                               itemCount:self.renderItems.count];    return 0;}
```

Case 2: you need to provide target textures to the beauty filter component

If the third-party beauty filter component you use does not generate new textures and you need to manually set an input texture and an output texture for the component, you can consider the following scheme:

```
uint32_t onProcessVideoFrame(TRTCVideoFrame * _Nonnull)srcFrame dstFrame:(TRTCVideoFrame * _Nonnull)dstFrame{    thirdparty_process(srcFrame.textureId, srcFrame.width, srcFrame.height, dstFrame.textureId);    return 0;}
```

| Param | DESC |
| --- | --- |
| dstFrame | Used to receive video images processed by third-party beauty filters |
| srcFrame | Used to carry images captured by TRTC via the camera |

> **Note**Currently, only the OpenGL texture scheme is supported(PC supports TRTCVideoBufferType_Buffer format Only)

## onGLContextDestory

**onGLContextDestory**

**The OpenGL context in the SDK was destroyed.**

## onCapturedAudioFrame:

**onCapturedAudioFrame:**

| - (void) onCapturedAudioFrame: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)frame |
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

## onLocalProcessedAudioFrame:

**onLocalProcessedAudioFrame:**

| - (void) onLocalProcessedAudioFrame: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)frame |
| --- | --- |

**Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed.**

After you configure the callback of custom audio processing, the SDK will return via this callback the data captured, pre-processed (ANS, AEC, and AGC), effect-processed and BGM-mixed in PCM format, before it is submitted to the network module for encoding.

- The audio data returned via this callback is in PCM format and has a fixed frame length (time) of 0.02s.
- The formula to convert a frame length in seconds to one in bytes is **sample rate * frame length in seconds * number of sound channels * audio bit depth**.
- Assume that the audio is recorded on a single channel with a sample rate of 48,000 Hz and audio bit depth of 16 bits, which are the default settings of TRTC. The frame length in bytes will be **48000 * 0.02s * 1 * 16 bits = 15360 bits = 1920 bytes**.

Instructions:

You could write data to the ` TRTCAudioFrame.extraData ` filed, in order to achieve the purpose of transmitting signaling.

Because the data block of the audio frame header cannot be too large, we recommend you limit the size of the signaling data to only a few bytes when using this API. If extra data more than 100 bytes, it won't be sent.

Other users in the room can receive the message through the ` TRTCAudioFrame.extraData ` in ` onRemoteUserAudioFrame ` callback in [TRTCAudioFrameDelegate](https://www.tencentcloud.com/document/product/647/50755#da66ef151b799273aa9b22b41bef74a6).

| Param | DESC |
| --- | --- |
| frame | Audio frames in PCM format |

> **Note**1. Please avoid time-consuming operations in this callback function. The SDK processes an audio frame every 20 ms, so if your operation takes more than 20 ms, it will cause audio exceptions.2. The audio data returned via this callback can be read and modified, but please keep the duration of your operation short.3. Audio data is returned via this callback after ANS, AEC, AGC, effect-processing and BGM-mixing, and therefore the delay is longer than that with [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50755#da380be77fec333b97a6955b2d33b496).

## onRemoteUserAudioFrame:userId:

**onRemoteUserAudioFrame:userId:**

| - (void) onRemoteUserAudioFrame: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)frame |
| --- | --- |
| userId: | (NSString *)userId |

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

## onMixedPlayAudioFrame:

**onMixedPlayAudioFrame:**

| - (void) onMixedPlayAudioFrame: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)frame |
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

## onMixedAllAudioFrame:

**onMixedAllAudioFrame:**

| - (void) onMixedAllAudioFrame: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)frame |
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

## onVoiceEarMonitorAudioFrame:

**onVoiceEarMonitorAudioFrame:**

| - (void) onVoiceEarMonitorAudioFrame: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)frame |
| --- | --- |

**In-ear monitoring data.**

After you configure the callback of custom audio processing, the SDK will return to you via this callback the in-ear monitoring data (PCM format) before it is submitted to the system for playback.

- The audio returned is in PCM format and has a not-fixed frame length (time).
- The formula to convert a frame length in seconds to one in bytes is **sample rate * frame length in seconds * number of sound channels * audio bit depth**.
- Assume that the audio is recorded on a single channel with a sample rate of 48,000 Hz and audio bit depth of 16 bits, which are the default settings of TRTC. The length of 0.02s frame in bytes will be **48000 * 0.02s * 1 * 16 bits = 15360 bits = 1920 bytes**.

| Param | DESC |
| --- | --- |
| frame | Audio frames in PCM format |

> **Note**1. Please avoid time-consuming operations in this callback function, or it will cause audio exceptions.2. The audio data returned via this callback can be read and modified, but please keep the duration of your operation short.

## onLog:LogLevel:WhichModule:

**onLog:LogLevel:WhichModule:**

| -(void) onLog: | (nullable NSString*)log |
| --- | --- |
| LogLevel: | ([TRTCLogLevel](https://www.tencentcloud.com/document/product/647/50760#3b7ff44175cba4dd48e97aa8ac7b0b98))level |
| WhichModule: | (nullable NSString*)module |

**Printing of local log.**

If you want to capture the local log printing event, you can configure the log callback to have the SDK return to you via this callback all logs that are to be printed.

| Param | DESC |
| --- | --- |
| level | Log level. For more information, please see TRTC_LOG_LEVEL. |
| log | Log content |
| module | Reserved field, which is not defined at the moment and has a fixed value of ` TXLiteAVSDK `. |


---
*Source: [https://trtc.io/document/50755](https://trtc.io/document/50755)*
