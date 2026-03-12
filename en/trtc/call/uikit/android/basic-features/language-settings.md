# Language Settings

## Supported Languages

Currently supports **Simplified Chinese, English, Japanese, and Arabic.**

## Switch Language

TUICallKitÂ Default Language matches the mobile system. If you need to switch languages, you can use `TUIThemeManager.getInstance().changeLanguage` to change the language. For example, to switch to English:

```
â¦import com.tencent.qcloud.tuicore.TUIThemeManager;public class MainActivity extends BaseActivity {    @Override
  public void onCreate(Bundle savedInstanceState) {
      super.onCreate(savedInstanceState);
      TUIThemeManager.getInstance().changeLanguage(getApplicationContext(), "en");      â¦    }    â¦}
```

## Add New Language

### Step 1: Source Code Integration

1. Clone or download the code from [GitHub](https://github.com/Tencent-RTC/TUICallKit), then copy the tuicallkit-kt subdirectory under the Android directory to the same level under your current project's app directory, as shown below.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ee158e964fdd11efb66652540055f650.png)

2. Find the `settings.gradle.kts (or settings.gradle)` file in your project's root directory, add the following code to import the `tuicallkit-kt` component into your project.

setting.gradle.kts

settings.gradle

```
include(":tuicallkit-kt")
```

```
include ':tuicallkit-kt'
```

3. In the app directory, find the `build.gradle.kts (or build.gradle)` file, add the following code in the `dependencies` section to declare the current app's dependency on the newly added component.

build.gradle.kts

build.gradle

```
dependencies {    api(project(":tuicallkit-kt"))}
```

```
dependencies {    api project(':tuicallkit-kt')}
```

### Step 2: Add a new language pack

#### Using **Spanish** as an example:

1. Add a new Spanish language file.

Navigate to the  `TUICallKit`  source code file directory under the  `src/main/res`  directory, and add a new  `value-es/strings.xml` file .

2. Copy the contents of  `src/main/res/values-en/strings.xml`  to the newly added  `src/main/res/values-es/strings.xml`  file.
3. Translate the English in  `src/main/res/values-es/strings.xml`  to Spanish.
4. Add new language.

```
  â¦import com.tencent.qcloud.tuicore.TUIThemeManager;public class MainActivity extends BaseActivity {    @Override  public void onCreate(Bundle savedInstanceState) {      super.onCreate(savedInstanceState);      Locale locale = new Locale("es");
      TUIThemeManager.addLanguage("es", locale);      â¦    }    â¦}
```


---
*Source: [https://trtc.io/document/63264](https://trtc.io/document/63264)*
