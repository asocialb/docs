# Audience List

## Component Overview

The audience list component mainly provides following features: display the real-time number of participants in the live broadcast, and show the online audience list in the live broadcast.

| **Audience List Component** | **Click Component to Display Online Audience Details Panel** | **Effect Display after Integration** |
| --- | --- | --- |
|  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9ab95e9624d711f0b0b1525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa2937be45d111f09bbe525400454e06.png) |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b1788b9245d111f0b0ce5254007c27c5.png) |

## Component Integration

Android

iOS

Flutter

**step 1:Download the TUILiveKit component**

Clone/download the code from [GitHub](https://github.com/tencentyun/TUILiveRoom), then copy the tuilivekit subdirectory under the Android directory to the same-level directory as your app in the current project, as shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/490bbd6f6b7a11f09dc95254007c27c5.png)

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

Import components using CocoaPods. The specific steps for importing components are as follows:

1. You need to download the `AudienceList` and `Common` folders on [GitHub](https://github.com/Tencent-RTC/TUILiveKit/tree/main/iOS) to your local system.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/02be05f42b3c11f0b0b1525400e889b2.png)

2. Add dependencies of `pod 'TUIAudienceList'` and `pod 'TUILiveResources'` in your `Podfile`.

Swift

```
target 'xxxx' do  ...  ...  pod 'TUILiveResources', :path => '../Component/Common/TUILiveResources.podspec'  // The path is the relative path between your Podfile file and TUILiveResources.podspec file.  pod 'TUIAudienceList', :path => '../Component/AudienceList/TUIAudienceList.podspec'  // The path is the relative path between your Podfile file and TUIAudienceList.podspec file.end
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
1. reate a directory named livekit_component under the lib directory in your project, and copy the common directory and component/audience_list directory from the [livekit/lib](https://github.com/Tencent-RTC/TUILiveKit/tree/main/Flutter/livekit/lib) directory on github to the livekit_component directory you created.
2. Adjust the import directory and change the import path to a relative path within your own project.

## Component Usage

> **Notes:**Since online audience information can only be obtained in the live streaming room. When using the audience list component, note the use limits and reuse it after successfully entering the live streaming room.

### Creating Components

Android

iOS

Flutter

You have two ways to create a live streaming room information component, as follows:

1. Create in code

```
AudienceListView audienceListView = new AudienceListView(getContext());
```

2. Define in xml:

```
<com.trtc.uikit.livekit.component.audiencelist.AudienceListView    android:id="@+id/audience_list_view"    android:layout_width="135dp"    android:layout_height="24dp"    android:layout_gravity="end" />
```

```
import TUIAudienceListlet audienceListView = AudienceListView()// ...Add audienceListView to your parent view here and adjust the layout
```

> **Noteï¼**This operation needs to be executed after successfully entering the room. You need to set `enterRoomSuccessNotifier.value` to `true` after success.

```
final enterRoomSuccessNotifier = ValueNotifer(false);// change enterRoomSuccessNotifier.value to true after enter room successValueListenableBuilder(    valueListenable: enterRoomSuccessNotifier,    builder: (context, enterRoomSuccess, _) {      return Visibility(        visible: enterRoomSuccess,        child: AudienceListWidget(          roomId: 'replace with your roomId',        ),      );    }),
```

### Component Initialization

Android

iOS

Flutter

After successfully entering the room, you can call the `init` method of the `AudienceListView` to bind data and events for the component.

> **Note:**This operation needs to be executed after successful room entry. The callback for room entry success will return a TUIRoomDefine.RoomInfo object.

```
audienceListView.init(roomInfo);
```

After successfully entering the room, you can call the `initialize` method of the `AudienceListView` to bind data and events for the component.

> **Note:**Note: This operation needs to be executed after successful room entry. The callback for room entry success will return a TUIRoomInfo object.

```
audienceListView.initialize(roomInfo: roomInfo)
```

For details, see [Creating Components](#b47155fa-84bf-49d8-85cf-f57566c4ecbd)


---
*Source: [https://trtc.io/document/69846](https://trtc.io/document/69846)*
