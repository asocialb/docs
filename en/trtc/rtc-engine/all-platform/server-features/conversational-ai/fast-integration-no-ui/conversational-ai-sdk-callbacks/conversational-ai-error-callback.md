# Conversational AI Error Callback

Conversational AI of Tencent RTC provides the error callback feature. The error callbacks are sent through custom messages of Tencent RTC, enabling easy monitoring of conversation performance in the client. For example, when a LLM/TTS call fails, the data is pushed to the terminal in real time through custom messages of Tencent RTC to monitor the AI conversation quality and success rate.

You can use the [Receive Custom Messages feature](https://www.tencentcloud.com/document/product/647/47866) provided by the RTC Engine SDK to listen to callbacks in the client to receive data from AI conversation error callbacks. **The cmdID value is fixed at 1.**

| Field | Type | Description |
| --- | --- | --- |
| type | Number | Message type. 10030 indicates an AI service error. |
| sender | String | User ID of the sender, which is the chatbot ID. |
| payload | Object | Message payload, including the detail information. |

The payload object contains the following fields:

| Field | Type | Description |
| --- | --- | --- |
| metric | String | The names of called metrics are as follows:asr_errorllm_errortts_error |
| tag | Object | Tag associated with the metric. |

The tag object contains the following fields:

| Field | Type | Description |
| --- | --- | --- |
| roundid | String | Conversation round ID. |
| code | Number | Call error code. |
| message | String | Detailed description of the error message. |

Metric name description:

| Status Code | Description |
| --- | --- |
| asr_error | ASR (STT) error. |
| llm_error | LLM request error. |
| tts_error | TTS request error. |

Error code list:

| Service Category | Error Code | Error Description |
| --- | --- | --- |
| ASR (STT) | 30100 | Request timed out. |
|  | 30102 | Internal error. |
| LLM | 30200 | LLM request timed out. |
|  | 30201 | The LLM request frequency is limited. |
|  | 30202 | LLM service response failed. |
| TTS | 30300 | TTS request timed out. |
|  | 30301 | The TTS request frequency is limited. |
|  | 30302 | TTS service response failed. |

> **Note:**More specific error codes, such as those of third-party LLM and TTS errors, will be included in `tag.message` to help quickly locate the issue and notify users of errors.


---
*Source: [https://trtc.io/document/68335](https://trtc.io/document/68335)*
