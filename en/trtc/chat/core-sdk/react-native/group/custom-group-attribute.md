# Custom Group Attribute

## Feature Overview

With group attributes, you can manage the seats of audio chat rooms. When a user mics on, you can set a group attribute to manage the information of the user. When the user mics off, you can delete the group attribute. Other members can get the list of group attributes to display the seat list.

> **Note:**Topic does not support group attributes.

The group attribute feature has the following characteristics:

1. You can configure up to 16 group attributes. The size of each group attribute can be up to 4 KB, and the total size of all group attributes can be up to 16 KB. When you modify group attributes for the first time after each successful login, call `getGroupAttributes` to pull the latest group attributes before you initiate the modification operation again.
2. When multiple users modify the same group attributes at the same time, only the first user can execute successfully, and other users will receive the 10056 error code. After receiving this error code, please call `getGroupAttributes` to update the locally stored group attributes to the latest before you initiate the modification operation.
3. Before you use this feature in an AVChatRoom after successful login, you need to call the `joinGroup`API to join the audio-video group. For a public group (Public), meeting group (Meeting), work group (Work), and community group (Community), you do not need to join the group again.

### Initializing group attributes

The access side needs to control the operation permissions of this interface according to the application scenario. After successful initialization, all group members will receive a `GROUP_ATTRIBUTES_UPDATED` event.

##### **API**

```
chat.initGroupAttributes(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | Group ID |
| groupAttributes | Object | Group attributes |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.initGroupAttributes({  groupID: 'group1',  groupAttributes: { key1: 'value1', key2: 'value2' }});promise.then(function(imResponse) {  console.log(imResponse.data.groupAttributes); // Group attributes initialized successfully}).catch(function(imError) {  console.warn('initGroupAttributes error:', imError); // Error information});
```

### Setting group attributes

##### **API**

```
chat.setGroupAttributes(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | Group ID |
| groupAttributes | Object | Group attributes |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.setGroupAttributes({  groupID: 'group1',  groupAttributes: { key1: 'value1', key2: 'value2' }});promise.then(function(imResponse) { // Set successfully  console.log(imResponse.data.groupAttributes); // Group attributes set successfully}).catch(function(imError) { // Setting failed  console.warn('setGroupAttributes error:', imError); // Error information});
```

### Deleting group attributes

> **Noteï¼**To delete specified group attributes (key-value pairs), pass in a non-empty array for `keyList`. To delete all group attributes, pass in an empty array for `keyList`.

##### **API**

```
chat.deleteGroupAttributes(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | Group ID |
| keyList | Array | List of keys of the group attributes |

##### **Return value**

`Promise`

##### **Examples**

```
// Delete the `key-value` of the specified group attributeslet promise = chat.deleteGroupAttributes({  groupID: 'group1',  keyList: ['key1', 'key2']});promise.then(function(imResponse) {  console.log(imResponse.data.keyList); // List of group attributes deleted successfully}).catch(function(imError) {  console.warn('deleteGroupAttributes error:', imError); // Error information});
```

```
// Delete all group attributeslet promise = chat.deleteGroupAttributes({  groupID: 'group1',  keyList: []});promise.then(function(imResponse) {  console.log(imResponse.data.keyList); // List of group attributes deleted successfully}).catch(function(imError) {  console.warn('deleteGroupAttributes error:', imError); // Error information});
```

### Getting group attributes

> **Noteï¼**To get specified group attributes, pass in a non-empty array for `keyList`. To get all group attributes, pass in an empty array for `keyList`.

##### **API**

```
chat.getGroupAttributes(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | Group ID |
| keyList | Array | List of keys of the group attributes |

##### **Return value**

`Promise`

##### **Examples**

```
// Get specified group attributeslet promise = chat.getGroupAttributes({  groupID: 'group1',  keyList: ['key1', 'key2']});promise.then(function(imResponse) { // Got successfully  console.log(imResponse.data.groupAttributes); // Specified group attributes}).catch(function(imError) { // Getting failed  console.warn('getGroupAttributes error:', imError); // Error information});
```

```
// Get all group attributeslet promise = chat.getGroupAttributes({  groupID: 'group1',  keyList: []});promise.then(function(imResponse) { // Got successfully  console.log(imResponse.data.groupAttributes); // All group attributes}).catch(function(imError) { // Getting failed  console.warn('getGroupAttributes error:', imError); // Error information});
```

### Listening for group attributes update event

##### Examples

```
let onGroupAttributesUpdated = function(event) {   const groupID = event.data.groupID // Group ID   const groupAttributes = event.data.groupAttributes //Updated group properties   console.log(event.data);};chat.on(TencentCloudChat.EVENT.GROUP_ATTRIBUTES_UPDATED, onGroupAttributesUpdated);
```


---
*Source: [https://trtc.io/document/50408](https://trtc.io/document/50408)*
