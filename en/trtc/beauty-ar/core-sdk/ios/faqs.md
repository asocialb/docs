# FAQs

### When I tried to run my iOS project in Xcode 12.x after importing the resources, the error âBuilding for iOS Simulator, but the linked and embedded framework '.framework'...â occurred. What should I do?

> **Note:**If you change **Validate Workspace** back to **No** after compilation, you can still run your project successfully.

### What should I do if the filter settings don't take effect?

### What should I do if a `dSYM` generation error occurs when I compile the iOS demo project?

```
PhaseScriptExecution CMake\\ PostBuild\\ Rules build/XMagicDemo.build/Debug-iphoneos/XMagicDemo.build/Script-81731F743E244CF2B089C1BF.sh  cd /Users/zhenli/Downloads/xmagic_s106  /bin/sh -c /Users/zhenli/Downloads/xmagic_s106/build/XMagicDemo.build/Debug-iphoneos/XMagicDemo.build/Script-81731F743E244CF2B089C1BF.shCommand /bin/sh failed with exit code 1
```

- **Cause**: Failed to sign `libpag.framework` and `Masonary.framework` again.
- **Solution**:
  1.1. Open **demo/copy_framework.sh**.
  1.2. Change `$(which cmake)` to the absolute path of the local CMake.
  1.3. Change `Apple Development: ......` to your own account signature.

### What should I do if an authorization error occurs when I enter the homepage of the iOS demo?

### What should I do if an error occurs when I build the iOS demo project?

```
unexpected service error: build aborted due to an internal error: unable to write manifest to-xxxx-manifest.xcbuild': mkdir(/data, S_IRWXU | S_IRWXG | S_IRWXO): Read-only file system (30):
```

- **Solution**:
  1.1. Go to **File** > **Project settings** > **Build System** and select **Legacy Build System**.
  1.2. For Xcode 13.0++, you need to select **File** > **Workspace Settings** > **Do not show a diagnostic issue about build system deprecation**.

### What are the relationships between different effect properties?

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2217f0785bb11eda61e525400463ef7.png)


---
*Source: [https://trtc.io/document/60209](https://trtc.io/document/60209)*
