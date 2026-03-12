# History

## Release 39

Release time: 2025-07-10 16:12:06

Release updates:

Improvement to existing documentation.

New APIs:

CreateLivePadRule

## Release 38

Release time: 2025-07-10 16:10:52

Release updates:

Improvement to existing documentation.

New APIs:

CreateLivePadTemplate

## Release 37

Release time: 2025-07-07 11:26:29

Release updates:

Improvement to existing documentation.

New APIs:

StopLivePadStream

## Release 36

Release time: 2025-07-01 20:14:06

Release updates:

Improvement to existing documentation.

New APIs:

StartLivePadStream

## Release 35

Release time: 2023-09-20 11:38:24

Release updates:

Improvement to existing documentation.

New APIs:

RestartLivePullStreamTask

## Release 34

Release time: 2023-09-20 10:28:23

Release updates:

Improvement to existing documentation.

Modified data structures:

PullStreamTaskInfo
New members:RecordTemplateId, BackupToUrl

## Release 33

Release time: 2023-07-25 15:54:49

Release updates:

Improvement to existing documentation.

New APIs:

DescribeRecordTask

New data structures:

RecordTask

## Release 32

Release time: 2023-05-15 11:50:28

Release updates:

Improvement to existing documentation.

New APIs:

DescribeBillBandwidthAndFluxList

New data structures:

BillDataInfo

## Release 31

Release time: 2023-04-28 10:49:30

Release updates:

Improvement to existing documentation.

New APIs:

CreateScreenshotTask

Modified data structures:

CallBackTemplateInfo
New members:AudioAuditNotifyUrl

## Release 30

Release time: 2023-02-21 16:13:45

Release updates:

Improvement to existing documentation.

New APIs:

CreateLiveTimeShiftRule
CreateLiveTimeShiftTemplate
DeleteLiveTimeShiftRule
DeleteLiveTimeShiftTemplate
DescribeLiveTimeShiftRules
DescribeLiveTimeShiftTemplates
DescribeTimeShiftRecordDetail
DescribeTimeShiftStreamList
ModifyLiveTimeShiftTemplate

New data structures:

TimeShiftRecord
TimeShiftStreamInfo
TimeShiftTemplate

## Release 29

Release time: 2023-01-17 17:37:46

Release updates:

Improvement to existing documentation.

Modified data structures:

CallBackRuleInfo
Modified members:
CreateTime, UpdateTime, TemplateId, DomainName, AppName
CertInfo
Modified members:
CertId, CertName, Description, CreateTime, HttpsCrt, CertType, CertExpireTime, DomainList
DomainCertInfo
Modified members:
CertId, CertName, Description, CreateTime, HttpsCrt, CertType, CertExpireTime, DomainName, Status, CertDomains, CloudCertId
DomainInfo
Modified members:
Name, Type, Status, CreateTime, BCName, TargetDomain, PlayType, IsDelayLive, CurrentCName, RentTag, RentExpireTime, IsMiniProgramLive
ForbidStreamInfo
Modified members:
StreamName, CreateTime, ExpireTime, AppName, DomainName
LiveDomainCertBindings
Modified members:
DomainName, CertificateAlias, CertType, Status, CertExpireTime, CertId, CloudCertId, UpdateTime
RuleInfo
Modified members:
CreateTime, UpdateTime, TemplateId, DomainName, AppName, StreamName
WatermarkInfo
Modified members:
WatermarkId, PictureUrl, XPosition, YPosition, WatermarkName, Status, CreateTime, Width, Height

## Release 28

Release time: 2023-01-03 15:23:15

Release updates:

Improvement to existing documentation.

New APIs:

DescribeAllStreamPlayInfoList
DescribeStreamPushInfoList

Modified APIs:

CreateLiveCallbackTemplate
New input parameters:PushExceptionNotifyUrl
ModifyLiveCallbackTemplate
New input parameters:PushExceptionNotifyUrl

New data structures:

MonitorStreamPlayInfo
PushQualityData

Modified data structures:

CallBackTemplateInfo
New members:PushExceptionNotifyUrl

## Release 27

Release time: 2022-11-16 17:08:10

Release updates:

Improvement to existing documentation.

Modified APIs:

CreateLivePullStreamTask
New input parameters:VodLocalMode
ModifyLivePullStreamTask
New input parameters:VodLocalMode

Modified data structures:

PullStreamTaskInfo
New members:VodLocalMode

## Release 26

Release time: 2022-11-08 11:19:20

Release updates:

Improvement to existing documentation.

New APIs:

DropLiveStream

Modified data structures:

TranscodeDetailInfo
New members:MainlandOrOversea

## Release 25

Release time: 2022-10-08 11:02:57

Release updates:

Improvement to existing documentation.

New APIs:

AuthenticateDomainOwner
DescribeTranscodeTaskNum

Modified APIs:

AddLiveDomain
New input parameters:VerifyOwnerType
ModifyLiveSnapshotTemplate
Modified input parameters:
CosAppId, CosBucket, CosRegion

New data structures:

TranscodeTaskNum

## Release 24

Release time: 2022-08-31 10:17:40

Release updates:

Improvement to existing documentation.

Modified APIs:

ModifyLivePullStreamTask
New input parameters:WatermarkList

Modified data structures:

PullPushWatermarkInfo
New members:Location
Deleted members:
WatermarkId, WatermarkName, Status, CreateTime
PullStreamTaskInfo
New members:BackupSourceType, BackupSourceUrl, WatermarkList

## Release 23

Release time: 2022-08-23 14:24:31

Release updates:

Improvement to existing documentation.

New APIs:

DescribeLiveDomainCertBindings
ModifyLiveDomainCertBindings

**Deleted APIs:**

BindLiveDomainCert
CreateLiveCert
DeleteLiveCert
ModifyLiveCert
ModifyLiveDomainCert

Modified APIs:

CreateLivePullStreamTask
New input parameters:WatermarkList
DescribeLiveDomains
New output parameters:PlayTypeCount

New data structures:

BatchDomainOperateErrors
LiveCertDomainInfo
LiveDomainCertBindings
PullPushWatermarkInfo

Modified data structures:

ForbidStreamInfo
New members:AppName, DomainName

## Release 22

Release time: 2022-07-06 14:59:45

Release updates:

Improvement to existing documentation.

New APIs:

CreateLivePullStreamTask
DeleteLivePullStreamTask
DescribeLivePullStreamTasks
ModifyLivePullStreamTask

New data structures:

PullStreamTaskInfo
RecentPullInfo

## Release 21

Release time: 2022-06-30 15:37:50

Release updates:

Improvement to existing documentation.

Modified APIs:

CreateLiveTranscodeTemplate
New input parameters:DRMType, DRMTracks
ModifyLiveTranscodeTemplate
New input parameters:DRMType, DRMTracks

Modified data structures:

TemplateInfo
New members:DRMType, DRMTracks

## Release 20

Release time: 2022-06-24 15:41:09

Release updates:

Improvement to existing documentation.

New APIs:

DescribeLiveTimeShiftBillInfoList

New data structures:

TimeShiftBillData

## Release 19

Release time: 2022-06-15 16:16:30

Release updates:

Improvement to existing documentation.

**Deleted APIs:**

DescribeAllStreamPlayInfoList
DescribeAreaBillBandwidthAndFluxList
DescribeLiveDomainPlayInfoList
DescribeProIspPlaySumInfoList
DropLiveStream

Modified APIs:

CreateLiveRecordTemplate
New input parameters:FlvSpecialParam
ModifyLiveRecordTemplate
New input parameters:FlvSpecialParam

New data structures:

FlvSpecialParam

**Deleted data structures:**

BillAreaInfo
BillCountryInfo
BillDataInfo
DomainDetailInfo
DomainInfoList
MonitorStreamPlayInfo
ProIspPlaySumInfo

Modified data structures:

RecordTemplateInfo
New members:FlvSpecialParam

## Release 18

Release time: 2022-03-31 15:46:30

Release updates:

Improvement to existing documentation.

**Deleted APIs:**

DescribeBillBandwidthAndFluxList
DescribeStreamPushInfoList

Modified APIs:

CreateLiveRecordTemplate
New input parameters:RemoveWatermark
ModifyLiveRecordTemplate
New input parameters:RemoveWatermark

**Deleted data structures:**

PushQualityData

Modified data structures:

RecordTemplateInfo
New members:RemoveWatermark

## Release 17

Release time: 2022-01-24 14:29:35

Release updates:

Improvement to existing documentation.

New APIs:

DescribeLiveTranscodeTotalInfo

New data structures:

TranscodeTotalInfo

## Release 16

Release time: 2022-01-19 14:55:06

Release updates:

Improvement to existing documentation.

Modified APIs:

DescribeBillBandwidthAndFluxList
New input parameters:RegionNames

## Release 15

Release time: 2021-11-10 17:38:35

Release updates:

Improvement to existing documentation.

Modified APIs:

DescribeLiveDomains
New input parameters:PlayType

## Release 14

Release time: 2021-09-14 10:19:36

Release updates:

Improvement to existing documentation.

Modified APIs:

DescribeLiveDomains
New output parameters:CreateLimitCount

## Release 13

Release time: 2021-08-06 15:40:33

Release updates:

Improvement to existing documentation.

Modified APIs:

UnBindLiveDomainCert
New input parameters:Type

## Release 12

Release time: 2021-07-19 16:40:55

Release updates:

Improvement to existing documentation.

Modified data structures:

RecordParam
New members:Procedure, StorageMode, ClassId

## Release 11

Release time: 2021-06-04 11:41:54

Release updates:

Improvement to existing documentation.

New APIs:

DescribeLiveDomainReferer
ModifyLiveDomainReferer

New data structures:

RefererAuthConfig

## Release 10

Release time: 2021-05-12 19:12:07

Release updates:

Improvement to existing documentation.

Modified APIs:

DescribeAllStreamPlayInfoList
New input parameters:PlayDomains
DescribeStreamDayPlayInfoList
New input parameters:MainlandOrOversea, ServiceName

## Release 9

Release time: 2021-05-10 14:50:39

Release updates:

Improvement to existing documentation.

Modified APIs:

DescribeLiveForbidStreamList
New input parameters:StreamName

Modified data structures:

CommonMixControlParams
New members:PassInputSei

## Release 8

Release time: 2021-04-15 16:24:25

Release updates:

Improvement to existing documentation.

Modified data structures:

PushQualityData
New members:StreamParam

## Release 7

Release time: 2021-02-03 17:31:24

Release updates:

Improvement to existing documentation.

Modified APIs:

DescribeStreamPlayInfoList
New input parameters:ServiceName

## Release 6

Release time: 2021-01-27 15:16:31

Release updates:

Improvement to existing documentation.

New APIs:

DescribeUploadStreamNums

Modified APIs:

DescribeProvinceIspPlayInfoList
New input parameters:IpType

## Release 5

Release time: 2021-01-07 19:36:46

Release updates:

Improvement to existing documentation.

Modified data structures:

DomainCertInfo
New members:CertDomains, CloudCertId

## Release 4

Release time: 2020-10-16 18:30:51

Release updates:

Improvement to existing documentation.

New APIs:

DescribeAreaBillBandwidthAndFluxList

New data structures:

BillAreaInfo
BillCountryInfo

Modified data structures:

TemplateInfo
New members:ShortEdgeAsHeight

## Release 3

Release time: 2020-09-25 11:40:32

Release updates:

Improvement to existing documentation.

Modified APIs:

CreateLiveTranscodeTemplate
New input parameters:ShortEdgeAsHeight
DescribeLiveTranscodeRules
New input parameters:TemplateIds, DomainNames
ModifyLiveTranscodeTemplate
New input parameters:ShortEdgeAsHeight

## Release 2

Release time: 2020-08-06 19:42:55

Release updates:

Improvement to existing documentation.

New APIs:

DescribeDeliverBandwidthList

New data structures:

BandwidthInfo

Modified data structures:

CommonMixControlParams
New members:AllowCopy

## Existing Release

Release time: 2020-07-30 20:02:43

Existing APIs/data structures are as follows:

Improvement to existing documentation.

Existing APIs:

AddDelayLiveStream
AddLiveDomain
AddLiveWatermark
BindLiveDomainCert
CancelCommonMixStream
CreateCommonMixStream
CreateLiveCallbackRule
CreateLiveCallbackTemplate
CreateLiveCert
CreateLiveRecord
CreateLiveRecordRule
CreateLiveRecordTemplate
CreateLiveSnapshotRule
CreateLiveSnapshotTemplate
CreateLiveTranscodeRule
CreateLiveTranscodeTemplate
CreateLiveWatermarkRule
CreateRecordTask
DeleteLiveCallbackRule
DeleteLiveCallbackTemplate
DeleteLiveCert
DeleteLiveDomain
DeleteLiveRecord
DeleteLiveRecordRule
DeleteLiveRecordTemplate
DeleteLiveSnapshotRule
DeleteLiveSnapshotTemplate
DeleteLiveTranscodeRule
DeleteLiveTranscodeTemplate
DeleteLiveWatermark
DeleteLiveWatermarkRule
DeleteRecordTask
DescribeAllStreamPlayInfoList
DescribeBillBandwidthAndFluxList
DescribeConcurrentRecordStreamNum
DescribeGroupProIspPlayInfoList
DescribeHttpStatusInfoList
DescribeLiveCallbackRules
DescribeLiveCallbackTemplate
DescribeLiveCallbackTemplates
DescribeLiveCert
DescribeLiveCerts
DescribeLiveDelayInfoList
DescribeLiveDomain
DescribeLiveDomainCert
DescribeLiveDomainPlayInfoList
DescribeLiveDomains
DescribeLiveForbidStreamList
DescribeLivePlayAuthKey
DescribeLivePushAuthKey
DescribeLiveRecordRules
DescribeLiveRecordTemplate
DescribeLiveRecordTemplates
DescribeLiveSnapshotRules
DescribeLiveSnapshotTemplate
DescribeLiveSnapshotTemplates
DescribeLiveStreamEventList
DescribeLiveStreamOnlineList
DescribeLiveStreamPublishedList
DescribeLiveStreamPushInfoList
DescribeLiveStreamState
DescribeLiveTranscodeDetailInfo
DescribeLiveTranscodeRules
DescribeLiveTranscodeTemplate
DescribeLiveTranscodeTemplates
DescribeLiveWatermark
DescribeLiveWatermarkRules
DescribeLiveWatermarks
DescribePlayErrorCodeDetailInfoList
DescribePlayErrorCodeSumInfoList
DescribeProIspPlaySumInfoList
DescribeProvinceIspPlayInfoList
DescribeScreenShotSheetNumList
DescribeStreamDayPlayInfoList
DescribeStreamPlayInfoList
DescribeStreamPushInfoList
DescribeTopClientIpSumInfoList
DescribeVisitTopSumInfoList
DropLiveStream
EnableLiveDomain
ForbidLiveDomain
ForbidLiveStream
ModifyLiveCallbackTemplate
ModifyLiveCert
ModifyLiveDomainCert
ModifyLivePlayAuthKey
ModifyLivePlayDomain
ModifyLivePushAuthKey
ModifyLiveRecordTemplate
ModifyLiveSnapshotTemplate
ModifyLiveTranscodeTemplate
ResumeDelayLiveStream
ResumeLiveStream
StopLiveRecord
StopRecordTask
UnBindLiveDomainCert
UpdateLiveWatermark

Existing data structures:

BillDataInfo
CallBackRuleInfo
CallBackTemplateInfo
CdnPlayStatData
CertInfo
ClientIpPlaySumInfo
CommonMixControlParams
CommonMixCropParams
CommonMixInputParam
CommonMixLayoutParams
CommonMixOutputParams
ConcurrentRecordStreamNum
DayStreamPlayInfo
DelayInfo
DomainCertInfo
DomainDetailInfo
DomainInfo
DomainInfoList
ForbidStreamInfo
GroupProIspDataInfo
HlsSpecialParam
HttpCodeInfo
HttpCodeValue
HttpStatusData
HttpStatusInfo
MonitorStreamPlayInfo
PlayAuthKeyInfo
PlayCodeTotalInfo
PlayDataInfoByStream
PlayStatInfo
PlaySumStatInfo
ProIspPlayCodeDataInfo
ProIspPlaySumInfo
PublishTime
PushAuthKeyInfo
PushDataInfo
PushQualityData
RecordParam
RecordTemplateInfo
RuleInfo
SnapshotTemplateInfo
StreamEventInfo
StreamName
StreamOnlineInfo
TemplateInfo
TimeValue
TranscodeDetailInfo
WatermarkInfo


---
*Source: [https://www.tencentcloud.com/document/product/267/30766](https://www.tencentcloud.com/document/product/267/30766)*
