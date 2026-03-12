# Reactions

## Description

Starting from version 7.8, the emoji response feature is provided by the TUIEmojiPlugin plugin.

- If you do not need this feature, simply skip integrating the plugin. In this case, when you long press a text message, the emoji response module will not be displayed.
- If you need this feature, you need to integrate TUIChat and TUIEmojiPlugin. Please refer to ["Integrating Basic Features"](https://www.tencentcloud.com/document/product/1047/50056?lang=en&pg=) for integration methods. After integration, no further settings are required. When you long press a text message, the emoji response button will be displayed automatically.

> **Note:**The emoji response feature is only supported by the Pro Plus edition ãEnterprise edition, please [purchase the Pro Plus edition ãEnterprise edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use.

## Effect

### Sending Emoji Response

After emoji response is integrated, there will be an emoji selection area above the long press menu for messages. You can click the right button to expand the area to view more emojis. Clicking on an emoji will respond to the message with that emoji. If you have already responded to the message with an emoji, clicking on the emoji will cancel the response.

| Long press menu for messages | More emojis |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1a23fa48167c11efb8ef5254002fd0a8.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a0e5ff89dc7211ee8c73525400ea3514.jpeg) |

If emoji response is not integrated, the emoji response entry will not be displayed above the long press popup for messages, as shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2852d5a7167c11efb6495254005ac0ca.png)

### Displaying Emoji Response

All responses received for a message will be displayed below the message, and all members in the chat can see them. Below the message, the responding emoji and the nickname of the chat member who responded with the emoji will be displayed. Click on the emoji or nickname, and you will see the emoji response details for that message. In the emoji response details interface, clicking on the emoji response you sent can quickly recall the emoji response.

| Emoji Response Preview | Emoji Response Details |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3528f375167c11ef9c015254002977b6.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/37309230167c11efa66f525400f65c2a.png) |


---
*Source: [https://trtc.io/document/59442](https://trtc.io/document/59442)*
