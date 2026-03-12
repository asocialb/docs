# Blocklist

## Feature Description

To block a user's messages, add the user to the blocklist.

## Blocklist

### Blocking a user

Call the `FriendshipAddToBlackList` API ([Details](https://comm.qq.com/im/doc/unity/en/api/FriendshipApi/FriendshipAddToBlackList.html)) to add a user to the blocklist, that is, block the user.

By default, a blocked user does not know that he/she is "blocked". After the user sends a message, the error code indicating that he/she has been blocked will not be returned.
To have the "You have been blocked by the user" error message returned after a blocked user sends a message, you can log in to the [Chat console](https://console.tencentcloud.com/im), select **Feature Configuration** > **Login and Message** > **Blocklist Check**, and disable **Show "Sent successfully" After Sending Messages**. Then the SDK will report error code 20007 after a blocked user sends a message.

```
// Add a user to the blocklistList<string> param = new List<string>  {    "user_id"  };TIMResult res = TencentIMSDK.FriendshipAddToBlackList(param, (int code, string desc, List<FriendResult> result, string user_data)=>{ // Process the async logic});
```

### Unblocking a user

Call `FriendshipDeleteFromBlackList` ([Details](https://comm.qq.com/im/doc/unity/en/api/FriendshipApi/FriendshipDeleteFromBlackList.html)) to remove a user from the blocklist, after which messages from the user can be received.

```
// Remove a user from the blocklistList<string> param = new List<string>  {    "user_id"  };TIMResult res = TencentIMSDK.FriendshipDeleteFromBlackList(param, (int code, string desc, List<FriendResult> result, string user_data)=>{ // Process the async logic});
```

### Getting the blocklist

Call `FriendshipGetBlackList` ([Details](https://comm.qq.com/im/doc/unity/en/api/FriendshipApi/FriendshipGetBlackList.html)) to view how many users have been blocked and manage them.

```
// Get the blocklistTIMResult res = TencentIMSDK.FriendshipGetBlackList((int code, string desc, List<FriendProfile> result, string user_data)=>{ // Process the async logic});
```


---
*Source: [https://trtc.io/document/49567](https://trtc.io/document/49567)*
