# API Reference

AtomicXCore SDK is TRTC's next-generation scenario-based API framework designed for live streaming and voice chat room applications. It enables you to quickly build custom UIs with minimal effort.

The SDK offers comprehensive features including room management, screen sharing, member management, microphone seat control, and built-in beauty filters. Built on top of TRTC, it delivers ultra-low latency and high-quality audio/video experiences.

This page provides a complete reference of all **AtomicXCore SDK** (Android) APIs, organized by feature module.

## LoginStore

User Identity Authentication and Login Management Module

**Core features:** Responsible for user authentication, login status management, user information maintenance and other basic authentication services.

**Responsive data**

| **Data List** | **Description** |
| --- | --- |
| [loginUserInfo](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.login/-login-state/login-user-info.html) | Current logged-in user info. |
| [loginStatus](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.login/-login-state/login-status.html) | Current log-in status. |

**API Function**

| **Function List** | **Description** |
| --- | --- |
| [login](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.login/-login-store/login.html) | Login method. |
| [logout](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.login/-login-store/logout.html) | Logout method. |
| [setSelfInfo](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.login/-login-store/set-self-info.html) | Set user information. |
| [addLoginListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.login/-login-store/add-login-listener.html) | Add login callback event listener. |
| [removeLoginListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.login/-login-store/remove-login-listener.html) | Remove login callback event listener. |

## LiveListStore

Live Streaming List Management Module

- Core Features: Manages the complete lifecycle of live streaming rooms, including creation, joining, leaving, and core business workflows.
- Technical Features:
  - Supports paginated loading, real-time status synchronization, and dynamic live streaming information updates.
  - Implements reactive data management using Kotlin Flow to ensure seamless synchronization between UI and data states.
- Benefits: Provides essential live room management capabilities for live streaming platforms, handles high-concurrency scenarios at scale, and serves as the foundational infrastructure for live streaming services.
- Use Cases: Live stream list display, room creation, live status management, and broadcast analytics.

**Responsive data**

| Data List | Description |
| --- | --- |
| [liveList](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-state/live-list.html) | Live stream list data. |
| [liveListCursor](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-state/live-list-cursor.html) | Live list cursor, used for load by page. |
| [currentLive](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-state/current-live.html) | Current live streaming information. |

**API Function**

| Function List | Description |
| --- | --- |
| [fetchLiveList](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/fetch-live-list.html) | Retrieve the live stream list. |
| [fetchLiveInfo](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/fetch-live-info.html) | Retrieve live room information based on the live streaming room ID. |
| [createLive](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/create-live.html) | Create live streaming room. |
| [joinLive](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/join-live.html) | Join live room. |
| [leaveLive](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/leave-live.html) | Leave the live streaming room. |
| [endLive](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/end-live.html) | End live stream. |
| [updateLiveInfo](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/update-live-info.html) | Update live streaming information. |
| [addLiveListListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/add-live-list-listener.html) | Add live stream list events listener. |
| [removeLiveListListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-list-store/remove-live-list-listener.html) | Remove live stream list event listener. |

## LiveSeatStore

Live Streaming Seat Management Module

- Core Features: Enables seat control in multi-user voice chat scenarios, supporting complex seat state management and audio/video device control.
- Technical Features:
  - Built on WebRTC technology with multi-stream management capabilities
  - Supports seat locking and unlocking
  - Provides audio/video device control
  - Implements role-based permission management
- Benefits: Delivers essential technology infrastructure for interactive live streaming, enabling various engagement scenarios such as co-hosting, anchor battles (PK), and multiplayer interactions.
- Use Cases: Multi-user audio/video interaction scenarios including co-hosting streams, anchor competitions, interactive games, online education, and live conferencing.

**Responsive data**

| Data List | Description |
| --- | --- |
| [seatList](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-state/seat-list.html) | Seat List. |
| [canvas](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-state/canvas.html) | Canvas information. |
| [speakingUsers](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-state/speaking-users.html) | List of users currently speaking. |
| [avStatistics](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-state/av-statistics.html) | Audio/Video stats. |

**API Function**

| Function List | Description |
| --- | --- |
| [takeSeat](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/take-seat.html) | User joins the stage. |
| [leaveSeat](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/leave-seat.html) | User Microphone Dequeuing. |
| [muteMicrophone](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/mute-microphone.html) | Silent microphone. |
| [unmuteMicrophone](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/unmute-microphone.html) | Unmute the microphone. |
| [kickUserOutOfSeat](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/kick-user-out-of-seat.html) | Kick out the user. |
| [moveUserToSeat](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/move-user-to-seat.html) | Move the user to the stage. |
| [lockSeat](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/lock-seat.html) | Lock the seat. |
| [unlockSeat](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/unlock-seat.html) | Unlock the mic. |
| [openRemoteCamera](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/open-remote-camera.html) | Enable the remote user's camera. |
| [closeRemoteCamera](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/close-remote-camera.html) | Turn the remote user's camera off. |
| [openRemoteMicrophone](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/open-remote-microphone.html) | Enable the remote user's microphone. |
| [closeRemoteMicrophone](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/close-remote-microphone.html) | Turn the remote user's microphone off. |
| [addLiveSeatEventListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/add-live-seat-event-listener.html) | Add mic seat event listener. |
| [removeLiveSeatEventListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-seat-store/remove-live-seat-event-listener.html) | Remove mic seat event listener. |

## LiveAudienceStore

Live Streaming Audience Management Module

- Core Features: Manages live room audience lists with permission control, admin configuration, and moderation tools to maintain room order.
- Technical Features:
  - Real-time audience list updates
  - Hierarchical permission management
  - Batch operations support
  - Advanced moderation controls
- Benefits: Delivers comprehensive audience management solutions for live streaming platforms, ensuring smooth moderation at scale.
- Use Cases: Audience list management, permission control, room moderation, and audience interaction management.

**Responsive data**

| Data List | Description |
| --- | --- |
| [audienceList](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-state/audience-list.html) | Live streaming room audience list. |
| [audienceCount](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-state/audience-count.html) | Live streaming room audience size. |
| [messageBannedUserList](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-state/message-banned-user-list.html) | List of muted users. |

**API Function**

| Function List | Description |
| --- | --- |
| [fetchAudienceList](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-store/fetch-audience-list.html) | Retrieve the audience list. |
| [setAdministrator](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-store/set-administrator.html) | Set administrator. |
| [revokeAdministrator](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-store/revoke-administrator.html) | Revoke administrator. |
| [kickUserOutOfRoom](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-store/kick-user-out-of-room.html) | Kick the user out of the room. |
| [disableSendMessage](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-store/disable-send-message.html) | Disable sending messages. |
| [addAudienceListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-store/add-live-audience-listener.html) | Add audience listener. |
| [removeAudienceListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-live-audience-store/remove-live-audience-listener.html) | Remove audience listener. |

## DeviceStore

Device Status Management Module

- Core Features: Manage control of cameras, microphones and other audio/video devices, provide device status monitoring, permission check and other basic device services.
- Technical Features: Support advanced functions such as multi-device management, real-time status monitoring, dynamic permission check, and automatic failure recovery.
- Benefits: Provide stability to the device base for the live streaming system, underwrite reliability of audio and video capture and user experience.
- Use Cases: Basic technical scenarios such as device management, permission control, audio and video capture, and device failure handling.

**Responsive data**

| Data List | Description |
| --- | --- |
| [microphoneStatus](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/microphone-status.html) | Microphone on status. |
| [microphoneLastError](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/microphone-last-error.html) | Microphone last error status. |
| [captureVolume](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/capture-volume.html) | Audio Capturing volume (0-100). |
| [currentMicVolume](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/current-mic-volume.html) | Current microphone volume (0-100). |
| [outputVolume](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/output-volume.html) | Audio output volume (0-100). |
| [cameraStatus](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/camera-status.html) | Camera on status. |
| [cameraLastError](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/camera-last-error.html) | Camera last error status. |
| [isFrontCamera](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/is-front-camera.html) | Whether the camera is front-facing. |
| [localMirrorType](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/local-mirror-type.html) | Local image type. |
| [localVideoQuality](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/local-video-quality.html) | Local video quality settings. |
| [currentAudioRoute](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/current-audio-route.html) | Current audio output route (speaker/headphone). |
| [screenStatus](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/screen-status.html) | Screen sharing status. |
| [networkInfo](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-state/network-info.html) | Network information status. |

**API Function**

| Function List | Description |
| --- | --- |
| [openLocalMicrophone](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/open-local-microphone.html) | Open local microphone. |
| [closeLocalMicrophone](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/close-local-microphone.html) | Close local microphone. |
| [setCaptureVolume](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/set-capture-volume.html) | Set the capture volume. |
| [setOutputVolume](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/set-output-volume.html) | Set the output volume. |
| [setAudioRoute](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/set-audio-route.html) | Set audio output routing. |
| [startCameraTest](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/start-camera-test.html) | Preview the front camera, the video preview will be rendered on the cameraView parameter. |
| [stopCameraTest](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/stop-camera-test.html) | Stop camera preview. |
| [openLocalCamera](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/open-local-camera.html) | Turn on local camera. |
| [closeLocalCamera](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/close-local-camera.html) | Turn off local camera. |
| [switchCamera](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/switch-camera.html) | Switch camera. true: front camera, false: rear camera. |
| [switchMirror](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/switch-mirror.html) | Set camera mirror. |
| [updateVideoQuality](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/update-video-quality.html) | Set streaming resolution. |
| [startScreenShare](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/start-screen-share.html) | Enable screen sharing. |
| [stopScreenShare](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-device-store/stop-screen-share.html) | Disable screen sharing. |

## CoGuestStore

Guest Management Module

- Core Features: Manages interactive co-hosting between audience members and anchors, handling the complete workflow of mic requests, invitations, acceptances, and rejections.
- Technical Features:
  - Built on real-time audio/video technology
  - Real-time co-hosting status synchronization
  - Adaptive audio/video quality adjustment based on network conditions
  - Network quality monitoring and optimization
- Benefits: Enables audience participation and engagement on live streaming platforms, increasing user retention and enhancing stream interactivity.
- Use Cases: Interactive scenarios such as audience co-hosting, live Q&A sessions, online karaoke, and gaming streams.

**Responsive data**

| Data List | Description |
| --- | --- |
| [connected](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-state/connected.html) | Connected guest list. |
| [invitees](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-state/invitees.html) | List of users invited to speak. |
| [applicants](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-state/applicants.html) | List of users requesting to speak. |
| [candidates](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-state/candidates.html) | List of candidate users available for invitation to speak. |

**API Function**

| Function List | Description |
| --- | --- |
| [applyForSeat](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/apply-for-seat.html) | Apply for a mic-connection seat. |
| [cancelApplication](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/cancel-application.html) | Cancel the application. |
| [acceptApplication](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/accept-application.html) | Accept application. |
| [rejectApplication](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/reject-application.html) | Reject application. |
| [inviteToSeat](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/invite-to-seat.html) | Invitation to speak. |
| [cancelInvitation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/cancel-invitation.html) | Cancel invitation. |
| [acceptInvitation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/accept-invitation.html) | Accept invitation. |
| [rejectInvitation](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/reject-invitation.html) | Reject invitation. |
| [disconnect](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/disconnect.html) | Disconnect. |
| [addGuestListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/add-guest-listener.html) | Add guest-side event listener for co-streaming. |
| [removeGuestListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/remove-guest-listener.html) | Remove guest-side event listener for co-streaming. |
| [addHostListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/add-host-listener.html) | Add Anchor-side event listener for co-streaming. |
| [removeHostListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-guest-store/remove-host-listener.html) | Remove Anchor-side event listener for co-streaming. |

## **CoHostStore**

Co-hosting Management Module

- Core Features: Enables real-time collaboration between anchors, supporting invitations, connection requests, status management, and interactive workflows.
- Technical Features:
  - Multi-anchor audio/video synchronization
  - Picture-in-Picture (PiP) display
  - Adaptive audio/video quality optimization
  - Low-latency stream coordination
- Benefits: Delivers essential infrastructure for anchor collaboration on live streaming platforms, powering advanced engagement scenarios such as anchor battles and co-streaming.
- Use Cases: Advanced streaming scenarios including anchor competitions (PK), co-streaming, cross-platform collaboration, and multi-anchor interactions.

**Responsive data**

| Data List | Description |
| --- | --- |
| [connected](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-state/connected.html) | Connected Anchor list. |
| [invitees](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-state/invitees.html) | Invited Anchor list. |
| [applicant](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-state/applicant.html) | Currently applied Anchor information for connecting line. |
| [coHostStatus](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-state/co-host-status.html) | Current connection status. |

**API Function**

| Function List | Description |
| --- | --- |
| [requestHostConnection](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/request-host-connection.html) | Request connection. |
| [cancelHostConnection](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/cancel-host-connection.html) | Cancel the connection request. |
| [acceptHostConnection](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/accept-host-connection.html) | Accept the connection request. |
| [rejectHostConnection](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/reject-host-connection.html) | Reject connection request. |
| [exitHostConnection](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/exit-host-connection.html) | Exit connection. |
| [addCoHostListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/add-co-host-listener.html) | Add event listener for connected host. |
| [removeCoHostListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-co-host-store/remove-co-host-listener.html) | Remove event listener for connected host. |

## AudioEffectStore

Audio Processing Module

- Core Features: Offer advanced sound effect functions such as voice-changing, reverb, and ear monitoring, support various audio effects and real-time sound effect adjustment.
- Technical Features: Support advanced technologies like real-time audio processing, low delay audio transmission, and sound quality optimization.
- BusinessValue: Provide differentiated audio experience for live streaming platforms, enhance user engagement and live stream fun.
- Use Cases: Scenarios requiring audio processing, such as voice-changing live stream, karaoke live stream, sound effects entertainment, and professional audio effects.

**Responsive data**

| Data List | Description |
| --- | --- |
| [isEarMonitorOpened](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-state/is-ear-monitor-opened.html) | Toggle status |
| [earMonitorVolume](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-state/ear-monitor-volume.html) | Volume of IEMs. |
| [audioChangerType](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-state/audio-changer-type.html) | Voice-changing status. |
| [audioReverbType](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-state/audio-reverb-type.html) | Reverberation status. |

**API Function**

| Function List | Description |
| --- | --- |
| [setAudioChangerType](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-store/set-audio-changer-type.html) | Set the voice changing effect. |
| [setAudioReverbType](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-store/set-audio-reverb-type.html) | Set the reverb effect. |
| [setVoiceEarMonitorEnable](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-store/set-voice-ear-monitor-enable.html) | Set the toggle status. |
| [setVoiceEarMonitorVolume](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-audio-effect-store/set-voice-ear-monitor-volume.html) | Set the volume of IEMs. |

## BarrageStore

Live Comments and Messaging Module

- Core Features: Handles text messages, custom messages, and live comments in streaming rooms, supporting message sending, status synchronization, and a complete commenting system.
- Technical Features:
  - High-concurrency message processing
  - Real-time message synchronization
  - Message filtering and moderation
  - Emoji and sticker support
  - Custom message formats
- Benefits: Delivers essential interactive capabilities for live streaming platforms, boosting user engagement and fostering community interaction.
- Use Cases: Live comments, chat management, emoji and sticker interactions, and in-stream messaging.

**Responsive data**

| Data List | Description |
| --- | --- |
| [messageList](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.barrage/-barrage-state/message-list.html) | Bullet screen messages of the current room. |

**API Function**

| Function List | Description |
| --- | --- |
| [sendTextMessage](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.barrage/-barrage-store/send-text-message.html) | Send text type bullet screen. |
| [sendCustomMessage](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.barrage/-barrage-store/send-custom-message.html) | Send custom type bullet screen. |

## BaseBeautyStore

Basic Beauty Filter Module

- Core Features: Provide basic beauty effects such as skin smoothing, whitening, and rosy skin, supporting real-time beautification parameter adjustment.
- Technical Features: Support advanced technologies such as real-time beautification processing, smooth parameter adjustment, and performance optimization.
- Benefits: Provide basic beauty effect capability for live streaming platforms to enhance user image and streaming quality.
- Use Cases: Live streams, image optimization, beauty adjustment, and beautification in scenarios where smart beautification capabilities are required.

**Responsive data**

| Data List | Description |
| --- | --- |
| [smoothLevel](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-base-beauty-state/smooth-level.html) | Smoothing level value ranges from 0 to 9: 0 means disabling, 9 indicates the most obvious effect. |
| [whitenessLevel](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-base-beauty-state/whiteness-level.html) | Whiteness level value ranges from 0 to 9: 0 means disabling, 9 indicates the most clear effect. |
| [ruddyLevel](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-base-beauty-state/ruddy-level.html) | Rosy level value ranges from 0 to 9: 0 means disabling, 9 indicates the most clear effect. |

**API Function**

| Function List | Description |
| --- | --- |
| [setSmoothLevel](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-base-beauty-store/set-smooth-level.html) | Set the skin smoothing level. |
| [setWhitenessLevel](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-base-beauty-store/set-whiteness-level.html) | Set the whitening level. |
| [setRuddyLevel](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.device/-base-beauty-store/set-ruddy-level.html) | Set the rosy level. |

## GiftStore

Gift System Management Module

- Core Features: Manages gift sending, receiving, and inventory, supporting gift categorization, animations, statistics, and a complete virtual gifting economy.
- Technical Features:
  - Gift animation rendering and effects
  - Real-time gift statistics and tracking
  - Leaderboard and ranking system
  - Multi-tier gift categorization
  - Transaction history management
- Benefits: Enables core monetization capabilities for live streaming platforms, supporting virtual economy and revenue generation.
- Use Cases: Virtual gifting, in-app purchases, animated gift effects, gift leaderboards, and revenue analytics.

**Responsive data**

| Data List | Description |
| --- | --- |
| [usableGifts](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.gift/-gift-state/usable-gifts.html) | Gift list availability. |

**API Function**

| Function List | Description |
| --- | --- |
| [refreshUsableGifts](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.gift/-gift-store/refresh-usable-gifts.html) | Refresh the available gift list. |
| [sendGift](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.gift/-gift-store/send-gift.html) | Send a gift. |
| [addGiftListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.gift/-gift-store/add-gift-listener.html) | Add gift event listener. |
| [removeGiftListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.gift/-gift-store/remove-gift-listener.html) | Remove gift event listener. |

## LikeStore

Like Interaction Module

- Core Features: Manages like interactions in streaming rooms, supporting like sending, statistics tracking, event monitoring, and engagement metrics.
- Technical Features:
  - High-concurrency like processing
  - Real-time like statistics and aggregation
  - Animated like effects and visual feedback
  - Popularity leaderboards and rankings
  - Batch like event handling
- Benefits: Enables basic engagement features for live streaming platforms, driving user interaction and community participation.
- Use Cases: Like interactions, popularity metrics, engagement tracking, and audience sentiment analysis.

**Responsive data**

| Data List | Description |
| --- | --- |
| [totalLikeCount](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-like-state/total-like-count.html) | Total number of likes. |

**API Function**

| Function List | Description |
| --- | --- |
| [sendLike](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-like-store/send-like.html) | Send a like. |
| [addLikeListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-like-store/add-like-listener.html) | Add event listener for like. |
| [removeLikeListener](https://tencent-rtc.github.io/TUIKit_Android/-atomic-x%20-core%20-a-p-i/io.trtc.tuikit.atomicxcore.api.live/-like-store/remove-like-listener.html) | Remove event listener for like. |


---
*Source: [https://trtc.io/document/66146](https://trtc.io/document/66146)*
