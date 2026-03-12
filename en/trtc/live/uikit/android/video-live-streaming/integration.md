# Integration

## Feature Overview

**TUILiveKit** is a comprehensive live-streaming component. Once integrated, it allows you to quickly implement the following key functional modules for your Android application:

| **Host Prepare Page** | **Host Streaming Page** | **Live Stream List** | **Audience Viewing Page** |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9c4f00c5985c11f09b0c525400bf7822.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98bd193d985c11f09b0c525400bf7822.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a9241a4398f911f0961e52540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/95fb6e6d985c11f0ad595254007c27c5.png) |

## **Preparations**

### Activate Service

Before using **TUILiveKit**, please refer to [Activate Service](https://www.tencentcloud.com/document/product/647/60033) to get the TUILiveKit trial version or activate the paid version.

### Environment Requirements

- **Android** **Studio Arctic Fox (2020.3.1)**or a later version.
- **Gradle 7.0** or a later version.
- **Android** **5.0**or a later version.

## Code Integration

### **Step 1.**Download the TUILiveKit Component

Clone or download the code from [GitHub](https://github.com/Tencent-RTC/TUIKit_Android). Then, copy the `live` and `atomic_x` subdirectory into the same directory as your current Android project's `app` folder.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/82894163c39211f0aa02525400e889b2.png)

### Step 2. Project Configuration

#### 1. Configure the JitPack Repository

In your project's **root directory,** open the `settings.gradle.kts` or `settings.gradle` file and add the JitPack repository address. The third-party library for playing gift SVG animations is hosted on JitPack, so you must include this repository to resolve dependencies.

settings.gradle.kts

settings.gradle

```
dependencyResolutionManagement {    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)    repositories {        google()        mavenCentral()        // Add JitPack repository url        maven { url = uri("https://jitpack.io") }    }}
```

```
dependencyResolutionManagement {    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)    repositories {        google()        mavenCentral()        // Add JitPack repository url        maven { url 'https://jitpack.io' }    }}
```

#### 2. Import the TUILiveKit Component

In your project's root directory, add the following line to the `settings.gradle.kts `or `settings.gradle` file to import the **TUILiveKit** component (as a module).

settings.gradle.kts

settings.gradle

```
include ':tuilivekit'project(':tuilivekit').projectDir = new File(settingsDir, "live/tuilivekit")include(":atomic")project(':atomic').projectDir = new File(settingsDir, "atomic_x")
```

```
include ':tuilivekit'project(':tuilivekit').projectDir = new File(settingsDir, "live/tuilivekit")include(":atomic")project(':atomic').projectDir = new File(settingsDir, "atomic_x")
```

#### 3. Adding Component Dependency

Navigate to the app directory and find the `build.gradle.kts` or `build.gradle` file. Add the following dependency to declare that your app module relies on the newly added `TUILiveKit` component module.

build.gradle.kts

build.gradle

```
dependencies {    // Add tuilivekit dependency    api(project(":tuilivekit"))}
```

```
dependencies {    // Add tuilivekit dependency    api project(':tuilivekit')}
```

> **Note:**TUILiveKit has default dependencies on public libraries like the TRTC SDK and IM SDK, so you **do not**need to configure them separately.

#### 4. Configure Proguard Rules

Since the SDK uses Java reflection internally, you must add the following rules to the **proguard-rules.pro** file. This prevents the relevant classes from being obfuscated, ensuring proper function.

```
SVG
```

#### 5. Modify AndroidManifest.xml

To prevent conflicts during the **AndroidManifest** merge process, you must add `tools:replace="android:allowBackup"` and `android:allowBackup="false"` to the **<application>** node in your `app/src/main/AndroidManifest.xml` file. This overrides the settings within the component and disables the backup feature.

```
 <application    ...      // Add the following configuration to override the settings in the dependent SDK    android:allowBackup="false"    tools:replace="android:allowBackup">
```

#### 6. Complete Project Sync

After completing the steps above, Android Studio will typically prompt you with a **Sync Now** button. Click this button to complete the project synchronization. If the IDE doesn't prompt you automatically, manually click the sync button in the toolbar. Once synchronized, the IDE will finish project configuration and indexing, allowing you to use the **TUILiveKit** component in your project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc7b5cd0985a11f093df52540099c741.png)

## Complete Login

After code integration, the next step is to complete the login. All **TUILiveKit** features require a successful login to function properly, so ensure your parameters are configured correctly.

> **Note:**In the example code, the login API is called directly. However, in a real-world application, it is highly recommended that you call the **TUILiveKit** login service only after your own user authentication and other internal login processes are complete. This prevents potential business logic confusion or data inconsistency caused by calling the login service too early, and it better aligns with your existing user management system.

Kotlin

Java

```
// 1. Import dependencyimport com.tencent.qcloud.tuicore.TUILogin// 2. Call the login API. It is recommended to call TUILogin after your own login business is completed.TUILogin.login(applicationContext,    1400000001,      // Please replace with the SDKAppID from the service activation console    "denny",         // Please replace with your UserID    "xxxxxxxxxxx",   // You can generate a UserSig in the console and fill it in here    object : TUICallback() {        override fun onSuccess() {            Log.i(TAG, "login success")        }        override fun onError(errorCode: Int, errorMessage: String) {            Log.e(TAG, "login failed, errorCode: $errorCode msg:$errorMessage")        }    })
```

```
// 1. Import dependencyimport com.tencent.qcloud.tuicore.TUILogin// 2. Call the login API. It is recommended to call TUILogin after completing your own login service.TUILogin.login(context,     1400000001,      // Please replace with the SDKAppID from the service activation console    "denny",         // Please replace with your UserID    "xxxxxxxxxxx",   // You can generate a UserSig in the console and fill it in here    new TUICallback() {    @Override    public void onSuccess() {        Log.i(TAG, "login success");    }    @Override    public void onError(int errorCode, String errorMessage) {        Log.e(TAG, "login failed, errorCode: " + errorCode + " msg:" + errorMessage);    }});
```

**Login API Parameter Description**

| Parameter | Type | Description |
| --- | --- | --- |
| SDKAppID | Int | Get this from [TRTC console > Application management](https://console.trtc.io/app). |
| UserID | String | The unique ID for the current user. Must contain only English letters, numbers, hyphens, and underscores. |
| userSig | String | A ticket for Tencent Cloud authentication. Please note:**Development Environment**: You can use the local `GenerateTestUserSig.genTestSig` function to generate a UserSig or generate a temporary UserSig via the [UserSig Generation Tool](https://console.trtc.io/usersig).**Production Environment**: To prevent key leakage, you must use a server-side method to generate UserSig. For details, see [Generating UserSig on the Server](https://www.tencentcloud.com/document/product/647/69883).For more information, see [How to Calculate and Use UserSig](https://www.tencentcloud.com/document/product/647/35166). |

### Handling Login Exception Status [Optional]

**TUILogin** provides a login status callback mechanism to help you handle possible login exceptions, mainly including "**kicked offline**" and "**signature expired**" callbacks:

- **Kicked Offline:** If a user is kicked offline while online, the **SDK** will notify you via the `onKickedOffline` callback. At this point, you can display a UI prompt to the user and call `TUILogin.login` to login again.
- **Signature Expired:** If a user receives the `onUserSigExpired` callback while online, it means the **userSig** previously issued for that user has expired. If the user's login session on your backend is still valid, you can have your app request a new **userSig** from your backend and call `TUILogin.login` to renew the login session.

kotlin

java

```
class YourLoginService : TUILoginListener() {    // Listen to login status callback    fun addObserver() {        TUILogin.addLoginListener(this)    }    // Cancel listening for login status callback    fun removeObserver() {        TUILogin.removeLoginListener(this)    }    // User kicked offline callback    override fun onKickedOffline() {        // Your business code: UI prompts the user, then log in again    }    // User signature expired callback    override fun onUserSigExpired() {        // Your business code: If the current user is still logged in on your backend, you can let your app request a new userSig from the backend and call TUILogin.login to renew the login status.    }}
```

```
class YourLoginService extends TUILoginListener {    // Listen to login status callback    public void addObserver() {        TUILogin.addLoginListener(this);    }    // Cancel listening for login status callback    public void removeObserver() {        TUILogin.removeLoginListener(this);    }    // User kicked offline callback    @Override    public void onKickedOffline() {        // Your business code: UI prompts the user, then log in again    }    // User signature expired callback    @Override    public void onUserSigExpired() {        // Your business code: If the current user is still logged in on your backend, you can let your app request a new userSig from the backend and call TUILogin.login to renew the login status.    }}
```

## Next Steps

Congratulations! You have successfully integrated the **TUILiveKit** component and completed the login. You can now implement features such as host streaming, viewer watching, and the live stream list. Please refer to the table below for integration guides:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Streaming** | The complete workflow for a host to start a stream, including pre-stream setup and various in-stream interactions. | [Host Streaming](https://www.tencentcloud.com/document/product/647/72219) |
| **Audience Viewing** | Audience can watch live streaming after entering the anchor's live streaming room, with features like audience mic connection, live room information, online audience, and bullet screen display. | [Audience Viewing](https://www.tencentcloud.com/document/product/647/72221) |
| **Live Stream List** | Display the live stream list interface and features, including the live stream list and room information display. | [Live Stream List](https://www.tencentcloud.com/document/product/647/72220) |

## FAQs

### Do I need to call the login API every time I enter a room?

No. You typically only need to call `TUILogin.login` once. We recommend associating `TUILogin.login` and `TUILogin.logout` with your app's own user login and logout business logic.

### How do I handle the `allowBackup` compilation error shown in the figure below after code integration?

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc551d7b985a11f0af98525400454e06.png)

- **Reason**: The `allowBackup` attribute is configured in the `AndroidManifest.xml` of multiple modules, which causes a conflict during the manifest merge process.
- **Solution**: In your project's `AndroidManifest.xml` file, you can either delete the `allowBackup` attribute or change it to false to disable backup and restore functionality. Crucially, add `tools:replace="android:allowBackup"` to the **<application>** node to override the settings of other modules with your own configuration. See the example fix:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc619de5985a11f09b0c525400bf7822.png)

### After code integration, do I still need to explicitly declare camera and microphone permissions?

No, **TUILiveKit** already has built-in declarations for permissions like the camera and microphone in its manifest file. You do not need to worry about declaring these permissions separately during the integration process.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bc84e777985a11f0ad595254007c27c5.png)


---
*Source: [https://trtc.io/document/72217](https://trtc.io/document/72217)*
