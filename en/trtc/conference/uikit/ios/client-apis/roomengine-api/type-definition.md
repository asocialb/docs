# Type Definition

### Enumeration Definition

#### TUIRoomDefine

| Type | Description |
| --- | --- |
| [TUIRoomType](/document/product/647/54859#RoomType) | Room Type |
| [TUISpeechMode](/document/product/647/54859#55e7dd70-efb6-4d47-a31e-d64f290ab6c1) | Mic Control Mode |
| [TUIMediaDevice](/document/product/647/54859#45f8cc27-8bbe-4ed5-bb40-511a08e27477) | Room Media Device Type |
| [TUIRole](/document/product/647/54859#Role) | Room Role Type |
| [TUIVideoQuality](/document/product/647/54859#74d0aadf-0c54-4a05-9e30-f40b427f1402) | Video Quality |
| [TUIAudioQuality](/document/product/647/54859#c079e8f9-62be-4ea2-b740-20658dcec529) | Audio Quality |
| [TUIVideoStreamType](/document/product/647/54859#VideoStreamType) | Video Stream Type |
| [TUIChangeReason](/document/product/647/54859#ChangeReason) | Change Reason (User audio and video status change operation reason: self-modification or modified by room owner/administrator) |
| [TUICaptureSourceType](/document/product/647/54859#02abd5f6-ef70-4636-9ff5-fd331baac4f5) | Screen Sharing Capture Source Type |
| [TUIRequestAction](/document/product/647/54859#RequestAction) | Request Type |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [TUINetworkQuality](/document/product/647/54859#NetworkQuality) | Network Quality |

### Common Structure

#### TUIRoomDefine

| Type | Description |
| --- | --- |
| [TUIRoomInfo](/document/product/647/54859#RoomInfo) | Room data |
| [TUILoginUserInfo](/document/product/647/54859#83093ad1-7671-4f9f-aada-3c74d5006c75) | User Login Information |
| [TUIUserInfo](/document/product/647/54859#UserInfo) | Room User Information |
| [TUISeatInfo](/document/product/647/54859#SeatInfo) | Room Seat Information |
| [TUISeatLockParams](/document/product/647/54859#080212f8-d6ce-4430-b745-2fdd5ef8c330) | Lock Seat Operation Parameters |
| [TUIUserVoiceVolume](/document/product/647/54859#UserVoiceVolume) | Room User Volume |
| [TUIRequest](/document/product/647/54859#Request) | Signaling Request |
| [TUIShareTarget](/document/product/647/54859#200329d6-b424-4bec-b9a1-7e6b7f8ea580) | Screen Sharing Capture Source Information |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [TUINetworkInfo](/document/product/647/54859#NetworkInfo) | Network Quality Information |
| [TUIMessage](/document/product/647/54859#Message) | Message |

### TUIRoomType

Room Type

| Enumeration | Value | Description |
| --- | --- | --- |
| TUIRoomTypeConference | 1 | Conference Type Room, suitable for conference and education scenarios, this room can enable free speech, apply for speech, go live and other modes. |
| TUIRoomTypeLivingRoom | 2 | Live Type Room, suitable for live broadcast scenarios, this room can enable free speech, mic control mode, and the seats in this room are numbered. |

### TUISpeechMode

Mic Control Mode

| Enumeration | Value | Description |
| --- | --- | --- |
| TUISpeechModeFreeToSpeak | 1 | Free speech mode. |
| TUISpeechModeApplyToSpeak | 2 | Apply to speak mode. (Only effective in conference type room) |
| TUISpeechModeApplySpeakAfterTakingSeat | 3 | Go Live mode. |

### TUIMediaDevice

Room Media Device Type

| Enumeration | Value | Description |
| --- | --- | --- |
| TUIMediaDeviceMicrophone | 1 | Mic |
| TUIMediaDeviceCamera | 2 | Camera |
| TUIMediaDeviceApplyScreenSharing | 3 | Screen Sharing |

### TUIRole

Room Role Types

| Enumeration | Value | Description |
| --- | --- | --- |
| TUIRoleRoomOwner | 0 | Room Owner, generally refers to the creator of the room, the highest authority holder in the room |
| TUIRoleAdministrator | 1 | Room Administrator |
| TUIRoleGeneralUser | 2 | General Member in the room |

### TUIVideoQuality

Video Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| TUIVideoQuality360P | 1 | Low-quality 360P |
| TUIVideoQuality540P | 2 | Standard Definition 540P |
| TUIVideoQuality720P | 3 | High Definition 720P |
| TUIVideoQuality1080P | 4 | Ultra-clear 1080P |

### TUIAudioQuality

Audio Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| TUIAudioQualitySpeech | 0 | Speech Mode |
| TUIAudioQualityDefault | 1 | Default Mode |
| TUIAudioQualityMusic | 2 | Music Mode |

### TUIVideoStreamType

Video Stream Type

| Enumeration | Value | Description |
| --- | --- | --- |
| TUIVideoStreamTypeCameraStream | 0 | High-quality Camera Video Stream |
| TUIVideoStreamTypeScreenStream | 1 | Screen Sharing Video Stream |
| TUIVideoStreamTypeCameraStreamLow | 2 | Low-quality Camera Video Stream |

### TUIChangeReason

Change Reason (User audio and video status change operation reason: self-modification or modification by room owner/administrator)

| Enumeration | Value | Description |
| --- | --- | --- |
| TUIChangeReasonBySelf | 0 | Self-operation |
| TUIChangeReasonByAdmin | 1 | Room Owner or Administrator Operation |

### TUICaptureSourceType

Screen Sharing Capture Source Type

| Enumeration | Value | Description |
| --- | --- | --- |
| TUICaptureSourceTypeUnknown | -1 | Undefined |
| TUICaptureSourceTypeWindow | 0 | Window |
| TUICaptureSourceTypeScreen | 1 | Screen |

### TUIRequestAction

Request Type

| Enumeration | Value | Description |
| --- | --- | --- |
| TUIRequestActionInvalidAction | 0 | Invalid Request |
| TUIRequestActionOpenRemoteCamera | 1 | Request Remote User to Open Camera |
| TUIRequestActionOpenRemoteMicrophone | 2 | Request Remote User to Open Microphone |
| TUIRequestActionConnectOtherRoom | 3 | Request to Connect to Other Room |
| TUIRequestActionTakeSeat | 4 | Request to Go Live |
| TUIRequestActionRemoteUserOnSeat | 5 | Request Remote User to Go Live |
| TUIRequestActionApplyToAdminToOpenLocalCamera | 6 | Request to Admin to Open Local Camera |
| TUIRequestActionApplyToAdminToOpenLocalMicrophone | 7 | Request to Admin to Open Local Microphone |

### TUINetworkQuality

Network Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| TUINetworkQualityUnknown | 0 | Undefined |
| TUINetworkQualityExcellent | 1 | Current Network is Excellent |
| TUINetworkQualityGood | 2 | Current Network is Good |
| TUINetworkQualityPoor | 3 | Current Network is Average |
| TUINetworkQualityBad | 4 | Current Network is Poor |
| TUINetworkQualityVeryBad | 5 | Current Network is Very Poor |
| TUINetworkQualityDown | 6 | Current Network Does Not Meet TRTC's Minimum Requirements |

### TUIRoomInfo

Room Information

| Field | Type | Description |
| --- | --- | --- |
| roomId | NSString * | Room ID |
| roomType | [TUIRoomType](/document/product/647/54859#RoomType) | Room Type |
| ownerId | NSString * | Host ID, default is the room creator (read-only) |
| name | NSString * | Room Name, default is the room ID |
| speechMode | [TUISpeechMode](/document/product/647/54859#55e7dd70-efb6-4d47-a31e-d64f290ab6c1) | Mic Control Mode |
| createTime | NSUInteger | Room Creation Time (read-only) |
| memberCount | NSInteger | Number of Members in the Room (read-only) |
| maxSeatCount | NSUInteger | Maximum Number of Mic Seats (only supported when entering the room and creating the room) |
| isCameraDisableForAllUser | BOOL | Whether to Disable Opening Camera (optional when creating a room), default value: false |
| isMicrophoneDisableForAllUser | BOOL | Whether to Disable Opening Microphone (optional when creating a room), default value: false |
| isMessageDisableForAllUser | BOOL | Whether to Disable Sending Messages (optional when creating a room), default value: false |
| enableCDNStreaming | BOOL | Whether to Enable CDN Live Streaming (optional when creating a room, for live streaming rooms), default value: false |
| cdnStreamDomain | NSString* | Live Streaming Push Domain (optional when creating a room, for live streaming rooms), default value: empty |

### TUILoginUserInfo

User Login Information

| Field | Type | Meaning |
| --- | --- | --- |
| userId | NSString * | User ID |
| userName | NSString * | User Name |
| avatarUrl | NSString * | User Avatar URL |

### TUIUserInfo

User Information in the Room

| Field | Type | Description |
| --- | --- | --- |
| userId | NSString * | User ID |
| userName | NSString * | User Name |
| avatarUrl | NSString * | User Avatar URL |
| userRole | [TUIRole](/document/product/647/54859#Role) | User Role Type |
| hasAudioStream | BOOL | Whether There is Audio Stream, default value: false |
| hasVideoStream | BOOL | Whether There is Video Stream, default value: false |
| hasScreenStream | BOOL | Whether There is Screen Sharing Stream, default value: false |

### TUISeatInfo

Seat Information in the Room

| Field | Type | Description |
| --- | --- | --- |
| index | NSInteger | Mic Seat Number |
| userId | NSString * | User ID |
| isLocked | BOOL | Whether the Mic Seat is Locked, default false |
| isVideoLocked | BOOL | Whether the Mic Seat is Prohibited from Opening Camera, default false |
| isAudioLocked | BOOL | Whether the Mic Seat is Prohibited from Opening Microphone, default false |

### TUISeatLockParams

Lock Seat Operation Parameters

| Field | Type | Meaning |
| --- | --- | --- |
| lockSeat | BOOL | Lock Mic Seat, default false |
| lockVideo | BOOL | Lock Mic Seat Camera, default false |
| lockAudio | BOOL | Lock Mic Seat Microphone, default false |

### TUIUserVoiceVolume

User Voice Volume in the Room

| Field | Type | Description |
| --- | --- | --- |
| userId | NSString * | User ID |
| volume | NSUInteger | Volume Size, Value range 0 - 100 |

### TUIRequest

Signaling Request

| Field | Type | Description |
| --- | --- | --- |
| requestId | NSString * | Request ID |
| requestAction | [TUIRequestAction](/document/product/647/54859#RequestAction) | Request Type |
| userId | NSString * | User ID |
| content | NSString * | Signaling Content |
| timestamp | NSUInteger | Timestamp |

### TUIShareTarget

Screen Sharing Capture Source Information

| Field | Type | Description |
| --- | --- | --- |
| targetId | NSString * | Capturing Source ID, for windows, this field represents the window ID; for screens, this field represents the display ID |
| sourceType | [TUICaptureSourceType](/document/product/647/54859#02abd5f6-ef70-4636-9ff5-fd331baac4f5) | Capturing Source Type |
| sourceName | NSString * | Capturing Source Name |
| thumbnailImage | TUIImage * | Thumbnail |
| iconImage | TUIImage * | Icon |
| extInfo | NSDictionary * | Window's Extended Information |

### TUINetworkInfo

Network Quality Information

| Field | Type | Description |
| --- | --- | --- |
| userId | NSString * | User ID |
| quality | [TUINetworkQuality](/document/product/647/54859#NetworkQuality) | Network Quality |
| upLoss | uint32_t | Upstream Packet Loss Rate |
| downLoss | uint32_t | Downstream Packet Loss Rate |
| delay | uint32_t | Network Delay |

### TUIMessage

Message

| Field | Type | Description |
| --- | --- | --- |
| messageId | NSString * | Message ID |
| message | NSString * | Message Text |
| timestamp | uint64_t | Message Time |
| userId | NSString * | Message Sender |
| userName | NSString * | Message Sender Nickname |
| avatarUrl | NSString * | Message Sender Avatar |


---
*Source: [https://trtc.io/document/54859](https://trtc.io/document/54859)*
