# Statistics

This article aims to introduce the various statistics pages for push statistics data, enabling users to quickly query statistical data.

> **Note:**The Statistics feature will only record the push data details of the last device logged in to, and does not support scenarios with multiple devices logged in to.

## Regular Push

### Push Records

You can query all push record data for users under this application. It is necessary to specify the time window, Sender ID, and Recipient ID. Querying user push data includes push time, Push ID, push title, and push content; it also supports locating specific push records by searching for push titles or push content.

#### Query conditions

Time window: A specific time period within a specified date, maximum one hour, precise to minutes and seconds, required.

Sender ID: Required.

Recipient ID: Required.

Push Title: Optional.

Push Content: Optional.

#### Query results (Recorded in the last 7 days)

Push Time: The exact time of push reach.

Push ID: The unique ID of the push message, which can be used to locate the full push link situation of this push in the troubleshooting tool.

Push Title: Push display title.

Push Content: Push display content.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/223cbbbbbc5a11ef928f525400d5f8ef.png)

### Push Data

The statistics display various push metrics data of the application in recent days, mainly including an overview of yesterday's push, push data conversion funnel for multi-type time intervals, supports viewing classified by vendor dimensions, and details of daily push metrics data.

#### Yesterday's Push Overview Metrics Data

Includes the number that can be sent, the number sent, the number reached, the number of clicks, the actual delivery rate, the reach rate, the click-through rate.

#### Time Range

Supports yesterday, the last 7 days, the last 30 days, and specified time window types.

#### Push Data Conversion Funnel

Includes the dimensions of sendable quantity, sent quantity, reached quantity, and clicked quantity.

#### Viewing by a vendor dimension ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5459b9dabc5a11ef928f525400d5f8ef.png)

Support viewing by all vendor categories.

## Push to All/Tag/Specified UserID

### Push Records

You can query all push record data sent to users under the application, specifying the time window for the query. The user push data includes push time, task ID, and push request content. It also supports searching and locating specific push records by push content.

#### Query conditions

Time window: A specific time period within a specified date, up to 7 days, precise to minutes and seconds, required.

Push Content: Optional.

#### Query results (Recorded in the last 7 days)

Push Time: The exact time of push reach.

Task ID: The unique ID of the push message, which can be used to locate the full push notification link status in the troubleshooting tool.

Push Content: The detailed data in JSON format of the push.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9a9c0ab1bc5a11efb9aa5254009f2522.png)

### Push Data

The statistics display various push metrics data of the application in recent days, including the features page and the meaning of the metric data, same as standard push.

#### Yesterday's Push Overview Metrics Data

Includes the number that can be sent, the number sent, the number reached, the number of clicks, the actual delivery rate, the reach rate, the click-through rate.

#### Time Range

Supports yesterday, the last 7 days, the last 30 days, and specified time window types.

#### Push Data Conversion Funnel

Includes the dimensions of sendable quantity, sent quantity, reached quantity, and clicked quantity.

#### Support viewing by vendor dimension

Support viewing by all vendor categories.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a7bac1e6bc5a11efb9aa5254009f2522.png)

#### Task ID

All-staff/Tag Push supports viewing the detailed metrics data and details of a single push by Task ID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/dd14b8f0bc5a11ef965e525400a6537a.png)

## Metrics Data Calculation Method

**Sendable Quantity:** The total number of valid devices that can be reached by filtering the target population selected for the push task (when a device is online and switches to the background, both online and offline pushes will be sent simultaneously, and it will be counted as two devices, not deduplicated).

**Sent Quantity:** The total number of valid devices that have been successfully distributed through the Instant Messaging (Chat) Channel and the Manufacturer Channel among the valid devices that can be sent (when a device is online and switches to the background, both online and offline pushes will be sent simultaneously, and it will be counted as two devices, not deduplicated).

**Reached Quantity:** The total number of receipts successfully received by the device terminal through the Instant Messaging (Chat) Channel and the Manufacturer Channel (when a device is online and switches to the background, both online and offline pushes will be sent simultaneously, and it will be counted as two devices, not deduplicated).

**Clicked Quantity:** The total number of receipts for clicks after the push is successfully displayed.

**Actual Delivery Rate:** Sent Quantity / Sendable Quantity * 100%.

**Reach Rate**: Reached Quantity / Sent Quantity * 100%.

**Click-through Rate:** Clicked Quantity / Reached Quantity * 100%.

## Push Statistics Support Status by Manufacturer

| **Manufacturer** | **Reach** | **Click** |
| --- | --- | --- |
| Huawei | Supported ([Requires configuration of Acknowledgement](https://www.tencentcloud.com/zh/document/product/1047/60552#daa658b0-1ac0-44a8-8a47-7ec8822ebe82)) | Supported ([Requires integration of push service](https://www.tencentcloud.com/document/product/1047/60534)) |
| HONOR | Supported ([Requires configuration of Acknowledgement](https://www.tencentcloud.com/zh/document/product/1047/60552#daa658b0-1ac0-44a8-8a47-7ec8822ebe82)) | Supported ([Requires integration of push service](https://www.tencentcloud.com/document/product/1047/60534)) |
| vivo | Supported ([Requires configuration of Acknowledgement](https://www.tencentcloud.com/zh/document/product/1047/60552#daa658b0-1ac0-44a8-8a47-7ec8822ebe82)) | Supported ([Requires integration of push service](https://www.tencentcloud.com/document/product/1047/60534)) |
| OPPO | Supported | Supported ([Requires integration of push service](https://www.tencentcloud.com/document/product/1047/60534)) |
| Mi | Supported | Supported ([Requires integration of push service](https://www.tencentcloud.com/document/product/1047/60534)) |
| Meizu | Supported ([Requires configuration of Acknowledgement](https://www.tencentcloud.com/zh/document/product/1047/60552#daa658b0-1ac0-44a8-8a47-7ec8822ebe82)) | Supported ([Requires integration of push service](https://www.tencentcloud.com/document/product/1047/60534)) |
| FCM | Not supported. | Supported ([Requires integration of push service](https://www.tencentcloud.com/document/product/1047/60534)) |
| Apns | Supported ([Requires integration of push service](https://www.tencentcloud.com/zh/document/product/1047/60552#daa658b0-1ac0-44a8-8a47-7ec8822ebe82)) | Supported ([Requires integration of push service](https://www.tencentcloud.com/document/product/1047/60534)) |


---
*Source: [https://trtc.io/document/60540](https://trtc.io/document/60540)*
