# Push Media Stream into TRTC

## Overview

Watch together, listen together, play together, learn togetherâ¦ Various experiences that once required face-to-face interaction are now moving online. Even if separated by thousands of miles, friends can still watch movies, listen to music and chat together. This amazing real-time interactive experience is becoming popular among young people and is now a major feature and mainstream direction of audio and video products.

TRTC offers two streaming solutions: [push online media stream](https://www.tencentcloud.com/document/product/647/62716#50940aad-d90f-4473-9f46-d5dd46917653) and [RTMP streaming with TRTC](https://www.tencentcloud.com/document/product/647/62716#3b96cc52-90be-46ee-aec0-218dcf302119), each with their own application scenario, as detailed below:

- [Push online media stream](https://www.tencentcloud.com/document/product/647/62716#50940aad-d90f-4473-9f46-d5dd46917653) is used to  **pull cloud-based online media streams (online streaming or cloud-based on-demand files)**  and push them into a TRTC room.
- [RTMP streaming with TRTC](https://www.tencentcloud.com/document/product/647/62716#3b96cc52-90be-46ee-aec0-218dcf302119) is used to**stream local media files and audio and video from capture devices**  into a TRTC room via the RTMP standard protocol.

> **Note:**Relevant fees are as follows:Feature unlocking:  **Push online media stream**  and  **RTMP streaming with TRTC**  features need to be unlocked by a subscription to the **basic** or **professional version** of [RTC-Engine monthly package](https://www.tencentcloud.com/document/product/647/56025#).Usage fees:Using the streaming feature involves transcoding operations, incurring transcoding costs. For more details, see the [Description of Billing of MixTranscoding and Bypass Relay](https://www.tencentcloud.com/document/product/647/47631#).The costs of audio duration incurred by the streaming robot in the room are charged (Note: The costs incurred by the robot in the room for push online media stream features will not be charged by August 15, 2024, and they will begin to be charged on August 16, 2024).The audience in the room subscribing to audio and video streams will incur audio and video call costs. For details, see the [Description of Billing of Audio and Video Duration](https://www.tencentcloud.com/document/product/647/42734).

## Push Online Media Stream

### Application Scenario

| Scenario type | Description |
| --- | --- |
| AI interactive classroom | Relying on TRTC's ability to push online media stream, the platform enables online live interactive teaching by combining recorded real-life teaching videos with AI technology. This significantly reduces operational costs while ensuring teaching effectiveness. Before class, the platform records video segments for explanation of knowledge points, interactive questioning, feedback on questions, and answers based on the teacher's course setup, and uploads them to the video library. During the class, these videos are streamed to the TRTC room for live broadcasting through the TRTC push online media capability. Students can engage in interactive learning through voice and touchscreen. The server uses AI technology to evaluate real-time voice and responses of students, seamlessly switches teaching segments, and provides different real-time feedback, thus offering a personalized teaching experience. |
| "Watch together" room service | Live streaming contents, such as game live streaming, fashion shows, and sports events, can be pushed to a TRTC room through the TRTC's push online media stream capability for ultra-low latency synchronized viewing within the room. With TRTC's real-time interaction capability, the audience can communicate in real-time, cheer together, and enjoy an immersive viewing experience. On-demand programs like movies and music can also be inputted into the TRTC room through the capability, allowing users to share in real-time and chat with friends while watching. |

### Feature Architecture

1. Users create push online media stream tasks using the REST API. These tasks are executed by the relay server.
2. The relay server pulls online streams or on-demand files.
3. The relay server pushes the fetched audio and video to the TRTC room and automatically generates a virtual anchor user. The username and room number of this user are specified when the task is created.
4. Other TRTC clients can watch these streams and utilize TRTC capabilities such as recording and relay.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6eef3c7e4a5611ef8357525400bdab9d.png)

### Feature Description

The feature description of push online media stream is as follows:

| Type | Description |
| --- | --- |
| Task initiation method | Users can initiate push online media stream tasks via the REST API. The audience can watch these streams, and features such as recording and relay are supported. |
| Multiple source protocols and formats | Protocols: HTTP, HTTPS, RTMP, HLSFormats: FLV, MP3, MP4, MPEG-TS, MOV, MKV, M4AVideo encoding: H.264, VP8Audio encoding: AAC, OPUS |
| Server-side callback | When a push online media stream task is created and completed, it can be called backed to the server on the service side for service logic purposes. For detailed push online media stream events, [go to view](https://www.tencentcloud.com/document/product/647/62717#). |

### Related Rest API

- Start push online media stream: [StartStreamIngest]( https://trtc.io/document/57835?product=serverapis)
- Stop push online media stream: [StopStreamIngest](https://trtc.io/document/57834?product=serverapis)
- Query push online media stream: [DescribeStreamIngest](https://trtc.io/document/57836?product=serverapis)

## RTMP Streaming With TRTC

TRTC supports the streaming of  **local media files**  and  **audio and video from capture devices**  into a TRTC room via the RTMP standard protocol. To facilitate your integration of TRTC, you can install [OBS](https://obsproject.com/download), FFmpeg, or other RTMP libraries to realize streaming with TRTC. OBS is a third-party open-source tool for live streaming. It is easy to use and free of charge, and it supports OS X, Windows, and Linux. OBS can be used in a wide range of scenarios and is capable of meeting most live streaming needs without requiring additional plugins. You can download its latest version from the [OBS website](https://obsproject.com/download?spm=a2c4g.11186623.2.15.6aac1445JPlKR8).

### Use Cases

| Scenario | Description |
| --- | --- |
| Online education | Use the desktop edition of OBS or FFmpeg to publish learning materials (most media formats are supported) over RTMP to a TRTC room. Students in the room can play the stream via the TRTC SDK and see the same learning materials as the teacher controls the playback progress/speed or switches between chapters. Excellent synchronization across multiple devices ensures better teaching quality. |
| Sports watching | Sports event organizers provide content in the form of RTMP streams. You can publish the streams to TRTC rooms so that users in the rooms can watch the event with ultra-low latency. With TRTCâs interaction capability, users can also audio/video chat with each other throughout an event. |
| Others | You can also use the RTMP publishing feature to implement other real-time interactive applications based on streaming. |

### Architecture

An RTMP client is a module of TRTC and can communicate with other TRTC clients. The interconnection delay is less than 600ms under normal circumstances. It can also use TRTC capabilities such as recording and relaying. The network architecture is shown in the figure below. **Not support pulling RTMP stream from TRTC; only support pushing stream to TRTC.**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4298b058b6b111ee9d74525400c26da5.png)

### Publishing and Playback URLs

#### Publishing URLs

```
rtmp://intl-rtmp.rtc.qq.com/push/Room ID?sdkappid=Application ID&userid=User ID&usersig=Signature
```

- Primary domain is intl-rtmp.rtc.qq.com; backup domain is rtmp.rtc-web.com. If there are issues with the primary domain DNS resolution, you can use the backup domain.
- For RTMP publishing, `appName` is `push`.
- Replace "Room ID", "Application ID", "User ID", and "Signature" with their actual values.
- For the sake of simplicity, we support only string-type room IDs. A room ID can contain numbers, letters, and underscores and cannot exceed 64 characters.

> **Warning:**To play an RTMP stream on other TRTC clients, when entering the room, make sure you use a string-type room ID.

- For how to generate `UserSig`, see [UserSig](https://www.tencentcloud.com/document/product/647/35166). **Make sure your signature is within the validity period**.

**Example:**

```
rtmp://intl-rtmp.rtc.qq.com/push/hello-string-room?sdkappid=140*****66&userid=******rtmp2&usersig=eJw1jdE********RBZ8qKGRj8Yp-wVbv*mGMVZqS7w-mMDQL
```

### Usage Example

You can use software or a programming library that supports RTMP to publish RTMP streams. The section below shows you how to do this.

#### Using OBS to publish streams

##### Prerequisites

You have installed [OBS](https://obsproject.com/download?spm=a2c4g.11186623.2.15.6aac1445JPlKR8).

##### Step 1. Select a source

In the **Sources** panel at the bottom, click **+**, and select a source based on your needs. Common sources include the following:

| Source | Note |
| --- | --- |
| Image | Publishes a single image |
| Image Slide Show | Publishes multiple images (you can determine the order of playback and whether to loop the playback) |
| Scene | Inserts an entire scene to enable various streaming effects |
| Media Source | Uploads a local file and publishes it as a live stream |
| Text | Adds real-time text to your stream |
| Window Capture | Captures and publishes the window you select in real time |
| Video Capture Device | Captures and publishes the images captured by a camera in real time |
| Audio Input Capture | Audio live streaming (audio input device) |
| Audio Output Capture | Audio live streaming (audio output device) |

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/00d504ed7b7c11ed8e7e525400463ef7.png)

##### Step 2. Set publishing parameters

1. In the **Controls** panel at the bottom, click **Settings**.
![img](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/00e684b27b7c11ed8e7e525400463ef7.png)
2. Click **Stream** and select **Custom** for **Service**.
3. Enter `rtmp://intl-rtmp.rtc.qq.com/push/` for **Server**.
4. Enter a stream key in the following format:

```
Room ID?sdkappid=Application&userid=User ID&usersig=Signature
```

Replace "Room ID", "Application ID", "User ID", and "Signature" with the actual values, for example:

```
hello-string-room?sdkappid=140*****66&userid=******rtmp2&usersig=eJw1jdE***************ZLgi5UAgOzoMhrayt*cjbmiCJ699T09juc833IMT94Ld7I0iHZqVDzvVAqkZsG-IKlzLiXOnEhswHu1iUyTc9pv*****D8MQwoA496Ke6U1ip4EAH4UMc5H9pSmv6MeTBWLamhwFnWRBZ8qKGRj8Yp-wVbv*mGMVZqS7w-mMDQL
```

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f6b507aa2ae11edbb45525400c56988.png)

##### Step 3. Configure the output

Because RTMP does not support B-frames, set the video encoding parameters as follows to remove B-frames.

1. Go to **Controls** > **Settings** > **Output**.
2. Select **Advanced** for **Output Mode**. The recommended **Keyframe Interval** is **1** or **2**. For **CPU Usage Preset**, select **ultrafast**. For **Profile**, select **baseline**. For **Tune**, select **zerolatency**. And for **x264 Options**, enter `threads=1`, and then click **OK**.

> **Warning:**You need to remove the B-frames in RTMP streams, otherwise the connection will be disconnected after pushing. To achieve this, select baseline for Profile.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/685ee210c6fe11edbe95525400088f3a.png)

##### Step 4. Set video parameters

You can set video resolution and frame rate under the

**Video**

section of

**Settings**

. Resolution determines the clarity of video shown to audience members. The higher the resolution, the clearer the video. Frame rate (frames per second) determines playback smoothness. Typical frame rate falls in the range of 24 fps to 30 fps. Playback may stutter if frame rate is lower than 16 fps. Video games require higher frame rate and tend to stutter at a frame rate lower than 30 fps.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/00d7736d7b7c11ed8e7e525400463ef7.png)

##### Step 5. Configure advanced settings

- To reduce end-to-end delay, we recommend you do not enable **Stream Delay**.
- Keep **Automatically Reconnect** enabled and make **Retry Delay** as short as possible so that the publisher can be reconnected quickly after a disconnection occurs due to network jitter.
![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/00fb5f967b7c11edab50525400c56988.png)

##### Step 6. Publish the stream

1. In the **Controls** panel at the bottom, click **Start Streaming**.
![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/00ff974d7b7c11ed8e7e525400463ef7.png)
2. If streaming is successful, the bottom bar will show streaming statistics, and the entry of a user will be recorded by the TRTC [monitoring dashboard](https://www.tencentcloud.com/document/product/647/39070).
![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/00f6df817b7c11edab50525400c56988.png)

##### Step 7. Play the stream on other clients

As mentioned above in

Set publishing parameters

, to play the RTMP stream on other TRTC clients, you need to use a string-type room ID when entering the room. The screenshot below is an example of playing the RTMP stream on

Web

. ï¼ps : You can go to the

Demo page

and enter the room on any client-side to view the stream .ï¼

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0103c8e67b7c11edab50525400c56988.png)

#### Using FFmpeg to publish streams

To publish RMTP streams using FFmpeg commands or other RTMP libraries, you need to use the full URL, the H.264 video codec, and the AAC audio codec. For the container format, FLV is recommended. For GOP, one or two seconds is recommended.
The configuration of FFmpeg parameters varies with different scenarios, so you need to have some knowledge of FFmpeg in order to use it to publish streams. The table below lists some common FFmpeg commands. For more options, see [FFmpeg documentation](https://ffmpeg.org/ffmpeg.html).

##### FFmpeg commands

```
ffmpeg [global_options] {[input_file_options] -i input_url} ... {[output_file_options] output_url}
```

##### Common FFmpeg options

| Option | Note |
| --- | --- |
| -re | Reads input at the native frame rate. This is usually used to read local files. |

Options for **output_file_options** include:

| Option | Note |
| --- | --- |
| -c:v | The video encoding library. `libx264` is recommended. |
| -b:v | The video bitrate. For example, `1500k` means 1,500 Kbps. |
| -r | The video frame rate. |
| -profile:v | The video profile. If you set it to `baseline`, B-frames will not be encoded. The TRTC backend does not support B-frames. |
| -g | The GOP (keyframe interval). |
| -c:a | The audio encoding library. `libfdk_aac` is recommended. |
| -ac | The number of sound channels. Valid values: `1`, `2`. |
| -b:a | The audio bitrate. |
| -f | The container format. Set it to `flv`. The FLV container format is required to publish to TRTC. |

Below is an example of reading a local file and publishing it to TRTC (note that quotation marks are required for the URL):

```
ffmpeg -loglevel debug -re -i sample.flv -c:v libx264 -preset ultrafast -profile:v baseline -g 30 -sc_threshold 0 -b:v 1500k -c:a libfdk_aac -ac 2 -b:a 128k -f flv 'rtmp://intl-rtmp.rtc.qq.com/push/hello-string-room?userid=rtmpForFfmpeg&sdkappid=140xxxxxx&usersig=xxxxxxxxxx'
```

##### Playback on other clients

The screenshot below is an example of playback on the [Web](https://www.tencentcloud.com/document/product/647/35076#). You can also play the stream on other clients.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/395492709fdc11efa0b3525400bdab9d.png)

## FAQ

### Streaming failed

Common causes

- No package purchased or expired.
- Incorrect or expired signature.
- Streaming with B-frames (appears as "stream ends after one second" on the dashboard); should set to baseline encoding.

Other causes

- If the stream is pushed by an embedded hardware device, the URL may be truncated.
- Streaming with H.265; should use H.264.
- Setting chunk size too large on the client; recommend setting chunk size to 1360.

### Lag and screen artifacts

Check the Tencent Cloud Real-Time Communication [dashboard](https://www.tencentcloud.com/document/product/647/39070) to monitor streaming frame rate stability. If stable, the issue is likely on the player's side - please investigate the player. **If the frame rate is unstable**, consider the following:

- Check if the streaming client's local CPU and memory are under high load. If using OBS for streaming, observe the status bar at the bottom for information on dropped frames, network, CPU, and frame rate.
- Check if the local **network bandwidth** is sufficient. Ping the streaming domain to observe RTT; use the [network diagnostic tool](https://itango.tencent.com/app/data/huatuo) to test the streaming domain and check bandwidth, ideally reaching 10M.
- The streaming client may try reducing bitrate and frame rate to lessen client load, refer to the OBS settings in the main text, recommend setting bitrate to 1500 Kbps for 720p.

### High Latency

- If the client pulling stream uses TRTC anchor role, latency is usually lower than that of TRTC audience role. If not anchor role, change to that and compare to see if there is improvement.
- Local encoding and network significantly affect the streaming end. Try different platforms for testing; if using OBS, consider streaming on a Windows system; ping the streaming domain to observe RTT.

### Stream not visible on other ends

The streaming end used a string room number, but the pulling end used a numerical room number; modify the pulling end to use a string room number to enter the room.

### Frequent disconnections and re-streaming

- Username duplication, causing mutual kicking out; ensure that the userid is globally unique under a single sdkappid.
- Streaming with B-frames; set to baseline encoding.

### Server callback

An RTMP streaming user is also a user in the TRTC room, with no fundamental difference from other end users, see [event callback](https://www.tencentcloud.com/document/product/647/39558).

### Using your own domain

Configure your own domain CNAME to official domain - recommended for future use.


---
*Source: [https://trtc.io/document/62716](https://trtc.io/document/62716)*
