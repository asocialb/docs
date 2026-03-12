# Task Result Viewing

### How to Obtain Media Metadata?

Please see [DescribeMediaMetaData](https://intl.cloud.tencent.com/document/product/1041/37461).

### Can I Query Newly Finished Tasks Using `ScrollToken`?

> **Note:**The pagination flag parameter `ScrollToken` is used when you paginate your queries. If it is impossible to query all tasks with one request, the API will return `ScrollToken`, which should be passed in for the next request so that it starts from the record following `ScrollToken`.

### How to Query the Task List?

For detailed directions, see the [DescribeTasks](https://intl.cloud.tencent.com/document/product/1041/33643) API.

### How Are the Tasks Returned Sorted?

The tasks returned are sorted by **creation time**. For details, see [DescribeTasks](https://intl.cloud.tencent.com/document/product/1041/33643).

### How to Add Animated Watermarks?

Convert animated images into APNG format, and add them as watermarks in workflow settings.

### How to Modify a Watermark Template?

For details, see the [ModifyWatermarkTemplate](https://intl.cloud.tencent.com/document/product/1041/33646) API.

### How to Associate MPS with COS Buckets?

When configuring a workflow, select a trigger bucket, and videos uploaded to the selected bucket will be processed automatically. For more information, see [Workflow Management](https://intl.cloud.tencent.com/document/product/1041/33485).

### OCR Results Are Generated for a Video Frame. How Do I Get the Frame in Question?

1. Note the time point when OCR results are generated.
2. Pass the time point to the request parameter of `ProcessMedia`: [MediaProcessTaskInput](https://intl.cloud.tencent.com/document/product/1041/33640) > [SnapshotByTimeOffsetTaskInput](https://intl.cloud.tencent.com/document/product/1041/33690).

### How to Query Statistical Data?

You can log in to the [Media Processing Service Console](https://console.tencentcloud.com/mps/statistics?tab=transcode) and click  **Usage Statistics** . This page offers detailed statistical data.


---
*Source: [https://www.tencentcloud.com/document/product/1041/43058](https://www.tencentcloud.com/document/product/1041/43058)*
