# Feature Configuration

## Login and Message

Log in to the [Chat console](https://console.tencentcloud.com/im), select**Chat > Configuration >** **Login and Message** on the left sidebar, and **select the target application at the top**. You can manage login and message related settings according to your business needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ebf92108caa911f08942525400e889b2.png)

### Login Settings

1. On the **Login and Message** page, click **Edit** in the upper-right corner of the **Login Settings** area.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7afd9a52caa811f0a7775254005ef0f7.png)

2. In the pop-up dialog box, select a multi-device login policy and set the maximum number of concurrent online web instances.

> **Note:**If you select multi-device login for the Pro edition ãPro Plus editionãEnterprise edition, up to 10 concurrent online web clients are supported, and up to 3 online devices are supported for each of the Android, iPhone, iPad, Windows, macOS, and Linux platforms.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/83f5d547caa811f09e745254007c27c5.png)

3. Click **Confirm**.

### Historical Message Storage Period Settings

Historical messages are stored for seven days by default. **Extending the storage period is a value-added service.** For more information on billing, see [Pricing](https://intl.cloud.tencent.com/document/product/1047/34350). You can modify the storage period once every month.

1. On the **Login and Message** page, click **Edit** in the upper-right corner of the **Historical Message Storage Period Settings** area.
2. In the pop-up dialog box, extend the storage period of historical messages.
3. Click **Confirm** and the configuration will take effect immediately.

### Message Recall Settings

1. On the **Login and Message** page, click **Edit** in the upper-right corner of the **Message Recall Settings** area.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/950bf3df7b0a11ef8829525400fdb830.png)

2. In the pop-up dialog box, set the time limit for message recall.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c41ee5a6caa811f0aedb525400454e06.png)

3. Click **Confirm**.

### Multi-client Synchronization Settings

You can enable or disable **Sync Conversation Deletion Across Clients** in the **Multi-client Synchronization Settings** area on the **Login and Message** page.

- Enabled: If multiple clients are online concurrently, deleting a conversation from one client will be synced to other clients (that is, the conversation will also be deleted from other clients).
- Disabled: If multiple clients are online concurrently, deleting a conversation from one client will not be synced to other clients. The feature of syncing conversation deletion across clients is disabled by default.

> **Note:**The feature of syncing conversation deletion across clients is available only to **native SDK v5.1.1 and web SDK v2.14.0 or later**. If you are using an earlier SDK version, you need to **upgrade your SDK** before you can use the feature.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ca309000caa811f0a7775254005ef0f7.png)

### User Status Query and Status Change Notification Configuration

You can enable the feature of user status query and status change notification in the **Set user status query and status change notification** area on the **Login and Message** page.

> **Note:**The feature of user status query and status change notification is disabled by default. When it is disabled, the error code 72001 will be reported for user status query, subscription, or unsubscription on clients. The feature can be enabled on native SDK v6.3 or later and is available only to Pro edition ãPro Plus editionãEnterprise edition users. You can [click here to upgrade](https://www.tencentcloud.com/document/product/1047/34577).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d47a2818caa811f0aedb525400454e06.png)

### Message Extension Setting

You can enable message extension in the **Set message extension** area on the **Login and Message** page.

> **Note:**Message extension allows you to configure keys and values for messages to implement features such as polling, group notices, and surveys. For more information, see [here](https://www.tencentcloud.com/document/product/1047/50865). Message extension is available only to Pro edition ãPro Plus editionãEnterprise edition users and is supported only on native SDK Enhanced edition v6.7.3184 or later. If you are using an earlier version, upgrade your SDK.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d9df3b54caa811f0aedb525400454e06.png)

### All/Tag Users Push Settings

You can enable the feature of pushing to all users in the **All/Tag users push settings** area.

> **Note:**All/Tag Users Push is an excellent tool for application user operations. It not only supports sending specific content to all users, but also can send personalized content to specific user groups based on tags and attributes, such as member events, and regional notifications. This helps effectively attract, convert, and activate users. For more information, see [Pushing to All Users](https://intl.cloud.tencent.com/document/product/1047/37166).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/de75d863caa811f0a4a55254001c06ec.png)

### Configuration of Conversations to Pull

In the **Configuration of conversations to pull** area on the **Login and Message** page, you can configure the number of conversations to be pulled from the cloud. The default number is 100, and you can change the number to up to 500.

> **Note:**The feature of configuring the number of conversations to pull is available only to **Pro edition ãPro Plus editionãEnterprise edition** users. If you are not an Pro edition ãPro Plus editionãEnterprise edition user, you need to upgrade your package before you can use the feature.The feature of configuring the number of conversations to pull is available only to **native SDK v5.1.1 and web SDK v2.0 or later**. If you are using an earlier SDK version, you need to upgrade your SDK before you can use the feature.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e34c0f48caa811f0a93d52540044a08e.png)

### Blocklist Check

You can enable or disable **Show "Sent successfully" After Sending Messages** in the **Blocklist check** area on the **Login and Message** page.

- Enabled: If you are in the recipientâs blocklist, you will see **Sent successfully** after sending a one-to-one message and the recipient will not receive the message. This is the default setting.
- Disabled: If you are in the recipientâs blocklist, you will see **Failed to send** after sending a one-to-one message.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e8b8ac30caa811f0b011525400bf7822.png)

### Relationship Check

You can enable or disable **Check Relationship for One-to-One Messages** in the **Relationship Check** area on the **Login and Message** page.

- Enabled: Check relationships before a one-to-one chat starts and only allow sending one-to-one messages to friends. When a user sends a one-to-one message to a stranger, the SDK will return [error code 20009](https://intl.cloud.tencent.com/document/product/1047/34348).
- Disabled: Do not check relationships before a one-to-one chat starts and allow users to send and receive one-to-one messages to and from friends and strangers. This is the default setting.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f1b6e86ecaa811f0a4a55254001c06ec.png)

### Receive Callback for being Kicked Offline

On the login and message page, within the section for receiving the kicked-offline callback, you can choose to enable or disable this callback. The buttons are categorized into "Reconnect after network disconnection" and "Active login":

When both "Triggered when reconnecting after network disconnection" and "Triggered when actively logging in" are enabled, the system will trigger a reconnection login under any circumstances, and you will receive [Error Code 6208](https://trtc.io/zh/document/34348?platform=web&product=chat&menulabel=uikit#.E5.B8.90.E5.8F.B7.E9.94.99.E8.AF.AF.E7.A0.81).

If only "Triggered when reconnecting after network disconnection" is enabled and "Triggered when actively logging in" is disabled, you will receive [Error Code 6208](https://trtc.io/zh/document/34348?platform=web&product=chat&menulabel=uikit#.E5.B8.90.E5.8F.B7.E9.94.99.E8.AF.AF.E7.A0.81) in scenarios other than active login.

Note:

> **Note:**This feature is only applicable to the Native SDK. The Web SDK will not return Error Code 6208.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f5cf0a0bcaa811f0b011525400bf7822.png)

### User Profile Change Subscription

On the **Login and Messaging** page, you can enable or disable the subscription to user profile changes in the **Friend Relationship Check** section. For details, see [Notification of User Profile Change](https://trtc.io/document/48162?product=chat&menulabel=core%20sdk&platform=android#0ab13ed0-a4a4-4f9d-ad16-21a8012ee783).

Based on the type of user, user profile changes can be divided into the following three:

- Personal profile update.
- Friend's profile update.
- Profile update for subscribed users (non-friends).

> **Note:**This feature is disabled by default. At this point, the client will receive error code [72012](https://trtc.io/document/34348?platform=web&product=chat&menulabel=uikit#.E5.B8.90.E5.8F.B7.E9.94.99.E8.AF.AF.E7.A0.812) when subscribing to User Profile updates.The default supports subscribing to 200 users. When the limit is exceeded, the earliest subscribed user will be eliminated.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/033ec024caaa11f0b011525400bf7822.png)

## Friends and Relationship Chain

Log in to the [Chat Console](https://console.trtc.io), select **Chat > Configuration >** [**Friends and Relationship**](https://console.trtc.io/chat/friends-diy-vars) in the left sidebar, and **select the target application at the top**. You can manage friends and relationship chain configuration based on actual business needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed100b4ecaaa11f09e745254007c27c5.png)

### Setting Verification Method for Adding Friends

1. On the right side of the **default verification method for adding friends settings** function card, click **Edit**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87dd7919caac11f0a7775254005ef0f7.png)

2. Choose an appropriate default verification method for adding friends, then click **Confirm** to save.

### Block Configuration

1. On the right side of the **Block Configuration** function card, click **Edit**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87e55351caac11f0b011525400bf7822.png)

2. Select the processing method after blocking a friend, then click **Confirm** to save.

### Follow / Fan Feature Setting

1. On the right side of the **Follow / Fan Feature Setting** function card, click **Edit**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/87da6db2caac11f0b011525400bf7822.png)

2. Select to turn on or off the Follow / Fan feature configuration status, then click **Confirm** to save.

### Custom Friend Fields

> **Note:**You can add up to 20 custom friend fields, which cannot be deleted and whose field name and type cannot be modified. Please set the fields properly as needed.

1. Click **Add New** on the right side of the **Custom Friend Field** function card.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a56233cdcaac11f0a93d52540044a08e.png)

2. In the pop-up dialog box, enter a field name and select a field type.

> **Note:**The field name must be all letters and cannot exceed eight characters.

## User-Defined Fields

Log in to the [Chat Console](https://console.trtc.io), select **Chat > Configuration >**[**Custom User Field**](https://console.trtc.io/chat/user-data) in the left sidebar, and **select the target application at the top**. You can manage user-defined fields based on actual business needs.

> **Caution:**You can add up to 20 custom user fields, which cannot be deleted and whose field name and type cannot be modified. Please set the fields properly as needed.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d53f8651caac11f0a4a55254001c06ec.png)

### Adding a User-Defined Field

1. On the **Custom User Field** page, click **Add** in the upper-right corner.
2. In the pop-up dialog box, enter a field name, select a field type, and set read/write permissions.

> **Note:**The field name must be all letters and cannot exceed eight characters.You need to enable at least one read permission and one write permission

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea9553cccaac11f08942525400e889b2.png)

3. Click **Confirm**.

### Modifying User-Defined Field Permissions

1. On the **Custom User Field** page, click **Change Permissions** in the row of the target field.
2. In the pop-up dialog box, change the read or write permission.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/024c746fcaad11f09e745254007c27c5.png)

3. Click **Confirm**.

## Group Configuration

### Custom Group Member Fields

Log in to the [Chat console](https://console.trtc.io), select **Chat > Configuration >**[**Custom User Field**](https://console.trtc.io/chat/user-data) in the left sidebar, **select the target application at the top**, and choose the **Custom Group Member Field tag column**. You can manage custom fields of group members based on actual business needs.

> **Caution:**You can add up to five custom group member fields, which cannot be deleted and whose group type and read/write permissions can be changed. Please set the fields properly as needed.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7777ba5dcaad11f0a7775254005ef0f7.png)

#### Adding Custom Group Member Field

1. On the **Custom Group Member Field** page, click **Add** in the upper-right corner.
2. In the pop-up dialog box, enter a field name and set group types and read/write permissions.

> **Note:**The field name can contain up to 16 characters, supporting letters, digits, and underscores (_). It cannot begin with a digit.A custom group member field and a custom group field cannot have the same name.

  - ClickÂ **Add Group Type**Â to add one group type at a time. Duplicate group types are not allowed.
  - ClickÂ **Delete**Â in the row of the target group type to delete it. However, you must retain at least one group type.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9d5ad8b6caad11f0a7775254005ef0f7.png)

3. Select **I understand that after a custom group member field is added, only the read-write permissions of the added group type can be modified; the group type cannot be reselected or deleted; the field cannot be deleted.**
4. Click **Confirm**.

#### Editing Custom Group Member Field

1. On the **Custom Group Member Field** page, click **Edit** in the row of the target custom group member field.
2. In the pop-up dialog box, modify the read and write permissions of existing group types, or click **Add Group Type** to add a new one and set its parameters. Duplicate group types are not allowed.
![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/270b17e17b0d11ef80ff525400d5f8ef.png)
3. Select **I understand that after a custom group member field is added, only the read-write permissions of the added group type can be modified; the group type cannot be reselected or deleted; the field cannot be deleted.**
4. Click **Confirm**.

### Group Custom Field

Log in to the [Chat console](https://console.trtc.io), select **Chat > Configuration >**[**Group configuration**](https://console.trtc.io/chat/qun-setting) in the left sidebar, **select the target application at the top**, and choose the **Custom Group Field tag column**. You can manage group custom fields based on actual business needs.

> **Note:**You can add up to 10 custom group fields. Once set, these fields cannot be deleted, and only the group types and the corresponding read and write permissions can be modified. Therefore, set these fields properly as needed.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/091974c6caae11f0a4a55254001c06ec.png)

#### Adding Custom Group Field

1. On the **Custom Group Field** page, click **Add** in the upper-right corner.
2. In the pop-up dialog box, enter a field name and set the group types and read/write permissions.

> **Note:**The field name can contain up to 16 characters, supporting letters, digits, and underscores (_). It cannot begin with a digit.A custom group field and a custom group member field cannot have the same name.

  - Click **Add Group Type** to add one group type at a time. Duplicate group types are not allowed.
  - Click **Delete** in the row of the target group type to delete it. However, you must retain at least one group type.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1a45bd34caae11f0b011525400bf7822.png)

3. Select **I understand that after a custom group member field is added, only the read-write permissions of the added group type can be modified; the group type cannot be reselected or deleted; the field cannot be deleted.**
4. Click **Confirm**.

#### Editing Custom Group Field

1. On the **Custom Group Field** page, click **Edit** in the row of the target custom group field.
2. In the pop-up dialog box, modify the read/write permissions of existing group types, or click **Add Group Type** to add a new one and set its parameters. Duplicate group types are not allowed.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/244c1f7bcaae11f08942525400e889b2.png)

3. Select **I understand that after a custom group member field is added, only the read-write permissions of the added group type can be modified; the group type cannot be reselected or deleted; the field cannot be deleted.**
4. Click **Confirm**.

### Group Message Configuration

Log in to the [Chat console](https://console.trtc.io), select **Chat > Configuration >**[**Group Configuration**](https://console.trtc.io/chat/qun-setting) in the left sidebar, **select the target application at the top**, and choose the **Group Message Configuration tag column**. You can perform group message configuration based on actual business needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3e6f68e6caae11f0a7775254005ef0f7.png)

#### Pulling Message History before Group Join

1. On the **Pull message history before group join** page, select a **Group Type** and click **Edit**.
2. In the **Pull message history before group join** pop-up window, select the required configuration items.

> **Note:**It takes about ten minutes for the configuration to take effect.Audio-video groups do not support this configuration.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/492f21facaae11f0b011525400bf7822.png)

### Group System Notification Configuration

Log in to the [Chat console](https://console.trtc.io), select **Chat > Configuration >**[**Group configuration**](https://console.trtc.io/chat/qun-setting) in the left sidebar, **select the target application at the top**, and choose the **Group System Notification Configuration tag column**. You can perform group system notification configuration based on actual business needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6df21899caae11f087ad52540099c741.png)

#### Group Member Change Notification

1. On the **Notification of group member change**, select a **Group Type** and click **Edit**.
2. In the **Notification of group member change** pop-up window, select the required configuration items.

> **Note:**It takes about ten minutes for the configuration to take effect.Audio-video groups do not support configuring the notification of group member change.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/affa49efcaae11f0aedb525400454e06.png)

#### Group Profile Change Notification

1. On the **Notification of group profile change** page, select a **Group Type** and click **Edit**.
2. In the **Notification of group profile change** pop-up window, select the required configuration items.

> **Note:**It takes about ten minutes for the configuration to take effect.Audio-video groups do not support configuring the notification of group profile change.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c0fe0542caae11f09e745254007c27c5.png)

#### Group Member Profile Change Notification

1. On the **Notification of group member profile change** page, select a **Group Type** and click **Edit**.
2. In the **Notification of group member profile change** pop-up window, select the required configuration items.

> **Note:**It takes about ten minutes for the configuration to take effect.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dbe39d99caae11f08942525400e889b2.png)

### Group Feature Configuration

Log in to the [Chat console](https://console.trtc.io), select **Chat > Configuration >**[**Group Configuration**](https://console.trtc.io/chat/qun-setting) in the left sidebar, **select the target application at the top**, and choose the **Group Feature Configuration tag column**. You can perform group feature configuration based on actual business needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ef56fc9ccaae11f087ad52540099c741.png)

#### Community Group

A community is a large group that can hold up to 100,000 users. Once a community is created, it allows users to join or leave freely and supports historical message storage. The community feature is disabled by default. Enabling it allows you to create communities and use associated features.

If you need to use the topic feature, enable it after creating a community. Multiple topics can be created under the same community, and they share the same set of community member relationships. However, different topics have their own message sending and receiving independently and do not interfere with each other.

> **Note:**The community feature is available only for native SDK v5.8.1668 enhanced edition or later and for web SDK v2.17.0 or later. If you are using an earlier SDK version, you need to upgrade your SDK before you can use the feature.This feature is available only for Pro edition ãPro Plus editionãEnterprise edition users. You can [click here to upgrade](https://www.tencentcloud.com/document/product/1047/34577).

#### Online Members List of Live Streaming Group

The feature of "List of online audio-video group members" is disabled by default. You can enable it as needed.

> **Note:**If the feature is enabled, the list of the 1,000 latest online members of an audio-video group will be stored and the list can be pulled on clients.This feature is available only for native SDK v6.3 or later. If you are using an earlier SDK version, you need to upgrade your SDK before you can use the feature.This feature is available only for Pro edition ãPro Plus editionãEnterprise edition users. You can [click here to upgrade](https://www.tencentcloud.com/document/product/1047/34577).

#### Broadcast Messaging of Live Group

Broadcast messaging of audio-video group is disabled by default. You can enable it as needed.

> **Note:**Broadcast messaging of audio-video group is disabled by default and can be enabled on native SDK v6.5 or later.Enabling this feature allows you to set the call frequency of the broadcast messaging of audio-video group, which defaults to one message per second and can be set to up to five messages per second.This feature is available only for Pro edition ãPro Plus editionãEnterprise edition users. You can [click here to upgrade](https://www.tencentcloud.com/document/product/1047/34577).

#### Live Streaming Group Ban

Once this feature is enabled, audio-video group members can be banned as needed. A banned member cannot receive group messages or rejoin the group during the ban.

> **Note:**This feature is available only for native SDK v6.6 and web SDK v2.22 or later. If you are using an earlier SDK version, you need to upgrade your SDK before you can use the feature.This feature is available only for Pro edition ãPro Plus editionãEnterprise edition users. You can [click here to upgrade](https://www.tencentcloud.com/document/product/1047/34577).

#### Live Group New Member View Messages before Joining Group Configuration

Message history for new members is an important feature to increase the user stickiness in audio-video groups. It enables users to know what was going on before they enter an audio-video group, so they can quickly fit into interactive discussions and feel more involved. This helps deliver an highly immersive live chat experience and increase users' length of stay in live rooms.

1. On the **Login and Message** page, click **Edit** in the upper-right corner of the **Message History for New Members** area.
2. In the pop-up dialog box, set the number of messages viewable to new members.
3. Click **Confirm**.

#### Group Message Read Receipt Configuration

Group message read receipt is a must-have feature for efficient communication. As a powerful feedback tool, it allows viewing the numbers and details of members who have or have not read the sent messages. This helps teams create a more timely and efficient atmosphere of communication, especially in business and OA scenarios.

1. On the **Login and Message** page, click **Edit** in the upper-right corner of **Read receipts for group messages**.
2. In the pop-up **Read receipts for group messages** dialog box, set the group types that support message receipts.
3. Click **Confirm**.

> **Note:**The group message read receipt feature is **available only for Pro edition ãPro Plus editionãEnterprise edition users**. If you are not an Pro edition ãPro Plus editionãEnterprise edition user, you need to [upgrade](https://www.tencentcloud.com/document/product/1047/34577) before you can use the feature. The feature is supported by **native SDK v6.1.2155 or later** and is applicable to **work groups (Work)**, **public groups (Public)**, and **meeting groups (Meeting)** that support up to 200 members per group.

## Server API Frequency Modulation

Log in to [Chat Console](https://console.trtc.io/chat/adjust-frequency). In the left navigation **Chat** > **Feature Management** **>**[**Server API Frequency Modulation**](https://console.trtc.io/chat/adjust-frequency), you can perform server API frequency modulation configuration based on actual business needs.

1. Click edit on the right of the server API that needs frequency modulation.
2. Slide the slider to the required frequency size and click save.
3. In the pop-up dialog box to save current configuration, click confirm to save configuration.

> **Notes:**Server API frequency modulation is a paid service, available only for the Pro-plus Edition and Enterprise Edition. Each frequency modulation item is calculated based on the highest value configured on the current day. Fees are only charged for the part that exceeds the default frequency limit. For billing details, see [Billing Description - Server API Frequency Modulation](https://www.tencentcloud.com/document/product/1047/67651#4bd5b460-57b2-4ac3-874c-e2738c2024a8).

Server APIs that support adjustments:

| Feature Description | API | Default frequency limit | Package size of each overlay |
| --- | --- | --- | --- |
| [Sending One-to-One Messages to Multiple Users](https://trtc.io/document/34920?product=chat&menulabel=restfulapi) | v4/openim/batchsendmsg | 12,000 Items/Minute200 times/second | 6,000 per minute,Free to upgrade to 1000 times/second |
| [Sending One-to-One Messages to One User](https://trtc.io/document/34919?product=chat&menulabel=restfulapi) | v4/openim/sendmsg | 200 pieces/second | 100 entries/second |
| [Sending Ordinary Messages in a Group](https://trtc.io/document/34959?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/send_group_msg | 200 pieces/second | 100 entries/second |
| [Sending System Messages in a Group](https://trtc.io/document/34958?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/send_group_system_notification | 200 pieces/second | 100 entries/second |
| [Querying Unread One-to-One Message Count](https://trtc.io/document/41046?product=chat&menulabel=restfulapi) | v4/openim/get_c2c_unread_msg_num | 200 times/second | 100 times/second |
| [Adding Group Members](https://trtc.io/document/34921?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/add_group_member | 200 times/second | 100 times/second |
| [Delete Group Members](https://trtc.io/document/34949?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/delete_group_member | 200 times/second | 100 times/second |
| [Create a Group](https://trtc.io/document/34895?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/create_group | 200 times/second | 100 times/second |
| [Dissolve the Group](https://trtc.io/document/34896?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/destroy_group | 200 times/second | 100 times/second |
| [Get group details](https://trtc.io/document/34961?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/get_group_info | 200 times/second | 100 times/second |
| [Getting group member detailed information](https://trtc.io/document/64897?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/get_group_member_info | 200 times/second | 100 times/second |
| [Get groups that the user has joined](https://trtc.io/document/34925?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/get_joined_group_list | 200 times/second | 100 times/second |
| [Query the user's identity in the group](https://trtc.io/document/34963?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/get_role_in_group | 200 times/second | 100 times/second |
| [Pull group chat history messages](https://trtc.io/document/34971?product=chat&menulabel=restfulapi) | v4/group_open_http_svc/group_msg_get_simple | 200 times/second | 100 times/second |
| [Setting Profile](https://trtc.io/document/34916?product=chat&menulabel=restfulapi) | v4/profile/portrait_set | 200 times/second | 100 times/second |
| [Pull the profile](https://trtc.io/document/34917?product=chat&menulabel=restfulapi) | v4/profile/portrait_get | 200 times/second | 100 times/second |
| [Query account online status](https://trtc.io/document/35477?product=chat&menulabel=restfulapi) | v4/openim/query_online_status | 200 times/second | 100 times/second |
| [Pull the blocklist](https://trtc.io/document/34914?product=chat&menulabel=restfulapi) | v4/sns/black_list_get | 200 times/second | 100 times/second |


---
*Source: [https://trtc.io/document/34419](https://trtc.io/document/34419)*
