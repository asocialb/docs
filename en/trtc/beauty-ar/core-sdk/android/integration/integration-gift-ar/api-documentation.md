# API documentation

This document mainly introduces the Android API documentation of Tencent Gift AR SDK for easy reading and use.

## TCMediaXBase

### getInstance

**Description**

Retrieve the singleton of TCMediaXBase.

**API**

```
public static TCMediaXBase getInstance()
```

**Parameter Description**

None

### setLicense

**Description**

Configuring License.

**API**

```
public void setLicense(Context context, String url, String key, ILicenseCallback callback)
```

**Parameter Description**

| Parameter Name | Type | Description |
| --- | --- | --- |
| Context | Context | Application Context |
| url | String | License url |
| key | String | License key |
| callback | ILicenseCallback | Callback |

Callback declaration:

```
public interface ILicenseCallback {    void onResult(final int errCode, final String msg);}
```

Common error codes for License verification:

| Error Code | Description |
| --- | --- |
| 0 | Succeeded. |
| -1 | The input parameter is invalid. For example, the URL or KEY is empty. |
| -3 | The download process fails. Check the network settings. |
| -4 | The TE authorization information read locally is empty, which might be caused by an I/O failure. |
| -5 | The file content of the VCUBE TEMP License file is empty. It might be caused by an I/O failure. |
| -6 | The JSON field of the v_cube.license file is incorrect. Contact the Tencent Cloud team to handle it. |
| -7 | Signature verification failed. Contact the Tencent Cloud team to handle it. |
| -8 | Decryption failed. Contact the Tencent Cloud team to handle it. |
| -9 | The JSON field in the TELicense field is incorrect. Contact the Tencent Cloud team to handle it. |
| -10 | The TE authorization information from network resolution is empty. Contact the Tencent Cloud team to handle it. |
| -11 | Failed to write TE authorization information to a local file. It might be caused by an I/O failure. |
| -12 | Download failed, and parsing the local asset also failed. |
| -13 | Authentication failure. Please check if the so file is in the package, or if the so path has been correctly set. |
| 3004/3005 | Invalid authorization. Contact the Tencent Cloud team to handle it. |
| 3015 | The Bundle Id / Package Name does not match. Check whether the Bundle Id / Package Name used by your App is consistent with the applied one and whether the correct authorization file is used. |
| 3018 | The license file has expired. You need to apply for renewal from Tencent Cloud. |
| Other | Contact the Tencent Cloud team to handle it. |

### setLogEnable

**Description**

Whether Log output is enabled. It starts by default.

> **Note:**Save in the /sdcard/Android/data/packagename/files/TCMediaX directory on the Android side. You can upload the logs in this directory to the backend according to business needs for locating online user issues.

**API**

```
public void setLogEnable(Context context, boolean enable)
```

## TCEffectAnimView

### startPlay

**Description**

Start the player.

**API**

```
public int startPlay(String playUrl)
```

**Parameter Description**

playUrl is the video resource address.

> **Note:**Supports only playing local video resources on sdcard. If you use online video resources, download to local and then replay.

### setVideoMode

**Description**

Set the alignment mode of the alpha and rgb areas of the tep animation.

**API**

```
public void setVideoMode(TCEffectPlayerConstant.VideoMode mode)
```

**Parameter Description**

mode supports the following formats:

| Enumeration Value | Description |
| --- | --- |
| TCEffectPlayerConstant.VideoMode#VIDEO_MODE_NONE | Ordinary mp4 file. |
| TCEffectPlayerConstant.VideoMode#VIDEO_MODE_SPLIT_HORIZONTAL | Left-right alignment (alpha on the left, rgb on the right). |
| TCEffectPlayerConstant.VideoMode#VIDEO_MODE_SPLIT_VERTICAL | Top-bottom alignment (alpha on the top, rgb on the bottom). |
| TCEffectPlayerConstant.VideoMode#VIDEO_MODE_SPLIT_HORIZONTAL_REVERSE | Left-right alignment (rgb on the left, alpha on the right). |
| TCEffectPlayerConstant.VideoMode#VIDEO_MODE_SPLIT_VERTICAL_REVERSE | Top-bottom alignment (rgb on the top, alpha on the bottom). |

### setConfig

**Description**

Set the parameters of the effect player. A call needs to be made before starting to play.

**API**

```
public void setConfig(TCEffectConfig config)
```

**Parameter Description**

Refer to the TCEffectConfig class below.

### setScaleType

**Description**

Set Alignment Mode

**API**

```
public void setScaleType(TCEffectPlayerConstant.ScaleType type)
```

**Parameter Description**

type supports the following formats:

| Enumeration Value | Description |
| --- | --- |
| TCEffectPlayerConstant.ScaleType.FIT_XY | Complete fill the entire layout, default value. |
| TCEffectPlayerConstant.ScaleType.FIT_CENTER | Display fully in the middle of the layout according to the video ratio. |
| TCEffectPlayerConstant.ScaleType.CENTER_CROP | Fill the layout completely according to the video ratio (do not display the excess part). |

### setFetchResource

**Description**

Set the resources belonging to the fusion animation.

**API**

```
public void setFetchResource(IFetchResource fetchResource)
```

**Parameter Description**

IFetchResource interface:

```
public interface IFetchResource {    // Get image    void fetchImage(Resource resource, IFetchResourceImgResult result);    // Get text    void fetchText(Resource resource, IFetchResourceTxtResult result);    // Resource release notification    void releaseResource(List<Resource> resources);}
```

resource.tag is the tag (index) for fusion animation. It can determine if the tag imports different text or image resources.

### setOnResourceClickListener

**Description**

Set the click event of the resources belonging to the fusion animation.

**API**

```
public void setOnResourceClickListener(OnResourceClickListener listener)
```

**Parameter Description**

OnResourceClickListener API:

```
public interface OnResourceClickListener {    void onClick(Resource resource);}
```

Distinguish the resources belonging to the fusion animation based on resource.tag.

### requestUpdateResource

**Description**

Update fusion animation information during playback, supported since version 3.2.

After calling the current method, the IFetchResource interface callback will be triggered to update the fusion animation information.

**API**

```
public void requestUpdateResource()
```

### setAudioFrameDataListener

**Description**

Listen to audio callback for audio tracks during animation playback. Supported starting from version 3.3. To enable the audio track callback switch, see: TCEffectConfig#enableAudioFrameCallback().

**API**

```
public void setAudioFrameDataListener(ITCEffectAudioFrameDataListener audioFrameDataListener)
```

### preloadTCAnimInfo

**Description**

Obtain the width, height, duration, and fusion animation metadata. Supported starting from version 3.3.

- playUrl: animation path address
- config: When playing the animation, if you have called the TCEffectAnimView#setConfig() method and set up a TCEffectConfig instance containing extendMapParams(), then at this point when calling the current preloadTCAnimInfo method, input the TCEffectConfig instance as the second parameter to ensure normal parsing, otherwise just input null.

**API**

```
public static TCEffectAnimInfo preloadTCAnimInfo(String playUrl, TCEffectConfig config)
```

> **Note:**For earlier versions of vap animations that exclude vapc box, the current method cannot parse out the animation configuration message and will return null.The current method involves IO operations and is not recommended to call in the main thread.

### setRenderRotation

**Description**

Set the rotation angle for the fusion animation. Rotation angles of 0, 90, 180, 270, and 360 degrees are supported.

**API**

```
public void setRenderRotation(int rotation)
```

### isPlaying

**Description**

Return whether the effect player is playing.

**API**

```
public boolean isPlaying()
```

### resume

**Description**

Restore effect animation playback.

**API**

```
public void resume()
```

### pause

**Description**

Suspend effect animation playback.

**API**

```
public void pause()
```

### seekTo

**Description**

Navigate to the specified position and start playback.

> **Note:**You can call this method only after startPlay(). Otherwise, it does not take effect.This API takes effect for tcmp4 animations or mp4 animations played when TCEffectConfig.CodecType.TX_LITEAV_SDK is set.milliSec: Navigate to the specified duration to start playback, in milliseconds.

**API**

```
public void seekTo(long milliSec)
```

### seekProgress

**Description**

Navigate to the specified position and start playback.

progress: Navigate to the specified percentage of the animation duration to start playback, unit percentage, value range: [0.0-1.0]

> **Note:**You can call this method only after startPlay(). Otherwise, it does not take effect.This API takes effect for tcmp4 animations or mp4 animations played when TCEffectConfig.CodecType.TX_LITEAV_SDK is set.The input parameter progress has a value range of [0.0-1.0]. Values outside this range will not take effect.

**API**

```
public void seekProgress(float progress)
```

### setLoop

**Description**

Set loop playback.

- true: Indicates loop playback.
- false: Means disabling loop playback.

**API**

```
public void setLoop(boolean isLoop)
```

### setLoopCount

**Description**

Set the number of loop playbacks.

loopCount: Indicates the number of loop playbacks. When loopCount â¤ 0, it means infinite loop playback; when loopCount=n (nâ¥1), it means playing from start playback to end of playback for n times.

> **Note:**The default value of loopCount is 1, that is, when the external does not actively call this method, the animation plays only once and then ends.The setLoop(boolean isLoop) method will call the current method internally. That is, when isLoop = true, it is equivalent to calling setLoopCount(-1); when isLoop = false, it is equivalent to calling setLoopCount(1). Therefore, these two methods affect each other, and the later call will overwrite the earlier call.

**API**

```
public void setLoopCount(int loopCount)
```

### setDuration

**Description**

How long does it take to set the animation to play complete. After the settings, the playback speed of subsequent animations will be automatically adjusted to ensure that the animation plays complete within the set duration.

That is: If the set duration exceeds the original duration of the animation, the animation will be played in slow motion; if it is less than the original duration of the animation, it will be fast-forwarded.

durationInMilliSec: The duration to be set, in milliseconds.

> **Note:**Currently only applicable to animations in tcmp4 format.The current method and the setRate method for setting the playback speed are mutually exclusive. The later-called one will override the earlier-called one.

**API**

```
public void setDuration(long durationInMilliSec)
```

### stopPlay

**Description**

Stop playback.

**API**

```
public void stopPlay(boolean clearLastFrame)
```

### setMute

**Description**

Set whether to play in mute.

- true: Play in mute.
- false: Play unmuted.

**API**

```
public void setMute(boolean mute)
```

### setPlayListener

**Description**

Set the playback callback of the effect player.

**API**

```
public void setPlayListener(IAnimPlayListener listener)
```

**Parameter Description**

IAnimPlayListener interface:

```
public interface IAnimPlayListener {    void onPlayStart();    void onPlayEnd();    void onPlayError(int errorCode);        void onPlayEvent(int event, Bundle param);}
```

For the event value in the onPlayEvent method, see the constant values in the TCEffectPlayerConstant class:

```
public static final int REPORT_INFO_ON_PLAY_EVT_PLAY_END = 2006;public static final int REPORT_INFO_ON_PLAY_EVT_RCV_FIRST_I_FRAME = 2003;public static final int REPORT_INFO_ON_PLAY_EVT_CHANGE_RESOLUTION = 2009;public static final int REPORT_INFO_ON_PLAY_EVT_LOOP_ONCE_COMPLETE = 6001;public static final int REPORT_INFO_ON_VIDEO_CONFIG_READY = 200001;public static final int REPORT_INFO_ON_NEED_SURFACE = 200002;public static final int REPORT_INFO_ON_VIDEO_SIZE_CHANGE = 200003;public static final int REPORT_ANIM_INFO = 200004;
```

For the errorCode value in the onPlayError method, see the constant values in the TCEffectPlayerConstant class:

```
public static final int REPORT_ERROR_TYPE_HEVC_UNSUPPORTED = -10007; // Unsupported h265public static final int REPORT_ERROR_TYPE_INVALID_PARAM = -10008; // Invalid parameterpublic static final int REPORT_ERROR_TYPE_INVALID_LICENSE = -10009; // INVALID LICENSEpublic static final int REPORT_ERROR_TYPE_ADVANCE_MEDIA_PLAYER = -10010; // MediaPlayer playback failurepublic static final int REPORT_ERROR_TYPE_MC_DECODER = -10011; // Decoder failure in MediaCodecpublic static final int REPORT_ERROR_TYPE_UNKNOWN_ERROR = -20000; // Unknown error
```

### getTCAnimInfo

**Description**

Retrieve the information corresponding to the current playback animation. Return a TCEffectAnimInfo instance. For details, see [TCEffectAnimInfo](https://www.tencentcloud.com/document/product/1143/70533#30b9e35a-0dd0-4f82-9416-e0a1997de157).

> **Note:**This method must be called within the IAnimPlayListener#onPlayStart() method or after this method is executed to obtain the information of the current animation. Otherwise, it returns null.

**API**

```
public TCEffectAnimInfo getTCAnimInfo()
```

### getTCEffectPlayer

**Description**

Retrieve a TCEffectPlayer instance.

**API**

```
public TCEffectPlayer getTCEffectPlayer()
```

### onDestroy

**Description**

Stop playback and release resources.

**API**

```
public void onDestroy()
```

## TCEffectConfig

**Description**

Construct the player configuration for effects. It needs to be constructed via Builder.

**Builder API**

```
// Set CodecTypepublic Builder setCodecType(CodecType type)
```

**Parameter Description**

setCodecType(CodecType type): It has three parameter values, which are:

- TCEffectConfig.CodecType.TC_MPLAYER (MPLAYER playback engine)
- TCEffectConfig.CodecType.TC_MCODEC(MCODEC playback engine)
- TCEffectConfig.CodecType.TX_LITEAV_SDK (Tencent Cloud Player SDK)

```
// Set the playback configuration. It is an optional step.TCEffectConfig config = new TCEffectConfig.Builder().setCodecType(TCEffectConfig.CodecType.TC_MPLAYER).build();mPlayerView.setConfig(config);
```

> **Note:**Currently, you can only call the setConfig() method before the player starts to set the playback configuration. Configuration modification is not supported after playback starts.The three currently supported CodecTypes are only applicable to TEP animations.If the CodecType is set to TCEffectConfig.CodecType.TX_LITEAV_SDK, you also need to separately introduce the Tencent Cloud Player SDK and apply for and register its corresponding license. If config is not set, CodecType = TCEffectConfig.CodecType.TC_MPLAYER will be used by default.

```
// Set the freeze stay frame indexpublic Builder setFreezeFrame(int frame)
```

**Parameter Description**

The input parameter frame indicates which frame to stay at during animation playback. Current available values:

- TCEffectConfig.FREEZE_FRAME_NONE: Disable the freezeFrame capability, and the player resumes normal playback without any pause or disappearance.
- TCEffectConfig.FREEZE_FRAME_LAST: After the first playback is finished, the visual stays on the last frame.

```
// Set the animation format to be played nextpublic Builder setAnimType(AnimType type)
```

**Parameter Description**

Used to specify the animation format to be played subsequently, applicable to scenarios where the file suffix of the animation to be played has been modified in some cases. The input parameter type indicates the animation format to be specified. Current available values:

- TCEffectConfig.AnimType.AUTO (The default sdk policy, that is, determine the animation format by the suffix of the animation file, such as tcmp4/mp4/tep/tepg formats).
- TCEffectConfig.AnimType.MP4 (MP4 animation format, all subsequent animations will be played as MP4 type, ignoring the file extension).
- TCEffectConfig.AnimType.TCMP4 (TCMP4 animation format, all subsequent animations will be played as TCMP4 type, ignoring the file extension).

```
public Builder enableAudioFrameCallback(boolean enableAudioFrameCallback)
```

**Parameter description**

Enable the audio callback switch during playback, suitable for scenarios where gift animation audio tracks need to be listened to and processed.

> **Note:**Currently only support calling the setConfig() method to set playback configuration before the player starts. Configuration modification is not supported after playback starts.This parameter is valid only when CodecType is TCEffectConfig.CodecType.TX_LITEAV_SDK and the animation kind is MP4/TEP.After turning on the switch, you can set up the callback listener through TCEffectAnimView#setAudioFrameDataListener(ITCEffectAudioFrameDataListener).

```
public Builder enableProgressCallback(boolean enable)
```

**Parameter description**

Enable the playing animation progress callback switch.

```
public Builder progressCallbackIntervalMs(int intervalInMS)
```

**Parameter description**

Playing animation progress callback interval, in milliseconds, default value 200 ms.

> **Note:**Note that this configuration is effective only when the enableProgressCallback() switch is on.After turning on the switch, you can listen for the event TCEffectAnimView.IAnimPlayListener#onPlayEvent() to obtain the current playback progress. Use TCEffectPlayerConstant#EVT_PLAY_PROGRESS_MS and TCEffectPlayerConstant#EVT_PLAY_DURATION_MS to respectively obtain the current playback duration and total duration (in milliseconds) from the bundle.Set the interval to a reasonable value. Too small an interval may affect performance.

## TCEffectAnimInfo

**Description**

Store information of the current playback animation.

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| type | int | Current animation type, Parameter Value: TCEffectAnimInfo.TYPE_MP4 and TCEffectAnimInfo.TYPE_TCMP4. |
| duration | long | Animation duration, milliseconds. |
| width | int | Animation width. |
| height | int | Animation height. |
| encryptLevel | int | The advanced encryption type of the current animation. If the value is TCEffectAnimInfo#ENCRYPT_LEVEL_NONE, it means there is no advanced encryption; otherwise, it indicates that it has been advanced encrypted. |
| mixInfo | MixInfo | Fusion animation info. It means that the animation has no fusion info when it is null. |

## TCEffectAnimInfo.MixInfo

**Description**

Store the fusion information in the current playback animation.

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| textMixItemList | List<MixItem> | Text fusion info. It means that there is no text fusion info when it is null. |
| imageMixItemList | List<MixItem> | Image fusion info. It means that there is no image fusion info when it is null. |

## TCEffectAnimInfo.MixInfo.MixItem

**Description**

Store the fusion information in the current playback animation.

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| id | String | Current fusion animation id. If it is tcmp4, it is the corresponding layer index to be replaced; if it is mp4, it is the id value displayed in the tool. |
| tag | String | Current fusion animation tag. If it is tcmp4, it is a fixed value: TCEffectPlayerConstant.TAG_TPEG; if it is mp4, it is the tag value filled in the tool. |
| text | String | Current text content of text fusion animation (this value is empty for image fusion animation). If it is tcmp4, it is the original text content inside; if it is mp4, it is the tag value filled in the tool. |

## TCEffectText

**Description**

Fusion animation text replacement style data class.

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| text | String | The text content to be displayed will eventually be replaced. |
| color | int | Text color, format requirement: ARGB, for example, 0xFFFFFFFF. |
| fontStyle | String | Text display style, valid value: "bold" indicates bold text, default size if not specified. |
| alignment | int | TEXT ALIGNMENT mode, valid values: TEXT_ALIGNMENT_NONE (default value, that is, keep the default ALIGNMENT mode of the sdk), TCEffectText.TEXT_ALIGNMENT_LEFT (LEFT-aligned), TCEffectText.TEXT_ALIGNMENT_CENTER (centered), TCEffectText.TEXT_ALIGNMENT_RIGHT (RIGHT-aligned). |
| fontSize | float | Text size, unit: px; if the text size is set (value greater than 0), the internal Auto Scaling policy will be invalidated, and the set text size will be forcibly used as the standard, which may result in the problem of oversized text not being fully displayed. |

## TCEffectAudioFrameData

**Description**

audio track callback audio data class

**Attribute Description**

| Attribute Name | Type | Description |
| --- | --- | --- |
| data | byte[][] | Audio sample dataWhen the data is non-planar, data[0] stores data; when the data is planar, data[0] to data[channels-1] store each sound channel. |
| size | int[] | Audio sample data sizeWhen the data is non-planar, size[0] stores the length; when the data is planar, size[0] to size[channels-1] store each sound track size. |
| format | int | Audio format |
| channelLayout | long | channel layout of audio |
| sampleRate | int | sampling rate of audio |
| channels | int | number of sound channels |
| nbSamples | int | Sampling number of each sound channel |
| ptsMs | long | PTS of the current sample |


---
*Source: [https://trtc.io/document/70533](https://trtc.io/document/70533)*
