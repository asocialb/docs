# Authorizing CSS to Store Screenshots in a COS Bucket

This document describes how to store screenshots or porn detection data in a COS bucket. You need to create a COS bucket, authorize CSS to store data in it, and then configure live screencapture and porn detection settings in the CSS console. After that, screenshots and porn detection data can be stored in the bucket. This feature is available in the new console.

### Creating a COS Bucket

1. Log in to the COS console and select [Bucket List](https://console.tencentcloud.com/cos5/bucket) on the left sidebar.
2. Click **Create Bucket**. In the pop-up window, enter the basic information, select a permission for the bucket, and click **Next**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dface17c8f7911ef95ae525400fdb830.png)

3. Complete the advanced configuration (optional) and click **Next**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/363b1f458f7a11ef9ba5525400f69702.png)

4. Confirm the configuration information and click **Create**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/566258088f7a11efa11a525400a9236a.png)

> **Note:**In the example above, the bucket name is `test02` (`-130****051 `is not part of the name).  Complete the above settings based on your actual needs.

5. To enable CDN acceleration.
  5.1. Click the name of your bucket or click **Configure**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e6886b278f9311ef9ed652540075b605.png)

  5.2. In the bucket list, and select **Domains and Transfer** > **Custom CDN Acceleration Domain** on the left sidebar. Click**Edit** in the Global Acceleration configuration item.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/37759c898f9611efa11a525400a9236a.png)

  5.3. Toggle on **status**, and compete the settings. For detailed directions, see [Enabling Custom CDN Acceleration Domain Name](https://www.tencentcloud.com/document/product/436/31505?lang=zh&pg=). After the configuration, click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/595a78668f9611ef9ba5525400f69702.png)

### Authorizing CSS to store screenshots in COS

1. Grant the root account `3508645126`**write access** and **read access** to the COS bucket.
  1.1. In the [Bucket List](https://console.tencentcloud.com/cos5/bucket), find the bucket you created, and click **Configure**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8c3cb1ac8f9611ef95ae525400fdb830.png)

  1.2. On the bucket configuration page, select **Permission Management** > [**Bucket ACL (Access Control List)**](https://console.tencentcloud.com/cos5/bucket/setting?type=aclconfig&anchorType=accessPermission&bucketName=text-1258968577&projectId=&path=%2F®ion=ap-guangzhou). Then, click **Add User**,

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d2fafd488f9611ef9ba5525400f69702.png)

  1.3. Select **Root account** as the user type, **enter the root account ID 3508645126.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0de7d7d98f9711efa22452540055f650.png)

  1.4. Click **save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/237bf06d8f9711ef9897525400d5f8ef.png)

  - Alternatively, in the bucket list, click **Manage Permissions**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7d743c448f9711ef95ae525400fdb830.png)

    - Select the bucket you created, Then, click **Add User**, select **Root account** as the user type, enter the root account ID `3508645126`, click **Save** to save the configuration, and then click **OK**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/edd681bb8f9711ef9ba5525400f69702.png)

> **Note:**`3508645126`**is the**`APPID`**of CSS. You need to enter this ID for the authorization to succeed.**

  1.5. For information about how to use an API to set bucket access, see [PUT Bucket acl](https://intl.cloud.tencent.com/document/product/436/7737).
2. Get the information of the COS bucket to which CSS is granted access.
  2.1. Select the authorized bucket in the**Bucket list**and click the **Bucket Name** on the left to enter the Overview.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1d2739b08f9811ef9ed652540075b605.png)

  2.2. All COS information can be viewed in the [Overview](https://console.intl.cloud.tencent.com/cos/bucket) of the bucket.You can find in the endpoint the bucket name, COS APPID, and bucket region.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7e0e5e4b8f9811efac345254002693fd.png)

  - Bucket name: `test02`
  - COS appid: `130****051`
  - Bucket region: `ap-guangzhou`
  2.3. Provide the above information to CSS and the system will store live screenshots in the COS bucket you created.


---
*Source: [https://www.tencentcloud.com/document/product/267/33384](https://www.tencentcloud.com/document/product/267/33384)*
