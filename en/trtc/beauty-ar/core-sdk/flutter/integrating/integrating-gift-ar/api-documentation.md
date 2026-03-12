# API documentation

This document describes the Flutter API documentation for Tencent Gift AR SDK, making it easy to read and use.

## FTCMediaXBase

### instance

**Description**

Get the singleton of FTCMediaXBase.

**API**

```
static FTCMediaXBase get instance
```

**Parameter description**

None

### setLicense

**Description**

Configuring a License.

**API**

```
Future<void> setLicense(String url, String key, FTCMediaLicenseListener listener) async
```

**Parameter description**

| Parameter Name | Type | Description |
| --- | --- | --- |
| url | String | License url. |
| key | String | License key. |
| callback | ILicenseCallback | Callback |

Callback declaration:

```
typedef FTCMediaLicenseListener = void Function(int errCode, String msg);
```

Common error codes for License verification

| Error Code | Description |
| --- | --- |
| 0 | Success: Succeeded |
| -1 | The input parameter is invalid, such as an empty URL or KEY. |
| -3 | Download failed. Check the network settings. |
| -4 | The TE authorization information read locally is empty, which might be caused by an I/O failure. |
| -5 | Reading VCUBE TEMP License file content is empty, might be caused by I/O failure. |
| -6 | The JSON field in the v_cube.license file is incorrect. Contact the Tencent Cloud team to fix it. |
| -7 | Signature verification failed. Contact the Tencent Cloud team to fix it. |
| -8 | Decryption failed. Contact the Tencent Cloud team to fix it. |
| -9 | The JSON field in the TELicense field is incorrect. Contact the Tencent Cloud team to fix it. |
| -10 | The TE authorization information from network resolution is empty. Contact the Tencent Cloud team to fix it. |
| -11 | Failed to write TE authorization info to the local file, which might be caused by an I/O failure. |
| -12 | Download failed. Failed to parse the local asset. |
| -13 | Authentication failure. Please check whether the so file is in the package or the so path is correctly set. |
| 3004/3005 | Invalid authorization. Contact the Tencent Cloud team to fix it. |
| 3015 | Bundle Id / Package Name mismatch. Check whether the Bundle Id / Package Name used by your App matches the applied one, and verify the correct license file is used. |
| 3018 | The authorization file has expired. Apply for renewal with Tencent Cloud. |
| Others | Contact the Tencent Cloud team to fix it. |

### setLogEnable

**Description**

Whether to enable Log output. Default is enabled.

> **Note:**On Android, save in the /sdcard/Android/data/packagename/files/TCMediaX directory. On iOS, save in the Documents/TCMediaX directory in the sandbox. You can upload logs from this directory to the backend according to business needs for locating online user issues.

**API**

```
Future<void> setLogEnable(bool enable) async
```

## FTCEffectAnimView

### FTCEffectAnimView

**Description**

Create a `FTCEffectAnimView` gift animation playback instance.

**API**

```
FTCEffectAnimView({this.controllerCallback, Key? viewKey})
```

**Parameter description**

| Parameter Name | Type | Description |
| --- | --- | --- |
| controllerCallback | FEffectViewControllerCallback | The playback controller for the current gift animation was successfully created. |

## FTCEffectViewController

### startPlay

**Description**

Start the player.

**API**

```
Future<int> startPlay(String playUrl) async
```

**Parameter description**

playUrl is the video resource address.

> **Note:**Supports only playback of local video resources on mobile phones. If you use network video resources, download them to local first before playback.

### setVideoMode

**Description**

Set the alpha and rgb area alignment mode of tep animation.

**API**

```
Future<void> setVideoMode(FVideoMode videoMode) async
```

**Parameter description**

videoMode supports the following formats:

| Enumeration Value | Description |
| --- | --- |
| FVideoMode.VIDEO_MODE_NONE | Ordinary mp4 file |
| FVideoMode.EVIDEO_MODE_SPLIT_HORIZONTAL | left-right alignment (alpha left, rgb right) |
| FVideoMode.VIDEO_MODE_SPLIT_VERTICAL | top-bottom alignment (alpha top, rgb bottom) |
| FVideoMode.VIDEO_MODE_SPLIT_HORIZONTAL_REVERSE | left-right alignment (rgb left, alpha right) |
| FVideoMode.VIDEO_MODE_SPLIT_VERTICAL_REVERSE | top-bottom alignment (rgb top, alpha bottom) |

### setConfig

**Description**

Set effect player parameters before starting playback.

**API**

```
Future<void> setConfig(FTCEffectConfig config) async
```

**Parameter description**

Refer to the following FTCEffectConfig class.

### setScaleType

**Description**

Set alignment mode.

**API**

```
Future<void> setScaleType(FScaleType type) async
```

**Parameter description**

type supports the following formats:

| Enumeration Value | Description |
| --- | --- |
| FScaleType.FIT_XY | Fully fill the entire layout with default values. |
| FScaleType.FIT_CENTER | Display the video in the middle of the layout at its original ratio. |
| FScaleType.CENTER_CROP | Fill the layout completely according to the video ratio (excess part not shown). |

### setFetchResource

**Description**

Set animation resources for fusion.

**API**

```
void setFetchResource(FResourceFetcher resFetcher)
```

**Parameter description**

FResourceFetcher API

```
class FResourceFetcher {  get image  FResImgResultFetcher? imgFetcher;  get text  FResTextResultFetcher? textFetcher;   // Resource release notification  FResReleaseListener? releaseListener;  FResourceFetcher({this.imgFetcher, this.textFetcher, this.releaseListener});}
```

FEffectResource#tag is the tag (index) for fusion animation, which can determine if the tag imports different text or image resources.

### requestUpdateResource

**Description**

Update animation info during playback.

After calling the current method, it will trigger the IFetchResource API callback to update the animation fusion info.

**API**

```
Future<void> requestUpdateResource() async
```

### setRenderRotation

**Description**

Set animation fusion and select rotation angle, support 0, 90, 180, 270, 360 degrees.

**API**

```
Future<void> setRenderRotation(int rotation) async
```

### isPlaying

**Description**

Check whether the effect player is playing.

**API**

```
Future<bool> isPlaying() async
```

### resume

**Description**

Restore special effect animation playback.

**API**

```
Future<void> resume() async
```

### pause

**Description**

Suspend special effect animation playback.

**API**

```
Future<void> pause() async
```

### seekTo

**Description**

Navigate to the specified position and start playback.

> **Note:**Call this method after startPlay(), otherwise it does not take effect.This API takes effect for tcmp4 animation or MP4 animation with FCodecType.TX_LITEAV_SDK set up.milliSec: Navigate to the specified duration and start playback, in milliseconds.

**API**

```
Future<void> seekTo(int millSec) async
```

### seekProgress

**Description**

Navigate to the specified position and start playback.

progress: Navigate to the specified percentage of the animation duration and start playback. Unit percentage, value range: [0.0-1.0].

> **Note:**Call this method after startPlay(), otherwise it does not take effect.This API takes effect for tcmp4 animation or MP4 animation with FCodecType.TX_LITEAV_SDK set up.The input parameter progress has a value range of [0.0-1.0]. Values out of range will not take effect.

**API**

```
Future<void> seekProgress(double progress) async
```

### setLoop

**Description**

Set loop playback.

- true: means loop playback.
- false: means disabling loop playback.

**API**

```
Future<void> setLoop(bool isLoop) async
```

### setLoopCount

**Description**

Set the number of loop playbacks.

loopCount: indicates the number of loop playbacks. When loopCount <= 0, it means infinite loop playback; when loopCount=n(n>=1), it means playing from start to end of playback for a total of n times.

> **Note:**The default value of loopCount is 1, meaning the animation plays only once and ends when the method is not actively called externally.The setLoop(boolean isLoop) method internally calls the current method. When isLoop = true, it is equivalent to calling setLoopCount(-1). When isLoop = false, it is equivalent to calling setLoopCount(1). Therefore, these two methods affect each other, and the later call will override the previous one.

**API**

```
Future<void> setLoopCount(int loopCount) async
```

### setDuration

**Description**

How long does it take to set the animation playback complete. After set, the animation playback speed will automatically adjust subsequently to ensure the animation stops at the set duration.

If the set duration exceeds the original animation duration, the animation will play in slow motion; if less than the original duration, it will fast-forward.

durationInMilliSec: The duration to set, in milliseconds.

> **Note:**Currently only applicable to animations in tcmp4 format.The current method and the setRate method of speed adjustment are mutually exclusive. The later call will override the earlier one.

**API**

```
Future<void> setDuration(int durationInMilliSec) async
```

### stopPlay

**Description**

Stop playback.

**API**

```
Future<void> stopPlay({bool? clearLastFrame}) async
```

### setMute

**Description**

Set mute playback.

- true: mute playback.
- false: unmuted playback.

**API**

```
Future<void> setMute(bool mute)
```

### setPlayListener

**Description**

Set the effect player playback callback.

**API**

```
void setPlayListener(FAnimPlayListener? listener)
```

**Parameter description**

IAnimPlayListener API

```
class FAnimPlayListener {  FEmptyFunction? onPlayStart;  FEmptyFunction? onPlayEnd;  FIntParamsFunction? onPlayError;  FOnPlayEventFunction? onPlayEvent;  FAnimPlayListener({this.onPlayStart, this.onPlayEnd, this.onPlayError, this.onPlayEvent});}
```

For the event value in the onPlayEvent method, see the constant values in the FTCEffectPlayerConstant class.

```
static static int REPORT_INFO_ON_PLAY_EVT_PLAY_END = 2006;static static int REPORT_INFO_ON_PLAY_EVT_RCV_FIRST_I_FRAME = 2003;static static int REPORT_INFO_ON_PLAY_EVT_CHANGE_RESOLUTION = 2009;static static int REPORT_INFO_ON_PLAY_EVT_LOOP_ONCE_COMPLETE = 6001;static static int REPORT_INFO_ON_VIDEO_CONFIG_READY = 200001;static static int REPORT_INFO_ON_NEED_SURFACE = 200002;static static int REPORT_INFO_ON_VIDEO_SIZE_CHANGE = 200003;static static int REPORT_ANIM_INFO = 200004;
```

For the errorCode value in the onPlayError method, see the constant values in the FTCEffectPlayerConstant class.

```
static const REPORT_ERROR_TYPE_HEVC_NOT_SUPPORT = -10007; // HEVC NOT supportedstatic const  REPORT_ERROR_TYPE_INVALID_PARAM = -10008; // invalid parameterstatic const  REPORT_ERROR_TYPE_INVALID_LICENSE = -10009; // INVALID LICENSEstatic const  REPORT_ERROR_TYPE_ADVANCE_MEDIA_PLAYER = -10010; // MediaPlayer playback failurestatic const  REPORT_ERROR_TYPE_MC_DECODER = -10011; // MediaCodec Decoder failurestatic const  REPORT_ERROR_TYPE_UNKNOWN_ERROR = -20000; // unknown error
```

### getTCAnimInfo

**Description**

Get current playback animation information, return FTCEffectAnimInfo instance. See FTCEffectAnimInfo for details.

> **Note:**This method must be called in FAnimPlayListener#onPlayStart() or after this method execution to obtain current animation info, otherwise return null.

**API**

```
Future<FTCEffectAnimInfo> getTCAnimInfo() async
```

## FTCEffectConfig

**Description**

Construct the effect player configuration.

**codecType property**

```
// Set CodecTypeFCodecType? codecType;
```

**Parameter description**

It has three values:

- FCodecType.TC_MPLAYER (MPLAYER playback engine)
- FCodecType.TC_MCODEC (MCODEC playback engine, takes effect on Android platform only)
- FCodecType.TX_LITEAV_SDK (Tencent Cloud Player SDK)

> **Note:**Currently only support calling the setConfig() method to set playback configuration before the player starts. Configuration modification is not supported after playback starts.Currently supports three CodecTypes, only applicable to TEP animation.If CodecType is set to FCodecType.TX_LITEAV_SDK, you need to separately import Tencent Cloud Player SDK and apply for and register its corresponding license.

```
// Set freeze frame indexFFreezeFrame? freezeFrame;
```

**Parameter description**

The input parameter frame indicates the frame to stay on during animation playback. Current value range:

- FFreezeFrame.FREEZE_FRAME_NONE: Disable freezeFrame power. The player will play, pause, and disappear normally.
- FFreezeFrame.FREEZE_FRAME_LAST: After first playback, the frame stays on the last frame.

**animType property (Android only)**

```
// Set the animation format to playFAnimType? animType;
```

**Parameter description**

Set the animation format to play, suitable for scenarios where the file suffix of the animation to play is modified. The input parameter type indicates the specified animation format. Current available values:

- FAnimType.AUTO (The SDK default policy determines the animation format by the file suffix, such as tcmp4, mp4, tep, or tepg.)
- FAnimType.MP4 (MP4 animation format. Subsequently, animation files will be played as MP4 type, ignoring the file suffix.)
- FAnimType.TCMP4 (TCMP4 animation format. Subsequently, animation files will be played as TCMP4 type, ignoring the file suffix.)

## FTCEffectAnimInfo

**Description**

Store current playback animation info.

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| type | int | Current animation type: FAnimType.MP4 (MP4 resources) and FAnimType.TCMP4 (TCMP4 resources). |
| duration | long | Animation duration: milliseconds. |
| width | int | Animation width. |
| height | int | Animation height. |
| encryptLevel | int | The current animation's advanced encryption type. If the value is 0, it means no advanced encryption. Otherwise, it indicates advanced encryption. |
| mixInfo | FMixInfo | Fusion animation info. When null, it means the animation has no fusion info. |

## FMixInfo

**Description**

Store current playback animation fusion info.

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| textMixItemList | List<FMixItem> | Text fusion info. When null, it means no text fusion info. |
| imageMixItemList | List<FMixItem> | Image fusion info. When null, it means no image fusion info. |

## FMixItem

**Description**

Store current playback animation fusion info.

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| id | String | Current fusion animation id. |
| tag | String | Current fusion animation tag. |
| text | String | Current text content of the fusion animation (empty for image fusion animations). If it is tcmp4, the value is its internal original text content; if it is mp4, the value is the tag filled in the tool. |

## FTCEffectText

**Description**

Fusion animation replaces text style data.

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| text | String | Finally replace the displayed text content. |
| color | int | Text color, format requirement: ARGB, such as 0xFFFFFFFF. |
| fontStyle | String | Text display style, valid values: "bold" means bold text, default size if not specified. |
| alignment | int | Text alignment mode, valid values: TEXT_ALIGNMENT_NONE (default value, keep SDK default alignment), TEXT_ALIGNMENT_LEFT (left), TEXT_ALIGNMENT_CENTER (center), TEXT_ALIGNMENT_RIGHT (right). |
| fontSize | double | Text size, unit is px; if text size is set (value larger than 0), the internal auto scale policy will be disabled and the set text size will be forcibly applied, which may cause oversized text not fully displayed. |


---
*Source: [https://trtc.io/document/73977](https://trtc.io/document/73977)*
