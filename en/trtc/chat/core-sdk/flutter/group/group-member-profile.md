# Group Member Profile

## Feature Description

The methods to manipulate the group member profile are in the `TencentImSDKPlugin.v2TIMManager.getGroupManager()` core class.

## Getting the Profile of a Group Member

Call `getGroupMembersInfo` ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/getGroupMembersInfo.html)) to get the group member profile. This API supports passing in multiple `userID` values at a time to batch get group member profiles and therefore improve the network transfer efficiency.

Sample code:

```
// Get the group member profileV2TimValueCallback<List<V2TimGroupMemberFullInfo>> memberInfos = await groupManager.getGroupMembersInfo(groupID: "groupID", memberList: ["id1"]);
```

## Modifying the Profile of a Group Member

The group owner or admin can call the `setGroupMemberInfo` API ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_group_manager/V2TIMGroupManager/setGroupMemberInfo.html)) to modify the group name card (`nameCard`), custom field (`customInfo`), and other information of a group member.

Sample code:

```
// Set the group member profilegroupManager.setGroupMemberInfo(groupID: "",userID: "",nameCard: "",customInfo: {});
```


---
*Source: [https://trtc.io/document/48176](https://trtc.io/document/48176)*
