# Host Broadcasting

`UILiveKit` Voice Chat Room is a ready-to-use interface providing all the core functionalities for starting a live stream. It enables you to integrate a host broadcasting flow into your app with simple steps.

## Feature Overview

- **Pre-Live Preview**: Allows hosts to configure personalized settings such as room name and cover image before going live.
- **Seat Management**: Supports seat management operations including taking a seat, leaving a seat, muting, and locking seats.
- **Audience Interaction**: Enables interactive features such as live chat (bullet comments), virtual gifts, and likes.
- **Live Room Management**: Displays the online user list and provides moderation controls such as muting or removing users from the live room.

| **Pre-Live Preview** | **Seat Management** | **Audience Interaction** | **Live Room Management** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2fccecbdc06d11f0a0935254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f5ee976c06d11f0b4a7525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f8abc35c06d11f083155254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f5ef6a0c06d11f0aa02525400e889b2.png) |

## Quick Integration

## Integrate the Component

Follow the [Preparation](https://www.tencentcloud.com/document/product/647/60334) guide to integrate `TUILiveKit`.

### Create and Present the Voice Room View Controller

The `TUIVoiceRoomViewController` component provides a complete host-side UI and business logic for the voice room scenario. To enable hosts to start a live session, simply create and present this view controller. We recommend triggering the following logic in your appâs "Start Live" button click handler:

```
import TUILiveKitimport UIKit// YourViewController represents the view controller from which you start the live sessionclass YourViewController: UIViewController {    // Handle the "Start Live" button click event    @objc func onStartVoiceRoomClicked() {        // 1. Configure room parameters (RoomParams)        var params = RoomParams()        params.maxSeatCount = 10 // Maximum number of seats        params.seatMode = .applyToTake // Seat mode        // 2. Instantiate the voice room controller        let roomId = "test_voice_room_id"        let voiceRoomVC = TUIVoiceRoomViewController(roomId: roomId, behavior: .prepareCreate, roomParams: params)        voiceRoomVC.modalPresentationStyle = .fullScreen        // 3. Present the voice room page        present(voiceRoomVC, animated: true)    }}
```

- **TUIVoiceRoomViewController Parameter Reference:**

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| `roomId` | `string` | Globally unique ID for the live room. |
|  `behavior` | `RoomBehavior` | Room entry behavior:- autoCreate: Automatically create and enter the live room.- prepareCreate: Enter the pre-live preview page first, then create and enter the live room after the user clicks "Start Live".- join: Audience joins the room. |
| ```roomParams` | `RoomParams?` | Parameters for the host to start the live session. See the table below for details. |

- **RoomParams Parameter Reference:**

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| `maxSeatCount` | `Int` | Maximum number of seats in the live room. |
| `seatMode` | `TUISeatMode` | Audience seat mode:- `applyToTake`: Audience must apply and be approved by the host to take a seat.- `freeToTake`: Audience can take a seat freely without host approval. |

## Customize UI

`TUILiveKit` provides flexible UI customization to meet a variety of business requirements. You can select different layout templates and easily update UI text and icons.

### Live Layout Template Selection

`TUILiveKit` Voice Room offers **two layout styles**. Select your preferred style using the **"Layout" option** on the host's pre-live preview page:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ad2aca58c08011f0aa02525400e889b2.png)

#### Layout Overview:

| **** | **Chat Room** | **KTV** |
| --- | --- | --- |
| **Description** | Default layout; displays only the seat grid. | Displays a KTV song player above the seat grid. |
| **Preview** | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/14641e10c07211f08c0e52540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dc9a83e1c07311f083155254001c06ec.png) |

### Text Customization (Localization)

`TUILiveKit` uses the [Apple Strings Catalog](https://developer.apple.com/documentation/xcode/localizing-and-varying-text-with-a-string-catalog)(`.xcstrings`) format, introduced in **Xcode 15**, to manage the text displayed in the UI. You can modify the string resources using Xcode's graphical interface:

> **Note:**[Apple Strings Catalog](https://developer.apple.com/documentation/xcode/localizing-and-varying-text-with-a-string-catalog) (.xcstrings) is a localization format introduced in Xcode 15. It enhances how developers manage localized strings, supporting a structured format to handle plurals, device-specific variants, etc. This format is becoming the recommended way to manage localization for iOS and macOS applications.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cfb30877c06d11f08c0e52540044a08e.png)

### Icon Customization (Image Assets)

TUILiveKit uses `TUILiveKit.xcassets` to manage the image resources for the UI. You can quickly modify the custom icons using Xcode's graphical tools.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cf9b6711c06d11f0aa02525400e889b2.png)

## Next Steps

You have now successfully integrated **host live streaming**. Next, implement features such as **audience listening**, **live stream list** and **gift system**. See the table below for details:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Audience Listening** | Enables users to join as audience members, listen to the host, take seats, and view live chat (bullet comments). | [Integration Guide](https://www.tencentcloud.com/document/product/647/74328) |
| **Live Stream List** | Displays a list of live rooms and their details. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74326) |
| **Gift System** | Support custom gift asset configuration, billing system integration, and gift-sending in PK scenarios. | [Integration Guide](https://www.tencentcloud.com/document/product/647/69849) |

## FAQs

### No sound after going live?

Go to your device's `Settings > App > Microphone` and ensure that microphone permissions are enabled.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2372bb5fc07211f09c26525400bf7822.png)

### Unable to go live when clicking the start button, with a "Not Logged In" prompt?

See [Complete Login](https://www.tencentcloud.com/document/product/647/60334#6ebcab01-c3d7-4fb4-a933-016cf1cf5193) to ensure login functionality is properly integrated.


---
*Source: [https://trtc.io/document/74324](https://trtc.io/document/74324)*
