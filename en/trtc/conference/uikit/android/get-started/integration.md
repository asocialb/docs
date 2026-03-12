# Integration

This article will introduce how to complete the integration of the `TUIRoomKit` Component in the shortest time. By following this document, you will complete the following key steps within ten minutes and ultimately obtain an audio/video conference function with a complete UI interface.

Conference interface and partial function display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7f398b2931f911ef9d17525400f69702.png)

## Environment preparation

- Minimum compatibility with Android 4.4 (SDK API Level 19), recommended to use Android 5.0 (SDK API Level 21) and above.
- Android Studio 3.5 and above (Gradle 3.5.4 and above).
- Mobile devices with Android 4.4 and above.

## Step 1: Activate the service

Before initiating a meeting with TUIRoomKit, you need to activate the exclusive multi-person audio and video interaction service for TUIRoomKit on the console. For specific steps, please refer to [Activate Service](https://www.tencentcloud.com/document/product/647/59973#).

## Step 2: Download the TUIRoomKit component

1. Clone/download the code in [Github](https://github.com/tencentyun/TUIRoomKit), and then copy the timcommon and tuiroomkit subdirectories in the Android directory to the same level directory as the app in your current project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a8a86c2c314411ef9d17525400f69702.png)

## Step 3: Project configuration

1. Find the `setting.gradle (or settings.gradle.kts) `file in the project root directory and add the following code to it. Its function is to import the tuiroomkit component into your current project.

setting.gradle

settings.gradle.kts

```
include ':timcommon'include ':tuiroomkit'
```

```
include (":timcommon")
include (":tuiroomkit")
```

2. Find the `build.gradle (or build.gradle.kts)` file in the app directory and add the following code to it. Its function is to declare the current app's dependence on the newly added tuiroomkit component.

build.gradle

build.gradle.kts

```
api project(':tuiroomkit')
```

```
api(project(":tuiroomkit"))
```

3. Since we use the reflection feature of Java inside the SDK, we need to add some classes in the SDK to the unobfuscated list, so you need to add the following code to the **proguard-rules.pro** file:

```
  -keep class com.tencent.** { *; }
```

4. Find the AndroidManifest.xml file in the app directory, and add tools:replace="android:allowBackup" to the application node to override the settings within the component and use your own settings.

```
  // app/src/main/AndroidManifest.xml  <application
    android:name=".DemoApplication"
    android:allowBackup="false"
    android:icon="@drawable/app_ic_launcher"
    android:label="@string/app_name"
    android:largeHeap="true"
    android:theme="@style/AppTheme"
    tools:replace="android:allowBackup">
```

## Step 4: Login

Add the following code to your project. Its function is to complete the component login by calling the relevant interface in TUILogin.**This step is extremely critical**, because you can only use the various functions of TUIRoomKit normally after logging in, so please be patient and check whether the relevant parameters are configured correctly:

Java

Kotlin

```
import com.tencent.qcloud.tuicore.TUILogin;
import com.tencent.qcloud.tuicore.interfaces.TUICallback;import com.tencent.cloud.tuikit.roomkit.debug.GenerateTestUserSig;String userId = "denny" // Please replace with your UserIDint sdkAppId = 1400000001 // Please replace with the sdkAppId obtained in step oneString sdkSecretKey = "xxxx" // Please replace with your sdkSecretKeyString userSig = GenerateTestUserSig.genTestUserSig(sdkAppId, userId, sdkSecretKey);TUILogin.login(context,     sdkAppId,    userId,    userSig,    new TUICallback() {        @Override        public void onSuccess() {        }            @Override        public void onError(int errorCode, String errorMessage) {        }});
```

```
import com.tencent.qcloud.tuicore.TUILogin
import com.tencent.qcloud.tuicore.interfaces.TUICallbackimport com.tencent.cloud.tuikit.roomkit.debug.GenerateTestUserSigval userId = "denny" // Please replace with your UserIDval sdkAppId = 1400000001 // Please replace with the sdkAppId obtained in step oneval sdkSecretKey = "xxxx" // Please replace with your sdkSecretKeyval userSig = GenerateTestUserSig.genTestUserSig(sdkAppId, userId, sdkSecretKey)TUILogin.login(this,    sdkAppId,    userId,    userSig,    object : TUICallback() {      override fun onSuccess() {      }      override fun onError(errorCode: Int, errorMessage: String) {      }    })}
```

| **TUILogin.login Parameter Descriptionï¼** |
| --- |
| Here is a detailed introduction to several key parameters needed in the login function:**SDKAppID**ï¼Get it in the last step of [activating the service](https://www.tencentcloud.com/document/product/647/54843#087dff27-11d0-42ec-bb14-202b4b333452).**UserID**ï¼The ID of the current user, a string type, only allowed to contain English letters (a-z and A-Z), numbers (0-9), hyphens (-) and underscores (_).**UserSig**ï¼Use the SDKSecretKey obtained in step 4 of [activating the service](https://www.tencentcloud.com/document/product/647/54843#087dff27-11d0-42ec-bb14-202b4b333452) to encrypt the SDKAppID, UserID and other information to obtain the UserSig, which is an authentication ticket used by Tencent Cloud to identify whether the current user can use TRTC services. You can generate a temporarily available UserSig through the auxiliary tools in the [console](https://console.tencentcloud.com/im/tool-usersig).**Noteï¼****Development environment**ï¼If you are in the local development and debugging stage, you can use the local GenerateTestUserSig.genTestUserSig() function to generate a userSig. The SDKSecretKey in this method can be easily decompiled and reverse-engineered. Once your key is leaked, attackers can steal your Tencent Cloud traffic.**production environment**ï¼If your project is to be launched, please use the method of [server-side generation of UserSig](https://www.tencentcloud.com/document/product/647/35166#). |

## Step 5: Start your first conference

After [TUILogin.login](https://www.tencentcloud.com/document/product/647/54843#05771e5e-e6ca-48f7-b99d-40b9a7c99cc4) succeeds, refer to the following code to initiate a conference.

Java

Kotlin

```
// Please replace "123456" with your customized  conference numberConferenceDefine.StartConferenceParams params = new ConferenceDefine.StartConferenceParams("123456");Intent intent = new Intent(this, ConferenceMainActivity.class);intent.putExtra(KEY_START_CONFERENCE_PARAMS, params);startActivity(intent);
```

```
// Please replace "123456" with your customized  conference numberval params = ConferenceDefine.StartConferenceParams("123456")val intent = Intent(this, ConferenceMainActivity::class.java)intent.putExtra(KEY_START_CONFERENCE_PARAMS, params);startActivity(intent)
```

## Step 6: Join conference

After [TUILogin.login](https://www.tencentcloud.com/document/product/647/54843#05771e5e-e6ca-48f7-b99d-40b9a7c99cc4) succeeds, refer to the following code to join the conference.

Java

Kotlin

```
// Please replace "123456" with your customized  conference numberConferenceDefine.JoinConferenceParams params = new ConferenceDefine.JoinConferenceParams("123456");Intent intent = new Intent(this, ConferenceMainActivity.class);intent.putExtra(KEY_JOIN_CONFERENCE_PARAMS, params);startActivity(intent);
```

```
// Please replace "123456" with your customized  conference numberval params = ConferenceDefine.JoinConferenceParams("123456")val intent = Intent(this, ConferenceMainActivity::class.java)intent.putExtra(KEY_JOIN_CONFERENCE_PARAMS, params);startActivity(intent)
```

## Interface display

When you successfully complete steps 1 - 6, the interface will appear as follows:

| Conference main interface | User list |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e1d95643314211ef8eb4525400bdab9d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fcce9c0a314211efbe0a525400fdb830.png) |

## Common problem

If you encounter problems with access and use, please see the [FAQ](https://www.tencentcloud.com/document/product/647/52820#).

## Suggestions and Feedback

If you have any suggestions or feedback, please contact info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/54843](https://trtc.io/document/54843)*
