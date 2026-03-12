# Lyric Synchronization

## 1.1 Implementation process

In the lyrics synchronization solution, the actions of the three different roles are as follows:

| Main Singer | Chorus | Audience |
| --- | --- | --- |
| NTP time calibrationEnable black frame insertionSend SEI messagesLocal lyrics synchronizationUpdate lyrics control | NTP time calibrationLocal lyrics synchronizationUpdate lyrics control | NTP time calibrationReceive SEI messagesUpdate lyrics control |

Among them, the main singer and chorus update the lyrics progress locally based on the synchronized song playback progress; the audience end needs to receive SEI messages containing the latest lyrics progress sent by the main singer end to update the local lyrics progress.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5af106675c4c11ee9ff8525400d917da.png)

## Timing diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ddc7ebb85cde11ee94c3525400d793d0.png)

The synchronization of lyrics timing can mainly be divided into three parts: NTP time synchronization, enabling black frame compensation, and local and remote lyrics synchronization. The code implementation of NTP time synchronization has been provided in the [Song Synchronization](https://www.tencentcloud.com/document/product/647/57026) document. The following will provide specific code implementation for the latter two parts.

## Key code implementation

### **1. Enable Black Frame Insertion**

```
// In pure audio mode, the main instance (vocal instance) // needs to enable black frame padding to carry SEI messages.NSDictionary *jsonDic = @{                            @"api": @"enableBlackStream",                            @"params":                                  @{                                    @"enable": @(1)                                  }                          };NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDic options:NSJSONWritingPrettyPrinted error:nil];NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[trtcCloud callExperimentalAPI:jsonString];
```

> **Note:**The experimental interface `enableBlackStream` needs to be called after entering the room;On Android, the value type of the `enable` parameter is Boolean, and on iOS it is Integer;The receiving end needs to call `startRemoteView(userId, null)` after receiving `onUserVideoAvailable(userId, true)`.

### **2. Sending Song Progress through SEI Message**

```
TXAudioMusicProgressBlock progressBlock = ^(NSInteger progressMs, NSInteger durationMs) {    // current ntp time    NSInteger ntpTime = [TXLiveBase getNetworkTimestamp];    // Notify the song progress, users will scroll the lyrics here.    NSDictionary *progressMsg = @{            @"bgmProgressTime":@(progressMs),            @"ntpTime":@(ntpTime),            @"musicId": @(musicId),            @"duration": @(durationMs),    };    NSData *jsonData = [NSJSONSerialization dataWithJSONObject:progressMsg options:NSJSONWritingPrettyPrinted error:nil];    NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];    [trtcCloud sendSEIMsg:[jsonString dataUsingEncoding:NSUTF8StringEncoding] repeatCount:1];};
```

> **Note:**The frequency at which the lead singer sends SEI messages is determined by the frequency of background music playback event callbacks, which is usually 200ms;The reason for **not directly using CMD messages to send song progress** is that the signaling transmitted through the SEI channel can be transmitted with the video frame to the live CDN, which has better compatibility for viewers who pull the CDN stream.

### **3. Synchronization of Local and Remote Lyrics**

```
// local lyrics synchronizationTXAudioMusicProgressBlock progressBlock = ^(NSInteger progressMs, NSInteger durationMs) {    ...    // TODO Update the logic of the lyrics control.    // Determine whether it is necessary to seek the lyrics control     // based on the latest progress and the error of the local lyrics progress.    ...};// remote lyrics synchronization.- (void)onRecvSEIMsg:(NSString *)userId message:(NSData *)message {    NSError *err = nil;    NSDictionary *dic = [NSJSONSerialization JSONObjectWithData:message options:NSJSONReadingMutableContainers error:&err];    if (err || ![dic isKindOfClass:[NSDictionary class]]) {        // Parsing error.        return;    }    NSInteger bgmProgressTime = [[dic objectForKey:@"bgmProgressTime"] integerValue];    NSInteger ntpTime = [[dic objectForKey:@"ntpTime"] integerValue];    int32_t musicId = [[dic objectForKey:@"musicId"] intValue];    NSInteger duration = [[dic objectForKey:@"duration"] integerValue];    ...    // TODO Update the logic of the lyrics control.    // Determine whether it is necessary to seek the lyrics control     // based on the received latest progress and the error of the local lyrics progress.    ...}
```

> **Note**If reusing the TUIKaraoke component's lyric control, please refer to the code logic in the [TUIKaraoke TRTCLyricView](https://github.com/tencentyun/TUIKaraoke/blob/main/iOS/Source/ui/TUILyricKit/TUILyricsView.swift) section to synchronize the progress of the lyric control.


---
*Source: [https://trtc.io/document/57028](https://trtc.io/document/57028)*
