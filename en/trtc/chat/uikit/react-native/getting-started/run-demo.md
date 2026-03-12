# Run Demo

chat-uikit-react-native is a React Native UI component library based on Tencent Cloud Chat SDK. It provides universal UI components, including conversation, chat, and group features. With these well-designed UI components, you can quickly build elegant, reliable, and scalable chat applications. The UIKit interface developed with React Native is more in line with the usage habits of overseas customers and supports internationalization. If your business needs to expand overseas, you are welcome to integrate it. For details, refer to the [open source code](https://github.com/TencentCloud/chat-demo-react-native).

The interface effect of chat-uikit-react-native is shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/036274b3b8fa11efa1ff525400bdab9d.png)

## Prerequisites

### Enabling a Service

1. Log in to the [Chat console](https://console.trtc.io/), go to the **application management** page, and click **Create New Application**. If you have an existing application, you can omit the application creation process.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6d6cbd15c07911f0a6dd5254005ef0f7.png)

2. On the **application management** page, obtain the SDKAppID and key information from the SDKAppID column.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6d51e946c07911f0b4a7525400454e06.png)

> **Note:**View key info requires identity verification.Key information is sensitive information. To prevent misappropriation, keep it safe and guard against leakage.

3. [Go to the user management page](https://console.trtc.io/chat/account-management), create 2â3 test accounts for experience in C2C chat and group chat capacities.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6ccd717cc07911f08c0e52540044a08e.png)

4. userSig info. Click [Chat console > Development tool > userSig tool](https://console.trtc.io/usersig), fill in the created userID to generate userSig.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6cf1125dc07911f0a6dd5254005ef0f7.png)

### Development Environment Requirement

- React Native 0.75.0
- [Node.js](https://nodejs.org/en/) version 18+
- Xcode version 14.0 or above
- Android Studio

### Configuring the development environment

If you are developing a React Native project for the first time, please refer to the steps on the React Native official website [set-up-your-environment](https://reactnative.dev/docs/set-up-your-environment) to configure your development environment.

If you encounter any environment issues during project creation or compilation, you can run `npx react-native doctor` for an environmental diagnosis.

## Download Demo

```
git clone https://github.com/TencentCloud/chat-demo-react-native
```

```
cd chat-demo-react-native/Demo
```

Install Using `npm`

```
npm i --legacy-peer-deps
```

## Configure Demo

> **Note:**To respect the copyright of emoji designs, the Chat Demo/TUIKit project does not include cutouts of large emoji elements. Please replace them with your own designs or other emoji packs for which you hold the copyright before officially launching for commercial use. **The default smiley face emoji pack shown below is copyrighted by Tencent RTC**, you can upgrade to [Chat Pro Plus Edition and Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it for free.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d1eda06a9aa611f0bf2352540044a08e.png)

1. Open the Demo project, the GenerateTestUserSig.js file under the ./debug directory.
2. Set `SDKAPPID` and `SECRETKEY` in the `GenerateTestUserSig.js` file, which can be obtained from the [Chat Console](https://console.trtc.io/). Click the target application card to enter its configuration page.

```
const SDKAppID = 0; // numberconst SECRETKEY = 'xxx'; // stringconst APPKey = 'xxx'; // string, and For Offline Push only, optional to fill in.
```

## Run Demo

- To compile and run the project, you need to use a real device or an emulator. It is recommended to use a real device. You can refer to the React Native official website [running-on-device](https://reactnative.dev/docs/running-on-device) for connecting a real device for debugging.

Android

iOS

1. Enable Developer Mode on the phone and turn on the **USB Debugging** switch.
2. Connect the phone with a USB cable, it is recommended to choose the **Transferring File** option, **do not choose the Charge Only option**.
3. After confirming the phone is successfully connected, execute `npm run android` to compile and run the project.

```
npm run android
```

1. Connect the phone with a USB cable and open the project ios directory with Xcode.
2. Configure the signing information according to the [running-on-device](https://reactnative.dev/docs/running-on-device?platform=ios) section on the React Native official website.
3. Go to the ios directory and install dependencies.

```
cd iospod install
```

4. Go back to the root directory and execute npm run ios to compile and run the project.

```
cd ../npm run ios
```

## Sending Your First Message

1. After the project starts, click Initiate Session in the top left corner.
2. Enter the conversation initiation window. In the search bar, enter the userID created in Step 2 (**test_2**), select it, and open the conversation.
3. Enter the message in the input box and click send.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/03c6e4f6b8fa11ef86025254002693fd.png)

## FAQ

1. If you encounter an error as shown in the figure when running npm run android, please reset the environment variables in the project root directory.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0368a004b8fa11ef89f2525400d5f8ef.png)

```
export ANDROID_HOME=$HOME/Library/Android/sdkexport PATH=$PATH:$ANDROID_HOME/emulatorexport PATH=$PATH:$ANDROID_HOME/platform-tools
```

2. If you encounter node environment variable issues when executing the Build command in Xcode, please follow these steps:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/03ebc4ccb8fa11ef86025254002693fd.png)

```
cd iosecho export NODE_BINARY=$(command -v node) > .xcode.env
```

## Reference Documentation

- [chat-uikit-react-native npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-react-native)
- [Quick Integration Documentation for UIKit](https://www.tencentcloud.com/document/product/1047/56573)
- [chat-uikit-engine API Manual](https://web.sdk.qcloud.com/im/doc/chat-engine/index.html)
- [chat-uikit-engine npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-engine)


---
*Source: [https://trtc.io/document/52397](https://trtc.io/document/52397)*
