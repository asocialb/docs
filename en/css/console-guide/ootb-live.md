# OOTB live

OOTB Live is a ready-to-use tool that lets you create your own personalized live streaming rooms in only two steps, with no special technical expertise or development required. With OOTB Live, you can quickly start a live streaming session for training or product promotion while maintaining private traffic, promoting your own brand and products, and enhancing the effectiveness of online training and sales follow-ups. This document describes how to create and manage live rooms on the management side, how to carry out live streaming on the host side, and how to view live streams on the audience side.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- You have added a [playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Points of Attention

Currently, this feature is in beta testing. Fees are collected based on the actual use of the function. For more details, refer to [Pricing Overview](https://www.tencentcloud.com/document/product/267/2819?has_map=1&lang=zh&pg=). As of January 1,2024, billing will be based on monthly subscription plans.

## Live Room Management (Management Side)

### Creating a Live Room

1. Log in to the CSS console and go to **CSS Toolkit**> [OOTB Live](https://console.intl.cloud.tencent.com/live/txelvb).
2. Click **New room** to enter the live room creation window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a3c851e2016011efb881525400a7e516.png)

3. Specify **Room name**. The name can contain up to 20 characters and supports only Chinese characters, English letters,  numbers, underscores (_),  and hyphens (-).
4. Choose the **start time** to specify when live streaming will begin, and click **OK** to confirm the time.
5. Select a **playback domain** that you have already added in the Domain Management page.
6. A default thumbnail image is provided for the live room. Click **Change** to upload your own thumbnail image. We recommend a JPG or PNG image 2 MB or smaller with resolution of 1280x720 px.
7. Click **Create.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b4f1def8016011efb881525400a7e516.png)

### Live Control

1. Log in to the CSS console, go to **CSS Toolkit** > [OOTB live](https://console.intl.cloud.tencent.com/live/txelvb).
2. Select the live room you created and click **Manage rooms**. On this page, you can delete a live room or copy and share links for viewing the live stream.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c52bbef4016011efbba352540095b445.png)

3. Enter the Live Control page and choose [Web](#82e0ba6a-224f-4c69-8654-0eca9a7eeb17), [Publish](#ff759044-0633-4b9a-bc44-a17ce6ec2648), or [Playback](#5e8bf136-02a7-4106-82c1-c53d9d8b4f7b) to select which method you want to use for live streaming.
  - Web: The host uses the web-based live streaming tools provided by OOTB live. Options for live streaming include using a camera, local files, or screen sharing.
  - Publish: The host can stream using third-party tools such as OBS. In this case, the push streaming addresses provided by the system are entered into these third-party tools. For more information, refer to [Push via OBS](https://www.tencentcloud.com/document/product/267/31569).
  - Playback: This method is for scenarios in which you want to play a pre-recorded video as a live stream (pseudo-live streaming) or pull a stream from a third-party platform.

#### Scenario 1: Web

This scenario is mainly focused on real-time processing.

1. When you select **Web**, a streaming URL is provided for the host. Click on **Copy** to copy and send the URL to the streaming host.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0cbf1c33016111efbba352540095b445.png)

2. A **Playback URL** is provided at the top of the page. You can copy the URL or click on the copy icon to copy it and distribute it to your audience.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7f362082016111efb881525400a7e516.png)

3. To enable the chat feature, go to **Settings**.

#### Scenario 2: Publish

1. By default, the system generates a publish URL and stream name, which can be copied to third-party publish streaming tools such as OBS for live streaming.
2. The copied publish URL and stream name can be pasted into OBS's server and stream code respectively for publishing.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/afcda555016111efbba352540095b445.png)

#### Scenario 3: Playback

1. The source stream address supports live streaming playback protocols such as RTMP, HLS, and FLV, among others.
2. In the source stream address input box, you can enter the source stream address, which is equivalent to setting the content source to a live source in [Pull and Push Streaming](https://www.tencentcloud.com/document/product/267/42524). After entering the address, click **Play**on the right to pull the corresponding live stream and push it to Tencent Cloud.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cf82c2c5016111ef9125525400275b90.png)

### Live Room Configuration

#### Basic settings

- Log in to the CSS console and go to **CSS Toolkit** > [OOTB Live](https://console.intl.cloud.tencent.com/live/txelvb) > **Manage rooms** > **Settings**.
- On this page, you can adjust and modify the basic settings of a live room you created, including the live room name, start time, playback domain, and thumbnail.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e7a0e5c7016111ef9125525400275b90.png)

#### Feature configuration

1. **Viewing Modes**
  1.1. The default viewing mode is **Public**. However, you can also choose **Encrypted** viewing or use an **Allowlist** to control who can access the live stream.
  - If you opt for encrypted viewing, a password is required for viewing the live stream. This password should be between 8-14 characters in length and must not contain spaces, Chinese characters, or special symbols.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f96b1dac016111ef9125525400275b90.png)

  - If the viewing mode is set to Allowlist:
    - Click **Add viewer** to add a user to the allowlist. You can remove users from the allowlist by selecting them and clicking **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0c086dc9016211efb881525400a7e516.png)

      - Verification Info: Enter the corresponding verification information for the user, such as an employee number, mobile number, etc.
      - Nickname: Set a name for the viewer. It can be the viewer's real name or a custom nickname.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/35485a46016211efb881525400a7e516.png)

      - Click **Create**.
    - Click **Import via file** to import CSV or Excel files to quickly add users allowed to view the live stream.
    - Click **Download template** to download the import template for adding users. User information must be added to the import file according to the template. Otherwise, errors may occur during the import.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5fc4aa3c016211efbf03525400ae4d13.png)

2. **Live Stream Interactive Chat**

The live stream chat feature is disabled by default. You can click

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4ec221ae903211eeb6c6525400e46040.png)

to enable it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/97c42cfb016211efbba352540095b445.png)

> **Note:**Interactive chat, on-screen comments, and other interactive features in live stream rooms are provided by [Tencent Cloud Chat](https://www.tencentcloud.com/products/im). A Chat Developer Edition application is created by default (the application name starts with "elvb_"), which is valid for one month. After expiration, you can go to the [Chat console](https://console.intl.cloud.tencent.com/im) to renew or upgrade the version at any time.

### Organization/Enterprise info

- The options on this page are **disabled** by default. You can click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/0b44513e903311ee8964525400321be2.png) to display them during the live stream.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ecbec5ae016211ef9125525400275b90.png)

  - Name: Enter the name of the organization or enterprise. The name cannot be more than 60 characters.
  - Logo: Click **Upload** to add an organization or enterprise logo to be displayed during the stream. We recommend a JPG or PNG image with the resolution of 1280x720 px, 2 MB or smaller.
  - Contact: Click **Upload** to display a QR code to the audience. When a viewer clicks **Contact us**, this QR code will be displayed.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a1a259ad016311efb881525400a7e516.png)

### Before Live Streaming Begins

1. When modifying live room configurations, you can instantly view the changes in the **Configuration Preview** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c6b32c88016311efbf03525400ae4d13.png)

2. After confirming the preview, click **Save**, and commence the live streaming as needed.

> **Note:**The configuration will take approximately one minute to take effect after it has been completed.

## Host Side

### Before Live Streaming Begins

1. Even if the live streaming start time has not yet arrived, you can start your live stream in advance. Just click on **Go live** at the bottom-right corner.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e8c13096016311efbba352540095b445.png)

> **Note:**The live streaming countdown shows the amount of time remaining until the scheduled start time of the live stream.

2. To confirm that you want to start the live stream in advance, click **Confirm**. The live stream will begin immediately.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0a00ac47016411efbf03525400ae4d13.png)

### During the Live Stream

1. When the web platform is used to conduct a live stream, the WebRTC stream publishing protocol is employed (it is the only protocol supported on the web platform).
2. You can conduct live streaming through a camera, screen sharing, local files, and so on. Click the **Go live** button and the system will commence streaming. Here's an example of how to live stream through uploading a video from local files:
  2.1. On the webpage, select **Local file** and choose the video file you want to upload. After the video is uploaded, click **Go live** to commence the live streaming. It's advised to perform a test in advance to ensure that the live room's settings and video quality meet your requirements.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/626ebaf7016411efbba352540095b445.png)

  2.2. The host can click the ![](https://staticintl.cloudcachetci.com/cms/backend-cms/fe063ff5903511ee8964525400321be2.png) button in the top-right corner, click **Copy**(the live room's name, time, and URL) or **Download code**, and forward it to viewers. The shared link corresponds to the live stream room. The audience can watch the live stream by scanning the QR code shared by the host or visiting the link.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a937a41e016411ef9125525400275b90.png)

  2.3. When the live stream concludes, the host can click **End the broadcast** to stop the live streaming.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c813d799016411efb881525400a7e516.png)

> **Note:**If the live room is deleted during the live streaming, the ongoing live streaming will not be interrupted.

## Audience Side

### Before Live Streaming Begins

1. After visiting the link shared by the host, the audience can, by default, directly open and watch the live stream. If the host implemented **Encrypted** or **Allowlist** viewing modes, the audience is required to enter verification information (nickname and password) in the pop-up verification bar. Only after successful verification can they proceed to open the live room.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/41d99cdb016011ef9125525400275b90.png)

2. Before the host begins live streaming, the audience entering the live room can see the countdown timer, which shows the remaining time until the live stream starts.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/765a71668e8211eea5405254004fadac.png)

### During the Live Stream

After entering the live room, viewers can watch the live stream and view and post comments.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/766b030f8e8211ee9cfb525400ffb43f.png)

### End of Live Stream

After the live stream has ended, viewers can remain in the room and continue to view and post comments.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/766d55808e8211ee9e23525400089cca.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/57989](https://www.tencentcloud.com/document/product/267/57989)*
