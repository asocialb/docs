# Deleting Message

## Feature Description

Both local messages and cloud messages can be deleted.
When cloud messages are deleted, such messages will be deleted both locally and from the cloud and **cannot be recovered**.

If the last message is deleted, the `lastMessage` in the conversation will become the last but one message.

### Deleting a local message

Call `deleteMessageFromLocalStorage` ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_message_manager/V2TIMMessageManager/deleteMessageFromLocalStorage.html)) to delete a local message.

> **Note:**This API can only be used to delete a local historical message. After deleted, the message will be marked as deleted locally by the SDK and can no longer be pulled through `getHistoryMessage`.If the application is uninstalled and reinstalled, the delete marker will be lost locally, and the message can still be pulled through `getHistoryMessage`.

Sample code:

```
TencentImSDKPlugin.v2TIMManager.getMessageManager().deleteMessageFromLocalStorage(msgID: "");
```

### Deleting a message from the cloud

Call `deleteMessages` ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_message_manager/V2TIMMessageManager/deleteMessages.html)) to delete messages from the cloud.

This API deletes messages both locally and from the cloud, which cannot be recovered.

> **Note:**Up to 30 messages can be deleted per call.Messages to be deleted per call **must** be from the same conversation.This API can be called only once per second.If messages have been pulled on a device by an account, they will remain on the device after the API is called to delete them from the cloud; in other words, deleted messages are not synced.

Sample code:

```
TencentImSDKPlugin.v2TIMManager.getMessageManager().deleteMessages(msgIDs: ['messageid']);
```


---
*Source: [https://trtc.io/document/48009](https://trtc.io/document/48009)*
