# VoIP (Apple CallKit)

VoIP (Voice over IP) Push is a notification mechanism provided by Apple for responding to VoIP calls. Combining Apple's PushKit.framework and CallKit.framework can achieve system-level call effects.

> **Note:**Apple requires that VoIP Push be used in conjunction with the CallKit.framework starting with iOS 13.0; otherwise, the app will crash after running.VoIP Push cannot reuse the general APNs push certificates, so a separateÂ [VoIP Push certificate needs to be applied for](https://www.tencentcloud.com/document/product/647/51000##apply_ceritificate)Â on the Apple Developer website.

## Integration effect

| Lock screen effects | Effects of Applications in the Background | Effects of Applications in the Background and Expanding |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6b1171760c6511ef89045254000ded98.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6b26066c0c6511ef9ef35254002977b6.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6b0436630c6511efa4155254005a7266.jpeg) |

## Configuring VoIP Push

To receive VoIP Push notifications, follow these steps:

1. Apply for a VoIP Push certificate.
2. Upload the certificate to the Chat console.
3. Complete the project configuration.
4. Integrate the TUICallKitVoIPExtension component.

### Step 1: Apply for a VoIP Push certificate

Before applying for a VoIP Push certificate, log in to theÂ [Apple Developer Center](https://developer.apple.com/account/),Â enable your app's remote push capabilities.

Once your AppID has Push Notification capabilities, follow these steps to apply for and configure a VoIP Push certificate:

1. Log in to theÂ [Apple Developer Center](https://developer.apple.com/account/)Â website, click "Certificates, IDs & Profiles" in the sidebar, and go to the "Certificates, Identifiers & Profiles" page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8e8e6a630c6411efa4155254005a7266.png)

2. Click **+**next to Certificates.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a38c88be0c6411ef8fbd5254008af8cc.png)

3. In the **Create a New Ceritificate**tab, select **VoIP Services Certificate** and click **Continue**.
4. In the **Select an App ID for your VoIP Service Certificate**tab, select your app's BundleID, and click **Continue**.
5. The system will prompt you for a Certificate Signing Request (CSR).
6. Next, create a CSR file. OpenÂ **Keychain Access**Â on your Mac, and in the menu, chooseÂ **Keychain Access** > **Certificate Assistant** > **Request a Certificate From a Certificate Authority**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e05a58d90c6411ef86f1525400967725.png)

7. Enter your email address, common name (your name or company name), chooseÂ **Save to disk**, click **Continue**, and the system will generate aÂ `*.certSigningRequest`Â file.

Go back to the Apple Developer website in [Step5](#step5) , click "Choose File" and upload the generatedÂ `*.certSigningRequest`Â file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3184b9d40c6511efb74e525400b3b5af.png)

8. Click **Continue** to generate the certificate, and click **Download** to download the corresponding certificate to your local device.
9. Double-click the downloadedÂ `voip_services.cer`Â file, and the system will import it into your keychain.
10. Open the Keychain app, underÂ **Login**Â >Â **My Certificates**, right-click on the created VoIP Services certificate.

> **Note:**When saving theÂ `P12`Â file, be sure to set a password for it.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/49b35b920c6511ef86f1525400967725.png)

### Step 2: Upload certificates to the Chat Console

[Open the Chat Console](https://console.tencentcloud.com/im/detail), select your created Chat application, and follow the steps below to upload your certificates:

1. Choose your Chat application, clickÂ **Go new**Â under theÂ **Offline Push Certificate Configuration**Â tab.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7b85cf0cb37911eeae9a525400c26da5.png)

2. In the **Manufacturer configuration**, switch to **iOS**, click the **Add Certificate** button. Then upload the VoIP certificates for both the production and development environments.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a215556eb37911ee9fd6525400bb593a.png)

> **Note:**The VoIP Push Certificate itself does not distinguish between production and testing environments. Both environments use the same VoIP Push Certificate.The uploaded certificate name should be in English (especially avoiding brackets and other special characters).The uploaded certificate must have a password set, or the push notification won't be received.The certificate for publishing to the App Store needs to be set to the production environment; otherwise, the push notification won't be received.The p12 certificate you upload must be a valid and genuinely applied certificate.

3. After the upload is completed, record the certificate ID for different environments.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bb6a2be0b37911eeb2a1525400170219.png)

> Note:The certificate IDs for the development and production environments must be strictly distinguished and filled in according to the actual environment in [Step 4: Integrate the TUICallKitVoIPExtension component.](https://www.tencentcloud.com/document/product/647/51000#98d97e23-09f1-455f-baea-0db0dedffe06)

### Step 3: Complete the project configuration

1. As shown below, confirm whether the Push Notification capability has been added to your project's capabilities.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/503047d80a9811ee8ec2525400c56988.png)

2. As shown below, please check if the Voice over IP option is enabled under Background Modes in your project's capabilities.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/503377ac0a9811eead3b5254007e6a5b.png)

### Step 4: Integrate the TUICallKitVoIPExtension component

Use CocoaPods to import the component, following these steps:

1. Add the following dependency to yourÂ `Podfile`.

```
pod 'TUIVoIPExtension'
```

> **Note****ï¼**Please make sure to specify the same `Subspecs` for `TUICallKit_Swift` and `TUICallKitVoIPExtension` components in your `Podfile`.

2. Execute the command below to install the component.

```
pod install
```

3. Report the [Certificate ID recorded in Step 2](https://www.tencentcloud.com/document/product/647/51000#b6b4bd45-7700-41d1-8e1b-6efcf5ce2929).

Swift

Objective-C

```
import TUIVoIPExtensionfunc application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {        // Report certificate ID    TUIVoIPExtension.setCertificateID(1234)        return true}
```

```
#import <TUIVoIPExtension/TUIVoIPExtension.h>- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {        // Report certificate ID    [TUIVoIPExtension setCertificateID:1234];        return YES;}
```

> **Note:**If you cannot install the latest version of TUICallKit, execute the command below to update your local CocoaPods repository list.pod repo update

## Make a VoIP call

If you need to make a VoIP call, you need to set the iOSPushType field of the OfflinePushInfo toÂ `TUICallIOSOfflinePushTypeVoIP`Â when callingÂ calls. The default value isÂ `TUICallIOSOfflinePushTypeAPNs`.

Swift

Java

Dart

Objective-C

```
import TUICallKit_Swiftimport TUICallEnginelet pushInfo: TUIOfflinePushInfo = TUIOfflinePushInfo()pushInfo.title = ""pushInfo.desc = "You have a new call"pushInfo.iOSPushType = .voippushInfo.ignoreIOSBadge = falsepushInfo.iOSSound = "phone_ringing.mp3"pushInfo.androidSound = "phone_ringing"// OPPO must set a ChannelID to receive push messages. This channelID needs to be the same as the console.pushInfo.androidOPPOChannelID = "tuikit"// FCM channel ID, you need change PrivateConstants.java and set "fcmPushChannelId"pushInfo.androidFCMChannelID = "fcm_push_channel"// VIVO message type: 0-push message, 1-System message(have a higher delivery rate)pushInfo.androidVIVOClassification = 1// HuaWei message type: https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835pushInfo.androidHuaWeiCategory = "IM"let params = TUICallParams()params.userData = "User Data"params.timeout = 30params.offlinePushInfo = pushInfoTUICallKit.createInstance().calls(userIdList: ["123456"], callMediaType: .audio, params: params) {} fail: { code, message in}
```

```
TUICallDefine.OfflinePushInfo offlinePushInfo = new TUICallDefine.OfflinePushInfo();offlinePushInfo.setTitle("");offlinePushInfo.setDesc("You have receive a new call");// For OPPO, you must set the `ChannelID` to receive push messages. The `ChannelID` must be identical with that in the console.// OPPO must set a ChannelID to receive push messages. This channelID needs to be the same as the console.offlinePushInfo.setAndroidOPPOChannelID("tuikit");offlinePushInfo.setIgnoreIOSBadge(false);offlinePushInfo.setIOSSound("phone_ringing.mp3");offlinePushInfo.setAndroidSound("phone_ringing"); //Note:don't add suffix//VIVO message type: 0-push message, 1-System message(have a higher delivery rate)offlinePushInfo.setAndroidVIVOClassification(1);//FCM channel ID, you need change PrivateConstants.java and set "fcmPushChannelId"offlinePushInfo.setAndroidFCMChannelID("fcm_push_channel");//Huawei message typeofflinePushInfo.setAndroidHuaWeiCategory("IM");//IOS push type: if you want user VoIP, please modify type to TUICallDefine.IOSOfflinePushType.VoIPofflinePushInfo.setIOSPushType(TUICallDefine.IOSOfflinePushType.VoIP);TUICallDefine.CallParams params = new TUICallDefine.CallParams();params.offlinePushInfo = offlinePushInfo;List<String> list = new ArrayList<>();list.add("mike")TUICallKit.createInstance(context).calls(list, TUICallDefine.MediaType.Video, params, null);
```

```
TUIOfflinePushInfo offlinePushInfo = TUIOfflinePushInfo(); offlinePushInfo.title = "Flutter TUICallKit"; offlinePushInfo.desc = "This is an incoming call from Flutter TUICallkit"; offlinePushInfo.ignoreIOSBadge = false; offlinePushInfo.iOSSound = "phone_ringing.mp3"; offlinePushInfo.androidSound = "phone_ringing"; offlinePushInfo.androidOPPOChannelID = "Flutter TUICallKit"; offlinePushInfo.androidVIVOClassification = 1; offlinePushInfo.androidFCMChannelID = "fcm_push_channel"; offlinePushInfo.androidHuaWeiCategory = "Flutter TUICallKit"; offlinePushInfo.iOSPushType = TUICallIOSOfflinePushType.VoIP; TUICallParams params = TUICallParams(offlinePushInfo: offlinePushInfo);   TUICallKit.instance.calls(['vince'], TUICallMediaType.audio, params);
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>#import <RTCRoomEngine/TUICallEngine.h>- (TUICallParams *)getCallParams {    TUIOfflinePushInfo *offlinePushInfo = [self createOfflinePushInfo];    TUICallParams *callParams = [TUICallParams new];    callParams.offlinePushInfo = offlinePushInfo;    callParams.timeout = 30;    return callParams;}- (TUIOfflinePushInfo *)createOfflinePushInfo {    TUIOfflinePushInfo *pushInfo = [TUIOfflinePushInfo new];    pushInfo.title = @"";    pushInfo.desc = @"You have a new call";    pushInfo.iOSPushType = TUICallIOSOfflinePushTypeVoIP;    pushInfo.ignoreIOSBadge = NO;    pushInfo.iOSSound = @"phone_ringing.mp3";    pushInfo.AndroidSound = @"phone_ringing";    // For OPPO, you must set the `ChannelID` to receive push messages. The `ChannelID` must be identical with that in the console.    // OPPO must set a ChannelID to receive push messages. This channelID needs to be the same as the console.    pushInfo.AndroidOPPOChannelID = @"tuikit";    // FCM channel ID, you need change PrivateConstants.java and set "fcmPushChannelId"    pushInfo.AndroidFCMChannelID = @"fcm_push_channel";    // VIVO message type: 0-push message, 1-System message(have a higher delivery rate)    pushInfo.AndroidVIVOClassification = 1;    // HuaWei message type: https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835    pushInfo.AndroidHuaWeiCategory = @"IM";    return pushInfo;}[[TUICallKit createInstance] calls:@[@"123456"]                     callMediaType:TUICallMediaTypeAudio                            params:[self getCallParams] succ:^{} fail:^(int code, NSString * _Nullable errMsg) {}];Objective-C
```

## Call from the system call log

If you want to initiate a one-on-one audio or video call directly by clicking the call record in theÂ **System PhoneÂ**>**Â Recent Calls**Â list, you need to use theÂ **callWith**Â method in theÂ **TUICallKitVoIPExtension**Â component in the Application lifecycle callback function. Here's an example:

> **Note:**Only supports dialing one-on-one audio and video calls directly.The logged-in account must be the same account.

1. On iOS 13 (and later versions) withÂ **SceneDelegateÂ**support, and with a minimum compatibility version prior to iOS 13, you need to implement the following methods inÂ **AppDelegateÂ**andÂ **SceneDelegateÂ**respectively.

Swift

Objective-C

```
import TUIVoIPExtension/// Implementation in AppDelegate, for versions before iOS 13func application(_ application: UIApplication, continue userActivity: NSUserActivity, restorationHandler: @escaping ([any UIUserActivityRestoring]?) -> Void) -> Bool {    TUIVoIPExtension.call(with: userActivity)    return true}/// Implementation in SceneDelegatefunc scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {    for userActivity in connectionOptions.userActivities {        TUIVoIPExtension.call(with: userActivity);     }}func scene(_ scene: UIScene, continue userActivity: NSUserActivity) {    TUIVoIPExtension.call(with: userActivity);}
```

```
#import <TUIVoIPExtension/TUIVoIPExtension.h>/// Implementation in AppDelegate, for versions before iOS 13- (BOOL)application:(UIApplication *)application continueUserActivity:(nonnull NSUserActivity *)userActivity restorationHandler:(nonnull void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler {    [TUIVoIPExtension callWith:userActivity];    return YES;}/// Implementation in SceneDelegate- (void)scene:(UIScene *)scene willConnectToSession:(UISceneSession *)sessionptions:(UISceneConnectionOptions *)connectionOptions {    [connectionOptions.userActivities enumerateObjectsUsingBlock:^(NSUserActivity * _Nonnull userActivity, BOOL * _Nonnull stop) {        [TUIVoIPExtension callWith:userActivity];    }];}- (void)scene:(UIScene *)scene continueUserActivity:(NSUserActivity *)userActivity {    [TUIVoIPExtension callWith:userActivity];}
```

2. On iOS 13 (and later versions) withoutÂ **SceneDelegate**, you only need to implement the following method inÂ **AppDelegate**.

Swift

Objective-C

```
import TUIVoIPExtensionfunc application(_ application: UIApplication, continue userActivity: NSUserActivity, restorationHandler: @escaping ([any UIUserActivityRestoring]?) -> Void) -> Bool {    TUIVoIPExtension.call(with: userActivity)    return true}
```

```
#import <TUIVoIPExtension/TUIVoIPExtension.h>- (BOOL)application:(UIApplication *)application continueUserActivity:(nonnull NSUserActivity *)userActivity restorationHandler:(nonnull void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler {    [TUIVoIPExtension callWith:userActivity];    return YES;}
```

## Frequently Asked Questions

### 1. Can't receive VoIP Push ?

1. First, check if the App's running environment and the certificate environment are consistent, and if the certificate ID matches. If they are inconsistent, you won't be able to receive push notifications.
2. Please make sure your currently logged-in account is offline: press the home key to switch to the background, or log in and then manually kill the process to exit. VoIP Push currently only supports push notifications in offline mode.
3. Check if [Step 3: Complete the Project Configuration](https://www.tencentcloud.com/document/product/647/51000#3165881b-b747-4fbe-90a1-a0fbf10a9462) is done correctly.
4. **Try restarting the test phone to clear the system cache and memory (very important).**

### **2. How to Self-Integrate VoIP Push Functionality**

We also support you to integrate VoIP push capabilities yourself through SDK methods. The overall solution design is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cb0d8aec662a11f0b5365254001c06ec.png)

Related process description:

1. Refer to [Vendor Configuration](#b6b4bd45-7700-41d1-8e1b-6efcf5ce2929) to apply for VoIP push certificates, and upload certificates on IM console to get certificate ID.
2. Refer to [Apple PushKit](https://developer.apple.com/documentation/pushkit) to use and get device token.
3. Use IMSDK's [setVOIP](https://www.tencentcloud.com/document/product/1047/36170#offline-push-apis) interface to report device token to IM server.
4. Refer to [Apple CallKit](https://developer.apple.com/documentation/callkit) to use and display push popup.
5. Refer to TUICallKit interface usage to [initiate VoIP calls](#31eb20b8-182b-49f0-ba94-d44d66de8593).


---
*Source: [https://trtc.io/document/51000](https://trtc.io/document/51000)*
