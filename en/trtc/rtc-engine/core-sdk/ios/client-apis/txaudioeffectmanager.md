# TXAudioEffectManager

Copyright (c) 2021 Tencent. All rights reserved.

Module: management class for background music, short audio effects, and voice effects

Description: sets background music, short audio effects, and voice effects

**TXAudioEffectManager**

## TXAudioEffectManager

| FuncList | DESC |
| --- | --- |
| [enableVoiceEarMonitor:](https://www.tencentcloud.com/document/product/647/50757#300c68bccbf3480ab8c99cf2f31d014a) | Enabling in-ear monitoring. |
| [setVoiceEarMonitorVolume:](https://www.tencentcloud.com/document/product/647/50757#3857607a3e9b5fc2e57a77f2c1dd6359) | Setting in-ear monitoring volume. |
| [setVoiceReverbType:](https://www.tencentcloud.com/document/product/647/50757#7135a441f275bed8330db039f1bfba2d) | Setting voice reverb effects. |
| [setVoiceChangerType:](https://www.tencentcloud.com/document/product/647/50757#fee0da19f6060c0544e73a79da113bd0) | Setting voice changing effects. |
| [setVoiceVolume:](https://www.tencentcloud.com/document/product/647/50757#9fe5b02fc52fa9bfae721e1f0d4d9427) | Setting speech volume. |
| [setVoicePitch:](https://www.tencentcloud.com/document/product/647/50757#517e19882847820a81b870d49d1ae2f4) | Setting speech pitch. |
| [startPlayMusic:onStart:onProgress:onComplete:](https://www.tencentcloud.com/document/product/647/50757#3e6d92e47d6770c50e0e4ca4df429c31) | Starting background music. |
| [stopPlayMusic:](https://www.tencentcloud.com/document/product/647/50757#2214eecbdca5062136821aff0d95bfbe) | Stopping background music. |
| [pausePlayMusic:](https://www.tencentcloud.com/document/product/647/50757#8e5076dea4c4b43df4c07cf1fe4003f1) | Pausing background music. |
| [resumePlayMusic:](https://www.tencentcloud.com/document/product/647/50757#15f5b80077c596dc1d39402d421a6ec2) | Resuming background music. |
| [setAllMusicVolume:](https://www.tencentcloud.com/document/product/647/50757#8fafba6b1d27799ea32812f08f564ee5) | Setting the local and remote playback volume of background music. |
| [setMusicPublishVolume:volume:](https://www.tencentcloud.com/document/product/647/50757#50a9fe2dc5ee4a6f92160ef4f1367c13) | Setting the remote playback volume of a specific music track. |
| [setMusicPlayoutVolume:volume:](https://www.tencentcloud.com/document/product/647/50757#5ba979d09b84dfe360785c659ab7c8b7) | Setting the local playback volume of a specific music track. |
| [setMusicPitch:pitch:](https://www.tencentcloud.com/document/product/647/50757#6f7407593caa553bccee1da218e79d2e) | Adjusting the pitch of background music. |
| [setMusicSpeedRate:speedRate:](https://www.tencentcloud.com/document/product/647/50757#5a66bf1956d164a98f5f274f46b9c3a7) | Changing the speed of background music. |
| [getMusicCurrentPosInMS:](https://www.tencentcloud.com/document/product/647/50757#4d6f9629f7623102e3e04f5e05bdea1e) | Getting the playback progress (ms) of background music. |
| [getMusicDurationInMS:](https://www.tencentcloud.com/document/product/647/50757#6ca86334e6bf179bc3cfd98ca5e01975) | Getting the total length (ms) of background music. |
| [seekMusicToPosInMS:pts:](https://www.tencentcloud.com/document/product/647/50757#c00ed7c5735f4c126f0fbd099cae8998) | Setting the playback progress (ms) of background music. |
| [setMusicScratchSpeedRate:speedRate:](https://www.tencentcloud.com/document/product/647/50757#76ccca8d0e4ad4ef6ba3abc02170b18b) | Adjust the speed change effect of the scratch disc. |
| [preloadMusic:onProgress:onError:](https://www.tencentcloud.com/document/product/647/50757#c5a7017fe11985ad47ba9e935d726020) | Preload background music. |
| [getMusicTrackCount:](https://www.tencentcloud.com/document/product/647/50757#19fc33f9be59df8b0f4524219fbd4350) | Get the number of tracks of background music. |
| [setMusicTrack:track:](https://www.tencentcloud.com/document/product/647/50757#bcac516dcc63f775829e34f75646fdf4) | Specify the playback track of background music. |

## StructType

| FuncList | DESC |
| --- | --- |
| [TXAudioMusicParam](https://www.tencentcloud.com/document/product/647/50757#1b83f556d7876fc9f0ec4b5f8bea469c) | Background music playback information. |

## EnumType

| EnumType | DESC |
| --- | --- |
| [TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50757#b9abfb68de51b5a85074406dbe956cbf) | Reverb effects. |
| [TXVoiceChangeType](https://www.tencentcloud.com/document/product/647/50757#e6f03d6a29abd12b6ecc056432e40cc8) | Voice changing effects. |

## enableVoiceEarMonitor:

**enableVoiceEarMonitor:**

| - (void)enableVoiceEarMonitor: | (BOOL)enable |
| --- | --- |

**Enabling in-ear monitoring.**

After enabling in-ear monitoring, anchors can hear in earphones their own voice captured by the mic. This is designed for singing scenarios.

In-ear monitoring cannot be enabled for Bluetooth earphones. This is because Bluetooth earphones have high latency. Please ask anchors to use wired earphones via a UI reminder.

Given that not all phones deliver excellent in-ear monitoring effects, we have blocked this feature on some phones.

| Param | DESC |
| --- | --- |
| enable | ` YES: ` enable; ` NO `: disable |

> **Note**In-ear monitoring can be enabled only when earphones are used. Please remind anchors to use wired earphones.

## setVoiceEarMonitorVolume:

**setVoiceEarMonitorVolume:**

| - (void)setVoiceEarMonitorVolume: | (NSInteger)volume |
| --- | --- |

**Setting in-ear monitoring volume.**

This API is used to set the volume of in-ear monitoring.

| Param | DESC |
| --- | --- |
| volume | Volume. Value range: [0, 150]; default: 100 |

> **Note**The volume of the ear monitor is one of the most important factors affecting the user experience. Considering that different users have different sensitivities to volume, it is strongly recommended to provide a ear monitor volume adjustment slider on the UI interface. The recommended adjustment range is between 0 and 150. The gain effect of 100-150 is very helpful for some Android phones with low recording volume.

## setVoiceReverbType:

**setVoiceReverbType:**

| - (void)setVoiceReverbType: | ([TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50757#b9abfb68de51b5a85074406dbe956cbf))reverbType |
| --- | --- |

**Setting voice reverb effects.**

This API is used to set reverb effects for human voice. For the effects supported, please see [TXVoiceReverbType](https://www.tencentcloud.com/document/product/647/50757#b9abfb68de51b5a85074406dbe956cbf).

> **Note**Effects become invalid after room exit. If you want to use the same effect after you enter the room again, you need to set the effect again using this API.

## setVoiceChangerType:

**setVoiceChangerType:**

| - (void)setVoiceChangerType: | ([TXVoiceChangeType](https://www.tencentcloud.com/document/product/647/50757#e6f03d6a29abd12b6ecc056432e40cc8))changerType |
| --- | --- |

**Setting voice changing effects.**

This API is used to set voice changing effects. For the effects supported, please see [TXVoiceChangeType](https://www.tencentcloud.com/document/product/647/50757#e6f03d6a29abd12b6ecc056432e40cc8).

> **Note**Effects become invalid after room exit. If you want to use the same effect after you enter the room again, you need to set the effect again using this API.

## setVoiceVolume:

**setVoiceVolume:**

| - (void)setVoiceVolume: | (NSInteger)volume |
| --- | --- |

**Setting speech volume.**

This API is used to set the volume of speech. It is often used together with the music volume setting API [setAllMusicVolume](https://www.tencentcloud.com/document/product/647/50757#8fafba6b1d27799ea32812f08f564ee5) to balance between the volume of music and speech.

| Param | DESC |
| --- | --- |
| volume | Volume. Value range: [0, 150]; default: 100 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setVoicePitch:

**setVoicePitch:**

| -(void)setVoicePitch: | (double)pitch |
| --- | --- |

**Setting speech pitch.**

This API is used to set the pitch of speech.

| Param | DESC |
| --- | --- |
| pitch | Ptichï¼Value range: [-1.0f, 1.0f]; default: 0.0fã |

## startPlayMusic:onStart:onProgress:onComplete:

**startPlayMusic:onStart:onProgress:onComplete:**

| - (void)startPlayMusic: | ([TXAudioMusicParam](https://www.tencentcloud.com/document/product/647/50757#1b83f556d7876fc9f0ec4b5f8bea469c) *)musicParam |
| --- | --- |
| onStart: | (TXAudioMusicStartBlock _Nullable)startBlock |
| onProgress: | (TXAudioMusicProgressBlock _Nullable)progressBlock |
| onComplete: | (TXAudioMusicCompleteBlock _Nullable)completeBlock |

**Starting background music.**

You must assign an ID to each music track so that you can start, stop, or set the volume of music tracks by ID.

| Param | DESC |
| --- | --- |
| completeBlock | Callback of ending music |
| musicParam | Music parameter |
| progressBlock | Callback of playback progress |
| startBlock | Callback of starting music |

> **Note**1. If you play the same music track multiple times, please use the same ID instead of a separate ID for each playback.2. If you want to play different music tracks at the same time, use different IDs for them.3. If you use the same ID to play a music track different from the current one, the SDK will stop the current one before playing the new one.

## stopPlayMusic:

**stopPlayMusic:**

| - (void)stopPlayMusic: | (int32_t)id |
| --- | --- |

**Stopping background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

## pausePlayMusic:

**pausePlayMusic:**

| - (void)pausePlayMusic: | (int32_t)id |
| --- | --- |

**Pausing background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

## resumePlayMusic:

**resumePlayMusic:**

| - (void)resumePlayMusic: | (int32_t)id |
| --- | --- |

**Resuming background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

## setAllMusicVolume:

**setAllMusicVolume:**

| - (void)setAllMusicVolume: | (NSInteger)volume |
| --- | --- |

**Setting the local and remote playback volume of background music.**

This API is used to set the local and remote playback volume of background music.

- Local volume: the volume of music heard by anchors
- Remote volume: the volume of music heard by audience

| Param | DESC |
| --- | --- |
| volume | Volume. Value range: [0, 150]; default: 60 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setMusicPublishVolume:volume:

**setMusicPublishVolume:volume:**

| - (void)setMusicPublishVolume: | (int32_t)id |
| --- | --- |
| volume: | (NSInteger)volume |

**Setting the remote playback volume of a specific music track.**

This API is used to control the remote playback volume (the volume heard by audience) of a specific music track.

| Param | DESC |
| --- | --- |
| id | Music ID |
| volume | Volume. Value range: [0, 150]; default: 60 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setMusicPlayoutVolume:volume:

**setMusicPlayoutVolume:volume:**

| - (void)setMusicPlayoutVolume: | (int32_t)id |
| --- | --- |
| volume: | (NSInteger)volume |

**Setting the local playback volume of a specific music track.**

This API is used to control the local playback volume (the volume heard by anchors) of a specific music track.

| Param | DESC |
| --- | --- |
| id | Music ID |
| volume | Volume. Value range: [0, 150]. default: 60 |

> **Note**If 100 is still not loud enough for you, you can set the volume to up to 150, but there may be side effects.

## setMusicPitch:pitch:

**setMusicPitch:pitch:**

| - (void)setMusicPitch: | (int32_t)id |
| --- | --- |
| pitch: | (double)pitch |

**Adjusting the pitch of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| pitch | Pitch. Value range: floating point numbers in the range of [-1, 1]; default: 0.0f |

## setMusicSpeedRate:speedRate:

**setMusicSpeedRate:speedRate:**

| - (void)setMusicSpeedRate: | (int32_t)id |
| --- | --- |
| speedRate: | (double)speedRate |

**Changing the speed of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| speedRate | Music speed. Value range: floating point numbers in the range of [0.5, 2]; default: 1.0f |

## getMusicCurrentPosInMS:

**getMusicCurrentPosInMS:**

| - (NSInteger)getMusicCurrentPosInMS: | (int32_t)id |
| --- | --- |

**Getting the playback progress (ms) of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

**Return Desc:**

The milliseconds that have passed since playback started. -1 indicates failure to get the the playback progress.

## getMusicDurationInMS:

**getMusicDurationInMS:**

| - (NSInteger)getMusicDurationInMS: | (NSString *)path |
| --- | --- |

**Getting the total length (ms) of background music.**

| Param | DESC |
| --- | --- |
| path | Path of the music file. |

**Return Desc:**

The length of the specified music file is returned. -1 indicates failure to get the length.

## seekMusicToPosInMS:pts:

**seekMusicToPosInMS:pts:**

| - (void)seekMusicToPosInMS: | (int32_t)id |
| --- | --- |
| pts: | (NSInteger)pts |

**Setting the playback progress (ms) of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| pts | Unit: millisecond |

> **Note**Do not call this API frequently as the music file may be read and written to each time the API is called, which can be time-consuming.Wait till users finish dragging the progress bar before you call this API.The progress bar controller on the UI tends to update the progress at a high frequency as users drag the progress bar. This will result in poor user experience unless you limit the frequency.

## setMusicScratchSpeedRate:speedRate:

**setMusicScratchSpeedRate:speedRate:**

| - (void)setMusicScratchSpeedRate: | (int32_t)id |
| --- | --- |
| speedRate: | (double)scratchSpeedRate |

**Adjust the speed change effect of the scratch disc.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| scratchSpeedRate | Scratch disc speed, the default value is 1.0f, the range is: a floating point number between [-12.0 ~ 12.0], the positive/negative speed value indicates the direction is positive/negative, and the absolute value indicates the speed. |

> **Note**Precondition preloadMusic succeeds.

## preloadMusic:onProgress:onError:

**preloadMusic:onProgress:onError:**

| - (void)preloadMusic: | ([TXAudioMusicParam](https://www.tencentcloud.com/document/product/647/50757#1b83f556d7876fc9f0ec4b5f8bea469c) *)preloadParam |
| --- | --- |
| onProgress: | (TXMusicPreloadProgressBlock _Nullable)progressBlock |
| onError: | (TXMusicPreloadErrorBlock _Nullable)errorBlock |

**Preload background music.**

You must assign an ID to each music track so that you can start, stop, or set the volume of music tracks by ID.

| Param | DESC |
| --- | --- |
| musicParam | Music parameter |

> **Note**1. Preload supports up to 2 preloads with different IDs at the same time, and the preload time does not exceed 10 minutes,you need to call [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50757#2214eecbdca5062136821aff0d95bfbe) API after use, otherwise the memory will not be released.2. If the music corresponding to the ID is being played, the preloading fails, and [stopPlayMusic](https://www.tencentcloud.com/document/product/647/50757#2214eecbdca5062136821aff0d95bfbe) must be called first.3. When the ` musicParam ` passed to [startPlayMusic](https://www.tencentcloud.com/document/product/647/50757#3e6d92e47d6770c50e0e4ca4df429c31) is exactly the same, preloading works.

## getMusicTrackCount:

**getMusicTrackCount:**

| - (NSInteger)getMusicTrackCount: | (int32_t)id |
| --- | --- |

**Get the number of tracks of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |

## setMusicTrack:track:

**setMusicTrack:track:**

| - (void)setMusicTrack: | (int32_t)id |
| --- | --- |
| track: | (NSInteger)track |

**Specify the playback track of background music.**

| Param | DESC |
| --- | --- |
| id | Music ID |
| index | Specify which track to play (the first track is played by default). Value range [0, total number of tracks). |

> **Note**The total number of tracks can be obtained through the [getMusicTrackCount](https://www.tencentcloud.com/document/product/647/50757#19fc33f9be59df8b0f4524219fbd4350) interface.

## TXVoiceReverbType

**TXVoiceReverbType**

**Reverb effects.**

Reverb effects can be applied to human voice. Based on acoustic algorithms, they can mimic voice in different environments. The following effects are supported currently:

0: original; 1: karaoke; 2: room; 3: hall; 4: low and deep; 5: resonant; 6: metal; 7: husky; 8: ethereal; 9: studio; 10: melodious; 11: studio2;

| Enum | Value | DESC |
| --- | --- | --- |
| TXVoiceReverbType_0 | 0 | disable |
| TXVoiceReverbType_1 | 1 | KTV |
| TXVoiceReverbType_2 | 2 | small room |
| TXVoiceReverbType_3 | 3 | great hall |
| TXVoiceReverbType_4 | 4 | deep voice |
| TXVoiceReverbType_5 | 5 | loud voice |
| TXVoiceReverbType_6 | 6 | metallic sound |
| TXVoiceReverbType_7 | 7 | magnetic sound |
| TXVoiceReverbType_8 | 8 | ethereal |
| TXVoiceReverbType_9 | 9 | studio |
| TXVoiceReverbType_10 | 10 | melodious |
| TXVoiceReverbType_11 | 11 | studio2 |

## TXVoiceChangeType

**TXVoiceChangeType**

**Voice changing effects.**

Voice changing effects can be applied to human voice. Based on acoustic algorithms, they change the tone of voice. The following effects are supported currently:

0: original; 1: child; 2: little girl; 3: middle-aged man; 4: metal; 5: nasal; 6: foreign accent; 7: trapped beast; 8: otaku; 9: electric; 10: robot; 11: ethereal; 12: pig king; 13: hulk

| Enum | Value | DESC |
| --- | --- | --- |
| TXVoiceChangeType_0 | 0 | disable |
| TXVoiceChangeType_1 | 1 | naughty kid |
| TXVoiceChangeType_2 | 2 | Lolita |
| TXVoiceChangeType_3 | 3 | uncle |
| TXVoiceChangeType_4 | 4 | heavy metal |
| TXVoiceChangeType_5 | 5 | catch cold |
| TXVoiceChangeType_6 | 6 | foreign accent |
| TXVoiceChangeType_7 | 7 | caged animal trapped beast |
| TXVoiceChangeType_8 | 8 | indoorsman |
| TXVoiceChangeType_9 | 9 | strong current |
| TXVoiceChangeType_10 | 10 | heavy machinery |
| TXVoiceChangeType_11 | 11 | intangible |
| TXVoiceChangeType_12 | 12 | pig king |
| TXVoiceChangeType_13 | 13 | hulk |

## TXAudioMusicParam

**TXAudioMusicParam**

**Background music playback information.**

The information, including playback ID, file path, and loop times, is passed in the [startPlayMusic](https://www.tencentcloud.com/document/product/647/50757#3e6d92e47d6770c50e0e4ca4df429c31) API.

1. If you play the same music track multiple times, please use the same ID instead of a separate ID for each playback.

2. If you want to play different music tracks at the same time, use different IDs for them.

3. If you use the same ID to play a music track different from the current one, the SDK will stop the current one before playing the new one.

| EnumType | DESC |
| --- | --- |
| ID | ` Field description: ` music ID**Note**the SDK supports playing multiple music tracks. IDs are used to distinguish different music tracks and control their start, end, volume, etc. |
| endTimeMS | ` Field description: ` the point in time in milliseconds for ending music playback. 0 indicates that playback continues till the end of the music track. |
| isShortFile | ` Field description: ` whether the music played is a short music track` Valid values: `` YES `: short music track that needs to be looped; ` NO ` (default): normal-length music track |
| loopCount | ` Field description: ` number of times the music track is looped` Valid values: `0 or any positive integer. 0 (default) indicates that the music is played once, 1 twice, and so on. |
| path | ` Field description: ` absolute path of the music file or url.the mp3,aac,m4a,wav supported. |
| publish | ` Field description: ` whether to send the music to remote users` Valid values: `` YES ` (default): remote users can hear the music played locally; ` NO `: only the local user can hear the music. |
| startTimeMS | ` Field description: ` the point in time in milliseconds for starting music playback |


---
*Source: [https://trtc.io/document/50757](https://trtc.io/document/50757)*
