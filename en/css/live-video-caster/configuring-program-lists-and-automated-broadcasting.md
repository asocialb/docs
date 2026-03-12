# Configuring Program Lists and Automated Broadcasting

Live Video Caster (LVC) allows you to create schedules to configure scheduled broadcasting. This enables input sources or layouts to be published in a planned way.

## Prerequisites

- You have completed the steps in [Adding Input Sources](https://www.tencentcloud.com/document/product/267/58532).
- You have completed the steps in [Directing and Editing](https://www.tencentcloud.com/document/product/267/58531).

## Configuring a Schedule

### Creating a Schedule

1. In the [Live Video Caster](https://console.tencentcloud.com/live/caster?rid=5) list, find the target caster and click its **ID** or click **Open** on the right to enter the caster editing page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/92dad179dc8611f08d525254001c06ec.png)

2. Select **Schedule**, click **Create schedule**, and proceed with the following configurations:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3903f5cf6d2111f087e15254005ef0f7.png)

| Configuration Item | Description |
| --- | --- |
| Schedule name | Enter the schedule name, which can consist of up to 10 characters. |
| Start time | Select the start time of the schedule, which should be later than the time the schedule is saved. If scheduled broadcasting is enabled, at the start time, LVC automatically turns on the main monitor (PGM) to start streaming and billing begins. |
| End time | Select the end time of the schedule, which must be later than the start time and not exceed the expiration time of the caster. If scheduled broadcasting is enabled, at the end time, LVC automatically stops the PGM to stop streaming, and billing ends. |
| Switch audio and video together | The Switch audio and video together feature is enabled by default. You can choose to manually disable this feature based on your business needs.If it is enabled, the audio/video switches accordingly when programs in the schedule are switched. If it is disabled, you need to select an input source as the schedule background audio. The background audio will always play regardless of program switches. You can set the audio volume in the soundboard.Changes to the background audio for an ongoing schedule will take effect at the start of the next program. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b8dc2dc4201e11f08ca05254005ef0f7.png)

3. Click **Next** and configure the following items in the **Add program** area:

| Configuration Item | Description |
| --- | --- |
| Program name | Enter a program name, which can consist of up to 10 characters. |
| Stream time | The stream time of the first program must be the same as the schedule's start time. For others, the stream time should be between the schedule's start time and end time. |
| Program type | You can choose pre-configured sources or layouts. |
| Watermark | You can choose up to five watermarks. |
| Text | You can choose up to five texts. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/daf429586d0e11f084fc525400bf7822.png)

4. Click **Add to schedule** to add the program. You can add multiple programs to a single schedule.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f76b4f736d0e11f0b9a25254007c27c5.png)

5. After adding programs, click **Save** to complete the creation of the schedule.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/38ed8d176d0f11f081ce52540044a08e.png)

> **Note:**The stream time you set for an inserted program should be later than the current time.

### Editing a Schedule

1. In the [Live Video Caster](https://console.tencentcloud.com/live/caster?rid=5) list, find the target caster and click its **ID** or click **Open** on the right to enter the caster editing page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/91c35e61dc8211f0a4f35254007c27c5.png)

2. Select a successfully created schedule, and click **Edit** on the right to enter the schedule editing page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cbdeb7656d0f11f09f3d52540099c741.png)

> **Note:**Expired schedules cannot be edited.If scheduled broadcasting is enabled, the ongoing schedule's start time cannot be changed, though the end time can be changed.Click **Schedule** to navigate to the ongoing program.

3. Click**Edit**on the right side of Schedule.
  3.1. The schedule live broadcast start time and live broadcast end time can be modified.
  3.2. The Switch audio and video together feature is enabled by default. You can choose to manually disable this feature based on your business needs.
  3.3. Click **Confirm**to save the changes.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1395d34c6d1011f096685254001c06ec.png)

4. Select the program you want to edit, and click **Edit** on the right to edit the program.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4c53fc7a6d1011f087e15254005ef0f7.png)

5. Select the program you want to delete, and click **Delete** on the right to delete the program.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6df4dd7f6d1011f096685254001c06ec.png)

6. Click **Change** to change the program content.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/899908d66d1011f09e39525400454e06.png)

7. After the editing, click **Save** to save the modifications.

### Deleting a Schedule

> **Note:**Schedules cannot be recovered once deleted. **Exercise utmost caution when deleting a schedule**.The system automatically clears each schedule seven days after its end time.

1. On the Schedule tab page, select the target schedule, and click **Delete** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a8d4b1aa6d1011f0bcac525400e889b2.png)

2. Click **Confirm** to delete the schedule.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b9854a4a6d1011f09f3d52540099c741.png)

### Inserting a Schedule

1. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/d74d2a19a46a11eebd03525400c26da5.png) to insert a newly created schedule.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d7727df16d1011f084fc525400bf7822.png)

> **Note:**The time period you set for an inserted schedule should not be earlier than the current time.

2. Repeat the previous step to insert more schedules, or edit or delete existing schedules.

#### Close a Schedule

1. According to your business needs, you can click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/eacadfa86d1011f087e15254005ef0f7.png) to close the schedule.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0132ca5a6d1111f087e15254005ef0f7.png)

2. After closing, you can click **Schedule** in the upper right corner to reopen it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5a74b8846d2111f087e15254005ef0f7.png)

## Configuring Scheduled Broadcasting

### Enabling Scheduled Broadcasting

1. After configuring schedules, you can enable scheduled broadcasting.
2. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/d7506fcfa46a11eebd03525400c26da5.png) to enable scheduled broadcasting. If this function is enabled, LVC will automatically start and stop the PGM output according to the start and end time of the schedules. **The caster will run and incur charges while the PGM output is on**. To stop the current and future billing, ensure that both scheduled broadcasting and PGM are turned off.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/708d1f386d1111f0b9a25254007c27c5.png)

3. Click **Enable**to enable scheduled broadcasting.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3f43e9702d4011ef97da5254007d9c55.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6b443e256d2111f096685254001c06ec.png)

  - **Schedule start time** (when live broadcast starts): If scheduled broadcasting is enabled, at the schedule start time, LVC automatically turns on the PGM to start streaming the first program and billing begins.
  - **Program stream time** (excluding the first program): If scheduled broadcasting and the PGM are both enabled, at the stream time of a program, LVC automatically switches to the program and pushes it to the PGM.

> **Note:**If the PGM or scheduled broadcasting is disabled during a scheduled broadcast, programs will no longer switch automatically.

  - **Schedule end time** (when live broadcast ends): If scheduled broadcasting is enabled, at the schedule end time, LVC automatically stops the PGM and billing ends.

### Disabling scheduled Broadcasting

> **Note:**After scheduled broadcasting is disabled, LVC will no longer start and end live broadcasts according to the schedules' start and end time. To avoid incurring unnecessary charges, ensure that the main monitor (PGM) is also turned off.

1. To end scheduled broadcasting, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/7e4ad3e9dcd811f0a6e3525400e889b2.png).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f38231086d1111f084fc525400bf7822.png)

2. Consider your actual business needs before deciding to stop scheduled broadcasting; proceed with caution. Click **Disable**to stop scheduled broadcasting.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/112284a1202211f0b21052540099c741.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/58528](https://www.tencentcloud.com/document/product/267/58528)*
