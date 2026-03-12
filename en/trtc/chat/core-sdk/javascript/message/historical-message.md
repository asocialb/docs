# Historical Message

## Feature Overview

The SDK supports message pull by page, sequence, or time range. Historical messages stored in the cloud are subject to the following time limits:

- Developer edition: The free storage period is 7 days and cannot be extended.
- Standard edition: The free storage period is 7 days and cannot be extended.
- Premium edition: The free storage period is 30 days and cannot be extended.

> **Note**Extending the storage period of historical messages is a Value-Added Service. You can log in to the [Chat Console](https://console.trtc.io/) to modify the relevant configuration. For billing details, see [Pricing](https://trtc.io/pricing/chat). Rich media messages (such as images, files, and audios) have the same storage periods as historical messages.

## Pulling a Message List

### getMessageList

This API is used to pull the list of messages in a specified conversation by page. It needs to be called when the message list is rendered for the first time after the user enters the conversation, or when the user pulls down the list to view more messages.

> **Note**This API can retrieve message history for all group types **except AVChatRoom**.By default, **AVChatRoom** does not store message history. New members can only see messages sent after they join the room. To improve engagement, you can enable message history for new members:Navigate to: **Chat Console > Configuration > Group Configuration > Message History for New Members**Configuration: Set the number of recent messages visible to new membersAvailability: **Pro edition, Pro Plus edition,**or**Enterprise edition** onlyLimits: New members can receive up to **50** messages from the **past 24 hours** via `MESSAGE_RECEIVED` eventIf you want to search local messages, use `findMessage`. If you want to search full cloud messages, use `searchCloudMessages` (This is a value-added service requiring the Cloud Search Plugin. [Purchase here](https://console.trtc.io/chat/plugin/TUICloudSearch)).

##### **API**

```
chat.getMessageList(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| conversationID | String | Conversation ID, which consists of:`C2C${userID}` (for one-to-one chats)`GROUP${groupID} `(for group chats)`GROUP${topicID}` (topic)`@TIM#SYSTEM` (system notification conversation) |
| nextReqMessageID | String \| undefined | Message ID used for the subsequent paged pull. Leave this field empty for the first pull and enter its the value returned by the `getMessageList` API for the subsequent pull. |

##### **Return value**

`Promise`

##### **Examples**

```
// Pull the message list for the first time when a conversation is openedlet promise = chat.getMessageList({conversationID: 'C2Ctest'});promise.then(function(imResponse) {  const messageList = imResponse.data.messageList; // Message list  // This parameter must be passed in for the next pull by page.  const nextReqMessageID = imResponse.data.nextReqMessageID;  // It indicates whether all messages have been pulled.  const isCompleted = imResponse.data.isCompleted;});
```

```
// Pull down the message list to view more messageslet promise = chat.getMessageList({conversationID: 'C2Ctest', nextReqMessageID});promise.then(function(imResponse) {  const messageList = imResponse.data.messageList; // Message list  // This parameter must be passed in for the next pull by page.  const nextReqMessageID = imResponse.data.nextReqMessageID;  // It indicates whether all messages have been pulled.  const isCompleted = imResponse.data.isCompleted; });
```

### getMessageListHopping

This API is used to pull a message list by specified sequence or time range.

##### **API**

```
chat.getMessageListHopping(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| conversationID | String | Conversation ID, which consists of:`C2C${userID}` (for one-to-one chats)`GROUP${groupID} `(for group chats)`GROUP${topicID}` (topic). |
| sequence | Number \| undefined | `sequence` of the message starting from which to pull roaming group messages |
| time | Number \| undefined | Server time of the message, starting from which to pull roaming one-to-one messages |
| direction | Number | Message pull direction, which defaults to `0`.0: pull in reverse chronological order  to get older messages;1: pull in chronological order to get recent messages |
| count | Number \| undefined | Number of messages to be pulled. It defaults toÂ 15, which is also the maximum value, indicating that up to 15 messages can be pulled and returned at a time. |

##### **Return value**

`Promise`

##### **Examples**

```
// Pull roaming group messages by sequence.// `direction`: 0: pull in reverse chronological order to get older messages// 1: pull in chronological order to get recent messageslet promise = chat.getMessageListHopping({  conversationID: 'GROUPtest',  sequence: 100,  count: 15,  direction: 0});promise.then(function(imResponse) {  const messageList = imResponse.data.messageList; // Message list});
```

****

```
// Pull roaming one-to-one messages by time range.// `direction`: 0: pull in reverse chronological order to get older messages// 1: pull in chronological order to get recent messageslet promise = chat.getMessageListHopping({  conversationID: 'C2Ctest',  time: xxx,  count: 15,  direction: 0});promise.then(function(imResponse) {  const messageList = imResponse.data.messageList; // Message list});
```


---
*Source: [https://trtc.io/document/47999](https://trtc.io/document/47999)*
