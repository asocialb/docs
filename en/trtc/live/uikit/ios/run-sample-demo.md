# Run Sample Demo

This guide walks you through getting started with the `TUILiveKit` iOS Demo in just 10 minutes. Experience a fully featured UI for video live streaming and voice chat room scenarios.

## Quick Experience

You can directly experience all **Live** features using the following methods.

## Prerequisites

### Enable the Service

Refer to [Enable the Service](https://www.tencentcloud.com/document/product/647/60033) to obtain a TUILiveKit trial version. Then, go to [the Console](https://console.trtc.io/app) for application management, and get the following:

- `SDKAppID`: Application identifier (required). Tencent Cloud uses `SDKAppId` for billing and details.
- `SDKSecretKey`: Application secret key, used to initialize the configuration file with secret information.

### Environment Preparation

Ensure your development environment meets these requirements:

- **Xcode**: Xcode 15 or later
- **iOS System**: Devices running iOS 13.0 or later
- **CocoaPods**: CocoaPods must be installed. If not, refer to the [CocoaPods Official Installation Guide](https://guides.cocoapods.org/using/getting-started.html) or run:
  - Install CocoaPods via gem:

```
sudo gem install cocoapods
```

> **Tipï¼**During sudo gem install cocoapods, you may be prompted for your computer password. Enter your administrator password as instructed.

## Instructions

### Get the Demo

1. **Download the source code**: Download the [TUIKit_iOS](https://github.com/Tencent-RTC/TUIKit_iOS) source code from GitHub, or run:

```
git clone https://github.com/Tencent-RTC/TUIKit_iOS.git
```

2. **Install dependencies**: In your `terminal`, navigate to the directory containing the `Podfile` and run:

```
# The Demo project's Podfile is located in the application directorycd application/# Install dependenciespod install --repo-update
```

3. **After installation**, you will see a `Pods` directory and an `App-UIKit.xcworkspace` file in your project directory. Double-click `App-UIKit.xcworkspace` to open the project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2530c0c5bf7b11f0b4c35254001c06ec.png)

### Setup

1. **Configure**`SDKAppID`**and**`SDKSecretKey`: In the `App-UIKit.xcworkspace` project, enter your `SDKAppID` and `SDKSecretKey` in the `Debug/GenerateTestUserSig.swift` file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5acccb7fbf7b11f08863525400e889b2.png)

> **Noteï¼**In this Demo, authentication is performed by configuring `SecretKey` in the client code. `SecretKey` can be reverse-engineered; if leaked, attackers can steal your Tencent Cloud traffic. This method is for local Demo testing and debugging only.For production, generate UserSig on your server. When needed, your app should request a dynamic UserSig from your business server. See [Generating UserSig on the Server](https://www.tencentcloud.com/document/product/647/35166) for details.

2. **Configure Apple Developer Signing**: In the projectâs **TARGETS** under the **Signing & Capabilities** tab, enable **Automatically** **manage signing** and set your **Apple Developer account** and Bundle Identifier.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6efb9271bf9a11f0a5e052540099c741.png)

### Build and Run the Demo

Live streaming scenarios require camera and microphone access. Use a physical device for debugging and running the Demo.

1. Connect your iOS device to your computer. On the device, go to `Settings > Privacy & Security > Developer Mode` and enable Developer Mode.
2. In Xcode, select your device from the **iOS Device** dropdown.
3. Click the Run button to deploy the app to your device.

> **Note:**For a complete live streaming workflow, run the Demo on **two devices** and log in with **two different users**(e.g., one as the host and one as the audience).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3c9e53e8bf9a11f08863525400e889b2.png)

### Experience the Basic Features

#### 1. Login & Registration

Enter your `ID` in the `UserID` field. If the `UserID` has not been used before, youâll be redirected to the registration page to set your avatar and nickname.

| **Anchorï¼mikeï¼** |  | **Audieceï¼vinceï¼** |  |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/781570c3bf9111f0a5e052540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77aae6dbbf9111f0b9945254005ef0f7.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/784a90f9bf9111f08863525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7842f6babf9111f085a55254007c27c5.png) |

> **Note:**Do not use simple UserIDs such as "1", "123", or "111". TRTC does not support multi-end login for the same UserID, and these simple UserIDs are likely to be used by others during collaborative development, which can cause login failures. Use distinctive UserIDs during debugging.

#### 2. Video Live Streaming

Click `Live > Video Live` to start a video live streaming session.

| **Live Streaming List** | **Host Preview Before Going Live** | **Host Starts Video Live Streaming** | **Audience Watches Live Stream** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8f909f5bf7611f0b4c35254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e5298586bf7611f0a6c652540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fc7ac332bf7611f09a6b525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/02c2ffc9bf7711f08863525400e889b2.png) |

#### 3. Voice Chat Room

Click `Live > Voice Room` to start a voice chat session.

| **Live Streaming List** | **Host Preview Before Going Live** | **Host Starts Voice Chat Live** | **Audience Joins Voice Chat Room** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0334f99abef911f085a55254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/033eba1fbef911f0a6c652540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/034bdf67bef911f08863525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/035934d9bef911f0b4c35254001c06ec.png) |

## Next Steps

After running the Demo, refer to the following integration guides to add these features to your own project:

|  | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Video Live Streaming** | Supports ultra-low latency HD streaming, multi-user co-hosting/PK, real-time beauty filters, bullet comments, and gift interactionsâenabling you to build interactive video live streaming scenarios. | [Integration Guide](https://www.tencentcloud.com/document/product/647/72224) |
| **Voice Chat Room** | Delivers ultra-clear audio quality, supports multi-user co-hosting, seat management, and real-time text chatâideal for KTV, social, or gaming-themed rooms. | [Integration Guide](https://www.tencentcloud.com/document/product/647/60334) |

## FAQs

### Encounter signature errors or login failures when running the Demo

Verify that the `SDKAppID` and `SDKSecretKey` in `Debug/GenerateTestUserSig.swift` are correct and match those from the [Tencent Cloud Console Application Management](https://console.tencentcloud.com/trtc) page.

### Encounter error code "-3301" with the message "Services are not available in your region" after entering the room

If you receive this error code, [contact us](https://trtc.io/contact) for support.

## Contact Us

If you have any questions or suggestions during integration or usage, join our [Telegram technical group](https://t.me/+EPk6TMZEZMM5OGY1?s_url=https%3A%2F%2Ftrtc.io)or [contact us](https://trtc.io/contact)for support.


---
*Source: [https://trtc.io/document/60455](https://trtc.io/document/60455)*
