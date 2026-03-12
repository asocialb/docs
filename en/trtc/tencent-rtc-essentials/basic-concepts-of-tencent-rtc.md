# Basic concepts of Tencent RTC

This document explains some of the basic concepts you may encounter while using Tencent RTC services.

### Application

Tencent RTC's Call, Conference, Live, RTC Engine, and Chat products manage different businesses or projects through the use of **applications**. You can create different applications for your projects in the [Tencent RTC console](https://console.trtc.io/) to separate their data. For details, please refer to the [application creation tutorial](https://www.tencentcloud.com/document/product/647/39077).

### SDKAppID

Tencent Cloud uses `SDKAppID` (application ID) to uniquely identify TRTC applications. It is generated automatically when you create an application in the [Tencent RTC console](https://console.trtc.io/). Applications that do not have the same `SDKAppID` cannot communicate data with each other.

### SDKSecretKey

`SDKSecretKey` is the encryption key paired with `SDKAppID`, used to generate the user authentication token UserSig. It ensures the legitimacy and security of service calls and is automatically generated when creating an application in the [Tencent RTC console](https://console.trtc.io/).

### UserID

UserID (user ID) uniquely identifies a user in a TRTC application.

- `UserID` is a mapping of the user accounts of your project in Tencent Cloud. Normally, you can use a username as `UserID`.
- `UserID` should preferably be 32 bytes or shorter. It can contain digits, underscores, and letters (case sensitive).

### TUICallKitãCallEngine

- TUICallKit: A real-time call component with **a complete UI**launched by Tencent Cloud, also known as the Call product. It provides pre-built audio and video call UI components, supporting 1v1 calls, group calls, custom ringtones, floating windows, and other features, enabling quick integration into applications.
- CallEngine:  A **no-UI** underlying audio and video call engine. Developers can fully customize the call interaction interface based on this API. It serves as the fundamental dependency for UI components (TUICallkit) and supports more complex call feature customization.

### TUIRoomKitãTUILiveKitãRoomEngine

- TUIRoomKit: A multi-person audio and video real-time meeting component with **a complete UI**launched by Tencent Cloud, also known as the Conference product. It offers out-of-the-box features such as room management, screen sharing, member control, and in-meeting chat. It supports rapid integration across multiple platforms.
- TUILiveKit: A real-time interactive live streaming component with **a complete UI**launched by Tencent Cloud, also known as the Live product. It offers core live room components, supporting going live, muti-guest, anchor connection and battle, chat in live room, gifts, audience management and more, and can be quickly integrated into application.
- RoomEngine: A **no-UI** underlying audio and video room engine. It serves as the fundamental dependency for UI components (TUIRoomKit and TUILiveKit) and supports customization of more advanced conference and live streaming features.

### MAU

MAU (Monthly Active Users) refers to the total number of unique users who use Chat features (such as sending/receiving messages, group management) each month. Besides the Chat product, the Live, Call, and Conference products also generate MAU during usage. Different package versions correspond to different free quotas; exceeding the quota requires upgrading or payment.

### License

An authorization credential used to activate Tencent Effects SDKs (such as the Beauty AR product), containing information like service validity period and package version.

- Official License: Generated after purchasing a beauty package in the [Tencent RTC Console](https://console.trtc.io/subscription/buy/beauty), dynamically obtained via LicenseUrl (authorization file download link) and LicenseKey (authorization key).
- Trial  License: In some scenarios (e.g., local debugging), a temporary file (such as v_cube.license) can be configured, but the first network authentication must succeed.

### License Key

Authorization key: Used together with LicenseUrl to verify the legitimacy of the authorization file. Storing it in plaintext on the frontend is prohibited; in production environments, it must be dynamically obtained via server-side APIs.

### License Token

Signature key: Used to generate temporary signatures (Signature) to verify the legitimacy of frontend requests. The Token must be migrated to the server side, and signatures should be obtained through APIs to avoid leakage risks.

### Room

A room is a space where users can receive each otherâs audio and video data in real time.

- Rooms are virtual spaces TRTC uses to separate one user group from another.
- Only users in the same room can receive each otherâs audio and video.
- A user can be in only one room at a time. A user who is already in a room must exit the room before they can enter another.

> **Note:**The first user who enters a room is the owner of the room. Room owners cannot close rooms manually.In call modes, TRTC closes a room when all users leave the room.In live streaming modes, if the last user who exits a room is an anchor, TRTC will close the room immediately; if the user is an audience member, TRTC will close the room after 10 minutes.A user is removed from a room 90 seconds after an unexpected disconnection occurs. If all users are disconnected, the room is closed after 90 seconds. **The waiting time after a disconnection occurs is also billed**.If a user attempts to enter a room that does not exist, TRTC creates a room automatically.

### Room ID

`RoomID` (room number/ID) uniquely identifies a room in a Tencent RTC application. It is a UInt32 number that you assign to a room and maintain. Its value range is 1-4294967295.

### UserSig

`UserSig` (user signature) is a security signature designed by Tencent Cloud to authenticate user logins and verify that a user is real. It helps prevent attackers from accessing your Tencent Cloud account. For more information, see [UserSig Generation](https://www.tencentcloud.com/document/product/647/35166).

### Push

Push is the operation in which a user uploads local audio/video data to the Tencent RTC server.

### Subscription

Subscription is the operation in which a user sends a request to the Tencent RTC server to pull the audio/video data of a specified user.

### Role

In Tencent RTC, users can have either of two roles: **anchor** (`TRTCRoleAnchor`) and **audience** (`TRTCRoleAudience`).

- An anchor can push local audio/video data to the server. They can also subscribe to and play back the audio/video data of other anchors.
- Audience members **can only** subscribe to and play back the audio/video data of anchors.

In call modes, all users in a room have the anchor role. In live streaming modes, users in a room can be either anchors or audience memebers. A user can switch roles as needed.

### CDN Live Watching

CDN live watching is also known as CDN relayed live streaming. Tencent RTC uses relayed transcoding clusters to convert its UDP audio/video streams into RTMP streams in the cloud. The streams are then pushed to a standard live streaming system and distributed through CDNs to the audience. For details, see [Relay to CDN](https://www.tencentcloud.com/document/product/647/47858#).

### On-cloud recording

Tencent RTC leverages the capabilities of [CSS](https://intl.cloud.tencent.com/document/product/267) to record entire audio/video calls in the cloud. Recording files are securely saved in real time to [VOD](https://intl.cloud.tencent.com/document/product/266). For details, see [On-Cloud Recording](https://www.tencentcloud.com/document/product/647/45169#).

### On-Cloud MixTranscoding

In scenarios such as **CDN live watching** and **on-cloud recording**, you may need to mix multiple audio/video streams in a Tencent RTC room into one stream. This can be achieved using Tencent RTCâs stream mixing and transcoding MCU cluster. The MCU cluster can mix multiple audio/video streams as needed and distribute the mixed stream to live streaming CDNs and the on-cloud recording system. For details, see [Relay to CDN](https://www.tencentcloud.com/document/product/647/47858#).

### Dumb terminal

A user entering a room on a dumb terminal will not be detected by the SDK, and remote users will not receive notifications when the user enters or exits the room.


---
*Source: [https://trtc.io/document/69909](https://trtc.io/document/69909)*
