# UA Blocklist/Allowlist Configuration

Cloud Streaming Services (CSS) supports access control by configuring User-Agent blacklist and whitelist rules. This method makes rule judgment based on the User-Agent information in the user's HTTP request header to allow or deny user access as needed.

## How It Works

- Configure **UA allowlist**: Only the configured UA content can access the current live broadcast content.
- Configure**UA blocklist:** Only the configured UA content cannot access the current live broadcast content.

## Must-Knows

- Turn on/off UA Blocklist/Allowlist, it is expected to take effect in 15-20 minutes.
- If UA authentication and other authentication methods are configured at the same time, the priority order is: Protocol > IP > Region > UA. The system will first authenticate according to the protocol, then IP, region, and finally UA.

## Prerequisites

- You have activated CSS and logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- You have added a [playback domain](https://www.tencentcloud.com/document/product/267/35970).

## Enabling UA Blocklist/Allowlist

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage), click the **Playback Domain** that requires UA Blocklist/Allowlist configuration or the **Manage**on the right, and enter the Domain Management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6abeb062959a11ef9dcd525400f69702.png)

2. Within the **Access Control**> **UA Blocklist/Allowlist**, click on ![](https://staticintl.cloudcachetci.com/cms/backend-cms/6ab51ea8959a11efb488525400a9236a.png) to enable the UA Blocklist/Allowlist.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/85a512b3cc3211f0afdc52540044a08e.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6bf680f7cc3311f08e74525400bf7822.png)

3. After enabling the **UA blocklist/allowlist**,  enter the **UA ​​blocklist/allowlist**, configuration page and perform the following configuration:

Blocklist

Allowlist

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d0d9b52f95cc11efb488525400a9236a.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/df6d901a95cc11ef8bbd525400fdb830.png)

| Configuration Item | Description |
| --- | --- |
| Authenticate By | Allowlist or blocklist:You cannot select both. |
| Empty UA | The empty User-Agent function is turned off by default and can be turned on manually.After empty User-Agent is enabled:In the blocklist scenario, requests are allowed if the UA value is empty or the UA field does not exist.In the allowlist scenario, requests are rejected if the UA value is empty, and requests are allowed if the UA field does not exist. |
| Authentication Content | Wildcards * and multiple values are supported, with one value per line. For multiple values, fill in each value on a separate line. English semicolons (;) are not supported. For example: curl**IE**Chrome**Firefox*It is case-sensitive, supporting up to 100 characters. |

4. Click **Confirm** to save the configuration.

> **Note:**The UA blocklist/allowlist will take effect in about 10 minutes after configuration. Please wait.

## Modifying an UA Blocklist/Allowlist

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar, and click the target **playback domain** or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6aede7ea959a11ef9dcd525400f69702.png)

2. Click Access Control and, in the **UA Blocklist/Allowlist** area, click **Edit.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8c8c060695d011efa50f52540075b605.png)

3. Modify the configuration and click **Confirm**.

## Disabling UA Blocklist/Allowlist

Follow the steps below to disable UA Blocklist/Allowlist:

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar, and click the target **playback domain** or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6abfd58e959a11efafd5525400d5f8ef.png)

2. Select the**Access Control** tab. In the **UA Blocklist/Allowlist** area, click ![img](https://staticintl.cloudcachetci.com/cms/backend-cms/6abbebf5959a11efafd5525400d5f8ef.png)to disable UA Blocklist/Allowlist.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a6d38ff595d111efb488525400a9236a.png)

3. When closing UA Blocklist/Allowlist, the system will pop up a confirmation window. Click **Confirm** to turn off the feature. Please note that it is expected to take 15-20 minutes after shutdown to take effect.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5888f8fb95d311efa50f52540075b605.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/69859](https://www.tencentcloud.com/document/product/267/69859)*
