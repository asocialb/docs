# Real-Time Monitoring

The real-time data monitoring capability offers a real-time, multi-dimensional, and visualized display of the performance of TRTC applications, allowing you to monitor your applications in real time and detect and troubleshoot problems in a timely manner.

> **Note:**Data monitoring became a paid service on November 1, 2022. The default edition is free. You can purchase the [paid edition](https://console.trtc.io/subscription/buy/dashboard?packType=standard) to unlock more features.

## Features

Real-time monitoring:

- Statistics including the number of online rooms and users are collected and analyzed automatically at 10-second update intervals.
- The real-time monitoring data is linked to the statistics on call details, making it easy for you to troubleshoot user-related issues.
- Data is displayed in a visualized way from multiple dimensions. You can view statistics at a specific time point.

## Directions

1. Log in to the [Tencent RTC Console > Data Monitoring > Real-Time Monitoring](https://console.trtc.io/realtime-monitor) on the left sidebar. If you havenât activated the data monitoring service yet, activate it first.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/4f955f45d4d911f0a73852540099c741.png)

2. Select an application (`SDKAppID`) to monitor. Please note that you have to wait for about 10 minutes after an application is created before you can view its data.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/df3bd8ea9a4811eea869525400c26cb9.png)

### Overview

- The data on the real-time monitoring page is updated every 20 seconds (you can find the last updated time next to **Latest data**).
- **Select application**: Select an application to view the data of all rooms under the application.
- **Pause data**: Click **Pause data** to lock data at the current time, and click **View latest data** to unlock it.

### Latest data

The **Latest data** section shows online users, abnormal users, online rooms, video stutter rate, and audio stutter rate in the last 20 seconds. For details, see [monitoring indicators](#index). The data is updated every 20 seconds.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/09f272ea9a4911ee8964525400321be2.png)

### Details

The **Details** section shows data for five different scale- and quality-related indicators. You can pause the data at the current time.

- **Time state**

Users can switch to the paused state or the latest state by clicking the button **Pause data** / **View latest data**, or switch to the paused state by double clicking the node in the image. In the locked state, the data will be fixed at a specific moment; in the latest state, it's updated every 20 seconds.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c389c5219a4911ee8964525400321be2.png)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c71cc7989a4911ee8964525400321be2.png)

- **Scale indicators**
This area uses line charts to show the number of online users (abnormal users) and rooms of the selected application in the last 64 minutes. The data is updated every 10 seconds. You can hover over anywhere on the line charts to view data at a specific time point and double-click a chart to pause data at the current time.
- **Quality indicators**
This area uses line charts to show the average video and audio stutter rate and number of abnormal users in the last 64 minutes across all rooms of the selected application. The data is updated every 10 seconds. You can hover over anywhere on the line charts to view data at a specific time point and double-click a chart to pause data at the current time.

Example: The following image shows part of the page in a paused state.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/53d04cb29a4a11eea869525400c26cb9.png)

### Room data

This area shows the Room ID, Online users, Abnormal users, Video stutter rate, Audio stutter rate, and Operation of active rooms.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/989d4549a61d11ee9fd6525400bb593a.png)

- **Pause data:**Support pause data to observe the room details at a specific time point, users can click the button **Pause data**to switch to the pause state, and click again to return to the latest state.
- **Download room data**: Click **Download room data** to download the xlsx format file of room data at the current time.
- **Abnormal** **room data**: Click **Exception** option under Operation field, user can view the abnormal room data, including 8 fields: Room ID, User ID, Exception, Region, Network, Device, SDK Version, ISP. user can filter the 8 dimensions to search for the abnormal data.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1cb9de759a5811ee8964525400321be2.png)

- **Call details**: Click **Call Details** option under Operation field to view the call quality data of users in a room. See [Call details](https://www.tencentcloud.com/document/product/647/39070) for more description.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b0e28a95a61d11eeae9a525400c26da5.png)

In the actions above, Download room data, Abnormal room data and Call details will pause data at the current time. To resume viewing the latest data, click **View latest data** next to **Details**.

### Multidimensional data

- This area shows data from different dimensions such as region, network, device, SDK version, and ISP.
- Support pause data to observe information at a specific point in time.
- You can also download the data from this area.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/085efb289a5911eeb6c6525400e46040.png)

## Key Indicators

### Scale indicators

| Indicator | Description |
| --- | --- |
| Online users | The total number of users who entered the rooms of the selected application in the past 10 seconds. A user who entered multiple rooms is counted multiple times. A user who entered the same room multiple times is counted only once. |
| Online rooms | The total number of rooms that were entered by users in the past 10 seconds |
| Abnormal users | The total number of abnormal users (counted by user IDs) in the rooms of the selected application in the past 10 seconds. Abnormal users are users who encountered an exception.Exceptions: no audio, abnormal video frame rate, high CPU usage. |

### Quality indicators

| Indicator | Description |
| --- | --- |
| Video stutter rate | Stuttering duration (any stutter that lasts for 600 ms or longer)/Total video duration x 100%, updated every 10 seconds |
| Audio stutter rate | Stuttering duration (any stutter that lasts for 200 ms or longer is counted)/Total audio duration x 100%, updated every 10 seconds |
| Video stutter severity | Low: [0.00% - 5.00%) (green). Moderately high: [5.00%ï¼10.00%) (yellow). High: â¥ 10.00% (red). |
| Audio stutter severity | Low: [0.00% - 3.00%) (green). Moderately high: [3.00% - 5.00%) (yellow). High: â¥ 5.00% (red). |

## RESTful APIs

You can also use the RESTful APIs we provide to query real-time monitoring data.

> **Note:**Only users who have activated the **Standard** edition of the dashboard can use the RESTful APIs.


---
*Source: [https://trtc.io/document/52069](https://trtc.io/document/52069)*
