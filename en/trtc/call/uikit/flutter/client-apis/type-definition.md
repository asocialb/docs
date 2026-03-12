# Type Definition

## Common structures

### TUIResult

The return value of calling the API.

| Value | Type | Description |
| --- | --- | --- |
| code | String | If the code is empty "", it means the call succeeded, if the code is not empty "", it means the call failed. |
| message | String? | Error message |

### TUIRoomId

Room ID for audio and video in a call.

**Noteï¼**

(1) `intRoomId`Â andÂ `strRoomId`Â are mutually exclusive. If you choose to useÂ `strRoomId`,Â `intRoomId`Â needs to be filled in as 0. If both are filled in, the SDK will prioritizeÂ `intRoomId`.

(2) Do not mixÂ `intRoomId`Â andÂ `strRoomId`Â because they are not interchangeable. For example, the number 123 and the string "123" represent two completely different rooms.

| Value | Type | Description |
| --- | --- | --- |
| intRoomId | int | Numeric room ID. |
| strRoomId | String | String room number. |

### VideoRenderParams

Video render parameters.

| Value | Type | Description |
| --- | --- | --- |
| fillMode | [FillMode](https://www.tencentcloud.com/document/product/647/54909#FillMode) | Video image fill mode |
| rotation | [Rotation](https://www.tencentcloud.com/document/product/647/54909#Rotation) | Video image rotation direction |

### VideoEncoderParams

Video encoding parameters.

| Value | Type | Description |
| --- | --- | --- |
| resolution | [Resolution](https://www.tencentcloud.com/document/product/647/54909#Resolution) | Video resolution |
| resolutionMode | [ResolutionMode](https://www.tencentcloud.com/document/product/647/54909#ResolutionMode) | Video aspect ratio mode |

### TUICallParams

Call params.

| Value | Type | Description |
| --- | --- | --- |
| roomId | [TUIRoomId](https://www.tencentcloud.com/document/product/647/54909#TUIRoomId) | Room Id. |
| offlinePushInfo | [TUIOfflinePushInfo](https://www.tencentcloud.com/document/product/647/54909#TUIOfflinePushInfo) | Offline push vendor configuration information. |
| timeout | String | Call timeout period, default: 30s, unit: seconds. |
| userData | String | An additional parameter. |
| chatGroupId | String | Group ID. |

### TUIOfflinePushInfo

Offline push vendor configuration informationï¼please refer to:[Offline call push](https://www.tencentcloud.com/document/product/647/50999#).

| Value | Type | Description |
| --- | --- | --- |
| title | String | offlinepush notification title |
| desc | String | offlinepush notification description |
| ignoreIOSBadge | bool | Ignore badge count for offline push (only for iOS), if set to true, the message will not increase the unread count of the app icon on the iOS receiver's side. |
| iOSSound | String | Offline push sound setting (only for iOS). When sound = IOS_OFFLINE_PUSH_NO_SOUND , there will be no sound played when the message is received. When  sound = IOS_OFFLINE_PUSH_DEFAULT_SOUND , the system sound will be played when the message is received. If you want to customize the iOSSound, you need to link the audio file into the Xcode project first, and then set the audio file name (with extension) to the iOSSound. |
| androidSound | String | Offline push sound setting (only for Android, supported by IMSDK 6.1 and above). Only Huawei and Google phones support setting sound prompts. For Xiaomi phones, please refer to:  Xiaomi custom ringtones . In addition, for Google phones, in order to set sound prompts for FCM push on Android 8.0 and above systems, you must call  setAndroidFCMChannelID to set the channelID for it to take effect. |
| androidOPPOChannelID | String | Set the channel ID for OPPO phones with Android 8.0 and above systems. |
| androidVIVOClassification | int | Classification of VIVO push messages (deprecated interface, VIVO push service will optimize message classification rules on April 3, 2023. It is recommended to use setAndroidVIVOCategory to set the message category). 0: Operational messages, 1: System messages. The default value is 1. |
| androidXiaoMiChannelID | String | Set the channel ID for Xiaomi phones with Android 8.0 and above systems. |
| androidFCMChannelID | String | Set the channel ID for google phones with Android 8.0 and above systems. |
| androidHuaWeiCategory | String | Classification of Huawei push messages, please refer to: [Huawei message classification standard.](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835) |
| isDisablePush | bool | Whether to turn off push notifications (default is on). |
| iOSPushType | [TUICallIOSOfflinePushType](https://www.tencentcloud.com/document/product/647/54909#TUICallIOSOfflinePushType) | iOS offline push typeï¼default is APNs |

### TUICallRecords

Call recording information.

| Value | Type | Description |
| --- | --- | --- |
| callId | String | Call recording ID. |
| inviter | String | Inviter ID. |
| inviteList | List<String> | List of invited user IDs. |
| scene | [TUICallScene](https://www.tencentcloud.com/document/product/647/54909#83cc1eda-8838-4ad9-8d60-538b097ab2b7) | Call scenario. |
| mediaType | [TUICallMediaType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Media type. |
| groupId | String | Group ID. |
| role | [TUICallRole](https://www.tencentcloud.com/document/product/647/54909#2be5b153-a7fc-4608-b095-edc663d0f37c) | Role. |
| result | [TUICallResultType](https://www.tencentcloud.com/document/product/647/54909#TUICallMediaType) | Call result type. |
| beginTime | int | Start time. |
| totalTime | int | Total time. |

### TUICallRecentCallsFilter

Call recording filtering conditions.

| Value | Type | Description |
| --- | --- | --- |
| begin | double | Start time. |
| end | double | End time. |
| resultType | [TUICallResultType](https://www.tencentcloud.com/document/product/647/54909#TUICallResultType) | Call result type. |

### CallObserverExtraInfo

Callback extended information.

| Type | Type | Description |
| --- | --- | --- |
| roomId | [TUIRoomId](https://www.tencentcloud.com/document/product/647/54909#TUIRoomId) | room ID |
| role | [TUICallRole](https://www.tencentcloud.com/document/product/647/54909#2be5b153-a7fc-4608-b095-edc663d0f37c) | Call role |
| userData | String | Custom extended field when initiating a call. For details, see [TUICallParams](https://www.tencentcloud.com/document/product/647/54909#TUICallParams). |
| chatGroupId | String | Group ID |

## **enum definition**

### TUICallMediaType

Call media type.

| Type | Description |
| --- | --- |
| none | Unknown |
| audio | Audio call |
| video | Video call |

### TUICallRole

Call role.

| Type | Description |
| --- | --- |
| none | Unknown |
| caller | Callerï¼inviterï¼ |
| called | Calleeï¼inviteeï¼ |

### TUICallStatus

Call status.

| Type | Description |
| --- | --- |
| none | Unknown |
| waiting | The call is currently waiting |
| accept | The call has been accepted |

### TUICallScene

Call scene.

| Type | Description |
| --- | --- |
| groupCall | Group call |
| singleCall | one to one call |

### TUINetworkQuality

Network quality.

| Type | Description |
| --- | --- |
| unknown | Unknown |
| excellent | Excellent |
| good | Good |
| poor | Poor |
| bad | Bad |
| vBad | Very bad |
| down | Down |

### FillMode

If the aspect ratio of the video display area is not equal to that of the video image, you need to specify the fill mode:

| Type | Description |
| --- | --- |
| fill | Fill mode: the video image will be centered and scaled to fill the entire display area, where parts that exceed the area will be cropped. The displayed image may be incomplete in this mode. |
| fit | Fit mode: the video image will be scaled based on its long side to fit the display area, where the short side will be filled with black bars. The displayed image is complete in this mode, but there may be black bars. |

### Rotation

We provides rotation angle setting APIs for local and remote images. The following rotation angles are all clockwise.

| Type | Description |
| --- | --- |
| rotation_0 | No rotation |
| rotation_90 | Clockwise rotation by 90 degrees |
| rotation_180 | Clockwise rotation by 180 degrees |
| rotation_270 | Clockwise rotation by 270 degrees |

### ResolutionMode

Video aspect ratio mode.

| Type | Description |
| --- | --- |
| landscape | Landscape resolution, such as Resolution.Resolution_640_360 + ResolutionMode.Landscape = 640 Ã 360. |
| portrait | Portrait resolution, such as Resolution.Resolution_640_360 + ResolutionMode.Portrait = 360 Ã 640. |

### Resolution

Video resolution.

| Type | Description |
| --- | --- |
| resolution_640_360 | Aspect ratio: 16:9ï¼resolution: 640x360ï¼recommended bitrate: 500kbps |
| resolution_960_540 | Aspect ratio: 16:9ï¼resolution: 960x540ï¼recommended bitrate: 850kbps |
| resolution_1280_720 | Aspect ratio: 16:9ï¼resolution: 1280x720ï¼recommended bitrate: 1200kbps |
| resolution_1920_1080 | Aspect ratio: 16:9ï¼resolution: 1920x1080ï¼recommended bitrate: 2000kbps |

### TUICallIOSOfflinePushType

iOS offline push type.

| Type | Description |
| --- | --- |
| APNs | APNs |
| VoIP | VoIP |

### TUICamera

Camera type.

| Type | Description |
| --- | --- |
| front | Front camera. |
| back | Rear camera. |

### TUIAudioPlaybackDevice

Audio playback device.

| Type | Description |
| --- | --- |
| speakerphone | Speaker |
| earpiece | Earpiece |

### TUICallResultType

Call recording type.

| Type | Description |
| --- | --- |
| unknown | Unknown |
| missed | Missed |
| incoming | Incoming call |
| outgoing | Outgoing Call |

### CallEndReason

Call end reason.

| Type | Description |
| --- | --- |
| unknown | Unknown |
| hangup | Hang up |
| reject | Deny |
| noResponse | No response |
| offline | Offline |
| lineBusy | Busy Line |
| canceled | Cancel call |
| otherDeviceAccepted | Other device answers |
| otherDeviceReject | Other device denies |
| endByServer | Backend ends |


---
*Source: [https://trtc.io/document/54909](https://trtc.io/document/54909)*
