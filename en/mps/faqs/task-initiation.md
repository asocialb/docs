# Task Initiation

### What Should I Do If Automated Triggering Is Enabled in Orchestration, but Tasks Are Not Automatically Initiated?

Possible reasons and troubleshooting methods include:

- **Upload failed**: File upload through a Tencent Cloud COS SDK or in the COS Console failed, and an HTTP error code was returned (e.g., `4XX` or `5XX`). In this case, no COS event notification will be triggered, and MPS will not initiate a transcoding task. **Please check whether the file is successfully uploaded.**
- **Upload succeeded but automatic processing tasks are not triggered** : Possible scenarios include: absence of orchestration, incorrect orchestration settings, etc.  **Please verify and ensure that the orchestration is configured accurately** .

### What Should I Do If Initiating a Task Fails?

Possible reasons and troubleshooting methods include:

- **Incorrect request parameters**: If the API returns an error, please check the API parameters and make sure that the API call is successful.
- **No authorization**: If the API returns a permission-related error, please check whether you have granted MPS permissions to COS and CMQ resources.

### What Should I Do If a Task Was Successfully Initiated but Failed During Processing?

Task failure refers to a case where failure occurs in any type of subtask (such as transcoding, screen capturing, watermarking, intelligent recognition, and intelligent analysis) provided by the Media Processing Service (MPS).
You can determine the error type based on the returned error code and message, as shown below:

- Incorrect source file metadata or unsupported format. Please verify the accuracy of the file's metadata and encoding parameters.
- The configuration of the template parameters is incorrect, unknown errors, etc.

If the error is relevant to the source file, please check the file metadata and encoding parameters. For other error types, please [submit a ticket](https://console.tencentcloud.com/workorder/category).

### Will Having the Trigger Directory and Output Directory as the Same Cause a Loop Trigger?

If the orchestrated trigger directory and output directory are the same file path, it will not cause a loop trigger.

### What is the maximum number of concurrent transcoding channels?

The default limit for concurrent transcoding channels is set at 60. Should you require an increase in this quota, please [submit a ticket](https://console.tencentcloud.com/workorder/category).


---
*Source: [https://www.tencentcloud.com/document/product/1041/33501](https://www.tencentcloud.com/document/product/1041/33501)*
