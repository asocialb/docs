# Reducing SDK Size

## BeautyAR Model Dynamic Resource Download

To reduce package size, you can change the required model resource and dynamic effect resource MotionRes (some basic version SDKs do not have dynamic effect resource) to download online. After the download succeeds, set the file path to the SDK. See demo: [TEBeauty_Download_Example](https://github.com/Tencent-RTC/TencentEffect_iOS/tree/main/TEBeauty_Download_Example).

1. Upload the ZIP package of the beauty effect model resource to the cloud and generate a download URL, such as `https://server_address/LightCore.bundle.zip`.
2. Use the generated URL in the project to download the file and extract it to the sandbox (example: sandbox path `Document/Xmagic`). At this point, the Document/Xmagic folder contains the resources required by the SDK.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b57cba864c411ed83b6525400c56988.png)

3. During SDK initialization, input the sandbox path from the previous step in the root_path field.

```
 NSDictionary *assetsDict = @{@"core_name":@"LightCore.bundle",                           @"root_path":_filePath //_filePath is the parent directory after beauty resource is downloaded to local:xx/Ducument/Xmagic, }; // Init beauty kit                                 @"root_path":Ducument/Xmagic, self.beautyKit = [[XMagic alloc] initWithRenderSize:_inputSize assetsDict:assetsDict];
```

## Filter and Motion Effect Resource Download

- Each filter is an image in png format, and each motion effect is a folder. For filter and motion effect resources, it is recommended to download one item when the user clicks to use it. After the download succeeds, call the SDK's [setEffect](https://www.tencentcloud.com/document/product/1143/60202#setEffect) API and set the filter path or motion effect folder path to the SDK.
- Filters and motion effect resources can be saved in any directory on the mobile phone. We recommend that you save them in the app's private directory to prevent accidental deletion.


---
*Source: [https://trtc.io/document/60205](https://trtc.io/document/60205)*
