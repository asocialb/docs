# Android

> **Note:**If you need to use products such as Chat, CallKit, RoomKit, LiveKit, etc. simultaneously, please refer to [Chat Quick Integration Solution](https://www.tencentcloud.com/document/product/1047/50034).

### Step 1: Download and add the configuration file

After completing the console manufacturer push information, download and add the configuration file to the project. Add the downloaded timpush-configs.json file to the assets directory of the application module:

| 1.Choose to download the configuration file timpush-configs.json | 2.Add to the project |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a59da675b2d611ef9d2952540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a5603402b2d611ef8c01525400fdb830.png) |

### Step 2: Integrate TIMPush

```
// The version number "VERSION" can be obtained from the Update Log.// 1. Integration of the push main package is mandatoryimplementation 'com.tencent.timpush:timpush:VERSION'implementation 'com.tencent.liteav.tuikit:tuicore:VERSION'// 2. Integrate FCM push packageimplementation 'com.tencent.timpush:fcm:VERSION'// 3. If only the FCM channel is needed, the following packages do not need to be integrated; if you want to prioritize the FCM channel, call the API forceUseFCMPushChannel implementation 'com.tencent.timpush:huawei:VERSION'implementation 'com.tencent.timpush:xiaomi:VERSION'implementation 'com.tencent.timpush:oppo:VERSION'implementation 'com.tencent.timpush:vivo:VERSION'implementation 'com.tencent.timpush:honor:VERSION'implementation 'com.tencent.timpush:meizu:VERSION'
```

- **vivo and Honor configuration**

According to vivo and Honor manufacturer's access guidance, it is necessary to add the APPID and APPKEY to the manifest file, otherwise compilation issues will occur.

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

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a5647d5db2d611efbfb3525400bdab9d.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a57337e6b2d611ef970f525400d5f8ef.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c005637bc1cf11efa3e352540099c741.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a57306c5b2d611ef9d2952540055f650.png)

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
pluginManagement {    repositories {        gradlePluginPortal()        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }        // Configure the Maven repository address for HMS Core SDK.        maven {url 'https://developer.huawei.com/repo/'}        maven {url 'https://developer.hihonor.com/repo'}    }}dependencyResolutionManagement {    ...    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }    }}
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

### Step 3: Set obfuscation rules

In the proguard-rules.pro file, add TIMPush-related classes to the non-obfuscation list:

```
-keep class com.tencent.qcloud.** { *; }-keep class com.tencent.timpush.** { *; }
```

### Step 4: Register for Push Notifications

After the push registration is successfully called, you can receive offline push notifications.

```
TIMPushManager.getInstance().registerPush(context, your sdkAppId, "client key", new TIMPushCallback() {    @Override        public void onSuccess(Object data) {        }            @Override        public void onError(int errCode, String errMsg, Object data) {            }});
```

### Step 5. Message Delivery Statistics Configuration

If you need to collect data reach statistics, please complete the configuration as follows:

Huawei

HONOR

vivo

Meizu

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a5b613f3b2d611ef8b1b525400f69702.png)

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/huawei

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/huawei

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/huawei

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/huawei

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/huawei

China: https://api.im.qcloud.com/v3/offline_push_report/huawei

> **Note:**Huawei Push Certificate ID <= 11344, using Huawei Push v2 interface, does not support Reach and Click Receipt, please regenerate and update Certificate ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a5859f6eb2d611efa2e952540075b605.png)

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/honor

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/honor

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/honor

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/honor

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/honor

China: https://api.im.qcloud.com/v3/offline_push_report/honor

| Callback Address Configuration | Configure Receipt ID in the IM Console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a59ed268b2d611efa2e952540075b605.png) Receipt Address:Singapore :https://apisgp.im.qcloud.com/v3/offline_push_report/vivoKorea:https://apikr.im.qcloud.com/v3/offline_push_report/vivoUSA: https://apiusa.im.qcloud.com/v3/offline_push_report/vivoGermany: https://apiger.im.qcloud.com/v3/offline_push_report/vivoIndonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/vivoChina: https://api.im.qcloud.com/v3/offline_push_report/vivo | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a58fe1cbb2d611ef9dc0525400329841.png) |

| Enable Receipt Switch | Configure Receipt Address |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a5b15b4db2d611ef970f525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a5a910e9b2d611ef970f525400d5f8ef.png) |

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/meizu

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/meizu

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/meizu

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/meizu

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/meizu

China: https://api.im.qcloud.com/v3/offline_push_report/meizu

> **Note:**After turning on the receipt toggle, please make sure the receipt address is correctly configured. Not configuring it or configuring the wrong address will affect the push notification feature.

> **Note:**No configuration for message delivery statistics is required for other supported manufacturers.FCM currently does not support the push notification statistics feature.

### Step 6: Send push messages

For detailed interface description, see: [REST API Interface - Initiate All-staff/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).

### Step 7: Parse offline push messages

After receiving the push message, clicking the notification bar will trigger the component to callback the click event and pass through the offline message.

Custom click redirect implementation

Custom click redirect implementation (old solution)

> **Note:**It is recommended to place the registration callback timing in the onCreate() function of the application.Console configuration follow-up actions are configured as follows, select **Open the specified interface within the app** and do not modify, use the default values.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6d7edb57c1dd11efa3e352540099c741.png)

```
TIMPushManager.getInstance().addPushListener(new TIMPushListener() {    @Override    public void onNotificationClicked(String ext) {        Log.d(TAG, "onNotificationClicked =" + ext);        // Getting ext for Definition redirect            }});
```

The component will notify the application in the form of a callback or broadcast, and the application can configure the app's page jump in the callback.

> **Note:**It is recommended to place the registration callback timing in the onCreate() function of the application.Console configuration follow-up actions are configured as follows, select **Open the specified interface within the app** and do not modify, use the default values.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dcf35d69c1cf11efb44452540044a08e.png)

1. The callback method is as follows:

```
TUICore.registerEvent(TUIConstants.TIMPush.EVENT_NOTIFY, TUIConstants.TIMPush.EVENT_NOTIFY_NOTIFICATION, new ITUINotification() {        @Override        public void onNotifyEvent(String key, String subKey, Map<String, Object> param) {            Log.d(TAG, "onNotifyEvent key = " + key + "subKey = " + subKey);            if (TUIConstants.TIMPush.EVENT_NOTIFY.equals(key)) {                if (TUIConstants.TIMPush.EVENT_NOTIFY_NOTIFICATION.equals(subKey)) {                    if (param != null) {                        String extString = (String)param.get(TUIConstants.TIMPush.NOTIFICATION_EXT_KEY);                        // Getting ext for Definition redirect                                             }                }            }        }    });
```

2. The broadcast method is as follows:

```
// Dynamic Broadcast RegistrationIntentFilter intentFilter = new IntentFilter();intentFilter.addAction(TUIConstants.TIMPush.NOTIFICATION_BROADCAST_ACTION);LocalBroadcastManager.getInstance(context).registerReceiver(localReceiver, intentFilter);// Broadcast Receiverpublic class OfflinePushLocalReceiver extends BroadcastReceiver {    public static final String TAG = OfflinePushLocalReceiver.class.getSimpleName();    @Override    public void onReceive(Context context, Intent intent) {        DemoLog.d(TAG, "BROADCAST_PUSH_RECEIVER intent = " + intent);        if (intent != null) {            String ext = intent.getStringExtra(TUIConstants.TIMPush.NOTIFICATION_EXT_KEY);            // Getting ext for Definition redirect        } else {            Log.e(TAG, "onReceive ext is null");        }    }}
```

Congratulations! You have completed the integration of the push plugin. Please be reminded: After the trial period or subscription expires, the push service (including regular message offline push, all-staff/Tag push, etc.) will automatically cease. To avoid affecting the normal use of your services, please make sure to [purchase](https://buy.tencentcloud.com/avc?activeId=plugin&position=20012840&regionId=9)/[renew](https://buy.tencentcloud.com/avc?activeId=plugin&position=20012840&regionId=9) in advance.

> **Note:**Manufacturer offline channels all have [message categorization mechanism](https://trtc.io/document/60576?platform=web&product=chat&menulabel=uikit). Different types will also contain different push policies.If the push demand belongs to IM type push and you want the push to be delivered in a timely manner, you need to set your application as the corresponding push type according to the manufacturer's rule setting. It will be categorized as a system message type or an important message type with high priority.Conversely, there are limits on the quantity and frequency of offline push, which may not be pushed to the device in a timely manner.If you are unable to receive push notifications after integration, please first use the [Troubleshooting Tool](https://trtc.io/document/60541?platform=web&product=chat&menulabel=uikit) to check the specific reasons. To view push indicator data, please use [Statistics](https://trtc.io/document/60540?platform=web&product=chat&menulabel=uikit) query.For the All/Tag Push feature, please refer to: [RESTful APIs - Initiate All/Tag Push](https://trtc.io/document/60561?platform=web&product=chat&menulabel=uikit).


---
*Source: [https://trtc.io/document/60552](https://trtc.io/document/60552)*
