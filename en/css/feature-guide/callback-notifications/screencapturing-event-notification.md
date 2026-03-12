# Screencapturing Event Notification

Live screencapture takes real-time screenshots from a live stream at the specified interval and stores them in COS. A screencapture callback returns information about stored screenshots, including the screenshot generation time, image size, file path, and download link. To receive screencapture callbacks, you need to configure your server address in a callback template and bind the template with your push domain. When a live screencapture event occurs, the CSS backend will send the screenshot information to the server configured.

This document describes the fields in a live screencapture callback message.

## Notes

- This guide assumes that you understand how to configure callbacks and receive callback notifications from CSS. For details, see [How to Receive Event Notification](https://intl.cloud.tencent.com/document/product/267/38080).
- The information returned by a screencapture callback can be used for porn detection, live video thumbnail generation, and other scenarios.

## Screencapture Event Parameters

### Event type

| Event Type | Value |
| --- | --- |
| Live screencapture | event_type = 200 |

### Common callback parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires. The default validity period of a message notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a message notification has elapsed, then this notification is considered invalid, thereby preventing network replay attacks. The value of `t` is a decimal Unix timestamp, that is, the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Security signature. sign = MD5(key + t). Tencent Cloud splices the encryption **key**and `t`, generates the MD5 hash of the spliced string, and embeds it in callback messages. Your backend server can perform the same calculation when it receives a callback message. If the signature matches, it indicates the message is from Tencent Cloud. |

> **Note：**A key is used for authentication. You can set it in **Feature Configuration** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback). We recommend you set it to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/4edc50c4cb6711f084a45254005ef0f7.png)

### Callback message parameters

| Parameter | Type | Description |
| --- | --- | --- |
| app | string | Push domain name |
| appname | string | Push path |
| stream_param | string | Push URL parameters |
| stream_id | string | Live stream name |
| channel_id | string | Same as the stream name |
| create_time | int64 | Unix timestamp when a screenshot is generated |
| file_size | int | Screenshot file size in bytes |
| width | int | Screenshot width in pixels |
| height | int | Screenshot height in pixels |
| pic_url | string | Screenshot file path (`/path/name.jpg`) |
| pic_full_url | string | Screenshot download URL |
| task_id | string | Screenshot task ID |

### Sample callback message

```
{    "app":"test.app",    "appname":"live",    "channel_id":"your_channelid",    "create_time":1622599925,    "event_type":200,    "file_size":30670,    "height":720,    "pic_full_url":"http://your.cos.region.myqcloud.com/channelid/channelid-screenshot-10-12-05-1280x720.jpg",    "pic_url":"/channelid/channelid-screenshot-10-12-05-1280x720.jpg",    "sign":"ca3e25e5dc17a6f9909a9ae7281e300d",    "stream_id":"your_streamid",    "stream_param":"txSecret=ca3e25e5dc17a6f9909a9ae7281e300d&txTime=60B83800",    "t":1622600525,    "width":1280        "task_id":"1867908378267662126"}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/38083](https://www.tencentcloud.com/document/product/267/38083)*
