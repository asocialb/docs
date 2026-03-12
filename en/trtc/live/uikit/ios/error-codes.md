#  Error Codes

## General Error Code

| Error Code | Description |
| --- | --- |
| 0 | Operation Successful. |
| -1 | Temporarily Unclassified General Error. |
| -2 | `Request Rate` limited, please try again later. |
| -3 | Repeat Operation. |
| -1000 | Not Found `SDKAppID`, Please Confirm Application Info in [TRTC Console](https://console.tencentcloud.com/trtc/allapp). |
| -1001 | Passing illegal parameters when calling API, check if the parameters are legal. |
| -1002 | Not logged in, please call `Login` API. |
| -1003 | Failed to obtain permission, unauthorized audio/video permission, please check if `Device Permission` is enabled. |
| -1004 | This feature requires an additional package. Please activate the corresponding package as needed in the [TRTC Console](https://console.tencentcloud.com/trtc/allapp). |
| -3301 | Network access is restricted. Please [contact us](https://trtc.io/contact) for support. |

### Local User Rendering, Video Management, Audio Management API Callback Error Definition

| Error Code | Description |
| --- | --- |
| -1100 | System issue, failed to open camera. Check if camera device functions well. |
| -1101 | Camera has no system authorization, please check system authorization. |
| -1102 | Camera is occupied. Check if other process is using camera. |
| -1103 | No camera device currently, please insert camera device to solve the problem. |
| -1104 | System issue, failed to open mic. Check if mic device functions well. |
| -1105 | Mic has no system authorization, check system authorization. |
| -1106 | Mic is occupied. |
| -1107 | No mic device currently. |
| -1108 | Failed to obtain screen sharing object, check screen recording permission. |
| -1109 | Failed to enable screen sharing, check if someone is already screen sharing in the room. |

### Room Management Related API Callback Error Definition

| Error Code | Description |
| --- | --- |
| -2101 | This feature can only be used after entering the room. |
| -2102 | Room owner does not support leaving the room, conference room type: transfer room ownership first, then leave the room. Living room type: room owner can only close the room. |
| -2103 | This operation is not supported in the current room type. |
| -2105 | Illegal Custom Room ID, must be `Printable ASCII Characters (0x20-0x7e)`, Up to **48 Bytes** Long. |
| -2107 | Illegal Room Name, maximum **30 Bytes**. Must Be `UTF-8 Encoding` if contains Chinese characters. |
| -2108 | User is already in another room, single roomengine instance only supports user entering one room, to enter different room, please leave the room or use new roomengine instance |

### Room User Information API Callback Error Definition

| Error Code | Description |
| --- | --- |
| -2200 | User Not Found. |

### Room User Speech Management API Callback Error Definition & Room Mic Seat Management API Callback Error Definition

| Error Code | Description |
| --- | --- |
| -2300 | Room owner permission required for operation. |
| -2301 | Room owner or administrator permission required for operation. |
| -2310 | No permission for signaling request, e.g. canceling an invite not initiated by yourself. |
| -2311 | Signaling request id is invalid or has been processed. |
| -2312 | Signal request repetition. |
| -2340 | Maximum mic seat exceeds package quantity limit. |
| -2344 | Mic seat serial number does not exist. |
| -2360 | Current mic seat audio is locked. |
| -2361 | Need to apply to room owner or administrator to open mic. |
| -2370 | Current mic seat video is locked, need room owner to unlock mic seat before opening camera. |
| -2371 | Need to apply to room owner or administrator to open camera. |
| -2372 | The current microphone position video is locked and needs to be unlocked by the room owner before screen sharing can be enabled. |
| -2373 | Screen sharing needs to be enabled after applying to the room owner or administrator. |
| -2380 | All members muted in the current room. |
| -2381 | You have been muted in the current room. |

## Definition Of Room Preload API Callback Error

| Error code | Description |
| --- | --- |
| -4001 | The current room does not support preloading. |

## Common Error Codes for RESTful APIs

| Error code | Description |
| --- | --- |
| 60002 | `HTTP` parsing error, please check the `HTTP` request `URL` format. |
| 60003 | HTTP request `JSON` parsing error, please check the `JSON` format. |
| 60004 | Request `URL` or `JSON` payload contains an incorrect account or signature. |
| 60005 | Request `URL` or `JSON` payload contains an incorrect account or signature. |
| 60006 | `SDKAppID` invalid, please verify the validity of `SDKAppID`. |
| 60007 | `RESTful API` invocation frequency exceeds its limit, please reduce the request frequency. |
| 60008 | Service request timed out or `HTTP` request format is incorrect, please check and retry. |
| 60009 | Request Resource Error, please check the request `URL`. |
| 60010 | The request requires App administrator privileges. |
| 60011 | `SDKAppID` request frequency exceeds the limit, please reduce the request frequency. |
| 60012 | `RESTful API` requires `SDKAppID`, please check the `SDKAppID` in the request `URL`. |
| 60013 | `HTTP` response package `JSON` parsing error. |
| 60014 | Account Replacement timed out. |
| 60015 | The request body has the wrong account type. Please ensure the account is in string format. |
| 60016 | `SDKAppID` is disabled. |
| 60017 | The request is disabled. |
| 60018 | The request is too frequent, please try again later. |
| 60019 | The request is too frequent, please try again later. |
| 60020 | Your Professional Edition package has expired and been deactivated. Please  log in to [Chat  purchase page](https://buy.tencentcloud.com/avc) to repurchase the package. Once purchased, it will take effect 5 minutes later. |
| 60021 | Calling `Source IP` for `RestAPI` is illegal. |

## Error codes

Common error codes (60000 to 79999) see [Error Code](https://intl.cloud.tencent.com/document/product/1047/34348) documentation.
The private error codes for this API are as follows:

| Error Code | Explanation |
| --- | --- |
| 100001 | Server internal error, please retry. |
| 100002 | The parameter is illegal. Check whether the request is correct according to the error description. |
| 100003 | The room ID already exists. Please select another room ID. |
| 100004 | The room does not exist, or it once existed but has now been dissolved. |
| 100005 | Not a room member. |
| 100006 | Insufficient operation permissions. |
| 100007 | No payment information; you need to purchase a package in the console. |
| 100008 | The room is full. |
| 100009 | Tag quantity exceeds upper limit. |
| 100010 | The room ID has been used, and the operator is the room owner; it can be used directly. |
| 100011 | The room ID has been occupied by Chat. You can use a different room ID or dissolve the group first. |
| 100012 | Creating rooms exceeds the frequency limit; the same room ID can only be created once within 1 second. |
| 100013 | Exceeds the upper limit, for example, the number of microphone seats, the number of PK match rooms, etc., exceeds the payment limit. |
| 100015 | Invalid room type. |
| 100016 | This member has been banned. |
| 100017 | This member has been muted. |
| 100018 | The current room requires a password for entry. |
| 100019 | Room Entry Password Error. |
| 100020 | The admin quantity exceeds the upper limit. |
| 100102 | Signal request conflict. |
| 100200 | The mic seat is locked. You can try another mic seat. |
| 100201 | The current seat is already occupied. |
| 100202 | Already on the mic queue. |
| 100203 | Already on the mic. |
| 100204 | Not on the mic queue. |
| 100205 | The seats are all taken. |
| 100206 | Not on the mic seat. |
| 100210 | The user is already on the mic seat. |
| 100211 | The room does not support mic ability. |
| 100251 | The seat list is empty. |
| 100400 | The current connection does not exist or has ended. |
| 100401 | The room is already in connection. |
| 100402 | There is a pending connection request for this room. |
| 100403 | The current room is connecting with other rooms. |
| 100404 | The room number has exceeded the limit in connection or battle. |
| 100405 | Creating connections too frequent in a short time. Wait a moment and try again. |
| 100411 | The battle does not exist or has ended. |
| 100412 | None of the rooms in the battle is valid. |
| 100413 | Creating battles too frequently. Wait a moment and try again. |
| 100414 | The room isn't in the battle. |
| 100415 | The room is already in other battle. |
| 100416 | There is a pending battle request for this room. |
| 100419 | It's not allowed to cancel battle for room in battle. |
| 100420 | The battle has not started yet. |
| 100421 | The battle session has ended. |
| 100500 | The number of keys in the room's `Metadata` exceeds the limit. |
| 100501 | The size of value in the room's `Metadata` exceeds the maximum byte limit. |
| 100502 | The total size of all value in the room's `Metadata` exceeds the maximum byte limit. |
| 100503 | There is no valid keys when delete `Metadata`. |
| 100504 | The size of key in the room's `Metadata` exceeds the maximum byte limit. |


---
*Source: [https://trtc.io/document/60027](https://trtc.io/document/60027)*
