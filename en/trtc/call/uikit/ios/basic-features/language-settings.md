# Language Settings

## Supported Languages

Currently supports **Simplified Chinese, English, Japanese, and Arabic.**

## Switch Language

TUICallKit defaults to the same language as the phone system . If you need to switch languages, you can use `TUIGlobalization.setPreferredLanguage` to switch languages, taking switching to English as an example:

```
â¦import TUICorefunc steLanguage() {    TUIGlobalization.setPreferredLanguage("en")}
```

## Add New Language

### Step 1: Source Code Integration

1. Clone/download the code from [GitHub](https://github.com/Tencent-RTC/TUICallKit).
2. Download the TUICallKit source code dependency to local in the Podfile file of the Application project.

```
  target 'TUICallKitApp' do  use_frameworks!  â¦  pod 'TUICallKit-Swift/Professional', :path => "Your Download Path/TUICallKit/iOS"  end
```

3. Run the `pod update` command to update dependencies.

### Step 2: Add a new language pack

#### Using **Spanish** as an example:

1. Add a new Spanish language file.

Navigate to the `TUICallKit` source file directory, under iOS/TUICallKit-Swift/Resources, and create a new `es.lproj/Localized.strings` file.

2. Copy the content in  `iOS/TUICallKit-Swift/Resources/en.lproj/Localized.strings`   into the newly added  `iOS/TUICallKit-Swift/Resources/es.lproj/Localized.strings`  file.
3. Translate the English content in `iOS/TUICallKit-Swift/Resources/es.lproj/Localized.strings` to Spanish.
4. Navigate to the directory containing the  Application  projectâs   Podfile  and execute the  `pod install ` command to update dependencies.

```
  â¦import com.tencent.qcloud.tuicore.TUIThemeManager;public class MainActivity extends BaseActivity {    @Override  public void onCreate(Bundle savedInstanceState) {      super.onCreate(savedInstanceState);      Locale locale = new Locale("es");
      TUIThemeManager.addLanguage("es", locale);      â¦    }    â¦}
```


---
*Source: [https://trtc.io/document/63263](https://trtc.io/document/63263)*
