# Playing Background Music

This tutorial mainly introduces how to play background music while using the RTC Engine live streaming feature.

## Integration Guideline

### Play/Stop Background Music

TRTC provides [TXAudioMusicParam](https://trtc.io/document/50765#79f73cf8c10624089eddf7856fdb22c7) information, used to specify background music-related details in the [startPlayMusic](https://trtc.io/document/50765#e7b176192e2cf33abe2bd18618ad6bc1) interface, including Background Music ID, file path, and loop count.

It is recommended to set the playback event callback using [setMusicObserver](https://trtc.io/document/50765#fc6d76f7ebe087957ba81a5ee62710b0) before calling the [startPlayMusic](https://trtc.io/document/50765#e7b176192e2cf33abe2bd18618ad6bc1) interface to help detect the playback status of the background music. To stop playing background music, call the [stopPlayMusic](https://trtc.io/document/50765#35e1e5bd5b10eb63b6313fd95b95580b) interface.

Android

iOS

Mac

Windows

```
int mPlayBGMId = 1024; // Background Music IDString[] mBgmUrlArray = { // Background Music URLs
        "https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/PositiveHappyAdvertising.mp3",
        "https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/SadCinematicPiano.mp3",
        "https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/WonderWorld.mp3"};// Play background musicTXAudioEffectManager audioEffectManager = mCloud.getAudioEffectManager(); // Get audio effects manageraudioEffectManager.setMusicObserver(mPlayBGMId, new TXAudioEffectManager.TXMusicPlayObserver() {
    @Override
    public void onStart(int i, int i1) {
        Toast.makeText(getApplicationContext(), "id: " + i + "errCode: " + i1, Toast.LENGTH_LONG).show();
    }
});TXAudioEffectManager.AudioMusicParam audioMusicParam =
        new TXAudioEffectManager.AudioMusicParam(mPlayBGMId, mBgmUrlArray[mPlayBGMId - 1024]); // Set background music playback parameters
audioMusicParam.publish = true; // Transmit background music to the remote side
audioEffectManager.startPlayMusic(audioMusicParam); // Stop background musicaudioEffectManager.stopPlayMusic(mPlayBGMId);
```

```
// .h file@property(nonatomic, strong) NSArray *mBgmUrlArray;@property(nonatomic, assign) int mPlayBGMId;// .m file_mPlayBGMId = 1024;_mBgmUrlArray = @[@"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/PositiveHappyAdvertising.mp3",                  @"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/SadCinematicPiano.mp3",                  @"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/WonderWorld.mp3"];// Play background musicTXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager]; // Get the sound effect management classTXAudioMusicParam *audioMusicParam = [[TXAudioMusicParam alloc] init];audioMusicParam.ID = self.mPlayBGMId; // Specify the BGM IDaudioMusicParam.path = self.mBgmUrlArray[self.mPlayBGMId - 1024]; // Specify the BGM addressaudioMusicParam.publish = YES; // Transmit the background music to remote
[audioEffectManager startPlayMusic:audioMusicParam onStart:NULL onProgress:NULL onComplete:NULL]; // Stop background music[audioEffectManager stopPlayMusic:self.mPlayBGMId];
```

```
// .h file@property(nonatomic, strong) NSArray *mBgmUrlArray;@property(nonatomic, assign) int mPlayBGMId;// .m file_mPlayBGMId = 1024;_mBgmUrlArray = @[@"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/PositiveHappyAdvertising.mp3",                  @"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/SadCinematicPiano.mp3",                  @"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/WonderWorld.mp3"];// Play background musicTXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager]; // Get the sound effect management classTXAudioMusicParam *audioMusicParam = [[TXAudioMusicParam alloc] init];audioMusicParam.ID = self.mPlayBGMId; // Specify the BGM IDaudioMusicParam.path = self.mBgmUrlArray[self.mPlayBGMId - 1024]; // Specify the BGM addressaudioMusicParam.publish = YES; // Transmit the background music to remote
[audioEffectManager startPlayMusic:audioMusicParam onStart:NULL onProgress:NULL onComplete:NULL]; // Stop background music[audioEffectManager stopPlayMusic:self.mPlayBGMId];
```

```
// Implement pure virtual functions in ITXMusicPlayObserverclass MusicPlayObserver : public ITXMusicPlayObserver {public:	void onStart(int id, int errCode) {		// Implement onStart method	}	void onPlayProgress(int id, long curPtsMS, long durationMS) {		// Implement onPlayProgress method	}	void onComplete(int id, int errCode) {		// Implement onComplete method	}};int mPlayBGMId = 1024; // Background Music IDchar* mBgmUrlArray[] = { // Background music URL addresses    "https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/PositiveHappyAdvertising.mp3",	"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/SadCinematicPiano.mp3",	"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/WonderWorld.mp3"};// Play background musicITXAudioEffectManager* audioEffectManager = trtc_cloud_->getAudioEffectManager(); // Get the sound effect management classITXMusicPlayObserver* musicPlayObserver = new MusicPlayObserver();// Initialize musicPlayObserveraudioEffectManager->setMusicObserver(mPlayBGMId, musicPlayObserver);if (mPlayBGMId >= 1024 && mPlayBGMId < 1024 + sizeof(mBgmUrlArray) / sizeof(mBgmUrlArray[0])) {    // Set background music parameters	AudioMusicParam audioMusicParam = { mPlayBGMId, mBgmUrlArray[mPlayBGMId - 1024] };	audioMusicParam.publish = true; // Transmit the background music to remote 	audioEffectManager->startPlayMusic(audioMusicParam); // Start playing background music}// Stop background musicaudioEffectManager->stopPlayMusic(mPlayBGMId);
```

### Pause/Resume background music

Call [pausePlayMusic](https://trtc.io/document/50765#2ee1a37638877d7041493a7ce1402077)/[resumePlayMusic](https://trtc.io/document/50765#dfcbb473c7ddfe6b0028e1d318ed8ff3) to pause and resume the currently playing background music.

Android

iOS

Mac

Windows

```
private int mPlayBGMId = 1024; // Background Music IDprivate String[] mBgmUrlArray = { // Background Music URL addresses
        "https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/PositiveHappyAdvertising.mp3",
        "https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/SadCinematicPiano.mp3",
        "https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/WonderWorld.mp3"};// Pause background musicTXAudioEffectManager audioEffectManager = mCloud.getAudioEffectManager();
audioEffectManager.pausePlayMusic(mPlayBGMId); // Resume background musicaudioEffectManager.resumePlayMusic(mPlayBGMId);
```

```
// .h file@property(nonatomic, strong) NSArray *mBgmUrlArray;@property(nonatomic, assign) int mPlayBGMId;// .m file_mPlayBGMId = 1024;_mBgmUrlArray = @[@"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/PositiveHappyAdvertising.mp3",                  @"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/SadCinematicPiano.mp3",                  @"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/WonderWorld.mp3"];// Pause background musicTXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager pausePlayMusic:self.mPlayBGMId];// Resume background music[audioEffectManager resumePlayMusic:self.mPlayBGMId];
```

```
// .h file@property(nonatomic, strong) NSArray *mBgmUrlArray;@property(nonatomic, assign) int mPlayBGMId;// .m file_mPlayBGMId = 1024;_mBgmUrlArray = @[@"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/PositiveHappyAdvertising.mp3",                  @"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/SadCinematicPiano.mp3",                  @"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/WonderWorld.mp3"];// Pause background musicTXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager pausePlayMusic:self.mPlayBGMId];// Resume background music[audioEffectManager resumePlayMusic:self.mPlayBGMId];
```

```
int mPlayBGMId = 1024; // Background Music IDchar* mBgmUrlArray[] = { // Background music URL addresses    "https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/PositiveHappyAdvertising.mp3",	"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/SadCinematicPiano.mp3",	"https://sdk-liteav-1252463788.cos.ap-hongkong.myqcloud.com/app/res/bgm/trtc/WonderWorld.mp3"};// Pause background musicITXAudioEffectManager* audioEffectManager = trtc_cloud_->getAudioEffectManager();audioEffectManager->pausePlayMusic(mPlayBGMId);// Resume background musicaudioEffectManager->resumePlayMusic(mPlayBGMId);
```

### Set background music volume

- Call [setAllMusicVolume](https://trtc.io/document/50765#01e8b8f4cb30d56b50e931c2857d7754) to set the volume of background music. This interface can set both local and remote volume of all background music at the same time.

Android

iOS

Mac

Windows

```
TXAudioEffectManager audioEffectManager = mCloud.getAudioEffectManager();audioEffectManager.setAllMusicVolume(100); // Set both local and remote volume of all background music to 100
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setAllMusicVolume:100]; // Set both local and remote volume of all background music to 100
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicPublishVolume:self.mPlayBGMId volume:100]; // Set the remote volume of a specific background music to 100
```

```
ITXAudioEffectManager* audioEffectManager = trtc_cloud_->getAudioEffectManager();trtc_cloud_->setAllMusicVolume(100); // Set the remote volume of a specific background music to 100
```

- Call [setMusicPublishVolume](https://trtc.io/document/50765#fc3c4bf5f3c047d05371ddd6c8aa87d9) to set the remote volume of a specific background music. This interface can fine-tune the volume that the audience hears for each background music.

Android

iOS

Mac

Windows

```
TXAudioEffectManager audioEffectManager = mCloud.getAudioEffectManager();audioEffectManager.setMusicPublishVolume(mPlayBGMId, 100); // Set the remote volume of a specific background music to 100
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicPublishVolume:self.mPlayBGMId volume:100]; // Set the remote volume of a specific background music to 100
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicPublishVolume:self.mPlayBGMId volume:100]; // Set the remote volume of a specific background music to 100
```

```
ITXAudioEffectManager* audioEffectManager = trtc_cloud_->getAudioEffectManager();trtc_cloud_->setMusicPublishVolume(mPlayBGMId, 100); // Set the remote volume of a specific background music to 100
```

- Call [setMusicPlayoutVolume](https://trtc.io/document/50765#d8911047524dead67735746adff09354) to set the local volume of a specific background music. This interface can fine-tune the volume that the host hears for each background music.

Android

iOS

Mac

Windows

```
TXAudioEffectManager audioEffectManager = mCloud.getAudioEffectManager();audioEffectManager.setMusicPlayoutVolume(mPlayBGMId, 100); // Set the local volume of a specific background music to 100
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicPlayoutVolume:self.mPlayBGMId volume:100]; // Set the local volume of a specific background music to 100
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicPlayoutVolume:self.mPlayBGMId volume:100]; // Set the local volume of a specific background music to 100
```

```
ITXAudioEffectManager* audioEffectManager = trtc_cloud_->getAudioEffectManager();trtc_cloud_->setMusicPlayoutVolume(mPlayBGMId, 100); // Set the local volume of a specific background music to 100
```

> **Note:**The volume range is 0-100, with a default value of 60.

### Adjust the pitch of background music

Call [setMusicPitch](https://trtc.io/document/50765#d8911047524dead67735746adff09354) to adjust the pitch of a specific background music.

Android

iOS

Mac

Windows

```
TXAudioEffectManager audioEffectManager = mCloud.getAudioEffectManager();audioEffectManager.setMusicPitch(mPlayBGMId, 1); // Raise the pitch of a specific background music to 1audioEffectManager.setMusicPitch(mPlayBGMId, -1); // Lower the pitch of a specific background music to -1
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicPitch:self.mPlayBGMId pitch:1]; // Raise the pitch of a specific background music to 1[audioEffectManager setMusicPitch:self.mPlayBGMId pitch:-1]; // Lower the pitch of a specific background music to -1
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicPitch:self.mPlayBGMId pitch:1]; // Raise the pitch of a specific background music to 1[audioEffectManager setMusicPitch:self.mPlayBGMId pitch:-1]; // Lower the pitch of a specific background music to -1
```

```
ITXAudioEffectManager* audioEffectManager = trtc_cloud_->getAudioEffectManager();trtc_cloud_->setMusicPitch(mPlayBGMId, 1); // Raise the pitch of a specific background music to 1trtc_cloud_->setMusicPitch(mPlayBGMId, -1); // Lower the pitch of a specific background music to -1
```

> **Note:**The pitch range is: -1 to 1, with a default value of 0.0f.

### Adjust the variable speed effect of background music

Call [setMusicSpeedRate](https://trtc.io/document/50765#5245a320dc95f7031cf39fd21d80248e) to adjust the pitch of a specific background music.

Android

iOS

Mac

Windows

```
TXAudioEffectManager audioEffectManager = mCloud.getAudioEffectManager();audioEffectManager.setMusicSpeedRate(mPlayBGMId, 2); // Adjust the speed of a specific background music to 2audioEffectManager.setMusicSpeedRate(mPlayBGMId, 0.5); // Adjust the speed of a specific background music to 0.5
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicSpeedRate:self.mPlayBGMId speedRate:2]; // Adjust the speed of a specific background music to 2[audioEffectManager setMusicSpeedRate:self.mPlayBGMId speedRate:0.5]; // Adjust the speed of a specific background music to 0.5
```

```
TXAudioEffectManager *audioEffectManager = [self.trtcCloud getAudioEffectManager];[audioEffectManager setMusicSpeedRate:self.mPlayBGMId speedRate:2]; // Adjust the speed of a specific background music to 2[audioEffectManager setMusicSpeedRate:self.mPlayBGMId speedRate:0.5]; // Adjust the speed of a specific background music to 0.5
```

```
ITXAudioEffectManager* audioEffectManager = trtc_cloud_->getAudioEffectManager();trtc_cloud_->setMusicSpeedRate(mPlayBGMId, 2); // Adjust the speed of a specific background music to 2trtc_cloud_->setMusicSpeedRate(mPlayBGMId, 0.5); // Adjust the speed of a specific background music to 0.5
```

> **Note:**The music speed range is: 0.5 to 2, with a default value of 1.0f.

## Contact Us

If you have any requirements or feedback, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/64699](https://trtc.io/document/64699)*
