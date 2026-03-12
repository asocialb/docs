# Do not Notify

## Feature Overview

You can set the message receiving option for a **one-to-one or group chat** to implement the notification muting feature.

The Chat SDK supports the following five message receiving options:

| Message Receiving Option | Feature Description |
| --- | --- |
| `TencentCloudChat.TYPES.MSG_REMIND_ACPT_AND_NOTE` | Messages will be received when the user is online, and offline push notifications will be received when the user is offline. |
| `TencentCloudChat.TYPES.MSG_REMIND_ACPT_NOT_NOTE` | The SDK receives a message and notifies you (by reporting the message receiving event), and you display no notification. This option is usually used to implement message notification muting. |
| `TencentCloudChat.TYPES.MSG_REMIND_DISCARD` | The SDK rejects a message. |
| `TencentCloudChat.TYPES.NOT_RECEIVE_OFFLINE_PUSH_EXCEPT_AT` | Messages will be received when the user is online, and only group @ mentioned messages will be received when the user is offline. |
| `TencentCloudChat.TYPES.NOT_RECEIVE_MSG_EXCEPT_AT` | The SDK only receives @ mentioned messages (only applicable to Topic). |

## UI Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/357eee70c71e11efad4f52540044a08e.png)

## Setting the Conversation Message Notification Type

> **Note:**As a group member, you can set the type of message notifications for the groups you are in."Message Do Not Disturb" generally means receiving messages online but not offline (in cases where there is offline push capability)."Reject Messages" means not receiving messages either online or offline; messages sent by the other party can be retrieved through `getMessageList`.This API supports setting the message notification type for community topics; simply pass the `topicID`as the `groupID`. If the community to which the topic belongs is set to `TencentCloudChat.TYPES.MSG_REMIND_DISCARD`, then the topic's settings will be ignored.Supports synchronization of reminder types for group conversation messages and topic messages across multiple terminals and instances.

##### **API**

```
chat.setMessageRemindType(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | Group ID or topic ID |
| userIDList | Array | List of `userID` values of the receivers of the one-to-one conversation. The number of `userID` values cannot exceed 30 per request. |
| messageRemindType | String | Group message notification type. Valid values:`TencentCloudChat.TYPES.MSG_REMIND_ACPT_AND_NOTE` (The SDK receives messages and notifies the receiver (by reporting the message receiving event), and a notification is displayed for the receiver)`TencentCloudChat.TYPES.MSG_REMIND_ACPT_NOT_NOTE` (The SDK receives messages and notifies the receiver (by reporting the message receiving event), and no notification is displayed. This option is usually used to implement message notification muting)`TencentCloudChat.TYPES.MSG_REMIND_DISCARD` (The SDK rejects messages)`TencentCloudChat.TYPES.NOT_RECEIVE_OFFLINE_PUSH_EXCEPT_AT`(Messages will be received when the user is online, and only group @ mentioned messages will be received when the user is offline)`TencentCloudChat.TYPES.NOT_RECEIVE_MSG_EXCEPT_AT`(The SDK only receives @ mentioned messages (only applicable to Topic)) |

##### **Return value**

`Promise`

##### **Examples**

```
// Set to reject group messages// (The `getMessageList` API can be called to pull messages sent by other group members)let promise = chat.setMessageRemindType({  groupID: 'group1',  messageRemindType: TencentCloudChat.TYPES.MSG_REMIND_DISCARD});promise.then(function(imResponse) {  // The SDK triggers the `TencentCloudChat.EVENT.CONVERSATION_LIST_UPDATED` event  // (after traversing the list and reading `Conversation.messageRemindType`).}).catch(function(imError) {  console.warn('setMessageRemindType error:', imError);});
```

```
// Enable message notifications after setting to reject group messageslet promise = chat.setMessageRemindType({  groupID: 'group1',  messageRemindType: TencentCloudChat.TYPES.MSG_REMIND_ACPT_AND_NOTE});promise.then(function(imResponse) {  // The SDK triggers the `TencentCloudChat.EVENT.CONVERSATION_LIST_UPDATED` event  // (after traversing the list and reading `Conversation.messageRemindType`).}).catch(function(imError) {  console.warn('setMessageRemindType error:', imError);});
```

```
// If the message notification type for a one-to-one conversation is set to mute message notifications// messages will be received when the user is online and will not be received when the user is offline// (with offline push supported)let promise = chat.setMessageRemindType({  userIDList: ['user1', 'user2'],  messageRemindType: TencentCloudChat.TYPES.MSG_REMIND_ACPT_NOT_NOTE});promise.then(function(imResponse) {  // The SDK triggers the `TencentCloudChat.EVENT.CONVERSATION_LIST_UPDATED` event  // (after traversing the list and reading `Conversation.messageRemindType`).  const { successUserIDList, failureUserIDList } = imResponse.data;  // List of successfully deleted `userID` values  successUserIDList.forEach((item) => {    const { userID } = item;  });  // List of `userID` values failed to be deleted  failureUserIDList.forEach((item) => {    const { userID, code, message } = item;  });}).catch(function(imError) {  console.warn('setMessageRemindType error:', imError);});
```

```
// If the message notification type for a community topic is set to mute message notifications,// messages will be received when the user is online and will not be received when the user is offline// (with offline push supported).let promise = chat.setMessageRemindType({  groupID: 'topicID',  messageRemindType: TencentCloudChat.TYPES.MSG_REMIND_ACPT_NOT_NOTE});promise.then(function(imResponse) {  // Message notification muting set successfully}).catch(function(imError) {  // Failed to set message notification muting  console.warn('setMessageRemindType error:', imError);});
```

```
// only receives @ mentioned messageslet promise = chat.setMessageRemindType({  groupID: 'topicID',  messageRemindType: TencentCloudChat.TYPES.NOT_RECEIVE_MSG_EXCEPT_AT });promise.then(function(imResponse) {}).catch(function(imError) {  console.warn('setMessageRemindType error:', imError);});
```

```
// When user online, set Topic only receive @messages (@me and @everyone's messages)let promise = chat.setMessageRemindType({  groupID: 'topicID',  messageRemindType: TencentCloudChat.TYPES.NOT_RECEIVE_MSG_EXCEPT_AT});
promise.then(function(imResponse) {
}).catch(function(imError) {
  console.warn('setMessageRemindType error:', imError);
});
```


---
*Source: [https://trtc.io/document/48031](https://trtc.io/document/48031)*
