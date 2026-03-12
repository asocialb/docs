# FAQs

## Ear Monitor-related Issues

### In Karaoke scenarios, ear monitoring is likely to be used. How can I enable the ear monitoring function?

```
mTRTCCloud.getAudioEffectManager().enableVoiceEarMonitor(true)
```

### What if there is no effect after enabling the ear monitoring function?

Due to the high hardware latency of Bluetooth headsets, please try to prompt the host to wear wired headphones on the user interface. At the same time, please note that not all phones can achieve excellent ear monitoring effects after enabling this feature. The TRTC SDK has already blocked this effect on some phones with poor ear monitoring performance.

### Is the ear monitoring latency too high?

Please check if you are using a Bluetooth headset. Due to the high hardware latency of Bluetooth headsets, please try to use wired headphones as much as possible.

In addition, you can try to improve the high latency of ear monitoring by enabling hardware ear monitoring through the experimental interface setSystemAudioKitEnabled. Currently, for Huawei and Vivo devices, the SDK uses hardware ear monitoring by default, while other devices use software ear monitoring by default.

```
// Enable hardware ear monitoringmTRTCCloud.callExperimentalAPI("{\\"api\\":\\"setSystemAudioKitEnabled\\", \\"params\\": {\\"enable\\":1}}");
```

## NTP Time Synchronization Issues

### Reminder: **âNTP time sync finished, but result maybe inaccurateâï¼**

NTP time synchronization is successful, but the deviation may be more than 30ms, reflecting poor client network environment and continuous rtt jitter.

### Reminder: **âError in AddressResolver: No address associated with hostnameâï¼**

NTP time synchronization failure may be due to temporary anomalies in the local carrier DNS resolution under the current network environment. Please try again later.

### NTP service retry processing logic?

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9bceefc85c4b11ee9ff8525400d917da.png)

## Network Speed Test Recommendations

Online Karaoke scenarios have high network requirements for users, especially real-time chorus. A high-quality and stable network environment is necessary for a good Karaoke experience. Therefore, it is recommended to perform a network speed test on the user before entering the room, and give a UI layer reminder to users who do not meet the network requirements, prohibiting them from joining the Karaoke room or participating in chorus.

Initiating network speed test with TRTC SDK:

```
TRTCCloudDef.TRTCSpeedTestParams speedTestParams = new TRTCCloudDef.TRTCSpeedTestParams();speedTestParams.sdkAppId = SDK_APP_ID;speedTestParams.userId = userId;speedTestParams.userSig = userSig;// If the actual bandwidth is higher than the expected value, the test result is the expected value;// if the actual bandwidth is lower than the expected value, the test result is the actual bandwidth value.speedTestParams.expectedDownBandwidth = 3000; // Expected downstream bandwidth, ranging from 10 to 5000 kbpsspeedTestParams.expectedUpBandwidth = 3000; // Expected upstream bandwidth, ranging from 10 to 5000 kbpsmTRTCCloud.startSpeedTest(speedTestParams);
```

> **Note:**Expected upstream bandwidth, ranging from 10 to 5000 kbpsPlease perform the network speed test before entering the room. Network speed testing in the room will affect the normal audio and video transmission effects, and due to too much interference, the network speed test results will also be inaccurate.

TRTC SDK network speed test result callback:

```
@Overridepublic void onSpeedTestResult(TRTCCloudDef.TRTCSpeedTestResult result) {    String tquality = "Unknown";    switch (result.quality) {        case 0:            tquality = "Unknown";            break;        case 1:            tquality = "The current network is very good";            break;        case 2:            tquality = "The current network is good";            break;        case 3:            tquality = "The current network is average";            break;        case 4:            tquality = "The current network is poor";            break;        case 5:            tquality = "The current network is very poor";            break;        case 6:            tquality = "The current network does not meet TRTC's minimum requirements";            break;    }    if (result.success) {        mTextTestResult.append("Speed test successful!" + "\\n");        mTextTestResult.append("IP address: " + result.ip + "\\n");        mTextTestResult.append("Uplink packet loss rate: " + result.upLostRate + "\\n");        mTextTestResult.append("Downlink packet loss rate: " + result.downLostRate + "\\n");        mTextTestResult.append("Network latency: " + result.rtt + "ms\\n");        mTextTestResult.append("Downlink bandwidth: " + result.availableDownBandwidth + "kbps\\n");        mTextTestResult.append("Uplink bandwidth: " + result.availableUpBandwidth + "kbps\\n");        mTextTestResult.append("Network quality: " + tquality + "\\n");    } else {        mTextTestResult.append("Speed test failed!" + "\\n");        mTextTestResult.append("Error message: " + result.errMsg + "\\n");    }}
```

## Joining a Chorus Midway

The real-time chorus solution theoretically has no limit on the number of chorus participants, supporting multiple people to participate in the chorus simultaneously, as well as joining the chorus midway.

The following are the key actions for joining a chorus midway:

- NTP time synchronization
- Enable chorus experimental interface
- Enter the room and start streaming on the microphone
- Receive chorus signaling, obtain accompaniment resources and chorus agreed time
- Calculate the difference between the agreed time and the current time, preload and seek accompaniment
- Start participating in the chorus and synchronize accompaniment progress and lyrics progress in real-time

For the specific implementation process and code implementation of the above key actions, please refer to the documentation on[song synchronization](https://www.tencentcloud.com/zh/document/product/647/57026), [lyrics synchronization](https://www.tencentcloud.com/zh/document/product/647/57028), [vocal synchronization](https://www.tencentcloud.com/zh/document/product/647/57033).


---
*Source: [https://trtc.io/document/57039](https://trtc.io/document/57039)*
