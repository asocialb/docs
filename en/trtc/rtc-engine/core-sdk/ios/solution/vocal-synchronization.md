# Vocal Synchronization

## Introduction to Synchronization of Vocals and Songs

Due to the existence of certain gaps between the jitter buffer for local voice collection, the jitter buffer for song playback mixing, and the sound reaching the singer's ears, when the singer sings completely facing the lyrics and BGM playback, remote audiences will feel that there is a certain delay between the playback of BGM, vocals, and lyrics. The chorus solution in the TRTC SDK uses low-latency AAudio collection internally. You only need to enable chorus mode and low-latency mode after entering the room.

## Specific Code Implementation

### Enable Chorus Mode

```
// Enable tutti mode for the main instance (vocal instance) by reducing the buffer interval // and enabling audio redundancy protection.NSDictionary *jsonDic = @{                              @"api": @"enableChorus",                              @"params": @{                                            @"enable": @(YES),                                            @"audioSource": @(0)                                          }                          };NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDic options:NSJSONWritingPrettyPrinted error:nil];NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[trtcCloud callExperimentalAPI:jsonString];// Enable tutti mode for the sub-instance (accompaniment instance) by reducing the buffer interval // and enabling audio redundancy protection.NSDictionary *jsonDic = @{                              @"api": @"enableChorus",                              @"params": @{                                            @"enable": @(YES),                                            @"audioSource": @(1)                                          }                          };NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDic options:NSJSONWritingPrettyPrinted error:nil];NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[subCloud callExperimentalAPI:jsonString];
```

> **Note****ï¼**The parameter settings for enabling chorus mode through the experimental interface `enableChorus` are as follows: audioSource: 0 (vocals)audioSource: 1 (accompaniment)

### Enable Low-Latency Mode (High-Performance Audio AAudio)

```
// Enable high-performance audio AAudio for the main instance (vocal instance).NSDictionary *jsonDic = @{                              @"api": @"setLowLatencyModeEnabled",                              @"params": @{                                            @"enable": @(1)                                          }                          };NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDic options:NSJSONWritingPrettyPrinted error:nil];NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[trtcCloud callExperimentalAPI:jsonString];// Enable high-performance audio AAudio for the sub-instance (accompaniment instance).NSDictionary *jsonDic = @{                             @"api": @"setLowLatencyModeEnabled",                             @"params": @{                                           @"enable": @(1)                                         }                         };NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDic options:NSJSONWritingPrettyPrinted error:nil];NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[subCloud callExperimentalAPI:jsonString];
```


---
*Source: [https://trtc.io/document/57032](https://trtc.io/document/57032)*
