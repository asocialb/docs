# Modify a Message

## Feature Overview

This feature enables any member in a conversation to modify a successfully sent message in the conversation. The message will be synced to all the members in the conversation once modified successfully.

## UI Display

You can use the message modification API to change the `cloudCustomData` of a message, enabling features such as message replies and references as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f551b7f1d9b11efafe1525400db4520.png)

## Modifying a Message

This API is used to modify a message. After a user modifies a message successfully, both the user and the receiver (one-to-one) or group members (Group) will receive the `MESSAGE_MODIFIED` event.

> **Note:**It does not support modifying online messages or AVChatRoom messages. Do not modify the `random/sequence/time` fields of a message.It only supports modifying text, custom, geographical location, and emoji messages.If a message is modified by another member during modification, the SDK will return the error code 2480, indicating that a conflict occurred while modifying the message.It supports for modifying the `cloudCustomData `field of all types of messages.

##### **API**

```
chat.modifyMessage(message);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| message | Message | Message instance |

##### **Return value**

`Promise`

##### **Examples**

```
// Listen for the `MESSAGE_MODIFIED` event// which will be delivered by the SDK after a message is modified successfullylet onMessageModified = function(event) {  // event.data - An array that stores modified Message objects - [Message]};chat.on(TencentCloudChat.EVENT.MESSAGE_MODIFIED, onMessageModified);// Change the text content of `txtMessage` to `Hello Tencent`txtMessage.payload.text = "Hello Tencent";let promise = chat.modifyMessage(txtMessage);promise.then(function(imResponse) {  const { message } = imResponse.data;  // Message modified successfully. `message` is the latest message.}).catch(function(imError) {  // Failed to modify the message  const { code, data } = imError;  if (code === 2480) {    // A conflict occurred while modifying the message. `data.message` is the latest message.  } else if (code === 2481) {    // Audio-video group messages cannot be modified.  } else if (code === 20026) {    // The message does not exist.  }});
```


---
*Source: [https://trtc.io/document/48005](https://trtc.io/document/48005)*
