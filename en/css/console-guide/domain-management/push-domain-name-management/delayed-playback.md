# Delayed Playback

Delayed playback is a feature that processes streams in the cloud, enabling the playback end to operate with a set delay. This delay is distinct from the inherent delay of the protocol itself. Delayed playback is applicable to significant live streaming events. To prevent unforeseen circumstances during the events, if you need to prepare control and response measures in advance, you can configure this feature directly through the console. For instance, during the live streaming of a large-scale evening party, if you set a delay of 5 minutes in advance, the online audience will see the picture 5 minutes later than the actual event. In case of an unexpected incident, the director will have a 5-minute pre-processing time period to switch machine positions or backup streams through the director's console, thereby mitigating live streaming risks.

## Notes

- You can enable delayed playback via three methods:
  - Configure it in the Cloud Streaming Services (CSS) console.
  - Call the [playback delaying API](https://www.tencentcloud.com/document/product/267/30850).
  - Add a `txDelayTime` parameter to the end of a push URL. For details, please see [Push Configuration](https://www.tencentcloud.com/document/product/267/41660)。
- Delayed playback is a billing value-added service. To activate the delayed playback feature, use the console settings, call the delayed live streaming interface or carry the delayed playback parameter configuration with the push domain name. After successful push, the [Value-added feature billing](https://www.tencentcloud.com/document/product/267/54973) will be generated.

> **Note：**Currently, the API method is not recommended because calling an API involves configuration caching, which makes it difficult to estimate when the feature takes effect. You are advised to quickly enable the feature using the first or third method.

- After enabling delayed playback, you need to add a delayed playback configuration in the console or using an API before the feature can take effect. After it takes effect, [extended feature fees](https://www.tencentcloud.com/document/product/267/54973) will be incurred for streams published.
- Delayed playback will take effect after waiting for 5 minutes once the configuration is completed.

## Prerequisites

- You have activated the Cloud Streaming Services (CSS) and logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have added a [push domain](https://www.tencentcloud.com/document/product/267/35970).

## Configuring Delayed Playback

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage) and click the **push domain** to be configured or click **Manage** on the right to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/964023b9558611efb36952540075b605.png)

2. Select the **Advanced Configuration** tab. In the **Delayed playback configuration** area, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/83460fddfeb811edad3b5254007e6a5b.png) to enable the delayed playback configuration.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/966360d9ab2111f096c2525400454e06.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/78af7d75ab2111f0b08552540044a08e.png)

  2.1. Confirm whether to  **enable** the current delayed playback configuration. Click  **Enable**  to enable it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/014c5034ab2311f0a0a052540099c741.png)

  2.2. After the delayed playback is enabled, click  **Add** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2b714f21ab2311f09b75525400bf7822.png)

3. Complete the following settings based on your needs:

Scope Select All

Scope Select Custom

![](https://staticintl.cloudcachetci.com/cms/backend-cms/379713dfab2411f0b0045254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/57502d31ab2411f0b08552540044a08e.png)

| Configuration Item | Description |
| --- | --- |
| Scope | Select **All** or **Custom**:**All**:  Apply the configuration to the current domain.**Custom**: Apply the configuration to a specific application or stream, which will override the configurations applied to **All**. |
| AppName | When there are configurations for the same AppName and StreamName, the most recently created configuration takes effect. |
| StreamName | When there are configurations for the same AppName and StreamName, the most recently created configuration takes effect. |
| Delay | A positive integer no greater than 600. |
| Expiration Time | The maximum selectable time is no more than 7 days from the current time. |

  3.1. Click **Confirm** to save the configuration.
  3.2. Based on your actual business needs, click **New** on the right side to continue adding **Delayed playback configuration**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9a8df6f9ab2411f09710525400e889b2.png)

> **Note：**You can add up to 50 delayed playback configurations.

## Modifying Delayed Playback Configuration

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the **push domain** to be configured or click **Manage** on the right to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/04ecb2a6558711ef9bf1525400a9236a.png)

2. Select the **Advanced Configuration** tab. In the **Delayed playback configuration** area. Click **Edit** on the right side to enter the delayed playback configuration page.
3. Update the configurations based on your needs, and click **Confirm** to save the modifications.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c5621112ab2411f0a0a052540099c741.png)

## Deleting Delayed Playback Configuration

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage), click the **push domain** to be configured, or click **Manage** on the right to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/18be7d3c558711efb36952540075b605.png)

2. Select the **Advanced Configuration** tab. In the **Delayed playback configuration** area, select the configuration to be deleted and click **Delete** on the right side.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e143532cab2411f0b08552540044a08e.png)

3. Confirm whether to delete this **Delayed playback configuration**, and click **Are you sure you want to delete** to successfully delete it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f8fe7a9aab2411f0a0a052540099c741.png)

> **Note:**After deletion, ongoing streams will be delivered in real time again only after you stop them and publish them again.

## Disabling Delayed Playback

If you want to disable delayed playback configuration after enabling it, follow these steps:

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage), click the **push domain** to be configured, or click **Manage** on the right side to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2bf87693558711efb36952540075b605.png)

2. Select **Advanced Configuration** tab. In the **Delayed playback configuration** area, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/148826c0feb911edad3b5254007e6a5b.png) to toggle off the configuration.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/385e21ccab2511f0b5345254005ef0f7.png)

3. Confirm whether to disable this delayed playback configuration, and click **Disable**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4ab6cdd5ab2511f0b0045254007c27c5.png)

> **Note:**After delayed playback is disabled, the delayed playback configurations added via the console or using APIs will no longer take effect. For ongoing streams, the change will be applied only if you stop the streams and publish them again.


---
*Source: [https://www.tencentcloud.com/document/product/267/55264](https://www.tencentcloud.com/document/product/267/55264)*
