# Package Purchase, Renewal and Upgrade

## **Package Purchase**

Tencent Real-Time Communication (Tencent RTC) products support both **prepaid packages** and **pay-as-you-go** billing. For detailed billing methods, please refer to the [Billing Overview](https://trtc.io/document/64149). You can also use the [Price Calculator](https://trtc.io/pricing/calculator) to estimate the service usage and costs for your business.

This document primarily explains how to purchase a prepaid package.

### Prerequisites

Before purchasing a package, you must register a Tencent Cloud account and log in to the [Tencent RTC Console](https://trtc.io/login?s_url=https://console.trtc.io).

### Operation Steps

1. **Access Package Subscription:**After logging into the [Tencent RTC Console](https://trtc.io/login?s_url=https://console.trtc.io), navigate via the left sidebar to **Package Management -> Package Subscription**. Select the product and corresponding version you wish to purchase, then click the Subscribe Now button under the version to enter the order page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f7e64a7ac5e811f0a1dc52540044a08e.png)

2. **Submit Order and Complete Payment:**On the order page, complete your selections and confirm the information as follows:
  - **Step 1:  Bind Application.**Select an existing application or create a new one to bind the package to.
  - **Step 2: Select Package Version.**Choose the product package version you need to purchase.
  - **Step 3: Set Auto-Renewal.**Choose whether to enable auto-renewal for the package. If enabled, the package will automatically renew next month at the list price, ensuring service continuity without manual intervention.
  - **Step 4: Read and Accept Agreements.**Read and tick the checkboxes for the Service Level Agreement (SLA) and Billing Rules.
  - **Step 5: Complete Payment.**After making all selections and confirming the information, click Subscribe Now to enter the payment page and complete the order payment.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/440adc15c5e911f085c7525400454e06.png)

> **Noteï¼**If you have not yet bound your payment information, please follow the console prompts to complete the payment binding first.

## Package Renewal

### Manual Renewal

Log in to the [Tencent RTC Console](https://trtc.io/login?s_url=https://console.trtc.io), and use the left sidebar to navigate to the page of the product you need to renew. In the Application Information Card, click the **Renew / Upgrade** button to enter the renewal order page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aab3d236c5e911f0b88b525400bf7822.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b09308b8c5e911f0a1dc52540044a08e.png)

### Auto-Renewal

#### Enabling Auto-Renewal

**During Purchase:**You can select to enable auto-renewal when placing the order on the package purchase page. Once enabled, the service for the following month will be automatically subscribed before the package expires, ensuring uninterrupted service. You can cancel auto-renewal at any time.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/16a02bc1c5ea11f0b88b525400bf7822.png)

**After Purchase:**If you did not enable auto-renewal during the initial purchase, you can still enable it through the console. Log in to the console, select the product for which you want to enable auto-renewal via the left sidebar (if you have multiple packages for the same product, you can switch the application in the top-left corner). Find Auto-Renewal in the Application Information Card and click **Enable**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8f98f741c5ea11f0a62b5254007c27c5.png)

> **Noteï¼**Before enabling auto-renewal, please ensure that your account has sufficient available balance. Otherwise, failed deduction will lead to the failure of auto-renewal, and the service termination for the following month will affect your usage.

### Disabling Auto-Renewal

If you need to disable auto-renewal for a package, find **Auto-Renewal** in the same **Application Information Card** location as described above, and click **Disable**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f62f61a3c5ea11f0b88b525400bf7822.png)

## Package Upgrade

### Package Upgrade Description

If a monthly package you have purchased no longer meets your needs and you require an upgrade to unlock more capabilities, you can follow the instructions below to upgrade your package version. Upgrading a package that is still valid allows you to **immediately unlock** the functional services corresponding to the new version, without having to wait for the current version to expire or purchase a new resource separately.

- **Scope of Support:** This feature is limited to RTC-related product packages (Call, Live, Conference, RTC Engine) and Chat packages.Beauty AR related packages currently do not support upgrading. If you require an upgrade for the Beauty AR package, please [contact us](https://trtc.io/contact).
- **Upgrade Direction:**Package upgrades can **only be from a lower version to a higher version.** For example, the Live Standard version can only be upgraded to the Live Pro version, but cannot be downgraded to the Live Lite version.

### Upgrade Rules

Packages for Call, Conference, Live, RTC Engine, and Chat products can be upgraded to **any higher version package** within their validity period.

- **Upgrade Price Calculation:**The upgrade price is calculated as

*Upgrade Price = (List Price of Upgraded Package - Discounted Price of Current Package) * Remaining Validity Days / Total Validity Days*

- **Special Case for Discounted Purchase:**If the current package was purchased at a discounted price, the supplemental price difference is calculated as

*Upgrade Price = (List Price of Upgraded Package - Discounted Price of Current Package) * Remaining Validity Days / Total Validity Days*

- **Calculation of Remaining Package Minutes** (Only for Call, Conference, Live, and RTC Engine package upgrades): The available minutes in the upgraded package is calculated as

*Available  Minutes After Upgrade = ( Available Minutes in Upgrade Package - Available Minutes in Current Package)  * Remaining Validity Days / Total Validity Days*

### Upgrade Guide

**Accessing the Upgrade Page**

Select the product you wish to upgrade from the left sidebar, enter the product page, and click the **Renew / Upgrade** button in the Application Information Card of the application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b8795603c5ec11f0a7ca5254001c06ec.png)

**Upgrade Purchase Operation**

Once on the upgrade page, follow these steps to complete the upgrade:

- **Step 1: Select Application.**Choose the application corresponding to the package you are upgrading.
- **Step 2: Select Target Version.**Choose the target version you wish to upgrade to.
- **Step 3: Confirm Agreements.**Read and tick the checkboxes for the SLA and Billing Rules.
- **Step 4: Confirm and Pay.**Confirm the supplemental price difference required for the upgrade, click Subscribe Now to submit the order, and complete the payment.

> **Noteï¼**Upon completion of the upgrade, the new functional services will be unlocked immediately. Please confirm your application version on the Application Details page in the console to ensure it matches the upgraded version. If the version information matches, your application has been successfully upgraded.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c7f347fec5ec11f085c7525400454e06.png)


---
*Source: [https://trtc.io/document/74514](https://trtc.io/document/74514)*
