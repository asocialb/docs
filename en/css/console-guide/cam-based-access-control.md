# CAM-Based Access Control

CSS supports permission control via CAM, allowing you to manage access to your CSS domains, settings, and other data. You can create, manage, or terminate users or user groups and grant API access permissions to them to achieve identity management and policy control.
You can use CAM to bind a user or user group to a policy which allows or denies them access to specified resources to complete specified tasks.

## Concepts

- Root account: A Tencent Cloud account
- Sub-user: A user created and fully owned by a root account.
- Collaborator: You can add another root account as a collaborator to your account. The added account becomes a sub-account of your account.
- User group: Users that perform the same functions and can be bound with a permission policy for centralized access management.

> **Note:**For more information on the concepts and permissions, see [User Types](https://tencentcloud.com/document/product/598/32633).

## Directions

### Step 1. Create a sub-user or user group

One or more sub-users can be created under each root account and can be associated with specific roles and policies. A sub-user has a unique ID and identity credential that can be used to log in to the Tencent Cloud console. It also has API access. You can log in to the [CAM console](https://console.tencentcloud.com/cam/) to create a sub-user.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/933d84158b8711efac345254002693fd.png)

> **Note:**For detailed directions, see [Creating Sub-user](https://intl.cloud.tencent.com/document/product/598/13674) and [Creating User Group](https://intl.cloud.tencent.com/document/product/598/33380).

### Step 2. Add a policy to the sub-user or user group

You can associate policies on the user/user group management page or policy management page. For detailed directions, see [Authorization Management](https://intl.cloud.tencent.com/document/product/598/10602).

Method 1. Add a policy to a sub-user or user group

Method 2. Associate a policy with a user/user group

Go to the user/user group page and select the user/user group to which you want to add a policy.

- Select **Users > User List** or **User Groups** on the left sidebar of the CAM console. Find the user/user group to which you want to add a policy, click **Authorize** on the right, select a CSS policy, and click **OK**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d12085a48b8811ef9ba5525400f69702.png)

- Select **Users > User List** or **User Groups** on the left sidebar and click the name of the user/user group to which you want to add a policy. Click **Associate Policy**, select a CSS policy, and click **OK**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2de5af908b8911ef9ed652540075b605.png)

Select **Policies** on the left sidebar of the CAM console, find the policy you want to associate, and click **Associate User/User Group/Role** in the **Operation** column. Select the user/user group you want to associate the policy with, and click **OK**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/889c49f48b8911efa11a525400a9236a.png)

#### Addable policies

- **Preset policies**: You can view all preset policies on the **Policies** page.
  - CSS preset policies include [QcloudLIVEFullAccess](https://console.tencentcloud.com/cam/policy/detail/9545933&QcloudLIVEFullAccess&2) (read and write policy) and [QcloudLIVEReadOnlyAccess](https://console.tencentcloud.com/cam/policy/detail/13346800&QcloudLIVEReadOnlyAccess&2) (read-only policy).
  - For a user to use tags, you need to associate [QcloudTAGFullAccess](https://console.tencentcloud.com/cam/policy/detail/1592575&QcloudTAGFullAccess&2) (full read and write access by tag).
  - For a user to use real-time logs, associate [QcloudCamFullAccess](https://console.tencentcloud.com/cam/policy/detail/596169&QcloudCamFullAccess&2) (full read/write access to CAM).
  - To use the screenshot & porn detection feature, associate [QcloudAccessFoLVBRoleInSaveLiveScreenshottoCOS](https://console.tencentcloud.com/cam/policy/detail/115867019&QcloudAccessFoLVBRoleInSaveLiveScreenshottoCOS&2) with your CSS service role to grant it access to COS.
- **Custom policy**: Go to the **Policies** page, click **Create Custom Policy**, and select **Create by Policy Generator**. For more information, see [Custom Policy](https://intl.cloud.tencent.com/document/product/598/10601).

> **Note:**Currently, some APIs of CSS support resource-level authorization.

**Example:** If you want to allow a sub-user to use the **DescribeLiveDomains** API, follow the steps below to grant the permission.

  1.1. Create a domain-level policy that allows access to the API: Go to the **Create by Policy Generator** page and complete the following settings:

| Item | Required | Setting |
| --- | --- | --- |
| Effect | Yes | Select Allow |
| Service | Yes | Select Cloud Streaming Services |
| Action | Yes | Select DescribeLiveDomains |
| Resource | Yes | Select all resources or specific resources.Tencent Cloud services for which the authorization granularity is operation or service don't support six-segment resource descriptions; for them, select “All resources”. For Tencent Cloud services that support resource-level authorization, you can select specific resources. For the resource description method and authorization granularity of Tencent Cloud services, see [CAM-Enabled Products](https://intl.cloud.tencent.com/document/product/598/10588). |
| Condition | No | Set the condition for the authorization to take effect. If you enter IP addresses, the API will be accessible only if a request is from the specified IP range. You can also add other conditions. For more information, see [Conditions](https://www.tencentcloud.com/document/product/598/58420). |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9f52151e8b8a11ef9ba5525400f69702.png)

> **Note:**If you want to authorize multiple services, click **Add Permissions**.

  1.2. Click **Next** to generate the policy. Then, associate it using either of the two methods above.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/eccf15518b8a11efa11a525400a9236a.png)

### Step 3. Use a sub-account

You can now use the sub-user’s account (the account ID and password) to call the API authorized (such as `DescribeLiveDomains`) and get the corresponding CSS data (such as all the domains under the current account).


---
*Source: [https://www.tencentcloud.com/document/product/267/32468](https://www.tencentcloud.com/document/product/267/32468)*
