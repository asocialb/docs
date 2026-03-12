# Data Types

## BandwidthInfo

Bandwidth information

Used by actions: DescribeDeliverBandwidthList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Format of return value: yyyy-mm-dd HH:MM:SS The time accuracy matches with the query granularity. |
| Bandwidth | Float | Bandwidth. |

## BatchDomainOperateErrors

Error information for domains that a batch domain operation API fails to operate.

Used by actions: ModifyLiveDomainCertBindings.

| Name | Type | Description |
| --- | --- | --- |
| DomainName | String | The domain that the API failed to operate. |
| Code | String | The API 3.0 error code. |
| Message | String | The API 3.0 error message. |

## BillDataInfo

Bandwidth and traffic information.

Used by actions: DescribeBillBandwidthAndFluxList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Time point in the format of `yyyy-mm-dd HH:MM:SS`. |
| Bandwidth | Float | Bandwidth in Mbps. |
| Flux | Float | Traffic in MB. |
| PeakTime | String | Time point of peak value in the format of `yyyy-mm-dd HH:MM:SS`. As raw data is at a 5-minute granularity, if data at a 1-hour or 1-day granularity is queried, the time point of peak bandwidth value at the corresponding granularity will be returned. |

## CallBackRuleInfo

Rule information

Used by actions: DescribeLiveCallbackRules.

| Name | Type | Description |
| --- | --- | --- |
| CreateTime | String | The rule creation time. Note: Beijing time (UTC+8) is used. |
| UpdateTime | String | The rule update time. Note: Beijing time (UTC+8) is used. |
| TemplateId | Integer | Template ID. |
| DomainName | String | Push domain name. |
| AppName | String | Push path. |

## CallBackTemplateInfo

Callback template information.

Used by actions: DescribeLiveCallbackTemplate, DescribeLiveCallbackTemplates.

| Name | Type | Description |
| --- | --- | --- |
| TemplateId | Integer | Template ID. |
| TemplateName | String | Template name. |
| Description | String | Description. |
| StreamBeginNotifyUrl | String | Stream starting callback URL. |
| StreamMixNotifyUrl | String | Stream mixing callback URL (disused) |
| StreamEndNotifyUrl | String | Interruption callback URL. |
| RecordNotifyUrl | String | Recording callback URL. |
| SnapshotNotifyUrl | String | Screencapturing callback URL. |
| PornCensorshipNotifyUrl | String | Porn detection callback URL. |
| CallbackKey | String | Callback authentication key. |
| PushExceptionNotifyUrl | String | The push error callback URL. Note: This field may return null, indicating that no valid values can be obtained. |
| AudioAuditNotifyUrl | String | The audio/video moderation callback URL. Note: This field may return null, indicating that no valid values can be obtained. |

## CdnPlayStatData

Downstream playback statistical metrics

Used by actions: DescribeGroupProIspPlayInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Time point in the format of `yyyy-mm-dd HH:MM:SS`. |
| Bandwidth | Float | Bandwidth in Mbps. |
| Flux | Float | Traffic in MB. |
| Request | Integer | Number of new requests. |
| Online | Integer | Number of concurrent connections. |

## CertInfo

Certificate information.

Used by actions: DescribeLiveCert, DescribeLiveCerts.

| Name | Type | Description |
| --- | --- | --- |
| CertId | Integer | Certificate ID. |
| CertName | String | Certificate name. |
| Description | String | Description. |
| CreateTime | String | The creation time in UTC format. Note: Beijing time (UTC+8) is used. |
| HttpsCrt | String | Certificate content. |
| CertType | Integer | Certificate type. 0: user-added certificate 1: Tencent Cloud-hosted certificate |
| CertExpireTime | String | The certificate expiration time in UTC format. Note: Beijing time (UTC+8) is used. |
| DomainList | Array of String | List of domain names that use this certificate. |

## ClientIpPlaySumInfo

Aggregated playback information of client IP.

Used by actions: DescribeTopClientIpSumInfoList.

| Name | Type | Description |
| --- | --- | --- |
| ClientIp | String | Client IP in dotted-decimal notation. |
| Province | String | District where the client is located. |
| TotalFlux | Float | Total traffic. |
| TotalRequest | Integer | Total number of requests. |
| TotalFailedRequest | Integer | Total number of failed requests. |
| CountryArea | String | Country/region where the client is located. |

## CommonMixControlParams

General stream mix control parameter

Used by actions: CreateCommonMixStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UseMixCropCenter | Integer | No | Value range: [0,1].  If 1 is entered, when the layer resolution in the parameter is different from the actual video resolution, the video will be automatically cropped according to the resolution set by the layer. |
| AllowCopy | Integer | No | Value range: [0,1]. If this parameter is set to 1, when both `InputStreamList` and `OutputParams.OutputStreamType` are set to 1, you can copy a stream instead of canceling it. |
| PassInputSei | Integer | No | Valid values: 0, 1 If you set this parameter to 1, SEI (Supplemental Enhanced Information) of the input streams will be passed through. |

## CommonMixCropParams

General stream mix input crop parameter.

Used by actions: CreateCommonMixStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| CropWidth | Float | No | Crop width. Value range: [0,2000]. |
| CropHeight | Float | No | Crop height. Value range: [0,2000]. |
| CropStartLocationX | Float | No | Starting crop X coordinate. Value range: [0,2000]. |
| CropStartLocationY | Float | No | Starting crop Y coordinate. Value range: [0,2000]. |

## CommonMixInputParam

General stream mix input parameter.

Used by actions: CreateCommonMixStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| InputStreamName | String | Yes | Input stream name, which can contain up to 80 bytes of letters, digits, and underscores. The value should be the name of an input stream for stream mix when `LayoutParams.InputType` is set to `0` (audio and video), `4` (pure audio), or `5` (pure video). The value can be a random name for identification, such as `Canvas1` or `Picture1`, when `LayoutParams.InputType` is set to `2` (image) or `3` (canvas). |
| LayoutParams | [CommonMixLayoutParams](#CommonMixLayoutParams) | Yes | Input stream layout parameter. |
| CropParams | [CommonMixCropParams](#CommonMixCropParams) | No | Input stream crop parameter. |

## CommonMixLayoutParams

General stream mix layout parameter.

Used by actions: CreateCommonMixStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ImageLayer | Integer | Yes | Input layer. Value range: [1,16] (1) For the background stream, i.e., the room owner’s image or the canvas, set this parameter to `1`. (2) This parameter is required for audio-only stream mixing as well. Note that two inputs cannot have the same `ImageLayer` value. |
| InputType | Integer | No | Input type. Value range: [0,5]. If this parameter is left empty, 0 will be used by default. 0: the input stream is audio/video. 2: the input stream is image. 3: the input stream is canvas.  4: the input stream is audio. 5: the input stream is pure video. |
| ImageHeight | Float | No | Output height of input video image. Value range: Pixel: [0,2000] Percentage: [0.01,0.99] If this parameter is left empty, the input stream height will be used by default. If percentage is used, the expected output is (percentage * background height). |
| ImageWidth | Float | No | Output width of input video image. Value range: Pixel: [0,2000] Percentage: [0.01,0.99] If this parameter is left empty, the input stream width will be used by default. If percentage is used, the expected output is (percentage * background width). |
| LocationX | Float | No | X-axis offset of input in output video image. Value range: Pixel: [0,2000] Percentage: [0.01,0.99] If this parameter is left empty, 0 will be used by default. Horizontal offset from the top-left corner of main host background video image.  If percentage is used, the expected output is (percentage * background width). |
| LocationY | Float | No | Y-axis offset of input in output video image. Value range: Pixel: [0,2000] Percentage: [0.01,0.99] If this parameter is left empty, 0 will be used by default. Vertical offset from the top-left corner of main host background video image.  If percentage is used, the expected output is (percentage * background width) |
| Color | String | No | When `InputType` is 3 (canvas), this value indicates the canvas color. Commonly used colors include: Red: 0xcc0033. Yellow: 0xcc9900. Green: 0xcccc33. Blue: 0x99CCFF. Black: 0x000000. White: 0xFFFFFF. Gray: 0x999999 |
| WatermarkId | Integer | No | When `InputType` is 2 (image), this value is the watermark ID. |

## CommonMixOutputParams

General stream mix output parameter.

Used by actions: CreateCommonMixStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| OutputStreamName | String | Yes | Output stream name. |
| OutputStreamType | Integer | No | Output stream type. Valid values: [0,1]. If this parameter is left empty, 0 will be used by default. If the output stream is a stream in the input stream list, enter 0. If you want the stream mix result to be a new stream, enter 1. If this value is 1, `output_stream_id` cannot appear in `input_stram_list`, and there cannot be a stream with the same ID on the LVB backend. |
| OutputStreamBitRate | Integer | No | The output bitrate. Value range: 1-10000. If you do not specify this, the system will select a bitrate automatically. |
| OutputStreamGop | Integer | No | Output stream GOP size. Value range: [1,10]. If this parameter is left empty, the system will automatically determine. |
| OutputStreamFrameRate | Integer | No | Output stream frame rate. Value range: [1,60]. If this parameter is left empty, the system will automatically determine. |
| OutputAudioBitRate | Integer | No | Output stream audio bitrate. Value range: [1,500] If this parameter is left empty, the system will automatically determine. |
| OutputAudioSampleRate | Integer | No | Output stream audio sample rate. Valid values: [96000, 88200, 64000, 48000, 44100, 32000,24000, 22050, 16000, 12000, 11025, 8000]. If this parameter is left empty, the system will automatically determine. |
| OutputAudioChannels | Integer | No | Output stream audio sound channel. Valid values: [1,2]. If this parameter is left empty, the system will automatically determine. |
| MixSei | String | No | SEI information in output stream. If there are no special needs, leave it empty. |

## ConcurrentRecordStreamNum

Number of concurrent recording channels

Used by actions: DescribeConcurrentRecordStreamNum, DescribeUploadStreamNums.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Time point. |
| Num | Integer | Number of channels. |

## DayStreamPlayInfo

Stream playback information

Used by actions: DescribeStreamPlayInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Data point in time in the format of `yyyy-mm-dd HH:MM:SS`. |
| Bandwidth | Float | Bandwidth in Mbps. |
| Flux | Float | Traffic in MB. |
| Request | Integer | Number of requests. |
| Online | Integer | Number of online viewers. |

## DelayInfo

Delayed playback information.

Used by actions: DescribeLiveDelayInfoList.

| Name | Type | Description |
| --- | --- | --- |
| DomainName | String | Push domain name. |
| AppName | String | Push path, which is the same as the   `AppName` in push and playback addresses and is `live` by default. |
| StreamName | String | Stream name. |
| DelayInterval | Integer | Delay time in seconds. |
| CreateTime | String | Creation time in UTC time. Note: the difference between UTC time and Beijing time is 8 hours. Example: 2019-06-18T12:00:00Z (i.e., June 18, 2019 20:00:00 Beijing time). |
| ExpireTime | String | Expiration time in UTC time. Note: the difference between UTC time and Beijing time is 8 hours. Example: 2019-06-18T12:00:00Z (i.e., June 18, 2019 20:00:00 Beijing time). |
| Status | Integer | Current status: -1: expired. 1: in effect. |

## DomainCertInfo

Domain name certificate information

Used by actions: DescribeLiveDomainCert.

| Name | Type | Description |
| --- | --- | --- |
| CertId | Integer | Certificate ID. |
| CertName | String | Certificate name. |
| Description | String | Description. |
| CreateTime | String | The creation time in UTC format. Note: Beijing time (UTC+8) is used. |
| HttpsCrt | String | Certificate content. |
| CertType | Integer | Certificate type. 0: user-added certificate 1: Tencent Cloud-hosted certificate. |
| CertExpireTime | String | The certificate expiration time in UTC format. Note: Beijing time (UTC+8) is used. |
| DomainName | String | Domain name that uses this certificate. |
| Status | Integer | Certificate status. |
| CertDomains | Array of String | List of domain names in the certificate. ["*.x.com"] for example. Note: this field may return `null`, indicating that no valid values can be obtained. |
| CloudCertId | String | Tencent Cloud SSL certificate ID. Note: this field may return `null`, indicating that no valid values can be obtained. |

## DomainInfo

LVB domain name information

Used by actions: DescribeLiveDomain, DescribeLiveDomains.

| Name | Type | Description |
| --- | --- | --- |
| Name | String | LVB domain name. |
| Type | Integer | Domain name type: 0: push. 1: playback. |
| Status | Integer | Domain name status: 0: deactivated. 1: activated. |
| CreateTime | String | The time when the domain was added. Note: Beijing time (UTC+8) is used. |
| BCName | Integer | Whether there is a CNAME record pointing to a fixed rule domain name: 0: no. 1: yes. |
| TargetDomain | String | Domain name corresponding to CNAME record. |
| PlayType | Integer | Playback region. This parameter is valid only if `Type` is 1. 1: in Mainland China. 2: global. 3: outside Mainland China. |
| IsDelayLive | Integer | Whether it is LCB: 0: LVB. 1: LCB. |
| CurrentCName | String | Information of currently used CNAME record. |
| RentTag | Integer | Disused parameter, which can be ignored. |
| RentExpireTime | String | A disused parameter. Note: Beijing time (UTC+8) is used. |
| IsMiniProgramLive | Integer | 0: LVB. 1: LVB on Mini Program. Note: this field may return null, indicating that no valid values can be obtained. |

## FlvSpecialParam

Special FLV recording setting.

Used by actions: CreateLiveRecordTemplate, DescribeLiveRecordTemplate, DescribeLiveRecordTemplates, ModifyLiveRecordTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UploadInRecording | Boolean | No | Whether to enable upload while recording. This parameter is only valid for FLV recording. |

## ForbidStreamInfo

List of forbidden streams

Used by actions: DescribeLiveForbidStreamList.

| Name | Type | Description |
| --- | --- | --- |
| StreamName | String | Stream name. |
| CreateTime | String | The creation time. Note: Beijing time (UTC+8) is used. |
| ExpireTime | String | The end time. Note: Beijing time (UTC+8) is used. |
| AppName | String | The push path. Note: This field may return null, indicating that no valid values can be obtained. |
| DomainName | String | The push domain name. Note: This field may return null, indicating that no valid values can be obtained. |

## GroupProIspDataInfo

Bandwidth, traffic, number of requests, and number of concurrent connections of an ISP in a district.

Used by actions: DescribeGroupProIspPlayInfoList.

| Name | Type | Description |
| --- | --- | --- |
| ProvinceName | String | District. |
| IspName | String | ISP. |
| DetailInfoList | Array of [CdnPlayStatData](#CdnPlayStatData) | Detailed data at the minute level. |

## HlsSpecialParam

HLS-specific recording parameter

Used by actions: CreateLiveRecordTemplate, DescribeLiveRecordTemplate, DescribeLiveRecordTemplates, ModifyLiveRecordTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| FlowContinueDuration | Integer | No | Timeout period for restarting an interrupted HLS push. Value range: [0, 1,800]. |

## HttpCodeInfo

HTTP return code and statistics

Used by actions: DescribePlayErrorCodeDetailInfoList.

| Name | Type | Description |
| --- | --- | --- |
| HttpCode | String | HTTP return code. Example: "2xx", "3xx", "4xx", "5xx". |
| ValueList | Array of [HttpCodeValue](#HttpCodeValue) | Statistics. 0 will be added for points in time when there is no data. |

## HttpCodeValue

HTTP return code data

Used by actions: DescribePlayErrorCodeDetailInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Time in the format of `yyyy-mm-dd HH:MM:SS`. |
| Numbers | Integer | Occurrences. |
| Percentage | Float | Proportion. |

## HttpStatusData

Playback error code information

Used by actions: DescribeHttpStatusInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Data point in time, In the format of `yyyy-mm-dd HH:MM:SS`. |
| HttpStatusInfoList | Array of [HttpStatusInfo](#HttpStatusInfo) | Playback status code details. |

## HttpStatusInfo

Playback error code information

Used by actions: DescribeHttpStatusInfoList.

| Name | Type | Description |
| --- | --- | --- |
| HttpStatus | String | Playback HTTP status code. |
| Num | Integer | Quantity. |

## LiveCertDomainInfo

The domains to bind to a certificate.

Used by actions: ModifyLiveDomainCertBindings.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| DomainName | String | Yes | The domain name. |
| Status | Integer | Yes | Whether to enable HTTPS for the domain. 1: Enable 0: Disable -1: Keep the current configuration |

## LiveDomainCertBindings

The domain and certificate information returned by `DescribeLiveDomainCertBindings` and `DescribeLiveDomainCertBindingsGray`.

Used by actions: DescribeLiveDomainCertBindings.

| Name | Type | Description |
| --- | --- | --- |
| DomainName | String | The domain name. |
| CertificateAlias | String | The remarks for the certificate. This parameter is the same as `CertName`. |
| CertType | Integer | The certificate type. 0: Self-owned certificate 1: Tencent Cloud-hosted certificate |
| Status | Integer | Whether HTTPS is enabled. 1: Enabled 0: Disabled |
| CertExpireTime | Timestamp | The certificate expiration time. Note: Beijing time (UTC+8) is used. |
| CertId | Integer | The certificate ID. |
| CloudCertId | String | The SSL certificate ID assigned by Tencent Cloud. |
| UpdateTime | Timestamp | The last updated time. Note: Beijing time (UTC+8) is used. Note: This field may return null, indicating that no valid values can be obtained. |

## MonitorStreamPlayInfo

The playback data.

Used by actions: DescribeAllStreamPlayInfoList.

| Name | Type | Description |
| --- | --- | --- |
| PlayDomain | String | The playback domain. |
| StreamName | String | The stream ID. |
| Rate | Integer | The playback bitrate. `0` indicates the original bitrate. |
| Protocol | String | The playback protocol. Valid values: `Unknown`, `Flv`, `Hls`, `Rtmp`, `Huyap2p`. |
| Bandwidth | Float | The bandwidth (Mbps). |
| Online | Integer | The number of online users, which is represented by the number of TCP connections (data collected every minute). |
| Request | Integer | The number of requests. |

## PlayAuthKeyInfo

Playback authentication key information.

Used by actions: DescribeLivePlayAuthKey.

| Name | Type | Description |
| --- | --- | --- |
| DomainName | String | Domain name. |
| Enable | Integer | Whether to enable: 0: disable. 1: enable. |
| AuthKey | String | Authentication key. |
| AuthDelta | Integer | Validity period in seconds. |
| AuthBackKey | String | Authentication `BackKey`. |

## PlayCodeTotalInfo

Total occurrences of each status code. Most HTTP return codes are supported.

Used by actions: DescribePlayErrorCodeSumInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Code | String | HTTP code. Valid values: 400, 403, 404, 500, 502, 503, 504. |
| Num | Integer | Total occurrences. |

## PlayDataInfoByStream

Playback information at the stream level.

Used by actions: DescribeStreamDayPlayInfoList.

| Name | Type | Description |
| --- | --- | --- |
| StreamName | String | Stream name. |
| TotalFlux | Float | Total traffic in MB. |

## PlayStatInfo

Queries the playback information by ISP and district.

Used by actions: DescribeProvinceIspPlayInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Data point in time. |
| Value | Float | Value of bandwidth/traffic/number of requests/number of concurrent connections/download speed. If there is no data returned, the value is 0. Note: this field may return null, indicating that no valid values can be obtained. |

## PlaySumStatInfo

Aggregated playback statistics.

Used by actions: DescribeVisitTopSumInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Name | String | Domain name or stream ID. |
| AvgFluxPerSecond | Float | Average download speed, In MB/s. Calculation formula: average download speed per minute. |
| TotalFlux | Float | Total traffic in MB. |
| TotalRequest | Integer | Total number of requests. |

## ProIspPlayCodeDataInfo

Playback error code information

Used by actions: DescribePlayErrorCodeSumInfoList.

| Name | Type | Description |
| --- | --- | --- |
| CountryAreaName | String | Country or region. |
| ProvinceName | String | District. |
| IspName | String | ISP. |
| Code2xx | Integer | Occurrences of 2xx error codes. |
| Code3xx | Integer | Occurrences of 3xx error codes. |
| Code4xx | Integer | Occurrences of 4xx error codes. |
| Code5xx | Integer | Occurrences of 5xx error codes. |

## PublishTime

Push time.

Used by actions: DescribeLiveStreamOnlineList.

| Name | Type | Description |
| --- | --- | --- |
| PublishTime | String | Push time. In UTC format, such as 2018-06-29T19:00:00Z. |

## PullPushWatermarkInfo

The watermark configuration for a relay task.

Used by actions: CreateLivePullStreamTask, DescribeLivePullStreamTasks, ModifyLivePullStreamTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| PictureUrl | String | Yes | The watermark image URL. Characters not allowed: ;(){}$>`#"'\| |
| XPosition | Integer | Yes | The horizontal offset (%) of the watermark. The default value is 0. |
| YPosition | Integer | Yes | The vertical offset (%) of the watermark. The default value is 0. |
| Width | Integer | Yes | The watermark width as a percentage of the video width. To avoid distorted images, we recommend you specify only the width or height so that the other side can be scaled proportionally. By default, the original width of the watermark image is used. |
| Height | Integer | Yes | The watermark height as a percentage of the video height. To avoid distorted images, we recommend you specify only the width or height so that the other side can be scaled proportionally. By default, the original height of the watermark image is used. |
| Location | Integer | Yes | The origin. The default value is 0. 0: Top left corner 1: Top right corner 2: Bottom right corner 3: Bottom left corner |

## PullStreamTaskInfo

The information of a stream pulling task.

Used by actions: DescribeLivePullStreamTasks.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | The task ID. |
| SourceType | String | The source type. Valid values: PullLivePushLive: Live streaming PullVodPushLive: Video files PullPicPushLive: Images |
| SourceUrls | Array of String | The source URL(s). If `SourceType` is `PullLiveToLive`, there can be only one source URL. If `SourceType` is `PullVodToLive`, there can be at most 10 source URLs. |
| DomainName | String | The push domain name. The pulled stream is pushed to this domain. |
| AppName | String | The application to push to. The pulled stream is pushed to this application. |
| StreamName | String | The stream name. The pulled stream is pushed under this name. |
| PushArgs | String | The push parameter. A custom push parameter. |
| StartTime | String | The start time. It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| EndTime | String | The end time. Notes: 1. The end time must be later than the start time. 2. The end time and start time must be later than the current time. 3. The end time and start time must be less than seven days apart. It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| Region | String | The region where the task was created. `ap-beijing`: North China (Beijing) `ap-shanghai`: East China (Shanghai) `ap-guangzhou`: South China (Guangzhou) `ap-mumbai`: India `ap-hongkong`: Hong Kong `eu-frankfurt`: Germany `ap-seoul`: Korea `ap-bangkok`: Thailand `ap-singapore`: Singapore `na-siliconvalley`: Western US `na-ashburn`: Eastern US `ap-tokyo`: Japan |
| VodLoopTimes | Integer | The number of times to loop video files. -1: Loop indefinitely 0: Do not loop > 0: The number of loop times. A task will end either when the videos are looped for the specified number of times or at the specified task end time, whichever is earlier. This parameter is valid only if the source is video files. |
| VodRefreshType | String | The behavior after the source video files (`SourceUrls`) are changed. ImmediateNewSource: Play the new videos immediately ContinueBreakPoint: Finish the current video first and then pull from the new source.  This parameter is valid only if the source is video files. |
| CreateTime | String | The task creation time. It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| UpdateTime | String | The last updated time. It must be in UTC format. Example: 2019-01-08T10:00:00Z. Note: Beijing time is 8 hours ahead of UTC. The [ISO 8601 format](https://intl.cloud.tencent.com/document/product/266/11732#iso-date-format) is used. |
| CreateBy | String | The task creator. |
| UpdateBy | String | The operator of the last update. |
| CallbackUrl | String | The callback URL. |
| CallbackEvents | Array of String | The events to listen for. TaskStart: Callback for starting a task TaskExit: Callback for ending a task VodSourceFileStart: Callback for starting to pull from video files VodSourceFileFinish: Callback for stopping pulling from video files ResetTaskConfig: Callback for modifying a task |
| CallbackInfo | String | Note: This parameter is not returned currently. The information of the last callback. |
| ErrorInfo | String | Note: This parameter is not returned currently. Error message. |
| Status | String | The task status. enable: Enabled pause: Paused |
| RecentPullInfo | [RecentPullInfo](#RecentPullInfo) | Note: This parameter is returned only if one task is queried. The latest pull information. The information includes the source URL, offset, and report time. |
| Comment | String | The remarks for the task. |
| BackupSourceType | String | The backup source type. Valid values: PullLivePushLive: Live streaming PullVodPushLive: Video files Note: This field may return null, indicating that no valid values can be obtained. |
| BackupSourceUrl | String | The URL of the backup source. Note: This field may return null, indicating that no valid values can be obtained. |
| WatermarkList | Array of [PullPushWatermarkInfo](#PullPushWatermarkInfo) | The information of watermarks to add. Note: This field may return null, indicating that no valid values can be obtained. |
| VodLocalMode | Integer | Whether to use local mode when the source type is video files. The default is `0`. 0: Do not use local mode 1: Use local mode Note: This field may return null, indicating that no valid values can be obtained. |
| RecordTemplateId | String | Recording template ID. |
| BackupToUrl | String | Newly added streaming address. Used for the scenario of pushing two streams with a single task. |

## PushAuthKeyInfo

Push authentication key information.

Used by actions: DescribeLivePushAuthKey.

| Name | Type | Description |
| --- | --- | --- |
| DomainName | String | Domain name. |
| Enable | Integer | Whether to enable. 0: disabled; 1: enabled. |
| MasterAuthKey | String | Master authentication key. |
| BackupAuthKey | String | Standby authentication key. |
| AuthDelta | Integer | Validity period in seconds. |

## PushDataInfo

Push information

Used by actions: DescribeLiveStreamPushInfoList.

| Name | Type | Description |
| --- | --- | --- |
| StreamName | String | Stream name. |
| AppName | String | Push path. |
| ClientIp | String | Push client IP. |
| ServerIp | String | IP of the server that receives the stream. |
| VideoFps | Integer | Pushed video frame rate in Hz. |
| VideoSpeed | Integer | Video bitrate (bps) for publishing |
| AudioFps | Integer | Pushed audio frame rate in Hz. |
| AudioSpeed | Integer | Audio bitrate (bps) for publishing |
| PushDomain | String | Push domain name. |
| BeginPushTime | String | Push start time. |
| Acodec | String | Audio codec, Example: AAC. |
| Vcodec | String | Video codec, Example: H.264. |
| Resolution | String | Resolution. |
| AsampleRate | Integer | Sample rate. |
| MetaAudioSpeed | Integer | Audio bitrate (bps) in metadata |
| MetaVideoSpeed | Integer | Video bitrate (bps) in metadata |
| MetaFps | Integer | Frame rate in `metadata`. |

## PushQualityData

The push data of a stream.

Used by actions: DescribeStreamPushInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | The time of the data in the format of “%Y-%m-%d %H:%M:%S.%ms” (accurate to the millisecond). |
| PushDomain | String | The push domain. |
| AppName | String | The push path. |
| ClientIp | String | The IP address of the push client. |
| BeginPushTime | String | The push start time in the format of “%Y-%m-%d %H:%M:%S.%ms” (accurate to the millisecond). |
| Resolution | String | The resolution. |
| VCodec | String | The video codec. |
| ACodec | String | The audio codec. |
| Sequence | String | The push sequence number, which uniquely identifies a push. |
| VideoFps | Integer | The video frame rate. |
| VideoRate | Integer | The video bitrate (bps). |
| AudioFps | Integer | The audio frame rate. |
| AudioRate | Integer | The audio bitrate (bps). |
| LocalTs | Integer | The local elapsed time (milliseconds). The greater the difference between the local elapsed time and audio/video elapsed time, the poorer the push quality and the more severe the upstream lag. |
| VideoTs | Integer | The video elapsed time (milliseconds). |
| AudioTs | Integer | The audio elapsed time (milliseconds). |
| MetaVideoRate | Integer | The video bitrate (Kbps) in the metadata. |
| MetaAudioRate | Integer | The audio bitrate (Kbps) in the metadata. |
| MateFps | Integer | The frame rate in the metadata. |
| StreamParam | String | The push parameter. |
| Bandwidth | Float | The bandwidth (Mbps). |
| Flux | Float | The traffic (MB). |
| ServerIp | String | The IP address of the push client. Note: This field may return null, indicating that no valid values can be obtained. |

## RecentPullInfo

The latest pull information.

Used by actions: DescribeLivePullStreamTasks.

| Name | Type | Description |
| --- | --- | --- |
| FileUrl | String | The URL of the file currently pulled. |
| OffsetTime | Integer | The offset of the file currently pulled. |
| ReportTime | String | The time when the offset is reported, in UTC format. Example: 2020-07-23T03:20:39Z Note: Beijing time is 8 hours ahead of UTC. |
| LoopedTimes | Integer | The number of times looped. |

## RecordParam

Recording template parameter.

Used by actions: CreateLiveRecordTemplate, DescribeLiveRecordTemplate, DescribeLiveRecordTemplates, ModifyLiveRecordTemplate.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| RecordInterval | Integer | No | Max recording time per file Default value: `1800` (seconds) Value range: 30-7200 This parameter is invalid for HLS. Only one HLS file will be generated from push start to push end. |
| StorageTime | Integer | No | Storage duration of the recording file Value range: 0-129600000 seconds (0-1500 days) `0`: permanent |
| Enable | Integer | No | Whether to enable recording in the current format. Default value: 0. 0: no, 1: yes. |
| VodSubAppId | Integer | No | VOD subapplication ID. |
| VodFileName | String | No | Recording filename. Supported special placeholders include: {StreamID}: stream ID {StartYear}: start time - year {StartMonth}: start time - month {StartDay}: start time - day {StartHour}: start time - hour {StartMinute}: start time - minute {StartSecond}: start time - second {StartMillisecond}: start time - millisecond {EndYear}: end time - year {EndMonth}: end time - month {EndDay}: end time - day {EndHour}: end time - hour {EndMinute}: end time - minute {EndSecond}: end time - second {EndMillisecond}: end time - millisecond  If this parameter is not set, the recording filename will be `{StreamID}_{StartYear}-{StartMonth}-{StartDay}-{StartHour}-{StartMinute}-{StartSecond}_{EndYear}-{EndMonth}-{EndDay}-{EndHour}-{EndMinute}-{EndSecond}` by default |
| Procedure | String | No | Task flow Note: this field may return `null`, indicating that no valid value is obtained. |
| StorageMode | String | No | Video storage class. Valid values: `normal`: STANDARD `cold`: STANDARD_IA Note: this field may return `null`, indicating that no valid value is obtained. |
| ClassId | Integer | No | VOD subapplication category Note: this field may return `null`, indicating that no valid value is obtained. |

## RecordTask

Recording task.

Used by actions: DescribeRecordTask.

| Name | Type | Description |
| --- | --- | --- |
| TaskId | String | Recording task ID. |
| DomainName | String | Push domain name. |
| AppName | String | Push path. |
| StreamName | String | Stream name. |
| StartTime | Integer | The start time of the recording task in Unix timestamp. |
| EndTime | Integer | The end time of the recording task in Unix timestamp. |
| TemplateId | Integer | Recording template ID. |
| Stopped | Integer | The StopRecordTask API call stops the task at the Unix timestamp. A value of 0 indicates that the API has not been called to stop the task. |

## RecordTemplateInfo

Recording template information

Used by actions: DescribeLiveRecordTemplate, DescribeLiveRecordTemplates.

| Name | Type | Description |
| --- | --- | --- |
| TemplateId | Integer | Template ID. |
| TemplateName | String | Template name. |
| Description | String | Message description |
| FlvParam | [RecordParam](#RecordParam) | FLV recording parameter. |
| HlsParam | [RecordParam](#RecordParam) | HLS recording parameter. |
| Mp4Param | [RecordParam](#RecordParam) | MP4 recording parameter. |
| AacParam | [RecordParam](#RecordParam) | AAC recording parameter. |
| IsDelayLive | Integer | 0: LVB, 1: LCB. |
| HlsSpecialParam | [HlsSpecialParam](#HlsSpecialParam) | A special parameter for HLS recording. |
| Mp3Param | [RecordParam](#RecordParam) | MP3 recording parameter. |
| RemoveWatermark | Boolean | Whether the watermark is removed. Note: This field may return `null`, indicating that no valid value was found. |
| FlvSpecialParam | [FlvSpecialParam](#FlvSpecialParam) | A special parameter for FLV recording. Note: This field may return `null`, indicating that no valid value can be obtained. |

## RefererAuthConfig

Referer allowlist/blocklist configuration of a live streaming domain name

Used by actions: DescribeLiveDomainReferer.

| Name | Type | Description |
| --- | --- | --- |
| DomainName | String | Domain name |
| Enable | Integer | Whether to enable referer. Valid values: `0` (no), `1` (yes) |
| Type | Integer | List type. Valid values: `0` (blocklist), `1` (allowlist) |
| AllowEmpty | Integer | Whether to allow empty referer. Valid values: `0` (no), `1` (yes) |
| Rules | String | Referer list. Separate items in it with semicolons (;). |

## RuleInfo

Rule information.

Used by actions: DescribeLiveRecordRules, DescribeLiveSnapshotRules, DescribeLiveTimeShiftRules, DescribeLiveTranscodeRules, DescribeLiveWatermarkRules.

| Name | Type | Description |
| --- | --- | --- |
| CreateTime | String | The rule creation time. Note: Beijing time (UTC+8) is used. |
| UpdateTime | String | The rule update time. Note: Beijing time (UTC+8) is used. |
| TemplateId | Integer | Template ID. |
| DomainName | String | Push domain name. |
| AppName | String | Push path. |
| StreamName | String | Stream name. |

## SnapshotTemplateInfo

Screencapturing template information.

Used by actions: DescribeLiveSnapshotTemplate, DescribeLiveSnapshotTemplates.

| Name | Type | Description |
| --- | --- | --- |
| TemplateId | Integer | Template ID. |
| TemplateName | String | Template name. |
| SnapshotInterval | Integer | Screencapturing interval. Value range: 5-300s. |
| Width | Integer | Screenshot width. Value range: 0-3000.  0: original width and fit to the original ratio. |
| Height | Integer | Screenshot height. Value range: 0-2000. 0: original height and fit to the original ratio. |
| PornFlag | Integer | Whether to enable porn detection. 0: no, 1: yes. |
| CosAppId | Integer | COS application ID. |
| CosBucket | String | COS bucket name. |
| CosRegion | String | COS region. |
| Description | String | Template description. |
| CosPrefix | String | COS bucket folder prefix. Note: this field may return null, indicating that no valid values can be obtained. |
| CosFileName | String | COS filename. Note: this field may return null, indicating that no valid values can be obtained. |

## StreamEventInfo

Streaming event information.

Used by actions: DescribeLiveStreamEventList.

| Name | Type | Description |
| --- | --- | --- |
| AppName | String | Application name. |
| DomainName | String | Push domain name. |
| StreamName | String | Stream name. |
| StreamStartTime | String | Push start time. In UTC format, such as 2019-01-07T12:00:00Z. |
| StreamEndTime | String | Push end time. In UTC format, such as 2019-01-07T15:00:00Z. |
| StopReason | String | Stop reason. |
| Duration | Integer | Push duration in seconds. |
| ClientIp | String | The IP address of the host. If the stream is published from a private network, this parameter will be `-`. |
| Resolution | String | Resolution. |

## StreamName

Stream name list.

Used by actions: DescribeLiveStreamPublishedList.

| Name | Type | Description |
| --- | --- | --- |
| StreamName | String | Stream name. |
| AppName | String | Application name. |
| DomainName | String | Push domain name. |
| StreamStartTime | String | Push start time. In UTC format, such as 2019-01-07T12:00:00Z. |
| StreamEndTime | String | Push end time. In UTC format, such as 2019-01-07T15:00:00Z. |
| StopReason | String | Stop reason. |
| Duration | Integer | Push duration in seconds. |
| ClientIp | String | Host IP. |
| Resolution | String | Resolution. |

## StreamOnlineInfo

Queries active push information

Used by actions: DescribeLiveStreamOnlineList.

| Name | Type | Description |
| --- | --- | --- |
| StreamName | String | Stream name. |
| PublishTimeList | Array of [PublishTime](#PublishTime) | Push time list |
| AppName | String | Application name. |
| DomainName | String | Push domain name. |

## TemplateInfo

Transcoding template information.

Used by actions: DescribeLiveTranscodeTemplate, DescribeLiveTranscodeTemplates.

| Name | Type | Description |
| --- | --- | --- |
| Vcodec | String | Codec: h264/h265/origin. Default value: h264.  origin: keep the original codec. |
| VideoBitrate | Integer | Video bitrate. Value range: 0–8,000 Kbps. If the value is 0, the original bitrate will be retained. Note: transcoding templates require a unique bitrate. The final saved bitrate may differ from the input bitrate. |
| Acodec | String | Audio codec: aac. Default value: aac. Note: This parameter will not take effect for now and will be supported soon. |
| AudioBitrate | Integer | Audio bitrate. Value range: 0–500 Kbps. 0 by default. |
| Width | Integer | Width. Default value: 0. Value range: [0-3,000]. The value must be a multiple of 2. The original width is 0. |
| Height | Integer | Height. Default value: 0. Value range: [0-3,000]. The value must be a multiple of 2. The original width is 0. |
| Fps | Integer | Frame rate. Default value: 0. Range: 0-60 Fps. |
| Gop | Integer | Keyframe interval, unit: second. Original interval by default Range: 2-6 |
| Rotate | Integer | Rotation angle. Default value: 0. Value range: 0, 90, 180, 270 |
| Profile | String | Encoding quality: baseline/main/high. Default value: baseline. |
| BitrateToOrig | Integer | Whether to use the original bitrate when the set bitrate is larger than the original bitrate. 0: no, 1: yes Default value: 0. |
| HeightToOrig | Integer | Whether to use the original height when the set height is higher than the original height. 0: no, 1: yes Default value: 0. |
| FpsToOrig | Integer | Whether to use the original frame rate when the set frame rate is larger than the original frame rate. 0: no, 1: yes Default value: 0. |
| NeedVideo | Integer | Whether to keep the video. 0: no; 1: yes. |
| NeedAudio | Integer | Whether to keep the audio. 0: no; 1: yes. |
| TemplateId | Integer | Template ID. |
| TemplateName | String | Template name. |
| Description | String | Template description. |
| AiTransCode | Integer | Whether it is a top speed codec template. 0: no, 1: yes. Default value: 0. |
| AdaptBitratePercent | Float | Bitrate compression ratio of top speed code video. Target bitrate of top speed code = VideoBitrate * (1-AdaptBitratePercent)  Value range: 0.0-0.5. |
| ShortEdgeAsHeight | Integer | Whether to take the shorter side as height. 0: no, 1: yes. Default value: 0. Note: this field may return `null`, indicating that no valid value is obtained. |
| DRMType | String | The DRM encryption type. Valid values: fairplay, normalaes, widevine. Note: This field may return null, indicating that no valid values can be obtained. |
| DRMTracks | String | The tracks to encrypt. Valid values: AUDIO, SD, HD, UHD1, UHD2. Separate multiple tracks with “\|”. You can choose only one video track (SD, HD, UHD1, or UHD2). Note: This field may return null, indicating that no valid values can be obtained. |

## TimeShiftBillData

The time shifting billing data.

Used by actions: DescribeLiveTimeShiftBillInfoList.

| Name | Type | Description |
| --- | --- | --- |
| Domain | String | The push domain name. |
| Duration | Float | The time-shift video length (minutes). |
| StoragePeriod | Float | The time-shift days. |
| Time | String | The time for the data returned. Format: YYYY-MM-DDThh:mm:ssZ. |
| TotalDuration | Float | The total time-shift duration (minutes). |

## TimeShiftRecord

A recorded time shifting session.

Used by actions: DescribeTimeShiftRecordDetail.

| Name | Type | Description |
| --- | --- | --- |
| Sid | String | The session ID. |
| StartTime | Integer | The recording start time, which is a Unix timestamp. |
| EndTime | Integer | The recording end time, which is a Unix timestamp. |

## TimeShiftStreamInfo

The information of a time shifted stream.

Used by actions: DescribeTimeShiftStreamList.

| Name | Type | Description |
| --- | --- | --- |
| DomainGroup | String | The group the push domain belongs to. Note: This field may return null, indicating that no valid values can be obtained. |
| Domain | String | The push domain. |
| AppName | String | The push path. |
| StreamName | String | The stream name. |
| StartTime | Integer | The stream start time, which is a Unix timestamp. |
| EndTime | Integer | The stream end time (for streams that ended before the time of query), which is a Unix timestamp. |
| TransCodeId | Integer | The transcoding template ID. Note: This field may return null, indicating that no valid values can be obtained. |
| StreamType | Integer | The stream type. `0`: The original stream; `1`: The watermarked stream; `2`: The transcoded stream. |
| Duration | Integer | The storage duration (seconds) of the recording. Note: This field may return null, indicating that no valid values can be obtained. |

## TimeShiftTemplate

The information of a time shifting template.

Used by actions: DescribeLiveTimeShiftTemplates.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| TemplateName | String | Yes | The template name. |
| Duration | Integer | Yes | The time shifting duration. Unit: second |
| ItemDuration | Integer | Yes | The segment size. Value range: 3-10. Unit: Second. Default value: 5 |
| TemplateId | Integer | No | The template ID. |
| Description | String | No | The template description. |
| Area | String | No | The region. Valid values: `Mainland`: The Chinese mainland. `Overseas`: Outside the Chinese mainland. Default value: `Mainland`. |
| RemoveWatermark | Boolean | No | Whether to remove watermarks. If you pass in `true`, the original stream will be recorded. Default value: `false`. |
| TranscodeTemplateIds | Array of Integer | No | The transcoding template IDs. This API works only if `RemoveWatermark` is `false`. |

## TimeValue

Metric value at a specified point in time.

Used by actions: DescribeScreenShotSheetNumList.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | UTC time in the format of `yyyy-mm-ddTHH:MM:SSZ`. |
| Num | Integer | Value. |

## TranscodeDetailInfo

Transcoding details.

Used by actions: DescribeLiveTranscodeDetailInfo.

| Name | Type | Description |
| --- | --- | --- |
| StreamName | String | Stream name. |
| StartTime | String | Start time (Beijing time) in the format of `yyyy-mm-dd HH:MM`. |
| EndTime | String | End time (Beijing time) in the format of `yyyy-mm-dd HH:MM`. |
| Duration | Integer | Transcoding duration in minutes. Note: given the possible interruptions during push, duration here is the sum of actual duration of transcoding instead of the interval between the start time and end time. |
| ModuleCodec | String | Codec with modules, Example: liveprocessor_H264: LVB transcoding - H264, liveprocessor_H265: LVB transcoding - H265, topspeed_H264: top speed codec - H264, topspeed_H265: top speed codec - H265. |
| Bitrate | Integer | Bitrate. |
| Type | String | The task type. Valid values: Transcode, MixStream, WaterMark, Webrtc. |
| PushDomain | String | Push domain name. |
| Resolution | String | Resolution. |
| MainlandOrOversea | String | The region. Valid values: `Mainland`: Inside the Chinese mainland. `Overseas`: Outside the Chinese mainland. |

## TranscodeTaskNum

The number of tasks.

Used by actions: DescribeTranscodeTaskNum.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | The time of query. |
| CodeRate | Integer | The bitrate. |
| Num | Integer | The number of tasks. |

## TranscodeTotalInfo

Total usage of the transcoding service

Used by actions: DescribeLiveTranscodeTotalInfo.

| Name | Type | Description |
| --- | --- | --- |
| Time | String | Usage time (Beijing time) Example: 2019-03-01 00:00:00 |
| Duration | Integer | Transcoding duration in minutes |
| ModuleCodec | String | Codec, with modules Examples: `liveprocessor_H264`: live transcoding-H264 `liveprocessor_H265`: live transcoding-H265 `topspeed_H264`: top speed codec-H264 `topspeed_H265`: top speed codec-H265 |
| Resolution | String | Resolution Example: 540*480 |

## WatermarkInfo

Watermark information.

Used by actions: DescribeLiveWatermark, DescribeLiveWatermarks.

| Name | Type | Description |
| --- | --- | --- |
| WatermarkId | Integer | Watermark ID. |
| PictureUrl | String | Watermark image URL. |
| XPosition | Integer | Display position: X-axis offset. |
| YPosition | Integer | Display position: Y-axis offset. |
| WatermarkName | String | Watermark name. |
| Status | Integer | Current status. 0: not used. 1: in use. |
| CreateTime | String | The time when the watermark was added. Note: Beijing time (UTC+8) is used. |
| Width | Integer | Watermark width. |
| Height | Integer | Watermark height. |


---
*Source: [https://www.tencentcloud.com/document/product/267/30767](https://www.tencentcloud.com/document/product/267/30767)*
