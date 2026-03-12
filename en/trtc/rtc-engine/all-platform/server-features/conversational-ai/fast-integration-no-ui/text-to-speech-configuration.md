# Text-To-Speech Configuration

This document describes how to configure the `TTSConfig` parameter of the [StartAIConversation](https://trtc.io/document/64963?product=rtcengine&menulabel=serverfeaturesapis) API.

Use TRTCâs built-in TTS or bring your own (BYO) third-party TTS service.

## TRTC TTS Configuration

If you choose TRTC Real-Time TTS for your conversational AI scenarios, follow the guide below for rapid integration. For service activation and billing rules, refer to [Billing instructions](https://trtc.io/document/67832?product=pricing).

```
{  "TTSType": "flow",  // [Required] Fixed value.  "VoiceId": "v-female-R2s4N9qJ", // [Required] Premium or Cloned Voice ID. Refer to the "Voice List" below for available IDs  "Model": "flow_01_turbo", //[Required] The current default TTS model version.  "Speed": 1.0,    //[Optional] Speech rate. Range: [0.5-2.0]. Default: 1.0. Higher values indicate faster speech.  "Volume": 1.0,   // [Optional] Volume level. Range: [0, 10]. Default: 1.0. Higher values indicate louder volume.  "Pitch": 0,   // [Optional] Pitch adjustment. Range: [-12, 12]. Default: 0 (original tone).Higher values result in a higher pitch.  "Language": "zh" // [Optional] Recommended. Language ID; Supports "zh" (Chinese), "en" (English), "yue" (Chinese-Cantonese). Standard: ISO 639-1.}
```

> **Noteï¼**TRTC TTS offers a library of premium voices in Chinese and English, as listed in the table below. For additional voice or language requirements, please [contact us](https://trtc.io/contact).To integrate a third-party TTS service for your Conversational AI scenarios, please refer to [BYO TTS Configurations](https://www.tencentcloud.com/document/product/647/68340#74f3d053-15a7-44ee-ae1d-3a1eba0b4f0e).

#### Voice Library

The TRTC premium TTS voice library are listed below. You can select and configure a voice based on your preferences.

| **Voice Name** | **Voice ID** | **Language** | **Language ID** |
| --- | --- | --- | --- |
| Commanding CEO - Male | v-male-Bk7vD3xP | Chinese | zh |
| Gentle Lady | v-female-R2s4N9qJ | Chinese | zh |
| Tsundere Girl | v-female-m1KpW7zE | Chinese | zh |
| Cutesy Girl | v-female-U8aT2yLf | Chinese | zh |
| Casual Man | v-male-s5NqE0rZ | Chinese | zh |
| Natural Man | v-male-W1tH9jVc | Chinese | zh |
| Customer Service - Xiaomei (Sweet Girl) | female-kefu-xiaomei | Chinese | zh |
| Customer Service - Xiaoxin (Soft Female) | female-kefu-xiaoxin | Chinese | zh |
| Customer Service - Xiaoyue (Cheerful Female) | female-kefu-xiaoyue | Chinese | zh |
| Customer Service - Xiaoxu (Professional Male) | male-kefu-xiaoxu | Chinese | zh |
| Articulate Narrator - Female | v-female-p9Xy7Q1L | English (US) | en |
| Analytical Presenter - Female | v-female-Z3x9LmQ2 | English (US) | en |
| Scholarly Lecturer - Male | v-male-A4b9KqP2 | English (US) | en |
| Expert Analyst - Male | v-male-r7K2pQ9L | English (US) | en |
| Calm Reviewer - Male | v-male-Q6p8ZxL3 | English (US) | en |
| Mindfulness Coach - Female | v-female-T3s8BqL9 | English (US) | en |
| Gentle Mentor - Male | v-male-P6q7LzD8 | English (US) | en |
| Reserved Broadcaster - Female | v-female-M7k2PxL9 | English (US) | en |
| Serene Voice Actress | v-female-S5n9QxJ4 | English (US) | en |
| Composed Voice Actress | v-female-T8m4WxP7 | English (US) | en |
| Resonant Reviewer - Male | v-male-D6p3KxN8 | English (US) | en |
| Empathic Host - Female | v-female-A9b3KfL2 | English (US) | en |
| Sincere Storyteller - Female | v-female-A7h2MxQ5 | English (US) | en |
| Gentle Storyteller - Male | v-male-G4n7RxM3 | English (US) | en |
| Caring Counselor | v-male-H3p9LxK7 | English (US) | en |
| Sincere Streamer - Male | v-male-R6n2MxT9 | English (US) | en |
| Confident Actress | v-female-C8k4NxL6 | English (US) | en |
| Uplifting Speaker - Male | v-male-L7m5QxP4 | English (US) | en |
| Rational Commentator - Male | v-male-N4k8TxR7 | English (US) | en |
| Intellectual Narrator - Female | v-female-B7k5WxN4 | English (US) | en |
| Elegant Narrator - Female | v-female-k3P8sL0Q | Chinese-Cantonese | yue |
| Composed Narrator - Male | v-male-L4s7PqZ9 | Chinese-Cantonese | yue |

## BYO TTS Configurations

If you choose to bring your own (BYO) third-party TTS service, you will need to prepare the corresponding TTS service account and API key. Please refer to the following sections for configuration instructions regarding different service providers.

#### Azure TTS

```
{    "TTSType": "azure", // Required. TTS type in string format.    "SubscriptionKey": "xxxxxxxx", // Required. Subscription key in string format.    "Region": "southeastasia",  // Required. Subscription region in string format.    "VoiceName": "en-US-AmandaMultilingualNeural", // Required. Timbre name in string format.    "Language": "en-US", // Required. Language for TTS in string format.     "Rate": 1 // Optional. Speech speed in float format. Value range: 0.5â2. Default value: 1.}
```

See [Azure language and voice support](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/language-support?tabs=stt)

#### Cartesia TTS

```
{    "TTSType": "cartesia", // Required. TTS type in string format.     "Model": "sonic-multilingual", // Required. Model.    "APIKey": "eyxxxx", // Required. Obtained API key.    "VoiceId": "eda5bbff-1ff1-4886-8ef1-4e69a77640a0" // Required. Timbre ID. Visit https://play.cartesia.ai/ for details.}
```

See [Cartesia TTS](https://docs.cartesia.ai/get-started/overview)

#### ElevenLabs TTS

```
{    "TTSType": "elevenlabs", // // Required. String. Specifies the TTS provider type.    "Model": "eleven_turbo_v2_5", // Required. Model Type.    "APIKey": "eyxxxx", // Required. The API key used to authenticate requests.    "VoiceId": "eda5bbff-1ff1-4886-8ef1-4e69a77640a0" // Required. The voice ID. See https://elevenlabs.io/docs/api-reference/get-voices for details.}
```

See: [ElevenLabs TTS](https://elevenlabs.io/docs/product/introduction)

#### Tencent TTS

```
{     "TTSType": "tencent", // TTS type in string format. Valid values: "tencent" and "minixmax". Other vendors will be supported in future versions.    "AppId": "Your application ID", // Required. The value is in string format.    "SecretId": "Your key ID", // Required. The value is in string format.  â "SecretKey": "Your key", // Required. The value is in string format.  â "VoiceType": 101001, // Required. Timbre ID in integer format. Standard timbre and premium timbre are supported. The premium timbre is more real, and its price differs from that of the standard timbre. See the TTS billing overview for details. For the complete list of timbre IDs, see the TTS timbre list.  â "Speed": 1.25, // Optional. Speech speed in integer format. Value range: [-2, 6], corresponding to different speech speeds. -2: 0.6 times; -1: 0.8 times; 0: 1.0 times (default value); 1: 1.2 times; 2: 1.5 times; 6: 2.5 times. If you need a more fine-grained speech speed, the value can be accurate to 2 decimal places, such as 0.5, 1.25, and 2.81. For the conversion between the parameter value and actual speech speed, see Speech Speed Conversion.  â "Volume": 5, // Optional. Volume level in integer format. Value range: [0, 10], corresponding to 11 volume levels. The default value is 0, representing the normal volume.    "PrimaryLanguage": 1, // Optional. Primary language in integer format. 1: Chinese (default value); 2: English; 3: Japanese.    "FastVoiceType": "xxxx"   // Optional. Parameter for fast voice cloning.}
```

See [TTS Timbre List - Document Center - Tencent Cloud](https://www.tencentcloud.com/document/product/1154/48916)

#### MiniMax TTS

```
{  "TTSType": "minimax", // Required. String. Specifies the TTS provider type.  "Model": "speech-02-turbo", // Required. The TTS model type.  "APIUrl": "https://api.minimax.chat/v1/t2a_v2",// Required. The API endpoint URL.  "APIKey": "eyxxxx",// Required. String. The API key used for authentication.  "GroupId": "181000000000000", // Required. The MiniMax group ID associated with your account.  "VoiceType": "female-tianmei", // Required. String. The requested voice identifier (voice_id).  "Speed": 1.2 // Optional. Float. Speech speed multiplier. Valid range: [0.5, 2.0]. Default is 1.0.}
```

See [MiniMax](https://platform.minimax.io/docs/api-reference/speech-t2a-http)

For rate limits, see [MiniMax](https://platform.minimax.io/docs/guides/rate-limits#rate-limits). Rate limits may cause response lag.

| API | T2A V2 (Speech generation) | T2A Pro (Speech generation) | T2A (Speech generation) | T2A Stream (Streaming speech generation) | T2A Stream (Streaming speech generation) |
| --- | --- | --- | --- | --- | --- |
|  Model | speech-2.6-hd, speech-2.6-turbo, speech-02-hd, speech-02-turbo, speech-01-hd, speech-01-turbo | speech-01, speech-02 | speech-01, speech-02 | speech-01 | speech-01 |
| Customer type/Limit type | RPM | RPM | RPM | RPM | CONN (maximum number of parallel tasks) |
| Users using a free account | 3 | 3 | 3 | 3 | 1 |
| Users using a paid account | 20 | 20 | 20 | 20 | 3 |

#### Custom TTS

```
{  "TTSType": "custom", // Required. The value is in string format.  "APIKey": "ApiKey", // Required. API key in string format for authentication.  "APIUrl": "http://0.0.0.0:8080/stream-audio", // Required. TTS API URL in string format.  "AudioFormat": "wav", // Optional. Expected output audio format in string format. For example, mp3, ogg_opus, pcm, and wav. Default value: wav. Currently, only pcm and wav are supported.  "SampleRate": 16000,  // Optional. Audio sampling rate in integer format. Default value: 16000 (16 kHz). Recommended value: 16000.  "AudioChannel": 1,    // Optional. Number of audio channels in integer format. Valid values: 1 and 2. Default value: 1.}
```

For specific protocol specifications, see [Custom TTS protocol](https://www.tencentcloud.com/document/product/647/65315).


---
*Source: [https://trtc.io/document/68340](https://trtc.io/document/68340)*
