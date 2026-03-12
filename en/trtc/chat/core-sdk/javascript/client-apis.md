# Client APIs

### TencentCloudChat

`TencentCloudChat` is the namespace of the Chat JavaScript SDK and provides the static method `create()` for creating SDK instances, the event constant `EVENT`, and the type constant `TYPES`, and the signaling constant `TSignaling`.

### **Initialization**

| API | Description |
| --- | --- |
| [create](https://trtc.io/document/47967?platform=javascript&product=chat&menulabel=sdk#calling-the-initialization-api) | Creates an SDK instance. |

### SDK Instance

| Term | Description |
| --- | --- |
| [Message](https://trtc.io/document/47990?platform=javascript&product=chat&menulabel=sdk) | `Message` indicates the content to be sent and carries multiple attributes which specify whether you are the sender, the sender account, the message generation time, and so on. |
| [Conversation](https://trtc.io/document/48328?platform=javascript&product=chat&menulabel=sdk) | Two types of conversation are available: Client to Client (C2C): A one-to-one chat, involving only two participants.GROUP: A group chat, involving more than two participants. |
| `Profile` | `Profile` describes the basic information of a user, including the nickname, gender, personal signature, and profile photo URL. |
| `Friend` | `Friend` describes the basic information of a friend, including the remarks and friend list. |
| `FriendApplication` | `FriendApplication` describes the basic information of a friend request, including the friend source and remarks. |
| `FriendGroup` | `FriendGroup` describes the basic information of a friend group, including the friend group name and members. |
| `Group` | `Group` indicates a communication system for group chatting, including Work Group, Public Group, Meeting Group, Audio-Video Group, and Community Group. |
| `GroupMember` | `GroupMember` indicates the basic information of each group member, such as the ID, nickname, role, and the time of joining the group. |
| `Group tip` | A group tip is generated when an event such as adding or deleting group member occurs. The access side can configure whether to display group tips to group members. |
| `Group system message` | For example, when a user requests to join a group, the group admin receives a system message. After the admin accepts or rejects the request, the Chat SDK returns the result to the access side, which then displays the result to the user. |
| `Message display on screen` | The sent messages, including text segments and images, are displayed on the computer or phone screen. |

### Event

| API | Description |
| --- | --- |
| [on](https://trtc.io/document/47967?platform=javascript&product=chat&menulabel=sdk#d39fb50f-f0f2-4b67-9b15-acd7e8608105) | Enables event listening. |
| [off](https://trtc.io/document/47967?platform=javascript&product=chat&menulabel=sdk#c4cb09c5-142a-4d8c-8c03-ea7f446aa844) | Disables event listening. |

### Plugin registration

| API | Description |
| --- | --- |
| [registerPlugin](https://trtc.io/document/34309?platform=javascript&product=chat&menulabel=sdk#25e1c195-9e04-4c43-9525-79ad5fecf070) | Registers a plugin. |

### Setting log level

| API | Description |
| --- | --- |
| [setLogLevel](https://trtc.io/document/34309?platform=javascript&product=chat&menulabel=sdk#08d86171-ca90-45dd-97bb-93b0501b4dd3) | Sets the log level. Logs below this level will not be printed. |

### SDK instance termination

| API | Description |
| --- | --- |
| [destroy](https://trtc.io/document/47967?platform=javascript&product=chat&menulabel=sdk#.E5.8F.8D.E5.88.9D.E5.A7.8B.E5.8C.96) | Terminates an SDK instance. The SDK will log out, disconnect the WebSocket persistent connection, and then release resources. |

### Login

| API | Description |
| --- | --- |
| [login](https://trtc.io/document/47970?platform=javascript&product=chat&menulabel=sdk#964d8f2e-a986-41fc-aba1-a8bfe6f6c8eb) | Logs in to the Chat SDK using userID and userSig. |
| [logout](https://trtc.io/document/47970?platform=javascript&product=chat&menulabel=sdk#c58e1694-051c-404f-acef-1bb45ebc277c) | Logs out to the Chat SDK. |
| [isReady](https://trtc.io/document/47970?platform=javascript&product=chat&menulabel=sdk#188c35da-d695-4d33-a192-ae808b597c66) | Indicates the SDK enter the ready state or not. |
| [getLoginUser](https://trtc.io/document/47970?platform=javascript&product=chat&menulabel=sdk#d11b69cb-28c4-45f5-b16e-ec239e8e5c61) | Get the userID of the logged-in user. If the user is not logged in, it returns an empty string (''). |
| [getServerTime](https://trtc.io/document/47970?platform=javascript&product=chat&menulabel=sdk#19bcbcd8-f380-4380-a148-7c99cf7bfd06) | Get the server time. |

### Message

| API | Description |
| --- | --- |
| [createTextMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-a-text-message) | Creates a text message. |
| [createTextAtMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-an-.40-message) | Creates a text message with the @ notification feature. |
| [createImageMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-an-image-message) | Creates an image message. |
| [createAudioMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-an-audio-message) | Creates an audio message. |
| [createVideoMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-a-video-message) | Creates a video message. |
| [createCustomMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-a-custom-message) | Creates a custom message. |
| [createFaceMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-an-emoji-message) | Creates an emoji message. |
| [createFileMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-a-file-message) | Creates a file message. |
| [createLocationMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-a-geographical-location-message) | Creates a location message. |
| [createMergerMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#creating-a-merged-message) | Creates a combined message. |
| [downloadMergerMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#downloading-a-merged-message) | Downloads a combined message. |
| [createForwardMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#forwarding-messages-one-by-one) | Creates a forward message. |
| [sendMessage](https://trtc.io/document/47993?platform=javascript&product=chat&menulabel=sdk#sending-a-message) | Sends a message. |
| [revokeMessage](https://trtc.io/document/48015?platform=javascript&product=chat&menulabel=sdk#3013baf3-7974-4ac9-af5f-4a85d5b29ea0) | Recalls a message. |
| [deleteMessage](https://trtc.io/document/48010?platform=javascript&product=chat&menulabel=sdk) | Deletes a message. |
| [translateText](https://trtc.io/document/55857?platform=javascript&product=chat&menulabel=sdk#2f1707bc-e7d9-4f1d-b219-6f12ba8aaab8) | Translates a message. |
| [setMessageExtensions](https://trtc.io/document/54166?platform=javascript&product=chat&menulabel=sdk#5243dc69-bf46-49a0-8c21-b7e7f3bbdb0e) | Sets message extensions. |
| [getMessageExtensions](https://trtc.io/document/54166?platform=javascript&product=chat&menulabel=sdk#.E8.8E.B7.E5.8F.96.E6.B6.88.E6.81.AF.E6.89.A9.E5.B1.95) | Gets message extensions. |
| [deleteMessageExtensions](https://trtc.io/document/54166?platform=javascript&product=chat&menulabel=sdk#9c2c4ca3-3f4d-4c33-86ba-f7000c2bb7e7) | Deletes message extensions. |
| [addMessageReaction](https://trtc.io/document/60749?platform=javascript&product=chat&menulabel=sdk#07af1608-075c-4f2b-84e8-48987cd2ee4e) | Add message reactions. This interface allows for scenarios such as "emoji reactions" to be implemented. |
| [removeMessageReaction](https://trtc.io/document/60749?platform=javascript&product=chat&menulabel=sdk#82baa97c-bf9e-4732-a9bd-29c05f18a930) | Remove message reactions. |
| [getMessageReactions](https://trtc.io/document/60749?platform=javascript&product=chat&menulabel=sdk#2ef2bd48-285f-4f4c-9e3e-662e3cf74330) | Retrieve information of message reactions. |
| [getAllUserListOfMessageReaction](https://trtc.io/document/60749?platform=javascript&product=chat&menulabel=sdk#c4cf8036-a7ab-4e1f-9c51-01cf44b2ef41) | Paginate and retrieve the user list for a specific message reaction. |

### Conversation

| API | Description |
| --- | --- |
| [modifyMessage](https://trtc.io/document/48005?platform=javascript&product=chat&menulabel=sdk#modifying-a-message) | Modifies a message. |
| [getMessageList](https://trtc.io/document/47999?platform=javascript&product=chat&menulabel=sdk#1a324216-7ec8-4df4-9060-bbe74be6477d) | Gets the message list. |
| [getMessageListHopping](https://trtc.io/document/47999?platform=javascript&product=chat&menulabel=sdk#a9fd17b1-21b0-4898-9d8f-1fa3c978e053) | Pulls the conversation message list by specified sequence or time range. |
| [sendMessageReadReceipt](https://trtc.io/document/48021?platform=javascript&product=chat&menulabel=sdk#sending-a-message-read-receipt-(by-the-receiver)) | Sends message read receipts. |
| [getMessageReadReceiptList](https://trtc.io/document/48021?platform=javascript&product=chat&menulabel=sdk#pulling-message-read-receipt-information-(by-the-sender)) | Pulls the list of message read receipts. |
| [getGroupMessageReadMemberList](https://trtc.io/document/48021?platform=javascript&product=chat&menulabel=sdk#pulling-the-list-of-members-who-have-or-have-not-read-a-group-message-(by-the-sender)) | Pulls the list of members who have (or have not) read a group message. |
| [findMessage](https://trtc.io/document/48024?platform=javascript&product=chat&menulabel=sdk#b77ad0fd-dbfa-4400-8075-e9f768100b1f) | Queries local messages in a specified conversation by `messageID`. |
| [setMessageRead](https://trtc.io/document/48319?platform=javascript&product=chat&menulabel=sdk#clearing-the-conversation-unread-count) | Marks a message as read. |
| [getConversationList](https://trtc.io/document/48325?platform=javascript&product=chat&menulabel=sdk#getting-the-conversation-list) | Gets the conversation list. |
| [getConversationProfile](https://trtc.io/document/48322?platform=javascript&product=chat&menulabel=sdk#.E8.8E.B7.E5.8F.96.E4.BC.9A.E8.AF.9D.E8.AF.A6.E7.BB.86.E8.B5.84.E6.96.99) | Gets the conversation information. |
| [deleteConversation](https://trtc.io/document/48313?platform=javascript&product=chat&menulabel=sdk#deleting-a-conversation) | Deletes a conversation. |
| [setConversationDraft](https://trtc.io/document/56184?platform=javascript&product=chat&menulabel=sdk#setting-a-conversation-draft) | Set conversation draft. |
| [clearHistoryMessage](https://trtc.io/document/53498?platform=javascript&product=chat&menulabel=sdk) | Clears the chat history with a user from local storage and the cloud (without deleting the conversation). |
| [pinConversation](https://trtc.io/document/48316?platform=javascript&product=chat&menulabel=sdk#pinning.2Funpinning-a-conversation-to.2Ffrom-the-top) | Pins/Unpins a conversation to/from top. |
| [setAllMessageRead](https://trtc.io/document/48319?platform=javascript&product=chat&menulabel=sdk#clearing-the-unread-count-of-all-conversations) | Marks the unread messages of all conversations as read. |
| [setMessageRemindType](https://trtc.io/document/48031?platform=javascript&product=chat&menulabel=sdk) | Sets the conversation message notification type. You can use this API to mute notifications or reject messages. |
| [getTotalUnreadMessageCount](https://trtc.io/document/48319?platform=javascript&product=chat&menulabel=sdk#0e51fa40-580e-4977-b80c-00f7d46de1fd) | Gets the total unread message count of conversations. |

### Conversation group

| API | Description |
| --- | --- |
| [setConversationCustomData](https://trtc.io/document/50291?platform=javascript&product=chat&menulabel=sdk#21c1afd9-bfdf-4fa0-8df7-07a27e94898a) | Sets custom conversation data. |
| [markConversation](https://trtc.io/document/50291?platform=javascript&product=chat&menulabel=sdk#conversation-mark) | Marks a conversation. |
| [getConversationGroupList](https://trtc.io/document/50289?platform=javascript&product=chat&menulabel=sdk#getting-the-list-of-conversation-groups) | Gets the list of conversation groups. |
| [createConversationGroup](https://trtc.io/document/50289?platform=javascript&product=chat&menulabel=sdk#creating-a-conversation-group) | Creates a conversation group. |
| [deleteConversationGroup](https://trtc.io/document/50289?platform=javascript&product=chat&menulabel=sdk#deleting-a-conversation-group) | Deletes a conversation group. |
| [renameConversationGroup](https://trtc.io/document/50289?platform=javascript&product=chat&menulabel=sdk#renaming-a-conversation-group) | Renames a conversation group. |
| [addConversationsToGroup](https://trtc.io/document/50289?platform=javascript&product=chat&menulabel=sdk#adding-a-conversation-to-a-group) | Adds a conversation to a conversation group. |
| [deleteConversationsFromGroup](https://trtc.io/document/50289?platform=javascript&product=chat&menulabel=sdk#deleting-a-conversation-from-a-group) | Deletes conversations from a conversation group. |

### Search

| API | Description |
| --- | --- |
| [searchCloudMessages](https://www.tencentcloud.com/document/product/1047/67677#b57f11f2-d80b-4e40-b9e3-8f9463195624) | Search cloud messages. |
| [searchCloudUsers](https://www.tencentcloud.com/document/product/1047/67679#b57f11f2-d80b-4e40-b9e3-8f9463195624) | Search cloud users. |
| [searchCloudGroups](https://www.tencentcloud.com/document/product/1047/67681#b57f11f2-d80b-4e40-b9e3-8f9463195624) | Search cloud groups. |
| [searchCloudGroupMembers](https://www.tencentcloud.com/document/product/1047/67683#b57f11f2-d80b-4e40-b9e3-8f9463195624) | Search cloud group members. |

### Profile

| API | Description |
| --- | --- |
| [getMyProfile](https://trtc.io/document/48161?platform=javascript&product=chat&menulabel=sdk#querying-a-user&) | Gets personal profile. |
| [getUserProfile](https://trtc.io/document/48161?platform=javascript&product=chat&menulabel=sdk#querying-the-profile-of-another-user) | Gets other userâs profile. |
| [updateMyProfile](https://trtc.io/document/48161?platform=javascript&product=chat&menulabel=sdk#updating-your-personal-profile) | Updates your personal profile. |
| [getBlacklist](https://trtc.io/document/48152?platform=javascript&product=chat&menulabel=sdk#07e8dcd3-0bca-411f-97a0-598760b76ee6) | Gets your blocklist. |
| [addToBlacklist](https://trtc.io/document/48152?platform=javascript&product=chat&menulabel=sdk#blocking-a-user) | Adds a user to the blocklist. |
| [removeFromBlacklist](https://trtc.io/document/48152?platform=javascript&product=chat&menulabel=sdk#unblocking-a-user) | Removes a user from the blocklist. |

### User status

| API | Description |
| --- | --- |
| [setSelfStatus](https://trtc.io/document/49561?platform=javascript&product=chat&menulabel=sdk#.E8.AE.BE.E7.BD.AE.E8.87.AA.E5.B7.B1.E7.9A.84.E8.87.AA.E5.AE.9A.E4.B9.89.E7.8A.B6.E6.80.81) | Sets one's own custom status. |
| [getUserStatus](https://trtc.io/document/49561?platform=javascript&product=chat&menulabel=sdk#.E6.9F.A5.E8.AF.A2.E7.94.A8.E6.88.B7.E7.8A.B6.E6.80.81) | Queries a user's status. |
| [subscribeUserStatus](https://trtc.io/document/49561?platform=javascript&product=chat&menulabel=sdk#5e87c5ae-7e0c-48cf-9805-235332b73ece) | Subscribes to a user's status. |
| [unsubscribeUserStatus](https://trtc.io/document/49561?platform=javascript&product=chat&menulabel=sdk#.E5.8F.96.E6.B6.88.E8.AE.A2.E9.98.85.E7.94.A8.E6.88.B7.E7.8A.B6.E6.80.81) | Unsubscribes from a user's status. |

### Relationship Chain

| API | Description |
| --- | --- |
| [getFriendList](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#getting-contacts) | Gets the contacts in the SDK cache. |
| [addFriend](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#adding-a-friend) | Adds friends. |
| [deleteFriend](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#deleting-a-friend) | Deletes friends. |
| [checkFriend](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#checking-the-friend-relationship) | Verifies friend relationship. |
| [getFriendProfile](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#53cc9f64-629e-4594-9464-d6b7aa36db36) | Gets the friend data and profile data of a specified user. |
| [updateFriend](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#e062500d-113a-441f-a568-e5952ae72d3f) | Updates the contacts data of friends. |
| [getFriendApplicationList](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#cfc251a7-01f1-430b-81d1-c60fe9e0da86) | Gets the friend request list in the SDK cache. |
| [acceptFriendApplication](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#0f3ceee8-d22f-4011-aa6f-389e7e05cab3) | Accepts a friend request. |
| [refuseFriendApplication](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#f3c8eac1-fdcf-48c2-8361-3231986b4496) | Rejects a friend request. |
| [deleteFriendApplication](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#13f2e2ac-b182-4bdd-bf8f-b37cdcbbe337) | Deletes a friend request. |
| [setFriendApplicationRead](https://trtc.io/document/48158?platform=javascript&product=chat&menulabel=sdk#f473a501-8276-4aa7-b330-c0a39ec0f76e) | Set a friend request as reads. |
| [getFriendGroupList](https://trtc.io/document/48155?platform=javascript&product=chat&menulabel=sdk#getting-a-friend-list) | Gets list of friend groups in the SDK cache. |
| [createFriendGroup](https://trtc.io/document/48155?platform=javascript&product=chat&menulabel=sdk#creating-a-friend-list) | Creates a friend group. |
| [deleteFriendGroup](https://trtc.io/document/48155?platform=javascript&product=chat&menulabel=sdk#deleting-a-friend-list) | Deletes a friend group. |
| [addToFriendGroup](https://trtc.io/document/48155?platform=javascript&product=chat&menulabel=sdk#adding-a-friend-to-a-list) | Adds friends to a friend group. |
| [removeFromFriendGroup](https://trtc.io/document/48155?platform=javascript&product=chat&menulabel=sdk#removing-a-friend-from-a-list) | Removes friends from a friend group. |
| [renameFriendGroup](https://trtc.io/document/48155?platform=javascript&product=chat&menulabel=sdk#renaming-a-friend-list) | Modifies the name of a friend group. |

### Group

| API | Description |
| --- | --- |
| [getGroupList](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#getting-the-joined-groups) | Gets the group list. |
| [getGroupProfile](https://trtc.io/document/48184?platform=javascript&product=chat&menulabel=sdk#getting-the-group-profile) | Gets the group profile. |
| [createGroup](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#creating-a-group) | Creates a group. |
| [dismissGroup](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#disbanding-a-group) | Disbands a group. |
| [updateGroupProfile](https://trtc.io/document/48184?platform=javascript&product=chat&menulabel=sdk#modifying-the-group-profile) | Modifies the group profile. |
| [joinGroup](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#joining-a-group) | Requests to join a group. |
| [quitGroup](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#leaving-a-group) | Quits a group. |
| [searchGroupByID](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#61b2415b-5e82-4827-84b9-77923e03740c) | Searches for a group. |
| [getGroupOnlineMemberCount](https://trtc.io/document/48180?platform=javascript&product=chat&menulabel=sdk#570611e5-cf0f-481d-bee9-5359abd7a4e4) | Gets the number of online users in an audio-video group. |
| [changeGroupOwner](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#transferring-a-group) | Transfers the group ownership. |
| [getGroupApplicationList](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#c69d4d7c-3f0b-4486-b31a-190e6176a1c5) | Gets the list of requests to join a group. |
| [handleGroupApplication](https://trtc.io/document/48465?platform=javascript&product=chat&menulabel=sdk#processing-(approving-or-rejecting)-a-group-join-request) | Processes requests to join the group. |
| [initGroupAttributes](https://trtc.io/document/48174?platform=javascript&product=chat&menulabel=sdk#initializing-group-attributes) | Initializes group attributes. |
| [setGroupAttributes](https://trtc.io/document/48174?platform=javascript&product=chat&menulabel=sdk#setting-group-attributes) | Sets group attributes. |
| [deleteGroupAttributes](https://trtc.io/document/48174?platform=javascript&product=chat&menulabel=sdk#deleting-group-attributes) | Deletes group attributes. |
| [getGroupAttributes](https://trtc.io/document/48174?platform=javascript&product=chat&menulabel=sdk#getting-group-attributes) | Gets group attributes. |
| [setGroupCounters](https://trtc.io/document/56042?platform=javascript&product=chat&menulabel=sdk#.E8.AE.BE.E7.BD.AE.E7.BE.A4.E8.AE.A1.E6.95.B0.E5.99.A8) | Sets group counters. |
| [increaseGroupCounter](https://trtc.io/document/56042?platform=javascript&product=chat&menulabel=sdk#.E9.80.92.E5.A2.9E.E7.BE.A4.E8.AE.A1.E6.95.B0.E5.99.A8) | Increases the specified group counters. |
| [decreaseGroupCounter](https://trtc.io/document/56042?platform=javascript&product=chat&menulabel=sdk#.E9.80.92.E5.87.8F.E7.BE.A4.E8.AE.A1.E6.95.B0.E5.99.A8) | Decreases the specified group counters. |
| [getGroupCounters](https://trtc.io/document/56042?platform=javascript&product=chat&menulabel=sdk#.E8.8E.B7.E5.8F.96.E7.BE.A4.E8.AE.A1.E6.95.B0.E5.99.A8) | Gets the specified group counters. |

### Group member

| API | Description |
| --- | --- |
| [getGroupMemberList](https://trtc.io/document/48180?platform=javascript&product=chat&menulabel=sdk#.E8.8E.B7.E5.8F.96.E7.BE.A4.E6.88.90.E5.91.98.E5.88.97.E8.A1.A8) | Gets the group member list. |
| [getGroupMemberProfile](https://trtc.io/document/48177?platform=javascript&product=chat&menulabel=sdk) | Gets a group memberâs profile. |
| [addGroupMember](https://trtc.io/document/48180?platform=javascript&product=chat&menulabel=sdk#49b805dd-4898-44a3-89a4-3b201f839fce) | Adds a group member. |
| [deleteGroupMember](https://trtc.io/document/48180?platform=javascript&product=chat&menulabel=sdk#e7560b78-af68-4009-bc84-1215d7a2ad0b) | Deletes a group member. |
| [setGroupMemberMuteTime](https://trtc.io/document/48180?platform=javascript&product=chat&menulabel=sdk#.E7.A6.81.E8.A8.80.E6.8C.87.E5.AE.9A.E7.BE.A4.E6.88.90.E5.91.98) | Configures the muting period. |
| [setGroupMemberRole](https://trtc.io/document/48180?platform=javascript&product=chat&menulabel=sdk#f35fb570-648c-4b97-99a1-cef5b81b1284) | Modifies the group memberâs role. |
| [setGroupMemberNameCard](https://trtc.io/document/48177?platform=javascript&product=chat&menulabel=sdk#setting-the-name-card-of-a-group-member) | Sets the name card for a group member. |
| [setGroupMemberCustomField](https://trtc.io/document/48177?platform=javascript&product=chat&menulabel=sdk#setting-a-custom-group-member-field) | Sets a custom field for a group member. |
| [markGroupMemberList](https://trtc.io/document/48177?platform=javascript&product=chat&menulabel=sdk#e2c2e663-29cf-4fdc-a9ba-f57a14514387) | Marks group members. |

### Topic

| API | Description |
| --- | --- |
| [getJoinedCommunityList](https://trtc.io/document/48171?platform=javascript&product=chat&menulabel=sdk#getting-the-list-of-topic-enabled-communities) | Gets the list of community groups the current user has joined. |
| [createTopicInCommunity](https://trtc.io/document/48171?platform=javascript&product=chat&menulabel=sdk#creating-a-topic) | Creates a topic in a community group. |
| [deleteTopicFromCommunity](https://trtc.io/document/48171?platform=javascript&product=chat&menulabel=sdk#deleting-a-topic) | Deletes a topic in a community group. |
| [updateTopicProfile](https://trtc.io/document/48171?platform=javascript&product=chat&menulabel=sdk#modifying-the-topic-profile) | Updates a topic profile in a community group. |
| [getTopicList](https://trtc.io/document/48171?platform=javascript&product=chat&menulabel=sdk#getting-the-topic-list) | Gets the topic list in a community group. |

### Signaling

| API | Description |
| --- | --- |
| [addSignalingListener](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#.E7.99.BB.E5.BD.95) | Listens for a signaling event. |
| [removeSignalingListener](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#c48153d7-271c-47fd-b735-b07514b255da) | Removes listener for a signaling event. |
| [invite](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#70fc833f-44f1-4eb0-8136-9fa22711abe8) | Invites someone. |
| [inviteInGroup](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#15399173-cd12-4cc1-8d61-e9ce89a142f8) | Invites members in a group. |
| [cancel](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#edd5129a-c9b8-405b-a4d2-e2ecfb734abc) | The inviter cancels the invitation. |
| [accept](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#a5834bb4-5435-43a1-84d6-4ce7f40f4355) | The invitee accepts the invitation. |
| [reject](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#3a799c2f-dff3-4e27-a71c-63f30d7f98b4) | The invitee rejects the invitation. |
| [getSignalingInfo](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#5205c0fa-1308-4e3c-b286-fbb8cdafd5db) | Gets signaling info from a message. |
| [modifyInvitation](https://trtc.io/document/66034?platform=javascript&product=chat&menulabel=sdk#a5ad293a-6cd7-4df1-ab70-d12e72433c98) | Modifies a invitation. |


---
*Source: [https://trtc.io/document/33999](https://trtc.io/document/33999)*
