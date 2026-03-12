# TUICallKit

## TUICallKit APIs

`TUICallKit` is an audio/video call component that **includes UI elements**. You can use its APIs to quickly implement an audio/video call application similar to WeChat. For directions on integration, see [Integrating TUICallKit](https://www.tencentcloud.com/document/product/647/54896).

## API overview

| API | Description |
| --- | --- |
| [login](#login) | Log in |
| [logout](#logout) | Sign out |
| [setSelfInfo](https://www.tencentcloud.com/document/product/647/54906#setSelfInfo) | Sets the user nickname and profile photo. |
| [calls](https://www.tencentcloud.com/document/product/647/54906#calls) | Start a call. |
| [join](https://www.tencentcloud.com/document/product/647/54906#join) | Join the call. |
| [enableMuteMode](https://www.tencentcloud.com/document/product/647/54906#enableMuteMode) | Sets whether to turn on the mute mode. |
| [enableFloatWindow](https://www.tencentcloud.com/document/product/647/54906#enableFloatWindow) | Sets whether to enable floating windows. |
| [setCallingBell](https://www.tencentcloud.com/document/product/647/54906#setCallingBell) | Custom ringtone. |
| [enableVirtualBackground](https://www.tencentcloud.com/document/product/647/54906#enableVirtualBackground) | Turn On/Off the Virtual Background feature |

## Details

### login

```
Future<TUIResult> login(int sdkAppId, String userId, String userSig)
```

| Parameter | Type | Description |
| --- | --- | --- |
| sdkAppId | int | User SDKAppID |
| userId | String | User ID, a string type, can only include English letters (a-z and A-Z), numbers (0-9), hyphens (-), and underscores (_). |
| userSig | String | User Signature. UserSig is obtained by encrypting information such as sdkAppId and userId using the SDKSecretKey([Signature calculation method](https://www.tencentcloud.com/document/product/647/35166)). It serves as a ticket for authentication, enabling Tencent Cloud to determine if the current user is authorized to use TRTC services. |
| return value | [TUIResult](https://www.tencentcloud.com/document/product/647/54909#TUIResult) | Contains code and message information: code is empty ("") means the call is successful; code is not empty ("") means the call failed, see message for the reason of failure |

### logout

```
Future<void> logout()
```

### setSelfInfo

This API is used to set the alias and profile photo. The alias cannot exceed 500 bytes, and the profile photo is specified by a URL.

```
Future<TUIResult> setSelfInfo(String nickname, String avatar)
```

| Parameter | Type | Description |
| --- | --- | --- |
| nickName | String | The nick name. |
| avatar | String | The profile photo. |
| return value | [TUIResult](https://www.tencentcloud.com/document/product/647/54909#TUIResult) | Contains code and message information: code is empty ("") means the call is successful; code is not empty ("") means the call failed, see message for the reason of failure |

### calls

Initiate a call. **Supported by v2.9+.**

```
Future<TUIResult> calls(List<String> userIdList, TUICallMediaType mediaType, TUICallParams params)
```

| Parameter | Type | Description |
| --- | --- | --- |
| userIdList | List<String> | The target user IDs. |
| callMediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | The call type, which can be video or audio. |
| params | [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams) | **Optional**Extended call parameters, such as room number, call invitation timeout, offline push of custom content, etc. |

### join

Actively join the call. **Supported by v2.9+.**

```
Future<void> join(String callId)
```

| Parameter | Type | Description |
| --- | --- | --- |
| callId | String | Unique ID for this call. |

### enableMuteMode

This API is used to set whether to turn on the mute mode.

```
Future<void> enableMuteMode(bool enable)
```

| Parameter | Type | Description |
| --- | --- | --- |
| enable | bool | Turn on and off the mute; true means to turn on the mute |

### enableFloatWindow

This API is used to set whether to enable floating windows. The default value is `false`, and the floating window button in the top left corner of the call view is hidden. If it is set to `true`, the button will become visible.

```
Future<void> enableFloatWindow(bool enable)
```

| Parameter | Type | Description |
| --- | --- | --- |
| enable | bool | The default value is false, and the floating window button in the top left corner of the call view is hidden. If it is set to true, the button will become visible. |

### setCallingBell

Custom ringtone.

```
Future<void> setCallingBell(String assetName)
```

| Parameter | Type | Description |
| --- | --- | --- |
| assetName | String | The path of the ringtone. The ringtone file needs to be added to the assets resource of the main project. |

### enableVirtualBackground

Turn On/Off the Virtual Background feature. After enabling the Virtual Background feature, you can display the Blurry Background feature button on the UI. Clicking the button will directly enable the Blurry Background feature.

```
Future<void> enableVirtualBackground(bool enable)
```

| Parameter | Type | Meaning |
| --- | --- | --- |
| enable | bool | Turn on, turn off mute; true means mute is on |

## Deprecated interfaces

### call

This API is used to make a (one-to-one) call.

> **Noteï¼**This interface has been deprecated in v2.9+. It is recommended to use the calls interface instead.

```
Future<void> call(String userId, TUICallMediaType callMediaType, [TUICallParams? params])
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | The target user ID. |
| callMediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | `The call type, which can be video or audio.` |

### groupCall

This API is used to make a group call.

> **Noteï¼**This interface has been deprecated in v2.9+. It is recommended to use the calls interface instead.

```
Future<void> groupCall(String groupId, List<String> userIdList, TUICallMediaType callMediaType,[TUICallParams? params])
```

The parameters are described below:

| Parameter | Type | Description |
| --- | --- | --- |
| groupId | String | The group ID. |
| userIdList | List<String> | The target user IDs. |
| callMediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | `The call type, which can be video or audio.` |

### joinInGroupCall

This API is used to join a group call.Before making a group call, you need to create an IM group first.

> **Noteï¼**This interface has been deprecated in v2.9+. It is recommended to use the join interface instead.

```
Future<void> joinInGroupCall(TUIRoomId roomId, String groupId, TUICallMediaType callMediaType)
```

| Parameter | Type | Description |
| --- | --- | --- |
| roomId | [TUIRoomID](https://www.tencentcloud.com/document/product/647/54909#TUIRoomId) | The room ID. |
| groupId | String | The group ID. |
| callMediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | `The call type, which can be video or audio.` |


---
*Source: [https://trtc.io/document/54906](https://trtc.io/document/54906)*
