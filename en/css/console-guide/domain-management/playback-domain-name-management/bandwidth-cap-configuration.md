# Bandwidth Cap Configuration

CSS allows you to set a bandwidth cap for your playback domain. In the acceleration region of your domain, if the peak downstream bandwidth in a reference period hits the cap you set, a 403 error will be returned to playback requests. This feature is disabled by default.

> **Note:**If the bandwidth cap configuration is enabled, the scanning granularity is 5 minutes. If there is a sudden increase in usage within a short period of time, the previous scan may not have triggered the threshold, and the next scan may directly exceed the threshold. In this scenario, there will be a certain delay (approximately 5 minutes) in the access interception operation, and the consumption during this period will be billed normally.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have added a [playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Limits

| Acceleration Region | Default Bandwidth Capping Region | Remarks |
| --- | --- | --- |
| Chinese mainland | Chinese mainland | You can only set a cap for the Chinese mainland. |
| Outside the Chinese mainland | Outside the Chinese mainland | You can only set a cap for outside the Chinese mainland. |
| Global acceleration | Global acceleration | You can set different caps for inside and outside the Chinese mainland.You can also set a global cap. |

## Configuring Bandwidth Cap

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click the name of your playback domain or **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2c38eea611d711ef9af4525400720cb5.png)

2. Select  **Advanced Configuration**  >  **Bandwidth cap configuration**  to view the  **Bandwidth cap configuration** tab.
3. Click  **Edit**  in the upper-right corner of the tab to enter the bandwidth cap configuration page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/960b7da7cc0611f091ab5254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a5f17474cc0611f084a45254005ef0f7.png)

4. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/98f2a38011d711ef89cc5254002fd0a8.png) to enable  **Bandwidth Cap** .

> **Note:**After the bandwidth threshold for global acceleration is configured, it will take effect preferentially.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d15f742acc0611f08e74525400bf7822.png)

  4.1. After the bandwidth cap is enabled, proceed with the following configuration:
  - **Bandwidth Threshold**
    - **Valid Region**  is determined based on the acceleration region type of the playback domain name. For related configuration rules, refer to [Limits](https://www.tencentcloud.com/document/product/267/36543#limits).
    - Fill in the bandwidth threshold based on your actual business needs. Choose the threshold unit as Mbps, Gbps, or Tbps.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ecfb4158cc0611f096d1525400e889b2.png)

5. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/cbc2785811d711efa2935254005ac0ca.png) to enable  **Alert threshold** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/063daa17cc0711f0afdc52540044a08e.png)

  5.1. After the alert threshold is enabled, set the  **alert threshold percentage**  based on your actual business needs. When the access bandwidth/bandwidth threshold reaches the alert threshold, the system will alert you through the Message Center and other methods.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cbbb26fb11d711efbf645254007bbd8c.png)

6. Click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3307a562cc0711f091ab5254007c27c5.png)

> **Note:**The conversion factor between the bandwidth units is 1,000: 1 Tbps = 1,000 Gbps; 1 Gbps = 1,000 Mbps.If you change the acceleration region for your domain, you need to configure the bandwidth cap again.The default alert threshold is 80% of the bandwidth cap. Value range: 0-100.

## Disabling Bandwidth Cap

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click the name of your playback domain or **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3fcc91c411d811efaa1c525400f65c2a.png)

2. Select the  **Advanced Configuration**  tab to view the  **Bandwidth cap configuration**  tab.
3. Click  **Edit**  in the upper-right corner of the tab to enter the bandwidth cap configuration page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/837de35dcc0711f093295254001c06ec.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/96953994cc0711f0ae4f52540099c741.png)

4. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/a98a83b011d811ef9fa952540019e87e.png) to disable  **Bandwidth Cap** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/aed98a8ccc0711f091ab5254007c27c5.png)

5. Click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c42fcd62cc0711f084a45254005ef0f7.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/36543](https://www.tencentcloud.com/document/product/267/36543)*
