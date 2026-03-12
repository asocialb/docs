# Access Control by Region Configuration

Access control by region lets you can manage a blocklist or allowlist for playback regions for the current domain, providing better control over content distribution in specific areas.

## How It Works

- If you are configuring a blocklist, requests from the selected regions are banned.
- If you are configuring an allowlist, only requests from the selected regions are allowed.

## Must-Knows

- After you complete the configuration of the blocklist and allowlist for the playback region, it takes approximately 10 minutes to take effect.
- If you have enabled both the [IP Blocklist/Allowlist Configuration](https://www.tencentcloud.com/document/product/267/46767) and playback region management features, note that the IP blocklist/allowlist takes precedence over playback region management.

## Prerequisites

- You have activated CSS and logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- You have added a [playback domain](https://www.tencentcloud.com/document/product/267/35970).

## Configuring Access Control by Region

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the **playback domain** you want to configure region management for, or click **Manage** on the right side to enter the Domain Management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c5c7cfd611c811ef9fa952540019e87e.png)

2. Under the **Access control** tab, find **Access control by region**.
3. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/31558f75cc2211f08658525400454e06.png)to enable access control by region and complete the following settings:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/006c97cbcc2211f0afdc52540044a08e.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1933afc3cc2211f084a45254005ef0f7.png)

| Configuration Item | Description |
| --- | --- |
| Authenticate By | Choose whether to configure an **Allowlist** or **Blocklist**.An allowlist and blocklist cannot be effective at the same time.If you configure an **allowlist**, access to live stream content will be allowed only for the regions added to the allowlist. Access will be denied for regions that are not added to the allowlist.If you configure a **blocklist**, access to live stream content will be denied for the regions added to the blocklist. Access will be allowed for all regions that are not added to the blocklist. |
| Configuring Regions | You can view and expand regions under **Asia**,**Africa**, **Europe**, **North America**, **South America**, and **Oceania** and them to the list of selected regions.You can also search for regions to find them more quickly. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/570a8feecc2211f084a45254005ef0f7.png)

4. Click **Save** to save the configuration (it takes a while for the configuration to take effect).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/144265344b0811eeb917525400b31cf9.png)

## Modifying Access Control by Region

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the **playback domain** you want to modify the region management settings for, or click **Manage** on the right side to enter the Domain Management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/da1ac17011c811ef9af4525400720cb5.png)

2. Under the **Access contro**l tab, find **Access control by region** and click **Edit**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2ebc422f4b0511eeb9595254003d2706.png)

3. Modify the configuration and click **Save**.

## Disabling Access Control by Region

Follow the steps below to disable access control by region:

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the **Playback Domain** you want to disable access control by region for, or click **Manage**on the right side to enter the Domain Management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/de48632a11c811efa09b525400762795.png)

2. Under the **Access control** tab, find **Access control by region**. Click ![img](https://staticintl.cloudcachetci.com/cms/backend-cms/52abd0582c9111efa01d5254005235d8.png) to disable access control by region.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9b7dc78f4b0711ee9f16525400a32c73.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/56788](https://www.tencentcloud.com/document/product/267/56788)*
