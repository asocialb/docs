# Run Demo

This guide provides step-by-step instructions to help you quickly get started with the Chat Demo and experience features such as text, voice, and video messaging. After setup, the application interface appears as shown below:

| Login Page | Conversation List Page | Chat Page |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7f3fb1f7a4ee11f0b1565254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8115fa3ca4ee11f09936525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/82bc5a9ba4ee11f0b1565254001c06ec.png) |

## Demo app

You can go to [Free Demo](https://trtc.io/document/35076#42b9c204-f927-4326-9af6-370e511773f3) to download the Chat Demo app to explore the full range of instant messaging features.

## Prerequisites

### Enable the Service

1. Log in to the [Console](https://console.trtc.io/). If you already have an Application, save your `SDKAppID` and `SDKSecretKey` and skip to [Environment Preparation](#env).
2. Click `Create Application`, enter your Application name, select the product to **Chat** and choose your region, and click `Create` to add the Application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8f0d0930ab0511f0b08552540044a08e.png)

3. After creation, you can see your Applicationâs `SDKAppID` and `SDKSecretKey` on the Console Overview page. You will need this information to run the Demo.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8ed5f433ab0511f09710525400e889b2.png)

> **Forbiddenï¼**Secure your `SDKSecretKey` to protect your Application from unauthorized access.

### Environment Preparation

Before you begin, ensure the following requirements are met:

- Xcode 10 or later
- iOS 9.0 or later (physical device or simulator)
- CocoaPods 1.7.5 or later. If not installed, refer to [CocoaPods Guides - Getting Started](https://guides.cocoapods.org/using/getting-started.html#getting-started).

## Instructions

### Get the Demo

> **Noteï¼**This demo uses TRTC's emoji pack with restricted licensing.**Commercial Usage Options****Option A: Keep Our Emoji (Recommended)** Upgrade to [Chat Pro Plus or Enterprise Plan](https://console.trtc.io/subscription/buy/chat?packType=pro) and use our emoji pack at no additional cost.**Option B: Use Your Own**Replace default emoji with your own custom designs, or use emoji packs with proper commercial licensing.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cf33bf6cab0511f09b75525400bf7822.png)

Get the Swift Demo

Get the Objective-C Demo

1. Download the [Swift Chat UIKit project](https://github.com/Tencent-RTC/Chat_UIKit).
2. In your terminal, navigate to the project directory and locate the `GenerateTestUserSig.swift` file at: Chat_UIKit/Swift/TUIKitDemo/TUIKitDemo/Private/GenerateTestUserSig.swift
3. Configure the following parameters in `GenerateTestUserSig.swift`:
- `public_SDKAPPID`: The SDKAppID you obtained above.
- `public_SECRETKEY`: The SDKSecretKey you obtained above.
1. Download the [iOS Demo project](https://github.com/TencentCloud/chat-uikit-ios) from GitHub.
2. In your terminal, navigate to the project directory and locate the `GenerateTestUserSig.h` file at: `chat-uikit-ios-main/Demo/TUIKitDemo/Private/GenerateTestUserSig.h`
3. Configure the following parameters:
- SDKAPPID: The SDKAppID you obtained above.
- SECRETKEY: The SDKSecretKey you obtained above.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f640557dab0511f0b5345254005ef0f7.png)

> **Forbiddenï¼**In this Demo, authentication uses the `SDKSecretKey` configured in the client code. The `SECRETKEY` can be reverse-engineered and compromised. If leaked, attackers can steal your TRTC traffic. This method is for local Demo testing and feature debugging only.In production, generate a `UserSig` on the server side. When your App needs a `UserSig`, request a dynamic `UserSig` from your server for authentication. See [Generate UserSig on the Server](https://intl.cloud.tencent.com/document/product/1047/34385) for details.

### Setup the Demo

Run the following command in your terminal to install dependencies:

Swift

Objective-C

```
# First cd into your downloaded project directory, then cd into the TUIKitDemo directorycd Swift/TUIKitDemopod install
```

```
# First cd into your downloaded project directory, then cd into the TUIKitDemo directorycd iOS/TUIKitDemopod install
```

> **Noteï¼**If installation fails, run `pod repo update` to update your local CocoaPods repository.

### Build and Run the Demo

> **Noteï¼**The Demo integrates audio and video call features by default. The audio/video SDK does not currently support simulators. Use a physical device to debug or run the Demo.

- For the Swift project, navigate to the `Swift/TUIKitDemo` folder and open `TUIKitDemo.xcworkspace` to build and run.
- For the Objective-C project, navigate to the `chat-uikit-ios-main/Demo` folder and open `TUIKitDemo.xcworkspace` to build and run.

For example, on an iOS device:

1. Connect your iOS device to your computer. On the device, go to **Settings** > **Privacy & Security** > **Developer Mode** and enable Developer Mode.
2. In Xcode, select your test iOS device from the **iOS Device** dropdown at the top.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8e777c29ab0511f0b5345254005ef0f7.png)

3. In the project **TARGETS** > **Signing & Capabilities** section, check **Automatically manage signing**, then configure your Apple developer account and Bundle Identifier for each Target. If you have not signed in to your Apple ID in Xcode, go to **Xcode** > **Preferences** > **Accounts** to add your developer account or Apple ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8e752bebab0511f0a0a052540099c741.png)

4. Click the run button to build. After a successful build, the TUIKitDemo is automatically installed on your device.
5. Open the App and enter any userid to create and log in to a user account.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8e9881c0ab0511f0a68e5254001c06ec.png)

## Experience Basic Features

After running the Demo, you can test the basic features of Chat.

### Create a User Account

First, create a user account. You can register directly in the Demo client or create an account in the Console. Choose one of the following methods:

Client Registration

Console Registration

Enter an userID in the Demo and log in to the Demo app.

Follow these steps to create a user account:

1. Click to enter the Application you created above. In the left sidebar, locate the Chat product entry and click to enter.
2. On the Chat product subpage, click `Users` to access the user management page.
3. Click `Create account`. For regular members, select the `General` type. While `Nickname` is optional, we recommend setting it. If the interface does not display `userID` clearly, use `Nickname` to distinguish users.

As shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9a793040ab0611f0b5345254005ef0f7.png)

> **Tips:**Sending messages requires at least two users. Create at least two accounts at this stage and record their userIDs for later steps.

### Add Contacts

To add contacts:

1. On the Contacts page, click the `+` button in the upper right corner and select `Add to Contacts` from the submenu.
2. Enter a valid userID to search for the user. If you created accounts in the Console, obtain valid userIDs from the Consoleâs `Account Management` page. Path: Applications > Your App > Chat > Users > Account Management.
3. Add a user as a contact.

| Click Add to Contacts | Search for User | Send Add Contact Request |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e87198f75a0c11ef8f105254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e8676f635a0c11ef8357525400bdab9d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e8696a0c5a0c11efb927525400fdb830.png) |

After adding a user successfully, the contact list displays the user you just added:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8eacb0a5ab0511f0a0a052540099c741.png)

### Send Messages

Select a user, click **Message**, and enter the message interface:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8ebb5942ab0511f0b0045254007c27c5.png)

You can now send text, voice, image, and video call messages to this user:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8edd23a8ab0511f0b08552540044a08e.png)

## FAQ

#### 1. How to fix "pod does not exist" or "pod version less than 1.7.5" error during pod install?

Run the following commands to install the latest pod.

```
# 1. Install pod sudo gem install cocoapods -n /usr/local/bin# If you have multiple Xcode versions installed, use the following command to select the Xcode version (generally choose the latest).sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer# 2. Update the local pod repositorypod setup
```

#### 2. TUICore version incompatibility

When using CocoaPods to get the Demo, if the TUICore version locked in the `Podfile.lock` file is incompatible with the plugin dependency, you may encounter the following error: `CocoaPods could not find compatible versions for pod "TUICore"`

Follow these steps to solve this:

1. In your Demo project root directory, run the following command to delete the `Podfile.lock` file:

```
rm Podfile.lock
```

2. Run the following command to update the local code repository:

```
pod repo update
```

3. Run the following command to reinstall:

```
pod update
```

After completing these steps, a new `Podfile.lock` file will be generated and dependencies installed successfully.

#### 3. Untrusted Developer

If you are debugging on a physical device and see an "Untrusted Developer" prompt after a successful build, tap Cancel to close the prompt. Then, on your iOS device, go to **Settings** > **General** > **VPN & Device Management**, select the developer app, and trust the developer. After that, open the Demo App to continue.

## Contact Us

If you have any questions or suggestions during integration or usage, [Contact Us](https://trtc.io/contact) for support and feedback.


---
*Source: [https://trtc.io/document/45913](https://trtc.io/document/45913)*
