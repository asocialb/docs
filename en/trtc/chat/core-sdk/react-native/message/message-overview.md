# Message Overview

## Message Class

In the Chat SDK, `Message` indicates the message object that is used to describe the attributes of a message, such as type, content, and conversation ID.

| Attribute | Type | Default Value | Description |
| --- | --- | --- | --- |
| ID | String | - | Message ID. The rule for concatenating the message ID is `${senderTinyID}-${clientTime}-${random}`, which is the same as that for concatenating the message ID of native Chat. |
| type | String | - | Message type. Valid values:`TencentCloudChat.TYPES.MSG_TEXT` - text message`TencentCloudChat.TYPES.MSG_IMAGE` - image message`TencentCloudChat.TYPES.MSG_AUDIO` - audio message`TencentCloudChat.TYPES.MSG_VIDEO` - video message`TencentCloudChat.TYPES.MSG_FILE` - file message`TencentCloudChat.TYPES.MSG_CUSTOM` - custom message`TencentCloudChat.TYPES.MSG_MERGER` - merged message`TencentCloudChat.TYPES.MSG_LOCATION` - location message`TencentCloudChat.TYPES.MSG_GRP_TIP` - group tip message`TencentCloudChat.TYPES.MSG_GRP_SYS_NOTICE` - group system notification |
| payload | Object | - | Message content. Valid values:`TextPayload``ImagePayload``AudioPayload``VideoPayload``FilePayload``CustomPayload``MergerPayload``LocationPayload``FacePayload``GroupTipPayload``GroupSystemNoticePayload` |
| conversationID | String | - | Conversation ID of the message. |
| conversationType | String | - | Conversation type of the message. Valid values:`TencentCloudChat.TYPES.CONV_C2C` --- C2C (one-to-one) conversation`TencentCloudChat.TYPES.CONV_GROUP` --- group conversation`TencentCloudChat.TYPES.CONV_SYSTEM` --- system conversation |
| to | String | - | `userID` of the receiver. |
| from | String | - | `userID` of the sender. It is set to the ID of the currently logged-in user by default when a message is sent. |
| flow | String | - | Message flow.`in` --- the received message`out` --- the sent message |
| time | Number | - | Message timestamp in seconds. |
| status | String | - | Message status.`unSend` --- not sent`success` --- sent successfully`fail` --- failed to send |
| isRevoked | Boolean | false | Whether the message is a recalled message. `true` indicates yes. |
| priority | String | `TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL` | Message priority. If messages in a group exceed the frequency limit, the backend will deliver high-priority messages first. Supported enumerated values:`TencentCloudChat.TYPES.MSG_PRIORITY_HIGH``TencentCloudChat.TYPES.MSG_PRIORITY_NORMAL (default)``TencentCloudChat.TYPES.MSG_PRIORITY_LOW``TencentCloudChat.TYPES.MSG_PRIORITY_LOWEST` |
| nick | String | - | Nickname of the message sender. This attribute needs to be set by calling the `updateMyProfile` API in advance. |
| avatar | String | - | Profile photo URL of the message sender. This attribute needs to be set by calling the `updateMyProfile` API in advance. |
| nameCard | String | - | Group name card of the sender that sends a non-audio-video group message. This attribute also is called the nickname of the message sender in the group and needs to be set by calling the `setGroupMemberNameCard` API in advance. |
| atUserList | Array | - | This field stores the `userID` values of the group members who are mentioned in the group message. |
| cloudCustomData | String | '' | Custom message data, which is saved in the cloud, will be sent to the receiver, and can still be pulled after the application is uninstalled and reinstalled. |
| isDeleted | Boolean | false | Whether the message is a deleted message. `true` indicates yes. |
| isModified | Boolean | false | Whether the message is a modified message. `true` indicates yes. |
| needReadReceipt | Boolean | false | Whether a read receipt is needed. `true` indicates yes. To use it, you need to purchase the Premium edition package. |
| readReceiptInfo | Object | - | Message read receipt information`readCount` - count of the messages that are read, which can be queried by calling `getMessageReadReceiptList` API; to query the group members who read the message, call the `getGroupMessageReadMemberList`.`unreadCount` - count of the messages that are not read, which can be queried by calling the `getMessageReadReceiptList` API.`isPeerRead` - Whether the peer of C2C message has sent a read receipt, this property will be updated when the message sender receives a read receipt notification or pulls roaming after the message receiver successfully calls `sendMessageReadReceipt`.`timestamp` - Time for the peer of C2C message to send a read receipt, in seconds. This attribute will be updated when the message sender receives a read receipt notification or pulls roaming after the message receiver successfully calls `sendMessageReadReceipt`. |
| isBroadcastMessage | Boolean | false | Whether the message is a broadcast message. `true` indicates yes. |
| isSupportExtension | Boolean | false | whether the message supports extensions. `true` indicates yes. To use it, you need to purchase the Premium edition package. |
| revokerInfo | Object | - | Information of the message recaller. |
| revokeReason | String | - | Reason for the message recall. |
| hasRiskContent | Boolean | - | Whether image, voice, and video messages are marked as having security risks, default is false. If the content of the voice or video message you send is non-compliant, the SDK will trigger a `MESSAGE_MODIFIED` event after asynchronous cloud review. |

### TextPayload

| Name | Type | Description |
| --- | --- | --- |
| text | String | Text message content |

### ImagePayload

| Name | Type | Description |
| --- | --- | --- |
| uuid | String | Unique identifier of an image |
| imageFormat | Format | Image format type. JPG/JPEG = 1, GIF = 2, PNG = 3, BMP = 4, other = 255 |
| imageInfoArray | Array.<Object> | Image information. Each element contains attributes described as follows:width - Numberheight - Numberurl - String - Image address, which can be used for renderingsize - Number - Image size, in bytestype - Number - 0, Original image; 1, 198p compressed image; 2, 720p compressed image |

### AudioPayload

| Name | Type | Description |
| --- | --- | --- |
| uuid | String | Unique identifier |
| url | String | Audio address, which can be used for playback |
| size | Number | File size, in bytes |
| second | Number | Audio duration, in seconds |

### VideoPayload

| Name | Type | Description |
| --- | --- | --- |
| videoFormat | String | Video file format |
| videoSecond | Number | Video file duration, in seconds and of integer type |
| videoSize | Number | Video file size, in bytes |
| videoUrl | String | Video file address, which can be used for playback |
| videoUUID | String | Unique identifier of a video |
| snapshotWidth | Number | snapshot image width |
| snapshotHeight | Number | snapshot image height |
| snapshotUrl | String | snapshot image address, which can be used rendering(the [tim-upload-plugin](https://www.npmjs.com/package/tim-upload-plugin) is required) |

### FilePayload

| Name | Type | Description |
| --- | --- | --- |
| uuid | String | Unique identifier |
| fileName | String | File name |
| fileUrl | String | File address |
| fileSize | Number | File size, in bytes |

### CustomPayload

| Name | Type | Description |
| --- | --- | --- |
| data | String | "data" field of a custom message |
| description | String | "description" field of a custom message |
| extension | String | "extension" field of a custom message |

### MergerPayload

| Name | Type | Description |
| --- | --- | --- |
| downloadKey | String | Key for downloading a combined message. If a combined message is large in size, the SDK will store it on the cloud, using this key as the unique identifier of the message. |
| messageList | Array.<SimplifiedMessage> | List of messages combined. |
| title | String | Title of the combined message, for example, "Chat History of the Talent Center in the Greater Bay Area". |
| abstractList | String | Digest list. You can set digest information in different formats for different message types, for example: for a text message, the digest can be in the "sender:text" format. For an image message, the digest can be in the "sender:[image]" format. For a file message, the digest can be in the "sender:[file]" format. |
| compatibleText | String | Compatible text. SDKs of early versions do not support combined messages, and they will send a text message with the content `compatibleText` by default. |
| layersOverLimit | Boolean | Whether the number of combination nesting levels exceeds the limit. true: the limit is exceeded, and the message is truncated. Default value: false. |

### GeoPayload

| Name | Type | Description |
| --- | --- | --- |
| description | String | Related description |
| latitude | Number | Latitude |
| longitude | Number | longitude |

### FacePayload

| Name | Type | Description |
| --- | --- | --- |
| index | Number | Emoji index, which is customized by the user |
| data | String | Extra data |

### GroupTipPayload

| Name | Type | Description |
| --- | --- | --- |
| groupJoinType | Number | Group joining type. Supported values are as follows:0 - Default value, indicating that the operation is not a group joining operation.1 - A user requests to join the group.2 - A user is invited to the group. |
| operatorID | String | ID of the user who performs the operation. |
| operatorInfo | Object | User information for executing this operation (supported from v3.4.2 onwards). |
| operationType | Number | Operation type. Supported values are as follows:1 - A member joins the group.2 - A member leaves the group.3 - A group member is removed from the group.4 - A group member is granted the group admin role.5 - The group admin role of a group member is revoked.6 - The group profile is modified.7 - The profile of a group member is modified. For example, a group member is muted.10 - An audio-video group member is banned.11 - An audio-video group member is unbanned. |
| userIDList | Array.<String> | List of relevant userIDs. |
| newGroupProfile | Object | If a group profile is modified, this field stores the new group profile. |
| memberList | Array.<Object> | If a group member is muted, this field stores related information. Each element contains attributes described as follows:`userID` - String - Group member userID`muteTime` - Number - Muting duration, in seconds`nick` - String - Nickname of the group member`avatar` - String - Avatar of group members`duration` - Number - Ban duration, unit: seconds`reason` - String - Reason for ban |

### GroupSystemNoticePayload

| Name | Type | Description |
| --- | --- | --- |
| operatorID | String | ID of the user who performs the operation. |
| operationType | Number | Operation type. Supported values are as follows:1 - A user requests to join the group.2 - The request to join the group is approved.3 - The request to join the group is rejected.4 - A user is removed from the group.5 - The group is deleted.6 - The group is created.7 - A user is invited to the group.8 - A user leaves the group.9 - The admin is modified.10 - The admin is canceled.11 - The group is repossessed.12 - A user receives a group joining invitation, and needs to accept or reject the invitation.13 - A user invites others to join the group, and the invitation is accepted.14 - A user invites others to join the group, and the invitation is rejected.15 - Read report synchronized across multiple terminals.20 - Group message remind type synchronized across multiple terminals.21 - ban an audio-video group member.22 - unban an audio-video group member.23 - a group member invites others to join the group.255 - A custom notification is triggered. |
| groupProfile | Object | Profile of the relevant group. |
| userDefinedField | String | User-defined field. |
| handleMessage | Object | Remarks on the processing. For example, if user1 enters remarks on an application to join group1 that requires approval, the admin of group1 will see this field in the group system message. |
| messageRemindType | String | `TencentCloudChat.TYPES.MSG_REMIND_ACPT_AND_NOTE` - the SDK receives a message and throws a MESSAGE_RECEIVED event to notify the access side, which then sends a notification.`TencentCloudChat.TYPES.MSG_REMIND_ACPT_NOT_NOTE` - the SDK receives a message and throws a MESSAGE_RECEIVED event to notify the access side, which then does not send a notification.`TencentCloudChat.TYPES.MSG_REMIND_DISCARD` - the SDK rejects a message.`TencentCloudChat.TYPES.NOT_RECEIVE_OFFLINE_PUSH_EXCEPT_AT` Receive messages online, and only receive push notifications for group @ messages when offline |


---
*Source: [https://trtc.io/document/48868](https://trtc.io/document/48868)*
