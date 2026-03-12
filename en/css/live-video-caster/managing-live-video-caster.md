# Managing Live Video Caster

The Cloud Streaming Services (CSS) console provides the Live Video Caster (LVC) service. This document describes how to configure and use the LVC and how to manage cloud streaming after activating the LVC service.

## Prerequisites

- You have activated the LVC service.
- You have logged in to the [CSS](https://console.tencentcloud.com/live/livestat).

## Creating a Caster

1. Log in to the CSS console, select [Live Video Caster](https://console.tencentcloud.com/live/caster?rid=5) from the left-hand navigation pane.
2. Click **Add caster**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/31347e27dc7811f08a7a52540099c741.png)

3. On the **Add caster** page, set the following parameters:
  3.1. Caster name: Enter a custom name for the caster.
  3.2. Caster description: Enter a description for the caster.
  3.3. Set end time: Enabled by default.
  3.4. End time: Select a time at which the caster will automatically stop.

> **Note:**The caster will stop at the set end time, and the preview, output, recording, and relay functions will all stop at that time.If the end time setting is disabled, the caster will not automatically stop, which will incur unnecessary charges. In this case, you need to manually turn off the live streaming (PGM) to stop the billing.Closing the console page will not stop the billing.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6d974174dc7811f09143525400bf7822.png)

4. Click **Confirm** to complete the creation of the caster.
5. If the end time is set, a dialog box pops up asking for your confirmation. Click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fd9117c3dc7911f08a7a52540099c741.png)

### Opening a Caster

To open the [Live Video Caster Console](https://console.tencentcloud.com/live/caster?rid=5), click **Open** in the operation column of a caster.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/22b2aea3dc7a11f08a7a52540099c741.png)

### Sharing

If you need to share the video caster with collaborators, you can click on **Sharing** in the corresponding director's console operation bar.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2d2fcfe7dc7a11f0a4f35254007c27c5.png)

#### Video Caster Main User Perspective

> **Note:**Users who access the video caster via a shared link will not have their access privileges affected by the primary user.The validity period of the video caster collaboration link is the same as the expiration time set when sharing.

Video Caster supports sharing (Share the broadcasting console collaboration link). Sharing is not possible if the video caster has exceeded its runtime.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/363e9ad4dc7a11f08304525400454e06.png)

#### Collaborator's perspective

1. After receiving the shared link, collaborators can click it to enter the collaboration interface. Please enter your authentication key to log in.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7700b711dc7a11f08d525254001c06ec.png)

2. After logging in with their authentication key, collaborators will be directly taken to the video caster interface. You can view the link expiration time in the upper left corner of the interface.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/82827b20dc7a11f08304525400454e06.png)

### Setting a Caster

1. You can view casters you created in the [Live Video Caster list](https://console.tencentcloud.com/live/caster?rid=5).
2. To modify a caster, click **Set** in the operation column of the caster to enter the caster settings page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/34d99f7adc7b11f0be395254005ef0f7.png)

3. After modifying the caster, click **Confirm** to save the modification.

### Copying a Caster

The copy function allows you to quickly duplicate existing caster instances.

1. Go to the [Live Video Caster Console](https://console.tencentcloud.com/live/caster?rid=5), and choose **More > Copy** in the caster operation column.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4d8d5f13dc7b11f0a4f35254007c27c5.png)

2. The default name of the copied caster is `Copy of xx`. You can customize the name of the caster. Click **Confirm** to complete the copy.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5efd9ea9dc7b11f0a6e3525400e889b2.png)

### Stopping a Caster

When you are finished using a caster, stop running it in a timely manner. When a caster is stopped, the preview, output, recording, and relay tasks will all stop, but all the LVC settings, including the input, layout, output, and relay settings, will be retained.

1. Go to the [Live Video Caster Console](https://console.tencentcloud.com/live/caster?rid=5) and click **Stop** in the caster status column.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7e88d370dc7f11f08a7a52540099c741.png)

2. A dialog box pops up asking whether to stop running the caster. Click **Confirm** to stop the caster.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ead2153d2d3e11ef9bb3525400ab9413.png)

> **Note:**When a caster is stopped, its status changes from ![](https://staticintl.cloudcachetci.com/cms/backend-cms/002a9b24a30811eea869525400c26cb9.png) to ![](https://staticintl.cloudcachetci.com/cms/backend-cms/002c10a3a30811eeb6c6525400e46040.png) and the billing stops.

### Deleting a Caster

If you no longer wish to maintain a caster, you can delete it. Once a caster is deleted, all its configurations will be deleted, and its preview, output, recording, and relay tasks will stop.

1. In the operation column of the caster you want to delete, choose **More > Delete**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9719b27cdc7b11f0a38652540044a08e.png)

2. In the dialog box that pops up, click **Confirm** to delete the caster. The deleted caster is no longer included in the instance management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/aaadbca0dc7b11f0a38652540044a08e.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/58533](https://www.tencentcloud.com/document/product/267/58533)*
