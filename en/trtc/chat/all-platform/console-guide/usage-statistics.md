# Usage Statistics

The Chat console provides you with data statistics and analysis features. You can view app data such as user base, message activity, group size, and real-time monitoring data.

> **Note:**Normally, the data is updated at 10:00 every morning. In the event that the data is 0 or not updated, check whether the SDKAppID produced relevant data (for example, whether there are new registered users) in the specified period. If data was produced but not updated, just wait a while for it to be updated.

## Daily Statistics

Log in to the [Chat console](https://console.trtc.io), select **Chat >**[**Statistics**](https://console.trtc.io/chat/data) in the left sidebar, and **select the target application** at the top.

### User base

1. On the **Daily Statistics** page, click the **User Base** tab.
2. In the overview area, you can view the following data:
  - Peak MAU of the current month: the peak MAU of the current month as of yesterday. This data is 0 on the first day of every month.
  - Cumulative number of users as of yesterday: the cumulative number of UserIDs registered with the SDKAppID as of yesterday.
  - Number of new registered users yesterday: the number of new UserIDs registered with the SDKAppID yesterday.
3. Select 7 days, 14 days, or 30 days, or specify a period.
4. In the data trend area, you can view the **MAU and New Users** or **Total Registered Users** chart for the selected period.
5. In the data details area, you can view the data of each day for the selected period, including MAU, MAU (day-over-day), total users, total users (day-over-day), new registered users, and new registered users (day-over-day). You can also export these data by clicking **Export as CSV**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c7af494cb4311f0a4a55254001c06ec.png)

### Message activity

1. On the **Daily Statistics** page, click the **Message Activity** tab.
2. In the overview area, you can view the following data:
  - Number of one-to-one messages yesterday: the total number of C2C chat upstream messages under the SDKAppID yesterday.
  - Number of group messages yesterday: the total number of upstream messages in private group, public group, and chat room chats under the SDKAppID yesterday.
3. Select 7 days, 14 days, or 30 days, or specify a period.
4. In the data trend area, you can view the **C2C** or **Ordinary Group** message count charts for the selected period.
5. In the data details area, you can view the data of each day for the selected period, including message count, message count (day-over-day), message senders, message senders (day-over-day), offline pushes, and offline pushes (day-over-day). You can also export these data by clicking **Export as CSV**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5ad5dfaacb4411f09e745254007c27c5.png)

### Group size

1. On the **Daily Statistics** page, click the **Group Scale** tab.
2. In the overview area, you can view the **Current Month's Peak Groups** data, which is the peak group count of the current month as of yesterday under the SDKAppID. This is 0 on the first day of every month.
3. Select 7 days, 14 days, or 30 days, or specify a period.
4. In the data trend area, you can select a data item to view the trends of **New**, **Total**, or **Active** groups within the selected time range.
5. In the data details area, you can view the data in each day for the selected period, including new groups, new groups (day-on-day), active groups, active groups (day-on-day), peak group count, and peak group count (day-on-day). You can also export these data by clicking **Export as CSV**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/622cabbfcb4411f0a7775254005ef0f7.png)

## Real-Time Monitoring

> **Note:**The real-time monitoring feature is in beta testing and is still being updated in iteration mode. If you have any feedback or suggestions, [submit a ticket](https://console.tencentcloud.com/workorder/category?level1_id=29&level2_id=40&source=0&data_title=%E5%8D%B3%E6%97%B6%E9%80%9A%E4%BF%A1%20IM&level3_id=237&radio_title=%E7%99%BB%E5%BD%95%E5%8F%8A%E5%A4%9A%E7%AB%AF%E5%9C%A8%E7%BA%BF%E9%97%AE%E9%A2%98&queue=3235&scene_code=27293&step=2).

1. In the left sidebar, select **Chat >**[**Monitor**](https://console.trtc.io/chat/monitor), and **select the target application** at the top.
2. In the overview area, you can view **Current Online Users**, **One-to-One Messages Today**, **Ordinary Group Messages Today**, and **Audio-Video Group Messages Today**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8f2f7e66cb4411f0aedb525400454e06.png)

3. In the detailed monitoring data area, data of the 24 hours of the natural day is displayed on the timestamp by default. When the mouse cursor points to the data chart area, you can use the scroll wheel to zoom in the timestamp to view details, drag the timestamp left and right to view the data before and after the time, and click the legend below the timestamp to hide or show the corresponding value in the chart.
  - In the login monitoring area, you can view the login times and login success rate of each client.

> **Note:**Currently, only the login data reported by 4.8.10 or later Chat SDKs for iOS, Android, Windows, and macOS will be displayed. You are advised to upgrade to the [latest version of SDK](https://intl.cloud.tencent.com/document/product/1047/33996).

  - In the message monitoring area, you can view the number of one-to-one or group messages sent by each client and the message sending success rate.

> **Note:**Currently, only the login data reported by 4.8.10 or later Chat SDKs for iOS, Android, Windows, and macOS will be displayed. You are advised to upgrade to the [latest version of SDK](https://intl.cloud.tencent.com/document/product/1047/33996). Currently, the web SDK does not support collecting message statistics by chat type.

  - In the callback monitoring area, you can view the number of callbacks and the callback success rate.
  - In the RESTful API monitoring area, you can view the number of RESTful API requests and the request success rate.
  - In the offline push monitoring area, you can view the number of offline push times and the push success rate.


---
*Source: [https://trtc.io/document/34579](https://trtc.io/document/34579)*
