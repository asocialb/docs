# Message Reactions

## Feature Overview

TUIKit supports emoji reactions, allowing users to respond to messages with emojis. This feature is built on top of the message editing capability.

> **Noteï¼**Emoji reactions are available only in the Pro edition plus and Enterprise edition packages. To use this feature, [purchase the Pro-plus edition or Enterprise edition](https://console.trtc.io/subscription/buy/chat?packType=pro).

## Feature Demo

### Send Emoji Reactions

Long-press a message to open the message menu, where you can select an emoji to react. Tap the button on the right to expand and view more emoji options. To add a reaction, click an emoji. If you have already reacted with that emoji, clicking it again will remove your reaction.

| Long-press message menu | More emojis |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4bee181f024711f191b4525400ecee81.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/95b8899b024611f18548525400380f7d.jpeg) |

### Displaying Emoji Reactions

All emoji reactions for a message are shown below that message, and everyone in the conversation can see them.

The number next to each emoji indicates how many users have reacted with that emoji. Clicking an emoji opens a details dialog.

In the details dialog, you can view the list of users who reacted with each emoji. If you have reacted, you can click to remove your own reaction.

| Emoji reaction display | Full list of users who reacted |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/95a4a95b024611f1b6b4525400370dda.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/90fa30f3024711f18e6252540073fd3b.jpeg) |

## Enable or Disable Emoji Reactions

The `config` parameter in `MessageList` lets you enable or disable emoji reactions for messages. By default, this feature is enabled (`true`). To turn it off, set the value to `false`. For details on using the `MessageList` component, see the [demo](https://github.com/Tencent-RTC/TUIKit_Flutter/blob/main/chat/uikit/lib/chat_page.dart).

```
MessageList(  config: ChatMessageListConfig(isSupportReaction: false),),
```


---
*Source: [https://trtc.io/document/52892](https://trtc.io/document/52892)*
