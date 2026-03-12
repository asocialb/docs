# Implementation Steps

## Introduction

To implement a complete online Karaoke scenario, multiple functional modules are required, including room management, seat management, song selection management, and Karaoke management. The key actions and features of each functional module are shown in the table below. In the following sections, each functional module will be introduced in detail to provide a complete understanding of the required functions for building a Karaoke room.

| Room Management | Seat Management | Song Selection Management | Karaoke Management |
| --- | --- | --- | --- |
| Room List | Go on/off the seat | Song List Display | Karaoke Play Mode |
| Create Room | Seat Control | Search for Songs | Song Switching |
| Join Room | Lock the Seat | Song Selection | Vocal Volume Adjustment |
| Leave Room | Take Seat | Song Top | Reverb/Sound Effects |
| Destroy Room | Mute Seat | Selected Song List | Lyric Synchronization |

The room owner creates the Karaoke room, and users can choose to join the room they are interested in. After entering the room, users can go on the seat to participate in the interaction and have voice interaction with the room owner. Of course, users can also choose to go directly on the seat to participate in the chorus. These are two different Karaoke play modes. The overall business process of the online Karaoke scenario is shown in the figure below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8263ca8f5b6f11ee974d5254005f490f.png)

## Room Management

Room management is mainly responsible for maintaining the room list. The main functions include creating a room, joining a room, destroying a room, and leaving a room. Moreover, Karaoke rooms are different from ordinary rooms and require a separate Karaoke room identifier to start related component management, such as song selection management and Karaoke management.

- **Create Room**: After logging into the business system, users can create a room. After creating a room, the room list needs to be updated with the new room.
- **Destroy Room**: After all users leave the room, the room needs to be destroyed. After destroying the room, the room list needs to be updated with the deletion of the room.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9254b9845b6f11ee974d5254005f490f.png)

> **Note****ï¼**Room management is a necessary module for implementing online karaoke, but it is not the main functional module. The specific implementation can be combined with the business system and TRTC SDK, please refer to the voice chat room scene access solution for details.

## Seat Management

The seats in the karaoke room are generally ordered and limited. Seat management is mainly responsible for defining the number of seats in the room and managing the status of all seats in the current room according to the business scenario. Seat management mainly includes the following functions: going on/off the seat, locking the seat, inviting to go on the seat, and muting the seat.

- After entering the room, users can only apply to go on the seat for the seats that are in idle state.
- After the host agrees to let the user go on the seat, the seat status needs to be changed to a non-idle state.
- After the user stops streaming and goes off the seat, the seat status needs to be reset.
- The host has the right to lock the seat, invite to go on the seat, force to go off the seat, and mute the seat.

> **Note****ï¼**Seat management is a necessary module for implementing online karaoke, but it is not the main functional module. The specific implementation can be combined with the business system and IM SDK, please refer to the voice chat room scene access solution for details.

## Song selection management

### Basic Introduction

Song selection management is an important part of the online karaoke scene, which mainly includes the following functions: song list display, song search, song selection and queue management, and list of selected songs. Moreover, each karaoke room needs to maintain a list of selected songs and an automatic queue management function, which requires the business backend to implement. Song list display and song search need to be combined with Yinsuda Authorized Music for Live Streaming to achieve.

### Implementation Process

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b8f46a305b6f11eeabd75254005810a4.png)

The entire song selection management mainly involves the business-side app, the business backend, and the Yinsuda backend, each with its own functions:

- **Business-side app:**
  - Call the song selection API to report song information.
  - Call the song cutting API to notify the business backend to update the list of selected songs.
  - Call the singing confirmation API to notify the business backend.
- **Business backend:**
  - Maintain the list of selected songs.
  - Send notifications to the business-side app to update the current list of selected songs.
- **Yinsuda backend:**
  - Provide APIs to obtain the recommended song list and song list details for live interactive music Song List/Song List Details.
  - Provide an API to obtain the details of live interactive music Get Live Interactive Music Details (playToken, lyric download URL).
  - Provide an API to search for live interactive music Search Live Interactive Music.

## Karaoke Management

The karaoke system mainly includes the following functions: singing gameplay, start/stop/song cutting, vocal volume adjustment, reverb/sound effects, and lyric synchronization. Below, we will introduce the implementation process of the karaoke management module in detail through two typical karaoke gameplay: solo singing and real-time chorus.

### Solo Singing

This is mainly a multi-user interactive Karaoke scene. After the host goes on the seat, they can select songs for singing. Once the host successfully selects a song, all song selection information will be displayed on the song selection platform. The host can then choose to begin singing.

#### **(1) Solution Architecture**

The overall solution architecture mainly utilizes the VOD SDK to achieve song downloading, the VOD backend to obtain the playToken and lyric download address of the song, and the TRTC SDK to implement the singer's voice streaming, song playback, and streaming. The overall solution architecture is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f7757a925b7011eeabd75254005810a4.png)

#### **(2) Specific Implementation**

In the singing scenario, different roles have different implementation processes, which can be divided into two roles: singer and audience.

| Role | Description | Differences |
| --- | --- | --- |
| Singer | The singer in the Karaoke room is evolved from the host who selects songs and sings after going on the seat. After leaving the room, the room is automatically dissolved and the list of selected songs is automatically cleared. | The role must be a hostUpstream audio and video (no video upstream black frame)Play BGMSend SEI information (send lyric information)Song selection |
| Audience | The audience in the Karaoke room plays the stream of the singer. | The role is an audience, but can also become a host by going on the seatDownstream audio and video streamsReceive SEI information (receive lyric information) |

The basic implementation processes for different roles are as follows:

ãHostã

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d156cbb45b6f11ee94c3525400d793d0.png)

- The host creates and joins a TRTC room, automatically goes on the seat, and becomes a singer after selecting a song.
- After selecting a song, the song/lyric is downloaded, and then the song is played through the BGM playback interface.
- If the singer does not bring up the video upstream, they need to enable video upstream.
- Synchronize the lyric progress of everyone through SEI information.
- The singer can cut the song at any time during the singing process, and then download and sing the song/lyric again after the download is complete.
- After the host leaves the room, the TRTC room will be dissolved.

ãAudienceã

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8a0e920a5c2e11ee94c3525400d793d0.png)

- The audience joins the TRTC room.
- Listen for changes in the room's song and load the lyrics.
- Pull the stream of the singer.
- Parse the SEI information sent by the singer and synchronize the lyrics.

The main task is to listen for the SEI information of the song and update the corresponding song control.

#### **ï¼3ï¼API call sequence**

The API calls for different roles are sequenced as follows:

| Host | Audience |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a8274fff5c1811ee9ff8525400d917da.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fbef5f325c1811ee974d5254005f490f.png) |

> **Note****ï¼**Given the technical threshold required for the above implementation solution, TRTC provides an open-source audio and video UI component called [TUIKaraoke](https://www.tencentcloud.com/zh/document/product/647/41940) on its official website. By integrating the TUIKaraoke component into your project, you can add online karaoke scenes to your application with just a few lines of code, and experience TRTC's related capabilities in Karaoke scenarios, such as karaoke, seat management, gift giving and receiving, text chat, and more.

### Real-time Chorus

Real-time chorus refers to playing songs simultaneously on various ends while connected, and then singing together on the seat. In multi-user mode, the singers can hear each other's voices almost without delay, achieving true real-time chorus.

#### **(1) Solution Architecture**

In terms of media streams, the singers push and pull streams to each other, and one ***lead singer pushes out the music***, while other ***singers play the music locally***, with time synchronization through NTP. In addition, the song and the voices of all singers are mixed and processed into one stream by the mixing robot, and then pushed back to the TRTC room. The audience only needs to pull one stream to hear the synchronized voices from all ends, perfectly achieving the effect of multi-person chorus. The solution architecture for real-time chorus is shown in the following figure.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/22243bde5b7111eeabd75254005810a4.png)

The advantages of this solution are:

- It reduces end-to-end latency.
- It provides a solution for users to join the chorus midway.
- It accurately synchronizes music, lyrics, and vocals between different ends.
- It improves the performance of devices on different ends and the accuracy of local time, and reduces the impact of network environment latency.

> **Note****ï¼**Depending on business needs, you can choose a real-time chorus solution for either pure audio or audio and video scenarios. If it is a pure audio scenario, black frames need to be added to send SEI messages for lyric synchronization.The lead singer needs to use a sub-instance to upstream both the music and vocals at the same time; other singers only need to pull each other's vocal streams and play the music locally; the audience only needs to pull one mixed stream.The figure shows the RTC viewing solution, where the mixing robot pushes the mixed stream back to the RTC room; in the CDN viewing solution, the mixing robot pushes the mixed stream to the live CDN, and the audience pulls the CDN stream to watch.

#### **(2) Specific Implementation**

We can divide the users in the online karaoke room into three roles: lead singer, chorus, and audience, as shown in the table below.

| Role | Description | Differences |
| --- | --- | --- |
| Lead Singer | The lead singer is responsible for selecting songs, sending chorus signals, and sending SEI messages. | The role must be an AnchorUpstream music and vocalsSong selection and initiating chorusPushing back mixed streamSending SEI messages |
| Chorus | The chorus can receive and process chorus signals, and participate in the chorus on the seat. | The role must be an AnchorUpstream vocalsPlay music locallyReceive chorus signals |
| Audience | After entering the karaoke room, the audience can pull the stream from the seat and also participate in the chorus on the seat. | The role must be an AudienceDownstream mixed streamReceive SEI messages Apply to become an Anchor to go on the seat |

The basic implementation processes for different roles are shown in the following figure:

ãLead Singerã

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/065b6a775b7011ee94c3525400d793d0.png)

- The lead singer needs to select a song and send chorus signals.
- The lead singer creates a sub-instance to push vocals and music, and pulls the vocals of other singers.
- After pushing the stream, the lead singer is responsible for initiating the mixed stream push task.
- After starting the performance, play the music and synchronize the lyrics through the playback progress callback.
- SEI messages need to be sent to synchronize the song progress on the audience end.
- All singers need to calibrate the local song playback progress according to NTP.

ãChorusã

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1a334ad85b7011ee9ff8525400d917da.png)

- The chorus pushes one vocal stream and pulls the vocal stream of the user on the seat.
- The chorus needs to listen for and receive chorus signals, and pre-load music resources.
- After starting the performance, play the music locally, and the chorus synchronizes the lyrics through the playback progress callback.
- All singers need to calibrate the local song playback progress according to NTP.

ãAudienceã

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b2b307e35b7011ee9ff8525400d917da.png)

- Pull the mixed stream to listen to the chorus.
- Parse the song progress information in the SEI of the mixed stream for lyric synchronization.
- After going on the seat, stop pulling the mixed stream, switch to pulling the vocal stream on the seat, and start the chorus mode.

#### **ï¼3ï¼API call sequence**

The sequence of API calls for different roles is as follows:

| Lead singer API sequence | Chorus API sequence | Audience API sequence |
| --- | --- | --- |
|  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9deb81d65c1911eeabd75254005810a4.png)  |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d10749215c1311ee94c3525400d793d0.png)  |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af7c08175c1311eeabd75254005810a4.png)  |

> **Noteï¼**Considering the technical expertise required for the above implementation, TRTC's official website provides an open-source audio and video UI component called TUIKaraoke, which can be integrated into your project. With just a few lines of code, you can add real-time karaoke scenes to your application and experience TRTC's related capabilities for KTV scenarios, such as singing, seat management, gift exchange, text chat, and more.


---
*Source: [https://trtc.io/document/57023](https://trtc.io/document/57023)*
