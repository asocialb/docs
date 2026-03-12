# API Category

## Room Management APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [RemoveUser](https://www.tencentcloud.com/document/api/647/34268) | Removes a user | 20 |
| [SetUserBlocked](https://www.tencentcloud.com/document/api/647/51289) | Disables/Enables the audio and video of a user | 20 |
| [SetUserBlockedByStrRoomId](https://www.tencentcloud.com/document/api/647/51288) | Disables/Enables the audio and video of a user (string-type room ID) | 20 |
| [DismissRoom](https://www.tencentcloud.com/document/api/647/34269) | Dismisses a room | 20 |
| [RemoveUserByStrRoomId](https://www.tencentcloud.com/document/api/647/39630) | Removes a user from a room (by room ID in string type) | 20 |
| [DismissRoomByStrRoomId](https://www.tencentcloud.com/document/api/647/39631) | Closes a room (by room ID in string type) | 20 |

## Call Quality Monitoring APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeRoomInfo](https://www.tencentcloud.com/document/api/647/36754) | Queries the room list | 20 |
| [DescribeUnusualEvent](https://www.tencentcloud.com/document/api/647/37763) | Queries abnormal user experiences | 20 |
| [DescribeUserEvent](https://www.tencentcloud.com/document/api/647/37762) | Queries the events during a call | 20 |
| [DescribeCallDetailInfo](https://www.tencentcloud.com/document/api/647/55013) | Queries the user list and call metrics | 20 |
| [DescribeUserInfo](https://www.tencentcloud.com/document/api/647/39096) | Queries the user list | 20 |
| [DescribeScaleInfo](https://www.tencentcloud.com/document/api/647/36758) | Queries the number of rooms and users | 20 |

## Stream mixing and relay APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [UpdatePublishCdnStream](https://www.tencentcloud.com/document/api/647/48245) | Changes relaying parameters | 20 |
| [StartPublishCdnStream](https://www.tencentcloud.com/document/api/647/48247) | Starts a relaying task | 20 |
| [StopPublishCdnStream](https://www.tencentcloud.com/document/api/647/48246) | Stops a relaying task | 20 |

## On-cloud recording APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DeleteCloudRecording](https://www.tencentcloud.com/document/api/647/46959) | Stops an on-cloud recording task | 20 |
| [DescribeCloudRecording](https://www.tencentcloud.com/document/api/647/46958) | Queries the status of a recording task | 20 |
| [CreateCloudRecording](https://www.tencentcloud.com/document/api/647/46960) | Starts an on-cloud recording task | 20 |
| [ModifyCloudRecording](https://www.tencentcloud.com/document/api/647/46957) | Modifies a recording task | 20 |

## Usage Statistics APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeTrtcUsage](https://www.tencentcloud.com/document/api/647/54137) | Queries TRTC audio/video duration | 5 |
| [DescribeRecordingUsage](https://www.tencentcloud.com/document/api/647/54139) | Queries TRTC recording usage | 5 |
| [DescribeMixTranscodingUsage](https://www.tencentcloud.com/document/api/647/54140) | Queries TRTC On-Cloud MixTranscoding usage | 5 |
| [DescribeRelayUsage](https://www.tencentcloud.com/document/api/647/54138) | Queries TRTC relay to CDN usage | 5 |
| [DescribeTrtcRoomUsage](https://www.tencentcloud.com/document/api/647/54327) | Queries usage data grouped by room | - |

## Data Monitoring APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DescribeTRTCRealTimeScaleData](https://www.tencentcloud.com/document/api/647/58628) | Query TRTC Monitoring Dashboard - Real-Time Monitoring Scale | 20 |
| [DescribeTRTCRealTimeQualityData](https://www.tencentcloud.com/document/api/647/58629) | Query TRTC Monitoring Dashboard - Real-Time Monitoring Quality | 20 |
| [DescribeTRTCMarketScaleData](https://www.tencentcloud.com/document/api/647/58630) | Query TRTC Monitoring Dashboard - Data Dashboard Scale Metrics | 20 |
| [DescribeTRTCMarketQualityData](https://www.tencentcloud.com/document/api/647/58631) | Query TRTC Monitoring Dashboard - Data Dashboard Quality Metrics | 20 |

## Web Record APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [StartWebRecord](https://www.tencentcloud.com/document/api/647/72066) | Starts an web-page recording task | 20 |
| [DescribeWebRecord](https://www.tencentcloud.com/document/api/647/72067) | Queries the status of a web-page recording task | 20 |
| [StopWebRecord](https://www.tencentcloud.com/document/api/647/72065) | Stop an web-page recording task | 20 |

## Pull stream Relay Related interface

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [StopStreamIngest](https://www.tencentcloud.com/document/api/647/57834) | Stop Pull stream Relay | 20 |
| [DescribeStreamIngest](https://www.tencentcloud.com/document/api/647/57836) | Query Relay Task | 20 |
| [StartStreamIngest](https://www.tencentcloud.com/document/api/647/57835) | Start Pull stream Relay | 20 |
| [UpdateStreamIngest](https://www.tencentcloud.com/document/api/647/63238) | Update Relay Task | 20 |

## AI Service APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [StartAIConversation](https://www.tencentcloud.com/document/api/647/64963) | Start AI conversation task | 20 |
| [DescribeAIConversation](https://www.tencentcloud.com/document/api/647/64964) | Describe AI conversation | 20 |
| [StopAIConversation](https://www.tencentcloud.com/document/api/647/65296) | Stop AI conversation task | 20 |
| [DescribeAITranscription](https://www.tencentcloud.com/document/api/647/64968) | Describe AI Transcription | 20 |
| [StopAITranscription](https://www.tencentcloud.com/document/api/647/64966) | Stop AI Transcription task | 20 |
| [ControlAIConversation](https://www.tencentcloud.com/document/api/647/64965) | Control AI dialogue | 50 |
| [StartAITranscription](https://www.tencentcloud.com/document/api/647/64967) | Start AI transcription task | 50 |
| [UpdateAIConversation](https://www.tencentcloud.com/document/api/647/64962) | Update AI conversation task | 20 |

## Cloud Slicing APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [CreateCloudSliceTask](https://www.tencentcloud.com/document/api/647/72331) | Creates a cloud slicing task | 20 |
| [DeleteCloudSliceTask](https://www.tencentcloud.com/document/api/647/72330) | Stops a cloud slicing task | 20 |
| [DescribeCloudSliceTask](https://www.tencentcloud.com/document/api/647/72329) | Queries information about cloud slicing tasks | 20 |
| [ModifyCloudSliceTask](https://www.tencentcloud.com/document/api/647/72328) | Modifies a cloud slicing task | 20 |

## Cloud Moderation APIs

| API Name | Feature | Frequency Limit (maximum requests per second) |
| --- | --- | --- |
| [DeleteCloudModeration](https://www.tencentcloud.com/document/api/647/72647) | Stops cloud moderation | 20 |
| [DescribeCloudModeration](https://www.tencentcloud.com/document/api/647/72646) | Queries cloud moderation information | 20 |
| [ModifyCloudModeration](https://www.tencentcloud.com/document/api/647/72645) | Modifies cloud moderation tasks | 20 |
| [CreateCloudModeration](https://www.tencentcloud.com/document/api/647/72648) | Creates cloud moderation tasks | 20 |


---
*Source: [https://trtc.io/document/34260](https://trtc.io/document/34260)*
