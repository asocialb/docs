# Quick Integration

### Step 1: Integrate the Message Push Plugin

The package name of this plugin on [pub.dev](https://pub.dev/packages/tencent_cloud_chat_push) is: `tencent_cloud_chat_push`. You can add it to the pubspec.yaml dependency directory or execute the following command to install it automatically.

```
tencent_cloud_chat_push
```

### Step 2: Push Parameter Configuration

iOS

Android

Please upload the iOS APNs Push Certificate obtained in the Manufacturer Configuration step to the Chat Console.

The Chat console will allocate a Certificate ID for you, see the image below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1be67b9cc1cd11ef95c1525400d5f8ef.png)

To register for push notifications, you need to pass in this Certificate ID (apnsCertificateID):

```
TencentCloudChatPush().registerPush(apnsCertificateID: Your configured Certificate ID);
```

After completing the console manufacturer push information, download and add the configuration file to the project. Add the downloaded timpush-configs.json file to the `android/app/src/main/assets` directory of the project. If the directory does not exist, please create it manually.

| 1.Choose to download the configuration file timpush-configs.json | 2.Add to the project |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d543ba94c1cc11ef95c1525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c4734e7b30d11ef970f525400d5f8ef.png) |

### Step 3: Client Code Configuration

This step requires writing some native code, such as Swift, Java, XML, etc.

Do not worry, you can directly copy our provided code into the specified file according to the instructions.

iOS

Android

You can edit using Xcode, or directly in Visual Studio Code or Android Studio.

Open the `ios/Runner/AppDelegate.swift` file and paste the circled code below into it. The effect is shown in the picture. The code is attached after the picture.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ffc5fce1c1cc11efbeb4525400f69702.png)

```
import UIKitimport Flutter// Add these two import linesimport TIMPushimport tencent_cloud_chat_push// Add `, TIMPushDelegate` to the following line@UIApplicationMain@objc class AppDelegate: FlutterAppDelegate, TIMPushDelegate {    override func application(        _ application: UIApplication,        didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?    ) -> Bool {        GeneratedPluginRegistrant.register(with: self)        return super.application(application, didFinishLaunchingWithOptions: launchOptions)    }        // To be deprecatedï¼please use the new field businessID below.    @objc func offlinePushCertificateID() -> Int32 {        return TencentCloudChatPushFlutterModal.shared.offlinePushCertificateID();    }    // Add this function    @objc func businessID() -> Int32 {        return TencentCloudChatPushFlutterModal.shared.businessID();    }    // Add this function    @objc func applicationGroupID() -> String {        return TencentCloudChatPushFlutterModal.shared.applicationGroupID()    }        // Add this function    @objc func onRemoteNotificationReceived(_ notice: String?) -> Bool {        TencentCloudChatPushPlugin.shared.tryNotifyDartOnNotificationClickEvent(notice)        return true    }}
```

It is recommended to use Android Studio to complete this part of the editing.

In your project android path, create a new Application file class in the same directory as `MainActivity`, for example, you can name it `MyApplication.java`.

If you have already customized an Application class, you can directly reuse it without creating a new one.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7cdf8dd9b30d11ef8c01525400fdb830.png)

Paste the following code into that file as shown above:

```
Replace the package with your own. Generally, Android Studio will generate it automatically;import com.tencent.chat.flutter.push.tencent_cloud_chat_push.application.TencentCloudChatPushApplication;public class MyApplication extends TencentCloudChatPushApplication {    @Override    public void onCreate() {        super.onCreate();    }}
```

> **Note:**If you have already created your own Application for other purposes, directly `extend TencentCloudChatPushApplication` and ensure that the `onCreate()` function calls `super.onCreate();`.

Open the `android/app/src/main/AndroidManifest.xml` file and add an `<application>` tag to specify an `android:name` parameter, pointing to the custom `Application` class you just created. As shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c84410db30d11ef96e55254002693fd.png)

### Step 4: Client Manufacturer Configuration

iOS

Android

This step is not required for iOS.

Open the android/app/build.gradle file and add the dependencies configuration at the end. According to your needs, introduce all or some of the following manufacturer push packages. The native push capability of a manufacturer is enabled only after the corresponding manufacturerâs push package is introduced.

```
dependencies {     // The version number "VERSION" can be obtained from the Update Log.     // Huawei     implementation 'com.tencent.timpush:huawei:VERSION'     // XiaoMi     implementation 'com.tencent.timpush:xiaomi:VERSION'     // OPPO     implementation 'com.tencent.timpush:oppo:VERSION'     // vivo     implementation 'com.tencent.timpush:vivo:VERSION'     // Honor     implementation 'com.tencent.timpush:honor:VERSION'     // Meizu     implementation 'com.tencent.timpush:meizu:VERSION'     // Google Firebase Cloud Messaging (Google FCM)     implementation 'com.tencent.timpush:fcm:VERSION'}
```

- **Vivo and Honor compatibility**
- According to Vivo and Honor manufacturer access guidelines, the APPID and APPKEY need to be added to the manifest file.

Method 1

Method 2

```
// android/app/build.gradleandroid {    ...        defaultConfig {                    ...                manifestPlaceholders = [                            "VIVO_APPKEY" : "`APPKEY` of the certificate assigned to your application",                            "VIVO_APPID" : "`APPID` of the certificate assigned to your application",                            "HONOR_APPID" : "`APPID` of the certificate assigned to your application"        ]        }}
```

```
// android/app/src/main/AndroidManifest.xml// Vivo begin<meta-data tools:replace="android:value"    android:name="com.vivo.push.api_key"    android:value="`APPKEY` of the certificate assigned to your application" /><meta-data tools:replace="android:value"    android:name="com.vivo.push.app_id"    android:value="`APPID` of the certificate assigned to your application" />// Vivo end// Honor begin<meta-data tools:replace="android:value"    android:name="com.hihonor.push.app_id"    android:value="`APPID` of the certificate assigned to your application" />// Honor end
```

- **Huawei, HONOR, and Google FCM Adaptation**

Follow the vendor method to integrate the corresponding plugin and JSON configuration file.

> **Note:**The following adaptation for HONOR only requires configuration for version 7.7.5283 and above.

  1.1. Download the configuration file and place it under the root directory/Android/app of the project.

Huawei

HONOR

Google FCM

Operation Path

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c8c830fb30d11ef96e55254002693fd.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c6d737db30d11ef8c01525400fdb830.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ad4885d2c2b411efb6165254001c06ec.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c8302ccb30d11efbfb3525400bdab9d.png)

  1.2. Add the following configuration under buildscript -> dependencies in your project-level build.gradle file:

For Gradle version 7.1 and above

Gradle version 7.0

Versions Below Gradle 7.0

Add the following configuration under buildscript -> dependencies in your project-level build.gradle file:

```
buildscript {    dependencies {        ...        classpath 'com.huawei.agconnect:agcp:1.6.0.300'        classpath 'com.hihonor.mcs:asplugin:2.0.1.300'        classpath 'com.google.gms:google-services:4.4.0'    }}
```

Add the following repository configuration under buildscript -> repositories and allprojects -> repositories in your project-level settings.gradle file:

```
pluginManagementbuildscript {    repositories {        gradlePluginPortal()        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }        // Configure the Maven repository address for HMS Core SDK.        maven {url 'https://developer.huawei.com/repo/'}        maven {url 'https://developer.hihonor.com/repo'}    }}allprojects {    ...    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }    }}
```

Add the following configuration under buildscript in your project-level build.gradle file:

```
buildscript {    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }    dependencies {        ...        classpath 'com.google.gms:google-services:4.2.0'        classpath 'com.huawei.agconnect:agcp:1.4.1.300'        classpath 'com.hihonor.mcs:asplugin:2.0.1.300'    }}
```

Add the following repository configuration under allprojects -> repositories in your project-level settings.gradle file:

```
allprojects {    ...    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }}
```

Add the following configuration under buildscript and allprojects in the project-level build.gradle file:

```
buildscript {    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }    dependencies {        ...        classpath 'com.google.gms:google-services:4.2.0'        classpath 'com.huawei.agconnect:agcp:1.4.1.300'        classpath 'com.hihonor.mcs:asplugin:2.0.1.300'    }}allprojects {    repositories {        mavenCentral()maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }// Configure the Maven repository address for HMS Core SDK.maven {url 'https://developer.huawei.com/repo/'}maven {url 'https://developer.hihonor.com/repo'}    }}
```

  1.3. Add the following configuration in the app-level build.gradle file:

```
apply plugin: 'com.google.gms.google-services'apply plugin: 'com.huawei.agconnect' apply plugin: 'com.hihonor.mcs.asplugin'
```

### Step 5: Handle message click callback and parse parameters

If you need to customize the parsing of received remote push notifications, you can implement it as follows:

Custom click redirect implementation

Custom click redirect implementation (old solution)

> **Note:**It is recommended to register the callback in the main() function at the program entry.For console configuration, click on 'Subsequent Actions' and configure as follows, choose **Open the specified interface within the app**, and the plugin users will by default fill in the jump parameters.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/76efa102138011f09b3252540044a08e.png)

```
TIMPushListener timPushListener = TIMPushListener(      onNotificationClicked: (String ext) {        debugPrint("ext: $ext");        // Getting ext for Definition redirect              }    );tencentCloudChatPush.addPushListener(listener: timPushListener);
```

Please define a function to receive the push message click callback event.

Define the function with the parameter format `{required String ext, String? userID, String? groupID}`.

- Among them, the ext field carries the complete ext information specified by the sender. If not specified, there is a default value. You can parse this field to navigate to the corresponding page.
- The userID and groupID fields are automatically parsed by the plugin from the ext Json String to get the single chat userID and group chat groupID information. If you do not customize the ext field, the ext field is specified by the SDK or UIKit by default, and you can use this default parsing. If parsing fails, it will be null.

You can define a function to receive this callback and use it to navigate to the corresponding Session Page or your Business Page.

Example below:

```
void _onNotificationClicked({required String ext, String? userID, String? groupID}) {  print("_onNotificationClicked: $ext, userID: $userID, groupID: $groupID");  if (userID != null || groupID != null) {    // Redirect to the corresponding Message page based on userID or groupID.  } else {    // Based on the ext field, write your own parsing method to redirect to the corresponding page.  }}
```

### Step 6: Register the Push Plugin

**Please register the push plugin immediately after IM login is completed and before using other plugins (e.g., CallKit). Note, do not call in the main method of the Flutter program entry.**

After successfully calling the `TencentCloudChatPush().registerPush` method, you can receive offline push notifications.

```
TencentCloudChatPush().registerPush(    onNotificationClicked: _onNotificationClicked,    apnsCertificateID: Your configured Certificate ID);
```

### Step 7: Message Push Reach Statistics

If you need to collect data reach statistics, please complete the configuration as follows:

Huawei

HONOR

vivo

Meizu

iOS

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c714f1bb30d11ef970f525400d5f8ef.png)

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/huawei

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/huawei

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/huawei

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/huawei

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/huawei

China: https://api.im.qcloud.com/v3/offline_push_report/huawei

> **Note:**Huawei Push Certificate ID <= 11344, using Huawei Push v2 version interface, does not support reach and click receipt. Please regenerate and update the Certificate ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c68b1ddb30d11ef8c01525400fdb830.png)

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/honor

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/honor

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/honor

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/honor

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/honor

China: https://api.im.qcloud.com/v3/offline_push_report/honor

| Callback Address Configuration | Configure Receipt ID in the IM Console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7ca6e5c4b30d11ef9d2952540055f650.png) Receipt Address:Singapore :https://apisgp.im.qcloud.com/v3/offline_push_report/vivoKorea:https://apikr.im.qcloud.com/v3/offline_push_report/vivoUSA: https://apiusa.im.qcloud.com/v3/offline_push_report/vivoGermany: https://apiger.im.qcloud.com/v3/offline_push_report/vivoIndonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/vivoChina: https://api.im.qcloud.com/v3/offline_push_report/vivo | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7ca6cec2b30d11efbfb3525400bdab9d.png) |

| Enable Receipt Switch | Configure Receipt Address |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7caa4f86b30d11efa2e952540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c7487fab30d11efa2e952540075b605.png) |

Receipt Address:

Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/meizu

Korea: https://apikr.im.qcloud.com/v3/offline_push_report/meizu

USA: https://apiusa.im.qcloud.com/v3/offline_push_report/meizu

Germany: https://apiger.im.qcloud.com/v3/offline_push_report/meizu

Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/meizu

China: https://api.im.qcloud.com/v3/offline_push_report/meizu

> **Note:**After turning on the receipt toggle, please make sure the receipt address is correctly configured. Not configuring it or configuring the wrong address will affect the push notification feature.

For iOS push reach statistics configuration, please refer to [**Push Arrival Rate Statistics**](https://www.tencentcloud.com/document/product/1047/60553#a76b331f-3d49-48c9-99a9-5301c7d7fa99).

No configuration needed for other supported manufacturers. FCM currently does not support push notification statistics feature.

Congratulations! You have completed the integration of the push plugin. Please be reminded: After the trial period or subscription expires, the push service (including regular message offline push, all-staff/Tag push, etc.) will automatically cease. To avoid affecting the normal use of your services, please make sure to [purchase](https://console.trtc.io/subscription?activeId=plugin)/[renew](https://console.trtc.io/subscription?activeId=plugin) in advance.

> **Note:**If you are unable to receive push notifications after integration, please first use the [Troubleshooting Tool](https://www.tencentcloud.com/document/product/1047/60541) to check the specific reasons. Also, pay attention to the [Vendor Message Classification Mechanism](https://www.tencentcloud.com/document/product/1047/60576).To view push indicator data, please use [Statistics](https://www.tencentcloud.com/document/product/1047/60540) query.For the All/Tag Push feature, please refer to: [RESTful APIs - Initiate All/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).


---
*Source: [https://trtc.io/document/50032](https://trtc.io/document/50032)*
