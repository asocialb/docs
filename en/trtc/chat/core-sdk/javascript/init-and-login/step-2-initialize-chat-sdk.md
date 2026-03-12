# Step 2: Initialize Chat SDK

## Feature Description

You **must** initialize the Chat SDK before using its features.

## Initialization

You can initialize the SDK in the following steps:

1. Prepare an `SDKAppID`.
2. Call `TencentCloudChat.create` to initialize the SDK.
3. Add SDK event listeners.

The detailed steps are as follows.

### Preparing an SDKAppID

To perform the initialization, you must have a correct

`SDKAppID`

.
The

`SDKAppID`

uniquely identifies a Tencent Cloud Chat account. We recommend you apply for a new

`SDKAppID`

for each application. Messages are naturally isolated and cannot communicate between different

`SDKAppID`

values.
In the

Chat Console

, you can view all your

`SDKAppID`

values, and you can click

**Create Application**

to create an

`SDKAppID`

.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9a455078128511efbf645254007bbd8c.png)

### Calling the initialization API

After performing the above steps, you can call `TencentCloudChat.create` to initialize the SDK.

##### **API**

```
TencentCloudChat.create(options);
```

The `options` parameter is of the `Object` type. It contains the following properties:

| Name | Type | Description |
| --- | --- | --- |
| SDKAppID | Number | `SDKAppID` for the Instant Messaging Chat app |
| proxyServer | String \| undefined | WebSocket proxy server (the mini-program platform does not support the use of IP addresses) |
| fileUploadProxy | String \| undefined | Image, video, and file upload proxy address (the mini-program platform does not support the use of IP addresses) |
| fileDownloadProxy | String \| undefined | Image, video, and file download proxy address (the mini-program platform does not support the use of IP addresses) |

##### **Examples**

```
import TencentCloudChat from '@tencentcloud/chat';import TIMUploadPlugin from 'tim-upload-plugin';let options = {  SDKAppID: 0 // Replace 0 with the `SDKAppID` of your chat application when connecting.};// Create an SDK instance.// The `TencentCloudChat.create()` method returns the same instance for the same `SDKAppID`.// The SDK instance is usually represented by `chat`.let chat = TencentCloudChat.create(options);// Set the SDK log output level.// 0 - Common level. We recommend you use this level during access as it covers more logs.// 1 - Release level. We recommend you use this log level in a production environment.chat.setLogLevel(0); // chat.setLogLevel(1);// Register the Tencent Cloud Chat upload plugin.chat.registerPlugin({'tim-upload-plugin': TIMUploadPlugin});
```

### Listening on events

> **Note:**Please call this interface to listen for events before calling the login API to avoid missing events dispatched by the SDK.

##### **API**

```
chat.on(eventName, handler, context);
```

| Name | Type | Description |
| --- | --- | --- |
| eventName | String | Event names. All event names are stored in the `TencentCloudChat.EVENT` variable. If you need to view them, you can use `console.log(TencentCloudChat.EVENT)` to display all the events. |
| handler | Function | The method for handling events. When an event is triggered, this handler will be called to process it. |
| context | Object \| undefined | The expected context in which the handler executes. |

##### **Examples**

```
let onMessageReceived = function(event) {  // event.name - TencentCloudChat.EVENT.MESSAGE_RECEIVED  // event.data - An array to store Messages - [Message]};chat.on(TencentCloudChat.EVENT.MESSAGE_RECEIVED, onMessageReceived);
```

### Unlistening on events

##### **API**

```
chat.off(eventName, handler, context, once);
```

| Name | Type | Description |
| --- | --- | --- |
| eventName | String | Event names. All event names are stored in the `TencentCloudChat.EVENT` variable. If you need to view them, you can use `console.log(TencentCloudChat.EVENT)` to display all the events. |
| handler | Function | The method for handling events. When an event is triggered, this handler will be called to process it. |
| context | Object \| undefined | The expected context in which the handler executes. |
| once | Boolean \| undefined | Whether to unbind only once. |

##### **Examples**

```
let onMessageReceived = function(event) {  // event.name - TencentCloudChat.EVENT.MESSAGE_RECEIVED  // event.data - An array to store Messages - [Message]};chat.off(TencentCloudChat.EVENT.MESSAGE_RECEIVED, onMessageReceived);
```

## List of events that the integration client needs to listen and handle

##### SDK_READY

This event is triggered when the SDK enters the `ready` status. When the SDK is ready, you can call SDK APIs such as the message sending API to use various features of the SDK.

```
let onSdkReady = function(event) {  let message = chat.createTextMessage({    to: 'user1',    conversationType: TencentCloudChat.TYPES.CONV_C2C,    payload: { text: 'Hello world!'  }});  chat.sendMessage(message);};chat.on(TencentCloudChat.EVENT.SDK_READY, onSdkReady);
```

##### SDK_NOT_READY

This event is triggered when the SDK enters the `not ready` status. When SDK is not ready, you cannot use SDK features such as message sending. To use them, you need to call the `login` API to put the SDK into the `ready` status.

```
let onSdkNotReady = function(event) {  // chat.login({userID: 'your userID', userSig: 'your userSig'});};chat.on(TencentCloudChat.EVENT.SDK_NOT_READY, onSdkNotReady);
```

##### MESSAGE_RECEIVED

This event is triggered when the SDK receives a newly pushed one-to-one message, group message, group tip, or group system notification. When this event occurs, you can traverse event.data to obtain the message list and render it to the UI.

```
let onMessageReceived = function(event) {  // event.data - An array that stores Message objects - [Message]};chat.on(TencentCloudChat.EVENT.MESSAGE_RECEIVED, onMessageReceived);
```

##### MESSAGE_MODIFIED

This event is triggered when the SDK receives a notification for message modifications. When this event occurs, the message sender can traverse event.data to obtain the message list and update the content of the message with the same ID on the UI.

```
let onMessageModified = function(event) {  // event.data - An array that stores modified Message objects - [Message]};chat.on(TencentCloudChat.EVENT.MESSAGE_MODIFIED, onMessageModified);
```

##### MESSAGE_REVOKED

This event is triggered when the SDK receives a notification of message revocation. When this event occurs, the access side can traverse event.data to obtain data of the revoked messages list and render the recalled messages to the UI. For example, "The peer has recalled a message" can be displayed during a one-to-one conversation, and "XXX has recalled a message" can be displayed during a group conversation.

```
let onMessageRevoked = function(event) {  // event.data - An array that stores Message objects - [Message]  // The `isRevoked` attribute value of each Message object is `true`};chat.on(TencentCloudChat.EVENT.MESSAGE_REVOKED, onMessageRevoked);
```

##### MESSAGE_READ_BY_PEER

This event is triggered when the SDK receives a notification that messages have been read by the peer after the message receiver successfully calls [setMessageRead](https://web.sdk.qcloud.com/im/doc/v3/zh-cn/SDK.html#setMessageRead) to report the read status. When this event occurs, the access side can traverse event.data to obtain the list of messages read by the peer and render them to the UI. For example, in a C2C Chat, messages sent by the user can be changed from 'unread' to 'read'.

```
let onMessageReadByPeer = function(event) {  // event.data - An array that stores Message objects - [Message]  // The `isPeerRead` attribute value of each Message object is `true`};chat.on(TencentCloudChat.EVENT.MESSAGE_READ_BY_PEER, onMessageReadByPeer);
```

##### MESSAGE_READ_RECEIPT_RECEIVED

This event is triggered when the SDK receives message read receipts. When the message receiver calls [sendMessageReadReceipt](https://web.sdk.qcloud.com/im/doc/v3/zh-cn/SDK.html#sendMessageReadReceipt), the message sender will receive this event.

```
let onMessageReadReceiptReceived = function(event) {  // event.data - An array that stores read receipts  const readReceiptInfoList = event.data;  readReceiptInfoList.forEach((item) => {    const { groupID, userID, messageID, readCount, unreadCount, isPeerRead } = item;    // messageID - message ID    // userID - receiver ID    // isPeerRead - whether the message is read by peer    // groupID - group ID    // readCount - count of members read the message    // unreadCount - count of members do not read the message    const message = chat.findMessage(messageID);    if (message) {     if (message.conversationType === TencentCloudChat.TYPES.CONV_C2C) {       if (message.readReceiptInfo.isPeerRead === true) {         // message read by peer       }     } else if (message.conversationType === TencentCloudChat.TYPES.CONV_GROUP) {      if (message.readReceiptInfo.unreadCount === 0) {        // message read by all group members      } else {        // message.readReceiptInfo.readCount        // If you want to find out who have read the message, please call getGroupMessageReadMemberList      }     }    }  });}chat.on(TencentCloudChat.EVENT.MESSAGE_READ_RECEIPT_RECEIVED, onMessageReadReceiptReceived);
```

##### MESSAGE_EXTENSIONS_UPDATED

This event is triggered when the SDK receives a notification of message extension updates. After successfully calling [setMessageExtensions](https://web.sdk.qcloud.com/im/doc/v3/zh-cn/SDK.html#setMessageExtensions), both oneself and the peer user (in C2C) or group members (in Group) will receive this event.

```
let onMessageExtensionsUpdated = function(event) {  const { messageID, extensions } = event.data;  // messageID - message ID  // extensions - list of message extensions  extensions.forEach((item) => {   const { key, value } = item;  });};chat.on(TencentCloudChat.EVENT.MESSAGE_EXTENSIONS_UPDATED, onMessageExtensionsUpdated);
```

##### MESSAGE_EXTENSIONS_DELETED

This event is triggered when the SDK receives a notification that Message Extension is deleted. After successfully calling [deleteMessageExtensions](https://web.sdk.qcloud.com/im/doc/v3/zh-cn/SDK.html#deleteMessageExtensions), both the sender and the recipient (in C2C Chat) or group members (in Group) will receive this event.

```
let onMessageExtensionsDeleted = function(event) {  const { messageID, keyList } = event.data;  // messageID - message ID  // keyList - list of keys which are deleted  keyList.forEach((key) => {   // console.log(key)  });};chat.on(TencentCloudChat.EVENT.MESSAGE_EXTENSIONS_DELETED, onMessageExtensionsDeleted);
```

##### CONVERSATION_LIST_UPDATED

This event is triggered when the conversation list is updated. event.data is an array that stores the Conversation objects.

```
let onConversationListUpdated = function(event) {  console.log(event.data); // Array that stores Conversation objects - [Conversation]};chat.on(TencentCloudChat.EVENT.CONVERSATION_LIST_UPDATED, onConversationListUpdated);
```

##### TOTAL_UNREAD_MESSAGE_COUNT_UPDATED

This event is triggered when the total unread message count of all conversations is updated. event.data is the current unread count of both one-on-one and group chats.

```
let onTotalUnreadMessageCountUpdated = function(event) {  console.log(event.data);};chat.on(TencentCloudChat.EVENT.TOTAL_UNREAD_MESSAGE_COUNT_UPDATED, onTotalUnreadMessageCountUpdated);
```

##### CONVERSATION_GROUP_LIST_UPDATED

This event is triggered when the conversation group list is updated.

```
let onConversationGroupListUpdated = function(event) {  console.log(event.data);}chat.on(TencentCloudChat.EVENT.CONVERSATION_GROUP_LIST_UPDATED, onConversationGroupListUpdated);
```

##### CONVERSATION_IN_GROUP_UPDATED

This event is triggered when conversations in a conversation group are updated (e.g., adding a conversation to the group or removing it from the group).

```
let onConversationInGroupUpdated = function(event) {  const { groupName, conversationList }  = event.data;}chat.on(TencentCloudChat.EVENT.CONVERSATION_IN_GROUP_UPDATED, onConversationInGroupUpdated);
```

##### GROUP_LIST_UPDATED

This event is triggered when the SDK group list is updated. The client side can traverse event.data to obtain the group list and render it to the UI.

```
let onGroupListUpdated = function(event) {   console.log(event.data);// Array that stores Group objects - [Group]};chat.on(TencentCloudChat.EVENT.GROUP_LIST_UPDATED, onGroupListUpdated);
```

##### GROUP_ATTRIBUTES_UPDATED

This event is triggered when attributes of a group are updated. The client side can obtain the updated group attributes data through event.data.

```
let onGroupAttributesUpdated = function(event) {   const groupID = event.data.groupID   const groupAttributes = event.data.groupAttributes   console.log(event.data);};chat.on(TencentCloudChat.EVENT.GROUP_ATTRIBUTES_UPDATED, onGroupAttributesUpdated);
```

##### GROUP_COUNTER_UPDATED

This event is triggered when counters of a group are updated. Both the user and other group members will receive this notification.

```
let onGroupCounterUpdated = function(event) {  const { groupID, key, value } = event.data;};chat.on(TencentCloudChat.EVENT.GROUP_COUNTER_UPDATED, onGroupCounterUpdated);
```

##### TOPIC_CREATED

This event is triggered when a topic is created.

```
let onTopicCreated = function(event) {   const groupID = event.data.groupID; // community group ID   const topicID = event.data.topicID; // topic ID   console.log(event.data);};chat.on(TencentCloudChat.EVENT.TOPIC_CREATED, onTopicCreated);
```

##### TOPIC_DELETED

This event is triggered when a topic is removed.

```
let onTopicDeleted = function(event) {   const groupID = event.data.groupID; // community group ID   const topicIDList = event.data.topicIDList; // topic ID   console.log(event.data);};chat.on(TencentCloudChat.EVENT.TOPIC_DELETED, onTopicDeleted);
```

##### TOPIC_UPDATED

This event is triggered when a topic profile is updated.

```
let onTopicUpdated = function(event) {   const groupID = event.data.groupID; // community group ID   const topic = event.data.topic; // the lastest topic   console.log(event.data);};chat.on(TencentCloudChat.EVENT.TOPIC_UPDATED, onTopicUpdated);
```

##### PROFILE_UPDATED

This event is triggered when the profile of the current user or friends' profiles are changed. event.data is an array that stores Profile objects.

```
let onProfileUpdated = function(event) {  console.log(event.data); // Array that stores Profile objects};chat.on(TencentCloudChat.EVENT.PROFILE_UPDATED, onProfileUpdated);
```

##### USER_STATUS_UPDATED

This event is triggered when the statuses of subscribed users or friends are updated, including online status and custom status.

```
let onUserStatusUpdated = function(event) {   console.log(event.data);   const userStatusList = event.data;   userStatusList.forEach((item) => {     const { userID, statusType, customStatus } = item;     // userID     // statusType, described as follows:     // TencentCloudChat.TYPES.USER_STATUS_UNKNOWN     // TencentCloudChat.TYPES.USER_STATUS_ONLINE     // TencentCloudChat.TYPES.USER_STATUS_OFFLINE     // TencentCloudChat.TYPES.USER_STATUS_UNLOGINED     // customStatus   })};chat.on(TencentCloudChat.EVENT.USER_STATUS_UPDATED, onUserStatusUpdated);
```

##### BLACKLIST_UPDATED

This event is triggered when the SDK blocklist is updated.

```
let onBlacklistUpdated = function(event) {  console.log(event.data); // Your blocklist. The value is an array that stores `userID` values.};chat.on(TencentCloudChat.EVENT.BLACKLIST_UPDATED, onBlacklistUpdated);
```

##### FRIEND_LIST_UPDATED

This event is triggered when the friend list is updated.

```
let onFriendListUpdated = function(event) {  console.log(event.data);}chat.on(TencentCloudChat.EVENT.FRIEND_LIST_UPDATED, onFriendListUpdated);
```

##### FRIEND_GROUP_LIST_UPDATED

This event is triggered when the friend group list is updated.

```
let onFriendGroupListUpdated = function(event) {  console.log(event.data);}chat.on(TencentCloudChat.EVENT.FRIEND_GROUP_LIST_UPDATED, onFriendGroupListUpdated);
```

##### FRIEND_APPLICATION_LIST_UPDATED

This event is triggered when the friend application list is updated.

```
let onFriendApplicationListUpdated = function(event) {  // friendApplicationList - Friend request list - [FriendApplication]  // unreadCount - Number of unread friend requests  const { friendApplicationList, unreadCount } = event.data;  // Friend requests received by you (friend requests that are sent to you by others)  const applicationSentToMe = friendApplicationList.filter((friendApplication) => friendApplication.type === TencentCloudChat.TYPES.SNS_APPLICATION_SENT_TO_ME);  // Friend requests sent by you (friend requests that you send to others)  const applicationSentByMe = friendApplicationList.filter((friendApplication) => friendApplication.type === TencentCloudChat.TYPES.SNS_APPLICATION_SENT_BY_ME);};chat.on(TencentCloudChat.EVENT.FRIEND_APPLICATION_LIST_UPDATED, onFriendApplicationListUpdated);
```

##### KICKED_OUT

This event is triggered when the current user is kicked offline.

```
TencentCloudChat.TYPES.KICKED_OUT_MULT_ACCOUNT
```

##### NET_STATE_CHANGE

This event is triggered when the network status changes.

```
TencentCloudChat.TYPES.NET_STATE_CONNECTED -
```

## Deinitialization

Destroy the SDK instance. The SDK will first log out, then disconnect the WebSocket long connection, and release resources.

```
chat.destroy();
```

**Next step,**[login and logout.](https://trtc.io/document/47970?platform=web&product=chat&menulabel=sdk)


---
*Source: [https://trtc.io/document/47967](https://trtc.io/document/47967)*
