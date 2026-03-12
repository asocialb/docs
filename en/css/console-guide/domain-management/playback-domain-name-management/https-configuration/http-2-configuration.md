# HTTP/2 Configuration

## Overview

HTTP/2 (HTTP/2.0) is upgraded from HTTP/1.1. Compared with HTTP/1.1, it introduces a range of optimization features, including binary framing, multiplexing, header compression, and server push. These features greatly optimize web performance and reduce data exchange latency. Before enabling HTTP/2 configuration, you need to configure an HTTPS certificate.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have [added a playback domain name](https://www.tencentcloud.com/document/product/267/35970).
- **To enable HTTP/2, ensure that HTTPS is correctly configured and enabled, as HTTP/2 depends on HTTPS. Complete the SSL certificate configuration and enable HTTPS before setting HTTP/2. For details, see**[HTTPS Configuration](https://www.tencentcloud.com/document/product/267/31066).

> **Note:**If you are configuring an HTTPS certificate for the first time, wait until the certificate configuration is completed and takes effect before enabling HTTP/2.If you disable the HTTPS certificate feature, the HTTP/2 settings will be automatically disabled and cannot be enabled.When HTTP/2 is enabled, if the HTTPS certificate feature is disabled, HTTP/2 will be automatically disabled.

## Notes

- Currently, only HTTP/2 access is supported. HTTP/2 origin-pull is not supported.
- If the domain name's service region is global, the HTTP/2 configuration will take effect globally. Separate configurations inside and outside the Chinese mainland are not supported.

## Configuration Guide

### Enabling or Disabling HTTP/2 Configuration

1. Enter [Domain Management](https://console.tencentcloud.com/live/domainmanage), click the **playback domain name** you want to configure or **Manage** on the right to enter the domain name detail page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6c3cbbe371a811ef8631525400a9236a.png)

2. Click **Advanced Configuration**. In the **HTTP/2 Configuration** area, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/0843be1f71a611ef8631525400a9236a.png) to enable or disable the **HTTP/2** feature.

> **Note:**Complete the SSL certificate configuration and enable HTTPS before enabling HTTP/2 in the **HTTP/2 Configuration** area.The HTTP/2 feature will take effect approximately 15 minutes after configuration.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e2e9ac07cb9811f093295254001c06ec.png)

  - When you highlight the switch, **HTTP/2** is enabled.
  - When you turn the switch gray, **HTTP/2** is disabled and the **HTTP/2** configuration is automatically invalidated.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0d00b72f71a611efaa4b525400d5f8ef.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/65424](https://www.tencentcloud.com/document/product/267/65424)*
