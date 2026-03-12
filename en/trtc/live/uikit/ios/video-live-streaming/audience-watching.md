# Audience Watching

**TUILiveKit**'s audience viewing page provides users with various and convenient live streaming and interaction features, enabling quick integration into your application to meet diverse audience needs.

## Feature Overview

- **Live streaming:** Clear and smooth viewing of the host's real-time live stream.
- **Interactive co-guest:** Apply for mic connection to interact with the host via audio and video.
- **Live information:** View the live streaming room title, description, and audience list, etc.
- **Live interactive:** Send a gift (with animation effects and host notification), like (with animation and real-time statistics), and interact via bullet screen.

| **Live Streaming** | **Interactive co-guest** | **Live Information** | **Live Interactive** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a70a68339a0211f0930a5254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a71c93259a0211f0bf2352540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a706209a9a0211f091df5254005ef0f7.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a71baf679a0211f0a90152540099c741.png) |

## Quick Start

### Step 1. Activate the Service

Refer to the [Activate Service](https://www.tencentcloud.com/document/product/647/60033) document to enable the Free trial or official package.

### Step 2. Code Integration

Refer to  [Preparations](https://www.tencentcloud.com/document/product/647/72223)  guide to integrate the TUILiveKit SDK.

### Step 3. Add an Audience Viewing view

In your audience view controller `YourAudienceViewController`, initialize and add `AudienceContainerView` for audience streaming:

Swift

```
YourAudienceViewController
```

### Step 4. Navigate to the **Audience Viewing** view

Usually in the [live stream list](https://www.tencentcloud.com/document/product/647/72226), use the following code example when you need to jump to the viewer watching page:

Swift

```
YourAudienceViewController
```

## Customize Your UI Layout

### Customize the `AudienceContainerView` Feature Area

By calling the API of [Step 3](#c9d8cb5f-0da5-496d-b175-0c0d58cdfb02) created `audienceView`, you can customize and disable (hide) the operation area or specific features on the viewer watching page:

Swift

```
YourAudienceViewController
```

| **API** | **Description** |
| --- | --- |
| `disableHeaderLiveData(true)` | Hide Top Operation Section Live Information |
| `disableHeaderFloatWin(true)` | Hide Top Operation Section Floating Window Feature |
| `disableHeaderVisitorCnt(true)` | Hide Top Operation Section Audience List Function |
| `disableFooterCoGuest(true)` | Hide Bottom Operation Section Co-Anchoring Function |
| `disableSliding(true)` | Forbid Swiping to Switch Live Rooms |

### Text Customization (Localization)

TUILiveKit uses the [Apple Strings Catalog](https://developer.apple.com/documentation/xcode/localizing-and-varying-text-with-a-string-catalog)(`.xcstrings`) format, introduced in **Xcode 15**, to manage the text displayed in the UI. You can modify the string resources using Xcode's graphical interface:

> **Note:**[Apple Strings Catalog](https://developer.apple.com/documentation/xcode/localizing-and-varying-text-with-a-string-catalog) (.xcstrings) is a localization format introduced in Xcode 15. It enhances how developers manage localized strings, supporting a structured format to handle plurals, device-specific variants, etc. This format is becoming the recommended way to manage localization for iOS and macOS applications.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7b5906219a0311f09936525400e889b2.png)

### Icon Customization (Image Assets)

TUILiveKit uses `TUILiveKit.xcassets` to manage the image resources for the UI. You can quickly modify the custom icons using Xcode's graphical tools.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7b5ae02d9a0311f09936525400e889b2.png)

## Next Steps

Congratulations! You have successfully integrated **Audience Viewing**. Next, you can implement features such as **host streaming**, **live stream list** and **gift system**. Please refer to the table below:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Streaming** | The complete workflow for a host to start a stream, including pre-stream setup and various in-stream interactions. | [Host Streaming](https://www.tencentcloud.com/document/product/647/72225) |
| **Live Stream List** | Display the live stream list interface and features, including the live stream list and room information display. | [Live Stream List](https://www.tencentcloud.com/document/product/647/72226) |
| **Gift System** | Support custom gift asset configuration, billing system integration, and gift-sending in PK scenarios. | [Gift System](https://www.tencentcloud.com/document/product/647/69849) |

## FAQs

### Why is the video screen black when a viewer selects video co-hosting?

Please go to **Phone Settings** > **App >** **Camera**, check whether camera permission is enabled, refer to the image below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6bcbba71991611f0961e52540099c741.png)

### Why can't other viewers in the live room see the barrage content sent by a viewer?

- **Reason 1**: First check the network connection to ensure the viewer's device network is normal.
- **Reason 2**: The viewer has been **muted (banned)** by the host and cannot send barrage.
- **Reason 3**: The viewer's barrage content involves **keyword blocking**. Please confirm whether the content sent by the viewer complies with the live room rules.


---
*Source: [https://trtc.io/document/72227](https://trtc.io/document/72227)*
