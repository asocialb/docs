# Read Receipt

## Description

Read Receipt is used to notify the sender that "the recipient has read the sent message". When the recipient reads the message, a read message is reported, the backend system will generate a notification to inform the sender that the message has been viewed.

In instant messaging tools (WhatsApp, WeChat, etc.), when the recipient views the message, the sender will see a read receipt next to the message, such as a blue check mark or the word "read".

> **Note:**"Receipt" means "Reply Receipt", which represents a credential for confirming receipt. When you send a message and request a receipt, you are actually asking the other party "I want to confirm whether you have received and read my message". This confirmation is like a "receipt", proving that your message has been received.

Read receipts help ensure important messages has been viewed but can also cause psychological stress and privacy issues. Therefore, we support users to turn off the read receipt feature.

> **Note:**This feature is only supported by the Pro edition  or Pro Plus edition or Enterprise edition. Please [purchase the Pro edition  or Pro Plus edition or Enterprise edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it."Group Chat Message Read Receipt" is supported from TUIKit [6.2.2363](https://www.tencentcloud.com/document/product/1047/34282#6.2.2363-.402022.04.29---.E5.A2.9E.E5.BC.BA.E7.89.88) version and later."One-to-one Chat Message Read Receipt" is supported from TUIKit [6.3.2609](https://www.tencentcloud.com/document/product/1047/34282#6.3.2619-.402022.06.29---.E5.A2.9E.E5.BC.BA.E7.89.88) version and later.

## Effect

### One-to-one Chat

Indicated by âï¸ or highlighted âï¸âï¸ on the message

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0f592ff6135111efa09b525400762795.png)

### Group Chat

Message reading status is indicated on the message:

- When no one has read it, âï¸ is displayed;
- When some chat members have read it, gray âï¸âï¸ is displayed;
- When everyone has read it, highlighted âï¸âï¸ is displayed.

#### Message List

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3a7206fb135111efa2935254005ac0ca.png)

#### Read Receipt Details

Click the read status to enter the read receipt details page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/474506fe135111efaa1c525400f65c2a.png)

## Enabling Message Read Receipt

In the `TUIChat` component, within the `TUIChatConfig` file, a switch for the "Message Read Receipt" feature, named `msgNeedReadReceipt`, is provided. Its type is BOOL, with a default value of `NO`.

If you want to enable the "Message Read Receipt" feature, please first activate the Pro edition  or Pro Plus edition or Enterprise edition and then change the default value of `msgNeedReadReceipt` to `YES`, or call the following method to enable it before the chat page is initialized.

Swift

Objective-C

```
TUIChatConfig.shared.msgNeedReadReceipt = true
```

```
TUIChatConfig.defaultConfig.msgNeedReadReceipt = YES;
```

## FAQs

**Error: The usage of this API is not supported by the package. Please upgrade to the Pro edition  or Pro Plus edition or Enterprise edition.**

The "Message Read Receipt" feature is only supported by the premium package. This error message indicates that your current package does not support this capability. Please log in to the [Chat purchase page](https://trtc.io/buy/chat) to activate the Pro edition  or Pro Plus edition or Enterprise edition for experience.


---
*Source: [https://trtc.io/document/59440](https://trtc.io/document/59440)*
