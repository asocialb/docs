# Changelog

### 1.9.2 @2023.11.03

- Added TIMSetMsgReactionsChangedCallback callback.
- Added TIMSetMsgAllMessageReceiveOptionCallback callback.
- Added TIMMsgSetAllReceiveMessageOpt interface.
- Added TIMMsgSetAllReceiveMessageOpt2 interface.
- Added TIMMsgGetAllReceiveMessageOpt interface.
- Added TIMMsgSearchCloudMessages interface.
- Added TIMMsgAddMessageReaction interface.
- Added TIMMsgRemoveMessageReaction interface.
- Added TIMMsgGetMessageReactions interface.
- Added TIMMsgGetAllUserListOfMessageReaction interface.
- Added TIMMsgConvertVoiceToText interface.

### 1.9.1 @2023.10.29

- Fixed the bug where the Windows editor cannot be used.

### 1.9.0 @2023.10.25

- Updated the underlying layer to v7.5.4864.
- Added an interface for subscribing to strangers' profiles.
- Added an interface for deleting a conversation list.
- Added an unread message count interface for cleaning a conversation.
- Modified some interface parameter fields (before modification -> after modification):
  - msg_getmsglist_param_is_remble -> msg_getmsglist_param_is_ramble
  - msg_delete_param_is_remble -> msg_delete_param_is_ramble
  - group_atrribute_key -> group_attribute_key
  - group_atrribute_value  --> group_attribute_value
  - friend_respone_identifier  -->  friend_response_identifier
  - friend_respone_action  -->  friend_response_action
  - friend_respone_remark  -->  friend_response_remark
  - friend_respone_group_name  -->. friend_response_group_name
  - group_base_info_lastest_seq â> group_base_info_latest_seq
  - friend_add_pendency_info_idenitifer â> friend_add_pendency_info_identifier
  - user_config_is_ingore_grouptips_unread â> user_config_is_ignore_grouptips_unread
  - message_offlie_push_config â> message_offline_push_config
  - msg_search_param_send_indentifier_array â> msg_search_param_send_identifier_array
  - group_detial_... -> group_detail_...
- Added some interface parameters:
  - UserProfile
  - ConvInfo
  - ConversationListFilter
  - Message
  - MsgGetMsgListParam
  - MessageSearchParam
  - AndroidOfflinePushConfig

## 1.8.3 @2023.01.13

- Added support for adding multiple callback functions to an event callback.
- Added support for deleting specified callback functions.
- Added conversation group related APIs and event callbacks.
- Added support for setting custom conversation data event callbacks.
- Added conversation marking APIs.
- Added the advanced API for getting the conversation list.
- Added group counter related APIs and event callbacks.
- Added the text message translation API.
- Added the API and event callback for getting/subscribing to the total unread message count by filter.

## 1.8.2 @2022.12.06

- Supported Mac M1 chips for build.
- Supported WebGL for build.
- Fixed the parameter types of callbacks such as `GroupGetTopicInfoList` and `ConvGetConvList`.
- Added parameters and callback data logs.

## 1.8.0 @2022.10.11

- Fixed the conversion performance issue involved in first parameter serialization.

## 1.7.9 @2022.09.22

- Fixed iOS build issues.

## 1.7.7 @2022.09.02

- Added English API annotations.
- Added topic, community, user status, and other APIs.
- Upgraded the native SDK.
- Fixed known issues.

## 1.7.6 @2022.06.24

- Supported `string callback data` and `object callback data`.

## 1.7.5 @2022.05.23

- Added APIs for group message read receipts.
- Fixed the issue where the field with a value of `null` was ignored by Newtonsoft serialization.
- Fixed the issue where the `uint64` field in `GroupPendencyResult` was changed to `ulong`.

## 1.6.4 @2022.01.13

- Added SDK support for package manager import.
- Added the feature of adding dependencies after iOS compilation.

## 1.6.0 @2021.12.21

- Switched the underlying cross-platform C APIs.
- Added support for the Windows, macOS, Android, and iOS platforms with unified APIs.
- Note that v1.6.0 is incompatible with earlier versions.

## 1.5.1 @2021.11.24

- Fixed the issue where `-1` is returned for `sequenceid` unexpectedly.
- Added support for macOS.
- Removed the simple message module and enabled the advanced message module for both message receiving and sending.

## 1.5.0 @2021.11.16

- Added support for Windows.

## 1.4.0 @2021.08.03

- Simplified the configuration process on iOS.
- Fixed the IL2CPP packaging error on Android.

## 1.3.1 @2021.05.21

- Fixed known issues.

## 1.3.0 @2021.05.10

- Added the C# model to instantiate data returned by APIs.
- Added the usage of the C# model to `ExampleEntry.cs`.

## 1.2.0 @2021.04.28

- Added `sequenceID` to some message sending APIs to associate message requests and responses.

## 1.1.1 @2021.04.25

- Separated the method of dynamically fetching userSig.

## 1.1.0 @2021.04.15

- Added advanced message APIs.
- Added signaling message APIs.

## 1.0.1 @2021.04.01

- Initialized the project and implemented most APIs.


---
*Source: [https://trtc.io/document/41800](https://trtc.io/document/41800)*
