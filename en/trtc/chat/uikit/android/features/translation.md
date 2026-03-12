# Translation

## Description

The text message translation feature allows you to manually long press a text message bubble in the message list after you enter the chat interface, and then click the Translate button in the pop-up menu to translate the text.

> **Note:**Text translation is a value-added paid feature, which is in the beta phase currently. You can contact us through the [Telegram Technical Group](https://t.me/+EPk6TMZEZMM5OGY1) to enable and experience the full feature.The message translation feature is only available to customers of **Pro Plus and Enterprise**. It can be used after [purchasing Pro Plus and Enterprise](https://console.trtc.io/subscription/buy/chat?packType=pro&language=en); the Free Trial version supports [a certain limit of free trial](https://www.tencentcloud.com/document/product/1047/67651#0182a443-4747-42cb-b5de-ad165eb5a2ff), valid for one month.

## Effect Display

The effect of integrating the translation plugin is shown below:

Minimalist Edition

| Without the translation plugin integrated, the Translate button is not displayed. | With the translation plugin integrated, the Translate button is displayed. | Text message translation effect |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b40340aa231c11ef860b52540049c929.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af1db83f231c11efbef6525400a8a0fb.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b73b984f231c11efb2cb5254006568c0.png) |

## Feature Overview

### Integrating Plugins

Starting from version 7.2, the translation feature is provided by the plugin `TUITranslationPlugin`.

- If you do not need the translation feature, simply do not integrate the plugin. The Translate button will not be displayed when you long press a text message.
- If you need the translation feature, you must integrate `TUIChat` and `TUITranslationPlugin`. For integration methods, refer to Integrating TUIKit ([Android](https://www.tencentcloud.com/zh/document/product/1047/50057)/[iOS](https://www.tencentcloud.com/zh/document/product/1047/50056)). No further settings are required after integration. The Translate button will be displayed automatically when you long press a text message.

After `TUITranslationPlugin` is integrated, you can also set the target language for translation. The default target language is the current language used by `TUIChat`.

> **Note:**`TUITranslationPlugin` is dependent on `TUIChat` and cannot be integrated individually.Only text messages and text type of quotes or replies are supported. Image, voice, video, file, emoji, and custom messages are not supported for translation.Not all source languages can be translated into the set target language. For example, English can be translated into Hindi, but Chinese cannot be translated into Hindi. For translation languages supported currently, refer to [Supported Text Translation Languages](https://www.tencentcloud.com/zh/document/product/1047/53434#.E6.96.87.E6.9C.AC.E7.BF.BB.E8.AF.91.E8.AF.AD.E8.A8.80.E6.94.AF.E6.8C.81). If translation fails, consult this document to change the source or target language.

## Contact Us

If you have any questions about this feature, feel free to join the [Telegram Technical Group](https://t.me/+EPk6TMZEZMM5OGY1), and obtain reliable technical support from it.


---
*Source: [https://trtc.io/document/60772](https://trtc.io/document/60772)*
