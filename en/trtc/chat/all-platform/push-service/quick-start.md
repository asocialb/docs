# Quick Start

### Step 1: Activate the Push Service

Before proceeding, please refer to the [Service Activation](https://www.tencentcloud.com/document/product/1047/60534) documentation to either obtain a trial version of the Push service or purchase a paid subscription package.

### Step 2: Integrate TIMPush and register for push notifications

> **Note:**The parameters required for the registration interface, sdkAppId and client key appKey, can be obtained from: [Console](https://console.trtc.io/chat/push-plugin-push-identifier) > Push Basic information, as shown in the screenshot below:![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6783851fc35c11ef8f945254007c27c5.png)

Android

iOS

Flutter

uni-app

React Native

1. **Integration of TIMPush**

```
// The version number "VERSION" can be obtained from the Update Log.implementation 'com.tencent.timpush:timpush:VERSION'implementation 'com.tencent.liteav.tuikit:tuicore:latest.release'
```

2. **Registration for push notifications (after successful registration, you can receive online push notifications)**

```
int sdkAppId = 0; // Your sdkAppIdString appKey = ""; //Client secretTIMPushManager.getInstance().registerPush(context, sdkAppId, appKey, new TIMPushCallback() {    @Override        public void onSuccess(Object data) {        }            @Override        public void onError(int errCode, String errMsg, Object data) {            }});
```

> **Note:**After successfully registering for offline push service, you can obtain the unique push ID, RegistrationID, through the [getRegistrationID](https://www.tencentcloud.com/document/product/1047/60557#getRegistrationID) interface. Then, you can push messages to the specified device based on the RegistrationID.RegistrationID is the push unique identifier ID of the device. It is automatically generated after the default registration of the push service succeeds. It will change after uninstall.

3. **Implement click notification bar callback**

After receiving the push message, clicking the notification bar will trigger the component to callback the click event and pass through the offline message.

Custom click redirect implementation

Custom click redirect implementation (old solution)

> **Note:**It is recommended to place the registration callback timing in the onCreate() function of the application.

```
TIMPushManager.getInstance().addPushListener(new TIMPushListener() {    @Override    public void onNotificationClicked(String ext) {        Log.d(TAG, "onNotificationClicked =" + ext);        // Getting ext for Definition redirect            }});
```

The component will notify the application in the form of a callback or broadcast, and the application can configure the app's page jump in the callback.

> **Note:**It is recommended to place the registration callback timing in the onCreate() function of the application.

```
// Dynamic Broadcast RegistrationIntentFilter intentFilter = new IntentFilter();intentFilter.addAction(TUIConstants.TIMPush.NOTIFICATION_BROADCAST_ACTION);LocalBroadcastManager.getInstance(context).registerReceiver(localReceiver, intentFilter);// Broadcast Receiverpublic class OfflinePushLocalReceiver extends BroadcastReceiver {    public static final String TAG = OfflinePushLocalReceiver.class.getSimpleName();    @Override    public void onReceive(Context context, Intent intent) {        DemoLog.d(TAG, "BROADCAST_PUSH_RECEIVER intent = " + intent);        if (intent != null) {            String ext = intent.getStringExtra(TUIConstants.TIMPush.NOTIFICATION_EXT_KEY);            // Getting ext for Definition redirect        } else {            Log.e(TAG, "onReceive ext is null");        }    }}
```

1. **Integration of TIMPush**

Supports CocoaPods integration. You need to add the component dependencies in the Podfile.

```
target 'YourAppName' do  # Uncommment the next line if you're using Swift or would like to use dynamic frameworks  use_frameworks!  use_modular_headers!    # Pods for Example  pod 'TXIMSDK_Plus_iOS_XCFramework'  # The version number "VERSION" can be obtained from the Update Log.  pod 'TIMPush', 'VERSION'end
```

Run the following command to install the TIMPush component.

```
pod install # If you cannot install the latest version of TUIKit, run the following command to update your local CocoaPods repository list.pod repo update
```

2. **Registration for push notifications (after successful registration, you can receive online push notifications)**

```
const int sdkAppId = 0; // Your sdkAppIdstatic const NSString *appKey = @""; // Client secret key[TIMPushManager registerPush:sdkAppId appKey:appKey succ:^(NSData * _Nonnull deviceToken) {} fail:^(int code, NSString * _Nonnull desc) {}];
```

> **Note:**After successfully registering for offline push service, you can obtain the unique push ID, RegistrationID, through the [getRegistrationID](https://www.tencentcloud.com/document/product/1047/60558#getRegistrationID) interface. Then, you can push messages to the specified device based on the RegistrationID.RegistrationID is the push unique identifier ID of the device. It is automatically generated after the default registration of the push service succeeds. It will change after uninstall.

3. **Implement click notification bar callback**

After receiving the push message, clicking the notification bar will trigger the component to callback the click event and pass through the offline message.

Custom click redirect implementation

Custom click redirect implementation (old solution)

> **Note:**It is recommended to place the registration callback timing in the didFinishLaunchingWithOptions function of the AppDelegate.

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {    [TIMPushManager addPushListener:self];    return YES;}#pragma mark - TIMPushListener- (void)onNotificationClicked:(NSString *)ext {        // Getting ext for Definition redirect}
```

You need to implement the `- onRemoteNotificationReceived` method in the AppDelegate.m file.

```
#pragma mark - TIMPush  - (BOOL)onRemoteNotificationReceived:(NSString *)notice {    //- If YES is returned, TIMPush will not execute the built-in TUIKit offline push parsing logic, leaving it entirely to you to handle.    //NSString *ext = notice;    //OfflinePushExtInfo *info = [OfflinePushExtInfo createWithExtString:ext];    //return YES;        //- If NO is returned, TIMPush will continue to execute the built-in TUIKit offline push parsing logic and continue to callback - navigateToBuiltInChatViewController:groupID: method.    return NO;}
```

1. **Integration of TIMPush**

This plugin is available on [pub.dev](https://pub.dev/packages/tencent_cloud_chat_push) under the package name: `tencent_cloud_chat_push`. You can include it in your pubspec.yaml dependency directory, or install it automatically with the following command.

```
tencent_cloud_chat_push
```

2. **Registration for push notifications (after successful registration, you can receive online push notifications)**

You can define a function to receive this callback and use it to navigate to the corresponding Session Page or your Business Page.

Example below:

```
void _onNotificationClicked({required String ext, String? userID, String? groupID}) {  print("_onNotificationClicked: $ext, userID: $userID, groupID: $groupID");  if (userID != null || groupID != null) {    // Navigate to the corresponding Message Page based on userID or groupID.  } else {    // Use your own parsing method based on the ext field to navigate to the corresponding page.  }}TencentCloudChatPush().registerPush(onNotificationClicked: _onNotificationClicked, sdkAppId: Your sdkAppId, appKey: "Client secret key");
```

> **Note:**After successfully registering for offline push service, you can obtain the unique push ID, RegistrationID, through the [getRegistrationID](https://www.tencentcloud.com/document/product/1047/60559#getRegistrationID) interface. Then, you can push messages to the specified device based on the RegistrationID.RegistrationID is the push unique identifier ID of the device. It is automatically generated after the default registration of the push service succeeds. It will change after uninstall.

3. **Implement click notification bar callback**

Android

iOS

The Application class inherits from TencentCloudChatPushApplication

```
Replace "package" with your own package name (usually auto-generated by Android Studio) import com.tencent.chat.flutter.push.tencent_cloud_chat_push.application.TencentCloudChatPushApplication;public class MyApplication extends TencentCloudChatPushApplication {    @Override    public void onCreate() {        super.onCreate();    }}
```

> **Note:**If you have already created your own Application for other purposes, directly `extend TencentCloudChatPushApplication` and ensure that the `onCreate()` function calls `super.onCreate();`.

`The AppDelegate class inherits from TIMPushDelegate`

```
import UIKit
```

1. **HBuilderX 4.29 has a bug, please use HBuilderX 4.36 or a higher version, and upgrade the**[**uni-app Tencent Cloud Push Service (Push)**](https://ext.dcloud.net.cn/plugin?id=20169)**to version 1.1.0 or higher.**
2. **Import the**[**uni-app Tencent Cloud Push Service (Push)**](https://ext.dcloud.net.cn/plugin?id=20169)**plugin into the project in HbuilderX. As shown in the figure:**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f0e08efc1d611ef8f945254007c27c5.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/651e4a91c1d611efa3e352540099c741.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6fa97cdfc1d611efb6165254001c06ec.png)

3. **Import and register Tencent Cloud Push Service (Push) in App.vue (after successful registration, you can receive online push notifications)**

> **Note:**After successfully registering for push service with `registerPush`, you can obtain the push ID identifier, RegistrationID, through `getRegistrationID`. You can push messages to specified devices based on RegistrationID.

```
// Integration of TencentCloud-Pushimport * as Push from '@/uni_modules/TencentCloud-Push';const SDKAppID = 0; // Your SDKAppIDconst appKey = ''; // Client secret keyPush.registerPush(SDKAppID, appKey, (data) => {        console.log('registerPush ok', data);        Push.getRegistrationID((registrationID) => {            console.log('getRegistrationID ok', registrationID);        });    }, (errCode, errMsg) => {        console.error('registerPush failed', errCode, errMsg);    });// Listen for notification bar click events and obtain push extension information.Push.addPushListener(Push.EVENT.NOTIFICATION_CLICKED, (res) => {    // res is the push extension info    console.log('notification clicked', res);});// Listen for online pushPush.addPushListener(Push.EVENT.MESSAGE_RECEIVED, (res) => {    // res is the message content    console.log('message received', res);});// Listen for online push revocationPush.addPushListener(Push.EVENT.MESSAGE_REVOKED, (res) => {    // res is the revoked message ID    console.log('message revoked', res);});
```

4. **Use cloud certificate to generate custom base**

Click HBuilderX's **Run > Run on Phone or Emulator > Create Custom Debug Base**, and use the cloud certificate to create an Android or iOS custom debug base. As shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8d2b9830c1d611ef8f945254007c27c5.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/983a723ec1d611efa3e352540099c741.png)

1. **Create a React Native project (skip this step if you already have a project)**

```
npx @react-native-community/cli@latest init MyReactNativeApp --version 0.75.0
```

2. **Integrate @tencentcloud/react-native-push**

```
npm install @tencentcloud/react-native-push --save
```

3. **Register for push notifications**

Copy the following code to `App.tsx` and replace `SDKAppID` and `appKey` with your application's information.

```
import Push from '@tencentcloud/react-native-push';const SDKAppID = 0; // Your SDKAppIDconst appKey = ''; // Client secret keyif (Push) {  Push.registerPush(SDKAppID, appKey, (data) => {      console.log('registerPush ok', data);      Push.getRegistrationID((registrationID) => {        console.log('getRegistrationID ok', registrationID);      });    }, (errCode, errMsg) => {      console.error('registerPush failed', errCode, errMsg);    }  );    // Listen for notification bar click events and obtain push extension information.  Push.addPushListener(Push.EVENT.NOTIFICATION_CLICKED, (res) => {    // res is the push extension info    console.log('notification clicked', res);  });    // Listen for online push  Push.addPushListener(Push.EVENT.MESSAGE_RECEIVED, (res) => {    // res is the message content    console.log('message received', res);  });  // Listen for online push recall  Push.addPushListener(Push.EVENT.MESSAGE_REVOKED, (res) => {    // res is the recalled message ID    console.log('message revoked', res);  });}
```

4. **Configure Native Modules and dependencies**

Android

iOS

1. Open the `MyReactNativeApp/android` directory using Android Studio.
2. Modify the project entry file.

The project entry file is MainApplication.kt

The project entry file is MainApplication.java

```
...import com.tencent.qcloud.rntimpush.TencentCloudPushApplication// Replace Application with TencentCloudPushApplicationclass MainApplication : TencentCloudPushApplication(), ReactApplication {  ...  // add TencentCloudPushPackage to the list of packages returned in ReactNativeHost's getPackages() method  override fun getPackages(): List<ReactPackage> =    PackageList(this).packages.apply {        // Packages that cannot be autolinked yet can be added manually here, for example:        // add(MyReactNativePackage())    }}
```

```
...import com.tencent.qcloud.rntimpush.TencentCloudPushApplication;// Replace Application with TencentCloudPushApplicationpublic class MainApplication extends TencentCloudPushApplication implements ReactApplication {  ...  // add TencentCloudPushPackage to the list of packages returned in ReactNativeHost's getPackages() method  @Override  protected List<ReactPackage> getPackages() {    List<ReactPackage> packages = new PackageList(this).getPackages();    // Packages that cannot be autolinked yet can be added manually here, for example:    // packages.add(new MyReactNativePackage());    return packages;  }  ...}
```

3. After completing the above steps, select `File > Sync Project with Gradle Files`.
1. Open `MyReactNativeApp/ios/MyReactNativeApp.xcworkspace` using XCode.
2. Go to the `MyReactNativeApp/ios` directory and install TIMPush.

```
pod install# If you cannot install the latest version, # execute the following command to update the local CocoaPods repository list.pod repo update
```

3. Enable push notification feature in the app. Open the Xcode project, and on the Project > Target > Capabilities page, select and add Push Notifications.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ccbb1b56c1d111efbcd1525400bf7822.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cfaa7d57c1d111efa3e352540099c741.png)

5. **Run on a real device (make sure to enable phone notification permissions and allow app notifications before testing.)**

From the root directory of the project, run the following command in the command prompt to install and launch your application on the device:

Android

iOS

```
npm run android
```

```
npm run ios
```

### Step 3: Specify RegistrationID for push

Finally, you can specify the registrationID in the [console](https://console.tencentcloud.com/im) for online push testing:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/82a3f3f9b2d511efa2e952540075b605.png)

> **Note:**For official use, please refer to the following methods.Send to all users or tagged users, for details, see [Pushing to All Users/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).Batch send to specified RegistrationID, for details, see [Single Push](https://www.tencentcloud.com/document/product/1047/67553).For details on the offline channel, see [manufacturer channel](https://www.tencentcloud.com/document/product/1047/60547) configuration.


---
*Source: [https://trtc.io/document/67555](https://trtc.io/document/67555)*
