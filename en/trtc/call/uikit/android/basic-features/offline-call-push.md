# Offline Call Push

The TIMPush plugin is a powerful paid feature that brings VoIP call notification mechanisms to the Google platform. Combined with the data messaging capabilities of `Firebase Cloud Messaging (FCM)` and the `TUICallKit` component, it provides an incoming call display interface with a customizable layout.

> **Note:**Phones with Google Mobile Services.The FCM data message feature is only available in TIMPush **7.9.5668** and later versions.Support for TUICallKit is limited to **2.3** and later versions.

This article provides a detailed introduction on how to integrate the TIMPush plugin into the TUICallKit component, utilize FCM's data messages, and achieve banner views for audio and video incoming calls.

## Integration effect

TUICallKit has successfully integrated FCM data messages on the GitHub sample project. You can quickly implement the feature's normal operation by referring to the [Call UIKit sample project](https://github.com/tencentyun/TUICallKit/tree/main/Android). The following diagram shows the incoming call views after receiving an call invitation when the **application is in the foreground, background**, or when the **application process does not exist.**

| The display view when the **application is in the foreground** | The display view when the **application is in the background** or **offline** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7403235ffd3911eea33752540095b445.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/74164c7afd3911ee82c9525400275b90.png) |

> **Note:**To achieve a good call experience as shown above, it is recommended to enable "notification", "Display over other apps" and "Background pop-ups" permissions in your application. For more details, refer to: [Relevant permissions enabled](https://www.tencentcloud.com/document/product/647/50999#4f15e437-fb41-4a95-8f7c-5c8473ad063b).

## Preparation Requirements

1. Register your application to the [FCM Push Platform](https://console.firebase.google.com/) to obtain parameters such as **AppID** and **AppKey**, as well as the `google-services.json` file.
2. log in to the [Instant Messaging Chat Console](https://console.intl.cloud.tencent.com/im), go to **Push Management** > **Access Settings** feature tab, select FCM, add FCM's certificate, and select **Transparent transmission(data) message**.

| FCM Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0d855493fd4f11eeb7f5525400a7e516.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3c0a7789fd4f11eeb7f5525400a7e516.png) |

## Quick Integration

#### 1. Download and add the configuration file

After completing the push information in the console,  download `timpush-configs.json` file and add the file to the `assets` directory of the application module, and add the `google-services.json` to the project app directory.

| Download the file timpush-configs.json | Download the file google-services.json | Add to the project |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5b20fa55fd5011eea33752540095b445.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9c9acee8fd5011eea33752540095b445.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7409e016fd3911ee82c9525400275b90.png) |

#### 2. Integrate the TIMPush plugin

In the `app/build.gradle`file, add the following dependency.

```
implementation "com.tencent.timpush:timpush:latest.release"implementation "com.tencent.timpush:fcm:latest.release"
```

> **Note:**TIMPush requires integration with Chat SDK in version **7.9.5668** and above.You can modify the version of the Chat SDK in the `tuicallkit-kt/build.gradle` file.

#### 3. Complete project configuration

- In the project-level `build.gradle` file, under `buildscript -> dependencies`section, add the following configuration.

```
buildscript {    dependencies {        classpath 'com.google.gms:google-services:4.3.15'    }}
```

- In the `app/build.gradle` file, add the following configuration.

```
apply plugin: 'com.google.gms.google-services'
```

- In the `app/proguard-rules.pro` file, add TIMPush related classes to the non-aliasing list.

```
-keep class com.tencent.qcloud.** { *; }-keep class com.tencent.timpush.** { *; }
```

- In the `app/build.gradle` file, change the application package name to your actual application package name.

```
applicationId 'com.****.callkit'
```

#### 4. Comlete automatic login

In your `application` class, listener to the TIMPush event and implement automatic login method by your self.

Kotlin

Java

```
import com.tencent.qcloud.tuicore.TUIConstants
import com.tencent.qcloud.tuicore.TUICore
import com.tencent.qcloud.tuicore.interfaces.ITUINotification

class BaseApplication : Application() {
    override fun onCreate() {
        super.onCreate()

        TUICore.registerEvent(TUIConstants.TIMPush.EVENT_IM_LOGIN_AFTER_APP_WAKEUP_KEY,
            TUIConstants.TIMPush.EVENT_IM_LOGIN_AFTER_APP_WAKEUP_SUB_KEY) { key, subKey, param ->
            if (TUIConstants.TIMPush.EVENT_IM_LOGIN_AFTER_APP_WAKEUP_KEY == key                 && TUIConstants.TIMPush.EVENT_IM_LOGIN_AFTER_APP_WAKEUP_SUB_KEY == subKey) {
                //you need to login again to launch call activity, please implement this method by yourself
                autoLogin()
            }
        }
    }
}
```

```
import com.tencent.qcloud.tuicore.TUIConstants;
import com.tencent.qcloud.tuicore.TUICore;
import com.tencent.qcloud.tuicore.interfaces.ITUINotification;public class BaseApplication extends Application {    @Override    public void onCreate() {        super.onCreate();        TUICore.registerEvent(TUIConstants.TIMPush.EVENT_IM_LOGIN_AFTER_APP_WAKEUP_KEY,                TUIConstants.TIMPush.EVENT_IM_LOGIN_AFTER_APP_WAKEUP_SUB_KEY, new ITUINotification() {                    @Override                    public void onNotifyEvent(String key, String subKey, Map<String, Object> param) {                        if (TUIConstants.TIMPush.EVENT_IM_LOGIN_AFTER_APP_WAKEUP_KEY.equals(key)                                && TUIConstants.TIMPush.EVENT_IM_LOGIN_AFTER_APP_WAKEUP_SUB_KEY.equals(subKey)) {                            //you need to login again to launch call activity, please implement this method by yourself                            autoLogin();                        }                    }                });    }}
```

After completing the above steps, you can use the offline push capability in TUICallKit.

> **Note:**If your Android application encounters issues when receiving push notifications or pulling up pages, you can refer to the [Called party's call display policy](https://trtc.io/document/51022?platform=android&product=call&menulabel=android#bfe2ed33-0611-4ca2-9aa8-f75b2a443e4a) for troubleshooting.

## Advanced features

#### Custom Ringtone

If you wish to customize the ringtone, you can replace the `tuicallkit-kt/src/main/res/raw/phone_ringing.mp3` file.

> **Note:**After replacing the ringtone, no matter if the application is in the foreground, background, or offline, the ringtone will be the one that has been replaced.After replacement, the ringtone received by other manufacturer's mobile phones upon invitation will also be the replaced one.

## FAQs

#### **1. Unable to pop up the incoming call UI after the application is killed**

- Confirm receipt of push. If push cannot be received, refer to step 1 in the above document **Quick Integration** to see if the certificates have been  correctly added to the Chat cosole.
- Make sure the console has selected FCM **Transparent transmission(data) message**, in accordance with the second step of the above **Preparation Requirements.**
- Confirm receipt of data messages, filter logs (keyword: TIMPush), and check the following logs for printing (if messages are not received.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/73fce76afd3911eea33752540095b445.png)

- Confirm implementation of **automatic login**. It is only after  **automatic login** that call requests are pulled and the incoming call UI is displayed.

#### 2. **Relevant permissions enabled**

To ensure a good calling experience, it is recommended to enable "notification" permissions, "Display over other apps(Floating window)" and "Background pop-ups" permissions in your application. The specific methods are as follows:

Code guidance

Manually Enabled

- **Notification permissions**: For showcasing push notifications: please refer to [Notification runtime permissions](https://developer.android.com/develop/ui/views/notifications/notification-permission) and [Request runtime permissions](https://developer.android.com/training/permissions/requesting#request-permission) and implement according to business needs.
- **Floating window permission**: Used for displaying custom incoming call notifications and call floating windows.
- **Background pop-ups:** Used to pop up the interface when the application is in the background (for example: on a VIVO phone).

```
fun requestPermission(context: Context?) {    //In TUICallKit,Please open both OverlayWindows and Background pop-ups permission.    PermissionRequester.newInstance(         PermissionRequester.FLOAT_PERMISSION, PermissionRequester.BG_START_PERMISSION)        .request()}
```

After the application is installed, you can long-press the application Icon, select "Application Information", then enable "notification" permission, "Display over other applications," and "Background pop-ups" permissions. Alternatively, you can go to `Mobile Phone > System Settings > Application Management > Application` to manually enable these permissions.

| Pixel 4a | VIVO |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d980d6cfd6c11ee9f79525400a7e516.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4d9623dafd6c11ee848952540095b445.png) |

## Suggestions and Feedback

If you have any suggestions or feedback, please contact `info_rtc@tencent.com`.


---
*Source: [https://trtc.io/document/50999](https://trtc.io/document/50999)*
