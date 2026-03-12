# Basic Configuration

Log in to the [Console > Chat Product Details Page](https://console.trtc.io/chat), and **select the target application at the top**. On the page, you can manage the basic configuration of the app based on your business needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a7f1eeaacaa311f0aedb525400454e06.png)

## Application Package Information

### Upgrade Package

On the [Chat product detail page](https://console.trtc.io/chat), you can see the current business package information of the application. Click **Basic information** in the **Renewal/Upgrade** section to upgrade the business package version or configuration. For details, see [Upgrading an Application](https://www.tencentcloud.com/document/product/1047/34577#.E5.8D.87.E7.BA.A7.E5.BA.94.E7.94.A8).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6654e7f1caa311f0b011525400bf7822.png)

### Disabling/Deleting an Application

Disable/Delete this application in [Application Management](https://console.trtc.io/app/app-detail).

> **Important Note: Disable or Delete Applications****Status Update Latency**: After manually disabling, re-enabling, or deleting an application, it takes **3â5 minutes for the changes to take effect** across the system.**Billing During Update**: During this 3â5 minute window, new users may still enter rooms, **and usage will be billed as usual**.Once disabled or deleted, new entries are blocked, but **billing continues for users already in**[rooms](https://trtc.io/document/37714#room). Use the [Dismiss Room](https://trtc.io/document/34269) API to force-close active rooms.**Global Impact**: Disabling or deleting an application affects all associated services, including Call, Conference, RTC Engine, Live, and Chat. A**ll services will become unavailable**.Applications in a **Enabled** state cannot be deleted directly. You must **disable the application first** before performing a deletion.**Cloud Recording Assets**: Disabling an application will not automatically delete your cloud recording files. Please manage these files via the [COS](https://console.tencentcloud.com/cos?lang=zh) or [VOD](https://console.tencentcloud.com/vod/overview?lang=zh) console.

#### **Trial Edition Application**

- Support manual deactivation: In the **Basic Information** section, click **Disable** on the right of **Status**, then click **Confirm** in the pop-up deactivation reminder dialog box to disable.
- Support manual deletion: In the **Basic Information** section, click **Delete** on the right of **Status**, then click **Confirm** in the pop-up confirmation dialog box to delete.

#### **Standard Edition, Pro Edition, Pro Edition Plus, Enterprise Edition Applications**

- Automatically changes to **disabled** status after 24 hours in arrears. If you need to delete, please [contact us](https://www.tencentcloud.com/document/product/1047/41676) to delete this application.
- Automatically changes to **disabled** status after refund. If you need to delete, please [contact us](https://www.tencentcloud.com/document/product/1047/41676) to delete this application.

> **Note:**Disable the application before deleting it.Deleting or deactivating the application will stop ALL subservices.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/710757b8caa611f0a4a55254001c06ec.png)

### Extending Trial Edition Valid Period

When the application package is Trial Edition and exceeds a one-month valid period, the application will be suspended upon expiration. To continue using **Trial Edition** for test development, you can **apply for extension** for in the console for this application.

1. Go to [console > Chat App Details Page](https://console.trtc.io/chat), **select the target application at the top**, and enter the **Overview** page of this application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/710f9578caa611f0a7775254005ef0f7.png)

2. Click **Basic Information** and then **Apply for Extension**.
3. Click **Confirm** to complete the application for extending the Trial Edition valid period by one month.

## Configure Application Information

In the **Basic Information** section, you can edit the basic information of the application, including **Application Name** and **Description**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a5fa21dacaa611f0a4a55254001c06ec.png)

### Editing Basic Information

1. Click **Edit** on the right of **Basic Info** to edit the app settings.
2. You can modify the **application name** and **description**.
3. Click **Save**.

## Configuring Basic Information

In the **Basic Information** section, you can obtain the key of this application.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e653c4afcaa611f09e745254007c27c5.png)

### Obtaining a key

**Key information is sensitive. Keep it secret to prevent leakage.**  By default, apps (SDKAppIDs) created before August 15, 2019 use the [ECDSA-SHA256](https://intl.cloud.tencent.com/document/product/1047/34385) signature algorithm that uses a public key and a private key. You can choose to update to the HMAC-SHA256 signature algorithm.

1. Click **SDKSecretKey** on the right to view your `SDKSecretKey`.
2. Click **Copy** to copy and store the key information. The key can be used to generate UserSig. For detailed operations, see [Generating UserSig](https://intl.cloud.tencent.com/document/product/1047/34385).

## Managing Offline Push Certificates

### Adding an offline push certificate

#### Adding an Android certificate

1. Visit [Console > Chat > Push > Access Setting](https://console.trtc.io/chat/push-plugin-push-identifier), under the **Android** tab, **select target platform**, and click **Add Certificate**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/45fbd77fcaa711f0a93d52540044a08e.png)

2. In the pop-up **Add Certificate** dialog box, fill in relevant parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9a59f654c91411f0a4a55254001c06ec.png)

3. Click **Confirm** to save the configuration.

#### Adding iOS Certificate

1. Visit [Console > Chat > Push > Access Setting](https://console.trtc.io/chat/push-plugin-push-identifier), under the **iOS tab**, click **Add Certificate**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fe00125ccaa711f0b011525400bf7822.png)

2. In the pop-up Add Certificate dialog box, fill in relevant parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fdf4d5cdcaa711f0a4a55254001c06ec.png)

3. Click **Confirm** to save the configuration.

### Editing an offline push certificate

1. Visit [Console > Chat > Push > Access Setting](https://console.trtc.io/chat/push-plugin-push-identifier), click **Edit** in the existing certificate section.
2. In the dialog box that pops up, modify the parameters as needed and click **Confirm** to save the configuration.

### Deleting an offline push certificate

> **Note:**Once the certificate is deleted, push messages are no longer delivered. Deleted certificates cannot be restored. Proceed with caution.

1. Visit [Console > Chat > Push > Access Setting](https://console.trtc.io/chat/push-plugin-push-identifier), click **Delete** in the existing certificate section.
2. In the pop-up confirm deletion dialog box, click **Confirm**.


---
*Source: [https://trtc.io/document/34540](https://trtc.io/document/34540)*
