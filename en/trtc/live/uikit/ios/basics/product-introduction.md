# Product Introduction

## Overview

Live is a real-time interactive live streaming component, encompassing functionalities such as anchor going live, audience viewing, chat and emoji, likes and gift-giving, audience management, and multi-guest management. It is perfectly suited for live streaming scenarios across entertainment, e-commerce, education, and more. By integrating Live, you can swiftly incorporate all the aforementioned live streaming features into your application in just three steps, enabling a rapid deployment of your service. The basic functionalities are illustrated in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c92496f86b8111efb0e2525400a9236a.png)

## Supported Platforms

| **Platform** | **Android** | **iOS** | **Desktop** | **Flutter** | **Web** |
| --- | --- | --- | --- | --- | --- |
| **Supported** |  |  |  |  |  |
| **Supported Languages/Frameworks** | JavaKotlin | SwiftObjective-C | Electron(Only **Windows** currently) | Dart | Vue3 |

## Features

### Basic Features

|  | **Feature Description** |
| --- | --- |
| High-Definition Live Streaming | The host can preview the screen before going live, with the option to start and stop the stream |
| Voice Chat Room | The host can set the background and sound effects before starting the voice chat room, with the option to open and close the chat room |
| Live Streaming Viewing | Supports multiple viewers watching the live stream simultaneously |
| Single-room Multi-Guest | Supports Multi-Guest within a single room |
| Cross-room Multi-Guest/PK | Supports two-person and multi-person cross-room connection/PK |
| Audience List | The audience list component supports displaying the latest 100 viewers entering the live room and the total number of viewers, with simplified and detailed view options |
| Chat and EmojiChat in Live Room | Users can send emoticons and text message barrages, which are displayed in real-time within the live room |
| Likes | Supports a like feature and tracks basic like data |

### Advanced Features

|  | **Feature Description** |
| --- | --- |
| Member Management | Supports the host in blocking and muting viewers. |
| Live Preview | Viewers can preview the live room content without entering it. |
| Live Feed | Viewers can swipe up and down the screen to view different live rooms, supporting both single-column and double-column waterfall UI formats. |
| Gift System | Provide a comprehensive gift solution, including gift material configuration, panel display, special effects playback and data analytics capabilities, to support rapid monetization. |
| Number of Robots | Supports adding live room robots, which can join the room as dummy viewers, interact via multi-guest, and send comments. |
| View Past Messages | Users who join a live room can view messages sent before they entered the room. |
| Follow | Viewers can follow the host and other viewers in the live room. |
| In-Room Search | Supports searching for members within the live room. |
| Ultimate Image Quality | Significantly reduces bitrate while maintaining picture quality, or improves picture quality at the same bitrate, optimizing the viewing experience in bandwidth-limited environments. |
| PC Live Streaming Assistant | Supports multi-camera scene capture and local audio-video mixing, suitable for professional streaming on PC. |
| RTMP Entry/Input Online Media Stream | Pushes local video and audio to the live room via RTMP protocol, supporting scenarios such as host OBS streaming and virtual host live streaming. |
| QUIC Weak Network Optimization | Automatically selects and switches network links or multi-link transmission based on the terminal's network condition, improving transmission speed in weak network environments. |
| Beauty AR | With the default beauty enabled, you can integrate [Beauty AR](https://trtc.io/document/60216) to unlock a wider range of advanced beauty features. |
| Sound Effects | Supports setting volume, voice change, and reverb effects before starting the stream. |

## Use Cases

Live is suitable for all kinds of high-concurrency and large-scale live streaming scenarios such as live show, live shopping, live sports streaming, live product launch, live roadshow, and online auction.

| **Social entertainment** | **Voice Room** |
| --- | --- |
| ![Entertainment](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea9acf726b8011efb0e2525400a9236a.png) | ![Audio Social](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d4f2d1586b8011efa016525400bdab9d.png) |

| **Live shopping** | **Live Education** |
| --- | --- |
| ![Live Shopping](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f29d3bea6b8011ef839b52540055f650.png) | ![Live Education](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/233c9cb86b8111efac6a5254002693fd.png) |

| **Live Gaming** | **Live Fitness** |
| --- | --- |
| ![Gaming](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/34df2d6b6b8111ef80ed52540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0f1686e7fcad11eea33752540095b445.png) |

## Trying It Online

| **Platform** | **Android** | **iOS** | **Desktop** | **Flutter** | **Web** |
| --- | --- | --- | --- | --- | --- |
| **Demo Integration** | [GitHub: Android](https://github.com/tencentyun/TUILiveRoom/tree/main/Android) | [GitHub: iOS](https://github.com/tencentyun/TUILiveRoom/tree/main/iOS) | [GitHub: Electron](https://github.com/Tencent-RTC/ultra-live-electron) | [GitHub: Flutter](https://github.com/Tencent-RTC/TUILiveKit/tree/main/Flutter) | [GitHub: Web](https://github.com/Tencent-RTC/TUILiveKit/tree/main/Web/web-vite-vue3) |

# How to Connect

| **Access method** | **Live Streaming Room Full Feature Integration** | **Voice Chat Room Full Feature Integration** | **Single Feature Integration** | **Room Engine Integration** |
| --- | --- | --- | --- | --- |
| **Method Description** | Seamless integration of all features in the live streaming room will provide you with all functions in the live streaming scenario. | Seamless integration of all features in the voice chat room will provide you with all functions in the voice chat room scenario. | Single-feature integration provides a series of UI components for live streaming and voice chat room scenarios. You can choose the necessary components for integration. | Integrating the room engine will provide you with a range of business APIs for room management, member management, microphone position control, live-connection management, PK, and more. |
| **Applicable Scenarios** | When your UI matches the UI provided in our [Demo](https://www.tencentcloud.com/document/product/647/60454), and you only need to modify image resources and string resources, you can use this method for integration. | When your UI is consistent with the UI provided in our [Demo](https://www.tencentcloud.com/document/product/647/60454), and you only need to modify image resources and string resources, you can use this method for integration. | When your UI partially matches the UI provided in our [Demo](https://www.tencentcloud.com/document/product/647/60454), and you need to block some features and add some of your own business, you can use this method for integration. | When you want to implement your own UI and do not want to use the UI we provide, you can use this method for integration. |
| **Access documentation** | Live Streaming Room Full Feature Integration | [Voice Chat Room Full Feature Integration](https://www.tencentcloud.com/document/product/647/60335) | [Integrate core controls for video live streaming](https://www.tencentcloud.com/document/product/647/69844)[Integrate voice chat room core controls](https://www.tencentcloud.com/document/product/647/69845)[Integrate message sending component](https://www.tencentcloud.com/document/product/647/69848)[Integrate message rendering component](https://www.tencentcloud.com/document/product/647/69847)[Integrate gift panel component](https://www.tencentcloud.com/document/product/647/69850)[Integrate gift player](https://www.tencentcloud.com/document/product/647/69849)[Integrate beauty effect](https://www.tencentcloud.com/document/product/647/69851)[Integrate audience list](https://www.tencentcloud.com/document/product/647/69846) | [RTC RoomEngine](https://www.tencentcloud.com/document/product/647/70008) |
| **Supported Platforms** | Android, iOS, Flutter, Web, Electron | Android, iOS, Flutter | Android, iOS | Android, iOS, Flutter, Web, Electron |

## Suggestions and Feedback

If you have any requirements or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/60034](https://trtc.io/document/60034)*
