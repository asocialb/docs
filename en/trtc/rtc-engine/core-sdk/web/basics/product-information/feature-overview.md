# Feature Overview

## Basic Features

| Feature | Description | Use Cases | Billing |
| --- | --- | --- | --- |
| Video call | 720p/1080p one-to-one or group video callsEach room allows up to 300 concurrent users, and up to 50 of them can turn their cameras on at the same time. | One-to-one video calls, video conferences with up to 300 participants, online medical consultation, video chat, video customer service, video interviews, dual-channel recording, online insurance claim settlement, and video-based party games | [Billing of TRTC Basic Services](https://www.tencentcloud.com/document/product/647/42734#) |
| Audio call | One-to-one or group audio calls, which support 48 kHz sampling and dual channelsEach room allows up to 300 concurrent users, and up to 50 of them can keep their mics on at the same time. | One-to-one or group audio calls, voice chat, audio conferences, audio customer service, and audio-based party games |  |
| Interactive video streaming | Video communication between anchors and audience membersCross-room anchor communicationSmooth mic on/off without waiting; anchor latency less than 300 msNo upper limit on the cumulative number of co-anchoring users in a room; up to 50 users can keep their mics on at the same time.Streaming to up to 100,000 concurrent users and a playback latency as low as 1,000 ms in the low-latency live streaming modeNo upper limit on audience size in the CDN live streaming mode | Low-latency live video streaming, interactive classrooms with up to 100,000 participants, live video competitions, video dating, remote training, large-scale conferences |  |
| Interactive audio streaming | Audio communication between anchors and audience membersCross-room anchor communicationSmooth mic on/off without waiting; anchor latency less than 300 msNo upper limit on the cumulative number of co-anchoring users in a room; up to 50 users can keep their mics on at the same time.Streaming to up to 100,000 concurrent users and a playback latency as low as 1,000 ms in the low-latency live streaming modeNo upper limit on audience size in the CDN live streaming mode | Low-latency live audio streaming, live audio co-anchoring, live audio competitions, audio chat rooms, audio dating, karaoke rooms, FM radio |  |
| [On-Cloud Recording](https://www.tencentcloud.com/document/product/647/45169) | Uses a recording MCU cluster to record the upstream audio and video streams in a room either separately or after mixing. Recording files are saved securely and in real time to [VOD](https://www.tencentcloud.com/document/product/266). | Dual-channel recording, archiving, compliance | On-cloud recording is a value-added service and incurs [additional fees](https://www.tencentcloud.com/zh/document/product/647/45176). |
| [On-Cloud MixTranscoding](https://www.tencentcloud.com/document/product/647/47858#) | Uses an MCU cluster to mix and transcode the audio and video streams in a room and publishes the mixed stream to CSS for on-cloud recording or CDN playback. | Stream mixing, recording format conversion | On-Cloud MixTranscoding is a value-added service and incurs [additional fees](https://www.tencentcloud.com/document/product/647/47631). |
| [Publishing to CSS CDN](https://www.tencentcloud.com/document/product/647/47858#) | Uses a relay and transcoding cluster to convert UDP streams into RTMP streams in the cloud, pushes the streams to CSS, and distributes them via CDNs. | Interactive live streaming, live sharing, large-scale conferencing, live stream viewing by remote users | Relay to CDN is a value-added service and is charged by [CSS](https://www.tencentcloud.com/document/product/267/2819). For details, see [Relay to CDN > Billing](https://www.tencentcloud.com/document/product/267/41059). |

## Advanced Features (Paid)

| Feature | Description | Use Cases | Billing |
| --- | --- | --- | --- |
| AI noise suppression | AI noise suppression can eliminate sounds that traditional noise reduction cannot, such as coughing, sneezing, car honking, and other non-stationary noises. To initiate, select TRTCAudioQualitySpeech for sound quality in [startLocalAudio](https://www.tencentcloud.com/document/product/647/50754#df3c633d8a6277d5271813f9fac58cb9) (using iOS as an example). | Audio call, video call, interactive live streaming, audio chat room, online class | Buy a [TRTC monthly package](https://www.tencentcloud.com/document/product/647/56025#) to unlock these features. |
| Less stutter under poor network conditions | Reduces stutter rate and loading time under poor network conditions. | Audio call, video call, interactive live streaming, audio chat room, online class |  |
|  |  |  |  |
| [RTMP Streaming with TRTC](https://www.tencentcloud.com/document/product/647/63457) | Publishes and plays streams using RTMP. | Online class, sports event streaming |  |
| 3D spatial audio | Delivers different audio effects according to the face orientation of a virtual anchor and the orientation and location of audio sources to enable a spatial and life-like sound experience. | Audio chat room, karaoke room, FM radio, virtual concert, online gaming |  |
| Scaled video coding | Leverages the O264RT coding technology of Tencent Media Lab to reduce loading time, notably cut bandwidth consumption, and improve compatibility with devices. | Video call, online class, interactive live streaming |  |
| Region of interest coding | Reduces CPU usage and delivers a video experience with the lowest possible latency and highest possible quality in most scenarios. | Video call, online class, interactive live streaming |  |
| [High video resolution](https://www.tencentcloud.com/document/product/647/35153) | The anchor can publish videos and share the screen at a resolution of 2K/4K (only 2K+ is supported on PC and web currently). | Video call, online class, interactive live streaming |  |
| Voice changing effects | Uses acoustic algorithms to change the sound of a speaker's voice. | Audio chat room, karaoke room, FM radio, virtual concert, online games, etc. |  |

## Other Advanced Features

| Feature | Description | Use Cases | Billing |
| --- | --- | --- | --- |
| Anchor-audience communication | Audience members can turn their mics to communicate with the anchor. The mic-on/off process is smooth and requires no waiting. | Interactive live streaming, online class, chat room | The feature itself is free, but audio/video call or live streaming durations will be generated when you use this feature, so [TRTC basic service fees](https://intl.cloud.tencent.com/document/product/647/34610) will be incurred. |
| Cross-room communication | Anchors from different rooms can communicate with each other while audience members watch. | Showroom streaming, cross-room match, cross-room class | The feature itself is free, but audio/video call or live streaming durations will be generated when you use this feature, so [TRTC basic service fees](https://intl.cloud.tencent.com/document/product/647/34610) will be incurred. |
| Screen sharing | The anchor can share the desktop, a window (for example, a Microsoft PowerPoint window), or a portion of the desktop to others. | Online class, slide sharing, remote assistance | The feature itself is free, but audio/video call or live streaming durations will be generated when you use this feature, so [TRTC basic service fees](https://intl.cloud.tencent.com/document/product/647/34610) will be incurred. |
| Local server recording | Server-side recording relies on the Linux SDK, which is not commercially available yet. If you have questions about the SDK or want to use it, please contact us at info_rtc@tencent.com. | Dual-channel recording, archiving, compliance | The feature itself is free, but audio/video call or live streaming durations will be generated when you use this feature, so [TRTC basic service fees](https://intl.cloud.tencent.com/document/product/647/34610) will be incurred. |
| High sound quality | 48 kHz sample rate, end-to-end 192 Kbps bitrate, and dual channels for a clear and immersive audio interaction experience | Audio call, video call, interactive live streaming, audio chat room, high-audio-quality FM radio, music class, karaoke, online class | Free |
| High video quality | 720/1080p video quality | Video call, interactive live streaming, online class | Free |
| 3A processing | Leverages the industry-leading 3A (acoustic echo cancellation, active noise suppression, automatic gain control) technologies of Tencent Ethereal Audio Lab to deliver high audio quality even when multiple people speak at the same time or in the presence of background noises. | All audio scenarios | Free |
| Basic beauty filters | Basic beautification effects, including skin brightening, skin smoothing, rosy skin, and basic filters | Video call, interactive live streaming, online class | Free |
| BGM | The anchor can play an audio file in MP3, AAC, or WAV format as background music during a call or live stream. | Audio call, video call, interactive live streaming, online class, audio chat room, karaoke room, FM radio | Free |
| Audio effects | Audio effects such as applauding, cheering, whistling, and booing | Audio call, video call, interactive live streaming, audio chat room, karaoke, FM radio | Free |
| Publishing computer audio | The anchor can publish the audio they play locally, for example, the music played by QQ Music on their computer, to remote users. | Interactive live streaming, online class, audio chat room, FM radio | Free |
| Voice changing | Voice changing effects such as little girl, middle-aged man, and metal | Audio call, video call, interactive live streaming, audio chat room, karaoke, FM radio | Free |
| Reverb | Reverb effects such as karaoke, small room, hall, and shower room | Audio call, video call, interactive live streaming, audio chat room, karaoke, FM radio | Free |
| Audio volume callback | Callback of audio volumes, which you can use to display audio waveforms or show volume reminders | Audio call, video call, audio chat room, FM radio, karaoke, and speech detection | Free |
| In-ear monitoring | Records local audio and plays it back in the local userâs earphones, usually for detection of speech errors or pitch control during singing | Interactive live streaming, showroom streaming, karaoke | Free |
| Custom audio data | Callback of raw audio captured from a non-standard external device or a local audio file for custom processing. | Non-standard device connection, custom audio effect, speech processing, speech recognition | Free |
| Custom video data | Custom video sources (such as video files, external devices, and third-party data sources) and renderers | Custom beauty filters, custom data sources, multi-device management, video recognition, image processing | Free |
| SEI message | Embeds custom information such as lyrics and questions as SEI frames into published video streams. | Karaoke, live quiz, interactive live streaming | Free |

## Extended Features

> **Note**Extended features are provided by other Tencent Cloud products and are charged according to the billing standards of the corresponding products.

| Feature | Description | Use Cases | Billing |
| --- | --- | --- | --- |
| Chat | You can use the capabilities of Tencent Cloud Chat, including one-to-one chat, group chat, and chat rooms with no upper limit on the number of users, to implement features such as chat, comments, on-screen comments, gift sending, and liking.You can also use Chat to implement signaling-based interaction, call invitations, and user counting. | Online customer service, interactive live streaming, interactive classroom, remote training | These features incur [Chat](https://intl.cloud.tencent.com/document/product/1047) fees. For details, see [Pricing](https://intl.cloud.tencent.com/document/product/1047/34350). |
| AI beauty filters | Diverse effects enabled by face recognition technologies, such as AI-based beautification, makeup effects, facial feature adjustment, and green screen keying | Video call, interactive live streaming, showroom streaming | This feature incurs Tencent Effect SDK fees. |


---
*Source: [https://trtc.io/document/35428](https://trtc.io/document/35428)*
