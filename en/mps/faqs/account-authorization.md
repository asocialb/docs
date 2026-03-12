# Account Authorization

If your account permissions are insufficient, you may not be able to use MPS normally, which is more likely to occur when sub-accounts are used. This document describes common scenarios of insufficient permissions and corresponding solutions.

## Scenario 1 (Required): MPS Service Not Enabled for an Account

If the MPS service is not enabled for your account, you cannot use MPS normally. In this case, you need to enable the MPS service first before using the MPS console or calling APIs. **This operation is required**.

### Solution

- Contact the owner of the **root account**, log in to the root account, go to the [MPS console](https://console.tencentcloud.com/mps/index), and click **Activate For Free**.
- If a sub-account has full read/write permissions for MPS (see [Scenario 2](#mpsfullaccess) to associate the QcloudMPSFullAccess preset policy), you can directly enable MPS under the sub-account.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/474c1881190311f09bd7525400e889b2.png)

## Scenario 2 (Required): No MPS Operation Permissions for a Sub-account

If the root account does not grant read/write operation permissions for MPS to your sub-account, the sub-account cannot use MPS normally.

- At this time, the error below will be reported when you use the sub-account to access the MPS console:

![The message in the pop-up window indicates that the sub-account does not have permission for the "DescribeUserInfo" API of MPS.](https://staticintl.cloudcachetci.com/cms/backend-cms/a45e7ec4190811f09240525400bf7822.png)

- The error below will be reported if you use the sub-account to call the APIs of MPS:

![The error message indicates that the sub-account has no operation permissions.](https://staticintl.cloudcachetci.com/cms/backend-cms/15d4a4f3190911f0b5c65254001c06ec.png)

To solve this issue, you can follow any of the solutions below to grant MPS operation permissions to your sub-account. **This operation is required.**

### Solution

#### Solution 1: Associate the Sub-account with the QcloudMPSFullAccess Preset Policy (Recommended)

1. Contact the root account owner and log in to the root account.
2. Go to [Cloud Access Management](https://console.tencentcloud.com/cam) under the root account, find the sub-account that needs to use MPS in the **User List,** and click **Authorize**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7d4a9582160711f09bd7525400e889b2.png)

3. Search for "QcloudMPSFullAccess" and grant the permission of the QcloudMPSFullAccess preset policy to the sub-account.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/51712b08160711f08ac55254007c27c5.png)

#### Solution 2: Associate the Sub-account with a Custom Policy

> **Note:**Currently, only QcloudMPSFullAccess is the preset policy of MPS. This full read/write policy allows sub-accounts to access all APIs of MPS. If the root account hopes to limit the API access permissions of sub-accounts for security purposes, it can associate a custom policy with sub-accounts.

1. Go to [Cloud Access Management](https://console.tencentcloud.com/cam/policy) under the root account and click **Create Custom Policy** on the **Policies** page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/af4ff670160711f09240525400bf7822.png)

2. Select **Create by policy builder**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2d90e714190911f08ac55254007c27c5.png)

3. Under 'Service', select the **Media Processing Service (mps)**. Then, under 'Action', select the MPS APIs permitted for sub-accounts. Multiple APIs can be selected at a time.

> **Note:**The RequestFromSdk API should be selected if you are using the SDK.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/98ddb736190911f09240525400bf7822.png)

4. Under 'Resource', Select **All resources** and click **Next**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6327f446190a11f09bd7525400e889b2.png)

5. Enter a policy name, associate the policy with your sub-account in the "Grant this permission to users" field, and click **Done**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8aa807db190a11f0b5c65254001c06ec.png)

6. Return to the **Policies** page. You can view all custom policies on this page and click a policy name to modify the corresponding policy later.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9cac8bc1190a11f0b5c65254001c06ec.png)

## Scenario 3 (Optional): MPS Not Authorized to Perform Necessary Read/Write Operations on Files in Your Buckets

Currently, Media Processing Service supports four types of input file sources: Tencent Cloud Object Storage (COS), Tencent Cloud [VOD Pro](https://www.tencentcloud.com/document/product/266/67978), AWS S3, and downloadable URLs.

- **To utilize COS as the file source, COS authorization must be completed beforehand.** Create the `MPS_QcsRole` service role to grant Media Processing Service read and write permissions, including downloading, transcoding, and uploading files from your COS bucket.
- **To utilize**[VOD Pro](https://www.tencentcloud.com/document/product/266/67978)**as the file source, VOD authorization must be completed beforehand.** Create the `MPS_QCSLinkedRoleInVOD` service role to grant Media Processing Service read and write permissions, including downloading, transcoding, and uploading files from your VOD Pro bucket.
- If you intend to use AWS S3 or a URL as the file source, COS authorization can be skipped.

If you initiate a processing task via the MPS API without completing the required authorization for COS or VOD Pro buckets, the task will fail. An example is illustrated below:

![First, call the ProcessMedia API to process files in a COS bucket:](https://staticintl.cloudcachetci.com/cms/backend-cms/54a1eef6190f11f0b04252540044a08e.png)

![Then, use the 'TaskId' to check the task status, where you will encounter an error:](https://staticintl.cloudcachetci.com/cms/backend-cms/a3170ce9191011f09bd7525400e889b2.png)

### Solution

To utilize COS, log in to the **root account**, enter the overview page of the [MPS console](https://console.tencentcloud.com/mps/index), click **COS Authorization**, and click **Authorize** in the pop-up window. After authorization is completed, the `MPS_QcsRole` service role will be automatically created in [Cloud Access Management > Role](https://console.tencentcloud.com/cam/role).

Similarly, if you wish to utilize VOD Pro, simply click **VOD Authorization** to create the `MPS_QCSLinkedRoleInVOD` service role.

> **Note:**This authorization operation **does not require enabling COS or VOD and will not incur COS or VOD fees**. It just allows MPS to obtain the necessary API read/write permissions for COS or VOD buckets.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/33ea794bc8e711f09e745254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3e5f6088c8e711f08942525400e889b2.png)

## Scenario 4 (Optional): No cam:GetRole Permission for a Sub-account

After permission authorization in the above three scenarios is completed, the error message below may pop up when you use a sub-account to log in to the MPS console:

![The message in the pop-up window indicates that the sub-account has no cam:GetRole permission.](https://staticintl.cloudcachetci.com/cms/backend-cms/5ef0287c191111f091eb525400454e06.png)

This is because the MPS console frontend will call the GetRole API of Tencent Cloud Access Management (CAM) to query whether the user has the MPS_QcsRole service role. The frontend assesses whether an authorization prompt is given according to the query result. If the sub-account has no cam:GetRole permission, the MPS console frontend cannot call the GetRole API to query the role. As a result, a window indicating such an error pops up.

> **Note:**GetRole involves a frontend operation of the MPS console. The sub-account cannot use the MPS console normally if it has no cam:GetRole permission. APIs can still be called. The console helps you complete MPS operations and view task results. Therefore, it is recommended that you follow the solution below to grant the cam:GetRole permission to the sub-account.

### Solution

1. Contact the root account owner and log in to the root account.
2. Go to [Cloud Access Management > Policy](https://console.tencentcloud.com/cam/policy) under the root account, click **Create Custom Policy**, and select **Create by policy generator** to create a custom policy.

Select Cloud Access Management (CAM) for Service, GetRole as the read operation, and All resources, as shown in the red box below. Then, click **Next**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/98039f08191111f09bd7525400e889b2.png)

3. Enter a policy name, grant this permission to the sub-account that needs to use MPS, and click **Complete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/aab7638b191111f0897952540099c741.png)


---
*Source: [https://www.tencentcloud.com/document/product/1041/69220](https://www.tencentcloud.com/document/product/1041/69220)*
