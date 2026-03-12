# Region Configuration

To use content delivery, acceleration, and playback services in a different region, you can change the acceleration region for your playback domain in the CSS console.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have added a **playback domain name**.

> **Note:**In the process of adding a new domain and selecting a playback domain, please choose the acceleration region required for live broadcast distribution, such as "Chinese mainland". Subsequently, fill in the domain name and tag information optionally. Click on **Add Domain and proceed to the next step**.![](https://staticintl.cloudcachetci.com/cms/backend-cms/947a4776144811f0aaa3525400e889b2.png)

## Notes

- **CSS pricing differs inside and outside the Chinese mainland. For details, see**[Billing Overview](https://intl.cloud.tencent.com/document/product/267/2819)**.**
- A playback domain cannot be used outside its acceleration region.
- If the accelerated region includes the Chinese mainland, you need to apply for ICP filing for your playback domain.
- Changing the acceleration region will reset the bandwidth cap. You need to configure it again.

## Directions

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click the name of your**playback domain** or **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/aa2e7c3d3dd211efbec9525400a9236a.png)

2. Select the **Advanced Configuration** tab and find **Region configuration**.
3. Click **Edit**. In the pop-up window, you can change the acceleration region to **Chinese mainland**, **Global**, or **Outside Chinese mainland**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/63d8c9d9cbf711f08e74525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e3bd293bcc0411f096d1525400e889b2.png)

4. Click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2f18bb663dd311efb89a52540075b605.png)

| Acceleration Region | ICP Filing Required | Description |
| --- | --- | --- |
| Chinese mainland | Yes | Cannot handle requests outside the Chinese mainland. |
| Global | Yes | Acceleration is supported globally, but prices differ inside and outside the Chinese mainland. |
| Outside Chinese mainland | No | Cannot handle requests inside the Chinese mainland. Prices differ inside and outside the Chinese mainland. |


---
*Source: [https://www.tencentcloud.com/document/product/267/31067](https://www.tencentcloud.com/document/product/267/31067)*
