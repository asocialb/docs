# Type Definition

### Enumeration Definition

#### TUIRoomDefine

| Type | Description |
| --- | --- |
| [RoomType](/document/product/647/54866#RoomType) | Room Type |
| [SpeechMode](/document/product/647/54866#SpeechMode) | Room Mode |
| [MediaDevice](/document/product/647/54866#MediaDevice) | Room Media Device Type |
| [Role](/document/product/647/54866#Role) | Room Role Type |
| [VideoQuality](/document/product/647/54866#VideoQuality) | Video Quality |
| [AudioQuality](/document/product/647/54866#AudioQuality) | Audio Quality |
| [VideoStreamType](/document/product/647/54866#VideoStreamType) | Video Stream Type |
| [ChangeReason](/document/product/647/54866#ChangeReason) | Change Reason (User audio and video status change operation reason: self-modification or modified by room owner/administrator) |
| [RequestAction](/document/product/647/54866#RequestAction) | Request Type |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [NetworkQuality](/document/product/647/54866#NetworkQuality) | Network Quality |

### Common Structure

#### TUIRoomDefine

| Type | Description |
| --- | --- |
| [RoomInfo](/document/product/647/54866#RoomInfo) | Room data |
| [LoginUserInfo](/document/product/647/54866#RoomInfo) | User Login Information |
| [UserInfo](/document/product/647/54866#UserInfo) | Room User Information |
| [SeatInfo](/document/product/647/54866#SeatInfo) | Room Seat Information |
| [SeatLockParams](/document/product/647/54866#SeatLockParams) | Lock Seat Operation Parameters |
| [UserVoiceVolume](/document/product/647/54866#UserVoiceVolume) | Room User Volume |
| [Request](/document/product/647/54866#Request) | Signaling Request |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [NetworkInfo](/document/product/647/54866#NetworkInfo) | Network Quality Information |
| [Message](/document/product/647/54866#Message) | Message |

### RoomType

Room Type

| Enumeration | Value | Description |
| --- | --- | --- |
| CONFERENCE | 1 | Conference Type Room, suitable for conference and education scenarios, this room can enable free speech, apply for speech, go live and other modes. |
| LIVE_ROOM | 2 | Live Type Room, suitable for live broadcast scenarios, this room can enable free speech, mic control mode, and the seats in this room are numbered. |

### SpeechMode

Mic Control Mode

| Enumeration | Value | Description |
| --- | --- | --- |
| FREE_TO_SPEAK | 1 | Free speech mode. |
| APPLY_TO_SPEAK | 2 | Apply to speak mode. (Only effective in conference type room) |
| SPEAK_AFTER_TAKING_SEAT | 3 | Go Live mode. |

### MediaDevice

Room Media Device Type

| Enumeration | Value | Description |
| --- | --- | --- |
| MICROPHONE | 1 | Mic |
| CAMERA | 2 | Camera |
| SCREEN_SHARING | 3 | Screen Sharing |

### Role

Room Role Types

| Enumeration | Value | Description |
| --- | --- | --- |
| ROOM_OWNER | 0 | Room Owner, generally refers to the creator of the room, the highest authority holder in the room |
| MANAGER | 1 | Room Administrator |
| GENERAL_USER | 2 | General Member in the room |

### VideoQuality

Video Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| Q_360P | 1 | Low-quality 360P |
| Q_540P | 2 | Standard Definition 540P |
| Q_720P | 3 | High Definition 720P |
| Q_1080P | 4 | Ultra-clear 1080P |

### AudioQuality

Audio Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| SPEECH | 0 | Speech Mode |
| DEFAULT | 1 | Default Mode |
| MUSIC | 2 | Music Mode |

### VideoStreamType

Video Stream Type

| Enumeration | Value | Description |
| --- | --- | --- |
| CAMERA_STREAM | 0 | High-quality Camera Video Stream |
| SCREEN_STREAM | 1 | Screen Sharing Video Stream |
| CAMERA_STREAM_LOW | 2 | Low-quality Camera Video Stream |

### ChangeReason

Change Reason (User audio and video status change operation reason: self-modification or modification by room owner/administrator)

| Enumeration | Value | Description |
| --- | --- | --- |
| BY_SELF | 0 | Self-operation |
| BY_ADMIN | 1 | Room Owner or Administrator Operation |

### RequestAction

Request Type

| Enumeration | Value | Description |
| --- | --- | --- |
| INVALID_ACTION | 0 | Invalid Request |
| REQUEST_TO_OPEN_REMOTE_CAMERA | 1 | Request Remote User to Open Camera |
| REQUEST_TO_OPEN_REMOTE_MICROPHONE | 2 | Request Remote User to Open Microphone |
| REQUEST_TO_CONNECT_OTHER_ROOM | 3 | Request to Connect to Other Room |
| REQUEST_TO_TAKE_SEAT | 4 | Request to Go Live |
| REQUEST_REMOTE_USER_ON_SEAT | 5 | Request Remote User to Go Live |
| REQUEST_APPLY_TO_ADMIN_TO_OPEN_LOCAL_CAMERA | 6 | Request to Admin to Open Local Camera |
| REQUEST_APPLY_TO_ADMIN_TO_OPEN_LOCAL_MICROPHONE | 7 | Request to Admin to Open Local Microphone |

### NetworkQuality

Network Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| UNKNOWN | 0 | Undefined |
| EXCELLENT | 1 | Current Network is Excellent |
| GOOD | 2 | Current Network is Good |
| POOR | 3 | Current Network is Average |
| BAD | 4 | Current Network is Poor |
| VERY_BAD | 5 | Current Network is Very Poor |
| DOWN | 6 | Current Network Does Not Meet TRTC's Minimum Requirements |

### RoomInfo

Room Information

| Field | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| ownerId | String | Host ID, default is the room creator (read-only) |
| roomType | [RoomType](/document/product/647/54866#RoomType) | Room Type |
| name | String | Room Name, default is the room ID |
| speechMode | [SpeechMode](/document/product/647/54866#SpeechMode) | Mic Control Mode |
| isCameraDisableForAllUser | boolean | Whether to Disable Opening Camera (optional when creating a room), default value: false |
| isMicrophoneDisableForAllUser | boolean | Whether to Disable Opening Microphone (optional when creating a room), default value: false |
| isMessageDisableForAllUser | boolean | Whether to Disable Sending Messages (optional when creating a room), default value: false |
| maxSeatCount | int | Maximum Number of Mic Seats (only supported when entering the room and creating the room) |
| enableCDNStreaming | boolean | Whether to Enable CDN Live Streaming (optional when creating a room, for live streaming rooms), default value: false |
| cdnStreamDomain | String | Live Streaming Push Domain (optional when creating a room, for live streaming rooms), default value: empty |
| createTime | long | Room Creation Time (read-only) |
| memberCount | int | Number of Members in the Room (read-only) |

### LoginUserInfo

User Login Information

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| userName | String | User Name |
| avatarUrl | String | User Avatar URL |

### UserInfo

User Information in the Room

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| userName | String | User Name |
| avatarUrl | String | User Avatar URL |
| userRole | [Role](/document/product/647/54866#Role) | User Role Type |
| hasAudioStream | boolean | Whether There is Audio Stream, default value: false |
| hasVideoStream | boolean | Whether There is Video Stream, default value: false |
| hasScreenStream | boolean | Whether There is Screen Sharing Stream, default value: false |

### SeatInfo

Seat Information in the Room

| Field | Type | Description |
| --- | --- | --- |
| index | int | Mic Seat Number |
| userId | String | User ID |
| isLocked | boolean | Whether the Mic Seat is Locked, default false |
| isVideoLocked | boolean | Whether the Mic Seat is Prohibited from Opening Camera, default false |
| isAudioLocked | boolean | Whether the Mic Seat is Prohibited from Opening Microphone, default false |

### SeatLockParams

Lock Seat Operation Parameters

| Field | Type | Description |
| --- | --- | --- |
| lockSeat | boolean | Lock Mic Seat, default false |
| lockVideo | boolean | Lock Mic Seat Camera, default false |
| lockAudio | boolean | Lock Mic Seat Microphone, default false |

### UserVoiceVolume

User Voice Volume in the Room

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| volume | int | Volume Size, Value range 0 - 100 |

### Request

Signaling Request

| Field | Type | Description |
| --- | --- | --- |
| requestId | String | Request ID |
| requestAction | [RequestAction](/document/product/647/54866#RequestAction) | Request Type |
| userId | String | User ID |
| content | String | Signaling Content |
| timestamp | int | Timestamp |

### NetworkInfo

Network Quality Information

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| quality | [NetworkQuality](/document/product/647/54866#NetworkQuality) | Network Quality |
| upLoss | int | Upstream Packet Loss Rate |
| downLoss | int | Downstream Packet Loss Rate |
| delay | int | Network Delay |

### Message

Message

| Field | Type | Description |
| --- | --- | --- |
| messageId | String | Message ID |
| message | String | Message Text |
| timestamp | long | Message Time |
| userId | String | Message Sender |
| userName | String | Message Sender Nickname |
| avatarUrl | String | Message Sender Avatar |


---
*Source: [https://trtc.io/document/54866](https://trtc.io/document/54866)*
