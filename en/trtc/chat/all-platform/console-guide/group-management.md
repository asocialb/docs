# Group Management

Log in to the [Chat console](https://console.trtc.io), select **Chat >**[**Groups**](https://console.trtc.io/chat/qun-manage) in the left sidebar, and **select target application** at the top. You can manage groups based on actual business needs.

Alternatively, you can call relevant RESTful APIs to manage groups. For more information, see the [Group Management API Documentation](https://intl.cloud.tencent.com/document/product/1047/34960).

## Adding Groups

1. On the **Group Management** page, click **Add Group**.
2. Configure the following parameters in the pop-up dialog box for adding a group:
  - Group Name: Enter the name of the group. This is a required parameter, and the length cannot exceed 30 bytes.
  - Group Owner ID: Enter the ID of the group owner. This is an optional parameter. You must enter the name of a registered user.
  - Group Type: Set the group type, which can be Work, Public, Meeting, or Audio-video Group. For more information on group types, see [Group Types](https://intl.cloud.tencent.com/document/product/1047/33529).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/66132af7cb3711f087ad52540099c741.png)

3. Click **OK** to save the configuration.
 After creating the group, you can view the group ID, group name, group owner, group type, and creation time of the group in the group list.

## Viewing Group Details

On the **Group Management** page, you can click **Learn more** in the row of the target group to go to the **Group Details** page, where you can view and modify the basic information of the group and manage group members.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cc97f5747b1311efb9d8525400f69702.png)

### Modifying basic information

1. On the **Group Details** page, click **Edit** in the basic information area.
2. In the pop-up dialog box for modifying group information, you can modify the group name and group introduction.
 ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dfc49f3b7b1311ef82535254002693fd.png)
3. Click **Confirm** to save the configuration.

### Managing group members

**Adding a group member**

1. On the **Group Details** page, click **Add Member** in the group member management area.
2. In the pop-up dialog box for adding members, enter the username.

> **Note:** You must enter the name of a registered user.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e71effdd7b1311efa87e52540055f650.png)

3. Click **Confirm** to save the configuration. After adding a group member, you can view the username, nickname, join time, last speak time, and role of the member on the group member list.

**Deleting a group member**

1. On the **Group Details** page, you can delete group members in the following ways:
  - Delete a single member: Click **Delete** in the row of the target member.
  - Delete a batch of members: Select the members to be deleted and click **Delete Members** above the group member list.
2. In the pop-up dialog box, click **Confirm**.
 After deletion, the selected members will no longer belong to the group.

## Sending Messages

1. On the **Group Management** page, you can send messages in the following ways:
  - Send a message to a single group: Click **Send Messages** in the row of the target group.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fe002e7a7b1311ef8631525400a9236a.png)

  - Send a message to multiple groups: Select the target groups to which you want to send a message and click **Send Messages** above the group list.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/06a073607b1411ef852f52540075b605.png)

2. In the pop-up dialog box for sending a group message, enter the message content.

> **Note:** The message length cannot exceed 300 characters.

3. Click **OK** to send the message.

## Deleting Groups

**After a group is deleted, all its information will be deleted and cannot be recovered. Please exercise caution when deleting groups.**

1. On the **Group Management** page, you can delete groups in the following ways:
  - Delete a single group: Click **Delete** in the row of the target group.
  - Delete a batch of groups: Select the target groups to be deleted and click **Delete Groups** above the group list.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/19b0229d7b1411ef852f52540075b605.png)

2. In the pop-up dialog box, click **Confirm**. **After the group is deleted, all its information will be deleted and cannot be recovered.**


---
*Source: [https://trtc.io/document/34578](https://trtc.io/document/34578)*
