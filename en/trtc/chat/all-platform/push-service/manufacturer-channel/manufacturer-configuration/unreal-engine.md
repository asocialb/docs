# Unreal Engine

The push service currently supports Vendor Channels such as Xiaomi, Huawei, Honor, OPPO, vivo, Meizu, OnePlus, realme, iQOO, FCM, and Apple.

iOS

Android

Before integrating the message push plug-in, you must apply for an APNs Push Certificate from Apple and upload the push certificate to the Chat console. Then follow the quick integration procedure to complete the setup.

## Operation Steps

### Step 1: Apply for an APNs Certificate

#### Enable Remote App Push

1. Log in to the [Apple Developer Center](https://developer.apple.com/account/) website, click **Certificates, Identifiers & Profiles** or **Certificates, IDs & Profiles** in the sidebar, and enter the **Certificates, IDs & Profiles** page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e679ed6920011f0a14552540099c741.jpeg)

2. Click **+** on the right of Identifiers.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e8415a3920011f089d25254007c27c5.png)

3. You can refer to the following steps to create a new AppID or add the `Push Notification` `Service` to your original AppID.

> **Note** Note: Your App's `Bundle ID` cannot use wildcard `*`, otherwise Remote Push Service will be unavailable.

4. Check **App IDs**, then click **Continue** to proceed to the next step.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e40e270920011f097255254005ef0f7.png)

5. Select **App**, then click **Continue** to proceed to the next step.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f0e21b5920011f0a14552540099c741.jpeg)

6. Configure `Bundle ID` and other info, then click **Continue** to proceed to the next step.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e919b19920011f090a8525400e889b2.png)

7. Check **Push Notifications** and enable Remote Push Service.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e773327920011f097255254005ef0f7.png)

#### Generating a Certificate

1. Select your AppID, then click **Configure**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f1d7739920011f0aa79525400454e06.png)

2. You can see two `SSL Certificates` in the **Apple Push Notification service SSL Certificates** window, used for development environment (Development) and production environment (Production) remote push certificates, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e65ad08920011f087025254001c06ec.jpeg)

3. First select the development environment (Development) **Create Certificate**, the system will prompt us to provide a Certificate Signing Request (CSR).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f1504e7920011f08e0452540044a08e.png)

4. On your Mac, open **Keychain Access**, then select **Keychain Access** > **Certificate Assistant** > **Request a Certificate From a Certificate Authority** (`Keychain Access - Certificate Assistant - Request a Certificate From a Certificate Authority`).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d954f712a5a911f09936525400e889b2.png)

5. Enter the user email address (your mailbox), common name (Your Name or company name), select **Save to Disk**, click **Continue**, and the system will generate a `*.certSigningRequest` file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e40d8ea5a5a911f0930a5254007c27c5.png)

6. Go back to the webpage on the Apple Developer website in [Step 3](https://www.tencentcloud.com/document/product/1047/60548#step3), click **Choose File** to upload the generated `*.certSigningRequest` file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e7698d5920011f0bdaa525400bf7822.png)

7. Click **Continue** to generate the Push Certificate.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f358753920011f097255254005ef0f7.png)

8. Click **Download** to download the `Development SSL Certificate` for the development environment locally.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1eb26fb6920011f0aa79525400454e06.jpeg)

9. Repeat steps 1-8 to download the `Production SSL Certificate` for the production environment locally.

> **Note**Note: The cert in the production environment is actually a merged certificate of Sandbox and Production, which can be used as the cert for both development and production environments.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/200c0124920011f087025254001c06ec.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1ebd35f0920011f090a8525400e889b2.png)

10. Double-click to open the downloaded `SSL Certificate` for development and production environments, and the system will import it into the Keychain.
11. Open the keychain access app, go to **Login** > **My Certificates**, right-click and export the newly created `Apple Development IOS Push Service` and `Apple Push Services` `P12` files for development and production environments respectively.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f3a17f05a5a911f0a90152540099c741.png)

> **Note**When saving a `P12` file, ensure to set password for it.

### Step 2: Upload Certificate to Console

1. Sign in to the [Chat Console](https://console.trtc.io/chat/push-plugin-push-identifier).
2. Click the target application card to enter the basic configuration page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fcb5bd37a5a911f091df5254005ef0f7.png)

3. Click **iOS Native Offline Push Settings** on the right **add certificate**.
4. Select certificate type, upload iOS certificate (.p12), set certificate password, click **confirm**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/05d26942a5aa11f09936525400e889b2.png)

> **Note**Use English for the certificate name (do not use parentheses or other special characters).Upload certificate needs to be set with password. Passwordless will not receive push notifications.To publish an App Store certificate, set it to production environment, otherwise unable to receive push.Uploaded p12 certificate must be a real and valid certificate applied by yourself.

5. After generation of pending certificate information, record the cert ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12ff76bca5aa11f0a90152540099c741.png)

## Operation Steps

### Step 1: Register Application to Manufacturer Push Platform

Offline push requires registering your own application to various manufacturers' push platforms to get parameters such as AppID and AppKey, enabling offline push functionality. Currently supported domestic mobile manufacturers include: [Xiaomi](https://dev.mi.com/console/doc/detail?pId=68), [Huawei](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/service-introduction-0000001050040060), [Honor](https://developer.hihonor.com/cn/kitdoc?category=&kitId=11002), [OPPO](https://open.oppomobile.com/wiki/doc#id=10195), [VIVO](https://dev.vivo.com.cn/documentCenter/doc/281), [Meizu](https://open.flyme.cn/service/3), with overseas support for [Google FCM](https://console.firebase.google.com/u/0/?hl=zh-cn).

### Step 2: Chat Console Configuration

Sign in to the [Chat console](https://console.trtc.io/chat/push-plugin-push-identifier), go to the **push management** > **access setting** feature section, add push certificates for various manufacturers, and configure the AppId, AppKey, AppSecret and other parameters obtained from step 1 for the added push certificates.

> **Note:**Note: For the **click subsequent actions** option, if you need to use the click redirect power provided by this Plugin, keep default values unchanged, usually `open a specified page within the app` with default configuration. If you need to use the report statistics feature, keep this item unchanged.

Xiaomi

Huawei

OPPO

vivo

Meizu

Honor

Google FCM

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1e792f59920011f0aa79525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/37ff8c7ba5aa11f0bf2352540044a08e.png) |

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/201ab41f920011f090a8525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3cb79315a5aa11f0bf2352540044a08e.png)**Note:**Client ID corresponds to AppID, and Client Secret corresponds to AppSecret. |

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f410530920011f090a8525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/426327dca5aa11f0bf2352540044a08e.png) |

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1faf21fc920011f0a14552540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/46ac087ba5aa11f0b1565254001c06ec.png) |

**Receipt configuration**

**Receipt Address:**

- Singapore :https://apisgp.im.qcloud.com/v3/offline_push_report/vivo
- Korea:https://apikr.im.qcloud.com/v3/offline_push_report/vivo
- USA: https://apiusa.im.qcloud.com/v3/offline_push_report/vivo
- Germany: https://apiger.im.qcloud.com/v3/offline_push_report/vivo
- Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/vivo
- China: https://api.im.qcloud.com/v3/offline_push_report/vivo

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1fefbffe920011f090a8525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/51e445e7a5aa11f091df5254005ef0f7.png) |

**Receipt configuration**

**Receipt Address:**

- Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/meizu
- Korea: https://apikr.im.qcloud.com/v3/offline_push_report/meizu
- USA: https://apiusa.im.qcloud.com/v3/offline_push_report/meizu
- Germany: https://apiger.im.qcloud.com/v3/offline_push_report/meizu
- Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/meizu
- China: https://api.im.qcloud.com/v3/offline_push_report/meizu

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1eab4fbf920011f0a14552540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6048b3c5a5aa11f0b1565254001c06ec.png) |

#### Receipt configuration

**Receipt Address:**

- Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/honor
- Korea: https://apikr.im.qcloud.com/v3/offline_push_report/honor
- USA: https://apiusa.im.qcloud.com/v3/offline_push_report/honor
- Germany: https://apiger.im.qcloud.com/v3/offline_push_report/honor
- Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/honor
- China: https://api.im.qcloud.com/v3/offline_push_report/honor

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f673c84920011f0a14552540099c741.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/69b39e3da5aa11f09936525400e889b2.png) |


---
*Source: [https://trtc.io/document/73890](https://trtc.io/document/73890)*
