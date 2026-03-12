# Live Broadcasting Image Audit Event Notification

If you have configured an image moderation callback address, the server will return the moderation results in JSON to the specified callback address after the image moderation is complete. You can then proceed with subsequent file processing operation based on the callback content.

This document describes the notification fields of the callback message sent by Tencent Cloud Streaming Services (CSS) to the user after the image moderation callback event is triggered.

## Note

- You need to understand how to configure callbacks and how you will receive messages via Tencent Cloud CSS before reading this document. For more information, see [How to Receive Event Notifications](https://intl.cloud.tencent.com/document/product/267/38080).
- By default, only potentially non-compliant results will be returned. Compliant results will not be returned.
- It is recommended that you employ the type, score, and suggestion parameters from the callback message to moderate non-compliant images. The moderation system does not provide 100% accuracy, so a few images may be identified as potentially non-compliant or incorrectly identified. You can determine whether manual check is required based on the actual application scenario.
- The image moderation service has been upgraded, and some callback message parameters have been adjusted. You are advised to refer to the latest version and the following parameter description. To ensure compatibility with old versions for users, we will still call back some parameters that are currently not used to the receiving server, including: tid, abductionRisk, confidence, normalScore, hotScore, pornScore, terrorScore, polityScore, illegalScore, similarScore, abuseScore, teenagerScore, adScore, and customScore.

## Image Moderation Callback Parameters

### Event Type Parameter

| Event Type | Parameter Value |
| --- | --- |
| Image moderation | event_type = 317 |

### Common Callback Parameters

| Parameter | Type | Description |
| --- | --- | --- |
| t | int64 | Expiration time, which is the Unix timestamp when the event notification signature expires.The default validity period of a message notification from Tencent Cloud is 10 minutes. If the time specified by the `t` value in a message notification has elapsed, then this notification is considered invalid, thereby preventing network replay attacks.The format of `t` is a decimal Unix timestamp, i.e., the number of seconds that have elapsed since 00:00:00 (UTC/GMT time), January 1, 1970. |
| sign | string | Event notification security signature sign = MD5(key + t).Note: Tencent Cloud concatenates the encryption **key**and `t`, calculates the `sign` value through MD5, and places it in the notification message. When your backend server receives the notification message, it can confirm whether the `sign` is correct based on the same algorithm and then determine whether the message is indeed from the Tencent Cloud backend. |

> **Note：**You can set the callback key in **Event Center** > [**Live Stream Callback**](https://console.tencentcloud.com/live/config/callback), which is used for authentication. We recommend you set this field to ensure data security.![](https://staticintl.cloudcachetci.com/cms/backend-cms/5695bdeacb6711f0b011525400bf7822.png)

### Callback message parameters

| Parameter | Required or Not | Data Type | Description |
| --- | --- | --- | --- |
| streamId | Mandatory | String | Stream name. |
| channelId | Mandatory | String | Channel ID. |
| img | Mandatory | String | Link to the moderated image |
| type | Mandatory | Array | Categories of negative labels with the highest priority in the detection result. For details, see the description of `label`. |
| score | Mandatory | Array | Scores of `type` |
| ocrMsg | Optional | String | OCR result (if any) |
| suggestion | Mandatory | String | Suggestion. Valid values:BlockReviewPass |
| label | Optional | String | Negative label with the highest priority in the detection result(labelResults,objectResults,ocrResults). This is the moderation result suggested by the model. We recommend you handle different types of violations and suggestions based on your business needs. |
| subLabel | Mandatory | String | Sub-label under the negative label with the highest priority in the detection result, such as porn - sexual acts. If no content is sub-labeled, this parameter will be empty. |
| labelResults | Optional | [Array of LabelResult](#labelresult) | Negative label hit details of the category model, including the detected porn content, ads, terrorism content, and politically sensitive content.Note: **This field may return** `null` **, indicating that no valid values can be obtained.** |
| objectResults | Optional | [Array of ObjectResult](#objectresult) | Detection result of the object model, including label name, hit score, coordinates, scenario, and suggested operation regarding objects, advertising logos, QR codes, etc. For details, see the description of the data structure of `ObjectResults`. Note: **This field may return** `null` **, indicating that no valid values can be obtained.** |
| ocrResults | Optional | [Array of OcrResult](#ocrresult) | OCR result, including text coordinates, recognized text, suggested operation, etc. For details, see the description of the data structure of `OcrResults`.Note: **This field may return** `null` **, indicating that no valid values can be obtained.** |
| libResults | Optional | [Array of LibResult](#libresult) | Blocklist/Allowlist moderation result |
| screenshotTime | Mandatory | Number | Screenshot time |
| sendTime | Mandatory | Number | Time when the request was sent, in Unix timestamp format |
| stream_param | Mandatory | String | Push parameters |
| app | Mandatory | String | Push domain name. |
| appid | Mandatory | Number | Application ID |
| appname | Mandatory | String | Push path |

#### LabelResult

Hit result of the category model

| Parameter | Type | Description |
| --- | --- | --- |
| Scene | String | Scenario identified by the model, such as advertising, pornographic, and harmful |
| Suggestion | String | Operation suggested by the system for the current negative label. We recommend you handle different types of violations and suggestions based on your business needs. Returned values:BlockReviewPass |
| label | String | Negative label in the detection result |
| SubLabel | String | Sub-label name |
| Score | Integer | Hit score of the label model |
| Details | [Array of LabelDetailItem](#labeldetailitem) | Sub-label hit details of the category model |

#### LabelDetailItem

Sub-label hit details of the category model

| Parameter | Type | Description |
| --- | --- | --- |
| Id | Integer | ID |
| Name | String | Sub-label name |
| Score | Integer | Sub-label score. Value range: 0-100 |

#### ObjectResult

Object detection result

| Parameter | Type | Description |
| --- | --- | --- |
| Scene | String | Object scenario identified, such as QR code, logo, and OCR |
| Suggestion | String | Operation suggested by the system for the current negative label. We recommend you handle different types of violations and suggestions based on your business needs. Returned values:BlockReviewPass |
| label | String | Negative label in the detection result |
| SubLabel | String | Sub-label name |
| Score | Integer | Sub-label hit score of the scenario model. Value range: 0-100 |
| Names | Array of String | List of object names |
| Details | [Array of ObjectDetail](#objectdetail) | Object detection details |

#### ObjectDetail

Object detection details. When the detection scenario is object, advertising logo, or QR code, it returns the label name, label value, label score, and location information of the detection frame.

| Parameter | Type | Description |
| --- | --- | --- |
| Id | Integer | ID of the object identified |
| Name | String | Object label identified |
| Value | String | Value or content of the object label identified. For example, if the label is QR code ( `QrCode`), this parameter is the URL of the QR code. |
| Score | Integer | Hit score of the object label. Value range: 0-100. For example, `QrCode 99` indicates a high likelihood that the content is a QR code. |
| Location | [Location](#location) | Coordinates (of the top-left corner), dimensions, and rotation of the object detection frame |

#### Location

Coordinates and other information of the detection frame

| Parameter | Type | Description |
| --- | --- | --- |
| X | Float | Horizontal coordinate of the top-left corner |
| Y | Float | Vertical coordinate of the top-left corner |
| Width | Float | Width |
| Height | Float | Height |
| Rotate | Float | Rotation angle of the detection frame |

#### OcrResult

OCR result

| Parameter | Type | Description |
| --- | --- | --- |
| Scene | String | Recognition scenario. Default value: OCR |
| Suggestion | String | Operation suggested by the system for the negative label with the highest priority. We recommend you handle different types of violations and suggestions based on your business needs. Returned values:BlockReviewPass |
| label | String | Negative label in the detection result |
| SubLabel | String | Sub-label name |
| Score | Integer | Sub-label hit score of the scenario model. Value range: 0-100 |
| Text | String | Text |
| Details | [Array of OcrTextDetail](#ocrtextdetail) | OCR details |

#### OcrTextDetail

OCR details

| Parameter | Type | Description |
| --- | --- | --- |
| Text | String | Text recognized (up to **5,000 bytes**) |
| label | String | Negative label in the detection result |
| Keywords | Array of String | Keywords hit under the label |
| Score | Integer | Hit score of the label model. Value range: 0-100 |
| Location | [Location](#location) | OCR text coordinates |

#### LibResult

Blocklist/Allowlist result

| Parameter | Type | Description |
| --- | --- | --- |
| Scene | String | Scenario recognition result of the model. Default value: Similar |
| Suggestion | String | Operation suggested by the system. We recommend you handle different types of violations and suggestions based on your business needs. Returned values:BlockReviewPass |
| label | String | Negative label in the detection result |
| SubLabel | String | Sub-label name |
| Score | Integer | Recognition score of the image search model. Value range: 0-100 |
| Details | [Array of LibDetail](#libdetail) | Blocklist/Allowlist details |

#### LibDetail

Custom list or blocklist/allowlist details

| Parameter | Type | Description |
| --- | --- | --- |
| Id | Integer | ID |
| ImageId | String | Image ID |
| label | String | Negative label in the detection result |
| Tag | String | Custom label |
| Score | Integer | Model recognition score. Value range: 0-100 |

### Callback Message Example

```
{        "ocrMsg": "",        "type": [1],        "socre": [99],        "screenshotTime": 1610640000,        "level": 0,        "img": "http://1.1.1.1/download/porn/test.jpg",        "abductionRisk": [],        "faceDetails": [],        "sendTime": 1615859827,        "suggestion": "Block",        "label": "Porn",        "subLabel": "PornHigh",        "labelResults": [{                "HitFlag": 0,                "Scene": "Illegal",                "Suggestion": "Pass",                "Label": "Normal",                "SubLabel": "",                "Score": 0,                "Details": []        }, {                "HitFlag": 1,                "Scene": "Porn",                "Suggestion": "Block",                "Label": "Porn",                "SubLabel": "PornHigh",                "Score": 99,                "Details": [{                        "Id": 0,                        "Name": "PornHigh",                        "Score": 99                }, {                        "Id": 1,                        "Name": "WomenChest",                        "Score": 99                }]        }, {                "HitFlag": 0,                "Scene": "Sexy",                "Suggestion": "Pass",                "Label": "Normal",                "SubLabel": "",                "Score": 0,                "Details": []        }, {                "HitFlag": 0,                "Scene": "Terror",                "Suggestion": "Pass",                "Label": "Normal",                "SubLabel": "",                "Score": 0,                "Details": []        }],        "objectResults": [{                "HitFlag": 0,                "Scene": "QrCode",                "Suggestion": "Pass",                "Label": "Normal",                "SubLabel": "",                "Score": 0,                "Names": [],                "Details": []        }, {                "HitFlag": 0,                "Scene": "MapRecognition",                "Suggestion": "Pass",                "Label": "Normal",                "SubLabel": "",                "Score": 0,                "Names": [],                "Details": []        }, {                "HitFlag": 0,                "Scene": "PolityFace",                "Suggestion": "Pass",                "Label": "Normal",                "SubLabel": "",                "Score": 0,                "Names": [],                "Details": []        }],        "ocrResults": [{                "HitFlag": 0,                "Scene": "OCR",                "Suggestion": "Pass",                "Label": "Normal",                "SubLabel": "",                "Score": 0,                "Text": "",                "Details": []        }],        "streamId": "teststream",        "channelId": "teststream",        "stream_param": "txSecret=40f38f69f574fd51126c421a3d96c374&txTime=5DEBEC80",        "app": "5000.myqcloud.com",        "appname": "live",        "appid": 10000,        "event_type": 317,        "sign": "ac920c3e66**********78cf1b5de2c63",        "t": 1615860427}
```


---
*Source: [https://www.tencentcloud.com/document/product/267/38084](https://www.tencentcloud.com/document/product/267/38084)*
