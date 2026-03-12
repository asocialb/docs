# Usage Guide

This article will introduce in detail how to quickly use Tencent Gift AR SDK in the project. Just follow the following steps to complete the configuration and use of the SDK.

## Initializing Registration License

When using Gift AR SDK officially, you need to configure the License first. After successfully configuring the License, you can subsequently use the SDK.

The method for configuring the License is as follows:

```
private static final String sLicenseUrl = "${licenseUrl}";private static final String sLicenseKey = "${licenseKey}";private final ILicenseCallback mLicenseCallback = new ILicenseCallback() {    @Override    public void onResult(int errCode, String msg) {        // Note: This callback may not be on the calling thread        Log.d(TAG, "TCMediaX license result: errCode: " + errCode + ", msg: " + msg);        if (errorCode == TXLicenceErrorCode.LicenseCheckOk) {               // Authentication successful           } else {               // Authentication failure         }    }};// Call the current method to perform license configurationpublic void init() {    TCMediaXBase.getInstance().setLicense(DemoApplication.getAppContext(), sLicenseUrl, sLicenseKey, mLicenseCallback);}
```

> **Note:**The License has strong online verification logic. When calling TCMediaXBase#setLicense after the application starts for the first time, ensure that the network is available. When the App starts for the first time, network permission may not be authorized yet. You need to wait until permission is granted and then call TCMediaXBase#setLicense again.Listen to the loading result of TCMediaXBase#setLicence: ILicenseCallback#onResult API. If it fails, retry and guide according to the actual situation. If there are multiple failures, limit the frequency and supplement with product pop-ups and other guides to allow users to check network conditions.For multi-process Apps, ensure that TCMediaXBase#setLicense is called when each process using the effect player starts. For example: For Apps that use a separate process to play effects on the Android side, TCMediaXBase#setLicense should also be called when the process is killed and restarted by the system during background playback.

**Authentication error code description:**

| Error Code | Description |
| --- | --- |
| 0 | Success. |
| -1 | The input parameter is invalid. For example, the URL or KEY is empty. |
| -3 | The download process failed. Check the network settings. |
| -4 | The TE authorization information read from local is empty, which might be caused by I/O failure. |
| -5 | The file content of the VCUBE TEMP License is empty, which might be caused by an I/O failure. |
| -6 | The JSON field of the v_cube.license file is incorrect. Contact the Tencent Cloud team to handle it. |
| -7 | Signature verification failed. Contact the Tencent Cloud team to handle it. |
| -8 | Decryption failed. Contact the Tencent Cloud team to handle it. |
| -9 | The JSON field in the TELicense field is incorrect. Contact the Tencent Cloud team to handle it. |
| -10 | The TE authorization information from network resolution is empty. Contact the Tencent Cloud team to handle it. |
| -11 | Failed to write TE authorization information to a local file, which might be caused by an I/O failure. |
| -12 | Download failed. Parsing the local asset also failed. |
| -13 | Authentication failure. Please check if the so file is in the package, or if the so path has been correctly set. |
| 3004/3005 | Invalid authorization. Contact the Tencent Cloud team to handle it. |
| 3015 | The Bundle Id / Package Name does not match. Check whether the Bundle Id / Package Name used by your App is consistent with the applied one, and check whether the correct license file is used. |
| 3018 | The license file has expired. You need to apply for renewal from Tencent Cloud. |
| Other | Contact the Tencent Cloud team to handle it. |

## Log Management

Gift AR SDK supports saving running logs by default. If problems occur during the test, you can extract the logs and give feedback to Tencent Cloud customer service. According to business needs, you can upload the logs in this directory to the backend to locate online user problems.

The log of Gift AR SDK Android version is saved in the directory: `/sdcard/Android/data/${your_packagename}/files/TCMediaLog`. The log files are named by date. Export the TCMediaLog folder.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2f0d4bf9095a11f0990f52540099c741.png)

> **Note:****Missing logs file?**Check whether false has been passed in through TCMediaXBase#setLogEnable to disable the log. The default file log is enabled.

## Player Usage

### Add TCEffectAnimView to the Layout

```
<FrameLayout    android:layout_width="match_parent"    android:layout_height="match_parent"    android:layout_marginTop="0dp">    <com.tencent.tcmediax.tceffectplayer.api.TCEffectAnimView        android:id="@+id/video_view"        android:layout_width="match_parent"        android:layout_height="match_parent"        android:layout_centerInParent="true"        android:visibility="visible" /></FrameLayout>
```

### Initializing TCEffectAnimView

```
private TCEffectAnimView mPlayerView;mPlayerView = (TCEffectAnimView) findViewById(R.id.video_view);// Optional: Set the alignment mode of the animation (default FIT_CENTER, customizable)mPlayerView.setScaleType(TCEffectPlayerConstant.ScaleType.FIT_CENTER);
```

### Playback and Listen

You can call the `setPlayListener` method before starting playback to set the animation playback status listener:

```
// Set the playback state callbackplayerView.setPlayListener(new TCEffectAnimView.IAnimPlayListener() {    @Override    public void onPlayStart() {        // Start animation playback    }    @Override    public void onPlayEnd() {        // Stop animation playback    }    @Override    public void onPlayError(int errorCode) {        // Animation playback failure    }        @Override    public void onPlayEvent(int event, Bundle param) {        // Animation playback event    }});
```

1. If you need to obtain the information of the currently playing animation, you can call the `getTCAnimInfo()` method in the `onPlayStart()` method (or after the execution of this method) to obtain a `TCEffectAnimInfo` object instance, and then obtain the type, duration, width and height, fusion animation, etc. of the currently playing animation.
2. The onPlayEvent() method will callback events during Animation playback. The callback thread does not guarantee to be in the main thread.

### Playback Configuration

```
// Set the playback configuration, optional stepsTCEffectConfig config = new TCEffectConfig.Builder().setCodecType(TCEffectConfig.CodecType.TC_MPLAYER).build();mPlayerView.setConfig(config);
```

TCEffectConfig currently supports:

1. setCodecType(CodecType type): It has three parameter values, which are:
  - TCEffectConfig.CodecType.TC_MPLAYER (MPLAYER playback engine)
  - TCEffectConfig.CodecType.TC_MCODEC (MCODEC playback engine)
  - TCEffectConfig.CodecType.TX_LITEAV_SDK (Tencent Cloud Player SDK)

> **Note:**Currently, you can only call the setConfig() method before the player starts to set the playback configuration. Configuration modification is not supported after playback starts.The three currently supported CodecTypes are only applicable to TEP animations.If you set CodecType to TCEffectConfig.CodecType.TX_LITEAV_SDK, you also need to separately introduce Tencent Cloud Player SDK, as well as apply for and register its corresponding license. If config is not set, CodecType = TCEffectConfig.CodecType.TC_MPLAYER will be used by default.

2. setFreezeFrame(int frame): Used to set the freeze frame for playing animations. For a detailed explanation, see [API document](https://www.tencentcloud.com/document/product/1143/70533#a5a2aac9-4cbe-4528-9b63-17a44fb49eed).
3. setAnimType(AnimType type): Used to specify the animation format to be played subsequently, suitable for scenarios where the file suffix of the animation to be played has been modified in some cases. Values are as follows:
  - TCEffectConfig.AnimType.AUTO (The default sdk policy, that is, determining the animation format by the suffix of the animation file, such as tcmp4/mp4/tep/tepg formats).
  - TCEffectConfig.AnimType.MP4 (MP4 animation format. Subsequently, all animation files will be played as MP4 type, ignoring the file extension).
  - TCEffectConfig.AnimType.TCMP4 (TCMP4 animation format. Subsequently, all animation files will be played as TCMP4 type, ignoring the file extension).
4. enableAudioFrameCallback(boolean enableAudioFrameCallback): Enable audio callback during playback, suitable for scenarios where event listening processing of gift animation audio tracks is required.

> **Note:**Currently only support calling the setConfig() method to set playback configuration before the player starts. Configuration modification is not supported after playback starts.This parameter is valid only when CodecType is TCEffectConfig.CodecType.TX_LITEAV_SDK and the animation kind is MP4/TEP.After turning on the switch, you can set up callback listening through the TCEffectAnimView#setAudioFrameDataListener(ITCEffectAudioFrameDataListener) method. For details, see: [API document](https://www.tencentcloud.com/document/product/1143/70533#a5a2aac9-4cbe-4528-9b63-17a44fb49eed).

5. enableProgressCallback(boolean enable): Enable progress callback during animation playback.
6. progressCallbackIntervalMs(int intervalInMS): Progress callback interval during animation playback, in milliseconds. Default value: 200 ms.

> **Note:**Note that this configuration is effective only when enableProgressCallback() is switched on.After turning on the switch, you can listen for the event TCEffectPlayerConstant.EVT_PLAY_PROGRESS in the TCEffectAnimView.IAnimPlayListener#onPlayEvent() callback to obtain the current playback progress. For details, see [API document](https://www.tencentcloud.com/document/product/1143/70533#a5a2aac9-4cbe-4528-9b63-17a44fb49eed).Note: Do not set the sampling interval too low. A small interval may affect performance.

### Fusion Animation Configuration

Implement the playback of mp4 or tcmp4 fusion animations. The IFetchResource API needs to be implemented.

1. If it is a fusion animation of the picture type, need to return the corresponding Bitmap to replace the corresponding element;
2. If it is a fusion animation of the text type, need to return the corresponding TCEffectText object instance to specify the text display configuration message.

```
mPlayerView.setFetchResource(new IFetchResource() {    @Override    public void fetchImage(Resource resource, IFetchResourceImgResult result) {        // If the replaced is a tepg file resource, isTEPG() = true.        boolean isTEPG = resource.isTEPG();        // If the original file is a pag file, the id here is the index corresponding to the image layer in the original pag file, such as 0, 1, 2...        String index = resource.id;        // Subsequently, you can select the Bitmap resource to be returned for replacement based on the value of the layer index.        // If you want to skip replacing the specified layer, you can return null        BitmapFactory.Options options = new BitmapFactory.Options();        options.inScaled = false;        Bitmap bitmap = BitmapFactory.decodeResource(getResources(), R.drawable.test, options);        // Callback result out        result.fetch(bitmap);    }    @Override    public void fetchText(Resource resource, IFetchResourceTxtResult result) {        // If the replaced is a tepg file resource, isTEPG() = true.        boolean isTEPG = resource.isTEPG();        // If the original file is a pag file, the id here is the index corresponding to the text layer in the original pag file, such as 0, 1, 2...        String index = resource.id;        // Select the String you want to replace and return according to the value of the layer index.        TCEffectText tcEffectText = new TCEffectText();        tcEffectText.text = "test";//      tcEffectText.color = Color.YELLOW;//      tcEffectText.alignment = TCEffectText.TEXT_ALIGNMENT_RIGHT;        tcEffectText.fontStyle = "bold";        result.loadTextForPlayer(tcEffectText);    }    @Override    public void releaseResource(List<Resource> resources) {        // Resource release notification        for (Resource resource : resources) {            if (resource.bitmap != null) resource.bitmap.recycle();        }    }});
```

If necessary, listen to the click event of the custom resource of the fusion animation and need to register OnResourceClickListener :

```
mPlayerView.setOnResourceClickListener(new OnResourceClickListener() {    @Override    public void onClick(Resource resource) {        // Process the display according to the clicked resource type        if (resource.srcType.equals(Resource.SrcType.TXT)) {            // If it is TXT type, the id field is its layer id and the text is its replaced text.            tvTest.setText(resource.text);        } else {            // If it is IMG type, the id field is its layer id and the bitmap is its replaced image.            ivTest.setImageBitmap(resource.bitmap);        }    }});
```

#### Animation Property Retrieval

To obtain the width, height, duration, and fusion animation property information before animation playback, you can use the following solution:

```
TCEffectAnimInfo animInfo = TCEffectAnimView.preloadTCAnimInfo(playPath, config);
```

- playPath: The path address of the animation to obtain information, similar to the passed parameters when calling the TCEffectAnimView#startPlay() method.
- config: A TCEffectConfig instance used to specify additional configuration for the animation.

> **Note:**When playing an animation, if you have called the TCEffectAnimView#setConfig() method and set up a TCEffectConfig instance containing extendMapParams(), then at this point when calling the current preloadTCAnimInfo method, pass this TCEffectConfig instance as the second input parameter to ensure normal resolution of the animation, otherwise just pass null.For earlier versions of vap animations that exclude vapc box, the current method cannot parse out the animation configuration message and will return null.The current method involves IO operations and is not recommended to be called in the main thread.

### Playback Control

#### Start Playing

TCEffectPlayer supports playback of .mp4, .tcmp4 file format resources.

> **Note:**Supports only playing local video resources on sdcard. If you use online video resources, download to local first and then play.Animation resources can be generated through [Gift AR Conversion Tool](https://www.tencentcloud.com/document/product/1143/70541). Besides, VAP format animation resources can also be played.

```
String localPath = /sdcard/Android/${packageName}/files/tep_cool_ss.tepmPlayerView.startPlay(localPath)
```

#### Pause Playing

```
mPlayerView.pause()
```

#### Continue Playing

```
mPlayerView.resume()
```

#### Loop Playback

```
mPlayerView.setLoop(true)
```

#### Mute Playback

```
mPlayerView.setMute(true)
```

#### Stop Playback

When the player is no longer needed, playback needs to be stopped and occupied resources need to be released.

```
mPlayerView.stopPlay(true)
```

## Common Issues

### What Should Be Done If the Following Log Information Appears during the Playback Process?

```
License checked failed! tceffect player license required!
```

Please check whether you have applied for the effect player License and completed the initialization registration.

### How to Extract Log Files?

- Method 1: The log of the effect player is saved in the directory: /sdcard/Android/data/${your_packagename}/files/TCMediaLog. The log files are named by date. Export the TCMediaLog folder and compress it into a zip file.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9527363c517011f095fc5254001c06ec.png)

- Method Two: If there is a development environment, you can run the following command through adb to capture full logs:

`adb logcat -v time > log.txt`

## Common Error Codes

| Error Code | Description |
| --- | --- |
| -10003 | Failed to create a thread. |
| -10004 | Failed to create a render. |
| -10005 | Configuration parsing failure |
| -10006 | Unable to read the file. |
| -10007 | The animation video coding format is H.265, which is not supported on the current device. |
| -10008 | Invalid parameter |
| -10009 | Invalid license |
| -10010 | MediaPlayer playback failure |
| -10012 | Lack essential dependencies. For example, when the playback type is TX_LITEAV_SDK, liteavSDK is not introduced. |


---
*Source: [https://trtc.io/document/70532](https://trtc.io/document/70532)*
