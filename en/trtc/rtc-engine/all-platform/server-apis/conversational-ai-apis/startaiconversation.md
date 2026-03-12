# StartAIConversation

## 1. API Description

Domain name for API request: trtc.intl.tencentcloudapi.com.

Initiate AI conversation task, where the AI bot enters the TRTC room to engage in AI conversation with specified members in the room. This is suitable for scenarios such as intelligent customer service and AI language teachers. The TRTC AI conversation feature has built-in speech-to-text capabilities , allowing customers to flexibly specify third-party AI model (LLM) services and text-to-speech (TTS) services. For more [feature details](https://cloud.tencent.com/document/product/647/108901).

A maximum of 20 requests can be initiated per second for this API.

We recommend you to use API Explorer

Try it

API Explorer provides a range of capabilities, including online call, signature authentication, SDK code generation, and API quick search.  It enables you to view the request, response, and auto-generated examples.

## 2. Input Parameters

The following request parameter list only provides API request parameters and some common parameters. For the complete common parameter list, see [Common Request Parameters](https://www.tencentcloud.com/document/api/647/34263).

| Parameter Name | Required | Type | Description |
| --- | --- | --- | --- |
| Action | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: StartAIConversation. |
| Version | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). The value used for this API: 2019-07-22. |
| Region | Yes | String | [Common Params](https://www.tencentcloud.com/document/api/647/34263). For more information, please see the [list of regions](https://www.tencentcloud.com/document/api/647/34263#region-list) supported by the product. This API only supports: ap-guangzhou, ap-singapore, ap-tokyo, na-siliconvalley. |
| SdkAppId | Yes | Integer | TRTC's [SdkAppId](https://intl.cloud.tencent.com/document/product/647/37714) is the same as the SdkAppId used by the room that starts the conversation task. |
| RoomId | Yes | String | TRTC's [RoomId](https://intl.cloud.tencent.com/document/product/647/37714), which indicates the room number where the conversation task is started. |
| AgentConfig | Yes | [AgentConfig](https://www.tencentcloud.com/document/api/647/36760#AgentConfig) | Robot parameters |
| SessionId | No | String | The unique ID passed in by the caller can be used by the client to prevent repeated task initiation and to query the task status through this field. |
| RoomIdType | No | Integer | The type of TRTC room number. 0 represents a numeric room number, and 1 represents a string room number. If not filled in, the default is a numeric room number. |
| STTConfig | No | [STTConfig](https://www.tencentcloud.com/document/api/647/36760#STTConfig) | Speech recognition configuration. |
| LLMConfig | No | String | LLM configuration. It must comply with the openai specification and be a JSON string. The example is as follows:  {     "LLMType": "Large model type", // String required, such as: "openai"     "Model": "Your model name", // String required, specify the model to be used  "APIKey": "Your LLM API key", // String required     "APIUrl": "https://api.xxx.com/chat/completions", // String required, URL for LLM API access    "Streaming": true // Boolean optional, specify whether to use streaming   } |
| TTSConfig | No | String | TTS configuration, which is a JSON string. The Tencent Cloud TTS example is as follows: {     "AppId": your application ID, // Integer Required    "TTSType": "TTS type", // String TTS type, fixed to "tencent"    "SecretId": "Your key ID", // String Required    "SecretKey": "Your keyKey", // String Required    "VoiceType": 101001, // Integer Required, voice ID, including standard voice and premium voice. Premium voice has higher fidelity and different price from standard voice. For details, please refer to [Overview of Speech Synthesis Billing](https://cloud.tencent.com/document/product/1073/34112). For a complete list of timbre IDs, see [List of speech synthesis timbre IDs](https://cloud.tencent.com/document/product/1073/92668#55924b56-1a73-4663-a7a1-a8dd82d6e823).     "Speed": 1.25, // Integer Optional, speaking speed, range: [-2, 6], corresponding to different speaking speeds: -2: 0.6 times -1: 0.8 times 0: 1.0 times (default) 1: 1.2 times 2: 1.5 times 6: 2.5 times If a more detailed speaking speed is required, 2 decimal places can be retained, such as 0.5/1.25/2.81, etc. For the conversion between parameter value and actual speech speed, please refer to [Speed Conversion](https://sdk-1300466766.cos.ap-shanghai.myqcloud.com/sample/speed_sample.tar.gz)    "Volume": 5, // Integer Optional, volume size, range: [0, 10], corresponding to 11 levels of volume, the default value is 0, representing normal volume.     "PrimaryLanguage": "zh-CN" // String Optional, primary language   } |

## 3. Output Parameters

| Parameter Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Used to uniquely identify a conversation task. |
| RequestId | String | The unique request ID, generated by the server, will be returned for every request (if the request fails to reach the server for other reasons, the request will not obtain a RequestId). RequestId is required for locating a problem. |

## 4. Example

### Example1 Start an AI robot conversation task

#### Input Example

```
POST / HTTP/1.1
Host: trtc.intl.tencentcloudapi.com
Content-Type: application/json
X-TC-Action: StartAIConversation
<Common request parameters>

{
    "SdkAppId": 12345678,
    "RoomId": "room_987654321",
    "RoomIdType": 1,
    "AgentConfig": {
        "UserId": "user_12345",
        "UserSig": "user_signature_example",
        "MaxIdleTime": 120,
        "TargetUserId": "target_user_54321"
    },
    "SessionId": "session_1234567890abcdef",
    "STTConfig": {
        "Language": "en-US",
        "AlternativeLanguage": [
            "en-US",
            "zh"
        ]
    },
    "LLMConfig": "{\"LLMType\": \"openai\", \"Model\": \"gpt-3.5-turbo\", \"APIKey\": \"xxx\", \"APIUrl\": \"http://xxxx-api.woa.com/v1/chat/completions\", \"Streaming\": true}",
    "TTSConfig": "{\"TTSType\": \"tencent\", \"AppId\": 130000000, \"SecretId\": \"AKIDxxxxx\", \"SecretKey\": \"HlDxxxxxx\", \"VoiceType\": 1008, \"Speed\": 1}"
}
```

#### Output Example

```json
{
    "Response": {
        "TaskId": "abc",
        "RequestId": "abc"
    }
}
```

## 5. Developer Resources

### SDK

TencentCloud API 3.0 integrates SDKs that support various programming languages to make it easier for you to call APIs.

Tencent Cloud SDK 3.0 for Python
Tencent Cloud SDK 3.0 for Java
Tencent Cloud SDK 3.0 for PHP
Tencent Cloud SDK 3.0 for Go
Tencent Cloud SDK 3.0 for Node.js
Tencent Cloud SDK 3.0 for .NET
Tencent Cloud SDK 3.0 for C++

### Command Line Interface

Tencent Cloud CLI 3.0

## 6. Error Code

The following only lists the error codes related to the API business logic. For other error codes, see [Common Error Codes](https://www.tencentcloud.com/document/api/647/34270#common-error-codes).

| Error Code | Description |
| --- | --- |
| FailedOperation.NotAbility | Need to unlock the required ability |
| FailedOperation.NotAllowed | This operation is not allowed, please submit a ticket to contact us |
| FailedOperation.TaskExist | Task already exists |
| InvalidParameter.UserSig | UserSig is expired or wrong |
| ResourceInsufficient.RequestRejection | Insufficient resources. |


---
*Source: [https://trtc.io/document/64963](https://trtc.io/document/64963)*
