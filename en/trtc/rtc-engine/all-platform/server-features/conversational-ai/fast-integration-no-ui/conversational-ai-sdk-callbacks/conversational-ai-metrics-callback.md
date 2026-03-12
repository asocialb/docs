# Conversational AI Metrics Callback

Conversational AI of Tencent RTC provides rich metric callbacks. The metric callbacks are sent through custom messages of Tencent RTC, allowing you to easily monitor conversation performance in the client. Metrics such as LLM and TTS call duration and performance are pushed to terminals in real time via custom messages of Tencent RTC, enabling monitoring of AI conversation duration and quality.

You can use the [Receive Custom Messages feature](https://www.tencentcloud.com/document/product/647/47866) provided by the RTC Engine SDK to listen to callbacks in the client to receive the AI conversation metric data. **The cmdID value is fixed at 1.**

| Field | Type | Description |
| --- | --- | --- |
| type | Number | Message type. 10020 indicates AI service invocation callback. |
| sender | String | User ID of the sender, which is the chatbot ID. |
| payload | Object | Message payload, including metric details. |

The payload object contains the following fields:

| Field | Type | Description |
| --- | --- | --- |
| metric | String | The names of called metrics are as follows:asr_latencyllm_network_latencyllm_first_tokentts_network_latencytts_first_frame_latencytts_discontinuityinterruption |
| value | Number | Called metric. |
| tag | Object | Tag associated with the metric. |

The tag object contains the following fields:

| Field | Type | Description |
| --- | --- | --- |
| roundid | String | Conversation round ID. |

Metric name description:

| Status Code | Description |
| --- | --- |
| asr_latency | ASR(STT) latency. Note: This metric includes the time set by VadSilenceTime when conversational AI is started. |
| llm_network_latency | LLM request network latency. |
| llm_first_token | LLM first token latency. This metric includes the network latency. |
| tts_network_latency | TTS request network latency. |
| tts_first_frame_latency | TTS first frame latency. This metric includes the network latency. |
| tts_discontinuity | Number of occurrences of TTS request discontinuity. Discontinuity indicates that no result is returned for the next request after the current TTS streaming request is completed, which is usually caused by high TTS request network latency. |
| interruption | This metric indicates that the conversation is interrupted. |


---
*Source: [https://trtc.io/document/68334](https://trtc.io/document/68334)*
