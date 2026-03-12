# Run Demo

This document describes how to integrate the SDK for Unity.

## Environment Requirements

| Environment | Version |
| --- | --- |
| Unity | 2019.4.15f1 or later |
| Android | Android Studio 3.5 or later; devices with Android 4.1 or later for apps |
| iOS | Xcode 11.0 or later. Ensure that your project has a valid developer signature. |

## Supported Platforms

We are committed to building a set of Chat SDK and TUIKit for all Unity platforms, allowing you to run one set of code on all platforms.

| Platform | Chat SDK |
| --- | --- |
| iOS | Supported |
| Android | Supported |
| macOS | Supported |
| Windows | Supported |
| [Web](#web) | Supported from 1.8.1+ |

> **Note** For web, you need to perform a few extra steps for SDK integration. For details, see [Part 5](#web).

## Prerequisites

1. You have [signed up](https://intl.cloud.tencent.com/document/product/378/17985) for a Tencent Cloud account and completed [identity verification](https://intl.cloud.tencent.com/document/product/378/3629).
2. You have created an application as instructed in Creating and Upgrading an Application and recorded the SDKAppID.

## Part 1. Creating Test Accounts

In the [Chat console](https://console.tencentcloud.com/im), select your application and click **Auxiliary Tools** > **UserSig Generation & Verification** on the left sidebar. Create two `UserID` values and their `UserSig` values, and copy the `UserID`, `Key`, and `UserSig` for subsequent logins.

> **Forbiddenï¼**The test account is for development and testing only. Before the application is launched, the correct method for generating a UserSig is to integrate the UserSig calculation code into your server and provide an application-oriented API. When UserSig is needed, your application can send a request to the business server for a dynamic UserSig. For more information, see [Generating UserSig](https://intl.cloud.tencent.com/document/product/1047/34385).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/935c742f55fa11eeabd75254005810a4.png)

## Part 2. Integrating Chat SDK into Your Unity Project

1. Use Unity to create a project and record the project directory, or open an existing Unity project.
2. Open the project with an IDE (such as Visual Studio Code):

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/20a6ae2e788111ee8fb05254000e2caf.png)

3. Find Packages/manifest.json based on the directory, and modify dependencies as follows:

```
{  "dependencies":{    "com.tencent.imsdk.unity":"https://github.com/TencentCloud/chat-sdk-unity.git#unity"  }}
```

To help you better understand Chat SDK APIs, we provide [API examples](https://github.com/TencentCloud/tc-chat-sdk-unity/tree/main/Assets/IM_Api_Example)to demonstrate how to call APIs and trigger listeners.

## Part 3. Loading Dependencies

Open the project in the Unity Editor, wait until dependencies are loaded, and confirm the Tencent Cloud Chat is successfully loaded.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9377d9ec55fa11ee974d5254005f490f.jpeg)

## Part 4. Implementing Your Own UI

### Prerequisites

You have created a Unity project or have a project that can be based on Unity, and have loaded Tencent Cloud Chat SDK.

### Initializing the SDK

> **Note:**To respect the copyright of emoji designs, the Chat Demo/TUIKit project does not include cutouts of large emoji elements. Please replace them with your own designs or other emoji packs for which you hold the copyright before officially launching for commercial use. **The default smiley face emoji pack shown below is copyrighted by Tencent RTC**, you can upgrade to [Chat Pro Plus Edition and Enterprise Edition](https://console.trtc.io/subscription/buy/chat?packType=pro) to use it for free.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bef6c1fc97f411ef992f52540075b605.png)

[Detailed documentation](https://intl.cloud.tencent.com/document/product/1047/48570)

Call `TencentIMSDK.Init` to initialize the SDK.

Pass in your `SDKAppID`.

```
using Com.Tencent.IM.Unity.UIKit;using com.tencent.imsdk.unity;using com.tencent.imsdk.unity.types;using com.tencent.imsdk.unity.enums;namespace Com.Tencent.IM.Unity.UIKit{    public static void Init() {      string SDKAppID = ""; // Get the `SDKAppID` from the Chat console      SdkConfig sdkConfig = new SdkConfig();          sdkConfig.sdk_config_config_file_path = Application.persistentDataPath + "/TIM-Config";          sdkConfig.sdk_config_log_file_path = Application.persistentDataPath + "/TIM-Log";          TIMResult res = TencentIMSDK.Init(long.Parse(SDKAppID), sdkConfig);    }}
```

After `Init`, you can mount some listeners to the Chat SDK, mainly including those for network status and user information change. For more information, see [here](https://intl.cloud.tencent.com/document/product/1047/48570).

### Logging in with a test account

[Detailed documentation](https://intl.cloud.tencent.com/document/product/1047/48571)

Log in with one of the test accounts you created earlier.

Call the `TencentIMSDK.Login` method to log in with the test account.

If the returned `res.code` is `0`, the login is successful.

```
public static void Login() {  if (userid == "" || user_sig == "")  {      return;  }  TIMResult res = TencentIMSDK.Login(userid, user_sig, (int code, string desc, string json_param, string user_data)=>{    // Process the login callback logic  });}
```

> **Forbiddenï¼**The test account is for development and testing only. Before the application is launched, the correct method for generating a UserSig is to integrate the UserSig calculation code into your server and provide an application-oriented API. When UserSig is needed, your application can send a request to the business server for a dynamic UserSig. For more information, see [Generating UserSig](https://intl.cloud.tencent.com/document/product/1047/34385).

### Sending a message

[Detailed documentation](https://intl.cloud.tencent.com/document/product/1047/48572)

The following shows how to send a text message:

Sample code:

```
public static void MsgSendMessage() {        string conv_id = ""; // The conversation ID of a one-to-one message is the `userID`, and that of a group message is the `groupID`.        Message message = new Message        {          message_conv_id = conv_id,          message_conv_type = TIMConvType.kTIMConv_C2C, // For a group message, this value is `TIMConvType.kTIMConv_Group`          message_elem_array = new List<Elem>          {            new Elem            {              elem_type = TIMElemType.kTIMElem_Text,              text_elem_content =  "This is an ordinary text message"            }          }        };        StringBuilder messageId = new StringBuilder(128); // messageId for getting message ID when message is sent        TIMResult res = TencentIMSDK.MsgSendMessage(conv_id, TIMConvType.kTIMConv_C2C, message, messageId, (int code, string desc,                         string json_param, string user_data)=>{          // Async message sending result        });          // The message ID returned when the message is sent}
```

> **Note**If sending fails, it may be that your `sdkAppID` doesn't support sending messages to strangers. In this case, you can disable the relationship check feature in the console.Disable the friend relationship chain check [here](https://console.tencentcloud.com/im/login-message).

### Obtaining the conversation list

[Detailed documentation](https://intl.cloud.tencent.com/document/product/1047/50020)

Log in with the second test account to pull the conversation list.

The conversation list can be obtained in two ways:

1. Listen for the persistent connection callback to get message changes and update and render the historical message list in real time.
2. Call an API to get the message history at certain time points.

Common use cases include:

Getting the conversation list when the application starts and listening for the persistent connection callback to update the conversation list in real time.

#### Requesting the conversation list at certain time points

```
TIMResult res = TencentIMSDK.ConvGetConvList((int code, string desc, List<ConvInfo> info_list, string user_data)=>{ // Process the async logic});
```

At this point, you can see the message sent by the first test account in the previous step.

#### Listening for the persistent connection to get the conversation list in real time

Mount the conversation list listener, process the callback event, and update the UI.

- Mount the listener.

```
TencentIMSDK.SetConvEventCallback((TIMConvEvent conv_event, List<ConvInfo> conv_list, string user_data)=>{ // Process the callback logic});
```

- Process the callback event and display the latest conversation list on the UI.

### Receiving messages

[Detailed documentation](https://intl.cloud.tencent.com/document/product/1047/48573)

Messages can be received with the Chat SDK in two ways:

- Listen for the persistent connection callback to get message changes and update and render the historical message list in real time.
- Call an API to get the message history at certain time points.

Common use cases include:

- After a new conversation is opened on the UI, request and display a certain number of historical messages.
- Listen for the persistent connection to receive messages in real time and add them to the historical message list.

#### Requesting the historical message list at a time

To avoid affecting the pull speed, we recommend you limit the number of messages pulled to 20 per page.

You need to dynamically record the current number of pages for the next request.

Sample code:

```
// Pull historical one-to-one messages// Do not set `msg_getmsglist_param_last_msg` for the first pull. It will pull the newest message if not set.// `msg_getmsglist_param_last_msg` can be the last message in the returned message list for the second pull.Message LastMessage = null;string LastMessageID = "";var get_message_list_param = new MsgGetMsgListParam();TIMResult res = TencentIMSDK.MsgGetMsgList(conv_id, TIMConvType.kTIMConv_C2C, get_message_list_param, (params object[] parameters) => {  // handle callback logic  List<Message> messages = Utils.FromJson<List<Message>>((string)parameters[1]);       if (messages.Count > 0){          LastMessage = messages[messages.Count - 1];          LastMessageID.text = messages[messages.Count - 1].message_msg_id;   }else {         LastMessage = null;          LastMessageID.text = "";       }  });// `msg_getmsglist_param_last_msg` can be the last message in the returned message list for the second pull.var get_message_list_param = new MsgGetMsgListParam    {      msg_getmsglist_param_last_msg = LastMessage    };TIMResult res = TencentIMSDK.MsgGetMsgList(conv_id, TIMConvType.kTIMConv_Group, get_message_list_param, (int code, string desc, string user_data) => {  // handle callback logic});
```

#### Listening for the persistent connection callback to get new messages in real time

After the historical message list is initialized, new messages are from the persistent connection `TencentIMSDK.AddRecvNewMsgCallback`.

After the `AddRecvNewMsgCallback` callback is triggered, you can add new messages to the historical message list as needed.

Sample code for binding a listener:

```
TencentIMSDK.AddRecvNewMsgCallback((List<Message> message, string user_data) => {  // Process new messages});
```

At this point, you have completed the Chat module development, and now users can send and receive messages and enter different conversations.

You can develop more features, such as [group](https://intl.cloud.tencent.com/document/product/1047/48169), [user profile](https://intl.cloud.tencent.com/document/product/1047/48859), [relationship chain](https://intl.cloud.tencent.com/document/product/1047/49563), and [local search](https://intl.cloud.tencent.com/document/product/1047/50066).

For more information, see [Integration Solution (No UI)](https://www.tencentcloud.com/document/product/1047/46263).

## Part 5. Enabling Unity Support for WebGL

Tencent Cloud Chat SDK for Unity 1.8.1 or later supports building WebGL.

To enable support for web, you need to perform the following extra steps in addition to those for enabling support for Android and iOS:

### Importing JS

1. Execute the following commands in the folder containing the build output of the WebGL project.

```
// Initialize npmnpm init -y// Download the @tencentcloud/chat SDK via npm.npm install @tencentcloud/chat --save// Download the ââtim-upload-pluginââ plugin via npm.npm install tim-upload-plugin --save
```

2. Open `index.html` and import the JS files as follows:

```
<script src="./node_modules/@tencentcloud/chat/index.js"></script><script src="./node_modules/@tencentcloud/chat/modules/group-module.js"></script><script src="./node_modules/@tencentcloud/chat/modules/relationship-module.js"></script><script src="./node_modules/@tencentcloud/chat/modules/signaling-module.js"></script><script src="./node_modules/tim-upload-plugin/index.js"></script>
```

## FAQs

#### What platforms are supported?

iOS, Android, Windows, macOS, and WebGL are supported.

#### What should I do if clicking **Build And Run** for an Android device triggers an error, stating no available device is found?

Check that the device is not occupied by other resources. Alternatively, click **Build** to generate an APK package, drag it to the simulator, and run it.

#### What should I do if an error occurs during the first run for an iOS device?

If an error is reported for an iOS device after the demo configured as above is run, choose **Product** > **Clean** to clean the product, and build the demo again. You can also close Xcode and open it again, and then build the demo again.

#### What should I do if Unity v2019.04 reports the following error for iOS?

Library/PackageCache/com.unity.collab-proxy@1.3.9/Editor/UserInterface/Bootstrap.cs(23,20): error CS0117: 'Collab' does not contain a definition for 'ShowChangesWindow'
Choose **Window** > **Package Manager** on the toolbar of the Editor and downgrade Unity Collaborate to 1.2.16.

#### What should I do if Unity v2019.04 reports the following error for iOS?

Library/PackageCache/com.unity.textmeshpro@3.0.1/Scripts/Editor/TMP_PackageUtilities.cs(453,84): error CS0103: The name 'VersionControlSettings' does not exist in the current context
Open the source code and delete the code snippet of `|| VersionControlSettings.mode != "Visible Meta Files"`.

#### Is this a C# interface? How to use it without Unity?

Unity SDK is an SDK using C#, but because Unity SDK contains Unity features, it cannot be used directly in a C# environment.

If you need to use it in a C# environment, we provide a separate [C# SDK](https://www.nuget.org/packages/TencentCloudChat/1.0.1) nuget package. The usage method is the same as Unity SDK, you can refer to Unity SDK documentation for use.

Among them, the C# SDK only supports the PC side, and the unity SDK supports the mobile side.

#### Is there a UI that can be used directly?

The corresponding UIKit of Unity SDK and C# SDK is currently not provided.

#### How do I query error codes?

For Chat SDK API error codes, see [Error Codes](https://intl.cloud.tencent.com/document/product/1047/34348).


---
*Source: [https://trtc.io/document/41656](https://trtc.io/document/41656)*
