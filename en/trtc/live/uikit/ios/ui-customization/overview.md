# Overview

## Integrating a Single Feature Overview

When integrating a single feature, we provide a series of UI components for live-streaming scenarios, including audio and video core components, voice chat core components, live room information components, audience list components, message components, gift components, and more. Based on these UI components, you can quickly build your own live streaming business logic like building blocks.

#### Effect Display

| **Live Streaming Scenarios** | **Voice Chat Scenarios** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/491facf745d011f0aa86525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8204282f45d011f0be2052540099c741.png) |

#### Component Overview

| **Component English Name** | **Component Chinese Name** | **Supported Platforms** | **Function** | **Thumbnail** |
| --- | --- | --- | --- | --- |
| **LiveCoreView** | Live stream core component | Android,iOS,Flutter | The live stream core component provides various APIs such as preview before broadcasting, starting video live streaming, stopping video live streaming, connecting with the audience in the live streaming room, and cross-room connection with other anchors. | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f970bc137a711f0aed2525400e889b2.png) |
| **SeatGridView** | Voice chat core component | Android,iOS,Flutter | The voice chat core component can easily start or stop the voice chat room and efficiently manage microphone seat operations in the live streaming room, including applying for a microphone, inviting to speak, moving seats, and kicking someone off the mic. With SeatGridView, you can quickly integrate the voice chat room module into your application, significantly enhancing user experience while reducing development costs. | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5ff9d5b537a711f0912c52540044a08e.png) |
| **AudienceListView** | audience list component | Android,iOS,Flutter | The audience list component displays the latest 100 newcomers in the live stream and the total number of viewers. You can show a simplified view of the audience list on your live broadcast interface. When the simplified view is clicked, it can pull up the audience list detail view. | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f676dd837a711f0912c52540044a08e.png)  |
| **LiveInfoView** | live streaming room information component | Android,iOS,Flutter | The live streaming room information component displays anchor information and live room information, and supports functions such as following or unfollowing favorite anchors. | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f8507f937a711f0b95f5254005ef0f7.png)![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ade2d99245d011f09bbe525400454e06.png) |
| **BarrageStreamView** | message rendering component | Android,iOS,Flutter | message rendering component displays barrage messages on the screen. | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c6101483660611f0924f5254005ef0f7.png) |
| **BarrageInputView** | message sending component | Android,iOS,Flutter | message sending component allows users to input emojis and text messages in bullet screens and send the messages to the live streaming room. |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c5615e44660611f0bd33525400e889b2.png) |
| **GiftPlayView** | gift player | Android,iOS,Flutter | The gift player mainly provides playback functionality for showing bullet animations, displaying full-screen animations (in svga and mp4 formats), and playing like animations. |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5fa31bf437a711f08806525400bf7822.png) |
| **GiftListPanelView** | gift | Android,iOS,Flutter | The gift panel component displays our default built-in gifts. Clicking these gifts allows you to send them to the live streaming room. | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/999ad18545cb11f0b95f5254005ef0f7.png) |

## Introducing the LiveCoreView Component

LiveCoreView is a basic control we developed for the video live streaming UIKit. This core control provides various APIs, including preview before broadcasting, start video live streaming, stop video live streaming, live streaming room connection with audience, and cross-room connection with other hosts, and so on. You just need to call a few lines of API from the LiveCoreView component to achieve the following live streaming.

For specific integration of the LiveCoreView component, see [LiveCoreView](https://www.tencentcloud.com/document/product/647/69844) integration documentation.

| Anchor is live streaming | Anchor is connecting - Nine-grid layout | Anchor is connecting - Floating window layout |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/60047f3337a711f0b0ce5254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/60285be137a711f0b0ce5254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6039c7c137a711f0be2052540099c741.png) |

## Introducing the SeatGridView Component

**Core control components of the voice chat room** (**SeatGridView**) can easily enable or disable the voice chat room and efficiently manage seat operations in the live streaming room, including requesting to speak, inviting to speak, moving seats, and removing speakers. With the aid of **SeatGridView**, you can quickly integrate the voice chat room module into your application, significantly enhance user experience, and simultaneously reduce development costs.

For specific integration of the SeatGridView component, see [SeatGridView](https://www.tencentcloud.com/document/product/647/69845) integration documentation.

| Broadcaster creates a room and takes the mic. | Broadcaster chats with the audience on mic. |
| --- | --- |
|  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/61b4238437a711f0912c52540044a08e.png) |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/608e4cec37a711f0b0ce5254007c27c5.png) |

## Key Component Introduction

### Live Streaming Room Information Component

LiveInfoView displays the broadcaster and live streaming room information. By default, it shows the broadcaster information view. When you click the broadcaster information view, it will display the detailed view of the live streaming room information.

- Broadcaster information view

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f9cbaf237a711f0aed2525400e889b2.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c52b40fb45d011f0912c52540044a08e.png)

- Live Room Information View
- Specific access method. For details, see [Live Room Information](https://www.tencentcloud.com/document/product/647/70407).

### Audience List Component

The AudienceListView displays the latest 100 viewers who entered the live streaming room and the total number of spectators. By default, it shows the list view. After clicking, it will expand to display the detailed view of the audience list.

- Audience list view

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/60038f4137a711f09bbe525400454e06.png)

- List details of the audience

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dcda64aa45d011f0aa86525400e889b2.png)

- Specific access method. For details, see [Audience List](https://www.tencentcloud.com/document/product/647/69846).

### Message Rendering Component

BarrageStreamView (message rendering component) displays barrage messages on the screen.

- message rendering component

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5fba4a0b37a711f08806525400bf7822.png)

- specific access method. For details, see: [message rendering component](https://www.tencentcloud.com/document/product/647/69847).

### Message Sending Component

BarrageInputView (message sending component) allows users to input emojis and text messages in bullet screens and send the messages to the live streaming room.

- message sending component

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f9bc62f37a711f09bbe525400454e06.png)

- specific access method. For details, see: [message sending component](https://www.tencentcloud.com/document/product/647/69848).

### Gift Player

GiftPlayView (gift player) The gift player mainly provides playback functionality for showing bullet animations, displaying full-screen animations (in svga and mp4 formats), and playing like animations.

- gift player

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/608d4f2e37a711f09bbe525400454e06.png)

- specific access method. For details, see: [gift player](https://www.tencentcloud.com/document/product/647/69849).

### Gift Panel Component

The GiftListPanelView displays our default built-in gifts. Clicking these gifts allows you to send them to the live streaming room.

- Gift Panel Component

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3e07c31c45cd11f08806525400bf7822.png)

- specific access method. For details, see: [Gift Panel Component](https://www.tencentcloud.com/document/product/647/69850).


---
*Source: [https://trtc.io/document/70007](https://trtc.io/document/70007)*
