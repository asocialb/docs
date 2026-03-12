# FAQs

## What are the requirements for TUIRoomKit's dependencies on TRTC and IM SDK?

TUIRoomEngine will perform version verification when logging in, prompting you to use the correct TRTC SDK and IM SDK Version.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/488efca535c311eeaa5e5254005c1bd1.png)

## Can TUIRoomKit remove the dependency on IM SDK?

No, Real-time Conference SDK requires IM for signaling-related communication, including mic control, bullet screen, and other functions, so it needs to have a dependency on IM SDK.

## Does TUIRoomKit support features like conference scheduling?

It is not supported yet, this feature is in planning, you can follow our update log to get the latest information on the launch status of this feature.

## After integrating TUIRoomKit, how can I quickly modify the user name and user avatar?

You can set it by calling the `setSelfInfo` interface of TUIRoomKit.


---
*Source: [https://trtc.io/document/52820](https://trtc.io/document/52820)*
