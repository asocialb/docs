# Certificate Management

Normally, live streaming domain names use the Hypertext Transfer Protocol (HTTP). HTTP can be converted to Hyper Text Transfer Protocol over Secure Socket Layer (HTTPS) using SSL/TLS protocol for encrypted data transmission. You can go to **Certificate Management** to query and configure SSL certificates for domain names.

## How to Configure

The purpose of configuring an SSL certificate for a domain name is to encrypt key user data for secure transmission. A Secure Sockets Layer (SSL) certificate allows a site to switch from HTTP (HyperText Transfer Protocol) to its SSL-based encrypted version HTTPS (HyperText Transfer Protocol over Secure Socket Layer). Currently, only the playback domain name supports the configuration of SSL certificates.

## Configuring Certificate

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage) in the CSS console, and click **Certificate Management** to go to the certificate management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/db44debf3f6311ef91ee525400d5f8ef.png)

2. Click **Configure Certificate** to add a certificate configuration.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fd044f8c3f6311efa180525400f69702.png)

3. In the certificate configuration pop-up window, select a certificate source:
  - **Self-owned certificate**: enter remarks, content, and key of this certificate. After the configuration is saved, the certificate info will be synced to [Certificate Management](https://console.tencentcloud.com/ssl) in the SSL Certificate Service console. For details about how to set the certificate content and key, please see [HTTPS Configuration](https://intl.cloud.tencent.com/document/product/267/31066).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/453b1da33f6411efa917525400fdb830.png)

  - **Tencent Cloud-hosted certificate**: select a certificate you purchased in the SSL Certificate Service console.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/189a76fe3f6511efa917525400fdb830.png)

4. After the certificate is confirmed to be available, click **Next** to enter the domain name configuration page.
5. In **Bind Domain Names**, select one or more playback domain names which match the certificate. If a selected domain name is already bound to a certificate, the new certificate will apply.
6. In **Selected**, you can view selected domain names and whether their HTTPS configuration is enabled.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9a3d6479520c11ee84f2525400494e51.png)

7. Choose whether to enable HTTPS Configuration for selected domain names:

> **Note:**Toggling **Enable HTTPS Configuration** on will enable HTTPS configuration for the domain names.**Enable HTTPS Configuration** is enabled by default. If you toggle this button off, the HTTPS configuration status of the domain names will not change after binding, with only their certificate updated.

8. Click **Confirm**.

## Viewing Certificate Configuration

After you [configure a certificate](https://www.tencentcloud.com/document/product/267/41317#configuring-certificate), you can go to [Certificate Management](https://console.tencentcloud.com/live/domainmanage/certificate) to view its configuration, including the domain name, remarks, source, HTTPS configuration, and expiration time.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9a4626a5520c11ee84f2525400494e51.png)

## Updating Certificate Configuration

1. Go to [Certificate Management](https://console.tencentcloud.com/live/domainmanage/certificate), find the target certificate configuration in the list, and click **Update** on its right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9a486d8e520c11eeabd75254005810a4.png)

2. On the certificate configuration page, configure the certificate again.
3. Click **Confirm**.

## Deleting Certificate Configuration

1. Go to [Certificate Management](https://console.tencentcloud.com/live/domainmanage/certificate), find the target certificate configuration in the list, and click **Delete** on its right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9a45a918520c11ee94c3525400d793d0.png)

2. In the confirmation pop-up window, click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9a3b6839520c11ee974d5254005f490f.png)

> **Note:**After you unbind the certificate, the domain names cannot use HTTPS configuration.


---
*Source: [https://www.tencentcloud.com/document/product/267/41317](https://www.tencentcloud.com/document/product/267/41317)*
