# Web Push

CSS allows you to push streams over the web. You can generate a push URL quickly and push streams from the camera or screen or push a local file to test CSS features.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have added a [push domain name](https://intl.cloud.tencent.com/document/product/267/35970).
- Your device has a camera installed and your browser allows Flash to access the camera.

## Single stream

1. Log in to the CSS console and select [**Web Push**](https://console.tencentcloud.com/live/tools/webpush).Click on **Single stream**.
2. **Select the capturing source**, which can be camera, screen, or local file.

Camera

Screen Sharing

Local File

Capture and publish audio/video from the camera/mic (which can be a peripheral device). Click **Turn On** for **Camera**/**Mic**. You need to grant your browser access to the camera/mic if it is the first time you perform this action.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/92b0126243ec11ef91ee525400d5f8ef.png)

Capture and publish streams from the screen. Click **Select Screen** to select a screen/window/browser tab to publish.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a3006d9843ec11efa917525400fdb830.png)

Publish a local file using the web push tool to CSS. Click **Select** to select a file to publish. Currently, you can publish only files in MP4 format.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b22141cb43ec11ef8d465254002693fd.png)

> **Note：**You cannot change the capturing source after enabling camera preview or selecting screen content to share. To switch the source, disable camera preview or cancel screen sharing first.

3. **Configure capturing data**. The defaults are recommended settings, which vary with resolution. You can click **Edit** and select **Custom** to customize capturing data. **For camera and screen sharing, the settings include resolution, video frame rate, and audio sample rate, while for local files, only the former two are applicable.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5f4f40ca582711ee974d5254005f490f.png)

4. **Configure push data**. The defaults are recommended settings (the recommended video bitrate varies with resolution, and the audio bitrate is fixed). You can click**Edit** and select**Custom** to customize video and audio bitrates.

> **Note：**WebRTC push uses the Opus audio codec, and you are advised to play the streams pushed using LEB WebRTC URLs. If you use a standard live streaming protocol (RTMP, FLV, or HLS), the system will automatically convert the streams to AAC, which will incur transcoding fees. For details, see the [billing document](https://www.tencentcloud.com/document/product/267/39604).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e6ecf0d4582711ee84f2525400494e51.png)

5. **Preview streams**. After completing the above steps, you can enable preview to preview the stream on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/93c6564f44b911ef9287525400fdb830.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/48eee62943ed11efbc2f52540055f650.png)

6. Enter a WebRTC push URL or click **Generate** and complete the following configuration:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fc194ccb43ed11ef98fd52540075b605.png)

  6.1. Select your push domain.
  6.2. Enter a unique `AppName` for an application to distinguish it from other applications under the same domain name. `AppName` is `live` by default.
  6.3. Enter a custom `StreamName`, such as `test`.
  6.4. Select an expiration time, such as `2024-07-18 11:41:04`.
  6.5. Click **Confirm**, and a push URL is auto-generated.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9ea4601e43ee11efa136525400bdab9d.png)

7. Click **Start Push** to start streaming.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ccd9c03c43ee11efa24b525400a9236a.png)

  7.1. To enable/disable video or audio, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/06f38ed1582911ee94c3525400d793d0.png) or![](https://staticintl.cloudcachetci.com/cms/backend-cms/0e7342b8582911eeabd75254005810a4.png) . After you disable video/audio, data capturing will continue and push will still succeed, but the stream cannot be previewed and will have no video or audio.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e25c199b43ee11efa24b525400a9236a.png)

> **Note：**You cannot enable or disable preview after push succeeds, and you may incur bandwidth/traffic costs or the costs of other value-added services for pushing streams.

8. After push succeeds, click **View** below the preview to view streaming statistics. You cannot obtain statistics or playback URLs for push URLs not under your account. Please use a push domain under your account to generate push URLs or relay streams to your account.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5959a1ba43ef11ef91ee525400d5f8ef.png)

9. If you have added a playback domain in **Domain Management**, you can **select the domain** to generate a playback URL. If you need to generate a playback address with transcoding or adaptive transcoding configuration, you must first bind the playback domain to a transcoding template or adaptive transcoding template to generate a transcoded stream or adaptive transcoded stream.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7491a38943ef11efa136525400bdab9d.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8735833643ef11ef98fd52540075b605.png)

A playback URL is made up of four parts, as shown below:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a31c96bf582a11ee94c3525400d793d0.png)

Supported protocols include RTMP, FLV, HLS, and UDP. You can also click the QR code icon and scan the QR code using the [TCToolkit app](https://intl.cloud.tencent.com/document/product/1071/38147) to obtain the playback URL.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a881bc6343ef11efa917525400fdb830.png)

> **Note：**If HTTPS is enabled for the playback domain selected, the FLV and HLS URLs generated will start with https.

## Multiple streams

### Enter configuration

1. Log in to the CSS console and select [**Web Push**](https://console.tencentcloud.com/live/tools/webpush).Click on **Multiple streams**.
2. In the input configuration, click **Add**. Choose the capture method. You can select from three capture methods: camera capture, screen sharing capture, and local file capture. You can also add text configuration for multi-stream mixed live streaming. **Up to 10 input sources can be added**.

Camera

Screen Sharing

Local File

Text

Camera capture is the process of capturing video and audio through a camera/microphone (external devices are supported). Click **Enable Camera**/ **Enable Microphone**, and the first time you enable it, you'll need to grant the browser permission to use the camera and microphone.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/89efb113583111ee84f2525400494e51.png)

Screen sharing capture is the process of capturing a specific window or interface through the browser for sharing. Click **Select Screen Sharing**and choose the content to share, which can be the entire screen, a specific window, or a browser tab. You need to select the screen to share before you can save it.

Screen sharing capture supports selecting audio sources. Currently, only Chrome 74+ and Edge 79+ support capturing sound. On Windows systems, you can capture the entire system's sound, while on Linux and Mac, you can only capture the sound from a browser tab.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/826f2ae8583211eeabd75254005810a4.png)

Local file capture is the process of capturing images from a specified local file and then pushing it to the cloud live streaming service using a Web-based push tool. Click **Select Local File** to choose the content to be pushed. Currently, MP4, MP3, JPG, PNG, and BMP file formats are supported. Click **Enable Preview**to save the settings.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1618ecb5583311ee974d5254005f490f.png)

Text configuration allows you to add text to the mixed streaming image and then push it to the cloud live streaming service using a Web-based push tool. Enter text in the text content field.

In the image configuration, you can set the font, color, shadow, transparency, thickness, and text coordinates. The default text coordinates are in the center of the page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dcb32843583311ee94c3525400d793d0.png)

3. You can set capture configurations for camera capture, screen sharing capture, and local file capture. The default is the recommended configuration (different resolutions have different recommended configurations). Switching or modifying the configuration is not supported during the capture process. You need to make changes when the preview is closed.
4. You can set advanced configurations for camera capture, screen sharing capture, and local file capture. You can adjust the image, coordinates, mirroring, contrast, brightness, and saturation.
5. Click **Save**, and the input source will be added to the configuration.

### Change setting

1. In the input configuration, you can perform operations on the configured input sources.
2. Select the input source you want to modify and click **Configure**. The right-side pop-up window will display the configuration information of this input source, and you can modify the configuration information again. Switching or modifying the configuration is not supported during the capture process. You need to make changes when the preview is closed.
3. You can adjust the display order of input sources by dragging the buttons on the left side of the input sources up or down.
4. Click **Delete** to remove the input source.
5. Click **Disable Preview** to close the preview of the input source, but you can still select the image for editing in the image editing area.
6. For input sources with audio, you can adjust the volume. Click "Adjust Volume", drag the volume slider, and click **Confirm** to confirm.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/80b50f4343f011ef8d465254002693fd.png)

### Push configuration

**Push configuration**: Set the push configuration, with the default being the recommended configuration (different resolutions have different recommended video bitrates, and audio bitrate cannot be modified). You can click **Edit**in the upper right corner to enter custom editing configuration, where you can customize and modify the video and audio bitrates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e47ceaff43f011efa24b525400a9236a.png)

> **Note：**The audio encoding method for web push is Opus encoding, and it is recommended to use the Live Event Broadcasting (LEB) WebRTC address for playback. If you use the playback address of the standard live streaming (RTMP/FLV/HLS), the system will automatically convert it to AAC encoding for normal playback, which will generate audio transcoding fees. For details, please refer to the [Billing Documentation](https://www.tencentcloud.com/document/product/267/39604).

### Screen editing

1. After confirming the input configuration and push configuration, you can see the preview image in the preview box on the right, and you can edit the image as needed.
2. Click **Edit**, select the image in the preview box that needs to be adjusted, and you can drag and resize the image as needed.
3. After adjusting, click **Exit Edit**. If you are in the middle of pushing the stream, saving the changes will continue pushing the stream with the new image layout.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5addfbca43f111efa136525400bdab9d.png)

> **Note：**When you enter the image editing mode, you can adjust the image layout in the preview box. Exiting the image editing mode allows you to view the preview image of the push stream in the preview box. Editing the page does not affect the real-time push stream, and the configuration will be saved only when you exit the editing mode.

### Push address

1. Enter the WebRTC push address in the preview box below or click **Generate**, and configure the following information in the pop-up window:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8964f53243f111ef8d465254002693fd.png)

  1.1. Select your push domain.
  1.2. Enter a unique AppName for an application to distinguish it from other applications under the same domain name. AppName is live by default.
  1.3. Enter a custom StreamName, such as test.
  1.4. Select an expiration time, such as `2024-07-18 12:41:06`.
  1.5. Click**Confirm**, and a push URL is auto-generated.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0b50790443f711efb438525400f69702.png)

### Start streaming

1. To enable/disable video or audio.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/276d328943f711ef91ee525400d5f8ef.png)

  1.1. click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/587e7c9c584e11eeabd75254005810a4.png) or![](https://staticintl.cloudcachetci.com/cms/backend-cms/58788802584e11ee84f2525400494e51.png) . After you disable video/audio, data capturing will continue and push will still succeed, but the stream cannot be previewed and will have no video or audio.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3b88e7fb43f711ef8d465254002693fd.png)

  1.2. After push succeeds, click **View** below the preview to view streaming statistics. You cannot obtain statistics or playback URLs for push URLs not under your account. Please use a push domain under your account to generate push URLs or relay streams to your account.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5e2cd75343f711efa917525400fdb830.png)

  1.3. If you have added a playback domain in **Domain Management**, you can **select the domain** to generate a playback URL. If you need to generate a playback address with transcoding or adaptive transcoding configuration, you must first bind the playback domain to a transcoding template or adaptive transcoding template to generate a transcoded stream or adaptive transcoded stream.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/75ba835343f711ef8d465254002693fd.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/84606df943f711efb438525400f69702.png)

A playback URL is made up of four parts, as shown below:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/40d15354584f11ee94c3525400d793d0.png)

Supported protocols include RTMP, FLV, HLS, and UDP. You can also click the QR code icon and scan the QR code using the [TCToolkit app](https://intl.cloud.tencent.com/document/product/1071/38147) to obtain the playback URL.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9e4b2f1843f711efa917525400fdb830.png)

> **Note：**If HTTPS is enabled for the playback domain selected, the FLV and HLS URLs generated will start with https.


---
*Source: [https://www.tencentcloud.com/document/product/267/35968](https://www.tencentcloud.com/document/product/267/35968)*
