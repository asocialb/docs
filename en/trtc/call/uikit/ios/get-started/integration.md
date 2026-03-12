# Integration

This document describes how to rapidly integrate the TUICallKit component. You can complete the following key steps within 10 minutes and obtain a complete audio and video call interface.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4bad7c6eb0bd11f0995e525400454e06.png)

## Preparations

### Environment Requirements

- **iOS system version requirements:**iOS 13.0 and above.
- **Development tool version requirements:**Xcode 13.0 and above,Xcode 15 and above may encounter Sandbox errors. Please refer to [[Sandbox Issue Solutions](https://www.tencentcloud.com/document/product/647/51023#e24c3216-a8ee-455e-8d46-89d7f8143718)] for fixes.
- **Dependency management tool requirements:**CocoaPods environment setup
- **Device requirements:** Apple mobile devices such as iPhone and iPad with iOS 13.0 or later (ensure the app can be properly installed and run).

### Service Activation

Please refer to the [Service Activation](https://www.tencentcloud.com/document/product/647/59832) documentation to obtain your `SDKAppID` and `SDKSecretKey`. These credentials will be required in the subsequent [Login](#e3e0b27f-96fd-45d4-8a29-b7cc3161d03e) steps.

## Implementation

### Step 1.Importing Components

1. Add Pod dependency:
  - If the project has an existing Podfile file.

Add the `pod 'TUICallKit_Swift'` dependency in your project's `Podfile` file. For example:

```
  target 'YourProjectTarget' do      pod 'TUICallKit_Swift'  end
```

  - If the project has no Podfile file.

Enter your `.xcodeproj` directory in the terminal, then execute the `pod init` command to create a `Podfile` file. After creation, add the `pod 'TUICallKit_Swift'` dependency in your `Podfile` file. For example:

```
// 1cd /Users/yourusername/Projects/YourProject// 2pod init// 3 In the generated Podfile file  target 'YourProjectTarget' do      pod 'TUICallKit_Swift'  end
```

2. Install components:

Enter the directory where the `Podfile` file is located in the terminal, then run the following command to install components.

```
pod update
```

### Step 2.Project Configuration

To ensure the audio and video features function correctly, your application needs to request access to the microphone and camera. Please add the following two privacy usage descriptions to your project's `Info.plist` fileï¼these descriptions will be displayed to the user when the system initially prompts for permission.

```
<key>NSCameraUsageDescription</key><string>TUICallKitApp needs access to your camera, and it can be used for functions such as Video Call, Group Video Call.</string><key>NSMicrophoneUsageDescription</key><string>TUICallKitApp needs access to your microphoneï¼and it can be used for functions such as Audio Call, Group Audio Call, Video Call, Group Video Call.</string>
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/55667c9eb30311f09e195254007c27c5.png)

### Step 3.Login

Add the following code in your project. It enables logging in to the TUI component by calling relevant APIs in TUICore. This step is critical. Only after logging in successfully can you use the features provided by TUICallKit properly.

**login**

iOS (Swift)

iOS (Objective-C)

```
import TUICoreimport TUICallKit_Swiftfunc application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {            let userID = "denny"       // Please replace with your UserId    let sdkAppID: Int32 = 0    // Please replace it with the SDKAppID obtained from the console.    let secretKey = "****"     // Please replace it with the SecretKey obtained from the console.    let userSig = GenerateTestUserSig.genTestUserSig(userID: userID, sdkAppID: sdkAppID, secretKey: secretKey)    TUILogin.login(sdkAppID, userID: userID, userSig: userSig) {      print("login success")    } fail: { code, message in      print("login failed, code: \\(code), error: \\(message ?? "nil")")    }    return true}
```

```
#import <TUICore/TUILogin.h>#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {        NSString *userID = @"denny";     // Please replace with your UserID    int sdkAppID = 0;                // Please replace it with the SDKAppID obtained from the console.    NSString *secretKey = @"****";   // Please replace it with the SecretKey obtained from the console.    NSString *userSig = [GenerateTestUserSig genTestUserSigWithUserID:userID sdkAppID:sdkAppID secretKey:secretKey];    [TUILogin login:sdkAppID             userID:userID            userSig:userSig               succ:^{        NSLog(@"login success");    } fail:^(int code, NSString * _Nullable msg) {        NSLog(@"login failed, code: %d, error: %@", code, msg);    }];        return YES;}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | only allow a combination of uppercase and lowercase letters (a-z A-Z), numbers (0-9), underline and hyphen |
| sdkAppId | int | The unique ID assigned to your application when you [Tencent Real-Time Communication (TRTC) Console](https://console.tencentcloud.com/trtc). |
| secretKey | String | The SDKSecretKey of the audio and video application created in the [Tencent Real-Time Communication (TRTC) Console](https://console.tencentcloud.com/trtc). |
| userSig | String | A security signature used for user login authentication, confirming user authenticity and preventing malicious attacks from stealing your cloud service usage rights. |

> **Note:****Development environment**: If you are in the local development and debugging stage, you can adopt the local `GenerateTestUserSig.genTestSig` function to generate userSig. In this method, the secretKey is very easy to decompile and reverse. Once your key is leaked, attackers can steal your Tencent Cloud traffic.**Production environment**: If your project is ready to go live, implement [server-side generation of UserSig](https://www.tencentcloud.com/document/product/647/35166) via the server.

### Step 4.Set Nickname and Avatar  [Optional]

After a successful login, you can call the `setSelfInfo` function to set your nickname and avatar. The set nickname and avatar will be displayed on the caller/callee interface.

**setSelfInfo**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_SwiftTUICallKit.createInstance().setSelfInfo(nickname: "jack", avatar: "https:/****/user_avatar.png") {} fail: { code, message in}
```

```
#import <TUICore/TUILogin.h>#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>NSString *nickname = @"jack";NSString *avatar = @"https:/****/user_avatar.png";[[TUICallKit createInstance] setSelfInfo:nickname avatar:avatar callback:nil];
```

| Parameter | Type | Description |
| --- | --- | --- |
| nickname | String | Target user's nickname |
| avatar | String | Target user's avatar |

### Step 5.Initiating a Call

The caller initiates a call by invoking the `calls` function and specifying the media type (voice or video) and the callee's User ID list (userIdList). The calls interface supports both one-to-one and group calls. A one-to-one call is initiated when the userIDList contains only a single User ID; a group call is initiated when it contains multiple User IDs.

**Note:**The [calls](https://www.tencentcloud.com/document/product/647/51011#calls) interface cannot be written in the `viewDidLoad` method; it should be called in the button's click event or other user interaction response methods.

**calls**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_Swift// Trigger single-person voice callTUICallKit.createInstance().calls(userIdList: ["mike"], callMediaType: .audio, params: nil) {} fail: { code, message in}
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>#import <RTCRoomEngine/TUICallEngine.h>[[TUICallKit createInstance] calls:@[@"mike"] callMediaType:TUICallMediaTypeAudio params:NULL succ:^{} fail:^(int code, NSString * _Nullable errMsg) {}];
```

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | [String] | Target user ID list |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54902#TUICallMediaType) | Media type of the call, such as video call, voice call |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54902#TUICallParams) | Call extension parameters, such as room number, call invitation timeout, offline push custom content |

### Step 6.Answering a Call

Once the callee successfully logs in, the caller can initiate a call, and the callee will receive the call invitation, accompanied by a ringtone and vibration.

## More Features

### Enabling Floating Window

You can enable/disable the floating window feature by calling `enableFloatWindow`. This feature should be enabled when initializing the TUICallKit component, with the default status being Off (false).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b61fb350b0b711f0bb7b525400bf7822.png)

**enableFloatWindow**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_SwiftTUICallKit.createInstance().enableFloatWindow(enable: true)
```

```
[[TUICallKit createInstance] enableFloatWindow:YES];
```

**Details:** false by default, the floating window button in the top-left corner of the call interface is hidden. Set to true to display the button and enable the feature.

### Enabling Banner

You can enable or disable the incoming call banner functionality by calling the `enableIncomingBanner` API: by default (disabled), the callee will immediately display the full-screen call interface upon receiving an invitation, while enabling it will show a notification banner first, followed by launching the full-screen call interface as required.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2e5d86bb0b711f0a6a2525400e889b2.png)

**enbalecomingBanner**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_SwiftTUICallKit.createInstance().enableIncomingBanner(enable: true)
```

```
[[TUICallKit createInstance] enableIncomingBanner:YES];
```

**Details:** Default false. When the callee receives an invitation, the full-screen call waiting interface pops up by default. When enabled, a banner is shown first, then the full-screen call interface is pulled up as needed.

### Multi-Person Calling

When the caller uses the `calls` method to initiate a call, if the list of called users exceeds one person, it is automatically recognized as a multi-person call. Other members can then join this multi-person call using the `join` method.

- **Initiating a Multi-person Call:** When the `calls` method is used to initiate a call, if the callee User ID list (userIdList) contains more than one user, it will be automatically deemed a multi-person call.

**calls**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_SwiftTUICallKit.createInstance().calls(userIdList: ["mike", "tate"], callMediaType: .audio, params: nil) {} fail: { code, message in}
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>#import <RTCRoomEngine/TUICallEngine.h>[[TUICallKit createInstance] calls:@[@"mike", @"tate"] callMediaType:TUICallMediaTypeAudio params:NULL succ:^{} fail:^(int code, NSString * _Nullable errMsg) {}];
```

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | [String] | Target user ID list |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54902#TUICallMediaType) | Media type of the call, such as video call, voice call |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54902#TUICallParams) | Call extension parameters, such as room number, call invitation timeout, offline push custom content |

- **Joining a Multi-person Call:** You can use the `join` method to enter the specified multi-person call.

**join**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_SwiftTUICallKit.createInstance().join(callId: "")
```

```
[[TUICallKit createInstance] joinWithCallId: @"***"];
```

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | The unique ID for this call. |

### Language Settings

- **Supported Languages:** We currently support Simplified Chinese, Traditional Chinese, English, Japanese, and Arabic.
- **Switching Languages:** By default, the language of TUICallKit is consistent with the mobile operating system's language setting. To switch the language, you can use the `TUIGlobalization.setPreferredLanguage` method.

**setLanguage**

iOS (Swift)

```
import TUICorefunc steLanguage() {    TUIGlobalization.setPreferredLanguage("en")}
```

| Parameter | Type | Description |
| --- | --- | --- |
| language | String | "zh-Hans": Simplified Chinese."zh-Hant": Traditional Chinese."en": English."ar" : Arabic. |

> **Noteï¼**If you need to set up other languages, please contact us at **info_rtc@tencent.com** for assistance.

### Ringtone Setting

You can configure the default ringtone, incoming call silent mode, and offline push ringtone using the following methods:

- **Method 1:** If you include the TUICallKit component via source code, you can set the default ringtone by replacing the corresponding resource files ([the ringtone played when initiating a call](https://github.com/Tencent-RTC/TUICallKit/blob/main/iOS/TUICallKit_Swift/Resources/AudioFile/phone_dialing.m4a) and [the ringtone played when receiving a call](https://github.com/Tencent-RTC/TUICallKit/blob/main/iOS/TUICallKit_Swift/Resources/AudioFile/phone_ringing.mp3)) .
- **Method 2:** Use the `setCallingBell` interface to set the incoming call ringtone received by the callee.

**setCallingBell**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_SwiftTUICallKit.createInstance().setCallingBell(filePath: "***/callingBell.mp3")
```

```
[[TUICallKit createInstance] setCallingBell:@"***/callingBell.mp3"];
```

**Details:** Only local file paths can be imported here. You must ensure that the file directory is accessible to the application. The ringtone setting is bound to the device; therefore, replacing the user will not affect the ringtone. To restore the default ringtone, simply pass an empty `filePath`.

| Parameter | Type | Description |
| --- | --- | --- |
| filePath | String | Ringtone file path |

- **Incoming call silent mode:** You can set mute mode through [enableMuteMode](https://www.tencentcloud.com/document/product/647/51005#enableMuteMode).

**enableMuteMode**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_SwiftTUICallKit.createInstance().enableMuteMode(enable: true)
```

```
[TUICallKit createInstance] enableMuteMode: YES];
```

**Details:** When turned on, incoming call requests will not trigger ring.

- **Custom offline push ringtone:**

**TUIOfflinePushInfo Parameter configuration description**

iOS (Swift)

iOS (Objective-C)

```
import TUICallKit_Swiftlet params = TUICallParams()let pushInfo: TUIOfflinePushInfo = TUIOfflinePushInfo()pushInfo.title = "TUICallKit"pushInfo.desc = "TUICallKit.have.new.invitation"pushInfo.iOSPushType = .apnspushInfo.ignoreIOSBadge = falsepushInfo.iOSSound = "phone_ringing.mp3"pushInfo.androidSound = "phone_ringing"// OPPO must set ChannelID to receive push message, this channelID needs to be consistent with that in the consolepushInfo.androidOPPOChannelID = "tuikit"// FCM channel ID, you need to change PrivateConstants.java and set "fcmPushChannelId"pushInfo.androidFCMChannelID = "fcm_push_channel"// VIVO message type: 0-push message, 1-system message (high delivery rate)pushInfo.androidVIVOClassification = 1// HuaWei message type: https://developer.HuaWei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835pushInfo.androidHuaWeiCategory = "IM"params.userData = "User Data"params.timeout = 30params.offlinePushInfo = pushInfoTUICallKit.createInstance().call(userId: "123456", callMediaType: .audio, params: params) {} fail: {    code, message in }
```

```
[TUICallKit createInstance] call:@"mike's id" params:[self getCallParams] callMediaType:TUICallMediaTypeVideo];- (TUICallParams *)getCallParams {    TUIOfflinePushInfo *offlinePushInfo = [self createOfflinePushInfo];    TUICallParams *callParams = [TUICallParams new];    callParams.offlinePushInfo = offlinePushInfo;    callParams.timeout = 30;    return callParams;}+ (TUIOfflinePushInfo *)createOfflinePushInfo {    TUIOfflinePushInfo *pushInfo = [TUIOfflinePushInfo new];    pushInfo.title = @"";    pushInfo.desc = TUICallingLocalize(@"TUICallKit.have.new.invitation");    pushInfo.iOSPushType = TUICallIOSOfflinePushTypeAPNs;    pushInfo.ignoreIOSBadge = NO;    pushInfo.iOSSound = @"phone_ringing.mp3";    pushInfo.AndroidSound = @"phone_ringing";    // OPPO must set ChannelID to receive push message, this channelID needs to be consistent with that in the console    pushInfo.AndroidOPPOChannelID = @"tuikit";    // FCM channel ID, you need to change PrivateConstants.java and set "fcmPushChannelId"    pushInfo.AndroidFCMChannelID = @"fcm_push_channel";    // VIVO message type: 0-push message, 1-system message (high delivery rate)    pushInfo.AndroidVIVOClassification = 1;    message type: https://developer.HuaWei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835    pushInfo.AndroidHuaWeiCategory = @"IM";    return pushInfo;}
```

**Details:** VoIP push does not support custom push ringtones. APNs push allows setting the iOSSound field in the [offlinePushInfo](https://www.tencentcloud.com/document/product/647/54902#TUIOfflinePushInfo) of params when calling the call interface during a phone call. iOSSound should be passed with the audio filename.

> **Note:**Offline Push Sound settings (only applicable to iOS). To customize iOSSound, first link the voice file to the Xcode project, then set the audio filename (with extension) to iOSSound.Ringtone duration should be less than 30s.

## Customizing Your UI

### Replace Icon Button

You can directly replace the icons under the [Resources\\Assets.xcassets](https://github.com/Tencent-RTC/TUICallKit/tree/main/iOS/TUICallKit_Swift/Resources/Assets.xcassets) folder to ensure the icon color and style remain consistent across the entire App. Below lists the basic feature buttons. You can replace the corresponding icons to fit your own business scenario.

Commonly Used Icon File Name List

| Icon | File name | Description |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b11b307b0b811f0995e525400454e06.png) | icon_dialing.png | Answer incoming call icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b167b73b0b811f099275254005ef0f7.png) | icon_hangup.png | Hang Up Call icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b14bf96b0b811f0bd1d5254001c06ec.png) | icon_mute_on.png | Turn off the mic icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b12b468b0b811f0bb7b525400bf7822.png) | icon_handsfree.png | Turn off the speaker icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b12f13db0b811f0bb7b525400bf7822.png) | icon_camera_off.png | Camera Off icon |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0bb5dec9b0b911f099275254005ef0f7.png) | icon_add_user.png | Invite user icon during call |

## FAQs

**Due to business needs, we need the TUICallKit source code. However, every time we update the pod, it's overwritten, resulting in loss. How can we fix this?**

1. You can fork the [TUICallKit repository](https://github.com/Tencent-RTC/TUICallKit/tree/main) to your GitHub/Gitee account.
2. Reference it in your project using the local [pod](https://guides.cocoapods.org/using/the-podfile.html) method. The sample code is as follows:

```
pod 'TUICallKit_Swift', :path=>"your TUICallKit_Swift.podspec path"
```

**Does TUICallKit support running in the background?**

**Yes,** if you need relevant functions to continue running when the application enters the background, select the current engineering project, go to the **Capabilities** tab, and under the **Background Modes section**, check **Audio, AirPlay, and Picture in Picture**, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/051e204dc5bc11f0a2c65254005ef0f7.png)

If you encounter problems during integration and use, see [FAQs](https://www.tencentcloud.com/document/product/647/51023).

## Contact Us

If you have any suggestions or feedback, please contact `info_rtc@tencent.com`.


---
*Source: [https://trtc.io/document/50992](https://trtc.io/document/50992)*
