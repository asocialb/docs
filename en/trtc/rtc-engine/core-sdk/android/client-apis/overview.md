# Overview

**API OVERVIEW**

## Create Instance And Event Callback

| FuncList | DESC |
| --- | --- |
| [sharedInstance](https://www.tencentcloud.com/document/product/647/50762#e2bae3658fa025c8bbf64fa9cca4b6a5) | Create TRTCCloud instance (singleton mode). |
| [destroySharedInstance](https://www.tencentcloud.com/document/product/647/50762#61247ee5547195d11e99e12d2443f62b) | Terminate TRTCCloud instance (singleton mode). |
| [addListener](https://www.tencentcloud.com/document/product/647/50762#0fad348ab0a5747c07d1527fdb4683cc) | Add TRTC event callback. |
| [removeListener](https://www.tencentcloud.com/document/product/647/50762#dfb8cd7a7935e2404217253e0774eaa0) | Remove TRTC event callback. |
| [setListenerHandler](https://www.tencentcloud.com/document/product/647/50762#255fa1616f2826edfb5e9508c374f040) | Set the queue that drives the TRTCCloudListener event callback. |

## Room APIs

| FuncList | DESC |
| --- | --- |
| [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) | Enter room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/50762#4651ae2c9ff5aa99442102e0d77a8606) | Exit room. |
| [switchRole](https://www.tencentcloud.com/document/product/647/50762#0a2b76d62a79877c408aa638b61d9b8e) | Switch role. |
| [switchRoom](https://www.tencentcloud.com/document/product/647/50762#fab001093db697fd493494283e992a9f) | Switch room. |
| [ConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50762#d7e553b397dcc62ffbe0456fdbb1c072) | Request cross-room call. |
| [DisconnectOtherRoom](https://www.tencentcloud.com/document/product/647/50762#71e28e2184ffae717c6d768d9f757ad7) | Exit cross-room call. |
| [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/50762#0f8a372a4d0698fd7eac24007ed7a9a9) | Set subscription mode (which must be set before room entry for it to take effect). |
| [createSubCloud](https://www.tencentcloud.com/document/product/647/50762#04003ddc949012d796c8e9e105353b3a) | Create room subinstance (for concurrent multi-room listen/watch). |
| [destroySubCloud](https://www.tencentcloud.com/document/product/647/50762#f03d12f1ac2c1f27e0d76c10dcda39a4) | Terminate room subinstance. |
| [updateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50762#f74725866e0df9e3763df166f1692c88) | Change the upstream capability of the cross-room anchor in the current room. |

## CDN APIs

| FuncList | DESC |
| --- | --- |
| [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4) | Publish a stream. |
| [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#735a40ecbeb18a37348b9dbce0ae8c68) | Modify publishing parameters. |
| [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#ef07e55b75ccb81b9849502f67b07083) | Stop publishing. |

## Video APIs

| FuncList | DESC |
| --- | --- |
| [startLocalPreview](https://www.tencentcloud.com/document/product/647/50762#b1f7334c9de08e2e26545ea4ddfd5507) | Enable the preview image of local camera (mobile). |
| [updateLocalView](https://www.tencentcloud.com/document/product/647/50762#ac03b1641aea9006f369fb38766eee20) | Update the preview image of local camera. |
| [stopLocalPreview](https://www.tencentcloud.com/document/product/647/50762#e379630cda7e794574b00d549b64a815) | Stop camera preview. |
| [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50762#3b9dab7aed0816028e9e593bce4525a9) | Pause/Resume publishing local video stream. |
| [setVideoMuteImage](https://www.tencentcloud.com/document/product/647/50762#91921f49406d5eb2c70a32b3a84f6fa6) | Set placeholder image during local video pause. |
| [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) | Subscribe to remote user's video stream and bind video rendering control. |
| [updateRemoteView](https://www.tencentcloud.com/document/product/647/50762#a0c8dcabf184480ecf8d232aa3f0cb82) | Update remote user's video rendering control. |
| [stopRemoteView](https://www.tencentcloud.com/document/product/647/50762#68b5d6962bc817f4032ce699e71c9556) | Stop subscribing to remote user's video stream and release rendering control. |
| [stopAllRemoteView](https://www.tencentcloud.com/document/product/647/50762#5d9b1929a45db4a7a01d715628e3bbe0) | Stop subscribing to all remote users' video streams and release all rendering resources. |
| [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50762#7931b1f535d9b6f7af27c0f73d1bc3b0) | Pause/Resume subscribing to remote user's video stream. |
| [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/50762#124d79f21fc06c00349eab464fecbf6d) | Pause/Resume subscribing to all remote users' video streams. |
| [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50762#d227231fc6993ebe2f1c332d48f71563) | Set the encoding parameters of video encoder. |
| [setNetworkQosParam](https://www.tencentcloud.com/document/product/647/50762#e348c485bbdbf8db3e7974880a113a6e) | Set network quality control parameters. |
| [setLocalRenderParams](https://www.tencentcloud.com/document/product/647/50762#76357b0efbb14de26221c0c3c4dbb2ff) | Set the rendering parameters of local video image. |
| [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50762#bfce08bf4cac4decd14d800b69d0ee8e) | Set the rendering mode of remote video image. |
| [enableEncSmallVideoStream](https://www.tencentcloud.com/document/product/647/50762#c8decbf786be761073799e48fe807de7) | Enable dual-channel encoding mode with big and small images. |
| [setRemoteVideoStreamType](https://www.tencentcloud.com/document/product/647/50762#e293c11261601d33cd288501e6e7f71f) | Switch the big/small image of specified remote user. |
| [snapshotVideo](https://www.tencentcloud.com/document/product/647/50762#aa3fec7de2d2ab3fe151c3596d9f735e) | Screencapture video. |
| [setPerspectiveCorrectionPoints](https://www.tencentcloud.com/document/product/647/50762#4f90d58dd3131d81acafc174942006f9) | Sets perspective correction coordinate points. |
| [setGravitySensorAdaptiveMode](https://www.tencentcloud.com/document/product/647/50762#bf715558283a53cc0caf10f84997f86d) | Set the adaptation mode of gravity sensing (version 11.7 and above). |

## Audio APIs

| FuncList | DESC |
| --- | --- |
| [startLocalAudio](https://www.tencentcloud.com/document/product/647/50762#a127184d8d223906a5413d9610d6d22d) | Enable local audio capturing and publishing. |
| [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50762#8fafafeb80fe86f9fc0d893c9c35bd4e) | Stop local audio capturing and publishing. |
| [muteLocalAudio](https://www.tencentcloud.com/document/product/647/50762#8f14edc25b55deaceece6e48c8ccdd9b) | Pause/Resume publishing local audio stream. |
| [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/50762#d6800ccf317e0ccecc8ba17e44e59438) | Pause/Resume playing back remote audio stream. |
| [muteAllRemoteAudio](https://www.tencentcloud.com/document/product/647/50762#2f7b99d99dacb0bbd26b0ea4f2a0c066) | Pause/Resume playing back all remote users' audio streams. |
| [setAudioRoute](https://www.tencentcloud.com/document/product/647/50762#d9efd5e0d3c1a26dfb5b9f184cbea929) | Set audio route. |
| [setRemoteAudioVolume](https://www.tencentcloud.com/document/product/647/50762#dbc906d4b03074487cbd71cc4e7ff326) | Set the audio playback volume of remote user. |
| [setAudioCaptureVolume](https://www.tencentcloud.com/document/product/647/50762#8326d139f429c00b542151923d12d579) | Set the capturing volume of local audio. |
| [getAudioCaptureVolume](https://www.tencentcloud.com/document/product/647/50762#2d920084bbca50226a4e23db7178838c) | Get the capturing volume of local audio. |
| [setAudioPlayoutVolume](https://www.tencentcloud.com/document/product/647/50762#43a82fe566327b25f73fcf509ec3fbcc) | Set the playback volume of remote audio. |
| [getAudioPlayoutVolume](https://www.tencentcloud.com/document/product/647/50762#3563829d921079d4da7207263302f8d4) | Get the playback volume of remote audio. |
| [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50762#a4342e2f3b540f5ecad64bbacb738787) | Enable volume reminder. |
| [startAudioRecording](https://www.tencentcloud.com/document/product/647/50762#413476ab4159de3f7444f7c86d594f50) | Start audio recording. |
| [stopAudioRecording](https://www.tencentcloud.com/document/product/647/50762#f3578857a142a30508f670a6c50683db) | Stop audio recording. |
| [startLocalRecording](https://www.tencentcloud.com/document/product/647/50762#0107285c499b0f9a3cf30c34ef5199c8) | Start local media recording. |
| [stopLocalRecording](https://www.tencentcloud.com/document/product/647/50762#a1236129ca8f62c01939c1882f184a88) | Stop local media recording. |
| [setRemoteAudioParallelParams](https://www.tencentcloud.com/document/product/647/50762#57763e4d399a46da481a3ebda4f46ae4) | Set the parallel strategy of remote audio streams. |
| [enable3DSpatialAudioEffect](https://www.tencentcloud.com/document/product/647/50762#6ccdbf0c4accea85822b243df90754f0) | Enable 3D spatial effect. |
| [updateSelf3DSpatialPosition](https://www.tencentcloud.com/document/product/647/50762#fddf5f6f662981c8ba5f24e409bf94d0) | Update self position and orientation for 3D spatial effect. |
| [updateRemote3DSpatialPosition](https://www.tencentcloud.com/document/product/647/50762#10c92d62c3f477cb179f1bcf249332d8) | Update the specified remote user's position for 3D spatial effect. |
| [set3DSpatialReceivingRange](https://www.tencentcloud.com/document/product/647/50762#67e1291d3f9781b94d4a9234e2680d05) | Set the maximum 3D spatial attenuation range for userId's audio stream. |

## Device management APIs

| FuncList | DESC |
| --- | --- |
| [getDeviceManager](https://www.tencentcloud.com/document/product/647/50762#a860af35dc6cbd03a87871c47a0f9bff) | Get device management class (TXDeviceManager). |

## Beauty filter and watermark APIs

| FuncList | DESC |
| --- | --- |
| [getBeautyManager](https://www.tencentcloud.com/document/product/647/50762#a63717cd7f21b8d14a095345d5067e8b) | Get beauty filter management class (TXBeautyManager). |
| [setWatermark](https://www.tencentcloud.com/document/product/647/50762#22c51c50a68a560cd03fadb43ef21092) | Add watermark. |

## Background music and sound effect APIs

| FuncList | DESC |
| --- | --- |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/50762#4c0541b3fc6023e5e3c5a57d7cacea53) | Get sound effect management class (TXAudioEffectManager). |
| [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50762#e50d6c1b86145e690e50c3cf64afcfb8) | Enable system audio capturing. |
| [stopSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50762#a542a2b1c0a06558e5ee453811395fca) | Stop system audio capturing(iOS not supported). |

## Screen sharing APIs

| FuncList | DESC |
| --- | --- |
| [startScreenCapture](https://www.tencentcloud.com/document/product/647/50762#9b55d2e9cd4e32eae74a9eb3555f6c8b) | Start screen sharing. |
| [stopScreenCapture](https://www.tencentcloud.com/document/product/647/50762#2a667ba75e08183bd5f764374a6de7ba) | Stop screen sharing. |
| [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/50762#d7f9ad7b108c98e919f5f1cca757e72d) | Pause screen sharing. |
| [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/50762#1924263011bb92fba1642ad3e139629f) | Resume screen sharing. |
| [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50762#ae8dee3c3444ccd1450021b8f2cc5d4e) | Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems). |

## Custom capturing and rendering APIs

| FuncList | DESC |
| --- | --- |
| [enableCustomVideoCapture](https://www.tencentcloud.com/document/product/647/50762#104e33c28cf5092a051adcd75aaf725c) | Enable/Disable custom video capturing mode. |
| [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50762#1ff9dbb21f79dea11b0ed338a4922261) | Deliver captured video frames to SDK. |
| [enableCustomAudioCapture](https://www.tencentcloud.com/document/product/647/50762#61e36718fdbd819a429d43c2f7bddc0e) | Enable custom audio capturing mode. |
| [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50762#ec667f2a4e28f7cd0932bb25f04bd498) | Deliver captured audio data to SDK. |
| [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50762#50d27eb1a03e5d65b1ba93b81763ff06) | Enable/Disable custom audio track. |
| [mixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50762#63bd66a5a1cbb589159ed3bdcf8d9588) | Mix custom audio track into SDK. |
| [setMixExternalAudioVolume](https://www.tencentcloud.com/document/product/647/50762#a4471e339cba10a9b333d6faa95edfec) | Set the publish volume and playback volume of mixed custom audio track. |
| [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50762#ca8ae7330112c5ceb7b65e1eb6b80a9b) | Generate custom capturing timestamp. |
| [setLocalVideoProcessListener](https://www.tencentcloud.com/document/product/647/50762#714daaa9eb9a8b4a05dd5db8ed862815) | Set video data callback for third-party beauty filters. |
| [setLocalVideoRenderListener](https://www.tencentcloud.com/document/product/647/50762#316393403d659ec96c082f459eb769a5) | Set the callback of custom rendering for local video. |
| [setRemoteVideoRenderListener](https://www.tencentcloud.com/document/product/647/50762#5eead22eedd090f9c32205e596a8ef6d) | Set the callback of custom rendering for remote video. |
| [setAudioFrameListener](https://www.tencentcloud.com/document/product/647/50762#4b21f659ddf9cc2dfd8477e16a432c69) | Set custom audio data callback. |
| [setCapturedAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50762#ef7e9820c2580b9b6d754a408a438ff7) | Set the callback format of audio frames captured by local mic. |
| [setLocalProcessedAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50762#f2ad5b8dda79c6302cb93a1d2e2bacea) | Set the callback format of preprocessed local audio frames. |
| [setMixedPlayAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50762#9a3eac5ba2a1c1debe4ebfb946ea6108) | Set the callback format of audio frames to be played back by system. |
| [enableCustomAudioRendering](https://www.tencentcloud.com/document/product/647/50762#ae84ad6beb1326386dfde33ece5e4ed1) | Enabling custom audio playback. |
| [getCustomAudioRenderingFrame](https://www.tencentcloud.com/document/product/647/50762#f42f7c81832111bd55e15cffc5e0ce7a) | Getting playable audio data. |

## Custom message sending APIs

| FuncList | DESC |
| --- | --- |
| [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50762#9649cfc709c73d6dbb4df75bbc798fab) | Use UDP channel to send custom message to all users in room. |
| [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50762#52a919f9f3a990ebd08679bd47aa69bb) | Use SEI channel to send custom message to all users in room. |

## Network test APIs

| FuncList | DESC |
| --- | --- |
| [startSpeedTest](https://www.tencentcloud.com/document/product/647/50762#ebfdd762ef3bab9136d8ca683892294b) | Start network speed test (used before room entry). |
| [stopSpeedTest](https://www.tencentcloud.com/document/product/647/50762#300e5f71dde3917dc5e057f9e1f6e014) | Stop network speed test. |

## Debugging APIs

| FuncList | DESC |
| --- | --- |
| [getSDKVersion](https://www.tencentcloud.com/document/product/647/50762#931c5ef5098a8b7cf4c2988104ac9e89) | Get SDK version information. |
| [setLogLevel](https://www.tencentcloud.com/document/product/647/50762#ded8d5d4a8c7531405e1915c646a3132) | Set log output level. |
| [setConsoleEnabled](https://www.tencentcloud.com/document/product/647/50762#7173269cfd715b2730be7aab261d647c) | Enable/Disable console log printing. |
| [setLogCompressEnabled](https://www.tencentcloud.com/document/product/647/50762#67d4f29628d27e97edab41b15770c91b) | Enable/Disable local log compression. |
| [setLogDirPath](https://www.tencentcloud.com/document/product/647/50762#770e9da3f6780da61505e784e3ba0df2) | Set local log storage path. |
| [setLogListener](https://www.tencentcloud.com/document/product/647/50762#8cde741f40653e7780b88d6607c210fb) | Set log callback. |
| [showDebugView](https://www.tencentcloud.com/document/product/647/50762#b821f814c735a081b1de0398d23a42b1) | Display dashboard. |
| [TRTCViewMargin](https://www.tencentcloud.com/document/product/647/50762#803bd588c0708af97010b59052e669db) | Set dashboard margin. |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/50762#c6c3457a98b055087f5811b88b663ad7) | Call experimental APIs. |

## Encrypted interface

| FuncList | DESC |
| --- | --- |
| [enablePayloadPrivateEncryption](https://www.tencentcloud.com/document/product/647/50762#81ba4cf3583c7bd43cf3496d3001e6a1) | Enable or disable private encryption of media streams. |

## Error and warning events

| FuncList | DESC |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/50763#a210036518497eee3f50b3e0738476fd) | Error event callback. |
| [onWarning](https://www.tencentcloud.com/document/product/647/50763#b325c0a398a4c9666a3d66a312163bae) | Warning event callback. |

## Room event callback

| FuncList | DESC |
| --- | --- |
| [onEnterRoom](https://www.tencentcloud.com/document/product/647/50763#00a62e5b89b24bcac09ce0bdc5cb0da7) | Whether room entry is successful. |
| [onExitRoom](https://www.tencentcloud.com/document/product/647/50763#41db48ab552c935ba865dc86eeb5b9d0) | Room exit. |
| [onSwitchRole](https://www.tencentcloud.com/document/product/647/50763#64c825f856ed30751fb936ee640ce478) | Role switching. |
| [onSwitchRoom](https://www.tencentcloud.com/document/product/647/50763#259a9711a076b472dc07e5d12b6cb533) | Result of room switching. |
| [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50763#bb05cf36cc9a461e0b45ae825ee5e2e0) | Result of requesting cross-room call. |
| [onDisConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50763#162e6a6e08df62dbb8ad7e2457228211) | Result of ending cross-room call. |
| [onUpdateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50763#0841e8dd52bc5ca16cb1f5154ce3b75b) | Result of changing the upstream capability of the cross-room anchor. |

## User event callback.

| FuncList | DESC |
| --- | --- |
| [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/50763#a5bd4299b42d86c93067c2b8f581e959) | A user entered the room. |
| [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/50763#1fdebb79d1eff714ad27835bf083b075) | A user exited the room. |
| [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/50763#448623ba3ddafa44cdb425bea100c2d8) | A remote user published/unpublished primary stream video. |
| [onUserSubStreamAvailable](https://www.tencentcloud.com/document/product/647/50763#d017527d1cf1495be47ce48057d76f01) | A remote user published/unpublished substream video. |
| [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50763#cb979bbb36c24acc891ce2115ff2b6c6) | A remote user published/unpublished audio. |
| [onFirstVideoFrame](https://www.tencentcloud.com/document/product/647/50763#a11a508ae7b71797961235888ddc2770) | The SDK started rendering the first video frame of the local or a remote user. |
| [onFirstAudioFrame](https://www.tencentcloud.com/document/product/647/50763#2431efb28ed2592b0852b05b014e72ae) | The SDK started playing the first audio frame of a remote user. |
| [onSendFirstLocalVideoFrame](https://www.tencentcloud.com/document/product/647/50763#601283fbd3d366fbe3fcbe4aa95d020a) | The first local video frame was published. |
| [onSendFirstLocalAudioFrame](https://www.tencentcloud.com/document/product/647/50763#f5f5c12cda23f75553cf01b05b0234bd) | The first local audio frame was published. |
| [onRemoteVideoStatusUpdated](https://www.tencentcloud.com/document/product/647/50763#a1ae5e4972a8d710daa1788c0cf979f9) | Change of remote video status. |
| [onRemoteAudioStatusUpdated](https://www.tencentcloud.com/document/product/647/50763#ed977ff550b75caf7dcbc40b4c155fba) | Change of remote audio status. |
| [onUserVideoSizeChanged](https://www.tencentcloud.com/document/product/647/50763#dd52bb555d46c27a29fc118d0b3e58fe) | Change of remote video size. |

## Callback of statistics on network and technical metrics.

| FuncList | DESC |
| --- | --- |
| [onNetworkQuality](https://www.tencentcloud.com/document/product/647/50763#5220c567251698e35a0aae0bd50d4cd1) | Real-time network quality statistics. |
| [onStatistics](https://www.tencentcloud.com/document/product/647/50763#faca91305f246db336cb6c56f7bfbf25) | Real-time statistics on technical metrics. |
| [onSpeedTestResult](https://www.tencentcloud.com/document/product/647/50763#daf3b15c9f1bd505ee8e2600cc27f49b) | Callback of network speed test. |

## Callback of connection to the cloud

| FuncList | DESC |
| --- | --- |
| [onConnectionLost](https://www.tencentcloud.com/document/product/647/50763#ffc0f58daed671ee4efca27b54deca45) | The SDK was disconnected from the cloud. |
| [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50763#fd6b9c3956e35b67413fe7c7938ca5de) | The SDK is reconnecting to the cloud. |
| [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50763#85a1f134a3fb0d0b6903c1a42797a604) | The SDK is reconnected to the cloud. |

## Callback of hardware events

| FuncList | DESC |
| --- | --- |
| [onCameraDidReady](https://www.tencentcloud.com/document/product/647/50763#a2166e1dc3a1cfcf71c08e5de6056abe) | The camera is ready. |
| [onMicDidReady](https://www.tencentcloud.com/document/product/647/50763#afe1886bee9081dd93357591ea190897) | The mic is ready. |
| [onAudioRouteChanged](https://www.tencentcloud.com/document/product/647/50763#388f09037008693f6531d93db090d9d7) | The audio route changed (for mobile devices only). |
| [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/50763#2ec23470e2480bd26d91353c0998d019) | Volume. |

## Callback of the receipt of a custom message.

| FuncList | DESC |
| --- | --- |
| [onRecvCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50763#fa42648c207d482ed4124f99100823fc) | Receipt of custom message. |
| [onMissCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50763#44459f158ee25b624f3f067824485bcb) | Loss of custom message. |
| [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/50763#825b49ace1d64ee095ab1f2014529738) | Receipt of SEI message. |

## CDN event callback

| FuncList | DESC |
| --- | --- |
| [onStartPublishing](https://www.tencentcloud.com/document/product/647/50763#c0e748fa851bec48a82d42e27f0c1bd9) | Started publishing to Tencent Cloud CSS CDN. |
| [onStopPublishing](https://www.tencentcloud.com/document/product/647/50763#2c41f3b6cc5622fc3654b701ccb71c96) | Stopped publishing to Tencent Cloud CSS CDN. |
| [onStartPublishCDNStream](https://www.tencentcloud.com/document/product/647/50763#43ddc92c2362dd8662c17d776a90ecd4) | Started publishing to non-Tencent Cloudâs live streaming CDN. |
| [onStopPublishCDNStream](https://www.tencentcloud.com/document/product/647/50763#81c40c1ae4aae815191a1d236ccc7840) | Stopped publishing to non-Tencent Cloudâs live streaming CDN. |
| [onSetMixTranscodingConfig](https://www.tencentcloud.com/document/product/647/50763#353a7d9b80cda90f70916d67652e8097) | Set the layout and transcoding parameters for On-Cloud MixTranscoding. |
| [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#95cedc06908dda47f4459b30961764a4) | Callback for starting to publish. |
| [onUpdatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#7d8052ed48b758cbdf0fb4d90e8b68f0) | Callback for modifying publishing parameters. |
| [onStopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#52edf2fdf62fb3be10c20e6c33fd9169) | Callback for stopping publishing. |
| [onCdnStreamStateChanged](https://www.tencentcloud.com/document/product/647/50763#2e8c5883ed22424a1424f1b256cdc76d) | Callback for change of RTMP/RTMPS publishing status. |

## Screen sharing event callback

| FuncList | DESC |
| --- | --- |
| [onScreenCaptureStarted](https://www.tencentcloud.com/document/product/647/50763#b8df6d78ecc8f8c7ee36545c5c390ba0) | Screen sharing started. |
| [onScreenCapturePaused](https://www.tencentcloud.com/document/product/647/50763#a1382f12b655dc8b374aec24d67f58d1) | Screen sharing was paused. |
| [onScreenCaptureResumed](https://www.tencentcloud.com/document/product/647/50763#e10e68d5858a269200d5fdbc6d9e348a) | Screen sharing was resumed. |
| [onScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/50763#128e1720d2db631bf47bfd9ac2671705) | Screen sharing stopped. |

## Callback of local recording and screenshot events

| FuncList | DESC |
| --- | --- |
| [onLocalRecordBegin](https://www.tencentcloud.com/document/product/647/50763#4483cc99d86553aefe9f975c69c52d44) | Local recording started. |
| [onLocalRecording](https://www.tencentcloud.com/document/product/647/50763#62d4da4491e58833757e9117d3af70c5) | Local media is being recorded. |
| [onLocalRecordFragment](https://www.tencentcloud.com/document/product/647/50763#707cf5564bb9b16e891a45295e5f916d) | Record fragment finished. |
| [onLocalRecordComplete](https://www.tencentcloud.com/document/product/647/50763#34d5a7ab0dd7566631a7dd3a35582a3e) | Local recording stopped. |
| [onSnapshotComplete](https://www.tencentcloud.com/document/product/647/50763#2178e76eaae55ba207a82453e595b1f7) | Finished taking a local screenshot. |

## Disused callbacks

| FuncList | DESC |
| --- | --- |
| [onUserEnter](https://www.tencentcloud.com/document/product/647/50763#7fce6d0cdcd7d553eaa53f37b636cec7) | An anchor entered the room (disused). |
| [onUserExit](https://www.tencentcloud.com/document/product/647/50763#9f4a171973a5d322f937aefebaeeb7b8) | An anchor left the room (disused). |
| [onAudioEffectFinished](https://www.tencentcloud.com/document/product/647/50763#fdb499d0bd647201078dad545ff605eb) | Audio effects ended (disused). |
| [onSpeedTest](https://www.tencentcloud.com/document/product/647/50763#a585f7bcab66ec6c5b4709aa27f98844) | Result of server speed testing (disused). |

## Callback of custom video processing

| FuncList | DESC |
| --- | --- |
| [onRenderVideoFrame](https://www.tencentcloud.com/document/product/647/50763#5be091bd1a65e342c86407f252b0d5e2) | Custom video rendering. |
| [onGLContextCreated](https://www.tencentcloud.com/document/product/647/50763#e9cdbfe822913f9cef0f8356858a9505) | An OpenGL context was created in the SDK. |
| [onProcessVideoFrame](https://www.tencentcloud.com/document/product/647/50763#ca7517167849fe21e3fc21c678b8b427) | Video processing by third-party beauty filters. |
| [onGLContextDestory](https://www.tencentcloud.com/document/product/647/50763#2a0ea0c174a3231091f2097077a60da9) | The OpenGL context in the SDK was destroyed. |

## Callback of custom audio processing

| FuncList | DESC |
| --- | --- |
| [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#b02cc5237a701b6ea1a7b5f99aad625c) | Audio data captured by the local mic and pre-processed by the audio module. |
| [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#d481858c6d71a2accc18a96f59e8db6c) | Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed. |
| [onRemoteUserAudioFrame](https://www.tencentcloud.com/document/product/647/50763#e244077b85f3b7659e10fd7a916e5ccd) | Audio data of each remote user before audio mixing. |
| [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50763#544fc0be68d0c91599e4e94046ea7ef9) | Data mixed from each channel before being submitted to the system for playback. |
| [onMixedAllAudioFrame](https://www.tencentcloud.com/document/product/647/50763#acc0351ba4a069cc57489de536e94b89) | Data mixed from all the captured and to-be-played audio in the SDK. |
| [onVoiceEarMonitorAudioFrame](https://www.tencentcloud.com/document/product/647/50763#0293bff9b393f05d4d44c6fc4be7d59b) | In-ear monitoring data. |

## Other event callbacks

| FuncList | DESC |
| --- | --- |
| [onLog](https://www.tencentcloud.com/document/product/647/50763#bfb112052d1af03d29bf03dde9f7a38e) | Printing of local log. |

## Background music preload event callback

| FuncList | DESC |
| --- | --- |
| [onLoadProgress](https://www.tencentcloud.com/document/product/647/50765#072926b93551b1af8dbb1fbb3d087004) | Background music preload progress. |
| [onLoadError](https://www.tencentcloud.com/document/product/647/50765#f3989bff41bf5801b07d181cc72845ec) | Background music preload error. |

## Callback of playing background music

| FuncList | DESC |
| --- | --- |
| [onStart](https://www.tencentcloud.com/document/product/647/50765#8a783933a586aee9a5302b57740b11ea) | Background music started. |
| [onPlayProgress](https://www.tencentcloud.com/document/product/647/50765#75e96d61252e138c16469318e54e86a3) | Playback progress of background music. |
| [onComplete](https://www.tencentcloud.com/document/product/647/50765#2e16ac103491244a957557a26325b408) | Background music ended. |

## Voice effect APIs

| FuncList | DESC |
| --- | --- |
| [enableVoiceEarMonitor](https://www.tencentcloud.com/document/product/647/50765#889cc3da70a6c0820633bc197ed2b2a3) | Enabling in-ear monitoring. |
| [setVoiceEarMonitorVolume](https://www.tencentcloud.com/document/product/647/50765#7d600f2108d854b2b3230304156058f0) | Setting in-ear monitoring volume. |
| [setVoiceReverbType](https://www.tencentcloud.com/document/product/647/50765#56f1d6a2079ce56b75781a4ffcf5347a) | Setting voice reverb effects. |
| [setVoiceChangerType](https://www.tencentcloud.com/document/product/647/50765#407622eca1ec0c089ac0db6a699f11fa) | Setting voice changing effects. |
| [setVoiceCaptureVolume](https://www.tencentcloud.com/document/product/647/50765#c881a67177f8396b70c2abf117036381) | Setting speech volume. |
| [setVoicePitch](https://www.tencentcloud.com/document/product/647/50765#fd4b19b0a1bc40aa8e8dc8070d96a68f) | Setting speech pitch. |

## Background music APIs

| FuncList | DESC |
| --- | --- |
| [setMusicObserver](https://www.tencentcloud.com/document/product/647/50765#fc6d76f7ebe087957ba81a5ee62710b0) | Setting the background music callback. |
| [startPlayMusic](https://www.tencentcloud.com/document/product/647/50765#e7b176192e2cf33abe2bd18618ad6bc1) | Starting background music. |
| [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50765#35e1e5bd5b10eb63b6313fd95b95580b) | Stopping background music. |
| [pausePlayMusic](https://www.tencentcloud.com/document/product/647/50765#2ee1a37638877d7041493a7ce1402077) | Pausing background music. |
| [resumePlayMusic](https://www.tencentcloud.com/document/product/647/50765#dfcbb473c7ddfe6b0028e1d318ed8ff3) | Resuming background music. |
| [setAllMusicVolume](https://www.tencentcloud.com/document/product/647/50765#01e8b8f4cb30d56b50e931c2857d7754) | Setting the local and remote playback volume of background music. |
| [setMusicPublishVolume](https://www.tencentcloud.com/document/product/647/50765#fc3c4bf5f3c047d05371ddd6c8aa87d9) | Setting the remote playback volume of a specific music track. |
| [setMusicPlayoutVolume](https://www.tencentcloud.com/document/product/647/50765#d8911047524dead67735746adff09354) | Setting the local playback volume of a specific music track. |
| [setMusicPitch](https://www.tencentcloud.com/document/product/647/50765#c7f57592b0cbdc16bbac71310ebc88ae) | Adjusting the pitch of background music. |
| [setMusicSpeedRate](https://www.tencentcloud.com/document/product/647/50765#5245a320dc95f7031cf39fd21d80248e) | Changing the speed of background music. |
| [getMusicCurrentPosInMS](https://www.tencentcloud.com/document/product/647/50765#a3c50caad27c04e3f8c5535d4c669ffd) | Getting the playback progress (ms) of background music. |
| [getMusicDurationInMS](https://www.tencentcloud.com/document/product/647/50765#db1e65508258187a248abf436025f126) | Getting the total length (ms) of background music. |
| [seekMusicToPosInMS](https://www.tencentcloud.com/document/product/647/50765#505db77305b5d4ede7f93fcb4a79b1b5) | Setting the playback progress (ms) of background music. |
| [setMusicScratchSpeedRate](https://www.tencentcloud.com/document/product/647/50765#b0c8a792d1e8bab154063728086ad4db) | Adjust the speed change effect of the scratch disc. |
| [setPreloadObserver](https://www.tencentcloud.com/document/product/647/50765#6fee9439865a630a0e77991be80f0ab6) | Setting music preload callback. |
| [preloadMusic](https://www.tencentcloud.com/document/product/647/50765#9d6d01a8519d56c348853f2f2467d537) | Preload background music. |
| [getMusicTrackCount](https://www.tencentcloud.com/document/product/647/50765#30d19d232faa06d74b16bc04032fc9b4) | Get the number of tracks of background music. |
| [setMusicTrack](https://www.tencentcloud.com/document/product/647/50765#8dc4b355cd2af90de761cec9b9057937) | Specify the playback track of background music. |

## beauty interface

| FuncList | DESC |
| --- | --- |
| [setBeautyStyle](https://www.tencentcloud.com/document/product/647/50766#d3fdd4986152f2b9418bef94aaa62575) | Sets the beauty (skin smoothing) filter algorithm. |
| [setBeautyLevel](https://www.tencentcloud.com/document/product/647/50766#0f1ab9f5e3c2150d3b7acc043636993b) | Sets the strength of the beauty filter. |
| [setWhitenessLevel](https://www.tencentcloud.com/document/product/647/50766#4156425a7c70c41fd9eb92b0afead869) | Sets the strength of the brightening filter. |
| [enableSharpnessEnhancement](https://www.tencentcloud.com/document/product/647/50766#3fdef66469d194422353bbdd1582b116) | Enables clarity enhancement. |
| [setRuddyLevel](https://www.tencentcloud.com/document/product/647/50766#e910671c2d434f192746135b222b1f26) | Sets the strength of the rosy skin filter. |
| [setFilter](https://www.tencentcloud.com/document/product/647/50766#b68995a74e5e1f8a74d1d601002df436) | Sets color filter. |
| [setFilterStrength](https://www.tencentcloud.com/document/product/647/50766#67fa5ec3f6ad3e6ee221a2419f5fbf1c) | Sets the strength of color filter. |
| [setGreenScreenFile](https://www.tencentcloud.com/document/product/647/50766#cc40b48dfcfca3652eb1b14d1951cb03) | Sets green screen video. |
| [setEyeScaleLevel](https://www.tencentcloud.com/document/product/647/50766#499ecdc88602c0180a2e429a43f6479c) | Sets the strength of the eye enlarging filter. |
| [setFaceSlimLevel](https://www.tencentcloud.com/document/product/647/50766#1541edd89ed993dc95cccc1ad7da2096) | Sets the strength of the face slimming filter. |
| [setFaceVLevel](https://www.tencentcloud.com/document/product/647/50766#db51c69a28d817bc0e9887a3031ea418) | Sets the strength of the chin slimming filter. |
| [setChinLevel](https://www.tencentcloud.com/document/product/647/50766#24a531bdfa6c2cac251cebbcbe33bf9e) | Sets the strength of the chin lengthening/shortening filter. |
| [setFaceShortLevel](https://www.tencentcloud.com/document/product/647/50766#7a74136e5fdb9113c55b38ac5fb68ad0) | Sets the strength of the face shortening filter. |
| [setFaceNarrowLevel](https://www.tencentcloud.com/document/product/647/50766#355fd6987714bf4f1e77e3692d71ce1c) | Sets the strength of the face narrowing filter. |
| [setNoseSlimLevel](https://www.tencentcloud.com/document/product/647/50766#e91f334ff8acdc7a0ada260f1ec9af7a) | Sets the strength of the nose slimming filter. |
| [setEyeLightenLevel](https://www.tencentcloud.com/document/product/647/50766#98bfa71c0efce410fcad9a54e71cd23c) | Sets the strength of the eye brightening filter. |
| [setToothWhitenLevel](https://www.tencentcloud.com/document/product/647/50766#46fa131a69e36b2c53fea50ccbedb5ca) | Sets the strength of the teeth whitening filter. |
| [setWrinkleRemoveLevel](https://www.tencentcloud.com/document/product/647/50766#ae65bfc2413b2e30e5c4d415edea8dc1) | Sets the strength of the wrinkle removal filter. |
| [setPounchRemoveLevel](https://www.tencentcloud.com/document/product/647/50766#7eb3906cc8d8c824f51245648c1ad314) | Sets the strength of the eye bag removal filter. |
| [setSmileLinesRemoveLevel](https://www.tencentcloud.com/document/product/647/50766#35faeed6286e030cc373206171860792) | Sets the strength of the smile line removal filter. |
| [setForeheadLevel](https://www.tencentcloud.com/document/product/647/50766#6fff839e209eca06c177c3a6b52e1322) | Sets the strength of the hairline adjustment filter. |
| [setEyeDistanceLevel](https://www.tencentcloud.com/document/product/647/50766#af54d76bb28ae3482a5c6c35fb500cbf) | Sets the strength of the eye distance adjustment filter. |
| [setEyeAngleLevel](https://www.tencentcloud.com/document/product/647/50766#fa64d8156a269b767701f84f93a83f5e) | Sets the strength of the eye corner adjustment filter. |
| [setMouthShapeLevel](https://www.tencentcloud.com/document/product/647/50766#f8548ba279ca3a3a726597dabf5d48ee) | Sets the strength of the mouth shape adjustment filter. |
| [setNoseWingLevel](https://www.tencentcloud.com/document/product/647/50766#c2cd7b9bd4a3079e419628af9f1c7da2) | Sets the strength of the nose wing narrowing filter. |
| [setNosePositionLevel](https://www.tencentcloud.com/document/product/647/50766#7fa2f6542f50b66d7831ce876655502d) | Sets the strength of the nose position adjustment filter. |
| [setLipsThicknessLevel](https://www.tencentcloud.com/document/product/647/50766#20ba318ec854b3cac9f975cf79791edf) | Sets the strength of the lip thickness adjustment filter. |
| [setFaceBeautyLevel](https://www.tencentcloud.com/document/product/647/50766#1f320ba994f61fab04b195796d7dc6ad) | Sets the strength of the face shape adjustment filter. |
| [setMotionTmpl](https://www.tencentcloud.com/document/product/647/50766#be3f0f9f80456be2a2e9c598f3164bc5) | Selects the AI animated effect pendant. |
| [setMotionMute](https://www.tencentcloud.com/document/product/647/50766#b249750633c498650d73c15902de468e) | Sets whether to mute during animated effect playback. |

## Device APIs

| FuncList | DESC |
| --- | --- |
| [isFrontCamera](https://www.tencentcloud.com/document/product/647/50767#71820ed8e774434ec01d6dc6a44dfe3d) | Querying whether the front camera is being used. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/50767#98743c4b46e3baea8308a8e27cf44c8a) | Switching to the front/rear camera (for mobile OS). |
| [getCameraZoomMaxRatio](https://www.tencentcloud.com/document/product/647/50767#c792f2cefe9b867591a00071f673da52) | Getting the maximum zoom ratio of the camera (for mobile OS). |
| [setCameraZoomRatio](https://www.tencentcloud.com/document/product/647/50767#de6f0bc85a439308d2bca3f5a338e3f7) | Setting the camera zoom ratio (for mobile OS). |
| [isAutoFocusEnabled](https://www.tencentcloud.com/document/product/647/50767#f3c9fb1db152e2ef198256dcf992fc30) | Querying whether automatic face detection is supported (for mobile OS). |
| [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/50767#5bb9ad6ffa0c173d8864188d143a6332) | Enabling auto focus (for mobile OS). |
| [setCameraFocusPosition](https://www.tencentcloud.com/document/product/647/50767#c50deb76ecaed735d7a7571ae9e1e719) | Adjusting the focus (for mobile OS). |
| [enableCameraTorch](https://www.tencentcloud.com/document/product/647/50767#b71d15b7be8cd6fa6f4cf6435d7548be) | Enabling/Disabling flash, i.e., the torch mode (for mobile OS). |
| [setAudioRoute](https://www.tencentcloud.com/document/product/647/50767#bd5eb5475f6b3cf2e2881fe4c4dee818) | Setting the audio route (for mobile OS). |
| [setExposureCompensation](https://www.tencentcloud.com/document/product/647/50767#260167d6608887a70694ee2983fefc10) | Set the exposure parameters of the camera, ranging from - 1 to 1. |
| [setCameraCapturerParam](https://www.tencentcloud.com/document/product/647/50767#3a720bdf065f7984d709180bdd28cd02) | Set camera acquisition preferences. |

## Disused APIs

| FuncList | DESC |
| --- | --- |
| [setSystemVolumeType](https://www.tencentcloud.com/document/product/647/50767#d4219ee8b3e722282cd8e564f79d4cd8) | Setting the system volume type (for mobile OS). |


---
*Source: [https://trtc.io/document/35125](https://trtc.io/document/35125)*
