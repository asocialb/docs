# User Online Status

## Description

TUIKit supports displaying user online status starting from version [6.5.2803](https://www.tencentcloud.com/document/product/1047/34282?lang=en&pg=#6.5.2803-.402022.07.15---enhanced-edition).

When "Show User Online Status" is enabled, user online status will be displayed on each user's avatar in the chat list and contact list. A green circle indicates online; absence of the green circle indicates offline.

When "Show User Online Status" is disabled, user online status will not be displayed.

> **Note:**The "User Online Status" feature is only supported by the [Pro edition ãPro Plus edition ãEnterprise edition](https://www.tencentcloud.com/document/product/1047/34350?lang=en&pg=). Please make sure that the premium package is activated before using this feature.The "User Online Status" feature requires turning on the user status switch in the [Chat console](https://console.trtc.io/). Please make sure that the switch is turned on before using this feature.Only friends in the conversation list support displaying their online status. If you need to support non-friends, you  should call the API to subscribe to non-friends' status and implement the UI yourself. API reference:[User Status](https://trtc.io/document/49562?platform=ios%20and%20macos&product=chat&menulabel=coresdk#change-in-a-non-friend-user&).

## Enabling User Online Status

In the `TUICore` component, within the `TUIConfig` file, a switch for the "User Online Status" feature, named `displayOnlineStatusIcon`, is provided. Its type is BOOL, with the default value of NO.

To enable the chat list to display user online status, first subscribe to the premium package, then turn on the user status feature switch in the [Chat console](https://console.trtc.io/), and change the default value of `displayOnlineStatusIcon` to `YES`, or call the following method before initializing the chat page.

Swift

Objective-C

```
TUIConfig.default().displayOnlineStatusIcon = true
```

```
[TUIConfig defaultConfig].displayOnlineStatusIcon = YES;
```

## Display Effect

### Chat List

| Enabling "Show User Online Status" | Disabling "Show User Online Status" |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12b3b288dc3711eeb1c5525400c4ffd8.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12d3095cdc3711ee8c73525400ea3514.jpeg) |

### Contacts List

| Enabling "Show User Online Status" | Disabling "Show User Online Status" |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12c8274adc3711eeb1c5525400c4ffd8.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12b7a8f1dc3711eea122525400bb593a.jpeg) |

## FAQs

- **When the Subscription/Unsubscription API is called, the API returns error code "72001".**

Error code 72001 indicates that the corresponding capability has not been activated in the console. Please log in to the [Chat console](https://console.trtc.io/) and enable the corresponding feature switch.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0a9d068e135811efa2935254005ac0ca.png)

- **Error: The package does not support the use of this API, please upgrade to the premium package.**

The "User Online Status" feature is only supported by the premium package. This error message indicates that your current package does not support this feature. Please log in to the [Chat purchase page](https://console.trtc.io/buy/active) to activate the premium package and experience it.

## Exchange and Feedback

Join the [Telegram technical exchange group](https://t.me/+1doS9AUBmndhNGNl) or [WhatsApp discussion group](https://chat.whatsapp.com/Gfbxk7rQBqc8Rz4pzzP27A), benefit from the support of professional engineers, and solve your toughest challenges.


---
*Source: [https://trtc.io/document/59436](https://trtc.io/document/59436)*
