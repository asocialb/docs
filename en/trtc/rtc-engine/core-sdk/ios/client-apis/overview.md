# Overview

**API OVERVIEW**

## Create Instance And Event Callback

| FuncList | DESC |
| --- | --- |
| [sharedInstance](https://www.tencentcloud.com/document/product/647/50754#6bb80f84c5674f5fa98cf67080909c71) | Create TRTCCloud instance (singleton mode). |
| [destroySharedInstance](https://www.tencentcloud.com/document/product/647/50754#efdff42059de072cfccbb4fcf1bc9646) | Terminate TRTCCloud instance (singleton mode). |
| [addDelegate:](https://www.tencentcloud.com/document/product/647/50754#e227a9126fee9a548fec6d0051326ffc) | Add TRTC event callback. |
| [removeDelegate:](https://www.tencentcloud.com/document/product/647/50754#203bf0b8d403ecda3beafd1fc386155c) | Remove TRTC event callback. |
| [delegateQueue](https://www.tencentcloud.com/document/product/647/50754#3d350e9088c246f32d434ce3514ed9e8) | Set the queue that drives the TRTCCloudDelegate event callback. |

## Room APIs

| FuncList | DESC |
| --- | --- |
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

## CDN APIs

| FuncList | DESC |
| --- | --- |
| [startPublishMediaStream:encoderParam:mixingConfig:](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e) | Publish a stream. |
| [updatePublishMediaStream:publishTarget:encoderParam:mixingConfig:](https://www.tencentcloud.com/document/product/647/50754#fc8a7778d8fc91d7dff4c3801b5e5cfe) | Modify publishing parameters. |
| [stopPublishMediaStream:](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e) | Stop publishing. |

## Video APIs

| FuncList | DESC |
| --- | --- |
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

## Audio APIs

| FuncList | DESC |
| --- | --- |
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

## Device management APIs

| FuncList | DESC |
| --- | --- |
| [getDeviceManager](https://www.tencentcloud.com/document/product/647/50754#db8daa4a00cfdd6e2b2d436ace8b54e0) | Get device management class (TXDeviceManager). |

## Beauty filter and watermark APIs

| FuncList | DESC |
| --- | --- |
| [getBeautyManager](https://www.tencentcloud.com/document/product/647/50754#a74f40ea545fcc505d53f767ff09c71e) | Get beauty filter management class (TXBeautyManager). |
| [setWatermark:streamType:rect:](https://www.tencentcloud.com/document/product/647/50754#1e65eb4cba6287f43eefab07aab02895) | Add watermark. |

## Background music and sound effect APIs

| FuncList | DESC |
| --- | --- |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/50754#324d36f56aaba193d6ea8c2ed04b3633) | Get sound effect management class (TXAudioEffectManager). |
| [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50754#755f9f590bf398deb0c538b32a2aede2) | Enable system audio capturing(iOS not supported). |
| [stopSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50754#3da3978da7aa2b81e524fba4f7bb05a5) | Stop system audio capturing(iOS not supported). |
| [setSystemAudioLoopbackVolume:](https://www.tencentcloud.com/document/product/647/50754#679fb63113ef1285208c35c406a74ff0) | Set the volume of system audio capturing. |

## Screen sharing APIs

| FuncList | DESC |
| --- | --- |
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

## Custom capturing and rendering APIs

| FuncList | DESC |
| --- | --- |
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

## Custom message sending APIs

| FuncList | DESC |
| --- | --- |
| [sendCustomCmdMsg:data:reliable:ordered:](https://www.tencentcloud.com/document/product/647/50754#65a0ef621d0fdc876f649fc8b20ca117) | Use UDP channel to send custom message to all users in room. |
| [sendSEIMsg:repeatCount:](https://www.tencentcloud.com/document/product/647/50754#f1c4a686a1e513f8dce8b8d57cc5bbe8) | Use SEI channel to send custom message to all users in room. |

## Network test APIs

| FuncList | DESC |
| --- | --- |
| [startSpeedTest:](https://www.tencentcloud.com/document/product/647/50754#9446ef81737de395b79baa311622f04e) | Start network speed test (used before room entry). |
| [stopSpeedTest](https://www.tencentcloud.com/document/product/647/50754#c039fb88d4d55a5ba7d6b4e48120e569) | Stop network speed test. |

## Debugging APIs

| FuncList | DESC |
| --- | --- |
| [getSDKVersion](https://www.tencentcloud.com/document/product/647/50754#483cc6aeb60177fca185ac596ce47c5c) | Get SDK version information. |
| [setLogLevel:](https://www.tencentcloud.com/document/product/647/50754#76af89e47bf1be956d6bea99277b21ad) | Set log output level. |
| [setConsoleEnabled:](https://www.tencentcloud.com/document/product/647/50754#4acb68e95c32c395723d66ca1437348a) | Enable/Disable console log printing. |
| [setLogCompressEnabled:](https://www.tencentcloud.com/document/product/647/50754#fe3626e347f2d7cdd7bad55630255901) | Enable/Disable local log compression. |
| [setLogDirPath:](https://www.tencentcloud.com/document/product/647/50754#b37af0c781ddf50244c1a81370384c74) | Set local log storage path. |
| [setLogDelegate:](https://www.tencentcloud.com/document/product/647/50754#0e9c1d84c3eaea94d94b31eb460acd3d) | Set log callback. |
| [showDebugView:](https://www.tencentcloud.com/document/product/647/50754#237b5598918783a30b64118a6215d9d2) | Display dashboard. |
| [setDebugViewMargin:margin:](https://www.tencentcloud.com/document/product/647/50754#0954b98d38ecc392a3330babbcb286ac) | Set dashboard margin. |
| [callExperimentalAPI:](https://www.tencentcloud.com/document/product/647/50754#c052372d1d99c72d35109f8c33d23fc3) | Call experimental APIs. |

## Encrypted interface

| FuncList | DESC |
| --- | --- |
| [enablePayloadPrivateEncryption:params:](https://www.tencentcloud.com/document/product/647/50754#999b4ba6e9f3bdba882955507f30df02) | Enable or disable private encryption of media streams. |

## Error and warning events

| FuncList | DESC |
| --- | --- |
| [onError:errMsg:extInfo:](https://www.tencentcloud.com/document/product/647/50755#98036f82055fc2396135d65f53b5352e) | Error event callback. |
| [onWarning:warningMsg:extInfo:](https://www.tencentcloud.com/document/product/647/50755#d5e4b51436cb24c1729e800ba4e14fc7) | Warning event callback. |

## Room event callback

| FuncList | DESC |
| --- | --- |
| [onEnterRoom:](https://www.tencentcloud.com/document/product/647/50755#1301efa2e0717a4563b73173dc0c6e57) | Whether room entry is successful. |
| [onExitRoom:](https://www.tencentcloud.com/document/product/647/50755#95c38564f6c910cbb33746046da9cb8d) | Room exit. |
| [onSwitchRole:errMsg:](https://www.tencentcloud.com/document/product/647/50755#ac3151ae1495107f0e7f03f0d9542bc1) | Role switching. |
| [onSwitchRoom:errMsg:](https://www.tencentcloud.com/document/product/647/50755#999e808efabcd529554d107b1c6cd87b) | Result of room switching. |
| [onConnectOtherRoom:errCode:errMsg:](https://www.tencentcloud.com/document/product/647/50755#b18062a114b045be21872948fdf4dbad) | Result of requesting cross-room call. |
| [onDisconnectOtherRoom:errMsg:](https://www.tencentcloud.com/document/product/647/50755#5abe6df6e800adb198a270f3562718ce) | Result of ending cross-room call. |
| [onUpdateOtherRoomForwardMode:errMsg:](https://www.tencentcloud.com/document/product/647/50755#b1dd7c7bc5eea79931e0b8c67f055832) | Result of changing the upstream capability of the cross-room anchor. |

## User event callback.

| FuncList | DESC |
| --- | --- |
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

## Callback of statistics on network and technical metrics.

| FuncList | DESC |
| --- | --- |
| [onNetworkQuality:remoteQuality:](https://www.tencentcloud.com/document/product/647/50755#bed8fae237b70d2eb41ef79fcd80cc39) | Real-time network quality statistics. |
| [onStatistics:](https://www.tencentcloud.com/document/product/647/50755#93a0b2ea899a43e082cf11a8f1f156b1) | Real-time statistics on technical metrics. |
| [onSpeedTestResult:](https://www.tencentcloud.com/document/product/647/50755#c7e95e341056e89e96ca3ee422a64fbb) | Callback of network speed test. |

## Callback of connection to the cloud

| FuncList | DESC |
| --- | --- |
| [onConnectionLost](https://www.tencentcloud.com/document/product/647/50755#02f8b3e9b8f7e4c2880664873a5e5ebf) | The SDK was disconnected from the cloud. |
| [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50755#4adcb84c3609b674d8fa21c85afe3822) | The SDK is reconnecting to the cloud. |
| [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50755#531b03dfa5421c4cf58840304294c4e1) | The SDK is reconnected to the cloud. |

## Callback of hardware events

| FuncList | DESC |
| --- | --- |
| [onCameraDidReady](https://www.tencentcloud.com/document/product/647/50755#ec5a558dd75524fad4cd432fa67fed42) | The camera is ready. |
| [onMicDidReady](https://www.tencentcloud.com/document/product/647/50755#4b77128c829032d35c7a0aa00b079e67) | The mic is ready. |
| [onAudioRouteChanged:fromRoute:](https://www.tencentcloud.com/document/product/647/50755#a9a145e262beb35b8e9185df3a4e67b0) | The audio route changed (for mobile devices only). |
| [onUserVoiceVolume:totalVolume:](https://www.tencentcloud.com/document/product/647/50755#c28a692ba631a72b910e17b042d6f293) | Volume. |
| [onDevice:type:stateChanged:](https://www.tencentcloud.com/document/product/647/50755#6d014ddf887fb42b6b1bcb09c421ac77) | The status of a local device changed (for desktop OS only). |
| [onAudioDeviceCaptureVolumeChanged:muted:](https://www.tencentcloud.com/document/product/647/50755#de2fa988c26d3d9a9cc2567ef876920e) | The capturing volume of the mic changed. |
| [onAudioDevicePlayoutVolumeChanged:muted:](https://www.tencentcloud.com/document/product/647/50755#6f2d12e81ddcdba1fb0d2fc2d59ff17d) | The playback volume changed. |
| [onSystemAudioLoopbackError:](https://www.tencentcloud.com/document/product/647/50755#fd5d382c0ddacab5a7d80671cbf1832d) | Whether system audio capturing is enabled successfully (for desktop OS only). |

## Callback of the receipt of a custom message.

| FuncList | DESC |
| --- | --- |
| [onRecvCustomCmdMsgUserId:cmdID:seq:message:](https://www.tencentcloud.com/document/product/647/50755#667629e70997daf22ff61a07545c66b4) | Receipt of custom message. |
| [onMissCustomCmdMsgUserId:cmdID:errCode:missed:](https://www.tencentcloud.com/document/product/647/50755#6b1a0dd8786abac4e6a9c313a570cf11) | Loss of custom message. |
| [onRecvSEIMsg:message:](https://www.tencentcloud.com/document/product/647/50755#ca85eadea7896e29f377476dc2827dc9) | Receipt of SEI message. |

## CDN event callback

| FuncList | DESC |
| --- | --- |
| [onStartPublishing:errMsg:](https://www.tencentcloud.com/document/product/647/50755#17672fd0fbc3c4d85470d3464ae8ff5a) | Started publishing to Tencent Cloud CSS CDN. |
| [onStopPublishing:errMsg:](https://www.tencentcloud.com/document/product/647/50755#197b5d3744d2c49a1e2777c454eabb21) | Stopped publishing to Tencent Cloud CSS CDN. |
| [onStartPublishCDNStream:errMsg:](https://www.tencentcloud.com/document/product/647/50755#10dac4ffc70848883357a40d4595f387) | Started publishing to non-Tencent Cloudâs live streaming CDN. |
| [onStopPublishCDNStream:errMsg:](https://www.tencentcloud.com/document/product/647/50755#a02ff3be93fe002dd85e24f6d526ef0b) | Stopped publishing to non-Tencent Cloudâs live streaming CDN. |
| [onSetMixTranscodingConfig:errMsg:](https://www.tencentcloud.com/document/product/647/50755#ae934629ed64d447aae708d44d21380f) | Set the layout and transcoding parameters for On-Cloud MixTranscoding. |
| [onStartPublishMediaStream:code:message:extraInfo:](https://www.tencentcloud.com/document/product/647/50755#7793cc61deebd412cb1f1b8c4762cb3e) | Callback for starting to publish. |
| [onUpdatePublishMediaStream:code:message:extraInfo:](https://www.tencentcloud.com/document/product/647/50755#f346d805a3514f0e4d64b3833124645e) | Callback for modifying publishing parameters. |
| [onStopPublishMediaStream:code:message:extraInfo:](https://www.tencentcloud.com/document/product/647/50755#a21c1d4f01b00f2e6a01ea1975358902) | Callback for stopping publishing. |
| [onCdnStreamStateChanged:status:code:msg:extraInfo:](https://www.tencentcloud.com/document/product/647/50755#6d9f289cca801ada27b66f274d855223) | Callback for change of RTMP/RTMPS publishing status. |

## Screen sharing event callback

| FuncList | DESC |
| --- | --- |
| [onScreenCaptureStarted](https://www.tencentcloud.com/document/product/647/50755#f8f5dcda1fa11da88aacd50e441ba279) | Screen sharing started. |
| [onScreenCapturePaused:](https://www.tencentcloud.com/document/product/647/50755#bda29151f45073c1d972b8236b301a49) | Screen sharing was paused. |
| [onScreenCaptureResumed:](https://www.tencentcloud.com/document/product/647/50755#c2c14200a63c8dcbf69c691738deca8d) | Screen sharing was resumed. |
| [onScreenCaptureStoped:](https://www.tencentcloud.com/document/product/647/50755#13c882d11cf67b8b87b6387b7da7741c) | Screen sharing stopped. |

## Callback of local recording and screenshot events

| FuncList | DESC |
| --- | --- |
| [onLocalRecordBegin:storagePath:](https://www.tencentcloud.com/document/product/647/50755#4ec87a51e74a97ee8e58fea261081bb0) | Local recording started. |
| [onLocalRecording:storagePath:](https://www.tencentcloud.com/document/product/647/50755#c41ae5ce2e56dc0c63718ebc8963bb85) | Local media is being recorded. |
| [onLocalRecordFragment:](https://www.tencentcloud.com/document/product/647/50755#7c3216a760663566d5a04c620a153afa) | Record fragment finished. |
| [onLocalRecordComplete:storagePath:](https://www.tencentcloud.com/document/product/647/50755#d1f747d79e07579f09a0e2358399321e) | Local recording stopped. |

## Disused callbacks

| FuncList | DESC |
| --- | --- |
| [onUserEnter:](https://www.tencentcloud.com/document/product/647/50755#a92c91b0ff3b5baa530f08e8d5dad494) | An anchor entered the room (disused). |
| [onUserExit:reason:](https://www.tencentcloud.com/document/product/647/50755#f6cb1c4f996bfe8565865f68e8f66a4e) | An anchor left the room (disused). |
| [onAudioEffectFinished:code:](https://www.tencentcloud.com/document/product/647/50755#a46a76f2cf33b96a7d5e25725d828e5f) | Audio effects ended (disused). |

## Callback of custom video processing

| FuncList | DESC |
| --- | --- |
| [onRenderVideoFrame:userId:streamType:](https://www.tencentcloud.com/document/product/647/50755#2554116174a810d42ab22ec89eb5c0ac) | Custom video rendering. |
| [onGLContextCreated](https://www.tencentcloud.com/document/product/647/50755#e8f3ba7f5571f4974658a599c50787ec) | An OpenGL context was created in the SDK. |
| [onProcessVideoFrame:dstFrame:](https://www.tencentcloud.com/document/product/647/50755#b8d844b62eb629ec92eeb49f31ce7d14) | Video processing by third-party beauty filters. |
| [onGLContextDestory](https://www.tencentcloud.com/document/product/647/50755#1887ebbbea32eba8584032e3e40f4d68) | The OpenGL context in the SDK was destroyed. |

## Callback of custom audio processing

| FuncList | DESC |
| --- | --- |
| [onCapturedAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#da380be77fec333b97a6955b2d33b496) | Audio data captured by the local mic and pre-processed by the audio module. |
| [onLocalProcessedAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#4e466d2653ea24dd48f363dd82c85110) | Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed. |
| [onRemoteUserAudioFrame:userId:](https://www.tencentcloud.com/document/product/647/50755#7373aa620f0c23297ec72825c1d4f79a) | Audio data of each remote user before audio mixing. |
| [onMixedPlayAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#4c17d629cda95c9a635cceffa1bf28fd) | Data mixed from each channel before being submitted to the system for playback. |
| [onMixedAllAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#c0a618f0068e7cd9f922bcc43d9e940a) | Data mixed from all the captured and to-be-played audio in the SDK. |
| [onVoiceEarMonitorAudioFrame:](https://www.tencentcloud.com/document/product/647/50755#eb7453a97f1bffad68271c27fffbd167) | In-ear monitoring data. |

## Other event callbacks

| FuncList | DESC |
| --- | --- |
| [onLog:LogLevel:WhichModule:](https://www.tencentcloud.com/document/product/647/50755#0a6cc600612002ebc150de8f563777c9) | Printing of local log. |

## Voice effect APIs

| FuncList | DESC |
| --- | --- |
| [enableVoiceEarMonitor:](https://www.tencentcloud.com/document/product/647/50757#300c68bccbf3480ab8c99cf2f31d014a) | Enabling in-ear monitoring. |
| [setVoiceEarMonitorVolume:](https://www.tencentcloud.com/document/product/647/50757#3857607a3e9b5fc2e57a77f2c1dd6359) | Setting in-ear monitoring volume. |
| [setVoiceReverbType:](https://www.tencentcloud.com/document/product/647/50757#7135a441f275bed8330db039f1bfba2d) | Setting voice reverb effects. |
| [setVoiceChangerType:](https://www.tencentcloud.com/document/product/647/50757#fee0da19f6060c0544e73a79da113bd0) | Setting voice changing effects. |
| [setVoiceVolume:](https://www.tencentcloud.com/document/product/647/50757#9fe5b02fc52fa9bfae721e1f0d4d9427) | Setting speech volume. |
| [setVoicePitch:](https://www.tencentcloud.com/document/product/647/50757#517e19882847820a81b870d49d1ae2f4) | Setting speech pitch. |

## Background music APIs

| FuncList | DESC |
| --- | --- |
| [startPlayMusic:onStart:onProgress:onComplete:](https://www.tencentcloud.com/document/product/647/50757#3e6d92e47d6770c50e0e4ca4df429c31) | Starting background music. |
| [stopPlayMusic:](https://www.tencentcloud.com/document/product/647/50757#2214eecbdca5062136821aff0d95bfbe) | Stopping background music. |
| [pausePlayMusic:](https://www.tencentcloud.com/document/product/647/50757#8e5076dea4c4b43df4c07cf1fe4003f1) | Pausing background music. |
| [resumePlayMusic:](https://www.tencentcloud.com/document/product/647/50757#15f5b80077c596dc1d39402d421a6ec2) | Resuming background music. |
| [setAllMusicVolume:](https://www.tencentcloud.com/document/product/647/50757#8fafba6b1d27799ea32812f08f564ee5) | Setting the local and remote playback volume of background music. |
| [setMusicPublishVolume:volume:](https://www.tencentcloud.com/document/product/647/50757#50a9fe2dc5ee4a6f92160ef4f1367c13) | Setting the remote playback volume of a specific music track. |
| [setMusicPlayoutVolume:volume:](https://www.tencentcloud.com/document/product/647/50757#5ba979d09b84dfe360785c659ab7c8b7) | Setting the local playback volume of a specific music track. |
| [setMusicPitch:pitch:](https://www.tencentcloud.com/document/product/647/50757#6f7407593caa553bccee1da218e79d2e) | Adjusting the pitch of background music. |
| [setMusicSpeedRate:speedRate:](https://www.tencentcloud.com/document/product/647/50757#5a66bf1956d164a98f5f274f46b9c3a7) | Changing the speed of background music. |
| [getMusicCurrentPosInMS:](https://www.tencentcloud.com/document/product/647/50757#4d6f9629f7623102e3e04f5e05bdea1e) | Getting the playback progress (ms) of background music. |
| [getMusicDurationInMS:](https://www.tencentcloud.com/document/product/647/50757#6ca86334e6bf179bc3cfd98ca5e01975) | Getting the total length (ms) of background music. |
| [seekMusicToPosInMS:pts:](https://www.tencentcloud.com/document/product/647/50757#c00ed7c5735f4c126f0fbd099cae8998) | Setting the playback progress (ms) of background music. |
| [setMusicScratchSpeedRate:speedRate:](https://www.tencentcloud.com/document/product/647/50757#76ccca8d0e4ad4ef6ba3abc02170b18b) | Adjust the speed change effect of the scratch disc. |
| [preloadMusic:onProgress:onError:](https://www.tencentcloud.com/document/product/647/50757#c5a7017fe11985ad47ba9e935d726020) | Preload background music. |
| [getMusicTrackCount:](https://www.tencentcloud.com/document/product/647/50757#19fc33f9be59df8b0f4524219fbd4350) | Get the number of tracks of background music. |
| [setMusicTrack:track:](https://www.tencentcloud.com/document/product/647/50757#bcac516dcc63f775829e34f75646fdf4) | Specify the playback track of background music. |

## beauty interface

| FuncList | DESC |
| --- | --- |
| [setBeautyStyle:](https://www.tencentcloud.com/document/product/647/50758#89215cdfd5905aa81993b53b8c6b66be) | Sets the beauty (skin smoothing) filter algorithm. |
| [setBeautyLevel:](https://www.tencentcloud.com/document/product/647/50758#b5fedd8ce52caee75365c967a92b08e4) | Sets the strength of the beauty filter. |
| [setWhitenessLevel:](https://www.tencentcloud.com/document/product/647/50758#6e5243ac8d73b038a9c603a3ee7f7e38) | Sets the strength of the brightening filter. |
| [enableSharpnessEnhancement:](https://www.tencentcloud.com/document/product/647/50758#19b6a86699f384e98f6071f2040aed3a) | Enables clarity enhancement. |
| [setRuddyLevel:](https://www.tencentcloud.com/document/product/647/50758#821ebd8ee9c03f1b5e5ae77121cc61c3) | Sets the strength of the rosy skin filter. |
| [setFilter:](https://www.tencentcloud.com/document/product/647/50758#f73520b36361749d3f59eeb6db50f940) | Sets color filter. |
| [setFilterStrength:](https://www.tencentcloud.com/document/product/647/50758#4115cda15fa0692c38d1fe4b825a8b81) | Sets the strength of color filter. |
| [setGreenScreenFile:](https://www.tencentcloud.com/document/product/647/50758#c161a410f89d9f10e10dad0f1aaa6cf7) | Sets green screen video. |
| [setEyeScaleLevel:](https://www.tencentcloud.com/document/product/647/50758#2bf78eafcb88db8fdd9398eb4011619b) | Sets the strength of the eye enlarging filter. |
| [setFaceSlimLevel:](https://www.tencentcloud.com/document/product/647/50758#da3ed5adfa61941f1a11adc9938e9ba5) | Sets the strength of the face slimming filter. |
| [setFaceVLevel:](https://www.tencentcloud.com/document/product/647/50758#8350cda9b6a217967d8274cc39ccc6e6) | Sets the strength of the chin slimming filter. |
| [setChinLevel:](https://www.tencentcloud.com/document/product/647/50758#c3a377df9b943cbb361e87e2c9c7c47d) | Sets the strength of the chin lengthening/shortening filter. |
| [setFaceShortLevel:](https://www.tencentcloud.com/document/product/647/50758#98f562ff406656d9808f5a830403f301) | Sets the strength of the face shortening filter. |
| [setFaceNarrowLevel:](https://www.tencentcloud.com/document/product/647/50758#86fc487ad9836db7ef9e563917fcead9) | Sets the strength of the face narrowing filter. |
| [setNoseSlimLevel:](https://www.tencentcloud.com/document/product/647/50758#15b40583cade49e0487647d7f5c26d7c) | Sets the strength of the nose slimming filter. |
| [setEyeLightenLevel:](https://www.tencentcloud.com/document/product/647/50758#b02bf69415717f60da87233ab2a1bbf8) | Sets the strength of the eye brightening filter. |
| [setToothWhitenLevel:](https://www.tencentcloud.com/document/product/647/50758#3d97ddad87942486cb07496a4587447f) | Sets the strength of the teeth whitening filter. |
| [setWrinkleRemoveLevel:](https://www.tencentcloud.com/document/product/647/50758#a412c7fb9fcea0dc7c10d96a9aca95a5) | Sets the strength of the wrinkle removal filter. |
| [setPounchRemoveLevel:](https://www.tencentcloud.com/document/product/647/50758#846593213cef3d1f7b249586d209f0bf) | Sets the strength of the eye bag removal filter. |
| [setSmileLinesRemoveLevel:](https://www.tencentcloud.com/document/product/647/50758#aaded62695d2171b734016192ecf4fcb) | Sets the strength of the smile line removal filter. |
| [setForeheadLevel:](https://www.tencentcloud.com/document/product/647/50758#b608f5fe8511f829d131d32fc62654ab) | Sets the strength of the hairline adjustment filter. |
| [setEyeDistanceLevel:](https://www.tencentcloud.com/document/product/647/50758#2d0cb800cea51b9f8b09325e6adadb8d) | Sets the strength of the eye distance adjustment filter. |
| [setEyeAngleLevel:](https://www.tencentcloud.com/document/product/647/50758#643e7e93c2cbea98c2476b5cbc3d997d) | Sets the strength of the eye corner adjustment filter. |
| [setMouthShapeLevel:](https://www.tencentcloud.com/document/product/647/50758#f0d2c61efb5538d843e0a90128515b2a) | Sets the strength of the mouth shape adjustment filter. |
| [setNoseWingLevel:](https://www.tencentcloud.com/document/product/647/50758#17b9e0789d34ccd780fd271a5bd4cc6d) | Sets the strength of the nose wing narrowing filter. |
| [setNosePositionLevel:](https://www.tencentcloud.com/document/product/647/50758#12fc79a32b974f74a544af7ce164b54a) | Sets the strength of the nose position adjustment filter. |
| [setLipsThicknessLevel:](https://www.tencentcloud.com/document/product/647/50758#bf90775c7125cb53ff972e9fe447a282) | Sets the strength of the lip thickness adjustment filter. |
| [setFaceBeautyLevel:](https://www.tencentcloud.com/document/product/647/50758#4f4731a58b72b8cbc33ad84f4c397de9) | Sets the strength of the face shape adjustment filter. |
| [setMotionTmpl:inDir:](https://www.tencentcloud.com/document/product/647/50758#7f66b71987061e914cdfc9f756d3b762) | Selects the AI animated effect pendant. |
| [setMotionMute:](https://www.tencentcloud.com/document/product/647/50758#3146072ddea1c320588b1a27bc8bff2e) | Sets whether to mute during animated effect playback. |

## Type definitions of audio/video devices

| FuncList | DESC |
| --- | --- |
| [onDeviceChanged:type:state:](https://www.tencentcloud.com/document/product/647/50759#dfd15b3a97c8d91d85618afb47ea252f) | The status of a local device changed (for desktop OS only). |

## Device APIs

| FuncList | DESC |
| --- | --- |
| [isFrontCamera](https://www.tencentcloud.com/document/product/647/50759#6d3ec289d7e2325835e0d1da358103a6) | Querying whether the front camera is being used. |
| [switchCamera:](https://www.tencentcloud.com/document/product/647/50759#a6c41b29145df78c75f83db394a5757d) | Switching to the front/rear camera (for mobile OS). |
| [isCameraZoomSupported](https://www.tencentcloud.com/document/product/647/50759#3d221dfef2379ff2d7465873b190d279) | Querying whether the current camera supports zooming (for mobile OS). |
| [getCameraZoomMaxRatio](https://www.tencentcloud.com/document/product/647/50759#36e2b33316fc8b7a9d4ba089594c77ff) | Getting the maximum zoom ratio of the camera (for mobile OS). |
| [setCameraZoomRatio:](https://www.tencentcloud.com/document/product/647/50759#aa61befc4a161b72e2a3eb9703e8ab8a) | Setting the camera zoom ratio (for mobile OS). |
| [isAutoFocusEnabled](https://www.tencentcloud.com/document/product/647/50759#a8d8a4fa66b628c21a080177204744b2) | Querying whether automatic face detection is supported (for mobile OS). |
| [enableCameraAutoFocus:](https://www.tencentcloud.com/document/product/647/50759#b73d99629f1936b786b6ada790e458dd) | Enabling auto focus (for mobile OS). |
| [setCameraFocusPosition:](https://www.tencentcloud.com/document/product/647/50759#2f2ceca9ad0f46650334e6b5aa813633) | Adjusting the focus (for mobile OS). |
| [isCameraTorchSupported](https://www.tencentcloud.com/document/product/647/50759#0f67ffd852a08dc7735f51d3b3f0f163) | Querying whether flash is supported (for mobile OS). |
| [enableCameraTorch:](https://www.tencentcloud.com/document/product/647/50759#bf86fe99b08324c7114c2da6875baca9) | Enabling/Disabling flash, i.e., the torch mode (for mobile OS). |
| [setAudioRoute:](https://www.tencentcloud.com/document/product/647/50759#669f49baa33336be868377f8bc8e6f32) | Setting the audio route (for mobile OS). |
| [setExposureCompensation:](https://www.tencentcloud.com/document/product/647/50759#da0dea11c433416dc2b20e27937bc92f) | Set the exposure parameters of the camera, ranging from - 1 to 1. |
| [getDevicesList:](https://www.tencentcloud.com/document/product/647/50759#cf4514b579d88cadae56a424baeb110f) | Getting the device list (for desktop OS). |
| [setCurrentDevice:deviceId:](https://www.tencentcloud.com/document/product/647/50759#1c0a01aa96ce0aa6c596c654041fbee6) | Setting the device to use (for desktop OS). |
| [getCurrentDevice:](https://www.tencentcloud.com/document/product/647/50759#c56fd31ac73ceda8a28d9f4bfe834bbd) | Getting the device currently in use (for desktop OS). |
| [setCurrentDeviceVolume:deviceType:](https://www.tencentcloud.com/document/product/647/50759#aefc135c5b1cf942a4d7445274fa2465) | Setting the volume of the current device (for desktop OS). |
| [getCurrentDeviceVolume:](https://www.tencentcloud.com/document/product/647/50759#1fc1b55bc7722cc70a07302e46507467) | Getting the volume of the current device (for desktop OS). |
| [setCurrentDeviceMute:deviceType:](https://www.tencentcloud.com/document/product/647/50759#647a252eb815bae8854023af3717a79f) | Muting the current device (for desktop OS). |
| [getCurrentDeviceMute:](https://www.tencentcloud.com/document/product/647/50759#7b46a3e3052b4b59e685fb8365c3955d) | Querying whether the current device is muted (for desktop OS). |
| [enableFollowingDefaultAudioDevice:enable:](https://www.tencentcloud.com/document/product/647/50759#f1a3e4a48a4a2e81e7d0eee4c9f37bb7) | Set the audio device used by SDK to follow the system default device (for desktop OS). |
| [startCameraDeviceTest:](https://www.tencentcloud.com/document/product/647/50759#e2d8e209071fef8bbf78f16971bae39f) | Starting camera testing (for desktop OS). |
| [stopCameraDeviceTest](https://www.tencentcloud.com/document/product/647/50759#30be4cfa94699be138130c1919b3af68) | Ending camera testing (for desktop OS). |
| [startMicDeviceTest:](https://www.tencentcloud.com/document/product/647/50759#3dce7bfcf95708a5ce69f5ce7baad6f4) | Starting mic testing (for desktop OS). |
| [startMicDeviceTest:playback:](https://www.tencentcloud.com/document/product/647/50759#f4002f97005e59258de6fe5088ae75b8) | Starting mic testing (for desktop OS). |
| [stopMicDeviceTest](https://www.tencentcloud.com/document/product/647/50759#d0adbc1fbeae9620cf4c78d06b24d26e) | Ending mic testing (for desktop OS). |
| [startSpeakerDeviceTest:](https://www.tencentcloud.com/document/product/647/50759#e4ac7cc2a6dbecee30b0b4a9a17ce3b3) | Starting speaker testing (for desktop OS). |
| [stopSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50759#d9f52ca878aa99ec873170b4bc394f11) | Ending speaker testing (for desktop OS). |
| [setObserver:](https://www.tencentcloud.com/document/product/647/50759#e277523e1a2b2426d66ef6fdecae1fb8) | set onDeviceChanged callback (for Mac). |
| [setCameraCapturerParam:](https://www.tencentcloud.com/document/product/647/50759#0d4167b17f3b52529be4b7a04f648a0d) | Set camera acquisition preferences. |

## Disused APIs

| FuncList | DESC |
| --- | --- |
| [setSystemVolumeType:](https://www.tencentcloud.com/document/product/647/50759#632301e178fc664876e5888669368049) | Setting the system volume type (for mobile OS). |


---
*Source: [https://trtc.io/document/35119](https://trtc.io/document/35119)*
