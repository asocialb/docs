# API Category

## Processing Task Initiation APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [BatchProcessMedia](https://www.tencentcloud.com/document/api/1041/70403) | Enters multiple video URLs and initiates multiple tasks | 20 |
| [ProcessMedia](https://www.tencentcloud.com/document/api/1041/33640) | Starts a media processing task | 100 |
| [ProcessLiveStream](https://www.tencentcloud.com/document/api/1041/33641) | Initiates a live stream processing task | 100 |
| [ProcessImage](https://www.tencentcloud.com/document/api/1041/66929) | Initiates image processing | 20 |
| [EditMedia](https://www.tencentcloud.com/document/api/1041/37460) | Edits video | 20 |
| [DescribeMediaMetaData](https://www.tencentcloud.com/document/api/1041/37461) | Gets media metadata | 20 |
| [ExtractBlindWatermark](https://www.tencentcloud.com/document/api/1041/74705) | Extracts the digital watermark for a video | 20 |
| [RecognizeAudio](https://www.tencentcloud.com/document/api/1041/77359) | Recognizes audio | 5 |
| [SyncDubbing](https://www.tencentcloud.com/document/api/1041/77775) | Generates dubbing synchronously. | 20 |

## Task Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeBatchTaskDetail](https://www.tencentcloud.com/document/api/1041/70402) | Queries the details of a multi-input task | 20 |
| [DescribeTaskDetail](https://www.tencentcloud.com/document/api/1041/33644) | Queries task details | 100 |
| [DescribeTasks](https://www.tencentcloud.com/document/api/1041/33643) | Gets the task list | 100 |
| [ManageTask](https://www.tencentcloud.com/document/api/1041/37462) | Manages task | 20 |
| [DescribeImageTaskDetail](https://www.tencentcloud.com/document/api/1041/70401) | Queries the image processing task details | 100 |

## Transcoding and Enhancement Template APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateTranscodeTemplate](https://www.tencentcloud.com/document/api/1041/33671) | Creates a transcoding template | 100 |
| [CreateAdaptiveDynamicStreamingTemplate](https://www.tencentcloud.com/document/api/1041/37469) | Creates adaptive bitrate streaming templates | 20 |
| [DeleteTranscodeTemplate](https://www.tencentcloud.com/document/api/1041/33663) | Deletes a transcoding template | 100 |
| [DeleteAdaptiveDynamicStreamingTemplate](https://www.tencentcloud.com/document/api/1041/37467) | Deletes an adaptive bitrate streaming template | 20 |
| [DescribeTranscodeTemplates](https://www.tencentcloud.com/document/api/1041/33655) | Gets the list of transcoding templates | 100 |
| [DescribeAdaptiveDynamicStreamingTemplates](https://www.tencentcloud.com/document/api/1041/37465) | Gets the list of adaptive bitrate streaming templates | 20 |
| [ModifyTranscodeTemplate](https://www.tencentcloud.com/document/api/1041/33647) | Modifies a transcoding template | 100 |
| [ModifyAdaptiveDynamicStreamingTemplate](https://www.tencentcloud.com/document/api/1041/37463) | Modifies an adaptive bitrate streaming template | 20 |

## Watermark Template APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateBlindWatermarkTemplate](https://www.tencentcloud.com/document/api/1041/74704) | Creates a digital watermark template | 20 |
| [CreateWatermarkTemplate](https://www.tencentcloud.com/document/api/1041/33670) | Creates a watermarking template | 100 |
| [DeleteBlindWatermarkTemplate](https://www.tencentcloud.com/document/api/1041/74703) | Deletes a digital watermark template | 20 |
| [DeleteWatermarkTemplate](https://www.tencentcloud.com/document/api/1041/33662) | Deletes a watermarking template | 100 |
| [DescribeBlindWatermarkTemplates](https://www.tencentcloud.com/document/api/1041/74702) | Obtains the list of digital watermark templates | 20 |
| [DescribeWatermarkTemplates](https://www.tencentcloud.com/document/api/1041/33654) | Gets the list of watermarking templates | 100 |
| [ModifyBlindWatermarkTemplate](https://www.tencentcloud.com/document/api/1041/74701) | Modifies a digital watermark template | 20 |
| [ModifyWatermarkTemplate](https://www.tencentcloud.com/document/api/1041/33646) | Modifies a watermarking template | 100 |

## Screenshot Template APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateAnimatedGraphicsTemplate](https://www.tencentcloud.com/document/api/1041/33676) | Creates an animated image generating template | 100 |
| [CreateSnapshotByTimeOffsetTemplate](https://www.tencentcloud.com/document/api/1041/33672) | Creates a time point screencapturing template | 100 |
| [CreateSampleSnapshotTemplate](https://www.tencentcloud.com/document/api/1041/33673) | Creates a sampled screencapturing template | 100 |
| [CreateImageSpriteTemplate](https://www.tencentcloud.com/document/api/1041/33674) | Creates an image sprite generating template | 100 |
| [DeleteAnimatedGraphicsTemplate](https://www.tencentcloud.com/document/api/1041/33668) | Deletes an animated image generating template | 100 |
| [DeleteSnapshotByTimeOffsetTemplate](https://www.tencentcloud.com/document/api/1041/33664) | Deletes a time point screencapturing template | 100 |
| [DeleteSampleSnapshotTemplate](https://www.tencentcloud.com/document/api/1041/33665) | Deletes a sampled screencapturing template | 100 |
| [DeleteImageSpriteTemplate](https://www.tencentcloud.com/document/api/1041/33666) | Deletes an image sprite generating template | 100 |
| [DescribeAnimatedGraphicsTemplates](https://www.tencentcloud.com/document/api/1041/33660) | Gets the list of animated image generating templates | 100 |
| [DescribeSnapshotByTimeOffsetTemplates](https://www.tencentcloud.com/document/api/1041/33656) | Gets the list of time point screencapturing templates | 100 |
| [DescribeSampleSnapshotTemplates](https://www.tencentcloud.com/document/api/1041/33657) | Gets the list of sampled screencapturing templates | 100 |
| [DescribeImageSpriteTemplates](https://www.tencentcloud.com/document/api/1041/33658) | Gets the list of image sprite generating templates | 100 |
| [ModifyAnimatedGraphicsTemplate](https://www.tencentcloud.com/document/api/1041/33652) | Modifies an animated image generating template | 100 |
| [ModifySnapshotByTimeOffsetTemplate](https://www.tencentcloud.com/document/api/1041/33648) | Modifies a time point screencapturing template | 100 |
| [ModifySampleSnapshotTemplate](https://www.tencentcloud.com/document/api/1041/33649) | Modifies a sampled screencapturing template | 100 |
| [ModifyImageSpriteTemplate](https://www.tencentcloud.com/document/api/1041/33650) | Modifies an image sprite generating template | 100 |

## Media AI Template APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateSmartEraseTemplate](https://www.tencentcloud.com/document/api/1041/73667) | Creates a smart erasing template | 20 |
| [CreateSmartSubtitleTemplate](https://www.tencentcloud.com/document/api/1041/68919) | Creates a smart subtitle template | 20 |
| [CreateContentReviewTemplate](https://www.tencentcloud.com/document/api/1041/33675) | Creates a content moderation template | 10 |
| [CreateAIAnalysisTemplate](https://www.tencentcloud.com/document/api/1041/37470) | Creates content analysis template | 10 |
| [CreateAIRecognitionTemplate](https://www.tencentcloud.com/document/api/1041/33677) | Creates a content recognition template | 10 |
| [DeleteSmartEraseTemplate](https://www.tencentcloud.com/document/api/1041/73666) | Deletes a smart erasing template | 20 |
| [DeleteSmartSubtitleTemplate](https://www.tencentcloud.com/document/api/1041/68918) | Deletes a smart subtitle template | 20 |
| [DeleteContentReviewTemplate](https://www.tencentcloud.com/document/api/1041/33667) | Deletes a content moderation template | 10 |
| [DeleteAIAnalysisTemplate](https://www.tencentcloud.com/document/api/1041/37468) | Deletes content analysis template | 10 |
| [DeleteAIRecognitionTemplate](https://www.tencentcloud.com/document/api/1041/33669) | Deletes a content recognition template | 10 |
| [DescribeSmartEraseTemplates](https://www.tencentcloud.com/document/api/1041/73665) | Obtains the smart erasing template list | 20 |
| [DescribeSmartSubtitleTemplates](https://www.tencentcloud.com/document/api/1041/68917) | Obtains the smart subtitle template list | 20 |
| [DescribeContentReviewTemplates](https://www.tencentcloud.com/document/api/1041/33659) | Queries content moderation templates | 10 |
| [DescribeAIAnalysisTemplates](https://www.tencentcloud.com/document/api/1041/37466) | Gets content analysis template list | 10 |
| [DescribeAIRecognitionTemplates](https://www.tencentcloud.com/document/api/1041/33661) | Gets the list of content recognition templates | 10 |
| [ModifySmartEraseTemplate](https://www.tencentcloud.com/document/api/1041/73664) | Modifies a smart erasing template | 20 |
| [ModifySmartSubtitleTemplate](https://www.tencentcloud.com/document/api/1041/68916) | Modifies a smart subtitle template | 20 |
| [ModifyContentReviewTemplate](https://www.tencentcloud.com/document/api/1041/33651) | Modifies a content moderation template | 10 |
| [ModifyAIAnalysisTemplate](https://www.tencentcloud.com/document/api/1041/37464) | Modifies content analysis template | 10 |
| [ModifyAIRecognitionTemplate](https://www.tencentcloud.com/document/api/1041/33653) | Modifies a content recognition template | 10 |

## Media AI—Hotword Lexicon APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateAsrHotwords](https://www.tencentcloud.com/document/api/1041/68915) | Creates a smart subtitle hotword lexicon | 20 |
| [DeleteAsrHotwords](https://www.tencentcloud.com/document/api/1041/68914) | Deletes a smart subtitle hotword lexicon | 20 |
| [DescribeAsrHotwords](https://www.tencentcloud.com/document/api/1041/68913) | Queries the details of a smart subtitle hotword lexicon | 20 |
| [DescribeAsrHotwordsList](https://www.tencentcloud.com/document/api/1041/68912) | Queries the list of smart subtitle hotword lexicons | 20 |
| [ModifyAsrHotwords](https://www.tencentcloud.com/document/api/1041/68911) | Modifies a smart subtitle hotword lexicon | 20 |

## Media AI—Sample Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreatePersonSample](https://www.tencentcloud.com/document/api/1041/33689) | Creates image samples | 100 |
| [CreateWordSamples](https://www.tencentcloud.com/document/api/1041/33688) | Creates keyword samples | 100 |
| [DeletePersonSample](https://www.tencentcloud.com/document/api/1041/33687) | Deletes image samples | 100 |
| [DeleteWordSamples](https://www.tencentcloud.com/document/api/1041/33686) | Deletes keyword samples | 100 |
| [DescribePersonSamples](https://www.tencentcloud.com/document/api/1041/33685) | Gets the list of image samples | 100 |
| [DescribeWordSamples](https://www.tencentcloud.com/document/api/1041/33684) | Gets the list of keyword samples | 100 |
| [ModifyPersonSample](https://www.tencentcloud.com/document/api/1041/33683) | Modifies image samples | 100 |
| [ModifyWordSample](https://www.tencentcloud.com/document/api/1041/33682) | Modifies a keyword sample | 100 |

## Media Quality Inspection Template APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateQualityControlTemplate](https://www.tencentcloud.com/document/api/1041/64713) | Creates a media quality inspection template | 20 |
| [DeleteQualityControlTemplate](https://www.tencentcloud.com/document/api/1041/64712) | Deletes a media quality inspection template | 20 |
| [DescribeQualityControlTemplates](https://www.tencentcloud.com/document/api/1041/64711) | Obtains a list of media quality inspection templates | 20 |
| [ModifyQualityControlTemplate](https://www.tencentcloud.com/document/api/1041/64710) | Modifies a media quality inspection template | 20 |

## Live Streaming Recording Template APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateLiveRecordTemplate](https://www.tencentcloud.com/document/api/1041/67515) | Creates a live recording template | 20 |
| [DeleteLiveRecordTemplate](https://www.tencentcloud.com/document/api/1041/67514) | Deletes a live recording template | 20 |
| [DescribeLiveRecordTemplates](https://www.tencentcloud.com/document/api/1041/67513) | Gets a live recording template | 20 |
| [ModifyLiveRecordTemplate](https://www.tencentcloud.com/document/api/1041/67512) | Modifies a live recording template | 20 |

## Orchestration Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateSchedule](https://www.tencentcloud.com/document/api/1041/54035) | Creates a scheme | 20 |
| [CreateWorkflow](https://www.tencentcloud.com/document/api/1041/33638) | Creates a workflow | 200 |
| [DeleteSchedule](https://www.tencentcloud.com/document/api/1041/54034) | Deletes a scheme | 20 |
| [DeleteWorkflow](https://www.tencentcloud.com/document/api/1041/33637) | Deletes a workflow | 20 |
| [DescribeSchedules](https://www.tencentcloud.com/document/api/1041/54033) | Queries a scheme | 20 |
| [DescribeWorkflows](https://www.tencentcloud.com/document/api/1041/33636) | Get the workflow list | 20 |
| [ModifySchedule](https://www.tencentcloud.com/document/api/1041/54030) | Modifies a scheme | 20 |
| [ResetWorkflow](https://www.tencentcloud.com/document/api/1041/33633) | Resets a workflow | 20 |
| [EnableSchedule](https://www.tencentcloud.com/document/api/1041/54031) | Enables a scheme | 20 |
| [EnableWorkflow](https://www.tencentcloud.com/document/api/1041/33634) | Enables a workflow | 20 |
| [DisableSchedule](https://www.tencentcloud.com/document/api/1041/54032) | Disables a scheme | 20 |
| [DisableWorkflow](https://www.tencentcloud.com/document/api/1041/33635) | Disables a workflow | 20 |

## Data Statistics APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeUsageData](https://www.tencentcloud.com/document/api/1041/75556) | Queries usage information | 100 |

## StreamLink—Security Group Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeStreamLinkSecurityGroup](https://www.tencentcloud.com/document/api/1041/67844) | Queries a Security Group | 20 |

## Other APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [ParseLiveStreamProcessNotification](https://www.tencentcloud.com/document/api/1041/33680) | Parses the live stream processing result | 20 |
| [ParseNotification](https://www.tencentcloud.com/document/api/1041/33679) | Parses an event notification | 20 |
| [ExecuteFunction](https://www.tencentcloud.com/document/api/1041/38515) | Runs a custom API | 20 |
| [TextTranslation](https://www.tencentcloud.com/document/api/1041/75936) | Translates text | 5 |

## AI Generation APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateAigcImageTask](https://www.tencentcloud.com/document/api/1041/76488) | Creates an AIGC image generation task | 20 |
| [CreateAigcVideoTask](https://www.tencentcloud.com/document/api/1041/76487) | Creates an AIGC video generation task | 10 |
| [DescribeAigcImageTask](https://www.tencentcloud.com/document/api/1041/76486) | Queries an AIGC image generation task | 20 |
| [DescribeAigcVideoTask](https://www.tencentcloud.com/document/api/1041/76485) | Queries an AIGC video generation task | 50 |

## Image Processing Template APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateProcessImageTemplate](https://www.tencentcloud.com/document/api/1041/74710) | Creates an image processing template | 20 |
| [DeleteProcessImageTemplate](https://www.tencentcloud.com/document/api/1041/74709) | Deletes an image processing template | 20 |
| [DescribeProcessImageTemplates](https://www.tencentcloud.com/document/api/1041/74708) | Queries the list of image processing templates | 20 |
| [ModifyProcessImageTemplate](https://www.tencentcloud.com/document/api/1041/74707) | Modifies an image processing template | 20 |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33625](https://www.tencentcloud.com/document/product/1041/33625)*
