# Type Definition

Copyright (c) 2021 Tencent. All rights reserved.

Module: TRTC key class definition

Description: definitions of enumerated and constant values such as resolution and quality level

**Type Definition**

## StructType

| FuncList | DESC |
| --- | --- |
| [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190) | Room entry parameters. |
| [TRTCVideoEncParam](https://www.tencentcloud.com/document/product/647/72275#b5beabfeefb812ccf1060aea67185c4e) | Video encoding parameters. |
| [TRTCNetworkQosParam](https://www.tencentcloud.com/document/product/647/72275#15fa30eb2d0220259cea127fdb0f886f) | Network QoS control parameter set. |
| [TRTCRenderParams](https://www.tencentcloud.com/document/product/647/72275#660db44737d95899da095d02d163c478) | Rendering parameters of video image. |
| [TRTCQualityInfo](https://www.tencentcloud.com/document/product/647/72275#008511ed00730a2ef603fd62f64ca33c) | Network quality. |
| [TRTCVolumeInfo](https://www.tencentcloud.com/document/product/647/72275#6895db8871ff30fc996e931a213e2b0c) | Volume. |
| [TRTCSpeedTestParams](https://www.tencentcloud.com/document/product/647/72275#dd22aad94fc4b4773ca7323c7d34a1a7) | Network speed testing parameters. |
| [TRTCSpeedTestResult](https://www.tencentcloud.com/document/product/647/72275#25124dd8b486afcaeaabe326bfe10288) | Network speed test result. |
| [TRTCVideoFrame](https://www.tencentcloud.com/document/product/647/72275#9233a1b1573333abc70e53b51bd89740) | Video frame information. |
| [TRTCAudioFrame](https://www.tencentcloud.com/document/product/647/72275#799a6b31551472fb0770177a57ac2dcb) | Audio frame data. |
| [TRTCMixUser](https://www.tencentcloud.com/document/product/647/72275#a1a20e75e4f4ce2445754edc6942e80d) | Description information of each video image in On-Cloud MixTranscoding. |
| [TRTCTranscodingConfig](https://www.tencentcloud.com/document/product/647/72275#a6ada890d78dfe98a27315cc51a807ee) | Layout and transcoding parameters of On-Cloud MixTranscoding. |
| [TRTCPublishCDNParam](https://www.tencentcloud.com/document/product/647/72275#4aa4692cc9d8e63bcd0dfbf1f6d92efa) | Push parameters required to be set when publishing audio/video streams to non-Tencent Cloud CDN. |
| [TRTCAudioRecordingParams](https://www.tencentcloud.com/document/product/647/72275#364876527a7fc00850ca1926a4dd2245) | Local audio file recording parameters. |
| [TRTCLocalRecordingParams](https://www.tencentcloud.com/document/product/647/72275#4d8f80d5bf4ece224c7125eec1490b3d) | Local media file recording parameters. |
| [TRTCSwitchRoomConfig](https://www.tencentcloud.com/document/product/647/72275#d43f5dc42762839497bd8586ac2091e3) | Room switch parameter. |
| [TRTCAudioFrameCallbackFormat](https://www.tencentcloud.com/document/product/647/72275#352b0878415e79fcd48d9027fab3f683) | Format parameter of custom audio callback. |
| [TRTCImageBuffer](https://www.tencentcloud.com/document/product/647/72275#59a85413d0ae7d51336e2f7dbb575146) | Structure for storing window thumbnails and icons. |
| [TRTCUserParam](https://www.tencentcloud.com/document/product/647/72275#45a4828314c413dfe17bb431087723a7) | The users whose streams to publish. |
| [TRTCPublishCdnUrl](https://www.tencentcloud.com/document/product/647/72275#01fa41670434c53e53ac2e26f80f974d) | The destination URL when you publish to Tencent Cloud or a third-party CDN. |
| [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49) | The publishing destination. |
| [TRTCVideoLayout](https://www.tencentcloud.com/document/product/647/72275#eb7f6bda17ad0a4ae06b03db2882b95b) | The video layout of the transcoded stream. |
| [TRTCWaterMark](https://www.tencentcloud.com/document/product/647/72275#68cc8a894cbedbf3d2cf80d7bf3d14a3) | The watermark layout. |
| [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72275#22718fe81d94d21ec895cbc11820c726) | The encoding parameters. |
| [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166) | The transcoding parameters. |
| [TRTCAudioVolumeEvaluateParams](https://www.tencentcloud.com/document/product/647/72275#a009476d3d69bd49ff693344302409bf) | Volume evaluation and other related parameter settings. |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TRTCVideoResolution](https://www.tencentcloud.com/document/product/647/72275#6f987ce3b421d0d01b928065d4ebc5cb) | Video resolution. |
| [TRTCVideoResolutionMode](https://www.tencentcloud.com/document/product/647/72275#b2b7a5585994f1f4a88fbc17e2c821e7) | Video aspect ratio mode. |
| [TRTCVideoStreamType](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868) | Video stream type. |
| [TRTCVideoFillMode](https://www.tencentcloud.com/document/product/647/72275#b3c03b374c30311eef2887dc4799347f) | Video image fill mode. |
| [TRTCVideoRotation](https://www.tencentcloud.com/document/product/647/72275#3a45499a02ba68182709073cc7e29b4c) | Video image rotation direction. |
| [TRTCBeautyStyle](https://www.tencentcloud.com/document/product/647/72275#6b80cffd21c1ebc2f793a0dcc11abda6) | Beauty (skin smoothing) filter algorithm. |
| [TRTCVideoPixelFormat](https://www.tencentcloud.com/document/product/647/72275#0fd3b6da1fb10e3d92eb55b00ba55dc3) | Video pixel format. |
| [TRTCVideoBufferType](https://www.tencentcloud.com/document/product/647/72275#133a51a3a497d78c2b4d5de72ec7aaeb) | Video data transfer method. |
| [TRTCVideoMirrorType](https://www.tencentcloud.com/document/product/647/72275#21ddf23a6e62530028a4bd15ecd2387e) | Video mirror type. |
| [TRTCSnapshotSourceType](https://www.tencentcloud.com/document/product/647/72275#04962d5c2bd39860cae5394bac4ac9f8) | Data source of local video screenshot. |
| [TRTCAppScene](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) | Use cases. |
| [TRTCRoleType](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b) | Role. |
| [TRTCQosControlMode](https://www.tencentcloud.com/document/product/647/72275#d93de717f708e639093b7eae8965030a) | QoS control mode (disused). |
| [TRTCVideoQosPreference](https://www.tencentcloud.com/document/product/647/72275#e1af969d7b99606d3c064b5482ed4cfe) | Image quality preference. |
| [TRTCQuality](https://www.tencentcloud.com/document/product/647/72275#1d80134eda8e3a1608daa960ed67d092) | Network quality. |
| [TRTCAVStatusType](https://www.tencentcloud.com/document/product/647/72275#8ff0fad63c24db1b35490152f56d5bb3) | Audio/Video playback status. |
| [TRTCAVStatusChangeReason](https://www.tencentcloud.com/document/product/647/72275#37616803ec0eec21697bb3c20f20ca0d) | Reasons for playback status changes. |
| [TRTCAudioQuality](https://www.tencentcloud.com/document/product/647/72275#f8aeb89d8ef78db15d893e55f68cdb42) | Sound quality. |
| [TRTCAudioRoute](https://www.tencentcloud.com/document/product/647/72275#aaca0d57f6f9d9c6a6425485464b0877) | Audio route (i.e., audio playback mode). |
| [TRTCAudioFrameFormat](https://www.tencentcloud.com/document/product/647/72275#ac73b0af225be99342eab0db97c8ee5b) | Audio frame content format. |
| [TRTCAudioFrameOperationMode](https://www.tencentcloud.com/document/product/647/72275#712e9ebdb0469f1ee53dc91617c62d6b) | Audio callback data operation mode. |
| [TRTCLogLevel](https://www.tencentcloud.com/document/product/647/72275#3b7ff44175cba4dd48e97aa8ac7b0b98) | Log level. |
| [TRTCScreenCaptureSourceType](https://www.tencentcloud.com/document/product/647/72275#18d36b5519a892bf4b8b3f52a8b0a210) | Screen sharing target type (for desktops only). |
| [TRTCTranscodingConfigMode](https://www.tencentcloud.com/document/product/647/72275#c3eef0088da62b5dd27fb0c08db18906) | Layout mode of On-Cloud MixTranscoding. |
| [TRTCLocalRecordType](https://www.tencentcloud.com/document/product/647/72275#a33f990ed6e807aa140e0c2d999abe4a) | Media recording type. |
| [TRTCMixInputType](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6) | Stream mix input type. |
| [TRTCWaterMarkSrcType](https://www.tencentcloud.com/document/product/647/72275#49ce20e9ead413a1fe53e7a7854a9ef9) | Watermark image source type. |
| [TRTCAudioRecordingContent](https://www.tencentcloud.com/document/product/647/72275#4fc3c15e81a85e0a8d954f5e083a092b) | Audio recording content type. |
| [TRTCPublishMode](https://www.tencentcloud.com/document/product/647/72275#064db271e894d12e1e3ad63bbb1677fb) | The publishing mode. |
| [TRTCEncryptionAlgorithm](https://www.tencentcloud.com/document/product/647/72275#d013615ce328f9be9b01ee3f147651c0) | Encryption Algorithm. |
| [TRTCSpeedTestScene](https://www.tencentcloud.com/document/product/647/72275#d3063c0cbe17f166846aa9b251aa0878) | Speed Test Scene. |
| [TRTCGravitySensorAdaptiveMode](https://www.tencentcloud.com/document/product/647/72275#601299c4e6bd66487314e0edd164bf03) | Set the adaptation mode of gravity sensing (only applicable to mobile terminals). |

## TRTCVideoResolution

**TRTCVideoResolution**

#### Video resolution.

Here, only the landscape resolution (e.g., 640x360) is defined. If the portrait resolution (e.g., 360x640) needs to be used, ` Portrait ` must be selected for [TRTCVideoResolutionMode](https://www.tencentcloud.com/document/product/647/72275#b2b7a5585994f1f4a88fbc17e2c821e7).

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoResolution_120_120 | 1 | Aspect ratio: 1:1; resolution: 120x120; recommended bitrate (VideoCall): 80 Kbps; recommended bitrate (LIVE): 120 Kbps. |
| TRTCVideoResolution_160_160 | 3 | Aspect ratio: 1:1; resolution: 160x160; recommended bitrate (VideoCall): 100 Kbps; recommended bitrate (LIVE): 150 Kbps. |
| TRTCVideoResolution_270_270 | 5 | Aspect ratio: 1:1; resolution: 270x270; recommended bitrate (VideoCall): 200 Kbps; recommended bitrate (LIVE): 300 Kbps. |
| TRTCVideoResolution_480_480 | 7 | Aspect ratio: 1:1; resolution: 480x480; recommended bitrate (VideoCall): 350 Kbps; recommended bitrate (LIVE): 500 Kbps. |
| TRTCVideoResolution_160_120 | 50 | Aspect ratio: 4:3; resolution: 160x120; recommended bitrate (VideoCall): 100 Kbps; recommended bitrate (LIVE): 150 Kbps. |
| TRTCVideoResolution_240_180 | 52 | Aspect ratio: 4:3; resolution: 240x180; recommended bitrate (VideoCall): 150 Kbps; recommended bitrate (LIVE): 250 Kbps. |
| TRTCVideoResolution_280_210 | 54 | Aspect ratio: 4:3; resolution: 280x210; recommended bitrate (VideoCall): 200 Kbps; recommended bitrate (LIVE): 300 Kbps. |
| TRTCVideoResolution_320_240 | 56 | Aspect ratio: 4:3; resolution: 320x240; recommended bitrate (VideoCall): 250 Kbps; recommended bitrate (LIVE): 375 Kbps. |
| TRTCVideoResolution_400_300 | 58 | Aspect ratio: 4:3; resolution: 400x300; recommended bitrate (VideoCall): 300 Kbps; recommended bitrate (LIVE): 450 Kbps. |
| TRTCVideoResolution_480_360 | 60 | Aspect ratio: 4:3; resolution: 480x360; recommended bitrate (VideoCall): 400 Kbps; recommended bitrate (LIVE): 600 Kbps. |
| TRTCVideoResolution_640_480 | 62 | Aspect ratio: 4:3; resolution: 640x480; recommended bitrate (VideoCall): 600 Kbps; recommended bitrate (LIVE): 900 Kbps. |
| TRTCVideoResolution_960_720 | 64 | Aspect ratio: 4:3; resolution: 960x720; recommended bitrate (VideoCall): 1000kbps; recommended bitrate (LIVE): 1500kbpsã |
| TRTCVideoResolution_160_90 | 100 | Aspect ratio: 16:9; resolution: 160x90; recommended bitrate (VideoCall): 150 Kbps; recommended bitrate (LIVE): 250 Kbps. |
| TRTCVideoResolution_256_144 | 102 | Aspect ratio: 16:9; resolution: 256x144; recommended bitrate (VideoCall): 200 Kbps; recommended bitrate (LIVE): 300 Kbps. |
| TRTCVideoResolution_320_180 | 104 | Aspect ratio: 16:9; resolution: 320x180; recommended bitrate (VideoCall): 250 Kbps; recommended bitrate (LIVE): 400 Kbps. |
| TRTCVideoResolution_480_270 | 106 | Aspect ratio: 16:9; resolution: 480x270; recommended bitrate (VideoCall): 350 Kbps; recommended bitrate (LIVE): 550 Kbps. |
| TRTCVideoResolution_640_360 | 108 | Aspect ratio: 16:9; resolution: 640x360; recommended bitrate (VideoCall): 500 Kbps; recommended bitrate (LIVE): 900 Kbps. |
| TRTCVideoResolution_960_540 | 110 | Aspect ratio: 16:9; resolution: 960x540; recommended bitrate (VideoCall): 850 Kbps; recommended bitrate (LIVE): 1300 Kbps. |
| TRTCVideoResolution_1280_720 | 112 | Aspect ratio: 16:9; resolution: 1280x720; recommended bitrate (VideoCall): 1200 Kbps; recommended bitrate (LIVE): 1800 Kbps. |
| TRTCVideoResolution_1920_1080 | 114 | Aspect ratio: 16:9; resolution: 1920x1080; recommended bitrate (VideoCall): 2000 Kbps; recommended bitrate (LIVE): 3000 Kbps. |

## TRTCVideoResolutionMode

**TRTCVideoResolutionMode**

#### Video aspect ratio mode.

Only the landscape resolution (e.g., 640x360) is defined in ` TRTCVideoResolution `. If the portrait resolution (e.g., 360x640) needs to be used, ` Portrait ` must be selected for ` TRTCVideoResolutionMode `.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoResolutionModeLandscape | 0 | Landscape resolution, such as ` TRTCVideoResolution_640_360 + TRTCVideoResolutionModeLandscape = 640x360 `. |
| TRTCVideoResolutionModePortrait | 1 | Portrait resolution, such as ` TRTCVideoResolution_640_360 + TRTCVideoResolutionModePortrait = 360x640 `. |

## TRTCVideoStreamType

**TRTCVideoStreamType**

#### Video stream type.

TRTC provides three different video streams, including:

- HD big image: it is generally used to transfer video data from the camera.
- Smooth small image: it has the same content as the big image, but with lower resolution and bitrate and thus lower definition.
- Substream image: it is generally used for screen sharing. Only one user in the room is allowed to publish the substream video image at any time, while other users must wait for this user to close the substream before they can publish their own substream.

> **Note**The SDK does not support enabling the smooth small image alone, which must be enabled together with the big image. It will automatically set the resolution and bitrate of the small image.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoStreamTypeBig | 0 | HD big image: it is generally used to transfer video data from the camera. |
| TRTCVideoStreamTypeSmall | 1 | Smooth small image: it has the same content as the big image, but with lower resolution and bitrate and thus lower definition. |
| TRTCVideoStreamTypeSub | 2 | Substream image: it is generally used for screen sharing. Only one user in the room is allowed to publish the substream video image at any time, while other users must wait for this user to close the substream before they can publish their own substream. |

## TRTCVideoFillMode

**TRTCVideoFillMode**

#### Video image fill mode.

If the aspect ratio of the video display area is not equal to that of the video image, you need to specify the fill mode:

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoFillMode_Fill | 0 | Fill mode: the video image will be centered and scaled to fill the entire display area, where parts that exceed the area will be cropped. The displayed image may be incomplete in this mode. |
| TRTCVideoFillMode_Fit | 1 | Fit mode: the video image will be scaled based on its long side to fit the display area, where the short side will be filled with black bars. The displayed image is complete in this mode, but there may be black bars. |

## TRTCVideoRotation

**TRTCVideoRotation**

#### Video image rotation direction.

TRTC provides rotation angle setting APIs for local and remote images. The following rotation angles are all clockwise.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoRotation0 | 0 | No rotation |
| TRTCVideoRotation90 | 1 | Clockwise rotation by 90 degrees |
| TRTCVideoRotation180 | 2 | Clockwise rotation by 180 degrees |
| TRTCVideoRotation270 | 3 | Clockwise rotation by 270 degrees |

## TRTCBeautyStyle

**TRTCBeautyStyle**

#### Beauty (skin smoothing) filter algorithm.

TRTC has multiple built-in skin smoothing algorithms. You can select the one most suitable for your product.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCBeautyStyleSmooth | 0 | Smooth style, which uses a more radical algorithm for more obvious effect and is suitable for show live streaming. |
| TRTCBeautyStyleNature | 1 | Natural style, which retains more facial details for more natural effect and is suitable for most live streaming use cases. |

## TRTCVideoPixelFormat

**TRTCVideoPixelFormat**

#### Video pixel format.

TRTC provides custom video capturing and rendering features.

- For the custom capturing feature, you can use the following enumerated values to describe the pixel format of the video you capture.
- For the custom rendering feature, you can specify the pixel format of the video you expect the SDK to call back.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoPixelFormat_Unknown | 0 | Undefined format |
| TRTCVideoPixelFormat_I420 | 1 | YUV420P (I420) format |
| TRTCVideoPixelFormat_Texture_2D | 2 | OpenGL 2D texture format |
| TRTCVideoPixelFormat_BGRA32 | 3 | BGRA32 format |
| TRTCVideoPixelFormat_RGBA32 | 5 | RGBA format |

## TRTCVideoBufferType

**TRTCVideoBufferType**

#### Video data transfer method.

For custom capturing and rendering features, you need to use the following enumerated values to specify the method of transferring video data:

- Method 1. This method uses memory buffer to transfer video data. It is efficient on iOS but inefficient on Android. It is the only method supported on Windows currently.
- Method 2. This method uses texture to transfer video data. It is efficient on both iOS and Android but is not supported on Windows. To use this method, you should have a general familiarity with OpenGL programming.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoBufferType_Unknown | 0 | Undefined transfer method |
| TRTCVideoBufferType_Buffer | 1 | Use memory buffer to transfer video data. iOS: ` PixelBuffer `; Android: ` Direct Buffer ` for JNI layer; Windows: memory data block. |
| TRTCVideoBufferType_Texture | 3 | Use OpenGL texture to transfer video data |

## TRTCVideoMirrorType

**TRTCVideoMirrorType**

#### Video mirror type.

Video mirroring refers to the left-to-right flipping of the video image, especially for the local camera preview image. After mirroring is enabled, it can bring anchors a familiar "look into the mirror" experience.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoMirrorType_Auto | 0 | Auto mode: mirror the front camera's image but not the rear camera's image (for mobile devices only). |
| TRTCVideoMirrorType_Enable | 1 | Mirror the images of both the front and rear cameras. |
| TRTCVideoMirrorType_Disable | 2 | Disable mirroring for both the front and rear cameras. |

## TRTCSnapshotSourceType

**TRTCSnapshotSourceType**

#### Data source of local video screenshot.

The SDK can take screenshots from the following two data sources and save them as local files:

- Video stream: the SDK screencaptures the native video content from the video stream. The screenshots are not controlled by the display of the rendering control.
- Rendering layer: the SDK screencaptures the displayed video content from the rendering control, which can achieve the effect of WYSIWYG, but if the display area is too small, the screenshots will also be very small.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCSnapshotSourceTypeStream | 0 | The SDK screencaptures the native video content from the video stream. The screenshots are not controlled by the display of the rendering control. |
| TRTCSnapshotSourceTypeView | 1 | The SDK screencaptures the displayed video content from the rendering control, which can achieve the effect of WYSIWYG, but if the display area is too small, the screenshots will also be very small. |

## TRTCAppScene

**TRTCAppScene**

#### Use cases.

TRTC features targeted optimizations for common audio/video application scenarios to meet the differentiated requirements in various verticals. The main scenarios can be divided into the following two categories:

- Live streaming scenario (LIVE): including ` LIVE ` (audio + video) and ` VoiceChatRoom ` (pure audio).

In the live streaming scenario, users are divided into two roles: "anchor" and "audience". A single room can sustain up to 100,000 concurrent online users. This is suitable for live streaming to a large audience.

- Real-Time scenario (RTC): including ` VideoCall ` (audio + video) and ` AudioCall ` (pure audio).

In the real-time scenario, there is no role difference between users, but a single room can sustain only up to 300 concurrent online users. This is suitable for small-scale real-time communication.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCAppSceneVideoCall | 0 | In the video call scenario, 720p and 1080p HD image quality is supported. A single room can sustain up to 300 concurrent online users, and up to 50 of them can speak simultaneously.Use cases: [one-to-one video call], [video conferencing with up to 300 participants], [online medical diagnosis], [small class], [video interview], etc. |
| TRTCAppSceneLIVE | 1 | In the interactive video live streaming scenario, mic can be turned on/off smoothly without waiting for switchover, and the anchor latency is as low as less than 300 ms. Live streaming to hundreds of thousands of concurrent users in the audience role is supported with the playback latency down to 1,000 ms.Use cases: [low-latency interactive live streaming], [big class], [anchor competition], [video dating room], [online interactive classroom], [remote training], [large-scale conferencing], etc.**Note**In this scenario, you must use the ` role ` field in ` TRTCParams ` to specify the role of the current user. |
| TRTCAppSceneAudioCall | 2 | Audio call scenario, where the ` SPEECH ` sound quality is used by default. A single room can sustain up to 300 concurrent online users, and up to 50 of them can speak simultaneously.Use cases: [one-to-one audio call], [audio conferencing with up to 300 participants], [audio chat], [online Werewolf], etc. |
| TRTCAppSceneVoiceChatRoom | 3 | In the interactive audio live streaming scenario, mic can be turned on/off smoothly without waiting for switchover, and the anchor latency is as low as less than 300 ms. Live streaming to hundreds of thousands of concurrent users in the audience role is supported with the playback latency down to 1,000 ms.Use cases: [audio club], [online karaoke room], [music live room], [FM radio], etc.**Note**In this scenario, you must use the ` role ` field in ` TRTCParams ` to specify the role of the current user. |

## TRTCRoleType

**TRTCRoleType**

#### Role.

Role is applicable only to live streaming scenarios (` TRTCAppSceneLIVE ` and ` TRTCAppSceneVoiceChatRoom `). Users are divided into two roles:

- Anchor, who can publish their audio/video streams. There is a limit on the number of anchors. Up to 50 anchors are allowed to publish streams at the same time in one room.
- Audience, who can only listen to or watch audio/video streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/72270#a2f85cd8f74124a8d0ec0c8b34d94b01). One room can sustain up to 100,000 concurrent online users in the audience role.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCRoleAnchor | 20 | An anchor can publish their audio/video streams. There is a limit on the number of anchors. Up to 50 anchors are allowed to publish streams at the same time in one room. |
| TRTCRoleAudience | 21 | Audience can only listen to or watch audio/video streams of anchors in the room. If they want to publish their streams, they need to switch to the "anchor" role first through [switchRole](https://www.tencentcloud.com/document/product/647/72270#a2f85cd8f74124a8d0ec0c8b34d94b01). One room can sustain up to 100,000 concurrent online users in the audience role. |

## TRTCQosControlMode(Deprecated)

**TRTCQosControlMode(Deprecated)**

#### QoS control mode (disused).

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCQosControlModeClient | 0 | Client-based control, which is for internal debugging of SDK and shall not be used by users. |
| TRTCQosControlModeServer | 1 | On-cloud control, which is the default and recommended mode. |

## TRTCVideoQosPreference

**TRTCVideoQosPreference**

#### Image quality preference.

TRTC has two control modes in weak network environments: "ensuring clarity" and "ensuring smoothness". Both modes will give priority to the transfer of audio data.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCVideoQosPreferenceSmooth | 1 | Ensuring smoothness: in this mode, when the current network is unable to transfer a clear and smooth video image, the smoothness of the image will be given priority, but there will be blurs. |
| TRTCVideoQosPreferenceClear | 2 | Ensuring clarity (default value): in this mode, when the current network is unable to transfer a clear and smooth video image, the clarity of the image will be given priority, but there will be lags. |

## TRTCQuality

**TRTCQuality**

#### Network quality.

TRTC evaluates the current network quality once every two seconds. The evaluation results are divided into six levels: ` Excellent ` indicates the best, and ` Down ` indicates the worst.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCQuality_Unknown | 0 | Undefined |
| TRTCQuality_Excellent | 1 | The current network is excellent |
| TRTCQuality_Good | 2 | The current network is good |
| TRTCQuality_Poor | 3 | The current network is fair |
| TRTCQuality_Bad | 4 | The current network is bad |
| TRTCQuality_Vbad | 5 | The current network is very bad |
| TRTCQuality_Down | 6 | The current network cannot meet the minimum requirements of TRTC |

## TRTCAVStatusType

**TRTCAVStatusType**

#### Audio/Video playback status.

This enumerated type is used in the audio status changed API onRemoteAudioStatusUpdated and the video status changed API onRemoteVideoStatusUpdated to specify the current audio/video status.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCAVStatusStopped | 0 | Stopped |
| TRTCAVStatusPlaying | 1 | Playing |
| TRTCAVStatusLoading | 2 | Loading |

## TRTCAVStatusChangeReason

**TRTCAVStatusChangeReason**

#### Reasons for playback status changes.

This enumerated type is used in the audio status changed API onRemoteAudioStatusUpdated and the video status changed API onRemoteVideoStatusUpdated to specify the reason for the current audio/video status change.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCAVStatusChangeReasonInternal | 0 | Default value |
| TRTCAVStatusChangeReasonBufferingBegin | 1 | The stream enters the ` Loading ` state due to network congestion |
| TRTCAVStatusChangeReasonBufferingEnd | 2 | The stream enters the ` Playing ` state after network recovery |
| TRTCAVStatusChangeReasonLocalStarted | 3 | As a start-related API was directly called locally, the stream enters the ` Playing ` state |
| TRTCAVStatusChangeReasonLocalStopped | 4 | As a stop-related API was directly called locally, the stream enters the ` Stopped ` state |
| TRTCAVStatusChangeReasonRemoteStarted | 5 | As the remote user started (or resumed) publishing the audio or video stream, the stream enters the ` Loading ` or ` Playing ` state |
| TRTCAVStatusChangeReasonRemoteStopped | 6 | As the remote user stopped (or paused) publishing the audio or video stream, the stream enters the "Stopped" state |

## TRTCAudioQuality

**TRTCAudioQuality**

#### Sound quality.

TRTC provides three well-tuned modes to meet the differentiated requirements for sound quality in various verticals:

- Speech mode (Speech): it is suitable for application scenarios that focus on human communication. In this mode, the audio transfer is more resistant, and TRTC uses various voice processing technologies to ensure the optimal smoothness even in weak network environments.
- Music mode (Music): it is suitable for scenarios with demanding requirements for music. In this mode, the amount of transferred audio data is very large, and TRTC uses various technologies to ensure that the high-fidelity details of music signals can be restored in each frequency band.
- Default mode (Default): it is between ` Speech ` and ` Music `. In this mode, the reproduction of music is better than that in ` Speech ` mode, and the amount of transferred data is much lower than that in ` Music ` mode; therefore, this mode has good adaptability to various scenarios.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCAudioQualitySpeech | 1 | Speech mode: mono channel; bitrate: 18 Kbps. This mode has the best resistance among all modes and is suitable for audio call scenarios, such as online meeting and audio call. |
| TRTCAudioQualityDefault | 2 | Default mode: mono channel; bitrate: 50 Kbps. This mode is between the speech mode and the music mode as the default mode in the SDK and is recommended. |
| TRTCAudioQualityMusic | 3 | Music mode: full-band stereo; bitrate: 128 Kbps. This mode is suitable for scenarios where Hi-Fi music transfer is required, such as online karaoke and music live streaming. |

## TRTCAudioRoute

**TRTCAudioRoute**

#### Audio route (i.e., audio playback mode).

"Audio route" determines whether the sound is played back from the speaker or receiver of a mobile device; therefore, this API is applicable only to mobile devices such as phones.

Generally, a phone has two speakers: one is the receiver at the top, and the other is the stereo speaker at the bottom.

- If the audio route is set to the receiver, the volume is relatively low, and the sound can be heard clearly only when the phone is put near the ear. This mode has a high level of privacy and is suitable for answering calls.
- If the audio route is set to the speaker, the volume is relatively high, so there is no need to put the phone near the ear. Therefore, this mode can implement the "hands-free" feature.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCAudioModeUnknown | -1 | Unknownï¼default router. |
| TRTCAudioModeSpeakerphone | 0 | Speakerphone: the speaker at the bottom is used for playback (hands-free). With relatively high volume, it is used to play music out loud. |
| TRTCAudioModeEarpiece | 1 | Earpiece: the receiver at the top is used for playback. With relatively low volume, it is suitable for call scenarios that require privacy. |
| TRTCAudioModeWiredHeadset | 2 | WiredHeadsetï¼play using wired headphones. |
| TRTCAudioModeBluetoothHeadset | 3 | BluetoothHeadsetï¼play with bluetooth headphones. |
| TRTCAudioModeSoundCard | 4 | SoundCardï¼play using a USB sound card. |

## TRTCAudioFrameFormat

**TRTCAudioFrameFormat**

#### Audio frame content format.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCAudioFrameFormatNone | 0 | None |
| TRTCAudioFrameFormatPCM | 1 | Audio data in PCM format |

## TRTCAudioFrameOperationMode

**TRTCAudioFrameOperationMode**

#### Audio callback data operation mode.

TRTC provides two modes of operation for audio callback data.

- Read-only mode (ReadOnly): Get audio data only from the callback.
- ReadWrite mode (ReadWrite): You can get and modify the audio data of the callback.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCAudioFrameOperationModeReadWrite | 0 | Read-write mode: You can get and modify the audio data of the callback, the default mode. |
| TRTCAudioFrameOperationModeReadOnly | 1 | Read-only mode: Get audio data from callback only. |

## TRTCLogLevel

**TRTCLogLevel**

#### Log level.

Different log levels indicate different levels of details and number of logs. We recommend you set the log level to ` TRTCLogLevelInfo ` generally.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCLogLevelVerbose | 0 | Output logs at all levels |
| TRTCLogLevelDebug | 1 | Output logs at the DEBUG, INFO, WARNING, ERROR, and FATAL levels |
| TRTCLogLevelInfo | 2 | Output logs at the INFO, WARNING, ERROR, and FATAL levels |
| TRTCLogLevelWarn | 3 | Output logs at the WARNING, ERROR, and FATAL levels |
| TRTCLogLevelError | 4 | Output logs at the ERROR and FATAL levels |
| TRTCLogLevelFatal | 5 | Output logs at the FATAL level |
| TRTCLogLevelNone | 6 | Do not output any SDK logs |

## TRTCScreenCaptureSourceType

**TRTCScreenCaptureSourceType**

#### Screen sharing target type (for desktops only).

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCScreenCaptureSourceTypeUnknown | -1 | Undefined |
| TRTCScreenCaptureSourceTypeWindow | 0 | The screen sharing target is the window of an application |
| TRTCScreenCaptureSourceTypeScreen | 1 | The screen sharing target is the entire screen |
| TRTCScreenCaptureSourceTypeCustom | 2 | The screen sharing target is a user-defined data source |

## TRTCTranscodingConfigMode

**TRTCTranscodingConfigMode**

#### Layout mode of On-Cloud MixTranscoding.

TRTC's On-Cloud MixTranscoding service can mix multiple audio/video streams in the room into one stream. Therefore, you need to specify the layout scheme of the video images. The following layout modes are provided:

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCTranscodingConfigMode_Unknown | 0 | Undefined |
| TRTCTranscodingConfigMode_Manual | 1 | Manual layout modeIn this mode, you need to specify the precise position of each video image. This mode has the highest degree of freedom, but its ease of use is the worst: You need to enter all the parameters in [TRTCTranscodingConfig](https://www.tencentcloud.com/document/product/647/72275#c3eef0088da62b5dd27fb0c08db18906), including the position coordinates of each video image (TRTCMixUser). You need to listen on the [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/72271#59380ac1827201d40a1795e59f2f894a) and [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/72271#6d7c1afbfcb241ccb76adf4fcd2a4999) event callbacks in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431) and constantly adjust the ` mixUsers ` parameter according to the audio/video status of each user with mic on in the current room. |
| TRTCTranscodingConfigMode_Template_PureAudio | 2 | Pure audio modeThis mode is suitable for pure audio scenarios such as audio call (AudioCall) and audio chat room (VoiceChatRoom). You only need to set it once through the setMixTranscodingConfig API after room entry, and then the SDK will automatically mix the audio of all mic-on users in the room into the current user's live stream. You don't need to set the ` mixUsers ` parameter in [TRTCTranscodingConfig](https://www.tencentcloud.com/document/product/647/72275#c3eef0088da62b5dd27fb0c08db18906); instead, you only need to set the ` audioSampleRate `, ` audioBitrate ` and ` audioChannels ` parameters. |
| TRTCTranscodingConfigMode_Template_PresetLayout | 3 | Preset layout modeThis is the most popular layout mode, because it allows you to set the position of each video image in advance through placeholders, and then the SDK automatically adjusts it dynamically according to the number of video images in the room.In this mode, you still need to set the ` mixUsers ` parameter, but you can set ` userId ` as a "placeholder". Placeholder values include: "$PLACE_HOLDER_REMOTE$": image of remote user. Multiple images can be set. "$PLACE_HOLDER_LOCAL_MAIN$": local camera image. Only one image can be set. "$PLACE_HOLDER_LOCAL_SUB$": local screen sharing image. Only one image can be set.In this mode, you don't need to listen on the [onUserVideoAvailable](https://www.tencentcloud.com/document/product/647/72271#59380ac1827201d40a1795e59f2f894a) and [onUserAudioAvailable](https://www.tencentcloud.com/document/product/647/72271#6d7c1afbfcb241ccb76adf4fcd2a4999) callbacks in [ITRTCCloudCallback](https://www.tencentcloud.com/document/product/647/72271#338fdd109b5c9711d47c618b7d14b431) to make real-time adjustments.Instead, you only need to call setMixTranscodingConfig once after successful room entry. Then, the SDK will automatically populate the placeholders you set with real ` userId ` values. |
| TRTCTranscodingConfigMode_Template_ScreenSharing | 4 | Screen sharing modeThis mode is suitable for screen sharing-based use cases such as online education and supported only by the SDKs for Windows and macOS.In this mode, the SDK will first build a canvas according to the target resolution you set (through the ` videoWidth ` and ` videoHeight ` parameters). Before the teacher enables screen sharing, the SDK will scale up the teacher's camera image and draw it onto the canvas. After the teacher enables screen sharing, the SDK will draw the video image shared on the screen onto the same canvas.The purpose of this layout mode is to ensure consistency in the output resolution of the mixtranscoding module and avoid problems with blurred screen during course replay and webpage playback (web players don't support adjustable resolution).Meanwhile, the audio of mic-on students will be mixed into the teacher's audio/video stream by default.Video content is primarily the shared screen in teaching mode, and it is a waste of bandwidth to transfer camera image and screen image at the same time.Therefore, the recommended practice is to directly draw the camera image onto the current screen through the [setLocalVideoRenderCallback](https://www.tencentcloud.com/document/product/647/72270#90446bafe45e8f227390ec15613cbcf7) API.In this mode, you don't need to set the ` mixUsers ` parameter in [TRTCTranscodingConfig](https://www.tencentcloud.com/document/product/647/72275#c3eef0088da62b5dd27fb0c08db18906), and the SDK will not mix students' images so as not to interfere with the screen sharing effect.You can set width x height in [TRTCTranscodingConfig](https://www.tencentcloud.com/document/product/647/72275#c3eef0088da62b5dd27fb0c08db18906) to 0 px x 0 px, and the SDK will automatically calculate a suitable resolution based on the aspect ratio of the user's current screen. If the teacher's current screen width is less than or equal to 1920 px, the SDK will use the actual resolution of the teacher's current screen. If the teacher's current screen width is greater than 1920 px, the SDK will select one of the three resolutions of 1920x1080 (16:9), 1920x1200 (16:10), and 1920x1440 (4:3) according to the current screen aspect ratio. |

## TRTCRecordType

**TRTCRecordType**

#### Media recording type.

This enumerated type is used in the local media recording API [startLocalRecording](https://www.tencentcloud.com/document/product/647/72270#c0358d2dce89b4c19aa824350e2db40d) to specify whether to record audio/video files or pure audio files.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCLocalRecordType_Audio | 0 | Record audio only |
| TRTCLocalRecordType_Video | 1 | Record video only |
| TRTCLocalRecordType_Both | 2 | Record both audio and video |

## TRTCMixInputType

**TRTCMixInputType**

#### Stream mix input type.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCMixInputTypeUndefined | 0 | Default.Considering the compatibility with older versions, if you specify the inputType as Undefined, the SDK will determine the stream mix input type according to the value of the ` pureAudio ` parameter |
| TRTCMixInputTypeAudioVideo | 1 | Mix both audio and video |
| TRTCMixInputTypePureVideo | 2 | Mix video only |
| TRTCMixInputTypePureAudio | 3 | Mix audio only |
| TRTCMixInputTypeWatermark | 4 | Mix watermarkIn this case, you don't need to specify the ` userId ` parameter, but you need to specify the ` image ` parameter. It is recommended to use png format. |

## TRTCWaterMarkSrcType

**TRTCWaterMarkSrcType**

#### Watermark image source type.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCWaterMarkSrcTypeFile | 0 | Path of the image file, which can be in BMP, GIF, JPEG, PNG, TIFF, Exif, WMF, or EMF format |
| TRTCWaterMarkSrcTypeBGRA32 | 1 | Memory block in BGRA32 format |
| TRTCWaterMarkSrcTypeRGBA32 | 2 | Memory block in RGBA32 format |

## TRTCAudioRecordingContent

**TRTCAudioRecordingContent**

#### Audio recording content type.

This enumerated type is used in the audio recording API startAudioRecording to specify the content of the recorded audio.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCAudioRecordingContentAll | 0 | Record both local and remote audio |
| TRTCAudioRecordingContentLocal | 1 | Record local audio only |
| TRTCAudioRecordingContentRemote | 2 | Record remote audio only |

## TRTCPublishMode

**TRTCPublishMode**

#### The publishing mode.

This enum type is used by the publishing API [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

TRTC can mix multiple streams in a room and publish the mixed stream to a CDN or to a TRTC room. It can also publish the stream of the local user to Tencent Cloud or a third-party CDN.

You can specify one of the following publishing modes to use:

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCPublishModeUnknown | 0 | Undefined |
| TRTCPublishBigStreamToCdn | 1 | Use this parameter to publish the primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)) in the room to Tencent Cloud or a third-party CDN (only RTMP is supported). |
| TRTCPublishSubStreamToCdn | 2 | Use this parameter to publish the substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)) in the room to Tencent Cloud or a third-party CDN (only RTMP is supported). |
| TRTCPublishMixStreamToCdn | 3 | Use this parameter together with the encoding parameter [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72275#22718fe81d94d21ec895cbc11820c726) and On-Cloud MixTranscoding parameter [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166) to transcode the streams you specify and publish the mixed stream to Tencent Cloud or a third-party CDN (only RTMP is supported). |
| TRTCPublishMixStreamToRoom | 4 | Use this parameter together with the encoding parameter [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72275#22718fe81d94d21ec895cbc11820c726) and On-Cloud MixTranscoding parameter [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166) to transcode the streams you specify and publish the mixed stream to the room you specify. Use ` TRTCUser ` in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49) to specify the robot that publishes the transcoded stream to a TRTC room. |

## TRTCEncryptionAlgorithm

**TRTCEncryptionAlgorithm**

#### Encryption Algorithm.

This enumeration type is used for media stream private encryption algorithm selection.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCEncryptionAlgorithmAes128Gcm | 0 | AES GCM 128ã |
| TRTCEncryptionAlgorithmAes256Gcm | 1 | AES GCM 256ã |

## TRTCSpeedTestScene

**TRTCSpeedTestScene**

#### Speed Test Scene.

This enumeration type is used for speed test scene selection.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCSpeedTestScene_DelayTesting | 1 | Delay testing. |
| TRTCSpeedTestScene_DelayAndBandwidthTesting | 2 | Delay and bandwidth testing. |
| TRTCSpeedTestScene_OnlineChorusTesting | 3 | Online chorus testing. |

## TRTCGravitySensorAdaptiveMode

**TRTCGravitySensorAdaptiveMode**

#### Set the adaptation mode of gravity sensing (only applicable to mobile terminals).

Begin from v11.7 versionï¼It only takes effect when the camera capture scene inside SDK is used.

| Enum | Value | DESC |
| --- | --- | --- |
| TRTCGravitySensorAdaptiveMode_Disable | 0 | Turn off the gravity sensor and make a decision based on the current acquisition resolution and the set encoding resolution. If the two are inconsistent, rotate 90 degrees to ensure the maximum frame. |
| TRTCGravitySensorAdaptiveMode_FillByCenterCrop | 1 | Turn on the gravity sensor to always ensure that the remote screen image is positive. When the intermediate process needs to deal with inconsistent resolutions, use the center cropping mode. |
| TRTCGravitySensorAdaptiveMode_FitWithBlackBorder | 2 | Turn on the gravity sensor to always ensure that the remote screen image is positive. When the resolution needs to be processed inconsistently in the intermediate process, use the superimposed black border mode. |

## TRTCParams

**TRTCParams**

#### Room entry parameters.

As the room entry parameters in the TRTC SDK, these parameters must be correctly set so that the user can successfully enter the audio/video room specified by ` roomId ` or ` strRoomId `.

For historical reasons, TRTC supports two types of room IDs: ` roomId ` and ` strRoomId `.

Note: do not mix ` roomId ` and ` strRoomId `, because they are not interchangeable. For example, the number ` 123 ` and the string ` 123 ` are two completely different rooms in TRTC.

| EnumType | DESC |
| --- | --- |
| businessInfo | Field description: business data, which is optional. This field is needed only by some advanced features.Recommended value: do not set this field on your own. |
| privateMapKey | Field description: permission credential used for permission control, which is optional. If you want only users with the specified ` userId ` values to enter a room, you need to use ` privateMapKey ` to restrict the permission.Recommended value: we recommend you use this parameter only if you have high security requirements. For more information, please see [Enabling Advanced Permission Control](https://www.tencentcloud.com/document/product/647/35157). |
| role | Field description: role in the live streaming scenario, which is applicable only to the live streaming scenario ([TRTCAppSceneLIVE](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1) or [TRTCAppSceneVoiceChatRoom](https://www.tencentcloud.com/document/product/647/72275#50498dba914e98bc767b83dc0c72a0a1)) but doesn't take effect in the call scenario.Recommended value: default value: anchor ([TRTCRoleAnchor](https://www.tencentcloud.com/document/product/647/72275#874dbd6062bbf1384648ca9f9054aa5b)). |
| roomId | Field description: numeric room ID. Users (userId) in the same room can see one another and make audio/video calls.Recommended value: value range: 1â4294967294.@note ` roomId ` and ` strRoomId ` are mutually exclusive. If you decide to use ` strRoomId `, then ` roomId ` should be entered as 0. If both are entered, ` roomId ` will be used.**Note**do not mix ` roomId ` and ` strRoomId `, because they are not interchangeable. For example, the number ` 123 ` and the string ` 123 ` are two completely different rooms in TRTC. |
| sdkAppId | Field description: application ID, which is required. Tencent Cloud generates bills based on ` sdkAppId `.Recommended value: the ID can be obtained on the account information page in the [TRTC console](https://console.tencentcloud.com/rav/) after the corresponding application is created. |
| strRoomId | Field description: string-type room ID. Users (userId) in the same room can see one another and make audio/video calls.@note ` roomId ` and ` strRoomId ` are mutually exclusive. If you decide to use ` strRoomId `, then ` roomId ` should be entered as 0. If both are entered, ` roomId ` will be used.**Note**do not mix ` roomId ` and ` strRoomId `, because they are not interchangeable. For example, the number ` 123 ` and the string ` 123 ` are two completely different rooms in TRTC.Recommended value: the length limit is 64 bytes. The following 89 characters are supported: Uppercase and lowercase letters (aâz and AâZ) Digits (0â9) Space, "!", "#", "$", "%", "&", "(", ")", "+", "-", ":", ";", "<", "=", ".", ">", "?", "@", "[", "]", "^", "_", "{", "}", "\|", "~", and ",". |
| streamId | Field description: specified ` streamId ` in Tencent Cloud CSS, which is optional. After setting this field, you can play back the user's audio/video stream on Tencent Cloud CSS CDN through a standard pull scheme (FLV or HLS).Recommended value: this parameter can contain up to 64 bytes and can be left empty. We recommend you use ` sdkappid_roomid_userid_main ` as the ` streamid `, which is easier to identify and will not cause conflicts in your multiple applications.**Note**to use Tencent Cloud CSS CDN, you need to enable the auto-relayed live streaming feature on the "Function Configuration" page in the [console](https://console.tencentcloud.com/trtc/) first.For more information, please see [Relay to CDN](https://www.tencentcloud.com/document/product/647/47858). |
| userDefineRecordId | Field description: on-cloud recording field, which is optional and used to specify whether to record the user's audio/video stream in the cloud.For more information, please see [On-Cloud Recording](https://www.tencentcloud.com/document/product/647/45169).Recommended value: it can contain up to 64 bytes. Letters (aâz and AâZ), digits (0â9), underscores, and hyphens are allowed.Scheme 1. Manual recording1. Enable on-cloud recording in "Application Management" > "On-cloud Recording Configuration" in the [console](https://console.tencentcloud.com/trtc).2. Set "Recording Mode" to "Manual Recording".3. After manual recording is set, in a TRTC room, only users with the ` userDefineRecordId ` parameter set will have video recording files in the cloud, while users without this parameter set will not.4. The recording file will be named in the format of "userDefineRecordId_start time_end time" in the cloud.Scheme 2. Auto-recording1. You need to enable on-cloud recording in "Application Management" > "On-cloud Recording Configuration" in the [console](https://console.tencentcloud.com/trtc).2. Set "Recording Mode" to "Auto-recording".3. After auto-recording is set, any user who upstreams audio/video in a TRTC room will have a video recording file in the cloud.4. The file will be named in the format of "userDefineRecordId_start time_end time". If ` userDefineRecordId ` is not specified, the file will be named in the format of "streamId_start time_end time". |
| userId | Field description: user ID, which is required. It is the ` userId ` of the local user in UTF-8 encoding and acts as the username.Recommended value: if the ID of a user in your account system is "mike", ` userId ` can be set to "mike". |
| userSig | Field description: user signature, which is required. It is the authentication signature corresponding to the current ` userId ` and acts as the login password for Tencent Cloud services.Recommended value: for the calculation method, please see [UserSig](https://www.tencentcloud.com/document/product/647/35166). |

## TRTCVideoEncParam

**TRTCVideoEncParam**

#### Video encoding parameters.

These settings determine the quality of image viewed by remote users as well as the image quality of recorded video files in the cloud.

| EnumType | DESC |
| --- | --- |
| enableAdjustRes | Field description: whether to allow dynamic resolution adjustment. Once enabled, this field will affect on-cloud recording.Recommended value: this feature is suitable for scenarios that don't require on-cloud recording. After it is enabled, the SDK will intelligently select a suitable resolution according to the current network conditions to avoid the inefficient encoding mode of "large resolution + small bitrate".**Note**default value: false. If you need on-cloud recording, please do not enable this feature, because if the video resolution changes, the MP4 file recorded in the cloud cannot be played back normally by common players. |
| minVideoBitrate | Field description: minimum video bitrate. The SDK will reduce the bitrate to as low as the value specified by ` minVideoBitrate ` to ensure the smoothness only if the network conditions are poor.Note: default value: 0, indicating that a reasonable value of the lowest bitrate will be automatically calculated by the SDK according to the resolution you specify.Recommended value: you can set the ` videoBitrate ` and ` minVideoBitrate ` parameters at the same time to restrict the SDK's adjustment range of the video bitrate: If you want to "ensure clarity while allowing lag in weak network environments", you can set ` minVideoBitrate ` to 60% of ` videoBitrate `. If you want to "ensure smoothness while allowing blur in weak network environments", you can set ` minVideoBitrate ` to a low value, for example, 100 Kbps. If you set ` videoBitrate ` and ` minVideoBitrate ` to the same value, it is equivalent to disabling the adaptive adjustment capability of the SDK for the video bitrate. |
| resMode | Field description: resolution mode (landscape/portrait)Recommended value: for mobile platforms (iOS and Android), ` Portrait ` is recommended; for desktop platforms (Windows and macOS), ` Landscape ` is recommended.**Note**to use a portrait resolution, please specify ` resMode ` as ` Portrait `; for example, when used together with ` Portrait `, 640x360 represents 360x640. |
| videoBitrate | Field description: target video bitrate. The SDK encodes streams at the target video bitrate and will actively reduce the bitrate only in weak network environments.Recommended value: please see the optimal bitrate for each specification in ` TRTCVideoResolution `. You can also slightly increase the optimal bitrate.For example, ` TRTCVideoResolution_1280_720 ` corresponds to the target bitrate of 1,200 Kbps. You can also set the bitrate to 1,500 Kbps for higher definition.**Note**you can set the ` videoBitrate ` and ` minVideoBitrate ` parameters at the same time to restrict the SDK's adjustment range of the video bitrate: If you want to "ensure clarity while allowing lag in weak network environments", you can set ` minVideoBitrate ` to 60% of ` videoBitrate `. If you want to "ensure smoothness while allowing blur in weak network environments", you can set ` minVideoBitrate ` to a low value, for example, 100 Kbps. If you set ` videoBitrate ` and ` minVideoBitrate ` to the same value, it is equivalent to disabling the adaptive adjustment capability of the SDK for the video bitrate. |
| videoFps | Field description: video capturing frame rateRecommended value: 15 or 20 fps. If the frame rate is lower than 5 fps, there will be obvious lagging; if lower than 10 fps but higher than 5 fps, there will be slight lagging; if higher than 20 fps, the bandwidth will be wasted (the frame rate of movies is generally 24 fps).**Note**the front cameras on certain Android phones do not support a capturing frame rate higher than 15 fps. For some Android phones that focus on beautification features, the capturing frame rate of the front cameras may be lower than 10 fps. |
| videoResolution | Field description: video resolutionRecommended value For mobile video call, we recommend you select a resolution of 360x640 or below and select ` Portrait ` (portrait resolution) for ` resMode `. For mobile live streaming, we recommend you select a resolution of 540x960 and select ` Portrait ` (portrait resolution) for ` resMode `. For desktop platforms (Windows and macOS), we recommend you select a resolution of 640x360 or above and select ` Landscape ` (landscape resolution) for ` resMode `.**Note**to use a portrait resolution, please specify ` resMode ` as ` Portrait `; for example, when used together with ` Portrait `, 640x360 represents 360x640. |

## TRTCNetworkQosParam

**TRTCNetworkQosParam**

#### Network QoS control parameter set.

Network QoS control parameter. The settings determine the QoS control policy of the SDK in weak network conditions (e.g., whether to "ensure clarity" or "ensure smoothness").

| EnumType | DESC |
| --- | --- |
| controlMode | Field description: QoS control mode (disused)Recommended value: on-cloud control**Note**please set the on-cloud control mode (TRTCQosControlModeServer). |
| preference | Field description: whether to ensure smoothness or clarityRecommended value: ensuring clarity**Note**this parameter mainly affects the audio/video performance of TRTC in weak network environments: Ensuring smoothness: in this mode, when the current network is unable to transfer a clear and smooth video image, the smoothness of the image will be given priority, but there will be blurs. See [TRTCVideoQosPreferenceSmooth](https://www.tencentcloud.com/document/product/647/72275#e1af969d7b99606d3c064b5482ed4cfe) Ensuring clarity (default value): in this mode, when the current network is unable to transfer a clear and smooth video image, the clarity of the image will be given priority, but there will be lags. See [TRTCVideoQosPreferenceClear](https://www.tencentcloud.com/document/product/647/72275#e1af969d7b99606d3c064b5482ed4cfe) |

## TRTCRenderParams

**TRTCRenderParams**

#### Rendering parameters of video image.

You can use these parameters to control the video image rotation angle, fill mode, and mirror mode.

| EnumType | DESC |
| --- | --- |
| fillMode | Field description: image fill modeRecommended value: fill (the image may be stretched or cropped) or fit (there may be black bars in unmatched areas). Default value: [TRTCVideoFillMode_Fill](https://www.tencentcloud.com/document/product/647/72275#b3c03b374c30311eef2887dc4799347f) |
| mirrorType | Field description: image mirror modeRecommended value: default value: [TRTCVideoMirrorType_Auto](https://www.tencentcloud.com/document/product/647/72275#21ddf23a6e62530028a4bd15ecd2387e) |
| rotation | Field description: clockwise image rotation angleRecommended value: rotation angles of 90, 180, and 270 degrees are supported. Default value: [TRTCVideoRotation0](https://www.tencentcloud.com/document/product/647/72275#3a45499a02ba68182709073cc7e29b4c) |

## TRTCQualityInfo

**TRTCQualityInfo**

#### Network quality.

This indicates the quality of the network. You can use it to display the network quality of each user on the UI.

| EnumType | DESC |
| --- | --- |
| quality | Network quality |
| userId | User ID |

## TRTCVolumeInfo

**TRTCVolumeInfo**

#### Volume.

This indicates the audio volume value. You can use it to display the volume of each user in the UI.

| EnumType | DESC |
| --- | --- |
| pitch | The local user's vocal frequency (unit: Hz), the value range is [0 - 4000]. For remote users, this value is always 0. |
| spectrumData | Audio spectrum data, which divides the sound frequency into 256 frequency domains, spectrumData records the energy value of each frequency domain,The value range of each energy value is [-300, 0] in dBFS.**Note**The local spectrum is calculated using the audio data before encoding, which will be affected by the capture volume, BGM, etc.; the remote spectrum is calculated using the received audio data, and operations such as adjusting the remote playback volume locally will not affect it. |
| userId | ` userId ` of the speaker. An empty value indicates the local user. |
| vad | Vad result of the local user. 0: not speech 1: speech. |
| volume | Volume of the speaker. Value range: 0â100. |

## TRTCSpeedTestParams

**TRTCSpeedTestParams**

#### Network speed testing parameters.

You can test the network speed through the startSpeedTest: interface before the user enters the room (this API cannot be called during a call).

| EnumType | DESC |
| --- | --- |
| expectedDownBandwidth | Expected downstream bandwidth (kbps, value range: 10 to 5000, no downlink bandwidth test when it is 0).**Note**When the parameter ` scene ` is set to [TRTCSpeedTestScene_OnlineChorusTesting](https://www.tencentcloud.com/document/product/647/72275#d3063c0cbe17f166846aa9b251aa0878), in order to obtain more accurate information such as ` rtt / jitter `, the value range is limited to [10, 1000]. |
| expectedUpBandwidth | Expected upstream bandwidth (kbps, value range: 10 to 5000, no uplink bandwidth test when it is 0).**Note**When the parameter ` scene ` is set to [TRTCSpeedTestScene_OnlineChorusTesting](https://www.tencentcloud.com/document/product/647/72275#d3063c0cbe17f166846aa9b251aa0878), in order to obtain more accurate information such as ` rtt / jitter `, the value range is limited to [10, 1000]. |
| scene | Speed test scene. |
| sdkAppId | Application identification, please refer to the relevant instructions in [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190). |
| userId | User identification, please refer to the relevant instructions in [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190). |
| userSig | User signature, please refer to the relevant instructions in [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190). |

## TRTCSpeedTestResult

**TRTCSpeedTestResult**

#### Network speed test result.

The startSpeedTest: API can be used to test the network speed before a user enters a room (this API cannot be called during a call).

| EnumType | DESC |
| --- | --- |
| availableDownBandwidth | Downstream bandwidth (in kbps, -1: invalid value). |
| availableUpBandwidth | Upstream bandwidth (in kbps, -1: invalid value). |
| downJitter | Downlink data packet jitter (ms) refers to the stability of data communication in the user's current network environment. The smaller the value, the better. The normal value range is [0, 100]. -1 means that the speed test failed to obtain an effective value. Generally, the Jitter of the WiFi network will be slightly larger than that of the 4G/5G environment. |
| downLostRate | Downstream packet loss rate between 0 and 1.0. For example, 0.2 indicates that 2 data packets may be lost in every 10 packets received from the server. |
| errMsg | Error message for network speed test. |
| ip | Server IP address. |
| quality | Network quality, which is tested and calculated based on the internal evaluation algorithm. For more information, please see [TRTCQuality](https://www.tencentcloud.com/document/product/647/72275#1d80134eda8e3a1608daa960ed67d092) |
| rtt | Delay in milliseconds, which is the round-trip time between the current device and TRTC server. The smaller the value, the better. The normal value range is 10â100 ms. |
| success | Whether the network speed test is successful. |
| upJitter | Uplink data packet jitter (ms) refers to the stability of data communication in the user's current network environment. The smaller the value, the better. The normal value range is [0, 100]. -1 means that the speed test failed to obtain an effective value. Generally, the Jitter of the WiFi network will be slightly larger than that of the 4G/5G environment. |
| upLostRate | Upstream packet loss rate between 0 and 1.0. For example, 0.3 indicates that 3 data packets may be lost in every 10 packets sent to the server. |

## TRTCVideoFrame

**TRTCVideoFrame**

#### Video frame information.

` TRTCVideoFrame ` is used to describe the raw data of a frame of the video image, which is the image data before frame encoding or after frame decoding.

| EnumType | DESC |
| --- | --- |
| bufferType | Field description: video data structure type |
| data | Field description: video data when ` bufferType ` is [TRTCVideoBufferType_Buffer](https://www.tencentcloud.com/document/product/647/72275#133a51a3a497d78c2b4d5de72ec7aaeb), which carries the memory data blocks for the C++ layer. |
| height | Field description: video heightRecommended value: please enter the height of the video data passed in. |
| length | Field description: video data length in bytes. For I420, length = width * height * 3 / 2; for BGRA32, length = width * height * 4. |
| rotation | Field description: clockwise rotation angle of video pixels |
| textureId | Field description: video data when ` bufferType ` is [TRTCVideoBufferType_Texture](https://www.tencentcloud.com/document/product/647/72275#133a51a3a497d78c2b4d5de72ec7aaeb), which carries the texture data used for OpenGL rendering. |
| timestamp | Field description: video frame timestamp in millisecondsRecommended value: this parameter can be set to 0 for custom video capturing. In this case, the SDK will automatically set the ` timestamp ` field. However, please "evenly" set the calling interval of [sendCustomVideoData](https://www.tencentcloud.com/document/product/647/72270#8c8378c65a0b11187d6812523706a9f0). |
| videoFormat | Field description: video pixel format |
| width | Field description: video widthRecommended value: please enter the width of the video data passed in. |

## TRTCAudioFrame

**TRTCAudioFrame**

#### Audio frame data.

| EnumType | DESC |
| --- | --- |
| audioFormat | Field description: audio frame format |
| channel | Field description: number of sound channels |
| data | Field description: audio data |
| extraData | Field description: extra data in audio frame, message sent by remote users through [onLocalProcessedAudioFrame](https://www.tencentcloud.com/document/product/647/72271#7013577cbc775c66b7d94a1299b86a64) that add to audio frame will be callback through this field. |
| extraDatalength | Field description: extra data length |
| length | Field description: audio data length |
| sampleRate | Field description: sample rate |
| timestamp | Field description: timestamp in ms |

## TRTCMixUser

**TRTCMixUser**

#### Description information of each video image in On-Cloud MixTranscoding.

` TRTCMixUser ` is used to specify the location, size, layer, and stream type of each video image in On-Cloud MixTranscoding.

| EnumType | DESC |
| --- | --- |
| image | Field description: specify the placeholder or watermark image. The placeholder image will be displayed when there is no upstream video.A watermark image is a semi-transparent image posted in the mixed image, and this image will always be overlaid on the mixed image. When the ` inputType ` field is set to [TRTCMixInputTypePureAudio](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6), the image is a placeholder image, and you need to specify ` userId `. When the ` inputType ` field is set to [TRTCMixInputTypeWatermark](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6), the image is a watermark image, and you don't need to specify ` userId `.Recommended value: default value: null, indicating not to set the placeholder or watermark image.**Note**TRTC's backend service will mix the image specified by the URL address into the final stream.URL link length is limited to 512 bytes. The image size is limited to 10MB.Support png, jpg, jpeg, bmp format. Take effects iff the ` inputType ` field is set to [TRTCMixInputTypePureAudio](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6) or [TRTCMixInputTypeWatermark](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6). |
| inputType | Field description: specify the mixed content of this stream (audio only, video only, audio and video, or watermark).Recommended value: default value: [TRTCMixInputTypeUndefined](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6).**Note** When specifying ` inputType ` as [TRTCMixInputTypeUndefined](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6) and specifying ` pureAudio ` to YES, it is equivalent to setting ` inputType ` to ` TRTCMixInputTypePureAudio `. When specifying ` inputType ` as [TRTCMixInputTypeUndefined](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6) and specifying ` pureAudio ` to NO, it is equivalent to setting ` inputType ` to ` TRTCMixInputTypeAudioVideo `. When specifying ` inputType ` as [TRTCMixInputTypeWatermark](https://www.tencentcloud.com/document/product/647/72275#c0ab99ff8ae7d990d3a535e916fcd0f6), you don't need to specify the ` userId ` field, but you need to specify the ` image ` field. |
| pureAudio | Field description: specify whether this stream mixes audio onlyRecommended value: default value: false**Note**this field has been disused. We recommend you use the new field ` inputType ` introduced in v8.5. |
| rect | Field description: specify the coordinate area of this video image in px |
| renderMode | Field description: specify the display mode of this stream.Recommended value: default value: 0. 0 is cropping, 1 is zooming, 2 is zooming and displaying black background.**Note**image doesn't support setting ` renderMode ` temporarily, the default display mode is forced stretch. |
| roomId | Field description: ID of the room where this audio/video stream is located (an empty value indicates the local room ID) |
| soundLevel | Field description: specify the target volumn level of On-Cloud MixTranscoding. (value range: 0-100)Recommended value: default value: 100. |
| streamType | Field description: specify whether this video image is the primary stream image ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)) or substream image ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)). |
| userId | Field description: user ID |
| zOrder | Field description: specify the level of this video image (value range: [1, 15]; the value must be unique) |

## TRTCTranscodingConfig

**TRTCTranscodingConfig**

#### Layout and transcoding parameters of On-Cloud MixTranscoding.

These parameters are used to specify the layout position information of each video image and the encoding parameters of mixtranscoding during On-Cloud MixTranscoding.

| EnumType | DESC |
| --- | --- |
| appId | Field description: ` appId ` of Tencent Cloud CSSRecommended value: please click ` Application Management ` > ` Application Information ` in the [TRTC console](https://console.tencentcloud.com/trtc) and get the ` appId ` in ` Relayed Live Streaming Info `.**Note**applications created on or after January 9, 2020 do not need to fill in this field. |
| audioBitrate | Field description: specify the target audio bitrate of On-Cloud MixTranscodingRecommended value: default value: 64 Kbps. Value range: [32,192]. |
| audioChannels | Field description: specify the number of sound channels of On-Cloud MixTranscodingRecommended value: default value: 1, which means mono channel. Valid values: 1: mono channel; 2: dual channel. |
| audioCodec | Field description: specify the audio encoding type of On-Cloud MixTranscodingRecommended value: default value: 0, which means LC-AAC. Valid values: 0:  LC-AAC; 1: HE-AAC; 2: HE-AACv2.**Note** HE-AAC and HE-AACv2 only support [48000, 44100, 32000, 24000, 16000]  sample rate. HE-AACv2  only support dual channel. HE-AAC and HE-AACv2 take effects iff the output streamId is specified. |
| audioSampleRate | Field description: specify the target audio sample rate of On-Cloud MixTranscodingRecommended value: default value: 48000 Hz. Valid values: 12000 Hz, 16000 Hz, 22050 Hz, 24000 Hz, 32000 Hz, 44100 Hz, 48000 Hz. |
| backgroundColor | Field description: specify the background color of the mixed video image.Recommended value: default value: 0x000000, which means black and is in the format of hex number; for example: "0x61B9F1" represents the RGB color (97,158,241). |
| backgroundImage | Field description: specify the background image of the mixed video image.**Recommended value: default value: null, indicating not to set the background image.**Note**TRTC's backend service will mix the image specified by the URL address into the final stream.URL link length is limited to 512 bytes. The image size is limited to 10MB.Support png, jpg, jpeg, bmp format. |
| bizId | Field description: ` bizId ` of Tencent Cloud CSSRecommended value: please click ` Application Management ` > ` Application Information ` in the [TRTC console](https://console.tencentcloud.com/trtc) and get the ` bizId ` in ` Relayed Live Streaming Info `.**Note**applications created on or after January 9, 2020 do not need to fill in this field. |
| mixUsersArray | Field description: specify the position, size, layer, and stream type of each video image in On-Cloud MixTranscodingRecommended value: this field is an array in ` TRTCMixUser ` type, where each element represents the information of a video image. |
| mixUsersArraySize | Field description: number of elements in the ` mixUsersArray ` array |
| mode | Field description: layout modeRecommended value: please choose a value according to your business needs. The preset mode has better applicability. |
| streamId | Field description: ID of the live stream output to CDNRecommended value: default value: null, that is, the audio/video streams in the room will be mixed into the audio/video stream of the caller of this API. If you don't set this parameter, the SDK will execute the default logic, that is, it will mix the multiple audio/video streams in the room into the audio/video stream of the caller of this API, i.e., A + B => A. If you set this parameter, the SDK will mix the audio/video streams in the room into the live stream you specify, i.e., A + B => C (C is the ` streamId ` you specify). |
| videoBitrate | Field description: specify the target video bitrate (Kbps) of On-Cloud MixTranscodingRecommended value: if you enter 0, TRTC will estimate a reasonable bitrate value based on ` videoWidth ` and ` videoHeight `. You can also refer to the recommended bitrate value in the video resolution enumeration definition (in the comment section). |
| videoFramerate | Field description: specify the target video frame rate (fps) of On-Cloud MixTranscodingRecommended value: default value: 15 fps. Value range: (0,30]. |
| videoGOP | Field description: specify the target video keyframe interval (GOP) of On-Cloud MixTranscodingRecommended value: default value: 2 (in seconds). Value range: [1,8]. |
| videoHeight | Field description: specify the target resolution (height) of On-Cloud MixTranscodingRecommended value: 640 px. If you only mix audio streams, please set both ` width ` and ` height ` to 0; otherwise, there will be a black background in the live stream after mixtranscoding. |
| videoSeiParams | Field description: SEI parameters. default value: null**Note**the parameter is passed in the form of a JSON string. Here is an example to use it:` ``json{"payLoadContent":"xxx","payloadType":5,"payloadUuid":"1234567890abcdef1234567890abcdef","interval":1000,"followIdr":false}` ``The currently supported fields and their meanings are as follows: payloadContent: Required. The payload content of the passthrough SEI, which cannot be empty. payloadType: Required. The type of the SEI message, with a value range of 5 or an integer within the range of [100, 254] (excluding 244, which is an internally defined timestamp SEI). payloadUuid: Required when payloadType is 5, and ignored in other cases. The value must be a 32-digit hexadecimal number. interval: Optional, default is 1000. The sending interval of the SEI, in milliseconds. followIdr: Optional, default is false. When this value is true, the SEI will be ensured to be carried when sending a key frame, otherwise it is not guaranteed. |
| videoWidth | Field description: specify the target resolution (width) of On-Cloud MixTranscodingRecommended value: 360 px. If you only mix audio streams, please set both ` width ` and ` height ` to 0; otherwise, there will be a black background in the live stream after mixtranscoding. |

## TRTCPublishCDNParam

**TRTCPublishCDNParam**

#### Push parameters required to be set when publishing audio/video streams to non-Tencent Cloud CDN.

TRTC's backend service supports publishing audio/video streams to third-party live CDN service providers through the standard RTMP protocol.

If you use the Tencent Cloud CSS CDN service, you don't need to care about this parameter; instead, just use the [startPublish](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4) API.

| EnumType | DESC |
| --- | --- |
| appId | Field description: ` appId ` of Tencent Cloud CSSRecommended value: please click ` Application Management ` > ` Application Information ` in the [TRTC console](https://console.tencentcloud.com/trtc) and get the ` appId ` in ` Relayed Live Streaming Info `. |
| bizId | Field description: ` bizId ` of Tencent Cloud CSSRecommended value: please click ` Application Management ` > ` Application Information ` in the [TRTC console](https://console.tencentcloud.com/trtc) and get the ` bizId ` in ` Relayed Live Streaming Info `. |
| streamId | Field description: specify the push address (in RTMP format) of this audio/video stream at the third-party live streaming service providerRecommended value: default value: null,that is, the audio/video streams in the room will be pushed to the target service provider of the caller of this API. |
| url | Field description: specify the push address (in RTMP format) of this audio/video stream at the third-party live streaming service providerRecommended value: the push URL rules vary greatly by service provider. Please enter a valid push URL according to the requirements of the target service provider. TRTC's backend server will push audio/video streams in the standard format to the third-party service provider according to the URL you enter.**Note**the push URL must be in RTMP format and meet the specifications of your target live streaming service provider; otherwise, the target service provider will reject the push requests from TRTC's backend service. |

## TRTCAudioRecordingParams

**TRTCAudioRecordingParams**

#### Local audio file recording parameters.

This parameter is used to specify the recording parameters in the audio recording API startAudioRecording.

| EnumType | DESC |
| --- | --- |
| filePath | Field description: The path where the recording file is saved (required).Note: The path must be accurate to the file name and format suffix. The format suffix is used to determine the format of the recording file. Currently supported formats are PCM, WAV, and AAC.For example: If you specify the path as "mypath/record/audio.aac", it means that you want the SDK to generate an audio recording file in AAC format.Please specify a legal path with read and write permissions, otherwise the recording file cannot be generated. |
| maxDurationPerFile | Field description: ` maxDurationPerFile ` is the max duration of each recorded file segments, in milliseconds, with a minimum value of 10000. The default value is 0, indicating no segmentation. |
| recordingContent | Field description: Audio recording content type.Note: Record all local and remote audio by default. |

## TRTCLocalRecordingParams

**TRTCLocalRecordingParams**

#### Local media file recording parameters.

This parameter is used to specify the recording parameters in the local media file recording API [startLocalRecording](https://www.tencentcloud.com/document/product/647/72270#c0358d2dce89b4c19aa824350e2db40d).

The [startLocalRecording](https://www.tencentcloud.com/document/product/647/72270#c0358d2dce89b4c19aa824350e2db40d) API is an enhanced version of the startAudioRecording API. The former can record video files, while the latter can only record audio files.

| EnumType | DESC |
| --- | --- |
| filePath | Field description: address of the recording file, which is required. Please ensure that the path is valid with read/write permissions; otherwise, the recording file cannot be generated.**Note**this path must be accurate to the file name and extension. The extension determines the format of the recording file. Currently, only the MP4 format is supported.For example, if you specify the path as ` mypath/record/test.mp4 `, it means that you want the SDK to generate a local video file in MP4 format.Please specify a valid path with read/write permissions; otherwise, the recording file cannot be generated. |
| interval | Field description: ` interval ` is the update frequency of the recording information in milliseconds. Value range: [1000, 10000]. Default value: -1, indicating not to call back |
| maxDurationPerFile | Field description: ` maxDurationPerFile ` is the max duration of each recorded file segments, in milliseconds, with a minimum value of 10000. The default value is 0, indicating no segmentation. |
| recordType | Field description: media recording type, which is ` TRTCRecordTypeBoth ` by default, indicating to record both audio and video. |

## TRTCSwitchRoomConfig

**TRTCSwitchRoomConfig**

#### Room switch parameter.

This parameter is used for the room switch API [switchRoom](https://www.tencentcloud.com/document/product/647/72270#9f8d51bf4f02a354b060068482db62e8), which can quickly switch a user from one room to another.

| EnumType | DESC |
| --- | --- |
| privateMapKey | Field description: permission credential used for permission control, which is optional. If you want only users with the specified ` userId ` values to enter a room, you need to use ` privateMapKey ` to restrict the permission.Recommended value: we recommend you use this parameter only if you have high security requirements. For more information, please see [Enabling Advanced Permission Control](https://www.tencentcloud.com/document/product/647/35157). |
| roomId | Field description: numeric room ID, which is optional. Users in the same room can see one another and make audio/video calls.Recommended value: value range: 1â4294967294.**Note**either ` roomId ` or ` strRoomId ` must be entered. If both are entered, ` roomId ` will be used. |
| strRoomId | Field description: string-type room ID, which is optional. Users in the same room can see one another and make audio/video calls.**Note**either ` roomId ` or ` strRoomId ` must be entered. If both are entered, ` roomId ` will be used. |
| userSig | Field description: user signature, which is optional. It is the authentication signature corresponding to the current ` userId ` and acts as the login password.If you don't specify the newly calculated ` userSig ` during room switch, the SDK will continue to use the ` userSig ` you specified during room entry (enterRoom).This requires you to ensure that the old ` userSig ` is still within the validity period allowed by the signature at the moment of room switch; otherwise, room switch will fail.Recommended value: for the calculation method, please see [UserSig](https://www.tencentcloud.com/document/product/647/35166). |

## TRTCAudioFrameDelegateFormat

**TRTCAudioFrameDelegateFormat**

#### Format parameter of custom audio callback.

This parameter is used to set the relevant format (including sample rate and number of channels) of the audio data called back by the SDK in the APIs related to custom audio callback.

| EnumType | DESC |
| --- | --- |
| channel | Field description: number of sound channelsRecommended value: default value: 1, which means mono channel. Valid values: 1: mono channel; 2: dual channel. |
| mode | Field description: audio callback data operation modeRecommended value: [TRTCAudioFrameOperationModeReadOnly](https://www.tencentcloud.com/document/product/647/72275#712e9ebdb0469f1ee53dc91617c62d6b), get audio data from callback only. The modes that can be set are [TRTCAudioFrameOperationModeReadOnly](https://www.tencentcloud.com/document/product/647/72275#712e9ebdb0469f1ee53dc91617c62d6b), [TRTCAudioFrameOperationModeReadWrite](https://www.tencentcloud.com/document/product/647/72275#712e9ebdb0469f1ee53dc91617c62d6b). |
| sampleRate | Field description: sample rateRecommended value: default value: 48000 Hz. Valid values: 16000, 32000, 44100, 48000. |
| samplesPerCall | Field description: number of sample pointsRecommended value: the value must be an integer multiple of ` sampleRate/100 `. |

## TRTCImageBuffer

**TRTCImageBuffer**

#### Structure for storing window thumbnails and icons.

| EnumType | DESC |
| --- | --- |
| buffer | image content in BGRA format |
| height | image height |
| length | buffer size |
| width | image width |

## TRTCUser

**TRTCUser**

#### The users whose streams to publish.

You can use this parameter together with the publishing destination parameter [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49) and On-Cloud MixTranscoding parameter [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166) to transcode the streams you specify and publish the mixed stream to the destination you specify.

| EnumType | DESC |
| --- | --- |
| intRoomId | **Description:** Numeric room ID. The room ID must be of the same type as that in [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190).**Value:** Value range: 1-4294967294**Note:** You cannot use both ` intRoomId ` and ` strRoomId `. If you specify ` strRoomId `, you need to set ` intRoomId ` to ` 0 `. If you set both, only ` intRoomId ` will be used. |
| strRoomId | **Description:** String-type room ID. The room ID must be of the same type as that in [TRTCParams](https://www.tencentcloud.com/document/product/647/72275#a1de1e93c6cfc6be81dd4152b9e4c190).**Note:** You cannot use both ` intRoomId ` and ` strRoomId `. If you specify ` roomId `, you need to leave ` strRoomId ` empty. If you set both, only ` intRoomId ` will be used.**Value:** 64 bytes or shorter; supports the following character set (89 characters): Uppercase and lowercase letters (a-z and A-Z) Numbers (0-9) Space, "!", "#", "$", "%", "&", "(", ")", "+", "-", ":", ";", "<", "=", ".", ">", "?", "@", "[", "]", "^", "_", "{", "}", "\|", "~", "," |
| userId | /**Description**: UTF-8-encoded user ID (required)**Value:** For example, if the ID of a user in your account system is "mike", set it to ` mike `. |

## TRTCPublishCdnUrl

**TRTCPublishCdnUrl**

#### The destination URL when you publish to Tencent Cloud or a third-party CDN.

This enum type is used by the publishing destination parameter [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49) of the publishing API [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

| EnumType | DESC |
| --- | --- |
| isInternalLine | **Description:** Whether to publish to Tencent Cloud**Value:** The default value is ` true `.**Note:** If the destination URL you set is provided by Tencent Cloud, set this parameter to ` true `, and you will not be charged relaying fees. |
| rtmpUrl | **Description:** The destination URL (RTMP) when you publish to Tencent Cloud or a third-party CDN.**Value:** The URLs of different CDN providers may vary greatly in format. Please enter a valid URL as required by your service provider. TRTC's backend server will push audio/video streams in the standard format to the URL you provide.**Note:** The URL must be in RTMP format. It must also meet the requirements of your service provider, or your service provider may reject push requests from the TRTC backend. |

## TRTCPublishTarget

**TRTCPublishTarget**

#### The publishing destination.

This enum type is used by the publishing API [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

| EnumType | DESC |
| --- | --- |
| cdnUrlList | ` Description: ` The destination URLs (RTMP) when you publish to Tencent Cloud or third-party CDNs.` Note: ` You donât need to set this parameter if you set the publishing mode to [TRTCPublishMixStreamToRoom](https://www.tencentcloud.com/document/product/647/72275#064db271e894d12e1e3ad63bbb1677fb). |
| cdnUrlListSize | ` Description: ` The length of the ` cdnUrlList ` array.` Note: ` You donât need to set this parameter if you set the publishing mode to [TRTCPublishMixStreamToRoom](https://www.tencentcloud.com/document/product/647/72275#064db271e894d12e1e3ad63bbb1677fb). |
| mixStreamIdentity | ` Description: ` The information of the robot that publishes the transcoded stream to a TRTC room.` Note: ` You need to set this parameter only if you set the publishing mode to [TRTCPublishMixStreamToRoom](https://www.tencentcloud.com/document/product/647/72275#064db271e894d12e1e3ad63bbb1677fb)`.` Note: ` After you set this parameter, the stream will be pushed to the room you specify. We recommend you set it to a special user ID to distinguish the robot from the anchor who enters the room via the TRTC SDK.` Note: ` Users whose streams are transcoded cannot subscribe to the transcoded stream.` Note: ` If you set the subscription mode ([setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/72270#f796890d9df3075ba7ce0cfa3b8a77a3)) to manual before room entry, you need to manage the streams to receive by yourself (normally, if you receive the transcoded stream, you need to unsubscribe from the streams that are transcoded).` Note: ` If you set the subscription mode ([setDefaultStreamRecvMode](https://www.tencentcloud.com/document/product/647/72270#f796890d9df3075ba7ce0cfa3b8a77a3)) to auto before room entry, users whose streams are not transcoded will receive the transcoded stream automatically and will unsubscribe from the users whose streams are transcoded. You call [muteRemoteVideoStream](https://www.tencentcloud.com/document/product/647/72270#e47216c48085fc929661d33cfece2181) and [muteRemoteAudio](https://www.tencentcloud.com/document/product/647/72270#b9f7792974d2df2e3922f2ed1e06ea39) to unsubscribe from the transcoded stream. |
| mode | ` Description: ` The publishing mode.` Value: ` You can relay streams to a CDN, transcode streams, or publish streams to an RTC room. Select the mode that fits your needs.**Note**If you need to use more than one publishing mode, you can call [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4) multiple times and set ` TRTCPublishTarget ` to a different value each time.You can use one mode each time you call the [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4)) API. To modify the configuration, call updatePublishCDNStream. |

## TRTCVideoLayout

**TRTCVideoLayout**

#### The video layout of the transcoded stream.

This enum type is used by the On-Cloud MixTranscoding parameter [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166) of the publishing API [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

You can use this parameter to specify the position, size, layer, and stream type of each video in the transcoded stream.

| EnumType | DESC |
| --- | --- |
| backgroundColor | ` Description: ` The background color of the mixed stream.` Value: ` The value must be a hex number. For example, "0x61B9F1" represents the RGB color value (97,158,241). Default value: 0x000000 (black). |
| fillMode | ` Description: ` The rendering mode.` Value: ` The rendering mode may be fill (the image may be stretched or cropped) or fit (there may be black bars). Default value: [TRTCVideoFillMode_Fill](https://www.tencentcloud.com/document/product/647/72275#b3c03b374c30311eef2887dc4799347f). |
| fixedVideoStreamType | ` Description: ` Whether the video is the primary stream ([TRTCVideoStreamTypeBig](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)) or substream ([TRTCVideoStreamTypeSub](https://www.tencentcloud.com/document/product/647/72275#50d8d09e9837560e2946e7b187296868)). |
| fixedVideoUser | ` Description: ` The users whose streams are transcoded.**Note**If you do not specify [TRTCUser](https://www.tencentcloud.com/document/product/647/72275#45a4828314c413dfe17bb431087723a7) (` userId `, ` intRoomId `, ` strRoomId `), the TRTC backend will automatically mix the streams of anchors who are sending audio/video in the room according to the video layout you specify. |
| placeHolderImage | ` Description: ` The URL of the placeholder image. If a user sends only audio, the image specified by the URL will be mixed during On-Cloud MixTranscoding.` Value: ` This parameter is left empty by default, which means no placeholder image will be used.**Note** You need to specify the ` userId ` parameter in ` fixedVideoUser `. The URL can be 512 bytes long at most, and the image must not exceed 2 MB. The image can be in PNG, JPG, JPEG, or BMP format. We recommend you use a semitransparent image in PNG format. |
| rect | ` Description: ` The coordinates (in pixels) of the video. |
| zOrder | ` Description: ` The layer of the video, which must be unique. Value range: 0-15. |

## TRTCWatermark

**TRTCWatermark**

#### The watermark layout.

This enum type is used by the On-Cloud MixTranscoding parameter [TRTCStreamMixingConfig](https://www.tencentcloud.com/document/product/647/72275#7ddba434412d83f9aa8f34b1bb36b166) of the publishing API [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

| EnumType | DESC |
| --- | --- |
| rect | ` Description: ` The coordinates (in pixels) of the watermark. |
| watermarkUrl | ` Description: ` The URL of the watermark image. The image specified by the URL will be mixed during On-Cloud MixTranscoding.**Note** The URL can be 512 bytes long at most, and the image must not exceed 2 MB. The image can be in PNG, JPG, JPEG, or BMP format. We recommend you use a semitransparent image in PNG format. |
| zOrder | ` Description: ` The layer of the watermark, which must be unique. Value range: 0-15. |

## TRTCStreamEncoderParam

**TRTCStreamEncoderParam**

#### The encoding parameters.

` Description: ` This enum type is used by the publishing API [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

` Note: ` This parameter is required if you set the publishing mode to ` TRTCPublish_MixStream_ToCdn ` or ` TRTCPublish_MixStream_ToRoom ` in [TRTCPublishTarget](https://www.tencentcloud.com/document/product/647/72275#e106259cbc7f1cff297f52931b7e7c49).

` Note: ` If you use the relay to CDN feature (the publishing mode set to ` RTCPublish_BigStream_ToCdn ` or ` TRTCPublish_SubStream_ToCdn `), to improve the relaying stability and playback compatibility, we also recommend you set this parameter.

| EnumType | DESC |
| --- | --- |
| audioEncodedChannelNum | ` Description: ` The sound channels of the stream to publish.` Value: ` Valid values: 1 (mono channel); 2 (dual-channel). Default: 1. |
| audioEncodedCodecType | ` Description: ` The audio codec of the stream to publish.` Value: ` Valid values: 0 (LC-AAC); 1 (HE-AAC); 2 (HE-AACv2). Default: 0.**Note** The audio sample rates supported by HE-AAC and HE-AACv2 are 48000, 44100, 32000, 24000, and 16000. When HE-AACv2 is used, the output stream can only be dual-channel. |
| audioEncodedKbps | ` Description: ` The audio bitrate (Kbps) of the stream to publish.` Value: ` Value range: [32,192]. Default: 50. |
| audioEncodedSampleRate | ` Description: ` The audio sample rate of the stream to publish.` Value: ` Valid values: [48000, 44100, 32000, 24000, 16000, 8000]. Default: 48000 (Hz). |
| videoEncodedCodecType | ` Description: ` The video codec of the stream to publish.` Value: ` Valid values: 0 (H264); 1 (H265). Default: 0. |
| videoEncodedFps | ` Description: ` The frame rate (fps) of the stream to publish.` Value: ` Value range: (0,30]. Default: 20. |
| videoEncodedGop | ` Description: ` The keyframe interval (GOP) of the stream to publish.` Value: ` Value range: [1,5]. Default: 3 (seconds). |
| videoEncodedHeight | ` Description: ` The resolution (height) of the stream to publish.` Value: ` Recommended value: 640. If you mix only audio streams, to avoid displaying a black video in the transcoded stream, set both ` width ` and ` height ` to ` 0 `. |
| videoEncodedKbps | ` Description: ` The video bitrate (Kbps) of the stream to publish.` Value: ` If you set this parameter to ` 0 `, TRTC will work out a bitrate based on ` videoWidth ` and ` videoHeight `. For details, refer to the recommended bitrates for the constants of the resolution enum type (see comment). |
| videoEncodedWidth | ` Description: ` The resolution (width) of the stream to publish.` Value: ` Recommended value: 368. If you mix only audio streams, to avoid displaying a black video in the transcoded stream, set both ` width ` and ` height ` to ` 0 `. |
| videoSeiParams | ` Description: ` SEI parameters. Default: null` Note: ` the parameter is passed in the form of a JSON string. Here is an example to use it:{  "payLoadContent":"xxx",  "payloadType":5,  "payloadUuid":"1234567890abcdef1234567890abcdef",  "interval":1000,  "followIdr":false}The currently supported fields and their meanings are as follows: payloadContent: Required. The payload content of the passthrough SEI, which cannot be empty. payloadType: Required. The type of the SEI message, with a value range of 5 or an integer within the range of [100, 254] (excluding 244, which is an internally defined timestamp SEI). payloadUuid: Required when payloadType is 5, and ignored in other cases. The value must be a 32-digit hexadecimal number. interval: Optional, default is 1000. The sending interval of the SEI, in milliseconds. followIdr: Optional, default is false. When this value is true, the SEI will be ensured to be carried when sending a key frame, otherwise it is not guaranteed. |

## TRTCStreamMixingConfig

**TRTCStreamMixingConfig**

#### The transcoding parameters.

This enum type is used by the publishing API [startPublishMediaStream](https://www.tencentcloud.com/document/product/647/72270#1a29a736a9eba0c853f1962fb8d682a4).

You can use this parameter to specify the video layout and input audio information for On-Cloud MixTranscoding.

| EnumType | DESC |
| --- | --- |
| audioMixUserList | ` Description: ` The information of each audio stream to mix.` Value: ` This parameter is an array. Each ` TRTCUser ` element in the array indicates the information of an audio stream.**Note**If you do not specify this array, the TRTC backend will automatically mix all streams of the anchors who are sending audio in the room according to the audio encode param [TRTCStreamEncoderParam](https://www.tencentcloud.com/document/product/647/72275#22718fe81d94d21ec895cbc11820c726) you specify (currently only supports up to 16 audio and video inputs). |
| audioMixUserListSize | **Description:** The length of the ` audioMixUserList ` array. |
| backgroundColor | ` Description: ` The background color of the mixed stream.` Value: ` The value must be a hex number. For example, "0x61B9F1" represents the RGB color value (97,158,241). Default value: 0x000000 (black). |
| backgroundImage | ` Description: ` The URL of the background image of the mixed stream. The image specified by the URL will be mixed during On-Cloud MixTranscoding.` Value: ` This parameter is left empty by default, which means no background image will be used.**Note** The URL can be 512 bytes long at most, and the image must not exceed 2 MB. The image can be in PNG, JPG, JPEG, or BMP format. We recommend you use a semitransparent image in PNG format. |
| videoLayoutList | ` Description: ` The position, size, layer, and stream type of each video in On-Cloud MixTranscoding.` Value: ` This parameter is an array. Each ` TRTCVideoLayout ` element in the array indicates the information of a video in On-Cloud MixTranscoding. |
| videoLayoutListSize | **Description:** The length of the ` videoLayoutList ` array. |
| watermarkList | ` Description: ` The position, size, and layer of each watermark image in On-Cloud MixTranscoding.` Value: ` This parameter is an array. Each ` TRTCWatermark ` element in the array indicates the information of a watermark. |
| watermarkListSize | ` Description: ` The length of the ` watermarkList ` array. |

## TRTCAudioVolumeEvaluateParams

**TRTCAudioVolumeEvaluateParams**

#### Volume evaluation and other related parameter settings.

This setting is used to enable vocal detection and sound spectrum calculation.

| EnumType | DESC |
| --- | --- |
| enablePitchCalculation | ` Description: ` Whether to enable local vocal frequency calculation. |
| enableSpectrumCalculation | ` Description: ` Whether to enable sound spectrum calculation. |
| enableVadDetection | ` Description: ` Whether to enable local voice detection.**Note**Call before startLocalAudio. |
| interval | ` Description: ` Set the trigger interval of the [onUserVoiceVolume](https://www.tencentcloud.com/document/product/647/72271#12c009f500ddcfac4dc9bbf142bf68cb) callback, the unit is milliseconds, the minimum interval is 100ms, if it is less than or equal to 0, the callback will be closed.` Value: ` Recommended value: 300, in milliseconds.**Note**When the interval is greater than 0, the volume prompt will be enabled by default, no additional setting is required. |


---
*Source: [https://trtc.io/document/72275](https://trtc.io/document/72275)*
