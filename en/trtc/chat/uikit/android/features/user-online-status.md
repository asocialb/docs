# User Online Status 

## Description

TUIKit supports displaying user online status starting from version [6.5.2803](https://www.tencentcloud.com/document/product/1047/34282?lang=en&pg=#6.5.2803-.402022.07.15---enhanced-edition).

When "Show User Online Status" is enabled, user online status will be displayed on each user's avatar in the chat list and contact list. A green circle indicates online; absence of the green circle indicates offline.

When "Show User Online Status" is disabled, user online status will not be displayed.

> **Note:**The "User Online Status" feature is only supported by the [Pro edition ãPro Plus edition ãEnterprise edition](https://www.tencentcloud.com/document/product/1047/34350?lang=en&pg=). Please make sure that the Pro  ãPro Plus or Enterprise package is activated before using this feature.The "User Online Status" feature requires turning on the user status switch in the [Chat console](https://console.trtc.io/). Please make sure that the switch is turned on before using this feature.Only friends in the conversation list support displaying their online status. If you need to support non-friends, you  should call the API to subscribe to non-friends' status and implement the UI yourself. API reference: [User Status](https://trtc.io/document/49562?platform=android&product=chat&menulabel=coresdk#change-in-a-non-friend-user&).

## Enabling User Online Status in Chat List

In the `TUIConversation` component, within the [TUIConversationConfig.java](https://github.com/TencentCloud/chat-uikit-android/blob/main/TUIKit/TUIConversation/tuiconversation/src/main/java/com/tencent/qcloud/tuikit/tuiconversation/config/TUIConversationConfig.java) file, a switch for the "User Online Status" feature, named **isShowUserStatus**, is provided. Its type is boolean, with the default value of false.

```
public class TUIConversationConfig {    private boolean isShowUserStatus;}
```

To enable the chat list to display user online status, first subscribe to the Pro  ãPro Plus or Enterprise package, then turn on the user status feature switch in the [Chat console](https://console.trtc.io/), and change the default value of **isShowUserStatus** to `true`, or call the following method before initializing the chat page.

```
TUIConversationConfig.getInstance().setShowUserStatus(true);
```

### Chat List Effect

| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0d1f84db129c11efa2935254005ac0ca.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/21324f1a129c11efaa1c525400f65c2a.png) |
| --- | --- |

## Enabling User Online Status in Contacts List

In the `TUIContact` component, within the [TUIContactConfig.java](https://github.com/TencentCloud/chat-uikit-android/blob/main/TUIKit/TUIContact/tuicontact/src/main/java/com/tencent/qcloud/tuikit/tuicontact/config/TUIContactConfig.java) file, a switch for the "User Online Status" feature, named **isShowUserStatus**, is provided. Its type is boolean, with the default value of false.

```
public class TUIContactConfig {    private boolean isShowUserStatus;}
```

To enable the contacts list to display user online status, first subscribe to the Pro  ãPro Plus or Enterprise package, then turn on the user status feature switch in the [Chat console](https://console.trtc.io/), and change the default value of **isShowUserStatus** to `true`, or call the following method before initializing the contacts list page.

```
TUIContactConfig.getInstance().setShowUserStatus(true);
```

### Contacts List Effect

| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f96b167a129c11efaa1c525400f65c2a.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0e99b4a8129d11efbf645254007bbd8c.png) |
| --- | --- |

## FAQs

### When the Subscription/Unsubscription API is called, the API returns error code "72001".

Error code 72001 indicates that the corresponding capability has not been activated in the console. Please log in to the [Chat console](https://console.trtc.io/) and enable the corresponding feature switch.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6376f3ff129e11ef89cc5254002fd0a8.png)

### Error: The package does not support the use of this API. Please upgrade to the Pro  ãPro Plus or Enterprise package.

The "User Online Status" feature is only supported by the Pro  ãPro Plus or Enterprise package. This error message indicates that your current package does not support this feature. Please log in to the [Chat purchase page](https://console.trtc.io/buy/active) to activate the Pro  ãPro Plus or Enterprise package and experience it.

## Exchange and Feedback

Join the [Telegram technical exchange group](https://t.me/+1doS9AUBmndhNGNl) or [WhatsApp discussion group](https://chat.whatsapp.com/Gfbxk7rQBqc8Rz4pzzP27A), benefit from the support of professional engineers, and solve your toughest challenges.


---
*Source: [https://trtc.io/document/59435](https://trtc.io/document/59435)*
