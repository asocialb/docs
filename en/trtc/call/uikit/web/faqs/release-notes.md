# Release Notes

> **Release Notes****ï¼**Starting from **v4.1.0**, all packages have been migrated to the `@trtc` namespace with API updates. The table below shows the mapping between new and legacy package names:**Framework****New Package (v4.1.0+)****Legacy Package (Below v4.0.x)****Description****Vue3****@trtc/calls-uikit-vue****@tencentcloud/call-uikit-vue****v4.1.0+ is actively updated and maintained (recommended for use).****For legacy versions (v4.0.x and below), only bug fixes will be provided.****v4.1.0+ replaces the deprecated the**`call`**and**`groupCall`**methods with the**`calls`**method.****Vue2.7****@trtc/calls-uikit-vue2****@tencentcloud/call-uikit-vue2**
> **Vue2.6****@trtc/calls-uikit-vue2.6****@tencentcloud/call-uikit-vue2.6**
> **React****@trtc/calls-uikit-react****@tencentcloud/call-uikit-react**
> **Before upgrading to v4.1.0+, please note:**If you upgrade to use the new `calls` method, ensure that all participants in a call are using compatible versions. **Calls initiated with v4.1.0+ will not be received by users on v4.0.x or below**, as they do not support the new `calls` interface.

## New Package Name (v4.1.0+)

## Version 4.4.1 @2025.12.03

### New Feature

- Added error message pop-up functionality, enabling users to promptly understand operation statuses.

## Version 4.4.0 @2025.11.21

### Fixes

- Fixed an issue where the call interface would rarely and incorrectly display call duration after the caller canceled the call.
- Fixed an issue where, after the callee logged out, if the caller initiated a call and the callee re-logged into the same device within the timeout period, the callee would not receive the call request.
- Fixed an issue where the userID parameter was incorrectly passed in the callee's callback when the caller canceled a call.

## Version 4.2.4 @2025.10.28

### Fixes

- Resolved call connection failure issue caused by repeatedly clicking the "Answer" button.

## Version 4.2.3 @2025.10.22

### Optimization

Optimized the init interface to execute only after the WASM module is fully loaded.

## Version 4.2.2 @2025.10.10

### Optimization

- When integrating with Chat, removed logic related to using the legacy call and groupCall interfaces.

## Version 4.2.1 @2025.09.29

### Optimization

- Upgraded the dependency from tui-core to tui-core-lite.

## Version 4.1.0 @2025.09.19

### Breaking Change

- CallKit package name changed from @tencentcloud/call-uikit-vue to @trtc/calls-uikit-vue.
- Dependency upgraded from @tencentcloud/chat to @tencentcloud/lite-chat.
- Support for the original call/groupCall interfaces has been discontinued.

### **Legacy**Package Name (Below v4.0.x)

## Version 4.0.11 @2025.10.28

### Fixes

- Resolved call connection failure issue caused by repeatedly clicking the "Answer" button.

## Version 4.0.10 @2025.10.22

### Optimization

- Optimized the init interface to execute only after the WASM module is fully loaded.

## Version 4.0.9 @2025.09.01

### Fixes

- Fixed an issue where calling the nickname or avatar setting interface caused abnormal modifications to IM user custom information.
- Fixed a UI anomaly that occurred when the caller hung up simultaneously as the callee clicked to answer.

## Version 4.0.8 @2025.07.14

### Fixes

- Fixed an issue where valid call invitations were not received upon IM reconnection (OnConnectSuccess).
- Fixed abnormal execution issues when calling destroyInstance of CallEngine.
- Addressed an issue where multiple login calls could cause the callee's Reject to refuse the call.

## Version 4.0.7 @2025.06.06

### New Features

- Added support for ending calls via REST API.
- When inviting others, notifying the callee about users already in a call via the inviteeList parameter.
- Added handling for room destruction via REST API.
- Enhanced compatibility handling for network interruption and recovery in calls.

### Optimizations

- Optimized the "join-in-progress" functionality when integrating with Chat TUIKit.
- Optimized the logic for ending calls after prolonged consecutive heartbeat failures (network loss/timeout) on the client.
- Optimized handling for abnormal interruptions (closing browser, refreshing browser, swiping left in mini-program, exiting via top-right corner, etc.) to immediately end the call.
- Optimized the callee's reject interface logic by removing the room exit operation.
- Enhanced troubleshooting logs by adding online logging.
- Optimized CallKit event listening, changing the monitored event from USER_ACCEPT to ON_CALL_BEGIN.
- Defaulted camera to off when joining a call in progress.
- In multi-user calls, the caller defaults to the large screen view.

### Fixes

- Fixed an issue where groupId was not updated when joining a call in progress.
- Fixed an issue where groupId was missing in call record reporting.
- Fixed inaccuracies in recorded call participants for scenarios involving joining in progress and inviting others.
- Fixed abnormal onUserLeave callback issues when actively joining a call.

## Version 4.0.4 @2025.03.31

### New features

- Added onCallNotConnected event.
- Added onUserInviting event.
- Added chatGroupID field in ON_CALL_RECEIVED, CALLING_END, and ON_CALL_BEGIN events.
- Added online troubleshooting logs.

### Feature Optimization

- Optimized multi-device login issues.
- Optimized the room dismissal logic via TRTC REST API.
- Optimized local log printing.

### Bug Fixes

- Fixed log reporting issues (missing fields caused no records in Kibana).
- Fixed the invalid setSelfInfo API issue.
- Fixed the abnormal capability bit verification code issue in calls API.
- Fixed the issue where onCallCanceled event was not triggered when all callees were busy during outgoing calls.
- Removed the userLeave event triggered by TRTC room exit.

## Version 4.0.3 @2025.03.13

### Bug Fixes

When all callees are busy and the engine does not emit a cancel event, CallKit terminates the call based on the remote user list.

## Version 4.0.2 @2025.02.18

### New features

- Added calls API, supporting initiating one-to-one calls or group calls, with more flexible call member management and more powerful REST API capabilities. Welcome to use it.
- Added join API, working with calls API to support joining existing calls.

## Version 3.3.9 @2024.10.21

### Feature Optimization

Component text can be dynamically changed after language switching.

### Bug Fixes

- Fix the issue of resetting front/rear camera when closing camera.
- Fix the problem where call interface disappears when inviteUser API reports an error during call.

## Version 3.3.8 @2024.09.27

### New features

Add theme switching functionality to React CallKit.

### Feature Optimization

Optimize the parent element mounting for device list in React CallKit.

## Version 3.3.7 @2024.09.13

### Bug Fixes

Fixed the issue where the speaker remains off in the next call after being turned off in the first call.

## Version 3.3.6 @2024.09.13

### New features

Added CallMessage component in React for integrating on-screen message display with chat.

### Feature Optimization

Optimized the on-screen message display logic to align with WeChat's message display.

## Version 3.3.4 @2024.09.10

### New features

React added onMinimized Callback Event.

### Feature Optimization

- React supports Floating Window Drag and Drop.
- Optimized Mobile Terminal interaction for clicking the Speaker button, adjusted to turn on/off the Speaker.
- Optimized React Device List hierarchy.

## Version 3.3.3 @2024.08.06

### New features

Added feature to turn on/off the speaker .

### Feature Optimization

- react: Optimized button loading effect.
- Optimized the creation and termination of ringtone instances.
- Optimized the interaction of flipping the camera and virtual background button after turning off the camera.
- Optimized the error content when directly calling call/groupCall API before the user init .
- Optimized the warning phenomenon of setVideoResolution in the console when the user has not init and introduced the TUICallKit component on the page.

### Bug Fixes

- react: Fixed the spacing issue of the Virtual Background button.
- react: Fixed the issue where the nickname was not truncated.

## Version 3.3.2 @2024.07.12

### New features

- Added support for showing and hiding the invite others button.
- Prompt when the network status is poor.

### Bug Fixes

- After selecting the device, redial. The selected device in the device list does not match the current device.
- When the device list is empty, do not display the device selection list.
- Fix the known issues of midway joining.

## Version 3.3.1 @2024.06.25

### Bug Fixes

- Fix some issues with midway joining feature .
- Delete the comments for debug files.

## Version 3.3.0 @2024.06.14

### New features

- Added support for Custom Definition window size display and setting camera initial state feature.
- Vue&React: Added support for passing in Custom Definition string Room Number.
- React: Added react TUICallKit Virtual Background feature.

### Feature Optimization

Extended offlinePushInfo parameters to support Offline Push Sound Settings and other features.

### Bug Fixes

- Fixed the issue where a call exception occurs immediately after a call is accepted and then timed out.
- Fix the issue with group call, caller waiting, answer page, remote user, and nickname display.

### Feature Optimization

UI Customization:Add Interface Log Reporting

## Version 3.2.9 @2024.05.29

### Feature Optimization

UI Customized Interface adds Log Reporting.

## Version 3.2.8 @2024.05.27

### Bug Fixes

Fixed SDK Import ref Path Error issue.

## Version 3.2.7 @2024.05.17

### New features

- New Feature UI component for joining in group.
- New Feat UI interface, supporting setting of call background and button hiding.
- Adjusted parameter validation when initiating a call, supports string room numbers.

## Version 3.2.4 @2024.05.06

### New features

- Video call supports background blur.

### Bug Fixes

- Fixed an issue in uni-app packaging for web projects where image loading icon failed.
- Fixed the issue with the group call switch camera button.
- Optimized the application getting stuck after a button click, addressing the abnormal issues caused by clicking the button again.

## Version 3.2.3 @2024.04.19

### New features

New Feature Group Call Supports Camera Switching.

### Feature Optimization

Optimize [TUICallKit SDK](https://www.npmjs.com/package/@tencentcloud/call-uikit-vue) Readme.

## Version 3.2.2 @2024.03.25

### New features

Brand new UI visual effects, clearer functions, and better experience.

### Feature Feature Optimization

Optimize data reporting using TUICallKit.

## Version 3.2.1 @2024.03.08

### New features

Language log reporting.

## Version 3.2.0 @2024.02.23

### New features

New features default offline push parameters.

### Bug Fixes

Bug Fixes the issue where group calls have no nickname.

## Version 3.1.9 @2024.01.30

### Bug Fixes

- Bug Fixes the issue where group calls do not display user information.
- Fixed the issue where the 'Confirm' button was still clickable in the selector component when there were no members available.
- Fixed the issue where muting the microphone during a call would prevent the audio stream from being transmitted in subsequent calls (upgrade [trtc-cloud-js-sdk](https://www.npmjs.com/package/trtc-cloud-js-sdk) to v2.2.7+).

## Version 3.1.8 @2024.01.19

### Bug Fixes

Fixed the impact of the selector component's style on the page.

## Version 3.1.7 @2024.01.12

### Bug Fixes

- New features a retry mechanism for interfaces and fixed the playback failure issue due to the inability to find the DOM node.
- Fixed the device list selection style issue on PC.

## Version 3.1.6 @2023.12.29

### Feature Optimization

- Optimized the prompt message during group calls.
- Optimized the display issue when the nickname is too long.

### Bug Fixes

- Fixed the camera permission issue for voice call requests.
- Fixed the issue with 'destroyed'.
- Fixed the hang-up issue in the floating window under different call scenarios.
- Fixed the display remote issue during the caller call status.
- Fixed the incomplete fill style issue on PC.

## Version 3.1.5 @2023.12.15

### New features

Optimized the timing of accessing device permissions. No longer access device permissions during initialization, only access when using call.

### Bug Fixes

Fixed [@tencentcloud/call-uikit-vue2](https://www.npmjs.com/package/@tencentcloud/call-uikit-vue2),[@tencentcloud/call-uikit-vue2.6](https://www.npmjs.com/package/@tencentcloud/call-uikit-vue2.6) components not having declare file issues.

## Version 3.1.4 @2023.12.01

### New features

Integrated into Chat, added isFromChat reporting.

### Bug Fixes

Fixed the issue where the button is clickable under loading.

## Version 3.1.3 @2023.11.17

### New features

New features parameter validation to the interface.

## Version 3.1.2 @2023.11.03

### New features

- Add the inviteUser feature for inviting others.
- New features the feature to add people mid-call joinInGroupCall.
- Introduced the feature to mute incoming call ringtones enableMuteMode.

### Bug Fixes

Fixed the issue where remote stream microphone status was displayed incorrectly.

## Version 3.1.0 @2023.10.20

### New features

- New features Floating Window feature.
- New features enableFloatWindow interface for enabling/disabling Floating Window feature.
- Desktop Terminal supports switching Camera and Microphone devices.
- New features failure prompt message for calling blocked users.
- New features support for Japanese.

### Feature Optimization

During video calls, the big screen defaults to displaying the remote user.

## Version 3.0.8 @2023.10.10

### New features

New features reporting for version number, framework, and other information.

## Version 3.0.7 @2023.10.08

### New features

Add desktop video call duration display.

### Feature Optimization

- Optimized desktop video stream preview of rounded corners and black edges.
- Optimized display priority for remote stream user information: Remarks > Nickname > userId.
- Optimized TUICallKit component package size (Removed unused images and code).

## Version 3.0.6 @2023.09.19

### Bug Fixes

Fixed the message display issue integrated into TUIKit.

## Version 3.0.5 @2023.09.15

### Feature Optimization

Optimized mutual references in TUICallKit to avoid the stack overflow issue that occurs when packaging mini-programs in uniapp.

### New features

New features a prompt for desktop devices when there is no permission, guiding customers on how to authorize devices.

### Bug Fixes

- Fixed setCallingBell where the called ringtone was overridden by the calling ringtone, leading to ringtone repetition issue.
- Fixed styling issues on mobile devices.

## Version 3.0.4 @2023.09.01

### Bug Fixes

- Fixed setCallingBell targeting incoming call ringtone (called ringtone).
- Fixed destroyed error reporting problem.
- Fixed the lack of Chinese and English in the error popup prompt.
- Fixed the issue where it is impossible to switch between multi-screen support after turning off the camera during a 1v1 call.

## Version 3.0.3 @2023.8.25

### New features

Add [@tencentcloud/call-uikit-vue2.6](https://www.npmjs.com/package/@tencentcloud/call-uikit-vue2.6) compatible with Vue 2.6 version.

### Feature Optimization

- Optimize the default language of the component to the system default language.
- Optimize the log information printed.
- Optimize error message thrown by [tuicall-engine-webrtc](https://www.npmjs.com/package/tuicall-engine-webrtc).
- Optimize resource cleanup after component destruction.

### Bug Fixes

- Fixed an issue where videoDisplayMode,videoResolution did not take effect when calling again after hanging up.
- Fixed the issue where statusChanged was not triggered during the call.
- Fixed the issue of init being called multiple times.
- Fixed the issue of being unable to switch between full and split screens when turning off the camera during a call.

## Version 3.0.2 @2023.8.14

### Bug Fixes

- Fixed styling issues of the called component on the H5 platform.
- Fixed the styling issues that occurred after switching to a small window during another call.

## Version 3.0.1 @2023.8.8

### Bug Fixes

Fixed the issue of the caller's local preview failing during a group call, and modified the component layer's default reading mode from the data layer.

## Version 3.0.0 @2023.8.4

### Breaking Change

Upgraded the underlying dependency [tuicall-engine-webrtc](https://www.npmjs.com/package/tuicall-engine-webrtc) to ^2.0.0. It no longer supports creating tim instances with [tim-js-sdk](https://www.npmjs.com/package/tim-js-sdk). If you need to create a tim instance, please use [@tencentcloud/chat](https://www.npmjs.com/package/@tencentcloud/chat).

### **Add**

Add the custom ringtone feature setCallingBell.

## Version 2.4.2 @2023.11.03

### New features

- Add the inviteUser feature for inviting others.
- New features the feature to add people mid-call joinInGroupCall.
- Introduced the feature to mute incoming call ringtones enableMuteMode.

### Bug Fixes

Fixed the issue where remote stream microphone status was displayed incorrectly.

## Version 2.4.0 @2023.10.20

### New features

- New features Floating Window feature.
- New features enableFloatWindow interface for enabling/disabling Floating Window feature.
- Desktop Terminal supports switching Camera and Microphone devices.
- New features failure prompt message for calling blocked users.
- New features support for Japanese.

### Feature Optimization

During video calls, the big screen defaults to displaying the remote user.

## Version 2.3.9 @2023.10.10

### New features

New features reporting for version number, framework, and other information.

## Version 2.3.8 @2023.10.08

### New features

Add desktop video call duration display.

### Feature Optimization

- Optimized desktop video stream preview of rounded corners and black edges.
- Optimized display priority for remote stream user information: Remarks > Nickname > userId.
- Optimized TUICallKit component package size (Removed unused images and code).

## Version 2.3.6 @2023.09.15

### Feature Optimization

Optimized mutual references in TUICallKit to avoid the stack overflow issue that occurs when packaging mini-programs in uniapp.

### New features

New features a prompt for desktop devices when there is no permission, guiding customers on how to authorize devices.

### Bug Fixes

- Fixed setCallingBell where the called ringtone was overridden by the calling ringtone, leading to ringtone repetition issue.
- Fixed styling issues on mobile devices.

## Version 2.3.5 @2023.9.5

### Bug Fixes

Fixed the issue where the camera and microphone buttons were by default turned on before entering the room.

## Version 2.3.4 @2023.9.1

### New features

Add the feature to disable or enable the camera before answering a video call.

### Bug Fixes

- Fixed the issue where it is impossible to switch screen sizes after turning off the camera during a 1v1 call.
- Fixed the issue where statusChanged was not triggered when switching from a video call to a voice call.

## Version 2.3.3 @2023.8.22

### Bug Fixes

- Fixed an issue where videoDisplayMode,videoResolution did not take effect when calling again after hanging up.
- Fixed the issue where statusChanged was not triggered during the call.

## Version 2.3.2 @2023.7.26

### Breaking Change

- Removed the TUICallKitMini floating window component, merged it into the TUICallKit component.
- The thrown @kicked-out event has been adjusted to the affinity callback `:kickedOut`.
- The thrown @status-changed event has been adjusted to the affinity callback `:statusChanged`.

### **Add**

- Add animation effect when the call page appears.
- Add group call layout on H5.

### Feature Optimization

- Optimize the problem prompt message during the call, prompt method.
- Optimize support on H5 page, interaction.
- Optimize the time it takes to bring up the call interface.
- Optimize the [@tencentcloud/call-uikit-vue](https://www.npmjs.com/package/@tencentcloud/call-uikit-vue) package directory structure.

### Bug Fixes

- Fixed call issues under boundary operations such as immediately hanging up after connecting.
- Fixed styling issues on H5 for some models, browsers.
- Fixed call anomaly issues caused by repeated clicks.

## Version 2.2.1 @2023.7.7

### **Add**

[@tencentcloud/call-uikit-vue2](https://www.npmjs.com/package/@tencentcloud/call-uikit-vue2) Add detection and prompt for the Vue version.

### Bug Fixes

- Fixed the issue where repeatedly clicking the "Answer" button on the incoming call page causes the answer to fail.

## Version 2.2.0 @2023.6.30

### **Add**

- call,groupCall support custom roomID parameter for digital room numbers.
- call,groupCall support custom userData parameter for extended fields (used to add additional information in the invitation signaling).
- Add setSelfInfo interface, supporting user configuration of aliases and profile photos.

## Version 2.1.0 @2023.4.14

### **Add**

- In the H5 voice chat pattern, while calling, it supports displaying the opposite party's nickname.
- When initiating a call fails, "Call initiation failed" will be displayed on the calling page.
- When answering a call fails, "Answer failed" will be shown on the incoming call page.
- Support for monitoring whether the current user is kicked out (e.g., due to being logged out), see TUICallKit Method - @kicked-out.
- Support for listening to TUICallKit call status, see TUICallKit Method - @status-changed.
- Support for business-side code to control the answering, canceling, and hanging up of calls, see More Features - Auto-answer through Interface Setting.
- The Vue2 version adds TypeScript type declaration files, allowing normal compilation of types in TypeScript projects.

### **Bug Fixes**

- Fixed a warning about updating personal profile interface appearing in the console during component initialization.
- Fixed background image misalignment issues of the callee answer button in the H5 pattern.

### **Interface Change**

`TUICallKitServer.destroy()` New features invocation limit, can only be called in non-call status.

## Version 2.0.1 @2023.03.31

### **Add**

- Optimized the rendering logic of 1v1 and group call videos to improve performance and stability.
- Optimized UI presentation, support for displaying corresponding UI during the execution of `TUICallKitServer.call()`, which enables immediate UI display of `<TUICallKit/>` components upon clicking the call button.

### **Bug Fixes**

- Fixed the issue of incorrect nickname display in group calls.
- Fixed the issue of CSS not being scoped properly, leading to global style pollution.

## Version 2.0.0 @2023.03.21

### **Add**

- Support for importing the packaged CallKit file from npm.
- Support for Vue projects in JavaScript version.
- Supports all versions of Vue2 projects, applicable to the npm package for Vue2: [call-uikit-vue2](https://www.npmjs.com/package/@tencentcloud/call-uikit-vue).

### **Bug Fixes**

Fixed the issue where calls could not be initiated due to the absence of a camera device or permission.

## Version 1.4.2 @2023.03.03

### **Add**

- Supports setting call resolution. See API Documentation for details.
- Supports changing the display pattern. See API Documentation for details.
- Optimized the integration steps.
- Optimized error throwing.

## Version 1.4.1 @2023.02.13

### **Add**

- Optimized the logic for previewing the local camera.
- Optimized the rendering logic for remote video streams.

## Version 1.4.0 @2023.01.06

#### **Add**

- Supports importing in Vue2.7+ projects.
- Call interface defaults to displaying nicknames.

## Version 1.3.3 @2022.12.27

#### **Add**

- New features null value detection for the call list when making calls in the Basic Demo.
- New features a loading icon when making calls in the Basic Demo.
- Optimized the logic for device detection in the Basic Demo, no longer proactively popping up after manually skipping.
- Optimized the reference method for component icons.
- Changed the default package management tool to npm.
- Optimized the rendering method for videos, reducing the number of iterative renderings.

#### **Bug Fixes**

Fixed an error in the Basic Demo caused by outdated dependencies in vue-CLI.

## Version 1.3.2 @2022.12.07

#### **Add**

- Language switching is supported, see setLanguage for interface details.
- Optimized the device detection logic in the Basic Demo; it will no longer pop up proactively after being manually skipped.

#### **Bug Fixes**

Fixed a warning caused by introducing `defineProps`.

## Version 1.3.1 @2022.11.29

> **Note:**This version depends on the SDK version [tuicall-engine-webrtc@1.2.1](https://www.npmjs.com/package/tuicall-engine-webrtc), please update promptly.

#### **Add**

- Optimize style details.
- Support monitoring the other party's modification of call type when the call is not answered.
- Basic demo adds device detection feature.

#### **Bug Fixes**

Fixed errors caused by internal logic when hanging up the phone.

## Version 1.3.0 @2022.11.14

#### **Add**

- Supports automatic switching to vertical screen style when using mobile H5.
- Supports previewing the local camera when making a phone call.
- Basic demo adds device detection before making a phone call.

#### **Bug Fixes**

- Fixed the issue where the tim instance did not fully log out after calling TUICallKitServer.destroyed().
- Fixed the problem where a 'No response' message was displayed when the line was busy.
- Fixed the issue where TypeScript types were not successfully packaged in a vite environment.

#### **Interface Change**

When actively calling TUICallKitServer.call() or TUICallKitServer.groupCall(), if an error occurs, the beforeCalling callback will not be invoked. Please use try catch to capture errors directly.

## Version 1.2.0 @2022.11.03

#### **Add**

Adaptation to new versions of TUICallEngine SDK.

## Version 1.1.0 @2022.10.21

#### **Add**

- During a call, the call page can be displayed in full screen.
- During a call, you can use `<TUICallKitMini/>` to minimize.

#### **Bug Fixes**

Fixed known issues, improved stability.

## Version 1.0.3 @2022.10.14

#### **Add**

Basic demo adds quick copy UserID, one-click open new window.

## Version 1.0.2 @2022.09.30

#### **Add**

Optimized access documentation, added demonstration images and detailed guides.

#### **Bug Fixes**

- Fixed the issue where the device status bit became invalid when first entering the room.
- Fixed the occasional failure of Icon loading when packaging with webpack.
- Fixed known styling issues.

## Version 1.0.1 @2022.09.26

#### **Add**

Hide the other party's microphone icon during a phone call.

#### **Bug Fixes**

Fixed the issue where the SDKAppID input box in the basic demo should be numeric.

## Version 1.0.0 @2022.09.23

- Quickly Run Through the TUICallKit Demo
- Quick Integration of TUICallKit
- TUICallKit API
- TUICallKit Customizable Interface Guide
- Frequently Asked Questions About TUICallKit (Web)


---
*Source: [https://trtc.io/document/51019](https://trtc.io/document/51019)*
