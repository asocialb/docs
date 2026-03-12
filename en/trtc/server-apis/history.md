# History

## Release 40

Release time: 2026-01-22 14:43:57

Release updates:

Improvement to existing documentation.

Modified data structures:

MixLayoutParams
New members:PureAudioDisableLayout
RecordParams
New members:FillType, SubscribeAbility

## Release 39

Release time: 2026-01-21 14:24:54

Release updates:

Improvement to existing documentation.

Modified APIs:

ControlAIConversation
New input parameters:InvokeLLM

New data structures:

InvokeLLM

Modified data structures:

ServerPushText
New members:Audio, DropMode, Priority, AddHistory, MetaInfo

## Release 38

Release time: 2025-09-25 22:51:58

Release updates:

Improvement to existing documentation.

Modified APIs:

StartAITranscription
New input parameters:TranslationConfig

New data structures:

TTSConfig
Terminology
TranslationConfig

## Release 37

Release time: 2025-08-14 16:14:37

Release updates:

Improvement to existing documentation.

New APIs:

CreateCloudModeration
DeleteCloudModeration
DescribeCloudModeration
ModifyCloudModeration

New data structures:

CloudModerationStorage
ModerationParams
ModerationStorageParams
ModerationSupplierParam
SubscribeModerationUserIds

## Release 36

Release time: 2025-08-06 16:19:00

Release updates:

Improvement to existing documentation.

New APIs:

CreateCloudSliceTask
DeleteCloudSliceTask
DescribeCloudSliceTask
ModifyCloudSliceTask

New data structures:

CloudSliceStorage
SliceParams
SliceStorageParams

## Release 35

Release time: 2025-07-22 15:44:41

Release updates:

Improvement to existing documentation.

New APIs:

DescribeWebRecord
StartWebRecord
StopWebRecord

New data structures:

EmulateMobileParams
WebRecordVideoParams

## Release 34

Release time: 2025-07-14 10:52:39

Release updates:

Improvement to existing documentation.

Modified APIs:

StartPublishCdnStream
New input parameters:RecordParams

New data structures:

McuCloudVod
McuRecordParams
McuStorageParams
McuTencentVod

## Release 33

Release time: 2024-12-30 11:47:01

Release updates:

Improvement to existing documentation.

Modified APIs:

UpdateStreamIngest
New input parameters:IsPause

## Release 32

Release time: 2024-11-20 17:56:59

Release updates:

Improvement to existing documentation.

Modified APIs:

StartStreamIngest
New input parameters:Volume
UpdateStreamIngest
New input parameters:Volume
Modified input parameters:
StreamUrl

Modified data structures:

AudioEncodeParams
Modified members:
SampleRate, Channel, BitRate
VideoEncodeParams
Modified members:
Width, Height, Fps, BitRate, Gop

## Release 31

Release time: 2024-10-24 21:28:08

Release updates:

Improvement to existing documentation.

New APIs:

StopAIConversation

## Release 30

Release time: 2024-10-22 15:06:52

Release updates:

Improvement to existing documentation.

New APIs:

DescribeAITranscription
StartAITranscription
StopAITranscription

New data structures:

RecognizeConfig
TranscriptionParams

## Release 29

Release time: 2024-10-22 15:06:19

Release updates:

Improvement to existing documentation.

New APIs:

ControlAIConversation
DescribeAIConversation
StartAIConversation
UpdateAIConversation

New data structures:

AgentConfig
STTConfig
ServerPushText

## Release 28

Release time: 2024-08-13 11:43:31

Release updates:

Improvement to existing documentation.

New APIs:

UpdateStreamIngest

Modified APIs:

StartStreamIngest
New input parameters:SeekSecond, AutoPush, RepeatNum, MaxDuration
Deprecate input parameters:
VideoEncodeParams, AudioEncodeParams, SourceUrl

## Release 27

Release time: 2024-07-22 15:13:00

Release updates:

Improvement to existing documentation.

Modified APIs:

StartStreamIngest
New input parameters:StreamUrl
Modified input parameters:
SourceUrl

## Release 26

Release time: 2024-01-25 19:47:42

Release updates:

Improvement to existing documentation.

New APIs:

DescribeTRTCMarketQualityData
DescribeTRTCMarketScaleData
DescribeTRTCRealTimeQualityData
DescribeTRTCRealTimeScaleData

New data structures:

RowValues
SeriesInfos
TRTCDataResult

## Release 25

Release time: 2023-11-24 16:25:45

Release updates:

Improvement to existing documentation.

New APIs:

DescribeStreamIngest
StartStreamIngest
StopStreamIngest

New data structures:

AudioEncodeParams
VideoEncodeParams

## Release 24

Release time: 2023-07-28 15:26:39

Release updates:

Improvement to existing documentation.

Modified data structures:

McuLayout
New members:BackgroundRenderMode
McuVideoParams
New members:BackgroundRenderMode

## Release 23

Release time: 2023-05-12 11:26:05

Release updates:

Improvement to existing documentation.

New APIs:

DescribeCallDetailInfo
DescribeRoomInfo
DescribeScaleInfo
DescribeUnusualEvent
DescribeUserEvent
DescribeUserInfo

Modified APIs:

DescribeTrtcRoomUsage
New output parameters:Data

New data structures:

AbnormalEvent
AbnormalExperience
EventList
EventMessage
QualityData
RoomState
ScaleInfomation
TimeValue
UserInformation
WaterMarkChar
WaterMarkTimestamp

Modified data structures:

McuLayoutParams
New members:RenderMode
WaterMark
New members:WaterMarkChar, WaterMarkTimestamp

## Release 22

Release time: 2023-03-31 11:13:18

Release updates:

Improvement to existing documentation.

New APIs:

DescribeTrtcRoomUsage

## Release 21

Release time: 2023-03-17 11:38:29

Release updates:

Improvement to existing documentation.

New APIs:

DescribeMixTranscodingUsage
DescribeRecordingUsage
DescribeRelayUsage
DescribeTrtcUsage

New data structures:

McuWaterMarkText
TrtcUsage

Modified data structures:

McuWaterMarkParams
New members:WaterMarkText

## Release 20

Release time: 2023-03-14 16:04:41

Release updates:

Improvement to existing documentation.

Modified data structures:

McuLayoutVolume
New members:Interval, FollowIdr
McuPassThrough
New members:Interval, FollowIdr

## Release 19

Release time: 2023-03-02 17:29:46

Release updates:

Improvement to existing documentation.

Modified data structures:

RecordParams
New members:MediaId

## Release 18

Release time: 2022-12-16 15:45:24

Release updates:

Improvement to existing documentation.

Modified data structures:

MixLayoutParams
New members:RenderMode, MaxResolutionUserAlign
RecordParams
New members:MaxMediaFileDuration
TencentVod
New members:UserDefineRecordId

## Release 17

Release time: 2022-11-10 16:45:18

Release updates:

Improvement to existing documentation.

New APIs:

SetUserBlocked
SetUserBlockedByStrRoomId

## Release 16

Release time: 2022-11-03 14:29:50

Release updates:

Improvement to existing documentation.

Modified APIs:

StartPublishCdnStream
New input parameters:FeedBackRoomParams
UpdatePublishCdnStream
New input parameters:FeedBackRoomParams

New data structures:

McuFeedBackRoomParams

Modified data structures:

McuAudioParams
New members:UnSubscribeAudioList

## Release 15

Release time: 2022-09-20 10:16:48

Release updates:

Improvement to existing documentation.

New data structures:

McuCustomCrop

Modified data structures:

McuLayout
New members:CustomCrop
RecordParams
New members:AvMerge
TencentVod
New members:MediaType

## Release 14

Release time: 2022-08-19 10:23:41

Release updates:

Improvement to existing documentation.

Modified APIs:

StartPublishCdnStream
New input parameters:SeiParams
UpdatePublishCdnStream
New input parameters:SeiParams

New data structures:

McuLayoutVolume
McuPassThrough
McuSeiParams

Modified data structures:

McuWaterMarkParams
New members:WaterMarkType

## Release 13

Release time: 2022-07-04 11:00:48

Release updates:

Improvement to existing documentation.

New APIs:

StartPublishCdnStream
StopPublishCdnStream
UpdatePublishCdnStream

New data structures:

AgentParams
AudioEncode
MaxVideoUser
McuAudioParams
McuLayout
McuLayoutParams
McuPublishCdnParam
McuUserInfoParams
McuVideoParams
McuWaterMarkImage
McuWaterMarkParams
MixUserInfo
SingleSubscribeParams
UserMediaStream
VideoEncode

## Release 12

Release time: 2022-05-11 15:16:52

Release updates:

Improvement to existing documentation.

New APIs:

CreateCloudRecording
DeleteCloudRecording
DescribeCloudRecording
ModifyCloudRecording

**Deleted APIs:**

CreatePicture
CreateTroubleInfo
DeletePicture
DescribeAbnormalEvent
DescribeCallDetail
DescribeDetailEvent
DescribeHistoryScale
DescribePicture
DescribeRecordStatistic
DescribeRoomInformation
DescribeTrtcInteractiveTime
DescribeTrtcMcuTranscodeTime
DescribeUserInformation
ModifyPicture
StartMCUMixTranscode
StartMCUMixTranscodeByStrRoomId
StopMCUMixTranscode
StopMCUMixTranscodeByStrRoomId

New data structures:

AudioParams
CloudStorage
CloudVod
MixLayout
MixLayoutParams
MixTranscodeParams
RecordParams
StorageFile
StorageParams
SubscribeStreamUserIds
TencentVod
VideoParams
WaterMark
WaterMarkImage

**Deleted data structures:**

AbnormalEvent
AbnormalExperience
EncodeParams
EventList
EventMessage
LayoutParams
OneSdkAppIdTranscodeTimeUsagesInfo
OneSdkAppIdUsagesInfo
OutputParams
PictureInfo
PresetLayoutConfig
PublishCdnParams
QualityData
RecordUsage
RoomState
ScaleInfomation
SdkAppIdRecordUsage
SdkAppIdTrtcMcuTranscodeTimeUsage
SdkAppIdTrtcUsage
SmallVideoLayoutParams
TimeValue
UserInformation
WaterMarkParams

## Release 11

Release time: 2021-11-09 10:13:12

Release updates:

Improvement to existing documentation.

New APIs:

DescribeRecordStatistic
DescribeTrtcInteractiveTime
DescribeTrtcMcuTranscodeTime

**Deleted APIs:**

DescribeRealtimeNetwork
DescribeRealtimeQuality
DescribeRealtimeScale

New data structures:

OneSdkAppIdTranscodeTimeUsagesInfo
OneSdkAppIdUsagesInfo
RecordUsage
SdkAppIdRecordUsage
SdkAppIdTrtcMcuTranscodeTimeUsage
SdkAppIdTrtcUsage

**Deleted data structures:**

RealtimeData

## Release 10

Release time: 2021-10-27 16:00:34

Release updates:

Improvement to existing documentation.

Modified data structures:

EncodeParams
New members:BackgroundImageUrl
WaterMarkParams
New members:WaterMarkUrl

## Release 9

Release time: 2021-06-15 16:57:07

Release updates:

Improvement to existing documentation.

New data structures:

WaterMarkParams

Modified data structures:

LayoutParams
New members:WaterMarkParams

## Release 8

Release time: 2021-04-28 11:08:14

Release updates:

Improvement to existing documentation.

New APIs:

CreatePicture
DeletePicture
DescribePicture
ModifyPicture

New data structures:

PictureInfo

## Release 7

Release time: 2021-04-07 19:54:14

Release updates:

Improvement to existing documentation.

Modified data structures:

EncodeParams
New members:AudioCodec

## Release 6

Release time: 2021-02-20 17:51:34

Release updates:

Improvement to existing documentation.

New APIs:

StartMCUMixTranscodeByStrRoomId
StopMCUMixTranscodeByStrRoomId

Modified data structures:

LayoutParams
New members:PureAudioHoldPlaceMode

## Release 5

Release time: 2021-02-19 16:22:07

Release updates:

Improvement to existing documentation.

New APIs:

DismissRoomByStrRoomId
RemoveUserByStrRoomId

## Release 4

Release time: 2021-01-21 17:40:36

Release updates:

Improvement to existing documentation.

Modified APIs:

StartMCUMixTranscode
New input parameters:PublishCdnParams

New data structures:

PublishCdnParams

Modified data structures:

LayoutParams
New members:PlaceHolderMode
PresetLayoutConfig
New members:MixInputType, PlaceImageId

## Release 3

Release time: 2020-12-21 17:07:47

Release updates:

Improvement to existing documentation.

New APIs:

DescribeUserInformation

New data structures:

PresetLayoutConfig

Modified data structures:

LayoutParams
New members:PresetLayoutConfig

## Release 2

Release time: 2020-09-25 11:41:53

Release updates:

Improvement to existing documentation.

Modified APIs:

DescribeCallDetail
New input parameters:PageNumber, PageSize

Modified data structures:

LayoutParams
New members:MixVideoUids

## Existing Release

Release time: 2020-07-30 20:35:23

Existing APIs/data structures are as follows:

Improvement to existing documentation.

Existing APIs:

CreateTroubleInfo
DescribeAbnormalEvent
DescribeCallDetail
DescribeDetailEvent
DescribeHistoryScale
DescribeRealtimeNetwork
DescribeRealtimeQuality
DescribeRealtimeScale
DescribeRoomInformation
DismissRoom
RemoveUser
StartMCUMixTranscode
StopMCUMixTranscode

Existing data structures:

AbnormalEvent
AbnormalExperience
EncodeParams
EventList
EventMessage
LayoutParams
OutputParams
QualityData
RealtimeData
RoomState
ScaleInfomation
SmallVideoLayoutParams
TimeValue
UserInformation


---
*Source: [https://trtc.io/document/38192](https://trtc.io/document/38192)*
