# Live Streaming

This tutorial mainly introduces how to implement the Live Streaming feature in the [TRTC_APP_SCENE_LIVE](https://trtc.io/document/50768#45c6782b29cadc377b5763a5d8490340) scenario.

## Supported Platforms

| iOS | Android | Mac OS | Windows | Web | Electron | Flutter |
| --- | --- | --- | --- | --- | --- | --- |
| â | â | â | â | â | â | â |

## TRTC Scenarios and Roles

In common business scenarios, not all users need to publish streams; they only need to subscribe to streams from remote users.

**TRTC** Audio and Video usage scenarios are mainly divided into the following categories:

- **Real-time Conmmucation (RTC):** In real-time scenarios, there is no difference in user roles. However, a single room can support up to 300 online users simultaneously, making it suitable for small-scale real-time communication scenarios.
- **Live Broadcasting (LIVE):**In live broadcasting scenarios, users are divided into two roles: **"Host"** and **"Audience"**, with a single room supporting up to 100,000 people online simultaneously, suitable for live broadcasting with a large audience.
  - **Anchor:**Can publish their own audio and video streams at any time, but the number is limited, with up to 50 hosts allowed to publish their streams simultaneously in the same room.
  - **Audience:**Can only watch other users' audio and video streams. To publish streams, one must first switch to a host by using [switchRole](https://trtc.io/document/50762#0a2b76d62a79877c408aa638b61d9b8e). A single room can accommodate up to 100,000 audience members.

## Anchor side

The process of implementing audio and video on the host side is basically the same as in the **RTC** scenario.

The main difference lies in the two parameters passed when calling `enterRoom`: **scene** and **role**. Refer to the example code below:

Android

iOS

Mac

Windows

```
void enterRoom() {    TRTCCloudDef.TRTCParams trtcParams = new TRTCCloudDef.TRTCParams();    trtcParams.sdkAppId = 1400000123;    trtcParams.userId = "anchor";    trtcParams.roomId = 123321;    trtcParams.userSig = "xxx";    trtcParams.role = TRTCCloudDef.TRTCRoleAnchor; // Enter the room as an anchor    // For group video call scenarios, it is recommended to use TRTC_APP_SCENE_LIVE    mCloud.enterRoom(trtcParams, TRTCCloudDef.TRTC_APP_SCENE_LIVE);  }
```

```
- (void)enterRoom {    TRTCParams *trtcParams = [[TRTCParams alloc] init];    trtcParams.sdkAppId = 1400000123;    trtcParams.roomId = 123321;    trtcParams.userId = @"anchor";    trtcParams.userSig = @"";    trtcParams.role = TRTCRoleAnchor; // Enter the room as an anchor        // For group video call scenarios, it is recommended to use TRTC_APP_SCENE_LIVE    [self.trtcCloud enterRoom:trtcParams appScene:TRTCAppSceneLIVE];}
```

```
-(void)enterRoom {    TRTCParams * trtcParams = [[TRTCParams alloc] init];    trtcParams.sdkAppId = 1400000123;    trtcParams.roomId = 123321;    trtcParams.userId = @"anchor";    trtcParams.userSig = @"";    trtcParams.role = TRTCRoleAnchor; // Enter the room as an anchor        // For multi-person video call scenarios, it is recommended to use TRTC_APP_SCENE_LIVE    [self.trtcCloud enterRoom:trtcParams appScene:TRTCAppSceneLIVE];}
```

```
void CLASSNAME::OnBnClickedButton() {    liteav::TRTCParams trtcParams;    trtcParams.sdkAppId = 1400000123;    trtcParams.userId = "denny";     trtcParams.roomId = 123321;    trtcParams.userSig = "xxx";    trtcParams.role = liteav::TRTCRoleAnchor; // Enter the room as anchor    // For group video call scenarios, it is recommended to use TRTC_APP_SCENE_LIVE    trtc_cloud_->enterRoom(trtcParams, liteav::TRTCAppSceneLIVE);}
```

## Audience side

### Enter the room as an Audience

To enter the room as audience, set the **role** parameter to **TRTCRoleAudience**.

Android

iOS

Mac

Windows

```
void enterRoom() {    TRTCCloudDef.TRTCParams trtcParams = new TRTCCloudDef.TRTCParams();    trtcParams.sdkAppId = 1400000123;    trtcParams.userId = "audience";    trtcParams.roomId = 123321;    trtcParams.userSig = "xxx";    trtcParams.role = TRTCCloudDef.TRTCRoleAudience; // Enter the room as audience    // For group video call scenarios, it is recommended to use TRTC_APP_SCENE_LIVE    mCloud.enterRoom(trtcParams, TRTCCloudDef.TRTC_APP_SCENE_LIVE);  }
```

```
- (void)enterRoom {    TRTCParams *trtcParams = [[TRTCParams alloc] init];    trtcParams.sdkAppId = 1400000123;    trtcParams.roomId = 123321;    trtcParams.userId = @"audience";    trtcParams.userSig = @"";    trtcParams.role = TRTCRoleAudience; // Enter the room as audience        // For multi-person video call scenarios, it is recommended to use TRTC_APP_SCENE_LIVE    [self.trtcCloud enterRoom:trtcParams appScene:TRTCAppSceneLIVE];}
```

```
-(void)enterRoom {    TRTCParams * trtcParams = [[TRTCParams alloc] init];    trtcParams.sdkAppId = 1400000123;    trtcParams.roomId = 123321;    trtcParams.userId = @"audience";    trtcParams.userSig = @"";    trtcParams.role = TRTCRoleAudience; // Enter the room as audience        // For multi-person video call scenarios, it is recommended to use TRTC_APP_SCENE_LIVE    [self.trtcCloud enterRoom:trtcParams appScene:TRTCAppSceneLIVE];}
```

```
void CLASSNAME::OnBnClickedButton() {    liteav::TRTCParams trtcParams;    trtcParams.sdkAppId = 1400000123;    trtcParams.userId = "audience";     trtcParams.roomId = 123321;    trtcParams.userSig = "xxx";    trtcParams.role = liteav::TRTCRoleAudience; // Enter the room as audience    // For multi-person video call scenarios, it is recommended to use TRTC_APP_SCENE_LIVE    trtc_cloud_->enterRoom(trtcParams, liteav::TRTCAppSceneLIVE);}
```

### Play remote audio

By default, the SDK will automatically play remote audio. You do not need to call any API to play remote audio.

If you do not need to play remote audio after entering the room, you can call `muteRemoteAudio` to mute a specific remote user, or call `muteAllRemoteAudio` to mute all remote users. Refer to the code below:

Android

iOS

Mac

Windows

```
// Mute only the remote audio of the anchormCloud.muteRemoteAudio("anchor", true);// Mute all remote usersmCloud.muteAllRemoteAudio(true);
```

```
// Mute only the remote audio of the anchor[self.trtcCloud muteRemoteAudio:@"anchor" mute:YES];// Mute all remote users[self.trtcCloud muteAllRemoteAudio:YES];
```

```
// Mute only the remote audio of the anchor[self.trtcCloud muteRemoteAudio:@"anchor" mute:YES];// Mute all remote usersAppDelegate *appDelegate = (AppDelegate *)[[NSApplication sharedApplication] delegate];[self.trtcCloud muteAllRemoteAudio:YES];
```

```
// Mute only the remote audio of the anchortrtc_cloud_->muteRemoteAudio("anchor", true);// Mute all remote userstrtc_cloud_->muteAllRemoteAudio(true);
```

When you need to resume remote audio playback, refer to the following code:

Android

iOS

Mac

Windows

```
// Unmute only the remote audio of the anchormCloud.muteRemoteAudio("anchor", false);// Unmute all remote usersmCloud.muteAllRemoteAudio(false);
```

```
// Unmute only the remote audio of the anchor[self.trtcCloud muteRemoteAudio:@"anchor" mute:NO];// Unmute all remote users[self.trtcCloud muteAllRemoteAudio:NO];
```

```
// Unmute only the remote audio of the anchor[self.trtcCloud muteRemoteAudio:@"anchor" mute:NO];// Unmute all remote users[self.trtcCloud muteAllRemoteAudio:NO];
```

```
// Unmute only the remote audio of the anchortrtc_cloud_->muteRemoteAudio("anchor", false);// Unmute all remote userstrtc_cloud_->muteAllRemoteAudio(false);
```

### Play remote video

1. Listen to [onUserVideoAvailable](https://trtc.io/document/50763#cb979bbb36c24acc891ce2115ff2b6c6) event to receive all remote user video publish events before entering the room. When you receive `onUserVideoAvailable(userId, true)` notification, it means that the video frame is playable.
2. When a playable video frame arrives, invoke [startRemoteView](https://trtc.io/document/50762#01208b71b9c2edf6ad8ea4b8220a1d90) to subscribe to the user's remote video.

Android

iOS

Mac

Windows

```
// Set local rendering parametersTRTCCloudDef.TRTCRenderParams trtcRenderParams = new TRTCCloudDef.TRTCRenderParams();trtcRenderParams.fillMode   = TRTCCloudDef.TRTC_VIDEO_RENDER_MODE_FILL; // Render mode is filltrtcRenderParams.mirrorType = TRTCCloudDef.TRTC_VIDEO_MIRROR_TYPE_AUTO; // Mirror type is automCloud.setLocalRenderParams(trtcRenderParams);// Play the anchor's videoTXCloudVideoView cameraVideo = findViewById(R.id.txcvv_main_remote);mCloud.startRemoteView("anchor", TRTCCloudDef.TRTC_VIDEO_STREAM_TYPE_BIG, cameraVideo); // Play anchor's video content in high-definition big screen
```

```
// Set local preview rendering parametersTRTCRenderParams *trtcRenderParams = [[TRTCRenderParams alloc] init];trtcRenderParams.fillMode   = TRTCVideoFillMode_Fill;trtcRenderParams.mirrorType = TRTCVideoMirrorTypeAuto;[self.trtcCloud setLocalRenderParams:trtcRenderParams];// Play the anchor's video[self.trtcCloud startRemoteView:@"anchor" streamType:TRTCVideoStreamTypeBig view:self.remoteCameraVideoView];
```

```
// Set local preview rendering parametersTRTCRenderParams *trtcRenderParams = [[TRTCRenderParams alloc] init];trtcRenderParams.fillMode   = TRTCVideoFillMode_Fill;trtcRenderParams.mirrorType = TRTCVideoMirrorTypeAuto;[self.trtcCloud setLocalRenderParams:trtcRenderParams];// Play the anchor's video[self.trtcCloud startRemoteView:@"anchor" streamType:TRTCVideoStreamTypeBig view:self.remoteCameraVideoView];
```

```
// Play back the videoCWnd* pLocalVideoView = GetDlgItem(AFX_IDC_PICTURE);if (pLocalVideoView != nullptr) {    auto video_view = (liteav::TXView)(pLocalVideoView->GetSafeHwnd());    trtc_cloud_->startRemoteView("anchor", liteav::TRTCVideoStreamTypeBig, video_view); // Start playing the anchor's video}
```

### Switch Role

Due to the need to support up to 100,000 viewers watching simultaneously in video live broadcasts and voice chat rooms, a rule has been set that **only the host can publish their own audio and video**. Therefore, when some viewers wish to publish their own audio and video streams (in order to interact with the host), they need to first call [switchRole](https://trtc.io/document/50762#0a2b76d62a79877c408aa638b61d9b8e) to switch their role to **host**.

Android

iOS

Mac

Windows

```
// Switch to the anchormCloud.switchRole(TRTCCloudDef.TRTCRoleAnchor);// Turn on mic and camera, then the other anchor in the room will able to receive your audio and video.mCloud.startLocalAudio(TRTCCloudDef.TRTC_AUDIO_QUALITY_SPEECH);TXCloudVideoView cameraVideo = findViewById(R.id.txcvv_main_remote);
mCloud.startLocalPreview(true, cameraVideo);// Switch back to the audience when the calling is endedmCloud.switchRole(TRTCCloudDef.TRTCRoleAudience);
```

```
// Switch to the anchor[self.trtcCloud switchRole:TRTCRoleAnchor];// Turn on mic and camera, then the other anchor in the room will able to receive your audio and video.[self.trtcCloud startLocalAudio:TRTCAudioQualitySpeech];[self.trtcCloud startLocalPreview:self.view];// Switch back to the audience when the calling is ended[self.trtcCloud switchRole:TRTCRoleAudience];
```

```
// Switch to the anchor[self.trtcCloud switchRole:TRTCRoleAnchor];// Turn on mic and camera, then the other anchor in the room will able to receive your audio and video.[self.trtcCloud startLocalAudio:TRTCAudioQualitySpeech];[self.trtcCloud startLocalPreview:self.view];// Switch back to the audience when the calling is ended[self.trtcCloud switchRole:TRTCRoleAudience];
```

```
// Switch to the anchortrtc_cloud_->switchRole(TRTCRoleAnchor);// Turn on mic and camera, then the other anchor in the room will able to receive your audio and video.trtc_cloud_->startLocalAudio(TRTCAudioQualitySpeech);CWnd* pLocalVideoView = GetDlgItem(AFX_IDC_PICTURE);if (pLocalVideoView != nullptr) {	auto video_view = pLocalVideoView->GetSafeHwnd();	trtc_cloud_->startLocalPreview(video_view);}// Switch back to the audience when the calling is endedtrtc_cloud_->switchRole(TRTCRoleAudience);
```

## Contact us

If you have any suggestions or feedback, please contact `info_rtc@tencent.com`.


---
*Source: [https://trtc.io/document/64695](https://trtc.io/document/64695)*
