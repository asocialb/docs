# Type Definition

### Common structures

#### TUICallDefine

| Type | Description |
| --- | --- |
| [CallParams](https://www.tencentcloud.com/document/product/647/54900#CallParams) | An additional parameter. |
| [OfflinePushInfo](https://www.tencentcloud.com/document/product/647/54900#OfflinePushInfo) | Offline push vendor configuration information. |
| [CallObserverExtraInfo](https://www.tencentcloud.com/document/product/647/54900#CallObserverExtraInfo) | Extended information |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [RoomId](https://www.tencentcloud.com/document/product/647/54900#RoomId) | Room ID for audio and video in a call. |
| [NetworkQualityInfo](https://www.tencentcloud.com/document/product/647/54900#NetworkQualityInfo) | Network quality information |
| [VideoRenderParams](https://www.tencentcloud.com/document/product/647/54900#VideoRenderParams) | Video render parameters |
| [VideoEncoderParams](https://www.tencentcloud.com/document/product/647/54900#VideoEncoderParams) | Video encoding parameters |

### Enum definition

#### TUICallDefine

| Type | Description |
| --- | --- |
| [MediaType](https://www.tencentcloud.com/document/product/647/54900#MediaType) | Media type in a call |
| [Role](https://www.tencentcloud.com/document/product/647/54900#Role) | Roles of individuals in a call. |
| [Status](https://www.tencentcloud.com/document/product/647/54900#Status) | The call status |
| [Scene](https://www.tencentcloud.com/document/product/647/54900#Scene) | The call scene |
| [IOSOfflinePushType](https://www.tencentcloud.com/document/product/647/54900#IOSOfflinePushType) | iOS offline push type |
| [CallEndReason](https://www.tencentcloud.com/document/product/647/54900#CallEndReason) | Call end reason |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [AudioPlaybackDevice](https://www.tencentcloud.com/document/product/647/54900#AudioPlaybackDevice) | Audio route |
| [Camera](https://www.tencentcloud.com/document/product/647/54900#Camera) | Camera type |
| [NetworkQuality](https://www.tencentcloud.com/document/product/647/54900#NetworkQuality) | Network quality |
| [FillMode](https://www.tencentcloud.com/document/product/647/54900#FillMode) | Video image fill mode |
| [Rotation](https://www.tencentcloud.com/document/product/647/54900#Rotation) | Video image rotation direction |
| [ResolutionMode](https://www.tencentcloud.com/document/product/647/54900#ResolutionMode) | Video aspect ratio mode |
| [Resolution](https://www.tencentcloud.com/document/product/647/54900#Resolution) | Video resolution |

### CallParams

Call params

| Value | Type | Description |
| --- | --- | --- |
| offlinePushInfo | [OfflinePushInfo](https://www.tencentcloud.com/document/product/647/54900#OfflinePushInfo) | Offline push vendor configuration information. |
| timeout | int | Call timeout period, default: 30s, unit: seconds. |
| userData | String | An additional parameter. Callback when the callee receives [onCallReceived](https://www.tencentcloud.com/document/product/647/51007#oncallreceived) |
| chatGroupId | String | chat group Id. |

### OfflinePushInfo

Offline push vendor configuration information, please refer to: [Offline call push](https://www.tencentcloud.com/document/product/647/50999).

| Value | Type | Description |
| --- | --- | --- |
| title | String | offlinepush notification title |
| desc | String | offlinepush notification description |
| ignoreIOSBadge | boolean | Ignore badge count for offline push (only for iOS), if set to true, the message will not increase the unread count of the app icon on the iOS receiver's side. |
| iOSSound | String | Offline push sound setting (only for iOS). When `sound = IOS_OFFLINE_PUSH_NO_SOUND`, there will be no sound played when the message is received. When `sound = IOS_OFFLINE_PUSH_DEFAULT_SOUND`, the system sound will be played when the message is received. If you want to customize the iOSSound, you need to link the audio file into the Xcode project first, and then set the audio file name (with extension) to the iOSSound. |
| androidSound | String | Offline push sound setting (only for Android, supported by IMSDK 6.1 and above). Only Huawei and Google phones support setting sound prompts. For Xiaomi phones, please refer to: [Xiaomi custom ringtones](https://dev.mi.com/console/doc/detail?pId=1278%23_3_0#_3_0). In addition, for Google phones, in order to set sound prompts for FCM push on Android 8.0 and above systems, you must call `setAndroidFCMChannelID`to set the channelID for it to take effect. |
| androidOPPOChannelID | String | Set the channel ID for OPPO phones with Android 8.0 and above systems. |
| androidVIVOClassification | int | Classification of VIVO push messages (deprecated interface, VIVO push service will optimize message classification rules on April 3, 2023. It is recommended to use setAndroidVIVOCategory to set the message category). 0: Operational messages, 1: System messages. The default value is 1. |
| androidXiaoMiChannelID | String | Set the channel ID for Xiaomi phones with Android 8.0 and above systems. |
| androidFCMChannelID | String | Set the channel ID for google phones with Android 8.0 and above systems. |
| androidHuaWeiCategory | String | Classification of Huawei push messages, please refer to: [Huawei message classification standard.](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835) |
| isDisablePush | boolean | Whether to turn off push notifications (default is on). |
| iOSPushType | [IOSOfflinePushType](https://www.tencentcloud.com/document/product/647/54900#IOSOfflinePushType) | iOS offline push type, default is APNs |

### CallObserverExtraInfo

| Value | Type | Description |
| --- | --- | --- |
| roomId | [TUICommonDefine.RoomId](https://www.tencentcloud.com/document/product/647/54900#RoomId) | room ID |
| role | [Role](https://www.tencentcloud.com/document/product/647/54900#Role) | Call role |
| userData | NSString | Custom extended field when initiating a call. |
| chatGroupId | NSString | Group ID |

### RoomId

Room ID for audio and video in a call.
**Note:**

(1) `intRoomId`Â andÂ `strRoomId`Â are mutually exclusive. If you choose to useÂ `strRoomId`,Â `intRoomId`Â needs to be filled in as 0. If both are filled in, the SDK will prioritizeÂ `intRoomId`.

(2)  Do not mixÂ `intRoomId`Â andÂ `strRoomId`Â because they are not interchangeable. For example, the number 123 and the string "123" represent two completely different rooms.

| Value | Type | Description |
| --- | --- | --- |
| intRoomId | int | Numeric room ID.**range:**1 - 2147483647(2^31-1) |
| strRoomId | String | String room ID. **range:**Limited to 64 bytes in length. The supported character set range is as follows (a total of 89 characters):Lowercase and uppercase English letters. (a-zA-Z)Number (0-9) `space`, `!`, `#`, `$`, `%`, `&`, `(`, `)`, `+`, `-`, `:`, `;`, `<`, `=`, `.`, `>`, `?`, `@`, `[`, `]`, `^`, `_`, `{`, `}`, `\|`, `~`, `,` |

> **Note:**Currently, string room number is only supported on Android and iOS platforms. Support for other platforms such as Web, Mini Programs, Flutter, and Uniapp will be available in the future. Please stay tuned!

### NetworkQualityInfo

User network quality information

| Value | Type | Description |
| --- | --- | --- |
| userId | String | user ID |
| quality | [NetworkQuality](https://www.tencentcloud.com/document/product/647/54900#NetworkQuality) | network quality |

### VideoRenderParams

Video render parameters

| Value | Type | Description |
| --- | --- | --- |
| fillMode | [VideoRenderParams.FillMode](https://www.tencentcloud.com/document/product/647/54900#FillMode) | Video image fill mode |
| rotation | [VideoRenderParams.Rotation](https://www.tencentcloud.com/document/product/647/54900#Rotation) | Video image rotation direction |

### VideoEncoderParams

Video encoding parameters

| Value | Type | Description |
| --- | --- | --- |
| resolution | [VideoEncoderParams.Resolution](https://www.tencentcloud.com/document/product/647/54900#Resolution) | Video resolution |
| resolutionMode | [VideoEncoderParams.ResolutionMode](https://www.tencentcloud.com/document/product/647/54900#ResolutionMode) | Video aspect ratio mode |

### MediaType

Call media type

| Value | Type | Description |
| --- | --- | --- |
| Unknown | 0 | Unknown |
| Audio | 1 | Audio call |
| Video | 2 | Video call |

### Role

Call role

| Value | Type | Description |
| --- | --- | --- |
| None | 0 | Unknown |
| Caller | 1 | Caller (inviter) |
| Called | 2 | Callee (invitee) |

### Status

Call status

| Value | Type | Description |
| --- | --- | --- |
| None | 0 | Unknown |
| Waiting | 1 | The call is currently waiting |
| Accept | 2 | The call has been accepted |

### Scene

Call scene

| Value | Type | Description |
| --- | --- | --- |
| SINGLE_CALL | 0 | Group call |
| GROUP_CALL | 1 | Anonymous group calling (not supported at this moment, please stay tuned). |
| MULTI_CALL | 2 | one to one call |

### IOSOfflinePushType

iOS offline push type

| Type | Value | Description |
| --- | --- | --- |
| APNs | 0 | APNs |
| VoIP | 1 | VoIP |

### CallEndReason

| Value | Type | Description |
| --- | --- | --- |
| UNKNOWN | 0 | Unknown |
| HANGUP | 1 | Hang up |
| REJECT | 2 | Deny |
| NO_RESPONSE | 3 | No response |
| OFFLINE | 4 | Offline |
| LINE_BUSY | 5 | Busy Line |
| CANCELED | 6 | Cancel call |
| OTHER_DEVICE_ACCEPTED | 7 | Other device answers |
| OTHER_DEVICE_REJECT | 8 | Other device denies |
| END_BY_SERVER | 9 | Backend ends |

### AudioPlaybackDevice

Audio route

| Type | Value | Description |
| --- | --- | --- |
| Speakerphone | 0 | Earpiece |
| Earpiece | 1 | Speakerphone |

### Camera

Front/Back camera

| Type | Value | Description |
| --- | --- | --- |
| Front | 0 | Front camera |
| Back | 1 | Back camera |

### NetworkQuality

Network quality

| Type | Value | Description |
| --- | --- | --- |
| UNKNOWN | 0 | Unknown |
| EXCELLENT | 1 | Excellent |
| GOOD | 2 | Good |
| GOOD | 3 | Poor |
| BAD | 4 | Bad |
| VERY_BAD | 5 | very bad |
| DOWN | 6 | Down |

### FillMode

If the aspect ratio of the video display area is not equal to that of the video image, you need to specify the fill mode:

| Type | Value | Description |
| --- | --- | --- |
| Fill | 0 | Fill mode: the video image will be centered and scaled to fill the entire display area, where parts that exceed the area will be cropped. The displayed image may be incomplete in this mode. |
| Fit | 1 | Fit mode: the video image will be scaled based on its long side to fit the display area, where the short side will be filled with black bars. The displayed image is complete in this mode, but there may be black bars. |

### Rotation

We provides rotation angle setting APIs for local and remote images. The following rotation angles are all clockwise.

| Type | Value | Description |
| --- | --- | --- |
| Rotation_0 | 0 | No rotation |
| Rotation_90 | 1 | Clockwise rotation by 90 degrees |
| Rotation_180 | 2 | Clockwise rotation by 180 degrees |
| Rotation_270 | 3 | Clockwise rotation by 0 degrees |

### ResolutionMode

Video aspect ratio mode

| Type | Value | Description |
| --- | --- | --- |
| Landscape | 0 | Landscape resolution, such as Resolution.Resolution_640_360 + ResolutionMode.Landscape = 640 Ã 360. |
| Portrait | 1 | Portrait resolution, such as Resolution.Resolution_640_360 + ResolutionMode.Portrait = 360 Ã 640. |

### Resolution

Video resolution

| Type | Value | Description |
| --- | --- | --- |
| Resolution_640_360 | 108 | Aspect ratio: 16:9, resolution: 640x360, recommended bitrate: 500kbps |
| Resolution_960_540 | 110 | Aspect ratio: 16:9, resolution: 960x540, recommended bitrate: 850kbps |
| Resolution_1280_720 | 112 | Aspect ratio: 16:9, resolution: 1280x720, recommended bitrate: 1200kbps |
| Resolution_1920_1080 | 114 | Aspect ratio: 16:9, resolution: 1920x1080, recommended bitrate: 2000kbps |


---
*Source: [https://trtc.io/document/54900](https://trtc.io/document/54900)*
