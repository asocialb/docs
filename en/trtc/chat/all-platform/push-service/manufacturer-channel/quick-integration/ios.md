# iOS

> **Note:**If you need to use products like Chat, CallKit, RoomKit, LiveKit simultaneously, please refer to [Chat Quick Integration Solution](https://www.tencentcloud.com/document/product/1047/50033).

### Step 1. Integrate TIMPush

1. The TIMPush component supports CocoaPods integration. You need to add the component dependencies in the Podfile.

```
target 'YourAppName' do  # Uncommment the next line if you're using Swift or would like to use dynamic frameworks  use_frameworks!  use_modular_headers!    # Pods for Example  pod 'TXIMSDK_Plus_iOS_XCFramework'  # The version number "VERSION" can be obtained from the Update Log.  pod 'TIMPush', 'VERSION'end
```

2. Run the following command to install the TIMPush component.

```
pod install # If you cannot install the latest version of TUIKit, run the following command to update your local CocoaPods repository list.pod repo update
```

### Step 2. Set push parameters

1. After you upload a certificate to the Chat console, the Chat console will assign a certificate ID to you, as shown below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/afe3c25cc1dd11efb492525400e889b2.png)

2. You need to implement the `- businessID` protocol method in AppDelegate to return the certificate ID.

Objective-C

Swift

```
businessID
```

```
#pragma mark - TIMPush//Swift must carry the @objc keyword@objc func businessID() -> Int32 {    // Certificate ID provided by the back console    return 0}@objc func applicationGroupID() -> String {    //AppGroup ID    return "group.com.yourcompony.pushkey"}@objc func onRemoteNotificationReceived(_ notice: String?) -> Bool {    // custom navigate    return false}
```

### Step 3: Register for Push

After the push registration is successful through the API call, offline push notifications can be received.

Objective-C

Swift

```
 const int sdkAppId = your sdkAppId; static const NSString *appKey = @"Client Key"; [TIMPushManager registerPush:sdkAppId appKey:appKey succ:^(NSData * _Nonnull deviceToken) {   } fail:^(int code, NSString * _Nonnull desc) { }];
```

```
let sdkAppId: Int = 0let appKey: String = "Client Key"TIMPushManager.registerPush(Int32(sdkAppId), appKey: appKey, succ: { deviceToken in    // success}, fail: { code, desc in    // failed})
```

> **Note:**After you log in, when you see the APNs configuration success log printed on the console, it indicates that the integration is successful.If your app has obtained push permissions, you can receive remote push notifications when the app is moved to the background or the process is killed.

### Step 4: Send push notifications

Detailed usage instructions can be found at: [RESTful APIs - Initiate All-staff/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).

### Step 5: Click Custom Redirect after offline push

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

### Step 6: Push Arrival Rate Statistics

1. If you need to collect data on push delivery and click rates, you need to implement the `- applicationGroupID` method in the AppDelegate.m file and return the App Group ID ([the generation method can be referred to in Vendor Configuration - Generating App Group ID](https://www.tencentcloud.com/document/product/1047/60548#ae5590eb-b974-4226-9f1b-720fb0201c85)).
2. In the Notification Service Extension's `- didReceiveNotificationRequest:withContentHandler:` method, call the push arrival rate statistics function:

Objective-C

Swift

```
@implementation NotificationService- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {    //appGroup identifies the app group shared between the main app and extension. It needs to be configured in the App Groups capability of the main app.    //Format: group + [mainBundleID] + key    //E.g., group.com.tencent.im.pushkey    NSString * appGroupID = kTIMPushAppGroupKey;    __weak typeof(self) weakSelf = self;    [TIMPushManager handleNotificationServiceRequest:request appGroupID:appGroupID callback:^(UNNotificationContent *content) {        weakSelf.bestAttemptContent = [content mutableCopy];        // Modify the notification content here...        // self.bestAttemptContent.title = [NSString stringWithFormat:@"%@ [modified]", self.bestAttemptContent.title];        weakSelf.contentHandler(weakSelf.bestAttemptContent);    }];}@end
```

```
override func didReceive(_ request: UNNotificationRequest, withContentHandler contentHandler: @escaping (UNNotificationContent) -> Void) {    self.contentHandler = contentHandler    bestAttemptContent = (request.content.mutableCopy() as? UNMutableNotificationContent)    //appGroup identifies the app group shared between the main app and extension. It needs to be configured in the App Groups capability of the main app.    //Format: group + [mainBundleID] + key    //E.g., group.com.tencent.im.pushkey    TIMPushManager.handleNotificationServiceRequest(request: request, appGroupID: "appGroupID") {        [weak self] content  in        if let bestAttemptContent = self?.bestAttemptContent {            // Modify the notification content here...            bestAttemptContent.title = "\\(bestAttemptContent.title) [modified]"            contentHandler(bestAttemptContent)        }    }}
```

> **Note:**To report push delivery data, enable the mutable-content switch to support iOS 10's extension feature.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ee0afa00b2d611ef970f525400d5f8ef.png)Data details can be viewed on the Push Data Page. The Push Data Page can only be used after [purchasing the Push Plugin](https://buy.tencentcloud.com/avc?activeId=plugin&regionId=1).

### Regarding All-staff/Tag Push

All-staff/Tag Push supports sending specific content, and also allows for the delivery of personalized content to specific user groups based on Tag, attribute, such as Membership Activities, Regional Notifications, etc. It aids in User Acquisition, Conversion, Activation Promotion, and other operational work phases, while also supporting Push Delivery Reports, Self-service Push Troubleshooting Tool. For more details, please see [Effect Display](https://www.tencentcloud.com/document/product/1047/60541).

For more detailed content, it is recommended to refer to [All-staff/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).

Congratulations on completing the integration of the Push Plugin. Please note: After the **trial or purchase expiry of the Push Plugin, push services (including regular message offline push, all-staff push, etc.) will be automatically stopped**. To avoid affecting the normal use of your business, please [purchase](https://buy.tencentcloud.com/avc?activeId=plugin&regionId=1)/[renew](https://buy.tencentcloud.com/avc?activeId=plugin&regionId=1) in advance.


---
*Source: [https://trtc.io/document/60553](https://trtc.io/document/60553)*
