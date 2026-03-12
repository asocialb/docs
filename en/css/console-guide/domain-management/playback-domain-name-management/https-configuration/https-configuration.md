# HTTPS Configuration

## Overview

The HTTPS protocol is a network protocol built based on the SSL and HTTP protocols for encrypted transfer and authentication, which is more secure than the HTTP protocol. If you want to enable HTTPS acceleration, you can do so by enabling the HTTPS feature for the playback domain name and configuring a correct and valid certificate. You can purchase a certificate from Tencent Cloud [SSL Certificate Service](https://intl.cloud.tencent.com/product/ssl). If you already have one, you can upload it to the CSS console for configuration. Currently, CSS only supports the PEM format. If your certificate is in another format, you need to convert it to PEM format first. The format requirements and configuration method for the certificate are as follows:

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have [added a playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Directions

### Step 1. Edit the HTTPS configuration

1. Enter [**Domain Management**](https://console.tencentcloud.com/live/domainmanage) and click the **playback domain name** to be configured or **Manage** on the right to enter the domain name details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b8a43a9d2a2b11efa01d5254005235d8.png)

2. Select **Advanced Configuration** > **HTTPS Configuration**, then click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/c2b8a2e82a2b11ef97da5254007d9c55.png) to enable the HTTPS service.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9d1ca38fcb9511f084a45254005ef0f7.png)

3. After enabling the HTTPS service, enter the HTTPS Configuration page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/aec80bc4cb9511f0ae4f52540099c741.png)

4. Select the source of the certificate to be configured, enter relevant information, and click **Save**.

| Certificate Source | Required Configuration Items |
| --- | --- |
| Self-owned certificate | Certificate Name: enter a custom name used to identify the certificate.Certificate Content: enter the content of the .crt file for Nginx. For more information, please see [Certificate content](#content).Private Key Content: enter the content of the .key file for Nginx. For more information, please see [Certificate key](#private_key). |
| Tencent Cloud-hosted certificate | Certificate List: select an uploaded certificate in [SSL Certificate Service](https://console.tencentcloud.com/ssl). |

> **Note:**The HTTPS feature will take effect approximately 2 hours after configuration is completed, please be patient.

#### Certificate Description

A certificate provided by the [CA](https://intl.cloud.tencent.com/document/product/1007/30192#354) includes Apache, IIS, Nginx, and Tomcat files. **The encryption service of CSS uses Nginx, so you should select the content of the Nginx files for the configuration.**

Go to **SSL Certificate Service console** > [**Certificate Management**](https://console.tencentcloud.com/ssl), select the target certificate, click **Download** in the "Operation" column, and decompress the downloaded package to get the following files:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/55402e92df7911eea462525400bb593a.png)

##### **Certificate****content**:

  - Select the`.crt `file in Nginx and fill in the input box with everything including `-----BEGIN CERTIFICATE----- `and` -----END CERTIFICATE-----`.
  - **Sample content:**

****

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5540a5c1df7911ee9f745254008eb8a8.png)

> **Note:**If your certificate is issued by an intermediate CA and contains multiple certificates, the certificate content should be spliced as follows:
> -----BEGIN CERTIFICATE-----
> -----END CERTIFICATE-----
> -----BEGIN CERTIFICATE-----
> -----END CERTIFICATE-----

##### **Certificate****private key**:

  - Enter the entire content between ` -----BEGIN RSA PRIVATE KEY----- ` and `-----END RSA PRIVATE KEY----- ` in the `.key` file for Nginx.
  - **Sample content:**

****

![](https://staticintl.cloudcachetci.com/cms/backend-cms/55404b43df7911eeb1eb525400b5f95f.png)

### Step 2. Verify the configuration

The HTTPS configuration will take effect in about 2 hours. Please visit the domain name about 2 hours after the certificate is submitted. If HTTPS is displayed in the address bar of the browser, the configuration is successful.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/55403e9ddf7911ee9f745254008eb8a8.png)

### Step 3. Modify the configuration

The configuration can be modified if the HTTPS function is turned on. If this feature is turned off, editing will not be possible. Once it is disabled, CSS will no longer provide HTTPS service for the domain name. If the certificate has expired, it should be replaced with a new valid one.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dffc8ce1cb9511f0a5fa525400454e06.png)

## FAQs

- [What format of the certificate should be filled in for the live HTTPS configuration?](https://intl.cloud.tencent.com/document/product/267/32478)
- [How to identify whether a certificate is in PEM format or DER format?](https://intl.cloud.tencent.com/document/product/267/32478)


---
*Source: [https://www.tencentcloud.com/document/product/267/31066](https://www.tencentcloud.com/document/product/267/31066)*
