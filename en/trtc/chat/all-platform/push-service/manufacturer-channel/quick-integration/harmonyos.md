# HarmonyOS

## Operation Steps

### Step 1: TIMPush Integration

```
// For the version number "VERSION", please refer to the changelog for configuration.// Configure the integration package in oh-package.json5dependencies: {    "@tencentcloud/timpush": "^VERSION",    "@tencentcloud/imsdk": "^VERSION",}
```

### Step 2: Register for Push Services

Call the API to push after registration is successful, and you can receive offline push notifications.

```
import { TIMPushListener, TIMPushManager, TIMPushMessage } from '@tencentcloud/timpush';TIMPushManager.getInstance()  .registerPush(context, your sdkAppId, "client secret", Chat console certificate ID)  .then((result) => {    HiLog("registerPush success:", result.message);  })  .catch((error: Error) => {    HiLog("registerPush failed", error.code, error.message);  })
```

### Step 3: Message Delivery Statistics Configuration

If you need statistics on reach data, complete the configuration as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/059565fc7f2011f0b3fe525400bf7822.png)

Receipt address: `https://api.im.qcloud.com/v3/offline_push_report/harmony`

### Step 4: Sending Push Notifications

For detailed API instructions, see [RESTful APIs - Initiate Push to All Users/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).

### Step 5: Parsing Offline Push Messages

After receiving the push message and clicking the notification, the component will Webhook the click event and offline message pass-through.

> **Note:**Register the callback timing in the oncreate() function of the application [UIAbility](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/uiability-lifecycle).Console configuration click subsequent actions with the following configuration, select **open specified in-app page**, do not modify use default values.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f199a167da111f0bda35254007c27c5.png)

```
let pushListener: TIMPushListener = {  onNotificationClicked: (data) => {    HiLog("onNotificationClicked", data);  }}TIMPushManager.getInstance().addPushListener(pushListener);
```

Congratulations on completing the Push Plugin access. Remind you: **After trial or purchase expiry, the Push Plugin will automatically stop providing push service (including offline push for regular messages, Tag Push, etc.)**. To avoid affecting normal business operation, please [proceed to purchase](https://buy.tencentcloud.com/avc?activeId=plugin&position=20012840&regionId=9) or [renew](https://buy.tencentcloud.com/avc?activeId=plugin&position=20012840&regionId=9) in advance.

> **Note:**Integration completed but not receiving push notifications? Please first use the [troubleshooting tool](https://www.tencentcloud.com/document/product/1047/60541) to check the reason. To view push metrics data, use [data statistics](https://www.tencentcloud.com/document/product/1047/60540) for querying.For push notification feature to all users/Tag Push, please refer to: [RESTful APIs - Initiate Push to All Users/Tag Push](https://www.tencentcloud.com/document/product/1047/60561).


---
*Source: [https://trtc.io/document/72701](https://trtc.io/document/72701)*
