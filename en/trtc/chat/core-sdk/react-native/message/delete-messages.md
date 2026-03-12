# Delete Messages

## Feature Overview

After a message is deleted successfully, its `isDeleted` is `true`. In one-to-one conversations, deleted messages cannot be pulled on the next login, but the receiver will not be affected. In group conversations, deleted messages cannot be pulled on the next login, but other group members will not be affected.

> **Note:**Up to 30 messages can be deleted at a time. If more than 30 messages are selected, the first 30 messages will be deleted.Messages to be deleted must be from the same conversation, that is, the conversation of the first message in the message list.This API can be called only once per second.Deleted messages are not synced.Messages cannot be deleted from audio-video groups (AVChatRoom), and if you call this API, the error code 10035 will be returned.This API does not support deleting group system notifications.

## UI Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7058314ecbe011ef81865254005ef0f7.png)

##### **API**

```
chat.deleteMessage(messageList);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| messageList | Array | List of messages (up to 30) in the same conversation |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.deleteMessage([message1, message2, message3, ...]);promise.then(function(imResponse) {  // Messages deleted successfully}).catch(function(imError) {  // Failed to delete the messages  console.warn('deleteMessage error:', imError);});
```


---
*Source: [https://trtc.io/document/48878](https://trtc.io/document/48878)*
