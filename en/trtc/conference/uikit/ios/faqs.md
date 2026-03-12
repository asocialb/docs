# FAQs

### **I need to modify the UI myself. Every time I update the pod, the source code will be refreshed, causing the modifications to be lost. How should I handle this?**

It is suggested to Fork the [TUIRoomKit repository](https://github.com/tencentyun/TUIRoomKit/tree/main) to your personal GitHub account, and then use the [local pod](https://guides.cocoapods.org/using/the-podfile.html) or [git pod path](https://guides.cocoapods.org/using/the-podfile.html) to reference the corresponding code in your project.

For details, please refer to the [official Pod documentation](https://guides.cocoapods.org/using/the-podfile.html):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3b68eed135c311eeaa5e5254005c1bd1.png)

### Is there a conflict between TUIRoomKit and the integrated audio and video library?

Tencent Cloud's audio and video libraries cannot be integrated at the same time, and there may be symbol conflicts. You can handle it according to the following scenarios.

1. If you are using the `TXLiteAVSDK_TRTC` library, there will be no symbol conflicts. You can directly add dependencies in the Podfile file.

```
pod 'TUIRoomKit'
```

2. If you are using the `TXLiteAVSDK_Professional` library, there will be symbol conflicts. You can add dependencies in the `Podfile` file.

```
pod 'TUIRoomKit/Professional'
```

3. If you are using the `TXLiteAVSDK_Enterprise` library, there will be symbol conflicts. It is recommended to upgrade to `TXLiteAVSDK_Professional` and then use TUIRoomKit/Professional.

### How to view TRTC logs?

TRTC logs are compressed and encrypted by default, with the extension .xlog. Whether the log is encrypted can be controlled by setLogCompressEnabled. The file name containing C(compressed) is encrypted and compressed, and the file name containing R(raw) is plaintext.

- iOS&Macï¼Sandbox's `Documents/log`
- Androidï¼
  - Versions 6.7 and earlierï¼`/sdcard/log/tencent/liteav`
  - Versions after 6.8ï¼`/sdcard/Android/data/package name/files/log/tencent/liteav/`
  - Versions after 8.5ï¼`/sdcard/Android/data/package name/files/log/liteav/`
- Windowsï¼
  - Versions before 8.8ï¼`%appdata%/tencent/liteav/log`
  - Versions 8.8 and laterï¼`%appdata%/liteav/log`
- Webï¼Open the browser Console, or use vConsole to record SDK print information.

> **Note:**To view the .xlog file, you need to download the [decryption tool](https://dldir1.qq.com/hudongzhibo/log_tool/decode_mars_log_file.py) and run it directly in the Python 2.7 environment with the xlog file in the same directory using python decode_mars_log_file.py.To view the .clog file (new log format after version 9.6), you need to download the [decryption tool](http://dldir1.qq.com/hudongzhibo/log_tool/decompress_clog.py) and run it directly in the Python 2.7 environment with the clog file in the same directory using python decompress_clog.py.


---
*Source: [https://trtc.io/document/54895](https://trtc.io/document/54895)*
