# Mixing Stream Solution

## Specific code implementation

### 1. Create main and sub-instances

```
// Create TRTCCloud main instance (vocal instance)TRTCCloud mTRTCCloud = TRTCCloud.sharedInstance(getApplicationContext());// Create TRTCCloud sub-instance (accompaniment instance)TRTCCloud subCloud = mTRTCCloud.createSubCloud();
```

> **Note:**In the real-time chorus scheme, the lead singer needs to create the main instance-vocal instance and the sub-instance-accompaniment instance separately for uploading vocals and accompaniment music.

### 2. Vocal instance enters the room and pushes the stream

```
TRTCCloudDef.TRTCParams params = new TRTCCloudDef.TRTCParams();params.sdkAppId = sdkAppId;params.userId = mUserId;params.userSig = userSig;params.role = TRTCCloudDef.TRTCRoleAnchor;params.roomId = mRoomId;mTRTCCloud.enterRoom(params, TRTCCloudDef.TRTC_APP_SCENE_LIVE);// Turn on audio uplink and set audio qualitymTRTCCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_MUSIC);// Set media typemTRTCCloud.setSystemVolumeType(TRTCCloudDef.TRTCSystemVolumeTypeMedia);// Mute remote accompaniment musicmTRTCCloud.muteRemoteAudio(mUserId + "_bgm", true);
```

> **Noticeï¼**In pure RTC audio scenarios, it is recommended to use VOICE_CHATROOM for entering the room.If there is a need for video or CDN forwarding, the room entry scenario must use LIVE, as VOICE_CHATROOM will add pure audio parameters during forwarding, causing SEI messages to fail to pass through.The lead singer/chorus needs to muteRemoteAudio(true) to unsubscribe from the audio stream uploaded by the accompaniment instance, otherwise, the local and remote accompaniment music will be played repeatedly.

### 3. Accompaniment instance enters the room and pushes the stream

```
TRTCCloudDef.TRTCParams bgmParams = new TRTCCloudDef.TRTCParams();bgmParams.sdkAppId = sdkAppId;bgmParams.userId = mUserId + "_bgm";bgmParams.userSig = userSig;bgmParams.role = TRTCCloudDef.TRTCRoleAnchor;bgmParams.roomId = mRoomId;subCloud.enterRoom(bgmParams, TRTCCloudDef.TRTC_APP_SCENE_LIVE);// Set media typesubCloud.setSystemVolumeType(TRTCCloudDef.TRTCSystemVolumeTypeMedia);// Enable preloadingsubCloud.callExperimentalAPI("{\\"api\\":\\"preloadMusic\\",\\"params\\": {\\"musicId\\":musicId,\\"path\\":\\"path\\",\\"startTimeMS\\":startTimeMS}}");// Play accompaniment music and push the stream (play at the agreed time)TXAudioEffectManager.AudioMusicParam param = new TXAudioEffectManager.AudioMusicParam(musicID, musicPath);// Send accompaniment music to the remote endparam.publish = true;subCloud.getAudioEffectManager().startPlayMusic(param);
```

> **Note:**Pay attention to distinguish between the userId of the main instance and the sub-instance, ensuring that they are not duplicated and easy to identify;Accompaniment instance background music parameter AudioMusicParam settings:publishï¼trueÂ (while the music is playing locally, remote users can also hear the music)publishï¼falseÂ (default value, the music can only be heard locally, remote users cannot hear it)

### 4. Initiate mixed stream transcoding and pushing

```
// Create a TRTCPublishTarget objectTRTCCloudDef.TRTCPublishTarget target = new TRTCCloudDef.TRTCPublishTarget();// Push back to the room after mixing, if publishing to CDN, fill in TRTC_PublishMixStream_ToCdntarget.mode = TRTCCloudDef.TRTC_PublishMixStream_ToRoom;target.mixStreamIdentity.intRoomId = Integer.parseInt(mRoomId);// The userid of the mixing robot, which cannot be duplicated with other users' userid in the roomtarget.mixStreamIdentity.userId = mUserId + "_mix"; // Set the encoding parameters of the transcoded audio streamTRTCCloudDef.TRTCStreamEncoderParam trtcStreamEncoderParam = new TRTCCloudDef.TRTCStreamEncoderParam();trtcStreamEncoderParam.audioEncodedChannelNum = 2;trtcStreamEncoderParam.audioEncodedKbps = 64;trtcStreamEncoderParam.audioEncodedCodecType = 2;trtcStreamEncoderParam.audioEncodedSampleRate = 48000;// Set audio mixing parametersTRTCCloudDef.TRTCStreamMixingConfig trtcStreamMixingConfig = new TRTCCloudDef.TRTCStreamMixingConfig();// Support filling in empty values, which will automatically mix the audio of all hosts and outputtrtcStreamMixingConfig.audioMixUserList = null;// Initiate mixed stream transcoding and pushing requestmTRTCCloud.startPublishMediaStream(target, trtcStreamEncoderParam, trtcStreamMixingConfig);
```

> **Noteï¼**It is recommended to prioritize the lead singer to initiate mixed stream transcoding and pushing through the mixing robot to the backend, mixing the accompaniment music and all vocal streams and pushing them back to the TRTC room, or pushing them to the live CDN.In automatic subscription mode, the hosts participating in the mixed stream transcoding will pull each other's single stream by default and not receive the mixed stream pushed back to the room; the audience will automatically pull the mixed stream pushed back to the room and no longer receive the single stream.The mixed stream transcoding and pushing method startPublishMediaStream used here adopts a brand new backend architecture. The old version of the application needs to provide the SdkAppId to apply for an upgrade before it can be used.


---
*Source: [https://trtc.io/document/57036](https://trtc.io/document/57036)*
