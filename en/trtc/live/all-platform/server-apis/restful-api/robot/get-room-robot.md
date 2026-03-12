# Get Room Robot

## Feature Description

App admins can get the robot list in the room use this API.

## API Call Description

### Sample Request URL

```
https://xxxxxx/v4/live_engine_http_srv/get_robot?sdkappid=88888888&identifier=admin&usersig=xxx&random=99999999&contenttype=json
```

### Request Parameters

The following table only lists the parameters involved in modification when calling this API and their descriptions. For more details about the parameters, please see [RESTful API Overview](https://www.tencentcloud.com/document/product/647/63398).

| Parameters | Description |
| --- | --- |
| xxxxxx | Domain name corresponding to the country/region where your SDKAppID is located: China: `console.tim.qq.com`Singapore: `adminapisgp.im.qcloud.com`US: `adminapiusa.im.qcloud.com` |
| v4/live_engine_http_srv/get_robot | Request API |
| sdkappid | Create an assigned SDKAppID for the Live application |
| identifier | Must be an App administrator account. For more details, see [App Admin](https://www.tencentcloud.com/document/product/647/69882#app-admin) |
| usersig | The generated signature of the App administrator account. For specific operations, see [Generating UserSig](https://www.tencentcloud.com/document/product/647/69883) |
| random | Enter a random 32-bit unsigned integer in the range of 0 to 4294967295 |
| contenttype | The request format has a fixed value of `json` |

### Maximum Calling Frequency

100 times/second.

### Request Packet

**Basic form**

```
{    "RoomId":"mix1"}
```

### Request Packet Fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| RoomId | String | Required | room ID, longest 48 bytes |

> **Noteï¼**If there are robots present in the room, the room will not automatically dismiss and requires manual invocation of the [dismiss](https://www.tencentcloud.com/document/product/647/63406) interface.

### Response Package Body

**Basic form**

```
{  "ActionStatus": "OK",  "ErrorInfo": "",  "ErrorCode": 0,  "RequestId": "Id-8c9858f01e954611ae2d4c1b1ed7d583-O-Seq-52720",   "Response": {        "RobotList_Account": [            "brennanli",            "brennanli2"        ]    }}
```

### Response Packet Fields

| Field | Type | Description |
| --- | --- | --- |
| ActionStatus | String | Request processing result. OK: processing successful; FAIL: processing failed |
| ErrorCode | Integer | Error code. 0: success; non-0: failure |
| ErrorInfo | String | Error message |
| RequestId | String | Unique request ID. It is returned for each request. RequestId is required for locating a problem |
| RobotList_Account | Array | Robot list |
| Response | Object | Respond to specific data |

## Error Code Description

Unless a network error (for example, 502 error) occurs, the HTTP return code of this API is 200. The actual error code and error information are indicated by ErrorCode and ErrorInfo in the response packet body.

For common error codes (60000 to 79999), see the  [Error Code](https://www.tencentcloud.com/document/product/647/60027) document.

The private error codes of this API are as follows:

| Error Code | Description of meaning |
| --- | --- |
| 100001 | Internal server error, please retry |
| 100002 | Invalid parameter. Check whether the request is correct according to the error description |
| 100006 | The room type required is the Live room type |
| 100004 | The room does not exist or is dissolved |


---
*Source: [https://trtc.io/document/69081](https://trtc.io/document/69081)*
