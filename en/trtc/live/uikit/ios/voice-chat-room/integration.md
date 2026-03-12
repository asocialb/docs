# Integration

## Feature Overview

`TUILiveKit` is a comprehensive voice chat room component. After integration, you can quickly implement the following key modules:

| Host Preparation Page | Host Live Page | Live Stream List | Audience Viewing Page |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2dd6c975c06311f0a6c652540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d1c226bc06311f0a5e052540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d182830c06311f09a6b525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d1dd744c06311f0b9945254005ef0f7.png) |

## Prerequisites

### Activate Service

Before using **TUILiveKit**, please refer to [Activate Service](https://www.tencentcloud.com/document/product/647/60033) to get the TUILiveKit trial version or activate the paid version.

### Environment Requirements

- **Xcode**: Requires **Xcode 15**or a later version.
- **iOS**: Supports devices running **iOS 13.0**or a later version.
- **CocoaPods environment**: A CocoaPods environment must be installed. If you haven't installed it, please refer to the [CocoaPods installation guide](https://guides.cocoapods.org/using/getting-started.html), or follow these steps:
  - **Install CocoaPods using gem**: execute the `sudo gem install cocoapods` command in the terminal to install.

> **Note:**During the `sudo gem install cocoapods` installation process, you may be prompted to enter your computer's password. Enter the administrator password as prompted.

## Integrate TUIKit

### Step 1: Add the Component via CocoaPods

1. **Add Pod Dependencyï¼**
  - **If your project already has a Podfile**:

Add the `pod 'TUILiveKit'` dependency to your project's `Podfile`. For example:

```
target 'YourProjectTarget' do    # Other existing Pod dependencies...    # Add pod 'TUILiveKit' dependency  pod 'TUILiveKit'end
```

  - **If your project does not have a Podfile:**

Use the `cd` command in the terminal to navigate to your `.xcodeproj` directory, then run `pod init` to create a `Podfile`. After creation, add the `pod 'TUILiveKit'` dependency. For example:

```
# If your project directory is /Users/yourusername/Projects/YourProject# 1. cd to your .xcodeproj project directorycd /Users/yourusername/Projects/YourProject# 2. Run pod init. After this command completes, a Podfile will be generated.pod init# 3. Edit the generated Podfile to add the dependencytarget 'YourProjectTarget' do    # Add pod 'TUILiveKit' dependency  pod 'TUILiveKit'end
```

2. **Install the Component:**

In the `terminal`, `cd` to the directory containing your `Podfile`, then run:

```
pod install
```

### Step 2: Project Configuration

To use audio features, your app must request microphone permission. Add the following entries to your app's Info.plist file with appropriate usage descriptions. These descriptions are shown to users when the system requests permissions:

```
<key>NSMicrophoneUsageDescription</key><string>TUILiveKit requires access to your microphone. Enabling this allows recorded videos to have sound.</string>
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/31d1cdbcc06411f09a6b525400454e06.png)

## Complete Login

After code integration, the next step is to complete the login. All **TUILiveKit** features require a successful login to function properly, so ensure your parameters are configured correctly.

> **Note:**In the example code, the login API is called directly. However, in a real-world application, it is highly recommended that you call the **TUILiveKit** login service only after your own user authentication and other internal login processes are complete. This prevents potential business logic confusion or data inconsistency caused by calling the login service too early, and it better aligns with your existing user management system.

Swift

Objective-C

```
////  AppDelegate.swift//// 1. Import TUICoreimport TUICore// 2. The example code completes login in didFinishLaunchingWithOptions. Recommendation for you: call the login service after completing your own login service. func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {        // 3. Call the login API    TUILogin.login(1400000001,               // replace with the SDKAppID from the service console            userID: "denny",                 // replace with your UserID            userSig: "xxxxxxxxxxx") {        // You can calculate a UserSig in the console and fill it in this location      print("login success")    } fail: { (code, message) in      print("login failed, code: \\(code), error: \\(message ?? "nil")")    }        return true}
```

```
////  AppDelegate.m//// 1. Import TUICore#import <TUICore/TUILogin.h>// 2. The example code completes login in didFinishLaunchingWithOptions. Recommendation for you: call the login service after completing your own login service. - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {        // 3. Call the login API    [TUILogin login:1400000001        // replace with the SDKAppID from the service console             userID:@"denny"          // replace with your UserID            userSig:@"xxxxxxxxxxx"    // You can calculate a UserSig in the console and fill it in this location               succ:^{        NSLog(@"login success");    } fail:^(int code, NSString * _Nullable msg) {        NSLog(@"login failed, code: %d, error: %@", code, msg);    }];    return YES;}
```

**Login API Parameter Description**

| Parameter | Type | Description |
| --- | --- | --- |
| SDKAppID | Int | Get this from [TRTC console > Application management](https://console.trtc.io/app). |
| UserID | String | The unique ID for the current user. Must contain only English letters, numbers, hyphens, and underscores. |
| userSig | String | A ticket for Tencent Cloud authentication. Please note:**Development Environment**: You can use the local `GenerateTestUserSig.genTestSig` function to generate a UserSig or generate a temporary UserSig via the [UserSig Generation Tool](https://console.trtc.io/usersig).**Production Environment**: To prevent key leakage, you must use a server-side method to generate UserSig. For details, see [Generating UserSig on the Server](https://www.tencentcloud.com/document/product/647/35166).For more information, see [How to Calculate and Use UserSig](https://www.tencentcloud.com/document/product/647/35166). |

### Handling Login Exception Status [Optional]

**TUILogin** provides a login status callback mechanism to help you handle possible login exceptions, mainly including "**kicked offline**" and "**signature expired**" callbacks:

- **Kicked Offline:** If a user is kicked offline while online, the **SDK** will notify you via the `onKickedOffline` callback. At this point, you can display a UI prompt to the user and call `TUILogin.login` to login again.
- **Signature Expired:** If a user receives the `onUserSigExpired` callback while online, it means the **userSig** previously issued for that user has expired. If the user's login session on your backend is still valid, you can have your app request a new **userSig** from your backend and call `TUILogin.login` to renew the login session.

Swift

Objective-C

```
// YourLoginService represents the business module responsible for loginclass YourLoginService: NSObject {    // Listen to login status callback    func addLoginListener() {        TUILogin.add(self)    }    // Cancel listening to login status callback    func removeLoginListener() {        TUILogin.remove(self)    }}// Implement login callback TUILoginListenerextension YourLoginService: TUILoginListener {    // User kicked offline callback    func onKickedOffline() {      // Your business code: UI prompt user, then log in again    }         // User signature expired callback    func onUserSigExpired() {      // Your business code: If the current user is still logged in on your backend, you can have your app request a new userSig from your backend and call TUILogin.login to renew the login status.    }}
```

```
@interface YourLoginService() <TUILoginListener>// Listen to login status callback- (void)addLoginListener;// Cancel listening to login status callback- (void)removeLoginListener;@end@implementation YourLoginService// Listen to login status callback- (void)addLoginListener {    [TUILogin add:self];}// Cancel listening to login status callback- (void)removeLoginListener {    [TUILogin remove:self];}#pragma mark - TUILoginListener// User kicked offline callback- (void)onKickedOffline {    // Your business code: UI interaction prompts user, then log in again}// User signature expired callback- (void)onUserSigExpired {    // Your business code: UI interaction prompts user, then log in again}@end
```

## Next Steps

Congratulations! You have successfully integrated the **Voice Chat Room** component and completed login. Next, implement features such as **Host Live**, **Audience Viewing**, and **Live Room List**. See the table below for more details:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Live Streaming** | The complete process for hosts to create a voice chat room, including preparation and all live interactions. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74324) |
| **Audience Viewing** | Audience members can listen, request to join the mic, view bullet comments, and more after entering a voice chat room. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74328) |
| **Live Stream List** | Displays the list of available voice chat rooms and their details. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74326) |

## FAQs

### After executing pod install, why can't I find the latest version of TUILiveKit locally?

If you are unable to install the latest version of TUILiveKit, please follow these steps:

1. In the directory where the **Podfile** is located, delete `Podfile.lock` and `Pods`. You can choose to delete them manually or execute the following command in the terminal:

```
Podfile.lock
```

2. In the directory where Podfile is located, execute `pod install --repo-update`

```
// cd to the directory where Podfile is locatedpod install --repo-update
```

### Do I need to call the login method every time I enter a room?

No. You usually only need to complete one `TUILogin.login` call. We recommend associating `TUILogin.login`and `TUILogin.logout` with your own application's login business logic.

### Is there a sample configuration for the Podfile that I can refer to?

You can refer to the [GitHub TUILiveKit Example](https://github.com/Tencent-RTC/TUILiveKit/blob/main/iOS/Example/Podfile) project `Podfile` sample file.

## Contact Us

If you have any questions or suggestions during running the demo or usage, join our [Telegram technical group](https://t.me/+EPk6TMZEZMM5OGY1?s_url=https%3A%2F%2Ftrtc.io) or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/60334](https://trtc.io/document/60334)*
