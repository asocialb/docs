# Invisible Watermark（Digital watermark）Configuration

The invisible watermark (digital watermark) feature is disabled by default for live push. This document describes how to bind/unbind a push domain name to/from an invisible watermark (digital watermark) template to enable/disable the invisible watermark feature.

## Notes

- The template configuration will take effect in about 5–10 minutes.
- After the template is bound successfully, the digital watermark feature will be enabled for push addresses under the specified push domain name.
- One domain name can be bound to only one digital watermark template. After they are bound, all streams under the domain name will be digital watermarked according to this template.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live/livestat) and added a [push domain name](https://www.tencentcloud.com/document/product/267/35970).
- You have created an [invisible watermark template](https://www.tencentcloud.com/document/product/267/74854#Watermark).

## Binding Invisible Watermark Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage) and click the **push domain name** to be configured or **Manage** to enter the domain name details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/90348c36d0c411f093295254001c06ec.png)

2. Select **Template Configuration** and click **Edit** in the**Invisible Watermark Configuration** section.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/03f35254d1a611f08f8f525400454e06.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8741fd89d1a611f09f555254007c27c5.png)

3. Select a watermark template and click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ff3d57e3d0c511f0a3b05254007c27c5.png)

## Unbinding Invisible Watermark Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage) and click the **push domain name** to be configured or **Manage** to enter the domain name details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/962e26bfd0c411f0800752540099c741.png)

2. Select **Template Configuration** and click **Edit** in the**Invisible Watermark Configuration** section.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9af0f6f8d1a611f08206525400e889b2.png)

3. Clear the target template and click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2b9ec05ad0c611f0b638525400e889b2.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/74855](https://www.tencentcloud.com/document/product/267/74855)*
