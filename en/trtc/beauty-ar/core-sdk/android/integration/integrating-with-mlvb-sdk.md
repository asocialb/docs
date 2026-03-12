# Integrating With MLVB SDK

## SDK Integration

1. **Integration BeautyAR**
  - [Integrating BeautyAR SDK](https://www.tencentcloud.com/document/product/1143/60195)
  - [Integrating BeautyAR Resources](https://www.tencentcloud.com/document/product/1143/60195#d45c5308-0cf3-4ed7-99ad-4e6156981a89)
2. **Integration TEBeautyKit**
  - [Add TEBeautyKit dependencies](https://www.tencentcloud.com/document/product/1143/60196#9738dff7-5329-40f4-96df-9006105b28e7)
  - [Add panel JSON file](https://www.tencentcloud.com/document/product/1143/60196#bfa4a17f-c33c-4a93-8400-59ffba2472a7)ï¼optional if not using default panelï¼
3. **Integration**`te_adapter_live`

Maven Dependencies

AAR Dependencies

Add the dependency for `te_adapter_live` in dependencies.

```
dependencies{    ...    implementation 'com.tencent.mediacloud:te_adapter_live:Version number'}
```

1. [Download AAR](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/Android/te_beauty_adapter/latest/te_adapter_latest.zip) file (a zip file will be downloaded; extract it to get the AAR file).
2. Add the downloaded te_adapter_live_xxxx`.aar` file to the app project `libs` directory.
3. Open `build.gradle` in the app module and add a dependency reference:

```
dependencies{    ...    implementation fileTree(dir: 'libs', include: ['*.jar','*.aar'])   //add *.aar}
```

**Refer to**[MLVB Demo](https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/Android/latest/MLVB-API-Example_latest.zip)**project.**

> **Note:**To run the code, you need to add your applied License information in the file `com.tencent.thirdbeauty.xmagic.LicenseConstant.java`, and modify the `applicationId` in the` build.gradle `file under the App module to the package name you provided when applying for the License.Due to the dependency on MLVB capability, you need to find the file `com.tencent.mlvb.debug.GenerateTestUserSig.java` under the Debug module and add the corresponding `LICENSEURL, LICENSEURLKEY, SDKAPPID, and SECRETKEY`.For the main code integration of beauty effects, please refer to the file `com.tencent.mlvb.thirdbeauty.ThirdBeautyActivity.java`.

## SDK Usage Steps

### Step 1: Set Panel's JSON File

Please append the path of the JSON file added to your project in the second step of the 'How to Integrate' section in the [TEBeautyKit Integration Document](https://www.tencentcloud.com/document/product/1143/60196#bfa4a17f-c33c-4a93-8400-59ffba2472a7). If there is no JSON file, then the path Setting should be null.

> **Note:****If you do not use the provided beauty panel, please ignore this step.**

```
    TEPanelViewResModel resModel = new TEPanelViewResModel();    String combo = "S1_07";   //Set according to your package. If your package does not include a certain feature, the customer is set to null.    resModel.beauty = "beauty_panel/"+combo+"/beauty.json";    resModel.lut = "beauty_panel/"+combo+"/lut.json";    resModel.beautyBody = "beauty_panel/"+combo+"/beauty_body.json";    resModel.motion = "beauty_panel/"+combo+"/motions.json";    resModel.lightMakeup = "beauty_panel/"+combo+"/light_makeup.json";    resModel.segmentation = "beauty_panel/"+combo+"/segmentation.json";    TEUIConfig.getInstance().setTEPanelViewRes(resModel);
```

### Step 2: Authenticate and copy resource

> **Noteï¼**Resource copying is based on the SDK version number, so resources will only be successfully copied once for the same SDK version number.

```
TEBeautyKit.setupSDK(this.getApplicationContext(),LicenseConstant.mXMagicLicenceUrl,LicenseConstant.mXMagicKey, (i, s) -> {    if (i == LicenseConstant.AUTH_STATE_SUCCEED) {        runOnUiThread(() -> {            Intent intent = new Intent(MainActivity.this, ThirdBeautyActivity.class);            startActivity(intent);       }    } else {        Log.e(TAG, "te license check is failed,please checke  ");    }});
```

### Step 3: Initialize the adapter and the panel

> **Note:**If you do not want to use the provided panel, you can skip creating `TEPanelView` and configure the beauty attributes yourself by calling `TEBeautyKit`'s `setEffect` to set beauty attributes.

```
this.beautyLiveAdapter = new TEBeautyLiveAdapter(XmagicConstant.EffectMode.PRO, TEBeautyKit.getResPath());// Set the phone orientationthis.beautyLiveAdapter.notifyScreenOrientationChanged(ActivityInfo.SCREEN_ORIENTATION_PORTRAIT);// Set the camera to front-facing or rear-facing, and whether to use encoding mirrorthis.beautyLiveAdapter.notifyCameraChanged(isFront, this.isEncoderMirror);private void initBeautyPanelView() {    RelativeLayout panelLayout = findViewById(R.id.live_pusher_bp_beauty_panel);    this.tePanelView = new TEPanelView(this);    if (lastParamList != null) {  // Used to restore the last beauty effects        this.tePanelView.setLastParamList(lastParamList);    }  this.tePanelView.showView(this);    panelLayout.addView(this.tePanelView);}
```

### Step 4. Create Beauty

After V3.9.0

V3.9.0 and earlier

```
this.beautyLiveAdapter.bind(this, mLivePusher, new ITEBeautyAdapter.CallBack() {    @Override    public void onCreatedTEBeautyApi(XmagicApi xmagicApi) {        mBeautyKit = new TEBeautyKit(xmagicApi);        tePanelView.setupWithTEBeautyKit(mBeautyKit);        setTipListener(mBeautyKit);        setLastParam(mBeautyKit);        Log.e("beautyLiveAdapter", "onCreatedTEBeautyKit");    }    @Override    public void onDestroyTEBeautyApi() {        mBeautyKit = null;        Log.e("beautyLiveAdapter", "onDestroyTEBeautyKit");    }});
```

```
this.beautyLiveAdapter.bind(this, mLivePusher, new ITEBeautyAdapter.CallBack() {    @Override    public void onCreatedTEBeautyKit(TEBeautyKit beautyKit) {        mBeautyKit = beautyKit;        tePanelView.setupWithTEBeautyKit(mBeautyKit);        setTipListener(mBeautyKit);        setLastParam(mBeautyKit);        Log.e("beautyLiveAdapter", "onCreatedTEBeautyKit");    }    @Override    public void onDestroyTEBeautyKit() {        mBeautyKit = null;        Log.e("beautyLiveAdapter", "onDestroyTEBeautyKit");    }});
```

### Step 5. Notify adapter while Parameter Changed

```
//Notify adapter of the latest status when the camera or screen mirror changes this.beautyLiveAdapter.notifyCameraChanged(isFront, this.isEncoderMirror);//When the screen orientation changes, you need to call the notifyScreenOrientationChange method this.beautyLiveAdapter.notifyScreenOrientationChanged(orientation);
```

### Step 6: Destroy Effect

```
 //You can call the unbind method to unbind when the beauty filter is no longer needed  this.beautyLiveAdapter.unbind();
```

### Step 7: Resume Audio

```
/** * Used to restore sound in stickers * Restore gyroscope sensor, usually called in the onResume method of Activity */this.mBeautyKit.onResume()
```

### Step 8: Pause Audio

```
/** * Used to pause sound in stickers * Pause gyroscope sensor, usually called in the onPause method of Activity */this.mBeautyKit.onPause()
```


---
*Source: [https://trtc.io/document/73767](https://trtc.io/document/73767)*
