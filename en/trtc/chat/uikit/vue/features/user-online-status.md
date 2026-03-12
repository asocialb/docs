# User Online Status

## Description

@tencentcloud/chat-uikit-vue starting from the v2.0.0 version, has started to support the "User Online Status" featureã

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/40f030cd1cc111efb7495254005ac0ca.png)

> **Note:**The User Online Status feature **is only supported by the** Pro edition ãPro Plus edition ãEnterprise edition, please confirm before use.The User Online Status feature needs to be activated via the [Chat Console](https://console.trtc.io/chat/login-message), please confirm before use.

## Enable/Disable User Online Status

"**User Online Status" is switched off by default**, you need to follow the steps below to enable it:

```
import { TUIUserService } from "@tencentcloud/chat-uikit-engine";// open user online status// This interface is only valid when called after successful loginTUIUserService.switchUserStatus({ displayOnlineStatus: true });// close user online status// This interface is only valid when called after successful login TUIUserService.switchUserStatus({ displayOnlineStatus: false });
```

> **Note:**The above interface `TUIUserService.switchUserStatus`**is only effective after a successful sign in**, please make sure to call this interface only after signing in.Here is the example code to enable user online status by calling this interface after signing in:

```
import { TUILogin } from "@tencentcloud/tui-core";import { TUIUserService } from "@tencentcloud/chat-uikit-engine";TUILogin.login(loginInfo).then((res: any) => {  TUIUserService.switchUserStatus({ displayOnlineStatus: true });});
```

## Supplementary Information: How does TUIKit internally achieve the "user online status" feature?

> **Note:**The following content is only for the purpose of auxiliary reading. The user online status feature is already included in TUIKit by default, negating the need for manual implementation by the user.

Both the `TUIConversion` and `TUIContact` components support the "User Online Status" feature. The `TUIContact` is given as an example for discussion below:

##### 1. Monitor User Online Status List Changes

In `TUIKit/components/TUIContact/contact-list/index.vue`, monitor changes in the user online status list:

```
TUIStore.watch(StoreName.USER, {  ...  displayOnlineStatus: (status: boolean) => {    displayOnlineStatus.value = status;  },  userStatusList: (list: Map<string, IUserStatus>) => {    list?.size && (userOnlineStatusMap.value = Object.fromEntries(list?.entries()));  },});
```

##### 2. Display of User Online Status

In `TUIKit/components/TUIContact/contact-list/contact-list-item/index.vue`:

**2.1 Interpretation of the user's online status:**

```
function getOnlineStatus(): boolean {  return (    props.displayOnlineStatus &&    props.userOnlineStatusMap &&    props.item?.userID &&    props.userOnlineStatusMap?.[props.item.userID]?.statusType === TUIChatEngine.TYPES.USER_STATUS_ONLINE   );};
```

**2.2 Display the online status of the user:**

```
<div  v-if="props.displayOnlineStatus"  :class="{    'online-status': true,    'online-status-online': isOnline,    'online-status-offline': !isOnline  }"></div>
```

## FAQs

### When invoking the Subscription/Cancel Subscription API, the interface prompts the error code "72001"

The error code 72001 indicates that the corresponding capability is not enabled on the console, please sign in to the [Chat Console](https://console.trtc.io/chat/login-message) to activate the corresponding functional switch.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ce29129a126d11ef9fa952540019e87e.png)

### Error: The package does not support the usage of this API, please upgrade to the  Pro edition ãPro Plus edition ãEnterprise edition

The "User Online Status" feature is only supported by the Pro edition ãPro Plus edition or Enterprise edition. This error message indicates that your current package does not support this capability.

## Contact us

Join the [Telegram technical exchange group](https://t.me/tencent_imsdk) or [WhatsApp discussion group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik), benefit from the support of professional engineers, and solve your toughest challenges.


---
*Source: [https://trtc.io/document/58651](https://trtc.io/document/58651)*
