# Friend Management

## Feature Overview

The Chat SDK supports friend management, and users can add and delete friends and set to send messages only to friends.

> **Note:**By default, Chat SDK does not check the relationship when sending one-to-one messages. This default setting is generally applied in customer service scenarios, where having to friend a customer service agent before chatting is inefficient.
> To implement "adding a friend before sending a message", you can log in to the [Chat Console](https://console.trtc.io/chat/login-message), select **Feature Configuration** > **Login and Message** > **Relationship Check**, and enable **Check Relationship for One-to-One Messages**. After it is enabled, a user can send messages only to friends. If the user sends a message to a non-friend user, the SDK will report error code 20009.

## Getting contacts

Contacts cached in the SDK can be obtained. When the contacts are updated, the SDK will deliver the `TencentCloudChat.EVENT.FRIEND_LIST_UPDATED`event.

##### **API**

```
chat.getFriendList();
```

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.getFriendList();promise.then(function(imResponse) {  const friendList = imResponse.data; // Contacts}).catch(function(imError) {  console.warn('getFriendList error:', imError); // Failed to obtain contacts});
```

## Adding a friend

##### **API**

```
chat.addFriend(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | User ID |
| source | String | Friend source. It consists of two parts: the prefix and the keyword. The former is `AddSource_Type_`, and the latter must be a string of up to 8 bytes. We recommend you use an English word or its abbreviation as the keyword. For example, if the keyword is `Android`, this field will be `AddSource_Type_Android`. |
| wording | String \| undefined | Friending remarks, which can contain up to 256 bytes. |
| type | String \| undefined | Friending method (two-way friending by default). Valid values:`TencentCloudChat.TYPES.SNS_ADD_TYPE_SINGLE` (one-way friending, where user B is in the friend list of user A but not vice versa)`TencentCloudChat.TYPES.SNS_ADD_TYPE_BOTH` (two-way friending, where user B is in the friend list of user A and vice versa) |
| remark | String \| undefined | Friend remarks, which can contain up to 96 bytes. |
| groupName | String \| undefined | List name, which can contain up to 30 bytes. |

##### **Return value**

`Promise`

##### **Examples**

```
// Add a friendlet promise = chat.addFriend({  to: 'user1',  source: 'AddSource_Type_Web',  remark: 'Jane',  groupName: 'Friend',  wording: 'I'm user0',  type: TencentCloudChat.TYPES.SNS_ADD_TYPE_BOTH,});promise.then(function(imResponse) {  // Sent the friend request successfully  const { code } = imResponse.data;  if (code === 30539) {    // 30539 indicates that user1 has set the friend request processing method    // to manually accept friend requests received.    // The SDK will trigger the TencentCloudChat.EVENT.FRIEND_APPLICATION_LIST_UPDATED event.  } else if (code === 0) {    // 0 indicates that user1 has set the friend request processing method    // to automatically accept all friend requests received.    // The SDK will trigger the TencentCloudChat.EVENT.FRIEND_LIST_UPDATED event.  }}).catch(function(imError) {  console.warn('addFriend error:', imError); // Failed to add the friend});
```

## Deleting a friend

Delete friends. Both one-way deletion and two-way deletion are supported.

> **Note:**We recommend you include up to 100 `userID` values in the `userIDList` at a time, as a large data packet may be rejected by the backend, which requires that a data packet not exceed 1 MB.

##### **API**

```
chat.deleteFriend(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| userIDList | Array | List of `userID` values of the friends to be deleted. The number of `userID` values cannot exceed 100 per request. |
| type | String \| undefined | Deletion mode (two-way deletion by default). Valid values:`TencentCloudChat.TYPES.SNS_DELETE_TYPE_SINGLE` (one-way deletion, where user B is deleted from the friend list of user A but not vice versa)`TencentCloudChat.TYPES.SNS_DELETE_TYPE_BOTH` (two-way deletion, where user B is deleted from the friend list of user A and vice versa) |

##### **Return value**

`Promise`

##### **Examples**

```
TencentCloudChat
```

## Checking the friend relationship

##### **API**

```
chat.checkFriend(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| userIDList | Array | List of the `userID` values to be verified. The number of `userID` values cannot exceed 1,000 per request. |
| type | String \| undefined | Verification mode (two-way verification by default). Valid values:`TencentCloudChat.TYPES.SNS_CHECK_TYPE_SINGLE` (one-way verification, where the friend list of user A is checked for user B but not vice versa)`TencentCloudChat.TYPES.SNS_CHECK_TYPE_BOTH `(two-way verification, where the friend list of user A is checked for user B and vice versa) |

##### **Return value**

`Promise`

##### **Examples**

```
TencentCloudChat
```

## Getting the friend profile

Obtain the complete friend data (including standard friend fields and custom friend fields) and the complete profile data (including standard profile fields and custom profile fields) of a specified friend.

##### **API**

```
chat.getFriendProfile(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| userIDList | Array | List of `userID` values of the friends. |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.getFriendProfile({  userIDList: ['user0','user1']});promise.then(function(imResponse) {  const { friendList, failureUserIDList } = imResponse.data;  friendList.forEach((friend) => {  });  failureUserIDList.forEach((item) => {    const { userID, code, message } = item;  });}).catch(function(imError) {  console.warn('getFriendProfile error:', imError);});
```

## Updating friends

Update the relationship chain data of a friend, only supporting updates to `remark` and `friendCustomField`.

##### **API**

```
chat.updateFriend(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| userID | String | `userID` value of a friend |
| remark | String | Friend remarks, which can contain up to 96 bytes. |
| friendCustomField | Array.<Object> | A collection of custom field key-value pairs, which can be used according to the needs of the business side. |

##### **Return value**

`Promise`

##### **Examples**

```
// update friend remarklet promise = chat.updateFriend({  userID: 'user1',  remark: 'helloworld'});promise.then(function(imResponse) {  console.log(imResponse.data);}).catch(function(imError) {  console.warn('getFriendProfile error:', imError);});
```

```
let promise = chat.updateFriend({  userID: 'user1',  friendCustomField: [    { key: 'Tag_SNS_Custom_test1', value: 'hello' },    { key: 'Tag_SNS_Custom_test2', value: 'world' },  ]});promise.then(function(imResponse) {  console.log(imResponse.data);}).catch(function(imError) {  console.warn('getFriendProfile error:', imError);});
```

## Getting the friend request list

Get  the friend request list cached by the SDK. When there is an update to the friend request list, the SDK will dispatch the event TencentCloudChat.EVENT.FRIEND_APPLICATION_LIST_UPDATED.

> **Note:**If the `allowType` in your profile (obtained through the `getMyProfile` interface) is set to `TencentCloudChat.TYPES.ALLOW_TYPE_ALLOW_ANY` (when being added as a friend: allowing anyone to add oneself as a friend), this interface will not be able to pull the friend request list.

##### **API**

```
chat.getFriendApplicationList();
```

##### **Parameters**

None

##### **Return value**

`Promise`

##### **Examples**

```
// update friend remarklet promise = chat.updateFriend({  userID: 'user1',  remark: 'helloworld'});promise.then(function(imResponse) {  console.log(imResponse.data);}).catch(function(imError) {  console.warn('getFriendProfile error:', imError);});
```

## Accepting a friend request

##### **API**

```
chat.acceptFriendApplication(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| userID | String | The `userID` of the pending friend request. |
| remark | String | Friend remarks, which can contain up to 96 bytes. |
| type | String | `TencentCloudChat.TYPES.SNS_APPLICATION_AGREE` - Agree to add as a one-way friend.`TencentCloudChat.TYPES.SNS_APPLICATION_AGREE_AND_ADD` - Agree and add as a two-way friend. |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.acceptFriendApplication({  userID: 'user1',  remark: 'My Customer Service 1',  type: TencentCloudChat.TYPES.SNS_APPLICATION_AGREE_AND_ADD});promise.then(function(imResponse) {}).catch(function(imError) {  console.warn('acceptFriendApplication error:', imError);});
```

## Refusing a friend request

##### **API**

```
chat.refuseFriendApplication(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| userID | String | The `userID` of the pending friend request. |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.refuseFriendApplication({  userID: 'user1',});promise.then(function(imResponse) {}).catch(function(imError) {  console.warn('refuseFriendApplication error:', imError);});
```

## Deleting a friend request

##### **API**

```
chat.deleteFriendApplication(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| userID | String | The `userID` of the pending friend request. |
| type | String | `TencentCloudChat.TYPES.SNS_APPLICATION_AGREE` - Agree to add as a one-way friend.`TencentCloudChat.TYPES.SNS_APPLICATION_AGREE_AND_ADD` - Agree and add as a two-way friend. |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.refuseFriendApplication({  userID: 'user1',});promise.then(function(imResponse) {}).catch(function(imError) {  console.warn('refuseFriendApplication error:', imError);});
```

## Reporting the friend request has been read

##### **API**

```
chat.setFriendApplicationRead();
```

##### **Parameters**

None

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.setFriendApplicationRead();promise.then(function(imResponse) {}).catch(function(imError) {  console.warn('setFriendApplicationRead error:', imError);});
```


---
*Source: [https://trtc.io/document/48158](https://trtc.io/document/48158)*
