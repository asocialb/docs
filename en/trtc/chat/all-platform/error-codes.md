# Error Codes

## 1. Chat SDK Error Codes

> **Note:**For web SDK error codes, see [here](https://web.sdk.qcloud.com/im/doc/en/module-ERROR_CODE.html).

### Common error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 6015 | Cancel the current request because the last request is running. | Do not make repeated calls in parallel. Wait for the previous API callback before making the next call (for example: clear conversation unread count, handle pending group message, retrieve blocklist, and other API interfaces). |
| 6017 | Invalid parameter. Check the error information to locate the invalid parameter. | Refer to [Chat official documentation parameter description](https://www.tencentcloud.com/document/product/1047/36169).If unresolved, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 6022 | Local I/O operation error. Check whether you have the read/write permission or whether the disk is full. | This error code usually indicates a permission problem, disk remaining space shortage and other issues. It is advisable to perform troubleshooting based on the error prompt. |
| 6027 | Incorrect JSON format. Check the error information to locate the specific field. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 6028 | Insufficient memory. A memory leak may occur. Analyze and identify the location with high memory usage by using the Instrument tool on the iOS platform or the Profiler tool on the Android platform. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 6001 | PB parsing failed. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 6002 | PB serialization failed. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 6013 | The Chat SDK has not been initialized. Try again after the Chat SDK is initialized and the response is returned through callback. | Please first call the initSDK API to initialize. |
| 6005 | Failed to load the local database, possibly due to file corruption. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 6019 | Operation on the local database failed. This error may be caused by a lack of permissions for some directories or file corruption in the database. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7001 | Cross-thread error. Cross-thread operations are not supported. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7002 | TinyId is empty. Internal error. Check whether the UserID exists and is valid. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7003 | Invalid UserID. | Please confirm if the UserID is empty and whether its length exceeds 32 bytes. |
| 7004 | The file does not exist. Check whether the file path is correct. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7005 | Send a rich media message. The file size exceeds the limit. | Confirm the file size:Voice, image, maximum limit 28MBVideo, file, maximum limit 100MB |
| 7006 | Send rich media message. File invalid. | Confirm that the file is not empty and the file size is not 0 bytes. |
| 7007 | Failed to open the file. Check whether the file exists or has been opened exclusively, which causes the SDK to fail to open it. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7008 | Exceeded the API call frequency limit. Check and control the API call frequency. | Do not repeat high-frequency calls to the SDK API, or provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7009 | The ongoing operation was unexpectedly terminated due to the invocation of the unInitSDK interface. For example, if a login is in progress and the unInitSDK interface is called, the login operation will be terminated. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7010 | The database operation failed. | Please first call the `login` API to log in, then reoperate. |
| 7011 | The queried data does not exist in the database. | Please confirm the corresponding data is cached locally. |
| 7012 | An internal error occurred in the SDK. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7013 | The current package does not support this API. Please upgrade to the Pro edition ãPro Plus edition or Enterprise edition package. | Please [upgrade bundle](https://www.tencentcloud.com/document/product/1047/55096#.E5.8A.9F.E8.83.BD.E5.8C.85.E5.8D.87.E7.BA.A7). |
| 7014 | Invalid request. Check the API call meets requirements. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7015 | Sensitive words found in SDK local content moderation. | Confirm the sensitive word settings. |

### Account error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 6014 | You have not logged in to the Chat SDK or have been forcibly logged out. Log in to the Chat SDK first and try again after a successful callback. To check whether you are online, use TIMManager getLoginUser. | Please first call the login API, then reoperate. |
| 6206 | UserSig has expired. | Get a new valid UserSig and log in again. For more information about how to get a UserSig, see [Generating UserSig](https://intl.cloud.tencent.com/document/product/1047/34385). |
| 6208 | You have been logged out because your account is logged in on another device. Please log in again. | If not in multi-device login with the same account, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 7503 | Failed to initialize the TLS SDK. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7504 | The TLS SDK has not been initialized. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7505 | The TRANS packet format of the TLS SDK is incorrect. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7506 | Failed to decrypt the TLS SDK. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7507 | Failed to send the request to the TLS SDK. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 7508 | Request to the TLS SDK timed out. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |

### Message error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 6004 | The session does not exist. | Please confirm whether the session exists locally. |
| 6006 | File transfer authentication failed. We recommend that you check whether the file format is correct. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 6007 | Failed to get the server list via FTP. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 6008 | File transfer failed to retrieve the Server list. | Please confirm whether Chat is connected. If the uploaded file is an image, confirm it can open |
| 6009 | Send rich media message. File upload failed. | Check whether your network is connected or whether the file or audio has expired. Currently, resource files are stored for up to 7 days. |
| 6010 | HTTP request failed. | Check whether the URL is valid. You can try to visit the URL via a web browser. |
| 6016 | Invalid message elem of the Chat SDK. | Define the field based on the returned error information. |
| 6031 | Failed to upload the file. | Check whether the uploaded image can be opened properly. |
| 6032 | Invalid message receiver. | Please check whether the message receiver exists in the Console. |
| 8001 | The message overall length exceeds the limit. | The message length must not exceed 12K. The message length is the sum of each elem length, and the elem length is the sum of all elem field lengths. |
| 8002 | Message key error. This is an internal error. The key of the network request packet is not consistent with that of the response packet. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 8003 | The image conversion HTTP request failed. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 8004 | Thumbnail conversion failed due to reasons such as CI pornographic recognition. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 8005 | The nested level of merged forwarding messages exceeds the limit. | Please confirm whether the nested level exceeds 100. |
| 8006 | Message modification conflict. The message that you request to modify is modified by another user. | Get the error message body, re-edit and retry. |
| 8010 | Invalid signaling ID. | Please ensure the signaling ID is correct and hasn't been processed. |
| 8011 | The signaling request is not authorized. | Please confirm permission to perform operations, such as canceling invitations not initiated by yourself. |
| 8012 | The signaling invitation already exists. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 8020 | Failed to cancel sending message. | Please ensure the message exists and is not sent successfully. |
| 8021 | Failed to send the message. | Please confirm whether it is caused by calling the "cancel sending" API. |

### Group error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 8501 | Invalid group ID (unique group identifier). | A custom group ID must be printable ASCII characters (0x20-0x7e) containing up to 48 bytes in length. To avoid confusion with the default group IDs assigned by Chat, a custom group ID cannot be prefixed with @TGS#. |
| 8502 | Invalid group name. | A group name can be up to 30 bytes in length and must be encoded in UTF-8. If the group name contains a Chinese character, the Chinese character may be expressed in multiple bytes. Check the length of the string in bytes. |
| 8503 | Invalid group introduction. | A group introduction can be up to 240 bytes in length and must be encoded in UTF-8. If the group introduction contains a Chinese character, the Chinese character may be expressed in multiple bytes. Check the length of the string in bytes. |
| 8504 | Invalid group notice. | A group notice can be up to 300 bytes in length and must be encoded in UTF-8. If the group notice contains a Chinese character, the Chinese character may be expressed in multiple bytes. Check the length of the string in bytes. |
| 8505 | Invalid URL of the group profile photo. | The URL of a group profile photo can be up to 100 bytes in length. You can try to access the URL via a web browser. |
| 8506 | Invalid group name card. | A group name card can be up to 50 bytes in length and must be encoded in UTF-8. If the group name card contains a Chinese character, the Chinese character may be expressed in multiple bytes. Check the length of the string in bytes. |
| 8507 | The number of participants exceeds the limit on the number of group members. | Maximum number of group members: 200 for Standard Version, 2,000 for Pro Edition, 5,000 for Pro Edition Plus, 6,000 for Enterprise Edition. BChatRoom and Online Member Broadcast Group have no limit. |
| 8508 | A private group cannot be joined via app. | Private group does not support join requests by default. You can modify group information to update the default configuration. |
| 8509 | You cannot invite a group member whose role is group owner. | Ensure that the role field is entered correctly. |
| 8510 | You cannot invite 0 members. | Ensure that the member field is entered correctly. |
| 8511 | API call frequency for group attributes exceeds the limit. | Group attribute Create, Delete, and Update APIs are restricted to 5 calls per second in the backend. Read APIs are limited to 20 calls every 5 seconds in the SDK. |
| 8512 | API call frequency for group online users exceeds the limit. | SDK API rate limit: 1 time per 60 seconds. |
| 8513 | API call frequency for Group Profile exceeds the limit. | SDK API rate limit: 1 time per second. |
| 8514 | API call frequency for join group list exceeds the limit. | SDK API rate limit: 1 time per second. |

### Relationship chain error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 9001 | Invalid data field. | The material supports standard fields and custom fields. Among them, the keyword of a custom field must be English letters and its length should not exceed 8 bytes. The value of a custom field has a maximum limit not to exceed 500 bytes. |
| 9002 | Invalid remark field. | Maximum 96 bytes, character encoding must be UTF-8. If containing Chinese, a single Chinese character may use multiple bytes. Check the byte length of the string. |
| 9003 | Invalid request description field for friend request. | Maximum 120 bytes, character encoding must be UTF-8. If containing Chinese, a single Chinese character may use multiple bytes. Check the byte length of the string. |
| 9004 | Invalid source field for friend request. | The source needs to be added with the "AddSource_Type_" prefix. |
| 9005 | Friend grouping field illegal. | Must not be empty. The name of each group must be no longer than 30 bytes, character encoding must be UTF-8. If containing Chinese, a single Chinese character may use multiple bytes. Check the byte length of the string. |

### Network error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 9501 | SSO encryption failed. Internal error. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9502 | SSO decryption failed. Internal error. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9503 | SSO has not been authenticated. The login process may not be completed. Complete the login process and then try again. | Please retry after successful log-in. |
| 9504 | Failed to compress the data packet. Internal error. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9505 | Failed to decompress the data packet. Internal error. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9506 | The call frequency exceeds the frequency limit. | Please confirm whether there is a high frequency of calling the SDK API, with a maximum of 5 requests initiated per second. |
| 9507 | The network request queue exceeds the maximum number (1,000) of concurrent requests allowed. For example, when users keep sending messages when the network is abnormal, the network request queue will keep adding new requests without consumption and quickly reach the maximum number of requests. | Check whether the current network is available, or switch to another network and retry. |
| 9508 | The network is disconnected, no connection has been set up, or no network is detected when setting up a socket connection. | Please ensure the network is available. |
| 9509 | A network connection has been established, but is created repeatedly. Internal error. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9510 | Network connection setup timed out. Try again after the network recovers. | Check whether the network is functioning normally or switch networks and retry. If other requests are available but only Chat is unavailable, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9511 | The network connection setup has been rejected by the server due to frequent connection requests. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9512 | No available route to the network. Try again after the network recovers. | Please ensure the network is available. |
| 9513 | Insufficient buffer capacity for calls. The system is too busy. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 9514 | The peer end has reset the connection, possibly because the server is overloaded. The SDK automatically initiates reconnection. Try again after the network is reconnected and the callback function `onConnSucc` on iOS or `onConnected` on Android is called successfully. | Retry, or contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9515 | Invalid socket. Internal error. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 9516 | Domain resolution failed. Multiple strategies have been attempted, but the connection could not be established. | Check your network connection or try a different network. If other services work normally but Chat doesn't, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for assistance. |
| 9517 | Invalid connection. The network is connected to an intermediate node or is reset by the server. This is an internal error. The SDK automatically initiates reconnection. Try again after the network is reconnected and the callback function `onConnSucc` on iOS or `onConnected` on Android is called successfully. | Retry, or contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9518 | The request packet timed out when waiting to enter the sending queue. This usually occurs when the network connection setup is slow or the network is frequently disconnected and reconnected. Check whether the network connection is normal. | Check whether the network is functioning normally or switch networks and retry. If other requests are available but only Chat is unavailable, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9519 | The request packet entered the Chat SDK sending queue but timed out while waiting to enter the network layer of the operating system. This usually occurs when the local network is restricted or disconnected or the local network and the Chat SDK backend are not connected. We recommend that you run the Chat SDK in different network environments to check whether this issue is caused by the current network environment. | Check whether the network is functioning normally or switch networks and retry. If other requests are available but only Chat is unavailable, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9520 | The request packet entered the network layer of the operating system from the Chat SDK sending queue but timed out while waiting for a response packet from the server. This usually occurs when the local network is restricted or disconnected or the local network and the Chat SDK backend are not connected. We recommend that you run the Chat SDK in different network environments to check whether this issue is caused by the current network environment. | Check whether the network is functioning normally or switch networks and retry. If other requests are available but only Chat is unavailable, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9521 | The request packet has entered the sending queue, certain data has been sent, but the remaining data timed out when waiting to be sent. This usually occurs because the upstream bandwidth is insufficient or the network is connected when the error is called back. Please check whether the network connection is normal. | Check whether the network is functioning normally or switch networks and retry. If other requests are available but only Chat is unavailable, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9522 | The request packet length exceeds the maximum limit of 1 MB. | Please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |
| 9523 | The request packet has entered the sending queue but timed out when waiting to enter the network buffer of the system. This usually occurs because too many packets are to be sent, the sending thread is too busy to handle the packets, or the network is disconnected when the error code is called back. | Check whether the network is functioning normally or switch networks and retry. If other requests are available but only Chat is unavailable, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9524 | The request packet has entered the network buffer of the system but timed out when waiting for the server to return packets. This usually occurs because the request packet does not leave the client device, is discarded in an intermediate route, or is dropped accidentally by the server, the response packet is discarded by the network layer of the system, or the network is disconnected when the error code is called back. | Check whether the network is functioning normally or switch networks and retry. If other requests are available but only Chat is unavailable, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 9525 | The request packet has entered the sending queue, certain data has been sent, but the remaining data timed out when waiting to be sent. This usually occurs because the upstream bandwidth is insufficient or the network is disconnected when the error code is called back. Please check whether the network connection is normal. | Check whether the network is functioning normally or switch networks and retry. If other requests are available but only Chat is unavailable, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |

## 2. Server Error Codes

### Access layer error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| -302 | The number of server connections exceeds the limit. The server refused to provide services. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| -10001 | Key expired. A key is an internal credential generated based on the UserSig. The validity period of a key is less than or equal to that of the UserSig. | Call the `TIMManager.getInstance().login` API again to generate a new key. |
| -10003 | Ticket expired. A ticket is an internal credential generated based on the UserSig. The validity period of a ticket is less than or equal to that of the UserSig. | Call the `TIMManager.getInstance().login` API again to generate a new ticket. |
| -10004 | Ticket verification failed. | Call the `TIMManager.getInstance().login` API again to generate a new ticket. |
| -10005 | The key cannot be empty. | Call TIMManager.getInstance().login again to generate a Key. |
| -10006 | The account in `Key` does not match the account in the request packet header. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| -10007 | Verification code delivery timed out. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| -10008 | The key and ticket are required. | Call the `TIMManager.getInstance().login` API again to generate a Key and Ticket. |
| -10009 | Cookie mismatch. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| -10106 | Decryption failure count exceeds threshold, notify the terminal to reset. | Call the `TIMManager.getInstance().login` API again to generate a new Key. |
| -10108 | Prepaid arrears. | - |
| -10109 | Request packet format error. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| -10110 | The SDKAppID is in the blocklist. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| -10111 | The SDKAppID accesses the blocklist API. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| -10113 | The request exceeds the frequency limit allowed for the user. The frequency limit is set for the number of requests per second based on a specific protocol. | Please check whether the API call frequency is reasonable. |
| -10114 | Packet loss due to system overload. The connected server has too many requests to process and therefore refuses to provide services. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| -20009 | The frequency of terminals accessing APIs exceeds the limit. | Please check whether the API call frequency is reasonable. |

### Resource file error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 114011 | Invalid parameter. | Please check whether the parameters in the SDK API calls are correct.If unable to confirm, please provide logs to [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) for troubleshooting. |

### Common backend error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 60002 | HTTP parsing error. | Please check the HTTP Request URL Format. |
| 60003 | HTTP request JSON parsing error. | Please check the package JSON format. |
| 60004 | Account check failed. | Please retry later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 60005 | Account check failed. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 60007 | REST API call frequency exceeds the limit. | Please upgrade the API rate limit via the console or reduce the request frequency. |
| 60008 | Service request timeout or HTTP request format error. | Check the request and retry. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 60009 | Request resource error. | Check the request URL. |
| 60010 | The request requires App administrator permissions. | Check whether the request Identifier is an admin. |
| 60012 | The RESTful API requires the SDKAppID. | Check the SDKAppID in the request URL. |
| 60013 | HTTP response packet JSON parsing error. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 60014 | Account check timeout. | Check the request and retry. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 60015 | Request packet body UserID type error. | Please confirm UserID is in string format. |
| 60016 | The SDKAppID is disabled. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 60017 | The request is disabled. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 60018 | Requests are too frequent. Please try again later. | Please check whether the API call frequency is reasonable. |
| 60020 | Service unavailable. | If the basic service plan is not purchased or has expired and become invalid, [purchase](https://buy.tencentcloud.com/avc) a basic service plan. If the Tencent Cloud account is in arrears, [top up](https://www.tencentcloud.com/document/product/555/11319) to pay off. |
| 60021 | Server-side REST API call source IP illegal. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 60025 | Server-side REST API call SDKAppID, Identifier, UserSig, or ContentType error, please check URL parameter. | Check the URL parameter. |
| 60026 | Server-side REST API call domain name or SDKAppID mismatched with the application station. | Please check the consistency between the SDKAppID and the domain name of the Chat data cent |
| 60027 | Access to non-TPush product resources not allowed. | Please check the Consistency between the product type of created products and the RESTful APIs. |
| 60028 | Server-side REST API request volume exceeds Trial Edition limits within 24 hours. | - |
| 80001 | The text in the message or material contains sensitive content and cannot be delivered. | Check content to be sent for sensitive information. |
| 80002 | Message packet body too long. Currently supports a maximum message body length of 12K. Reduce packet size and retry. | Reduce packet size and retry. |
| 80003 | If the message pre-callback for C2C Messages or group chat fails or response packet timeout occurs, the message will not be sent. In the console, you can configure the [processing policy for callback timeout before event occurrence](https://www.tencentcloud.com/document/product/1047/34354#.E4.BA.8B.E4.BB.B6.E5.8F.91.E7.94.9F.E4.B9.8B.E5.89.8D.E5.9B.9E.E8.B0.83.E8.B6.85.E6.97.B6.E7.9A.84.E5.A4.84.E7.90.86.E7.AD.96.E7.95.A5) through self-configuration. | - |
| 80004 | The image in the message contains sensitive content and cannot be delivered. | Check content to be sent for sensitive information. |
| 80005 | Service deactivated. | If the version expires, [purchase](https://buy.tencentcloud.com/avc) or [renew](https://console.tencentcloud.com/expense/renewal) a package. If the account is in arrears, [top up](https://www.tencentcloud.com/document/product/555/11319). |

### Account error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 70001 | UserSig expired. | Regenerate. It is recommended to set the UserSig valid period to not less than 24 hours. |
| 70003 | Illegal UserSig. | Please use the API provided by the official website to [generate UserSig](https://www.tencentcloud.com/document/product/1047/34385) again. |
| 70009 | UserSig verification failed. | The UserSig may have been generated using the SecretKey or PrivateKey of another SDKAppID. Please check the Consistency between the requested SDKAppID and the key or private key used to generate UserSig. |
| 70013 | The UserID in the request differs from the one used when generating UserSig. | You can use the console [UserSig generation & verification](https://console.trtc.io/usersig) tool to verify UserSig. |
| 70014 | The SDKAppID in the request is inconsistent with the one used when generating UserSig. | You can use the console [UserSig generation & verification](https://console.trtc.io/usersig) tool to verify UserSig. |
| 70016 | PublicKey does not exist. UserSig verification failed. | Please check the consistency between the SDKAppID and the Chat data center. |
| 70020 | SDKAppID does not exist. UserSig verification failed. | Please check the consistency between the SDKAppID and the Chat data center. |
| 70050 | UserSig verification failed, and the request frequency exceeds the limit. | Please check whether the UserSig is correct and verify again after 1 minute. |
| 70051 | The account has been added to the blocklist. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 70107 | The requested user account is not imported into the Chat System. | Please import the account into the Chat System first. |
| 70169 | Server-side internal timeout. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 70402 | Illegal request parameters. | Please check whether the required field is filled or the field population meets protocol requirements. |
| 70404 | Low SDK version. | Upgrade to the latest version. |
| 70398 | Account number exceeds limit. | Upgrade the application. For specific operation guide, see [Purchase Guide](https://www.tencentcloud.com/document/product/1047/55096). |
| 70399 | For non-Chat Trial Edition applications, the account cannot be re-imported within three months after deletion. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 70500 | Internal server error. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 71000 | The current application does not support account deletion. | You can lift the restriction in the [Console](https://console.trtc.io/chat/account-management). |
| 72000 | DAU exceeds the free quota. | Your current application is the Trial Edition. DAU exceeds the free quota. To remove this restriction, upgrade the application to Standard Edition, Pro Edition, Pro Edition Plus, or Enterprise Edition. For specific operation guide, see [Purchase Guide](https://www.tencentcloud.com/document/product/1047/55096). |
| 72001 | Feature not enabled. | Activate user status query and status change notification configuration in the console. For operation guide, see [Operation Guide](https://www.tencentcloud.com/document/product/1047/49562#.E8.B0.83.E7.94.A8.E8.AE.A2.E9.98.85.2F.E5.8F.96.E6.B6.88.E8.AE.A2.E9.98.85.E6.8E.A5.E5.8F.A3.E6.97.B6.EF.BC.8C.E6.8E.A5.E5.8F.A3.E6.8F.90.E7.A4.BA-.E2.80.9D72001.E2.80.9C-.E7.9A.84.E9.94.99.E8.AF.AF.E7.A0.81). |
| 72002 | MAU exceeds the free quota. | Your current application is the Trial Edition. MAU exceeds the free quota. To remove this restriction, upgrade the application to Standard Edition, Pro Edition, Pro Edition Plus, or Enterprise Edition. For specific operation guide, see [Purchase Guide](https://www.tencentcloud.com/document/product/1047/55096). |
| 72010 | Request overfrequency. | Login, log out, switch to foreground, switch to background, and set offline push configuration requests exceed the frequency limit for single user. |
| 72011 | Feature not enabled. | Please enable the global do not disturb related configuration in [Console > Login and Messaging](https://console.trtc.io/chat/login-message). |
| 72012 | Feature not enabled. | Activate user profile change subscription configuration in the console. For specific operation guide, see [Operation Guide](https://www.tencentcloud.com/document/product/1047/48162#53edea52-35ef-4d82-aae9-941ba690f051). |

### Profile error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 40001 | Illegal request parameters. | Please check whether the required field is filled or the field population meets protocol requirements. |
| 40002 | User account for pulls of the profile is not specified. | Specify the user account for pulls of the profile. |
| 40003 | The requested user account is not imported into the Chat System. | Please import the user account into the Chat System first. |
| 40004 | The request requires App administrator permissions. | Check whether the request Identifier is an admin. |
| 40006 | Internal server error. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 40007 | No read permission for the data field. | You can change the read permission of the field in the [Console](https://console.trtc.io/chat/login-message). |
| 40008 | No write permission for the data field. | You can change the write permission of the field in the [Console](https://console.trtc.io/chat/login-message). |
| 40009 | Tag of the data field does not exist. | For more details, see [Profile Management](https://www.tencentcloud.com/document/product/1047/33520). |
| 40601 | The Value length of the data field exceeds 500 bytes. | For more details, see [Profile Management](https://www.tencentcloud.com/document/product/1047/33520). |
| 40605 | The Value of the standard profile field is invalid. | For more details, see [Profile Management](https://www.tencentcloud.com/document/product/1047/33520). |
| 40610 | The Value Type of the profile field is illegal. | For more details, see [Profile Management](https://www.tencentcloud.com/document/product/1047/33520). |

### Relationship chain error codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 30001 | Illegal request parameters. | Please check whether the required field is filled or the field population meets protocol requirements. For more information, please refer to [Error Code 30001 Description](https://www.tencentcloud.com/document/product/1047/34457#why-do-i-encounter-error-code-30001.3F). |
| 30002 | The requested user account is illegal. | The SDK may have cached the deleted account locally. It is advisable to uninstall reinstall the App and try again. |
| 30003 | The requested user account is not imported into the Chat System. | Please import the user account into the Chat System first. |
| 30004 | The request requires App administrator permissions. | Check whether the request Identifier is an admin. |
| 30005 | The current application does not have the follow and fan feature enabled. | Purchase [Pro Edition, Pro Edition Plus, or Enterprise Package](https://trtc.io/document/67650?platform=web&product=chat&menulabel=uikit#function) and activate it in the [console](https://console.trtc.io/chat/friends-diy-vars?language=zh) to use. |
| 30006 | Internal server error. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 30007 | Server-side internal timeout. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 30008 | Concurrent write operations cause write conflicts. | Recommend using batch processing. |
| 30009 | The backend forbids this user from sending a friend request. | For more details, see [standard profile field](https://www.tencentcloud.com/document/product/1047/33520#.E6.A0.87.E9.85.8D.E8.B5.84.E6.96.99.E5.AD.97.E6.AE.B5). |
| 30010 | The number of friends has reached the system limit. | You can [fetch friends](https://www.tencentcloud.com/document/product/1047/34908) to view the total number of user friends. |
| 30011 | The group has reached the upper limit. | You can [fetch groups](https://www.tencentcloud.com/document/product/1047/40123) to view the total number of user groups. |
| 30012 | The pending number has reached the system limit. | If the other party's consent is required to add as a friend, it is advisable to add no more than 100 friends per request. |
| 30013 | The blocklist has reached the system limit. | You can [fetch blocklist](https://www.tencentcloud.com/document/product/1047/34914) to view the total number of names. |
| 30014 | The other party's number of friends has reached the system limit. | You can [fetch friends](https://www.tencentcloud.com/document/product/1047/34908) to view the total number of user friends. |
| 30515 | When sending a friend request, the other party is on your blocklist. Adding a friend is not allowed. | Please first remove users from the blocklist. |
| 30516 | When sending a friend request, the other party's verification method does not allow anyone to add them as a friend. | For more details, see [standard profile field](https://www.tencentcloud.com/document/product/1047/33520#.E6.A0.87.E9.85.8D.E8.B5.84.E6.96.99.E5.AD.97.E6.AE.B5). |
| 30525 | When sending a friend request, you are on the other party's blocklist. Adding a friend is not allowed. | Please first remove users from the blocklist. |
| 30539 | You can add as a friend after the other party agrees. | A sends a friend request to B. B's verification method for adding friends is set to "AllowType_Type_NeedConfirm". At this point, A and B can only form a pending relationship. The return code is used to identify a successful pending request, so that it can be separated from the successful friend request response code. The caller can capture the error and provide users with an appropriate prompt. |
| 30614 | The friend request for processing does not exist. | Please check if there are pending friend requests. |
| 31704 | No friend relationship exists with the account requested for deletion. | You can [verify friends](https://www.tencentcloud.com/document/product/1047/34907) to check friend relationship. |
| 31804 | The pending request for deletion does not exist. | The caller can capture the error and provide users with a reasonable prompt. |
| 38000 - 39000 | The custom error code returned by the Relationship Chain third-party webhook. | - |

### Error codes for recent contacts

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 50001 | The requested user account is not imported into the Chat System. | Please import the user account into the Chat System first. |
| 50002 | Illegal request parameters. | Please check whether the required field is filled or the field population meets protocol requirements. |
| 50003 | The request requires App administrator permissions. | Check whether the request Identifier is an admin. |
| 50004 | Internal server error. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 50005 | Server-side internal timeout. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 51006 | The number of sessions requested for update is illegal. | It is advisable to keep the number of sessions per request to no more than 100. |
| 51007 | G2C session permission verification failed. | Please retry later. If it still fails, check whether the user has left the group. |
| 51008 | The number of grouped/tagged sessions has reached the upper limit. | You can [fetch conversation group mark data](https://www.tencentcloud.com/document/product/1047/53440) to view the total number of sessions. |
| 51009 | The requested conversation group does not exist. | You can [fetch conversation group mark data](https://www.tencentcloud.com/document/product/1047/53440) to view group information. |
| 51010 | The conversation group has reached the upper limit. | You can [fetch conversation group mark data](https://www.tencentcloud.com/document/product/1047/53440) to view group information. |
| 51011 | The conversation group name exceeds 32 bytes. | The group name length should not exceed 32 bytes. |
| 51012 | The number of pinned conversations has reached the upper limit. | The maximum number of pinned conversations is 50 and cannot be expanded. |

### Message Error Codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 20001 | Invalid request packet. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 20002 | UserSig or A2 expired. | Log in again. |
| 20003 | Message sender or recipient UserID is invalid or does not exist. | - |
| 20004 | Network issue. Please retry. | - |
| 20005 | Internal server error. Please retry. | - |
| 20006 | Message cannot be delivered. | Trigger the Webhook before sending a private chat message, and the App backend returns that the message cannot be delivered. |
| 20007 | The sender is blocked. Message sending is prohibited. | Send a private chat message. The other party blocked you. Sending is prohibited. The message sending status is displayed as failed by default. You can log in to the console to modify the display result in this scenario. For details, see [blocklist check](https://www.tencentcloud.com/document/product/1047/34419#blocklist-check). |
| 20008 | The sender and recipient belong to different SDKAppIDs. The reason is the client switched SDKAppID but the database was not cleared. The solution is to delete the original database when switching SDKAppID. | Clear the client cache and data, and reinstall the client. |
| 20009 | The sender and receiver are non-friends. Sending is prohibited. | The two parties are not friends, so sending is prohibited (this occurs only when friend relationship verification is configured for C2C Messages). |
| 20010 | The sender is not a friend of the recipient. Sending is prohibited. | Send private chat message. Sending is prohibited if you are not a friend of the other party (one-way relationship). |
| 20011 | The recipient is not a friend of the sender. Sending is prohibited. | Send private chat message. Sending is prohibited if the other party is not your friend (one-way relationship). |
| 20012 | The sender is muted. Sending is prohibited. | The sender is muted. The message is prohibited from sending. |
| 20016 | Exceeding the time limit for recall. | The message recall exceeds the time limit (default: 2 minutes). |
| 20018 | Internal error. | Delete roam internal error, retry. If it occurs frequently, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 20022 | Message does not exist. | The message to be revoked does not exist. Please check. |
| 20023 | Message revoked. | The message has been recalled. |
| 20027 | Message version number conflict. Get the latest message and try again. | - |
| 20028 | Concurrent message modification caused conflicts. Retry. | - |
| 21005 | Please ensure to log in before setting the token, as the token request may reach the backend before the log-in request. | - |
| 22001 | No Offline Push Certificate has been uploaded. | Enable offline push functionality on the console and upload the corresponding certificate. |
| 22002 | Network issue. Please retry. | Retry. If it occurs frequently, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 22003 | The uploaded token is empty. | The Token length is 0. Please check. |
| 22004 | The uploaded token length exceeds 256 bytes. | The set Token length is greater than 256 bytes. Please check. |
| 22006 | Request overfrequency. | Reduce the operation frequency. |
| 22007 | DAU exceeds the free quota. | Your current application is the Trial Edition or Development Edition. The number of senders exceeds the free quota. To remove this restriction, upgrade the application to Standard Edition, Pro Edition, Pro Edition Plus, or Enterprise Edition package. For specific operation guide, see [Purchase Guide](https://www.tencentcloud.com/document/product/1047/55096). |
| 90001 | JSON format parsing failed. Check whether the request packet conforms to the JSON Specification. | Use tools like JSONLint to check whether there is a syntax error in the JSON. |
| 90002 | Request format error. | The MsgBody in the JSON format request packet does not match the message format description, or MsgBody is not an Array type. Refer to the [TIMMsgElement object](https://www.tencentcloud.com/document/product/1047/33527#TIMMsgElement) definition. |
| 90003 | To_Account field error. | The JSON format request body lacks the To_Account field or the To_Account account does not exist. |
| 90005 | MsgRandom field error. | The JSON format request body lacks the MsgRandom field or the MsgRandom field is not of integer type. |
| 90006 | MsgTimeStamp field error. | The JSON format request body lacks the MsgTimeStamp field or the MsgTimeStamp field is not of integer type. |
| 90007 | MsgBody field error. | The MsgBody field in the JSON format request body is not of Array type. Please change it to Array type. |
| 90008 | From_Account field error. | The JSON format request body lacks the From_Account field or the From_Account account does not exist. |
| 90009 | The request requires App administrator permissions. | The identifier field in the Rest API URL must be an admin account. |
| 90010 | Request format error. | The JSON format request packet does not match the message format description. Refer to the [TIMMsgElement object](https://www.tencentcloud.com/document/product/1047/33527#TIMMsgElement) definition. |
| 90011 | The target account exceeds 500. | The number of target accounts in To_Account exceeds 500. Reduce the number of target accounts. |
| 90012 | To_Account field error. | To_Account is not registered or does not exist. Confirm whether To_Account is imported in Chat or check for spelling errors. |
| 90018 | Number of requested accounts exceeds the limit. | - |
| 90022 | Duplicate tags exist in TagsOr and TagsAnd of the push condition. | - |
| 90024 | Excessive frequency of push. The push interval must be greater than 1 second. | - |
| 90026 | MsgLifeTime field error. | The MsgLifeTime value in the request JSON is too large. |
| 90028 | To_Account field error. | The To_Account field for batch sending one-to-one chat messages is not an array type. Please modify it to an array type. |
| 90029 | To_Account field error. | The array size of To_Account for sending one-to-one messages to multiple users is 0. Please fill in accounts in the To_Account array. |
| 90030 | SyncFromOldSystem field error. | Click to view [reference document](https://www.tencentcloud.com/document/product/1047/35014). |
| 90031 | SyncOtherMachine field error. | The SyncOtherMachine field in the JSON format request body is not of Integer type. |
| 90032 | The number of tags in push conditions exceeds 10, or the number of tags in the add tag request exceeds 10. | - |
| 90033 | Invalid attribute. | Click to view [reference document](https://www.tencentcloud.com/document/product/1047/60562). |
| 90034 | Tag length greater than 50. | Click to view [reference document](https://www.tencentcloud.com/document/product/1047/60565). |
| 90040 | One of the tags in the push conditions is empty. | - |
| 90043 | OfflinePushInfo field error. | The JSON format request packet does not match the message format description. Refer to the [OfflinePushInfo object](https://www.tencentcloud.com/document/product/1047/33527#offlinepushinfo) definition. |
| 90044 | MsgLifeTime field error. | The MsgLifeTime field in the JSON format request body is not of Integer type. |
| 90045 | All Users Push feature not enabled. | Refer to [enable Push service](https://www.tencentcloud.com/document/product/1047/60534). |
| 90047 | Push times exceed the daily limit (default: 100). | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 90048 | The user account does not exist. | Check whether the UserID is deleted. If not deleted, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 90054 | MsgKey field error. | Check the existence of the MsgKey field and verify the validity of its format. If you cannot confirm, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 90055 | Message body too long for batch sending. Currently supports a maximum message body length of 12K. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 90994 | Internal service error. Please retry. | Retry. If it occurs frequently, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 90995 | Internal Server Error. Please retry. | The message is too long. Reduce the message content or contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 91000 | Internal Server Error. Please retry. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 90992 | Message callback error. | Internal service error, retry. If all requests return this error code and the App is configured with third-party callback, please check whether the App Server is returning the callback result normally to the Chat backend server. |
| 93000 | JSON packet is overly long. Do not exceed 12K for the message body. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 91101 | Web long polling is terminated (number of simultaneously online instances exceeds the limit). | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 90057 | Batch sending one-to-one chat messages exceeds the maximum rate limit. Configure related options in the console. See: [server API frequency modulation](https://www.tencentcloud.com/document/product/1047/34419#4bd5b460-57b2-4ac3-874c-e2738c2024a8). | Reduce the operation frequency or increase the batch send C2C chat rate limit on the console. |
| 120001 - 130000 | The custom error code returned by the C2C Chat third-party webhook. | - |

### Group Error Codes

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 10002 | Internal server error. | Retry. |
| 10003 | In-progress request API name error. | Check the API name and retry. |
| 10004 | Invalid parameter. | Check the request for correctness based on the error description. |
| 10005 | Number of accounts in the request payload is too many. | Reduce the number of accounts in the request payload. |
| 10006 | Operation frequency reaches the limit. | Try to reduce the call frequency. |
| 10007 | Common causes:The group does not support this operation by default. Check the current group type.Insufficient permissions for the operation account (for example, during a ban, an admin can ban ordinary members but not the group owner).The account calling the RestAPI is not the administrator account of the SDKAppID. | Check based on the error cause. Or contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 10009 | Group owners are not allowed to exit. | Check whether the member exiting the group is the group owner. |
| 10010 | The group does not exist, or it may have existed but has already been dismissed. | The group does not exist and cannot operate. |
| 10011 | Failed to parse the JSON packet. | Please check whether the package format conforms to JSON format. |
| 10012 | The UserID to initiate the operation is illegal. | Please check whether the operating user's UserID is filled in correctly. |
| 10013 | The user is already a group member. | The user is already a group member. Do not add repeatedly. |
| 10014 | The group is full. Unable to add the user in request to the group. | If batch adding users, can try to reduce the number of users to join. |
| 10015 | The group does not exist or has already been dismissed. | - |
| 10016 | The App backend denied this operation via third-party callback. | Please check whether the App backend reported blocking this operation. |
| 10017 | The sender is muted and cannot send messages. | Please check whether the sender is set to silence. |
| 10018 | Response packet length exceeds the maximum packet length (1 MB), too many requested content. | Try to reduce the data volume per request. |
| 10019 | Requested user account does not exist. | Please check whether the UserID in the request body is filled in correctly. |
| 10021 | GroupId is already used. | Please select the rest group ID. |
| 10023 | The frequency of sending messages exceeds the limit, triggering a single-group rate limit of 40 messages per second. | Extend the time interval for sending messages twice, or set message priority based on business needs. |
| 10024 | This invitation or request has been processed. | No need to process duplicate invitations or requests. |
| 10025 | The group ID is already used and the operator is the group owner. | Use this group ID directly. |
| 10026 | The command word requested by this SDKAppID is disabled. | - |
| 10030 | The message requested for recall does not exist. | Check whether the message seq is filled correctly. |
| 10031 | The message recall exceeds the time limit (default: 2 minutes). | Please recall the message within the time limit (default: 2 minutes). |
| 10032 | The requested message does not support recall operation. | Please check whether the message to be revoked is supported. |
| 10033 | The group type does not support message recall. | Please check whether this group type supports message recall. |
| 10034 | This message type does not support deletion. | Please check whether the message type in the request supports deletion. |
| 10035 | AVChatRoom and BChatRoom do not support message deletion. | Do not delete messages in AVChatRoom and BChatRoom. |
| 10036 | The number of AVChatRoom creations exceeds the limit. | Refer to [Pricing](https://trtc.io/document/67650?product=pricing) to purchase the prepaid plan "AVChatRoom". |
| 10037 | The number of groups a single user can create and join exceeds the limit. | Refer to [Pricing](https://trtc.io/document/67650?product=pricing) to purchase or upgrade the prepaid plan "Single-person Group Creation and Joining Limit". |
| 10038 | The number of group members exceeds the limit. | Refer to [Pricing](https://trtc.io/document/67650?product=pricing) to purchase or upgrade the prepaid plan "Upper Limit of Group Members Expansion". (After upgrade, you need to call the [Modify Group Information API](https://www.tencentcloud.com/document/product/1047/34962) to modify the maximum group size) |
| 10041 | This application (SDKAppID) is configured to not support group message recall. | Please check whether group message recall operation is supported. |
| 10044 | This group type does not support message roaming, such as AVChatRoom. | Please check whether the group type supports message roaming. |
| 10045 | The custom attribute key exceeds the size limit of 32 bytes. | Reduce the custom attribute key size. |
| 10046 | The custom attribute val exceeds the size limit of 4000 bytes. | Reduce the custom attribute val size. |
| 10047 | The custom attribute key count exceeds the limit of 16. | Reduce the custom attribute key count. |
| 10048 | The sum of sizes for ALL custom attribute key vals exceeds the upper limit of 16000 bytes. | Reduce the size of ALL key vals. |
| 10049 | Write operations on custom attributes triggered rate limiting. | Extend the interval between two custom attribute write operations. |
| 10050 | Delete non-existing custom attributes. | Please check the existence of the custom attribute to be deleted. |
| 10051 | Message deletion exceeds the maximum range limit. | Reduce the difference between the maximum value and minimum value of message seq to be deleted in-progress request. |
| 10052 | Message deletion failed as the message does not exist in the group. | Check whether the message exists in the group. |
| 10053 | The number of group mentions exceeds the limit of 30. | Reduce the number of group mentions, perform mentions in batches. |
| 10054 | Too many group members. | Pull by page. |
| 10056 | Custom attribute write operation competition conflict. | Get the latest custom attributes before and then proceed with write operations. |
| 10058 | The Trial Edition exceeds the 100-group limit. | Purchase a package to increase the group limit. |
| 10059 | This feature requires purchase of Pro Edition, Pro Edition Plus, or Enterprise Plan to support. | [Pro Edition, Pro Edition Plus, or Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro&language=en) is required. |
| 10060 | The group size exceeds the read receipt group cap. | Please check whether the group member count exceeds the read receipt cap. |
| 10061 | Online messages do not support read receipts. | Please check whether the message request is set as an online message and requires a read receipt. |
| 10062 | Read receipt information does not exist. | A read receipt should be set when sending a message. |
| 10063 | The number of GroupCounter Keys exceeds the limit. The maximum is 20. | Simplify GroupCounter Keys. |
| 10070 | The pinned message exceeds the quantity limit. | Please check whether the pinned message exceeds the maximum limit. |
| 11000 | Community feature not enabled. | After enabling the Community feature, related features will be supported. |
| 110006 | The permission group does not exist, or it may have existed but has already been dismissed. | - |
| 110007 | Permission group deletion failed. | Retry. |
| 110008 | The permission group does not exist or has been deleted. | Replace the permission group ID and try again. |
| 110010 | The topic already exists in the corresponding permission group. | Replace the permission group ID or topic ID and try again. |
| 110011 | The topic does not exist in the corresponding permission group. | Replace the permission group ID or topic ID and try again. |
| 110012 | The number of permission group members exceeds the limit. | Reduce the number of permission group members and try again. |
| 110013 | Invalid topic ID. | Replace the topic ID. |
| 110014 | The topic permission has been deleted. | Replace the permission group ID or topic ID and try again. |

### Offline Push Error Codes

Please visit [Push Service > Error Code](https://www.tencentcloud.com/document/product/1047/74196) to view.

### Retrieving Operation Data Error Codes

| Error Code | Description |
| --- | --- |
| 1001 | Illegal request; please check whether the "request URL" is correct. |
| 1003 | System error. |
| 1004 | File not generated, or no messages during the request period. |
| 1005 | File expired. |

## Content Review Error Code

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 2001 | Please try again later. | If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 2002 | This command word is not currently supported. | - |
| 2003 | Invalid request parameters. | - |
| 2004 | The request is unauthorized. | Check whether the RestAPI is an admin call. |
| 2015 | Audit service not enabled. | - |
| 2016 | Dirty words added exceed the limit per request. | Up to 10 keywords can be added each time. |
| 2100 | Failed to delete sensitive words in Cloud Moderation. | - |
| 93000 | Content for review exceeds the maximum limit of 8KB. | Please check the Content length. |
| 93001 | Internal error. | Please try again later. If it still fails, contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 93005 | Batch Review API. | Supports only graphic text review. |
| 93006 | Batch Review API. | Moderation timeout exists. The timeout period is 5s. |
| 93007 | Batch Review API. | Duplicate ContentId is not supported. |
| 93008 | Batch Review API. | Up to 10 Content submissions for review are supported. |

### WeChat Official Account Error Code

| Error Code | Description | Handling Suggestion |
| --- | --- | --- |
| 130002 | Insufficient operation permissions. Check request parameters according to the error information. | Please check whether the requesting user has subscribed to the WeChat Official Account or possesses management permissions for it. |
| 130004 | The WeChat Official Account user does not exist, or may have existed but has been terminated. | - |
| 130005 | The user has already subscribed to the WeChat Official Account. Do not repeat. | - |
| 130006 | The number of subscribers for this WeChat Official Account is full. | Upgrade to [Pro Edition Plus or Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro&language=en) and contact us to expand the maximum number of subscribers for the WeChat Official Account. |
| 130007 | The official account user ID does not meet the format requirements. | Please retry after modification according to the [Public Account System](https://www.tencentcloud.com/document/product/1047/60813) requirements. |
| 130008 | The official account user ID is in use. | Please modify and try again. |
| 130009 | This official account does not support message deletion. | - |
| 130010 | The number of prepaid official accounts created and joined exceeds the limit. | Cancel some public account subscriptions and try again. |
| 131000 | This AppId does not have the official account service activated. | Contact [Chat technical support](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) to fix. |
| 130010 | The number of official accounts created exceeds the limit. | Dismiss some official accounts and try again. |
| 131003 | Subscription information not found. The user may not have subscribed to this official account. | Please check whether the requesting user has subscribed to the WeChat Official Account. |
| 131005 | The SDK version is too low and does not support public account features. Please upgrade the SDK version. | - |

## Error Codes for Chat SDK V3

| Error Code | Description |
| --- | --- |
| 6003 | Batch operation with no successful outcome. |
| 6011 | Invalid recipient. |
| 6012 | Request timeout. |
| 6018 | INIT CORE module failed. |
| 6020 | SessionNode is null. |
| 6023 | Logged out before login complete (returned during log-in). |
| 6024 | TLS SDK not initialized. |
| 6025 | TLS SDK no user information was found. |
| 6100 | QALSDK BIND failed for unknown reason. |
| 6101 | Lack of SSO invoice. |
| 6102 | Repeated BIND. |
| 6103 | TinyId is empty. |
| 6104 | GUID is empty. |
| 6105 | Failed to unpack the registration package. |
| 6106 | Registration timeout. |
| 6107 | BIND operation underway. |
| 6120 | Unknown error in sending the package. |
| 6121 | No network when sending request packet. |
| 6122 | No network when sending response packet. |
| 6123 | No permission when sending request packet. |
| 6124 | SSO error. |
| 6125 | Request timeout. |
| 6126 | Reply timeout. |
| 6127 | Resend fail. |
| 6128 | Resend not actual send. |
| 6129 | Saving filtered. |
| 6130 | Send overload. |
| 6131 | Data Logic Error |
| 6150 | proxy_manager has not completed server-side data synchronization. |
| 6151 | proxy_manager is currently synchronizing server-side data. |
| 6152 | proxy_manager synchronization failed. |
| 6153 | The proxy_manager request parameters are invalid when checked locally. |
| 6160 | The Group assistant request field contains non-preset fields. |
| 6161 | Group assistant group information local storage not enabled. |
| 6162 | Failed to load group information. |
| 6200 | No network when sending a request. |
| 6201 | No network when responding. |
| 6205 | QALSDK service is not ready. |
| 6207 | Authentication failed (TinyId conversion failure). Please check if the UserID exists and is valid. |
| 6209 | After the application launches, it does not attempt to go online. |
| 6210 | QALSDK execution failed. |
| 6211 | Illegal request, toMsgService is illegal. |
| 6212 | Request queue is full. |
| 6213 | You have been kicked by another terminal. |
| 6214 | Service paused. |
| 6215 | SSO signature error. |
| 6216 | SSO cookie invalid. |
| 6217 | Packet checksum in TLS SDK response upon login, invalid length. |
| 6218 | Timeout when OPENSTATSVC reports status to OPENMSG upon login. |
| 6219 | Failed to parse response packet when OPENSTATSVC reports status to OPENMSG upon login. |
| 6220 | TLS SDK decryption failed upon login. |
| 6221 | WIFI authentication required. |
| 6222 | User canceled. |
| 6223 | The message recall exceeds the time limit (default: 2 minutes). |
| 6224 | Lack of UGC expansion package. |
| 6226 | Auto login. Local ticket expires. UserSig manual login required. |
| 6300 | No available non-persistent connection SSO. |
| 70101 | Log in back. Ticket expires. |
| 90101 | Chat SDK is already initialized. No need to initialize again. |
| 115000 | OpenBDH Error Code |
| 6250 | No network at the time of request. Please try again after network recovery. |
| 6251 | No network at the time of response. Please try again after network recovery. |
| 6252 | QALSDK execution failed. |
| 6253 | Illegal request, toMsgService is illegal. |
| 6254 | Request queue is full. |
| 6255 | You have been kicked by another terminal. |
| 6256 | Service paused. |
| 6257 | SSO signature error. |
| 6258 | SSO cookie invalid. |

> **Note:**If the encountered issues cannot be resolved on your own, you can [contact us](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=14&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&step=1) and provide API, error code, and detailed error information to ask for help from the technical support team.


---
*Source: [https://trtc.io/document/34348](https://trtc.io/document/34348)*
