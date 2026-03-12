# Chat UIKit

TUIKit is a UI component library built on the Chat SDK. It enables rapid implementation of chat, conversation, search, relationship chain, and group management features through ready-to-use UI components. Message sending and receiving are handled by the TUIChat component. This guide explains how to quickly integrate TUIKit and implement its core features.

> **Noteï¼**This demo uses TRTC's emoji pack with restricted licensing.**Commercial Usage Options****Option A: Keep Our Emoji (Recommended)** Upgrade to [Chat Pro Plus or Enterprise Plan](https://console.trtc.io/subscription/buy/chat?packType=pro) and use our emoji pack at no additional cost.**Option B: Use Your Own**Replace default emoji with your own custom designs, or use emoji packs with proper commercial licensing.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/005a2031cb3911f0a7775254005ef0f7.png)

## Prerequisites

- Flutter version >= 3.29.0, Dart version >= 3.7.0.
- Android Studio 2022.3.1 or later, Android Gradle plugin version 7.3.1 or above.
- Xcode 12.0 or later.
- A valid Tencent Cloud account and Chat Application. Refer to [Enable the Service](https://trtc.io/zh/document/45907?product=chat&menulabel=uikit&platform=flutter) to obtain the following information from the Console:
  - `SDKAppID`: The unique identifier for your Chat Application.
  - `SDKSecretKey`: The secret key for your Application.

> **Version Compatibility Notice:**To ensure a stable build environment, strictly follow official compatibility requirements:For Gradle, Android Gradle Plugin, JDK, and Android Studio compatibility, refer to the Android official documentation: [Release Notes](https://developer.android.com/build/releases/gradle-plugin?hl=en#updating-gradle).For Kotlin, Android Gradle Plugin, and Gradle version mapping, refer to the Kotlin official documentation: [Kotlin-Gradle Plugin Compatibility](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin).If Android Studio installs with a higher default JDK version, compilation may fail. We recommend using JDK 17. See: [Switching Java Versions](https://developer.android.com/build/jdks#kts)We recommend selecting a version combination that matches your project requirements exactly, following the guidelines above.

## Integrate TUIKit

1. If you don't have a Flutter app, refer to the [Flutter documentation](https://docs.flutter.dev/get-started/codelab) to quickly create a Flutter application. If you already have a Flutter app, skip this step.
2. Add the following dependencies to your project's root `pubspec.yaml` file:

```
tencent_cloud_chat_common: ^4.1.0+1tencent_cloud_chat_conversation: ^4.1.0tencent_cloud_chat_message: ^4.1.0+3tencent_cloud_chat_contact: ^4.1.0tencent_cloud_chat_sticker: ^4.1.0tencent_cloud_chat_message_reaction: ^4.1.0tencent_cloud_chat_text_translate: ^4.1.0tencent_cloud_chat_sound_to_text: ^4.1.0
```

3. Configure Permissions

TUIKit requires camera, photo library, audio recording, and network permissions. You must manually declare these permissions in your native files to enable related features.

Android

iOS

Open `android/app/src/main/AndroidManifest.xml` file, and add the following permissions:

```
<uses-permission android:name="android.permission.RECORD_AUDIO" /><uses-permission    android:name="android.permission.READ_EXTERNAL_STORAGE"    android:maxSdkVersion="32" /><uses-permission android:name="android.permission.READ_MEDIA_IMAGES" /><!-- Compatibility for Android13 --><uses-permission android:name="android.permission.MANAGE_EXTERNAL_STORAGE" />
```

1. Open `ios/Podfile`. Add the following permissions:

```
post_install do |installer|  installer.pods_project.targets.each do |target|    flutter_additional_ios_build_settings(target)    target.build_configurations.each do |config|                  config.build_settings['EXCLUDED_ARCHS[sdk=iphonesimulator*]'] = 'arm64'                         config.build_settings['ENABLE_BITCODE'] = 'NO'                  config.build_settings["ONLY_ACTIVE_ARCH"] = "NO"            end    target.build_configurations.each do |config|          config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [            '$(inherited)',            'PERMISSION_MICROPHONE=1',            'PERMISSION_CAMERA=1',            'PERMISSION_PHOTOS=1',          ]        end  endend
```

2. Open `ios/Runner/info.plist` and add permission description keys:

```
<key>NSCameraUsageDescription</key><string>Our app requires access to your camera to enable video calling and capturing photos or videos to share in your conversations.</string><key>NSMicrophoneUsageDescription</key><string>Our app requires access to your microphone to enable voice and video calling features.</string><key>NSPhotoLibraryUsageDescription</key><string>Our app requires access to your photo library to enable sharing photos, videos, and files in your conversations.</string>
```

At this point, you have successfully integrated TUIKit into your project. To continue building chat, conversation, and other basic interfaces, refer to the [Demo Example](https://trtc.io/zh/document/45907?product=chat&menulabel=uikit&platform=flutter).

## FAQs

### Android Error: Unsupported class file major version 65

**Cause:**

This error indicates that your project uses an outdated Gradle version or your system has a Java version higher than what the project supports. (Version 65 corresponds to Java 21; each Java version has a unique class file version number.)

**Solution:**

Use JDK 17. See: [Switching Java Versions](https://developer.android.com/build/jdks#kts).


---
*Source: [https://trtc.io/document/58585](https://trtc.io/document/58585)*
