# Audience Watching

**TUILiveKit**âs audience viewing page offers a comprehensive suite of live streaming and interactive features designed for seamless integration into your application. With TUILiveKit, you can quickly deliver a rich live experience tailored to your audienceâs needs.

## Feature Overview

- **Live streaming:** Clear and smooth viewing of the host's real-time live stream.
- **Interactive co-guest:** Apply for mic connection to interact with the host via audio and video.
- **Live information:** View the live streaming room title, description, and audience list, etc.
- **Live interactive:** Send a gift (with animation effects and host notification), like (with animation and real-time statistics), and interact via bullet screen.

| **Live Streaming** | **Interactive co-guest** | **Live Information** | **Live Interactive** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/691552f49a0411f0930a5254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/690f70159a0411f0a90152540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/68fdbc449a0411f0a90152540099c741.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/690db2169a0411f0930a5254007c27c5.png) |

## Quick Start

### Step 1. Activate the Service

Refer to the [Activate Service](https://www.tencentcloud.com/document/product/647/60033) document to enable the **trial version** or activate the **Pro Edition** package.

### **Step 2: Install**TUILiveKit

Refer to  [Preparations](https://www.tencentcloud.com/document/product/647/63255) guide to integrate the TUILiveKit SDK.

### Step 3: Add Audience Viewing Page

`TUILiveRoomAudienceWidget` provides a complete audience-side UI and business logic for live streaming scenarios. This widget does not support floating window mode. If you require floating window, see [Add Floating Window (Audience Page)](#330378b2-2f2c-45ba-9a1a-743448cc3d19).

To launch the audience viewing page or embed it in your widget tree, set up the entry point for calling `TUILiveRoomAudienceWidget` according to your business logic and use one of the following approaches:

Direct Navigation

Integrate Into Widget Tree

```
import 'package:tencent_live_uikit/tencent_live_uikit.dart';// Navigate to the audience viewing pageNavigator.push(context, MaterialPageRoute(  builder: (BuildContext context) {     final roomId = "test_live_room_id";     return TUILiveRoomAudienceWidget(roomId: roomId);}));
```

```
// --- Select one integration method based on your Widget tree structure ---// [Option one] As the only child Widget (single subtree)// Suitable for containers like Container, Padding that usually only contain one child WidgetContainer(       child: TUILiveRoomAudienceWidget(roomId: roomId) // Integrate audience viewing here)// [Option two] As one of multiple child Widgets (multiple subtrees)// Suitable for layouts like Column, Row, Stack that can contain multiple child WidgetsStack(       children: [           YourOtherWidget(), // Your other child Widget           TUILiveRoomAudienceWidget(roomId: roomId), // Integrate audience viewing here        YourOtherWidget(), // Your other child Widget   ])
```

After integration, After integration, calling this code will open the audience page and start playback of live stream, as shown in the figure for viewing live stream in [Features Overview](#ea46de7c-2609-4756-8514-ee368993168c).

### Step 4: (Optional) Add a Floating Window

`TUILiveRoomAudienceOverlay` enables floating window mode for the audience viewing page. During a live stream, you can switch between**in-app** and **out-of-app** (Picture-in-Picture) floating window modes. `TUILiveRoomAudienceOverlay` is built using Flutterâs official `Overlay` API and native Picture-in-Picture. To integrate:

#### 1. Enable System Picture-in-Picture

Refer to [Project Configuration](https://www.tencentcloud.com/document/product/647/63255#62b3f143-07f5-416a-8057-fff865e35d46) to enable the system Picture-in-Picture feature.

#### 2. Add a Secondary Navigator

Refer to [Floating Live Room Configuration](https://www.tencentcloud.com/document/product/647/63255#43bbc9ad-91f3-4216-8807-462e9df28f7a) to add a new secondary navigator in the App. This navigator hosts the live streaming page, keeping it separate from your main navigation stack and enabling floating window effects.

#### 3. Navigate to the Floating Window

At the entry point where your audience enters the room (based on your business logic), navigate to the viewing page as follows:

```
import 'package:tencent_live_uikit/tencent_live_uikit.dart';// Navigate to the viewing pageNavigator.push(context, MaterialPageRoute(  builder: (BuildContext context) {     final roomId = "test_live_room_id";     return TUILiveRoomAudienceOverlay(roomId: roomId);}));
```

> **Note:**`TUILiveRoomAudienceOverlay` cannot be embedded as a child widget in container widgets (such as Container, Stack, etc.); it must be navigated to as a standalone page. This is because `Overlay` is used internally, and LiveKit needs to control the entire `Overlay` page to switch floating window modes.On iOS, only regular audience members can enter out-of-app floating window mode.

#### Floating Window Mode Effect

Click the floating window button at the top right of the page to enter floating window mode, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0db067cde22c11f095ab5254001c06ec.png)

#### Out-of-App Floating Window Effect

Tap **More** > **PIP** at the bottom of the viewing page to enable Picture-in-Picture. When your app moves to the background, it will automatically enter system Picture-in-Picture mode:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/602e0c95e22c11f08775525400bf7822.png)

## Customize UI Layout

### Text Customization (ARB)

TUILiveKit uses **ARB files**and the **Flutter standard internationalization (i18n) solution** to manage the UI text display. You can directly edit the ARB files in the `livekit/lib/common/language/i10n/` directory to modify the text:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f4575de09a0911f091df5254005ef0f7.png)

- `livekit_en.arb`: English Text.
- `livekit_zh.arb`: Simplified Chinese Text.
- `livekit_zh_Hant.arb`: Traditional Chinese Text.

After editing, run `flutter gen-l10n` in your terminal to regenerate localization code.

### Icon Customization

TUILiveKitâs UI image assets are stored in the `livekit/assets/images/` directory. To update icons, simply replace the PNG files in this folder.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fe57fa0798f511f0961e52540099c741.png)

Rebuild and run the application, and you will see the updated icon.

## Next Steps

Congratulations! You have successfully integrated **Audience Viewing**. Next, you can implement features such as **Host Streaming**, and **Live Stream List**. Please refer to the table below:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Streaming** | The complete workflow for a host to start a stream, including pre-stream setup and various in-stream interactions. | [Host Streaming](https://www.tencentcloud.com/document/product/647/73742) |
| **Live Stream List** | Display the live stream list interface and features, including the live stream list and room information display. | [Live Stream List](https://www.tencentcloud.com/document/product/647/73761) |

## FAQs

### Why does the video screen go black after the audience chooses video interaction?

Go to **Phone Settings** > **App** > **Camera** and check whether camera permission is enabled. Refer to the image below:

| iOS | Android |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/327c4be8991f11f0a3b8525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/32793103991f11f08bb25254005ef0f7.png) |

### Why canât other audience members see live comments sent by an audience member?

- **Reason 1**: First check the network connection to ensure the viewer's device network is online and stable.
- **Reason 2**: The viewer has been **muted (banned)** by the host and cannot send live comments.
- **Reason 3**: The live comment may contain blocked keywords. Make sure comments comply with live room rules.

### Why canât the app enter out-of-app floating window (Picture-in-Picture) mode when in the background?

Refer to [Entering Out-Of-App Floating Window](#c28b2363-6d3e-40e8-be0d-4e4dba28a665). After entering the live room, enable the Picture-in-Picture switch.

On Android, after enabling Picture-in-Picture, the app will automatically check the system setting. If Picture-in-Picture is not enabled, the app will prompt you to allow this mode in system settings:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e64f5d4de22b11f08775525400bf7822.png)

### Why do pop-up windows not appear or get covered?

If you have integrated `TUILiveRoomAudienceOverlay`, ensure that pop-up components (such as BottomSheet, Dialog, etc.) use the `rootNavigator` context (recommended: `Global.appContext()`).

**Reason:** The live streaming page Overlay is rendered on the `secondaryNavigator`. Pop-ups using the `secondaryNavigator` context will be obstructed by the Overlay because, on the same Navigator, the Overlay layer is above regular pages, allowing it to float above them. Using the `rootNavigator` ensures pop-ups display correctly above the Overlay.


---
*Source: [https://trtc.io/document/73749](https://trtc.io/document/73749)*
