# Video Live Streaming

This document guides you through building a basic live streaming app with host broadcasting and audience viewing capabilities using the core component [LiveCoreView](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.view/-live-core-view/index.html) from the **AtomicXCore SDK**.

### Core Features

**LiveCoreView** is a lightweight `View` component purpose-built for live streaming scenarios. It serves as the foundation of your live streaming implementation, encapsulating all complex streaming technologiesâincluding stream publishing and playback, co-hosting, and audio/video rendering. Use LiveCoreView as the "canvas" for your live video, enabling you to focus on developing your custom UI and interactions.

The following view hierarchy diagram illustrates the position and role of **LiveCoreView** within the live streaming interface:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/96041acccc0711f093295254001c06ec.png)

## Core Concepts

| **Core Concept** | **Core Responsibility** | **Key API / Property** |
| --- | --- | --- |
| LiveCoreView | Handles publishing, playing, and rendering audio/video streams. Provides adapter interfaces for integrating custom UI components (e.g., user info, PK progress bar). | `viewType`:`.pushView` (host publishing view)`.playView` (audience playback view)`setLiveId()`: Binds the live room ID for this view.`videoViewDelegate`: Adapter for custom video display UI slots. |
| LiveListStore | Manages the complete live room lifecycle (create, join, leave), synchronizes state, and listens for passive events (e.g., live ended, kicked out). | `createLive()`: Start live stream as host.`endLive()`: End live stream as host.`joinLive()`: Audience joins live room.`leaveLive()`: Leave live room. |
| LiveInfo | Defines room parameters before going live, such as room ID, seat layout mode, max co-hosts, etc. | `liveID`: Unique room identifier.[seatTemplate](#id): Layout template. |

## Preparation

### Step 1: Activate the Service

See [Activate Service](https://www.tencentcloud.com/document/product/647/60033) to obtain either the trial or paid version of the SDK.Then, go to [the Console](https://console.trtc.io/app) for application management, and get the following:

- `SDKAppID`: Application identifier (required). Tencent Cloud uses `SDKAppID` for billing and details.
- `SDKSecretKey`: Application secret key, used to initialize the configuration file with secret information.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a926d228cc0711f093295254001c06ec.png)

### Step 2: Import AtomicXCore into Your Project

1. **Install the Component**: Add `pod 'AtomicXCore'` to your `Podfile`, then run `pod install`.

```
target 'xxxx' do  pod 'AtomicXCore', '~> 4.0'end
```

2. **Configure App Permissions**: Add camera and microphone usage descriptions to your app's `Info.plist` file.

```
<key>NSCameraUsageDescription</key><string>TUILiveKit needs camera access to enable video recording with picture</string><key>NSMicrophoneUsageDescription</key><string>TUILiveKit needs microphone permission to enable sound in recorded videos</string>
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b47f58e0cc0711f0afdc52540044a08e.png)

### Step 3: Implement Login Logic

Call `LoginStore.shared.login` in your project to complete authentication. **This is required before using any functionality of AtomicXCore**.

> **Noteï¼**We recommend calling LoginStore.shared.login only after your app's own user authentication is successful, to ensure clear and consistent login logic.

```
import AtomicXCore//  AppDelegate.swiftfunc application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {    LoginStore.shared.login(sdkAppID: 1400000001,                  // Replace with your SDKAppID                            userID: "test_001",                    // Replace with your UserID                            userSig: "xxxxxxxxxxx") { result in    // Replace with your UserSig      switch result {        case .success(let info):        debugPrint("login success")        case .failure(let error):        debugPrint("login failed code:\\(error.code), message:\\(error.message)")      }    }    return true}
```

**Login API Parameter Description**

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| `SDKAppID` | `Int` | Get this from [TRTC console](https://console.trtc.io/app). |
| `UserID` | `String` | The unique ID for the current user. Must contain only English letters, numbers, hyphens, and underscores. |
| `userSig` | `String` | A ticket for Tencent Cloud authentication. Please note:Development Environment: You can use the local `GenerateTestUserSig.genTestSig` function to generate a `UserSig` or generate a temporary UserSig via the [UserSig Generation Tool](https://console.trtc.io/usersig).Production Environment: To prevent key leakage, you must use a server-side method to generate `UserSig`. For details, see [Generating UserSig on the Server](https://www.tencentcloud.com/document/product/647/35166). |

## Building a Basic Live Room

### Step 1: Implement Broadcaster Video Streaming

Follow these steps to quickly set up broadcaster video streaming:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bf07f34bcc0711f0ae4f52540099c741.png)

> **Noteï¼**For a complete broadcaster streaming implementation, refer to [TUILiveRoomAnchorViewController.swift](https://github.com/Tencent-RTC/TUIKit_iOS/blob/main/live/Sources/LiveStream/TUILiveRoomAnchorViewController.swift) in the TUILiveKit open source project.

1. **Initialize the Broadcaster Streaming View**

In your broadcaster view controller, create a `LiveCoreView` instance and set `viewType` to `.pushView`.

```
import AtomicXCore// YourAnchorViewController represents your broadcaster streaming view controllerclass YourAnchorViewController: UIViewController {    private let liveId: String    // 1. Add LiveCoreView as a property of your view controller    private let coreView = LiveCoreView(viewType: .pushView, frame: UIScreen.main.bounds)    // 2. Add a convenience initializer for instance initialization    //    - liveId: The ID of the live room to start streaming    public init(liveId: String) {        self.liveId = liveId        super.init(nibName: nil, bundle: nil)        self.coreView.setLiveID(liveId)    }    required init?(coder: NSCoder) {        fatalError("init(coder:) has not been implemented")    }    public override func viewDidLoad() {        super.viewDidLoad()        // 3. Add the broadcaster streaming view to your view        view.addSubview(coreView)    }}
```

2. **Open Camera and Microphone**

Call `DeviceStore.shared.openLocalCamera` and `DeviceStore.shared.openLocalMicrophone` to open the camera and microphone. **No further action is requiredâLiveCoreView automatically previews the current camera video stream**.

```
import AtomicXCoreclass YourAnchorViewController: UIViewController {    // ... other code ...    public override func viewDidLoad() {        super.viewDidLoad()        // Enable devices        openDevices()    }    private func openDevices() {        // 1. Enable front camera        DeviceStore.shared.openLocalCamera(isFront: true, completion: nil)        // 2. Enable microphone        DeviceStore.shared.openLocalMicrophone(completion: nil)    }}
```

3. **Start Live Streaming**

Call `LiveListStore.shared.createLive` to start streaming.

```
import AtomicXCoreclass YourAnchorViewController: UIViewController {    // ... other code ...    // Call the start streaming interface to begin live streaming    private func startLive() {        var liveInfo = LiveInfo()        // 1. Set the live room ID        liveInfo.liveID = self.liveId        // 2. Set the live room name        liveInfo.liveName = "test live"        // 3. Configure the seat layout template. Default: VideoDynamicGrid9Seats (portrait dynamic video grid layout)        liveInfo.seatTemplate = .videoDynamicGrid9Seats        // 4. Call LiveListStore.shared.createLive to start streaming        LiveListStore.shared.createLive(liveInfo) { [weak self] result in            guard let self = self else { return }            switch result {            case .success(let info):                debugPrint("startLive success")            case .failure(let error):                debugPrint("startLive error:\\(error.message)")            }        }    }}
```

`LiveInfo` Parameter Descriptions:

| **Parameter Name** | **Type** | **Attribute** | **Description** |
| --- | --- | --- | --- |
| `liveID` | `String` | Required | Unique identifier for the live room. |
| `liveName` | `String` | Optional | Title of the live room. |
| `notice` | `String` | Optional | Announcement for the live room. |
| `isMessageDisable` | `Bool` | Optional | Whether to mute chat (true: yes, false: no). |
| `isPublicVisible` | `Bool` | Optional | Whether the room is publicly visible (true: yes, false: no). |
| `seatMode` | `TakeSeatMode` | Optional | Seat mode (.free: free to take seat, .apply: apply to take seat). |
| `seatTemplate` | [SeatLayoutTemplate](#id) | Required | Seat layout template. |
| `coverURL` | `String` | Optional | Cover image URL for the live room. |
| `backgroundURL` | `String` | Optional | Background image URL for the live room. |
| `categoryList` | `NSNumber` | Optional | Category tag list for the live room. |
| `activityStatus` | `Int` | Optional | Live activity status. |
| `isGiftEnabled` | `Bool` | Optional | Whether to enable gift functionality (true: yes, false: no). |

4. **End Live Streaming**

After the live stream ends, call `LiveListStore.shared.endLive `to stop streaming and destroy the room. The SDK handles cleanup automatically.

```
import AtomicXCoreclass YourAnchorViewController: UIViewController {    // ... other code ...    // End live streaming    private func stopLive() {        LiveListStore.shared.endLive { [weak self] result in            guard let self = self else { return }            switch result {            case .success(let data):                debugPrint("endLive success")            case .failure(let error):                debugPrint("endLive error: \\(error.message)")            }        }    }}
```

### Step 2: Implement Audience Join and Watch

Enable audience viewing with the following steps:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d1169383cc0711f084a45254005ef0f7.png)

> **Noteï¼**For a complete audience playback implementation, refer to [TUILiveRoomAudienceViewController.swift](https://github.com/Tencent-RTC/TUIKit_iOS/blob/main/live/Sources/LiveStream/TUILiveRoomAudienceViewController.swift) in the TUILiveKit open source project.

1. **Implement the Audience Playback Page**

In your audience view controller, create a `LiveCoreView` instance and set `viewType` to `.playView`.

```
import AtomicXCoreclass YourAudienceViewController: UIViewController {    // 1. Initialize the audience playback page    private let coreView = LiveCoreView(viewType: .playView, frame: UIScreen.main.bounds)    private let liveId: String    public init(liveId: String) {        self.liveId = liveId        super.init(nibName: nil, bundle: nil)        // 2. Bind the live ID        self.coreView.setLiveID(liveId)    }    required init?(coder: NSCoder) {        fatalError("init(coder:) has not been implemented")    }    public override func viewDidLoad() {        super.viewDidLoad()        // 3. Add the playback view to your view        view.addSubview(coreView)    }}
```

2. **Join the Live Room to Watch**

Call `LiveListStore.shared.joinLive` to join the live stream. **No further action is requiredâLiveCoreView will automatically play the current room's video stream**.

```
import AtomicXCoreclass YourAudienceViewController: UIViewController {    // ... other code ...    public override func viewDidLoad() {        super.viewDidLoad()        view.addSubview(coreView)        // 4. Join the live room        joinLive()    }    private func joinLive() {        // Call LiveListStore.shared.joinLive to enter the live room        // - liveId: Same liveId as the broadcaster        LiveListStore.shared.joinLive(liveID: liveId) { [weak self] result in            guard let self = self else { return }            switch result {            case .success(let info):                debugPrint("joinLive success")            case .failure(let error):                debugPrint("joinLive error \\(error.message)")                // If joining fails, exit the page                // self.dismiss(animated: true)            }        }    }}
```

3. **Leave the Live Room**

When the audience leaves, call `LiveListStore.shared.leaveLive` to exit. The SDK will automatically stop playback and leave the room.

```
import AtomicXCoreclass YourAudienceViewController: UIViewController {    // ... other code ...    // Leave the live room    private func leaveLive() {        LiveListStore.shared.leaveLive { [weak self] result in            guard let self = self else { return }            switch result {            case .success:                debugPrint("leaveLive success")            case .failure(let error):                debugPrint("leaveLive error \\(error.message)")            }        }    }}
```

### Step 3: Listen for Live Events

After joining a live room, handle "passive" events such as the broadcaster ending the stream or the audience being removed. If you do not listen for these events, the audience UI may remain on a black screen, impacting user experience.

Subscribe to `liveListEventPublisher` from `LiveListStore` to listen for events:

```
import AtomicXCoreimport Combine // 1. Import the Combine frameworkclass YourAudienceViewController: UIViewController {    // ... other code (coreView, liveId, init, deinit, joinLive, leaveLive, etc.) ...    // 2. Define cancellableSet to manage subscription lifecycle    private var cancellableSet: Set<AnyCancellable> = []    public override func viewDidLoad() {        super.viewDidLoad()        view.addSubview(coreView)        // 3. Listen for live events        setupLiveEventListener()        // 4. Join the live room        joinLive()    }    // 5. Add a method to set up event listeners    private func setupLiveEventListener() {        LiveListStore.shared.liveListEventPublisher            .receive(on: RunLoop.main) // Ensure UI updates are handled on the main thread            .sink { [weak self] event in                guard let self = self else { return }                switch event {                case .onLiveEnded(let liveID, let reason, let message):                    // Live stream ended                    debugPrint("Live ended. liveID: \\(liveID), reason: \\(reason.rawValue), message: \\(message)")                    // Handle logic to exit the live room, e.g., close the current page                    // self.dismiss(animated: true)                case .onKickedOutOfLive(let liveID, let reason, let message):                    // Kicked out of live stream                    debugPrint("Kicked out of live. liveID: \\(liveID), reason: \\(reason.rawValue), message: \\(message)")                    // Handle logic to exit the live room                    // self.dismiss(animated: true)                }            }            .store(in: &cancellableSet) // Manage subscription    }    // ... joinLive() and leaveLive() methods ...}
```

### Run and Test

After integrating `LiveCoreView`, you will have a pure video rendering view with full live streaming capabilities, but without any interactive UI. To add interactive features, see [Enriching the Live Streaming Scene](#enriching-the-live-streaming-scene).

| **** | **Dynamic Grid Layout** | **Floating Window Layout** | **Fixed Grid Layout** | **Fixed Window Layout** |
| --- | --- | --- | --- | --- |
| Template ID | .videoDynamicGrid9Seats | .videoDynamicFloat7Seats | .videoFixedGrid9Seats | .videoFixedFloat7Seats |
| Description | Default layout; grid size adjusts dynamically based on number of co-hosts. | Co-hosts are displayed as floating windows. | Fixed number of co-hosts; each occupies a fixed grid. | Fixed number of co-hosts; guests are displayed as fixed windows. |
| Example | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6a730a2ecc0d11f084a45254005ef0f7.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/71c322e9cc0d11f084a45254005ef0f7.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a1855792cc0d11f0ae4f52540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8885e3ffcc0d11f0afdc52540044a08e.png) |

## Advanced Features

### Synchronizing Custom Status in Live Streaming Room

In live streaming room, the host may need to synchronize custom information to all audience members, such as "current room topic" or "background music info". Use the `metaData` feature of LiveListStore to achieve this.

#### Implementation

1. On the host side, set custom information (recommended as JSON) to one or more keys using the `updateLiveMetaData` API. AtomicXCore will synchronize these changes in real time to all audience members.
2. On the audience side, subscribe to `LiveListState.currentLive` and listen for changes in `metaData`. When a relevant key is updated, parse its value and update your business state.

#### Code Example

```
import AtomicXCoreimport Combine// 1. Define a background music model (recommended: Codable)struct MusicModel: Codable {    let musicId: String    let musicName: String}// 2. Host side: Push background music infofunc updateBackgroundMusic(music: MusicModel) {    guard let jsonData = try? JSONEncoder().encode(music),          let jsonString = String(data: jsonData, encoding: .utf8) else { return }    let metaData = ["music_info": jsonString]    LiveListStore.shared.updateLiveMetaData(metaData) { result in        if case .success = result {            print("Background music \\(music.musicName) pushed successfully")        } else if case .failure(let error) = result {            print("Background music push failed: \\(error.message)")        }    }}// 3. Audience side: Subscribe and update business logicprivate func subscribeToDataUpdates() {    LiveListStore.shared.state        // Listen for metaData changes in the current room        .subscribe(StatePublisherSelector(keyPath: \\LiveListState.currentLive))        .map { $0.metaData["music_info"] }        .removeDuplicates()        .receive(on: DispatchQueue.main)        .sink { jsonString in            guard let jsonString = jsonString,                  let data = jsonString.data(using: .utf8),                  let music = try? JSONDecoder().decode(MusicModel.self, from: data) else {                return            }            // Update business state, play new music            // ... (e.g.: playMusic(music))        }        .store(in: &cancellables)}
```

## Enriching the Live Streaming Scene

Once the basic live streaming functionality is in place, refer to the following guides to add interactive features to your live stream:

| **Feature** | **Description** | **Store** | **Implementation Guide** |
| --- | --- | --- | --- |
| Enable Audience Audio/Video Co-hosting | Audience can apply to join the host and interact via real-time video. | [CoGuestStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore) | [Implementation Guide](https://www.tencentcloud.com/document/product/647/74598) |
| Enable Host Cross-room PK | Hosts from different rooms can connect for interaction or PK. | [CoHostStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststore) | [Implementation Guide](https://www.tencentcloud.com/document/product/647/74600) |
| Add Bullet Chat Feature | Audience can send and receive real-time text messages in the live room. | [BarrageStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/barragestore) | [Implementation Guide](https://www.tencentcloud.com/document/product/647/74602) |
| Build a Gift Giving System | Audience can send virtual gifts to the host, increasing engagement and fun. | [GiftStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/giftstore) | [Implementation Guide](https://www.tencentcloud.com/document/product/647/74604) |

## API Documentation

| **Store/Component** | **Description** | **API Reference** |
| --- | --- | --- |
| LiveCoreView | Core view component for displaying and interacting with live video streams. Handles video rendering and view widgets, supports host streaming, audience co-hosting, host connections, and more. | [LiveCoreView](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/livecoreview/) |
| LiveListStore | Manages the full lifecycle of live rooms: create/join/leave/destroy rooms, query room list, modify live info (name, announcement, etc.), and listen to live status events (e.g., kicked out, ended). | [LiveListStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore) |
| DeviceStore | Controls audio/video devices: microphone (on/off, volume), camera (on/off, switch, quality), screen sharing, and real-time device status monitoring. | [DeviceStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestore) |
| CoGuestStore | Manages audience co-hosting: apply/invite/accept/reject co-host requests, member permission control (microphone/camera), and status synchronization. | [CoGuestStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore) |
| CoHostStore | Handles host cross-room connections: supports multiple layout templates (dynamic grid, etc.), initiates/accepts/rejects connections, and manages co-host interactions. | [CoHostStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststore) |
| BattleStore | Manages host PK battles: initiate PK (set duration/opponent), manage PK status (start/end), synchronize scores, and listen for battle results. | [BattleStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/battlestore) |
| GiftStore | Handles gift interactions: get gift list, send/receive gifts, and listen for gift events (including sender and gift details). | [GiftStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/giftstore) |
| BarrageStore | Supports live chat: send text/custom danmaku, maintain danmaku list, and monitor danmaku status in real time. | [BarrageStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/barragestore) |
| LikeStore | Handles like interactions: send likes, listen for like events, and synchronize total like count. | [LikeStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/likestore) |
| LiveAudienceStore | Manages audience: get real-time audience list (ID/name/avatar), count audience, and listen for join/leave events. | [LiveAudienceStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveaudiencestore) |
| AudioEffectStore | Audio effects: voice change (child/male), reverb (KTV, etc.), ear return adjustment, and real-time effect switching. | [AudioEffectStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstore) |
| BaseBeautyStore | Basic beauty filters: adjust smoothing/whitening/rosiness (0-9), reset beauty status, and synchronize effect parameters. | [BaseBeautyStore](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/basebeautystore) |

## FAQs

### Why is the screen black with no video after the host calls createLive or the audience calls joinLive?

- **Check**`setLiveID`: Ensure you have set the correct liveID for the LiveCoreView instance before calling start or join methods.
- **Check device permissions**: Ensure the app has system permissions for camera and microphone usage.
- **Check the host side**: Has the host called `DeviceStore.shared().openLocalCamera(true)`to enable the camera?
- **Check the network**: Ensure the device has a stable network connection.

### After the host enables the camera, why is there a local video preview after starting the stream, but a black screen before starting?

- **Check the host side**: Make sure the host streaming view (`LiveCoreView`) has its `viewType` set to `PUSH_VIEW`.
- **Check the audience side**: Make sure the audience playback view (`LiveCoreView`) has its `viewType` set to `PLAY_VIEW`.

### What restrictions and rules apply to `updateLiveMetaData`?

To maintain system stability and efficiency, metaData usage follows these rules:

- **Permissions**: Only hosts and administrators can call `updateLiveMetaData`. Regular audience members cannot.
- **Quantity and Size Limits:**
  - Each room supports up to **10** keys.
  - Each key can be up to **50 bytes**; each value up to **2KB**.
  - The total size of all values in a room cannot exceed **16KB**.
- **Conflict Resolution**: The update mechanism is "last write wins". If multiple administrators modify the same key in quick succession, the last change takes effect. Avoid concurrent modifications to the same key in your business logic.

### sync Fails to Copy Third-party Library Resources Due to Insufficient Permissions

For example, when integrating the SnapKit framework with Xcode, you may encounter the following build error:

```
rsync(xxxx):1:1: SnapKit.framework/SnapKit_Privacy.bundle/: mkpathat: Operation not permitted
```

**Cause**

Xcode's user script sandboxing mechanism restricts the rsync script's write access to `SnapKit.framework` resource files during the build process, causing the `SnapKit_Privacy.bundle` in the framework to fail to copy properly.

Solution Steps

1. Disable user script sandboxing. Open your Xcode project, go to **Build Settings**, search for User Script Sandboxing (or `ENABLE_USER_SCRIPT_SANDBOXING`), and change its value from YES to NO.
2. Clean and rebuild the project. Run **Product â Clean** Build Folder to clear the project cache, then rebuild and run the project.


---
*Source: [https://trtc.io/document/74594](https://trtc.io/document/74594)*
