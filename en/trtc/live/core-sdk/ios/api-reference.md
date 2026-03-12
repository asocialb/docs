# API Reference

**AtomicXCore SDK** is the next-generation reactive API from **TRTC**, purpose-built for live streaming, and voice chat rooms. This API suite enables rapid UI development and supports comprehensive features including room management, member management, seat control, basic beauty effects, and more. Built on the TRTC SDK, AtomicXCore delivers ultra-low latency and high-quality audio and video experiences. This page provides a complete reference for all **AtomicXCore SDK API**interfaces, organized by functional module.

## LoginStore

**User Authentication and Login Management**

**Core Features:** Provide user authentication, manages login state, maintains user profiles, and delivers essential authentication services.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [loginUserInfo](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/loginstate/loginuserinfo) | Information about the currently logged-in user. |
| [loginStatus](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/loginstate/loginstatus) | Current login status. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [login(sdkAppID:userID:userSig:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/loginstore/login(sdkappid:userid:usersig:completion:)) | Authenticate and log in a user. |
| [logout(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/loginstore/logout(completion:)) | Log out the current user. |
| [setSelfInfo(userProfile:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/loginstore/setselfinfo(userprofile:completion:)) | Update the user's profile information. |

## LiveListStore

**Live Room List Management**

- **Core Features**: Manage the complete lifecycle of live rooms, including creation, joining, leaving, and ending, covering all core business processes.
- **Technical Highlights**: Support paginated loading, real-time status synchronization, dynamic live info updates, and uses reactive data management (Combine) to keep UI and data state synchronized.
- **Use Cases**: Live room list display, room creation, live status management, live data statistics, and other core live streaming scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [liveList](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststate/livelist) | Live room list data. |
| [liveListCursor](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststate/livelistcursor) | Cursor for paginated live room loading. |
| [currentLive](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststate/currentlive) | Information about the current live room. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [fetchLiveList(cursor:count:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore/fetchlivelist(cursor:count:completion:)) | Retrieve the live room list. |
| [createLive(_:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore/createlive(_:completion:)) | Create a new live room. |
| [joinLive(liveID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore/joinlive(liveid:completion:)) | Join an existing live room. |
| [leaveLive(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore/leavelive(completion:)) | Leave the current live room. |
| [endLive(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore/endlive(completion:)) | End the live stream. |
| [updateLiveInfo(_:modifyFlag:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore/updateliveinfo(_:modifyflag:completion:)) | Update live room information. |
| [queryMetaData](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore/querymetadata(keys:completion:)) | Query custom metadata. |
| [updateLiveMetaData](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveliststore/updatelivemetadata(_:completion:)) | Update custom metadata for the live room. |

## LiveSeatStore

**Live Room Seat Management**

- **Core Features:**Provide seat control for multi-user co-hosting scenarios, supporting advanced seat status management and audio/video device control.
- **Technical Highlights:** Built on WebRTC, supports multi-stream audio/video management, seat locking, device control, and permission management.
- **Use Cases:**Multi-user co-hosting, host PK, interactive games, online education, conference live streaming, and other multi-user live interaction scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [seatList](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstate/seatlist) | List of seats in the live room. |
| [canvas](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstate/canvas) | Canvas information for video layout. |
| [speakingUsers](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstate/speakingusers) | List of users currently speaking. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [takeSeat(seatIndex:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/takeseat(seatindex:completion:)) | Take a seat (join as co-host). |
| [leaveSeat(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/leaveseat(completion:)) | Leave the seat (exit co-host). |
| [muteMicrophone()](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/mutemicrophone()) | Mute the microphone. |
| [unmuteMicrophone(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/unmutemicrophone(completion:)) | Unmute the microphone. |
| [kickUserOutOfSeat(userID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/kickuseroutofseat(userid:completion:)) | Remove a user from a seat. |
| [moveUserToSeat(userID:targetIndex:policy:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/moveusertoseat(userid:targetindex:policy:completion:)) | Move a user to a specified seat. |
| [lockSeat(seatIndex:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/lockseat(seatindex:completion:)) | Lock a seat. |
| [unlockSeat(seatIndex:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/unlockseat(seatindex:completion:)) | Unlock a seat. |
| [openRemoteCamera(userID:policy:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/openremotecamera(userid:policy:completion:)) | Turn on a remote user's camera. |
| [closeRemoteCamera(userID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/closeremotecamera(userid:completion:)) | Turn off a remote user's camera. |
| [openRemoteMicrophone(userID:policy:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/openremotemicrophone(userid:policy:completion:)) | Turn on a remote user's microphone. |
| [closeRemoteMicrophone(userID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveseatstore/closeremotemicrophone(userid:completion:)) | Turn off a remote user's microphone. |

## LiveAudienceStore

**Live Room Audience Management**

- **Core Features:**Manage the audience list, controls audience permissions, sets administrators, and maintains order in the live room.
- **Technical Highlights:** Provide real-time audience list updates, hierarchical permission management, batch operations, and advanced moderation features.
- **Use Cases:** Audience management, permission control, live room moderation, audience interaction, and other live streaming scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [audienceList](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveaudiencestate/audiencelist) | List of audience members in the live room. |
| [audienceCount](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveaudiencestate/audiencecount) | Number of audience members. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [fetchAudienceList(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveaudiencestore/fetchaudiencelist(completion:)) | Retrieve the audience list. |
| [setAdministrator(userID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveaudiencestore/setadministrator(userid:completion:)) | Assign administrator privileges. |
| [revokeAdministrator(userID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveaudiencestore/revokeadministrator(userid:completion:)) | Remove administrator privileges. |
| [kickUserOutOfRoom(userID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveaudiencestore/kickuseroutofroom(userid:completion:)) | Remove a user from the room. |
| [disableSendMessage(userID:isDisable:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/liveaudiencestore/disablesendmessage(userid:isdisable:completion:)) | Disable a user's ability to send messages. |

## DeviceStore

**Device Status Management**

- **Core Features:** Control audio/video devices such as camera and microphone, monitors device status, and checks permissions.
- **Technical Highlights:** Support multi-device management, real-time device status monitoring, dynamic permission checking, and automatic device recovery.
- **Use Cases:** Device management, permission control, audio/video capture, device fault handling, and other foundational technical scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [microphoneStatus](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/microphonestatus) | Microphone enabled status. |
| [microphoneLastError](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/microphonelasterror) | Last microphone error. |
| [captureVolume](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/capturevolume) | Microphone capture volume (0-100). |
| [currentMicVolume](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/currentmicvolume) | Current microphone volume (0-100). |
| [outputVolume](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/outputvolume) | Audio output volume (0-100). |
| [cameraStatus](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/camerastatus) | Camera enabled status. |
| [cameraLastError](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/cameralasterror) | Last camera error. |
| [isFrontCamera](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/isfrontcamera) | Indicates if the front camera is in use. |
| [localMirrorType](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/localmirrortype) | Local video mirror type. |
| [localVideoQuality](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/localvideoquality) | Local video quality settings. |
| [currentAudioRoute](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/currentaudioroute) | Current audio output route (speaker or earpiece). |
| [screenStatus](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/screenstatus) | Screen sharing status. |
| [networkInfo](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestate/networkinfo) | Current network information. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [openLocalMicrophone(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestore/openlocalmicrophone(completion:)) | Enable the local microphone. |
| [closeLocalMicrophone()](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestore/closelocalmicrophone()) | Disable the local microphone. |
| [setCaptureVolume(volume:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestore/setcapturevolume(volume:)) | Set the microphone capture volume. |
| [setOutputVolume(_:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestore/setoutputvolume(_:)) | Set the audio output volume. |
| [openLocalCamera(isFront:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/devicestore/openlocalcamera(isfront:completion:)) | Enable the local camera. |

## CoGuestStore

**Co-Host Guest Management**

- **Core Features:** Manage co-host interactions between audience and host, including application, invitation, acceptance, and rejection workflows.
- **Technical Highlights:** Utilize real-time audio/video technology, supports real-time co-hosting status sync, adaptive audio/video quality, and network monitoring.
- **Use Cases:** Audience co-hosting, interactive Q&A, online karaoke, game streaming, and other audience participation scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [connected](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststate/connected) | List of connected co-host guests. |
| [invitees](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststate/invitees) | List of users invited to co-host. |
| [applicants](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststate/applicants) | List of users applying to co-host. |
| [candidates](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststate/candidates) | List of candidate users available for co-host invitation. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [applyForSeat(seatIndex:timeout:extraInfo:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/applyforseat(seatindex:timeout:extrainfo:completion:)) | Apply for a co-host seat. |
| [cancelApplication(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/cancelapplication(completion:)) | Cancel a co-host application. |
| [acceptApplication(userID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/acceptapplication(userid:completion:)) | Accept a co-host application. |
| [rejectApplication(userID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/rejectapplication(userid:completion:)) | Reject a co-host application. |
| [inviteToSeat(userID:seatIndex:timeout:extraInfo:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/invitetoseat(userid:seatindex:timeout:extrainfo:completion:)) | Invite a user to a co-host seat. |
| [cancelInvitation(inviteeID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/cancelinvitation(inviteeid:completion:)) | Cancel a co-host invitation. |
| [acceptInvitation(inviterID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/acceptinvitation(inviterid:completion:)) | Accept a co-host invitation. |
| [rejectInvitation(inviterID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/rejectinvitation(inviterid:completion:)) | Reject a co-host invitation. |
| [disConnect(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cogueststore/disconnect(completion:)) | Disconnect from co-host. |

## CoHostStore

**Host Connection Management**

- **Core Features:** Enable host-to-host connections, including invitations, connection requests, status management, and host interactions.
- **Technical Highlights:** Support multi-host audio/video synchronization, picture-in-picture display, and audio/video quality optimization for seamless host collaboration.
- **Use Cases:**Host PK, collaborative streaming, cross-platform co-hosting, host interaction, and advanced live streaming scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [connected](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststate/connected) | List of connected hosts. |
| [invitees](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststate/invitees) | List of hosts invited to connect. |
| [applicant](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststate/applicant) | Host currently applying for connection. |
| [coHostStatus](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststate/cohoststatus) | Current host connection status. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [requestHostConnection(targetHost:layoutTemplate:timeout:extraInfo:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststore/requesthostconnection(targethost:layouttemplate:timeout:extrainfo:completion:)) | Request a host-to-host connection. |
| [cancelHostConnection(toHostLiveID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststore/cancelhostconnection(tohostliveid:completion:)) | Cancel a host connection request. |
| [acceptHostConnection(fromHostLiveID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststore/accepthostconnection(fromhostliveid:completion:)) | Accept a host connection request. |
| [rejectHostConnection(fromHostLiveID:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststore/rejecthostconnection(fromhostliveid:completion:)) | Reject a host connection request. |
| [exitHostConnection(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/cohoststore/exithostconnection(completion:)) | Exit a host connection. |

## AudioEffectStore

**Audio Effects Processing**

- **Core Features:**Provide advanced audio effects, including voice changing, reverb, and ear monitoring, with real-time audio adjustments.
- **Technical Highlights:** Powered by Tencent Ethereal Lab's audio algorithms, supports real-time audio effects, low-latency transmission, and audio quality optimization.
- **Use Cases:**Voice changer live streaming, karaoke, audio entertainment, professional audio effects, and other audio processing scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [isEarMonitorOpened](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstate/isearmonitoropened) | Status of ear monitoring (on/off). |
| [earMonitorVolume](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstate/earmonitorvolume) | Ear monitor volume level. |
| [audioChangerType](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstate/audiochangertype) | Current voice changer effect. |
| [audioReverbType](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstate/audioreverbtype) | Current reverb effect. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [setAudioChangerType(type:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstore/setaudiochangertype(type:)) | Set the voice changer effect. |
| [setAudioReverbType(type:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstore/setaudioreverbtype(type:)) | Set the reverb effect. |
| [setVoiceEarMonitorEnable(enable:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstore/setvoiceearmonitorenable(enable:)) | Enable or disable ear monitoring. |
| [setVoiceEarMonitorVolume(volume:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/audioeffectstore/setvoiceearmonitorvolume(volume:)) | Set the ear monitor volume. |

## BarrageState

Barrage Message Management

- **Core Features:** Manage barrage messaging in live rooms, including text and custom messages, with real-time message synchronization.
- **Technical Highlights:**Support high-concurrency message processing, real-time sync, message filtering, emoji support, and more.
- **Use Cases:**Barrage interaction, message management, emoji, chat room, and other social features.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [messageList](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/barragestate/messagelist) | List of barrage messages for the current room. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [sendTextMessage(text:extensionInfo:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/barragestore/sendtextmessage(text:extensioninfo:completion:)) | Send a text barrage message. |
| [sendCustomMessage(businessID:data:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/barragestore/sendcustommessage(businessid:data:completion:)) | Send a custom barrage message. |

## BaseBeautyStore

**Basic Beauty Effects**

- **Core Features:**Provide basic beauty adjustments, including skin smoothing, whitening, and ruddy effects, with real-time parameter tuning.
- **Technical Highlights:** Utilize AI beauty algorithms for real-time processing, smooth parameter adjustment, and optimized performance.
- **Use Cases:**Beauty live streaming, appearance enhancement, beauty adjustment, and live stream beautification.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [smoothLevel](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/basebeautystate/smoothlevel) | Skin smoothing level [0-9]: 0 is off, 9 is maximum. |
| [whitenessLevel](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/basebeautystate/whitenesslevel) | Whitening level [0-9]: 0 is off, 9 is maximum. |
| [ruddyLevel](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/basebeautystate/ruddylevel) | Ruddy level [0-9]: 0 is off, 9 is maximum. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [setSmoothLevel(smoothLevel:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/basebeautystore/setsmoothlevel(smoothlevel:)) | Set skin smoothing level. |
| [setWhitenessLevel(whitenessLevel:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/basebeautystore/setwhitenesslevel(whitenesslevel:)) | Set whitening level. |
| [setRuddyLevel(ruddyLevel:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/basebeautystore/setruddylevel(ruddylevel:)) | Set ruddy level. |

## GiftStore

**Gift System Management**

- **Core Features:**Manage sending and receiving gifts, gift list management, gift categorization, gift animation, gift statistics, and a complete gift economy system.
- **Technical Highlights:**Support gift animation rendering, effect processing, statistics, leaderboards, and more.
- **Use Cases:**Gift tipping, virtual currency, gift effects, gift statistics, and other monetization scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [usableGifts](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/giftstate/usablegifts) | List of available gifts. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [refreshUsableGifts(completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/giftstore/refreshusablegifts(completion:)) | Refresh the available gift list. |
| [sendGift(giftID:count:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/giftstore/sendgift(giftid:count:completion:)) | Send a gift. |

## LikeStore

**Like Interaction**

- **Core Features:** Manage the like feature in live rooms, including sending likes, like statistics, event listening, and interactive effects.
- **Technical Highlights:**Support high-concurrency like processing, real-time statistics, like animations, leaderboards, and more.
- **Use Cases:**Like interaction, popularity statistics, interactive effects, user engagement, and other live streaming scenarios.

**Reactive Data**

| **Data List** | **Description** |
| --- | --- |
| [totalLikeCount](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/likestate/totallikecount) | Total number of likes. |

**API Functions**

| **Function List** | **Description** |
| --- | --- |
| [sendLike(count:completion:)](https://tencent-rtc.github.io/TUIKit_iOS/documentation/atomicxcore/likestore/sendlike(count:completion:)) | Send a like. |


---
*Source: [https://trtc.io/document/66838](https://trtc.io/document/66838)*
