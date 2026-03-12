# Translate Message

## Feature Description

Starting from version v2.1.0, TUIKit offers a text message translation feature. The messaging tool in the TUIChat component supports translating text messages. Currently, it can translate from mainstream languages to languages such as English, Chinese, Russian, Japanese, Korean, and more. For details on supported languages, see the [Text Translation Support List](https://www.tencentcloud.com/document/product/1047/60746#437f6f49-c77f-4b59-b138-7c219e8d21f8).

After text translation, the results will be retained for the duration of the current login session, and remain saved even after conversation switching. If you switch conversations and change the target language for translation, the previous translation results will automatically be translated into the new target language.

> **Note:**The text message translation feature is currently offered for free. You can contact us through the [Telegram technical exchange group](https://t.me/+EPk6TMZEZMM5OGY1) to enable and experience the full feature.

## ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/37576d581cbc11efb7495254005ac0ca.png)

## **Feature Introduction**

### Setting the Target Language for Translation

The default target language for translation is Chinese, but you can also manually switch the target language. Import `TUIChatService` from `@tencentcloud/chat-uikit-engine` and call the `setTranslationLanguage` method, as shown in the following code:

```
import { TUIChatService } from "@tencentcloud/chat-uikit-engine";// Switches to English.TUIChatService.setTranslationLanguage('en');// Switches to Chinese.TUIChatService.setTranslationLanguage('zh');// Switches to Japanese and supports other languages as well.TUIChatService.setTranslationLanguage('jp');
```

> **Note:**Logging in again will reset the default translation to Chinese.

### Setting the Source Language for Translation

Currently, in TUIKit, it is **default and recommended** to use automatic detection of the source language, but you can also manually set the source language to ensure the accuracy of the translation.

In `TUIChat/utils/translation.ts`, a translation utility class `Translator` is implemented, where you can change the `sourceLanguage` attribute according to the [Text Translation Language Support List](https://www.tencentcloud.com/document/product/1047/60746#437f6f49-c77f-4b59-b138-7c219e8d21f8).

```
TUIChatService.translateText({    sourceTextList: [text],    sourceLanguage: 'auto', // zh/en/jp/kr}).then((response) => {    // response data});
```

### Extended Reading

The following content serves as supplementary reading material only. Text message translation and related features have been implemented in TUIKit 2.1.0 and later, and do not require manual implementation by users.

### Checking Whether the Current Package Supports the Translation Feature

By querying the `StoreName.APP` in `TUIStore` for the key `enabledTranslationPlugin`, the obtained boolean value indicates whether the feature is enabled.

```
const enable = TUIStore.getData(StoreName.APP, 'enabledTranslationPlugin');
```

### Removing the Translation Feature

In the file `TUIKit/components/TUIChat/message-list/message-tool/index.vue`, simply delete the object with the key `translate` in `actionItems`.

```
{    key: 'translate',    text: TUITranslateService.t('TUIChat.Translation'),    visible: false,    iconUrl: translateIcon,    renderCondition() {},    clickEvent: translateMessage,}
```

### Text Translation Language Support List

| Source Language | Supported Target Language |
| --- | --- |
| zh (Simplified Chinese) | en (English), ja (Japanese), ko (Korean), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian), pt (Portuguese), vi (Vietnamese), id (Indonesian), th (Thai), ms (Malay) |
| zh-TW (Traditional Chinese) | en (English), ja (Japanese), ko (Korean), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian), pt (Portuguese), vi (Vietnamese), id (Indonesian), th (Thai), ms (Malay) |
| en (English) | zh (Chinese), ja (Japanese), ko (Korean), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian), pt (Portuguese), vi (Vietnamese), id (Indonesian), th (Thai), ms (Malay), ar (Arabic), hi (Hindi) |
| ja (Japanese) | zh (Chinese), en (English), ko (Korean) |
| ko (Korean) | zh (Chinese), en (English), ja (Japanese) |
| fr (French) | zh (Chinese), en (English), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian), pt (Portuguese) |
| es (Spanish) | zh (Chinese), en (English), fr (French), it (Italian), de (German), tr (Turkish), ru (Russian), pt (Portuguese) |
| it (Italian) | zh (Chinese), en (English), fr (French), es (Spanish), de (German), tr (Turkish), ru (Russian), pt (Portuguese) |
| de (German) | zh (Chinese), en (English), fr (French), es (Spanish), it (Italian), tr (Turkish), ru (Russian), pt (Portuguese) |
| tr (Turkish) | zh (Chinese), en (English), fr (French), es (Spanish), it (Italian), de (German), ru (Russian), pt (Portuguese) |
| ru (Russian) | zh (Chinese), en (English), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), pt (Portuguese) |
| pt (Portuguese) | zh (Chinese), en (English), fr (French), es (Spanish), it (Italian), de (German), tr (Turkish), ru (Russian) |
| vi (Vietnamese) | zh (Chinese), en (English) |
| id (Indonesian) | zh (Chinese), en (English) |
| th (Thai) | zh (Chinese), en (English) |
| ms (Malay) | zh (Chinese), en (English) |
| ar (Arabic) | en (English) |
| hi (Hindi) | en (English) |


---
*Source: [https://trtc.io/document/60746](https://trtc.io/document/60746)*
