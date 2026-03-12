# Group Profile

## Feature Overview

The group profile refers to the information about the group, the attributes of which are in the `Group` core class.

## Getting the Group Profile

##### **API**

```
chat.getGroupProfile(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | Group ID |
| groupCustomFieldFilter | Array \| undefined | Custom group field filter. You can specify the custom group field to be obtained. For more information, see [Custom Group Field](https://console.trtc.io/chat/qun-setting). |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.getGroupProfile({ groupID: 'group1', groupCustomFieldFilter: ['key1','key2'] });promise.then(function(imResponse) {  console.log(imResponse.data.group);}).catch(function(imError){  console.warn('getGroupProfile error:', imError); // Failed to obtain the detailed group profile});
```

## Modifying the Group Profile

> **Note:**This API does not support modifying the maximum number of group members. If modification is needed, please use the [REST API](https://trtc.io/document/34962?product=chat&menulabel=serverapis).This API can modify the group's `inviteOption`.Group profile change notification, different types of groups have different notification methods. For details, please refer to [Group System](https://trtc.io/document/33529?platform=web&product=chat&menulabel=uikit).AVChatRoom does not support setting `inviteOption`.

##### **API**

```
chat.updateGroupProfile(options);
```

##### Parameters

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | Group ID |
| name | String \| undefined | Group name, up to 100 bytes, using UTF-8 encoding. |
| avatar | String \| undefined | Group avatar URL, up to 500 bytes. |
| introduction | String \| undefined | Group introduction, up to 400 bytes, using UTF-8 encoding. |
| notification | String \| undefined | Group notice, up to 400 bytes, using UTF-8 encoding. |
| maxMemberNum | Number \| undefined | Maximum number of group members, which is 6,000. |
| muteAllMembers | Boolean \| undefined | Muting all. Valid values:`true`: mute all;`false`: unmute all. |
| joinOption | String | Method to join a group. Valid values:`TencentCloudChat.TYPES.JOIN_OPTIONS_FREE_ACCESS` (free to join)`TencentCloudChat.TYPES.JOIN_OPTIONS_NEED_PERMISSION` (approval required)`TencentCloudChat.TYPES.JOIN_OPTIONS_DISABLE_APPLY` (no group join)**Note:**It cannot be modified for `TencentCloudChat.TYPES.GRP_WORK`, `TencentCloudChat.TYPES.GRP_MEETING`, and `TencentCloudChat.TYPES.GRP_AVCHATROOM` groups. Work groups cannot be joined on request, and meeting groups and AVChatRoom can be joined freely.Note: |
| inviteOption | String | Group inviting option. Valid values:`TencentCloudChat.TYPES.INVITE_OPTIONS_FREE_ACCESS`: allow free group inviting`TencentCloudChat.TYPES.INVITE_OPTIONS_NEED_PERMISSION`: require approval for group inviting`TencentCloudChat.TYPES.INVITE_OPTIONS_DISABLE_INVITE`: forbid group inviting**Note:**For groups of type `TencentCloudChat.TYPES.GRP_AVCHATROOM`, this attribute is not allowed to be modified, while all other types of groups support modification. |
| groupCustomField | Array \| undefined | Custom group field, which is unavailable by default. For more information on how to enable a custom group field, see [Custom Group Field](https://console.trtc.io/chat/qun-setting). |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.updateGroupProfile({  groupID: 'group1',  name: 'new name', // Modify the group name  introduction: 'this is introduction.', // Modify the group introduction  groupCustomField: [{ key: 'group_level', value: 'high'}] // Modify the group custom field});promise.then(function(imResponse) {  console.log(imResponse.data.group) // Detailed group profile after modification}).catch(function(imError){  console.warn('updateGroupProfile error:', imError); // Failed to modify the group profile});
```

```
// muting all group memberslet promise = chat.updateGroupProfile({  groupID: 'group1',  muteAllMembers: true, // true: mute all; false: unmute all});promise.then(function(imResponse) {  console.log(imResponse.data.group) // Detailed group profile after modification}).catch(function(imError){  console.warn('updateGroupProfile error:', imError); // Failed to modify the group profile});
```

```
let promise = chat.updateGroupProfile({  groupID: 'group1',  inviteOption: TencentCloudChat.TYPES.INVITE_OPTIONS_NEED_PERMISSION,});promise.then(function(imResponse) {  console.log(imResponse.data.group) // modify the group details success}).catch(function(imError) {  console.warn('updateGroupProfile error:', imError); // modify the group details error});
```


---
*Source: [https://trtc.io/document/50405](https://trtc.io/document/50405)*
