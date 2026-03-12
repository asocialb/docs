# Integration

This article will introduce how to complete the integration of the `TUIRoomKit` Component in the shortest time. By following this document, you will complete the following key steps within an hour and ultimately obtain an audio/video conference function with a complete UI interface.

## Environment preparation

iOS 13.0 and higher.

Xcode 12.0 and higher.

Swift 4.2 and higher.

## Step 1: Activate the service

Before initiating a meeting with TUIRoomKit, you need to activate the exclusive multi-person audio and video interaction service for TUIRoomKit on the console. For specific steps, please refer to [Activate Service](https://www.tencentcloud.com/document/product/647/59973#).

## Step 2: Integrate the TUIRoomKit Component

1. Add the following dependencies to your Podfile file.

```
pod 'TUIRoomKit'
```

2. Execute the following command to install the Component.

```
pod install
```

> **Note:**If you cannot install the latest version of TUIRoomKit, execute the following command to update the local CocoaPods repository list.pod repo update

## Step 3: Project Configuration

To use the audio and video functions, you need to authorize the use of microphone, camera and photo album. Add the following items to the App's Info.plist, corresponding to the prompt messages for the microphone, camera, and photo album when the system pops up the authorization dialog box.

```
<key>NSCameraUsageDescription</key><string>TUIRoom needs access to your Camera permission</string><key>NSMicrophoneUsageDescription</key><string>TUIRoom needs access to your Mic permission</string><key>NSPhotoLibraryUsageDescription</key><string>TUIRoom needs access to your Photo Library</string>
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9199c439522211eeabd75254005810a4.png)

## Step 4: Log in

Add the following code to your project. Its function is to complete the initialization of TUI components by calling the relevant interfaces in TUICore. This step is very critical, because all functions of TUIRoomKit can only be used normally after successful login, so please be patient and check whether the relevant parameters are configured correctly:

Swift

OC

```
import TUICoreTUILogin.login(1400000001,                        // Please replace with the SDKAppID obtained in step 1            userID: "998",                        // Please replace with your UserID           userSig: "xxxxxxxxxx") {               // You can calculate a UserSig in the Console and fill it in this position    print("login success")} fail: { (code, message) in    print("login failed, code: \\(code), error: \\(message ?? "nil")")}
```

```
#import "TUICore/TUILogin.h"[TUILogin login:1400000001                      // Please replace with the SDKAppID obtained in step 1         userID:@"998"                          // Please replace with your UserID        userSig:@"xxxxxxxxxx" succ:^{           // You can calculate a UserSig in the Console and fill it in this position    NSLog(@"login,success");                    } fail:^(int code, NSString * _Nullable msg) {    NSLog(@"login,failed,code:%d,msg:%@",code,msg);}];
```

**Parameter Description**
Here is a detailed introduction to the key parameters used in the login function:

- **SDKAppID**ï¼You have already obtained it in [Activate the service](https://www.tencentcloud.com/document/product/647/54842#.E6.AD.A5.E9.AA.A4.E4.B8.80.EF.BC.9A.E5.BC.80.E9.80.9A.E6.9C.8D.E5.8A.A1), so it will not be repeated here.
- **UserID**ï¼The ID of the current user, string type, only allows to contain English letters (a-z and A-Z), numbers (0-9), hyphens (-), and underscores (_).
- **UserSig**ï¼Encrypt the SDKAppID, UserID, etc. with the SDKSecretKey obtained in [Activate the service](https://www.tencentcloud.com/document/product/647/54842#.E6.AD.A5.E9.AA.A4.E4.B8.80.EF.BC.9A.E5.BC.80.E9.80.9A.E6.9C.8D.E5.8A.A1) to get the UserSig, which is a ticket for authorization and is used for Tencent Cloud to recognize whether the current user can use the TRTC service. You can create a temporarily available UserSig through the [UserSig Tools](https://console.trtc.io/usersig) through the project sidebar in the console.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/561066c5e10d11ee9f745254008eb8a8.png)

- For more information, please refer to the [UserSig related](https://www.tencentcloud.com/document/product/647/35166#).

## Step 5: The host start a quick conference

The main conference page is ConferenceMainViewController. After logging in, you only need to create and navigate to ConferenceMainViewController according to the following example to initiate a quick conference.

Swift

OC

```
import TUIRoomKit// CreateConferenceViewController is your own ViewControllerclass CreateConferenceViewController: UIViewController {    func quickStartConferenceAction() {        let params = StartConferenceParams(roomId: "123456") // replace "123456" with your conference ID        let conferenceViewController = ConferenceMainViewController()        conferenceViewController.setStartConferenceParams(params: params)                navigationController?.pushViewController(conferenceViewController, animated: true)     } }
```

```
#import <TUIRoomKit/TUIRoomKit-Swift.h>// CreateConferenceViewController is your own ViewController@interface CreateConferenceViewController ()@end@implementation CreateConferenceViewController- (void)quickStartConferenceAction {    // replace "123456" with your conference ID    StartConferenceParams *params = [[StartConferenceParams alloc] initWithRoomId: @"123456"];      ConferenceMainViewController *conferenceViewController = [[ConferenceMainViewController alloc] init];        [conferenceViewController setStartConferenceParams:params];             [self.navigationController pushViewController:conferenceViewController animated:YES];}@end
```

## Step 6: Members join the conference

Create and navigate to ConferenceMainViewController according to the following example to join a conference.

Swift

OC

```
import TUIRoomKit// EnterConferenceViewController is your own ViewControllerclass EnterConferenceViewController: UIViewController {    private func joinConferenceAction() {        // replace "123456" with conference ID you want to join        let params = JoinConferenceParams(roomId: "123456")        let conferenceViewController = ConferenceMainViewController()        conferenceViewController.setJoinConferenceParams(params: params)        navigationController?.pushViewController(conferenceViewController, animated: true)    } }
```

```
#import <TUIRoomKit/TUIRoomKit-Swift.h>// EnterConferenceViewController is your own ViewController@interface EnterConferenceViewController ()@end@implementation EnterConferenceViewController- (void)joinConferenceAction {    // replace "123456" with conference ID you want to join    JoinConferenceParams *params = [[JoinConferenceParams alloc] initWithRoomId: @"123456"];      ConferenceMainViewController *conferenceViewController = [[ConferenceMainViewController alloc] init];        [conferenceViewController setJoinConferenceParams:params];              [self.navigationController pushViewController:conferenceViewController animated:YES];}@end
```

> **Note:****When using OC for access, TUIRoomKit needs to be imported into the bridge file.**#import <TUIRoomKit/TUIRoomKit-Swift.h>

| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cf07da40054a11efa7e752540052a3fc.jpg) Conference main interface | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d9db6172054a11efa2e5525400488742.jpg) User list |
| --- | --- |

## Common Problems

If you encounter problems when using TUIRoomKit, please check the [FAQ document](https://www.tencentcloud.com/document/product/647/54895#) first.

## Suggestions and Feedback

If you have any suggestions or feedback, please contact info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/54842](https://trtc.io/document/54842)*
