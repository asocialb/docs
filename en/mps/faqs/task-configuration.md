# Task Configuration

### How Do I Receive Callbacks?

The Media Processing Service (MPS) supports callback notification methods based on message queues, cloud functions, and HTTP push.

### What Do I Do If I Do Not Receive Callbacks?

If you successfully uploaded a file but did not receive a notification containing the file transcoding result after a certain amount of time, possible reasons include:

- The workflow was not set up correctly. Please check the workflow settings.
- If you initiated the transcoding task through an API and the call was successful, you can use the [DescribeTaskDetail API](https://intl.cloud.tencent.com/document/product/1041/33497) to query the task progress.
- Message backlog in the task queue can cause prolonged processing or other service exceptions. You can [submit a ticket](https://console.tencentcloud.com/workorder) to query your queue status.

### How do I set up callback?

For further details, please refer to [Configuring Event Callback Notification](https://www.tencentcloud.com/document/product/1041/58242#.E4.BA.8B.E4.BB.B6.E9.80.9A.E7.9F.A5.E9.85.8D.E7.BD.AE).

### Is there a Fee Associated with Using Callbacks?

- For CMQ-related usage and fee information, please see [CMQ Cost Description](https://www.tencentcloud.com/document/product/406/38676).
- For information on the usage and pricing of Serverless Cloud Functions (SCF), please refer to the [SCF Billing Overview](https://intl.cloud.tencent.com/document/product/583/17299).
- The HTTP push method is currently free of charge.

### How to Configure Automatic Trigger Tasks?

Upon completion of the orchestration, navigate to the

**Orchestration Management> VOD Orchestration**

page. By clicking on the provided link

![](https://staticintl.cloudcachetci.com/cms/backend-cms/051466b23cdd11efb958525400f69702.png)

, you can activate the automatic trigger feature.


---
*Source: [https://www.tencentcloud.com/document/product/1041/33502](https://www.tencentcloud.com/document/product/1041/33502)*
