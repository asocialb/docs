# Integration

## Feature Overview

**TUILiveKit** is a comprehensive live-streaming component. Once integrated, it allows you to quickly implement the following key functional modules for your Android application:

| **Host Prepare Page** | **Host Streaming Page** | **Live Stream List** | **Audience Viewing Page** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f6c9b1399ed11f0930a5254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f72943c99ed11f09936525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f73e09599ed11f0bf2352540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f72750799ed11f0a90152540099c741.png) |

## **Preparations**

### Activate the Service

Before using **TUILiveKit**, please refer to [Activate Service](https://www.tencentcloud.com/document/product/647/60033) to get the TUILiveKit **Trial Edition** or activate the **Pro Edition**.

### **Environment Requirements**

- **Flutter**
  - Flutter 3.27.4 or higher.
  - Dart 3.6.2 or higher.
- **Android**
  - Android 5.0 (SDK API Level 21) or later.
  - Gradle 7.0 or higher.
  - Android 5.0 or higher mobile devices.
- **iOS**
  - Xcode 15 or later.
  - iOS 13.0 or later.
  - CocoaPods environment is installed. If not installed, [how to install CocoaPods](https://guides.cocoapods.org/using/getting-started.html).

## Code Integration

### **Step 1. Install**TUILiveKit

In the root directory of your project, run the following command to install [tencent_live_uikit](https://pub.dev/packages/tencent_live_uikit):

```
flutter pub
```

After installation completes, you should see output similar to:

```
Resolving dependencies... Downloading packages... ......+ tencent_live_uikit x.x.x......Changed xx dependencies!xx packages have newer versions incompatible with dependency constraints.Try `flutter pub outdated` for more information.
```

### Step 2. Project Configuration

Android

iOS

1. f you're building for Android, add certain SDK classes to the obfuscation exclusion list because the SDK uses Java reflection internally.
  - Configure and enable obfuscation rules in your project's `android/app/build.gradle` file:

```
  android {    ......    buildTypes {          release {              ......            // configuration and activation obfuscation rule            minifyEnabled true              proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'          }     }}
```

  - Add the following code in the `android/app/proguard-rules.pro` file. If the file does not exist, create a new one:

```
-keep class com.tencent.** { *; }
```

2. Configure and enable Multidex support in your project's `android/app/build.gradle` file.

```
  android {      ......    defaultConfig {      ......      // Enable Multidex support      multiDexEnabled true    } }
```

3. (Optional) If you need to integrate the floating live broadcast page, the system Picture-in-Picture feature needs to be enabled.

In the App main project's `AndroidManifest.xml`, set `MainActivity`'s `android:supportsPictureInPicture` to true:

```
  <manifest xmlns:android="http://schemas.android.com/apk/res/android">    <application>        <activity            android:name=".MainActivity"            android:supportsPictureInPicture="true"        </activity>    </application></manifest>
```

1. For iOS release builds, configure symbol retention rules. In Xcode, select your app target (usually Runner) in TARGETS, go to **Project** > **Build Settings** > **Deployment**, and set **Strip Style** to `Non-Global Symbols`. This is required to avoid runtime errors and ensure you can enter the room.
2. (**Optional**) If you are debugging on an iOS simulator and your Mac uses an Intel chip, add the following code to your `ios/Podfile`:

```
target 'xxxx' do  ......end......post_install do |installer|  installer.pods_project.targets.each do |target|    flutter_additional_ios_build_settings(target)    target.build_configurations.each do |config|      config.build_settings['VALID_ARCHS'] = 'arm64 arm64e x86_64'      config.build_settings['VALID_ARCHS[sdk=iphonesimulator*]'] = 'x86_64'    end  endend
```

3. TUILiveKit requires access to the microphone and camera. Request permissions by adding the following entries under the top-level `<dict>` in your iOS projectâs `Info.plist`. These messages appear in the system permission dialogs:

```
<key>NSCameraUsageDescription</key><string>CallingApp needs camera access. Video recording with picture only after enabling</string><key>NSMicrophoneUsageDescription</key><string>CallingApp needs mic access. Recorded video will have sound when enabled</string>
```

After updating `Info.plist`, add these preprocessor definitions in your `ios/Podfile` to enable camera and microphone permissions:

```
post_install do |installer|  installer.pods_project.targets.each do |target|    flutter_additional_ios_build_settings(target)      target.build_configurations.each do |config|        config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [      '$(inherited)',      'PERMISSION_MICROPHONE=1',      'PERMISSION_CAMERA=1',      ]    end  endend
```

4. (Optional) To support floating window live streaming, enable Picture-in-Picture in your Xcode project settings:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/69d2e94fe22511f0a5a25254007c27c5.png)

### Step 3. Configure Navigation and Localization

To enable TUILiveKit to manage page navigation and support multiple languages, update your Flutter app as follows:

- Add `TUILiveKitNavigatorObserver.instance` to `navigatorObservers` to track route changes and manage lifecycle events.
- Add the required localization delegates to `localizationsDelegates` to display UI text in the appropriate system language.

Take the **MaterialApp** framework as an example, the sample code is as follows:

```
import 'package:tencent_live_uikit/tencent_live_uikit.dart';// Your own APP main classclass XXX extends StatelessWidget {  const XXX({super.key}); @override  Widget build(BuildContext context) {    return MaterialApp(      // Add TUILiveKit navigator observer to listen for page routing changes and lifecycle management      navigatorObservers: [TUILiveKitNavigatorObserver.instance],      // Add localized agent to support multilingual copywriting display      localizationsDelegates: [      ...LiveKitLocalizations.localizationsDelegates,      ...BarrageLocalizations.localizationsDelegates,      ...GiftLocalizations.localizationsDelegates],            // Other configuration of your APP      ......    );  }}
```

After configuration, the component will support multilingual and correctly handle page transitions.

## Complete Login

After integrating the code, call `TUILogin.login` to authenticate. **This step is required before you can use any TUILiveKit features**. Make sure all parameters are set correctly.

> **Note:**In the example code, the login API is called directly. However, In real-world projects, always call TUILiveKitâs `login` after completing your own user authentication and login logic. This prevents business logic conflicts or data inconsistencies, and ensures TUILiveKit integrates smoothly with your user management and permission system.

```
import 'package:tencent_cloud_uikit_core/tencent_cloud_uikit_core.dart';......login() async {  await TUILogin.instance.login(    1400000001,     // replace with the SDKAppID from the open service console    "denny",        // replace with your UserID    "xxxxxxxxxxx",  // you can calculate a UserSig in the console and fill it in this location    TUICallback(      onError: (code, message) {        print("TUILogin login fail, {code:$code, message:$message}");      },      onSuccess: () async {        print("TUILogin login success");      },    ),  );}
```

**Login API Parameters**

| Parameter | Type | Description |
| --- | --- | --- |
| SDKAppID | Int | Get this from [Tencent RTC Console > My Application](https://console.trtc.io/app). |
| UserID | String | The unique ID for the current user. Must contain only English letters, numbers, hyphens, and underscores. |
| UserSig | String | Authentication credential for TRTC. Please note:**Development Environment**: You can use the local `GenerateTestUserSig.genTestSig` function to generate a UserSig or generate a temporary UserSig via the [UserSig Generation Tool](https://console.trtc.io/usersig).**Production Environment**: To prevent key leakage, you must use a server-side method to generate UserSig. For details, see [Generating UserSig on the Server](https://www.tencentcloud.com/document/product/647/69883).For more information, see [How to Calculate and Use UserSig](https://www.tencentcloud.com/document/product/647/35166). |

## (Optional) Floating Window Setup

By default, your appâs `MaterialApp` home page is displayed on the `rootNavigator`. To support floating window live rooms (minimize the live window during streaming and keep it floating above other pages), add a secondary navigator (`secondaryNavigator`) above the rootNavigator and move your home page to `secondaryNavigator`.

The live pageâs Overlay will be shown on `secondaryNavigator`, which stays resident in the app to enable the floating window effect.

```
import 'package:tencent_live_uikit/tencent_live_uikit.dart';import 'package:tencent_live_uikit/common/widget/global.dart';// Your own App's main classclass XXX extends StatelessWidget {  const XXX({super.key}); @override  Widget build(BuildContext context) {    return MaterialApp(         // Homepage configuration         home: Navigator(            // Global.secondaryNavigatorKey is the global navigation key provided by TUILiveKit to manage floating windows.            key: Global.secondaryNavigatorKey,            onGenerateRoute: (settings) => MaterialPageRoute(              settings: const RouteSettings(name: 'home_widget'),              builder: (BuildContext context) {                // HomeWidget is your own application homepage widget, replace with your actual homepage class                return const HomeWidget();              },            ),          ),         // Other configuration of your App         ......    );  }}
```

This step is the necessary configuration to enter the floating window page. For the complete process, refer to [Add Floating Window (Host Page)](https://www.tencentcloud.com/document/product/647/73742#330378b2-2f2c-45ba-9a1a-743448cc3d19) and [Add Floating Window (Audience Page)](https://www.tencentcloud.com/document/product/647/73749#330378b2-2f2c-45ba-9a1a-743448cc3d19). If you do not need to connect the floating window page, please skip this step.

## Next Steps

Congratulations! You have successfully integrated the **TUILiveKit** component and completed the login. You can now implement features such as **host streaming**, **audience viewing**, and **live stream list**. Please refer to the table below for integration guides:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Streaming** | The complete workflow for a host to start a stream, including pre-stream setup and various in-stream interactions. | [Host Streaming](https://www.tencentcloud.com/document/product/647/73742) |
| **Audience Viewing** | Audience can watch live streaming after entering the anchor's live streaming room, with features like audience mic connection, live room information, online audience, and bullet screen display. | [Audience Viewing](https://www.tencentcloud.com/document/product/647/73749) |
| **Live Stream List** | Display the live stream list interface and features, including the live stream list and room information display. | [Live Stream List](https://www.tencentcloud.com/document/product/647/73761) |

## FAQs

### Repeated Login

You do not need to log in each time you enter a room. Typically, a single call to `TUILogin.login` is sufficient. We recommend aligning `TUILogin.login` and `TUILogin.logout` with your own authentication logic.

### Running or Unable to Enter Room after Packaging in iOS Release?

Refer to [Project Configuration](#62b3f143-07f5-416a-8057-fff865e35d46) for iOS:

In Xcode, select your application target (usually Runner) from the TARGETS list, choose **Item** > **Build Settings** > **Deployment**, and set **Strip Style** to `Non-Global Symbols` to preserve the necessary global symbol information. Otherwise, runtime exceptions may prevent you from entering the room.

## Contact Us

If you have questions or need help during integration, join our [Telegram technical group](https://t.me/+EPk6TMZEZMM5OGY1?s_url=https%3A%2F%2Ftrtc.io) or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/63255](https://trtc.io/document/63255)*
