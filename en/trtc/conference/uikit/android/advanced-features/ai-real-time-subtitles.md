# AI Real-Time Subtitles

## Feature Introduction

After integrating TUIRoomKit, you can enable the AI real-time subtitle feature by clicking "AI Assistant" in the bottom bar. The feature is achievable:

- **AI real-time subtitles**: Display the discussion content during the meeting process in the form of subtitles.
- **AI real-time meeting minutes**: Record the discussion content during the meeting process in text form.

> **Note:**Using this feature requires subscribing to [TUIRoomKit Activate the Service](https://www.tencentcloud.com/document/product/647/59973#). Except for normal call charges ([Audio/Video Duration Billing Instructions](https://www.tencentcloud.com/document/product/647/42734#)); when this feature performs speech to text, additional AI Intelligent Identification fees will occur. For details, see [AI Intelligent Identification Billing Instructions](https://www.tencentcloud.com/document/product/647/67832#).

| Click AI assistant in the bottom bar. | Enable AI real-time subtitles | View AI Real-Time Meeting Minutes |
| --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/15f6122f0ea911f088bd525400e889b2.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3d30ebc60ea911f0b3015254001c06ec.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/40f5adf70ea911f0ae6a525400454e06.png) |

## Feature Integration

### Prerequisites for Access

Turn on the "AI assistant" button in the bottom bar.

```
ConferenceSessionImpl.sharedInstance().isShowAISpeechToTextButton = true;
```

### **Enable AI Real-Time Subtitles**

Enable the AI real-time subtitle feature, which actually starts an AI transcription task. During this process, the backend will use robot stream pulling to perform real-time speech recognition and send subtitles and transcription messages. For more information on parameter configuration for enabling AI transcription tasks and querying transcription task status, please refer to [AI service-related interfaces](https://trtc.io/document/64967?product=rtcengine&menulabel=serverfeaturesapis).

- After a room is created, you can enable the AI real-time subtitle feature by using the following example code.

> **Note:**The voice transcription feature requires a key to be enabled. Since code leakage may lead to the leakage of SecretId and SecretKey, and threaten the security of all resources under the account. It is recommended to use the key in a more secure way. For details, see [Recommended Cloud API Key Security Solutions](https://www.tencentcloud.com/document/product/1061/36935). The key can be obtained by going to [API Key Management](https://console.tencentcloud.com/cam/capi).

Java

Kotlin

```
private String mTaskId;                          // Task ID after enabling AI transcriptionprivate String aiSecretId  = "PLACEHOLDER";      // AI voice transcription IDprivate String aiSecretKey = "PLACEHOLDER";      // AI voice transcription keyprivate String roomId = "PLACEHOLDER";           // Room IDprivate int    sdkAppId = 0L;                    // Your SDKAppIdprivate String sdkSecretKey = "PLACEHOLDER";     // Your SDKAppId keyprivate String robotUserId = "PLACEHOLDER";      // AI chatbot's userId in the room, which cannot be the same as other users' userIds in the roomprivate void startAITranscription() {    Runnable startAITranscriptionRun = () -> {        try {            // Code leakage may lead to the leakage of aiSecretId and aiSecretKey, and threaten the security of all resources under the account.            // The following code example is for reference only. It is recommended to use the key in a more secure way. Please see: https://cloud.tencent.com/document/product/1278/85305            // Obtain the key at the official website console https://console.cloud.tencent.com/cam/capi            Credential credential = new Credential(aiSecretId, aiSecretKey);            TrtcClient client = new TrtcClient(credential, null);            StartAITranscriptionRequest request = new StartAITranscriptionRequest();            request.setRoomId(roomId);            request.setRoomIdType(1L);            request.setSdkAppId((long)sdkAppId);            TranscriptionParams transcriptionParams = new TranscriptionParams();            transcriptionParams.setUserId(robotUserId);            transcriptionParams.setUserSig(GenerateTestUserSig.genTestUserSig(sdkAppId, robotUserId, sdkSecretKey));            request.setTranscriptionParams(transcriptionParams);            StartAITranscriptionResponse response = client.StartAITranscription(request);            mTaskId = response.getTaskId();        } catch (TencentCloudSDKException e) {            e.printStackTrace();        }    };    new Thread(startAITranscriptionRun).start();}
```

```
private var mTaskId: String? = null      // Task ID after enabling AI transcriptionprivate val aiSecretId = "PLACEHOLDER"   // AI voice transcription IDprivate val aiSecretKey = "PLACEHOLDER"  // AI voice transcription keyprivate val roomId = "PLACEHOLDER"       // Room IDprivate val sdkAppId = 0L                // Your SDKAppIdprivate val sdkSecretKey = "PLACEHOLDER" // Your SDKAppId keyprivate val robotUserId = "PLACEHOLDER"  // AI chatbot's userId in the room, which cannot be the same as other users' userIds in the roomprivate fun startAITranscription() {    Thread {        try {            // Code leakage may lead to the leakage of aiSecretId and aiSecretKey, and threaten the security of all resources under the account.            // The following code example is for reference only. It is recommended to use the key in a more secure way. Please see: https://cloud.tencent.com/document/product/1278/85305            // Obtain the key at the official website console https://console.cloud.tencent.com/cam/capi            val credential = Credential(aiSecretId, aiSecretKey)            val client = TrtcClient(credential, null)                        val request = StartAITranscriptionRequest()            request.roomId = roomId            request.roomIdType = 1L            request.sdkAppId = sdkAppId                        val transcriptionParams = TranscriptionParams()            transcriptionParams.userId = robotUserId            transcriptionParams.userSig = GenerateTestUserSig.genTestUserSig(sdkAppId, robotUserId, sdkSecretKey)            request.transcriptionParams = transcriptionParams                        val response = client.StartAITranscription(request)            mTaskId = response?.taskId        } catch (e: TencentCloudSDKException) {            e.printStackTrace()        }    }.start()}
```

### Disable AI Real-Time Subtitles Feature

You can call the following code to disable the AI real-time subtitle feature when exiting room / terminating room.

Java

Kotlin

```
private void stopAITranscription() {    Runnable stopAITranscriptionRun = () -> {        try {            Credential credential = new Credential(secretId, secretKey);            TrtcClient client = new TrtcClient(credential, null);            StopAITranscriptionRequest stopAITranscriptionRequest = new StopAITranscriptionRequest();            stopAITranscriptionRequest.setTaskId(mTaskId);            client.StopAITranscription(stopAITranscriptionRequest);        } catch (TencentCloudSDKException e) {            e.printStackTrace();        }    };    new Thread(stopAITranscriptionRun).start();}
```

```
private fun stopAITranscription() {    Thread {        try {            val credential = Credential(secretId, secretKey)            val client = TrtcClient(credential, null)            val stopAITranscriptionRequest = StopAITranscriptionRequest()            stopAITranscriptionRequest.taskId = mTaskId            client.StopAITranscription(stopAITranscriptionRequest)        } catch (e: TencentCloudSDKException) {            e.printStackTrace()        }    }.start()}
```

> **Note:**If you have any requirements or feedback during the integration and use process, you can contact: info_rtc@tencent.com.


---
*Source: [https://trtc.io/document/68971](https://trtc.io/document/68971)*
