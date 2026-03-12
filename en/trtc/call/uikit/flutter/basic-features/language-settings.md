# Language Settings

## Supported Languages

Currently supported languages are **Simplified Chinese, English, and Japanese,** with the default language being   **English .**

## Switch Language

`TUICallKit` does not provide a separate interface for language switching, `TUICallKit` automatically switches languages based on the current `Application`'s `MaterialApp` (or CupertinoApp, etc. style components) language setting. Simply change the language used by `MaterialApp` (or CupertinoApp, etc. style components).

## Add New Language

### Step 1: Source Code Integration

1. Download Source Code

Go to   [`https://pub.dev/packages/tencent_calls_uikit`](https://pub.dev/packages/tencent_calls_uikit) to download the latest   `TUICallKit`  source code.

2. Depend on Local Source Code

In the  `Application`  project's `pubspec.yaml` file, modify `TUICallKit`   to local dependency:

```
dependencies:  tencent_calls_uikit:
    path: /TUICallKit local_path/
```

### Step 2: Add a new language pack

#### Using **Spanish** as an example:

1. Add a new Spanish language file.

Go to the  `TUICallKit`  source code directory's  `lib/src/i18n`  folder and add `strings_es.i18n.json`  .

2. Copy the contents from  `lib/src/i18n/strings.i18n.json`  to the newly added  `lib/src/i18n/strings_es.i18n.json`  file.
3. Translate the English content in  `lib/src/i18n/strings_es.i18n.json`  to Spanish.
4. Update Translation Package

In the  `TUICallKit`  source code directory, go to  TCCLI , and run the following commands to update the translation package:

```
  flutter pub add fast_i18nflutter pub run fast_i18n
```

5. Update the language adaptation method for  `TUICallKit` .

Navigate to  `lib/src/i18n/i18n_utils.dart`  source file and modify the  `setLanguage`  method as follows:

```
  static setLanguage(Locale currentLocale) {
  switch (currentLocale.languageCode) {
    case 'zh':
      {
        CallKitI18nUtils(null, 'zh');
        break;
      }
    case 'en':
      {
        CallKitI18nUtils(null, 'en');
        break;
      }
    case 'ja':
      {
        CallKitI18nUtils(null, 'ja');
        break;
      }    // Add case 'es'
    case 'es':
      {
        CallKitI18nUtils(null, 'es');
        break;
      }
  }
}
```


---
*Source: [https://trtc.io/document/63265](https://trtc.io/document/63265)*
