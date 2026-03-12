# Release Notes

> **The new version (2.9.0.1230) involves API changes for TUICallEngine:**If you encounter compilation errors after updating the Android code to the latest version during development, you can resolve them as follows:Replace "com.tencent.qcloud.tuikit.tuicallengine" with "com.tencent.cloud.tuikit.engine.call".Replace "com.tencent.qcloud.tuikit.TUICommonDefine" with "com.tencent.cloud.tuikit.engine.common.TUICommonDefine".The filename remains unchanged after the upgrade. If there are errors with other files, please re-import them yourself.If you encounter compilation errors after performing a pod update during development, you can resolve them as follows:Replace "import TUICallEngine" with "import RTCRoomEngine".For users who need to upgrade to the Calls API, please note the version grayscale. If you use the Calls API to make a call and the other party's version has not been upgraded, it will lead to a call failure.

## Version 3.3.0.1081 @ 2025.08.25

### New Features

Android/iOS: Supports setting ephemeral call mode.

### Bug Fixes

- Fixed an exceptional issue where setting nickname or avatar via interface would inadvertently modify IM user's custom information.
- Fixed a UI exception when the callee clicks to answer at the same time as the caller hangs up.
- Fixed the Xiaomi channel_id in push notification settings not taking effect.
- Fixed the issue where the camera was not turned off after the callee rejected a video call.
- Fixed UI view not being removed in time due to heartbeat timeout after the user answers the call.
- Android: Optimized construction and destruction processes to eliminate potential exceptions in asynchronous and multi-threaded scenarios, improving stability.
- iOS: Optimized thread management and object destruction processes to enhance stability.

## Version 3.2.0.835 @ 2025.07.16

### New Features

- Android & iOS: Added multiple control fields to TUIOfflinePushInfo, enhancing flexibility and controllability of offline push.
- Android & iOS: Some TUICallEvent callback interfaces now include more essential information, making it easier for developers to obtain comprehensive call event data.
- Android & iOS: Added onUserInviting and onCallNotConnected callbacks to TUICallEvent. It is recommended to use onCallNotConnected instead of the original onCallCancelled callback.

### Bug Fixes

- Android & iOS: Fixed abnormal issues in scenarios of joining a call midway, further improving the stability of joining the call process.
- Android & iOS: Fixed abnormal issues in scenarios of joining a call midway, further improving the stability of joining the call process.

Feature Optimization

- Android & iOS: Optimized the issue where users could not initiate or receive calls again after abnormal hang-ups, improving continuity experience.
- Android & iOS: Improved abnormal call status issues that could occur when call members recover in weak network environments, enhancing call stability under poor network conditions.
- Android & iOS: Optimized the overall experience when Chat and Call are used together, enhancing product collaboration capability.

## Version 3.1.0.824 @ 2025.06.12

### Bug Fixes

- Android/iOS: Fix abnormal issues when joining call, making the call process more stable.

### Feature Optimization

- Across the platform: Optimize experience issues where users are unable to initiate or receive calls again after an abnormal hang-up.
- Across the platform: Optimize call status issues caused by member recovery in weak network environments.
- Across the platform: Optimize experience issues when chat and call are both used.
- iOS: Optimize APNs offline push, support continuous vibration and ring, enhance call answering rate.

## Version 3.0.0.690 @ 2025.04.02

### Bug Fixes

- Across the platform: Fix the issue where the caller cannot display the callee video image normally after the callee answers.
- Across the platform: Fix the call timeout restriction issue of no more than 30 seconds.
- iOS: Fix the issue where video resolution cannot be configured on iOS devices.

### Feature Optimization

- Across the platform: Add the onUserInviting callback API (scenario where inviting a user to call), making the scenario experience better.
- Across the platform: Optimize the TUICallObserver interface with clearer parameters and event, making it easier to understand and use.
- Across the platform: Video call default resolution changed to 720P for better and clearer experience.
- Android/iOS: Upgrade to new UIKit architecture with clearer business logic and easier UI customization.

## Version 2.9.0.1230 @ 2025.2.18

### New Features

- Android & iOS:  Added [calls](https://www.tencentcloud.com/document/product/647/51005#c50c326d-a9c8-48d8-a25e-cf43b7045d65) API, supporting single-person or multiple calls, more flexible call member management, and more powerful REST API. Welcome to use it.
- Android & iOS:  Added [join](https://www.tencentcloud.com/document/product/647/51005#388e76ae-8f44-41e4-ab6e-f41145c59cd3) API, which works with the Calls API to support joining existing calls.
- Android & iOS:  Support for incoming call vibrations.

## Version 2.7.0.1130 @ 2024.11.27

### New Features

Android&iOSï¼Added Traditional Chinese, optimized user experience.

### Bug Fixes

- Android: Fixed the issue of FCM push notifications not popping up.
- Android: Fixed the issue of joining a voice call mid-way and not being able to retrieve the screen of users with the camera on.
- iOS: Fixed the issue of other callee's abnormal view when caller entering in float window mode before answering.
- iOS: Fixed the issue of camera status inconsistency after turning off the camera on the waiting page and then answering page.

## Version 2.6.0.1080 @ 2024.9.29

### Feature optimization

- Android: Support landscape layout on large screen devices to enhance user experience.
- iOS: Adaptation for iOS 16 and above, supports floating window outside the application.
- Android: Supports floating window outside the application when âDisplay over other appsâ permission is granted.

### Bug Fixes

- Android & iOS: Fixed no callback issue after initiating a call in rare scenarios.
- Android & iOS: Fixed the issue of the hangup interface callback occurring twice.
- iOS: Fixed the issue where switching the audio playback device was unavailable during VoIP usage.
- iOS: Fixed the issue where the ringtone does not sound when entering the app after receiving an incoming call in active background status.

## Version 2.5.0.1025 @ 2024.8.7

### Feature optimization

Android: Optimize the logic of joinInGroupCall to fix memory leaks.

### Bug Fixes

- Android&iOS: Fix the issue where web users do not receive group call invitations sent from Android and iOS.
- Android: Fix the issue where during a group call, A voice calls B, and when B clicks the push notification to open the interface, it shows Speaker instead of Earpiece.

## Version 2.4.0.970 Released June 15, 2024

### Feature Optimization

- Android&iOS: Show tips in weak network conditions.
- Android: Optimize the incoming call strategy when the callee's screen is locked.
- iOS: Fix the issue of abnormal memory growth in group calls.

### Bug Fixes

Android&iOS: Fix the display issue when the joinInGroupCall interface is invoked.

## Version 2.3.0.915 Released April 15, 2024

### Feature Optimization

- Android&iOS: Support for displaying call status at the top of the TUIChat group, and allowing group members to join the call actively.
- Android&iOS: Optimized incoming call pop-up logic, default to display banner answer box.
- Android&iOS: Video call supports background blur.

### Bug Fixes

- Android: Fixed the issue of no response when clicking the delete button in the call record editing interface.
- iOS: Fixed the issue of ghosting during the switching process when clicking on the member view in the group call.
- iOS: Fixed the issue of not displaying in specific scenarios of the audio and video interface.
- Android&iOS: Fixed the issue of missing prompts after the call ends when calling a busy line user.

## Version 2.2.0.860 Released February 1, 2024

### Feature Optimization

Android&iOS: Brand new UI visual effects, clearer functions, and better experience.

### Bug Fixes

Android&iOS: Fixed the issue of microphone and camera device mutual occupation after answering incoming calls in conference, live broadcast scenarios.

## Version 2.1.0.810 Released December 19, 2023

### Feature Optimization

- Android: Optimized the prompt for abnormality when calling the TUICallKit interface without logging in.
- Android: Optimized compatibility for Android 14 platform (API 34), for details, see: [Android 14 behavior changes](https://developer.android.com/about/versions/14/behavior-changes-all).
- Android&iOS: Optimized the display of user nicknames, displayed in the following order: User Remarks > User Nickname > User ID, the default is userId.

### Bug Fixes

- iOS: Fixed the issue of overlapping group call avatars.
- iOS: Fixed the problem that the keyboard cannot be retracted when returning to the call interface after opening the floating window to send messages during a video call.
- iOS: Fixed the issue that the camera cannot be switched and moved when switching the camera, turning off the camera, and then switching back to the original camera and reopening it during a video call.
- Android: Fixed the issue that the small window of a single video call cannot be moved under the right-to-left layout mode (RTL mode) such as Arabic.

## Version 2.0.0.750 Released November 3, 2023

### Functionality Enhancement

- Android & iOS: The UIKit supports the Japanese language.
- Android & iOS: Enhanced the display of call nicknames.
- Android & iOS: Adjusted the default ringtone volume from 60% to 100%.

### Defect Rectification

- iOS: Corrected the slow image loading issue in Swift version.
- iOS: Fixed the issue where the call invitation was automatically cancelled after the caller initiated the call and moved the application to the background.

## Version 1.9.0.680 Released September 27, 2023

### Functionality Enhancement

- Android & iOS: Added support for the Arabic language.
- Android & iOS: Optimized the package purchase prompts, enabling redirection to corresponding package purchase pages based on the provided links.
- Android & iOS: Enhanced the default bitrate at different resolutions to ensure clearer output at higher resolutions. For details, refer to [Resolution](https://www.tencentcloud.com/document/product/647/54900#Resolution).
- Android & iOS: The default bitrate for video calls has been set to 600kbps, with a beauty level of grade 4.

### Defect Rectification

- Android & iOS: Resolved inconsistencies between the rejection prompt when initiating a call to a user on the blacklist and the rejection prompt when sending a private chat message.
- iOS: Rectified an anomaly in the video placement for the initiator, which occurred on a 4-person group video call interface when one member declined the call.
- iOS: Addressed an issue where the resolution would be reset if the beauty feature was enabled immediately after successful login.

## Version 1.8.0.620 Released August 14, 2023

### Functionality Enhancement

- Android & iOS: By default, call messages are excluded from the unread count.
- Android: Enhanced the redirection page for floating window permissions on Xiaomi smartphones.

### Defect Rectification

- iOS: Remedied an issue where the onKickOffline callback interface became ineffective after being kicked offline.
- iOS: Fixed an issue where, after clearing the call on the Missed Call interface, returning to the All Calls interface would result in an empty list.

## Version 1.7.2.570 Released July 20, 2023

### Functionality Enhancement

Android: Gravity sensor is turned off by default, optimizing the call experience on large-screen and customized devices.

### Defect Rectification

- Android & iOS: Rectified an issue where, after User A (online) calls User B (offline) and cancels the call, User A calls back User B who logs in thereafter, leading to abnormal cloud call records for user B.
- Android: Resolved the crash issue of TUICallKit after upgrading the TRTC SDK version to 11.3.

## Version 1.7.0.460 Released June 25, 2023

### Functionality Enhancement

- Android & iOS: Includes UI integration solutions, optimizes sample projects, and improves call setting items.
- Android: Reduced the status preservation level during a call to only show standby prompts in the status bar; removed notifications and vibrations.

## Version 1.6.1.410 Released on May 22, 2023

### New features:

- Android & iOS: The UI interfaceÂ [call()](https://www.tencentcloud.com/document/product/647/51005#call_param)Â andÂ [groupCall()](https://www.tencentcloud.com/document/product/647/51005#groupCall_param)Â now support custom room ID.
- Android & iOS: When initiating a call, a string-type room ID can be passed in, seeÂ [CallParams](https://www.tencentcloud.com/document/product/647/54900#CallParams)Â for details.

### Bug fixes:

- Android: Fixed issue where an error would occur on theÂ groupCall when generating list parameters usingÂ Arrays.asList.
- Android: Fixed issue where the video call display was abnormal.
- iOS: Fixed issue where it conflicted with TUIRoom component.
- iOS: Fixed issue where initiating a call immediately after successful login would cause a crash.
- iOS: Fixed issue where the invite page would not appear intermittently when clicking on a notification message to enter the app.

## Version 1.6.0.360 Released on April 27, 2023

### New features:

- Android: TUICallKit added the Kotlin language version;
- iOS: TUICallKit added the Swift language version;
- Android & iOS: Added a page to display local call records.

### Functional optimization:

- Android: Optimized the display of video call avatars.
- Android & iOS: In group calls, other group members can be invited to join the call by default.

### Bug fixes:

- Android: Fixed issues where devices running Android 12 or higher would have no sound after being connected to Bluetooth;
- Android: Fixed intermittent issues where the muting setting on the callee side was not effective;
- iOS: Fixed intermittent issues where devices could not receive incoming call invitations after relogging in;
- iOS: Fixed the issue where theÂ enableCustomViewRouteÂ interface of TUICallKit was not valid;
- iOS: Fixed the issue where the nickname was displayed incorrectly on the VoIP push page.

## Version 1.5.1.310 Released on April 17, 2023

### New features:

- Android & iOS: Added VoIP message push function to provide a better call answering experience.
- Android & iOS: Support custom extended fields when initiating a call, seeÂ TUICallDefine.CallParamsÂ parameter in theÂ [call()](https://www.tencentcloud.com/document/product/647/51006#call)Â method for details.

### Functional optimization:

- Android & iOS: Optimized offline push capabilities for Huawei, Xiaomi, FCM, and other manufacturers, added manufacturer message categories, and channel ID settings.

### Bug fixes:

- Android & iOS: Fixed issue where the Chat custom property was overwritten after initiating a call.
- Android: Fixed issue where theÂ totalTimeÂ unit in theÂ [onCallEnd](https://www.tencentcloud.com/document/product/647/51007#oncallend)Â callback was incorrect.

## Version 1.5.0.305 Released on March 09, 2023

### Functional optimization:

- Android & iOS: Optimized chat-message display.
- Android: The ear-to-screen messaging function is turned off by default now.
- Android: Upgraded gradle plugin and version.
- Android: Optimized mediaPlayer class, supporting loop playback of ringtones.

### Bug fixes:

- Android & iOS: Fixed issue where the callee would not receive theÂ onCallCancelÂ callback when answering a call fails.
- Android: Fixed issue where the caller would receive an exception when the callee fails to answer the call.
- Android: Fixed issue where the caller cancels the call during the permission check of the first call and the callee pulls up the interface again.
- Android: Fixed the issue whereÂ userIdÂ was empty when returning network quality to the upper callback.

## Version 1.4.0.255 Released on January 06, 2023

### New features:

- Android & iOS: Support custom call timeout time, see TUICallDefine.CallParams parameter in theÂ call()Â method for details.

### Bug fixes:

- Android & iOS: Fixed issue where joining a room actively (joinInGroupCall) would result in abnormal termination of the call.
- Android: Fixed issue where there were abnormalities with call status when you exited the audio and video call answer interface and came back to the foreground again.

## Version 1.3.0.205 Released on November 30, 2022

### New features:

- Android & iOS: Added beauty setting interfaceÂ setBeautyLevel(), supporting turning off default beauty.

### Functional optimization:

- iOS: Optimized the framework size of TUICallKit.

### Bug fixes:

- Android & iOS: Fixed issue where the calling interface did not disappear when the server dissolves a room or kicks out a user.
- Android: Fixed issue where if A called offline user B and then cancelled, then A called B again and B came online, the calling interface did not appear.

## Version 1.2.0.153 Released on November 14, 2022

### New features:

- Android & iOS: Support for custom video encoding resolutions.
- Android & iOS: Support setting rendering parameters for video: rendering direction and filling mode.
- Android & iOS: Support integration of third-party beauty features.
- Android & iOS: TUICallKit has added overloaded interfacesÂ call()Â andÂ groupCall(), supporting custom offline messages (see API documentation for details).

### Functional optimization:

- Android & iOS: Optimized some TUICallObserver callback exception issues.
- Android & iOS: Optimized the video-to-audio switching function, supporting switching in offline state.
- Android & iOS: Improved error codes and error prompts for TUICallKit.
- iOS: Standardized TUICallEngine and TUICallKit Swift API names.

### Bug fixes:

- Android & iOS: Fixed issue where you would still receive previously rejected incoming calls after logging back in to your account.
- Android: Fixed issue where you would encounter abnormal hang-ups in invites from group chats in one-to-one chats.
- Android: Fixed issue where there were abnormalities with multiple-scene exits from live rooms, preventing the initiation of calls.
- Android: Fixed issue where contacting person A while B and C were calling each other at the same time would cause C to enter A's room at random.

## Version 1.1.0.103 Released on September 30, 2022

- Android & iOS: Optimized the feature of inviting new members to the current group call.
- Android & iOS: Optimized the call process to avoid the charging of recording, moderation, and other fees before a call is answered.
- Android & iOS: Added support for custom offline notifications.
- Android & iOS: Changed the parameters of some **TUICallEngine** APIs. For details, see [call()](https://www.tencentcloud.com/document/product/647/51006#call), [groupCall()](https://www.tencentcloud.com/document/product/647/51006#groupcall), [inviteUser()](https://www.tencentcloud.com/document/product/647/51006#inviteuser), and [onCallReceived()](https://www.tencentcloud.com/document/product/647/51007#oncallreceived).
- Android & iOS: Fixed occasional callback errors during a group call.
- Android & iOS: Fixed the status abnormal issue caused by repeated login or expired `UserSig`.
- iOS: Fixed the issue where, when a mixed-language `TUICallKit` project is built with Objective-C and Swift, an error occurs when `init` is called.
- Android: Fixed the issue where an error occurs when the floating window feature is integrated for a Kotlin project.

## Version 1.0.0.53 Released on August 15, 2022

### First release:

- Android & iOS: Supports one-to-one and group audio/video calls.
- Android & iOS: Supports offline call push for mainstream devices on the market.
- Android & iOS: Supports custom profile photos and aliases.
- Android & iOS: Supports floating call windows.
- Android & iOS: Supports custom ringtones.
- Android & iOS: Supports receiving calls when the user is logged in on multiple platforms.


---
*Source: [https://trtc.io/document/51020](https://trtc.io/document/51020)*
