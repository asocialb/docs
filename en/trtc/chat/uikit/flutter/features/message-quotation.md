# Message Quotation

## Description

In TencentCloudChatMessage's message list, you can reply to a specific previous message by quoting it. After replying, clicking the quoted message will jump to the original message, which will be highlighted.

There are two modes for quoting messages: "Message Quote" and "Message Reply".

- **Message Quote**: Only quotes the message. The text displayed in the message context menu is "Quote".
- **Message Reply**: Quotes and replies to the message, mentioning the message sender in group chats. The text displayed in the message context menu is "Reply".

## Effect Display

In the TencentCloudChatMessage message list, you can long press a message to experience the quote effect, as shown in the figure below:

Mobile

Desktop

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6dca900e39af11ef9c9c525400d5f8ef.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e2be95439b011efb958525400f69702.png)

## Feature Overview

### Quoting a Message

After you long press a message, a message toolbar will pop up on the message. Click the Quote button in the toolbar to quote the message.

Mobile

Desktop

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0c0e787e39af11ef94925254002693fd.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b70c129b39af11efbec9525400a9236a.png)

### Canceling Message Quotation

When a message is quoted but not yet sent, you can cancel message quotation by clicking the Close button behind the quote.

Mobile

Desktop

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3f51a98c39af11efbec9525400a9236a.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c77d679839af11ef9b60525400bdab9d.png)

### Viewing the Quoted Message

By clicking the citation content of a quoted message, you can locate the original message, which will be highlighted.

- When the quoted message is within the screen, clicking the citation content of the quoted message will only cause it to be highlighted.
- When the quoted message is not within the screen but is in the message list, clicking the citation content will cause the message list to automatically scroll to the original message, which will be highlighted.
- When the quoted message is neither within the screen nor in the message list, clicking the citation content will not cause the original message to be located or highlighted.

Mobile

Desktop

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/088fb37b39b111ef94925254002693fd.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d83de3f739af11efb89a52540075b605.png)

## Usage

This module is automatically enabled.

You can specify `enableReplyWithMention` in `TencentCloudChatMessageConfig` to choose which mode of message quoting to use.

Example:

```
TencentCloudChatMessageConfig(  enableReplyWithMention: ({String? groupID, String? userID, String? topicID}) => true,)
```

## Contact Us

If you have any questions about this feature, feel free to join the [Telegram Technical Group](https://t.me/+EPk6TMZEZMM5OGY1), and obtain reliable technical support from it.


---
*Source: [https://trtc.io/document/61683](https://trtc.io/document/61683)*
