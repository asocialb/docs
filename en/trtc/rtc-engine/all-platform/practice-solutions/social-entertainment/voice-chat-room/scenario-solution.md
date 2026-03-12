# Scenario Solution

## Scenario Introduction

A voice chat room is a virtual space for online social interaction in audio-only mode. Normally, several seats are available in the room where anchors and mic-connecting audience chat via microphones, and other listeners can enter the room to listen. Different room types correspond to varying number of seats and varying maximum audience capacities. [RTC Engine](https://trtc.io/products/chat) supports up to 50 people chatting via microphones simultaneously with smooth switching between becoming a speaker and leaving the seat and voice chat latency less than 300 ms. It also provides a variety of audio effects, such as voice changing, ambiance sound effects, and reverb to enrich the voice chat experience. Combined with [Chat](https://trtc.io/products/chat), it supports various forms of message interaction such as public chat, private chat, group chat, likes, and gift sending to create a lively and engaging chat interaction experience.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4119fbfc8f0411f0ae9d5254001c06ec.png)

## Implementation Scheme

Implementing a complete voice chat room scenario usually involves several functional modules: [Room Management](#45608109-3c99-471b-9911-2ddf76785e47), [Seat Management](#f6b567ce-31cc-4bff-bc6b-c26483820a6f), [Audio Stream Management](#510bdc2b-c44b-41f4-af70-aec43c9cfdf8), [On-Cloud Recording](#386b6ae3-8aff-4b87-9dd5-6527257cce97), etc. The key actions and feature points under each functional module are as follows:

| Functional Module | Key Actions and Feature Points |
| --- | --- |
| Room Management | Room list, create a room, enter a room, exit a room, and terminate a room. |
| Seat Management | Become a speaker, invite a listener to speak, become a listener, remove a speaker, mute a seat, lock a seat and move a seat. |
| Audio Stream Management | Publishing/Playback Architecture Solution, Real-Time Stream Subscription Mode |
| On-Cloud Recording | RTC Engine On-Cloud Recording |

The overall business architecture of the voice chat room is shown in the figure below. Room owners create voice chat rooms, and users can choose to join rooms that interest them. After entering a room, users can go on the seat and engage in voice interaction with the speakers. However, due to compliance requirements, the voice content in the room needs to be recorded and reviewed.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/41173c1d8f0411f088af5254005ef0f7.png)

### Room Management

The Room Management Module is primarily responsible for maintaining the room list and includes the following features:

- Create Room: After users log in to the business system, they can create a room. The room list needs to be updated after a room is created.
- Enter Room: Users can choose to enter an existing room. Upon entering, the current list of room members should be updated.
- Exit Room: Users can choose to exit the current room. Upon exiting, the current list of room members needs to be updated with a delete operation.
- Terminate Room: After all users exit the room, it needs to be terminateed. Upon destruction, the room list needs to be updated with a delete operation.

#### Scheme Architecture

In the overall architecture of room management, there are primarily three major modules involved:

- Room Management: Mainly used for the maintenance and administration of the room list, such as synchronizing the properties and status of rooms. Features include room list querying, entering/exiting rooms, and creating/terminateing rooms.
- Chat Group Management: Mainly used for room member list, signaling receiving and transmission, and message interaction, such as approving/rejecting requests for becoming a speaker, inviting a listener to speak/removing a speaker, muting/unmuting seats, and blocking/unblocking a seat. It also distinguishes by group dimension, with features including creating a group, joining a group, exiting a group, and terminating a group.
- RTC Engine Room Management: Mainly used for interaction and transmission of audio streams, such as sending and listening to voice/music of anchors/listeners. It also distinguishes by room dimension, with features including entering/exiting RTC Engine rooms.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/412b95718f0411f0bd05525400454e06.png)

#### Specific Implementation

In room management, different user roles have different feature permissions and implementation processes. In voice chat rooms, there are mainly two roles: the room owner and the listeners. For a detailed description and differences of roles, see the table below:

| Role | Description | Differences |
| --- | --- | --- |
| Room Owner | The room owner with the highest authority in the room can create or terminate the room. | The role should be an anchor.Create or terminate business rooms/Chat groups/RTC rooms |
| Listeners | Participants in the room can also take the mic to become the anchor. | The role can be either audience or anchor.Enter/Exit Room |

#### Implementation Process

- **Room Owner**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/413298c88f0411f0818a52540099c741.png)

1. Obtain the room list.
2. Create the corresponding room through the business API.
3. Create a Chat group.
4. Enter the business room/Chat room/RTC room to interact with others.
5. Exit the Chat group/RTC room/business room.
6. Terminate the Chat group.
- **Listeners**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/411a16848f0411f0b321525400e889b2.png)

1. Obtain the room list.
2. Enter the business room/Chat group/RTC room to interact with others.
3. Exit the Chat group/RTC room/business room.

### Seat Management

In a Voice Chat Room, the seats are usually ordered and limited. For example, an audience needs the room owner's approval to speak orderly. Generally, the number of seats in a room does not exceed 10. Seat management is mainly responsible for managing the number of seats in a room according to the business scenario, as well as the status of all current seats in the room. The main features of seat management include: becoming a speaker, inviting a listener to speak, becoming a listener, removing a speaker, muting a seat, locking a seat, and moving a seat.

- After users enter the room, they can only request to speak when there are idle seats available.
- After the room owner approves a user to become a speaker, the seat status needs to be changed to non-idle.
- After the user stops streaming and becomes a listener, the seat status needs to be reset.
- The room owner has the authority to lock the seat, invite a listener to speak, remove a speaker, mute a speaker, etc.

#### Scheme Architecture

The solution architecture of seat management will be organized through the combination of RTC Engine and Chat. In the overall architecture of room management, the room owner has the highest permission to invite users to speak, remove users, mute/unmute seat audio, and block/unblock seats. Listeners can also request to speak and become anchors to interact with the rest of the anchors in the room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/411063f08f0411f088af5254005ef0f7.png)

#### Specific Implementation

In seat management, different user roles have different feature permissions and implementation processes, primarily involving two roles: room owner and audience. For details on role descriptions and their differences, see the table below:

| Role | Description | Differences |
| --- | --- | --- |
| Room Owner | The figure with the highest authority over seats. The room owner is responsible for managing all seats. When the room owner exits the room, all seats are automatically dissolved. | The role must be an anchor.Enter the room and become a speakerApprove or reject speaking requestsInvite a listener to speak/Remove a listenerMutes/Unmutes a seatBlocks/Unblocks a seat |
| Listeners | Room seat participants who engage in voice interactions. | The role can be either audience or anchor.Request to speak/become a listener |

#### Implementation Process

- **Room Owner**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/413147e28f0411f0b321525400e889b2.png)

1. Anchors enter the Room Lobby and obtain the room list.
2. Anchors create and enter the room as room owners.
3. The room owner obtains the seat list based on group attributes and becomes a speaker.
4. Listeners become speakers. After becoming speakers, they can interact with other speakers. There are two ways for listeners to become speakers: they can either request to speak actively, which the room owner approves, or the room owner can invite them to speak, which they accept.
5. Speakers become listeners. There are two ways to become listeners: they can become listeners actively, or the room owner can forcibly remove them.
6. The room owner exits and terminates the room (the room is dissolved, and all speakers are forcibly removed and exit the room).
- **Listeners**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/40fd9c1d8f0411f0ae9d5254001c06ec.png)

1. Listeners enter the Room Lobby and obtain the room list.
2. Listeners select and enter the room.
3. Listeners obtain the seat list based on group attributes.
4. Listeners request to speak. After approval from the room owner, they interact with other speakers.
5. Speakers become listeners and exit the room.

### Audio Stream Management

The typical interactive scenario for voice chat often opts for the RTC stream access solution, as it offers simplicity and quick integration while providing the low-latency characteristics of real-time interaction. As shown in the figure below, a classic publishing/playback architecture of real-time interactive voice chat is displayed, showcasing two roles: speakers and listeners.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/412d941a8f0411f0ae9d5254001c06ec.png)

For real-time stream subscription within the room, RTC Engine offers 2 subscription modes, Automatic Subscription and Manual Subscription.

- Automatic Subscription: Upon entering the room, users will immediately receive the room's audio and video streams, with audio automatically playing and video automatically starting to decode.
- Manual Subscription: After entering the room, users need to manually call `startRemoteView` to start the subscription and decoding of the video stream, and manually call `muteRemoteAudio` to start the playback of audio.

In most scenarios, RTC Engine defaults to the automatic subscription mode. Upon entering the room, users subscribe to audio and video streams from all anchors for a better "instant-play experience." The manual subscription mode offers greater flexibility and customizability, allowing users to subscribe to audio and video streams selectively.

> **Note:**Compared to the Manual Subscription mode, Automatic Subscription does not require complex media stream subscription management. For voice chat scenarios without special requirements, Automatic Subscription is recommended.

### On-Cloud Recording

RTC Engine's latest upgraded On-Cloud Recording uses RTC Engine's internal real-time recording cluster for audio and video recording, offering a more complete and unified recording experience.

- Single-stream recording: Via RTC Engine's on-cloud recording feature, you can record the audio stream of each user in the room into a separate file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/411c349f8f0411f084bd5254007c27c5.png)

- Mixed Stream Recording: Mix and record the audio media streams from the same room into a single file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/412871818f0411f0ae9d5254001c06ec.png)

> **Note:**For a detailed introduction and activation instructions of RTC Engine on-cloud recording, see [RTC Engine On-Cloud Recording Instructions](https://trtc.io/zh/document/45169?product=rtcengine&menulabel=core%20sdk&platform=android).

## Key Business Logic

### Ganchor Mic Handling Solution

Ganchor mic, also known as blast mic or black mic, refers to the phenomenon where users not becoming speakers can speak and other users can hear their voice. The root cause of this issue is the inconsistency between the business seat status and the RTC Engine user role status. This issue may be caused by the following reasons.

- When a speaker becomes a listener, the seat list is updated. However, due to the seat information callback not being triggered or intercepted, local RTC Engine operations for switching the audience's role and turning off the microphone are not performed, so the speaker remains able to speak despite becoming a listener.
- When a speaker becomes a listener, the seat list is updated. After seat information callback is received, audience's local call to the API for switching to the audience role provided by RTC Engine is conducted, but fails, making users able to speak after they leave the seat.
- The App is cracked by brute force, causing UserSig being intercepted by hackers, allowing hackers to enter the RTC Engine room as an anchor and speak freely.

#### Detection and Handling of Ganchor Mics

By detecting ganchor mics, we can proactively identify and promptly handle them. It is recommended to use a server detection solution: Real-time anchor list comparison detection.

Principle of the Solution: In the voice chat room scenario, user roles are divided into anchors and audiences, with only the anchor role being able to upstream local audio. Therefore, ganchor mics can be detected by comparing the business seat list with the RTC Engine role list. RTC Engine provides server-side room and media event callbacks. By listening for events such as entering the room, switching roles, and exiting the room, you can maintain a real-time anchor list for the current room. Then, by comparing the RTC Engine real-time anchor list with the business full seat list, you can easily detect and identify ganchor mics, and then actions such as removing users from the room or muting can be performed.

1. The RTC Engine console supports self-service configuration of callback information. Once configured, you can receive event callback notifications. For details, see [Callback Configuration](https://trtc.io/document/39558?product=rtcengine&menulabel=core%20sdk&platform=android).
2. Receive and parse callback event packages, pay attention to events 103/104/105, and count the real-time online anchor list in the current room. For more details, see [Callback Event](https://trtc.io/document/39558?product=rtcengine&menulabel=core%20sdk&platform=android#event_type).

103

104

105

```
{	"EventGroupId":	1,                        #Room event group	"EventType":	103,                      #Enter room event	"CallbackTs":	1687679847972,            #Callback time, in milliseconds	"EventInfo":	{		"RoomId":	"123456",                 #Room ID		"EventTs":	1687679847,               #Event occurrence time, in seconds		"EventMsTs":  1687679847899,          #Event occurrence time, in milliseconds		"UserId":  "1a99b0a9",                #Username		"Role":  20,                          #User role 20:Anchor; 21:Audience        "TerminalType": 2,                    #Terminal Type        "UserType": 3,                        #User Type        "Reason": 1                           #Specific reasons	}}
```

```
{	"EventGroupId":	1,                        #Room event group	"EventType":	104,                      #Exit room event	"CallbackTs":	1687679847972,            #Callback time, in milliseconds	"EventInfo":	{		"RoomId":	"123456",                 #Room ID		"EventTs":	1687679847,               #Event occurrence time, in seconds		"EventMsTs":  1687679847899,          #Event occurrence time, in milliseconds		"UserId":  "1a99b0a9",                #Username		"Role":  20,                          #User role 20:Anchor; 21:Audience        "Reason": 1                           #Specific reasons	}}
```

```
{	"EventGroupId":	1,                        #Room event group	"EventType":	105,                      #Switch role event	"CallbackTs":	1687679847972,            #Callback time, in milliseconds	"EventInfo":	{		"RoomId":	"123456",                 #Room ID		"EventTs":	1687679847,               #Event occurrence time, in seconds		"EventMsTs":  1687679847899,          #Event occurrence time, in milliseconds		"UserId":  "1a99b0a9",                #Username		"Role":  20                           #User role 20: Anchor; 21: Audience	}}
```

> **Note:****105-Switch Role Event** is only triggered by changes in the user role after entering the room. Therefore, you also need to supplement the user role list based on the initial role information in **103-Enter Room Event**, as well as update the user role list according to **104-Exit Room Event**, to maintain a more accurate list of room user roles.

3. Periodically compare the business seat list for each room with the RTC Engine real-time anchor list to identify ganchor mics and [mute](https://trtc.io/document/51289?product=rtcengine&menulabel=core%20sdk&platform=android) them or [remove](https://trtc.io/document/34268?product=rtcengine&menulabel=core%20sdk&platform=android) them out of the room.

### Anti-Stutter Solution When Switching on and Off the Mic

#### Problem Description

Due to differences in the mechanisms of mobile device systems, the performance of switching on and off the mic in the voice chat scenario may differ between Android and iOS. On iOS devices, there may be brief audio stutters when switching on and off the mic.

#### Cause Analysis

This is related to the iOS system's audio mechanism. The `startLocalAudio` and `stopLocalAudio` operations access and release the microphone device permissions, respectively. SDK's audio re-capturing causes the AVAudioSession to restart the audio driver, resulting in a temporary audio stutter when switching on and off the mic.

#### Solutions

The conventional sequence of the solution of becoming a speaker and leaving the seat in RTC Engine is shown below. Local audio collecting and publishing are simultaneously enabled or stopped when roles are switched. This solution works normally on the Android platform.

On iOS, during the mic off operation, it is possible to stop streaming simply by switching the audience role, without the need to call `stopLocalAudio` to stop audio capture and release mic permissions, thereby avoiding audio stutters during mic on/off.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/410152138f0411f0ae9d5254001c06ec.svg)

> **Note:**In the anti-stutter solution, not calling `stopLocalAudio` will keep the mic in a continuous capturing state, which may lead to user misunderstanding.

### Best Practices for Audio Configuration

In audio configuration, audio quality and volume type are 2 distinct concepts. In RTC Engine, audio quality can be set during the enabling of local audio collecting and publishing by using `startLocalAudio(TRTCAudioQuality)`, or be set individually through `setAudioQuality(TRTCAudioQuality)`. Volume type is determined by a combination of factors such as room entry scenarios and audio quality settings. Additionally, a certain volume type can be forcibly specified through `setSystemVolumeType(TRTCSystemVolumeType)`.

#### **Best Practices for Audio Quality Configuration**

The RTC Engine SDK provides 3 finely tuned audio quality modes to meet the diverse audio quality needs in various vertical scenarios.

| Audio Quality Mode | Audio Quality Enumeration Value | Audio Quality Parameters | Audio Quality Explanation |
| --- | --- | --- | --- |
| Voice Mode | TRTCAudioQualitySpeech | Sampling Rate: 16 k; Mono;Encoding Bitrate: 16 kbps | It has strong network resilience and performs well in poor network environments, making it suitable for applications primarily focused on voice communication, such as online meetings, voice calls, etc. |
| Default Mode | TRTCAudioQualityDefault | Sampling Rate: 48k; Mono;Encoding Bitrate: 50 kbps | The default SDK settings. It offers better fidelity for music than the Voice Mode, while also transmitting much less data volume than the Music Mode. This makes it versatile and suitable for various scenarios. |
| Music Mode | TRTCAudioQualityMusic | Sampling Rate: 48 k; Full-Band Stereo;Encoding Bitrate: 128 kbps | Under this mode, the audio transmission consumes a significant data volume, ensuring that the music signal achieves high fidelity in detail restoration across all frequency bands, suitable for scenarios requiring high-quality music transmission. |

As can be seen from the table, from Voice Mode to Music Mode, the audio quality effect improves, but the data volume of audio transmission also increases.

- In the scenario of a voice chat room, it is recommended to choose the Voice Mode for pure voice communication, which can achieve better smoothness under weak network conditions.
- For voice chat rooms with a need to play background music, it is recommended to choose the Default Mode or Music Mode to achieve good audio detail restoration.
- Considering the bandwidth pressure on downstream audience networks, to ensure a good user experience, it is advisable to use the Music Mode cautiously in business scenarios with ten or more seats.

> **Note:**RTC Engine supports dynamic adjustment of audio quality. In the streaming process, you can dynamically adjust audio quality by calling setAudioQuality(TRTCAudioQuality).

#### **Best Practices for Volume Type Configuration**

The RTC Engine SDK provides 3 control modes for system volume types to meet the different needs of volume types in various scenarios.

| Volume Type Mode | Volume Type Mode Enumerated Value | Volume Type Mode Description |
| --- | --- | --- |
| Full Call Volume | TRTCSystemVolumeTypeVOIP | The advantage of this solution is that the audio module does not need to switch working modes during mic on/off, enabling seamless mic switching. It is suitable for applications where users frequently switch mics. If the scenario selected upon entering the room is TRTCAppSceneVideoCall or TRTCAppSceneAudioCall, the SDK will automatically use this mode. |
| Automatic Switching Mode | TRTCSystemVolumeTypeAuto | Also known as Voice Call on Mic, Media Off Mic. This mode ensures that the anchor uses call volume when on the mic, while the off-mic audience uses media volume, suitable for live streaming scenarios. If the scenario selected upon entering the room is TRTCAppSceneLIVE or TRTCAppSceneVoiceChatRoom, the SDK will automatically use this mode. |
| Full Media Volume | TRTCSystemVolumeTypeMedia | Use Media Volume for the entire call. It is suitable for music scenarios where demanding audio quality is required. If your users mainly use external devices (such as external sound cards), this mode can be adopted. |

- In call scenarios, it is recommended to choose the default Full Call Volume, where the audio module does not need to switch;
- In voice chat room scenarios, it is recommended to use the default Automatic Switching mode for pure voice communication, that is, Voice Call on Mic, Media Off Mic.
- Voice chat rooms that need background music can consider setting the volume to Full Media Volume throughout to avoid users perceiving stuttering or sudden volume changes in music when going on and off the mic.

> **Note:**If you need to specify a volume type, it is recommended to call `setSystemVolumeType` once after entering the room and before starting to stream. Do not call it during the mic on/off.Call Volume supports the phone's built-in AEC feature and allows audio pickup via the mic on Bluetooth headphones, but the disadvantage is the audio quality is relatively average.Media Volume does not support the phone's built-in AEC feature and does not support audio pickup via the mic on Bluetooth headphones, but it has better music playback performance.

### Single-Stream Volume Evaluation

In the voice chat room scenario, some customers may choose speakers for RTC single streams and playback and audience for playback of mixed streams in the room to save bandwidth and costs. However, the voice chat room scenario typically requires UI prompts based on the volume of on-mic users, such as a "sound wave graph" or "volume slider." The feature of volume evaluation and feedback for single-channel audio is easy to implement in an RTC Engine room, but achieving it in an audio-only mixed stream requires specialized techniques. The specific information of 2 solutions will be introduced below.

#### **Single-Stream Volume Evaluation in RTC Room**

**Step One: Enable Volume Prompts**

Enable the volume callback through the `enableAudioVolumeEvaluation` API, and optionally enable the local voice detection feature. After enabling this feature, the SDK will provide feedback in the `onUserVoiceVolume` callback about the volume of both local users and remote streaming users, the maximum volume value, as well as the local voice detection result.

> **Note:**RTC Engine SDK 10.2 or later adds the local voice detection feature. Once enabled, it will show the local voice detection result in `TRTCVolumeInfo.vad` (only for the anchor role). `muteLocalAudio` and `setAudioCaptureVolume(0)`. The operations will not affect the voice detection result, making it easy to remind users to turn on their microphones.

**Step Two: Listen to the Volume Callback**

Listen to the `onUserVoiceVolume` callback in `TRTCCloudListener`. This callback provides information on the volume levels of both local and remote users' streams, as well as the maximum volume value of remote users. Based on these volume levels, you can adjust the UI to display corresponding voice waveforms.

> **Note:**Rendering voice waveform animations for speakers can be determined by the volume level in the [onUserVoiceVolume](https://trtc.io/document/50763?platform=android&product=rtcengine&menulabel=core%20sdk#2ec23470e2480bd26d91353c0998d019) callback. The activation and deactivation of voice waveform animations (user's mic on/off state) are recommended to be determined based on the [onUserAudioAvailable](https://trtc.io/document/50763?platform=android&product=rtcengine&menulabel=core%20sdk#cb979bbb36c24acc891ce2115ff2b6c6) callback.

#### **Evaluation of Single Stream Volume in Audio-Only Mixed Stream**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/411a73dd8f0411f0814e525400bf7822.png)

The implementation process of evaluating single stream volume in audio-only mixed stream is shown in the diagram above. Speakers need to listen for volume level callback and determine both local and remote volume levels. Then, insert the local volume value and user information into the audio stream in the form of SEI messages. After mixing, these messages are transmitted to listeners. **Alternatively, the room owner can send out speakers' callback volume values through SEI messages**. The diagram below shows the sequence diagram of the entire process:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/41276e148f0411f0bd05525400454e06.svg)

> **Note:**If there is a requirement for mixing and relaying to CDN while transmitting SEI:The room entry scenario must be set to LIVE and cannot be set to pure audio entry, otherwise SEI messages will not be transmitted.If the mixing API adopts `setMixTranscodingConfig`, then the mixing mode cannot use the `PureAudio` audio-only mode.If the mixing API adopts `startPublishMediaStream`, then the media stream transcoding configuration parameters must carry the `TRTCVideoLayout` parameter.

As shown below, the audience will see the volume levels of the respective speakers in the SEI messages parsed from the mixed stream.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/41064c658f0411f0ae9d5254001c06ec.png)

## Scenario Gameplay

In the voice chat room scenario, the room owner and several speakers interact online through voice, and there may also be listeners who cannot speak but only listen and interact through sending gifts and chat messages. Different room themes are usually set to attract users with similar interests for viewing and interaction. Common themes include FM radio, Karaoke chat, game interaction, and sports event streaming.

### FM Radio Room

There may be a solo live broadcast by an anchor or a host with several fixed chatting guests, while background music and sound effects are played simultaneously. Listeners can request to speak by giving gifts to participate in voice interaction.

This scenario usually involves a considerable audience size. A single RTC Engine room can simultaneously support up to 100,000 users, and is suitable for the solution of anchor streaming and playback of RTC streams as well as audience streaming and playback of RTC single streams.

> **Note:**For this scenario, it is recommended to use the solution of speakers pushing and pulling RTC streams while the audience pulls CDN mixed streams.

### Karaoke Voice Chat Room

Usually, there is one administrator, and everyone can select songs, comment, guess songs, continue singing, etc. It mainly consists of two models: Multi-Person Co-Anchoring and Multi-Person Mic Rotation. In the Multi-Person Co-Anchoring mode, one person sings while other co-anchoring users can listen and speak simultaneously, but the lead singer cannot hear the other speakers. However, the audience in the room can hear all the voices. The Multi-Person Mic Rotation mode allows a person to sing a portion of a song, after which it automatically transitions to the next person; meanwhile, other users can only listen and comment during the waiting period, without participating in voice chat.

Online Karaoke scenarios require high synchronization and allow audiences to sing together at any time, making it suitable to use the solution of anchor streaming and playback of RTC streams as well as audience streaming and playback of RTC mixed streams. Here, a mixed-stream robot is needed to initiate the mixed-stream command and push the mixed streams back to the RTC Engine room for playback and watching by the audience.

> **Note:**For this scenario, it is recommended to use the solution of the speaker pushing and pulling RTC streams while the audience pulls RTC mixed streams.For specific technical details and precautions regarding the implementation of Karaoke Voice Chat Rooms, please refer to [Online Karaoke Scenario Solutions](https://www.tencentcloud.com/document/product/1228/59946?lang=en&pg=).

### Interactive Gaming Room

In scenarios like Werewolf, Murder Mystery, Dubbing, Truth or Dare, and Draw and Guess, rooms are created based on the game's progression, and the speaking permissions of players are controlled in sequence according to the game's progress.

In interactive gaming scenarios, the number of participants is typically limited, and there is a need for frequent joining and leaving of the mic for gaming purposes. This scenario is suitable for the conventional approach of having the speaker pull and push RTC streams while the audience pulls RTC single streams. Game participants can request to speak at any time or choose to mute themselves until their character dies, forcing them to become listeners or exit the room.

> **Note:**This scenario recommends the solution of the speaker pulling and pushing RTC streams while the audience pulls RTC single streams.Interactive gaming rooms usually include the playing of local game audio effects, so attention must be paid to AEC processing and the selection of volume types.

## Supporting Products for the Solution

| System Level | Product Name | Application Scenarios |
| --- | --- | --- |
| Access Layer | [RTC Engine](https://trtc.io/products/rtc) | Provides low-latency, high-quality real-time interactive live streaming solutions for multi-person voice interaction, serving as the foundational capability for voice chat scenarios. |
| Access Layer | [Chat](https://trtc.io/products/chat) | Provides room management and seat management capabilities based on group features, enables the sending and receiving of rich media messages such as live streaming room-wide messaging, public screen messages, as well as custom signaling and other communication needs. |
| Cloud Services | [Video on Demand (VOD)](https://www.tencentcloud.com/products/vod) | For audio-video media, it offers an integrated high-quality media service that includes production and upload, storage, transcoding, media processing, media AI, accelerated distribution and playback, and copyright protection |
| Data Storage | [Cloud Object Storage (COS)](https://www.tencentcloud.com/products/cos) | Provides storage services for audio recording files and audio slicing files. |


---
*Source: [https://trtc.io/document/73426](https://trtc.io/document/73426)*
