# Android

## Operation step

### Step 1. Register your app with vendor push platforms

Offline push requires registering your app with each vendor's push platform to obtain parameters such as AppID and AppKey to enable the offline push feature. Currently supported mobile manufacturers are: [Mi](https://dev.mi.com/console/doc/detail?pId=68), [Huawei](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/service-introduction-0000001050040060), [HONOR](https://developer.hihonor.com/cn/kitdoc?category=&kitId=11002), [OPPO](https://open.oppomobile.com/wiki/doc#id=10195), [vivo](https://dev.vivo.com.cn/documentCenter/doc/281), [Meizu](https://open.flyme.cn/service/3), [Google FCM](https://console.firebase.google.com/u/0/).

### Step 2. Create resources in the Chat console

Log in to Tencent Cloud [Chat Console](https://console.trtc.io/chat/push-plugin-push-identifier), then in the **Push Management** > **Access Settings** feature section, add each vendor's push certificate, and configure the AppID, AppKey, AppSecret, and other parameters obtained in Step 1 to the added push certificate.

Explanation of the **Subsequent Actions** option:

- Open Application: Clicking the notification bar launches the app, by default starting the app's Launcher interface;
- Open Web Page: Clicking the notification bar will redirect to the configured web link;
- Open the specified interface within the app: clicking the notification bar will redirect the interface based on the configured self Definition, see [Custom Redirect on Click](https://www.tencentcloud.com/zh/document/product/1047/60575).

Mi

Huawei

OPPO

vivo

Meizu

HONOR

Google FCM

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed00de9bb2d511ef96e55254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed287f2eb2d511ef8b1b525400f69702.png) |

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed2c3b1eb2d511ef970f525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed2167b8b2d511efbfb3525400bdab9d.png) **Note:**Client ID corresponds to AppID, Client Secret corresponds to AppSecret. |

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed40e2e8b2d511ef9d2952540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed211544b2d511efa2e952540075b605.png) |

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed46961eb2d511efa2e952540075b605.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed310539b2d511efbfb3525400bdab9d.png) |

For receipt configuration, please refer to: [Message Delivery Statistics Configuration - vivo](https://www.tencentcloud.com/document/product/1047/60552#daa658b0-1ac0-44a8-8a47-7ec8822ebe82).

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed1162c5b2d511ef96e55254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed42d041b2d511ef8c01525400fdb830.png) |

For receipt configuration, please refer to: [Message Delivery Statistics Configuration - Meizu](https://www.tencentcloud.com/document/product/1047/60552#daa658b0-1ac0-44a8-8a47-7ec8822ebe82).

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ecfb7befb2d511ef9d2952540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ecfa9815b2d511ef8b1b525400f69702.png) |

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/91097dadc1bf11efad135254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed2ded1eb2d511ef8c01525400fdb830.png) |

> **Note:**Regarding **Click for Subsequent Actions** supports the Report Statistics feature:If you choose to open an app or a web page, purchasing the plugin will by default support reporting statistics.If you choose to open a specified interface within the application:For new certificate status, please directly use the auto-fill default value to support click statistics reporting.If there was a certificate configured previously, continue using the old certificate and modify it to the default value to support reporting statistics, or regenerate a new certificate.

### About FCM Data Messaging

FCM provides two push methods: Notification Message and Data Messaging.

- Notification messages have a simple style and do not differentiate between devices. Once successfully integrated, offline push can be performed.
- Data Messaging, offering rich customization for specific devices, supports reach and click reporting, and requires testing on the device before going live after integration.

The console defaults to Notification Message, and switching between modes can be done in the Chat Console:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed12b2f4b2d511ef96e55254002693fd.png)

> **Note:**FCM data messaging capability only supports TIMPush version 7.8 and above on pixel phones. Other manufacturers' devices need to be tested for support.


---
*Source: [https://trtc.io/document/60547](https://trtc.io/document/60547)*
