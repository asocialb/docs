# Step 1: Install Chat SDK

This document describes how to quickly integrate the Tencent Cloud Chat SDK into your web, mini program, uni-app and React Native projects.

## File Structure of the Chat SDK

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/460419721a5311ee909c525400cea498.png)

## Integrating the SDK

- You can integrate the Chat SDK into your web, mini program, and uni-app projects by using npm.
- You can integrate the upload plugin [tim-upload-plugin](https://www.npmjs.com/package/tim-upload-plugin) for faster and safer upload of rich media resources.

### Integration via npm (Recommended)

Use npm to install the corresponding Chat SDK dependencies in your project.

```
npm install @tencentcloud/chat --save// The Tencent Cloud Chat upload plugin is required to send messages such as images and files.npm install tim-upload-plugin --save
```

```
import TencentCloudChat from '@tencentcloud/chat';import TIMUploadPlugin from 'tim-upload-plugin';let options = {  SDKAppID: 0 // Replace 0 with the SDKAppID of your Chat application when connecting.};// Create an SDK instance.// The `TencentCloudChat.create()` method returns the same instance for the same `SDKAppID`.// The SDK instance is usually represented by chat.let chat = TencentCloudChat.create(options);// Set the SDK log level.// 0: Common level. You are advised to use this level during access as it covers more logs.// 1: Release level. You are advised to use this level for key information in a production environment.chat.setLogLevel(0);// chat.setLogLevel(1);// Register the Tencent Cloud Chat upload plugin.chat.registerPlugin({'tim-upload-plugin': TIMUploadPlugin});
```

### **Set Log Level**

Set the log level. Logs below the specified level will not be output.

##### **API**

```
chat.setLogLevel(level);
```

| Name | Type | Description |
| --- | --- | --- |
| level | Number | Log levels: 0 - Normal level, with a larger amount of logs. It is recommended for use during integration. 1 - Release level, the SDK outputs key information. It is recommended for use in production environments. 2 - Warning level, the SDK only outputs warning and error level logs. 3 - Error level, the SDK only outputs error level logs. 4 - No log level, the SDK will not print any logs. |

##### **Examples**

```
chat.setLogLevel(0);
```

### **Register Plugins**

> **Noteï¼**To send messages such as images, voice, video, and files, you need to use the upload plugin `tim-upload-plugin` to upload files to Tencent Cloud Object Storage.When using` tim-upload-plugin` in a React Native project, you need to upgrade `tim-upload-plugin` to version v1.3.1 or above. Also, to improve the user experience in poor network conditions or during network switching, you need to register the network status listening plugin `@react-native-community/netinfo`.To send rich media messages in a React Native packaged App, you need to add permissions:Add the following permissions to the `AndroidManifest.xml` in the Android project: <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" /> <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" /> <uses-permission android:name="android.permission.RECORD_AUDIO" />Add the following permissions to the `Info.plist` in the iOS project:<key>NSCameraUsageDescription</key><string>We need access to your camera to take photos</string><key>NSPhotoLibraryUsageDescription</key><string>We need access to your photo library to select photos</string><key>NSMicrophoneUsageDescription</key><string>We need access to your microphone to record audio</string>

##### **API**

```
chat.registerPlugin(options);
```

The `options` parameter is of the `Object` type. It contains the following attribute values:

| Name | Type | Description |
| --- | --- | --- |
| key | String | Plugin name. |
| value | Class | Plugin class. |

##### **Examples**

```
chat.registerPlugin({'tim-upload-plugin': TIMUploadPlugin});
```

```
// Register the network status listening plugin in a React Native project.npm install @react-native-community/netinfo --save import NetInfo from "@react-native-community/netinfo";chat.registerPlugin({'chat-network-monitor': NetInfo});
```

**Next stepï¼**[**initialize Chat SDK**](https://trtc.io/document/47967?platform=web&product=chat&menulabel=sdk)**.**

### Relevant Resources

- [SDK Update Logs](https://intl.cloud.tencent.com/document/product/1047/34281)
- [SDK APIs](https://www.tencentcloud.com/document/product/1047/33999)

## FAQs

**Are there any open-source UI components that can be reused or redeveloped?**
Tencent Cloud Chat provides open-source UIKits for all platforms that can be reused or redeveloped by developers. Find the reference documentation below:

- [Quick Startï¼Reactï¼](https://trtc.io/document/50055?platform=web&product=chat)
- [Quick Startï¼Vueï¼](https://trtc.io/document/58644?platform=web&product=chat)


---
*Source: [https://trtc.io/document/34309](https://trtc.io/document/34309)*
