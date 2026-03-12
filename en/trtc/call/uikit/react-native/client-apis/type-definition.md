# Type Definition

### callParams

In the [Tencent RTC Console](https://console.trtc.io/), call extension parameters such as room number, call invitation timeout, offline push custom content, etc.

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| roomId | [RoomId](https://www.tencentcloud.com/document/product/647/66840#280a991e-d6a9-4194-9c98-ab703173227f) | No | Room ID, for details, please refer to RoomId. |
| timeout | Number | No | Call timeout, default: 40 seconds, unit: seconds. timeout = 0 means no timeout |
| userData | String | No | Custom extension fields when initiating a call |
| offlinePushInfo | [OfflinePushInfo](https://www.tencentcloud.com/document/product/647/66840#999e53e6-d49d-48d9-b058-d5b690019c49) | No | Custom offline message push parameters |
| chatGroupId | String | No | chat group Id. |

### RoomId

Room ID, divided into String type and Number type.

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| strRoomId | String | No | Room ID, String type |
| intRoomId | Number | No | Room ID, String type |

### OfflinePushInfo

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| title | String | No | offlinepush notification title |
| desc | String | No | offlinepush notification description |
| ignoreIOSBadge | boolean | No | Ignore badge count for offline push (only for iOS), if set to true, the message will not increase the unread count of the app icon on the iOS receiver's side. |
| iOSSound | String | No | Offline push sound setting (only for iOS). When`sound = IOS_OFFLINE_PUSH_NO_SOUND`, there will be no sound played when the message is received. When `sound = IOS_OFFLINE_PUSH_DEFAULT_SOUND`, the system sound will be played when the message is received. If you want to customize the iOSSound, you need to link the audio file into the Xcode project first, and then set the audio file name (with extension) to the iOSSound. |
| androidSound | String | No | Offline push sound setting (only for Android, supported by IMSDK 6.1 and above). Only Huawei and Google phones support setting sound prompts. For Xiaomi phones, please refer to: [Xiaomi custom ringtones](https://dev.mi.com/console/doc/detail?pId=1278%23_3_0#_3_0). In addition, for Google phones, in order to set sound prompts for FCM push on Android 8.0 and above systems, you must call `setAndroidFCMChannelID`to set the channelID for it to take effect. |
| androidOPPOChannelID | String | No | Set the channel ID for OPPO phones with Android 8.0 and above systems. |
| androidVIVOClassification | Number | No | Classification of VIVO push messages (deprecated interface, VIVO push service will optimize message classification rules on April 3, 2023. It is recommended to use setAndroidVIVOCategory to set the message category). 0: Operational messages, 1: System messages. The default value is 1. |
| androidXiaoMiChannelID | String | No | Set the channel ID for Xiaomi phones with Android 8.0 and above systems. |
| androidFCMChannelID | String | No | Set the channel ID for google phones with Android 8.0 and above systems. |
| androidHuaWeiCategory | String | No | Classification of Huawei push messages, please refer to:[Huawei message classification standard.](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835) |
| isDisablePush | boolean | No | Whether to turn off push notifications (default is on). |
| iOSPushType | [IOSOfflinePushType](https://www.tencentcloud.com/document/product/647/66840#9031c0d2-69a0-4e33-bda1-aea049930293) | No | iOS offline push typeï¼default is APNs |

### IOSOfflinePushType

iOS offline push type

| Parameter | Description |
| --- | --- |
| APNs | APNs |
| VoIP | VoIP |

### MediaType

Call media type

| Parameter | Description |
| --- | --- |
| Audio | Audio call |
| Video | Video call |

### Camera

Front or Back Camera

| Parameter | Description |
| --- | --- |
| Front | Front camera |
| Back | Rear camera |

### AudioPlaybackDevice

Audio route

| Parameter | Description |
| --- | --- |
| Earpiece | Audio route is earpiece |
| Speakerphone | Audio route is Speakerphone |

### FillMode

If the aspect ratio of the video display area is not equal to that of the video image, you need to specify the fill mode:

| Parameter | Description |
| --- | --- |
| Fill | Fill mode: the video image will be centered and scaled to fill the entire display area, where parts that exceed the area will be cropped. The displayed image may be incomplete in this mode. |
| Fit | Fit mode: the video image will be scaled based on its long side to fit the display area, where the short side will be filled with black bars. The displayed image is complete in this mode, but there may be black bars. |

### Rotation

We provides rotation angle setting APIs for local and remote images. The following rotation angles are all clockwise.

| Parameter | Description |
| --- | --- |
| Rotation_0 | No rotation |
| Rotation_90 | Clockwise rotation by 90 degrees |
| Rotation_180 | Clockwise rotation by 180 degrees |
| Rotation_270 | Clockwise rotation by 0 degrees |

### Resolution

Video resolution

| Parameter | Description |
| --- | --- |
| Resolution_640_360 | Aspect ratio: 16:9ï¼resolution: 640x360ï¼recommended bitrate: 500kbps |
| Resolution_640_480 | Aspect ratio: 4:3ï¼resolution: 640x480ï¼recommended bitrate: 600kbps |
| Resolution_960_540 | Aspect ratio: 16:9ï¼resolution: 960x540ï¼recommended bitrate: 850kbps |
| Resolution_960_720 | Aspect ratio: 4:3ï¼resolution: 960x720ï¼recommended bitrate: 1000kbps |
| Resolution_1280_720 | Aspect ratio: 16:9ï¼resolution: 1280x720ï¼recommended bitrate: 1200kbps |
| Resolution_1920_1080 | Aspect ratio: 16:9ï¼resolution: 1920x1080ï¼recommended bitrate: 2000kbps |

### ResolutionMode

Video aspect ratio mode

| Parameter | Description |
| --- | --- |
| Landscape | Landscape resolution, such as Resolution.Resolution_640_360 + ResolutionMode.Landscape = 640 Ã 360. |
| Portrait | Portrait resolution, such as Resolution.Resolution_640_360 + ResolutionMode.Portrait = 360 Ã 640. |


---
*Source: [https://trtc.io/document/66840](https://trtc.io/document/66840)*
