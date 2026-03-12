# Forward Messages

## Feature Overview

You can merge and forward messages in the following steps:

1. Create a merged message based on the list of original messages.
2. Send the merged message to the receiver.
3. The receiver receives the merged message and parses the list of original messages.

## UI Display

| Merge and Forward | Display of Merged Message | Click Merged Message to Download Message List for Display |
| --- | --- | --- |
|  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8d2e790c167111eea6e9525400cea498.png)  | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e067ecd4167111eea27e525400c56988.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f9d1af98167111eea27e525400c56988.png) |

## Creating a Merged Message

This API is used to create a merged message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send a merged message.

> **Note:**Unable to merge messages that failed to be sent. If the message list contains a message that failed to be sent, the API will report an error.

##### **API**

```
chat.createMergerMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values: `TencentCloudChat.TYPES.CONV_C2C` (one-to-one conversation)`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values: `TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| messageList | Array | Merged message list |
| title | String | Title of merged messages, for example, "Chat History of the Talent Center in the Greater Bay Area" |
| abstractList | String | Digest list. You can set digest information in different formats for different message types, for example, in the `sender:text` format for a text message, in the `sender:[image]` format for an image message, or in the `sender:[file]` format for a file message. |
| compatibleText | String | Compatibility text. If the early SDK version does not support the merged message, the user will receive a text message with the content `${compatibleText}` by default. This field is required. |

##### **Return value**

`Message`

##### **Examples**

```
// 1. Forward group messages to a one-to-one conversation.// `message1`, `message2`, and `message3` are group messages.let mergerMessage = chat.createMergerMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: {    messageList: [message1, message2, message3],    title: 'Chat History of the Talent Center in the Greater Bay Area',    abstractList: ['allen: 666', 'iris: [Image]', 'linda: [File]'],    compatibleText: 'Upgrade your Chat SDK to v2.10.1 or later to view this message.'  },  // cloudCustomData: 'your cloud custom data'});// 2. Send the message.let promise = chat.sendMessage(mergerMessage);promise.then(function(imResponse) {  // Message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

## Downloading a Merged Message

This API is used to download a merged message. When the merged message sent by the sender is large in size, the SDK will store it in the cloud, and the message receiver needs to download it from the cloud before viewing it.

##### **API**

```
chat.downloadMergerMessage(message);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| message | Message | Message instance |

##### **Return value**

`Promise`

##### **Examples**

```
// If `downloadKey` exists, the received merged message is stored in the cloud// and needs to be downloaded first.if (message.type === TencentCloudChat.TYPES.MSG_MERGER && message.payload.downloadKey !== '') {  let promise = chat.downloadMergerMessage(message);  promise.then(function(imResponse) {    // After the download is successful    // the SDK will update information such as `message.payload.messageList`.    console.log(imResponse.data);  }).catch(function(imError) {    // Download failed    console.warn('downloadMergerMessage error:', imError);  });}
```

## Forwarding Messages One by One

To forward a single message, create a message identical to the original message through the `createForwardMessage` API first, and then call the `sendMessage` API to send the message.

##### **API**

```
chat.createForwardMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C` (one-to-one conversation)`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL `(default)`TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Message | Message instance |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

##### **Return value**

`Message`

##### **Examples**

```
let forwardMessage = chat.createForwardMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: message, // Message instance for the received or sent message  // cloudCustomData: 'your cloud custom data'});// 2. Send the message.let promise = chat.sendMessage(forwardMessage);promise.then(function(imResponse) {  // Message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```


---
*Source: [https://trtc.io/document/48874](https://trtc.io/document/48874)*
