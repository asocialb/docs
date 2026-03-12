# Host Streaming

The **TUILiveKit** Host Live Streaming Page provides a **full-featured UI** for live streaming scenarios. It supports the rapid deployment of core host capabilities, allowing you to efficiently integrate the live streaming workflow without worrying about complex UI and logic implementation.

## Feature Overview

- **Pre-stream Setup**: Supports various personalized configurations before the host goes live, including room name, background, video preview, beauty filters (beauty effects) debugging, audio effects debugging, and layout templates.
- **Co-Host Interaction:** Supports real-time interaction (co-hosting) with viewers or other hosts during the live stream.
- **Audience Interaction:** Supports rich interaction forms such as barrage (bullet screen) and gifts.
- **Live Room Management**: Supports displaying the online user list and various management operations within the room, such as muting (banning) and kicking users.

| **Pre-stream Setup** | **Co-Host Interaction** | **Audience Interaction** | **Live Room Management** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cb616afc9a0011f09936525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cb7326369a0011f0a90152540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cb6917189a0011f091df5254005ef0f7.png) |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cb629b2b9a0011f0a90152540099c741.png) |

## Quick Start

### Step 1. Activate the Service

Refer to the [Activate Service](https://www.tencentcloud.com/document/product/647/60033) document to enable the Free trial or official package.

### Step 2. Code Integration

Refer to  [Preparations](https://www.tencentcloud.com/document/product/647/72223)  guide to integrate the TUILiveKit SDK.

### Step 3. Add the Pre-stream Setup view

The `AnchorPrepareView` component already has built-in features for camera preview, audio effects settings, layout settings, and other functional configurations. You need to create and load `AnchorPrepareView`. The specific example code is as follows:

Swift

```
// YourAnchorPrepareViewController represents the view controller for loading the anchor starts live streaming viewclass YourAnchorPrepareViewController: UIViewController {    // 1. Declare to create a LiveCoreView instance    private let coreView = LiveCoreView()        // 2. Lazy load AnchorPrepareView    private lazy var prepareView: AnchorPrepareView = {        // 3. Import the coreView instance object when initializing AnchorPrepareView        let view = AnchorPrepareView(coreView: coreView)        return view    }()    public override func viewDidLoad() {        super.viewDidLoad()        // 4. Add prepareView to view        view.addSubview(prepareView)        prepareView.snp.makeConstraints { make in            make.edges.equalToSuperview()        }    }}
```

### Step 4. Add the Host Streaming view

The `AnchorView` component has built-in features for audio/video pushing (streaming), viewer co-hosting, live interaction, and live room management. You only need to create and load `AnchorView`. The specific example code is as follows:

swift

```
// YourAnchorPrepareViewController represents the view controller for loading the anchor starts live streaming viewclass YourAnchorViewController: UIViewController {        // Live room information    private let liveInfo: LiveInfo    // Core view component    private let coreView: LiveCoreView    // Room entry action:    //    RoomBehavior.createRoom: Broadcaster creates a room    //    RoomBehavior.enterRoom: Audience enters room    private let behavior: RoomBehavior        // 1. Declare anchorView instance    private let anchorView: AnchorView        // 2. Add new construct function to complete instance initialization    public init(liveInfo: LiveInfo, coreView: LiveCoreView? = nil) {        self.liveInfo = liveInfo        self.behavior = behavior        if let coreView = coreView {            self.coreView = coreView        } else {            self.coreView = LiveCoreView()        }        // 3. Instantiate the live stream publishing page        self.anchorView = AnchorView(liveInfo: liveInfo, coreView: self.coreView, behavior: .createRoom)        super.init(nibName: nil, bundle: nil)    }        public override func viewDidLoad() {        super.viewDidLoad()        // 4. Add anchorView to view        view.addSubview(anchorView)        anchorView.snp.makeConstraints { make in            make.edges.equalToSuperview()        }      }}
```

### **Step 5.**Transition from Pre-stream Setup to Host Streaming

Combine [Step 3](#c9d8cb5f-0da5-496d-b175-0c0d58cdfb02) to implement the delegate events of the `AnchorPrepareView` component, completing the transition to the host streaming page. The specific example code is as follows:

swift

```
// Set proxy during AnchorPrepareView initialization in Step 1class YourAnchorPrepareViewController: UIViewController {        private lazy var prepareView: AnchorPrepareView = {        let view = AnchorPrepareView(coreView: coreView)        // 1. Set callback proxy        prepareView.view.delegate = self        return view    }()}// 2. Implement AnchorPrepareViewDelegate callback proxyextension YourAnchorPrepareViewController : AnchorPrepareViewDelegate {    // Respond to the click event of the go live button    //   - state: PrepareState encapsulates camera, sound effect and other feature settings of the live stream publishing view. Just set it as the following example code.    public func onClickStartButton(state: PrepareState) {        // 4. Navigate to the live stream publishing page        // 4.1. Initialize live information        var liveInfo = LiveInfo()        // you only need to set roomId        liveInfo.roomId = roomId        liveInfo.name = state.roomName        liveInfo.coverUrl = state.coverUrl        liveInfo.isPublicVisible = state.privacyMode == .public        liveInfo.seatLayoutId = .videoDynamicGrid9Seats        liveInfo.backgroundUrl = state.coverUrl        liveInfo.pkTemplateId = state.pkTemplateMode.rawValue                // 4.2. Instantiate your live stream view controller        let anchorVC = YourAnchorViewController(liveInfo: liveInfo, coreView: coreView)        anchorVC.modalPresentationStyle = .fullScreen        // 4.3. Navigate to your live stream view controller        present(anchorVC, animated: false)    }    // Respond to the click event of the back button    public func onClickBackButton() {        if let nav = navigationController {            nav.popViewController(animated: true)        } else {            dismiss(animated: true)        }    }}
```

## Customize Your UI Layout

**TUILiveKit** supports flexible customization of the host setup and live pages, allowing you to adjust the layout and hide/show functional modules based on your business requirements.

### Live Layout Template Selection

**TUILiveKit** provides **4 live layout templates**. You can select the appropriate style in the **"Layout" UI interaction** entry on the host setup page:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af4e2ca79a0111f0bf2352540044a08e.png)

#### Layout Template Overview

| Name | dynamic grid layout | dynamic float layout | static grid layout | static float layout |
| --- | --- | --- | --- | --- |
| Template ID | .videoDynamicGrid9Seats | .videoDynamicFloat7Seats | .videoFixedGrid9Seats | .videoFixedFloat7Seats |
| Description | The default layout; grid size adjusts dynamically based on the number of co-hosts. | Co-hosts are displayed in floating small windows. | The number of co-hosts is fixed, and each co-host occupies a fixed grid cell. | The number of co-hosts is fixed, and co-hosts are displayed in fixed small windows. |
| Preview | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af31e9cf9a0111f091df5254005ef0f7.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af1ec6c79a0111f09936525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af2c29b69a0111f091df5254005ef0f7.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af37d0b59a0111f09936525400e889b2.png) |

### Custom `AnchorPrepareView` Feature Area

By calling the API of `prepareView` created in [Step 3](#c9d8cb5f-0da5-496d-b175-0c0d58cdfb02) , you can customize and hide the operation area or specific features on the host setup page:

swift

```
// YourAnchorPrepareViewController represents the view controller for loading the anchor starts live streaming viewclass YourAnchorPrepareViewController: UIViewController {    private let coreView = LiveCoreView()        private lazy var prepareView: AnchorPrepareView = {        let view = AnchorPrepareView(coreView: coreView)        view.delegate = self        return view    }()    public override func viewDidLoad() {        super.viewDidLoad()        // 1. Add prepareView to view        view.addSubview(prepareView)        prepareView.snp.makeConstraints { make in            make.edges.equalToSuperview()        }        // 2. Custom function area - Example: Hide beauty effect feature         prepareView.disableMenuBeautyButton(true)         }}
```

| **API** | **Description** |
| --- | --- |
| `disableFeatureMenu(true)` | Hide Entire Feature Area |
| `disableMenuBeautyButton(true)` | Hide Beauty Effect Button |
| `disableMenuAudioEffectButton(true)` | Hide Sound Effect Button |
| `disableMenuSwitchCameraButton(true)` | Hide Camera Toggle Button |

### Customize `AnchorView` Feature Area

By calling the API of [Step 4](#1c47a194-38a4-4789-a636-0fa74221800a) created `anchorView`, you can customize and hide the operation area or specific features on the host live page:

swift

```
disableFooterCoHost
```

| **API** | **Description** |
| --- | --- |
| `disableHeaderVisitorCnt(true)` | Hide Top Audience List Feature |
| `disableFooterCoGuest(true)` | Hide Bottom Audience Mic Connection Feature |
| `disableFooterCoHost(true)` | Hide Bottom Anchor Connection Feature |
| `disableFooterBattle(true)` | Hide Bottom Anchor PK Function |

### Text Customization (Localization)

TUILiveKit uses the [Apple Strings Catalog](https://developer.apple.com/documentation/xcode/localizing-and-varying-text-with-a-string-catalog)(`.xcstrings`) format, introduced in **Xcode 15**, to manage the text displayed in the UI. You can modify the string resources using Xcode's graphical interface:

> **Note:**[Apple Strings Catalog](https://developer.apple.com/documentation/xcode/localizing-and-varying-text-with-a-string-catalog) (.xcstrings) is a localization format introduced in Xcode 15. It enhances how developers manage localized strings, supporting a structured format to handle plurals, device-specific variants, etc. This format is becoming the recommended way to manage localization for iOS and macOS applications.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b2e3b9de991d11f0a207525400bf7822.png)

### Icon Customization (Image Assets)

TUILiveKit uses `TUILiveKit.xcassets` to manage the image resources for the UI. You can quickly modify the custom icons using Xcode's graphical tools.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c0e8364f991b11f0961e52540099c741.png)

## Next Steps

Congratulations! You have successfully integrated the **Host Live Streaming**component. Next, you can implement features such as **audience viewing**, **live stream list** and **gift system**. Please refer to the table below:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Audience Viewing** | Audience can watch live streaming after entering the anchor's live streaming room, with features like audience mic connection, live room information, online audience, and bullet screen display. | [Audience Viewing](https://www.tencentcloud.com/document/product/647/72227) |
| **Live Stream List** | Display the live stream list interface and features, including the live stream list and room information display. | [Live Stream List](https://www.tencentcloud.com/document/product/647/72226) |
| **Gift System** | Support custom gift asset configuration, billing system integration, and gift-sending in PK scenarios. | [Gift System](https://www.tencentcloud.com/document/product/647/69849) |

## FAQs

### Why is there no video feed after starting the stream?

Please go to **Settings** > **App** > **Camera** and check whether the camera permission is enabled. See the following figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/505f45d9991611f0a207525400bf7822.png)

### Why does clicking the "Start Stream" button fail with a "Not Logged In" prompt?

Refer to the [Complete Login](https://www.tencentcloud.com/document/product/647/72223#6ebcab01-c3d7-4fb4-a933-016cf1cf5193) and confirm completion of login feature integration.


---
*Source: [https://trtc.io/document/72225](https://trtc.io/document/72225)*
