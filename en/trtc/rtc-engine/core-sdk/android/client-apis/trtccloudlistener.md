# TRTCCloudListener

Copyright (c) 2021 Tencent. All rights reserved.

Module:   TRTCCloudListener @ TXLiteAVSDK

Function: event callback APIs for TRTCâs video call feature

**TRTCCloudListener**

## TRTCVideoRenderListener

| FuncList | DESC |
| --- | --- |
| [onRenderVideoFrame](https://www.tencentcloud.com/document/product/647/50763#5be091bd1a65e342c86407f252b0d5e2) | Custom video rendering. |

## TRTCVideoFrameListener

| FuncList | DESC |
| --- | --- |
| [onGLContextCreated](https://www.tencentcloud.com/document/product/647/50763#e9cdbfe822913f9cef0f8356858a9505) | An OpenGL context was created in the SDK. |
| [onProcessVideoFrame](https://www.tencentcloud.com/document/product/647/50763#ca7517167849fe21e3fc21c678b8b427) | Video processing by third-party beauty filters. |
| [onGLContextDestory](https://www.tencentcloud.com/document/product/647/50763#2a0ea0c174a3231091f2097077a60da9) | The OpenGL context in the SDK was destroyed. |

## TRTCAudioFrameListener

| FuncList | DESC |
| --- | --- |
| [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#b02cc5237a701b6ea1a7b5f99aad625c) | Audio data captured by the local mic and pre-processed by the audio module. |
| [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#d481858c6d71a2accc18a96f59e8db6c) | Audio data captured by the local mic, pre-processed by the audio module, effect-processed and BGM-mixed. |
| [onRemoteUserAudioFrame](https://www.tencentcloud.com/document/product/647/50763#e244077b85f3b7659e10fd7a916e5ccd) | Audio data of each remote user before audio mixing. |
| [onMixedPlayAudioFrame](https://www.tencentcloud.com/document/product/647/50763#544fc0be68d0c91599e4e94046ea7ef9) | Data mixed from each channel before being submitted to the system for playback. |
| [onMixedAllAudioFrame](https://www.tencentcloud.com/document/product/647/50763#acc0351ba4a069cc57489de536e94b89) | Data mixed from all the captured and to-be-played audio in the SDK. |
| [onVoiceEarMonitorAudioFrame](https://www.tencentcloud.com/document/product/647/50763#0293bff9b393f05d4d44c6fc4be7d59b) | In-ear monitoring data. |

## TRTCLogListener

| FuncList | DESC |
| --- | --- |
| [onLog](https://www.tencentcloud.com/document/product/647/50763#bfb112052d1af03d29bf03dde9f7a38e) | Printing of local log. |

## TRTCCloudListener

| FuncList | DESC |
| --- | --- |
| [onError](https://www.tencentcloud.com/document/product/647/50763#a210036518497eee3f50b3e0738476fd) | Error event callback. |
| [onWarning](https://www.tencentcloud.com/document/product/647/50763#b325c0a398a4c9666a3d66a312163bae) | Warning event callback. |
| [onEnterRoom](https://www.tencentcloud.com/document/product/647/50763#00a62e5b89b24bcac09ce0bdc5cb0da7) | Whether room entry is successful. |
| [onExitRoom](https://www.tencentcloud.com/document/product/647/50763#41db48ab552c935ba865dc86eeb5b9d0) | Room exit. |
| [onSwitchRole](https://www.tencentcloud.com/document/product/647/50763#64c825f856ed30751fb936ee640ce478) | Role switching. |
| [onSwitchRoom](https://www.tencentcloud.com/document/product/647/50763#259a9711a076b472dc07e5d12b6cb533) | Result of room switching. |
| [onConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50763#bb05cf36cc9a461e0b45ae825ee5e2e0) | Result of requesting cross-room call. |
| [onDisConnectOtherRoom](https://www.tencentcloud.com/document/product/647/50763#162e6a6e08df62dbb8ad7e2457228211) | Result of ending cross-room call. |
| [onUpdateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50763#0841e8dd52bc5ca16cb1f5154ce3b75b) | Result of changing the upstream capability of the cross-room anchor. |
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
| [onNetworkQuality](https://www.tencentcloud.com/document/product/647/50763#5220c567251698e35a0aae0bd50d4cd1) | Real-time network quality statistics. |
| [onStatistics](https://www.tencentcloud.com/document/product/647/50763#faca91305f246db336cb6c56f7bfbf25) | Real-time statistics on technical metrics. |
| [onSpeedTestResult](https://www.tencentcloud.com/document/product/647/50763#daf3b15c9f1bd505ee8e2600cc27f49b) | Callback of network speed test. |
| [onConnectionLost](https://www.tencentcloud.com/document/product/647/50763#ffc0f58daed671ee4efca27b54deca45) | The SDK was disconnected from the cloud. |
| [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50763#fd6b9c3956e35b67413fe7c7938ca5de) | The SDK is reconnecting to the cloud. |
| [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50763#85a1f134a3fb0d0b6903c1a42797a604) | The SDK is reconnected to the cloud. |
| [onCameraDidReady](https://www.tencentcloud.com/document/product/647/50763#a2166e1dc3a1cfcf71c08e5de6056abe) | The camera is ready. |
| [onMicDidReady](https://www.tencentcloud.com/document/product/647/50763#afe1886bee9081dd93357591ea190897) | The mic is ready. |
| [onAudioRouteChanged](https://www.tencentcloud.com/document/product/647/50763#388f09037008693f6531d93db090d9d7) | The audio route changed (for mobile devices only). |
| [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/50763#2ec23470e2480bd26d91353c0998d019) | Volume. |
| [onRecvCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50763#fa42648c207d482ed4124f99100823fc) | Receipt of custom message. |
| [onMissCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50763#44459f158ee25b624f3f067824485bcb) | Loss of custom message. |
| [onRecvSEIMsg](https://www.tencentcloud.com/document/product/647/50763#825b49ace1d64ee095ab1f2014529738) | Receipt of SEI message. |
| [onStartPublishing](https://www.tencentcloud.com/document/product/647/50763#c0e748fa851bec48a82d42e27f0c1bd9) | Started publishing to Tencent Cloud CSS CDN. |
| [onStopPublishing](https://www.tencentcloud.com/document/product/647/50763#2c41f3b6cc5622fc3654b701ccb71c96) | Stopped publishing to Tencent Cloud CSS CDN. |
| [onStartPublishCDNStream](https://www.tencentcloud.com/document/product/647/50763#43ddc92c2362dd8662c17d776a90ecd4) | Started publishing to non-Tencent Cloudâs live streaming CDN. |
| [onStopPublishCDNStream](https://www.tencentcloud.com/document/product/647/50763#81c40c1ae4aae815191a1d236ccc7840) | Stopped publishing to non-Tencent Cloudâs live streaming CDN. |
| [onSetMixTranscodingConfig](https://www.tencentcloud.com/document/product/647/50763#353a7d9b80cda90f70916d67652e8097) | Set the layout and transcoding parameters for On-Cloud MixTranscoding. |
| [onStartPublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#95cedc06908dda47f4459b30961764a4) | Callback for starting to publish. |
| [onUpdatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#7d8052ed48b758cbdf0fb4d90e8b68f0) | Callback for modifying publishing parameters. |
| [onStopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50763#52edf2fdf62fb3be10c20e6c33fd9169) | Callback for stopping publishing. |
| [onCdnStreamStateChanged](https://www.tencentcloud.com/document/product/647/50763#2e8c5883ed22424a1424f1b256cdc76d) | Callback for change of RTMP/RTMPS publishing status. |
| [onScreenCaptureStarted](https://www.tencentcloud.com/document/product/647/50763#b8df6d78ecc8f8c7ee36545c5c390ba0) | Screen sharing started. |
| [onScreenCapturePaused](https://www.tencentcloud.com/document/product/647/50763#a1382f12b655dc8b374aec24d67f58d1) | Screen sharing was paused. |
| [onScreenCaptureResumed](https://www.tencentcloud.com/document/product/647/50763#e10e68d5858a269200d5fdbc6d9e348a) | Screen sharing was resumed. |
| [onScreenCaptureStopped](https://www.tencentcloud.com/document/product/647/50763#128e1720d2db631bf47bfd9ac2671705) | Screen sharing stopped. |
| [onLocalRecordBegin](https://www.tencentcloud.com/document/product/647/50763#4483cc99d86553aefe9f975c69c52d44) | Local recording started. |
| [onLocalRecording](https://www.tencentcloud.com/document/product/647/50763#62d4da4491e58833757e9117d3af70c5) | Local media is being recorded. |
| [onLocalRecordFragment](https://www.tencentcloud.com/document/product/647/50763#707cf5564bb9b16e891a45295e5f916d) | Record fragment finished. |
| [onLocalRecordComplete](https://www.tencentcloud.com/document/product/647/50763#34d5a7ab0dd7566631a7dd3a35582a3e) | Local recording stopped. |
| [onSnapshotComplete](https://www.tencentcloud.com/document/product/647/50763#2178e76eaae55ba207a82453e595b1f7) | Finished taking a local screenshot. |
| [onUserEnter](https://www.tencentcloud.com/document/product/647/50763#7fce6d0cdcd7d553eaa53f37b636cec7) | An anchor entered the room (disused). |
| [onUserExit](https://www.tencentcloud.com/document/product/647/50763#9f4a171973a5d322f937aefebaeeb7b8) | An anchor left the room (disused). |
| [onAudioEffectFinished](https://www.tencentcloud.com/document/product/647/50763#fdb499d0bd647201078dad545ff605eb) | Audio effects ended (disused). |
| [onSpeedTest](https://www.tencentcloud.com/document/product/647/50763#a585f7bcab66ec6c5b4709aa27f98844) | Result of server speed testing (disused). |

## onRenderVideoFrame

**onRenderVideoFrame**

| void onRenderVideoFrame | (String userId |
| --- | --- |
|  | int streamType |
|  | TRTCCloudDef.[TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50768#9233a1b1573333abc70e53b51bd89740) frame) |

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

| int onProcessVideoFrame | (TRTCCloudDef.[TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50768#9233a1b1573333abc70e53b51bd89740) srcFrame |
| --- | --- |
|  | TRTCCloudDef.[TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/50768#9233a1b1573333abc70e53b51bd89740) dstFrame) |

**Video processing by third-party beauty filters.**

If you use a third-party beauty filter component, you need to configure this callback in ` TRTCCloud ` to have the SDK return to you video frames that are otherwise pre-processed by TRTC.

You can then send the video frames to the third-party beauty filter component for processing. As the data returned can be read and modified, the result of processing can be synced to TRTC for subsequent encoding and publishing.

Case 1: the beauty filter component generates new textures

If the beauty filter component you use generates a frame of new texture (for the processed image) during image processing, please set ` dstFrame.textureId ` to the ID of the new texture in the callback function.

```
private final TRTCVideoFrameListener mVideoFrameListener = new TRTCVideoFrameListener() {    @Override    public void onGLContextCreated() {        mFURenderer.onSurfaceCreated();        mFURenderer.setUseTexAsync(true);    }    @Override    public int onProcessVideoFrame(TRTCVideoFrame srcFrame, TRTCVideoFrame dstFrame) {        dstFrame.texture.textureId = mFURenderer.onDrawFrameSingleInput(srcFrame.texture.textureId, srcFrame.width, srcFrame.height);        return 0;    }    @Override    public void onGLContextDestory() {        mFURenderer.onSurfaceDestroyed();    }};
```

Case 2: you need to provide target textures to the beauty filter component

If the third-party beauty filter component you use does not generate new textures and you need to manually set an input texture and an output texture for the component, you can consider the following scheme:

```
int onProcessVideoFrame(TRTCCloudDef.TRTCVideoFrame srcFrame, TRTCCloudDef.TRTCVideoFrame dstFrame) {    thirdparty_process(srcFrame.texture.textureId, srcFrame.width, srcFrame.height, dstFrame.texture.textureId);    return 0;}
```

| Param | DESC |
| --- | --- |
| dstFrame | Used to receive video images processed by third-party beauty filters |
| srcFrame | Used to carry images captured by TRTC via the camera |

> **Note**Currently, only the OpenGL texture scheme is supported(PC supports TRTCVideoBufferType_Buffer format Only)

## onGLContextDestory

**onGLContextDestory**

**The OpenGL context in the SDK was destroyed.**

## onCapturedAudioFrame

**onCapturedAudioFrame**

| void onCapturedAudioFrame | (TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) frame) |
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

| void onLocalProcessedAudioFrame | (TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) frame) |
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

> **Note**1. Please avoid time-consuming operations in this callback function. The SDK processes an audio frame every 20 ms, so if your operation takes more than 20 ms, it will cause audio exceptions.2. The audio data returned via this callback can be read and modified, but please keep the duration of your operation short.3. Audio data is returned via this callback after ANS, AEC, AGC, effect-processing and BGM-mixing, and therefore the delay is longer than that with [onCapturedAudioFrame](https://www.tencentcloud.com/document/product/647/50763#b02cc5237a701b6ea1a7b5f99aad625c).

## onRemoteUserAudioFrame

**onRemoteUserAudioFrame**

| void onRemoteUserAudioFrame | (TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) frame |
| --- | --- |
|  | String userId) |

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

| void onMixedPlayAudioFrame | (TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) frame) |
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

| void onMixedAllAudioFrame | (TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) frame) |
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

## onVoiceEarMonitorAudioFrame

**onVoiceEarMonitorAudioFrame**

| void onVoiceEarMonitorAudioFrame | (TRTCCloudDef.[TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/50768#79f2ee18ad9ffc6859bd72ae05a27081) frame) |
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

## onLog

**onLog**

| void onLog | (String log |
| --- | --- |
|  | int level |
|  | String module) |

**Printing of local log.**

If you want to capture the local log printing event, you can configure the log callback to have the SDK return to you via this callback all logs that are to be printed.

| Param | DESC |
| --- | --- |
| level | Log level. For more information, please see [TRTC_LOG_LEVEL](https://www.tencentcloud.com/document/product/647/50768#2953af68de5929f131c00faf8346e0b0). |
| log | Log content |
| module | Reserved field, which is not defined at the moment and has a fixed value of ` TXLiteAVSDK `. |

## onError

**onError**

| void onError | (int errCode |
| --- | --- |
|  | String errMsg |
|  | Bundle extraInfo) |

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

| void onWarning | (int warningCode |
| --- | --- |
|  | String warningMsg |
|  | Bundle extraInfo) |

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

| void onEnterRoom | (long result) |
| --- | --- |

**Whether room entry is successful.**

After calling the [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) API in ` TRTCCloud ` to enter a room, you will receive the ` onEnterRoom(result) ` callback from ` TRTCCloudDelegate `.

- If room entry succeeded, ` result ` will be a positive number (` result ` > 0), indicating the time in milliseconds (ms) the room entry takes.
- If room entry failed, ` result ` will be a negative number (result < 0), indicating the error code for the failure.

For more information on the error codes for room entry failure, see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135).

| Param | DESC |
| --- | --- |
| result | If ` result ` is greater than 0, it indicates the time (in ms) the room entry takes; if ` result ` is less than 0, it represents the error code for room entry. |

> **Note**1. In TRTC versions below 6.6, the ` onEnterRoom(result) ` callback is returned only if room entry succeeds, and the [onError](https://www.tencentcloud.com/document/product/647/50763#a210036518497eee3f50b3e0738476fd) callback is returned if room entry fails.2. In TRTC 6.6 and above, the ` onEnterRoom(result) ` callback is returned regardless of whether room entry succeeds or fails, and the [onError](https://www.tencentcloud.com/document/product/647/50763#a210036518497eee3f50b3e0738476fd) callback is also returned if room entry fails.

## onExitRoom

**onExitRoom**

| void onExitRoom | (int reason) |
| --- | --- |

**Room exit.**

Calling the [exitRoom](https://www.tencentcloud.com/document/product/647/50762#4651ae2c9ff5aa99442102e0d77a8606) API in ` TRTCCloud ` will trigger the execution of room exit-related logic, such as releasing resources of audio/video devices and codecs.

After all resources occupied by the SDK are released, the SDK will return the ` onExitRoom() ` callback.

If you need to call [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f) again or switch to another audio/video SDK, please wait until you receive the ` onExitRoom() ` callback.

Otherwise, you may encounter problems such as the camera or mic being occupied.

| Param | DESC |
| --- | --- |
| reason | Reason for room exit. ` 0 `: the user called ` exitRoom ` to exit the room; ` 1 `: the user was removed from the room by the server; ` 2 `: the room was dismissed; ` 3 `: the server status was abnormal. |

## onSwitchRole

**onSwitchRole**

| void onSwitchRole | (final int errCode |
| --- | --- |
|  | final String errMsg) |

**Role switching.**

You can call the [switchRole](https://www.tencentcloud.com/document/product/647/50762#0a2b76d62a79877c408aa638b61d9b8e) API in ` TRTCCloud ` to switch between the anchor and audience roles. This is accompanied by a line switching process.

After the switching, the SDK will return the ` onSwitchRole() ` event callback.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates a successful switch. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onSwitchRoom

**onSwitchRoom**

| void onSwitchRoom | (final int errCode |
| --- | --- |
|  | final String errMsg) |

**Result of room switching.**

You can call the [switchRoom](https://www.tencentcloud.com/document/product/647/50762#fab001093db697fd493494283e992a9f) API in ` TRTCCloud ` to switch from one room to another.

After the switching, the SDK will return the ` onSwitchRoom() ` event callback.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates a successful switch. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35124). |
| errMsg | Error message |

## onConnectOtherRoom

**onConnectOtherRoom**

| void onConnectOtherRoom | (final String userId |
| --- | --- |
|  | final int errCode |
|  | final String errMsg) |

**Result of requesting cross-room call.**

You can call the [connectOtherRoom](https://www.tencentcloud.com/document/product/647/50762#71e28e2184ffae717c6d768d9f757ad7) API in ` TRTCCloud ` to establish a video call with the anchor of another room. This is the âanchor competitionâ feature.

The caller will receive the ` onConnectOtherRoom() ` callback, which can be used to determine whether the cross-room call is successful.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that cross-room connection is established successfully. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |
| userId | The user ID of the anchor (in another room) to be called |

## onDisConnectOtherRoom

**onDisConnectOtherRoom**

| void onDisConnectOtherRoom | (final int errCode |
| --- | --- |
|  | final String errMsg) |

**Result of ending cross-room call.**

You can call the disConnectOtherRoom API in ` TRTCCloud ` to end a video call with the anchor of another room. This is the âanchor competitionâ feature.

The caller will receive the ` onDisconnectOtherRoom() ` callback to determine whether the cross-room call has been successfully disconnected.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that the cross-room call has been successfully disconnected. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onUpdateOtherRoomForwardMode

**onUpdateOtherRoomForwardMode**

| void onUpdateOtherRoomForwardMode | (final int errCode |
| --- | --- |
|  | final String errMsg) |

**Result of changing the upstream capability of the cross-room anchor.**

You can call the [updateOtherRoomForwardMode](https://www.tencentcloud.com/document/product/647/50762#f74725866e0df9e3763df166f1692c88) API in ` TRTCCloud ` to limit the upstream capability of the cross-room anchor in the current room, and prohibit or allow the cross-room anchor to publish audio/video/sub-stream. This behavior will affect all users in the room.

The caller will receive the ` onUpdateOtherRoomForwardMode() ` callback to determine whether the changing upstream capability of the cross-room anchor is successful.

| Param | DESC |
| --- | --- |
| errCode | Error code. ` ERR_NULL ` indicates that upstream capability of the cross-room anchor is changed successfully. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onRemoteUserEnterRoom

**onRemoteUserEnterRoom**

| void onRemoteUserEnterRoom | (String userId) |
| --- | --- |

**A user entered the room.**

Due to performance concerns, this callback works differently in different scenarios (i.e., ` AppScene `, which you can specify by setting the second parameter when calling [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f)).

- Live streaming scenarios ([TRTC_APP_SCENE_LIVE](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340) or [TRTC_APP_SCENE_VOICE_CHATROOM](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)): in live streaming scenarios, a user is either in the role of an anchor or audience. The callback is returned only when an anchor enters the room.
- Call scenarios ([TRTC_APP_SCENE_VIDEOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340) or [TRTC_APP_SCENE_AUDIOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)): in call scenarios, the concept of roles does not apply (all users can be considered as anchors), and the callback is returned when any user enters the room.

| Param | DESC |
| --- | --- |
| userId | User ID of the remote user |

> **Note**1. The ` onRemoteUserEnterRoom ` callback indicates that a user entered the room, but it does not necessarily mean that the user enabled audio or video.2. If you want to know whether a user enabled video, we recommend you use the [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/50763#448623ba3ddafa44cdb425bea100c2d8) callback.

## onRemoteUserLeaveRoom

**onRemoteUserLeaveRoom**

| void onRemoteUserLeaveRoom | (String userId |
| --- | --- |
|  | int reason) |

**A user exited the room.**

As with [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/50763#a5bd4299b42d86c93067c2b8f581e959), this callback works differently in different scenarios (i.e., ` AppScene `, which you can specify by setting the second parameter when calling [enterRoom](https://www.tencentcloud.com/document/product/647/50762#b379e54cd925946c111f4c5994480a3f)).

- Live streaming scenarios ([TRTC_APP_SCENE_LIVE](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340) or [TRTC_APP_SCENE_VOICE_CHATROOM](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)): the callback is triggered only when an anchor exits the room.
- Call scenarios ([TRTC_APP_SCENE_VIDEOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340) or [TRTC_APP_SCENE_AUDIOCALL](https://www.tencentcloud.com/document/product/647/50768#45c6782b29cadc377b5763a5d8490340)): in call scenarios, the concept of roles does not apply, and the callback is returned when any user exits the room.

| Param | DESC |
| --- | --- |
| reason | Reason for room exit. ` 0 `: the user exited the room voluntarily; ` 1 `: the user exited the room due to timeout; ` 2 `: the user was removed from the room; ` 3 `: the anchor user exited the room due to switch to audience. |
| userId | User ID of the remote user |

## onUserVideoAvailable

**onUserVideoAvailable**

| void onUserVideoAvailable | (String userId |
| --- | --- |
|  | boolean available) |

**A remote user published/unpublished primary stream video.**

The primary stream is usually used for camera images. If you receive the ` onUserVideoAvailable(userId, true) ` callback, it indicates that the user has available primary stream video.

You can then call [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) to subscribe to the remote userâs video. If the subscription is successful, you will receive the ` onFirstVideoFrame(userid) ` callback, which indicates that the first video frame of the user is rendered.

If you receive the ` onUserVideoAvailable(userId, false) ` callback, it indicates that the video of the remote user is disabled, which may be because the user called [muteLocalVideo](https://www.tencentcloud.com/document/product/647/50762#3b9dab7aed0816028e9e593bce4525a9) or [stopLocalPreview](https://www.tencentcloud.com/document/product/647/50762#e379630cda7e794574b00d549b64a815).

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) primary stream video. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

## onUserSubStreamAvailable

**onUserSubStreamAvailable**

| void onUserSubStreamAvailable | (String userId |
| --- | --- |
|  | boolean available) |

**A remote user published/unpublished substream video.**

The substream is usually used for screen sharing images. If you receive the ` onUserSubStreamAvailable(userId, true) ` callback, it indicates that the user has available substream video.

You can then call [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) to subscribe to the remote userâs video. If the subscription is successful, you will receive the ` onFirstVideoFrame(userid) ` callback, which indicates that the first frame of the user is rendered.

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) substream video. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

> **Note**The API used to display substream images is [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90), not startRemoteSubStreamView, startRemoteSubStreamView is deprecated.

## onUserAudioAvailable

**onUserAudioAvailable**

| void onUserAudioAvailable | (String userId |
| --- | --- |
|  | boolean available) |

**A remote user published/unpublished audio.**

If you receive the ` onUserAudioAvailable(userId, true) ` callback, it indicates that the user published audio.

- In auto-subscription mode, the SDK will play the userâs audio automatically.
- In manual subscription mode, you can call [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/50762#d6800ccf317e0ccecc8ba17e44e59438)(userid, false) to play the userâs audio.

| Param | DESC |
| --- | --- |
| available | Whether the user published (or unpublished) audio. ` true `: published; ` false `: unpublished |
| userId | User ID of the remote user |

> **Note**The auto-subscription mode is used by default. You can switch to the manual subscription mode by calling [setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/50762#0f8a372a4d0698fd7eac24007ed7a9a9), but it must be called before room entry for the switch to take effect.

## onFirstVideoFrame

**onFirstVideoFrame**

| void onFirstVideoFrame | (String userId |
| --- | --- |
|  | int streamType |
|  | int width |
|  | int height) |

**The SDK started rendering the first video frame of the local or a remote user.**

The SDK returns this event callback when it starts rendering your first video frame or that of a remote user. The ` userId ` in the callback can help you determine whether the frame is yours or a remote userâs.

- If ` userId ` is empty, it indicates that the SDK has started rendering your first video frame. The precondition is that you have called [startLocalPreview](https://www.tencentcloud.com/document/product/647/50762#b1f7334c9de08e2e26545ea4ddfd5507) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50762#9b55d2e9cd4e32eae74a9eb3555f6c8b).
- If ` userId ` is not empty, it indicates that the SDK has started rendering the first video frame of a remote user. The precondition is that you have called [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) to subscribe to the userâs video.

| Param | DESC |
| --- | --- |
| height | Video height |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | The user ID of the local or a remote user. If it is empty, it indicates that the first local video frame is available; if it is not empty, it indicates that the first video frame of a remote user is available. |
| width | Video width |

> **Note**1. The callback of the first local video frame being rendered is triggered only after you call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50762#b1f7334c9de08e2e26545ea4ddfd5507) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50762#9b55d2e9cd4e32eae74a9eb3555f6c8b).2. The callback of the first video frame of a remote user being rendered is triggered only after you call [startRemoteView](https://www.tencentcloud.com/document/product/647/50762#01208b71b9c2edf6ad8ea4b8220a1d90) or startRemoteSubStreamView.

## onFirstAudioFrame

**onFirstAudioFrame**

| void onFirstAudioFrame | (String userId) |
| --- | --- |

**The SDK started playing the first audio frame of a remote user.**

The SDK returns this callback when it plays the first audio frame of a remote user. The callback is not returned for the playing of the first audio frame of the local user.

| Param | DESC |
| --- | --- |
| userId | User ID of the remote user |

## onSendFirstLocalVideoFrame

**onSendFirstLocalVideoFrame**

| void onSendFirstLocalVideoFrame | (int streamType) |
| --- | --- |

**The first local video frame was published.**

After you enter a room and call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50762#b1f7334c9de08e2e26545ea4ddfd5507) or [startScreenCapture](https://www.tencentcloud.com/document/product/647/50762#9b55d2e9cd4e32eae74a9eb3555f6c8b) to enable local video capturing (whichever happens first),

the SDK will start video encoding and publish the local video data via its network module to the cloud.

It returns the ` onSendFirstLocalVideoFrame ` callback after publishing the first local video frame.

| Param | DESC |
| --- | --- |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |

## onSendFirstLocalAudioFrame

**onSendFirstLocalAudioFrame**

**The first local audio frame was published.**

After you enter a room and call [startLocalAudio](https://www.tencentcloud.com/document/product/647/50762#a127184d8d223906a5413d9610d6d22d) to enable audio capturing (whichever happens first),

the SDK will start audio encoding and publish the local audio data via its network module to the cloud.

The SDK returns the ` onSendFirstLocalAudioFrame ` callback after sending the first local audio frame.

## onRemoteVideoStatusUpdated

**onRemoteVideoStatusUpdated**

| void onRemoteVideoStatusUpdated | (String userId |
| --- | --- |
|  | int streamType |
|  | int status |
|  | int reason |
|  | Bundle extraInfo) |

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

| void onRemoteAudioStatusUpdated | (String userId |
| --- | --- |
|  | int status |
|  | int reason |
|  | Bundle extraInfo) |

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

| void onUserVideoSizeChanged | (String userId |
| --- | --- |
|  | int streamType |
|  | int newWidth |
|  | int newHeight) |

**Change of remote video size.**

If you receive the ` onUserVideoSizeChanged(userId, streamType, newWidth, newHeight) ` callback, it indicates that the user changed the video size. It may be triggered by [setVideoEncoderParam](https://www.tencentcloud.com/document/product/647/50762#d227231fc6993ebe2f1c332d48f71563) or [setSubStreamEncoderParam](https://www.tencentcloud.com/document/product/647/50762#ae8dee3c3444ccd1450021b8f2cc5d4e).

| Param | DESC |
| --- | --- |
| newHeight | Video height |
| newWidth | Video width |
| streamType | Video stream type. The primary stream (` Main `) is usually used for camera images, and the substream (` Sub `) for screen sharing images. |
| userId | User ID |

## onNetworkQuality

**onNetworkQuality**

| void onNetworkQuality | (TRTCCloudDef.[TRTCQuality](https://www.tencentcloud.com/document/product/647/50768#1796fe5bcef4aec6d520bdd8e530474b) localQuality |
| --- | --- |
|  | ArrayList<TRTCCloudDef.[TRTCQuality](https://www.tencentcloud.com/document/product/647/50768#1796fe5bcef4aec6d520bdd8e530474b)> remoteQuality) |

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

| void onStatistics | ([TRTCStatistics](https://www.tencentcloud.com/document/product/647/50764#2a1e88fd90554975be810d09be8b16f6) statistics) |
| --- | --- |

**Real-time statistics on technical metrics.**

This callback is returned every 2 seconds and notifies you of the statistics on technical metrics related to video, audio, and network. The metrics are listed in [TRTCStatistics](https://www.tencentcloud.com/document/product/647/50764#2a1e88fd90554975be810d09be8b16f6):

- Video statistics: video resolution (` resolution `), frame rate (` FPS `), bitrate (` bitrate `), etc.
- Audio statistics: audio sample rate (` samplerate `), number of audio channels (` channel `), bitrate (` bitrate `), etc.
- Network statistics: the round trip time (` rtt `) between the SDK and the cloud (SDK -> Cloud -> SDK), package loss rate (` loss `), upstream traffic (` sentBytes `), downstream traffic (` receivedBytes `), etc.

| Param | DESC |
| --- | --- |
| statistics | Statistics, including local statistics and the statistics of remote users. For details, please see [TRTCStatistics](https://www.tencentcloud.com/document/product/647/50764#2a1e88fd90554975be810d09be8b16f6). |

> **Note**If you want to learn about only the current network quality and do not want to spend much time analyzing the statistics returned by this callback, we recommend you use [onNetworkQuality](https://www.tencentcloud.com/document/product/647/50763#5220c567251698e35a0aae0bd50d4cd1).

## onSpeedTestResult

**onSpeedTestResult**

| void onSpeedTestResult | (TRTCCloudDef.[TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/50768#25124dd8b486afcaeaabe326bfe10288) result) |
| --- | --- |

**Callback of network speed test.**

The callback is triggered by [startSpeedTest](https://www.tencentcloud.com/document/product/647/50762#ebfdd762ef3bab9136d8ca683892294b).

| Param | DESC |
| --- | --- |
| result | Speed test data, including loss rates, rtt and bandwidth rates, please refer to [TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/50768#25124dd8b486afcaeaabe326bfe10288) for details. |

## onConnectionLost

**onConnectionLost**

**The SDK was disconnected from the cloud.**

The SDK returns this callback when it is disconnected from the cloud, which may be caused by network unavailability or change of network, for example, when the user walks into an elevator.

After returning this callback, the SDK will attempt to reconnect to the cloud, and will return the [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50763#fd6b9c3956e35b67413fe7c7938ca5de) callback. When it is reconnected, it will return the [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50763#85a1f134a3fb0d0b6903c1a42797a604) callback.

In other words, the SDK proceeds from one event to the next in the following order:

![](https://qcloudimg.tencent-cloud.cn/raw/fb3c40a4fca55b0010d385cf3b2472cd.png)

## onTryToReconnect

**onTryToReconnect**

**The SDK is reconnecting to the cloud.**

When the SDK is disconnected from the cloud, it returns the [onConnectionLost](https://www.tencentcloud.com/document/product/647/50763#ffc0f58daed671ee4efca27b54deca45) callback. It then attempts to reconnect and returns this callback ([onTryToReconnect](https://www.tencentcloud.com/document/product/647/50763#fd6b9c3956e35b67413fe7c7938ca5de)). After it is reconnected, it returns the [onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50763#85a1f134a3fb0d0b6903c1a42797a604) callback.

## onConnectionRecovery

**onConnectionRecovery**

**The SDK is reconnected to the cloud.**

When the SDK is disconnected from the cloud, it returns the [onConnectionLost](https://www.tencentcloud.com/document/product/647/50763#ffc0f58daed671ee4efca27b54deca45) callback. It then attempts to reconnect and returns the [onTryToReconnect](https://www.tencentcloud.com/document/product/647/50763#fd6b9c3956e35b67413fe7c7938ca5de) callback. After it is reconnected, it returns this callback ([onConnectionRecovery](https://www.tencentcloud.com/document/product/647/50763#85a1f134a3fb0d0b6903c1a42797a604)).

## onCameraDidReady

**onCameraDidReady**

**The camera is ready.**

After you call [startLocalPreview](https://www.tencentcloud.com/document/product/647/50762#b1f7334c9de08e2e26545ea4ddfd5507), the SDK will try to start the camera and return this callback if the camera is started.

If it fails to start the camera, itâs probably because the application does not have access to the camera or the camera is being used.

You can capture the [onError](https://www.tencentcloud.com/document/product/647/50763#a210036518497eee3f50b3e0738476fd) callback to learn about the exception and let users know via UI messages.

## onMicDidReady

**onMicDidReady**

**The mic is ready.**

After you call [startLocalAudio](https://www.tencentcloud.com/document/product/647/50762#a127184d8d223906a5413d9610d6d22d), the SDK will try to start the mic and return this callback if the mic is started.

If it fails to start the mic, itâs probably because the application does not have access to the mic or the mic is being used.

You can capture the [onError](https://www.tencentcloud.com/document/product/647/50763#a210036518497eee3f50b3e0738476fd) callback to learn about the exception and let users know via UI messages.

## onAudioRouteChanged

**onAudioRouteChanged**

| void onAudioRouteChanged | (int newRoute |
| --- | --- |
|  | int oldRoute) |

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

| void onUserVoiceVolume | (ArrayList<TRTCCloudDef.[TRTCVolumeInfo](https://www.tencentcloud.com/document/product/647/50768#6895db8871ff30fc996e931a213e2b0c)> userVolumes |
| --- | --- |
|  | int totalVolume) |

**Volume.**

The SDK can assess the volume of each channel and return this callback on a regular basis. You can display, for example, a waveform or volume bar on the UI based on the statistics returned.

You need to first call [enableAudioVolumeEvaluation](https://www.tencentcloud.com/document/product/647/50762#a4342e2f3b540f5ecad64bbacb738787) to enable the feature and set the interval for the callback.

Note that the SDK returns this callback at the specified interval regardless of whether someone is speaking in the room.

| Param | DESC |
| --- | --- |
| totalVolume | The total volume of all remote users. Value range: [0, 100] |
| userVolumes | An array that represents the volume of all users who are speaking in the room. Value range: [0, 100] |

> **Note**` userVolumes ` is an array. If ` userId ` is empty, the elements in the array represent the volume of the local userâs audio. Otherwise, they represent the volume of a remote userâs audio.

## onRecvCustomCmdMsg

**onRecvCustomCmdMsg**

| void onRecvCustomCmdMsg | (String userId |
| --- | --- |
|  | int cmdID |
|  | int seq |
|  | byte[] message) |

**Receipt of custom message.**

When a user in a room uses [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50762#9649cfc709c73d6dbb4df75bbc798fab) to send a custom message, other users in the room can receive the message through the ` onRecvCustomCmdMsg ` callback.

| Param | DESC |
| --- | --- |
| cmdID | Command ID |
| message | Message data |
| seq | Message serial number |
| userId | User ID |

## onMissCustomCmdMsg

**onMissCustomCmdMsg**

| void onMissCustomCmdMsg | (String userId |
| --- | --- |
|  | int cmdID |
|  | int errCode |
|  | int missed) |

**Loss of custom message.**

When you use [sendCustomCmdMsg](https://www.tencentcloud.com/document/product/647/50762#9649cfc709c73d6dbb4df75bbc798fab) to send a custom UDP message, even if you enable reliable transfer (by setting ` reliable ` to ` true `), there is still a chance of message loss. Reliable transfer only helps maintain a low probability of message loss, which meets the reliability requirements in most cases.

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

| void onRecvSEIMsg | (String userId |
| --- | --- |
|  | byte[] data) |

**Receipt of SEI message.**

If a user in the room uses [sendSEIMsg](https://www.tencentcloud.com/document/product/647/50762#52a919f9f3a990ebd08679bd47aa69bb) to send an SEI message via video frames, other users in the room can receive the message through the ` onRecvSEIMsg ` callback.

| Param | DESC |
| --- | --- |
| message | Data |
| userId | User ID |

## onStartPublishing

**onStartPublishing**

| void onStartPublishing | (int err |
| --- | --- |
|  | String errMsg) |

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
|  | String errMsg) |

**Stopped publishing to Tencent Cloud CSS CDN.**

When you call stopPublishing to stop publishing streams to Tencent Cloud CSS CDN, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStartPublishCDNStream

**onStartPublishCDNStream**

| void onStartPublishCDNStream | (int err |
| --- | --- |
|  | String errMsg) |

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

| void onStopPublishCDNStream | (int err |
| --- | --- |
|  | String errMsg) |

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
|  | String errMsg) |

**Set the layout and transcoding parameters for On-Cloud MixTranscoding.**

When you call setMixTranscodingConfig to modify the layout and transcoding parameters for On-Cloud MixTranscoding, the SDK will sync the command to the CVM immediately.

The SDK will then receive the execution result from the CVM and return the result to you via this callback.

| Param | DESC |
| --- | --- |
| err | ` 0 `: successful; other values: failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| errMsg | Error message |

## onStartPublishMediaStream

**onStartPublishMediaStream**

| void onStartPublishMediaStream | (String taskId |
| --- | --- |
|  | int code |
|  | String message |
|  | Bundle extraInfo) |

**Callback for starting to publish.**

When you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4) to publish a stream to the TRTC backend, the SDK will immediately update the command to the cloud server.

The SDK will then receive the publishing result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server failed to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended actions are as follows: 2000: Parameter error. Check the request parameters. 2001: Live streaming service is not enabled. Enable it in the Live streaming console. 2021: Third-party retweet service is not enabled. Contact product support to enable it. 3000: Internal server error. Retry is recommended. 4006: Concurrency conflict with the same task. The server is still processing the previous startPublishMediaStream task. Retry after a delay is recommended. 4007: The same task has already been successfully started using startPublishMediaStream. Use the returned taskId to call the updatePublishMediaStream API to update the task. 5001: Resource constraints. Retry after a delay is recommended. |
| message | : The callback information. |
| taskId | : If a request is successful, a task ID will be returned via the callback. You need to provide this task ID when you call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#735a40ecbeb18a37348b9dbce0ae8c68) to modify publishing parameters or [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#ef07e55b75ccb81b9849502f67b07083) to stop publishing. |

## onUpdatePublishMediaStream

**onUpdatePublishMediaStream**

| void onUpdatePublishMediaStream | (String taskId |
| --- | --- |
|  | int code |
|  | String message |
|  | Bundle extraInfo) |

**Callback for modifying publishing parameters.**

When you call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#735a40ecbeb18a37348b9dbce0ae8c68) to modify publishing parameters, the SDK will immediately update the command to the cloud server.

The SDK will then receive the modification result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server failed to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended solutions are as follows: 2000: Parameter error. Check the request parameters. 2001: Live streaming service is not enabled. Enable it in the Live Streaming Console. 2002: Task not found. Restart the task by calling the startPublishMediaStream API. 2018: Concurrent requests are out of order. Retry with the latest streaming parameters. 2021: Third-party retweet service is not enabled. Contact product support to enable it. 3000: Internal server error. Retry. 4003: Task is exiting. Stop the task by calling the stopPublishMediaStream API first, then restart it by calling the startPublishMediaStream API. |
| message | : The callback information. |
| taskId | : The task ID you pass in when calling [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#735a40ecbeb18a37348b9dbce0ae8c68), which is used to identify a request. |

## onStopPublishMediaStream

**onStopPublishMediaStream**

| void onStopPublishMediaStream | (String taskId |
| --- | --- |
|  | int code |
|  | String message |
|  | Bundle extraInfo) |

**Callback for stopping publishing.**

When you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#ef07e55b75ccb81b9849502f67b07083) to stop publishing, the SDK will immediately update the command to the cloud server.

The SDK will then receive the modification result from the cloud server and will send the result to you via this callback.

| Param | DESC |
| --- | --- |
| code | : ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues.If the code return value is ERR_SERVER_PROCESS_FAILED, it means the server was unable to process your request. You can use "error_code" as the key to retrieve the error code returned by the server. The specific error codes and recommended actions are as follows: 2000: Parameter error. Please check the request parameters. 2002: Task not found. No action required. 3000: Internal server error. Please retry. 4003: Task is exiting. No action required. |
| message | : The callback information. |
| taskId | : The task ID you pass in when calling [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#ef07e55b75ccb81b9849502f67b07083), which is used to identify a request. |

## onCdnStreamStateChanged

**onCdnStreamStateChanged**

| void onCdnStreamStateChanged | (String cdnUrl |
| --- | --- |
|  | int status |
|  | int code |
|  | String msg |
|  | Bundle extraInfo) |

**Callback for change of RTMP/RTMPS publishing status.**

When you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4) to publish a stream to the TRTC backend, the SDK will immediately update the command to the cloud server.

If you set the publishing destination ([TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50768#11c06c485af4d4bd3b60bc0c883a9a32)) to the URL of Tencent Cloud or a third-party CDN, you will be notified of the RTMP/RTMPS publishing status via this callback.

| Param | DESC |
| --- | --- |
| cdnUrl | : The URL you specify in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/50768#11c06c485af4d4bd3b60bc0c883a9a32) when you call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#bb3260a94c9fe97ee7231fe849fec1d4). |
| code | : The publishing result. ` 0 `: Successful; other values: Failed. For more information, please see [Error Codes](https://intl.cloud.tencent.com/document/product/647/35135). |
| extraInfo | : Additional information. For some error codes, there may be additional information to help you troubleshoot the issues. |
| message | : The publishing information. |
| status | : The publishing status. 0: The publishing has not started yet or has ended. This value will be returned after you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#ef07e55b75ccb81b9849502f67b07083). 1: The TRTC server is connecting to the CDN server. If the first attempt fails, the TRTC backend will retry multiple times and will return this value via the callback (every five seconds). After publishing succeeds, the value ` 2 ` will be returned. If a server error occurs or publishing is still unsuccessful after 60 seconds, the value ` 4 ` will be returned. 2: The TRTC server is publishing to the CDN. This value will be returned if the publishing succeeds. 3: The TRTC server is disconnected from the CDN server and is reconnecting. If a CDN error occurs or publishing is interrupted, the TRTC backend will try to reconnect and resume publishing and will return this value via the callback (every five seconds). After publishing resumes, the value ` 2 ` will be returned. If a server error occurs or the attempt to resume publishing is still unsuccessful after 60 seconds, the value ` 4 ` will be returned. 4: The TRTC server is disconnected from the CDN server and failed to reconnect within the timeout period. In this case, the publishing is deemed to have failed. You can call [updatePublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#735a40ecbeb18a37348b9dbce0ae8c68) to try again. 5: The TRTC server is disconnecting from the CDN server. After you call [stopPublishMediaStream](https://www.tencentcloud.com/document/product/647/50762#ef07e55b75ccb81b9849502f67b07083), the SDK will return this value first and then the value ` 0 `. |

## onScreenCaptureStarted

**onScreenCaptureStarted**

**Screen sharing started.**

The SDK returns this callback when you call [startScreenCapture](https://www.tencentcloud.com/document/product/647/50762#9b55d2e9cd4e32eae74a9eb3555f6c8b) and other APIs to start screen sharing.

## onScreenCapturePaused

**onScreenCapturePaused**

**Screen sharing was paused.**

The SDK returns this callback when you call [pauseScreenCapture](https://www.tencentcloud.com/document/product/647/50762#d7f9ad7b108c98e919f5f1cca757e72d) to pause screen sharing.

## onScreenCaptureResumed

**onScreenCaptureResumed**

**Screen sharing was resumed.**

The SDK returns this callback when you call [resumeScreenCapture](https://www.tencentcloud.com/document/product/647/50762#1924263011bb92fba1642ad3e139629f) to resume screen sharing.

## onScreenCaptureStopped

**onScreenCaptureStopped**

| void onScreenCaptureStopped | (int reason) |
| --- | --- |

**Screen sharing stopped.**

The SDK returns this callback when you call [stopScreenCapture](https://www.tencentcloud.com/document/product/647/50762#2a667ba75e08183bd5f764374a6de7ba) to stop screen sharing.

| Param | DESC |
| --- | --- |
| reason | Reason. ` 0 `: the user stopped screen sharing; ` 1 `: screen sharing stopped because the shared window was closed. |

## onLocalRecordBegin

**onLocalRecordBegin**

| void onLocalRecordBegin | (int errCode |
| --- | --- |
|  | String storagePath) |

**Local recording started.**

When you call [startLocalRecording](https://www.tencentcloud.com/document/product/647/50762#0107285c499b0f9a3cf30c34ef5199c8) to start local recording, the SDK returns this callback to notify you whether recording is started successfully.

| Param | DESC |
| --- | --- |
| errCode | status.  0: successful. -1: failed. -2: unsupported format. -6: recording has been started. Stop recording first. -7: recording file already exists and needs to be deleted. -8: recording directory does not have the write permission. Please check the directory permission. |
| storagePath | Storage path of recording file |

## onLocalRecording

**onLocalRecording**

| void onLocalRecording | (long duration |
| --- | --- |
|  | String storagePath) |

**Local media is being recorded.**

The SDK returns this callback regularly after local recording is started successfully via the calling of [startLocalRecording](https://www.tencentcloud.com/document/product/647/50762#0107285c499b0f9a3cf30c34ef5199c8).

You can capture this callback to stay up to date with the status of the recording task.

You can set the callback interval when calling [startLocalRecording](https://www.tencentcloud.com/document/product/647/50762#0107285c499b0f9a3cf30c34ef5199c8).

| Param | DESC |
| --- | --- |
| duration | Cumulative duration of recording, in milliseconds |
| storagePath | Storage path of recording file |

## onLocalRecordFragment

**onLocalRecordFragment**

| void onLocalRecordFragment | (String storagePath) |
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
|  | String storagePath) |

**Local recording stopped.**

When you call [stopLocalRecording](https://www.tencentcloud.com/document/product/647/50762#a1236129ca8f62c01939c1882f184a88) to stop local recording, the SDK returns this callback to notify you of the recording result.

| Param | DESC |
| --- | --- |
| errCode | status  0: successful. -1: failed. -2: Switching resolution or horizontal and vertical screen causes the recording to stop. -3: recording duration is too short or no video or audio data is received. Check the recording duration or whether audio or video capture is enabled. |
| storagePath | Storage path of recording file |

## onSnapshotComplete

**onSnapshotComplete**

| void onSnapshotComplete | (Bitmap bmp) |
| --- | --- |

**Finished taking a local screenshot.**

| Param | DESC |
| --- | --- |
| bmp | Screenshot result. If it is ` null `, the screenshot failed to be taken. |
| data | Screenshot data. If it is ` nullptr `, it indicates that the SDK failed to take the screenshot. |
| format | Screenshot data format. Only TRTCVideoPixelFormat_BGRA32 is supported now. |
| height | Screenshot height |
| length | Screenshot data length. In BGRA32 format, ` length = width * height * 4 `. |
| type | Video stream type |
| userId | User ID. If it is empty, the screenshot is a local image. |
| width | Screenshot width |

> **Note**The parameters of the full-platform C++ interface and the Java interface are different. The C++ interface uses 7 parameters to describe a screenshot, while the Java interface uses only one Bitmap to describe a screenshot.

## onUserEnter

**onUserEnter**

| void onUserEnter | (String userId) |
| --- | --- |

**An anchor entered the room (disused).**

@deprecated This callback is not recommended in the new version. Please use [onRemoteUserEnterRoom](https://www.tencentcloud.com/document/product/647/50763#a5bd4299b42d86c93067c2b8f581e959) instead.

## onUserExit

**onUserExit**

| void onUserExit | (String userId |
| --- | --- |
|  | int reason) |

**An anchor left the room (disused).**

@deprecated This callback is not recommended in the new version. Please use [onRemoteUserLeaveRoom](https://www.tencentcloud.com/document/product/647/50763#1fdebb79d1eff714ad27835bf083b075) instead.

## onAudioEffectFinished

**onAudioEffectFinished**

| void onAudioEffectFinished | (int effectId |
| --- | --- |
|  | int code) |

**Audio effects ended (disused).**

@deprecated This callback is not recommended in the new version. Please use [TXAudioEffectManager](https://www.tencentcloud.com/document/product/647/50765#3ed6c2f3d8ab0e5cabc2c5ffffb6e1fb) instead.

Audio effects and background music can be started using the same API ([startPlayMusic](https://www.tencentcloud.com/document/product/647/50765#e7b176192e2cf33abe2bd18618ad6bc1)) now instead of separate ones.

## onSpeedTest

**onSpeedTest**

| void onSpeedTest | (TRTCCloudDef.[TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/50768#25124dd8b486afcaeaabe326bfe10288) currentResult |
| --- | --- |
|  | int finishedCount |
|  | int totalCount) |

**Result of server speed testing (disused).**

@deprecated This callback is not recommended in the new version. Please use onSpeedTestResult: instead.


---
*Source: [https://trtc.io/document/50763](https://trtc.io/document/50763)*
