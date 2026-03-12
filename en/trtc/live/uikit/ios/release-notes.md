# Release Notes

## August 2025

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 3.3.0 | New Features**Multi-Template Video Mixing:** We've added multi-template support across all platforms. Viewers can now get the media and pending status of the mic seats and the hosts on stage.**Experimental Picture-in-Picture API:** A new Picture-in-Picture API is now available for developers to try out.**Flutter Platform Features:**All live room list plugin APIs have been added.Full gift functionality is now available.**Web Platform Features:**The video stream preview API has been added.Live PK-related APIs have been added.Optimizations and Improvements**Video Encoding Optimization:** We've optimized upstream video encoding for different video mixing templates, improving video quality and performance.**API Annotation Optimization:** We've optimized the annotations for some APIs to make our documentation clearer and easier to understand.Bug FixesFixed a black screen issue caused by unsupported video mixing capabilities.Fixed an issue where the rendering view would show as black when a single stream had no video.Fixed an issue with abnormal room entry status after a multi-device kick-out on the same account.Fixed an issue where media status was not reported in a timely manner after a new room joined a cross-room connection.Fixed an issue with abnormal video status during placeholder streaming.**Android Platform:** Fixed an issue with abnormal modify_flag callbacks after TUILiveInfo field changes.**iOS Platform:** Fixed an issue where the TUILiveInfo field was not displayed correctly.**Web Platform:**Fixed an issue where the video player would fail to play.Fixed a setLiveInfo API call failure caused by incompatibility with the basicRoomInfo field.**Flutter Platform:** Fixed an issue where calls and foreground/background status could not be accurately monitored due to a thread-related problem. | 2025.08.22 |

## July 2025

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 3.2.0 | **TUILiveKit Change Log**Page Component Module RefreshTargeting iOS and Android Dual-Platform, Completing Independent Split of Live Stream Core WebpageSplit into five core webpage components: **preparation page**, **live page**, **live stream list**, **viewing page**, and **data statistics**.Support developers to flexibly access on demand based on business needs, reduce integration cost, and enhance customized development efficiency.Gift Function Deep Upgrade (RTCRoomEngine Integration)Newly Upgraded Gift Function System, covering data statistics, notification stability, and internationalization capability:Improved data statistics accuracy: gift-related data syncs in real time with more complete statistical dimensions.Optimized notification mechanism: enhanced stability of gift message push to reduce missed or latency issues.Internationalization support: adapts to multiple language scenarios, with localized configuration for gift names and reminders.Open capability expansion: provides the TUILiveGiftManager API, supporting business customization through various RestAPIs and third-party callbacks (see the API document). RTCRoomEngine **Change Log**Live Stream Management API ExpansionNewly-added core APIs for TUILiveListManager management class: startLive (create live stream), stopLive (end live stream), joinLive (join live stream), leaveLive (log out live stream), covering full lifecycle management of live rooms.Enhanced Closed Data Loop: When calling the stopLive API, it now returns key stats such as **viewing count**, **total amount of gifts**, and **number of likes**, supporting rapid generation of live stream reports.Resolution dynamic perception: Newly-added OnUserVideoSizeChanged callback event provides real-time notifications to the client about anchor resolution adjustment, optimizing screen display experience.Stability and Compliance ReinforcementNewly-added license invalidation error code (-1005): When triggered, video playback will be restricted. The App should check license validity immediately.Android decoder pre-launch optimization: Preloading decoder resources significantly shortens audio and video first frame playback duration (faster startup experience).Enhanced setLocalVideoMuteImage API: Supports clearing padding images to accommodate business scenarios without custom placeholder images.Core Link Performance TuningMix stream logic optimization: Adjust the stream push policy and resource scheduling algorithm to reduce mix stream delay and enhance video smoothness.QoS adaptive encoding upgrade: Dynamically adjust encoding parameters (bitrate/resolution) based on network status to balance video quality and smoothness.Optimize the getUserList API: Decrease backend request frequency, avoid client-side rate limiting risks, and guarantee list pull stability.Multi-Scenario Experience CompatibilityLive stream and CallKit call mixed use support: Allow answering CallKit inbound calls during live streaming, automatically recover live status after call ends, avoid interruption.Multi-person live stream canvas filling mode optimization: Support customizable cropping/scaling policies, adapt to screens with different ratios, reduce black borders/deformation issues.Optimize live stream list rate limit policy: Optimize getRoomInfo API pull logic, dynamically adjust request frequency, reduce probability of triggering server rate limit. Web Capability Extension and FixAdding New Core APILive connection feature: Support initiating/answering live streaming mic connection on Web, improve multi-person interactive scene.Message sending ability completion: Open sendTextMessage (text message) and sendCustomMessage (custom message) APIs to support business message passthrough.Room metadata management: Add roomMetadata-related APIs to support setting custom room information (such as background image, notice).Key Issue FixingLive stream interruption recovery exception: Fix the issue where the viewer side experiences continuous black screen unable to recover after interruption due to network/device problems.Mic mute display issue: Fix the status icon inconsistency between mute and actual state in voice chat room scenarios.Web playback black screen: Address the occasional black screen issue during TRTC stream mixing in browser.getUserList serial number anomaly: Fix the issue of sequence field confusion in API calls on the Web. | 2025.7.16 |

## June 2025

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 3.1.0 | **TUILiveKit**New featureAndroid & iOS: Add a new component, the waterfall list component.  Android & iOS: Add a new component, the host preparation page component.Feature enhance  Live stream createRoom supports setting the host to remain on the mic after taking the mic.  Live stream / audience end interface adds a gradient color overlay.Process optimization  Optimize the display logic of the audience list.  Optimize the data flow for fetching room information when entering a room.Bug fixesiOS: Optimize the UI abnormal issue of the connection feature in offline state.  iOS: Fix the room status exception issue caused by the abnormal exit UI. iOS: Fix the UI abnormality/black screen issue of the mic position request in a weak network environment.  iOS: Fix the incomplete display issue of the voice chat room UI on iPhone 7.Android: Fix the occasional inconsistency issue between the audience size and the list.  Android: Fix the abnormal icon display issue for PK.**RTCRoomEngine SDK**Bug fixesAdjust the loading timing of the client's capability bit to ensure the capability bit is loaded before the RoomEngine callback succeeds.  Add message API, supports the use of RoomEngine to receive IM messages, and supports ignoring muting.  Fix the issue where entering the room fails after TRTC room entry returns a result of 0.  Add user profile mapping to SSO channel notifications to reduce the concurrent completion of user information by the SDK and alleviate the pressure on the backend. Add cloud control configuration change callback to provide timely updates for the configuration center and rate-limiting parameters.  Set the client bitrate cap, aligned with the official website.  Fix the issue where accounts cannot log in when RoomEngine and TIMPush are mixed.**LiveStreamCore**API change   Adding stream push APIFeature optimization  createRoom adds the `keepOwnerOnSeat` field, supporting the room owner staying on mic permanently.  `OnUserNetworkQualityChanged` callback adds local network quality detection during audience streaming.  `onKickedOutOfRoom` callback adds the reason for being kicked out.  Optimize the synchronization strategy for the mute list and administrator list, reduce the frequency of background requests.  Optimize the sync logic for the state of live connections, reduce the frequency of background requests.  Optimize the preview pull stream logic when the audience has not entered the room.Bug fixes  Fix the issue where the error code fails to return correctly when the user has not entered the room.  Fix the issue where the local layout notification record is not cleared after going on mic, causing the layout to stop being called back when pulling the mixed stream after going off mic.  Fix the issue where the parameter is invalid when checking out repeatedly.  Fix the black screen issue caused by the failure to synchronize microphone position information in a timely manner after an abnormal network response.  Fix the issue where audio and video are still missing after being blacklisted and banned, even though they load instantly upon reconnection.  Fix the issue where the local user fails to disable collection promptly after going off-mic due to an anomaly resolved in the network.  Fix the issue where TUIUserInfo is inaccurate in the `onRequestTimeout` callback under network exception conditions. | 2025.06.10 |

## April 2025

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 3.0.0 | **TUILiveKit**Flutter: New voice chat room scenarioFlutter: Unified internationalization copywritingFlutter: Fix known issuesiOS&Android: Fixed authentication issues with advanced effects playeriOS: advanced beauty effects now support historical presetsiOS&Android: Added live room user management (mute, kick, remove from stage, AV ban, etc.)iOS&Android: Removed incomplete features (user level, music playback, live streaming types)iOS&Android: Fixed abnormal room behavior caused by frequent giftingiOS&Android: Unified internationalization copywritingiOS: iOS live list information now supports customizationAndroid: Optimized compatibility issues with specific Android modelsiOS&Android: Audience automatically leaves stage when entering room via co-streamingiOS&Android: Fixed known issues**LiveStreamCore**Flutter: newly-added voice chat componentiOS: Release of static libraryiOS&Android: The status is accessible and changes can be subscribed to.iOS&Android: Add APIs switchCamera & enableMirroriOS&Android: Unify internationalization copywritingiOS&Android: Fix known issues**RoomEngine SDK**New FeaturesAdded fuzzy member search support for live streaming roomsAdded custom layout interface in LayoutManagerAdded screen sharing pause interfaceCompleted live list interface for WebAdded room metadata interface for WebAPI changeError code updatesAdded mute field to userInfo parameter in OnRemoteUserEnterRoom/OnRemoteUserLeaveRoomSwift API declaration changes for mute APIs on iOSFix issuesOptimized screen sharing exceptionsFixed occasional crashes on AndroidFixed potential microphone activation failure after entering room | 2025.04.03 |

## February 2025

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 2.9.0 | **TUILiveKit**New features:Android&iOS: VideoLiveKit API adds: disable follow feature, end and exit live streaming roomAndroid&iOS: Floating window support on the streamer sideBug fixes: Android&iOS: Fixed some known issues**RoomEngine SDK**Flutter: Added support for connecting lines and PK featureAll Platforms: Optimization of `onRoomUserCountChanged` Callback | 2025.02.12 |

## December 2024

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 2.8.0 | New featureLiveKit supports large rooms with tens of thousands of participantsStability:iOS: Improved the stability of the bullet screen componentBug fixes: Android&iOS: Fixed some known issues | 2024.12.18 |

## November 2024

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 2.4.3 | New featureAdded LiveCoreView componentSupports floating window feature | 2024.11.20 |

## October 2024

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 2.4.2 | New featureAdded VideoLiveKit and VoiceRoomKit interface. | 2024.10.12 |

## August 2024

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 2.4.1 | New featureNew Live Connection feature | 2024.08.29 |

## July 2024

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 2.1.0 | New featureAndroid&iOS: Demonstration Interaction upgrade.Bug fixesAndroid&iOS: Fixed some runtime crashes. | 2024.07.22 |

## June 2024

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 2.0.0 | New featureAndroid&iOS: UI2.0 Interactive Update.Android&iOS: Support for Room List.Android: Supports swipe to switch live rooms. | 2024.06.26 |

## May 2024

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 1.0.1 | New featureAndroid&iOS: Supports voice chat room scenario.Android&iOS: Supports host sending barrage.Bug fixesAndroid: Fixes microphone connection issue and dashboard display issue.Android: Fixes microphone status issue when seat locking. | 2024.05.24 |

## April 2024

| Post updates | Description | Release Date |
| --- | --- | --- |
| Version 1.0.0 | New featureAndroid&iOS: Supports hosts to start broadcasting.Android&iOS: Supports audience entering the live streaming room.Android&iOS: Supports audience microphone connection.Android&iOS: Supports audience list.Android&iOS: Supports barrage component.Android&iOS: Supports the Gift Component. | 2024.04.22 |


---
*Source: [https://trtc.io/document/67291](https://trtc.io/document/67291)*
