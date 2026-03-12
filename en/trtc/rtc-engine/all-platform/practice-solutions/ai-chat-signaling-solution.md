# AI Chat Signaling Solution

## Chat SDK Integration

iOS

Android

Web & Mini Programs

### Integrating Chat SDK

It is recommended to use CocoaPods for automatic loading when integrating the Chat SDK.

1. Install CocoaPods by entering the following command in the terminal window (ensure that the Ruby environment is pre-installed on your Mac):

```
sudo gem install cocoapods
```

2. Create a Podfile. Navigate to the project directory and enter the following command. A Podfile will then be generated in the project directory.

```
pod init
```

3. Edit the Podfile. Configure the Podfile as follows:

```
platform :ios, '8.0'source 'https://github.com/CocoaPods/Specs.git'target 'App' do    # Integrate the full version of the Chat SDK. The version number should be greater than '8.1.6129'.    pod 'TXIMSDK_Plus_iOS','8.1.6129'    # Alternatively, integrate the trimmed version of the Chat SDK (only includes AI signaling-related capabilities). The version number should be greater than '8.2.6361'.    pod 'TXIMSDK_Plus_SignalingSDK','8.2.6361'end
```

4. Update and install the SDK.

In the terminal window, enter the following command to update the local repository files and install the Chat SDK.

```
pod install
```

Or run this command to update the local repository:

```
pod update
```

> **Note:**If you encounter issues after performing the above steps, see [Xcode Integration Common Issues](https://trtc.io/document/34307?platform=ios%20and%20macos&product=chat&menulabel=sdk#faqs) document.

### Referencing Chat SDK

There are two ways to use the SDK in your project code:

- In `Xcode > Build Settings > Header Search Paths`, set the path to the SDK header files. Then, in the project files where the SDK APIs are needed, include the specific header files.

```
#import "ImSDK_Plus.h"
```

- In the project files where the SDK APIs are needed, include the specific header files.

```
#import <ImSDK_Plus/ImSDK_Plus.h>
```

### Integrating SDK (AAR)

It is recommended to use Gradle for automatic loading when integrating the Chat SDK.

1. Add SDK dependencies.
  1.1. Locate the appâs build.gradle file and add the mavenCentral() dependency under the repositories.

```
repositories {    google()    // Add the mavenCentral repository.    mavenCentral()}
```

  1.2. Then, add the Chat SDK dependency to the dependencies.

```
dependencies {    // Integrate the full version of the Chat SDK. The version number should be greater than '8.1.6129'.    api 'com.tencent.imsdk:imsdk-plus:8.1.6129'         // Alternatively, integrate the trimmed version of the Chat SDK (only includes AI signaling-related capabilities). The version number should be greater than '8.2.6361'.    api 'com.tencent.imsdk:signalingsdk:8.2.6361'}
```

2. Specify the CPU architecture used by the App in defaultConfig. (Chat SDK version 4.3.118 and later support armeabi-v7a, arm64-v8a, x86, and x86_64.)

```
defaultConfig {    ndk {      abiFilters "arm64-v8a"     } }
```

3. Sync the SDK. Ensure your network is connected to Maven, then click Sync to automatically download and integrate the SDK into your project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/15f4c7ebc43211f0aa02525400e889b2.png)

### Configuring App Permissions

To configure App permissions in AndroidManifest.xml. the Chat SDK requires the following permissions:

```
    <uses-permission android:name="android.permission.INTERNET" />    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
```

### Configuring Obfuscation Rules

In the proguard-rules.pro file, add the Chat SDK-related classes to the non-obfuscation list:

```
-keep class com.tencent.imsdk.** { *; }
```

### Integrating SDK

It is recommended to integrate the Chat SDK into your Web or Mini Programs using npm.

```
// Version v3.4.5 or laternpm install @tencentcloud/chat
```

> **Note:**If issues occur during dependency synchronization, switch the npm source and try again.

```
npm config set registry http://r.cnpmjs.org/
```

### Importing Modules

```
import TencentCloudChat from '@tencentcloud/chat';
```

## Initializing the SDK

iOS

Android

Web & Mini Programs

1. Call the initialization API.

```
// 1. Obtain the application SDKAppID from the Chat console.// 2. Initialize the config object.V2TIMSDKConfig *config = [[V2TIMSDKConfig alloc] init];// 3. Specify the log output level.config.logLevel = V2TIM_LOG_INFO;// 4. Add the event listener for V2TIMSDKListener. The self is an implementation of id<V2TIMSDKListener>. If you do not need to listen to IM SDK events, this step can be skipped.[[V2TIMManager sharedInstance] addIMSDKListener:self];// 5. Initialize the Chat SDK. After calling this API, you can immediately call the log-in API.[[V2TIMManager sharedInstance] initSDK:sdkAppID config:config];
```

2. Log in.

```
NSString *userID = @"your user id";NSString *userSig = @"userSig from your server";[[V2TIMManager sharedInstance] login:userID userSig:userSig succ:^{    NSLog(@"success");} fail:^(int code, NSString *desc) {    // The following error codes indicate an expired userSig, and you need to generate a new one for log-in again.    // 1. ERR_USER_SIG_EXPIRED(6206).    // 2. ERR_SVR_ACCOUNT_USERSIG_EXPIRED(70001).    // Note: Do not call the log-in API in case of other error codes. Otherwise, the Chat SDK login may enter an infinite loop.    NSLog(@"failure, code:%d, desc:%@", code, desc);}];
```

1. Call the initialization API.

```
// 1. Obtain the application SDKAppID from the Chat console.// 2. Initialize the config object.V2TIMSDKConfig config = new V2TIMSDKConfig();// 3. Specify the log output level.config.setLogLevel(V2TIMSDKConfig.V2TIM_LOG_INFO);// 4. Add the event listener for V2TIMSDKListener. The sdkListener is an implementation of V2TIMSDKListener. If you do not need to listen to IM SDK events, this step can be skipped.V2TIMManager.getInstance().addIMSDKListener(sdkListener);// 5. Initialize the IM SDK. After calling this API, you can immediately call the log-in API.V2TIMManager.getInstance().initSDK(context, sdkAppID, config);
```

2. Log in.

```
String userID = "your user id";String userSig = "userSig from your server";V2TIMManager.getInstance().login(userID, userSig, new V2TIMCallback() {    @Override    public void onSuccess() {        Log.i("imsdk", "success");    }    @Override    public void onError(int code, String desc) {        // The following error codes indicate an expired userSig, and you need to generate a new one to log in again.        // 1. ERR_USER_SIG_EXPIRED(6206).        // 2. ERR_SVR_ACCOUNT_USERSIG_EXPIRED(70001).        // Note: Do not call the log-in API in case of other error codes. Otherwise, the Chat SDK login may enter an infinite loop.        Log.i("imsdk", "failure, code:" + code + ", desc:" + desc);    }});
```

1. Call the initialization API.

```
import TencentCloudChat from '@tencentcloud/chat';let options = {  SDKAppID: 0 // Replace 0 with the SDKAppID of your Chat application during access.};// Create an SDK instance. The `TencentCloudChat.create()` method will return the same instance for the same `SDKAppID`.let chat = TencentCloudChat.create(options); // The SDK instance is typically represented as chat.chat.setLogLevel(0); // Standard level with extensive volume of logs; recommended for access.// chat.setLogLevel(1); // Release level, where the SDK outputs critical information; recommended for production environments.
```

2. Log in.

```
let promise = chat.login({userID: 'your userID', userSig: 'your userSig'});promise.then(function(imResponse) {  console.log(imResponse.data); // Login successful.  if (imResponse.data.repeatLogin === true) {    // Indicates that the account is already logged in, and this login operation is a duplicate login.    console.log(imResponse.data.errorInfo);  }}).catch(function(imError) {  console.warn('login error:', imError); // Information related to login failure.});
```

> **Note:**The `sdkAppId` and `secretKey` for TRTC and Chat should be identical.The recipientâs Chat should be successfully logged in and online to receive messages.The recipientâs TRTC account and Chat account should share the same `userId`, meaning they should use the same `userId` for entering the TRTC room and logging in to Chat .

## Receiving Server Downstream Messages

Receive one-on-one custom messages via the Chat SDK ([iOS & Android](https://trtc.io/document/47995?platform=ios%20and%20macos&product=chat&menulabel=sdk#receiving-a-custom-message) / [Web & Mini Programs](https://trtc.io/document/47996?platform=javascript&product=chat&menulabel=sdk)) by listening to callbacks on the client to receive real-time subtitles and AI status data.

| Type | Description |
| --- | --- |
| 10000 | Real-time subtitles and translation delivery |
| 10001 | AI conversation real-time status delivery |
| 10010 | Large model message passthrough |

### Receiving Real-Time Subtitles

```
{  "type": 10000, // 10000 indicates the delivery of real-time subtitles.  "sender": "user_a", // The user ID of the speaker.  "receiver": [], // List of receiver user IDs. This message is actually broadcast within the room.  "payload": {     "text":"", // The text recognized by Automatic Speech Recognition (ASR).     "translation_text":"", // The translated text.     "start_time":"00:00:01", // The start time of this sentence.     "end_time":"00:00:02", // The end time of this sentence.     "roundid": "xxxxx" // A unique identifier for a single conversation round.     "end": true // If true, it indicates this is a complete sentence.  }}
```

### Receiving Chatbot Status

```
{  "type": 10001, // Chatbot status.  "sender": "user_a", // The user ID of the sender, which represents the chatbot's ID in this case.  "receiver": [], // List of receiver user IDs. This message is actually broadcast within the room.  "payload": {    "roundid": "xxx", // A unique identifier for a single conversation round.    "timestamp": 123     "state": 1,      //   1 Listening  2 Thinking  3 Speaking  4 Interrupted  }}
```

### Receiving Large Model Message Passthrough

```
{  "type": 10010, // Downstream large model message passthrough.  "sender": "user_a", // The user ID of the sender, which represents the chatbot's ID in this case.  "receiver": [], // List of receiver user IDs. This message is actually broadcast within the room.  "payload": {    "id": "uuid", // Message ID, can use UUID; optional, used for troubleshooting.    "taskid":"xxxxxx", // The task ID of the AI conversation; required.    "timestamp": 123 // Timestamp, used for troubleshooting; optional.        "data": {            "key": "value" // Custom JSON format defined by business.        }  }}
```

### Sample Code

iOS

Android

Web & Mini Programs

```
// Call addSimpleMsgListener to set up an event listener.V2TIMManager.sharedInstance().addSimpleMsgListener(listener: self)/// Receive one-on-one custom messages./// @param msgID message ID/// @param info sender information/// @param data custom message content in binary formatfunc onRecvC2CCustomMessage(_ msgID: String!, sender info: V2TIMUserInfo!, customData data: Data!) {    do {        if let jsonObject = try JSONSerialization.jsonObject(with: data, options: []) as? [String: Any] {            print("onRecvGroupCustomMessage: \\(jsonObject)")            handleMessage(jsonObject)        } else {            print("The data is not a dictionary.")        }    } catch {        print("Error parsing JSON: \\(error)")    }}
```

```
// Call addSimpleMsgListener to set up an event listener.V2TIMManager.getInstance().addSimpleMsgListener(sdkListener);/** * Receive one-on-one custom messages. * @param msgID message ID * @param sender sender information * @param customData the content to be sent */public void onRecvC2CCustomMessage(String msgID, V2TIMUserInfo sender, byte[] customData) {    Log.i("onRecvC2CCustomMessage", "msgID:" + msgID + ", from:" + sender.getNickName() + ", content:" + new String(customData));    try {        String jsonString = new String(customData, "UTF-8");        JSONObject jsonObject = new JSONObject(jsonString);        System.out.println("onRecvGroupCustomMessage: " + jsonObject);        handleMessage(jsonObject);     } catch (UnsupportedEncodingException e) {        System.out.println("The data is not a dictionary.");     } catch (JSONException e) {        System.out.println("Error parsing JSON: " + e);     }}
```

```
const onMessageReceived = (event) => {  const messageList = event.data;  messageList?.forEach((msg) => {    if (msg.type === TencentCloudChat.TYPES.MSG_CUSTOM) {      console.log('received custom message', event);      const { data } = msg.payload;      try {        const jsonData = JSON.parse(data);        console.log(`receive custom msg from ${msg.from} data: ${data}`);        if (jsonData.type === 10000) {          console.log('subtitle message', jsonData);          return;        }        if (jsonData.type === 10001) {          console.log('chatbot status', jsonData);          return;        }        if (jsonData.type === 10010) {          console.log('downstream large model message passthrough', jsonData);          return;        }      } catch (error) {        console.error('receive custom msg', data, error);      }    }  });}// Listen to messages.chat.on(TencentCloudChat.EVENT.MESSAGE_RECEIVED, onMessageReceived);
```

> **Note:**By default, real-time subtitles and AI status data are received via one-on-one custom messages. If one-on-one messaging does not meet your needs and you require a group chat custom message channel, [contact us](https://www.tencentcloud.com/contact-us).

## Sending Upstream Signaling from Client

You can send custom signaling to skip the ASR process and communicate directly with AI using text, send interruption signaling to perform an interruption, or directly send passthrough information to the large model.

| Type | Description |
| --- | --- |
| 20000 | ai_conversation_chat: Send AI conversation text. |
| 20001 | ai_conversation_interrupt: Manually interrupt. |
| 20010 | Send passthrough information to the large model. |

### Sending Upstream Signaling to Skip the ASR Process and Communicate Directly with AI Using Text

```
{  "type": 20000,   "sender": "user_a", // The user ID of the sender. The server will validate if this user ID is valid.  "receiver": ["user_bot"], // List of receiver userIDs. Only the chatbot user ID needs to be specified. The server will validate if this user ID is valid.  "payload": {    "id": "uuid", // Message ID, can use UUID; used for troubleshooting.    "message": "xxx", // Message content.    "timestamp": 123, // Timestamp, used for troubleshooting.    "taskid": "v2_20240920_xxxxx",  }}
```

### Sending Interruption Signaling for Interruption

```
{  "type": 20001,   "sender": "userid", // The user ID of the sender. The server will check if this userID is valid.  "receiver": ["user_bot"], // List of receiver userIDs. Only the chatbot user ID needs to be specified.  "payload": {    "id": "uuid", // Message ID, can use UUID; used for troubleshooting.    "timestamp": 123 // Timestamp, used for troubleshooting.    "taskid": "v2_20240920_xxxxx",  }}
```

### Send Passthrough Information to the Large Model

```
{    "type": 20010,    "sender": "userid",    "receiver": [        "robotid"    ],    "payload": {        "id": "uuid",        "taskid": "v2_20240920_xxxxx",        "timestamp": 1234,        "data": {            "key": "value" // Custom JSON format defined by business.        }    }}
```

### Sample Code

iOS

Android

Web & Mini Programs

```
@IBAction func interruptAi(_ sender: UIButton) {    let timestamp = Int(Date().timeIntervalSince1970 * 1000)    let payload = [        "id": userId + "_\\(roomId)" + "_\\(timestamp)", // Message ID, can use UUID; used for troubleshooting.        "timestamp": timestamp, // Timestamp, used for troubleshooting.        "taskid": aiTaskId,    ] as [String : Any]    let content = [        "type": 20001,        "sender": userId,        "receiver": [botId],        "payload": payload    ] as [String : Any]    let contentData = try! JSONSerialization.data(withJSONObject: content, options: [])    let contentString = String(data: contentData, encoding: .utf8)!    let dataDict = [        "service_command": "trtc_ai_service.SendCustomCmdMsg",        "request_content": contentString    ] as [String : Any]    do {        let jsonData = try JSONSerialization.data(withJSONObject: dataDict, options: [])        V2TIMManager.sharedInstance().callExperimentalAPI("sendTRTCCustomData", param: jsonData as NSObject) { _ in            print("sendTRTCCustomData success")        } fail: { code, desc in            print("sendTRTCCustomData error, \\(code), \\(desc ?? "null")")        }    } catch {        print("Error serializing dictionary to JSON: \\(error)")    }}
```

```
public void interruptAi() {    long timestamp = System.currentTimeMillis();    Map<String, Object> payload = new HashMap<>();    payload.put("id", userId + "_" + roomId + "_" + timestamp); // Message ID, can use UUID; used for troubleshooting.    payload.put("timestamp", timestamp); // Timestamp, used for troubleshooting.    payload.put("taskid", aiTaskId);    Map<String, Object> content = new HashMap<>();    content.put("type", 20001);    content.put("sender", userId);    content.put("receiver", Collections.singletonList(botId));    content.put("payload", payload);    String contentString = new JSONObject(content).toString();    Map<String, Object> dataDict = new HashMap<>();    dataDict.put("service_command", "trtc_ai_service.SendCustomCmdMsg");    dataDict.put("request_content", contentString);    try {        byte[] jsonData = new JSONObject(dataDict).toString().getBytes("UTF-8");        V2TIMManager.getInstance().callExperimentalAPI("sendTRTCCustomData", jsonData, new V2TIMValueCallback() {            @Override            public void onSuccess(Object o) {                System.out.println("sendTRTCCustomData success");            }            @Override            public void onError(int code, String desc) {                System.out.println("sendTRTCCustomData error, " + code + ", " + (desc != null ? desc : "null"));            }        });    } catch (UnsupportedEncodingException e) {        System.out.println("Error serializing dictionary to JSON: " + e);    }}
```

```
// Send interruption signaling.chat.callExperimentalAPI('sendTRTCCustomData', {serviceCommand: 'trtc_ai_service.SendCustomCmdMsg',data: {  type: 20001,  sender: "user_a", // The user ID of the sender. The server will check if this user ID is valid.  receiver: ["user_bot"], // List of receiver user IDs. Only the chatbot user ID needs to be specified.  payload: {    id: "uuid", // Message ID, can use UUID; used for troubleshooting.    timestamp: 123, // Timestamp, used for troubleshooting.    taskid: "Task's taskID",  }}});
```

> **Note:**The fields `type`, `sender`, `receiver`, and `payload`, including `taskid`, `id`, and `timestamp`, are required.


---
*Source: [https://trtc.io/document/74580](https://trtc.io/document/74580)*
