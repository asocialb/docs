# No-Code Quick Integration Of Conversational AI Feature

Tencent RTC provides a convenient testing and verification platform, supporting the connection to third-party STT, LLM, and TTS capacities for rapid configuration. It enables the quick implementation of conversational AI services without coding for verification tests, facilitating efficient development and deployment. This article will introduce how to use this tool.

## Logging In To the Console

1. Create a RTC Engine application: [Tencent RTC Console > Create RTC Engine Application](https://console.trtc.io/app).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/26eb84e5211111f0a62e525400454e06.png)

2. Click: Start configuring conversational AI.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/489fb14b211111f0b0b1525400e889b2.png)

3. Select No-Code Playground.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/81fb4d73211111f0b47352540044a08e.png)

## Resource Configuration

Conversational AI support for docking with multiple STT, LLM, and TTS manufacturers. Click **Get Started** to quickly configure, test, and integrate conversational AI services here, achieving efficient development and deployment.

> **Note:**Click [Try Demo](https://trtc.io/demo/homepage/#/detail?scene=ai) to experience the capabilities of Conversational AI.Using the quick conversational AI testing tool will incur usage fees. For billing details, see [Billing of Conversational AI Services](https://trtc.io/document/67833?product=pricing).

## Step 1: Basic Configuration

### 1. Select an Application

On the **Basic Configuration** page, you first need to select the application you want to test. You can enable the STT service for the application to use the AI service and STT Automatic Speech Recognition feature byproceeding to **purchase the**[**RTC-Engine Monthly Packages**](https://trtc.io/document/56025?product=pricing)**(including Starter Plan)**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2a43acccedad11efaef452540099c741.png)

### 2. Basic Configuration Items

We provide default parameters, and you can fine-tune the basic configuration items according to your needs. After completing the configuration, click **Next**.

- Fill in the bot welcome message.
- Select the interruption mode. It can automatically interrupt the robot's speech based on specific rules. This mode supports both automatic and manual interruptions. For detailed description, see [Intelligent interruption](https://www.tencentcloud.com/document/product/647/65319).
- Select the interruption duration.

## STEP 2: STT (Speech To Text ) Configuration

The STT speech recognition configuration model can choose Tencent, Azure, and Deepgram. It supports multiple languages, and the VAD duration can be adjusted. The setting range is 240-2000. A smaller value will make the speech recognition sentence segmentation faster. After the configuration is completed, click **Next**.

Tencent

Azure

Deepgram

When selecting Tencent as the STT provider, we provide default parameters for other configurations, and you can fine-tune them according to your needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/940b3cd6e9b511ef9e13525400454e06.png)

When selecting Azure as the STT provider:

- The APIKey can be obtained from the [guidance document](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/how-to-recognize-speech?pivots=programming-language-csharp).
- For Region, refer to [Region Support](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/regions) to fill in.
- We provide default parameters for other configurations; you can fine-tune them according to your needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/36be7290ed2411efaef452540099c741.png)

When selecting Deepgram as the STT provider, we provide default parameters for other configurations; you can fine-tune them according to your needs. The APIKey can be obtained from [Deepgram](https://console.deepgram.com/project/52991c8c-2c62-4492-ba6d-88ca33be6a7b/keys).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4519148fed2411efab2f5254007c27c5.png)

## STEP 3: LLM (Large Language Model) Configuration

On this page, you need to apply for third-party resources for configuration: LLM providers support OpenAI, Deepseek, Minimax, Tencent Hunyuan, Coze, and Dify. After the configuration is completed, click **Next**.

OpenAI

Deepseek

Minimax

Tencent Hunyuan

Coze

Dify

When selecting OpenAI as the LLM provider, this place supports **any LLM model that complies with the OpenAI standard protocol**, such as Google, Anthropic, etc. You can adjust the parameters of the model, Url and Key below by yourself for calling. When you choose to use the model provided by OpenAI, the API Key can be obtained from [OpenAI](https://platform.openai.com/api-keys).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4ed84befe8e311ef9e13525400454e06.png)

When selecting Deepseek as the LLM provider, we provide default parameters for other configurations; you can fine-tune them according to your needs. The LLM model can be viewed at [Deepseek](https://api-docs.deepseek.com/zh-cn/) by checking the supported model list, and the API Key can be obtained from [Deepseek](https://platform.deepseek.com/api_keys).

Besides Deepseek official, you can also choose to call the Deepseek service deployed on third-party cloud platforms. According to the OpenAI protocol, just replace the parameters of LLM Model, Url and Key below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/67899cd6e8e311efab2f5254007c27c5.png)

When selecting Minimax as the LLM provider, we provide default parameters; you can fine-tune them according to your needs. The LLM model can be freely selected from the dropdown option, and the API Key can be obtained from [Minimax management console](https://platform.minimaxi.com/user-center/basic-information/interface-key).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7b3008fce8e311ef922c5254001c06ec.png)

When selecting Hunyuan as the LLM provider, we provide default parameters for other configurations; you can fine-tune them according to your needs. The LLM model can be freely selected from the dropdown option, and the API Key can be obtained from [API Token Management](https://console.tencentcloud.com/hunyuan/api-key).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9e53f6eee8e311efaef452540099c741.png)

When selecting Coze as the LLM provider, we provide default parameters for other configurations; you can fine-tune them according to your needs. The API Key can be obtained by going to [Coze](https://www.coze.com/open/oauth/pats) to get the Secret token, and see [guidance document](https://www.coze.com/open/docs/developer_guides/coze_api_overview) to obtain BotId.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/aa2802e7e8e311ef93475254005ef0f7.png)

When selecting Dify as the LLM provider, we provide default parameters for other configurations; you can fine-tune them according to your needs. The API Key can be obtained from [Dify](https://cloud.dify.ai/datasets?category=api).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b7d81268e8e311ef922c5254001c06ec.png)

## STEP 4: TTS (Text To Speech) Configuration

On the TTS (Text To Speech) configuration page: The TTS provider supports Tencent, Minimax, Azure, Cartesia, Elevenlabs, and custom. After completing the configuration, click **Connect**, if the configuration information is correct, you will enter the Start Conversation page.

Cartesia

Azure

Elevenlabs

Custom

Tencent

Minimax

When selecting Cartesia as the TTS provide:

- The APIKey can be obtained from [Cartesia](https://play.cartesia.ai/keys).
- The voice ID can be obtained from [Cartesia](https://play.cartesia.ai/voices).
- We provide default parameters for other configurations; you can fine-tune them according to your needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/daec134ee8e511ef9e13525400454e06.png)

When selecting Azure as the TTS provide:

- The SubscriptionKey can be obtained by referring to the [guidance document](https://learn.microsoft.com/en-us/azure/ai-services/multi-service-resource?pivots=azportal).
- For Region, refer to [Region Support](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/regions) to fill in.
- For language, refer to [Language and Sound Support](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/language-support?tabs=stt) to fill in.
- We provide default parameters for other configurations; you can fine-tune them according to your needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dc41de3a88bd11f0bd05525400454e06.png)

- e-tune them according to your needs.

When selecting Elevenlabs as the TTS provide:

- The APIKey can be obtained from [ElevenLabs](https://elevenlabs.io/app/settings/api-keys).
- The voice ID can be obtained from [ElevenLabs](https://elevenlabs.io/app/voice-lab).
- We provide default parameters for other configurations; you can fine-tune them according to your needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ebc775c8e8ea11efab2f5254007c27c5.png)

- You can refer to [custom TTS protocol](https://www.tencentcloud.com/document/product/647/65315) configuration.
- When the TTS provider is set to custom, you can fill in the API Key and API Url according to your actual situation.
- We provide default parameters for other configurations; you can fine-tune them according to your needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fd1044f9e8ef11ef840e52540044a08e.png)

- When selecting Tencent as the TTS provider, you need to [activate the application's TTS service](https://console.tencentcloud.com/tts?lang=en) to use the TTS voice synthesis feature.
- The SecretId can be obtained from the [guidance document](https://console.tencentcloud.com/cam/capi?lang=en).
- The SecretKey can be obtained from the [guidance document](https://console.tencentcloud.com/cam/capi?lang=en). The SecretKey can only be viewed when creating the key, please save it in time.
- Voice type can be obtained from the [voice list](https://www.tencentcloud.com/document/product/1154/48916?lang=en).

We provide default parameters for other configurations; you can fine-tune them according to your needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cdebb9bc211311f0948f52540099c741.png)

When selecting Minimax as the TTS providex:

- The APIKey can be obtained from the [Minimax management console](https://platform.minimaxi.com/user-center/basic-information/interface-key).
- GroupID can be obtained from the [Minimax management console](https://platform.minimaxi.com/user-center/basic-information).
- The voice ID can be obtained by referring to the [guidance document](https://platform.minimaxi.com/document/T2A%20V2?key=66719005a427f0c8a5701643).

We provide default parameters for other configurations; you can fine-tune them according to your needs.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e9b10911211311f08caa5254005ef0f7.png)

## Homepage Introduction

### Starting Talking

- AI noise suppression: To use this feature, you need to activate the [RTC-Engine Monthly Packages](https://www.tencentcloud.com/document/product/647/56025) standard or pro version.
- During the conversation, it supports editing and modifying interruption duration, LLM configuration, and TTS configuration to facilitate effect evaluation.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9086cc17e8f411efb98e525400e889b2.png)

- Region: The system defaults to the nearest access region to reduce delay. You can also select a region freely.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/40e7f810edf511ef840e52540044a08e.png)

- During the conversation, if there is a **display of error codes**: Please note that some error codes may block the dialogue. Modify the configuration according to the error prompt in time. If it cannot be resolved, **copy the Task ID and Round ID information** and [contact us]( https://t.me/+EPk6TMZEZMM5OGY1) for query. Some error codes do not affect the normal progress of the dialogue, such as response timeout, which you can handle according to the actual situation.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bfc3f27fed2511efab2f5254007c27c5.png)

### View Latency Metrics

You can check the latency rate at any time during the conversation to select a low-latency model.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2dbe993e8f411efab2f5254007c27c5.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/68cb4d47ed0f11efa1f2525400bf7822.png)

### Quick Integration

We support users in quickly implementing Conversational AI in their local environments. The parameters filled in during system configuration have been preset and do not need to be filled in again (currently supports web).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b2c71551e8f411efab2f5254007c27c5.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7f4317cce8f411ef93475254005ef0f7.png)


---
*Source: [https://trtc.io/document/68137](https://trtc.io/document/68137)*
