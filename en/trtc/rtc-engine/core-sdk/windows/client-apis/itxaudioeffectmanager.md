# ITXAudioEffectManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: management class for background music, short audio effects, and voice effects

Description: sets background music, short audio effects, and voice effects

**ITXAudioEffectManager**

## ITXMusicPreloadObserver

| FuncList | DESC |
| --- | --- |
| [onLoadProgress](https://www.tencentcloud.com/document/product/647/50773#252983e16058385423c9b198b01cb69e) | Background music preload progress. |
| [onLoadError](https://www.tencentcloud.com/document/product/647/50773#1842628ca4d7f36f4858449f61a02440) | Background music preload error. |

## ITXMusicPlayObserver

| FuncList | DESC |
| --- | --- |
| [onStart](https://www.tencentcloud.com/document/product/647/50773#bac31892ad2f5910c3d256b01a61e81e) | Background music started. |
| [onPlayProgress](https://www.tencentcloud.com/document/product/647/50773#386181aa98f75be9af4c612f33ad8c8d) | Playback progress of background music. |
| [onComplete](https://www.tencentcloud.com/document/product/647/50773#f15898805455a229bceebf717dc0c84c) | Background music ended. |

## ITXAudioEffectManager

| FuncList | DESC |
| --- | --- |
| [enableVoiceEarMonitor](https://www.tencentcloud.com/document/product/647/50773#ce206abf19487155ebafe9f456bc84b0) | Enabling in-ear monitoring. |
| [setVoiceEarMonitorVolume](https://www.tencentcloud.com/document/product/647/50773#de297f1ab27a50566e80dc41ffee0faf) | Setting in-ear monitoring volume. |
| [setVoiceReverbType](https://www.tencentcloud.com/document/product/647/50773#b2c60a1394dcd44551b2253666ffbb5c) | Setting voice reverb effects. |
| [setVoiceChangerType](https://www.tencentcloud.com/document/product/647/50773#f9cfcc00f81b02d9f1b1526462d8418e) | Setting voice changing effects. |
| [setVoiceCaptureVolume](https://www.tencentcloud.com/document/product/647/50773#79d19bbc256e38dd8fc49d827fad81e4) | Setting speech volume. |
| [setVoicePitch](https://www.tencentcloud.com/document/product/647/50773#611b42876c3252c9210eac5fad77f75b) | Setting speech pitch. |
| [setMusicObserver](https://www.tencentcloud.com/document/product/647/50773#d536291b7952f338944913ad467460d2) | Setting the background music callback. |
| [startPlayMusic](https://www.tencentcloud.com/document/product/647/50773#aacead5ce840018e0505825e2b942052) | Starting background music. |
| [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50773#be8c49a0723691a13da9d0b1a21ad6ab) | Stopping background music. |
| [pausePlayMusic](https://www.tencentcloud.com/document/product/647/50773#4023582e7d64ac4b95619a1ef8d4e2d7) | Pausing background music. |
| [resumePlayMusic](https://www.tencentcloud.com/document/product/647/50773#be322cd251e6920b0d3aa53d97ef1312) | Resuming background music. |
| [setAllMusicVolume](https://www.tencentcloud.com/document/product/647/50773#ba5ca3fa89c2c6200e1d5065a0f91e4a) | Setting the local and remote playback volume of background music. |
| [setMusicPublishVolume](https://www.tencentcloud.com/document/product/647/50773#b627e25338fa8c8539be389a9725bc82) | Setting the remote playback volume of a specific music track. |
| [setMusicPlayoutVolume](https://www.tencentcloud.com/document/product/647/50773#967877f3fb37950e281ee618a1b2b778) | Setting the local playback volume of a specific music track. |
| [setMusicPitch](https://www.tencentcloud.com/document/product/647/50773#ff5c217848d5ef6d6a7dab5367529013) | Adjusting the pitch of background music. |
| [setMusicSpeedRate](https://www.tencentcloud.com/document/product/647/50773#eed882f556c1504fcac185b16de63e6c) | Changing the speed of background music. |
| [getMusicCurrentPosInMS](https://www.tencentcloud.com/document/product/647/50773#1a204f26c0098cbd37620587ca957613) | Getting the playback progress (ms) of background music. |
| [getMusicDurationInMS](https://www.tencentcloud.com/document/product/647/50773#9ad2a04d0e58d8a522c99c34f9c3e3fb) | Getting the total length (ms) of background music. |
| [seekMusicToPosInTime](https://www.tencentcloud.com/document/product/647/50773#ff4023335909d5f2e340da1bf261cf83) | Setting the playback progress (ms) of background music. |
| [setMusicScratchSpeedRate](https://www.tencentcloud.com/document/product/647/50773#be170f854565a69c739b4b6b3f4564e9) | Adjust the speed change effect of the scratch disc. |
| [setPreloadObserver](https://www.tencentcloud.com/document/product/647/50773#e1b6e2bc56c578665b95a2136811f036) | Setting music preload callback. |
| [preloadMusic](https://www.tencentcloud.com/document/product/647/50773#342eee5266978a1d609ae10cc0e05dc8) | Preload background music. |
| [getMusicTrackCount](https://www.tencentcloud.com/document/product/647/50773#d54ff7c549f20eee445120d68fc1f354) | Get the number of tracks of background music. |
| [setMusicTrack](https://www.tencentcloud.com/document/product/647/50773#4bf48f6bde1b5f585fbfbfd622c69971) | Specify the playback track of background music. |

## StructType

| FuncList | DESC |
| --- | --- |
| [AudioMusicParam](https://www.tencentcloud.com/document/product/647/50773#79f73cf8c10624089eddf7856fdb22c7) | Background music playback information. |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50773#b9abfb68de51b5a85074406dbe956cbf) | Reverb effects. |
| [TXVoiceChangerType](https://www.tencentcloud.com/document/product/647/50773#304317cef161787ccdd1a097d73e7861) | Voice changing effects. |

## onLoadProgress

**onLoadProgress**

| void onLoadProgress | (int id |
| --- | --- |
|  | int progress) |

**Background music preload progress.**

## onLoadError

**onLoadError**

| void onLoadError | (int id |
| --- | --- |
|  | int errorCode) |

**Background music preload error.**

| Param | DESC |
| --- | --- |
| errorCode | -4001: Failed to open the file, such as invalid data found when processing input, ffmpeg protocol not found, etc; -4002: Decoding failure, such as audio file corruption, inaccessible network audio file server, etc; -4003: The number of preloads exceeded the limitï¼Please call stopPlayMusic first to release the useless preloadï¼-4005: Invalid path, Please check whether the path you passed points to a legal music fileï¼-4006: Invalid URL, Please use a browser to check whether the URL address you passed in can download the desired music fileï¼-4007: No audio stream, Please confirm whether the file you passed is a legal audio file and whether the file is damagedï¼-4008: Unsupported format, Please confirm whether the file format you passed is a supported file format. The mobile version supports [mp3, aac, m4a, wav, ogg, mp4, mkv], and the desktop version supports [mp3, aac, m4a, wav, mp4, mkv]. |

## onStart

**onStart**

| void onStart | (int id |
| --- | --- |
|  | int errCode) |

**Background music started.**

Called after the background music starts.

| Param | DESC |
| --- | --- |
| errCode | 0: Start playing successfully; -4001: Failed to open the file, such as invalid data found when processing input, ffmpeg protocol not found, etc; -4005: Invalid path, Please check whether the path you passed points to a legal music fileï¼-4006: Invalid URL, Please use a browser to check whether the URL address you passed in can download the desired music file. If the operating system is iOS or MacOS, please ensure the use of HTTPS linksï¼-4007: No audio stream, Please confirm whether the file you passed is a legal audio file and whether the file is damagedï¼-4008: Unsupported format, Please confirm whether the file format you passed is a supported file format. The mobile version supports [mp3, aac, m4a, wav, ogg, mp4, mkv], and the desktop version supports [mp3, aac, m4a, wav, mp4, mkv]; -4009: The number of concurrent BGM playbacks has exceeded the limit. This error occurs when more than 10 BGMs are playing simultaneously. Please check the number of concurrent BGM playbacks. |
| id | music ID. |

## onPlayProgress

**onPlayProgress**

| void onPlayProgress | (int id |
| --- | --- |
|  | long curPtsMS |
|  | long durationMS) |

**Playback progress of background music.**

## onComplete

**onComplete**

| void onComplete | (int id |
| --- | --- |
|  | int errCode) |

**Background music ended.**

Called when the background music playback ends or an error occurs.

| Param | DESC |
| --- | --- |
| errCode | 0: End of play; -4002: Decoding failure, such as audio file corruption, inaccessible network audio file server, etc. |
| id | music ID. |

## enableVoiceEarMonitor

**enableVoiceEarMonitor**

| void enableVoiceEarMonitor | (bool enable) |
| --- | --- |

**Enabling in-ear monitoring.**

After enabling in-ear monitoring, anchors can hear in earphones their own voice captured by the mic. This is designed for singing scenarios.

In-ear monitoring cannot be enabled for Bluetooth earphones. This is because Bluetooth earphones have high latency. Please ask anchors to use wired earphones via a UI reminder.

Given that not all phones deliver excellent in-ear monitoring effects, we have blocked this feature on some phones.

| Param | DESC |
| --- | --- |
| enable | ` true: ` enable; ` false `: disable |

> **Note**In-ear monitoring can be enabled only when earphones are used. Please remind anchors to use wired earphones.

## setVoiceEarMonitorVolume

**setVoiceEarMonitorVolume**

| void setVoiceEarMonitorVolume | (int volume) |
| --- | --- |

**Setting in-ear monitoring volume.**

This API is used to set the volume of in-ear monitoring.

| Param | DESC |
| --- | --- |
| volume | Volume. Value range: [0, 150]; default: 100 |

> **Note**The volume of the ear monitor is one of the most important factors affecting the user experience. Considering that different users have different sensitivities to volume, it is strongly recommended to provide a ear monitor volume adjustment slider on the UI interface. The recommended adjustment range is between 0 and 150. The gain effect of 100-150 is very helpful for some Android phones with low recording volume.

## setVoiceReverbType

**setVoiceReverbType**

| void setVoiceReverbType | ([TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50773#b9abfb68de51b5a85074406dbe956cbf) type) |
| --- | --- |

**Setting voice reverb effects.**

This API is used to set reverb effects for human voice. For the effects supported, please see [TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50773#b9abfb68de51b5a85074406dbe956cbf).

> **Note**Effects become invalid after room exit. If you want to use the same effect after you enter the room again, you need to set the effect again using this API.

## setVoiceChangerType

**setVoiceChangerType**

| void setVoiceChangerType | ([TXVoiceChangerType](https://www.tencentcloud.com/document/product/647/50773#304317cef161787ccdd1a097d73e7861) type) |
| --- | --- |

**Setting voice changing effects.**

This API is used to set voice changing effects. For the effects supported, please see [TXVoiceChangeType](https://www.tencentcloud.com/document/product/647/50773#304317cef161787ccdd1a097d73e7861).

> **Note**Effects become invalid after room exit. If you want to use the same effect after you enter the room again, you need to set the effect again using this API.

## setVoiceCaptureVolume

**setVoiceCaptureVolume**

| void setVoiceCaptureVolume | (int volume) |
| --- | --- |

**Setting speech volume.**

This API is used to set the volume of speech. It is often used together with the music volume setting API [setAllMusicVolume](https://www.tencentcloud.com/document/product/647/50773#ba5ca3fa89c2c6200e1d5065a0f91e4a) to balance between the volume of music and speech.

| Param | DESC |
| --- | --- |
| volume | Volume. Value range: [0, 150]; default: 100 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setVoicePitch

**setVoicePitch**

| void setVoicePitch | (double pitch) |
| --- | --- |

**Setting speech pitch.**

This API is used to set the pitch of speech.

| Param | DESC |
| --- | --- |
| pitch | Ptichï¼Value range: [-1.0f, 1.0f]; default: 0.0fã |

## setMusicObserver

**setMusicObserver**

| void setMusicObserver | (int musicId |
| --- | --- |
|  | [ITXMusicPlayObserver](https://www.tencentcloud.com/document/product/647/50773#8bc42ffc210c9d2b244908a2c914e2d8)* observer) |

**Setting the background music callback.**

Before playing background music, please use this API to set the music callback, which can inform you of the playback progress.

| Param | DESC |
| --- | --- |
| musicId | Music ID |
| observer | For more information, please see the APIs defined in ` ITXMusicPlayObserver `. |

> **Note**1. If the ID does not need to be used, the observer can be set to NULL to release it completely.

## startPlayMusic

**startPlayMusic**

| void startPlayMusic | ([AudioMusicParam](https://www.tencentcloud.com/document/product/647/50773#79f73cf8c10624089eddf7856fdb22c7) musicParam) |
| --- | --- |

**Starting background music.**

You must assign an ID to each music track so that you can start, stop, or set the volume of music tracks by ID.

| Param | DESC |
| --- | --- |
| musicParam | Music parameter |

> **Note**1. If you play the same music track multiple times, please use the same ID instead of a separate ID for each playback.2. If you want to play different music tracks at the same time, use different IDs for them.3. If you use the same ID to play a music track different from the current one, the SDK will stop the current one before playing the new one.

## stopPlayMusic

**stopPlayMusic**

| void stopPlayMusic | (int id) |
| --- | --- |

**Stopping background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

## pausePlayMusic

**pausePlayMusic**

| void pausePlayMusic | (int id) |
| --- | --- |

**Pausing background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

## resumePlayMusic

**resumePlayMusic**

| void resumePlayMusic | (int id) |
| --- | --- |

**Resuming background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

## setAllMusicVolume

**setAllMusicVolume**

| void setAllMusicVolume | (int volume) |
| --- | --- |

**Setting the local and remote playback volume of background music.**

This API is used to set the local and remote playback volume of background music.

- Local volume: the volume of music heard by anchors
- Remote volume: the volume of music heard by audience

| Param | DESC |
| --- | --- |
| volume | Volume. Value range: [0, 150]; default: 60 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setMusicPublishVolume

**setMusicPublishVolume**

| void setMusicPublishVolume | (int id |
| --- | --- |
|  | int volume) |

**Setting the remote playback volume of a specific music track.**

This API is used to control the remote playback volume (the volume heard by audience) of a specific music track.

| Param | DESC |
| --- | --- |
| id | Music ID |
| volume | Volume. Value range: [0, 150]; default: 60 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setMusicPlayoutVolume

**setMusicPlayoutVolume**

| void setMusicPlayoutVolume | (int id |
| --- | --- |
|  | int volume) |

**Setting the local playback volume of a specific music track.**

This API is used to control the local playback volume (the volume heard by anchors) of a specific music track.

| Param | DESC |
| --- | --- |
| id | Music ID |
| volume | Volume. Value range: [0, 150]. default: 60 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setMusicPitch

**setMusicPitch**

| void setMusicPitch | (int id |
| --- | --- |
|  | float pitch) |

**Adjusting the pitch of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| pitch | Pitch. Value range: floating point numbers in the range of [-1, 1]; default: 0.0f |

## setMusicSpeedRate

**setMusicSpeedRate**

| void setMusicSpeedRate | (int id |
| --- | --- |
|  | float speedRate) |

**Changing the speed of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| speedRate | Music speed. Value range: floating point numbers in the range of [0.5, 2]; default: 1.0f |

## getMusicCurrentPosInMS

**getMusicCurrentPosInMS**

| long getMusicCurrentPosInMS | (int id) |
| --- | --- |

**Getting the playback progress (ms) of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

**Return Desc:**

The milliseconds that have passed since playback started. -1 indicates failure to get the the playback progress.

## getMusicDurationInMS

**getMusicDurationInMS**

| long getMusicDurationInMS | (char* path) |
| --- | --- |

**Getting the total length (ms) of background music.**

| Param | DESC |
| --- | --- |
| path | Path of the music file. |

**Return Desc:**

The length of the specified music file is returned. -1 indicates failure to get the length.

## seekMusicToPosInTime

**seekMusicToPosInTime**

| void seekMusicToPosInTime | (int id |
| --- | --- |
|  | int pts) |

**Setting the playback progress (ms) of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| pts | Unit: millisecond |

> **Note**Do not call this API frequently as the music file may be read and written to each time the API is called, which can be time-consuming.Wait till users finish dragging the progress bar before you call this API.The progress bar controller on the UI tends to update the progress at a high frequency as users drag the progress bar. This will result in poor user experience unless you limit the frequency.

## setMusicScratchSpeedRate

**setMusicScratchSpeedRate**

| void setMusicScratchSpeedRate | (int id |
| --- | --- |
|  | float scratchSpeedRate) |

**Adjust the speed change effect of the scratch disc.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| scratchSpeedRate | Scratch disc speed, the default value is 1.0f, the range is: a floating point number between [-12.0 ~ 12.0], the positive/negative speed value indicates the direction is positive/negative, and the absolute value indicates the speed. |

> **Note**Precondition preloadMusic succeeds.

## setPreloadObserver

**setPreloadObserver**

| void setPreloadObserver | ([ITXMusicPreloadObserver](https://www.tencentcloud.com/document/product/647/50773#98bf86ba1dcb3a8c0b7974bb09d50430)* observer) |
| --- | --- |

**Setting music preload callback.**

Before preload music, please use this API to set the preload callback, which can inform you of the preload status.

| Param | DESC |
| --- | --- |
| observer | For more information, please see the APIs defined in TXMusicPreloadObserver. |

## preloadMusic

**preloadMusic**

| void preloadMusic | ([AudioMusicParam](https://www.tencentcloud.com/document/product/647/50773#79f73cf8c10624089eddf7856fdb22c7) preloadParam) |
| --- | --- |

**Preload background music.**

You must assign an ID to each music track so that you can start, stop, or set the volume of music tracks by ID.

| Param | DESC |
| --- | --- |
| musicParam | Music parameter |

> **Note**1. Preload supports up to 2 preloads with different IDs at the same time, and the preload time does not exceed 10 minutes,you need to call [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50773#be8c49a0723691a13da9d0b1a21ad6ab) API after use, otherwise the memory will not be released.2. If the music corresponding to the ID is being played, the preloading fails, and [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50773#be8c49a0723691a13da9d0b1a21ad6ab) must be called first.3. When the ` musicParam ` passed to [startPlayMusic](https://www.tencentcloud.com/document/product/647/50773#aacead5ce840018e0505825e2b942052) is exactly the same, preloading works.

## getMusicTrackCount

**getMusicTrackCount**

| long getMusicTrackCount | (int id) |
| --- | --- |

**Get the number of tracks of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

## setMusicTrack

**setMusicTrack**

| void setMusicTrack | (int id |
| --- | --- |
|  | int trackIndex) |

**Specify the playback track of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| index | Specify which track to play (the first track is played by default). Value range [0, total number of tracks). |

> **Note**The total number of tracks can be obtained through the [getMusicTrackCount](https://www.tencentcloud.com/document/product/647/50773#d54ff7c549f20eee445120d68fc1f354) interface.

## TXVoiceReverbType

**TXVoiceReverbType**

**Reverb effects.**

Reverb effects can be applied to human voice. Based on acoustic algorithms, they can mimic voice in different environments. The following effects are supported currently:

0: original; 1: karaoke; 2: room; 3: hall; 4: low and deep; 5: resonant; 6: metal; 7: husky; 8: ethereal; 9: studio; 10: melodious; 11: studio2;

| Enum | Value | DESC |
| --- | --- | --- |
| TXLiveVoiceReverbType_0 | 0 | disable |
| TXLiveVoiceReverbType_1 | 1 | KTV |
| TXLiveVoiceReverbType_2 | 2 | small room |
| TXLiveVoiceReverbType_3 | 3 | great hall |
| TXLiveVoiceReverbType_4 | 4 | deep voice |
| TXLiveVoiceReverbType_5 | 5 | loud voice |
| TXLiveVoiceReverbType_6 | 6 | metallic sound |
| TXLiveVoiceReverbType_7 | 7 | magnetic sound |
| TXLiveVoiceReverbType_8 | 8 | ethereal |
| TXLiveVoiceReverbType_9 | 9 | studio |
| TXLiveVoiceReverbType_10 | 10 | melodious |
| TXLiveVoiceReverbType_11 | 11 | studio2 |

## TXVoiceChangeType

**TXVoiceChangeType**

**Voice changing effects.**

Voice changing effects can be applied to human voice. Based on acoustic algorithms, they change the tone of voice. The following effects are supported currently:

0: original; 1: child; 2: little girl; 3: middle-aged man; 4: metal; 5: nasal; 6: foreign accent; 7: trapped beast; 8: otaku; 9: electric; 10: robot; 11: ethereal; 12: pig king; 13: hulk

| Enum | Value | DESC |
| --- | --- | --- |
| TXVoiceChangerType_0 | 0 | disable |
| TXVoiceChangerType_1 | 1 | naughty kid |
| TXVoiceChangerType_2 | 2 | Lolita |
| TXVoiceChangerType_3 | 3 | uncle |
| TXVoiceChangerType_4 | 4 | heavy metal |
| TXVoiceChangerType_5 | 5 | catch cold |
| TXVoiceChangerType_6 | 6 | foreign accent |
| TXVoiceChangerType_7 | 7 | caged animal trapped beast |
| TXVoiceChangerType_8 | 8 | indoorsman |
| TXVoiceChangerType_9 | 9 | strong current |
| TXVoiceChangerType_10 | 10 | heavy machinery |
| TXVoiceChangerType_11 | 11 | intangible |
| TXVoiceChangerType_12 | 12 | pig king |
| TXVoiceChangerType_13 | 13 | hulk |

## TXAudioMusicParam

**TXAudioMusicParam**

**Background music playback information.**

The information, including playback ID, file path, and loop times, is passed in the [startPlayMusic](https://www.tencentcloud.com/document/product/647/50773#aacead5ce840018e0505825e2b942052) API.

1. If you play the same music track multiple times, please use the same ID instead of a separate ID for each playback.

2. If you want to play different music tracks at the same time, use different IDs for them.

3. If you use the same ID to play a music track different from the current one, the SDK will stop the current one before playing the new one.

| EnumType | DESC |
| --- | --- |
| endTimeMS | ` Field description: ` the point in time in milliseconds for ending music playback. 0 indicates that playback continues till the end of the music track. |
| id | ` Field description: ` music ID**Note**the SDK supports playing multiple music tracks. IDs are used to distinguish different music tracks and control their start, end, volume, etc. |
| isShortFile | ` Field description: ` whether the music played is a short music track` Valid values: `` true `: short music track that needs to be looped; ` false ` (default): normal-length music track |
| loopCount | ` Field description: ` number of times the music track is looped` Valid values: `0 or any positive integer. 0 (default) indicates that the music is played once, 1 twice, and so on. |
| path | ` Field description: ` absolute path of the music file or url.the mp3,aac,m4a,wav supported. |
| publish | ` Field description: ` whether to send the music to remote users` Valid values: `` true `: remote users can hear the music played locally; ` false ` (default): only the local user can hear the music. |
| startTimeMS | ` Field description: ` the point in time in milliseconds for starting music playback |


---
*Source: [https://trtc.io/document/50773](https://trtc.io/document/50773)*
