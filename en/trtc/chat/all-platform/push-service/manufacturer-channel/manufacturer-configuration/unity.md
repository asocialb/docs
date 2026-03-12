# Unity

Currently, the message push plugin in Unity only supports push to Android (including manufacturer channels) and iOS devices.

iOS

Android

Before integrating the message push plug-in, you must apply for an APNs Push Certificate from Apple and then upload the Push Certificate to the Chat console. Afterward, follow the quick integration procedure to complete the setup.

## Operation Steps

### Step 1: Apply for an APNs Certificate

#### Enable Remote App Push

1. Log in to the [Apple Developer Center](https://developer.apple.com/account/) website, click **Certificates, Identifiers & Profiles** or **Certificates, IDs & Profiles** in the sidebar, and enter the **Certificates, IDs & Profiles** page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c3ca1410943911f089d25254007c27c5.jpeg)

2. Click **+** on the right of Identifiers.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c402b242943911f0a14552540099c741.png)

3. You can refer to the following procedure to create a new AppID, or add the `Push Notification` `Service` to your original AppID.

> **Note** Note: The `Bundle ID` of your App cannot use wildcard `*`, otherwise the Remote Push Service will be unavailable.

4. Check **App IDs**, click **Continue** to proceed to the next step.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c3f3977c943911f090a8525400e889b2.png)

5. Select **App**, click **Continue** to proceed to the next step.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c3ea1fb9943911f086065254001c06ec.jpeg)

6. Configure `Bundle ID` and other info, then click **Continue** to proceed to the next step.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c3f63bae943911f0a14552540099c741.png)

7. Check **Push Notifications** and enable Remote Push Service.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c3e9dee0943911f090a8525400e889b2.png)

#### Generating a Certificate

1. Select your AppID, choose **Configure**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c475e37d943911f0aa79525400454e06.png)

2. In the **Apple Push Notification service SSL Certificates** window, you can see two `SSL Certificates`, respectively for remote push certificates in development environment (Development) and production environment (Production), as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c45f0681943911f0a14552540099c741.jpeg)

3. First select the development environment (Development) **Create Certificate**, the system will prompt you to provide a Certificate Signing Request (CSR).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c44bb103943911f08e0452540044a08e.png)

4. On your Mac, open **Keychain Access**, select **Keychain Access** > **Certificate Assistant** > **Request a Certificate From a Certificate Authority** (`Keychain Access - Certificate Assistant - Request a Certificate From a Certificate Authority`).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/41047ed8a5a811f0b8b9525400454e06.png)

5. Enter the user email address (your mailbox), common name (Your Name or company name), select **save to disk**, click **continue**, and the system will generate a `*.certSigningRequest` file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4b8f58d3a5a811f0b8b9525400454e06.png)

6. Go back to the webpage on the Apple Developer website in [Step 3](https://www.tencentcloud.com/document/product/1047/60548#step3), click **Choose File** to upload the generated `*.certSigningRequest` file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c425a997943911f086065254001c06ec.png)

7. Click **Continue** to generate the push certificate.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4156198943911f08e0452540044a08e.png)

8. Click **Download** to download the `Development SSL Certificate` for the development environment locally.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c404f330943911f0a14552540099c741.jpeg)

9. Repeat steps 1 - 8 to download the `Production SSL Certificate` for the production environment to local.

> **Note**The certificate in the production environment is a merged certificate of development (Sandbox) and production (Production), which can be used as both a development and production environment certificate.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4565030943911f0bdaa525400bf7822.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4364c44943911f090a8525400e889b2.png)

10. Double-click to open the downloaded `SSL Certificate` for the development and production environment, and the system will import it into the keychain.
11. Open the keychain access app, go to **Login** > **My Certificates**, right-click to export the newly created `P12` files for the development environment (`Apple Development IOS Push Service`) and production environment (`Apple Push Services`).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6a7c0b64a5a811f0b1565254001c06ec.png)

> **Note**When saving the `P12` file, ensure to set a password for it.

### Step 2: Upload Certificate to Console

1. Log in to the [Chat console](https://console.trtc.io/chat/push-plugin-push-identifier).
2. Click the target application card to enter the basic configuration page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7b8c7d46a5a811f0bf2352540044a08e.png)

3. Click **iOS Native Offline Push Settings** on the right **add certificate**.
4. Select certificate type, upload iOS certificate (.p12), set certificate password, click **confirm**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/94381ec2a5a811f0872c525400bf7822.png)

> **Note**Upload certificate name should be in English (do not use parentheses or other special characters).Upload certificate needs to be set with password. Passwordless will not receive push notifications.Set the certificate for App Store release to production environment, otherwise unable to receive push notifications.Uploaded p12 certificate must be your own real and valid applied certificate.

5. After generation of pending certificate information, record the cert ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a4797725a5a811f0930a5254007c27c5.png)

## Operation Steps

### Step 1: Register Application to Manufacturer Push Platform

Offline push requires registering your own application to various manufacturers' push platforms to obtain AppID and AppKey parameters such as, enabling offline push functionality. Currently supported domestic mobile manufacturers include: [Xiaomi](https://dev.mi.com/console/doc/detail?pId=68), [Huawei](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/service-introduction-0000001050040060), [honor](https://developer.hihonor.com/cn/kitdoc?category=&kitId=11002), [OPPO](https://open.oppomobile.com/wiki/doc#id=10195), [VIVO](https://dev.vivo.com.cn/documentCenter/doc/281), [Meizu](https://open.flyme.cn/service/3), with overseas support for [Google FCM](https://console.firebase.google.com/u/0/?hl=zh-cn).

### Step 2: Chat Console Configuration

Log in to Tencent Cloud [Chat console](https://console.trtc.io/chat/push-plugin-push-identifier), go to **Push Management** > **Access Setting** feature section, add push certificates from various manufacturers, and configure the AppId, AppKey, AppSecret and other parameters obtained from step 1 for the added certificates.

> **Note:**Note: For the **click subsequent actions** option, if you need to use the click redirect capacity provided by this Plugin, keep default values unchanged, usually `open a specified page within the app` with default configuration. If you need to use the report statistics feature, keep this item unchanged.

Xiaomi

Huawei

OPPO

vivo

Meizu

Honor

Google FCM

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4837e0c943911f090a8525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bfc1971fa5a811f0872c525400bf7822.png) |

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4aea03b943911f08e0452540044a08e.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ce30b272a5a811f0bf2352540044a08e.png)**Note:**Client ID corresponds to AppID, and Client Secret corresponds to AppSecret. |

#### Receipt configuration

**Receipt Address:**

- Singapore : https://apisgp.im.qcloud.com/v3/offline_push_report/huawei
- Korea: https://apikr.im.qcloud.com/v3/offline_push_report/huawei
- USA: https://apiusa.im.qcloud.com/v3/offline_push_report/huawei
- Germany: https://apiger.im.qcloud.com/v3/offline_push_report/huawei
- Indonesia: https://apiidn.im.qcloud.com/v3/offline_push_report/huawei
- China: https://api.im.qcloud.com/v3/offline_push_report/huawei

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c472004e943911f090a8525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d8ad3d1ea5a811f0b8b9525400454e06.png) |

| Vendor Push Platform | Chat Console Configuration |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c47b37c6943911f0aa79525400454e06.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e18f6534a5a811f091df5254005ef0f7.png) |

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
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4968a8b943911f086065254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/326f2357a5a911f0930a5254007c27c5.png) |

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
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c4ababf5943911f097255254005ef0f7.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/469ede31a5a911f0872c525400bf7822.png) |

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
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c46cbf80943911f0bdaa525400bf7822.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/571ee104a5a911f0872c525400bf7822.png) |


---
*Source: [https://trtc.io/document/73798](https://trtc.io/document/73798)*
