# Message Translation

## Feature Overview

Text Message Translation allows users to translate text messages directly within the chat interface. To use this feature, long-press any text message in the message list and select **Translate** from the menu to view the translated text.

> **Noteï¼**The Text Message Translation feature is available to **Pro Plus and Enterprise edition** customers. To enable this feature, [purchase Pro edition Plus or Enterprise edition](https://console.trtc.io/subscription/buy/chat?packType=pro&language=en). The Trial Edition offers [limited free usage](https://www.tencentcloud.com/document/product/1047/67651#0182a443-4747-42cb-b5de-ad165eb5a2ff) for one month.

## Text Message Translation

| Translate Button | Text Message Translation Result |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/488d9239025b11f18e6252540073fd3b.jpeg) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f788704025b11f18e6252540073fd3b.jpeg) |

## Configure Target Language

The target language for translation is managed by `AppBuilder`. To set or retrieve the target language, refer to the [demo](https://github.com/Tencent-RTC/TUIKit_Flutter/blob/main/chat/demo/lib/pages/settings_page.dart):

```
// Set the target language for translationAppBuilder.getInstance().translateConfig.setTargetLanguage('zh');// Get the current target language for translationfinal currentLanguage = AppBuilder.getInstance().translateConfig.targetLanguage;
```

## Enable or Disable Text Message Translation

The `MessageList` widget includes a toggle for the **Text Message Translation** feature in its `config` parameter. By default, this feature is enabled (`true`). To disable it, set the value to `false`:

```
MessageList(  config: ChatMessageListConfig(isSupportTranslate: false),),
```

> **Noteï¼**Only text messages and text-based reference or reply messages are supported. Images, voice, video, files, emojis, custom messages, and other formats are not supported for translation.The maximum translation request rate is 5 times per second.


---
*Source: [https://trtc.io/document/61682](https://trtc.io/document/61682)*
