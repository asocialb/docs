# Custom Ringtone

This article explains how to replace the incoming call ringtone for TUICallKit, which includes **application ringtone** and **offline push ringtone**.

## Setting application Ringtone

There are two ways to set the application ringtone:

#### 1. Replace Audio File

If you integrate the TUICallKit component via source code dependency, you can achieve the goal of replacing the ringtone by swapping out the audio files under the `Resources\\AudioFile` folder:

| File Name | Use |
| --- | --- |
| phone_dialing.mp3 | Ringtone when initiating a call |
| phone_ringing.mp3 | Ringtone when receiving a call |

#### 2. Call Ringtone Interface

You can also set the incoming call ringtone via the [setCallingBell](https://www.tencentcloud.com/document/product/647/51011#setcallingbell) interface.

Swift

Objective-C

```
import TUICallKit_SwiftTUICallKit.createInstance().setCallingBell(filePath: "")
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>[[TUICallKit createInstance] setCallingBellWithFilePath:@""];
```

## Set Mute Mode

If you do not require a ringtone, you can set the mute mode via [enableMuteMode](https://www.tencentcloud.com/document/product/647/51011#enablemutemode) interface.

Swift

Objective-C

```
import TUICallKit_SwiftTUICallKit.createInstance().enableMuteMode(enable: true)
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>[[TUICallKit createInstance] enableMuteModeWithEnable:YES];
```

## Set Offline Push Ringtone

VoIP push does not support custom push ringtones. APNs push can be set by specifying the iOSSound field in the offlinePushInfo params when making a call via the Call Interface. iOSSound should be passed the audio file name.

> **Note:**Offline push sound settings (only effective for iOS), to customize iOSSound, you first need to link the audio file into the Xcode project, then set the audio file name (with extension) to iOSSound.Ringtone duration should be less than 30s.

Swift

Objective-C

```
import TUICallKit_Swiftimport TUICallEnginelet pushInfo: TUIOfflinePushInfo = TUIOfflinePushInfo()pushInfo.title = ""pushInfo.desc = "You have a new call"pushInfo.iOSPushType = .apnspushInfo.ignoreIOSBadge = falsepushInfo.iOSSound = "phone_ringing.mp3"pushInfo.androidSound = "phone_ringing"// OPPO must set a ChannelID to receive push messages. This channelID needs to be the same as the console.pushInfo.androidOPPOChannelID = "tuikit"// FCM channel ID, you need change PrivateConstants.java and set "fcmPushChannelId"pushInfo.androidFCMChannelID = "fcm_push_channel"// VIVO message type: 0-push message, 1-System message(have a higher delivery rate)pushInfo.androidVIVOClassification = 1// HuaWei message type: https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835pushInfo.androidHuaWeiCategory = "IM"let params = TUICallParams()params.userData = "User Data"params.timeout = 30params.offlinePushInfo = pushInfoTUICallKit.createInstance().call(userId: "123456", callMediaType: .audio, params: params) {} fail: { code, message in}
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>#import <TUICallEngine/TUICallEngine.h>- (TUICallParams *)getCallParams {    TUIOfflinePushInfo *offlinePushInfo = [self createOfflinePushInfo];    TUICallParams *callParams = [TUICallParams new];    callParams.offlinePushInfo = offlinePushInfo;    callParams.timeout = 30;    return callParams;}- (TUIOfflinePushInfo *)createOfflinePushInfo {    TUIOfflinePushInfo *pushInfo = [TUIOfflinePushInfo new];    pushInfo.title = @"";    pushInfo.desc = @"You have a new call";    pushInfo.iOSPushType = TUICallIOSOfflinePushTypeAPNs;    pushInfo.ignoreIOSBadge = NO;    pushInfo.iOSSound = @"phone_ringing.mp3";    pushInfo.AndroidSound = @"phone_ringing";    // OPPO must set a ChannelID to receive push messages. This channelID needs to be the same as the console.    pushInfo.AndroidOPPOChannelID = @"tuikit";    // FCM channel ID, you need change PrivateConstants.java and set "fcmPushChannelId"    pushInfo.AndroidFCMChannelID = @"fcm_push_channel";    // VIVO message type: 0-push message, 1-System message(have a higher delivery rate)    pushInfo.AndroidVIVOClassification = 1;    // HuaWei message type: https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835    pushInfo.AndroidHuaWeiCategory = @"IM";    return pushInfo;}[[TUICallKit createInstance] callWithUserId:@"123456"                              callMediaType:TUICallMediaTypeAudio                                     params:[self getCallParams] succ:^{} fail:^(int code, NSString * _Nullable errMsg) {}];C
```


---
*Source: [https://trtc.io/document/59846](https://trtc.io/document/59846)*
