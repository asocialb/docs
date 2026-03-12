# Global

The following content will show you how to set global customized options.

## Switch TUIKit language

API Functionality: Switch TUIKit language.

Method Prototype:

```
// TUIConfigMinimalist.java/** * Switch the language of TUIKit.  * The currently supported languages are "en", "zh", and "ar". */public static void switchLanguageToTarget(Context context, String targetLanguage)
```

Sample code:

```
// When to call: In the application initialization phase.TUIConfigMinimalist.switchLanguageToTarget(context, "en");
```

Result:

| Set to English | Set to Arabic |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/92c1bd4b8f4a11ef9897525400d5f8ef.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/92b81d468f4a11efb3eb525400bdab9d.png) |

## Enable TUIKit Built-in Prompts

API Functionality: Enable TUIKit built-in toast prompts. If enable, TUIKit components will display the built-in prompts.

Method Prototype:

```
// TUIConfigMinimalist.java/** *  Show the toast prompt built in TUIKit. *  The default value is true. */public static void enableToast(boolean enableToast)
```

Sample code:

```
// When to call: Before initializing the TUIKit interface.TUIConfigMinimalist.enableToast(false);
```

Result:

| Enable Toast Prompts | Disable Toast Prompts |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/92b6f39c8f4a11efac345254002693fd.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/92b440488f4a11efb3eb525400bdab9d.png) |


---
*Source: [https://trtc.io/document/65364](https://trtc.io/document/65364)*
