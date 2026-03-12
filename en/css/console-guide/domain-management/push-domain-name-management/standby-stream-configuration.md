# Standby Stream Configuration

This document shows you how to bind a standby stream template to a push domain to enable the standby stream feature for that domain, as well as how to unbind a template to disable the feature. The standby stream feature is disabled by default.

## Notes

- A template takes effect about 5-10 minutes after it is bound to a domain.
- After a template is successfully bound to a push domain, the standby stream configured will take effect for all push addresses under that domain.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live) and added a [push domain](https://intl.cloud.tencent.com/document/product/267/35970).
- You have [created a standby stream template](https://intl.cloud.tencent.com/document/product/267/31073).

## Binding a Standby Stream Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the target **push domain** or click **Manage** to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d5378bf40c6011ef8222525400188675.png)

2. Select the **Template Configuration** tab and click **Edit** in the **Standby stream configuration** area.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b4f88069ab2011f0a0a052540099c741.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c6ff1138ab2011f0a0a052540099c741.png)

3. Select a standby stream template and click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e93d352aab2011f096c2525400454e06.png)

> **Note:**You can click **Preview** in the **Operation** column to preview the standby stream.

## Unbinding a Standby Stream Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the target **push domain** or click **Manage** to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ed2497980c6011ef89045254000ded98.png)

2. Select the **Template Configuration** tab and click **Edit** in the **Standby stream configuration** area.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fec49df2ab2011f09b75525400bf7822.png)

3. Unselect the template and click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/12f1ac50ab2111f09b75525400bf7822.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/53403](https://www.tencentcloud.com/document/product/267/53403)*
