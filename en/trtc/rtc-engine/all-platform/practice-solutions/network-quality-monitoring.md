# Network Quality Monitoring

To help users be more aware of network quality, we recommend that business personnel perform a speed test before calls, monitor network quality and connection status during calls, and provide appropriate UI prompts and notifications. This way, users can easily evaluate their current network quality and promptly adjust network settings for optimal call performance.

## Performing Network Speed Tests Before Calls

Regular users often lack awareness of their network conditions. Therefore, it is recommended that you perform a speed test before calls. This can help users assess their current network quality and promptly adjust network settings for optimal call performance.

The principle of a speed test is that the SDK sends a batch of probe packets to server nodes, then calculates the quality of the returned packets, and notifies the speed test results through the callback API, as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e5d37ecebea511f085a55254007c27c5.png)

Advantages of pre-call speed tests:

- The speed test results will be used to optimize the server selection policy for the SDK. Therefore, we recommend running a speed test before a user makes the first call to help the SDK select the optimal server.
- If the test results are highly unsatisfactory, you can prompt the user through a prominent UI to choose a better network.

### Performing a Speed Test Through startSpeedTest

Android

iOS

Windows

```
// Example code for starting a network speed test. sdkAppId and UserSig are required (for the acquisition method, refer to Basic Features).// Here is an example of starting a speed test after logging inpublic void onLogin(String userId, String userSig) {  TRTCCloudDef.TRTCSpeedTestParams params = new TRTCCloudDef.TRTCSpeedTestParams();  params.sdkAppId = GenerateTestUserSig.SDKAPPID;  params.userId = mEtUserId.getText().toString();  params.userSig = GenerateTestUserSig.genTestUserSig(params.userId);  params.expectedUpBandwidth = Integer.parseInt(expectUpBandwidthStr);  params.expectedDownBandwidth = Integer.parseInt(expectDownBandwidthStr);    // sdkAppID is the actual application AppID obtained in the console    trtcCloud.startSpeedTest(params);}// Listen for the speed test results, inherit TRTCCloudListener, and implement the following methodvoid onSpeedTestResult(TRTCCloudDef.TRTCSpeedTestResult result){    // Call back the speed test results once the speed test is completed}Android
```

```
// Example code for starting a network speed test. sdkAppId and UserSig are required (for the acquisition method, refer to Basic Features).// Here is an example of starting a speed test after logging in- (void)onLogin:(NSString *)userId userSig:(NSString *)userSid {    TRTCSpeedTestParams *params;    // sdkAppID is the actual application AppID obtained in the console    params.sdkAppID = sdkAppId;    params.userID = userId;    params.userSig = userSig;    // Expected upstream bandwidth (Unit: kbps. Value range: 10â5000. A value of 0 indicates no test)    params.expectedUpBandwidth = 5000;    // Expected downstream bandwidth (Unit: kbps. Value range: 10â5000. A value of 0 indicates no test)    params.expectedDownBandwidth = 5000;    [trtcCloud startSpeedTest:params];}- (void)onSpeedTestResult:(TRTCSpeedTestResult *)result {    // Return the speed test results once the speed test is completed}
```

```
// Example code for starting a network speed test. sdkAppId and UserSig are required (for the acquisition method, refer to Basic Features).// Here is an example of starting a speed test after logging invoid onLogin(const char* userId, const char* userSig){    TRTCSpeedTestParams params;    // sdkAppID is the actual application AppID obtained in the console    params.sdkAppID = sdkAppId;    params.userId = userid;    param.userSig = userSig;    // Expected upstream bandwidth (Unit: kbps. Value range: 10â5000. A value of 0 indicates no test)    param.expectedUpBandwidth = 5000;    // Expected downstream bandwidth (Unit: kbps. Value range: 10â5000. A value of 0 indicates no test)    param.expectedDownBandwidth = 5000;    trtcCloud->startSpeedTest(params);}// Listen for the speed test resultsvoid TRTCCloudCallbackImpl::onSpeedTestResult(             const TRTCSpeedTestResult& result){    // Call back the speed test results once the speed test is completed}
```

The speed test results ([TRTCSpeedTestResult](https://trtc.io/document/50768?platform=android&product=rtcengine&menulabel=core%20sdk#25124dd8b486afcaeaabe326bfe10288)) contain the following fields:

| Field | Meaning | Description |
| --- | --- | --- |
| success | Whether the test is successful | Whether the current test is successful. |
| errMsg | Error message | Detailed error information of the bandwidth test. |
| ip | Server IP address | IP address of the testing server. |
| [quality](https://trtc.io/document/50768?platform=android&product=rtcengine&menulabel=core%20sdk#1796fe5bcef4aec6d520bdd8e530474b) | Network quality score | Network quality as calculated by the assessment algorithm. The lower the packet loss and the smaller the rtt, the higher the score. |
| upLostRate | Upstream packet loss rate | Range: 0â1.0. For example, a value of 0.3 means that 3 out of every 10 packets sent to the server may be lost midway. |
| downLostRate | Downstream packet loss rate | Range: 0â1.0. For example, a value of 0.2 means that 2 out of every 10 packets received from the server may be lost midway. |
| rtt | Network latency | Time taken for a round trip between the SDK and the server. The smaller the value, the better. A normal value is between 10 ms and 100 ms. |
| availableUpBandwidth | Upstream bandwidth | Predicted upstream bandwidth. Unit: kbps. A value of -1 indicates an invalid result. |
| availableDownBandwidth | Downstream bandwidth | Predicted downstream bandwidth. Unit: kbps. A value of -1 indicates an invalid result. |

### Performing a Speed Test Through Tools

If you do not want to perform a network speed test through API calls, Real-Time Communication Engine (RTC Engine) also provides a PC-based network speed test tool that allows you to quickly obtain detailed network quality information. Depending on your platform, you can choose the appropriate tool program from the options below to download. The program supports two test options, that is, rapid testing and continuous testing.

- [Mac](https://liteav.sdk.qcloud.com/customer/%E6%B5%8B%E8%AF%95/%E6%B5%8B%E8%AF%95%E5%B7%A5%E5%85%B7/trtc-network-tools-latest.dmg)
- [Windows](https://liteav.sdk.qcloud.com/customer/%E6%B5%8B%E8%AF%95/%E6%B5%8B%E8%AF%95%E5%B7%A5%E5%85%B7/trtc-network-tools_Setup_latest.exe)

| Metric | Meaning |
| --- | --- |
| WiFi Quality | Wi-Fi signal quality |
| DNS RTT | Duration of parsing the Tencent Cloud speed test domain name |
| MTR | A network test tool that can detect the packet loss rate and latency between the client and the RTC Engine node and display detailed information of each hop in the route |
| UDP Loss | UDP packet loss rate between the client and the RTC Engine node |
| UDP RTT | UDP latency between the client and the RTC Engine node |
| Local RTT | Latency between the client and the local gateway |
| Upload | Estimated upstream bandwidth |
| Download | Estimated downstream bandwidth |

> **Note:**Do not perform speed tests during video calls, as this may degrade the call quality.Performing a speed test consumes a small amount of traffic, which may result in minimal (almost negligible) additional traffic fees.

## Detecting Network Quality During Calls

To help users be more aware of potential network fluctuations during calls, it is recommended that you add appropriate UI alerts on the call interface. This is particularly important when network conditions are poor, as these alerts inform users of the issue, allowing them to make timely adjustments to improve network quality.

### Listening for Local Network Quality Through onNetworkQuality

The callback event onNetworkQuality reports the current network quality to you every 2 seconds. It includes two parameters, that is, localQuality and remoteQuality.

- localQuality: Represents your current network quality. The quality is divided into 6 levels, namely, Excellent, Good, Poor, Bad, VeryBad, and Down.
- remoteQuality: Represents the network quality of remote users. This is an array where each element represents the network quality of a remote user.

| Quality | Name | Description |
| --- | --- | --- |
| 0 | Unknown | Not detected. |
| 1 | Excellent | The current network is excellent. |
| 2 | Good | The current network is good. |
| 3 | Poor | The current network is moderate. |
| 4 | Bad | The current network is poor, and obvious lags and call delays may occur. |
| 5 | VeryBad | The current network is very poor. RTC Engine can merely sustain the connection but cannot guarantee communication quality. |
| 6 | Down | The current network fails to satisfy the minimum requirements of RTC Engine, and normal audio and video calls cannot be performed. |

Listen for onNetworkQuality and provide corresponding prompts on the interface.

Android

iOS&Mac

Windows

```
// Listen for the onNetworkQuality callback to stay aware of changes in the current network status@Overridepublic void onNetworkQuality(TRTCCloudDef.TRTCQuality localQuality,                             ArrayList<trtcclouddef.trtcquality> remoteQuality){    // Get your local network quality    switch(localQuality) {        case TRTCQuality_Unknown:            Log.d(TAG, "SDK has not yet sensed the current network quality.");            break;        case TRTCQuality_Excellent:            Log.d(TAG, "The current network is very good.");            break;        case TRTCQuality_Good:            Log.d(TAG, "The current network is good.");            break;        case TRTCQuality_Poor:            Log.d(TAG, "The current network quality barely meets the demand.");            break;        case TRTCQuality_Bad:            Log.d(TAG, "The current network is poor, and there may be significant freezes and call delays.");            break;        case TRTCQuality_VeryBad:            Log.d(TAG, "The current network is very poor, the communication quality cannot be guaranteed");            break;        case TRTCQuality_Down:            Log.d(TAG, "The current network does not meet the minimum requirements.");            break;        default:            break;    }    // Get the network quality of remote users    for (TRTCCloudDef.TRTCQuality info : arrayList) {        Log.d(TAG, "remote user : = " + info.userId + ", quality = " + info.quality);    }}
```

```
// Listen for the onNetworkQuality callback to stay aware of changes in the current network status- (void)onNetworkQuality:(TRTCQualityInfo *)localQuality remoteQuality:(NSArray<trtcqualityinfo *=""> *)remoteQuality {    // Get your local network quality    switch(localQuality.quality) {        case TRTCQuality_Unknown:            NSLog(@"SDK has not yet sensed the current network quality.");            break;        case TRTCQuality_Excellent:            NSLog(@"The current network is very good.");            break;        case TRTCQuality_Good:            NSLog(@"The current network is good.");            break;        case TRTCQuality_Poor:            NSLog(@"The current network quality barely meets the demand.");            break;        case TRTCQuality_Bad:            NSLog(@"The current network is poor, and there may be significant freezes and call delays.");            break;        case TRTCQuality_VeryBad:           NSLog(@"The current network is very poor, the communication quality cannot be guaranteed");            break;        case TRTCQuality_Down:            NSLog(@"The current network does not meet the minimum requirements.");            break;        default:            break;    }    // Get the network quality of remote users    for (TRTCQualityInfo *info in arrayList) {        NSLog(@"remote user : = %@, quality = %@", info.userId, @(info.quality));    }}iOSMac
```

```
// Listen for the onNetworkQuality callback to stay aware of changes in the current network statusvoid onNetworkQuality(liteav::TRTCQualityInfo local_quality,    liteav::TRTCQualityInfo* remote_quality, uint32_t remote_quality_count) {    // Get your local network quality    switch (local_quality.quality) {    case TRTCQuality_Unknown:        printf("SDK has not yet sensed the current network quality.");        break;    case TRTCQuality_Excellent:        printf("The current network is very good.");        break;    case TRTCQuality_Good:        printf("The current network is good.");        break;    case TRTCQuality_Poor:        printf("The current network quality barely meets the demand.");        break;    case TRTCQuality_Bad:        printf("The current network is poor, and there may be significant freezes and call delays.");        break;    case TRTCQuality_Vbad:        printf("The current network is very poor, the communication quality cannot be guaranteed");        break;    case TRTCQuality_Down:        printf("The current network does not meet the minimum requirements.");        break;    default:        break;    }    // Get the network quality of remote users    for (int i = 0; i < remote_quality_count; ++i) {        printf("remote user : = %s, quality = %d", remote_quality[i].userId, remote_quality[i].quality);    }}
```

### Listening for Full Network Quality Through onStatistics

The statistics callback event [onStatistics](https://trtc.io/document/50763?product=rtcengine&menulabel=core%20sdk&platform=android#faca91305f246db336cb6c56f7bfbf25) is thrown every 2 seconds to notify the statistics on professional technical metrics related to audio, video, and network performance within the SDK. The metrics are listed in [TRTCStatistics](https://trtc.io/document/50764?product=rtcengine&menulabel=core%20sdk&platform=android):

- Video statistics: Video resolution, frame rate (FPS), bitrate, and other information.
- Audio statistics: Audio sample rate (samplerate), number of audio channels (channel), bitrate, and other information.
- Network statistics: Network duration (rtt), packet loss rate (loss), upstream traffic (sentBytes), downstream traffic (receivedBytes), and other information for a round trip between the SDK and the cloud (SDK > Cloud > SDK).

| Enumeration Type | Description |
| --- | --- |
| appCpu | CPU utilization of the current application. Unit: %. Android 8.0 or later is not supported. |
| downLoss | Downstream packet loss rate from the cloud to the SDK. Unit: %.The smaller the value, the better. If downLoss is 0%, the downstream network quality is very good, and the data packets received from the cloud experience little to no loss.If downLoss is 30%, 30% of the audio and video data packets transmitted from the cloud to the SDK will be lost in the transmission link. |
| gatewayRtt | Round-trip latency from the SDK to the local router. Unit: ms. This value represents the total duration for a network packet to travel from the SDK to the local router gateway and back again, that is, the complete cycle of "SDK > gateway > SDK."The smaller the value, the better. A gatewayRtt value below 50 ms indicates low latency for audio and video calls, while a value above 200 ms indicates high latency for audio and video calls.When the network type is a cellular network, the value is invalid. |
| localArray | Local audio and video statistics.Since three audio and video streams may be available locally (that is, the primary HD stream, secondary low-resolution stream, and substream), the local audio and video statistics are provided as an array. |
| receiveBytes | Total number of received bytes (including signaling data and audio and video data). Unit: byte. |
| remoteArray | Remote audio and video statistics.Since multiple remote users may be present simultaneously, and each of them may carry multiple audio and video streams (that is, a primary HD stream, a secondary low-resolution stream, and a substream), the remote audio and video statistics are provided as an array. |
| rtt | Round-trip latency from the SDK to the cloud. Unit: ms. This value represents the total duration for a network packet to travel from the SDK to the cloud and back again, that is, the complete cycle of "SDK > cloud > SDK."The smaller the value, the better. A rtt value below 50 ms indicates low latency for audio and video calls, while a value above 200 ms indicates high latency for audio and video calls.**Note:**rtt represents the total duration on the link of "SDK > cloud > SDK." Therefore, upRtt and downRtt do not need to be distinguished. |
| sendBytes | Total number of sent bytes (including signaling data and audio and video data). Unit: byte. |
| systemCpu | CPU utilization of the current system. Unit: %. Android 8.0 or later is not supported. |
| upLoss | Upstream packet loss rate from the SDK to the cloud. Unit: %.The smaller the value, the better. If upLoss is 0%, the upstream network quality is very good, and the data packets uploaded to the cloud experience little to no loss.If upLoss is 30%, 30% of the audio and video data packets sent from the SDK to the cloud will be lost in the transmission link. |

Android

iOS&Mac

Windows

```
@Overridepublic void onStatistics(TRTCStatistics statistics) {    super.onStatistics(statistics);    // appCpu is the application CPU utilization    Log.d(TAG, "appCpu:" + statistics.appCpu);    // systemCpu is the system CPU utilization    Log.d(TAG, "systemCpu:" + statistics.systemCpu);    // rtt is the round-trip latency from the SDK to the cloud    Log.d(TAG, "rtt:" + statistics.rtt);    // upLoss is the upstream packet loss rate    Log.d(TAG, "upLoss:" + statistics.upLoss);    // downLoss is the downstream packet loss rate    Log.d(TAG, "downLoss:" + statistics.downLoss);    // gatewayRtt is the round-trip latency from the gateway to the cloud    Log.d(TAG, "gatewayRtt:" + statistics.gatewayRtt);    // sendBytes is the number of sent bytes    Log.d(TAG, "sendBytes:" + statistics.sendBytes);    // receiveBytes is the number of received bytes    Log.d(TAG, "receiveBytes:" + statistics.receiveBytes);    if(statistics.localArray != null) {        for (int i = 0; i < statistics.localArray.size(); i++) {            // Local video width            Log.d(TAG, "localStatistics width:" + statistics.localArray.get(i).width);            // Local video height            Log.d(TAG, "localStatistics height:" + statistics.localArray.get(i).height);            // Local video frame rate            Log.d(TAG, "localStatistics frameRate:" + statistics.localArray.get(i).frameRate);            // Local video bitrate            Log.d(TAG, "localStatistics videoBitrate:" + statistics.localArray.get(i).videoBitrate);            // Local audio bitrate            Log.d(TAG, "localStatistics audioBitrate:" + statistics.localArray.get(i).audioBitrate);            // Capture status of the local audio device (used to monitor the health of audio peripherals). 0: capture device in normal status; 1: long-time silence detected; 2: audio clipping detected; 3: abnormal sound intermittency detected.            Log.d(TAG, "localStatistics audioCaptureState:" + statistics.localArray.get(i).audioCaptureState);            // Local audio sample rate            Log.d(TAG, "localStatistics audioSampleRate:" + statistics.localArray.get(i).audioSampleRate);            // Local stream type            Log.d(TAG, "localStatistics streamType:" + statistics.localArray.get(i).streamType);        }    }    if(statistics.remoteArray != null) {        for (int i = 0; i < statistics.remoteArray.size(); i++) {            // userid of the remote user            Log.d(TAG, "remoteStatistics userId:" + statistics.remoteArray.get(i).userId);            // Stream type of the remote user            Log.d(TAG, "remoteStatistics streamType:" + statistics.remoteArray.get(i).streamType);            // Remote video width            Log.d(TAG, "remoteStatistics width:" + statistics.remoteArray.get(i).width);            // Remote video height            Log.d(TAG, "remoteStatistics height:" + statistics.remoteArray.get(i).height);            // Remote video frame rate            Log.d(TAG, "remoteStatistics frameRate:" + statistics.remoteArray.get(i).frameRate);            // Remote video bitrate            Log.d(TAG, "remoteStatistics videoBitrate:" + statistics.remoteArray.get(i).videoBitrate);            // Remote video lag rate. Unit: %. Video playback lag rate (videoBlockRate) = Cumulative video playback lag duration (videoTotalBlockTime) / Total video playback duration.            Log.d(TAG, "remoteStatistics videoBlockRate:" + statistics.remoteArray.get(i).videoBlockRate);            // Cumulative lag duration of the video playback. Unit: ms.            Log.d(TAG, "remoteStatistics videoTotalBlockTime:" + statistics.remoteArray.get(i).videoTotalBlockTime);            // Total packet loss rate of the video stream            // videoPacketLoss represents the packet loss rate calculated at the audience end after the video stream goes through a complete transmission link of "anchor > cloud > audience."            // The smaller the videoPacketLoss value, the better. A packet loss rate of 0 means that all data of the video stream has fully arrived at the audience end.            // If downLoss == 0 but videoPacketLoss != 0, it means that the video stream experienced no packet loss on the cloud-to-audience link, but irreversible packet loss was detected on the anchor-to-cloud link.            Log.d(TAG, "remoteStatistics videoPacketLoss:" + statistics.remoteArray.get(i).videoPacketLoss);            // Remote audio bitrate            Log.d(TAG, "remoteStatistics audioBitrate:" + statistics.remoteArray.get(i).audioBitrate);            // Lag rate of the remote audio playback            Log.d(TAG, "remoteStatistics audioBlockRate:" + statistics.remoteArray.get(i).audioBlockRate);            // Remote audio sample rate            Log.d(TAG, "remoteStatistics audioSampleRate:" + statistics.remoteArray.get(i).audioSampleRate);            // Packet loss rate of the remote audio            Log.d(TAG, "remoteStatistics audioPacketLoss:" + statistics.remoteArray.get(i).audioPacketLoss);            // Cumulative lag duration of the audio playback            Log.d(TAG, "remoteStatistics audioTotalBlockTime:" + statistics.remoteArray.get(i).audioTotalBlockTime);            // Playback delay. The playback buffer, maintained by RTC Engine on the player side, organizes received network packets to prevent sound and image lags caused by network jitter and out-of-order network packets. The buffer size adjusts adaptively based on the current network quality. The buffer size, expressed as a time duration in milliseconds, is measured as the jitterBufferDelay.            Log.d(TAG, "remoteStatistics jitterBufferDelay:" + statistics.remoteArray.get(i).jitterBufferDelay);            // End-to-end delay. Unit: ms.            // point2PointDelay represents the delay in the link of "anchor => cloud => audience." More precisely, it represents the delay in the entire link of "capture => encoding => network transmission => reception => buffering => decoding => playback."            // point2PointDelay takes effect only when both the local and remote SDKs are version 8.5 or later. If the remote user is using a version earlier than 8.5, this value will remain 0, indicating no valid measurement.            Log.d(TAG, "remoteStatistics point2PointDelay:" + statistics.remoteArray.get(i).point2PointDelay);        }    }}
```

```
- (void)onStatistics:(TRTCStatistics *)statistics {    // appCpu is the application CPU utilization    NSLog(@"appCpu: %u", statistics.appCpu);        // systemCpu is the system CPU utilization    NSLog(@"systemCpu: %u", statistics.systemCpu);    // rtt is the round-trip latency from the SDK to the cloud    NSLog(@"rtt: %d", statistics.rtt);    // upLoss is the upstream packet loss rate    NSLog(@"upLoss: %u", statistics.upLoss);    // downLoss is the downstream packet loss rate    NSLog(@"downLoss: %u", statistics.downLoss);    // gatewayRtt is the round-trip latency from the gateway to the cloud    NSLog(@"gatewayRtt: %d", statistics.gatewayRtt);    // sendBytes is the number of sent bytes    NSLog(@"sendBytes: %llu", (unsigned long long)statistics.sentBytes);    // receiveBytes is the number of received bytes    NSLog(@"receiveBytes: %llu", (unsigned long long)statistics.receivedBytes);    if (statistics.localStatistics != nil) {        for (int i = 0; i < statistics.localStatistics.count; i++) {            // Local video width            NSLog(@"localStatistics width: %d", statistics.localStatistics[i].width);            // Local video height            NSLog(@"localStatistics height: %d", statistics.localStatistics[i].height);            // Local video frame rate            NSLog(@"localStatistics frameRate: %u", statistics.localStatistics[i].frameRate);            // Local video bitrate            NSLog(@"localStatistics videoBitrate: %d", statistics.localStatistics[i].videoBitrate);            // Local audio bitrate            NSLog(@"localStatistics audioBitrate: %d", statistics.localStatistics[i].audioBitrate);            // Capture status of the local audio device            NSLog(@"localStatistics audioCaptureState: %d", statistics.localStatistics[i].audioCaptureState);            // Local audio sample rate            NSLog(@"localStatistics audioSampleRate: %d", statistics.localStatistics[i].audioSampleRate);            // Local stream type            NSLog(@"localStatistics streamType: %ld", (long)statistics.localStatistics[i].streamType);        }    }    if (statistics.remoteStatistics != nil) {        for (int i = 0; i < statistics.remoteStatistics.count; i++) {            // userid of the remote user            NSLog(@"remoteStatistics userId: %@", statistics.remoteStatistics[i].userId);            // Stream type of the remote user            NSLog(@"remoteStatistics streamType: %ld", (long)statistics.remoteStatistics[i].streamType);            // Remote video width            NSLog(@"remoteStatistics width: %d", statistics.remoteStatistics[i].width);            // Remote video height            NSLog(@"remoteStatistics height: %d", statistics.remoteStatistics[i].height);            // Remote video frame rate            NSLog(@"remoteStatistics frameRate: %u", statistics.remoteStatistics[i].frameRate);            // Remote video bitrate            NSLog(@"remoteStatistics videoBitrate: %d", statistics.remoteStatistics[i].videoBitrate);            // Remote video lag rate            NSLog(@"remoteStatistics videoBlockRate: %u", statistics.remoteStatistics[i].videoBlockRate);            // Cumulative lag duration of the video playback            NSLog(@"remoteStatistics videoTotalBlockTime: %d", statistics.remoteStatistics[i].videoTotalBlockTime);            // Total packet loss rate of the video stream            NSLog(@"remoteStatistics videoPacketLoss: %u", statistics.remoteStatistics[i].videoPacketLoss);            // Remote audio bitrate            NSLog(@"remoteStatistics audioBitrate: %d", statistics.remoteStatistics[i].audioBitrate);            // Lag rate of the remote audio playback            NSLog(@"remoteStatistics audioBlockRate: %u", statistics.remoteStatistics[i].audioBlockRate);            // Remote audio sample rate            NSLog(@"remoteStatistics audioSampleRate: %d", statistics.remoteStatistics[i].audioSampleRate);            // Packet loss rate of the remote audio            NSLog(@"remoteStatistics audioPacketLoss: %u", statistics.remoteStatistics[i].audioPacketLoss);            // Cumulative lag duration of the audio playback            NSLog(@"remoteStatistics audioTotalBlockTime: %d", statistics.remoteStatistics[i].audioTotalBlockTime);            // Playback delay            NSLog(@"remoteStatistics jitterBufferDelay: %d", statistics.remoteStatistics[i].jitterBufferDelay);            // End-to-end delay            NSLog(@"remoteStatistics point2PointDelay: %d", statistics.remoteStatistics[i].point2PointDelay);        }    }}
```

```
void onStatistics(const TRTCStatistics& statistics) {	// appCpu is the application CPU utilization	printf("appCpu: %f\\n", statistics.appCpu);	// systemCpu is the system CPU utilization	printf("systemCpu: %f\\n", statistics.systemCpu);	// rtt is the round-trip latency from the SDK to the cloud	printf("rtt: %d\\n", statistics.rtt);	// upLoss is the upstream packet loss rate	printf("upLoss: %f\\n", statistics.upLoss);	// downLoss is the downstream packet loss rate	printf("downLoss: %f\\n", statistics.downLoss);	// gatewayRtt is the round-trip latency from the gateway to the cloud	printf("gatewayRtt: %d\\n", statistics.gatewayRtt);	// sentBytes is the number of sent bytes	printf("sentBytes: %lld\\n", statistics.sentBytes); 	// receiveBytes is the number of received bytes	printf("receivedBytes: %lld\\n", statistics.receivedBytes);	//for (const auto& localStat : statistics.localStatisticsArray) {	if (statistics.localStatisticsArray != nullptr && statistics.localStatisticsArraySize != 0)	{		for (int i = 0; i < statistics.localStatisticsArraySize; i++)		{			// Local video width			printf("localStatistics width: %d\\n", statistics.localStatisticsArray[i].width);			// Local video height			printf("localStatistics height: %d\\n", statistics.localStatisticsArray[i].height);			// Local video frame rate			printf("localStatistics frameRate: %f\\n", statistics.localStatisticsArray[i].frameRate);			// Local video bitrate			printf("localStatistics videoBitrate: %d\\n", statistics.localStatisticsArray[i].videoBitrate);			// Local audio bitrate			printf("localStatistics audioBitrate: %d\\n", statistics.localStatisticsArray[i].audioBitrate);			// Capture status of the local audio device			printf("localStatistics audioCaptureState: %d\\n", statistics.localStatisticsArray[i].audioCaptureState);			// Local audio sample rate			printf("localStatistics audioSampleRate: %d\\n", statistics.localStatisticsArray[i].audioSampleRate);			// Local stream type			printf("localStatistics streamType: %d\\n", statistics.localStatisticsArray[i].streamType);		}	}	//for (const auto& remoteStat : statistics.remoteStatisticsArray) {	if (statistics.remoteStatisticsArray != nullptr && statistics.remoteStatisticsArraySize != 0)	{		for (int i = 0; i < statistics.remoteStatisticsArraySize; i++)		{			// userid of the remote user			printf("remoteStatistics userId: %s\\n", statistics.remoteStatisticsArray[i].userId);			// Stream type of the remote user			printf("remoteStatistics streamType: %d\\n", statistics.remoteStatisticsArray[i].streamType);			// Remote video width			printf("remoteStatistics width: %d\\n", statistics.remoteStatisticsArray[i].width);			// Remote video height			printf("remoteStatistics height: %d\\n", statistics.remoteStatisticsArray[i].height);			// Remote video frame rate			printf("remoteStatistics frameRate: %f\\n", statistics.remoteStatisticsArray[i].frameRate);			// Remote video bitrate			printf("remoteStatistics videoBitrate: %d\\n", statistics.remoteStatisticsArray[i].videoBitrate);			// Remote video lag rate			printf("remoteStatistics videoBlockRate: %f\\n", statistics.remoteStatisticsArray[i].videoBlockRate);			// Cumulative lag duration of the video playback			printf("remoteStatistics videoTotalBlockTime: %d\\n", statistics.remoteStatisticsArray[i].videoTotalBlockTime);			// Total packet loss rate of the video stream			printf("remoteStatistics videoPacketLoss: %f\\n", statistics.remoteStatisticsArray[i].videoPacketLoss);			// Remote audio bitrate			printf("remoteStatistics audioBitrate: %d\\n", statistics.remoteStatisticsArray[i].audioBitrate);			// Lag rate of the remote audio playback			printf("remoteStatistics audioBlockRate: %f\\n", statistics.remoteStatisticsArray[i].audioBlockRate);			// Remote audio sample rate			printf("remoteStatistics audioSampleRate: %d\\n", statistics.remoteStatisticsArray[i].audioSampleRate);			// Packet loss rate of the remote audio			printf("remoteStatistics audioPacketLoss: %f\\n", statistics.remoteStatisticsArray[i].audioPacketLoss);			// Cumulative lag duration of the audio playback			printf("remoteStatistics audioTotalBlockTime: %d\\n", statistics.remoteStatisticsArray[i].audioTotalBlockTime);			// Playback delay			printf("remoteStatistics jitterBufferDelay: %d\\n", statistics.remoteStatisticsArray[i].jitterBufferDelay);			// End-to-end delay			printf("remoteStatistics point2PointDelay: %d\\n", statistics.remoteStatisticsArray[i].point2PointDelay);		}	}}
```

## Monitoring Connections During Calls

During a call, users need to stay aware of both network fluctuations and the connection status between the SDK and the backend. This allows users to better assess whether the current network adjustments have been completed and if the call can continue normally.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/21ade88e966611efaaca525400fdb830.png)

| Callback API | Description |
| --- | --- |
| onConnectionLost | The SDK has been disconnected from the cloud. |
| onTryToReconnect | The SDK is trying to connect to the cloud again. |
| onConnectionRecovery | The connection between the SDK and the cloud has been recovered. |

### Disconnection and Reconnection Logic

The SDK supports automatic reconnection when a user disconnects (if the reconnection fails for 30 minutes, the user will automatically exit the room, and the error code -3301 will be returned). The specific connection status and handling logic during the connection process are described below. The following diagram shows the listening callback events received from the moment Userid1 joins the channel, through disconnection, to rejoining the room:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/19aa417ebea611f0a5e052540099c741.png)

Detailed instructions:

- T1: The user initiates a call to the `enterRoom` API to trigger a room entry request.
- T2: Userid1 receives the `onEnterRoom` callback. Userid2 becomes aware of the presence of Userid1 with a delay of approximately 300 ms before receiving the `onRemoteUserEnterRoom` callback.
- T3: The Userid1 client disconnects due to a network issue. The SDK will attempt to join the room again.
- T4: If Userid1 does not connect successfully to the server for **8 consecutive seconds**, Userid1 will receive the `onConnectionLost` disconnection callback.
- T5: If Userid1 still fails to connect to the server for **another 3 seconds**, Userid1 receives the `onTryToReconnect` retry callback.
- T6: Userid1 receives the `onTryToReconnect` retry callback **every 24 seconds**.
- T7: Userid2 will receive the `onRemoteUserLeaveRoom` callback once the SDK detects that the remote user Userid1 has disconnected 90 seconds after Userid2 receives the Userid1 disconnection notification.
- T8: If Userid1 reconnects successfully at any moment during the disconnection period, Userid1 receives the `onConnectionRecovery` recovery callback.

Android

iOS&Mac

Windows

```
@Overridepublic void onConnectionLost() {    // Connection lost    Log.d(TAG, "onConnectionLost");}@Overridepublic void onTryToReconnect() {    // Attempt to reconnect    Log.d(TAG, "onTryToReconnect");}@Overridepublic void onConnectionRecovery() {    // Reconnect successfully    Log.d(TAG, "onConnectionRecovery");}
```

```
- (void)onConnectionLost {    // Connection lost    NSLog(@"onConnectionLost");}- (void)onTryToReconnect {    // Attempt to reconnect    NSLog(@"onTryToReconnect");}- (void)onConnectionRecovery {    // Reconnect successfully    NSLog(@"onConnectionRecovery");}
```

```
void onConnectionLost() {    // Connection lost    printf("onConnectionLost\\n");}void onTryToReconnect() {    // Attempt to reconnect    printf("onTryToReconnect\\n");}void onConnectionRecovery() {    // Reconnect successfully    printf("onConnectionRecovery\\n");}
```


---
*Source: [https://trtc.io/document/74575](https://trtc.io/document/74575)*
