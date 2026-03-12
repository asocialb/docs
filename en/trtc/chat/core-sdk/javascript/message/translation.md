# Translation

## Feature Overview

The message translation feature currently supports the translation of text messages only, which can be triggered by manual API calls. Non-text messages such as image, video, file, audio, and custom messages cannot be translated.

> **Note:**The message translation feature is only available to customers of **Pro Plus and Enterprise**. It can be used after [purchasing Pro Plus and Enterprise](https://console.trtc.io/subscription/buy/chat?packType=pro&language=en); the Free Trial version supports [a certain limit of free trial](https://www.tencentcloud.com/document/product/1047/67651#0182a443-4747-42cb-b5de-ad165eb5a2ff), valid for one month.

## UI Display

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1f9d9e851db311ef95b8525400e64ebc.png)

## Translating Text Messages

##### API

```
chat.translateText(options);
```

##### Parameters

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| sourceTextList | Array<String> | List of texts to be translated. |
| sourceLanguage | String | Source Language. 'auto' indicates the SDK automatically identifies the source language. |
| targetLanguage | String | Target Language. For example:English - 'en'Simplified Chinese - 'zh'French - 'fr'German - 'de' |

##### Return value

`Promise`

##### Examples

```
// Translate Arabic to Chineselet promise = chat.translateText({  sourceTextList: ['ÙØ±Ø­Ø¨ÙØ§'],  sourceLanguage: 'auto',  targetLanguage: 'en'});promise.then(function(imResponse) {  const { translatedTextList } = imResponse.data;}).catch(function(imError) {  // error code 2117 indicates translation failed  console.warn('translateText error:', imError);});
```

```
// Translate English to Chineselet promise = chat.translateText({  sourceTextList: ['Hello Tencent', 'Build in-app chat with Tencent Cloud Chat'],  sourceLanguage: 'auto',  targetLanguage: 'zh'});promise.then(function(imResponse) {  const { translatedTextList } = imResponse.data;}).catch(function(imError) {  // error code 2117 indicates translation failed  console.warn('translateText error:', imError);});
```

## Supported Text Translation Languages

| Source Language | Supported Target Language |
| --- | --- |
| zh (Simplified Chinese) | en (English), ja (Japanese), ko (Korean), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian), pt (Portuguese), vi (Vietnamese), id (Bahasa Indonesian), th (Thai), and ms (Malay) |
| zh-TW (Traditional Chinese) | en (English), ja (Japanese), ko (Korean), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian), pt (Portuguese), vi (Vietnamese), id (Bahasa Indonesian), th (Thai), and ms (Malay) |
| en (English) | zh (Simplified Chinese), ja (Japanese), ko (Korean), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian), pt (Portuguese), vi (Vietnamese), id (Bahasa Indonesian), th (Thai), ms (Malay), ar (Arabic), and hi (Hindi) |
| ja (Japanese) | zh (Simplified Chinese), en (English), ko (Korean) |
| ko (Korean) | zh (Simplified Chinese), en (English), ja (Japanese) |
| fr (French) | zh (Simplified Chinese), en (English), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian), and pt (Portuguese) |
| es (Spanish) | zh (Simplified Chinese), en (English), fr (French), it (Italian), de (German), tr (Turkish), ru (Russian), and pt (Portuguese) |
| it (Italian) | zh (Simplified Chinese), en (English), fr (French), es (Spanish), de (German), tr (Turkish), ru (Russian), and pt (Portuguese) |
| de (German) | zh (Simplified Chinese), en (English), fr (French), es (Spanish), it (Italian), tr (Turkish), ru (Russian), and pt (Portuguese) |
| tr (Turkish) | zh (Simplified Chinese), en (English), fr (French), es (Spanish), it (Italian), de (German), ru (Russian), and pt (Portuguese) |
| ru (Russian) | zh (Simplified Chinese), en (English), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), and pt (Portuguese) |
| pt (Portuguese) | zh (Simplified Chinese), en (English), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), and ru (Russian) |
| vi (Vietnamese) | zh (Simplified Chinese), en (English) |
| id (Bahasa Indonesian) | zh (Simplified Chinese), en (English) |


---
*Source: [https://trtc.io/document/55857](https://trtc.io/document/55857)*
