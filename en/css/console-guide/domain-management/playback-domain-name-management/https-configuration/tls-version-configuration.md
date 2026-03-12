# TLS Version Configuration

## Background

The Transport Layer Security (TLS) protocol aims to ensure the security and confidentiality of data exchanged between two applications. Currently, four versions of the TLS protocol are available, including TLS 1.0, TLS 1.1, TLS 1.2, and TLS 1.3. Earlier versions are more compatible but less secure, while later versions are more secure but less compatible.

### Description of TLS Protocol Versions

| TLS Protocol Version | Supported Mainstream Browser |
| --- | --- |
| TLS 1.0 | IE6+ |
|  | Chrome 1+ |
|  | Firefox 2+ |
| TLS 1.1 | IE 11+ |
|  | Chrome 22+ |
|  | Firefox 24+ |
|  | ME 12+ |
|  | Safari 7+ |
|  | Opera 12.1+ |
| TLS 1.2 | IE 11+ |
|  | Chrome 30+ |
|  | ME 12+ |
|  | Firefox 27+ |
|  | Safari 7+ |
|  | Opera 16+ |
| TLS 1.3 | Chrome 70+ |
|  | Firefox 63+ |
|  | ME 79+ |
|  | Safari 14+ |
|  | Opera 57+ |

#### Using More Secure TLS Encryption Feature of Updated Version to Encrypt Network Connections at Transport Layer

| Version | Description |
| --- | --- |
| TLS 1.3 (Recommended) | RFC 8446, published in 2018. TLS 1.3 is faster and more secure than TLS 1.2. |
| TLS 1.2 (Recommended) | RFC 5246, published in 2008. It adopted a strong encryption technology to provide higher security protection. |
| TLS 1.1 | RFC 4346, published in 2006. It fixed several vulnerabilities in TLS 1.0. |
| TLS 1.0 | RFC 2246, published in 1999 based on SSL v3.0. This version is susceptible to various attacks, such as BEAST and POODLE. |

## Overview

When you have enabled HTTPS configuration, Cloud Streaming Services (CSS) supports multiple TLS versions by default to meet the access needs of various user terminals. Generally, there is no need to modify this configuration. If you have higher security requirements for your website and need to prevent user access by using TLS versions of lower security, you can customize the SSL/TLS versions. CSS supports TLS 1.0, TLS 1.1, TLS 1.2, and TLS 1.3 by default. You can disable/enable specific TLS versions based on your business needs.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have [added a playback domain name](https://www.tencentcloud.com/document/product/267/35970).
- **To modify the TLS version configuration, you need to first ensure that HTTPS is correctly configured and enabled, as the TLS version configuration depends on HTTPS. Before setting the TLS version, complete the SSL Certificates configuration and enable HTTPS. For operation methods, refer to** [HTTPS Configuration](https://www.tencentcloud.com/document/product/267/31066).

## Notes

- The TLS version configuration will take effect approximately 15 minutes after completion.
- Downgrading the TLS version (for example, from TLS 1.2 to TLS 1.1 or TLS 1.0) or disabling the TLS version configuration may cause security and compliance issues. Proceed with caution.
- TLS 1.3 is enabled by default and cannot be disabled.
- After the HTTPS configuration is disabled, the console will hide the TLS version configuration.
- Disabling the HTTPS configuration will lead the TLS version configuration failure.
- If you change the TLS version after enabling the HTTPS configuration, and then disable the HTTPS configuration, the TLS version will remain as the previously selected version upon re-enabling of HTTPS next time.

## Configuration Guide

### Viewing TLS Version Configuration

1. Enter [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the **playback domain** you want to configure or **Manage** on the right to enter the domain detail page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d9186135ae1e11efbfb3525400bdab9d.png)

2. Switch to **Advanced Configuration** and find **TLS Version Configuration**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8bb4dbb0cb9911f0afdc52540044a08e.png)

### Modifying TLS Version Configuration

1. Enter [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the **playback domain** you want to configure or **Manage** on the right to enter the domain detail page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dc9d6a6aae1e11ef8c01525400fdb830.png)

2. Choose **Advanced Configuration** > **TLS Version Configuration** and click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/5cfa1514b21711ef970f525400d5f8ef.png) to enter the TLS version configuration modification page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/05ee231acb9a11f093295254001c06ec.png)

3. In the TLS version control area, you can enable or disable the corresponding TLS version based on your business needs.

> **Note:**You can enable a single version or multiple consecutive ones. For example, you can concurrently enable versions 1.0, 1.1, and 1.2, but not versions 1.0 and 1.2.You cannot disable all versions.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ae80cceeae1f11ef96e55254002693fd.png)

4. Click **Confirm** to save the configuration. The edited TLS version configuration will take effect in about 15 minutes. Please be patient.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6904e62dcb9a11f093295254001c06ec.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/67511](https://www.tencentcloud.com/document/product/267/67511)*
