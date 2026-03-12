# Type Definition

### Enumeration Definition

#### TUIRoomDefine

| Type | Description |
| --- | --- |
| [TUIRoomType](https://www.tencentcloud.com/document/product/647/57515#RoomType) | Room Type |
| [TUISpeechMode](https://www.tencentcloud.com/document/product/647/57515#SpeechMode) | Mic Control Mode |
| [TUIMediaDevice](https://www.tencentcloud.com/document/product/647/57515#MediaDevice) | Room Media Device Type |
| [TUIRole](https://www.tencentcloud.com/document/product/647/57515#Role) | Room Role Type |
| [TUIVideoQuality](https://www.tencentcloud.com/document/product/647/57515#VideoQuality) | Video Quality |
| [TUIAudioQuality](https://www.tencentcloud.com/document/product/647/57515#AudioQuality) | Audio Quality |
| [TUIVideoStreamType](https://www.tencentcloud.com/document/product/647/57515#VideoStreamType) | Video Stream Type |
| [TUIChangeReason](https://www.tencentcloud.com/document/product/647/57515#ChangeReason) | Change Reason (User audio and video status change operation reason: self-modification or modified by room owner/administrator) |
| [TUICaptureSourceType](https://www.tencentcloud.com/document/product/647/57515#CaptureSourceType) | Screen Sharing Capture Source Type |
| [TUIRequestAction](https://www.tencentcloud.com/document/product/647/57515#RequestAction) | Request Type |
| [TUIResolutionMode](https://www.tencentcloud.com/document/product/647/57515#TUIResolutionMode) | Video resolution mode (landscape or portrait) |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [TUIError](https://www.tencentcloud.com/document/product/647/57515#TUIError) | Error Code |
| [TUINetworkQuality](https://www.tencentcloud.com/document/product/647/57515#NetworkQuality) | Network Quality |

### Common Structure

#### TUIRoomDefine

| Type | Description |
| --- | --- |
| [TUIRoomInfo](https://www.tencentcloud.com/document/product/647/57515#RoomInfo) | Room data |
| [TUILoginUserInfo](https://www.tencentcloud.com/document/product/647/57515#LoginUserInfo) | User Login Information |
| [TUIUserInfo](https://www.tencentcloud.com/document/product/647/57515#UserInfo) | Room User Information |
| [TUISeatInfo](https://www.tencentcloud.com/document/product/647/57515#SeatInfo) | Room Seat Information |
| [TUISeatLockParams](https://www.tencentcloud.com/document/product/647/57515#SeatLockParams) | Lock Seat Operation Parameters |
| [TUIUserVoiceVolume](https://www.tencentcloud.com/document/product/647/57515#UserVoiceVolume) | Room User Volume |
| [TUIRequest](https://www.tencentcloud.com/document/product/647/57515#Request) | Signaling Request |
| [TUIActionCallback](https://www.tencentcloud.com/document/product/647/57515#TUIActionCallback) | User Operation Callback |
| [TUIPlayCallback](https://www.tencentcloud.com/document/product/647/57515#TUIPlayCallback) | Video Playback Callback |
| [TUIRequestCallback](https://www.tencentcloud.com/document/product/647/57515#TUIRequestCallback) | User Request Callback |
| [TUIUserListResult](https://www.tencentcloud.com/document/product/647/57515#TUIUserListResult) | User List Information |
| [TUIUserVoiceVolume](https://www.tencentcloud.com/document/product/647/57515#TUIUserVoiceVolume) | User Volume Information |
| [TUIValueCallBack<T>](https://www.tencentcloud.com/document/product/647/57515#TUIValueCallBack<T>) | With Return Value (T) Callback |
| [TUIRoomVideoEncoderParams](https://www.tencentcloud.com/document/product/647/57515#TUIVideoEncoderParams) | Video encoder params |

#### TUICommonDefine

| Type | Description |
| --- | --- |
| [TUINetwork](https://www.tencentcloud.com/document/product/647/57515#NetworkInfo) | Network Quality Information |
| [TUIMessage](https://www.tencentcloud.com/document/product/647/57515#Message) | Message |
| [TUIImageBuffer](https://www.tencentcloud.com/document/product/647/57515#ImageBuffer) | Image Info |

### TUIRoomType

Room Type

| Enumeration | Value | Description |
| --- | --- | --- |
| conference | 1 | Conference Type Room, suitable for conference and education scenarios, this room can enable free speech, apply for speech, go live and other modes. |
| livingRoom | 2 | Live Type Room, suitable for live broadcast scenarios, this room can enable free speech, mic control mode, and the seats in this room are numbered. |

### TUISpeechMode

Mic Control Mode

| Enumeration | Value | Description |
| --- | --- | --- |
| freeToSpeak | 1 | Free speech mode |
| applyToSpeak | 2 | Apply to speak mode. (Only effective in conference type room) |
| applySpeakAfterTakingSeat | 3 | Go Live mode |

> **Explanation:**The relationship between Room Type, Mic Control Mode, and Going Live (takeSeat)Room TypeMic Control Mode
> 
> 
> freeToSpeakapplyToSpeakapplySpeakAfterTakingSeatconferenceNot SupportedNot SupportedNeed to Apply to the Host/Admin (takeSeat), Can Speak with Mic/Camera After ApprovallivingRoomCan Freely Go LiveNot SupportedNeed to Apply to the Host/Admin (takeSeat), Can Speak with Mic/Camera After Approval

### TUIMediaDevice

Room Media Device Type

| Enumeration | Value | Description |
| --- | --- | --- |
| microphone | 1 | Mic |
| camera | 2 | Camera |
| screen | 3 | Screen Sharing |

### TUIRole

Room Role Types

| Enumeration | Value | Description |
| --- | --- | --- |
| roomOwner | 0 | Room Owner. Generally refers to the creator of the room, the highest authority holder in the room |
| administrator | 1 | Room Administrator |
| generalUser | 2 | General Member in the room |

### TUIVideoQuality

Video Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| videoQuality_360P | 1 | Low Definition 360P |
| videoQuality_540P | 2 | Standard Definition 540P |
| videoQuality_720P | 3 | High Definition 720P |
| videoQuality_1080P | 4 | Ultra Definition 1080P |

### TUIAudioQuality

Audio Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| audioProfileSpeech | 0 | Vocal Mode |
| audioProfileDefault | 1 | Default Mode |
| audioProfileMusic | 2 | Music Mode |

### TUIVideoStreamType

Video Stream Types

| Enumeration | Value | Description |
| --- | --- | --- |
| cameraStream | 0 | HD Camera Video Stream |
| screenStream | 1 | Screen Sharing Video Stream |
| cameraStreamLow | 2 | Low Definition Camera Video Stream |

### TUIChangeReason

Change Reason (User audio and video status change operation reason: self-initiated modification or modified by room owner/administrator)

| Enumeration | Value | Description |
| --- | --- | --- |
| changedBySelf | 0 | Self-operation |
| changedByAdmin | 1 | Room Owner or Administrator operation |

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
| requestToOpenRemoteCamera | 1 | Request remote user to open the camera |
| requestToOpenRemoteMicrophone | 2 | Request remote user to open the microphone |
| requestToConnectOtherRoom | 3 | Request to connect to another room |
| requestToTakeSeat | 4 | Request to go live |
| requestRemoteUserOnSeat | 5 | Request remote user to go live |
| applyToAdminToOpenLocalCamera | 6 | Request to the administrator to open the local camera |
| applyToAdminToOpenLocalMicrophone | 7 | Request to the administrator to open the local microphone |

### TUIResolutionMode

Video resolution mode (landscape or portrait)

| Enumeration | Value | Description |
| --- | --- | --- |
| landscape | 0 | landscape |
| portrait | 1 | portrait |

### TUIError

Error Code

| Enumeration | Value | Description |
| --- | --- | --- |
| success | 0 | Operation Successful |
| errFailed | -1 | Temporarily Unclassified General Error |
| errFreqLimit | -2 | Request Limited, Please Try Again Later |
| errRepeatOperation | -3 | Repeated operation, please check whether your interface call is repeated |
| errSDKAppIDNotFound | -1000 | SDKAppID Not Found, Please Confirm Application Info in [TRTC Console](https://console.tencentcloud.com/trtc/allapp) |
| errInvalidParameter | -1001 | Illegal Input Parameters When Calling API |
| errSdkNotInitialized | -1002 | SDK Not Initialized |
| errPermissionDenied | -1003 | No Operation Permission |
| errRequirePayment | -1004 | Need to Open Extra Package for This Feature |
| errCameraStartFailed | -1100 | Failed to Open Camera |
| errCameraNotAuthorized | -1101 | Camera Not Authorized |
| errCameraOccupy | -1102 | Camera Occupied |
| errCameraDeviceEmpty | -1103 | No Camera Device Currently |
| errMicrophoneStartFailed | -1104 | Microphone Opening Failed |
| errMicrophoneNotAuthorized | -1105 | Microphone Not Authorized |
| errMicrophoneOccupy | -1106 | Microphone Occupied |
| errMicrophoneDeviceEmpty | -1107 | No Microphone Device Currently |
| errGetScreenSharingTargetFailed | -1108 | Failed to Get Screen Sharing Target |
| errStartScreenSharingFailed | -1109 | Failed to Start Screen Sharing |
| errRoomIdNotExist | -2100 | Room Does Not Exist When Entering, or Maybe Closed |
| errOperationInvalidBeforeEnterRoom | -2101 | Need to Enter the Room Before Using This Feature |
| errExitNotSupportedForRoomOwner | -2102 | Room Owner Does Not Support Exit Operation, Conference Room Type: You can transfer the room owner first, then exit the room. LivingRoom Room Type: The room owner can only close the room |
| errOperationNotSupportedInCurrentRoomType | -2103 | This Operation is Not Supported in the Current Room Type |
| errOperationNotSupportedInCurrentSpeechMode | -2104 | This Operation is Not Supported in the Current Speech Mode |
| errRoomIdInvalid | -2105 | Illegal Room ID Creation, Custom ID Must Be Printable ASCII Characters (0x20-0x7e), Up to 48 Bytes |
| errRoomIdOccupied | -2106 | Room ID Already in Use, Please Choose Another Room ID |
| errRoomNameInvalid | -2107 | Illegal Room Name, The Name Must Be Up to 30 Bytes, The Character Encoding Must Be UTF-8, If It Contains Chinese |
| errAlreadyInOtherRoom | -2108 | The Current User is Already in Another Room, You Need to Exit the Room First to Join a New Room.A single roomEngine instance only supports the user entering one room. If you want to enter a different room, please exit the room first or use a new roomEngine instance |
| errUserNotExist | -2200 | User Does Not Exist |
| errUserNotEntered | -2201 | User is Not in the Current Room |
| errUserNeedOwnerPermission | -2300 | Room Owner Permission Required for Operation |
| errUserNeedAdminPermission | -2301 | Room Owner or Administrator Permission Required for Operation |
| errRequestNoPermission | -2310 | No Permission for Signaling Request, For Example, Canceling an Invitation Not Initiated by Yourself |
| errRequestIdInvalid | -2311 | Invalid Signaling Request ID or Already Processed |
| errMaxSeatCountLimit | -2340 | Maximum Seat Exceeds Package Quantity Limit |
| errAlreadyInSeat | -2341 | Current User is Already on the Seat |
| errSeatOccupied | -2342 | The Current Seat is Already Occupied |
| errSeatLocked | -2343 | The Current Seat is Locked |
| errSeatIndexNotExist | -2344 | Seat Number Does Not Exist |
| errUserNotInSeat | -2345 | Current User is Not on the Mic |
| errAllSeatOccupied | -2346 | The Number of People on the Mic is Full |
| errOpenMicrophoneNeedSeatUnlock | -2360 | The Current Seat Audio is Locked |
| errOpenMicrophoneNeedPermissionFromAdmin | -2361 | Need to Apply to the Room Owner or Administrator to Open the Microphone |
| errOpenCameraNeedSeatUnlock | -2370 | The Current Seat Video is Locked, The Room Owner Needs to Unlock the Seat Before Opening the Camera |
| errOpenCameraNeedPermissionFromAdmin | -2371 | Need to Apply to the Room Owner or Administrator to Open the Camera |
| errSendMessageDisabledForAll | -2380 | The Current Room Has Enabled Mute for All |
| errSendMessageDisabledForCurrent | -2381 | In the Current Room, You Have Been Muted |

### TUINetworkQuality

Network Quality

| Enumeration | Value | Description |
| --- | --- | --- |
| qualityUnknown | 0 | Undefined |
| qualityExcellent | 1 | The Current Network is Very Good |
| qualityGood | 2 | The Current Network is Good |
| qualityPoor | 3 | The Current Network is Average |
| qualityBad | 4 | The Current Network is Poor |
| qualityVeryBad | 5 | The Current Network is Very Poor |
| qualityDown | 6 | The Current Network Does Not Meet the Minimum Requirements of TRTC |

### TUIRoomInfo

Room data

| Field | Type | Description |
| --- | --- | --- |
| roomId | String | Room ID |
| roomType | [TUIRoomType](https://www.tencentcloud.com/document/product/647/57515#RoomType) | Room Type |
| ownerId | String | Host ID, Default is Room Creator (Read Only) |
| name | String | Room Name, Default is Room ID |
| speechMode | [TUISpeechMode](https://www.tencentcloud.com/document/product/647/57515#SpeechMode) | Room Speech Mode |
| createTime | int | Room Creation Time (Read Only) |
| memberCount | int | Number of Members in the Room (Read Only) |
| maxSeatCount | int | Maximum Seat Quantity (Only Supported When Entering the Room and Creating the Room) |
| isCameraDisableForAllUser | bool | Whether to Prohibit Opening the Camera (Optional Parameter When Creating a Room). Default Value: false |
| isMicrophoneDisableForAllUser | bool | Whether to Prohibit Opening the Microphone (Optional Parameter When Creating a Room). Default Value: false |
| isMessageDisableForAllUser | bool | Whether to Prohibit Sending Messages (Optional Parameter When Creating a Room). Default Value: false |
| enableCDNStreaming | bool | Whether to Enable CDN Live Streaming (Optional Parameter When Creating a Room, for Live Room Use). Default Value: false |
| cdnStreamDomain | String | Live Streaming Push Domain (Optional Parameter When Creating a Room, for Live Room Use). Default Value: Empty |

### TUILoginUserInfo

User Login Info

| Field | Type | Meaning |
| --- | --- | --- |
| userId | String | User ID |
| userName | String | User Name |
| avatarUrl | String | User Avatar URL |
| customInfo | Map<String, String> | Custom Information |

### TUIUserInfo

User Information in the Room

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| userName | String | User Name |
| avatarUrl | String | User Avatar URL |
| userRole | [TUIRole](https://www.tencentcloud.com/document/product/647/57515#Role) | User Role Type |
| hasAudioStream | bool | Whether There is an Audio Stream. Default Value: false |
| hasVideoStream | bool | Whether There is a Video Stream. Default Value: false |
| hasScreenStream | bool | Whether There is a Screen Sharing Stream. Default Value: false |

### TUISeatInfo

Seat Information in the Room

| Field | Type | Description |
| --- | --- | --- |
| index | int | Seat Number |
| userId | String | User ID |
| isLocked | bool | Whether the Seat is Locked. Default Value: false |
| isVideoLocked | bool | Whether the Seat is Prohibited from Opening the Camera. Default Value: false |
| isAudioLocked | bool | Whether the Seat is Prohibited from Opening the Microphone. Default Value: false |

### TUISeatLockParams

Lock Seat Operation Parameters

| Field | Type | Meaning |
| --- | --- | --- |
| lockSeat | bool | Lock Seat. Default Value: false |
| lockVideo | bool | Lock Seat Camera. Default Value: false |
| lockAudio | bool | Lock Seat Microphone. Default Value: false |

### TUIUserVoiceVolume

User Volume in the Room

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| volume | int | Volume. Used to Carry the Volume of All Speaking Users, Value Range 0 - 100 |

### TUIRequest

Signaling Request

| Field | Type | Description |
| --- | --- | --- |
| requestId | String | Request ID |
| requestAction | [TUIRequestAction](https://www.tencentcloud.com/document/product/647/57515#RequestAction) | Request Type |
| userId | String | User ID |
| content | String | Signaling Content |
| timestamp | int | Timestamp |

### TUIActionCallback

| Field | Type | Description |
| --- | --- | --- |
| code | [TUIError](https://www.tencentcloud.com/document/product/647/57515#TUIError) | Error Code |
| message | String? | Error Information |

### TUIPlayCallback

| Field | Type | Description |
| --- | --- | --- |
| onPlaying | (String userId) {} | Playing Callback |
| onLoading | (String userId) {} | Loading Callback |
| onPlayError | (String userId, TUIError code, String message) {} | Playback Error Callback |

### TUIRequestCallback

| Field | Type | Description |
| --- | --- | --- |
| onAccepted | (String requestId, String userId) {} | Request Accepted Callback |
| onRejected | (String requestId, String userId, String message) {} | Request Rejected Callback |
| onCancelled | (String requestId, String userId) {} | Request Cancelled Callback |
| onTimeout | (String requestId, String userId) {} | Request Timeout Callback |
| onError | (String requestId, String userId, TUIError error, String message) {} | Request Error Callback |

### TUIUserListResult

| Field | Type | Description |
| --- | --- | --- |
| nextSequence | int | Pagination Fetch Flag, if the returned nextSequence is not zero, you need to use the returned nextSequence to fetch again until it returns 0 |
| userInfoList | List<TUIUserInfo> | The user list returned by this call |

### TUIUserVoiceVolume

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| volume | int | User Volume Size |

### TUIValueCallBack<T>

| Field | Type | Description |
| --- | --- | --- |
| code | [TUIError](https://www.tencentcloud.com/document/product/647/57515#TUIError) | Error Code |
| message | String? | Error Message |
| data | T? | Return Data, example: if T is TUIUserInfo, then the data field type of TUIValueCallBack<TUIUserInfo> is TUIUserInfo |

### TUIRoomVideoEncoderParams

Video encoder params

| Field | Type | Description |
| --- | --- | --- |
| videoResolution | [TUIVideoQuality](https://www.tencentcloud.com/document/product/647/57515#74d0aadf-0c54-4a05-9e30-f40b427f1402) | Video resolution |
| resolutionMode | [TUIResolutionMode](https://www.tencentcloud.com/document/product/647/57515#TUIResolutionMode) | Video resolution mode |
| fps | int | Video capturing frame rate |
| bitrate | int | Target video bitrate |

### TUINetwork

Network Quality Information

| Field | Type | Description |
| --- | --- | --- |
| userId | String | User ID |
| quality | [TUINetworkQuality](https://www.tencentcloud.com/document/product/647/57515#NetworkQuality) | Network Quality |
| upLoss | int | Packet Loss Rate for Upstream |
| downLoss | int | Packet Loss Rate for Downstream |
| delay | int | Network Delay |

### TUIMessage

Message

| Field | Type | Description |
| --- | --- | --- |
| messageId | String | Message ID |
| message | String | Message Text |
| timestamp | int | Message Timestamp |
| userId | String | Message Sender |
| userName | String | Message Sender Nickname |
| avatarUrl | String | Message Sender Avatar |

### TUIImageBuffer

Image Info

| Field | Type | Description |
| --- | --- | --- |
| buffer | String | Image Data Cache Address |
| length | int | Length |
| width | int | Width |
| height | int | Height |


---
*Source: [https://trtc.io/document/57515](https://trtc.io/document/57515)*
