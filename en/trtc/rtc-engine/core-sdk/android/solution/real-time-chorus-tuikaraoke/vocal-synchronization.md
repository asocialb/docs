# Vocal Synchronization

## Introduction to vocal and song synchronization

Due to the jitter buffer of local vocal collection, the jitter buffer of song playback mixing, and the certain GAP between sound playback to the human ear and singing, when the singer sings along with the lyrics and BGM, the remote audience feels that there is a certain delay in the BGM playback, vocals, and lyrics. The chorus scheme uses low-latency AAudio collection inside the TRTC SDK. Specifically, you only need to enable the chorus mode and low-latency mode after entering the room.

## Specific code implementation

### Enable chorus mode

```
// The main instance (vocal instance) enables chorus mode (reducing buffer interval and audio redundancy protection)mTRTCCloud.callExperimentalAPI("{\\"api\\":\\"enableChorus\\",\\"params\\":{\\"enable\\":1,\\"audioSource\\":0}}");// The sub-instance (accompaniment instance) enables chorus mode (reducing buffer interval and audio redundancy protection)subCloud.callExperimentalAPI("{\\"api\\":\\"enableChorus\\",\\"params\\":{\\"enable\\":1,\\"audioSource\\":1}}");
```

> **Note:**Parameter settings for the experimental interface enableChorus to enable chorus mode:audioSourceï¼0(vocals).audioSourceï¼1Â (accompaniment).

### Enable low-latency mode (high-performance audio AAudio)

```
// The main instance (vocal instance) enables high-performance audio AAudiomTRTCCloud.callExperimentalAPI("{\\"api\\":\\"setLowLatencyModeEnabled\\",\\"params\\":{\\"enable\\":1}}");// The sub-instance (accompaniment instance) enables high-performance audio AAudiosubCloud.callExperimentalAPI("{\\"api\\":\\"setLowLatencyModeEnabled\\",\\"params\\":{\\"enable\\":1}}");
```


---
*Source: [https://trtc.io/document/57033](https://trtc.io/document/57033)*
