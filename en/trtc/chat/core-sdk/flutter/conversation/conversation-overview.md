# Conversation Overview

## Conversation

When a user creates a one-to-one or group chat, a conversation will be created.

In the Tencent Cloud Chat SDK, the conversation class is `TencentImSDKPlugin.v2TIMManager.getConversationManager()`. You can use the conversation management class APIs to display/update the conversation list, update the unread count, pin a conversation to the top, make a conversation draft, and mute message notifications.

## Conversation Class

The conversation class is `V2TIMConversation` ([Details](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/models_v2_tim_conversation/V2TimConversation-class.html)), which defines the following content:

| Attribute | Definition | Description |
| --- | --- | --- |
| type | Conversation type | See the definition of `V2TIMConversationType`, which can be `C2C` or `Group`. |
| conversationID | Unique conversation ID | It is in the format of `c2c_userID` for a one-to-one chat or `group_groupID` for a group chat. |
| userID | User ID of the message receiver | `userID` stores the user ID of the message receiver if the conversation type is one-to-one chat; otherwise, it is `nil/null`. |
| groupID | Group ID | `groupID` stores the group ID if the conversation type is group chat; otherwise, it is `nil/null`. |
| groupType | Group type | `groupType` is the type of the group if the conversation type is group chat; otherwise, it is `nil/null`. |
| showName | Displayed conversation name | The name of a group conversation is displayed in the following order of priority: group name > group ID; The name of a one-to-one conversation is displayed in the following order of priority: friend remarks of the message receiver > nickname of the message receiver > `userID` of the message receiver. |
| faceUrl | Displayed conversation profile photo | It is the group profile photo for a group chat or the profile photo of the message receiver for a one-to-one chat. |
| unreadCount | Unread message count of the conversation | For detailed directions, see [unreadCount property](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/models_v2_tim_conversation/V2TimConversation/unreadCount.html). It is invalid and defaults to `0` for an audio-video group (AVChatRoom). |
| recvOpt | Message receiving option | See the definition of `V2TIMReceiveMessageOpt`. For detailed directions, see [V2TimReceiveMessageOptInfo class](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/enum_receive_message_opt_enum/ReceiveMsgOptEnum.html). |
| lastMessage | Last message in the conversation | For detailed directions, see [getConversationList metho](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_conversation_manager/V2TIMConversationManager/getConversationList.html). |
| groupAtInfolist | List of @ information in the group conversation | Generally, it is used to display the notifications of "someone@me" and "@all". |
| draftText | Draft information | The draft information can be set by calling the `setConversationDraft` API. For detailed directions, see [setConversationDraft method](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/models_v2_tim_conversation/V2TimConversation/draftText.html). |
| draftTimestamp | Draft editing time | It is automatically generated when a draft is set. |
| isPinned | Whether to pin the conversation to the top | For detailed directions, see [pinConversation method](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_conversation_manager/V2TIMConversationManager/pinConversation.html). |
| orderKey | Field for sorting conversations | For detailed directions, see [getConversationList method](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_conversation_manager/V2TIMConversationManager/getConversationList.html). |
| customData | Conversation's custom data | For detailed directions, see [setConversationCustomData method](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_conversation_manager/V2TIMConversationManager/setConversationCustomData.html) |

## Conversation Storage Policy

There is no limit on the number of locally stored conversations.

Up to 100 conversations can be stored in the cloud. To increase this limit, upgrade to the Pro edition ãPro Plus edition or Enterprise edition. Then you can set the limit to 500 in the console.

Up to 100 conversations can be stored in the cloud. To increase this limit, upgrade to the Pro edition ãPro Plus edition or Enterprise edition. Then you can set the limit to 500 in the console:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1c757601ceca11ee86df525400c26da5.png)

If the information of a conversation has not been updated for a long time, the conversation can be stored in the cloud for up to seven days. To extend the conversation storage period, [contact us](https://trtc.io/zh/contact) for application.

Locally stored conversations may not always be consistent with those stored in the cloud. If the user does not call the `deleteConversation` API to delete the local conversations, the conversations will always exist. However, up to 100 conversations can be stored in the cloud, and if the information of a conversation has not been updated for a long time, the conversation can be stored in the cloud for up to seven days. Therefore, local conversations displayed on different terminals may differ.


---
*Source: [https://trtc.io/document/48327](https://trtc.io/document/48327)*
