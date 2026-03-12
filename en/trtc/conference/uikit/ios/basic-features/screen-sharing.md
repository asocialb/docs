# Screen Sharing

This document will introduce the `TUIRoomKit` screen sharing features in detail and help you better master the operation of screen sharing related features during `TUIRoomKit` meetings. With this document, you can make full use of TUIRoomKit's features to achieve high-quality audio and video conferencing.  If the UI interaction of TUIRoomKit does not meet your product requirements, and you have your own interactions and business logic to customise the screen sharing related interactions, you can access the TUIRoomEngineSDK related to the call to achieve your needs.

## Function

TUIRoomKit supports screen sharing, which allows users to share their screen after entering a room, and other members of the room can view the screen being shared. This article describes in detail the functionality of this feature and explains how to use it in TUIRoomKit components.

## Instructions for use

After entering the room, users of `Android&iOS&Flutter` side can achieve the screen sharing operation by clicking the sharing button on the bottom toolbar.

| **Screen Sharing** |  |  |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/38086f23c1a711efae1f525400bdab9d.png) |  |  |

### Feature Access

When accessing the screen sharing feature, you may need to do some configuration. See Configuration methods for different platforms:

Android

iOS

Flutter

Due to the change of the privacy policy of Android system, if you use screen recording and other functions in Android 10 and above Apps, you need to do it in the Foreground Service, otherwise the system will report an error or the App will be terminated by the system when recording/screen sharing. In our component, this Android Foreground Service will be enabled for you automatically, you just need to click the screen sharing button and agree to the relevant privacy policy to share.

The code for Android Foreground Service can be found in our [code examples](https://github.com/Tencent-RTC/TUIRoomKit/blob/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/common/KeepAliveService.java#L36).

Cross-app screen sharing on iOS requires the addition of the Extension recording process to work with the main App process for push streaming.The Extension recording process is created by the system when it needs to record a screen and is responsible for receiving screen images captured by the system. Therefore, you need to:

1. create an App Group and configure it in XCode (optional). The purpose of this step is to allow the Extension screen recording process to communicate across processes with the main App process.
2. In your project, create a new Target for Broadcast Upload Extension and integrate [TXLiteAVSDK_ReplayKitExt.framework](https://trtc.io/sdkDownload?id=conference), which is customised for the Extension in the SDK archive.
3. Click the Screen Sharing button to start sharing your screen.

> **Noteï¼**If you skip [Step 1](https://www.tencentcloud.com/document/product/647/67520#8c55e9f6-8124-45e7-bb5c-a055950b78c8), i.e. don't configure App Group (the interface passes null), the screen sharing can still work, but the stability will be reduced, so although there are more steps, please try to configure the correct App Group to ensure the stability of the screen sharing function.

#### Step 1:

#### Create an App Group (optional)

[Sign in](https://developer.apple.com/) with your account and do the following, note that you need to re-download the corresponding Provisioning Profile after completing the process.

1. Click Certificates, IDs & Profiles. 2.
2. Click the plus sign on the right side of the screen. 3.
3. Select App Groups and click Continue. 4.
4. In the pop-up form, fill in Description and Identifier, where Identifier needs to be passed into the corresponding AppGroup parameter in the interface. Click Continue when you are done.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/111ade23c12311efa28d525400329841.jpeg)

5. Back on the Identifier page, select App IDs from the top left menu and click on your App ID (the AppIDs for the main App and Extension need to be configured the same way).
6. Select App Groups and click Edit.
7. In the pop-up form, select the App Group you created earlier, click Continue to return to the Edit page, and click Save to save it.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/10ee7472c12311ef934f52540055f650.jpeg)

8. Redownload the Provisioning Profile and configure it into XCode.

#### **Step 2ï¼Create Broadcast Upload Extension**

1. Click File > New > Target... in the Xcode menu. Select Broadcast Upload Extension. 2.
2. Fill in the relevant information in the pop-up dialogue box, without checking Include UI Extension, click Finish to complete the creation.
3. Drag [TXLiteAVSDK_ReplayKitExt.framework](https://trtc.io/sdkDownload?id=conference) from the downloaded SDK zip package to the project, and check the Target you just created. 4.
4. If you choose to perform [Step 1](https://www.tencentcloud.com/document/product/647/67520#8c55e9f6-8124-45e7-bb5c-a055950b78c8), you need to click + Capability and double click App Groups in the newly added Target, as shown below:

![AddCapability](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/10ee4ed5c12311efb86b525400f69702.png)

After the operation is completed, a file named Target.entitlements will be generated in the file list, as shown in the following figure, select the file and click the + sign to fill in the App Group in the above steps.

![AddGroup](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/110279abc12311efbb7252540075b605.png)

5. Select the Target of the main App and follow the above steps to do the same for the Target of the main App. 6.
6. In the newly created Target, Xcode will automatically create a file named âSampleHandler.swiftâ and replace it with the following code. If [Step 1](https://www.tencentcloud.com/document/product/647/67520#8c55e9f6-8124-45e7-bb5c-a055950b78c8) was performed, replace APPGROUP in the code with the App Group Identifier you created earlier, and then locate the EngineManager.swift file in TUIRoomKit, and set appGroupString there to App Group Identifier as well. If [Step 1](https://www.tencentcloud.com/document/product/647/67520#8c55e9f6-8124-45e7-bb5c-a055950b78c8) is skipped, you don't need to modify APPGROUP.

Swift

OC

```
import ReplayKitimport TXLiteAVSDK_ReplayKitExtlet APPGROUP = "group.com.tencent.comm.trtc.demo"class SampleHandler: RPBroadcastSampleHandler, TXReplayKitExtDelegate {    let recordScreenKey = Notification.Name.init("TRTCRecordScreenKey")    override func broadcastStarted(withSetupInfo setupInfo: [String : NSObject]?) {        // User has requested to start the broadcast. Setup info from the UI extension can be supplied but optional.        TXReplayKitExt.sharedInstance().setup(withAppGroup: APPGROUP, delegate: self)    }    override func broadcastPaused() {        // User has requested to pause the broadcast. Samples will stop being delivered.    }    override func broadcastResumed() {        // User has requested to resume the broadcast. Samples delivery will resume.    }    override func broadcastFinished() {        // User has requested to finish the broadcast.        TXReplayKitExt.sharedInstance().broadcastFinished()    }    func broadcastFinished(_ broadcast: TXReplayKitExt, reason: TXReplayKitExtReason) {        var tip = ""        switch reason {        case TXReplayKitExtReason.requestedByMain:            tip = "Screensharing has ended"            break        case TXReplayKitExtReason.disconnected:            tip = "Application Disconnect"            break        case TXReplayKitExtReason.versionMismatch:            tip = "Integration error (SDK version number does not match)"            break        default:            break        }        let error = NSError(domain: NSStringFromClass(self.classForCoder), code: 0, userInfo: [NSLocalizedFailureReasonErrorKey:tip])        finishBroadcastWithError(error)    }    override func processSampleBuffer(_ sampleBuffer: CMSampleBuffer, with sampleBufferType: RPSampleBufferType) {        switch sampleBufferType {        case RPSampleBufferType.video:            // Handle video sample buffer            TXReplayKitExt.sharedInstance() .sendVideoSampleBuffer(sampleBuffer)            break        case RPSampleBufferType.audioApp:            // Handle audio sample buffer for app audio            break        case RPSampleBufferType.audioMic:            // Handle audio sample buffer for mic audio            break        @unknown default:            // Handle other sample buffer types            fatalError("Unknown type of sample buffer")        }    }}
```

```
#import "SampleHandler.h"@import TXLiteAVSDK_ReplayKitExt;#define APPGROUP @"group.com.tencent.comm.trtc.demo"@protocol TXReplayKitExtDelegate;@interface SampleHandler()@end@implementation SampleHandler- (void)broadcastStartedWithSetupInfo:(NSDictionary<NSString *,NSObject *> *)setupInfo {    [[TXReplayKitExt sharedInstance] setupWithAppGroup:APPGROUP delegate:self];}- (void)broadcastPaused {    // User has requested to pause the broadcast. Samples will stop being delivered.}- (void)broadcastResumed {    // User has requested to resume the broadcast. Samples delivery will resume.}- (void)broadcastFinished {    [[TXReplayKitExt sharedInstance] broadcastFinished];    // User has requested to finish the broadcast.}#pragma mark - TXReplayKitExtDelegate- (void)broadcastFinished:(TXReplayKitExt *)broadcast reason:(TXReplayKitExtReason)reason{    NSString *tip = @"";    switch (reason) {        case TXReplayKitExtReasonRequestedByMain:            tip = @"Screensharing has ended";            break;        case TXReplayKitExtReasonDisconnected:            tip = @"Application Disconnect";            break;        case TXReplayKitExtReasonVersionMismatch:            tip = @"Integration error (SDK version number does not match)";            break;    }    NSError *error = [NSError errorWithDomain:NSStringFromClass(self.class)                                         code:0                                     userInfo:@{        NSLocalizedFailureReasonErrorKey:tip    }];    [self finishBroadcastWithError:error];}- (void)processSampleBuffer:(CMSampleBufferRef)sampleBuffer withType:(RPSampleBufferType)sampleBufferType {    switch (sampleBufferType) {        case RPSampleBufferTypeVideo:            [[TXReplayKitExt sharedInstance] sendSampleBuffer:sampleBuffer withType:sampleBufferType];            break;        case RPSampleBufferTypeAudioApp:            // Handle audio sample buffer for app audio            break;        case RPSampleBufferTypeAudioMic:            // Handle audio sample buffer for mic audio            break;        default:            // Handle other sample buffer types            break;    }}@end
```

7. Click on the newly created Target, select the General option and add the following libraries to Frameworks and Libraries:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/11232fd3c12311efb86b525400f69702.png)

**Androidï¼**Due to the change of the privacy policy of Android system, if you use screen recording and other functions in Android 10 and above Apps, you need to do it in the Foreground Service, otherwise the system will report an error or the App will be terminated by the system when recording/screen sharing. In our component, this Android Foreground Service will be enabled for you automatically, you just need to click the screen sharing button and agree to the relevant privacy policy to share.

The code for Android Foreground Service can be found in our [code examples](https://github.com/Tencent-RTC/TUIRoomKit/blob/main/Android/tuiroomkit/src/main/java/com/tencent/cloud/tuikit/roomkit/common/KeepAliveService.java#L36).

**iOS**ï¼Cross-app screen sharing on iOS requires the addition of the Extension recording process to work with the main App process for push streaming.The Extension recording process is created by the system when it needs to record a screen and is responsible for receiving screen images captured by the system. Therefore, you need to:

1. create an App Group and configure it in XCode (optional). The purpose of this step is to allow the Extension screen recording process to communicate across processes with the main App process.
2. In your project, create a new Target for Broadcast Upload Extension and integrate [TXLiteAVSDK_ReplayKitExt.framework](https://trtc.io/sdkDownload?id=conference), which is customised for the Extension in the SDK archive.
3. Click the Screen Sharing button to start sharing your screen.

> **Noteï¼**If you skip [Step 1](https://www.tencentcloud.com/document/product/647/67520#step1), i.e. don't configure App Group (the interface passes null), the screen sharing can still work, but the stability will be reduced, so although there are more steps, please try to configure the correct App Group to ensure the stability of the screen sharing function.

#### Step 1:

#### Create an App Group (optional)

[Sign in](https://developer.apple.com/) with your account and do the following, note that you need to re-download the corresponding Provisioning Profile after completing the process.

1. Click Certificates, IDs & Profiles. 2.
2. Click the plus sign on the right side of the screen. 3.
3. Select App Groups and click Continue. 4.
4. In the pop-up form, fill in Description and Identifier, where Identifier needs to be passed into the corresponding AppGroup parameter in the interface. Click Continue when you are done.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1161c96fc12311efad135254002693fd.jpeg)

5. Back on the Identifier page, select App IDs from the top left menu and click on your App ID (the AppIDs for the main App and Extension need to be configured the same way).
6. Select App Groups and click Edit.
7. In the pop-up form, select the App Group you created earlier, click Continue to return to the Edit page, and click Save to save it.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1148d4c1c12311efae1f525400bdab9d.jpeg)

8. Redownload the Provisioning Profile and configure it into XCode.

#### **Step 2ï¼Create Broadcast Upload Extension**

1. Click File > New > Target... in the Xcode menu. Select Broadcast Upload Extension. 2.
2. Fill in the relevant information in the pop-up dialogue box, without checking Include UI Extension, click Finish to complete the creation.
3. Drag [TXLiteAVSDK_ReplayKitExt.framework](https://trtc.io/sdkDownload?id=conference) from the downloaded SDK zip package to the project, and check the Target you just created. 4.
4. If you choose to perform [Step 1](https://www.tencentcloud.com/document/product/647/67520#3b31580d-e74c-4434-8385-f5baa8d38c41), you need to click + Capability and double click App Groups in the newly added Target, as shown below:

![AddCapability](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/11220d1ec12311efb86b525400f69702.png)

After the operation is completed, a file named Target.entitlements will be generated in the file list.

As shown in the figure below, select the file and click the + sign to fill in the App Group in the above steps.

![AddGroup](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/11182b99c12311efbb7252540075b605.png)

5. Select the Target of the main App and follow the above steps to do the same for the Target of the main App.
6. In the newly created Target, Xcode will automatically create a file named âSampleHandler.swiftâ and replace it with the following code. Replace the APPGROUP in the code with the App Group Identifier you created above.

```
import ReplayKitimport TXLiteAVSDK_ReplayKitExtlet APPGROUP = "group.com.tencent.comm.trtc.demo"class SampleHandler: RPBroadcastSampleHandler, TXReplayKitExtDelegate {    let recordScreenKey = Notification.Name.init("TRTCRecordScreenKey")    override func broadcastStarted(withSetupInfo setupInfo: [String : NSObject]?) {        // User has requested to start the broadcast. Setup info from the UI extension can be supplied but optional.        TXReplayKitExt.sharedInstance().setup(withAppGroup: APPGROUP, delegate: self)    }    override func broadcastPaused() {        // User has requested to pause the broadcast. Samples will stop being delivered.    }    override func broadcastResumed() {        // User has requested to resume the broadcast. Samples delivery will resume.    }    override func broadcastFinished() {        // User has requested to finish the broadcast.        TXReplayKitExt.sharedInstance() .finishBroadcast()    }    func broadcastFinished(_ broadcast: TXReplayKitExt, reason: TXReplayKitExtReason) {        var tip = ""        switch reason {        case TXReplayKitExtReason.requestedByMain:            tip = "Screensharing has ended"            break        case TXReplayKitExtReason.disconnected:            tip = "Application Disconnect"            break        case TXReplayKitExtReason.versionMismatch:            tip = "Integration error (SDK version number does not match)"            break        default:            break        }        let error = NSError(domain: NSStringFromClass(self.classForCoder), code: 0, userInfo: [NSLocalizedFailureReasonErrorKey:tip])        finishBroadcastWithError(error)    }    override func processSampleBuffer(_ sampleBuffer: CMSampleBuffer, with sampleBufferType: RPSampleBufferType) {        switch sampleBufferType {        case RPSampleBufferType.video:            // Handle video sample buffer            TXReplayKitExt.sharedInstance() .sendVideoSampleBuffer(sampleBuffer)            break        case RPSampleBufferType.audioApp:            // Handle audio sample buffer for app audio            break        case RPSampleBufferType.audioMic:            // Handle audio sample buffer for mic audio            break        @unknown default:            // Handle other sample buffer types            fatalError("Unknown type of sample buffer")        }    }}.
```

**Step 3**: Replace our app's App Group and BroadCast Upload Extension name with your App Group and BroadCast Upload Extension name in the component, for the code location please click on the [file link](https://github.com/Tencent-RTC/TUIRoomKit/blob/main/Flutter/tencent_conference_uikit/lib/pages/conference_main/widgets/bottom_view/controller.dart#L97).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/11576826c12311efa28d525400329841.png)

**Step 4ï¼**Tap the Screen Share button to start sharing your screen.

## Key Code

If you want to customise the screen sharing functionality, please see the TUIRoomEngine SDK : [Android](https://www.tencentcloud.com/document/product/647/54864#cc949f99d6a39e2bcf4723b664fe2d74) , [iOS&Mac](https://www.tencentcloud.com/document/product/647/54855#fe00b96dd343d6975b4350efc157d5c8), [Flutter](https://www.tencentcloud.com/document/product/647/57514#startPushLocalVideo).

## Communication and feedback

If you have any needs or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/67520](https://trtc.io/document/67520)*
