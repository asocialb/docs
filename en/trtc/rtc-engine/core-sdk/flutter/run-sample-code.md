# Run Sample Code

This document describes how to quickly run the demo for the TRTC Flutter SDK.

> **Note**Currently, screen sharing and device selection are not supported on Windows or macOS.

## Environment Requirements

- Flutter 2.0 or later.
- **Developing for Android:**
  - Android Studio 3.5 or later.
  - Devices with Android 4.1 or later.
- **Developing for iOS and macOS:**
  - Xcode 11.0 or later.
  - OS X 10.11 or later.
  - A valid developer signature for your project.
- **Developing for Windows:**
  - OS: Windows 7 SP1 or later (64-bit based on x86-64).
  - Disk space: At least 1.64 GB of space after the IDE and relevant tools are installed.
  - [Visual Studio 2019](https://visualstudio.microsoft.com/zh-hans/downloads/).

## Prerequisites

You have [signed up for a Tencent Cloud account](https://trtc.io/register?s_url=https://console.trtc.io).

## Directions

### Step 1. Create an application

1. Log in to the [TRTC console overview page](https://console.trtc.io/), click **Create Application**.
2. In the popup page, select RTC Engine, enter the application name, and then click **Create**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/63a1c7700ddd11efaa2e525400493f3c.png)

### Step 2. Get your SDKAppId and SecretKey

After your application created, you can get your `SDKAppID` and `SDKSecretKey` on Basic informaction. `SDKAppID` and `SDKSecretKey` is needed for running demo.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1eb9f447b5d411eeb2a1525400170219.png)

### Step 3. Download the sample code

1.Go to [GitHub](https://github.com/LiteAVSDK/TRTC_Flutter/tree/master/TRTC-Simple-Demo) to download the SDK and demo source code.

```
git clone https://github.com/LiteAVSDK/TRTC_Flutter.git
```

2.The steps to import SDK can refer to [Flutter SDK import](https://trtc.io/document/35098).

### Step 4. Configure the project

Open the file downloaded previously, find and open `/lib/debug/GenerateTestUserSig.dart`, and set the following parameters:

- `SDKAPPID`: A placeholder by default. Set it to the actual `SDKAppID`.
- `SDKSECRETKEY`: A placeholder by default. Set it to the actual key.

> **Note**The method for generating UserSig described in this document involves configuring `SDKSECRETKEY` in the client code. In this method, `SDKSECRETKEY` may be easily decompiled and reversed, and if your key is disclosed, attackers can steal your Tencent Cloud traffic. Therefore, this method is only suitable for the local execution and debugging of TRTC-Simple-Demo.The best practice is to integrate the calculation code of UserSig into your server and provide an application-oriented API. When UserSig is needed, your application can send a request to your server for a dynamic UserSig. For more information, see [How do I calculate UserSig during production?](https://www.tencentcloud.com/zh/document/product/1047/34385).

### Step 5. Compile and run the demo

1. Execute `flutter pub get`.
2. Build and run the project.

#### Android

1. Execute `flutter run`.
2. Open the demo project with Android Studio (3.5 or later), and run the project.

#### iOS

1. Execute `cd ios`.
2. Execute `pod install`.
3. Open `/ios` in the source code directory with Xcode (11.0 or later). Compile and run the demo project.

#### Windows

1. Execute `flutter config --enable-windows-desktop`.
2. Execute `flutter run -d windows`.

#### macOS

1. Execute `flutter config --enable-macos-desktop`.
2. Execute `cd macos`.
3. Execute `pod install`.
4. Execute `flutter run -d macos`.

## FAQs

### How do I view TRTC logs?

TRTC logs are compressed and encrypted by default (XLOG format). You can find them at the following paths:

- **iOS**: `Documents/log` of the application sandbox
- **Android**:
  - v6.7 or earlier: `/sdcard/log/tencent/liteav`
  - v6.8 or later: `/sdcard/Android/data/package name/files/log/tencent/liteav/`

### What should I do if videos show on Android but not on iOS?

Make sure that in `info.plist` of your project, the value of `io.flutter.embedded_views_preview` is `YES`.

### What should I do if the "Manifest merge failed" error occurs in Android Studio?

Open `/example/android/app/src/main/AndroidManifest.xml`.

1. Add `xmlns:tools="http://schemas.android.com/tools"` to `manifest`.
2. Add `tools:replace="android:label"` to `application`.
![Illustration](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e0d22b29662411ed83b6525400c56988.png)

> **Note**For more FAQs, see [Flutter](https://trtc.io/document/39242).


---
*Source: [https://trtc.io/document/39243](https://trtc.io/document/39243)*
