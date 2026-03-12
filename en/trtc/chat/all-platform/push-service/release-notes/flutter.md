# Flutter

### 8.8.7357 @2025.12.05

- Optimize the reporting logic for reach.
- Optimize the update logic for badges.
- Upgrade the Honor and vivo push packages.
- Support Push online message click report.
- Optimize the registration push logic.

### 8.7.7201 @2025.09.08

- Support OPPO Private Message Channel push template.
- Support FCM message priority setting.
- Support vivo notification type setting.
- Optimize OPPO registration push success rate.
- Support Apple LiveCommunicationKit feature.
- Optimize iOS multi-product set didReceiveRemoteNotification conflict issue
- Remove glide dependency package and optimize large image notification display function.
- Optimize error code parsing logic.

### 8.6.7019 @2025.05.29

- Support push messages adapted to device system languages.
- Support Meizu message categorization.
- Optimize the logic for applying for notification permissions.
- Resolve the initialization failure issue caused by lazy loading providers on some devices.
- Resolve the potential concurrency issue in token retrieval.
- Optimize the default value of strong reminders for C-end OPPO.
- Optimize the thread safety logic of iOS addPushListener.
- Solve the login issue in push registration notifications.

### 8.5.6864 @2025.03.31

- Support push capability for specified device ID.
- Support automatic adaptation feature for overseas FCM channel.
- Optimize the unregistration logic in hybrid mode.
- Optimization of iOS foreground or background status concurrency issue.
- Optimization of iOS notification bar callback closure issue.
- Optimization of Push error codes.

### 8.4.6667+3 @2025.02.24

- Optimize the message receiving logic to solve the problem that may cause OOM.

### 8.4.6667 @2025.01.16

- Optimize the logic for unregister push.
- Support honor offline message categorization.
- Add offline storage feature for Push messages.
- Optimize the offline handling logic for roaming messages.

### 8.3.6498+2 @2024.12.27

- Optimize FCM VOIP logic.
- Optimize the push notification registration logic to not strongly depend on stack verification.

### 8.3.6498+1 @2024.11.27

- Supports OPPO push message classification new regulations.
- Added notification bar click event listening method onNotificationClicked.
- Supports custom ringtones for frontend online channel.
- Resolved database concurrency issue.
- Resolved login concurrency issue.
- Resolve the issue of direct jump interface upon receiving foreground push.
- Resolve the issue of multiple call failures on Xiaomi, upgrade Xiaomi push package.
- Optimize registerPush logic to support calling with appKey parameter after login.
- Optimize Huawei model recognition.
- Mixed mode disables foreground push by default.
- Deprecated some APIs, it is recommended to stop using them and switch to other APIs.
- Deprecated the iOS push certificate ID setting field offlinePushCertificateID, please use businessID.

### 8.2.6325 @2024.09.29

- Added support for non-landing push message feature.
- FCM supports custom redirect on notification bar click.
- Optimized log print feature before registration for push notifications.
- Fixed the issue where iOS Donut platform does not callback on cold startup notification bar click.

### 8.1.6907 @2024.09.06

- Resolved Push user login type error issue.
- Resolved APNs push issue due to agency failure.
- Optimized APNs offline transmission message Ext empty callback click event issue.
- Resolved APNs foreground status resolution notification exception callback issue.
- Optimized FCM data empty message pop-up window issue.
- Optimize the full platform type setting logic.
- Add a global callback interface for Push.

### 8.1.6107 @2024.08.06

- Add login-free push notification feature.
- The intelligent detection available channels policy is disabled by default, add a configuration switch.
- Resolve the automated detection task rotation issue.
- Optimize confusion settings.


---
*Source: [https://trtc.io/document/67544](https://trtc.io/document/67544)*
