# Mentions

## Feature Overview

The sender listens for the characters in the input box. When the user enters @, the group member selection UI will pop up. After the target group members are selected, the message will be displayed in the input box in the format of `"@A @B @C......"`, which can be further edited before sent.

In the group chat list of the receiver's conversation UI, the identifier `"someone@me"` or `"@all"` will be displayed to remind the user that the user was mentioned by someone in the group chat.

> **Note** Currently, only text @ messages are supported.

## UI Display

| Listening for the @ character for group member selection | Editing and sending the group @ message | Receiving the group @ message |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0b0ddb759c1c11ef820f525400d5f8ef.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0b1630339c1c11ef992f52540075b605.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0b112f259c1c11efa0b3525400bdab9d.jpeg) |

Figure 1: When the @ character is detected in the input box on the chat UI, the user is redirected to the group member selection UI to select the target group members.

Figure 2: After selecting the target group members, the user goes back to the chat UI to edit and send the group @ message.

Figure 3: If a user is mentioned, the user receives the conversation update, and the "someone@me" information is displayed in the conversation `Cell`.

## Sending a Group @mention Message

1. The sender listens for the text input box on the chat UI and launches the group member selection UI. After group members are selected, the ID and nickname information of the members is called back.
2. The sender calls the `createTextAtMessage` API to create a group @ message.
3. The sender calls `sendMessage`to send the created @ message object.

##### API

```
chat.createTextAtMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `groupID` of the message receiver |
| conversationType | String | Conversation type, which must be `TencentCloudChat.TYPES.CONV_GROUP` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| text | String | Message text content |
| atUserList | Array.<String> | The list of users who need to be @mentioned. If you need to @ALL, please pass in `TencentCloudChat.TYPES.MSG_AT_ALL`. For example, suppose this text message wants to @mention denny and lucy, while also wanting to @mention everyone, `atUserList` would be passed as `['denny', 'lucy', TencentCloudChat.TYPES.MSG_AT_ALL]`. |

##### **Return value**

`Promise`

##### **Examples**

```
let message = chat.createTextAtMessage({  to: 'group1',  conversationType: TencentCloudChat.TYPES.CONV_GROUP,  payload: {    text: '@denny @lucy Dinner gathering tonight, reply with 1 if you are coming.',    atUserList: ['denny', 'lucy', TencentCloudChat.TYPES.MSG_AT_ALL] // 'denny' 'lucy' are both userID  },  // cloudCustomData: 'your cloud custom data'});let promise = chat.sendMessage(message);promise.then(function(imResponse) {  console.log(imResponse);}).catch(function(imError) {  console.warn('sendMessage error:', imError);});
```


---
*Source: [https://trtc.io/document/48889](https://trtc.io/document/48889)*
