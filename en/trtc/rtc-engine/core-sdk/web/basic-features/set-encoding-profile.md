# Set Encoding Profile

This tutorial mainly introduces how to

1. Set video encoding profile.
2. Set audio encoding profile.
3. Set screen sharing encoding profile.

## Demo

## Set Video Encoding Profile

You can set the video encoding profile through the parameter **profile**in [trtc.startLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) and [trtc.updateLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalVideo).

Specify a predefined profile, and each profile corresponds to a set of recommended resolution, frame rate, and bit rate.

```
// Specify video profile when startingawait trtc.startLocalVideo({  option: { profile: '480p' }});// Dynamically adjust video profile during the callawait trtc.updateLocalVideo({  option: { profile: '360p' }});
```

| Video Profile | Resolution (width x height) | Frame Rate (fps) | Bit Rate (kbps) | Note |
| --- | --- | --- | --- | --- |
| 120p | 160 x 120 | 15 | 200 |  |
| 120p_2 | 160 x 120 | 15 | 100 | Only supported in v5.1.1+ |
| 180p | 320 x 180 | 15 | 350 |  |
| 180p_2 | 320 x 180 | 15 | 150 | Only supported in v5.1.1+ |
| 240p | 320 x 240 | 15 | 400 |  |
| 240p_2 | 320 x 240 | 15 | 200 | Only supported in v5.1.1+ |
| 360p | 640 x 360 | 15 | 800 |  |
| 360p_2 | 640 x 360 | 15 | 400 | Only supported in v5.1.1+ |
| 480p | 640 x 480 | 15 | 900 |  |
| 480p_2 **(Default)** | 640 x 480 | 15 | 500 | Only supported in v5.1.1+ |
| 720p | 1280 x 720 | 15 | 1500 |  |
| 1080p | 1920 x 1080 | 15 | 2000 |  |
| 1440p | 2560 x 1440 | 30 | 4860 |  |
| 4K | 3840 x 2160 | 30 | 9000 |  |

Specify custom resolution, frame rate, and bit rate:

```
// Specify video profile when startingawait trtc.startLocalVideo({  option: { profile: { width: 640, height: 480, frameRate: 15, bitrate: 900 /* kpbs */} }});// Dynamically adjust video profile during the callawait trtc.updateLocalVideo({  option: { profile: { width: 640, height: 360, frameRate: 15, bitrate: 800 /* kpbs */} }});
```

> **Note:**Due to device and browser limitations, the video resolution may not match exactly. In this case, the browser will automatically adjust the resolution to make it closer to the one specified by the profile.Due to the network and cpu performance, the resolution and frame rate of video encoding may be lower than expected. For camera, it's smooth first as default, which reduce the resolution appropriately and give priority to the encoding of frame rate when the performance is insufficient.For screen sharing, it's clear first as default, which reduce the frame rate appropriately and give priority to the encoding of resolution when the performance is insufficient.You can change this priority by the **qosPreference** paramerter in [trtc.startLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalVideo) and [trtc.updateLocalVideo()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#updateLocalVideo). Refer to [QOS_PREFERENCE_SMOOTH](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.QOS_PREFERENCE_SMOOTH) and [QOS_PREFERENCE_CLEAR](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/module-TYPE.html#.QOS_PREFERENCE_CLEAR).

## Set Audio Encoding Profile

You can set the audio encoding profile through the parameter **profile**in [trtc.startLocalAudio()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startLocalAudio).

```
// Default profileawait trtc.startLocalAudio({ option: { profile: TRTC.TYPE.AUDIO_PROFILE_STANDARD }});// Note: SDK does not support dynamic adjustment of audio profile during the call.// You have to set audio profile in trtc.startLocalAudioawait trtc.updateLocalAudio({ option: { profile: TRTC.TYPE.AUDIO_PROFILE_HIGH }}); // Does not work.
```

| Audio Profile | Sampling Rate | Channel | Bitrate (kbps) |
| --- | --- | --- | --- |
| TRTC.TYPE.AUDIO_PROFILE_STANDARD **(Default)** | 48000 | Mono | 40 |
| TRTC.TYPE.AUDIO_PROFILE_HIGH | 48000 | Mono | 128 |
| TRTC.TYPE.AUDIO_PROFILE_STANDARD_STEREO | 48000 | Stereo | 64 |
| TRTC.TYPE.AUDIO_PROFILE_HIGH_STEREO | 48000 | Stereo | 192 |

## Set Screen Sharing Encoding Profile

You can set the screen sharing encoding profile through the parameter **profile**in [trtc.startScreenShare()](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/TRTC.html#startScreenShare).

```
// The default profile is '1080p'await trtc.startScreenShare({ option: { profile: '1080p_2' }});// Note: SDK does not support dynamic adjustment of screen sharing profile during the call.// Specify custom profile when startingawait trtc.startLocalVideo({  option: { profile: { width: 1280, height: 720, frameRate: 15, bitrate: 1500 /* kpbs */} }});
```

| Screen Profile | Resolution (width x height) | Frame Rate (fps) | Bitrate (kbps) |
| --- | --- | --- | --- |
| 480p | 640 x 480 | 5 | 900 |
| 480p_2 | 640 x 480 | 30 | 1000 |
| 720p | 1280 x 720 | 5 | 1200 |
| 720p_2 | 1280 x 720 | 30 | 3000 |
| 1080p | 1920 x 1080 | 5 | 1600 |
| 1080p_2 | 1920 x 1080 | 30 | 4000 |


---
*Source: [https://trtc.io/document/59654](https://trtc.io/document/59654)*
