# Follow

## Description

- **Following** feature allows users to follow other users they are interested in, so they can timely receive the latest news, feeds, or event information of these users. The system can provide personalized content recommendations based on the user's following list.
- **Followers** feature refers to the state of a user being followed by others. When user A follows user B, A becomes a follower of B. Users can view the count of followers, followers list, or profile of followers on their own profile page.

Through the features, you can create an active, interconnected user network, promoting the spread of information and the building of the community.

> **Note:**This feature is available only in SDK v7.8 or later.This feature is only supported by the Pro, Pro-plus, and Enterprise Edition, Please [purchase the Pro, Pro-plus, or Enterprise](https://console.trtc.io/subscription/buy/chat?language=en) to use it.

## Display Effect

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6aeb3b1269c911ef9664525400d5f8ef.png)

## API Description

### Follow user

You can call the `followUser` API to follow specified users.

Sample code:

```
V2TimValueCallback<List<V2TimFollowOperationResult>> followResults = await friendshipManager.followUser(userIDList: ['user1']);if (followResults.code == 0) {    // Follow users successfully    followResults.data?.forEach((element) {        element?.userID;        element?.resultCode;        element.resultInfo;    });}
```

> **Note:**This API supports following up to 20 users at a time (excluding yourself, you can follow any other user).The maximum number of followers per user is 5000, and there is no limit on the number of fan users.

### Unfollow user

You can call the `unfollowUser` API to unfollow the specified users.

Sample code:

```
V2TimValueCallback<List<V2TimFollowOperationResult>> unfollowResults = await friendshipManager.unFollowUser(userIDList: ['user1']);if (unfollowResults.code == 0) {        // Unfollow users successfully        unfollowResults.data?.forEach((element) {        element?.userID;  // User ID        element?.resultCode;  // Operation result code        element?.resultInfo;  // Operation result information    });}
```

> **Note:**
> This API supports unfollowing up to 20 users at a time.

### Get my following list

You can use the `getMyFollowingList` API to pull the list of users you are following.

Sample code:

```
V2TimValueCallback<V2TimUserInfoResult> userInfoListRes = await friendshipManager.getMyFollowingList(nextCursor: "");if (userInfoListRes.code == 0) {    // Get following list successfully    userInfoListRes.data?.nextCursor;  // The next cursor for paging pull    userInfoListRes.data?.userFullInfoList?.forEach((element) {        element?.userID;  // User ID        element?.nickName;  // User nick name        element?.faceUrl;  // User avatar url        element?.selfSignature;  // User signature        element?.gender;  // User gender        element?.allowType;  // User option for allowing others to add friends        element?.customInfo;  // User coustom info        element?.role;  // User role        element?.level;  // User level        element?.birthday;  // User birthday    });}
```

> **Note:**This API returns a maximum of 500 users at a time.When pulling the API for the first time, you can enter the nextCursor parameter of the API as "". If the returned nextCursor is not "" after the callback is successful, you can pass this value and pull it again until nextCursor returns "", indicating that the pull is complete.

### Get my followers list

You can use the `getMyFollowersList` API to fetch your own list of follower users.

Sample code:

```
getMyFollowersList
```

> **Note:**This API returns a maximum of 500 users at a time.For the first fetch, you can fill the `nextCursor` parameter of the API with `""`. After a successful callback, if the returned `nextCursor` is not `""`, you can input this value to fetch again, until `nextCursor` returns `""`, indicating that the fetch is complete.

### Get mutual followers list

You can call the `getMutualFollowersList` API to pull the list of users who mutually follow each other (**Users who mutually follow can find each other in their following and followers lists**).

Sample code:

```
getMutualFollowersList
```

> **Note:**This API returns a maximum of 500 users at a time.For the first fetch, you can fill the `nextCursor` parameter of the API with `""`. After a successful callback, if the returned `nextCursor` is not `""`, you can input this value to fetch again, until `nextCursor` returns `""`, indicating that the fetch is complete.

### Get the count of following/followers/mutual followers

You can call the `getUserFollowInfo` API  to get the count of following/followers/mutual followers for specific users.

Sample code:

```
V2TimValueCallback<List<V2TimFollowInfo>> userFollowInfoListRes = await friendshipManager.getUserFollowInfo(userIDList:  ['user1']);if (userFollowInfoListRes.code == 0) {    // Obtained successfully    userFollowInfoListRes.data?.forEach((element) {        element?.resultCode;  // Result code: 0 indicates success, while any other value indicates failure        element?.resultInfo;  // Result information        element?.userID;  // User ID        element?.followingCount;  // The count of users this user is following        element?.followersCount;  // The count of followers for this user        element?.mutualFollowersCount;  // The count of mutual followers for this user    });}
```

### Check follow type

You can call the `checkFollowType` API to check your following relationship with specified users.

In the successful callback, you can obtain your relationship with the specified user through the `followType` of  `V2TimFollowTypeCheckResul`:

| `V2TimFollowTypeCheckResult.followType` | Relationship with yourself |
| --- | --- |
| `V2TIM_FOLLOW_TYPE_NONE = 0` | No following relationship |
| `V2TIM_FOLLOW_TYPE_IN_MY_FOLLOWING_LIST = 1` | The user is only in my following list |
| `V2TIM_FOLLOW_TYPE_IN_MY_FOLLOWERS_LIST = 2` | The user is only in my followers list |
| `V2TIM_FOLLOW_TYPE_IN_BOTH_FOLLOWERS_LIST = 3` | Mutually follow with the user (the user is both in my following list and in my followers list) |

Sample code:

```
V2TimValueCallback<List<V2TimFollowTypeCheckResult>> followTypeCheckRes = await friendshipManager.checkFollowType(userIDList:  ['user1']);if (followTypeCheckRes.code == 0) {    // Checked the follow relationship successfully    followTypeCheckRes.data?.forEach((element) {        element?.resultCode;  // Result code: 0 indicates success, while any other value indicates failure        element?.resultInfo;  // Result information        element?.userID;  // User ID        element?.followType;  // Type of following relationship    });}
```

> **Note:**The frequency limit of `checkFollowType` API is up to 20 calls within 5 seconds, and each call can support up to 100 users.

### Notifications

The specific list change notifications are as follows:

| List Change Notification | Description |
| --- | --- |
| Follow List Change Notification `onMyFollowingListChanged` | When the `isAdd` in the notification is `true`, it signifies a notification for **adding a user** to the list, and at this time, **the complete user profile is returned**When the `isAdd` in the notification is `false`, it signifies a notification for **deleting a user** from the list, and at this time, **only the user ID is included in the returned user profile** |
| Followers List Change Notification `onMyFollowersListChanged` |  |
| Mutual Followers List Change Notification `onMutualFollowersListChanged` |  |

> **Note:**To receive notifications for the aforementioned events, please call `addFriendListener` beforehand to add a relationship event listener.

### Notifications of adding users to a list

Suppose there are two users `Alice` and `Bob`. During the process of mutual following, the related list change notifications and relationship changes are as follows:

| Event | `Alice` |  | `Bob` |  |
| --- | --- | --- | --- | --- |
|  | Notifications received | Relationship with `Bob` | Notifications received | Relationship with `Alice` |
| `Alice` follows `Bob` | [Notification for adding users to following list](https://www.tencentcloud.com/document/product/1047/64330#onMyFollowingListChanged) | [Follow](https://www.tencentcloud.com/document/product/1047/64330#V2TIM_FOLLOW_TYPE_IN_MY_FOLLOWING_LIST) | [Notification for adding users to followers list](https://www.tencentcloud.com/document/product/1047/64330#onMyFollowersListChanged) | [Follower](https://www.tencentcloud.com/document/product/1047/64330#V2TIM_FOLLOW_TYPE_IN_MY_FOLLOWERS_LIST) |
| `Bob` follows `Alice` | [Notification for adding users to followers list](https://www.tencentcloud.com/document/product/1047/64330#onMyFollowersListChanged) [Notification for adding users to mutual followers list](https://www.tencentcloud.com/document/product/1047/64330#onMutualFollowersListChanged) | [Mutual follower](https://www.tencentcloud.com/document/product/1047/64330#V2TIM_FOLLOW_TYPE_IN_BOTH_FOLLOWERS_LIST) | [Notification for adding users to following list](https://www.tencentcloud.com/document/product/1047/64330#onMyFollowingListChanged) [Notification for adding users to mutual followers list](https://www.tencentcloud.com/document/product/1047/64330#onMutualFollowersListChanged) | [Mutual follower](https://www.tencentcloud.com/document/product/1047/64330#V2TIM_FOLLOW_TYPE_IN_BOTH_FOLLOWERS_LIST) |

### Notifications of deleting users from a list

Assuming there are two users, `Alice` and `Bob`, who are mutual followers, during the process of mutually unfollowing, the related list change notifications and relationship changes are as follows:

| Event | `Alice` |  | `Bob` |  |
| --- | --- | --- | --- | --- |
|  | Notifications received | Relationship with `Bob` | Notifications received | Relationship with `Alice` |
| `Alice` unfollows  `Bob` | [Notification for deleting users from following list](https://www.tencentcloud.com/document/product/1047/64330#onMyFollowingListChanged) [Notification for deleting users from mutual followers list](https://www.tencentcloud.com/document/product/1047/64330#onMutualFollowersListChanged) | [Follower](https://www.tencentcloud.com/document/product/1047/64330#V2TIM_FOLLOW_TYPE_IN_MY_FOLLOWERS_LIST) | [Notification for deleting users from followers list](https://www.tencentcloud.com/document/product/1047/64330#onMyFollowersListChanged) [Notification for deleting users from mutual follow list](https://www.tencentcloud.com/document/product/1047/64330#onMutualFollowersListChanged) | [Follow](https://www.tencentcloud.com/document/product/1047/64330#V2TIM_FOLLOW_TYPE_IN_MY_FOLLOWING_LIST) |
| `Bob` unfollows  `Alice` | [Notification for deleting users from followers list](https://www.tencentcloud.com/document/product/1047/64330#onMyFollowersListChanged) | [No following relationship](https://www.tencentcloud.com/document/product/1047/64330#V2TIM_FOLLOW_TYPE_NONE) | [Notification for deleting users from following list](https://www.tencentcloud.com/document/product/1047/64330#onMyFollowingListChanged) | [No following relationship](https://www.tencentcloud.com/document/product/1047/64330#V2TIM_FOLLOW_TYPE_NONE) |

Sample code:

```
V2TimFriendshipListener listener = V2TimFriendshipListener(    OnMyFollowingListChanged: (List<V2TimUserFullInfo> userInfoList, bool isAdd) async {       if (isAdd) {            // Receive notification of users added to following list        } else {            // Receive notification of users deleted from following list        }    },    OnMyFollowersListChanged: (List<V2TimUserFullInfo> userInfoList, bool isAdd) async {        if (isAdd) {            // Receive notification of users added to followers list        } else {            // Receive notification of users deleted from followers list        }    },    OnMutualFollowersListChanged: (List<V2TimUserFullInfo> userInfoList, bool isAdd) async {        if (isAdd) {            // Receive notification of users added to  mutual followers list        } else {            // Receive notification of users deleted from mutual follow list        }    }    // Other member functions ...);// Add a relationship chain listenerTencentImSDKPlugin.v2TIMManager.getFriendshipManager().addFriendListener(listener: listener);// Remove a relationship chain listenerfriendshipManager.removeFriendListener(listener : friendshipListener);
```

## Contact Us

If you have any questions about this article, feel free to join the [Telegram Technical Group](https://t.me/+EPk6TMZEZMM5OGY1), where you will receive reliable technical support.


---
*Source: [https://trtc.io/document/64330](https://trtc.io/document/64330)*
