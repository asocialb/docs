# Group Member Management

## Overview

Group member management includes pulling the member list, muting group members, removing group members, granting permissions, and transferring the group ownership, which can be implemented through the methods in the `TencentImSDKPlugin.v2TIMManager.getGroupManager()` core class.

## Getting the Group Member List

Call [`getGroupMemberList`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/getGroupMemberList.html) to get the list of members in a specified group. This list contains the profile information of each member, such as user ID (`userID`), group name card (`nameCard`), profile photo (`faceUrl`), nickname (`nickName`), and time for joining the group (`joinTime`).

As a group might have a large number of members (for example, over 5,000), this API supports two advanced features: pulling by filter (`filter`) and pulling by page (`nextSeq`).

### Filter (`filter`)

When calling the [`getGroupMemberList`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/getGroupMemberList.html) API, you can specify `filter` to pull the list of the information of specified roles.

| Filter | Type |
| --- | --- |
| GroupMemberFilterTypeEnum.V2TIM_GROUP_MEMBER_FILTER_ALL | Pull the list of the information of all the group members |
| GroupMemberFilterTypeEnum.V2TIM_GROUP_MEMBER_FILTER_OWNER | Pull the list of the information of the group owner |
| GroupMemberFilterTypeEnum.V2TIM_GROUP_MEMBER_FILTER_ADMIN | Pull the list of the information of the group admin |
| GroupMemberFilterTypeEnum.V2TIM_GROUP_MEMBER_FILTER_COMMON | Pull the information list of ordinary group members |

Sample code:

```
// Use the `filter` parameter to specify only the profile of the group owner is to be pulledgroupManager.getGroupMemberList(count: 10,filter: GroupMemberFilterTypeEnum.V2TIM_GROUP_MEMBER_FILTER_ADMIN,nextSeq: '0',offset: 0,groupID: "",);
```

### Pulling by page (`nextSeq`)

In many cases, only the first page of the group member list, not the information of all the group members, needs to be displayed on the user UI. More group members need to be pulled only when the user clicks **Next Page** or pulls up the list page. In this case, you can use pulling by page.

Directions for pulling by page:

1. When you call `getGroupMemberList` for the first time, set `nextSeq` to `0` (indicating to pull the group member list from the beginning). Up to 50 group member objects can be pulled at a time.
2. After the group member list is pulled successfully for the first time, the `V2TIMGroupMemberInfoResult` callback of `getGroupMemberList` will contain `nextSeq` (field for the next pull):
  - If `nextSeq` is `0`, all the group members have been pulled.
  - If `group_get_memeber_info_list_result_next_seq` is greater than `0`, there are more group members that can be pulled. This doesn't mean that the next page of the member list will be pulled immediately. In common communications software, a paged pull is often triggered by a swipe operation.
3. When the user continues to pull up the group member list, if there are more members that can be pulled, you can continue to call the `getGroupMemberList` API and pass in the `nextSeq` parameter (the value is from the `V2TIMGroupMemberInfoResult` object returned by the last pull) for the next pull.
4. Repeat [step 3] until `nextSeq` is `0`.

Sample code:

```
// Use the `filter` parameter to specify only the profile of the group owner is to be pulledgroupManager.getGroupMemberList(count: 10,filter: GroupMemberFilterTypeEnum.V2TIM_GROUP_MEMBER_FILTER_ADMIN,nextSeq: '0',offset: 0,groupID: "",);
```

## Muting group members

### Muting a specified group member

The group owner or admin can call [`muteGroupMember`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/muteGroupMember.html) to mute a specified group member and set the muting period in seconds. The muting information is stored in the `muteUtil` attribute of the group member.

After a group member is muted, all the group members (including the muted member) will receive the [`onMemberInfoChanged`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimGroupListener/V2TimGroupListener/onMemberInfoChanged.html) callback.

### Muting the entire group

The group owner or admin can also call the [`setGroupInfo`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/setGroupInfo.html) API to mute the entire group by setting the `allMuted` attribute to `true`. The entire group can be muted for an unlimited period of time and needs to be unmuted through `setAllMuted(false)` of the group profile.

> **Note:**Muting all the group members will trigger the [`onGroupInfoChanged`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimGroupListener/V2TimGroupListener/onGroupInfoChanged.html) callback. This feature is disabled by default and can be enabled in the console.
> Directions: Go to the [**Group configuration module**](https://console.trtc.io/chat/qun-setting) module in the Chat console, select **Group system notification configuration**, click **Edit** in the **Operation** column, and modify **Notification of muting all change**.

Sample code:

```
// Mute the group member `userB` for ten minutesgroupManager.muteGroupMember(groupID: '',userID: 'userB',seconds: 10);// Mute all membersgroupManager.setGroupInfo(info: V2TimGroupInfo(isAllMuted: true,groupID: '',groupType: 'Public'));TencentImSDKPlugin.v2TIMManager.addGroupListener(listener: V2TimGroupListener(onMemberInfoChanged: (groupID, v2TIMGroupMemberChangeInfoList) {    // The group member information is changed.  },  onGroupInfoChanged: (groupID,info){    // Group profile modification  }  ));
```

> **Note:**Only the group owner can mute the admin.

## Removing Group Members

The group owner or admin can call the [`kickGroupMember`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/kickGroupMember.html) API to remove a specified ordinary group member from the group.

After the ordinary group member is removed, all the members (including the removed member) will receive the [`onMemberKicked`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimGroupListener/V2TimGroupListener/onMemberKicked.html) callback.

As an audio-video group (AVChatRoom) can be joined freely, there is no API for removing a group member from an audio-video group (AVChatRoom). You can use [`muteGroupMember`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/muteGroupMember.html) to mute a specified member to implement similar controls.

> **Note:**Only the group owner can remove the admin from the group.

Sample code:

```
groupManager.kickGroupMember(groupID: '',memberList: []);
```

## Setting an Admin

The group owner can call [`setGroupMemberRole`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/setGroupMemberRole.html) to set a group member in a public group (Public) or meeting group (Meeting) as the admin.

An ordinary member set as the admin has the admin permission to perform the following operations:

- Modify the basic group profile.
- Remove an ordinary member from the group
- Mute an ordinary member (prevent the member from speaking during a specified period of time)
- Approve a request to join the group

For more information, see [Group Member Roles](https://intl.cloud.tencent.com/document/product/1047/33529).

After an ordinary member is set as the admin, all the members (including the ordinary member) will receive the [`onGrantAdministrator`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimGroupListener/V2TimGroupListener/onGrantAdministrator.html) callback.

After the ordinary member is unset as the admin, all the members (including the ordinary member) will receive the [`onRevokeAdministrator`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimGroupListener/V2TimGroupListener/onRevokeAdministrator.html) callback.

Sample code:

```
groupManager.setGroupMemberRole(groupID: '',userID: '',role: GroupMemberRoleTypeEnum.V2TIM_GROUP_MEMBER_ROLE_ADMIN);// Listen for the role changeTencentImSDKPlugin.v2TIMManager.addGroupListener(listener: V2TimGroupListener(onMemberInfoChanged: (groupID, v2TIMGroupMemberChangeInfoList) {  },  onGroupInfoChanged: (groupID,info){  },  onGrantAdministrator: (String groupID, V2TimGroupMemberInfo info, List<V2TimGroupMemberInfo> infolist){},  onRevokeAdministrator: (String groupID, V2TimGroupMemberInfo info, List<V2TimGroupMemberInfo> infolist){},  ));
```

## Transferring Group Ownership

The group owner can call [transferGroupOwner](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/transferGroupOwner.html) to transfer the group ownership to a group member.

After the group ownership is transferred, all the group members will receive the [`onGroupInfoChanged`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_V2TimGroupListener/V2TimGroupListener/onGroupInfoChanged.html) callback. Here, the `type` of `V2TIMGroupChangeInfo` is `V2TIMGroupChangeInfo.V2TIM_GROUP_INFO_CHANGE_TYPE_OWNER`, and the value is the `UserID` of the new group owner.

Sample code:

```
groupManager.transferGroupOwner(groupID: "", userID: "userID");
```

## Getting the Number of Online Group Members

Call [`getGroupOnlineMemberCount`](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/getGroupOnlineMemberCount.html) to get the number of online group members.

> **Note:**This API is only supported in audio-video groups (AVChatRoom) before SDK 7.3 version.You can call this API for all kinds of groups in SDK 7.3 and later versions.

Sample code:

```
groupManager.getGroupOnlineMemberCount(groupID: '');
```


---
*Source: [https://trtc.io/document/48179](https://trtc.io/document/48179)*
