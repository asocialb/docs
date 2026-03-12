# Upgrading

## Upgrade Instructions

**TUICallKit** is a new audio and video calling UI component launched by Tencent Cloud. It is an upgraded version of TUICalling, which supports more functional features such as group calling and AI noise reduction, and supports calling between all platforms with greater stability. We welcome you to use the new TUICallKit component. Before upgrading, please note the following:

- TUICalling and TUICallKit support mutual calling. Please keep the SDKAppID unchanged before and after the upgrade, otherwise it will affect mutual communication.
- TUICallKit needs to be used with the IM audio and video calling capability package. You can click on the [IM console](https://console.tencentcloud.com/im), enter the **Basic Configuration** page of the corresponding SDKAppID application, and find the Call function area in the lower right corner of the page. Click **Try now** to open TUICallKit's 7-day free trial service. If you need to officially launch the application, click **Purchase** to enter the [purchase](https://buy.tencentcloud.com/avc) page.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3c206347b5f511eeb395525400461a83.png)

> **Noteï¼**The IM audio and video calling capability provides differentiated paid versions for different business needs, and you can learn about the included features and purchase the version that suits you on the [IM purchase page](https://buy.tencentcloud.com/avc).

## Upgrade Steps

TUICallKit was designed to accommodate the upgrade needs of TUICalling customers, and can be upgraded in just two simple steps, which is expected to take 20 minutes:

### Upgrade the dependency to TUICallKit

Complete the dependency upgrade to TUICallKit in your project and set the configuration file **pubspec.yaml** for your project:

```
dependencies:  # Remove the old dependency tim_ui_kit_calling_plugin and add the new dependency tencent_calls_uikit:  tencent_calls_uikit:
```

After setting up, execute the command `flutter pub get`.

> **Note****ï¼**If you previously used it with IM components such as TUIChat and TUIContact, you can use TUICallKit normally after completing this step. The compatibility logic has been handled internally in the TUICallKit component.

### 2ãModify API usage

After completing the above steps, your project will not compile normally. You need to replace the TUICalling API with the new TUICallKit API. You can refer to the following API comparison information and search and replace it.

| API meaning | TUICalling(tim_ui_kit_calling_plugin) | TUICallKit(tencent_calls_uikit) | Explanation |
| --- | --- | --- | --- |
| Create a TUICallKit instance | TUICalling.sharedInstance | TUICallKit.[instance](https://trtc.io/document/46660/51002/54904/54906) | Replace reference and name. |
| Set the user's nickname | TUICalling.setUserNickname | TUICallKit.[setSelfInfo](https://trtc.io/document/46660/51002/54904/54906#setSelfInfo) | Integrate the interface for setting avatar and nickname into the setSelfInfo interface. |
| Set the user's avatar | TUICalling.setUserAvatar | TUICallKit.[setSelfInfo](https://trtc.io/document/46660/51002/54904/54906#setSelfInfo) | Integrate the interface for setting avatar and nickname into the setSelfInfo interface. |
| Initiate a 1v1 call | TUICalling.call | TUICallKit.[call](https://trtc.io/document/46660/51002/54904/54906#call) | See TUICalling.call interface changes for details. |
| Initiate a group call | / | TUICallKit.[groupCall](https://trtc.io/document/46660/51002/54904/54906#groupCall) | / |
| Actively join the current group call | / | TUICallKit.[joinInGroupCall](https://trtc.io/document/46660/51002/54904/54906#joinInGroupCall) | / |
| Set custom ringtone | TUICalling.setCallingBell | TUICallKit.[setCallingBell](https://trtc.io/document/46660/51002/54904/54906) | Replace reference and name. |
| Enable/disable mute mode | TUICalling.enableMuteMode | TUICallKit.[enableMuteMode](https://trtc.io/document/46660/51002/54904/54906#enableMuteMode) | Replace reference and name. |
| Enable/disable floating window function | TUICalling.enableFloatWindow | TUICallKit.[enableFloatWindow](https://trtc.io/document/46660/51002/54904/54906#enableFloatWindow) | Replace reference and name. |
| Set listener | TUICalling.registerListener | TUICallEngine.[addObserver](https://trtc.io/document/46660/51002/54904/54907#addobserver) | See TUICalling.registerListener interface changes for details. |

Here are the adaptation solutions for the two APIs with significant changes during this upgrade:

#### TUICalling.call Interface Changes

- **TUICalling Code Example:**

```
// Original InterfaceFuture<void> call(String userId, CallingScenes type, [OfflinePushInfo? offlinePushInfo]);
```

- **TUICallKit Code Example:**

```
// New InterfaceFuture<void> call(String userId, TUICallMediaType callMediaType, [TUICallParams? params]);// New Calling MethodTUIOfflinePushInfo offlinePushInfo = TUIOfflinePushInfo();offlinePushInfo.title = "Flutter TUICallKit";offlinePushInfo.desc = "This is an incoming call from Flutter TUICallkit";TUICallParams params = TUICallParams(offlinePushInfo: offlinePushInfo);TUICallKit.instance.call(callUserId, TUICallMediaType.audio, params);
```

#### TUICallKit.setCallingListener Interface Changes

- **TUICalling Code Example:**

```
TUICalling.sharedInstance().registerListener(TUICallingListener(    onInvited: (params) {    }    onCallingCancel: () {    }    â¦â¦));
```

- **TUICallKit Code Example:**

```
TUICallEngine.instance.addObserver(TUICallObserver(    onError:(int code, String message) {    },     onCallCancelled: (String callerId) {    },    onCallBegin:(TUIRoomId roomId, TUICallMediaType callMediaType, TUICallRole callRole) {    },    â¦â¦));
```

After upgrading the above APIs, you can use the `TUICallKit` component normally.


---
*Source: [https://trtc.io/document/58626](https://trtc.io/document/58626)*
