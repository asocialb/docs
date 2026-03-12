# Targeted Group Message

## Feature Overview

A targeted group message is a message sent to specified members in a group, which cannot be received by other group members.

> **Note:**To use this feature, you need to purchase the Pro edition ãPro Plus edition or Enterprise edition as instructed in [Pricing](https://trtc.io/pricing/chat).When creating a group @ message, you cannot specify the list of group members to receive the message (`receiverList`).The targeted group message feature is not available for community and audio-video (AVChatRoom) groups.By default, targeted group messages are excluded from the unread count of the group conversation.

## UI Display

By using the targeted group message feature, you can achieve the effect shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2d1430581db211efafe1525400db4520.png)

## Sending a Targeted Group Message

To send a targeted group message to specified members in a group, follow the instructions below:

- Call the `createXxxMessage` API (here, `Xxx` indicates the message type) to create a message (specify the message recipients via `receiverList`).
- Call the `sendMessage` API to send the message.

##### Examples

```
// Create a targeted group messagelet message = chat.createTextMessage({  to: 'test',  conversationType: TencentCloudChat.TYPES.CONV_GROUP,  payload: {    text: 'Hello world!'  },  receiverList: ['user0', 'user1']});// Send the messagelet promise = chat.sendMessage(message);promise.then(function(imResponse) {  // Message sent successfully  console.log(imResponse);}).catch(function(imError){  // The message failed to be sent  console.warn('sendMessage error:', imError);});
```

## Receiving a Targeted Group Message

By default, targeted group messages are excluded from the unread count of a group conversation.
A targeted group message can be received in the same way as an ordinary message.


---
*Source: [https://trtc.io/document/52716](https://trtc.io/document/52716)*
