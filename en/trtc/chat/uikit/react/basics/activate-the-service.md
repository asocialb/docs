# Activate the Service

This article introduces how to [activate the Trial Edition for free](#free), [purchase the official version](#official) of Chat, as well as [renew the official version](#renew), [upgrade to the official version](#upgrade), and [enable automatic renewal](#autorenew). Based on the [Chat version pricing and feature description](https://trtc.io/zh/document/67650?product=chat&menulabel=uikit&platform=react#function), you can select the version you need and refer to the guide below for free activation, purchase, renewal, and upgrade to the official version of Chat.

## Enabling Trial Service

With the Chat service, you can quickly integrate instant messaging to implement various messaging and group management features.

To help you better experience Chat features, we provide a 1-month Trial Edition for each SDKAppID (the Trial Edition does not include complimentary call duration). Each SDKAppID offers a free MAU quota of 100 and allows 2 free trials, each with a valid period of 1 month. Meanwhile, the total experience times for all SDKAppIDs under one account are limited to 10.

1. Log in to the [Tencent RTC console](https://console.trtc.io) and click **Create Application**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8ac73a67c6ac11f08942525400e889b2.png)

2. In the popup, enter an **application name**, select **Chat**, choose the appropriate **deployment region**, and click **Create** to complete the trial version setup.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bb9befd4c6ac11f0a4a55254001c06ec.png)

3. After completing application creation, you will enter the Chat product details page by default. At this point, you have quickly created an application and successfully claimed the free Chat Trial Edition. You can view information in the current [**Chat Product Details Page**](https://console.trtc.io/chat) or [**My Applications**](https://console.trtc.io/app), and refer to the [integration guide](https://trtc.io/document/50056?product=chat&menulabel=uikit&platform=ios%20and%20macos) for integration. The `SDKAppID` and `SDKSecretKey` here will be used in the integration guide.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c89ebcf5c6ad11f0a7775254005ef0f7.png)

### Retrieving UserSig

UserSig is a security signature generated based on SDKAppID, SDKSecretKey and user ID to verify user identity, similar to a login credential.

When using basic cloud services, SDKAppID, UserID, and UserSig are required during SDK initialization or log-in.

In a formal production environment, to underwrite business security, you need to deploy a **UserSig generator on the server** to generate UserSig for authentication. For details, see [UserSig Authentication](https://trtc.io/zh/document/34385?product=chat&menulabel=uikit&platform=react).

But in this step, for the purpose of test and product experience, see the following procedure to get UserSig for testing from console.

> **Note:**UserSig retrieved from console has a default valid period of 180 days.

The process to get UserSig from console is as follows:

1. Enter the [Tencent RTC console](https://console.trtc.io), select **Development Tools >**[**UserSig Tools**](https://console.trtc.io/usersig) in the left sidebar.
2. In the **UserSig generation** module on the left, click the dropdown list to select your **created application (SDKAppID)**. Upon completion, the corresponding **SecretKey (Key)** will be automatically generated.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0cc273a0c6ae11f087ad52540099c741.png)

3. Enter username (UserID).
4. Click **Generate** to generate the corresponding signature UserSig now.

### Next

After obtaining the above information, you can:

- [Run the Demo](https://trtc.io/zh/document/45913?product=chat&menulabel=uikit&platform=ios%20and%20macos) to quickly experience all features of the product.
- [Quickly integrate](https://trtc.io/zh/document/50056?product=chat&menulabel=uikit&platform=ios%20and%20macos) SDK/TUIKit into your project.

## Purchasing the Official Editions

**You need to purchase Chat Monthly Package to use Chat**. For details on the price and feature comparison of Chat Monthly Package, refer to [Chat Version Features and Billing Instructions](https://trtc.io/zh/document/67650?product=pricing).**To purchase, follow these steps:**

1. Visit [Chat purchase page](https://console.trtc.io/subscription/buy/chat), choose appropriate **Deployment Region**, select **the application (SDKAppID) and version to purchase**, **and it is recommended to enable auto-renewal to avoid impacting the business usage**. After confirming purchase information and agreeing to the relevant agreement, click **Subscribe now**.

> **Note:**To purchase enterprise edition, [contact us](https://trtc.io/zh/contact).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e028ed8ac6ae11f0a7775254005ef0f7.png)

2. Proceed to the payment page to complete payment. After purchase completion, you can go to [**Chat Product Details Page**](https://console.trtc.io/chat) or [**My Applications**](https://console.trtc.io/app) to view application version information. See [integration guide](https://trtc.io/document/50056?product=chat&menulabel=uikit&platform=ios%20and%20macos) for integration.

## Renew the Official Edition

1. Visit [**Chat Product Details Page**](https://console.trtc.io/chat), click **Renewal / Upgrade**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/298890a6c6b011f0a93d52540044a08e.png)

2. Visit [Chat Purchase Page](https://console.trtc.io/subscription/buy/chat), select the appropriate **Deployment Region**, confirm the application (SDKAppID) to be purchased, choose the version of the same application package, **and it is recommended to enable auto-renewal to avoid impacting business usage**. Once enabled, when the **account balance is sufficient, it will automatically renew monthly upon expiration**. After confirming purchase information and agreeing to the relevant agreement, click **Subscribe now**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c022660fc6b011f0a4a55254001c06ec.png)

3. Proceed to the payment page to complete payment. After purchase completion, you can go to [**Chat Product Details Page**](https://console.trtc.io/chat) or [**My Applications**](https://console.trtc.io/app) to view application version information. See [integration guide](https://trtc.io/document/50056?product=chat&menulabel=uikit&platform=ios%20and%20macos) for integration.

## Upgrading to Official Edition

1. Visit [**Chat Product Details Page**](https://console.trtc.io/chat), click **Renewal / Upgrade**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dcf96991c6b011f0a7775254005ef0f7.png)

2. Visit [Chat Purchase Page](https://console.trtc.io/subscription/buy/chat), choose appropriate **Deployment Region**, confirm the application (SDKAppID) requiring upgrade, select **a higher version than the application package**, confirm purchase information and agree to the relevant agreement, then click **Subscribe now**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2da972e3c6b111f0a93d52540044a08e.png)

3. Proceed to the payment page to complete payment. After purchase completion, you can go to [**Chat Product Details Page**](https://console.trtc.io/chat) or [**My Applications**](https://console.trtc.io/app) to view application version information. See [integration guide](https://trtc.io/document/50056?product=chat&menulabel=uikit&platform=ios%20and%20macos) for integration.

## Automatic Renewal

Specific steps to enable auto-renewal in the console are as follows:

1. Visit [**Chat Product Details Page**](https://console.trtc.io/chat).
2. Select **the application that requires automatic renewal**.
3. In the Chat product information, click the **Enable** button next to **Auto-renewable**. A confirmation pop-up will appear. Click **Enable**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b272b7e5c6b111f087ad52540099c741.png)

## Contact Us

Welcome to join the [Telegram Technical Exchange Group](https://t.me/tencent_imsdk) and [WhatsApp Communication Group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik) for technical exchange and issue feedback with us and other developers. If you have questions or suggestions during the integration or usage process, please [contact us](https://trtc.io/zh/contact).


---
*Source: [https://trtc.io/document/74511](https://trtc.io/document/74511)*
