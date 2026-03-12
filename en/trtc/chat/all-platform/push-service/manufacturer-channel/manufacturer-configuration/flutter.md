# Flutter

Currently, the message push plugin in Flutter only supports pushing to Android (including various vendor channels) and iOS devices.

iOS

Android

Before integrating the Message Push plugins, you need to apply for an APNs Push Certificate from Apple, then upload the push certificate to the Chat Console. After that, follow the Quick Integration steps to proceed.

## Operation step

### Step 1: Apply for an APNs certificate

#### Activate remote push for the app

1. Log in to  [Apple Developer Center](https://developer.apple.com/account/) website, click  **Certificates, Identifiers & Profiles** or the sidebar's **Certificates, IDs & Profiles**, to enter **Certificates, IDS & Profiles** page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8792b4acb2d611ef96e55254002693fd.jpeg)

2. Click  Identifiers on the right-side **+**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/73e2214dc1da11ef87c05254005ef0f7.png)

3. You can follow the steps below to create a new AppID, or add a `Push Notification` service to your existing AppID .

> **Note:** Your App's `Bundle ID` cannot use a wildcard `*`, otherwise, remote push service will not be available.

4. Select **App IDs**, click  **Continue** to proceed with Next .

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87da6030b2d611ef8b1b525400f69702.png)

5. Choose **App**, click  **Continue** to proceed with Next .

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87886afab2d611ef970f525400d5f8ef.jpeg)

6. Configure `Bundle ID` and other information, click  **Continue** to proceed with Next .

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/86f4509fb2d611efa2e952540075b605.png)

7. Select **Push Notifications** to activate remote push service.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/86f99927b2d611ef9dc0525400329841.png)

#### Generating Certificate

1. Select your AppID, choose **Configure**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87f03292b2d611ef96e55254002693fd.png)

2. You can see in the  **Apple Push Notification service SSL Certificates**  window, there are two  `SSL  Certificate`, one for the development environment (Development) and the other for the production environment (Production) remote push certificate, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/872fe9b4b2d611ef970f525400d5f8ef.jpeg)

3. First, we choose the Development **Create Certificate**; the system will prompt us that a Certificate Signing Request (CSR) is required.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/870b0abcb2d611efa2e952540075b605.png)

4. Open **Keychain Access** on your Mac, in the menu, select **Keychain Access** > **Certificate Assistant** > **Request a Certificate From a Certificate Authority** (`Keychain Access - Certificate Assistant - Request a Certificate From a Certificate Authority`).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7fef62f4c1cb11efabd3525400bdab9d.png)

5. Enter the user's Email address (your email), Common Name (your name or company name), select **Save to disk**, click **continue**, and the system will generate a `*.certSigningRequest` file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8a2a279cc1cb11ef95c1525400d5f8ef.png)

6. Return to the page on the Apple Developer website you were just at in step 3 of the above instructions, click **Choose File** to upload the `*.certSigningRequest` file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87095162b2d611ef9d2952540055f650.png)

7. Click **Continue** to generate the push certificate.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87284e76b2d611ef9dc0525400329841.png)

8. Click **Download** to download the `Development SSL Certificate` to your local machine.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87a68a70b2d611efa2e952540075b605.jpeg)

9. Follow the steps 1 - 8 above again to download the `Production SSL Certificate` to your local machine.

> **Indication**Actually, this certificate is a Sandbox and Production merged certificate that applies to both the development and production environments.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87e7396eb2d611efa2e952540075b605.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87ce29a0b2d611ef8b1b525400f69702.png)

10. Double-click the downloaded `SSL Certificate` for the development and production environments. The system will import it into the keychain.
11. Open the Keychain Access app, go to **Login** > **My Certificates**, and right-click to export the newly created development environment (`Apple Development IOS Push Service`) and production environment (`Apple Push Services`) `P12` files respectively.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9ceacb19c1cb11ef9beb525400fdb830.png)

> **Noteï¼**When saving the `P12` file, make sure to set a password.

### Step 2: Upload the certificate to the console

1. log in  [Chat  Console](https://console.trtc.io/chat/push-plugin-push-identifier).
2. Click the target app card to go to the basic configuration page of the app.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa68214fc1cb11ef95c1525400d5f8ef.png)

3. Click  **iOS native offline push settings** on the right, click **Add Certificate**.
4. Select the certificate type, upload the iOS certificate (p12), set the certificate password, and click **Confirm**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af5fecaac1cb11efbeb4525400f69702.png)

> **Note:**We recommend naming the uploaded certificate in English (special characters such as brackets are not allowed).You need to set a password for the uploaded certificate. Without a password, push notifications cannot be received.For an app published on App Store, the environment of the certificate must be the production environment. Otherwise, push notifications cannot be received.The uploaded .p12 certificate must be your own authentic and valid certificate.

5. After the push certificate information is generated, record the certificate ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b402fdfdc1cb11ef80ba52540055f650.png)

## Operation step

### Step 1. Register your app with vendor push platforms

Offline push requires registering your app with each vendor's push platform to obtain parameters such as AppID and AppKey to achieve the offline push feature. Currently, mobile phone vendors supported inside the Chinese mainland are [Mi](https://dev.mi.com/console/doc/detail?pId=68), [Huawei](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/service-introduction-0000001050040060), [HONOR](https://developer.hihonor.com/cn/kitdoc?category=&kitId=11002), [OPPO](https://open.oppomobile.com/wiki/doc#id=10195), [vivo](https://dev.vivo.com.cn/documentCenter/doc/281), and [Meizu](https://open.flyme.cn/service/3), and the mobile phone vendor supported outside the Chinese mainland is [Google FCM](https://console.firebase.google.com/u/0/).

### Step 2. Create resources in the Chat console

Log in to Tencent Cloud [Chat Console](https://console.trtc.io/chat/push-plugin-push-identifier), then in the **Push Management** > **Access Settings** feature section, add each vendor's push certificate, and configure the AppID, AppKey, AppSecret, and other parameters obtained in Step 1 to the added push certificate.

Explanation of the **Subsequent Actions** option:

- Open Application: Clicking the notification bar launches the app, by default starting the app's Launcher interface;
- Open Web Page: Clicking the notification bar will redirect to the configured web link;
- Open the specified interface within the app: clicking the notification bar will redirect the interface based on the configured self Definition, see [Custom Redirect on Click](https://www.tencentcloud.com/zh/document/product/1047/60575).

Mi

Huawei

OPPO

vivo

Meizu

HONOR

Google FCM

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/878a3ed1b2d611efbfb3525400bdab9d.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/875513a1b2d611ef9d2952540055f650.png) |

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/874f3bf5b2d611ef970f525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/876d798cb2d611ef970f525400d5f8ef.png) **Note:**Client ID corresponds to AppID, Client Secret corresponds to AppSecret. |

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/881e4941b2d611ef8c01525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/88077824b2d611ef8c01525400fdb830.png) |

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8813a72bb2d611ef970f525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/874aff04b2d611ef9dc0525400329841.png) |

For receipt configuration, please refer to: [Message Delivery Statistics Configuration - vivo](https://www.tencentcloud.com/zh/document/product/1047/60555?lang=zh#d725ba03-4c2e-41fb-a247-6b4b3afa96f0).

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/876785c8b2d611ef970f525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87e73042b2d611ef9d2952540055f650.png) |

For receipt configuration, please refer to: [Message Delivery Statistics Configuration - Meizu](https://www.tencentcloud.com/zh/document/product/1047/60555?lang=zh#d725ba03-4c2e-41fb-a247-6b4b3afa96f0).

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/876fa8eab2d611ef9dc0525400329841.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8843e109b2d611ef8c01525400fdb830.png) |

| Vendor Push Platform | Configuring in the Chat console |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ccea44a2c1cb11ef9beb525400fdb830.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/882d45bab2d611ef970f525400d5f8ef.png) |

> **Note:**Regarding **Click for Subsequent Actions** supports the Report Statistics feature:If you choose to open an app or a web page, purchasing the plugin will by default support reporting statistics.If you choose to open a specified interface within the application:For new certificate status, please directly use the auto-fill default value to support click statistics reporting.If there was a certificate configured previously, continue using the old certificate and modify it to the default value to support reporting statistics, or regenerate a new certificate.

### About FCM Data Messaging

FCM provides two push methods: Notification Message and Data Messaging.

- Notification messages have a simple style and do not differentiate between devices. Once successfully integrated, offline push can be performed.
- Data Messaging, offering rich customization for specific devices, supports reach and click reporting, and requires testing on the device before going live after integration.

The console defaults to Notification Message, and switching between modes can be done in the Chat Console:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8808396eb2d611ef970f525400d5f8ef.png)

> **Note:**FCM data messaging capability only supports TChatPush version 7.8 and above on pixel phones. Other manufacturers' devices need to be tested for support.


---
*Source: [https://trtc.io/document/60550](https://trtc.io/document/60550)*
