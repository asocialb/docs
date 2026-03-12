# Draft

## Feature Overview

When sending a message, the user may want to switch to another chat window before finishing the message. The unfinished message can be saved through the `setConversationDraft` API, so that the user can get back to it through the `draftText` field of the `Conversation` object and finish it.

> **Note:**A conversation draft can contain only text.A conversation draft will be stored only in the local database and not on the server. Therefore, it cannot be synced across devices and will not be available after the application is uninstalled and reinstalled.

## UI Display

You can achieve the conversation draft effect shown in the figure below using this feature. Click on that conversation to enter the chat interface, and the draft content will automatically be filled into the input box:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eef0465c9ced11efa04c52540055f650.png)

## Setting a Conversation Draft

##### **API**

```
chat.setConversationDraft(options);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| conversationID | String | Conversation ID, which consists of:`C2C${userID} `(for one-to-one chats)`GROUP{groupID}` (for group chats) |
| draftText | String | draft content, passing an empty string `''` indicates canceling the draft. |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.setConversationDraft({   conversationID: 'GROUPpublic1',   draftText: '123'});promise.then(function(imResponse) {}).catch(function(imError) {  console.warn('setConversationDraft error:', imError);});
```

```
// Canceling a conversation draftlet promise = chat.setConversationDraft({   conversationID: 'GROUPpublic1',   draftText: ''});promise.then(function(imResponse) {}).catch(function(imError) {  console.warn('setConversationDraft error:', imError);});
```


---
*Source: [https://trtc.io/document/48848](https://trtc.io/document/48848)*
