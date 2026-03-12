# GroupCall

This article introduces the use of the group call feature, such as initiating a group call and joining a group call.

## Expected outcome

TUICallKit supports group calls (up to 9 people). The expected outcome is shown in the figure below.

| **Web** | **Mobile Client** |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c0ee84111bdd11ef88ad5254002977b6.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/719237f0ec0b11ee896d5254005cb287.png) |

## Initiate a Multiplayer Call

Initiate a group call by calling the `groupCall` API.

```
import { TUICallKitAPI, CallMediaType } from "@trtc/calls-uikit-react";try {   const params = {     userIDList: ['user1', 'user2'],      type: CallMediaType.VIDEO,   }  await TUICallKitAPI.calls(params);} catch (error: any) {  console.error(`[TUICallKit] calls failed. Reason:${error}`);}
```

### Join a group call

Join an existing audio and video call in the group by calling the `join` API.

```
try {  const params = {    callId: 'xxx'  };  await TUICallKitAPI.join(params);} catch (error: any) {  console.error(`[TUICallKit] join failed. Reason: ${error}`);}
```


---
*Source: [https://trtc.io/document/59838](https://trtc.io/document/59838)*
