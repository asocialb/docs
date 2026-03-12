# Group Member Profile

## Feature Description

The methods to manipulate the group member profile are in the `GroupGetMemberInfoList` and `GroupModifyMemberInfo` core classes.

## Getting the Profile of a Group Member

Sample code:

```
// Get the group member profileGroupGetMemberInfoListParam param = new GroupGetMemberInfoListParam{  group_get_members_info_list_param_group_id = "group_id",  group_get_members_info_list_param_identifier_array = new List<string>  {    "user_id"  }};TIMResult res = TencentIMSDK.GroupGetMemberInfoList(param, (int code, string desc, GroupGetMemberInfoListResult result, string user_data)=>{ // Process the async logic});
```

## Modifying the Profile of a Group Member

Sample code:

```
// Set the group member profileGroupModifyMemberInfoParam param = new GroupModifyMemberInfoParam{  group_modify_member_info_group_id = "group_id",  group_modify_member_info_identifier = "userB",  group_modify_member_info_modify_flag = TIMGroupMemberModifyInfoFlag.kTIMGroupMemberModifyFlag_NameCard,  group_modify_member_info_name_card = "new name card"};TIMResult res = TencentIMSDK.GroupModifyMemberInfo(param, (int code, string desc, string user_data)=>{ // Process the async logic});
```


---
*Source: [https://trtc.io/document/50320](https://trtc.io/document/50320)*
