# Visible Watermark Configuration

The visible watermark feature is disabled by default for live push. This document describes how to bind/unbind a push domain name to/from a visible watermark template to enable/disable the visible watermark feature.

## Notes

- The template configuration will take effect in about 5–10 minutes.
- After the template is bound successfully, the visible watermark feature will be enabled for push addresses under the specified push domain name.
- One domain name can be bound to only one visible watermark template. After they are bound, all streams under the domain name will be visible watermarked according to this template.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live/livestat) and added a [push domain name](https://tencentcloud.com/document/product/267/35970).
- You have created a [visible watermark template](https://www.tencentcloud.com/document/product/267/31073#Watermark).

## Binding Visible Watermark Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage) and click the **push domain name** to be configured or **Manage** to enter the domain name details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7d85d9d6d0c411f084a45254005ef0f7.png)

2. Select **Template Configuration** and click **Edit** in the **Visible Watermark Configuration** section.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb2a7544d1a511f08f8f525400454e06.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/147fd44fd1a611f0b1675254001c06ec.png)

3. Select a watermark template and click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f1dd36d7d0c311f0b638525400e889b2.png)

> **Note:**You can click **Preview** in the Operation column to view the  visible watermark.

## Unbinding Visible Watermark Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage) and click the **push domain name** to be configured or **Manage** to enter the domain name details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/881633b3d0c411f08823525400454e06.png)

2. Select **Template Configuration** and click **Edit** in the **Visible Watermark Configuration** section.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/72c91d37d1a611f0b1675254001c06ec.png)

3. Clear the target template and click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4c915748d0c411f0a3b05254007c27c5.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/31064](https://www.tencentcloud.com/document/product/267/31064)*
