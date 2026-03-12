# Signaling

## Listen for signaling events.

> **Note:**Please call this interface to listen for events before calling the `login` interface to avoid missing events dispatched by the SDK.

##### **API**

```
chat.addSignalingListener(options);
```

##### **Parameters**

The `options` parameter is of the `Object` type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| eventName | String | Event name. All event names are stored in the `TencentCloudChat.TSignaling` variable. If you need to view them, you can use `console.log(TencentCloudChat.TSignaling)` to display all the events. |
| handler | Function | The method for handling events; when an event is triggered, this handler will be called for processing. |
| context | any | The expected context in which the handler executes. |

##### **Return value**

`Promise`

##### **Examples**

```
let onNewInvitationReceived = function(event) {};chat.addSignalingListener(TencentCloudChat.TSignaling.NEW_INVITATION_RECEIVED, onNewInvitationReceived);
```

## Remove listening for signaling events.

##### **API**

```
chat.removeSignalingListener(options);
```

##### **Parameters**

The `options` parameter is of the `Object`type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| eventName | String | Event name. All event names are stored in the `TencentCloudChat.TSignaling` variable. If you need to view them, you can use `console.log(TencentCloudChat.TSignaling)` to display all the events. |
| handler | Function | The method for handling events; when an event is triggered, this handler will be called for processing. |
| context | any | The expected context in which the handler executes. |

##### **Return value**

`Promise`

##### **Examples**

```
let onNewInvitationReceived = function(event) {};chat.removeSignalingListener(TencentCloudChat.TSignaling.NEW_INVITATION_RECEIVED, onNewInvitationReceived);
```

## Invite someone

##### **API**

```
chat.invite(options);
```

##### **Parameters**

The `options` parameter is of the `Object`type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| userID | String | user ID |
| data | String | custom data |
| timeout | Number | Timeout period, in seconds. If set to 0, the SDK will not perform timeout detection and will not trigger the `onInvitationTimeout` callback. |
| onlineUserOnly | Boolean | A flag indicating whether the message is only sent to online users; the default value is `false`. If set to `true`, the message will neither be roaming nor counted as unread, nor will it be pushed offline to the recipient. Additionally, the invite operation will not generate a historical message (subsequent `cancel`, `accept`, `reject`, timeout operations for that invite will also not generate historical messages). |
| offlinePushInfo | Object | Offline push configuration. |

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

The`androidInfo`is as described below:

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
| image | String | Identifies the APNs notification bar notification image address. When the client obtains this field, it can display the image on the pop-up window by downloading the image resource.The protocol used must be HTTPS, an example value: https://example.com/image.pngSupports JPEG, GIF, PNG, with a size not exceeding 10 MB.The mutable-content attribute needs to be enabled in the IM console to support iOS 10 Service Extension features.The resource's key value is "image". |

##### **Return value**

`Promise`

##### **Examples**

```
// invite someonelet promise = chat.invite({  userID: 'user1',  data: ''});promise.then(function(imResponse) { console.warn('invite success:', imResponse)}).catch(function(imError) {  console.warn('invite error:', imError);});
```

```
// Invite someone, with the setting not to update the conversation's unreadCount and lastMessage.let promise = chat.invite({  userID: 'user1',  data: JSON.stringify({ excludeFromHistoryMessage: true }),});promise.then(function(imResponse) { console.warn('invite success:', imResponse)}).catch(function(imError) {  console.warn('invite error:', imError);});
```

```
// Invite someone, and set a 30-second timeout. If there is no operation within 30 seconds// the inviter will receive the TencentCloudChat.TSignaling.INVITATION_TIMEOUT event.let promise = chat.invite({  userID: 'user1',  data: '',  timeout: 30});promise.then(function(imResponse) { console.warn('invite success:', imResponse)}).catch(function(imError) {  console.warn('invite error:', imError);});
```

```
// Invite someone, set a 30-second timeout, and the related signaling will not be stored in roaming// nor will it be pushed offline.let promise = chat.invite({  userID: 'user1',  data: '',  timeout: 30,  onlineUserOnly: true});promise.then(function(imResponse) {  console.warn('invite success:', imResponse)}).catch(function(imError) {  console.warn('invite error:', imError);});
```

## Invite certain people within a group.

##### **API**

```
chat.inviteInGroup(options);
```

##### **Parameters**

The `options` parameter is of the `Object`type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | a group ID |
| inviteeList | Array.<String> | List of invitees |
| data | String | custom data |
| timeout | Number | Timeout period, in seconds. If set to 0, the SDK will not perform timeout detection and will not trigger the `onInvitationTimeout` callback. |
| onlineUserOnly | Boolean | A flag indicating whether the message is only sent to online users; the default value is `false`. If set to `true`, the message will neither be roaming nor counted as unread, nor will it be pushed offline to the recipient. Additionally, the invite operation will not generate a historical message (subsequent `cancel`, `accept`, `reject`, timeout operations for that invite will also not generate historical messages). |
| offlinePushInfo | Object | Offline push configuration. |

##### **Return value**

`Promise`

##### **Examples**

```
// Invite certain people within a group.let promise = chat.inviteInGroup({  groupID: 'AV1',  inviteeList: ['user1', 'user2'],  data: '',});promise.then(function(imResponse) { console.warn('inviteInGroup success:', imResponse)}).catch(function(imError) {  console.warn('inviteInGroup error:', imError);});
```

## The inviter cancels the invitation.

##### **API**

```
chat.cancel(options);
```

##### **Parameters**

The `options` parameter is of the `Object`type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| inviteID | String | ID of the invitation |
| data | String | custom data |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.cancel({  inviteID: '38897dbf-ecd4-4b59-a132-bc31529a2b18',  data: '',})promise.then(function(imResponse) { console.log('cancel OK', imResponse);}).catch(function(error) {  console.warn('cancel failed:', error);});
```

## The invitee accepts the invitation.

##### **API**

```
chat.accept(options);
```

##### **Parameters**

The `options` parameter is of the `Object`type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| inviteID | String | ID of the invitation |
| data | String | custom data |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.accept({  inviteID: '38897dbf-ecd4-4b59-a132-bc31529a2b18',  data: '',})promise.then(function(imResponse) { console.log('accept OK', imResponse);}).catch(function(error) {  console.warn('accept failed:', error); });
```

## The invitee rejects the invitation.

##### **API**

```
chat.reject(options);
```

##### **Parameters**

The `options` parameter is of the `Object`type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| inviteID | String | ID of the invitation |
| data | String | custom data |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.reject({  inviteID: '38897dbf-ecd4-4b59-a132-bc31529a2b18',  data: '',})promise.then(function(imResponse) { console.log('reject OK', imResponse);}).catch(function(error) {  console.warn('reject failed:', error);});
```

## Get signaling information.

##### **API**

```
chat.getSignalingInfo(message);
```

##### **Parameters**

| Name | Type | Description |
| --- | --- | --- |
| message | Message | a message instance |

##### **Return value**

`Message | Null`

##### **Examples**

```
// When signaling is null, it indicates that the message is a regular message, not a signaling message.let signaling = chat.getSignalingInfo(message);console.log('signaling info', signaling);
```

## Modify the invitation signaling.

> **Note:**Support for modifying `data` of the invitation signaling. When the invitation signaling's `onlineUserOnly = true`, modifications are not supported.

##### **API**

```
chat.modifyInvitation(options);
```

##### **Parameters**

The `options` parameter is of the `Object`type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| inviteID | String | ID of the invitation |
| data | String | custom data |

##### **Return value**

`Promise`

##### **Examples**

```
let promise = chat.modifyInvitation({  inviteID:'38897dbf-ecd4-4b59-a132-bc31529a2b18',  data: 'xxxx'});promise.then(function(imResponse) { console.log('modifyInvitation OK', imResponse);}).catch(function(error) {  console.warn('modifyInvitation failed:', error);});
```


---
*Source: [https://trtc.io/document/50076](https://trtc.io/document/50076)*
