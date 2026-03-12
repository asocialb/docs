# TXAudioEffectManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: management class for background music, short audio effects, and voice effects

Description: sets background music, short audio effects, and voice effects

**TXAudioEffectManager**

## TXMusicPreloadObserver

| FuncList | DESC |
| --- | --- |
| [onLoadProgress](https://www.tencentcloud.com/document/product/647/50765#072926b93551b1af8dbb1fbb3d087004) | Background music preload progress. |
| [onLoadError](https://www.tencentcloud.com/document/product/647/50765#f3989bff41bf5801b07d181cc72845ec) | Background music preload error. |

## TXMusicPlayObserver

| FuncList | DESC |
| --- | --- |
| [onStart](https://www.tencentcloud.com/document/product/647/50765#8a783933a586aee9a5302b57740b11ea) | Background music started. |
| [onPlayProgress](https://www.tencentcloud.com/document/product/647/50765#75e96d61252e138c16469318e54e86a3) | Playback progress of background music. |
| [onComplete](https://www.tencentcloud.com/document/product/647/50765#2e16ac103491244a957557a26325b408) | Background music ended. |

## TXAudioEffectManager

| FuncList | DESC |
| --- | --- |
| [enableVoiceEarMonitor](https://www.tencentcloud.com/document/product/647/50765#889cc3da70a6c0820633bc197ed2b2a3) | Enabling in-ear monitoring. |
| [setVoiceEarMonitorVolume](https://www.tencentcloud.com/document/product/647/50765#7d600f2108d854b2b3230304156058f0) | Setting in-ear monitoring volume. |
| [setVoiceReverbType](https://www.tencentcloud.com/document/product/647/50765#56f1d6a2079ce56b75781a4ffcf5347a) | Setting voice reverb effects. |
| [setVoiceChangerType](https://www.tencentcloud.com/document/product/647/50765#407622eca1ec0c089ac0db6a699f11fa) | Setting voice changing effects. |
| [setVoiceCaptureVolume](https://www.tencentcloud.com/document/product/647/50765#c881a67177f8396b70c2abf117036381) | Setting speech volume. |
| [setVoicePitch](https://www.tencentcloud.com/document/product/647/50765#fd4b19b0a1bc40aa8e8dc8070d96a68f) | Setting speech pitch. |
| [setMusicObserver](https://www.tencentcloud.com/document/product/647/50765#fc6d76f7ebe087957ba81a5ee62710b0) | Setting the background music callback. |
| [startPlayMusic](https://www.tencentcloud.com/document/product/647/50765#e7b176192e2cf33abe2bd18618ad6bc1) | Starting background music. |
| [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50765#35e1e5bd5b10eb63b6313fd95b95580b) | Stopping background music. |
| [pausePlayMusic](https://www.tencentcloud.com/document/product/647/50765#2ee1a37638877d7041493a7ce1402077) | Pausing background music. |
| [resumePlayMusic](https://www.tencentcloud.com/document/product/647/50765#dfcbb473c7ddfe6b0028e1d318ed8ff3) | Resuming background music. |
| [setAllMusicVolume](https://www.tencentcloud.com/document/product/647/50765#01e8b8f4cb30d56b50e931c2857d7754) | Setting the local and remote playback volume of background music. |
| [setMusicPublishVolume](https://www.tencentcloud.com/document/product/647/50765#fc3c4bf5f3c047d05371ddd6c8aa87d9) | Setting the remote playback volume of a specific music track. |
| [setMusicPlayoutVolume](https://www.tencentcloud.com/document/product/647/50765#d8911047524dead67735746adff09354) | Setting the local playback volume of a specific music track. |
| [setMusicPitch](https://www.tencentcloud.com/document/product/647/50765#c7f57592b0cbdc16bbac71310ebc88ae) | Adjusting the pitch of background music. |
| [setMusicSpeedRate](https://www.tencentcloud.com/document/product/647/50765#5245a320dc95f7031cf39fd21d80248e) | Changing the speed of background music. |
| [getMusicCurrentPosInMS](https://www.tencentcloud.com/document/product/647/50765#a3c50caad27c04e3f8c5535d4c669ffd) | Getting the playback progress (ms) of background music. |
| [getMusicDurationInMS](https://www.tencentcloud.com/document/product/647/50765#db1e65508258187a248abf436025f126) | Getting the total length (ms) of background music. |
| [seekMusicToPosInMS](https://www.tencentcloud.com/document/product/647/50765#505db77305b5d4ede7f93fcb4a79b1b5) | Setting the playback progress (ms) of background music. |
| [setMusicScratchSpeedRate](https://www.tencentcloud.com/document/product/647/50765#b0c8a792d1e8bab154063728086ad4db) | Adjust the speed change effect of the scratch disc. |
| [setPreloadObserver](https://www.tencentcloud.com/document/product/647/50765#6fee9439865a630a0e77991be80f0ab6) | Setting music preload callback. |
| [preloadMusic](https://www.tencentcloud.com/document/product/647/50765#9d6d01a8519d56c348853f2f2467d537) | Preload background music. |
| [getMusicTrackCount](https://www.tencentcloud.com/document/product/647/50765#30d19d232faa06d74b16bc04032fc9b4) | Get the number of tracks of background music. |
| [setMusicTrack](https://www.tencentcloud.com/document/product/647/50765#8dc4b355cd2af90de761cec9b9057937) | Specify the playback track of background music. |

## StructType

| FuncList | DESC |
| --- | --- |
| [AudioMusicParam](https://www.tencentcloud.com/document/product/647/50765#79f73cf8c10624089eddf7856fdb22c7) | Background music playback information. |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50765#b9abfb68de51b5a85074406dbe956cbf) | Reverb effects. |
| [TXVoiceChangerType](https://www.tencentcloud.com/document/product/647/50765#304317cef161787ccdd1a097d73e7861) | Voice changing effects. |

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

| void enableVoiceEarMonitor | (boolean enable) |
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

| void setVoiceReverbType | ([TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50765#b9abfb68de51b5a85074406dbe956cbf) type) |
| --- | --- |

**Setting voice reverb effects.**

This API is used to set reverb effects for human voice. For the effects supported, please see [TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50765#b9abfb68de51b5a85074406dbe956cbf).

> **Note**Effects become invalid after room exit. If you want to use the same effect after you enter the room again, you need to set the effect again using this API.

## setVoiceChangerType

**setVoiceChangerType**

| void setVoiceChangerType | ([TXVoiceChangerType](https://www.tencentcloud.com/document/product/647/50765#304317cef161787ccdd1a097d73e7861) type) |
| --- | --- |

**Setting voice changing effects.**

This API is used to set voice changing effects. For the effects supported, please see [TXVoiceChangeType](https://www.tencentcloud.com/document/product/647/50765#304317cef161787ccdd1a097d73e7861).

> **Note**Effects become invalid after room exit. If you want to use the same effect after you enter the room again, you need to set the effect again using this API.

## setVoiceCaptureVolume

**setVoiceCaptureVolume**

| void setVoiceCaptureVolume | (int volume) |
| --- | --- |

**Setting speech volume.**

This API is used to set the volume of speech. It is often used together with the music volume setting API [setAllMusicVolume](https://www.tencentcloud.com/document/product/647/50765#01e8b8f4cb30d56b50e931c2857d7754) to balance between the volume of music and speech.

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

| void setMusicObserver | (int id |
| --- | --- |
|  | [TXMusicPlayObserver](https://www.tencentcloud.com/document/product/647/50765#90fe82030e495380f36f43b0b80e941b) observer) |

**Setting the background music callback.**

Before playing background music, please use this API to set the music callback, which can inform you of the playback progress.

| Param | DESC |
| --- | --- |
| musicId | Music ID |
| observer | For more information, please see the APIs defined in ` ITXMusicPlayObserver `. |

> **Note**1. If the ID does not need to be used, the observer can be set to NULL to release it completely.

## startPlayMusic

**startPlayMusic**

| boolean startPlayMusic | (final [AudioMusicParam](https://www.tencentcloud.com/document/product/647/50765#79f73cf8c10624089eddf7856fdb22c7) musicParam) |
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

| long getMusicDurationInMS | (String path) |
| --- | --- |

**Getting the total length (ms) of background music.**

| Param | DESC |
| --- | --- |
| path | Path of the music file. |

**Return Desc:**

The length of the specified music file is returned. -1 indicates failure to get the length.

## seekMusicToPosInMS

**seekMusicToPosInMS**

| void seekMusicToPosInMS | (int id |
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

| void setPreloadObserver | ([TXMusicPreloadObserver](https://www.tencentcloud.com/document/product/647/50765#1f2269f801c48a2d4d262b38d8f924d4) observer) |
| --- | --- |

**Setting music preload callback.**

Before preload music, please use this API to set the preload callback, which can inform you of the preload status.

| Param | DESC |
| --- | --- |
| observer | For more information, please see the APIs defined in [TXMusicPreloadObserver](https://www.tencentcloud.com/document/product/647/50765#1f2269f801c48a2d4d262b38d8f924d4). |

## preloadMusic

**preloadMusic**

| boolean preloadMusic | (final [AudioMusicParam](https://www.tencentcloud.com/document/product/647/50765#79f73cf8c10624089eddf7856fdb22c7) preloadParam) |
| --- | --- |

**Preload background music.**

You must assign an ID to each music track so that you can start, stop, or set the volume of music tracks by ID.

| Param | DESC |
| --- | --- |
| musicParam | Music parameter |

> **Note**1. Preload supports up to 2 preloads with different IDs at the same time, and the preload time does not exceed 10 minutes,you need to call [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50765#35e1e5bd5b10eb63b6313fd95b95580b) API after use, otherwise the memory will not be released.2. If the music corresponding to the ID is being played, the preloading fails, and [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50765#35e1e5bd5b10eb63b6313fd95b95580b) must be called first.3. When the ` musicParam ` passed to [startPlayMusic](https://www.tencentcloud.com/document/product/647/50765#e7b176192e2cf33abe2bd18618ad6bc1) is exactly the same, preloading works.

## getMusicTrackCount

**getMusicTrackCount**

| int getMusicTrackCount | (int id) |
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

> **Note**The total number of tracks can be obtained through the [getMusicTrackCount](https://www.tencentcloud.com/document/product/647/50765#30d19d232faa06d74b16bc04032fc9b4) interface.

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
| TXLiveVoiceChangerType_0 | 0 | disable |
| TXLiveVoiceChangerType_1 | 1 | naughty kid |
| TXLiveVoiceChangerType_2 | 2 | Lolita |
| TXLiveVoiceChangerType_3 | 3 | uncle |
| TXLiveVoiceChangerType_4 | 4 | heavy metal |
| TXLiveVoiceChangerType_5 | 5 | catch cold |
| TXLiveVoiceChangerType_6 | 6 | foreign accent |
| TXLiveVoiceChangerType_7 | 7 | caged animal trapped beast |
| TXLiveVoiceChangerType_8 | 8 | indoorsman |
| TXLiveVoiceChangerType_9 | 9 | strong current |
| TXLiveVoiceChangerType_10 | 10 | heavy machinery |
| TXLiveVoiceChangerType_11 | 11 | intangible |
| TXLiveVoiceChangerType_12 | 12 | pig king |
| TXLiveVoiceChangerType_13 | 13 | hulk |

## TXAudioMusicParam

**TXAudioMusicParam**

**Background music playback information.**

The information, including playback ID, file path, and loop times, is passed in the [startPlayMusic](https://www.tencentcloud.com/document/product/647/50765#e7b176192e2cf33abe2bd18618ad6bc1) API.

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
*Source: [https://trtc.io/document/50765](https://trtc.io/document/50765)*
