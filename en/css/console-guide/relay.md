# Relay

If your live streaming source does not have the capability to push streams or if you want to stream on-demand videos, you can use the relay feature to quickly pull content from an existing live streaming source or video and then deliver it to the destination. You don’t need to push streams yourself.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8ea628892a0911ee909c525400cea498.png)

## Prerequisites

- You have activated [CSS](https://intl.cloud.tencent.com/product/css) and logged in to the [CSS console](https://console.intl.cloud.tencent.com/live/livestat).
- You have added a [push domain name](https://intl.cloud.tencent.com/document/product/267/35970) in the console.

## Limits

- You can create up to **200** relay tasks. If your relay business has a substantial volume and you require a larger task quota, contact us by [submitting a service ticket](https://intl.cloud.tencent.com/en/account/login?s_url=https%3A%2F%2Fconsole.intl.cloud.tencent.com%2Fworkorder%2Fcategory), or seek assistance from our business manager.
- The relay feature is charged based on the **duration of relay tasks**. For details, see [Relay](https://intl.cloud.tencent.com/document/product/267/41059).
- CSS is only responsible for pulling and relaying content. **Please make sure that your content is authorized and complies with relevant laws and regulations. In case of copyright infringement or violation of laws or regulations, CSS will suspend its services for you and reserves the right to seek legal remedies.**
- The local relay mode became a paid feature starting from **00:00 on November 23, 2022**. To learn more, see [Extended Features](https://www.tencentcloud.com/document/product/267/51555).
- For relay, when pulling or pushing global streams, you need to set the task region to outside Chinese mainland.
- You can use the relay recording function by binding a cloud streaming recording template, which will generate [recording costs](https://www.tencentcloud.com/document/product/267/39605?has_map=1&lang=en&pg=). The recording templates bound to the relay function only support templates that record the original stream content. To modify the recording template during a relay task, you need to halt the current task for 30 seconds before restarting it, only then can the new recording template take effect.
- After the relay is bound to the transcoding template, the stream will first be pushed to CSS for transcoding, and then forwarded to the objective address of the task. The stream ID style of the push stream used for transcoding is "pp_relay task id", example: pp_12345678. Additional upstream push charges may be incurred. For the upstream push billing rules, please refer to [Upstream Push Billing Instructions](https://www.tencentcloud.com/document/product/267/2818#cfac37fd-ceab-4431-bcc1-cdd283719c91).

## Creating a Task

1. Go to [Relay](https://console.tencentcloud.com/live/tools/relay), and click **Create Task**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/58d2d3d118e111f0b04252540044a08e.png)

2. Enter the basic information:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8f05415818e211f0abe05254005ef0f7.png)

| Configuration Item | Description |
| --- | --- |
| Task Description | Describe the task. |
| Execution Time | By default, it is from `Current Time` to `Current Time + 24 Hours`. The optional range of execution time is any time within one year of the current time, but the duration cannot exceed 30 days.Assuming the current time is  11:34:28 on April  14, 2025, then:The optional time is from  11:34:28 on April  14, 2025 to  11:34:28 on May 14, 2025.The end time cannot exceed  11:34:28 on May 14, 2025. |
| Event Callback Notification | Enter a callback URL for receiving relay event notifications. |

3. Provide the source information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/beaa8ddebdfd11ef928f525400d5f8ef.png)

  - Region: Random (Chinese mainland), North China(Beijing), East China (Shanghai), South China (Guangzhou), Southeast Asia (Singapore), Southeast Asia (Bangkok), Northeast Asia(Tokyo), Northeast Asia (Seoul), Hong Kong/Macao/Taiwan (China) Hong Kong (China), West US(Silicon Valley),East US(Virginia),Europe(Frankfurt).
  - If you select **Random (Chinese mainland)**, the system will assign a region that is nearby.
4. For **Content Type**, you can select **Live streaming**, **Custom video path**, or **Image**.
  4.1. **Live streaming**:
  - Enter a live streaming URL (**only one** is allowed).
  - You can select **Enable backup**.
    - In the event that the primary input source fails to retrieve content, an automatic switch to the backup input source will be initiated for content acquisition. If the backup input source's content type is live streaming, a manual switch back to the primary input source is required once it is restored. However, if the backup input source's content type is a custom video, the system will automatically revert to the primary input source upon completion of the current custom video playback cycle. The backup input source only supports the continuous loop playback of a single video.
    - Application scenarios: The backup source function is ideal for long-term live streaming tasks, preventing black screen viewing due to stream interruption, and providing backup sources and padding. For manual real-time switching of live streaming scenarios, it is recommended to use the cloud director station function.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cf031a1ebdfd11ef96d352540075b605.png)

  4.2. **Custom video path**:
  - You can enter **multiple** (max 30) source URLs.
  - Select **Repeat** to repeat the playback indefinitely or **Specified** to specify the number of times (1-100) to play the content.
  - If you enable local mode, sources in MP4 format will be cached to the **local node** before they are relayed. This ensures smoother and more reliable playback.

> **Note****：**The system will stop a relay task either when the playback count reaches the specified value or when the task reaches its end time.In case of task modification:If you change only the playback count, after the new value is applied, the count will start from 2.If you change both the source URL and playback count, after the new configuration takes effect (whether immediately or after the current playback ends), the count will start from 1.If you change the destination URL, the playback count will be reset.Relaying a locally cached MP4 file will incur additional fees, which are based on the duration of the file relayed.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/eb6c6cb5bdfd11ef96d352540075b605.png)

  4.3. **Image**:
  - Upload an image or enter an image URL. You can click **Preview** to preview the image.
  - Images in JPEG, JPG, PNG, or BMP format are supported. If you enter an image URL, there is no limit on image size. If you upload an image, it cannot exceed 2 MB.
  - The file names of images to be uploaded only support letters, digits, and the following characters: `- ! _ . *`

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e572fd06190a11ef942e525400720cb5.png)

5. You can select **Watermark Configuration** ,**Transcoding Configuration**, and **Recording Configuration**. The configuration methods are as follows:
  5.1. **Watermark Configuration:**

Click

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8a028c82779e11ee8fb05254000e2caf.png)

to enable the watermark configuration. The PNG, JPG, and GIF watermark image formats are supported.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e426e8d4bdff11efb86b525400f69702.png)

    - Set **Watermark Type**. You can select **Custom watermark URL**and**Upload image**.
    - For optimal visual effect, the watermark should be a transparent PNG image, with a file size less than 2 MB.
    - The file names of images to be uploaded only support letters, digits, and the following characters: `- ! _ . *`

Custom watermark URL

Upload image

Select **Custom watermark URL**, Enter the URL of the watermark image in the image address input field. By clicking on **Preview**, you can view the watermark in the preview section.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4c414d58190b11ef8a48525400762795.png)

select **Upload image**, click **Select Image**Upload Watermark Image. The watermark image size supports full-window dimension stretching.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/038ed0e5be0011ef934f52540055f650.png)

    - Configure the preview window size for watermark images:
      - Default dimensions: width 1920px, height 1080px.
      - Dimensional range: 360px to 4096px.
      - You can click the **Update**button on the right to perform automatic verification and synchronize the update of the watermark preview window.
    - Set the display position of the watermark image through the following methods.
      - Drag the image position on the watermark image configuration bar.
      - Configure the display position in the X-axis and Y-axis directions.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/28b2854ebe0111efa28d525400329841.png)

> **Note:**Enter the source information of the content. When the content type is image, the watermark configuration cannot be enabled.Enabling the watermark function will generate [transcoding costs](https://www.tencentcloud.com/document/product/267/39604?lang=en&pg=).When modifying the watermark, it takes effect immediately for live streaming source tasks, and for on-demand video source tasks, it takes effect starting from the next file. Modifying the watermark can cause playback to stutter. Usage scenario: It is recommended to use when relaying to a third-party origin server that does not have a watermark feature. For example, if you relay to CSS, you can use the live watermarking feature of CSS.

  5.2. **Transcoding Configuration**:
    - Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/e217948b190b11efa1975254005ac0ca.png), select to enable the transcoding configuration, select a transcoding template, and click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4f9ad3e1be0111efae1f525400bdab9d.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6d2a532bbe0111efad135254002693fd.png)

> **Note:**Enabling transcoding will incur [live transcoding fees](https://www.tencentcloud.com/document/product/267/39604).After the relay is bound to the transcoding template, the stream will first be pushed to CSS for transcoding, and then forwarded to the objective address of the task. The stream ID style of the push stream used for transcoding is "pp_relay task id", example: pp_12345678. Additional upstream push charges may be incurred. For the upstream push billing rules, please refer to [Upstream Push Billing Instructions](https://www.tencentcloud.com/document/product/267/2818#cfac37fd-ceab-4431-bcc1-cdd283719c91).Turning on, off, or changing the transcoding template will take immediate effect. Modifications to the currently bound transcoding template in the pull task will only take effect after the task is restarted.

  5.3. **Recording Configuration**
    - Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/5ad725d277b911eeb3675254006b5335.png) to enable the recording configuration, select a recording configuration template, and click **Confirm** .

![](https://staticintl.cloudcachetci.com/cms/backend-cms/84eabbe3be0111ef934f52540055f650.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a4d010c5be0111efb0b5525400d5f8ef.png)

    - Select a recording mode. You can select **Record and relay** or **Record only**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c8b4760fbe0111efae1f525400bdab9d.png)

> **Node:**Enabling recording will generate [recording fees](https://www.tencentcloud.com/document/product/267/39605).The recording templates bound to the relay function only support templates that record the original stream content. Templates for watermark streams and transcoding streams are not supported.To modify the recording template during a relay task, you need to halt the current task for 30 seconds before restarting it, only then can the new recording template take effect.If the recording template has been associated, it must first be unbound before being deleted. For unbinding procedures, refer to the [unbinding recording configuration](https://www.tencentcloud.com/document/product/267/34224).

6. Enter a destination URL.
  6.1. Click **Address Generator** to enter the URL generation page.
    - Click **Add** to add destination address 2.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/438702c0190c11efac7f5254007bbd8c.png)

  6.2. Select an existing push domain, enter the `Appname`, `StreamName`, and expiration time, and click **Confirm** to generate a push URL, which will be auto-filled as **Destination Address**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e041ccffbe0111efad135254002693fd.png)

> **Note:**The URL expiration time must be later than the task end time. If you change the destination URL after the task starts, it will stop and restart.

7. Upon completing all configuration details, simply click **Save** to proceed.

## Managing Tasks

### Viewing Task Details

In the [task list](https://console.tencentcloud.com/live/tools/relay), find your task, and click its description/ID to view task details in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7149abdebe0211efb0b5525400d5f8ef.png)

> **Note:**You can click the buttons at the bottom of the pop-up window to **edit the task**, **switch sources**,**restart the task**, or **disable the task**.

### Viewing Task Status

In the [task list](https://console.tencentcloud.com/live/tools/relay), find your task, and click its description/ID to view its execution status in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a5133bbabe0211efbb7252540075b605.png)

| Task Status | Field Value | Description |
| --- | --- | --- |
| Not started | Inactive | The task has not started yet. |
| Valid | Active | The task has started and is executed as expected. |
|  | Inactive | The task has started but is not executed as expected. |
| Disabled | Inactive | The task is disabled. |
| Expired | Inactive | The task has expired. |

### Querying Streaming Data

In the task list, select the successfully created relay task, and click **Streaming data**in the **Operation** column on the right to query the streaming data of the relay task. The event display information includes the event type, content type, time, source IP, target IP, and detailed information.

### ![](https://staticintl.cloudcachetci.com/cms/backend-cms/dcdc6ee0be0211efbb7252540075b605.png)

- The streaming data query page of a relay task allows you to query the data of a single stream in the past seven days, including the video frame rate, video bit rate, audio frame rate, and audio bit rate.
- The interval between the start and end time of the query should not exceed 3 hours.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3139eb71be0311efb86b525400f69702.png)

### Modifying a Task

1. In the [task list](https://console.tencentcloud.com/live/tools/relay), find the task you want to modify, and click **Edit**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/06aed0cfbe0311ef8fa3525400fdb830.png)

2. Modify the task information, and then click **Save**.
  - You cannot change the region or content type.
  - When modifying the task end time, make sure that the destination URL is valid until the task ends. Modifying the destination URL will cause the task to stop and restart.
  - If you change watermark settings for a live streaming source, the modifications will take effect immediately. For an on-demand video source, modifications to watermark settings will take effect starting from the next video. Modifying watermark settings may cause playback to stutter. We recommend you use the watermark feature for relay only if you relay to third-party sites that do not have watermarking capabilities. If you relay to CSS, you can use the live watermarking feature of CSS.
  - The recording templates bound to the relay function only support templates that record the original stream content. To modify the recording template during a relay task, you need to halt the current task for 30 seconds before restarting it, only then can the new recording template take effect.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b2efb278190c11ef8bfe5254002fd0a8.png)

3. In the pop-up window, check the information:
  - Suppose you modified the **start time, end time, and playback count** of a task. You would see the following information in the pop-up window:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e0a1eb25be0311efad135254002693fd.png)

  - If the source URLs for **Custom video path** are changed, you need to select whether to apply the change **After the current video ends** (default) or **Now**. After the changes take effect, relay will restart from the first source URL.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8ea615c62a0911eea27e525400c56988.png)

  - If **Destination Address** is changed, the system will remind you that after you click **Confirm**, the current relay task will **stop and restart**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8ead0af22a0911ee909c525400cea498.png)

4. After checking, click **Confirm**.

### Copying a Task

1. In the [task list](https://console.tencentcloud.com/live/tools/relay), find the relay task you want to copy, and click **Copy**. You will be directed to the task creation page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/175a7f74be0411efbb7252540075b605.png)

2. The information of the copied task will be auto-filled. You can **modify** it as needed.
3. Click **Save** to create a new relay task.

### Restarting a Task

Restarting a task will **not change its status**. An ongoing task will be **restarted from the beginning**. Perform the following to restart a task:

1. In the [task list](https://console.tencentcloud.com/live/tools/relay), find the relay task you want to restart, and click **Restart**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3eef5d99be0411efa28d525400329841.png)

2. In the pop-up window, click **Restart**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4f7528fabe0411efa28d525400329841.png)

### Disabling a Task

If you disable a task, **the task will stop**. You can click **Enable** to start it again. Perform the following to disable a task:

1. In the [task list](https://console.tencentcloud.com/live/tools/relay), find the relay task you want to disable, and click **Disable**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7922398ebe0411efae1f525400bdab9d.png)

2. In the pop-up window, click **Disable**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/86bff3e6be0411efb0b5525400d5f8ef.png)

### Enabling a Task

If you enable a task, **the task will start from the beginning**. Perform the following to enable a task:

1. In the [task list](https://console.tencentcloud.com/live/tools/relay), find the relay task you want to enable, and click **Enable**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b0cbc8cfbe0411efb0b5525400d5f8ef.png)

2. In the pop-up window, click **OK**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c0807dc8be0411efbb7252540075b605.png)

### Deleting a Task

Deleted tasks **cannot be recovered**. Perform the following to delete a task:

1. In the [task list](https://console.tencentcloud.com/live/tools/relay), find the relay task you want to delete, and click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e81e4e96be0411efb86b525400f69702.png)

2. In the pop-up window, click **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f941c07dbe0411efae1f525400bdab9d.png)

### Batch Operations

You can delete, disable, and enable **up to 10 relay tasks** at a time.

1. In the [task list](https://console.tencentcloud.com/live/tools/relay), select the relay tasks you want to delete, disable, or enable.
2. Click **Batch Operation**, and select **Enable**, **Disable**or **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/448af10ebe0511efae1f525400bdab9d.png)

3. In the pop-up window, click **Enable**, **Disable**or **Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/534a1ea6be0511ef8fa3525400fdb830.png)

## Auto-Deleting Expired Tasks

A task expires after its end time. If you have too many relay tasks, you may fail to create new ones. To avoid this, you can enable auto-delete for the system to delete expired tasks automatically at the specified time. Deleted tasks cannot be recovered.

1. Go to [Relay](https://console.tencentcloud.com/live/tools/relay), and click **Set** in the **Expired** area.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/807853ffbe0511efae1f525400bdab9d.png)

2. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/8ea615cb2a0911eea27e525400c56988.png) to enable auto-delete.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8b3a48acbe0511efa28d525400329841.png)

3. Specify a period (1-24 hours) to retain expired tasks before they are deleted.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/961d3149be0511efad135254002693fd.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/42524](https://www.tencentcloud.com/document/product/267/42524)*
