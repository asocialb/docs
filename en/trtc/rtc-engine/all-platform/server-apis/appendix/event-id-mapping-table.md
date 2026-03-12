# Event ID Mapping Table

### SDK Event Mapping Table

| Event ID | First Parameter Value | Second Parameter Value | Specific Event |
| --- | --- | --- | --- |
| 1001 | 0 | -1 | The user unplugged wired earphone |
| 1001 | 1 | -1 | The user plugged wired earphone |
| 1002 | 0 | -1 | The earphone has disconnected from Bluetooth connection |
| 1002 | 1 | -1 | The earphone initiated a Bluetooth connection |
| 1003 | 0 | -1 | The user has disconnected from the network |
| 1003 | 1 | -1 | The user is using Wi-Fi network |
| 1003 | 2 | -1 | The user is using 4G network |
| 1003 | 3 | -1 | The user is using 3G network |
| 1003 | 4 | -1 | The user is using 2G network |
| 1003 | 5 | -1 | The user is using wired network |
| 2001 | 0 | -1 | The application has been switched to run in the foreground |
| 2001 | 1 | -1 | The application has been switched to run in the background |
| 2002 | 1 | -1 | The application does not have network access |
| 2002 | 2 | -1 | The application does not have permission to read local file |
| 2002 | 3 | -1 | The application does not have permission to write local file |
| 2002 | 4 | -1 | The application does not have permission to record audio |
| 2002 | 5 | -1 | The application does not have permission to use camera |
| 3001 | 0 | -1 | The mic started capturing audio |
| 3001 | 1 | -1 | Muted |
| 3001 | 2 | -1 | Mic capturing was disabled |
| 3001 | 3 | -1 | Unmuted |
| 3002 | 0 | -1 | Canceled mute playback |
| 3002 | 1 | -1 | Mute playback mode |
| 3003 | 10 | -1 | Audio codec: aac |
| 3003 | 11 | -1 | Audio codec: opus |
| 3004 | 0 | -1 | Speaker |
| 3004 | 1 | -1 | Receiver |
| 4001 | 0 | -1 | Enabled front camera successfully |
| 4001 | 1 | -1 | Enabled rear camera successfully |
| 4002 | 0 | -1 | Failed to enable front camera |
| 4002 | 1 | -1 | Failed to enable rear camera |
| 4003 | Resolution width | Resolution height | Video resolution has been switched |
| 4004 | 0 | -1 | Switched software encoding mode (SW) |
| 4004 | 1 | -1 | Switched to hardware encoding mode (HW) |
| 4005 | 0 | -1 | Switched software decoding mode (SW) |
| 4005 | 1 | -1 | Switched to hardware decoding mode (HW) |
| 4006 | 0 | -1 | The user enabled video upstreaming |
| 4006 | 1 | -1 | The user disabled video upstreaming |
| 4007 | Resolution width | Resolution height | The user switched video resolution |
| 4008 | Video frame rate | -1 | The user switched video frame rate |
| 4009 | Video bitrate | -1 | The user switched video bitrate |
| 4010 | 1 | -1 | RPS (reference picture selection) was disabled due to insufficient performance or poor network |
| 4011 | -1 | -1 | Failed to start hardware decoder |
| 4012 | -1 | -1 | Switched to software decoder as there is too much hardware decoder buffer |
| 4013 | Number of frames failed to be decoded (3s) | 0 | (Software) decoding failed |
| 4013 | Number of frames failed to be decoded (3s) | 1 | (Hardware) decoding failed |
| 4014 | 0 | -1 | The playback client enabled remote image |
| 4014 | 1 | -1 | The playback client disabled remote image |
| 4015 | 0 | -1 | The primary video stream was unsubscribed from |
| 4015 | 1 | -1 | The primary video stream was subscribed to |
| 5001 | -1 | -1 | Started entering room |
| 5002 | 0 | -1 | Failed to obtain IP address info |
| 5002 | 1 | -1 | Obtained IP address info successfully |
| 5003 | 0 | -1 | Failed to enter room |
| 5003 | 1 | -1 | Entered room successfully |
| 5004 | -1 | -1 | Started sending video data to the cloud |
| 5005 | -1 | -1 | Connection to CVM timed out |
| 5006 | -1 | -1 | The first video packet was received |
| 5007 | -1 | -1 | Started playing the first video frame |
| 5008 | 0 | -1 | Failed to exit room |
| 5008 | 1 | -1 | Exited room successfully |
| 5009 | -1 | -1 | Sent first audio frame |
| 6001 | 1 | 0 | (Qos: local mode - smoothness preferred) video call |
| 6001 | 1 | 1 | (Qos: local mode - smoothness preferred) live streaming |
| 6001 | 1 | 2 | (Qos: local mode - smoothness preferred) audio call |
| 6001 | 1 | 3 | (Qos: local mode - smoothness preferred) voice chat room |
| 6001 | 2 | 0 | (Qos: local mode - definition preferred) video call |
| 6001 | 2 | 1 | (Qos: local mode - definition preferred) live streaming |
| 6001 | 2 | 2 | (Qos: local mode - definition preferred) audio call |
| 6001 | 2 | 3 | (Qos: local mode - definition preferred) voice chat room |
| 6001 | 101 | 0 | (Qos: cloud control mode - smoothness preferred) video call |
| 6001 | 101 | 1 | (Qos: cloud control mode - smoothness preferred) live streaming |
| 6001 | 101 | 2 | (Qos: cloud control mode - smoothness preferred) audio call |
| 6001 | 101 | 3 | (Qos: cloud control mode - smoothness preferred) voice chat room |
| 6001 | 102 | 0 | (Qos: cloud control mode - definition preferred) video call |
| 6001 | 102 | 1 | (Qos: cloud control mode - definition preferred) live streaming |
| 6001 | 102 | 2 | (Qos: cloud control mode - definition preferred) audio call |
| 6001 | 102 | 3 | (Qos: cloud control mode - definition preferred) voice chat room |
| 7000 | 0 | -1 | Entered room normally |
| 7000 | 1 | -1 | Entered room again |
| 7001 | 0 | -1 | Exited room normally |
| 7001 | 1 | -1 | Timed out |
| 7001 | 2 | -1 | Kicked out |

### WebRTC Event Mapping Table

| Event ID | First Parameter Value | Second Parameter Value | Specific Event |
| --- | --- | --- | --- |
| 36864 | -1 | -1 | Signaling channel has disconnected, which is reported by the backend |
| 32768 | -1 | -1 | Enabled video |
| 32769 | -1 | -1 | Enabled audio |
| 32770 | -1 | -1 | Disabled video |
| 32771 | -1 | -1 | Disabled audio |
| 32772 | -1 | -1 | Disabled audio (still send mute packets) |
| 32773 | -1 | -1 | Disabled video (still send black screen packets) |
| 32774 | -1 | -1 | Enabled audio |
| 32775 | -1 | -1 | Enabled video |
| 32776 | -1 | -1 | Subscribed to video |
| 32777 | -1 | -1 | Subscribed to audio |
| 32778 | -1 | -1 | Unsubscribed from video |
| 32779 | -1 | -1 | Unsubscribed from audio |
| 32780 | -1 | -1 | Switched camera |
| 32781 | -1 | -1 | Switched mic |
| 32782 | -1 | -1 | Updated video |
| 32783 | -1 | -1 | Updated audio |
| 32784 | -1 | -1 | Disabled remote video |
| 32785 | -1 | -1 | Disabled remote audio |
| 32786 | -1 | -1 | Enabled remote video |
| 32787 | -1 | -1 | Enabled remote audio |
| 32788 | -1 | -1 | Entered room |
| 32789 | -1 | -1 | Exited room |
| 32790 | -1 | -1 | Signaling channel has disconnected |
| 32791 | -1 | -1 | Connected signaling channel successfully |
| 32792 | -1 | -1 | Media transmission channel has disconnected |
| 32793 | -1 | -1 | Connected media transmission channel successfully |

### Exceptional Experience ID Mapping Table

| Experience ID | Description |
| --- | --- |
| 1 | Room entry was slow |
| 2 | Unable to enable video |
| 3 | Unable to enable audio |
| 4 | Video lagged |
| 5 | Audio lagged |

### Exceptional Room Dismissal Event ID Mapping Table

Note: events in this table are reported after the room is dismissed; therefore, the events can be queried only after the room is dismissed.

| Exceptional Event ID | Description |
| --- | --- |
| 1001 | Failed to initialize audio device |
| 1002 | Failed to initialize video device |
| 1003 | Failed to request token |
| 1004 | Failed to request access server |
| 1005 | Failed to enter room |
| 1006 | Room entry eventually failed (including failures in any stage, such as SDK verification failure) |
| 1007 | The user IP changed, and the IP in the signaling stage was different from that in the data stage |
| 1008 | Empty room entry parameter. Please check whether valid parameters were passed into the `enterRoom:appScene:` API when it was called |
| 1009 | Incorrect room entry parameter `sdkAppId` |
| 1010 | Incorrect room entry parameter `RoomId` |
| 1011 | Incorrect room entry parameter `UserID` |
| 1012 | Incorrect room entry parameter `UserSig` |
| 1013 | The room entry request timed out. Please check the network |
| 1014 | Unavailable service. Please check whether the remained validity period in minutes in the package is greater than 0 and whether the Tencent Cloud account is in arrears |
| 1015 | Failed to enable the camera; for example, the configuration program (driver) of the camera on Windows or macOS was exceptional. In this case, please try to disable and then enable the camera again, restart the device, or update the configuration program |
| 1016 | The camera permission is not granted. This error usually occurs on mobile devices and may be caused by permission denial by user |
| 1017 | Incorrect camera parameter settings (unsupported value or other causes) |
| 1018 | The camera is being used. Please try to enable another camera |
| 1019 | Failed to enable the mic; for example, the configuration program (driver) of the mic on Windows or macOS was exceptional. In this case, please try to disable and then enable the mic again, restart the device, or update the configuration program |
| 1020 | The mic permission is not granted. This error usually occurs on mobile devices and may be caused by permission denial by user |
| 1021 | Failed to set mic parameters |
| 1022 | The mic is being used. For example, if the mobile device is on a call, the mic will fail to be enabled |
| 1023 | Failed to enable the speaker; for example, the configuration program (driver) of the speaker on Windows or macOS was exceptional. In this case, please try to disable and then enable the speaker again, restart the device, or update the configuration program |
| 1024 | Failed to start screen sharing. If this error occurs on a mobile device, it may be caused by permission denial by user; if on Windows or macOS, please check whether parameters of the screen sharing API meet the requirements |
| 1025 | Screen sharing failed. Please use Android 5.0 or above if the device is on Android or use iOS 11.0 or above if the device is on iOS |
| 1026 | No permission to upstream substream |
| 1027 | Another user is upstreaming substream |
| 1028 | Screen sharing was stopped by the system |
| 1029 | Failed to encode video frames; for example, when a user switches from an iOS device to another device, the hardware encoder may be released by the system; and after the user switches back, this error may be thrown before the hardware encoder is restarted |
| 1030 | Unsupported video resolution |
| 1031 | Failed to encode audio frames; for example, the SDK could not process the custom audio data passed in |
| 1032 | Unsupported audio sample rate |

### Real-Time Exceptional Event ID Mapping Table

Note: as it takes time to collect statistics, there may be a delay of less than 5 minutes.

| Exceptional Event ID | Description |
| --- | --- |
| 2001 | The system CPU utilization was too high |
| 2002 | The application CPU utilization was too high |
| 2003 | The upstream network latency was too high |
| 2004 | The upstream network jitter was too high |
| 2005 | The packet loss rate of upstream audio was too high |
| 2006 | The volume level of audio capturing was 0 |
| 2007 | The packet loss rate of upstream big image was too high |
| 2008 | The packet loss rate of upstream small image was too high |
| 2009 | The packet loss rate of upstream substream image was too high |
| 2010 | The FPS capturing of upstream big image was exceptional |
| 2011 | The FPS capturing of upstream small image was exceptional |
| 2012 | The FPS capturing of upstream substream image was exceptional |
| 2013 | The downstream network latency was too high |
| 2014 | The downstream network jitter was too high |
| 2015 | The packet loss rate of downstream audio was too high |
| 2016 | The volume level of audio playback was 0 |
| 2017 | The packet loss rate of downstream big image was too high |
| 2018 | The packet loss rate of downstream small image was too high |
| 2019 | The packet loss rate of downstream substream image was too high |
| 2020 | The FPS rendering of downstream big image was exceptional |
| 2021 | The FPS rendering of downstream small image was exceptional |
| 2022 | The FPS rendering of downstream substream image was exceptional |
| 2023 | The downstream audio lagged |
| 2024 | The downstream big image lagged |
| 2025 | The downstream small image lagged |
| 2026 | The downstream substream image lagged |


---
*Source: [https://trtc.io/document/37906](https://trtc.io/document/37906)*
