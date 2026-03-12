# Typing Status

## Description

@tencentcloud/chat-uikit-vue support for the C2C conversation "Typing..." feature has been established since the v2.0.0

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ec8b80e61cc011ef9b9e5254002977b6.png)

Displaying the rule of "Typing...":

1. Activate the "Typing..." toggle (switched on by default).
2. In the current C2C conversation, if the other user has sent you a message within the last 30 seconds and is currently inputting text.

## Activating/Deactivating the state of the other party typing

The "Interlocutor is typing..." is default to be on, so there is no need for repetition in the following steps to enable it.

```
import { TUIStore, StoreName } from "@tencentcloud/chat-uikit-engine";// Enable the 'Typing' featureTUIStore.update(StoreName.APP, "enableTyping", true);// Disable the 'Typing' featureTUIStore.update(StoreName.APP, "enableTyping", false);
```

## Extended Information: How is 'typing ...' implemented within TUIKit?

> **Note:**The following content is merely supplementary reading material. The 'typing' feature is already included in TUIKit by default and does not require manual implementation.

##### 1. Sender: Monitors the start and end of input, sending an online message to the other party

In `TUIKit/components/TUIChat/message-input/index.vue`, you can send a message to start input status via `TUIChatService.enterTypingState()`, and deliver a message signalling the end of the input state through `TUIChatService.leaveTypingState().`

```
// TUIKit/components/TUIChat/message-input/index.vueimport { TUIChatService } from "@tencentcloud/chat-uikit-engine";const onTyping = (inputContentEmpty: boolean, inputBlur: boolean) => {  sendTyping(inputContentEmpty, inputBlur);};// TUIKit/components/TUIChat/utils/sendMessage.tsexport const sendTyping = (inputContentEmpty: boolean, inputBlur: boolean) => {  if (!inputContentEmpty && !inputBlur) {    TUIChatService.enterTypingState();  } else {    TUIChatService.leaveTypingState();  }};
```

##### 2. Receiver: Monitor input state of sender and display

In `TUIKit/components/TUIChat/chat-header/index.vue`, monitor the input state in the C2C conversation via listening to `typingStatus`.

```
TUIStore.watch(StoreName.CHAT, {  typingStatus: (status: boolean) => {    typingStatus.value = status;    switch (typingStatus.value) {      case true:        currentConversationName.value = "Typing...";        break;      case false:        currentConversationName.value =          currentConversation?.value?.getShowName();        break;    }  },});
```

## FAQs

### Why is there no typing indication from the other party after turning on the switch? What are the rules for displaying "Typing..."?

1. Turn on the "Typing" switch (it's on by default)
2. In the current C2C conversation, if the other user has sent you a message within the last 30 seconds and is currently inputting text.

## Contact us

Join the [Telegram technical exchange group](https://t.me/tencent_imsdk) or [WhatsApp discussion group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik), benefit from the support of professional engineers, and solve your toughest challenges.


---
*Source: [https://trtc.io/document/58663](https://trtc.io/document/58663)*
