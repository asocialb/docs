# Webhooks Overview

For convenience in controlling the functional form of your App, CallKit provides callback capability.

## Feature Description

Users can configure a callback for a specified Url via the REST API method. When the executed CallbackCommand is in the configuration list, the callback will be triggered.

## Must-Knows

- Only one callback can be configured for a sdkAppId.
- Ensure that the callback URL can be accessed normally.

> **Warning:**If you use the deprecated interfaces`TUICallKit.call()` or `TUICallKit.groupCall()`to initiate a call, please check the**Deprecated Document** directory. If you have any questions, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/68933](https://trtc.io/document/68933)*
