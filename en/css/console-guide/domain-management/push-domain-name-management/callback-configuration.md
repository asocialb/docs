# Callback Configuration

The callback feature is disabled by default for Cloud Streaming Services (CSS) push. After a push domain name is bound to a callback configuration, the callback feature will be enabled for all push addresses under this domain name. If a callback event is triggered by the configured template during live streaming, Tencent Cloud will send a request to the customer's server which is responsible for the response. After verification, the customer can obtain a JSON packet containing the callback information.
This document describes how to bind/unbind a push domain name to/from a callback template to enable/disable the callback feature.

## Notes

- The template configuration will take effect in about 5–10 minutes.
- When a CSS event is triggered after the callback feature is enabled, you can receive the event information through the [event message notification](https://intl.cloud.tencent.com/document/product/267/38080).
- The callback templates are managed at the domain name level in the console, and rules created by APIs cannot be canceled for the time being. If you bound a template to a specified stream through the callback APIs and want to unbind it, you need to call the [DeleteLiveCallbackTemplate](https://intl.cloud.tencent.com/document/product/267/30813) API.
- One domain name can be bound to only one callback template. After binding, all streams under it will be called back according to this template.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live) and added a [push domain name](https://intl.cloud.tencent.com/document/product/267/35970).
- You have created a [callback template](https://www.tencentcloud.com/document/product/267/31074#creating-a-callback-template.5B.5D(id.3Acallback)).

## Binding Callback Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the target  **push domain name**  or  **Manage**  to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/678d56c6ce9911f084a45254005ef0f7.png)

2. Select  **Template Configuration**  and click  **Edit**  in the upper right corner of the  **Callback Configuration**  tab.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5b8afc48ab0b11f096c2525400454e06.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/722517eeab0b11f0b08552540044a08e.png)

3. Select the corresponding callback template, and click  **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/973549e8ce9911f0aecd525400454e06.png)

## Unbinding Callback Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the target  **push domain name**  or  **Manage**  to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6da32782ce9911f093295254001c06ec.png)

2. Select  **Template Configuration**  and click  **Edit**  in the upper right corner of the  **Callback Configuration**  tab.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c7162a9dce9911f093295254001c06ec.png)

3. Uncheck the associated template and click  **Confirm** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e037a90dce9911f098d1525400bf7822.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/31065](https://www.tencentcloud.com/document/product/267/31065)*
