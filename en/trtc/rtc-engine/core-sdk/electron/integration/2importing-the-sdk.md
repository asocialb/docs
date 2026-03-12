# 2.Importing the SDK

This document describes how to quickly integrate the TRTC Electron SDK into your project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/05f95b8937ff11ed8088525400463ef7.png)

## Supported Platforms

- Windows
- macOS

## Importing the SDK

### Step 1. Install Node.js

Windows

macOS

1. Download the latest version of [Node.js](https://nodejs.org/en/download/) installer `Windows Installer (.msi) 64-bit`.
2. Open `Node.js command prompt` in the application list and open a terminal window.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/061313f137ff11edb1de525400c56988.png)

1. Open the terminal window and run the following command to install Homebrew. If you have already installed it, skip this step.

```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Run the following command to install Node.js (v10.0 or later).

```
$ brew install node
```

### Step 2. Install Electron

```
$ npm install electron@latest --save-dev
```

### Step 3. Install the TRTC Electron SDK

```
$ npm install trtc-electron-sdk@latest --save
```

> **Note:**You can view the information of the latest version of the TRTC Electron SDK [here](https://www.npmjs.com/package/trtc-electron-sdk).

2. In the project script, import and use the module:

```
const TRTCCloud = require('trtc-electron-sdk').default;// import TRTCCloud from 'trtc-electron-sdk';this.rtcCloud = new TRTCCloud();// Get the SDK version numberthis.rtcCloud.getSDKVersion();
```

Since v7.9.348, the TRTC Electron SDK has integrated `trtc.d.ts` for developers using TypeScript.

```
import TRTCCloud from 'trtc-electron-sdk';const rtcCloud: TRTCCloud = new TRTCCloud();// Get the SDK version numberrtcCloud.getSDKVersion();
```

### Step 4. Create an executable program

```
$ npm install electron-builder@latest --save-dev
```

In order to package the TRTC Electron SDK (`trtc_electron_sdk.node`) correctly, you must also run the following command to install `native-ext-loader`.

```
$ npm install native-ext-loader@latest --save-dev
```

### Step 5. Modify build configuration (`webpack.config.js`)

- Normally, `webpack.config.js` is in the root directory of the project.
- If you create your project with `create-react-app`, the configuration file will be `node_modules/react-scripts/config/webpack.config.js`.
- If you create your project with `vue-cli`, webpack configuration will be stored in the `configureWebpack` property of `vue.config.js`.
- If your project is customized, please locate webpack configuration according to your project.
1. First, add the following code before `module.exports` to make `webpack.config.js` accept the `--target_platform` command line parameter so that your project can be built correctly for its target platform.

```
const os = require('os');const targetPlatform = (function(){     let target = os.platform();     for (let i=0; i<process.argv.length; i++) {         if (process.argv[i].includes('--target_platform=')) {             target = process.argv[i].replace('--target_platform=', '');             break;         }     }     if (!['win32', 'darwin'].includes) target = os.platform();     return target;})();
```

> **Note:**In the result returned by `os.platform()`, `darwin` means macOS, and `win32` means Windows (64-bit or 32-bit).

2. Add the following configuration to the `rules` option. The `targetPlatform` variable ensures that `rewritePath` changes automatically according to the target platform.

```
rules: [  {          test: /\\.node$/,          loader: 'native-ext-loader',          options: {              rewritePath: targetPlatform === 'win32' ? './resources' : '../Resources'             // Build for different platforms             // rewritePath: './node_modules/trtc-electron-sdk/build/Release'         }      },]
```

The above code achieves the following:

- If you create an EXE file for Windows, `native-ext-loader` will load the TRTC SDK in `[application root directory]/resources`.
- If you create a DMG file for macOS, `native-ext-loader` will load the TRTC SDK in `[application directory]/Contents/Frameworsk/../Resources`.
- For local building, `native-ext-loader` will load the TRTC SDK in `./node_modules/trtc-electron-sdk/build/Release`. For details, see [TRTCSimpleDemo configuration](https://github.com/LiteAVSDK/TRTC_Electron/blob/main/TRTCSimpleDemo/vue.config.js).

You also need to add the `--target_platform` parameter to the build script of `package.json`, which brings us to the next step.

### Step 6. Modify `package.json`

1. Modify `main`.

```
// In most cases, the name of the `main` file can be customized. For example, in TRTCSimpleDemo, `main` can be configured as follows:"main": "main.electron.js",// However, for projects created with the `create-react-app` scaffolding tool, `main` must be configured as follows:"main": "public/electron.js",
```

2. Copy the following `build` configuration to your `package.json` file for `electron-builder` to read.

```
"build": {  "appId": "[Custom appId]",  "directories": { "output": "./bin"  },  "win": { "extraFiles": [   {     "from": "node_modules/trtc-electron-sdk/build/Release/",     "to": "./resources",     "filter": ["**/*"]   } ]  },  "mac": { "extraFiles": [   {      "from": "node_modules/trtc-electron-sdk/build/Release/trtc_electron_sdk.node",      "to": "./Resources"    } ]  }},
```

3. Add command scripts for building and packaging under `scripts`.
The following command scripts are for projects created with `create-react-app` and `vue-cli`. They provide samples for projects created with other tools too.

```
// Use this configuration for projects created with `create-react-app`."scripts": {  "build:mac": "react-scripts build --target_platform=darwin",  "build:win": "react-scripts build --target_platform=win32",  "compile:mac": "node_modules/.bin/electron-builder --mac",  "compile:win64": "node_modules/.bin/electron-builder --win --x64",  "pack:mac": "npm run build:mac && npm run compile:mac",  "pack:win64": "npm run build:win && npm run compile:win64"}// Use this configuration for projects created with `vue-cli`."scripts": {  "build:mac": "vue-cli-service build --target_platform=darwin",  "build:win": "vue-cli-service build --target_platform=win32",  "compile:mac": "node_modules/.bin/electron-builder --mac",  "compile:win64": "node_modules/.bin/electron-builder --win --x64",  "pack:mac": "npm run build:mac && npm run compile:mac",  "pack:win64": "npm run build:win && npm run compile:win64"}
```

| Parameter | Description |
| --- | --- |
| main | The entry point file of Electron, which can be customized in most cases. However, if your project is created with create-react-app, the entry point file must be public/electron.js. |
| build.win.extraFiles | When building for Windows, electron-builder will copy all files in the directory specified by from to bin/win-unpacked/resources (all in lowercase). |
| build.mac.extraFiles | When packaging for macOS, electron-builder will copy the trtc_electron_sdk.node file specified by from to bin/mac/your-app-name.app/Contents/Resources (capitalize the first letter of each word) |
| build.directories.output | The output path. In the sample above, the output file is saved to bin. You can modify it as needed. |
| build.scripts.build:mac | The script for building for macOS. |
| build.scripts.build:win | The script for building for Windows. |
| build.scripts.compile:mac | Creates a DMG file for macOS |
| build.scripts.compile:win64 | Creates an EXE file for Windows |
| build.scripts.pack:mac | Calls build:mac to build the project and then `compile:mac` to generate a DMG file |
| build.scripts.pack:win64 | Calls build:win to build the project and then `compile:win64` to generate an EXE file |

### Step 7. Run the build command

```
$ cd [Project directory]$ npm run pack:mac
```

The build tool will generate an installation file named `bin/your-app-name-0.1.0.dmg`. Publish this file.

- Build the project into an EXE file for Windows:

```
$ cd [Project directory]$ npm run pack:win64
```

The build tool will generate an installation file named `bin/your-app-name Setup 0.1.0.exe`. Publish this file.

> **Note:**Currently, the TRTC Electron SDK does not support cross-platform building. This means you cannot build your project into an EXE file on macOS or a DMG file on Windows. We are working on this and may add support for it in the future.

## FAQs

### What firewall restrictions does TRTC face?

The SDK uses the UDP protocol for audio/video transmission and therefore cannot be used in office networks that block UDP. If you encounter such a problem, see [Firewall Restrictions](https://intl.cloud.tencent.com/document/product/647/35164).

### What should I do if an error occurs when I install or build the TRTC Electron SDK?

## Learn More

- [SDK API Guide](https://web.sdk.qcloud.com/trtc/electron/doc/en-us/trtc_electron_sdk/TRTCCloud.html)
- [Release Notes (Electron)](https://intl.cloud.tencent.com/document/product/647/38702)
- [Simple Demo Source Code](https://github.com/LiteAVSDK/TRTC_Electron/tree/main/TRTCSimpleDemo)
- [API Example Source Code](https://github.com/LiteAVSDK/TRTC_Electron/tree/main/TRTC-API-Example)
- [FAQs](https://intl.cloud.tencent.com/document/product/647/43093)


---
*Source: [https://trtc.io/document/35097](https://trtc.io/document/35097)*
