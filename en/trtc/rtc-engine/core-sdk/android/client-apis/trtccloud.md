# TRTCCloud

Copyright (c) 2021 Tencent. All rights reserved.

Module:   TRTCCloud @ TXLiteAVSDK

Function: TRTC's main feature API

Version: 13.0

**TRTCCloud**

## TRTCCloud

| FuncList | DESC |
| --- | --- |
| [sharedInstance](https://www.tencentcloud.com/document/product/647/50762#e2bae3658fa025c8bbf64fa9cca4b6a5) | Create TRTCCloud instance (singleton mode). |
| [destroySharedInstance](https://www.tencentcloud.com/document/product/647/50762#61247ee5547195d11e99e12d2443f62b) | Terminate TRTCCloud instance (singleton mode). |
| [addListener](https://www.tencentcloud.com/document/product/647/50762#0fad348ab0a5747c07d1527fdb4683cc) | Add TRTC event callback. |
| [removeListener](https://www.tencentcloud.com/document/product/647/50762#dfb8cd7a7935e2404217253e0774eaa0) | Remove TRTC event callback. |
| [setListenerHandler](https://www.tencentcloud.com/document/product/647/50762#255fa1616f2826edfb5e9508c374f040) | Set the queue that drives the TRTCCloudListener event callback. |
| [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) | Enter room. |
| [exitRoom](https://www.tencentcloud.com/document/product/647/50762#4651ae2c9ff5aa99442102e0d77a8606) | Exit room. |
| [switchRole](https://www.tencentcloud.com/document/product/647/50762#0a2b76d62a79877c408aa638b61d9b8e) | Switch role. |
| [switchRole](https://www.tencentcloud.com/document/product/647/50762#c78a86f0f8ca1b5a7a2b4e876cf43589) | Switch role(support permission credential). |
| [switchRoom](https://www.tencentcloud.com/document/product/647/50762#fab001093db697fd493494283e992a9f) | Switch room. |
| [ConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50762#d7e553b397dcc62ffbe0456fdbb1c072) | Request cross-room call. |
| [DisconnectOtherRoom](https://www.tencentcloud.com/document/product/647/50762#71e28e2184ffae717c6d768d9f757ad7) | Exit cross-room call. |
| [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/50762#0f8a372a4d0698fd7eac24007ed7a9a9) | Set subscription mode (which must be set before room entry for it to take effect). |
| [createSubCloud](https://www.tencentcloud.com/document/product/647/50762#04003ddc949012d796c8e9e105353b3a) | Create room subinstance (for concurrent multi-room listen/watch). |
| [destroySubCloud](https://www.tencentcloud.com/document/product/647/50762#f03d12f1ac2c1f27e0d76c10dcda39a4) | Terminate room subinstance. |
| [updateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50762#f74725866e0df9e3763df166f1692c88) | Change the upstream capability of the cross-room anchor in the current room. |
| [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4) | Publish a stream. |
| [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#735a40ecbeb18a37348b9dbce0ae8c68) | Modify publishing parameters. |
| [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#ef07e55b75ccb81b9849502f67b07083) | Stop publishing. |
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
| [getDeviceManager](https://www.tencentcloud.com/document/product/647/50762#a860af35dc6cbd03a87871c47a0f9bff) | Get device management class (TXDeviceManager). |
| [getBeautyManager](https://www.tencentcloud.com/document/product/647/50762#a63717cd7f21b8d14a095345d5067e8b) | Get beauty filter management class (TXBeautyManager). |
| [setWatermark](https://www.tencentcloud.com/document/product/647/50762#22c51c50a68a560cd03fadb43ef21092) | Add watermark. |
| [getAudioEffectManager](https://www.tencentcloud.com/document/product/647/50762#4c0541b3fc6023e5e3c5a57d7cacea53) | Get sound effect management class (TXAudioEffectManager). |
| [startSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50762#e50d6c1b86145e690e50c3cf64afcfb8) | Enable system audio capturing. |
| [stopSystemAudioLoopback](https://www.tencentcloud.com/document/product/647/50762#a542a2b1c0a06558e5ee453811395fca) | Stop system audio capturing(iOS not supported). |
| [startScreenCapture](https://www.tencentcloud.com/document/product/647/50762#9b55d2e9cd4e32eae74a9eb3555f6c8b) | Start screen sharing. |
| [stopScreenCapture](https://www.tencentcloud.com/document/product/647/50762#2a667ba75e08183bd5f764374a6de7ba) | Stop screen sharing. |
| [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/50762#d7f9ad7b108c98e919f5f1cca757e72d) | Pause screen sharing. |
| [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/50762#1924263011bb92fba1642ad3e139629f) | Resume screen sharing. |
| [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50762#ae8dee3c3444ccd1450021b8f2cc5d4e) | Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems). |
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
| [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50762#9649cfc709c73d6dbb4df75bbc798fab) | Use UDP channel to send custom message to all users in room. |
| [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50762#52a919f9f3a990ebd08679bd47aa69bb) | Use SEI channel to send custom message to all users in room. |
| [startSpeedTest](https://www.tencentcloud.com/document/product/647/50762#ebfdd762ef3bab9136d8ca683892294b) | Start network speed test (used before room entry). |
| [stopSpeedTest](https://www.tencentcloud.com/document/product/647/50762#300e5f71dde3917dc5e057f9e1f6e014) | Stop network speed test. |
| [getSDKVersion](https://www.tencentcloud.com/document/product/647/50762#931c5ef5098a8b7cf4c2988104ac9e89) | Get SDK version information. |
| [setLogLevel](https://www.tencentcloud.com/document/product/647/50762#ded8d5d4a8c7531405e1915c646a3132) | Set log output level. |
| [setConsoleEnabled](https://www.tencentcloud.com/document/product/647/50762#7173269cfd715b2730be7aab261d647c) | Enable/Disable console log printing. |
| [setLogCompressEnabled](https://www.tencentcloud.com/document/product/647/50762#67d4f29628d27e97edab41b15770c91b) | Enable/Disable local log compression. |
| [setLogDirPath](https://www.tencentcloud.com/document/product/647/50762#770e9da3f6780da61505e784e3ba0df2) | Set local log storage path. |
| [setLogListener](https://www.tencentcloud.com/document/product/647/50762#8cde741f40653e7780b88d6607c210fb) | Set log callback. |
| [showDebugView](https://www.tencentcloud.com/document/product/647/50762#b821f814c735a081b1de0398d23a42b1) | Display dashboard. |
| [TRTCViewMargin](https://www.tencentcloud.com/document/product/647/50762#803bd588c0708af97010b59052e669db) | Set dashboard margin. |
| [callExperimentalAPI](https://www.tencentcloud.com/document/product/647/50762#c6c3457a98b055087f5811b88b663ad7) | Call experimental APIs. |
| [enablePayloadPrivateEncryption](https://www.tencentcloud.com/document/product/647/50762#81ba4cf3583c7bd43cf3496d3001e6a1) | Enable or disable private encryption of media streams. |

## sharedInstance

**sharedInstance**

| TRTCCloud sharedInstance | (Context context) |
| --- | --- |

**Create TRTCCloud instance (singleton mode).**

| Param | DESC |
| --- | --- |
| context | It is only applicable to the Android platform. The SDK internally converts it into the ` ApplicationContext ` of Android to call the Android system API. |

> **Note**1. Please use [destroySharedInstance](https://www.tencentcloud.com/document/product/647/50762#61247ee5547195d11e99e12d2443f62b) to release the object pointer.

## destroySharedInstance

**destroySharedInstance**

**Terminate TRTCCloud instance (singleton mode).**

## addListener

**addListener**

| void addListener | ([TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) listener) |
| --- | --- |

**Add TRTC event callback.**

You can use [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) to get various event notifications from the SDK, such as error codes, warning codes, and audio/video status parameters.

## removeListener

**removeListener**

| void removeListener | ([TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) listener) |
| --- | --- |

**Remove TRTC event callback.**

## setListenerHandler

**setListenerHandler**

| void setListenerHandler | (Handler listenerHandler) |
| --- | --- |

**Set the queue that drives the $TRTCCloudDelegate$ event callback.**

If you do not specify a ` listenerHandler `, the SDK will use ` MainQueue ` as the queue for driving [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) event callbacks by default.

In other words, if you do not set the ` listenerHandler ` attribute, all callback functions in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) will be driven by ` MainQueue `.

| Param | DESC |
| --- | --- |
| listenerHandler |  |

> **Note**If you specify a ` listenerHandler `, please do not manipulate the UI in the [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) callback function; otherwise, thread safety issues will occur.

## enterRoom

**enterRoom**

| void enterRoom | (TRTCCloudDef.[TRTCParams](https://www.tencentcloud.com/document/product/647/50768#a1de1e93c6cfc6be81dd4152b9e4c190) param |
| --- | --- |
|  | int scene) |

**Enter room.**

All TRTC users need to enter a room before they can "publish" or "subscribe to" audio/video streams. "Publishing" refers to pushing their own streams to the cloud, and "subscribing to" refers to pulling the streams of other users in the room from the cloud.

When calling this API, you need to specify your application scenario ([TRTCAppScene](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)) to get the best audio/video transfer experience. We provide the following four scenarios for your choice:

- [TRTC_APP_SCENE_VIDEOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340):

Video call scenario. Use cases: [one-to-one video call], [video conferencing with up to 300 participants], [online medical diagnosis], [small class], [video interview], etc.

In this scenario, each room supports up to 300 concurrent online users, and up to 50 of them can speak simultaneously.

- [TRTC_APP_SCENE_AUDIOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340):

Audio call scenario. Use cases: [one-to-one audio call], [audio conferencing with up to 300 participants], [audio chat], [online Werewolf], etc.

In this scenario, each room supports up to 300 concurrent online users, and up to 50 of them can speak simultaneously.

- [TRTC_APP_SCENE_LIVE](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340):

Live streaming scenario. Use cases: [low-latency video live streaming], [interactive classroom for up to 100,000 participants], [live video competition], [video dating room], [remote training], [large-scale conferencing], etc.

In this scenario, each room supports up to 100,000 concurrent online users, but you should specify the user roles: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50768#ba5a0edf12dbdde569c7456699ba9e75)) or audience ([TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50768#ba5a0edf12dbdde569c7456699ba9e75)).

- [TRTC_APP_SCENE_VOICE_CHATROOM](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340):

Audio chat room scenario. Use cases: [Clubhouse], [online karaoke room], [music live room], [FM radio], etc.

In this scenario, each room supports up to 100,000 concurrent online users, but you should specify the user roles: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50768#ba5a0edf12dbdde569c7456699ba9e75)) or audience ([TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50768#ba5a0edf12dbdde569c7456699ba9e75)).

After calling this API, you will receive the ` onEnterRoom(result) ` callback from [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0):

- If room entry succeeded, the ` result ` parameter will be a positive number (` result ` > 0), indicating the time in milliseconds (ms) between function call and room entry.
- If room entry failed, the ` result ` parameter will be a negative number (` result ` < 0), indicating the [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35130#336ef58d7636c75f9aa0c87753e08e7c) for room entry failure.

| Param | DESC |
| --- | --- |
| param | Room entry parameter, which is used to specify the user's identity, role, authentication credentials, and other information. For more information, please see [TRTCParams](https://www.tencentcloud.com/document/product/647/50768#a1de1e93c6cfc6be81dd4152b9e4c190). |
| scene | Application scenario, which is used to specify the use case. The same [TRTCAppScene](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340) should be configured for all users in the same room. |

> **Note**1. If ` scene ` is specified as [TRTC_APP_SCENE_LIVE](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340) or [TRTC_APP_SCENE_VOICE_CHATROOM](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340), you must use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50768#a1de1e93c6cfc6be81dd4152b9e4c190) to specify the role of the current user in the room.2. The same ` scene ` should be configured for all users in the same room.3. Please try to ensure that [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) and [exitRoom](https://www.tencentcloud.com/document/product/647/50762#4651ae2c9ff5aa99442102e0d77a8606) are used in pair; that is, please make sure that "the previous room is exited before the next room is entered"; otherwise, many issues may occur.

## exitRoom

**exitRoom**

**Exit room.**

Calling this API will allow the user to leave the current audio or video room and release the camera, mic, speaker, and other device resources.

After resources are released, the SDK will use the ` onExitRoom() ` callback in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) to notify you.

If you need to call [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) again or switch to the SDK of another provider, we recommend you wait until you receive the [onExitRoom](https://www.tencentcloud.com/document/product/647/50763#41db48ab552c935ba865dc86eeb5b9d0) callback, so as to avoid the problem of the camera or mic being occupied.

## switchRole

**switchRole**

| void switchRole | (int role) |
| --- | --- |

**Switch role.**

This API is used to switch the user role between ` anchor ` and ` audience `.

As video live rooms and audio chat rooms need to support an audience of up to 100,000 concurrent online users, the rule "only anchors can publish their audio/video streams" has been set. Therefore, when some users want to publish their streams (so that they can interact with anchors), they need to switch their role to "anchor" first.

You can use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50768#a1de1e93c6cfc6be81dd4152b9e4c190) during room entry to specify the user role in advance or use the ` switchRole ` API to switch roles after room entry.

| Param | DESC |
| --- | --- |
| role | Role, which is ` anchor ` by default: [TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50768#ba5a0edf12dbdde569c7456699ba9e75): anchor, who can publish their audio/video streams. Up to 50 anchors are allowed to publish streams at the same time in one room. [TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50768#ba5a0edf12dbdde569c7456699ba9e75): audience, who cannot publish their audio/video streams, but can only watch streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/50762#0a2b76d62a79877c408aa638b61d9b8e). One room supports an audience of up to 100,000 concurrent online users. |

> **Note**1. This API is only applicable to two scenarios: live streaming ([TRTC_APP_SCENE_LIVE](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)) and audio chat room ([TRTC_APP_SCENE_VOICE_CHATROOM](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)).2. If the ` scene ` you specify in [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) is [TRTC_APP_SCENE_VIDEOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340) or [TRTC_APP_SCENE_AUDIOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340), please do not call this API.

## switchRole

**switchRole**

| void switchRole | (int role |
| --- | --- |
|  | final String privateMapKey) |

**Switch role(support permission credential).**

This API is used to switch the user role between ` anchor ` and ` audience `.

As video live rooms and audio chat rooms need to support an audience of up to 100,000 concurrent online users, the rule "only anchors can publish their audio/video streams" has been set. Therefore, when some users want to publish their streams (so that they can interact with anchors), they need to switch their role to "anchor" first.

You can use the ` role ` field in [TRTCParams](https://www.tencentcloud.com/document/product/647/50768#a1de1e93c6cfc6be81dd4152b9e4c190) during room entry to specify the user role in advance or use the ` switchRole ` API to switch roles after room entry.

| Param | DESC |
| --- | --- |
| privateMapKey | Permission credential used for permission control. If you want only users with the specified ` userId ` values to enter a room or push streams, you need to use ` privateMapKey ` to restrict the permission. We recommend you use this parameter only if you have high security requirements. For more information, please see [Enabling Advanced Permission Control](https://www.tencentcloud.com/document/product/647/35157). |
| role | Role, which is ` anchor ` by default: [TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/50768#ba5a0edf12dbdde569c7456699ba9e75): anchor, who can publish their audio/video streams. Up to 50 anchors are allowed to publish streams at the same time in one room. [TRTCRoleAudience](https://www.tencentcloud.com/document/product/647/50768#ba5a0edf12dbdde569c7456699ba9e75): audience, who cannot publish their audio/video streams, but can only watch streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/50762#0a2b76d62a79877c408aa638b61d9b8e). One room supports an audience of up to 100,000 concurrent online users. |

> **Note**1. This API is only applicable to two scenarios: live streaming ([TRTC_APP_SCENE_LIVE](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)) and audio chat room ([TRTC_APP_SCENE_VOICE_CHATROOM](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)).2. If the ` scene ` you specify in [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) is [TRTC_APP_SCENE_VIDEOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340) or [TRTC_APP_SCENE_AUDIOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340), please do not call this API.

## switchRoom

**switchRoom**

| void switchRoom | (final TRTCCloudDef.[TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/50768#d43f5dc42762839497bd8586ac2091e3) config) |
| --- | --- |

**Switch room.**

This API is used to quickly switch a user from one room to another.

- If the user's role is ` audience `, calling this API is equivalent to ` exitRoom ` (current room) + ` enterRoom ` (new room).
- If the user's role is ` anchor `, the API will retain the current audio/video publishing status while switching the room; therefore, during the room switch, camera preview and sound capturing will not be interrupted.

This API is suitable for the online education scenario where the supervising teacher can perform fast room switch across multiple rooms. In this scenario, using ` switchRoom ` can get better smoothness and use less code than ` exitRoom + enterRoom `.

The API call result will be called back through ` onSwitchRoom(errCode, errMsg) ` in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).

| Param | DESC |
| --- | --- |
| config | Room parameter. For more information, please see [TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/50768#d43f5dc42762839497bd8586ac2091e3). |

> **Note**Due to the requirement for compatibility with legacy versions of the SDK, the ` config ` parameter contains both ` roomId ` and ` strRoomId ` parameters. You should pay special attention as detailed below when specifying these two parameters:1. If you decide to use ` strRoomId `, then set ` roomId ` to 0. If both are specified, ` roomId ` will be used.2. All rooms need to use either ` strRoomId ` or ` roomId ` at the same time. They cannot be mixed; otherwise, there will be many unexpected bugs.

## ConnectOtherRoom

**ConnectOtherRoom**

| void ConnectOtherRoom | (String param) |
| --- | --- |

**Request cross-room call.**

By default, only users in the same room can make audio/video calls with each other, and the audio/video streams in different rooms are isolated from each other.

However, you can publish the audio/video streams of an anchor in another room to the current room by calling this API. At the same time, this API will also publish the local audio/video streams to the target anchor's room.

In other words, you can use this API to share the audio/video streams of two anchors in two different rooms, so that the audience in each room can watch the streams of these two anchors. This feature can be used to implement anchor competition.

The result of requesting cross-room call will be returned through the [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50763#bb05cf36cc9a461e0b45ae825ee5e2e0) callback in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).

For example, after anchor A in room "101" uses ` connectOtherRoom() ` to successfully call anchor B in room "102":

- All users in room "101" will receive the ` onRemoteUserEnterRoom(B) ` and ` onUserVideoAvailable(B,true) ` event callbacks of anchor B; that is, all users in room "101" can subscribe to the audio/video streams of anchor B.
- All users in room "102" will receive the ` onRemoteUserEnterRoom(A) ` and ` onUserVideoAvailable(A,true) ` event callbacks of anchor A; that is, all users in room "102" can subscribe to the audio/video streams of anchor A.

![](https://qcloudimg.tencent-cloud.cn/raw/c5e6c72fc163ad5c0b6b7b00e1da55b5.png)

For compatibility with subsequent extended fields for cross-room call, parameters in JSON format are used currently.

Case 1: numeric room ID

If anchor A in room "101" wants to co-anchor with anchor B in room "102", then anchor A needs to pass in {"roomId": 102, "userId": "userB"} when calling this API.

Below is the sample code:

```
  JSONObject jsonObj = new JSONObject();  jsonObj.put("roomId", 102);  jsonObj.put("userId", "userB");  trtc.ConnectOtherRoom(jsonObj.toString());
```

Case 2: string room ID

If you use a string room ID, please be sure to replace the ` roomId ` in JSON with ` strRoomId `, such as ` {"strRoomId": "102", "userId": "userB"} `

Below is the sample code:

```
  JSONObject jsonObj = new JSONObject();  jsonObj.put("strRoomId", "102");  jsonObj.put("userId", "userB");  trtc.ConnectOtherRoom(jsonObj.toString());
```

| Param | DESC |
| --- | --- |
| param | You need to pass in a string parameter in JSON format: ` roomId ` represents the room ID in numeric format, ` strRoomId ` represents the room ID in string format, and ` userId ` represents the user ID of the target anchor. |

## DisconnectOtherRoom

**DisconnectOtherRoom**

**Exit cross-room call.**

The result will be returned through the ` onDisconnectOtherRoom() ` callback in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).

## setDefaultStreamRecvMode

**setDefaultStreamRecvMode**

| void setDefaultStreamRecvMode | (boolean autoRecvAudio |
| --- | --- |
|  | boolean autoRecvVideo) |

**Set subscription mode (which must be set before room entry for it to take effect).**

You can switch between the "automatic subscription" and "manual subscription" modes through this API:

- Automatic subscription: this is the default mode, where the user will immediately receive the audio/video streams in the room after room entry, so that the audio will be automatically played back, and the video will be automatically decoded (you still need to bind the rendering control through the ` startRemoteView ` API).
- Manual subscription: after room entry, the user needs to manually call the [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) API to start subscribing to and decoding the video stream and call the [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/50762#d6800ccf317e0ccecc8ba17e44e59438) (false) API to start playing back the audio stream.

In most scenarios, users will subscribe to the audio/video streams of all anchors in the room after room entry. Therefore, TRTC adopts the automatic subscription mode by default in order to achieve the best "instant streaming experience".

In your application scenario, if there are many audio/video streams being published at the same time in each room, and each user only wants to subscribe to 1â2 streams of them, we recommend you use the "manual subscription" mode to reduce the traffic costs.

| Param | DESC |
| --- | --- |
| autoRecvAudio | true: automatic subscription to audio; false: manual subscription to audio by calling ` muteRemoteAudio(false) `. Default value: true |
| autoRecvVideo | true: automatic subscription to video; false: manual subscription to video by calling ` startRemoteView `. Default value: true |

> **Note**1. The configuration takes effect only if this API is called before room entry (enterRoom).2. In the automatic subscription mode, if the user does not call [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) to subscribe to the video stream after room entry, the SDK will automatically stop subscribing to the video stream in order to reduce the traffic consumption.

## createSubCloud

**createSubCloud**

**Create room subinstance (for concurrent multi-room listen/watch).**

` TRTCCloud ` was originally designed to work in the singleton mode, which limited the ability to watch concurrently in multiple rooms.

By calling this API, you can create multiple ` TRTCCloud ` instances, so that you can enter multiple different rooms at the same time to listen/watch audio/video streams.

However, it should be noted that your ability to publish audio and video streams in multiple ` TRTCCloud ` instances will be limited.

This feature is mainly used in the "super small class" use case in the online education scenario to break the limit that "only up to 50 users can publish their audio/video streams simultaneously in one TRTC room".

Below is the sample code:

```
    //In the small room that needs interaction, enter the room as an anchor and push audio and video streams    TRTCCloud mainCloud = TRTCCloud.sharedInstance(mContext);    TRTCCloudDef.TRTCParams mainParams = new TRTCCloudDef.TRTCParams();    //Fill your params    mainParams.role = TRTCCloudDef.TRTCRoleAnchor;    mainCloud.enterRoom(mainParams, TRTCCloudDef.TRTC_APP_SCENE_LIVE);    //...    mainCloud.startLocalPreview(true, videoView);    mainCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_DEFAULT);    //In the large room that only needs to watch, enter the room as an audience and pull audio and video streams    TRTCCloud subCloud = mainCloud.createSubCloud();    TRTCCloudDef.TRTCParams subParams = new TRTCCloudDef.TRTCParams();    //Fill your params    subParams.role = TRTCCloudDef.TRTCRoleAudience;    subCloud.enterRoom(subParams, TRTCCloudDef.TRTC_APP_SCENE_LIVE);    //...    subCloud.startRemoteView(userId, TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, view);    //...    //Exit from new room and release it.    subCloud.exitRoom();    mainCloud.destroySubCloud(subCloud);
```

> **Note**1. The same user can enter multiple rooms with different ` roomId ` values by using the same ` userId `.2. Two devices cannot use the same ` userId ` to enter the same room with a specified ` roomId `.3. You can set [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) separately for different instances to get their own event notifications.4. The same user can push streams in multiple ` TRTCCloud ` instances at the same time, and can also call APIs related to local audio/video in the sub instance. But need to pay attention to: Audio needs to be collected by the microphone or custom data at the same time in all instances, and the result of API calls related to the audio device will be based on the last time; The result of camera-related API call will be based on the last time: [startLocalPreview](https://www.tencentcloud.com/document/product/647/50762#b1f7334c9de08e2e26545ea4ddfd5507).

**Return Desc:**

` TRTCCloud ` subinstance

## destroySubCloud

**destroySubCloud**

| void destroySubCloud | (final [TRTCCloud](https://www.tencentcloud.com/document/product/647/50762#0586d1684814cdfa935ab2f318c30565) subCloud) |
| --- | --- |

**Terminate room subinstance.**

| Param | DESC |
| --- | --- |
| subCloud |  |

## updateOtherRoomForwardMode

**updateOtherRoomForwardMode**

| void updateOtherRoomForwardMode | (String param) |
| --- | --- |

**Change the upstream capability of the cross-room anchor in the current room.**

By default, after calling the [connectOtherRoom](https://www.tencentcloud.com/document/product/647/50762#71e28e2184ffae717c6d768d9f757ad7) API to make a cross-room call with an anchor in another room, all users in the current room will receive the audio/video streams published by that anchor.

You can use this API to limit the upstream capability of the cross-room anchor in the current room, and prohibit or allow the cross-room anchor to publish audio/video/sub-stream. This behavior will affect all users in the room.

After disabling a certain upstream capability of the cross-room anchor, all users in the current room will no longer receive the corresponding audio/video stream, and cannot subscribe to the corresponding audio/video.

Note that this API can only be called by the anchor who is conducting the cross-room call, and the restrictions set by this API will be reset when the cross-room call is interrupted or the corresponding anchor leaves the room.

The result of calling this API will be returned through the ` onUpdateOtherRoomForwardMode() ` callback in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).

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

| void startPublishMediaStream | (TRTCCloudDef.[TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50768#11c06c485af4d4bd3b60bc0c883a9a32) target |
| --- | --- |
|  | TRTCCloudDef.[TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50768#22718fe81d94d21ec895cbc11820c726) params |
|  | TRTCCloudDef.[TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50768#a5a3b285846955f523db70b37449f161) config) |

**Publish a stream.**

After this API is called, the TRTC server will relay the stream of the local user to a CDN (after transcoding or without transcoding), or transcode and publish the stream to a TRTC room.

You can use the [TRTCPublishMode](https://www.tencentcloud.com/document/product/647/50768#b610b2f512786514d768201353902e93) parameter in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50768#11c06c485af4d4bd3b60bc0c883a9a32) to specify the publishing mode.

| Param | DESC |
| --- | --- |
| config | The On-Cloud MixTranscoding settings. This parameter is invalid in the relay-to-CDN mode. It is required if you transcode and publish the stream to a CDN or to a TRTC room. For details, see [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50768#a5a3b285846955f523db70b37449f161). |
| params | The encoding settings. This parameter is required if you transcode and publish the stream to a CDN or to a TRTC room. If you relay to a CDN without transcoding, to improve the relaying stability and playback compatibility, we also recommend you set this parameter. For details, see [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50768#22718fe81d94d21ec895cbc11820c726). |
| target | The publishing destination. You can relay the stream to a CDN (after transcoding or without transcoding) or transcode and publish the stream to a TRTC room. For details, see [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50768#11c06c485af4d4bd3b60bc0c883a9a32). |

> **Note**1. The SDK will send a task ID to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#95cedc06908dda47f4459b30961764a4) callback.2. You can start a publishing task only once and cannot initiate two tasks that use the same publishing mode and publishing cdn url. Note the task ID returned, which you need to pass to [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#735a40ecbeb18a37348b9dbce0ae8c68) to modify the publishing parameters or [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#ef07e55b75ccb81b9849502f67b07083) to stop the task.3. You can specify up to 10 CDN URLs in ` target `. You will be charged only once for transcoding even if you relay to multiple CDNs.4. To avoid causing errors, do not specify the same URLs for different publishing tasks executed at the same time. We recommend you add "sdkappid_roomid_userid_main" to URLs to distinguish them from one another and avoid application conflicts.

## updatePublishMediaStream

**updatePublishMediaStream**

| void updatePublishMediaStream | (final String taskId |
| --- | --- |
|  | TRTCCloudDef.[TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50768#11c06c485af4d4bd3b60bc0c883a9a32) target |
|  | TRTCCloudDef.[TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50768#22718fe81d94d21ec895cbc11820c726) params |
|  | TRTCCloudDef.[TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50768#a5a3b285846955f523db70b37449f161) config) |

**Modify publishing parameters.**

You can use this API to change the parameters of a publishing task initiated by [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4).

| Param | DESC |
| --- | --- |
| config | The On-Cloud MixTranscoding settings. This parameter is invalid in the relay-to-CDN mode. It is required if you transcode and publish the stream to a CDN or to a TRTC room. For details, see [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/50768#a5a3b285846955f523db70b37449f161). |
| params | The encoding settings. This parameter is required if you transcode and publish the stream to a CDN or to a TRTC room. If you relay to a CDN without transcoding, to improve the relaying stability and playback compatibility, we recommend you set this parameter. For details, see [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50768#22718fe81d94d21ec895cbc11820c726). |
| target | The publishing destination. You can relay the stream to a CDN (after transcoding or without transcoding) or transcode and publish the stream to a TRTC room. For details, see [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50768#11c06c485af4d4bd3b60bc0c883a9a32). |
| taskId | The task ID returned to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#95cedc06908dda47f4459b30961764a4) callback. |

> **Note**1. You can use this API to add or remove CDN URLs to publish to (you can publish to up to 10 CDNs at a time). To avoid causing errors, do not specify the same URLs for different tasks executed at the same time.2. You can use this API to switch a relaying task to transcoding or vice versa. For example, in cross-room communication, you can first call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4) to relay to a CDN. When the anchor requests cross-room communication, call this API, passing in the task ID to switch the relaying task to a transcoding task. This can ensure that the live stream and CDN playback are not interrupted (you need to keep the encoding parameters consistent).3. You can not switch output between "only audio", "only video" and "audio and video" for the same task.

## stopPublishMediaStream

**stopPublishMediaStream**

| void stopPublishMediaStream | (final String taskId) |
| --- | --- |

**Stop publishing.**

You can use this API to stop a task initiated by [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4).

| Param | DESC |
| --- | --- |
| taskId | The task ID returned to you via the [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#95cedc06908dda47f4459b30961764a4) callback. |

> **Note**1. If the task ID is not saved to your backend, you can call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4) again when an anchor re-enters the room after abnormal exit. The publishing will fail, but the TRTC backend will return the task ID to you.2. If ` taskId ` is left empty, the TRTC backend will end all tasks you started through [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4). You can leave it empty if you have started only one task or want to stop all publishing tasks started by you.

## startLocalPreview

**startLocalPreview**

| void startLocalPreview | (boolean frontCamera |
| --- | --- |
|  | TXCloudVideoView view) |

**Enable the preview image of local camera (mobile).**

If this API is called before [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f), the SDK will only enable the camera and wait until [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) is called before starting push.

If it is called after [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f), the SDK will enable the camera and automatically start pushing the video stream.

When the first camera video frame starts to be rendered, you will receive the ` onCameraDidReady ` callback in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).

| Param | DESC |
| --- | --- |
| frontCamera | true: front camera; false: rear camera |
| view | Control that carries the video image |

> **Note**If you want to preview the camera image and adjust the beauty filter parameters through ` BeautyManager ` before going live, you can: Scheme 1. Call ` startLocalPreview ` before calling [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f). Scheme 2. Call ` startLocalPreview ` and ` muteLocalVideo(true) ` after calling [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f).

## updateLocalView

**updateLocalView**

| void updateLocalView | (TXCloudVideoView view) |
| --- | --- |

**Update the preview image of local camera.**

## stopLocalPreview

**stopLocalPreview**

**Stop camera preview.**

## muteLocalVideo

**muteLocalVideo**

| void muteLocalVideo | (int streamType |
| --- | --- |
|  | boolean mute) |

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
| streamType | Specify for which video stream to pause (or resume). Only [TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) and [TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) are supported |

## setVideoMuteImage

**setVideoMuteImage**

| void setVideoMuteImage | (Bitmap image |
| --- | --- |
|  | int fps) |

**Set placeholder image during local video pause.**

When you call ` muteLocalVideo(true) ` to pause the local video image, you can set a placeholder image by calling this API. Then, other users in the room will see this image instead of a black screen.

| Param | DESC |
| --- | --- |
| fps | Frame rate of the placeholder image. Minimum value: 5. Maximum value: 10. Default value: 5 |
| image | Placeholder image. A null value means that no more video stream data will be sent after [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50762#3b9dab7aed0816028e9e593bce4525a9). The default value is null. |

## startRemoteView

**startRemoteView**

| void startRemoteView | (String userId |
| --- | --- |
|  | int streamType |
|  | TXCloudVideoView view) |

**Subscribe to remote user's video stream and bind video rendering control.**

Calling this API allows the SDK to pull the video stream of the specified ` userId ` and render it to the rendering control specified by the ` view ` parameter. You can set the display mode of the video image through [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50762#bfce08bf4cac4decd14d800b69d0ee8e).

- If you already know the ` userId ` of a user who has a video stream in the room, you can directly call ` startRemoteView ` to subscribe to the user's video image.
- If you don't know which users in the room are publishing video streams, you can wait for the notification from [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/50763#448623ba3ddafa44cdb425bea100c2d8) after [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f).

Calling this API only starts pulling the video stream, and the image needs to be loaded and buffered at this time. After the buffering is completed, you will receive a notification from [onFirstVideoFrame](https://www.tencentcloud.com/document/product/647/50763#a11a508ae7b71797961235888ddc2770).

| Param | DESC |
| --- | --- |
| streamType | Video stream type of the ` userId ` specified for watching: HD big image: [TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) Smooth small image: [TRTC_VIDEO_STREAM_TYPE_SMALL](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) (the remote user should enable dual-channel encoding through [enableEncSmallVideoStream](https://www.tencentcloud.com/document/product/647/50762#c8decbf786be761073799e48fe807de7) for this parameter to take effect) Substream image (usually used for screen sharing): [TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) |
| userId | ID of the specified remote user |
| view | Rendering control that carries the video image |

> **Note**The following requires your attention:1. The SDK supports watching the big image and substream image or small image and substream image of a ` userId ` at the same time, but does not support watching the big image and small image at the same time.2. Only when the specified ` userId ` enables dual-channel encoding through [enableEncSmallVideoStream](https://www.tencentcloud.com/document/product/647/50762#c8decbf786be761073799e48fe807de7) can the user's small image be viewed.3. If the small image of the specified ` userId ` does not exist, the SDK will switch to the big image of the user by default.

## updateRemoteView

**updateRemoteView**

| void updateRemoteView | (String userId |
| --- | --- |
|  | int streamType |
|  | TXCloudVideoView view) |

**Update remote user's video rendering control.**

This API can be used to update the rendering control of the remote video image. It is often used in interactive scenarios where the display area needs to be switched.

| Param | DESC |
| --- | --- |
| streamType | Type of the stream for which to set the preview window (only [TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) and [TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) are supported) |
| userId | ID of the specified remote user |
| view | Control that carries the video image |

## stopRemoteView

**stopRemoteView**

| void stopRemoteView | (String userId |
| --- | --- |
|  | int streamType) |

**Stop subscribing to remote user's video stream and release rendering control.**

Calling this API will cause the SDK to stop receiving the user's video stream and release the decoding and rendering resources for the stream.

| Param | DESC |
| --- | --- |
| streamType | Video stream type of the ` userId ` specified for watching: HD big image: [TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) Smooth small image: [TRTC_VIDEO_STREAM_TYPE_SMALL](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) Substream image (usually used for screen sharing): [TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) |
| userId | ID of the specified remote user |

## stopAllRemoteView

**stopAllRemoteView**

**Stop subscribing to all remote users' video streams and release all rendering resources.**

Calling this API will cause the SDK to stop receiving all remote video streams and release all decoding and rendering resources.

> **Note**If a substream image (screen sharing) is being displayed, it will also be stopped.

## muteRemoteVideoStream

**muteRemoteVideoStream**

| void muteRemoteVideoStream | (String userId |
| --- | --- |
|  | int streamType |
|  | boolean mute) |

**Pause/Resume subscribing to remote user's video stream.**

This API only pauses/resumes receiving the specified user's video stream but does not release displaying resources; therefore, the video image will freeze at the last frame before it is called.

| Param | DESC |
| --- | --- |
| mute | Whether to pause receiving |
| streamType | Specify for which video stream to pause (or resume): HD big image: [TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) Smooth small image: [TRTC_VIDEO_STREAM_TYPE_SMALL](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) Substream image (usually used for screen sharing): [TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2) |
| userId | ID of the specified remote user |

> **Note**This API can be called before room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f)), and the pause status will be reset after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50762#4651ae2c9ff5aa99442102e0d77a8606)). After calling this API to pause receiving the video stream from a specific user, simply calling the [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) API will not be able to play the video from that user. You need to call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50762#7931b1f535d9b6f7af27c0f73d1bc3b0)(false) or [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/50762#124d79f21fc06c00349eab464fecbf6d)(false) to resume it.

## muteAllRemoteVideoStreams

**muteAllRemoteVideoStreams**

| void muteAllRemoteVideoStreams | (boolean mute) |
| --- | --- |

**Pause/Resume subscribing to all remote users' video streams.**

This API only pauses/resumes receiving all users' video streams but does not release displaying resources; therefore, the video image will freeze at the last frame before it is called.

| Param | DESC |
| --- | --- |
| mute | Whether to pause receiving |

> **Note**This API can be called before room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f)), and the pause status will be reset after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50762#4651ae2c9ff5aa99442102e0d77a8606)).After calling this interface to pause receiving video streams from all users, simply calling the [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) interface will not be able to play the video from a specific user. You need to call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50762#7931b1f535d9b6f7af27c0f73d1bc3b0)(false) or [muteAllRemoteVideoStreams](https://www.tencentcloud.com/document/product/647/50762#124d79f21fc06c00349eab464fecbf6d)(false) to resume it.

## setVideoEncoderParam

**setVideoEncoderParam**

| void setVideoEncoderParam | (TRTCCloudDef.[TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50768#b5beabfeefb812ccf1060aea67185c4e) param) |
| --- | --- |

**Set the encoding parameters of video encoder.**

This setting can determine the quality of image viewed by remote users, which is also the image quality of on-cloud recording files.

| Param | DESC |
| --- | --- |
| param | It is used to set relevant parameters for the video encoder. For more information, please see [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50768#b5beabfeefb812ccf1060aea67185c4e). |

> **Note**Begin from v11.5 version, the encoding output resolution will be aligned according to width 8 and height 2 bytes, and will be adjusted downward, eg: input resolution 540x960, actual encoding output resolution 536x960.

## setNetworkQosParam

**setNetworkQosParam**

| void setNetworkQosParam | (TRTCCloudDef.[TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/50768#15fa30eb2d0220259cea127fdb0f886f) param) |
| --- | --- |

**Set network quality control parameters.**

This setting determines the quality control policy in a poor network environment, such as "image quality preferred" or "smoothness preferred".

| Param | DESC |
| --- | --- |
| param | It is used to set relevant parameters for network quality control. For details, please refer to [TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/50768#15fa30eb2d0220259cea127fdb0f886f). |

## setLocalRenderParams

**setLocalRenderParams**

| void setLocalRenderParams | (TRTCCloudDef.[TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50768#660db44737d95899da095d02d163c478) params) |
| --- | --- |

**Set the rendering parameters of local video image.**

The parameters that can be set include video image rotation angle, fill mode, and mirror mode.

| Param | DESC |
| --- | --- |
| params | Video image rendering parameters. For more information, please see [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50768#660db44737d95899da095d02d163c478). |

## setRemoteRenderParams

**setRemoteRenderParams**

| void setRemoteRenderParams | (String userId |
| --- | --- |
|  | int streamType |
|  | TRTCCloudDef.[TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50768#660db44737d95899da095d02d163c478) params) |

**Set the rendering mode of remote video image.**

The parameters that can be set include video image rotation angle, fill mode, and mirror mode.

| Param | DESC |
| --- | --- |
| params | Video image rendering parameters. For more information, please see [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/50768#660db44737d95899da095d02d163c478). |
| streamType | It can be set to the primary stream image (TRTCVideoStreamTypeBig) or substream image (TRTCVideoStreamTypeSub). |
| userId | ID of the specified remote user |

## enableEncSmallVideoStream

**enableEncSmallVideoStream**

| int enableEncSmallVideoStream | (boolean enable |
| --- | --- |
|  | TRTCCloudDef.[TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50768#b5beabfeefb812ccf1060aea67185c4e) smallVideoEncParam) |

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

| int setRemoteVideoStreamType | (String userId |
| --- | --- |
|  | int streamType) |

**Switch the big/small image of specified remote user.**

After an anchor in a room enables dual-channel encoding, the video image that other users in the room subscribe to through [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) will be **HD big image** by default.

You can use this API to select whether the image subscribed to is the big image or small image. The API can take effect before or after [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) is called.

| Param | DESC |
| --- | --- |
| streamType | Video stream type, i.e., big image or small image. Default value: big image |
| userId | ID of the specified remote user |

> **Note**To implement this feature, the target user must have enabled the dual-channel encoding mode through [enableEncSmallVideoStream](https://www.tencentcloud.com/document/product/647/50762#c8decbf786be761073799e48fe807de7); otherwise, this API will not work.

## snapshotVideo

**snapshotVideo**

| void snapshotVideo | (String userId |
| --- | --- |
|  | int streamType |
|  | int sourceType |
|  | [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).TRTCSnapshotListener listener) |

**Screencapture video.**

You can use this API to screencapture the local video image or the primary stream image and substream (screen sharing) image of a remote user.

| Param | DESC |
| --- | --- |
| sourceType | Video image source, which can be the video stream image ([TRTC_SNAPSHOT_SOURCE_TYPE_STREAM](https://www.tencentcloud.com/document/product/647/50768#5857d748d7d477d7eabb65a774d8fea1), generally in higher definition) ãthe video rendering image ([TRTC_SNAPSHOT_SOURCE_TYPE_VIEW](https://www.tencentcloud.com/document/product/647/50768#5857d748d7d477d7eabb65a774d8fea1)) or the capture picture ([TRTC_SNAPSHOT_SOURCE_TYPE_CAPTURE](https://www.tencentcloud.com/document/product/647/50768#5857d748d7d477d7eabb65a774d8fea1)).The captured picture screenshot will be clearer. |
| streamType | Video stream type, which can be the primary stream image ([TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2), generally for camera) or substream image ([TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2), generally for screen sharing) |
| userId | User ID. A null value indicates to screencapture the local video. |

> **Note**On Windows, only video image from the [TRTC_SNAPSHOT_SOURCE_TYPE_STREAM](https://www.tencentcloud.com/document/product/647/50768#5857d748d7d477d7eabb65a774d8fea1) source can be screencaptured currently.

## setPerspectiveCorrectionPoints

**setPerspectiveCorrectionPoints**

| void setPerspectiveCorrectionPoints | (String userId |
| --- | --- |
|  | PointF[] srcPoints |
|  | PointF[] dstPoints) |

**Sets perspective correction coordinate points.**

This function allows you to specify coordinate areas for perspective correction.

| Param | DESC |
| --- | --- |
| dstPoints | The coordinates of the four vertices of the target corrected area should be passed in the order of top-left, bottom-left, top-right, bottom-right. All coordinates need to be normalized to the [0,1] range based on the render view width and height, or null to stop perspective correction of the corresponding stream. |
| srcPoints | The coordinates of the four vertices of the original stream image area should be passed in the order of top-left, bottom-left, top-right, bottom-right. All coordinates need to be normalized to the [0,1] range based on the render view width and height, or null to stop perspective correction of the corresponding stream. |
| userId | userId which corresponding to the target stream. If null value is specified, it indicates that the function is applied to the local stream. |

## setGravitySensorAdaptiveMode

**setGravitySensorAdaptiveMode**

| void setGravitySensorAdaptiveMode | (int mode) |
| --- | --- |

**Set the adaptation mode of gravity sensing (version 11.7 and above).**

After turning on gravity sensing, if the device on the collection end rotates, the images on the collection end and the audience will be rendered accordingly to ensure that the image in the field of view is always facing up.

It only takes effect in the camera capture scene inside the SDK, and only takes effect on the mobile terminal.

1. This interface only works for the collection end. If you only watch the picture in the room, opening this interface is invalid.

2. When the capture device is rotated 90 degrees or 270 degrees, the picture seen by the capture device or the audience may be cropped to maintain proportional coordination.

| Param | DESC |
| --- | --- |
| mode | Gravity sensing mode, see [TRTC_GRAVITY_SENSOR_ADAPTIVE_MODE_DISABLE](https://www.tencentcloud.com/document/product/647/50768#8b623f6360d6d70d7ced8a2a0d5127da)ã[TRTC_GRAVITY_SENSOR_ADAPTIVE_MODE_FILL_BY_CENTER_CROP](https://www.tencentcloud.com/document/product/647/50768#8b623f6360d6d70d7ced8a2a0d5127da) and [TRTC_GRAVITY_SENSOR_ADAPTIVE_MODE_FIT_WITH_BLACK_BORDER](https://www.tencentcloud.com/document/product/647/50768#8b623f6360d6d70d7ced8a2a0d5127da) for details, default value: [TRTC_GRAVITY_SENSOR_ADAPTIVE_MODE_DISABLE](https://www.tencentcloud.com/document/product/647/50768#8b623f6360d6d70d7ced8a2a0d5127da). |

## startLocalAudio

**startLocalAudio**

| void startLocalAudio | (int quality) |
| --- | --- |

**Enable local audio capturing and publishing.**

The SDK does not enable the mic by default. When a user wants to publish the local audio, the user needs to call this API to enable mic capturing and encode and publish the audio to the current room.

After local audio capturing and publishing is enabled, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50763#cb979bbb36c24acc891ce2115ff2b6c6)(userId, true) notification.

| Param | DESC |
| --- | --- |
| quality | Sound quality [TRTC_AUDIO_QUALITY_SPEECH](https://www.tencentcloud.com/document/product/647/50768#9ccda47c68c6d873c7938428e0f9fd5d) - Smooth: mono channel; audio bitrate: 18 Kbps. This is suitable for audio call scenarios, such as online meeting and audio call. [TRTC_AUDIO_QUALITY_DEFAULT](https://www.tencentcloud.com/document/product/647/50768#9ccda47c68c6d873c7938428e0f9fd5d) - Default: mono channel; audio bitrate: 50 Kbps. This is the default sound quality of the SDK and recommended if there are no special requirements. [TRTC_AUDIO_QUALITY_MUSIC](https://www.tencentcloud.com/document/product/647/50768#9ccda47c68c6d873c7938428e0f9fd5d) - HD: dual channel + full band; audio bitrate: 128 Kbps. This is suitable for scenarios where Hi-Fi music transfer is required, such as online karaoke and music live streaming. |

> **Note**This API will check the mic permission. If the current application does not have permission to use the mic, the SDK will automatically ask the user to grant the mic permission.

## stopLocalAudio

**stopLocalAudio**

**Stop local audio capturing and publishing.**

After local audio capturing and publishing is stopped, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50763#cb979bbb36c24acc891ce2115ff2b6c6)(userId, false) notification.

## muteLocalAudio

**muteLocalAudio**

| void muteLocalAudio | (boolean mute) |
| --- | --- |

**Pause/Resume publishing local audio stream.**

After local audio publishing is paused, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50763#cb979bbb36c24acc891ce2115ff2b6c6)(userId, false) notification.

After local audio publishing is resumed, other users in the room will receive the [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/50763#cb979bbb36c24acc891ce2115ff2b6c6)(userId, true) notification.

Different from [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50762#8fafafeb80fe86f9fc0d893c9c35bd4e), ` muteLocalAudio(true) ` does not release the mic permission; instead, it continues to send mute packets with extremely low bitrate.

This is very suitable for scenarios that require on-cloud recording, as video file formats such as MP4 have a high requirement for audio continuity, while an MP4 recording file cannot be played back smoothly if [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50762#8fafafeb80fe86f9fc0d893c9c35bd4e) is used.

Therefore, ` muteLocalAudio ` instead of [stopLocalAudio](https://www.tencentcloud.com/document/product/647/50762#8fafafeb80fe86f9fc0d893c9c35bd4e) is recommended in scenarios where the requirement for recording file quality is high.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |

## muteRemoteAudio

**muteRemoteAudio**

| void muteRemoteAudio | (String userId |
| --- | --- |
|  | boolean mute) |

**Pause/Resume playing back remote audio stream.**

When you mute the remote audio of a specified user, the SDK will stop playing back the user's audio and pulling the user's audio data.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |
| userId | ID of the specified remote user |

> **Note**This API works when called either before or after room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f)), and the mute status will be reset to ` false ` after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50762#4651ae2c9ff5aa99442102e0d77a8606)).

## muteAllRemoteAudio

**muteAllRemoteAudio**

| void muteAllRemoteAudio | (boolean mute) |
| --- | --- |

**Pause/Resume playing back all remote users' audio streams.**

When you mute the audio of all remote users, the SDK will stop playing back all their audio streams and pulling all their audio data.

| Param | DESC |
| --- | --- |
| mute | true: mute; false: unmute |

> **Note**This API works when called either before or after room entry ([enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f)), and the mute status will be reset to ` false ` after room exit ([exitRoom](https://www.tencentcloud.com/document/product/647/50762#4651ae2c9ff5aa99442102e0d77a8606)).

## setAudioRoute

**setAudioRoute**

| void setAudioRoute | (int route) |
| --- | --- |

**Set audio route.**

Setting "audio route" is to determine whether the sound is played back from the speaker or receiver of a mobile device; therefore, this API is only applicable to mobile devices such as phones.

Generally, a phone has two speakers: one is the receiver at the top, and the other is the stereo speaker at the bottom.

If audio route is set to the receiver, the volume is relatively low, and the sound can be heard clearly only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.

If audio route is set to the speaker, the volume is relatively high, so there is no need to put the phone near the ear. Therefore, this mode can implement the "hands-free" feature.

| Param | DESC |
| --- | --- |
| route | Audio route, i.e., whether the audio is output by speaker or receiver. Default value: [TRTC_AUDIO_ROUTE_SPEAKER](https://www.tencentcloud.com/document/product/647/50768#2e9bec9e051396669cd0f820a9d6bfc3) |

## setRemoteAudioVolume

**setRemoteAudioVolume**

| void setRemoteAudioVolume | (String userId |
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

| void enableAudioVolumeEvaluation | (boolean enable |
| --- | --- |
|  | TRTCCloudDef.[TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/50768#a009476d3d69bd49ff693344302409bf) params) |

**Enable volume reminder.**

After this feature is enabled, the SDK will return the audio volume assessment information of local user who sends stream and remote users in the [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/50763#2ec23470e2480bd26d91353c0998d019) callback of [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).

| Param | DESC |
| --- | --- |
| enable | Whether to enable the volume prompt. Itâs disabled by default. |
| params | Volume evaluation and other related parameters, please see [TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/50768#a009476d3d69bd49ff693344302409bf) |

> **Note**To enable this feature, call this API before calling [startLocalAudio](https://www.tencentcloud.com/document/product/647/50762#a127184d8d223906a5413d9610d6d22d).

## startAudioRecording

**startAudioRecording**

| int startAudioRecording | (TRTCCloudDef.[TRTCAudioRecordingParams](https://www.tencentcloud.com/document/product/647/50768#856a9c899752cb0b60944b7acc5fb868) param) |
| --- | --- |

**Start audio recording.**

After you call this API, the SDK will selectively record local and remote audio streams (such as local audio, remote audio, background music, and sound effects) into a local file.

This API works when called either before or after room entry. If a recording task has not been stopped through [stopAudioRecording](https://www.tencentcloud.com/document/product/647/50762#f3578857a142a30508f670a6c50683db) before room exit, it will be automatically stopped after room exit.

The startup and completion status of the recording will be notified through local recording-related callbacks. See TRTCCloud related callbacks for reference.

| Param | DESC |
| --- | --- |
| param | Recording parameter. For more information, please see [TRTCAudioRecordingParams](https://www.tencentcloud.com/document/product/647/50768#856a9c899752cb0b60944b7acc5fb868) |

> **Note**Since version 11.5, the results of audio recording have been changed to be notified through asynchronous callbacks instead of return values. Please refer to the relevant callbacks of [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0) .

**Return Desc:**

0: success; -1: audio recording has been started; -2: failed to create file or directory; -3: the audio format of the specified file extension is not supported.

## stopAudioRecording

**stopAudioRecording**

**Stop audio recording.**

If a recording task has not been stopped through this API before room exit, it will be automatically stopped after room exit.

## startLocalRecording

**startLocalRecording**

| void startLocalRecording | (TRTCCloudDef.[TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/50768#4d8f80d5bf4ece224c7125eec1490b3d) params) |
| --- | --- |

**Start local media recording.**

This API records the audio/video content during live streaming into a local file,and no recording fees for local recording.

| Param | DESC |
| --- | --- |
| params | Recording parameter. For more information, please see [TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/50768#4d8f80d5bf4ece224c7125eec1490b3d) |

## stopLocalRecording

**stopLocalRecording**

**Stop local media recording.**

If a recording task has not been stopped through this API before room exit, it will be automatically stopped after room exit.

## setRemoteAudioParallelParams

**setRemoteAudioParallelParams**

| void setRemoteAudioParallelParams | (TRTCCloudDef.TRTCAudioParallelParams params) |
| --- | --- |

**Set the parallel strategy of remote audio streams.**

For room with many speakers.

| Param | DESC |
| --- | --- |
| params | Audio parallel parameter. For more information, please see TRTCAudioParallelParams |

## enable3DSpatialAudioEffect

**enable3DSpatialAudioEffect**

| void enable3DSpatialAudioEffect | (boolean enabled) |
| --- | --- |

**Enable 3D spatial effect.**

Enable 3D spatial effect. Note that [TRTC_AUDIO_QUALITY_SPEECH](https://www.tencentcloud.com/document/product/647/50768#9ccda47c68c6d873c7938428e0f9fd5d) smooth or [TRTC_AUDIO_QUALITY_DEFAULT](https://www.tencentcloud.com/document/product/647/50768#9ccda47c68c6d873c7938428e0f9fd5d) default audio quality should be used.

| Param | DESC |
| --- | --- |
| enabled | Whether to enable 3D spatial effect. Itâs disabled by default. |

## updateSelf3DSpatialPosition

**updateSelf3DSpatialPosition**

| void updateSelf3DSpatialPosition | (int[] position |
| --- | --- |
|  | float[] axisForward |
|  | float[] axisRight |
|  | float[] axisUp) |

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

| void updateRemote3DSpatialPosition | (String userId |
| --- | --- |
|  | int[] position) |

**Update the specified remote user's position for 3D spatial effect.**

Update the specified remote user's position in the world coordinate system. The SDK will calculate the relative position between self and the remote users according to the parameters of this method, and then render the spatial sound effect.

| Param | DESC |
| --- | --- |
| position | The coordinate of self in the world coordinate system. The three values represent the forward, right and up coordinate values in turn. |
| userId | ID of the specified remote user. |

> **Note**1. The length of array should be 3.2. Please limit the calling frequency appropriately. It's recommended that the interval between two operations of the same remote user be at least 100ms.

## set3DSpatialReceivingRange

**set3DSpatialReceivingRange**

| void set3DSpatialReceivingRange | (String userId |
| --- | --- |
|  | int range) |

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

device management class [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50767#34ebe0bbd38c315e9bedec90588a9cd1).

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

beauty filter management class [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50766#e8b1b413512983964f87866caf492640).

## setWatermark

**setWatermark**

| void setWatermark | (Bitmap image |
| --- | --- |
|  | int streamType |
|  | float x |
|  | float y |
|  | float width) |

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
| streamType | Specify for which image to set the watermark. For more information, please see [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2). |

> **Note**If you want to set watermarks for both the primary image (generally for the camera) and the substream image (generally for screen sharing), you need to call this API twice with ` streamType ` set to different values.

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

sound effect management class [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50765#3ed6c2f3d8ab0e5cabc2c5ffffb6e1fb).

## startSystemAudioLoopback

**startSystemAudioLoopback**

**Enable system audio capturing.**

This API captures audio data from another app and mixes it into the current audio stream of the SDK. This ensures that other users in the room hear the audio played back by the another app.

In online education scenarios, a teacher can use this API to have the SDK capture the audio of instructional videos and broadcast it to students in the room.

In live music scenarios, an anchor can use this API to have the SDK capture the music played back by his or her player so as to add background music to the room.

> **Note**1. This interface only works on Android API 29 and above.2. You need to use this interface to enable system sound capture first, and it will take effect only when you call startScreenCapture to enable screen sharing.3. You need to add a foreground service to ensure that the system sound capture is not silenced, and set ` android:foregroundServiceType="mediaProjection" `.4. The SDK only capture audio of applications that satisfies the capture strategy and audio usage. Currently, the audio usage captured by the SDK includes USAGE_MEDIA, USAGE_GAME.

## stopSystemAudioLoopback

**stopSystemAudioLoopback**

**Stop system audio capturing(iOS not supported).**

## startScreenCapture

**startScreenCapture**

| void startScreenCapture | (int streamType |
| --- | --- |
|  | TRTCCloudDef.[TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50768#b5beabfeefb812ccf1060aea67185c4e) encParams |
|  | TRTCCloudDef.[TRTCScreenShareParams](https://www.tencentcloud.com/document/product/647/50768#35a9602741bd3ebd6ec82f6440ca73af) shareParams) |

**Start screen sharing.**

This API supports capturing the screen of the entire Android system, which can implement system-wide screen sharing similar to VooV Meeting.

For more information, please see [Android](https://www.tencentcloud.com/document/product/647/37337)

Video encoding parameters recommended for screen sharing on Android ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50768#b5beabfeefb812ccf1060aea67185c4e)):

- Resolution (videoResolution): 1280x720
- Frame rate (videoFps): 10 fps
- Bitrate (videoBitrate): 1200 Kbps
- Resolution adaption (enableAdjustRes): false

| Param | DESC |
| --- | --- |
| encParams | Encoding parameters. For more information, please see TRTCCloudDef#TRTCVideoEncParam. If ` encParams ` is set to ` null `, the SDK will automatically use the previously set encoding parameter. |
| shareParams | For more information, please see TRTCCloudDef#TRTCScreenShareParams. You can use the ` floatingView ` parameter to pop up a floating window (you can also use Android's ` WindowManager ` parameter to configure automatic pop-up). |

> **Note**Starting from Android 14 version, if you do not need to use the screen sharing function, you need to remove the permissions of the screen sharing front-end service in AndroidManifest.xml in your project, as follows:<uses-permission android:name="android.permission.FOREGROUND_SERVICE_MEDIA_PROJECTION" tools:node="remove" />If you need to use the screen sharing feature, you need to fill in the Play Console Statement as required by Google. The reference document is as follows:https://support.google.com/googleplay/android-developer/answer/13392821

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

## setSubStreamEncoderParam

**setSubStreamEncoderParam**

| void setSubStreamEncoderParam | (TRTCCloudDef.[TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50768#b5beabfeefb812ccf1060aea67185c4e) param) |
| --- | --- |

**Set the video encoding parameters of screen sharing (i.e., substream) (for desktop and mobile systems).**

This API can set the image quality of screen sharing (i.e., the substream) viewed by remote users, which is also the image quality of screen sharing in on-cloud recording files.

Please note the differences between the following two APIs:

- [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50762#d227231fc6993ebe2f1c332d48f71563) is used to set the video encoding parameters of the primary stream image ([TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2), generally for camera).
- [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50762#ae8dee3c3444ccd1450021b8f2cc5d4e) is used to set the video encoding parameters of the substream image ([TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2), generally for screen sharing).

| Param | DESC |
| --- | --- |
| param | Substream encoding parameters. For more information, please see [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50768#b5beabfeefb812ccf1060aea67185c4e). |

## enableCustomVideoCapture

**enableCustomVideoCapture**

| void enableCustomVideoCapture | (int streamType |
| --- | --- |
|  | boolean enable) |

**Enable/Disable custom video capturing mode.**

After this mode is enabled, the SDK will not run the original video capturing process (i.e., stopping camera data capturing and beauty filter operations) and will retain only the video encoding and sending capabilities.

You need to use [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50762#1ff9dbb21f79dea11b0ed338a4922261) to continuously insert the captured video image into the SDK.

| Param | DESC |
| --- | --- |
| enable | Whether to enable. Default value: false |
| streamType | Specify video stream type ([TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2): HD big image; [TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2): substream image). |

## sendCustomVideoData

**sendCustomVideoData**

| void sendCustomVideoData | (int streamType |
| --- | --- |
|  | TRTCCloudDef.[TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50768#9233a1b1573333abc70e53b51bd89740) frame) |

**Deliver captured video frames to SDK.**

You can use this API to deliver video frames you capture to the SDK, and the SDK will encode and transfer them through its own network module.

There are two delivery schemes for Android:

- Memory-based delivery scheme: its connection is easy but its performance is poor, so it is not suitable for scenarios with high resolution.
- Video memory-based delivery scheme: its connection requires certain knowledge in OpenGL, but its performance is good. For resolution higher than 640x360, please use this scheme.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/35158).

| Param | DESC |
| --- | --- |
| frame | Video data. If the memory-based delivery scheme is used, please set the ` data ` field; if the video memory-based delivery scheme is used, please set the ` TRTCTexture ` field. For ` bufferType `, [TRTC_VIDEO_BUFFER_TYPE_TEXTURE](https://www.tencentcloud.com/document/product/647/50768#31544309b70d6f17182c5daee7b739d8) is recommended; for ` pixelFormat `, [TRTC_VIDEO_PIXEL_FORMAT_Texture_2D](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b) is recommended. Refer to [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50768#9233a1b1573333abc70e53b51bd89740) for more supported formats. |
| streamType | Specify video stream type ([TRTC_VIDEO_STREAM_TYPE_BIG](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2): HD big image; [TRTC_VIDEO_STREAM_TYPE_SUB](https://www.tencentcloud.com/document/product/647/50768#ecf7855e3e38b63cea7d946957f964f2): substream image). |

> **Note**1. We recommend you call the [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50762#ca8ae7330112c5ceb7b65e1eb6b80a9b) API to get the ` timestamp ` value of a video frame immediately after capturing it, so as to achieve the best audio/video sync effect.2. The video frame rate eventually encoded by the SDK is not determined by the frequency at which you call this API, but by the FPS you set in [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50762#d227231fc6993ebe2f1c332d48f71563).3. Please try to keep the calling interval of this API even; otherwise, problems will be caused, such as unstable output frame rate of the encoder or out-of-sync audio/video.

## enableCustomAudioCapture

**enableCustomAudioCapture**

| void enableCustomAudioCapture | (boolean enable) |
| --- | --- |

**Enable custom audio capturing mode.**

After this mode is enabled, the SDK will not run the original audio capturing process (i.e., stopping mic data capturing) and will retain only the audio encoding and sending capabilities.

You need to use [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50762#ec667f2a4e28f7cd0932bb25f04bd498) to continuously insert the captured audio data into the SDK.

| Param | DESC |
| --- | --- |
| enable | Whether to enable. Default value: false |

> **Note**As acoustic echo cancellation (AEC) requires strict control over the audio capturing and playback time, after custom audio capturing is enabled, AEC may fail.

## sendCustomAudioData

**sendCustomAudioData**

| void sendCustomAudioData | (TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) frame) |
| --- | --- |

**Deliver captured audio data to SDK.**

We recommend you enter the following information for the [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) parameter (other fields can be left empty):

- audioFormat: audio data format, which can only be ` TRTCAudioFrameFormatPCM `.
- data: audio frame buffer. Audio frame data must be in PCM format, and it supports a frame length of 5â100 ms (20 ms is recommended). Length calculation method: **for example, if the sample rate is 48000, then the frame length for mono channel will be `48000 * 0.02s * 1 * 16 bit = 15360 bit = 1920 bytes`.**
- sampleRate: sample rate. Valid values: 16000, 24000, 32000, 44100, 48000.
- channel: number of channels (if stereo is used, data is interwoven). Valid values: 1: mono channel; 2: dual channel.
- timestamp (ms): Set it to the timestamp when audio frames are captured, which you can obtain by calling [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50762#ca8ae7330112c5ceb7b65e1eb6b80a9b) after getting a audio frame.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/47635).

| Param | DESC |
| --- | --- |
| frame | Audio data |

> **Note**Please call this API accurately at intervals of the frame length; otherwise, sound lag may occur due to uneven data delivery intervals.

## enableMixExternalAudioFrame

**enableMixExternalAudioFrame**

| void enableMixExternalAudioFrame | (boolean enablePublish |
| --- | --- |
|  | boolean enablePlayout) |

**Enable/Disable custom audio track.**

After this feature is enabled, you can mix a custom audio track into the SDK through this API. With two boolean parameters, you can control whether to play back this track remotely or locally.

| Param | DESC |
| --- | --- |
| enablePlayout | Whether the mixed audio track should be played back locally. Default value: false |
| enablePublish | Whether the mixed audio track should be played back remotely. Default value: false |

> **Note**If you specify both ` enablePublish ` and ` enablePlayout ` as ` false `, the custom audio track will be completely closed.

## mixExternalAudioFrame

**mixExternalAudioFrame**

| int mixExternalAudioFrame | (TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) frame) |
| --- | --- |

**Mix custom audio track into SDK.**

Before you use this API to mix custom PCM audio into the SDK, you need to first enable custom audio tracks through [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50762#50d27eb1a03e5d65b1ba93b81763ff06).

You are expected to feed audio data into the SDK at an even pace, but we understand that it can be challenging to call an API at absolutely regular intervals.

Given this, we have provided a buffer pool in the SDK, which can cache the audio data you pass in to reduce the fluctuations in intervals between API calls.

The value returned by this API indicates the size (ms) of the buffer pool. For example, if ` 50 ` is returned, it indicates that the buffer pool has 50 ms of audio data. As long as you call this API again within 50 ms, the SDK can make sure that continuous audio data is mixed.

If the value returned is ` 100 ` or greater, you can wait after an audio frame is played to call the API again. If the value returned is smaller than ` 100 `, then there isnât enough data in the buffer pool, and you should feed more audio data into the SDK until the data in the buffer pool is above the safety level.

Fill the fields in [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) as follows (other fields are not required).

- ` data `: audio frame buffer. Audio frames must be in PCM format. Each frame can be 5-100 ms (20 ms is recommended) in duration. Assume that the sample rate is 48000, and sound channels mono-channel. Then the **frame size would be 48000 x 0.02s x 1 x 16 bit = 15360 bit = 1920 bytes**.
- ` sampleRate `: sample rate. Valid values: 16000, 24000, 32000, 44100, 48000
- ` channel `: number of sound channels (if dual-channel is used, data is interleaved). Valid values: ` 1 ` (mono-channel); ` 2 ` (dual channel)
- ` timestamp `: timestamp (ms). Set it to the timestamp when audio frames are captured, which you can obtain by calling [generateCustomPTS](https://www.tencentcloud.com/document/product/647/50762#ca8ae7330112c5ceb7b65e1eb6b80a9b) after getting an audio frame.

| Param | DESC |
| --- | --- |
| frame | Audio data |

**Return Desc:**

If the value returned is ` 0 ` or greater, the value represents the current size of the buffer pool; if the value returned is smaller than ` 0 `, it means that an error occurred. ` -1 ` indicates that you didnât call [enableMixExternalAudioFrame](https://www.tencentcloud.com/document/product/647/50762#50d27eb1a03e5d65b1ba93b81763ff06) to enable custom audio tracks.

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

When you call APIs such as [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50762#1ff9dbb21f79dea11b0ed338a4922261) or [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50762#ec667f2a4e28f7cd0932bb25f04bd498) for custom video or audio capturing, please use this API as instructed below:

1. First, when a video or audio frame is captured, call this API to get the corresponding PTS timestamp.

2. Then, send the video or audio frame to the preprocessing module you use (such as a third-party beauty filter or sound effect component).

3. When you actually call [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50762#1ff9dbb21f79dea11b0ed338a4922261) or [sendCustomAudioData](https://www.tencentcloud.com/document/product/647/50762#ec667f2a4e28f7cd0932bb25f04bd498) for delivery, assign the PTS timestamp recorded when the frame was captured to the ` timestamp ` field in [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50768#9233a1b1573333abc70e53b51bd89740) or [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081).

**Return Desc:**

Timestamp in ms

## setLocalVideoProcessListener

**setLocalVideoProcessListener**

| int setLocalVideoProcessListener | (int pixelFormat |
| --- | --- |
|  | int bufferType |
|  | TRTCCloudListener.[TRTCVideoFrameListener](https://www.tencentcloud.com/document/product/647/50763#46ade1be457c943419d9eee7f46a06c7) listener) |

**Set video data callback for third-party beauty filters.**

After this callback is set, the SDK will call back the captured video frames through the ` listener ` you set and use them for further processing by a third-party beauty filter component. Then, the SDK will encode and send the processed video frames.

| Param | DESC |
| --- | --- |
| bufferType | Specify the format of the data called back. Currently, it supports: [TRTC_VIDEO_BUFFER_TYPE_TEXTURE](https://www.tencentcloud.com/document/product/647/50768#31544309b70d6f17182c5daee7b739d8): suitable when ` pixelFormat ` is set to [TRTC_VIDEO_PIXEL_FORMAT_Texture_2D](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b). [TRTC_VIDEO_BUFFER_TYPE_BYTE_BUFFER](https://www.tencentcloud.com/document/product/647/50768#31544309b70d6f17182c5daee7b739d8): suitable when ` pixelFormat ` is set to [TRTC_VIDEO_PIXEL_FORMAT_I420](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b). [TRTC_VIDEO_BUFFER_TYPE_BYTE_ARRAY](https://www.tencentcloud.com/document/product/647/50768#31544309b70d6f17182c5daee7b739d8): suitable when ` pixelFormat ` is set to [TRTC_VIDEO_PIXEL_FORMAT_I420](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b). |
| listener | Custom preprocessing callback. For more information, please see [TRTCVideoFrameListener](https://www.tencentcloud.com/document/product/647/50763#46ade1be457c943419d9eee7f46a06c7) |
| pixelFormat | Specify the format of the pixel called back. Currently, it supports: [TRTC_VIDEO_PIXEL_FORMAT_Texture_2D](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b): video memory-based texture scheme. [TRTC_VIDEO_PIXEL_FORMAT_I420](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b): memory-based data scheme. |

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35130#336ef58d7636c75f9aa0c87753e08e7c))

## setLocalVideoRenderListener

**setLocalVideoRenderListener**

| int setLocalVideoRenderListener | (int pixelFormat |
| --- | --- |
|  | int bufferType |
|  | TRTCCloudListener.[TRTCVideoRenderListener](https://www.tencentcloud.com/document/product/647/50763#47b4cd9dfe6d034573007cd66ed55490) listener) |

**Set the callback of custom rendering for local video.**

After this callback is set, the SDK will skip its own rendering process and call back the captured data. Therefore, you need to complete image rendering on your own.

- ` pixelFormat ` specifies the format of the data called back. Currently, Texture2D, I420, and RGBA formats are supported.
- ` bufferType ` specifies the buffer type. ` BYTE_BUFFER ` is suitable for the JNI layer, while ` BYTE_ARRAY ` can be used in direct operations at the Java layer.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/35158).

| Param | DESC |
| --- | --- |
| bufferType | Specify the data structure of the video frame: [TRTC_VIDEO_BUFFER_TYPE_TEXTURE](https://www.tencentcloud.com/document/product/647/50768#31544309b70d6f17182c5daee7b739d8): suitable when ` pixelFormat ` is set to [TRTC_VIDEO_PIXEL_FORMAT_Texture_2D](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b). [TRTC_VIDEO_BUFFER_TYPE_BYTE_BUFFER](https://www.tencentcloud.com/document/product/647/50768#31544309b70d6f17182c5daee7b739d8): suitable when ` pixelFormat ` is set to [TRTC_VIDEO_PIXEL_FORMAT_I420](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b) or [TRTC_VIDEO_PIXEL_FORMAT_RGBA](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b). [TRTC_VIDEO_BUFFER_TYPE_BYTE_ARRAY](https://www.tencentcloud.com/document/product/647/50768#31544309b70d6f17182c5daee7b739d8): suitable when ` pixelFormat ` is set to [TRTC_VIDEO_PIXEL_FORMAT_I420](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b) or [TRTC_VIDEO_PIXEL_FORMAT_RGBA](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b). |
| listener | Callback of custom video rendering. The callback is returned once for each video frame |
| pixelFormat | Specify the format of the video frame, such as: [TRTC_VIDEO_PIXEL_FORMAT_Texture_2D](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b): OpenGL texture format, which is suitable for GPU processing and has a high processing efficiency. [TRTC_VIDEO_PIXEL_FORMAT_I420](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b): standard I420 format, which is suitable for CPU processing and has a poor processing efficiency. [TRTC_VIDEO_PIXEL_FORMAT_RGBA](https://www.tencentcloud.com/document/product/647/50768#ae3a870f2a96a2a74e55f565e3040b4b): RGBA format, which is suitable for CPU processing and has a poor processing efficiency. |

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35130#336ef58d7636c75f9aa0c87753e08e7c))

## setRemoteVideoRenderListener

**setRemoteVideoRenderListener**

| int setRemoteVideoRenderListener | (String userId |
| --- | --- |
|  | int pixelFormat |
|  | int bufferType |
|  | TRTCCloudListener.[TRTCVideoRenderListener](https://www.tencentcloud.com/document/product/647/50763#47b4cd9dfe6d034573007cd66ed55490) listener) |

**Set the callback of custom rendering for remote video.**

After this callback is set, the SDK will skip its own rendering process and call back the captured data. Therefore, you need to complete image rendering on your own.

- ` pixelFormat ` specifies the format of the called back data, such as NV12, I420, and 32BGRA.
- ` bufferType ` specifies the buffer type. ` PixelBuffer ` has the highest efficiency, while ` NSData ` makes the SDK perform a memory conversion internally, which will result in extra performance loss.

For more information, please see [Custom Capturing and Rendering](https://www.tencentcloud.com/document/product/647/35158).

| Param | DESC |
| --- | --- |
| bufferType | Specify video data structure type. |
| listener | listen for custom rendering |
| pixelFormat | Specify the format of the pixel called back |
| userId | ID of the specified remote user |

> **Note**Before this API is called, ` startRemoteView(nil) ` needs to be called to get the video stream of the remote user (` view ` can be set to ` nil ` for this end); otherwise, there will be no data called back.

**Return Desc:**

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35130#336ef58d7636c75f9aa0c87753e08e7c))

## setAudioFrameListener

**setAudioFrameListener**

| void setAudioFrameListener | (TRTCCloudListener.[TRTCAudioFrameListener](https://www.tencentcloud.com/document/product/647/50763#283b8a17b28e3db63056c8c71bcb2768) listener) |
| --- | --- |

**Set custom audio data callback.**

After this callback is set, the SDK will internally call back the audio data (in PCM format), including:

- [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#b02cc5237a701b6ea1a7b5f99aad625c): callback of the audio data captured by the local mic
- [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#d481858c6d71a2accc18a96f59e8db6c): callback of the audio data captured by the local mic and preprocessed by the audio module
- [onRemoteUserAudioFrame](https://www.tencentcloud.com/document/product/647/50763#e244077b85f3b7659e10fd7a916e5ccd): audio data from each remote user before audio mixing
- [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50763#544fc0be68d0c91599e4e94046ea7ef9): callback of the audio data that will be played back by the system after audio streams are mixed

> **Note**Setting the callback to null indicates to stop the custom audio callback, while setting it to a non-null value indicates to start the custom audio callback.

## setCapturedAudioFrameCallbackFormat

**setCapturedAudioFrameCallbackFormat**

| int setCapturedAudioFrameCallbackFormat | (TRTCCloudDef.[TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50768#352b0878415e79fcd48d9027fab3f683) format) |
| --- | --- |

**Set the callback format of audio frames captured by local mic.**

This API is used to set the ` AudioFrame ` format called back by [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#b02cc5237a701b6ea1a7b5f99aad625c):

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

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35130#336ef58d7636c75f9aa0c87753e08e7c))

## setLocalProcessedAudioFrameCallbackFormat

**setLocalProcessedAudioFrameCallbackFormat**

| int setLocalProcessedAudioFrameCallbackFormat | (TRTCCloudDef.[TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50768#352b0878415e79fcd48d9027fab3f683) format) |
| --- | --- |

**Set the callback format of preprocessed local audio frames.**

This API is used to set the ` AudioFrame ` format called back by [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#d481858c6d71a2accc18a96f59e8db6c):

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

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35130#336ef58d7636c75f9aa0c87753e08e7c))

## setMixedPlayAudioFrameCallbackFormat

**setMixedPlayAudioFrameCallbackFormat**

| int setMixedPlayAudioFrameCallbackFormat | (TRTCCloudDef.[TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/50768#352b0878415e79fcd48d9027fab3f683) format) |
| --- | --- |

**Set the callback format of audio frames to be played back by system.**

This API is used to set the ` AudioFrame ` format called back by [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50763#544fc0be68d0c91599e4e94046ea7ef9):

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

0: success; values smaller than 0: error(For more information, please see [TXLiteAVError](https://www.tencentcloud.com/document/product/647/35130#336ef58d7636c75f9aa0c87753e08e7c))

## enableCustomAudioRendering

**enableCustomAudioRendering**

| void enableCustomAudioRendering | (boolean enable) |
| --- | --- |

**Enabling custom audio playback.**

You can use this API to enable custom audio playback if you want to connect to an external audio device or control the audio playback logic by yourself.

After you enable custom audio playback, the SDK will stop using its audio API to play back audio. You need to call [getCustomAudioRenderingFrame](https://www.tencentcloud.com/document/product/647/50762#f42f7c81832111bd55e15cffc5e0ce7a) to get audio frames and play them by yourself.

| Param | DESC |
| --- | --- |
| enable | Whether to enable custom audio playback. It's disabled by default. |

> **Note**The parameter must be set before room entry to take effect.

## getCustomAudioRenderingFrame

**getCustomAudioRenderingFrame**

| void getCustomAudioRenderingFrame | (final TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) audioFrame) |
| --- | --- |

**Getting playable audio data.**

Before calling this API, you need to first enable custom audio playback using [enableCustomAudioRendering](https://www.tencentcloud.com/document/product/647/50762#ae84ad6beb1326386dfde33ece5e4ed1).

Fill the fields in [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) as follows (other fields are not required):

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

| boolean sendCustomCmdMsg | (int cmdID |
| --- | --- |
|  | byte[] data |
|  | boolean reliable |
|  | boolean ordered) |

**Use UDP channel to send custom message to all users in room.**

This API allows you to use TRTC's UDP channel to broadcast custom data to other users in the current room for signaling transfer.

Other users in the room can receive the message through the ` onRecvCustomCmdMsg ` callback in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).

| Param | DESC |
| --- | --- |
| cmdID | Message ID. Value range: [1, 10] |
| data | Message to be sent. The maximum length of one single message is 1 KB. |
| ordered | Whether orderly sending is enabled, i.e., whether the data packets should be received in the same order in which they are sent; if so, a certain delay will be caused. |
| reliable | Whether reliable sending is enabled. Reliable sending can achieve a higher success rate but with a longer reception delay than unreliable sending. |

> **Note**1. Up to 30 messages can be sent per second to all users in the room (this is not supported for web and mini program currently. this limit is shared with [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50762#52a919f9f3a990ebd08679bd47aa69bb)).2. A packet can contain up to 1 KB of data; if the threshold is exceeded, the packet is very likely to be discarded by the intermediate router or server.(this limit is shared with [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50762#52a919f9f3a990ebd08679bd47aa69bb)).3. A client can send up to 16 KB of data in total per second.4. ` reliable ` and ` ordered ` must be set to the same value (` true ` or ` false `) and cannot be set to different values currently.5. We strongly recommend you set different ` cmdID ` values for messages of different types. This can reduce message delay when orderly sending is required.6. Currently only the anchor role is supported.

**Return Desc:**

true: sent the message successfully; false: failed to send the message.

## sendSEIMsg

**sendSEIMsg**

| boolean sendSEIMsg | (byte[] data |
| --- | --- |
|  | int repeatCount) |

**Use SEI channel to send custom message to all users in room.**

This API allows you to use TRTC's SEI channel to broadcast custom data to other users in the current room for signaling transfer.

The header of a video frame has a header data block called SEI. This API works by embedding the custom signaling data you want to send in the SEI block and sending it together with the video frame.

Therefore, the SEI channel has a better compatibility than [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50762#9649cfc709c73d6dbb4df75bbc798fab) as the signaling data can be transferred to the CSS CDN along with the video frame.

However, because the data block of the video frame header cannot be too large, we recommend you limit the size of the signaling data to only a few bytes when using this API.

The most common use is to embed the custom timestamp into video frames through this API so as to implement a perfect alignment between the message and video image (such as between the teaching material and video signal in the education scenario).

Other users in the room can receive the message through the ` onRecvSEIMsg ` callback in [TRTCCloudListener](https://www.tencentcloud.com/document/product/647/50763#3ac99d5f5509a822ae68d6d0fff9bde0).

| Param | DESC |
| --- | --- |
| data | Data to be sent, which can be up to 1 KB (1,000 bytes) |
| repeatCount | Data sending count |

> **Note**This API has the following restrictions:1. The data will not be instantly sent after this API is called; instead, it will be inserted into the next video frame after the API call.2. Up to 30 messages can be sent per second to all users in the room (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50762#9649cfc709c73d6dbb4df75bbc798fab)).3. Each packet can be up to 1 KB (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50762#9649cfc709c73d6dbb4df75bbc798fab)). If a large amount of data is sent, the video bitrate will increase, which may reduce the video quality or even cause lagging.4. Each client can send up to 16 KB of data in total per second (this limit is shared with [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50762#9649cfc709c73d6dbb4df75bbc798fab)).5. If multiple times of sending is required (i.e., ` repeatCount ` > 1), the data will be inserted into subsequent ` repeatCount ` video frames in a row for sending, which will increase the video bitrate.6. If ` repeatCount ` is greater than 1, the data will be sent for multiple times, and the same message may be received multiple times in the [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/50763#825b49ace1d64ee095ab1f2014529738) callback; therefore, deduplication is required.

**Return Desc:**

true: the message is allowed and will be sent with subsequent video frames; false: the message is not allowed to be sent

## startSpeedTest

**startSpeedTest**

| int startSpeedTest | (TRTCCloudDef.[TRTCSpeedTestParams](https://www.tencentcloud.com/document/product/647/50768#dd22aad94fc4b4773ca7323c7d34a1a7) params) |
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

| void setLogLevel | (int level) |
| --- | --- |

**Set log output level.**

| Param | DESC |
| --- | --- |
| level | For more information, please see [TRTCLogLevel](https://www.tencentcloud.com/document/product/647/50768#2953af68de5929f131c00faf8346e0b0). Default value: TRTCLogLevelNone |

## setConsoleEnabled

**setConsoleEnabled**

| void setConsoleEnabled | (boolean enabled) |
| --- | --- |

**Enable/Disable console log printing.**

| Param | DESC |
| --- | --- |
| enabled | Specify whether to enable it, which is disabled by default |

## setLogCompressEnabled

**setLogCompressEnabled**

| void setLogCompressEnabled | (boolean enabled) |
| --- | --- |

**Enable/Disable local log compression.**

If compression is enabled, the log size will significantly reduce, but logs can be read only after being decompressed by the Python script provided by Tencent Cloud.

If compression is disabled, logs will be stored in plaintext and can be read directly in Notepad, but will take up more storage capacity.

| Param | DESC |
| --- | --- |
| enabled | Specify whether to enable it, which is enabled by default |

## setLogDirPath

**setLogDirPath**

| void setLogDirPath | (String path) |
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

## setLogListener

**setLogListener**

| void setLogListener | (final TRTCCloudListener.[TRTCLogListener](https://www.tencentcloud.com/document/product/647/50763#e23573c054014c2a039334b5cfde7181) logListener) |
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

## TRTCViewMargin

**TRTCViewMargin**

| public TRTCViewMargin | (float leftMargin |
| --- | --- |
|  | float rightMargin |
|  | float topMargin |
|  | float bottomMargin) |

**Set dashboard margin.**

This API is used to adjust the position of the dashboard in the video rendering control. It must be called before [showDebugView](https://www.tencentcloud.com/document/product/647/50762#b821f814c735a081b1de0398d23a42b1) for it to take effect.

| Param | DESC |
| --- | --- |
| margin | Inner margin of the dashboard. It should be noted that this is based on the percentage of ` parentView `. Value range: [0, 1] |
| userId | User ID |

## callExperimentalAPI

**callExperimentalAPI**

| String callExperimentalAPI | (String jsonStr) |
| --- | --- |

**Call experimental APIs.**

## enablePayloadPrivateEncryption

**enablePayloadPrivateEncryption**

| int enablePayloadPrivateEncryption | (boolean enabled |
| --- | --- |
|  | TRTCCloudDef.[TRTCPayloadPrivateEncryptionConfig](https://www.tencentcloud.com/document/product/647/50768#e31d0d9395f1cb44ee256f450523ce86) config) |

**Enable or disable private encryption of media streams.**

In scenarios with high security requirements, TRTC recommends that you call the enablePayloadPrivateEncryption method to enable private encryption of media streams before joining a room.

After the user exits the room, the SDK will automatically close the private encryption. To re-enable private encryption, you need to call this method before the user joins the room again.

| Param | DESC |
| --- | --- |
| config | Configure the algorithm and key for private encryption of media streams, please see [TRTCPayloadPrivateEncryptionConfig](https://www.tencentcloud.com/document/product/647/50768#e31d0d9395f1cb44ee256f450523ce86). |
| enabled | Whether to enable media stream private encryption. |

> **Note**TRTC has built-in encryption for media streams before transmission. After private encryption of media streams is enabled, it will be re-encrypted with the key and initial vector you pass in.

**Return Desc:**

Interface call result, 0: Method call succeeded, -1: The incoming parameter is invalid, -2: Your subscription has expired. If you want to renew it, Please go to purchase the [TRTC Professional Edition](https://console.trtc.io/subscription/buy/rtc?packType=pro), and [contact us](https://trtc.io/zh/contact) for review before use.


---
*Source: [https://trtc.io/document/50762](https://trtc.io/document/50762)*
