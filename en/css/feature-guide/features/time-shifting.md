# Time Shifting

We have recently upgraded the time shifting feature. When you create a time shifting template in the console, you will now be enabling the new time shifting feature. Generate a URL in the required format, and you can use the URL to play content from an earlier time point. API 3.0 is also now available for the time shifting feature. For details, see [Time Shifting APIs](https://intl.cloud.tencent.com/document/product/267/30760). This document shows you how the time shifting feature works and how to make a playback request.

## Must-Knows

- The new time shifting feature currently supports 30,000 concurrent viewers. If you need a higher concurrency, please [submit a ticket](https://console.tencentcloud.com/workorder/category).
- If you enabled authentication for your playback domain and configured an expiration time, the time shifting URL will expire after the specified time.
- To use the [old time shifting feature](https://www.tencentcloud.com/document/product/266/39564?lang=en&pg=) (which pulls content from a VOD domain), you need to submit a ticket. For a better experience, we recommend you use the new time shifting feature.

## How It Works

CSS enables time shifting by saving live streams as TS segments and information about the playback time of each TS segment in the cloud. This feature is often used to replay TV programs or highlights of sports events. Content is distributed to clients over HLS. You can specify the exact playback time by setting the M3U8 request parameters (for details, see [Playback Request](https://www.tencentcloud.com/document/product/267/31565#5b9e1a89-7b22-4a20-b574-bf7b53dd728f)).

## Playback Request

The format of time shifting URL is `http://domain/appname/stream.m3u8`. There are two types of time shifting:

- Playing a specific duration. This is suitable for replaying highlights of sports events.
- Playing from a specific time ago. This is suitable if you want to delay the playback of a live stream.

### Request parameters for playing a specific duration

| Parameter | Description | Required | Example |
| --- | --- | --- | --- |
| txTimeshift | Whether to enable the new time shifting feature (<code>on</code>: Enable). | Yes | txTimeshift=on |
| tsStart | The time-shift start time must be at least 30 seconds earlier than the current time, and the interval between tsStart and tsEnd cannot be less than one TS segment duration and cannot exceed 6 hours. | Yes | tsStart=20121010010101 |
| tsEnd | The time-shift end time, the interval between tsStart and tsEnd cannot be less than one TS segment duration and cannot be more than 6 hours. | Yes | tsEnd=20121010010102 |
| tsFormat | The format of tsStart and tsEnd is `{timeformat}_{unit}_{zone}`Valid values of timeformatunix - unix timestamp. If you use this format, you don’t need to specify zonehuman - Human-readable time, such as “20121010010101”.Valid values of unit:s. s indicates second.zone：Time zones are divided into Eastern, Western, and Central Time Zones (Zero Time Zone).The value range for the Eastern Time Zone is 1 to 12The value range for the Western Time Zone is -12 to -1. | Yes | tsFormat=unix_stsFormat=human_s_8 |
| tsCodecname | For a transcoded stream, set this parameter to the ID of the transcoding template. For original streams or watermarked streams, leave out this parameter. | No | tsCodecname=hd |

#### Request example 1 (Unix timestamp)

```
http://example.domain.com/live/stream.m3u8?txTimeshift=on&tsFormat=unix_s&tsStart=1675302995&tsEnd=1675303025&tsCodecname=test
```

#### Request example 2 (human-readable time)

```
http://example.domain.com/live/stream.m3u8?txTimeshift=on&tsFormat=human_s_8&tsStart=20230202095635&tsEnd=20230202095705&tsCodecname=test
```

### Request parameters for playing from a specific time ago

| Parameter | Description | Required | Example |
| --- | --- | --- | --- |
| txTimeshift | Whether to enable the new time shifting feature (`on`: Enable). | Yes | txTimeshift=on |
| tsDelay | The number of seconds to delay the playback by. | Yes | `tsDelay=30` indicates that playback will start from 30 seconds ago. |
| tsCodecname | For a transcoded stream, set this parameter to the ID of the transcoding template. | No | tsCodecname=2000 |

#### Request example

```
http:://example.domain.com/live/stream.m3u8?txTimeshift=on&tsDelay=30&tsCodecname=test
```

### Authentication parameters

The authentication parameters for time shifting are the same as those for playback. For details, see [Playback Authentication Configuration](https://intl.cloud.tencent.com/document/product/267/31060) (HLS URLs generated in the console are only valid for one day).

### Querying time shifted streams

The **Time Shifting > Time shifting details** page of the console shows a list of time shifted streams. You can click **Details** to view the details of a time shifted stream.
You can also use APIs to query time shifted streams and the details of a specific stream. For details, see the following documents:

- [DescribeTimeShiftStreamList](https://www.tencentcloud.com/document/product/267/53719)
- [DescribeTimeShiftRecordDetail](https://www.tencentcloud.com/document/product/267/53720)


---
*Source: [https://www.tencentcloud.com/document/product/267/31565](https://www.tencentcloud.com/document/product/267/31565)*
