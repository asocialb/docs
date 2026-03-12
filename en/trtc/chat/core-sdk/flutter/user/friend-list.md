# Friend List

## Feature Description

To group friends into categories such as "Classmates at university" and "Coworkers", call the following APIs.

## Friend List

### Creating a friend list

Call the `createFriendGroup` API ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_friendship_manager/V2TIMFriendshipManager/createFriendGroup.html)) to create a friend list.

Sample code:

```
// Create a friend list and add a friend to the listV2TimValueCallback<List<V2TimFriendOperationResult>> friendgroups = await friendshipManager.createFriendGroup(groupName: "Friend list 1",userIDList: ['user1']);
```

### Deleting a friend list

Call the `deleteFriendGroup` API ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_friendship_manager/V2TIMFriendshipManager/deleteFriendGroup.html)) to delete a friend list.

Sample code:

```
// Delete a friend listV2TimCallback deleteFriendsgroup = await friendshipManager.deleteFriendGroup(groupNameList: ['Friend list 1']);
```

### Renaming a friend list

Call the `renameFriendGroup` API ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_friendship_manager/V2TIMFriendshipManager/renameFriendGroup.html)) to rename a friend list.

Sample code:

```
// Rename a friend listV2TimCallback rename = await friendshipManager.renameFriendGroup(newName: "New friend list 1",oldName: 'Friend list 1');
```

### Getting a friend list

Call the `getFriendGroups` API ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_friendship_manager/V2TIMFriendshipManager/getFriendGroups.html)) to get a friend list.

Sample code:

```
// Get the information of a friend list by list nameV2TimValueCallback<List<V2TimFriendGroup>> friendGrous = await friendshipManager.getFriendGroups(groupNameList: ['Friend list 1']);
```

### Adding a friend to a list

Call the `addFriendsToFriendGroup` API ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_friendship_manager/V2TIMFriendshipManager/addFriendsToFriendGroup.html)) to add a friend to a list.

Sample code:

```
// Add a friend to a friend listV2TimValueCallback<List<V2TimFriendOperationResult>> addToFrindgroups = await friendshipManager.addFriendsToFriendGroup(groupName: "Friend list 1",userIDList: ['user1']);
```

### Removing a friend from a list

Call `deleteFriendsFromFriendGroup` ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_friendship_manager/V2TIMFriendshipManager/deleteFriendsFromFriendGroup.html)) to remove a friend from a list.

Sample code:

```
// Remove a friend from a listV2TimValueCallback<List<V2TimFriendOperationResult>> deletefromFriendsGrousps = await friendshipManager.deleteFriendsFromFriendGroup(groupName: "Friend list 1", userIDList: ['user1']);
```


---
*Source: [https://trtc.io/document/48154](https://trtc.io/document/48154)*
