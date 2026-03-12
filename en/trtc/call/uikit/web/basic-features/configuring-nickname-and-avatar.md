# Configuring Nickname and Avatar

This article explains how to set up a user's avatar and nickname.

## Setting Avatar, Nickname

To customize the nickname or profile photo, use the following API for update:

Androidï¼Kotlinï¼

Androidï¼Javaï¼

iOS(Swift)

iOS(Objective-C)

Flutterï¼Dartï¼

Web&H5

uni-app(Andorid&iOS)

```
import com.tencent.qcloud.tuikit.TUICommonDefineimport com.tencent.qcloud.tuikit.tuicallkit.TUICallKitTUICallKit.createInstance(context).setSelfInfo("jack", "https:/****/user_avatar.png",    object : TUICommonDefine.Callback {        override fun onSuccess() {        }        override fun onError(errorCode: Int, errorMessage: String?) {        }    })
```

```
import com.tencent.qcloud.tuikit.TUICommonDefine;import com.tencent.qcloud.tuikit.tuicallkit.TUICallKit;TUICallKit.createInstance(context).setSelfInfo("jack", "https:/****/user_avatar.png", new TUICommonDefine.Callback() {    @Override    public void onSuccess() {    }    @Override    public void onError(int errorCode, String errorMessage) {    }});
```

```
import TUICallKit_Swiftimport TUICallEngineTUICallKit.createInstance().setSelfInfo(nickname: "", avatar: "") {} fail: { code, message in}
```

```
#import <TUICallKit_Swift/TUICallKit_Swift-Swift.h>[[TUICallKit createInstance] setSelfInfoWithNickname:@"" avatar:@"" succ:^{} fail:^(int code, NSString * _Nullable errMsg) {}];
```

```
import 'package:tencent_calls_uikit/tencent_calls_uikit.dart';void setSelfInfo() {    TUIResult result = TUICallKit.instance.setSelfInfo('userName', 'url:********');}
```

```
import { TUICallKitAPI } from '@trtc/calls-uikit-vue';// import { TUICallKitAPI } from '@tencentcloud/call-uikit-react';try {  await TUICallKitAPI.setSelfInfo({ nickName: "jack", avatar: "http://xxx" });} catch (error) {  console.error(`[TUICallKit] Failed to call the setSelfInfo API. Reason: ${error}`);}
```

```
const options = {    nickName: 'jack',    avatar: 'https:/****/user_avatar.png'};TUICallKit.setSelfInfo(options, (res) => {    if (res.code === 0) {        console.log('setSelfInfo success');    } else {        console.log(`setSelfInfo failed, error message = ${res.msg}`);    }});
```

> **Note**The update of the callee's nickname and profile photo may be delayed during a call between non-friend users due to the user privacy settings. After a call is made successfully, the information will also be updated properly in subsequent calls.


---
*Source: [https://trtc.io/document/59834](https://trtc.io/document/59834)*
