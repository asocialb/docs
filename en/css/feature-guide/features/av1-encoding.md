# AV1 Encoding

AOMedia Video 1 (AV1) is a free, open source video encoding format. It encodes videos at a bitrate 30%+ lower than H.265 (HEVC) does while delivering the same video quality. This means that with the same bandwidth, AV1-encoded videos have higher quality than H.265-encoded videos. This document shows you how to encode videos using AV1 and how to play AV1-encoded videos.

## How to Use AV1

### Prerequisites

- You have [signed up for a Tencent Cloud account](https://intl.cloud.tencent.com/document/product/378/17985).
- You have activated CSS and added [a playback domain and a push domain](https://intl.cloud.tencent.com/document/product/267/35970).

### Step 1. Create a transcoding template

1. Log in to the CSS console and select **Feature Configuration** > [Live Transcoding](https://console.tencentcloud.com/live/config/transcode) on the left sidebar.
2. Click  **Create template** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b15d51582c7c11efb0275254006c0558.png)

3. Select the transcoding type as either  **Standard Transcoding**  or  **Top Speed Codec Transcoding** , and expand the advanced configuration. In Codec, choose  **AV1** .

Standard Transcoding

Top Speed Codec Transcoding

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b1633f4c2c7c11ef97da5254007d9c55.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b15c9b1d2c7c11efa4f552540077de32.png)

4. Click **Save**.

### Step 2. Bind a domain

1. Select a transcoding template, and click  **Bind Domain Name** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/97f3a1662c7d11efb0275254006c0558.png)

2. Select the  **Transcoding Template**  and  **Playback Domain**  you wish to bind, and then click  **Confirm** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/97f2346d2c7d11ef918f52540005b090.png)

> **Note:**The domain name binding will take effect in approximately 10 minutes after being bound.

### Step 3. Generate a playback URL

1. Log in to the CSS console > Go to **CSS Toolkit**> [Address Generator](https://console.intl.cloud.tencent.com/live/addrgenerator/addrgenerator).
2. Select URL Type: Playback Address.
3. Select the playback domain name bound in [Step 2](https://www.tencentcloud.com/document/product/267/50796#step-2.-bind-a-domain) and the transcoding template from [Step 1](https://www.tencentcloud.com/document/product/267/50796#step-1.-create-a-transcoding-template)to generate the playback address.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/41149cd52c7e11ef918f52540005b090.png)

### Step 4. Play AV1-encoded videos

Play the AV1-encoded videos with a player that supports AV1 using the playback URL generated in[step 3](https://www.tencentcloud.com/document/product/267/50796#step-3.-generate-a-playback-url). You can either use a third-party player that supports AV1 or rebuild your own player.

- **Third-party players that support AV1**
  - **App**
    - [ExoPlayer](https://github.com/google/ExoPlayer) (use `libgav1`)
    - [ijkplayer](https://github.com/bilibili/ijkplayer) FFmpeg (update FFmpeg and integrate [dav1d](https://code.videolan.org/videolan/dav1d))
  - **Web**
    - [dash.js](http://cdn.dashjs.org/v2.4.0/jsdoc/index.html). The player supports AV1, but whether AV1 videos can be decoded depends on the browser. Chrome supports AV1 decoding.
    - [shaka-player](https://github.com/shaka-project/shaka-player). The player supports AV1, but whether AV1 videos can be decoded depends on the browser. Chrome supports AV1 decoding.
  - **PC**
  VLC for [Windows](https://share.weiyun.com/haPT1L0W) and [macOS](https://share.weiyun.com/W2btBASt) support AV1 in FLV and HEVC in FLV.
- **Rebuilding your own player**
If your player cannot play AV1 videos, you can refer to [AV1 Video Playback](https://www.tencentcloud.com/document/product/267/51157) to rebuild your player accordingly.


---
*Source: [https://www.tencentcloud.com/document/product/267/50796](https://www.tencentcloud.com/document/product/267/50796)*
