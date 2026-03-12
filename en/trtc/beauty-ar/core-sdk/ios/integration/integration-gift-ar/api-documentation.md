# API documentation

### TCMediaXBase

### getInstance

**Description**

Retrieve the singleton of TCMediaXBase.

**API**

```
+ (instancetype)getInstance;
```

### setLicense

**Description**

Configuring License.

**API**

```
- (void)setLicenceURL:(NSString *)url key:(NSString *)key;
```

**Parameter Description**

| Parameter Name | Type | Description |
| --- | --- | --- |
| url | NSString | License url |
| key | NSString | License key |

### setDelegate

**Description**

Configuring License registration result callback.

**API**

```
- (void)setDelegate:(id<TCMediaXBaseDelegate>)delegate;
```

Callback Declaration

```
- (void)onLicenseCheckCallback:(int)errcode withParam:(NSDictionary *)param;
```

Common error codes for License verification

| Error code | Description |
| --- | --- |
| 0 | Success. |
| -1 | Input parameters are invalid, such as URL or KEY is empty. |
| -3 | Download failed, please check network settings. |
| -4 | TE authorization information read from local is empty, which may be caused by IO failure. |
| -5 | The content of VCUBE TEMP License file is empty, which may be caused by IO failure. |
| -6 | The JSON field of v_cube.license file is incorrect. Please contact Tencent Cloud team for processing. |
| -7 | Signature verification failed. Please contact Tencent Cloud team for processing. |
| -8 | Decryption failed. Please contact Tencent Cloud team for processing. |
| -9 | The JSON field in the TELicense field is incorrect. Please contact Tencent Cloud team for processing. |
| -10 | TE authorization information parsed from the network is empty. Please contact Tencent Cloud team for processing. |
| -11 | Failed to write TE authorization information to local file, which may be caused by IO failure. |
| -12 | Download failed, parsing local asset also failed. |
| -13 | Authentication failed. |
| Others | Please contact Tencent Cloud team for processing. |

### setLogEnable

**Description**

Whether Log output is enabled. It starts by default.

On Android, it is saved in the /sdcard/Android/data/packagename/files/TCMediaX directory. On iOS, it is saved in the Documents/TCMediaX directory of the sandbox. You can upload the logs in this directory to the backend according to business needs, for locating online user issues.

**API**

```
- (void)setLogEnable:(BOOL)enabled;
```

### getSdkVersion

**Description**

Get the current version of the sdk.

**API**

```
- (NSString *)getSdkVersion;
```

## TCEffectAnimView

### initWithFrame

**Description**

Create TCEffectAnimView.

**API**

```
- (instancetype)initWithFrame:(CGRect)frame;
```

**Parameter Description**

frame: Frame of the View Object.

### startPlay

**Description**

Start the player.

**API**

```
- (void)startPlay:(NSString *)url;
```

**Parameter Description**

The url is the address of the video resource.

> **Note:**Supports only playing local video resources. If you use online video resources, download to local and then replay.

### setVideoMode

**Description**

Set the alignment mode of the alpha and rgb areas of the mp4 animation.

**API**

```
- (void)setVideoMode:(TCEPVAPVideoFrameTextureBlendMode)mode;
```

**Parameter Description**

The mode supports the following formats:

| Enumeration Value | Meaning |
| --- | --- |
| TCEPVAPVFTextureBlendMode_None | Ordinary mp4 file |
| TCEPVAPVFTextureBlendMode_AlphaLeft | Left-right alignment (alpha on the left, rgb on the right) |
| TCEPVAPVFTextureBlendMode_AlphaTop | Top-bottom alignment (alpha on the top, rgb on the bottom) |
| TCEPVAPVFTextureBlendMode_AlphaRight | Left-right alignment (rgb on the left, alpha on the right) |
| TCEPVAPVFTextureBlendMode_AlphaBottom | Top-bottom alignment (rgb on the top, alpha on the bottom) |

### setEffectPlayerConfig

**Description**

Set effect player parameters. A call needs to be made before starting playback.

**API**

```
- (void)setEffectPlayerConfig:(TCEffectConfig *)config;
```

**Parameter Description**

Refer to the [TCEffectConfig](https://www.tencentcloud.com/document/product/1143/70539#0bb97557-0b86-4a05-95aa-e3674a785ba5) class.

### setRenderMode

**Description**

Set alignment mode.

**API**

```
- (void)setRenderMode:(TCEPVPViewContentMode)renderMode;
```

**Parameter Description**

renderMode supports the following formats:

| Enumeration Value | Meaning |
| --- | --- |
| TCEPVPViewContentModeScaleToFill | The content is stretched to fill the entire view, possibly distorted. Default value. |
| TCEPVPViewContentModeAspectFit | The content maintains the original aspect ratio and scales to be fully displayed, with possible blank areas. |
| TCEPVPViewContentModeAspectFill | The content maintains the original aspect ratio and scales to fill the view, possibly cropping partial content. |

### effectPlayerDelegate

**Description**

TCEPAnimViewDelegate supports setting playback event callbacks for effect player sdk and setting fusion animation information.

**Playback callback API**

```
// Animation start playback callback- (void)tcePlayerStart:(ITCEffectPlayer *)player;// End of animation playback callback- (void)tcePlayerEnd:(ITCEffectPlayer *)player;// Playback error callback for animation- (void)tcePlayerError:(ITCEffectPlayer *)player error:(NSError *)error;// Player event notification- (void)onPlayEvent:(ITCEffectPlayer *)player              event:(int)EvtID          withParam:(NSDictionary *)param;
```

**Fusion animation information replace API**

```
// Replace the text placeholder in the fusion animation resource configuration, supporting attributes such as alignment mode and color in the configuration file.- (TCEffectText *)loadTextForPlayer:(ITCEffectPlayer *)player                           withTag:(NSString *)tag;// Replace the image information in the fusion animation resource// Get the tag corresponding to the current image: NSString *tag = context[TCEPContextSourceTypeImageIndex];  - (void)loadImageForPlayer:(ITCEffectPlayer *)player                   context:(NSDictionary *)context                completion:(void(^)(UIImage *image,                                    NSError *error))completionBlock;
```

**Fusion animation click API**

```
// Callback for the click event of the resources belonging to the fusion animation- (void)tcePlayerTagTouchBegan:(ITCEffectPlayer *)player tag:(NSString *)tag;
```

**Audio data callback API**

```
// Animation play audio callback- (void)tcePlayerAudioFrame:(TCEffectAudioFrameData *)audioFrameData;
```

### requestUpdateResource

**Description**

Update fusion animation information during playback, supported since version 3.2.

After calling the current method, the IFetchResource interface callback will be triggered to update the fusion animation information.

**API**

```
- (void)requestUpdateResource
```

### preloadTCAnimInfo

**Description**

Obtain the width, height, duration, and fusion animation attribute information. Support starts from version 3.3.

- playUrl: animation path address
- config: When playing the animation, if you have called the TCEffectAnimView#setEffectPlayerConfig() method and set up a TCEffectConfig instance containing extendMapParams, then at this point when calling the current preloadTCAnimInfo method, input the TCEffectConfig instance as the second parameter to ensure normal parsing, otherwise input null.

**API**

```
+ (nullable TCEffectAnimInfo *)preloadTCAnimInfo:(NSString *)playUrl config:(TCEffectConfig *)config;
```

> **Note:**For earlier versions of vap animations that exclude the vapc box, the current method cannot parse out the animation configuration message and will return null.The current method involves IO operations. Pay attention to thread calls.

### setRenderRotation

**Description**

Set the animation rotation direction.

**API**

```
- (void)setRenderRotation:(TCEP_Enum_Type_HomeOrientation)rotation;
```

**Parameter Description**

rotation supports the following formats:

| Enumeration Value | Meaning |
| --- | --- |
| TCEP_HOME_ORIENTATION_RIGHT | The HOME key is on the right, in landscape mode. |
| TCEP_HOME_ORIENTATION_DOWN | The HOME key is on the bottom, the most common vertical screen live streaming mode in mobile live streaming. |
| TCEP_HOME_ORIENTATION_LEFT | The HOME key is on the left, in landscape mode. |
| TCEPVAPVFTextureBlendMode_AlphaRight | The HOME key is on the top, vertical screen live streaming. |

### isPlaying

**Description**

Return whether the effect player is playing.

**API**

```
- (BOOL)isPlaying;
```

### resume

**Description**

Restore special effect animation playback.

**API**

```
- (void)resume;
```

### pause

**Description**

Suspend special effect animation playback.

**API**

```
- (void)pause;
```

### seekTo

**Description**

Navigate to the specified position and start playback.

> **Note:**Call this method only after startPlay(). Otherwise, it does not take effect.This API takes effect for tcmp4 animations or mp4 animations played when vapEngineType is set to TCEPCodecTypeVODPlayer.time: Navigate to the specified duration to start playback, in milliseconds.

**API**

```
- (void)seek:(float)time;
```

### seekProgress

**Description**

Navigate to the specified position and start playback.

> **Note:**Call this method only after startPlay(). Otherwise, it does not take effect.This API takes effect for tcmp4 animations or mp4 animations played when vapEngineType is set to TCEPCodecTypeVODPlayer.The input parameter progress has a value range of [0.0 - 1.0]. Values out of range do not take effect.progress: Start playback at the specified percentage of the animation duration. Unit percentage. Value range: [0.0 - 1.0].

**API**

```
- (void)seekProgress:(float)progress;
```

### setLoop

**Description**

Set loop playback.

- YES: Indicates loop playback.
- NO: Means disabling loop playback.

**API**

```
- (void)setLoop:(BOOL)loop;
```

### setLoopCount

**Description**

Set the number of loop playbacks.

loopCount: Indicates the number of loop playbacks. When loopCount <= 0, it means infinite loop playback; when loopCount = n (n >= 1), it means playing from start to end for n times.

> **Note:**The default value of loopCount is 1, that is, when the external does not actively call this method, the animation plays only once and then ends.The setLoop method will call the current method internally. That is, when isLoop = true, it is equivalent to calling setLoopCount(-1); when isLoop = false, it is equivalent to calling setLoopCount(1). Therefore, these two methods affect each other, and the later call will overwrite the previous one.

**API**

```
- (void)setLoopCount:(int)loopCount;
```

### setDuration

**Description**

How long does it take to complete the animation set? After setting, the animation playback speed will be automatically adjusted during subsequent animation playback to ensure that the animation stops at the set duration.

That is, if the set duration exceeds the original duration of the animation, the animation will be played in slow motion; if it is less than the original duration of the animation, it will be fast-forwarded.

> **Note:**Currently only applicable to animations in tcmp4 format.The current method and the method of setting the playback speed via setRate are mutually exclusive. The later-called one will override the earlier-called one.durationInMilliSec: The duration to be set, in milliseconds.

**API**

```
- (void)setDuration:(long)durationInMilliSec;
```

### stopPlay

**Description**

Stop playback.

**API**

```
- (void)stopPlay;
```

### setMute

**Description**

Set whether to play in mute.

- YES: Play in mute.
- NO: Play unmuted.

**API**

```
- (void)setMute:(BOOL)bEnable;
```

### getTCAnimInfo

**Description**

Retrieve the information corresponding to the current playback animation and return a TCEffectAnimInfo instance. For details, see [TCEffectAnimInfo](https://www.tencentcloud.com/document/product/1143/70539#cc3dc4bf-4ad4-4466-a4c8-fe6b17d315d4).

> **Note:**This method must be called within the IAnimPlayListener#onPlayStart() method or after this method execution to obtain the current animation information; otherwise, it returns null.

**API**

```
- (nullable TCEffectAnimInfo *)getAnimInfo;
```

## TCEffectConfig

**Description**

Construct special effect player configuration. Supported attributes:

1. vapEngineType(CodecType type): It has two parameter values, which are:
  - TCEPCodecTypeAVPlayer, the default playback engine for gift animation special effects.
  - TCEPCodecTypeVODPlayer, the playback engine of Tencent Cloud Player SDK.

```
// Set playback configuration, an optional step.TCEffectConfig *config = [[TCEffectConfig alloc] init];[self.alphaAnimView setEffectPlayerConfig:config];
```

> **Note:**Currently, you can only call the setEffectPlayerConfig method before the player starts to set the playback configuration. Configuration modification is not supported after playback starts.The currently supported 2 vapEngineTypes are only applicable to MP4 animations.If you set vapEngineType to TCEPCodecTypeVODPlayer, you also need to separately introduce the Tencent Cloud Player SDK, as well as apply for and register its corresponding license.

2. freezeFrame are used to set the freeze frame of playing animation. Current optional values:
  - FRAME_NONE: Default value. Disable the freezeFrame capacity. The player plays, pauses, and disappears normally.
  - FRAME_FIRST: After playback finished, restart playing and pause when the first frame of the next time appears.
  - FRAME_LAST: After the first playback finished, the visual stays on the last frame.
3. enableAudioFrameCallback  turn on the callback switch for playing audio, suitable for scenarios where event listening processing is needed for gift animation audio tracks.

> **Note:**Currently only support calling the setEffectPlayerConfig() method to set the playback configuration before the player starts. Configuration modification is not supported after playback starts.This parameter is valid only when CodecType is TCEPCodecTypeVODPlayer and the event type is MP4/TEP.After turning on the switch, you can set up monitoring through the TCEPAnimViewDelegate#tcePlayerAudioFrame method.

4. enableProgressCallback turn on the playing animation
5. progressCallbackIntervalMs  The progress callback interval for playing animations, in milliseconds. Default value: 200 ms.

> **Note:**Note that this configuration is effective only when the enableProgressCallback switch is on.After turning on the switch, you can listen for the event TCEPConstant.TCEP_PLAYER_EVT_PROGRESS in the TCEPAnimViewDelegate#onPlayEvent callback to obtain the current playback progress. Use TCEPEventProgressMSKey and TCEPEventDurationMSKey to respectively obtain the current playback duration and total duration (in milliseconds) from the param.Set a reasonable time interval. Too small an interval may affect performance.

## TCEffectAnimInfo

**Description**

Store information of the current playback animation

**{Attribute description}**

| Attribute Name | Type | Description |
| --- | --- | --- |
| type | TCEPAnimResourceType | Current animation type, Value: TCEPAnimResourceTypeMP4 MP4 resources, TCEPAnimResourceTypeTCMP4 TCMP4 resources. |
| duration | long | Animation duration, milliseconds. |
| width | int | Animation width. |
| height | int | Animation height. |
| encryptLevel | TCEPEncryptLevelType | The advanced encryption type of the current animation. If the value is TCEffectAnimInfo#ENCRYPT_LEVEL_NONE, it means there is no advanced encryption; otherwise, it means the animation has been advanced encrypted. |

## TCEffectText

**Description**

Fusion animation replacement text style data class.

**{Attribute description}**

| Attribute Name | Type | Description |
| --- | --- | --- |
| text | NSString | The text content to be displayed will eventually be replaced. |
| color | UIColor | Text color, format requirement: ARGB, for example, 0xFFFFFFFF. |
| fontStyle | NSString | Text display style. Valid values: "bold" indicates bold text. If not specified, the default size will be used. |
| alignment | int | Text alignment mode. Valid values: TCEPTextAlignmentNone (default value, that is, keep the default alignment mode of the sdk), TCEPTextAlignmentLeft (left-aligned), TCEPTextAlignmentCenter (centered), TCEPTextAlignmentRight (right-aligned). |
| fontSize | CGFloat | Text size, unit: px; if the text size is set (value greater than 0), the internal Auto Scaling policy will be disabled, and the set text size will be forcibly used as the standard, which may cause the problem of oversized text not being fully displayed. |

## TCEffectAudioFrameData

**Description**

audio track callback audio data class

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| data |  uint8_t** | Audio sample dataWhen the data is non-planar, data[0] stores the data; when the data is planar, data[0] to data[channels-1] store each sound channel. |
| size | int* | Audio sample data sizeWhen the data is non-planar, size[0] stores the data length; when the data is planar, size[0] to size[channels-1] store each sound channel size. |
| format | int | Audio format |
| channelLayout | uint64_t | channel layout of audio |
| sampleRate | unsigned int | Audio sampling rate |
| channels | int | number of sound channels |
| nbSamples | int | sampling number of each sound channel |
| ptsMs | int64_t | current sample PTS |


---
*Source: [https://trtc.io/document/70539](https://trtc.io/document/70539)*
