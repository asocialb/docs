# Step 1: SDK Integration

This document describes how to quickly integrate the Chat SDK for Unity to your projects. To configure and integrate the SDK, follow these steps.

## Environment Requirements

| Platform | Version |
| --- | --- |
| Unity | 2019.4.15f1 or later |
| Android | Android Studio 3.5 or later; devices with Android 4.1 or later for apps |
| iOS | Xcode 11.0 or later. Ensure that your project has a valid developer signature. |

## UPM Integration (Recommended)

1. Find the `manifest.json` file:
![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48db71a0966911ef992f52540075b605.png)
2. Modify it as follows:

```
{  "dependencies":{    "com.tencent.imsdk.unity":"https://github.com/TencentCloud/chat-sdk-unity.git#unity"  }}
```

3. Open the project in the Unity Editor, wait until dependencies are loaded, and confirm the Tencent Cloud Chat is successfully loaded.
![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48dd1bef966911efa04c52540055f650.jpeg)
4. This is a test step. You can download [IM_Api_Example](https://github.com/TencentCloud/tc-chat-sdk-unity/tree/main/Assets/IM_Api_Example) and put it in your project after decompression.
![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48d55b0a966911ef992f52540075b605.png)

> **Note:**IM_Api_Example is a demo used to test the callback data of the SDK's API. You can also call the API during early project development to manipulate your project.

Drag all the scenes under the

`IM_Api_Example/Assets`

folder to

`Build Settings`

, and make sure that the

`Main`

scene is put at the first place.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48d66fd6966911ef967c525400a9236a.jpeg)

Double-click the

`Main`

scene under

`IM_Api_Example/Assets`

to start the demo. Here, you can select the language.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48d3a04d966911ef834b525400f69702.jpeg)

Click

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48ba3aff966911efaaca525400fdb830.png)

on the right of the header and enter the information.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48d64327966911efa04c52540055f650.jpeg)

Click

**InitSDK**

and

**Login**

in

**Base Module**

for initialization and login. Then you can call the APIs available in IM_Api_Example.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48c795e0966911ef820f525400d5f8ef.jpeg)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/48dd47ad966911ef992f52540075b605.jpeg)


---
*Source: [https://trtc.io/document/46263](https://trtc.io/document/46263)*
