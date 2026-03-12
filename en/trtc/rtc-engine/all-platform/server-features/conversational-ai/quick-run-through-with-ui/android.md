# Android

This document will guide you on how to integrate the `AIConversationKit` component in a short time. Following this guide, you will complete the following key steps within 20 minutes and implement a conversational AI project with a complete UI.

| **Conversational AI Interface**![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e2c65f4312e511f09fca52540099c741.png) |
| --- |
|  |

## Environment Preparation

- Minimum compatibility with Android 4.4 (SDK API Level 19). Recommend using Android 5.0 (SDK API Level 21) and above versions.
- Android Studio 3.5 and above versions (Gradle 3.5.4 and above versions).
- Mobile devices running Android 4.4 and above.

## Step One: Activating Service

Before initiating a conversation with AiConversationKit, you need to go to the console to activate conversational AI service for AIConversationKit. For specific steps, please see [Activate Service](https://www.tencentcloud.com/document/product/647/69002#).

## Step Two: Download the TUIRoomKit Component

1. Clone the code in [Github](https://github.com/Tencent-RTC/AIConversationKit), then copy the `aiconversatonkit` subdirectory under the `Android` directory to the same-level directory of the app in your current project, as shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e2b1d43812e511f0aaa3525400e889b2.png)

## Step Three: Configuration

1. Find the `setting.gradle (or settings.gradle.kts)` file in the project root directory, and add the following code in it. It enables importing the `aiconversationkit` component into your current project.

settings.gradle

settings.gradle.kts

```
include ':aiconversationkit'
```

```
include (":aiconversationkit")
```

2. Find the `build.gradle (or build.gradle.kts)` file under the app directory, and add the following code in it. It enables the current `app` to depend on the newly added `aiconversationkit` component.

build.gradle

build.gradle.kts

```
api project(':aiconversationkit')
```

```
api(project(":aiconversatonkit"))
```

3. Since we use Java's reflection features within the SDK, some classes in the SDK need to be added to the non-obfuscation list. Therefore, you need to add the following code in the proguard-rules.pro file:

```
-keep class com.tencent.** { *; }
```

4. Find the AndroidManifest.xml file under the app directory. Add `tools:replace="android:allowBackup"` in the `application` node. Override the settings within the component and use your own settings.

```
  // app/src/main/AndroidManifest.xml  <application    android:name=".DemoApplication"    android:allowBackup="false"    android:icon="@drawable/app_ic_launcher"    android:label="@string/app_name"    android:largeHeap="true"    android:theme="@style/AppTheme"    tools:replace="android:allowBackup">
```

## Step Four: Sign In

Add the following code to your project. It enables the login of the component by calling relevant APIs in `TUILogin`. **This step is critical** because only after logging in can `AIConversationkit` features be used normally. Please patiently check if the relevant parameters are configured correctly.

Java

Kotlin

```
String userId = "denny"; // Please replace with your UserIDint ââsdkAppId = 1400000001; // Please replace with the sdkAppId obtained in step 1String sdkSecretKey = "xxxx"; // Please replace with the sdkSecretKey obtained in step 1String userSig = GenerateTestUserSig.genTestUserSig(sdkAppId, userId, sdkSecretKey);TUILogin.login(this, sdkAppId, userId, userSig, new TUICallback() {    @Override public void onSuccess() {}    @Override public void onError(int errorCode, String errorMessage) {}});
```

```
val userId = "denny" // Please replace with your UserIDval sdkAppId = 1400000001 // Please replace with the sdkAppId obtained in step 1val sdkSecretKey = "xxxx" // Please replace with the sdkSecretKey obtained in step 1val userSig = GenerateTestUserSig.genTestUserSig(sdkAppId, userId, sdkSecretKey)TUILogin.login(this, sdkAppId, userId, userSig, object : TUICallback() {      override fun onSuccess() {}      override fun onError(errorCode: Int, errorMessage: String) {}})
```

| Parameter | Type | Description |
| --- | --- | --- |
| userId | String | Customers customize their Custom User IDs according to their own business, which only allow a combination of uppercase and lowercase letters (a-z A-Z), numbers (0-9), underline and hyphen. |
| sdkAppId | int | The unique identifier SDKAppID of the audio and video application created in [Tencent RTC console](https://console.trtc.io/). |
| secretKey | String | The SDKSecretKey of the audio and video application created in [Tencent RTC console](https://console.trtc.io/). |
| userSig | String | A security protection signature used for user login authentication to confirm the authenticity of the user and prevent malicious attackers from misappropriating your cloud service usage rights. |

> **Notes:****Development environment**: If you are in the local development and debugging stage, you can use the local `GenerateTestUserSig.genTestSig` function to generate userSig. In this method, the SDKSecretKey can be easily decompiled and reverse cracked. Once your key leaks, attackers can unauthorized use your Tencent Cloud traffic.**Production environment**: If you want to launch your project, please use [UserSig generation by the server](https://trtc.io/document/35166).

## Step Five: Start Your First AI Conversation

Upon success of [TUILogin.login](https://www.tencentcloud.com/document/product/647/69004#07002a30-aca6-4e6e-991f-0d8b65e315a6), see the following code to initiate conversational AI service.

Java

Kotlin

```
AIConversationDefine.StartAIConversationParams startParams = new AIConversationDefine.StartAIConversationParams();int sdkAppId = 1400000001;      // 1,Replace your sdkAppIdString sdkSecretKey = "xxxx";   // 2,Replace your sdkSecretKeyString aiRobotId = "robot_" + TUILogin.getUserId();String aiRobotSig = GenerateTestUserSig.genTestUserSig(sdkAppId, aiRobotId, sdkSecretKey);startParams.agentConfig = AIConversationDefine.AgentConfig.generateDefaultConfig(aiRobotId, aiRobotSig);startParams.secretId = "xxx";  // 3,Replace your secretIdstartParams.secretKey = "xxx"; // 4,Replace your secretKey// 5,Replace your  llmConfigstartParams.llmConfig = "{\\"LLMType\\":\\"openai\\",\\"Model\\":\\"hunyuan-turbo-latest\\",\\"SystemPrompt\\":\\"You are a private assistant\\",\\"APIUrl\\":\\"https:xxx\\",\\"APIKey\\":\\"xxx\\",\\"History\\":5,\\"Streaming\\":true}"; // 6,Replace your  ttsConfigstartParams.ttsConfig = "{\\"TTSType\\":\\"tencent\\",\\"AppId\\":\\"xxx\\",\\"SecretId\\":\\"xxx\\",\\"SecretKey\\":\\"xxx\\",\\"VoiceType\\":\\"502001\\",\\"Speed\\":1.25,\\"Volume\\":5,\\"PrimaryLanguage\\":1,\\"FastVoiceType\\":\\"\\"}";Intent intent = new Intent(this, AIConversationActivity.class);intent.putExtra(KEY_START_AI_CONVERSATION, startParams);startActivity(intent);
```

```
val startParams = AIConversationDefine.StartAIConversationParams()val sdkAppId = 1400000001 // 1,Replace your sdkAppIdval sdkSecretKey = "xxxx" // 2,Replace your sdkSecretKeyval aiRobotId = "robot_" + TUILogin.getUserId()val aiRobotSig = GenerateTestUserSig.genTestUserSig(sdkAppId, aiRobotId, sdkSecretKey)startParams.agentConfig = AIConversationDefine.AgentConfig.generateDefaultConfig(aiRobotId, aiRobotSig)startParams.secretId = "xxx" // 3,Replace your  secretIdstartParams.secretKey = "xxx" // 4,Replace your secretKey// 5,Replace your  llmConfigstartParams.llmConfig = "{\\"LLMType\\":\\"openai\\",\\"Model\\":\\"hunyuan-turbo-latest\\",\\"SystemPrompt\\":\\"You are a private assistant\\",\\"APIUrl\\":\\"https:xxx\\",\\"APIKey\\":\\"xxx\\",\\"History\\":5,\\"Streaming\\":true}"// 6,Replace your  ttsConfigstartParams.ttsConfig = "{\\"TTSType\\":\\"tencent\\",\\"AppId\\":\\"xxx\\",\\"SecretId\\":\\"xxx\\",\\"SecretKey\\":\\"xxx\\",\\"VoiceType\\":\\"502001\\",\\"Speed\\":1.25,\\"Volume\\":5,\\"PrimaryLanguage\\":1,\\"FastVoiceType\\":\\"\\"}"val intent = Intent(this, AIConversationActivity::class.java)intent.putExtra(KEY_START_AI_CONVERSATION, startParams)startActivity(intent)
```

1. Use the data obtained in [step four](https://www.tencentcloud.com/document/product/647/69004#07002a30-aca6-4e6e-991f-0d8b65e315a6) for sdkAppId and sdkSecretKey.
2. On the application details page, select **RTC-Engine** **> Conversational AI**, refer to [No-Code Quick Integration Of Conversational AI Feature](https://www.tencentcloud.com/document/product/647/68137) configure conversational AI service parameters, including basic configuration, STT, LLM, TTS, click lower right corner **Quick Interation**, switch to Android, obtain SecretId, SecretKey and Config parameters.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e2d9131512e511f0a9cd5254007c27c5.png)

3. Copy the SecretId and SecretKey of TencentCloud API to `startParams.secretId` and `startParams.secretKey`.
4. Copy the Config info to a JSON parsing tool, such as [JsonUtil](https://www.json.cn/). Copy the string value corresponding to LLMConfig to `startParams.llmConfig`, and copy the string value corresponding to TTSConfig to `startParams.ttsConfig`.

> **Note:****Development environment**: If you are in the local development and debugging stage, you can quickly integrate AI conversation by adopting the above method. In this method, account information can be easily decompiled and reverse engineered. Once your key leaks, attackers can misappropriate your Tencent Cloud traffic.**Live production environment**: If your project is going to be launched, please save the above account information to the server to avoid traffic misappropriation; related dialogue configurations can also be saved to the server for convenient dynamic adjustment of the AI dialogue effect.

## Contact us

If you have any questions or suggestions during the integration process, feel free to contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/69004](https://trtc.io/document/69004)*
