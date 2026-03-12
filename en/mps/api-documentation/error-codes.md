# Error Codes

## Feature Description

If there is an Error field in the response, it means that the API call failed. For example:

```
 {
    "Response": {
        "Error": {
            "Code": "AuthFailure.SignatureFailure",
            "Message": "The provided credentials could not be validated. Please check your signature is correct."
        },
        "RequestId": "ed93f3cb-f35e-473f-b9f3-0d451b8b79c6"
    }
}
```

Code in Error indicates the error code, and Message indicates the specific information of the error.

## Error Code List

### Common Error Codes

| Error Code | Description |
| --- | --- |
| ActionOffline | This API has been deprecated. |
| AuthFailure.InvalidAuthorization | `Authorization` in the request header is invalid. |
| AuthFailure.InvalidSecretId | Invalid key (not a TencentCloud API key type). |
| AuthFailure.MFAFailure | MFA failed. |
| AuthFailure.SecretIdNotFound | Key does not exist. Check if the key has been deleted or disabled in the console, and if not, check if the key is correctly entered. Note that whitespaces should not exist before or after the key. |
| AuthFailure.SignatureExpire | Signature expired. Timestamp and server time cannot differ by more than five minutes. Please ensure your current local time matches the standard time. |
| AuthFailure.SignatureFailure | Invalid signature. Signature calculation error. Please ensure you’ve followed the signature calculation process described in the Signature API documentation. |
| AuthFailure.TokenFailure | Token error. |
| AuthFailure.UnauthorizedOperation | The request is not authorized. For more information, see the [CAM](https://intl.cloud.tencent.com/document/product/598) documentation. |
| DryRunOperation | DryRun Operation. It means that the request would have succeeded, but the DryRun parameter was used. |
| FailedOperation | Operation failed. |
| InternalError | Internal error. |
| InvalidAction | The API does not exist. |
| InvalidParameter | Incorrect parameter. |
| InvalidParameterValue | Invalid parameter value. |
| InvalidRequest | The multipart format of the request body is incorrect. |
| IpInBlacklist | Your IP is in uin IP blacklist. |
| IpNotInWhitelist | Your IP is not in uin IP whitelist. |
| LimitExceeded | Quota limit exceeded. |
| MissingParameter | A parameter is missing. |
| NoSuchProduct | The product does not exist. |
| NoSuchVersion | The API version does not exist. |
| RequestLimitExceeded | The number of requests exceeds the frequency limit. |
| RequestLimitExceeded.GlobalRegionUinLimitExceeded | Uin exceeds the frequency limit. |
| RequestLimitExceeded.IPLimitExceeded | The number of ip requests exceeds the frequency limit. |
| RequestLimitExceeded.UinLimitExceeded | The number of uin requests exceeds the frequency limit. |
| RequestSizeLimitExceeded | The request size exceeds the upper limit. |
| ResourceInUse | Resource is in use. |
| ResourceInsufficient | Insufficient resource. |
| ResourceNotFound | The resource does not exist. |
| ResourceUnavailable | Resource is unavailable. |
| ResponseSizeLimitExceeded | The response size exceeds the upper limit. |
| ServiceUnavailable | Service is unavailable now. |
| UnauthorizedOperation | Unauthorized operation. |
| UnknownParameter | Unknown parameter. |
| UnsupportedOperation | Unsupported operation. |
| UnsupportedProtocol | HTTP(S) request protocol error; only GET and POST requests are supported. |
| UnsupportedRegion | API does not support the requested region. |

### Service Error Codes

| Error Code | Description |
| --- | --- |
| FailedOperation.BucketNotifyAlreadyExist | Operation failed: notification has already been set for the bucket. |
| FailedOperation.CosStatusInavlid | Operation failed: COS service is suspended. |
| FailedOperation.GenerateResource | Resource generation failed. |
| FailedOperation.GetSourceNotify | Operation failed: Error getting the source notification. |
| FailedOperation.InvalidMpsUser | Operation failed: unauthorized MPS user. |
| FailedOperation.InvalidUser | Operation failed: invalid user. |
| FailedOperation.NetWorkError | Operation failed due to a network error. |
| FailedOperation.SetSourceNotify | Operation failed: Error setting the source notification. |
| InternalError.AccessDBError | Data error. |
| InternalError.GenDefinition | Internal error: failed to generate template ID. |
| InternalError.RecognitionError | Recognition error. |
| InternalError.UploadWatermarkError | Internal error: failed to upload watermark image. |
| InvalidParameter.Id | InvalidParameter.Id |
| InvalidParameter.NotFound | InvalidParameter.NotFound |
| InvalidParameterValue.AsrHotWordsConfigure | The value of the hotword lexicon configuration parameter is incorrect. |
| InvalidParameterValue.AsrHotWordsLibraryId | The value of the hotword lexicon ID parameter is incorrect. |
| InvalidParameterValue.AsrHotWordsSwitch | The value of the hotword lexicon switch parameter is incorrect. |
| InvalidParameterValue.AudioBitrate | Parameter error: Audio stream bitrate. |
| InvalidParameterValue.AudioChannel | Incorrect parameter value: AudioChannel. |
| InvalidParameterValue.AudioCodec | Parameter error: audio stream codec. |
| InvalidParameterValue.AudioData | Invalid audio data. |
| InvalidParameterValue.AudioDataTooLong | The audio data is too long. |
| InvalidParameterValue.AudioFormat | Unsupported audio data format. |
| InvalidParameterValue.AudioSampleRate | Parameter error: audio stream sample rate. |
| InvalidParameterValue.AutoAreas | The configuration for the automatic erasing area of the erasing template is incorrect. |
| InvalidParameterValue.Bitrate | Invalid audio/video bitrate. |
| InvalidParameterValue.BlockConfidence | Incorrect parameter value: the value of the `BlockConfidence` parameter is invalid. |
| InvalidParameterValue.ClassifcationConfigure | Incorrect parameter value: the control field parameter for intelligent categorization is incorrect. |
| InvalidParameterValue.Codec | Invalid audio/video codec. |
| InvalidParameterValue.ColumnCount | Incorrect parameter value: ColumnCount. |
| InvalidParameterValue.Comment | Parameter error: template description. |
| InvalidParameterValue.Container | Parameter error: container format. |
| InvalidParameterValue.ContainerType | Incorrect parameter value: ContainerType. |
| InvalidParameterValue.CoordinateOrigin | Incorrect parameter value: CoordinateOrigin. |
| InvalidParameterValue.CoverConfigure | Incorrect parameter value: the control field parameter for intelligent cover generation is incorrect. |
| InvalidParameterValue.CustomAreas | The specified area of the erasing template is incorrect. |
| InvalidParameterValue.DefaultLibraryLabelSet | Incorrect parameter value: the default face library filter tag is invalid. |
| InvalidParameterValue.Definition | Parameter error: Definition. |
| InvalidParameterValue.Definitions | Parameter error: Definitions. |
| InvalidParameterValue.DeleteDefaultTemplate | Incorrect parameter value: the default template cannot be deleted. |
| InvalidParameterValue.DestinationLanguage | DestinationLanguage parameter error. |
| InvalidParameterValue.DisableHigherVideoBitrate | Invalid switch value used to prohibit transcoding from low bitrate to high bitrate. |
| InvalidParameterValue.DisableHigherVideoResolution | Invalid switch value used to prohibit transcoding from low resolution to high resolution. |
| InvalidParameterValue.DuplicatedTextContent | Duplicated watermark text. |
| InvalidParameterValue.EmptyDetectItem | The enabled detection items of the template are empty. |
| InvalidParameterValue.ErasePrivacyConfig | The privacy protection configuration of the erasing template is incorrect. |
| InvalidParameterValue.EraseSubtitleConfig | The subtitle erasing configuration of the erasing template is incorrect. |
| InvalidParameterValue.EraseType | The erasing type of the erasing template is incorrect. |
| InvalidParameterValue.EraseWatermarkConfig | The watermark erasing configuration of the erasing template is incorrect. |
| InvalidParameterValue.FaceDuplicate | Incorrect parameter value: duplicated face. |
| InvalidParameterValue.FaceLibrary | Incorrect parameter value: invalid face library parameter. |
| InvalidParameterValue.FaceScore | Incorrect parameter value: the value of the face score parameter is invalid. |
| InvalidParameterValue.FillType | Invalid parameter: incorrect fill type. |
| InvalidParameterValue.Format | Incorrect parameter value: Format. |
| InvalidParameterValue.FormatWebpLackWidthAndHeight | Incorrect parameter value: `Format` is `webp`, but both `Width` and `Height` are empty. |
| InvalidParameterValue.FormatWebpWidthAndHeightBothZero | Incorrect parameter value: when `Format` is `webp`, `Width` and `Height` cannot be both 0. |
| InvalidParameterValue.Fps | Parameter error: video frame rate. |
| InvalidParameterValue.FrameTagConfigure | Incorrect parameter value: the control field parameter for intelligent frame-specific tagging is incorrect. |
| InvalidParameterValue.FunctionArg | Incorrect parameter value: FunctionArg. |
| InvalidParameterValue.FunctionName | Incorrect parameter value: FunctionName. |
| InvalidParameterValue.Gop | Invalid GOP value. |
| InvalidParameterValue.Height | Parameter error: height. |
| InvalidParameterValue.HotWordsNotExist | Parameter error. The hotword lexicon does not exist. |
| InvalidParameterValue.HotwordsFormatError | Hot word vocabulary format error. see the hot word configuration instruction document (https://intl.cloud.tencent.com/document/product/862/116244?from_cn_redirect=1#afc37e17-2786-4289-9bc3-8e24435d3f45). |
| InvalidParameterValue.ImageContent | Invalid ImageContent |
| InvalidParameterValue.ImageTemplate | Parameter error: image watermarking template. |
| InvalidParameterValue.InputInfo | Incorrect input parameters. |
| InvalidParameterValue.InvalidContent | The value of the parsed `Content` is invalid. |
| InvalidParameterValue.InvalidOperationType | Invalid operation type. |
| InvalidParameterValue.LabelSet | Incorrect parameter value: invalid `LabelSet` value. |
| InvalidParameterValue.Limit | Parameter error: Limit. |
| InvalidParameterValue.ModifyDefaultTemplate | Incorrect parameter value: the default template cannot be modified. |
| InvalidParameterValue.Name | Incorrect parameter value: `Name` exceeds the length limit. |
| InvalidParameterValue.NotProcessingTask | Tasks not in processing status are not supported. |
| InvalidParameterValue.ObjectLibrary | Incorrect parameter value: object library parameter is invalid. |
| InvalidParameterValue.OcrSwitch | Incorrect parameter value: the OcrSwitch parameter value is invalid. |
| InvalidParameterValue.PicFormatError | Incorrect parameter value: incorrect face image format. |
| InvalidParameterValue.PrivacyModel | The privacy protection model of the erasing template is incorrect. |
| InvalidParameterValue.PrivacyTargets | The privacy protection target of the erasing template is incorrect. |
| InvalidParameterValue.Quality | Incorrect parameter value: Quality. |
| InvalidParameterValue.RemoveAudio | Incorrect parameter value: RemoveAudio. |
| InvalidParameterValue.RemoveVideo | Incorrect parameter value: RemoveVideo. |
| InvalidParameterValue.RepeatType | Parameter error: invalid `RepeatType`. |
| InvalidParameterValue.Resolution | Parameter error: Incorrect resolution. |
| InvalidParameterValue.ResolutionAdaptive | Invalid ResolutionAdaptive |
| InvalidParameterValue.ReviewConfidence | Incorrect parameter value: The value of the `ReviewConfidence` parameter is invalid. |
| InvalidParameterValue.RowCount | Incorrect parameter value: RowCount. |
| InvalidParameterValue.SampleInterval | Incorrect parameter value: SampleInterval. |
| InvalidParameterValue.SampleRate | Invalid audio sample rate. |
| InvalidParameterValue.SampleType | Incorrect parameter value: SampleType. |
| InvalidParameterValue.Service | A service parameter value error occurs. |
| InvalidParameterValue.SessionContextTooLong | `SessionContext` is too long. |
| InvalidParameterValue.SessionId | The deduplication ID already exists. The request is removed due to duplication. |
| InvalidParameterValue.SessionIdTooLong | `SessionId` is too long. |
| InvalidParameterValue.SoundSystem | Invalid parameter: incorrect audio channel system. |
| InvalidParameterValue.SourceLanguage | SourceLanguage parameter error. |
| InvalidParameterValue.SourceText | A SourceText parameter error occurs. |
| InvalidParameterValue.SrcFile | Source file error. |
| InvalidParameterValue.SubtitleEraseMethod | The subtitle erasing method of the erasing template is incorrect. |
| InvalidParameterValue.SubtitleFormat | Incorrect parameter value: The value of the `SubtitleFormat` parameter is invalid. |
| InvalidParameterValue.SubtitleLang | The language for the subtitle erasing of the erasing template is incorrect. |
| InvalidParameterValue.SubtitleModel | The subtitle erasing model of the erasing template is incorrect. |
| InvalidParameterValue.SubtitleType | The value of the subtitle language type is incorrect. |
| InvalidParameterValue.SvgTemplate | Incorrect parameter value: SVG is empty. |
| InvalidParameterValue.SvgTemplateHeight | Incorrect parameter value: SVG height. |
| InvalidParameterValue.SvgTemplateWidth | Incorrect parameter value: SVG width. |
| InvalidParameterValue.Switch | Incorrect parameter value: invalid `Switch` value. |
| InvalidParameterValue.TEHDType | Incorrect parameter value: invalid `TEHD Type` . |
| InvalidParameterValue.TagConfigure | Incorrect parameter value: the control field parameter for intelligent tagging is incorrect. |
| InvalidParameterValue.TaskId | The task ID does not exist. |
| InvalidParameterValue.TextAlpha | Parameter error: text transparency. |
| InvalidParameterValue.TextContent | A TextContent parameter value error occurs. |
| InvalidParameterValue.TextTemplate | Parameter error: text template. |
| InvalidParameterValue.TransDstLang | The configuration for the translation target language is incorrect under the smart erasing - subtitle erasing template. |
| InvalidParameterValue.TransSwitch | Incorrect parameter value: the TransSwitch parameter value is invalid. |
| InvalidParameterValue.TranslateDstLanguage | The value of the target language parameter is incorrect. |
| InvalidParameterValue.TranslateSwitch | The value of the translation switch parameter is incorrect. |
| InvalidParameterValue.Type | Parameter error: incorrect `Type` value. |
| InvalidParameterValue.UnknownCategory | Unknown detection category. |
| InvalidParameterValue.UserDefineLibraryLabelSet | Incorrect parameter value: the custom face library filter tag is invalid. |
| InvalidParameterValue.VideoBitrate | Parameter error: video stream bitrate. |
| InvalidParameterValue.VideoCodec | Parameter error: video stream codec. |
| InvalidParameterValue.VideoSrcLanguage | The value of the video source language parameter is incorrect. |
| InvalidParameterValue.WatermarkEraseMethod | The watermark erasing method of the erasing template is incorrect. |
| InvalidParameterValue.WatermarkModel | The watermark erasing model of the erasing template is incorrect. |
| InvalidParameterValue.Width | Parameter error: Wwdth. |
| InvalidParameterValue.XPos | The horizontal position of the origin of the watermark relative to the origin of coordinates of the video. % and px formats are supported. |
| InvalidParameterValue.YPos | The vertical position of the origin of the watermark relative to the origin of coordinates of the video. % and px formats are supported. |
| LimitExceeded.TooMuchHotWords | The number of created hotword lexicons has reached the default upper limit. |
| LimitExceeded.TooMuchLargeHotWords | The number of created large hotword lexicons has reached the upper limit. |
| LimitExceeded.TooMuchTemplate | Limit reached: the number of templates exceeds the limit. |
| ResourceNotFound.CosBucketNameInvalid | The resource does not exist: invalid COS bucket name. |
| ResourceNotFound.CosBucketNotExist | The resource does not exist: the COS bucket does not exist. |
| ResourceNotFound.Person | The resource does not exist: figure. |
| ResourceNotFound.TemplateNotExist | The resource does not exist: the template does not exist. |
| ResourceNotFound.UserUnregister | The user is not registered. |
| ResourceNotFound.Word | The resource does not exist: Keyword. |
| UnsupportedOperation.TextTooLong | The text for a single request exceeds the length limit. |


---
*Source: [https://www.tencentcloud.com/document/product/1041/33691](https://www.tencentcloud.com/document/product/1041/33691)*
