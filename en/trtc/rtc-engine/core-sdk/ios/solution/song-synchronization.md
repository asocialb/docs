# Song Synchronization

Real-time synchronization of song progress is required in the real-time solution to avoid increasing end-to-end delay due to song errors after the start of the performance. Synchronizing the song requires using NTP time. The local clocks of different devices are not consistent and there is a certain error, so Tencent Cloud's self-developed NTP service needs to be introduced. At the same time, users who join the chorus midway also need to synchronize the song progress, and only after synchronizing the progress can they participate in the chorus.

## Implementation process

The method of synchronizing songs is that the main singer user agrees to start playing the song at a future point in time (such as N seconds after delay), and other users participate in the chorus. The time of each end is based on NTP time, which will start synchronizing after the TRTC SDK is initialized.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b1f3c29c5c4d11ee974d5254005f490f.png)

The specific process is as follows:

1. Each end performs NTP time calibration, updates and obtains the latest NTP time T to the TRTC cloud.
2. The main singer end sends a chorus signal (custom message) to agree on the start time T2 of the chorus.
3. Preload the song locally based on T2 and play it at a scheduled time.
4. Other chorus users execute step 3 after receiving the chorus signal.
5. During the process, the local song playback progress is verified, and seek calibration is performed when the difference between TE and TC exceeds 50ms.

> **Note****ï¼**The 50ms error here is a typical value, which can be adjusted appropriately according to the business tolerance. It is recommended to fluctuate around 50ms.

## Timing diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6b343fce5cde11ee94c3525400d793d0.png)

The song synchronization timing can mainly be divided into three parts: NTP time calibration, sending and receiving chorus signals, and correcting the song playback progress. The following will provide specific code implementation for these three parts.

## Key code implementation

### **1. NTP calibration time service**

```
// Call the NTP time synchronization interface when entering the room.[TXLiveBase updateNetworkTime];// In the TXLiveBaseDelegate callback, determine whether the time synchronization is successful.- (void)onUpdateNetworkTime:(int)errCode message:(NSString *)errMsg {    // errCode 0: 0: Time synchronization is successful and the deviation is within 30ms;     // 1: Time synchronization is successful, but the deviation may be over 30ms;     // -1: Time synchronization failed.    if (errCode == 0) {        // Call TXLiveBase's getNetworkTimestamp to obtain the NTP timestamp.        NSInteger ntpTime = [TXLiveBase getNetworkTimestamp];    } else {        // Call updateNetworkTime again to initiate a time synchronization.        [TXLiveBase updateNetworkTime];    }}
```

### **2. Sending chorus signals on the main singer end**

```
NSDictionary *json = @{                        @"cmd": @"startChorus",                        // Scheduled time for a tutti.                        @"startPlayMusicTS": @(startTs),                        @"musicId": @"musicId",                        @"musicDuration": @(musicDuration),                      };NSString *jsonString = [self jsonStringFrom:json];[trtcCloud sendCustomMessage:jsonString reliable:NO];
```

> **Note****ï¼**It is recommended that the main singer send chorus signal messages to the room at a fixed time frequency in a loop, so that chorus users can join in midway;The reason for **not using SEI messages to send chorus signals** is that the SEI information will be inserted into the video frame, causing a lot of invalid information to be carried in the video stream pulled by the audience side.

### **3. Receiving chorus signals on the chorus end**

```
- (void)onRecvCustomCmdMsgUserId:(NSString *)userId cmdID:(NSInteger)cmdId seq:(UInt32)seq message:(NSData *)message {    NSString *msg = [[NSString alloc] initWithData:message encoding:NSUTF8StringEncoding];    NSError *error;    NSDictionary *json = [NSJSONSerialization JSONObjectWithData:[msg dataUsingEncoding:NSUTF8StringEncoding]                                                         options:NSJSONReadingMutableContainers                                                           error:&error];    NSObject *cmdObj = [json objectForKey:@"cmd"];    NSInteger musicDuration = [[json objectForKey:@"musicDuration"] integerValue];    NSString *cmd = (NSString *)cmdObj;    // tutti command    if ([cmd isEqualToString:@"startChorus"]) {        // tutti start time        NSObject *startPlayMusicTsObj = [json objectForKey:@"startPlayMusicTS"];        NSString *musicId = [json objectForKey:@"musicId"];        NSInteger startPlayMusicTs = ((NSNumber *)startPlayMusicTsObj).longLongValue;        // The difference between the scheduled tutti time and the current time.        NSInteger startDelayMS = labs(startPlayMusicTs - [TXLiveBase getNetworkTimestamp]);        // Start preloading, and jump the song progress according to the difference         // between the scheduled duet time and the current NTP time.        NSDictionary *jsonDict = @{            @"api": @"preloadMusic",            @"params": @{                    @"musicId": @(musicId),                    @"path": path,                    @"startTimeMS": @(startDelayMS),            }        };        NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDict options:0 error:NULL];        NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];        [subCloud callExperimentalAPI:jsonString];        // play music        TXAudioMusicParam *param = [[TXAudioMusicParam alloc] init];        param.ID = musicId;        param.path = url;        param.loopCount = 0;        param.publish = NO;        [[subCloud getAudioEffectManager] startPlayMusic:param onStart:^(NSInteger errCode) {            // star play callback        } onProgress:^(NSInteger progressMs, NSInteger durationMs) {            // lyric progress callback        } onComplete:^(NSInteger errCode) {            // play completely callback        }];    }}
```

> **Note****ï¼**After the chorus end receives the first startChorus signal, the status should be changed from "not singing" to "singing", and no longer respond to the startChorus signal to avoid restarting the BGM playback.

### **4. Song playback progress correction**

```
self.startPlayChorusMusicTs; // The originally scheduled tutti time.// Current playback progressNSInteger currentProgress = [[self audioEffecManager] getMusicCurrentPosInMS:self.currentPlayMusicID];// The ideal playback time progress of the current song.NSInteger estimatedProgress = [TXLiveBase getNetworkTimestamp] - self.startPlayChorusMusicTs;if (estimatedProgress >= 0 && labs(currentProgress - estimatedProgress) > 50) {    // When the playback progress exceeds 50ms, make adjustments.    [[subCloud getAudioEffectManager] seekMusicToPosInMS:self.currentPlayMusicID pts:estimatedProgress];}
```


---
*Source: [https://trtc.io/document/57025](https://trtc.io/document/57025)*
