# Integration and Login

This document will introduce how to integrate and log in to the core component of the voice chat room, `SeatGridView`.

## Integration

iOS

Android

### Environment Preparation

- Xcode 15 or later.
- iOS 13.0 or later.
- CocoaPods environment setup, [Click to view](https://guides.cocoapods.org/using/getting-started.html).
- If you encounter any problems with access and use, please refer to [FAQs](https://www.tencentcloud.com/document/product/647/60322#).

### Activate Service

Please refer to [Activating Services (TUILiveKit)](https://www.tencentcloud.com/document/product/647/60336#) to receive the trial version or activate the paid version.

### Importing the SeatGridView

Use CocoaPods to import the component. If you encounter any issues, please refer to [Environment Preparation](https://www.tencentcloud.com/document/product/647/67506#7d035489-3ed3-46ff-845e-eb7279e0d486) first. Detailed steps for importing the component are as follows:

1. Add the `pod 'SeatGridView'` dependency to your `Podfile` file.

Swift

```
target 'xxxx' do  ...  ...  pod 'SeatGridView'end
```

If you don't have a `Podfile` file, first `cd` in Terminal into the `xxxx.xcodeproj` directory, then create one using the following command:

```
pod init
```

2. In Terminal, first `cd` into the `Podfile` directory and then run the following command to install components.

```
pod install
```

If you can't install the latest version of SeatGridView, delete **Podfile.lock** and **Pods** first. Then run the following command to update the local CocoaPods repository list.

```
pod repo update
```

Then, run the following command to update the Pod version of the component library.

```
pod update
```

3. You can compile and run it first. If you encounter any issues, please refer to [FAQs](https://www.tencentcloud.com/document/product/647/60322#). If you have any questions during the integration and usage, feel free to [give us feedback](https://github.com/Tencent-RTC/TUILiveKit/issues).

### Environment Preparation

- Android 5.0 (SDK API Level 21) or later.
- Gradle v7.0 or later.
- Mobile device on Android 5.0 or later.
- For issues during environment configuration or compilation, please refer to [FAQ](https://www.tencentcloud.com/document/product/647/60322#).

### Activate Service

Please refer to [Activating Services (TUILiveKit)](https://www.tencentcloud.com/document/product/647/60336#) to receive the trial version or activate the paid version.

### Importing the SeatGridView

1. Find the `build.gradle.kts (or build.gradle)` file under the app directory and add the following code to include the dependency for SeatGridView component:

build.gradle.kts

build.gradle

```
api("io.trtc.uikit:voice-room-core:latest.release")
```

```
api 'io.trtc.uikit:voice-room-core:latest.release'
```

2. As the SDK uses Java's reflection feature internally, you need to add certain classes in the SDK to the obfuscation allowlist by adding the following code to the `proguard-rules.pro` file:

```
-keep class com.tencent.** { *; }-keep class com.trtc.uikit.livekit.voiceroomcore.** { *; }
```

3. Find the `AndroidManifest.xml` file under the app directory and add tools:replace="android:allowBackup" and android:allowBackup="false" in the application node to override the settings within the component with your own settings.

```
  // app/src/main/AndroidManifest.xml    <application    ...      // Add the following configuration to override the configuration in the dependency SDK    android:allowBackup="false"    tools:replace="android:allowBackup">
```

## Log-in

iOS

Android

Add the following code to your project, which completes the login of TUI Components by calling the relevant interfaces in TUICore. This step is critical; you can only use the features provided by SeatGridView after successful login.

swift

```
////  AppDelegate.swift//import TUICorefunc application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {        TUILogin.login(1400000001,               // Please replace with the SDKAppID obtained in Step 1            userID: "denny",                 // Please replace with your UserID            userSig: "xxxxxxxxxxx") {        // You can calculate a UserSig in the console and fill it here      print("login success")    } fail: { (code, message) in      print("login failed, code: \\(code), error: \\(message ?? "nil")")    }        return true}
```

**Parameter Description**

Here we detail the key parameters required in the login function:

| Parameters | Type | Description |
| --- | --- | --- |
| SDKAppID | int | You have already obtained it in the last step of Step 1, so it will not be elaborated here. |
| UserID | String | The ID of the current user, in string format, only allows letters (a-z and A-Z), digits (0-9), hyphens, and underscores. |
| userSig | String | Use the SecretKey obtained in step 3 of [Activate Service](https://www.tencentcloud.com/document/product/647/60336#) to encrypt information such as SDKAppID and UserID to generate a UserSig. It's a credential used for authentication purposes, allowing Tencent Cloud to identify if the current user is authorized to use the TRTC service. You can generate a temporary UserSig through the [Auxiliary Tools](https://trtc.io/login?s_url=https://console.trtc.io/usersig) in the console. For more information, please refer to [How to Calculate and Use UserSig](https://www.tencentcloud.com/document/product/647/35166#). |

> **Note:****Development Environment**: If you are in the local development and debugging stage, you can use the local `GenerateTestUserSig.genTestSig` function to generate userSig. In this method, the SDKSecretKey is vulnerable to decompilation and reverse engineering, and once your key is leaked, attackers can steal your Tencent Cloud traffic.**Production Environment**: If your project is going to be launched, please adopt the method of [Server-side Generation of UserSig](https://www.tencentcloud.com/document/product/647/35166#).

Add the following code to your project, which completes the login of TUI Components by calling the relevant interfaces in TUICore. This step is critical; you can only use the features provided by SeatGridView after successful login.

Kotlin

Java

```
// Log inTUILogin.login(applicationContext,    1400000001,  // Please replace with the SDKAppID obtained in Step 1    "denny",  // Please replace with your UserID    "xxxxxxxxxxx",  // You can calculate a UserSig in the Console and fill it in here    object : TUICallback() {        override fun onSuccess() {            Log.i(TAG, "login success")        }        override fun onError(errorCode: Int, errorMessage: String) {            Log.e(TAG, "login failed, errorCode: $errorCode msg:$errorMessage")        }    })
```

```
// Log inTUILogin.login(context,     1400000001,     // Please replace with the SDKAppID obtained in Step 1    "denny",        // Please replace with your UserID    "xxxxxxxxxxx",  // You can calculate a UserSig in the Console and fill it in here    new TUICallback() {    @Override    public void onSuccess() {        Log.i(TAG, "login success");    }    @Override    public void onError(int errorCode, String errorMessage) {        Log.e(TAG, "login failed, errorCode: " + errorCode + " msg:" + errorMessage);    }});
```

**Parameter Description**

Here we detail the key parameters required in the login function:

| Parameters | Type | Description |
| --- | --- | --- |
| SDKAppID | int | You have already obtained it in the last step of Step 1, so it will not be elaborated here. |
| UserID | String | The ID of the current user, in string format, only allows letters (a-z and A-Z), digits (0-9), hyphens, and underscores. |
| userSig | String | Use the SecretKey obtained in step 3 of [Activate Service](https://www.tencentcloud.com/document/product/647/60336#) to encrypt information such as SDKAppID and UserID to generate a UserSig. It's a credential used for authentication purposes, allowing Tencent Cloud to identify if the current user is authorized to use the TRTC service. You can generate a temporary UserSig through the [Auxiliary Tools](https://trtc.io/login?s_url=https://console.trtc.io/usersig) in the console. For more information, please refer to [How to Calculate and Use UserSig](https://www.tencentcloud.com/document/product/647/35166#). |

> **Note:****Development Environment**: If you are in the local development and debugging stage, you can use the local `GenerateTestUserSig.genTestSig` function to generate userSig. In this method, the SDKSecretKey is vulnerable to decompilation and reverse engineering, and once your key is leaked, attackers can steal your Tencent Cloud traffic.**Production Environment**: If your project is going to be launched, please adopt the method of [Server-side Generation of UserSig](https://www.tencentcloud.com/document/product/647/35166#).


---
*Source: [https://trtc.io/document/67506](https://trtc.io/document/67506)*
