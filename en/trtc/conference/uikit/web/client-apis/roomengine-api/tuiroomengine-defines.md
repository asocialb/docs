# TUIRoomEngine Defines

Introduction to Key Type Definition of TUIRoomEnigne web side.

## Enumeration Value

### TUIRole

User Role, TUIRoomEngine provides three user roles, which are Host, Administrator, and Regular User.

| Field | Type | Description |
| --- | --- | --- |
| kRoomOwner | number | Host Role |
| kAdministrator | number | Administrator Role |
| kGeneralUser | number | Regular User Role |

### TUIVideoProfile

Video Resolution

| Field | Type | Description |
| --- | --- | --- |
| kLowDefinition | number | Low Resolution |
| kStandardDefinition | number | SD |
| kHighDefinition | number | HD |
| kSuperDefinition | number | Ultra HD |

### TUIAudioProfile

Audio Resolution

| Field | Type | Description |
| --- | --- | --- |
| kAudioProfileSpeech | number | Voice Mode |
| kAudioProfileDefault | number | Standard Mode (Default Mode) |
| kAudioProfileMusic | number | Music Mode |

### TUIVideoStreamType

Streams Type

| Field | Type | Description |
| --- | --- | --- |
| kCameraStream | number | Camera Streams |
| kScreenStream | number | Screen Sharing Streams |
| kCameraStreamLow | number | Low Resolution Camera Streams |

### TUINetworkQuality

Network Status

| Field | Type | Description |
| --- | --- | --- |
| kQualityUnknown | number | Network Condition Unknown |
| kQualityExcellent | number | Network Condition Excellent |
| kQualityGood | number | Network Condition Good |
| kQualityPoor | number | Network Condition Fair |
| kQualityBad | number | Network Condition Poor |
| kQualityVeryBad | number | Network Condition Very Poor |
| kQualityDown | number | Network Connection Disconnected |

### TUIRoomType

Room Type

| Field | Type | Description |
| --- | --- | --- |
| kGroup | number | Group Type Room, suitable for conference and educational scene, the microphone position in this room is unordered and has no quantity limit |
| kOpen | number | Open Type Room, suitable for live streaming scene, the microphone position in this room is ordered and has a quantity limit |

### TUISpeechMode

Speech Type

| Field | Type | Description |
| --- | --- | --- |
| kFreeToSpeak | number | Free Speech Mode |
| kApplyToSpeak | number | Hand-raising Speech Mode |
| kSpeakAfterTakingSeat | number | Speak After Sitting (Grab Microphone Position) |

### TUICaptureSourceType

Screen Sharing Type

| Field | Type | Description |
| --- | --- | --- |
| kWindow | number | Sharing Target is a specific Windows or Mac window todo (only for electron) |
| kScreen | number | Sharing Target is the entire Windows desktop or Mac desktop |

### TUIChangeReason

Change Reason (Audio and Video Status Change Operation Reason: Self-initiated modification or modified by room owner/administrator)

| Field | Type | Description |
| --- | --- | --- |
| kChangedBySelf | number | Self-operation |
| kChangedByAdmin | number | Room Owner or Administrator Operation |

### TUIRequestAction

Room Type

| Field | Type | Description |
| --- | --- | --- |
| kInvalidAction | number | Invalid Operation |
| kRequestToOpenRemoteCamera | number | Request Remote Camera On |
| kRequestToOpenRemoteMicrophone | number | Request Remote Mic On |
| kRequestToConnectOtherRoom | number | Request Remote Cross-room Streaming, web side temporarily unsupported |
| kRequestToTakeSeat | number | Request Go Live |
| kRequestRemoteUserOnSeat | number | Request Remote Go Live |

### TUIRequestCallbackType

Request Type

| Field | Type | Description |
| --- | --- | --- |
| kRequestAccepted | number | Peer Accepted |
| kRequestRejected | number | Peer Rejected |
| kRequestCancelled | number | Request Canceled |
| kRequestTimeout | number | Request Timeout |
| kRequestError | number | Request Error |

## Type Definition

### TUIRoomInfo

Room data, user can use roomEngine.getRoomInfo to get room data.

| Field | Type | Description |
| --- | --- | --- |
| roomId | string | Room Number, String Type Room Number |
| roomType | [TUIRoomType](/document/product/647/54876#d149b153-35ff-4cab-84cb-c8d0009e179f) | Room Type |
| owner | string | Host's userId |
| name | string | Room ID |
| createTime | string | Creation time |
| roomMemberCount | number | Current total number of people in the room |
| maxSeatCount | number | Maximum number of microphone positions in the room |
| enableVideo | boolean | Allow users to join and turn on Audio |
| enableAudio | boolean | Allow users to join and turn on Video |
| enableMessage | boolean | Allow users to join and send messages |
| enableSeatControl | boolean | Enable microphone position control |

### TUIUserInfo

User Information

| Field | Type | Description |
| --- | --- | --- |
| userId | string | User Id |
| userName | string | User Name |
| avatarUrl | string | User Avatar |
| userRole | [TUIRole](/document/product/647/54876#ca95b9a1-9ce7-4f90-9d05-caef5616592d) | User Role |
| hasAudioStream | boolean | Whether there are Audio streams |
| hasVideoStream | boolean | Whether there are Video streams |
| hasScreenStream | boolean | Whether there is Screen Sharing stream |

### TUIMessage

Message Information

| Field | Type | Description |
| --- | --- | --- |
| messageId | string | Message Id |
| message | string | Message |
| timestamp | number | Timestamp information, accurate to seconds |
| userId | string | User Id |
| userName | string | User name |
| avatarUrl | string | User Avatar |

### TUIRequest

Request Information

| Field | Type | Description |
| --- | --- | --- |
| requestAction | [TUIRequestAction](/document/product/647/54876#e2746642-b1ff-453c-bb41-ca4c64c75566) | Request Type |
| timestamp | number | Request Initiation Time |
| requestId | string | Request Idv1.0.2 and above versions requestId type is string;v1.0.0 and v1.0.1 versions requestId type is number; |
| userId | string | Initiate Request's User Id |
| content | string | Other Content |

### TUIRequestCallback

Request Callback Information

| Field | Type | Description |
| --- | --- | --- |
| requestCallbackType | [TUIRequestCallbackType](/document/product/647/54876#a0211e22-30e2-4b3a-bc89-1cf1aa816695) | Request Callback Type, Accept/Reject/Cancel/Timeout/Error |
| requestId | string | Request Idv1.0.2 and above versions requestId type is string;v1.0.0 and v1.0.1 versions requestId type is number; |
| userId | string | User Id |
| code | number | Request Response Code |
| message | string | Request Status Supplemental Description |

### TUISeatInfo

Microphone Position Information

| Field | Type | Description |
| --- | --- | --- |
| index | number | Microphone Position Number |
| userId | string | Microphone Position Correspondence's User Id |
| locked | boolean | Whether the current microphone position is locked |
| videoMuted | boolean | Whether the current microphone position prohibits Video |
| audioMuted | boolean | Whether the current microphone position prohibits Audio |


---
*Source: [https://trtc.io/document/54876](https://trtc.io/document/54876)*
