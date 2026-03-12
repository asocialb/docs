# ITRTCCloud

Copyright (c) 2021 Tencent. All rights reserved.

Module:   TRTCCloud @ TXLiteAVSDK

Function: TRTC's main feature API

Version: 13.0

**ITRTCCloud**

## ITRTCCloud

| FuncList | DESC |
| --- | --- |
| [getTRTCShareInstance](https://www.tencentcloud.com/document/product/647/50770#d817d491e3ec85d6b2e5880e4f1d4309) | Create TRTCCloud instance (singleton mode). |
| [destroyTRTCShareInstance](https://www.tencentcloud.com/document/product/647/50770#5e76d84cc813399072e4fe50bfcc1663) | Terminate TRTCCloud instance (singleton mode). |
| [addCallback](https://www.tencentcloud.com/document/product/647/50770#1c3368fb92a2809a4095874c2980f68c) | Add TRTC event callback. |
| [removeCallback](https://www.tencentcloud.com/document/product/647/50770#8297cfe9383f11812f7ca3a917243b9e) | Remove TRTC event callback. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) | Enter room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/50770#3cdc249ad1953cdbfa83c93733f952fa) | Exit room. |
| [switchRole](https://www.tencentcloud.com/document/product/647/50770#97e4bd705285a3846d2dc78e21b27508) | Switch role. |
| [switchRole](https://www.tencentcloud.com/document/product/647/50770#22dff565faee8228972c631b87af4f2f) | Switch role(support permission credential). |
| [switchRoom](https://www.tencentcloud.com/document/product/647/50770#c1f8ee70eb0df8f09cc410243a5b86af) | Switch room. |
| [connectOtherRoom](https://www.tencentcloud.com/document/product/647/50770#b3e33b4e5c9bb2e3670895ecfffce7cc) | Request cross-room call. |
| [disconnectOtherRoom](https://www.tencentcloud.com/document/product/647/50770#54bb12e5c34ae35d6b5f5aad213dbb12) | Exit cross-room call. |
| [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/50770#1bd891d9afeb9021c825ab3d39da6fe7) | Set subscription mode (which must be set before room entry for it to take effect). |
| [createSubCloud](https://www.tencentcloud.com/document/product/647/50770#f553df5bb3471677a3f7806b4cd342d3) | Create room subinstance (for concurrent multi-room listen/watch). |
| [destroySubCloud](https://www.tencentcloud.com/document/product/647/50770#fbcb5d292c2ed3d07cf7999c9e6372eb) | Terminate room subinstance. |
| [updateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50770#9d234f56d6bfdca31ec9390aa5ddc055) | Change the upstream capability of the cross-room anchor in the current room. |
| [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a) | Publish a stream. |
| [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#311979ce8f747d30ba68eb412789fffd) | Modify publishing parameters. |
| [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#f4d187c5e85084e1f96efcea1b5e076a) | Stop publishing. |
| [startLocalPreview](https://www.tencentcloud.com/document/product/647/50770#66bab4d115291cba164b192ccb3c23a6) | Enable the preview image of local camera (mobile). |
| [startLocalPreview](https://www.tencentcloud.com/document/product/647/50770#b2fbbc7d82ce36ecf22c12c8b5d4d20d) | Enable the preview image of local camera (desktop). |
| [updateLocalView](https://www.tencentcloud.com/document/product/647/50770#d66402958ebe28555d63f02d4b5696e5) | Update the preview image of local camera. |
| [stopLocalPreview](https://www.tencentcloud.com/document/product/647/50770#57cfe4af12b1160ae4a904e65246d70f) | Stop camera preview. |
| [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50770#fbe283b224cacea70a96e4e445bebb43) | Pause/Resume publishing local video stream. |
| [setVideoMuteImage](https://www.tencentcloud.com/document/product/647/50770#904ba3a0c6e2344e322202b027361779) | Set placeholder image during local video pause. |
| [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) | Subscribe to remote user's video stream and bind video rendering control. |
| [updateRemoteView](https://www.tencentcloud.com/document/product/647/50770#995ab4d43dcb8917c4c3ddad4680a274) | Update remote user's video rendering control. |
| [stopRemoteView](https://www.tencentcloud.com/document/product/647/50770#fcdb436399a9ae9f60cdc2035d46d688) | Stop subscribing to remote user's video stream and release rendering control. |
| [stopAllRemoteView](https://www.tencentcloud.com/document/product/647/50770#9588d79047a0dbf0b25275e0dce1d206) | Stop subscribing to all remote users' video streams and release all rendering resources. |
| [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50770#5b3dc4a04f807ab8c106408450824394) | Pause/Resume subscribing to remote user's video stream. |
| [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/50770#2a62b8d0ae0e1995c725a399e8447726) | Pause/Resume subscribing to all remote users' video streams. |
| [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50770#0450f3674968a78b9a53a17865aa5277) | Set the encoding parameters of video encoder. |
| [setNetworkQosParam](https://www.tencentcloud.com/document/product/647/50770#3c9dea653a6a1aacc0084bdeb31a4b4e) | Set network quality control parameters. |
| [setLocalRenderParams](https://www.tencentcloud.com/document/product/647/50770#838ae756cbe662c01b633c4c1de38e3f) | Set the rendering parameters of local video image. |
| [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50770#e15268ff41c7c2ae0a8f79f8e5fcd8df) | Set the rendering mode of remote video image. |
| [enableSmallVideoStream](https://www.tencentcloud.com/document/product/647/50770#6d590cec5da031e940cc0e79f7deb40a) | Enable dual-channel encoding mode with big and small images. |
| [setRemoteVideoStreamType](https://www.tencentcloud.com/document/product/647/50770#b8e73cb59140849f57bf432752b555c5) | Switch the big/small image of specified remote user. |
| [snapshotVideo](https://www.tencentcloud.com/document/product/647/50770#62993ca322ad8742a427b13c188b0d6a) | Screencapture video. |
| [setGravitySensorAdaptiveMode](https://www.tencentcloud.com/document/product/647/50770#36c8f5ab3ebfd6c7a627ea94dc700bb7) | Set the adaptation mode of gravity sensing (version 11.7 and above). |
| [startLocalAudio](https://www.tencentcloud.com/document/product/647/50770#37f11bf81ac7eef6af030790d31bc86d) | Enable local audio capturing and publishing. |
| [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50770#02929bb6693afbf66cae64a9bf7d34e5) | Stop local audio capturing and publishing. |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/50770#a44ebefc5b2a3f560cd8bed5a4e43a89) | Pause/Resume publishing local audio stream. |
| [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/50770#457b7fc9a9cec63b20e3ab012848d235) | Pause/Resume playing back remote audio stream. |
| [muteAllRemoteAudio](https://www.tencentcloud.com/document/product/647/50770#8ef3fc9f90aeec724c19ac6ef206f3a0) | Pause/Resume playing back all remote users' audio streams. |
| [setRemoteAudioVolume](https://www.tencentcloud.com/document/product/647/50770#d6f3ba48b9c4152e236bb8abde5b905c) | Set the audio playback volume of remote user. |
| [setAudioCaptureVolume](https://www.tencentcloud.com/document/product/647/50770#11ea595838b23b558bb341291f26b3c1) | Set the capturing volume of local audio. |
| [getAudioCaptureVolume](https://www.tencentcloud.com/document/product/647/50770#429105ee6469721d8df148521a9fa913) | Get the capturing volume of local audio. |
| [setAudioPlayoutVolume](https://www.tencentcloud.com/document/product/647/50770#4d0fa5a71bb58e3f19e3cb68914e3118) | Set the playback volume of remote audio. |
| [getAudioPlayoutVolume](https://www.tencentcloud.com/document/product/647/50770#273d881897fb46ecceea47a3728fb897) | Get the playback volume of remote audio. |
| [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50770#1e7a0c85189378920f2e2a446d897907) | Enable volume reminder. |
| [startAudioRecording](https://www.tencentcloud.com/document/product/647/50770#cbbd6ff99965181d81f1cacda8245d17) | Start audio recording. |
| [stopAudioRecording](https://www.tencentcloud.com/document/product/647/50770#d51e817ea322c0da1817c26980fe69d2) | Stop audio recording. |
| [startLocalRecording](https://www.tencentcloud.com/document/product/647/50770#addffbd3c894aca3c6a8efa01936a086) | Start local media recording. |
| [stopLocalRecording](https://www.tencentcloud.com/document/product/647/50770#2e45348447589f72e1c44ae10e0f4de1) | Stop local media recording. |
| [setRemoteAudioParallelParams](https://www.tencentcloud.com/document/product/647/50770#ed840060fbe647b947bb4cd7ab5b9f66) | Set the parallel strategy of remote audio streams. |
| [enable3DSpatialAudioEffect](https://www.tencentcloud.com/document/product/647/50770#d82bbde29607863c8954873c5c788abf) | Enable 3D spatial effect. |
| [updateSelf3DSpatialPosition](https://www.tencentcloud.com/document/product/647/50770#a3dd536fa3cf5e46ee43fc953b35fe5c) | Update self position and orientation for 3D spatial effect. |
| [updateRemote3DSpatialPosition](https://www.tencentcloud.com/document/product/647/50770#6ceb01aa07b88b0899116da44f6a4318) | Update the specified remote user's position for 3D spatial effect. |
| [set3DSpatialReceivingRange](https://www.tencentcloud.com/document/product/647/50770#a4043099f43eb1cc8d1e34cb20e4a9da) | Set the maximum 3D spatial attenuation range for userId's audio stream. |
| [*getDeviceManager](https://www.tencentcloud.com/document/product/647/50770#501064d6605beb476dc25f7639a956c0) | Get device management class (TXDeviceManager). |
| [getBeautyManager](https://www.tencentcloud.com/document/product/647/50770#059bcc9a1996feee7a0e6b7b293da5e1) | Get beauty filter management class (TXBeautyManager). |
| [setWaterMark](https://www.tencentcloud.com/document/product/647/50770#c8cbf50686954f1ea85a3dd88afe853e) | Add watermark. |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/50770#59d65371953ec37eef801d6207d6111a) | Get sound effect management class (TXAudioEffectManager). |
| [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50770#792556646f98fdbb0eb9e4b7fb12c42b) | Enable system audio capturing(iOS not supported). |
| [stopSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50770#afed828e50c50eed29f3c14790384353) | Stop system audio capturing(iOS not supported). |
| [setSystemAudioLoopbackVolume](https://www.tencentcloud.com/document/product/647/50770#70ff72cab273dfc306cda1502ab1dcfd) | Set the volume of system audio capturing. |
| [startScreenCapture](https://www.tencentcloud.com/document/product/647/50770#94be1579f497befa5e6450725b4f1a5c) | Start screen sharing. |
| [stopScreenCapture](https://www.tencentcloud.com/document/product/647/50770#f509d7682570422562b2dce3dca474be) | Stop screen sharing. |
| [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/50770#1403f1a194ad64c9c1edefe09758990e) | Pause screen sharing. |
| [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/50770#d8717bb76a81445b956b856befa37a2a) | Resume screen sharing. |
| [getScreenCaptureSources](https://www.tencentcloud.com/document/product/647/50770#f839d347fc9f9cc87e132274abfcb634) | Enumerate shareable screens and windows (for desktop systems only). |
| [selectScreenCaptureTarget](https://www.tencentcloud.com/document/product/647/50770#beecf3ba98f69960536998355044dc8e) | Select the screen or window to share (for desktop systems only). |
| [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50770#dd9e46a8eafd30b0f054a2c1e720868c) | Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems). |
| [setSubStreamMixVolume](https://www.tencentcloud.com/document/product/647/50770#e685a0959faf64c1046dfe6d6365a196) | Set the audio mixing volume of screen sharing (for desktop systems only). |
| [addExcludedShareWindow](https://www.tencentcloud.com/document/product/647/50770#6707156b336b03b27ce942de77228d06) | Add specified windows to the exclusion list of screen sharing (for desktop systems only). |
| [removeExcludedShareWindow](https://www.tencentcloud.com/document/product/647/50770#bc5301641166e16b25bd750dbbba4a03) | Remove specified windows from the exclusion list of screen sharing (for desktop systems only). |
| [removeAllExcludedShareWindow](https://www.tencentcloud.com/document/product/647/50770#4c4fff59d9fdc3b1c91f7c5600a98da9) | Remove all windows from the exclusion list of screen sharing (for desktop systems only). |
| [addIncludedShareWindow](https://www.tencentcloud.com/document/product/647/50770#4ddb37e3f6db52046f22ecf4f7545d69) | Add specified windows to the inclusion list of screen sharing (for desktop systems only). |
| [removeIncludedShareWindow](https://www.tencentcloud.com/document/product/647/50770#e5db118d6d628ab857350c581c4209e3) | Remove specified windows from the inclusion list of screen sharing (for desktop systems only). |
| [removeAllIncludedShareWindow](https://www.tencentcloud.com/document/product/647/50770#4b56a6dacb8557e8cce05e5902c86cf1) | Remove all windows from the inclusion list of screen sharing (for desktop systems only). |
| [enableCustomVideoCapture](https://www.tencentcloud.com/document/product/647/50770#6d0ee8e74a483f50e6b3d496d07bfba8) | Enable/Disable custom video capturing mode. |
| [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50770#ab662864256180ad7ecf66eaa49bb70f) | Deliver captured video frames to SDK. |
| [enableCustomAudioCapture](https://www.tencentcloud.com/document/product/647/50770#58743ee83debf8d16d151efac7a65aa8) | Enable custom audio capturing mode. |
| [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50770#583cf9547ea33e472ad0928fe947e9c5) | Deliver captured audio data to SDK. |
| [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50770#a49d9c3532c8f6b32819f5df5d30606f) | Enable/Disable custom audio track. |
| [mixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50770#69487e429ff40d9c279952c091fa6bba) | Mix custom audio track into SDK. |
| [setMixExternalAudioVolume](https://www.tencentcloud.com/document/product/647/50770#fb05be151eef543b19638ca18efb54e0) | Set the publish volume and playback volume of mixed custom audio track. |
| [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50770#423a10754c9cf276a8c0374acd8aee7e) | Generate custom capturing timestamp. |
| [enableLocalVideoCustomProcess](https://www.tencentcloud.com/document/product/647/50770#45ef27c2bb212079555c7af4c5ea1f28) | .1 Enable third-party beauty filters in video. |
| [setLocalVideoCustomProcessCallback](https://www.tencentcloud.com/document/product/647/50770#357265a655016bf35864a947073e7ea4) | .2 Set video data callback for third-party beauty filters. |
| [setLocalVideoRenderCallback](https://www.tencentcloud.com/document/product/647/50770#58ead030937b17839c952192ba2810fb) | Set the callback of custom rendering for local video. |
| [setRemoteVideoRenderCallback](https://www.tencentcloud.com/document/product/647/50770#43400f581166514bd487a4b0753e83f8) | Set the callback of custom rendering for remote video. |
| [setAudioFrameCallback](https://www.tencentcloud.com/document/product/647/50770#4c77e17cfee9b4e79aa62623af54698c) | Set custom audio data callback. |
| [setCapturedAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50770#8bc42bf3a78da75037d9df72356b3d6e) | Set the callback format of audio frames captured by local mic. |
| [setLocalProcessedAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50770#a6482491906e30e8fbe4ff17990450b1) | Set the callback format of preprocessed local audio frames. |
| [setMixedPlayAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50770#f803a008344b6cac337a65da35d1c428) | Set the callback format of audio frames to be played back by system. |
| [enableCustomAudioRendering](https://www.tencentcloud.com/document/product/647/50770#39ec05a397f4ebb398f3655679072245) | Enabling custom audio playback. |
| [getCustomAudioRenderingFrame](https://www.tencentcloud.com/document/product/647/50770#7c58a64f102323c6420c0acdbc4d6c4a) | Getting playable audio data. |
| [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50770#b39e25426586d217f2fdf44b7777b47c) | Use UDP channel to send custom message to all users in room. |
| [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50770#419654e5edfe1587ac98d7d43a47c744) | Use SEI channel to send custom message to all users in room. |
| [startSpeedTest](https://www.tencentcloud.com/document/product/647/50770#ad6d84be7e3d8b20fae6b5f6f56d65f0) | Start network speed test (used before room entry). |
| [stopSpeedTest](https://www.tencentcloud.com/document/product/647/50770#4ff1163b6d7c4ee154038619e97d93fd) | Stop network speed test. |
| [getSDKVersion](https://www.tencentcloud.com/document/product/647/50770#2c99e9c9fe63339640d3aef0180edc8d) | Get SDK version information. |
| [setLogLevel](https://www.tencentcloud.com/document/product/647/50770#ccccdd35beb94f8c7df9b8dcc36b035d) | Set log output level. |
| [setConsoleEnabled](https://www.tencentcloud.com/document/product/647/50770#0dd9b9a5a22e32d304a2bedff1207a71) | Enable/Disable console log printing. |
| [setLogCompressEnabled](https://www.tencentcloud.com/document/product/647/50770#a359474ff7de4e260f7028112593d48c) | Enable/Disable local log compression. |
| [setLogDirPath](https://www.tencentcloud.com/document/product/647/50770#7d9cfe89693ba84820a16f8bb26f9be0) | Set local log storage path. |
| [setLogCallback](https://www.tencentcloud.com/document/product/647/50770#b98b09e7a09ce913c98f38f683281268) | Set log callback. |
| [showDebugView](https://www.tencentcloud.com/document/product/647/50770#39079784c81c16dcb5e16ab24ee2f8dc) | Display dashboard. |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/50770#3e746d07f491f672c1dce2622bb97d07) | Call experimental APIs. |
| [enablePayloadPrivateEncryption](https://www.tencentcloud.com/document/product/647/50770#925d04bb9e69e658644d5ee54f863977) | Enable or disable private encryption of media streams. |

## getTRTCShareInstance

**getTRTCShareInstance**

| ITRTCCloud* getTRTCShareInstance | (void *context) |
| --- | --- |

**Create TRTCCloud instance (singleton mode).**

| Param | DESC |
| --- | --- |
| context | It is only applicable to the Android platform. The SDK internally converts it into the ` ApplicationContext ` of Android to call the Android system API. |

> **Note**1. If you use ` delete ITRTCCloud* `, a compilation error will occur. Please use [destroyTRTCShareInstance](https://www.tencentcloud.com/document/product/647/50770#5e76d84cc813399072e4fe50bfcc1663) to release the object pointer.2. On Windows, macOS, or iOS, please call the ` getTRTCShareInstance() ` API.3. On Android, please call the ` getTRTCShareInstance(void *context) ` API.

## destroyTRTCShareInstance

**destroyTRTCShareInstance**

**Terminate TRTCCloud instance (singleton mode).**

## addCallback

**addCallback**

| void addCallback | ([ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33)* callback) |
| --- | --- |

**Add TRTC event callback.**

You can use [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33) to get various event notifications from the SDK, such as error codes, warning codes, and audio/video status parameters.

## removeCallback

**removeCallback**

| void removeCallback | ([ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33)* callback) |
| --- | --- |

**Remove TRTC event callback.**

## enterRoom

**enterRoom**

| void enterRoom | (const [TRTCParams](https://www.tencentcloud.com/document/product/647/50775#a1de1e93c6cfc6be81dd4152b9e4c190)& param |
| --- | --- |
|  | [TRTCAppScene](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) scene) |

**Enter room.**

All TRTC users need to enter a room before they can "publish" or "subscribe to" audio/video streams. "Publishing" refers to pushing their own streams to the cloud, and "subscribing to" refers to pulling the streams of other users in the room from the cloud.

When calling this API, you need to specify your application scenario ([TRTCAppScene](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)) to get the best audio/video transfer experience. We provide the following four scenarios for your choice:

- [TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1):

Video call scenario. Use cases: [one-to-one video call], [video conferencing with up to 300 participants], [online medical diagnosis], [small class], [video interview], etc.

In this scenario, each room supports up to 300 concurrent online users, and up to 50 of them can speak simultaneously.

- [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1):

Audio call scenario. Use cases: [one-to-one audio call], [audio conferencing with up to 300 participants], [audio chat], [online Werewolf], etc.

In this scenario, each room supports up to 300 concurrent online users, and up to 50 of them can speak simultaneously.

- [TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1):

Live streaming scenario. Use cases: [low-latency video live streaming], [interactive classroom for up to 100,000 participants], [live video competition], [video dating room], [remote training], [large-scale conferencing], etc.

In this scenario, each room supports up to 100,000 concurrent online users, but you should specify the user roles: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b)) or audience ([TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b)).

- [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1):

Audio chat room scenario. Use cases: [Clubhouse], [online karaoke room], [music live room], [FM radio], etc.

In this scenario, each room supports up to 100,000 concurrent online users, but you should specify the user roles: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b)) or audience ([TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b)).

After calling this API, you will receive the ` onEnterRoom(result) ` callback from [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33):

- If room entry succeeded, the ` result ` parameter will be a positive number (` result ` > 0), indicating the time in milliseconds (ms) between function call and room entry.
- If room entry failed, the ` result ` parameter will be a negative number (` result ` < 0), indicating the [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384) for room entry failure.

| Param | DESC |
| --- | --- |
| param | Room entry parameter, which is used to specify the user's identity, role, authentication credentials, and other information. For more information, please see [TRTCParams](https://www.tencentcloud.com/document/product/647/50775#a1de1e93c6cfc6be81dd4152b9e4c190). |
| scene | Application scenario, which is used to specify the use case. The same [TRTCAppScene](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) should be configured for all users in the same room. |

> **Note**1. If ` scene ` is specified as [TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1), you must use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50775#a1de1e93c6cfc6be81dd4152b9e4c190) to specify the role of the current user in the room.2. The same ` scene ` should be configured for all users in the same room.3. Please try to ensure that [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) and [exitRoom](https://www.tencentcloud.com/document/product/647/50770#3cdc249ad1953cdbfa83c93733f952fa) are used in pair; that is, please make sure that "the previous room is exited before the next room is entered"; otherwise, many issues may occur.

## exitRoom

**exitRoom**

**Exit room.**

Calling this API will allow the user to leave the current audio or video room and release the camera, mic, speaker, and other device resources.

After resources are released, the SDK will use the ` onExitRoom() ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33) to notify you.

If you need to call [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) again or switch to the SDK of another provider, we recommend you wait until you receive the [onExitRoom](https://www.tencentcloud.com/document/product/647/50771#a80925fbd52d416a44f8c29f48d08c7a) callback, so as to avoid the problem of the camera or mic being occupied.

## switchRole

**switchRole**

| void switchRole | ([TRTCRoleType](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b) role) |
| --- | --- |

**Switch role.**

This API is used to switch the user role between ` anchor ` and ` audience `.

As video live rooms and audio chat rooms need to support an audience of up to 100,000 concurrent online users, the rule "only anchors can publish their audio/video streams" has been set. Therefore, when some users want to publish their streams (so that they can interact with anchors), they need to switch their role to "anchor" first.

You can use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50775#a1de1e93c6cfc6be81dd4152b9e4c190) during room entry to specify the user role in advance or use the ` switchRole ` API to switch roles after room entry.

| Param | DESC |
| --- | --- |
| role | Role, which is ` anchor ` by default: [TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b): anchor, who can publish their audio/video streams. Up to 50 anchors are allowed to publish streams at the same time in one room. [TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b): audience, who cannot publish their audio/video streams, but can only watch streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/50770#97e4bd705285a3846d2dc78e21b27508). One room supports an audience of up to 100,000 concurrent online users. |

> **Note**1. This API is only applicable to two scenarios: live streaming ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)) and audio chat room ([TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)).2. If the ` scene ` you specify in [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) is [TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1), please do not call this API.

## switchRole

**switchRole**

| void switchRole | ([TRTCRoleType](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b) role |
| --- | --- |
|  | const char* privateMapKey) |

**Switch role(support permission credential).**

This API is used to switch the user role between ` anchor ` and ` audience `.

As video live rooms and audio chat rooms need to support an audience of up to 100,000 concurrent online users, the rule "only anchors can publish their audio/video streams" has been set. Therefore, when some users want to publish their streams (so that they can interact with anchors), they need to switch their role to "anchor" first.

You can use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50775#a1de1e93c6cfc6be81dd4152b9e4c190) during room entry to specify the user role in advance or use the ` switchRole ` API to switch roles after room entry.

| Param | DESC |
| --- | --- |
| privateMapKey | Permission credential used for permission control. If you want only users with the specified ` userId ` values to enter a room or push streams, you need to use ` privateMapKey ` to restrict the permission. We recommend you use this parameter only if you have high security requirements. For more information, please see [Enabling Advanced Permission Control](https://www.tencentcloud.com/document/product/647/35157). |
| role | Role, which is ` anchor ` by default: [TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b): anchor, who can publish their audio/video streams. Up to 50 anchors are allowed to publish streams at the same time in one room. [TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50775#874dbd6062bbf1384648ca9f9054aa5b): audience, who cannot publish their audio/video streams, but can only watch streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/50770#97e4bd705285a3846d2dc78e21b27508). One room supports an audience of up to 100,000 concurrent online users. |

> **Note**1. This API is only applicable to two scenarios: live streaming ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)) and audio chat room ([TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1)).2. If the ` scene ` you specify in [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) is [TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50775#50498dba914e98bc767b83dc0c72a0a1), please do not call this API.

## switchRoom

**switchRoom**

| void switchRoom | (const [TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/50775#d43f5dc42762839497bd8586ac2091e3)& config) |
| --- | --- |

**Switch room.**

This API is used to quickly switch a user from one room to another.

- If the user's role is ` audience `, calling this API is equivalent to ` exitRoom ` (current room) + ` enterRoom ` (new room).
- If the user's role is ` anchor `, the API will retain the current audio/video publishing status while switching the room; therefore, during the room switch, camera preview and sound capturing will not be interrupted.

This API is suitable for the online education scenario where the supervising teacher can perform fast room switch across multiple rooms. In this scenario, using ` switchRoom ` can get better smoothness and use less code than ` exitRoom + enterRoom `.

The API call result will be called back through ` onSwitchRoom(errCode, errMsg) ` in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

| Param | DESC |
| --- | --- |
| config | Room parameter. For more information, please see [TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/50775#d43f5dc42762839497bd8586ac2091e3). |

> **Note**Due to the requirement for compatibility with legacy versions of the SDK, the ` config ` parameter contains both ` roomId ` and ` strRoomId ` parameters. You should pay special attention as detailed below when specifying these two parameters:1. If you decide to use ` strRoomId `, then set ` roomId ` to 0. If both are specified, ` roomId ` will be used.2. All rooms need to use either ` strRoomId ` or ` roomId ` at the same time. They cannot be mixed; otherwise, there will be many unexpected bugs.

## connectOtherRoom

**connectOtherRoom**

| void connectOtherRoom | (const char* param) |
| --- | --- |

**Request cross-room call.**

By default, only users in the same room can make audio/video calls with each other, and the audio/video streams in different rooms are isolated from each other.

However, you can publish the audio/video streams of an anchor in another room to the current room by calling this API. At the same time, this API will also publish the local audio/video streams to the target anchor's room.

In other words, you can use this API to share the audio/video streams of two anchors in two different rooms, so that the audience in each room can watch the streams of these two anchors. This feature can be used to implement anchor competition.

The result of requesting cross-room call will be returned through the [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50771#69534513bb766ecb024b4b7e475d5ddd) callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

For example, after anchor A in room "101" uses ` connectOtherRoom() ` to successfully call anchor B in room "102":

- All users in room "101" will receive the ` onRemoteUserEnterRoom(B) ` and ` onUserVideoAvailable(B,true) ` event callbacks of anchor B; that is, all users in room "101" can subscribe to the audio/video streams of anchor B.
- All users in room "102" will receive the ` onRemoteUserEnterRoom(A) ` and ` onUserVideoAvailable(A,true) ` event callbacks of anchor A; that is, all users in room "102" can subscribe to the audio/video streams of anchor A.

![](https://qcloudimg.tencent-cloud.cn/raw/c5e6c72fc163ad5c0b6b7b00e1da55b5.png)

For compatibility with subsequent extended fields for cross-room call, parameters in JSON format are used currently.

Case 1: numeric room ID

If anchor A in room "101" wants to co-anchor with anchor B in room "102", then anchor A needs to pass in {"roomId": 102, "userId": "userB"} when calling this API.

Below is the sample code:

```
  Json::Value jsonObj;  jsonObj["roomId"] = 102;  jsonObj["userId"] = "userB";  Json::FastWriter writer;  std::string params = writer.write(jsonObj);  trtc.connectOtherRoom(params.c_str());
```

Case 2: string room ID

If you use a string room ID, please be sure to replace the ` roomId ` in JSON with ` strRoomId `, such as ` {"strRoomId": "102", "userId": "userB"} `

Below is the sample code:

```
  Json::Value jsonObj;  jsonObj["strRoomId"] = "102";  jsonObj["userId"] = "userB";  Json::FastWriter writer;  std::string params = writer.write(jsonObj);  trtc.connectOtherRoom(params.c_str());
```

| Param | DESC |
| --- | --- |
| param | You need to pass in a string parameter in JSON format: ` roomId ` represents the room ID in numeric format, ` strRoomId ` represents the room ID in string format, and ` userId ` represents the user ID of the target anchor. |

## disconnectOtherRoom

**disconnectOtherRoom**

**Exit cross-room call.**

The result will be returned through the ` onDisconnectOtherRoom() ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

## setDefaultStreamRecvMode

**setDefaultStreamRecvMode**

| void setDefaultStreamRecvMode | (bool autoRecvAudio |
| --- | --- |
|  | bool autoRecvVideo) |

**Set subscription mode (which must be set before room entry for it to take effect).**

You can switch between the "automatic subscription" and "manual subscription" modes through this API:

- Automatic subscription: this is the default mode, where the user will immediately receive the audio/video streams in the room after room entry, so that the audio will be automatically played back, and the video will be automatically decoded (you still need to bind the rendering control through the ` startRemoteView ` API).
- Manual subscription: after room entry, the user needs to manually call the [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) API to start subscribing to and decoding the video stream and call the [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/50770#457b7fc9a9cec63b20e3ab012848d235) (false) API to start playing back the audio stream.

In most scenarios, users will subscribe to the audio/video streams of all anchors in the room after room entry. Therefore, TRTC adopts the automatic subscription mode by default in order to achieve the best "instant streaming experience".

In your application scenario, if there are many audio/video streams being published at the same time in each room, and each user only wants to subscribe to 1â2 streams of them, we recommend you use the "manual subscription" mode to reduce the traffic costs.

| Param | DESC |
| --- | --- |
| autoRecvAudio | true: automatic subscription to audio; false: manual subscription to audio by calling ` muteRemoteAudio(false) `. Default value: true |
| autoRecvVideo | true: automatic subscription to video; false: manual subscription to video by calling ` startRemoteView `. Default value: true |

> **Note**1. The configuration takes effect only if this API is called before room entry (enterRoom).2. In the automatic subscription mode, if the user does not call [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) to subscribe to the video stream after room entry, the SDK will automatically stop subscribing to the video stream in order to reduce the traffic consumption.

## createSubCloud

**createSubCloud**

**Create room subinstance (for concurrent multi-room listen/watch).**

` TRTCCloud ` was originally designed to work in the singleton mode, which limited the ability to watch concurrently in multiple rooms.

By calling this API, you can create multiple ` TRTCCloud ` instances, so that you can enter multiple different rooms at the same time to listen/watch audio/video streams.

However, it should be noted that your ability to publish audio and video streams in multiple ` TRTCCloud ` instances will be limited.

This feature is mainly used in the "super small class" use case in the online education scenario to break the limit that "only up to 50 users can publish their audio/video streams simultaneously in one TRTC room".

Below is the sample code:

```
    //In the small room that needs interaction, enter the room as an anchor and push audio and video streams    ITRTCCloud *mainCloud = getTRTCShareInstance();    TRTCParams mainParams;    //Fill your params    mainParams.role = TRTCRoleAnchor;    mainCloud->enterRoom(mainParams, TRTCAppSceneLIVE);    //...    mainCloud->startLocalAudio(TRTCAudioQualityDefault);    mainCloud->startLocalPreview(renderView);        //In the large room that only needs to watch, enter the room as an audience and pull audio and video streams    ITRTCCloud *subCloud = mainCloud->createSubCloud();    TRTCParams subParams;    //Fill your params    subParams.role = TRTCRoleAudience;    subCloud->enterRoom(subParams, TRTCAppSceneLIVE);    //...    subCloud->startRemoteView(userId, TRTCVideoStreamTypeBig, renderView);    //...    //Exit from new room and release it.    subCloud->exitRoom();    mainCloud->destroySubCloud(subCloud);
```

> **Note**1. The same user can enter multiple rooms with different ` roomId ` values by using the same ` userId `.2. Two devices cannot use the same ` userId ` to enter the same room with a specified ` roomId `.3. You can set [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33) separately for different instances to get their own event notifications.4. The same user can push streams in multiple ` TRTCCloud ` instances at the same time, and can also call APIs related to local audio/video in the sub instance. But need to pay attention to: Audio needs to be collected by the microphone or custom data at the same time in all instances, and the result of API calls related to the audio device will be based on the last time; The result of camera-related API call will be based on the last time: [startLocalPreview](https://www.tencentcloud.com/document/product/647/50770#66bab4d115291cba164b192ccb3c23a6).

**Return Desc:**

` TRTCCloud ` subinstance

## destroySubCloud

**destroySubCloud**

| void destroySubCloud | ([ITRTCCloud](https://www.tencentcloud.com/document/product/647/50770#6bfd6872d692884609319ec1555b84b7) *subCloud) |
| --- | --- |

**Terminate room subinstance.**

| Param | DESC |
| --- | --- |
| subCloud |  |

## updateOtherRoomForwardMode

**updateOtherRoomForwardMode**

| void updateOtherRoomForwardMode | (const char* param) |
| --- | --- |

**Change the upstream capability of the cross-room anchor in the current room.**

By default, after calling the [connectOtherRoom](https://www.tencentcloud.com/document/product/647/50770#b3e33b4e5c9bb2e3670895ecfffce7cc) API to make a cross-room call with an anchor in another room, all users in the current room will receive the audio/video streams published by that anchor.

You can use this API to limit the upstream capability of the cross-room anchor in the current room, and prohibit or allow the cross-room anchor to publish audio/video/sub-stream. This behavior will affect all users in the room.

After disabling a certain upstream capability of the cross-room anchor, all users in the current room will no longer receive the corresponding audio/video stream, and cannot subscribe to the corresponding audio/video.

Note that this API can only be called by the anchor who is conducting the cross-room call, and the restrictions set by this API will be reset when the cross-room call is interrupted or the corresponding anchor leaves the room.

The result of calling this API will be returned through the ` onUpdateOtherRoomForwardMode() ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

For example, in room "101", there is anchor A and audience B, and in room "102", there is anchor C who publishes audio/video streams normally. Anchor A calls ` connectOtherRoom() ` to make a cross-room call with anchor C.

- At this time, both anchor A and audience B will receive the ` onRemoteUserEnterRoom(C) `, ` onUserVideoAvailable(C,true) `, and ` onUserAudioAvailable(C,true) ` event callbacks, and can subscribe to the audio/video streams of anchor C.

Later, anchor A calls this API to disable the audio publishing capability of anchor C in the current room.

- After that, the audio stream of anchor C will no longer be published to room "101", and both anchor A and audience B will receive the ` onUserAudioAvailable(C,false) ` event callback, and cannot subscribe to the audio stream of anchor C by calling ` muteRemoteAudio(C,false) `.
- The video stream of anchor C will not be affected. The other audience members in Room 102 will not be affected and can subscribe to the audio stream of anchor C normally.

For compatibility with subsequent extended fields for this call, parameters in JSON format are used currently.

Case 1: numeric room ID

```
{  "roomId":102,  "userId":"userC",  "muteAudio":false,  "muteVideo":true,  "muteSubStream":false}
```

Case 2: string room ID

```
{  "strRoomId":"102",  "userId":"userC",  "muteAudio":false,  "muteVideo":true,  "muteSubStream":false}
```

| Param | DESC |
| --- | --- |
| param | You need to pass in a string parameter in JSON format: ` roomId ` represents the room ID in numeric format, ` strRoomId ` represents the room ID in string format, and ` userId ` represents the user ID of the target anchor. ` muteAudio `, ` muteVideo ` and ` muteSubStream ` are optional, representing whether to prohibit or allow the cross-room anchor to publish audio/video/sub-stream. |

## startPublishMediaStream

**startPublishMediaStream**

| void startPublishMediaStream | ([TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50775#e106259cbc7f1cff297f52931b7e7c49) * target |
| --- | --- |
|  | [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50775#22718fe81d94d21ec895cbc11820c726) * params |
|  | [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50775#7ddba434412d83f9aa8f34b1bb36b166) * config) |

**Publish a stream.**

After this API is called, the TRTC server will relay the stream of the local user to a CDN (after transcoding or without transcoding), or transcode and publish the stream to a TRTC room.

You can use the [TRTCPublishMode](https://www.tencentcloud.com/document/product/647/50775#064db271e894d12e1e3ad63bbb1677fb) parameter in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50775#e106259cbc7f1cff297f52931b7e7c49) to specify the publishing mode.

| Param | DESC |
| --- | --- |
| config | The On-Cloud MixTranscoding settings. This parameter is invalid in the relay-to-CDN mode. It is required if you transcode and publish the stream to a CDN or to a TRTC room. For details, see [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50775#7ddba434412d83f9aa8f34b1bb36b166). |
| params | The encoding settings. This parameter is required if you transcode and publish the stream to a CDN or to a TRTC room. If you relay to a CDN without transcoding, to improve the relaying stability and playback compatibility, we also recommend you set this parameter. For details, see [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50775#22718fe81d94d21ec895cbc11820c726). |
| target | The publishing destination. You can relay the stream to a CDN (after transcoding or without transcoding) or transcode and publish the stream to a TRTC room. For details, see [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50775#e106259cbc7f1cff297f52931b7e7c49). |

> **Note**1. The SDK will send a task ID to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#886b2dee59842d22542b673febbd5549) callback.2. You can start a publishing task only once and cannot initiate two tasks that use the same publishing mode and publishing cdn url. Note the task ID returned, which you need to pass to [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#311979ce8f747d30ba68eb412789fffd) to modify the publishing parameters or [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#f4d187c5e85084e1f96efcea1b5e076a) to stop the task.3. You can specify up to 10 CDN URLs in ` target `. You will be charged only once for transcoding even if you relay to multiple CDNs.4. To avoid causing errors, do not specify the same URLs for different publishing tasks executed at the same time. We recommend you add "sdkappid_roomid_userid_main" to URLs to distinguish them from one another and avoid application conflicts.

## updatePublishMediaStream

**updatePublishMediaStream**

| void updatePublishMediaStream | (const char* taskId |
| --- | --- |
|  | [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50775#e106259cbc7f1cff297f52931b7e7c49) * target |
|  | [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50775#22718fe81d94d21ec895cbc11820c726) * params |
|  | [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50775#7ddba434412d83f9aa8f34b1bb36b166) * config) |

**Modify publishing parameters.**

You can use this API to change the parameters of a publishing task initiated by [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a).

| Param | DESC |
| --- | --- |
| config | The On-Cloud MixTranscoding settings. This parameter is invalid in the relay-to-CDN mode. It is required if you transcode and publish the stream to a CDN or to a TRTC room. For details, see [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50775#7ddba434412d83f9aa8f34b1bb36b166). |
| params | The encoding settings. This parameter is required if you transcode and publish the stream to a CDN or to a TRTC room. If you relay to a CDN without transcoding, to improve the relaying stability and playback compatibility, we recommend you set this parameter. For details, see [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50775#22718fe81d94d21ec895cbc11820c726). |
| target | The publishing destination. You can relay the stream to a CDN (after transcoding or without transcoding) or transcode and publish the stream to a TRTC room. For details, see [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50775#e106259cbc7f1cff297f52931b7e7c49). |
| taskId | The task ID returned to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#886b2dee59842d22542b673febbd5549) callback. |

> **Note**1. You can use this API to add or remove CDN URLs to publish to (you can publish to up to 10 CDNs at a time). To avoid causing errors, do not specify the same URLs for different tasks executed at the same time.2. You can use this API to switch a relaying task to transcoding or vice versa. For example, in cross-room communication, you can first call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a) to relay to a CDN. When the anchor requests cross-room communication, call this API, passing in the task ID to switch the relaying task to a transcoding task. This can ensure that the live stream and CDN playback are not interrupted (you need to keep the encoding parameters consistent).3. You can not switch output between "only audio", "only video" and "audio and video" for the same task.

## stopPublishMediaStream

**stopPublishMediaStream**

| void stopPublishMediaStream | (const char* taskId) |
| --- | --- |

**Stop publishing.**

You can use this API to stop a task initiated by [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a).

| Param | DESC |
| --- | --- |
| taskId | The task ID returned to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#886b2dee59842d22542b673febbd5549) callback. |

> **Note**1. If the task ID is not saved to your backend, you can call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a) again when an anchor re-enters the room after abnormal exit. The publishing will fail, but the TRTC backend will return the task ID to you.2. If ` taskId ` is left empty, the TRTC backend will end all tasks you started through [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a). You can leave it empty if you have started only one task or want to stop all publishing tasks started by you.

## startLocalPreview

**startLocalPreview**

| void startLocalPreview | (bool frontCamera |
| --- | --- |
|  | TXView view) |

**Enable the preview image of local camera (mobile).**

If this API is called before [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d), the SDK will only enable the camera and wait until [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) is called before starting push.

If it is called after [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d), the SDK will enable the camera and automatically start pushing the video stream.

When the first camera video frame starts to be rendered, you will receive the ` onCameraDidReady ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

| Param | DESC |
| --- | --- |
| frontCamera | true: front camera; false: rear camera |
| view | Control that carries the video image |

> **Note**If you want to preview the camera image and adjust the beauty filter parameters through ` BeautyManager ` before going live, you can: Scheme 1. Call ` startLocalPreview ` before calling [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d). Scheme 2. Call ` startLocalPreview ` and ` muteLocalVideo(true) ` after calling [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d).

## startLocalPreview

**startLocalPreview**

| void startLocalPreview | (TXView view) |
| --- | --- |

**Enable the preview image of local camera (desktop).**

Before this API is called, [setCurrentDevice](https://www.tencentcloud.com/document/product/647/50774#a6ce23ec66c6d809518d37600b58eede) can be called first to select whether to use the desktop device's built-in camera or an external camera.

If this API is called before  [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d), the SDK will only enable the camera and wait until [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) is called before starting push.

If it is called after  [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d), the SDK will enable the camera and automatically start pushing the video stream.

When the first camera video frame starts to be rendered, you will receive the ` onCameraDidReady ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

| Param | DESC |
| --- | --- |
| view | Control that carries the video image |

> **Note**If you want to preview the camera image and adjust the beauty filter parameters through ` BeautyManager ` before going live, you can: Scheme 1. Call ` startLocalPreview ` before calling [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d). Scheme 2. Call ` startLocalPreview ` and ` muteLocalVideo(true) ` after calling [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d).

## updateLocalView

**updateLocalView**

| void updateLocalView | (TXView view) |
| --- | --- |

**Update the preview image of local camera.**

## stopLocalPreview

**stopLocalPreview**

**Stop camera preview.**

## muteLocalVideo

**muteLocalVideo**

| void muteLocalVideo | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
| --- | --- |
|  | bool mute) |

**Pause/Resume publishing local video stream.**

This API can pause (or resume) publishing the local video image. After the pause, other users in the same room will not be able to see the local image.

This API is equivalent to the two APIs of ` startLocalPreview/stopLocalPreview ` when TRTCVideoStreamTypeBig is specified, but has higher performance and response speed.

The ` startLocalPreview/stopLocalPreview ` APIs need to enable/disable the camera, which are hardware device-related operations, so they are very time-consuming.

In contrast, ` muteLocalVideo ` only needs to pause or allow the data stream at the software level, so it is more efficient and more suitable for scenarios where frequent enabling/disabling are needed.

After local video publishing is paused, other members in the same room will receive the ` onUserVideoAvailable(userId, false) ` callback notification.

After local video publishing is resumed, other members in the same room will receive the ` onUserVideoAvailable(userId, true) ` callback notification.

| Param | DESC |
| --- | --- |
| mute | true: pause; false: resume |
| streamType | Specify for which video stream to pause (or resume). Only [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) and [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) are supported |

## setVideoMuteImage

**setVideoMuteImage**

| void setVideoMuteImage | (TRTCImageBuffer* image |
| --- | --- |
|  | int fps) |

**Set placeholder image during local video pause.**

When you call ` muteLocalVideo(true) ` to pause the local video image, you can set a placeholder image by calling this API. Then, other users in the room will see this image instead of a black screen.

| Param | DESC |
| --- | --- |
| fps | Frame rate of the placeholder image. Minimum value: 5. Maximum value: 10. Default value: 5 |
| image | Placeholder image. A null value means that no more video stream data will be sent after [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50770#fbe283b224cacea70a96e4e445bebb43). The default value is null. |

## startRemoteView

**startRemoteView**

| void startRemoteView | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | TXView view) |

**Subscribe to remote user's video stream and bind video rendering control.**

Calling this API allows the SDK to pull the video stream of the specified ` userId ` and render it to the rendering control specified by the ` view ` parameter. You can set the display mode of the video image through [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50770#e15268ff41c7c2ae0a8f79f8e5fcd8df).

- If you already know the ` userId ` of a user who has a video stream in the room, you can directly call ` startRemoteView ` to subscribe to the user's video image.
- If you don't know which users in the room are publishing video streams, you can wait for the notification from [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/50771#6d1cb6b1fcf292ac6f34cd8baa647937) after [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d).

Calling this API only starts pulling the video stream, and the image needs to be loaded and buffered at this time. After the buffering is completed, you will receive a notification from [onFirstVideoFrame](https://www.tencentcloud.com/document/product/647/50771#8da71f3fa431f74bbc902324abc2a5ff).

| Param | DESC |
| --- | --- |
| streamType | Video stream type of the ` userId ` specified for watching: HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) (the remote user should enable dual-channel encoding through [enableSmallVideoStream](https://www.tencentcloud.com/document/product/647/50770#6d590cec5da031e940cc0e79f7deb40a) for this parameter to take effect) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |
| view | Rendering control that carries the video image |

> **Note**The following requires your attention:1. The SDK supports watching the big image and substream image or small image and substream image of a ` userId ` at the same time, but does not support watching the big image and small image at the same time.2. Only when the specified ` userId ` enables dual-channel encoding through [enableSmallVideoStream](https://www.tencentcloud.com/document/product/647/50770#6d590cec5da031e940cc0e79f7deb40a) can the user's small image be viewed.3. If the small image of the specified ` userId ` does not exist, the SDK will switch to the big image of the user by default.

## updateRemoteView

**updateRemoteView**

| void updateRemoteView | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | TXView view) |

**Update remote user's video rendering control.**

This API can be used to update the rendering control of the remote video image. It is often used in interactive scenarios where the display area needs to be switched.

| Param | DESC |
| --- | --- |
| streamType | Type of the stream for which to set the preview window (only [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) and [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) are supported) |
| userId | ID of the specified remote user |
| view | Control that carries the video image |

## stopRemoteView

**stopRemoteView**

| void stopRemoteView | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType) |

**Stop subscribing to remote user's video stream and release rendering control.**

Calling this API will cause the SDK to stop receiving the user's video stream and release the decoding and rendering resources for the stream.

| Param | DESC |
| --- | --- |
| streamType | Video stream type of the ` userId ` specified for watching: HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |

## stopAllRemoteView

**stopAllRemoteView**

**Stop subscribing to all remote users' video streams and release all rendering resources.**

Calling this API will cause the SDK to stop receiving all remote video streams and release all decoding and rendering resources.

> **Note**If a substream image (screen sharing) is being displayed, it will also be stopped.

## muteRemoteVideoStream

**muteRemoteVideoStream**

| void muteRemoteVideoStream | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | bool mute) |

**Pause/Resume subscribing to remote user's video stream.**

This API only pauses/resumes receiving the specified user's video stream but does not release displaying resources; therefore, the video image will freeze at the last frame before it is called.

| Param | DESC |
| --- | --- |
| mute | Whether to pause receiving |
| streamType | Specify for which video stream to pause (or resume): HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |

> **Note**This API can be called before room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d)), and the pause status will be reset after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50770#3cdc249ad1953cdbfa83c93733f952fa)). After calling this API to pause receiving the video stream from a specific user, simply calling the [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) API will not be able to play the video from that user. You need to call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50770#5b3dc4a04f807ab8c106408450824394)(false) or [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/50770#2a62b8d0ae0e1995c725a399e8447726)(false) to resume it.

## muteAllRemoteVideoStreams

**muteAllRemoteVideoStreams**

| void muteAllRemoteVideoStreams | (bool mute) |
| --- | --- |

**Pause/Resume subscribing to all remote users' video streams.**

This API only pauses/resumes receiving all users' video streams but does not release displaying resources; therefore, the video image will freeze at the last frame before it is called.

| Param | DESC |
| --- | --- |
| mute | Whether to pause receiving |

> **Note**This API can be called before room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d)), and the pause status will be reset after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50770#3cdc249ad1953cdbfa83c93733f952fa)).After calling this interface to pause receiving video streams from all users, simply calling the [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) interface will not be able to play the video from a specific user. You need to call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50770#5b3dc4a04f807ab8c106408450824394)(false) or [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/50770#2a62b8d0ae0e1995c725a399e8447726)(false) to resume it.

## setVideoEncoderParam

**setVideoEncoderParam**

| void setVideoEncoderParam | (const [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50775#b5beabfeefb812ccf1060aea67185c4e)& param) |
| --- | --- |

**Set the encoding parameters of video encoder.**

This setting can determine the quality of image viewed by remote users, which is also the image quality of on-cloud recording files.

| Param | DESC |
| --- | --- |
| param | It is used to set relevant parameters for the video encoder. For more information, please see [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50775#b5beabfeefb812ccf1060aea67185c4e). |

> **Note**Begin from v11.5 version, the encoding output resolution will be aligned according to width 8 and height 2 bytes, and will be adjusted downward, eg: input resolution 540x960, actual encoding output resolution 536x960.

## setNetworkQosParam

**setNetworkQosParam**

| void setNetworkQosParam | (const [TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/50775#15fa30eb2d0220259cea127fdb0f886f)& param) |
| --- | --- |

**Set network quality control parameters.**

This setting determines the quality control policy in a poor network environment, such as "image quality preferred" or "smoothness preferred".

| Param | DESC |
| --- | --- |
| param | It is used to set relevant parameters for network quality control. For details, please refer to [TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/50775#15fa30eb2d0220259cea127fdb0f886f). |

## setLocalRenderParams

**setLocalRenderParams**

| void setLocalRenderParams | (const [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50775#660db44737d95899da095d02d163c478) &params) |
| --- | --- |

**Set the rendering parameters of local video image.**

The parameters that can be set include video image rotation angle, fill mode, and mirror mode.

| Param | DESC |
| --- | --- |
| params | Video image rendering parameters. For more information, please see [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50775#660db44737d95899da095d02d163c478). |

## setRemoteRenderParams

**setRemoteRenderParams**

| void setRemoteRenderParams | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | const [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50775#660db44737d95899da095d02d163c478) &params) |

**Set the rendering mode of remote video image.**

The parameters that can be set include video image rotation angle, fill mode, and mirror mode.

| Param | DESC |
| --- | --- |
| params | Video image rendering parameters. For more information, please see [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50775#660db44737d95899da095d02d163c478). |
| streamType | It can be set to the primary stream image (TRTCVideoStreamTypeBig) or substream image (TRTCVideoStreamTypeSub). |
| userId | ID of the specified remote user |

## enableSmallVideoStream

**enableSmallVideoStream**

| void enableSmallVideoStream | (bool enable |
| --- | --- |
|  | const [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50775#b5beabfeefb812ccf1060aea67185c4e)& smallVideoEncParam) |

**Enable dual-channel encoding mode with big and small images.**

In this mode, the current user's encoder will output two channels of video streams, i.e., **HD big image** and **Smooth small image**, at the same time (only one channel of audio stream will be output though).

In this way, other users in the room can choose to subscribe to the **HD big image** or **Smooth small image** according to their own network conditions or screen size.

| Param | DESC |
| --- | --- |
| enable | Whether to enable small image encoding. Default value: false |
| smallVideoEncParam | Video parameters of small image stream |

> **Note**Dual-channel encoding will consume more CPU resources and network bandwidth; therefore, this feature can be enabled on macOS, Windows, or high-spec tablets, but is not recommended for phones.

**Return Desc:**

0: success; -1: the current big image has been set to a lower quality, and it is not necessary to enable dual-channel encoding

## setRemoteVideoStreamType

**setRemoteVideoStreamType**

| void setRemoteVideoStreamType | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType) |

**Switch the big/small image of specified remote user.**

After an anchor in a room enables dual-channel encoding, the video image that other users in the room subscribe to through [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) will be **HD big image** by default.

You can use this API to select whether the image subscribed to is the big image or small image. The API can take effect before or after [startRemoteView](https://www.tencentcloud.com/document/product/647/50770#1b8685dc60f89384926e40f234a27aea) is called.

| Param | DESC |
| --- | --- |
| streamType | Video stream type, i.e., big image or small image. Default value: big image |
| userId | ID of the specified remote user |

> **Note**To implement this feature, the target user must have enabled the dual-channel encoding mode through [enableSmallVideoStream](https://www.tencentcloud.com/document/product/647/50770#6d590cec5da031e940cc0e79f7deb40a); otherwise, this API will not work.

## snapshotVideo

**snapshotVideo**

| void snapshotVideo | (const char* userId |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | [TRTCSnapshotSourceType](https://www.tencentcloud.com/document/product/647/50775#1406df3b7414908d324734a5df7b746c) sourceType) |

**Screencapture video.**

You can use this API to screencapture the local video image or the primary stream image and substream (screen sharing) image of a remote user.

| Param | DESC |
| --- | --- |
| sourceType | Video image source, which can be the video stream image ([TRTCSnapshotSourceTypeStream](https://www.tencentcloud.com/document/product/647/50775#1406df3b7414908d324734a5df7b746c), generally in higher definition) ãthe video rendering image ([TRTCSnapshotSourceTypeView](https://www.tencentcloud.com/document/product/647/50775#1406df3b7414908d324734a5df7b746c)) or the capture picture ([TRTCSnapshotSourceTypeCapture](https://www.tencentcloud.com/document/product/647/50775#1406df3b7414908d324734a5df7b746c)).The captured picture screenshot will be clearer. |
| streamType | Video stream type, which can be the primary stream image ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868), generally for camera) or substream image ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868), generally for screen sharing) |
| userId | User ID. A null value indicates to screencapture the local video. |

> **Note**On Windows, only video image from the [TRTCSnapshotSourceTypeStream](https://www.tencentcloud.com/document/product/647/50775#1406df3b7414908d324734a5df7b746c) source can be screencaptured currently.

## setGravitySensorAdaptiveMode

**setGravitySensorAdaptiveMode**

| void setGravitySensorAdaptiveMode | ([TRTCGravitySensorAdaptiveMode](https://www.tencentcloud.com/document/product/647/50775#601299c4e6bd66487314e0edd164bf03) mode) |
| --- | --- |

**Set the adaptation mode of gravity sensing (version 11.7 and above).**

After turning on gravity sensing, if the device on the collection end rotates, the images on the collection end and the audience will be rendered accordingly to ensure that the image in the field of view is always facing up.

It only takes effect in the camera capture scene inside the SDK, and only takes effect on the mobile terminal.

1. This interface only works for the collection end. If you only watch the picture in the room, opening this interface is invalid.

2. When the capture device is rotated 90 degrees or 270 degrees, the picture seen by the capture device or the audience may be cropped to maintain proportional coordination.

| Param | DESC |
| --- | --- |
| mode | Gravity sensing mode, see [TRTCGravitySensorAdaptiveMode_Disable](https://www.tencentcloud.com/document/product/647/50775#601299c4e6bd66487314e0edd164bf03)ã[TRTCGravitySensorAdaptiveMode_FillByCenterCrop](https://www.tencentcloud.com/document/product/647/50775#601299c4e6bd66487314e0edd164bf03) and [TRTCGravitySensorAdaptiveMode_FitWithBlackBorder](https://www.tencentcloud.com/document/product/647/50775#601299c4e6bd66487314e0edd164bf03) for details, default value: [TRTCGravitySensorAdaptiveMode_Disable](https://www.tencentcloud.com/document/product/647/50775#601299c4e6bd66487314e0edd164bf03). |

## startLocalAudio

**startLocalAudio**

| void startLocalAudio | ([TRTCAudioQuality](https://www.tencentcloud.com/document/product/647/50775#f8aeb89d8ef78db15d893e55f68cdb42) quality) |
| --- | --- |

**Enable local audio capturing and publishing.**

The SDK does not enable the mic by default. When a user wants to publish the local audio, the user needs to call this API to enable mic capturing and encode and publish the audio to the current room.

After local audio capturing and publishing is enabled, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50771#2efaaf0cd5c69f4857c4c40f6cec038f)(userId, true) notification.

| Param | DESC |
| --- | --- |
| quality | Sound quality [TRTCAudioQualitySpeech](https://www.tencentcloud.com/document/product/647/50775#f8aeb89d8ef78db15d893e55f68cdb42) - Smooth: mono channel; audio bitrate: 18 Kbps. This is suitable for audio call scenarios, such as online meeting and audio call. [TRTCAudioQualityDefault](https://www.tencentcloud.com/document/product/647/50775#f8aeb89d8ef78db15d893e55f68cdb42) - Default: mono channel; audio bitrate: 50 Kbps. This is the default sound quality of the SDK and recommended if there are no special requirements. [TRTCAudioQualityMusic](https://www.tencentcloud.com/document/product/647/50775#f8aeb89d8ef78db15d893e55f68cdb42) - HD: dual channel + full band; audio bitrate: 128 Kbps. This is suitable for scenarios where Hi-Fi music transfer is required, such as online karaoke and music live streaming. |

> **Note**This API will check the mic permission. If the current application does not have permission to use the mic, the SDK will automatically ask the user to grant the mic permission.

## stopLocalAudio

**stopLocalAudio**

**Stop local audio capturing and publishing.**

After local audio capturing and publishing is stopped, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50771#2efaaf0cd5c69f4857c4c40f6cec038f)(userId, false) notification.

## muteLocalAudio

**muteLocalAudio**

| void muteLocalAudio | (bool mute) |
| --- | --- |

**Pause/Resume publishing local audio stream.**

After local audio publishing is paused, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50771#2efaaf0cd5c69f4857c4c40f6cec038f)(userId, false) notification.

After local audio publishing is resumed, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50771#2efaaf0cd5c69f4857c4c40f6cec038f)(userId, true) notification.

Different from [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50770#02929bb6693afbf66cae64a9bf7d34e5), ` muteLocalAudio(true) ` does not release the mic permission; instead, it continues to send mute packets with extremely low bitrate.

This is very suitable for scenarios that require on-cloud recording, as video file formats such as MP4 have a high requirement for audio continuity, while an MP4 recording file cannot be played back smoothly if [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50770#02929bb6693afbf66cae64a9bf7d34e5) is used.

Therefore, ` muteLocalAudio ` instead of [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50770#02929bb6693afbf66cae64a9bf7d34e5) is recommended in scenarios where the requirement for recording file quality is high.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |

## muteRemoteAudio

**muteRemoteAudio**

| void muteRemoteAudio | (const char* userId |
| --- | --- |
|  | bool mute) |

**Pause/Resume playing back remote audio stream.**

When you mute the remote audio of a specified user, the SDK will stop playing back the user's audio and pulling the user's audio data.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |
| userId | ID of the specified remote user |

> **Note**This API works when called either before or after room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d)), and the mute status will be reset to ` false ` after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50770#3cdc249ad1953cdbfa83c93733f952fa)).

## muteAllRemoteAudio

**muteAllRemoteAudio**

| void muteAllRemoteAudio | (bool mute) |
| --- | --- |

**Pause/Resume playing back all remote users' audio streams.**

When you mute the audio of all remote users, the SDK will stop playing back all their audio streams and pulling all their audio data.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |

> **Note**This API works when called either before or after room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d)), and the mute status will be reset to ` false ` after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50770#3cdc249ad1953cdbfa83c93733f952fa)).

## setRemoteAudioVolume

**setRemoteAudioVolume**

| void setRemoteAudioVolume | (const char *userId |
| --- | --- |
|  | int volume) |

**Set the audio playback volume of remote user.**

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

**Set the capturing volume of local audio.**

| Param | DESC |
| --- | --- |
| volume | Volume. 100 is the original volume. Value range: [0,150]. Default value: 100 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## getAudioCaptureVolume

**getAudioCaptureVolume**

**Get the capturing volume of local audio.**

**Return Desc:**

capturing volume

## setAudioPlayoutVolume

**setAudioPlayoutVolume**

| void setAudioPlayoutVolume | (int volume) |
| --- | --- |

**Set the playback volume of remote audio.**

This API controls the volume of the sound ultimately delivered by the SDK to the system for playback. It affects the volume of the recorded local audio file but not the volume of in-ear monitoring.

| Param | DESC |
| --- | --- |
| volume | Volume. 100 is the original volume. Value range: [0,150]. Default value: 100 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## getAudioPlayoutVolume

**getAudioPlayoutVolume**

**Get the playback volume of remote audio.**

## enableAudioVolumeEvaluation

**enableAudioVolumeEvaluation**

| void enableAudioVolumeEvaluation | (bool enable |
| --- | --- |
|  | const [TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/50775#a009476d3d69bd49ff693344302409bf)& params) |

**Enable volume reminder.**

After this feature is enabled, the SDK will return the audio volume assessment information of local user who sends stream and remote users in the [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/50771#454923f2ebbf576be5048238c2908e1f) callback of [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

| Param | DESC |
| --- | --- |
| enable | Whether to enable the volume prompt. Itâs disabled by default. |
| params | Volume evaluation and other related parameters, please see [TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/50775#a009476d3d69bd49ff693344302409bf) |

> **Note**To enable this feature, call this API before calling [startLocalAudio](https://www.tencentcloud.com/document/product/647/50770#37f11bf81ac7eef6af030790d31bc86d).

## startAudioRecording

**startAudioRecording**

| int startAudioRecording | (const [TRTCAudioRecordingParams](https://www.tencentcloud.com/document/product/647/50775#856a9c899752cb0b60944b7acc5fb868)& param) |
| --- | --- |

**Start audio recording.**

After you call this API, the SDK will selectively record local and remote audio streams (such as local audio, remote audio, background music, and sound effects) into a local file.

This API works when called either before or after room entry. If a recording task has not been stopped through [stopAudioRecording](https://www.tencentcloud.com/document/product/647/50770#d51e817ea322c0da1817c26980fe69d2) before room exit, it will be automatically stopped after room exit.

The startup and completion status of the recording will be notified through local recording-related callbacks. See TRTCCloud related callbacks for reference.

| Param | DESC |
| --- | --- |
| param | Recording parameter. For more information, please see [TRTCAudioRecordingParams](https://www.tencentcloud.com/document/product/647/50775#856a9c899752cb0b60944b7acc5fb868) |

> **Note**Since version 11.5, the results of audio recording have been changed to be notified through asynchronous callbacks instead of return values. Please refer to the relevant callbacks of [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33) .

**Return Desc:**

0: success; -1: audio recording has been started; -2: failed to create file or directory; -3: the audio format of the specified file extension is not supported.

## stopAudioRecording

**stopAudioRecording**

**Stop audio recording.**

If a recording task has not been stopped through this API before room exit, it will be automatically stopped after room exit.

## startLocalRecording

**startLocalRecording**

| void startLocalRecording | (const [TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/50775#4d8f80d5bf4ece224c7125eec1490b3d)& params) |
| --- | --- |

**Start local media recording.**

This API records the audio/video content during live streaming into a local file,and no recording fees for local recording.

| Param | DESC |
| --- | --- |
| params | Recording parameter. For more information, please see [TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/50775#4d8f80d5bf4ece224c7125eec1490b3d) |

## stopLocalRecording

**stopLocalRecording**

**Stop local media recording.**

If a recording task has not been stopped through this API before room exit, it will be automatically stopped after room exit.

## setRemoteAudioParallelParams

**setRemoteAudioParallelParams**

| void setRemoteAudioParallelParams | (const TRTCAudioParallelParams& params) |
| --- | --- |

**Set the parallel strategy of remote audio streams.**

For room with many speakers.

| Param | DESC |
| --- | --- |
| params | Audio parallel parameter. For more information, please see TRTCAudioParallelParams |

## enable3DSpatialAudioEffect

**enable3DSpatialAudioEffect**

| void enable3DSpatialAudioEffect | (bool enabled) |
| --- | --- |

**Enable 3D spatial effect.**

Enable 3D spatial effect. Note that [TRTCAudioQualitySpeech](https://www.tencentcloud.com/document/product/647/50775#f8aeb89d8ef78db15d893e55f68cdb42) smooth or [TRTCAudioQualityDefault](https://www.tencentcloud.com/document/product/647/50775#f8aeb89d8ef78db15d893e55f68cdb42) default audio quality should be used.

| Param | DESC |
| --- | --- |
| enabled | Whether to enable 3D spatial effect. Itâs disabled by default. |

## updateSelf3DSpatialPosition

**updateSelf3DSpatialPosition**

| void updateSelf3DSpatialPosition | (int position[3] |
| --- | --- |
|  | float axisForward[3] |
|  | float axisRight[3] |
|  | float axisUp[3]) |

**Update self position and orientation for 3D spatial effect.**

Update self position and orientation in the world coordinate system. The SDK will calculate the relative position between self and the remote users according to the parameters of this method, and then render the spatial sound effect.

| Param | DESC |
| --- | --- |
| axisForward | The unit vector of the forward axis of user coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| axisRight | The unit vector of the right axis of user coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| axisUp | The unit vector of the up axis of user coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| position | The coordinate of self in the world coordinate system. The three values represent the forward, right and up coordinate values in turn. |

> **Note**1. The length of array should be 3.2. Please limit the calling frequency appropriately. It's recommended that the interval between two operations be at least 100ms.

## updateRemote3DSpatialPosition

**updateRemote3DSpatialPosition**

| void updateRemote3DSpatialPosition | (const char* userId |
| --- | --- |
|  | int position[3]) |

**Update the specified remote user's position for 3D spatial effect.**

Update the specified remote user's position in the world coordinate system. The SDK will calculate the relative position between self and the remote users according to the parameters of this method, and then render the spatial sound effect.

| Param | DESC |
| --- | --- |
| position | The coordinate of self in the world coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| userId | ID of the specified remote user. |

> **Note**1. The length of array should be 3.2. Please limit the calling frequency appropriately. It's recommended that the interval between two operations of the same remote user be at least 100ms.

## set3DSpatialReceivingRange

**set3DSpatialReceivingRange**

| void set3DSpatialReceivingRange | (const char* userId |
| --- | --- |
|  | int range) |

**Set the maximum 3D spatial attenuation range for userId's audio stream.**

After set the range, the specified user's audio stream will attenuate to zero within the range.

| Param | DESC |
| --- | --- |
| range | Maximum attenuation range of the audio stream. |
| userId | ID of the specified user. |

## *getDeviceManager

***getDeviceManager**

**Get device management class (TXDeviceManager).**

Through device management, you can set the functions of audio and video related hardware devices such as cameras, microphones, and speakers.

**Return Desc:**

device management class TXDeviceManager.

## getBeautyManager

**getBeautyManager**

**Get beauty filter management class (TXBeautyManager).**

You can use the following features with beauty filter management:

- Set beauty effects such as "skin smoothing", "brightening", and "rosy skin".
- The following features are only supported on iOS/Android.
- Set face adjustment effects such as "eye enlarging", "face slimming", "chin slimming", "chin lengthening/shortening", "face shortening", "nose narrowing", "eye brightening", "teeth whitening", "eye bag removal", "wrinkle removal", and "smile line removal".
- Set face adjustment effects such as "hairline", "eye distance", "eye corners", "mouth shape", "nose wing", "nose position", "lip thickness", and "face shape".
- Set makeup effects such as "eye shadow" and "blush".
- Set animated effects such as animated sticker and facial pendant.

**Return Desc:**

beauty filter management class TXBeautyManager.

## setWaterMark

**setWaterMark**

| void setWaterMark | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
| --- | --- |
|  | const char* srcData |
|  | [TRTCWaterMarkSrcType](https://www.tencentcloud.com/document/product/647/50775#49ce20e9ead413a1fe53e7a7854a9ef9) srcType |
|  | uint32_t nWidth |
|  | uint32_t nHeight |
|  | float xOffset |
|  | float yOffset |
|  | float fWidthRatio |
|  | bool isVisibleOnLocalPreview = false) |

**Add watermark.**

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
| srcType | Source data type of watermark image. For more information, please see [TRTCWaterMarkSrcType](https://www.tencentcloud.com/document/product/647/50775#49ce20e9ead413a1fe53e7a7854a9ef9) |
| streamType | Stream type of the watermark to be set ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) or @@link TRTCVideoStreamTypeSub}) |
| xOffset | Top-left offset on the X axis of watermark |
| yOffset | Top-left offset on the Y axis of watermark |

> **Note**This API only supports adding an image watermark to the primary stream

## getAudioEffectManager

**getAudioEffectManager**

**Get sound effect management class (TXAudioEffectManager).**

` TXAudioEffectManager ` is a sound effect management API, through which you can implement the following features:

- Background music: both online music and local music can be played back with various features such as speed adjustment, pitch adjustment, original voice, accompaniment, and loop.
- In-ear monitoring: the sound captured by the mic is played back in the headphones in real time, which is generally used for music live streaming.
- Reverb effect: karaoke room, small room, big hall, deep, resonant, and other effects.
- Voice changing effect: young girl, middle-aged man, heavy metal, and other effects.
- Short sound effect: short sound effect files such as applause and laughter are supported (for files less than 10 seconds in length, please set the ` isShortFile ` parameter to ` true `).

**Return Desc:**

sound effect management class TXAudioEffectManager.

## startSystemAudioLoopback

**startSystemAudioLoopback**

| void startSystemAudioLoopback | (const char* deviceName = nullptr) |
| --- | --- |

**Enable system audio capturing(iOS not supported).**

This API captures audio data from the sound card of the anchorâs computer and mixes it into the current audio stream of the SDK. This ensures that other users in the room hear the audio played back by the anchorâs computer.

In online education scenarios, a teacher can use this API to have the SDK capture the audio of instructional videos and broadcast it to students in the room.

In live music scenarios, an anchor can use this API to have the SDK capture the music played back by his or her player so as to add background music to the room.

| Param | DESC |
| --- | --- |
| deviceName | If this parameter is empty, the audio of the entire system is captured. |

> **Note**On the Windows platform, you can specify the parameter ` deviceName ` to the absolute path of an executable file (such as ` QQMuisc.exe `) of a certain application. In this case, the SDK will only capture the sound of that application (32-bit version of the SDK is supported, 64-bit version of the SDK requires Windows version 10.0.19042 or higher).You can also specify ` deviceName ` as the name of a certain speaker device to capture specific speaker sound (you can use the getDevicesList interface in TXDeviceManager to obtain the speaker devices of type [TXMediaDeviceTypeSpeaker](https://www.tencentcloud.com/document/product/647/50774#f023a4d94be317eb399df83a25af6b2b)).On the Windows platform, you can also specify ` deviceName ` as the process ID of a certain process (in the format of "process_xxx", where xxx is the process ID), and then the SDK will capture the sound of that process (requires Windows version 10.0.19042 or higher).Alternatively, on the Windows platform, you can specify ` deviceName ` as the process ID of a certain process to be excluded (in the format of "exclude_process_xxx", where xxx is the process ID), and then the SDK will capture all sounds except for that process (requires Windows version 10.0.19042 or higher).About speaker device name you can see TXDeviceManager

## stopSystemAudioLoopback

**stopSystemAudioLoopback**

**Stop system audio capturing(iOS not supported).**

## setSystemAudioLoopbackVolume

**setSystemAudioLoopbackVolume**

| void setSystemAudioLoopbackVolume | (uint32_t volume) |
| --- | --- |

**Set the volume of system audio capturing.**

| Param | DESC |
| --- | --- |
| volume | Set volume. Value range: [0, 150]. Default value: 100 |

## startScreenCapture

**startScreenCapture**

| void startScreenCapture | (TXView view |
| --- | --- |
|  | [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
|  | [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50775#b5beabfeefb812ccf1060aea67185c4e)* encParam) |

**Start screen sharing.**

This API can capture the content of the entire screen or a specified application and share it with other users in the same room.

| Param | DESC |
| --- | --- |
| encParam | Image encoding parameters used for screen sharing, which can be set to empty, indicating to let the SDK choose the optimal encoding parameters (such as resolution and bitrate). |
| streamType | Channel used for screen sharing, which can be the primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868)) or substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868)). |
| view | Parent control of the rendering control, which can be set to a null value, indicating not to display the preview of the shared screen. |

> **Note**1. A user can publish at most one primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868)) and one substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868)) at the same time.2. By default, screen sharing uses the substream image. If you want to use the primary stream for screen sharing, you need to stop camera capturing (through [stopLocalPreview](https://www.tencentcloud.com/document/product/647/50770#57cfe4af12b1160ae4a904e65246d70f)) in advance to avoid conflicts.3. Only one user can use the substream for screen sharing in the same room at any time; that is, only one user is allowed to enable the substream in the same room at any time.4. When there is already a user in the room using the substream for screen sharing, calling this API will return the ` onError(ERR_SERVER_CENTER_ANOTHER_USER_PUSH_SUB_VIDEO) ` callback from [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

## stopScreenCapture

**stopScreenCapture**

**Stop screen sharing.**

## pauseScreenCapture

**pauseScreenCapture**

**Pause screen sharing.**

> **Note**Begin from v11.5 version, paused screen capture will use the last frame to output at a frame rate of 1fps.

## resumeScreenCapture

**resumeScreenCapture**

**Resume screen sharing.**

## getScreenCaptureSources

**getScreenCaptureSources**

| ITRTCScreenCaptureSourceList* getScreenCaptureSources | (const SIZE &thumbnailSize |
| --- | --- |
|  | const SIZE &iconSize) |

**Enumerate shareable screens and windows (for desktop systems only).**

When you integrate the screen sharing feature of a desktop system, you generally need to display a UI for selecting the sharing target, so that users can use the UI to choose whether to share the entire screen or a certain window.

Through this API, you can query the IDs, names, and thumbnails of sharable windows on the current system. We provide a default UI implementation in the demo for your reference.

| Param | DESC |
| --- | --- |
| iconSize | Specify the icon size of the window to be obtained. |
| thumbnailSize | Specify the thumbnail size of the window to be obtained. The thumbnail can be drawn on the window selection UI. |

> **Note**1. The returned list contains the screen and the application windows. The screen is the first element in the list. If the user has multiple displays, then each display is a sharing target.2. Please do not use ` delete ITRTCScreenCaptureSourceList* ` to delete the ` SourceList `; otherwise, crashes may occur. Instead, please use the ` release ` method in ITRTCScreenCaptureSourceList to release the list.

**Return Desc:**

List of windows (including the screen)

## selectScreenCaptureTarget

**selectScreenCaptureTarget**

| void selectScreenCaptureTarget | (const TRTCScreenCaptureSourceInfo &source |
| --- | --- |
|  | const RECT& captureRect |
|  | const TRTCScreenCaptureProperty &property) |

**Select the screen or window to share (for desktop systems only).**

After you get the sharable screens and windows through [getScreenCaptureSources](https://www.tencentcloud.com/document/product/647/50770#f839d347fc9f9cc87e132274abfcb634), you can call this API to select the target screen or window you want to share.

During the screen sharing process, you can also call this API at any time to switch the sharing target.

The following four sharing modes are supported:

- Sharing the entire screen: for ` source ` whose ` type ` is [TRTCScreenCaptureSourceTypeScreen](https://www.tencentcloud.com/document/product/647/50775#18d36b5519a892bf4b8b3f52a8b0a210)  in ` sourceInfoList `, set ` captureRect ` to ` { 0, 0, 0, 0 } `.
- Sharing a specified area: for ` source ` whose ` type ` is [TRTCScreenCaptureSourceTypeScreen](https://www.tencentcloud.com/document/product/647/50775#18d36b5519a892bf4b8b3f52a8b0a210)  in ` sourceInfoList `, set ` captureRect ` to a non-nullptr value, e.g., ` { 100, 100, 300, 300 } `.
- Sharing an entire window: for ` source ` whose ` type ` is [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/50775#18d36b5519a892bf4b8b3f52a8b0a210) in ` sourceInfoList `, set ` captureRect ` to ` { 0, 0, 0, 0 } `.
- Sharing a specified window area: for ` source ` whose ` type ` is [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/50775#18d36b5519a892bf4b8b3f52a8b0a210) in ` sourceInfoList `, set ` captureRect ` to a non-nullptr value, e.g., ` { 100, 100, 300, 300 } `.

| Param | DESC |
| --- | --- |
| captureRect | Specify the area to be captured |
| property | Specify the attributes of the screen sharing target, such as capturing the cursor and highlighting the captured window. For more information, please see the definition of ` TRTCScreenCaptureProperty ` |
| source | Specify sharing source |

> **Note**Setting the highlight border color and width parameters does not take effect on macOS.

## setSubStreamEncoderParam

**setSubStreamEncoderParam**

| void setSubStreamEncoderParam | (const [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50775#b5beabfeefb812ccf1060aea67185c4e)& param) |
| --- | --- |

**Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems).**

This API can set the image quality of screen sharing (i.e., the substream) viewed by remote users, which is also the image quality of screen sharing in on-cloud recording files.

Please note the differences between the following two APIs:

- [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50770#0450f3674968a78b9a53a17865aa5277) is used to set the video encoding parameters of the primary stream image ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868), generally for camera).
- [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50770#dd9e46a8eafd30b0f054a2c1e720868c) is used to set the video encoding parameters of the substream image ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868), generally for screen sharing).

| Param | DESC |
| --- | --- |
| param | Substream encoding parameters. For more information, please see [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50775#b5beabfeefb812ccf1060aea67185c4e). |

## setSubStreamMixVolume

**setSubStreamMixVolume**

| void setSubStreamMixVolume | (uint32_t volume) |
| --- | --- |

**Set the audio mixing volume of screen sharing (for desktop systems only).**

The greater the value, the larger the ratio of the screen sharing volume to the mic volume. We recommend you not set a high value for this parameter as a high volume will cover the mic sound.

| Param | DESC |
| --- | --- |
| volume | Set audio mixing volume. Value range: [0, 150] |

## addExcludedShareWindow

**addExcludedShareWindow**

| void addExcludedShareWindow | (TXView windowID) |
| --- | --- |

**Add specified windows to the exclusion list of screen sharing (for desktop systems only).**

The excluded windows will not be shared. This feature is generally used to add a certain application's window to the exclusion list to avoid privacy issues.

You can set the filtered windows before starting screen sharing or dynamically add the filtered windows during screen sharing.

| Param | DESC |
| --- | --- |
| window | Window not to be shared |

> **Note**1. This API takes effect only if the ` type ` in TRTCScreenCaptureSourceInfo is specified as [TRTCScreenCaptureSourceTypeScreen](https://www.tencentcloud.com/document/product/647/50775#18d36b5519a892bf4b8b3f52a8b0a210); that is, the feature of excluding specified windows works only when the entire screen is shared.2. The windows added to the exclusion list through this API will be automatically cleared by the SDK after room exit.3. On macOS, please pass in the window ID (CGWindowID), which can be obtained through the ` sourceId ` member in TRTCScreenCaptureSourceInfo.

## removeExcludedShareWindow

**removeExcludedShareWindow**

| void removeExcludedShareWindow | (TXView windowID) |
| --- | --- |

**Remove specified windows from the exclusion list of screen sharing (for desktop systems only).**

| Param | DESC |
| --- | --- |
| windowID |  |

## removeAllExcludedShareWindow

**removeAllExcludedShareWindow**

**Remove all windows from the exclusion list of screen sharing (for desktop systems only).**

## addIncludedShareWindow

**addIncludedShareWindow**

| void addIncludedShareWindow | (TXView windowID) |
| --- | --- |

**Add specified windows to the inclusion list of screen sharing (for desktop systems only).**

This API takes effect only if the ` type ` in TRTCScreenCaptureSourceInfo is specified as [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/50775#18d36b5519a892bf4b8b3f52a8b0a210); that is, the feature of additionally including specified windows works only when a window is shared.

You can call it before or after [startScreenCapture](https://www.tencentcloud.com/document/product/647/50770#94be1579f497befa5e6450725b4f1a5c).

| Param | DESC |
| --- | --- |
| windowID | Window to be shared (which is a window handle ` HWND ` on Windows) |

> **Note**The windows added to the inclusion list by this method will be automatically cleared by the SDK after room exit.

## removeIncludedShareWindow

**removeIncludedShareWindow**

| void removeIncludedShareWindow | (TXView windowID) |
| --- | --- |

**Remove specified windows from the inclusion list of screen sharing (for desktop systems only).**

This API takes effect only if the ` type ` in TRTCScreenCaptureSourceInfo is specified as [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/50775#18d36b5519a892bf4b8b3f52a8b0a210).

That is, the feature of additionally including specified windows works only when a window is shared.

| Param | DESC |
| --- | --- |
| windowID | Window to be shared (window ID on macOS or HWND on Windows) |

## removeAllIncludedShareWindow

**removeAllIncludedShareWindow**

**Remove all windows from the inclusion list of screen sharing (for desktop systems only).**

This API takes effect only if the ` type ` in TRTCScreenCaptureSourceInfo is specified as [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/50775#18d36b5519a892bf4b8b3f52a8b0a210).

That is, the feature of additionally including specified windows works only when a window is shared.

## enableCustomVideoCapture

**enableCustomVideoCapture**

| void enableCustomVideoCapture | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
| --- | --- |
|  | bool enable) |

**Enable/Disable custom video capturing mode.**

After this mode is enabled, the SDK will not run the original video capturing process (i.e., stopping camera data capturing and beauty filter operations) and will retain only the video encoding and sending capabilities.

You need to use [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50770#ab662864256180ad7ecf66eaa49bb70f) to continuously insert the captured video image into the SDK.

| Param | DESC |
| --- | --- |
| enable | Whether to enable. Default value: false |
| streamType | Specify video stream type ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868): HD big image; [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868): substream image). |

## sendCustomVideoData

**sendCustomVideoData**

| void sendCustomVideoData | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868) streamType |
| --- | --- |
|  | [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50775#9233a1b1573333abc70e53b51bd89740)* frame) |

**Deliver captured video frames to SDK.**

You can use this API to deliver video frames you capture to the SDK, and the SDK will encode and transfer them through its own network module.

We recommend you enter the following information for the [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50775#9233a1b1573333abc70e53b51bd89740) parameter (other fields can be left empty):

- pixelFormat: on Windows and Android, only [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) is supported; on iOS and macOS, [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) and [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) are supported.
- bufferType: [TRTCVideoBufferType_Buffer](https://www.tencentcloud.com/document/product/647/50775#b2c90f7f7ec6ab033949b94f0fe34942) is recommended.
- data: buffer used to carry video frame data.
- length: video frame data length. If ` pixelFormat ` is set to I420, ` length ` can be calculated according to the following formula: ` length = width * height * 3 / 2 `.
- width: video image width, such as 640 px.
- height: video image height, such as 480 px.
- timestamp (ms): Set it to the timestamp when video frames are captured, which you can obtain by calling [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50770#423a10754c9cf276a8c0374acd8aee7e) after getting a video frame.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/35158).

| Param | DESC |
| --- | --- |
| frame | Video data, which can be in I420 format. |
| streamType | Specify video stream type ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868): HD big image; [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50775#50d8d09e9837560e2946e7b187296868): substream image). |

> **Note**1. We recommend you call the [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50770#423a10754c9cf276a8c0374acd8aee7e) API to get the ` timestamp ` value of a video frame immediately after capturing it, so as to achieve the best audio/video sync effect.2. The video frame rate eventually encoded by the SDK is not determined by the frequency at which you call this API, but by the FPS you set in [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50770#0450f3674968a78b9a53a17865aa5277).3. Please try to keep the calling interval of this API even; otherwise, problems will occur, such as unstable output frame rate of the encoder or out-of-sync audio/video.4. On iOS and macOS, video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) or [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) format can be passed in currently.5. On Windows and Android, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) format can be passed in currently.

## enableCustomAudioCapture

**enableCustomAudioCapture**

| void enableCustomAudioCapture | (bool enable) |
| --- | --- |

**Enable custom audio capturing mode.**

After this mode is enabled, the SDK will not run the original audio capturing process (i.e., stopping mic data capturing) and will retain only the audio encoding and sending capabilities.

You need to use [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50770#583cf9547ea33e472ad0928fe947e9c5) to continuously insert the captured audio data into the SDK.

| Param | DESC |
| --- | --- |
| enable | Whether to enable. Default value: false |

> **Note**As acoustic echo cancellation (AEC) requires strict control over the audio capturing and playback time, after custom audio capturing is enabled, AEC may fail.

## sendCustomAudioData

**sendCustomAudioData**

| void sendCustomAudioData | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a)* frame) |
| --- | --- |

**Deliver captured audio data to SDK.**

We recommend you enter the following information for the [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a) parameter (other fields can be left empty):

- audioFormat: audio data format, which can only be ` TRTCAudioFrameFormatPCM `.
- data: audio frame buffer. Audio frame data must be in PCM format, and it supports a frame length of 5â100 ms (20 ms is recommended). Length calculation method: **for example, if the sample rate is 48000, then the frame length for mono channel will be `48000 * 0.02s * 1 * 16 bit = 15360 bit = 1920 bytes`.**
- sampleRate: sample rate. Valid values: 16000, 24000, 32000, 44100, 48000.
- channel: number of channels (if stereo is used, data is interwoven). Valid values: 1: mono channel; 2: dual channel.
- timestamp (ms): Set it to the timestamp when audio frames are captured, which you can obtain by calling [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50770#423a10754c9cf276a8c0374acd8aee7e) after getting a audio frame.

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

**Enable/Disable custom audio track.**

After this feature is enabled, you can mix a custom audio track into the SDK through this API. With two boolean parameters, you can control whether to play back this track remotely or locally.

| Param | DESC |
| --- | --- |
| enablePlayout | Whether the mixed audio track should be played back locally. Default value: false |
| enablePublish | Whether the mixed audio track should be played back remotely. Default value: false |

> **Note**If you specify both ` enablePublish ` and ` enablePlayout ` as ` false `, the custom audio track will be completely closed.

## mixExternalAudioFrame

**mixExternalAudioFrame**

| int mixExternalAudioFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a)* frame) |
| --- | --- |

**Mix custom audio track into SDK.**

Before you use this API to mix custom PCM audio into the SDK, you need to first enable custom audio tracks through [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50770#a49d9c3532c8f6b32819f5df5d30606f).

You are expected to feed audio data into the SDK at an even pace, but we understand that it can be challenging to call an API at absolutely regular intervals.

Given this, we have provided a buffer pool in the SDK, which can cache the audio data you pass in to reduce the fluctuations in intervals between API calls.

The value returned by this API indicates the size (ms) of the buffer pool. For example, if ` 50 ` is returned, it indicates that the buffer pool has 50 ms of audio data. As long as you call this API again within 50 ms, the SDK can make sure that continuous audio data is mixed.

If the value returned is ` 100 ` or greater, you can wait after an audio frame is played to call the API again. If the value returned is smaller than ` 100 `, then there isnât enough data in the buffer pool, and you should feed more audio data into the SDK until the data in the buffer pool is above the safety level.

Fill the fields in [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a) as follows (other fields are not required).

- ` data `: audio frame buffer. Audio frames must be in PCM format. Each frame can be 5-100 ms (20 ms is recommended) in duration. Assume that the sample rate is 48000, and sound channels mono-channel. Then the **frame size would be 48000 x 0.02s x 1 x 16 bit = 15360 bit = 1920 bytes**.
- ` sampleRate `: sample rate. Valid values: 16000, 24000, 32000, 44100, 48000
- ` channel `: number of sound channels (if dual-channel is used, data is interleaved). Valid values: ` 1 ` (mono-channel); ` 2 ` (dual channel)
- ` timestamp `: timestamp (ms). Set it to the timestamp when audio frames are captured, which you can obtain by calling [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50770#423a10754c9cf276a8c0374acd8aee7e) after getting an audio frame.

| Param | DESC |
| --- | --- |
| frame | Audio data |

**Return Desc:**

If the value returned is ` 0 ` or greater, the value represents the current size of the buffer pool; if the value returned is smaller than ` 0 `, it means that an error occurred. ` -1 ` indicates that you didnât call [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50770#a49d9c3532c8f6b32819f5df5d30606f) to enable custom audio tracks.

## setMixExternalAudioVolume

**setMixExternalAudioVolume**

| void setMixExternalAudioVolume | (int publishVolume |
| --- | --- |
|  | int playoutVolume) |

**Set the publish volume and playback volume of mixed custom audio track.**

| Param | DESC |
| --- | --- |
| playoutVolume | set the play volumeï¼from 0 to 150, -1 means no change |
| publishVolume | set the publish volumeï¼from 0 to 150, -1 means no change |

## generateCustomPTS

**generateCustomPTS**

**Generate custom capturing timestamp.**

This API is only suitable for the custom capturing mode and is used to solve the problem of out-of-sync audio/video caused by the inconsistency between the capturing time and delivery time of audio/video frames.

When you call APIs such as [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50770#ab662864256180ad7ecf66eaa49bb70f) or [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50770#583cf9547ea33e472ad0928fe947e9c5) for custom video or audio capturing, please use this API as instructed below:

1. First, when a video or audio frame is captured, call this API to get the corresponding PTS timestamp.

2. Then, send the video or audio frame to the preprocessing module you use (such as a third-party beauty filter or sound effect component).

3. When you actually call [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50770#ab662864256180ad7ecf66eaa49bb70f) or [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50770#583cf9547ea33e472ad0928fe947e9c5) for delivery, assign the PTS timestamp recorded when the frame was captured to the ` timestamp ` field in [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50775#9233a1b1573333abc70e53b51bd89740) or [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a).

**Return Desc:**

Timestamp in ms

## enableLocalVideoCustomProcess

**enableLocalVideoCustomProcess**

| int enableLocalVideoCustomProcess | (bool enable |
| --- | --- |
|  | [TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) pixelFormat |
|  | [TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/50775#b2c90f7f7ec6ab033949b94f0fe34942) bufferType) |

**.1 Enable third-party beauty filters in video.**

After it is enabled, you can get the image frame of the specified pixel format and video data structure type through [ITRTCVideoFrameCallback](https://www.tencentcloud.com/document/product/647/50771#9454c2f295e4e4519548382c4b6d868c).

| Param | DESC |
| --- | --- |
| bufferType | Specify the format of the data called back. |
| enable | Whether to enable local video process. Itâs disabled by default. |
| pixelFormat | Specify the format of the pixel called back. |

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384))

## setLocalVideoCustomProcessCallback

**setLocalVideoCustomProcessCallback**

| void setLocalVideoCustomProcessCallback | ([ITRTCVideoFrameCallback](https://www.tencentcloud.com/document/product/647/50771#9454c2f295e4e4519548382c4b6d868c)* callback) |
| --- | --- |

**.2 Set video data callback for third-party beauty filters.**

After this callback is set, the SDK will call back the captured video frames through the ` callback ` you set and use them for further processing by a third-party beauty filter component. Then, the SDK will encode and send the processed video frames.

| Param | DESC |
| --- | --- |
| callback | : Custom preprocessing callback. For more information, please see [ITRTCVideoFrameCallback](https://www.tencentcloud.com/document/product/647/50771#9454c2f295e4e4519548382c4b6d868c) |

## setLocalVideoRenderCallback

**setLocalVideoRenderCallback**

| int setLocalVideoRenderCallback | ([TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) pixelFormat |
| --- | --- |
|  | [TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/50775#b2c90f7f7ec6ab033949b94f0fe34942) bufferType |
|  | [ITRTCVideoRenderCallback](https://www.tencentcloud.com/document/product/647/50771#fce7830c6c3adc13fe5fa5da776a9da3)* callback) |

**Set the callback of custom rendering for local video.**

After this callback is set, the SDK will skip its own rendering process and call back the captured data. Therefore, you need to complete image rendering on your own.

- You can call ` setLocalVideoRenderCallback(TRTCVideoPixelFormat_Unknown, TRTCVideoBufferType_Unknown, nullptr) ` to stop the callback.
- On iOS, macOS, and Windows, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) or [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) pixel format can be called back currently.
- On Android, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567), [TRTCVideoPixelFormat_RGBA32](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) or [TRTCVideoPixelFormat_Texture_2D](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) pixel format can be passed in currently.

| Param | DESC |
| --- | --- |
| bufferType | Specify video data structure type. |
| callback | Callback for custom rendering |
| pixelFormat | Specify the format of the pixel called back |

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384))

## setRemoteVideoRenderCallback

**setRemoteVideoRenderCallback**

| int setRemoteVideoRenderCallback | (const char* userId |
| --- | --- |
|  | [TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) pixelFormat |
|  | [TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/50775#b2c90f7f7ec6ab033949b94f0fe34942) bufferType |
|  | [ITRTCVideoRenderCallback](https://www.tencentcloud.com/document/product/647/50771#fce7830c6c3adc13fe5fa5da776a9da3)* callback) |

**Set the callback of custom rendering for remote video.**

After this callback is set, the SDK will skip its own rendering process and call back the captured data. Therefore, you need to complete image rendering on your own.

- You can call ` setRemoteVideoRenderCallback(TRTCVideoPixelFormat_Unknown, TRTCVideoBufferType_Unknown, nullptr) ` to stop the callback.
- On iOS, macOS, and Windows, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) or [TRTCVideoPixelFormat_BGRA32](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) pixel format can be called back currently.
- On Android, only video frames in [TRTCVideoPixelFormat_I420](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) , [TRTCVideoPixelFormat_RGBA32](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567) or [TRTCVideoPixelFormat_Texture_2D](https://www.tencentcloud.com/document/product/647/50775#562ec64d51515fd8aa2efbccaf171567)pixel format can be passed in currently.

| Param | DESC |
| --- | --- |
| bufferType | Specify video data structure type. Only [TRTCVideoBufferType_Buffer](https://www.tencentcloud.com/document/product/647/50775#b2c90f7f7ec6ab033949b94f0fe34942) is supported currently |
| callback | Callback for custom rendering |
| pixelFormat | Specify the format of the pixel called back |
| userId | remote user id |

> **Note**In actual use, you need to call ` startRemoteView(userid, nullptr) ` to get the video stream of the remote user first (set ` view ` to ` nullptr `); otherwise, there will be no data called back.

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384))

## setAudioFrameCallback

**setAudioFrameCallback**

| int setAudioFrameCallback | ([ITRTCAudioFrameCallback](https://www.tencentcloud.com/document/product/647/50771#2841236ef9a6933d9471d25521d5a3ff)* callback) |
| --- | --- |

**Set custom audio data callback.**

After this callback is set, the SDK will internally call back the audio data (in PCM format), including:

- [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2012baeb6789e1eaabc97764626fd101): callback of the audio data captured by the local mic
- [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2a3a126d62184e1cd093e47562f54774): callback of the audio data captured by the local mic and preprocessed by the audio module
- [onPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50771#25988e5cee8c6ab0ed83c8be752fd9a6): audio data from each remote user before audio mixing
- [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50771#59235444572469f2b1458f0a5265676c): callback of the audio data that will be played back by the system after audio streams are mixed

> **Note**Setting the callback to null indicates to stop the custom audio callback, while setting it to a non-null value indicates to start the custom audio callback.

## setCapturedAudioFrameCallbackFormat

**setCapturedAudioFrameCallbackFormat**

| int setCapturedAudioFrameCallbackFormat | ([TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50775#352b0878415e79fcd48d9027fab3f683)* format) |
| --- | --- |

**Set the callback format of audio frames captured by local mic.**

This API is used to set the ` AudioFrame ` format called back by [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2012baeb6789e1eaabc97764626fd101):

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

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384))

## setLocalProcessedAudioFrameCallbackFormat

**setLocalProcessedAudioFrameCallbackFormat**

| int setLocalProcessedAudioFrameCallbackFormat | ([TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50775#352b0878415e79fcd48d9027fab3f683)* format) |
| --- | --- |

**Set the callback format of preprocessed local audio frames.**

This API is used to set the ` AudioFrame ` format called back by [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2a3a126d62184e1cd093e47562f54774):

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

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384))

## setMixedPlayAudioFrameCallbackFormat

**setMixedPlayAudioFrameCallbackFormat**

| int setMixedPlayAudioFrameCallbackFormat | ([TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50775#352b0878415e79fcd48d9027fab3f683)* format) |
| --- | --- |

**Set the callback format of audio frames to be played back by system.**

This API is used to set the ` AudioFrame ` format called back by [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50771#59235444572469f2b1458f0a5265676c):

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

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35135#e9c6eb6577e24853dd9716de29044384))

## enableCustomAudioRendering

**enableCustomAudioRendering**

| void enableCustomAudioRendering | (bool enable) |
| --- | --- |

**Enabling custom audio playback.**

You can use this API to enable custom audio playback if you want to connect to an external audio device or control the audio playback logic by yourself.

After you enable custom audio playback, the SDK will stop using its audio API to play back audio. You need to call [getCustomAudioRenderingFrame](https://www.tencentcloud.com/document/product/647/50770#7c58a64f102323c6420c0acdbc4d6c4a) to get audio frames and play them by yourself.

| Param | DESC |
| --- | --- |
| enable | Whether to enable custom audio playback. It's disabled by default. |

> **Note**The parameter must be set before room entry to take effect.

## getCustomAudioRenderingFrame

**getCustomAudioRenderingFrame**

| void getCustomAudioRenderingFrame | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a)* audioFrame) |
| --- | --- |

**Getting playable audio data.**

Before calling this API, you need to first enable custom audio playback using [enableCustomAudioRendering](https://www.tencentcloud.com/document/product/647/50770#39ec05a397f4ebb398f3655679072245).

Fill the fields in [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50775#c4548e14c21c3416c1ba8d886aebba8a) as follows (other fields are not required):

- ` sampleRate `: sample rate (required). Valid values: 16000, 24000, 32000, 44100, 48000
- ` channel `: number of sound channels (required). ` 1 `: mono-channel; ` 2 `: dual-channel; if dual-channel is used, data is interleaved.
- ` data `: the buffer used to get audio data. You need to allocate memory for the buffer based on the duration of an audio frame.

The PCM data obtained can have a frame duration of 10 ms or 20 ms. 20 ms is recommended.

Assume that the sample rate is 48000, and sound channels mono-channel. The buffer size for a 20 ms audio frame would be ` 48000 x 0.02s x 1 x 16 bit = 15360 bit = 1920 bytes `.

| Param | DESC |
| --- | --- |
| audioFrame | Audio frames |

> **Note**1. You must set ` sampleRate ` and ` channel ` in ` audioFrame `, and allocate memory for one frame of audio in advance.2. The SDK will fill the data automatically based on ` sampleRate ` and ` channel `.3. We recommend that you use the systemâs audio playback thread to drive the calling of this API, so that it is called each time the playback of an audio frame is complete.

## sendCustomCmdMsg

**sendCustomCmdMsg**

| bool sendCustomCmdMsg | (uint32_t cmdId |
| --- | --- |
|  | const uint8_t* data |
|  | uint32_t dataSize |
|  | bool reliable |
|  | bool ordered) |

**Use UDP channel to send custom message to all users in room.**

This API allows you to use TRTC's UDP channel to broadcast custom data to other users in the current room for signaling transfer.

Other users in the room can receive the message through the ` onRecvCustomCmdMsg ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

| Param | DESC |
| --- | --- |
| cmdID | Message ID. Value range: [1, 10] |
| data | Message to be sent. The maximum length of one single message is 1 KB. |
| ordered | Whether orderly sending is enabled, i.e., whether the data packets should be received in the same order in which they are sent; if so, a certain delay will be caused. |
| reliable | Whether reliable sending is enabled. Reliable sending can achieve a higher success rate but with a longer reception delay than unreliable sending. |

> **Note**1. Up to 30 messages can be sent per second to all users in the room (this is not supported for web and mini program currently. this limit is shared with [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50770#419654e5edfe1587ac98d7d43a47c744)).2. A packet can contain up to 1 KB of data; if the threshold is exceeded, the packet is very likely to be discarded by the intermediate router or server.(this limit is shared with [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50770#419654e5edfe1587ac98d7d43a47c744)).3. A client can send up to 16 KB of data in total per second.4. ` reliable ` and ` ordered ` must be set to the same value (` true ` or ` false `) and cannot be set to different values currently.5. We strongly recommend you set different ` cmdID ` values for messages of different types. This can reduce message delay when orderly sending is required.6. Currently only the anchor role is supported.

**Return Desc:**

true: sent the message successfully; false: failed to send the message.

## sendSEIMsg

**sendSEIMsg**

| bool sendSEIMsg | (const uint8_t* data |
| --- | --- |
|  | uint32_t dataSize |
|  | int32_t repeatCount) |

**Use SEI channel to send custom message to all users in room.**

This API allows you to use TRTC's SEI channel to broadcast custom data to other users in the current room for signaling transfer.

The header of a video frame has a header data block called SEI. This API works by embedding the custom signaling data you want to send in the SEI block and sending it together with the video frame.

Therefore, the SEI channel has a better compatibility than [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50770#b39e25426586d217f2fdf44b7777b47c) as the signaling data can be transferred to the CSS CDN along with the video frame.

However, because the data block of the video frame header cannot be too large, we recommend you limit the size of the signaling data to only a few bytes when using this API.

The most common use is to embed the custom timestamp into video frames through this API so as to implement a perfect alignment between the message and video image (such as between the teaching material and video signal in the education scenario).

Other users in the room can receive the message through the ` onRecvSEIMsg ` callback in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/50771#c334ca01f4134afa7b339a9da12fbb33).

| Param | DESC |
| --- | --- |
| data | Data to be sent, which can be up to 1 KB (1,000 bytes) |
| repeatCount | Data sending count |

> **Note**This API has the following restrictions:1. The data will not be instantly sent after this API is called; instead, it will be inserted into the next video frame after the API call.2. Up to 30 messages can be sent per second to all users in the room (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50770#b39e25426586d217f2fdf44b7777b47c)).3. Each packet can be up to 1 KB (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50770#b39e25426586d217f2fdf44b7777b47c)). If a large amount of data is sent, the video bitrate will increase, which may reduce the video quality or even cause lagging.4. Each client can send up to 16 KB of data in total per second (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50770#b39e25426586d217f2fdf44b7777b47c)).5. If multiple times of sending is required (i.e., ` repeatCount ` > 1), the data will be inserted into subsequent ` repeatCount ` video frames in a row for sending, which will increase the video bitrate.6. If ` repeatCount ` is greater than 1, the data will be sent for multiple times, and the same message may be received multiple times in the [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/50771#567707ef1f7ff43f79cfaf84e1bc2368) callback; therefore, deduplication is required.

**Return Desc:**

true: the message is allowed and will be sent with subsequent video frames; false: the message is not allowed to be sent

## startSpeedTest

**startSpeedTest**

| int startSpeedTest | (const [TRTCSpeedTestParams](https://www.tencentcloud.com/document/product/647/50775#dd22aad94fc4b4773ca7323c7d34a1a7)& params) |
| --- | --- |

**Start network speed test (used before room entry).**

| Param | DESC |
| --- | --- |
| params | speed test options |

> **Note**1. The speed measurement process will incur a small amount of basic service fees, See [Purchase Guide > Base Services](https://intl.cloud.tencent.com/document/product/647/34610?lang=en&pg=#basic-services).2. Please perform the Network speed test before room entry, because if performed after room entry, the test will affect the normal audio/video transfer, and its result will be inaccurate due to interference in the room.3. Only one network speed test task is allowed to run at the same time.

**Return Desc:**

interface call result, <0: failure

## stopSpeedTest

**stopSpeedTest**

**Stop network speed test.**

## getSDKVersion

**getSDKVersion**

**Get SDK version information.**

## setLogLevel

**setLogLevel**

| void setLogLevel | ([TRTCLogLevel](https://www.tencentcloud.com/document/product/647/50775#3b7ff44175cba4dd48e97aa8ac7b0b98) level) |
| --- | --- |

**Set log output level.**

| Param | DESC |
| --- | --- |
| level | For more information, please see [TRTCLogLevel](https://www.tencentcloud.com/document/product/647/50775#3b7ff44175cba4dd48e97aa8ac7b0b98). Default value: [TRTCLogLevelNone](https://www.tencentcloud.com/document/product/647/50775#3b7ff44175cba4dd48e97aa8ac7b0b98) |

## setConsoleEnabled

**setConsoleEnabled**

| void setConsoleEnabled | (bool enabled) |
| --- | --- |

**Enable/Disable console log printing.**

| Param | DESC |
| --- | --- |
| enabled | Specify whether to enable it, which is disabled by default |

## setLogCompressEnabled

**setLogCompressEnabled**

| void setLogCompressEnabled | (bool enabled) |
| --- | --- |

**Enable/Disable local log compression.**

If compression is enabled, the log size will significantly reduce, but logs can be read only after being decompressed by the Python script provided by Tencent Cloud.

If compression is disabled, logs will be stored in plaintext and can be read directly in Notepad, but will take up more storage capacity.

| Param | DESC |
| --- | --- |
| enabled | Specify whether to enable it, which is enabled by default |

## setLogDirPath

**setLogDirPath**

| void setLogDirPath | (const char* path) |
| --- | --- |

**Set local log storage path.**

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

| void setLogCallback | ([ITRTCLogCallback](https://www.tencentcloud.com/document/product/647/50771#486f92ae649081ecfa3769fb441f77da)* callback) |
| --- | --- |

**Set log callback.**

## showDebugView

**showDebugView**

| void showDebugView | (int showType) |
| --- | --- |

**Display dashboard.**

"Dashboard" is a semi-transparent floating layer for debugging information on top of the video rendering control. It is used to display audio/video information and event information to facilitate integration and debugging.

| Param | DESC |
| --- | --- |
| showType | 0: does not display; 1: displays lite edition (only with audio/video information); 2: displays full edition (with audio/video information and event information). |

## callExperimentalAPI

**callExperimentalAPI**

| char* callExperimentalAPI | (const char *jsonStr) |
| --- | --- |

**Call experimental APIs.**

## enablePayloadPrivateEncryption

**enablePayloadPrivateEncryption**

| int enablePayloadPrivateEncryption | (bool enabled |
| --- | --- |
|  | const [TRTCPayloadPrivateEncryptionConfig](https://www.tencentcloud.com/document/product/647/50775#e31d0d9395f1cb44ee256f450523ce86)& config) |

**Enable or disable private encryption of media streams.**

In scenarios with high security requirements, TRTC recommends that you call the enablePayloadPrivateEncryption method to enable private encryption of media streams before joining a room.

After the user exits the room, the SDK will automatically close the private encryption. To re-enable private encryption, you need to call this method before the user joins the room again.

| Param | DESC |
| --- | --- |
| config | Configure the algorithm and key for private encryption of media streams, please see [TRTCPayloadPrivateEncryptionConfig](https://www.tencentcloud.com/document/product/647/50775#e31d0d9395f1cb44ee256f450523ce86). |
| enabled | Whether to enable media stream private encryption. |

> **Note**TRTC has built-in encryption for media streams before transmission. After private encryption of media streams is enabled, it will be re-encrypted with the key and initial vector you pass in.

**Return Desc:**

Interface call result, 0: Method call succeeded, -1: The incoming parameter is invalid, -2: Your subscription has expired. If you want to renew it, Please go to purchase the [TRTC Professional Edition](https://console.trtc.io/subscription/buy/rtc?packType=pro), and [contact us](https://trtc.io/zh/contact) for review before use.


---
*Source: [https://trtc.io/document/50770](https://trtc.io/document/50770)*
