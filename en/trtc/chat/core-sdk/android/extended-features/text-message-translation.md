# Text Message Translation

### Plugin Feature

After entering the Chat interface, you can manually long-press a text message item in the message list. In the menu that appears, click the **translation button** to translate the text.

> **Note:**The message translation feature is provided by the plugin. It is required to integrate `TUITranslationPlugin`, which is supported by version 7.2 and later.The message translation feature is only available to customers of Pro Plus and Enterprise. It can be used after [purchasing Pro Plus and Enterprise](https://console.trtc.io/subscription/buy/chat?packType=pro&language=en); the Free Trial version supports [a certain limit of free trial](https://trtc.io/document/67651?product=chat&menulabel=core%20sdk&platform=javascript#0182a443-4747-42cb-b5de-ad165eb5a2ff), valid for one month.

- If you do not need the translation feature, do not integrate this plugin. The **translation button** will not appear when you long-press a text message.
- If you need the translation feature, integrate `TUIChat` and `TUITranslationPlugin`. For integration methods, refer to Integration Basics ([Android](https://www.tencentcloud.com/document/product/1047/50057#)/[iOS](https://www.tencentcloud.com/document/product/1047/50056#)). No additional settings are required after integration, and the **translation button** will automatically appear when you long-press a text message.

After integrating `TUITranslationPlugin`, you can also set the target language for translation in the **Me** interface. The default target language is the current language used by `TUIChat`.

> **Note:**`TUITranslationPlugin` is dependent on `TUIChat` and cannot be integrated separately.Only text messages, text quotes, and text reply messages support translation. Image, audio, video, file, emoji, and custom messages do not support translation.Not all source languages can be translated into the target languages. For example, English can be translated into Hindi, but Chinese cannot. Refer to [Supported Languages for Translation](https://trtc.io/zh/document/53434) for the currently supported languages. If the translation fails, refer to this document to switch the source or target language.


---
*Source: [https://trtc.io/document/65360](https://trtc.io/document/65360)*
