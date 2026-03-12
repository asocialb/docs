# Language

## Feature Description

React UIKit has built-in **English, Japanese, Korean, Chinese (Simplified), and Chinese (Traditional)** language packs as the interface display language.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c0fded35621711f0ad0f5254005ef0f7.png)

## Using Default Supported Languages

If your App only requires **English, Japanese, Korean, Chinese (Simplified), or Chinese (Traditional)**, and does not need new entries or modifications to existing translations, see this section. The following languages are supported by default:

- `en-US` - English
- `zh-CN` - Simplified Chinese
- `zh-TW` - Traditional Chinese
- `ja-JP` - Japanese
- `ko-KR` - Korean
- `auto` - auto-detection

Among them, automatic detection (`auto`) selects the language in the following priority:

1. Browser language settings.
2. System language settings.
3. Fall back to `en-US` by default.

### Specify a Language

Wrap your application with `UIKitProvider` and set the language attribute:

```
  // language support en-US / zh-CN / ja-JP / ko-KR / zh-TW / auto  <UIKitProvider language={'en-US'}>...</UIKitProvider>
```

### Dynamically Switch Language

Outside `UIKitProvider`, dynamically switch React UIKit language.

```
import { UIKitProvider, ConversationList } from '@tencentcloud/chat-uikit-react';function App() {  const [lang, setLang] = useState<'en-US' | 'zh-CN' | 'zh-TW' | 'ja-JP' | 'ko-KR'>('en-US');  return (    <div>      <button onClick={() => setLang('zh-CN')}>Chinese</button>      <button onClick={() => setLang('en-US')}>English</button>      <div>{`Current language: ${lang}`}</div>      <UIKitProvider        language={lang}        theme="light"      >        <ConversationList />      </UIKitProvider>    </div>  );}
```

`UIKitProvider` within can use the `useUIKit` Hook to access internationalization features. However, since the `useUIKit` Hook is based on Context implementation, it cannot be called externally outside `<UIKitProvider />`.

```
Current language
```

### Using Language Entries

Use the hook `useUIKit` to export the translation function `t`. `useUIKit` as a Hook can only be accessed in child components of `UIKitProvider`.

```
import React from 'react';import { UIKitProvider, useUIKit } from '@tencentcloud/chat-uikit-react';export default function App() {  return (    // init language    <UIKitProvider language='en-US'>      <Child />    </UIKitProvider>  );}function Child() {    const { t } = useUIKit();    return <div>{t('TUIChat.No More')}</div>}
```

## Communication and Feedback

Join the [Telegram Technical Exchange Group](https://t.me/tencent_imsdk) or [WhatsApp communication group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik) to enjoy support from professional engineers and solve your problems.


---
*Source: [https://trtc.io/document/62741](https://trtc.io/document/62741)*
