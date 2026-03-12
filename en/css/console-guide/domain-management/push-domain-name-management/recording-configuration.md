# Recording Configuration

The live recording feature is disabled by default. This document describes how to bind a recording template to a push domain to enable the recording feature, as well as how to unbind a template to disable the feature.

## Use Limits

- A template takes effect about 5-10 minutes after it is bound to a domain.
- After a template is successfully bound to a push domain, recording will be enabled for push addresses under that domain.
- One domain can be bound with only one recording template. After binding, all streams under that domain will be recorded according to the template.
- Mixed-stream recording does not support mixing streams inside the Chinese mainland with those outside. It will cause an error and playback will fail.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live) and added a [push domain](https://intl.cloud.tencent.com/document/product/267/35970).
- You have [created a recording template](https://intl.cloud.tencent.com/document/product/267/34223).

## Binding a Recording Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the target **push domain** or click **Manage** to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1f54892b4a6111efbaba525400d5f8ef.png)

2. Select the **Template Configuration** tab and click **Edit** in the **Recording configuration** area.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2dbaa107ab0511f09710525400e889b2.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4827df4bab0511f09710525400e889b2.png)

3. Select a recording template and click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6ea76cdeab0511f0b08552540044a08e.png)

## Unbinding a Recording Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage), and click the target **push domain** or click **Manage** to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7a78374f4a6111efbaba525400d5f8ef.png)

2. Select the **Template Configuration** tab and click **Edit** in the **Recording configuration** area.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e83400d9ab0511f0a68e5254001c06ec.png)

3. Unselect the template and click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3d643c5dab0611f0b08552540044a08e.png)

> **Note:**Unbinding a recording template will not affect ongoing live streams.To cancel recording for ongoing streams, stop the streams and push them again.

## Obtaining Recording Files

### Recording to VOD

#### From the VOD console

Log in to the [VOD console](https://console.intl.cloud.tencent.com/vod/app-manage), select the target subapplication, and click **Video/Audio Management**on the left sidebar. You can view all your recording files on this page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6eb5ea3d4a6211efb36952540075b605.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f66ce7564a6211ef8f105254002693fd.png)

#### From recording callbacks

If you have configured a recording callback address in the console or using an API, after a recording file is generated, a notification will be sent to the callback address configured. For details about the fields of the callback, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).

> **Note:**The recording callback method is recommended for its reliability and real-timeliness.

#### Using a VOD API

You can also call the [SearchMedia](https://intl.cloud.tencent.com/document/product/266/34179) API of VOD to query recording files.

### Recording to COS

#### From the COS console

Log in to the COS console, click [Bucket List](https://console.tencentcloud.com/cos/bucket) on the left sidebar, and then click the target bucket. You will be able to find the recording files in the file list.


---
*Source: [https://www.tencentcloud.com/document/product/267/34224](https://www.tencentcloud.com/document/product/267/34224)*
