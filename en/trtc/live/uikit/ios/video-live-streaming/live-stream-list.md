# Live Stream List

## Feature Preview

This document provides a detailed introduction to the **Live Stream List Page** in TUILiveKit. You can directly integrate our pre-built live stream list page into your existing project, or deeply customize the page style, layout, and features according to your specific needs.

- **Double-Column Waterfall Flow**: Default view, simultaneously displaying previews for 2 live rooms.
- **Single-Column Waterfall Flow**: Default view, simultaneously displaying a preview for 1 live room.

| **Double-Column Waterfall Flow** | **Single-Column Waterfall Flow** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6ed6ca4d9a0511f0872c525400bf7822.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6eda33269a0511f0a90152540099c741.png) |

> **Note:**When previewing live room screens, the preview duration is counted into the viewer's audio/video duration. For detailed billing information, please refer to [Pricing](https://www.tencentcloud.com/document/product/647/66078).

## Quick Start

### Step 1. Activate the Service

Refer to the [Activate Service](https://www.tencentcloud.com/document/product/647/60033) document to enable the Free trial or official package.

### Step 2. Code Integration

Refer to  [Preparations](https://www.tencentcloud.com/document/product/647/72223)  guide to integrate the TUILiveKit SDK.

### Step 3. Add the Live Stream List Page

The **LiveListView** component is a dedicated view for displaying the live stream list. It automatically pulls the live room list, supports different display styles (**single-column** and **double-column**).

Swift

```

```

### Step 4. Navigate to the Audience Viewing Page

You can customize the page navigation by setting a click listener. For audience viewing page implementation, see [Audience Viewing](https://www.tencentcloud.com/document/product/647/72227):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b625ee42992311f0961e52540099c741.png)

**Example Code**:

Swift

```
YourAudienceViewController
```

### Step 5. Optimizing Page Transitions for `LiveListView` Interaction

To ensure a more complete and smooth experience during page transitions, the `LiveListView` component, combined with iOS page routing system attributes, provides the `refreshLiveList` and `onRouteToNextPage` methods. With just one line of code, you can optimize live list display and video stream playback. The optimization method is as follows:

Swift

```
// Implement in your live stream list view controller, for example: YourLiveListViewControllerclass YourLiveListViewController: UIViewController {    override func viewDidAppear(_ animated: Bool) {        super.viewDidAppear(animated)        // refreshLiveList: Call this method in viewDidAppear to ensure getting the latest list every time returning to current page        liveListView.refreshLiveList()    }    override func viewWillDisappear(_ animated: Bool) {        super.viewWillDisappear(animated)        // onRouteToNextPage: Call this method in viewWillDisappear to stop the video stream playback on current live list page when entering another page        liveListView.onRouteToNextPage()    }}
```

## Customize Your UI Layout

**TUILiveKit** provides flexible interfaces to customize the live list waterfall component. You can customize the data source and list item styles according to your business needs.

### Customize Data Source

If your backend has a separate live list data, you can customize the data source by implementing the `LiveListDataSource` interface instead of using the component's default list data.

Swift

```

```

### Custom View

The bottom of the waterfall list items displays the video stream or live cover by default. If you need to customize the UI elements at the top of the list items (such as the host's avatar, live title, etc.), you can do so by implementing the `LiveListViewAdapter` interface.

Swift

```
YourL
```

### Custom Transition Animation

**Double-Column Waterfall Flow** and **Single-Column Waterfall Flow** to navigate to the audience viewing page, custom transition animation is often needed for better transition effects. `TUILiveKit` has open-sourced the live stream transition animation [LiveTransitioningDelegate](https://github.com/Tencent-RTC/TUILiveKit/blob/main/iOS/TUILiveKit/Sources/TUILiveListViewController.swift#L193) in the **GitHub** repository. You just need to set `audienceVC.transitioningDelegate` to achieve the same transition animation as TUILiveKit.

Swift

```
YourAudienceViewController
```

| **Double-Column Waterfall Transition Animation** | **Single-Column Waterfall Transition Animation** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0fe06b1798f511f08bb25254005ef0f7.gif) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0fd108f198f511f0a207525400bf7822.gif) |

## Next Steps

Congratulations! You have successfully integrated the **Live Stream List** feature. Next, you can implement features such as **Host Live Streaming** and **Audience Viewing**. Please refer to the table below:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Streaming** | The complete workflow for a host to start a stream, including pre-stream setup and various in-stream interactions. | [Host Streaming](https://www.tencentcloud.com/document/product/647/72225) |
| **Audience Viewing** | Audience can watch live streaming after entering the anchor's live streaming room, with features like audience mic connection, live room information, online audience, and bullet screen display. | [Audience Viewing](https://www.tencentcloud.com/document/product/647/72227) |

## FAQs

### What should I do if the page shows no live streams after integrating the live list feature?

If you see a blank page, you need to check if you have completed the [Complete Login](https://www.tencentcloud.com/document/product/647/72223#6ebcab01-c3d7-4fb4-a933-016cf1cf5193). To test this feature, you can use two devices: one device to start a broadcast, and the other on the live list page to pull the list of ongoing live streams.

### What is the difference between single-column and double-column waterfall flows?

A single-column waterfall flow previews one live room at a time, while a double-column waterfall flow previews two live rooms simultaneously. You can choose the appropriate layout based on your design requirements.

### Is there a charge for previewing live streams?

Yes, the duration of previewing a live room is counted towards the audience's audio/video duration, which is a paid service. For detailed

[Pricing](https://www.tencentcloud.com/document/product/647/66078), you can refer to the relevant content in the documentation.


---
*Source: [https://trtc.io/document/72226](https://trtc.io/document/72226)*
