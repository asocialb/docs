# Quick Integration

### Effect Showcase

| Xiaomi 11 Pro (Integrated with [CallKit](https://ext.dcloud.net.cn/plugin?id=9035))![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4bfadd75c3ff11ef91c2525400e889b2.gif) | iPhone 13![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4bd0c577c3ff11efad4f52540044a08e.gif) | Samsung Galaxy A23 Overseas Version (Google FCM Push)![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4c731323c3ff11ef82565254005ef0f7.gif) |
| --- | --- | --- |

### Step 1: Create a React Native project (skip this step if you already have one)

```
npx @react-native-community/cli@latest init MyReactNativeApp --version 0.75.0
```

### Step 2: **Entering the MyReactNativeApp Directory**, Integrating @tencentcloud/react-native-push

npm

yarn

```
npm install @tencentcloud/react-native-push --save
```

```
yarn add @tencentcloud/react-native-push
```

### Step 3:**Register for Push Notifications**

Copy the following code to `App.tsx` and replace `SDKAppID` and `appKey` with your application's information.

> **Note:**After successfully registering the push service with `registerPush`, you can obtain the push ID, namely RegistrationID, through `getRegistrationID`. You can push messages to the specified RegistrationID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ff952fddc3fe11ef82565254005ef0f7.png)

```
import { TUILogin } from '@tencentcloud/tui-core';import { TUIConversationService } from '@tencentcloud/chat-uikit-engine';import Push from '@tencentcloud/react-native-push';const SDKAppID = 0; // Your SDKAppIDconst appKey = ''; // Client Keyconst userID = ''; // Your userIDconst userSig = ''; // Encrypted signature string generated from UserIDTUILogin.login({  SDKAppID,  userID,  userSig,  useUploadPlugin: true,  framework: 'rn',}).then(() => {  if (Push) {    Push.setRegistrationID(userID, () => {      console.log('setRegistrationID ok', userID);    });    Push.registerPush(SDKAppID, appKey, (data) => {        console.log('registerPush ok', data);        Push.getRegistrationID((registrationID) => {          console.log('getRegistrationID ok', registrationID);        });      }, (errCode, errMsg) => {        console.error('registerPush failed', errCode, errMsg);      }    );        // Listen for notification bar click events to get push extension information    Push.addPushListener(Push.EVENT.NOTIFICATION_CLICKED, (res) => {      console.log('notification clicked', res);      // Parse extended information and navigate to the corresponding session      try {        const data = JSON.parse(res);        const conv_type = data?.entity?.chatType === 1 ? 'C2C' : 'GROUP';        TUIConversationService.switchConversation(`${conv_type}${data.entity.sender}`);        navigation.navigate('Chat');      } catch (error) {        console.log('error', error);      }    });        // Listen for online push    Push.addPushListener(Push.EVENT.MESSAGE_RECEIVED, (res) => {      // res is the message content      console.log('message received', res);    });      // Listen for online push recall    Push.addPushListener(Push.EVENT.MESSAGE_REVOKED, (res) => {      // res is the ID of the recalled message      console.log('message revoked', res);    });  }});
```

### Step 4: Configuring Vendor Push

Android

iOS

1. After completing the vendor push information in the console, download the `timpush-configs.json` file from the console and add it to the `MyReactNativeApp/android/app/src/main/assets` directory of the project. If this directory does not exist, please create it manually. As shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/88303c6bbde611efb9d2525400329841.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/451a2bdda66011ef897b52540075b605.png)

2. Huawei, HONOR, vivo, FCM.

FCM

Huawei

HONOR

vivo

When you need to support FCM push, you must configure the `google-services.json` file in the `MyReactNativeApp/android/app` directory (**Please note! Not in the**`MyReactNativeApp/android/app/src/main/assets directory`). As shown in the picture:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/45466171a66011efba3e5254002693fd.png)

To support Huawei push, you need to configure the `agconnect-services.json` file in the `MyReactNativeApp/android/app/src/main/assets/` directory. As shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/451a28f8a66011ef897b52540075b605.png)

To support HONOR Push, you need to configure `appID` in the `MyReactNativeApp/android/app/build.gradle` file. As shown in the figure:

```
......android {    ......    defaultConfig {        ......        manifestPlaceholders = [          "HONOR_APPID" : ""        ]    }}
```

| Obtain HONOR appID | Configure HONOR appID |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a32cb50bbde611efb9d2525400329841.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1c9b1c11bdea11ef8a945254002693fd.png) |

To support vivo Push, you need to configure `appID` and `appKey` in the `MyReactNativeApp/android/app/build.gradle` file. As shown in the figure:

```
......android {    ......    defaultConfig {        ......        manifestPlaceholders = [          "VIVO_APPKEY" : "0",          "VIVO_APPID" : "0",        ]    }}
```

| Obtain vivo appID && appKey | Configure vivo appID && appKey |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d39bdc16bde611ef8a945254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/149a22f1bdea11efb9d2525400329841.png) |

1. Please upload the iOS APNs Push Certificate obtained in the manufacturer configuration step to the Chat Console. The Chat Console will assign a Certificate ID to you, as shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e4ec5a17bde611ef928f525400d5f8ef.png)

2. In the `MyReactNativeApp/ios/MyReactNativeApp` directory, create a new `Resources` folder and a new `timpush-configs.json` file. Edit `timpush-configs.json` and enter the certificate ID obtained from the console, as shown below:

```
{  "businessID": "Your Certificate ID"}
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7e8db86db3a111ef9d2952540055f650.png)

3. Open the MyReactNativeApp project in XCode, right-click the project > **Add Files to "MyReactNativeApp"**, and add the `timpush-configs.json` directory to the project. As shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6fa80b3db3a111ef8b1b525400f69702.png)

### Step 5: **Configuring Native Modules and Dependencies**

Android

iOS

> **Note:**Please ensure the package name in `timpush-configs.json` matches the `applicationId` value in `MyReactNativeApp/android/app/build.gradle`. Inconsistency will result in offline push notifications being unavailable. Note.

1. Open the `MyReactNativeApp/android` directory with Android Studio.
2. Modify the project entry file.

The project entry file is: MainApplication.kt

The Project Entry File Is: MainApplication.java

```
...import com.tencent.qcloud.rntimpush.TencentCloudPushApplication// Replace Application with TencentCloudPushApplicationclass MainApplication : TencentCloudPushApplication(), ReactApplication {  ...  //  add TencentCloudPushPackage to the list of packages returned in ReactNativeHost's getPackages() method  override fun getPackages(): List<ReactPackage> =    PackageList(this).packages.apply {        // Packages that cannot be autolinked yet can be added manually here, for example:        // add(MyReactNativePackage())    }}
```

```
...import com.tencent.qcloud.rntimpush.TencentCloudPushApplication;// Replace Application with TencentCloudPushApplicationpublic class MainApplication extends TencentCloudPushApplication implements ReactApplication {  ...  // add TencentCloudPushPackage to the list of packages returned in ReactNativeHost's getPackages() method  @Override  protected List<ReactPackage> getPackages() {    List<ReactPackage> packages = new PackageList(this).getPackages();    // Packages that cannot be autolinked yet can be added manually here, for example:    // packages.add(new MyReactNativePackage());    return packages;  }  ...
```

3. Edit the `android/build.gradle` file to update `repositories`, `dependencies`, and `allprojects`.

```
buildscript {    ...    repositories {        ...        google()        mavenCentral()        maven { url 'https://mirrors.tencent.com/nexus/repository/maven-public/' }        // Configure the Maven repository address for HMS Core SDK.        maven { url 'https://developer.huawei.com/repo/' }        maven { url 'https://developer.hihonor.com/repo' }    }    dependencies {        ...        // If the com.android.tools.build:gradle in your created project does not have a version number, set it to 8.5.0        // classpath("com.android.tools.build:gradle:8.5.0")        classpath 'com.google.gms:google-services:4.3.15'        classpath 'com.huawei.agconnect:agcp:1.9.1.301'        classpath 'com.hihonor.mcs:asplugin:2.0.1.300'    }}allprojects {    repositories {        mavenCentral()        maven { url 'https://mirrors.tencent.com/nexus/repository/maven-public/' }        // Configure the Maven repository address for HMS Core SDK.        maven { url 'https://developer.huawei.com/repo/' }        maven { url 'https://developer.hihonor.com/repo' }    }}...
```

4. Edit the `android/app/build.gradle` file to update `plugin` and `defaultConfig`.

```
...// If your APP requires FCM push notifications, uncomment the following line// apply plugin: 'com.google.gms.google-services'apply plugin: 'com.huawei.agconnect'apply plugin: 'com.hihonor.mcs.asplugin'...android {    ...    defaultConfig {        ...        manifestPlaceholders = [            "VIVO_APPKEY" : "0",            "VIVO_APPID" : "0",            "HONOR_APPID" : ""        ]    }}
```

5. After completing the above steps, select **File > Sync Project with Gradle Files**.
1. Open **MyReactNativeApp/ios/MyReactNativeApp.xcworkspace** with XCode.
2. Go to the `MyReactNativeApp/ios` directory and install TChatPush.

```
pod install # If you cannot install the latest version, run the following command to update your local CocoaPods repository listpod repo update
```

3. Enable push notification feature in the app. Open the Xcode project, and select and add **Push Notifications** on the **Project > Target > Capabilities** page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/940c2887bde811efba8d525400f69702.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a47f374cbde811ef8d65525400fdb830.png)

### Step 6: **Running on a Real Device (Make sure to enable notification permissions on your phone before testing, allowing the app to send notifications.)**

Starting from the project's root directory, run the following command in the command prompt to install and launch your app on the device:

Android

iOS

```
npm run android
```

```
npm run ios
```

### Step 7: Message Push Reach Statistics

If you need to collect data on delivery, please complete the setup as follows:

Huawei

HONOR

vivo

Meizu

iOS

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2ec540f4d48211ee9409525400c26da5.png)

**Receipt Address:**

- Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/huawei
- Korea: https://apikr.im.qcloud.com/v3/offline_push_report/huawei
- USA: https://apiusa.im.qcloud.com/v3/offline_push_report/huawei
- Germany: https://apiger.im.qcloud.com/v3/offline_push_report/huawei
- Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/huawei
- China: https://api.im.qcloud.com/v3/offline_push_report/huawei

> **Note:**Huawei Push Certificate ID <= 11344, using Huawei Push v2 version interface does not support reach and click receipt, please regenerate and update the certificate ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f14cca5d48211eeb0d9525400461a83.png)

**Receipt Address:**

- Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/honor
- Korea: https://apikr.im.qcloud.com/v3/offline_push_report/honor
- USA: https://apiusa.im.qcloud.com/v3/offline_push_report/honor
- Germany: https://apiger.im.qcloud.com/v3/offline_push_report/honor
- Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/honor
- China: https://api.im.qcloud.com/v3/offline_push_report/honor

| Callback Address Configuration | Receipt ID Configuration in the Chat Console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2edc891dd48211ee89c5525400170219.png) **Receipt Address:**Singapore :https://apisgp.im.qcloud.com/v3/offline_push_report/vivoKorea:https://apikr.im.qcloud.com/v3/offline_push_report/vivoUSA: https://apiusa.im.qcloud.com/v3/offline_push_report/vivoGermany: https://apiger.im.qcloud.com/v3/offline_push_report/vivoIndonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/vivoChina: https://api.im.qcloud.com/v3/offline_push_report/vivo | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e65222bbde711efb9d2525400329841.png) |

| Enable Receipt Switch | Configure Receipt Address |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/afbbfe09be8511efa28d525400329841.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f1021e6d48211ee89c5525400170219.png) |

**Receipt Address:**

- Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/meizu
- Korea: https://apikr.im.qcloud.com/v3/offline_push_report/meizu
- USA: https://apiusa.im.qcloud.com/v3/offline_push_report/meizu
- Germany: https://apiger.im.qcloud.com/v3/offline_push_report/meizu
- Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/meizu
- China: https://api.im.qcloud.com/v3/offline_push_report/meizu

> **Note:**After enabling the Receipt Switch, please make sure the Receipt Address is configured correctly. Failing to configure or configuring the wrong address will affect the push feature.

For iOS push reach statistics configuration, see [**Statistics of Push Arrival Rate**](https://www.tencentcloud.com/document/product/1047/60553#).

No configuration is needed for other supported manufacturers; FCM does not support the push notification statistics feature.


---
*Source: [https://trtc.io/document/67584](https://trtc.io/document/67584)*
