# API Category

## Live Pad APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateLivePadTemplate](https://www.tencentcloud.com/document/api/267/71831) | create live pad template | 20 |
| [CreateLivePadRule](https://www.tencentcloud.com/document/api/267/71832) | create live pad rule | 20 |
| [StartLivePadStream](https://www.tencentcloud.com/document/api/267/70664) | StartLivePadStream | 20 |
| [StopLivePadStream](https://www.tencentcloud.com/document/api/267/71611) | StopLivePadStream | 20 |

## LVB Transcoding APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DeleteLiveTranscodeRule](https://www.tencentcloud.com/document/api/267/30789) | Deletes a transcoding rule | 200 |
| [DeleteLiveTranscodeTemplate](https://www.tencentcloud.com/document/api/267/30788) | Deletes a transcoding template | 200 |
| [DescribeLiveTranscodeRules](https://www.tencentcloud.com/document/api/267/30787) | Gets the list of transcoding rules | 500 |
| [DescribeLiveTranscodeTemplate](https://www.tencentcloud.com/document/api/267/30786) | Gets a single transcoding template | 500 |
| [DescribeLiveTranscodeTemplates](https://www.tencentcloud.com/document/api/267/30785) | Gets the list of transcoding templates | 500 |
| [CreateLiveTranscodeTemplate](https://www.tencentcloud.com/document/api/267/30790) | Creating a transcoding template | 200 |
| [ModifyLiveTranscodeTemplate](https://www.tencentcloud.com/document/api/267/30784) | Modifies the transcoding template configuration | 200 |
| [CreateLiveTranscodeRule](https://www.tencentcloud.com/document/api/267/30791) | Creates a transcoding rule | 200 |

## Delayed Playback Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeLiveDelayInfoList](https://www.tencentcloud.com/document/api/267/33532) | Gets the list of delayed playbacks. | 500 |
| [ResumeDelayLiveStream](https://www.tencentcloud.com/document/api/267/30849) | Cancels the live streaming delay | 200 |
| [AddDelayLiveStream](https://www.tencentcloud.com/document/api/267/30850) | Sets a live streaming delay | 200 |

## Domain Name Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [AddLiveDomain](https://www.tencentcloud.com/document/api/267/35189) | Adds domain name | 100 |
| [AuthenticateDomainOwner](https://www.tencentcloud.com/document/api/267/50612) | Verifies the ownership of a domain | 20 |
| [DeleteLiveDomain](https://www.tencentcloud.com/document/api/267/35188) | Deletes domain name | 100 |
| [DescribeLiveDomain](https://www.tencentcloud.com/document/api/267/35187) | Queries domain name information | 500 |
| [DescribeLiveDomains](https://www.tencentcloud.com/document/api/267/35186) | Queries domain name list | 200 |
| [EnableLiveDomain](https://www.tencentcloud.com/document/api/267/35185) | Enables domain name | 100 |
| [ForbidLiveDomain](https://www.tencentcloud.com/document/api/267/35184) | Disables domain name | 100 |
| [ModifyLivePlayDomain](https://www.tencentcloud.com/document/api/267/35183) | Modifies playback domain name | 200 |

## Watermark Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [AddLiveWatermark](https://www.tencentcloud.com/document/api/267/30826) | Adds watermark | 100 |
| [CreateLiveWatermarkRule](https://www.tencentcloud.com/document/api/267/30825) | Creates watermarking rule | 200 |
| [DeleteLiveWatermark](https://www.tencentcloud.com/document/api/267/30824) | Delete watermark | 100 |
| [DeleteLiveWatermarkRule](https://www.tencentcloud.com/document/api/267/30823) | Deletes watermarking rule | 200 |
| [DescribeLiveWatermark](https://www.tencentcloud.com/document/api/267/30822) | Gets the information of a single watermark | 500 |
| [DescribeLiveWatermarkRules](https://www.tencentcloud.com/document/api/267/30821) | Gets the watermarking rule list | 500 |
| [DescribeLiveWatermarks](https://www.tencentcloud.com/document/api/267/30820) | Queries watermark list | 500 |
| [UpdateLiveWatermark](https://www.tencentcloud.com/document/api/267/30818) | Updates watermark | 100 |

## Certificate Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeLiveCert](https://www.tencentcloud.com/document/api/267/30779) | Gets certificate information | 500 |
| [DescribeLiveCerts](https://www.tencentcloud.com/document/api/267/30778) | Gets certificate information list | 500 |
| [DescribeLiveDomainCert](https://www.tencentcloud.com/document/api/267/30777) | Gets domain name certificate information | 500 |
| [DescribeLiveDomainCertBindings](https://www.tencentcloud.com/document/api/267/49645) | Querying domains bound with certificates | 20 |
| [ModifyLiveDomainCertBindings](https://www.tencentcloud.com/document/api/267/49644) | Binding a certificate to multiple playback domains | 20 |
| [UnBindLiveDomainCert](https://www.tencentcloud.com/document/api/267/30774) | Unbinds domain name certificate | 200 |

## Live Stream Mix APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CancelCommonMixStream](https://www.tencentcloud.com/document/api/267/35998) | Cancels general stream mix | 100 |
| [CreateCommonMixStream](https://www.tencentcloud.com/document/api/267/35997) | Creates general stream mix | 200 |

## Stream Pulling APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DeleteLivePullStreamTask](https://www.tencentcloud.com/document/api/267/48356) | Deletes a stream pulling task | 50 |
| [DescribeLivePullStreamTasks](https://www.tencentcloud.com/document/api/267/48355) | Queries stream pulling tasks | 30 |
| [RestartLivePullStreamTask](https://www.tencentcloud.com/document/api/267/56967) | RestartLivePullStreamTask | 20 |
| [CreateLivePullStreamTask](https://www.tencentcloud.com/document/api/267/48357) | Creates a stream pulling task | 50 |
| [ModifyLivePullStreamTask](https://www.tencentcloud.com/document/api/267/48354) | Modifies a stream pulling task | 20 |

## Recording Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateLiveRecord](https://www.tencentcloud.com/document/api/267/30847) | Creates recording task (disused; please use the new API) | 500 |
| [CreateLiveRecordRule](https://www.tencentcloud.com/document/api/267/30846) | Creates a recording rule | 200 |
| [CreateLiveRecordTemplate](https://www.tencentcloud.com/document/api/267/30845) | Creates a recording template | 200 |
| [CreateRecordTask](https://www.tencentcloud.com/document/api/267/37309) | Creates recording task (new) | 20 |
| [DeleteLiveRecord](https://www.tencentcloud.com/document/api/267/30844) | Deletes recording task (disused; please use the new API) | 200 |
| [DeleteLiveRecordRule](https://www.tencentcloud.com/document/api/267/30843) | Deletes a recording rule | 200 |
| [DeleteLiveRecordTemplate](https://www.tencentcloud.com/document/api/267/30842) | Deletes a recording template. | 200 |
| [DeleteRecordTask](https://www.tencentcloud.com/document/api/267/37308) | Deletes recording task (new) | 20 |
| [DescribeLiveRecordRules](https://www.tencentcloud.com/document/api/267/30841) | Gets the list of recording rules | 500 |
| [DescribeLiveRecordTemplate](https://www.tencentcloud.com/document/api/267/30840) | Gets a single recording template | 500 |
| [DescribeLiveRecordTemplates](https://www.tencentcloud.com/document/api/267/30839) | Gets the list of recording templates | 500 |
| [DescribeRecordTask](https://www.tencentcloud.com/document/api/267/56133) | CreateRecordTask (New) | 20 |
| [ModifyLiveRecordTemplate](https://www.tencentcloud.com/document/api/267/30838) | Modifies a recording template | 200 |
| [StopLiveRecord](https://www.tencentcloud.com/document/api/267/30837) | Terminates recording task (disused; please use the new API) | 200 |
| [StopRecordTask](https://www.tencentcloud.com/document/api/267/37307) | Terminates recording task (API) | 20 |

## Time Shifting APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateLiveTimeShiftRule](https://www.tencentcloud.com/document/api/267/53726) | Creates a time shifting rule | 20 |
| [CreateLiveTimeShiftTemplate](https://www.tencentcloud.com/document/api/267/53725) | Creates a time shifting template | 20 |
| [DeleteLiveTimeShiftRule](https://www.tencentcloud.com/document/api/267/53724) | Deletes a time shifting rule | 20 |
| [DeleteLiveTimeShiftTemplate](https://www.tencentcloud.com/document/api/267/53723) | Deletes a time shifting template | 20 |
| [DescribeLiveTimeShiftRules](https://www.tencentcloud.com/document/api/267/53722) | Queries time shifting rules | 20 |
| [DescribeLiveTimeShiftTemplates](https://www.tencentcloud.com/document/api/267/53721) | Queries time shifting templates | 20 |
| [DescribeTimeShiftRecordDetail](https://www.tencentcloud.com/document/api/267/53720) | Queries time shifting details | 20 |
| [DescribeTimeShiftStreamList](https://www.tencentcloud.com/document/api/267/53719) | Queries time shifted streams | 20 |
| [ModifyLiveTimeShiftTemplate](https://www.tencentcloud.com/document/api/267/53718) | Modifies a standby stream template | 20 |

## LVB Callback APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateLiveCallbackRule](https://www.tencentcloud.com/document/api/267/30816) | Creates callback rule | 200 |
| [CreateLiveCallbackTemplate](https://www.tencentcloud.com/document/api/267/30815) | Creates callback template | 200 |
| [DeleteLiveCallbackRule](https://www.tencentcloud.com/document/api/267/30814) | Deletes callback rule | 200 |
| [DeleteLiveCallbackTemplate](https://www.tencentcloud.com/document/api/267/30813) | Deletes callback template | 200 |
| [DescribeLiveCallbackRules](https://www.tencentcloud.com/document/api/267/30812) | Gets callback rule list | 500 |
| [DescribeLiveCallbackTemplate](https://www.tencentcloud.com/document/api/267/30811) | Gets a callback template | 500 |
| [DescribeLiveCallbackTemplates](https://www.tencentcloud.com/document/api/267/30810) | Gets callback template list | 500 |
| [ModifyLiveCallbackTemplate](https://www.tencentcloud.com/document/api/267/30809) | Modifies callback template | 200 |

## Screencapturing and Porn Detection APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateLiveSnapshotRule](https://www.tencentcloud.com/document/api/267/30835) | Creates screencapturing rule | 200 |
| [CreateLiveSnapshotTemplate](https://www.tencentcloud.com/document/api/267/30834) | Creates screencapturing template | 200 |
| [CreateScreenshotTask](https://www.tencentcloud.com/document/api/267/54799) | Creates a screencapturing task | 20 |
| [DeleteLiveSnapshotRule](https://www.tencentcloud.com/document/api/267/30833) | Deletes screencapturing rule | 200 |
| [DeleteLiveSnapshotTemplate](https://www.tencentcloud.com/document/api/267/30832) | Deletes screencapturing template | 200 |
| [DescribeLiveSnapshotRules](https://www.tencentcloud.com/document/api/267/30831) | Gets screencapturing rule list | 500 |
| [DescribeLiveSnapshotTemplate](https://www.tencentcloud.com/document/api/267/30830) | Gets single screencapturing template | 500 |
| [DescribeLiveSnapshotTemplates](https://www.tencentcloud.com/document/api/267/30829) | Gets screencapturing template list | 500 |
| [ModifyLiveSnapshotTemplate](https://www.tencentcloud.com/document/api/267/30828) | Modifies screencapturing template configuration | 200 |

## Authentication Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeLiveDomainReferer](https://www.tencentcloud.com/document/api/267/40611) | Queries referer allowlist/blocklist configuration of a live streaming domain name | 20 |
| [DescribeLivePlayAuthKey](https://www.tencentcloud.com/document/api/267/30772) | Queries the playback authentication key | 500 |
| [DescribeLivePushAuthKey](https://www.tencentcloud.com/document/api/267/30771) | Queries the push authentication key | 500 |
| [ModifyLiveDomainReferer](https://www.tencentcloud.com/document/api/267/40610) | Configures referer allowlist/blocklist of a live streaming domain name | 20 |
| [ModifyLivePlayAuthKey](https://www.tencentcloud.com/document/api/267/30770) | Modifies the playback authentication key | 100 |
| [ModifyLivePushAuthKey](https://www.tencentcloud.com/document/api/267/30769) | Modifies the push authentication key | 200 |

## Monitoring Data Query APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeAllStreamPlayInfoList](https://www.tencentcloud.com/document/api/267/37306) | Gets the playback data of all streams at a specified time point | 20 |
| [DescribeGroupProIspPlayInfoList](https://www.tencentcloud.com/document/api/267/36097) | Queries downstream playback data by district and ISP | 200 |
| [DescribeHttpStatusInfoList](https://www.tencentcloud.com/document/api/267/37305) | Queries the details of each playback HTTP status code | 200 |
| [DescribeLiveStreamPushInfoList](https://www.tencentcloud.com/document/api/267/37303) | Gets the push data of live streams | 500 |
| [DescribePlayErrorCodeDetailInfoList](https://www.tencentcloud.com/document/api/267/37301) | Queries the real-time data of each playback HTTP error code | 100 |
| [DescribePlayErrorCodeSumInfoList](https://www.tencentcloud.com/document/api/267/37300) | Queries the aggregated data of playback HTTP error codes | 200 |
| [DescribeProvinceIspPlayInfoList](https://www.tencentcloud.com/document/api/267/37299) | Queries the playback information by ISP and district | 200 |
| [DescribeStreamDayPlayInfoList](https://www.tencentcloud.com/document/api/267/36095) | Queries the traffic data of all streams | 500 |
| [DescribeStreamPlayInfoList](https://www.tencentcloud.com/document/api/267/37297) | Queries the playback information list of stream | 500 |
| [DescribeStreamPushInfoList](https://www.tencentcloud.com/document/api/267/36094) | Gets the push data of a stream | 40 |
| [DescribeTopClientIpSumInfoList](https://www.tencentcloud.com/document/api/267/37296) | Queries the information of top n client IPs in certain period of time | 100 |
| [DescribeVisitTopSumInfoList](https://www.tencentcloud.com/document/api/267/37295) | Queries the information of top n domain names or stream IDs in certain period of time | 100 |
| [DescribeLiveTranscodeDetailInfo](https://www.tencentcloud.com/document/api/267/37302) | Queries LVB transcoding statistics | 200 |

## Billing Data Query APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeDeliverBandwidthList](https://www.tencentcloud.com/document/api/267/37836) | Queries the billable bandwidth of live stream relaying | 20 |
| [DescribeLiveTimeShiftBillInfoList](https://www.tencentcloud.com/document/api/267/47919) | Queries time shift billing data | 20 |
| [DescribeLiveTranscodeTotalInfo](https://www.tencentcloud.com/document/api/267/44907) | Queries total usage of the transcoding service | 200 |
| [DescribeScreenShotSheetNumList](https://www.tencentcloud.com/document/api/267/37298) | Queries the number of screenshots | 100 |
| [DescribeTranscodeTaskNum](https://www.tencentcloud.com/document/api/267/50613) | Queries the number of transcoding tasks | 20 |
| [DescribeUploadStreamNums](https://www.tencentcloud.com/document/api/267/39500) | Queries the number of LVB upstream channels. | 20 |
| [DescribeConcurrentRecordStreamNum](https://www.tencentcloud.com/document/api/267/36188) | Queries the number of concurrent recording channels | 200 |
| [DescribeBillBandwidthAndFluxList](https://www.tencentcloud.com/document/api/267/36098) | Queries the data of billable bandwidth and traffic | 100 |

## Live Stream Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeLiveForbidStreamList](https://www.tencentcloud.com/document/api/267/30801) | Gets the list of forbidden streams. | 100 |
| [DescribeLiveStreamEventList](https://www.tencentcloud.com/document/api/267/30800) | Queries streaming events. | 300 |
| [DescribeLiveStreamOnlineList](https://www.tencentcloud.com/document/api/267/30798) | Queries live streams. | 100 |
| [DescribeLiveStreamPublishedList](https://www.tencentcloud.com/document/api/267/30797) | Queries the list of pushed streams. | 300 |
| [DropLiveStream](https://www.tencentcloud.com/document/api/267/30795) | Pauses a live stream | 100 |
| [ResumeLiveStream](https://www.tencentcloud.com/document/api/267/30793) | Resumes a live stream. | 100 |
| [DescribeLiveStreamState](https://www.tencentcloud.com/document/api/267/30796) | Queries stream status. | 300 |
| [ForbidLiveStream](https://www.tencentcloud.com/document/api/267/30794) | Forbids a live stream. | 200 |


---
*Source: [https://www.tencentcloud.com/document/product/267/30760](https://www.tencentcloud.com/document/product/267/30760)*
