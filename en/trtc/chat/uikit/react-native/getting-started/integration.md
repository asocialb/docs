# Integration

## Introduction to chat-uikit-react-native

chat-uikit-react-native is a React Native UI component library based on Tencent Cloud Chat SDK, providing common UI components such as session, chat, and group features. With these well-designed UI components, you can quickly build elegant, reliable, and scalable chat applications. The UI style developed based on React Native is more in line with the habits of overseas users and supports internationalization. You are welcome to integrate it.

The interface effect of chat-uikit-react-native is shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2e7900faa26a11ef820f525400d5f8ef.png)

## Environment Requirements

- React Native 0.75.0
- [Node.js](https://nodejs.org/en/) version 18+
- JDK 17
- Xcode version 14.0 or above
- Android Studio

## Configuring the development environment

If you are developing a React Native project for the first time, please refer to the steps on the React Native official website [set-up-your-environment](https://reactnative.dev/docs/set-up-your-environment) to configure your development environment.

If you encounter any environment issues during project creation or compilation, you can run `npx react-native doctor` for an environmental diagnosis.

## Integrate chat-uikit-react-native

### Step 1: Create a project (this step can be skipped if you already have a project)

1. Create a new React Native project.

```
npx @react-native-community/cli@latest init MyChatApp --version 0.75.0
```

2. After the project is created, go to the project directory.

```
cd MyChatApp
```

### Step 2. Integrate chat-uikit-react-native

- Download [chat-uikit-react-native](https://www.npmjs.com/package/@tencentcloud/chat-uikit-react-native) via npm/yarn and use it in the project. You can also use it for secondary development.

npm

yarn

```
npm install @tencentcloud/chat-uikit-react-native react-native-image-picker react-native-document-picker react-native-video
```

```
yarn add @tencentcloud/chat-uikit-react-native react-native-image-picker react-native-document-picker react-native-video
```

- Add device permissions

Android

iOS

Add the following permissions to the android/app/src/main/AndroidManifest.xml file.

```
 <uses-permission android:name="android.permission.READ_MEDIA_ChatAGES" /> <uses-permission android:name="android.permission.READ_MEDIA_AUDIO" /> <uses-permission android:name="android.permission.READ_MEDIA_VIDEO" /> <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" /> <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

Add the following permission usage description to the info.plist file.

```
  <key>NSCameraUsageDescription</key>    <string> we would like to use your camera</string>   <key>NSPhotoLibraryUsageDescription</key>    <string> we would like to use your photo library</string>  <key>NSMicrophoneUsageDescription</key>    <string>we would like to use your microphone</string>
```

### Step 3: Set up navigation

Please install the React Navigation dependencies. Refer to the documentation [React Navigation](https://reactnavigation.org/docs/getting-started).

npm

yarn

```
npm install @react-navigation/native@^6.1.18 react-native-screens@^3.34.0 react-native-safe-area-context @react-navigation/native-stack@^6.11.0
```

```
yarn add @react-navigation/native@^6.1.18 react-native-screens@^3.34.0 react-native-safe-area-context @react-navigation/native-stack@^6.11.0
```

### Step 4. Import chat-uikit-react-native

> **Note:**The following code does not contain SDKAppID, userID, and userSig, which should be replaced after obtaining the relevant information in Step 5.To respect the copyright of emoji designs, the Chat Demo/TUIKit project does not include cutouts of large emoji elements. Please replace them with your own designs or other emoji packs for which you hold the copyright before officially launching for commercial use. **The default smiley face emoji pack shown below is copyrighted by Tencent RTC**, you can upgrade to [Chat Pro Plus Edition and Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it for free.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2e708462a26a11efa04c5254002693fd.png)

App.tsx

Screens.tsx

> **Note:**The code below does not contain `SDKAppID`, `userID`, and `userSig`, which should be replaced after obtaining the relevant information in **Step 5**.

Replace the content in App.tsx, or you can create a new component to introduce.

```
import React from 'react';import {  View,  TouchableOpacity,  Text,  Image,  StyleSheet,} from 'react-native';import { NavigationContainer, useNavigation } from '@react-navigation/native';import { createNativeStackNavigator } from '@react-navigation/native-stack';import { UIKitProvider } from '@tencentcloud/chat-uikit-react-native';import resources from '@tencentcloud/chat-uikit-react-native/i18n';import { TUITranslateService } from '@tencentcloud/chat-uikit-engine';import { TUILogin } from '@tencentcloud/tui-core';import { ConversationListScreen, ChatScreen, ChatSettingScreen } from './Screens';const LoginScreen = () => {  const navigation = useNavigation<any>();  // Init localization  TUITranslateService.provideLanguages(resources);  TUITranslateService.useI18n('en-US');  // Login  const Login = () => {    TUILogin.login({      SDKAppID: 0, // Your SDKAppID      userID: 'test_1', // Login UserID      userSig: '', // Login userSig      useUploadPlugin: true,      framework: 'rn',    }).then(() => {      navigation.navigate('ConversationList');    });  }  return (    <View style={styles.container}>      <Image        style={styles.logo}        source={{uri:'https://web.sdk.qcloud.com/im/assets/images/tencent_rtc_logo.png'}}      />      <TouchableOpacity style={styles.buttonContainer} onPress={Login}>        <Text style={styles.buttonText}>Log in</Text>      </TouchableOpacity>    </View>  );};const Navigation = () => {  const Stack = createNativeStackNavigator();  return (    <NavigationContainer>      <Stack.Navigator        screenOptions={{ headerShown: false }}        initialRouteName="Login">        <Stack.Screen          name="Login"          component={LoginScreen} />        <Stack.Screen          name="ConversationList"          component={ConversationListScreen} />        <Stack.Screen          name="Chat"          component={ChatScreen} />        <Stack.Screen          name="ChatSetting"          component={ChatSettingScreen}/>      </Stack.Navigator>    </NavigationContainer>  );};const App = () => {  return (    <UIKitProvider>      <Navigation />    </UIKitProvider>  );};const styles = StyleSheet.create({  container: {    flex: 1,    justifyContent: 'center',    alignItems: 'center',    backgroundColor: '#FFFFFF',  },  logo: {    width: 232,    height: 80,  },  buttonContainer: {    width: '80%',    justifyContent: 'center',    alignItems: 'center',    paddingVertical: 11,    borderRadius: 5,    backgroundColor: '#2F80ED',  },  buttonText: {    fontSize: 18,    lineHeight: 24,    color: '#FFFFFF',  },});export default App;
```

Create a new Screens.tsx file in the same directory as the App.tsx file.

```
import React from 'react';import { useNavigation } from '@react-navigation/native';import { ConversationList, Chat, ChatSetting } from '@tencentcloud/chat-uikit-react-native';export const ConversationListScreen = () => {  const navigation = useNavigation<any>();  const onPressConversation = () => {    navigation.navigate('Chat');  };  return (    <ConversationList onPressConversation={onPressConversation} />  );};export const ChatScreen = () => {  const navigation = useNavigation<any>();  const navigateBack = () => {    navigation.goBack();  };  const navigateToChatSetting = () => {    navigation.navigate('ChatSetting');  };  return (    <Chat      navigateBack={navigateBack}      navigateToChatSetting={navigateToChatSetting}    />  );};export const ChatSettingScreen = () => {  const navigation = useNavigation<any>();  // Navigate to Chat when you click header back button.  const navigateBack = () => {    navigation.goBack();  };  // Navigate to Chat when you click the send message button.  const navigateToChat = () => {    navigation.goBack();  };  // Navigate to ConversationList when you disband group or leave group.  const navigateToConversationList = () => {    navigation.navigate('ConversationList');  };  return (    <ChatSetting      navigateBack={navigateBack}      navigateToChat={navigateToChat}      navigateToConversationList={navigateToConversationList}    />  );};
```

### Step 5: Obtain SDKAppID, userID, and userSig

Obtain the relevant parameters SDKAppID, userID, and the corresponding userSig from `Login`:

- `SDKAppID`, can be obtained through [Chat Console](https://console.trtc.io/app) in `Applications`:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2ec13858a26a11ef992f52540075b605.png)

- `userID`
  - Click to enter the [Application](https://console.trtc.io/app) you created above, you will see the `Chat` product entry in the left sidebar, click to enter.
  - After entering the Chat product sub-page, click `Users` to enter the User Management page.
  - Click `Create account` to pop up the account creation information filling box. If it is just a regular member, we recommend selecting the `General` type.
  - **For a better experience with messaging and other features, it is recommended that you create two user IDs (test_1, test_2)**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2e93b04da26a11efa04c52540055f650.png)

- `userSig` can be generated in real-time using the development tools provided by the console. For development tools, click [Chat Console > Development Tools > UserSig Tools > Signature (UserSig) Generator](https://console.trtc.io/usersig).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2e946583a26a11efaaca525400fdb830.png)

### Step 6: Compile and run the project

- To compile and run the project, you need to use a real device or an emulator. It is recommended to use a real device. You can refer to the React Native official website [running-on-device](https://reactnative.dev/docs/running-on-device) for connecting a real device for debugging.
- Replace SDKAppID, userID, userSig in App.tsx, then run the following command:

Android

iOS

1. Enable Developer Mode on the phone and turn on the **USB Debugging** switch.
2. Connect the phone with a USB cable, it is recommended to choose the **Transfering File** option, **do not choose the Charge Only option**.
3. After confirming the phone is successfully connected, execute `npm run android` to compile and run the project.

```
npm run start
```

1. Connect the phone with a USB cable and open the project ios directory with Xcode.
2. Configure the signing information according to the [running-on-device](https://reactnative.dev/docs/running-on-device?platform=ios) section on the React Native official website.
3. Go to the ios directory and install dependencies.

```
cd iospod install
```

4. Go back to the root directory and execute npm run ios to compile and run the project.

```
cd ../npm run start
```

## Step 7: Send your first message

1. After the project starts, click Initiate Session in the top left corner.
2. Enter the Initiate Session window. In the search bar, enter the user ID created in Step 5 (**test_2**), select it and open the session.
3. Enter the message in the input box and click send.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2e895f8aa26a11efa0b3525400bdab9d.png)

## Exchange and Feedback

Join [Telegram Technical Support Group](https://t.me/tencent_imsdk) or [WhatsApp Communication Group](https://chat.whatsapp.com/IVa11ZkVmKTEwSWsAzSyik) for professional engineer support to solve your problems.

## FAQs

#### What to do when there is a runtime environment error?

You can run the following command for environmental diagnosis.

```
npx react-native doctor
```

## Documentation

#### Related to UIKit:

- [chat-uikit-react-native npm](https://www.npmjs.com/package/@tencentcloud/chat-uikit-react-native)


---
*Source: [https://trtc.io/document/56573](https://trtc.io/document/56573)*
