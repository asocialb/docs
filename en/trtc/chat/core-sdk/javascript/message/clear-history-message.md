# Clear History Message

## Feature Overview

When messages in a conversation are cleared, all the messages in the conversation will be cleared both locally and from the cloud, but the conversation itself will not be deleted.

> **Note:**When messages in a conversation are cleared, `unreadCount` will be set to `0`, and the content of `lastMessage` will be cleared as well.This API cannot be used to clear messages in a topic.

## UI Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bb7096d2cbe111ef97675254007c27c5.png)

## Clearing Messages

##### **API**

```
chat.clearHistoryMessage(conversationID);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| conversationID | String | Conversation ID, in the format of:`C2C${userID}` (for one-to-one chats)`GROUP{groupID}` (for group chats) |

##### **Return value**

`Promise`

##### **Examples**

```
// Clear one-to-one messages locally and from the cloudlet promise = chat.clearHistoryMessage('C2CExample');promise.then(function(imResponse) {  // Messages cleared successfully}).catch(function(imError){  console.warn('clearHistoryMessage error:', imError); // Message clearing failure information});
```

```
// Clear group messages locally and from the cloudlet promise = chat.clearHistoryMessage('GROUPExample');promise.then(function(imResponse) {  // Messages cleared successfully}).catch(function(imError){  console.warn('clearHistoryMessage error:', imError); // Message clearing failure information});
```


---
*Source: [https://trtc.io/document/53498](https://trtc.io/document/53498)*
