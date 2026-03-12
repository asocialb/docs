# Song Synchronization

Real-time synchronization of song progress is required in the real-time solution to avoid increasing end-to-end delay due to song errors after the start of the performance. Synchronizing the song requires using NTP time, as the local clocks of different devices are not consistent and have some error. Therefore, Tencent Cloud's self-developed NTP service needs to be introduced. In addition, users who join the chorus midway also need to synchronize the song progress before they can participate in the chorus.

## Implementation process

The practice of song synchronization is as follows: The lead singer user agrees to start playing the song at a certain point in the future (e.g., after a delay of N seconds), and other users participate in the chorus. The time of each end is based on NTP time, which will be synchronized after TRTC SDK initialization.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0dc790fb5b7411ee974d5254005f490f.png)

The specific process is as follows:

1. Each end performs NTP calibration, updates and obtains the latest NTP time T from the TRTC cloud.
2. The lead singer sends a chorus signaling (custom message), agreeing on the start time T2 for the chorus.
3. The local end preloads the song according to T2 and plays it on schedule.
4. Other chorus users perform step 3 after receiving the chorus signaling.
5. During the process, the local song playback progress is checked, and when the difference between TE and TC exceeds 50ms, seek calibration is performed.

> **Note:**The 50ms error mentioned here is a typical value, and can be adjusted according to the tolerance of the business. It is recommended to fluctuate around 50ms.

## Timing diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3ffc0e8b5c1b11ee94c3525400d793d0.png)

The song synchronization timing can be mainly divided into three parts: NTP calibration, sending and receiving chorus signaling, and song playback progress correction. The specific code implementation for these three parts will be provided below.

## Key code implementation

### **1.**NTP calibration service

```
TXLiveBase.setListener(new TXLiveBaseListener() {    @Override    public void onUpdateNetworkTime(int errCode, String errMsg) {        super.onUpdateNetworkTime(errCode, errMsg);        // errCode 0: Calibration is successful and the deviation is within 30ms;        //         1: Calibration is successful, but the deviation may be more than 30ms;        //         -1: Calibration failed.        if (errCode == 0) {            // Call getNetworkTimestamp of TXLivebase to get the NTP timestamp.            long ntpTime = TXLiveBase.getNetworkTimestamp();        } else {            // Call updateNetworkTime again to start a calibration.            TXLiveBase.updateNetworkTime();        }    }});TXLiveBase.updateNetworkTime();
```

### **2.**Lead singer sends chorus signaling

```
JSONObject jsonObject = new JSONObject();jsonObject.put("cmd", "startChorus");// Agree on a time for the chorus.jsonObject.put("startPlayMusicTS", startTs);jsonObject.put("musicId", "musicId");String body = jsonObject.toString();mTRTCCloud.sendCustomCmdMsg(0, body.getBytes(), false, false);
```

> **Note:**It is recommended that the lead singer sends chorus signaling messages to the room at a fixed time interval, so that the chorus users can join the chorus midway.Reason for **not using SEI messages to send chorus signaling:**SEI information will be inserted into the video frame, causing the video stream pulled by the audience side to carry a lot of invalid information.

### **3.**Chorus end receives chorus signaling

```
public void onRecvCustomCmdMsg(String userId, int cmdID, int seq, byte[] message) {    JSONObject json = new JSONObject(new String(message, "UTF-8"));    String cmd = json.getString("cmd");    // Chorus command    if (cmd.equals("startChorus")) {    // Chorus start time    long startPlayMusicTs = json.getLong("startPlayMusicTS");    int musicId = json.getInt("musicId");    // The difference between the agreed chorus time and the current time    long delayMs = Math.abs(startPlayMusicTs - getNtpTime());    // Start preloading, and jump the song progress according to the agreed chorus time and the current NTP difference.    mTRTCCloud.callExperimentalAPI("{\\"api\\":\\"preloadMusic\\",\\"params\\": {\\"musicId\\":musicId,\\"path\\":\\"path\\",\\"startTimeMS\\":delayMs}}");    // Play the song    TXAudioEffectManager.AudioMusicParam param = new TXAudioEffectManager.AudioMusicParam(musicId, musicPath);    param.publish = false;    mTRTCCloud.getAudioEffectManager().startPlayMusic(param);}
```

> **Note:**After the chorus end receives the first startChorus signaling, the status should change from "not in chorus" to "in chorus", and no longer respond to startChorus signaling to avoid restarting BGM playback.

### **4.**Song playback progress correction

```
long mStartPlayMusicTs = "The initially agreed chorus time"ï¼long currentProgress = subCloud.getAudioEffectManager().getMusicCurrentPosInMS(musicID);// The ideal playback progress of the current songlong estimatedProgress = getNtpTime() - mStartPlayMusicTs;// When the playback progress exceeds 50ms, make correctionsif (estimatedProgress >= 0 &&; Math.abs(currentProgress - estimatedProgress) > 50) {    subCloud.getAudioEffectManager().seekMusicToPosInMS(mMusicID, (int) estimatedProgress);}
```


---
*Source: [https://trtc.io/document/57026](https://trtc.io/document/57026)*
