# Step Three: Generate Output

After configuring the Live Video Caster (LVC), you can start PGM output. LVC also supports recording and relay, enriching downstream live broadcast systems.

## Prerequisites

- You have completed the steps in [Adding Input Sources](https://www.tencentcloud.com/document/product/267/58532).
- You have completed the steps in [Directing and Editing](https://www.tencentcloud.com/document/product/267/58531).

## Step 1: Starting Output

1. If the preview effect meets your requirements, you can click **To PGM** to start the output.

> **Note:**A red frame appears on the input source or layout that is currently being used for output, indicating that the input source or layout is in use in PGM.Once the stream is published to PGM, formal output and billing start. Closing the LVC console will not stop the live streaming or PGM output; the LVC will remain in operation and billing will continue. To stop the LVC, you need to manually turn off the PGM.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/59c8d2a96d1f11f096685254001c06ec.png)

2. Before publishing the stream, the system once again verifies whether to turn on the main monitor (PGM).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f6aa88ed295111ef812f5254002a8f58.png)

3. Once the output starts, you can see the published stream in the main monitor.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fe9858056cf811f081ce52540044a08e.png)

## Step 2: Obtaining the Output Playback URL

1. After the stream is published to PGM, if you want to obtain the output playback URL, you can click **Details**in the upper-right corner to enter the details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6d3a24466d1f11f087e15254005ef0f7.png)

2. Click **Generate** to enter the [Address Generator](https://www.tencentcloud.com/document/product/267/31084) to generate the URL.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1ef0ad0c200b11f08ca05254005ef0f7.png)

> **Note:**Make sure you have already successfully [configured a CNAME](https://www.tencentcloud.com/document/product/267/31057) for your domain.If you have not set a live streaming playback domain, this section is blank and you cannot play the stream through Tencent Cloud CDN.If you have multiple domains, the LVC system will randomly select a domain to generate a playback URL. If the randomly selected domain does not meet your needs, you can go to the CSS console to generate a playback URL.

## Step 3: Recording the Live Stream

1. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/50325ed7a46311eebf3d525400bb593a.png) in the main monitor (PGM) to enter the recording configuration page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/adcb3da56cf911f096685254001c06ec.png)

2. Select a recording template you configured and set the recording end time. The maximum recording duration is 24 hours. Click **Confirm** to start recording.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8ee0ef12200b11f08f0a5254007c27c5.png)

3. Once recording has started, hover your mouse over **Recording** and click to stop recording.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e32b84196cf911f09f3d52540099c741.png)

4. The system transmits the recorded file to the Video on Demand (VOD) system. You can view the recorded file in **VOD**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7a70d999295211ef9dd5525400441de3.png)

5. Click **Details** in the upper-right corner to enter the details page and view or copy the prefix of your recording file.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/55449480200c11f08f0a5254007c27c5.png)

> **Note:**You can go to [VOD](https://console.tencentcloud.com/vod/overview) > **Application Management**, select an application, and click **Enter Application** to access the **Media Asset Management Guide**.![](https://staticintl.cloudcachetci.com/cms/backend-cms/4a95e0ac200d11f0ab845254001c06ec.png)On the **Audio/Video Management** page, you can search for a recorded video by entering its file prefix.![](https://staticintl.cloudcachetci.com/cms/backend-cms/29ba1f6a200d11f0bc15525400bf7822.png)

## Step 4: Setting a Relay

To push your live stream to a third-party cloud vendor, you need to configure a relay first.

1. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/505e2fb0a46311eeb0fd525400170219.png) in the upper-right corner and select **Publish** to enter the push settings page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7f357c966d1f11f09e39525400454e06.png)

2. Fill in the **CSS stream name**.
3. You can enable delayed playback for the live stream. The maximum delay is 300 seconds.
4. Click **Advanced settings** to configure the domain and parameters.

| Advanced Settings | Required | Description |
| --- | --- | --- |
| Push domain | No | Select an available push domain. If left blank, this field will be filled with a backend-generated value when you save the settings. |
| AppName | No | Use English letters, numbers, and underscores only. |
| Custom parameters | No | Enter stream push parameters. |

5. Set a relay address:

Click

![](https://staticintl.cloudcachetci.com/cms/backend-cms/505edd8ba46311eeb0fd525400170219.png)

to add a custom third-party vendor address.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/901a3c866d1f11f096685254001c06ec.png)

> **Note:**Third-party relay supports only RTMP and RTMPS protocols.The stream push address format is as follows: rtmp(s)://domain/app/stream?arg1=xxx.The relay feature is enabled by CSS.To learn more,see [Getting Started with LVC](https://www.tencentcloud.com/document/product/267/58532) and [LVC Billing](https://www.tencentcloud.com/document/product/267/58538).A maximum of three target addresses are supported in third-party relay. One of the target addresses defaults to the current Tencent Cloud Streaming Services account, and the other two can be third-party addresses, excluding streaming domain names under the current account. Relay to third parties incurs relay bandwidth-based fees, which are calculated according to the relay charging standard.Relay to other CSS accounts (other than those under the current account) also incurs bandwidth-based fees, which are calculated according to the relay billing rules. For more information, see [Live Video Caster Billing Overview](https://www.tencentcloud.com/document/product/267/58538).

6. Set the size of the video output.
  - Select **Custom**, and set the following parameters:
    - Video width: The long side and short side of the video must not exceed 4096 x 2160 pixels.
    - Video height: The long side and short side of the video must not exceed 4096 x 2160 pixels.
    - Frame rate: No greater than 60 fps.
    - Video bitrate: No greater than 10,000 kbps.
    - Audio bitrate: Supports 128 kbps, 192 kbps, and 256 kbps.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6217810a200e11f0b21052540099c741.png)

7. Click **Confirm** to save the settings.

## Step 5: Setting a Standby Input Source

You can enable a standby input source on the standby stream page.

1. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/5068efa5a46311eebd03525400c26da5.png) in the upper-right corner and select **Standby Settings** to enter the standby stream page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9cdcb9f46d1f11f09e39525400454e06.png)

2. Enable or disable the standby video. A standby video serves as an auxiliary input source. If a standby video is enabled, when the input source or pulled stream for the PGM (primary stream) fails or is interrupted, LVC automatically switches to the standby video. Once the primary stream recovers, LVC switches back to the primary stream.
3. Set the input type to On demand URL or Live URL.
  - On demand URL: You can set multiple on-demand URLs by separating them with semicolons (;) or line breaks.
  - Live URL: Fill in this field with the stream/playback URL.
4. Enable or disable the standby image. A standby image serves as an auxiliary image input source. If a standby video is not enabled, when the input source or pulled stream for the PGM (primary stream) fails or is interrupted, LVC automatically switches to the standby image. Once the primary stream recovers, LVC switches back to the primary stream.
5. Click **Upload**and upload a standby image. The size limit is 5MB, and the image format must be PNG, JPG or JPEG.
6. Click **Confirm** to save the settings.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d1d8a2ae6d2011f0bcac525400e889b2.png)

> **Note:**If a standby video and standby image are both enabled, LVC switches to the standby video first. If the standby video also fails, LVS switches to the standby image.

### Enable Emergency Standby

1. After the PGM on the director's console is turned on, you can also manually insert the standby input through the Emergency Standby function. You can click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/6cdb261e2b1611f08caa5254005ef0f7.png) to manually start the Emergency Standby.

> **Note:**First, you need to configure the standby in the settings [(add Standby video/picture)](https://www.tencentcloud.com/document/product/267/58531#.5B.5D(id.3Astep6).E6.AD.A5.E9.AA.A46.EF.BC.9A.E6.B7.BB.E5.8A.A0.E5.A4.87.E6.92.AD.E8.A7.86.E9.A2.91.2F.E5.9B.BE.E7.89.87) and turn on PGM to enable the Emergency Standby function.If the Standby video function is not enabled, when the input source (referred to as the primary stream) of PGM is disconnected or fails to pull the stream, it will automatically switch to the Standby image. When the primary stream is recovered, it will switch back to the primary stream.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e3d42b7b6d2011f084fc525400bf7822.png)

2. After clicking **Confirm**, the PGM image willbe switched to the standby image immediately.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/093f55cb2a2911f0a62e525400454e06.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fd8d2c866d2011f096685254001c06ec.png)

### Turn off Emergency Standby

1. According to your business needs, you can click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/fe296f7d2b1611f0b47352540044a08e.png) to turn off Emergency Standby. Once it is disabled, standby will be switched to PGM. If delayed playback is configured for LVC, delayed playback will be performed before the standby is switched to PGM.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/118d9d316d2111f09e39525400454e06.png)

2. Click **Confirm** to switch to live streaming.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0cadf15c2a2a11f0a62e525400454e06.png)

## Step 6: Monitoring Output Stream Quality

After the stream is output from LVC, you can view the frame rate and bitrate data in the **Monitor** section.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ddfae8856d0d11f096685254001c06ec.png)

1. Click **Refresh** in the upper-right corner to refresh the current chart.
2. Click **Stream data** to view the detailed push stream data.

Frame rate

Video bitrate

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f62b480f6d0d11f09f3d52540099c741.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0c0463c56d0e11f084fc525400bf7822.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/58530](https://www.tencentcloud.com/document/product/267/58530)*
