# Run Demo

This document provides step-by-step instructions to quickly set up and run the Chat Demo, allowing you to experience text, voice, and video messaging features. Once setup is complete, the demo will appear as shown in the screenshots below:

| Login Page | Conversation List Page | Chat Page |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b74c1f6f01b711f1b6b4525400370dda.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b76ff1e701b711f18ab45254001d6acc.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b76630c901b711f18ab45254001d6acc.png) |

## Quick Experience

Try the Chat Demo on multiple platforms here: [Demo Experience](https://trtc.io/document/35076#42b9c204-f927-4326-9af6-370e511773f3).

## Prerequisites

### Enable the Service

1. Log in to the [Console](https://trtc.io/login). If you already have an application, record its SDKAppID and SecretKey.
2. Click `Create Application`, enter your application name, select the product and region, then click `Create` to complete the process.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b83a230d01b711f18e6252540073fd3b.png)

3. After creation, view your application's `SDKAppID` and `SDKSecretKey` on the console overview page. You will need both to run the demo.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b7f3777401b711f191b4525400ecee81.png)

> **Noteï¼**Keep your SDKSecretKey secure to prevent unauthorized access.

### Environment Preparation

- Flutter >= 3.29.0, Dart >= 3.7.0
- Android Studio Ladybug | 2024.2.1 or later, Android Gradle plugin 7.3.1 or later, JDK 17.
- Xcode 12.0 or later

> **Version Compatibility Note****ï¼**To maintain a stable build environment, strictly follow official compatibility requirements:For Gradle, Android Gradle Plugin, JDK, and Android Studio compatibility, refer to the official Android documentation: [Version Notes](https://developer.android.com/build/releases/gradle-plugin#updating-gradle).For Kotlin, Android Gradle Plugin, and Gradle version mapping, refer to the official Kotlin documentation: [Kotlin-Gradle Plugin Compatibility](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin).Use JDK 17; other versions may cause build failures. See: [Java Version Switching](https://developer.android.com/build/jdks#kts).Choose a version combination that matches your project requirements according to the guidelines above.

## Instructions

### Get the Demo

> **Noteï¼**This demo uses TRTC's emoji pack with restricted licensing.**Commercial Usage Options****Option A: Keep Our Emoji (Recommended)** Upgrade to [Chat Pro Plus or Enterprise Plan](https://console.trtc.io/subscription/buy/chat?packType=pro) and use our emoji pack at no additional cost.**Option B: Use Your Own**Replace default emoji with your own custom designs, or use emoji packs with proper commercial licensing.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a6b2927601b811f1b5ce525400074c32.png)

1. Download the [Flutter Chat UIKit](https://github.com/Tencent-RTC/TUIKit_Flutter) project.
2. Open the downloaded `chat/demo` project in Android Studio: **Android Studio** > **File** > **Open** > select the demo root directory, and locate the `login_page` file at lib/login_page.dart.
3. Update the required parameters in the `login_page` file:
  - SDKAPPID: Enter the `SDKAppID` you obtained earlier.
  - SECRETKEY: Enter the SecretKey you obtained earlier.

> **Cautionï¼**In this Demo, authentication uses the `SDKSecretKey` configured in the client code. The `SECRETKEY` can be reverse-engineered and compromised. If leaked, attackers can steal your TRTC traffic. This method is for local Demo testing and feature debugging only.In production, generate a `UserSig` on the server side. When your App needs a `UserSig`, request a dynamic `UserSig` from your server for authentication. See [Generate UserSig on the Server](https://intl.cloud.tencent.com/document/product/1047/34385) for details.

### Build and Run the Demo

- Import the project into Android Studio and install the Flutter and Dart plugins.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b729402701b711f191b4525400ecee81.png)

- Run the following command in the project root directory to install dependencies.

```
flutter pub get
```

- To run on an Android device:
  - Connect your Android device to your computer, enable developer mode, turn on USB debugging, and select USB for file transfer (if applicable).
  - In Android Studio, select your test device from the **Running devices** dropdown at the top.
  - Click the run button to build the project. After a successful build, the Tencent Cloud Chat App will be installed automatically on your device.
  - Open the app and enter any UserID to create and log in to a user account.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b6ec823b01b711f198e252540097cba1.png)

  - For easier message testing, create two different user accounts, add each other as friends, and send messages to each other.

| Add Friends | Search Friends | New Friend in Contacts | Chat with Friends |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b7af797d01b711f1b5ce525400074c32.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b7aebab701b711f18e6252540073fd3b.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b7ce6a1e01b711f1b6b4525400370dda.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b7ef586601b711f18548525400380f7d.png) |

## FAQs

### iOS Pods Dependency Installation Issues

**Solution 1:** Manually delete the `ios/Pods` folder and `ios/Podfile.lock` file, then run the following commands to reinstall dependencies.

```
cd iossudo gem install ffipod install --repo-update
```

**Solution 2:** If you encounter errors after configuration and running, click **Product** > **Clean Build Folder** to clean the build artifacts, then rerun `pod install` or `flutter run`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b704b86f01b711f18e6252540073fd3b.png)

### Flutter Environment Issues

To verify your Flutter environment setup, run `flutter doctor`.

### Android Errors After Importing TUIKit in a Flutter Auto-generated Project

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b6e8f2db01b711f18e6252540073fd3b.png)

1. Open `android\\app\\src\\main\\AndroidManifest.xml` and add `xmlns:tools="http://schemas.android.com/tools"` / `android:label="@string/android_label"` and `tools:replace="android:label"` as shown below.

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="Replace with your Android package name" xmlns:tools="http://schemas.android.com/tools"> <application     android:label="@string/android_label"     tools:replace="android:label"     android:icon="@mipmap/ic_launcher" // Specify an icon path     android:usesCleartextTraffic="true"     android:requestLegacyExternalStorage="true">
```

2. Open `android\\app\\build.gradle` and add `minSdkVersion` and `targetSdkVersion` to the `defaultConfig` section.

```
defaultConfig {  applicationId "" // Replace with your Android package name  minSdkVersion 21  targetSdkVersion 30}
```

### Supported Data Centers for Speech-to-Text

Currently, Speech-to-Text is only available for SDKAppID in the China data center.

## Contact Us

If you have any questions or suggestions during integration or use, feel free to [Contact Us](https://trtc.io/contact) for feedback.


---
*Source: [https://trtc.io/document/45907](https://trtc.io/document/45907)*
