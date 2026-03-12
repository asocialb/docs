# Live Stream List

## Feature Preview

This document provides a detailed introduction to the **Live Stream List Page** feature within **TUILiveKit**. You can directly integrate our pre-built live stream list page into your existing project by referring to this guide. This page supports features such as pull-to-refresh, load-more on scroll, and clicking to join a live room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87cd0eb798f911f0b7a5525400454e06.png)

## Quick Start

### Step 1. Activate the Service

Refer to the [Activate Service](https://www.tencentcloud.com/document/product/647/60033) document to enable the Free trial or official package.

### Step 2. Code Integration

Refer to  [Preparations](https://www.tencentcloud.com/document/product/647/63255) guide to integrate the TUILiveKit SDK.

### Step 3: Add the Live Stream List Page

At the entry point where you need to access the live stream list page (determined by your business logic), perform the following operation to either navigate to the live list page or integrate it into your existing **Widget** tree:

Direct Navigation

Integrate Into Widget Tree

```
// navigate to live list pageNavigator.push(context, MaterialPageRoute(  builder: (context) {     return LiveListWidget();}));
```

```
// --- Select one integration method based on your Widget tree structure ---// [option one] as the only child Widget (single subtree)// Suitable for containers such as Container, Padding that usually only contain one child WidgetContainer(       child: LiveListWidget() // Integrate the live stream list here)// [option two] as one of multiple child Widgets (multi-subtree)// Suitable for layouts such as Column, Row, Stack that can contain multiple child WidgetsStack(       children: [           YourOtherWidget(), // Your other child Widget           LiveListWidget(), // Integrate the live stream list here       YourOtherWidget(), // Your other child Widget   ])
```

## Next Steps

Congratulations! You have successfully integrated the **Live Stream List** feature. Next, you can implement features such as **Host Live Streaming** and **Audience Viewing**. Please refer to the table below:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Streaming** | The complete workflow for a host to start a stream, including pre-stream setup and various in-stream interactions. | [Host Streaming](https://www.tencentcloud.com/document/product/647/73742) |
| **Audience Viewing** | Audience can watch live streaming after entering the anchor's live streaming room, with features like audience mic connection, live room information, online audience, and bullet screen display. | [Audience Viewing](https://www.tencentcloud.com/document/product/647/73749) |

## FAQs

### What should I do if the page shows no live streams after integrating the live list feature?

If you see a blank page, you need to check whether you have completed the [Complete Login](https://www.tencentcloud.com/document/product/647/63255#6b283542-df2f-4f16-b3b4-1fb0065d497a). To test the feature, you can use two devices: one device for starting live streaming, and the other device on the list page to pull the live streaming room that has gone live.


---
*Source: [https://trtc.io/document/73761](https://trtc.io/document/73761)*
