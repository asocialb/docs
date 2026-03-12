# Live Comment Input

## Component Overview

`Message Sending Component` allows users to input emojis and text messages in the bullet screen and send the message to the live streaming room. Users in the live streaming room can receive the message through the `Live Streaming Rendering Component` and display it on the screen, thereby enhancing the fun of the live stream and making the interaction experience more enjoyable and vivid.

Android

iOS

Flutter

`BarrageInputView`: Message Sending Component that allows users to input emojis and text messages in the barrage and send the message to the live streaming room.

`BarrageInputView`: `Message Sending Component`, which allows users to input emojis and text messages in the barrage and send the message to the live streaming room.

`BarrageSendWidget`: `Message Sending Component`, which enables users to input emojis and text messages in the barrage and send the message to the live streaming room.

Rendering display:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4182e6424d711f0948f52540099c741.png)

> **Notes:**Support switching between **system keyboard** and **emoji keyboard**.To respect emoji design copyright, large emoji element slicing is not included in the TUILiveKit project. Before official commercial launch, please replace it with other emoji packs designed or owned by yourself. The default **little yellow face emoji pack copyright belongs to Tencent Cloud**, and it can be licensed for a fee. If you need to obtain authorization, you can [submit a ticket](https://console.tencentcloud.com/workorder/category) to contact us.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c37b7d4624d711f0b47352540044a08e.png)

## Component Integration

Android

iOS

Flutter

**step 1:Download the TUILiveKit component**

Clone/download the code from [GitHub](https://github.com/tencentyun/TUILiveRoom), then copy the tuilivekit subdirectory under the Android directory to the same-level directory as your app in the current project, as shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5b3d40926b7a11f09cbf525400454e06.png)

**step 2:Project Configuration**

1. Add the jitpack repository address in the `settings.gradle.kts (or settings.gradle)` file in the project root directory: add the jitpack repository dependency (to download the SVGAPlayer third-party library for playing gift svg animations).

settings.gradle.kts

settings.gradle

```
dependencyResolutionManagement {    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)    repositories {        google()        mavenCentral()        // Add jitpack repository url        maven { url = uri("https://jitpack.io") }    }}
```

```
dependencyResolutionManagement {    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)    repositories {        google()        mavenCentral()        // Add jitpack repository url        maven { url 'https://jitpack.io' }    }}
```

2. Add the following code in the `settings.gradle.kts (or settings.gradle)` file in the project root directory. It enables importing the downloaded tuilivekit component into your current project:

settings.gradle.kts

settings.gradle

```
include(":tuilivekit")
```

```
include ':tuilivekit'
```

3. Locate the `build.gradle.kts (or build.gradle)` file under the app directory and add the following code in it. It enables declaring the current app's dependency on the newly joined tuilivekit component:

build.gradle.kts

build.gradle

```
api(project(":tuilivekit"))
```

```
api project(':tuilivekit')
```

> **Note:**Note: The TUILiveKit project internally depends on `TRTC SDK`, `IM SDK`, `tuiroomengine`, and the public library `tuicore` by default. Developers do not need to separately configure them. If needed, just modify the `tuilivekit/build.gradle` file to upgrade.

4. Since we use Java reflection features internally in the SDK, some classes in the SDK need to be added to the non-obfuscation list. Therefore, you need to add the following code in the `proguard-rules.pro` file:

```
-keep class com.tencent.** { *; }-keep class com.trtc.uikit.livekit.livestreamcore.** { *; }-keep class com.trtc.uikit.livekit.component.gift.store.model.** { *; }-keep class com.squareup.wire.** { *; }-keep class com.opensource.svgaplayer.proto.** { *; }-keep class com.tcmediax.** { *; }-keep class com.tencent.** { *; }-keep class com.tencent.xmagic.** { *; }-keep class androidx.exifinterface.** {*;}-keep class com.google.gson.** { *;}# Tencent Effect SDK - beauty-keep class com.tencent.xmagic.** { *;}-keep class org.light.** { *;}-keep class org.libpag.** { *;}-keep class org.extra.** { *;}-keep class com.gyailib.**{ *;}-keep class com.tencent.cloud.iai.lib.** { *;}-keep class com.tencent.beacon.** { *;}-keep class com.tencent.qimei.** { *;}-keep class androidx.exifinterface.** { *;}
```

5. Find the `AndroidManifest.xml` file under the app directory, add tools:replace="android:allowBackup" and android:allowBackup="false" in the application node, overwrite the setting within component, and use your own setting.

```
  // app/src/main/AndroidManifest.xml    <application    ...      // add the following configuration to overwrite the configuration in the dependent sdk    android:allowBackup="false"    tools:replace="android:allowBackup">
```

Import components using CocoaPods. The specific steps to import components are as follows:

1. You need to download the `Barrage` folder from [GitHub](https://github.com/Tencent-RTC/TUILiveKit/tree/main/iOS) to your local system.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bb8e60ca2b3c11f0948f52540099c741.png)

2. Add `pod 'TUIBarrage'` dependency in the `Podfile` file of your project.

Swift

```
target 'xxxx' do  ...  ...  pod 'TUIBarrage', :path => '../Component/Barrage/TUIBarrage.podspec'   // The path is the relative path between your Podfile file and TUIBarrage.Podspec file.end
```

If you don't have a `Podfile` file, first use the terminal to `cd` into the `xxxx.xcodeproj` directory, then create it with the following command:

```
pod init
```

3. In the terminal, first `cd` to the `Podfile` directory, then execute the following commands to install components.

```
pod install
```

4. Any issues you encounter during integration and use, feel free to [give feedback](https://github.com/Tencent-RTC/TUILiveKit/issues).
1. In the dependencies node of the pubspec.yaml file in the project engineering, add a dependency on **barrage**.

```
dependencies:  flutter:    sdk: flutter  flutter_localizations:    sdk: flutter  intl: ^0.19.0  # Add barrage dependency  live_uikit_barrage: ^1.0.0
```

1. Execute the
2. `flutter pub get` command.
3. Configure multilingual support. Add multilingual support for the **gift** component to the `localizationsDelegates` and `supportedLocales` properties of your application's `MaterialApp`.

```
MaterialApp(localizationsDelegates: const [  ...BarrageLocalizations.localizationsDelegates,], supportedLocales: const [  ...BarrageLocalizations.supportedLocales,], // ...);
```

## Component Usage

> **Notes:**Since the barrage component requires live room information parameters, it is necessary to load the barrage component after **Audience Entering the Live Room** or **Anchor Create Live Room**.

### Integration of Sending Barrage Message Component

Android

iOS

Flutter

At the position to send barrage, create `BarrageInputView`. Click to bring up the input interface.

```
BarrageInputView barrageInputView = new BarrageInputView(mContext);barrageInputView.init(roomId);mBarrageInputContainer.addView(barrageInputView);
```

At the position to send barrage, create `BarrageInputView`. Click to bring up the input interface.

```
BarrageInputView
```

> **Notes:**You can only send danmaku into the room successfully after successfully entering the room.

Construct the BarrageSendController and BarrageSendWidget objects where you need to connect to send barrage messages. Add the constructed BarrageSendWidget object to your Widget tree. Sample code:

```
BarrageSendController _sendController = BarrageSendController(                roomId: "liveRoomId",             /// Replace with your liveRoomId                ownerId:  "liveOwnerId",          /// Replace liveOwnerId with your live stream host ID                 selfUserId: "selfUserId",         /// Replace selfUserId with your currently logged-in user ID                selfName: "selfUserName";         /// Replace selfUserName with your currently logged-in user nicknameBarrageSendWidget(controller: _sendController);
```


---
*Source: [https://trtc.io/document/69848](https://trtc.io/document/69848)*
