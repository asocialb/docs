# Subtitle & Simultaneous Interpretation

The Subtitle & AI Dubbing​ feature can perform real-time Automatic Speech Recognition (ASR) in live streaming, convert the speech into subtitles, and supports translating into target languages as well as AI dubbing. Currently, this feature provides speech translation services for mutual translation among multiple language types. In practical applications, please choose the appropriate combination of source and target languages according to your business needs and audience profile.

This document describes how to create, modify, and delete subtitle templates through the console.

## Points of Attention

- A template takes effect about 5 to 10 minutes after successfully created.
- There are two ways to use the subtitle & AI dubbing​ feature:
  - Method 1:​ Bind the subtitle & AI dubbing template to a transcoding template, then append the corresponding transcoding template name to the pull-stream URL to obtain the subtitle stream；
  - Method 2:​ Append the pull-stream parameter `SubtitleTemplateName=SubtitleTemplateName` to the end of the pull-stream URL. An example pull-stream URL is as follows:

`http://domain/AppName/StreamName.flv?txSecret=Md5(key+StreamName+hex(time))&txTime=hex(time)&SubtitleTemplateName=subtitletest`

- Live subtitling function is a **premium service**. Utilizing this function will incur [live transcoding](https://www.tencentcloud.com/document/product/267/39604) fees and ASR fees of MPS. Cross-language translation may generate voice translation fees of MPS. For the specific billing rules, please refer to [billing document](https://www.tencentcloud.com/document/product/1041/49204?lang=zh).

## Prerequisites for Use

The CSS service has been activated.

## Creating Subtitle Template

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Choose **Feature Configuration**> **AI Features**>**Subtitle & Simultaneous Interpretation**.

> **Note:**To use **Subtitle & Simultaneous Interpretation** in the**AI ​​Features**, you need to create a service role and authorize the current account role to use the **Media Processing Service** (MPS) and **Cloud Object Storage** (COS) products on first creation.

2. Click **Authorize** to enter the CAM role management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/aa5fc060c9da11f08942525400e889b2.png)

3. On the role management page, click **Authorize**. After completing identity verification, you can authorize Media Processing Service and Cloud Object Storage (COS) and use the Media Processing Service and Cloud Object Storage services normally.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d77acb61c9da11f08942525400e889b2.png)

4. After successful authorization, select the service agreement and click **Start**. The system will automatically activate the Media Processing Service product and Cloud Object Storage (COS), and will redirect you to the Smart Highlight management page.
5. Click **Create template** to enter the Subtitle & Simultaneous Interpretation Template creation page and configure the template as follows:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7e953a9400a011f198c8525400370dda.png)

> **Note:**The font selection for subtitles will vary depending on the  **Subtitle Translation**  and  **Subtitles**  you have selected. Select the appropriate source language type, target language, and subtitles according to your actual needs.

| Configuration Item |  | Description |
| --- | --- | --- |
| Template Name |  | The prefix for the template name is fixed to "subtitle". The template name cannot exceed 30 characters and only supports English letters and digits. |
| Template Description |  | Subtitle template description. It contains up to 100 characters, only supporting letters, digits, underscores, and dashes. |
| Mode |  | The default mode is Subtitles; you can also choose Subtitles and Dubbing. |
| Language |  | The default source language is Chinese. English, Japanese, and Korean are also supported.It is set to "No Selection" by default. Switching to any of other unselected options in the source language is supported. For example, if "English" is selected as the source language, the available options for the target language include: No Selection, Chinese, Japanese, and Korean.Cross-language translation will incur voice translation fees of MPS. ASR fees will be generated without translation. For more details, please see [Content II](https://www.tencentcloud.com/document/product/1041/49204). If you need to translate it into other languages, please [submit a ticket](https://console.intl.cloud.tencent.com/workorder/category) to contact us. |
| Preset styles |  | When preset styles are selected, the system will automatically adapt  **Font Color** ,  **Subtitle Line Count** ,  **Characters per Line** , and  **Margins and Line Spacing** . Currently, the following preset styles are supported: The default option is Small text without bar. You may select Small text without bar, Large text without bar, Small text with bar, or Large text with bar to configure the settings.After selection, the system will automatically set the corresponding subtitle style, which can be modified.Modifying configurations will clear the selected preset styles. |
|  Style Adjustment | Subtitles | Source  is supported by default.  Target  and  Bilingual Subtitle  are also supported.By selecting the three options of  Source language ,  Target language , and  Subtitles , you can achieve subtitle effects in different languages. |
|  | Subtitle Line Count | Options are  **1**  or  **2** .When lines exceed the displayed range, only the latest content will be displayed. |
|  | Characters per line | The value range is 1 - 200.When the Preset styles are set to "Small text without bar" or "Small text with bar," the default number of characters per line is 65.When the Preset styles are set to "Large text without bar" or "Large text with bar," the default number of characters per line is 25.One Chinese character counts as 1, while one English character or number counts as half. The fewer the characters per line are, the larger the font size is. |
|  | Target Font | The font selection for subtitles will vary depending on the  **Subtitle Translation**  and  **Subtitles**  you have selected.You may choose a variety of fonts such as DIN Alternate Bold, Helvetica, or HelveticalnseratLTPro-Roman, or select a custom font according to your service needs.If you need a custom font, click **Custom** to upload the font. The system will display a confirmation box. Before uploading and using the font, check the notice, and then click **OK**. Note that only .ttf files are supported. Before using a custom font, make sure that you have obtained legal authorization, otherwise Tencent Cloud will not bear any legal responsibility arising from the use.The default font color is  **white** , and you can customize the font color according to your preference.When "Subtitles" is set to "Bilingual Subtitle," it supports the configuration of distinct fonts and colors for each language individually. |
|  | Subtitle Background | You can select a preset style or upload a custom background according to your business needs. After selection, you can preview the effect. Custom upload instructions: Upload a file in PNG format, with a file size not exceeding 1MB. |
|  | Dynamic/Steady State Effect | The default setting is **delayed steady-state sentence-by-sentence subtitles.** You can switch it to real-time dynamic subtitles or delayed steady-state word-by-word subtitles.When choosing the Delayed Steady State Subtitles mode, it's necessary to set the latency, with a default value of 10 seconds. Available latency options include 20 seconds, 30 seconds, and 60 seconds.**Note:**When you choose real-time dynamic subtitles, subtitles in live streaming will be dynamically corrected word by word based on changes in speech. When you choose delayed steady-state word-by-word subtitles, the system will delay the display of live streaming based on the set time, but the full-sentence subtitle mode provides a better viewing experience. |
|  | Lexicon |  The Association with Lexicon feature is disabled by default.After enabling the feature of custom hotword lexicons, you need to select the hotword lexicon you want to apply. If you have not created a hotword lexicon, you can click Add to jump to the Manage Lexicon page. For detailed steps, see [Manage Lexicon](https://www.tencentcloud.com/document/product/267/64435#3595e9e7-4a23-4836-b380-ba4edabd416d). |
| Real-Time Interpretation |  | The Real-Time Interpretation feature is disabled by default and will only be displayed when the following conditions are met simultaneously:The selected mode is "Subtitle and Dubbing".The subtitle effect is set to "Delayed steady-state sentence-by-sentence subtitles".The subtitle type is "Target" or "Bilingual Subtitle".**Note:**Note: If this feature is enabled, the system will interpret the source audio to the target audio with the selected voice effect. This feature will incur recognition [fees](https://www.tencentcloud.com/document/product/267/39604?lang=zh&pg=). For billing rules, see [Billing Documentation](https://www.tencentcloud.com/document/product/1041/49204). This feature does not support Korean currently.You can choose between Cloned timbre or Specified timbre based on your specific business needs.Specified timbre：By clicking and dragging the mouse over the relevant language play icon, you can audition the real-time voice translation effects.When the translation language is set to English, Real-Time Interpretation supports the following voice: WeRose.By clicking and dragging the mouse over the relevant language play icon, you can audition the real-time voice translation effects. |
| Preview |  | You can adjust the subtitle display effect by dragging and scaling the position and size of the subtitle content type and subtitle background.Uploading background images, selecting the preview window resolution, and entering the subtitle test content can help you preview subtitle styles. The subtitle effect is for reference only and the test content will not be translated. |

6. Click **Save** to save the current template.

## Binding Transcoding Template

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Choose **Feature Configuration**> **AI Feature**> **Subtitle & Simultaneous Interpretation**.
2. The system allows subtitle templates to bind transcoding templates or adaptive bitrate templates. Both transcoding templates and adaptive bitrate templates have similar subsequent use procedures. A transcoding template serves as an example for description below:
  2.1. Direct association with transcoding templates:
    2.1.1. Associate a transcoding template after it is successfully created: After the successful creation of a [transcoding template](https://www.tencentcloud.com/document/product/267/31071#creating-a-transcoding-template), click **Bind transcoding template** in the upper left corner.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d19a9bd900a011f18e41525400ecee81.png)

    2.1.2. Select **Transcoding template** or **Adaptive bitrate template**according to your actual business requirements, then click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f397170c00a011f1b5c0525400380f7d.png)

  2.2. In order to bind a [playback domain](https://www.tencentcloud.com/document/product/267/31071#binding-a-domain-name) to the corresponding transcoding template, the subtitle effects will be output at the same time when the transcoding stream is obtained subsequently (add _ transcoding template name after the corresponding live stream StreamName to generate a transcoding stream address).

> **Note:**Once the transcoding template is bound, the subtitle function configured in the transcoding template will be synchronously activated.

## Unbinding

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Choose **Feature Configuration**> **AI Features**> **Subtitle & Simultaneous Interpretation**.
2. Select the transcoding template associated with a domain name and click **Unbind**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/13f1493c00a111f18080525400074c32.png)

3. Confirm whether to unbind the current associated domain. Click **Confirm**to unbind it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cf79ee9df64711eea3bf525400fe11be.png)

## Modifying a Template

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Choose **Feature Configuration**> **AI Features** > **Subtitle & Simultaneous Interpretation.**
2. Select the successfully created subtitle template and click **Edit** on the right to go to the template information modification page. Click **Save** to finish the modification.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/24542a4f00a111f18080525400074c32.png)

## Deleting a Template

> **Note:**If the template has already been associated, you must first [unbind](https://www.tencentcloud.com/document/product/267/31071#deleting-a-template) it before you proceed with the deletion process.Note that a template cannot be restored after deleted. Be careful when performing operations.

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat). Choose **Feature Configuration**> **AI Features** > **Subtitle & Simultaneous Interpretation**.
2. Select the successfully created subtitle template and click **Delete** above.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/39e54e4600a111f18e41525400ecee81.png)

3. Confirm whether to delete the current subtitle template, then click **Confirm** to successfully delete it.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/46711b0100a111f183755254001d6acc.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/58144](https://www.tencentcloud.com/document/product/267/58144)*
