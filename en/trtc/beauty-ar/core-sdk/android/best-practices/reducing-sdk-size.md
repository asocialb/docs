# Reducing SDK Size

To reduce package size, you can change the required so libraries and model resources to download online, only need to download these files before SDK initialization. For filters and dynamic effect resources, it is advisable to download one when in use upon user click.

## Demo Project: TEBeauty_Download_Example

Clone the [demo project](https://github.com/Tencent-RTC/TencentEffect_Android) from GitHub, configure and run TEBeauty_Download_Example according to TEBeauty_Download_Example/readme document to learn about the overall process of dynamic Download.

## Downloading SO Libraries and Model Resources

If You Reuse the Download Code in Demo

If You Do the Download Yourself

1. Copy the code under the directory `com.tencent.demo.download` of the demo project to your project.
2. [Download SDK](https://trtc.io/document/45377), decompress it, then find the `.zip` format compression package in the "SDK" directory, decompress it again, and you will see the following files:

![20240516-205143@2x](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f3a13e513fc11efaa1c525400f65c2a.png)

3. Upload download_assets.zip, arm64-v8a.zip, and armeabi-v7a.zip to your server to get the download links. Calculate the MD5 of these 3 zip files. Fill the download links and MD5 values into the corresponding constants in `ResDownloadConfig.java`.
4. Refer to the code in `TEMenuActivity.java`, use `ResDownloadUtil.getValidLibsDirectory` to check whether the so library has been downloaded. If not, call `ResDownloadUtil.checkOrDownloadFiles` to start download. After download success, get the so library path sdkLibraryDirectory, then call `XmagicApi.setLibPathAndLoad(sdkLibraryDirectory)` to load the so library.

```
String validLibsDirectory = ResDownloadUtil.getValidLibsDirectory(this, libraryMD5);if (validLibsDirectory == null) {    ResDownloadUtil.checkOrDownloadFiles(this, ResDownloadUtil.FILE_TYPE_LIBS, libraryURL, libraryMD5,        new TEDownloadListener() {            @Override            public void onDownloadSuccess(String directory) {              sdkLibraryDirectory = directory;            }            @Override            public void onDownloading(int progress) {            }            @Override            public void onDownloadFailed(int errorCode) {            }        });} else {    sdkLibraryDirectory = validLibsDirectory;}
```

5. Refer to the code in `TEMenuActivity.java`, use `ResDownloadUtil.getValidAssetsDirectory` to check whether the model resources have been downloaded. If not, call `ResDownloadUtil.checkOrDownloadFiles` to start download. The module will download, organize and copy these resources to the `AppConfig.resPathForSDK` directory, then transmit them to the SDK when new XmagicApi is created.

```
String validAssetsDirectory = ResDownloadUtil.getValidAssetsDirectory(this, ResDownloadConfig.DOWNLOAD_MD5_ASSETS);if (TextUtils.isEmpty(validAssetsDirectory)) {    ResDownloadUtil.checkOrDownloadFiles(this, ResDownloadUtil.FILE_TYPE_ASSETS,            ResDownloadConfig.DOWNLOAD_URL_ASSETS,            ResDownloadConfig.DOWNLOAD_MD5_ASSETS, new TEDownloadListener() {                @Override                public void onDownloadSuccess(String directory) {                }                @Override                public void onDownloading(int progress) {                }                @Override                public void onDownloadFailed(int errorCode) {                }            });} else {    }
```

6. In the Demo, checkpoint restart is enabled by default (the `ENABLE_RESUME_FROM_BREAKPOINT` property in `ResDownloadUtil.java` is set to `true`), ensuring that downloads can RESUME FROM the BREAKPOINT if interrupted due to exceptions next time. If you want to ENABLE checkpoint restart, please ensure your download service supports BREAKPOINT resumption. Detection method:

```
To check whether the server supports breakpoint resumption, just verify if the Web server supports Range request. The test method is to run the curl command in the command line:curl -i --range 0-9 https://your_server_address/downloaded_fileExample:curl -i --range 0-9 https://mediacloud-76607.gzc.vod.tencent-cloud.com/TencentEffect/Android/2.4.1.119/xmagic_S1-04_android_2.4.1.119.zipIf the returned content has the Content-Range field, it indicates the server supports breakpoint resumption.
```

1. [Download SDK](https://trtc.io/document/45377), decompress it, then find the .zip format compression package in the "SDK" directory, decompress it again, and you will see the following files. The model files in assets and the so files in jniLibs can be dynamically downloaded. The aar in libs is required to be built into the package.

![20240516-205143@2x](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d74236e0141611ef83b95254002977b6.png)

2. Download the so file and unzip it, then call `XmagicApi.setLibPathAndLoad(/path/to/so/files)` to load the so library.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/123d40d0665811ed87ca525400463ef7.png)

> **Note:**It is highly recommended to download the so file to the App's private directory rather than external storage to prevent accidental deletion by clearing tools. Meanwhile, you can download the v8a or v7a so file based on the user mobile phone CPU type for on-demand download to speed up downloads. See the Demo project TEMenuActivity for reference.

3. For the files in the download_assets.zip package, after download completion, decompress it, then call the following code to let the SDK copy the files to the correct directory (the directory pointed to by `AppConfig.resPathForSDK`). The `downloadedDirectory` in the code is the directory where your decompressed files are located.

`addAiModeFiles` returns error code -2, which means the file copy failed during the process. This might be due to insufficient space on the mobile phone or an IO exception. You can try copying again or re-downloading.

```
  private static boolean organizeAssetsDirectory(String downloadedDirectory) {    for (String path : XmagicResourceUtil.AI_MODE_DIR_NAMES) {        if (XmagicApi.addAiModeFiles(downloadedDirectory + File.separator + path, AppConfig.resPathForSDK) == -2) {            return false;        }    }    return true;}
```

> **Note:**When the SDK version is updated, the corresponding .so files and assets may undergo changes. To ensure compatibility, you need to redownload these files. It is recommended to follow the approach demonstrated in the Demo by utilizing MD5 checksum verification.Since the Tencent Effect SDK **also relies on the libpag and gson libraries**, while the current dynamic download functionality is designed solely for the Tencent Effect SDK itself, you are required to manually add dependencies for **libpag and gson** in your projectï¼For specific version numbers, please refer to the [documentation](https://www.tencentcloud.com/document/product/1143/60195#sdkversion).

## Filter and Animation Resource Download

- Each filter is an image in png format, and each animation is a folder. For filter and animation resources, it is recommended to download one item when the user clicks to use it. After download success, call the SDK's [XmagicApi.setEffect](https://www.tencentcloud.com/document/product/1143/60207) API and set the filter path or animation folder path to the SDK.
- Filters and animation resources can be saved in any directory on the mobile phone. We recommend that you save them in the app's private directory to prevent accidental deletion.


---
*Source: [https://trtc.io/document/60206](https://trtc.io/document/60206)*
