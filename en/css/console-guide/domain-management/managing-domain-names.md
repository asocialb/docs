# Managing Domain Names

On the Domain Management page of the Cloud Streaming Services (CSS) console, you can perform a series of operations on your domain names according to your business needs, including enabling, disabling, and deleting the domain names.

## Note

CSS provides a test domain name `xxxx.livepush.myqcloud.com` by default. You can use it for push testing, but we do not recommend using it as the push domain name for your real business. This domain name cannot be deleted.

## Prerequisites

1. You have activated the [CSS](https://intl.cloud.tencent.com/product/css) service.
2. You have added a [domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Viewing a Domain Name

Log in to the [CSS console](https://console.tencentcloud.com/live/domainmanage) and select **Domain Management**. you can view the CNAME configuration status, type, status,and domain name addition time. To view details, click the domain name or Manage on its right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6fdaf0c7531e11f0adb15254005ef0f7.png)

## Configuring a Domain Name

- If you need to configure a push domain name, please see [Push Configuration](https://intl.cloud.tencent.com/document/product/267/31059).
- If you need to configure a playback domain name, please see [Playback Configuration](https://intl.cloud.tencent.com/document/product/267/31058).

## Disabling a Domain Name

If you do not want to use a live streaming domain name temporarily, you can disable it. Here are the steps to disable a domain name:

> **Note:**After a live streaming domain name is disabled, the domain name information will still be retained in the system, but the live streaming services will no longer process requests for the domain name. This means users will no longer be able to initiate live streaming push and playback through the domain name. Additionally, ongoing streaming or playback will not be interrupted.

1. Log in to the [CSS console](https://console.tencentcloud.com/live/domainmanage) and select **Domain Management**. In the domain name list, find the domain name you want to disable and click **Disable**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bf78eeb3531e11f0bf84525400454e06.png)

2. In the pop-up window, click **Confirm** to disable the live streaming domain name.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e9625b51531e11f095fc5254001c06ec.png)

3. In the Status column on the Domain Management page, you can see that the current status of the domain name has changed to **Disabled**. The domain name has been successfully disabled and cannot be used for live streaming push and playback.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/32f898d3531f11f0abce52540099c741.png)

## Enabling a Domain Name

If you need to re-enable a disabled domain name, follow these steps:

1. Log in to the [CSS console](https://console.tencentcloud.com/live/domainmanage) and select **Domain Management**. In the domain name list, find the domain name you want to re-enable and click **Enable**. Live streaming services will be resumed for the domain name.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8ac71986531f11f095fc5254001c06ec.png)

2. In the Status column on the Domain Management page, you can see that the current status of the domain name has changed to **Enabled**. You can use this domain name again for live streaming push and playback.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c6164289531f11f09a935254007c27c5.png)

## Deleting a Domain Name

> **Note:**Deletion is irreversible. When you delete a domain name, all its configurations will be permanently deleted.You can still view the usage data of deleted domain names.

If you need to delete a domain name, follow these steps:

1. Log in to the [CSS console](https://console.tencentcloud.com/live/domainmanage) and select **Domain Management**. In the domain name list, find the domain name you want to delete and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f886ae3c532011f095fc5254001c06ec.png)

2. In the pop-up window, click **Confirm** to delete the domain name from your CSS console.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/43e7114c532111f09a935254007c27c5.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/64153](https://www.tencentcloud.com/document/product/267/64153)*
