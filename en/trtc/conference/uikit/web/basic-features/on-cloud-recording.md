# On-Cloud Recording

This article introduces how to quickly use TUIRoomKit's cloud recording feature to help developers achieve diversified needs such as archiving and reviewing important content in video conferencing, online education, live interactive, and other scenarios. We provide two solutions for you to choose from: [Automatic Recording](https://www.tencentcloud.com/document/product/647/60094#.E6.96.B9.E6.A1.88.E4.B8.80.EF.BC.9A.E8.87.AA.E5.8A.A8.E5.BD.95.E5.88.B6.E6.96.B9.E6.A1.88.EF.BC.88.E6.8E.A8.E8.8D.90.EF.BC.89) and [RESTful API-Based Recording](https://www.tencentcloud.com/document/product/647/60094#.E6.96.B9.E6.A1.88.E4.B8.80.EF.BC.9A.E8.87.AA.E5.8A.A8.E5.BD.95.E5.88.B6.E6.96.B9.E6.A1.88.EF.BC.88.E6.8E.A8.E8.8D.90.EF.BC.89#.E6.96.B9.E6.A1.88.E4.BA.8C.EF.BC.9Arest-api-.E5.BD.95.E5.88.B6.E6.96.B9.E6.A1.88).

## Scheme 1. Automatic Recording (Recommended)

We recommend using the automatic recording solution, which does not require the business side to start and stop the recording. The Tencent Cloud Real-Time Audio and Video backend manages the recording tasks, and it automatically records when there is audio and video stream uploading during the call. The access process is fast and simple. You can complete it in the following steps:

1. Find the application of the target `SDKAppId` in [**Application Management**](https://console.tencentcloud.com/trtc/app) in the TRTC console and enter the **Advanced Feature** page.
2. In the **Advanced Function** configuration page, you can see the option for **On-cloud recording** configuration. Click on **Global Auto-Recording** to enter the configuration popup window.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2568e33fbda11eeac26525400ae4d13.png)

3. In the configuration popup windowï¼You can customize the recording template as needed. ã

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c28eb414fbda11eeb7f5525400a7e516.png)

> **Noteï¼**Global automatic recording only supports [single-stream recording (i.e., each host records a single file)](https://www.tencentcloud.com/document/product/647/45169#single-stream-recording). Once enabled, it only applies to newly created rooms and does not take effect for rooms created before the automatic recording feature is enabled. If you need to record the screen after mixing multiple streams, please use the [RESTful API-Based recording](https://www.tencentcloud.com/document/product/647/60094#.E6.96.B9.E6.A1.88.E4.BA.8C.EF.BC.9Arest-api-.E5.BD.95.E5.88.B6.E6.96.B9.E6.A1.88).Global automatic recording supports recording up to 25 hosts in a room. If there are more than 25 hosts, they will be sorted by the time they enter the room, and the first 25 hosts will be recorded (if you need to record more than 25 hosts in a single stream, please refer to the [RESTful API-Based recording](https://www.tencentcloud.com/document/product/647/60094#.E6.96.B9.E6.A1.88.E4.BA.8C.EF.BC.9Arest-api-.E5.BD.95.E5.88.B6.E6.96.B9.E6.A1.88)).

After enabling the global automatic recording feature, the automatic start recording task will be triggered after the conference starts and there is audio and video uploading. After the conference ends, the recording will automatically stop. If you leave the room abnormally due to network or other situations, our recording backend will automatically stop the recording task according to the MaxIdleTime value you set (idle waiting time, default 5s) to avoid causing additional billing losses.

## Scheme 2. RESTful API-Based Recording

If the automatic recording scheme doesn't meet your needs, you can also use the more flexible RESTful API-based recording scheme. In this scheme, you can record and subscribe to a specified anchor in the room, customize the layout of mixed streams, and update the layout and subscription during recording. However, **using its features requires using it together with the business backend service and performing complex integration operations**:

1. Find the application of the target `SDKAppId` in [**Application Management**](https://console.tencentcloud.com/trtc/app) in the TRTC console and enter the **Advanced Feature** page.
2. On the Advanced Features configuration page, you can see the options for cloud recording configuration. Enable the cloud recording feature. Here, it is recommended to turn off Global Automatic Recording, which defaults to Manual Custom Recording, that is, RESTful API-based recording mode.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c2270289fbda11ee894852540046dfed.png)

3. Afterward, you can call the REST API ([CreateCloudRecording](https://trtc.io/document/46960)) to start the cloud recording. Here, it is recommended that you can listen to the notification events of [TUIRoomObserver](https://www.tencentcloud.com/document/product/647/54863#) and start recording when the meeting starts.

> **Note:****Under manual recording, you can go to the console to configure the callback address to receive recording callback events**, please see [Recording Callback Description](https://www.tencentcloud.com/document/product/647/54914#).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c234603bfbda11eeac26525400ae4d13.png)

## FAQs

### 1. Can the two recording solutions be used simultaneously?

The [Automatic Recording Solution](https://www.tencentcloud.com/document/product/647/60094#.E6.96.B9.E6.A1.88.E4.B8.80.EF.BC.9A.E8.87.AA.E5.8A.A8.E5.BD.95.E5.88.B6.E6.96.B9.E6.A1.88.EF.BC.88.E6.8E.A8.E8.8D.90.EF.BC.89) and [REST API Recording Solution](https://www.tencentcloud.com/document/product/647/60094#.E6.96.B9.E6.A1.88.E4.B8.80.EF.BC.9A.E8.87.AA.E5.8A.A8.E5.BD.95.E5.88.B6.E6.96.B9.E6.A1.88.EF.BC.88.E6.8E.A8.E8.8D.90.EF.BC.89#.E6.96.B9.E6.A1.88.E4.BA.8C.EF.BC.9Arest-api-.E5.BD.95.E5.88.B6.E6.96.B9.E6.A1.88) do not conflict and can be used simultaneously. However, two recording files and [fees](https://www.tencentcloud.com/document/product/647/45176#) will be generated.

### 2. How do I view recorded files?

Log in to the [VOD console](https://console.tencentcloud.com/vod), select **Video/Audio Management** on the left sidebar, click **Search by prefix** above the list, select **Search by prefix**, and enter the keyword in the search box. The recording filenames are in the following formats:

- The filename format of an MP4 single-stream recording file: `<SdkAppId>_<RoomId>_UserId_s_<UserId>_UserId_e_<MediaId>_<Index>.mp4`
- The filename format of an MP4 mixed-stream recording file: `<SdkAppId>_<RoomId>_<Index>.mp4`


---
*Source: [https://trtc.io/document/60094](https://trtc.io/document/60094)*
