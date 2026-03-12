# Step 1: Install Chat SDK

This document describes how to quickly integrate the Chat SDK into your Android project.

## Environment Requirements

- JDK 1.6.
- Android 4.1 (SDK API level 16) or above

## Integrating SDK (AAR)

You can use Gradle to automatically load the AAR file or manually download the AAR file and import it into your project.

### Method 1: Automatic Loading (AAR)

You can configure Gradle to automatically download the latest Chat SDK that has been released in the Maven Central library.
Use Android Studio to open your project and modify the `app/build.gradle` file in three simple steps to integrate the SDK to your project, as shown below:

#### Step 1. Add SDK Dependencies

1. Find `build.gradle` of the app and add `mavenCentral()` dependencies to `repositories`.

```
repositories {    google()    jcenter()    // Add the `mavenCentral` repository.    mavenCentral()}
```

2. Add the Chat SDK dependencies to `dependencies`.

```
dependencies {    // Add the SDK and use the latest version number as recommended    api 'com.tencent.imsdk:imsdk-plus:Version number'    // If you need to add the Quic plugin, please uncomment the next line (Note: the plugin version number must match the Chat SDK version number)    // api "com.tencent.imsdk:timquic-plugin:Version number"}
```

Replace `Version number` with the actual version number of the SDK. We recommend you use the [latest version](https://github.com/TencentCloud/chat-uikit-android/tree/main/ChatSDK).Take the version number 5.4.666 as an example:

```
dependencies {    api 'com.tencent.imsdk:imsdk-plus:5.4.666'}
```

> **Note**Quic plugin provides axp-quic multiplexing protocol, which has better weak network resistance and can still provide services even when the network packet loss rate reaches 70%. This plugin is only available on the Chat Pro editionãPro Plus editionãEnterprise edition, [purchase the Pro editionãPro Plus editionãEnterprise edition](https://trtc.io/buy/chat) to use it. To ensure proper functionality, please update the client SDK to version 7.7.5282 or higer.

#### Step 2. Specify the App Architecture

InÂ `defaultConfig`, specify the CPU architecture used by the appÂ (armeabi-v7a, arm64-v8a, x86, and x86_64 are supported starting from Chat SDK v4.3.118).

```
defaultConfigÂ {    ndkÂ {        abiFiltersÂ "arm64-v8a"    }}
```

#### Step 3. Sync the SDK

Click theÂ `Sync`Â icon. If the connection to JCenter is normal, the SDK will be automatically downloaded and integrated to your project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9aa9eac41ef911ee818e525400088f3a.png)

### Method 2: Manual Download (AAR)

If JCenter cannot be accessed, you can manually download the SDK and integrate it into your project:

#### Step 1. Download SDK

Download the latest version of theÂ [Chat SDK](https://github.com/TencentCloud/chat-uikit-android/tree/main/ChatSDK)Â from GitHub.

#### Step 2. Copy SDK to the Project Directory

Copy the downloaded AARÂ fileÂ to the **/libs** directory of the project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1cdd70e91ef811eebb095254005c1bd1.png)

#### Step 3. Specify, Compile, and Run

In theÂ `defaultConfig`Â ofÂ `app/build.gradle`, specify the CPU architecture used by the appÂ (armeabi-v7a, arm64-v8a, x86, and x86_64 are supported starting from SDK v4.3.118).

```
defaultConfigÂ {    ndkÂ {        abiFiltersÂ "arm64-v8a"    }}
```

> **Noteï¼**If you need to add a Quic plugin, please refer to the previous steps and manually download the integrated Quic plugin.

## Integrating SDK

If youÂ doÂ not want to integrate the AAR library, you can integrate the Chat SDK by importing the JAR and SO libraries.

### Step 1. Download and Decompress SDK

[Download](https://github.com/TencentCloud/chat-uikit-android/tree/main/ChatSDK)Â the latest version of the AARÂ file from GitHub and decompress it. The extracted folder contains a JARÂ fileÂ and an SO subfolder. Rename **classes.jar** to **imsdk.jar**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/70993a501ef811eea27e525400c56988.png)

### Step 2. Copy SDK to the Project Directory

Copy the renamed JARÂ fileÂ and SO files of different architectures to the default loading directories of Android Studio.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9af213901ef811ee818e525400088f3a.png)

### Step 3. Specify, Compile, and Run

In theÂ `defaultConfig`Â ofÂ `app/build.gradle`, specify the CPU architecture used by the appÂ (armeabi-v7a, arm64-v8a, x86, and x86_64 are supported starting from Chat SDK v4.3.118).

```
defaultConfigÂ {    ndkÂ {        abiFiltersÂ "arm64-v8a"    }}
```

## Configuring Permissions

To configure app permissionsÂ inÂ `AndroidManifest.xml`, the Chat SDK requires the following permissions:

```
<uses-permission android:name="android.permission.INTERNET" /><uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /><uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
```

## Configuring Obfuscation Rules

In theÂ `proguard-rules.pro`Â file,Â addÂ the Chat SDK classes to theÂ "do not obfuscate"Â list.

```
-keep class com.tencent.imsdk.** { *; }
```


---
*Source: [https://trtc.io/document/34306](https://trtc.io/document/34306)*
