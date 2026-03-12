# Global

The following content will show you how to set global customized options.

## Switch TUIKit language

API Functionality: Switch TUIKit language.

Method Prototype:

Swift

Objective-C

```
// TUIConfig_Minimalist.swift/** * Switch the language of TUIKit. * The currently supported languages are "en", "zh-Hans", and "ar". */static func switchLanguage(to targetLanguage: String) {    TUIGlobalization.setPreferredLanguage(targetLanguage)}
```

```
// TUIConfig_Minimalist.h/** * Switch the language of TUIKit.  * The currently supported languages are "en", "zh-Hans", and "ar". */+ (void)switchLanguageToTarget:(NSString *)targetLanguage;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the TUIKit interface.TUIConfig_Minimalist.switchLanguage(to: "en")
```

```
// When to call: Before initializing the TUIKit interface.[TUIConfig_Minimalist switchLanguageToTarget:@"en"];
```

Result:

| Set to English | Set to Arabic |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ec9ffd335af711ef998b525400f69702.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eca129ba5af711efb927525400fdb830.png) |

## Enable TUIKit Built-in Prompts

API Functionality: Enable TUIKit built-in toast prompts. If enable, TUIKit components will display the built-in prompts.

Method Prototype:

Swift

Objective-C

```
// TUIConfig_Minimalist.swift/*** Show the toast prompt built in TUIKit.* The default value is YES.*/static func enableToast(_ enable: Bool) {    TUIConfig.default().enableToast = enable}
```

```
// TUIConfig_Minimalist.h/** *  Show the toast prompt built in TUIKit. *  The default value is YES. */+ (void)enableToast:(BOOL)enable;
```

Sample code:

Swift

Objective-C

```
// When to call: Before initializing the TUIKit interface.TUIConfig_Minimalist.enableToast(false)
```

```
// When to call: Before initializing the TUIKit interface.[TUIConfig_Minimalist enableToast:NO];
```

Result:

| Enable Toast Prompts | Disable Toast Prompts |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a4a1ff455af511efb66652540055f650.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/807d43b25af511efb36952540075b605.png) |


---
*Source: [https://trtc.io/document/65369](https://trtc.io/document/65369)*
