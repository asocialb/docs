# Speech-To-Text Configuration

this document mainly introduces how to configure third-party `STT` in the [StartAIConversation](https://trtc.io/document/64963?product=rtcengine&menulabel=serverfeaturesapis) API. Currently, we support access to Azure and Deepgram. If you have other needs, please feel free to [contact us](https://trtc.io/contact).

## Request Example

`STTConfig` supports a parameter `CustomParam`. See the following example to configure third-party `STT`:

```
"STTConfig": {    "Language": "zh",    "VadSilenceTime": 1200,    "CustomParam": "{\\"STTType\\": \\"azure\\",                      \\"SubscriptionKey\\": \\"xxxxx\\",                      \\"Region\\": \\"chinanorth3\\"}",  },}
```

## Supported Third-Party STT Configurations

### Azure STT

```
{    "STTType": "azure", // required: String STT type    "SubscriptionKey": "xxxxx", // required: String Subscription key    "Region": "chinanorth3" // required: String region}
```

**Example:**

```
"CustomParam": "{\\"STTType\\": \\"azure\\", \\"SubscriptionKey\\": \\"xxxxx\\", \\"Region\\": \\"chinanorth3\\"}"
```

For more details, please refer to: [https://learn.microsoft.com/en-us/azure/ai-services/speech-service/speech-to-text](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/speech-to-text).

### Deepgram STT

```
{    "STTType": "deepgram", // required: String STT type    "ApiKey": "XXXXXX", // required: String Authentication    "Model": "nova-2" // required: String Select STT Model}
```

**Example:**

```
"CustomParam": "{\\"STTType\\": \\"deepgram\\", \\"AppKey\\": \\"xxxxx\\", \\"Model\\": \\"nova-2\\"}"
```

For more details, please refer to: [https://developers.deepgram.com/docs/models-languages-overview](https://developers.deepgram.com/docs/models-languages-overview).


---
*Source: [https://trtc.io/document/69592](https://trtc.io/document/69592)*
