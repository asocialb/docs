# Context management

Context management is very important for large models. It allows the model to provide more accurate responses based on chat history. Tencent Real-Time Communication (Tencent RTC) AI offers basic context management capabilities and also supports developers in creating their own rich context management solutions.

## Basic Context Management:

Tencent RTC AI provides basic context management features. In the LLMConfig parameters, we introduce a History parameter to control context management:

History:

- It is used to set the LLM's context rounds, with a default value of 0 (no context management is provided).
- Maximum value: 50 (context management is provided for the most recent 50 rounds).

A relevant configuration example is shown below:

```
"LLMConfig": {          "LLMType": "openai",            "Model":"gpt-4o",          "APIKey":"api-key",          "APIUrl":"https://api.openai.com/chat/completions",          "Streaming": true,          "SystemPrompt": "You are a personal assistant",          "Timeout": 3.0,          "History": 5    // Up to 50 rounds of conversations are supported, with a default value of 0.  }
```

## Custom Context Management:

The Tencent RTC AI conversation service supports standard OpenAI specifications, allowing developers to implement customized context management in their own business. The implementation process is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7d5f0a6194dd11ef810152540055f650.png)

This flowchart shows the basic steps for custom context management. Developers can adjust and optimize this process according to their specific needs.

### Implementation Example

Developers can implement an OpenAI API-compatible large model interface at their own business backend and send large model requests encapsulated with context logic to third-party large models. Here is a simplified sample code:

```
import timefrom fastapi import FastAPI, HTTPExceptionfrom fastapi.middleware.cors import CORSMiddlewarefrom pydantic import BaseModelfrom typing import List, Optionalfrom langchain_core.messages import HumanMessage, SystemMessagefrom langchain_openai import ChatOpenAIapp = FastAPI(debug=True)# Add CORS middleware.app.add_middleware(    CORSMiddleware,    allow_origins=["*"],    allow_credentials=True,    allow_methods=["*"],    allow_headers=["*"],)class Message(BaseModel):    role: str    content: strclass ChatRequest(BaseModel):    model: str    messages: List[Message]    temperature: Optional[float] = 0.7class ChatResponse(BaseModel):    id: str    object: str    created: int    model: str    choices: List[dict]    usage: dict@app.post("/v1/chat/completions")async def chat_completions(request: ChatRequest):    try:        # Convert the request message to the LangChain message format.        langchain_messages = []        for msg in request.messages:            if msg.role == "system":                langchain_messages.append(SystemMessage(content=msg.content))            elif msg.role == "user":                langchain_messages.append(HumanMessage(content=msg.content))        # Add more histories.        # Use LangChain's ChatOpenAI model.        chat = ChatOpenAI(temperature=request.temperature,                          model_name=request.model)        response = chat(langchain_messages)        print(response)        # Construct a response that conforms to the OpenAI API format.        return ChatResponse(            id="chatcmpl-" + "".join([str(ord(c))                                     for c in response.content[:8]]),            object="chat.completion",            created=int(time.time()),            model=request.model,            choices=[{                "index": 0,                "message": {                    "role": "assistant",                    "content": response.content                },                "finish_reason": "stop"            }],            usage={                "prompt_tokens": -1,  # LangChain does not provide this information, so we use a placeholder value.                "completion_tokens": -1,                "total_tokens": -1            }        )    except Exception as e:        raise HTTPException(status_code=500, detail=str(e))if __name__ == "__main__":    import uvicorn    uvicorn.run(app, host="0.0.0.0", port=8000)
```

[Click to view an example](https://github.com/Tencent-RTC/trtc-conversation-ai-example).


---
*Source: [https://trtc.io/document/65318](https://trtc.io/document/65318)*
