# TUIRoomEngine Defines

This document introduces the type definitions for the TUIRoomEngine on Electron.

## Enumerations

### TUIRole

User roles, TUIRoomEngine provides three types of user roles: host, administrator, and general user.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kRoomOwner | number | Room owner role |
| kAdministrator | number | Room administrator role |
| kGeneralUser | number | Regular user role |

### TUIVideoQuality

Video resolution.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kVideoQuality_360p | number | Low definition, resolution of 640 * 360 |
| kVideoQuality_540p | number | Standard definition, resolution of 960 * 540 |
| kVideoQuality_720p | number | High definition, resolution of 1280 * 720 |
| kVideoQuality_1080p | number | Ultra-high definition, resolution of 1920 * 1080 |

### TUIResolutionMode

Video resolution mode.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kResolutionMode_Landscape | number | Landscape mode |
| kResolutionMode_Portrait | number | Portrait mode |

### TUIAudioQuality

Audio resolution.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kAudioProfileSpeech | number | Speech mode |
| kAudioProfileDefault | number | Standard mode (default mode) |
| kAudioProfileMusic | number | Music mode |

### TUIVideoStreamType

Video stream type.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kCameraStream | number | High quality camera video stream |
| kScreenStream | number | Scree/Window sharing video stream |
| kCameraStreamLow | number | Low quality camera video stream |

### TUINetworkQuality

Network quality status.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kQualityUnknown | number | unknown network condition |
| kQualityExcellent | number | Excellent network condition |
| kQualityGood | number | Good network condition |
| kQualityPoor | number | Average network condition |
| kQualityBad | number | Poor network condition |
| kQualityVeryBad | number | Very poor network condition |
| kQualityDown | number | etwork connection has been disconnected |

### TUIRoomType

Room type.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kConference | number | Conference room: best for meeting and education and so on. |
| kLive | number | Live room: best for online live streaming |

### TUISeatMode

Seat mode.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kFreeToTake | number | Free-to-take mode, where audience members can freely become speakers without applying. |
| kApplyToTake | number | Apply-to-take mode, where audience members need the approval of the host or administrator to become speakers. |

### TUICaptureSourceType

Screen sharing type.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kWindow | number | The sharing target is a specific Windows or Mac window |
| kScreen | number | The sharing target is the entire Windows desktop or Mac desktop screen |

### TUIChangeReason

Change reason (reason for user's audio and video status change: modified by oneself or by the host/administrator).

| Enumeration item | Type | Description |
| --- | --- | --- |
| kChangedBySelf | number | Self-operation |
| kChangedByAdmin | number | Operation by room owner or administrator |

### TUIMediaDeviceState

Media device status.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kMediaDeviceStateAdd | number | New device added |
| kMediaDeviceStateRemove | number | Device removed |
| kMediaDeviceStateActive | number | Device activated |
| kMediaDefaultDeviceChanged | number | System default device changed |

### TUICameraCaptureMode

Camera capture mode

| Enumeration item | Type | Description |
| --- | --- | --- |
| kCameraResolutionStrategyAuto | number | Automatically adjust capture parameters. The SDK selects appropriate camera output parameters based on the actual performance of the capture device and network conditions, maintaining a balance between device performance and video preview quality. |
| kCameraResolutionStrategyPerformance | number | Priority on device performance. The SDK selects the closest camera output parameters based on the user's settings for encoder resolution and frame rate, thereby ensuring device performance. |
| kCameraResolutionStrategyHighQuality | number | Priority on video preview quality. The SDK selects higher camera output parameters to improve the quality of the preview video. In this case, more CPU and memory will be consumed for video preprocessing. |
| kCameraCaptureManual | number | Allows users to set the local camera capture video width and height. |

### TUIRequestAction

Request operation type.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kInvalidAction | number | Invalid operation |
| kRequestToOpenRemoteCamera | number | Request to open remote camera |
| kRequestToOpenRemoteMicrophone | number | Request to open remote microphone |
| kRequestToConnectOtherRoom | number | Request for a remote room mic connection |
| kRequestToTakeSeat | number | Request to speak |
| kRequestRemoteUserOnSeat | number | Request for remote user to speak |

### TUIRequestCallbackType

Request callback type.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kRequestAccepted | number | Request was accepted by receiver |
| kRequestRejected | number | Request has rejected by receiver |
| kRequestCancelled | number | Request has been canceled by sender |
| kRequestTimeout | number | Request timed out |
| kRequestError | number | Request error |

### TUIKickedOutOfRoomReason

Kick out of room reason.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kKickedByAdmin | number | Removed by room owner or administrator |
| kKickedByLoggedOnOtherDevice | number | Removed when the same userId user enters the same room on another device |
| kKickedByServer | number | Removed by the server |

### TUIConferenceStatus

Conference status.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kConferenceStatusNone | number | Unknown status |
| kConferenceStatusNotStarted | number | The conference has not started |
| kConferenceStatusRunning | number | The conference is in progress |

### TUIConferenceCancelReason

Reasons for conference cancellation

| Enumeration item | Type | Description |
| --- | --- | --- |
| kConferenceCancelReasonCancelledByAdmin | number | Cancelled by room owner |
| kConferenceCancelReasonRemovedFromAttendees | number | The current user was removed from the list of attendees |

### TUIMediaDeviceEventType

Media device events

| Enumeration item | Type | Description |
| --- | --- | --- |
| onDeviceChanged | string | Device state change event name |

### TUIVoiceReverbType

Voice reverberation effects

| Enumeration item | Type | Description |
| --- | --- | --- |
| kVoiceReverbType_0 | number | Off |
| kVoiceReverbType_1 | number | KTV |
| kVoiceReverbType_2 | number | Small room |
| kVoiceReverbType_3 | number | Auditorium |
| kVoiceReverbType_4 | number | Deep |
| kVoiceReverbType_5 | number | Loud |
| kVoiceReverbType_6 | number | Metallic |
| kVoiceReverbType_7 | number | Magnetic |
| kVoiceReverbType_8 | number | Ethereal |
| kVoiceReverbType_9 | number | Studio |
| kVoiceReverbType_10 | number | Mellow |
| kVoiceReverbType_11 | number | Studio 2 |

### TUIVoiceChangerType

Voice changer effects

| Enumeration item | Type | Description |
| --- | --- | --- |
| kVoiceChangerType_0 | number | Off |
| kVoiceChangerType_1 | number | Naughty child |
| kVoiceChangerType_2 | number | Lolita |
| kVoiceChangerType_3 | number | Uncle |
| kVoiceChangerType_4 | number | Heavy metal |
| kVoiceChangerType_5 | number | Cold |
| kVoiceChangerType_6 | number | Foreign accent |
| kVoiceChangerType_7 | number | Trapped beast |
| kVoiceChangerType_8 | number | Otaku |
| kVoiceChangerType_9 | number | Strong current |
| kVoiceChangerType_10 | number | Heavy machinery |
| kVoiceChangerType_11 | number | Ethereal |

### TUIMediaRotation

Rotation angle

| Enumeration item | Type | Description |
| --- | --- | --- |
| kMediaRotation0 | number | Rotate 0 degrees |
| kMediaRotation90 | number | Rotate 90 degrees |
| kMediaRotation180 | number | Rotate 180 degrees |
| kMediaRotation270 | number | Rotate 270 degrees |

### TUIMediaFillMode

Media displaying Fill mode

| Enumeration item | Type | Description |
| --- | --- | --- |
| kMediaFillMode_Fill | number | The media fills the display area, and the parts of the video that exceed the display window will be cut off. The picture content may not be displayed completely |
| kMediaFillMode_Fit | number | The long side of the media fills the display area, and the short side area will be filled with black. The picture content is displayed completely |

### TUIMediaMirrorType

Mirror mode

| Enumeration item | Type | Description |
| --- | --- | --- |
| kMediaMirrorType_Auto | number | Automatic mode. During local preview, the front camera is mirrored, and the rear camera is not mirrored |
| kMediaMirrorType_Enable | number | Enable mirror |
| kMediaMirrorType_Disable | number | Disable mirror |

### TUIVideoResolution

Video resolution. Only landscape resolutions are defined here. If you want to use a portrait resolution such as 360 Ã 640, you need to specify TUIResolutionMode as Portrait at the same time.

| Enumeration item | Type | Description |
| --- | --- | --- |
| kVideoResolution_120_120 | number | Recommended bitrate (VideoCall) 80kbps; Recommended bitrate (LIVE) 120kbps |
| kVideoResolution_160_160 | number | Recommended bitrate (VideoCall) 100kbps; Recommended bitrate (LIVE) 150kbps |
| kVideoResolution_270_270 | number | Recommended bitrate (VideoCall) 200kbps; Recommended bitrate (LIVE) 300kbps |
| kVideoResolution_480_480 | number | Recommended bitrate (VideoCall) 350kbps; Recommended bitrate (LIVE) 500kbps |
| kVideoResolution_160_120 | number | Recommended bitrate (VideoCall) 100kbps; Recommended bitrate (LIVE) 150kbps |
| kVideoResolution_240_180 | number | Recommended bitrate (VideoCall) 150kbps; Recommended bitrate (LIVE) 250kbps |
| kVideoResolution_280_210 | number | Recommended bitrate (VideoCall) 200kbps; Recommended bitrate (LIVE) 300kbps |
| kVideoResolution_320_240 | number | Recommended bitrate (VideoCall) 250kbps; Recommended bitrate (LIVE) 375kbps |
| kVideoResolution_400_300 | number | Recommended bitrate (VideoCall) 300kbps; Recommended bitrate (LIVE) 450kbps |
| kVideoResolution_480_360 | number | Recommended bitrate (VideoCall) 400kbps; Recommended bitrate (LIVE) 600kbps |
| kVideoResolution_640_480 | number | Recommended bitrate (VideoCall) 600kbps; Recommended bitrate (LIVE) 900kbps |
| kVideoResolution_960_720 | number | Recommended bitrate (VideoCall) 1000kbps; Recommended bitrate (LIVE) 1500kbps |
| kVideoResolution_160_90 | number | Recommended bitrate (VideoCall) 150kbps; Recommended bitrate (LIVE) 250kbps |
| kVideoResolution_256_144 | number | Recommended bitrate (VideoCall) 200kbps; Recommended bitrate (LIVE) 300kbps |
| kVideoResolution_320_180 | number | Recommended bitrate (VideoCall) 250kbps; Recommended bitrate (LIVE) 400kbps |
| kVideoResolution_480_270 | number | Recommended bitrate (VideoCall) 350kbps; Recommended bitrate (LIVE) 550kbps |
| kVideoResolution_640_360 | number | Recommended bitrate (VideoCall) 500kbps; Recommended bitrate (LIVE) 900kbps |
| kVideoResolution_960_540 | number | Recommended bitrate (VideoCall) 850kbps; Recommended bitrate (LIVE) 1300kbps |
| kVideoResolution_1280_720 | number | Recommended bitrate (VideoCall) 1200kbps; Recommended bitrate (LIVE) 1800kbps |
| kVideoResolution_1920_1080 | number | Recommended bitrate (VideoCall) 2000kbps; Recommended bitrate (LIVE) 3000kbpy |

### TUIMediaSourceType

Media source type

| Enumeration item | Type | Description |
| --- | --- | --- |
| kCamera | number | Camera |
| kScreen | number | Screen/Window |
| kImage | number | Image |

### TUIVideoPixelFormat

Video data format

| Enumeration item | Type | Description |
| --- | --- | --- |
| TUIVideoPixelFormat_I420 | number | I420 |
| TUIVideoPixelFormat_BGRA32 | number | BGRA32 |
| TUIVideoPixelFormat_RGBA32 | number | RGBA32 |

## Type Definition

### TUILoginUserInfo

Current login user information.

| Field | Type | Description |
| --- | --- | --- |
| userId | string | Login user's ID |
| userName | string | Login user's name |
| avatarUrl | string | Login user's avatar URL |

### TUIRoomInfo

Room information, which can be obtained using roomEngine.fetchRoomInfo.

| Field | Type | Description |
| --- | --- | --- |
| roomId | string | Room ID |
| roomName | string | Room name |
| roomType | [TUIRoomType](#tuiroomtype) | Room type |
| isSeatEnabled | boolean | Whether to enable seat control (optional parameter when creating a room, default value is false) |
| seatMode | [TUISeatMode](#tuiseatmode) | Seat mode in the room (effective after enabling seat control, default value is TUISeatMode.kFreeToTake) |
| isMicrophoneDisableForAllUser | boolean | Whether to enable mute for all users (optional parameter when creating a room, default value is false) |
| isCameraDisableForAllUser | boolean | Whether to enable disable camera for all users (optional parameter when creating a room, default value is false) |
| isMessageDisableForAllUser | boolean | Whether to allow all users to send messages (optional parameter when creating a room, default value is false) |
| isScreenShareDisableForAllUser | boolean | Whether to enable prohibit screen sharing (optional parameter when creating a room, default value is false) |
| maxSeatCount | number | Maximum seat count, default is 6 |
| roomOwner | string | Room owner user ID, read-only |
| createTime | number | Room creation time, read-only, accurate to seconds |
| roomMemberCount | number | Number of room members, read-only |

### TUIUserInfo

User information.

| Field | Type | Description |
| --- | --- | --- |
| userId | string | User ID |
| userName | string | User name |
| avatarUrl | string | User avatar URL |
| userRole | [TUIRole](#tuirole) | User role |
| hasAudioStream | boolean | Whether there is an audio stream |
| hasVideoStream | boolean | Whether there is a video stream |
| hasScreenStream | boolean | Whether there is a screen sharing stream |

### TUIMessage

Message information.

| Field | Type | Description |
| --- | --- | --- |
| messageId | string | Message ID |
| message | string | Message |
| timestamp | number | Timestamp information, accurate to seconds |
| userId | string | User ID |
| userName | string | User name |
| avatarUrl | string | User avatar URL |

### TUIRequest

Request information.

| Field | Type | Description |
| --- | --- | --- |
| requestAction | [TUIRequestAction](#tuirequestaction) | Request type |
| timestamp | number | Request initiation time |
| requestId | string | Request ID |
| userId | string | User ID sending the request |
| content | string | Other content |

### TUIRequestCallback

Request callback information.

| Field | Type | Description |
| --- | --- | --- |
| requestCallbackType | [TUIRequestCallbackType](#tuirequestcallbacktype) | Request callback type, accept/reject/cancel/timeout/error |
| requestId | string | Request ID |
| userId | string | User ID |
| code | number | Response code of the request |
| message | string | Supplementary description of request status |

### TUISeatInfo

Seat information.

| Field | Type | Description |
| --- | --- | --- |
| index | number | Seat index |
| userId | string | User ID corresponding to the seat |
| locked | boolean | Whether the current seat is locked |
| videoMuted | boolean | Whether the current seat is video muted |
| audioMuted | boolean | Whether the current seat is audio muted |

### TUISeatLockParams

Seat lock status.

| Field | Type | Description |
| --- | --- | --- |
| lockSeat | boolean | Lock the seat |
| lockVideo | boolean | Lock the seat video |
| lockAudio | boolean | Lock the seat audio |

### TUINetwork

Network Information.

| Field | Type | Description |
| --- | --- | --- |
| userId | string | User ID |
| quality | TUINetworkQuality | Network quality |
| upLoss | number | Upstream packet loss rate, unit (%) The smaller the value, the better. Currently, only local users have this information |
| downLoss | number | Downstream packet loss rate, unit (%) The smaller the value, the better. Currently, only local users have this information |
| delay | number | Network delay, unit ms, currently only local users have this information |

### TUIVideoEncoderParams

Video encoding parameters.

| Field | Type | Description |
| --- | --- | --- |
| videoResolution | [TUIVideoResolution](#tuivideoresolution) | Video resolution |
| fps | number | Video frame rate |
| bitrate | number | Video bitrate |
| resolutionMode | [TUIResolutionMode](#tuiresolutionmode) | Portrait/landscape mode |

### TUIRect

Rectangular coordinate area

| Field | Type | Description |
| --- | --- | --- |
| left | number | Left line coordinate |
| top | number | Top line coordinate |
| right | number | Right line coordinate |
| bottom | number | Bottom line coordinate |

### TUICameraCaptureParam

Camera capture parameters

| Enumeration item | Type | Description |
| --- | --- | --- |
| mode | [TUICameraCaptureMode](#tuicameracapturemode) | Camera capture mode |
| width | number | Captured image width |
| height | number | Captured image height |

### TUIAudioMusicParam

Background music playback control information

| Field | Type | Description |
| --- | --- | --- |
| id | number | Music ID. Multiple music tracks are allowed to be played, so an ID is needed to mark them for controlling the start, stop, volume, etc. of the music. |
| path | string | The full path or URL address of the audio file. Supported audio formats include MP3, AAC, M4A, WAV. |
| loopCount | number | Number of times the music is looped. The range is 0 - any positive integer, default value: 0. 0 means playing the music once; 1 means playing the music twice; and so on. |
| publish | boolean | Whether to transmit the music to the remote end. true: The music can be heard by remote users while playing locally; false: The anchor can only hear the music locally, and remote audiences cannot hear it. Default value: false. |
| isShortFile | boolean | Whether it is a short music file. true: A short music file that needs to be repeated; false: A normal music file. Default value: false. |
| startTimeMS | number | Music start playback time point, unit: milliseconds. |
| endTimeMS | number | Music end playback time point, unit milliseconds, 0 means play to the end of the file. |

### TUIMusicPlayObserver

Background music playback event listener type definition

| Field | Type | Description |
| --- | --- | --- |
| onStart | Function \| null | Background music start playback event |
| onPlayProgress | Function \| null | Background music playback progress event |
| onComplete | Function \| null | Background music playback completion event |

### TUIScreenCaptureSourceInfo

Screen/window data

| Field | Type | Description |
| --- | --- | --- |
| type | [TUIMediaSourceType](#tuimediasourcetype) | Media source type: screen/window |
| sourceId | number | Unique ID |
| sourceName | string | Name |
| isMinimizeWindow | boolean | Whether the window is minimized |
| isMainScreen | boolean | Whether it is the main screen |
| rect | [TUIRect](#tuirect) | Relative coordinate position on the display screen |

### TUIMediaSource

Media source data

| Field | Type | Description |
| --- | --- | --- |
| sourceType | [TUIMediaSourceType](#tuimediasourcetype) | Media source type |
| sourceId | string | Unique ID of media source |
| rect | [TUIRect](#tuirect) | Coordinate position relative to the local mixing layout |
| zOrder | number | Display hierarchy. Media sources with higher display hierarchy will cover those with lower display hierarchy, and multiple media sources cannot have the same hierarchy. |
| rotation | [TUIMediaRotation](#tuimediarotation) | Optional, rotation angle |
| fillMode | [TUIMediaFillMode](#tuimediafillmode) | Optional, fill mode |
| mirrorType | [TUIMediaMirrorType](#tuimediamirrortype) | Optional, mirror mode |
| isSelected | boolean | Optional, default: false, whether the media source is selected |

### TUIVideoEncParam

Mixed-stream video encoding parameters

| Field | Type | Description |
| --- | --- | --- |
| videoResolution | [TUIVideoResolution](#tuivideoresolution) | Video resolution |
| resMode | [TUIResolutionMode](#tuiresolutionmode) | Video portrait/landscape mode |
| videoFps | number | Frame rate |
| videoBitrate | number | Bitrate |
| minVideoBitrate | number | Minimum bitrate |
| enableAdjustRes | boolean | Whether to enable adaptive bitrate adjustment, default: true |

### TUILocalMediaTranscodingParams

Local medix mixing transcoding configuration parameters

| Field | Type | Description |
| --- | --- | --- |
| inputSourceList | Array<[TUIMediaSource](#tuimediasource)> | Media source list |
| videoEncoderParams | [TUIVideoEncParam](#tuivideoencparam) | Mixed-stream video encoding parameters |
| canvasColor | number | Mixed-stream video background color, RGB format, default: 0x0 |


---
*Source: [https://trtc.io/document/64351](https://trtc.io/document/64351)*
