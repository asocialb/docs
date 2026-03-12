# TUIKit

TUIKit is a UI component library built on the Chat SDK. It enables rapid implementation of chat, conversation, search, relationship chain, and group management features through ready-to-use UI components. Message sending and receiving are handled by the TUIChat component. This guide explains how to quickly integrate TUIKit and implement its core features.

## Key Concepts

- **Classic UI**: Starting from version 5.7.1435, TUIKit supports modular integration and provides the Classic UI (WeChat-style interface).
- **Minimalist UI**: Starting from version 6.9.3557, TUIKit introduces a new Minimalist UI (WhatsApp-style interface).

You can select either the Classic or Minimalist UI components as needed. If you are unfamiliar with the appearance of each UI library, see [TUIKit UI Library Introduction](https://www.tencentcloud.com/zh/document/product/1047/50062).

> **Noteï¼**This demo uses TRTC's emoji pack with restricted licensing.**Commercial Usage Options****Option A: Keep Our Emoji (Recommended)**Upgrade to [Chat Pro Plus or Enterprise Plan](https://console.trtc.io/subscription/buy/chat?packType=pro) and use our emoji pack at no additional cost.**Option B: Use Your Own**Replace default emoji with your own custom designs, or use emoji packs with proper commercial licensing.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b2d60841b88e11f0a5e052540099c741.png)

## Prerequisites

- Android Studio 2022.3.1 or later
- Android 5.0 or higher (physical device or emulator)
- A valid Tencent Cloud account and Chat application. See [Service Activation](https://trtc.io/document/45914?product=chat&menulabel=uikit&platform=android#directions) to obtain the following from the Console:
  - `SDKAppID`: Unique identifier for your Chat application
  - `SDKSecretKey`: Application secret key

> **Version Compatibility Notice**:To ensure a stable build environment, strictly follow the official compatibility requirements:For compatibility between Gradle, Android Gradle Plugin, JDK, and Android Studio, see the Android official documentation: [Release Notes](https://developer.android.com/build/releases/gradle-plugin#updating-gradle)For the mapping between Kotlin, Android Gradle Plugin, and Gradle versions, see the Kotlin official documentation: [Kotlin-Gradle Plugin Compatibility](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin)Select a version combination that fully matches your project requirements according to these guidelines.

## Integration

1. Download the [Android TUIKit source code](https://github.com/TencentCloud/chat-uikit-android) from GitHub and copy the TUIKit directory into your project directory:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bb36fb54b62811f0a6c652540044a08e.png)

2. Add the required TUI components to your `settings.gradle` based on your business needs. TUI components are independent; adding or removing them does not affect project compilation.

> **Note:**You can place the TUIKit directory anywhere, as long as the relative path is correctly set in `settings.gradle`

```
// Include the app moduleinclude ':app'// Core communication module (required)include ':tuicore'project(':tuicore').projectDir = new File(settingsDir, '../TUIKit/TUICore/tuicore')// Common IM module (required)include ':timcommon'project(':timcommon').projectDir = new File(settingsDir, '../TUIKit/TIMCommon/timcommon')// Chat module (core feature)include ':tuichat'project(':tuichat').projectDir = new File(settingsDir, '../TUIKit/TUIChat/tuichat')// Contacts module (core feature)include ':tuicontact'project(':tuicontact').projectDir = new File(settingsDir, '../TUIKit/TUIContact/tuicontact')// Conversation list module (core feature)include ':tuiconversation'project(':tuiconversation').projectDir = new File(settingsDir, '../TUIKit/TUIConversation/tuiconversation')// Search module (requires Pro, Pro Plus, or Enterprise edition)include ':tuisearch'project(':tuisearch').projectDir = new File(settingsDir, '../TUIKit/TUISearch/tuisearch')// Community module (requires Pro, Pro Plus, or Enterprise edition)include ':tuicommunity'project(':tuicommunity').projectDir = new File(settingsDir, '../TUIKit/TUICommunity/tuicommunity')// Audio/video call moduleinclude ':tuicallkit-kt'project(':tuicallkit-kt').projectDir = new File(settingsDir, '../TUIKit/TUICallKit/tuicallkit-kt')// Video conference moduleinclude ':tuiroomkit'project(':tuiroomkit').projectDir = new File(settingsDir, '../TUIKit/TUIRoomKit/tuiroomkit')// Speech-to-text plugin (supported from version 7.5)include ':tuivoicetotextplugin'project(':tuivoicetotextplugin').projectDir = new File(settingsDir, '../TUIKit/TUIVoiceToTextPlugin/tuivoicetotextplugin')// Message translation plugin (supported from version 7.2; value-added feature activation required)include ':tuitranslationplugin'project(':tuitranslationplugin').projectDir = new File(settingsDir, '../TUIKit/TUITranslationPlugin/tuitranslationplugin')// Emoji reaction plugin (supported from version 7.8; requires Pro, Pro Plus, or Enterprise edition)include ':tuiemojiplugin'project(':tuiemojiplugin').projectDir = new File(settingsDir, '../TUIKit/TUIEmojiPlugin/tuiemojiplugin')
```

3. Add the following dependencies to your app module's `build.gradle`:

```
dependencies { api project(':tuiconversation') api project(':tuicontact') api project(':tuichat') api project(':tuisearch') api project(':tuicommunity') api project(':tuicallkit-kt') api project(':tuiroomkit') // Speech-to-text plugin (from version 7.5) api project(':tuivoicetotextplugin') // Translation plugin (from version 7.2; value-added feature activation required) api project(':tuitranslationplugin') // Emoji reaction plugin (from version 7.8; requires Pro, Pro Plus, or Enterprise edition) api project(':tuiemojiplugin') // Group notes plugin (from version 7.1) api 'com.tencent.imsdk:tuigroupnote-plugin:8.4.6667' // Poll plugin (from version 7.1) api 'com.tencent.imsdk:tuipoll-plugin:8.4.6667' // Conversation grouping plugin (from version 7.3) api 'com.tencent.imsdk:tuiconversationgroup-plugin:8.4.6667' // Conversation tagging plugin (from version 7.3) api 'com.tencent.imsdk:tuiconversationmark-plugin:8.4.6667' // Message push plugin (from version 7.6) api 'com.tencent.timpush:timpush:8.4.6667' // Manufacturer-specific push packages as needed api 'com.tencent.timpush:fcm:8.4.6667' api 'com.tencent.timpush:xiaomi:8.4.6667' api 'com.tencent.timpush:meizu:8.4.6667' api 'com.tencent.timpush:oppo:8.4.6667' api 'com.tencent.timpush:vivo:8.4.6667' api 'com.tencent.timpush:huawei:8.4.6667' api 'com.tencent.timpush:honor:8.4.6667'}
```

4. In your app's `AndroidManifest.xml`, add `tools:replace="android:allowBackup"` to the `<application>` node to override the component's internal setting and use your own value.

```
// app/src/main/AndroidManifest.xml<application  android:name=".BaseApplication"  android:allowBackup="false"  android:icon="@drawable/app_ic_launcher"  android:label="@string/app_name"  android:largeHeap="true"  android:theme="@style/AppTheme"  tools:replace="android:allowBackup">
```

5. Add Maven repositories

For Gradle 7.0 and above (Recommended)

For Gradle below 7.0

Groovy DSL

Kotlin DSL

```
// settings.gradlepluginManagement {    repositories {        google()        mavenCentral()        gradlePluginPortal()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public" }        maven { url "https://developer.huawei.com/repo" }        maven { url "https://developer.hihonor.com/repo" }    }}dependencyResolutionManagement {    repositories {        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }        maven { url "https://mirrors.tencent.com/repository/maven/liteavsdk/" }        maven { url "https://developer.huawei.com/repo/" }        maven { url "https://developer.hihonor.com/repo" }    }}
```

```
// settings.gradle.ktspluginManagement {    repositories {        google()        mavenCentral()        gradlePluginPortal()        maven { url = uri("https://mirrors.tencent.com/nexus/repository/maven-public") }        maven { url = uri("https://developer.huawei.com/repo") }        maven { url = uri("https://developer.hihonor.com/repo") }    }}dependencyResolutionManagement {    repositories {        mavenCentral()        maven { url = uri("https://mirrors.tencent.com/nexus/repository/maven-public") }        maven { url = uri("https://mirrors.tencent.com/repository/maven/liteavsdk") }        maven { url = uri("https://developer.huawei.com/repo") }        maven { url = uri("https://developer.hihonor.com/repo") }    }}
```

Groovy DSL

Kotlin DSL

```
// project root build.gradlebuildscript {    repositories {        google()        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public" }        maven { url "https://developer.huawei.com/repo" }        maven { url "https://developer.hihonor.com/repo" }    }}allprojects {    repositories {        google()        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }        maven { url "https://mirrors.tencent.com/repository/maven/liteavsdk/" }        maven { url "https://developer.huawei.com/repo/" }        maven { url "https://developer.hihonor.com/repo" }    }}
```

```
// project root build.gradle.ktsbuildscript {    repositories {            google()        mavenCentral()        maven { url = uri("https://mirrors.tencent.com/nexus/repository/maven-public") }        maven { url = uri("https://developer.huawei.com/repo") }        maven { url = uri("https://developer.hihonor.com/repo") }    }}allprojects {    repositories {        google()        mavenCentral()        maven { url = uri("https://mirrors.tencent.com/nexus/repository/maven-public") }        maven { url = uri("https://mirrors.tencent.com/repository/maven/liteavsdk") }        maven { url = uri("https://developer.huawei.com/repo") }        maven { url = uri("https://developer.hihonor.com/repo") }    }}
```

6. Configure Kotlin support (optional)
  - If your project already uses Kotlin, skip this step.
  - If your project does not use Kotlin, add the appropriate version of the Kotlin Gradle plugin:

> **Note:**If you need to add the Kotlin Gradle plugin, set `$kotlin_version` to a specific version number and ensure it is compatible with your Android Gradle Plugin version (for example, if `$kotlin_version` is 1.9.0, use Android Gradle Plugin 8.6.0). See [Kotlin-Gradle Plugin Compatibility](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin)

```
// project root build.gradlebuildscript {   dependencies {      classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"   }}
```

7. Configure ProGuard rules

Add the following rules to your `app/proguard-rules.pro` file:

```
-dontshrink-dontoptimize-keep class com.tencent.qcloud.** { *; }-keep class com.tencent.imsdk.** { *; }-keep class * implements com.tencent.qcloud.tuicore.interfaces.TUIInitializer {}
```

8. In Android Studio, select **File > Sync Project with Gradle Files** to sync and integrate the components.
  - When using local integration, always update your local TUIKit directory with the latest code from GitHub during upgrades.
  - If you have made private modifications, manually resolve any merge conflicts with the remote repository.

> **Note:**When integrating TUIKit from source, both UI versions are included by default.Classic UI and Minimalist UI components cannot be mixed. When integrating multiple components, use either all Classic UI components or all Minimalist UI components. For example, the Classic "TUIChat" component must be used together with the Classic "TUIConversation" and "TUIContact" components. Similarly, the Minimalist "TUIChat" component must be used together with the Minimalist "TUIConversation" and "TUIContact" components.

Now you have successfully integrated TUIKit into your project. To continue building basic interfaces such as chat and conversation, see [Building a Chat Interface](https://www.tencentcloud.com/document/product/1047/61214) and [Building a Conversation List](https://www.tencentcloud.com/document/product/1047/61216).

## FAQs

#### Audio/Video FAQs

##### What is the default timeout for call invitations?

The default timeout for call invitations is 30 seconds.

##### If an invitee goes offline and comes back online within the invitation timeout period, will they receive the invitation immediately?

- For one-on-one call invitations, if the invitee goes offline and then comes back online, they will receive the call invitation. TUIKit will automatically display the call invitation interface.
- For group call invitations, if the invitee goes offline and then comes back online, TUIKit will automatically retrieve invitations from the last 30 seconds and display the group call interface.

#### Android Studio Integration FAQs

##### How do I resolve "Manifest merger failed: Attribute application@allowBackup value=(true) from AndroidManifest.xml"?

By default, the IM SDK sets `allowBackup` to `false`, disabling the application's backup and restore functionality.

To resolve this, either remove the `allowBackup` attribute from your `AndroidManifest.xml` to disable backup and restore, or add `tools:replace="android:allowBackup"` to the `<application>` node to override the IM SDK's setting and use your own value.

```
// app/src/main/AndroidManifest.xml<application  android:name=".BaseApplication"  android:allowBackup="false"  android:icon="@drawable/app_ic_launcher"  android:label="@string/app_name"  android:largeHeap="true"  android:theme="@style/AppTheme"  tools:replace="android:allowBackup">
```

##### How do I resolve "Plugin with id 'kotlin-android' not found."?

The `TUIChat` component uses Kotlin code. Add the Kotlin build plugin as described in [Kotlin Setup](#kotlin_step).

##### Why do NullPointerExceptions or similar issues occur after copying TUIKit code into my own project module?

When copying a TUIKit module into your own project, in addition to migrating the Manifest file content, you must add the following dependency to the target module's `build.gradle` file. This is required for proper initialization of TUIKit components. Omitting this step may result in NullPointerExceptions or other errors.

```
dependencies {    annotationProcessor 'com.google.auto.service:auto-service:1.1.1'}
```

## Contact Us

If you have any questions or suggestions, feel free to join our [Telegram](https://t.me/tencent_imsdk) or [WhatsApp](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik) community, or [contact us](https://trtc.io/contact) for support.


---
*Source: [https://trtc.io/document/50057](https://trtc.io/document/50057)*
