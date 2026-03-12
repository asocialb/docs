# Usage Guide

This document will introduce in detail how to use Tencent Gift AR  SDK quickly in the project. Just follow the following steps to complete the configuration and usage of the SDK.

## Initialize Registration License

When using Tencent Gift AR SDK officially, you need to configure the License first. After the License is configured successfully, you can use the SDK subsequently.

The methods for configuring the License are as follows:

> **Note:**The example code here sets the License when the application starts. But it is not recommended to trigger it here in your project, because there may not be network permission or the network connection failure rate may be relatively high (especially when starting the application for the first time) at this time. Please select a more suitable timing to set the License.

```
#import <TCMediaX/TCMediaX.h>@interface AppDelegate ()<TCMediaXBaseDelegate>@end  @implementation AppDelegate// Replace LICENCE_URL with your own LICENCE_URL when in usestatic NSString *LICENCE_URL = @"";static NSString *LICENCE_KEY = @"";- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {    // Override point for customization after application launch.   [[TCMediaXBase getInstance] setLicenceURL:LICENCE_URL key:LICENCE_KEY];   [[TCMediaXBase getInstance] setDelegate:self];    return YES;}#pragma mark - TCMediaXBaseDelegate- (void)onLicenseCheckCallback:(int)errcode withParam:(NSDictionary *)param {    // Note: This callback may not be on the calling thread.    NSLog(@"onLicenseCheckCallback:%d",errcode);    if (errcode == TMXLicenseCheckOk) {        // Authentication successful    } else {        // Authentication failure    }}@end
```

> **Note:**The License features strong online verification logic. When calling TCMediaXBase#setLicense after the application starts for the first time, network must be available. At the first launch of the App, network permission may not yet be authorized. You need to wait until permission is granted and then call TCMediaXBase#setLicense again.Listen to the loading result of TCMediaXBase#setLicence: ILicenseCallback#onResult API. If it fails, retry and guide according to the actual situation. If there are multiple failures, limit frequency and supplement with product pop-ups and other guides to allow users to check network conditions.For multi-process Apps, ensure that TCMediaXBase#setLicense is called when each process using the Gift AR  player starts. For example, for Apps that use a separate process to play effects on the Android side, TCMediaXBase#setLicense should also be called when the process is killed and restarted by the system during background playback.

**Authentication error code description:**

| Error Code | Description |
| --- | --- |
| 0 | Successful. |
| -1 | The input parameter is invalid. For example, the URL or KEY is empty. |
| -3 | The download process failed. Check the network settings. |
| -4 | The TE authorization information read locally is empty, which might be caused by an I/O failure. |
| -5 | The file content of the VCUBE TEMP License file is empty, which might be caused by an I/O failure. |
| -6 | The JSON field of the v_cube.license file is incorrect. Contact the Tencent Cloud team to handle it. |
| -7 | Signature verification failed. Contact the Tencent Cloud team to handle it. |
| -8 | Decryption failed. Contact the Tencent Cloud team to handle it. |
| -9 | The JSON field in the TELicense field is incorrect. Contact the Tencent Cloud team to handle it. |
| -10 | The TE Authorization information from network resolution is empty. Contact the Tencent Cloud team to handle it. |
| -11 | Failed to write the TE authorization information to the local file. It might be caused by an IO failure. |
| -12 | Download failed, and parsing the local asset also failed. |
| -13 | Authentication Failure |
| Other | Contact the Tencent Cloud team to handle it. |

## Log Management

Tencent Effect Player SDK supports saving running logs by default. If problems occur during the test, you can extract the logs and give feedback to Tencent Cloud customer service. You can upload the logs in this directory to the backend according to business needs for locating online user problems.

The log of Tencent Effect Player SDK iOS version is saved in the sandbox Documents/TCMedialog folder, and the log file is named by date. For detailed log export tutorial, [refer here](https://www.tencentcloud.com/document/product/1143/70544#59b6468e-c7a0-48da-9b96-94c85e49e48c).

Playback log is enabled for saving by default. If you need to disable it, you can pass in NO through `TCMediaXBase#setLogEnable` to disable it.

## Player Usage

### Initializing TCEffectAnimView

```
- (TCEffectAnimView *)alphaAnimView {    if (!_alphaAnimView) {        _alphaAnimView = [[TCEffectAnimView alloc] init];        _alphaAnimView.backgroundColor = [UIColor clearColor];        _alphaAnimView.effectPlayerDelegate = self;        _alphaAnimView.loop = YES;        [_alphaAnimView setRenderMode:TCEPVPViewContentModeScaleToFill];    }    return _alphaAnimView;}
```

### Add AlphaAnimView and Layout

```
// Add alphaAnimView[self.view addSubview:self.alphaAnimView];// Layoutself.alphaAnimView.frame = self.view.bounds;
```

### Playback and Listen

You can listen to the animation playback status by setting the `effectPlayerDelegate` proxy method before starting playback:

```
self.alphaAnimView..effectPlayerDelegate = self;#pragma mark - TCEPAnimViewDelegate // Animation starts playing- (void)tcePlayerStart:(ITCEffectPlayer *)player {    NSLog(@"player = %p, start..", player);}// Animation stops playback- (void)tcePlayerEnd:(ITCEffectPlayer *)player {    NSLog(@"player = %p, end..", player);}// Animation playback failure-  (void)tcePlayerError:(ITCEffectPlayer *)player error:(NSError *)error {    NSLog(@"player = %p, error..", player);}// Animation playback event- (void)onPlayEvent:(ITCEffectPlayer *)player              event:(int)EvtID          withParam:(NSDictionary *)param {    NSLog(@"player = %p, EvtID = %@", player, @(EvtID));}
```

### Get Video Resources and Perform Playback

> **Note:**Supports only playing local video resources. If you use online video resources, download to local and replay.Animated resources can be generated through [Gift AR  conversion tool](https://www.tencentcloud.com/document/product/1143/70541). Besides, VAP format animated resources can also be played.

```
 [self.alphaAnimView startPlay:localPathUrl];
```

### Fusion Animation Configuration

To realize fusion animation, it is required to implement the TCEffectAnimViewDelegate proxy method.

#### Fusion Animation Text Replacement

Replace text, and specify the alignment mode, color, and whether it is bold text of the specified text, using the loadTextForPlayer API.

```
// Replace text, and specify the alignment mode, color, and whether it is bold of the text. Use the loadTextForPlayer API. It is recommended to use this API.- (TCEffectText *)loadTextForPlayer:(ITCEffectPlayer *)player                            withTag:(NSString *)tag {    if (tag != nil && [tag isEqualToString:@"name"]) {        TCEffectText *effectText = [[TCEffectText alloc] init];        effectText.text = @"reText";        // TCEPTextAlignmentLeft = 0,     ///< Text aligns left        // TCEPTextAlignmentCenter = 1,   ///< Text aligns center        // TCEPTextAlignmentRight = 2     ///< Text aligns right        effectText.alignment = TCEPTextAlignmentLeft;         //effectText.fontStyle = @"bold";        //effectText.color = [UIColor blackColor];        return effectText;;    }    return nil;}
```

#### Fusion Animation Image Replacement

Retrieve the UIImage by obtaining the tag value. The fusion animation player does not handle the conversion process internally. Handle it yourself in this method.

```
- (void)loadImageForPlayer:(ITCEffectPlayer *)player                   context:(NSDictionary *)context                completion:(void(^)(UIImage *image,                                    NSError *error))completionBlock {    dispatch_async(dispatch_get_main_queue(), ^{        // Obtain the current tag of the image to be replaced, then return the image according to the tag        NSString *tag = context[TCEPContextSourceTypeImageIndex];           ...        // Download and cache the image        if (image) {            completionBlock(image, nil);        } else {            completionBlock(nil, error);        }        }];    });}
```

Listen to the event that the custom resource of the animation is clicked, and distinguish different fusion animation areas by tag.

```
- (void)tcePlayerTagTouchBegan:(ITCEffectPlayer *)player tag:(NSString *)tag {    NSString *content = [NSString stringWithFormat:@"Clicked: %@", tag];    [self.view tuiad_alert:content];}
```

#### Animation Property Retrieval

To obtain the width, height, duration, and fusion animation property information before playback, the following solution can be achieved:

```
TCEffectAnimInfo* animInfo = [TCEffectAnimView preloadTCAnimInfo:playPath config:config];
```

- playPath: the path address of the animation to obtain information, similar to the passed parameters when calling the TCEffectAnimView#startPlay() method.
- config: TCEffectConfig instance, used to specify additional configuration for the animation

> **Note:**When playing an animation, if you have called the TCEffectAnimView#setEffectPlayerConfig() method and set up a TCEffectConfig instance containing extendMapParams, then when calling the current preloadTCAnimInfo method, pass this TCEffectConfig instance as the second input parameter to ensure normal parsing, otherwise just pass null.For earlier versions of vap animations that exclude the vapc box, the current method cannot parse out the animation configuration message and will return null.The current method involves IO operations. Pay attention to thread calls.

### Playback Configuration

```
// Set playback configuration, optional stepsTCEffectConfig *config = [[TCEffectConfig alloc] init];[self.alphaAnimView setEffectPlayerConfig:config];
```

TCEffectConfig currently supports:

1. vapEngineType(CodecType type): It has two parameter values, which are:
  - TCEPCodecTypeAVPlayer, the default playback engine for gift animation special effects.
  - TCEPCodecTypeVODPlayer, the playback engine of Tencent Cloud Player SDK.

> **Note:**Currently, you can only call the setEffectPlayerConfig method before the player starts to set the playback configuration. Configuration modification is not supported after playback starts.The currently supported 2 vapEngineTypes are only applicable to MP4 animations.If you set vapEngineType to TCEPCodecTypeVODPlayer, you also need to separately introduce Tencent Cloud Player SDK, as well as apply for and register its corresponding license.

2. freezeFrame is used to set the freeze frame for playing animations. Current available values:
  - FRAME_NONE: Default value. Disable the freezeFrame capacity. The player will playback normally and the pause will disappear.
  - FRAME_FIRST: After playback is finished, restart playing and pause when the first frame appears next time.
  - FRAME_LAST: When playback is finished for the first time, the visual stays on the last frame.
3. enableAudioFrameCallbackï¼Turn on the audio callback switch during playback, suitable for scenarios where listening and processing gift animation audio tracks is required.

> **Note:**Currently only support calling the setEffectPlayerConfig() method to set the playback configuration before the player starts. Configuration modification is not supported after playback starts.This parameter is valid only when CodecType is TCEPCodecTypeVODPlayer and the animation type is MP4/TEP.After turning on the switch, you can use the TCEPAnimViewDelegate#tcePlayerAudioFrame method to listen for callbacks

4. enableProgressCallbackï¼ Turn on the playing animation progress callback.
5. progressCallbackIntervalMsï¼ The progress callback interval for playing animations, in milliseconds, with a default value of 200 ms.

> **Note:**Note: This configuration is effective only when the enableProgressCallback switch is on.After turning on the switch, you can listen for the event TCEPConstant.TCEP_PLAYER_EVT_PROGRESS in the TCEPAnimViewDelegate#onPlayEvent callback to obtain the current playback progress.Do not set the time interval too low. A too small interval may affect performance.

### Playback Control

#### Start Playing

TCEffectPlayer supports playback of resource file formats .mp4, .tcmp4.

> **Note:**Supports only playing local video resources. If you use online video resources, download to local and replay.Animated resources can be generated through [Gift AR conversion tool](https://www.tencentcloud.com/document/product/1143/70541). Besides, VAP format animated resources can also be played.

```
NSString *mp4Url = @"xxx/xxx/tuiad_vapx_cool_sss.mp4"];[self.alphaAnimView startPlay:mp4Url];
```

#### Pause Playing

```
[self.alphaAnimView pause];
```

#### Continue Playing

```
[self.alphaAnimView resume];
```

#### Stop Playback

When the player is no longer needed, stop playback and release the occupied resources.

```
[self.alphaAnimView stopPlay];
```

#### Mute Playback

```
[self.alphaAnimView setMute:YES];
```

#### Loop Playback

```
[self.alphaAnimView setLoop:YES];
```

## Common Issues

### What Should Be Done If the Following Log Information Appears during the Playback Process?

```
License checked failed! tceffect player license required!
```

Please check whether you have applied for the Gift AR  player License and completed the initialization registration.

### How to Extract Running Logs?

Extract running logs of Gift AR  Player. Please see [Log Management](https://www.tencentcloud.com/document/product/1143/70538#5f064c39-0316-4160-b900-ebbbdc3285ab).

## Common Error Codes

| Error Code | Description |
| --- | --- |
| -10003 | Failed to create thread. |
| -10004 | Failed to create render. |
| -10005 | Configuration parsing failure |
| -10006 | Unable to read the file. |
| -10007 | The animation video encoding format is H.265, which is not supported on the current device. |
| -10008 | Invalid parameter |
| -10009 | Invalid license |
| -10010 | Emulator is not supported. |
| -100200 | Signature verification failed |
| -100201 | Decryption of data failed. |
| -100202 | BundleID or PackageName is not the same. |
| -100203 | Resource expiration. |
| -100204 | Incorrect JSON field |
| -100205 | The boxType is not supported. |
| -100206 | Fusion animation resource acquisition failed. |


---
*Source: [https://trtc.io/document/70538](https://trtc.io/document/70538)*
