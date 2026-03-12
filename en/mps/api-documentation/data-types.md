# Data Types

## AIAnalysisTemplateItem

AI-based intelligent analysis template details

Used by actions: DescribeAIAnalysisTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of intelligent analysis template. |
| Name | String | Intelligent analysis template name. |
| Comment | String | Intelligent analysis template description. |
| ClassificationConfigure | [ClassificationConfigureInfo](#ClassificationConfigureInfo) | Control parameter of intelligent categorization task. |
| TagConfigure | [TagConfigureInfo](#TagConfigureInfo) | Control parameter of intelligent tagging task. |
| CoverConfigure | [CoverConfigureInfo](#CoverConfigureInfo) | Control parameter of intelligent cover generating task. |
| FrameTagConfigure | [FrameTagConfigureInfo](#FrameTagConfigureInfo) | Control parameter of intelligent frame-specific tagging task. |
| CreateTime | String | Creation time of template in [ISO date format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |
| UpdateTime | String | Last modified time of template in [ISO date format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |
| Type | String | The template type. Valid values: * Preset * Custom Note: This field may return `null`, indicating that no valid value can be obtained. |

## AIRecognitionTemplateItem

Details of a video content recognition template

Used by actions: DescribeAIRecognitionTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of a video content recognition template. |
| Name | String | Name of a video content recognition template. |
| Comment | String | Description of a video content recognition template. |
| FaceConfigure | [FaceConfigureInfo](#FaceConfigureInfo) | Face recognition control parameter. Note: This field may return null, indicating that no valid values can be obtained. |
| OcrFullTextConfigure | [OcrFullTextConfigureInfo](#OcrFullTextConfigureInfo) | Full text recognition control parameter. Note: This field may return null, indicating that no valid values can be obtained. |
| OcrWordsConfigure | [OcrWordsConfigureInfo](#OcrWordsConfigureInfo) | Text keyword recognition control parameter. Note: This field may return null, indicating that no valid values can be obtained. |
| AsrFullTextConfigure | [AsrFullTextConfigureInfo](#AsrFullTextConfigureInfo) | Full speech recognition control parameter. Note: This field may return null, indicating that no valid values can be obtained. |
| AsrWordsConfigure | [AsrWordsConfigureInfo](#AsrWordsConfigureInfo) | Speech keyword recognition control parameter. Note: This field may return null, indicating that no valid values can be obtained. |
| TranslateConfigure | [TranslateConfigureInfo](#TranslateConfigureInfo) | Voice translation control parameters. Note: This field may return null, indicating that no valid values can be obtained. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| Type | String | The template type. Valid values: * Preset * Custom Note: This field may return `null`, indicating that no valid value can be obtained. |

## Activity

A subtask of a scheme.

Used by actions: CreateSchedule, DescribeSchedules, ModifySchedule.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ActivityType | String | Yes | Atomic task type. input: starting node.. output: termination node.. action-trans: specifies transcoding.. action-samplesnapshot: specifies sampled screenshot taking.. action-AIAnalysis: analysis.. action-AIRecognition: recognition.. action-aiReview: specifies the review action.. action-animated-graphics: specifies the animated image.. action-image-sprite: specifies the sprite sheet.. action-snapshotByTimeOffset: specifies time point screenshot taking.. action-adaptive-substream: specifies the adaptive bitrate stream.. action-AIQualityControl: media quality inspection.. action-SmartSubtitles: smart subtitling.. action-exec-rules: judgment rule.. action-SmartErase: smart erasure.. |
| ReardriveIndex | Array of Integer | No | Rear node index array. |
| ActivityPara | [ActivityPara](#ActivityPara) | No | The parameters of a subtask. Note: This field may return null, indicating that no valid values can be obtained. |

## ActivityPara

A subtask of a scheme.

Used by actions: CreateSchedule, ModifySchedule.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| TranscodeTask | [TranscodeTaskInput](#TranscodeTaskInput) | No | A transcoding task. |
| AnimatedGraphicTask | [AnimatedGraphicTaskInput](#AnimatedGraphicTaskInput) | No | An animated screenshot generation task. |
| SnapshotByTimeOffsetTask | [SnapshotByTimeOffsetTaskInput](#SnapshotByTimeOffsetTaskInput) | No | A time point screenshot task. |
| SampleSnapshotTask | [SampleSnapshotTaskInput](#SampleSnapshotTaskInput) | No | A sampled screenshot task. |
| ImageSpriteTask | [ImageSpriteTaskInput](#ImageSpriteTaskInput) | No | An image sprite screenshot task. |
| AdaptiveDynamicStreamingTask | [AdaptiveDynamicStreamingTaskInput](#AdaptiveDynamicStreamingTaskInput) | No | An adaptive bitrate streaming task. |
| AiContentReviewTask | [AiContentReviewTaskInput](#AiContentReviewTaskInput) | No | A content moderation task. |
| AiAnalysisTask | [AiAnalysisTaskInput](#AiAnalysisTaskInput) | No | A content analysis task. |
| AiRecognitionTask | [AiRecognitionTaskInput](#AiRecognitionTaskInput) | No | A content recognition task. |
| QualityControlTask | [AiQualityControlTaskInput](#AiQualityControlTaskInput) | No | Media quality inspection task. Note: This field may return null, indicating that no valid values can be obtained. |
| ExecRulesTask | [ExecRulesTask](#ExecRulesTask) | No | Conditional judgment of the task. Note: This field may return null, indicating that no valid value can be obtained. |
| SmartSubtitlesTask | [SmartSubtitlesTaskInput](#SmartSubtitlesTaskInput) | No | Smart subtitle task. Note: This field may return null, indicating that no valid value can be obtained. |
| SmartEraseTask | [SmartEraseTaskInput](#SmartEraseTaskInput) | No | Smart erasure task. Note: This field may return null, indicating that no valid value can be obtained. |

## ActivityResItem

The execution results of the subtasks of a scheme.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| TranscodeTask | [MediaProcessTaskTranscodeResult](#MediaProcessTaskTranscodeResult) | The result of a transcoding task. Note: This field may return null, indicating that no valid values can be obtained. |
| AnimatedGraphicTask | [MediaProcessTaskAnimatedGraphicResult](#MediaProcessTaskAnimatedGraphicResult) | The result of an animated image generating task. Note: This field may return null, indicating that no valid values can be obtained. |
| SnapshotByTimeOffsetTask | [MediaProcessTaskSnapshotByTimeOffsetResult](#MediaProcessTaskSnapshotByTimeOffsetResult) | The result of a time point screenshot task. Note: This field may return null, indicating that no valid values can be obtained. |
| SampleSnapshotTask | [MediaProcessTaskSampleSnapshotResult](#MediaProcessTaskSampleSnapshotResult) | The result of a sampled screenshot task. Note: This field may return null, indicating that no valid values can be obtained. |
| ImageSpriteTask | [MediaProcessTaskImageSpriteResult](#MediaProcessTaskImageSpriteResult) | The result of an image sprite task. Note: This field may return null, indicating that no valid values can be obtained. |
| AdaptiveDynamicStreamingTask | [MediaProcessTaskAdaptiveDynamicStreamingResult](#MediaProcessTaskAdaptiveDynamicStreamingResult) | The result of an adaptive bitrate streaming task. Note: This field may return null, indicating that no valid values can be obtained. |
| RecognitionTask | [ScheduleRecognitionTaskResult](#ScheduleRecognitionTaskResult) | The result of a content recognition task. Note: This field may return null, indicating that no valid values can be obtained. |
| ReviewTask | [ScheduleReviewTaskResult](#ScheduleReviewTaskResult) | The result of a content moderation task. Note: This field may return null, indicating that no valid values can be obtained. |
| AnalysisTask | [ScheduleAnalysisTaskResult](#ScheduleAnalysisTaskResult) | The result of a content analysis task. Note: This field may return null, indicating that no valid values can be obtained. |
| QualityControlTask | [ScheduleQualityControlTaskResult](#ScheduleQualityControlTaskResult) | Media quality inspection task output. Note: This field may return null, indicating that no valid values can be obtained. |
| ExecRuleTask | [ScheduleExecRuleTaskResult](#ScheduleExecRuleTaskResult) | Conditional judgment task output. Note: This field may return null, indicating that no valid value can be obtained. |
| SmartSubtitlesTask | [ScheduleSmartSubtitleTaskResult](#ScheduleSmartSubtitleTaskResult) | Smart subtitle task output. Note: This field may return null, indicating that no valid value can be obtained. |
| SmartEraseTask | [SmartEraseTaskResult](#SmartEraseTaskResult) | Smart erase task output. Note: This field may return null, indicating that no valid value can be obtained. |

## ActivityResult

The execution result of a scheme.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| ActivityType | String | Atomic task type. Transcode: transcoding.. SampleSnapshot: specifies sampled screenshot taking.. AnimatedGraphics: specifies the animated image.. SnapshotByTimeOffset: specifies time point screenshot taking.. ImageSprites: specifies the sprite sheet.. AdaptiveDynamicStreaming: adaptive bitrate streaming.. AiContentReview: specifies content moderation.. AIRecognition: intelligent identification.. AIAnalysis: specifies ai analysis.. AiQualityControl: media quality inspection  SmartSubtitles: smart subtitle  SmartErase: smart erasure.. |
| ActivityResItem | [ActivityResItem](#ActivityResItem) | The execution results of the subtasks of the scheme. |

## AdaptiveDynamicStreamingInfoItem

Adaptive bitrate streaming information

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Adaptive bitrate streaming specification. |
| Package | String | Container format. Valid values: HLS, MPEG-DASH. |
| Path | String | Playback address. |
| Storage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of adaptive bitrate streaming files. |

## AdaptiveDynamicStreamingTaskInput

Input parameter type of adaptive bitrate streaming

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | Adaptive dynamic streaming template ID. |
| WatermarkSet | Array of [WatermarkInput](#WatermarkInput) | No | Watermark list. Multiple image or text watermarks up to a maximum of 10 are supported. |
| BlindWatermark | [BlindWatermarkInput](#BlindWatermarkInput) | No | Digital watermark parameter.     Note: This field may return null, indicating that no valid values can be obtained. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | Target storage for files after adaptive dynamic streaming. If left blank, it inherits the upper-level OutputStorage value. Note: This field may return null, indicating that no valid value can be obtained. |
| OutputObjectPath | String | No | Output path for the manifest file after adaptive dynamic streaming. It can be either a relative path or an absolute path. If you need to define an output path, the path must end with `.{format}`. Refer to [Filename Variable Description](https://intl.cloud.tencent.com/document/product/862/37039?from_cn_redirect=1) for variable names. Example of relative path: filename_{variable name}.{format}filename.{format} Example of absolute path: /custom path/filename_{variable name}.{format} If not filled in, it is a relative path by default: {inputName}_adaptiveDynamicStreaming_{definition}.{format}. |
| SubStreamObjectName | String | No | After adaptive dynamic streaming, the output path of substream files can only be a relative path. If not filled in, it is a relative path by default: `{inputName}_adaptiveDynamicStreaming_{definition}_{subStreamNumber}.{format}`. |
| SegmentObjectName | String | No | After adaptive dynamic streaming (for HLS only), the output path of segment files can only be a relative path. If not filled in, it is a relative path by default: `{inputName}_adaptiveDynamicStreaming_{definition}_{subStreamNumber}_{segmentNumber}.{format}`. |
| AddOnSubtitles | Array of [AddOnSubtitle](#AddOnSubtitle) | No | External subtitle feature specifies the subtitle file to be inserted. Note: This field may return null, indicating that no valid value can be obtained. |
| DrmInfo | [DrmInfo](#DrmInfo) | No | Specifies the Drm information. Note: This field may return null, indicating that no valid value can be obtained. |
| DefinitionType | String | No | Adaptive transcoding template type. Common: audio/video type. PureAudio: audio-only. |
| SubtitleTemplate | [SubtitleTemplate](#SubtitleTemplate) | No | Hard subtitle (suppression subtitle) feature, specify subtitles source, font size, position and other subtitle parameters. Note: This field may return null, indicating that no valid value can be obtained. |
| StdExtInfo | String | No | Transcoding parameter extension field. |
| KeyPTSList | Array of Integer | No | Specifies the frame at the given pts time as a key frame and segments it. unit: milliseconds (relative deviation <=1ms is allowed). when gop and segment duration are specified simultaneously, they function together. note: enable RawPts, keep the frame rate as source, and ensure the passed-in pts time corresponds to a frame in the source. Note: This field may return null, indicating that no valid values can be obtained. |

## AdaptiveDynamicStreamingTemplate

Details of an adaptive bitrate streaming template

Used by actions: DescribeAdaptiveDynamicStreamingTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of an adaptive bitrate streaming template. |
| Type | String | Template type. Valid values: Preset: preset template;Custom: custom template. |
| Name | String | Name of an adaptive bitrate streaming template. |
| Comment | String | Description of an adaptive bitrate streaming template. |
| Format | String | Adaptive bitrate streaming format. Valid values: HLS;MPEG-DASH. |
| StreamInfos | Array of [AdaptiveStreamTemplate](#AdaptiveStreamTemplate) | Parameter information of input streams for transcoding to adaptive bitrate streaming. Up to 10 streams can be input. |
| DisableHigherVideoBitrate | Integer | Whether to prohibit transcoding from low bitrate to high bitrate. Valid values: 0: no,1: yes. |
| DisableHigherVideoResolution | Integer | Whether to prohibit transcoding from low resolution to high resolution. Valid values: 0: no,1: yes. |
| CreateTime | String | Creation time of template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#I). |
| UpdateTime | String | Last modified time of template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#I). |
| PureAudio | Integer | Whether it is an audio-only template. 0: video template. 1: audio-only template.Note: This field may return null, indicating that no valid values can be obtained. |
| SegmentType | String | HLS segment type. Valid values: ts-segment: HLS+TS segment.ts-byterange: HLS+TS byte range.mp4-segment: HLS+MP4 segment.mp4-byterange: HLS+MP4 byte range.ts-packed-audio: TS+Packed audio.mp4-packed-audio: MP4+Packed audio. Default value: ts-segment.  Note: The HLS segment format for adaptive bitrate streaming is based on this field.Note: This field may return null, indicating that no valid values can be obtained. |

## AdaptiveStreamTemplate

Adaptive bitrate streaming parameter template

Used by actions: CreateAdaptiveDynamicStreamingTemplate, DescribeAdaptiveDynamicStreamingTemplates, ModifyAdaptiveDynamicStreamingTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Audio | [AudioTemplateInfo](#AudioTemplateInfo) | Yes | Audio parameter information. |
| Video | [VideoTemplateInfo](#VideoTemplateInfo) | No | Video parameter information. |
| RemoveAudio | Integer | No | Whether to remove audio stream. Valid values: 0: no,1: yes. |
| RemoveVideo | Integer | No | Whether to remove video stream. Valid values: 0: no,1: yes. |
| AudioList | Array of [AudioTemplateInfo](#AudioTemplateInfo) | No | Audio parameter information list. The parameter is only used when merging multiple audio tracks in adaptive bitrate transcoding. the maximum length of the parameter array is 64.  Note: This field may return null, indicating that no valid value can be obtained. |

## AddOnSubtitle

The information of the subtitles to add.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | No | The mode. Valid values: `subtitle-stream`: Add a subtitle track.`close-caption-708`: Embed CEA-708 subtitles in SEI frames.`close-caption-608`: Embed CEA-608 subtitles in SEI frames. Note: This field may return null, indicating that no valid values can be obtained. |
| Subtitle | [MediaInputInfo](#MediaInputInfo) | No | The subtitle file. Note: This field may return null, indicating that no valid values can be obtained. |
| SubtitleName | String | No | Subtitle name. Note: supports Chinese characters, letters, digits, spaces, underscores (_), hyphens (-), periods (.), and parentheses. Max 64 characters. Note: This field may return null, indicating that no valid value can be obtained. |
| OutputFormat | String | No | Output format of the subtitle. valid values: "WebVTT", "TTML". Default value: "WebVTT". |
| DefaultTrack | Boolean | No | Default subtitle track. specifies the current subtitle as the default track when true. a maximum of 1 default subtitle track can be specified. Default value: `false`. |

## AdvancedSuperResolutionConfig

Super-resolution configuration.

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Capability configuration switch. Valid values: ON: enabled.OFF: disabled. Default value: ON. |
| Type | String | No | Type. Valid values:standard: standard super-resolution.super: super advanced super-resolution.ultra: ultra advanced super-resolution.Default value: standard. Note: This field may return null, indicating that no valid values can be obtained. |
| Mode | String | No | Image output mode. The default value is percent. aspect: obtain a larger rectangle with specified width and height through super-resolution.fixed: obtain images of fixed width and height through super-resolution, with forced scaling supported.percent: magnification factor of super-resolution, which can be a decimal. Note: This field may return null, indicating that no valid values can be obtained. |
| Percent | Float | No | Scale factor of super-resolution, which can be a decimal.Note: This is used when Mode is percent.Note: This field may return null, indicating that no valid values can be obtained. |
| Width | Integer | No | Width of the target image. The value cannot exceed 4096.Note: When Mode is aspect or fixed, this configuration takes priority.Note: This field may return null, indicating that no valid values can be obtained. |
| Height | Integer | No | Height of the target image. The value cannot exceed 4096.Note: When Mode is aspect or fixed, this configuration takes priority.Note: This field may return null, indicating that no valid values can be obtained. |
| LongSide | Integer | No | Long side length of the target image. The value cannot exceed 4096.Note: This configuration is used when Mode is aspect or fixed and the Width and Height fields are not specified.Note: This field may return null, indicating that no valid values can be obtained. |
| ShortSide | Integer | No | Short side length of the target image. The value cannot exceed 4096.Note: This configuration is used when Mode is aspect or fixed and the Width and Height fields are not specified.Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisResult

Intelligent analysis results

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | Task type. Valid values:Classification: intelligent classification.Cover: intelligent cover.Tag: intelligent tagging.FrameTag: intelligent frame-level tagging.Highlight: intelligent highlights.DeLogo: intelligent removal.Description: LLM summarization.Dubbing: intelligent dubbing.VideoRemake: video recreation.VideoComprehension: video (audio) recognition.Cutout: video matting.Reel: intelligent video editing. |
| ClassificationTask | [AiAnalysisTaskClassificationResult](#AiAnalysisTaskClassificationResult) | Query result of intelligent categorization task in video content analysis, which is valid if task type is `Classification`. |
| CoverTask | [AiAnalysisTaskCoverResult](#AiAnalysisTaskCoverResult) | Query result of intelligent cover generating task in video content analysis, which is valid if task type is `Cover`. |
| TagTask | [AiAnalysisTaskTagResult](#AiAnalysisTaskTagResult) | Query result of intelligent tagging task in video content analysis, which is valid if task type is `Tag`. |
| FrameTagTask | [AiAnalysisTaskFrameTagResult](#AiAnalysisTaskFrameTagResult) | Query result of intelligent frame-specific tagging task in video content analysis, which is valid if task type is `FrameTag`. |
| HighlightTask | [AiAnalysisTaskHighlightResult](#AiAnalysisTaskHighlightResult) | The result of a highlight generation task. This parameter is valid if `Type` is `Highlight`. Note: This field may return null, indicating that no valid values can be obtained. |
| DeLogoTask | [AiAnalysisTaskDelLogoResult](#AiAnalysisTaskDelLogoResult) | The query result of an intelligent removal task for video analysis, which is valid when the task type is DeLogo. Note: This field may return null, indicating that no valid values can be obtained. |
| SegmentTask | [AiAnalysisTaskSegmentResult](#AiAnalysisTaskSegmentResult) | The query result of a splitting task for video analysis, which is valid when the task type is SegmentRecognition. Note: This field may return null, indicating that no valid values can be obtained. |
| HeadTailTask | [AiAnalysisTaskHeadTailResult](#AiAnalysisTaskHeadTailResult) | The query result of an opening and closing segments recognition task for video analysis, which is valid when the task type is HeadTailRecognition. Note: This field may return null, indicating that no valid values can be obtained. |
| DescriptionTask | [AiAnalysisTaskDescriptionResult](#AiAnalysisTaskDescriptionResult) | The query result of a video analysis summarization task, which is valid when the task type is Description. Note: This field may return null, indicating that no valid values can be obtained. |
| HorizontalToVerticalTask | [AiAnalysisTaskHorizontalToVerticalResult](#AiAnalysisTaskHorizontalToVerticalResult) | The query result of a landscape-to-portrait task for video analysis, which is valid when the task type is HorizontalToVertical. Note: This field may return null, indicating that no valid values can be obtained. |
| DubbingTask | [AiAnalysisTaskDubbingResult](#AiAnalysisTaskDubbingResult) | The query result of a Dubbing task for video content analysis, which is valid when the task type is Dubbing. Note: This field may return null, indicating that no valid value can be obtained. |
| VideoRemakeTask | [AiAnalysisTaskVideoRemakeResult](#AiAnalysisTaskVideoRemakeResult) | The query result of a video content deduplication task, which is valid when the task type is VideoRemake. Note: This field may return null, indicating that no valid value can be obtained. |
| VideoComprehensionTask | [AiAnalysisTaskVideoComprehensionResult](#AiAnalysisTaskVideoComprehensionResult) | Query result of the video (audio) recognition task. This parameter is valid when the task type is VideoComprehension. Note: This field may return null, indicating that no valid values can be obtained. |
| CutoutTask | [AiAnalysisTaskCutoutResult](#AiAnalysisTaskCutoutResult) | Query result of video content analysis intelligent image masking task. valid when task type is Cutout. Note: This field may return null, indicating that no valid values can be obtained. |
| ReelTask | [AiAnalysisTaskReelResult](#AiAnalysisTaskReelResult) | Query result of the video content analysis AI narration and video re-creation task. valid when the task type is Reel. Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskClassificationInput

Input type of intelligent categorization task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Intelligent video categorization template ID. |

## AiAnalysisTaskClassificationOutput

Result information of intelligent categorization

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| ClassificationSet | Array of [MediaAiAnalysisClassificationItem](#MediaAiAnalysisClassificationItem) | List of intelligently generated video categories. |

## AiAnalysisTaskClassificationResult

Result type of intelligent categorization task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskClassificationInput](#AiAnalysisTaskClassificationInput) | Input of intelligent categorization task. |
| Output | [AiAnalysisTaskClassificationOutput](#AiAnalysisTaskClassificationOutput) | Output of intelligent categorization task. |

## AiAnalysisTaskCoverInput

Input type of intelligent categorization task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Intelligent video cover generating template ID. |

## AiAnalysisTaskCoverOutput

Result information of intelligent cover generating

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| CoverSet | Array of [MediaAiAnalysisCoverItem](#MediaAiAnalysisCoverItem) | List of intelligently generated covers. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of intelligently generated cover. |

## AiAnalysisTaskCoverResult

Result type of intelligent cover generating task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskCoverInput](#AiAnalysisTaskCoverInput) | Input of intelligent cover generating task. |
| Output | [AiAnalysisTaskCoverOutput](#AiAnalysisTaskCoverOutput) | Output of intelligent cover generating task. |

## AiAnalysisTaskCutoutInput

Input type of the intelligent video matting task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | ID of the intelligent video matting template. |

## AiAnalysisTaskCutoutOutput

Video matting result information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Path | String | File path for the intelligent video matting. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location for the intelligent video matting. |

## AiAnalysisTaskCutoutResult

Data structure of the video intelligent image masking result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values are `PROCESSING`, `SUCCESS`, and `FAIL`. |
| ErrCodeExt | String | Error code. An empty string indicates that the task is successful, while other values indicate that the task has failed. For valid values, see the list of [MPS error codes](https://www.tencentcloud.comom/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81). |
| Message | String | Error message. |
| Input | [AiAnalysisTaskCutoutInput](#AiAnalysisTaskCutoutInput) | Input of the video matting task. |
| Output | [AiAnalysisTaskCutoutOutput](#AiAnalysisTaskCutoutOutput) | Output of the video matting task.Note: This field may return null, indicating that no valid values can be obtained. |
| Progress | Integer | Task progress. |
| BeginProcessTime | String | Task start time, in ISO date and time format. |
| FinishTime | String | Task completion time, in ISO date and time format. |

## AiAnalysisTaskDelLogoInput

Intelligent removal task input type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Intelligent removal template ID. |

## AiAnalysisTaskDelLogoOutput

Intelligent removal result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Path | String | Path of a file after removal. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of a file after removal. |
| OriginSubtitlePath | String | Path of a subtitle file extracted from a video. |
| TranslateSubtitlePath | String | Path of a subtitle translation file extracted from a video. |
| SubtitlePos | [SubtitlePosition](#SubtitlePosition) | Position of the erased subtitle. Note: This field is only valid for subtitle extraction when the option to return subtitle positions is enabled. Note: This field may return null, indicating that no valid value can be obtained. |
| VoiceClonedVideo | String | Specifies the file url of the video after voice cloning. Note: This field may return null, indicating that no valid value can be obtained. |
| VoiceClonedMarkFile | String | Specifies the file address of the voice type clone annotation. Note: This field may return null, indicating that no valid value can be obtained. |

## AiAnalysisTaskDelLogoResult

Intelligent removal result type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCode | Integer | Error code. `0`: Task successful. Other values: Task failed. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskDelLogoInput](#AiAnalysisTaskDelLogoInput) | Intelligent removal task input. |
| Output | [AiAnalysisTaskDelLogoOutput](#AiAnalysisTaskDelLogoOutput) | Intelligent removal task output.Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskDescriptionInput

Intelligent classification task input type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Intelligent description template ID. |

## AiAnalysisTaskDescriptionOutput

Intelligent description result information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| DescriptionSet | Array of [MediaAiAnalysisDescriptionItem](#MediaAiAnalysisDescriptionItem) | Intelligent video description list. |

## AiAnalysisTaskDescriptionResult

Intelligent description result type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCode | Integer | Error code. `0`: Task successful. Other values: Task failed. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskDescriptionInput](#AiAnalysisTaskDescriptionInput) | Intelligent description task input. |
| Output | [AiAnalysisTaskDescriptionOutput](#AiAnalysisTaskDescriptionOutput) | Intelligent description task output. Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskDubbingInput

Intelligent translation task input type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Video translation template ID. |

## AiAnalysisTaskDubbingOutput

Intelligent translation result information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| VideoPath | String | Specifies the video path for translation. |
| SpeakerPath | String | Specifies the file path of the tag. |
| VoiceId | String | Voice type ID. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Specifies the storage location of the transcoded video. |

## AiAnalysisTaskDubbingResult

Intelligent translation result type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCode | Integer | Error code. `0`: Task successful. Other values: Task failed. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskDubbingInput](#AiAnalysisTaskDubbingInput) | Describes the task input for intelligent translation. |
| Output | [AiAnalysisTaskDubbingOutput](#AiAnalysisTaskDubbingOutput) | Describes the task output of intelligent translation. Note: This field may return null, indicating that no valid value can be obtained. |

## AiAnalysisTaskFrameTagInput

Input type of intelligent frame-specific tagging task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Intelligent frame-specific video tagging template ID. |

## AiAnalysisTaskFrameTagOutput

Result information of intelligent frame-specific tagging

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| SegmentSet | Array of [MediaAiAnalysisFrameTagSegmentItem](#MediaAiAnalysisFrameTagSegmentItem) | List of frame-specific video tags. |

## AiAnalysisTaskFrameTagResult

Result type of intelligent frame-specific tagging

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskFrameTagInput](#AiAnalysisTaskFrameTagInput) | Input of intelligent frame-specific tagging task. |
| Output | [AiAnalysisTaskFrameTagOutput](#AiAnalysisTaskFrameTagOutput) | Output of intelligent frame-specific tagging task. |

## AiAnalysisTaskHeadTailInput

Opening and closing segments recognition task input type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Opening and closing segments recognition template ID. |

## AiAnalysisTaskHeadTailOutput

Opening and closing segments recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| HeadTimeOffset | Float | Opening segment PTS. Note: This field may return null, indicating that no valid values can be obtained. |
| TailTimeOffset | Float | Closing segment PTS. Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskHeadTailResult

Opening and closing segments recognition result type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCode | Integer | Error code. `0`: Task successful. Other values: Task failed. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskHeadTailInput](#AiAnalysisTaskHeadTailInput) | Opening and closing segments recognition task input. |
| Output | [AiAnalysisTaskHeadTailOutput](#AiAnalysisTaskHeadTailOutput) | Opening and closing segments recognition task output.Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskHighlightInput

The input of an intelligent highlight generation task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | The ID of the intelligent highlight generation template. |

## AiAnalysisTaskHighlightOutput

The output of an intelligent highlight generation task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| HighlightSet | Array of [MediaAiAnalysisHighlightItem](#MediaAiAnalysisHighlightItem) | A list of the highlight segments generated. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | The storage location of the highlight segments. Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskHighlightResult

The result of an intelligent highlight generation task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | The task status. Valid values: `PROCESSING`, `SUCCESS`, `FAIL`. |
| ErrCode | Integer | Error code. `0`: The task succeeded; other values: The task failed. |
| Message | String | The error message. |
| Input | [AiAnalysisTaskHighlightInput](#AiAnalysisTaskHighlightInput) | The input of the intelligent highlight generation task. |
| Output | [AiAnalysisTaskHighlightOutput](#AiAnalysisTaskHighlightOutput) | The output of the intelligent highlight generation task. Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskHorizontalToVerticalInput

Intelligent landscape-to-portrait task input type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Intelligent landscape-to-portrait template ID. Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskHorizontalToVerticalOutput

Intelligent landscape-to-portrait result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Path | String | Intelligent landscape-to-portrait video list. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of intelligent landscape-to-portrait videos. Note: This field may return null, indicating that no valid values can be obtained. |
| Confidence | Float | Confidence.       Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskHorizontalToVerticalResult

Intelligent landscape-to-portrait result type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. Note: This field may return null, indicating that no valid values can be obtained. |
| ErrCode | Integer | Error code. 0: Task successful. Other values: Task failed.  Note: This field may return null, indicating that no valid values can be obtained. |
| Message | String | Error message  Note: This field may return null, indicating that no valid values can be obtained. |
| Input | [AiAnalysisTaskHorizontalToVerticalInput](#AiAnalysisTaskHorizontalToVerticalInput) | Intelligent landscape-to-portrait task input. Note: This field may return null, indicating that no valid values can be obtained. |
| Output | [AiAnalysisTaskHorizontalToVerticalOutput](#AiAnalysisTaskHorizontalToVerticalOutput) | Intelligent landscape-to-portrait task output. Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskInput

AI video intelligent analysis input parameter types

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, DescribeWorkflows, ModifySchedule, ParseNotification, ProcessLiveStream, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | Video content analysis template ID. |
| ExtendedParameter | String | No | Additional parameter. Its value is a serialized JSON string. Note: This parameter is used to meet customization requirements. References: [Smart Erase Tutorial]: https://intl.cloud.tencent.com/document/product/862/101530?from_cn_redirect=1 [Video Splitting (Long Videos to Short Videos) Tutorial](https://intl.cloud.tencent.com/document/product/862/112098?from_cn_redirect=1) [Intelligent Highlights Tutorial](https://intl.cloud.tencent.com/document/product/862/107280?from_cn_redirect=1) [Horizontal-to-Vertical Video Transformation Tutorial](https://intl.cloud.tencent.com/document/product/862/112112?from_cn_redirect=1) Note: This field may return null, indicating that no valid value can be obtained. |

## AiAnalysisTaskReelInput

Input type of the intelligent video editing task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | ID of the intelligent video editing template. |

## AiAnalysisTaskReelOutput

AI narration and video re-creation result info.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| VideoPath | String | Path of the output video. |
| VideoPaths | Array of String | Path list of the output videos.  **Note**:. 1. when returning a file, `VideoPath` returns a file path, and `VideoPaths` likewise populates an element with the same path. 2. when multiple files are returned, `VideoPath` returns an empty string, and `VideoPaths` returns the file path list. |
| ScriptPath | String | Script file path. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of the output video. |

## AiAnalysisTaskReelResult

AI narration and video re-creation result type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values are PROCESSING, SUCCESS, and FAIL. |
| ErrCode | Integer | Error code. 0: Task successful. Other values: Task failed. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskReelInput](#AiAnalysisTaskReelInput) | AI narration and video re-creation task input. |
| Output | [AiAnalysisTaskReelOutput](#AiAnalysisTaskReelOutput) | AI narration and video re-creation task output. Note: This field may return null, indicating that no valid values can be obtained. |
| ErrCodeExt | String | Error code. An empty string indicates that the task is successful, while other values indicate that the task has failed. For valid values, see the list of MPS error codes.Note: This field may return null, indicating that no valid values can be obtained. |
| Progress | Integer | Task progress. Note: This field may return null, indicating that no valid values can be obtained. |
| BeginProcessTime | String | Task start time, in ISO date and time format.Note: This field may return null, indicating that no valid values can be obtained. |
| FinishTime | String | Task completion time, in ISO date and time format. Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskSegmentInput

Splitting task input type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Splitting task template ID. |

## AiAnalysisTaskSegmentOutput

Intelligent splitting result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| SegmentSet | Array of [SegmentRecognitionItem](#SegmentRecognitionItem) | Intelligent splitting sub-segment list. |
| Abstract | String | Video abstract, used for offline scenarios. Note: This field may return null, indicating that no valid value can be obtained. |

## AiAnalysisTaskSegmentResult

Splitting result type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCode | Integer | Error code. `0`: Task successful. Other values: Task failed. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskSegmentInput](#AiAnalysisTaskSegmentInput) | Splitting task input. |
| Output | [AiAnalysisTaskSegmentOutput](#AiAnalysisTaskSegmentOutput) | Splitting task output.Note: This field may return null, indicating that no valid values can be obtained. |

## AiAnalysisTaskTagInput

Input type of intelligent tagging task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Intelligent video tagging template ID. |

## AiAnalysisTaskTagOutput

Result information of intelligent tagging

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| TagSet | Array of [MediaAiAnalysisTagItem](#MediaAiAnalysisTagItem) | List of intelligently generated video tags. |

## AiAnalysisTaskTagResult

Result type of intelligent tagging task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskTagInput](#AiAnalysisTaskTagInput) | Input of intelligent tagging task. |
| Output | [AiAnalysisTaskTagOutput](#AiAnalysisTaskTagOutput) | Output of intelligent tagging task. |

## AiAnalysisTaskVideoComprehensionInput

Input file for the video (audio) recognition task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Video (audio) recognition template ID. |

## AiAnalysisTaskVideoComprehensionOutput

Information about the video (audio) recognition output content result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| VideoComprehensionAnalysisResult | String | Details of the video (audio) recognition output content. |
| VideoComprehensionExtInfo | String | Video (audio) extended information. |
| VideoComprehensionResultList | Array of [VideoComprehensionResultItem](#VideoComprehensionResultItem) | Video shot understanding result. |

## AiAnalysisTaskVideoComprehensionResult

Video (audio) recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: `PROCESSING`, `SUCCESS`, and `FAIL`. |
| ErrCode | Integer | Error code. 0: successful; other values: failed. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskVideoComprehensionInput](#AiAnalysisTaskVideoComprehensionInput) | Input file for video (audio) recognition. |
| Output | [AiAnalysisTaskVideoComprehensionOutput](#AiAnalysisTaskVideoComprehensionOutput) | Output file for video (audio) recognition. Note: This field may return null, indicating that no valid values can be obtained. |
| ErrCodeExt | String | Error code. A null string indicates that the task is successful, while other values indicate that the task has failed. For valid values, see the list of MPS error codes. |
| Progress | Integer | Task progress |
| BeginProcessTime | String | Starting time of task execution, in ISO date and time format. |
| FinishTime | String | Completion time of task execution, in ISO date and time format. |

## AiAnalysisTaskVideoRemakeInput

Video deduplication task input type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Intelligent deduplication template ID. |

## AiAnalysisTaskVideoRemakeOutput

Video deduplication result information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Path | String | Specifies the file path for intelligent video deduplication. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Specifies the storage location for intelligent video deduplication. |

## AiAnalysisTaskVideoRemakeResult

Video deduplication result data structure.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Specifies the task status. valid values: `PROCESSING`, `SUCCESS`, and `FAIL`. |
| ErrCode | Integer | Error code. 0: success. other values: failure. |
| Message | String | Error message. |
| Input | [AiAnalysisTaskVideoRemakeInput](#AiAnalysisTaskVideoRemakeInput) | Deduplication task input. |
| Output | [AiAnalysisTaskVideoRemakeOutput](#AiAnalysisTaskVideoRemakeOutput) | Task output. Note: This field may return null, indicating that no valid value can be obtained. |

## AiContentReviewResult

Content audit result

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | Task type. Valid values: Porn (in images)Terrorism (in images)Political (in images)Porn.AsrPorn.OcrPolitical.AsrPolitical.OcrTerrorism.OcrProhibited.AsrProhibited.Ocr |
| SampleRate | Float | Sample rate, which indicates the number of video frames captured per second for audit |
| Duration | Float | Audited video duration in seconds. |
| PornTask | [AiReviewTaskPornResult](#AiReviewTaskPornResult) | Query result of an intelligent porn information detection in image task in video content audit, which is valid when task type is `Porn`. Note: This field may return null, indicating that no valid values can be obtained. |
| TerrorismTask | [AiReviewTaskTerrorismResult](#AiReviewTaskTerrorismResult) | The result of detecting terrorism content in images, which is valid when the task type is `Terrorism`. Note: This field may return `null`, indicating that no valid values can be obtained. |
| PoliticalTask | [AiReviewTaskPoliticalResult](#AiReviewTaskPoliticalResult) | The result of detecting politically sensitive information in images, which is valid when the task type is `Political`. Note: This field may return `null`, indicating that no valid values can be obtained. |
| PornAsrTask | [AiReviewTaskPornAsrResult](#AiReviewTaskPornAsrResult) | Query result of an ASR-based porn information detection in text task in video content audit, which is valid when task type is `Porn.Asr`. Note: This field may return null, indicating that no valid values can be obtained. |
| PornOcrTask | [AiReviewTaskPornOcrResult](#AiReviewTaskPornOcrResult) | Query result of an OCR-based porn information detection in text task in video content audit, which is valid when task type is `Porn.Ocr`. Note: This field may return null, indicating that no valid values can be obtained. |
| PoliticalAsrTask | [AiReviewTaskPoliticalAsrResult](#AiReviewTaskPoliticalAsrResult) | The result of detecting politically sensitive information based on ASR, which is valid when the task type is `Political.Asr`. Note: This field may return `null`, indicating that no valid values can be obtained. |
| PoliticalOcrTask | [AiReviewTaskPoliticalOcrResult](#AiReviewTaskPoliticalOcrResult) | The result of detecting politically sensitive information based on OCR, which is valid when the task type is `Political.Ocr`. Note: This field may return `null`, indicating that no valid values can be obtained. |
| TerrorismOcrTask | [AiReviewTaskTerrorismOcrResult](#AiReviewTaskTerrorismOcrResult) | The result of detecting terrorism content based on OCR, which is valid when task type is `Terrorism.Ocr`. Note: This field may return `null`, indicating that no valid values can be obtained. |
| ProhibitedAsrTask | [AiReviewTaskProhibitedAsrResult](#AiReviewTaskProhibitedAsrResult) | Query result of ASR-based prohibited information detection in speech task in video content audit, which is valid if task type is `Prohibited.Asr`. |
| ProhibitedOcrTask | [AiReviewTaskProhibitedOcrResult](#AiReviewTaskProhibitedOcrResult) | Query result of OCR-based prohibited information detection in text task in video content audit, which is valid if task type is `Prohibited.Ocr`. |

## AiContentReviewTaskInput

Task type of intelligent content audit

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, DescribeWorkflows, ModifySchedule, ParseNotification, ProcessLiveStream, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | Video content audit template ID. |

## AiParagraphInfo

Segment information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Summary | String | Segment summary. Note: This field may return null, indicating that no valid values can be obtained. |
| Title | String | Segment title. |
| Keywords | Array of String | Segment keywords. |
| StartTimeOffset | Float | Segmentation start time point, in seconds. Note: This field may return null, indicating that no valid values can be obtained. |
| EndTimeOffset | Float | Segmentation end time point, in seconds. Note: This field may return null, indicating that no valid values can be obtained. |

## AiQualityControlTaskInput

Input parameter type for media quality inspection.

Used by actions: CreateSchedule, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessLiveStream, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | No | Media quality inspection template ID. You can directly use a preset template or customize a template in the console. The preset templates are as follows: - 10: Enable all quality inspection items. - 20: Only enable quality inspection items corresponding to format diagnosis. - 30: Only enable quality inspection items corresponding to no-reference scoring. - 40: Only enable quality inspection items corresponding to screen quality. Note: This field may return null, indicating that no valid values can be obtained. |
| ChannelExtPara | String | No | The channel extension parameter, which is a serialized JSON string. Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionResult

Intelligent recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | The task type. Valid values: FaceRecognition: Face recognitionAsrWordsRecognition: Speech keyword recognitionOcrWordsRecognition: Text keyword recognitionAsrFullTextRecognition: Full speech recognitionOcrFullTextRecognition: Full text recognitionTransTextRecognition: Speech translation |
| FaceTask | [AiRecognitionTaskFaceResult](#AiRecognitionTaskFaceResult) | Face recognition result, which is valid when `Type` is   `FaceRecognition`. Note: This field may return null, indicating that no valid values can be obtained. |
| AsrWordsTask | [AiRecognitionTaskAsrWordsResult](#AiRecognitionTaskAsrWordsResult) | Speech keyword recognition result, which is valid when `Type` is  `AsrWordsRecognition`. Note: This field may return null, indicating that no valid values can be obtained. |
| AsrFullTextTask | [AiRecognitionTaskAsrFullTextResult](#AiRecognitionTaskAsrFullTextResult) | Full speech recognition result, which is valid when `Type` is  `AsrFullTextRecognition`. Note: This field may return null, indicating that no valid values can be obtained. |
| OcrWordsTask | [AiRecognitionTaskOcrWordsResult](#AiRecognitionTaskOcrWordsResult) | Text keyword recognition result, which is valid when `Type` is  `OcrWordsRecognition`. Note: This field may return null, indicating that no valid values can be obtained. |
| OcrFullTextTask | [AiRecognitionTaskOcrFullTextResult](#AiRecognitionTaskOcrFullTextResult) | Full text recognition result, which is valid when `Type` is  `OcrFullTextRecognition`. Note: This field may return null, indicating that no valid values can be obtained. |
| TransTextTask | [AiRecognitionTaskTransTextResult](#AiRecognitionTaskTransTextResult) | The translation result. This parameter is valid only if `Type` is  `TransTextRecognition`. Note: This field may return null, indicating that no valid values can be obtained. |
| ObjectTask | [AiRecognitionTaskObjectResult](#AiRecognitionTaskObjectResult) | Object recognition result, which is valid when Type is  ObjectRecognition. Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionTaskAsrFullTextResult

Full speech recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiRecognitionTaskAsrFullTextResultInput](#AiRecognitionTaskAsrFullTextResultInput) | Input information of a full speech recognition task. |
| Output | [AiRecognitionTaskAsrFullTextResultOutput](#AiRecognitionTaskAsrFullTextResultOutput) | Output information of a full speech recognition task. Note: This field may return null, indicating that no valid values can be obtained. |
| Progress | Integer | Task progress. Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionTaskAsrFullTextResultInput

Input for full speech recognition.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Full speech recognition template ID. |

## AiRecognitionTaskAsrFullTextResultOutput

Full speech recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| SegmentSet | Array of [AiRecognitionTaskAsrFullTextSegmentItem](#AiRecognitionTaskAsrFullTextSegmentItem) | List of full speech recognition segments. |
| SubtitlePath | String | Subtitles file address. |

## AiRecognitionTaskAsrFullTextSegmentItem

Full speech recognition segment.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Confidence of a recognition segment. Value range: 0-100. |
| StartTimeOffset | Float | Start time offset of a recognition segment in seconds. |
| EndTimeOffset | Float | End time offset of a recognition segment in seconds. |
| Text | String | Recognized text. |
| Wordlist | Array of [WordResult](#WordResult) | Word timestamp information. |

## AiRecognitionTaskAsrWordsResult

Speech keyword recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiRecognitionTaskAsrWordsResultInput](#AiRecognitionTaskAsrWordsResultInput) | Input information of a speech keyword recognition task. |
| Output | [AiRecognitionTaskAsrWordsResultOutput](#AiRecognitionTaskAsrWordsResultOutput) | Output information of a speech keyword recognition task. Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionTaskAsrWordsResultInput

Input for speech keyword recognition.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Speech keyword recognition template ID. |

## AiRecognitionTaskAsrWordsResultItem

Speech keyword recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Word | String | Speech keyword. |
| SegmentSet | Array of [AiRecognitionTaskAsrWordsSegmentItem](#AiRecognitionTaskAsrWordsSegmentItem) | List of time segments that contain the speech keyword. |

## AiRecognitionTaskAsrWordsResultOutput

Output of speech keyword recognition.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| ResultSet | Array of [AiRecognitionTaskAsrWordsResultItem](#AiRecognitionTaskAsrWordsResultItem) | Speech keyword recognition result set. |

## AiRecognitionTaskAsrWordsSegmentItem

Speech recognition segment.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a recognition segment in seconds. |
| EndTimeOffset | Float | End time offset of a recognition segment in seconds. |
| Confidence | Float | Confidence of a recognition segment. Value range: 0-100. |

## AiRecognitionTaskFaceResult

Face recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiRecognitionTaskFaceResultInput](#AiRecognitionTaskFaceResultInput) | Input information of a face recognition task. |
| Output | [AiRecognitionTaskFaceResultOutput](#AiRecognitionTaskFaceResultOutput) | Output information of a face recognition task. Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionTaskFaceResultInput

Face recognition input.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Face recognition template ID. |

## AiRecognitionTaskFaceResultItem

Face recognition result

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Id | String | Unique ID of a figure. |
| Type | String | Figure library type, indicating to which figure library the recognized figure belongs: Default: Default figure library;UserDefine: Custom figure library. |
| Name | String | Name of a figure. |
| SegmentSet | Array of [AiRecognitionTaskFaceSegmentItem](#AiRecognitionTaskFaceSegmentItem) | Result set of segments that contain a figure. |
| Gender | String | Gender of the person. Male: man.. Female: specifies the woman.. |
| Birthday | String | Date of birth. |
| Profession | String | Occupation or position of a person. |
| SchoolOfGraduation | String | Specifies the graduation institution of the person. |
| Abstract | String | Description of the person. |
| PlaceOfBirth | String | Specifies the birthplace or place of origin. |
| PersonType | String | Person type. Politician: specifies the official.. Artist: specifies the artist.. |
| Remark | String | Sensitivity labeling. Normal: specifies the scaling group is normal.. Sensitive: specifies sensitivity.. |
| Url | String | Specifies the screenshot link. |

## AiRecognitionTaskFaceResultOutput

Output of intelligent face recognition.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| ResultSet | Array of [AiRecognitionTaskFaceResultItem](#AiRecognitionTaskFaceResultItem) | Intelligent face recognition result set. |

## AiRecognitionTaskFaceSegmentItem

Face recognition result segment

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a recognition segment in seconds. |
| EndTimeOffset | Float | End time offset of a recognition segment in seconds. |
| Confidence | Float | Confidence of a recognition segment. Value range: 0-100. |
| AreaCoordSet | Array of Integer | Zone coordinates of a recognition result. The array contains four elements: [x1,y1,x2,y2], i.e., the horizontal and vertical coordinates of the top-left and bottom-right corners. |

## AiRecognitionTaskInput

Input parameter type of video content recognition

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, DescribeWorkflows, ModifySchedule, ParseNotification, ProcessLiveStream, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | Intelligent video recognition template ID. |
| UserExtPara | String | No | User extension field, which does not need to be filled in for general scenarios. |

## AiRecognitionTaskObjectResult

Object recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCode | Integer | Error code. `0`: Task successful. Other values: Task failed. |
| Message | String | Error message. |
| Input | [AiRecognitionTaskObjectResultInput](#AiRecognitionTaskObjectResultInput) | Object recognition task input. |
| Output | [AiRecognitionTaskObjectResultOutput](#AiRecognitionTaskObjectResultOutput) | Object recognition task output.Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionTaskObjectResultInput

Object recognition task input type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Object recognition template ID. |

## AiRecognitionTaskObjectResultItem

Single object recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Name | String | Name of a recognized object. |
| SegmentSet | Array of [AiRecognitionTaskObjectSeqmentItem](#AiRecognitionTaskObjectSeqmentItem) | List of segments that contain the object. |

## AiRecognitionTaskObjectResultOutput

Intelligent object recognition output.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| ResultSet | Array of [AiRecognitionTaskObjectResultItem](#AiRecognitionTaskObjectResultItem) | Intelligent object recognition result set. |

## AiRecognitionTaskObjectSeqmentItem

Object recognition result segment.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a recognized segment, in seconds. |
| EndTimeOffset | Float | End time offset of a recognized segment, in seconds. |
| Confidence | Float | Confidence of a recognized segment. Value range: 0-100. |
| AreaCoordSet | Array of Integer | Zone coordinates of the recognition result. An array contains four elements: [x1, y1, x2, y2], representing the horizontal and vertical coordinates of the top-left and bottom-right corners, respectively. |

## AiRecognitionTaskOcrFullTextResult

Full text recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiRecognitionTaskOcrFullTextResultInput](#AiRecognitionTaskOcrFullTextResultInput) | Input information of a full text recognition task. |
| Output | [AiRecognitionTaskOcrFullTextResultOutput](#AiRecognitionTaskOcrFullTextResultOutput) | Output information of a full text recognition task. Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionTaskOcrFullTextResultInput

Input for full text recognition.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Full text recognition template ID. |

## AiRecognitionTaskOcrFullTextResultOutput

Output of full text recognition.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| SegmentSet | Array of [AiRecognitionTaskOcrFullTextSegmentItem](#AiRecognitionTaskOcrFullTextSegmentItem) | Full text recognition result set. |

## AiRecognitionTaskOcrFullTextSegmentItem

Full text recognition segment.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a recognition segment in seconds. |
| EndTimeOffset | Float | End time offset of a recognition segment in seconds. |
| TextSet | Array of [AiRecognitionTaskOcrFullTextSegmentTextItem](#AiRecognitionTaskOcrFullTextSegmentTextItem) | Recognition segment result set. |

## AiRecognitionTaskOcrFullTextSegmentTextItem

Full text recognition segment.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Confidence of a recognition segment. Value range: 0-100. |
| AreaCoordSet | Array of Integer | Zone coordinates of a recognition result. The array contains four elements: [x1,y1,x2,y2], i.e., the horizontal and vertical coordinates of the top-left and bottom-right corners. |
| Text | String | Recognized text. |

## AiRecognitionTaskOcrWordsResult

Text keyword recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiRecognitionTaskOcrWordsResultInput](#AiRecognitionTaskOcrWordsResultInput) | Input information of a text keyword recognition task. |
| Output | [AiRecognitionTaskOcrWordsResultOutput](#AiRecognitionTaskOcrWordsResultOutput) | Output information of a text keyword recognition task. Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionTaskOcrWordsResultInput

Input for text keyword recognition.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Text keyword recognition template ID. |

## AiRecognitionTaskOcrWordsResultItem

Text keyword recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Word | String | Text keyword. |
| SegmentSet | Array of [AiRecognitionTaskOcrWordsSegmentItem](#AiRecognitionTaskOcrWordsSegmentItem) | List of segments that contain a text keyword. |

## AiRecognitionTaskOcrWordsResultOutput

Output of text keyword recognition.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| ResultSet | Array of [AiRecognitionTaskOcrWordsResultItem](#AiRecognitionTaskOcrWordsResultItem) | Text keyword recognition result set. |

## AiRecognitionTaskOcrWordsSegmentItem

Text recognition segment.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a recognition segment in seconds. |
| EndTimeOffset | Float | End time offset of a recognition segment in seconds. |
| Confidence | Float | Confidence of a recognition segment. Value range: 0-100. |
| AreaCoordSet | Array of Integer | Zone coordinates of a recognition result. The array contains four elements: [x1,y1,x2,y2], i.e., the horizontal and vertical coordinates of the top-left and bottom-right corners. |

## AiRecognitionTaskTransTextResult

The translation result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | The task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value indicates the task has failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | The error code. `0` indicates the task is successful; other values indicate the task has failed. This parameter is not recommended. Please use `ErrCodeExt` instead. |
| Message | String | The error message. |
| Input | [AiRecognitionTaskTransTextResultInput](#AiRecognitionTaskTransTextResultInput) | The input of the translation task. |
| Output | [AiRecognitionTaskTransTextResultOutput](#AiRecognitionTaskTransTextResultOutput) | The output of the translation task. Note: This field may return null, indicating that no valid values can be obtained. |
| Progress | Integer | Task progress. Note: This field may return null, indicating that no valid values can be obtained. |

## AiRecognitionTaskTransTextResultInput

The translation input.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | The translation template ID. |

## AiRecognitionTaskTransTextResultOutput

The translation result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| SegmentSet | Array of [AiRecognitionTaskTransTextSegmentItem](#AiRecognitionTaskTransTextSegmentItem) | The translated segments. |
| SubtitlePath | String | The subtitle URL. |

## AiRecognitionTaskTransTextSegmentItem

The translated segments.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | The confidence score for a segment. Value range: 0-100. |
| StartTimeOffset | Float | The start time offset (seconds) of a segment. |
| EndTimeOffset | Float | The end time offset (seconds) of a segment. |
| Text | String | The text transcript. |
| Trans | String | The translation. |
| Wordlist | Array of [WordResult](#WordResult) | Word timestamp information. |

## AiReviewPoliticalAsrTaskInput

The input parameters for ASR-based detection of politically sensitive information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | The template ID. |

## AiReviewPoliticalAsrTaskOutput

The information about the sensitive content detected based on ASR.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | The confidence score for the ASR-based detection of sensitive information. Value range: 0-100. |
| Suggestion | String | The suggestion for handling the sensitive information detected based on ASR. Valid values: passreviewblock |
| SegmentSet | Array of [MediaContentReviewAsrTextSegmentItem](#MediaContentReviewAsrTextSegmentItem) | The video segments that contain sensitive information detected based on ASR. |

## AiReviewPoliticalOcrTaskInput

The input parameters for OCR-based detection of politically sensitive information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | The template ID. |

## AiReviewPoliticalOcrTaskOutput

The information about the sensitive content detected based on OCR.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | The confidence score for the OCR-based detection of sensitive information. Value range: 0-100. |
| Suggestion | String | The suggestion for handling the sensitive information detected based on OCR. Valid values: passreviewblock |
| SegmentSet | Array of [MediaContentReviewOcrTextSegmentItem](#MediaContentReviewOcrTextSegmentItem) | The video segments that contain sensitive information detected based on OCR. |

## AiReviewPoliticalTaskInput

The input parameters for the detection of politically sensitive information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | The template ID. |

## AiReviewPoliticalTaskOutput

The sensitive information detected.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | The confidence score for the detection of sensitive information. Value range: 0-100. |
| Suggestion | String | The suggestion for handling the sensitive information detected. Valid values: passreviewblock |
| Label | String | The labels for the detected sensitive content. The relationship between the values of this parameter and those of the `LabelSet` parameter in [PoliticalImgReviewTemplateInfo](https://intl.cloud.tencent.com/document/api/862/37615?from_cn_redirect=1#AiReviewPoliticalTaskOutput) is as follows: violation_photo: violation_photo (banned icons) Other values (politician/entertainment/sport/entrepreneur/scholar/celebrity/military): politician |
| SegmentSet | Array of [MediaContentReviewPoliticalSegmentItem](#MediaContentReviewPoliticalSegmentItem) | The video segments that contain sensitive information. |

## AiReviewPornAsrTaskInput

Input parameter type of an ASR-based porn information detection in text task during content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | ID of a porn information detection template. |

## AiReviewPornAsrTaskOutput

ASR-detected porn information in text

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Score of the ASR-detected porn information in text from 0 to 100. |
| Suggestion | String | Suggestion for the ASR-detected porn information in text. Valid values: pass.review.block. |
| SegmentSet | Array of [MediaContentReviewAsrTextSegmentItem](#MediaContentReviewAsrTextSegmentItem) | List of video segments that contain the ASR-detected porn information in text. |

## AiReviewPornOcrTaskInput

Input parameter type of an OCR-based porn information detection in text task during content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | ID of a porn information detection template. |

## AiReviewPornOcrTaskOutput

OCR-detected porn information in text

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Score of the OCR-detected porn information in text from 0 to 100. |
| Suggestion | String | Suggestion for the OCR-detected porn information in text. Valid values: pass.review.block. |
| SegmentSet | Array of [MediaContentReviewOcrTextSegmentItem](#MediaContentReviewOcrTextSegmentItem) | List of video segments that contain the OCR-detected porn information in text. |

## AiReviewPornTaskInput

Input parameter type of a porn information detection task during content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | The ID of a porn detection template. Note: This field may return null, indicating that no valid values can be obtained. |

## AiReviewPornTaskOutput

Porn information detection result

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Score of the detected porn information in video from 0 to 100. |
| Suggestion | String | Suggestion for the detected porn information. Valid values: pass.review.block. |
| Label | String | Tag of the detected porn information in video. Valid values: porn: Porn.sexy: Sexiness.vulgar: Vulgarity.intimacy: Intimacy. |
| SegmentSet | Array of [MediaContentReviewSegmentItem](#MediaContentReviewSegmentItem) | List of video segments that contain the detected porn information. |

## AiReviewProhibitedAsrTaskInput

Input parameter type of ASR-based prohibited information detection in speech task in content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Prohibited information detection template ID. |

## AiReviewProhibitedAsrTaskOutput

ASR-detected prohibited information in speech

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Score of ASR-detected prohibited information in speech between 0 and 100. |
| Suggestion | String | Suggestion for ASR-detected prohibited information in speech. Valid values: pass.review.block. |
| SegmentSet | Array of [MediaContentReviewAsrTextSegmentItem](#MediaContentReviewAsrTextSegmentItem) | List of video segments that contain the ASR-detected prohibited information in speech. |

## AiReviewProhibitedOcrTaskInput

Input parameter type of OCR-based prohibited information detection in text task in content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Prohibited information detection template ID. |

## AiReviewProhibitedOcrTaskOutput

OCR-detected prohibited information in text

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Score of OCR-detected prohibited information in text between 0 and 100. |
| Suggestion | String | Suggestion for OCR-detected prohibited information in text. Valid values: pass.review.block. |
| SegmentSet | Array of [MediaContentReviewOcrTextSegmentItem](#MediaContentReviewOcrTextSegmentItem) | List of video segments that contain the OCR-detected prohibited information in text. |

## AiReviewTaskPoliticalAsrResult

The result of ASR-based detection of politically sensitive information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiReviewPoliticalAsrTaskInput](#AiReviewPoliticalAsrTaskInput) | The input parameter for ASR-based detection of politically sensitive information. |
| Output | [AiReviewPoliticalAsrTaskOutput](#AiReviewPoliticalAsrTaskOutput) | The output of ASR-based detection of politically sensitive information. Note: This field may return `null`, indicating that no valid values can be obtained. |

## AiReviewTaskPoliticalOcrResult

The result of OCR-based detection of politically sensitive information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. Note: This field may return null, indicating that no valid values can be obtained. |
| Input | [AiReviewPoliticalOcrTaskInput](#AiReviewPoliticalOcrTaskInput) | The input parameter for OCR-based detection of politically sensitive information. |
| Output | [AiReviewPoliticalOcrTaskOutput](#AiReviewPoliticalOcrTaskOutput) | The output of OCR-based detection of politically sensitive information. Note: This field may return `null`, indicating that no valid values can be obtained. |

## AiReviewTaskPoliticalResult

The result of sensitive information detection.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiReviewPoliticalTaskInput](#AiReviewPoliticalTaskInput) | The input parameter for sensitive information detection. |
| Output | [AiReviewPoliticalTaskOutput](#AiReviewPoliticalTaskOutput) | The output of sensitive information detection. Note: This field may return `null`, indicating that no valid values can be obtained. |

## AiReviewTaskPornAsrResult

Result type of an ASR-based porn information detection in text task during content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiReviewPornAsrTaskInput](#AiReviewPornAsrTaskInput) | Input for an ASR-based porn information detection in text task during content audit. |
| Output | [AiReviewPornAsrTaskOutput](#AiReviewPornAsrTaskOutput) | Output of an ASR-based porn information detection in text task during content audit. Note: This field may return null, indicating that no valid values can be obtained. |

## AiReviewTaskPornOcrResult

Result type of an OCR-based porn information detection in text task during content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiReviewPornOcrTaskInput](#AiReviewPornOcrTaskInput) | Input for an OCR-based porn information detection in text task during content audit. |
| Output | [AiReviewPornOcrTaskOutput](#AiReviewPornOcrTaskOutput) | Output of an OCR-based porn information detection in text task during content audit. Note: This field may return null, indicating that no valid values can be obtained. |

## AiReviewTaskPornResult

Result type of a porn information detection task during content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. Note: This field may return null, indicating that no valid values can be obtained. |
| Input | [AiReviewPornTaskInput](#AiReviewPornTaskInput) | Input for a porn information detection task during content audit. |
| Output | [AiReviewPornTaskOutput](#AiReviewPornTaskOutput) | Output of a porn information detection task during content audit. Note: This field may return null, indicating that no valid values can be obtained. |

## AiReviewTaskProhibitedAsrResult

Result type of ASR-based prohibited information detection in speech task in content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0: success; other values: failure. 40000: invalid input parameter. Please check it;60000: invalid source file (e.g., video data is corrupted). Please check whether the source file is normal;70000: internal service error. Please try again. |
| Message | String | Error message. |
| Input | [AiReviewProhibitedAsrTaskInput](#AiReviewProhibitedAsrTaskInput) | Input of ASR-based prohibited information detection in speech task in content audit |
| Output | [AiReviewProhibitedAsrTaskOutput](#AiReviewProhibitedAsrTaskOutput) | Output of ASR-based prohibited information detection in speech task in content audit |

## AiReviewTaskProhibitedOcrResult

Result type of OCR-based prohibited information detection in text task in content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0: success; other values: failure. 40000: invalid input parameter. Please check it;60000: invalid source file (e.g., video data is corrupted). Please check whether the source file is normal;70000: internal service error. Please try again. |
| Message | String | Error message. |
| Input | [AiReviewProhibitedOcrTaskInput](#AiReviewProhibitedOcrTaskInput) | Input of OCR-based prohibited information detection in text task in content audit |
| Output | [AiReviewProhibitedOcrTaskOutput](#AiReviewProhibitedOcrTaskOutput) | Output of OCR-based prohibited information detection in text task in content audit |

## AiReviewTaskTerrorismOcrResult

The result of OCR-based detection of terrorism content.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0: success; other values: failure. 40000: invalid input parameter. Please check it;60000: invalid source file (e.g., video data is corrupted). Please check whether the source file is normal;70000: internal service error. Please try again. |
| Message | String | Error message. |
| Input | [AiReviewTerrorismOcrTaskInput](#AiReviewTerrorismOcrTaskInput) | The input parameter for OCR-based detection of terrorism content. |
| Output | [AiReviewTerrorismOcrTaskOutput](#AiReviewTerrorismOcrTaskOutput) | The output of OCR-based detection of terrorism content. Note: This field may return `null`, indicating that no valid values can be obtained. |

## AiReviewTaskTerrorismResult

The result of sensitive information detection.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AiReviewTerrorismTaskInput](#AiReviewTerrorismTaskInput) | The input parameter for sensitive information detection. |
| Output | [AiReviewTerrorismTaskOutput](#AiReviewTerrorismTaskOutput) | The output of sensitive information detection. Note: This field may return `null`, indicating that no valid values can be obtained. |

## AiReviewTerrorismOcrTaskInput

The input parameter for OCR-based detection of sensitive information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | The template ID. |

## AiReviewTerrorismOcrTaskOutput

The information about the sensitive content detected based on OCR.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | The confidence score for the OCR-based detection of sensitive information. Value range: 1-100. |
| Suggestion | String | The suggestion for handling the sensitive information detected based on OCR. Valid values: passreviewblock |
| SegmentSet | Array of [MediaContentReviewOcrTextSegmentItem](#MediaContentReviewOcrTextSegmentItem) | The video segments that contain sensitive information detected based on OCR. |

## AiReviewTerrorismTaskInput

The input parameter for the detection of sensitive information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | The template ID. |

## AiReviewTerrorismTaskOutput

The information about the sensitive content detected.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | The confidence score for the detection of sensitive information. Value range: 0-100. |
| Suggestion | String | The suggestion for handling the sensitive information detected. Valid values: passreviewblock |
| Label | String | The labels for the detected sensitive content. Valid values: gunscrowdpolicebloodybanners (sensitive flags)militantexplosionterroristsscenario (sensitive scenes) |
| SegmentSet | Array of [MediaContentReviewSegmentItem](#MediaContentReviewSegmentItem) | The video segments that contain sensitive information. |

## AiSampleFaceInfo

AI-based sample management - face information.

Used by actions: CreatePersonSample, DescribePersonSamples, ModifyPersonSample.

| Name | Type | Description |
| --- | --- | --- |
| FaceId | String | Face image ID. |
| Url | String | Face image address. |

## AiSampleFaceOperation

AI-based sample management - face data operation.

Used by actions: ModifyPersonSample.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | Operation type. Valid values: add, delete, reset. The `reset` operation will clear the existing face data of a figure and add `FaceContents` as the specified face data. |
| FaceIds | Array of String | No | Face ID set. This field is required when `Type` is `delete`. |
| FaceContents | Array of String | No | String set generated by [Base64-encoding](https://tools.ietf.org/html/rfc4648) the face image. This field is required when `Type` is `add` or `reset`;Array length limit: 5 images. Note: The image must be a relatively clear full-face photo of a figure in at least 200 * 200 px. |

## AiSampleFailFaceInfo

AI-based sample management - face information failing to be processed.

Used by actions: CreatePersonSample, ModifyPersonSample.

| Name | Type | Description |
| --- | --- | --- |
| Index | Integer | Corresponds to incorrect image subscripts in the `FaceContents` input parameter, starting from 0. |
| ErrCode | Integer | Error code. Valid values: 0: Succeeded;Other values: Failed. |
| Message | String | Error description. |

## AiSamplePerson

AI-based sample management - figure information.

Used by actions: CreatePersonSample, DescribePersonSamples, ModifyPersonSample.

| Name | Type | Description |
| --- | --- | --- |
| PersonId | String | Figure ID. |
| Name | String | Name of a figure. |
| Description | String | Figure description. |
| FaceInfoSet | Array of [AiSampleFaceInfo](#AiSampleFaceInfo) | Face information. |
| TagSet | Array of String | Figure tag. |
| UsageSet | Array of String | Use case. |
| CreateTime | String | Creation time in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## AiSampleTagOperation

AI-based sample management - tag operation.

Used by actions: ModifyPersonSample, ModifyWordSample.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | Operation type. Valid values: add, delete, reset. |
| Tags | Array of String | Yes | Tag. Length limit: 128 characters. |

## AiSampleWord

AI-based sample management - keyword output information.

Used by actions: DescribeWordSamples.

| Name | Type | Description |
| --- | --- | --- |
| Keyword | String | Keyword. |
| TagSet | Array of String | Keyword tag. |
| UsageSet | Array of String | Keyword use case. |
| CreateTime | String | Creation time in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## AiSampleWordInfo

AI-based sample management - keyword input information.

Used by actions: CreateWordSamples.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Keyword | String | Yes | Keyword. Length limit: 20 characters. |
| Tags | Array of String | No | Keyword tag Array length limit: 20 tags;Tag length limit: 128 characters. |

## AigcImageExtraParam

Extended parameters used for AIGC image generation.

Used by actions: CreateAigcImageTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| AspectRatio | String | No | The aspect ratio of the generated video.Supported aspect ratios for different models:1. GEM: 1:1, 3:2, 2:3, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9, and 21:9.Note: For more information about the aspect ratios of specific models, see the model website. |
| Resolution | String | No | Output resolution of the image.Models that support this parameter:Valid values: 720P, 1080P, 2K, and 4K. |

## AigcImageInfo

Image information for AIGC generation.

Used by actions: CreateAigcImageTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImageUrl | String | No | Image URL for video generation. The URL must be accessible from the public network and must be accessible to crawlers. |
| ReferenceType | String | No | Reference type. Note:1. When the model uses Vidu's q2 multi-reference image generation, this can also be used to specify the subject ID.2. If the GV model is used, this serves as the reference method. Valid values are asset and style. |

## AigcStoreCosParam

Information required for uploading AIGC result files to COS. The LVB_QCSRole role needs to be created and authorized.

Used by actions: CreateAigcImageTask, CreateAigcVideoTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| CosBucketName | String | No | Name of the COS bucket to store to. This value is required if you need to store the results in COS. Example value: bucket. |
| CosBucketRegion | String | No | Region of the COS bucket to store to. This is required if you need to upload the results to COS. Example value: ap-guangzhou. |
| CosBucketPath | String | No | Path of the COS bucket to store to.Optional.Example value: my_file. |

## AigcVideoExtraParam

Extended parameters used for AIGC video generation.

Used by actions: CreateAigcVideoTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Resolution | String | No | The resolution of the generated video, which is related to the selected model and set video duration.Supported resolution options for different models:1. Kling: 720P (default) and 1080P.2. Hailuo: 768P (default) and 1080P.3. Vidu: 720P (default) and 1080P.4. GV: 720P (default) and 1080P.5. OS: 720P. For images, only 1280x720 and 720x1280 are supported. Resolution cannot be specified.Note: In addition to the resolution supported by the model, 2K and 4K resolutions are also available. |
| AspectRatio | String | No | The aspect ratio of the generated video.Support for this parameter by different models:1. Kling only supports this parameter for text-to-video, with aspect ratios of 16:9 (default), 9:16, and 1:1.2. Hailuo does not support this parameter.3. Vidu supports [16:9, 9:16, 4:3, 3:4, 1:1] for text-to-video and reference image-to-video only. Only q2 supports 4:3 and 3:4.4. GV supports 16:9 (default) and 9:16.5. OS only supports this parameter for text-to-video, with aspect ratios of 16:9 (default) and 9:16.Note: For more information about the supported aspect ratios of specific models, see the model website. |
| LogoAdd | Integer | No | Indicates whether to add a logo watermark.1. Hailuo supports this parameter.2. Kling supports this parameter. 3. Vidu supports this parameter. |
| EnableAudio | Boolean | No | Indicates whether to generate audio for the video. Valid values: true or false.Models that support this parameter:1. GV. Default value: true.2. OS. Default value: true. |
| OffPeak | Boolean | No | Indicates whether to use the off-peak scheduling mode. Only Vidu supports this parameter.Tasks submitted in off-peak mode will be processed within 48 hours. Uncompleted tasks will be canceled. |

## AigcVideoReferenceImageInfo

Reference image information for AIGC video generation.

Used by actions: CreateAigcVideoTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImageUrl | String | No | Image URL for video generation. The URL must be accessible from the public network and must be accessible to crawlers. |
| ReferenceType | String | No | Reference type. Note:1. If the GV model is used, this serves as the reference method. Valid values are asset and style. |

## AigcVideoReferenceVideoInfo

Used by actions: CreateAigcVideoTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| VideoUrl | String | No |  |
| ReferType | String | No |  |
| KeepOriginalSound | String | No |  |

## AnimatedGraphicTaskInput

Type of an animated image generating task.

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | Animated image generating template ID. |
| StartTimeOffset | Float | Yes | Start time of an animated image in a video in seconds. |
| EndTimeOffset | Float | Yes | End time of an animated image in a video in seconds. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | Target bucket of a generated animated image file. If this parameter is left empty, the `OutputStorage` value of the upper folder will be inherited. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputObjectPath | String | No | Output path of a file after animated image generating, which can be a relative or absolute path. If you need to define an output path, the path must end with `.{format}`. For variable names, refer to [Filename Variable](https://intl.cloud.tencent.com/document/product/862/37039?from_cn_redirect=1). Relative path example: Filename_{Variable name}.{format}.Filename.{format}. Absolute path example: /Custom path/Filename_{Variable name}.{format}. If left empty, a relative path is used by default: `{inputName}_animatedGraphic_{definition}.{format}`. |

## AnimatedGraphicsTemplate

Details of an animated image generating template.

Used by actions: DescribeAnimatedGraphicsTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of an animated image generating template. |
| Type | String | Template type. Valid values: Preset: Preset template;Custom: Custom template. |
| Name | String | Name of an animated image generating template. |
| Comment | String | Description of an animated image generating template. |
| Width | Integer | Maximum value of the width (or long side) of an animated image in px. Value range: 0 and [128, 4,096]. If both `Width` and `Height` are 0, the resolution will be the same as that of the source video;If `Width` is 0, but `Height` is not 0, `Width` will be proportionally scaled;If `Width` is not 0, but `Height` is 0, `Height` will be proportionally scaled;If both `Width` and `Height` are not 0, the custom resolution will be used. Default value: 0. |
| Height | Integer | Maximum value of the height (or short side) of an animated image in px. Value range: 0 and [128, 4,096]. If both `Width` and `Height` are 0, the resolution will be the same as that of the source video;If `Width` is 0, but `Height` is not 0, `Width` will be proportionally scaled;If `Width` is not 0, but `Height` is 0, `Height` will be proportionally scaled;If both `Width` and `Height` are not 0, the custom resolution will be used. Default value: 0. |
| ResolutionAdaptive | String | Resolution adaption. Valid values: open: Enabled. In this case, `Width` represents the long side of a video, while `Height` the short side;close: Disabled. In this case, `Width` represents the width of a video, while `Height` the height. Default value: open. |
| Format | String | Animated image format. |
| Fps | Integer | Frame rate. |
| Quality | Float | Image quality. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## ArtifactRepairConfig

Artifact removal (smoothing) configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Type | String | No | The strength. Valid values: weakstrong Default value: weak. Note: This field may return null, indicating that no valid values can be obtained. |

## AsrFullTextConfigureInfo

Control parameter of a full speech recognition task.

Used by actions: CreateAIRecognitionTemplate, DescribeAIRecognitionTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a full speech recognition task. Valid values: ON: Enables an intelligent full speech recognition task;OFF: Disables an intelligent full speech recognition task. |
| SubtitleFormat | String | No | Format of the generated subtitles file. If this parameter is left empty or an empty string is entered, no subtitles files will be generated. Valid value: vtt: Generates a WebVTT subtitles file. |

## AsrFullTextConfigureInfoForUpdate

Control parameter of a full speech recognition task.

Used by actions: ModifyAIRecognitionTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a full speech recognition task. Valid values: ON: Enables an intelligent full speech recognition task;OFF: Disables an intelligent full speech recognition task. |
| SubtitleFormat | String | No | Format of the generated subtitles file. If an empty string is entered, no subtitles files will be generated. Valid value: vtt: Generates a WebVTT subtitles file. |

## AsrHotWordsConfigure

Smart subtitle hotword parameter.

Used by actions: BatchProcessMedia, CreateSmartSubtitleTemplate, DescribeSmartSubtitleTemplates, ModifySmartSubtitleTemplate, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Hotword switch. Note: This field may return null, indicating that no valid value can be obtained. |
| LibraryId | String | No | Hotword lexicon ID. Note: This field may return null, indicating that no valid value can be obtained. |

## AsrHotwordsSet

Returned result set of hotword lexicon query.

Used by actions: DescribeAsrHotwordsList.

| Name | Type | Description |
| --- | --- | --- |
| HotwordsId | String | Hotword lexicon ID. Note: This field may return null, indicating that no valid value can be obtained. |
| Status | Integer | Current hotword lexicon status. The value indicates the number of smart subtitle templates bound to this hotword lexicon. If the value of Status is 0, it indicates that the hotword lexicon is not referenced by any smart subtitle template and that it can be deleted. If the value of Status is not 0, it indicates that the hotword lexicon cannot be deleted. Note: This field may return null, indicating that no valid value can be obtained. |
| Name | String | Hotword lexicon name. Note: This field may return null, indicating that no valid value can be obtained. |
| WordCount | Integer | Number of hotwords in the hotword lexicon. Note: This field may return null, indicating that no valid value can be obtained. |
| FileName | String | Name of the uploaded hotword file. Note: This field may return null, indicating that no valid value can be obtained. |
| CreateTime | String | Creation time of the hotword lexicon in ISO datetime format (UTC time). For example, 2006-01-02T15:04:05Z. Note: This field may return null, indicating that no valid value can be obtained. |
| UpdateTime | String | Creation time of the hotword lexicon in ISO datetime format (UTC time). For example, 2006-01-02T15:04:05Z. Note: This field may return null, indicating that no valid value can be obtained. |
| Type | Integer | 0: temporary hotword lexicon 1: file-based hotword lexicon Note: This field may return null, indicating that no valid value can be obtained. |

## AsrHotwordsSetItem

Information on a single hotword.

Used by actions: DescribeAsrHotwords.

| Name | Type | Description |
| --- | --- | --- |
| Id | Integer | Hotword ID. Note: This field may return null, indicating that no valid value can be obtained. |
| Text | String | Hotword text. Note: This field may return null, indicating that no valid value can be obtained. |
| Weight | Integer | Hotword weight. The value can be 11 or 100 or be in the range of 1 to 10. Note: This field may return null, indicating that no valid value can be obtained. |

## AsrWordsConfigureInfo

Speech keyword recognition control parameter.

Used by actions: CreateAIRecognitionTemplate, DescribeAIRecognitionTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a speech keyword recognition task. Valid values: ON: Enables a speech keyword recognition task;OFF: Disables a speech keyword recognition task. |
| LabelSet | Array of String | No | Keyword filter tag, which specifies the keyword tag that needs to be returned. If this parameter is left empty, all results will be returned. There can be up to 10 tags, each with a length limit of 16 characters. |

## AsrWordsConfigureInfoForUpdate

Speech keyword recognition control parameter.

Used by actions: ModifyAIRecognitionTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a speech keyword recognition task. Valid values: ON: Enables a speech keyword recognition task;OFF: Disables a speech keyword recognition task. |
| LabelSet | Array of String | No | Keyword filter tag, which specifies the keyword tag that needs to be returned. If this parameter is left empty, all results will be returned. There can be up to 10 tags, each with a length limit of 16 characters. |

## AudioBeautifyConfig

The audio improvement configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: `ON``OFF`  Default value: `ON`. |
| Types | Array of String | No | The audio improvement options. You can specify multiple options. Valid values: `declick`: Noise removal.`deesser`: De-essing. Default: `declick`. Note: This field may return null, indicating that no valid values can be obtained. |

## AudioDenoiseConfig

The noise reduction configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: `ON``OFF`  Default value: `ON`. |

## AudioEnhanceConfig

The audio enhancement configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Denoise | [AudioDenoiseConfig](#AudioDenoiseConfig) | No | The audio noise reduction configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| Separate | [AudioSeparateConfig](#AudioSeparateConfig) | No | The audio separation configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| VolumeBalance | [VolumeBalanceConfig](#VolumeBalanceConfig) | No | The volume equalization configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| Beautify | [AudioBeautifyConfig](#AudioBeautifyConfig) | No | The audio improvement configuration. Note: This field may return null, indicating that no valid values can be obtained. |

## AudioSeparateConfig

The audio separation configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: `ON``OFF`  Default value: `ON`. |
| Type | String | No | The scenario. Valid values: `normal`: Separate voice and background audio.`music`: Separate vocals and instrumentals. Default value: `normal`. Note: This field may return null, indicating that no valid values can be obtained. |
| Track | String | No | The output audio track. Valid values: `vocal`: Voice.`background`: Output background audio if the scenario is `normal`, and output instrumentals if the scenario is `music`. Default value: `vocal`. Note: This field may return null, indicating that no valid values can be obtained. |

## AudioTemplateInfo

Audio stream configuration parameter

Used by actions: CreateAdaptiveDynamicStreamingTemplate, CreateTranscodeTemplate, CreateWorkflow, DescribeTranscodeTemplates, ModifyAdaptiveDynamicStreamingTemplate, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Codec | String | Yes | Specifies the encoding format of the audio stream. When audio transcoding is not needed, the optional values are:. copy. When the outer parameter Container is mp3, the valid values are:. mp3. When the outer parameter Container is ogg or flac, the valid values are:. flac. When the outer parameter Container is m4a, valid values are:. aac;ac3. When the outer parameter Container is mp4 or flv, valid values are:. aac: more suitable for mp4;. mp3: more suitable for flv;. mp2. When the outer parameter Container is hls, valid values are:. aac;mp3;eac3: used when merging adaptive transcoding audio tracks.. |
| Bitrate | Integer | Yes | The bitrate of the audio stream. value ranges from 0 to 26 and in the range of [26, 256]. measurement unit: kbps. If the value is 0, the audio bitrate will be the same as that of the original audio. Specifies that when using the TrackChannelInfo parameter for adaptive transcoding audio track merging, the valid values are:. Cannot be set to 0. 2). when Codec is aac, valid values: [26, 256]. 3). when Codec is ac3, valid values: [26, 640]. 4) when Codec is eac3, value range: [26, 6144]. remark: when SampleRate is 44100HZ, maximum value: 5644. when SampleRate is 48000HZ, maximum value: 6144. |
| SampleRate | Integer | Yes | Sampling rate of the audio stream. Different encoding standards support different sampling rate options. The value of 0 indicates using the sampling rate value of the source audio. For details, see [Supported Range of Audio Sampling Rate](https://www.tencentcloud.comom/document/product/862/77166?from_cn_redirect=1#f3b039f1-d817-4a96-b4e4-90132d31cd53). Unit: Hz. Note: Make sure that the sampling rate of the source audio stream is among the above options. Otherwise, transcoding may fail. |
| AudioChannel | Integer | No | Audio channel mode. Valid values: 1: mono-channel.2: dual-channel.6: 5.1 surround sound. Default value: 2. When the container format is audio (flac, ogg, mp3, and m4a), the audio channel cannot be set to 5.1 surround sound. |
| TrackChannelInfo | [AudioTrackChannelInfo](#AudioTrackChannelInfo) | No | Merge audio track information. This field only takes effect in adaptive bitrate transcoding.  Note: This field may return null, indicating that no valid value can be obtained. |

## AudioTemplateInfoForUpdate

Audio stream configuration parameter

Used by actions: CreateWorkflow, ModifyTranscodeTemplate, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Codec | String | No | Audio stream encoding format. When audio transcoding is not needed, the value is: copy. When the outer parameter Container is mp3, the value is: mp3. When the outer parameter Container is ogg or flac, the value is: flac. When the outer parameter Container is m4a, valid values are: aac;ac3. When the outer parameter Container is mp4 or flv, valid values are: aac: more suitable for mp4;mp3: more suitable for flv;mp2. When the outer parameter Container is hls, valid values are: aac;mp3. Note: This field may return null, indicating that no valid values can be obtained. |
| Bitrate | Integer | No | Audio stream bitrate in Kbps. Value range: 0 and [26, 256]. If the value is 0, the bitrate of the audio stream will be the same as that of the original audio. |
| SampleRate | Integer | No | Sampling rate of the audio stream. Different encoding standards support different sampling rate options. The value of 0 indicates using the sampling rate value of the source audio. For details, see [Supported Range of Audio Sampling Rate](https://www.tencentcloud.comom/document/product/862/77166?from_cn_redirect=1#f3b039f1-d817-4a96-b4e4-90132d31cd53). Unit: Hz. Note: Make sure that the sampling rate of the source audio stream is among the above options. Otherwise, transcoding may fail. Note: This field may return null, indicating that no valid values can be obtained. |
| AudioChannel | Integer | No | Audio channel mode. Valid values: 1: mono-channel.2: dual-channel.6: 5.1 surround sound. When the container format is audio (flac, ogg, mp3, and m4a), the audio channel cannot be set to 5.1 surround sound.  Note: This field may return null, indicating that no valid values can be obtained. |
| StreamSelects | Array of Integer | No | The audio tracks to retain. All audio tracks are retained by default. |

## AudioTrackChannelInfo

Audio track information.

Used by actions: CreateTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ChannelsRemix | Integer | No | Whether to enable the feature of multi-audio track mixing. Valid values: 0: To disable the multi-audio track mixing feature. 1: To enable the multi-audio track mixing feature.  Default value: 0.  Note: This field may return null, indicating that no valid value can be obtained. |
| SelectType | String | No | Set the selector type for the input audio track. Valid values: track: indicates the usage of audio track id to identify the track to be used. track_channel: indicates the usage of both the audio track id and sound channel id to identify the track and channel to be used. Default value: track. If the original audio track has multiple sound channels, please use track_channel.  Note: This field may return null, indicating that no valid value can be obtained. |
| InputTrackInfo | Array of [TrackInfo](#TrackInfo) | No | Audio track information.  Note: This field may return null, indicating that no valid value can be obtained. |

## AwsS3FileUploadTrigger

An AWS S3 file upload trigger.

Used by actions: CreateSchedule, CreateWorkflow, ModifySchedule, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| S3Bucket | String | Yes | The AWS S3 bucket bound to the scheme. |
| S3Region | String | Yes | The region of the AWS S3 bucket. |
| Dir | String | No | The bucket directory bound. It must be an absolute path that starts and ends with `/`, such as `/movie/201907/`. If you do not specify this, the root directory will be bound. |
| Formats | Array of String | No | The file formats that will trigger the scheme, such as ["mp4", "flv", "mov"]. If you do not specify this, the upload of files in any format will trigger the scheme. |
| S3SecretId | String | No | The key ID of the AWS S3 bucket. Note: This field may return null, indicating that no valid values can be obtained. |
| S3SecretKey | String | No | The key of the AWS S3 bucket. Note: This field may return null, indicating that no valid values can be obtained. |
| AwsSQS | [AwsSQS](#AwsSQS) | No | The SQS queue of the AWS S3 bucket. Note: The queue must be in the same region as the bucket. Note: This field may return null, indicating that no valid values can be obtained. |

## AwsSQS

The information of an AWS SQS queue.

Used by actions: BatchProcessMedia, CreateSchedule, CreateWorkflow, DescribeBatchTaskDetail, DescribeTaskDetail, EditMedia, ExtractBlindWatermark, ModifySchedule, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SQSRegion | String | Yes | The region of the SQS queue. Note: This field may return null, indicating that no valid values can be obtained. |
| SQSQueueName | String | Yes | The name of the SQS queue. Note: This field may return null, indicating that no valid values can be obtained. |
| S3SecretId | String | No | The key ID required to read from/write to the SQS queue. Note: This field may return null, indicating that no valid values can be obtained. |
| S3SecretKey | String | No | The key required to read from/write to the SQS queue. Note: This field may return null, indicating that no valid values can be obtained. |

## BatchSmartSubtitlesResult

Smart subtitle task result.

Used by actions: DescribeBatchTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Input | [SmartSubtitleTaskResultInput](#SmartSubtitleTaskResultInput) | Input information for smart subtitle tasks. Note: This field may return null, indicating that no valid value can be obtained. |
| Outputs | Array of [SmartSubtitleTaskBatchOutput](#SmartSubtitleTaskBatchOutput) | Output information for smart subtitle tasks. Note: This field may return null, indicating that no valid value can be obtained. |

## BatchSubTaskResult

Results of subtasks for a batch task.

Used by actions: DescribeBatchTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| InputInfos | Array of [MediaInputInfo](#MediaInputInfo) | Input information for a batch task. Note: This field may return null, indicating that no valid value can be obtained. |
| Metadatas | Array of [MediaMetaData](#MediaMetaData) | Metadata of the original video. Note: This field may return null, indicating that no valid value can be obtained. |
| SmartSubtitlesTaskResult | [BatchSmartSubtitlesResult](#BatchSmartSubtitlesResult) | Execution result of the smart subtitle task. Note: This field may return null, indicating that no valid value can be obtained. |

## BlindWatermarkInput

Digital watermark parameter type in the MPS task.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | Digital watermark template ID. |

## BlindWatermarkTemplate

Digital watermark template details.

Used by actions: DescribeBlindWatermarkTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique identifier of the digital watermark template. |
| Type | String | Digital watermark type. Valid values: blind-basic: basic copyright digital watermark; blind-nagra: NAGRA forensics watermark. |
| Name | String | Digital watermark template name. |
| TextContent | String | Text content of the digital watermark template. The length cannot exceed 64 characters. |
| Comment | String | Description information of the digital watermark template. |
| CreateTime | String | Creation time of the digital watermark template in [ISO date and time format](https://www.tencentcloud.comom/document/product/862/37710?from_cn_redirect=1#52). |
| UpdateTime | String | Last modification time of the digital watermark template in [ISO date and time format](https://www.tencentcloud.comom/document/product/862/37710?from_cn_redirect=1#52). |
| Strength | String | Digital watermark strength.  default: default, balance between hd video quality and resilience.  stronger: clear image quality, strong resilience.  strongest: normal video quality, strongest resilience. |

## ClassificationConfigureInfo

Control parameter of intelligent categorization task

Used by actions: CreateAIAnalysisTemplate, DescribeAIAnalysisTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of intelligent categorization task. Valid values: ON: enables intelligent categorization task;OFF: disables intelligent categorization task. |

## ClassificationConfigureInfoForUpdate

Control parameter of intelligent categorization task

Used by actions: ModifyAIAnalysisTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of intelligent categorization task. Valid values: ON: enables intelligent categorization task;OFF: disables intelligent categorization task. |

## ColorEnhanceConfig

Color enhancement configuration.

Used by actions: CreateProcessImageTemplate, CreateTranscodeTemplate, ModifyProcessImageTemplate, ModifyTranscodeTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Type | String | No | The strength. Valid values: weaknormalstrong Default value: weak. Note: This field may return null, indicating that no valid values can be obtained. |

## ComposeAudioItem

The audio element information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SourceMedia | [ComposeSourceMedia](#ComposeSourceMedia) | Yes | The media information of the element. |
| TrackTime | [ComposeTrackTime](#ComposeTrackTime) | No | The time of the element in the timeline. If this is not specified, the element will follow the previous element. |
| AudioOperations | Array of [ComposeAudioOperation](#ComposeAudioOperation) | No | The operations performed, such as muting. |

## ComposeAudioOperation

The audio operations of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | The operation type. Valid values: `Volume`: Volume adjustment. |
| Volume | Float | No | The volume level. This parameter is valid if `Type` is `Volume`. Value range: 0–5.  If the parameter value is `0`, the video will be muted. If the parameter value is smaller than 1, the volume will be reduced. If the parameter value is `1`, the original volume will be kept. If the parameter value is greater than 1, the volume will be increased. |

## ComposeAudioStream

The audio stream information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Codec | String | No | The codec of the audio stream. Valid values: `AAC`: AAC (default), which is used for the MP4 container. `MP3`: MP3 codec, which is used for the MP3 container. |
| SampleRate | Integer | No | The sample rate (Hz) of the audio stream. 16000 (default)320004410048000 |
| AudioChannel | Integer | No | The number of sound channels. Valid values: u200c`1`: Mono. `2`: Dual (default). |
| Bitrate | Integer | No | Reference bitrate, in kbps. Value range: 26-10000. If set, the encoder will try to encode at this bitrate. If not set, the service will automatically adopt a suitable bitrate based on audio parameters. |

## ComposeCanvas

The canvas information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Color | String | No | The RGB value of the background color. The format is #RRGGBB, such as `#F0F0F0`.  Default value: `#000000` (black). |
| Width | Integer | No | The canvas width (px), which is the width of the output video. Value range: 0–3840.   The default value is `0`, which means that the canvas is as wide as the first video. |
| Height | Integer | No | The canvas height (px), which is the height of the output video. Value range: 0–3840.   The default value is `0`, which means that the canvas is as high as the first video. |

## ComposeEmptyItem

The placeholder element information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Duration | String | Yes | The element duration. The value of this parameter ends with `s`, which means seconds. For example, `3.5s` indicates 3.5 seconds. |

## ComposeImageItem

The image element information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SourceMedia | [ComposeSourceMedia](#ComposeSourceMedia) | Yes | The media information of the element. |
| TrackTime | [ComposeTrackTime](#ComposeTrackTime) | No | The time of the element in the timeline. If this is not specified, the element will follow the previous element. |
| XPos | String | No | The horizontal distance of the element's center from the canvas origin. Two formats are supported: If the value ends with %, it specifies the distance as a percentage of the canvas width. For example, `10%` means that the distance is 10% of the canvas width.  u200cIf the value ends with px, it specifies the distance in pixels. For example, `100px` means that the distance is 100 pixels.  Default value: `50%`. |
| YPos | String | No | The vertical distance of the element's center from the canvas origin. Two formats are supported: u200cIf the value ends with %, it specifies the distance as a percentage of the canvas height. For example, `10%` means that the distance is 10% of the canvas height.  u200cIf the value ends with px, it specifies the distance in pixels. For example, `100px` means that the distance is 100 pixels.  Default value: `50%`. |
| Width | String | No | The width of the video segment. Two formats are supported: u200cIf the value ends with %, it specifies the width as a percentage of the canvas width. For example, `10%` means that the video width is 10% of the canvas width.  u200cIf the value ends with px, it specifies the width in pixels. For example, `100px` means that the video width is 100 pixels.  If one or both parameters are empty or set to `0`: If both `Width` and `Height` are empty, the original width and height of the element will be kept. If `Width` is empty and `Height` is not, the width will be auto scaled. If `Width` is not empty and `Height` is, the height will be auto scaled. |
| Height | String | No | The height of the element. Two formats are supported: u200cIf the value ends with %, it specifies the height as a percentage of the canvas height. For example, `10%` means that the height is 10% of the canvas height.  u200cIf the value ends with px, it specifies the height in pixels. For example, `100px` means that the height is 100 pixels.  If one or both parameters are empty or set to `0`: If both `Width` and `Height` are empty, the original width and height of the video will be kept. If `Width` is empty and `Height` is not, the width will be auto scaled. If `Width` is not empty and `Height` is, the height will be auto scaled. |
| ImageOperations | Array of [ComposeImageOperation](#ComposeImageOperation) | No | The image operations, such as image rotation. |

## ComposeImageOperation

The image operations of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | The type. Valid values: u200c`Rotate`: Image rotation. `Flip`: Image flipping. |
| RotateAngle | Float | No | This is valid if `Type` is `Rotate`. The angle of rotation around the image center. Value range: 0–360. |
| FlipType | String | No | This is valid if `Type` is `Flip`. How to flip the image. Valid values:xa0 u200c`Horizental`: Flip horizontally. `Vertical`: Flip vertically. |

## ComposeMediaConfig

The information of a video editing/compositing task.

The figure below outlines the relationships among tracks, elements, and the timeline.

![image](https://ie-mps-1258344699.cos.ap-nanjing.tencentcos.cn/common/cloud/EditMedia-Compose-Track-Item-en.png)

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| TargetInfo | [ComposeTargetInfo](#ComposeTargetInfo) | No | The information of the output video. |
| Canvas | [ComposeCanvas](#ComposeCanvas) | No | The canvas information of the output video. |
| Styles | Array of [ComposeStyles](#ComposeStyles) | No | The global styles. This parameter is used together with `Tracks` to specify styles, such as the subtitle style. |
| Tracks | Array of [ComposeMediaTrack](#ComposeMediaTrack) | No | The information of media tracks (consisting of video, audio, image, and text elements) used to composite the video. About tracks and the timeline: The timeline of a track is the same as the timeline of the output video. The elements of different tracks are overlaid at the same time point in the timeline.Video, image, and text elements are overlaid according to their track number, with the first track on top. Audio elements are mixed. Note: The different elements of the same track cannot be overlaid (except subtitles). |

## ComposeMediaItem

The element information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | The element type. Valid values: `Video` `Audio` `Image` `Transition` `Subtitle` `Empty` |
| Video | [ComposeVideoItem](#ComposeVideoItem) | No | The information of the video element, which is valid if `Type` is `Video`. |
| Audio | [ComposeAudioItem](#ComposeAudioItem) | No | The information of the audio element, which is valid if `Type` is `Audio`. |
| Image | [ComposeImageItem](#ComposeImageItem) | No | The information of the image element, which is valid if `Type` is `Image`. |
| Transition | [ComposeTransitionItem](#ComposeTransitionItem) | No | The information of the transition element, which is valid if `Type` is `Transition`. |
| Subtitle | [ComposeSubtitleItem](#ComposeSubtitleItem) | No | The information of the subtitle element, which is valid if `Type` is `Subtitle`. |
| Empty | [ComposeEmptyItem](#ComposeEmptyItem) | No | The information of the empty element, which is valid if `Type` is `Empty`. An empty element is used as a placeholder in the timeline. |

## ComposeMediaTrack

The track information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | Track type. Valid values: Video: video track. It can consist of the following elements:Video elementsImage elementsTransition elementsEmpty elementsAudio: audio track. It can consist of the following elements:Audio elementsTransition elementsEmpty elementsTitle: text track. It can consist of the following elements:Subtitle elements |
| Items | Array of [ComposeMediaItem](#ComposeMediaItem) | Yes | The elements of a track. |

## ComposeSourceMedia

The material source of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| FileId | String | Yes | The material ID, which can be found in `FileInfos`. |
| StartTime | String | No | The start time of the material. The following two formats are supported. If the value of this parameter ends with `s`, it specifies the time in seconds. For example, `3.5s` indicates the time when 3.5 seconds of the material elapses. u200cIf the value of this parameter ends with `%`, it specifies the time as a percentage of the material's duration. For example, `10%` indicates the time when 10% of the material's duration elapses.  Default value: `0s`. |
| EndTime | String | No | The end time of the material. This parameter and `StartTime` determine which time segment of the material is used. The following two formats are supported: If the value of this parameter ends with `s`, it specifies the time in seconds. For example, `3.5s` indicates the time when 3.5 seconds of the material elapses. u200cIf the value of this parameter ends with `%`, it specifies the time as a percentage of the material's duration. For example, `10%` indicates the time when 10% of the material's duration elapses.  If the track duration is set, the default value is `StartTime` plus the track duration. If not, the default value is `StartTime` plus 1 second. Note: `EndTime` must be at least 0.02 seconds later than `StartTime`. |

## ComposeStyles

The style information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Id | String | Yes | The style ID, which identifies an element style. Note: The style ID can be up to 32 characters long and can contain letters, digits, and special characters -_ |
| Type | String | Yes | The type. Valid values: `Subtitle`: The subtitle style. |
| Subtitle | [ComposeSubtitleStyle](#ComposeSubtitleStyle) | No | The subtitle style details. This parameter is valid if `Type` is `Subtitle`. |

## ComposeSubtitleItem

The subtitle element information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| StyleId | String | Yes | The subtitle style ID, which corresponds to the `Id` field of `ComposeStyles`. |
| Text | String | Yes | Subtitle text. note: long text may exceed the frame. recommend using \n for line breaks. |
| TrackTime | [ComposeTrackTime](#ComposeTrackTime) | No | The time of the element in the timeline. If this is not specified, the element will follow the previous element. |

## ComposeSubtitleStyle

The subtitle style of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Height | String | No | The subtitle height. Two formats are supported: u200cIf the value ends with %, it specifies the height as a percentage of the canvas height. For example, `10%` means that the height is 10% of the canvas height.  u200cIf the value ends with px, it specifies the height in pixels. For example, `100px` means that the height is 100 pixels.  The default value is the value of `FontSize`. |
| MarginBottom | String | No | The bottom margin. Two formats are supported: u200cIf the value ends with %, it specifies the margin as a percentage of the canvas height. For example, `10%` means that the margin is 10% of the canvas height.  u200cIf the value ends with px, it specifies the margin in pixels. For example, `100px` means that the margin is 100 pixels.  Default value: `0px`. |
| FontType | String | No | The font type. Valid values: `SimHei`(default): Chinese font Heiti.  `SimSun`: Chinese font Songti. |
| FontSize | String | No | The font size. Two formats are supported: u200cIf the value ends with %, it specifies the size as a percentage of the canvas height. For example, `10%` means that the size is 10% of the canvas height.  u200cIf the value ends with px, it specifies the size in pixels. For example, `100px` means that the size is 100 pixels.  Default value: `2%`. |
| FontBold | Integer | No | Whether to bold the text (some fonts may not support bold). Valid values: `0` (default): No. `1`: Yes. |
| FontItalic | Integer | No | Whether to italicize the text (some fonts may not support italics). Valid values: `0` (default): No. `1`: Yes. |
| FontColor | String | No | The font color (#RRGGBBAA).   Default value: `0x000000FF` (black).   Note: `AA` in the color notation defines the opacity of the color. It's optional. |
| FontAlign | String | No | The text alignment. Valid values: `Center`(default) `Left` `Right` |
| FontAlignMargin | String | No | The margin for left/right align. If `FontAlign` is `Left`, this parameter specifies the left margin of the subtitles. If `FontAlign` is `Right`, this parameter specifies the right margin of the subtitles.  Two formats are supported: u200cIf the value ends with %, it specifies the margin as a percentage of the canvas width. For example, `10%` means that the margin is 10% of the canvas width.  u200cIf the value ends with px, it specifies the margin in pixels. For example, `100px` means that the margin is 100 pixels. |
| BorderWidth | String | No | The subtitle border width. Two formats are supported: u200cIf the value ends with %, it specifies the width as a percentage of the canvas height. For example, `10%` means that the width is 10% of the canvas height.  u200cIf the value ends with px, it specifies the width in pixels. For example, `100px` means that the width is 100 pixels.  The default value is `0`, which means the subtitles will have no borders. |
| BorderColor | String | No | The border color, whose format is the same as that for `FontColor`. This parameter is valid if `BorderWidth` is not `0`. |
| BottomColor | String | No | The text background color, whose format is the same as that for `FontColor`.   The default value is an empty string, which means the subtitles will not have a background color. |

## ComposeTargetInfo

The output video information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Container | String | No | The container. Valid values: `mp4` (default), for video files. `mp3`, for audio files. |
| RemoveVideo | Integer | No | Whether to remove video data. Valid values: `0` (default): No. `1`: Yes. |
| RemoveAudio | Integer | No | Whether to remove audio data. Valid values: `0` (default): No. `1`: Yes. |
| VideoStream | [ComposeVideoStream](#ComposeVideoStream) | No | The information of the output video stream. |
| AudioStream | [ComposeAudioStream](#ComposeAudioStream) | No | The information of the output audio stream. |

## ComposeTrackTime

The time information of an element on the output video track of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Start | String | No | The time when the element starts on the track. The value of this parameter ends with `s`, which means seconds. For example, `3.5s` indicates the time when 3.5 seconds of the video elapses. Note: If this parameter is not specified, the start time will be the end time of the previous element. Therefore, you can also use the placeholder parameter `ComposeEmptyItem` to configure the start time. |
| Duration | String | No | The element duration. The value of this parameter ends with `s`, which means seconds. For example, `3.5s` means 3.5 seconds. The default value is the material duration, which is determined by `EndTime` and `StartTime` of `ComposeSourceMedia`. If `ComposeSourceMedia` is not specified, the duration will be 1 second. |

## ComposeTransitionItem

The transition element information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Duration | String | No | The element duration. The value of this parameter ends with `s`, which means seconds. For example, `3s` indicates 3 seconds.  Default value: `1s`. Note The number before `s` must be an integer. Non-integers will be rounded down to the nearest integer. The transition element must be between two non-empty elements. The duration of the transition element must be shorter than that of the preceding element and the following element.  u200cThe start time of the following element on the track will be automatically changed to the end time of the preceding element minus the duration of the transition element. |
| Transitions | Array of [ComposeTransitionOperation](#ComposeTransitionOperation) | No | The transition effects. The default transition effect is fade. Note: You can add at most one image transition and one audio transition. |

## ComposeTransitionOperation

The transition information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | The transition type.  The image transition, which connects two video segments. `ImageFadeInFadeOut`  u200c`BowTieHorizontal`  u200c`BowTieVertical`  u200c`ButterflyWaveScrawler` `Cannabisleaf` `Circle` `CircleCrop`  u200c`Circleopen` `Crosswarp` `Cube` `DoomScreenTransition` `Doorway` `Dreamy` `DreamyZoom` `FilmBurn` `GlitchMemories` `Heart` `InvertedPageCurl` `Luma` `Mosaic` `Pinwheel` `PolarFunction` `PolkaDotsCurtain` `Radial` `RotateScaleFade` `Squeeze` `Swap` `Swirl` `UndulatingBurnOutSwirl` `Windowblinds` `WipeDown` `WipeLeft` `WipeRight` `WipeUp` `ZoomInCircles`   The audio transition, which connects two audio segments. `AudioFadeInFadeOut` |

## ComposeVideoItem

The video element information of a video editing/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SourceMedia | [ComposeSourceMedia](#ComposeSourceMedia) | Yes | The media information of the element. |
| TrackTime | [ComposeTrackTime](#ComposeTrackTime) | No | The time of the element in the timeline. If this is not specified, the element will follow the previous element. |
| XPos | String | No | The horizontal distance of the element's center from the canvas origin. Two formats are supported: If the value ends with %, it specifies the distance as a percentage of the canvas width. For example, `10%` means that the distance is 10% of the canvas width.  u200cIf the value ends with px, it specifies the distance in pixels. For example, `100px` means that the distance is 100 pixels.  Default value: `50%`. |
| YPos | String | No | The vertical distance of the element's center from the canvas origin. Two formats are supported: u200cIf the value ends with %, it specifies the distance as a percentage of the canvas height. For example, `10%` means that the distance is 10% of the canvas height.  u200cIf the value ends with px, it specifies the distance in pixels. For example, `100px` means that the distance is 100 pixels.  Default value: `50%`. |
| Width | String | No | The width of the video segment. Two formats are supported: u200cIf the value ends with %, it specifies the width as a percentage of the canvas width. For example, `10%` means that the video width is 10% of the canvas width.  u200cIf the value ends with px, it specifies the width in pixels. For example, `100px` means that the video width is 100 pixels.  If one or both parameters are empty or set to `0`: If both `Width` and `Height` are empty, the original width and height of the element will be kept. If `Width` is empty and `Height` is not, the width will be auto scaled. If `Width` is not empty and `Height` is, the height will be auto scaled. |
| Height | String | No | The height of the element. Two formats are supported: u200cIf the value ends with %, it specifies the height as a percentage of the canvas height. For example, `10%` means that the height is 10% of the canvas height.  u200cIf the value ends with px, it specifies the height in pixels. For example, `100px` means that the height is 100 pixels.  If one or both parameters are empty or set to `0`: If both `Width` and `Height` are empty, the original width and height of the element will be kept. If `Width` is empty and `Height` is not, the width will be auto scaled. If `Width` is not empty and `Height` is, the height will be auto scaled. |
| ImageOperations | Array of [ComposeImageOperation](#ComposeImageOperation) | No | The image operations, such as image rotation. |
| AudioOperations | Array of [ComposeAudioOperation](#ComposeAudioOperation) | No | The audio operations, such as muting. |

## ComposeVideoStream

The video stream information of a video edit/compositing task.

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Codec | String | No | The codec. Valid values: `H.264` (default) |
| Fps | Integer | No | The video frame rate (Hz). Value range: 0–60.   The default value is `0`, which means that the frame rate will be the same as that of the first video. |
| Bitrate | Integer | No | Reference bitrate, in kbps. Value range: 50-35000. If set, the encoder will try to encode at this bitrate. If not set, the service will automatically adopt a suitable bitrate based on the complexity of an image. |

## ContainerDiagnoseResultItem

Container format diagnostic result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Category | String | Diagnosed exception category. Valid values: DecodeParamException: decoding parameter exception. TimeStampException: timestamp exception. FrameException: frame rate exception. StreamStatusException: stream status exception. StreamInfo: stream information exception. StreamAbnormalCharacteristics: stream characteristics exception. DecodeException: decoding exception. HLSRequirements: HLS format exception. Note: This field may return null, indicating that no valid values can be obtained. |
| Type | String | Diagnosed specific exception type. Valid values:  VideoResolutionChanged: video resolution change. AudioSampleRateChanged: audio sample rate change. AudioChannelsChanged: audio channel quantity change. ParameterSetsChanged: stream parameter set information change. DarOrSarInvalid: video aspect ratio exception. TimestampFallback: DTS timestamp rollback. DtsJitter: DTS jitter too high. PtsJitter: PTS jitter too high. AACDurationDeviation: improper AAC frame timestamp interval. AudioDroppingFrames: audio frame dropping. VideoDroppingFrames: video frame dropping. AVTimestampInterleave: improper audio-video interleaving. PtsLessThanDts: PTS less than DTS for media streams. ReceiveFpsJitter: significant jitter in the network receive frame rate. ReceiveFpsTooSmall: network receive video frame rate too low. FpsJitter: significant jitter in the stream frame rate calculated via PTS. StreamOpenFailed: stream open failure. StreamEnd: stream end. StreamParseFailed: stream parsing failure. VideoFirstFrameNotIdr: first frame not an IDR frame. StreamNALUError: NALU start code error. TsStreamNoAud: no AUD NALU in the H26x stream of MPEG-TS. AudioStreamLack: no audio stream. VideoStreamLack: no video stream. LackAudioRecover: missing audio stream recovery. LackVideoRecover: missing video stream recovery. VideoBitrateOutofRange: video stream bitrate (kbps) out of range. AudioBitrateOutofRange: audio stream bitrate (kbps) out of range. VideoDecodeFailed: video decoding error. AudioDecodeFailed: audio decoding error. AudioOutOfPhase: opposite phase in dual-channel audio. VideoDuplicatedFrame: duplicate frames in video streams. AudioDuplicatedFrame: duplicate frames in audio streams. VideoRotation: video rotation. TsMultiPrograms: multiple programs in MPEG2-TS streams Mp4InvalidCodecFourcc: codec FourCC in MP4 not meeting Apple HLS requirements. HLSBadM3u8Format: invalid M3U8 file. HLSInvalidMasterM3u8: invalid main M3U8 file. HLSInvalidMediaM3u8: invalid media M3U8 file. HLSMasterM3u8Recommended: parameters recommended by standards missing in main M3U8. HLSMediaM3u8Recommended: parameters recommended by standards missing in media M3U8. HLSMediaM3u8DiscontinuityExist: EXT-X-DISCONTINUITY in media M3U8. HLSMediaSegmentsStreamNumChange: changed number of streams in segments. HLSMediaSegmentsPTSJitterDeviation: PTS jumps between segments without EXT-X-DISCONTINUITY. HLSMediaSegmentsDTSJitterDeviation: DTS jumps between segments without EXT-X-DISCONTINUITY. TimecodeTrackExist: TMCD track in MP4. Note: This field may return null, indicating that no valid values can be obtained. |
| SeverityLevel | String | Diagnosed exception level. Valid values: Fatal: affecting subsequent playback and parsing. Error: may affect playback. Warning: potential risk, which may not necessarily affect playback. Notice: important stream information. Info: general stream information. Note: This field may return null, indicating that no valid values can be obtained. |
| DateTimeSet | Array of String | Timestamp of warning, in the format of 2022-12-25T13:14:16Z. Note: This field may return null, indicating that no valid values can be obtained. |
| TimestampSet | Array of Float | Timestamp.  Note: This field may return null, indicating that no valid values can be obtained. |

## ContentReviewTemplateItem

Details of a content audit template

Used by actions: DescribeContentReviewTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of a content audit template. |
| Name | String | Name of a content audit template. Length limit: 64 characters. |
| Comment | String | Description of a content audit template. Length limit: 256 characters. |
| PornConfigure | [PornConfigureInfo](#PornConfigureInfo) | Porn information detection control parameter. Note: This field may return null, indicating that no valid values can be obtained. |
| TerrorismConfigure | [TerrorismConfigureInfo](#TerrorismConfigureInfo) | The parameters for detecting sensitive information. Note: This field may return `null`, indicating that no valid values can be obtained. |
| PoliticalConfigure | [PoliticalConfigureInfo](#PoliticalConfigureInfo) | The parameters for detecting sensitive information. Note: This field may return `null`, indicating that no valid values can be obtained. |
| ProhibitedConfigure | [ProhibitedConfigureInfo](#ProhibitedConfigureInfo) | Control parameter of prohibited information detection. Prohibited information includes: Abusive;Drug-related. Note: this field may return null, indicating that no valid values can be obtained. |
| UserDefineConfigure | [UserDefineConfigureInfo](#UserDefineConfigureInfo) | Custom content audit control parameter. Note: This field may return null, indicating that no valid values can be obtained. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| Type | String | The template type. Valid values: * Preset * Custom Note: This field may return `null`, indicating that no valid values can be obtained. |

## CosFileUploadTrigger

Input rule bound to COS.

Used by actions: CreateSchedule, CreateWorkflow, ModifySchedule, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Bucket | String | Yes | Name of the COS bucket bound to a workflow, such as `TopRankVideo-125xxx88`. |
| Region | String | Yes | Region of the COS bucket bound to a workflow, such as `ap-chongiqng`. |
| Dir | String | No | Input path directory bound to a workflow, such as `/movie/201907/`. If this parameter is left empty, the `/` root directory will be used. |
| Formats | Array of String | No | All supported formats are as follows: - Video file extension. The following 15 options are supported: `.mp4`, `.avi`, `.mov`, `.wmv`, `.flv`, `.mkv`, `.mpg`, `.mpeg`, `.rm`, `.rmvb`, `.asf`, `.3gp`, `.webm`, `.ts`, and `.m4v`. - Audio file extension. The following 7 options are supported: `.mp3`, `.wav`, `.aac`, `.flac`, `.ogg`, `.m4a`, and `.amr`. - Subtitle file extension. The following 2 options are supported: `.vtt` and `.srt`. - `*`: any file format is supported. - Unspecified or input an empty list: the system supports the following preset file formats: video (`.mp4`, `.ts`, `.flv`, `.wmv`, `.asf`, `.rm`, `.rmvb`, `.mpg`, `.mpeg`, `.3gp`, `.mov`, `.webm`, `.mkv`, `.avi`, and `.m4v`); audio (`.mp3`, `.m4a`, `.flac`, `.ogg`, `.wav`, `.amr`, and `.aac`); subtitle (`.vtt` and `.srt`). **Note**: 1. If the input format list includes `*`, it indicates that any file format is supported. 2. File extensions can be provided with or without `.`, such as `.mp4` or `mp4`, both are supported. 3. Custom file extensions should consist of digits, letters, and characters, and have a length between 1 and 64 characters. |

## CosInputInfo

The information of the COS object to process.

Used by actions: BatchProcessMedia, DescribeMediaMetaData, ExtractBlindWatermark, ProcessImage, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Bucket | String | Yes | The COS bucket of the object to process, such as `TopRankVideo-125xxx88`. |
| Region | String | Yes | The region of the COS bucket, such as `ap-chongqing`. |
| Object | String | Yes | The path of the object to process, such as `/movie/201907/WildAnimal.mov`. |

## CosOutputStorage

The information of the output COS object after media processing.

Used by actions: BatchProcessMedia, CreateSchedule, CreateWorkflow, EditMedia, ModifySchedule, ProcessImage, ProcessLiveStream, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Bucket | String | No | The bucket to which the output file of media processing is saved, such as `TopRankVideo-125xxx88`. If this parameter is left empty, the value of the upper layer will be inherited. |
| Region | String | No | The region of the output bucket, such as `ap-chongqing`. If this parameter is left empty, the value of the upper layer will be inherited. |

## CoverConfigureInfo

Control parameter of intelligent cover generating task

Used by actions: CreateAIAnalysisTemplate, DescribeAIAnalysisTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of intelligent cover generating task. Valid values: ON: enables intelligent cover generating task;OFF: disables intelligent cover generating task. |

## CoverConfigureInfoForUpdate

Control parameter of intelligent cover generating task

Used by actions: ModifyAIAnalysisTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of intelligent cover generating task. Valid values: ON: enables intelligent cover generating task;OFF: disables intelligent cover generating task. |

## DiagnoseResult

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Category | String | Diagnosed exception category. Valid values: DecodeParamException: decoding parameter exception. TimeStampException: timestamp exception. FrameException: frame rate exception. StreamStatusException: stream status exception. StreamInfo: stream information exception. StreamAbnormalCharacteristics: stream characteristics exception. DecodeException: decoding exception. HLSRequirements: HLS format exception. Note: This field may return null, indicating that no valid values can be obtained. |
| Type | String | Diagnosed specific exception type. Valid values:  VideoResolutionChanged: video resolution change. AudioSampleRateChanged: audio sample rate change. AudioChannelsChanged: audio channel quantity change.ParameterSetsChanged: stream parameter set information change. DarOrSarInvalid: video aspect ratio exception. TimestampFallback: DTS timestamp rollback.DtsJitter: DTS jitter too high. PtsJitter: PTS jitter too high. AACDurationDeviation: improper AAC frame timestamp interval. AudioDroppingFrames: audio frame dropping. VideoDroppingFrames: video frame dropping. AVTimestampInterleave: improper audio-video interleaving. PtsLessThanDts: PTS less than DTS for media streams. ReceiveFpsJitter: significant jitter in the network receive frame rate.ReceiveFpsTooSmall: network receive video frame rate too low.FpsJitter: significant jitter in the stream frame rate calculated via PTS.StreamOpenFailed: stream open failure. StreamEnd: stream end. StreamParseFailed: stream parsing failure. VideoFirstFrameNotIdr: first frame not an IDR frame. StreamNALUError: NALU start code error. TsStreamNoAud: no AUD NALU in the H26x stream of MPEG-TS.AudioStreamLack: no audio stream. VideoStreamLack: no video stream. LackAudioRecover: missing audio stream recovery. LackVideoRecover: missing video stream recovery. VideoBitrateOutofRange: video stream bitrate (kbps) out of range. AudioBitrateOutofRange: audio stream bitrate (kbps) out of range. VideoDecodeFailed: video decoding error. AudioDecodeFailed: audio decoding error. AudioOutOfPhase: opposite phase in dual-channel audio. VideoDuplicatedFrame: duplicate frames in video streams. AudioDuplicatedFrame: duplicate frames in audio streams. VideoRotation: video rotation. TsMultiPrograms: multiple programs in MPEG2-TS streams.Mp4InvalidCodecFourcc: codec FourCC in MP4 not meeting Apple HLS requirements. HLSBadM3u8Format: invalid M3U8 file. HLSInvalidMasterM3u8: invalid main M3U8 file. HLSInvalidMediaM3u8: invalid media M3U8 file. HLSMasterM3u8Recommended: parameters recommended by standards missing in main M3U8. HLSMediaM3u8Recommended: parameters recommended by standards missing in media M3U8. HLSMediaM3u8DiscontinuityExist: EXT-X-DISCONTINUITY in media M3U8. HLSMediaSegmentsStreamNumChange: changed number of streams in segments. HLSMediaSegmentsPTSJitterDeviation: PTS jumps between segments without EXT-X-DISCONTINUITY. HLSMediaSegmentsDTSJitterDeviation: DTS jumps between segments without EXT-X-DISCONTINUITY. TimecodeTrackExist: TMCD track in MP4. Note: This field may return null, indicating that no valid values can be obtained. |
| Timestamp | Float |  |
| Description | String |  |
| DateTime | String |  |
| SeverityLevel | String | Diagnosed exception level. Valid values: Fatal: affecting subsequent playback and parsing. Error: may affect playback. Warning: potential risk, which may not necessarily affect playback. Notice: important stream information. Info: general stream information. Note: This field may return null, indicating that no valid values can be obtained. |

## DiffusionEnhanceConfig

LLM enhancement.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Capability configuration switch. Valid values: ON: enabled. OFF: disabled. Default value: OFF. |
| Type | String | No | Strength type. Valid values: weak normal strong Default value: normal. Note: This field may return null, indicating that no valid values can be obtained. |

## DrmInfo

The DRM encryption details.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | Encryption type.  - simpleaes Can only be used for HLS. format support: ts and mp4. Only can be used in slice mode. cannot be used in singlefile mode.  - fairplay: Can only be used for HLS. the segment format can only be mp4. Supports slice mode or singlefile mode.  - widevine: Can be used for HLS and DASH. the slice format can only be mp4. Output HLS: specifies the slicing or singlefile mode can be used. OutputOutput DASH]: can only be in singlefile mode.  - playready: Can be used for HLS and DASH. the slice format can only be mp4. Output HLS: specifies the slicing or singlefile mode can be used. Output DASH: can only be in singlefile mode.  - widevine+fairplay,playready+fairplay,widevine+playready+fairplay: Can only be used for HLS. valid values: mp4. Supports slice mode or single file mode.  - widevine+playready: Applicable to HLS and MPEG-DASH. the format can only be mp4. HLS format can use slice mode or single file mode. Specifies that only singlefile mode can be used for MPEG-DASH. |
| SimpleAesDrm | [SimpleAesDrm](#SimpleAesDrm) | No | The AES-128 encryption details. Note: This field may return null, indicating that no valid values can be obtained. |
| SpekeDrm | [SpekeDrm](#SpekeDrm) | No | Information about FairPlay, WideVine, and PlayReady encryption. |

## EditMediaFileInfo

VOD video file editing information

Used by actions: DescribeTaskDetail, EditMedia, ParseNotification.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| InputInfo | [MediaInputInfo](#MediaInputInfo) | Yes | Video input information. |
| StartTimeOffset | Float | No | The start offset (seconds) for video clipping. This parameter is valid for video clipping tasks. |
| EndTimeOffset | Float | No | The end offset (seconds) for video clipping. This parameter is valid for video clipping tasks. |
| Id | String | No | The ID of the material associated with an element. This parameter is required for video compositing tasks.  Note: The ID can be up to 32 characters long and can contain letters, digits, and special characters -_ Note: This field may return null, indicating that no valid values can be obtained. |

## EditMediaOutputConfig

Configuration for output files of video editing

Used by actions: EditMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Container | String | No | The container. Valid values: `mp4` (default), `hls`, `mov`, `flv`, `avi`. Note: This field may return null, indicating that no valid values can be obtained. |
| Type | String | No | Editing mode. Optional values: normal (default): Precise editing fast: Fast editing, with faster processing speed but lower precision to some extent Note: fast only supports individual files, and the default output transcoding format of normal is h264. Note: This field may return null, indicating that no valid value can be obtained. |

## EditMediaTask

Video editing task information

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Task ID. |
| Status | String | Task status. Valid values: PROCESSING: processing;FINISH: completed. |
| ErrCode | Integer | Error code 0: success;Other values: failure. |
| Message | String | Error message. |
| Input | [EditMediaTaskInput](#EditMediaTaskInput) | Input of video editing task. |
| Output | [EditMediaTaskOutput](#EditMediaTaskOutput) | Output of video editing task. |

## EditMediaTaskInput

Input of video editing task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| FileInfoSet | Array of [EditMediaFileInfo](#EditMediaFileInfo) | Information of input video file. |

## EditMediaTaskOutput

Output of video editing task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Target storage of edited file. |
| Path | String | Path of edited video file. |

## EnhanceConfig

Audio/Video enhancement configuration.

Used by actions: CreateTranscodeTemplate, CreateWorkflow, DescribeTranscodeTemplates, ModifyTranscodeTemplate, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| VideoEnhance | [VideoEnhanceConfig](#VideoEnhanceConfig) | No | Video enhancement configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| AudioEnhance | [AudioEnhanceConfig](#AudioEnhanceConfig) | No | The audio enhancement configuration. Note: This field may return null, indicating that no valid values can be obtained. |

## EraseArea

Smart erasure. coordinate configuration of the removal area.
The region is defined by the coordinates of the upper left corner and the bottom-right corner.
The coordinate origin is the top-left corner of the frame and the coordinate points can be specified using pixel values or percentage units.
**For the Automatic Erasing Area:**
When the unit is %, the coordinate range is [0,1].
When unit is px, X value range is [0, video image width]. Y value range is [0, video image height].
**For the Specified area erasing:**
Specifies the coordinate range as [0,1) when the unit is %.
When unit: px, X value range [0, video image width], Y value range [0, video image height].

Used by actions: CreateSmartEraseTemplate, CreateSmartSubtitleTemplate, ModifySmartEraseTemplate, ModifySmartSubtitleTemplate, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| LeftTopX | Float | Yes | X-Axis coordinate of the upper left corner. |
| LeftTopY | Float | Yes | Y-Axis coordinate of the upper left corner. |
| RightBottomX | Float | Yes | X-Axis coordinate of the bottom-right corner. |
| RightBottomY | Float | Yes | Y-Axis coordinate of the bottom-right corner. |
| Unit | Integer | Yes | Specifies the coordinate unit. |

## EraseTimeArea

Smart Erase, specifies the region configuration.
Erase the designated region directly within a specified period.
When both BeginMs and EndMs are set to 0, directly perform removal of the designated region in the entire video.

Used by actions: CreateSmartEraseTemplate, ModifySmartEraseTemplate, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| BeginMs | Integer | Yes | Start time, in ms. |
| EndMs | Integer | Yes | End time, unit: ms. |
| Areas | Array of [EraseArea](#EraseArea) | Yes | Erases the domain list within the period. |

## ExecRuleTaskData

Conditional judgment output.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| RearDriveIndex | Array of Integer | Indexes of nodes that needs to be executed based on the conditional judgment for quality inspection. |

## ExecRulesTask

Task judgment conditions.

Used by actions: CreateSchedule, DescribeTaskDetail, ModifySchedule, ParseNotification.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Rules | Array of [Rules](#Rules) | No | Conditional judgment information. |

## ExtractBlindWatermarkTask

Extract video digital watermark task information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Media processing task ID. |
| Status | String | Task flow status. valid values:. |
| ErrCode | Integer | Error code. `0` indicates success. other values indicate failure. |
| Message | String | Error message. |
| InputInfo | [MediaInputInfo](#MediaInputInfo) | Target file information for media processing. |
| Type | String | Specifies the digital watermark type. valid values: blind-basic: basic version copyright digital watermark; blind-ab: ab copyright digital watermark.. |
| IsDetected | Boolean | Indicates whether a watermark is detected. if this parameter is true, the Result field will return the watermark extraction Result. if this parameter is false, the Result field will not return. |
| Result | String | Fetched watermark content. this field will not be returned when no detection. |
| ExtractBlindWatermarkConfig | [ExtractBlindWatermarkTaskConfig](#ExtractBlindWatermarkTaskConfig) | Extracts the digital watermark configuration. |

## ExtractBlindWatermarkTaskConfig

Extracts the digital watermark task configuration for video transcoding.

Used by actions: DescribeTaskDetail, ExtractBlindWatermark, ParseNotification.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SegmentDuration | Integer | Yes | Valid when the watermark type is blind-abseq. specifies the segment duration of the input video. unit: ms. Segment duration is 5 seconds by default if left empty. Note: This field may return null, indicating that no valid value can be obtained. |

## FaceConfigureInfo

Control parameter of a face recognition task

Used by actions: CreateAIRecognitionTemplate, DescribeAIRecognitionTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a face recognition task. Valid values: ON: Enables an intelligent face recognition task;OFF: Disables an intelligent face recognition task. |
| Score | Float | No | Face recognition filter score. If this score is reached or exceeded, a recognition result will be returned. Value range: 0-100. Default value: 95. |
| DefaultLibraryLabelSet | Array of String | No | The default face filter labels, which specify the types of faces to return. If this parameter is left empty, the detection results for all labels are returned. Valid values: entertainment (people in the entertainment industry)sport (sports celebrities)politician |
| UserDefineLibraryLabelSet | Array of String | No | Custom face tags for filter, which specify the face recognition results to return. If this parameter is not specified or left empty, the recognition results for all custom face tags are returned. Up to 100 tags are allowed, each containing no more than 16 characters. |
| FaceLibrary | String | No | Figure library. Valid values: Default: Default figure library;UserDefine: Custom figure library.All: Both default and custom figure libraries will be used. Default value: All (both default and custom figure libraries will be used.) |

## FaceConfigureInfoForUpdate

Control parameter of a face recognition task

Used by actions: ModifyAIRecognitionTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a face recognition task. Valid values: ON: Enables an intelligent face recognition task;OFF: Disables an intelligent face recognition task. |
| Score | Float | No | Face recognition filter score. If this score is reached or exceeded, a recognition result will be returned. Value range: 0-100. |
| DefaultLibraryLabelSet | Array of String | No | The default face filter labels, which specify the types of faces to return. If this parameter is left empty, the detection results for all labels are returned. Valid values: entertainment (people in the entertainment industry)sport (sports celebrities)politician |
| UserDefineLibraryLabelSet | Array of String | No | Custom face tags for filter, which specify the face recognition results to return. If this parameter is not specified or left empty, the recognition results for all custom face tags are returned. Up to 100 tags are allowed, each containing no more than 16 characters. |
| FaceLibrary | String | No | Figure library. Valid values: Default: Default figure library;UserDefine: Custom figure library.All: Both default and custom figure libraries will be used. |

## FaceEnhanceConfig

Face enhancement configuration.

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Intensity | Float | No | The strength. Value range: 0.0-1.0 Default value: 0.0. Note: This field may return null, indicating that no valid values can be obtained. |

## FrameRateConfig

Frame interpolation configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Fps | Integer | No | The frame rate (Hz). Value range: [0, 100]. Default value: 0. Note: For transcoding, this parameter will overwrite `Fps` of `VideoTemplate`. Note: This field may return null, indicating that no valid values can be obtained. |

## FrameRateWithDenConfig

New frame interpolation configuration, which supports fractional frame rates.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Capability configuration switch. Valid values: ON: enabled.OFF: disabled. Default value: ON. |
| FpsNum | Integer | No | Frame rate numerator. Value range: non-negative number, which should be less than 120 when divided by the denominator, and in the unit of Hz. The default value is 0. Note: For transcoding, this parameter will overwrite the Fps in the VideoTemplate. Note: This field may return null, indicating that no valid values can be obtained. |
| FpsDen | Integer | No | Frame rate denominator.Value range: numbers equal to or greater than 1. The default value is 1. Note: For transcoding, this parameter will overwrite the FpsDenominator in the VideoTemplate. Note: This field may return null, indicating that no valid values can be obtained. |

## FrameTagConfigureInfo

Control parameter of intelligent frame-specific tagging task

Used by actions: CreateAIAnalysisTemplate, DescribeAIAnalysisTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of intelligent frame-specific tagging task. Valid values: ON: enables intelligent frame-specific tagging task;OFF: disables intelligent frame-specific tagging task. |

## FrameTagConfigureInfoForUpdate

Control parameter of intelligent frame-specific tagging task

Used by actions: ModifyAIAnalysisTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of intelligent frame-specific tagging task. Valid values: ON: enables intelligent frame-specific tagging task;OFF: disables intelligent frame-specific tagging task. |

## HLSConfigureInfo

HLS configuration parameters

Used by actions: CreateLiveRecordTemplate, DescribeLiveRecordTemplates, ModifyLiveRecordTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ItemDuration | Integer | No | Duration of a single TS file in seconds. Value range: 5-30 seconds.  If this parameter is left empty, 30 seconds will be used by default. Note: This field may return null, indicating that no valid value can be obtained. |
| Interval | Integer | No | Recording cycle in seconds. Value range: 10 minutes to 12 hours.  If this parameter is left empty, 10 minutes (3600 seconds) will be used by default. Note: This field may return null, indicating that no valid value can be obtained. |
| ContinueTimeout | Integer | No | Resume recording waiting time, unit: seconds. Value range: 60-1800 seconds. If this parameter is left empty, 0 (resume recording not enabled) will be used by default. Note: This field may return null, indicating that no valid value can be obtained. |

## HdrConfig

HDR configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Type | String | No | Type. Valid values: HDR10HLG Default value: HDR10. Note: The video encoding method should be h264 or h265. Note: The video encoding bit depth is 10. Note: This field may return null, indicating that no valid values can be obtained. |

## HeadTailParameter

Opening and closing credits parameters

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| HeadSet | Array of [MediaInputInfo](#MediaInputInfo) | No | The opening segments. Note: This field may return null, indicating that no valid values can be obtained. |
| TailSet | Array of [MediaInputInfo](#MediaInputInfo) | No | The closing segments. Note: This field may return null, indicating that no valid values can be obtained. |

## HighlightSegmentItem

The information of a highlight segment.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | The confidence score. |
| StartTimeOffset | Float | The start time offset of the segment. |
| EndTimeOffset | Float | The end time offset of the segment. |
| SegmentTags | Array of String | Segment tag. Note: This field may return null, indicating that no valid values can be obtained. |
| BeginTime | String | Start time of the live streaming segment in ISO date and time format. |
| EndTime | String | End time of the live streaming segment in ISO date and time format. |
| Title | String | Highlight title. |
| Summary | String | Highlight overview. |

## ImageAreaBoxInfo

Information on the box selection area in an image.

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | No | Type of the box selection area in the image. Valid values: logo: icon.Text: text. Default value: logo. Note: This field may return null, indicating that no valid value can be obtained. |
| AreaCoordSet | Array of Integer | No | Coordinates (pixel-level) of the box selection area in the image, in the format of [x1, y1, x2, y2]. It indicates the coordinates of the top left corner and the bottom right corner. Note: The maximum value of this field is 4096. For example, [101, 85, 111, 95]. Note: This field may return null, indicating that no valid values can be obtained. |
| BoundingBox | Array of Float | No | Coordinates of the box selection area in the image, in the format of [x1, y1, x2, y2]. It indicates the coordinates of the top left corner and the bottom right corner. This field takes effect when AreaCoordSet is not specified. When it indicates the pixel, the maximum value of this field is 4096. - [0.1, 0.1, 0.3, 0.3]: indicates the ratio (values are less than 1). - [50, 50, 350, 280]: indicates the pixel (values are greater than or equal to 1). Note: This field may return null, indicating that no valid values can be obtained. |
| BoundingBoxUnitType | Integer | No | BoundingBox field unit. When the value is set to 0, select the unit automatically according to the field rule. When it is set to 1, the unit is ratio. When it is set to 2, the unit is pixel. |

## ImageDenoiseConfig

Image denoising configuration.

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Capability configuration enabling status. Valid values: ON: enabled.OFF: disabled. Default value: ON. |
| Type | String | No | Type, with valid values including: weakstrong Default value: weak. Note: This field may return null, indicating that no valid value can be obtained. |

## ImageEncodeConfig

Image encoding format parameters

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Format | String | No | Image format. Valid values: JPEG, PNG, BMP, and WebP. If it is not specified, the original image format is used. Animations are not supported. Note: This field may return null, indicating that no valid value can be obtained. |
| Quality | Integer | No | Relative image quality. Valid range: 1 - 100. The value is based on the original image quality, and the default is the original image quality. Note: This field may return null, indicating that no valid value can be obtained. |

## ImageEnhanceConfig

Image enhancement parameters

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SuperResolution | [SuperResolutionConfig](#SuperResolutionConfig) | No | Super-resolution configuration. |
| AdvancedSuperResolutionConfig | [AdvancedSuperResolutionConfig](#AdvancedSuperResolutionConfig) | No | Advanced super-resolution configuration. |
| Denoise | [ImageDenoiseConfig](#ImageDenoiseConfig) | No | Denoising configuration. Note: This field may return null, indicating that no valid value can be obtained. |
| ImageQualityEnhance | [ImageQualityEnhanceConfig](#ImageQualityEnhanceConfig) | No | Comprehensive enhancement configuration. Note: This field may return null, indicating that no valid value can be obtained. |
| ColorEnhance | [ColorEnhanceConfig](#ColorEnhanceConfig) | No | Color enhancement configuration. |
| SharpEnhance | [SharpEnhanceConfig](#SharpEnhanceConfig) | No | Detail enhancement configuration. |
| FaceEnhance | [FaceEnhanceConfig](#FaceEnhanceConfig) | No | Face enhancement configuration. |
| LowLightEnhance | [LowLightEnhanceConfig](#LowLightEnhanceConfig) | No | Low-light enhancement configuration. Note: This field may return null, indicating that no valid value can be obtained. |

## ImageEraseConfig

Image erasing parameter.

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImageEraseLogo | [ImageEraseLogoConfig](#ImageEraseLogoConfig) | No | Icon erasing configuration. Note: This field may return null, indicating that no valid value can be obtained. |

## ImageEraseLogoConfig

Icon erasing configuration.

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Capability configuration enabling status. Valid values: ON: enabledOFF: disabled Default value: ON. Note: This field may return null, indicating that no valid value can be obtained. |
| ImageAreaBoxes | Array of [ImageAreaBoxInfo](#ImageAreaBoxInfo) | No | Multiple box selection areas that need to be erased, with a maximum of 16 areas available. Note: This field may return null, indicating that no valid value can be obtained.  Note: This field may return null, indicating that no valid value can be obtained. |

## ImageProcessTaskOutput

Image processing result information.

Used by actions: DescribeImageTaskDetail.

| Name | Type | Description |
| --- | --- | --- |
| Path | String | Path of the output file. Note: This field may return null, indicating that no valid value can be obtained. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of the output file. Note: This field may return null, indicating that no valid value can be obtained. |
| Content | String | Processing result of the image-to-text task. |

## ImageProcessTaskResult

Result type of the image processing task.

Used by actions: DescribeImageTaskDetail.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. Note: This field may return null, indicating that no valid value can be obtained. |
| ErrMsg | String | Error code. A null string indicates that the task is successful, while other values indicate that the task has failed. For valid values, see the list of [MPS error codes](https://www.tencentcloud.comom/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81). |
| Message | String | Error message. Note: This field may return null, indicating that no valid value can be obtained. |
| Output | [ImageProcessTaskOutput](#ImageProcessTaskOutput) | Transcoding task output. Note: This field may return null, indicating that no valid value can be obtained. |
| Progress | Integer | Transcoding progress, with a value range of [0-100]. Note: This field may return null, indicating that no valid value can be obtained. |

## ImageQualityEnhanceConfig

Overall enhancement configuration.

Used by actions: CreateProcessImageTemplate, CreateTranscodeTemplate, ModifyProcessImageTemplate, ModifyTranscodeTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Type | String | No | The strength. Valid values: weaknormalstrong Default value: weak. Note: This field may return null, indicating that no valid values can be obtained. |

## ImageSpriteTaskInput

Input parameter type of an image sprite generating task

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | ID of an image sprite generating template. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | Target bucket of a generated image sprite. If this parameter is left empty, the `OutputStorage` value of the upper folder will be inherited. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputObjectPath | String | No | Output path of a captured sprite image file, which can be a relative or absolute path. If you need to define an output path, the path must end with `.{format}`. For variable names, refer to [Filename Variable](https://intl.cloud.tencent.com/document/product/862/37039?from_cn_redirect=1).Relative path example: Filename_{Variable name}.{format}.Filename.{format}. Absolute path example: /Custom path/Filename_{Variable name}.{format}. If left empty, a relative path is used by default: `{inputName}_imageSprite_{definition}_{number}.{format}`. |
| WebVttObjectName | String | No | Output path to the WebVTT file after an image sprite is generated, which can only be a relative path. If this parameter is left empty, the following relative path will be used by default: `{inputName}_imageSprite_{definition}.{format}`. |
| ObjectNumberFormat | [NumberFormat](#NumberFormat) | No | Rule of the `{number}` variable in the image sprite output path. Note: This field may return null, indicating that no valid values can be obtained. |

## ImageSpriteTemplate

Details of an image sprite generating template

Used by actions: DescribeImageSpriteTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of an image sprite generating template. |
| Type | String | Template type. Valid values: Preset: Preset template;Custom: Custom template. |
| Name | String | Name of an image sprite generating template. |
| Width | Integer | Subimage width of an image sprite. |
| Height | Integer | Subimage height of an image sprite. |
| ResolutionAdaptive | String | Resolution adaption. Valid values: open: enabled. In this case, `Width` represents the long side of a video, while `Height` the short side;close: disabled. In this case, `Width` represents the width of a video, while `Height` the height. Default value: open. |
| SampleType | String | Sampling type. |
| SampleInterval | Integer | Sampling interval. |
| RowCount | Integer | Subimage row count of an image sprite. |
| ColumnCount | Integer | Subimage column count of an image sprite. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| FillType | String | Fill type. "Fill" refers to the way of processing a screenshot when its aspect ratio is different from that of the source video. The following fill types are supported:  stretch: Stretch. The screenshot will be stretched frame by frame to match the aspect ratio of the source video, which may make the screenshot "shorter" or "longer";black: Fill with black. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with black color blocks. Default value: black. |
| Comment | String | Template description. |
| Format | String | The image format. |

## ImageTaskInput

Image task input parameters

Used by actions: CreateProcessImageTemplate, DescribeProcessImageTemplates, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| EncodeConfig | [ImageEncodeConfig](#ImageEncodeConfig) | No | Image encoding configuration. Note: This field may return null, indicating that no valid value can be obtained. |
| EnhanceConfig | [ImageEnhanceConfig](#ImageEnhanceConfig) | No | Image enhancement configuration. Note: This field may return null, indicating that no valid value can be obtained. |
| EraseConfig | [ImageEraseConfig](#ImageEraseConfig) | No | Image erasing configuration. Note: This field may return null, indicating that no valid value can be obtained. |

## ImageWatermarkInput

Input parameter of an image watermarking template

Used by actions: CreateWatermarkTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImageContent | String | Yes | String generated by [Base64-encoding](https://tools.ietf.org/html/rfc4648) a watermark image. JPEG and PNG images are supported. |
| Width | String | No | Width of a watermark, supporting two formats: % and px. If a string ends with %, it indicates that the `Width` of a watermark is a percentage of a video's width. For example, `10%` means that `Width` is 10% of a video's width.If a string ends with px, the `Width` of a watermark will be in pixels. For example, `100px` means that `Width` is 100 pixels. Value range: [8, 4096].  When width and height are not specified or set to 0, the default value is 10%. |
| Height | String | No | Watermark height. % and px formats are supported: If the string ends in %, the `Height` of the watermark will be the specified percentage of the video height. For example, `10%` means that `Height` is 10% of the video height;If the string ends in px, the `Height` of the watermark will be in pixels. For example, `100px` means that `Height` is 100 pixels. Value range: 0 or [8, 4096]. Default value: 0px, which means that `Height` will be proportionally scaled according to the aspect ratio of the original watermark image. |
| RepeatType | String | No | Repeat type of an animated watermark. Valid values: once: no longer appears after watermark playback ends.repeat_last_frame: stays on the last frame after watermark playback ends.repeat (default): repeats the playback until the video ends. |

## ImageWatermarkInputForUpdate

Input parameter of an image watermarking template

Used by actions: ModifyWatermarkTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImageContent | String | No | String generated by [Base64-encoding](https://tools.ietf.org/html/rfc4648) a watermark image. JPEG and PNG images are supported. |
| Width | String | No | Watermark width. % and px formats are supported: If the string ends in %, the `Width` of the watermark will be the specified percentage of the video width. For example, `10%` means that `Width` is 10% of the video width;If the string ends in px, the `Width` of the watermark will be in pixels. For example, `100px` means that `Width` is 100 pixels. Value range: [8, 4096]. |
| Height | String | No | Height of a watermark, supporting two formats: % and px. If a string ends with %, it indicates that the `Height` of a watermark is a percentage of a video's height. For example, `10%` means that `Height` is 10% of a video's height.If a string ends with px, the `Height` of a watermark will be in pixels. For example, `100px` means that `Height` is 100 pixels. Value range: 0 or [8, 4096]. |
| RepeatType | String | No | Repeat type of an animated watermark. Valid values: once: no longer appears after watermark playback ends.repeat_last_frame: stays on the last frame after watermark playback ends.repeat (default): repeats the playback until the video ends. |

## ImageWatermarkTemplate

Image watermarking template

Used by actions: DescribeWatermarkTemplates.

| Name | Type | Description |
| --- | --- | --- |
| ImageUrl | String | Watermark image address. |
| Width | String | Watermark width. % and px formats are supported: If the string ends in %, the `Width` of the watermark will be the specified percentage of the video width; for example, `10%` means that `Width` is 10% of the video width;If the string ends in px, the `Width` of the watermark will be in px; for example, `100px` means that `Width` is 100 px. |
| Height | String | Watermark height. % and px formats are supported: If the string ends in %, the `Height` of the watermark will be the specified percentage of the video height. For example, `10%` means that `Height` is 10% of the video height;If the string ends in px, the `Height` of the watermark will be in pixels. For example, `100px` means that `Height` is 100 pixels. `0px` means that `Height` will be proportionally scaled according to the video width. |
| RepeatType | String | Repeat type of an animated watermark. Valid values: once: no longer appears after watermark playback ends.repeat_last_frame: stays on the last frame after watermark playback ends.repeat (default): repeats the playback until the video ends. |

## LiveActivityResItem

The output of a live scheme subtask.

Used by actions: DescribeTaskDetail.

| Name | Type | Description |
| --- | --- | --- |
| LiveRecordTask | [LiveScheduleLiveRecordTaskResult](#LiveScheduleLiveRecordTaskResult) | The output of a live recording task. Note: This field may return null, indicating that no valid values can be obtained. |
| LiveQualityControlTask | [ScheduleQualityControlTaskResult](#ScheduleQualityControlTaskResult) | Media quality inspection task output. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveActivityResult

The output of a live scheme subtask.

Used by actions: DescribeTaskDetail.

| Name | Type | Description |
| --- | --- | --- |
| ActivityType | String | Atomic task type. LiveRecord: live recordingAiQualityControl: media quality inspection |
| LiveActivityResItem | [LiveActivityResItem](#LiveActivityResItem) | The task output. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveAiAnalysisDescriptionItem

Information about the live streaming summary result.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Paragraphs | Array of [LiveAiParagraphInfo](#LiveAiParagraphInfo) | Segmentation result. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveAiParagraphInfo

Segment information.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Summary | String | Segment summary. |
| Title | String | Segment title. |
| Keywords | Array of String | Segment keyword. |
| StartTimeOffset | Float | Starting time point of the segment, in seconds. |
| EndTimeOffset | Float | End time point of the segment, in seconds. |
| BeginTime | String | Starting time point of the live streaming segment in ISO date and time format. |
| EndTime | String | End time point of the live streaming segment in ISO date and time format. |

## LiveRecordFile

The information of a live recording file.

Used by actions: DescribeTaskDetail, ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Url | String | The URL of the recording file. Note: This field may return null, indicating that no valid values can be obtained. |
| Size | Integer | The size of the recording file. Note: This field may return null, indicating that no valid values can be obtained. |
| Duration | Integer | The duration of the recording file. Note: This field may return null, indicating that no valid values can be obtained. |
| StartTime | String | The recording start time in [ISO date format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). Note: This field may return null, indicating that no valid values can be obtained. |
| EndTime | String | The recording end time in [ISO date format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). Note: This field may return null, indicating that no valid values can be obtained. |

## LiveRecordResult

The live recording result.

Used by actions: DescribeTaskDetail.

| Name | Type | Description |
| --- | --- | --- |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | The storage of the recording file. Note: This field may return null, indicating that no valid values can be obtained. |
| FileList | Array of [LiveRecordFile](#LiveRecordFile) | The recording segments. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveRecordTaskInput

The input parameters of a live recording task.

Used by actions: DescribeTaskDetail.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | The live recording template ID. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | The storage of the recording file. If this parameter is left empty, the `OutputStorage` value of the parent folder will be inherited. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputObjectPath | String | No | The output path of the recording file. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveRecordTemplate

Live recording template details

Used by actions: DescribeLiveRecordTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Specifies the recording template unique identifier. |
| HLSConfigure | [HLSConfigureInfo](#HLSConfigureInfo) | HLS configuration parameters |
| MP4Configure | [MP4ConfigureInfo](#MP4ConfigureInfo) | MP4 configuration parameter. |
| Name | String | Recording template name. |
| Comment | String | Template description. |
| Type | String | Template type. Valid values: Preset: system-preset template;Custom: Custom template. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| RecordType | String | Recording type. Valid values: video: audio and video recording; audio: audio recording; auto: automatic detection. |

## LiveScheduleLiveRecordTaskResult

The result of a live scheme's live recording task.

Used by actions: DescribeTaskDetail.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | The task status. Valid values: `PROCESSING`, `SUCCESS`, `FAIL`. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value indicates the task has failed. For details, see [Error Codes](https://www.tencentcloud.com/document/product/1041/40249). Note: This field may return null, indicating that no valid values can be obtained. |
| ErrCode | Integer | The error code. `0` indicates the task is successful; other values indicate the task has failed. This parameter is not recommended. Please use `ErrCodeExt` instead. Note: This field may return null, indicating that no valid values can be obtained. |
| Message | String | The error message. Note: This field may return null, indicating that no valid values can be obtained. |
| Input | [LiveRecordTaskInput](#LiveRecordTaskInput) | The input of a live recording task. Note: This field may return null, indicating that no valid values can be obtained. |
| Output | [LiveRecordResult](#LiveRecordResult) | The output of a live recording task. Note: This field may return null, indicating that no valid values can be obtained. |
| BeginProcessTime | String | The time when the task was started, in [ISO date format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). Note: This field may return null, indicating that no valid values can be obtained. |
| FinishTime | String | The time when the task was completed, in [ISO date format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). Note: This field may return null, indicating that no valid values can be obtained. |

## LiveScheduleTask

The information of a live scheme subtask.

Used by actions: DescribeTaskDetail.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Live orchestration task ID. |
| Status | String | Task stream status. Valid values: PROCESSING: processingFINISH: completed |
| ErrCode | Integer | An error code other than 0 is returned in case of a source exception. Use the error code of the specific task when a value of 0 is returned. |
| Message | String | The corresponding exception message is returned in case of a source exception. If no source exception occurs, use the message of each specific task. |
| Url | String | Live stream URL. |
| LiveActivityResultSet | Array of [LiveActivityResult](#LiveActivityResult) | The task output. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveSmartSubtitleResult

Smart subtitle task result for live stream.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Text | String | Recognized text. |
| StartPTSTime | Float | Translate the starting PTS time of a segment, in seconds. |
| EndPTSTime | Float | End PTS time of a translated segment, in seconds. |
| Trans | String | Translated text. |
| StartTime | String | Translation started at UTC time. Note: This field may return null, indicating that no valid values can be obtained. |
| EndTime | String | Translation ends at UTC time. Note: This field may return null, indicating that no valid values can be obtained. |
| SteadyState | Boolean | Steady-State tag. Note: This field may return null, indicating that no valid values can be obtained. |
| UserId | String | websocket and trtc real-time translation UserId. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveSmartSubtitlesTaskInput

Live stream smart subtitle input struct.

Used by actions: ProcessLiveStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | No | Smart subtitle template ID. |
| UserExtPara | String | No | User extension field, which does not need to be filled in for general scenarios. |

## LiveStreamAiAnalysisResultInfo

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| ResultSet | Array of [LiveStreamAiAnalysisResultItem](#LiveStreamAiAnalysisResultItem) | Live streaming analysis subtask result. Valid values: Live streaming video splitting.Live streaming highlight.Live streaming summary. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveStreamAiAnalysisResultItem

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | Result type. Valid values: SegmentRecognition: video splitting.Highlight: highlight.Description: summary. |
| SegmentResultSet | Array of [SegmentRecognitionItem](#SegmentRecognitionItem) |  |
| HighlightResultSet | Array of [MediaAiAnalysisHighlightItem](#MediaAiAnalysisHighlightItem) | Highlight result. This field is valid when Type is set to Highlight. Note: This field may return null, indicating that no valid values can be obtained. |
| DescriptionResult | [LiveAiAnalysisDescriptionItem](#LiveAiAnalysisDescriptionItem) | Summary result. It is valid when Type is Description. |

## LiveStreamAiQualityControlResultInfo

Live stream media quality inspection result.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| QualityControlResultSet | Array of [QualityControlResult](#QualityControlResult) | Content quality inspection result list. Note: This field may return null, indicating that no valid values can be obtained. |
| DiagnoseResultSet | Array of [DiagnoseResult](#DiagnoseResult) | Format diagnostic result list. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveStreamAiRecognitionResultInfo

Live stream AI recognition results

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| ResultSet | Array of [LiveStreamAiRecognitionResultItem](#LiveStreamAiRecognitionResultItem) | Content recognition result list. |

## LiveStreamAiRecognitionResultItem

AI-based live stream recognition result

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | Result type. Valid values: FaceRecognition: face recognition.AsrWordsRecognition: speech keyword recognition.OcrWordsRecognition: text keyword recognition.AsrFullTextRecognition: full speech recognition.OcrFullTextRecognition: full text recognition.TransTextRecognition: speech translation.  ObjectRecognition: object recognition.TagRecognition: highlights marking. |
| FaceRecognitionResultSet | Array of [LiveStreamFaceRecognitionResult](#LiveStreamFaceRecognitionResult) | Face recognition result, which is valid when `Type` is `FaceRecognition`. |
| AsrWordsRecognitionResultSet | Array of [LiveStreamAsrWordsRecognitionResult](#LiveStreamAsrWordsRecognitionResult) | Speech keyword recognition result, which is valid when `Type` is `AsrWordsRecognition`. |
| OcrWordsRecognitionResultSet | Array of [LiveStreamOcrWordsRecognitionResult](#LiveStreamOcrWordsRecognitionResult) | Text keyword recognition result, which is valid when `Type` is `OcrWordsRecognition`. |
| AsrFullTextRecognitionResultSet | Array of [LiveStreamAsrFullTextRecognitionResult](#LiveStreamAsrFullTextRecognitionResult) | Full speech recognition result, which is valid when `Type` is `AsrFullTextRecognition`. |
| OcrFullTextRecognitionResultSet | Array of [LiveStreamOcrFullTextRecognitionResult](#LiveStreamOcrFullTextRecognitionResult) | Full text recognition result, which is valid when `Type` is `OcrFullTextRecognition`. |
| TransTextRecognitionResultSet | Array of [LiveStreamTransTextRecognitionResult](#LiveStreamTransTextRecognitionResult) | The translation result. This parameter is valid only if `Type` is `TransTextRecognition`. |
| ObjectRecognitionResultSet | Array of [LiveStreamObjectRecognitionResult](#LiveStreamObjectRecognitionResult) | Object recognition result, which is valid when Type is ObjectRecognition. |
| TagRecognitionResultSet | Array of [LiveStreamTagRecognitionResult](#LiveStreamTagRecognitionResult) |  |

## LiveStreamAiReviewImagePoliticalResult

The result of detecting sensitive information in live streaming videos.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartPtsTime | Float | Start PTS time of a suspected segment in seconds. |
| EndPtsTime | Float | End PTS time of a suspected segment in seconds. |
| Confidence | Float | The confidence score for the detected sensitive segments. |
| Suggestion | String | Suggestion for porn information detection of a suspected segment. Valid values: passreviewblock |
| Label | String | The labels for the detected sensitive information. Valid values: politicianviolation_photo (banned icons) |
| Name | String | The name of a sensitive person or banned icon. |
| AreaCoordSet | Array of Integer | The pixel coordinates of the detected sensitive people or banned icons. The format is [x1, y1, x2, y2], which indicates the coordinates of the top-left and bottom-right corners. |
| Url | String | URL of a suspected image (which will not be permanently stored and will be deleted after `PicUrlExpireTime`). |
| PicUrlExpireTime | String | Expiration time of a suspected image URL in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## LiveStreamAiReviewImagePornResult

Result of porn information detection in image in AI-based live stream content audit

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartPtsTime | Float | Start PTS time of a suspected segment in seconds. |
| EndPtsTime | Float | End PTS time of a suspected segment in seconds. |
| Confidence | Float | Score of a suspected porn segment. |
| Suggestion | String | Suggestion for porn information detection of a suspected segment. Valid values: passreviewblock |
| Label | String | Tag of the detected porn information in video. Valid values: porn: Porn.sexy: Sexiness.vulgar: Vulgarity.intimacy: Intimacy. |
| Url | String | URL of a suspected image (which will not be permanently stored and will be deleted after `PicUrlExpireTime`). |
| PicUrlExpireTime | String | Expiration time of a suspected image URL in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## LiveStreamAiReviewImageTerrorismResult

The result of detecting sensitive information in live streaming videos.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartPtsTime | Float | Start PTS time of a suspected segment in seconds. |
| EndPtsTime | Float | End PTS time of a suspected segment in seconds. |
| Confidence | Float | The confidence score for the detected sensitive segments. |
| Suggestion | String | The suggestion for handling the sensitive segments. Valid values: passreviewblock |
| Label | String | The labels for the detected sensitive content. Valid values: gunscrowdpolicebloodybanners (sensitive flags)militantexplosionterrorists |
| Url | String | URL of a suspected image (which will not be permanently stored and will be deleted after `PicUrlExpireTime`). |
| PicUrlExpireTime | String | Expiration time of a suspected image URL in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## LiveStreamAiReviewResultInfo

Result of AI-based live stream audit

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| ResultSet | Array of [LiveStreamAiReviewResultItem](#LiveStreamAiReviewResultItem) | List of content audit results. |

## LiveStreamAiReviewResultItem

Result of AI-based live stream audit

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | The type of moderation result. Valid values: ImagePornImageTerrorismImagePoliticalVoicePorn |
| ImagePornResultSet | Array of [LiveStreamAiReviewImagePornResult](#LiveStreamAiReviewImagePornResult) | Result of porn information detection in image, which is valid when `Type` is `ImagePorn`. |
| ImageTerrorismResultSet | Array of [LiveStreamAiReviewImageTerrorismResult](#LiveStreamAiReviewImageTerrorismResult) | The result of detecting sensitive information in images, which is valid if `Type` is `ImageTerrorism`. |
| ImagePoliticalResultSet | Array of [LiveStreamAiReviewImagePoliticalResult](#LiveStreamAiReviewImagePoliticalResult) | The result of detecting sensitive information in images, which is valid if `Type` is `ImagePolitical`. |
| VoicePornResultSet | Array of [LiveStreamAiReviewVoicePornResult](#LiveStreamAiReviewVoicePornResult) | The result for moderation of pornographic content in audio. This parameter is valid if `Type` is `VoicePorn`. |

## LiveStreamAiReviewVoicePornResult

Result of porn information detection in speech in AI-based live stream content audit

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartPtsTime | Float | Start PTS time of a suspected segment in seconds. |
| EndPtsTime | Float | End PTS time of a suspected segment in seconds. |
| Confidence | Float | Score of a suspected porn segment. |
| Suggestion | String | Suggestion for porn information detection of a suspected segment. Valid values: passreviewblock |
| Label | String | Tag of the detected porn information in video. Valid values: sexual_moan: Sexual moans. |

## LiveStreamAiSmartSubtitleResultInfo

Smart subtitle task result for live stream.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| SmartSubtitleResult | Array of [LiveSmartSubtitleResult](#LiveSmartSubtitleResult) | Live stream smart subtitling task result list. |

## LiveStreamAsrFullTextRecognitionResult

ASR-based full live stream recognition

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Text | String | Recognized text. |
| StartPtsTime | Float | Start PTS time of recognized segment in seconds. |
| EndPtsTime | Float | End PTS time of recognized segment in seconds. |
| Confidence | Float | Confidence of recognized segment. Value range: 0–100. |
| StartTime | String |  |
| EndTime | String |  |
| SteadyState | Boolean |  |
| UserId | String | User ID in the result of recognition via WebSocket and TRTC.Note: This field may return null, indicating that no valid value can be obtained. |

## LiveStreamAsrWordsRecognitionResult

AI-based ASR-based live streaming keyword recognition result

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Word | String | Speech keyword. |
| StartPtsTime | Float | Start PTS time of recognized segment in seconds. |
| EndPtsTime | Float | End PTS time of recognized segment in seconds. |
| Confidence | Float | Confidence of recognized segment. Value range: 0–100. |

## LiveStreamFaceRecognitionResult

AI-based live streaming face recognition result

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Id | String | Unique ID of figure. |
| Name | String | Figure name. |
| Type | String | Figure library type, indicating to which figure library the recognized figure belongs: Default: default figure libraryUserDefine: custom figure library |
| StartPtsTime | Float | Start PTS time of recognized segment in seconds. |
| EndPtsTime | Float | End PTS time of recognized segment in seconds. |
| Confidence | Float | Confidence of recognized segment. Value range: 0–100. |
| AreaCoordSet | Array of Integer | Zone coordinates of recognition result. The array contains four elements: [x1,y1,x2,y2], i.e., the horizontal and vertical coordinates of the top-left and bottom-right corners. |

## LiveStreamObjectRecognitionResult

Live streaming AI object recognition result.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Name | String | Name of a recognized object. |
| StartPtsOffset | Float | Start PTS time of a recognized segment, in seconds. |
| EndPtsOffset | Float | End PTS time of a recognized segment, in seconds. |
| Confidence | Float | Confidence of a recognized segment. Value range: 0-100. |
| AreaCoordSet | Array of Integer | Zone coordinates of the recognition result. An array contains four elements: [x1, y1, x2, y2], representing the horizontal and vertical coordinates of the top-left and bottom-right corners, respectively. |
| Url | String | Screenshot link. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveStreamOcrFullTextRecognitionResult

OCR-based full live stream recognition

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Text | String | Speech text. |
| StartPtsTime | Float | Start PTS time of recognized segment in seconds. |
| EndPtsTime | Float | End PTS time of recognized segment in seconds. |
| Confidence | Float | Confidence of recognized segment. Value range: 0–100. |
| AreaCoordSet | Array of Integer | Zone coordinates of recognition result. The array contains four elements: [x1,y1,x2,y2], i.e., the horizontal and vertical coordinates of the top-left and bottom-right corners. |

## LiveStreamOcrWordsRecognitionResult

AI-based OCR-based live streaming keyword recognition result

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Word | String | Text keyword. |
| StartPtsTime | Float | Start PTS time of recognized segment in seconds. |
| EndPtsTime | Float | End PTS time of recognized segment in seconds. |
| Confidence | Float | Confidence of recognized segment. Value range: 0–100. |
| AreaCoords | Array of Integer | Zone coordinates of recognition result. The array contains four elements: [x1,y1,x2,y2], i.e., the horizontal and vertical coordinates of the top-left and bottom-right corners. |

## LiveStreamProcessErrorInfo

Information of a live stream processing error

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| ErrCode | Integer | Error code: 0: No error;If this parameter is not 0, an error has occurred. Please see the error message (`Message`). |
| Message | String | Error message. |

## LiveStreamProcessTask

Information of a live stream processing task

Used by actions: DescribeTaskDetail.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | The media processing task ID. |
| Status | String | Task flow status. Valid values: PROCESSING: Processing;FINISH: Completed. |
| ErrCode | Integer | Error code. 0: success; other values: failure. |
| Message | String | Error message. |
| Url | String | Live stream URL. |

## LiveStreamRecordResultInfo

Live stream recording result.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| RecordOver | Integer | Whether recording ends. 0: Recording does not end, returning a single file. 1: Recording ends, returning all recording files. Note: This field may return null, indicating that no valid values can be obtained. |
| FileResults | Array of [LiveRecordFile](#LiveRecordFile) | File list.  Note: This field may return null, indicating that no valid values can be obtained. |

## LiveStreamTagRecognitionResult

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Id | String |  |
| StartPtsTime | Float |  |
| EndPtsTime | Float |  |
| Confidence | Float |  |

## LiveStreamTaskNotifyConfig

Event notification configuration of a task.

Used by actions: ProcessLiveStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| NotifyType | String | No | Notification type: TDMQ-CMQ: message queue. "URL": When a URL is specified, HTTP callbacks are pushed to the address specified by NotifyUrl. The callback protocol is HTTP+JSON. The content of the packet body is the same as the output parameters of [ParseLiveStreamProcessNotification](https://www.tencentcloud.comom/document/product/862/39229?from_cn_redirect=1).  Note: if it is unspecified or left blank, no callback will be sent. To send a callback, fill in the corresponding type value. |
| NotifyUrl | String | No | HTTP callback URL, required if `NotifyType` is set to `URL` |
| CmqModel | String | No | Queue and Topic models are provided. |
| CmqRegion | String | No | Region when NotifyType is set to TDMQ-CMQ. For example, sh or bj. |
| QueueName | String | No | This field is valid when the model is Queue. It indicates the name of the TDMQ for CMQ queue for receiving event notifications. |
| TopicName | String | No | This field is valid when the model is Topic. It indicates the name of the TDMQ for CMQ topic for receiving event notifications. |
| NotifyKey | String | No | Key used to generate a callback signature. Note: This field may return null, indicating that no valid values can be obtained. |

## LiveStreamTransTextRecognitionResult

The live stream translation result.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Text | String | The text transcript. |
| StartPtsTime | Float | The PTS (seconds) of the start of a segment. |
| EndPtsTime | Float | The PTS (seconds) of the end of a segment. |
| Confidence | Float | The confidence score for a segment. Value range: 0-100. |
| Trans | String | The translation. |
| StartTime | String |  |
| EndTime | String |  |
| SteadyState | Boolean |  |
| UserId | String | User ID in the result of real-time translation via WebSocket and TRTC. Note: This field may return null, indicating that no valid value can be obtained. |

## LowLightEnhanceConfig

Low-light enhancement configuration.

Used by actions: CreateProcessImageTemplate, CreateTranscodeTemplate, ModifyProcessImageTemplate, ModifyTranscodeTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Type | String | No | The strength. Valid values: normal Default value: normal. Note: This field may return null, indicating that no valid values can be obtained. |

## MP4ConfigureInfo

MP4 configuration parameter.

Used by actions: CreateLiveRecordTemplate, DescribeLiveRecordTemplates, ModifyLiveRecordTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Interval | Integer | No | Recording duration, in seconds. The interval can range from 10 minutes to 720 minutes. It is 60 minutes (3,600 seconds) by default. |

## MediaAiAnalysisClassificationItem

Intelligent categorization result

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Classification | String | Name of intelligently generated category. |
| Confidence | Float | Confidence of intelligently generated category between 0 and 100. |

## MediaAiAnalysisCoverItem

Information of intelligently generated cover

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| CoverPath | String | Storage path of intelligently generated cover. |
| Confidence | Float | Confidence of intelligently generated cover between 0 and 100. |

## MediaAiAnalysisDescriptionItem

Intelligent description information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Description | String | Intelligent description. |
| Confidence | Float | Confidence of the intelligent description, with a value range from 0 to 100. |
| Title | String | Intelligent description title. |
| Keywords | Array of String | Intelligent description keywords. |
| Paragraphs | Array of [AiParagraphInfo](#AiParagraphInfo) | Segmentation result. Note: This field may return null, indicating that no valid values can be obtained. |
| MindMapUrl | String | Address of the mind map of a summary task. Note: This field may return null, indicating that no valid value can be obtained. |
| MindMapPath | String | Path of the mind map of a summary task. |
| SubtitlePath | String | Subtitle file path of the video. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of the summary file. |

## MediaAiAnalysisFrameTagItem

Result information of intelligent frame-specific tagging

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Tag | String | Frame-specific tag name. |
| CategorySet | Array of String |  |
| Confidence | Float | Confidence of intelligently generated frame-specific tag between 0 and 100. |

## MediaAiAnalysisFrameTagSegmentItem

List of frame-specific tag segments

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of frame-specific tag. |
| EndTimeOffset | Float | End time offset of frame-specific tag. |
| TagSet | Array of [MediaAiAnalysisFrameTagItem](#MediaAiAnalysisFrameTagItem) | List of tags in time period. |

## MediaAiAnalysisHighlightItem

The information of intelligently generated highlight segments.

Used by actions: DescribeTaskDetail, ParseLiveStreamProcessNotification, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| HighlightPath | String | The URL of the highlight segments. |
| CovImgPath | String | The URL of the thumbnail. |
| Confidence | Float | The confidence score. Value range: 0-100. |
| Duration | Float | The duration of the highlights. |
| SegmentSet | Array of [HighlightSegmentItem](#HighlightSegmentItem) | A list of the highlight segments. |
| HighlightUrl | String | Intelligent highlight address. Note: This field may return null, indicating that no valid values can be obtained. |
| CovImgUrl | String | Intelligent highlight cover address. Note: This field may return null, indicating that no valid values can be obtained. |

## MediaAiAnalysisTagItem

Result information of intelligent tagging

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Tag | String | Tag name. |
| Confidence | Float | Confidence of tag between 0 and 100. |
| SpecialInfo | String | Varies based on different types. |

## MediaAnimatedGraphicsItem

Result information of an animated image generating task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Storage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of a generated animated image file. |
| Path | String | Path to a generated animated image file. |
| Definition | Integer | Specifies the rotating image template ID. see [rotating image template](https://intl.cloud.tencent.com/document/product/862/77168?from_cn_redirect=1#.E8.BD.AC.E5.8A.A8.E5.9B.BE.E6.A8.A1.E6.9D.BF.5B.5D(ID.3Amove)). |
| Container | String | Animated image format, such as gif. |
| Height | Integer | Height of an animated image in px. |
| Width | Integer | Width of an animated image in px. |
| Bitrate | Integer | Bitrate of an animated image in bps. |
| Size | Integer | Size of an animated image in bytes. |
| Md5 | String | MD5 value of an animated image. |
| StartTimeOffset | Float | Start time offset of an animated image in the video in seconds. |
| EndTimeOffset | Float | End time offset of an animated image in the video in seconds. |

## MediaAudioStreamItem

Information of the audio stream in a VOD file

Used by actions: DescribeBatchTaskDetail, DescribeMediaMetaData, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Bitrate | Integer | Bitrate of an audio stream in bps. Note: This field may return null, indicating that no valid values can be obtained. |
| SamplingRate | Integer | Sample rate of an audio stream in Hz. Note: This field may return null, indicating that no valid values can be obtained. |
| Codec | String | Audio stream codec, such as aac. Note: This field may return null, indicating that no valid values can be obtained. |
| Channel | Integer | Number of sound channels, e.g., 2 Note: this field may return `null`, indicating that no valid value was found. |

## MediaContentReviewAsrTextSegmentItem

Suspected segment identified during ASR-based text audit during content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a suspected segment in seconds. |
| EndTimeOffset | Float | End time offset of a suspected segment in seconds. |
| Confidence | Float | Confidence of a suspected segment. |
| Suggestion | String | Suggestion for suspected segment audit. Valid values: pass.review.block. |
| KeywordSet | Array of String | List of suspected keywords. |

## MediaContentReviewOcrTextSegmentItem

Suspected segment identified during OCR-based text audit during content audit

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a suspected segment in seconds. |
| EndTimeOffset | Float | End time offset of a suspected segment in seconds. |
| Confidence | Float | Confidence of a suspected segment. |
| Suggestion | String | Suggestion for suspected segment audit. Valid values: pass.review.block. |
| KeywordSet | Array of String | List of suspected keywords. |
| AreaCoordSet | Array of Integer | Zone coordinates (at the pixel level) of suspected text: [x1, y1, x2, y2], i.e., the coordinates of the top-left and bottom-right corners. |
| Url | String | URL of a suspected image (which will not be permanently stored and will be deleted after `PicUrlExpireTime`). |
| PicUrlExpireTime | String | Expiration time of a suspected image URL in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## MediaContentReviewPoliticalSegmentItem

The information about the sensitive segments detected.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a suspected segment in seconds. |
| EndTimeOffset | Float | End time offset of a suspected segment in seconds. |
| Confidence | Float | The confidence score for the detected sensitive segments. |
| Suggestion | String | The suggestion for handling the sensitive segments. Valid values: passreviewblock |
| Name | String | The name of a sensitive person or banned icon. |
| Label | String | The labels for the detected sensitive segments. The relationship between the values of this parameter and those of the `LabelSet` parameter in [PoliticalImgReviewTemplateInfo](https://intl.cloud.tencent.com/document/api/862/37615?from_cn_redirect=1#PoliticalImgReviewTemplateInfo) is as follows: violation_photo: violation_photo (banned icons) politician: nation_politician (state leader)province_politician (provincial officials)bureau_politician (bureau-level officials)county_politician (county-level officials)rural_politician (township-level officials)sensitive_politician (sensitive people)foreign_politician (state leaders of other countries) entertainment: sensitive_entertainment (sensitive people in the entertainment industry sport: sensitive_sport (sensitive sports celebrities) entrepreneur: sensitive_entrepreneur scholar: sensitive_scholar celebrity: sensitive_celebrityhistorical_celebrity (sensitive historical figures) military: sensitive_military (sensitive people in military) |
| Url | String | URL of a suspected image (which will not be permanently stored  and will be deleted after `PicUrlExpireTime`). |
| AreaCoordSet | Array of Integer | The pixel coordinates of the detected sensitive people or banned icons. The format is [x1, y1, x2, y2], which indicates the coordinates of the top-left and bottom-right corners. |
| PicUrlExpireTime | String | Expiration time of a suspected image URL in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## MediaContentReviewSegmentItem

The information about the detected pornographic/sensitive segments.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTimeOffset | Float | Start time offset of a suspected segment in seconds. |
| EndTimeOffset | Float | End time offset of a suspected segment in seconds. |
| Confidence | Float | Score of a suspected porn segment. |
| Label | String | Tag of porn information detection result of a suspected segment. |
| Suggestion | String | Suggestion for porn information detection of a suspected segment. Valid values: pass.review.block. |
| Url | String | URL of a suspected image (which will not be permanently stored  and will be deleted after `PicUrlExpireTime`). |
| PicUrlExpireTime | String | Expiration time of a suspected image URL in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## MediaImageSpriteItem

Image sprite information

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Image sprite specification. For more information, please see [Image Sprite Parameter Template](https://intl.cloud.tencent.com/document/product/266/33480?from_cn_redirect=1#.E9.9B.AA.E7.A2.A7.E5.9B.BE.E6.A8.A1.E6.9D.BF). |
| Height | Integer | Subimage height of an image sprite. |
| Width | Integer | Subimage width of an image sprite. |
| TotalCount | Integer | Total number of subimages in each image sprite. |
| ImagePathSet | Array of String | Path to each image sprite. |
| WebVttPath | String | Path to a WebVtt file for the position-time relationship among subimages in an image sprite. The WebVtt file indicates the corresponding time points of each subimage and their coordinates in the image sprite, which is typically used by the player for implementing preview. |
| Storage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of an image sprite file. |

## MediaInputInfo

The information of the object to process.

Used by actions: BatchProcessMedia, CreateWorkflow, DescribeBatchTaskDetail, DescribeMediaMetaData, DescribeTaskDetail, EditMedia, ExtractBlindWatermark, ParseNotification, ProcessImage, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | Type of input source object. valid values:. COS: specifies the cos origin. URL: the url source. AWS-S3: aws source. currently only supports transcoding tasks. VOD: video-on-demand pro edition (VOD Pro). |
| CosInputInfo | [CosInputInfo](#CosInputInfo) | No | The information of the COS object to process. This parameter is valid and required when `Type` is `COS`. |
| UrlInputInfo | [UrlInputInfo](#UrlInputInfo) | No | The URL of the object to process. This parameter is valid and required when `Type` is `URL`. Note: This field may return null, indicating that no valid value can be obtained. |
| S3InputInfo | [S3InputInfo](#S3InputInfo) | No | The information of the AWS S3 object processed. This parameter is required if `Type` is `AWS-S3`. Note: This field may return null, indicating that no valid value can be obtained. |
| VODInputInfo | [VODInputInfo](#VODInputInfo) | No | The information of the VOD Pro object processed. This parameter is required if `Type` is `VOD`. Note: This field may return null, indicating that no valid value can be obtained. |

## MediaMetaData

Metadata of a VOD media file

Used by actions: DescribeBatchTaskDetail, DescribeMediaMetaData, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Size | Integer | Size of an uploaded media file in bytes (which is the sum of size of m3u8 and ts files if the video is in HLS format). Note: This field may return null, indicating that no valid values can be obtained. |
| Container | String | Container, such as m4a and mp4. Note: This field may return null, indicating that no valid values can be obtained. |
| Bitrate | Integer | Sum of the average bitrate of a video stream and that of an audio stream in bps. Note: This field may return null, indicating that no valid values can be obtained. |
| Height | Integer | Maximum value of the height of a video stream in px. Note: This field may return null, indicating that no valid values can be obtained. |
| Width | Integer | Maximum value of the width of a video stream in px. Note: This field may return null, indicating that no valid values can be obtained. |
| Duration | Float | Video duration in seconds. Note: This field may return null, indicating that no valid values can be obtained. |
| Rotate | Integer | Selected angle during video recording in degrees. Note: This field may return null, indicating that no valid values can be obtained. |
| VideoStreamSet | Array of [MediaVideoStreamItem](#MediaVideoStreamItem) | Video stream information. Note: This field may return null, indicating that no valid values can be obtained. |
| AudioStreamSet | Array of [MediaAudioStreamItem](#MediaAudioStreamItem) | Audio stream information. Note: This field may return null, indicating that no valid values can be obtained. |
| VideoDuration | Float | Video duration in seconds. Note: This field may return null, indicating that no valid values can be obtained. |
| AudioDuration | Float | Audio duration in seconds. Note: This field may return null, indicating that no valid values can be obtained. |

## MediaProcessTaskAdaptiveDynamicStreamingResult

Result type of adaptive bitrate streaming task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AdaptiveDynamicStreamingTaskInput](#AdaptiveDynamicStreamingTaskInput) | Input of an adaptive bitrate streaming task. |
| Output | [AdaptiveDynamicStreamingInfoItem](#AdaptiveDynamicStreamingInfoItem) | Output of an adaptive bitrate streaming task. Note: this field may return null, indicating that no valid values can be obtained. |

## MediaProcessTaskAnimatedGraphicResult

Result type of an animated image generating task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [AnimatedGraphicTaskInput](#AnimatedGraphicTaskInput) | Input for an animated image generating task. |
| Output | [MediaAnimatedGraphicsItem](#MediaAnimatedGraphicsItem) | Output of an animated image generating task. Note: This field may return null, indicating that no valid values can be obtained. |

## MediaProcessTaskImageSpriteResult

Result type of an image sprite generating task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://www.tencentcloud.com/document/api/1041/33691). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [ImageSpriteTaskInput](#ImageSpriteTaskInput) | Input for an image sprite generating task. |
| Output | [MediaImageSpriteItem](#MediaImageSpriteItem) | Output of the image sprite task for videos. Note: This field may return null, indicating that no valid value can be obtained. |
| BeginProcessTime | String | Task execution start time in ISO date and time format. |
| FinishTime | String | Task execution completion time in ISO date and time format. |

## MediaProcessTaskInput

The type of media processing task.

Used by actions: CreateWorkflow, DescribeWorkflows, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| TranscodeTaskSet | Array of [TranscodeTaskInput](#TranscodeTaskInput) | No | List of transcoding tasks. |
| AnimatedGraphicTaskSet | Array of [AnimatedGraphicTaskInput](#AnimatedGraphicTaskInput) | No | List of animated image screenshot tasks. |
| SnapshotByTimeOffsetTaskSet | Array of [SnapshotByTimeOffsetTaskInput](#SnapshotByTimeOffsetTaskInput) | No | List of time point screenshot tasks. |
| SampleSnapshotTaskSet | Array of [SampleSnapshotTaskInput](#SampleSnapshotTaskInput) | No | List of sampled screenshot tasks. |
| ImageSpriteTaskSet | Array of [ImageSpriteTaskInput](#ImageSpriteTaskInput) | No | List of image sprite screenshot tasks. |
| AdaptiveDynamicStreamingTaskSet | Array of [AdaptiveDynamicStreamingTaskInput](#AdaptiveDynamicStreamingTaskInput) | No | List of adaptive bitrate streaming tasks. |

## MediaProcessTaskResult

Query result type of a task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | Task type. Valid values: Transcode: TranscodingAnimatedGraphics: Animated image generatingSnapshotByTimeOffset: Time point screenshotSampleSnapshot: Sampled screenshotImageSprites: Image sprite screenshotCoverBySnapshot: Screenshot for cover imageAdaptiveDynamicStreaming: Adaptive bitrate streaming |
| TranscodeTask | [MediaProcessTaskTranscodeResult](#MediaProcessTaskTranscodeResult) | Query result of a transcoding task, which is valid when task type is `Transcode`. Note: This field may return null, indicating that no valid values can be obtained. |
| AnimatedGraphicTask | [MediaProcessTaskAnimatedGraphicResult](#MediaProcessTaskAnimatedGraphicResult) | Query result of an animated image generating task, which is valid when task type is `AnimatedGraphics`. Note: This field may return null, indicating that no valid values can be obtained. |
| SnapshotByTimeOffsetTask | [MediaProcessTaskSnapshotByTimeOffsetResult](#MediaProcessTaskSnapshotByTimeOffsetResult) | Query result of a time point screenshot task, which is valid when task type is `SnapshotByTimeOffset`. Note: This field may return null, indicating that no valid values can be obtained. |
| SampleSnapshotTask | [MediaProcessTaskSampleSnapshotResult](#MediaProcessTaskSampleSnapshotResult) | Query result of a sampled screenshot task, which is valid when task type is `SampleSnapshot`. Note: This field may return null, indicating that no valid values can be obtained. |
| ImageSpriteTask | [MediaProcessTaskImageSpriteResult](#MediaProcessTaskImageSpriteResult) | Query result of an image sprite screenshot task, which is valid when task type is `ImageSprite`. Note: This field may return null, indicating that no valid values can be obtained. |
| AdaptiveDynamicStreamingTask | [MediaProcessTaskAdaptiveDynamicStreamingResult](#MediaProcessTaskAdaptiveDynamicStreamingResult) | Query result of an adaptive bitrate streaming task, which is valid if the task type is `AdaptiveDynamicStreaming`. Note: this field may return null, indicating that no valid values can be obtained. |

## MediaProcessTaskSampleSnapshotResult

Result type of a sampled screenshot task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. Note: This field may return null, indicating that no valid values can be obtained. |
| Input | [SampleSnapshotTaskInput](#SampleSnapshotTaskInput) | Input for a sampled screenshot task. |
| Output | [MediaSampleSnapshotItem](#MediaSampleSnapshotItem) | Output of the sampled screenshot task for videos. Note: This field may return null, indicating that no valid value can be obtained. |
| BeginProcessTime | String | Task execution start time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |
| FinishTime | String | Task execution completion time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |

## MediaProcessTaskSnapshotByTimeOffsetResult

Result type of a time point screenshot task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [SnapshotByTimeOffsetTaskInput](#SnapshotByTimeOffsetTaskInput) | Input for a time point screenshot task. |
| Output | [MediaSnapshotByTimeOffsetItem](#MediaSnapshotByTimeOffsetItem) | Output of the time point screenshot task for videos. Note: This field may return null, indicating that no valid value can be obtained. |
| BeginProcessTime | String | Task execution start time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |
| FinishTime | String | Task execution completion time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |

## MediaProcessTaskTranscodeResult

Result type of a transcoding task

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | Error code. 0 indicates the task is successful; otherwise it is failed. This parameter is no longer recommended. Consider using the new error code parameter ErrCodeExt. |
| Message | String | Error message. |
| Input | [TranscodeTaskInput](#TranscodeTaskInput) | Input for a transcoding task. |
| Output | [MediaTranscodeItem](#MediaTranscodeItem) | Output of a transcoding task. Note: This field may return null, indicating that no valid values can be obtained. |
| Progress | Integer | Transcoding progress, with a value range of [0-100]. |

## MediaSampleSnapshotItem

Information of a sampled screenshot

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Sampled screenshot specification ID. For more information, please see [Sampled Screenshot Parameter Template](https://intl.cloud.tencent.com/document/product/266/33480?from_cn_redirect=1#.E9.87.87.E6.A0.B7.E6.88.AA.E5.9B.BE.E6.A8.A1.E6.9D.BF). |
| SampleType | String | Sample type. Valid values: Percent: Samples at the specified percentage interval.Time: Samples at the specified time interval. |
| Interval | Integer | Sampling interval If `SampleType` is `Percent`, this value means taking a screenshot at an interval of the specified percentage.If `SampleType` is `Time`, this value means taking a screenshot at an interval of the specified time (in seconds). The first screenshot is always the first video frame. |
| Storage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of a generated screenshot file. |
| ImagePathSet | Array of String | List of paths to generated screenshots. |
| WaterMarkDefinition | Array of Integer | List of watermarking template IDs if the screenshots are watermarked. |

## MediaSnapshotByTimeOffsetItem

Information of the time point screenshots in a VOD file

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Specification of a time point screenshot template. |
| PicInfoSet | Array of [MediaSnapshotByTimePicInfoItem](#MediaSnapshotByTimePicInfoItem) | Information set of screenshots of the same specification. Each element represents a screenshot. |
| Storage | [TaskOutputStorage](#TaskOutputStorage) | Location of a time point screenshot file. |

## MediaSnapshotByTimePicInfoItem

Information of a time point screenshot

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| TimeOffset | Float | The timestamp (seconds) of the screenshot. |
| Path | String | Path to the screenshot. |
| WaterMarkDefinition | Array of Integer | List of watermarking template IDs if the screenshots are watermarked. |

## MediaTranscodeItem

Transcoding information

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Target bucket of an output file. |
| Path | String | Path to an output video file. |
| Definition | Integer | Transcoding specification ID. For more information, please see [Transcoding Parameter Template](https://intl.cloud.tencent.com/document/product/266/33478?from_cn_redirect=1#.E8.BD.AC.E7.A0.81.E6.A8.A1.E6.9D.BF). |
| Bitrate | Integer | Sum of the average bitrate of a video stream and that of an audio stream in bps. |
| Height | Integer | Maximum value of the height of a video stream in px. |
| Width | Integer | Maximum value of the width of a video stream in px. |
| Size | Integer | Total size of a media file in bytes (which is the sum of size of m3u8 and ts files if the video is in HLS format). |
| Duration | Float | Video duration in seconds. |
| Container | String | Container, such as m4a and mp4. |
| Md5 | String | MD5 value of a video. |
| AudioStreamSet | Array of [MediaAudioStreamItem](#MediaAudioStreamItem) | Audio stream information. Note: This field may return null, indicating that no valid values can be obtained. |
| VideoStreamSet | Array of [MediaVideoStreamItem](#MediaVideoStreamItem) | Video stream information. Note: This field may return null, indicating that no valid values can be obtained. |
| CallBackExtInfo | String | Enhancement items used for video transcoding. Descriptions of enhancement items: hdr: HDR configurationwd_fps: configuration of frame interpolation for higher frame ratevideo_super_resolution:     super-resolution configurationrepair: comprehensive enhancement configurationdenoise: video denoising configuration color_enhance: color enhancement configuration scratch: scratch removal configurationartifact: artifact (glitch) removal configurationsharp: detail enhancement configuration low_light: low-light enhancement configuration face_enhance: face enhancement configuration Note: This field may return null, indicating that no valid value can be obtained. |

## MediaVideoStreamItem

Information of the video stream in a VOD file

Used by actions: DescribeBatchTaskDetail, DescribeMediaMetaData, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Bitrate | Integer | Bitrate of a video stream in bps. Note: This field may return null, indicating that no valid values can be obtained. |
| Height | Integer | Height of a video stream in px. Note: This field may return null, indicating that no valid values can be obtained. |
| Width | Integer | Width of a video stream in px. Note: This field may return null, indicating that no valid values can be obtained. |
| Codec | String | Video stream codec, such as h264. Note: This field may return null, indicating that no valid values can be obtained. |
| Fps | Integer | Frame rate in Hz. Note: This field may return null, indicating that no valid values can be obtained. |
| ColorPrimaries | String | Color primaries Note: this field may return `null`, indicating that no valid value was found. |
| ColorSpace | String | Color space Note: this field may return `null`, indicating that no valid value was found. |
| ColorTransfer | String | Color transfer Note: this field may return `null`, indicating that no valid value was found. |
| HdrType | String | HDR type Note: This field may return `null`, indicating that no valid value was found. |
| Codecs | String |  |
| FpsNumerator | Integer | Numerator of the frame rate. Note: This field may return null, indicating that no valid values can be obtained. |
| FpsDenominator | Integer | Denominator of the frame rate. Note: This field may return null, indicating that no valid values can be obtained. |

## MosaicInput

The mosaic effect parameters to use in a media processing task.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| CoordinateOrigin | String | No | Origin position, which currently can only be: TopLeft: the origin of coordinates is in the top-left corner of the video, and the origin of the blur is in the top-left corner of the image or text. Default value: TopLeft. |
| XPos | String | No | The horizontal position of the origin of the blur relative to the origin of coordinates of the video. % and px formats are supported: If the string ends in %, the `XPos` of the blur will be the specified percentage of the video width; for example, `10%` means that `XPos` is 10% of the video width;If the string ends in px, the `XPos` of the blur will be the specified px; for example, `100px` means that `XPos` is 100 px. Default value: 0 px. |
| YPos | String | No | Vertical position of the origin of blur relative to the origin of coordinates of video. % and px formats are supported: If the string ends in %, the `YPos` of the blur will be the specified percentage of the video height; for example, `10%` means that `YPos` is 10% of the video height;If the string ends in px, the `YPos` of the blur will be the specified px; for example, `100px` means that `YPos` is 100 px. Default value: 0 px. |
| Width | String | No | Blur width. % and px formats are supported: If the string ends in %, the `Width` of the blur will be the specified percentage of the video width; for example, `10%` means that `Width` is 10% of the video width;If the string ends in px, the `Width` of the blur will be in px; for example, `100px` means that `Width` is 100 px. Default value: 10%. |
| Height | String | No | Blur height. % and px formats are supported: If the string ends in %, the `Height` of the blur will be the specified percentage of the video height; for example, `10%` means that `Height` is 10% of the video height;If the string ends in px, the `Height` of the blur will be in px; for example, `100px` means that `Height` is 100 px. Default value: 10%. |
| StartTimeOffset | Float | No | Start time offset of blur in seconds. If this parameter is left empty or 0 is entered, the blur will appear upon the first video frame. If this parameter is left empty or 0 is entered, the blur will appear upon the first video frame;If this value is greater than 0 (e.g., n), the blur will appear at second n after the first video frame;If this value is smaller than 0 (e.g., -n), the blur will appear at second n before the last video frame. |
| EndTimeOffset | Float | No | End time offset of blur in seconds. If this parameter is left empty or 0 is entered, the blur will exist till the last video frame;If this value is greater than 0 (e.g., n), the blur will exist till second n;If this value is smaller than 0 (e.g., -n), the blur will exist till second n before the last video frame. |

## NumberFormat

Rule of the `{number}` variable in the output file name.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| InitialValue | Integer | No | Start value of the `{number}` variable. Default value: 0. |
| Increment | Integer | No | Increment of the `{number}` variable. Default value: 1. |
| MinLength | Integer | No | Minimum length of the `{number}` variable. A placeholder will be used if the variable length is below the minimum requirement. Default value: 1. |
| PlaceHolder | String | No | Placeholder used when the `{number}` variable length is below the minimum requirement. Default value: 0. |

## OcrFullTextConfigureInfo

Control parameter of a full text recognition task

Used by actions: CreateAIRecognitionTemplate, DescribeAIRecognitionTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a full text recognition task. Valid values: ON: Enables an intelligent full text recognition task;OFF: Disables an intelligent full text recognition task. |

## OcrFullTextConfigureInfoForUpdate

Control parameter of a full text recognition task

Used by actions: ModifyAIRecognitionTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a full text recognition task. Valid values: ON: Enables an intelligent full text recognition task;OFF: Disables an intelligent full text recognition task. |

## OcrWordsConfigureInfo

Text keyword recognition control parameter.

Used by actions: CreateAIRecognitionTemplate, DescribeAIRecognitionTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a text keyword recognition task. Valid values: ON: Enables a text keyword recognition task;OFF: Disables a text keyword recognition task. |
| LabelSet | Array of String | No | Keyword filter tag, which specifies the keyword tag that needs to be returned. If this parameter is left empty, all results will be returned. There can be up to 10 tags, each with a length limit of 16 characters. |

## OcrWordsConfigureInfoForUpdate

Text keyword recognition control parameter.

Used by actions: ModifyAIRecognitionTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a text keyword recognition task. Valid values: ON: Enables a text keyword recognition task;OFF: Disables a text keyword recognition task. |
| LabelSet | Array of String | No | Keyword filter tag, which specifies the keyword tag that needs to be returned. If this parameter is left empty, all results will be returned. There can be up to 10 tags, each with a length limit of 16 characters. |

## OverrideEraseParameter

Custom parameters for smart erasing.

Used by actions: ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| EraseType | String | No | Erasing type. -subtitle: subtitle removal. -watermark: watermark removal. -privacy: privacy protection. |
| EraseSubtitleConfig | [UpdateSmartEraseSubtitleConfig](#UpdateSmartEraseSubtitleConfig) | No | Subtitle erasing configuration. This field is required when the value of EraseType is subtitle. |
| EraseWatermarkConfig | [UpdateSmartEraseWatermarkConfig](#UpdateSmartEraseWatermarkConfig) | No | Watermark erasing configuration. This field is required when the value of EraseType is watermark. |
| ErasePrivacyConfig | [UpdateSmartErasePrivacyConfig](#UpdateSmartErasePrivacyConfig) | No | Privacy protection configuration. This field is required when the value of EraseType is privacy. |

## OverrideTranscodeParameter

Custom specification parameters for video processing, which are used to override corresponding parameters in templates.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Container | String | No | Container format. Valid values: mp4, flv, hls, mp3, flac, ogg, and m4a; mp3, flac, ogg, and m4a are formats of audio files. |
| RemoveVideo | Integer | No | Whether to remove video data. Valid values: 0: retain1: remove |
| RemoveAudio | Integer | No | Whether to remove audio data. Valid values: 0: retain1: remove |
| VideoTemplate | [VideoTemplateInfoForUpdate](#VideoTemplateInfoForUpdate) | No | Video stream configuration parameter. |
| AudioTemplate | [AudioTemplateInfoForUpdate](#AudioTemplateInfoForUpdate) | No | Audio stream configuration parameter. |
| TEHDConfig | [TEHDConfigForUpdate](#TEHDConfigForUpdate) | No | The TSC transcoding parameters. Note: This field may return null, indicating that no valid values can be obtained. |
| SubtitleTemplate | [SubtitleTemplate](#SubtitleTemplate) | No | Subtitle stream configuration parameter. |
| AddonAudioStream | Array of [MediaInputInfo](#MediaInputInfo) | No | Specifies the external audio track parameter. |
| StdExtInfo | String | No | Extension field for transcoding. |
| AddOnSubtitles | Array of [AddOnSubtitle](#AddOnSubtitle) | No | Subtitle file to be inserted. |

## PoliticalAsrReviewTemplateInfo

The parameters for detecting sensitive information based on ASR.

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Whether to detect sensitive information based on ASR. Valid values: ONOFF |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0-100. |

## PoliticalAsrReviewTemplateInfoForUpdate

The parameters for detecting sensitive information based on ASR.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to detect sensitive information based on ASR. Valid values: ONOFF |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## PoliticalConfigureInfo

The parameters for detecting sensitive information.

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImgReviewInfo | [PoliticalImgReviewTemplateInfo](#PoliticalImgReviewTemplateInfo) | No | The parameters for detecting sensitive information in images. |
| AsrReviewInfo | [PoliticalAsrReviewTemplateInfo](#PoliticalAsrReviewTemplateInfo) | No | The parameters for detecting sensitive information based on ASR. |
| OcrReviewInfo | [PoliticalOcrReviewTemplateInfo](#PoliticalOcrReviewTemplateInfo) | No | The parameters for detecting sensitive information based on OCR. |

## PoliticalConfigureInfoForUpdate

The parameters for detecting sensitive information.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImgReviewInfo | [PoliticalImgReviewTemplateInfoForUpdate](#PoliticalImgReviewTemplateInfoForUpdate) | No | The parameters for detecting sensitive information in images. |
| AsrReviewInfo | [PoliticalAsrReviewTemplateInfoForUpdate](#PoliticalAsrReviewTemplateInfoForUpdate) | No | The parameters for detecting sensitive information based on ASR. |
| OcrReviewInfo | [PoliticalOcrReviewTemplateInfoForUpdate](#PoliticalOcrReviewTemplateInfoForUpdate) | No | The parameters for detecting sensitive information based on OCR. |

## PoliticalImgReviewTemplateInfo

The parameters for detecting sensitive information in images.

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Whether to detect sensitive information in images. Valid values: ONOFF |
| LabelSet | Array of String | No | The filter labels for sensitive information detection in images, which specify the types of sensitive information to return. If this parameter is left empty, the detection results for all labels are returned. Valid values: violation_photo (banned icons)politicianentertainment (people in the entertainment industry)sport (people in the sports industry)entrepreneurscholarcelebritymilitary (people in military) |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 97 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 95 will be used by default. Value range: 0-100. |

## PoliticalImgReviewTemplateInfoForUpdate

The parameters for detecting sensitive information in images.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to detect sensitive information in images. Valid values: ONOFF |
| LabelSet | Array of String | No | The filter labels for sensitive information detection in images, which specify the types of sensitive information to return. If this parameter is left empty, the detection results for all labels are returned. Valid values: violation_photo (banned icons)politicianentertainment (people in the entertainment industry)sport (people in the sports industry)entrepreneurscholarcelebritymilitary (people in military) |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## PoliticalOcrReviewTemplateInfo

The parameters for detecting sensitive information based on OCR.

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Whether to detect sensitive information based on OCR. Valid values: ONOFF |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0-100. |

## PoliticalOcrReviewTemplateInfoForUpdate

The parameters for detecting sensitive information based on OCR.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to detect sensitive information based on OCR. Valid values: ONOFF |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## PornAsrReviewTemplateInfo

Control parameter of a porn information detection in speech task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a porn information detection in speech task. Valid values: ON: Enables a porn information detection in speech task;OFF: Disables a porn information detection in speech task. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0-100. |

## PornAsrReviewTemplateInfoForUpdate

Control parameter of a porn information detection in speech task.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a porn information detection in speech task. Valid values: ON: Enables a porn information detection in speech task;OFF: Disables a porn information detection in speech task. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## PornConfigureInfo

Control parameter of a porn information detection task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImgReviewInfo | [PornImgReviewTemplateInfo](#PornImgReviewTemplateInfo) | No | Control parameter of porn information detection in image. Note: This field may return null, indicating that no valid values can be obtained. |
| AsrReviewInfo | [PornAsrReviewTemplateInfo](#PornAsrReviewTemplateInfo) | No | Control parameter of porn information detection in speech. Note: This field may return null, indicating that no valid values can be obtained. |
| OcrReviewInfo | [PornOcrReviewTemplateInfo](#PornOcrReviewTemplateInfo) | No | Control parameter of porn information detection in text. Note: This field may return null, indicating that no valid values can be obtained. |

## PornConfigureInfoForUpdate

Control parameter of a porn information detection task.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImgReviewInfo | [PornImgReviewTemplateInfoForUpdate](#PornImgReviewTemplateInfoForUpdate) | No | Control parameter of porn information detection in image. |
| AsrReviewInfo | [PornAsrReviewTemplateInfoForUpdate](#PornAsrReviewTemplateInfoForUpdate) | No | Control parameter of porn information detection in speech. |
| OcrReviewInfo | [PornOcrReviewTemplateInfoForUpdate](#PornOcrReviewTemplateInfoForUpdate) | No | Control parameter of porn information detection in text. |

## PornImgReviewTemplateInfo

Control parameter of a porn information detection in image task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a porn information detection in image task. Valid values: ON: Enables a porn information detection in image task;OFF: Disables a porn information detection in image task. |
| LabelSet | Array of String | No | Filter tag for porn information detection in image. If an audit result contains the selected tag, it will be returned; if the filter tag is empty, all audit results will be returned. Valid values: porn: Porn;vulgar: Vulgarity;intimacy: Intimacy;sexy: Sexiness. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 90 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 0 will be used by default. Value range: 0-100. |

## PornImgReviewTemplateInfoForUpdate

Control parameter of a porn information detection in image task.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a porn information detection in image task. Valid values: ON: Enables a porn information detection in image task;OFF: Disables a porn information detection in image task. |
| LabelSet | Array of String | No | Filter tag for porn information detection in image. If an audit result contains the selected tag, it will be returned; if the filter tag is empty, all audit results will be returned. Valid values: porn: Porn;vulgar: Vulgarity;intimacy: Intimacy;sexy: Sexiness. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## PornOcrReviewTemplateInfo

Control parameter of a porn information detection in text task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a porn information detection in text task. Valid values: ON: Enables a porn information detection in text task;OFF: Disables a porn information detection in text task. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0-100. |

## PornOcrReviewTemplateInfoForUpdate

Control parameter of a porn information detection in text task.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a porn information detection in text task. Valid values: ON: Enables a porn information detection in text task;OFF: Disables a porn information detection in text task. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## ProcessImageTemplate

Image processing template.

Used by actions: DescribeProcessImageTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique identifier of the image processing template. |
| Name | String | Image processing template name. |
| Comment | String | Description information of the image processing template. |
| Type | String | Template type. |
| ProcessImageConfig | [ImageTaskInput](#ImageTaskInput) | Image processing template configuration parameter. |
| CreateTime | String | Template creation time. |
| UpdateTime | String | Last modification time of the template. |

## ProhibitedAsrReviewTemplateInfo

Control parameter of prohibited information detection in speech task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of prohibited information detection in speech task. Valid values: ON: enables prohibited information detection in speech task;OFF: disables prohibited information detection in speech task. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0–100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0–100. |

## ProhibitedAsrReviewTemplateInfoForUpdate

Control parameter of prohibited information detection in speech task

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of prohibited information detection in speech task. Valid values: ON: enables prohibited information detection in speech task;OFF: disables prohibited information detection in speech task. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0–100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0–100. |

## ProhibitedConfigureInfo

Control parameter of prohibited information detection task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| AsrReviewInfo | [ProhibitedAsrReviewTemplateInfo](#ProhibitedAsrReviewTemplateInfo) | No | Control parameter of prohibited information detection in speech. |
| OcrReviewInfo | [ProhibitedOcrReviewTemplateInfo](#ProhibitedOcrReviewTemplateInfo) | No | Control parameter of prohibited information detection in text. |

## ProhibitedConfigureInfoForUpdate

Control parameter of prohibited information detection task

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| AsrReviewInfo | [ProhibitedAsrReviewTemplateInfoForUpdate](#ProhibitedAsrReviewTemplateInfoForUpdate) | No | Control parameter of prohibited information detection in speech. |
| OcrReviewInfo | [ProhibitedOcrReviewTemplateInfoForUpdate](#ProhibitedOcrReviewTemplateInfoForUpdate) | No | Control parameter of prohibited information detection in text. |

## ProhibitedOcrReviewTemplateInfo

Control parameter of prohibited information detection in text task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of prohibited information detection in text task. Valid values: ON: enables prohibited information detection in text task;OFF: disables prohibited information detection in text task. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0–100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0–100. |

## ProhibitedOcrReviewTemplateInfoForUpdate

Control parameter of prohibited information detection in text task

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of prohibited information detection in text task. Valid values: ON: enables prohibited information detection in text task;OFF: disables prohibited information detection in text task. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0–100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0–100. |

## PureSubtitleTransResult

Translation result of pure subtitle files.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status (the three valid values are as follows): - PROCESSING - SUCCESS  - FAIL |
| ErrCodeExt | String | Error code. A null string indicates that the task is successful, while other values indicate that the task has failed. For valid values, see the list of Media Processing Service (MPS) error codes. |
| ErrCode | Integer | Error code. 0 indicates that the task is successful, and other values indicate that the task has failed. (This field is not recommended. Use the new error code field ErrCodeExt instead.) |
| Message | String | Error message |
| Input | [SmartSubtitleTaskResultInput](#SmartSubtitleTaskResultInput) | Translation task input information. |
| Output | [PureSubtitleTransResultOutput](#PureSubtitleTransResultOutput) | Translation output result of pure subtitle files. Note: This field may return null, indicating that no valid values can be obtained. |
| Progress | Integer | Task progress. |

## PureSubtitleTransResultOutput

Detailed output result of translation.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of the subtitle file. Note: This field may return null, indicating that no valid values can be obtained. |
| SubtitleResults | Array of [SubtitleTransResultItem](#SubtitleTransResultItem) | Result set of multilingual translation. |

## QualityControlData

Media quality inspection result output.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| NoAudio | Boolean | When this field is set to true, it indicates that the video has no audio track. |
| NoVideo | Boolean | When this field is set to true, it indicates that the video has no video track. |
| QualityEvaluationScore | Integer | No-reference quality score of the video (100 points in total). |
| QualityEvaluationMeanOpinionScore | Float | No-reference quality score of the video (MOS). |
| QualityControlResultSet | Array of [QualityControlResult](#QualityControlResult) | Exception items identified in content quality inspection. |
| ContainerDiagnoseResultSet | Array of [ContainerDiagnoseResultItem](#ContainerDiagnoseResultItem) | Exception items identified in format diagnosis. |

## QualityControlItem

The information of a checked segment in quality control.

Used by actions: ParseLiveStreamProcessNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Integer | The confidence score. Value range: 0-100. Note: This field may return null, indicating that no valid values can be obtained. |
| StartTimeOffset | Float | The start timestamp (second) of the segment. |
| EndTimeOffset | Float | The end timestamp (second) of the segment. |
| AreaCoordSet | Array of Integer | The coordinates (px) of the top left and bottom right corner. Note: This field may return null, indicating that no valid values can be obtained. |

## QualityControlItemConfig

Quality inspection item configurations.

Used by actions: CreateQualityControlTemplate, DescribeQualityControlTemplates, ModifyQualityControlTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | Quality inspection item name. valid values:. LowEvaluation: specifies the no-reference MOS score of the video.. AudioEvaluation: specifies the no-reference MOS score of the audio.. Mosaic: mosaic detection.. CrashScreen: specifies screen glitch detection.. Blur: specifies blur detection.. Jitter: jitter detection.. Noise: noise detection.. QRCode: qr code detection.. BarCode: specifies barcode detection.. AppletCode: specifies mini program code detection.. BlackWhiteEdge: specifies black and white edge detection.. SolidColorScreen: specifies solid color screen detection.. LowLighting: specifies low light.. HighLighting: overexposure.. NoVoice: specifies silence detection.. LowVoice: specifies bass detection.. HighVoice: explosion noise detection.. AudioNoise: specifies audio noise detection.. VideoResolutionChanged: specifies the video resolution change.. AudioSampleRateChanged: specifies the audio sample rate change.. AudioChannelsChanged: indicates the audio channel quantity change.. ParameterSetsChanged: indicates the stream parameter set information has changed.. DarOrSarInvalid: indicates an abnormal video aspect ratio.. TimestampFallback: specifies DTS timestamp rollback.. DtsJitter: specifies excessive DTS jitter.. PtsJitter: indicates excessive PTS jitter.. AACDurationDeviation: specifies an improper aac frame timestamp interval.. AudioDroppingFrames: indicates audio frame dropping.. VideoDroppingFrames: specifies video frame dropping.. AVTimestampInterleave: improper audio-video interleaving.. PtsLessThanDts: specifies that the pts of the media stream is less than the dts.. ReceiveFpsJitter: specifies excessive jitter in the network received frame rate.. ReceiveFpsTooSmall: indicates the network received video frame rate is too low.. FpsJitter: specifies excessive jitter in the stream frame rate calculated via PTS.. StreamOpenFailed: indicates the stream open failure.. StreamEnd: specifies the stream end.. StreamParseFailed: specifies the stream parsing failure.. VideoFirstFrameNotIdr: first frame not an IDR frame.. StreamNALUError: indicates an nalu start code error.. TsStreamNoAud: specifies whether the mpegts H26x stream misses AUD NALU.. AudioStreamLack: no audio stream.. VideoStreamLack: no video stream.. LackAudioRecover: specifies missing audio stream recovery.. LackVideoRecover: missing video stream recovery.. VideoBitrateOutofRange: video stream bitrate (kbps) out of range.. AudioBitrateOutofRange: audio stream bitrate (kbps) out of range.. VideoDecodeFailed: indicates a video decoding error.. AudioDecodeFailed: audio decoding error.. AudioOutOfPhase: specifies opposite phase in dual-channel audio.. VideoDuplicatedFrame: indicates duplicate frames in video streams.. AudioDuplicatedFrame: indicates duplicate frames in audio streams.. VideoRotation: specifies video rotation.. TsMultiPrograms: specifies multiple programs in MPEG2-TS streams.. Mp4InvalidCodecFourcc: specifies the codec fourcc in Mp4 does not meet Apple HLS requirements.. HLSBadM3u8Format: invalid m3u8 file.. HLSInvalidMasterM3u8: invalid main m3u8 file.. HLSInvalidMediaM3u8: invalid media m3u8 file.. HLSMasterM3u8Recommended: parameters recommended by standards missing in main m3u8.. HLSMediaM3u8Recommended: parameters recommended by standards missing in media m3u8.. HLSMediaM3u8DiscontinuityExist: indicates the existence of EXT-X-DISCONTINUITY in media m3u8.. HLSMediaSegmentsStreamNumChange: indicates the number of streams in segments changes.. HLSMediaSegmentsPTSJitterDeviation: indicates PTS jumps between segments without EXT-X-DISCONTINUITY.. HLSMediaSegmentsDTSJitterDeviation: indicates DTS jumps between segments without EXT-X-DISCONTINUITY.. TimecodeTrackExist: TMCD track in MP4. |
| Switch | String | No | Capability configuration switch. Valid values: ON: enabled;OFF: disabled.  Default value: ON.  Note: This field may return null, indicating that no valid values can be obtained. |
| Sampling | String | No | Sampling method, Valid value: - Time: sampling based on time interval. Note: This field may return null, indicating that no valid values can be obtained. |
| IntervalTime | Integer | No | Sampling interval time, in ms. Note: This field may return null, indicating that no valid values can be obtained. |
| Duration | Integer | No | Duration of abnormality, in ms. Note: This field may return null, indicating that no valid values can be obtained. |
| Threshold | String | No | Threshold of a detection item. Different detection items have different thresholds. Note: This field may return null, indicating that no valid values can be obtained. |

## QualityControlResult

The issues detected by quality control.

Used by actions: DescribeTaskDetail, ParseLiveStreamProcessNotification, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | Exception type. valid values:. Jitter: jitter. Blur: specifies the blur effect. LowLighting: specifies low light. HighLighting: overexposure. CrashScreen: specifies screen glitch. BlackWhiteEdge: specifies the black and white edges. SolidColorScreen: specifies the solid color screen. Noise: specifies the noise. Mosaic: mosaic. QRCode: specifies the qr code. AppletCode: specifies the mini program code. BarCode: specifies the barcode. LowVoice: specifies the bass. HighVoice: specifies high voice detection. NoVoice: specifies mute. LowEvaluation: specifies the video no-reference score (MOS) is below the threshold. AudioEvaluation: specifies the audio no-reference scoring (MOS) is below the threshold. AudioNoise: specifies the audio noise. |
| QualityControlItems | Array of [QualityControlItem](#QualityControlItem) | The information of a checked segment in quality control. |

## QualityControlStrategy

Detection policy for media quality inspection.

Used by actions: CreateQualityControlTemplate, DescribeQualityControlTemplates, ModifyQualityControlTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| StrategyType | String | No | Policy type. Valid values: - TimeSpotCheck |
| TimeSpotCheck | [TimeSpotCheck](#TimeSpotCheck) | No | Spot check policy based on time. |

## QualityControlTemplate

Media quality inspection template details.

Used by actions: DescribeQualityControlTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique identifier of a media quality inspection template. |
| Name | String | Media quality inspection template name. Note: This field may return null, indicating that no valid values can be obtained. |
| Comment | String | Template description.   Note: This field may return null, indicating that no valid values can be obtained. |
| Type | String | Template type. Valid values: Preset: system preset template;Custom: custom template.  Note: This field may return null, indicating that no valid values can be obtained. |
| QualityControlItemSet | Array of [QualityControlItemConfig](#QualityControlItemConfig) | Media quality inspection configuration parameters. Note: This field may return null, indicating that no valid values can be obtained. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F).  Note: This field may return null, indicating that no valid values can be obtained. |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F).  Note: This field may return null, indicating that no valid values can be obtained. |
| Strategy | [QualityControlStrategy](#QualityControlStrategy) | Spot check policy for media quality inspection. |

## RawImageWatermarkInput

Input parameter of image watermark template

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImageContent | [MediaInputInfo](#MediaInputInfo) | Yes | Input content of watermark image. JPEG and PNG images are supported. |
| Width | String | No | Watermark width. % and px formats are supported: If the string ends in %, the `Width` of the watermark will be the specified percentage of the video width; for example, `10%` means that `Width` is 10% of the video width;If the string ends in px, the `Width` of the watermark will be in px; for example, `100px` means that `Width` is 100 px. Default value: 10%. |
| Height | String | No | Watermark height. % and px formats are supported: If the string ends in %, the `Height` of the watermark will be the specified percentage of the video height; for example, `10%` means that `Height` is 10% of the video height;If the string ends in px, the `Height` of the watermark will be in px; for example, `100px` means that `Height` is 100 px. Default value: 0 px, which means that `Height` will be proportionally scaled according to the aspect ratio of the original watermark image. |
| RepeatType | String | No | Repeat type of an animated watermark. Valid values: `once`: no longer appears after watermark playback ends.`repeat_last_frame`: stays on the last frame after watermark playback ends.`repeat` (default): repeats the playback until the video ends. |

## RawSmartEraseParameter

Smart erasure custom parameter.

Used by actions: ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| EraseType | String | Yes | Specifies the removal type. -subtitle removal. -Remove watermark. -privacy protection. |
| EraseSubtitleConfig | [SmartEraseSubtitleConfig](#SmartEraseSubtitleConfig) | No | Subtitle erasure configuration. When EraseType is subtitle, this field is required. Note: This field may return null, indicating that no valid value can be obtained. |
| EraseWatermarkConfig | [SmartEraseWatermarkConfig](#SmartEraseWatermarkConfig) | No | Specifies the watermark removal configuration. When EraseType is watermark, this field is required. Note: This field may return null, indicating that no valid value can be obtained. |
| ErasePrivacyConfig | [SmartErasePrivacyConfig](#SmartErasePrivacyConfig) | No | Privacy protection configuration. When EraseType is privacy, this field is required. Note: This field may return null, indicating that no valid value can be obtained. |

## RawSmartSubtitleParameter

Custom smart subtitle parameter.

Used by actions: BatchProcessMedia, DescribeBatchTaskDetail, ParseNotification, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SubtitleType | Integer | Yes | Smart subtitle language type. 0: source language 1: target language 2: source language + target language The value can only be 0 when TranslateSwitch is set to OFF. The value can only be 1 or 2 when TranslateSwitch is set to ON. |
| VideoSrcLanguage | String | Yes | Source language of the video with smart subtitles. OCR recognition only supports the following languages: `zh_en`: Chinese and English. `multi`: others. ASR recognition and pure subtitle translation currently support the following languages: `auto`: automatic recognition (it is only supported in pure subtitle translation). `zh`: Simplified Chinese. `en`: English. `ja`: Japanese. `ko`: Korean. `zh-PY`: Chinese, English, and Cantonese. `zh_medical`: Chinese (medical scenario). `vi`: Vietnamese. `ms`: Malay. `id`: Indonesian. `fil`: Filipino. `th`: Thai. `pt`: Portuguese. `tr`: Turkish. `ar`: Arabic. `es`: Spanish. `hi`: Hindi. `fr`: French. `de`: German. `it`: Italian. `zh_dialect`: Chinese dialect. `zh_en`: Chinese and English. `yue`: Cantonese. `ru`: Russian. `prime_zh`: Chinese, English, and Chinese dialects. `af-ZA`: Afrikaans (South Africa). `sq-AL`: Albanian (Albania). `am-ET`: Amharic (Ethiopia). `ar-DZ`: Arabic (Algeria). `ar-BH`: Arabic (Bahrain). `ar-EG`: Arabic (Egypt). `ar-IQ`: Arabic (Iraq). `ar-IL`: Arabic (Israel). `ar-JO`: Arabic (Jordan). `ar-KW`: Arabic (Kuwait). `ar-LB`: Arabic (Lebanon). `ar-MR`: Arabic (Mauritania). `ar-MA`: Arabic (Morocco). `ar-OM`: Arabic (Oman). `ar-QA`: Arabic (Qatar). `ar-SA`: Arabic (Saudi Arabia). `ar-PS`: Arabic (State of Palestine). `ar-SY`: Arabic (Syria). `ar-TN`: Arabic (Tunisia). `ar-AE`: Arabic (United Arab Emirates). `ar-YE`: Arabic (Yemen). `hy-AM`: Armenian (Armenia). `az-AZ`: Azerbaijani (Azerbaijan). `eu-ES`: Basque (Spain). `bn-BD`: Bengali (Bangladesh). `bn-IN`: Bengali (India). `bs-BA`: Bosnian (Bosnia and Herzegovina). `bg-BG`: Bulgarian (Bulgaria). `my-MM`: Burmese (Myanmar). `ca-ES`: Catalan (Spain). `hr-HR`: Croatian (Croatia). `cs-CZ`: Czech (Czech Republic). `da-DK`: Danish (Denmark). `nl-BE`: Dutch (Belgium). `nl-NL`: Dutch (Holland). `en-AU`: English (Australia). `en-CA`: English (Canada). `en-GH`: English (Ghana). `en-HK`: English (Hong Kong (China)). `en-IN`: English (India). `en-IE`: English (Ireland). `en-KE`: English (Kenya). `en-NZ`: English (New Zealand). `en-NG`: English (Nigeria). `en-PK`: English (Pakistan). `en-PH`: English (Philippines). `en-SG`: English (Singapore). `en-ZA`: English (South Africa). `en-TZ`: English (Tanzania). `en-GB`: English (UK). `en-US`: English (US). `et-EE`: Estonian (Estonia). `fil-PH`: Filipino (Philippines). `fi-FI`: Finnish (Finland). `fr-BE`: French (Belgium). `fr-CA`: French (Canada). `fr-FR`: French (France). `fr-CH`: French (Switzerland). `gl-ES`: Galician (Spain). `ka-GE`: Georgian (Georgia). `el-GR`: Greek (Greece). `gu-IN`: Gujarati (India). `iw-IL`: Hebrew (Israel). `hi-IN`: Hindi (India). `hu-HU`: Hungarian (Hungary). `is-IS`: Icelandic (Iceland). `id-ID`: Indonesian (Indonesia). `it-IT`: Italian (Italy). `it-CH`: Italian (Switzerland). `ja-JP`: Japanese (Japan). `jv-ID`: Javanese (Indonesia). `kn-IN`: Kannada (India). `kk-KZ`: Kazakh (Kazakhstan). `km-KH`: Khmer (Cambodia). `rw-RW`: Kinyarwanda (Rwanda). `ko-KR`: Korean (South Korea). `lo-LA`: Lao (Laos). `lv-LV`: Latvian (Latvia). `lt-LT`: Lithuanian (Lithuania). `mk-MK`: Macedonian (North Macedonia). `ms-MY`: Malay (Malaysia). `ml-IN`: Malayalam (India). `mr-IN`: Marathi (India). `mn-MN`: Mongolian (Mongolia). `ne-NP`: Nepali (Nepal). `no-NO`: Bokmål Norwegian (Norway). `fa-IR`: Persian (Iran). `pl-PL`: Polish (Poland). `pt-BR`: Portuguese (Brazil). `pt-PT`: Portuguese (Portugal). `ro-RO`: Romanian (Romania). `ru-RU`: Russian (Russia). `sr-RS`: Serbian (Serbia). `si-LK`: Sinhalese (Sri Lanka). `sk-SK`: Slovak (Slovakia). `sl-SI`: Slovenian (Slovenia). `st-ZA`: Sesotho (South Africa). `es-AR`: Spanish (Argentina). `es-BO`: Spanish (Bolivia). `es-CL`: Spanish (Chile). `es-CO`: Spanish (Colombia). `es-CR`: Spanish (Costa Rica). `es-DO`: Spanish (Dominican Republic). `es-EC`: Spanish (Ecuador). `es-SV`: Spanish (El Salvador). `es-GT`: Spanish (Guatemala). `es-HN`: Spanish (Honduras). `es-MX`: Spanish (Mexico). `es-NI`: Spanish (Nicaragua). `es-PA`: Spanish (Panama). `es-PY`: Spanish (Paraguay). `es-PE`: Spanish (Peru). `es-PR`: Spanish (Puerto Rico). `es-ES`: Spanish (Spain). `es-US`: Spanish (US). `es-UY`: Spanish (Uruguay). `es-VE`: Spanish (Venezuela). `su-ID`: Sundanese (Indonesia). `sw-KE`: Swahili (Kenya). `sw-TZ`: Swahili (Tanzania). `sv-SE`: Swedish (Sweden). `ta-IN`: Tamil (India). `ta-MY`: Tamil (Malaysia). `ta-SG`: Tamil (Singapore). `ta-LK`: Tamil (Sri Lanka). `te-IN`: Telugu (India). `th-TH`: Thai (Thailand). `ts-ZA`: Tsonga (South Africa). `tr-TR`: Turkish (Turkey). `uk-UA`: Ukrainian (Ukraine). `ur-IN`: Urdu (India). `ur-PK`: Urdu (Pakistan). `uz-UZ`: Uzbek (Uzbekistan). `ve-ZA`: Venda (South Africa). `vi-VN`: Vietnamese (Vietnam). `xh-ZA`: Xhosa (South Africa). `zu-ZA`: Zulu (South Africa). |
| SubtitleFormat | String | No | Smart subtitle file format: - Under the ASR recognition and translation processing type:      - vtt: WebVTT format subtitle.      - srt: SRT format subtitle.      - Unspecified or left blank: no subtitle file generated. - Under the pure subtitle translation processing type:     - original: consistent with the source file.     - vtt: WebVTT format subtitle.     - srt: SRT format subtitle. - Under the OCR recognition and translation processing type:      - vtt: WebVTT format subtitle.      - srt: SRT format subtitle. **Note**: - For ASR recognition mode, when 2 or more languages are involved in translation, this field cannot be unspecified or left blank. - For pure subtitle translation and OCR recognition mode, this field cannot be unspecified or left blank. Note: This field may return null, indicating that no valid values can be obtained. |
| TranslateSwitch | String | No | Subtitle translation switch. `ON`: translation enabled. `OFF`: translation disabled. **Note**: For pure subtitle translation mode, the default value is enabled if the field is unspecified. The field cannot be left blank or set to `OFF`. Note: This field may return null, indicating that no valid values can be obtained. |
| TranslateDstLanguage | String | No | Target language for subtitle translation. This parameter takes effect when the value of TranslateSwitch is ON. Valid translation languages:`ab`: Abkhazian.`ace`: Acehnese.`ach`: Acholi.`af`: Afrikaans.`ak`: Twi (Akan).`am`: Amharic.`ar`: Arabic.`as`: Assamese.`ay`: Aymara.`az`: Azerbaijani.`ba`: Bashkir.`ban`: Balinese.`bbc`: Batak toba.`bem`: Bemba.`bew`: Betawi.`bg`: Bulgarian.`bho`: Bhojpuri.`bik`: Bikol.`bm`: Bambara.`bn`: Bengali.`br`: Breton.`bs`: Bosnian.`btx`: Batak Karo.`bts`: Batak Simalungun.`bua`: Buryat.`ca`: Catalan.`ceb`: Cebuano.`cgg`: Kiga.`chm`: Meadow Mari.`ckb`: Kurdish (Sorani).`cnh`: Hakha Chin.`co`: Corsican.`crh`: Crimean Tatar.`crs`: Seychellois Creole.`cs`: Czech.`cv`: Chuvash.`cy`: Welsh.`da`: Danish.`de`: German.`din`: Dinka.`doi`: Dogri.`dov`: Dombe.`dv`: Dhivehi.`dz`: Dzongkha.`ee`: Ewe.`el`: Greek.`en`: English.`eo`: Esperanto.`es`: Spanish.`et`: Estonian.`eu`: Basque.`fa`: Persian.`ff`: Fulah.`fi`: Finnish.`fil`: Filipino (Tagalog).`fj`: Fijian.`fr`: French.`fr-CA`: French (Canada).`fr-FR`: French (France).`fy`: Frisian.`ga`: Irish.`gaa`: Ga. `gd`: Scottish Gaelic.`gl`: Galician.`gn`: Guarani.`gom`: Konkani.`gu`: Gujarati.`gv`: Manx.`ha`: Hausa.`haw`: Hawaiian.`he`: Hebrew.`hi`: Hindi.`hil`: Hiligaynon.`hmn`: Hmong.`hr`: Croatian.`hrx`: Hunsrik.`ht`: Haitian Creole.`hu`: Hungarian.`hy`: Armenian.`id`: Indonesian.`ig`: Igbo.`ilo`: Iloko.`is`: Icelandic.`it`: Italian.`iw`: Hebrew.`ja`: Japanese.`jv`: Javanese.`ka`: Georgian.`kk`: Kazakh.`km`: Khmer.`kn`: Kannada.`ko`: Korean.`kri`: Krio.`ku`: Kurdish (Kurmanji).`ktu`: Kituba.`ky`: Kyrgyz.`la`: Latin.`lb`: Luxembourgish.`lg`: Ganda (Luganda).`li`: Limburgish.`lij`: Ligurian.`lmo`: Lombard.`ln`: Lingala.`lo`: Lao.`lt`: Lithuanian.`ltg`: Latgalian.`luo`: Luo.`lus`: Mizo.`lv`: Latvian.`mai`: Maithili.`mak`: Makasar.`mg`: Malagasy.`mi`: Maori.`min`: Minangkabau.`mk`: Macedonian.`ml`: Malayalam.`mn`: Mongolian.`mr`: Marathi.`ms`: Malay.`mt`: Maltese.`my`: Burmese.`ne`: Nepali.`new`: Newari.`nl`: Dutch.`no`: Norwegian.`nr`: Southern Ndebele.`nso`: Northern Sotho (Sepedi).`nus`: Nuer.`ny`: Chichewa (Nyanja).`oc`: Occitan.`om`: Oromo.`or`: Odia.`pa`: Punjabi.`pag`: Pangasinan.`pam`: Kapampangan.`pap`: Papiamento.`pl`: Polish.`ps`: Pashto.`pt`: Portuguese.`pt-BR`: Portuguese (Brazil).`pt-PT`: Portuguese (Portugal).`qu`: Quechua.`ro`: Romanian.`rom`: Romani.`rn`: Rundi.`ru`: Russian.`rw`: Kinyarwanda.`sa`: Sanskrit.`scn`: Sicilian.`sd`: Sindhi.`sg`: Sango.`shn`: Shan.`si`: Sinhala.`sk`: Slovak.`sl`: Slovenian.`sm`: Samoan.`sn`: Shona.`so`: Somali.`sq`: Albanian.`sr`: Serbian.`ss`: Swazi.`st`: Southern Sotho.`su`: Sundanese.`sv`: Swedish.`sw`: Swahili.`szl`: Silesian.`ta`: Tamil.`te`: Telugu.`tet`: Tetum.`tg`: Tajik.`th`: Thai.`ti`: Tigrinya.`tk`: Turkmen.`tn`: Tswana.`tr`: Turkish.`ts`: Tsonga.`tt`: Tatar.`ug`: Uyghur.`uk`: Ukrainian.`ur`: Urdu.`uz`: Uzbek.`vi`: Vietnamese.`xh`: Xhosa.`yi`: Yiddish.`yo`: Yoruba.`yua`: Yucatec Maya.`yue`: Cantonese.`zh`: Chinese (Simplified).`zh-TW`: Chinese (Traditional).`zu`: Zulu.**Note**: Use `/` to separate multiple languages, such as `en/ja`, which indicates English and Japanese. Note: This field may return null, indicating that no valid values can be obtained. |
| AsrHotWordsConfigure | [AsrHotWordsConfigure](#AsrHotWordsConfigure) | No | ASR hotword lexicon parameter. Note: This field may return null, indicating that no valid value can be obtained. |
| ExtInfo | String | No | Custom parameter. |
| ProcessType | Integer | No | Subtitle processing type: - 0: ASR recognition subtitle. - 1: pure subtitle translation. - 2: OCR recognition subtitle. **Note**: The default processing type is ASR recognition subtitle if the field is unspecified. |
| SelectingSubtitleAreasConfig | [SelectingSubtitleAreasConfig](#SelectingSubtitleAreasConfig) | No | Area configurations for the subtitle OCR extraction box.Note: This field may return null, indicating that no valid values can be obtained. |

## RawTranscodeParameter

Specifications for custom transcoding

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Container | String | Yes | Container. Valid values: mp4; flv; hls; mp3; flac; ogg; m4a. Among them, mp3, flac, ogg, and m4a are for audio files. |
| RemoveVideo | Integer | No | Whether to remove video data. Valid values: 0: retain;1: remove. Default value: 0. |
| RemoveAudio | Integer | No | Whether to remove audio data. Valid values: 0: retain;1: remove. Default value: 0. |
| VideoTemplate | [VideoTemplateInfo](#VideoTemplateInfo) | No | Video stream configuration parameter. This field is required when `RemoveVideo` is 0. |
| AudioTemplate | [AudioTemplateInfo](#AudioTemplateInfo) | No | Audio stream configuration parameter. This field is required when `RemoveAudio` is 0. |
| TEHDConfig | [TEHDConfig](#TEHDConfig) | No | TESHD transcoding parameter. |
| StdExtInfo | String | No | Additional parameter, which is a serialized JSON string. |
| EnhanceConfig | [EnhanceConfig](#EnhanceConfig) | No | Audio/Video enhancement configuration. Note: This field may return null, indicating that no valid value can be obtained. |
| SubtitleTemplate | [SubtitleTemplate](#SubtitleTemplate) | No | Subtitle parameter. Note: This field may return null, indicating that no valid values can be obtained. |

## RawWatermarkParameter

Custom watermark specifications.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | Watermark type. Valid values: image: image watermark. |
| CoordinateOrigin | String | No | Origin position. valid values:. TopLeft: indicates that the coordinate origin is at the top left corner of the video image and the watermark origin is at the top left corner of the image or text.. TopRight: indicates that the coordinate origin is at the top right corner of the video image and the watermark origin is at the top right corner of the image or text.. BottomLeft: indicates that the coordinate origin is at the bottom-left corner of the video image and the watermark origin is at the bottom-left corner of the image or text.. BottomRight: indicates that the coordinate origin is at the bottom right corner of the video image and the watermark origin is at the bottom right corner of the image or text.  Default value: TopLeft. |
| XPos | String | No | The horizontal position of the origin of the watermark relative to the origin of coordinates of the video. % and px formats are supported: If the string ends in %, the `XPos` of the watermark will be the specified percentage of the video width; for example, `10%` means that `XPos` is 10% of the video width;If the string ends in px, the `XPos` of the watermark will be the specified px; for example, `100px` means that `XPos` is 100 px. Default value: 0 px. |
| YPos | String | No | The vertical position of the origin of the watermark relative to the origin of coordinates of the video. % and px formats are supported: If the string ends in %, the `YPos` of the watermark will be the specified percentage of the video height; for example, `10%` means that `YPos` is 10% of the video height;If the string ends in px, the `YPos` of the watermark will be the specified px; for example, `100px` means that `YPos` is 100 px. Default value: 0 px. |
| ImageTemplate | [RawImageWatermarkInput](#RawImageWatermarkInput) | No | Image watermark template. This field is required when `Type` is `image` and is invalid when `Type` is `text`. |

## RecognizeAudioSentence

Result of the sentence recognition.

Used by actions: RecognizeAudio.

| Name | Type | Description |
| --- | --- | --- |
| Start | Float | Start time in the audio, in seconds. |
| End | Float | End time in the audio, in seconds. |
| Text | String | Audio recognition result. |
| WordsInfo | Array of [WordResult](#WordResult) | Word timestamp result. |

## RuleConditionItem

Rule condition configuration.

Used by actions: CreateSchedule, ModifySchedule.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Key | String | No | Key of the quality inspection item condition. |
| Value | String | No | Value corresponding to the condition. |

## Rules

Task judgment conditions.

Used by actions: CreateSchedule, ModifySchedule.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Id | String | No | Judgment condition ID. Note: This field may return null, indicating that no valid value can be obtained. |
| Conditions | Array of [RuleConditionItem](#RuleConditionItem) | No | Judgment condition configuration. Note: This field may return null, indicating that no valid value can be obtained. |
| Linker | String | No | Logical operator for the list of conditions. Valid values:   - &&: logical AND  - \|\|: logical OR |
| RearDriveIndexs | Array of Integer | No | Indexes of the nodes to execute if the judgment conditions are met. Note: This field may return null, indicating that no valid value can be obtained. |

## S3InputInfo

The AWS S3 storage information of a source file.

Used by actions: BatchProcessMedia, DescribeMediaMetaData, ExtractBlindWatermark, ProcessImage, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| S3Bucket | String | Yes | The AWS S3 bucket. |
| S3Region | String | Yes | The region of the AWS S3 bucket. |
| S3Object | String | Yes | The path of the AWS S3 object. |
| S3SecretId | String | No | The key ID required to access the AWS S3 object. |
| S3SecretKey | String | No | The key required to access the AWS S3 object. |

## S3OutputStorage

The AWS S3 storage information of an output file.

Used by actions: BatchProcessMedia, CreateSchedule, CreateWorkflow, EditMedia, ModifySchedule, ProcessImage, ProcessLiveStream, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| S3Bucket | String | Yes | The AWS S3 bucket. |
| S3Region | String | Yes | The region of the AWS S3 bucket. |
| S3SecretId | String | No | The key ID required to upload files to the AWS S3 object. |
| S3SecretKey | String | No | The key required to upload files to the AWS S3 object. |

## SampleSnapshotTaskInput

Input parameter type of a sampled screenshot task.

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | Sampled screenshot template ID. |
| WatermarkSet | Array of [WatermarkInput](#WatermarkInput) | No | List of up to 10 image or text watermarks. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | Target bucket of a sampled screenshot. If this parameter is left empty, the `OutputStorage` value of the upper folder will be inherited. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputObjectPath | String | No | Output path of an image file after sampled screenshot taking, which can be a relative or absolute path. If you need to define an output path, the path must end with `.{format}`. For variable names, refer to [Filename Variable](https://intl.cloud.tencent.com/document/product/862/37039?from_cn_redirect=1).Relative path example: Filename_{Variable name}.{format}.Filename.{format}. Absolute path example: /Custom path/Filename_{Variable name}.{format}. If left empty, a relative path is used by default: `{inputName}_sampleSnapshot_{definition}_{number}.{format}`. |
| ObjectNumberFormat | [NumberFormat](#NumberFormat) | No | Rule of the `{number}` variable in the sampled screenshot output path. Note: This field may return null, indicating that no valid values can be obtained. |

## SampleSnapshotTemplate

Details of a sampled screenshot template

Used by actions: DescribeSampleSnapshotTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of a sampled screenshot template. |
| Type | String | Template type. Valid values: Preset: Preset template;Custom: Custom template. |
| Name | String | Name of a sampled screenshot template. |
| Comment | String | Template description. |
| Width | Integer | Maximum value of the width (or long side) of a screenshot in px. Value range: 0 and [128, 4,096]. If both `Width` and `Height` are 0, the resolution will be the same as that of the source video;If `Width` is 0, but `Height` is not 0, `Width` will be proportionally scaled;If `Width` is not 0, but `Height` is 0, `Height` will be proportionally scaled;If both `Width` and `Height` are not 0, the custom resolution will be used. Default value: 0. |
| Height | Integer | Maximum value of the height (or short side) of a screenshot in px. Value range: 0 and [128, 4,096]. If both `Width` and `Height` are 0, the resolution will be the same as that of the source video;If `Width` is 0, but `Height` is not 0, `Width` will be proportionally scaled;If `Width` is not 0, but `Height` is 0, `Height` will be proportionally scaled;If both `Width` and `Height` are not 0, the custom resolution will be used. Default value: 0. |
| ResolutionAdaptive | String | Resolution adaption. Valid values: open: Enabled. In this case, `Width` represents the long side of a video, while `Height` the short side;close: Disabled. In this case, `Width` represents the width of a video, while `Height` the height. Default value: open. |
| Format | String | Image format. |
| SampleType | String | Sampled screenshot type. |
| SampleInterval | Integer | Sampling interval. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| FillType | String | Fill type. "Fill" refers to the way of processing a screenshot when its aspect ratio is different from that of the source video. The following fill types are supported:  stretch: Stretch. The screenshot will be stretched frame by frame to match the aspect ratio of the source video, which may make the screenshot "shorter" or "longer";black: Fill with black. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with black color blocks.white: Fill with white. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with white color blocks.gauss: Fill with Gaussian blur. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with Gaussian blur. Default value: black. |

## ScheduleAnalysisTaskResult

The result of a content analysis task of a scheme.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | The task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task has failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | The error code. 0 indicates the task is successful; other values indicate the task has failed. This parameter is not recommended. Please use `ErrCodeExt` instead. |
| Message | String | The error message. |
| Input | [AiAnalysisTaskInput](#AiAnalysisTaskInput) | The input of the content analysis task. |
| Output | Array of [AiAnalysisResult](#AiAnalysisResult) | Analysis task output. |
| BeginProcessTime | String | Task execution start time in ISO date and time format. |
| FinishTime | String | Task execution completion time in ISO date and time format. |

## ScheduleExecRuleTaskResult

Result type of the media quality inspection task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, which can be PROCESSING, SUCCESS, or FAIL. |
| ErrCodeExt | String | Error code. An empty string indicates success, while other values indicate failure. For specific values, see the list of MPS error codes at https://www.tencentcloud.comom/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81. |
| Message | String | Error message. |
| Input | [ExecRulesTask](#ExecRulesTask) | Input of the conditional judgment task. |
| Output | [ExecRuleTaskData](#ExecRuleTaskData) | Output of the conditional judgment task. Note: This field may return null, indicating that no valid value can be obtained. |

## ScheduleQualityControlTaskResult

Media quality inspection task result type.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | The task status. Valid values: `PROCESSING`, `SUCCESS`, `FAIL`. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value indicates the task has failed. For details, see [Error Codes](https://www.tencentcloud.com/document/product/1041/40249). |
| ErrCode | Integer | The error code. `0` indicates the task is successful; other values indicate the task has failed. This parameter is not recommended. Please use `ErrCodeExt` instead. |
| Message | String | The error message. |
| Input | [AiQualityControlTaskInput](#AiQualityControlTaskInput) | Media quality inspection task input. |
| Output | [QualityControlData](#QualityControlData) | Media quality inspection task output.Note: This field may return null, indicating that no valid values can be obtained. |
| Progress | Integer | Task execution progress. |

## ScheduleRecognitionTaskResult

The result of a content recognition task of a scheme.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | The task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task has failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | The error code. 0 indicates the task is successful; other values indicate the task has failed. This parameter is not recommended. Please use `ErrCodeExt` instead. |
| Message | String | The error message. |
| Input | [AiRecognitionTaskInput](#AiRecognitionTaskInput) | The input of the content recognition task. |
| Output | Array of [AiRecognitionResult](#AiRecognitionResult) | Output of the identification task. |
| BeginProcessTime | String | Task execution start time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |
| FinishTime | String | Task execution completion time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |

## ScheduleReviewTaskResult

The result of a content moderation task of a scheme.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | The task status. Valid values: PROCESSING, SUCCESS, FAIL. |
| ErrCodeExt | String | The error code. An empty string indicates the task is successful; any other value returned indicates the task has failed. For details, see [Error Codes](https://intl.cloud.tencent.com/document/product/1041/40249). |
| ErrCode | Integer | The error code. 0 indicates the task is successful; other values indicate the task has failed. This parameter is not recommended. Please use `ErrCodeExt` instead. |
| Message | String | The error message. |
| Input | [AiContentReviewTaskInput](#AiContentReviewTaskInput) | The input of the content moderation task. |
| Output | Array of [AiContentReviewResult](#AiContentReviewResult) | The output of the content moderation task. Note: This field may return null, indicating that no valid values can be obtained. |

## ScheduleSmartSubtitleTaskResult

Result of the smart subtitle scheduling task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCodeExt | String | Error code. An empty string indicates that the task is successful, and other values indicate that the task has failed. For specific values, see [Error Codes] (https://intl.cloud.tencent.com/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81). |
| ErrCode | Integer | Error code. 0 indicates that the task is successful, and other values indicate that the task has failed. (This field is not recommended. Use the new error code field ErrCodeExt instead.) |
| Message | String | Error message. |
| Input | [SmartSubtitlesTaskInput](#SmartSubtitlesTaskInput) | Input of the recognition task. |
| Output | Array of [SmartSubtitlesResult](#SmartSubtitlesResult) | Output of the identification task. |
| BeginProcessTime | String | Task execution start time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |
| FinishTime | String | Task execution completion time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |

## ScheduleTask

The information of a scheme.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | The scheme ID. |
| Status | String | The scheme status. Valid values: PROCESSINGFINISH |
| ErrCode | Integer | If the value returned is not 0, there was a source error. If 0 is returned, refer to the error codes of the corresponding task type. |
| Message | String | If there was a source error, this parameter is the error message. For other errors, refer to the error messages of the corresponding task type. |
| InputInfo | [MediaInputInfo](#MediaInputInfo) | The information of the file processed. Note: This field may return null, indicating that no valid values can be obtained. |
| MetaData | [MediaMetaData](#MediaMetaData) | The metadata of the source video. Note: This field may return null, indicating that no valid values can be obtained. |
| ActivityResultSet | Array of [ActivityResult](#ActivityResult) | The output of the scheme. Note: This field may return null, indicating that no valid values can be obtained. |

## SchedulesInfo

The details of a scheme.

Used by actions: DescribeSchedules.

| Name | Type | Description |
| --- | --- | --- |
| ScheduleId | Integer | The scheme ID. |
| ScheduleName | String | The scheme name. Note: This field may return null, indicating that no valid values can be obtained. |
| Type | String | The scheme type. Valid values:  `Preset``Custom`  Note: This field may return null, indicating that no valid values can be obtained. |
| Status | String | The scheme status. Valid values: `Enabled` `Disabled` Note: This field may return null, indicating that no valid values can be obtained. |
| Trigger | [WorkflowTrigger](#WorkflowTrigger) | The trigger of the scheme. Note: This field may return null, indicating that no valid values can be obtained. |
| Activities | Array of [Activity](#Activity) | The subtasks of the scheme. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | The bucket to save the output file. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputDir | String | The directory to save the output file. Note: This field may return null, indicating that no valid values can be obtained. |
| TaskNotifyConfig | [TaskNotifyConfig](#TaskNotifyConfig) | The notification configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| CreateTime | String | The creation time in [ISO date format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). Note: This field may return null, indicating that no valid values can be obtained. |
| UpdateTime | String | The last updated time in [ISO date format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). Note: This field may return null, indicating that no valid values can be obtained. |
| ResourceId | String | Resource ID. For those without an associated resource ID, fill in with an account's primary resource ID. Note: This field may return null, indicating that no valid values can be obtained. |

## ScratchRepairConfig

Banding removal configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Intensity | Float | No | The strength. Value range: 0.0-1.0 Default value: 0.0 Note: This field may return null, indicating that no valid values can be obtained. |

## SecurityGroupInfo

Security group information.

Used by actions: DescribeStreamLinkSecurityGroup.

| Name | Type | Description |
| --- | --- | --- |
| Id | String | Security group ID. |
| Name | String | Security group name. |
| Whitelist | Array of String | Allowlist list. |
| OccupiedInputs | Array of String | List of bound input streams. Note: This field may return null, indicating that no valid value can be obtained. |
| Region | String | Security group address. |
| OccupiedOutputs | Array of String | List of bound output streams. Note: This field may return null, indicating that no valid value can be obtained. |

## SegmentRecognitionItem

Used by actions: DescribeTaskDetail, ParseLiveStreamProcessNotification, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float |  |
| StartTimeOffset | Float |  |
| EndTimeOffset | Float |  |
| SegmentUrl | String | Specifies the split segment URL. |
| CovImgUrl | String | Specifies the segment cover. |
| Title | String | Segment title. |
| Summary | String | Specifies the segment summary. |
| Keywords | Array of String | Segmentation keywords. |
| BeginTime | String | Specifies the start time of a live streaming segment in the ISO date format. |
| EndTime | String | Specifies the end time of a live streaming segment in the ISO date format. |
| PersonId | String | Specifies the character ID. |

## SegmentSpecificInfo

Information on special segment configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch for segment duration at startup. Optional values: on: Turn on the switch off: Turn off the switch Default value: off Note: This field may return null, indicating that no valid value can be obtained. |
| FragmentTime | Integer | No | Segment duration at startup. Unit: second Note: This field may return null, indicating that no valid value can be obtained. |
| FragmentEndNum | Integer | No | Number of effective segments, indicating the first FragmentEndNum segments with FragmentTime. Value range: >=1 Note: This field may return null, indicating that no valid value can be obtained. |

## SelectingSubtitleAreasConfig

Area configurations for the subtitle OCR extraction box.

Used by actions: BatchProcessMedia, CreateSmartSubtitleTemplate, DescribeSmartSubtitleTemplates, ModifySmartSubtitleTemplate, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| AutoAreas | Array of [EraseArea](#EraseArea) | No | Automatically selects custom areas.For the selected areas, the AI model is used to automatically detect and extract the target content. |
| SampleWidth | Integer | No | Width of the sample video or image, in pixels. |
| SampleHeight | Integer | No | Height of the sample video or image, in pixels. |

## SharpEnhanceConfig

Detail enhancement configuration.

Used by actions: CreateProcessImageTemplate, ModifyProcessImageTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Intensity | Float | No | The strength. Value range: 0.0-1.0 Default value: 0.0 Note: This field may return null, indicating that no valid values can be obtained. |

## SimpleAesDrm

The AES-128 encryption details.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Uri | String | Yes | The URI of decryption key. Note: This field may return null, indicating that no valid values can be obtained. |
| Key | String | Yes | Encryption key (32-byte hexadecimal string). Note: This field may return null, indicating that no valid value can be obtained. |
| Vector | String | No | Initialization vector for encryption (32-byte hexadecimal string). Note: This field may return null, indicating that no valid value can be obtained. |

## SmartErasePrivacyConfig

Intelligent erasure template privacy protection configuration.

Used by actions: CreateSmartEraseTemplate, DescribeSmartEraseTemplates, ModifySmartEraseTemplate, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| PrivacyModel | String | Yes | Specifies the privacy protection removal method. -Blur: specifies the blur detection. -Specifies the mosaic. |
| PrivacyTargets | Array of String | Yes | Privacy protection objective. no need to import an array when in use on API Explorer. just add the corresponding item and fill in the value. -Human face. -License plate. |

## SmartEraseSubtitleConfig

Intelligent erasure template subtitle configuration.

Used by actions: CreateSmartEraseTemplate, DescribeSmartEraseTemplates, ModifySmartEraseTemplate, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SubtitleEraseMethod | String | Yes | Specifies the subtitle erasure method. **Automatic erasing:** automatically identifies subtitle text content in videos through AI models and performs seamless erasure to generate new videos. frame interference and unique subtitle styles may cause certain missed or incorrect erasures, which can be handled through specified area erasure. When using automatic erasure, if AutoAreas is not specified, the default region (lower middle of the frame) will be erased automatically. if AutoAreas is specified, it will change to erase the designated area. **Specified area erasing:** if your subtitle position is fixed, directly specify the erasure area to decrease the chance of removal omission to the maximum extent. When your choice is specified area erasure, please import at least one designated region in CustomAreas. -Automated removal. - specifies the custom specified area erasure. |
| SubtitleModel | String | Yes | Subtitle erasure model. **Standard version (recommend):** if your subtitle style is standard, normally recommend choose this version for better effectiveness with seamless detail. **Regional version:** if your subtitles have special styles such as italics, shadows, or motion effects, we recommend choosing the regional version for larger removal area, though the detail effect is not as good as the standard version. -Specifies the standard model. -area. specifies the regional model. |
| OcrSwitch | String | No | Whether OCR subtitle extraction is enabled. default value: OFF. Supports enabling OCR subtitle extraction only when SubtitleEraseMethod is set to auto. when enabled, it identifies the longest and most stable text area within the region as the subtitle area, then performs text extraction and removal. -ON: enable. -OFF. specifies the disabled state. |
| SubtitleLang | String | No | Subtitle language, for OCR guidance, default value zh_en. this parameter is valid only when OcrSwitch is ON. -Chinese and english. -multi other. Other supported languages:. Chinese, english, japanese, korean, spanish, french, german, portuguese, vietnamese, malay, russian, italian, dutch, swedish, finnish, danish, norwegian, hungarian, thai, hindi, arabic, indian-bengali, indian-gujarati, indian-kannada, indian-malayalam, indian-tamil, indian-telugu, slovenian, polish, catalan, bosnian, czech, estonian, croatian, punjabi, marathi, azerbaijani, indonesian, luxembourgish, lithuanian, latvian, maltese, slovak, turkish, kazakh, greek, irish, belarusian, khmer, tagalog, pashto, persian, tajik. |
| SubtitleFormat | String | No | Specifies the subtitle file format. default value: vtt. this parameter is valid only when OcrSwitch is set to ON. -srt format. -vtt: WebVTT format. |
| TransSwitch | String | No | Specifies whether to enable subtitle translation. default value: OFF. this parameter is valid only when OcrSwitch is set to ON. -ON: enable. -OFF. specifies the disabled state. |
| TransDstLang | String | No | Subtitle target language. default value: en. this parameter is valid only when TransSwitch is set to ON. Supported languages:. Simplified chinese. Specifies the language. valid values: en (english). Ja: japanese. Ko: korean. Fr: french. es: spanish. It: italian. de: german. tr: turkish. Ru: russian. pt: portuguese. Vi: vietnamese. id: indonesian. ms: malay. Th: thai. Ar: arabic. hi: Hindi |
| AutoAreas | Array of [EraseArea](#EraseArea) | No | Specifies automatic removal of a custom region. Specifies the use of an AI model to automatically detect and erase existing targets in the specified region. Note that this parameter will not take effect when the removal method is custom. for template modification, input [] to clean up the region. the template region information remains unchanged if not imported. |
| CustomAreas | Array of [EraseTimeArea](#EraseTimeArea) | No | Specifies erasure of a custom region. Detects and directly performs removal within a specified time range for the selected region. Note: when modifying the template, pass [] to clear the region. the template region information remains unchanged if not passed. |

## SmartEraseTaskInput

Smart erasure task.

Used by actions: CreateSchedule, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | No | Smart erasure template id. |
| RawParameter | [RawSmartEraseParameter](#RawSmartEraseParameter) | No | Intelligent erasure custom parameter. valid when Definition is 0. this parameter is used for highly custom scenarios. we recommend you prioritize using Definition to specify intelligent erasure parameters. Note: This field may return null, indicating that no valid value can be obtained. |
| OverrideParameter | [OverrideEraseParameter](#OverrideEraseParameter) | No | Custom parameters for smart erasing. When the value of Definition is not 0, this parameter is valid. When certain erasing parameters in this structure are specified, the specified parameters will be used to overwrite those in the smart erasing template. This parameter is used in highly customized scenarios. It is recommended to use only Definition to specify smart erasing parameters. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | Specifies the target storage for files. if left blank, it inherits the upper-level OutputStorage value. Note: This field may return null, indicating that no valid value can be obtained. |
| OutputObjectPath | String | No | Output path of the file, which can be a relative or absolute path. Specifies the output path must end with `.{format}`. variable names, please refer to [filename variable explanation](https://www.tencentcloud.com/document/product/1041/33495?has_map=1). **Relative path example**: Filename_{Variable name}.{format}Filename.{format}  **Absolute path example**: /Custom path/filename_{variable name}.{format}  **Note**: currently does not support the `BatchProcessMedia` api. |

## SmartEraseTaskResult

Smart erasure task result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCodeExt | String | Error code. An empty string indicates that the task is successful, and other values indicate that the task has failed. For specific values, see [Error Codes] (https://www.tencentcloud.comom/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81). |
| Message | String | Error message. |
| Input | [SmartEraseTaskInput](#SmartEraseTaskInput) | Input of the smart erasure task. Note: This field may return null, indicating that no valid value can be obtained. |
| Output | [AiAnalysisTaskDelLogoOutput](#AiAnalysisTaskDelLogoOutput) | Output of the smart erasure task. Note: This field may return null, indicating that no valid value can be obtained. |
| Progress | Integer | Task progress. |
| BeginProcessTime | String | Task execution start time in ISO datetime format. |
| FinishTime | String | Task execution completion time in ISO datetime format. |

## SmartEraseTemplateItem

Smart erasing template details.

Used by actions: DescribeSmartEraseTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique identifier of the smart erasing template. |
| Name | String | Smart erasing template name. |
| Comment | String | Smart erasing template description information. |
| Type | String | Template type. Valid values: * Preset: system preset template. * Custom: user-defined template. |
| EraseType | String | Erasing type. -subtitle: subtitle removal. -watermark: watermark removal. -privacy: privacy protection. |
| EraseSubtitleConfig | [SmartEraseSubtitleConfig](#SmartEraseSubtitleConfig) | Subtitle erasing configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| EraseWatermarkConfig | [SmartEraseWatermarkConfig](#SmartEraseWatermarkConfig) | Watermark erasing configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| ErasePrivacyConfig | [SmartErasePrivacyConfig](#SmartErasePrivacyConfig) | Privacy protection configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| CreateTime | String | Template creation time in [ISO datetime format](https://www.tencentcloud.comom/document/product/862/37710?from_cn_redirect=1#52). |
| UpdateTime | String | Last modification time of the template in [ISO datetime format](https://www.tencentcloud.comom/document/product/862/37710?from_cn_redirect=1#52). |
| AliasName | String | Alias of the preset smart erasing template. |

## SmartEraseWatermarkConfig

smart erasure template watermark configuration.

Used by actions: CreateSmartEraseTemplate, DescribeSmartEraseTemplates, ModifySmartEraseTemplate, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| WatermarkEraseMethod | String | Yes | Specifies the watermark removal method. **Auto-Removal:** automatically identifies watermarks in the video using model a and generates a new video after removal. suitable for dynamic watermarks. When using automated removal, if you do not specify AutoAreas, the full-screen video will be erased automatically. if AutoAreas is specified, it will change to erase the designated areas. **Specified area erasure:** for static watermarks with fixed locations, we recommend you directly specify the erasure area. When you choose specified area erasure, import at least one specified region.  -Automated removal. -Specifies the custom specified area erasure. |
| WatermarkModel | String | Yes | Specifies the watermark removal model. Basic version: average effect, cost-effective, suitable for videos with clean backgrounds or animations. Advanced edition: better effectiveness, suitable for mini-drama and reality style video. **Supported values**: - basic - advanced |
| AutoAreas | Array of [EraseArea](#EraseArea) | No | Automatically erase the custom region. Automatically detects and erases the targeted removal in the specified region using the AI model. Note that this parameter will not take effect when the removal method is custom. to modify the template, input [] for the clean-up region. if not provided, the template region information remains unchanged. |
| CustomAreas | Array of [EraseTimeArea](#EraseTimeArea) | No | Specifies the removal of a custom region. Specifies to directly perform removal without detection and recognition within a selected time range for the specified region. Note: when modifying the template, pass [] to clear the region. the template region information remains unchanged if not passed. |

## SmartSubtitleTaskAsrFullTextResult

Full speech recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCodeExt | String | Error code. An empty string indicates that the task is successful, and other values indicate that the task has failed. For specific values, see [Error Codes] (https://intl.cloud.tencent.com/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81). |
| ErrCode | Integer | Error code. 0 indicates that the task is successful, and other values indicate that the task has failed. (This field is not recommended. Use the new error code field ErrCodeExt instead.) |
| Message | String | Error message. |
| Input | [SmartSubtitleTaskResultInput](#SmartSubtitleTaskResultInput) | Input information on the full speech recognition task. Note: This field may return null, indicating that no valid value can be obtained. |
| Output | [SmartSubtitleTaskAsrFullTextResultOutput](#SmartSubtitleTaskAsrFullTextResultOutput) | Output information on the full speech recognition task. Note: This field may return null, indicating that no valid value can be obtained. |
| Progress | Integer | Task progress. Note: This field may return null, indicating that no valid value can be obtained. |

## SmartSubtitleTaskAsrFullTextResultOutput

Full speech recognition result.

Used by actions: DescribeBatchTaskDetail, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| SegmentSet | Array of [SmartSubtitleTaskAsrFullTextSegmentItem](#SmartSubtitleTaskAsrFullTextSegmentItem) | List of segments for full speech recognition. Note: This field may return null, indicating that no valid value can be obtained. |
| Path | String | Subtitle file path. |
| SubtitlePath | String | Subtitle file path. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Subtitle file storage location. |

## SmartSubtitleTaskAsrFullTextSegmentItem

Segment undergone full speech recognition.

Used by actions: DescribeBatchTaskDetail, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Confidence of a recognized segment. Value range: 0-100. |
| StartTimeOffset | Float | Start time offset of a recognized segment, in seconds. |
| EndTimeOffset | Float | End time offset of a recognized segment, in seconds. |
| Text | String | Recognized text. |
| Wordlist | Array of [WordResult](#WordResult) | Word timestamp information.  Note: This field may return null, indicating that no valid value can be obtained. |
| SpeakerId | String | Speaker ID (if speaker recognition is enabled). |

## SmartSubtitleTaskBatchOutput

Output information for smart subtitle tasks.

Used by actions: DescribeBatchTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Progress | Integer | Task progress. |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCodeExt | String | Error code. An empty string indicates that the task is successful, and other values indicate that the task has failed. For specific values, see [Error Codes] (https://intl.cloud.tencent.com/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81). |
| Message | String | Error message. |
| TransTextTask | [SmartSubtitleTaskTransTextResultOutput](#SmartSubtitleTaskTransTextResultOutput) | Translation task output information. Note: This field may return null, indicating that no valid value can be obtained. |
| AsrFullTextTask | [SmartSubtitleTaskAsrFullTextResultOutput](#SmartSubtitleTaskAsrFullTextResultOutput) | Output information on the full speech recognition task. Note: This field may return null, indicating that no valid value can be obtained. |

## SmartSubtitleTaskFullTextResult

Full-text recognition result for smart subtitle tasks.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, which can be PROCESSING, SUCCESS, or FAIL. |
| ErrCodeExt | String | Error code. A null string indicates that the task is successful, while other values indicate that the task has failed. For valid values, see the list of [MPS error codes](https://www.tencentcloud.comom/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81). |
| ErrCode | Integer | Error code. 0 indicates that the task is successful, and other values indicate that the task has failed. (This field is not recommended. Use the new error code field ErrCodeExt instead.) |
| Message | String | Error message. |
| Input | [SmartSubtitleTaskResultInput](#SmartSubtitleTaskResultInput) | Input information for smart subtitle tasks. Note: This field may return null, indicating that no valid values can be obtained. |
| Output | [SmartSubtitleTaskTextResultOutput](#SmartSubtitleTaskTextResultOutput) | Output information for smart subtitle tasks.Note: This field may return null, indicating that no valid values can be obtained. |
| Progress | Integer | Task progress. Note: This field may return null, indicating that no valid values can be obtained. |

## SmartSubtitleTaskResultInput

Smart subtitle translation input.

Used by actions: DescribeBatchTaskDetail, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Smart subtitle template ID. |
| RawParameter | [RawSmartSubtitleParameter](#RawSmartSubtitleParameter) | Custom smart subtitle parameter. It takes effect when Definition is set to 0. This parameter is used in high customization scenarios. It is recommended that you preferentially use Definition to specify smart subtitle parameters. Note: This field may return null, indicating that no valid value can be obtained. |

## SmartSubtitleTaskTextResultOutput

Smart subtitle recognition result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| RecognizeSubtitleResult | Array of [SubtitleResult](#SubtitleResult) | Subtitle recognition result. Note: This field may return null, indicating that no valid values can be obtained. |
| TransSubtitleResult | Array of [SubtitleResult](#SubtitleResult) | Subtitle translation result. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Storage location of the subtitle file. Note: This field may return null, indicating that no valid values can be obtained. |

## SmartSubtitleTaskTransTextResult

Translation result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Task status, including PROCESSING, SUCCESS, and FAIL. |
| ErrCodeExt | String | Error code. An empty string indicates that the task is successful, and other values indicate that the task has failed. For specific values, see [Error Codes] (https://intl.cloud.tencent.com/document/product/862/50369?from_cn_redirect=1#.E8.A7.86.E9.A2.91.E5.A4.84.E7.90.86.E7.B1.BB.E9.94.99.E8.AF.AF.E7.A0.81). |
| ErrCode | Integer | Error code. 0 indicates that the task is successful, and other values indicate that the task has failed. (This field is not recommended. Use the new error code field ErrCodeExt instead.) |
| Message | String | Error message. |
| Input | [SmartSubtitleTaskResultInput](#SmartSubtitleTaskResultInput) | Translation task input information. Note: This field may return null, indicating that no valid value can be obtained. |
| Output | [SmartSubtitleTaskTransTextResultOutput](#SmartSubtitleTaskTransTextResultOutput) | Translation task output information. Note: This field may return null, indicating that no valid value can be obtained. |
| Progress | Integer | Task progress. Note: This field may return null, indicating that no valid value can be obtained. |

## SmartSubtitleTaskTransTextResultOutput

Translation result.

Used by actions: DescribeBatchTaskDetail, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| SegmentSet | Array of [SmartSubtitleTaskTransTextSegmentItem](#SmartSubtitleTaskTransTextSegmentItem) | List of segments for translation. Note: This field may return null, indicating that no valid value can be obtained. |
| SubtitlePath | String | Subtitle file path. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | Subtitle file storage location. |
| Path | String | Subtitle file URL. |
| SubtitleResults | Array of [SubtitleTransResultItem](#SubtitleTransResultItem) | Returned translation result during multilingual translation. |

## SmartSubtitleTaskTransTextSegmentItem

Translated segment.

Used by actions: DescribeBatchTaskDetail, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Confidence | Float | Confidence of a recognized segment. Value range: 0-100. |
| StartTimeOffset | Float | Start time offset of a recognized segment, in seconds. |
| EndTimeOffset | Float | End time offset of a recognized segment, in seconds. |
| Text | String | Recognized text. |
| Trans | String | Translated text. |
| Wordlist | Array of [WordResult](#WordResult) | Word timestamp information.  Note: This field may return null, indicating that no valid value can be obtained. |

## SmartSubtitleTemplateItem

Smart subtitle template details.

Used by actions: DescribeSmartSubtitleTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique identifier of the smart subtitle template. |
| Name | String | Smart subtitle template name. Note: This field may return null, indicating that no valid value can be obtained. |
| Comment | String | Smart subtitle template description. Note: This field may return null, indicating that no valid value can be obtained. |
| Type | String | Template type. Valid values: * Preset: system preset template * Custom: user-defined template Note: This field may return null, indicating that no valid value can be obtained. |
| AsrHotWordsConfigure | [AsrHotWordsConfigure](#AsrHotWordsConfigure) | ASR hotword lexicon parameter. Note: This field may return null, indicating that no valid value can be obtained. |
| AsrHotWordsLibraryName | String | Name of the hotword lexicon associated with the template. Note: This field may return null, indicating that no valid value can be obtained. |
| VideoSrcLanguage | String | List of source languages of the video with smart subtitles. `zh`: Simplified Chinese. `yue`: Cantonese. `zh-PY`: Chinese, English, and Cantonese. `zh_medical`: Chinese (medical scenario). `zh_dialect`: Chinese dialect. `prime_zh`: Chinese, English, and Chinese dialects. `zh_en`: Chinese and English. `en`: English. `ja`: Japanese. `ko`: Korean. `fr`: French. `es`: Spanish. `it`: Italian. `de`: German. `tr`: Turkish. `ru`: Russian. `pt`: Portuguese (Brazil). `pt-PT`: Portuguese (Portugal). `vi`: Vietnamese. `id`: Indonesian. `ms`: Malay. `th`: Thai. `ar`: Arabic. `hi`: Hindi. `fil`: Filipino. `auto`: automatic recognition (it is only supported in pure subtitle translation). |
| SubtitleFormat | String | Smart subtitle file format. - vtt: WebVTT.- srt: SRT.- original: same as the source subtitle file (for subtitle translation templates).- Not specified or empty: no subtitle file generated.Note: This field may return null, indicating that no valid values can be obtained. |
| SubtitleType | Integer | Smart subtitle language type. 0: source language1: target language 2: source language + target language The value can only be 0 when TranslateSwitch is set to OFF.The value can only be 1 or 2 when TranslateSwitch is set to ON. |
| TranslateSwitch | String | Subtitle translation switch. ON: enable translation OFF: disable translation Note: This field may return null, indicating that no valid value can be obtained. |
| TranslateDstLanguage | String | Target language for subtitle translation. This field is valid when the value of TranslateSwitch is ON. `zh`: Simplified Chinese. `zh-TW`: Traditional Chinese. `en`: English. `ja`: Japanese. `ko`: Korean. `fr`: French. `es`: Spanish. `it`: Italian. `de`: German. `tr`: Turkish. `ru`: Russian. `pt`: Portuguese (Brazil). `pt-PT`: Portuguese (Portugal). `vi`: Vietnamese. `id`: Indonesian. `ms`: Malay. `th`: Thai. `ar`: Arabic. `hi`: Hindi. `fil`: Filipino. **Note**: Use `/` to separate multiple languages, such as `en/ja`, which indicates English and Japanese. Note: This field may return null, indicating that no valid values can be obtained. |
| CreateTime | String | Template creation time in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |
| UpdateTime | String | Last modification time of the template in [ISO datetime format](https://intl.cloud.tencent.com/document/product/862/37710?from_cn_redirect=1#52). |
| AliasName | String | Alias of the preset smart subtitle template. Note: This field may return null, indicating that no valid value can be obtained. |
| ProcessType | Integer | Subtitle processing type:- 0: ASR subtitle recognition.- 1: subtitle translation.- 2: OCR subtitle recognition. |
| SelectingSubtitleAreasConfig | [SelectingSubtitleAreasConfig](#SelectingSubtitleAreasConfig) | Area configurations for the subtitle OCR extraction box.Note: This field may return null, indicating that no valid values can be obtained. |

## SmartSubtitlesResult

Smart subtitle task result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Type | String | Task type. Valid values: - AsrFullTextRecognition: full speech recognition. - TransTextRecognition: speech translation. - PureSubtitleTrans: pure subtitle translation. - OcrFullTextRecognition: text-based subtitle extraction. |
| AsrFullTextTask | [SmartSubtitleTaskAsrFullTextResult](#SmartSubtitleTaskAsrFullTextResult) | Full speech recognition result. When Type is  set to AsrFullTextRecognition, this parameter takes effect. Note: This field may return null, indicating that no valid value can be obtained. |
| TransTextTask | [SmartSubtitleTaskTransTextResult](#SmartSubtitleTaskTransTextResult) | Translation result. When Type is   set to TransTextRecognition, this parameter takes effect. Note: This field may return null, indicating that no valid value can be obtained. |
| PureSubtitleTransTask | [PureSubtitleTransResult](#PureSubtitleTransResult) | The translation result of the pure subtitle file is returned when the translation type is PureSubtitleTrans. Note: This field may return null, indicating that no valid values can be obtained. |
| OcrFullTextTask | [SmartSubtitleTaskFullTextResult](#SmartSubtitleTaskFullTextResult) | Text-based subtitle extraction result. This field is valid when the value of Type is OcrFullTextRecognition. Note: This field may return null, indicating that no valid values can be obtained. |

## SmartSubtitlesTaskInput

Smart subtitle input struct.

Used by actions: BatchProcessMedia, CreateSchedule, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | No | Smart subtitle template ID. |
| UserExtPara | String | No | User extension field, which does not need to be filled in for general scenarios. |
| RawParameter | [RawSmartSubtitleParameter](#RawSmartSubtitleParameter) | No | Custom smart subtitle parameter. It takes effect when Definition is set to 0. This parameter is used in high customization scenarios. It is recommended that you preferentially use Definition to specify smart subtitle parameters.     Note: This field may return null, indicating that no valid value can be obtained. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | Bucket that stores the output file. If it is left unspecified, the storage location in InputInfo will be inherited. **Note**: This parameter is required when InputInfo.Type is set to URL. Note: This field may return null, indicating that no valid value can be obtained. |
| OutputObjectPath | String | No | Output path of the generated subtitle file, which can be a relative or absolute path. To define the output path, end the path with .{format}. For variable names, see the description of file name variables at https://www.tencentcloud.comom/document/product/862/37039.?from_cn_redirect=1  Relative path example:  - File name_{variable name}.{format}.  - File name.{format}.  Absolute path example:  -/Custom path/File name_{variable name}.{format}.  If this field is left unspecified, the default value is the relative path in the following format: {inputName}_smartsubtitle_{definition}.{format}. |

## SnapshotByTimeOffsetTaskInput

Input parameter type of a time point screenshot task

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | ID of a time point screenshot template. |
| ExtTimeOffsetSet | Array of String | No | List of screenshot time points in the format of `s` or `%`: If the string ends in `s`, it means that the time point is in seconds; for example, `3.5s` means that the time point is the 3.5th second;If the string ends in `%`, it means that the time point is the specified percentage of the video duration; for example, `10%` means that the time point is 10% of the video duration. |
| TimeOffsetSet | Array of Float | No | List of time points of screenshots in seconds. |
| WatermarkSet | Array of [WatermarkInput](#WatermarkInput) | No | List of up to 10 image or text watermarks. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | Target bucket of a generated time point screenshot file. If this parameter is left empty, the `OutputStorage` value of the upper folder will be inherited. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputObjectPath | String | No | Output path for an image file of screenshots taken at specific time points, which can be a relative or absolute path. If you need to define an output path, the path must end with `.{format}`. For variable names, refer to [Filename Variable](https://intl.cloud.tencent.com/document/product/862/37039?from_cn_redirect=1). Relative path example: Filename_{Variable name}.{format}.Filename.{format}. Absolute path example: /Custom path/Filename_{Variable name}.{format}. If left empty, a relative path is used by default: `{inputName}_snapshotByTimeOffset_{definition}_{number}.{format}`. |
| ObjectNumberFormat | [NumberFormat](#NumberFormat) | No | Rule of the `{number}` variable in the time point screenshot output path. Note: This field may return null, indicating that no valid values can be obtained. |

## SnapshotByTimeOffsetTemplate

Details of a time point screenshot template.

Used by actions: DescribeSnapshotByTimeOffsetTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of a time point screenshot template. |
| Type | String | Template type. Valid values: Preset: Preset template;Custom: Custom template. |
| Name | String | Name of a time point screenshot template. |
| Comment | String | Template description. |
| Width | Integer | Maximum value of the width (or long side) of a screenshot in px. Value range: 0 and [128, 4,096]. If both `Width` and `Height` are 0, the resolution will be the same as that of the source video;If `Width` is 0, but `Height` is not 0, `Width` will be proportionally scaled;If `Width` is not 0, but `Height` is 0, `Height` will be proportionally scaled;If both `Width` and `Height` are not 0, the custom resolution will be used. Default value: 0. |
| Height | Integer | Maximum value of the height (or short side) of a screenshot in px. Value range: 0 and [128, 4,096]. If both `Width` and `Height` are 0, the resolution will be the same as that of the source video;If `Width` is 0, but `Height` is not 0, `Width` will be proportionally scaled;If `Width` is not 0, but `Height` is 0, `Height` will be proportionally scaled;If both `Width` and `Height` are not 0, the custom resolution will be used. Default value: 0. |
| ResolutionAdaptive | String | Resolution adaption. Valid values: open: Enabled. In this case, `Width` represents the long side of a video, while `Height` the short side;close: Disabled. In this case, `Width` represents the width of a video, while `Height` the height. Default value: open. |
| Format | String | Image format. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| FillType | String | Fill type. "Fill" refers to the way of processing a screenshot when its aspect ratio is different from that of the source video. The following fill types are supported:  stretch: Stretch. The screenshot will be stretched frame by frame to match the aspect ratio of the source video, which may make the screenshot "shorter" or "longer";black: Fill with black. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with black color blocks.white: Fill with white. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with white color blocks.gauss: Fill with Gaussian blur. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with Gaussian blur. Default value: black. |

## SpecificationDataItem

Statistical data for the task of the specified specification.

Used by actions: DescribeUsageData.

| Name | Type | Description |
| --- | --- | --- |
| Specification | String | Task specification. |
| Data | Array of [TaskStatDataItem](#TaskStatDataItem) | Statistical data. |

## SpekeDrm

FairPlay, WideVine, PlayReady, and other DRM encryption technologies.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ResourceId | String | Yes | Resource ID. The field content is user-defined. It supports 1 to 128 characters consisting of digits, letters, underscores (_), and hyphens (-). This field corresponds to the cid field in the Speke request. Note: Different DRM vendors have different restrictions on this field (for example, SDMC Technology Co., Ltd. does not support this field containing underscores). For specific rules, check with the vendors. |
| KeyServerUrl | String | Yes | DRM manufacturer access address. the field content is obtained from the drm manufacturer.  Note: different DRM manufacturers have different limitations on the number of substreams. for example, PallyCon limits the number of substreams to no more than 5, and DRMtoday only supports encryption of up to 9 substreams. |
| Vector | String | Yes | Initialization vector for encryption (32-byte hexadecimal string). the field content is user-customized. |
| EncryptionMethod | String | No | Encryption method. Valid values: cbcs: supported by PlayReady, Widevine, FairPlay, Widevine+FairPlay, Widevine+PlayReady, PlayReady+FairPlay, and Widevine+PlayReady+FairPlay. cenc: supported by PlayReady, Widevine, and Widevine+PlayReady. If it is left unspecified: Use cbcs for FairPlay by default. Use cenc for PlayReady and Widevine by default. Use cbcs for Widevine+FairPlay, PlayReady+FairPlay, and Widevine+PlayReady+FairPlay by default. Use cenc for Widevine+PlayReady by default. |
| EncryptionPreset | String | No | Substream encryption rule. Default value: preset0. preset 0: use the same key to encrypt all substreams preset1: use different keys for each substream |

## SubtitlePosition

Subtitle position information.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| CenterY | Integer | Y-coordinate value when the subtitle is centered. |

## SubtitleResult

Smart subtitle task result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Language | String | No | Language of the subtitle file. |
| Status | String | No | Whether the processing is successful. |
| Path | String | No | Subtitle file URL. |

## SubtitleTemplate

The subtitle settings.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Path | String | No | The URL of the subtitles to add to the video. Note: This field may return null, indicating that no valid values can be obtained. |
| StreamIndex | Integer | No | Specifies the subtitle track for embedding subtitles into the video. the Streamindex parameter takes value starting from 0, where 0 indicates usage of the first subtitle track in the source video. if Path is specified, use Path preferentially. either Path or Streamindex should be specified.  -Note: StreamIndex must match the subtitle track index in the source file. for example, if the subtitle track in the source file is stream#0:3, StreamIndex should be 3. otherwise, task processing failed.   Note: This field may return null, indicating that no valid value can be obtained. |
| SubtitleFileInput | [MediaInputInfo](#MediaInputInfo) | No | Input information on the subtitle file to be embedded into the video. Currently, only subtitle files stored in COS are supported. Note: This field may return null, indicating that no valid values can be obtained. |
| FontFileInput | [MediaInputInfo](#MediaInputInfo) | No | Input information of the font file of the burned-in subtitle. URL and COS are supported. If both are specified, the URL information is used. If FontFileInput is specified, FontFileInput takes precedence over FontType. |
| FontType | String | No | Font type. Valid values: hei.ttf: SimHei.song.ttf: SimSun.kai.ttf (recommend) or simkai.ttf: SimKai.msyh.ttf: Microsoft YaHei.msyhbd.ttf: Microsoft YaHei Bold.hkjgt.ttf: DynaFont King Gothic.dhttx.ttf: DianHei Extra Light.xqgdzt.ttf: XiQue GuZiDian.qpcyt.ttf: QiaoPin ChaoYuan.arial.ttf: English only.dinalternate.ttf: DIN Alternate Bold.helveticalt.ttf: Helvetica.helveticains.ttf: Helvetica Inserat.trajanpro.ttf: TrajanPro-Bold.korean.ttf: Korean.japanese.ttf: Japanese.thai.ttf: Thai. Default value: hei.ttf.  Note: |
| FontSize | String | No | Font size. If not specified, the font size of the subtitle file applies. Pixel and percentage formats are supported:  - Pixel: Npx. Value range of N: (0,4096]. - Percentage: N%. Value range of N: (0,100]. For example, 10% means the subtitle font size is 10% of the source video height.  The default size is 5% of the source video height if this parameter is not specified or the font size is not configured in the subtitle file.  Note: This field may return null, indicating that no valid values can be obtained. |
| FontColor | String | No | Font color. Format: 0xRRGGBB. Default value: 0xFFFFFF (white). Note: This field may return null, indicating that no valid value can be obtained. |
| FontAlpha | Float | No | The text transparency. Value range: 0-1. `0`: Fully transparent.`1`: Fully opaque. Default value: 1. Note: This field may return null, indicating that no valid values can be obtained. |
| YPos | String | No | Subtitle position on the Y-axis. If this parameter is specified, the built-in coordinates in the subtitle file will be ignored. The pixel and percentage formats are supported.   - Pixel: Npx. Value range of N: [0,4096].  - Percentage: N%. Value range of N: [0,100]. For example, 10% indicates that the subtitle position on the Y-axis is 10% of the video height.  By default, the position is 4% of the source video height. Note: The origin of the coordinate axes is at the bottom of the central axis of the source video, and the subtitle reference position is at the bottom of the central axis of the subtitles, as shown in the figure below. ![image](https://ie-mps-1258344699.cos.ap-nanjing.tencentcos.cn/common/cloud/mps-demo/102_ai_subtitle/subtitle_style.png)  Note: This field may return null, indicating that no valid value can be obtained. |
| BoardY | String | No | Subtitle background position on the Y-axis. Pixel and percentage formats are supported.   - Pixel: Npx. Value range of N: [0,4096].  - Percentage: N%. Value range of N: [0,100]. For example, 10% indicates that the subtitle background position on the Y-axis is 10% of the video height.  If this parameter is not specified, the subtitle background is disabled. Note: The origin of the coordinate axes is at the bottom of the central axis of the source video, and the reference position of the subtitle background is at the bottom of the central axis of the source video, as shown in the figure below. ![image](https://ie-mps-1258344699.cos.ap-nanjing.tencentcos.cn/common/cloud/mps-demo/102_ai_subtitle/subtitle_style.png)  Note: This field may return null, indicating that no valid value can be obtained. |
| BoardWidth | Integer | No | Background width. The value should be a positive integer. - Value range for pixels: [0,4096]. - Value range for percentages: [0, 100]. If background is enabled and this parameter is not specified, the default width is 90% of the source video width.  Note: This field may return null, indicating that no valid values can be obtained. |
| BoardHeight | Integer | No | Background height. The value should be a positive integer. - Value range for pixels: [0,4096]. - Value range for percentages: [0, 100]. If background is enabled and this parameter is not specified, the default height is 15% of the source video height.  Note: This field may return null, indicating that no valid values can be obtained. |
| BoardColor | String | No | Board color. Format: 0xRRGGBB. Default value: 0x000000 (black). Note: This field may return null, indicating that no valid value can be obtained. |
| BoardAlpha | Float | No | Subtitle background transparency. Value range: [0, 1]. 0: completely transparent.1: completely opaque. Default value: 0.8. Note: This field may return null, indicating that no valid value can be obtained. |
| OutlineWidth | Float | No | Stroke width. The value should be a floating-point number. - Value range for pixels: [0, 1000]. - Value range for percentages: [0, 100]. If this is not specified, the default width is 0.3% of the source video height. |
| OutlineColor | String | No | Stroke color. The value should be a 6-digit hexadecimal RGB value. If this is not specified, the default color is black. |
| OutlineAlpha | Float | No | Stroke transparency. The value should be a positive floating-point number in the range of (0, 1]. If this is not specified, the default value is 1, which means completely opaque. |
| ShadowWidth | Float | No | Shadow width. The value should be a floating-point number. - Value range for pixels: [0, 1000]. - Value range for percentages: [0, 100]. If this is not specified, no shadow is applied by default. |
| ShadowColor | String | No | Shadow color. The value should be a 6-digit hexadecimal RGB value. If this is not specified, the default color is black (with shadow configured). |
| ShadowAlpha | Float | No | Shadow transparency. The value should be a positive floating-point number in the range of (0, 1]. If this is not specified, the default value is 1, which means completely opaque (with shadow configured). |
| LineSpacing | Integer | No | Line spacing. The value should be a positive integer. - Value range for pixels: [0, 1000]. - Value range for percentages: [0, 100]. If this is not specified, the default value is 0. |
| Alignment | String | No | Alignment mode. Valid values: top: The top position of the subtitle is fixed, while the bottom position changes according to the number of lines. bottom: The bottom position of the subtitle is fixed, while the top position changes according to the number of lines. If this is not specified, bottom alignment is used by default. |
| BoardWidthUnit | Integer | No | Default value is 0. If this is set to 1, the value of BoardWidth is a percentage based on the video width. |
| BoardHeightUnit | Integer | No | Default value is 0. If this is set to 1, the value of BoardHeight is a percentage based on the video height. |
| OutlineWidthUnit | Integer | No | Default value is 0. If this is set to 1, the value of OutlineWidth is a percentage based on the video height. |
| ShadowWidthUnit | Integer | No | Default value is 0. If this is set to 1, the value of ShadowWidth is a percentage based on the video height. |
| LineSpacingUnit | Integer | No | Default value is 0. If this is set to 1, the value of LineSpacing is a percentage based on the video height. |

## SubtitleTransResultItem

Subtitle translation output result.

Used by actions: DescribeBatchTaskDetail, DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| Status | String | Translation marker. - Success - Error |
| TransSrc | String | Source language (such as "en"). |
| TransDst | String | Target language (such as "zh"). |
| Path | String | Subtitle file URL. |

## SuperResolutionConfig

Super resolution configuration.

Used by actions: CreateProcessImageTemplate, CreateTranscodeTemplate, ModifyProcessImageTemplate, ModifyTranscodeTemplate, ProcessImage.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Type | String | No | The strength. Valid values: lq: For low-resolution videos with obvious noisehq: For high-resolution videos Default value: lq. Note: This field may return null, indicating that no valid values can be obtained. |
| Size | Integer | No | The ratio of the target resolution to the original resolution. Valid values: 2 Default value: 2. Note: This field may return null, indicating that no valid values can be obtained. |

## SvgWatermarkInput

Input parameter of an SVG watermarking template

Used by actions: CreateWatermarkTemplate, DescribeWatermarkTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Width | String | No | Watermark width, which supports six formats of px, %, W%, H%, S%, and L%: If the string ends in px, the `Width` of the watermark will be in px; for example, `100px` means that `Width` is 100 px; if `0px` is entered  and `Height` is not `0px`, the watermark width will be proportionally scaled based on the source SVG image; if `0px` is entered for both `Width` and `Height`, the watermark width will be the width of the source SVG image;If the string ends in `W%`, the `Width` of the watermark will be the specified percentage of the video width; for example, `10W%` means that `Width` is 10% of the video width;If the string ends in `H%`, the `Width` of the watermark will be the specified percentage of the video height; for example, `10H%` means that `Width` is 10% of the video height;If the string ends in `S%`, the `Width` of the watermark will be the specified percentage of the short side of the video; for example, `10S%` means that `Width` is 10% of the short side of the video;If the string ends in `L%`, the `Width` of the watermark will be the specified percentage of the long side of the video; for example, `10L%` means that `Width` is 10% of the long side of the video;If the string ends in %, the meaning is the same as `W%`. Default value: 10W%. |
| Height | String | No | Watermark height, which supports six formats of px, %, W%, H%, S%, and L%: If the string ends in px, the `Height` of the watermark will be in px; for example, `100px` means that `Height` is 100 px; if `0px` is entered  and `Width` is not `0px`, the watermark height will be proportionally scaled based on the source SVG image; if `0px` is entered for both `Width` and `Height`, the watermark height will be the height of the source SVG image;If the string ends in `W%`, the `Height` of the watermark will be the specified percentage of the video width; for example, `10W%` means that `Height` is 10% of the video width;If the string ends in `H%`, the `Height` of the watermark will be the specified percentage of the video height; for example, `10H%` means that `Height` is 10% of the video height;If the string ends in `S%`, the `Height` of the watermark will be the specified percentage of the short side of the video; for example, `10S%` means that `Height` is 10% of the short side of the video;If the string ends in `L%`, the `Height` of the watermark will be the specified percentage of the long side of the video; for example, `10L%` means that `Height` is 10% of the long side of the video;If the string ends in %, the meaning is the same as `H%`. Default value: 0 px. |

## SvgWatermarkInputForUpdate

Input parameter of an SVG watermarking template

Used by actions: ModifyWatermarkTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Width | String | No | Watermark width, which supports six formats of px, %, W%, H%, S%, and L%: If the string ends in px, the `Width` of the watermark will be in px; for example, `100px` means that `Width` is 100 px; if `0px` is entered  and `Height` is not `0px`, the watermark width will be proportionally scaled based on the source SVG image; if `0px` is entered for both `Width` and `Height`, the watermark width will be the width of the source SVG image;If the string ends in `W%`, the `Width` of the watermark will be the specified percentage of the video width; for example, `10W%` means that `Width` is 10% of the video width;If the string ends in `H%`, the `Width` of the watermark will be the specified percentage of the video height; for example, `10H%` means that `Width` is 10% of the video height;If the string ends in `S%`, the `Width` of the watermark will be the specified percentage of the short side of the video; for example, `10S%` means that `Width` is 10% of the short side of the video;If the string ends in `L%`, the `Width` of the watermark will be the specified percentage of the long side of the video; for example, `10L%` means that `Width` is 10% of the long side of the video;If the string ends in %, the meaning is the same as `W%`. Default value: 10W%. |
| Height | String | No | Watermark Height, which supports six formats of px, %, W%, H%, S%, and L%: If the string ends in px, the `Height` of the watermark will be in px; for example, `100px` means that `Height` is 100 px; if `0px` is entered  and `Width` is not `0px`, the watermark height will be proportionally scaled based on the source SVG image; if `0px` is entered for both `Width` and `Height`, the watermark size will be the size of the source SVG image;If the string ends in `W%`, the `Height` of the watermark will be the specified percentage of the video width; for example, `10W%` means that `Height` is 10% of the video width;If the string ends in `H%`, the `Height` of the watermark will be the specified percentage of the video height; for example, `10H%` means that `Height` is 10% of the video height;If the string ends in `S%`, the `Height` of the watermark will be the specified percentage of the short side of the video; for example, `10S%` means that `Height` is 10% of the short side of the video;If the string ends in `L%`, the `Height` of the watermark will be the specified percentage of the long side of the video; for example, `10L%` means that `Height` is 10% of the long side of the video;If the string ends in %, the meaning is the same as `W%`. Default value: 0px. |

## TEHDConfig

TESHD parameter configuration.

Used by actions: CreateTranscodeTemplate, CreateWorkflow, DescribeTranscodeTemplates, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | TESHD type. Valid values: TEHD-100: TESHD-100. If this parameter is left empty, TESHD will not be enabled. |
| MaxVideoBitrate | Integer | No | Maximum bitrate, which is valid when `Type` is `TESHD`. If this parameter is left empty or 0 is entered, there will be no upper limit for bitrate. |

## TEHDConfigForUpdate

TESHD parameter configuration.

Used by actions: CreateWorkflow, ModifyTranscodeTemplate, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | No | The TSC type. Valid values: `TEHD-100`: TSC-100 (video TSC). `TEHD-200`: TSC-200 (audio TSC).  If this parameter is left blank, no modification will be made. Note: This field may return null, indicating that no valid values can be obtained. |
| MaxVideoBitrate | Integer | No | The maximum video bitrate. If this parameter is not specified, no modifications will be made. Note: This field may return null, indicating that no valid values can be obtained. |

## TagConfigureInfo

Control parameter of intelligent tagging task

Used by actions: CreateAIAnalysisTemplate, DescribeAIAnalysisTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of intelligent tagging task. Valid values: ON: enables intelligent tagging task;OFF: disables intelligent tagging task. |

## TagConfigureInfoForUpdate

Control parameter of intelligent tagging task

Used by actions: ModifyAIAnalysisTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of intelligent tagging task. Valid values: ON: enables intelligent tagging task;OFF: disables intelligent tagging task. |

## TaskNotifyConfig

Event notification configuration of a task.

Used by actions: BatchProcessMedia, CreateSchedule, CreateWorkflow, DescribeBatchTaskDetail, DescribeSchedules, DescribeTaskDetail, DescribeWorkflows, EditMedia, ExtractBlindWatermark, ModifySchedule, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| NotifyType | String | No | Notification type. available values:. CMQ: offline. switch to TDMQ-CMQ.. TDMQ-CMQ: message queue. URL: when a URL is specified, the HTTP callback is pushed to the address specified by NotifyUrl. the callback protocol is HTTP+json. the content of the packet body is the same as the output parameters of the parseeventnotification api.. SCF: not recommended. additional configuration is required in the console.. AWS-SQS: aws queue, suitable for aws tasks only and requires the same region.. note: if left blank, it is TDMQ-CMQ by default. to use another type, you need to fill in the corresponding type value. if using TDMQ-CMQ message queue, an excessively large task response may cause queue failure.. |
| NotifyMode | String | No | Workflow notification method. Valid values: Finish, Change. If this parameter is left empty, `Finish` will be used. |
| NotifyUrl | String | No | HTTP callback URL, required if `NotifyType` is set to `URL` |
| CmqModel | String | No | The CMQ or TDMQ-CMQ model. Valid values: Queue, Topic. |
| CmqRegion | String | No | The CMQ or TDMQ-CMQ region, such as `sh` (Shanghai) or `bj` (Beijing). |
| TopicName | String | No | The CMQ or TDMQ-CMQ topic to receive notifications. This parameter is valid when `CmqModel` is `Topic`. |
| QueueName | String | No | The CMQ or TDMQ-CMQ queue to receive notifications. This parameter is valid when `CmqModel` is `Queue`. |
| AwsSQS | [AwsSQS](#AwsSQS) | No | The AWS SQS queue. This parameter is required if `NotifyType` is `AWS-SQS`.  Note: This field may return null, indicating that no valid values can be obtained. |
| NotifyKey | String | No | key used to generate a callback signature. |

## TaskOutputStorage

The information of the media processing output object.

Used by actions: BatchProcessMedia, CreateSchedule, CreateWorkflow, DescribeBatchTaskDetail, DescribeImageTaskDetail, DescribeSchedules, DescribeTaskDetail, DescribeWorkflows, EditMedia, ModifySchedule, ParseNotification, ProcessImage, ProcessLiveStream, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | Specifies the type of storage location for the media processing service output object. valid values:. COS: cos storage.. AWS-S3: aws storage, suitable for aws tasks only and requires the same region.. VOD: video-on-demand (vod) pro edition. |
| CosOutputStorage | [CosOutputStorage](#CosOutputStorage) | No | The location to save the output object in COS. This parameter is valid and required when `Type` is COS. Note: This field may return null, indicating that no valid value can be obtained. |
| S3OutputStorage | [S3OutputStorage](#S3OutputStorage) | No | The AWS S3 bucket to save the output file. This parameter is required if `Type` is `AWS-S3`. Note: This field may return null, indicating that no valid value can be obtained. |
| VODOutputStorage | [VODOutputStorage](#VODOutputStorage) | No | The VOD Pro application and bucket to save the output file. This parameter is required if `Type` is `VOD`. Note: This field may return null, indicating that no valid value can be obtained. |

## TaskSimpleInfo

Task overview information

Used by actions: DescribeTasks.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Task ID. |
| TaskType | String | Task type. Valid values:  WorkflowTask: Workflow processing task; LiveProcessTask: Live stream processing task. |
| CreateTime | String | Creation time of a task in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| BeginProcessTime | String | Start time of task execution in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). If the task has not been started yet, this field will be `0000-00-00T00:00:00Z`. |
| FinishTime | String | End time of a task in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). If the task has not been completed yet, this field will be `0000-00-00T00:00:00Z`. |
| SubTaskTypes | Array of String | The subtask type. |

## TaskStatData

Statistical data of the task.

Used by actions: DescribeUsageData.

| Name | Type | Description |
| --- | --- | --- |
| TaskType | String | Task type. Transcode: transcoding.Enhance: enhancement.AIAnalysis: intelligent analysis.AIRecognition: intelligent recognition.AIReview: content moderation.Snapshot: screenshot.AnimatedGraphics: conversion to GIF.ImageProcess: image processing. |
| Summary | Array of [TaskStatDataItem](#TaskStatDataItem) | Statistical data overview of the number of tasks. Transcode: The unit of usage is seconds.Enhance: The unit of usage is seconds.AIAnalysis: The unit of usage is seconds.AIRecognition: The unit of usage is seconds.AIReview: The unit of usage is seconds.Snapshot: The unit of usage is images.AnimatedGraphics: The unit of usage is seconds.ImageProcess: The unit of usage is images.. |
| Details | Array of [SpecificationDataItem](#SpecificationDataItem) | Statistical data details for tasks of various specifications. 1. Transcoding specification: Audio: audio-only.Remuxing: conversion to muxing.Other transcoding specifications: {TYPE}.{CODEC}.{SPECIFICATION}. Specifically, valid values for TYPE:     Standard: standard transcoding.     TESHD-10: TSC transcoding for videos.     TESHD-20: TSC transcoding for audios.     TESHD-30: TSC transcoding for audios/videos.     TESHD-30-SDK: duration-based billing of TSC transcoding SDK for audios/videos.     TESHD-30-SDKCores: core number-based billing of TSC transcoding SDK for audios/videos.     Edit: video editing.   Specifically, valid values for CODEC:     H264: H. 264 encoding.     H265: H.265 encoding.     AV1: AV1 encoding.     MV-HEVC: MV-HEVC encoding.   Specifically, valid values for SPECIFICATION:     SD: standard definition.     HD: high definition.     FHD: full HD.     2K: 2K.     4K: 4K. For example, TESHD-10.H265.HD indicates TSC transcoding using the H.265 encoding method. 2. Enhancement specification: video enhancement format: {TYPE}.{CODEC}.{SPECIFICATION}.{FPS}, where valid values for CODEC and SPECIFICATION follow the transcoding descriptions mentioned above, and FPS is valid only when the atomic enhancement type is used; audio enhancement format: {TYPE}. Valid values for enhancement TYPE: Enhance: common enhancement type, which might be any atomic enhancement type.Atomic enhancement type. Valid values for video atomic enhancement type:     Sdr2hdr: SDR2HDR.     SuperResolution: super resolution.     InsertFrame: frame interpolation.     ComprehensiveEnhancement: comprehensive enhancement.     NoiseReduction: video noise reduction.     ColorEnhancement: color enhancement.     RemoveScratches: scratch removal.     Deburr:  artifacts removal.     DetailEnhancement: detail enhancement.     LightEnhancement: low-light enhancement.     FaceEnhancement: face enhancement.   Valid value for audio atomic enhancement type.     AudioNoiseReduction     VolumeBalance     AudioBeautify     AudioSeparation  3. Screenshot specification: ImageSprite: sprite.SampleSnapshot: sampled screenshot.SnapshotByTime: time point screenshot. 4. Image processing specification: {TYPE}.{CODEC}.{SPECIFICATION}.  ImageCompression: image encoding. ImageSuperResolution: image super resolution.EnhanceImageColor: image color enhancement. 5. Intelligent analysis specification: AIAnalysis: major category for analysis.VideoTag: video tag.VideoClassification: video category.SmartCover: smart cover.FrameLabel: frame tag.VideoSplit: video splitting.Highlights: highlights.OpeningAndEnding: opening and ending clips. 6. Intelligent recognition specification: AIRecognition: major category for recognition.FaceRecognition: face recognition.TextRecognition: optical character recognition.ObjectRecognition: object recognition.VoiceRecognition: automatic speech recognition.VoiceTranslation: speech translation. 7. There are no segmentation specifications for content moderation and conversion to GIF. |

## TaskStatDataItem

Statistical data of the task, including the number of tasks and usage.

Used by actions: DescribeUsageData.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | The start time of the time interval where the data resides, using the ISO date format. for example, when the time granularity is day, 2018-12-01T00:00:00+08:00 indicates the interval from december 1, 2018 (inclusive) to december 2, 2018 (exclusive). |
| Count | Integer | Number of tasks. |
| Usage | Integer | Task usage. |

## TerrorismConfigureInfo

The parameters for detecting sensitive information.

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImgReviewInfo | [TerrorismImgReviewTemplateInfo](#TerrorismImgReviewTemplateInfo) | No | The parameters for detecting sensitive information in images. |
| OcrReviewInfo | [TerrorismOcrReviewTemplateInfo](#TerrorismOcrReviewTemplateInfo) | No | The parameters for detecting sensitive information based on OCR. |

## TerrorismConfigureInfoForUpdate

The parameters for detecting sensitive information.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImgReviewInfo | [TerrorismImgReviewTemplateInfoForUpdate](#TerrorismImgReviewTemplateInfoForUpdate) | No | The parameters for detecting sensitive information in images. |
| OcrReviewInfo | [TerrorismOcrReviewTemplateInfoForUpdate](#TerrorismOcrReviewTemplateInfoForUpdate) | No | The parameters for detecting sensitive information based on OCR. |

## TerrorismImgReviewTemplateInfo

The parameters for detecting sensitive information in images.

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Whether to detect sensitive information in images. Valid values: ONOFF |
| LabelSet | Array of String | No | Sensitive content filter tags. The auditing results including the selected tags are returned. If the filter tag is empty, all auditing results will be returned. Valid values: guns: weapons and guns;crowd: crowd gathering;bloody: bloodiness;police: police force;banners: sensitive flags;militant: militants;explosion: explosions and fires;terrorists: sensitive persons. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 90 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 80 will be used by default. Value range: 0-100. |

## TerrorismImgReviewTemplateInfoForUpdate

The parameters for detecting sensitive information in images.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to detect sensitive information in images. Valid values: ONOFF |
| LabelSet | Array of String | No | Sensitive content filter tags. The auditing results including the selected tags are returned. If the filter tag is empty, all auditing results will be returned. Valid values: guns: weapons and guns;crowd: crowd gathering;bloody: bloodiness;police: police force;banners: sensitive flags;militant: militants;explosion: explosions and fires;terrorists: sensitive persons. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## TerrorismOcrReviewTemplateInfo

The parameters for detecting sensitive information based on OCR.

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Whether to detect sensitive information based on OCR. Valid values: ONOFF |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0–100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0–100. |

## TerrorismOcrReviewTemplateInfoForUpdate

The parameters for detecting sensitive information based on OCR.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to detect sensitive information based on OCR. Valid values: ONOFF |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0–100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0–100. |

## TextWatermarkTemplateInput

Text watermarking template

Used by actions: CreateWatermarkTemplate, DescribeWatermarkTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| FontType | String | Yes | Font type. Currently, two types are supported: simkai.ttf: Both Chinese and English are supported;arial.ttf: Only English is supported. |
| FontSize | String | Yes | Font size, in the format of Npx. N is a numerical value with a value range of [0, 1] or [8, 4096]. |
| FontColor | String | Yes | Font color in 0xRRGGBB format. Default value: 0xFFFFFF (white). |
| FontAlpha | Float | Yes | Text transparency. Value range: (0, 1] 0: Completely transparent1: Completely opaque Default value: 1. |
| TextContent | String | No | Text content, up to 100 characters. Note: This field may return null, indicating that no valid values can be obtained. |

## TextWatermarkTemplateInputForUpdate

Text watermarking template

Used by actions: ModifyWatermarkTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| FontType | String | No | Font type. Currently, two types are supported: simkai.ttf: Both Chinese and English are supported;arial.ttf: Only English is supported. |
| FontSize | String | No | Font size, in the format of Npx. N is a numerical value with a value range of [0, 1] or [8, 4096]. |
| FontColor | String | No | Font color in 0xRRGGBB format. Default value: 0xFFFFFF (white). |
| FontAlpha | Float | No | Text transparency. Value range: (0, 1] 0: Completely transparent1: Completely opaque |
| TextContent | String | No | Text content, up to 100 characters. |

## TimeSpotCheck

Detection policy for media quality inspection.

Used by actions: CreateQualityControlTemplate, ModifyQualityControlTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| CheckDuration | Integer | No | Duration of each loop detection, in seconds. Value range:   - Minimum value: 10.  - Maximum value: 86400. |
| CheckInterval | Integer | No | Detection interval, in seconds. It indicates the duration after a detection is completed and before the next detection is conducted. Value range:  - Minimum value: 10.  - Maximum value: 3600. |
| SkipDuration | Integer | No | Skipped opening duration, in seconds. Value range:  - Minimum value: 1.  - Maximum value: 1800. |
| CirclesNumber | Integer | No | Number of loops. Value range:  - Minimum value: 0.  - Maximum value: 1000.  If the value is 0 or not specified, it indicates that loops are executed until the video ends. |

## TrackInfo

Audio track info.

Used by actions: CreateTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| TrackNum | String | No | The serial number of the audio track and sound channel. When the value of SelectType is track, this value is an integer, for example: 1. When the value of SelectType is track_channel, this value is a decimal, for example: 1.0. Default value: 1.0. The integer part represents the audio track serial number, and the decimal part represents the sound channel. The audio track serial number is the stream index value of the audio track, which can be 0 or a positive integer. The decimal part supports up to 2 decimal places, and only 0 - 63 is supported. However, when the Codec is aac/eac3/ac3, only 0 - 15 is supported for the decimal part. For example: for an audio track with a stream index value of 1, 1.0 represents the first sound channel of this audio track, and 1.1 represents the second sound channel of this audio track.  Note: This field may return null, indicating that no valid value can be obtained. |
| ChannelVolume | Array of Float | No | The volume of the sound channel. When the value of AudioChannel is 1, the length of this array is 1. For example: [6]. When the value of AudioChannel is 2, the length of this array is 2. For example: [0,6]. When the value of AudioChannel is 6, the length of this array is greater than 2 and less than 16. For example: [-60,0,0,6].  Please specify the value array for this parameter. The value range is between -60 and 6, where -60 indicates mute, 0 maintains the original volume, and 6 doubles the original volume. The default value is -60. Please note: This field supports up to 3 decimal places.  Note: This field may return null, indicating that no valid value can be obtained. |

## TranscodeTaskInput

Input parameter type of a transcoding task

Used by actions: CreateSchedule, CreateWorkflow, DescribeTaskDetail, ModifySchedule, ParseNotification, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | ID of a video transcoding template. |
| RawParameter | [RawTranscodeParameter](#RawTranscodeParameter) | No | Custom video transcoding parameter. valid when Definition is set to 0. This parameter is used in high customization scenarios. it is recommended that you preferentially use Definition to specify transcoding parameters. |
| OverrideParameter | [OverrideTranscodeParameter](#OverrideTranscodeParameter) | No | Video transcoding custom parameter, which is valid when `Definition` is not 0. When any parameters in this structure are entered, they will be used to override corresponding parameters in templates. This parameter is used in highly customized scenarios. We recommend you only use `Definition` to specify the transcoding parameter. Note: this field may return `null`, indicating that no valid value was found. |
| WatermarkSet | Array of [WatermarkInput](#WatermarkInput) | No | Watermark list. Multiple image or text watermarks up to a maximum of 10 are supported. |
| BlindWatermark | [BlindWatermarkInput](#BlindWatermarkInput) | No | Digital watermark parameter. Note: This field may return null, indicating that no valid values can be obtained. |
| MosaicSet | Array of [MosaicInput](#MosaicInput) | No | List of blurs. Up to 10 ones can be supported. |
| StartTimeOffset | Float | No | Start time offset of a transcoded video, in seconds. If this parameter is left empty or set to 0, the transcoded video will start at the same time as the original video.If this parameter is set to a positive number (n for example), the transcoded video will start at the nth second of the original video.If this parameter is set to a negative number (-n for example), the transcoded video will start at the nth second before the end of the original video. |
| EndTimeOffset | Float | No | End time offset of a transcoded video, in seconds. If this parameter is left empty or set to 0, the transcoded video will end at the same time as the original video.If this parameter is set to a positive number (n for example), the transcoded video will end at the nth second of the original video.If this parameter is set to a negative number (-n for example), the transcoded video will end at the nth second before the end of the original video. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | No | Target bucket of an output file. If this parameter is left empty, the `OutputStorage` value of the upper folder will be inherited. Note: This field may return null, indicating that no valid values can be obtained. |
| OutputObjectPath | String | No | Output path of the main file after transcoding, which can be a relative or absolute path. If you need to define an output path, the path must end with `.{format}`. For variable names, refer to [Filename Variable](https://intl.cloud.tencent.com/document/product/862/37039?from_cn_redirect=1).Relative path example: Filename_{Variable name}.{format}.Filename.{format}. Absolute path example: /Custom path/Filename_{Variable name}.{format}. If left empty, a relative path is used by default: `{inputName}_transcode_{definition}.{format}`. |
| SegmentObjectName | String | No | Path to an output file part (the path to ts during transcoding to HLS), which can only be a relative path. If this parameter is left empty, the following relative path will be used by default: `{inputName}_transcode_{definition}_{number}.{format}`. |
| ObjectNumberFormat | [NumberFormat](#NumberFormat) | No | Rule of the `{number}` variable in the output path after transcoding. Note: This field may return null, indicating that no valid values can be obtained. |
| HeadTailParameter | [HeadTailParameter](#HeadTailParameter) | No | Opening and closing credits parameters Note: this field may return `null`, indicating that no valid value was found. |

## TranscodeTemplate

Details of a transcoding template

Used by actions: DescribeTranscodeTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | String | Unique ID of a transcoding template. |
| Container | String | Container format. Valid values: mp4, flv, hls, mp3, flac, ogg. |
| Name | String | Name of a transcoding template. Note: This field may return null, indicating that no valid values can be obtained. |
| Comment | String | Template description. Note: This field may return null, indicating that no valid values can be obtained. |
| Type | String | Template type. Valid values: Preset: Preset template;Custom: Custom template. |
| RemoveVideo | Integer | Whether to remove video data. Valid values: 0: Retain;1: Remove. |
| RemoveAudio | Integer | Whether to remove audio data. Valid values: 0: Retain;1: Remove. |
| VideoTemplate | [VideoTemplateInfo](#VideoTemplateInfo) | Video stream configuration parameter. This field is valid only when `RemoveVideo` is 0. Note: This field may return null, indicating that no valid values can be obtained. |
| AudioTemplate | [AudioTemplateInfo](#AudioTemplateInfo) | Audio stream configuration parameter. This field is valid only when `RemoveAudio` is 0. Note: This field may return null, indicating that no valid values can be obtained. |
| TEHDConfig | [TEHDConfig](#TEHDConfig) | TESHD transcoding parameter. To enable it, please contact your Tencent Cloud sales rep. Note: This field may return null, indicating that no valid values can be obtained. |
| ContainerType | String | Container format filter. Valid values: Video: Video container format that can contain both video stream and audio stream;PureAudio: Audio container format that can contain only audio stream. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| EnhanceConfig | [EnhanceConfig](#EnhanceConfig) | Audio/Video enhancement configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| AliasName | String | Transcoding template alias. Note: This field may return null, indicating that no valid value can be obtained. |

## TranslateConfigureInfo

Control parameter of a full speech recognition task.

Used by actions: DescribeAIRecognitionTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a full speech recognition task. Valid values: ON: Enables an intelligent full speech recognition task;OFF: Disables an intelligent full speech recognition task. |
| SourceLanguage | String | No |  |
| DestinationLanguage | String | No |  |
| SubtitleFormat | String | No | Generated subtitle file format. Leaving it as an empty string means no subtitle file will be generated. Valid value: vtt: Generate a WebVTT subtitle file.  Note: This field may return null, indicating that no valid values can be obtained. |

## UpdateSmartErasePrivacyConfig

Privacy protection configuration for the smart erasing template.

Used by actions: ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| PrivacyModel | String | No | Erasing method of privacy protection. - blur - mosaic |
| PrivacyTargets | Array of String | No | Privacy protection target. (When API Explorer is used, it is not required to specify an array. Add the corresponding items and enter the corresponding values.) - face: human face. - plate: license plate. |

## UpdateSmartEraseSubtitleConfig

Subtitle removal configuration for the smart erasing template.

Used by actions: ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SubtitleEraseMethod | String | No | Subtitle erasing method. **Automatic erasing:** Video subtitles are automatically recognized using an AI model and are erased without traces to generate a new video. However, missed or incorrect erasing may occur due to image interference and special subtitle styles. In this case, you can specify the erasing area. When automatic erasing is used, if AutoAreas is not specified, the default area (lower middle part of the image) will be erased automatically. If AutoAreas is specified, the specified area will be erased automatically. **Specified area erasing:** If the subtitle position is relatively fixed, you are recommended to specify the erasing area directly to minimize missed erasing. When you choose specified area erasing, specify at least one area for CustomAreas. - auto: automatic erasing. - custom: specified area erasing. |
| SubtitleModel | String | No | Subtitle erasing model. **Standard edition (recommended):** For standard subtitle styles, you are recommended to select this edition to ensure better traceless effects in the details. **Area edition:** If the subtitles have special styles, such as calligraphy, shadow, or motion effects, you are recommended to select this edition to ensure a larger erasing area. However, the erasing effect in the details is not as good as the standard edition. - standard: standard edition. - area: area edition. |
| OcrSwitch | String | No | Whether to enable OCR subtitle extraction. The default value is OFF. OCR subtitle extraction is supported if and only if SubtitleEraseMethod is set to auto. When OCR subtitle extraction is enabled, it identifies the text region that appears most persistently and stably within the automatic erasing area as the subtitle area. The text within the subtitle area is extracted and erased. - ON: enabled. -OFF: disabled. |
| SubtitleLang | String | No | Subtitle language, which is used to guide OCR recognition. The default value is zh_en. This parameter is valid only when OcrSwitch is set to ON. - zh_en: Chinese and English. - multi: others. The following are other languages supported for recognition: Chinese, English, Japanese, Korean, Spanish, French, German, Portuguese, Vietnamese, Malay, Russian, Italian, Dutch, Swedish, Finnish, Danish, Norwegian, Hungarian, Thai, Hindi, Arabic, India-Bengali, India-Gujarati, India-Kannada, India-Malayalam, India-Tamil, India-Telugu, Slovenian, Polish, Catalan, Bosnian, Czech, Estonian, Croatian, Punjabi, Marathi, Azerbaijani, Indonesian, Luxembourgish, Lithuanian, Latvian, Maltese, Slovak, Turkish, Kazakh, Greek, Irish, Belarusian, Khmer, Tagalog, Pashto, Persian, and Tajik. |
| SubtitleFormat | String | No | Subtitle file format. The default value is vtt. This parameter is valid only when OcrSwitch is set to ON. - srt: SRT format. - vtt: WebVTT format. |
| TransSwitch | String | No | Whether to enable subtitle translation. The default value is OFF. This parameter is valid only when OcrSwitch is set to ON. - ON: enabled. - OFF: disabled. |
| TransDstLang | String | No | Target language for Subtitle translation. The default value is en. This parameter is valid only when TransSwitch is set to ON. Currently, the following languages are supported: zh: Simplified Chinese. en: English. ja: Japanese. ko: Korean. fr: French. es: Spanish. it: Italian. de: German. tr: Turkish. ru: Russian. pt: Portuguese. vi: Vietnamese. id: Indonesian. ms: Malay. th: Thai. ar: Arabic. hi: Hindi. |
| AutoAreas | Array of [EraseArea](#EraseArea) | No | Custom area for automatic erasing. For the specified area, AI models are used to automatically detect and erase the target objects. Note: When the erasing method is set to custom, this parameter is invalid. When a template is modified, input [] for the erasing area; if this parameter is unspecified, the template area information will remain unchanged. |
| CustomAreas | Array of [EraseTimeArea](#EraseTimeArea) | No | Custom area for specified area erasing. For the specified area, erase the target objects directly without detection and recognition within a selected time period. Note: When a template is modified, input [] for the erasing area; if this parameter is unspecified, the template area information will remain unchanged. |

## UpdateSmartEraseWatermarkConfig

Watermark removal configuration for the smart erasing template.

Used by actions: ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| WatermarkEraseMethod | String | No | Watermark erasing method. **Automatic erasing: ** Video watermarks are automatically recognized using an AI model and are erased to generate a new video. It applies to dynamic watermarks. When automatic erasing is used, if AutoAreas is not specified, the full-screen video image area will be erased automatically. If AutoAreas is specified, the specified area will be erased automatically.  **Specified area erasing: ** For static watermarks in fixed positions, you are recommended to specify the erasing area directly.When you choose specified area erasing, specify at least one area. - auto: automatic erasing. - custom: specified area erasing. |
| WatermarkModel | String | No | Watermark erasing model. Basic Edition: provide average effects and high cost performance. It applies to animations or videos with clean backgrounds. Advanced Edition: provide better effects. It applies to reality-style videos, such as short dramas. - basic: Basic Edition. - advanced: Advanced Edition. |
| AutoAreas | Array of [EraseArea](#EraseArea) | No | Custom area for automatic erasing. For the specified area, AI models are used to automatically detect and erase the target objects. Note: When the erasing method is set to custom, this parameter is invalid. Input [] for the erasing area; if this parameter is unspecified, the template area information will remain unchanged. |
| CustomAreas | Array of [EraseTimeArea](#EraseTimeArea) | No | Custom area for specified area erasing. For the specified area, erase the target objects directly without detection and recognition within a selected time period. Note: Input [] for the erasing area; if this parameter is unspecified, the template area information will remain unchanged. |

## UrlInputInfo

The URL of the object to process.

Used by actions: BatchProcessMedia, DescribeMediaMetaData, ExtractBlindWatermark, ProcessImage, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Url | String | Yes | URL of a video. |

## UserDefineAsrTextReviewTemplateInfo

Control parameter of a custom speech audit task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a custom speech audit task. Valid values: ON: Enables a custom speech audit task;OFF: Disables a custom speech audit task. |
| LabelSet | Array of String | No | Custom speech filter tag. If an audit result contains the selected tag, it will be returned; if the filter tag is empty, all audit results will be returned. To use the tag filtering feature, you need to add the corresponding tag when adding materials for custom speech keywords. There can be up to 10 tags, each with a length limit of 16 characters. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0-100. |

## UserDefineAsrTextReviewTemplateInfoForUpdate

Control parameter of a custom speech audit task

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a custom speech audit task. Valid values: ON: Enables a custom speech audit task;OFF: Disables a custom speech audit task. |
| LabelSet | Array of String | No | Custom speech filter tag. If an audit result contains the selected tag, it will be returned; if the filter tag is empty, all audit results will be returned. To use the tag filtering feature, you need to add the corresponding tag when adding materials for custom speech keywords. There can be up to 10 tags, each with a length limit of 16 characters. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## UserDefineConfigureInfo

Control parameter of a custom audit task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| FaceReviewInfo | [UserDefineFaceReviewTemplateInfo](#UserDefineFaceReviewTemplateInfo) | No | Control parameter of custom figure audit. Note: This field may return null, indicating that no valid values can be obtained. |
| AsrReviewInfo | [UserDefineAsrTextReviewTemplateInfo](#UserDefineAsrTextReviewTemplateInfo) | No | Control parameter of custom speech audit. Note: This field may return null, indicating that no valid values can be obtained. |
| OcrReviewInfo | [UserDefineOcrTextReviewTemplateInfo](#UserDefineOcrTextReviewTemplateInfo) | No | Control parameter of custom text audit. Note: This field may return null, indicating that no valid values can be obtained. |

## UserDefineConfigureInfoForUpdate

Control parameter of a custom audit task.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| FaceReviewInfo | [UserDefineFaceReviewTemplateInfoForUpdate](#UserDefineFaceReviewTemplateInfoForUpdate) | Yes | Control parameter of custom figure audit. |
| AsrReviewInfo | [UserDefineAsrTextReviewTemplateInfoForUpdate](#UserDefineAsrTextReviewTemplateInfoForUpdate) | Yes | Control parameter of custom speech audit. |
| OcrReviewInfo | [UserDefineOcrTextReviewTemplateInfoForUpdate](#UserDefineOcrTextReviewTemplateInfoForUpdate) | Yes | Control parameter of custom text audit. |

## UserDefineFaceReviewTemplateInfo

Control parameter of a custom figure audit task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a custom figure audit task. Valid values: ON: Enables a custom figure audit task;OFF: Disables a custom figure audit task. |
| LabelSet | Array of String | No | Custom figure filter tag. If an audit result contains the selected tag, it will be returned; if the filter tag is empty, all audit results will be returned. To use the tag filtering feature, you need to add the corresponding tag when adding materials for the custom figure library. There can be up to 10 tags, each with a length limit of 16 characters. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 97 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 95 will be used by default. Value range: 0-100. |

## UserDefineFaceReviewTemplateInfoForUpdate

Control parameter of a custom figure audit task.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a custom figure audit task. Valid values: ON: Enables a custom figure audit task;OFF: Disables a custom figure audit task. |
| LabelSet | Array of String | No | Custom figure filter tag. If an audit result contains the selected tag, it will be returned; if the filter tag is empty, all audit results will be returned. To use the tag filtering feature, you need to add the corresponding tag when adding materials for the custom figure library. There can be up to 10 tags, each with a length limit of 16 characters. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## UserDefineOcrTextReviewTemplateInfo

Control parameter of a custom text audit task

Used by actions: CreateContentReviewTemplate, DescribeContentReviewTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | Yes | Switch of a custom text audit task. Valid values: ON: Enables a custom text audit task;OFF: Disables a custom text audit task. |
| LabelSet | Array of String | No | Custom text filter tag. If an audit result contains the selected tag, it will be returned; if the filter tag is empty, all audit results will be returned. To use the tag filtering feature, you need to add the corresponding tag when adding materials for custom text keywords. There can be up to 10 tags, each with a length limit of 16 characters. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. If this parameter is left empty, 100 will be used by default. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. If this parameter is left empty, 75 will be used by default. Value range: 0-100. |

## UserDefineOcrTextReviewTemplateInfoForUpdate

Control parameter of a custom text audit task.

Used by actions: ModifyContentReviewTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Switch of a custom text audit task. Valid values: ON: Enables a custom text audit task;OFF: Disables a custom text audit task. |
| LabelSet | Array of String | No | Custom text filter tag. If an audit result contains the selected tag, it will be returned; if the filter tag is empty, all audit results will be returned. To use the tag filtering feature, you need to add the corresponding tag when adding materials for custom text keywords. There can be up to 10 tags, each with a length limit of 16 characters. |
| BlockConfidence | Integer | No | Threshold score for violation. If this score is reached or exceeded during intelligent audit, it will be deemed that a suspected violation has occurred. Value range: 0-100. |
| ReviewConfidence | Integer | No | Threshold score for human audit. If this score is reached or exceeded during intelligent audit, human audit will be considered necessary. Value range: 0-100. |

## VODInputInfo

VOD Pro object information for MPS.

Used by actions: BatchProcessMedia, DescribeMediaMetaData, ExtractBlindWatermark, ProcessImage, ProcessMedia.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Bucket | String | No | Specifies the Bucket ID where the input file resides. |
| Region | String | No | Specifies the region where the input file's Bucket resides. |
| Object | String | No | Path of the input file. |
| SubAppId | Integer | No | VOD Pro application Id. |

## VODOutputStorage

VOD Pro output object information for MPS.

Used by actions: BatchProcessMedia, CreateSchedule, CreateWorkflow, EditMedia, ModifySchedule, ProcessImage, ProcessLiveStream, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Bucket | String | No | Specifies the destination Bucket ID for the generated output file of MPS. |
| Region | String | No | Specifies the region of the target Bucket for the output. |
| SubAppId | Integer | No | VOD Pro application Id. |

## VideoComprehensionResultItem

Video shot understanding result.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| StartTime | Float | Segment start time (unit: seconds). |
| EndTime | Float | Segment end time (unit: s). |
| Title | String | Video clip title. |
| Description | String | Storyboard clip information description. |
| Keywords | Array of String | Scene clip keywords. |

## VideoDenoiseConfig

Image noise removal configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: ONOFF Default value: ON. |
| Type | String | No | The strength. Valid values: weakstrong Default value: weak. Note: This field may return null, indicating that no valid values can be obtained. |

## VideoEnhanceConfig

Video enhancement configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| FrameRate | [FrameRateConfig](#FrameRateConfig) | No | Frame rate configuration (old) for the frame interpolation. New users are recommended to use FrameRateWithDen for configuring the frame rate of frame interpolation, which supports fractions and provides better results. Note that FrameRate and FrameRateWithDen are mutually exclusive; configuring both simultaneously may cause task failures. The configuration does not take effect if the source frame rate is greater than or equal to the target frame rate. Note: This field may return null, indicating that no valid values can be obtained. |
| SuperResolution | [SuperResolutionConfig](#SuperResolutionConfig) | No | Super-resolution configuration. The video is not processed when the source resolution is higher than the target resolution. Note that it cannot be enabled simultaneously with Large Model enhancement. Note: This field may return null, indicating that no valid values can be obtained. |
| Hdr | [HdrConfig](#HdrConfig) | No | HDR configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| Denoise | [VideoDenoiseConfig](#VideoDenoiseConfig) | No | Video noise reduction configuration. Note that it cannot be enabled simultaneously with LLM enhancement. Note: This field may return null, indicating that no valid values can be obtained. |
| ImageQualityEnhance | [ImageQualityEnhanceConfig](#ImageQualityEnhanceConfig) | No | Comprehensive enhancement configuration. Note that only one of the three items, LLM enhancement, comprehensive enhancement, and artifacts removal, can be configured. Note: This field may return null, indicating that no valid values can be obtained. |
| ColorEnhance | [ColorEnhanceConfig](#ColorEnhanceConfig) | No | Color enhancement configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| LowLightEnhance | [LowLightEnhanceConfig](#LowLightEnhanceConfig) | No | Low-light enhancement configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| ScratchRepair | [ScratchRepairConfig](#ScratchRepairConfig) | No | Banding removal configuration. Note: This field may return null, indicating that no valid values can be obtained. |
| ArtifactRepair | [ArtifactRepairConfig](#ArtifactRepairConfig) | No | Artifacts removal configuration. Note that only one of the three items, LLM enhancement, comprehensive enhancement, and artifacts removal, can be configured. Note: This field may return null, indicating that no valid values can be obtained. |
| EnhanceSceneType | String | No | Enhancement scenario configuration. Valid values: common: common enhancement parameters, which are basic optimization parameters suitable for various video types, enhancing overall image quality.AIGC: overall resolution enhancement. It uses AI technology to improve the overall video resolution and image clarity.short_play: enhance facial and subtitle details, emphasizing characters' facial expressions and subtitle clarity to improve the viewing experience.short_video: optimize complex and diverse image quality issues, tailoring quality enhancements for the complex scenarios such as short videos to address various visual issues.game: fix motion blur and enhance details, with a focus on enhancing the clarity of game details and restoring blurry areas during motions to make the image content during gaming clearer and richer.HD_movie_series: provide a smooth playback effect for UHD videos. Standard 4K HDR videos with an FPS of 60 are generated to meet the needs of broadcasting/OTT for UHD videos. Formats for broadcasting scenarios are supported.LQ_material: low-definition material/old video restoration. It enhances overall resolution, and solves issues of old videos, such as low resolution, blur, distortion, scratches, and color temperature due to their age.lecture: live shows, e-commerce, conferences, and lectures. It improves the face display effect and performs specific optimizations, including face region enhancement, noise reduction, and artifacts removal, for scenarios involving human explanation, such as live shows, e-commerce, conferences, and lectures.Input of a null string indicates that the enhancement scenario is not used. Note: This field may return null, indicating that no valid values can be obtained. |
| DiffusionEnhance | [DiffusionEnhanceConfig](#DiffusionEnhanceConfig) | No | Large Model enhancement configuration. Note that only one of the three items, LLM enhancement, comprehensive enhancement, and artifacts removal, can be configured. It cannot be enabled simultaneously with super-resolution and noise reduction. Note: This field may return null, indicating that no valid values can be obtained. |
| FrameRateWithDen | [FrameRateWithDenConfig](#FrameRateWithDenConfig) | No | New frame rate configuration for the frame interpolation, which supports fractions. Note that it is mutually exclusive with FrameRate. The configuration does not take effect if the source frame rate is greater than or equal to the target frame rate. Note: This field may return null, indicating that no valid values can be obtained. |

## VideoTemplateInfo

Video stream configuration parameter

Used by actions: CreateAdaptiveDynamicStreamingTemplate, CreateTranscodeTemplate, CreateWorkflow, DescribeTranscodeTemplates, ModifyAdaptiveDynamicStreamingTemplate, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Codec | String | Yes | Encoding format of video streams. Valid values: h264: H.264 encoding.h265: H.265 encoding.h266: H.266 encoding.av1: AOMedia Video 1 encoding.vp8: VP8 encoding.vp9: VP9 encoding.mpeg2: MPEG2 encoding.dnxhd: DNxHD encoding.mv-hevc: MV-HEVC encoding. Note: The av1 codec currently only supports mp4, webm, and mkv. Note: The H.266 codec currently only supports mp4, hls, ts, and mov. Note: The VP8 and VP9 codecs currently only support webm and mkv. Note: The MPEG2 and dnxhd codecs currently only support mxf. Note: The MV-HEVC codec currently only supports mp4, hls, and mov. Among them, the HLS format only supports the MP4 segmented format and requires the input source to be a panoramic video (with multiple views). |
| Fps | Integer | Yes | Video frame rate. Value range: When FpsDenominator is empty, the range is [0, 120], in Hz. When FpsDenominator is not empty, the Fps/FpsDenominator range is [0, 120]. If the value is 0, the frame rate will be the same as that of the source video. |
| Bitrate | Integer | Yes | Bitrate of a video stream, in kbps. Value range: 0 and [128, 100000].If the value is 0, the bitrate of the video will be the same as that of the source video. |
| ResolutionAdaptive | String | No | Resolution adaption. Valid values: open: Enabled. When resolution adaption is enabled, `Width` indicates the long side of a video, while `Height` indicates the short side.close: Disabled. When resolution adaption is disabled, `Width` indicates the width of a video, while `Height` indicates the height. Default value: open. Note: When resolution adaption is enabled, `Width` cannot be smaller than `Height`. |
| Width | Integer | No | Maximum value of the video stream width (or long edge) in px. Value range: 0 and [128, 4096]. If both Width and Height are 0, the resolution is the same as the source.If Width is 0 but Height is not 0, the width will be proportionally scaled.If Width is not 0 but Height is 0, the height will be proportionally scaled.If both Width and Height are not 0, the resolution is as specified by the user. Default value: 0. Note: If Codec is set to MV-HEVC, the maximum value can be 7680. |
| Height | Integer | No | Maximum value of the video stream height (or short edge) in px. Value range: 0 and [128, 4,096]. If both Width and Height are 0, the resolution is the same as the source.If Width is 0 but Height is not 0, the width will be proportionally scaled.If Width is not 0 but Height is 0, the height will be proportionally scaled.If both Width and Height are not 0, the resolution is as specified by the user. Default value: 0. Note: If Codec is set to MV-HEVC, the maximum value can be 7680. |
| Gop | Integer | No | Interval between I-frames (keyframes), which can be customized in frames or seconds. GOP value range: 0 and [1, 100000]. If this parameter is 0 or left blank, the system will automatically set the GOP length. |
| GopUnit | String | No | GOP value unit. Optional values: frame: indicates frame second: indicates second Default value: frame Note: This field may return null, indicating that no valid value can be obtained. |
| FillType | String | No | Padding method. When the video stream configuration width and height parameters are inconsistent with the aspect ratio of the original video, the transcoding processing method is "padding". Optional filling method:  stretch: Stretch. The screenshot will be stretched frame by frame to match the aspect ratio of the source video, which may make the screenshot "shorter" or "longer";black: Fill with black. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with black color blocks.white: Fill with white. This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with white color blocks.gauss: applies Gaussian blur to the uncovered area, without changing the image's aspect ratio.  smarttailor: Video images are smartly selected to ensure proportional image cropping. Default value: black. |
| Vcrf | Integer | No | Specifies the constant bitrate control factor for the video. Value range: [0, 51]. Leaving this parameter blank sets it to "Automatic". It is recommended not to specify this parameter unless necessary. If the Mode parameter is set to VBR and the Vcrf value is also configured, MPS will process the video in VBR mode, considering both Vcrf and Bitrate parameters to balance video quality, bitrate, transcoding efficiency, and file size. If the Mode parameter is set to CRF, the Bitrate setting will be invalid, and encoding will be based on the Vcrf value. If the Mode parameter is set to ABR or CBR, the Vcrf value does not need to be configured. Note: This field may return null, indicating that no valid value can be obtained. |
| HlsTime | Integer | No | Average shard duration. value range: (0-10], unit: second. Leaving it blank means auto, which automatically chooses the appropriate segment duration based on video features such as GOP. Note: This field may return null, indicating that no valid values can be obtained. |
| SegmentType | Integer | No | HLS segment type. Valid values: 0: HLS+TS segment2: HLS+TS byte range7: HLS+MP4 segment5: HLS+MP4 byte range Default value: 0  Note: This field is used for normal/TSC transcoding settings and does not apply to adaptive bitrate streaming. To configure the segment type for adaptive bitrate streaming, use the outer field. Note: This field may return null, indicating that no valid value can be obtained. |
| FpsDenominator | Integer | No | Denominator of the frame rate. Note: The value must be greater than 0. Note: This field may return null, indicating that no valid values can be obtained. |
| Stereo3dType | String | No | 3D video splicing mode, applicable only to mv-hevc and effective for 3d videos. valid values: side_by_side: the original video content is arranged in a left-right layout.top_bottom: vertical layout arrangement of original video content. Submit the amount and cost based on the segmented resolution size. Default value: side_by_side. Note: This field may return null, indicating that no valid value can be obtained. |
| VideoProfile | String | No | Profile, suitable for different scenarios. baseline: It only supports I/P-frames and non-interlaced scenarios, and is suitable for scenarios such as video calls and mobile videos. main: It offers I-frames, P-frames, and B-frames, and supports both interlaced and non-interlaced modes. It is mainly used in mainstream audio and video consumption products such as video players and streaming media transmission devices. high: the highest encoding level, with 8x8 prediction added to the main profile and support for custom quantification. It is widely used in scenarios such as Blu-ray storage and HDTV. default: automatic filling along with the original video.      This configuration appears only when the encoding standard is set to H264. baseline/main/high is supported. Default value: default Note: This field may return null, indicating that no valid value can be obtained. |
| VideoLevel | String | No | Encoder level. Default value: auto ("") If the encoding standard is set to H264, the following options are supported: "", 1, 1.1, 1.2, 1.3, 2, 2.1, 2.2, 3, 3.1, 3.2, 4, 4.1, 4.2, 5, and 5.1. If the encoding standard is set to H265, the following options are supported: "", 1, 2, 2.1, 3, 3.1, 4, 4.1, 5, 5.1, 5.2, 6, 6.1, 6.2, and 8.5. Note: This field may return null, indicating that no valid value can be obtained. |
| Bframes | Integer | No | Number of B-frames between reference frames. The default is auto, and a range of 0 - 16 is supported. Note: Leaving it blank means using the auto option. Note: This field may return null, indicating that no valid value can be obtained. |
| Mode | String | No | Bitrate control mode. Optional values: VBR: variable bitrate. The output bitrate is adjusted based on the complexity of the video image, ensuring higher image quality. This mode is suitable for storage scenarios as well as applications with high image quality requirements. ABR: average bitrate. The average bitrate of the output video is kept stable to the greatest extent, but short-term bitrate fluctuations are allowed. This mode is suitable for scenarios where it is necessary to minimize the overall bitrate while a certain quality is maintained. CBR: constant bitrate. The output bitrate remains constant during the video encoding process, regardless of changes in image complexity. This mode is suitable for scenarios with strict network bandwidth requirements, such as live streaming. VCRF: constant rate factor. The video quality is controlled by setting a quality factor, achieving constant quality encoding of videos. The bitrate is automatically adjusted based on the complexity of the content. This mode is suitable for scenarios where maintaining a certain quality is desired. VBR is selected by default. Note: This field may return null, indicating that no valid value can be obtained. |
| Sar | String | No | Display aspect ratio. Optional values: [1:1, 2:1, default] Default value: default Note: This field may return null, indicating that no valid value can be obtained. |
| NoScenecut | Integer | No | Adaptive I-frame decision. When it is enabled, Media Processing Service will automatically identify transition points between different scenarios in the video (usually they are visually distinct frames, such as those of switching from one shot to another) and adaptively insert keyframes (I-frames) at these points to improve the random accessibility and encoding efficiency of the video. Optional values: 0: Disable the adaptive I-frame decision  1: Enable the adaptive I-frame decision Default value: 0  Note: This field may return null, indicating that no valid value can be obtained. |
| BitDepth | Integer | No | Bit: 8/10 is supported. Default value: 8 Note: This field may return null, indicating that no valid value can be obtained. |
| RawPts | Integer | No | Preservation of original timestamp. Optional values: 0: Disabled 1: Enabled Default value: Disabled Note: This field may return null, indicating that no valid value can be obtained. |
| Compress | Integer | No | Proportional compression bitrate. When it is enabled, the bitrate of the output video will be adjusted according to the proportion. After the compression ratio is entered, the system will automatically calculate the target output bitrate based on the source video bitrate. Compression ratio range: 0-100 Leaving this value blank means it is not enabled by default. Note: This field may return null, indicating that no valid value can be obtained. |
| SegmentSpecificInfo | [SegmentSpecificInfo](#SegmentSpecificInfo) | No | Segment duration at startup. Note: This field may return null, indicating that no valid value can be obtained. |
| ScenarioBased | Integer | No | Whether the template enables scenario-based settings.  0: disable.  1: enable    Default value: 0       Note: The values of SceneType and CompressType fields only take effect when this field value is 1. Note: This field may return null, indicating that no valid value can be obtained. |
| SceneType | String | No | Video scenario. Valid values:  - normal: General transcoding scenario. General transcoding and compression scenario. - pgc: PGC HD TV shows and movies. At the time of compression, focus is placed on the viewing experience of TV shows and movies and ROI encoding is performed according to their characteristics, while high-quality contents of videos and audio are retained.  - materials_video: HD materials. Scenario involving material resources, where requirements for image quality are extremely high and there are many transparent images, with almost no visual loss during compression.  - ugc: UGC content. It is suitable for a wide range of UGC/short video scenarios, with an optimized encoding bitrate for short video characteristics, improved image quality, and enhanced business QOS/QOE metrics.  - e-commerce_video. Fashion show/e-commerce: At the time of compression, emphasis is placed on detail clarity and ROI enhancement, with a particular focus on maintaining the image quality of the face region.  - educational_video. Education. At the time of compression, emphasis is placed on the clarity and readability of text and images to help students better understand the content, ensuring that the teaching content is clearly conveyed.   Default value: normal. Note: To use this value, the value of ScenarioBased must be 1; otherwise, this value will not take effect. Note: This field may return null, indicating that no valid value can be obtained. |
| CompressType | String | No | Transcoding policy. Valid values:  - ultra_compress: Extreme compression. Compared to standard compression, this policy can maximize bitrate compression while ensuring a certain level of image quality, thus greatly saving bandwidth and storage costs.  - standard_compress: Comprehensively optimal. Balances compression ratio and image quality, compressing files as much as possible without a noticeable reduction in subjective image quality. Only audio and video TSC transcoding fees are charged for this policy.  - high_compress: Bitrate priority. Prioritizes reducing file size, which may result in certain image quality loss. Only audio and video TSC transcoding fees are charged for this policy.  - low_compress: Image quality priority. Prioritizes ensuring image quality, and the size of compressed files may be relatively large. Only audio and video TSC transcoding fees are charged for this policy.   Default value: standard_compress.  Note: If you need to watch videos on TV, it is recommended not to use the ultra_compress policy. The billing standard for the ultra_compress policy is TSC transcoding + audio and video enhancement - artifacts removal. Note: To use this value, the value of ScenarioBased must be 1; otherwise, this value will not take effect. Note: This field may return null, indicating that no valid value can be obtained. |

## VideoTemplateInfoForUpdate

Video stream configuration parameter

Used by actions: CreateWorkflow, ModifyTranscodeTemplate, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Codec | String | No | Encoding format for video streams. valid values:. H264: h.264 encoding.. H265: h.265 encoding.. H266: h.266 encoding.. av1: AOMedia Video 1 encoding. vp8: vp8 encoding.. vp9: vp9 encoding.. mpeg2: mpeg2 encoding.. dnxhd: specifies dnxhd encoding.. mv-hevc: mv-hevc encoding..  Note: the av1 encoding container currently only supports mp4, webm, and mkv. Note: H.266 encoding containers currently only support mp4, hls, ts, and mov. Note: VP8 and VP9 encoding containers currently only support webm and mkv. Note: MPEG2 and dnxhd encoding containers currently only support mxf. Note: MV-HEVC encoding containers currently only support mp4, hls, and mov. among them, the hls format supports only mp4 segmentation format and requires the input source to be a panoramic video (with multi-perspective). Note: This field may return null, indicating that no valid values can be obtained. |
| Fps | Integer | No | Video frame rate. Value range: When FpsDenominator is empty, the range is [0, 120], in Hz. When FpsDenominator is not empty, the Fps/FpsDenominator range is [0, 120]. If the value is 0, the frame rate will be the same as that of the source video.Note: This field may return null, indicating that no valid values can be obtained. |
| Bitrate | Integer | No | Bitrate of a video stream, in kbps. Value range: 0 and [128, 100000].If the value is 0, the bitrate of the video will be the same as that of the source video.Note: This field may return null, indicating that no valid values can be obtained. |
| ResolutionAdaptive | String | No | Resolution adaption. Valid values: open: Enabled. When resolution adaption is enabled, `Width` indicates the long side of a video, while `Height` indicates the short side.close: Disabled. When resolution adaption is disabled, `Width` indicates the width of a video, while `Height` indicates the height. Note: When resolution adaption is enabled, `Width` cannot be smaller than `Height`. |
| Width | Integer | No | Maximum value of the video stream width (or long edge) in px. Value range: 0 and [128, 4096]. If both Width and Height are 0, the resolution is the same as the source.If Width is 0 but Height is not 0, the width will be proportionally scaled.If Width is not 0 but Height is 0, the height will be proportionally scaled.If both Width and Height are not 0, the resolution is as specified by the user. Note: If Codec is set to MV-HEVC, the maximum value can be 7680. Note: This field may return null, indicating that no valid value can be obtained. |
| Height | Integer | No | Maximum value of the video stream height (or short edge) in px. Value range: 0 and [128, 4,096]. Note: If Codec is set to MV-HEVC, the maximum value can be 7680. Note: This field may return null, indicating that no valid value can be obtained. |
| Gop | Integer | No | Interval between I-frames (keyframes), which can be customized in frames or seconds. GOP value range: 0 and [1, 100000]. If this parameter is 0, the system will automatically set the GOP length. Note: This field may return null, indicating that no valid value can be obtained. |
| GopUnit | String | No | GOP value unit. Optional values:  frame: indicates frame  second: indicates second Default value: frame Note: This field may return null, indicating that no valid value can be obtained. |
| FillType | String | No | Fill type. "Fill" refers to the way of processing a screenshot when its aspect ratio is different from that of the source video. Valid values:  stretch: Each frame is stretched to fill the entire screen, which may cause the transcoded video to be "flattened" or "stretched".black: Keep the image's original aspect ratio and fill the blank space with black bars.white: The aspect ratio of the video is kept unchanged, and the rest of the edges is filled with white.gauss: applies Gaussian blur to the uncovered area, without changing the image's aspect ratio.  smarttailor: Video images are smartly selected to ensure proportional image cropping. Default value: black.  Note: This field may return null, indicating that no valid value can be obtained. |
| Vcrf | Integer | No | The control factor of video constant bitrate. Value range: [0, 51]. If not specified, it means "auto". It is recommended not to specify this parameter unless necessary. When the Mode parameter is set to VBR, if the Vcrf value is also configured, MPS will process the video in VBR mode, considering both Vcrf and Bitrate parameters to balance video quality, bitrate, transcoding efficiency, and file size. When the Mode parameter is set to CRF, the Bitrate setting will be invalid, and the encoding will be based on the Vcrf value. When the Mode parameter is set to ABR or CBR, the Vcrf value does not need to be configured. Note: When you need to set it to auto, fill in 100.  Note: This field may return null, indicating that no valid value can be obtained. |
| ContentAdaptStream | Integer | No | Whether to enable adaptive encoding. Valid values: 0: Disable1: Enable Default value: 0. If this parameter is set to `1`, multiple streams with different resolutions and bitrates will be generated automatically. The highest resolution, bitrate, and quality of the streams are determined by the values of `width` and `height`, `Bitrate`, and `Vcrf` in `VideoTemplate` respectively. If these parameters are not set in `VideoTemplate`, the highest resolution generated will be the same as that of the source video, and the highest video quality will be close to VMAF 95. To use this parameter or learn about the billing details of adaptive encoding, please contact your sales rep. |
| HlsTime | Integer | No | Average segment duration. Value range: (0-10], unit: second Default value: 10 Note: It is used only in the format of HLS. Note: This field may return null, indicating that no valid value can be obtained. |
| SegmentType | Integer | No | HLS segment type. Valid values: 0: HLS+TS segment2: HLS+TS byte range7: HLS+MP4 segment5: HLS+MP4 byte range Default value: 0  Note: This field is used for normal/Top Speed Codec transcoding settings and does not apply to adaptive bitrate streaming. To configure the segment type for adaptive bitrate streaming, use the outer field. Note: This field may return null, indicating that no valid value can be obtained. |
| FpsDenominator | Integer | No | Denominator of the frame rate. Note: The value must be greater than 0. Note: This field may return null, indicating that no valid values can be obtained. |
| Stereo3dType | String | No | 3D video splicing mode, applicable only to mv-hevc and effective for 3d videos. valid values: side_by_side: the original video content is arranged in a left-right layout. top_bottom: layout arrangement of the original video content from top to bottom. The usage and charges will be reported based on the segmented resolution dimensions. Default value: side_by_side. Note: This field may return null, indicating that no valid value can be obtained. |
| VideoProfile | String | No | Profile, suitable for different scenarios.  baseline: It only supports I/P-frames and non-interlaced scenarios, and is suitable for scenarios such as video calls and mobile videos.  main: It offers I-frames, P-frames, and B-frames, and supports both interlaced and non-interlaced modes. It is mainly used in mainstream audio and video consumption products such as video players and streaming media transmission devices.  high: the highest encoding level, with 8x8 prediction added to the main profile and support for custom quantification. It is widely used in scenarios such as Blu-ray storage and HDTV. default: automatic filling along with the original video  This configuration appears only when the encoding standard is set to H264. Default value: default Note: This field may return null, indicating that no valid value can be obtained. |
| VideoLevel | String | No | Encoder level. Default value: auto ("") If the encoding standard is set to H264, the following options are supported: "", 1, 1.1, 1.2, 1.3, 2, 2.1, 2.2, 3, 3.1, 3.2, 4, 4.1, 4.2, 5, and 5.1.  If the encoding standard is set to H265, the following options are supported: "", 1, 2, 2.1, 3, 3.1, 4, 4.1, 5, 5.1, 5.2, 6, 6.1, 6.2, and 8.5. Note: This field may return null, indicating that no valid value can be obtained. |
| Bframes | Integer | No | Maximum number of consecutive B-frames. The default is auto, and 0 - 16 and -1 are supported. Note:  -1 indicates auto.     Note: This field may return null, indicating that no valid value can be obtained. |
| Mode | String | No | Bitrate control mode. Optional values:  VBR: variable bitrate. The output bitrate is adjusted based on the complexity of the video image, ensuring higher image quality. This mode is suitable for storage scenarios as well as applications with high image quality requirements.  ABR: average bitrate. The average bitrate of the output video is kept stable to the greatest extent, but short-term bitrate fluctuations are allowed. This mode is suitable for scenarios where it is necessary to minimize the overall bitrate while a certain quality is maintained.  CBR: constant bitrate. The output bitrate remains constant during the video encoding process, regardless of changes in image complexity. This mode is suitable for scenarios with strict network bandwidth requirements, such as live streaming.  VCRF: constant rate factor. The video quality is controlled by setting a quality factor, achieving constant quality encoding of videos. The bitrate is automatically adjusted based on the complexity of the content. This mode is suitable for scenarios where maintaining a certain quality is desired.  VBR is selected by default. Note: This field may return null, indicating that no valid value can be obtained. |
| Sar | String | No | Display aspect ratio. Optional values: [1:1, 2:1, default] Default value: default Note: This field may return null, indicating that no valid value can be obtained. |
| NoScenecut | Integer | No | Adaptive I-frame decision. When it is enabled, Media Processing Service will automatically identify transition points between different scenarios in the video (usually they are visually distinct frames, such as those of switching from one shot to another) and adaptively insert keyframes (I-frames) at these points to improve the random accessibility and encoding efficiency of the video. Optional values:  0: Disable the adaptive I-frame decision  1: Enable the adaptive I-frame decision  Default value: 0       Note: This field may return null, indicating that no valid value can be obtained. |
| BitDepth | Integer | No | Bit: 8/10 is supported. Default value: 8     Note: This field may return null, indicating that no valid value can be obtained. |
| RawPts | Integer | No | Preservation of original timestamp. Optional values:  0: Disabled  1: Enabled  Default value: Disabled     Note: This field may return null, indicating that no valid value can be obtained. |
| Compress | Integer | No | Proportional compression bitrate. When it is enabled, the bitrate of the output video will be adjusted according to the proportion. After the compression ratio is entered, the system will automatically calculate the target output bitrate based on the source video bitrate. Compression ratio range: 0-100, optional values: [0-100] and -1  Note: -1 indicates auto.     Note: This field may return null, indicating that no valid value can be obtained. |
| SegmentSpecificInfo | [SegmentSpecificInfo](#SegmentSpecificInfo) | No | Segment duration at startup. Note: This field may return null, indicating that no valid value can be obtained. |
| ScenarioBased | Integer | No | Indicates whether to enable scenario-based settings for the template.  0: Disable.  1: enable    Default value: 0       Note: This value takes effect only when the value of this field is 1. Note: This field may return null, indicating that no valid value can be obtained. |
| SceneType | String | No | Video scenario. Valid values:  - normal: General transcoding scenario. General transcoding and compression scenario. - pgc: PGC HD TV shows and movies. At the time of compression, focus is placed on the viewing experience of TV shows and movies and ROI encoding is performed according to their characteristics, while high-quality contents of videos and audio are retained.  - materials_video: HD materials. Scenario involving material resources, where requirements for image quality are extremely high and there are many transparent images, with almost no visual loss during compression.  - ugc: UGC content. It is suitable for a wide range of UGC/short video scenarios, with an optimized encoding bitrate for short video characteristics, improved image quality, and enhanced business QOS/QOE metrics.  - e-commerce_video. Fashion show/e-commerce: At the time of compression, emphasis is placed on detail clarity and ROI enhancement, with a particular focus on maintaining the image quality of the face region.  - educational_video. Education. At the time of compression, emphasis is placed on the clarity and readability of text and images to help students better understand the content, ensuring that the teaching content is clearly conveyed.   Default value: normal. Note: To use this value, the value of ScenarioBased must be 1; otherwise, this value will not take effect. Note: This field may return null, indicating that no valid value can be obtained. |
| CompressType | String | No | Transcoding policy. Valid values:  - ultra_compress: Extreme compression. Compared to standard compression, this policy can maximize bitrate compression while ensuring a certain level of image quality, thus greatly saving bandwidth and storage costs.  - standard_compress: Comprehensively optimal. Balances compression ratio and image quality, compressing files as much as possible without a noticeable reduction in subjective image quality. Only audio and video TSC transcoding fees are charged for this policy.  - high_compress: Bitrate priority. Prioritizes reducing file size, which may result in certain image quality loss. Only audio and video TSC transcoding fees are charged for this policy.  - low_compress: Image quality priority. Prioritizes ensuring image quality, and the size of compressed files may be relatively large. Only audio and video TSC transcoding fees are charged for this policy.   Default value: standard_compress.  Note: If you need to watch videos on TV, it is recommended not to use the ultra_compress policy. The billing standard for the ultra_compress policy is TSC transcoding + audio and video enhancement - artifacts removal. Note: To use this value, the value of ScenarioBased must be 1; otherwise, this value will not take effect. Note: This field may return null, indicating that no valid value can be obtained. |

## VolumeBalanceConfig

The volume equalization configuration.

Used by actions: CreateTranscodeTemplate, ModifyTranscodeTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Switch | String | No | Whether to enable the feature. Valid values: `ON``OFF`  Default value: `ON`. |
| Type | String | No | The type. Valid values: `loudNorm`: Loudness normalization.`gainControl`: Volume leveling. Default value: `loudNorm`. Note: This field may return null, indicating that no valid values can be obtained. |

## WatermarkInput

The watermark parameters to use in a media processing task.

Used by actions: CreateWorkflow, ProcessMedia, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Definition | Integer | Yes | ID of a watermarking template. |
| RawParameter | [RawWatermarkParameter](#RawWatermarkParameter) | No | Custom watermark parameter, which is valid if `Definition` is 0. This parameter is used in highly customized scenarios. We recommend you use `Definition` to specify the watermark parameter preferably. Custom watermark parameter is not available for screenshot. |
| TextContent | String | No | Text content of up to 100 characters. This field is required only when the watermark type is text. Text watermark is not available for screenshot. |
| SvgContent | String | No | SVG content of up to 2,000,000 characters. This field is required only when the watermark type is `SVG`. SVG watermark is not available for screenshot. |
| StartTimeOffset | Float | No | Start time offset of a watermark, in seconds. If not set or set to 0, a watermark starts appearing when a video starts. If not set or set to 0, a watermark starts appearing when a video starts.If the value is greater than 0 (for example, n), a watermark will appear at second n of a video.If the value is less than 0 (for example, -n), a watermark will appear n seconds before the end of a video.  Note: It is only used for video scenarios. Screenshots are not supported. |
| EndTimeOffset | Float | No | End time offset of a watermark, in seconds. If not set or set to 0, a watermark will last until the end of a video.If the value is greater than 0 (for example, n), a watermark will disappear at second n.If the value is less than 0 (for example, -n), a watermark will disappear n seconds before the end of a video.  Note: It is only used for video scenarios. Screenshots are not supported. |

## WatermarkTemplate

Details of a watermarking template

Used by actions: DescribeWatermarkTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Definition | Integer | Unique ID of a watermarking template. |
| Type | String | Watermark type. Valid values: image: Image watermark;text: Text watermark. |
| Name | String | Name of a watermarking template. |
| Comment | String | Template description. |
| XPos | String | Horizontal position of the origin of the watermark image relative to the origin of the video. If the string ends in %, the `Left` edge of the watermark will be at the position of the specified percentage of the video width; for example, `10%` means that the `Left` edge is at 10% of the video width;If the string ends in px, the `Left` edge of the watermark will be at the position of the specified px of the video width; for example, `100px` means that the `Left` edge is at the position of 100 px. |
| YPos | String | Vertical position of the origin of the watermark image relative to the origin of the video. If the string ends in %, the `Top` edge of the watermark will beat the position of the specified percentage of the video height; for example, `10%` means that the `Top` edge is at 10% of the video height;If the string ends in px, the `Top` edge of the watermark will be at the position of the specified px of the video height; for example, `100px` means that the `Top` edge is at the position of 100 px. |
| ImageTemplate | [ImageWatermarkTemplate](#ImageWatermarkTemplate) | Image watermarking template. This field is valid only when `Type` is `image`. Note: This field may return null, indicating that no valid values can be obtained. |
| TextTemplate | [TextWatermarkTemplateInput](#TextWatermarkTemplateInput) | Text watermarking template. This field is valid only when `Type` is `text`. Note: This field may return null, indicating that no valid values can be obtained. |
| SvgTemplate | [SvgWatermarkInput](#SvgWatermarkInput) | SVG watermarking template. This field is valid when `Type` is `svg`. Note: This field may return null, indicating that no valid values can be obtained. |
| CreateTime | String | Creation time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a template in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| CoordinateOrigin | String | Origin position. Valid values: TopLeft: indicates that the coordinate origin is at the top left corner of the video image and the watermark origin is at the top left corner of the image or text.TopRight: indicates that the coordinate origin is at the top right corner of the video image and the watermark origin is at the top right corner of the image or text.BottomLeft: indicates that the coordinate origin is at the bottom left corner of the video image and the watermark origin is at the bottom left corner of the image or text.BottomRight: indicates that the coordinate origin is at the bottom right corner of the video image and the watermark origin is at the bottom right corner of the image or text. |

## WordResult

Word information.

Used by actions: DescribeBatchTaskDetail, DescribeTaskDetail, ParseNotification, RecognizeAudio.

| Name | Type | Description |
| --- | --- | --- |
| Word | String | Word text. |
| Start | Float | Word start timestamp, in seconds. |
| End | Float | Word end timestamp, in seconds. |
| Trans | String | Text after translation. |

## WorkflowInfo

Workflow information details.

Used by actions: DescribeWorkflows.

| Name | Type | Description |
| --- | --- | --- |
| WorkflowId | Integer | Workflow ID. |
| WorkflowName | String | Workflow name. |
| Status | String | Workflow status. Valid values: Enabled: Enabled,Disabled: Disabled. |
| Trigger | [WorkflowTrigger](#WorkflowTrigger) | Input rule bound to a workflow. If an uploaded video hits the rule for the object, the workflow will be triggered. |
| OutputStorage | [TaskOutputStorage](#TaskOutputStorage) | The location to save the media processing output file. Note: This field may return null, indicating that no valid value can be obtained. |
| MediaProcessTask | [MediaProcessTaskInput](#MediaProcessTaskInput) | The media processing parameters to use. Note: This field may return null, indicating that no valid value can be obtained. |
| AiContentReviewTask | [AiContentReviewTaskInput](#AiContentReviewTaskInput) | Type parameter of a video content audit task. Note: This field may return null, indicating that no valid values can be obtained. |
| AiAnalysisTask | [AiAnalysisTaskInput](#AiAnalysisTaskInput) | Video content analysis task parameter. |
| AiRecognitionTask | [AiRecognitionTaskInput](#AiRecognitionTaskInput) | Type parameter of a video content recognition task. Note: This field may return null, indicating that no valid values can be obtained. |
| TaskNotifyConfig | [TaskNotifyConfig](#TaskNotifyConfig) | Event notification information of a task. If this parameter is left empty, no event notifications will be obtained. Note: This field may return null, indicating that no valid values can be obtained. |
| TaskPriority | Integer | Task flow priority. The higher the value, the higher the priority. Value range: [-10, 10]. If this parameter is left empty, 0 will be used. |
| OutputDir | String | The directory to save the media processing output file, such as `/movie/201907/`. |
| CreateTime | String | Creation time of a workflow in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |
| UpdateTime | String | Last modified time of a workflow in [ISO date format](https://intl.cloud.tencent.com/document/product/266/11732?from_cn_redirect=1#iso-.E6.97.A5.E6.9C.9F.E6.A0.BC.E5.BC.8F). |

## WorkflowTask

The information of the media processing task.

Used by actions: DescribeTaskDetail, ParseNotification.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | The media processing task ID. |
| Status | String | Task flow status. Valid values: PROCESSING: Processing;FINISH: Completed. |
| ErrCode | Integer | If the value returned is not 0, there was a source error. If 0 is returned, refer to the error codes of the corresponding task type. |
| Message | String | Except those for source errors, error messages vary with task type. |
| InputInfo | [MediaInputInfo](#MediaInputInfo) | The information of the file processed. Note: This field may return null, indicating that no valid value can be obtained. |
| MetaData | [MediaMetaData](#MediaMetaData) | Metadata of a source video. Note: This field may return null, indicating that no valid values can be obtained. |
| MediaProcessResultSet | Array of [MediaProcessTaskResult](#MediaProcessTaskResult) | The execution status and result of the media processing task. |
| AiContentReviewResultSet | Array of [AiContentReviewResult](#AiContentReviewResult) | Execution status and result of a video content audit task. |
| AiAnalysisResultSet | Array of [AiAnalysisResult](#AiAnalysisResult) | Execution status and result of video content analysis task. |
| AiRecognitionResultSet | Array of [AiRecognitionResult](#AiRecognitionResult) | Execution status and result of a video content recognition task. |
| AiQualityControlTaskResult | [ScheduleQualityControlTaskResult](#ScheduleQualityControlTaskResult) | Execution status and results of a media quality inspection task. Note: This field may return null, indicating that no valid values can be obtained. |
| SmartSubtitlesTaskResult | Array of [SmartSubtitlesResult](#SmartSubtitlesResult) | Execution result of the smart subtitle task. Note: This field may return null, indicating that no valid value can be obtained. |
| SmartEraseTaskResult | [SmartEraseTaskResult](#SmartEraseTaskResult) | Execution result of the smart erasure task. Note: This field may return null, indicating that no valid value can be obtained. |

## WorkflowTrigger

Input rule. If an uploaded video hits the rule, the workflow will be triggered.

Used by actions: CreateSchedule, CreateWorkflow, DescribeSchedules, DescribeWorkflows, ModifySchedule, ResetWorkflow.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Type | String | Yes | The trigger type. Valid values: `CosFileUpload`: Tencent Cloud COS trigger.`AwsS3FileUpload`: AWS S3 trigger. Currently, this type is only supported for transcoding tasks and schemes (not supported for workflows). |
| CosFileUploadTrigger | [CosFileUploadTrigger](#CosFileUploadTrigger) | No | This parameter is required and valid when `Type` is `CosFileUpload`, indicating the COS trigger rule. Note: This field may return null, indicating that no valid values can be obtained. |
| AwsS3FileUploadTrigger | [AwsS3FileUploadTrigger](#AwsS3FileUploadTrigger) | No | The AWS S3 trigger. This parameter is valid and required if `Type` is `AwsS3FileUpload`.  Note: Currently, the key for the AWS S3 bucket, the trigger SQS queue, and the callback SQS queue must be the same. Note: This field may return null, indicating that no valid values can be obtained. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33690](https://www.tencentcloud.com/document/product/1041/33690)*
