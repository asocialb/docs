# WebSocket Protocol for Recognition

## **WebSocket URL Format**

- The URL format is as follows:

`wss://mps.cloud.tencent.com/wss/v1/<appid>?{request parameters}`

`<appid>` is the unique identifier (UInt64) of a Tencent Cloud user account. It can be obtained on the **Account Center** >[**Account Information**](https://console.tencentcloud.com/developer)page in the console.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7ec194af678d11f0924f5254005ef0f7.png)

- The **request parameter** format is as follows:

`key1=value2&key2=value2...(Both keys and values should be in the URL-encoded format.)`

**Request parameters** are listed in the table below:

| Name | Type | Required | Description | Example |
| --- | --- | --- | --- | --- |
| asrDst | string | No | Language for Automatic Speech Recognition (ASR). | zh |
| transSrc | string | No | Source language for translation. | zh |
| transDst | string | No | Target language for translation. | en |
| fragmentNotify | int | No | 0: steady mode notification; 1: non-steady mode notification. Default value: 0. | 0 |
| resultType | int | No | Whether to retain the punctuation at the end.0: delete.1: retain.Default value: 1. | 1 |
| timeStamp | uint | Yes | Current Unix timestamp. Unit: seconds. | 1750217009 |
| expired | uint | Yes | Expiration Unix timestamp. Unit: seconds. | 1750220609 |
| timeoutSec | uint | No | Timeout. Unit: seconds. The connection is interrupted if no audio data has been received for a long time. Default value: 120. Maximum value: 300. | 120 |
| secretId | string | Yes | Key ID. | - |
| nonce | uint | Yes | 10-bit random integer. | 7549145852 |
| signature | string | Yes | Generated signature. | - |

> **Note:**If `asrDst` is not left blank, `transSrc` and `transDst` do not take effect. At this point, only ASR is performed, and subtitles in the source language are generated.If `asrDst` is left blank, `transSrc` and `transDst` cannot be empty. At this point, both ASR and subtitle translation are performed.The value of `fragmentNotify` is 0 by default.

## Signature Generation

For example, sign the following URL:

`wss://mps.cloud.tencent.com/wss/v1/1258344699?asrDst=zh&expired=1750220609&fragmentNotify=0&nonce=7549145852&secretId=<sid>&timeStamp=1750217009`

`<sid>` is the key ID.

### Step 1: Concatenating a Canonical Request String

```
CanonicalRequest =    HTTPRequestMethod + '\\n' +    CanonicalURI + '\\n' +    CanonicalQueryString + '\\n' +    CanonicalHeaders + '\\n' +    SignedHeaders + '\\n'
```

| Field Name | Explanation |
| --- | --- |
| HTTPRequestMethod | The value is fixed as post. |
| CanonicalURI | URI parameter path. Format: /wss/v1/<appid>, where <appid> is the user's AppId.For example, `/wss/v1/1258344699`. |
| CanonicalQueryString | Query string in the URL of the initiated HTTP request. For example, `asrDst=zh&expired=1750220609&fragmentNotify=0&nonce=7549145852&secretId=<sid>&timeStamp=1750217009`The parameters should be sorted alphabetically. Note: CanonicalQueryString should be in URL-encoded format as described in [RFC 3986](https://tools.ietf.org/html/rfc3986). (Special characters should be in uppercase after encoding.) |
| CanonicalHeaders | Format: content-type:application/json;charset=utf-8\\nhost:<host>\\n.<host> is generally a domain name, such as `mps.cloud.tencent.com`. |
| SignedHeaders | The value is fixed as content-type;host. |

### Step 2: Concatenating a String for Signing

```
StringToSign =    Algorithm + "\\n" +    RequestTimestamp + "\\n" +    CredentialScope + "\\n" +    HashedCanonicalRequest
```

| Field Name | Explanation |
| --- | --- |
| Algorithm | Signature algorithm. The value is currently fixed as TC3-HMAC-SHA256. |
| RequestTimestamp | Timestamp in the URL. For example, 1750217009. |
| CredentialScope | Credential scope. Format: <date>/mps/tc3_request. <date> is a date in UTC format, such as 2025-06-18.For example, `2025-06-18/mps/tc3_request`. |
| HashedCanonicalRequest | Hash value of the canonical request string concatenated in the previous step. Pseudocode for calculation: Lowercase(HexEncode(Hash.SHA256(CanonicalRequest))). |

### Step 3: Calculating the Signature

#### 1. Calculating the Derived Signature Key

The pseudocode is as follows:

```
SecretKey = "********************************"SecretDate = HMAC_SHA256("TC3" + SecretKey, Date)SecretService = HMAC_SHA256(SecretDate, Service)SecretSigning = HMAC_SHA256(SecretService, "tc3_request")
```

| Field Name | Explanation |
| --- | --- |
| SecretKey | Original SecretKey, which is masked with asterisks (*). |
| Date | Information in the <date> field of CredentialScope. |
| Service | The value is fixed as mps. |

#### 2. Calculating the Signature

The pseudocode is as follows:

```
signature = HexEncode(HMAC_SHA256(SecretSigning, StringToSign))
```

The final generated URL is as follows:

`wss://mps.cloud.tencent.com/wss/v1/1258344699?asrDst=zh&expired=1750220609&fragmentNotify=0&nonce=7549145852&secretId=<sid>&timeStamp=1750217009&signature=<signature>`

This URL is used to establish a WebSocket persistent connection.

## WebSocket Handshake Phase

After a WebSocket connection is established, the server performs the check and authentication and then returns the handshake result in JSON text message format. Example:

```
{"Code":0, //0: successful; values other than 0: failed."Message":"success", //Returned message."TaskId":"RnKu9FODFHK5FPpsrN" //Task ID, which is a unique identifier.}
```

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Code | int | Yes | 0: successful; values other than 0: failed. |
| Message | string | Yes | Returned message. |
| TaskId | string | Yes | Task ID, which is a unique identifier. |

### Error Code

| Error Code | Description |
| --- | --- |
| 0 | Successful |
| 4001 | Invalid parameter. |
| 4002 | Timed out. It is usually because no audio data has been received successfully for a long time. The default timeout is 2 minutes. It can be specified with a parameter. |
| 4003 | The format of the upload audio is invalid. |
| 4004 | The number of persistent connections that exist at the same time exceeds the limit, which is 2 by default. |
| 4005 | Invalid user status. It is usually because the user account is in arrears. |
| 4100 | Identity verification failed. |
| 4101 | Unauthorized access to APIs. |
| 4102 | Unauthorized access to resources. |
| 4104 | The SecretId does not exist. |
| 4105 | Incorrect session ID. |
| 4106 | MFA authentication failed. |
| 4110 | Authentication failed. |
| 4111 | Invalid AppId. |
| 4500 | Replay attacks, which are usually caused by QPS exceeding the limit. Such attacks may occur when too many WebSocket connections are established for the same AppId in a short time. |
| 5000 | Internal error. |

## Audio Upload

After authentication is successful, the server receives audio data pushed by the client as a binary message. The message definition is shown in the table below and uses the network byte order.

| Field | Type | Length | Description |
| --- | --- | --- | --- |
| format | uint8 | 1 byte | Audio format. |
| IsEnd | uint8 | 1 byte | 1: The user has no audio data during the follow-up period, and the recognition result is forcibly refreshed.0: The user has audio data during the follow-up period. |
| timeStamp | uint64 | 8 bytes | Timestamp. Unit: ms. |
| userIdLen | uint16 | 2 bytes | User ID length. |
| userId | string | Same as the value of userIdLen | User ID. It identifies an audio source in the a connection. |
| extLen | uint16 | 2 bytes | Extension length. Default value: 0. |
| extData | char[] | Same as the value of extLen | Extended data for future expansion. |
| Audio | char[] | Other data in the binary message | Audio data. |

> **Note:**The value of `format` can only be 1 currently, indicating PCM 16-kHz s16 (16-bit) single-channel.

## Recognition Result Sending

After the recognition result is output, the server sends the recognition result in JSON text message format.

For details, see [ParseLiveStreamProcessNotification](https://www.tencentcloud.com/document/product/1041/33680).

### Translation Result Notification

```
{    "Response": {        "NotificationType": "AiRecognitionResult",        "TaskId": "1258344699-wsssubtitle-d482fa50-5e1c-4c5c-b5b5-1083430e0d54",        "AiRecognitionResultInfo": {            "ResultSet": [                {                    "Type": "TransTextRecognition",                    "TransTextRecognitionResultSet": [                        {                            "Text":"How to ensure that global users can enjoy high-definition and smooth video content."                            "Trans": "How to ensure that global users can enjoy high-definition and smooth video content.",                            "StartPtsTime": 0.2,                            "EndPtsTime": 4.6,                            "Confidence": 100,                            "SteadyState": true,                            "StartTime": "2025-06-18T12:01:54Z",                            "EndTime": "2025-06-18T12:01:58Z",                            "UserId": "123456"                        }      ]                }    ]        }    }}
```

### Recognition Result Notification

If only ASR is performed without translation, the result notification only contains `Text`, without `Trans`.

```
{    "Response": {        "NotificationType": "AiRecognitionResult",        "TaskId": "1258344699-wsssubtitle-ce42ecfe-0f70-4244-91e0-07e6c20a5ab1",        "AiRecognitionResultInfo": {            "ResultSet": [                {                    "Type": "AsrFullTextRecognition",                    "AsrFullTextRecognitionResultSet": [                        {                            "Text":"How to ensure that global users can enjoy high-definition and smooth video content."                            "StartPtsTime": 0.2,                            "EndPtsTime": 4.6,                            "Confidence": 100,                            "SteadyState": true,                            "StartTime": "2025-06-18T12:00:41Z",                            "EndTime": "2025-06-18T12:00:45Z",                            "UserId": "123456"                        }      ]                }    ]        }    }}
```

### Ending Notification

```
{    "Response": {        "NotificationType": "ProcessEof",        "TaskId":"1258344699-wsssubtitle-033a7ae4-50ef-4d1f-a73f-0e51a28d3a68",        "ProcessEofInfo": {            "ErrCode": 4002,            "Message": "data timeout"        }    }}
```

### Field Description

For details, see [Data Types](https://www.tencentcloud.com/document/product/1041/33690).

| Name | Description |
| --- | --- |
| NotificationType | Valid values: AiRecognitionResult and ProcessEof. |
| TaskId | Task ID. |
| Type | Notification type. Valid values: AsrFullTextRecognition, TransTextRecognition, and ProcessEof. |
| Text | Recognized text. |
| StartPtsTime | Start timestamp. Unit: seconds. It corresponds to the timeStamp field in Audio Upload. |
| EndPtsTime | End timestamp. Unit: seconds. It corresponds to the timeStamp field in Audio Upload. |
| StartTime | Time when the server receives the audio packet. It is a UTC time. |
| EndTime | End time. It is a UTC time. |
| Confidence | Confidence. Value range: 0–100. |
| SteadyState | Steady status flag. It indicates that the result will not change. |
| UserId | User ID. It corresponds to userId in Audio Upload. |
| ErrCode | Same as the error code of the handshake phase. Only 4002 and 4003 are usually used. |
| Message | Returned message. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/72106](https://www.tencentcloud.com/document/product/1041/72106)*
