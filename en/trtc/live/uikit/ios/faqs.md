# FAQs

### Xcode 15 compiler error?

1. **Sandbox: rsync** is displayed.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/11f98d2f0f6111efb8f85254005a7266.png)

You can set User Script Sandboxing to **NO** in **Build Settings:**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1142dcdb0f6111ef98aa525400493f3c.png)

2. If **SDK does not contain**, compile error screenshot:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/11abe9e10f6111efbab15254000ded98.png)

Add the following code to the Podfile:

```
post_install do |installer|  installer.pods_project.targets.each do |target|    target.build_configurations.each do |config|      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '13.0'    end  endend
```

3. If you run the emulator on an M-series computer, **Linker command failed with exit code 1 (use-v to see invocation)** may appear.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1187403c0f6111ef9f885254000781d8.png)

The xcode configuration needs to be modified. xcode open projects > **Product > Destination > Destination Architectures** can choose which mode of emulator to open with, and need to select the ending emulator (**Rosetta**).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/114df26e0f6111efbab15254000ded98.png)

### Is there a conflict between TUILiveKit and the integrated audio and video library?

Tencent Cloud's audio and video libraries cannot be integrated at the same time, and there may be symbol conflicts. You can handle it according to the following scenarios.

1. If you are using the `TXLiteAVSDK_TRTC` library, there will be no symbol conflicts. You can directly add dependencies in the Podfile file.

```
pod 'TUILiveKit'
```

2. If you are using the `TXLiteAVSDK_Professional` library, there will be symbol conflicts. You can add dependencies in the `Podfile` file.

```
pod 'TUILiveKit/Professional'
```

If you are using the `TXLiteAVSDK_Enterprise` library, there will be symbol conflicts. It is recommended to upgrade to `TXLiteAVSDK_Professional` and then use TUILiveKit/Professional.

### How to view TRTC logs?

TRTC logs are compressed and encrypted by default, with the extension .xlog. Whether the log is encrypted can be controlled by setLogCompressEnabled. The file name containing C(compressed) is encrypted and compressed, and the file name containing R(raw) is plaintext.

iOSï¼Sandbox's `Documents/log`ã

> **Note:**To view the .xlog file, you need to download the [decryption tool](https://dldir1.qq.com/hudongzhibo/log_tool/decode_mars_log_file.py) and run it directly in the Python 2.7 environment with the xlog file in the same directory using python decode_mars_log_file.py.To view the .clog file (new log format after version 9.6), you need to download the [decryption tool](http://dldir1.qq.com/hudongzhibo/log_tool/decompress_clog.py) and run it directly in the Python 2.7 environment with the clog file in the same directory using python decompress_clog.py.


---
*Source: [https://trtc.io/document/60048](https://trtc.io/document/60048)*
