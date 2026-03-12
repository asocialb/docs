# Delete Conversations

## Feature Overview

If a user doesn't want to view the historical one-to-one or group messages after deleting a friend or leaving a group, the user can choose to delete the conversation.

## Deleting a Conversation

> **Note:**When deleting a conversation, the default behavior is to clear the conversation history messages. Please be cautious before proceeding. If you need to retain the conversation history messages, please set `clearHistoryMessage` to `false`.Multi-client sync is disabled for conversation deletion by default. To enable it, log in to the [Chat Console](https://console.trtc.io/chat/login-message), select **Application Configuration** > **Feature Configuration** > **Login and Message** > **Multi-client Synchronization Settings**, and enable **Sync Conversation Deletion Across Clients**.It supports for bulk deletion of conversations (up to 100 conversations at a time), with the option to choose whether to clear the history messages.In scenarios such as members leaving the group, the group owner dissolving the group, or members being kicked out of the group, if the user's login state has not expired, the corresponding group conversation will still be retained in the local conversation list. At this time, users can view the cached historical messages, but they cannot send messages.

##### **API**

```
chat.deleteConversation(options);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| options | String \| Object | If the options parameter is of the String type, it's valid values as blow:`C2C${userID}` (for a one-to-one chat)`GROUP{groupID} `(for a group chat)`@TIM#SYSTEM `(for a system notification conversation) |

##### **Return value**

`Promise`

##### **Examples**

```
// delete the specified conversation and clear chat historylet promise = chat.deleteConversation('C2CExample');promise.then(function(imResponse) {  // Deleted the conversation successfully  const { conversationID } = imResponse.data;// ID of the deleted conversation}).catch(function(imError) {  console.warn('deleteConversation error:', imError); // Failed to delete the conversation});
```

```
// delete the specified conversation and not clear chat historylet promise = chat.deleteConversation({conversationIDList: ['C2CExample'], clearHistoryMessage: false});promise.then(function(imResponse) {  // Deleted the conversation successfully  const { conversationIDList } = imResponse.data; // ID of the deleted conversation}).catch(function(imError) {  console.warn('deleteConversation error:', imError); // Failed to delete the conversation});
```

```
// delete multiple conversations and clear chat historylet promise = chat.deleteConversation({conversationIDList: ['C2CExample', 'GROUPExample']});promise.then(function(imResponse) {  const { conversationIDList } = imResponse.data; // ID list of the deleted conversations}).catch(function(imError) {  console.warn('deleteConversation error:', imError); // Failed to delete the conversation});
```

```
// delete multiple conversations and clear chat historylet promise = chat.deleteConversation({  conversationIDList: ['C2CExample', 'GROUPExample'],  clearHistoryMessage: false});promise.then(function(imResponse) {  const { conversationIDList } = imResponse.data; // ID list of the deleted conversations}).catch(function(imError) {  console.warn('deleteConversation error:', imError); // Failed to delete the conversation});
```


---
*Source: [https://trtc.io/document/49497](https://trtc.io/document/49497)*
