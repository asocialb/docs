# Quick Integration

### Step 1: Download and add the configuration file

After completing the console manufacturer push information, download and add the configuration file to the project. Add the downloaded timpush-configs.json file to the assets directory of the application module:

| 1.Choose to download the configuration file timpush-configs.json | 2.Add to the project |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4f34a6fb30a11ef9d2952540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4dd53bab30a11ef8c01525400fdb830.png) |

### Step 2: Integrate the TIMPush plugin

```
// The version number "VERSION" can be obtained from the Update Log.// 1. Integration of the push main package is mandatoryimplementation 'com.tencent.timpush:timpush:VERSION'// 2. Integrate FCM push packageimplementation 'com.tencent.timpush:fcm:VERSION'// 3. If only the FCM channel is needed, the following packages do not need to be integrated; if you want to prioritize the FCM channel, call the API forceUseFCMPushChannel implementation 'com.tencent.timpush:huawei:VERSION'implementation 'com.tencent.timpush:xiaomi:VERSION'implementation 'com.tencent.timpush:oppo:VERSION'implementation 'com.tencent.timpush:vivo:VERSION'implementation 'com.tencent.timpush:honor:VERSION'implementation 'com.tencent.timpush:meizu:VERSION'
```

> **Note:**TIMPush requires integration with IMSDK version 7.6.5011 or above.For users without UI or who haven't integrated other plugins, it is necessary to add integration with [TUICore](https://github.com/TencentCloud/chat-uikit-android/tree/main/TUIKit/TUICore). It supports both source and Maven integration, as follows:def projects = this.rootProject.getAllprojects().stream().map { project -> project.name }.collect()api projects.contains("tuicore") ? project(':tuicore') : "com.tencent.liteav.tuikit:tuicore:latest.release"

- **vivo and Honor configuration**
- According to vivo and Honor manufacturer's access guidance, it is necessary to add the APPID and APPKEY to the manifest file, otherwise compilation issues will occur.

Method 1

Method 2

```
android {    ...        defaultConfig {                    ...                manifestPlaceholders = [                            "VIVO_APPKEY" : "`APPKEY` of the certificate assigned to your application",                            "VIVO_APPID" : "`APPID` of the certificate assigned to your application",                            "HONOR_APPID" : "`APPID` of the certificate assigned to your application"                ]        }}
```

```
// vivo begin<meta-data tools:replace="android:value"    android:name="com.vivo.push.api_key"    android:value="`APPKEY` of the certificate assigned to your application" /><meta-data tools:replace="android:value"    android:name="com.vivo.push.app_id"    android:value="`APPID` of the certificate assigned to your application" />// vivo end// honor begin<meta-data tools:replace="android:value"    android:name="com.hihonor.push.app_id"    android:value="`APPID` of the certificate assigned to your application" />// honor end
```

- **Huawei, HONOR, and Google FCM Adaptation**

Follow the vendor method to integrate the corresponding plugin and JSON configuration file.

> **Note:**The following adaptation for HONOR only requires configuration for version 7.7.5283 and above.

  1.1. Download the configuration file and place it under the root directory of the project:

Huawei

HONOR

Google FCM

Operation Path

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4e65838b30a11ef96e55254002693fd.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4fa15ddb30a11efa2e952540075b605.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7614a139c1cd11ef95c1525400d5f8ef.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4e55f35b30a11ef96e55254002693fd.png)

  1.2. Add the following configuration under buildscript -> dependencies in your project-level build.gradle file:

For Gradle version 7.1 and above

Gradle version 7.0

Versions Below Gradle 7.0

Add the following configuration under buildscript -> dependencies in your project-level build.gradle file:

```
buildscript {    dependencies {        ...        classpath 'com.google.gms:google-services:4.3.15'        classpath 'com.huawei.agconnect:agcp:1.6.0.300'        classpath 'com.hihonor.mcs:asplugin:2.0.1.300'    }}
```

In the project-level settings.gradle file, add the following repository configurations under pluginManagement -> repositories and dependencyResolutionManagement -> repositories:

```
pluginManagement {    repositories {        gradlePluginPortal()        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }        // Configure the Maven repository address for HMS Core SDK.        maven {url 'https://developer.huawei.com/repo/'}        maven {url 'https://developer.hihonor.com/repo'}    }}dependencyResolutionManagement {    ...    repositories {        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }        // Configure the Maven repository address for HMS Core SDK.        maven {url 'https://developer.huawei.com/repo/'}        maven {url 'https://developer.hihonor.com/repo'}    }    }}
```

Add the following configuration under buildscript in your project-level build.gradle file:

```
buildscript {    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }    dependencies {        ...        classpath 'com.google.gms:google-services:4.3.15'        classpath 'com.huawei.agconnect:agcp:1.6.0.300'        classpath 'com.hihonor.mcs:asplugin:2.0.1.300'    }}
```

Add the following repository configurations under dependencyResolutionManagement -> repositories in your project-level settings.gradle file:

```
dependencyResolutionManagement {    ...    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }}
```

Add the following configuration under buildscript and allprojects in the project-level build.gradle file:

```
buildscript {    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }    dependencies {        ...        classpath 'com.google.gms:google-services:4.3.15'        classpath 'com.huawei.agconnect:agcp:1.6.0.300'        classpath 'com.hihonor.mcs:asplugin:2.0.1.300'    }}allprojects {    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }}
```

  1.3. Add the following configuration in the app-level build.gradle file:

```
apply plugin: 'com.google.gms.google-services'apply plugin: 'com.huawei.agconnect' apply plugin: 'com.hihonor.mcs.asplugin'
```

After the above steps are performed, offline push notifications can be received.

> **Note:**If you want to integrate the TIMPush component as easily as possible, you need to use the login and logout APIs provided by [TUILogin](https://github.com/TencentCloud/chat-uikit-android/blob/main/TUIKit/TUICore/tuicore/src/main/java/com/tencent/qcloud/tuicore/TUILogin.java) of the TUICore component. The TIMPush component will automatically sense login/logout events. If you don't want to use the APIs provided by TUILogin, you need to manually call the [registerPush](https://www.tencentcloud.com/document/product/1047/67571#registerPush) interface of TIMPushManager after completing the login operation.If you only want to support the login-free push feature, you can register for push using the appKey parameter. For more details on sending messages in step 5, see [REST API - Initiate All/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).

### Step 3: Set obfuscation rules

In the proguard-rules.pro file, add TIMPush-related classes to the non-obfuscation list:

```
-keep class com.tencent.qcloud.** { *; }-keep class com.tencent.timpush.** { *; }
```

### Step 4: Message Delivery Statistics Configuration

If you need to collect data reach statistics, please complete the configuration as follows:

Huawei

HONOR

vivo

Meizu

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c508eb4ab30a11efbfb3525400bdab9d.png)

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/huawei

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/huawei

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/huawei

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/huawei

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/huawei

China: https://api.im.qcloud.com/v3/offline_push_report/huawei

> **Note:**Huawei Push Certificate ID <= 11344, using Huawei Push v2 interface, does not support Reach and Click Receipt, please regenerate and update Certificate ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4e60894b30a11ef9dc0525400329841.png)

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/honor

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/honor

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/honor

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/honor

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/honor

China: https://api.im.qcloud.com/v3/offline_push_report/honor

| Callback Address Configuration | Configure Receipt ID in the IM Console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c5100d0bb30a11ef9dc0525400329841.png) Receipt Address:Singapore :https://apisgp.im.qcloud.com/v3/offline_push_report/vivoKorea:https://apikr.im.qcloud.com/v3/offline_push_report/vivoUSA: https://apiusa.im.qcloud.com/v3/offline_push_report/vivoGermany: https://apiger.im.qcloud.com/v3/offline_push_report/vivoIndonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/vivoChina: https://api.im.qcloud.com/v3/offline_push_report/vivo | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c5091d38b30a11ef970f525400d5f8ef.png) |

| Enable Receipt Switch | Configure Receipt Address |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c500ffe7b30a11efa2e952540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4f40bc1b30a11ef9d2952540055f650.png) |

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/meizu

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/meizu

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/meizu

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/meizu

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/meizu

China: https://api.im.qcloud.com/v3/offline_push_report/meizu

> **Note:**After turning on the receipt toggle, please make sure the receipt address is correctly configured. Not configuring it or configuring the wrong address will affect the push notification feature.

> **Note:**No configuration for message delivery statistics is required for other supported manufacturers.FCM currently does not support the push notification statistics feature.

### Step 5: Set the offline push parameters when sending a message

When you call [sendMessage](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMMessageManager.html#a28e01403acd422e53e999f21ec064795) to send messages, you can use [V2TIMOfflinePushInfo](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html) to set offline push parameters. Use the [setExt](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a9346ecab2e35ff516b24c27b0584a9a2) method of V2TIMOfflinePushInfo to set custom ext data. When users receive an offline push and launch the app, they can get the ext field in the click notification callback, and then jump to the specified UI interface based on the content of the ext field. For more information, see the sendMessage() method in [ChatProvider](https://github.com/TencentCloud/chat-uikit-android/blob/main/TUIKit/TUIChat/tuichat/src/main/java/com/tencent/qcloud/tuikit/tuichat/model/ChatProvider.java):

```
V2TIMOfflinePushInfo v2TIMOfflinePushInfo = new V2TIMOfflinePushInfo();v2TIMOfflinePushInfo.setTitle("Push Title");v2TIMOfflinePushInfo.setDesc("Push Content");OfflinePushExtInfo offlinePushExtInfo = new OfflinePushExtInfo();offlinePushExtInfo.getBusinessInfo().setSenderId("senderID");offlinePushExtInfo.getBusinessInfo().setSenderNickName("senderNickName");if (chatInfo.getType() == V2TIMConversation.V2TIM_GROUP) {    offlinePushExtInfo.getBusinessInfo().setChatType(V2TIMConversation.V2TIM_GROUP);    offlinePushExtInfo.getBusinessInfo().setSenderId("groupID");}v2TIMOfflinePushInfo.setExt(new Gson().toJson(offlinePushExtInfo).getBytes());// For OPPO, you must set the `ChannelID` to receive push messages. The `ChannelID` must be identical with that in the console.v2TIMOfflinePushInfo.setAndroidOPPOChannelID("tuikit");v2TIMOfflinePushInfo.setAndroidHuaWeiCategory("IM");v2TIMOfflinePushInfo.setAndroidVIVOCategory("IM");final V2TIMMessage v2TIMMessage = message.getTimMessage();String msgID = V2TIMManager.getMessageManager().sendMessage(v2TIMMessage, isGroup ? null : userID, isGroup ? groupID : null,    V2TIMMessage.V2TIM_PRIORITY_DEFAULT, false, v2TIMOfflinePushInfo, new V2TIMSendCallback<V2TIMMessage>() {        @Override        public void onProgress(int progress) {        }        @Override        public void onError(int code, String desc) {            TUIChatUtils.callbackOnError(callBack, TAG, code, desc);        }        @Override        public void onSuccess(V2TIMMessage v2TIMMessage) {            TUIChatLog.v(TAG, "sendMessage onSuccess:" + v2TIMMessage.getMsgID());            message.setMsgTime(v2TIMMessage.getTimestamp());            TUIChatUtils.callbackOnSuccess(callBack, message);        }    });
```

### Step 6: Parsing Offline Push Messages

After receiving the push message, clicking the notification bar will trigger the component to callback the click event and pass through the offline message.

Custom click redirect implementation

Custom click redirect implementation (old solution)

> **Note:**It is recommended to place the registration callback timing in the onCreate() function of the application.Console configuration follow-up actions are configured as follows, select **Open the specified interface within the app** and do not modify, use the default values.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a100b540c1cd11ef87c05254005ef0f7.png)

```
TIMPushManager.getInstance().addPushListener(new TIMPushListener() {    @Override    public void onNotificationClicked(String ext) {        Log.d(TAG, "onNotificationClicked =" + ext);        // Getting ext for Definition redirect                // Example: Redirect to the corresponding chat interface        OfflinePushExtInfo offlinePushExtInfo = null;        try {            offlinePushExtInfo = new Gson().fromJson(extString, OfflinePushExtInfo.class);            if (offlinePushExtInfo.getBusinessInfo().getChatAction() == OfflinePushExtInfo.REDIRECT_ACTION_CHAT) {                String senderId = offlinePushExtInfo.getBusinessInfo().getSenderId();                if (TextUtils.isEmpty(senderId)) {                    return;                }                TUIUtils.startChat(senderId, offlinePushExtInfo.getBusinessInfo().getSenderNickName(), offlinePushExtInfo.getBusinessInfo().getChatType());            }        } catch (Exception e) {            Log.e(TAG, "getOfflinePushExtInfo e: " + e);        }    }});
```

The component will notify the application in the form of a callback or broadcast, and the application can configure the app's page jump in the callback.

> **Note:**It is recommended to place the registration callback timing in the onCreate() function of the application.Console configuration follow-up actions are configured as follows, select **Open the specified interface within the app** and do not modify, use the default values.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c50f34d0b30a11ef8c01525400fdb830.png)

1. The callback method is as follows:

```
TUICore.registerEvent(TUIConstants.TIMPush.EVENT_NOTIFY, TUIConstants.TIMPush.EVENT_NOTIFY_NOTIFICATION, new ITUINotification() {        @Override        public void onNotifyEvent(String key, String subKey, Map<String, Object> param) {            Log.d(TAG, "onNotifyEvent key = " + key + "subKey = " + subKey);            if (TUIConstants.TIMPush.EVENT_NOTIFY.equals(key)) {                if (TUIConstants.TIMPush.EVENT_NOTIFY_NOTIFICATION.equals(subKey)) {                    if (param != null) {                        String extString = (String)param.get(TUIConstants.TIMPush.NOTIFICATION_EXT_KEY);                        // Getting ext for Definition redirect                                                // Example: Redirect to the corresponding chat interface                        OfflinePushExtInfo offlinePushExtInfo = null;                        try {                            offlinePushExtInfo = new Gson().fromJson(extString, OfflinePushExtInfo.class);                            if (offlinePushExtInfo.getBusinessInfo().getChatAction() == OfflinePushExtInfo.REDIRECT_ACTION_CHAT) {                                String senderId = offlinePushExtInfo.getBusinessInfo().getSenderId();                                if (TextUtils.isEmpty(senderId)) {                                    return;                                }                                TUIUtils.startChat(senderId, offlinePushExtInfo.getBusinessInfo().getSenderNickName(), offlinePushExtInfo.getBusinessInfo().getChatType());                            }                        } catch (Exception e) {                            Log.e(TAG, "getOfflinePushExtInfo e: " + e);                        }                    }                }            }        }    });
```

2. The broadcast method is as follows:

```
/ Dynamic registration broadcastIntentFilter intentFilter = new IntentFilter();intentFilter.addAction(TUIConstants.TIMPush.NOTIFICATION_BROADCAST_ACTION);LocalBroadcastManager.getInstance(context).registerReceiver(localReceiver, intentFilter);// Broadcast Receiverpublic class OfflinePushLocalReceiver extends BroadcastReceiver {    public static final String TAG = OfflinePushLocalReceiver.class.getSimpleName();    @Override    public void onReceive(Context context, Intent intent) {        DemoLog.d(TAG, "BROADCAST_PUSH_RECEIVER intent = " + intent);        if (intent != null) {            String ext = intent.getStringExtra(TUIConstants.TIMPush.NOTIFICATION_EXT_KEY);            // Getting ext for Definition redirect                        // Example: Redirect to the corresponding chat interface            OfflinePushExtInfo offlinePushExtInfo = null;            try {                offlinePushExtInfo = new Gson().fromJson(extString, OfflinePushExtInfo.class);                if (offlinePushExtInfo.getBusinessInfo().getChatAction() == OfflinePushExtInfo.REDIRECT_ACTION_CHAT) {                    String senderId = offlinePushExtInfo.getBusinessInfo().getSenderId();                    if (TextUtils.isEmpty(senderId)) {                        return;                    }                    TUIUtils.startChat(senderId, offlinePushExtInfo.getBusinessInfo().getSenderNickName(), offlinePushExtInfo.getBusinessInfo().getChatType());                }             } catch (Exception e) {                 Log.e(TAG, "getOfflinePushExtInfo e: " + e);             }        } else {            Log.e(TAG, "onReceive ext is null");        }    }}
```

Congratulations! You have completed the integration of the push plugin. Please be reminded: After the trial period or subscription expires, the push service (including regular message offline push, all-staff/Tag push, etc.) will automatically cease. To avoid affecting the normal use of your services, please make sure to [purchase](https://buy.tencentcloud.com/avc?activeId=plugin&position=20012840&regionId=9)/[renew](https://buy.tencentcloud.com/avc?activeId=plugin&position=20012840&regionId=9) in advance.

> **Note:**Manufacturer offline channels all have [message categorization mechanism](https://trtc.io/document/60576). Different types will also contain different push policies.If the push demand belongs to IM type push and you want the push to be delivered in a timely manner, you need to set your application as the corresponding push type according to the manufacturer's rule setting. It will be categorized as a system message type or an important message type with high priority.Conversely, there are limits on the quantity and frequency of offline push, which may not be pushed to the device in a timely manner.If you are unable to receive push notifications after integration, please first use the [Troubleshooting Tool](https://trtc.io/document/60541) to check the specific reasons. To view push indicator data, please use [Statistics](https://trtc.io/document/60540) query.For the All/Tag Push feature, please refer to: [RESTful APIs - Pushing to All/Tagged Users](https://trtc.io/document/60561).


---
*Source: [https://trtc.io/document/50034](https://trtc.io/document/50034)*
