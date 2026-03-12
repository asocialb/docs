# Live Gift Component

This guide introduces how to quickly integrate the TUILiveKit live gifting component into your project.

## Component Overview

The gifting feature in TUILiveKit consists of two main UI components:

| **Component Name** | **Class Name** | **Description** |
| --- | --- | --- |
| Gift Selection Panel | `GiftListView` | Shows the available gifts and handles user selection and sending actions. |
| Gift Animation Display | `GiftPlayView` | Receives gift messages and renders animations (e.g., SVGA) on screen. |

### Demo Effects

| **Gift Panel** | **Live Comment Gifts** | **Full-Screen Gifts** |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/541288dfdb2411f0bf585254005ef0f7.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/546c5700db2411f0b31e5254007c27c5.gif) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6fb56fb4db2411f0b45152540099c741.gif) |

## Quick Start

### Step 1. Activate the Service

Follow the [Activate the Service](https://www.tencentcloud.com/document/product/647/60033) guide to enable TUILiveKit.

> **Noteï¼**To use the gifting system, activate either the **Free Trial,** or **Pro**edition. The number of configurable gifts depends on the selected package. For details, see the **Gift System** section in [Feature and Billing Description](https://www.tencentcloud.com/document/product/647/59407#658e2423-30d2-45e2-91b8-128b2730b072) and choose the package that fits your needs.

### Step 2: Configure Your Project

- **Project Configuration**:
  - **Video Live Streaming**: Follow [Video Live Streaming - Preparation](https://www.tencentcloud.com/document/product/647/72223) to complete TUILiveKit integration.
  - **Voice Chat Room**: Follow [Voice Chat Room - Preparation](https://www.tencentcloud.com/document/product/647/60334) to complete TUILiveKit integration.
- **Version Requirement**: TUILiveKit >= 3.2.0.

### Step 3. Add Gift List Display Page

Add the gift list display page to your app so the audience can browse available gifts. Use the sample code below to create the `GiftListView` component and add it to your view:

```
import TUILiveKitclass YourGiftViewController: UIViewController {    // 1. Create GiftListView object    //    - roomId: Should match the roomId of the live stream the audience has joined    lazy var giftListView = {      let view = GiftListView(roomId: liveId)      return view    }()    private let liveId: String    // ... additional code ...    public override func viewDidLoad() {        super.viewDidLoad()        // 2. Add the component to your view and set up the layout        view.addSubView(giftListView)        giftPlayView.snp.remakeConstraints { make in            make.leading.trailing.equalToSuperview()            make.height.equalTo(256)            make.bottom.equalToSuperview()        }    }}
```

### Step 4. Add Gift Animation Playback Page

Add the gift animation playback page to your app. The `GiftPlayView` component automatically receives gift messages and plays the corresponding animations. Use the sample code below to create the `GiftPlayView` component and add it to your view:

```
import TUILiveKit// YourAnchorViewController represents your host view controller. Audience side can refer to the following example:class YourAnchorViewController: UIViewController {    // 1. Create and initialize GiftPlayView object    //    - roomId: Should match the roomId of the live stream the audience has joined    lazy var giftPlayView = {      let view = GiftPlayView(roomId: liveId)      return view    }()    private let liveId: String    // ... other code ...    public override func viewDidLoad() {        super.viewDidLoad()        // 2. Add the component to your view and set up the layout        view.addSubView(giftPlayView)        giftPlayView.snp.remakeConstraints { make in          make.edges.equalToSuperview()        }    }}
```

## Next Steps

After completing the UI integration, your app will support basic gifting functionality. To build a production-ready gifting system, refer to the [Backend Integration and Advanced Features](https://www.tencentcloud.com/document/product/647/69849) guide to implement the following:

- **Custom Gift Configuration:** Upload custom gift icons, animations, and pricing via Server APIs.
- **Payment Integration:** Configure callback URLs to handle balance verification and payment processing through your billing backend.
- **PK Score Sync:** Convert gift values to PK scores in real-time during host battles.
- **Analytics:** Access gift transaction records, revenue metrics, and other operational data.
- **Upgrade Gift Effect SDK**: If SVGA does not meet your needs, you can integrate advanced animation players to support MP4, PAG, or other high-quality transparent animation formats.


---
*Source: [https://trtc.io/document/73997](https://trtc.io/document/73997)*
