# Deprecated Interface

**Deprecated Interface**

## TRTCCloud

| FuncList | DESC |
| --- | --- |
| [destroySharedIntance](https://www.tencentcloud.com/document/product/647/50761#a58cedb329d7461ec4bc1c4c48117192) | Terminate TRTCCloud instance (singleton mode). |
| [delegate](https://www.tencentcloud.com/document/product/647/50761#5f2d539b7d50c0c750c707901aaf1a46) | Set TRTC event callback. |
| [setBeautyStyle:beautyLevel:whitenessLevel:ruddinessLevel:](https://www.tencentcloud.com/document/product/647/50761#0b5a32eddc87b2ea93ed7e460d7ff9b4) | Set the strength of beauty, brightening, and rosy skin filters. |
| [setEyeScaleLevel:](https://www.tencentcloud.com/document/product/647/50761#724bc943dafc29dcd8a164bbf6abbe20) | Set the strength of eye enlarging filter. |
| [setFaceScaleLevel:](https://www.tencentcloud.com/document/product/647/50761#c731c4c88e747307feb86680776d7f4e) | Set the strength of face slimming filter. |
| [setFaceVLevel:](https://www.tencentcloud.com/document/product/647/50761#3ab8dee5f9021b7b3399267846c88583) | Set the strength of chin slimming filter. |
| [setChinLevel:](https://www.tencentcloud.com/document/product/647/50761#ca4d8575b5e7377934d36b59a1e23991) | Set the strength of chin lengthening/shortening filter. |
| [setFaceShortLevel:](https://www.tencentcloud.com/document/product/647/50761#ff21afe4736fe14a3eba4d3409f6c654) | Set the strength of face shortening filter. |
| [setNoseSlimLevel:](https://www.tencentcloud.com/document/product/647/50761#9a7f1215ac8a7a877e24e7efe9a63763) | Set the strength of nose slimming filter. |
| [selectMotionTmpl:](https://www.tencentcloud.com/document/product/647/50761#346e0aa02c5f6d1be851dcba55aa08cc) | Set animated sticker. |
| [setMotionMute:](https://www.tencentcloud.com/document/product/647/50761#d25e579a4acb0790a3680fe25147c18a) | Mute animated sticker. |
| [setFilter:](https://www.tencentcloud.com/document/product/647/50761#6b89771044b46cfb889cdfc4ff41ebdd) | Set color filter. |
| [setFilterConcentration:](https://www.tencentcloud.com/document/product/647/50761#a08d1b83a2a4e51ef16a5c37da91b8f5) | Set the strength of color filter. |
| [setGreenScreenFile:](https://www.tencentcloud.com/document/product/647/50761#0abe00d717e38eda58ac553f0aad9f13) | Set green screen video. |
| [setReverbType:](https://www.tencentcloud.com/document/product/647/50761#fa6b144460c1b12b971d09d1d5983676) | Set reverb effect. |
| [setVoiceChangerType:](https://www.tencentcloud.com/document/product/647/50761#354674dcf777fdde94709bcd598d9bd9) | Set voice changing type. |
| [enableAudioEarMonitoring:](https://www.tencentcloud.com/document/product/647/50761#7894c3bae80ed6b78fedcda978ce7875) | Enable or disable in-ear monitoring. |
| [enableAudioVolumeEvaluation:](https://www.tencentcloud.com/document/product/647/50761#336ef6f289bf8773b7e9f14544d33a17) | Enable volume reminder. |
| [enableAudioVolumeEvaluation:enable_vad:](https://www.tencentcloud.com/document/product/647/50761#cda329eefcf083cf86cc330d39482d7f) | Enable volume reminder. |
| [switchCamera](https://www.tencentcloud.com/document/product/647/50761#2ac0a5771eb7e3c8f9bfa68ed87fb5bc) | Switch camera. |
| [isCameraZoomSupported](https://www.tencentcloud.com/document/product/647/50761#4d8a53e34c0e033eaf7cb4b9eb0fa9a0) | Query whether the current camera supports zoom. |
| [setZoom:](https://www.tencentcloud.com/document/product/647/50761#fa998f52d7c05059714aa64389c3d3fa) | Set camera zoom ratio (focal length). |
| [isCameraTorchSupported](https://www.tencentcloud.com/document/product/647/50761#7cf72713063c9fb9692a2dcb3894b149) | Query whether the device supports flash. |
| [enbaleTorch:](https://www.tencentcloud.com/document/product/647/50761#9ec59f0413e8facebf4970789ddb9f64) | Enable/Disable flash. |
| [isCameraFocusPositionInPreviewSupported](https://www.tencentcloud.com/document/product/647/50761#81c3089dcf9967be57c0bb39551df683) | Query whether the camera supports setting focus. |
| [setFocusPosition:](https://www.tencentcloud.com/document/product/647/50761#b149589bd17f91c1fb0e958d1189283b) | Set the focal position of camera. |
| [isCameraAutoFocusFaceModeSupported](https://www.tencentcloud.com/document/product/647/50761#6375e6061cb89533289c5df9a7388574) | Query whether the device supports the automatic recognition of face position. |
| [enableAutoFaceFoucs:](https://www.tencentcloud.com/document/product/647/50761#755a8171a995127f48dbdaba5383ad4b) | Enable/Disable face auto focus. |
| [setSystemVolumeType:](https://www.tencentcloud.com/document/product/647/50761#83372639dffb3aede05fecc54307be9f) | Setting the system volume type (for mobile OS). |
| [snapshotVideo:type:](https://www.tencentcloud.com/document/product/647/50761#0f784a6f6c12723079027f2e39d0d88d) | Screencapture video. |
| [startScreenCaptureByReplaykit:appGroup:](https://www.tencentcloud.com/document/product/647/50761#8180c1046e109b60be86038a872dba56) | Start system-level screen sharing (for iOS 11.0 and above only). |
| [startLocalAudio](https://www.tencentcloud.com/document/product/647/50761#f76c863cde5ee0c5a505f887f4909a48) | Set sound quality. |
| [startRemoteView:view:](https://www.tencentcloud.com/document/product/647/50761#0722cfb95da5317d4cde92530b51991e) | Start displaying remote video image. |
| [stopRemoteView:](https://www.tencentcloud.com/document/product/647/50761#4df052f6ca715936fdf7904680eebb83) | Stop displaying remote video image and pulling the video data stream of remote user. |
| [setLocalViewFillMode:](https://www.tencentcloud.com/document/product/647/50761#d1014c6f34f2e10b4d1d4c41ccf3f04f) | Set the rendering mode of local image. |
| [setLocalViewRotation:](https://www.tencentcloud.com/document/product/647/50761#842312c6acccd9eae908b8220e30a14c) | Set the clockwise rotation angle of local image. |
| [setLocalViewMirror:](https://www.tencentcloud.com/document/product/647/50761#a39555e17bd47aaac49e302b5ea160e7) | Set the mirror mode of local camera's preview image. |
| [setRemoteViewFillMode:mode:](https://www.tencentcloud.com/document/product/647/50761#1f8bff52adf3bccd2a88e420ca8c0b7f) | Set the fill mode of substream image. |
| [setRemoteViewRotation:rotation:](https://www.tencentcloud.com/document/product/647/50761#ed42aceb4e9d1744e6ac70ad439fb16b) | Set the clockwise rotation angle of remote image. |
| [startRemoteSubStreamView:view:](https://www.tencentcloud.com/document/product/647/50761#6eb9faa4058a41b20c7d5b8c0aa53de1) | Start displaying the substream image of remote user. |
| [stopRemoteSubStreamView:](https://www.tencentcloud.com/document/product/647/50761#41c75d425b677dc5ff09647c8ee43d27) | Stop displaying the substream image of remote user. |
| [setRemoteSubStreamViewFillMode:mode:](https://www.tencentcloud.com/document/product/647/50761#b2f80cb608ce1720e9bdaf448892655f) | Set the fill mode of substream image. |
| [setRemoteSubStreamViewRotation:rotation:](https://www.tencentcloud.com/document/product/647/50761#3431170b2de05ae963ebf8aa0b13bd83) | Set the clockwise rotation angle of substream image. |
| [setAudioQuality:](https://www.tencentcloud.com/document/product/647/50761#832b250ba78f2a658c2b7c08158ffc0c) | Set sound quality. |
| [setPriorRemoteVideoStreamType:](https://www.tencentcloud.com/document/product/647/50761#d76890dfdadecedcc9dc550c6fe38150) | Specify whether to view the big or small image. |
| [setMicVolumeOnMixing:](https://www.tencentcloud.com/document/product/647/50761#db0db53a8bfbc95fbb2ea63e1990145b) | Set mic volume. |
| [playBGM:](https://www.tencentcloud.com/document/product/647/50761#eb9c7a858da39e49b4a74a8b3fafef38) | Start background music. |
| [stopBGM](https://www.tencentcloud.com/document/product/647/50761#4319eb495c02c29db1712125b670fcdb) | Stop background music. |
| [pauseBGM](https://www.tencentcloud.com/document/product/647/50761#8fb45f97ad885adb51014b8b92062942) | Stop background music. |
| [resumeBGM](https://www.tencentcloud.com/document/product/647/50761#78ba8c8703a0786f611a471fae61a37c) | Stop background music. |
| [getBGMDuration:](https://www.tencentcloud.com/document/product/647/50761#3ffc0b34262bce2fc94e72d2d716f91b) | Get the total length of background music in ms. |
| [setBGMPosition:](https://www.tencentcloud.com/document/product/647/50761#0c5b4075c9f86d7fff1687953b819737) | Set background music playback progress. |
| [setBGMVolume:](https://www.tencentcloud.com/document/product/647/50761#29eadcdde96838235ed8429d11315c5f) | Set background music volume. |
| [setBGMPlayoutVolume:](https://www.tencentcloud.com/document/product/647/50761#6a8735f21e964c42a12b7d38d3e2de6b) | Set the local playback volume of background music. |
| [setBGMPublishVolume:](https://www.tencentcloud.com/document/product/647/50761#1bd27db3143d97daa2b86e9f465eef37) | Set the remote playback volume of background music. |
| [playAudioEffect:](https://www.tencentcloud.com/document/product/647/50761#1b9ee24ee6ebadb1488c3782c12f2249) | Play sound effect. |
| [setAudioEffectVolume:volume:](https://www.tencentcloud.com/document/product/647/50761#82b0348e5e7c9b9a7d645d48563acf5d) | Set sound effect volume. |
| [stopAudioEffect:](https://www.tencentcloud.com/document/product/647/50761#d5d654919c44b5e6f48d07b515e3ea48) | Stop sound effect. |
| [stopAllAudioEffects](https://www.tencentcloud.com/document/product/647/50761#98de2296bd48b0929d840b309b3e14ed) | Stop all sound effects. |
| [setAllAudioEffectsVolume:](https://www.tencentcloud.com/document/product/647/50761#4c57e288b129ae8886967723b0626d1b) | Set the volume of all sound effects. |
| [pauseAudioEffect:](https://www.tencentcloud.com/document/product/647/50761#214666427b21be6dfb085c5ebc97cbba) | Pause sound effect. |
| [resumeAudioEffect:](https://www.tencentcloud.com/document/product/647/50761#f13ccd1c4f6ae592b5c7f525afb1c57b) | Pause sound effect. |
| [enableCustomVideoCapture:](https://www.tencentcloud.com/document/product/647/50761#12f1b2f312e5d43032d1cad5b7303f4d) | Enable custom video capturing mode. |
| [sendCustomVideoData:](https://www.tencentcloud.com/document/product/647/50761#128866342180b8603aca12504a4ed914) | Deliver captured video data to SDK. |
| [muteLocalVideo:](https://www.tencentcloud.com/document/product/647/50761#9f198fb8473d0543e58eb98df86a8bc3) | Pause/Resume publishing local video stream. |
| [muteRemoteVideoStream:mute:](https://www.tencentcloud.com/document/product/647/50761#9041c3c8a880d26e33bf359655872544) | Pause/Resume subscribing to remote user's video stream. |
| [startSpeedTest:userId:userSig:](https://www.tencentcloud.com/document/product/647/50761#0d97f8b1d422066b8c9aa0ea6cc88182) | Start network speed test (used before room entry). |
| [startScreenCapture:](https://www.tencentcloud.com/document/product/647/50761#c49358c276a8de60afea017fd3533f18) | Start screen sharing. |
| [getCameraDevicesList](https://www.tencentcloud.com/document/product/647/50761#050ebc21be36303e40ab52e4435485ca) | Get the list of cameras. |
| [setCurrentCameraDevice:](https://www.tencentcloud.com/document/product/647/50761#8481ef098d5ce50f936772e3899e43a8) | Set the camera to be used currently. |
| [getCurrentCameraDevice](https://www.tencentcloud.com/document/product/647/50761#b9040729b9f2b65bd9d469cad9afe731) | Get the currently used camera. |
| [getMicDevicesList](https://www.tencentcloud.com/document/product/647/50761#c1474cfccfdf19fd90367b09f0a82b60) | Get the list of mics. |
| [getCurrentMicDevice](https://www.tencentcloud.com/document/product/647/50761#3ad4425d47611eeef442951b639cb686) | Get the current mic device. |
| [setCurrentMicDevice:](https://www.tencentcloud.com/document/product/647/50761#f9930e21d8dfc58c573021d603fd2b47) | Select the currently used mic. |
| [getCurrentMicDeviceVolume](https://www.tencentcloud.com/document/product/647/50761#1d8ada14f76733c01ef751827b5e6c52) | Get the current mic volume. |
| [setCurrentMicDeviceVolume:](https://www.tencentcloud.com/document/product/647/50761#9ed1a4bc02037519fda57b3e5a5074fc) | Set the current mic volume. |
| [setCurrentMicDeviceMute:](https://www.tencentcloud.com/document/product/647/50761#baf06e64cbec81b576e138167567d99d) | Set the mute status of the current system mic. |
| [getCurrentMicDeviceMute](https://www.tencentcloud.com/document/product/647/50761#220fc1f4f36674fea3168094a33ba00e) | Get the mute status of the current system mic. |
| [getSpeakerDevicesList](https://www.tencentcloud.com/document/product/647/50761#e66b0ac9548b073030fda63666dd8e39) | Get the list of speakers. |
| [getCurrentSpeakerDevice](https://www.tencentcloud.com/document/product/647/50761#7725c908810967e9f9c9b883a939f495) | Get the currently used speaker. |
| [setCurrentSpeakerDevice:](https://www.tencentcloud.com/document/product/647/50761#b760134ab3e06eeaab0ade72a936f452) | Set the speaker to use. |
| [getCurrentSpeakerDeviceVolume](https://www.tencentcloud.com/document/product/647/50761#65944ea08b0a6ef40f5d34ce2e7c6a5e) | Get the current speaker volume. |
| [setCurrentSpeakerDeviceVolume:](https://www.tencentcloud.com/document/product/647/50761#27e08e0fd08c5c692e63eaad06628670) | Set the current speaker volume. |
| [getCurrentSpeakerDeviceMute](https://www.tencentcloud.com/document/product/647/50761#5fbafd1fc67b79c01588c845bc6235e6) | Get the mute status of the current system speaker. |
| [setCurrentSpeakerDeviceMute:](https://www.tencentcloud.com/document/product/647/50761#69754d7bebc7bb9cbb3754e4c885c8d2) | Set whether to mute the current system speaker. |
| [startCameraDeviceTestInView:](https://www.tencentcloud.com/document/product/647/50761#3eb24ed003130b68599fe70da766e990) | Start camera test. |
| [stopCameraDeviceTest](https://www.tencentcloud.com/document/product/647/50761#30849b027c0ea9fd008441d2a4855ccd) | Start camera test. |
| [startMicDeviceTest:](https://www.tencentcloud.com/document/product/647/50761#a0f6dd0090c31b53eb1f6e19dfe34c63) | Start mic test. |
| [stopMicDeviceTest](https://www.tencentcloud.com/document/product/647/50761#f3cafdaed3b7647f89331233b4d0cb3d) | Start mic test. |
| [startSpeakerDeviceTest:](https://www.tencentcloud.com/document/product/647/50761#052eaa08af995d24af07eb7bb0f29be0) | Start speaker test. |
| [stopSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50761#94f6ae0f7bd57db07c0f58e646b26532) | Stop speaker test. |
| [startScreenCaptureInApp:](https://www.tencentcloud.com/document/product/647/50761#b207016bb10d6309fb40bcb035f3002d) | start in-app screen sharing (for iOS 13.0 and above only). |
| [setVideoEncoderRotation:](https://www.tencentcloud.com/document/product/647/50761#7f0a336c82c6f1f42830f29950ea2c98) | Set the direction of image output by video encoder. |
| [setVideoEncoderMirror:](https://www.tencentcloud.com/document/product/647/50761#8cc992bacbb4f394aad0e6105319f904) | Set the mirror mode of image output by encoder. |
| [setGSensorMode:](https://www.tencentcloud.com/document/product/647/50761#f08dca7422d56f7fd65262f2555c3c80) | Set the adaptation mode of G-sensor. |
| [startPublishing:type:](https://www.tencentcloud.com/document/product/647/50761#c696e4090dd9955ce2a46ee90a9aa114) | Start publishing audio/video streams to Tencent Cloud CSS CDN. |
| [stopPublishing](https://www.tencentcloud.com/document/product/647/50761#01db8b83a50fb08419ddcd058cc33151) | Stop publishing audio/video streams to Tencent Cloud CSS CDN. |
| [startPublishCDNStream:](https://www.tencentcloud.com/document/product/647/50761#855bb18efbb634d680052712824e25f3) | Start publishing audio/video streams to non-Tencent Cloud CDN. |
| [stopPublishCDNStream](https://www.tencentcloud.com/document/product/647/50761#25e9323437b31d9d7d41f6954249932f) | Stop publishing audio/video streams to non-Tencent Cloud CDN. |
| [setMixTranscodingConfig:](https://www.tencentcloud.com/document/product/647/50761#aa69121443ba408f9f3eb35cdc51ebb9) | Set the layout and transcoding parameters of On-Cloud MixTranscoding. |

## destroySharedIntance

**destroySharedIntance**

**Terminate TRTCCloud instance (singleton mode).**

@deprecated This API is not recommended after 11.5 Please use [destroySharedInstance](https://www.tencentcloud.com/document/product/647/50754#efdff42059de072cfccbb4fcf1bc9646) instead.

## delegate

**delegate**

**Set TRTC event callback.**

@deprecated This API is not recommended after v11.4 Please use [addDelegate](https://www.tencentcloud.com/document/product/647/50754#e227a9126fee9a548fec6d0051326ffc) instead.

## setBeautyStyle:beautyLevel:whitenessLevel:ruddinessLevel:

**setBeautyStyle:beautyLevel:whitenessLevel:ruddinessLevel:**

| - (void)setBeautyStyle: | ([TRTCBeautyStyle](https://www.tencentcloud.com/document/product/647/50760#a857e9ef306856452de13b60a170e310))beautyStyle |
| --- | --- |
| beautyLevel: | (NSInteger)beautyLevel |
| whitenessLevel: | (NSInteger)whitenessLevel |
| ruddinessLevel: | (NSInteger)ruddinessLevel |

**Set the strength of beauty, brightening, and rosy skin filters.**

@deprecated This API is not recommended after v6.9. Please use [setBeautyStyle](https://www.tencentcloud.com/document/product/647/50758#89215cdfd5905aa81993b53b8c6b66be), [setBeautyLevel](https://www.tencentcloud.com/document/product/647/50758#b5fedd8ce52caee75365c967a92b08e4), [setWhitenessLevel](https://www.tencentcloud.com/document/product/647/50758#6e5243ac8d73b038a9c603a3ee7f7e38), [setRuddyLevel](https://www.tencentcloud.com/document/product/647/50758#821ebd8ee9c03f1b5e5ae77121cc61c3) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setEyeScaleLevel:

**setEyeScaleLevel:**

| - (void)setEyeScaleLevel: | (float)eyeScaleLevel |
| --- | --- |

**Set the strength of eye enlarging filter.**

@deprecated This API is not recommended after v6.9. Please use [setEyeScaleLevel](https://www.tencentcloud.com/document/product/647/50758#2bf78eafcb88db8fdd9398eb4011619b) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setFaceScaleLevel:

**setFaceScaleLevel:**

| - (void)setFaceScaleLevel: | (float)faceScaleLevel |
| --- | --- |

**Set the strength of face slimming filter.**

@deprecated This API is not recommended after v6.9. Please use [setFaceSlimLevel](https://www.tencentcloud.com/document/product/647/50758#da3ed5adfa61941f1a11adc9938e9ba5) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setFaceVLevel:

**setFaceVLevel:**

| - (void)setFaceVLevel: | (float)faceVLevel |
| --- | --- |

**Set the strength of chin slimming filter.**

@deprecated This API is not recommended after v6.9. Please use [setFaceVLevel](https://www.tencentcloud.com/document/product/647/50758#8350cda9b6a217967d8274cc39ccc6e6) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setChinLevel:

**setChinLevel:**

| - (void)setChinLevel: | (float)chinLevel |
| --- | --- |

**Set the strength of chin lengthening/shortening filter.**

@deprecated This API is not recommended after v6.9. Please use [setChinLevel](https://www.tencentcloud.com/document/product/647/50758#c3a377df9b943cbb361e87e2c9c7c47d) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setFaceShortLevel:

**setFaceShortLevel:**

| - (void)setFaceShortLevel: | (float)faceShortlevel |
| --- | --- |

**Set the strength of face shortening filter.**

@deprecated This API is not recommended after v6.9. Please use [setFaceShortLevel](https://www.tencentcloud.com/document/product/647/50758#98f562ff406656d9808f5a830403f301) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setNoseSlimLevel:

**setNoseSlimLevel:**

| - (void)setNoseSlimLevel: | (float)noseSlimLevel |
| --- | --- |

**Set the strength of nose slimming filter.**

@deprecated This API is not recommended after v6.9. Please use [setNoseSlimLevel](https://www.tencentcloud.com/document/product/647/50758#15b40583cade49e0487647d7f5c26d7c) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## selectMotionTmpl:

**selectMotionTmpl:**

| - (void)selectMotionTmpl: | (NSString *)tmplPath |
| --- | --- |

**Set animated sticker.**

@deprecated This API is not recommended after v6.9. Please use [setMotionTmpl](https://www.tencentcloud.com/document/product/647/50758#7f66b71987061e914cdfc9f756d3b762) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setMotionMute:

**setMotionMute:**

| - (void)setMotionMute: | (BOOL)motionMute |
| --- | --- |

**Mute animated sticker.**

@deprecated This API is not recommended after v6.9. Please use [setMotionMute](https://www.tencentcloud.com/document/product/647/50758#3146072ddea1c320588b1a27bc8bff2e) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setFilter:

**setFilter:**

| - (void)setFilter: | (TXImage *)image |
| --- | --- |

**Set color filter.**

@deprecated This API is not recommended after v7.2. Please use [setFilter](https://www.tencentcloud.com/document/product/647/50758#f73520b36361749d3f59eeb6db50f940) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setFilterConcentration:

**setFilterConcentration:**

| - (void)setFilterConcentration: | (float)concentration |
| --- | --- |

**Set the strength of color filter.**

@deprecated This API is not recommended after v7.2. Please use [setFilterStrength](https://www.tencentcloud.com/document/product/647/50758#4115cda15fa0692c38d1fe4b825a8b81) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setGreenScreenFile:

**setGreenScreenFile:**

| - (void)setGreenScreenFile: | (NSURL *)file |
| --- | --- |

**Set green screen video.**

@deprecated This API is not recommended after v7.2. Please use [setGreenScreenFile](https://www.tencentcloud.com/document/product/647/50758#c161a410f89d9f10e10dad0f1aaa6cf7) API in [TXBeautyManager](https://www.tencentcloud.com/document/product/647/50758#9daae44d04e17beffd5200fd4e5ef252) instead.

## setReverbType:

**setReverbType:**

| - (void)setReverbType: | ([TRTCReverbType](https://www.tencentcloud.com/document/product/647/50760#f05ef898bf85025319186e44001413a5))reverbType |
| --- | --- |

**Set reverb effect.**

@deprecated This API is not recommended after v7.3. Please use [setVoiceReverbType](https://www.tencentcloud.com/document/product/647/50757#7135a441f275bed8330db039f1bfba2d) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## setVoiceChangerType:

**setVoiceChangerType:**

| - (void)setVoiceChangerType: | ([TRTCVoiceChangerType](https://www.tencentcloud.com/document/product/647/50760#0627489c54a24f108242928ec434e424))voiceChangerType |
| --- | --- |

**Set voice changing type.**

@deprecated This API is not recommended after v7.3. Please use [setVoiceChangerType](https://www.tencentcloud.com/document/product/647/50757#fee0da19f6060c0544e73a79da113bd0) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## enableAudioEarMonitoring:

**enableAudioEarMonitoring:**

| - (void)enableAudioEarMonitoring: | (BOOL)enable |
| --- | --- |

**Enable or disable in-ear monitoring.**

@deprecated This API is not recommended after v7.3. Please use [setVoiceEarMonitor](https://www.tencentcloud.com/document/product/647/50757#3857607a3e9b5fc2e57a77f2c1dd6359) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## enableAudioVolumeEvaluation:

**enableAudioVolumeEvaluation:**

| - (void)enableAudioVolumeEvaluation: | (NSUInteger)interval |
| --- | --- |

**Enable volume reminder.**

@deprecated This API is not recommended after v10.1. Please use [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50754#b8cb5a5ac09c8e46fcdf98f0acb2e792)(enable, params) instead.

## enableAudioVolumeEvaluation:enable_vad:

**enableAudioVolumeEvaluation:enable_vad:**

| - (void)enableAudioVolumeEvaluation: | (NSUInteger)interval |
| --- | --- |
| enable_vad: | (BOOL)enable_vad |

**Enable volume reminder.**

@deprecated This API is not recommended after v11.2. Please use [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50754#b8cb5a5ac09c8e46fcdf98f0acb2e792)(enable, params) instead.

## switchCamera

**switchCamera**

**Switch camera.**

@deprecated This API is not recommended after v8.0. Please use the [switchCamera](https://www.tencentcloud.com/document/product/647/50759#a6c41b29145df78c75f83db394a5757d) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## isCameraZoomSupported

**isCameraZoomSupported**

**Query whether the current camera supports zoom.**

@deprecated This API is not recommended after v8.0. Please use the [isCameraZoomSupported](https://www.tencentcloud.com/document/product/647/50759#3d221dfef2379ff2d7465873b190d279) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setZoom:

**setZoom:**

| - (void)setZoom: | (CGFloat)distance |
| --- | --- |

**Set camera zoom ratio (focal length).**

@deprecated This API is not recommended after v8.0. Please use the [setCameraZoomRatio](https://www.tencentcloud.com/document/product/647/50759#aa61befc4a161b72e2a3eb9703e8ab8a) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## isCameraTorchSupported

**isCameraTorchSupported**

**Query whether the device supports flash.**

@deprecated This API is not recommended after v8.0. Please use the [isCameraTorchSupported](https://www.tencentcloud.com/document/product/647/50759#0f67ffd852a08dc7735f51d3b3f0f163) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## enbaleTorch:

**enbaleTorch:**

| - (BOOL)enbaleTorch: | (BOOL)enable |
| --- | --- |

**Enable/Disable flash.**

@deprecated This API is not recommended after v8.0. Please use the [enableCameraTorch](https://www.tencentcloud.com/document/product/647/50759#bf86fe99b08324c7114c2da6875baca9) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## isCameraFocusPositionInPreviewSupported

**isCameraFocusPositionInPreviewSupported**

**Query whether the camera supports setting focus.**

@deprecated This API is not recommended after v8.0.

## setFocusPosition:

**setFocusPosition:**

| - (void)setFocusPosition: | (CGPoint)touchPoint |
| --- | --- |

**Set the focal position of camera.**

@deprecated This API is not recommended after v8.0. Please use the [setCameraFocusPosition](https://www.tencentcloud.com/document/product/647/50759#2f2ceca9ad0f46650334e6b5aa813633) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## isCameraAutoFocusFaceModeSupported

**isCameraAutoFocusFaceModeSupported**

**Query whether the device supports the automatic recognition of face position.**

@deprecated This API is not recommended after v8.0. Please use the [isAutoFocusEnabled](https://www.tencentcloud.com/document/product/647/50759#a8d8a4fa66b628c21a080177204744b2) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## enableAutoFaceFoucs:

**enableAutoFaceFoucs:**

| - (void)enableAutoFaceFoucs: | (BOOL)enable |
| --- | --- |

**Enable/Disable face auto focus.**

@deprecated This API is not recommended after v8.0. Please use the [enableCameraAutoFocus](https://www.tencentcloud.com/document/product/647/50759#b73d99629f1936b786b6ada790e458dd) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setSystemVolumeType:

**setSystemVolumeType:**

| - (void)setSystemVolumeType: | ([TRTCSystemVolumeType](https://www.tencentcloud.com/document/product/647/50760#231e219e2864cf7145620089c6321c8e))type |
| --- | --- |

**Setting the system volume type (for mobile OS).**

@deprecated This API is not recommended after v8.0. Please use the [startLocalAudio](https://www.tencentcloud.com/document/product/647/50754#df3c633d8a6277d5271813f9fac58cb9) instead, which param ` quality ` is used to decide audio quality.

## snapshotVideo:type:

**snapshotVideo:type:**

| - (void)snapshotVideo: | (NSString *)userId |
| --- | --- |
| type: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |

**Screencapture video.**

@deprecated This API is not recommended after v8.2. Please use [snapshotVideo](https://www.tencentcloud.com/document/product/647/50754#732e96881714e8af4872df0309b1d65b) instead.

## startScreenCaptureByReplaykit:appGroup:

**startScreenCaptureByReplaykit:appGroup:**

| - (void)startScreenCaptureByReplaykit: | ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e) *)encParams |
| --- | --- |
| appGroup: | (NSString *)appGroup |

**Start system-level screen sharing (for iOS 11.0 and above only).**

@deprecated This API is not recommended after v8.6. Please use [startScreenCaptureByReplaykit](https://www.tencentcloud.com/document/product/647/50754#a40e37e782a049150b3314810516bf44) instead.

## startLocalAudio

**startLocalAudio**

**Set sound quality.**

@deprecated This API is not recommended after v8.0. Please use [startLocalAudio](https://www.tencentcloud.com/document/product/647/50754#df3c633d8a6277d5271813f9fac58cb9):quality instead.

## startRemoteView:view:

**startRemoteView:view:**

| - (void)startRemoteView: | (NSString *)userId |
| --- | --- |
| view: | (TXView *)view |

**Start displaying remote video image.**

@deprecated This API is not recommended after v8.0. Please use [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3):streamType:view: instead.

## stopRemoteView:

**stopRemoteView:**

| - (void)stopRemoteView: | (NSString *)userId |
| --- | --- |

**Stop displaying remote video image and pulling the video data stream of remote user.**

@deprecated This API is not recommended after v8.0. Please use [stopRemoteView](https://www.tencentcloud.com/document/product/647/50754#a6aaf8745d8ecbc6b7d7fa3131338eb5):streamType: instead.

## setLocalViewFillMode:

**setLocalViewFillMode:**

| - (void)setLocalViewFillMode: | ([TRTCVideoFillMode](https://www.tencentcloud.com/document/product/647/50760#2404025cdb7d006f20648beefffbc893))mode |
| --- | --- |

**Set the rendering mode of local image.**

@deprecated This API is not recommended after v8.0. Please use [setLocalRenderParams](https://www.tencentcloud.com/document/product/647/50754#d32d9dde71a2485a76223d003d95c082) instead.

## setLocalViewRotation:

**setLocalViewRotation:**

| - (void)setLocalViewRotation: | ([TRTCVideoRotation](https://www.tencentcloud.com/document/product/647/50760#3a45499a02ba68182709073cc7e29b4c))rotation |
| --- | --- |

**Set the clockwise rotation angle of local image.**

@deprecated This API is not recommended after v8.0. Please use [setLocalRenderParams](https://www.tencentcloud.com/document/product/647/50754#d32d9dde71a2485a76223d003d95c082) instead.

## setLocalViewMirror:

**setLocalViewMirror:**

| - (void)setLocalViewMirror: | (TRTCLocalVideoMirrorType)mirror |
| --- | --- |

**Set the mirror mode of local camera's preview image.**

@deprecated This API is not recommended after v8.0. Please use [setLocalRenderParams](https://www.tencentcloud.com/document/product/647/50754#d32d9dde71a2485a76223d003d95c082) instead.

## setRemoteViewFillMode:mode:

**setRemoteViewFillMode:mode:**

| - (void)setRemoteViewFillMode: | (NSString*)userId |
| --- | --- |
| mode: | ([TRTCVideoFillMode](https://www.tencentcloud.com/document/product/647/50760#2404025cdb7d006f20648beefffbc893))mode |

**Set the fill mode of substream image.**

@deprecated This API is not recommended after v8.0. Please use [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50754#8a2b406ea2817c2feb2336d92eb7af20):streamType:params: instead.

## setRemoteViewRotation:rotation:

**setRemoteViewRotation:rotation:**

| - (void)setRemoteViewRotation: | (NSString*)userId |
| --- | --- |
| rotation: | ([TRTCVideoRotation](https://www.tencentcloud.com/document/product/647/50760#3a45499a02ba68182709073cc7e29b4c))rotation |

**Set the clockwise rotation angle of remote image.**

@deprecated This API is not recommended after v8.0. Please use [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50754#8a2b406ea2817c2feb2336d92eb7af20):streamType:params: instead.

## startRemoteSubStreamView:view:

**startRemoteSubStreamView:view:**

| - (void)startRemoteSubStreamView: | (NSString *)userId |
| --- | --- |
| view: | (TXView *)view |

**Start displaying the substream image of remote user.**

@deprecated This API is not recommended after v8.0. Please use [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3):streamType:view: instead.

## stopRemoteSubStreamView:

**stopRemoteSubStreamView:**

| - (void)stopRemoteSubStreamView: | (NSString *)userId |
| --- | --- |

**Stop displaying the substream image of remote user.**

@deprecated This API is not recommended after v8.0. Please use [stopRemoteView](https://www.tencentcloud.com/document/product/647/50754#a6aaf8745d8ecbc6b7d7fa3131338eb5):streamType: instead.

## setRemoteSubStreamViewFillMode:mode:

**setRemoteSubStreamViewFillMode:mode:**

| - (void)setRemoteSubStreamViewFillMode: | (NSString *)userId |
| --- | --- |
| mode: | ([TRTCVideoFillMode](https://www.tencentcloud.com/document/product/647/50760#2404025cdb7d006f20648beefffbc893))mode |

**Set the fill mode of substream image.**

@deprecated This API is not recommended after v8.0. Please use [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50754#8a2b406ea2817c2feb2336d92eb7af20):streamType:params: instead.

## setRemoteSubStreamViewRotation:rotation:

**setRemoteSubStreamViewRotation:rotation:**

| - (void)setRemoteSubStreamViewRotation: | (NSString*)userId |
| --- | --- |
| rotation: | ([TRTCVideoRotation](https://www.tencentcloud.com/document/product/647/50760#3a45499a02ba68182709073cc7e29b4c))rotation |

**Set the clockwise rotation angle of substream image.**

@deprecated This API is not recommended after v8.0. Please use [setRemoteRenderParams](https://www.tencentcloud.com/document/product/647/50754#8a2b406ea2817c2feb2336d92eb7af20):streamType:params: instead.

## setAudioQuality:

**setAudioQuality:**

| - (void)setAudioQuality: | ([TRTCAudioQuality](https://www.tencentcloud.com/document/product/647/50760#f8aeb89d8ef78db15d893e55f68cdb42))quality |
| --- | --- |

**Set sound quality.**

@deprecated This API is not recommended after v8.0. Please use [startLocalAudio](https://www.tencentcloud.com/document/product/647/50754#df3c633d8a6277d5271813f9fac58cb9):quality instead.

## setPriorRemoteVideoStreamType:

**setPriorRemoteVideoStreamType:**

| - (void)setPriorRemoteVideoStreamType: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |
| --- | --- |

**Specify whether to view the big or small image.**

@deprecated This API is not recommended after v8.0. Please use [startRemoteView](https://www.tencentcloud.com/document/product/647/50754#027af371d7ba5aa8bfb6c61ab09a5ba3):streamType:view: instead.

## setMicVolumeOnMixing:

**setMicVolumeOnMixing:**

| - (void)setMicVolumeOnMixing: | (NSInteger)volume |
| --- | --- |

**Set mic volume.**

@deprecated This API is not recommended after v6.9. Please use [setAudioCaptureVolume](https://www.tencentcloud.com/document/product/647/50754#7b85cce8049a984394c664b787394895) instead.

## playBGM:

**playBGM:**

| - (void) playBGM: | (NSString *)path |
| --- | --- |

**Start background music.**

@deprecated This API is not recommended after v7.3. Please use [startPlayMusic](https://www.tencentcloud.com/document/product/647/50757#3e6d92e47d6770c50e0e4ca4df429c31) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## stopBGM

**stopBGM**

**Stop background music.**

@deprecated This API is not recommended after v7.3. Please use [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50757#2214eecbdca5062136821aff0d95bfbe) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## pauseBGM

**pauseBGM**

**Stop background music.**

@deprecated This API is not recommended after v7.3. Please use [pausePlayMusic](https://www.tencentcloud.com/document/product/647/50757#8e5076dea4c4b43df4c07cf1fe4003f1) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## resumeBGM

**resumeBGM**

**Stop background music.**

@deprecated This API is not recommended after v7.3. Please use [resumePlayMusic](https://www.tencentcloud.com/document/product/647/50757#15f5b80077c596dc1d39402d421a6ec2) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## getBGMDuration:

**getBGMDuration:**

| - (NSInteger)getBGMDuration: | (NSString *)path |
| --- | --- |

**Get the total length of background music in ms.**

@deprecated This API is not recommended after v7.3. Please use [getMusicDurationInMS](https://www.tencentcloud.com/document/product/647/50757#6ca86334e6bf179bc3cfd98ca5e01975) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## setBGMPosition:

**setBGMPosition:**

| - (int)setBGMPosition: | (NSInteger)pos |
| --- | --- |

**Set background music playback progress.**

@deprecated This API is not recommended after v7.3. Please use [seekMusicToPosInMS](https://www.tencentcloud.com/document/product/647/50757#c00ed7c5735f4c126f0fbd099cae8998) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## setBGMVolume:

**setBGMVolume:**

| - (void)setBGMVolume: | (NSInteger)volume |
| --- | --- |

**Set background music volume.**

@deprecated This API is not recommended after v7.3. Please use setMusicVolume API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## setBGMPlayoutVolume:

**setBGMPlayoutVolume:**

| - (void)setBGMPlayoutVolume: | (NSInteger)volume |
| --- | --- |

**Set the local playback volume of background music.**

@deprecated This API is not recommended after v7.3. Please use [setMusicPlayoutVolume](https://www.tencentcloud.com/document/product/647/50757#5ba979d09b84dfe360785c659ab7c8b7) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## setBGMPublishVolume:

**setBGMPublishVolume:**

| - (void)setBGMPublishVolume: | (NSInteger)volume |
| --- | --- |

**Set the remote playback volume of background music.**

@deprecated This API is not recommended after v7.3. Please use setBGMPublishVolume API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## playAudioEffect:

**playAudioEffect:**

| - (void)playAudioEffect: | ([TRTCAudioEffectParam](https://www.tencentcloud.com/document/product/647/50760#1c578ca937d9382447e381be8a4b8f94)*)effect |
| --- | --- |

**Play sound effect.**

@deprecated This API is not recommended after v7.3. Please use [startPlayMusic](https://www.tencentcloud.com/document/product/647/50757#3e6d92e47d6770c50e0e4ca4df429c31) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## setAudioEffectVolume:volume:

**setAudioEffectVolume:volume:**

| - (void)setAudioEffectVolume: | (int)effectId |
| --- | --- |
| volume: | (int) volume |

**Set sound effect volume.**

@deprecated This API is not recommended after v7.3. Please use [setMusicPublishVolume](https://www.tencentcloud.com/document/product/647/50757#50a9fe2dc5ee4a6f92160ef4f1367c13) and [setMusicPlayoutVolume](https://www.tencentcloud.com/document/product/647/50757#5ba979d09b84dfe360785c659ab7c8b7) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## stopAudioEffect:

**stopAudioEffect:**

| - (void)stopAudioEffect: | (int)effectId |
| --- | --- |

**Stop sound effect.**

@deprecated This API is not recommended after v7.3. Please use [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50757#2214eecbdca5062136821aff0d95bfbe) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## stopAllAudioEffects

**stopAllAudioEffects**

**Stop all sound effects.**

@deprecated This API is not recommended after v7.3. Please use [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50757#2214eecbdca5062136821aff0d95bfbe) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## setAllAudioEffectsVolume:

**setAllAudioEffectsVolume:**

| - (void)setAllAudioEffectsVolume: | (int)volume |
| --- | --- |

**Set the volume of all sound effects.**

@deprecated This API is not recommended after v7.3. Please use [setMusicPublishVolume](https://www.tencentcloud.com/document/product/647/50757#50a9fe2dc5ee4a6f92160ef4f1367c13) and [setMusicPlayoutVolume](https://www.tencentcloud.com/document/product/647/50757#5ba979d09b84dfe360785c659ab7c8b7) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## pauseAudioEffect:

**pauseAudioEffect:**

| - (void)pauseAudioEffect: | (int)effectId |
| --- | --- |

**Pause sound effect.**

@deprecated This API is not recommended after v7.3. Please use pauseAudioEffect API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## resumeAudioEffect:

**resumeAudioEffect:**

| - (void)resumeAudioEffect: | (int)effectId |
| --- | --- |

**Pause sound effect.**

@deprecated This API is not recommended after v7.3. Please use [resumePlayMusic](https://www.tencentcloud.com/document/product/647/50757#15f5b80077c596dc1d39402d421a6ec2) API in [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50757#ea6e3f1c4c7bf63cba47cf67f5e066d7) instead.

## enableCustomVideoCapture:

**enableCustomVideoCapture:**

| - (void)enableCustomVideoCapture: | (BOOL)enable |
| --- | --- |

**Enable custom video capturing mode.**

@deprecated This API is not recommended after v8.5. Please use [enableCustomVideoCapture](https://www.tencentcloud.com/document/product/647/50754#e404d58245ffc8acdaef99a19bb3795c) instead.

## sendCustomVideoData:

**sendCustomVideoData:**

| - (void)sendCustomVideoData: | ([TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50760#9233a1b1573333abc70e53b51bd89740) *)frame |
| --- | --- |

**Deliver captured video data to SDK.**

@deprecated This API is not recommended after v8.5. Please use [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/50754#2ec8cee427b69adc1b75be389c7eaef7) instead.

## muteLocalVideo:

**muteLocalVideo:**

| - (void)muteLocalVideo: | (BOOL)mute |
| --- | --- |

**Pause/Resume publishing local video stream.**

@deprecated This API is not recommended after v8.9. Please use [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50754#dd2e6e6669e44947ac869fa038462588) (streamType, mute) instead.

## muteRemoteVideoStream:mute:

**muteRemoteVideoStream:mute:**

| - (void)muteRemoteVideoStream: | (NSString*)userId |
| --- | --- |
| mute: | (BOOL)mute |

**Pause/Resume subscribing to remote user's video stream.**

@deprecated This API is not recommended after v8.9. Please use [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/50754#b2d1898fc13a9583f8317cf3d9d40837) (userId, streamType, mute) instead.

## startSpeedTest:userId:userSig:

**startSpeedTest:userId:userSig:**

| - (void)startSpeedTest: | (uint32_t)sdkAppId |
| --- | --- |
| userId: | (NSString *)userId |
| userSig: | (NSString *)userSig |

**Start network speed test (used before room entry).**

@deprecated This API is not recommended after v9.2. Please use [startSpeedTest](https://www.tencentcloud.com/document/product/647/50754#9446ef81737de395b79baa311622f04e) (params) instead.

## startScreenCapture:

**startScreenCapture:**

| - (void)startScreenCapture: | (nullable NSView *)view |
| --- | --- |

**Start screen sharing.**

@deprecated This API is not recommended after v7.2. Please use ` startScreenCapture:streamType:encParam: ` instead.

## getCameraDevicesList

**getCameraDevicesList**

**Get the list of cameras.**

@deprecated This API is not recommended after v8.0. Please use the [getDevicesList](https://www.tencentcloud.com/document/product/647/50759#cf4514b579d88cadae56a424baeb110f) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setCurrentCameraDevice:

**setCurrentCameraDevice:**

| - (int)setCurrentCameraDevice: | (NSString *)deviceId |
| --- | --- |

**Set the camera to be used currently.**

@deprecated This API is not recommended after v8.0. Please use the [setCurrentDevice](https://www.tencentcloud.com/document/product/647/50759#1c0a01aa96ce0aa6c596c654041fbee6) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getCurrentCameraDevice

**getCurrentCameraDevice**

**Get the currently used camera.**

@deprecated This API is not recommended after v8.0. Please use the [getCurrentDevice](https://www.tencentcloud.com/document/product/647/50759#c56fd31ac73ceda8a28d9f4bfe834bbd) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getMicDevicesList

**getMicDevicesList**

**Get the list of mics.**

@deprecated This API is not recommended after v8.0. Please use the [getDevicesList](https://www.tencentcloud.com/document/product/647/50759#cf4514b579d88cadae56a424baeb110f) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getCurrentMicDevice

**getCurrentMicDevice**

**Get the current mic device.**

@deprecated This API is not recommended after v8.0. Please use the [getCurrentDevice](https://www.tencentcloud.com/document/product/647/50759#c56fd31ac73ceda8a28d9f4bfe834bbd) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setCurrentMicDevice:

**setCurrentMicDevice:**

| - (int)setCurrentMicDevice: | (NSString*)deviceId |
| --- | --- |

**Select the currently used mic.**

@deprecated This API is not recommended after v8.0. Please use the [setCurrentDevice](https://www.tencentcloud.com/document/product/647/50759#1c0a01aa96ce0aa6c596c654041fbee6) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getCurrentMicDeviceVolume

**getCurrentMicDeviceVolume**

**Get the current mic volume.**

@deprecated This API is not recommended after v8.0. Please use the [getCurrentDeviceVolume](https://www.tencentcloud.com/document/product/647/50759#1fc1b55bc7722cc70a07302e46507467) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setCurrentMicDeviceVolume:

**setCurrentMicDeviceVolume:**

| - (void)setCurrentMicDeviceVolume: | (NSInteger)volume |
| --- | --- |

**Set the current mic volume.**

@deprecated This API is not recommended after v8.0. Please use the [setCurrentDeviceVolume](https://www.tencentcloud.com/document/product/647/50759#aefc135c5b1cf942a4d7445274fa2465) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setCurrentMicDeviceMute:

**setCurrentMicDeviceMute:**

| - (void)setCurrentMicDeviceMute: | (BOOL)mute |
| --- | --- |

**Set the mute status of the current system mic.**

@deprecated This API is not recommended after v8.0. Please use the [setCurrentDeviceMute](https://www.tencentcloud.com/document/product/647/50759#647a252eb815bae8854023af3717a79f) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getCurrentMicDeviceMute

**getCurrentMicDeviceMute**

**Get the mute status of the current system mic.**

@deprecated This API is not recommended after v8.0. Please use the [getCurrentDeviceMute](https://www.tencentcloud.com/document/product/647/50759#7b46a3e3052b4b59e685fb8365c3955d) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getSpeakerDevicesList

**getSpeakerDevicesList**

**Get the list of speakers.**

@deprecated This API is not recommended after v8.0. Please use the [getDevicesList](https://www.tencentcloud.com/document/product/647/50759#cf4514b579d88cadae56a424baeb110f) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getCurrentSpeakerDevice

**getCurrentSpeakerDevice**

**Get the currently used speaker.**

@deprecated This API is not recommended after v8.0. Please use the [getCurrentDevice](https://www.tencentcloud.com/document/product/647/50759#c56fd31ac73ceda8a28d9f4bfe834bbd) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setCurrentSpeakerDevice:

**setCurrentSpeakerDevice:**

| - (int)setCurrentSpeakerDevice: | (NSString*)deviceId |
| --- | --- |

**Set the speaker to use.**

@deprecated This API is not recommended after v8.0. Please use the [setCurrentDevice](https://www.tencentcloud.com/document/product/647/50759#1c0a01aa96ce0aa6c596c654041fbee6) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getCurrentSpeakerDeviceVolume

**getCurrentSpeakerDeviceVolume**

**Get the current speaker volume.**

@deprecated This API is not recommended after v8.0. Please use the [getCurrentDeviceVolume](https://www.tencentcloud.com/document/product/647/50759#1fc1b55bc7722cc70a07302e46507467) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setCurrentSpeakerDeviceVolume:

**setCurrentSpeakerDeviceVolume:**

| - (int)setCurrentSpeakerDeviceVolume: | (NSInteger)volume |
| --- | --- |

**Set the current speaker volume.**

@deprecated This API is not recommended after v8.0. Please use the [setCurrentDeviceVolume](https://www.tencentcloud.com/document/product/647/50759#aefc135c5b1cf942a4d7445274fa2465) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## getCurrentSpeakerDeviceMute

**getCurrentSpeakerDeviceMute**

**Get the mute status of the current system speaker.**

@deprecated This API is not recommended after v8.0. Please use the [getCurrentDeviceMute](https://www.tencentcloud.com/document/product/647/50759#7b46a3e3052b4b59e685fb8365c3955d) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## setCurrentSpeakerDeviceMute:

**setCurrentSpeakerDeviceMute:**

| - (void)setCurrentSpeakerDeviceMute: | (BOOL)mute |
| --- | --- |

**Set whether to mute the current system speaker.**

@deprecated This API is not recommended after v8.0. Please use the [setCurrentDeviceMute](https://www.tencentcloud.com/document/product/647/50759#647a252eb815bae8854023af3717a79f) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## startCameraDeviceTestInView:

**startCameraDeviceTestInView:**

| - (void)startCameraDeviceTestInView: | (NSView *)view |
| --- | --- |

**Start camera test.**

@deprecated This API is not recommended after v8.0. Please use the [startCameraDeviceTest](https://www.tencentcloud.com/document/product/647/50759#e2d8e209071fef8bbf78f16971bae39f) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## stopCameraDeviceTest

**stopCameraDeviceTest**

**Start camera test.**

@deprecated This API is not recommended after v8.0. Please use the [stopCameraDeviceTest](https://www.tencentcloud.com/document/product/647/50759#30be4cfa94699be138130c1919b3af68) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## startMicDeviceTest:

**startMicDeviceTest:**

| - (void)startMicDeviceTest: | (NSInteger)interval |
| --- | --- |

**Start mic test.**

@deprecated This API is not recommended after v8.0. Please use the [startMicDeviceTest](https://www.tencentcloud.com/document/product/647/50759#3dce7bfcf95708a5ce69f5ce7baad6f4) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## stopMicDeviceTest

**stopMicDeviceTest**

**Start mic test.**

@deprecated This API is not recommended after v8.0. Please use the [stopMicDeviceTest](https://www.tencentcloud.com/document/product/647/50759#d0adbc1fbeae9620cf4c78d06b24d26e) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## startSpeakerDeviceTest:

**startSpeakerDeviceTest:**

| - (void)startSpeakerDeviceTest: | (NSString*)audioFilePath |
| --- | --- |

**Start speaker test.**

@deprecated This API is not recommended after v8.0. Please use the [startSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50759#e4ac7cc2a6dbecee30b0b4a9a17ce3b3) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## stopSpeakerDeviceTest

**stopSpeakerDeviceTest**

**Stop speaker test.**

@deprecated This API is not recommended after v8.0. Please use the [stopSpeakerDeviceTest](https://www.tencentcloud.com/document/product/647/50759#d9f52ca878aa99ec873170b4bc394f11) API in [TXDeviceManager](https://www.tencentcloud.com/document/product/647/50759#4ee7488c52213893527b2f5ce26a05c1) instead.

## startScreenCaptureInApp:

**startScreenCaptureInApp:**

| - (void)startScreenCaptureInApp: | ([TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/50760#b5beabfeefb812ccf1060aea67185c4e) *)encParams |
| --- | --- |

**start in-app screen sharing (for iOS 13.0 and above only).**

@deprecated This API is not recommended after v8.6. Please use [startScreenCaptureInApp](https://www.tencentcloud.com/document/product/647/50754#da3b9c66508d3f7a02a9e9a5319ee194) instead.

## setVideoEncoderRotation:

**setVideoEncoderRotation:**

| - (void)setVideoEncoderRotation: | ([TRTCVideoRotation](https://www.tencentcloud.com/document/product/647/50760#3a45499a02ba68182709073cc7e29b4c))rotation |
| --- | --- |

**Set the direction of image output by video encoder.**

@deprecated It is deprecated starting from v11.7.

## setVideoEncoderMirror:

**setVideoEncoderMirror:**

| - (void)setVideoEncoderMirror: | (BOOL)mirror |
| --- | --- |

**Set the mirror mode of image output by encoder.**

@deprecated It is deprecated starting from v11.7.

## setGSensorMode:

**setGSensorMode:**

| - (void)setGSensorMode: | ([TRTCGSensorMode](https://www.tencentcloud.com/document/product/647/50760#ffa70aea3ac0ccf4d5b8922eddd76b8d)) mode |
| --- | --- |

**Set the adaptation mode of G-sensor.**

@deprecated It is deprecated starting from v11.7. It is recommended to use the [setGravitySensorAdaptiveMode](https://www.tencentcloud.com/document/product/647/50754#790bcd4a0b0848f0cd3e2fe903d4ad89) interface instead.

## startPublishing:type:

**startPublishing:type:**

| - (void)startPublishing: | (NSString *)streamId |
| --- | --- |
| type: | ([TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/50760#50d8d09e9837560e2946e7b187296868))streamType |

**Start publishing audio/video streams to Tencent Cloud CSS CDN.**

@deprecated It is deprecated starting from v12.0. Please use [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e) instead.

## stopPublishing

**stopPublishing**

**Stop publishing audio/video streams to Tencent Cloud CSS CDN.**

@deprecated It is deprecated starting from v12.0. Please use [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e) instead.

## startPublishCDNStream:

**startPublishCDNStream:**

| - (void)startPublishCDNStream: | ([TRTCPublishCDNParam](https://www.tencentcloud.com/document/product/647/50760#4aa4692cc9d8e63bcd0dfbf1f6d92efa)*)param |
| --- | --- |

**Start publishing audio/video streams to non-Tencent Cloud CDN.**

@deprecated It is deprecated starting from v12.0. Please use [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e) instead.

## stopPublishCDNStream

**stopPublishCDNStream**

**Stop publishing audio/video streams to non-Tencent Cloud CDN.**

@deprecated It is deprecated starting from v12.0. Please use [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e) instead.

## setMixTranscodingConfig:

**setMixTranscodingConfig:**

| - (void)setMixTranscodingConfig: | (nullable [TRTCTranscodingConfig](https://www.tencentcloud.com/document/product/647/50760#c3eef0088da62b5dd27fb0c08db18906)*)config |
| --- | --- |

**Set the layout and transcoding parameters of On-Cloud MixTranscoding.**

@deprecated It is deprecated starting from v12.0. Please use [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#9cea9ae34a50a44c0a7023295313bf2e)ï¼ [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#fc8a7778d8fc91d7dff4c3801b5e5cfe) and [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50754#baed14d503098cc7af12328cf79da29e) instead.


---
*Source: [https://trtc.io/document/50761](https://trtc.io/document/50761)*
