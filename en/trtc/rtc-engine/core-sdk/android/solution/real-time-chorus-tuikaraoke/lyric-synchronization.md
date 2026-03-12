# Lyric Synchronization

## Implementation process

In the lyrics synchronization scheme, the actions of three different roles are as follows:

| Lead Singer | Chorus | Audience |
| --- | --- | --- |
| NTP time calibrationTurn on black frame compensationSend SEI messageLocal lyrics synchronizationUpdate lyrics widget | NTP time calibrationLocal lyrics synchronizationUpdate lyrics widget | NTP time calibrationReceive SEI messageUpdate lyrics widget |

The lead singer and chorus update the lyrics progress locally according to the synchronized song playback progress; the audience needs to receive the SEI message sent by the lead singer, which contains the latest lyrics progress, to update the local lyrics progress.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7895bd885ce211ee9ff8525400d917da.png)

## Timing diagram

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/78a659b75ce211ee974d5254005f490f.png)

The lyrics synchronization timing can be mainly divided into three parts: NTP time calibration, turning on black frame compensation, and local and remote lyrics synchronization. The code implementation of NTP time calibration has been given in the [song synchronization](https://www.tencentcloud.com/document/product/647/57026), and the specific code implementation for the latter two parts will be provided below.

## Key code implementation

### **1.**Turn on black frame compensation

```
// In pure audio mode, the main instance (vocal instance) needs to turn on black frame compensation to carry the SEI message.mTRTCCloud.callExperimentalAPI("{\\"api\\":\\"enableBlackStream\\",\\"params\\": {\\"enable\\":true}}");
```

> **Note:**The experimental interface enableBlackStream needs to be called after entering the room.On Android, the value type of the enable parameter is boolean, and on iOS, it is integer.The receiver needs to call startRemoteView(userId, null) when onUserVideoAvailable(userId, true) is received.

### **2.**Send song progress through SEI message

```
mAudioEffectManager.setMusicObserver(mCurPlayMusicId, new TXAudioEffectManager.TXMusicPlayObserver() {    @Override    public void onPlayProgress(int id, long curPtsMS, long durationMS) {        JSONObject jsonObject = new JSONObject();        // Current NTP time        long ntpTime = TXLiveBase.getNetworkTimestamp();        jsonObject.put("bgmProgressTime", curTime);        jsonObject.put("ntpTime", ntpTime);        jsonObject.put("musicId", musicId);        jsonObject.put("duration", duration);        jsonObject.toString().getBytes();        mTRTCCloud.sendSEIMsg(jsonObject.toString().getBytes(), 1);    }}
```

> **Note:**The frequency of the lead singer sending SEI messages is determined by the frequency of background music playback event callbacks, usually 200ms;The reason for **not directly using CMD messages to send song progress**: The signaling transmitted by the SEI channel can be transmitted to the live CDN along with the video frames, providing better compatibility for the audience pulling the CDN stream.

### **3.**Local and remote lyrics synchronization

```
// Local lyrics synchronizationmAudioEffectManager.setMusicObserver(mCurPlayMusicId, new TXAudioEffectManager.TXMusicPlayObserver() {    @Override    public void onPlayProgress(int id, long curPtsMS, long durationMS) {        ...        // TODO Update lyrics widget logic:        // Determine whether to seek the lyrics widget based on the latest progress and local lyrics progress error        ...    }}// Remote lyrics synchronization@Overridepublic void onRecvSEIMsg(String userId, byte[] data) {    String result = new String(data);    JSONObject jsonObject = new JSONObject(result);    long bgmProgressTime = jsonObject.getLong("bgmProgressTime");    long ntpTime = jsonObject.getLong("ntpTime");    String musicId = jsonObject.getString("musicId");    long duration = jsonObject.getLong("duration");    ...    // TODO Update lyrics widget logic:    // If you reuse the TUIKaraoke component's lyrics widget,     //please refer to the code logic of the TUIKaraoke LyricsView section to synchronize the lyrics widget progress.    ...}
```

> **Note:**If you reuse the TUIKaraoke component's lyrics widget, please refer to the code logic of the [TUIKaraoke LyricsView](https://github.com/tencentyun/TUIKaraoke/blob/main/Android/tuikaraoke/src/main/java/com/tencent/liteav/tuikaraoke/ui/lyric/LyricView.java) section to synchronize the lyrics widget progress.


---
*Source: [https://trtc.io/document/57029](https://trtc.io/document/57029)*
