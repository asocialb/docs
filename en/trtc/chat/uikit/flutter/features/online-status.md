# Online Status

## Description

UIKit supports displaying user online status in the conversation list and contact list.

When "Show User Online Status" is enabled, user online status will be displayed on each user's avatar in the chat list and contact list.

When "Show User Online Status" is disabled, user online status will not be displayed.

> **Note:**This feature is only supported by the Pro edition ãPro Plus edition ãEnterprise edition. Please [purchase the Pro edition ãPro Plus edition ãEnterprise edition](https://trtc.io/buy/chat) to use it.Please enable the user status switch in the [Chat Console](https://console.trtc.io/). Ensure the switch is turned on before use.

## Display Effect

### Conversation List

| Enable "Show User Online Status" | Disable "Show User Online Status" |
| --- | --- |
|  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/669a1843ed1511ef840e52540044a08e.jpg) |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/68a70813ed1511ef93475254005ef0f7.jpg) |

### Contacts List

| Enable "Show User Online Status" | Disable "Show User Online Status" |
| --- | --- |
|  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7731e24fed1511efa1f2525400bf7822.jpg) |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7887e288ed1511ef93475254005ef0f7.jpg) |

## Feature Overview

When initializing UIKit, config `useUserOnlineStatus` in `TencentCloudChatUserConfig` to enable this feature.

```
final bool initRes = await TencentCloudChat.controller.initUIKit(  config: TencentCloudChatConfig(    userConfig: TencentCloudChatUserConfig(      useUserOnlineStatus: true,      // ... other UIKit configurations    ),  ),);
```

## FAQs

- **When calling the Subscription/Unsubscription API, the interface prompts "Error Code 72001".**

Error Code 72001 indicates that the corresponding capability is not enabled in the Console. Please log in to the [Chat Console](https://console.trtc.io/) to enable the corresponding feature toggle.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bf08ba1c855511ef8829525400fdb830.png)

- **Error: The package bundle does not support the use of this interface. Please upgrade to the advanced package.**

This feature is only supported in the Pro edition ãPro Plus edition ãEnterprise edition. The error message indicates that your current package does not support this capability. Please log in to the [Chat Purchase Page](https://console.trtc.io/buy/active) to activate the Premium Edition and experience it.

## Contact Us

If you have any questions during the access and usage process, please contact us through the following methods.

- [Telegram Group](https://t.me/+1doS9AUBmndhNGNl)
- [WhatsApp Group](https://chat.whatsapp.com/Gfbxk7rQBqc8Rz4pzzP27A)


---
*Source: [https://trtc.io/document/52884](https://trtc.io/document/52884)*
