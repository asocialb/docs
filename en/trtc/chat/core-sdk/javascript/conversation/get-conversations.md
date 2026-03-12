# Get Conversations

## Feature Overview

The Chat SDK provides an API for getting conversations, which can be used to get the `Conversation` object information of one or multiple specified conversations.

## Getting the Conversation List

> **Note:**The profile in the conversation list obtained through this API is incomplete (it only includes profile photo, nickname, etc., which is sufficient to render the conversation list). To query detailed conversation profiles, refer to `getConversationProfile`.By default, the client can pull 100 recent conversations from the cloud. After upgrading to the Pro edition ãPro Plus edition or Enterprise edition, up to 500 recent conversations can be pulled from the cloud. The retention period of a conversation is the same as that of the last message, which is 7 days by default. Please see [Pricing](https://trtc.io/pricing/chat).The retention period of a conversation is the same as that of the last message, which is 7 days by default.The returned data field `isSyncCompleted` of this API is used to indicate whether the synchronization of the conversation list from the cloud has been completed.After successful login, the SDK will actively pull the conversation list in a pagination request manner. The return result of this API is the conversation list pulled by the SDK. If the SDK has not yet pulled data from the cloud, calling this API will return an empty array.

##### **API**

```
chat.getConversationList(options);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| options | undefined \| Array \| Object | Parameter options.If `options` are not passed, it means all conversations are retrievedIf a non-empty array parameter is passed in, it indicates to get multiple specified conversationsPassing` { type, markType, groupName, hasUnreadCount, hasGroupAtInfo }` in the `options` means filtering the conversation list according to these conditions. |

##### **Return value**

`Promise`

##### **Examples**

```
// Get the full conversation listlet promise = chat.getConversationList();promise.then(function(imResponse) {  const conversationList = imResponse.data.conversationList; }).catch(function(imError) {  console.warn('getConversationList error:', imError); // Failed to obtain the conversation list});
```

```
// Get the list of specified conversationslet promise = chat.getConversationList([conversationID1, conversationID2]);promise.then(function(imResponse) {  const conversationList = imResponse.data.conversationList;}).catch(function(imError) {  console.warn('getConversationList error:', imError); // Failed to obtain the conversation list});
```

```
// Get all group conversations
let promise = chat.getConversationList({ type: TencentCloudChat.TYPES.CONV_GROUP });
promise.then(function(imResponse) {
  const conversationList = imResponse.data.conversationList;
});
```

```
// Get all "starred" conversationslet promise = chat.getConversationList({ markType: TencentCloudChat.TYPES.CONV_MARK_TYPE_STAR });promise.then(function(imResponse) {  const conversationList = imResponse.data.conversationList;});
```

```
// Get all unmarked conversationslet promise = chat.getConversationList({ markType: 0 });promise.then(function(imResponse) {  const conversationList = imResponse.data.conversationList;});
```

```
// Get all conversations under a specified conversation grouplet promise = chat.getConversationList({ groupName: 'Suppliers' });promise.then(function(imResponse) {  const conversationList = imResponse.data.conversationList;});
```

```
// Get all conversations that do not belong to any grouplet promise = chat.getConversationList({ groupName: '' });promise.then(function(imResponse) {  const conversationList = imResponse.data.conversationList;});
```

```
// Get all conversations with unread countslet promise = chat.getConversationList({ hasUnreadCount: true });promise.then(function(imResponse) {  const conversationList = imResponse.data.conversationList;});
```

```
// Get conversations that include group @messageslet promise = chat.getConversationList({ hasGroupAtInfo: true });promise.then(function(imResponse) {  const conversationList = imResponse.data.conversationList;});
```

## Getting the Conversation Details

This API can be used to obtain detailed information about a conversation.

##### **API**

```
chat.getConversationProfile(conversationID);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| conversationID | String | Conversation ID.Conversation ID formation method:`C2C${userID}` (Private chat)`GROUP{groupID}` (Group Chat)`@TIM#SYSTEM` (System Notification Session) |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.getConversationProfile(conversationID);promise.then(function(imResponse) {  // Obtained successfully  console.log(imResponse.data.conversation); // Conversation profile}).catch(function(imError) {  console.warn('getConversationProfile error:', imError); // Failed to obtain the conversation profile});
```


---
*Source: [https://trtc.io/document/48322](https://trtc.io/document/48322)*
