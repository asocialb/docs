# Voice Room Componentï»¿

## Component Overview

**The core control of the voice chat room** (**SeaGridView**) is a core control designed specifically for live-streaming scenarios. It provides a series of powerful API features to help developers quickly implement voice chat room functionality. With this control, you can easily enable or disable the voice chat room and efficiently manage seat operations in the live streaming room, including applying for microphone mode, inviting speakers, moving microphone positions, and removing speakers. With the aid of **SeaGridView**, you can quickly integrate the voice chat room module into your application, significantly enhance the user experience, and simultaneously reduce development costs.

## Development Environment Requirement

Android

iOS

Flutter

- Android 5.0 (SDK API Level 21) and above versions.
- Gradle 7.0 or higher.
- Mobile devices with Android 5.0 and above.
- During environment configuration or running period, if there are issues, please see [common issues](https://www.tencentcloud.com/document/product/647/67290#).
- Xcode 15 or higher.
- iOS 13.0 and above.
- CocoaPods environment installation. [Click to view](https://guides.cocoapods.org/using/getting-started.html).
- If you encounter problems during access or while using, please see [common issues](https://www.tencentcloud.com/document/product/647/67290#).

| Platform | Version |
| --- | --- |
| Flutter | Flutter 3.27.4 and higher versions.Dart 3.6.2 or higher |
| Android | Android Studio 3.5 and above versions.Android devices with Android 5.0 and above. |
| iOS | Xcode 15.0 or higher.Ensure that your project has a deemed valid developer signature. |

## Step 1: activate the service

Please see [Activate Service (TUILiveKit)](https://www.tencentcloud.com/document/product/647/60033#) to claim the trial edition or activate the paid edition.

## Step Two: Seamless Integration and Configuration

Android

iOS

Flutter

1. In the app directory, find the `build.gradle.kts (or build.gradle)` file, add the following code in it, and add a dependency on the SeatGridView Component:

build.gradle.kts

build.gradle

```
api("io.trtc.uikit:live-stream-core:latest.release")
```

```
api 'io.trtc.uikit:live-stream-core:latest.release'
```

2. Since we use Java's reflection features internally in the SDK, some classes in the SDK need to be added to the non-obfuscation list. Therefore, you need to add the following code in the `proguard-rules.pro` file:

```
-keep class com.tencent.** { *; }-keep class com.trtc.uikit.livekit.voiceroomcore.** { *; }-keep class com.google.gson.** { *;}
```

3. In the app directory, find the `AndroidManifest.xml` file. In the application node, add tools:replace="android:allowBackup" and android:allowBackup="false". Override the settings within the component and use your own settings.

```
  // app/src/main/AndroidManifest.xml    <application    ...      // Add the following configuration to overwrite the configuration in the dependent sdk.    android:allowBackup="false"    tools:replace="android:allowBackup">
```

Use CocoaPods to import components. If you encounter problems, please first refer to [Environment Preparation](https://www.tencentcloud.com/document/product/647/69845#7d035489-3ed3-46ff-845e-eb7279e0d486). The specific steps for importing components are as follows:

1. Add `pod 'LiveStreamCore'` dependency in your `Podfile`.

Swift

```
target 'xxxx' do  ...  ...  pod 'LiveStreamCore'end
```

If you don't have a `Podfile` file, first use the terminal to `cd` into the `xxxx.xcodeproj` directory, then create it through the following command:

```
pod init
```

2. In the terminal, first `cd` to the `Podfile` directory, then execute the following commands to install components.

```
pod install
```

If the latest version of SeatGridView cannot be installed, first delete **Podfile.lock** and **Pods**. Then execute the following commands to update the local CocoaPods repository list.

```
pod repo update
```

Then execute the following commands to update the Pod version of the component library.

```
pod update
```

3. Compile and run first. If you encounter problems, please see [common issues](https://www.tencentcloud.com/document/product/647/67290#). If the problem is still unresolved, you can try running our [Example](https://github.com/Tencent-RTC/TUILiveKit/blob/main/iOS/Example) project. For any issues you encounter during integration and use, feel free to [give us feedback](https://github.com/Tencent-RTC/TUILiveKit/issues).

In the root directory of the project, run the following command to install the [live_stream_core](https://pub.dev/packages/live_stream_core) plug-in via command line.

```
flutter pub
```

Feel free to [give feedback](https://github.com/Tencent-RTC/TUILiveKit/issues) on any issues you encounter during integration and use.

## Step 3: Logging In

Android

iOS

Flutter

Add the following code in your project. It enables TUI component log in by calling relevant APIs in TUICore. This step is crucial. Only after successful log in can you properly use various features provided by SeatGridView.

Kotlin

Java

```
TUIRoomEngine.login(applicationContext,    1400000001,      // Replace with the SDKAppID obtained in step 1    "denny"         // Replace with your UserID    "xxxxxxxxxxx",   // You can calculate a UserSig in the console and fill it in this position    object : TUIRoomDefine.ActionCallback() {        override fun onSuccess() {            Log.i(TAG, "login success")        }        override fun onError(errorCode: Int, errorMessage: String) {            Log.e(TAG, "login failed, errorCode: $errorCode msg:$errorMessage")        }    })
```

```
TUIRoomEngine.login(context,     1400000001,     // Replace with the SDKAppID obtained in step 1    "denny"        // Replace with your UserID    "xxxxxxxxxxx",  // You can calculate a UserSig in the console and fill it in this position        new TUIRoomDefine.ActionCallback() {            @Override            public void onSuccess() {                Log.i(TAG, "login success");            }            @Override            public void onError(TUICommonDefine.Error error, String message) {                Log.e(TAG, "login failed, errorCode: " + errorCode + " msg:" + errorMessage);            }        });
```

Add the following code in your project. It enables TUI component log in by calling login-related APIs in RTCRoomEngine. This step is crucial. Only after successful log in can you properly use various features provided by SeatGridView.

swift

```
////  AppDelegate.swift//import RTCRoomEnginefunc application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {      TUIRoomEngine.login(sdkAppId: 1400000001,       // Replace with the SDKAppID obtained in step 1                          userId: "denny",          // Replace with your UserID                         userSig: "xxxxxxxxxxx") {  // You can calculate a UserSig in the console and fill it in this position      print("login success")    } onError: { code, message in      print("login failed, code: \\(code), error: \\(message ?? "nil")")    }        return true}
```

Add the following code in your project. It enables TUI component log in by calling login-related APIs in RTCRoomEngine. This step is crucial. Only after successful log in can you properly use various features provided by LiveStreamCore.

```
final result = await TUIRoomEngine.login(                    'Replace with your activated SDKAppID',                    'Replace with your userId',                    'Replace with your userSig');
```

**Parameter Description**

Here is a detailed introduction to several key parameters needed in the login function:

| Parameters | Type | Overview |
| --- | --- | --- |
| SDKAppID | int | In the final step of step 1, you have already obtained it. No redundancy here. |
| UserID | String | Current user's ID, string type, only allow to include English letters (a-z and A-Z), digits (0-9), hyphen and underscore. |
| userSig | String | Obtain the SecretKey from step 3 of [Step 1](https://www.tencentcloud.com/document/product/647/69845#step1), use it to encrypt information such as SDKAppID and UserID, and you can get UserSig. It is an authentication token used by Tencent Cloud to verify whether the current user can use the TRTC service. You can generate a temporary available UserSig through the [**Auxiliary Tool**](https://trtc.io/login?s_url=https://console.trtc.io/usersig) in the console. For more information, see [How to Calculate and Use UserSig](https://www.tencentcloud.com/document/product/647/39074#). |

> **Notes:****Development Environment**: If you are in the local development and debugging stage, you can use the local `GenerateTestUserSig.genTestSig` function to generate userSig. In this method, SDKSecretKey can be easily decompiled and reverse cracked. Once your key is leaked, attackers can misappropriate your Tencent Cloud traffic.**Production environment**: If you want to launch your project, use server-side generation of UserSig.

## Step 4: Use Core Controls to Implement Voice Chat Room Functionality

### Room Owner Enables Voice Chat Room & Becomes Speaker

#### **Effect Preview**

| **Room owner enables voice chat room & becomes speaker** |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c0f6ea4f24d611f09e67525400bf7822.png) |

#### **Create Core Controls**

Android

iOS

Flutter

You can load our core control in your Activity through java code or the xml method. The following is an example of the code method (the xml method is similar).

kotlin

java

```
val seatGridView = SeatGridView(this)
```

```
SeatGridView seatGridView = new SeatGridView(this);
```

swift

```
import LiveStreamCorelet seatGridView = SeatGridView()
```

You need to first create a controller `SeatGridController`, then assign it to the core component of the voice chat room `SeatGridWidget`.

`SeatGridController` is responsible for providing APIs. `SeatGridWidget` is used to display the seat UI. You can add `SeatGridWidget` anywhere you need to display the seat UI.

```
final controller = SeatGridController();SeatGridWidget(controller: controller);
```

#### **Anchor Enables Voice Chat Room & Becomes Speaker**

Turn on a voice chat room and stream the data of local microphone capture to the live streaming room.

Android

iOS

Flutter

kotlin

java

```
val roomInfo = TUIRoomDefine.RoomInfo()roomInfo.roomId = Config.roomIdroomInfo.seatMode = TUIRoomDefine.SeatMode.APPLY_TO_TAKEseatGridView.startVoiceRoom(roomInfo, object : TUIRoomDefine.GetRoomInfoCallback {    override fun onSuccess(roomInfo: TUIRoomDefine.RoomInfo) {        val seatIndex = 1        val timeout = 60        seatGridView.takeSeat(seatIndex, timeout, null)        seatGridView.startMicrophone(null)    }    override fun onError(error: TUICommonDefine.Error, message: String) {    }})
```

```
TUIRoomDefine.RoomInfo roomInfo = new TUIRoomDefine.RoomInfo();roomInfo.roomId = "roomId_123456";roomInfo.seatMode = TUIRoomDefine.SeatMode.APPLY_TO_TAKE;seatGridView.startVoiceRoom(roomInfo, new TUIRoomDefine.GetRoomInfoCallback() {    @Override    public void onSuccess(TUIRoomDefine.RoomInfo roomInfo) {        int seatIndex = 1;        int timeout = 60;        seatGridView.takeSeat(seatIndex, timeout, null);        seatGridView.startMicrophone(null);    }    @Override    public void onError(TUICommonDefine.Error error, String message) {    }});
```

swift

```
import LiveStreamCoreimport RTCRoomEnginelet roomInfo = TUIRoomInfo()roomInfo.roomId = "123456"roomInfo.seatMode = .applyToTakeseatGridView.startVoiceRoom(roomInfo: roomInfo) { roomInfo in} onError: { code, message in}seatGridView.startMicrophone() {} onError: { code,message in}
```

```
import 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';final roomInfo = TUIRoomInfo(roomId: 'replace with your roomId');roomInfo.name = 'replace with your roomName';roomInfo.seatMode = TUISeatMode.applyToTake;roomInfo.isSeatEnabled = true;roomInfo.roomType = TUIRoomType.livingRoom;final startVoiceRoomResult = await controller.startVoiceRoom(roomInfo);final startMicrophoneResult = await controller.startMicrophone();
```

### 

### Audience Joins a Voice Chat Room

#### Effect preview

| **Audience joins a voice chat room** |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1fb22e924d611f091625254001c06ec.png) |

Android

iOS

Flutter

kotlin

java

```
seatGridView.joinVoiceRoom("roomId_123456", null)
```

```
seatGridView.joinVoiceRoom("roomId_123456", null);
```

swift

```
import LiveStreamCoreimport RTCRoomEngineseatGridView.joinVoiceRoom(roomId: "roomId_123456") { roomInfo in} onError: { code, message in}
```

```
import 'package:live_stream_core/live_stream_core.dart';final result = await controller.joinVoiceRoom('replace with your roomId');
```

### 

### Audience Requests to Speak

#### **Effect Preview**

| Apply for Microphone Mode Before | Become a Speaker |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1dfc8a824d611f0b0b1525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1b1c1c824d611f0a62e525400454e06.png) |

The audience apply for microphone mode feature is mainly implemented through `SeatGridView (Android & iOS)` / `SeatGridController (Flutter)`. You can call the following API functions to implement the audience apply for microphone mode feature. The implementation is as follows, taking Audience B's request to speak as an example.

#### Audience Sending Request to Speak

Audience B sends a request to speak to anchor A. Anchor A will receive Audience B's request to speak in the onSeatRequestReceived callback.

Android

iOS

Flutter

Kotlin

Java

```
val seatIndex = 1; val timeout = 60; seatGridView.takeSeat(seatIndex, timeout, object : VoiceRoomDefine.RequestCallback {    override fun onAccepted(userInfo: TUIRoomDefine.UserInfo) {        Log.i(TAG, "Request to speak approved")    }    override fun onRejected(userInfo: TUIRoomDefine.UserInfo) {        Log.i(TAG, "Application for speaking is rejected")    }    override fun onCancelled(userInfo: TUIRoomDefine.UserInfo) {        Log.i(TAG, "Application for speaking is canceled")    }    override fun onTimeout(userInfo: TUIRoomDefine.UserInfo) {        Log.i(TAG, "Request to speak timed out")    }    override fun onError(userInfo: TUIRoomDefine.UserInfo, error: TUICommonDefine.Error, message: String) {        Log.i(TAG, "Error in applying for speaking")    }})
```

```
int seatIndex = 1; int timeout = 60;seatGridView.takeSeat(seatIndex, timeout, new VoiceRoomDefine.RequestCallback() {    @Override    public void onAccepted(TUIRoomDefine.UserInfo userInfo) {        Log.i(TAG, "Request to speak approved")    }    @Override    public void onRejected(TUIRoomDefine.UserInfo userInfo) {        Log.i(TAG, "Application for speaking is rejected")    }    @Override    public void onCancelled(TUIRoomDefine.UserInfo userInfo) {        Log.i(TAG, "Application for speaking is canceled");    }    @Override    public void onTimeout(TUIRoomDefine.UserInfo userInfo) {        Log.i(TAG, "Request to speak timed out")    }    @Override    public void onError(TUIRoomDefine.UserInfo userInfo, TUICommonDefine.Error error, String message) {        Log.i(TAG, "Error in requesting to speak")    }});
```

swift

```
import RTCRoomEngineimport LiveStreamCorelet seatIndex = 1let timeout = 60 seatGridView.takeSeat(index: index, timeout: timeout) { userInfo in      print("Request to speak approved")    } onRejected: { userInfo in      print("Application for speaking is rejected")    } onCancelled: { userInfo in      print("Application for speaking is canceled")    } onTimeout: { userInfo in      print("Request to speak timed out")    } onError: { userInfo, code, message in      print("Error in applying for speaking")    }
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';const int seatIndex = 1;const int timeout = 60;final controller = SeatGridController();final result = await controller.takeSeat(seatIndex, timeout);if (result.code == TUIError.success) {                              switch (result.type) {                                  case RequestResultType.onAccepted:                                      debugPrint('Request to speak approved');                                      break;                                  case RequestResultType.onRejected:                                      debugPrint('Application for speaking is rejected');                                      break;                                  case RequestResultType.onCancelled:                                      debugPrint('Application for speaking is canceled');                                      break;                                  case RequestResultType.onTimeout:                                      debugPrint('Request to speak timed out');                                      break;                                  default:                                      break;                              }                        } else {                              debugPrint('Error in applying for speaking');   }
```

The audience's ability to request to speak is primarily implemented through `SeatGridView (Android & iOS)` / `SeatGridController (Flutter)`. You can call the following API functions to implement the audience's request to speak feature. The implementation is as follows, taking Audience B's request to speak as an example.

> **Notes:****Only when the room mode is**APPLY_TO_TAKE (request to speak), will the room owner receive a speaking request. In FREE_TO_TAKE (Free to Join the Podium) mode, takeSeat will become a speaker successfully.

#### Anchor Responding to Speaking Request

After Anchor A receives the speaking request from the audience, they can call responseRemoteRequest to respond whether to agree to Audience B's speaking request. Audience B will receive callbacks for Anchor A's agreement or rejection (onAccepted/onRejected).

Android

iOS

Flutter

Kotlin

Java

```
// Broadcaster agrees to let the audience speakseatGridView.responseRemoteRequest(userId, true, null);// Broadcaster denies the audience's speaking requestseatGridView.responseRemoteRequest(userId, false, null);
```

```
// Broadcaster agrees to let the audience speakseatGridView.responseRemoteRequest(userId, true, null);// Broadcaster rejects the audience's speaking requestseatGridView.responseRemoteRequest(userId, false, null);
```

swift

```
import RTCRoomEngineimport LiveStreamCore// Broadcaster agrees to let the audience speakseatGridView.responseRemoteRequest(userId, true) {} onError: { code, message in }// Broadcaster denies the audience's speaking requestseatGridView.responseRemoteRequest(userId, false) {} onError: { code, message in }
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';final controller = SeatGridController();const String userId = 'Replace with the userId of userB';// Broadcaster agrees to let the audience speakfinal result = await controller.responseRemoteRequest(userId, true);// Broadcaster denies the audience's speaking requestfinal result = await controller.responseRemoteRequest(userId, false);
```

#### Callback for Seat Information Changes

Android

iOS

Flutter

If you have already set up a Custom Seat View, you can listen to the updateSeatView callback to refresh your own custom UI.

Kotlin

Java

```
override fun updateSeatView(seatGridView: SeatGridView, seatInfo: TUIRoomDefine.SeatInfo, seatView: View) {   Log.i(TAG, "Seat information changes")}
```

```
@Overridepublic void void updateSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo, View seatView) {    Log.i(TAG, "Seat information changes")}
```

If you have already set up a Custom Seat View, you can listen to the updateSeatView callback to refresh your own custom UI.

swift

```
import RTCRoomEngineimport LiveStreamCorefunc seatGridView(_ view: SeatGridView, updateSeatView seatInfo: TUISeatInfo, seatView: UIView) {    print("Seat information changes")}
```

When seat information changes, the corresponding value of the `seatInfoNotifier` parameter in `SeatWidgetBuilder` will change. You can use your custom seat widget as a child component of `ValueListenableBuilder` to update your custom seat UI instantly.

Dart

```
// Definition of seatWidetBuildertypedef SeatWidgetBuilder = Widget Function(        BuildContext context,        ValueNotifier<TUISeatInfo> seatInfoNotifier,    ValueNotifier<int> volumeNotifier);    // Usage exampleimport 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';SeatGridWidget(       controller: controller,       seatWidgetBuilder: (                   BuildContext context,                   ValueNotifier<TUISeatInfo> seatInfoNotifier,                   ValueNotifier<int> volumeNotifier) {                          return ValueListenableBuilder(                        valueListenable: seatInfoNotifier,                        builder: (context, seatInfo, _) {                          // Return your custom seat component                                  return Container();                        }                     );                   })
```

### 

### Moving Microphone Positions for Seat Users

**Effect Preview**

| **Before Moving Microphone Positions** | **After Moving Microphone Positions** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2394c7724d611f0948f52540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c107aa7924d611f08caa5254005ef0f7.png) |

Android

iOS

Flutter

Kotlin

Java

```
val index = 3seatGridView.moveToSeat(index, object : TUIRoomDefine.ActionCallback {    override fun onSuccess() {        // Move seat successfully    }    override fun onError(error: TUICommonDefine.Error, message: String) {        // Failed to move seat    }})
```

```
int index = 3;seatGridView.moveToSeat(index, new TUIRoomDefine.ActionCallback() {    @Override    public void onSuccess() {      // Move seat successfully    }    @Override    public void onError(TUICommonDefine.Error error, String message) {       // Failed to move seat    }});
```

Swift

```
import RTCRoomEngineimport LiveStreamCorelet index = 3self.seatGridView.moveToSeat(index: destinationIndex) {    // Move seat successfully} onError: { code, message in     // Failed to move seat}
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';final destinationIndex = 3; final result = await controller.moveToSeat(destinationIndex);
```

### On-Mic User Leaving the Mic

#### User Becomes a Speaker and Then Leaves the Mic

User B becomes a speaker and then can call leaveSeat to leave the mic.

Android

iOS

Flutter

Kotlin

Java

```
seatGridView.leaveSeat()
```

```
seatGridView.leaveSeat();
```

swift

```
import RTCRoomEngineimport LiveStreamCoreseatGridView.leaveSeat() { } onError: { code, message in }
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';final controller = SeatGridController();final result = await controller.leaveSeat();
```

### 

### Anchor Inviting Audience to Speak

#### Anchor Sending Invite Speaking Request

Anchor A sends an invite speaking request to audience C. Audience C will receive Anchor A's invite speaking request in the onSeatRequestReceived callback.

Android

iOS

Flutter

Kotlin

Java

```
val seatIndex = 1; val userId = "userIdC"; val timeout = 60; seatGridView.takeUserOnSeatByAdmin(seatIndex, timeout, userId, object : VoiceRoomDefine.RequestCallback {    override fun onAccepted(userInfo: TUIRoomDefine.UserInfo) {        Log.i(TAG, "Invitation to become a speaker accepted")    }    override fun onRejected(userInfo: TUIRoomDefine.UserInfo) {        Log.i(TAG, "Invitation to become a speaker rejected")    }    override fun onCancelled(userInfo: TUIRoomDefine.UserInfo) {        Log.i(TAG, "Invitation to become a speaker cancelled")    }    override fun onTimeout(userInfo: TUIRoomDefine.UserInfo) {        Log.i(TAG, "Invitation to become a speaker timed out")    }    override fun onError(userInfo: TUIRoomDefine.UserInfo, error: TUICommonDefine.Error, message: String) {        Log.i(TAG, "Invitation to become a speaker error")    }})
```

```
val seatIndex = 1; val userId = "userIdC"; val timeout = 60; seatGridView.takeUserOnSeatByAdmin(seatIndex, userId, timeout, new VoiceRoomDefine.RequestCallback() {    @Override    public void onAccepted(TUIRoomDefine.UserInfo userInfo) {        Log.i(TAG, "Invitation to become a speaker accepted");    }    @Override    public void onRejected(TUIRoomDefine.UserInfo userInfo) {        Log.i(TAG, "Invitation to become a speaker rejected")    }    @Override    public void onCancelled(TUIRoomDefine.UserInfo userInfo) {        Log.i(TAG, "Invitation to become a speaker cancelled");    }    @Override    public void onTimeout(TUIRoomDefine.UserInfo userInfo) {        Log.i(TAG, "Invitation to become a speaker timed out");    }    @Override    public void onError(TUIRoomDefine.UserInfo userInfo, TUICommonDefine.Error error, String message) {        Log.i(TAG, "Invitation to become a speaker error");    }});
```

swift

```
import RTCRoomEngineimport LiveStreamCorelet seatIndex = 1let timeout = 60let userId = "userIdC" seatGridView.takeUserOnSeatByAdmin(index: seatIndex, timeout: timeout, userId: userId) { userInfo in    print("Invitation to become a speaker accepted")} onRejected: { userInfo in    print("Invitation to become a speaker rejected")} onCancelled: { userInfo in    print("Invitation to become a speaker cancelled")} onTimeout: { userInfo in    print("Invitation to become a speaker timed out")} onError: { userInfo, code, message in    print("Invitation to become a speaker error")}
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';const int seatIndex = 1;const String userId = 'userIdC'const int timeout = 60;final controller = SeatGridController();final result = await controller.takeUserOnSeatByAdmin(seatIndex, userId, timeout);if (result.code == TUIError.success) {                              switch (result.type) {                                  case RequestResultType.onAccepted:                                      debugPrint('Invitation to become a speaker accepted');                                      break;                                  case RequestResultType.onRejected:                                      debugPrint('Invitation to become a speaker rejected');                                      break;                                  case RequestResultType.onCancelled:                                      debugPrint('Invitation to become a speaker cancelled');                                      break;                                  case RequestResultType.onTimeout:                                      debugPrint('Invitation to become a speaker timed out');                                      break;                                  default:                                      break;                              }                        } else {                              debugPrint('Error in inviting to become a speaker');   }
```

#### Audience End Received Invite Speaking Request

Audience C will receive Anchor A's invite speaking request in the onSeatRequestReceived callback method.

Android

iOS

Flutter

Kotlin

Java

```
override fun onSeatRequestReceived(type: VoiceRoomDefine.RequestType, userInfo: TUIRoomDefine.UserInfo) {   if (type == VoiceRoomDefine.RequestType.INVITE_TO_TAKE_SEAT) {      Log.i(TAG, "Receive an invitation to become a speaker from the anchor: ${userInfo.userId}")   }}
```

```
@Overridepublic void onSeatRequestReceived(VoiceRoomDefine.RequestType type, TUIRoomDefine.UserInfo userInfo) {    if (type == VoiceRoomDefine.RequestType.INVITE_TO_TAKE_SEAT) {        Log.i(TAG, "Receive an invitation to become a speaker from the anchor: " + userInfo.userId);    }}
```

swift

```
import RTCRoomEngineimport LiveStreamCorefunc onSeatRequestReceived(type: SGRequestType, userInfo: TUIUserInfo) {   if type == .inviteToTakeSeat {      print("Receive an invitation to become a speaker from the anchor: \\(userInfo.userId)")   }}
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';// Create a listener Observer instancefinal controller = SeatGridController();final exampleObserver = ExampleObserver(); // Add observercontroller.addObserver(exampleObserver);class ExampleObserver extends SeatGridWidgetObserver {      ExampleObserver() {          super.onSeatRequestReceived = (type, userInfo) {          if (type == RequestType.inviteToTakeSeat) {              debugPrint('Receive an invitation to become a speaker from the anchor: ${userInfo.userId}');           }         };        }}
```

#### Audience Response to Invite Speaking Request

After Audience C receives the speaking request from the audience, they can call responseRemoteRequest to respond whether to agree to Anchor A's speaking request. Anchor A will receive callbacks for Audience C's agreement or rejection (onAccepted/onRejected).

Android

iOS

Flutter

Kotlin

Java

```
// Audience accepts the anchor's invitationseatGridView.responseRemoteRequest("", true, null);// Audience rejects the anchor's invitationseatGridView.responseRemoteRequest("", false, null);
```

```
// Audience accepts the anchor's invitationseatGridView.responseRemoteRequest("", true, null);// The audience rejects the anchor's invitationseatGridView.responseRemoteRequest("", false, null);
```

swift

```
import RTCRoomEngineimport LiveStreamCore// Audience accepts the anchor's invitationseatGridView.responseRemoteRequest("userId of anchor", true) {} onError: { code, message in }// Audience rejects the anchor's invitationseatGridView.responseRemoteRequest("userId of anchor", false, null) {} onError: { code, message in }
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';final controller = SeatGridController();const String userId = 'userId of anchor';// Audience accepts the anchor's invitationfinal result = await controller.responseRemoteRequest(userId, true);// The audience rejects the anchor's invitationfinal result = await controller.responseRemoteRequest(userId, false);
```

> **Notes:**If you customize the seat view, both anchors and audience can refresh the seat UI by listening to the Callback for Seat Information Changes.

### 

### Host Kick Member From Microphone

#### Audience Becomes a Speaker Successfully, Then the Anchor Removes the Audience From the Microphone

Audience B becomes a speaker successfully, then Anchor A removes Audience B from the microphone.

Android

iOS

Flutter

Kotlin

Java

```
val userId = "userIdB"seatGridView.kickUserOffSeatByAdmin(userId, null)
```

```
String userId = "userIdB";seatGridView.kickUserOffSeatByAdmin(userId, null);
```

swift

```
import RTCRoomEngineimport LiveStreamCorelet userId = "userIdB"seatGridView.kickUserOffSeatByAdmin(userId) {} onError: { code, message in }
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';const String userId = "userIdB";final controller = SeatGridController();final result = await controller.kickUserOffSeatByAdmin();
```

#### Audience Receives Callback for Being Removed From Microphone by Anchor

After Anchor A removes Audience B from the microphone, Audience B will receive the onKickedOffSeat callback.

Android

iOS

Flutter

Kotlin

Java

```
override fun onKickedOffSeat(inviterUser: UserInfo) {   Log.i(TAG, "Anchor removes speaker")}
```

```
@Overridepublic void onKickedOffSeat(TUIRoomDefine.UserInfo userInfo) {    Log.i(TAG, "Anchor removes speaker from mic");}
```

swift

```
import RTCRoomEngineimport LiveStreamCorefunc onKickedOffSeat(userInfo: TUIUserInfo) {    print("Anchor removes speaker from mic")}
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';// Create a listener Observer instancefinal controller = SeatGridController();final exampleObserver = ExampleObserver(); // Add observercontroller.addObserver(exampleObserver);class ExampleObserver extends SeatGridWidgetObserver {      ExampleObserver() {          super.onKickedOffSeat = (userInfo) {          debugPrint('Anchor kicks the speaker off the mic');         };        }}
```

> **Notes:**If you customize the seat view, both anchors and audience can refresh the seat UI by listening to the Callback for Seat Information Changes.

### 

### Room Owner Locks Seat

**Effect Preview**

| **Before Locking Seats** | **After Locking Seats** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1aa2e5d24d611f0b0b1525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1475eb724d611f0948f52540099c741.png) |

#### Location Lock

The anchor can lock a certain seat. Once locked, the seat will be banned and mic on/off operations will be unavailable.

Android

iOS

Flutter

Kotlin

Java

```
val index = 1val isLockSeat = trueval params = TUIRoomDefine.SeatLockParams().apply {   lockSeat = isLockSeat}seatGridView.lockSeat(index, params, null)
```

```
int index = 1;bool isLockSeat = true;TUIRoomDefine.SeatLockParams params = new TUIRoomDefine.SeatLockParams();params.lockSeat = isLockSeat;seatGridView.lockSeat(index, params, null);
```

swift

```
import RTCRoomEngineimport LiveStreamCorelet index = 1let isLockSeat = truelet params = TUISeatLockParams()params.lockSeat = isLockSeatseatGridView.lockSeat(index: index, lockMode: params) {} onError: { code, message in }
```

Dart

```
import 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';const int index = 1;const bool isLockSeat = truefinal params = TUISeatLockParams();params.lockSeat = isLockSeat;final controller = SeatGridController();final result = await controller.lockSeat(index, params);
```

### 

### Set Microphone Position List Layout

Custom Seat List Layout Effect Preview

| **Grid layout** | **Element layout** | **Vertical layout** | **Custom layout** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c183d92224d611f0b47352540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1e9ebc924d611f0948f52540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1c002cd24d611f0b47352540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1cf82e224d611f0b44b5254007c27c5.png) |

You can quickly set your microphone position list layout in the following ways.

Android

iOS

Flutter

kotlin

java

```
// Set grid layoutseatGirdView.setLayoutMode(VoiceRoomDefine.LayoutMode.GRID, null)// Set element layoutseatGirdView.setLayoutMode(VoiceRoomDefine.LayoutMode.FOCUS, null)// Set vertical layoutseatGirdView.setLayoutMode(VoiceRoomDefine.LayoutMode.VERTICAL, null)// Set custom layoutval layoutConfig = VoiceRoomDefine.SeatViewLayoutConfig().apply {     rowConfigs = ArrayList()     rowSpacing = dp2px(10); // Spacing between each line } // First line configuration val rowConfig1 = VoiceRoomDefine.SeatViewLayoutRowConfig().apply {     count = 3 // Number displayed in the first line     seatSize = VoiceRoomDefine.Size(dp2px(50), dp2px(50)) // Size of each microphone position view displayed in the first row     seatSpacing = dp2px(10) // Horizontal spacing between each seat in the first row     alignment = VoiceRoomDefine.SeatViewLayoutRowAlignment.CENTER // Alignment mode of seats in the first row } layoutConfig.rowConfigs.add(rowConfig1)// Second line configuration val rowConfig2 = VoiceRoomDefine.SeatViewLayoutRowConfig().apply {     count = 3 // Number displayed in the second line     seatSize = VoiceRoomDefine.Size(dp2px(50), dp2px(50)) // Size of each seat displayed in the second row     seatSpacing = dp2px(10) // Horizontal spacing between each seat in the second row     alignment = VoiceRoomDefine.SeatViewLayoutRowAlignment.SPACE_AROUND // Alignment mode of seats in the second row }     layoutConfig.rowConfigs.add(rowConfig2) seatGirdView.setLayoutMode(VoiceRoomDefine.LayoutMode.FREE, layoutConfig)
```

```
// Set grid layoutseatGirdView.setLayoutMode(VoiceRoomDefine.LayoutMode.GRID, null)// Set element layoutseatGirdView.setLayoutMode(VoiceRoomDefine.LayoutMode.FOCUS, null)// Set vertical layoutseatGirdView.setLayoutMode(VoiceRoomDefine.LayoutMode.VERTICAL, null)// Set free layoutVoiceRoomDefine.SeatViewLayoutConfig layoutConfig = new VoiceRoomDefine.SeatViewLayoutConfig();layoutConfig.rowConfigs = new ArrayList<>();layoutConfig.rowSpacing = dp2px(10); // Spacing between each line// First line configurationVoiceRoomDefine.SeatViewLayoutRowConfig rowConfig1 = new VoiceRoomDefine.SeatViewLayoutRowConfig();rowConfig1.count = 3; // Number displayed in the first linerowConfig1.seatSize = new VoiceRoomDefine.Size(dp2px(50), dp2px(50)); // Size of each microphone position view displayed in the first rowrowConfig1.seatSpacing = dp2px(10); // Horizontal spacing between each seat in the first rowrowConfig1.alignment = VoiceRoomDefine.SeatViewLayoutRowAlignment.CENTER; // Alignment mode of seats in the first rowlayoutConfig.rowConfigs.add(rowConfig1);// Second line configurationVoiceRoomDefine.SeatViewLayoutRowConfig rowConfig2 = new VoiceRoomDefine.SeatViewLayoutRowConfig();rowConfig2.count = 3; // Number displayed in the second rowrowConfig2.seatSize = new VoiceRoomDefine.Size(dp2px(50), dp2px(50)); // Size of each microphone position view displayed in the second rowrowConfig1.seatSpacing = dp2px(10); // Horizontal spacing between each seat in the second rowrowConfig2.alignment = VoiceRoomDefine.SeatViewLayoutRowAlignment.SPACE_AROUND; // Alignment mode of seats in the second rowlayoutConfig.rowConfigs.add(rowConfig2);seatGirdView.setLayoutMode(VoiceRoomDefine.LayoutMode.FREE, layoutConfig);
```

> **Notes:**Parameter settings for custom layout can be viewed in the parameter descriptions of [SeatViewLayoutRowConfig](https://www.tencentcloud.com/document/product/647/66793#a2174da5-9786-4f90-a09e-01b3d9a99a2f). The alignment mode can be referred to in the description of [SeatViewLayoutRowAlignment](https://www.tencentcloud.com/document/product/647/66793#b22ba27c-695a-4ea9-9739-7d18450a39b1). For the effect of the alignment mode, see the figure below (diagram of custom layout alignment mode).

swift

```
import LiveStreamCore// Set grid layoutseatGridView.setLayoutMode(layoutMode: .grid)// Set element layoutseatGridView.setLayoutMode(layoutMode: .focus)// Set vertical layoutseatGridView.setLayoutMode(layoutMode: .vertical)// Set custom layout// First line configurationlet rowConfig1 = SGSeatViewLayoutRowConfig(count: 3, // Number displayed in the first line                                           seatSpacing: 10, // Horizontal spacing between each seat in the first row                                           seatSize: CGSize(width: 50, height: 50), // Size of each microphone position view displayed in the first row                                           alignment: .center) // Alignment mode of seats in the first row   // Second line configurationlet rowConfig2 = SGSeatViewLayoutRowConfig(count: 3, // Number displayed in the second row                                           seatSpacing: 10, // Horizontal spacing between each seat in the second row                                           seatSize: CGSize(width: 50, height: 50), // Size of each microphone position view displayed in the second row                                           alignment: .spaceAround) // Alignment mode of microphone positions in the second row  let layoutConfig = SGSeatViewLayoutConfig(rowConfigs: [rowConfig1, rowConfig2],                                          rowSpacing: 10)seatGridView.setLayoutMode(layoutMode: .free, layoutConfig: layoutConfig)
```

> **Notes:**Parameter settings for custom layout can be viewed in the parameter descriptions of [SGSeatViewLayoutRowConfig](https://www.tencentcloud.com/document/product/647/66860#a2174da5-9786-4f90-a09e-01b3d9a99a2f). The alignment mode can be referred to in the description of [SGSeatViewLayoutRowAlignment](https://www.tencentcloud.com/document/product/647/66860#b22ba27c-695a-4ea9-9739-7d18450a39b1). For the effect of the alignment mode, see the figure below (diagram of custom layout alignment mode).

```
// API definitionvoid setLayoutMode(LayoutMode layoutMode, SeatWidgetLayoutConfig? layoutConfig);// API utilizationimport 'package:live_stream_core/live_stream_core.dart';// Set grid layoutcontroller.setLayoutMode(LayoutMode.grid, null); // Set element layoutcontroller.setLayoutMode(LayoutMode.focus, null); // Set vertical layoutcontroller.setLayoutMode(LayoutMode.vertical, null); // Set custom layoutfinal rowConfig = SeatWidgetLayoutRowConfig(            count: 2,            seatSpacing: 20.0,            seatSize: const Size(80, 80),            alignment: SeatWidgetLayoutRowAlignment.spaceBetween);final layoutConfig = SeatWidgetLayoutConfig(            rowConfigs: [rowConfig, rowConfig]);controller.setLayoutMode(LayoutMode.free, layoutConfig);
```

> **Notes:**Parameter settings for custom layout can be viewed in the parameter descriptions of [SeatWidgetLayoutRowConfig](https://www.tencentcloud.com/document/product/647/69245#a2174da5-9786-4f90-a09e-01b3d9a99a2f). The alignment mode can be referred to in the description of [SeatWidgetLayoutRowAlignment](https://www.tencentcloud.com/document/product/647/69245#b22ba27c-695a-4ea9-9739-7d18450a39b1). For the effect of the alignment mode, see the figure below (diagram of custom layout alignment mode).

| **Diagram of custom layout alignment mode** |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1e77e7624d611f0948f52540099c741.png) |

### 

### Custom Seat View

Android

iOS

Flutter

If you consider our default UI does not meet your requirements and you want to customize your own microphone position UI, you can quickly set your microphone position layout in the following ways and fully customize your own microphone position view UI.

kotlin

java

```
val adapter = object : VoiceRoomDefine.SeatViewAdapter {    override fun createSeatView(seatGridView: SeatGridView, seatInfo: TUIRoomDefine.SeatInfo): View {        return TestSeatInfoView(context, seatGridView, seatInfo)    }    override fun updateSeatView(seatGridView: SeatGridView,seatInfo: TUIRoomDefine.SeatInfo, seatView: View) {        (seatView as TestSeatInfoView).updateSeatView(seatGridView, seatInfo)    }    override fun updateUserVolume(seatGridView: SeatGridView, volume: Int, customSeatView: View) {        (customSeatView as TestSeatInfoView).updateUserVolume(seatGridView, volume)    }}seatGirdView.setSeatViewAdapter(adapter)class TestSeatInfoView constructor(context: Context, seatGirdView: SeatGridView, seatInfo: TUIRoomDefine.SeatInfo) : FrameLayout(context) {    init {        initializeView()    }    fun updateSeatView(seatGirdView: SeatGridView, seatInfo: TUIRoomDefine.SeatInfo) {        updateView(seatInfo) // Refresh the custom seat view UI    }    fun updateUserVolume(seatGirdView: SeatGridView, volume: Int) {        updateUserVolume(volume) // Refresh the volume change UI    }}
```

```
VoiceRoomDefine.SeatViewAdapter adapter = new VoiceRoomDefine.SeatViewAdapter() {    @Override    public View createSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo) {        return new TestSeatInfoView(getApplicationContext(), seatGridView, seatInfo);    }    @Override    public void updateSeatView(SeatGridView seatGridView, TUIRoomDefine.SeatInfo seatInfo,                                     View customSeatView) {        ((TestSeatInfoView) customSeatView).updateSeatView(seatGridView, seatInfo);    }    @Override    public void updateUserVolume(SeatGridView seatGridView, int volume, View customSeatView) {        ((TestSeatInfoView) customSeatView).updateUserVolume(seatGridView, volume);    }};seatGirdView.setSeatViewAdapter(adapter);public class TestSeatInfoView extends FrameLayout {    public TestSeatInfoView(@NonNull Context context, SeatGridView seatGirdView, TUIRoomDefine.SeatInfo seatInfo) {        super(context);        initView();    }    public void updateSeatView(SeatGridView seatGirdView, TUIRoomDefine.SeatInfo seatInfo) {        updateView(seatInfo);    }    public void updateUserVolume(SeatGridView seatGirdView, int volume) {        updateUserVolume(volume);    } }
```

If you consider our default UI does not meet your requirements and you want to customize your own microphone position UI, you can quickly set your microphone position layout in the following ways and fully customize your own microphone position view UI.

swift

```
import LiveStreamCoreclass TestSeatViewDelegate: SGSeatViewDelegate {    func seatGridView(_ view: SeatGridView, createSeatView seatInfo: TUISeatInfo) -> UIView? {      return TestSeatInfoView(seatGridView: view, seatInfo: seatInfo)    }        func seatGridView(_ view: SeatGridView, updateSeatView seatInfo: TUISeatInfo, seatView: UIView) {      if let seatView = seatView as? TestSeatInfoView {        seatView.updateSeatView(seatGridView: view, seatInfo: seatInfo)      }    }        func seatGridView(_ view: SeatGridView, updateUserVolume volume: Int, seatView: UIView) {      if let seatView = seatView as? TestSeatInfoView {        seatView.updateUserVolume(seatGridView: view, volume: volume)      }    }}seatGridView.setSeatViewDelegate(TestSeatViewDelegate())class TestSeatInfoView: UIView {    init(seatGridView: SeatGridView, seatInfo: TUISeatInfo) {        super.init(frame: .zero)        initializeView()    }    func updateSeatView(seatGridView: SeatGridView, seatInfo: TUISeatInfo) {        updateView(seatInfo) // Refresh the custom seat view UI    }    func updateUserVolume(seatGridView: SeatGridView, volume: Int) {        updateUserVolume(volume) // Refresh the volume change UI    }}
```

If you consider our default UI does not meet your requirements and you want to customize your own microphone position UI, you can implement the UI style of a specified microphone position through the parameter `seatWidetBuilder` of `SeatGridWidget`.

```
// Definition of seatWidetBuildertypedef SeatWidgetBuilder = Widget Function(        BuildContext context,        ValueNotifier<TUISeatInfo> seatInfoNotifier,    ValueNotifier<int> volumeNotifier);    // Usage exampleimport 'package:live_stream_core/live_stream_core.dart';import 'package:rtc_room_engine/rtc_room_engine.dart';SeatGridWidget(       controller: controller,       onSeatWidgetTap: (TUISeatInfo seatInfo) {          // debugPrint('click seatWidget index:${seatInfo.index}');       },       seatWidgetBuilder: (                   BuildContext context,                   ValueNotifier<TUISeatInfo> seatInfoNotifier,                   ValueNotifier<int> volumeNotifier) {                          // Return your custom seat component                     return Container();                   })
```

| **Default Microphone Position View** | **Custom Seat View Example** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1f38d2424d611f0a62e525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c22f671624d611f0b44b5254007c27c5.png) |

### 

### Extended Feature

Android

iOS

Flutter

If you need to expand other management features (such as mic management), see the [SeatGridView](https://www.tencentcloud.com/document/product/647/66793#) document.

If you need to expand other management features (such as mic management), see the [SeatGridView](https://www.tencentcloud.com/document/product/647/66860#) document.

If you need to expand other management features (such as mic management), see the [SeatGridWidget](https://www.tencentcloud.com/document/product/647/69245#) document.


---
*Source: [https://trtc.io/document/69845](https://trtc.io/document/69845)*
