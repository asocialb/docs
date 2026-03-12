# Group Call

This article introduces the use of the group call feature, such as initiating a group call and joining a group call.

## Expected outcome

TUICallKit supports multiplayer calls. The expected outcome is shown in the figure below.

| **Initiate a multiplayer call** | **Receive a multiplayer call request** | **Accept a multiplayer call requests** |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ea835861ec1011ee896d5254005cb287.jpg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f71b3d5aec1011eea93552540076ba55.jpg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fc9901aeec1011ee896d5254005cb287.jpg) |

## Initiate a Multiplayer Call

Initiate a group call by calling the groupCall API.

Android (Kotlin)

Android (Java)

iOS (Swift)

iOS (Objective-C)

Flutter (Dart)

```
import com.tencent.qcloud.tuikit.tuicallengine.TUICallDefineimport com.tencent.qcloud.tuikit.tuicallkit.TUICallKitval list = mutableListOf<String>()list.add("mike")list.add("tate")TUICallKit.createInstance(context).calls(list, TUICallDefine.MediaType.Audio, null, null)
```

```
import com.tencent.qcloud.tuikit.tuicallengine.TUICallDefine;import com.tencent.qcloud.tuikit.tuicallkit.TUICallKit;List<String> list = new ArrayList<>();list.add("mike")list.add("tate")TUICallKit.createInstance(context).calls(list, TUICallDefine.MediaType.Audio, null, null);
```

```
import TUICallKit_Swiftimport RTCRoomEngineTUICallKit.createInstance().calls(userIdList: ["mike","tate"], callMediaType: .audio, params: nil) {} fail: { code, message in}
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>#import <RTCRoomEngine/TUICallEngine.h>[[TUICallKit createInstance] calls:@[@"mike", @"tate"] callMediaType:TUICallMediaTypeAudio params:NULL succ:^{} fail:^(int code, NSString * _Nullable errMsg) {}];
```

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';void call() {    List<String> userIdList = ['vince','mike'];    TUICallKit.instance.call(userIdList, TUICallMediaType.audio);}
```

## Join a Call

Call the join API to actively join an existing audio and video call.

Android (Kotlin)

Android (Java)

iOS (Swift)

iOS (Objective-C)

Flutter (Dart)

```
import com.tencent.qcloud.tuikit.tuicallkit.TUICallKitTUICallKit.createInstance(context).join("12345678")
```

```
import com.tencent.qcloud.tuikit.tuicallkit.TUICallKit;TUICallKit.createInstance(context).join("*****");
```

```
import TUICallKit_SwiftTUICallKit.createInstance().join(callId: "")
```

```
#import "TUICallKit_Swift-Swift.h"[[TUICallKit createInstance] joinWithCallId: @"***"];
```

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';void join() {    TUICallKit.instance.join("*****")}
```


---
*Source: [https://trtc.io/document/59837](https://trtc.io/document/59837)*
