# Manage Lexicon

The lexicon comprises two distinct categories: Term Lexicon and Hotword Lexicon. The Term Lexicon facilitates translation rules for specific vocabulary (such as product names, ambiguous terms, and loanwords) in cross-lingual translation scenarios, ensuring translation accuracy. Meanwhile, the Hotword Lexicon significantly enhances speech recognition accuracy for proprietary terms (including brands and technical terminology) by incorporating weighted entries. When encountering homophones with identical tones, the system prioritizes matches with higher-weighted hotwords, thereby enabling more precise and professional live subtitle generation.

## Points of Attention

- The system will identify and replace hot words based on their weight and frequency of occurrence. The larger the weight and the lower the frequency, the higher the probability of being hit.
- Currently, lexicons only support configuring Chinese and English. The lexicon content takes effect 10 minutes after each update.
- Term lexicon can translate the client's terminology in a specific field.

## Creating a Library

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat), and click **Feature Configuration**> **AI Features**> **Subtitle & Simultaneous Interpretation**, then click **Manage Lexicon**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/811a3a3700c911f18e41525400ecee81.png)

2. Click **Create library**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f803b245b3c711f0a6a2525400e889b2.png)

3. In the pop-up window, fill in the configuration information.Category: Default Hotword lexicon (optional Term lexicon). Please refer to the following table for detailed configuration.

Hotword lexicon

Term lexicon

![](https://staticintl.cloudcachetci.com/cms/backend-cms/55fafa3eb3c811f0bd1d5254001c06ec.png)

| Configuration Item | Description |
| --- | --- |
| Category | Hotword lexicon：For hotwords with the same pronunciation and tone, recognize the hotword with the highest weight. |
| Library | The prefix of the library name is always "hotword". It only supports English letters, digits, underscores (_), and hyphens (-), and contains up to 30 characters. |
| Description | Supports Chinese characters, letters, digits, spaces, and _-.The description cannot exceed 100 characters. |
| Direct Import | Toggle this on if you want to import hotwords from a file. Click **Select File**, and then select a file from your computer. Make sure that the file meets the following requirements:File format: TXT.File size: within 100 KB.File encoding: UTF-8 or GBK encoding. |
| Keywords | Add hotwords here.Only Chinese and English hotwords are supported. Each hotword can contain no more than 10 Chinese characters or 30 English characters. Punctuation marks and special characters are not allowed.Multiple hotwords should be separated by commas, and the number of hotwords cannot exceed 1,000.Hotwords and weights should be separated by "\|". For example, "Tencent Cloud\|10,speech recognition\|5,ASR\|10". The hotword weight ranges from 1 to 10. The greater the weight of a hotword, the greater the probability that the hotword can be recognized. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8776d600b3c711f09e195254007c27c5.png)

| Configuration Item | Description |
| --- | --- |
| Category | Term lexicon：Translate domain-specific terms for customers and correct translation results. |
| Library | The library prefix is ​​fixed to "term".It only supports English letters, digits, underscores (_), and hyphens (-), and contains up to 30 characters. |
| Description | Supports Chinese characters, letters, digits, spaces, and _-.The description cannot exceed 100 characters. |
| Language Pair | ​Language Conversion Directions:  Supports bidirectional translation between Chinese and English, including the following conversion options:  Chinese → EnglishEnglish → Chinese |
| Bidirectional | Based on your business requirements, you may choose whether to enable bidirectional translation between Chinese and English.Options: Yes/No (Default value: "Yes") |
| Direct Import | Depending on your actual business needs, you can choose to upload files from your computer or use the Common Vocabulary function.**Select File**If you need to import terminology, you can manually enable the direct terminology import feature. Click "Select File" and select the file to upload from your computer. Please ensure that the uploaded file meets the following requirements:File format: TXT.File size: within 100 KB.File encoding: UTF-8 or GBK encoding.**Common Vocabulary**You can directly select the preset vocabulary. |
| Keywords | Add hotwords here.Multiple terms should be separated by commas, and the number of terms cannot exceed 150. Separate terms in the source language and those in the target language by "\|". For example, “Tencent Cloud\|腾讯云,ASR\|语音识别,P&L\|盈亏,API\|API”Terms are case-sensitive. |

4. Click **Confirm**, and the hotwords are added.

## Viewing a Library

On the [Manage Lexicon](https://console.tencentcloud.com/live/config/subtitle/hot-word) page, click the name of the library you want to view on the left side, and view its detailed information in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/46827bcab3ce11f0bb7b525400bf7822.png)

The information includes the library name, lexicon table ID, last updated time, number of hotwords, and list of hotwords and their weights.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/68c7bd3cb3ce11f0b96752540044a08e.png)

## Modifying a Library

1. On the [Manage Lexicon](https://console.tencentcloud.com/live/config/subtitle/hot-word)page, find the library you want to modify, click **Edit**on the right, and then modify the configuration information of the library in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e66f5e3eb3cf11f099275254005ef0f7.png)

2. Click **Confirm** to save the current template and complete the modification of the custom library.

## Deleting a Library

1. On the [Manage Lexicon](https://console.tencentcloud.com/live/config/subtitle/hot-word) page, find the library you want to delete, and then click **Delete**on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/14e9274db3d011f0a6a2525400e889b2.png)

2. A confirmation box will pop up. Click **OK**to delete the custom library.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cbda10da6e5a11ef92db52540055f650.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/64435](https://www.tencentcloud.com/document/product/267/64435)*
