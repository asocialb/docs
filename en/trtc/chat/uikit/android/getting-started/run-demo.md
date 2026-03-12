# Run Demo

This guide provides step-by-step instructions to help you quickly get started with the Chat Demo and explore features including text, voice, and video messaging. After setup, the Demo app interface appears as shown below:

| Login Page | Conversation List | Chat Page |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2ab94505b55a11f0b4c35254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2acea595b55a11f085a55254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2ac3940eb55a11f0a808525400bf7822.png) |

## Demo App

You can go to [Free Demo](https://trtc.io/document/35076#42b9c204-f927-4326-9af6-370e511773f3) to download the Chat Demo app to explore the full range of instant messaging features.

## Prerequisites

### Enable the Service

1. Log in to the [Console](https://console.trtc.io/). If you already have an Application, save your `SDKAppID` and `SDKSecretKey` and skip to [Environment Preparation](#1c7f5d4b-cacf-4b54-9cbb-0fbf990847f5).
2. Click `Create Application`, enter your Application name, select **Chat** as the product, choose your region, and click `Create` to add the Application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b6c10ebb55a11f0b4c35254001c06ec.png)

3. After creation, you can view your Applicationâs `SDKAppID` and `SDKSecretKey` on the Console Overview page. You will need this information to run the Demo.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b60badeb55a11f09a6b525400454e06.png)

> **Forbiddenï¼**Secure your `SDKSecretKey` to protect your Application from unauthorized access.

### Environment Preparation

Before you begin, ensure you meet the following requirements:

- Android Studio 2022.3.1 or later
- A physical device or emulator running Android 5.0 or higher
- A valid Chat Application. Refer to the âEnable the Serviceâ section above to obtain or create one.

> **Version Compatibility Note:**To ensure a stable build environment, strictly follow official compatibility requirements:For compatibility between Gradle, Android Gradle Plugin, JDK, and Android Studio, see the official Android documentation: [Version Notes](https://developer.android.com/build/releases/gradle-plugin#updating-gradle)For version mapping between Kotlin, Android Gradle Plugin, and Gradle, see the official Kotlin documentation: [Kotlin-Gradle Plugin Compatibility](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin)We recommend selecting a version combination that matches your project requirements based on the above guidelines.

## Instructions

### Get the Demo

> **Noteï¼**This demo uses TRTC's emoji pack with restricted licensing.**Commercial Usage Options****Option A: Keep Our Emoji (Recommended)**Upgrade to [Chat Pro Plus or Enterprise Plan](https://console.trtc.io/subscription/buy/chat?packType=pro) and use our emoji pack at no additional cost.**Option B: Use Your Own**Replace the default emoji with your own custom designs, or use emoji packs with proper commercial licensing.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/838c3fd6b88211f0a808525400bf7822.png)

1. Download the [Android Chat UIKit project](https://github.com/TencentCloud/chat-uikit-android).
2. Open the project directory in your terminal and locate the `GenerateTestUserSig.java` file at `Demo/app/src/main/java/com/tencent/qcloud/tim/demo/signature/GenerateTestUserSig.java`.
3. Configure the following parameters in the `GenerateTestUserSig.java` file:
  - SDKAPPID: Set this to your actual SDKAppID obtained above.
  - SECRETKEY: Set this to your actual SecretKey obtained.

> **Forbiddenï¼**In this Demo, authentication is performed by configuring the `SECRETKEY` in the client code. However, the `SECRETKEY` can be easily extracted through reverse engineering. If leaked, attackers could misuse your Tencent Cloud resources. This approach is suitable only for local Demo trials and feature debugging.For production environments, we strongly recommend generating the UserSig on your server. When your app needs a UserSig, it should request a dynamic UserSig from your business server for authentication. For details, see [Generating UserSig on the Server](https://intl.cloud.tencent.com/document/product/1047/34385).

### Build and Run the Demo

Open Android Studio and launch the Demo directory.

> **Note:**The first time you import the Demo project, dependencies will be downloaded automatically. Wait until the download and synchronization are complete before running the project.

To run on an Android device:

1. Connect your Android device to your computer, enable Developer Mode and USB Debugging on the device, and set USB mode to File Transfer if required.
2. Set the Gradle JDK:
  - In Android Studio, go to **Settings** > **Build, Execution, Deployment** > **Build Tools** > **Gradle**.
  - In the **Gradle JDK** dropdown, select **JDK 17** (install JDK 17 if it is not available). Then, run **File > Sync Project with Gradle Files** to verify the configuration.
3. In the Android Studio toolbar, select your test Android device from the **Running devices** dropdown.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2aea5b88b55a11f0b4c35254001c06ec.png)

4. Click the **Run** button to build the project. Once the build succeeds, the Tencent Cloud IM App will be installed automatically on your device.
5. Open the app and enter any userID to create and log in to a user account.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b124b6ab55a11f09a6b525400454e06.png)

## Experience Basic Features

âTo experience the basic features, follow these steps after running the demo successfully.â

### Create a User Account

To create a user account, choose one of the following methods:

Client Registration

Console Registration

Enter a userID in the Demo and log in.

1. Click to enter the Application you created. In the left sidebar, click the Chat product entry to enter.
2. On the Chat product subpage, click `Users` to open the user management page.
3. Click `Create account` to open the account creation dialog. For regular users, select the `General` type. While `Nickname` is optional, we recommend setting it. If displaying `userID` is not ideal in your UI, use `Nickname` to distinguish users.

Illustration:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/30ca9a99b55b11f0a808525400bf7822.png)

> **Note:**Messaging requires at least two users. Create at least two accounts at this stage, and record their userIDs for the next steps.

### Add Contacts

To add contacts:

1. On the Contacts page, click the `+` button in the upper right corner and select `Add to Contacts` from the submenu.
2. Enter a valid userID to search for the user. If you created accounts in the Console, obtain valid userIDs from the Consoleâs `Account Management` page. Path:**Applications**>**Your App**>**Chat**>**Users**> **Account Management**.
3. Add a user as a contact.

| Tap `Add to Contacts` | Search for User | Send Contact Request |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b575b84b55a11f085a55254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b16c558b55a11f0b4c35254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b52ceadb55a11f085a55254007c27c5.png) |

After adding a user successfully, the contact list displays the user you just added:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b4be4d9b55a11f0a5e052540099c741.png)

### Send Messages

Select a user, click Message to enter the chat interface:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b6e8855b55a11f0a808525400bf7822.png)

You can now exchange text, voice, images, and audio/video calls with this user:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b7c6974b55a11f0a5e052540099c741.png)

## Contact Us

If you have any questions or suggestions, feel free to join our [Telegram](https://t.me/tencent_imsdk) or [WhatsApp](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik) community, or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/45914](https://trtc.io/document/45914)*
