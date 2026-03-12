# iOS

This document primarily introduces how to quickly run through the AIConversationKit Demo project and experience high-quality conversational AI project. Follow this document, and you can run through the Demo within 20 minutes and eventually experience a conversational AI example with a complete UI interface.

| **Conversational AI Interface** |
| --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c82eb29012e511f0854e525400454e06.png) |

## Environment Preparation

- Minimum compatibility with iOS 13. Recommend using iOS 13 and above versions.
- Xcode 13 and above versions.

## Download Demo

1. Download the source code of [AIConversationKit Demo](https://github.com/Tencent-RTC/AIConversationKit) from github, or run the following commands in command line:

```
  git clone https://github.com/Tencent-RTC/AIConversationKit.git
```

2. After unzipping the folder, use the Tencent Cloud Command Line Interface (TCCLI), enter `AIConversationKit/Example` path, and execute pod install.

## Configuration Demo

1. First, go to [console](https://console.trtc.io/) to create an application, and then [activate the corresponding service](https://www.tencentcloud.com/document/product/647/69002#).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fe46274d21a711f091625254001c06ec.png)

2. After creation, go to the application details page, select **RTC-Engine** **> Conversational AI**, refer to [No-Code Quick Integration Of Conversational AI Feature](https://www.tencentcloud.com/document/product/647/68137) configure conversational AI parameters, click **Quick Integration**  in the lower right corner, switch to iOS, and obtain SecretId, SecretKey and Config parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c85b244512e511f0a9cd5254007c27c5.png)

3. Use Xcode to open the AIConversationApp.xcworkspace project. Find the `App/Debug/Config.swift` file within the project. Fill in the corresponding **SecretId** and **SecretKey** obtained in the previous step:

```
let SECRET_ID = ""let SECRET_KEY = ""
```

4. Copy the config information obtained in step 3 to `App/Debug/Config.json`.

## Run through the Demo

1. Configure certificate

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c8493a2912e511f0aaa3525400e889b2.png)

2. Select a device that can run.
3. Click to run the Demo.

## Start Your First Dialogue

Start talking to AI, for example, ask AI to tell a joke.


---
*Source: [https://trtc.io/document/69000](https://trtc.io/document/69000)*
