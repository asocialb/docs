# Referer Configuration

You can set referer blocklist/allowlist and rules to block/allow playback requests so as to protect live streaming content. You can also choose whether to allow empty referer.

## How to Configure

Referer URL is based on the HTTP protocol. CSS uses the referer field in an HTTP request to identify the source and verify the request, and then determine whether to accept or reject the request.

## Notes

- Referer information is included in the HTTP. After configuration, RTMP and non-web WebRTC will not verify the Referer configuration and will still play normally. If you need to configure Referer, it is recommended to use FLV or HLS for playback.
- Enabling, disabling, or modifying the referer takes effect in 15-20 minutes after the configuration. You don't need to push streams again.
- The referer hotlink protection feature verifies the referer information in the header of an HTTP request so as to check whether the request is valid and allow or reject live streaming accordingly. However, there may be cases where a forged referer bypasses the verification to hotlink the service. Therefore, we recommend you not strongly rely on referer for content protection.

## Prerequisites

- You have activated the CSS service and logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- You have [added a playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Enabling Referer

1. Select [**Domain Management**](https://console.tencentcloud.com/live/domainmanage), and click the target **playback domain** or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d4c60ab309ee11f0990f52540099c741.png)

2. In **Access Control** > **Referer Configuration**, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/568af26447f711eeb917525400b31cf9.png) to enable Referer Hotlink Protection.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4af0aa5eab2911f096c2525400454e06.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6af68babab2911f0a0a052540099c741.png)

3. And configure as follows:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/811ede53ab2911f0a0a052540099c741.png)

| Configuration Item | Description |
| --- | --- |
| Referer Type | Select**Blocklist**or **Allowlist** as the referer type.You cannot select both of them, When the referer allowlist is configured, request sources on the list will be allowed to access the live streaming content while those not on the list will be blocked.When the referer blocklist is configured, request sources on the list will be blocked to access the live streaming content while those not on the list will be allowed. |
| Allow Empty Referer | When this feature is enabled, access will be allowed for HTTP requests with empty or no referer field. Users can access the live stream URL directly via browsers.When this feature is disabled, requests with empty referer will be rejected. |
| Referer Patterns | The total number of characters for rules cannot exceed 4,000. (It is recommended that the number of rules be no greater than 200.) Separate rules by line breaks. Blank lines and semicolons (；）are not allowed.For ordinary rules, strings in these rules can be matched, and the wildcard character * is supported for fuzzy matching. For example,`https://*.domain.com`.For regular expression rules, they should be included in parentheses（）. For example, you can use `(^https?://www.domain.com($/)` to match `www.domain.com` and use` (https?://[^/?]*domain.com($\|/) to match*.domain.com.` |

4. Click **Save** to save the configuration.

## Modifying Referer

1. Select [**Domain Management**](https://console.tencentcloud.com/live/domainmanage), and click the target **playback domain** or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a4f0848409f111f09d28525400bf7822.png)

2. In **Access Control** > **Referer Configuration**, click **Edit** to enter the referer configuration page.
3. Modify the configuration items and click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a582b4f3ab2911f0b08552540044a08e.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bc709151ab2911f096c2525400454e06.png)

## Disabling Referer

After [enabling the referer](#enabling-referer), you can disable it by performing the following steps:

1. Select [**Domain Management**](https://console.tencentcloud.com/live/domainmanage), and click the target **playback domain** or click **Manage** on the right to enter the domain management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c7b670e309f111f09ecc52540044a08e.png)

2. In **Access Control** > **Referer Configuration**, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/c2384be847f811ee9f16525400a32c73.png) to disable the referer.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c7a92ee7ab2911f09b75525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e97a5b3bab2911f09b75525400bf7822.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/39474](https://www.tencentcloud.com/document/product/267/39474)*
