# Large Language Model Configuration

This document describes how to configure the `LLMConfig` parameter of the [StartAIConversation](https://trtc.io/document/64963?product=rtcengine&menulabel=serverfeaturesapis) API.

## Parameter Description

| Name | Description |
| --- | --- |
| LLMType | Large language model (LLM) type. Fill in `openai` for LLMs that comply with the `OpenAI API` protocol. |
| Model | Specific LLM name. For example, `gpt-4o`. |
| APIKey | LLM `API Key`. |
| APIUrl | LLM `API URL`. |
| Streaming | Whether streaming transmission is used. |
| SystemPrompt | Prompt words. |
| Timeout | Timeout in seconds. It is 3 seconds by default. |
| History | Sets the context rounds for the LLM. Default value: 0 (no context provided for management). Maximum value: 50 (provide context of the last 50 rounds for management). |
| MetaInfo | Custom parameters. They will be contained in the request body and passed to the LLM. |

## LLMConfig Configuration Example

### OpenAI

```
"LLMConfig": {      "LLMType": "openai",        "Model":"gpt-4o",      "APIKey":"api-key",      "APIUrl":"https://api.openai.com/v1/chat/completions",      "Streaming": true,      "SystemPrompt": "You are a personal assistant."      "Timeout": 3.0,      "History": 5,      "MetaInfo": {}}
```

### MiniMax

```
"LLMConfig":{    "LLMType": "openai",    "Model": "abab6.5s-chat",    "Streaming": true,    "SystemPrompt": "You are a personal assistant."    "APIKey": "eyJhbGcixxxx",    "APIUrl": "https://api.minimax.chat/v1/text/chatcompletion_v2",    "History": 5,    "MetaInfo": {} }
```

### Hunyuan

```
"LLMConfig":{      "LLMType": "openai",      "Model": "hunyuan-standard", // hunyuan-turbo, hunyuan-standard      "APIKey": "hunyuan-apikey",      "APIUrl": "https://hunyuan.cloud.tencent.com/openai/v1/chat/completions",      "Streaming": true,      "History": 10,      "MetaInfo": {}}
```

> **Note:**LLMs that comply with the `OpenAI API` protocol are supported. For these LLMs, fill in `openai` for `LLMType`. Otherwise, fill in other values according to the actual situation.

## LLM Requests

Multiple parameters are added to the HTTP header to support more complex logic.

```
X-Task-Id: <task_id_value> // ID of the task.X-Request-Id: <request_id> // ID of the request. The same requestId value is used for retries.X-Sdk-App-Id: SdkAppIdX-User-Id: UserIdX-Room-Id: RoomId  X-Room-Id-Type: "0" // "0" indicates that the room ID is a number, and "1" indicates that the room ID is a string.
```


---
*Source: [https://trtc.io/document/68338](https://trtc.io/document/68338)*
