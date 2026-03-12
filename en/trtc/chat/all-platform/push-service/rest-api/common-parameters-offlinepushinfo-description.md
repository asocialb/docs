# Common Parameters (OfflinePushInfo Description)

## Push OfflinePushInfo Description

OfflinePushInfo is a JSON Object dedicated to notification bar push configuration, allowing you to configure whether to close the push, push title description, text description, push passthrough, and related parameters of push vendors.

### Standard Notification Push

- Marketing news push.

```
{    // other parameters...    "OfflinePushInfo": {        "PushFlag": 0,        "Title":"Offline Push Title"        "Desc": "offline push content"        "Ext": "{\\"entity\\":{\\"key1\\":\\"value1\\",\\"key2\\":\\"value2\\"}}",  // passthrough field, push uses string in json format        "AndroidInfo": {             "Sound": "shake",  // ringtone filename, without suffix            "XiaoMiChannelID": "xiaomi_channel_id",            "OPPOChannelID": "oppo_channel_id",            "OPPOCategory": "MARKETING",   // OPPO message categorization: content and marketing            "VIVOCategory": "MARKETING",   // VIVO message categorization: operational messages            "HuaWeiCategory": "MARKETING", // Huawei message category: information marketing            "HonorImportance": "LOW",      // Honor message category: information marketing            "MeiZuNoticeMsgType": 0        // Meizu Message category: information marketing        },        "ApnsInfo": {            "Sound": "apns.mp3", // ringtone filename, with suffix            "BadgeMode": 1,            "Title":"apns title",            "SubTitle":"apns subtitle",            "Image":"www.image.com",            "MutableContent": 1        }    }}
```

- Private message push.

```
{    // other parameters...    "OfflinePushInfo": {        "PushFlag": 0,        "Title":"Offline Push Title"        "Desc": "offline push content"        "Ext": "{\\"entity\\":{\\"key1\\":\\"value1\\",\\"key2\\":\\"value2\\"}}",  // passthrough field, recommended string in json format        "AndroidInfo": {             "Sound": "shake",  // ringtone filename, without suffix            "XiaoMiChannelID": "xiaomi_channel_id",            "OPPOChannelID": "oppo_channel_id",            "VIVOCategory": "IM",                 // vivo message categorization: system message            "HuaWeiCategory": "IM",               // Huawei message category: service and communication            "HonorImportance": "NORMAL",          // Honor message category: service communication            "MeiZuNoticeMsgType": 0               // Meizu Message category: private message            "OPPOCategory": "IM",                 // OPPO message category: communication and service            "OPPOPrivateMsgTemplateId": "xxxx",   // OPPO private message template id            "OPPOPrivateTitleParameters": {       // OPPO private message title template parameters in json format                "k1": "v1"                ...            },            "OPPOPrivateContentParameters": {     // OPPO private message content template parameters in json format                "k1": "v1",                ...            },        },        "ApnsInfo": {            ...    // For details, refer to the ApnsInfo field description        }    }}
```

### APNs Passthrough Push

```
{    // other parameters...    "OfflinePushInfo": {        "Ext": "{\\"entity\\":{\\"key1\\":\\"value1\\",\\"key2\\":\\"value2\\"}}"  // passthrough field, push uses string in json format        "ApnsInfo": {            "ContentAvailable": 1 // APNs Transparent Push Feature        },        "AndroidInfo": {            ...    // For details, see AndroidInfo field description        }    }}
```

### APNs VoIP Push

```
{    // other parameters...    "OfflinePushInfo": {        "Title":"Offline Push Title",  // Fallback to ordinary Notification push Title when recipient's VoIP token is not reported        "Desc": "Offline Push Content",  // Fallback to ordinary Notification push Desc when recipient's VoIP token is not reported        "Ext": "{\\"entity\\":{\\"key1\\":\\"value1\\",\\"key2\\":\\"value2\\"}}"  // passthrough field, push uses string in json format        "ApnsInfo": {            "IsVoipPush": 1 // APNs VoIP Push        },        "AndroidInfo": {              ...   // For details, see AndroidInfo field description        }    }}
```

### APNs LiveActivity (Dynamic Island) Push

- Update LiveActivity.

```
{  // other parameters...  "OfflinePushInfo": {      "Title": "Offline Push Title",      "Desc": "Offline push content",      "Ext": "{\\"entity\\":{\\"k1\\":\\"v1\\",\\"k2\\":\\"v2\\"}}",  // passthrough field, push uses string in json format      "ApnsInfo": {           "LiveActivity": {               "LaId": "timpush",               "Event": "update", // Update LiveActivity push               "ContentState": {                   "k1": v1,                   "k2": v2,                   ...                }            }        },        "AndroidInfo": {            ... // For details, see AndroidInfo field description        }  }}
```

- End LiveActivity.

```
{  // other parameters...  "OfflinePushInfo": {      "Title": "Offline Push Title",      "Desc": "Offline push content",      "Ext": "{\\"entity\\":{\\"k1\\":\\"v1\\",\\"k2\\":\\"v2\\"}}",  // passthrough field, push uses string in json format      "ApnsInfo": {           "LiveActivity": {               "LaId": "timpush",               "Event": "end", // End LiveActivity push               "ContentState": {                   "k1": v1,                   "k2": v2,                   ...                },               "DismissalDate": 1739502750            }        },        "AndroidInfo": {            ... // For details, see AndroidInfo field description        }  }}
```

### Multi-language Push

```
{    // other parameters...    "OfflinePushInfo": {        "PushFlag": 0,        "Title":"Offline Push Title"        "Desc": "offline push content"        "MultiLanguageContent":[            {                "Language":"zh-hant",                "Title":"Offline Push Title"                "Desc":"offline push content"            },            {                "Language":"en",                "Title":"Offline Push Notification Title",                "Desc":"Offline Push Notification Desc"            }        ],        "Ext": "{\\"entity\\":{\\"key1\\":\\"value1\\",\\"key2\\":\\"value2\\"}}",  // passthrough field, push uses string in json format        "AndroidInfo": {             ... // For details, refer to the AndroidInfo field description        },        "ApnsInfo": {            ... // For details, refer to the ApnsInfo field description        }    }}
```

### Template-based Push

- Template preset variables (Chat message push only).

```
{    // Other parameters...    "OfflinePushInfo": {        "PushFlag": 0,        "Title":"Offline Push Title",        "Desc": "Offline Push Content",        "PushTemplateId":"1400000000-1" // If the template only contains preset variables, PushTemplateParam is not required    }}
```

- Template custom variables.

```
{    // Other parameters...    "OfflinePushInfo": {        "PushFlag": 0,        "Title":"Offline Push Title",        "Desc": "Offline Push Content",        "PushTemplateId":"1400000000-2",        "PushTemplateParam":{"UserName":"aaaa","ProductID":"bbbb"}    }}
```

### OfflinePushInfo Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| PushFlag | Integer | Optional | 0:Normal push flow. If device is online, online message is preferred; otherwise offline message is pushed.1: Device receives online messages only. |
| Title | String | Optional | Notification bar push title. |
| Desc | String | Optional | Notification bar push title. |
| MultiLanguageContent | Array | Optional | Multilingual push content. The backend matches the push content based on the terminal's system language. If no match is found, the default Title and Desc are used. The feature requires SDK version 8.5.6870 or higher. Example code please see [Multilingual Push](#f94f5e36-30aa-4bef-aebf-4bbe992c8b87). |
| Language | String | Optional | Title and Desc language flags. For details, please refer to [Multilingual Code Table](https://www.tencentcloud.com/document/product/1047/52154#code). |
| Ext | String | Optional | Offline Push Passthrough Content. Since domestic Android phone manufacturers have different requirements for push platforms, ensure this field is in JSON format, otherwise it may cause failed delivery for specific manufacturers' offline push. |
| AndroidInfo | Object | Optional | Android message push control parameters. For specific fields, see [AndroidInfo field description](#1078aae2-c4ef-417c-8f09-4c43edd36c19). |
| ApnsInfo | Object | Optional | APNs message push control parameters. For specific fields, see [ApnsInfo field description](#8bb656b5-6786-4b9d-b714-86b50189b820). |
| HarmonyInfo | Object | Optional | Harmony message push control parameters. For specific fields, see [HarmonyInfo field description](#42c5bd72-b2fc-48d5-835a-6a7663a8845d). |
| BadgeAddNum | Integer | Optional | Sets the increment value for the badge number, adding to the current badge count.APNs Push: Value range: [1-99]. If both BadgeAddNum and BadgeSetNum are present, BadgeSetNum takes precedence. If neither is set, refer to ApnsInfo.BadgeMode.Huawei/Honor/Harmony Push: Value range: [1-99]. If both BadgeAddNum and BadgeSetNum are present, BadgeSetNum takes precedence. If neither is set, the badge number increments by 1.For other push vendors: This field has no effect. |
| BadgeSetNum | Integer | Optional | Set badge number.For APNs push, the value range is [0~999].For Huawei/Honor/HarmonyOS push, the value range is [0~99].For other push vendors, this field will not take effect.In other cases, refer to BadgeAddNum for badge accumulation. |
| PushTemplateId | String | Optional | Push template ID. You must create the template in [Push Settings](https://console.trtc.io/chat/push-plugin-push-setting) in advance. Format: `1400000000-1`. If omitted, the system default push style is used.**Note:** If template contains preset variables, it is only supported in Chat scenarios; pure Push scenarios (for example [single push](https://www.tencentcloud.com/document/product/1047/67553)) will return an error. |
| PushTemplateParam | JSON Object | Optional | Template fill parameters used to fill custom variables. Example: If template title is `{{UserName}} Order Notification`, pass `{"UserName":"aaaa"}` here.**Note:** The following variables are auto-filled by system and should not be provided in `PushTemplateParam`:`timTitle`: replaced by original push title.`timDesc`: replaced by original push content.`timSenderNick`: replaced by sender nickname.`timGroupName`: replaced by group name for group chat, empty string for C2C chat. |

#### AndroidInfo Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| Sound | String | Optional | Android system notification ringtone filename, without suffix. For example, setting it to "shake" refers to the local file "/res/raw/shake.xxx" in the corresponding application. |
| PushStyle | Integer | Optional | Android notification bar style. "0" represents the default style, "1" represents the large text style. If left blank, it defaults to 0. Only applicable to Huawei, Honor, and OPPO. |
| XiaoMiChannelID | String | Optional | Mi Push notification category (Channel) adaptation fields for MIUI 10 or higher.When this field is not empty, it overwrites the ChannelID value in the console push certificate configuration. |
| OPPOChannelID | String | Optional | OPPO Push notification channel adaptation fields for Android 8.0 or higher.When this field is not empty, it overwrites the ChannelID value in the console push certificate configuration. |
| OPPOCategory | String | Optional | OPPO push message categorization, used to identify message type. For details, see [category description](https://open.oppomobile.com/new/developmentDoc/info?id=13189).When this field is not empty, it overwrites the category value in the console push certificate configuration. |
| OPPOPrivateMsgTemplateId | String | Optional | OPPO push private message template id, must carry when delivering the corresponding private message template. If OPPOCategory is set to content and marketing, this field is invalid. For details, see ["OPUSH Private Message Template Verification"](https://open.oppomobile.com/documentation/page/info?id=12391). |
| OPPOPrivateTitleParameters | JSON Object | Optional | OPPO push private message template title parameters. Title template example is: welcome to ${city}$, ${city}$ welcomes you. The parameter content is: `{"city":"Beijing"}` |
| OPPOPrivateContentParameters | JSON Object | Optional | OPPO push private message template content parameters. Content template example is: `{"userName":"Tom", "city":"Shenzhen city"}` |
| OPPONotifyLevel | Integer | Optional | OPPO push notification bar message reminder level value definition. For details, see [notify_level description](https://open.oppomobile.com/new/developmentDoc/info?id=11236).1: Notification bar2: Notification bar + lock screen16: Notification bar + lock screen + banner + vibration + ringtoneWhen using OPPONotifyLevel, OPPOCategory is required. |
| VIVOClassification | Integer | Optional | vivo push message categorization: "0" represents operational messages, "1" represents system messages. Default is 1 if left blank. (vivo push service optimized message classification rules on April 3, 2023. Recommended to use AndroidInfo. VIVOCategory to set message type.) |
| VIVOCategory | String | Optional | vivo push message categorization, used to identify message type. For details, see [category description](https://dev.vivo.com.cn/documentCenter/doc/359).When this field is not empty, it overwrites the category value in the console push certificate configuration. |
| VIVONotifyType | String | Optional | Notification Type 1: None, 2: Ring, 3: Vibrate, 4: Ring and Vibrate. Default setting is 4, see [notifyType](https://dev.vivo.com.cn/documentCenter/doc/362). |
| HuaWeiImportance | String | Optional | Huawei push messaging reminder level, value is LOW, NORMAL. |
| HuaWeiCategory | String | Optional | Huawei push message classification, used to identify message type. For details, see [category description](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-References/https-send-api-0000001050986197#section13271045101216).When this field is not empty, it overwrites the category value in the console push certificate configuration. |
| HuaWeiImage | String | Optional | Small icon URL for Huawei push notifications in the notification bar. The URL must use HTTPS protocol. Example: `https://example.com/image.png`. The image file must be less than 512KB, with a recommended size of 40dp x 40dp and a corner radius of 8dp. Images exceeding the recommended size may be compressed or not fully displayed. Recommended image formats are JPG, JPEG, or PNG. |
| HonorImage | String | Optional | Icon URL for Honor push notifications in the notification bar. The URL must use HTTPS protocol. Example: `https://example.com/image.png`. The icon must be less than 512KB, with a recommended size of 40dp x 40dp and a corner radius of 8dp. Icons exceeding the recommended size may be compressed or not fully displayed. |
| HuaWeiChannelID | String | Optional | Huawei Push notification channel field for EMUI 10.0 or higher.When this field is not empty, it overwrites the ChannelID value in the console push certificate configuration. |
| HonorImportance | String | Optional | Categorization for Honor push messages, with values LOW or NORMAL. For details, refer to [Honor Message Categorization](https://developer.honor.com/cn/docs/11002/guides/notification-class). |
| GoogleImage | String | Optional | Icon URL for Google push notifications in the notification bar. The image resource must not exceed 1MB, supporting JPG, JPEG, or PNG formats. Example:  `https://example.com/image.png`. |
| GooglePriority | String | Optional | Google Push Notification Message Priority, see [priority](https://firebase.google.com/docs/cloud-messaging/android/message-priority).normal: When the device is in the foreground, messages are delivered immediately. When the device is in the background or Doze mode, messages are delivered in batches with a delay.high: Regardless of the device's state (background/Doze/foreground), messages wake up the device and are delivered immediately. |
| GoogleChannelID | String | Optional | Google Push notification channel fields for Android 8.0 or higher. |
| MeiZuNoticeMsgType | Integer | Optional | Categorization for Meizu push messages. "0" represents an official message, "1" represents a private message. For details, see [Meizu Message Classification Description](https://open-res.flyme.cn/fileserver/upload/file/202504/13dc49a671b643438431b386e071f59e.pdf).If this field is not empty, it overrides the message categorization in the console's Meizu Push certificate configuration. |

#### ApnsInfo Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| BadgeMode | Integer | Optional | 0 means counting is required, 1 means this message does not count, and the upper right corner icon number does not increase.**Note:**The default value is 0 in Chat scenarios and 1 in non-Chat scenarios (such as calling the [single push](https://www.tencentcloud.com/document/product/1047/67553) API). |
| Title | String | Optional | This field is used to specify the title of APNs push. If filled, it will overwrite the top-level Title. |
| SubTitle | String | Optional | This field is used to specify the subtitle of APNs push. |
| Image | String | Optional | This field is used to specify the image address carried by APNs. When the client receives this field, the image can be displayed in the popup by downloading the image resource. |
| MutableContent | Integer | Optional | Set to 1 to enable push extension for iOS 10+. Default is 0. |
| Sound | String | Optional | iOS system notification ringtone filename, with suffix. Custom ringtone length cannot exceed 30s. The audio file must be added to the Xcode project first. Example value: `shake.mp3`. |
| InterruptionLevel | String | Optional | The notification level for iOS 15+ push notifications can only be one of active, critical, passive, or time-sensitive. For details, please refer to: [APNs InterruptionLevel description](https://developer.apple.com/documentation/usernotifications/unnotificationinterruptionlevel). |
| ContentAvailable | Integer | Optional | 1 indicates a silent push for iOS, with no popup in the notification banner. Apple recommends sending no more than 3 silent messages per hour. For details, please refer to: [APNs Background Notification](https://developer.apple.com/documentation/usernotifications/pushing-background-updates-to-your-app). |
| IsVoipPush | Integer | Optional | 1 indicates a VoIP push for iOS. If the recipient does not provide a VoIP token, it will be automatically downgraded to a regular APNs notification push. |
| LiveActivity | Object | Optional | LiveActivity push control parameters. For specific fields, see [LiveActivity field description](#f4199d1f-0337-4c0b-bdd2-aed25d59bdab). |

##### Harmony Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| Title | String | Optional | This field is used to identify the title of Harmony push. If filled, it will overwrite the top-level Title. |
| Category | String | Optional | HarmonyOS push message categorization, used to identify message type. For details, see [category description](https://developer.huawei.com/consumer/cn/doc/harmonyos-references-V5/push-scenariozed-api-request-param-V5#section17371529101117).When not empty, this field will overwrite the category value in the console Push Certificate configuration. |
| Image | String | Optional | Notification Large Icon URL. The URL must use the HTTPS protocol. |
| Sound | String | Optional | Custom message notification sound. The ringtone file set here must be placed in the /resources/rawfile path of the application. For example, setting it to "alert.mp3" corresponds to the local /resources/rawfile/alert.mp3 file in the application. Supported file formats include MP3, WAV, MPEG. If not set, the default system ringtone is used.When the request does not carry the SoundDuration field, it is recommended that the ringtone duration cannot exceed 30 seconds. If it exceeds 30 seconds, truncate it. When the request carries the SoundDuration field, for details, see the [SoundDuration](#SoundDuration) field description.**Note:** Wearable, TV, PC/2in1 do not support customizable ringtone |
| SoundDuration | Integer | Optional | Custom message notification ringtone duration. Need to be used with the Sound field, effective only when the request carries both the Sound field and the SoundDuration field. Support numbers only, in seconds, in the range of [1,60].The custom message notification ringtone passed in the Sound field will play until the SoundDuration field value is reached. If the duration of the custom message notification ringtone is insufficient, it will loop playback and stop when the SoundDuration field value is reached. |

##### LiveActivity Field Description

| Field | Type | Attribute | Description |
| --- | --- | --- | --- |
| LaId | String | Required | The real-time activity identifier that needs to be pushed, corresponding to the client activityID, with a length not exceeding 64 bytes. For details, refer to [implementing LiveActivity (Dynamic Island) feature](https://www.tencentcloud.com/document/product/1047/69235). |
| Event | String | Required | For update, enter `update`; for end, enter `end`. |
| ContentState | Object | Required | A custom key-value object. Must match the client SDK value.Corresponding to the official APNs document: [Starting and updating Live Activities with ActivityKit push notifications \| Apple Developer Documentation](https://developer.apple.com/documentation/activitykit/updating-and-ending-your-live-activity-with-activitykit-push-notifications) |
| DismissalDate | Integer | Optional. | When the Event is "end", the Unix time shown for the real-time activity completion on the lock screen. If left blank, it defaults to the current time, and the lock screen will end soon. |

> **Note:**Since APNs push restrictions limit packet size to 4K, exclude other control fields and keep the sum of Desc and Ext fields under 3K.If offline push is needed, strongly recommend the sender to specify OfflinePushInfo.Title and OfflinePushInfo.Desc. For C2C/group messages, if OfflinePushInfo.Title and OfflinePushInfo.Desc are not filled in, the fallback logic will attempt to convert and retrieve Title and Desc from MsgBody for offline push.

### Notification Title and Content Length Limits

| Push Platform | Title Length Limit | Content Length Limit | Over-Length Handling Rule |
| --- | --- | --- | --- |
| Huawei | 60 | 600 | When the title or content exceeds the length limit of the corresponding channel, **it will be automatically truncated to the limit length with ... (ellipsis) appended at the end** (occupying 3 units). That is, the actual retained content is limit length â 3 units. |
| HONOR | 50 | 400 |  |
| Mi | 50 | 128 |  |
| OPPO | 50 | 50 (128 for long text push, i.e., when AndroidInfo.PushStyle = 1) |  |
| vivo | 40 | 100 |  |
| Meizu | 32 | 100 |  |

> **Note****ï¼**The length limits listed above are measured in UTF-16 code units.Common characters (Chinese, English, digits, common punctuation): each character counts as 1 unit.Certain special characters (such as most emoji like ðð, and some rare CJK characters): each character counts as 2 units.Composite emoji (such as ðð½, ð¨âð©âð§, etc.): composed of multiple characters, where the total unit count is the sum of each individual character's units, and may well exceed 2 units.


---
*Source: [https://trtc.io/document/77715](https://trtc.io/document/77715)*
