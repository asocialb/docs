# Overview

## Conversation Overview

In the Chat SDK, there are three types of `Conversation`:

- One-to-one (C2C): A one-to-one conversation between only two users. Its composition method is `C2C${userID}`.
- GROUP: A group conversation among group members. Its composition method is `GROUP${groupID}`.
- `@TIM#SYSTEM` (System Notification Session)

You can use the conversation class APIs to display/update the conversation list, update the unread count, pin a conversation to the top, and mute message notifications.

## UI Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dde69c9bc74511ef82565254005ef0f7.png)

## Conversation Storage Policy

By default, the client can pull 100 recent contact conversations from the cloud, and after upgrading to the [Pro edition ãPro Plus edition or Enterprise edition](https://trtc.io/buy/chat), it can be configured to pull up to 500 recent contact conversations. The conversation duration is consistent with the saving time of the last message in the conversation. Messages are saved for 7 days by default, which means the conversation is also saved for 7 days by default. Please refer to the [Pricing](https://trtc.io/pricing/chat).

## Conversation Class

| Attribute | Type | Description |
| --- | --- | --- |
| conversationID | String | Its composition method is:`C2C${userID}` - A one-to-one conversation between only two users`GROUP${groupID}` - A group conversation among group members`@TIM#SYSTEM` - System Notification Session |
| type | String | `TencentCloudChat.TYPES.CONV_C2C` -  A one-to-one conversation between only two users`TencentCloudChat.TYPES.CONV_GROUP` - A group conversation among group members`TencentCloudChat.TYPES.CONV_SYSTEM` - System Notification Session |
| unreadCount | Number | Unread count. Group conversations of type `TencentCloudChat.TYPES.GRP_MEETING` / `TencentCloudChat.TYPES.GRP_AVCHATROOM` do not record unread counts, and the value of this field is 0. |
| lastMessage | Object | The latest message in the conversation. Its attributes are described as follows.`nick` - String - The nickname of the message sender`nameCard` - String - The group name card of the message sender`lastTime` - Number - The timestamp of the message, in seconds`lastSequence` - Number - The sequence of the message`fromAccount` - String - The userID of the message sender`isRevoked` - Boolean - Whether the message has been recalled, with `true` indicating it has been recalled, and the default value is `false``revoker` - String \| null  - The userID of the message recall initiator`isPeerRead` - Boolean - Whether the message in a one-to-one conversation has been read by the other party; after the other party calls `setMessageRead` to report that it has been read, `isPeerRead` becomes `true`. The default is `false``messageForShow` - String - The content of the message, used for display. Possible values: text message content, "[Image]", "[Voice]", "[Location]", "[Emoji]", "[File]", "[Custom Message]". If this field does not meet your needs, you can use the payload to customize rendering.`type` - String`TencentCloudChat.TYPES.MSG_TEXT` \| Text message`TencentCloudChat.TYPES.MSG_IMAGE` \| Image message`TencentCloudChat.TYPES.MSG_AUDIO` \| Audio message`TencentCloudChat.TYPES.MSG_VIDEO` \| Video message`TencentCloudChat.TYPES.MSG_FILE` \| File message`TencentCloudChat.TYPES.MSG_LOCATION` \| Geolocation message`TencentCloudChat.TYPES.MSG_CUSTOM` \| Custom message`TencentCloudChat.TYPES.MSG_GRP_TIP` \| Group tips message`TencentCloudChat.TYPES.MSG_GRP_SYS_NOTICE` \| Group system notification message.`payload` - Object - The content of the message |
| groupProfile | Group | Group profile of the group conversation. |
| userProfile | Profile | User profile of the one-to-one conversation. |
| groupAtInfoList | Array.<GroupAtInfo> | @mentioned info list of the group conversation. The developer can display effects such as [Someone @ me] or [@all] in the conversation list based on this information. |
| remark | String | Friend remark. It has a value only when there is a C2C conversation, the other party is my friend, and I have set a remark for this friend. |
| isPinned | Boolean | Whether the conversation is pinned. |
| messageRemindType | String | Message reminder types, specifically as follows:`TencentCloudChat.TYPES.MSG_REMIND_ACPT_AND_NOTE` - Messages will be received when the user is online, and offline push notifications will be received when the user is offline.`TencentCloudChat.TYPES.MSG_REMIND_ACPT_NOT_NOTE` - The SDK receives a message and notifies you (by reporting the message receiving event), and you display no notification. This option is usually used to implement message notification muting.`TencentCloudChat.TYPES.MSG_REMIND_DISCARD` - The SDK rejects a message.`TencentCloudChat.TYPES.NOT_RECEIVE_OFFLINE_PUSH_EXCEPT_AT` - Messages will be received when the user is online, and only group @ mentioned messages will be received when the user is offline. |
| markList | Array | Conversation tag list, specifically as follows:`TencentCloudChat.TYPES.CONV_MARK_TYPE_STAR` - Star a conversation`TencentCloudChat.TYPES.CONV_MARK_TYPE_UNREAD` - Mark a conversation as unread`TencentCloudChat.TYPES.CONV_MARK_TYPE_FOLD` - Collapse a conversation`TencentCloudChat.TYPES.CONV_MARK_TYPE_HIDE` - Hide a conversation |
| customData | String | Custom data for the conversation. |
| conversationGroupList | Array | List of conversation groups that the conversation belongs to. |
| draftText | String | Conversation draft. Stored locally only, not in the cloud. |

### GroupAtInfo

| Name | Type | Description |
| --- | --- | --- |
| groupID | String | Group ID. |
| messageSequence | Number | Sequence of messages with @ information. |
| atTypeArray | Array.<Number> | `at` type array, `at` enumeration values in group conversations are as follows:`TencentCloudChat.TYPES.CONV_AT_ME`- Someone mentioned me.`TencentCloudChat.TYPES.CONV_AT_ALL`- Mentioned everyone in the group.`TencentCloudChat.TYPES.CONV_AT_ALL_AT_ME`- Mentioned everyone in the group and also mentioned me individually. |


---
*Source: [https://trtc.io/document/48844](https://trtc.io/document/48844)*
