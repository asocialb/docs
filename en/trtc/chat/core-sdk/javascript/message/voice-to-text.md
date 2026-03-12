# Voice-to-Text

## Feature Overview

The Speech-to-Text feature supports recognizing the VMS you **sent successfully or received**, converting it into text.

> **Note:**Speech-to-Text is a **Value-Added Paid Feature**, currently in a free trial phase. You can contact us through the [Telegram Technical Support Group](https://t.me/+EPk6TMZEZMM5OGY1) to activate the full feature experience.Supported by v3.1.3 or later.

## UI Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e5c3cb681f2c11efafe1525400db4520.png)

## convertVoiceToText

The Speech-to-Text interface. Audio format support includes wav, pcm, ogg-opus, speex, silk, mp3, m4a, aac, amr.

##### API

```
chat.convertVoiceToText(options);
```

##### Parameters

The options parameter is of the Object type, and contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| message | Message | Audio Message |
| language | String \| undefined | Language type, defaults to Chinese-English-Cantonese Speech-to-Text. Other selectable types:zh (cmn-Hans-CN), Universal Chineseen-US, Englishyue-Hant-HK, Cantoneseja-JP, Japanese |

##### Return value

`Promise`

##### Examples

```
// Most commonly used Chinese-English-Cantonese Speech-to-Text, the language parameter can be omittedlet promise = chat.convertVoiceToText({ message });promise.then(function(imResponse)) {  // Speech-to-Text Conversion Successful  const { result } = imResponse.data;}).catch(function(imError) {  // Speech-to-Text Conversion Failed  console.warn('convertVoiceToText error:', imError);});
```

```
// Japanese Speech-to-Textlet promise = chat.convertVoiceToText({ message, language: 'ja-JP'});promise.then(function(imResponse)) {  // Speech-to-Text Conversion Successful  const { result } = imResponse.data;}).catch(function(imError) {  // Speech-to-Text Conversion Failed  console.warn('convertVoiceToText error:', imError);});
```


---
*Source: [https://trtc.io/document/60751](https://trtc.io/document/60751)*
