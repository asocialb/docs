# Querying Message

## Feature Description

You can call `findMessages` to query a local message by `messageID`.

1. Only local messages can be queried, for example, received messages or historical messages pulled by API.
2. Audio-video group (AVChatRoom) messages cannot be queried, as they are not saved locally.

## Querying a Local Message

Call the `findMessages` API ([Details](https://pub.dev/documentation/tencent_im_sdk_plugin_platform_interface/latest/im_flutter_plugin_platform_interface/ImFlutterPlatform/findMessages.html)) to query a local message.

Sample code:

```
// Query a message by message IDV2TimValueCallback<List<V2TimMessage>> msgListRes = await TencentImSDKPlugin.v2TIMManager.getMessageManager().findMessages(messageIDList: ['msgid']);
```


---
*Source: [https://trtc.io/document/48023](https://trtc.io/document/48023)*
