# Mixing Stream Solution

## Specific code implementation

### 1. Create main and sub-instances

```
// Create TRTCCloud main instance (vocal instance)TRTCCloud *trtcCloud = [TRTCCloud sharedInstance];// Create TRTCCloud sub-instance (accompaniment instance)TRTCCloud *subCloud = [trtcCloud createSubCloud];
```

> **Noteï¼**In the real-time chorus scheme, the lead singer needs to create the main instance-vocal instance and the sub-instance-accompaniment instance separately for uploading vocals and accompaniment music.

### 2. Vocal instance enters the room and pushes the stream

```
TRTCParams *params = [[TRTCParams alloc] init];params.sdkAppId = sdkAppId;params.userId = userId;params.userSig = userSign;params.role = TRTCRoleAnchor;params.roomId = roomIdIntValue;[trtcCloud enterRoom:params appScene:TRTCAppSceneLIVE];// Turn on audio uplink and set audio quality[trtcCloud startLocalAudio:TRTCAudioQualityMusic];// Set media type[trtcCloud setSystemVolumeType:TRTCSystemVolumeTypeMedia];// Mute remote accompaniment music[trtcCloud muteRemoteAudio:remoteAudioId mute:YES];
```

> **Noteï¼**In pure RTC audio scenarios, it is recommended to use VOICE_CHATROOM for entering the room.If there is a need for video or CDN forwarding, the room entry scenario must use LIVE, as VOICE_CHATROOM will add pure audio parameters during forwarding, causing SEI messages to fail to pass through.The lead singer/chorus needs to muteRemoteAudio(true) to unsubscribe from the audio stream uploaded by the accompaniment instance, otherwise, the local and remote accompaniment music will be played repeatedly.

### 3. Accompaniment example: Joining room and pushing stream.

```
TRTCParams *bgmParams = [[TRTCParams alloc] init];bgmParams.sdkAppId = sdkAppId;bgmParams.userId = [NSString stringWithFormat:@"%@%@",userId,@"_bgm"];bgmParams.userSig = bgmUserSign;bgmParams.role = TRTCRoleAnchor;bgmParams.roomId = roomIdIntValue;[subCloud enterRoom:bgmParams appScene:TRTCAppSceneLIVE];// Set media type[subCloud setSystemVolumeType:TRTCSystemVolumeTypeMedia];// Enable preloadingNSDictionary *jsonDict = @{                              @"api": @"preloadMusic",                              @"params": @{                                            @"musicId": @(self.currentPlayMusicID),                                            @"path": path,                                            @"startTimeMS": @(startMs),                                           }                             };NSData *jsonData = [NSJSONSerialization dataWithJSONObject:jsonDict options:0 error:NULL];NSString *jsonString = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];[subCloud callExperimentalAPI:jsonString];// Play accompaniment music and push the stream (play at the agreed time)TXAudioMusicParam *musicParam = [[TXAudioMusicParam alloc] init];musicParam.ID = musicID;musicParam.path = url;musicParam.loopCount = 0;musicParam.publish = YES;// Send accompaniment music to the remote endparam.publish = YES;[[subCloud getAudioEffectManager] startPlayMusic:musicParam onStart:startBlock onProgress:progressBlock onComplete:completedBlock]
```

> **Noteï¼**Pay attention to distinguish between the userId of the main instance and the sub-instance, ensuring that they are not duplicated and easy to identify;Accompaniment instance background music parameter musicParam seettings:publishï¼YESÂ (while the music is playing locally, remote users can also hear the music)publishï¼NOÂ (default value, the music can only be heard locally, remote users cannot hear it)

### 4. Initiating mixed stream transcoding and pushing back.

```
// Create a TRTCPublishTarget objectTRTCPublishTarget *publishTarget = [[TRTCPublishTarget alloc] init];// Push back to the room after mixing, if publishing to CDN, fill in TRTCPublishMixStreamToCdnpublishTarget.mode = TRTCPublishMixStreamToRoom;// The userid of the mixing robot, which cannot be duplicated with other users' userid in the roompublishTarget.mixStreamIdentity = [NSString stringWithFormat:@"%@%@",userId,@"_mix"]; // Set the encoding parameters of the transcoded audio streamTRTCStreamEncoderParam *streamEncoderParam = [[TRTCStreamEncoderParam alloc] init];streamEncoderParam.videoEncodedFPS = 15;streamEncoderParam.videoEncodedGOP = 3;streamEncoderParam.videoEncodedKbps = 30;streamEncoderParam.audioEncodedSampleRate = 48000;streamEncoderParam.audioEncodedChannelNum = 2;streamEncoderParam.audioEncodedKbps = 64;streamEncoderParam.audioEncodedCodecType = 2;// Set audio mixing parametersTRTCStreamMixingConfig *streamMixingConfig = [[TRTCStreamMixingConfig alloc] init];// Support filling in empty values, which will automatically mix the audio of all hosts and outputstreamMixingConfig.audioMixUserList = @[];// Initiate mixed stream transcoding and pushing request[trtcCloud startPublishMediaStream:publishTarget encoderParam:streamEncoderParam mixingConfig:streamMixingConfig];
```

> **Note:**It is recommended to prioritize the lead singer to initiate mixed stream transcoding and pushing through the mixing robot to the backend, mixing the accompaniment music and all vocal streams and pushing them back to the TRTC room, or pushing them to the live CDN.In automatic subscription mode, the hosts participating in the mixed stream transcoding will pull each other's single stream by default and not receive the mixed stream pushed back to the room; the audience will automatically pull the mixed stream pushed back to the room and no longer receive the single stream.The mixed stream transcoding and pushing method startPublishMediaStream used here adopts a brand new backend architecture. The old version of the application needs to provide the SdkAppId to apply for an upgrade before it can be used.


---
*Source: [https://trtc.io/document/57035](https://trtc.io/document/57035)*
