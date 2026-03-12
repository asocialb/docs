# ITRTCCloud

Copyright (c) 2021 Tencent. All rights reserved.

Module:   TRTCCloud @ TXLiteAVSDK

Function: TRTC's main feature API

Version: 12.6

**ITRTCCloud**

## ITRTCCloud

| FuncList | DESC |
| --- | --- |
| [getTRTCShareInstance](https://www.tencentcloud.com/document/product/647/72270#65f8f22625bce741ae1b4f38d62979f5) | Create TRTCCloud instance (singleton mode). |
| [destroyTRTCShareInstance](https://www.tencentcloud.com/document/product/647/72270#a077f03f488af3cc8fefc5978d7f4dd0) | Terminate TRTCCloud instance (singleton mode). |
| [addCallback](https://www.tencentcloud.com/document/product/647/72270#e8ad8b727e6136af5ead580623dd58bf) | Add TRTC event callback. |
| [removeCallback](https://www.tencentcloud.com/document/product/647/72270#a3d2ae539728e319163b9a3364ea2d65) | Remove TRTC event callback. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b) | Enter room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/72270#8e2de8da4b60ce0e19d385897ed77888) | Exit room. |
| [switchRole](https://www.tencentcloud.com/document/product/647/72270#a2f85cd8f74124a8d0ec0c8b34d94b01) | Switch role. |
| [switchRoom](https://www.tencentcloud.com/document/product/647/72270#9f8d51bf4f02a354b060068482db62e8) | Switch room. |
| [connectOtherRoom](https://www.tencentcloud.com/document/product/647/72270#f02d65d741e1ab3431427b94d472d6ac) | Request cross-room call. |
| [disconnectOtherRoom](https://www.tencentcloud.com/document/product/647/72270#b061973682a21bfc056496655ba7e7e8) | Exit cross-room call. |
| [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/72270#f796890d9df3075ba7ce0cfa3b8a77a3) | Set subscription mode (which must be set before room entry for it to take effect). |
| [createSubCloud](https://www.tencentcloud.com/document/product/647/72270#2a6ba6f8c37d0a3453cef09671f8cee2) | Create room subinstance (for concurrent multi-room listen/watch). |
| [destroySubCloud](https://www.tencentcloud.com/document/product/647/72270#5a2d2f205d2590e44e36ec532a3e9260) | Terminate room subinstance. |
| [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4) | Publish a stream. |
| [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#dad88b0322dc59b7e5dbf084b963782e) | Modify publishing parameters. |
| [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#5d9c082fb84a8784246a729663df1ac4) | Stop publishing. |
| [startLocalPreview](https://www.tencentcloud.com/document/product/647/72270#38628a2c12121285b0ab3c24eba211dc) | Enable the preview image of local camera (mobile). |
| [stopLocalPreview](https://www.tencentcloud.com/document/product/647/72270#e379630cda7e794574b00d549b64a815) | Stop camera preview. |
| [muteLocalVideo](https://www.tencentcloud.com/document/product/647/72270#b56b309b0223256eac598cb305d37270) | Pause/Resume publishing local video stream. |
| [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) | Subscribe to remote user's video stream and bind video rendering control. |
| [stopRemoteView](https://www.tencentcloud.com/document/product/647/72270#67277df08ab18e0c02a7d65f7b9a65c4) | Stop subscribing to remote user's video stream and release rendering control. |
| [stopAllRemoteView](https://www.tencentcloud.com/document/product/647/72270#5d9b1929a45db4a7a01d715628e3bbe0) | Stop subscribing to all remote users' video streams and release all rendering resources. |
| [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/72270#e47216c48085fc929661d33cfece2181) | Pause/Resume subscribing to remote user's video stream. |
| [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/72270#d8b35494f4f1d45de0f70ca1f3cbdc15) | Pause/Resume subscribing to all remote users' video streams. |
| [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/72270#944184af05e4175e9458e5b0d563fb68) | Set the encoding parameters of video encoder. |
| [setNetworkQosParam](https://www.tencentcloud.com/document/product/647/72270#a082314a7ac982791d01615b9bd4b9ff) | Set network quality control parameters. |
| [setLocalRenderParams](https://www.tencentcloud.com/document/product/647/72270#89eb94d30d078da58b4e29ab88d0b8a0) | Set the rendering parameters of local video image. |
| [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/72270#80129ddbe95cb5820c30be890d25f299) | Set the rendering mode of remote video image. |
| [enableSmallVideoStream](https://www.tencentcloud.com/document/product/647/72270#0eaec8c2511ebc3aa5b402690bd6f007) | Enable dual-channel encoding mode with big and small images. |
| [setRemoteVideoStreamType](https://www.tencentcloud.com/document/product/647/72270#e68258e11f2b24f72390c6e12a1356f8) | Switch the big/small image of specified remote user. |
| [setGravitySensorAdaptiveMode](https://www.tencentcloud.com/document/product/647/72270#bbb20de90ec72745278e02ec92b2e7c6) | Set the adaptation mode of gravity sensing (version 11.7 and above). |
| [startLocalAudio](https://www.tencentcloud.com/document/product/647/72270#126e2ce82ad449e5aafe277315896806) | Enable local audio capturing and publishing. |
| [stopLocalAudio](https://www.tencentcloud.com/document/product/647/72270#8fafafeb80fe86f9fc0d893c9c35bd4e) | Stop local audio capturing and publishing. |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/72270#00a0d2a0d3979a7edaf3b013f1bedc6a) | Pause/Resume publishing local audio stream. |
| [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/72270#b9f7792974d2df2e3922f2ed1e06ea39) | Pause/Resume playing back remote audio stream. |
| [muteAllRemoteAudio](https://www.tencentcloud.com/document/product/647/72270#c6a3fa5a81dd319bd3e3cdc06176e3d0) | Pause/Resume playing back all remote users' audio streams. |
| [setRemoteAudioVolume](https://www.tencentcloud.com/document/product/647/72270#a4705489d5d338ee436694837813976c) | Set the audio playback volume of remote user. |
| [setAudioCaptureVolume](https://www.tencentcloud.com/document/product/647/72270#8326d139f429c00b542151923d12d579) | Set the capturing volume of local audio. |
| [getAudioCaptureVolume](https://www.tencentcloud.com/document/product/647/72270#2d920084bbca50226a4e23db7178838c) | Get the capturing volume of local audio. |
| [setAudioPlayoutVolume](https://www.tencentcloud.com/document/product/647/72270#43a82fe566327b25f73fcf509ec3fbcc) | Set the playback volume of remote audio. |
| [getAudioPlayoutVolume](https://www.tencentcloud.com/document/product/647/72270#3563829d921079d4da7207263302f8d4) | Get the playback volume of remote audio. |
| [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/72270#e47cf2e48182962b7afde88a8f31fbbd) | Enable volume reminder. |
| [startLocalRecording](https://www.tencentcloud.com/document/product/647/72270#c0358d2dce89b4c19aa824350e2db40d) | Start local media recording. |
| [stopLocalRecording](https://www.tencentcloud.com/document/product/647/72270#a1236129ca8f62c01939c1882f184a88) | Stop local media recording. |
| [getDeviceManager](https://www.tencentcloud.com/document/product/647/72270#3237892a1dc5ad0a46fa7ab04f5e6712) | Get device management class (TXDeviceManager). |
| [setBeautyStyle](https://www.tencentcloud.com/document/product/647/72270#d78703f46f5b1a03720a3f23b9a6fc80) | Set special effects such as beauty, brightening, and rosy skin filters. |
| [setWaterMark](https://www.tencentcloud.com/document/product/647/72270#9c85552e121871f7f2406189851aff0f) | Add watermark. |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/72270#dfd6d9d478ad8ca096bbe41997ab18c3) | Get sound effect management class (TXAudioEffectManager). |
| [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/72270#9c7f414129474867563f4cb57398db05) | Enable system audio capturing(iOS not supported). |
| [stopSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/72270#a542a2b1c0a06558e5ee453811395fca) | Stop system audio capturing(iOS not supported). |
| [startScreenCapture](https://www.tencentcloud.com/document/product/647/72270#62ca4f19707f9c5046ee470b2034ec5d) | Start screen sharing. |
| [stopScreenCapture](https://www.tencentcloud.com/document/product/647/72270#2a667ba75e08183bd5f764374a6de7ba) | Stop screen sharing. |
| [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/72270#d7f9ad7b108c98e919f5f1cca757e72d) | Pause screen sharing. |
| [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/72270#1924263011bb92fba1642ad3e139629f) | Resume screen sharing. |
| [selectScreenCaptureTarget](https://www.tencentcloud.com/document/product/647/72270#ee8657c153c0c55123ca2524fc87b833) | Select the screen or window to share (for desktop systems only). |
| [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72270#b809f30d749d36cfbd2d02d3975af747) | Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems). |
| [enableCustomVideoCapture](https://www.tencentcloud.com/document/product/647/72270#ab16ab952e0fab1102142bf0fd9dc13b) | Enable/Disable custom video capturing mode. |
| [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/72270#8c8378c65a0b11187d6812523706a9f0) | Deliver captured video frames to SDK. |
| [enableCustomAudioCapture](https://www.tencentcloud.com/document/product/647/72270#f6957b147b00bf21188cefb40d9d12b0) | Enable custom audio capturing mode. |
| [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/72270#346038d926da53656a6b0744a635a525) | Deliver captured audio data to SDK. |
| [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/72270#52ab34f49ed6033aa3856504c33c10ff) | Enable/Disable custom audio track. |
| [enableLocalVideoCustomProcess](https://www.tencentcloud.com/document/product/647/72270#ca8ffe633d84e1d03ac4513efd9730c9) | .1 Enable third-party beauty filters in video. |
| [setLocalVideoCustomProcessCallback](https://www.tencentcloud.com/document/product/647/72270#3ff1164f5fe9646f413a1f9ff5e8a83d) | .2 Set video data callback for third-party beauty filters. |
| [setLocalVideoRenderCallback](https://www.tencentcloud.com/document/product/647/72270#90446bafe45e8f227390ec15613cbcf7) | Set the callback of custom rendering for local video. |
| [setRemoteVideoRenderCallback](https://www.tencentcloud.com/document/product/647/72270#1f8dfcdde1c0f2cd099fc0ac1464fb37) | Set the callback of custom rendering for remote video. |
| [setAudioFrameCallback](https://www.tencentcloud.com/document/product/647/72270#f3d09f001ca9928b417b4d2a48ce692e) | Set custom audio data callback. |
| [setCapturedAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/72270#fbe5029c6cbbd6c4354e4a66807ff9b7) | Set the callback format of audio frames captured by local mic. |
| [setLocalProcessedAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/72270#06a441d79f72dc5269aa80e3fe766873) | Set the callback format of preprocessed local audio frames. |
| [setMixedPlayAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/72270#59c33318c04f505402792cf49535085c) | Set the callback format of audio frames to be played back by system. |
| [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72270#20d4d41de96d8e2e6d2cf6499ea55171) | Use UDP channel to send custom message to all users in room. |
| [sendSEIMsg](https://www.tencentcloud.com/document/product/647/72270#2d918c3d0ef54d41bd5f5adcb62f63d6) | Use SEI channel to send custom message to all users in room. |
| [startSpeedTest](https://www.tencentcloud.com/document/product/647/72270#ecb445c9cc990d87be9fd5b11877af87) | Start network speed test (used before room entry). |
| [stopSpeedTest](https://www.tencentcloud.com/document/product/647/72270#300e5f71dde3917dc5e057f9e1f6e014) | Stop network speed test. |
| [getScriptVersion](https://www.tencentcloud.com/document/product/647/72270#b71b2488d8664664486147fb47c570f4) | Get SDK ScriptVersion information. |
| [getSDKVersion](https://www.tencentcloud.com/document/product/647/72270#f01e9209a78e98ddd4562d429e473256) | Get SDK version information. |
| [setLogLevel](https://www.tencentcloud.com/document/product/647/72270#06eaac4ef81347a5804f5188214eb8e9) | Set log output level. |
| [setConsoleEnabled](https://www.tencentcloud.com/document/product/647/72270#9d772868a17e895634e911b5c1d64b1f) | Enable/Disable console log printing. |
| [setLogCompressEnabled](https://www.tencentcloud.com/document/product/647/72270#a2b056173cd36a1e3ce30bcbde1ad3a1) | Enable/Disable local log compression. |
| [setLogDirPath](https://www.tencentcloud.com/document/product/647/72270#171009adcb84ac7436010b7d84b95b6b) | Set local log storage path. |
| [setLogCallback](https://www.tencentcloud.com/document/product/647/72270#3581586698172fd227b6f6f1db929a7b) | Set log callback. |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/72270#d39524378aab365ff67e393e3844230c) | Call experimental APIs. |

## getTRTCShareInstance

**getTRTCShareInstance**

#### Create TRTCCloud instance (singleton mode).

> **Note**1. If you use ` delete ITRTCCloud* `, a compilation error will occur. Please use [destroyTRTCShareInstance](https://www.tencentcloud.com/document/product/647/72270#a077f03f488af3cc8fefc5978d7f4dd0) to release the object pointer.

## destroyTRTCShareInstance

**destroyTRTCShareInstance**

#### Terminate TRTCCloud instance (singleton mode).

## addCallback

**addCallback**

| void addCallback | ([ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431) callback) |
| --- | --- |

#### Add TRTC event callback.

You can use [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431) to get various event notifications from the SDK, such as error codes, warning codes, and audio/video status parameters.

## removeCallback

**removeCallback**

| void removeCallback | ([ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431) callback) |
| --- | --- |

#### Remove TRTC event callback.

## enterRoom

**enterRoom**

| void enterRoom | (ref [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190) param |
| --- | --- |
|  | [TRTCAppScene](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) scene) |

#### Enter room.

All TRTC users need to enter a room before they can "publish" or "subscribe to" audio/video streams. "Publishing" refers to pushing their own streams to the cloud, and "subscribing to" refers to pulling the streams of other users in the room from the cloud.

When calling this API, you need to specify your application scenario ([TRTCAppScene](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1)) to get the best audio/video transfer experience. We provide the following four scenarios for your choice:

- [TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1):

Video call scenario. Use cases: [one-to-one video call], [video conferencing with up to 300 participants], [online medical diagnosis], [small class], [video interview], etc.

In this scenario, each room supports up to 300 concurrent online users, and up to 50 of them can speak simultaneously.

- [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1):

Audio call scenario. Use cases: [one-to-one audio call], [audio conferencing with up to 300 participants], [audio chat], [online Werewolf], etc.

In this scenario, each room supports up to 300 concurrent online users, and up to 50 of them can speak simultaneously.

- [TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1):

Live streaming scenario. Use cases: [low-latency video live streaming], [interactive classroom for up to 100,000 participants], [live video competition], [video dating room], [remote training], [large-scale conferencing], etc.

In this scenario, each room supports up to 100,000 concurrent online users, but you should specify the user roles: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b)) or audience ([TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b)).

- [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1):

Audio chat room scenario. Use cases: [Clubhouse], [online karaoke room], [music live room], [FM radio], etc.

In this scenario, each room supports up to 100,000 concurrent online users, but you should specify the user roles: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b)) or audience ([TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b)).

After calling this API, you will receive the ` onEnterRoom(result) ` callback from [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431):

- If room entry succeeded, the ` result ` parameter will be a positive number (` result ` > 0), indicating the time in milliseconds (ms) between function call and room entry.
- If room entry failed, the ` result ` parameter will be a negative number (` result ` < 0), indicating the TXLiteAVError for room entry failure.

| Param | DESC |
| --- | --- |
| param | Room entry parameter, which is used to specify the user's identity, role, authentication credentials, and other information. For more information, please see [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190). |
| scene | Application scenario, which is used to specify the use case. The same [TRTCAppScene](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) should be configured for all users in the same room. |

> **Note**If ` scene ` is specified as [TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1), you must use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190) to specify the role of the current user in the room.The same ` scene ` should be configured for all users in the same room. Different `scene` may cause occasional abnormal problems.Please try to ensure that [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b) and [exitRoom](https://www.tencentcloud.com/document/product/647/72270#8e2de8da4b60ce0e19d385897ed77888) are used in pair; that is, please make sure that "the previous room is exited before the next room is entered"; otherwise, many issues may occur.

## exitRoom

**exitRoom**

#### Exit room.

Calling this API will allow the user to leave the current audio or video room and release the camera, mic, speaker, and other device resources.

After resources are released, the SDK will use the ` onExitRoom() ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431) to notify you.

If you need to call [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b) again or switch to the SDK of another provider, we recommend you wait until you receive the [onExitRoom](https://www.tencentcloud.com/document/product/647/72271#41f110aa6e3e428ef20c7a42438774ff) callback, so as to avoid the problem of the camera or mic being occupied.

## switchRole

**switchRole**

| void switchRole | ([TRTCRoleType](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b) role) |
| --- | --- |

#### Switch role.

This API is used to switch the user role between ` anchor ` and ` audience `.

As video live rooms and audio chat rooms need to support an audience of up to 100,000 concurrent online users, the rule "only anchors can publish their audio/video streams" has been set. Therefore, when some users want to publish their streams (so that they can interact with anchors), they need to switch their role to "anchor" first.

You can use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190) during room entry to specify the user role in advance or use the ` switchRole ` API to switch roles after room entry.

| Param | DESC |
| --- | --- |
| role | Role, which is ` anchor ` by default: [TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b): anchor, who can publish their audio/video streams. Up to 50 anchors are allowed to publish streams at the same time in one room. [TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b): audience, who cannot publish their audio/video streams, but can only watch streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/72270#a2f85cd8f74124a8d0ec0c8b34d94b01). One room supports an audience of up to 100,000 concurrent online users. |

> **Note**1. This API is only applicable to two scenarios: live streaming ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1)) and audio chat room ([TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1)).2. If the ` scene ` you specify in [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b) is [TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1), please do not call this API.

## switchRoom

**switchRoom**

| void switchRoom | ([TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/72275#d43f5dc42762839497bd8586ac2091e3) config) |
| --- | --- |

#### Switch room.

This API is used to quickly switch a user from one room to another.

- If the user's role is ` audience `, calling this API is equivalent to ` exitRoom ` (current room) + ` enterRoom ` (new room).
- If the user's role is ` anchor `, the API will retain the current audio/video publishing status while switching the room; therefore, during the room switch, camera preview and sound capturing will not be interrupted.

This API is suitable for the online education scenario where the supervising teacher can perform fast room switch across multiple rooms. In this scenario, using ` switchRoom ` can get better smoothness and use less code than ` exitRoom + enterRoom `.

The API call result will be called back through ` onSwitchRoom(errCode, errMsg) ` in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431).

| Param | DESC |
| --- | --- |
| config | Room parameter. For more information, please see [TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/72275#d43f5dc42762839497bd8586ac2091e3). |

> **Note**Due to the requirement for compatibility with legacy versions of the SDK, the ` config ` parameter contains both ` roomId ` and ` strRoomId ` parameters. You should pay special attention as detailed below when specifying these two parameters:1. If you decide to use ` strRoomId `, then set ` roomId ` to 0. If both are specified, ` roomId ` will be used.2. All rooms need to use either ` strRoomId ` or ` roomId ` at the same time. They cannot be mixed; otherwise, there will be many unexpected bugs.

## connectOtherRoom

**connectOtherRoom**

| void connectOtherRoom | (string jsonParams) |
| --- | --- |

#### Request cross-room call.

By default, only users in the same room can make audio/video calls with each other, and the audio/video streams in different rooms are isolated from each other.

However, you can publish the audio/video streams of an anchor in another room to the current room by calling this API. At the same time, this API will also publish the local audio/video streams to the target anchor's room.

In other words, you can use this API to share the audio/video streams of two anchors in two different rooms, so that the audience in each room can watch the streams of these two anchors. This feature can be used to implement anchor competition.

The result of requesting cross-room call will be returned through the [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/72271#225107b993ed84f6fab7f8950df71b81) callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431).

For example, after anchor A in room "101" uses ` connectOtherRoom() ` to successfully call anchor B in room "102":

- All users in room "101" will receive the ` onRemoteUserEnterRoom(B) ` and ` onUserVideoAvailable(B,true) ` event callbacks of anchor B; that is, all users in room "101" can subscribe to the audio/video streams of anchor B.
- All users in room "102" will receive the ` onRemoteUserEnterRoom(A) ` and ` onUserVideoAvailable(A,true) ` event callbacks of anchor A; that is, all users in room "102" can subscribe to the audio/video streams of anchor A.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fb12ead35bb011f095485254005ef0f7.png)

For compatibility with subsequent extended fields for cross-room call, parameters in JSON format are used currently.

Case 1: numeric room ID

If anchor A in room "101" wants to co-anchor with anchor B in room "102", then anchor A needs to pass in {"roomId": 102, "userId": "userB"} when calling this API.

Below is the sample code:

Case 2: string room ID

If you use a string room ID, please be sure to replace the ` roomId ` in JSON with ` strRoomId `, such as ` {"strRoomId": "102", "userId": "userB"} `

Below is the sample code:

| Param | DESC |
| --- | --- |
| param | You need to pass in a string parameter in JSON format: ` roomId ` represents the room ID in numeric format, ` strRoomId ` represents the room ID in string format, and ` userId ` represents the user ID of the target anchor. |

## disconnectOtherRoom

**disconnectOtherRoom**

#### Exit cross-room call.

The result will be returned through the ` onDisconnectOtherRoom() ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431).

## setDefaultStreamRecvMode

**setDefaultStreamRecvMode**

| void setDefaultStreamRecvMode | (bool autoRecvAudio |
| --- | --- |
|  | bool autoRecvVideo) |

#### Set subscription mode (which must be set before room entry for it to take effect).

You can switch between the "automatic subscription" and "manual subscription" modes through this API:

- Automatic subscription: this is the default mode, where the user will immediately receive the audio/video streams in the room after room entry, so that the audio will be automatically played back, and the video will be automatically decoded (you still need to bind the rendering control through the ` startRemoteView ` API).
- Manual subscription: after room entry, the user needs to manually call the [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) API to start subscribing to and decoding the video stream and call the [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/72270#b9f7792974d2df2e3922f2ed1e06ea39) (false) API to start playing back the audio stream.

In most scenarios, users will subscribe to the audio/video streams of all anchors in the room after room entry. Therefore, TRTC adopts the automatic subscription mode by default in order to achieve the best "instant streaming experience".

In your application scenario, if there are many audio/video streams being published at the same time in each room, and each user only wants to subscribe to 1â2 streams of them, we recommend you use the "manual subscription" mode to reduce the traffic costs.

| Param | DESC |
| --- | --- |
| autoRecvAudio | true: automatic subscription to audio; false: manual subscription to audio by calling ` muteRemoteAudio(false) `. Default value: true |
| autoRecvVideo | true: automatic subscription to video; false: manual subscription to video by calling ` startRemoteView `. Default value: true |

> **Note**1. The configuration takes effect only if this API is called before room entry (enterRoom).2. In the automatic subscription mode, if the user does not call [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) to subscribe to the video stream after room entry, the SDK will automatically stop subscribing to the video stream in order to reduce the traffic consumption.

## createSubCloud

**createSubCloud**

#### Create room subinstance (for concurrent multi-room listen/watch).

` TRTCCloud ` was originally designed to work in the singleton mode, which limited the ability to watch concurrently in multiple rooms.

By calling this API, you can create multiple ` TRTCCloud ` instances, so that you can enter multiple different rooms at the same time to listen/watch audio/video streams.

However, it should be noted that your ability to publish audio and video streams in multiple ` TRTCCloud ` instances will be limited.

This feature is mainly used in the "super small class" use case in the online education scenario to break the limit that "only up to 50 users can publish their audio/video streams simultaneously in one TRTC room".

Below is the sample code:

> **Note**1. The same user can enter multiple rooms with different ` roomId ` values by using the same ` userId `.2. Two devices cannot use the same ` userId ` to enter the same room with a specified ` roomId `.3. You can set [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431) separately for different instances to get their own event notifications.4. The same user can push streams in multiple ` TRTCCloud ` instances at the same time, and can also call APIs related to local audio/video in the sub instance. But need to pay attention to: Audio needs to be collected by the microphone or custom data at the same time in all instances, and the result of API calls related to the audio device will be based on the last time; The result of camera-related API call will be based on the last time: [startLocalPreview](https://www.tencentcloud.com/document/product/647/72270#38628a2c12121285b0ab3c24eba211dc).

#### Return Desc:

` TRTCCloud ` subinstance

## destroySubCloud

**destroySubCloud**

| void destroySubCloud | ([ITRTCCloud](https://www.tencentcloud.com/document/product/647/72270#c147edc3349cedea03776fa64458db5c) subCloud) |
| --- | --- |

#### Terminate room subinstance.

| Param | DESC |
| --- | --- |
| subCloud | Room subinstance |

## startPublishMediaStream

**startPublishMediaStream**

| void startPublishMediaStream | (ref [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49) target |
| --- | --- |
|  | ref [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72275#22718fe81d94d21ec895cbc11820c726) param |
|  | ref [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166) config) |

#### Publish a stream.

After this API is called, the TRTC server will relay the stream of the local user to a CDN (after transcoding or without transcoding), or transcode and publish the stream to a TRTC room.

You can use the [TRTCPublishMode](https://www.tencentcloud.com/document/product/647/72275#064db271e894d12e1e3ad63bbb1677fb) parameter in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49) to specify the publishing mode.

| Param | DESC |
| --- | --- |
| config | The On-Cloud MixTranscoding settings. This parameter is invalid in the relay-to-CDN mode. It is required if you transcode and publish the stream to a CDN or to a TRTC room. For details, see [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166). |
| params | The encoding settings. This parameter is required if you transcode and publish the stream to a CDN or to a TRTC room. If you relay to a CDN without transcoding, to improve the relaying stability and playback compatibility, we also recommend you set this parameter. For details, see [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72275#22718fe81d94d21ec895cbc11820c726). |
| target | The publishing destination. You can relay the stream to a CDN (after transcoding or without transcoding) or transcode and publish the stream to a TRTC room. For details, see [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49). |

> **Note**1. The SDK will send a task ID to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/72271#8c314542e34620ecf64a2310577b34ba) callback.2. You can start a publishing task only once and cannot initiate two tasks that use the same publishing mode and publishing cdn url. Note the task ID returned, which you need to pass to [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#dad88b0322dc59b7e5dbf084b963782e) to modify the publishing parameters or [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#5d9c082fb84a8784246a729663df1ac4) to stop the task.3. You can specify up to 10 CDN URLs in ` target `. You will be charged only once for transcoding even if you relay to multiple CDNs.4. To avoid causing errors, do not specify the same URLs for different publishing tasks executed at the same time. We recommend you add "sdkappid_roomid_userid_main" to URLs to distinguish them from one another and avoid application conflicts.

## updatePublishMediaStream

**updatePublishMediaStream**

| void updatePublishMediaStream | (string taskId |
| --- | --- |
|  | ref [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49) target |
|  | ref [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72275#22718fe81d94d21ec895cbc11820c726) param |
|  | ref [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166) config) |

#### Modify publishing parameters.

You can use this API to change the parameters of a publishing task initiated by [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

| Param | DESC |
| --- | --- |
| config | The On-Cloud MixTranscoding settings. This parameter is invalid in the relay-to-CDN mode. It is required if you transcode and publish the stream to a CDN or to a TRTC room. For details, see [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166). |
| params | The encoding settings. This parameter is required if you transcode and publish the stream to a CDN or to a TRTC room. If you relay to a CDN without transcoding, to improve the relaying stability and playback compatibility, we recommend you set this parameter. For details, see [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72275#22718fe81d94d21ec895cbc11820c726). |
| target | The publishing destination. You can relay the stream to a CDN (after transcoding or without transcoding) or transcode and publish the stream to a TRTC room. For details, see [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49). |
| taskId | The task ID returned to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/72271#8c314542e34620ecf64a2310577b34ba) callback. |

> **Note**1. You can use this API to add or remove CDN URLs to publish to (you can publish to up to 10 CDNs at a time). To avoid causing errors, do not specify the same URLs for different tasks executed at the same time.2. You can use this API to switch a relaying task to transcoding or vice versa. For example, in cross-room communication, you can first call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4) to relay to a CDN. When the anchor requests cross-room communication, call this API, passing in the task ID to switch the relaying task to a transcoding task. This can ensure that the live stream and CDN playback are not interrupted (you need to keep the encoding parameters consistent).3. You can not switch output between "only audio", "only video" and "audio and video" for the same task.

## stopPublishMediaStream

**stopPublishMediaStream**

| void stopPublishMediaStream | (string taskId) |
| --- | --- |

#### Stop publishing.

You can use this API to stop a task initiated by [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

| Param | DESC |
| --- | --- |
| taskId | The task ID returned to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/72271#8c314542e34620ecf64a2310577b34ba) callback. |

> **Note**1. If the task ID is not saved to your backend, you can call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4) again when an anchor re-enters the room after abnormal exit. The publishing will fail, but the TRTC backend will return the task ID to you.2. If ` taskId ` is left empty, the TRTC backend will end all tasks you started through [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4). You can leave it empty if you have started only one task or want to stop all publishing tasks started by you.

## startLocalPreview

**startLocalPreview**

| void startLocalPreview | (bool frontCamera |
| --- | --- |
|  | GameObject view) |

#### Enable the preview image of local camera (mobile).

If this API is called before [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b), the SDK will only enable the camera and wait until [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b) is called before starting push.

If it is called after [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b), the SDK will enable the camera and automatically start pushing the video stream.

When the first camera video frame starts to be rendered, you will receive the ` onCameraDidReady ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431).

| Param | DESC |
| --- | --- |
| frontCamera | true: front camera; false: rear camera |
| view | Control that carries the video image |

> **Note**If you want to preview the camera image and adjust the beauty filter parameters through ` BeautyManager ` before going live, you can: Scheme 1. Call ` startLocalPreview ` before calling [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b). Scheme 2. Call ` startLocalPreview ` and ` muteLocalVideo(true) ` after calling [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b).

## stopLocalPreview

**stopLocalPreview**

#### Stop camera preview.

## muteLocalVideo

**muteLocalVideo**

| void muteLocalVideo | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
| --- | --- |
|  | bool mute) |

#### Pause/Resume publishing local video stream.

This API can pause (or resume) publishing the local video image. After the pause, other users in the same room will not be able to see the local image.

This API is equivalent to the two APIs of ` startLocalPreview/stopLocalPreview ` when TRTCVideoStreamTypeBig is specified, but has higher performance and response speed.

The ` startLocalPreview/stopLocalPreview ` APIs need to enable/disable the camera, which are hardware device-related operations, so they are very time-consuming.

In contrast, ` muteLocalVideo ` only needs to pause or allow the data stream at the software level, so it is more efficient and more suitable for scenarios where frequent enabling/disabling are needed.

After local video publishing is paused, other members in the same room will receive the ` onUserVideoAvailable(userId, false) ` callback notification.

After local video publishing is resumed, other members in the same room will receive the ` onUserVideoAvailable(userId, true) ` callback notification.

| Param | DESC |
| --- | --- |
| mute | true: pause; false: resume |
| streamType | Specify for which video stream to pause (or resume). Only [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) and [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) are supported |

## startRemoteView

**startRemoteView**

| void startRemoteView | (string userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
|  | GameObject view) |

#### Subscribe to remote user's video stream and bind video rendering control.

Calling this API allows the SDK to pull the video stream of the specified ` userId ` and render it to the rendering control specified by the ` view ` parameter. You can set the display mode of the video image through [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/72270#80129ddbe95cb5820c30be890d25f299).

- If you already know the ` userId ` of a user who has a video stream in the room, you can directly call ` startRemoteView ` to subscribe to the user's video image.
- If you don't know which users in the room are publishing video streams, you can wait for the notification from [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/72271#59380ac1827201d40a1795e59f2f894a) after [enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b).

Calling this API only starts pulling the video stream, and the image needs to be loaded and buffered at this time. After the buffering is completed, you will receive a notification from [onFirstVideoFrame](https://www.tencentcloud.com/document/product/647/72271#7506c0166d59556803da3620d8bed4fb).

| Param | DESC |
| --- | --- |
| streamType | Video stream type of the ` userId ` specified for watching: HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) (the remote user should enable dual-channel encoding through [enableSmallVideoStream](https://www.tencentcloud.com/document/product/647/72270#0eaec8c2511ebc3aa5b402690bd6f007) for this parameter to take effect) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |
| view | Rendering control that carries the video image |

> **Note**The following requires your attention:1. The SDK supports watching the big image and substream image or small image and substream image of a ` userId ` at the same time, but does not support watching the big image and small image at the same time.2. Only when the specified ` userId ` enables dual-channel encoding through [enableSmallVideoStream](https://www.tencentcloud.com/document/product/647/72270#0eaec8c2511ebc3aa5b402690bd6f007) can the user's small image be viewed.3. If the small image of the specified ` userId ` does not exist, the SDK will switch to the big image of the user by default.

## stopRemoteView

**stopRemoteView**

| void stopRemoteView | (string userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType) |

#### Stop subscribing to remote user's video stream and release rendering control.

Calling this API will cause the SDK to stop receiving the user's video stream and release the decoding and rendering resources for the stream.

| Param | DESC |
| --- | --- |
| streamType | Video stream type of the ` userId ` specified for watching: HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |

## stopAllRemoteView

**stopAllRemoteView**

#### Stop subscribing to all remote users' video streams and release all rendering resources.

Calling this API will cause the SDK to stop receiving all remote video streams and release all decoding and rendering resources.

> **Note**If a substream image (screen sharing) is being displayed, it will also be stopped.

## muteRemoteVideoStream

**muteRemoteVideoStream**

| void muteRemoteVideoStream | (string userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
|  | bool mute) |

#### Pause/Resume subscribing to remote user's video stream.

This API only pauses/resumes receiving the specified user's video stream but does not release displaying resources; therefore, the video image will freeze at the last frame before it is called.

| Param | DESC |
| --- | --- |
| mute | Whether to pause receiving |
| streamType | Specify for which video stream to pause (or resume): HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |

> **Note**This API can be called before room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b)), and the pause status will be reset after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/72270#8e2de8da4b60ce0e19d385897ed77888)). After calling this API to pause receiving the video stream from a specific user, simply calling the [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) API will not be able to play the video from that user. You need to call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/72270#e47216c48085fc929661d33cfece2181)(false) or [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/72270#d8b35494f4f1d45de0f70ca1f3cbdc15)(false) to resume it.

## muteAllRemoteVideoStreams

**muteAllRemoteVideoStreams**

| void muteAllRemoteVideoStreams | (bool mute) |
| --- | --- |

#### Pause/Resume subscribing to all remote users' video streams.

This API only pauses/resumes receiving all users' video streams but does not release displaying resources; therefore, the video image will freeze at the last frame before it is called.

| Param | DESC |
| --- | --- |
| mute | Whether to pause receiving |

> **Note**This API can be called before room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b)), and the pause status will be reset after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/72270#8e2de8da4b60ce0e19d385897ed77888)).After calling this interface to pause receiving video streams from all users, simply calling the [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) interface will not be able to play the video from a specific user. You need to call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/72270#e47216c48085fc929661d33cfece2181)(false) or [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/72270#d8b35494f4f1d45de0f70ca1f3cbdc15)(false) to resume it.

## setVideoEncoderParam

**setVideoEncoderParam**

| void setVideoEncoderParam | (ref [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/72275#b5beabfeefb812ccf1060aea67185c4e) param) |
| --- | --- |

#### Set the encoding parameters of video encoder.

This setting can determine the quality of image viewed by remote users, which is also the image quality of on-cloud recording files.

| Param | DESC |
| --- | --- |
| param | It is used to set relevant parameters for the video encoder. For more information, please see [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/72275#b5beabfeefb812ccf1060aea67185c4e). |

> **Note**Begin from v11.5 version, the encoding output resolution will be aligned according to width 8 and height 2 bytes, and will be adjusted downward, eg: input resolution 540x960, actual encoding output resolution 536x960.

## setNetworkQosParam

**setNetworkQosParam**

| void setNetworkQosParam | (ref [TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/72275#15fa30eb2d0220259cea127fdb0f886f) param) |
| --- | --- |

#### Set network quality control parameters.

This setting determines the quality control policy in a poor network environment, such as "image quality preferred" or "smoothness preferred".

| Param | DESC |
| --- | --- |
| param | It is used to set relevant parameters for network quality control. For details, please refer to [TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/72275#15fa30eb2d0220259cea127fdb0f886f). |

## setLocalRenderParams

**setLocalRenderParams**

| void setLocalRenderParams | ([TRTCRenderParams](https://www.tencentcloud.com/document/product/647/72275#660db44737d95899da095d02d163c478) renderParams) |
| --- | --- |

#### Set the rendering parameters of local video image.

The parameters that can be set include video image rotation angle, fill mode, and mirror mode.

| Param | DESC |
| --- | --- |
| params | Video image rendering parameters. For more information, please see [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/72275#660db44737d95899da095d02d163c478). |

## setRemoteRenderParams

**setRemoteRenderParams**

| void setRemoteRenderParams | (string userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
|  | ref [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/72275#660db44737d95899da095d02d163c478) renderParams) |

#### Set the rendering mode of remote video image.

The parameters that can be set include video image rotation angle, fill mode, and mirror mode.

| Param | DESC |
| --- | --- |
| params | Video image rendering parameters. For more information, please see [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/72275#660db44737d95899da095d02d163c478). |
| streamType | It can be set to the primary stream image (TRTCVideoStreamTypeBig) or substream image (TRTCVideoStreamTypeSub). |
| userId | ID of the specified remote user |

## enableSmallVideoStream

**enableSmallVideoStream**

| void enableSmallVideoStream | (bool enable |
| --- | --- |
|  | ref [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/72275#b5beabfeefb812ccf1060aea67185c4e) smallVideoParam) |

#### Enable dual-channel encoding mode with big and small images.

In this mode, the current user's encoder will output two channels of video streams, i.e., **HD big image** and **Smooth small image**, at the same time (only one channel of audio stream will be output though).

In this way, other users in the room can choose to subscribe to the **HD big image** or **Smooth small image** according to their own network conditions or screen size.

| Param | DESC |
| --- | --- |
| enable | Whether to enable small image encoding. Default value: false |
| smallVideoEncParam | Video parameters of small image stream |

> **Note**Dual-channel encoding will consume more CPU resources and network bandwidth; therefore, this feature can be enabled on macOS, Windows, or high-spec tablets, but is not recommended for phones.

#### Return Desc:

0: success; -1: the current big image has been set to a lower quality, and it is not necessary to enable dual-channel encoding

## setRemoteVideoStreamType

**setRemoteVideoStreamType**

| void setRemoteVideoStreamType | (string userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) type) |

#### Switch the big/small image of specified remote user.

After an anchor in a room enables dual-channel encoding, the video image that other users in the room subscribe to through [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) will be **HD big image** by default.

You can use this API to select whether the image subscribed to is the big image or small image. The API can take effect before or after [startRemoteView](https://www.tencentcloud.com/document/product/647/72270#1d041c439b9c088d4351eaf5aa832ca7) is called.

| Param | DESC |
| --- | --- |
| streamType | Video stream type, i.e., big image or small image. Default value: big image |
| userId | ID of the specified remote user |

> **Note**To implement this feature, the target user must have enabled the dual-channel encoding mode through [enableSmallVideoStream](https://www.tencentcloud.com/document/product/647/72270#0eaec8c2511ebc3aa5b402690bd6f007); otherwise, this API will not work.

## setGravitySensorAdaptiveMode

**setGravitySensorAdaptiveMode**

| void setGravitySensorAdaptiveMode | ([TRTCGravitySensorAdaptiveMode](https://www.tencentcloud.com/document/product/647/72275#601299c4e6bd66487314e0edd164bf03) mode) |
| --- | --- |

#### Set the adaptation mode of gravity sensing (version 11.7 and above).

After turning on gravity sensing, if the device on the collection end rotates, the images on the collection end and the audience will be rendered accordingly to ensure that the image in the field of view is always facing up.

It only takes effect in the camera capture scene inside the SDK, and only takes effect on the mobile terminal.

1. This interface only works for the collection end. If you only watch the picture in the room, opening this interface is invalid.

2. When the capture device is rotated 90 degrees or 270 degrees, the picture seen by the capture device or the audience may be cropped to maintain proportional coordination.

| Param | DESC |
| --- | --- |
| mode | Gravity sensing mode, see [TRTCGravitySensorAdaptiveMode_Disable](https://www.tencentcloud.com/document/product/647/72275#601299c4e6bd66487314e0edd164bf03)ã[TRTCGravitySensorAdaptiveMode_FillByCenterCrop](https://www.tencentcloud.com/document/product/647/72275#601299c4e6bd66487314e0edd164bf03) and [TRTCGravitySensorAdaptiveMode_FitWithBlackBorder](https://www.tencentcloud.com/document/product/647/72275#601299c4e6bd66487314e0edd164bf03) for details, default value: [TRTCGravitySensorAdaptiveMode_Disable](https://www.tencentcloud.com/document/product/647/72275#601299c4e6bd66487314e0edd164bf03). |

## startLocalAudio

**startLocalAudio**

| void startLocalAudio | ([TRTCAudioQuality](https://www.tencentcloud.com/document/product/647/72275#f8aeb89d8ef78db15d893e55f68cdb42) quality) |
| --- | --- |

#### Enable local audio capturing and publishing.

The SDK does not enable the mic by default. When a user wants to publish the local audio, the user needs to call this API to enable mic capturing and encode and publish the audio to the current room.

After local audio capturing and publishing is enabled, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/72271#6d7c1afbfcb241ccb76adf4fcd2a4999)(userId, true) notification.

| Param | DESC |
| --- | --- |
| quality | Sound quality [TRTCAudioQualitySpeech](https://www.tencentcloud.com/document/product/647/72275#f8aeb89d8ef78db15d893e55f68cdb42) - Smooth: mono channel; audio bitrate: 18 Kbps. This is suitable for audio call scenarios, such as online meeting and audio call. [TRTCAudioQualityDefault](https://www.tencentcloud.com/document/product/647/72275#f8aeb89d8ef78db15d893e55f68cdb42) - Default: mono channel; audio bitrate: 50 Kbps. This is the default sound quality of the SDK and recommended if there are no special requirements. [TRTCAudioQualityMusic](https://www.tencentcloud.com/document/product/647/72275#f8aeb89d8ef78db15d893e55f68cdb42) - HD: dual channel + full band; audio bitrate: 128 Kbps. This is suitable for scenarios where Hi-Fi music transfer is required, such as online karaoke and music live streaming. |

> **Note**This API will check the mic permission. If the current application does not have permission to use the mic, the SDK will automatically ask the user to grant the mic permission.

## stopLocalAudio

**stopLocalAudio**

#### Stop local audio capturing and publishing.

After local audio capturing and publishing is stopped, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/72271#6d7c1afbfcb241ccb76adf4fcd2a4999)(userId, false) notification.

## muteLocalAudio

**muteLocalAudio**

| void muteLocalAudio | (bool mute) |
| --- | --- |

#### Pause/Resume publishing local audio stream.

After local audio publishing is paused, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/72271#6d7c1afbfcb241ccb76adf4fcd2a4999)(userId, false) notification.

After local audio publishing is resumed, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/72271#6d7c1afbfcb241ccb76adf4fcd2a4999)(userId, true) notification.

Different from [stopLocalAudio](https://www.tencentcloud.com/document/product/647/72270#8fafafeb80fe86f9fc0d893c9c35bd4e), ` muteLocalAudio(true) ` does not release the mic permission; instead, it continues to send mute packets with extremely low bitrate.

This is very suitable for scenarios that require on-cloud recording, as video file formats such as MP4 have a high requirement for audio continuity, while an MP4 recording file cannot be played back smoothly if [stopLocalAudio](https://www.tencentcloud.com/document/product/647/72270#8fafafeb80fe86f9fc0d893c9c35bd4e) is used.

Therefore, ` muteLocalAudio ` instead of [stopLocalAudio](https://www.tencentcloud.com/document/product/647/72270#8fafafeb80fe86f9fc0d893c9c35bd4e) is recommended in scenarios where the requirement for recording file quality is high.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |

## muteRemoteAudio

**muteRemoteAudio**

| void muteRemoteAudio | (string userId |
| --- | --- |
|  | bool mute) |

#### Pause/Resume playing back remote audio stream.

When you mute the remote audio of a specified user, the SDK will stop playing back the user's audio and pulling the user's audio data.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |
| userId | ID of the specified remote user |

> **Note**This API works when called either before or after room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b)), and the mute status will be reset to ` false ` after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/72270#8e2de8da4b60ce0e19d385897ed77888)).

## muteAllRemoteAudio

**muteAllRemoteAudio**

| void muteAllRemoteAudio | (bool mute) |
| --- | --- |

#### Pause/Resume playing back all remote users' audio streams.

When you mute the audio of all remote users, the SDK will stop playing back all their audio streams and pulling all their audio data.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |

> **Note**This API works when called either before or after room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/72270#159a2893d28f7e533ed7dd67e63a9a7b)), and the mute status will be reset to ` false ` after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/72270#8e2de8da4b60ce0e19d385897ed77888)).

## setRemoteAudioVolume

**setRemoteAudioVolume**

| void setRemoteAudioVolume | (string userId |
| --- | --- |
|  | int volume) |

#### Set the audio playback volume of remote user.

You can mute the audio of a remote user through ` setRemoteAudioVolume(userId, 0) `.

| Param | DESC |
| --- | --- |
| userId | ID of the specified remote user |
| volume | Volume. 100 is the original volume. Value range: [0,150]. Default value: 100 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setAudioCaptureVolume

**setAudioCaptureVolume**

| void setAudioCaptureVolume | (int volume) |
| --- | --- |

#### Set the capturing volume of local audio.

| Param | DESC |
| --- | --- |
| volume | Volume. 100 is the original volume. Value range: [0,150]. Default value: 100 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## getAudioCaptureVolume

**getAudioCaptureVolume**

#### Get the capturing volume of local audio.

#### Return Desc:

capturing volume

## setAudioPlayoutVolume

**setAudioPlayoutVolume**

| void setAudioPlayoutVolume | (int volume) |
| --- | --- |

#### Set the playback volume of remote audio.

This API controls the volume of the sound ultimately delivered by the SDK to the system for playback. It affects the volume of the recorded local audio file but not the volume of in-ear monitoring.

| Param | DESC |
| --- | --- |
| volume | Volume. 100 is the original volume. Value range: [0,150]. Default value: 100 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## getAudioPlayoutVolume

**getAudioPlayoutVolume**

#### Get the playback volume of remote audio.

## enableAudioVolumeEvaluation

**enableAudioVolumeEvaluation**

| void enableAudioVolumeEvaluation | (bool enable |
| --- | --- |
|  | [TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/72275#a009476d3d69bd49ff693344302409bf) evaluateParams) |

#### Enable volume reminder.

After this feature is enabled, the SDK will return the audio volume assessment information of local user who sends stream and remote users in the [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/72271#12c009f500ddcfac4dc9bbf142bf68cb) callback of [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431).

| Param | DESC |
| --- | --- |
| enable | Whether to enable the volume prompt. Itâs disabled by default. |
| params | Volume evaluation and other related parameters, please see [TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/72275#a009476d3d69bd49ff693344302409bf) |

> **Note**To enable this feature, call this API before calling [startLocalAudio](https://www.tencentcloud.com/document/product/647/72270#126e2ce82ad449e5aafe277315896806).

## startLocalRecording

**startLocalRecording**

| void startLocalRecording | (ref [TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/72275#4d8f80d5bf4ece224c7125eec1490b3d) localRecordingParams) |
| --- | --- |

#### Start local media recording.

This API records the audio/video content during live streaming into a local file,and no recording fees for local recording.

| Param | DESC |
| --- | --- |
| params | Recording parameter. For more information, please see [TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/72275#4d8f80d5bf4ece224c7125eec1490b3d) |

## stopLocalRecording

**stopLocalRecording**

#### Stop local media recording.

If a recording task has not been stopped through this API before room exit, it will be automatically stopped after room exit.

## getDeviceManager

**getDeviceManager**

#### Get device management class (TXDeviceManager).

Through device management, you can set the functions of audio and video related hardware devices such as cameras, microphones, and speakers.

#### Return Desc:

device management class TXDeviceManager.

## setBeautyStyle

**setBeautyStyle**

| void setBeautyStyle | ([TRTCBeautyStyle](https://www.tencentcloud.com/document/product/647/72275#6b80cffd21c1ebc2f793a0dcc11abda6) style |
| --- | --- |
|  | uint beauty |
|  | uint white |
|  | uint ruddiness) |

#### Set special effects such as beauty, brightening, and rosy skin filters.

The SDK is integrated with two skin smoothing algorithms of different styles:

- "Smooth" style, which uses a more radical algorithm for more obvious effect and is suitable for show live streaming.
- "Natural" style, which retains more facial details for more natural effect and is suitable for most live streaming use cases.

| Param | DESC |
| --- | --- |
| beautyLevel | Strength of the beauty filter. Value range: 0â9; 0 indicates that the filter is disabled, and the greater the value, the more obvious the effect. |
| ruddinessLevel | Strength of the rosy skin filter. Value range: 0â9; 0 indicates that the filter is disabled, and the greater the value, the more obvious the effect. |
| style | Skin smoothening algorithm ("smooth" or "natural") |
| whitenessLevel | Strength of the brightening filter. Value range: 0â9; 0 indicates that the filter is disabled, and the greater the value, the more obvious the effect. |

## setWaterMark

**setWaterMark**

| void setWaterMark | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
| --- | --- |
|  | string srcData |
|  | [TRTCWaterMarkSrcType](https://www.tencentcloud.com/document/product/647/72275#49ce20e9ead413a1fe53e7a7854a9ef9) srcType |
|  | uint nWidth |
|  | uint nHeight |
|  | float xOffset |
|  | float yOffset |
|  | float fWidthRatio |
|  | bool isVisibleOnLocalPreview = false) |

#### Add watermark.

The watermark position is determined by the ` xOffset `, ` yOffset `, and ` fWidthRatio ` parameters.

- ` xOffset `: X coordinate of watermark, which is a floating-point number between 0 and 1.
- ` yOffset `: Y coordinate of watermark, which is a floating-point number between 0 and 1.
- ` fWidthRatio `: watermark dimensions ratio, which is a floating-point number between 0 and 1.

| Param | DESC |
| --- | --- |
| fWidthRatio | Ratio of watermark width to image width (the watermark will be scaled according to this parameter) |
| isVisibleOnLocalPreview | true: local preview show wartermark;false: local preview hide wartermark.only effect on win/mac. |
| nHeight | Pixel height of watermark image (this parameter will be ignored if the source data is a file path) |
| nWidth | Pixel width of watermark image (this parameter will be ignored if the source data is a file path) |
| srcData | Source data of watermark image (if ` nullptr ` is passed in, the watermark will be removed) |
| srcType | Source data type of watermark image. For more information, please see [TRTCWaterMarkSrcType](https://www.tencentcloud.com/document/product/647/72275#49ce20e9ead413a1fe53e7a7854a9ef9) |
| streamType | Stream type of the watermark to be set ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) or @@link TRTCVideoStreamTypeSub}) |
| xOffset | Top-left offset on the X axis of watermark |
| yOffset | Top-left offset on the Y axis of watermark |

> **Note**This API only supports adding an image watermark to the primary stream

## getAudioEffectManager

**getAudioEffectManager**

#### Get sound effect management class (TXAudioEffectManager).

` TXAudioEffectManager ` is a sound effect management API, through which you can implement the following features:

- Background music: both online music and local music can be played back with various features such as speed adjustment, pitch adjustment, original voice, accompaniment, and loop.
- In-ear monitoring: the sound captured by the mic is played back in the headphones in real time, which is generally used for music live streaming.
- Reverb effect: karaoke room, small room, big hall, deep, resonant, and other effects.
- Voice changing effect: young girl, middle-aged man, heavy metal, and other effects.
- Short sound effect: short sound effect files such as applause and laughter are supported (for files less than 10 seconds in length, please set the ` isShortFile ` parameter to ` true `).

#### Return Desc:

sound effect management class TXAudioEffectManager.

## startSystemAudioLoopback

**startSystemAudioLoopback**

| void startSystemAudioLoopback | (string deviceName) |
| --- | --- |

#### Enable system audio capturing(iOS not supported).

This API captures audio data from the sound card of the anchorâs computer and mixes it into the current audio stream of the SDK. This ensures that other users in the room hear the audio played back by the anchorâs computer.

In online education scenarios, a teacher can use this API to have the SDK capture the audio of instructional videos and broadcast it to students in the room.

In live music scenarios, an anchor can use this API to have the SDK capture the music played back by his or her player so as to add background music to the room.

| Param | DESC |
| --- | --- |
| deviceName | If this parameter is empty, the audio of the entire system is captured. |

> **Note**On the Windows platform, you can specify the parameter ` deviceName ` to the absolute path of an executable file (such as ` QQMuisc.exe `) of a certain application. In this case, the SDK will only capture the sound of that application (32-bit version of the SDK is supported, 64-bit version of the SDK requires Windows version 10.0.19042 or higher).You can also specify ` deviceName ` as the name of a certain speaker device to capture specific speaker sound (you can use the getDevicesList interface in TXDeviceManager to obtain the speaker devices of type [TXMediaDeviceTypeSpeaker](https://www.tencentcloud.com/document/product/647/72274#f023a4d94be317eb399df83a25af6b2b)).On the Windows platform, you can also specify ` deviceName ` as the process ID of a certain process (in the format of "process_xxx", where xxx is the process ID), and then the SDK will capture the sound of that process (requires Windows version 10.0.19042 or higher).Alternatively, on the Windows platform, you can specify ` deviceName ` as the process ID of a certain process to be excluded (in the format of "exclude_process_xxx", where xxx is the process ID), and then the SDK will capture all sounds except for that process (requires Windows version 10.0.19042 or higher).About speaker device name you can see TXDeviceManager

## stopSystemAudioLoopback

**stopSystemAudioLoopback**

#### Stop system audio capturing(iOS not supported).

## startScreenCapture

**startScreenCapture**

| void startScreenCapture | (GameObject view |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) type |
|  | ref [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/72275#b5beabfeefb812ccf1060aea67185c4e) param) |

#### Start screen sharing.

This API can capture the content of the entire screen or a specified application and share it with other users in the same room.

| Param | DESC |
| --- | --- |
| encParam | Image encoding parameters used for screen sharing, which can be set to empty, indicating to let the SDK choose the optimal encoding parameters (such as resolution and bitrate). |
| streamType | Channel used for screen sharing, which can be the primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)) or substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)). |
| view | Parent control of the rendering control, which can be set to a null value, indicating not to display the preview of the shared screen. |

> **Note**1. A user can publish at most one primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)) and one substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)) at the same time.2. By default, screen sharing uses the substream image. If you want to use the primary stream for screen sharing, you need to stop camera capturing (through [stopLocalPreview](https://www.tencentcloud.com/document/product/647/72270#e379630cda7e794574b00d549b64a815)) in advance to avoid conflicts.3. Only one user can use the substream for screen sharing in the same room at any time; that is, only one user is allowed to enable the substream in the same room at any time.4. When there is already a user in the room using the substream for screen sharing, calling this API will return the ` onError(ERR_SERVER_CENTER_ANOTHER_USER_PUSH_SUB_VIDEO) ` callback from [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431).

## stopScreenCapture

**stopScreenCapture**

#### Stop screen sharing.

## pauseScreenCapture

**pauseScreenCapture**

#### Pause screen sharing.

> **Note**Begin from v11.5 version, paused screen capture will use the last frame to output at a frame rate of 1fps.

## resumeScreenCapture

**resumeScreenCapture**

#### Resume screen sharing.

## selectScreenCaptureTarget

**selectScreenCaptureTarget**

| void selectScreenCaptureTarget | (TRTCScreenCaptureSourceInfo source |
| --- | --- |
|  | Rect captureRect |
|  | TRTCScreenCaptureProperty property) |

#### Select the screen or window to share (for desktop systems only).

After you get the sharable screens and windows through getScreenCaptureSources, you can call this API to select the target screen or window you want to share.

During the screen sharing process, you can also call this API at any time to switch the sharing target.

The following four sharing modes are supported:

- Sharing the entire screen: for ` source ` whose ` type ` is [TRTCScreenCaptureSourceTypeScreen](https://www.tencentcloud.com/document/product/647/72275#18d36b5519a892bf4b8b3f52a8b0a210)  in ` sourceInfoList `, set ` captureRect ` to ` { 0, 0, 0, 0 } `.
- Sharing a specified area: for ` source ` whose ` type ` is [TRTCScreenCaptureSourceTypeScreen](https://www.tencentcloud.com/document/product/647/72275#18d36b5519a892bf4b8b3f52a8b0a210)  in ` sourceInfoList `, set ` captureRect ` to a non-nullptr value, e.g., ` { 100, 100, 300, 300 } `.
- Sharing an entire window: for ` source ` whose ` type ` is [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/72275#18d36b5519a892bf4b8b3f52a8b0a210) in ` sourceInfoList `, set ` captureRect ` to ` { 0, 0, 0, 0 } `.
- Sharing a specified window area: for ` source ` whose ` type ` is [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/72275#18d36b5519a892bf4b8b3f52a8b0a210) in ` sourceInfoList `, set ` captureRect ` to a non-nullptr value, e.g., ` { 100, 100, 300, 300 } `.

| Param | DESC |
| --- | --- |
| captureRect | Specify the area to be captured |
| property | Specify the attributes of the screen sharing target, such as capturing the cursor and highlighting the captured window. For more information, please see the definition of ` TRTCScreenCaptureProperty ` |
| source | Specify sharing source. For more information, please refer to [TRTCScreenCaptureSourceInfo](https://www.tencentcloud.com/document/product/647/72275#16efc1045b787ecedb85e181e0c2ce29). |

> **Note**Setting the highlight border color and width parameters does not take effect on macOS.

## setSubStreamEncoderParam

**setSubStreamEncoderParam**

| void setSubStreamEncoderParam | (ref [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/72275#b5beabfeefb812ccf1060aea67185c4e) param) |
| --- | --- |

#### Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems).

This API can set the image quality of screen sharing (i.e., the substream) viewed by remote users, which is also the image quality of screen sharing in on-cloud recording files.

Please note the differences between the following two APIs:

- [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/72270#944184af05e4175e9458e5b0d563fb68) is used to set the video encoding parameters of the primary stream image ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868), generally for camera).
- [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72270#b809f30d749d36cfbd2d02d3975af747) is used to set the video encoding parameters of the substream image ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868), generally for screen sharing).

| Param | DESC |
| --- | --- |
| param | Substream encoding parameters. For more information, please see [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/72275#b5beabfeefb812ccf1060aea67185c4e). |

## enableCustomVideoCapture

**enableCustomVideoCapture**

| void enableCustomVideoCapture | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
| --- | --- |
|  | bool enable) |

#### Enable/Disable custom video capturing mode.

After this mode is enabled, the SDK will not run the original video capturing process (i.e., stopping camera data capturing and beauty filter operations) and will retain only the video encoding and sending capabilities.

You need to use [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/72270#8c8378c65a0b11187d6812523706a9f0) to continuously insert the captured video image into the SDK.

| Param | DESC |
| --- | --- |
| enable | Whether to enable. Default value: false |
| streamType | Specify video stream type ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868): HD big image; [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868): substream image). |

## sendCustomVideoData

**sendCustomVideoData**

| void sendCustomVideoData | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) streamType |
| --- | --- |
|  | [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/72275#9233a1b1573333abc70e53b51bd89740) frame) |

#### Deliver captured video frames to SDK.

You can use this API to deliver video frames you capture to the SDK, and the SDK will encode and transfer them through its own network module.

We recommend you enter the following information for the [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/72275#9233a1b1573333abc70e53b51bd89740) parameter (other fields can be left empty):

- pixelFormat: on Windows and Android, only [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) is supported; on iOS and macOS, [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) and [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) are supported.
- bufferType: [TRTCVideoBufferType_Buffer](https://www.tencentcloud.com/document/product/647/72275#133a51a3a497d78c2b4d5de72ec7aaeb) is recommended.
- data: buffer used to carry video frame data.
- length: video frame data length. If ` pixelFormat ` is set to I420, ` length ` can be calculated according to the following formula: ` length = width * height * 3 / 2 `.
- width: video image width, such as 640 px.
- height: video image height, such as 480 px.
- timestamp (ms): Set it to the timestamp when video frames are captured, which you can obtain by calling generateCustomPTS after getting a video frame.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/35158).

| Param | DESC |
| --- | --- |
| frame | Video data, which can be in I420 format. |
| streamType | Specify video stream type ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868): HD big image; [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868): substream image). |

> **Note**1. We recommend you call the generateCustomPTS API to get the ` timestamp ` value of a video frame immediately after capturing it, so as to achieve the best audio/video sync effect.2. The video frame rate eventually encoded by the SDK is not determined by the frequency at which you call this API, but by the FPS you set in [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/72270#944184af05e4175e9458e5b0d563fb68).3. Please try to keep the calling interval of this API even; otherwise, problems will occur, such as unstable output frame rate of the encoder or out-of-sync audio/video.4. On iOS and macOS, video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) or [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) format can be passed in currently.5. On Windows and Android, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) format can be passed in currently.

## enableCustomAudioCapture

**enableCustomAudioCapture**

| void enableCustomAudioCapture | (bool enable) |
| --- | --- |

#### Enable custom audio capturing mode.

After this mode is enabled, the SDK will not run the original audio capturing process (i.e., stopping mic data capturing) and will retain only the audio encoding and sending capabilities.

You need to use [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/72270#346038d926da53656a6b0744a635a525) to continuously insert the captured audio data into the SDK.

| Param | DESC |
| --- | --- |
| enable | Whether to enable. Default value: false |

> **Note**As acoustic echo cancellation (AEC) requires strict control over the audio capturing and playback time, after custom audio capturing is enabled, AEC may fail.

## sendCustomAudioData

**sendCustomAudioData**

| void sendCustomAudioData | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/72275#ac73b0af225be99342eab0db97c8ee5b) frame) |
| --- | --- |

#### Deliver captured audio data to SDK.

We recommend you enter the following information for the [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/72275#ac73b0af225be99342eab0db97c8ee5b) parameter (other fields can be left empty):

- audioFormat: audio data format, which can only be ` TRTCAudioFrameFormatPCM `.
- data: audio frame buffer. Audio frame data must be in PCM format, and it supports a frame length of 5â100 ms (20 ms is recommended). Length calculation method: **for example, if the sample rate is 48000, then the frame length for mono channel will be `48000 * 0.02s * 1 * 16 bit = 15360 bit = 1920 bytes`.**
- sampleRate: sample rate. Valid values: 16000, 24000, 32000, 44100, 48000.
- channel: number of channels (if stereo is used, data is interwoven). Valid values: 1: mono channel; 2: dual channel.
- timestamp (ms): Set it to the timestamp when audio frames are captured, which you can obtain by calling generateCustomPTS after getting a audio frame.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/47635).

| Param | DESC |
| --- | --- |
| frame | Audio data |

> **Note**Please call this API accurately at intervals of the frame length; otherwise, sound lag may occur due to uneven data delivery intervals.

## enableMixExternalAudioFrame

**enableMixExternalAudioFrame**

| void enableMixExternalAudioFrame | (bool enablePublish |
| --- | --- |
|  | bool enablePlayout) |

#### Enable/Disable custom audio track.

After this feature is enabled, you can mix a custom audio track into the SDK through this API. With two boolean parameters, you can control whether to play back this track remotely or locally.

| Param | DESC |
| --- | --- |
| enablePlayout | Whether the mixed audio track should be played back locally. Default value: false |
| enablePublish | Whether the mixed audio track should be played back remotely. Default value: false |

> **Note**If you specify both ` enablePublish ` and ` enablePlayout ` as ` false `, the custom audio track will be completely closed.

## enableLocalVideoCustomProcess

**enableLocalVideoCustomProcess**

| int enableLocalVideoCustomProcess | (bool enable |
| --- | --- |
|  | [TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) pixelFormat |
|  | [TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/72275#133a51a3a497d78c2b4d5de72ec7aaeb) bufferType) |

#### .1 Enable third-party beauty filters in video.

After it is enabled, you can get the image frame of the specified pixel format and video data structure type through [ITRTCVideoFrameCallback](https://www.tencentcloud.com/document/product/647/72271#9454c2f295e4e4519548382c4b6d868c).

| Param | DESC |
| --- | --- |
| bufferType | Specify the format of the data called back. |
| enable | Whether to enable local video process. Itâs disabled by default. |
| pixelFormat | Specify the format of the pixel called back. |

#### Return Desc:

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setLocalVideoCustomProcessCallback

**setLocalVideoCustomProcessCallback**

| void setLocalVideoCustomProcessCallback | ([ITRTCVideoFrameCallback](https://www.tencentcloud.com/document/product/647/72271#9454c2f295e4e4519548382c4b6d868c) callback) |
| --- | --- |

#### .2 Set video data callback for third-party beauty filters.

After this callback is set, the SDK will call back the captured video frames through the ` callback ` you set and use them for further processing by a third-party beauty filter component. Then, the SDK will encode and send the processed video frames.

| Param | DESC |
| --- | --- |
| callback | : Custom preprocessing callback. For more information, please see [ITRTCVideoFrameCallback](https://www.tencentcloud.com/document/product/647/72271#9454c2f295e4e4519548382c4b6d868c) |

## setLocalVideoRenderCallback

**setLocalVideoRenderCallback**

| int setLocalVideoRenderCallback | ([TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) pixelFormat |
| --- | --- |
|  | [TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/72275#133a51a3a497d78c2b4d5de72ec7aaeb) bufferType |
|  | [ITRTCVideoRenderCallback](https://www.tencentcloud.com/document/product/647/72271#fce7830c6c3adc13fe5fa5da776a9da3) callback) |

#### Set the callback of custom rendering for local video.

After this callback is set, the SDK will skip its own rendering process and call back the captured data. Therefore, you need to complete image rendering on your own.

- You can call ` setLocalVideoRenderCallback(TRTCVideoPixelFormat_Unknown, TRTCVideoBufferType_Unknown, nullptr) ` to stop the callback.
- On iOS, macOS, and Windows, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) or [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) pixel format can be called back currently.
- On Android, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3), [TRTCVideoPixelFormat_RGBA32](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) or [TRTCVideoPixelFormat_Texture_2D](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) pixel format can be passed in currently.

| Param | DESC |
| --- | --- |
| bufferType | Specify video data structure type. |
| callback | Callback for custom rendering |
| pixelFormat | Specify the format of the pixel called back |

#### Return Desc:

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setRemoteVideoRenderCallback

**setRemoteVideoRenderCallback**

| int setRemoteVideoRenderCallback | (string userId |
| --- | --- |
|  | [TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) pixelFormat |
|  | [TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/72275#133a51a3a497d78c2b4d5de72ec7aaeb) bufferType |
|  | [ITRTCVideoRenderCallback](https://www.tencentcloud.com/document/product/647/72271#fce7830c6c3adc13fe5fa5da776a9da3) callback) |

#### Set the callback of custom rendering for remote video.

After this callback is set, the SDK will skip its own rendering process and call back the captured data. Therefore, you need to complete image rendering on your own.

- You can call ` setRemoteVideoRenderCallback(TRTCVideoPixelFormat_Unknown, TRTCVideoBufferType_Unknown, nullptr) ` to stop the callback.
- On iOS, macOS, and Windows, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) or [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) pixel format can be called back currently.
- On Android, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) , [TRTCVideoPixelFormat_RGBA32](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) or [TRTCVideoPixelFormat_Texture_2D](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3)pixel format can be passed in currently.

| Param | DESC |
| --- | --- |
| bufferType | Specify video data structure type. Only [TRTCVideoBufferType_Buffer](https://www.tencentcloud.com/document/product/647/72275#133a51a3a497d78c2b4d5de72ec7aaeb) is supported currently |
| callback | Callback for custom rendering |
| pixelFormat | Specify the format of the pixel called back |
| userId | remote user id |

> **Note**In actual use, you need to call ` startRemoteView(userid, nullptr) ` to get the video stream of the remote user first (set ` view ` to ` nullptr `); otherwise, there will be no data called back.

#### Return Desc:

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setAudioFrameCallback

**setAudioFrameCallback**

| int setAudioFrameCallback | ([ITRTCAudioFrameCallback](https://www.tencentcloud.com/document/product/647/72271#c83add42f0e7122e1149d522041a5af4) callback) |
| --- | --- |

#### Set custom audio data callback.

After this callback is set, the SDK will internally call back the audio data (in PCM format), including:

- onCapturedAudioFrame: callback of the audio data captured by the local mic
- [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/72271#7013577cbc775c66b7d94a1299b86a64): callback of the audio data captured by the local mic and preprocessed by the audio module
- [onPlayAudioFrame](https://www.tencentcloud.com/document/product/647/72271#e5b854ddfd36ca3dec95c5ec30a381e2): audio data from each remote user before audio mixing
- [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/72271#9e10a31ea56497b681f9c8fa7b36c52b): callback of the audio data that will be played back by the system after audio streams are mixed

> **Note**Setting the callback to null indicates to stop the custom audio callback, while setting it to a non-null value indicates to start the custom audio callback.

## setCapturedAudioFrameCallbackFormat

**setCapturedAudioFrameCallbackFormat**

| int setCapturedAudioFrameCallbackFormat | ([TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/72275#352b0878415e79fcd48d9027fab3f683) format) |
| --- | --- |

#### Set the callback format of audio frames captured by local mic.

This API is used to set the ` AudioFrame ` format called back by onCapturedAudioFrame:

- sampleRate: sample rate. Valid values: 16000, 32000, 44100, 48000
- channel: number of channels (if stereo is used, data is interwoven). Valid values: 1: mono channel; 2: dual channel
- samplesPerCall: number of sample points, which defines the frame length of the callback data. The frame length must be an integer multiple of 10 ms.

If you want to calculate the callback frame length in milliseconds, the formula for converting the number of milliseconds into the number of sample points is as follows: number of sample points = number of milliseconds * sample rate / 1000

For example, if you want to call back the data of 20 ms frame length with 48000 sample rate, then the number of sample points should be entered as ` 960 = 20 * 48000 / 1000 `.

Note that the frame length of the final callback is in bytes, and the calculation formula for converting the number of sample points into the number of bytes is as follows: ` number of bytes = number of sample points * number of channels * 2 (bit width) `

For example, if the parameters are 48000 sample rate, dual channel, 20 ms frame length, and 960 sample points, then the number of bytes is ` 3840 = 960 * 2 * 2 `

| Param | DESC |
| --- | --- |
| format | Audio data callback format |

#### Return Desc:

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setLocalProcessedAudioFrameCallbackFormat

**setLocalProcessedAudioFrameCallbackFormat**

| int setLocalProcessedAudioFrameCallbackFormat | ([TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/72275#352b0878415e79fcd48d9027fab3f683) format) |
| --- | --- |

#### Set the callback format of preprocessed local audio frames.

This API is used to set the ` AudioFrame ` format called back by [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/72271#7013577cbc775c66b7d94a1299b86a64):

- sampleRate: sample rate. Valid values: 16000, 32000, 44100, 48000
- channel: number of channels (if stereo is used, data is interwoven). Valid values: 1: mono channel; 2: dual channel
- samplesPerCall: number of sample points, which defines the frame length of the callback data. The frame length must be an integer multiple of 10 ms.

If you want to calculate the callback frame length in milliseconds, the formula for converting the number of milliseconds into the number of sample points is as follows: ` number of sample points = number of milliseconds * sample rate / 1000 `.

For example, if you want to call back the data of 20 ms frame length with 48000 sample rate, then the number of sample points should be entered as ` 960 = 20 * 48000 / 1000 `.

Note that the frame length of the final callback is in bytes, and the calculation formula for converting the number of sample points into the number of bytes is as follows: ` number of bytes = number of sample points * number of channels * 2 (bit width) `.

For example, if the parameters are 48000 sample rate, dual channel, 20 ms frame length, and 960 sample points, then the number of bytes is ` 3840 = 960 * 2 * 2 `.

| Param | DESC |
| --- | --- |
| format | Audio data callback format |

#### Return Desc:

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setMixedPlayAudioFrameCallbackFormat

**setMixedPlayAudioFrameCallbackFormat**

| int setMixedPlayAudioFrameCallbackFormat | ([TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/72275#352b0878415e79fcd48d9027fab3f683) format) |
| --- | --- |

#### Set the callback format of audio frames to be played back by system.

This API is used to set the ` AudioFrame ` format called back by [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/72271#9e10a31ea56497b681f9c8fa7b36c52b):

- sampleRate: sample rate. Valid values: 16000, 32000, 44100, 48000
- channel: number of channels (if stereo is used, data is interwoven). Valid values: 1: mono channel; 2: dual channel
- samplesPerCall: number of sample points, which defines the frame length of the callback data. The frame length must be an integer multiple of 10 ms.

If you want to calculate the callback frame length in milliseconds, the formula for converting the number of milliseconds into the number of sample points is as follows: ` number of sample points = number of milliseconds * sample rate / 1000 `.

For example, if you want to call back the data of 20 ms frame length with 48000 sample rate, then the number of sample points should be entered as ` 960 = 20 * 48000 / 1000 `.

Note that the frame length of the final callback is in bytes, and the calculation formula for converting the number of sample points into the number of bytes is as follows: ` number of bytes = number of sample points * number of channels * 2 (bit width) `.

For example, if the parameters are 48000 sample rate, dual channel, 20 ms frame length, and 960 sample points, then the number of bytes is ` 3840 = 960 * 2 * 2 `.

| Param | DESC |
| --- | --- |
| format | Audio data callback format |

#### Return Desc:

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## sendCustomCmdMsg

**sendCustomCmdMsg**

| bool sendCustomCmdMsg | (int cmdId |
| --- | --- |
|  | byte[] data |
|  | int dataSize |
|  | bool reliable |
|  | bool ordered) |

#### Use UDP channel to send custom message to all users in room.

This API allows you to use TRTC's UDP channel to broadcast custom data to other users in the current room for signaling transfer.

Other users in the room can receive the message through the ` onRecvCustomCmdMsg ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431).

| Param | DESC |
| --- | --- |
| cmdID | Message ID. Value range: [1, 10] |
| data | Message to be sent. The maximum length of one single message is 1 KB. |
| ordered | Whether orderly sending is enabled, i.e., whether the data packets should be received in the same order in which they are sent; if so, a certain delay will be caused. |
| reliable | Whether reliable sending is enabled. Reliable sending can achieve a higher success rate but with a longer reception delay than unreliable sending. |

> **Note**1. Up to 30 messages can be sent per second to all users in the room (this is not supported for web and mini program currently. this limit is shared with [sendSEIMsg](https://www.tencentcloud.com/document/product/647/72270#2d918c3d0ef54d41bd5f5adcb62f63d6)).2. A packet can contain up to 1 KB of data; if the threshold is exceeded, the packet is very likely to be discarded by the intermediate router or server.(this limit is shared with [sendSEIMsg](https://www.tencentcloud.com/document/product/647/72270#2d918c3d0ef54d41bd5f5adcb62f63d6)).3. A client can send up to 16 KB of data in total per second.4. ` reliable ` and ` ordered ` must be set to the same value (` true ` or ` false `) and cannot be set to different values currently.5. We strongly recommend you set different ` cmdID ` values for messages of different types. This can reduce message delay when orderly sending is required.6. Currently only the anchor role is supported.

#### Return Desc:

true: sent the message successfully; false: failed to send the message.

## sendSEIMsg

**sendSEIMsg**

| bool sendSEIMsg | (byte[] data |
| --- | --- |
|  | int dataSize |
|  | int repeatCount) |

#### Use SEI channel to send custom message to all users in room.

This API allows you to use TRTC's SEI channel to broadcast custom data to other users in the current room for signaling transfer.

The header of a video frame has a header data block called SEI. This API works by embedding the custom signaling data you want to send in the SEI block and sending it together with the video frame.

Therefore, the SEI channel has a better compatibility than [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72270#20d4d41de96d8e2e6d2cf6499ea55171) as the signaling data can be transferred to the CSS CDN along with the video frame.

However, because the data block of the video frame header cannot be too large, we recommend you limit the size of the signaling data to only a few bytes when using this API.

The most common use is to embed the custom timestamp into video frames through this API so as to implement a perfect alignment between the message and video image (such as between the teaching material and video signal in the education scenario).

Other users in the room can receive the message through the ` onRecvSEIMsg ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431).

| Param | DESC |
| --- | --- |
| data | Data to be sent, which can be up to 1 KB (1,000 bytes) |
| repeatCount | Data sending count |

> **Note**This API has the following restrictions:1. The data will not be instantly sent after this API is called; instead, it will be inserted into the next video frame after the API call.2. Up to 30 messages can be sent per second to all users in the room (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72270#20d4d41de96d8e2e6d2cf6499ea55171)).3. Each packet can be up to 1 KB (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72270#20d4d41de96d8e2e6d2cf6499ea55171)). If a large amount of data is sent, the video bitrate will increase, which may reduce the video quality or even cause lagging.4. Each client can send up to 16 KB of data in total per second (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/72270#20d4d41de96d8e2e6d2cf6499ea55171)).5. If multiple times of sending is required (i.e., ` repeatCount ` > 1), the data will be inserted into subsequent ` repeatCount ` video frames in a row for sending, which will increase the video bitrate.6. If ` repeatCount ` is greater than 1, the data will be sent for multiple times, and the same message may be received multiple times in the [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/72271#10bd0c1f0010a55c27922dadd2723042) callback; therefore, deduplication is required.

#### Return Desc:

true: the message is allowed and will be sent with subsequent video frames; false: the message is not allowed to be sent

## startSpeedTest

**startSpeedTest**

| void startSpeedTest | ([TRTCSpeedTestParams](https://www.tencentcloud.com/document/product/647/72275#dd22aad94fc4b4773ca7323c7d34a1a7) testParams) |
| --- | --- |

#### Start network speed test (used before room entry).

| Param | DESC |
| --- | --- |
| params | speed test options |

> **Note**1. The speed measurement process will incur a small amount of basic service fees, See [Purchase Guide > Base Services](https://intl.cloud.tencent.com/document/product/647/34610?lang=en&pg=#basic-services).2. Please perform the Network speed test before room entry, because if performed after room entry, the test will affect the normal audio/video transfer, and its result will be inaccurate due to interference in the room.3. Only one network speed test task is allowed to run at the same time.

#### Return Desc:

interface call result, <0: failure

## stopSpeedTest

**stopSpeedTest**

#### Stop network speed test.

## getScriptVersion

**getScriptVersion**

#### Get SDK ScriptVersion information.

## getSDKVersion

**getSDKVersion**

#### Get SDK version information.

## setLogLevel

**setLogLevel**

| void setLogLevel | ([TRTCLogLevel](https://www.tencentcloud.com/document/product/647/72275#3b7ff44175cba4dd48e97aa8ac7b0b98) level) |
| --- | --- |

#### Set log output level.

| Param | DESC |
| --- | --- |
| level | For more information, please see [TRTCLogLevel](https://www.tencentcloud.com/document/product/647/72275#3b7ff44175cba4dd48e97aa8ac7b0b98). Default value: [TRTCLogLevelNone](https://www.tencentcloud.com/document/product/647/72275#3b7ff44175cba4dd48e97aa8ac7b0b98) |

## setConsoleEnabled

**setConsoleEnabled**

| void setConsoleEnabled | (bool enabled) |
| --- | --- |

#### Enable/Disable console log printing.

| Param | DESC |
| --- | --- |
| enabled | Specify whether to enable it, which is disabled by default |

## setLogCompressEnabled

**setLogCompressEnabled**

| void setLogCompressEnabled | (bool enabled) |
| --- | --- |

#### Enable/Disable local log compression.

If compression is enabled, the log size will significantly reduce, but logs can be read only after being decompressed by the Python script provided by Tencent Cloud.

If compression is disabled, logs will be stored in plaintext and can be read directly in Notepad, but will take up more storage capacity.

| Param | DESC |
| --- | --- |
| enabled | Specify whether to enable it, which is enabled by default |

## setLogDirPath

**setLogDirPath**

| void setLogDirPath | (string path) |
| --- | --- |

#### Set local log storage path.

You can use this API to change the default storage path of the SDK's local logs, which is as follows:

- Windows: C:/Users/[username]/AppData/Roaming/liteav/log, i.e., under ` %appdata%/liteav/log `.
- iOS or macOS: under ` sandbox Documents/log `.
- Android: under ` /app directory/files/log/liteav/ `.

| Param | DESC |
| --- | --- |
| path | Log storage path |

> **Note**Please be sure to call this API before all other APIs and make sure that the directory you specify exists and your application has read/write permissions of the directory.

## setLogCallback

**setLogCallback**

| void setLogCallback | ([ITRTCLogCallback](https://www.tencentcloud.com/document/product/647/72271#486f92ae649081ecfa3769fb441f77da) callback) |
| --- | --- |

#### Set log callback.

## callExperimentalAPI

**callExperimentalAPI**

| void callExperimentalAPI | (string jsonStr) |
| --- | --- |

#### Call experimental APIs.


---
*Source: [https://trtc.io/document/72270](https://trtc.io/document/72270)*
