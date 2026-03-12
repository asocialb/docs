# Time Shifting Configuration

This document shows you how to bind a time shifting template to a push domain to enable time shifting for the domain, as well as how to unbind a template to disable the feature. Time shifting is disabled by default.

## Use Limits

- After a template is successfully bound to a push domain, time shifting will be enabled for push addresses under that domain.
- One domain can be bound to only one time shifting template. After binding, time shifting will be enabled for all streams under the domain.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live) and added a [push domain](https://intl.cloud.tencent.com/document/product/267/35970).
- You have created a [time shifting template](https://www.tencentcloud.com/document/product/267/53312#creating-a-time-shifting-template).

## Binding a Time Shifting Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the target **push domain** or click **Manage** to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/34e25fd10c6111ef8fbd5254008af8cc.png)

2. Select the **Template Configuration** tab and click **Edit** in the **Time shifting configuration** area.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1eb17b2aab0711f09b75525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/104dd197ab0711f09b75525400bf7822.png)

3. Select a time shifting template and click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/00d34634737711f087e15254005ef0f7.png)

## Unbinding a Time Shifting Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the target **push domain** or click **Manage** to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/489a63c70c6111ef8fbd5254008af8cc.png)

2. Select the **Template Configuration** tab and click **Edit** in the **Time shifting configuration** area.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1cef3083737711f084fc525400bf7822.png)

3. Unselect the template and click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/48aaac9a737711f0b9a25254007c27c5.png)

> **Note:**Unbinding a time shifting template will not affect ongoing live streams.


---
*Source: [https://www.tencentcloud.com/document/product/267/52829](https://www.tencentcloud.com/document/product/267/52829)*
