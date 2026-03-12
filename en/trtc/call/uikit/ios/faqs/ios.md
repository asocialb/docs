# iOS

### The error message "The package you purchased does not support this ability"?

If you encounter the above error message, it is because the audio and video call capability package of your current application has expired or has not been activated. You can refer to the [service activation guide](https://www.tencentcloud.com/document/product/647/59832#) to claim or activate the audio and video call capability, and then continue to use the TUICallKit component.

### How to modify TUICallKit source code?

To import the component using `CocoaPods`, follow these steps:

1. Create a **TUICallKit** folder in the same directory as your project's **Podfile**.
2. Click to enter [**Github/TUICallKit**](https://github.com/tencentyun/TUICalling) , select Clone/Download code, and then copy the [TUICallKit_Swift](https://github.com/Tencent-RTC/TUICallKit/tree/main/iOS/TUICallKit_Swift) folder and [TUICallKit_Swift.podspec](https://github.com/Tencent-RTC/TUICallKit/blob/main/iOS/TUICallKit_Swift.podspec) file in the [**iOS**](https://github.com/tencentyun/TUICalling/tree/main/iOS) directory to the **TUICallKit** folder you created in Step 1.
3. Add the following dependencies to your `Podfile`.

```
# :path => "Directed TUICallKit-Swift.podspec's phase path"pod 'TUICallKit_Swift', :path => "TUICallKit/TUICallKit_Swift.podspec"
```

4. Execute the **pod install** command to complete the import.

> **Note:**The `TUICallKit_Swift`folder and `TUICallKit_Swift.podspec` file must be in the same directory.

**After integrating the**`TUICallKit_Swift`**component, the effect is as follows:**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12e305f118d411ef91925254007bbd8c.png)

> **Noteï¼**After integrating the TUICallKit_Swift component, it supports hierarchical folder display, making it easier for you to read and modify the source code.

### Xcode 15 compiler error?

#### 1ã**Sandbox: rsync**is displayed.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12e2867d18d411efb6da5254002fd0a8.png)

You can set **User Script Sandboxing** to **NO** in **Build Settings:**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/131d94fe18d411efad1a52540019e87e.png)

#### 2ãIf **SDK does not contain**, compile error screenshot.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12efdccb18d411efb6da5254002fd0a8.png)

Add the following code to the Podfile:

```
# target 'xxxx' do#  ...#  pod 'TUICallKit_Swift'# endpost_install do |installer|  installer.pods_project.targets.each do |target|    target.build_configurations.each do |config|      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '13.0'    end  endend
```

#### 3ãIf you run the simulator on an M-series computer, **Linker command failed with exit code 1 (use-v to see invocation)**may appear.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12eca87218d411ef91925254007bbd8c.png)

Add the following code to the Podfile:

```
# target 'xxxx' do#  ...#  pod 'TUICallKit_Swift'# endpost_install do |installer|  installer.pods_project.targets.each do |target|    target.build_configurations.each do |config|      config.build_settings['EXCLUDED_ARCHS[sdk=iphonesimulator*]'] = "arm64"    end  endend
```

### Is there a conflict between TUICallKit and the integrated audio and video library?

Tencent Cloud's audio and video libraries cannot be integrated at the same time, and there may be symbol conflicts. You can handle it according to the following scenarios.

1. If you are using the `TXLiteAVSDK_TRTC` library, there will be no symbol conflicts. You can directly add dependencies in the Podfile file.

```
pod 'TUICallKit_Swift'
```

2. If you are using the `TXLiteAVSDK_Professional` library, there will be symbol conflicts. You can add dependencies in the `Podfile` file.

```
pod 'TUICallKit_Swift/Professional'
```

3. If you are using the `TXLiteAVSDK_Enterprise` library, there will be symbol conflicts. It is recommended to upgrade to `TXLiteAVSDK_Professional` and then use`TUICallKit_Swift/Professional`ã

### Does TUICallKit support background operation?

Yes, if you need to continue running related functions in the background, you can select the current project, and in the Background Modes section under Capabilities, check **Audio, AirPlay, and Picture in Picture**, as shown in the following image:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12e1121718d411efad1a52540019e87e.png)

### How to view TRTC logs?

TRTC logs are compressed and encrypted by default, with the extension .xlog. Whether the log is encrypted can be controlled by setLogCompressEnabled. The file name containing C(compressed) is encrypted and compressed, and the file name containing R(raw) is plaintext.

iOSï¼Sandbox's `Documents/log`

> **Note:**To view the .xlog file, you need to download the [decryption tool](https://dldir1.qq.com/hudongzhibo/log_tool/decode_mars_log_file.py) and run it directly in the Python 2.7 environment with the xlog file in the same directory using python decode_mars_log_file.py.To view the .clog file (new log format after version 9.6), you need to download the [decryption tool](http://dldir1.qq.com/hudongzhibo/log_tool/decompress_clog.py) and run it directly in the Python 2.7 environment with the clog file in the same directory using python decompress_clog.py.


---
*Source: [https://trtc.io/document/51023](https://trtc.io/document/51023)*
