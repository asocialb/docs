# Android

This document primarily introduces how to quickly run through the AIConversationKit Demo project and experience high-quality conversational AI project. Follow this documentation, and you can run through the Demo within 20 minutes and eventually experience a conversational AI project with a complete UI interface.

| **Conversational AI Interface** |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ba53190412e511f0aaa3525400e889b2.png) |

## Environment Preparation

- Minimum compatibility with Android 4.4 (SDK API Level 19). Recommend using Android 5.0 (SDK API Level 21) and above versions.
- Android Studio 3.5 and above versions.

## Download Demo

1. Download the source code of [AIConversationKit Demo](https://github.com/Tencent-RTC/AIConversationKit) from github, or run the following commands in command line:

```
git clone https://github.com/Tencent-RTC/AIConversationKit.git
```

2. Open the **AIConversationKit/Android** project via Android Studio.

## Configuration Demo

1. First, go to [console](https://console.trtc.io/) to create an application, and then [activate the corresponding service](https://www.tencentcloud.com/document/product/647/69002#).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2a074adf211611f0a62e525400454e06.png)

2. After creation, go to the application details page, select **RTC-Engine** **> Conversational AI**, refer to [No-Code Quick Integration Of Conversational AI Feature](https://www.tencentcloud.com/document/product/647/68137) configure conversational AI parameters, click **Quick Integration** in the lower right corner, switch to Android, and retrieve the SecretId, SecretKey and Config parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f0a28cd712e511f09b3252540044a08e.png)

3. Open the project and find the `Android/app/src/main/java/com/trtc/uikit/aiconversationkit/demo/Config.java` file within the project. Fill in the obtained corresponding **SecretId**, **SecretKey**, and **Config** from the previous step:

```
public class Config {    public static final String SECRET_ID  = "";    public static final String SECRET_KEY = "";    public static final String CONFIG     = "";}
```

## Run through the Demo

1. In the upper-right corner of Android Studio as shown below, select the device on which you want to run the Demo:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ba46c7ad12e511f0aaa3525400e889b2.png)

2. After completing the selection, click to run and operate the AIConversationKit Android Demo on the target device.

## Start Your First Dialogue

Start talking to AI, for example, ask AI to tell a joke.


---
*Source: [https://trtc.io/document/69001](https://trtc.io/document/69001)*
