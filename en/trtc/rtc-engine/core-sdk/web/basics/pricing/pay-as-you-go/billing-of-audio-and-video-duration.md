# Billing of Audio and Video Duration

Audio and video duration is a basic billing item of TRTC. The audio and video duration usage generated during your use of RTC Engine, Call, Conference, and Live Audio Room component will be billed according to the charges in this document. Usage generated from Video Live component will be billed according to the [Billing of Video Live component](https://www.tencentcloud.com/document/product/647/66078).

Charges are based on each participant's duration in an audio call, video call, or interactive live streaming room. The price of video duration varies with resolution.

If you have a contract with TRTC, the billing details in the contract will apply.

> **Note:**[Aggregate video resolution](https://www.tencentcloud.com/document/product/647/42734#.E7.AC.AC.E4.B8.80.E6.AD.A5.EF.BC.8C.E8.AE.A1.E7.AE.97.E5.90.84.E7.94.A8.E6.88.B7.E8.AE.A2.E9.98.85.E7.9A.84.E8.A7.86.E9.A2.91.E6.80.BB.E5.88.86.E8.BE.A8.E7.8E.87.EF.BC.8C.E4.BB.A5.E5.8F.8A.E6.97.B6.E9.95.BF.E7.94.A8.E9.87.8F2) applies to accounts whose first TRTC [application](https://www.tencentcloud.com/document/product/647/37714) is created on or after October 27, 2021.Live's voice room component: When you use the Live Voice [Room core control component (SeatGridView)](https://trtc.io/document/60334?product=live) or refer to [RTCRoomEngine API](https://trtc.io/document/61639?product=live) for integration, it is considered as using this component.Live's video live component: When your application is created after December 18, 2024 (SDKAppID) and integrates with Live v2.8.0 or later versions of [the core control for Video Live (LiveStreamCoreView)](https://trtc.io/document/60036?product=live), it is considered as using this component. If the above conditions are not met, it is considered as using the live's voice room component.

## Billing Instructions

- Billing mode: Daily pay-as-you-go.
- Billing cycle: Billing occurs on a daily basis, with audio and video duration fees deducted when the billing statement is generated the following day. For exact billing details and statement generation times, please refer to the actual [Billing Statement](https://console.tencentcloud.com/expense/bill/overview).
- You can buy [pre-paid packages](https://www.tencentcloud.com/document/product/647/56025) to deduct your audio and video duration.Â Pre-paid packages will be used first.Â If you havenât purchased a package or have used up your packages, your audio and video duration will be billed at pay-as-you-go rates.Â The deduction ratios for pre-paid packages are **1:1, 1:4, 1:9, 1:16, and 1:36** for audio, HD, FHD, 2K, and 4K duration respectively. For example, for 1 minute of HD video duration generated, 4 minutes will be deducted from a pre-paid package.
- 10,000 free minutes are also available for audio and video duration usage. For details, refer to [Free Minutes](https://www.tencentcloud.com/document/product/647/42735).
- You can use the [TRTC Price Calculator](https://trtc.io/pricing/calculator) to estimate the audio and video duration usage and fees for your service.
- If the audio/video streams in a TRTC room are relayed to CSS to enable playback via CDN, additional fees will be incurred. For details, refer to [Billing of MixTranscoding and Relay to CDN](https://www.tencentcloud.com/document/product/647/47631).

> **Note:**If an audio/video stream processing task (recording, audit, relay, etc.) is initiated for a room, the system will assign a robot to the room (if multiple tasks are initiated, there will be multiple robots). The robot will enter the room as a user and will subscribe to streams of the room. This will incur audio/video duration fees.For relaying to RTC rooms, because the robot does not subscribe to streams in the room, audio duration fees will be charged according to the robotâs length of stay in the room.In other scenarios (relaying streams in one RTC room to another room or to a third-party platform, etc.), audio/video duration fees will be charged according to the media received by the robot.If you use other TRTC services that are neither audio/video calls nor interactive live streaming, such as [cloud recording](https://www.tencentcloud.com/document/product/647/45176), additional fees will be incurred. For details, see billing instructions for the corresponding TRTC services.If you want your pay-as-you-go usage to be billed monthly, please [contact us](https://console.tencentcloud.com/workorder/category).

## Billing Formula

**Monthly cost** = **Audio duration** x **Unit price of audio duration** + **Video durations of different categories** x **Unit price of the corresponding video category**

## Pricing

| Category | Unit price (USD/1,000 minutes) | Aggregate Video Resolution |
| --- | --- | --- |
| Audio | 0.99 | - |
| HD | 3.99 | Resolution â¤ 921,600 (1280 x 720) |
| FHD | 8.99 | 921,600 (1280 x 720) < Resolution â¤ 2,073,600 (1920 x 1080) |
| 2K | 15.99 | 2,073,600 (1920 x 1080) < Resolution â¤ 3,686,400 (2560 x 1440) |
| 4K | 35.99 | 3,686,400 (2560 x 1440) < Resolution â¤ 8,847,360 (4096 x 2160) |

> **Note:**You can use the TRTC [Price Calculator](https://trtc.io/pricing/calculator) to estimate your costs.TRTC will calculate the total duration generated by your [Tencent RTC account](https://console.trtc.io/statistics) for each category each day.Video durations are classified into four categories based on **aggregate video resolution** and are priced differently. The system will first deduct your usage using [the 10,000 free minutes](https://www.tencentcloud.com/document/product/647/42735) offered by TRTC for each developer account and the minutes of purchased [monthly packages](https://www.tencentcloud.com/document/product/647/56025). The remaining audio and video durations are multiplied by their corresponding unit prices and added up. The sum of these charges constitutes your daily audio/video duration fee.

### Dual-Stream Resolution

In the dual-stream mode, a user's resolution is calculated as follows:

- If the user subscribes to the high-quality stream, the resolution of the high-quality stream as set by the sender will be used for the calculation of the aggregate resolution.
- If the user subscribes to the low-quality stream, the resolution received by the user will be used for the calculation of the aggregate resolution.

### Resolution of Screen Sharing Stream

For screen sharing streams, audio/video duration is charged based on the resolution set in TRTCVideoEncParam. For details on how the resolution is set, see the following documents:

- All Platforms (C++): [startScreenCapture](https://www.tencentcloud.com/document/product/647/50770#94be1579f497befa5e6450725b4f1a5c)
- iOS: [startScreenCaptureInApp](https://liteav.sdk.qcloud.com/doc/api/zh-cn/group__TRTCCloud__ios.html#abf51acf26b2212192f7145468886b791), [startScreenCaptureByReplaykit](https://www.tencentcloud.com/document/product/647/50754#a40e37e782a049150b3314810516bf44)
- macOS: [startScreenCapture](https://www.tencentcloud.com/document/product/647/50754#a5556ab15765655b288ad33f8f49176d)
- Android: [startScreenCapture](https://www.tencentcloud.com/document/product/647/50762#9b55d2e9cd4e32eae74a9eb3555f6c8b)

On the Web, when a target resolution cannot be achieved due to device or browser limitations, the browser will automatically adjust the resolution to the closest possible match to the target. The actual resolution that is ultimately used will be the basis for billing purposes. For more detailed information on this process, refer to  [setScreenProfile](https://web.sdk.qcloud.com/trtc/webrtc/v5/doc/en/global.html#ScreenShareProfile).

## Usage Calculation

### Video Duration

For users who successfully enter a TRTC [room](https://www.tencentcloud.com/document/product/647/37714):

- Video duration is defined as t**he duration of video streams the users subscribe to** (the duration of received video).
- If a user subscribes to both the audio and video streams of another user, only the video duration will be billed.
- Users may enter and exit a room multiple times. TRTC will tally up the durations of multiple video segments in real time.
- If a user subscribes to multiple video streams simultaneously, the resolution of each video stream will be added up. The result is the user's aggregate resolution.
- TRTC will categorize videos based on  **the actual received video resolution**  and then bill the video duration of different categories respectively.

### Audio Duration

For users who successfully enter a TRTC [room](https://www.tencentcloud.com/document/product/647/37714):

- Audio duration is defined as **the duration of a userâs stay in the room when video streams are not received**, including when the user subscribes only to audio streams, when the user doesnât subscribe to any streams at all, and when the user only sends but does not receive audio and video in the room.
- If a user does not subscribe to any video stream in the room, audio duration fees will be charged based on the userâs length of stay in the room.
- Users may enter and exit a room multiple times. TRTC will tally up the durations of multiple audio segments in real time.
- Audio duration fees will be charged based on the length of time a user stays in the room, regardless of whether they are the only user present or if they publish any streams.

> **Note:**Durations for each day are calculated in seconds for each application (SDKAppID) and then converted to minutes (rounded up to the nearest minute) for billing.When there is a screen sharing stream in the room, the shared screen will be seen as published by a virtual anchor, and audio/video duration fees will be charged separately.

## Examples of Billing

### Example 1

Assume that six users entered a room at the same time and communicated over video for 60 minutes.

There were three anchors (A, B, and C) in the room. The video resolution of A was 960 x 720, and that of B and C were both 640 x 480. Two of the audience members subscribed to the video streams of all anchors, while the other subscribed to audio only. Anchor A also shared the screen at a resolution of 1920 x 1080.

#### Step 1: Calculating the Aggregate Video Resolution and Duration of Each User

The table below shows the aggregate resolution of videos received by each user, the categories the resolutions fall in, and their prices.

| User | Streams Received | Video Resolutions | Aggregate Resolution | Category | Duration (minutes) |
| --- | --- | --- | --- | --- | --- |
| A (shared the screen) | B's and C's video streams | 640 x 480 x 2 | 614,400 | HD | 60 |
| B | A's video and screen sharing streams + C's video stream | (960 x 720) + (640 x 480) + (1920 x 1080) | 3,072,000 | 2K | 60 |
| C | A's video and screen sharing streams + B's video stream | (960 x 720) + (640 x 480) + (1920 x 1080) | 3,072,000 | 2K | 60 |
| Audience 1 | A's video and screen sharing streams + B's and C's video streams | (960 x 720) + (640 x 480 x 2) + (1920 x 1080) | 3,379,200 | 2K | 60 |
| Audience 2 | A's video and screen sharing streams + B's and C's video streams | (960 x 720) + (640 x 480 x 2) + (1920 x 1080) | 3,379,200 | 2K | 60 |
| Audience 3 | Audio streams only | - | - | Audio | 60 |

The figure below shows the billing details:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7bd2a8d7511511ee94c3525400d793d0.png)

#### Step 2: Querying the Unit Price of the Corresponding Category, and Calculating the Final Cost according to the Formula

Formula: **Monthly cost** = **Audio duration** x **Unit price of audio duration** + **Video durations of different categories** x **Unit price of the corresponding video category**

| Billable Item | Total duration (minutes) = Sum of each user's duration | Unit price (USD/1,000 minutes) | Cost by Category (USD) | Total cost (USD)(Rounded to two decimal places) |
| --- | --- | --- | --- | --- |
| HD | 60 x 1 = 60 | 3.99 | (60/1000) x 3.99 = 0.2394 | 4.14 |
|  | 2K | 60 x 4 = 240 | 15.99 | (240/1000) x 15.99 = 3.8376 |
|  | Audio | 60 x 1 = 60 | 0.99 | (60/1000) x 0.99 = 0.0594 |

### Example 2

Assume that six users entered a room at the same time and communicated over video for 60 minutes. There were four anchors (A, B, C, and D) in the room. The video resolution of A, B, and C was 480 x 480, while D published only audio. One of the audience members subscribed to the video streams of all anchors, and the other subscribed to audio only.

#### Step 1: Calculating the Aggregate Video Resolution and Duration of Each User

The table below shows the aggregate resolution of videos received by each user, the categories the resolutions fall in, and their prices.

| User | Streams Received | Video Resolutions | Aggregate Resolution | Category | Duration (minutes) |
| --- | --- | --- | --- | --- | --- |
| A | B's and C's video streams + D's audio stream | 480 x 480 x 2 | 460,800 | HD | 60 |
| B | A's and C's video streams + D's audio stream | 480 x 480 x 2 | 460,800 | HD | 60 |
| C | A's and B's video streams + D's audio stream | 480 x 480 x 2 | 460,800 | HD | 60 |
| D | A's, B's, and C's video streams | 480 x 480 x 3 | 691,200 | HD | 60 |
| Audience 1 | A's, B's, and C's video streams + D's audio stream | 480 x 480 x 3 | 691,200 | HD | 60 |
| Audience 2 | Audio streams only | - | - | Audio | 60 |

#### Step 2: Querying the Unit Price of the Corresponding Category, and Calculating the Final Cost according to the Formula

Formula: **Monthly cost** = **Audio duration** x **Unit price of audio duration** + **Video durations of different categories** x **Unit price of the corresponding video category**

| Billable Item | Total duration (minutes) = Sum of each user's duration | Unit price (USD/1,000 minutes) | Cost by Category (USD) | Total cost (USD) (Rounded to two decimal places) |
| --- | --- | --- | --- | --- |
| HD | 60 x 5 = 300 | 3.99 | (300/1000) x 3.99 = 1.197 | 1.26 |
|  | Audio | 60 x 1 = 60 | 0.99 | (60/1000) x 0.99 = 0.0594 |


---
*Source: [https://trtc.io/document/42734](https://trtc.io/document/42734)*
