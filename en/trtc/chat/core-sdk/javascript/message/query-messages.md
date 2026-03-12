# Query Messages

## Feature Overview

You can call `findMessages` to query a local message by `messageID`.

1. Only local messages can be queried, for example, received messages or historical messages pulled by API.
2. Audio-video group (AVChatRoom) messages cannot be queried, as they are not saved locally.

You can call `searchCloudMessages` to search for cloud messages(recommended).

## UI Display

| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12ab7347c71d11ef85bd525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/17dc6db0c71d11efb54a52540099c741.png) |
| --- | --- |

## Find A Local Message

> **Note:**This interface queries the messages stored locally through `getMessageList`.

##### **API**

```
chat.findMessage(messageID);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| messageID | String | Message ID |

##### **Return value**

[Message](https://web.sdk.qcloud.com/im/doc/en//Message.html) or `null`.

##### **Examples**

```
let message = chat.findMessage('144115217363870632-1647417469-77069006');if (message) {  // Read the attributes of `message`, such as `readReceiptInfo`}
```

### Search cloud messages

> **Noteï¼**This feature is a value-added service, and you need to [purchase the cloud search plugin](https://console.trtc.io/chat/plugin/TUICloudSearch?language=en).This interface has a local rate limit of 2 times per second.When searching for messages in [All Conversations], if the number of matching messages messageCount > 1, the interface returns an empty messageList []. You can display [`${messageCount`} ]related records on the UI. If you want to highlight the matching messages, please refer to [Specified Search] to highlight the returned messageList.When searching for messages in [All Conversations], if the number of matching messages in a conversation = 1, then messageList is the matching message.Community, topic, and live group chats do not support searching cloud messages.

##### **API**

```
chat.searchCloudMessages(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| keywordList | Array.<String> | Keyword list, supporting up to 5 keywords. When neither the message sender nor the message type is specified, the keyword list must not be empty; otherwise, the keyword list can be empty. |
| keywordListMatchType | String | Keyword list matching typeor: "or" relationship search (default)and: "and" relationship search |
| senderUserIDList | Array.<String> | Specify messages sent by userID, supporting up to 5 IDs. |
| messageTypeList | Array.<String> | Specify the collection of message types to search for, with the default being to search all types. When not provided, it indicates searching for all supported types of messages (`TencentCloudChat.TYPES.MSG_FACE`, `TencentCloudChat.TYPES.MSG_GRP_TIP`, and `TencentCloudChat.TYPES.MSG_GRP_SYS_NOTICE` are not supported).For specific values when provided, refer to `TencentCloudChat.TYPES`. |
| conversationID | String | Search "All Conversations" or "Specified Conversations". If not specified, it means all conversations. Default: All Conversations. Conversation ID composition:C2C${userID} (one-to-one chat)GROUP${groupID} (group chat) |
| timePosition | Number | The starting time point of the search. The default is 0, which means searching from now. Unit: seconds |
| timePeriod | Number | The past time range from the starting time point, in seconds. The default is 0, which means no time limit. Passing 24 * 60 * 60 represents the past day. |
| cursor | String | The starting position of each cloud search. Do not pass in the cursor for the first search; when continuing the search, fill in the value of the cursor returned by the last call to the searchCloudMessages interface.Note: The cursor is valid for 2 minutes during a full search. |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.searchCloudMessages({   keywordList: ['hello', 'where are you'],});
```

```
let promise = chat.searchCloudMessages({   keywordList: ['hello', 'where are you'],   keywordListMatchType: 'and',});
```

```
let promise = chat.searchCloudMessages({   keywordList: ['hello', 'where are you'],   senderUserIDList: ['user1', 'user2'],});
```

```
let promise = chat.searchCloudMessages({   keywordList: ['hello', 'where are you'],   messageTypeList: [TencentCloudChat.TYPES.MSG_TEXT, TencentCloudChat.TYPES.MSG_CUSTOM],});
```

```
let promise = chat.searchCloudMessages({   keywordList: ['hello', 'where are you'],   timePosition: Number((new Date().getTime()/1000).toFixed(0)),   timePeriod: 24 * 60 * 60,});promise.then(function(imResponse) {   const { totalCount, cursor, searchResultList } = imResponse.data;   // The total number of all conversations where messages meet the search criteria.   console.log(totalCount);   // The starting position for the next cloud search. If there is no next position, it indicates that the search result retrieval is complete.   console.log(cursor);   // Messages that meet the search criteria are grouped by conversation ID and returned in pages.   console.log(searchResultList);    for (let i = 0; i < searchResultList.length; i++) {      const searchResultItem = searchResultList[i];      const { conversationID, messageCount, messageList } = searchResultItem;      console.log(conversationID);      console.log(messageCount);ã      console.log(messageList);    }}).catch(function(imError) {   console.error(imError); // Search message failed});
```


---
*Source: [https://trtc.io/document/48024](https://trtc.io/document/48024)*
