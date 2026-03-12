# Integration

## Feature Overview

`TUILiveKit` is a comprehensive voice chat room component. After integration, you can quickly implement the following key modules:

| Host Preparation Page | Host Live Page | Live Room List | Audience Viewing Page |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8245d3c8c05c11f085a55254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/49f09db0c04411f085a55254007c27c5.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6d0d1c3fc04411f0b9945254005ef0f7.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/465260cac04411f08863525400e889b2.png) |

## Prerequisites

### Activate Service

Before using `TUILiveKit`, refer to [Activate Service](https://www.tencentcloud.com/document/product/647/60033) to obtain a trial or activate the paid version of `TUILiveKit`.

### Environment Preparation

- `Android Studio Arctic Fox (2020.3.1)` or later
- `Gradle 7.0` or later
- Mobile devices running `Android 5.0` or later

## Integrate TUIKit

### **Step 1.**Download the TUILiveKit Component

Clone or download the code from [GitHub](https://github.com/Tencent-RTC/TUIKit_Android). Then, copy the `live` and `atomic_x` subdirectory into the same directory as your current Android project's `app` folder.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/77b16b61c39811f08c0e52540044a08e.png)

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

In your project's root directory, add the following line to the `settings.gradle.kts `or `settings.gradle` file to import the **tuilivekit** component (as a module).

settings.gradle.kts

settings.gradle

```
include ':tuilivekit'project(':tuilivekit').projectDir = new File(settingsDir, "live/tuilivekit")include(":atomic")project(':atomic').projectDir = new File(settingsDir, "atomic_x")
```

```
include(":tuilivekit")project(":tuilivekit").projectDir = File(settingsDir, "live/tuilivekit")include(":atomic")project(":atomic").projectDir = File(settingsDir, "atomic_x")
```

#### **3. Add Component Dependency**

In the `build.gradle.kts` (or `build.gradle`) file under your app directory, add the following to declare the dependency on the `TUILiveKit` component:

build.gradle.kts

build.gradle

```
dependencies {    // Add tuilivekit dependency    api(project(":tuilivekit"))}
```

```
dependencies {    // Add tuilivekit dependency    api project(':tuilivekit')}
```

> **Noteï¼**`TUILiveKit` already includes dependencies on public libraries such as `TRTC SDK` and `IM SDK`. You do not need to configure these separately.

#### **4. Configure ProGuard Rules**

Because the `SDK` uses Java reflection internally, add the following rules to your `proguard-rules.pro` file to prevent obfuscation of required classes and ensure proper functionality:

```
-keep class com.tencent.** { *; }-keep class com.tencent.beacon.** { *; }-keep class com.tencent.cloud.iai.lib.** { *; }-keep class com.tencent.qimei.** { *; }-keep class com.trtc.uikit.livekit.component.gift.store.model.** { *; }-keep class com.trtc.uikit.livekit.livestreamcore.** { *; }-keep class com.tcmediax.** { *; }# ProGuard rules for Google Gson serialization/deserialization library-keep class com.google.gson.** { *; }# ProGuard rules for SVG gift animation playback-keep class com.opensource.svgaplayer.proto.** { *; }-keep class com.squareup.wire.** { *; }
```

#### **5. Modify AndroidManifest.xml**

If you want to prevent attribute conflicts during the `AndroidManifest` merge at compile time to override the component's internal settings:

- add `tools:replace="android:allowBackup"`  to the `<application>` node in `app/src/main/AndroidManifest.xml`.
- add `android:allowBackup="false"`to the `<application>` node in `app/src/main/AndroidManifest.xml`.

```
 <application    ...    <!-- Add the following configuration to override settings from dependent SDKs -->    android:allowBackup="false"    tools:replace="android:allowBackup">
```

#### **6. Complete Project Sync**

- After completing the steps above, Android Studio will usually prompt you to `Sync Now`. Click this button to synchronize your project.
- If not prompted, manually click the sync button in the toolbar.
- Once syncing is complete, the IDE will finish project build configuration and indexing, and you can start using the `TUILiveKit` component in your project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4a1c4181c06011f0a6c652540044a08e.png)

## Complete Login

After integrating the code, you must complete the login process. This is a required stepfor using `TUILiveKit`âall features are available only after a successful login. Ensure all parameters are configured correctly:

> **Noteï¼**In the sample code, the login API is called directly. In production, call the `TUILiveKit` login service only after your own user authentication and login logic. This prevents business logic confusion or data inconsistency from premature login calls and ensures smooth integration with your existing user management and permission systems.

Kotlin

Java

```
// 1. Import dependencyimport com.tencent.qcloud.tuicore.TUILogin// 2. Call the login API. Call TUILogin.login after your own login logic is completeTUILogin.login(applicationContext,    1400000001,      // Replace with your SDKAppID from the service console    "denny",         // Replace with your UserID    "xxxxxxxxxxx",   // Generate a UserSig in the console and use it here    object : TUICallback() {        override fun onSuccess() {            Log.i(TAG, "login success")        }        override fun onError(errorCode: Int, errorMessage: String) {            Log.e(TAG, "login failed, errorCode: $errorCode msg:$errorMessage")        }    })
```

```
// 1. Import dependencyimport com.tencent.qcloud.tuicore.TUILogin// 2. Call the login API. Call TUILogin.login after your own login logic is completeTUILogin.login(context,    1400000001,     // Replace with your SDKAppID from the service console    "denny",        // Replace with your UserID    "xxxxxxxxxxx",  // Generate a UserSig in the console and use it here    new TUICallback() {    @Override    public void onSuccess() {        Log.i(TAG, "login success");    }    @Override    public void onError(int errorCode, String errorMessage) {        Log.e(TAG, "login failed, errorCode: " + errorCode + " msg:" + errorMessage);    }});
```

**Login API Parameter Description**

| Parameter | Type | Description |
| --- | --- | --- |
| SDKAppID | Int | Get this from [TRTC console > Application management](https://console.trtc.io/app). |
| UserID | String | The unique ID for the current user. Must contain only English letters, numbers, hyphens, and underscores. |
| userSig | String | A ticket for Tencent Cloud authentication. Please note:**Development Environment**: You can use the local `GenerateTestUserSig.genTestSig` function to generate a UserSig or generate a temporary UserSig via the [UserSig Generation Tool](https://console.trtc.io/usersig).**Production Environment**: To prevent key leakage, you must use a server-side method to generate UserSig. For details, see [Generating UserSig on the Server](https://www.tencentcloud.com/document/product/647/35166).For more information, see [How to Calculate and Use UserSig](https://www.tencentcloud.com/document/product/647/35166). |

### Handling Login Exception Status [Optional]

`TUILogin` provides a login status callback mechanism to help you handle possible login exceptions, mainly including "**kicked offline**" and "**signature expired**" callbacks:

- **Kicked Offline:** If a user is kicked offline while online, the `SDK` will notify you via the `onKickedOffline` callback. At this point, you can display a UI prompt to the user and call `TUILogin.login` to login again.
- **Signature Expired:** If a user receives the `onUserSigExpired` callback while online, it means the `userSig` previously issued for that user has expired. If the user's login session on your backend is still valid, you can have your app request a new `userSig` from your backend and call `TUILogin.login` to renew the login session.

kotlin

java

```
class YourLoginService : TUILoginListener() {    // Listen to login status callback    fun addObserver() {        TUILogin.addLoginListener(this)    }    // Cancel listening for login status callback    fun removeObserver() {        TUILogin.removeLoginListener(this)    }    // User kicked offline callback    override fun onKickedOffline() {        // Your business code: UI prompts the user, then log in again    }    // User signature expired callback    override fun onUserSigExpired() {        // Your business code: If the current user is still logged in on your backend, you can let your app request a new userSig from the backend and call TUILogin.login to renew the login status.    }}
```

```
class YourLoginService extends TUILoginListener {    // Listen to login status callback    public void addObserver() {        TUILogin.addLoginListener(this);    }    // Cancel listening for login status callback    public void removeObserver() {        TUILogin.removeLoginListener(this);    }    // User kicked offline callback    @Override    public void onKickedOffline() {        // Your business code: UI prompts the user, then log in again    }    // User signature expired callback    @Override    public void onUserSigExpired() {        // Your business code: If the current user is still logged in on your backend, you can let your app request a new userSig from the backend and call TUILogin.login to renew the login status.    }}
```

## Next Steps

Congratulations! You have successfully integrated the **Voice Chat Room** component and completed login. Next, implement features such as Host Live, Audience Viewing, and Live Room List. See the table below for more details:

| **Feature** | **Description** | **Integration Guide** |
| --- | --- | --- |
| **Host Live Streaming** | The complete process for hosts to create a voice chat room, including preparation and all live interactions. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74323) |
| **Audience Viewing** | Audience members can listen, request to join the mic, view bullet comments, and more after entering a voice chat room. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74327) |
| **Live Room List** | Displays the list of available voice chat rooms and their details. | [Integration Guide](https://www.tencentcloud.com/document/product/647/74325) |

## FAQs

### Do I need to call login every time I enter a room?

No. Typically, you only need to call `TUILogin.login` once. We recommend aligning `TUILogin.login` and `TUILogin.logout `with your own authentication logic.

### Encounter a compilation error related to allowBackup after integrating the code

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/86c9fdc3c06111f0a808525400bf7822.png)

- **Cause**: The allowBackup attribute is defined in multiple modules' `AndroidManifest.xml` files, causing a conflict.
- **Solution**: Remove the allowBackup attribute from your project's `AndroidManifest.xml` or set it to false to disable backup and restore. Also, add `tools:replace="android:allowBackup"` to the `<application>` node to override settings from other modules. See the example below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/86d0a221c06111f0a6c652540044a08e.png)

### Do I need to declare microphone permissions after integrating the code?

No. `TUILiveKit` already declares the required microphone permissions. You do not need to add them manually.

## Contact Us

If you have any questions or suggestions during running the demo or usage, join our [Telegram technical group](https://t.me/+EPk6TMZEZMM5OGY1?s_url=https%3A%2F%2Ftrtc.io) or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/60335](https://trtc.io/document/60335)*
