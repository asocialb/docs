# In-Conference Chat

In video conferences, participants can send messages in real-time in the chat area, share opinions and ideas, and create a relaxed and pleasant communication environment by exchanging emoticons and animations. To maintain the order of the meeting, the host or administrator can set to prohibit participants from sending messages in the chat, ensuring the focus and efficiency of the conference content. By flexibly using these features, video conferences can provide efficient and convenient communication experiences for various scenarios.

## Feature Introduction

### Text, Multimedia Information Interaction

Click the **Chat** option at the bottom of the conference interface to access the chat interface. Participants can freely send **text**,**pictures**, **videos**, and **voice**messages, enabling real-time communication without disrupting the conference flow.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/14e47d8839e811ef9397525400fdb830.png)

### Emoji Interaction

Click the **Emoji Icon** in the message board editor in the chat interface to bring up the emoji list. Click the corresponding emoji to display it in the message board for sending.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/15340a0139e811ef9397525400fdb830.png)

### Chat permissions in the control panel

The host/administrator can set a memberâs chat permissions in Member Management. If muted, regular members will not be able to send messages.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1511345239e811ef9c9c525400d5f8ef.png)

## feature Integration

### Integrate chat component

Add the [tencent_cloud_chat_message](https://pub.dev/packages/tencent_cloud_chat_message) plugin dependency to your project's `pubspec.yaml` file.

```
dependencies:       tencent_cloud_chat_message: latest version
```

### International Language Configuration

This step is required. First, import the localization tools into the entry file of the application.

```
import 'package:tencent_cloud_chat_intl/localizations/tencent_cloud_chat_localizations.dart';
```

Next, add the localization configuration to entries provided by third-party packages such as `MaterialApp` or `GetMaterialApp`. Here, `GetMaterialApp` is used as an example:

```
GetMaterialApp(  localizationsDelegates: const [    /// Your original configuration    GlobalMaterialLocalizations.delegate,        /// Add this line    ...TencentCloudChatLocalizations.localizationsDelegates,   ],  supportedLocales: [    /// Your original configuration    ...S.delegate.supportedLocales,    /// Add this line    ...TencentCloudChatLocalizations.supportedLocales,  ],  /// Other settings)
```

### **Initialization and Login**

Add the following code to your project. Its function is to complete the initialization and log in to by calling the relevant interfaces in the chat component. This step is crucial, as the chat can only be used normally after initialization. Therefore, please be patient and check whether the relevant parameters are configured correctly. Among the parameters, **sdkAppId**, **userID**, and **userSig**, you have already used them when [logging in to TUIRoomKit](https://www.tencentcloud.com/document/product/647/57508#db8f1a75-1b7d-4621-b981-3d52bcad4e95).

```
import 'package:tencent_cloud_chat/components/component_config/tencent_cloud_chat_message_common_defines.dart';import 'package:tencent_cloud_chat/components/component_config/tencent_cloud_chat_message_config.dart';import 'package:tencent_cloud_chat/models/tencent_cloud_chat_models.dart';import 'package:tencent_cloud_chat/tencent_cloud_chat.dart';import 'package:tencent_cloud_chat_message/tencent_cloud_chat_message.dart';await TencentCloudChat.controller.initUIKit(    options: TencentCloudChatInitOptions(      sdkAppID: 'SDKAPPID',  // Your SDKAPPID      userID: 'userID',      // Your userID      userSig: 'userSig',    // Your userSig    ),    components: TencentCloudChatInitComponentsRelated(      usedComponentsRegister: [TencentCloudChatMessageManager.register],  // Register chat components      componentConfigs: TencentCloudChatComponentConfigs(        messageConfig: TencentCloudChatMessageConfig(          // The following configuration is recommended.          showMessageSenderName: ({groupID, topicID, userID}) => true,          showSelfAvatar: ({groupID, topicID, userID}) => true,          defaultMessageMenuConfig: ({groupID, topicID, userID}) =>              TencentCloudChatMessageDefaultMessageMenuConfig(            enableMessageForward: false,            enableMessageSelect: false,          ),        ),      ),    ),    plugins: [],);
```

### Using Emojis (Optional)

If you need to send and receive emojis, you need to configure as follows:

#### Add Dependencies

In your project's `pubspec.yaml` file, add the [tencent_cloud_chat_sticker](https://pub.dev/packages/tencent_cloud_chat_sticker) plugin dependency.

#### Complete configuration

In the `plugins` of [Initialization and Login](https://www.tencentcloud.com/document/product/647/61632#3d0fd007-2189-48e0-8391-27d840e075f4) in the previous step, add the following code:

```
plugins: [  TencentCloudChatPluginItem(    name: "sticker",    initData: TencentCloudChatStickerInitData(      useDefaultSticker: true,            // Default stickers, only this sticker pack can interoperate with TUIRoomKit from other platforms.      useDefaultCustomFace_4350: false,   // If you do not need to use TUIRoomKit from other platforms, you can enable the following emoji pack.      useDefaultCustomFace_4351: false,      useDefaultCustomFace_4352: false,      userID: 'userId',                   // Your userId    ).toJson(),    pluginInstance: TencentCloudChatStickerPlugin(      context: context,    ),  ),],
```

> **Note:**To respect the copyright of emoji designs, the TUIRoomKit example project does not include large emoji cut elements. Before official commercial use, please replace them with your own designs or other emoji packs you have copyright to. The default **Little Yellow Face emoji pack is copyrighted by Tencent Cloud**, and can be licensed for a fee. If you wish to obtain a license, you can [Submit a ticket](https://console.tencentcloud.com/workorder/category) to contact us.

### Using Chat

When you [create or join a conference successfully](https://www.tencentcloud.com/document/product/647/57508#1.E5.AF.B91.E8.A7.86.E9.A2.91.E9.80.9A.E8.AF.9D), you need to pass the `chatWidget` into the conference page, `ConferenceMainPage`. After passing it in, the chat button will **display** in the bottom toolbar. Clicking the chat button will automatically navigate to `chatWidget`.

```
Navigator.push(  context,  MaterialPageRoute(    builder: (context) => ConferenceMainPage( // Conference main page      chatWidget: TencentCloudChatMessage(          options: TencentCloudChatMessageOptions(groupID: 'yourConferenceId'),  // Your Confere      ),    ),  ),);
```

After completing the above configuration, you can click the chat button to chat during the conference.


---
*Source: [https://trtc.io/document/61632](https://trtc.io/document/61632)*
