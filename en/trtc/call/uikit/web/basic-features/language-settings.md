# Language Settings

## Supported Languages

Currently supports **Simplified Chinese, English, Japanese**.

## Switch Language

TUICallKit will prioritize the browser language. If it is one of Chinese, English, or Japanese, the browser language will be used. Otherwise, English will be used. If you want to switch languages, you can use the [setLanguage](https://www.tencentcloud.com/document/product/647/51015#setLanguage) interface.

```
import { TUICallKitAPI, CallMediaType } from '@trtc/calls-uikit-vue';TUICallKitAPI.setLanguage("zh-cn"); // "en" | "zh-cn" | "ja_JP"
```

## Add New Language

If you need support for other languages, you can modify the language source file via source code integration.

### Step 1: Source Code Integration

> **Note:**Source code integration is suitable for `Vue + TypeScript` projects and `TUICallKit` version 3.2.2 or above.

1. **Download Source Code**

Vue3

```
npm install @trtc/calls-uikit-vue
```

2. **Copy the source code into your own project, taking copying into the**`src/components/`**directory as an example:**

macOS + Vue3

Windows + Vue3

```
mkdir -p ./src/components/TUICallKit && cp -r ./node_modules/@trtc/calls-uikit-vue/* ./src/components/TUICallKit
```

```
xcopy .\\node_modules\\@trtc\\calls-uikit-vue  .\\src\\components\\TUICallKit /i /e
```

3. **Modify Import Path**

You need to change TUICallKit to import from a local file, as shown in the code below. For other usage details, refer to [TUICallKit Quick Integration](https://www.tencentcloud.com/zh/document/product/647/50993).

```
import { TUICallKit, TUICallKitAPI, CallMediaType } from "./components/TUICallKit/src/index";
```

4. **Solve Errors That May Be Caused by Copying Source Code**

If you encounter an error while using the TUICallKit component, please don't worry. In most cases, this is due to inconsistencies between ESLint and TSConfig configurations. You can consult the documentation and configure correctly as required. If you need help, please feel free to contact us, and we will ensure that you can successfully use this component. Here are some common issues:

ESLint Error

TypeScript Error

If the TUICallKit causes an error due to inconsistency with your project's code style, you can block this component directory by adding a `.eslintignore` file in the root directory of your project, for example:

```
# .eslintignoresrc/components/TUICallKit
```

1. If you encounter the 'Cannot find module '../package.json'' error, it's because TUICallKit references a JSON file. You can add the related configuration in tsconfig.json, example:

```
{  "compilerOptions": {    "resolveJsonModule": true  }}
```

For other TSConfig issues, please refer to [TSConfig Reference](https://www.typescriptlang.org/tsconfig).

2. If you encounter the 'Uncaught SyntaxError: Invalid or unexpected token' error, it's because TUICallKit uses decorators. You can add the related configuration in tsconfig.json, example:

```
{  "compilerOptions": {    "experimentalDecorators": true  }}
```

### Step 2: Add a new language pack

**For example, adding Vietnamese:**

1. Create the target language source file.

Add a new file named vi.ts in the src/components/TUICallKit/src/TUICallService/locales directory. Copy the contents of src/components/TUICallKit/src/TUICallService/locales/zh-cn.ts to vi.ts and then translate the JSON values into Vietnamese.

```
export const vi = {    // Note the export variable here  'hangup': 'Hang Up',  'reject': 'Reject',  'accept': 'Acceptance',  'camera': 'Camera',  'microphone': 'Microphone',  'speaker': 'Speaker',  'open camera': 'Turn on the camera',  'close camera': 'Turn off the camera',  'open microphone': 'Open microphone',  'close microphone': 'Turn off the microphone',  'video-to-audio': 'Switch to audio call',  'virtual-background': 'Blur background',  'other side reject call': 'The other side has rejected',  'reject call': 'Reject call',  'cancel': 'Cancel call',  ...};
```

2. Export from index.ts

Modify the src/components/TUICallKit/src/TUICallService/locales/index.ts file.

```
import { TUIStore } from '../CallService/index';import { NAME, StoreName } from '../const/index';import { en } from './en';import { zh } from './zh-cn';import { ja_JP } from './ja_JP';import { vi } from './vi';  // Import new language file.....export const languageData: languageDataType = {  en,  'zh-cn': zh,  ja_JP,  vi,       // Export new language file};
```

3. Add new LanguageType enum.

Modify the src/components/TUICallKit/src/TUICallService/const/call.ts

```
export enum LanguageType {  EN = 'en',  'ZH-CN' = 'zh-cn',  JA_JP = 'ja_JP',  VI = 'vi',   // Add new enum type}
```

4. Switch Language

Switch languages in the project by calling the [setLanguage](https://www.tencentcloud.com/document/product/647/51015#setLanguage) interface.

```
import { TUICallKitAPI, CallMediaType } from '@trtc/calls-uikit-vue';TUICallKitAPI.setLanguage("vi");
```


---
*Source: [https://trtc.io/document/62424](https://trtc.io/document/62424)*
