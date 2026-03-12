# Integration

This document describes how to rapidly integrate the TUICallKit component. You can complete the following key steps within 10 minutes and obtain a complete audio and video call interface.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6dcf7117b60011f0a808525400bf7822.png)

## Preparations

### **Environmental Requirements**

- **Flutter Version**: Flutter 3.10.0, Dart 3.0 and above.

### Service Activation

Please refer to the [Service Activation](https://www.tencentcloud.com/document/product/647/59832) documentation to obtain your `SDKAppID` and `SDKSecretKey`. These credentials will be required in the subsequent login step.

## Implementation

### Step 1.Importing Components

Add the [tencent_calls_uikit](https://pub.dev/packages/tencent_calls_uikit) plugin dependency in your project's pubspec.yaml file:

```
flutter pub
```

### Step 2.Project Configuration

1. Native Project Configuration:

Android

iOS

1. Configure ProGuard Rules (Code Obfuscation):Since the SDK internally uses Java reflection, certain SDK classes must be added to the non-obfuscation list.
  - **Enable Obfuscation Rules**: In the `android/app/build.gradle` file, ensure that ProGuard rules are configured and enabled:

```
  android {    ......    buildTypes {          release {              ......            minifyEnabled true              proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'          }     }}
```

  - **Add Rules:** Create a `proguard-rules.pro` file in the android/app directory (if it doesn't exist) and add the following code:

```
-keep class com.tencent.** { *; }
```

2. Configure and enable Multidex support in the `android/app/build.gradle` file.

```
  android {      ......    defaultConfig {      ......      multiDexEnabled true    } }
```

Grant Camera and Microphone Permissions:Because TUICallKit requires audio and video functionality, you must obtain authorization for the microphone and camera. Add the following two privacy usage descriptions to the top-level `<dict>` directory in your iOS project's `Info.plist` file:

```
<key>NSCameraUsageDescription</key><string>CallingApp requires access to your camera to display video during calls.</string><key>NSMicrophoneUsageDescription</key><string>CallingApp requires access to your microphone to capture audio during calls.</string>
```

- Flutter Project Configuration:

Add TUICallKit.navigatorObserver to the navigatorObservers property of your Flutter application framework. Below is sample code using the MaterialApp framework:

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart'; ......class XXX extends StatelessWidget {  const XXX({super.key}); @override  Widget build(BuildContext context) {    return MaterialApp(      navigatorObservers: [TUICallKit.navigatorObserver],      ......    );  }}
```

### Step 3. Login

This step is critical: you can only use the features provided by TUICallKit after successfully logging in by calling the `login` interface.

**login**

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';import 'package:tencent_calls_uikit/debug/generate_test_user_sig.dart';......final String userID    = 'xxxxx';  // Replace with the UserID for the current user (required)final int    sdkAppID  = 0;        // Replace with the SDKAppID obtained in the previous stepfinal String secretKey = 'xxxx';   // Replace with the UserSig for the current user (required)void login() async {    String userSig  = GenerateTestUserSig.genTestSig(userID, sdkAppID, secretKey);    TUIResult result = await TUICallKit.instance.login(sdkAppID, userID, userSig);    if (result.code.isEmpty) {      print('Login success');    } else {      print('Login failed: ${result.code} ${result.message}');    }}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userID | String | Only allowing a combination of uppercase and lowercase letters (a-z A-Z), numbers (0-9), hyphens, and underscores. |
| sdkAppID | int | The unique identifier SDKAppID of the audio and video application created in the [Tencent Real-Time Communication (TRTC) Console](https://trtc.io/login?fro=gt&s_url=https%3A%2F%2Fconsole.trtc.io%2F). |
| secretKey | String | The SDKSecretKey of the audio/video application created in the [Tencent Real-Time Communication (TRTC) Console](https://trtc.io/login?fro=gt&s_url=https%3A%2F%2Fconsole.trtc.io%2F). |
| userSig | String | A security protection signature used to authenticate user login, confirm whether the user is genuine, and prevent malicious attackers from misappropriating your cloud service usage rights. |

> **Noteï¼****Development environment**: If you are in the local development and debugging stage, you can adopt the local `GenerateTestUserSig.genTestSig` function to generate userSig. In this method, the SDKSecretKey is very easy to decompile and reverse engineer. Once your key is leaked, attackers can steal your Tencent Cloud traffic.**Production environment**: If your project is ready to launch, use [server-side generation of UserSig](https://www.tencentcloud.com/document/product/647/35166).

### Step 4.Set Nickname and Avatar [Optional]

After a successful login, you can call the `setSelfInfo` function to set your nickname and avatar. The set nickname and avatar will be displayed on the caller/callee interface.

**setSelfInfo**

Flutterï¼Dartï¼

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dartvoid _setSelfInfo() {    String nickname = "jack"    String avatar = "https:/****/user_avatar.png"    TUIResult result = TUICallKit.instance.setSelfInfo(nickname, avatar);}
```

| Parameter | Type | Description |
| --- | --- | --- |
| nickname | String | Target user's nickname |
| avatar | String | Target user's avatar |

### Step 5.Initiating a Call

The caller initiates a call by invoking the `calls` function and specifying the media type (voice or video) and the callee's User ID list (userIdList). The calls interface supports both one-to-one and group calls. A one-to-one call is initiated when the userIDList contains only a single User ID; a group call is initiated when it contains multiple User IDs.

**calls**

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';......void _call() {    List<String> userIdList = ['vince'];    TUICallMediaType mediaType = TUICallMediaType.audio;    TUICallParams callParams = TUICallParams();        TUICallKit.instance.calls(participantIds, mediaType, callParams);}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | List<String> | Target user ID list. |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Media type of the call, such as video call, voice call. |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams) | Call extension parameters, such as room number, call invitation timeout, offline push custom content. |

### Step 6.Answering a Call

Once the callee successfully logs in, the caller can initiate a call, and the callee will receive the call invitation, accompanied by a ringtone and vibration.

## More Features

### Enabling Floating Window

You can enable/disable the floating window feature by calling `enableFloatWindow`. This feature should be enabled when initializing the TUICallKit component, with the default status being Off (false).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/61e27556bbb811f0a808525400bf7822.png)

**enableFloatWindow**

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';......void _enableFloatWindow() {    TUICallKit.instance.enableFloatWindow(true);}
```

**Details:** Default false, the floating window button in the top-left corner of the call interface is hidden. Set to true to display.

### Enabling Banner

You can enable or disable the incoming call banner display by calling `enableIncomingBanner`. By default, this feature is disabled (false). When the callee receives an inbound call, the full-screen call waiting interface is shown first. When the banner is enabled, a notification banner will display initially, switching to the full-screen view as required. Note that displaying the banner requires floating window permission. The exact display behavior depends on permission settings and whether the app is running in the foreground or background.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/89b0f4e5bbb811f0a808525400bf7822.png)

**enbalecomingBanner**

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';......void _enableFloatWindow() {    TUICallKit.instance.enableIncomingBanner(true);}
```

**Details:** Default false. The callee side pops up the full-screen call waiting interface by default when receiving an invitation. When enabled, a banner is displayed first, then the full-screen call interface is pulled up as needed.

### Multi-Person Calling

When the caller uses the `calls` method to initiate a call, if the list of called users exceeds one person, it is automatically recognized as a multi-person call. Other members can then join this multi-person call using the `join` method.

- **Initiating a Multi-person Call:** When the `calls` method is used to initiate a call, if the callee User ID list (userIdList) contains more than one user, it will be automatically deemed a multi-person call.

**calls**

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';......void _call() {    List<String> userIdList = ['vince','mike'];    TUICallMediaType mediaType = TUICallMediaType.audio;    TUICallParams callParams = TUICallParams();        TUICallKit.instance.calls(participantIds, mediaType, callParams);}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | List<String> | Target user ID list. |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Media type of the call, such as video call, voice call. |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams) | Call extension parameters, such as room number, call invitation timeout, offline push custom content. |

- **Joining a Multi-person Call:** You can use the `join` method to enter the specified multi-person call.

**join**

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';void join() {    String callId = "123456";    TUICallKit.instance.join(callId);}
```

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | The unique ID for this call. |

### Language Settings

- **Supported Languages:**We currently support Simplified Chinese, English, and Japanese. The default language is English.
- **Switching Languages:** TUICallKit does not provide a separate language switching API. Its interface language will automatically align with the language setting used by the application's current root component (such as MaterialApp or CupertinoApp).

> **Noteï¼**If you need to set up other languages, please contact us at **info_rtc@tencent.com** for assistance.

### Ringtone Setting

You can set the default ringtone, incoming call silent mode, and Offline Push Ringtone in the following ways:

- **Setting Default Ringtone (Method 1):**If you include TUICallKit component via source code, you can replace the resource fileï¼[ringtone when initiating a call](https://github.com/Tencent-RTC/TUICallKit/blob/main/Flutter/assets/audios/phone_dialing.mp3)ã[ringtone when initiating a call](https://github.com/Tencent-RTC/TUICallKit/blob/main/Flutter/assets/audios/phone_ringing.mp3)ï¼to set a custom default ringtone.
- **Setting Default Ringtone (Method 2):**Use the `setCallingBell` interface to set the incoming call ringtone received by the callee.

**setCallingBell**

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';......void _setCallingBell() {    TUICallKit.instance.setCallingBell('flieName');}
```

**Details:**The ringtone file must be placed in the main project's assets and configured in the main project's pubspec.yaml file.

| Parameter | Type | Description |
| --- | --- | --- |
| fileName | String | Ringtone Name. |

- **Incoming call silent mode:** You can set mute mode through `enableMuteMode`.

**enableMuteMode**

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';......void _setCallingBell() {    TUICallKit.instance.enableMuteMode(true);}
```

**Details:** When set to true, incoming call requests will not trigger ringtone playback (silent mode).

- **Custom Offline Push Ringtone**: Please refer to the specific setup methods for iOS and Android below.

Android

iOS

For FCM, the push ringtone is set by the application's configured notification sound.

For Huawei, Xiaomi, and APNs push services, the push ringtone must be configured when calling the `calls` methods by setting the `iOSSound` and `androidSound` fields within `TUIOfflinePushInfo`.

VoIP push notifications do not support custom ringtones.

For APNs push notifications, you can modify the offline message ringtone on the iOS platform by setting the `TUIOfflinePushInfo.iOSSound` parameter, which is located in the params parameter of the `calls` interfaces.

## Customizing Your UI

### Replacing Icon Button

You can directly replace the icons under the [assets/images](https://github.com/Tencent-RTC/TUICallKit/tree/main/Flutter/assets/images) folder to ensure the icon color and style remain consistent throughout the entire App. The following list shows basic feature buttons. You can replace the corresponding icons to fit your own business scenario.

Commonly Used Icon File Name List

| Icon | File name | Description |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87b3fd48b63411f0b4c35254001c06ec.png) | dialing.png | Answer incoming call icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87bc58a9b63411f0a808525400bf7822.png) | hangup.png | Hang Up Call icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87b50a49b63411f0b9945254005ef0f7.png) | mute_on.png | Turn off the mic icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87b948a1b63411f0a808525400bf7822.png) | handsfree.png | Turn off the speaker icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87b904d4b63411f0a808525400bf7822.png) | camera_off.png | Camera Off icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87ae00adb63411f0b0cf525400e889b2.png) | add_user.png | Invite user icon during call |

## FAQs

If you encounter any issues during integration and use, please refer to [Frequently Asked Questions](https://www.tencentcloud.com/document/product/647/56860).

## Contact Us

If you have any suggestions or feedback, please contact `info_rtc@tencent.com`.


---
*Source: [https://trtc.io/document/54896](https://trtc.io/document/54896)*
