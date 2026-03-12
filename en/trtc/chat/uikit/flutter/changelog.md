# Changelog

## IM Flutter SDK 8.9.7511 @2026.02.10

### SDK

- Added support for message streaming.
- Resolved an issue where synchronized conversation markers could be lost during login if the local conversation record did not exist.
- Fixed a potential failure to update atAll data in conversation information during multi-device login scenarios.
- Fixed abnormal behavior when fetching merged message lists after locally inserting merged messages.
- Resolved a failure to retrieve nested merged messages in offline scenarios.

## IM Flutter SDK 8.8.7354 @2025.11.27

### SDK

- Fixed known stability issues.

## IM Flutter SDK 8.7.7201 @2025.09.05

### SDK

- Added backup CN domain for long network connection DNS addresses.
- Long connections now include built-in HTTP-type IP addresses.
- Push supports OPPO private message channel templates.
- Push supports FCM message priority configuration.
- Push supports vivo notification type settings.
- Added data reporting for "joining multiple avchatrooms simultaneously".
- Supports sending group-directed messages in communities.
- Supports inserting local messages after login failure.
- Supports setting group approval options when creating Work groups.
- Optimized error message descriptions when sending messages after being kicked offline.
- Added cloud-controlled frequency limiting when pulling avchatroom member lists.
- Fixed Android platform Zip extraction security vulnerability.
- Fixed token reporting errors in self-integrated Flutter push notifications.
- Fixed occasional missing callbacks when pulling historical messages.

### IM Flutter SDK 8.6.7019 @2025.05.28

- Fix issues related to offline push.
- Fixed the conversion error of the message type parameter C interface in the interface for obtaining historical messages.
- Fix the problem of abnormal data returned by nextElem.
- Fixed the abnormal problem of getting the unread list of group messages.

### IM Flutter SDK 8.5.6864+4 @2025.04.14

- Support the HarmonyOS NEXT platform with Flutter version 3.22.1-0.0.pre.32.
- Implement the interface logic using FFI.
- Move the user_status_type.dart class from the models folder to the enum folder.
- Delete the v2_tim_offline_push_info.dart file and replace it with offlinePushInfo.dart
- Remove the groupID parameter in the setTopicInfo method of v2_tim_group_manager and v2_tim_community_manager.
- For integration on the web platform, please import and use the classes from the web/compatible_models package.

### IM Flutter SDK 8.5.6864 @2025.03.28

- Added support for binding device accounts to Chat accounts.
- Added support for end-to-end message troubleshooting.
- Added randomized domains for long connections.
- Optimized long connection routing rotation strategy.
- Completed read status reporting for the last message in conversations.
- Fixed inaccurate mute duration field in group member profiles.
- Fixed issue where setting custom fields on merged forwarded messages would create new conversations.
- Fixed incorrect account login state after switching accounts during network disconnection.
- Fixed inability to set custom fields for friends on HarmonyOS platform.
- Fixed inaccurate state synchronization for iOS offline push notifications.
- Fixed occasional incorrect ordering in conversation lists.

### IM Flutter SDK 8.4.6675-beta.2 @2025.03.10

- Supports HarmonyOS NEXT.

### IM Flutter SDK 8.4.6675 @2025.02.11

- Fixed the problem of abnormal paging group member list.

### IM Flutter SDK 8.4.6667 @2025.01.15

- Optimize the local cache policy of the log module.
- Upgrade the SSO connection IP address of the India site.
- Support SSO to configure the long - polling interval of live broadcast group owners.
- Optimize the topic data pulling logic and directly return when there is no network connection.

### IM Flutter SDK 8.3.6498 @2024.11.26

- Conversation markers support filtering duplicate requests.
- Optimization and upgrade of the protocol for unread messages and unread counts in single chats.
- Supplement the information of the retractor in the last message of the conversation.
- Fix an occasional issue where the size of the message body exceeds the limit when merging and forwarding messages.
- Fix an occasional failure when editing and merging forwarded messages.

### IM Flutter SDK 8.2.6325+4 @2024.11.18

- Migrated to Flutter 3.24.

### Chat Flutter SDK 8.1.6122 @2024.08.30

- Android platform IM SDK adapted to 16K Page Size.
- Optimize server time correction logic.
- Optimize HTTP addresses for anycast routing on the international site.
- Optimize default value for QUIC channel ping timeout.
- Fix the issue where Mac end group notifications do not distinguish between actively joining a group and being passively invited.

### Chat Flutter UIKit V2 - 1.4.0 @2024.06.14

#### General

- **[Breakthrough]**: Added comprehensive support for **Web**, including both Mobile and Desktop browsers.
- Added support to return the login status for the `initUIKit` method.
- Added `addGlobalCallback` and `removeGlobalCallback` to `TencentCloudChatCoreController`, enabling the integration and management of custom `TencentCloudChatCallbacks` throughout your codebase.
- Improved device screen recognition logic.

#### Message (TencentCloudChatMessage)

- **[Breakthrough]**: Added integration support of the new **Sticker Plugin**, allowing users to send and view a variety of stickers and emojis.
- Added support for **Community and Topic** chats. Users can now participate in these group types. Added `topicID` to `TencentCloudChatMessageOptions` to specify the chat topic along with its corresponding `groupID` for community identification.
- Added a unified format for all builders in `TencentCloudChatMessage`, modifying their parameters. The previous builders have been removed. Each builder in `TencentCloudChatMessageBuilders` now includes four standardized parameters: `Key? key`, `widgets`, `data`, and `methods`, enhancing usability and comprehension. Builders from other components will be updated to this unified format in future versions.
- Added support to select message text on desktop, facilitating easier copying of entire or partial text messages.
- Added markdown parsing support for text messages, which is disabled by default. Additionally, URLs in text messages can now be launched directly.
- Added new customization options to `TencentCloudChatMessageConfig`: `mentionGroupAdminAndOwnerOnly`, `showMessageSenderName`, `enableParseMarkdown`, `enableAutoReportReadStatusForComingMessages`, `enableReplyWithMention`, `attachmentConfig`, `additionalAttachmentOptionsForMobile`, `additionalInputControlBarOptionsForDesktop`, `defaultMessageSelectionOperationsConfig`, and `additionalMessageMenuOptions`.
- Added `beforeMessageSending` and `beforeRenderMessageList` hooks to `TencentCloudChatMessageLifeCycleEventHandlers`, and added `onTapLink`, `onPrimaryTapAvatar`, and `onSecondaryTapAvatar` to `TencentCloudChatMessageUIEventHandlers` for enhanced business logic customization.
- Added new methods to `TencentCloudChatMessageController`: `updateMessages`, `mentionGroupMembers`, `setMessageTextWithMentions`, and `scrollToBottom`, providing greater control over the component.
- Added support to re-edit recalled messages.
- Improved the UI display for text messages, particularly the time and status indicators, message bubble width, and more.
- Improved the icons in both the message context menu and input attachment actions, replacing Material Icons with custom-designed icons.
- Improved the display of quoted/replied messages in the message list, and changed the interaction for navigation.
- Improved the logic for message replies and sending, including group member mentions, auto-focus when replying, scrolling to the bottom after sending a message, and media message sending.
- Improved the performance of the message list, message status updates, and group member lists in large groups.
- Fixed an issue where calls could not be initiated via message header actions.
- Fixed video preview and playback issues.
- Fixed various UI display errors, including boundary issues.
- Fixed an issue where the message list could not be scrolled using a laptop touchpad.
- Fixed an issue where recording on mobile phone may lose control in some cases.

### Chat Flutter UIKit V2 - 1.3.0 @2024.04.17

#### General

- Enhanced the  `initUIKit`  function with several improvements, streamlining the configuration process and increasing overall usability. Key updates include:
  - A new  `components`  parameter that consolidates component-related configurations, including the required  `usedComponentsRegister`  for manually declaring used components. It also allows for optional global configurations, builders, controllers, and event handlers for each component, affecting all instances of each component.
  - A new  `onTencentCloudChatSDKEvent`  callback within the  `callbacks`  parameter handles SDK-related events, replacing the previous  `sdkListener`  from  `options` .
  - The  `config`  parameter now focuses on global configurations for the UIKit, removing  `usedComponentsRegister`  and  `preloadDataConfig` . The  `usedComponentsRegister`  has been moved to the  `components`  parameter.
  - Removed the requirement for passing in  `context` .
- Introduced a new manager for each component, named by appending  `Manager`  to the component's name (e.g.,  `TencentCloudChatMessageManager` ), providing the following functions for better and easier integration:
  - `register` : [Manually declaring the usage of each component](https://pub.dev/packages/tencent_cloud_chat#basic-usage) during the  `initUIKit`  call.
  - `controller` : [Taking control of each component](https://pub.dev/packages/tencent_cloud_chat#global-taking-control-of-each-component) on a global scale.
  - `eventHandlers` : [Handling component-level events](https://pub.dev/packages/tencent_cloud_chat#global-handling-component-level-events) on a global scale.
  - `builder` : [Dynamically updating UI builders](https://pub.dev/packages/tencent_cloud_chat#dynamically-updating-ui-builders) for all instances.
  - `config` : [Configuring components](https://pub.dev/packages/tencent_cloud_chat#global-configuring-components) for all instances dynamically.
- Migrated the  `register`  from the  `Instance`  of each component to the  `Manager` , as described in the previous point.
- Refined the core data storage structure and performance, paving the way for future feature enhancements.

#### Message (TencentCloudChatMessage)

- Changed the default configurations for  `enabledGroupTypesForMessageReadReceipt`  to be empty. This requires specifying the group types for which the message read receipt feature should be enabled, after enabling them in the console.
- Fixed an issue where the message read status could not be updated dynamically for one-to-one chats.
- Reduced the number of rebuilds for message list items to improve performance.

### Chat Flutter UIKit V2 - 1.2.1 @2024.04.02

#### Conversation (TencentCloudChatConversation)

- Fixed an issue where the main component was released on desktop after switching login accounts.
- Changed the button `Mark as Unread` to `Mark as Read` and implemented its functionality.

#### Message (TencentCloudChatMessage)

- Fixed an issue where some configurations in `TencentCloudChatMessageConfig` were invalid.
- Fixed an issue where a permission request failed on both iOS and Android devices when installing the app for the first time. Also fixed an issue where permissions could not be manually enabled in settings.
- Improved the message locating for the original message of a replied message.
- Fixed an issue where messages in the message list could not be dynamically received and displayed in some cases, especially after login account switching.
- Fixed an issue related to voice message playback.
- Displayed a default avatar for users without a profile picture.

### Chat Flutter UIKit V2 - 1.2.0 @2024.03.28

#### General

- Added support for **tablet devices**, including adaptive UI for iPad and various Android tablets. Now you can deploy to all platforms (mobile, tablet, desktop, web) at once using a single codebase.
- Introduced **callback** functionality, allowing handling of SDK API errors and specific UIKit events that require user attention with `eventCode` and `text` by default, on a global scale. Developers can use UIKit with `TencentCloudChatCoreController.initUIKit()`  and set the callbacks accordingly.
- Enhanced global dialog styles for Apple devices with a more native Cupertino style.
- Optimized global data storage structures and improved underlying performance.
- Ensured that all data from the previous account is removed from memory after logging out, and no data remains when logging in with a new account. 
Replaced the original `logout` method with the `resetUIKit({bool shouldLogout = false})`  method in `TencentCloudChatCoreController` to ensure no data remains in UIKit after logout and avoid logging out twice after being kicked off. For specific usage, refer to the comment.
- Added SVG support for avatars.

#### Conversation (TencentCloudChatConversation)

- Optimized time display in conversation items to improve readability.
- Fixed an issue where the conversation unread counts could not be updated dynamically.

#### Message (TencentCloudChatMessage)

- Added support for long press on mobile devices and navigate to the original message by clicking quoted message on desktop devices.
- Improved message location and navigation capabilities, including jumping to specific messages. Optimized performance and user experience. This capability is exposed by the `scrollToSpecificMessage` method in `TencentCloudChatMessageController`, which allows control to navigate to specific messages and optionally highlight the target message.
- Removed the ability to download large images and view original images in image preview mode.
- Optimized the calculation of message long-press menu height to improve accuracy, avoiding situations where menu items are not fully displayed. Also improved animation performance.
- Added `showMessageTimeIndicator`, `showMessageStatusIndicator`, `defaultMessageSelectionOperationsConfig`, and `defaultMessageMenuConfig` to `TencentCloudChatMessageConfig` for better customization of message bubbles, message selection menus, and message menus. For specific usage, refer to the comments for each parameter.
- Removed `useGroupMessageReadReceipt` from `TencentCloudChatMessageConfig`. Please use `enabledGroupTypesForMessageReadReceipt` instead.
- Improved the display position of text message status and time indicators, no longer occupying a separate column.
- Enhanced the default time separator in the message list to support localized and internationalized date and time representations.
- Resolved issues related to media preview and voice messaging functionality.
- Fixed several bugs, reduced redundant page builds, improved performance, and minimized CPU and memory resource usage.

### Contact (TencentCloudChatContact)

- Resolved the issue of contact names being too long and overflowing the boundaries.

### Chat Flutter UIKit V2 - 1.1.2 @2024.03.13

#### General

- Further enhanced the integration process.
- Optimized screen type recognition logic for better adaptation to different screen types.

#### Conversation *(TencentCloudChatConversation)*

- Added a new `onTap`event, `onTapConversationItem`, to `TencentCloudChatConversationUIEventHandlers`of `TencentCloudChatConversationEventHandlers`on the `eventHandlers`in the `TencentCloudChatConversation` component. This allows for custom event handling when a conversation item is clicked. If it returns `false`, the default logic will be executed, navigating to the corresponding `TencentCloudChatMessage` widget.
- Introduced a new builder, `conversationHeaderBuilder`, for customizing the header bar.

#### Message *(TencentCloudChatMessage)*

- Enhanced message list with localized date and time indicators, adapting to user's language settings for a localization experience.

### Chat Flutter UIKit V2 - 1.1.1 @2024.03.11

- Reduced the number of steps, increasing the success rate of one-time integration, lowering the barrier to entry, and enhancing the integration process.

### Chat Flutter UIKit - 2.5.0 @2023.2.28

#### Breaking Changes

- Migrated to Flutter 3.19. Support for Flutter 3.16 and earlier versions has been discontinued.

#### Notes

- Starting from Flutter 3.19, it is recommended to apply Flutter's Gradle plugins using Gradle's declarative plugins {} block (also known as the Plugin DSL) ( [see details](https://docs.flutter.dev/release/breaking-changes/flutter-gradle-plugin-apply)).
- In line with this, our sample app on the GitHub repo has also been migrated to this new approach. If you'd like to migrate to this new approach, see our [sample app repo](https://github.com/TencentCloud/chat-demo-flutter).

### Chat Flutter UIKit V2 - 1.1.0 @2024.1.23

The entirely redeveloped and revamped version of UIKit has been officially released. Compared to the previous version of UIKit, there are several significant enhancements and optimizations, which include:

1. **Theme Customization**: Switch between **light and dark mode** on the fly, or customize your own theme with our rich set of options.
2. **Internationalization**: We've added support for more languages including Arabic, and introduced **a Middle Eastern UI**. Our powerful and user-friendly [localization tools](https://pub.dev/packages/tencent_cloud_chat_intl) make it easier than ever to [customize the localization configuration and the translation](https://pub.dev/packages/tencent_cloud_chat_intl), and provide a localized user experience.
3. **Performance Enhancements**: We've made significant improvements to the **performance of the message list**, and introduced efficient and precise message positioning capabilities.
4. **Multimedia Support**: Experience improved multimedia and file message handling, with continuous playback for voice messages and **swipeable multimedia message previews**.
5. **Detail Optimizations**: We've added numerous detail optimizations including rich animations, haptic feedback, and refined interfaces to enhance the user experience.
6. **New Features**: Enjoy new features like a grid-style avatar, redesigned forwarding panel, group member selector, and a new message long-press menu.
7. **Modular Packages**: Components are broken down into **modular packages**, allowing for on-demand imports and reducing unnecessary bloat. 
Each modular package supports built-in navigation. For instance, you can automatically navigate from a Conversation to a Message to start a chat, 
without the need to manually instantiate multiple pages and handle the transitions yourself. This greatly simplifies the complexity of development and integration.
8. **Developer-friendly Design**: We've introduced a more unified, standardized component parameter design, clearer code naming, and more detailed comments to make development easier and more efficient.

### Chat Flutter UIKit - 2.4.0 @2023.11.28

#### Breaking Changes

- Migrated to support Flutter 3.16.0.
- Upgraded the minimum supported Android Gradle Plugin to the 7.3 version to meet Flutter requirements.

### Chat Flutter SDK (Low-level SDK) - 6.0.2-6.0.8 @2023.11.03

- Fixed several bugs.

### Chat Flutter UIKit - 2.3.3 @2023.10.30

#### New Features

- Added a new lifecycle hook of `MessageListShouldmount`.

#### Bug Fixes

- Fixed an issue on time tag creator.

### Chat Flutter SDK (Low-level SDK) - 6.0.1 @2023.10.24

- Non-friend user profile update listener
- Non-friend user profile update callback
- Group-wide mute callback
- Group member tag & group member tag callback
- Added message response interface and the corresponding callback
- Added message recall with recall information callback
- Set global message receiving options
- Message cloud search
- Conversation delete callback
- Callback for unread count statistics by specified category in conversation
- Delete conversations in batches
- Get unread count of conversations by category
- Listen for unread count changes by specified type
- Clear conversation unread count (markxxxAsRead interface deprecated)
- Improved offline push fields
- Voice-to-text

### Chat Flutter UIKit - 2.3.2 @2023.09.27

#### Improvements

- Enhanced message list performance.

#### Bug Fixes

- Fixed an issue that prevented the group member addition/removal modal box from closing.
- Addressed several other bugs.

### Chat Flutter UIKit - 2.3.1 @2023.09.13

#### Bug Fixes

- Resolved an issue that history messages can't be removed after a conversation was deleted.
- Fixed an issue that the Android users were prevented from opening files sent by themselves.

### Chat Flutter UIKit - 2.3.0 @2023.08.30

#### Breaking Changes

- Upgraded and migrated to support Flutter 3.13.0. Support for Flutter 3.10 and earlier versions has been dropped.

#### Recommendations

- Customers who do not wish to upgrade to Flutter 3.13.0 are advised to continue using version 2.2.1 of our Chat UIKit. However, we strongly recommend upgrading to Flutter 3.13.0 as it includes numerous performance improvements and introduces cutting-edge features.

### Chat Flutter UIKit - 2.2.1 @2023.08.29

#### New Features

- Introduced a new `groupMemberList` configuration in `TUIKitChat`; when specified, TUIKit will not load it automatically, optimizing network traffic usage.
- Added support for image copying on desktop platforms.

#### Bug Fixes

- Fixed an issue preventing the removal of image loading status.
- Resolved a problem that prevented images from being saved to the device gallery.
- Addressed a potential issue causing the `mentionOtherMemberInGroup` function in `TIMUIKitChatController` to fail.
- Corrected an issue that could lead to improper image rendering.

### Chat Flutter UIKit - 2.2.0 @2023.08.18

#### New Features

- Introduced a newly-designed set of Emoji image stickers, available for seamless integration within textual content, providing an enhanced user experience.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bce14292415a11eeacb1525400cea498.png)

- Streamlined the implementation of stickers, removing the need for additional complex coding. Full functionality is enabled by default, with customization options available through the `stickerPanelConfig` configuration in `TIMUIKitChatConfig`.
- Extended support for rendering embedded image stickers within text messages when the `Markdown` parsing mode is activated, combining a rich, user-friendly experience with the ability to display formatted Markdown text.

#### Improvements

- Enhanced group chat functionality on the Desktop, enabling mentions ( `@` tag) to be inserted at any position within a composed message, rather than only at the end. Additionally, deleting `@` tags has been optimized.
- Maintained message sending permissions for the group owner and administrators during "mute all" scenarios.
- Enabled the use of a return `null` value for the `customHoverBar` to utilize the default.
- Refined the revoke button functionality for group administrators.
- Removed full-screen support for video previews on the Web and introduced an alternative "Open in New Window" button for an enlarged view.
- Implemented UIKit log recording to facilitate issue identification and troubleshooting.
- Introduced a delete button for the small PNG sticker selection panel on mobile devices, which previously was only available in the Unicode emoji selection panel.

#### Bug Fixes

- Resolved an issue preventing photo capturing on devices running Android 12 or lower.
- Rectified display inaccuracies related to picture aspect ratios.
- Addressed several issues concerning voice and video calls.

### Chat Flutter UIKit - 2.1.3+1 @2023.07.19

#### New Features

- Introduced [a new custom internationalization language scheme](https://trtc.io/document/52154) that supports adding language packs, adding or modifying entries, and makes customizing i18n more accessible. This feature helps your app achieve a more convenient globalization process and easier customer acquisition worldwide.
- Provided a seamless experience for previewing large images and playing videos within desktop environments (applications and web) by avoiding frequent page transitions. Enhanced the user experience for image previews and video playback. Please note that video playback is currently supported only on the web and not in desktop applications.
- Supported to integrate with the new online customer service plugin (tencent_cloud_chat_customer_service_plugin).
- Added two new life cycle hooks, `messageDidSend` and `messageShouldMount` to `ChatLifeCycle`.

#### Improvements

- Optimized the usage, interface, and interaction of the sticker panel.
- Enhanced mobile video playback interaction and UI.
- Refined the error prompt when sending a 0 KB file fails.
- Enabled users to close modals on desktop by clicking the bottom gray overlay area.
- Improved the UI and interaction of image and video messages in the message list.
- Added the ability to open self-sent file messages without downloading.
- Optimized the download status animation of file messages on the web.

#### Bug Fixes

- Fixed an issue preventing mobile image previews from being dragged after zooming.
- Resolved an issue that might cause the message selection status not to be removed after canceling a message forward action.
- Addressed an issue that might cause the microphone usage not to end after sending a voice message, which means the microphone was not released.

### Chat Flutter UIKit - 2.1.2 @2023.06.20

#### New Features

- Introduced a new message recall mode, which enables group administrators to recall any message from any group member. To enable this feature, set `isGroupAdminRecallEnabled` in `TIMUIKitChatConfig` to `true`.
- Added support for draft text functionality on the Web. Activate this feature by setting `isUseDraftOnWeb` in `TIMUIKitChatConfig` to `true`. Since the Chat SDK doesn't support this functionality, draft data will be stored in TUIKit's memory. Be aware that draft text will be lost upon refreshing the website.
- Enabled using the default message abstract text when `abstractMessageBuilder` returns `null`.

#### Improvements

- The duration for video messages sent from the Web will no longer be displayed, as this type of video message does not contain an accurate video duration.
- Removed the hover color on the message input area on Desktop.
- Added auto-focus support for the message input area on Desktop.
- Enhanced the rendering of text messages in markdown mode, particularly for clickable link extraction and HTML tag handling.
- Limited the number of lines displayed for replied messages to a maximum of 2 lines to avoid occupying excessive space.
- Optimized the message replying process, ensuring that a message referencing another message can still display the replied message, even when it is too old.

#### Bug Fixes

- Fixed an issue that could cause the profile page to display no data.
- Fixed an issue that could prevent the message sending button from being displayed after selecting an emoji on mobile Web.
- Fixed an issue that could prevent the message long-press menu from showing on mobile Web.
- Fixed an issue where editing a message would carry over to another conversation when switching between conversations.
- Fixed an issue that could prevent displaying the `Modal` on Desktop.
- Fixed an issue that caused the `iconImageAsset` from the `MessageToolTipItem` class to not work properly.

### Chat Flutter UIKit - 2.1.0 @2023.05.30

#### Breaking Changes

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e3b89b4dfe9811edb545525400c56988.png)

- Migrated to **Flutter 3.10.0 and Dart 3.0.0**, no longer supporting projects with Flutter < 3.10.0 and Dart < 3.0.0.
- Updated the minimum requirement for **Android AGP to 7.0,** projects with AGP < 7.0 are no longer supported.

We highly recommend updating to these new versions for a better experience.

#### New Features

- Added several methods to `TIMUIKitChatController`, including `hideAllBottomPanelOnMobile`, `mentionOtherMemberInGroup`, `setInputTextField`, and `getGroupMemberList`. See the corresponding annotations for usage.
- Added more parameter fields to the `TIMUIKitChatController`'s `sendMessage` method. For details, see the corresponding annotations.
- Added `onSecondaryTapAvatar` to `TIMUIKitChat`, serving as callback trigger for secondary avatar clicks in the message list.
- Introduced `isUseMessageHoverBarOnDesktop` and `desktopMessageInputFieldLines` to `TIMUIKitChatConfig`. For usage details, see the corresponding annotations.

#### Improvements

- Enhanced performance and user experience when switching conversations on Desktop, including features like text field auto-focus and draft text.
- Enabled displaying correct new lines in markdown mode.
- Changed the order of members in the mentioned member selection panel: Group Owner => Group Administrator => Member, sorted based on the code units' first differing position in the member show names.
- Implemented auto-focus after clicking a member in the mentioned member selection panel.
- Added text field auto-focus when replying to a message.
- Updated other members' display names in at-tag messages to use `namecard`, followed by `nickname` and `userId`.
- Widened Desktop message input area's control bar.
- Replaced the default icon in Desktop's message input area from `png` to `svg` for better performance and clarity. `DesktopControlBarConfig` now supports defining `svgPath` for each item as well.
- Improved Web platform detection.
- Mentioning "all" or "at all" can now only be used by group owners and administrators.
- Supported returning null for each message item builder in `MessageItemBuilder` to use the default message widget.
- Enhanced group members filtering in the group member mentioned selection panel with case-insensitive fuzzy matching, leading to increased filtering accuracy.
- For security purposes, downloading files by `fetch` and `blob` in the Web now replaces previewing files in a new browser tab, whereas previewing images and videos is displayed in a new tab on the Web.
- Changed the default order in the message tooltip menu.
- Previewing images and videos is set to open in a new tab on the Web.
- Improved the ratio for sending video messages.

#### Bug Fixes

- Fixed issues when enabling the section function in markdown mode with `inEnableTextSelection` set to `true`.
- Addressed an issue where the replied message was removed when selecting all text in the message and clicking backspace.
- Fixed an issue where Chinese characters could not be entered while replying to a message.
- Resolved some console errors during debugging.
- Fixed an issue with links not opening in markdown mode.
- Fixed an issue that caused two `Scrollbar`s to appear in the message input field on Desktop.
- Solved an issue that might cause incorrect layout when the app is launched.
- Addressed an issue where messages were directly sent when the Enter key was pressed while entering Chinese text.
- Fixed related issues with the mentioned member selection panel on Desktop.
- Resolved an issue where images couldn't be pasted directly into the message input area for sending on the Web.
- Fixed an issue where files couldn't be sent on the Web.
- Remedied an issue where media and files couldn't be opened when local downloaded resources were deleted; now, resources will automatically re-download.
- Fixed an issue that caused the `iconImageAsset` of the `MessageToolTipItem` config to head internally to this chat UIKit.
- Improved the downloading process of media and files by avoiding frequent calls to `setState`, thus preventing the entire project from re-rendering.

### Chat Flutter UIKit - 2.0.0 @2023.05.06

***The version 2.0.0 has undergone significant changes and has gone through 7 preview versions. If you want to know the specific updates for each preview version, you can go to***[***pub.dev***](https://pub.dev/packages/tencent_cloud_chat_uikit/changelog)***to check.***

***Here are some key points:***

#### New Features:

- ***[Core capability]: TUIKit have been extended to support***[all platforms](https://www.tencentcloud.com/document/product/1047/50059)***, including iOS, Android, Web, Windows, and MacOS, with significant changes to the codebase. The user interface has been enhanced to adapt to devices with different screen types, and additional special capabilities are available for each type of device. For example, desktop devices now support file drag-and-drop for sending files.***
- Information copying: Added the ability to copy information from the screen, such as groupID.
- Callkit integration: The Callkit button no longer needs to be added to `MorePanelConfig`. If `tencent_call_uikit` is installed, the video call and voice call buttons will be displayed automatically.
- New chat configuration: `TIMUIKitChatConfig` now includes `offlinePushInfo`, which can customize the entire `offlinePushInfo` for each message. The priority of this field is higher than the previous separate configuration fields for this object.
- New color configuration: Added `appbarTextColor` and `appbarBgColor` to configure the color of the Appbar. Also added `selectPanelBgColor` and `selectPanelTextIconColor` to configure the color of the message multi-selection panel.
- New chat configuration: `isAllowLongPressAvatarToAt`. This option controls whether users are allowed to mention another user in the group by long-pressing on their avatar.
- Added `addtionalMessageToolTips` to `ToolTipsConfig`. This new property allows developers to add additional message operation tool tips beyond the default prompt items. The previous addtionalItemBuilder has been replaced by this new property. With `addtionalMessageToolTips`, developers only need to specify the data for the tool tip items, rather than providing the entire widget. This makes it easier to use, as you no longer need to worry about UI display.
- Added `isPreloadMessagesAfterInit` to `TIMUIKitConfig`, which can determine whether TUIKit should preload some messages after initialization to speed up message display.
- Introduced `isAutoReportRead` to `TIMUIKitChatConfig` to control read status reporting.

#### Improvements:

- Improved group management logic, non-administrators can no longer access the management interface.
- Improved cursor positioning when sending messages.
- Improved and optimized scrollbar functionality.
- Enhanced clickable URL support in messages, URLs now support both with and without "https://" prefixes.
- Improved compatibility: TUIKit is now compatible with Flutter versions 3.0.0 to 3.7.7.
- Improved group management: Members in `workgroup` can no longer be muted.
- Improved avatar: Ensures that the avatar can be as small as possible while covering the entire target box.
- Eliminated the dependency on `fluttertoast`. All necessary customer reminders are now triggered through the `onTUIKitCallbackListener` info callback in your project.
- Removed six other unnecessary dependency packages to reduce size and improve performance.
- Improved the clarity of the `sendMessage` function in `TIMUIKitChatController` by replacing the use of `convID` to represent both userID and `groupID` with separate parameters.
- The time separator on the message list: The default 12-hour display has been changed to 24-hour display.
- Message translation now targets the language of TUIKit, rather than directly depending on the system language. The language of TUIKit can be automatically set to the system language or defined by the user.
- Optimized the animation of the message text input area.
- Message operation menu display: If there are no operation items and the message sticker reaction module is not used, the long-press message will not display.
- Upgraded several dependencies to the latest version, including `ffi` upgraded to 2.0.1 and `file_picker` upgraded to 5.2.9.
- Added support for the new permission authorization schema on Android 13 and `targetSdkVersion` greater than 33.
- Corrected `extHight` to `extHeight` in `TIMUIKitChatConfig` and changed the default value to 1.3.
- When `isAtWhenReply` is set to `true`, the reply or quote button is marked as Reply, otherwise it is marked as Quote.
- The @member tag can now be deleted at once.

### Chat Flutter UIKit - 1.7.0 @2023.02.23

- Addition: Support for quickly navigating to the first unread message in a group chat with more than 20 new unread messages, using the dynamic tongue located in the top right corner of the screen. This feature allows for swift movement through the messages, regardless of their quantity.
- Addition: Customize the border radius for all avatars is now supported. You can set the default avatar border radius using `defaultAvatarBorderRadius` in `TIMUIKitConfig`.
- Optimization: The delete button on the sticker sending panel has been improved for better usability.
- Optimization: Some English labels on the screen have been updated to better reflect local expressions.
- Fix: An issue causing errors when sending a large number of stickers has been resolved.
- Fix: Some errors that were occurring in the sticker panel have been addressed.
- Fix: An issue that caused errors on mentioning all members.

### Chat Flutter UIKit - 1.6.0 @2023.02.08

- Added `scrollToConversation` to `TIMUIKitConversationController`. You can now easily navigate to a specific conversation in the conversation list and move to the next unread conversation by double-clicking the tab bar. For more information, see our [demo source code](https://github.com/TencentCloud/chat-demo-flutter/blob/main/lib/src/conversation.dart).
- Optimized the performance of the historical message list while scrolling over a large distance.

### Chat Flutter UIKit - 1.5.0 @2023.02.02

- Added `defaultAvatarAssetPath` to the global configuration `TIMUIKitConfig` to define the default profile photo.
- Added support for Flutter 3.7.0.
- Fixed the `chatBgColor` configuration.

### Chat Flutter UIKit - 1.4.0 @2023.01.13

- Added the feature of translating the text in text messages and replied and quoted messages. To use the feature, you only need to long press the text and choose **Translate**. This feature can be enabled or disabled by the `showTranslation` parameter in `ToolTipsConfig`.
- Optimized the position of the window that pops up when text is long pressed.
- Optimized the keyboard pop-up event.

### Chat Flutter SDK (Low-level SDK) - 5.0.8 @2023.01.13

- Added the group counter capability: Ordinary groups and audio-video groups support meta counters. For details, see groupCounter related APIs.

### Chat Flutter UIKit - 1.3.0 @2023.01.11

- Fixed the failure to display the nickname of the new group owner in the group tip message after the group ownership is transferred.
- Removed the confirmation window that pops up before a file is opened.

### Chat Flutter UIKit - 1.2.0 @2023.01.06

- Fixed the failure to display the input box when the chat component is switched from recording to keyboard.
- Fixed the issue where, when a combined message is sent to multiple recipients, only the first recipient can receive the message.
- Optimized `MessageItemBuilder` so that it can be used to display the combined message page.

### Chat Flutter UIKit - 1.1.0 @2022.12.27

- Embedded the emoji plug-in in TUIKit by default. Now we support three types of emojis: Unicode emoji, small image emoji, and big image emoji. The emoji use methods have been optimized. For more information, see [here](https://www.tencentcloud.com/document/product/1047/52227).
- Optimized the topic feature to support more custom capabilities.
- Optimized the animation for the input area, keyboard, sticker panel, and "More" panel.
- Optimized: Emojis, including Unicode and small images, can be inserted to any position in text messages.
- Optimized: The profile photo in a profile can be previewed with a large image.
- Optimized: The user ID in a user profile can be copied.
- Optimized: Several UI details are added, including `TIMUIKitAddFriend`, `TIMUIKitAddGroup`, `TIMUIKitGroupProfile`, and `TIMUIKitProfile`.
- Optimized: `TIMUIKitGroupProfile` and `TIMUIKitProfile` support modifying content by modifying IDs.
- Optimized `TIMUIKitGroupChat` to display the loading animation when a user clicks the image/video download button.
- Fixed some errors.

### Chat Flutter SDK (Low-level SDK) - 5.0.6 @2022.11.29

- Fixed the iOS bundle version loss issue.
- Improvement: The underlying native SDK has been upgraded to 6.9.3557.

### Chat Flutter UIKit - 1.0.1 @2022.11.28

- Removed `groupTRTCTipsItemBuilder` from `MessageItemBuilder`. Please use `customMessageItemBuilder` instead.

### Chat Flutter UIKit - 1.0.0 @2022.11.23

- Supported adding the Flutter module to your existing applications, that is, hybrid development. For more information, see [here](https://www.tencentcloud.com/document/product/1047/51456).
- Supported customizing stickers and emojis. **The use methods have changed greatly.**
- Supported adding the Flutter module to your existing applications, that is, hybrid development. For more information, see [here](https://www.tencentcloud.com/document/product/1047/51456).
- Supported customizing stickers and emojis. **The use methods have changed greatly.**
- Optimized the loading time of the historical message list, especially when there are a large number of media and file messages.
- Supported scrolling in more panel areas.
- Optimized the feature of loading the latest messages when scrolling back to the bottom for smoother loading.
- Fixed the Android album image quantity issue.
- Fixed the border crossing issue of long text in the group profile card.
- Fixed some errors.

> **Note**If you upgrade your TUIKit to this version, pay special attention to the changes of the emoji part (the second update item) and audio/video call part (the last but one update item). Otherwise, related capabilities will not work properly.
> If you have any questions in the process of modification, feel free to contact us.

### Chat Flutter SDK (Low-level SDK) - 5.0.4 @2022.11.23

- Multimedia message online URLs will no longer be returned by default. They need to be obtained by calling the `getMessageOnlineUrl` API.
- Multimedia message local URLs ( `localurl`) will no longer be returned by default. They will be returned only after you download messages successfully by calling the `downloadMessage` API.
- The `onMessageDownloadProgressCallback` callback is added for `advanceMessageListener` and will be triggered when the multimedia message download progress is updated.
- Added the `disableBadgeNumber` method to iOS clients. After the method is called, the application badge is not set by default when the application is switched to the background.
- Supported adding the Flutter module to your existing applications, that is, hybrid development. For more information, see [here](https://www.tencentcloud.com/document/product/1047/51456).
- Optimized the underlying dynamic library download logic for PC clients.
- Upgraded the underlying SDK version to 6.8.
- Reconstructed the web client underlying SDK. You need to import the corresponding JS via npm as instructed [here](https://intl.cloud.tencent.com/document/product/1047/45907).
- Reconstructed the macOS client underlying SDK. You need to import the SDK as instructed [here](https://intl.cloud.tencent.com/document/product/1047/45907).

> **Note**Major changes have been made to multimedia messages and file messages. Please modify your existing logic for obtaining and rendering such messages according to the first four updates. Otherwise, the messages will not be displayed.
> If you have any questions in the process of modification, feel free to contact us.

### Chat Flutter UIKit - 0.1.8 @2022.10.21

- Optimized the file batch download queue to allow a user to select multiple file messages at a time.
- Optimized the group list widget to support automatic update.
- Optimized camera shooting to support low-performance devices and automatically adjust the resolution for the devices.
- Optimized the support for customizing the color and text styles of the app bar, especially on the `TIMUIKitChat` component.
- Fixed the issue where friend notes or nicknames could not be displayed in group tips.
- Fixed video playback errors.
- Fixed several issues.

### Chat Flutter SDK (Low-level SDK) - 4.1.8 @2022.10.18

- Added support for PC platforms, including macOS and Windows.
- Added message extensions.
- Added signaling editing.
- Upgraded the underlying SDK.
- Fixed the later-version JDK conversion issue.
- Fixed several issues.

### Chat Flutter UIKit - 0.1.7 @2022.10.18

- Added support for large and RAW images, especially those captured from the latest versions of iOS and the iPhone 14 Pro series, compressed and formatted before automatic sending.
- Optimized performance and stability, especially the historical message list and startup.
- Optimized the initialization of `TIMUIKitChat` as an idempotent operation.
- Supported loading the latest messages when scrolling back to the bottom.
- Optimized support for Flutter 2.x and 3.x series.
- Permission support for iOS album: allowing only certain images.
- Fixed several issues.

### Chat Flutter UIKit - 0.1.5 @2022.09.22

- Added web support. Now you can implement TUIKit on iOS/Android/Web platforms.
- Added the feature of checking disk storage after login, which can be configured in `config` in `init`.
- Added the following attributes to `TIMUIKitChatConfig`: `timeDividerConfig`, `notificationAndroidSound` (Huawei and Google push sound configuration), `isSupportMarkdown` (whether text messages support Markdown parsing), and `onTapLink`.
- Removed the default emoji list due to copyright issues. You can provide TUIKit with your own emoji list via [tim_ui_kit_sticker_plugin](https://pub.dev/packages/tim_ui_kit_sticker_plugin).
- Optimized: Now you can disable the display of @ messages in the conversation list
- Optimized: Now you can set the return values of `notificationExt` and `notificationBody` in `TIMUIKitChatConfig` and `MessageItemBuilder` as `null`, and, in specific cases, you can use the default values ââas needed. This means you can control whether to use custom settings without redefining the same logic as TUIKit in code.
- Optimized: Supported multi-line text messages.
- Optimized the experience of `TIMUIKitChat`. In addition, to use `TIMUIKitChatController`, you need to pass in `controler`, as described [here](https://intl.cloud.tencent.com/document/product/1047/50054).

### Chat Flutter SDK (Low-level SDK) - 4.1.3 @2022.09.21

- Fixed some web issues.

### Chat Flutter SDK (Low-level SDK) - 4.1.1+2 @2022.08.25

- Upgraded the underlying library version to 6.6.x.
- Full support for Chat Flutter SDK for web.

### Chat Flutter SDK (Low-level SDK) -  4.1.0 @2022.08.09

- Upgraded the underlying library version.

### Chat Flutter UIKit - 0.1.3 @2022.08.03

- Added user input status.
- Added the capability to respond to message emojis.
- Added the display of user online status.

### Chat Flutter SDK (Low-level SDK) - 4.0.8 @2022.07.25

- Added an advanced API for getting the conversation list, which supports pulling the conversation list by conversation type/tag.
- Added an API for customizing conversation marks.
- Added the conversation grouping capability.
- Decreased the dependent Dart version to 2.0.0.
- Supported multi-engine Flutter.
- Supported offline push sound effect configuration on Android.
- Supported custom user online status.
- Upgraded the underlying library version to 6.5.x.

### Chat Flutter UIKit - 0.1.2 @2022.07.08

- Fixed the issue where the original referenced third-party underlying recording library `flutter_record_plugin_plus` could not be used.

### Chat Flutter UIKit - 0.1.1 @2022.07.07

- Optimized the image preview logic.
- Added lifecycle hooks for each component.
- Added the mute status to group chat page.
- Supported redirection upon clicking URLs in text messages and added the website information preview card.
- Added TUIKit layer global event callbacks, including callbacks for messages that need to be prompted, Flutter layer errors, and Chat API layer errors. TUIKit no longer provides message pop-ups. You can customize pop-up windows based on callbacks and prompts.
- Reconstructed the group profile component `TUIKitGroupProfile` and user profile component `TUIKitProfile`, simplifying usage and enabling super-fast access.

### Chat Flutter SDK (Low-level SDK) - 4.0.7 @2022.07.07

- Supported custom badge numbers in iOS.
- Optimized the group joining request logic.

### Chat Flutter SDK (Low-level SDK) - 4.0.6 @2022.07.04

- Upgraded the underlying library version to 6.2.x.
- Fixed offline push information fields.

### Chat Flutter SDK (Low-level SDK) - 4.0.5 @2022.07.01

- Added user online status query.
- Supported requesting historical messages by message type.
- Supported sending rich text messages.

### Chat Flutter UIKit - 0.1.0 @2022.06.10

- Added the atomic development capability of the `TIMUIKitChat` component, and you can assemble the chat page by yourself through various sub-components.
- Supported the capability to edit messages and update UIs.
- Added group joining request approval page components.
- Added Traditional Chinese as a language option.
- Opened up more custom component parameters.

### Chat Flutter UIKit - 0.0.9 @2022.05.30

- Supported offline push, with the newly released [tim_ui_kit_push_plugin](https://pub.dev/packages/tim_ui_kit_push_plugin) push plugin.
- Supported Flutter 3.0.
- Optimized the local preview of media messages.

### Chat Flutter SDK (Low-level SDK) - 4.0.2 @2022.05.27

- Fixed the local video path issue.

### Chat Flutter SDK (Low-level SDK) - 4.0.1 @2022.05.23

- Added the topic capability.
- Added the message editing capability.

### Chat Flutter SDK (Low-level SDK) - 4.0.0 @2022.04.26

- Upgraded the underlying library version to 6.2.x.
- Fixed offline push information fields.

### Chat Flutter UIKit - 0.0.8 @2022.04.24

- Added the group message read receipt capability.
- Added a small toolbar in the lower right corner of the chat area to support returning to the bottom/displaying the number of new messages/@message reminder.

### Chat Flutter SDK (Without UI Library) 3.9.3 @2022.04.20

- Fixed the issue where the `boolValue` of a group muting tip was lost.
- Added the `key(string)-boolValue(bool)`  format in addition to the existing `key(string)-value(string)`  in the callback for group information modification.
- Fixed the issue where the `nameCard` field of a conversation was not parsed by the instance.
- Added APIs for group message read receipts.
- [sendMessageReadRecepts](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_message_manager/V2TIMMessageManager/sendMessageReadReceipts.html): Sends group message read receipts.
- [getMessageReadRecepts](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_message_manager/V2TIMMessageManager/getMessageReadReceipts.html): Gets read receipts for messages sent by yourself.
- [getgroupMessageReadMemeberList](https://pub.dev/documentation/tencent_cloud_chat_sdk/latest/manager_v2_tim_message_manager/V2TIMMessageManager/getGroupMessageReadMemberList.html): Gets the list of members who have (or have not) read a message sent by yourself.
- Improved the Flutter for web.

### Chat Flutter UIKit - 0.0.7 @2022.04.13

- Optimized experience.

### Chat Flutter UIKit - 0.0.6 @2022.04.08

- Opened up the API for automatically displaying sent messages on the screen and provided more custom capability parameters.
- Optimized user login authentication.
- Optimized privacy policies to better align with personal information protection laws.

### Chat Flutter UIKit - 0.0.5 @2022.03.24

- Opened up more custom capabilities of the chat area component `TIMUIKitChat`.

### Chat Flutter SDK (Low-level SDK) - 3.9.1 @2022.03.24

- Upgraded the underlying library to v6.1.2155.

### Chat Flutter SDK (Low-level SDK) - 3.9.0 @2022.03.22

- Modified GroupListener.

### Chat Flutter SDK (Low-level SDK) - 3.8.9 @2022.03.18

- Fixed the registration result listening issue.

### Chat Flutter UIKit - 0.0.4 @2022.03.17

- Added support for sending images and videos.
- Optimized topic styles.
- Optimized the search component.

### Chat Flutter UIKit - 0.0.3 @2022.03.14

- Optimized component details.
- Improved the automatic internationalization capability.
- Added the global search component `TIMUIKitSearch`.
- Added the in-conversation search component `TIMUIKitSearchMsgDetail`.
- Added the friend adding component `TIMUIKitAddFriend`.
- Added the group joining component `TIMUIKitAddGroup`.
- Added topic styles.

### Chat Flutter SDK (Low-level SDK) - 3.8.4 @2022.03.14

- Updated APIs.

### Chat Flutter UIKit - 0.0.2 @2022.03.02

- Optimized the `TIMUIKitChat` component.
- Supported automatic and manual switching between Simplified Chinese and English.

### Chat Flutter UIKit - 0.0.1 @2022.03.01

- Launched Tencent Cloud Chat for Flutter (including the UI library and business logic).
- Released the first seven main components, including the chat area, conversation list, contact and group profiles, contacts list, blocklist, and friend request list.

### Chat Flutter SDK (Low-level SDK) - 3.8.3 @2022.03.01

- Switched the token encoding format based on the environment.

### Chat Flutter SDK (Low-level SDK) - 3.8.2 @2022.02.21

- Updated group member parameter constraints.

### Chat Flutter SDK (Low-level SDK) - 3.8.0 @2022.02.17

- Upgraded the underlying API dependencies.

### Chat Flutter SDK (Low-level SDK) - 3.7.8 @2022.02.15

- Fixed the exception caused by force unwrapping.

### Chat Flutter SDK (Low-level SDK) - 3.7.7 @2022.02.10

- Fixed the Swift code warning.
- Rewrote Swift's force unwrapping code.
- Added the `id` field to the `message` instance returned by the `sendMessage` API.

### Chat Flutter SDK (Low-level SDK) - 3.7.5 @2022.01.23

- Upgraded the underlying library to v6.0.1975.
- Supported the TPNS token for offline push configuration.

### Chat Flutter SDK (Low-level SDK) - 3.7.1 @2022.01.12

- Added the feature of returning the message creation ID for a message sending progress event.
- Optimized the callback by reminding the business side that the callback error is caught in SDK and needs to be modified.

### Chat Flutter SDK (Low-level SDK) - 3.7.0 @2022.01.10

- Optimized the unpacking of cloudCustomData.

### Chat Flutter SDK (Low-level SDK) - 3.6.9 @2022.01.06

- Optimized the message reply parameters.

### Chat Flutter SDK (Low-level SDK) - 3.6.8 @2022.01.06

- Optimized the message reply API.

### Chat Flutter SDK (Low-level SDK) - 3.6.7 @2022.01.05

- Upgraded the compiling environment for iOS from 8.0 to 9.0.

### Chat Flutter SDK (Low-level SDK) - 3.6.6 @2021.12.30

- Added the message reply API.
- Fixed the issue for web where the release mode triggered an error.

### Chat Flutter SDK (Low-level SDK) - 3.6.5 @2021.12.17

- Fixed syntax errors in Java.

### Chat Flutter SDK (Low-level SDK) - 3.6.4 @2021.12.17

- Fixed the issue where there was no return for Android async registration events.
- Fixed the issue where removing a general listening event triggered an error.
- Added the UUID of a message being sent in its progress event.

### Chat Flutter SDK (Low-level SDK) - 3.6.3 @2021.12.9

- Optimized the `addFriend` API: Changed `addType` from int to FriendTypeEnum.
- Optimized the `acceptFriendApplication` API: Changed `acceptType` from int to FriendResponseTypeEnum.
- Optimized the `checkFriend` API: Changed `checkType` from int to FriendTypeEnum.
- Optimized the `createGroup` API: Changed `addOpt` from int to GroupAddOptTypeEnum.
- Optimized the `deleteFromFriendList` API: Changed `deleteType` from int to FriendTypeEnum.
- Optimized the `getGroupMemberList` API: Changed `filter` from int to GroupMemberFilterTypeEnum.
- Optimized the `getHistoryMessageList` API: Changed `type` from int to HistoryMsgGetTypeEnum.
- Optimized the `getHistoryMessageListWithoutFormat` API: Changed `type` from int to HistoryMsgGetTypeEnum.
- Optimized the `getGroupMemberList` API: Changed `type` from int to GroupMemberFilterTypeEnum.
- Optimized the `getGroupMemberList` API: Changed `filter` from int to GroupMemberFilterTypeEnum.
- Optimized the `initSDK` API: Changed `loglevel` from int to LogLevelEnum.
- Optimized the `refuseFriendApplication` API: Changed `acceptType` from int to FriendApplicationTypeEnum.
- Optimized the `sendCustomMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendFaceMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendFileMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendForwardMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendImageMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendLocationMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendMergerMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendSoundMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendTextAtMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `sendTextMessage` API: Changed `priority` from int to MessagePriorityEnum.
- Optimized the `setGroupMemberRole` API: Changed `role` from int to GroupMemberRoleTypeEnum.
- Changed the event callback mode to asynchronous.

### Chat Flutter SDK (Low-level SDK) - 3.6.2 @2021.12.9

- Fixed the issue where no uuid was passed in for removing an advanced message.

### Chat Flutter SDK (Low-level SDK) - 3.6.1 @2021.12.8

- Fixed the loss of the file progress event.

### Chat Flutter SDK (Low-level SDK) - 3.6.0 @2021.12.1

- Added the support for multiple listener registrations and callbacks in modules.
- Added the `markAllMessageAsRead` API for marking all messages as read.
- Added the feature of parsing combined messages.
- Upgraded the Native SDK to v5.8.1668.

### Chat Flutter SDK (Low-level SDK) - 3.5.6 @2021.11.25

- Fixed the `checkFriend` failure.
- Fixed the issue where `getC2CHistoryMessageList` API failed to get subsequent messages.

### Chat Flutter SDK (Low-level SDK) - 3.5.5 @2021.11.23

- Adjusted the architecture.

### Chat Flutter SDK (Low-level SDK) - 3.5.4 @2021.11.22

- Added the `downloadMergeMessage` API.

### Chat Flutter SDK (Low-level SDK) - 3.5.3 @2021.11.15

- Added the `onTotalUnreadMessageCountChanged` event.
- Added the `orderkey` field in the `V2TimConversation` API for conversation sorting.

### Chat Flutter SDK (Low-level SDK) - 3.5.2 @2021.11.12

Added support for web.

### Chat Flutter SDK (Low-level SDK) - 3.5.1 @2021.11.10

- Added the logic to be compatible with array index out of bounds.

### Chat Flutter SDK (Low-level SDK) - 3.5.0 @2021.10.1

- Fixed several known issues.
- Added the following APIs:
- callExperimentalAPI
- clearC2CHistoryMessage
- clearGroupHistoryMessage
- searchLocalMessages
- findMessages
- searchGroups
- searchGroupMembers
- getSignalingInfo
- addInvitedSignaling
- searchFriends

### Chat Flutter SDK (Low-level SDK) - 1.0.34 @2021.03.22

- Fixed the issue for iOS where getting the message history triggered an error.

### Chat Flutter SDK (Low-level SDK) - 1.0.33 @2021.03.22

- Changed the `minSdkVersion` value of the SDK to 16.

### Chat Flutter SDK (Low-level SDK) - 1.0.32 @2021.03.22

- Fixed the crash that occurred when `lastMessage` in the conversation information was empty.

### Chat Flutter SDK (Low-level SDK) - 1.0.30-1.0.31 @2021.03.18

- Fixed the crash that occurred when the `data` field of a custom message was null.

### Chat Flutter SDK (Low-level SDK) - 1.0.29 @2021.03.16

- [Important] Fixed the issue where passing in parameters for getting the group member list triggered an error.

### Chat Flutter SDK (Low-level SDK) - 1.0.28 @2021.03.16

- [Important] Changed the input parameters of the `checkFriends` API.

### Chat Flutter SDK (Low-level SDK) - 1.0.15-1.0.27 @2021.03.15

- Added the group member custom field.
- Improved iOS signaling.
- Fixed the iOS signaling bug.
- Added the feature of parsing a custom field into `string` before returning it.
- Optimized the settings of custom fields of the profile.
- Updated the `getHistoryMessageList` API for Android.
- Fixed the issue for Android where passing in parameters for the `checkFriend` API triggered an error.

### Chat Flutter SDK (Low-level SDK) - 1.0.5-1.0.14 @2021.02.26

- Fixed the issue where passing in parameters for the `deleteFriendApplication` API triggered an error.
- Updated the Native SDK to v5.1.132.
- Updated the Native SDK to v5.1.137.
- Fixed the bug that occurred when passing in parameters for the signaling invitation API.
- Fixed the issue where the signaling API did not return an ID.
- Modified the SDK compression configuration.
- Fixed signaling callback bugs.
- Modified the return data of custom messages.
- [Important] Modified the format of content returned for a signaling message. Please upgrade to this version or later to use signaling.

### Chat Flutter SDK (Low-level SDK) - 1.0.4 @2021.01.14

- Upgraded the SDK for Android to v5.1.129.
- Upgraded the SDK for iOS to v5.1.129.

### Chat Flutter SDK (Low-level SDK) - 1.0.3 @2021.01.13

- Added support for Android and iOS platforms.
- Added support for one-to-one chat and group chat (discussion and audio-video groups).
- Added support for text, emoji, image, audio, and custom messages.
- Added support for offline push of APNs (reporting of token and foreground/background switch).
- Added the feature of storing messages locally.

### Chat Flutter SDK (Low-level SDK) - 0.0.1-1.0.2 @2020.12.01

- Launched the Flutter SDK.
- Invited users to join the beta test.


---
*Source: [https://trtc.io/document/45915](https://trtc.io/document/45915)*
