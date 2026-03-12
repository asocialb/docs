# Recall a Message

## Feature Overview

This feature is used to recall a one-to-one or group message. After the message is recalled successfully, the value of its `isRevoked` attribute will be `true`.

> **Note:**The time limit for message recall is two minutes by default. You can log in to the [Chat Console](https://console.trtc.io/chat/login-message) to change this limit.Call the `getMessageList` API to pull a recalled message from roaming one-to-one or group messages. The receiver needs to properly display the recalled message based on the `isRevoked` attribute of the message object, for example, as "The other party recalled a message" in a one-to-one conversation or as "XXX recalled a message" in a group conversation.

## UI Display

| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4677feb8c72211efb54a52540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4676f62ec72211ef82565254005ef0f7.png) |
| --- | --- |

## **Recall a Message**

##### **API**

```
chat.revokeMessage(message);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| message | Message | Message instance |

##### **Return value**

`Promise`

##### **Examples**

```
// Recall a messagelet promise = chat.revokeMessage(message);promise.then(function(imResponse) {  // Message recalled successfully}).catch(function(imError) {  // Failed to recall the message  console.warn('revokeMessage error:', imError);});
```

```
// Received a message recall notificationchat.on(TencentCloudChat.EVENT.MESSAGE_REVOKED, function(event) {  // event.name - TencentCloudChat.EVENT.MESSAGE_REVOKED  // event.data - An array that stores Message objects - [Message]  // The `isRevoked` attribute value of each Message object is `true`.});
```

```
// Encountered the recalled message while getting the list of messages in the conversationlet promise = chat.getMessageList({conversationID: 'C2Ctest', count: 15});promise.then(function(imResponse) {  const messageList = imResponse.data.messageList; // Message list  messageList.forEach(function(message) {    if (message.isRevoked) {      // Process the recalled message    } else {      // Process ordinary messages    }  });});
```


---
*Source: [https://trtc.io/document/48882](https://trtc.io/document/48882)*
