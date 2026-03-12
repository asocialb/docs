# Send a Message

## Chat

## UI Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dc0473afcbdd11ef8c8a525400454e06.png)

## Creating a Message

### Creating a text message

This API is used to create a text message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send a text message.

**API**

```
chat.createTextMessage(options);
```

**Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C` (one-to-one conversation)`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. This attribute is supported by v2.10.2 or later |
| receiverList | Array \| undefined | The list of group members who can receive targeted messages (not applicable to Community group and Audio-video group) |
| isSupportExtension | Boolean | Whether message extensions are supported: `true` (supported) or `false` (not supported) (requires you to purchase the flagship package) |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| text | String | Message text content |

##### **Return value**

`Message`

##### **Examples**

```
// 1. Create a message instance. The returned instance can be displayed on the screen.let message = chat.createTextMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  // priority: TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL,  payload: {    text: 'Hello world!'  },  // To use the read receipt feature, you need to purchase the Pro edition ãPro Plus edition or Enterprise edition  // and set `needReadReceipt` to `true` when creating a message.  needReadReceipt: true  // cloudCustomData: 'your cloud custom data'});// 2. Send the message.let promise = chat.sendMessage(message);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

```
// Send targeted group messages// targeted group messages are not counted towards conversation unreadCount// and the receiverList supports up to 50 recipients.let message = chat.createTextMessage({  to: 'group1',  conversationType: TencentCloudChat.TYPES.CONV_GROUP,  payload: {    text: 'Hello world!'  },  receiverList: ['user0', 'user1']});let promise = chat.sendMessage(message);promise.then(function(imResponse) {  console.log(imResponse);}).catch(function(imError) {  console.warn('sendMessage error:', imError);});
```

### Creating an @mention message

This API is used to create an @mention text message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send a text message.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f58f060acbdd11efa2ff52540044a08e.png)

> **Note:**It applies only to group chats, and @all members is not supported for a community and its topic.Creating a group @ message does not support specifying `receiverList`.

##### **API**

```
chat.createTextAtMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| text | String | Text content |
| atUserList | Array | List of users that need to be mentioned (@). To mention (@) all, pass in `TencentCloudChat.TYPES.MSG_AT_ALL`. For example, to mention (@) `denny` and `lucy` as well as all members, pass in` ['denny', 'lucy', TencentCloudChat.TYPES.MSG_AT_ALL] `for `atUserList`. |

##### **Return value**

`Message`

##### **Examples**

```
// 1. Create a message instance. The returned instance can be displayed on the screen.let message = chat.createTextAtMessage({  to: 'group1',  conversationType: TencentCloudChat.TYPES.CONV_GROUP,  // priority: TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL,  payload: {    text: '@denny @lucy @all Dinner tonight. Reply 1 if you receive this message',    // 'denny' and 'lucy' are `userID` values, not nicknames    atUserList: ['denny', 'lucy', TencentCloudChat.TYPES.MSG_AT_ALL]  },  // cloudCustomData: 'your cloud custom data'});// 2. Send the message.let promise = chat.sendMessage(message);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

### Creating an image message

This API is used to create an image message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send an image message.

##### **API**

```
chat.createImageMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | Message receiver |
| conversationType | String | Conversation type. Valid values: `TencentCloudChat.TYPES.CONV_C2C`, `TencentCloudChat.TYPES.CONV_GROUP`. |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| onProgress | function | Callback function for getting the upload progress |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| file | HTMLInputElement \| Object | It is used to select a DOM node (web) or `File` object (web) of the image. The SDK reads the data contained in this parameter and uploads the image. |

##### **Return value**

`Message`

##### **Examples**

```
// Example 1: Sending an image message on web - passing in a DOM node// 1. Create a message instance. The returned instance can be displayed on the screen.let message = chat.createImageMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  // priority: TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL,  payload: {    file: document.getElementById('imagePicker'),  },  // cloudCustomData: 'your cloud custom data'  onProgress: function(event) { console.log('file uploading:', event) }});// 2. Send the message.let promise = chat.sendMessage(message);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

```
// Example 2: Sending an image message on web - passing in a File object// Add a message input box with the ID set to `testPasteInput`document.getElementById('testPasteInput').addEventListener('paste', function(e) {  let clipboardData = e.clipboardData;  let file;  let fileCopy;  if (clipboardData && clipboardData.files && clipboardData.files.length > 0) {    file = clipboardData.files[0];    // After the image message is sent successfully    // the content pointed to by `file` may be cleared by the browser.    // If you have extra rendering needs, you can copy the data in advance.    fileCopy = file.slice();  }  if (typeof file === 'undefined') {    console.warn('The `file` is `undefined`. Check for the compatibility of the code or browser.');    return;  }  // 1. Create a message instance. The returned instance can be displayed on the screen.  let message = chat.createImageMessage({    to: 'user1',    conversationType: TencentCloudChat.TYPES.CONV_C2C,    payload: {      file: file    },    onProgress: function(event) { console.log('file uploading:', event) }  });  // 2. Send the message.  let promise = chat.sendMessage(message);  promise.then(function(imResponse) {    // The message sent successfully    console.log(imResponse);  }).catch(function(imError) {    // Failed to send the message    console.warn('sendMessage error:', imError);  });});
```

```
// Sending an image on wx mini-programwx.chooseImage({  sourceType: ['album'],  count: 1,  success: function (res) {    let message = chat.createImageMessage({      to: 'user1',      conversationType: TencentCloudChat.TYPES.CONV_C2C,      payload: { file: res },      onProgress: function(event) { console.log('file uploading:', event) }    });     let promise = chat.sendMessage(message);    promise.then(function(imResponse) {      console.log(imResponse);    }).catch(function(imError) {      console.warn('sendMessage error:', imError);    });  }})
```

```
// Sending an image on uni-appuni.chooseMedia({  count: 1,  mediaType: ['image'],  sizeType: ['original', 'compressed'],  sourceType: ['album'],  success: function(res) {    let message = chat.createImageMessage({      to: 'user1',      conversationType: TencentCloudChat.TYPES.CONV_C2C,      payload: { file: res },      onProgress: function(event) { console.log('file uploading:', event) }    });     let promise = chat.sendMessage(message);    promise.then(function(imResponse) {      console.log(imResponse);    }).catch(function(imError) {      console.warn('sendMessage error:', imError);    });  }});
```

### Creating an audio message

This API is used to create an audio message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send an audio message.

##### **API**

```
chat.createAudioMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | Message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C``TencentCloudChat.TYPES.CONV_GROUP` |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| file | Object | Audio file obtained after recording |

##### **Return value**

`Message`

##### **Examples**

```
// Sending an audio on wx mini-programconst recorderManager = wx.getRecorderManager();const recordOptions = {  duration: 60000,   sampleRate: 44100,  numberOfChannels: 1,  encodeBitRate: 192000,  format: 'aac'};recorderManager.onError(function(errMsg) {  console.warn('recorder error:', errMsg);});recorderManager.onStop(function(res) {  console.log('recorder stop', res);  const message = chat.createAudioMessage({    to: 'user1',    conversationType: TencentCloudChat.TYPES.CONV_C2C,    payload: {      file: res    },  });  let promise = chat.sendMessage(message);  promise.then(function(imResponse) {    console.log(imResponse);  }).catch(function(imError) {    console.warn('sendMessage error:', imError);  });});recorderManager.start(recordOptions);
```

```
// Sending an audio on weblet recorder = new Recorder({  sampleBits: 16,  sampleRate: 16000,  numChannels: 1,});let startTs;recorder.start().then(() => {  startTs = Date.now();}, (error) => {  console.log(`${error.name} : ${error.message}`);});recorder.stop();let duration = Date.now() - startTs; // unitï¼mslet wavBlob = recorder.getWAVBlob();// blob -> Filelet audioFile = new File([wavBlob], 'hello.wav', { type: 'wav' });audioFile.duration = duration;let message = chat.createAudioMessage({  to: 'user1',  conversationType: 'C2C',  payload: {    file: audioFile  }});let promise = chat.sendMessage(message);promise.then(function(imResponse) {  console.log(imResponse);}).catch(function(imError) {  console.warn('sendMessage error:', imError);});
```

### Creating a video message

This API is used to create a video message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send a video message.

##### **API**

```
chat.createVideoMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | Message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C``TencentCloudChat.TYPES.CONV_GROUP` |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| file | HTMLInputElement \| File \| Object | Video file obtained after recording. |

##### **Return value**

`Message`

##### **Examples**

```
// Sending a video message on wx mini-programwx.chooseVideo({  sourceType: ['album', 'camera'],  maxDuration: 60,  camera: 'back',  success (res) {    let message = chat.createVideoMessage({      to: 'user1',      conversationType: TencentCloudChat.TYPES.CONV_C2C,      payload: {        file: res      },      // cloudCustomData: 'your cloud custom data'      onProgress: function(event) { console.log('file uploading:', event) }    })       let promise = chat.sendMessage(message);    promise.then(function(imResponse) {      console.log(imResponse);    }).catch(function(imError) {      console.warn('sendMessage error:', imError);    });  }})
```

```
// Example: Sending a video message on web// 1. Get the video file by passing in the DOM node.// 2. Create a message instance.const message = chat.createVideoMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: {    file: document.getElementById('videoPicker') // Alternatively, use `event.target`  },  onProgress: function(event) { console.log('file uploading:', event) }});// 3. Send the message.let promise = chat.sendMessage(message);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

```
// Sending a video message on uni-appuni.chooseVideo({  count: 1,  sourceType: ['camera', 'album'],  maxDuration: 60,  camera: 'back',  success: function(res) {    let message = chat.createVideoMessage({      to: 'user1',      conversationType: TencentCloudChat.TYPES.CONV_C2C,      payload: { file: res },      onProgress: function(event) { console.log('file uploading:', event) }    });       let promise = chat.sendMessage(message);    promise.then(function(imResponse) {      console.log(imResponse);    }).catch(function(imError) {      console.warn('sendMessage error:', imError);    });  }})
```

### Creating a custom message

This API is used to create a custom message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send a custom message. When the current SDK capabilities cannot meet your needs, you can customize messages.

##### **API**

```
chat.createCustomMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C` (one-to-one conversation)`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| data | String | Data of the custom message |
| description | String | Description of the custom message |
| extension | String | Extension of the custom message |

##### **Return value**

`Message`

##### **Examples**

```
// Example: Using a custom message to implement dice rolling// 1. Define the random function.function random(min, max) {  return Math.floor(Math.random() * (max - min + 1) + min);}// 2. Create a message instance. The returned instance can be displayed on the screen.let message = chat.createCustomMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: {    data: 'dice', // Used to identify the message as a dice message    description: String(random(1,6)), // Get the outcome    extension: ''  }});// 3. Send the message.let promise = chat.sendMessage(message);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

### Creating an emoji message

This API is used to create an emoji message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send an emoji message.

##### **API**

```
chat.createFaceMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C` (one-to-one conversation)`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| index | Number | Emoji index, which is customized by the user |
| data | String | Extra data |

##### **Return value**

`Message`

##### **Examples**

```
// Send an emoji message on web// 1. Create a message instance. The returned instance can be displayed on the screen.let message = chat.createFaceMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: {    index: 1, // Number. Emoji index, which is customized by the user    data: 'tt00' // String. Extra data  },  // cloudCustomData: 'your cloud custom data'});// 2. Send the message.let promise = chat.sendMessage(message);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

### Creating a file message

This API is used to create a file message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send a file message.

##### **API**

```
chat.createFileMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C` (client to client conversation)`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| onProgress | function | Callback function for getting the upload progress |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| file | HTMLInputElement \| File \| Object | It is used to select a DOM node or `File` object of the file on web, or the success callback parameter of the uni.chooseFile API. The SDK reads the data contained in this parameter and uploads the file. |

##### **Return value**

`Message`

##### **Examples**

```
// Example 1: Sending a file message on web - passing in a DOM node// 1. Create a file message instance. The returned instance can be displayed on the screen.let message = chat.createFileMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: {    file: document.getElementById('filePicker'),  },  // cloudCustomData: 'your cloud custom data'  onProgress: function(event) { console.log('file uploading:', event) }});// 2. Send the message.let promise = chat.sendMessage(message);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

```
// Example 2: Sending a file message on web - passing in a File object// Add a message input box with the ID set to `testPasteInput`,   let clipboardData = e.clipboardData;  let file;  let fileCopy;  if (clipboardData && clipboardData.files && clipboardData.files.length > 0) {    file = clipboardData.files[0];    // After the image message is sent successfully    // the content pointed to by `file` may be cleared by the browser.     // If you have extra rendering needs, you can copy the data in advance.    fileCopy = file.slice();  }  if (typeof file === 'undefined') {    console.warn('The `file` is `undefined`. Check for the compatibility of the code or browser.');    return;  }  // 1. Create a message instance. The returned instance can be displayed on the screen.  let message = chat.createFileMessage({    to: 'user1',    conversationType: TencentCloudChat.TYPES.CONV_C2C,    payload: {      file: file    },    onProgress: function(event) { console.log('file uploading:', event) }  });  // 2. Send the message.  let promise = chat.sendMessage(message);  promise.then(function(imResponse) {    // The message sent successfully    console.log(imResponse);  }).catch(function(imError) {    // Failed to send the message    console.warn('sendMessage error:', imError);  });});
```

```
// Sending a file message on uni-appuni.chooseFile({  count: 1,  extension:['.zip','.doc'],  success: function(res) {    let message = chat.createFileMessage({      to: 'user1',      conversationType: TencentCloudChat.TYPES.CONV_C2C,      payload: { file: res },      onProgress: function(event) { console.log('file uploading:', event) }    });     let promise = chat.sendMessage(message);    promise.then(function(imResponse) {      console.log(imResponse);    }).catch(function(imError) {      console.warn('sendMessage error:', imError);    });  }});
```

```
// Sending a file message on mini-programwx.chooseMessageFile({  count: 1,  type: 'all',  success: (res) => {    const message = chat.createFileMessage({      to: 'user1',      conversationType: TencentCloudChat.TYPES.CONV_C2C,      payload: { file: res },      onProgress: function(event) { console.log('file uploading:', event) }    });    let promise = chat.sendMessage(message);    promise.then(function(imResponse) {      console.log(imResponse);    }).catch(function(imError) {      console.warn('sendMessage error:', imError);    });  }})ï¼
```

### Creating a geographical location message

This API is used to create a geographical location message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send a geographical location message.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/32e63cfdcbde11ef97675254007c27c5.png)

##### **API**

```
chat.createLocationMessage(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C` (one-to-one conversation)`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| description | String | Description of the geographical location |
| longitude | Number | Longitude |
| latitude | Number | Latitude |

##### **Return value**

`Message`

##### **Examples**

```
// Send a geographical location message on web// 1. Create a message instance. The returned instance can be displayed on the screen.let message = chat.createLocationMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: {    description: 'Tencent Building, No. 10000, Shennan Boulevard, Shenzhen',    longitude: 113.941079, // Longitude    latitude: 22.546103 // Latitude  }});// 2. Send the message.let promise = chat.sendMessage(message);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

### Creating a merged message

This API is used to create a merged message. It returns a message instance, which can be sent by calling the `sendMessage` API when you need to send a merged message.

> **Note:**This API does not support merging messages that failed to be sent. If the message list contains a message that failed to be sent, the API will report an error.

##### **API**

```
chat.createMergerMessage(options);
```

**Parameters**

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| to | String | `userID` or `groupID` of the message receiver |
| conversationType | String | Conversation type. Valid values:`TencentCloudChat.TYPES.CONV_C2C` (one-to-one conversation)`TencentCloudChat.TYPES.CONV_GROUP` (group conversation) |
| priority | String | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| payload | Object | Message content container |
| cloudCustomData | String | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |

The `payload` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| messageList | Array | Merged message list |
| title | String | Title of merged messages, for example, "Chat History of the Talent Center in the Greater Bay Area" |
| abstractList | String | Abstract list. You can set abstract information in different formats for different message types, for example, in the `sender:text` format for a text message, in the `sender:[image]` format for an image message, or in the `sender:[file]` format for a file message. |
| compatibleText | String | Compatibility text. If the SDK on an early version does not support the merged message, the user will receive a text message with the content `${compatibleText}` by default. This field is required. |

##### **Return value**

`Message`

##### **Examples**

```
// 1. Forward group messages to a one-to-one conversation.// `message1`, `message2`, and `message3` are group messages.let mergerMessage = chat.createMergerMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: {    messageList: [message1, message2, message3],    title: 'Chat History of the Talent Center in the Greater Bay Area',    abstractList: ['allen: 666', 'iris: [Image]', 'linda: [File]'],    compatibleText: 'Upgrade your Chat SDK to v2.10.1 or later to view this message.'  },  // cloudCustomData: 'your cloud custom data'});// 2. Send the message.let promise = chat.sendMessage(mergerMessage);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

### Downloading a Merged Message

This API is used to download a merged message. When the merged message sent by the sender is large in size, the SDK will store it in the cloud, and the message receiver needs to download it from the cloud before viewing it.

##### **API**

```
chat.downloadMergerMessage(message);
```

**Parameters**

| Name | Type | Description |
| --- | --- | --- |
| message | Message | Message instance |

##### **Return value**

`Promise`

##### **Examples**

```
// If `downloadKey` exists, the received merged message is stored in the cloud// and needs to be downloaded first.if (message.type === TencentCloudChat.TYPES.MSG_MERGER && message.payload.downloadKey !== '') {  let promise = chat.downloadMergerMessage(message);  promise.then(function(imResponse) {    // After the download is successful    // the SDK will update information such as `message.payload.messageList`.    console.log(imResponse.data);  }).catch(function(imError) {    // Download failed    console.warn('downloadMergerMessage error:', imError);  });}
```

### Forwarding Messages One by One

To forward a single message, create a message identical to the original message through the `createForwardMessage` API first, and then call the `sendMessage` API to send the message.

> **Note:**Supports single forwarding and individual forwarding.

**API**

```
chat.createForwardMessage(message);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| message | Message | Message instance |

##### **Examples**

```
let forwardMessage = chat.createForwardMessage({  to: 'user1',  conversationType: TencentCloudChat.TYPES.CONV_C2C,  payload: message, // The received or sent message instance});// 2. Send the message.let promise = chat.sendMessage(forwardMessage);promise.then(function(imResponse) {  // The message sent successfully  console.log(imResponse);}).catch(function(imError) {  // Failed to send the message  console.warn('sendMessage error:', imError);});
```

## Sending a message

This API is used to send a message. You need to call any of the following message instance creation APIs to create a message instance first before calling this API to send the message instance.

- `createTextMessage`
- `createTextAtMessage`
- `createImageMessage`
- `createAudioMessage`
- `createVideoMessage`
- `createCustomMessage`
- `createFaceMessage`
- `createFileMessage`
- `createLocationMessage`
- `createMergerMessage`
- `createForwardMessage`

> **Note:**When this API is called to send a message instance, the SDK must be in the `ready` status; otherwise, the message instance cannot be sent. The SDK status can be obtained by listening for the `TencentCloudChat.EVENT.SDK_READY` event, which will be triggered when the SDK is in the `ready` status.The `TencentCloudChat.EVENT.MESSAGE_RECEIVED` event must be listened for in order to receive newly pushed one-to-one messages, group messages, group tips, or group system notifications.Messages sent by this API will not trigger the `TencentCloudChat.EVENT.MESSAGE_RECEIVED` event. Messages sent by the same account from another client (or through the RESTful API) will trigger the `TencentCloudChat.EVENT.MESSAGE_RECEIVED` event.Offline push applies only to Android or iOS devices but is not supported for web.`onlineUserOnly` and `messageControlInfo` cannot be used together.Supports counting Community and Topic messages as read.When sending a message to the [System Conversation], the SDK will return error code 2106.The message body size limit is 12KB and is not adjustable; exceeding this limit will result in a message sending failure with error code 80002.After enabling friend relationship checking (Chat Console > Application Configuration > Feature Configuration > Login and Messages > Friend Relationship Checking), Chat will check the friend relationship when initiating a private chat, allowing only friends to send private messages. If a stranger sends a private message, the SDK will return error code 20009.

##### **API**

```
chat.sendMessage(message, options);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| message | Message | Message instance |
| options | Object | Message sending option (message content container), which is optional |

The `options` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| onlineUserOnly | Boolean | It specifies whether the message is sent only to online users and defaults to `false`. If it is set to `true`, the message will not be stored on the roaming server, nor counted as an unread message, nor pushed to the receiver offline. It is suitable for sending unimportant tips such as broadcast notifications. This parameter is not supported when a message is sent in an audio-video group (AVChatRoom). |
| offlinePushInfo | Object | For more information, see [Offline Push](https://intl.cloud.tencent.com/document/product/1047/33525). |
| messageControlInfo | Object | It is a message control configuration item. |

The `offlinePushInfo` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| disablePush | Boolean | `true`: offline push is disabled; `false` (default): offline push is enabled. |
| disableVoipPush | Boolean | `true` to disable VoIP push (default); `false` to enable VoIP push (enabling VoIP push requires enabling offline push simultaneously) |
| title | String | Offline push title. This parameter is used by both iOS and Android. |
| description | String | Offline push content. This parameter will overwrite the offline push display text of the message instance. If the sent message is a custom message, this parameter will overwrite `message.payload.description`. If both `description` and `message.payload.description` are left empty, the receiver cannot receive the offline push notification of the custom message. |
| extension | String | Content passed through by offline push. |
| androidInfo | Object | Android Push Configuration. |
| apnsInfo | Object | iOS Push Configuration. |

The` androidInfo` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| sound | String | Android offline push sound settings. Only supports Huawei, Xiaomi, and Google. For Xiaomi phones running Android 8.0 and above, you must set androidInfo.XiaoMiChannelID.  For Google phones with FCM push on Android 8.0 and above systems to set sound prompts, you must set androidInfo.FCMChannelID. Custom ringtones require setting the path to the sound file. For example: androidInfo.sound = "shake.xxx"Corresponding to the uniapp "nativeResources/android/res/raw/shake.xxx" audio file.Corresponding to the native app's "/res/raw/shake.xxx" audio file. |
| XiaoMiChannelID | String | Notification category (Channel) adaptation field for Xiaomi phones with MIUI 10 and above. |
| OPPOChannelID | String | NotificationChannel adaptation field for OPPO phones running Android 8.0 and above. |
| FCMChannelID | String | Notification channel field for Google phones running Android 8.0 and above. |
| VIVOClassification | Number | VIVO phone push message classification, 0: operational message, 1: system message, default is 1. |
| VIVOCategory | String | Used to identify the message type on VIVO phones. |
| HuaWeiCategory | String | Used to identify the message type on Huawei phones. |
| HuaWeiImage | String | Huawei push notification bar notification image URL.The protocol used must be HTTPS, an example value: https://example.com/image.png.The image file must be less than 512KB, with a recommended size of 40dp x 40dp and rounded corners of 8dp. Images exceeding the recommended specifications may experience compression or incomplete display. The recommended image formats are JPG/JPEG/PNG. |
| HonorImage | String | Honor push notification bar notification image URL.The protocol used must be HTTPS, an example value: https://example.com/image.png.The icon file size must be less than 100KB, with a recommended specification size of 160px x 160px and rounded corners of 32px. Icons exceeding the recommended specifications may experience compression or incomplete display. |
| GoogleImage | String | Google push notification bar notification image URL.The protocol used must be HTTPS, an example value: https://example.com/image.png.The icon file size must be less than 1 MB, icons exceeding the specification size may experience compression or incomplete display. |

The `apnsInfo` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| sound | String | iOS offline push sound settings. When `apnsInfo.sound = TencentCloudChat.TYPES.IOS_OFFLINE_PUSH_NO_SOUND`, it means that no sound will be played upon receipt. When `apnsInfo.sound = TencentCloudChat.TYPES.IOS_OFFLINE_PUSH_DEFAULT_SOUND`, it means that the system sound will be played upon receipt. Custom ringtones require setting the path to the sound file. For example: apnsInfo.sound = "shake.xxx"Corresponding to the uniapp "nativeResources/ios/Resources/shake.xxx" file, the uniapp must be a formal package.Corresponding to the "shake.xxx" audio file in the native Xcode project. |
| ignoreIOSBadge | Boolean | Ignore badge count for offline push (only effective for iOS), default is `false`. When set to `true`, on the iOS receiving end, this message will not increase the unread count on the APP's application icon. |
| disableVoipPush | Boolean | `true` to disable VoIP push (default); `false` to enable VoIP push (enabling VoIP push requires enabling offline push simultaneously) |
| image | String | Identifies the APNs notification bar notification image address. When the client obtains this field, it can display the image on the pop-up window by downloading the image resource.The protocol used must be HTTPS, an example value: https://example.com/image.pngSupports JPEG, GIF, PNG, with a size not exceeding 10 MB.The mutable-content attribute needs to be enabled in the Chat console to support iOS 10 Service Extension features.The resource's key value is "image". |

The `messageControlInfo` is as described below:

| Name | Type | Description |
| --- | --- | --- |
| excludedFromUnreadCount | Boolean | `true`: unreadCount of the conversation is not updated (the message is stored on the roaming server); `false` (default) |
| excludedFromLastMessage | Boolean | `true`: lastMessage of the conversation is not updated (the message is stored on the roaming server); false (default) |
| excludedFromContentModeration | Boolean | `true`: the message is excluded from content moderation. |

##### **Returned Value**

`Promise`

##### **Examples**

```
// If the receiver is offline, the message will be stored on the roaming server// and pushed offline on the precondition that the receiver's application switches to the background// or the process is killed.// The default title and content of offline push are kept.chat.sendMessage(message);
```

```
chat.sendMessage(message, {  // If the receiver is offline, the message will be neither stored on the roaming server  // nor pushed offline.  onlineUserOnly: true});
```

```
chat.sendMessage(message, {  offlinePushInfo: {    // If the receiver is offline, the message will be stored on the roaming server    // but will not be pushed offline.    disablePush: true  }});
```

```
chat.sendMessage(message, {  offlinePushInfo: {    title: '',    description: '',    androidInfo: {       OPPOChannelID: ''    }  }});
```

```
chat.sendMessage(message, {  messageControlInfo: {    // `unreadCount` of the conversation is not updated (the message is stored on the roaming server).    excludedFromUnreadCount: true,    // `lastMessage` of the conversation is not updated (the message is stored on the roaming server).    excludedFromLastMessage: true  }});
```

```
chat.sendMessage(message, {  messageControlInfo: {    excludedFromContentModeration: true,  }});
```

```
// Support VoIP pushchat.sendMessage(message, {  offlinePushInfo: {    disablePush: false,    disableVoipPush: false  }});
```

## API-related Limits

| Feature | Limit Item | Description |
| --- | --- | --- |
| One-to-one/group message | Content length | A one-to-one or group message must be no longer than 12 KB. |
|  | Sending frequency | One-to-one message: No limit for sending one-to-one messages on the client; sending through the RESTful API is subject to the frequency limit. See the corresponding API documentation. Group message: Up to 40 messages can be sent per second per group (regardless of the group type and platform interface, and this limit applies to each group separately). |
|  | Receiving frequency | No limit for one-to-one messages or group messages. |
|  | Size of a single file | SDKs support a maximum file size of 100 MB for any single file to be sent. |

> **Note:**When the number of sent messages exceeds the limit, the backend will first deliver high-priority messages, and messages with the same priority will be delivered randomly. However, if the number of high-priority messages sent in a second exceeds 40, high-priority messages will also be discarded.A message that has been restricted by frequency control is not delivered or stored in the message history, but a success response will be returned to the sender.[Before Group Message Is Sent](https://www.tencentcloud.com/document/product/1047/34374) callback is triggered, but [After a Group Message Is Sent](https://www.tencentcloud.com/document/product/1047/34375) callback is not triggered.The default frequency limit for calling the RESTful API to send group messages is 200 times per second, which is a different concept from the aforementioned "limit of 40 messages per second for each group." Please distinguish it.

Please refer to [Use Limits](https://www.tencentcloud.com/document/product/1047/34381) for more limits.crc


---
*Source: [https://trtc.io/document/47993](https://trtc.io/document/47993)*
