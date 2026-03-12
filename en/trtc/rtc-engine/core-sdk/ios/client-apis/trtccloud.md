# TRTCCloud

Copyright (c) 2021 Tencent. All rights reserved.

Module:   TRTCCloud @ TXLiteAVSDK

Function: TRTC's main feature API

Version: 13.0

**TRTCCloud**

## TRTCCloud

| FuncList | DESC |
| --- | --- |
| [sharedInstance](https://www.tencentcloud.com/document/product/647/50754#6bb80f84c5674f5fa98cf67080909c71) | Create TRTCCloud instance (singleton mode). |
| [destroySharedInstance](https://www.tencentcloud.com/document/product/647/50754#efdff42059de072cfccbb4fcf1bc9646) | Terminate TRTCCloud instance (singleton mode). |
| [addDelegate:](https://www.tencentcloud.com/document/product/647/50754#e227a9126fee9a548fec6d0051326ffc) | Add TRTC event callback. |
| [removeDelegate:](https://www.tencentcloud.com/document/product/647/50754#203bf0b8d403ecda3beafd1fc386155c) | Remove TRTC event callback. |
| [delegateQueue](https://www.tencentcloud.com/document/product/647/50754#3d350e9088c246f32d434ce3514ed9e8) | Set the queue that drives the TRTCCloudDelegate event callback. |
| [enterRoom:appScene:](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) | Enter room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/50754#812a3ac0ad44e274ef4c9213ab0d4a54) | Exit room. |
| [switchRole:](https://www.tencentcloud.com/document/product/647/50754#fd719f2e52ce49aea7a6c3796ed582cd) | Switch role. |
| [switchRole:privateMapKey:](https://www.tencentcloud.com/document/product/647/50754#4cda7adeb443b4e308a288d908963a5e) | Switch role(support permission credential). |
| [switchRoom:](https://www.tencentcloud.com/document/product/647/50754#10ebaed6c26e9f5d83938499b9f6be71) | Switch room. |
| [connectOtherRoom:](https://www.tencentcloud.com/document/product/647/50754#ffc25a3664d85ba2a5359da8026826fa) | Request cross-room call. |
| [disconnectOtherRoom](https://www.tencentcloud.com/document/product/647/50754#10acf09e35ca6dbff613b60791b0e515) | Exit cross-room call. |
| [setDefaultStreamRecvMode:video:](https://www.tencentcloud.com/document/product/647/50754#b2a93b2135b0d8a1a91bd2770b761fb1) | Set subscription mode (which must be set before room entry for it to take effect). |
| [createSubCloud](https://www.tencentcloud.com/document/product/647/50754#ef0c71ed30f70b6b733cf988c5953f79) | Create room subinstance (for concurrent multi-room listen/watch). |
| [destroySubCloud:](https://www.tencentcloud.com/document/product/647/50754#758a8b91a445756b3265b2813dc2ca5f) | Terminate room subinstance. |
| [updateOtherRoomForwardMode:](https://www.tencentcloud.com/document/product/647/50754#a02fd6197c5d4a240becc4c8349c2f9c) | Change the upstream capability of the cross-room anchor in the current room. |
| [startPublishMediaStream:encoderParam:mixingConfig:](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e) | Publish a stream. |
| [updatePublishMediaStream:publishTarget:encoderParam:mixingConfig:](https://www.tencentcloud.com/document/product/647/50754#fc8a7778d8fc91d7dff4c3801b5e5cfe) | Modify publishing parameters. |
| [stopPublishMediaStream:](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e) | Stop publishing. |
| [startLocalPreview:view:](https://www.tencentcloud.com/document/product/647/50754#95dba5aea272e22271bc4602cd5c99fa) | Enable the preview image of local camera (mobile). |
| [startLocalPreview:](https://www.tencentcloud.com/document/product/647/50754#d7fd2b86243b76dede02f51b0d718f4a) | Enable the preview image of local camera (desktop). |
| [updateLocalView:](https://www.tencentcloud.com/document/product/647/50754#0ac84db7f08705ac0d8b2a30232e903c) | Update the preview image of local camera. |
| [stopLocalPreview](https://www.tencentcloud.com/document/product/647/50754#39a28f132a6e183cb05d4ffd15fec991) | Stop camera preview. |
| [muteLocalVideo:mute:](https://www.tencentcloud.com/document/product/647/50754#dd2e6e6669e44947ac869fa038462588) | Pause/Resume publishing local video stream. |
| [setVideoMuteImage:fps:](https://www.tencentcloud.com/document/product/647/50754#287601eb96cdbc871e3ef31c2429da00) | Set placeholder image during local video pause. |
| [startRemoteView:streamType:view:](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) | Subscribe to remote user's video stream and bind video rendering control. |
| [updateRemoteView:streamType:forUser:](https://www.tencentcloud.com/document/product/647/50754#a153fcfe11be9758e9dd45cad087264f) | Update remote user's video rendering control. |
| [stopRemoteView:streamType:](https://www.tencentcloud.com/document/product/647/50754#a6aaf8745d8ecbc6b7d7fa3131338eb5) | Stop subscribing to remote user's video stream and release rendering control. |
| [stopAllRemoteView](https://www.tencentcloud.com/document/product/647/50754#51b999b324bcd51e4d2256c714939bf2) | Stop subscribing to all remote users' video streams and release all rendering resources. |
| [muteRemoteVideoStream:streamType:mute:](https://www.tencentcloud.com/document/product/647/50754#b2d1898fc13a9583f8317cf3d9d40837) | Pause/Resume subscribing to remote user's video stream. |
| [muteAllRemoteVideoStreams:](https://www.tencentcloud.com/document/product/647/50754#8414e579076b74d5ecf4497107414697) | Pause/Resume subscribing to all remote users' video streams. |
| [setVideoEncoderParam:](https://www.tencentcloud.com/document/product/647/50754#2add5add2f68df49f042ff400571ae48) | Set the encoding parameters of video encoder. |
| [setNetworkQosParam:](https://www.tencentcloud.com/document/product/647/50754#8df6ae508d4a48a32749b20aebc370cd) | Set network quality control parameters. |
| [setLocalRenderParams:](https://www.tencentcloud.com/document/product/647/50754#d32d9dde71a2485a76223d003d95c082) | Set the rendering parameters of local video image. |
| [setRemoteRenderParams:streamType:params:](https://www.tencentcloud.com/document/product/647/50754#8a2b406ea2817c2feb2336d92eb7af20) | Set the rendering mode of remote video image. |
| [enableEncSmallVideoStream:withQuality:](https://www.tencentcloud.com/document/product/647/50754#73531b17f6a66de14fc7dd1acd429f16) | Enable dual-channel encoding mode with big and small images. |
| [setRemoteVideoStreamType:type:](https://www.tencentcloud.com/document/product/647/50754#08d3c61370ba37b58f5d99469af76552) | Switch the big/small image of specified remote user. |
| [snapshotVideo:type:sourceType:](https://www.tencentcloud.com/document/product/647/50754#732e96881714e8af4872df0309b1d65b) | Screencapture video. |
| [setPerspectiveCorrectionWithUser:srcPoints:dstPoints:](https://www.tencentcloud.com/document/product/647/50754#c4adb14d0bd7b0e745ac646cd291cea5) | Sets perspective correction coordinate points. |
| [setGravitySensorAdaptiveMode:](https://www.tencentcloud.com/document/product/647/50754#790bcd4a0b0848f0cd3e2fe903d4ad89) | Set the adaptation mode of gravity sensing (version 11.7 and above). |
| [startLocalAudio:](https://www.tencentcloud.com/document/product/647/50754#df3c633d8a6277d5271813f9fac58cb9) | Enable local audio capturing and publishing. |
| [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50754#261e73f11221bdafb889bccd45b6d5d4) | Stop local audio capturing and publishing. |
| [muteLocalAudio:](https://www.tencentcloud.com/document/product/647/50754#b84fc7c80e899aa2e9815c9b6bfaa69c) | Pause/Resume publishing local audio stream. |
| [muteRemoteAudio:mute:](https://www.tencentcloud.com/document/product/647/50754#323bb92ad3d884c6c01d9842e3e350a3) | Pause/Resume playing back remote audio stream. |
| [muteAllRemoteAudio:](https://www.tencentcloud.com/document/product/647/50754#952383bbbef3e0d4cb5be4ea1d0ffca8) | Pause/Resume playing back all remote users' audio streams. |
| [setAudioRoute:](https://www.tencentcloud.com/document/product/647/50754#4566aecb07d50358ffb3cfd573b1148e) | Set audio route. |
| [setRemoteAudioVolume:volume:](https://www.tencentcloud.com/document/product/647/50754#96da6f660c11337bead71872deb5268f) | Set the audio playback volume of remote user. |
| [setAudioCaptureVolume:](https://www.tencentcloud.com/document/product/647/50754#7b85cce8049a984394c664b787394895) | Set the capturing volume of local audio. |
| [getAudioCaptureVolume](https://www.tencentcloud.com/document/product/647/50754#6c021be9bdba28b883aebe9c12bce007) | Get the capturing volume of local audio. |
| [setAudioPlayoutVolume:](https://www.tencentcloud.com/document/product/647/50754#e84fd297371020125d16a408c7959e38) | Set the playback volume of remote audio. |
| [getAudioPlayoutVolume](https://www.tencentcloud.com/document/product/647/50754#0883db89717618ca5f1c2c25aa6287da) | Get the playback volume of remote audio. |
| [enableAudioVolumeEvaluation:withParams:](https://www.tencentcloud.com/document/product/647/50754#b8cb5a5ac09c8e46fcdf98f0acb2e792) | Enable volume reminder. |
| [startAudioRecording:](https://www.tencentcloud.com/document/product/647/50754#e69600672eeec74c5ec77b33c90205fe) | Start audio recording. |
| [stopAudioRecording](https://www.tencentcloud.com/document/product/647/50754#0d75b463c4ab899ef1954ca8c03e38d6) | Stop audio recording. |
| [startLocalRecording:](https://www.tencentcloud.com/document/product/647/50754#622793b0e472c04351886ba0a6826140) | Start local media recording. |
| [stopLocalRecording](https://www.tencentcloud.com/document/product/647/50754#4fe2c8c6efe048db10a347ac226bef34) | Stop local media recording. |
| [setRemoteAudioParallelParams:](https://www.tencentcloud.com/document/product/647/50754#336aa550d5f07272c5667fcae2260d74) | Set the parallel strategy of remote audio streams. |
| [enable3DSpatialAudioEffect:](https://www.tencentcloud.com/document/product/647/50754#25befca287eef6b30e01106776ab781c) | Enable 3D spatial effect. |
| [updateSelf3DSpatialPosition](https://www.tencentcloud.com/document/product/647/50754#5c71e032142f7e7f9a8f698d6dec107e) | Update self position and orientation for 3D spatial effect. |
| [updateRemote3DSpatialPosition:](https://www.tencentcloud.com/document/product/647/50754#028bd569998b6be166e76067f80c451c) | Update the specified remote user's position for 3D spatial effect. |
| [set3DSpatialReceivingRange:range:](https://www.tencentcloud.com/document/product/647/50754#a698502189e8669d492d63ba953824d2) | Set the maximum 3D spatial attenuation range for userId's audio stream. |
| [getDeviceManager](https://www.tencentcloud.com/document/product/647/50754#db8daa4a00cfdd6e2b2d436ace8b54e0) | Get device management class (TXDeviceManager). |
| [getBeautyManager](https://www.tencentcloud.com/document/product/647/50754#a74f40ea545fcc505d53f767ff09c71e) | Get beauty filter management class (TXBeautyManager). |
| [setWatermark:streamType:rect:](https://www.tencentcloud.com/document/product/647/50754#1e65eb4cba6287f43eefab07aab02895) | Add watermark. |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/50754#324d36f56aaba193d6ea8c2ed04b3633) | Get sound effect management class (TXAudioEffectManager). |
| [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50754#755f9f590bf398deb0c538b32a2aede2) | Enable system audio capturing(iOS not supported). |
| [stopSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50754#3da3978da7aa2b81e524fba4f7bb05a5) | Stop system audio capturing(iOS not supported). |
| [setSystemAudioLoopbackVolume:](https://www.tencentcloud.com/document/product/647/50754#679fb63113ef1285208c35c406a74ff0) | Set the volume of system audio capturing. |
| [startScreenCaptureInApp:encParam:](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194) | Start in-app screen sharing (for iOS 13.0 and above only). |
| [startScreenCaptureByReplaykit:encParam:appGroup:](https://www.tencentcloud.com/document/product/647/50754#a40e37e782a049150b3314810516bf44) | Start system-level screen sharing (for iOS 11.0 and above only). |
| [startScreenCapture:streamType:encParam:](https://www.tencentcloud.com/document/product/647/50754#a5556ab15765655b288ad33f8f49176d) | Start screen sharing. |
| [stopScreenCapture](https://www.tencentcloud.com/document/product/647/50754#f07463b8a6a3ee03680356b3fb07364c) | Stop screen sharing. |
| [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/50754#77ba0ef5a41b95cf46da6cd0a539279e) | Pause screen sharing. |
| [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/50754#34bdf61c283c09fd3c12fdab1d07f4c1) | Resume screen sharing. |
| [getScreenCaptureSourcesWithThumbnailSize:iconSize:](https://www.tencentcloud.com/document/product/647/50754#d99a40c2e0806381169a238674f1e91f) | Enumerate shareable screens and windows (for macOS only). |
| [selectScreenCaptureTarget:rect:capturesCursor:highlight:](https://www.tencentcloud.com/document/product/647/50754#dbc26a9989e702f9ff84f3e04ce4bb1a) | Select the screen or window to share (for macOS only). |
| [setSubStreamEncoderParam:](https://www.tencentcloud.com/document/product/647/50754#8b9ac12176384adfb56850af375ece28) | Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems). |
| [setSubStreamMixVolume:](https://www.tencentcloud.com/document/product/647/50754#db7473ab998472ea212719abee1648ae) | Set the audio mixing volume of screen sharing (for desktop systems only). |
| [addExcludedShareWindow:](https://www.tencentcloud.com/document/product/647/50754#02b91750598485a72c33b97c5a60ec5f) | Add specified windows to the exclusion list of screen sharing (for desktop systems only). |
| [removeExcludedShareWindow:](https://www.tencentcloud.com/document/product/647/50754#18f15ee58d38ec0a2f6b8a617fe93493) | Remove specified windows from the exclusion list of screen sharing (for desktop systems only). |
| [removeAllExcludedShareWindows](https://www.tencentcloud.com/document/product/647/50754#8a497b74df32ca732baefe52fb441548) | Remove all windows from the exclusion list of screen sharing (for desktop systems only). |
| [addIncludedShareWindow:](https://www.tencentcloud.com/document/product/647/50754#8b799914db427278d83a0ffbd5e7ac06) | Add specified windows to the inclusion list of screen sharing (for desktop systems only). |
| [removeIncludedShareWindow:](https://www.tencentcloud.com/document/product/647/50754#0ed6a671adcf4e9a36b49ddc825a4cc2) | Remove specified windows from the inclusion list of screen sharing (for desktop systems only). |
| [removeAllIncludedShareWindows](https://www.tencentcloud.com/document/product/647/50754#ac3348c20495bc83e0599fe86359d357) | Remove all windows from the inclusion list of screen sharing (for desktop systems only). |
| [enableCustomVideoCapture:enable:](https://www.tencentcloud.com/document/product/647/50754#e404d58245ffc8acdaef99a19bb3795c) | Enable/Disable custom video capturing mode. |
| [sendCustomVideoData:frame:](https://www.tencentcloud.com/document/product/647/50754#2ec8cee427b69adc1b75be389c7eaef7) | Deliver captured video frames to SDK. |
| [enableCustomAudioCapture:](https://www.tencentcloud.com/document/product/647/50754#5fc1dfff7407b1d7a8eb0e985750abc5) | Enable custom audio capturing mode. |
| [sendCustomAudioData:](https://www.tencentcloud.com/document/product/647/50754#065fa14dfdbe241cd1d0286bf010388a) | Deliver captured audio data to SDK. |
| [enableMixExternalAudioFrame:playout:](https://www.tencentcloud.com/document/product/647/50754#714890054aef9e46d47aff9afa2b114d) | Enable/Disable custom audio track. |
| [mixExternalAudioFrame:](https://www.tencentcloud.com/document/product/647/50754#fae00625468052474250aef4d0f602c6) | Mix custom audio track into SDK. |
| [setMixExternalAudioVolume:playoutVolume:](https://www.tencentcloud.com/document/product/647/50754#fe002f6bc1551d26987f8b10a7906ac3) | Set the publish volume and playback volume of mixed custom audio track. |
| [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50754#d7dfdbb97b24b9304897c7acf776d803) | Generate custom capturing timestamp. |
| [setLocalVideoProcessDelegete:pixelFormat:bufferType:](https://www.tencentcloud.com/document/product/647/50754#8a00be9d6bdbde50550f76b1778fc713) | Set video data callback for third-party beauty filters. |
| [setLocalVideoRenderDelegate:pixelFormat:bufferType:](https://www.tencentcloud.com/document/product/647/50754#942d950756d625549380fe112550e0eb) | Set the callback of custom rendering for local video. |
| [setRemoteVideoRenderDelegate:delegate:pixelFormat:bufferType:](https://www.tencentcloud.com/document/product/647/50754#ffac4d7ccbf7a1dab155ebfecc006f9c) | Set the callback of custom rendering for remote video. |
| [setAudioFrameDelegate:](https://www.tencentcloud.com/document/product/647/50754#0c09123a785cbc38cf0243908acb205d) | Set custom audio data callback. |
| [setCapturedAudioFrameDelegateFormat:](https://www.tencentcloud.com/document/product/647/50754#c38b0298229ea804285011e623586463) | Set the callback format of audio frames captured by local mic. |
| [setLocalProcessedAudioFrameDelegateFormat:](https://www.tencentcloud.com/document/product/647/50754#898c87a404497d7c432120494215dd53) | Set the callback format of preprocessed local audio frames. |
| [setMixedPlayAudioFrameDelegateFormat:](https://www.tencentcloud.com/document/product/647/50754#7baa39b55924b0ca5a42d5859807e3e4) | Set the callback format of audio frames to be played back by system. |
| [enableCustomAudioRendering:](https://www.tencentcloud.com/document/product/647/50754#24703ae7507b94e475a89700e8b1bb9b) | Enabling custom audio playback. |
| [getCustomAudioRenderingFrame:](https://www.tencentcloud.com/document/product/647/50754#d0c11de324866d2a2c8555567a3963d4) | Getting playable audio data. |
| [sendCustomCmdMsg:data:reliable:ordered:](https://www.tencentcloud.com/document/product/647/50754#65a0ef621d0fdc876f649fc8b20ca117) | Use UDP channel to send custom message to all users in room. |
| [sendSEIMsg:repeatCount:](https://www.tencentcloud.com/document/product/647/50754#f1c4a686a1e513f8dce8b8d57cc5bbe8) | Use SEI channel to send custom message to all users in room. |
| [startSpeedTest:](https://www.tencentcloud.com/document/product/647/50754#9446ef81737de395b79baa311622f04e) | Start network speed test (used before room entry). |
| [stopSpeedTest](https://www.tencentcloud.com/document/product/647/50754#c039fb88d4d55a5ba7d6b4e48120e569) | Stop network speed test. |
| [getSDKVersion](https://www.tencentcloud.com/document/product/647/50754#483cc6aeb60177fca185ac596ce47c5c) | Get SDK version information. |
| [setLogLevel:](https://www.tencentcloud.com/document/product/647/50754#76af89e47bf1be956d6bea99277b21ad) | Set log output level. |
| [setConsoleEnabled:](https://www.tencentcloud.com/document/product/647/50754#4acb68e95c32c395723d66ca1437348a) | Enable/Disable console log printing. |
| [setLogCompressEnabled:](https://www.tencentcloud.com/document/product/647/50754#fe3626e347f2d7cdd7bad55630255901) | Enable/Disable local log compression. |
| [setLogDirPath:](https://www.tencentcloud.com/document/product/647/50754#b37af0c781ddf50244c1a81370384c74) | Set local log storage path. |
| [setLogDelegate:](https://www.tencentcloud.com/document/product/647/50754#0e9c1d84c3eaea94d94b31eb460acd3d) | Set log callback. |
| [showDebugView:](https://www.tencentcloud.com/document/product/647/50754#237b5598918783a30b64118a6215d9d2) | Display dashboard. |
| [setDebugViewMargin:margin:](https://www.tencentcloud.com/document/product/647/50754#0954b98d38ecc392a3330babbcb286ac) | Set dashboard margin. |
| [callExperimentalAPI:](https://www.tencentcloud.com/document/product/647/50754#c052372d1d99c72d35109f8c33d23fc3) | Call experimental APIs. |
| [enablePayloadPrivateEncryption:params:](https://www.tencentcloud.com/document/product/647/50754#999b4ba6e9f3bdba882955507f30df02) | Enable or disable private encryption of media streams. |

## sharedInstance

**sharedInstance**

**Create TRTCCloud instance (singleton mode).**

> **Note**1. Please use [destroySharedInstance](https://www.tencentcloud.com/document/product/647/50754#efdff42059de072cfccbb4fcf1bc9646) to release the object pointer.

## destroySharedInstance

**destroySharedInstance**

**Terminate TRTCCloud instance (singleton mode).**

## addDelegate:

**addDelegate:**

| - (void)addDelegate: | (id<[TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04)>)delegate |
| --- | --- |

**Add TRTC event callback.**

You can use [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04) to get various event notifications from the SDK, such as error codes, warning codes, and audio/video status parameters.

## removeDelegate:

**removeDelegate:**

| - (void)removeDelegate: | (id<[TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04)>)delegate |
| --- | --- |

**Remove TRTC event callback.**

## delegateQueue

**delegateQueue**

**Set the queue that drives the $TRTCCloudDelegate$ event callback.**

If you do not specify a ` delegateQueue `, the SDK will use ` MainQueue ` as the queue for driving [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04) event callbacks by default.

In other words, if you do not set the ` delegateQueue ` attribute, all callback functions in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04) will be driven by ` MainQueue `.

> **Note**If you specify a ` delegateQueue `, please do not manipulate the UI in the [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04) callback function; otherwise, thread safety issues will occur.

## enterRoom:appScene:

**enterRoom:appScene:**

| - (void)enterRoom: | ([TRTCParams](https://www.tencentcloud.com/document/product/647/50760#a1de1e93c6cfc6be81dd4152b9e4c190) *)param |
| --- | --- |
| appScene: | ([TRTCAppScene](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1))scene |

**Enter room.**

All TRTC users need to enter a room before they can "publish" or "subscribe to" audio/video streams. "Publishing" refers to pushing their own streams to the cloud, and "subscribing to" refers to pulling the streams of other users in the room from the cloud.

When calling this API, you need to specify your application scenario ([TRTCAppScene](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)) to get the best audio/video transfer experience. We provide the following four scenarios for your choice:

- [TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1):

Video call scenario. Use cases: [one-to-one video call], [video conferencing with up to 300 participants], [online medical diagnosis], [small class], [video interview], etc.

In this scenario, each room supports up to 300 concurrent online users, and up to 50 of them can speak simultaneously.

- [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1):

Audio call scenario. Use cases: [one-to-one audio call], [audio conferencing with up to 300 participants], [audio chat], [online Werewolf], etc.

In this scenario, each room supports up to 300 concurrent online users, and up to 50 of them can speak simultaneously.

- [TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1):

Live streaming scenario. Use cases: [low-latency video live streaming], [interactive classroom for up to 100,000 participants], [live video competition], [video dating room], [remote training], [large-scale conferencing], etc.

In this scenario, each room supports up to 100,000 concurrent online users, but you should specify the user roles: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b)) or audience ([TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b)).

- [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1):

Audio chat room scenario. Use cases: [Clubhouse], [online karaoke room], [music live room], [FM radio], etc.

In this scenario, each room supports up to 100,000 concurrent online users, but you should specify the user roles: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b)) or audience ([TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b)).

After calling this API, you will receive the ` onEnterRoom(result) ` callback from [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04):

- If room entry succeeded, the ` result ` parameter will be a positive number (` result ` > 0), indicating the time in milliseconds (ms) between function call and room entry.
- If room entry failed, the ` result ` parameter will be a negative number (` result ` < 0), indicating the TXLiteAVError for room entry failure.

| Param | DESC |
| --- | --- |
| param | Room entry parameter, which is used to specify the user's identity, role, authentication credentials, and other information. For more information, please see [TRTCParams](https://www.tencentcloud.com/document/product/647/50760#a1de1e93c6cfc6be81dd4152b9e4c190). |
| scene | Application scenario, which is used to specify the use case. The same [TRTCAppScene](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1) should be configured for all users in the same room. |

> **Note**1. If ` scene ` is specified as [TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1), you must use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50760#a1de1e93c6cfc6be81dd4152b9e4c190) to specify the role of the current user in the room.2. The same ` scene ` should be configured for all users in the same room.3. Please try to ensure that [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) and [exitRoom](https://www.tencentcloud.com/document/product/647/50754#812a3ac0ad44e274ef4c9213ab0d4a54) are used in pair; that is, please make sure that "the previous room is exited before the next room is entered"; otherwise, many issues may occur.

## exitRoom

**exitRoom**

**Exit room.**

Calling this API will allow the user to leave the current audio or video room and release the camera, mic, speaker, and other device resources.

After resources are released, the SDK will use the ` onExitRoom() ` callback in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04) to notify you.

If you need to call [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) again or switch to the SDK of another provider, we recommend you wait until you receive the [onExitRoom](https://www.tencentcloud.com/document/product/647/50755#95c38564f6c910cbb33746046da9cb8d) callback, so as to avoid the problem of the camera or mic being occupied.

## switchRole:

**switchRole:**

| -(void)switchRole: | ([TRTCRoleType](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b))role |
| --- | --- |

**Switch role.**

This API is used to switch the user role between ` anchor ` and ` audience `.

As video live rooms and audio chat rooms need to support an audience of up to 100,000 concurrent online users, the rule "only anchors can publish their audio/video streams" has been set. Therefore, when some users want to publish their streams (so that they can interact with anchors), they need to switch their role to "anchor" first.

You can use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50760#a1de1e93c6cfc6be81dd4152b9e4c190) during room entry to specify the user role in advance or use the ` switchRole ` API to switch roles after room entry.

| Param | DESC |
| --- | --- |
| role | Role, which is ` anchor ` by default: [TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b): anchor, who can publish their audio/video streams. Up to 50 anchors are allowed to publish streams at the same time in one room. [TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b): audience, who cannot publish their audio/video streams, but can only watch streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/50754#fd719f2e52ce49aea7a6c3796ed582cd). One room supports an audience of up to 100,000 concurrent online users. |

> **Note**1. This API is only applicable to two scenarios: live streaming ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)) and audio chat room ([TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)).2. If the ` scene ` you specify in [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) is [TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1), please do not call this API.

## switchRole:privateMapKey:

**switchRole:privateMapKey:**

| -(void)switchRole: | ([TRTCRoleType](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b))role |
| --- | --- |
| privateMapKey: | (NSString*)privateMapKey |

**Switch role(support permission credential).**

This API is used to switch the user role between ` anchor ` and ` audience `.

As video live rooms and audio chat rooms need to support an audience of up to 100,000 concurrent online users, the rule "only anchors can publish their audio/video streams" has been set. Therefore, when some users want to publish their streams (so that they can interact with anchors), they need to switch their role to "anchor" first.

You can use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50760#a1de1e93c6cfc6be81dd4152b9e4c190) during room entry to specify the user role in advance or use the ` switchRole ` API to switch roles after room entry.

| Param | DESC |
| --- | --- |
| privateMapKey | Permission credential used for permission control. If you want only users with the specified ` userId ` values to enter a room or push streams, you need to use ` privateMapKey ` to restrict the permission. We recommend you use this parameter only if you have high security requirements. For more information, please see [Enabling Advanced Permission Control](https://www.tencentcloud.com/document/product/647/35157). |
| role | Role, which is ` anchor ` by default: [TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b): anchor, who can publish their audio/video streams. Up to 50 anchors are allowed to publish streams at the same time in one room. [TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50760#874dbd6062bbf1384648ca9f9054aa5b): audience, who cannot publish their audio/video streams, but can only watch streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/50754#fd719f2e52ce49aea7a6c3796ed582cd). One room supports an audience of up to 100,000 concurrent online users. |

> **Note**1. This API is only applicable to two scenarios: live streaming ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)) and audio chat room ([TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1)).2. If the ` scene ` you specify in [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) is [TRTCAppSceneVideoCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneAudioCall](https://www.tencentcloud.com/document/product/647/50760#50498dba914e98bc767b83dc0c72a0a1), please do not call this API.

## switchRoom:

**switchRoom:**

| - (void)switchRoom: | ([TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/50760#d43f5dc42762839497bd8586ac2091e3) *)config |
| --- | --- |

**Switch room.**

This API is used to quickly switch a user from one room to another.

- If the user's role is ` audience `, calling this API is equivalent to ` exitRoom ` (current room) + ` enterRoom ` (new room).
- If the user's role is ` anchor `, the API will retain the current audio/video publishing status while switching the room; therefore, during the room switch, camera preview and sound capturing will not be interrupted.

This API is suitable for the online education scenario where the supervising teacher can perform fast room switch across multiple rooms. In this scenario, using ` switchRoom ` can get better smoothness and use less code than ` exitRoom + enterRoom `.

The API call result will be called back through ` onSwitchRoom(errCode, errMsg) ` in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

| Param | DESC |
| --- | --- |
| config | Room parameter. For more information, please see [TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/50760#d43f5dc42762839497bd8586ac2091e3). |

> **Note**Due to the requirement for compatibility with legacy versions of the SDK, the ` config ` parameter contains both ` roomId ` and ` strRoomId ` parameters. You should pay special attention as detailed below when specifying these two parameters:1. If you decide to use ` strRoomId `, then set ` roomId ` to 0. If both are specified, ` roomId ` will be used.2. All rooms need to use either ` strRoomId ` or ` roomId ` at the same time. They cannot be mixed; otherwise, there will be many unexpected bugs.

## connectOtherRoom:

**connectOtherRoom:**

| - (void)connectOtherRoom: | (NSString *)param |
| --- | --- |

**Request cross-room call.**

By default, only users in the same room can make audio/video calls with each other, and the audio/video streams in different rooms are isolated from each other.

However, you can publish the audio/video streams of an anchor in another room to the current room by calling this API. At the same time, this API will also publish the local audio/video streams to the target anchor's room.

In other words, you can use this API to share the audio/video streams of two anchors in two different rooms, so that the audience in each room can watch the streams of these two anchors. This feature can be used to implement anchor competition.

The result of requesting cross-room call will be returned through the [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50755#b18062a114b045be21872948fdf4dbad) callback in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

For example, after anchor A in room "101" uses ` connectOtherRoom() ` to successfully call anchor B in room "102":

- All users in room "101" will receive the ` onRemoteUserEnterRoom(B) ` and ` onUserVideoAvailable(B,YES) ` event callbacks of anchor B; that is, all users in room "101" can subscribe to the audio/video streams of anchor B.
- All users in room "102" will receive the ` onRemoteUserEnterRoom(A) ` and ` onUserVideoAvailable(A,YES) ` event callbacks of anchor A; that is, all users in room "102" can subscribe to the audio/video streams of anchor A.

![](https://qcloudimg.tencent-cloud.cn/raw/c5e6c72fc163ad5c0b6b7b00e1da55b5.png)

For compatibility with subsequent extended fields for cross-room call, parameters in JSON format are used currently.

Case 1: numeric room ID

If anchor A in room "101" wants to co-anchor with anchor B in room "102", then anchor A needs to pass in {"roomId": 102, "userId": "userB"} when calling this API.

Below is the sample code:

```
  NSMutableDictionaryjsonDict = [[NSMutableDictionary alloc] init];  [jsonDict setObject:@(102) forKey:@"roomId"];  [jsonDict setObject:@"userB" forKey:@"userId"];  NSData* jsonData = [NSJSONSerialization dataWithJSONObject:jsonDict options:NSJSONWritingPrettyPrinted error:nil];  NSString* jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];  [trtc connectOtherRoom:jsonString];
```

Case 2: string room ID

If you use a string room ID, please be sure to replace the ` roomId ` in JSON with ` strRoomId `, such as ` {"strRoomId": "102", "userId": "userB"} `

Below is the sample code:

```
  NSMutableDictionaryjsonDict = [[NSMutableDictionary alloc] init];  [jsonDict setObject:@"102" forKey:@"strRoomId"];  [jsonDict setObject:@"userB" forKey:@"userId"];  NSData* jsonData = [NSJSONSerialization dataWithJSONObject:jsonDict options:NSJSONWritingPrettyPrinted error:nil];  NSString* jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];  [trtc connectOtherRoom:jsonString];
```

| Param | DESC |
| --- | --- |
| param | You need to pass in a string parameter in JSON format: ` roomId ` represents the room ID in numeric format, ` strRoomId ` represents the room ID in string format, and ` userId ` represents the user ID of the target anchor. |

## disconnectOtherRoom

**disconnectOtherRoom**

**Exit cross-room call.**

The result will be returned through the ` onDisconnectOtherRoom() ` callback in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

## setDefaultStreamRecvMode:video:

**setDefaultStreamRecvMode:video:**

| - (void)setDefaultStreamRecvMode: | (BOOL)autoRecvAudio |
| --- | --- |
| video: | (BOOL)autoRecvVideo |

**Set subscription mode (which must be set before room entry for it to take effect).**

You can switch between the "automatic subscription" and "manual subscription" modes through this API:

- Automatic subscription: this is the default mode, where the user will immediately receive the audio/video streams in the room after room entry, so that the audio will be automatically played back, and the video will be automatically decoded (you still need to bind the rendering control through the ` startRemoteView ` API).
- Manual subscription: after room entry, the user needs to manually call the [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) API to start subscribing to and decoding the video stream and call the [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/50754#323bb92ad3d884c6c01d9842e3e350a3) (NO) API to start playing back the audio stream.

In most scenarios, users will subscribe to the audio/video streams of all anchors in the room after room entry. Therefore, TRTC adopts the automatic subscription mode by default in order to achieve the best "instant streaming experience".

In your application scenario, if there are many audio/video streams being published at the same time in each room, and each user only wants to subscribe to 1â2 streams of them, we recommend you use the "manual subscription" mode to reduce the traffic costs.

| Param | DESC |
| --- | --- |
| autoRecvAudio | YES: automatic subscription to audio; NO: manual subscription to audio by calling ` muteRemoteAudio(NO) `. Default value: YES |
| autoRecvVideo | YES: automatic subscription to video; NO: manual subscription to video by calling ` startRemoteView `. Default value: YES |

> **Note**1. The configuration takes effect only if this API is called before room entry (enterRoom).2. In the automatic subscription mode, if the user does not call [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) to subscribe to the video stream after room entry, the SDK will automatically stop subscribing to the video stream in order to reduce the traffic consumption.

## createSubCloud

**createSubCloud**

**Create room subinstance (for concurrent multi-room listen/watch).**

` TRTCCloud ` was originally designed to work in the singleton mode, which limited the ability to watch concurrently in multiple rooms.

By calling this API, you can create multiple ` TRTCCloud ` instances, so that you can enter multiple different rooms at the same time to listen/watch audio/video streams.

However, it should be noted that your ability to publish audio and video streams in multiple ` TRTCCloud ` instances will be limited.

This feature is mainly used in the "super small class" use case in the online education scenario to break the limit that "only up to 50 users can publish their audio/video streams simultaneously in one TRTC room".

Below is the sample code:

```
    //In the small room that needs interaction, enter the room as an anchor and push audio and video streams    TRTCCloud *mainCloud = [TRTCCloud sharedInstance];    TRTCParams *mainParams = [[TRTCParams alloc] init];    //Fill your params    mainParams.role = TRTCRoleAnchor;    [mainCloud enterRoom:mainParams appScene:TRTCAppSceneLIVE)];    //...    [mainCloud startLocalPreview:YES view:videoView];    [mainCloud startLocalAudio:TRTCAudioQualityDefault];    //In the large room that only needs to watch, enter the room as an audience and pull audio and video streams    TRTCCloud *subCloud = [mainCloud createSubCloud];    TRTCParams *subParams = [[TRTCParams alloc] init];    //Fill your params    subParams.role = TRTCRoleAudience;    [subCloud enterRoom:subParams appScene:TRTCAppSceneLIVE)];    //...    [subCloud startRemoteView:userId streamType:TRTCVideoStreamTypeBig view:videoView];    //...    //Exit from new room and release it.    [subCloud exitRoom];    [mainCloud destroySubCloud:subCloud];
```

> **Note**1. The same user can enter multiple rooms with different ` roomId ` values by using the same ` userId `.2. Two devices cannot use the same ` userId ` to enter the same room with a specified ` roomId `.3. You can set [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04) separately for different instances to get their own event notifications.4. The same user can push streams in multiple ` TRTCCloud ` instances at the same time, and can also call APIs related to local audio/video in the sub instance. But need to pay attention to: Audio needs to be collected by the microphone or custom data at the same time in all instances, and the result of API calls related to the audio device will be based on the last time; The result of camera-related API call will be based on the last time: [startLocalPreview](https://www.tencentcloud.com/document/product/647/50754#95dba5aea272e22271bc4602cd5c99fa).

**Return Desc:**

` TRTCCloud ` subinstance

## destroySubCloud:

**destroySubCloud:**

| - (void)destroySubCloud: | ([TRTCCloud](https://www.tencentcloud.com/document/product/647/50754#4a6a4b6d9ea12d9f5c26e8452740d65a) *)subCloud |
| --- | --- |

**Terminate room subinstance.**

| Param | DESC |
| --- | --- |
| subCloud |  |

## updateOtherRoomForwardMode:

**updateOtherRoomForwardMode:**

| - (void)updateOtherRoomForwardMode: | (NSString *)param |
| --- | --- |

**Change the upstream capability of the cross-room anchor in the current room.**

By default, after calling the [connectOtherRoom](https://www.tencentcloud.com/document/product/647/50754#ffc25a3664d85ba2a5359da8026826fa) API to make a cross-room call with an anchor in another room, all users in the current room will receive the audio/video streams published by that anchor.

You can use this API to limit the upstream capability of the cross-room anchor in the current room, and prohibit or allow the cross-room anchor to publish audio/video/sub-stream. This behavior will affect all users in the room.

After disabling a certain upstream capability of the cross-room anchor, all users in the current room will no longer receive the corresponding audio/video stream, and cannot subscribe to the corresponding audio/video.

Note that this API can only be called by the anchor who is conducting the cross-room call, and the restrictions set by this API will be reset when the cross-room call is interrupted or the corresponding anchor leaves the room.

The result of calling this API will be returned through the ` onUpdateOtherRoomForwardMode() ` callback in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

For example, in room "101", there is anchor A and audience B, and in room "102", there is anchor C who publishes audio/video streams normally. Anchor A calls ` connectOtherRoom() ` to make a cross-room call with anchor C.

- At this time, both anchor A and audience B will receive the ` onRemoteUserEnterRoom(C) `, ` onUserVideoAvailable(C,YES) `, and ` onUserAudioAvailable(C,YES) ` event callbacks, and can subscribe to the audio/video streams of anchor C.

Later, anchor A calls this API to disable the audio publishing capability of anchor C in the current room.

- After that, the audio stream of anchor C will no longer be published to room "101", and both anchor A and audience B will receive the ` onUserAudioAvailable(C,NO) ` event callback, and cannot subscribe to the audio stream of anchor C by calling ` muteRemoteAudio(C,NO) `.
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

## startPublishMediaStream:encoderParam:mixingConfig:

**startPublishMediaStream:encoderParam:mixingConfig:**

| - (void)startPublishMediaStream: | ([TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50760#11c06c485af4d4bd3b60bc0c883a9a32)*)target |
| --- | --- |
| encoderParam: | (nullable [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50760#22718fe81d94d21ec895cbc11820c726)*)param |
| mixingConfig: | (nullable [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50760#a5a3b285846955f523db70b37449f161)*)config |

**Publish a stream.**

After this API is called, the TRTC server will relay the stream of the local user to a CDN (after transcoding or without transcoding), or transcode and publish the stream to a TRTC room.

You can use the [TRTCPublishMode](https://www.tencentcloud.com/document/product/647/50760#064db271e894d12e1e3ad63bbb1677fb) parameter in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50760#11c06c485af4d4bd3b60bc0c883a9a32) to specify the publishing mode.

| Param | DESC |
| --- | --- |
| config | The On-Cloud MixTranscoding settings. This parameter is invalid in the relay-to-CDN mode. It is required if you transcode and publish the stream to a CDN or to a TRTC room. For details, see [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50760#a5a3b285846955f523db70b37449f161). |
| params | The encoding settings. This parameter is required if you transcode and publish the stream to a CDN or to a TRTC room. If you relay to a CDN without transcoding, to improve the relaying stability and playback compatibility, we also recommend you set this parameter. For details, see [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50760#22718fe81d94d21ec895cbc11820c726). |
| target | The publishing destination. You can relay the stream to a CDN (after transcoding or without transcoding) or transcode and publish the stream to a TRTC room. For details, see [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50760#11c06c485af4d4bd3b60bc0c883a9a32). |

> **Note**1. The SDK will send a task ID to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50755#7793cc61deebd412cb1f1b8c4762cb3e) callback.2. You can start a publishing task only once and cannot initiate two tasks that use the same publishing mode and publishing cdn url. Note the task ID returned, which you need to pass to [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#fc8a7778d8fc91d7dff4c3801b5e5cfe) to modify the publishing parameters or [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e) to stop the task.3. You can specify up to 10 CDN URLs in ` target `. You will be charged only once for transcoding even if you relay to multiple CDNs.4. To avoid causing errors, do not specify the same URLs for different publishing tasks executed at the same time. We recommend you add "sdkappid_roomid_userid_main" to URLs to distinguish them from one another and avoid application conflicts.

## updatePublishMediaStream:publishTarget:encoderParam:mixingConfig:

**updatePublishMediaStream:publishTarget:encoderParam:mixingConfig:**

| - (void)updatePublishMediaStream: | (NSString *)taskId |
| --- | --- |
| publishTarget: | ([TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50760#11c06c485af4d4bd3b60bc0c883a9a32)*)target |
| encoderParam: | (nullable [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50760#22718fe81d94d21ec895cbc11820c726)*)param |
| mixingConfig: | (nullable [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50760#a5a3b285846955f523db70b37449f161)*)config |

**Modify publishing parameters.**

You can use this API to change the parameters of a publishing task initiated by [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e).

| Param | DESC |
| --- | --- |
| config | The On-Cloud MixTranscoding settings. This parameter is invalid in the relay-to-CDN mode. It is required if you transcode and publish the stream to a CDN or to a TRTC room. For details, see [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50760#a5a3b285846955f523db70b37449f161). |
| params | The encoding settings. This parameter is required if you transcode and publish the stream to a CDN or to a TRTC room. If you relay to a CDN without transcoding, to improve the relaying stability and playback compatibility, we recommend you set this parameter. For details, see [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50760#22718fe81d94d21ec895cbc11820c726). |
| target | The publishing destination. You can relay the stream to a CDN (after transcoding or without transcoding) or transcode and publish the stream to a TRTC room. For details, see [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50760#11c06c485af4d4bd3b60bc0c883a9a32). |
| taskId | The task ID returned to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50755#7793cc61deebd412cb1f1b8c4762cb3e) callback. |

> **Note**1. You can use this API to add or remove CDN URLs to publish to (you can publish to up to 10 CDNs at a time). To avoid causing errors, do not specify the same URLs for different tasks executed at the same time.2. You can use this API to switch a relaying task to transcoding or vice versa. For example, in cross-room communication, you can first call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e) to relay to a CDN. When the anchor requests cross-room communication, call this API, passing in the task ID to switch the relaying task to a transcoding task. This can ensure that the live stream and CDN playback are not interrupted (you need to keep the encoding parameters consistent).3. You can not switch output between "only audio", "only video" and "audio and video" for the same task.

## stopPublishMediaStream:

**stopPublishMediaStream:**

| - (void)stopPublishMediaStream: | (NSString *)taskId |
| --- | --- |

**Stop publishing.**

You can use this API to stop a task initiated by [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e).

| Param | DESC |
| --- | --- |
| taskId | The task ID returned to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50755#7793cc61deebd412cb1f1b8c4762cb3e) callback. |

> **Note**1. If the task ID is not saved to your backend, you can call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e) again when an anchor re-enters the room after abnormal exit. The publishing will fail, but the TRTC backend will return the task ID to you.2. If ` taskId ` is left empty, the TRTC backend will end all tasks you started through [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e). You can leave it empty if you have started only one task or want to stop all publishing tasks started by you.

## startLocalPreview:view:

**startLocalPreview:view:**

| - (void)startLocalPreview: | (BOOL)frontCamera |
| --- | --- |
| view: | (nullable TXView *)view |

**Enable the preview image of local camera (mobile).**

If this API is called before [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689), the SDK will only enable the camera and wait until [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) is called before starting push.

If it is called after [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689), the SDK will enable the camera and automatically start pushing the video stream.

When the first camera video frame starts to be rendered, you will receive the ` onCameraDidReady ` callback in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

| Param | DESC |
| --- | --- |
| frontCamera | YES: front camera; NO: rear camera |
| view | Control that carries the video image |

> **Note**If you want to preview the camera image and adjust the beauty filter parameters through ` BeautyManager ` before going live, you can: Scheme 1. Call ` startLocalPreview ` before calling [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689). Scheme 2. Call ` startLocalPreview ` and ` muteLocalVideo(YES) ` after calling [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689).

## startLocalPreview:

**startLocalPreview:**

| - (void)startLocalPreview: | (nullable TXView *)view |
| --- | --- |

**Enable the preview image of local camera (desktop).**

Before this API is called, [setCurrentDevice](https://www.tencentcloud.com/document/product/647/50759#1c0a01aa96ce0aa6c596c654041fbee6) can be called first to select whether to use the desktop device's built-in camera or an external camera.

If this API is called before  [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689), the SDK will only enable the camera and wait until [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689) is called before starting push.

If it is called after  [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689), the SDK will enable the camera and automatically start pushing the video stream.

When the first camera video frame starts to be rendered, you will receive the ` onCameraDidReady ` callback in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

| Param | DESC |
| --- | --- |
| view | Control that carries the video image |

> **Note**If you want to preview the camera image and adjust the beauty filter parameters through ` BeautyManager ` before going live, you can: Scheme 1. Call ` startLocalPreview ` before calling [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689). Scheme 2. Call ` startLocalPreview ` and ` muteLocalVideo(YES) ` after calling [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689).

## updateLocalView:

**updateLocalView:**

| - (void)updateLocalView: | (nullable TXView *)view |
| --- | --- |

**Update the preview image of local camera.**

## stopLocalPreview

**stopLocalPreview**

**Stop camera preview.**

## muteLocalVideo:mute:

**muteLocalVideo:mute:**

| - (void)muteLocalVideo: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| --- | --- |
| mute: | (BOOL)mute |

**Pause/Resume publishing local video stream.**

This API can pause (or resume) publishing the local video image. After the pause, other users in the same room will not be able to see the local image.

This API is equivalent to the two APIs of ` startLocalPreview/stopLocalPreview ` when TRTCVideoStreamTypeBig is specified, but has higher performance and response speed.

The ` startLocalPreview/stopLocalPreview ` APIs need to enable/disable the camera, which are hardware device-related operations, so they are very time-consuming.

In contrast, ` muteLocalVideo ` only needs to pause or allow the data stream at the software level, so it is more efficient and more suitable for scenarios where frequent enabling/disabling are needed.

After local video publishing is paused, other members in the same room will receive the ` onUserVideoAvailable(userId, NO) ` callback notification.

After local video publishing is resumed, other members in the same room will receive the ` onUserVideoAvailable(userId, YES) ` callback notification.

| Param | DESC |
| --- | --- |
| mute | YES: pause; NO: resume |
| streamType | Specify for which video stream to pause (or resume). Only [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) and [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) are supported |

## setVideoMuteImage:fps:

**setVideoMuteImage:fps:**

| - (void)setVideoMuteImage: | (nullable TXImage *)image |
| --- | --- |
| fps: | (NSInteger)fps |

**Set placeholder image during local video pause.**

When you call ` muteLocalVideo(YES) ` to pause the local video image, you can set a placeholder image by calling this API. Then, other users in the room will see this image instead of a black screen.

| Param | DESC |
| --- | --- |
| fps | Frame rate of the placeholder image. Minimum value: 5. Maximum value: 10. Default value: 5 |
| image | Placeholder image. A null value means that no more video stream data will be sent after [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50754#dd2e6e6669e44947ac869fa038462588). The default value is null. |

## startRemoteView:streamType:view:

**startRemoteView:streamType:view:**

| - (void)startRemoteView: | (NSString *)userId |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| view: | (nullable TXView *)view |

**Subscribe to remote user's video stream and bind video rendering control.**

Calling this API allows the SDK to pull the video stream of the specified ` userId ` and render it to the rendering control specified by the ` view ` parameter. You can set the display mode of the video image through [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50754#8a2b406ea2817c2feb2336d92eb7af20).

- If you already know the ` userId ` of a user who has a video stream in the room, you can directly call ` startRemoteView ` to subscribe to the user's video image.
- If you don't know which users in the room are publishing video streams, you can wait for the notification from [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/50755#36daf607f51a906ea0b48b33fc628161) after [enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689).

Calling this API only starts pulling the video stream, and the image needs to be loaded and buffered at this time. After the buffering is completed, you will receive a notification from [onFirstVideoFrame](https://www.tencentcloud.com/document/product/647/50755#0494183885d1acf579b02e489b9e6607).

| Param | DESC |
| --- | --- |
| streamType | Video stream type of the ` userId ` specified for watching: HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) (the remote user should enable dual-channel encoding through [enableEncSmallVideoStream](https://www.tencentcloud.com/document/product/647/50754#73531b17f6a66de14fc7dd1acd429f16) for this parameter to take effect) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |
| view | Rendering control that carries the video image |

> **Note**The following requires your attention:1. The SDK supports watching the big image and substream image or small image and substream image of a ` userId ` at the same time, but does not support watching the big image and small image at the same time.2. Only when the specified ` userId ` enables dual-channel encoding through [enableEncSmallVideoStream](https://www.tencentcloud.com/document/product/647/50754#73531b17f6a66de14fc7dd1acd429f16) can the user's small image be viewed.3. If the small image of the specified ` userId ` does not exist, the SDK will switch to the big image of the user by default.

## updateRemoteView:streamType:forUser:

**updateRemoteView:streamType:forUser:**

| - (void)updateRemoteView: | (nullable TXView *)view |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| forUser: | (NSString *)userId |

**Update remote user's video rendering control.**

This API can be used to update the rendering control of the remote video image. It is often used in interactive scenarios where the display area needs to be switched.

| Param | DESC |
| --- | --- |
| streamType | Type of the stream for which to set the preview window (only [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) and [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) are supported) |
| userId | ID of the specified remote user |
| view | Control that carries the video image |

## stopRemoteView:streamType:

**stopRemoteView:streamType:**

| - (void)stopRemoteView: | (NSString *)userId |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |

**Stop subscribing to remote user's video stream and release rendering control.**

Calling this API will cause the SDK to stop receiving the user's video stream and release the decoding and rendering resources for the stream.

| Param | DESC |
| --- | --- |
| streamType | Video stream type of the ` userId ` specified for watching: HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |

## stopAllRemoteView

**stopAllRemoteView**

**Stop subscribing to all remote users' video streams and release all rendering resources.**

Calling this API will cause the SDK to stop receiving all remote video streams and release all decoding and rendering resources.

> **Note**If a substream image (screen sharing) is being displayed, it will also be stopped.

## muteRemoteVideoStream:streamType:mute:

**muteRemoteVideoStream:streamType:mute:**

| - (void)muteRemoteVideoStream: | (NSString*)userId |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| mute: | (BOOL)mute |

**Pause/Resume subscribing to remote user's video stream.**

This API only pauses/resumes receiving the specified user's video stream but does not release displaying resources; therefore, the video image will freeze at the last frame before it is called.

| Param | DESC |
| --- | --- |
| mute | Whether to pause receiving |
| streamType | Specify for which video stream to pause (or resume): HD big image: [TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) Smooth small image: [TRTCVideoStreamTypeSmall](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) Substream image (usually used for screen sharing): [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868) |
| userId | ID of the specified remote user |

> **Note**This API can be called before room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689)), and the pause status will be reset after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50754#812a3ac0ad44e274ef4c9213ab0d4a54)). After calling this API to pause receiving the video stream from a specific user, simply calling the [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) API will not be able to play the video from that user. You need to call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50754#b2d1898fc13a9583f8317cf3d9d40837)(NO) or [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/50754#8414e579076b74d5ecf4497107414697)(NO) to resume it.

## muteAllRemoteVideoStreams:

**muteAllRemoteVideoStreams:**

| - (void)muteAllRemoteVideoStreams: | (BOOL)mute |
| --- | --- |

**Pause/Resume subscribing to all remote users' video streams.**

This API only pauses/resumes receiving all users' video streams but does not release displaying resources; therefore, the video image will freeze at the last frame before it is called.

| Param | DESC |
| --- | --- |
| mute | Whether to pause receiving |

> **Note**This API can be called before room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689)), and the pause status will be reset after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50754#812a3ac0ad44e274ef4c9213ab0d4a54)).After calling this interface to pause receiving video streams from all users, simply calling the [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) interface will not be able to play the video from a specific user. You need to call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50754#b2d1898fc13a9583f8317cf3d9d40837)(NO) or [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/50754#8414e579076b74d5ecf4497107414697)(NO) to resume it.

## setVideoEncoderParam:

**setVideoEncoderParam:**

| - (void)setVideoEncoderParam: | ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e)*)param |
| --- | --- |

**Set the encoding parameters of video encoder.**

This setting can determine the quality of image viewed by remote users, which is also the image quality of on-cloud recording files.

| Param | DESC |
| --- | --- |
| param | It is used to set relevant parameters for the video encoder. For more information, please see [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e). |

> **Note**Begin from v11.5 version, the encoding output resolution will be aligned according to width 8 and height 2 bytes, and will be adjusted downward, eg: input resolution 540x960, actual encoding output resolution 536x960.

## setNetworkQosParam:

**setNetworkQosParam:**

| - (void)setNetworkQosParam: | ([TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/50760#15fa30eb2d0220259cea127fdb0f886f)*)param |
| --- | --- |

**Set network quality control parameters.**

This setting determines the quality control policy in a poor network environment, such as "image quality preferred" or "smoothness preferred".

| Param | DESC |
| --- | --- |
| param | It is used to set relevant parameters for network quality control. For details, please refer to [TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/50760#15fa30eb2d0220259cea127fdb0f886f). |

## setLocalRenderParams:

**setLocalRenderParams:**

| - (void)setLocalRenderParams: | ([TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50760#660db44737d95899da095d02d163c478) *)params |
| --- | --- |

**Set the rendering parameters of local video image.**

The parameters that can be set include video image rotation angle, fill mode, and mirror mode.

| Param | DESC |
| --- | --- |
| params | Video image rendering parameters. For more information, please see [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50760#660db44737d95899da095d02d163c478). |

## setRemoteRenderParams:streamType:params:

**setRemoteRenderParams:streamType:params:**

| - (void)setRemoteRenderParams: | (NSString *)userId |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| params: | ([TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50760#660db44737d95899da095d02d163c478) *)params |

**Set the rendering mode of remote video image.**

The parameters that can be set include video image rotation angle, fill mode, and mirror mode.

| Param | DESC |
| --- | --- |
| params | Video image rendering parameters. For more information, please see [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50760#660db44737d95899da095d02d163c478). |
| streamType | It can be set to the primary stream image (TRTCVideoStreamTypeBig) or substream image (TRTCVideoStreamTypeSub). |
| userId | ID of the specified remote user |

## enableEncSmallVideoStream:withQuality:

**enableEncSmallVideoStream:withQuality:**

| - (int)enableEncSmallVideoStream: | (BOOL)enable |
| --- | --- |
| withQuality: | ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e)*)smallVideoEncParam |

**Enable dual-channel encoding mode with big and small images.**

In this mode, the current user's encoder will output two channels of video streams, i.e., **HD big image** and **Smooth small image**, at the same time (only one channel of audio stream will be output though).

In this way, other users in the room can choose to subscribe to the **HD big image** or **Smooth small image** according to their own network conditions or screen size.

| Param | DESC |
| --- | --- |
| enable | Whether to enable small image encoding. Default value: NO |
| smallVideoEncParam | Video parameters of small image stream |

> **Note**Dual-channel encoding will consume more CPU resources and network bandwidth; therefore, this feature can be enabled on macOS, Windows, or high-spec tablets, but is not recommended for phones.

**Return Desc:**

0: success; -1: the current big image has been set to a lower quality, and it is not necessary to enable dual-channel encoding

## setRemoteVideoStreamType:type:

**setRemoteVideoStreamType:type:**

| - (void)setRemoteVideoStreamType: | (NSString*)userId |
| --- | --- |
| type: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |

**Switch the big/small image of specified remote user.**

After an anchor in a room enables dual-channel encoding, the video image that other users in the room subscribe to through [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) will be **HD big image** by default.

You can use this API to select whether the image subscribed to is the big image or small image. The API can take effect before or after [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3) is called.

| Param | DESC |
| --- | --- |
| streamType | Video stream type, i.e., big image or small image. Default value: big image |
| userId | ID of the specified remote user |

> **Note**To implement this feature, the target user must have enabled the dual-channel encoding mode through [enableEncSmallVideoStream](https://www.tencentcloud.com/document/product/647/50754#73531b17f6a66de14fc7dd1acd429f16); otherwise, this API will not work.

## snapshotVideo:type:sourceType:

**snapshotVideo:type:sourceType:**

| - (void)snapshotVideo: | (nullable NSString *)userId |
| --- | --- |
| type: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| sourceType: | ([TRTCSnapshotSourceType](https://www.tencentcloud.com/document/product/647/50760#1406df3b7414908d324734a5df7b746c))sourceType |

**Screencapture video.**

You can use this API to screencapture the local video image or the primary stream image and substream (screen sharing) image of a remote user.

| Param | DESC |
| --- | --- |
| sourceType | Video image source, which can be the video stream image ([TRTCSnapshotSourceTypeStream](https://www.tencentcloud.com/document/product/647/50760#1406df3b7414908d324734a5df7b746c), generally in higher definition) ãthe video rendering image ([TRTCSnapshotSourceTypeView](https://www.tencentcloud.com/document/product/647/50760#1406df3b7414908d324734a5df7b746c)) or the capture picture ([TRTCSnapshotSourceTypeCapture](https://www.tencentcloud.com/document/product/647/50760#1406df3b7414908d324734a5df7b746c)).The captured picture screenshot will be clearer. |
| streamType | Video stream type, which can be the primary stream image ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868), generally for camera) or substream image ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868), generally for screen sharing) |
| userId | User ID. A null value indicates to screencapture the local video. |

> **Note**On Windows, only video image from the [TRTCSnapshotSourceTypeStream](https://www.tencentcloud.com/document/product/647/50760#1406df3b7414908d324734a5df7b746c) source can be screencaptured currently.

## setPerspectiveCorrectionWithUser:srcPoints:dstPoints:

**setPerspectiveCorrectionWithUser:srcPoints:dstPoints:**

| - (void)setPerspectiveCorrectionWithUser: | (nullable NSString *)userId |
| --- | --- |
| srcPoints: | (nullable NSArray *)srcPoints |
| dstPoints: | (nullable NSArray *)dstPoints |

**Sets perspective correction coordinate points.**

This function allows you to specify coordinate areas for perspective correction.

| Param | DESC |
| --- | --- |
| dstPoints | The coordinates of the four vertices of the target corrected area should be passed in the order of top-left, bottom-left, top-right, bottom-right. All coordinates need to be normalized to the [0,1] range based on the render view width and height, or null to stop perspective correction of the corresponding stream. |
| srcPoints | The coordinates of the four vertices of the original stream image area should be passed in the order of top-left, bottom-left, top-right, bottom-right. All coordinates need to be normalized to the [0,1] range based on the render view width and height, or null to stop perspective correction of the corresponding stream. |
| userId | userId which corresponding to the target stream. If null value is specified, it indicates that the function is applied to the local stream. |

## setGravitySensorAdaptiveMode:

**setGravitySensorAdaptiveMode:**

| - (void)setGravitySensorAdaptiveMode: | ([TRTCGravitySensorAdaptiveMode](https://www.tencentcloud.com/document/product/647/50760#601299c4e6bd66487314e0edd164bf03)) mode |
| --- | --- |

**Set the adaptation mode of gravity sensing (version 11.7 and above).**

After turning on gravity sensing, if the device on the collection end rotates, the images on the collection end and the audience will be rendered accordingly to ensure that the image in the field of view is always facing up.

It only takes effect in the camera capture scene inside the SDK, and only takes effect on the mobile terminal.

1. This interface only works for the collection end. If you only watch the picture in the room, opening this interface is invalid.

2. When the capture device is rotated 90 degrees or 270 degrees, the picture seen by the capture device or the audience may be cropped to maintain proportional coordination.

| Param | DESC |
| --- | --- |
| mode | Gravity sensing mode, see [TRTCGravitySensorAdaptiveMode_Disable](https://www.tencentcloud.com/document/product/647/50760#601299c4e6bd66487314e0edd164bf03)ã[TRTCGravitySensorAdaptiveMode_FillByCenterCrop](https://www.tencentcloud.com/document/product/647/50760#601299c4e6bd66487314e0edd164bf03) and [TRTCGravitySensorAdaptiveMode_FitWithBlackBorder](https://www.tencentcloud.com/document/product/647/50760#601299c4e6bd66487314e0edd164bf03) for details, default value: [TRTCGravitySensorAdaptiveMode_Disable](https://www.tencentcloud.com/document/product/647/50760#601299c4e6bd66487314e0edd164bf03). |

## startLocalAudio:

**startLocalAudio:**

| - (void)startLocalAudio: | ([TRTCAudioQuality](https://www.tencentcloud.com/document/product/647/50760#f8aeb89d8ef78db15d893e55f68cdb42))quality |
| --- | --- |

**Enable local audio capturing and publishing.**

The SDK does not enable the mic by default. When a user wants to publish the local audio, the user needs to call this API to enable mic capturing and encode and publish the audio to the current room.

After local audio capturing and publishing is enabled, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50755#e9535d2e80eb01b4d671dcbd7dfa8c8f)(userId, YES) notification.

| Param | DESC |
| --- | --- |
| quality | Sound quality [TRTCAudioQualitySpeech](https://www.tencentcloud.com/document/product/647/50760#f8aeb89d8ef78db15d893e55f68cdb42) - Smooth: mono channel; audio bitrate: 18 Kbps. This is suitable for audio call scenarios, such as online meeting and audio call. [TRTCAudioQualityDefault](https://www.tencentcloud.com/document/product/647/50760#f8aeb89d8ef78db15d893e55f68cdb42) - Default: mono channel; audio bitrate: 50 Kbps. This is the default sound quality of the SDK and recommended if there are no special requirements. [TRTCAudioQualityMusic](https://www.tencentcloud.com/document/product/647/50760#f8aeb89d8ef78db15d893e55f68cdb42) - HD: dual channel + full band; audio bitrate: 128 Kbps. This is suitable for scenarios where Hi-Fi music transfer is required, such as online karaoke and music live streaming. |

> **Note**This API will check the mic permission. If the current application does not have permission to use the mic, the SDK will automatically ask the user to grant the mic permission.

## stopLocalAudio

**stopLocalAudio**

**Stop local audio capturing and publishing.**

After local audio capturing and publishing is stopped, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50755#e9535d2e80eb01b4d671dcbd7dfa8c8f)(userId, NO) notification.

## muteLocalAudio:

**muteLocalAudio:**

| - (void)muteLocalAudio: | (BOOL)mute |
| --- | --- |

**Pause/Resume publishing local audio stream.**

After local audio publishing is paused, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50755#e9535d2e80eb01b4d671dcbd7dfa8c8f)(userId, NO) notification.

After local audio publishing is resumed, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50755#e9535d2e80eb01b4d671dcbd7dfa8c8f)(userId, YES) notification.

Different from [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50754#261e73f11221bdafb889bccd45b6d5d4), ` muteLocalAudio(YES) ` does not release the mic permission; instead, it continues to send mute packets with extremely low bitrate.

This is very suitable for scenarios that require on-cloud recording, as video file formats such as MP4 have a high requirement for audio continuity, while an MP4 recording file cannot be played back smoothly if [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50754#261e73f11221bdafb889bccd45b6d5d4) is used.

Therefore, ` muteLocalAudio ` instead of [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50754#261e73f11221bdafb889bccd45b6d5d4) is recommended in scenarios where the requirement for recording file quality is high.

| Param | DESC |
| --- | --- |
| mute | YES: mute; NO: unmute |

## muteRemoteAudio:mute:

**muteRemoteAudio:mute:**

| - (void)muteRemoteAudio: | (NSString *)userId |
| --- | --- |
| mute: | (BOOL)mute |

**Pause/Resume playing back remote audio stream.**

When you mute the remote audio of a specified user, the SDK will stop playing back the user's audio and pulling the user's audio data.

| Param | DESC |
| --- | --- |
| mute | YES: mute; NO: unmute |
| userId | ID of the specified remote user |

> **Note**This API works when called either before or after room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689)), and the mute status will be reset to ` NO ` after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50754#812a3ac0ad44e274ef4c9213ab0d4a54)).

## muteAllRemoteAudio:

**muteAllRemoteAudio:**

| - (void)muteAllRemoteAudio: | (BOOL)mute |
| --- | --- |

**Pause/Resume playing back all remote users' audio streams.**

When you mute the audio of all remote users, the SDK will stop playing back all their audio streams and pulling all their audio data.

| Param | DESC |
| --- | --- |
| mute | YES: mute; NO: unmute |

> **Note**This API works when called either before or after room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50754#011dce4d6afaa3bcd684bebb77829689)), and the mute status will be reset to ` NO ` after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50754#812a3ac0ad44e274ef4c9213ab0d4a54)).

## setAudioRoute:

**setAudioRoute:**

| - (void)setAudioRoute: | ([TRTCAudioRoute](https://www.tencentcloud.com/document/product/647/50760#aaca0d57f6f9d9c6a6425485464b0877))route |
| --- | --- |

**Set audio route.**

Setting "audio route" is to determine whether the sound is played back from the speaker or receiver of a mobile device; therefore, this API is only applicable to mobile devices such as phones.

Generally, a phone has two speakers: one is the receiver at the top, and the other is the stereo speaker at the bottom.

If audio route is set to the receiver, the volume is relatively low, and the sound can be heard clearly only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.

If audio route is set to the speaker, the volume is relatively high, so there is no need to put the phone near the ear. Therefore, this mode can implement the "hands-free" feature.

| Param | DESC |
| --- | --- |
| route | Audio route, i.e., whether the audio is output by speaker or receiver. Default value: [TRTCAudioModeSpeakerphone](https://www.tencentcloud.com/document/product/647/50760#aaca0d57f6f9d9c6a6425485464b0877) |

## setRemoteAudioVolume:volume:

**setRemoteAudioVolume:volume:**

| - (void)setRemoteAudioVolume: | (NSString *)userId |
| --- | --- |
| volume: | (int)volume |

**Set the audio playback volume of remote user.**

You can mute the audio of a remote user through ` setRemoteAudioVolume(userId, 0) `.

| Param | DESC |
| --- | --- |
| userId | ID of the specified remote user |
| volume | Volume. 100 is the original volume. Value range: [0,150]. Default value: 100 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setAudioCaptureVolume:

**setAudioCaptureVolume:**

| - (void)setAudioCaptureVolume: | (NSInteger)volume |
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

## setAudioPlayoutVolume:

**setAudioPlayoutVolume:**

| - (void)setAudioPlayoutVolume: | (NSInteger)volume |
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

## enableAudioVolumeEvaluation:withParams:

**enableAudioVolumeEvaluation:withParams:**

| - (void)enableAudioVolumeEvaluation: | (BOOL)enable |
| --- | --- |
| withParams: | ([TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/50760#a009476d3d69bd49ff693344302409bf) *)params |

**Enable volume reminder.**

After this feature is enabled, the SDK will return the audio volume assessment information of local user who sends stream and remote users in the [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/50755#c28a692ba631a72b910e17b042d6f293) callback of [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

| Param | DESC |
| --- | --- |
| enable | Whether to enable the volume prompt. Itâs disabled by default. |
| params | Volume evaluation and other related parameters, please see [TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/50760#a009476d3d69bd49ff693344302409bf) |

> **Note**To enable this feature, call this API before calling [startLocalAudio](https://www.tencentcloud.com/document/product/647/50754#df3c633d8a6277d5271813f9fac58cb9).

## startAudioRecording:

**startAudioRecording:**

| - (int)startAudioRecording: | ([TRTCAudioRecordingParams](https://www.tencentcloud.com/document/product/647/50760#856a9c899752cb0b60944b7acc5fb868)*) param |
| --- | --- |

**Start audio recording.**

After you call this API, the SDK will selectively record local and remote audio streams (such as local audio, remote audio, background music, and sound effects) into a local file.

This API works when called either before or after room entry. If a recording task has not been stopped through [stopAudioRecording](https://www.tencentcloud.com/document/product/647/50754#0d75b463c4ab899ef1954ca8c03e38d6) before room exit, it will be automatically stopped after room exit.

The startup and completion status of the recording will be notified through local recording-related callbacks. See TRTCCloud related callbacks for reference.

| Param | DESC |
| --- | --- |
| param | Recording parameter. For more information, please see [TRTCAudioRecordingParams](https://www.tencentcloud.com/document/product/647/50760#856a9c899752cb0b60944b7acc5fb868) |

> **Note**Since version 11.5, the results of audio recording have been changed to be notified through asynchronous callbacks instead of return values. Please refer to the relevant callbacks of [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04) .

**Return Desc:**

0: success; -1: audio recording has been started; -2: failed to create file or directory; -3: the audio format of the specified file extension is not supported.

## stopAudioRecording

**stopAudioRecording**

**Stop audio recording.**

If a recording task has not been stopped through this API before room exit, it will be automatically stopped after room exit.

## startLocalRecording:

**startLocalRecording:**

| - (void)startLocalRecording: | ([TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/50760#4d8f80d5bf4ece224c7125eec1490b3d) *)params |
| --- | --- |

**Start local media recording.**

This API records the audio/video content during live streaming into a local file,and no recording fees for local recording.

| Param | DESC |
| --- | --- |
| params | Recording parameter. For more information, please see [TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/50760#4d8f80d5bf4ece224c7125eec1490b3d) |

## stopLocalRecording

**stopLocalRecording**

**Stop local media recording.**

If a recording task has not been stopped through this API before room exit, it will be automatically stopped after room exit.

## setRemoteAudioParallelParams:

**setRemoteAudioParallelParams:**

| - (void)setRemoteAudioParallelParams: | (TRTCAudioParallelParams*)params |
| --- | --- |

**Set the parallel strategy of remote audio streams.**

For room with many speakers.

| Param | DESC |
| --- | --- |
| params | Audio parallel parameter. For more information, please see TRTCAudioParallelParams |

## enable3DSpatialAudioEffect:

**enable3DSpatialAudioEffect:**

| - (void)enable3DSpatialAudioEffect: | (BOOL)enabled |
| --- | --- |

**Enable 3D spatial effect.**

Enable 3D spatial effect. Note that [TRTCAudioQualitySpeech](https://www.tencentcloud.com/document/product/647/50760#f8aeb89d8ef78db15d893e55f68cdb42) smooth or [TRTCAudioQualityDefault](https://www.tencentcloud.com/document/product/647/50760#f8aeb89d8ef78db15d893e55f68cdb42) default audio quality should be used.

| Param | DESC |
| --- | --- |
| enabled | Whether to enable 3D spatial effect. Itâs disabled by default. |

## updateSelf3DSpatialPosition

**updateSelf3DSpatialPosition**

**Update self position and orientation for 3D spatial effect.**

Update self position and orientation in the world coordinate system. The SDK will calculate the relative position between self and the remote users according to the parameters of this method, and then render the spatial sound effect.

| Param | DESC |
| --- | --- |
| axisForward | The unit vector of the forward axis of user coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| axisRight | The unit vector of the right axis of user coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| axisUp | The unit vector of the up axis of user coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| position | The coordinate of self in the world coordinate system. The three values represent the forward, right and up coordinate values in turn. |

> **Note**1. The length of array should be 3.2. Please limit the calling frequency appropriately. It's recommended that the interval between two operations be at least 100ms.

## updateRemote3DSpatialPosition:

**updateRemote3DSpatialPosition:**

| - (void)updateRemote3DSpatialPosition: | (NSString *)userId |
| --- | --- |

**Update the specified remote user's position for 3D spatial effect.**

Update the specified remote user's position in the world coordinate system. The SDK will calculate the relative position between self and the remote users according to the parameters of this method, and then render the spatial sound effect.

| Param | DESC |
| --- | --- |
| position | The coordinate of self in the world coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| userId | ID of the specified remote user. |

> **Note**1. The length of array should be 3.2. Please limit the calling frequency appropriately. It's recommended that the interval between two operations of the same remote user be at least 100ms.

## set3DSpatialReceivingRange:range:

**set3DSpatialReceivingRange:range:**

| - (void)set3DSpatialReceivingRange: | (NSString *)userId |
| --- | --- |
| range: | (NSInteger)range |

**Set the maximum 3D spatial attenuation range for userId's audio stream.**

After set the range, the specified user's audio stream will attenuate to zero within the range.

| Param | DESC |
| --- | --- |
| range | Maximum attenuation range of the audio stream. |
| userId | ID of the specified user. |

## getDeviceManager

**getDeviceManager**

**Get device management class (TXDeviceManager).**

Through device management, you can set the functions of audio and video related hardware devices such as cameras, microphones, and speakers.

**Return Desc:**

device management class [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1).

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

beauty filter management class [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252).

## setWatermark:streamType:rect:

**setWatermark:streamType:rect:**

| - (void)setWatermark: | (nullable TXImage*)image |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| rect: | (CGRect)rect |

**Add watermark.**

The watermark position is determined by the ` rect ` parameter, which is a quadruple in the format of (x, y, width, height).

- x: X coordinate of watermark, which is a floating-point number between 0 and 1.
- y: Y coordinate of watermark, which is a floating-point number between 0 and 1.
- width: width of watermark, which is a floating-point number between 0 and 1.
- height: it does not need to be set. The SDK will automatically calculate it according to the watermark image's aspect ratio.

Sample parameter:

If the encoding resolution of the current video is 540x960, and the ` rect ` parameter is set to (0.1, 0.1, 0.2, 0.0),

then the coordinates of the top-left point of the watermark will be (540 * 0.1, 960 * 0.1), i.e., (54, 96), the watermark width will be ` 540 * 0.2 = 108 px `, and the watermark height will be calculated automatically by the SDK based on the watermark image's aspect ratio.

| Param | DESC |
| --- | --- |
| image | Watermark image, which must be a PNG image with transparent background |
| rect | Unified coordinates of the watermark relative to the encoded resolution. Value range of ` x `, ` y `, ` width `, and ` height `: 0â1. |
| streamType | Specify for which image to set the watermark. For more information, please see [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868). |

> **Note**If you want to set watermarks for both the primary image (generally for the camera) and the substream image (generally for screen sharing), you need to call this API twice with ` streamType ` set to different values.

## getAudioEffectManager

**getAudioEffectManager**

**Get sound effect management class (TXAudioEffectManager).**

` TXAudioEffectManager ` is a sound effect management API, through which you can implement the following features:

- Background music: both online music and local music can be played back with various features such as speed adjustment, pitch adjustment, original voice, accompaniment, and loop.
- In-ear monitoring: the sound captured by the mic is played back in the headphones in real time, which is generally used for music live streaming.
- Reverb effect: karaoke room, small room, big hall, deep, resonant, and other effects.
- Voice changing effect: young girl, middle-aged man, heavy metal, and other effects.
- Short sound effect: short sound effect files such as applause and laughter are supported (for files less than 10 seconds in length, please set the ` isShortFile ` parameter to ` YES `).

**Return Desc:**

sound effect management class [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7).

## startSystemAudioLoopback

**startSystemAudioLoopback**

**Enable system audio capturing(iOS not supported).**

This API captures audio data from the sound card of a macOS computer and mixes it into the current audio data stream of the SDK, so that other users in the room can also hear the sound played back on the current macOS system.

In use cases such as video teaching or music live streaming, the teacher can use this feature to let the SDK capture the sound in the video played back by the teacher, so that students in the same room can also hear the sound in the video.

> **Note**1. This feature needs to install a virtual audio device plugin on the user's macOS system. After the installation is completed, the SDK will capture sound from the installed virtual device.2. The SDK will automatically download the appropriate plugin from the internet for installation, but the download may be slow. If you want to speed up this process, you can package the virtual audio plugin file into the ` Resources ` directory of your app bundle.

## stopSystemAudioLoopback

**stopSystemAudioLoopback**

**Stop system audio capturing(iOS not supported).**

## setSystemAudioLoopbackVolume:

**setSystemAudioLoopbackVolume:**

| - (void)setSystemAudioLoopbackVolume: | (uint32_t)volume |
| --- | --- |

**Set the volume of system audio capturing.**

| Param | DESC |
| --- | --- |
| volume | Set volume. Value range: [0, 150]. Default value: 100 |

## startScreenCaptureInApp:encParam:

**startScreenCaptureInApp:encParam:**

| - (void)startScreenCaptureInApp: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| --- | --- |
| encParam: | ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e) *)encParams |

**Start in-app screen sharing (for iOS 13.0 and above only).**

This API captures the real-time screen content of the current application and shares it with other users in the same room. It is applicable to iOS 13.0 and above.

If you want to capture the screen content of the entire iOS system (instead of the current application), we recommend you use [startScreenCaptureByReplaykit](https://www.tencentcloud.com/document/product/647/50754#a40e37e782a049150b3314810516bf44).

Video encoding parameters recommended for screen sharing on iPhone ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e)):

- Resolution (videoResolution): 1280x720
- Frame rate (videoFps): 10 fps
- Bitrate (videoBitrate): 1600 Kbps
- Resolution adaption (enableAdjustRes): NO

| Param | DESC |
| --- | --- |
| encParams | Video encoding parameters for screen sharing. We recommend you use the above configuration.If you set ` encParams ` to ` nil `, the SDK will use the video encoding parameters you set before calling the [startScreenCapture](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194) API. |
| streamType | Channel used for screen sharing, which can be the primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868)) or substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868)). |

## startScreenCaptureByReplaykit:encParam:appGroup:

**startScreenCaptureByReplaykit:encParam:appGroup:**

| - (void)startScreenCaptureByReplaykit: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| --- | --- |
| encParam: | ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e) *)encParams |
| appGroup: | (NSString *)appGroup |

**Start system-level screen sharing (for iOS 11.0 and above only).**

This API supports capturing the screen of the entire iOS system, which can implement system-wide screen sharing similar to VooV Meeting.

However, the integration steps are slightly more complicated than those of [startScreenCaptureInApp](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194). You need to implement a ReplayKit extension module for your application.

For more information, please see [iOS](https://www.tencentcloud.com/document/product/647/37338)

Video encoding parameters recommended for screen sharing on iPhone ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e)):

- Resolution (videoResolution): 1280x720
- Frame rate (videoFps): 10 fps
- Bitrate (videoBitrate): 1600 Kbps
- Resolution adaption (enableAdjustRes): NO

| Param | DESC |
| --- | --- |
| appGroup | Specify the ` Application Group Identifier ` shared by your application and the screen sharing process. You can specify this parameter as ` nil `, but we recommend you set it as instructed in the documentation for higher reliability. |
| encParams | Video encoding parameters for screen sharing. We recommend you use the above configuration.If you set ` encParams ` to ` nil `, the SDK will use the video encoding parameters you set before calling the ` startScreenCapture ` API. |
| streamType | Channel used for screen sharing, which can be the primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868)) or substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868)). |

## startScreenCapture:streamType:encParam:

**startScreenCapture:streamType:encParam:**

| - (void)startScreenCapture: | (nullable NSView *)view |
| --- | --- |
| streamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| encParam: | (nullable [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e) *)encParam |

**Start screen sharing.**

This API can capture the content of the entire screen or a specified application and share it with other users in the same room.

| Param | DESC |
| --- | --- |
| encParam | Image encoding parameters used for screen sharing, which can be set to empty, indicating to let the SDK choose the optimal encoding parameters (such as resolution and bitrate). |
| streamType | Channel used for screen sharing, which can be the primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868)) or substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868)). |
| view | Parent control of the rendering control, which can be set to a null value, indicating not to display the preview of the shared screen. |

> **Note**1. A user can publish at most one primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868)) and one substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868)) at the same time.2. By default, screen sharing uses the substream image. If you want to use the primary stream for screen sharing, you need to stop camera capturing (through [stopLocalPreview](https://www.tencentcloud.com/document/product/647/50754#39a28f132a6e183cb05d4ffd15fec991)) in advance to avoid conflicts.3. Only one user can use the substream for screen sharing in the same room at any time; that is, only one user is allowed to enable the substream in the same room at any time.4. When there is already a user in the room using the substream for screen sharing, calling this API will return the ` onError(ERR_SERVER_CENTER_ANOTHER_USER_PUSH_SUB_VIDEO) ` callback from [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

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

## getScreenCaptureSourcesWithThumbnailSize:iconSize:

**getScreenCaptureSourcesWithThumbnailSize:iconSize:**

| - (NSArray<TRTCScreenCaptureSourceInfo*>*)getScreenCaptureSourcesWithThumbnailSize: | (CGSize)thumbnailSize |
| --- | --- |
| iconSize: | (CGSize)iconSize |

**Enumerate shareable screens and windows (for macOS only).**

When you integrate the screen sharing feature of a desktop system, you generally need to display a UI for selecting the sharing target, so that users can use the UI to choose whether to share the entire screen or a certain window.

Through this API, you can query the IDs, names, and thumbnails of sharable windows on the current system. We provide a default UI implementation in the demo for your reference.

| Param | DESC |
| --- | --- |
| iconSize | Specify the icon size of the window to be obtained. |
| thumbnailSize | Specify the thumbnail size of the window to be obtained. The thumbnail can be drawn on the window selection UI. |

> **Note**The returned list contains the screen and the application windows. The screen is the first element in the list. If the user has multiple displays, then each display is a sharing target.

**Return Desc:**

List of windows (including the screen)

## selectScreenCaptureTarget:rect:capturesCursor:highlight:

**selectScreenCaptureTarget:rect:capturesCursor:highlight:**

| - (void)selectScreenCaptureTarget: | (TRTCScreenCaptureSourceInfo *)screenSource |
| --- | --- |
| rect: | (CGRect)rect |
| capturesCursor: | (BOOL)capturesCursor |
| highlight: | (BOOL)highlight |

**Select the screen or window to share (for macOS only).**

After you get the sharable screen and windows through [getScreenCaptureSources](https://www.tencentcloud.com/document/product/647/50754#d99a40c2e0806381169a238674f1e91f), you can call this API to select the target screen or window you want to share.

During the screen sharing process, you can also call this API at any time to switch the sharing target.

| Param | DESC |
| --- | --- |
| capturesCursor | Whether to capture mouse cursor |
| highlight | Whether to highlight the window being shared |
| rect | Specify the area to be captured (set this parameter to ` CGRectZero `: when the sharing target is a window, the entire window will be shared, and when the sharing target is the desktop, the entire desktop will be shared) |
| screenSource | Specify sharing source |

## setSubStreamEncoderParam:

**setSubStreamEncoderParam:**

| - (void)setSubStreamEncoderParam: | ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e) *)param |
| --- | --- |

**Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems).**

This API can set the image quality of screen sharing (i.e., the substream) viewed by remote users, which is also the image quality of screen sharing in on-cloud recording files.

Please note the differences between the following two APIs:

- [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50754#2add5add2f68df49f042ff400571ae48) is used to set the video encoding parameters of the primary stream image ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868), generally for camera).
- [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50754#8b9ac12176384adfb56850af375ece28) is used to set the video encoding parameters of the substream image ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868), generally for screen sharing).

| Param | DESC |
| --- | --- |
| param | Substream encoding parameters. For more information, please see [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e). |

## setSubStreamMixVolume:

**setSubStreamMixVolume:**

| - (void)setSubStreamMixVolume: | (NSInteger)volume |
| --- | --- |

**Set the audio mixing volume of screen sharing (for desktop systems only).**

The greater the value, the larger the ratio of the screen sharing volume to the mic volume. We recommend you not set a high value for this parameter as a high volume will cover the mic sound.

| Param | DESC |
| --- | --- |
| volume | Set audio mixing volume. Value range: [0, 150] |

## addExcludedShareWindow:

**addExcludedShareWindow:**

| - (void)addExcludedShareWindow: | (NSInteger)windowID |
| --- | --- |

**Add specified windows to the exclusion list of screen sharing (for desktop systems only).**

The excluded windows will not be shared. This feature is generally used to add a certain application's window to the exclusion list to avoid privacy issues.

You can set the filtered windows before starting screen sharing or dynamically add the filtered windows during screen sharing.

| Param | DESC |
| --- | --- |
| window | Window not to be shared |

> **Note**1. This API takes effect only if the ` type ` in TRTCScreenCaptureSourceInfo is specified as [TRTCScreenCaptureSourceTypeScreen](https://www.tencentcloud.com/document/product/647/50760#d17d41b4687c203691c6b51aa53418ac); that is, the feature of excluding specified windows works only when the entire screen is shared.2. The windows added to the exclusion list through this API will be automatically cleared by the SDK after room exit.3. On macOS, please pass in the window ID (CGWindowID), which can be obtained through the ` sourceId ` member in TRTCScreenCaptureSourceInfo.

## removeExcludedShareWindow:

**removeExcludedShareWindow:**

| - (void)removeExcludedShareWindow: | (NSInteger)windowID |
| --- | --- |

**Remove specified windows from the exclusion list of screen sharing (for desktop systems only).**

| Param | DESC |
| --- | --- |
| windowID |  |

## removeAllExcludedShareWindows

**removeAllExcludedShareWindows**

**Remove all windows from the exclusion list of screen sharing (for desktop systems only).**

## addIncludedShareWindow:

**addIncludedShareWindow:**

| - (void)addIncludedShareWindow: | (NSInteger)windowID |
| --- | --- |

**Add specified windows to the inclusion list of screen sharing (for desktop systems only).**

This API takes effect only if the ` type ` in TRTCScreenCaptureSourceInfo is specified as [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/50760#d17d41b4687c203691c6b51aa53418ac); that is, the feature of additionally including specified windows works only when a window is shared.

You can call it before or after [startScreenCapture](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194).

| Param | DESC |
| --- | --- |
| windowID | Window to be shared (which is a window handle ` HWND ` on Windows) |

> **Note**The windows added to the inclusion list by this method will be automatically cleared by the SDK after room exit.

## removeIncludedShareWindow:

**removeIncludedShareWindow:**

| - (void)removeIncludedShareWindow: | (NSInteger)windowID |
| --- | --- |

**Remove specified windows from the inclusion list of screen sharing (for desktop systems only).**

This API takes effect only if the ` type ` in TRTCScreenCaptureSourceInfo is specified as [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/50760#d17d41b4687c203691c6b51aa53418ac).

That is, the feature of additionally including specified windows works only when a window is shared.

| Param | DESC |
| --- | --- |
| windowID | Window to be shared (window ID on macOS or HWND on Windows) |

## removeAllIncludedShareWindows

**removeAllIncludedShareWindows**

**Remove all windows from the inclusion list of screen sharing (for desktop systems only).**

This API takes effect only if the ` type ` in TRTCScreenCaptureSourceInfo is specified as [TRTCScreenCaptureSourceTypeWindow](https://www.tencentcloud.com/document/product/647/50760#d17d41b4687c203691c6b51aa53418ac).

That is, the feature of additionally including specified windows works only when a window is shared.

## enableCustomVideoCapture:enable:

**enableCustomVideoCapture:enable:**

| - (void)enableCustomVideoCapture: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| --- | --- |
| enable: | (BOOL)enable |

**Enable/Disable custom video capturing mode.**

After this mode is enabled, the SDK will not run the original video capturing process (i.e., stopping camera data capturing and beauty filter operations) and will retain only the video encoding and sending capabilities.

You need to use [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50754#2ec8cee427b69adc1b75be389c7eaef7) to continuously insert the captured video image into the SDK.

| Param | DESC |
| --- | --- |
| enable | Whether to enable. Default value: NO |
| streamType | Specify video stream type ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868): HD big image; [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868): substream image). |

## sendCustomVideoData:frame:

**sendCustomVideoData:frame:**

| - (void)sendCustomVideoData: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| --- | --- |
| frame: | ([TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50760#9233a1b1573333abc70e53b51bd89740) *)frame |

**Deliver captured video frames to SDK.**

You can use this API to deliver video frames you capture to the SDK, and the SDK will encode and transfer them through its own network module.

We recommend you enter the following information for the [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50760#9233a1b1573333abc70e53b51bd89740) parameter (other fields can be left empty):

- pixelFormat: [TRTCVideoPixelFormat_NV12](https://www.tencentcloud.com/document/product/647/50760#0fd3b6da1fb10e3d92eb55b00ba55dc3) is recommended.
- bufferType: [TRTCVideoBufferType_PixelBuffer](https://www.tencentcloud.com/document/product/647/50760#b2c90f7f7ec6ab033949b94f0fe34942) is recommended.
- pixelBuffer: common video data format on iOS/macOS.
- data: raw video data format, which is used if ` bufferType ` is ` NSData `.
- timestamp (ms): Set it to the timestamp when video frames are captured, which you can obtain by calling [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50754#d7dfdbb97b24b9304897c7acf776d803) after getting a video frame.
- width: video image length, which needs to be set if ` bufferType ` is ` NSData `.
- height: video image width, which needs to be set if ` bufferType ` is ` NSData `.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/35158).

| Param | DESC |
| --- | --- |
| frame | Video data. For ` bufferType `, [TRTCVideoBufferType_PixelBuffer](https://www.tencentcloud.com/document/product/647/50760#b2c90f7f7ec6ab033949b94f0fe34942) is recommended; for ` pixelFormat `, [TRTCVideoPixelFormat_NV12](https://www.tencentcloud.com/document/product/647/50760#0fd3b6da1fb10e3d92eb55b00ba55dc3) is recommended. Refer to [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50760#9233a1b1573333abc70e53b51bd89740) for more supported formats. |
| streamType | Specify video stream type ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868): HD big image; [TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868): substream image). |

> **Note**1. We recommend you call the [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50754#d7dfdbb97b24b9304897c7acf776d803) API to get the ` timestamp ` value of a video frame immediately after capturing it, so as to achieve the best audio/video sync effect.2. The video frame rate eventually encoded by the SDK is not determined by the frequency at which you call this API, but by the FPS you set in [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50754#2add5add2f68df49f042ff400571ae48).3. Please try to keep the calling interval of this API even; otherwise, problems will occur, such as unstable output frame rate of the encoder or out-of-sync audio/video.

## enableCustomAudioCapture:

**enableCustomAudioCapture:**

| - (void)enableCustomAudioCapture: | (BOOL)enable |
| --- | --- |

**Enable custom audio capturing mode.**

After this mode is enabled, the SDK will not run the original audio capturing process (i.e., stopping mic data capturing) and will retain only the audio encoding and sending capabilities.

You need to use [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50754#065fa14dfdbe241cd1d0286bf010388a) to continuously insert the captured audio data into the SDK.

| Param | DESC |
| --- | --- |
| enable | Whether to enable. Default value: NO |

> **Note**As acoustic echo cancellation (AEC) requires strict control over the audio capturing and playback time, after custom audio capturing is enabled, AEC may fail.

## sendCustomAudioData:

**sendCustomAudioData:**

| - (void)sendCustomAudioData: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)frame |
| --- | --- |

**Deliver captured audio data to SDK.**

We recommend you enter the following information for the [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) parameter (other fields can be left empty):

- audioFormat: audio data format, which can only be ` TRTCAudioFrameFormatPCM `.
- data: audio frame buffer. Audio frame data must be in PCM format, and it supports a frame length of 5â100 ms (20 ms is recommended). Length calculation method: **for example, if the sample rate is 48000, then the frame length for mono channel will be `48000 * 0.02s * 1 * 16 bit = 15360 bit = 1920 bytes`.**
- sampleRate: sample rate. Valid values: 16000, 24000, 32000, 44100, 48000.
- channel: number of channels (if stereo is used, data is interwoven). Valid values: 1: mono channel; 2: dual channel.
- timestamp (ms): Set it to the timestamp when audio frames are captured, which you can obtain by calling [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50754#d7dfdbb97b24b9304897c7acf776d803) after getting a audio frame.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/47635).

| Param | DESC |
| --- | --- |
| frame | Audio data |

> **Note**Please call this API accurately at intervals of the frame length; otherwise, sound lag may occur due to uneven data delivery intervals.

## enableMixExternalAudioFrame:playout:

**enableMixExternalAudioFrame:playout:**

| - (void)enableMixExternalAudioFrame: | (BOOL)enablePublish |
| --- | --- |
| playout: | (BOOL)enablePlayout |

**Enable/Disable custom audio track.**

After this feature is enabled, you can mix a custom audio track into the SDK through this API. With two boolean parameters, you can control whether to play back this track remotely or locally.

| Param | DESC |
| --- | --- |
| enablePlayout | Whether the mixed audio track should be played back locally. Default value: NO |
| enablePublish | Whether the mixed audio track should be played back remotely. Default value: NO |

> **Note**If you specify both ` enablePublish ` and ` enablePlayout ` as ` NO `, the custom audio track will be completely closed.

## mixExternalAudioFrame:

**mixExternalAudioFrame:**

| - (int)mixExternalAudioFrame: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)frame |
| --- | --- |

**Mix custom audio track into SDK.**

Before you use this API to mix custom PCM audio into the SDK, you need to first enable custom audio tracks through [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50754#714890054aef9e46d47aff9afa2b114d).

You are expected to feed audio data into the SDK at an even pace, but we understand that it can be challenging to call an API at absolutely regular intervals.

Given this, we have provided a buffer pool in the SDK, which can cache the audio data you pass in to reduce the fluctuations in intervals between API calls.

The value returned by this API indicates the size (ms) of the buffer pool. For example, if ` 50 ` is returned, it indicates that the buffer pool has 50 ms of audio data. As long as you call this API again within 50 ms, the SDK can make sure that continuous audio data is mixed.

If the value returned is ` 100 ` or greater, you can wait after an audio frame is played to call the API again. If the value returned is smaller than ` 100 `, then there isnât enough data in the buffer pool, and you should feed more audio data into the SDK until the data in the buffer pool is above the safety level.

Fill the fields in [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) as follows (other fields are not required).

- ` data `: audio frame buffer. Audio frames must be in PCM format. Each frame can be 5-100 ms (20 ms is recommended) in duration. Assume that the sample rate is 48000, and sound channels mono-channel. Then the **frame size would be 48000 x 0.02s x 1 x 16 bit = 15360 bit = 1920 bytes**.
- ` sampleRate `: sample rate. Valid values: 16000, 24000, 32000, 44100, 48000
- ` channel `: number of sound channels (if dual-channel is used, data is interleaved). Valid values: ` 1 ` (mono-channel); ` 2 ` (dual channel)
- ` timestamp `: timestamp (ms). Set it to the timestamp when audio frames are captured, which you can obtain by calling [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50754#d7dfdbb97b24b9304897c7acf776d803) after getting an audio frame.

| Param | DESC |
| --- | --- |
| frame | Audio data |

**Return Desc:**

If the value returned is ` 0 ` or greater, the value represents the current size of the buffer pool; if the value returned is smaller than ` 0 `, it means that an error occurred. ` -1 ` indicates that you didnât call [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50754#714890054aef9e46d47aff9afa2b114d) to enable custom audio tracks.

## setMixExternalAudioVolume:playoutVolume:

**setMixExternalAudioVolume:playoutVolume:**

| - (void)setMixExternalAudioVolume: | (NSInteger)publishVolume |
| --- | --- |
| playoutVolume: | (NSInteger)playoutVolume |

**Set the publish volume and playback volume of mixed custom audio track.**

| Param | DESC |
| --- | --- |
| playoutVolume | set the play volumeï¼from 0 to 150, -1 means no change |
| publishVolume | set the publish volumeï¼from 0 to 150, -1 means no change |

## generateCustomPTS

**generateCustomPTS**

**Generate custom capturing timestamp.**

This API is only suitable for the custom capturing mode and is used to solve the problem of out-of-sync audio/video caused by the inconsistency between the capturing time and delivery time of audio/video frames.

When you call APIs such as [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50754#2ec8cee427b69adc1b75be389c7eaef7) or [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50754#065fa14dfdbe241cd1d0286bf010388a) for custom video or audio capturing, please use this API as instructed below:

1. First, when a video or audio frame is captured, call this API to get the corresponding PTS timestamp.

2. Then, send the video or audio frame to the preprocessing module you use (such as a third-party beauty filter or sound effect component).

3. When you actually call [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50754#2ec8cee427b69adc1b75be389c7eaef7) or [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50754#065fa14dfdbe241cd1d0286bf010388a) for delivery, assign the PTS timestamp recorded when the frame was captured to the ` timestamp ` field in [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50760#9233a1b1573333abc70e53b51bd89740) or [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b).

**Return Desc:**

Timestamp in ms

## setLocalVideoProcessDelegete:pixelFormat:bufferType:

**setLocalVideoProcessDelegete:pixelFormat:bufferType:**

| - (int)setLocalVideoProcessDelegete: | (nullable id<[TRTCVideoFrameDelegate](https://www.tencentcloud.com/document/product/647/50755#f45e5e0d960d32bda6a106b1e1bddbd2)>)delegate |
| --- | --- |
| pixelFormat: | ([TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/50760#0fd3b6da1fb10e3d92eb55b00ba55dc3))pixelFormat |
| bufferType: | ([TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/50760#b2c90f7f7ec6ab033949b94f0fe34942))bufferType |

**Set video data callback for third-party beauty filters.**

After this callback is set, the SDK will call back the captured video frames through the ` delegate ` you set and use them for further processing by a third-party beauty filter component. Then, the SDK will encode and send the processed video frames.

| Param | DESC |
| --- | --- |
| bufferType | Specify the format of the data called back. Currently, only [TRTCVideoBufferType_Texture](https://www.tencentcloud.com/document/product/647/50760#b2c90f7f7ec6ab033949b94f0fe34942) is supported |
| delegate | Custom preprocessing callback. For more information, please see [TRTCVideoFrameDelegate](https://www.tencentcloud.com/document/product/647/50755#f45e5e0d960d32bda6a106b1e1bddbd2) |
| pixelFormat | Specify the format of the pixel called back. Currently, only [TRTCVideoPixelFormat_Texture_2D](https://www.tencentcloud.com/document/product/647/50760#0fd3b6da1fb10e3d92eb55b00ba55dc3) is supported |

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setLocalVideoRenderDelegate:pixelFormat:bufferType:

**setLocalVideoRenderDelegate:pixelFormat:bufferType:**

| - (int)setLocalVideoRenderDelegate: | (nullable id<[TRTCVideoRenderDelegate](https://www.tencentcloud.com/document/product/647/50755#85e5610430dc5cd10bc98afbcd6d2c67)>)delegate |
| --- | --- |
| pixelFormat: | ([TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/50760#0fd3b6da1fb10e3d92eb55b00ba55dc3))pixelFormat |
| bufferType: | ([TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/50760#b2c90f7f7ec6ab033949b94f0fe34942))bufferType |

**Set the callback of custom rendering for local video.**

After this callback is set, the SDK will skip its own rendering process and call back the captured data. Therefore, you need to complete image rendering on your own.

- ` pixelFormat ` specifies the format of the called back data, such as NV12, I420, and 32BGRA.
- ` bufferType ` specifies the buffer type. ` PixelBuffer ` has the highest efficiency, while ` NSData ` makes the SDK perform a memory conversion internally, which will result in extra performance loss.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/35158).

| Param | DESC |
| --- | --- |
| bufferType | PixelBuffer: this can be directly converted to ` UIImage ` by using ` imageWithCVImageBuffer `; NSData: this is memory-mapped video data. |
| delegate | Callback for custom rendering |
| pixelFormat | Specify the format of the pixel called back |

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setRemoteVideoRenderDelegate:delegate:pixelFormat:bufferType:

**setRemoteVideoRenderDelegate:delegate:pixelFormat:bufferType:**

| - (int)setRemoteVideoRenderDelegate: | (NSString*)userId |
| --- | --- |
| delegate: | (nullable id<[TRTCVideoRenderDelegate](https://www.tencentcloud.com/document/product/647/50755#85e5610430dc5cd10bc98afbcd6d2c67)>)delegate |
| pixelFormat: | ([TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/50760#0fd3b6da1fb10e3d92eb55b00ba55dc3))pixelFormat |
| bufferType: | ([TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/50760#b2c90f7f7ec6ab033949b94f0fe34942))bufferType |

**Set the callback of custom rendering for remote video.**

After this callback is set, the SDK will skip its own rendering process and call back the captured data. Therefore, you need to complete image rendering on your own.

- ` pixelFormat ` specifies the format of the called back data, such as NV12, I420, and 32BGRA.
- ` bufferType ` specifies the buffer type. ` PixelBuffer ` has the highest efficiency, while ` NSData ` makes the SDK perform a memory conversion internally, which will result in extra performance loss.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/35158).

| Param | DESC |
| --- | --- |
| bufferType | PixelBuffer: this can be directly converted to ` UIImage ` by using ` imageWithCVImageBuffer `; NSData: this is memory-mapped video data. |
| delegate | Callback for custom rendering |
| pixelFormat | Specify the format of the pixel called back |
| userId | ID of the specified remote user |

> **Note**Before this API is called, ` startRemoteView(nil) ` needs to be called to get the video stream of the remote user (` view ` can be set to ` nil ` for this end); otherwise, there will be no data called back.

**Return Desc:**

0: success; values smaller than 0: error

## setAudioFrameDelegate:

**setAudioFrameDelegate:**

| - (void)setAudioFrameDelegate: | (nullable id<[TRTCAudioFrameDelegate](https://www.tencentcloud.com/document/product/647/50755#da66ef151b799273aa9b22b41bef74a6)>)delegate |
| --- | --- |

**Set custom audio data callback.**

After this callback is set, the SDK will internally call back the audio data (in PCM format), including:

- [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50755#da380be77fec333b97a6955b2d33b496): callback of the audio data captured by the local mic
- [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50755#4e466d2653ea24dd48f363dd82c85110): callback of the audio data captured by the local mic and preprocessed by the audio module
- [onRemoteUserAudioFrame](https://www.tencentcloud.com/document/product/647/50755#7373aa620f0c23297ec72825c1d4f79a): audio data from each remote user before audio mixing
- [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50755#4c17d629cda95c9a635cceffa1bf28fd): callback of the audio data that will be played back by the system after audio streams are mixed

> **Note**Setting the callback to null indicates to stop the custom audio callback, while setting it to a non-null value indicates to start the custom audio callback.

## setCapturedAudioFrameDelegateFormat:

**setCapturedAudioFrameDelegateFormat:**

| - (int)setCapturedAudioFrameDelegateFormat: | ([TRTCAudioFrameDelegateFormat](https://www.tencentcloud.com/document/product/647/50760#d13de8c2e8d27df4b32b6fa3285c7607) *)format |
| --- | --- |

**Set the callback format of audio frames captured by local mic.**

This API is used to set the ` AudioFrame ` format called back by [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50755#da380be77fec333b97a6955b2d33b496):

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

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setLocalProcessedAudioFrameDelegateFormat:

**setLocalProcessedAudioFrameDelegateFormat:**

| - (int)setLocalProcessedAudioFrameDelegateFormat: | ([TRTCAudioFrameDelegateFormat](https://www.tencentcloud.com/document/product/647/50760#d13de8c2e8d27df4b32b6fa3285c7607) *)format |
| --- | --- |

**Set the callback format of preprocessed local audio frames.**

This API is used to set the ` AudioFrame ` format called back by [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50755#4e466d2653ea24dd48f363dd82c85110):

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

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## setMixedPlayAudioFrameDelegateFormat:

**setMixedPlayAudioFrameDelegateFormat:**

| - (int)setMixedPlayAudioFrameDelegateFormat: | ([TRTCAudioFrameDelegateFormat](https://www.tencentcloud.com/document/product/647/50760#d13de8c2e8d27df4b32b6fa3285c7607) *)format |
| --- | --- |

**Set the callback format of audio frames to be played back by system.**

This API is used to set the ` AudioFrame ` format called back by [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50755#4c17d629cda95c9a635cceffa1bf28fd):

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

0: success; values smaller than 0: error(For more information, please see TXLiteAVError)

## enableCustomAudioRendering:

**enableCustomAudioRendering:**

| - (void)enableCustomAudioRendering: | (BOOL)enable |
| --- | --- |

**Enabling custom audio playback.**

You can use this API to enable custom audio playback if you want to connect to an external audio device or control the audio playback logic by yourself.

After you enable custom audio playback, the SDK will stop using its audio API to play back audio. You need to call [getCustomAudioRenderingFrame](https://www.tencentcloud.com/document/product/647/50754#d0c11de324866d2a2c8555567a3963d4) to get audio frames and play them by yourself.

| Param | DESC |
| --- | --- |
| enable | Whether to enable custom audio playback. It's disabled by default. |

> **Note**The parameter must be set before room entry to take effect.

## getCustomAudioRenderingFrame:

**getCustomAudioRenderingFrame:**

| - (void)getCustomAudioRenderingFrame: | ([TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) *)audioFrame |
| --- | --- |

**Getting playable audio data.**

Before calling this API, you need to first enable custom audio playback using [enableCustomAudioRendering](https://www.tencentcloud.com/document/product/647/50754#24703ae7507b94e475a89700e8b1bb9b).

Fill the fields in [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50760#712e9ebdb0469f1ee53dc91617c62d6b) as follows (other fields are not required):

- ` sampleRate `: sample rate (required). Valid values: 16000, 24000, 32000, 44100, 48000
- ` channel `: number of sound channels (required). ` 1 `: mono-channel; ` 2 `: dual-channel; if dual-channel is used, data is interleaved.
- ` data `: the buffer used to get audio data. You need to allocate memory for the buffer based on the duration of an audio frame.

The PCM data obtained can have a frame duration of 10 ms or 20 ms. 20 ms is recommended.

Assume that the sample rate is 48000, and sound channels mono-channel. The buffer size for a 20 ms audio frame would be ` 48000 x 0.02s x 1 x 16 bit = 15360 bit = 1920 bytes `.

| Param | DESC |
| --- | --- |
| audioFrame | Audio frames |

> **Note**1. You must set ` sampleRate ` and ` channel ` in ` audioFrame `, and allocate memory for one frame of audio in advance.2. The SDK will fill the data automatically based on ` sampleRate ` and ` channel `.3. We recommend that you use the systemâs audio playback thread to drive the calling of this API, so that it is called each time the playback of an audio frame is complete.

## sendCustomCmdMsg:data:reliable:ordered:

**sendCustomCmdMsg:data:reliable:ordered:**

| - (BOOL)sendCustomCmdMsg: | (NSInteger)cmdID |
| --- | --- |
| data: | (NSData *)data |
| reliable: | (BOOL)reliable |
| ordered: | (BOOL)ordered |

**Use UDP channel to send custom message to all users in room.**

This API allows you to use TRTC's UDP channel to broadcast custom data to other users in the current room for signaling transfer.

Other users in the room can receive the message through the ` onRecvCustomCmdMsg ` callback in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

| Param | DESC |
| --- | --- |
| cmdID | Message ID. Value range: [1, 10] |
| data | Message to be sent. The maximum length of one single message is 1 KB. |
| ordered | Whether orderly sending is enabled, i.e., whether the data packets should be received in the same order in which they are sent; if so, a certain delay will be caused. |
| reliable | Whether reliable sending is enabled. Reliable sending can achieve a higher success rate but with a longer reception delay than unreliable sending. |

> **Note**1. Up to 30 messages can be sent per second to all users in the room (this is not supported for web and mini program currently. this limit is shared with [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50754#f1c4a686a1e513f8dce8b8d57cc5bbe8)).2. A packet can contain up to 1 KB of data; if the threshold is exceeded, the packet is very likely to be discarded by the intermediate router or server.(this limit is shared with [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50754#f1c4a686a1e513f8dce8b8d57cc5bbe8)).3. A client can send up to 16 KB of data in total per second.4. ` reliable ` and ` ordered ` must be set to the same value (` YES ` or ` NO `) and cannot be set to different values currently.5. We strongly recommend you set different ` cmdID ` values for messages of different types. This can reduce message delay when orderly sending is required.6. Currently only the anchor role is supported.

**Return Desc:**

YES: sent the message successfully; NO: failed to send the message.

## sendSEIMsg:repeatCount:

**sendSEIMsg:repeatCount:**

| - (BOOL)sendSEIMsg: | (NSData *)data |
| --- | --- |
| repeatCount: | (int)repeatCount |

**Use SEI channel to send custom message to all users in room.**

This API allows you to use TRTC's SEI channel to broadcast custom data to other users in the current room for signaling transfer.

The header of a video frame has a header data block called SEI. This API works by embedding the custom signaling data you want to send in the SEI block and sending it together with the video frame.

Therefore, the SEI channel has a better compatibility than [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50754#65a0ef621d0fdc876f649fc8b20ca117) as the signaling data can be transferred to the CSS CDN along with the video frame.

However, because the data block of the video frame header cannot be too large, we recommend you limit the size of the signaling data to only a few bytes when using this API.

The most common use is to embed the custom timestamp into video frames through this API so as to implement a perfect alignment between the message and video image (such as between the teaching material and video signal in the education scenario).

Other users in the room can receive the message through the ` onRecvSEIMsg ` callback in [TRTCCloudDelegate](https://www.tencentcloud.com/document/product/647/50755#d8f7bddf1dbd4490d7801cb74808ed04).

| Param | DESC |
| --- | --- |
| data | Data to be sent, which can be up to 1 KB (1,000 bytes) |
| repeatCount | Data sending count |

> **Note**This API has the following restrictions:1. The data will not be instantly sent after this API is called; instead, it will be inserted into the next video frame after the API call.2. Up to 30 messages can be sent per second to all users in the room (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50754#65a0ef621d0fdc876f649fc8b20ca117)).3. Each packet can be up to 1 KB (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50754#65a0ef621d0fdc876f649fc8b20ca117)). If a large amount of data is sent, the video bitrate will increase, which may reduce the video quality or even cause lagging.4. Each client can send up to 16 KB of data in total per second (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50754#65a0ef621d0fdc876f649fc8b20ca117)).5. If multiple times of sending is required (i.e., ` repeatCount ` > 1), the data will be inserted into subsequent ` repeatCount ` video frames in a row for sending, which will increase the video bitrate.6. If ` repeatCount ` is greater than 1, the data will be sent for multiple times, and the same message may be received multiple times in the [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/50755#ca85eadea7896e29f377476dc2827dc9) callback; therefore, deduplication is required.

**Return Desc:**

YES: the message is allowed and will be sent with subsequent video frames; NO: the message is not allowed to be sent

## startSpeedTest:

**startSpeedTest:**

| - (int)startSpeedTest: | ([TRTCSpeedTestParams](https://www.tencentcloud.com/document/product/647/50760#dd22aad94fc4b4773ca7323c7d34a1a7) *)params |
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

## setLogLevel:

**setLogLevel:**

| + (void)setLogLevel: | ([TRTCLogLevel](https://www.tencentcloud.com/document/product/647/50760#3b7ff44175cba4dd48e97aa8ac7b0b98))level |
| --- | --- |

**Set log output level.**

| Param | DESC |
| --- | --- |
| level | For more information, please see [TRTCLogLevel](https://www.tencentcloud.com/document/product/647/50760#3b7ff44175cba4dd48e97aa8ac7b0b98). Default value: [TRTCLogLevelNone](https://www.tencentcloud.com/document/product/647/50760#3b7ff44175cba4dd48e97aa8ac7b0b98) |

## setConsoleEnabled:

**setConsoleEnabled:**

| + (void)setConsoleEnabled: | (BOOL)enabled |
| --- | --- |

**Enable/Disable console log printing.**

| Param | DESC |
| --- | --- |
| enabled | Specify whether to enable it, which is disabled by default |

## setLogCompressEnabled:

**setLogCompressEnabled:**

| + (void)setLogCompressEnabled: | (BOOL)enabled |
| --- | --- |

**Enable/Disable local log compression.**

If compression is enabled, the log size will significantly reduce, but logs can be read only after being decompressed by the Python script provided by Tencent Cloud.

If compression is disabled, logs will be stored in plaintext and can be read directly in Notepad, but will take up more storage capacity.

| Param | DESC |
| --- | --- |
| enabled | Specify whether to enable it, which is enabled by default |

## setLogDirPath:

**setLogDirPath:**

| + (void)setLogDirPath: | (NSString *)path |
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

## setLogDelegate:

**setLogDelegate:**

| + (void)setLogDelegate: | (nullable id<[TRTCLogDelegate](https://www.tencentcloud.com/document/product/647/50755#245049730b9ca4c832680b7940cebb9b)>)logDelegate |
| --- | --- |

**Set log callback.**

## showDebugView:

**showDebugView:**

| - (void)showDebugView: | (NSInteger)showType |
| --- | --- |

**Display dashboard.**

"Dashboard" is a semi-transparent floating layer for debugging information on top of the video rendering control. It is used to display audio/video information and event information to facilitate integration and debugging.

| Param | DESC |
| --- | --- |
| showType | 0: does not display; 1: displays lite edition (only with audio/video information); 2: displays full edition (with audio/video information and event information). |

## setDebugViewMargin:margin:

**setDebugViewMargin:margin:**

| - (void)setDebugViewMargin: | (NSString *)userId |
| --- | --- |
| margin: | (TXEdgeInsets)margin |

**Set dashboard margin.**

This API is used to adjust the position of the dashboard in the video rendering control. It must be called before [showDebugView](https://www.tencentcloud.com/document/product/647/50754#237b5598918783a30b64118a6215d9d2) for it to take effect.

| Param | DESC |
| --- | --- |
| margin | Inner margin of the dashboard. It should be noted that this is based on the percentage of ` parentView `. Value range: [0, 1] |
| userId | User ID |

## callExperimentalAPI:

**callExperimentalAPI:**

| - (NSString*)callExperimentalAPI: | (NSString*)jsonStr |
| --- | --- |

**Call experimental APIs.**

## enablePayloadPrivateEncryption:params:

**enablePayloadPrivateEncryption:params:**

| - (int)enablePayloadPrivateEncryption: | (BOOL)enabled |
| --- | --- |
| params: | ([TRTCPayloadPrivateEncryptionConfig](https://www.tencentcloud.com/document/product/647/50760#e31d0d9395f1cb44ee256f450523ce86) *)config |

**Enable or disable private encryption of media streams.**

In scenarios with high security requirements, TRTC recommends that you call the enablePayloadPrivateEncryption method to enable private encryption of media streams before joining a room.

After the user exits the room, the SDK will automatically close the private encryption. To re-enable private encryption, you need to call this method before the user joins the room again.

| Param | DESC |
| --- | --- |
| config | Configure the algorithm and key for private encryption of media streams, please see [TRTCPayloadPrivateEncryptionConfig](https://www.tencentcloud.com/document/product/647/50760#e31d0d9395f1cb44ee256f450523ce86). |
| enabled | Whether to enable media stream private encryption. |

> **Note**TRTC has built-in encryption for media streams before transmission. After private encryption of media streams is enabled, it will be re-encrypted with the key and initial vector you pass in.

**Return Desc:**

Interface call result, 0: Method call succeeded, -1: The incoming parameter is invalid, -2: Your subscription has expired. If you want to renew it, Please go to purchase the [TRTC Professional Edition](https://console.trtc.io/subscription/buy/rtc?packType=pro), and [contact us](https://trtc.io/zh/contact) for review before use.


---
*Source: [https://trtc.io/document/50754](https://trtc.io/document/50754)*
