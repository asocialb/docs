# TUIRoomDefine

### Enumeration definitions

#### TUIRoomDefine

| Type | Description |
| --- | --- |
| [TUIRoomType](https://www.tencentcloud.com/document/product/647/67259#RoomType) | Room type |
| [TUISeatMode](https://www.tencentcloud.com/document/product/647/67259#TUISeatMode) | Microphone Mode |
| [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/67259#45f8cc27-8bbe-4ed5-bb40-511a08e27477) | Media Device Type Inside the Room |
| [TUIRole](https://www.tencentcloud.com/document/product/647/67259#Role) | Role Type Inside the Room |
| [TUIVideoQuality](https://www.tencentcloud.com/document/product/647/67259#74d0aadf-0c54-4a05-9e30-f40b427f1402) | Video Quality |
| [TUIAudioQuality](https://www.tencentcloud.com/document/product/647/67259#c079e8f9-62be-4ea2-b740-20658dcec529) | Audio Quality |
| [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/67259#VideoStreamType) | Video stream type |
| [TUIChangeReason](https://www.tencentcloud.com/document/product/647/67259#ChangeReason) | Change Reason (Reason for user audio/video status change: self-initiated or modified by room owner or admin) |
| [TUICaptureSourceType](https://www.tencentcloud.com/document/product/647/67259#02abd5f6-ef70-4636-9ff5-fd331baac4f5) | Screen Sharing Capture Source Type |
| [TUIRequestAction](https://www.tencentcloud.com/document/product/647/67259#RequestAction) | Request Type |
| [TUIResolutionMode](https://www.tencentcloud.com/document/product/647/67259#TUIResolutionMode) | Resolution Mode (Landscape or Portrait) |
| [TUIUserInfoModifyFlag](https://www.tencentcloud.com/document/product/647/67259#TUIUserInfoModifyFlag) | User Information Modification Type |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [TUIError](https://www.tencentcloud.com/document/product/647/67259#NetworkQuality) | Error Codes |
| [TUINetworkQuality](https://www.tencentcloud.com/document/product/647/67259#960e26d8-5853-4903-8174-57d6e7f225a3) | Network quality |
| [TUIExtensionType](https://www.tencentcloud.com/document/product/647/67259#55ea0b2e-7c8d-4217-a78c-2d447aa72d08) | Plugin Type |

### Common Structure

#### TUIRoomDefine

| Type | Description |
| --- | --- |
| [TUIRoomInfo](https://www.tencentcloud.com/document/product/647/67259#RoomInfo) | Room Information |
| [TUILoginUserInfo](https://www.tencentcloud.com/document/product/647/67259#83093ad1-7671-4f9f-aada-3c74d5006c75) | User log in to Information |
| [TUIUserInfo](https://www.tencentcloud.com/document/product/647/67259#UserInfo) | Inside the Room User Information |
| [TUISeatInfo](https://www.tencentcloud.com/document/product/647/67259#SeatInfo) | Seat Information Inside the Room |
| [TUISeatLockParams](https://www.tencentcloud.com/document/product/647/67259#080212f8-d6ce-4430-b745-2fdd5ef8c330) | Parameters for Locking the Mic Position |
| [TUIUserVoiceVolume](https://www.tencentcloud.com/document/product/647/67259#UserVoiceVolume) | User Volume Inside the Room |
| [TUIRequest](https://www.tencentcloud.com/document/product/647/67259#Request) | Signaling Request |
| [TUIActionCallback](https://www.tencentcloud.com/document/product/647/67259#TUIActionCallback) | User Operation Callback |
| [TUIPlayCallback](https://www.tencentcloud.com/document/product/647/67259#TUIPlayCallback) | Video Playback Callback |
| [TUIRequestCallback](https://www.tencentcloud.com/document/product/647/67259#TUIRequestCallback) | User Request Callback |
| [TUIUserListResult](https://www.tencentcloud.com/document/product/647/67259#TUIUserListResult) | User List Information |
| [TUIUserVoiceVolume](https://www.tencentcloud.com/document/product/647/67259#TUIUserVoiceVolume) | User Volume Information |
| [TUIValueCallBack<T>](https://www.tencentcloud.com/document/product/647/67259#TUIValueCallBack<T>) | Callback with Return Value (T) |
| [TUIRoomVideoEncoderParams](https://www.tencentcloud.com/document/product/647/67259#TUIVideoEncoderParams) | Video Encoder Parameters |
| [TUIEnterRoomOptions](https://www.tencentcloud.com/document/product/647/67259#b27a2140-db19-4e74-b537-dde71f0a14b2) | Room entry parameters |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [TUINetwork](https://www.tencentcloud.com/document/product/647/67259#NetworkInfo) | Network quality information |
| [TUIMessage](https://www.tencentcloud.com/document/product/647/67259#Message) | Message |
| [TUIImageBuffer](https://www.tencentcloud.com/document/product/647/67259#046c7dbf-4a6c-4367-a074-2186c2fa9632) | Image information |

### TUIRoomType

Room type

| Enumeration | Value | Description |
| --- | --- | --- |
| conference | 1 | Meeting Type Room, suitable for meetings and educational contexts. In this room, users can choose different modes such as free speech mode, apply for speech, and speaking on the microphone |
| livingRoom | 2 | Live Streaming Type Room, suitable for live streaming scenarios. In this room, users can speak freely, and the room uses a microphone position control mode, where each microphone position has a number |

## TUISeatMode

Microphone Mode

| Enumeration | Value | Description |
| --- | --- | --- |
| freeToTake | 1 | Freely Join Microphone Mode, the audience can freely join the mic without application |
| applyToTake | 2 | Apply for Microphone Mode, the audience needs approval from the homeowner or administrator to join the mic |

### TUIMediaDevice

Media Device Type Inside the Room

| Enumeration | Value | Description |
| --- | --- | --- |
| microphone | 1 | Microphone |
| camera | 2 | Camera |
| screen | 3 | Screen Sharing |

### TUIRole

Role Type Inside the Room

| Enumeration | Value | Description |
| --- | --- | --- |
| roomOwner | 0 | Homeowner. Generally refers to the creator of the room and the owner of the highest permissions in the room |
| administrator | 1 | Room administrator |
| generalUser | 2 | Ordinary member in the room |

### TUIVideoQuality

Video Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| videoQuality_360P | 1 | Low-definition 360p |
| videoQuality_540P | 2 | Standard Definition 540p |
| videoQuality_720P | 3 | HD 720p |
| videoQuality_1080P | 4 | Ultra HD 1080p |

### TUIAudioQuality

Audio Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| audioProfileSpeech | 0 | Voice Mode |
| audioProfileDefault | 1 | Default Mode |
| audioProfileMusic | 2 | Music Mode |

### TUIVideoStreamType

Video stream type

| Enumeration | Value | Description |
| --- | --- | --- |
| cameraStream | 0 | HD Camera Video Stream |
| screenStream | 1 | Screen Share Video Stream |
| cameraStreamLow | 2 | Low-definition Camera Video Stream |

### TUIChangeReason

Change Reason (Reason for user audio/video status change: self-initiated or modified by room owner or admin)

| Enumeration | Value | Description |
| --- | --- | --- |
| changedBySelf | 0 | User Operation |
| changedByAdmin | 1 | Operation by Homeowner or Administrator |

### TUICaptureSourceType

Screen Sharing Capture Source Type

| Enumeration | Value | Description |
| --- | --- | --- |
| unknown | -1 | Undefined |
| window | 0 | Window |
| screen | 1 | Screen |

### TUIRequestAction

Request Type

| Enumeration | Value | Description |
| --- | --- | --- |
| invalidAction | 0 | Invalid request |
| requestToOpenRemoteCamera | 1 | Request remote user to turn on the camera |
| requestToOpenRemoteMicrophone | 2 | Request remote user to turn on the microphone |
| requestToConnectOtherRoom | 3 | Request to connect to another room |
| requestToTakeSeat | 4 | Request to take the mic |
| requestRemoteUserOnSeat | 5 | Request remote user to take the mic |
| applyToAdminToOpenLocalCamera | 6 | Request the administrator to turn on the local camera |
| applyToAdminToOpenLocalMicrophone | 7 | Request the administrator to turn on the local microphone |

### TUIResolutionMode

| Enumeration | Value | Description |
| --- | --- | --- |
| landscape | 0 | Landscape |
| portrait | 1 | Portrait |

### TUIUserInfoModifyFlag

| Enumeration | Value | Description |
| --- | --- | --- |
| none | 0x00 | Empty, indicating no change |
| userRole | 0x01 << 0 | User Role |
| nameCard | 0x01 << 1 | Nickname in the Room |

### TUIError

Error Codes

| Enumeration | Value | Description |
| --- | --- | --- |
| success | 0 | Operation successful |
| errFailed | -1 | A common error not yet classified |
| errFreqLimit | -2 | Request was frequency limited, please try again later |
| errRepeatOperation | -3 | Duplicate operation, please check if your API call is repeated |
| errSDKAppIDNotFound | -1000 | SDKAppID not found, please confirm application information in the [Console of TRTC](https://console.trtc.io/app) |
| errInvalidParameter | -1001 | An invalid parameter was passed in during API calling |
| errSdkNotInitialized | -1002 | SDK not initialized |
| errPermissionDenied | -1003 | No operational permissions |
| errRequirePayment | -1004 | This feature requires an additional package |
| errCameraStartFailed | -1100 | Failed to turn on the camera |
| errCameraNotAuthorized | -1101 | Camera not authorized |
| errCameraOccupy | -1102 | Camera is being used |
| errCameraDeviceEmpty | -1103 | No camera device available |
| errMicrophoneStartFailed | -1104 | Failed to open microphone |
| errMicrophoneNotAuthorized | -1105 | Microphone not authorized |
| errMicrophoneOccupy | -1106 | Microphone is occupied |
| errMicrophoneDeviceEmpty | -1107 | No microphone device available |
| errGetScreenSharingTargetFailed | -1108 | Failed to get screen sharing objects |
| errStartScreenSharingFailed | -1109 | Failed to enable screen sharing |
| errRoomIdNotExist | -2100 | The room does not exist when entering, it may have been dissolved |
| errOperationInvalidBeforeEnterRoom | -2101 | You need to enter the room to use this feature |
| errExitNotSupportedForRoomOwner | -2102 | Homeowner cannot perform check-out procedure, Conference room type: transfer homeowner first, then check out. LivingRoom room type: homeowner can only dissolve the room |
| errOperationNotSupportedInCurrentRoomType | -2103 | This operation is not supported under the current room type |
| errRoomIdInvalid | -2105 | Illegal Room ID creation, Custom ID must be printable ASCII characters (0x20-0x7e), up to 48 bytes |
| errRoomIdOccupied | -2106 | Room ID is already in use, please choose another room ID |
| errRoomNameInvalid | -2107 | Invalid room name, the maximum length is 30 bytes, character encoding must be UTF-8, if it includes Chinese characters |
| errAlreadyInOtherRoom | -2108 | The current user is already in another room and needs to check out before joining a new roomA single RoomEngine instance only supports a user entering one room. To enter a different room, please check out or use a new RoomEngine instance |
| errUserNotExist | -2200 | The user does not exist. |
| errUserNotEntered | -2201 | User is not in the current room |
| errUserNeedOwnerPermission | -2300 | Homeowner privileges are required to operate |
| errUserNeedAdminPermission | -2301 | Homeowner or administrator privileges are required to operate |
| errRequestNoPermission | -2310 | No permission for signaling request, such as canceling an invitation not initiated by yourself |
| errRequestIdInvalid | -2311 | Signaling request ID is invalid or has already been processed |
| errMaxSeatCountLimit | -2340 | Maximum microphone position limit exceeds the package quota |
| errAlreadyInSeat | -2341 | The current user is already on the microphone position |
| errSeatOccupied | -2342 | The current microphone position is already occupied |
| errSeatLocked | -2343 | The current microphone position is locked |
| errSeatIndexNotExist | -2344 | Microphone position number does not exist |
| errUserNotInSeat | -2345 | The current user is not on the microphone |
| errAllSeatOccupied | -2346 | The number of users on the microphone is full |
| errOpenMicrophoneNeedSeatUnlock | -2360 | The current microphone position is locked for audio |
| errOpenMicrophoneNeedPermissionFromAdmin | -2361 | You need to request permission from the homeowner or administrator to use the microphone |
| errOpenCameraNeedSeatUnlock | -2370 | The current microphone position is locked for video, it needs to be unlocked by the homeowner to use the camera |
| errOpenCameraNeedPermissionFromAdmin | -2371 | You need to request permission from the homeowner or administrator to use the camera |
| errSendMessageDisabledForAll | -2380 | All members are muted in the current room |
| errSendMessageDisabledForCurrent | -2381 | You are muted in the current room |

### TUINetworkQuality

Network quality

| Enumeration | Value | Description |
| --- | --- | --- |
| qualityUnknown | 0 | Undefined |
| qualityExcellent | 1 | The present network is exceedingly good |
| qualityGood | 2 | The current network is fairly good |
| qualityPoor | 3 | Current network is average |
| qualityBad | 4 | Current network is poor |
| qualityVeryBad | 5 | Current network is very poor |
| qualityDown | 6 | Current network does not meet the minimum requirements of TRTC |

### TUIRoomInfo

Room Information

| Field | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| roomType | [TUIRoomType](https://www.tencentcloud.com/document/product/647/67259#RoomType) | Room type |
| ownerId | String | Host ID. Defaults to the room creator (read-only) |
| name | String | Room Name. Defaults to Room ID |
| isSeatEnabled | bool | Whether to enable microphone position control |
| seatMode | [TUISeatMode](https://www.tencentcloud.com/document/product/647/67259#TUISeatMode) | Microphone Mode (effective only when microphone position control is enabled) |
| createTime | int | Room Creation Time (read-only) |
| memberCount | int | Number of members in the room (read-only) |
| maxSeatCount | int | Maximum number of microphones (can only be set before entering the room or when creating the room) |
| isCameraDisableForAllUser | bool | Whether to disable the camera (optional parameter when creating a room). Default value: false |
| isMicrophoneDisableForAllUser | bool | Whether to disable the microphone (optional parameter when creating a room). Default value: false |
| isMessageDisableForAllUser | bool | Whether to disable sending messages (optional parameter when creating a room). Default value: false |
| enableCDNStreaming | bool | Whether to enable CDN live streaming (optional parameter when creating a room, used in live rooms). Default value: false |
| cdnStreamDomain | String | Live streaming push domain name (optional parameter when creating a room, used in live rooms). Default value: empty |
| password | String | Room password |

### TUILoginUserInfo

User log in to Information

| Field | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| userName | String | Username |
| avatarUrl | String | User profile photo URL |
| customInfo | Map<String, String> | Customized Information |

### TUIUserInfo

Inside the Room User Information

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| userName | String | Username |
| nameCard | String | Nickname in the Room |
| avatarUrl | String | User profile photo URL |
| userRole | [TUIRole](https://www.tencentcloud.com/document/product/647/67259#Role) | User Role Type |
| hasAudioStream | bool | Whether there is an audio stream. Default value: false |
| hasVideoStream | bool | Whether there is a video stream. Default value: false |
| hasScreenStream | bool | Whether there is a screen sharing stream. Default value: false |
| customInfo | Map<String, String>? | Room member custom information |
| isMessageDisabled | bool | Whether muted |

### TUISeatInfo

Seat Information Inside the Room

| Field | Type | Description |
| --- | --- | --- |
| index | int | Mic seat serial number |
| userId | String | User ID |
| userName | String | Username |
| nameCard | String | Nickname in the Room |
| avatarUrl | String | User profile photo URL |
| isLocked | bool | Whether the microphone position is locked. Default value: false |
| isVideoLocked | bool | Whether the microphone position is prohibited from opening the camera. Default value: false |
| isAudioLocked | bool | Whether the microphone position is prohibited from opening the microphone. Default value: false |
| userName | String | User Nickname |
| avatarUrl | String | User profile photo URL |

### TUISeatLockParams

Parameters for Locking the Mic Position

| Field | Type | Meaning |
| --- | --- | --- |
| lockSeat | bool | Lock microphone position. Default is false |
| lockVideo | bool | Lock microphone position camera. Default is false |
| lockAudio | bool | Lock microphone position microphone. Default is false |

### TUIUserVoiceVolume

User Volume Inside the Room

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| volume | int | Volume. Used to carry the volume size of all speaking users, value range 0-100 |

### TUIRequest

Signaling Request

| Field | Type | Description |
| --- | --- | --- |
| requestId | String | Request ID |
| requestAction | [TUIRequestAction](https://www.tencentcloud.com/document/product/647/67259#RequestAction) | Request Type |
| userId | String | User ID |
| userName | String | Username |
| nameCard | String | Nickname in the Room |
| avatarUrl | String | User profile photo URL |
| content | String | Signaling content |
| timestamp | int | Timestamp |
| userName | String | User Nickname |
| avatarUrl | String | User profile photo URL |

### TUIActionCallback

| Field | Type | Description |
| --- | --- | --- |
| code | [TUIError](https://www.tencentcloud.com/document/product/647/67259#NetworkQuality) | Error Codes |
| message | String? | Error Message |

### TUIPlayCallback

| Field | Type | Description |
| --- | --- | --- |
| onPlaying | (String userId) {} | Playing callback |
| onLoading | (String userId) {} | Loading callback |
| onPlayError | (String userId, TUIError code, String message) {} | Playback error callback |

### TUIRequestCallback

| Field | Type | Description |
| --- | --- | --- |
| onAccepted | (String requestId, String userId) {} | Request accepted callback |
| onRejected | (String requestId, String userId, String message) {} | Request rejected callback |
| onCancelled | (String requestId, String userId) {} | Request canceled callback |
| onTimeout | (String requestId, String userId) {} | Request timeout callback |
| onError | (String requestId, String userId, TUIError error, String message) {} | Request error callback |

### TUIUserListResult

| Field | Type | Description |
| --- | --- | --- |
| nextSequence | int | Pagination retrieval flag. If the returned nextSequence is not zero, use the returned nextSequence to retrieve again until it returns zero |
| userInfoList | List<TUIUserInfo> | List of users returned by this call |

### TUIUserVoiceVolume

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| volume | int | User Volume Level |

### TUIValueCallBack<T>

| Field | Type | Description |
| --- | --- | --- |
| code | [TUIError](https://www.tencentcloud.com/document/product/647/67259#NetworkQuality) | Error Codes |
| message | String? | Error Message |
| data | T? | Return data, example: If T is TUIUserInfo, the data field type of TUIValueCallBack<TUIUserInfo> is TUIUserInfo |

### TUIRoomVideoEncoderParams

| Field | Type | Description |
| --- | --- | --- |
| videoResolution | TUIVideoQuality | Video Quality |
| resolutionMode | TUIResolutionMode | Resolution Mode |
| fps | int | Video Capture Frame Rate |
| bitrate | int | Target Video Bitrate |

### TUIEnterRoomOptions

| Field | Type | Description |
| --- | --- | --- |
| password | String | Room password |

### TUINetwork

Network quality information

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| quality | [TUINetworkQuality](https://www.tencentcloud.com/document/product/647/67259#960e26d8-5853-4903-8174-57d6e7f225a3) | Network quality |
| upLoss | int | Upstream packet loss rate |
| downLoss | int | Downstream packet loss rate |
| delay | int | Network Latency |

### TUIExtensionType

Plugin Type

| Enumeration | Value | Description |
| --- | --- | --- |
| deviceManager | 1 | TUIRoomDeviceManager type |
| liveListManger | 2 | TUIRLiveListManager type |
| conferenceListManager | 3 | TUIConferenceListManager type |

### TUIMessage

Message

| Field | Type | Description |
| --- | --- | --- |
| messageId | String | Message ID |
| message | String | Message text |
| timestamp | int | Message timestamp |
| userId | String | Message sender |
| userName | String | Nickname of the message sender |
| avatarUrl | String | Profile photo of the message sender |

### TUIImageBuffer

Image information

| Field | Type | Description |
| --- | --- | --- |
| buffer | String | Image data cache address |
| length | int | Length |
| width | int | Width |
| height | int | Height |


---
*Source: [https://trtc.io/document/67259](https://trtc.io/document/67259)*
