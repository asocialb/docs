# Custom Definition Badge

Android

iOS

Flutter

uni-app

### Supported Vendors

Huawei.

### Configuration Method

To configure the Huawei badge parameters in the console, set them to the application's startup class, for example, "com.tencent.qcloud.tim.demo.SplashActivity". The component will automatically parse and update the badge; otherwise, it will not update the badge.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d199a92b2d811ef9d2952540055f650.png)

By default, when the App goes into the background, the ChatSDK will set the total number of unread Chat messages as the badge. If the App is integrated with offline push, when a new offline push notification is received, the App badge will increment by 1 based on the baseline badge (default is the total number of unread Chat messages, or the custom-defined badge if one has been set).

### Configuration Method

If you want to customize the badge, follow these steps:

1. The App calls the [- (void)setAPNSListener:(id<V2TIMAPNSListener>)apnsListener](https://im.sdk.qcloud.com/doc/en/categoryV2TIMManager_07APNS_08.html#a62e1694cf9e1d65b76f90064cbcbb683) interface to set the listener.
2. The App implements the [- (uint32_t)onSetAPPUnreadCount](https://im.sdk.qcloud.com/doc/en/protocolV2TIMAPNSListener-p.html#a164265ae900e0ddeb6d6393786a548ba) interface and returns the custom-defined badge number.

```
// 1. Set the listener- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {    // Listen for push notifications    [V2TIMManager.sharedInstance setAPNSListener:self];    // Listen for unread conversation counts    [[V2TIMManager sharedInstance] setConversationListener:self];    return YES;}// 2. Save the unread count after it changes- (void)onTotalUnreadMessageCountChanged:(UInt64)totalUnreadCount {    self.unreadNumber = totalUnreadCount;}// 3. Report custom-defined unread count after the app is pushed to the background/** After the application enters the background, customize the app's unread count. If not handled, the default app unread count is the sum of all conversation unread counts *  <pre> * *   - (uint32_t)onSetAPPUnreadCount { *       return 100;  // Custom-defined unread count *   } * *  </pre> */- (uint32_t)onSetAPPUnreadCount {    // 1. Get the custom-defined badge    uint32_t customBadgeNumber = ...        // 2. Add the IM message unread count    customBadgeNumber += self.unreadNumber;        // 3. Report to the IM server via IMSDK    return customBadgeNumber;}
```

Please refer to Android and iOS for configuration. The methods called have the same names in the Flutter version of the IM SDK.

### Supported Vendors

Huawei.

### Configuration Method

#### Step 1. Configure the Huawei badge parameters in the console to the application's startup class.

> **Note:**The startup class for the uniapp application is `io.dcloud.PandoraEntry`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d198072b2d811ef96e55254002693fd.png)

#### Step 2. Listen to changes in the total unread count of the Chat SDK to set the badge quantity.

1. Listen to the Chat SDK total unread message count updates through [TOTAL_UNREAD_MESSAGE_COUNT_UPDATED](https://web.sdk.qcloud.com/im/doc/v3/zh-cn/module-EVENT.html#.TOTAL_UNREAD_MESSAGE_COUNT_UPDATED).
2. Set the badge number through `plus.runtime.setBadgeNumber`.

```
let onTotalUnreadMessageCountUpdated = function(event) {  const unreadCount = event.data; // Total unread count of the current session  plus.runtime.setBadgeNumber(unreadCount); // Set the badge number};chat.on(TencentCloudChat.EVENT.TOTAL_UNREAD_MESSAGE_COUNT_UPDATED, onTotalUnreadMessageCountUpdated);
```


---
*Source: [https://trtc.io/document/60572](https://trtc.io/document/60572)*
