# Errors

Tencent Cloud Streaming Services (CSS) supports the errors feature, allowing you to quickly check errors that occur during the live streaming process. Moreover, you can understand the status of these streams by viewing the primary and backup stream events.

## Prerequisites

You have logged in to the [CSS Console](https://console.tencentcloud.com/live).

## Note

You can configure the push errors event callback in the [Live Callback](https://console.tencentcloud.com/live/config/callback) settings. When an event occurs within the live streaming service, the message will be notified through a unified callback of the event message.

## Push Errors Query

1. Select **Monitoring** > [Errors](https://console.tencentcloud.com/live/event/error-event) on the left sidebar.
2. On the errors page, querying by stream ID is supported. You can query the push errors in the last 7 days, and the data within the query period is less than 3 hours.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2b5a1ec70e0411efa072525400b3b5af.png)

## Primary/Backup Streams Query

1. Select **Monitoring** > [Errors](https://console.tencentcloud.com/live/event/error-event) from the left sidebar to enter the Primary/Backup Streams page.
2. On the Primary/Backup Streams page, querying by stream ID is supported. You can query the primary/backup streams in the past 7 days, and the data within the query period is less than 3 hours.

## ![](https://staticintl.cloudcachetci.com/cms/backend-cms/498017fa0e0411efa24d525400493f3c.png)

## Error Types

Below is a list of errors that may occur during live streaming.

| Number | Error Type |
| --- | --- |
| 1 | The video timestamp moved backwards |
| 2 | The audio timestamp moved backwards |
| 3 | The video timestamp increased notably |
| 4 | The audio timestamp increased notably |
| 5 | Chunk size too big |
| 6 | Two consecutive video frames arrived late |
| 7 | Two consecutive audio frames arrived late |
| 8 | The video codec changed |
| 9 | The audio codec changed |
| 10 | No codec header before a video frame arrived |
| 11 | No codec header before an audio frame arrived |
| 12 | Video header parsing failure |
| 13 | Large Chunk Size |
| 14 | Low video frame rate |
| 15 | Large timestamp interval of audio frames |
| 16 | Large GOp Size |
| 17 | Uncommon audio/video encoding and decoding formats |


---
*Source: [https://www.tencentcloud.com/document/product/267/51202](https://www.tencentcloud.com/document/product/267/51202)*
