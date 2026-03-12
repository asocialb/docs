# Read Receipt

## Description

After enabling the "Message Read Receipt" feature, the TUIChat component will monitor message scrolling. When unread messages appear within the recipient's chat window's visible zone, it will automatically trigger the sending of read receipts to the sender, meticulously tracking the read status of each message.

> **Noteï¼**Beginning with version v2.0.0, TUIKit supports message read receipts for both group chats and one-to-one chats. **This feature is exclusive to the Pro edition ãPro Plus edition ãEnterprise editionï¼please**[**purchase the Pro edition ãPro Plus edition or Enterprise edition**](https://console.trtc.io/subscription/buy/chat?packType=pro)**to use.**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a33e8abe1cc011efb7495254005ac0ca.png)

## How to Enable Message Read Receipt

### Specifying a Group Type that Supports Read Receipts

For group message read receipts, first, proceed to the [Chat Console > Chat > Configuration > Group Configuration > Read receipts for group messages](https://console.trtc.io/chat/qun-setting) to set the group type that supports read receipt messages.

> **Note:**Live Chat Groups (AVChatRoom) or Communities (Community) **do not support** the read receipt feature.

### User-side Control for Enabling\\Disabling Read Receipt

> **Note:**After configuring the read receipt for group chats in the console, the read receipt capability is enabled by default. Unless specifically required, there is no need for user-side switch operation.

The user-side also supports manual enabling\\disabling of the read receipt capability (which is enabled by default). However, if it is disabled, others cannot see whether they have read (i.e., read receipts will not be sent), likewise one cannot see whether others have read their messages (will not display their sent message's read status).

After successful Sign in, use the `TUIUserService.switchMessageReadStatus(isDisplay: boolean)` Api to control this switch.

```
import { TUIUserService } from "@tencentcloud/chat-uikit-engine";TUIUserService.switchMessageReadStatus(true);  // EnableTUIUserService.switchMessageReadStatus(false); // Disable
```

## Supplementary Materials

> **Note:**The below content is only for supporting reading material. The read receipt function is already included in the flagship TUIKit. There is no need for user-initiated application.

### ReadReceipt Rules for Group and Direct Messaging

After activating the read receipt function, the `Message`'s `needReadReceipt` field is preset as `true`, when the message is in the visible position of the other party's message list, a read receipt will be sent. However, one should be aware that the rules for direct messages and group messages differ before and after the activation of the read receipts function.

#### Group Messaging Read Receipts Rules

1. Before activating the read receipt function in group messages:

Not displaying read status.

2. After group chat enables read receipts:

Get the read count and unread count based on the `Message`'s `readReceiptInfo`.

  - For read count of 0: display "Unread".
  - For unread count of 0: display "All read".
  - Otherwise, display "x people read", where x is the read count.

#### Read receipt rules for one-to-one chats

1. Before enabling read receipts in one-to-one chats:

Display the read status, but it is a full read, when the user clicks to enter the conversation, regardless of whether they see the message, all unread messages will be marked as read. Judge whether the message is read or unread based on the `Message`'s `isPeerRead`.

2. After enabling read receipts in one-to-one chats:

Based on the `Message` singular `readReceiptInfo.isReceiptPeerRead` field (boolean) access for read status, it can be determined whether it is in a state of "read" or "unread".

## FAQs

### 1. Error: The usage of this API is not supported by the package. Please upgrade to the premium version.

The "Group Message Read Receipt" feature is only supported by the flagship package. The error message means your current package does not support this capability.

### 2. How to disable the read feature?

Please refer to the content of [User-side Control for Disabling Read Receipt](https://www.tencentcloud.com/document/product/1047/58661#f81aa831-f9a8-40a1-a581-f828f4393361) of this document, use `TUIUserService.switchMessageReadStatus(isDisplay: boolean)` to turn off the read function.

```
import { TUIUserService } from "@tencentcloud/chat-uikit-engine";TUIUserService.switchMessageReadStatus(false);
```

## Exchange and Feedback

Join the [Telegram technical exchange group](https://t.me/+1doS9AUBmndhNGNl) or [WhatsApp discussion group](https://chat.whatsapp.com/Gfbxk7rQBqc8Rz4pzzP27A), enjoy the support of professional engineers, and resolve your issues.


---
*Source: [https://trtc.io/document/58661](https://trtc.io/document/58661)*
