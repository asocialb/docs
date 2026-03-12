# Read Receipt

## Description

Read Receipt is used to notify the sender that "the recipient has read the sent message". When the recipient reads the message, a read message is reported, the backend system will generate a notification to inform the sender that the message has been viewed.

In instant messaging tools (WhatsApp, WeChat, etc.), when the recipient views the message, the sender will see a read receipt next to the message, such as a blue check mark or the word "read".

> **Note:**"Receipt" means "Reply Receipt", which represents a credential for confirming receipt. When you send a message and request a receipt, you are actually asking the other party "I want to confirm whether you have received and read my message". This confirmation is like a "receipt", proving that your message has been received.

Read receipts help ensure important messages has been viewed but can also cause psychological stress and privacy issues. Therefore, we support users to turn off the read receipt feature.

> **Note:**This feature is only supported by the Pro edition ãPro Plus edition ãEnterprise edition. Please [purchase the Pro edition ãPro Plus edition ãEnterprise edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it."Group Chat Message Read Receipt" is supported from TUIKit [6.2.2363](https://www.tencentcloud.com/en/document/product/1047/34282#6.2.2363-.402022.04.29---enhanced-edition) version and later."One-to-one Chat Message Read Receipt" is supported from TUIKit [6.3.2609](https://www.tencentcloud.com/en/document/product/1047/34282#6.3.2609-.402022.06.16---enhanced-edition) version and later.

## Effect

### One-to-one Chat Message Read Receipt

Indicated by âï¸ or highlighted âï¸âï¸ on the message

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8cda7c6d129411efbf645254007bbd8c.png)

### Group Chat Message Read Receipt

Message reading status is indicated on the message:

- When no one has read it, âï¸ is displayed;
- When some chat members have read it, gray âï¸âï¸ is displayed;
- When everyone has read it, highlighted âï¸âï¸ is displayed.

#### Message List

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b932c79c129411efa09b525400762795.png)

#### Read Receipt Details

Click the read status to enter the read receipt details page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c6582e52129411ef89cc5254002fd0a8.png)

## Enabling Message Read Receipt

In the `TUIChat` component, within the [GeneralConfig.java](https://github.com/TencentCloud/chat-uikit-android/blob/main/TUIKit/TUIChat/tuichat/src/main/java/com/tencent/qcloud/tuikit/tuichat/config/GeneralConfig.java) file, a switch for the "Message Read Receipt" feature, named `msgNeedReadReceipt`, is provided. Its type is boolean, with a default value of `false`.

```
public class GeneralConfig {    private boolean msgNeedReadReceipt = false;}
```

If you want to enable the "Message Read Receipt" feature, please first activate the Pro edition ãPro Plus edition ãEnterprise edition and then change the default value of `msgNeedReadReceipt` to `true`, or call the following method to enable it before the chat page is initialized.

```
TUIChatConfigs.getConfigs().getGeneralConfig().setMsgNeedReadReceipt(true);
```

## FAQs

- **Error: The usage of this API is not supported by the package. Please upgrade to the Pro edition ãPro Plus edition ãEnterprise edition.**

The "Message Read Receipt" feature is only supported by the premium package. This error message indicates that your current package does not support this capability. Please log in to the [Chat purchase page](https://trtc.io/buy/chat) to activate the Pro edition ãPro Plus edition ãEnterprise edition for experience.


---
*Source: [https://trtc.io/document/59439](https://trtc.io/document/59439)*
