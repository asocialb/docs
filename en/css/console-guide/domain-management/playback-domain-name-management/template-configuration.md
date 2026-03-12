# Template Configuration

With CSS, the original bitrate is used for playback by default. To use a different playback bitrate, you can bind your domain with a transcoding or adaptive bitrate template. This document shows you how to bind a template to and unbind a template from a playback domain.

## Notes

- A template takes effect about 5-10 minutes after it is bound to a domain.
- After you specify a transcoding template, the backend will generate playback URLs of different formats for the transcoded stream. To avoid image distortion, push the stream at a resolution as close as possible to the original resolution.
- H.265 is supported by fewer players than H.264. Playback may fail if a player does not support H.265. To solve this issue, you can [configure a transcoding template](https://intl.cloud.tencent.com/document/product/267/31071) to transcode your video to H.264.
- Loading may take some time for the first user accessing the URL that uses a different playback bitrate.
- One domain can be bound with multiple transcoding templates. After you bind a template, videos will be transcoded as specified in the template.
- You can create up to **50** transcoding templates.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live) and added a [playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).
- You have created a [transcoding template](https://intl.cloud.tencent.com/document/product/267/31071) or an [adaptive bitrate template](https://www.tencentcloud.com/document/product/267/50271#creating-an-adaptive-bitrate-template).

## Transcoding Template

### Binding a transcoding template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click the name of your playback domain or **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7240bc1111ce11ef89cc5254002fd0a8.png)

2. Select  **Template Configuration > Transcoding Configuration** , and click **Edit** in the upper-right corner of the  **Transcoding Configuration**  tab.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7d91ccbbcb9311f08e74525400bf7822.png)

3. Based on your actual business needs, choose different transcoding configuration templates.

> **Note:**Choosing different transcoding configuration templates will specify the encoding method and bitrate settings set by the transcoding template for the playback URL under that domain.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ca861dd8cb9311f096d1525400e889b2.png)

4. Click **Confirm**.

### URL format for transcoded streams

Suppose the name of the transcoding template bound is **hd**, and the original playback URL is as follows:

```
http://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)
```

To play the transcoded stream, you need to use the following URL:

```
http://domain/AppName/StreamName_hd.flv?txSecret=Md5(key+StreamName_hd+hex(time))&txTime=hex(time)
```

### Unbinding a transcoding template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click the name of your playback domain or click **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4f58dd4211cf11ef9fa952540019e87e.png)

2. Select  **Template Configuration > Transcoding Configuration** , and click **Edit** in the upper-right corner of the  **Transcoding Configuration**  tab.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4076d7fdcb9411f08e74525400bf7822.png)

3. Based on your actual business needs, deselect the corresponding templates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/68ddb3eecb9411f091ab5254007c27c5.png)

4. Click **Confirm**.

> **Note**To delete a template, you need to unbind it first and then go to **Feature Configuration** > [Live Transcoding](https://console.tencentcloud.com/live/config/transcode) to delete it. For details, see [Deleting a Template](https://intl.cloud.tencent.com/document/product/267/31071#delect).

## Adaptive Bitrate Template

### Binding an adaptive bitrate template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click the name of your playback domain or **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cd87817411cf11ef9af4525400720cb5.png)

2. Select  **Template Configuration > Adaptive bitrate configuration** , and click **Edit** in the upper-right corner of the  **Adaptive bitrate configuration**  tab.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ac978c18cb9411f0ae4f52540099c741.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bbca0a75cb9411f093295254001c06ec.png)

3. Based on your actual business needs, choose the appropriate adaptive bitrate configuration template.

> **Note:**Choosing different adaptive bitrate configuration templates will specify the sub-stream information set by the adaptive bitrate template for the playback URL under that domain.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e292e377cb9411f084a45254005ef0f7.png)

4. Click **Confirm**.

### Adaptive bitrate URL format

Only HLS and WebRTC are supported for adaptive bitrate playback. The URL formats for the two protocols are different. For details, see [Playback Configuration](https://intl.cloud.tencent.com/document/product/267/31058).
**HLS URL**:
**Suppose** the name of the adaptive bitrate template bound is **autobitrate**, and the original playback URL is as follows:

```
http://domain/AppName/StreamName.m3u8?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)
```

To play the transcoded stream, you need to use the following URL:

```
http://domain/AppName/StreamName_autobitrate.m3u8?txSecret=Md5(key+StreamName_autobitrate+hex(time))&txTime=hex(time)
```

**WebRTC URL**:
**Suppose** the adaptive bitrate template bound has three streams. Their names are "test 1", "test 2", and "test 3", and their bitrates are 200 Kbps, 300 Kbps, and 400 Kbps respectively.
The adaptive bitrate playback URL would be as follows:

```
webrtc://domain/AppName/StreamName?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)&tabr_bitrates=test3,test2,test1&tabr_start_bitrate=test1&tabr_control=auto.
```

### Unbinding an adaptive bitrate template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click the name of your playback domain or click **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/519fdadf11d011efa2935254005ac0ca.png)

2. Select  **Template Configuration > Adaptive bitrate configuration** , and click **Edit** in the upper-right corner of the  **Adaptive bitrate configuration**  tab .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/09fd4c21cb9511f0ae4f52540099c741.png)

3. Based on your actual business needs, deselect the corresponding templates.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1ffa3442cb9511f0ae4f52540099c741.png)

4. Click **Confirm**.

> **Note**To delete a template, you need to unbind it first and then go to **Feature Configuration** > [Live Transcoding](https://console.tencentcloud.com/live/config/transcode) to delete it. For details, see [Deleting a Template](https://intl.cloud.tencent.com/document/product/267/31071#delect).


---
*Source: [https://www.tencentcloud.com/document/product/267/31062](https://www.tencentcloud.com/document/product/267/31062)*
