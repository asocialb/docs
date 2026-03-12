# Custom Message

TUIKit implements the sending and display for basic message types such as text, image, audio, video, and file messages by default. If these message types do not meet your needs, you can add custom message types.

## Basic Message Types

| Message Type | Renderings |
| --- | --- |
| Text message | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fcf03273b12e11ee9939525400461a83.png) |
| Image message | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ac20bec2b44611eeae9a525400c26da5.png) |
| Audio message | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/89ca08d4b44711eeae9a525400c26da5.png) |
| Video message | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0705b39cb12f11eeb2a1525400170219.png) |
| File message | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0afe02b6b12f11ee9fd6525400bb593a.png) |

## Custom message

If the basic message types do not meet your needs, you can customize the messages based on actual business needs.

There are several custom message styles built into TUIKit, as shown in the following figure:

| Custom message preset styles | Renderings |
| --- | --- |
| Hypertext message | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/977385f2b44211eeae9a525400c26da5.png) |
| Evaluation Message | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6b385bbab34d11eeae9a525400c26da5.png) |
| Order Message | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/34180b8eb44211eeb2a1525400170219.png) |

The following uses sending a custom hypertext message that can redirect to the browser as an example, assisting you to promptly understand the implementation process.

## Displaying a Custom Message

The hypertext custom message cell Element (XML) built into TUIKit is depicted in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3df05402b44611ee9fd6525400bb593a.png)

Custom messages and other common types of messages are received in the same way; all types of messages are monitored for access via `TUIStore.watch(StoreName.CHAT, { messageList: onMessageListUpdated })`.
The received custom messages are presented in the message list in different forms according to their respective specific type fields.
The following will explain how to display custom messages.

### Creating the display structure for the custom message

The display of custom messages is primarily accomplished by rendering `messageCustom` in the content area of the custom message type `messageBubble`.
You can add the display structure style you need for custom messages in the file at `src/TUIKit/components/TUIChat/message-list/message-elements/message-custom.vue`.
For instance, the following code demonstrates the display structure for a hypertext message:

```
<template v-else-if="isCustom.businessID === 'text_link'">  <div class="textLink">    <p>{{ isCustom.text }}</p>    <a :href="isCustom.link" target="view_window">      {{        TUITranslateService.t("message.custom.peekDetails>>")      }}    </a>  </div></template>
```

## Sending custom messages

You can send a custom message by calling the `TUIChatService.sendCustomMessage` method in the logical layer engine of TUIKit. For details, please refer to: [SendCustomMessage](https://web.sdk.qcloud.com/im/doc/chat-engine/en/ITUIChatService.html#sendCustomMessage).

Here are a few examples of sending built-in custom style messages in TUIKit:

#### **sendCustomMessage(options, sendMessageOptions) â {Promise.<any>}**

**example1: Sending custom evaluation message**

```
import { TUIChatService } from "@tencentcloud/chat-uikit-engine";let promise = TUIChatService.sendCustomMessage({  payload: {    data: JSON.stringify({      businessID: "evaluation",      version: 1,      score: 5,      comment: "so pretty!!!"    }),    description: "Evaluation of this service",    extension: "Evaluation of this service"  }});promise.catch((error) => {   ...});
```

**example2: Sending custom hypertext message**

```
import { TUIChatService } from "@tencentcloud/chat-uikit-engine";let promise = TUIChatService.sendCustomMessage({  payload: {    data: JSON.stringify({      businessID: "text_link",      text: "Welcome to Chat. Let's chat!",      link: "https://web.sdk.qcloud.com/im/demo/intl/index.html?scene=social"    }),    description: "",    extension: ""  }});promise.catch((error) => {   ...});
```

**Example 3: Sending custom order messages**

```
import { TUIChatService } from "@tencentcloud/chat-uikit-engine";let promise = TUIChatService.sendCustomMessage({  payload: {    data: JSON.stringify({      businessID: "order",      title: "Chat",      description: "Standard Edition",      price: "399 USD/month",      link: "https://buy.tencentcloud.com/avc",      imageUrl: "https://1302445663.vod2.myqcloud.com/cea47bfavodsgp1302445663/fd67ff345576678022395175485/2lCqNHbz5aYA.png",    }),    description: "",    extension: ""  }});promise.catch((error) => {   ...});
```

**Parameter description:**

| Name | Type | Optional type | Description |
| --- | --- | --- | --- |
| options | [SendMessageParams](https://web.sdk.qcloud.com/im/doc/chat-engine/en/SendMessageParams.html) | Required | Parameters related to custom messages |
| sendMessageOptions | [SendMessageOptions](https://web.sdk.qcloud.com/im/doc/chat-engine/en/SendMessageOptions.html) | Optional | Message sending options |

**Return values**

- `Promise.<any>`

## Contact us

Join the [Telegram technical exchange group](https://t.me/tencent_imsdk) or [WhatsApp discussion group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik), benefit from the support of professional engineers, and solve your toughest challenges.


---
*Source: [https://trtc.io/document/50042](https://trtc.io/document/50042)*
