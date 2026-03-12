# Custom Definition Click Redirect

Android

iOS

Flutter

After receiving an offline push, the notification bar will display the push message as shown. Clicking on the notification bar can custom open the application interface.

1. For console configuration, click on 'Subsequent Actions' and configure as follows, choose **Open the specified interface within the app**, and the plugin users will by default fill in the jump parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8ab0d83eb2ee11ef8b1b525400f69702.png)

2. After receiving the push message, clicking the notification bar will trigger the component to callback the click event and pass through the offline message.

Custom click redirect implementation

Custom click redirect implementation (old solution)

> **Note:**It is recommended to place the registration callback timing in the onCreate() function of the application.

```
TIMPushManager.getInstance().addPushListener(new TIMPushListener() {    @Override    public void onNotificationClicked(String ext) {        Log.d(TAG, "onNotificationClicked =" + ext);        // Getting ext for Definition redirect            }});
```

The component will notify the application in the form of a callback or broadcast, and the application can configure the app's page jump in the callback.

> **Note:**It is recommended to place the registration callback timing in the onCreate() function of the application.

1. The callback method is as follows:

```
TUICore.registerEvent(TUIConstants.TIMPush.EVENT_NOTIFY, TUIConstants.TIMPush.EVENT_NOTIFY_NOTIFICATION, new ITUINotification() {        @Override        public void onNotifyEvent(String key, String subKey, Map<String, Object> param) {            Log.d(TAG, "onNotifyEvent key = " + key + "subKey = " + subKey);            if (TUIConstants.TIMPush.EVENT_NOTIFY.equals(key)) {                if (TUIConstants.TIMPush.EVENT_NOTIFY_NOTIFICATION.equals(subKey)) {                    if (param != null) {                        String extString = (String)param.get(TUIConstants.TIMPush.NOTIFICATION_EXT_KEY);                        // Getting ext for Definition redirect                                             }                }            }        }    });
```

2. The broadcast method is as follows:

```
// Dynamic Broadcast RegistrationIntentFilter intentFilter = new IntentFilter();intentFilter.addAction(TUIConstants.TIMPush.NOTIFICATION_BROADCAST_ACTION);LocalBroadcastManager.getInstance(context).registerReceiver(localReceiver, intentFilter);// Broadcast Receiverpublic class OfflinePushLocalReceiver extends BroadcastReceiver {    public static final String TAG = OfflinePushLocalReceiver.class.getSimpleName();    @Override    public void onReceive(Context context, Intent intent) {        DemoLog.d(TAG, "BROADCAST_PUSH_RECEIVER intent = " + intent);        if (intent != null) {            String ext = intent.getStringExtra(TUIConstants.TIMPush.NOTIFICATION_EXT_KEY);            // Getting ext for Definition redirect        } else {            Log.e(TAG, "onReceive ext is null");        }    }}
```

If you need to customize the parsing of received remote push notifications, you can implement it as follows:

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

### **Step 1: Manufacturer Configuration**

For console configuration, click on 'Subsequent Actions' and configure as follows, choose **Open the specified interface within the app**, and the plugin users will by default fill in the jump parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8e5b15ffb2ee11efa2e952540075b605.png)

### **Step 2: Client Code Configuration**

Refer to [Client Code Configuration](https://www.tencentcloud.com/document/product/1047/60555#f78cb409-148d-4fc3-ba07-197d00c9441f), complete the configuration.

### **Step 3: Handle Message Click Callback and Parse Parameters**

If you need to customize the parsing of received remote push notifications, you can implement it as follows:

Custom click redirect implementation

Custom click redirect implementation (old solution)

> **Note:**It is recommended to register the callback in the main() function at the program entry.

```
TIMPushListener timPushListener = TIMPushListener(      onNotificationClicked: (String ext) {        debugPrint("ext: $ext");        // Getting ext for Definition redirect              }    );tencentCloudChatPush.addPushListener(listener: timPushListener);
```

Please define a function to accept push message click callback events.

Define the function with the parameter format `{required String ext, String? userID, String? groupID}`.

- Among them, the ext field carries the complete ext information specified by the sender. If not specified, there is a default value. You can parse this field to navigate to the corresponding page.
- The userID and groupID fields are automatically parsed by the plugin from the ext Json String to get the single chat userID and group chat groupID information. If you do not customize the ext field, the ext field is specified by the SDK or UIKit by default, and you can use this default parsing. If parsing fails, it will be null.

You can define a function to receive this callback and use it to navigate to the corresponding Session Page or your Business Page.

Example below:

```
void _onNotificationClicked({required String ext, String? userID, String? groupID}) {  print("_onNotificationClicked: $ext, userID: $userID, groupID: $groupID");  if (userID != null || groupID != null) {    // Redirect to the corresponding Message page based on userID or groupID.  } else {    // Based on the ext field, write your own parsing method to redirect to the corresponding page.  }}
```

**Please note, do not call in the main method of the Flutter program entry.**

After successfully calling the `TencentCloudChatPush().registerPush` method, you can receive offline push notifications.

```
TencentCloudChatPush().registerPush(    onNotificationClicked: _onNotificationClicked,    sdkAppId: Your sdkAppId,    appKey: "client key",    apnsCertificateID: Your configured Certificate ID);
```


---
*Source: [https://trtc.io/document/60575](https://trtc.io/document/60575)*
