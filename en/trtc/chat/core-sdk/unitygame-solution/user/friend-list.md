# Friend List

## Feature Description

To group friends into categories such as "Classmates at university" and "Coworkers", call the following APIs.

## Friend List

### Creating a friend list

Call the `FriendshipCreateFriendGroup` API ([Details](https://comm.qq.com/im/doc/unity/en/ api/FriendshipApi/FriendshipCreateFriendGroup.html)) to create a friend list.

Sample code:

```
// Create a friend list and add a friend to the listFriendGroupInfo param = new FriendGroupInfo{  friendship_create_friend_group_param_name_array = new List<string>  {    "group_name"  },  friendship_create_friend_group_param_identifier_array = new List<string>  {    "user_id"  }};TIMResult res = TencentIMSDK.FriendshipCreateFriendGroup(param, (int code, string desc, List<FriendResult> result, string user_data)=>{ // Process the async logic});
```

### Deleting a friend list

Call the `FriendshipDeleteFriendGroup` API ([Details](https://comm.qq.com/im/doc/unity/en/api/FriendshipApi/FriendshipDeleteFriendGroup.html)) to delete a friend list.

Sample code:

```
// Delete a friend listList<string> param = new List<string>{  "user_id"};TIMResult res = TencentIMSDK.FriendshipDeleteFriendGroup(param, (int code, string desc, string user_data)=>{ // Process the async logic});
```

### Renaming a friend list

Call the `FriendshipModifyFriendGroup` API ([Details](https://comm.qq.com/im/doc/unity/en/api/FriendshipApi/FriendshipModifyFriendGroup.html)) to rename a friend list.

Sample code:

```
// Rename a friend listFriendshipModifyFriendGroupParam param = new FriendshipModifyFriendGroupParam{  friendship_modify_friend_group_param_name = "old_group_name",  friendship_modify_friend_group_param_new_name = "new_group_name"};TIMResult res = TencentIMSDK.FriendshipModifyFriendGroup(param, (int code, string desc, List<FriendResult> result, string user_data)=>{ // Process the async logic});
```

### Getting a friend list

Call the `FriendshipGetFriendGroupList` API ([Details](https://comm.qq.com/im/doc/unity/en/api/FriendshipApi/FriendshipGetFriendGroupList.html)) to get a friend list.

Sample code:

```
// Get the information of a friend list by list nameList<string> param = new List<string>  {    "user_id"  };TIMResult res = TencentIMSDK.FriendshipGetFriendGroupList(param, (int code, string desc, List<FriendGroupInfo> info_list, string user_data)=>{ // Process the async logic});
```

### Adding a friend to a list

Call the `FriendshipModifyFriendGroup` API ([Details](https://comm.qq.com/im/doc/unity/en/api/FriendshipApi/FriendshipModifyFriendGroup.html)) to add a friend to a list.

Sample code:

```
// Add a friend to a friend listFriendshipModifyFriendGroupParam param = new FriendshipModifyFriendGroupParam{  friendship_modify_friend_group_param_name = "group_name",  friendship_modify_friend_group_param_add_identifier_array = new List<string>  {    "user_id"  }};TIMResult res = TencentIMSDK.FriendshipModifyFriendGroup(param, (int code, string desc, List<FriendResult> result, string user_data)=>{ // Process the async logic});
```

### Removing a friend from a list

Call `FriendshipModifyFriendGroup` ([Details](https://comm.qq.com/im/doc/unity/en/api/FriendshipApi/FriendshipModifyFriendGroup.html)) to remove a friend from a list.

Sample code:

```
// Remove a friend from a listFriendshipModifyFriendGroupParam param = new FriendshipModifyFriendGroupParam{  friendship_modify_friend_group_param_name = "group_name",  friendship_modify_friend_group_param_delete_identifier_array = new List<string>  {    "user_id"  }};TIMResult res = TencentIMSDK.FriendshipModifyFriendGroup(param, (int code, string desc, List<FriendResult> result, string user_data)=>{ // Process the async logic});
```


---
*Source: [https://trtc.io/document/49565](https://trtc.io/document/49565)*
