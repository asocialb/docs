# Audio Moderation Notification

If you have configured an audio moderation callback address, the server will return the moderation results in JSON to the specified callback address after the audio moderation is complete. You can then proceed with subsequent file processing operation based on the callback content.

This document describes the notification fields of the callback message sent by Tencent Cloud Streaming Services (CSS) to the user after the audio moderation callback event is triggered.

## Note

- Before reading this document, ensure that you have understood how the callback function is configured and callback messages are received in Tencent CSS. For detailed procedures, see [How to Receive Event Notifications](https://www.tencentcloud.com/document/product/267/38080).
- By default, only potentially non-compliant results will be returned. Compliant results will not be returned.

## Audio Moderation Callback Parameters

### Event Type Parameter

| Event Type | Field Value Description |
| --- | --- |
| Audio moderation | event_type = 315 |

### Common Callback Parameters

| Field Name | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time. It is the UNIX timestamp signifying the expiration of the event notification signature.The default expiration time for message notifications from Tencent Cloud is 10 minutes. If the time designated by the `t` value in a message notification has expired, the notification is deemed invalid, thereby safeguarding against network replay attacks.The format of `t` is a decimal UNIX timestamp, which is the seconds elapsed from midnight of January 1, 1970 (UTC/GMT). |
| sign | string | Security signature for event notification: `sign` = MD5(`key` + `t`)Tencent Cloud concatenates the encrypted **key** and t into a string, and then uses MD5 calculation to obtain the sign value, which is then placed in the notification message. After the notification is received, your backend server can determine whether the sign is correct using the same algorithm, thus confirming whether the message comes from Tencent Cloud's backend. |

> **Note：**You can set the callback key in **Event Center** > [Live Stream Callback](https://console.tencentcloud.com/live/config/callback), which is used for authentication. You are advised to specify this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/5d15eadecb6711f0a93d52540044a08e.png)

### Callback Message Parameters

| Parameter | Required or Not | Data Type | Description |
| --- | --- | --- | --- |
| appid | Required | Number | Business ID. |
| bizid | Optional | Number | Business ID (obsolete). |
| stream_id | Required | String | Stream name. |
| channel_id | Required | String | Channel ID. |
| domain | Required | String | Push domain name. |
| path | Optional | String | Push stream path. |
| HitFlag | Optional | Number | This field is utilized to indicate whether the content under review has triggered the audit model; Values: 0 (Not Triggered), 1 (Triggered). |
| Score | Optional | Number | This field is utilized to return the confidence level under the current tag, with a value range from 0 (lowest confidence) to 100 (highest confidence). |
| SubTag | Optional | String | This field serves as a subordinate secondary label. |
| task_id | Optional | Number | Audio Review Task ID |
| status | Optional | Number | Callback Status Value: 2 (Normal) |
| asr_text | Optional | String | Text transcription. |
| cdn_url | Optional | String | CDN address. |
| duration | Optional | Number | Speech recognition duration (seconds). |
| label | Optional | String | This field is used to return the malicious label with the highest priority in the detection result to indicate the moderation result recommended by the model. You are advised to process different violation types and suggested values according to your business requirements. |
| language_results | Optional | Array of AudioResultDetailLanguageResult | This field returns detection results for a minor language.For specific result content, please see the detailed descriptions of AudioResultDetailLanguageResult data structure.Note:**This field may return null, indicating that there is no valid value available.** |
| moan_results | Optional | Array of MoanResult | Moderation result of vulgar content in the audio; Note:**This field may return null, indicating that there is no valid value available.** |
| recognition_results | Optional | Array of RecognitionResult | Hit recognition labels.Note:**This field may return null, indicating that there is no valid value available.** |
| request_id | Optional | String | Request ID |
| seq | Optional | Number | Audio sequence |
| speaker_results | Optional | Array of AudioResultDetailSpeakerResult | Speaker identification result in the audio.Note:**This field may return null, indicating that there is no valid value available.** |
| sub_label | Optional | String | Sub-label name. If the sub-label is not matched, an empty string will be returned. |
| suggestion | Optional | string | Recommended value. Valid values:Block: content filteringReview: pending re-moderationPass: normal |
| text_results | Optional | Array of TextResult | Dialog content moderation result in the audio.Note:**This field may return null, indicating that there is no valid value available.** |
| data | Optional | Data | Speech recognition result. |

#### AudioResultDetailLanguageResult

Minority language detection result in the audio.

| Name | Type | Description |
| --- | --- | --- |
| Label | String | This field is used to return the corresponding language type information.Note:**This field may return null, indicating that there is no valid value available.** |
| Score | Integer | This parameter is used to return the confidence of the current label. Value range: 0 (lowest confidence) to100 (highest confidence). A larger value indicates a higher possibility that the audio belongs to the current returned language label.Note:**This field may return null, indicating that there is no valid value available.** |
| StartTime | Float | This parameter is used to return the start time of the segment corresponding to the specified language label within the audio file, in the unit of seconds. Note:**This field may return null, indicating that there is no valid value available.** |
| EndTime | Float | This parameter is used to return the end time of the segment corresponding to the specified language label within the audio file, in the unit of seconds.Note:**This field may return null, indicating that there is no valid value available.** |

#### MoanResult

Vulgar content moderation result.

| Name | Type | Description |
| --- | --- | --- |
| Label | String | The value of this field is fixed, which is Moan. If there is no **MoanResult** in the callback result for the audio, there are no relevant violations about moan/panting in this audio.Note:**This field may return null, indicating that there is no valid value available.** |
| Score | Integer | The confidence determined by the machine for the current category. Value range: 0 to 100. A higher score indicates a higher possibility that it belongs to the current category.(Example: Moan 99 indicates that the sample has a high possibility of belonging to the moan/panting category) |
| Suggestion | String | The suggested operation after the results are generated.Recommended value. Valid values:Block: Blocking is recommended.Review: Re-moderation is recommended.Pass: Pass is recommended. |
| StartTime | Float | Violation event start time, in the unit of seconds (s). |
| EndTime | Float | Violation event end time, in the unit of seconds (s). |
| SubLabel | String | This field is used to return the secondary label under the current label (Label).Note:**This field may return null, indicating that there is no valid value available.** |

#### RecognitionResult

Result information list of the recognition category label.

| Name | Type | Description |
| --- | --- | --- |
| Label | String | Possible values include: Teenager, GenderNote:**This field may return null, indicating that there is no valid value available.** |
| Tags | Array of Label | Identifying Tag ListNote:**This field may return null, indicating that there is no valid value available.** |

#### AudioResultDetailSpeakerResult

Speaker recognition result.

| Name | Type | Description |
| --- | --- | --- |
| Label | String | This field returns the detected content type.Note:**This field may return null, indicating that there is no valid value available.** |
| Score | Integer | This field is used to return the confidence level of the moaning detection. Value range: 0 (lowest confidence) to 100 (highest confidence). A larger value indicates a higher possibility that the audio is the speaker's voice print.Note:**This field may return null, indicating that there is no valid value available.** |
| StartTime | Float | This field is used to return the start time of the corresponding speaker's segment within the audio file, in the unit of seconds.Note:**This field may return null, indicating that there is no valid value available.** |
| EndTime | Float | This field is used to return the end time of the corresponding speaker's segment within the audio file, in the unit of seconds.Note: **This field may return null, indicating that there is no valid value available.** |

#### TextResult

Dialog moderation result.

| Name | Type | Description |
| --- | --- | --- |
| Label | String | Negative label:Normal: NormalPorn: PornAbuse: AbuseAd: AdvertisementCustom: Custom dictionaryAnd other types of content that are offensive, unsafe or inappropriate.If there is no **TextResults** returned in the callback result for the audio, there are no relevant violations in this audioNote:**This field may return null, indicating that there is no valid value available.** |
| Keywords | Array of String | Keywords that are matched. If it is empty, the violation is a preset violation type defined by the model.Note:**This field may return null, indicating that there is no valid value available.** |
| LibId | String | Library identifier of the matched keywordNote:**This field may return null, indicating that there is no valid value available.** |
| LibName | String | Name of the matched keyword libraryNote:**This field may return null, indicating that there is no valid value available.** |
| Score | Integer | The confidence determined by the machine for the current category. Value range: 0 to 100. A higher score indicates a higher possibility that it belongs to the current category.(Example: Porn 99 indicates that the sample has an extremely high possibility of being pornographic.)Note:**This field may return null, indicating that there is no valid value available.** |
| Suggestion | String | The suggested operation after the results are generated.Recommended value. Valid values:Block: Blocking is recommended.Review: Re-moderation is recommended.Pass: Pass is recommended.Note:**This field may return null, indicating that there is no valid value available.** |
| LibType | Integer | Type of the custom library. You can view details of custom libraries in the console.Custom Block and Allow LibraryCustom Library |
| SubLabel | String | This field is used to return the secondary label under the current label (Label).Note:**This field may return null, indicating that there is no valid value available.** |
| HitInfos | Array of HitInfo | This field is utilized to return information on violations detected in the text.Note: **This field may return null or an empty array, signifying the absence of any valid values.** |

#### Data

| Name | Type | Description |
| --- | --- | --- |
| asr_tmp_full_results | Array of AsrTmpFullResults | Details of the audio detection result, which may be empty. |

#### AsrTmpFullResults

Details of the audio detection results.

| Name | Type | Description |
| --- | --- | --- |
| appearing_point | Array of Number | Time point of occurrence. |
| confidence | Number | Confidence level. |
| id | String | Text transcription. |
| periods | String | Time period. |
| url | String | Audio URL. |

#### Tag

Recognition label list

| Name | Type | Description |
| --- | --- | --- |
| Name | String | The specific name is determined based on the Label field:When the Label field is Teenager, possible values for Name include: TeenagerWhen the Label field is Gender, possible values for Name include: Male, FemaleNote:**This field may return null, indicating that there is no valid value available.** |
| Score | Integer | Confidence score: 0 to 100. A larger value indicates a greater confidence.Note:**This field may return null, indicating that there is no valid value available.** |
| StartTime | Float | Recognition start offset time, unit: millisecondsNote:**This field may return null, indicating that there is no valid value available.** |
| EndTime | Float | Recognition end offset time, unit: millisecondsNote:**This field may return null, indicating that there is no valid value available.** |

#### HitInfo

Keyword hit position information

| Name | Type | Description |
| --- | --- | --- |
| Type | String | Identifying whether a hit is attributed to the model or a keywordSample Value: Model |
| Keyword | String | Hit keywordsSample Value: hello |
| LibName | String | Custom Dictionary nameSample Value: Test Dictionary1 |
| Positions | Array of Position | Location Information |

#### Position

Identify the location information of the illegal keywords hit

| Name | Type | Description |
| --- | --- | --- |
| Start | Integer | Keyword Starting PositionSample Value: 0 |
| End | Integer | Keyword Termination PositionSample Value: 10 |

### Callback Message Example

```
{    "HitFlag": 1,     "Score": 96,     "SubTag": "XXXsound",     "appid": 12345678,     "asr_text": "provide mobile phone number for easy contact",     "cdn_url": "",     "channel_id": "xxxun01",     "data": {        "asr_tmp_full_results": [            {                "appearing_point": [                    1810089.20,                    1810104.80                ],                 "confidence": 100,                 "create_time": 1685929588,                 "id": "",                 "periods": "00:00:00-00:00:15",                 "url": "https://xxx.Audit-09-46-27.wav"            }        ]    },     "domain": "xxx.cn",     "duration": 10,     "event_type": 315,     "interface": "general_callback",     "label": "Ad",     "language_results": [ ],     "moan_results": [        {            "EndTime": 15,             "Label": "Ad",             "Score": 0,             "StartTime": 0,             "SubLabel": "Contact",             "Suggestion": "Pass"        }    ],     "path": "live",     "recognition_results": [ ],     "request_id": "xxx594-4f4d-a5d0-99cce8b750b4",     "seq": 3232590095,     "speaker_results": [ ],     "status": 2,     "stream_id": "xxxn01",     "sub_label": "Contact",     "suggestion": "Block",     "task_id": xxx36881,     "text_results": [        {            "HitInfos": [                {                    "Keyword": "mobile phone number",                    "LibName": "XXViolationThesaurus",                    "Positions": [                        {                            "End": 16,                            "Start": 13                        },                        {                            "End": 22,                            "Start": 18                        }                    ],                    "Type": "Keyword"                }            ],            "Keywords": ["mobile phone number"],            "Label": "Ad",            "LibId": "",            "LibName": "",            "LibType": 0,            "Score": 100,            "SubLabel": "",            "Suggestion": "Block"        }    ]}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/58643](https://www.tencentcloud.com/document/product/267/58643)*
