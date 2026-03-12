# Integrating With UGSV SDK

## Step 1. Replace resources

1. Download the [UGSV demo](https://liteav.sdk.qcloud.com/download/latest/XiaoShiPin_UGC_Android_latest.zip) which has integrated the BeautyAR SDK S1 - 04.
2. Replace the SDK files in the demo with the files for the SDK you actually use. Specifically, follow the steps below:
  2.1. In the `build.gradle` file of the `xmagickit` module, find the following:

```
api 'com.tencent.mediacloud:TencentEffect_S1-04:latest.release'
```

Replace it with the SDK edition you purchased as described in [Integrating BeautyAR SDK](https://www.tencentcloud.com/document/product/1143/60195#.E9.9B.86.E6.88.90.E5.87.86.E5.A4.87).

  2.2. If your SDK edition includes animated effects and filters, you need to [download](https://trtc.io/sdkDownload?id=beauty) the corresponding SDK package and add the resources for animated effects and filters to the following directories of `xmagickit`:
    - Animated effects: `../assets/MotionRes`.
    - Filters: `../assets/lut`.
3. Import `xmagickit` in the demo project into your own project.

## Step 2. Modify the package name

Open `build.gradle` in `app` and set `applicationId` to the package name bound to your trial license.

## Step 3. Integrate the SDK APIs

You can refer to the `UGCKitVideoRecord` class of the demo.

1. **Set the license:**

```
 // For details about authentication and the error codes, see https://intl.cloud.tencent.com/document/product/1143/45385#.E6.AD.A5.E9.AA.A4.E4.B8.80.EF.BC.9A.E9.89.B4.E6.9D.83 XMagicImpl.checkAuth(new TELicenseCheck.TELicenseCheckListener() {         @Override         public void onLicenseCheckFinish(int errorCode, String msg) {             if (errorCode == TELicenseCheck.ERROR_OK) {                 loadXmagicRes();             } else {                 Log.e("TAG", "auth fail ï¼please check auth url and key" + errorCode + " " + msg);             }         }     });
```

2. **Initialize the resources:**

```
 private void loadXmagicRes() {     if (XMagicImpl.isLoadedRes) {         XmagicResParser.parseRes(mActivity.getApplicationContext());         initXMagic();         return;     }     new Thread(new Runnable() {         @Override         public void run() {             XmagicResParser.copyRes(mActivity.getApplicationContext());             XmagicResParser.parseRes(mActivity.getApplicationContext());             XMagicImpl.isLoadedRes = true;             new Handler(Looper.getMainLooper()).post(new Runnable() {                 @Override                 public void run() {                     initXMagic();                 }             });         }     }).start(); }
```

3. **Bind UGSV and Tencent Effect:**

```
 private void initBeauty() {     TXUGCRecord instance = TXUGCRecord.getInstance(UGCKit.getAppContext());     instance.setVideoProcessListener(new TXUGCRecord.VideoCustomProcessListener() {         @Override         public int onTextureCustomProcess(int textureId, int width, int height) {             if (xmagicState == XMagicImpl.XmagicState.STARTED && mXMagic != null) {                 return mXMagic.process(textureId, width, height);             }             return textureId;         }         @Override         public void onDetectFacePoints(float[] floats) {         }         @Override         public void onTextureDestroyed() {             if (Looper.getMainLooper() != Looper.myLooper()) {  // Not the main thread                 boolean stopped = xmagicState == XMagicImpl.XmagicState.STOPPED;                 if (stopped || xmagicState == XMagicImpl.XmagicState.DESTROYED) {                     if (mXMagic != null) {                         mXMagic.onDestroy();                     }                 }                 if (xmagicState == XMagicImpl.XmagicState.DESTROYED) {                     TXUGCRecord.getInstance(UGCKit.getAppContext()).setVideoProcessListener(null);                 }             }         }     }); }
```

4. **Pause/Terminate the SDK**:

`onPause()` is used to pause effects, which can be implemented in an Activity/Fragment lifecycle method. The `onDestroy` method needs to be called in an OpenGL thread (you can call `onDestroy()` of the `XMagicImpl` object in `onTextureDestroyed`). For more information, see `onTextureDestroyed` in the demo.

```
         @Override         public void onTextureDestroyed() {             if (Looper.getMainLooper() != Looper.myLooper()) {  // Not the main thread                 boolean stopped = xmagicState == XMagicImpl.XmagicState.STOPPED;                 if (stopped || xmagicState == XMagicImpl.XmagicState.DESTROYED) {                     if (mXMagic != null) {                         mXMagic.onDestroy();                     }                 }                 if (xmagicState == XMagicImpl.XmagicState.DESTROYED) {                     TXUGCRecord.getInstance(UGCKit.getAppContext()).setVideoProcessListener(null);                 }             }         }
```

5. **Add layout for the effect panel:**

```
 <RelativeLayout     android:id="@+id/panel_layout"     android:layout_width="match_parent"     android:layout_height="wrap_content"     android:layout_alignParentBottom="true"     android:visibility="gone"/>
```

6. **Create an effect object and add the effect panel:**

```
private void initXMagic() {    if (mXMagic == null) {        mXMagic = new XMagicImpl(mActivity, getBeautyPanel());    } else {        mXMagic.onResume();    }}
```

For detailed directions, see the `UGCKitVideoRecord` class of the demo.


---
*Source: [https://trtc.io/document/73769](https://trtc.io/document/73769)*
