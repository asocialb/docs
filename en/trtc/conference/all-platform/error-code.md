# Error Code

## General Error Code

| Error Code | Description |
| --- | --- |
| 0 | Operation Successful |
| -1 | Temporarily Unclassified General Error |
| -2 | Request Rate Limited, Please Try Again Later |
| -1000 | Not Found SDKAppID, Please Confirm Application Info in [TRTC Console](https://console.tencentcloud.com/trtc/allapp) |
| -1001 | Passing illegal parameters when calling API, check if the parameters are legal |
| -1002 | Not Logged In, Please Call Login API |
| -1003 | Failed to Obtain Permission, Unauthorized Audio/Video Permission, Please Check if Device Permission is Enabled |
| -1004 | This feature requires additional Package, please enable the corresponding Package as needed |

### Local User Rendering, Video Management, Audio Management API Callback Error Definition

| Error Code | Description |
| --- | --- |
| -1100 | System Issue, Failed to Open Camera. Check if Camera Device is Normal |
| -1101 | Camera has No System Authorization, Check System Authorization |
| -1102 | Camera is Occupied, Check if Other Process is Using Camera |
| -1103 | No Camera Device Currently, Please Insert Camera Device to Solve the Problem |
| -1104 | System Issue, Failed to Open Mic. Check if Mic Device is Normal |
| -1105 | Mic has No System Authorization, Check System Authorization |
| -1106 | Mic is Occupied |
| -1107 | No Mic Device Currently |
| -1108 | Failed to Obtain Screen Sharing Object, Check Screen Recording Permission |
| -1109 | Failed to Enable Screen Sharing, Check if Someone is Already Screen Sharing in the Room |

### Room Management Related API Callback Error Definition

| Error Code | Description |
| --- | --- |
| -2100 | Room Does Not Exist When Entering, May Have Been Closed |
| -2101 | This Feature Can Only Be Used After Entering the Room |
| -2102 | Room Owner Does Not Support Leaving the Room, Conference Room Type: Transfer Room Ownership First, Then Leave the Room. Living Room Type: Room Owner Can Only Close the Room |
| -2103 | This Operation is Not Supported in the Current Room Type |
| -2104 | This Operation is Not Supported in the Current Speaking Mode |
| -2105 | Illegal Custom Room ID, Must Be Printable ASCII Characters (0x20-0x7e), Up to 48 Bytes Long |
| -2106 | Room ID is Already in Use, Please Choose Another Room ID |
| -2107 | Illegal Room Name, Maximum 30 Bytes, Must Be UTF-8 Encoding if Contains Chinese Characters |
| -2108 | User is Already in Another Room, Single RoomEngine Instance Only Supports User Entering One Room, To Enter Different Room, Please Leave the Room or Use New RoomEngine Instance |

### Room User Information API Callback Error Definition

| Error Code | Description |
| --- | --- |
| -2200 | User Not Found |
| -2201 | User Not Found in the Room |

### Room User Speech Management API Callback Error Definition & Room Mic Seat Management API Callback Error Definition

| Error Code | Description |
| --- | --- |
| -2300 | Room Owner Permission Required for Operation |
| -2301 | Room Owner or Administrator Permission Required for Operation |
| -2310 | No Permission for Signaling Request, e.g. Canceling an Invite Not Initiated by Yourself |
| -2311 | Signaling Request ID is Invalid or Has Been Processed |
| -2340 | Maximum Mic Seat Exceeds Package Quantity Limit |
| -2341 | Current User is Already on Mic Seat |
| -2342 | Mic Seat is Already Occupied |
| -2343 | Mic Seat is Locked |
| -2344 | Mic Seat Serial Number Does Not Exist |
| -2345 | Current User is Not on Mic |
| -2346 | Mic-on Capacity is Full |
| -2360 | Current Mic Seat Audio is Locked |
| -2361 | Need to Apply to Room Owner or Administrator to Open Mic |
| -2370 | Current Mic Seat Video is Locked, Need Room Owner to Unlock Mic Seat Before Opening Camera |
| -2371 | Need to Apply to Room Owner or Administrator to Open Camera |
| -2380 | All Members Muted in the Current Room |
| -2381 | You Have Been Muted in the Current Room |


---
*Source: [https://trtc.io/document/57276](https://trtc.io/document/57276)*
