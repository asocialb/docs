# Quick Integration

If you want to integrate the TIMPush component as simply as possible, you need to use the login/logout interfaces of [TUILogin](https://github.com/TencentCloud/chat-uikit-ios/blob/main/TUIKit/TUICore/TUILogin.m) for IM account login/logout operations. The TIMPush component can automatically detect login/logout events.

### Step 1. Integrate the TIMPush component

1. The TIMPush component supports CocoaPods integration. You need to add the component dependencies in the Podfile.

```
target 'YourAppName' do  # Uncommment the next line if you're using Swift or would like to use dynamic frameworks  use_frameworks!  use_modular_headers!    # Pods for Example  # The version number "VERSION" can be obtained from the Update Log.  pod 'TIMPush', 'VERSION'end
```

2. Run the following command to install the TIMPush component.

```
pod install # If you cannot install the latest version of TUIKit, run the following command to update your local CocoaPods repository list.pod repo update
```

### Step 2. Set push parameters

1. After you upload the certificate to the Chat console, the Chat console allocates a certificate ID for you, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c1f9e5fcc1ce11ef87c05254005ef0f7.png)

2. You need to implement the `- businessID` protocol method in AppDelegate to return the certificate ID.

Objective-C

Swift

```
businessID
```

```
#pragma mark - TIMPush//Swift must carry the @objc keyword@objc func businessID() -> Int32 {    //The businessID ID given by the console in the previous step    return 0}@objc func applicationGroupID() -> String {    //AppGroup ID    return "group.com.yourcompony.pushkey"}@objc func onRemoteNotificationReceived(_ notice: String?) -> Bool {    // custom navigate    return false}
```

At this point, you have completed the basic push feature integration.

> **Note:**After you log in, when you see the APNs configuration success log printed on the console, it indicates that the integration is successful.If your app has obtained push permissions, you will receive remote push notifications when it goes to the background or the process is stopped.If you have not integrated the TUICore component and do not need to use TUILogin for login/logout but still want to implement offline push, you only need to:After your app/Chat login is complete, actively call the registerPush method to register for push notifications.When logging out, actively call the unRegisterPush method to unregister push notifications.If you only want to support push notifications without login, you can switch the registration interface to: call the registerPush interface of TIMPushManager. For details on sending messages in step 3, see - [restApi interface](https://www.tencentcloud.com/document/product/1047/60561).

### Step 3. Set offline push parameters when sending messages (TUIChat has already added this by default when integrating with UI, you can skip this step)

When calling [sendMessage](https://im.sdk.qcloud.com/doc/en/categoryV2TIMManager_07Message_08.html#a681947465d6ab718da40f7f983740a21) to send messages, you can set offline push parameters through [V2TIMOfflinePushInfo](https://im.sdk.qcloud.com/doc/en/interfaceV2TIMOfflinePushInfo.html). Use the [ext](https://im.sdk.qcloud.com/doc/en/interfaceV2TIMOfflinePushInfo.html#ab2b8698eb6c7b51453995c89f503ec35) of V2TIMOfflinePushInfo to set custom ext data. When the user receives the offline push and launches the app, they can get the ext field in the callback of clicking the notification and then navigate to the specified UI based on the ext field content. Refer to the sendMessage: method of [TUIMessageBaseDataProvider](https://github.com/TencentCloud/chat-uikit-ios/blob/main/TUIKit/TUIChat/BaseDataProvider/Impl/TUIMessageDataProvider.m):

Objective-C

Swift

```
#import <TUICore/OfflinePushExtInfo.h>V2TIMOfflinePushInfo *pushInfo = [[V2TIMOfflinePushInfo alloc] init];pushInfo.title = @"Push title";pushInfo.desc  = @"Push content";        BOOL isGroup = groupID.length > 0;NSString *senderId = isGroup ? (groupID) : ([TUILogin getUserID]);NSString *nickName = isGroup ? (conversationData.title) : ([TUILogin getNickName] ?: [TUILogin getUserID]);OfflinePushExtInfo *extInfo = [[OfflinePushExtInfo alloc] init];OfflinePushExtBusinessInfo * entity = extInfo.entity;entity.action = 1;entity.content = @"Push content";entity.sender = senderId;entity.nickname = nickName;entity.faceUrl = [TUILogin getFaceUrl] ?: @"";entity.chatType = [isGroup ? @(V2TIM_GROUP) : @(V2TIM_C2C) integerValue];entity.version = kOfflinePushVersion;pushInfo.ext = [extInfo toReportExtString];//The following fields are compatible with Android and need to be filled inpushInfo.AndroidOPPOChannelID = @"tuikit";pushInfo.AndroidSound = TUIConfig.defaultConfig.enableCustomRing ? @"private_ring" : nil;pushInfo.AndroidHuaWeiCategory = @"IM";pushInfo.AndroidVIVOCategory = @"IM";
```

```
import TIMPushimport TUICoreimport ImSDK_Pluslet pushInfo = V2TIMOfflinePushInfo()pushInfo.title = "Push title"pushInfo.desc = "Push content"let isGroup = groupID!.count > 0let senderId = isGroup ? groupID : TUILogin.getUserID()let nickName = isGroup ? "conversationData Title" : (TUILogin.getNickName() ?? TUILogin.getUserID())let extInfo = OfflinePushExtInfo()let entity = extInfo.entityentity.action = 1entity.content = "Push content"entity.sender = senderId ?? ""entity.nickname = nickName ?? ""entity.faceUrl = TUILogin.getFaceUrl() ?? ""entity.chatType = isGroup ? Int(V2TIMConversationType.GROUP.rawValue) : Int(V2TIMConversationType.C2C.rawValue)entity.version = 1pushInfo.ext = extInfo.toReportExtString()//The following fields are compatible with Android and need to be filled inpushInfo.androidOPPOChannelID = "tuikit"pushInfo.androidSound = TUIConfig.default().enableCustomRing ? "private_ring" : nilpushInfo.androidHuaWeiCategory = "IM"pushInfo.androidVIVOCategory = "IM"
```

### Step 4: Customize the tap-to-redirect logic for offline push

If you need to customize the parsing of received remote push notifications, you can implement it as follows:

Custom click redirect implementation

Custom click redirect implementation (old solution)

> **Note:**It is recommended to place the registration callback timing in the didFinishLaunchingWithOptions function of the AppDelegate.

Objective-C

Swift

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {    [TIMPushManager addPushListener:self];    return YES;}#pragma mark - TIMPushListener- (void)onNotificationClicked:(NSString *)ext {        // Getting ext for Definition redirect}
```

```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {    // Override point for customization after application launch.    TIMPushManager.addPushListener(listener: self)    return true}@objc func onNotificationClicked(_ ext: String) {    //Clicked}@objc func onRecvPushMessage(_ message: TIMPushMessage) {    //onRecvPushMessage}    @objc func onRevokePushMessage(_ messageID: String) {    //onRevokePushMessage}
```

You need to implement the `- onRemoteNotificationReceived` method in the AppDelegate.m file.

Objective-C

Swift

```
#pragma mark - TIMPush  - (BOOL)onRemoteNotificationReceived:(NSString *)notice {    //- If YES is returned, TIMPush will not execute the built-in TUIKit offline push parsing logic, leaving it entirely to you to handle.    //NSString *ext = notice;    //OfflinePushExtInfo *info = [OfflinePushExtInfo createWithExtString:ext];    //return YES;        //- If NO is returned, TIMPush will continue to execute the built-in TUIKit offline push parsing logic and continue to callback - navigateToBuiltInChatViewController:groupID: method.    return NO;}
```

```
@objc func onRemoteNotificationReceived(_ notice: String) -> Bool {    //- If YES is returned, TIMPush will not execute the built-in TUIKit offline push parsing logic, leaving it entirely to you to handle.    // let ext = notice    // let info = OfflinePushExtInfo.create(withExtString: ext)    // return true        //- If false is returned, TIMPush will continue to execute the built-in TUIKit offline push parsing logic and continue to callback - navigateToBuiltInChatViewController:groupID: method.    return false}
```

### Step 5: Statistics on push reach rate

1. If you need to collect data on push delivery and click rates, you need to implement the `- applicationGroupID` method in the AppDelegate.m file and return the App Group ID ([the generation method can be referred to in Vendor Configuration - Generating App Group ID](https://www.tencentcloud.com/document/product/1047/67573#ae5590eb-b974-4226-9f1b-720fb0201c85)).
2. In the Notification Service Extension's `- didReceiveNotificationRequest:withContentHandler:` method, call the push reach rate statistics function:

Objective-C

Swift

```
@implementation NotificationService- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {    //appGroup identifies the app group shared between the main app and extension. It needs to be configured in the App Groups capability of the main app.    //Format: group + [mainBundleID] + key    //E.g., group.com.tencent.im.pushkey    NSString * appGroupID = kTIMPushAppGroupKey;    __weak typeof(self) weakSelf = self;    [TIMPushManager handleNotificationServiceRequest:request appGroupID:appGroupID callback:^(UNNotificationContent *content) {        weakSelf.bestAttemptContent = [content mutableCopy];        // Modify the notification content here...        // self.bestAttemptContent.title = [NSString stringWithFormat:@"%@ [modified]", self.bestAttemptContent.title];        weakSelf.contentHandler(weakSelf.bestAttemptContent);    }];}@end
```

```
override func didReceive(_ request: UNNotificationRequest, withContentHandler contentHandler: @escaping (UNNotificationContent) -> Void) {    self.contentHandler = contentHandler    bestAttemptContent = (request.content.mutableCopy() as? UNMutableNotificationContent)    //appGroup identifies the app group shared between the main app and extension. It needs to be configured in the App Groups capability of the main app.    //Format: group + [mainBundleID] + key    //E.g., group.com.tencent.im.pushkey    TIMPushManager.handleNotificationServiceRequest(request: request, appGroupID: "appGroupID") {        [weak self] content  in        if let bestAttemptContent = self?.bestAttemptContent {            // Modify the notification content here...            bestAttemptContent.title = "\\(bestAttemptContent.title) [modified]"            contentHandler(bestAttemptContent)        }    }}
```

> **Note:**To report push delivery data, enable the mutable-content switch to support iOS 10's extension feature.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12470dd2b30c11ef96e55254002693fd.png)
> Data details can be viewed on the Push Data Page. The Push Data Page can only be used after [purchasing the Push Plugin](https://buy.tencentcloud.com/avc?activeId=plugin&regionId=1).

### About compliance

- TIMPush will not perform any other operations before you actively call registerPush, in accordance with relevant regulations.
- If you use TUILogin for login and logout, TIMPush will automatically call registerPush or unRegisterPush internally.

Congratulations on completing the integration of the Push Plugin. Please note: After the **trial or purchase expiry of the Push Plugin, push services (including regular message offline push, all-staff push, etc.) will be automatically stopped**. To avoid affecting the normal use of your business, please [purchase](https://buy.tencentcloud.com/avc?activeId=plugin&regionId=1)/[renew](https://buy.tencentcloud.com/avc?activeId=plugin&regionId=1) in advance.

### Regarding All-staff/Tag Push

All-staff/Tag Push supports sending specific content, and also allows for the delivery of personalized content to specific user groups based on Tag, attribute, such as Membership Activities, Regional Notifications, etc. It aids in User Acquisition, Conversion, Activation Promotion, and other operational work phases, while also supporting Push Delivery Reports, Self-service Push Troubleshooting Tool. For more details, please see [Effect Display](https://www.tencentcloud.com/document/product/1047/60541).

For more detailed content, it is recommended to refer to [All-staff/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).

Congratulations on completing the integration of the Push Plugin. Please note: After the **trial or purchase expiry of the Push Plugin, push services (including regular message offline push, all-staff push, etc.) will be automatically stopped**. To avoid affecting the normal use of your business, please [purchase](https://buy.tencentcloud.com/avc?activeId=plugin&regionId=1)/[renew](https://buy.tencentcloud.com/avc?activeId=plugin&regionId=1) in advance.

> **Note:**If you are unable to receive push notifications after integration, please first use the [Troubleshooting Tool](https://www.tencentcloud.com/document/product/1047/60541) to check the specific reasons. Also, pay attention to the [Vendor Message Classification Mechanism](https://www.tencentcloud.com/document/product/1047/60576).To view push indicator data, please use [Statistics](https://www.tencentcloud.com/document/product/1047/60540) query.For the All/Tag Push feature, please refer to: [RESTful APIs - Initiate All/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).


---
*Source: [https://trtc.io/document/50033](https://trtc.io/document/50033)*
