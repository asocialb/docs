# Monitoring Call Status

This article explains the usage of TUICallKit call status callback. You can monitor call events (e.g., start, end, member join, and leave) via call callback registration.

> **Note:**On the Android platform, when setting TUICallObserver to listen for callbacks, ensure that the class hosting the callback will not be destroyed. For example, it is not recommended to add the observer in LoginActivity, as when LoginActivity is destroyed, the callback will also be destroyed; it is suggested to observe in the application's Application class or the main application interface.

## Call Status Callback

Detect key state changes throughout the call lifecycle.

Kotlin

Swift

Dart

```
import com.tencent.qcloud.tuikit.TUICommonDefineimport com.tencent.qcloud.tuikit.tuicallengine.TUICallDefineimport com.tencent.qcloud.tuikit.tuicallengine.TUICallEngineimport com.tencent.qcloud.tuikit.tuicallengine.TUICallObserverprivate val observer: TUICallObserver = object : TUICallObserver() {    override fun onCallReceived(callId: String?, callerId: String?, calleeIdList: MutableList<String>?, mediaType: TUICallDefine.MediaType?, info: TUICallDefine.CallObserverExtraInfo?) {    }        override fun onCallBegin(roomId: TUICommonDefine.RoomId?, callMediaType: TUICallDefine.MediaType?, callRole: TUICallDefine.Role?) {    }        override fun onCallEnd(roomId: TUICommonDefine.RoomId?, callMediaType: TUICallDefine.MediaType?, callRole: TUICallDefine.Role?, totalTime: Long) {    }        override fun onCallNotConnected(callId: String?, mediaType: TUICallDefine.MediaType?, reason: TUICallDefine.CallEndReason?, userId: String?, info: TUICallDefine.CallObserverExtraInfo?) {    }    â¦â¦}private fun initData() {    TUICallEngine.createInstance(context).addObserver(observer)}
```

```
import TUICallEngineTUICallEngine.createInstance().addObserver(self)func onCallReceived(_ callId: String, callerId: String, calleeIdList: [String], mediaType: TUICallMediaType, info: TUICallObserverExtraInfo) {}func onCallBegin(callId: String, mediaType: TUICallMediaType, info: TUICallObserverExtraInfo) {}func onCallEnd(callId: String, mediaType: TUICallMediaType, reason: TUICallEndReason, userId: String, totalTime: Float, info: TUICallObserverExtraInfo) {}func onCallNotConnected(callId: String, mediaType: TUICallMediaType, reason: TUICallEndReason, userId: String, info: TUICallObserverExtraInfo) {}
```

```
import 'package:tencent_calls_engine/tencent_calls_engine.dart';TUICallObserver observer = TUICallObserver(    onCallReceived: (String callId, String callerId, List<String> calleeIdList, TUICallMediaType mediaType, CallObserverExtraInfo info) {    }, onCallBegin: (String callId, TUICallMediaType mediaType, CallObserverExtraInfo info) {    }, onCallEnd: (String callId, TUICallMediaType mediaType, CallEndReason reason, String userId, double totalTime, CallObserverExtraInfo info) {    }, onCallNotConnected: (String callId, TUICallMediaType mediaType, CallEndReason reason, String userId, CallObserverExtraInfo info) {    }    â¦â¦)void addObserver() {    TUICallEngine.instance.addObserver(observer);}
```

## Call Member Update Callback

Track individual actions or status changes of call participants, primarily used for real-time display of member dynamics (such as join, leave, reject).

Kotlin

Swift

Dart

```
import com.tencent.qcloud.tuikit.TUICommonDefineimport com.tencent.qcloud.tuikit.tuicallengine.TUICallDefineimport com.tencent.qcloud.tuikit.tuicallengine.TUICallEngineimport com.tencent.qcloud.tuikit.tuicallengine.TUICallObserverprivate val observer: TUICallObserver = object : TUICallObserver() {    override fun onUserJoin(userId: String?) {    }        override fun onUserLeave(userId: String?) {    }        override fun onUserInviting(userId: String?) {    }        override fun onUserReject(userId: String?) {    }    â¦â¦}private fun initData() {    TUICallEngine.createInstance(context).addObserver(observer)}
```

```
import TUICallEngineTUICallEngine.createInstance().addObserver(self)func onUserJoin(userId: String) {}func onUserLeave(userId: String) {}func onUserInviting(userId: String) {}func onUserReject(userId: String) {}â¦â¦
```

```
import 'package:tencent_calls_engine/tencent_calls_engine.dart';TUICallObserver observer = TUICallObserver(    onUserJoin: (String userId) {    }, onUserLeave: (String userId) {    }, onUserInviting: (String userId) {    }, onUserReject: (String userId) {    },    â¦â¦)void addObserver() {    TUICallEngine.instance.addObserver(observer);}
```


---
*Source: [https://trtc.io/document/59851](https://trtc.io/document/59851)*
