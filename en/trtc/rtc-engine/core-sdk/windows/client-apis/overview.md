# Overview

**API OVERVIEW**

## Create Instance And Event Callback

| FuncList | DESC |
| --- | --- |
| [getTRTCShareInstance](https://www.tencentcloud.com/document/product/647/50770#d817d491e3ec85d6b2e5880e4f1d4309) | Create TRTCCloud instance (singleton mode). |
| [destroyTRTCShareInstance](https://www.tencentcloud.com/document/product/647/50770#5e76d84cc813399072e4fe50bfcc1663) | Terminate TRTCCloud instance (singleton mode). |
| [addCallback](https://www.tencentcloud.com/document/product/647/50770#1c3368fb92a2809a4095874c2980f68c) | Add TRTC event callback. |
| [removeCallback](https://www.tencentcloud.com/document/product/647/50770#8297cfe9383f11812f7ca3a917243b9e) | Remove TRTC event callback. |

## Room APIs

| FuncList | DESC |
| --- | --- |
| [enterRoom](https://www.tencentcloud.com/document/product/647/50770#b6eb951dc67569848a415ba028f6746d) | Enter room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/50770#3cdc249ad1953cdbfa83c93733f952fa) | Exit room. |
| [switchRole](https://www.tencentcloud.com/document/product/647/50770#97e4bd705285a3846d2dc78e21b27508) | Switch role. |
| [switchRoom](https://www.tencentcloud.com/document/product/647/50770#c1f8ee70eb0df8f09cc410243a5b86af) | Switch room. |
| [connectOtherRoom](https://www.tencentcloud.com/document/product/647/50770#b3e33b4e5c9bb2e3670895ecfffce7cc) | Request cross-room call. |
| [disconnectOtherRoom](https://www.tencentcloud.com/document/product/647/50770#54bb12e5c34ae35d6b5f5aad213dbb12) | Exit cross-room call. |
| [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/50770#1bd891d9afeb9021c825ab3d39da6fe7) | Set subscription mode (which must be set before room entry for it to take effect). |
| [createSubCloud](https://www.tencentcloud.com/document/product/647/50770#f553df5bb3471677a3f7806b4cd342d3) | Create room subinstance (for concurrent multi-room listen/watch). |
| [destroySubCloud](https://www.tencentcloud.com/document/product/647/50770#fbcb5d292c2ed3d07cf7999c9e6372eb) | Terminate room subinstance. |
| [updateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50770#9d234f56d6bfdca31ec9390aa5ddc055) | Change the upstream capability of the cross-room anchor in the current room. |

## CDN APIs

| FuncList | DESC |
| --- | --- |
| [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#2b0ac079e8b754810595cd469719c63a) | Publish a stream. |
| [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#311979ce8f747d30ba68eb412789fffd) | Modify publishing parameters. |
| [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50770#f4d187c5e85084e1f96efcea1b5e076a) | Stop publishing. |

## Video APIs

| FuncList | DESC |
| --- | --- |
| [startLocalPreview](https://www.tencentcloud.com/document/product/647/50770#66bab4d115291cba164b192ccb3c23a6) | Enable the preview image of local camera (mobile). |
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

## Audio APIs

| FuncList | DESC |
| --- | --- |
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

## Device management APIs

| FuncList | DESC |
| --- | --- |
| [*getDeviceManager](https://www.tencentcloud.com/document/product/647/50770#501064d6605beb476dc25f7639a956c0) | Get device management class (TXDeviceManager). |

## Beauty filter and watermark APIs

| FuncList | DESC |
| --- | --- |
| [getBeautyManager](https://www.tencentcloud.com/document/product/647/50770#059bcc9a1996feee7a0e6b7b293da5e1) | Get beauty filter management class (TXBeautyManager). |
| [setWaterMark](https://www.tencentcloud.com/document/product/647/50770#c8cbf50686954f1ea85a3dd88afe853e) | Add watermark. |

## Background music and sound effect APIs

| FuncList | DESC |
| --- | --- |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/50770#59d65371953ec37eef801d6207d6111a) | Get sound effect management class (TXAudioEffectManager). |
| [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50770#792556646f98fdbb0eb9e4b7fb12c42b) | Enable system audio capturing(iOS not supported). |
| [stopSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50770#afed828e50c50eed29f3c14790384353) | Stop system audio capturing(iOS not supported). |
| [setSystemAudioLoopbackVolume](https://www.tencentcloud.com/document/product/647/50770#70ff72cab273dfc306cda1502ab1dcfd) | Set the volume of system audio capturing. |

## Screen sharing APIs

| FuncList | DESC |
| --- | --- |
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

## Custom capturing and rendering APIs

| FuncList | DESC |
| --- | --- |
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

## Custom message sending APIs

| FuncList | DESC |
| --- | --- |
| [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50770#b39e25426586d217f2fdf44b7777b47c) | Use UDP channel to send custom message to all users in room. |
| [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50770#419654e5edfe1587ac98d7d43a47c744) | Use SEI channel to send custom message to all users in room. |

## Network test APIs

| FuncList | DESC |
| --- | --- |
| [startSpeedTest](https://www.tencentcloud.com/document/product/647/50770#ad6d84be7e3d8b20fae6b5f6f56d65f0) | Start network speed test (used before room entry). |
| [stopSpeedTest](https://www.tencentcloud.com/document/product/647/50770#4ff1163b6d7c4ee154038619e97d93fd) | Stop network speed test. |

## Debugging APIs

| FuncList | DESC |
| --- | --- |
| [getSDKVersion](https://www.tencentcloud.com/document/product/647/50770#2c99e9c9fe63339640d3aef0180edc8d) | Get SDK version information. |
| [setLogLevel](https://www.tencentcloud.com/document/product/647/50770#ccccdd35beb94f8c7df9b8dcc36b035d) | Set log output level. |
| [setConsoleEnabled](https://www.tencentcloud.com/document/product/647/50770#0dd9b9a5a22e32d304a2bedff1207a71) | Enable/Disable console log printing. |
| [setLogCompressEnabled](https://www.tencentcloud.com/document/product/647/50770#a359474ff7de4e260f7028112593d48c) | Enable/Disable local log compression. |
| [setLogDirPath](https://www.tencentcloud.com/document/product/647/50770#7d9cfe89693ba84820a16f8bb26f9be0) | Set local log storage path. |
| [setLogCallback](https://www.tencentcloud.com/document/product/647/50770#b98b09e7a09ce913c98f38f683281268) | Set log callback. |
| [showDebugView](https://www.tencentcloud.com/document/product/647/50770#39079784c81c16dcb5e16ab24ee2f8dc) | Display dashboard. |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/50770#3e746d07f491f672c1dce2622bb97d07) | Call experimental APIs. |

## Encrypted interface

| FuncList | DESC |
| --- | --- |
| [enablePayloadPrivateEncryption](https://www.tencentcloud.com/document/product/647/50770#925d04bb9e69e658644d5ee54f863977) | Enable or disable private encryption of media streams. |

## Error and warning events

| FuncList | DESC |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/50771#3df71ff9905826c3d788593557c7f40b) | Error event callback. |
| [onWarning](https://www.tencentcloud.com/document/product/647/50771#972f298b26035f643d3512b8bbbe1ce6) | Warning event callback. |

## Room event callback

| FuncList | DESC |
| --- | --- |
| [onEnterRoom](https://www.tencentcloud.com/document/product/647/50771#6f9dcce089ddf638dac51f9789f44224) | Whether room entry is successful. |
| [onExitRoom](https://www.tencentcloud.com/document/product/647/50771#a80925fbd52d416a44f8c29f48d08c7a) | Room exit. |
| [onSwitchRole](https://www.tencentcloud.com/document/product/647/50771#bbf6926ae04d54d63c770cd13f03d828) | Role switching. |
| [onSwitchRoom](https://www.tencentcloud.com/document/product/647/50771#7d4de775235d838da1c216caddf074aa) | Result of room switching. |
| [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50771#69534513bb766ecb024b4b7e475d5ddd) | Result of requesting cross-room call. |
| [onDisconnectOtherRoom](https://www.tencentcloud.com/document/product/647/50771#2554839cf7be6599f136a98bb6b5625b) | Result of ending cross-room call. |
| [onUpdateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50771#943a6c15c33a5977cc718bba24af923b) | Result of changing the upstream capability of the cross-room anchor. |

## User event callback.

| FuncList | DESC |
| --- | --- |
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

## Callback of statistics on network and technical metrics.

| FuncList | DESC |
| --- | --- |
| [onNetworkQuality](https://www.tencentcloud.com/document/product/647/50771#7faad64d9fbb7d65876027eaa7d60b3d) | Real-time network quality statistics. |
| [onStatistics](https://www.tencentcloud.com/document/product/647/50771#3a8ca1601794ca5ab8aac596447684b8) | Real-time statistics on technical metrics. |
| [onSpeedTestResult](https://www.tencentcloud.com/document/product/647/50771#3f01ebf391cbb16fe1b9b9b3e983bb6c) | Callback of network speed test. |

## Callback of connection to the cloud

| FuncList | DESC |
| --- | --- |
| [onConnectionLost](https://www.tencentcloud.com/document/product/647/50771#6f1f6ac255f4027285ade6528d7fd80a) | The SDK was disconnected from the cloud. |
| [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50771#f4c4e0fc1d93660732758709d477efcc) | The SDK is reconnecting to the cloud. |
| [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50771#ddabb835fc7f8359827e33ba72514ec8) | The SDK is reconnected to the cloud. |

## Callback of hardware events

| FuncList | DESC |
| --- | --- |
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

## Callback of the receipt of a custom message.

| FuncList | DESC |
| --- | --- |
| [onRecvCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50771#4cd82f4edb24992a15a25187089e1565) | Receipt of custom message. |
| [onMissCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50771#b86ff5635dd07db269779d9a3f751f8b) | Loss of custom message. |
| [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/50771#567707ef1f7ff43f79cfaf84e1bc2368) | Receipt of SEI message. |

## CDN event callback

| FuncList | DESC |
| --- | --- |
| [onStartPublishing](https://www.tencentcloud.com/document/product/647/50771#80c4449085b648a0455de90f7a88640c) | Started publishing to Tencent Cloud CSS CDN. |
| [onStopPublishing](https://www.tencentcloud.com/document/product/647/50771#d314b918b62a270f1a1883ce9e71647f) | Stopped publishing to Tencent Cloud CSS CDN. |
| [onStartPublishCDNStream](https://www.tencentcloud.com/document/product/647/50771#4590b3a88275cb60c936b8fcd35c9c0d) | Started publishing to non-Tencent Cloudâs live streaming CDN. |
| [onStopPublishCDNStream](https://www.tencentcloud.com/document/product/647/50771#94cff50ac97c175da6aa02499d25edfc) | Stopped publishing to non-Tencent Cloudâs live streaming CDN. |
| [onSetMixTranscodingConfig](https://www.tencentcloud.com/document/product/647/50771#3dc61d7293745439dd34e0233f105047) | Set the layout and transcoding parameters for On-Cloud MixTranscoding. |
| [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#886b2dee59842d22542b673febbd5549) | Callback for starting to publish. |
| [onUpdatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#3a50d286d7cfe0c1f7f029e6d5b3206f) | Callback for modifying publishing parameters. |
| [onStopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50771#7a152f00d4f86489acb724138f2b8c66) | Callback for stopping publishing. |
| [onCdnStreamStateChanged](https://www.tencentcloud.com/document/product/647/50771#121f67d094d49a08d83ef0adda327578) | Callback for change of RTMP/RTMPS publishing status. |

## Screen sharing event callback

| FuncList | DESC |
| --- | --- |
| [onScreenCaptureStarted](https://www.tencentcloud.com/document/product/647/50771#fbf1f7083f4f4583a7d691a40ae55d9c) | Screen sharing started. |
| [onScreenCapturePaused](https://www.tencentcloud.com/document/product/647/50771#a8f341fb34c2a0969929f34ceb8b3a92) | Screen sharing was paused. |
| [onScreenCaptureResumed](https://www.tencentcloud.com/document/product/647/50771#609d1cc7606416b0e5a7186bdf90c135) | Screen sharing was resumed. |
| [onScreenCaptureStoped](https://www.tencentcloud.com/document/product/647/50771#6d61c99d694a71721431581ed1b1c0bd) | Screen sharing stopped. |
| [onScreenCaptureCovered](https://www.tencentcloud.com/document/product/647/50771#f5caba5a01c2574e2ae4ab0a5d0593ab) | The shared window was covered (for Windows only). |

## Callback of local recording and screenshot events

| FuncList | DESC |
| --- | --- |
| [onLocalRecordBegin](https://www.tencentcloud.com/document/product/647/50771#48421ae254e0029b6eadfe4b4810f57a) | Local recording started. |
| [onLocalRecording](https://www.tencentcloud.com/document/product/647/50771#b14c8492fe7f42893135a23434f243e0) | Local media is being recorded. |
| [onLocalRecordFragment](https://www.tencentcloud.com/document/product/647/50771#352e01c2315eca3649522dba34060de5) | Record fragment finished. |
| [onLocalRecordComplete](https://www.tencentcloud.com/document/product/647/50771#d9754b34c3638694eaf68c3ffdc183e9) | Local recording stopped. |
| [onSnapshotComplete](https://www.tencentcloud.com/document/product/647/50771#66ddc64d69b21230bd3523a78fdbb993) | Finished taking a local screenshot. |

## Disused callbacks

| FuncList | DESC |
| --- | --- |
| [onUserEnter](https://www.tencentcloud.com/document/product/647/50771#58e09a2f3f342339d38a2249150c2a45) | An anchor entered the room (disused). |
| [onUserExit](https://www.tencentcloud.com/document/product/647/50771#47d0fe4edc3978f6431931ff1331e3c7) | An anchor left the room (disused). |
| [onAudioEffectFinished](https://www.tencentcloud.com/document/product/647/50771#05a9c8f50d403a735ba04ff953c96830) | Audio effects ended (disused). |
| [onPlayBGMBegin](https://www.tencentcloud.com/document/product/647/50771#ba9e2cd78ef9abbe4c5017aea4f8334f) | Started playing background music (disused). |
| [onPlayBGMProgress](https://www.tencentcloud.com/document/product/647/50771#06c3ce9c30d9aa17cdc6a863ffd8e8bd) | Playback progress of background music (disused). |
| [onPlayBGMComplete](https://www.tencentcloud.com/document/product/647/50771#786cda61957e9bc05b2f4f3f6034ed36) | Background music stopped (disused). |
| [onSpeedTest](https://www.tencentcloud.com/document/product/647/50771#895ad42d5607c1ec46cec2f7d8e73e5c) | Result of server speed testing (disused). |

## Callback of custom video processing

| FuncList | DESC |
| --- | --- |
| [onRenderVideoFrame](https://www.tencentcloud.com/document/product/647/50771#eeb9ee31869141d9c8d56407d8cd02a9) | Custom video rendering. |
| [onGLContextCreated](https://www.tencentcloud.com/document/product/647/50771#e5d9a2200de15bc024ae70f8365aadfb) | An OpenGL context was created in the SDK. |
| [onProcessVideoFrame](https://www.tencentcloud.com/document/product/647/50771#1617c3b2b01565bb6f5dd34bdd0c6e98) | Video processing by third-party beauty filters. |
| [onGLContextDestroy](https://www.tencentcloud.com/document/product/647/50771#18827408d6e4c449f341b875ced98d48) | The OpenGL context in the SDK was destroyed. |

## Callback of custom audio processing

| FuncList | DESC |
| --- | --- |
| [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2012baeb6789e1eaabc97764626fd101) | Audio data captured by the local mic and pre-processed by the audio module. |
| [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50771#2a3a126d62184e1cd093e47562f54774) | Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed. |
| [onPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50771#25988e5cee8c6ab0ed83c8be752fd9a6) | Audio data of each remote user before audio mixing. |
| [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50771#59235444572469f2b1458f0a5265676c) | Data mixed from each channel before being submitted to the system for playback. |
| [onMixedAllAudioFrame](https://www.tencentcloud.com/document/product/647/50771#181f1e18e56e79c8614ebc86fe63380b) | Data mixed from all the captured and to-be-played audio in the SDK. |

## Other event callbacks

| FuncList | DESC |
| --- | --- |
| [onLog](https://www.tencentcloud.com/document/product/647/50771#0c0a3b56332927e19453b32de532e2d0) | Printing of local log. |

## Background music preload event callback

| FuncList | DESC |
| --- | --- |
| [onLoadProgress](https://www.tencentcloud.com/document/product/647/50773#252983e16058385423c9b198b01cb69e) | Background music preload progress. |
| [onLoadError](https://www.tencentcloud.com/document/product/647/50773#1842628ca4d7f36f4858449f61a02440) | Background music preload error. |

## Callback of playing background music

| FuncList | DESC |
| --- | --- |
| [onStart](https://www.tencentcloud.com/document/product/647/50773#bac31892ad2f5910c3d256b01a61e81e) | Background music started. |
| [onPlayProgress](https://www.tencentcloud.com/document/product/647/50773#386181aa98f75be9af4c612f33ad8c8d) | Playback progress of background music. |
| [onComplete](https://www.tencentcloud.com/document/product/647/50773#f15898805455a229bceebf717dc0c84c) | Background music ended. |

## Voice effect APIs

| FuncList | DESC |
| --- | --- |
| [enableVoiceEarMonitor](https://www.tencentcloud.com/document/product/647/50773#ce206abf19487155ebafe9f456bc84b0) | Enabling in-ear monitoring. |
| [setVoiceEarMonitorVolume](https://www.tencentcloud.com/document/product/647/50773#de297f1ab27a50566e80dc41ffee0faf) | Setting in-ear monitoring volume. |
| [setVoiceReverbType](https://www.tencentcloud.com/document/product/647/50773#b2c60a1394dcd44551b2253666ffbb5c) | Setting voice reverb effects. |
| [setVoiceChangerType](https://www.tencentcloud.com/document/product/647/50773#f9cfcc00f81b02d9f1b1526462d8418e) | Setting voice changing effects. |
| [setVoiceCaptureVolume](https://www.tencentcloud.com/document/product/647/50773#79d19bbc256e38dd8fc49d827fad81e4) | Setting speech volume. |
| [setVoicePitch](https://www.tencentcloud.com/document/product/647/50773#611b42876c3252c9210eac5fad77f75b) | Setting speech pitch. |

## Background music APIs

| FuncList | DESC |
| --- | --- |
| [setMusicObserver](https://www.tencentcloud.com/document/product/647/50773#d536291b7952f338944913ad467460d2) | Setting the background music callback. |
| [startPlayMusic](https://www.tencentcloud.com/document/product/647/50773#aacead5ce840018e0505825e2b942052) | Starting background music. |
| [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50773#be8c49a0723691a13da9d0b1a21ad6ab) | Stopping background music. |
| [pausePlayMusic](https://www.tencentcloud.com/document/product/647/50773#4023582e7d64ac4b95619a1ef8d4e2d7) | Pausing background music. |
| [resumePlayMusic](https://www.tencentcloud.com/document/product/647/50773#be322cd251e6920b0d3aa53d97ef1312) | Resuming background music. |
| [setAllMusicVolume](https://www.tencentcloud.com/document/product/647/50773#ba5ca3fa89c2c6200e1d5065a0f91e4a) | Setting the local and remote playback volume of background music. |
| [setMusicPublishVolume](https://www.tencentcloud.com/document/product/647/50773#b627e25338fa8c8539be389a9725bc82) | Setting the remote playback volume of a specific music track. |
| [setMusicPlayoutVolume](https://www.tencentcloud.com/document/product/647/50773#967877f3fb37950e281ee618a1b2b778) | Setting the local playback volume of a specific music track. |
| [setMusicPitch](https://www.tencentcloud.com/document/product/647/50773#ff5c217848d5ef6d6a7dab5367529013) | Adjusting the pitch of background music. |
| [setMusicSpeedRate](https://www.tencentcloud.com/document/product/647/50773#eed882f556c1504fcac185b16de63e6c) | Changing the speed of background music. |
| [getMusicCurrentPosInMS](https://www.tencentcloud.com/document/product/647/50773#1a204f26c0098cbd37620587ca957613) | Getting the playback progress (ms) of background music. |
| [getMusicDurationInMS](https://www.tencentcloud.com/document/product/647/50773#9ad2a04d0e58d8a522c99c34f9c3e3fb) | Getting the total length (ms) of background music. |
| [seekMusicToPosInTime](https://www.tencentcloud.com/document/product/647/50773#ff4023335909d5f2e340da1bf261cf83) | Setting the playback progress (ms) of background music. |
| [setMusicScratchSpeedRate](https://www.tencentcloud.com/document/product/647/50773#be170f854565a69c739b4b6b3f4564e9) | Adjust the speed change effect of the scratch disc. |
| [setPreloadObserver](https://www.tencentcloud.com/document/product/647/50773#e1b6e2bc56c578665b95a2136811f036) | Setting music preload callback. |
| [preloadMusic](https://www.tencentcloud.com/document/product/647/50773#342eee5266978a1d609ae10cc0e05dc8) | Preload background music. |
| [getMusicTrackCount](https://www.tencentcloud.com/document/product/647/50773#d54ff7c549f20eee445120d68fc1f354) | Get the number of tracks of background music. |
| [setMusicTrack](https://www.tencentcloud.com/document/product/647/50773#4bf48f6bde1b5f585fbfbfd622c69971) | Specify the playback track of background music. |

## Device APIs

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
| [stopMicDeviceTest](https://www.tencentcloud.com/document/product/647/50774#cd9086b5a20cf68057c2f74541781028) | Ending mic testing (for desktop OS). |
| [startSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50774#172044ecaba3934d3056dc14dd5a4306) | Starting speaker testing (for desktop OS). |
| [stopSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50774#f8ae44f6c8b4a34c2d0152009ed0447a) | Ending speaker testing (for desktop OS). |
| [setApplicationPlayVolume](https://www.tencentcloud.com/document/product/647/50774#2c64c587956888b01d42a98f3f6b4920) | Setting the volume of the current process in the volume mixer (for Windows). |
| [getApplicationPlayVolume](https://www.tencentcloud.com/document/product/647/50774#b174ef28c2d73868d18900a880e6fb5a) | Getting the volume of the current process in the volume mixer (for Windows). |
| [setApplicationMuteState](https://www.tencentcloud.com/document/product/647/50774#066978eb11cac8c3fb5381262d22c05f) | Muting the current process in the volume mixer (for Windows). |
| [getApplicationMuteState](https://www.tencentcloud.com/document/product/647/50774#3c79d03fa504902dd6a7dbc6f820bbe7) | Querying whether the current process is muted in the volume mixer (for Windows). |
| [setCameraCapturerParam](https://www.tencentcloud.com/document/product/647/50774#72bae8b9c2f0e059caccfee5984c5088) | Set camera acquisition preferences. |
| [setDeviceObserver](https://www.tencentcloud.com/document/product/647/50774#cd81927639621556c20a5be90371b8c0) | set onDeviceChanged callback. |

## Disused APIs

| FuncList | DESC |
| --- | --- |
| [setSystemVolumeType](https://www.tencentcloud.com/document/product/647/50774#9356758d7c8374559bd2e82f5a23a383) | Setting the system volume type (for mobile OS). |


---
*Source: [https://trtc.io/document/35131](https://trtc.io/document/35131)*
