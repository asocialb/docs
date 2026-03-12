# iOS

This document will guide you on how to integrate the `AIConversationKit` component in a short time. Following this guide, you will complete the following key steps within 20 minutes and implement a conversational AI project with a complete UI.

| **Conversational AI Interface**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ecf08a9312e511f0a9cd5254007c27c5.png) |
| --- |
|  |

## Environment Preparation

- Minimum compatibility with iOS 13. Recommend using iOS 13 and above versions.
- Xcode 13 and above versions.

## Step One: Activating Service

Before initiating a conversation using AiConversationKit, you need to go to the console to activate conversational AI service for AiConversationKit. For specific steps, please refer to [Activate Service](https://www.tencentcloud.com/document/product/647/69002#).

## Step Two: Download the AIConversationKit Component

Go to [Github](https://github.com/Tencent-RTC/AIConversationKit) to download the zip file. After decompressing it, you will see the **AIConversationKit** directory, the **AIConversationKit.podspec** file, and the **Resource** directory.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ecfada7b12e511f09fca52540099c741.png)

## Step Three: Configuration

1. Copy the **AIConversationKit**, **podspec** and **Resource** in the directory decompressed in the above [step two](https://www.tencentcloud.com/document/product/647/69005#step2) to your project:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed1d3d0e12e511f08c275254001c06ec.png)

2. Then, in the `Podfile` of your project, add the following dependencies:

```
   pod 'AIConversationKit',:path => 'AIConversationKit.podspec':
```

3. Once the configuration completed, execute `pod install` to complete the installation of dependencies;
4. Use XCode to open `.xcworkspace` and configure the certificate information:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ecee1d1412e511f0aaa3525400e889b2.png)

## Step Four: Sign In

Add the following code to your project. It enables the component to log in by calling relevant APIs in `TUILogin`. **This step is critical** because only after logging in can `AIConversationkit` features be used properly. Please patiently check if the relevant parameters are configured correctly.

swift

```
import TUICoreimport AIConversationKitfunc application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {        let sdkAppId = 1600000001  // Please replace with your sdkAppId        let userId = "people"      // Please replace with your UserID        let secretKey = "xxx"      // Please replace with your sdkSecretKey        let userSig = GenerateTestUserSig.genTestUserSig(sdkAppId: sdkAppId, identifier: userId, secrectkey: secretKey)        TUILogin.login(Int32(sdkAppId), userID: userId, userSig:userSig){            print("login success")        } fail: { code, message in            print("login failed, code: \\(code), error: \\(message ?? "nil")")        }    return true}
```

| Parameter | Type | Description |
| --- | --- | --- |
| userID | String | Customers customize their Custom User IDs according to their own business, only allowing a combination of uppercase and lowercase letters (a-z A-Z), numbers (0-9), underline, and hyphen. |
| sdkAppID | Int32 | The unique identifier SDKAppID of the audio and video application created in [Tencent RTC console](https://console.trtc.io/). |
| secretKey | String | The SDKSecretKey of the audio and video application created in [Tencent RTC console](https://console.trtc.io/). |
| userSig | String | A security protection signature used for user login authentication, confirming the authenticity of the user, and preventing malicious attackers from misappropriating your cloud service usage rights. |

> **Note:****Development environment**: If you are in the local development and debugging stage, you can use the local GenerateTestUserSig.genTestSig function to generate userSig. Note that the SDKSecretKey in this method may be easily decompiled and reverse engineered. Once the key is leaked, attackers may misappropriate your Tencent Cloud traffic.**Production environment**: If you want to launch your project, use [UserSig generation by the server](https://www.tencentcloud.com/zh/document/product/647/35166#.E6.AD.A3.E5.BC.8F.E8.BF.90.E8.A1.8C.E9.98.B6.E6.AE.B5.E5.A6.82.E4.BD.95.E8.AE.A1.E7.AE.97-usersig.EF.BC.9F).

## Step Five: Start Your First Conversational AI project

Upon success of [TUILogin.login](https://www.tencentcloud.com/document/product/647/54843#07002a30-aca6-4e6e-991f-0d8b65e315a6), see the following code to initiate conversational AI.

Swift

New Option

```
let startParams = StartAIConversationParams()let sdkAppId = 1600000001  // 1,Replace your sdkAppIdlet secretKey = "xxx"      // 2,Replace your sdkSecretKeylet aiRobotId = "robot_\\(TUILogin.getUserID() ?? "")"let aiRobotSig = GenerateTestUserSig.genTestUserSig(sdkAppId: sdkAppId, identifier: aiRobotId, secrectkey: secretKey)startParams.agentConfig = AIConversationDefine.AgentConfig.generateDefaultConfig(aiRobotId: aiRobotId, aiRobotSig: aiRobotSig)startParams.secretId = "xxx"           // 3,Replace your secretIdstartParams.secretKey = "xxx"          // 4,Replace your secretKey// 5,Replace your llmConfigstartParams.llmConfig = "{\\"LLMType\\":\\"openai\\",\\"Model\\":\\"hunyuan-turbo-latest\\",\\"SystemPrompt\\":\\"You are a personal assistant\\",\\"APIUrl\\":\\"https://hunyuan.cloud.tencent.com/openai/v1/chat/completions\\",\\"APIKey\\":\\"xxxx\\",\\"History\\":5,\\"Streaming\\":true}"// 6,Replace your ttsConfigstartParams.ttsConfig = "{\\"TTSType\\":\\"tencent\\",\\"AppId\\":\\"xxx\\",\\"SecretId\\":\\"xxx\\",\\"SecretKey\\":\\"xxx\\",\\"VoiceType\\":\\"502001\\",\\"Speed\\":1.25,\\"Volume\\":5,\\"PrimaryLanguage\\":1,\\"FastVoiceType\\":\\"\\"}"let aiViewController = AIConversationViewController(aiParams: startParams)navigationController?.pushViewController(aiViewController, animated: true)
```

```

```

1. Use the data obtained in [step four](https://www.tencentcloud.com/document/product/647/69005#07002a30-aca6-4e6e-991f-0d8b65e315a6) for sdkAppId and sdkSecretKey.
2. On the application details page, select **RTC-Engine** **> Conversational AI**, refer to [No-Code Quick Integration Of Conversational AI Feature](https://www.tencentcloud.com/document/product/647/68137) configure conversational AI service parameters, including basic configuration, STT, LLM, TTS, click lower right corner **Quick Interation**, switch to iOS, obtain SecretId, SecretKey and Config parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ed13240112e511f09fca52540099c741.png)

3. Copy the SecretId and SecretKey of TencentCloud API to `startParams.secretId` and `startParams.secretKey`.
4. Copy the Config information to a JSON parsing tool, such as [JsonUtil](https://www.json.cn/). Copy the string value corresponding to LLMConfig to `startParams.llmConfig`, and copy the string value corresponding to TTSConfig to `startParams.ttsConfig`.

> **Note:****Development environment**: If you are in the local development and debugging stage, you can quickly integrate AI conversation by adopting the above method. In this method, account information is very easy to be decompiled and reverse cracked. Once your key is leaked, attackers can misappropriate your Tencent Cloud traffic.**Live production environment**: If your project is going to be launched, please save the above account information to the server to avoid misappropriation of traffic; related dialogue configurations can also be saved to the server for convenient dynamic adjustment of the AI dialogue effect.

## Contact us

If you have any questions or suggestions during the integration process, you are welcome to contact: info_rtc@tencent.com .


---
*Source: [https://trtc.io/document/69005](https://trtc.io/document/69005)*
