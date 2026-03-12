# Floating Window

This article explains how to use the Floating Window feature.

## Expected outcome

| **Activate floating button** | **Voice call floating window** | **Video call floating window** |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b1852b3ec1211eeb5dc525400aa857d.PNG) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/46d96dc5ec1211ee896d5254005cb287.PNG) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/59f88978ec1211ee94705254001a1c03.PNG) |

## Floating Window feature

TUICallKit allows users to minimize the call interface into a floating window using the floating window button at the top left corner of the call interface during a call.

If your business needs to enable this feature, you can use the enableFloatWindow method to activate this feature during the initialization of the TUICallKit component:

Android(Kotlin)

Android(Java)

iOS(Swift)

iOS(Objective-C)

Flutter(Dart)

```
TUICallKit.createInstance(context).enableFloatWindow(true)
```

```
TUICallKit.createInstance(context).enableFloatWindow(true);
```

```
import TUICallKit_SwiftTUICallKit.createInstance().enableFloatWindow(enable: true)
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>[[TUICallKit createInstance] enableFloatWindowWithEnable:YES];
```

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';void enableFloatWindow() {    TUICallKit.instance.enableFloatWindow(true);}
```


---
*Source: [https://trtc.io/document/59841](https://trtc.io/document/59841)*
