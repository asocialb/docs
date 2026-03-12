# Data Types

## AbnormalEvent

The information of an error event (the possible cause of an abnormal user experience).

Used by actions: DescribeUnusualEvent.

| Name | Type | Description |
| --- | --- | --- |
| AbnormalEventId | Integer | The error event ID. For details, see https://www.tencentcloud.com/document/product/647/37906?has_map=1 |
| PeerId | String | The remote user ID. If this parameter is empty, it indicates that the error event is not associated with a remote user. Note: This field may return null, indicating that no valid values can be obtained. |

## AbnormalExperience

The information of an abnormal user experience and the possible causes.

Used by actions: DescribeUnusualEvent.

| Name | Type | Description |
| --- | --- | --- |
| UserId | String | The user ID. |
| ExperienceId | Integer | The abnormal experience ID. |
| RoomId | String | The room ID (string). |
| AbnormalEventList | Array of [AbnormalEvent](#AbnormalEvent) | The possible error events. |
| EventTime | Integer | The report time. |

## AgentConfig

Robot parameters

Used by actions: StartAIConversation.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserId | String | Yes | The robot's UserId is used to enter a room and initiate tasks. [Note] This UserId cannot be repeated with the host viewer [UserId](https://intl.cloud.tencent.com/document/product/647/37714) in the current room. If multiple tasks are initiated in a room, the robot's UserId cannot be repeated, otherwise the previous task will be interrupted. The robot's UserId must be unique in the room. |
| UserSig | String | Yes | The verification signature corresponding to the robot's UserId, that is, UserId and UserSig are equivalent to the robot's login password to enter the room. For the specific calculation method, please refer to the TRTC calculation [UserSig](https://cloud.tencent.com/document/product/647/45910#UserSig) solution. |
| TargetUserId | String | Yes | The UserId of the robot pulling the media stream. After filling in, the robot will pull the media stream of the UserId for real-time processing |
| MaxIdleTime | Integer | No | If there is no streaming in the room for more than MaxIdleTime, the Service will automatically close the task. The default value is 60s. |
| WelcomeMessage | String | No | Robot's welcome message |
| InterruptMode | Integer | No | Intelligent interruption mode, the default value is 0, 0 means the server automatically interrupts, 1 means the server does not interrupt, and the client sends an interrupt signal to interrupt |
| InterruptSpeechDuration | Integer | No | Used when InterruptMode is 0, in milliseconds, with a default value of 500ms. This means that the server will interrupt when it detects a human voice that lasts for InterruptSpeechDuration milliseconds. |

## AgentParams

The information of the relaying robot in the room.

Used by actions: StartPublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserId | String | Yes | The [user ID](https://intl.cloud.tencent.com/document/product/647/37714) of the relaying robot in the TRTC room, which cannot be the same as a user ID already in use. We recommend you include the room ID in this user ID. |
| UserSig | String | No | The signature (similar to a login password) required for the relaying robot to enter the room. For information on how to calculate the signature, see [What is UserSig?](https://intl.cloud.tencent.com/document/product/647/38104). \| |
| MaxIdleTime | Integer | No | The timeout period (seconds) for relaying to stop automatically after all the users whose streams are mixed leave the room. The value cannot be smaller than 5 or larger than 86400 (24 hours). Default value: 30. |

## AudioEncode

The audio encoding parameters.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SampleRate | Integer | Yes | The audio sample rate (Hz). Valid values: 48000, 44100, 32000, 24000, 16000, 8000. |
| Channel | Integer | Yes | The number of sound channels. Valid values: 1 (mono), 2 (dual). |
| BitRate | Integer | Yes | The audio bitrate (Kbps). Value range: 8-500. |
| Codec | Integer | No | The audio codec. Valid values: 0 (LC-AAC), 1 (HE-AAC), 2 (HE-AACv2). The default value is 0. If this parameter is set to 2, `Channel` must be 2. If it is set to 1 or 2, `SampleRate` can only be 48000, 44100, 32000, 24000, or 16000. |

## AudioParams

The audio transcoding parameters for recording.

Used by actions: CreateCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SampleRate | Integer | Yes | The audio sample rate. 1: 48000 Hz (default) 2: 44100 Hz 3: 16000 Hz |
| Channel | Integer | Yes | The number of sound channels. 1: Mono-channel 2: Dual-channel (default) |
| BitRate | Integer | Yes | The audio bitrate (bps). Value range: [32000, 128000]. Default: 64000. |

## CloudModerationStorage

Information about Tencent COS and third-party cloud storage accounts.

Used by actions: CreateCloudModeration.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Vendor | Integer | Yes | Information about Tencent COS and third-party cloud storage accounts. 0: Tencent COS. 1: AWS S3. 2: Alibaba Cloud OSS. Example value: 0. |
| Region | String | Yes | [Region information](https://www.tencentcloud.com/document/product/436/6224?from_cn_redirect=1#.E5.9C.B0.E5.9F.9F) of Tencent COS. Example value: cn-shanghai-1.  [Region information](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-regions) of AWS S3. Example value: ap-southeast-3. |
| Bucket | String | Yes | Cloud bucket name. |
| AccessKey | String | Yes | access_key account information of the cloud storage. To store files to Tencent COS, visit https://console.cloud.tencent.com/cam/capi to view or create the SecretId value corresponding to the key fields in the link. Example value: test-accesskey. |
| SecretKey | String | Yes | secret_key account information of cloud storage. To store files to Tencent COS, visit https://console.cloud.tencent.com/cam/capi to view or create the SecretKey value corresponding to the key fields in the link. Example value: test-secretkey. |
| FileNamePrefix | Array of String | No | Specified location of the cloud bucket, which consists of arrays of strings. Value range for the strings is lowercase letters (a-z), uppercase letters (A-Z), digits (0-9), and special characters (_-). For example, under the feature of ["prefix1", "prefix2"], the audio slicing file (xxx.mp3) is stored as prefix1/prefix2/{taskId}/{userId}/audios/{sdkappid}_{roomId}_{userid}_{UTC time}.ogg, while the video frame is stored as prefix1/prefix2/{taskId}/{userId}/images/{sdkappid}_{roomId}_{userid}_{UTC time}.png. |

## CloudSliceStorage

Information about Tencent COS and third-party cloud storage accounts.

Used by actions: CreateCloudSliceTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Vendor | Integer | Yes | Information about Tencent COS and third-party cloud storage accounts. 0: Tencent COS. 1: AWS S3. 2: Alibaba Cloud OSS. Example value: 0. |
| Region | String | Yes | [Region information](https://www.tencentcloud.com/document/product/436/6224?from_cn_redirect=1#.E5.9C.B0.E5.9F.9F) of Tencent COS. Example value: cn-shanghai-1. [Region information](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-regions) of AWS S3. Example value: ap-southeast-3. |
| Bucket | String | Yes | Cloud bucket name. |
| AccessKey | String | Yes | access_key account information of the cloud storage. To store files to Tencent COS, visit https://console.cloud.tencent.com/cam/capi to view or create the SecretId value corresponding to the key fields in the link. Example value: test-accesskey. |
| SecretKey | String | Yes | secret_key account information of the cloud storage. To store files to Tencent COS, visit https://console.cloud.tencent.com/cam/capi to view or create the SecretKey value corresponding to the key fields in the link. Example value: test-secretkey. |
| FileNamePrefix | Array of String | No | Specified location of the cloud bucket, which consists of an array of strings. Value range for the strings is lowercase letters (a-z), uppercase letters (A-Z), digits (0-9), and special characters (_-). For example, under the feature of ["prefix1", "prefix2"], the audio slicing file (xxx.mp3) is stored as prefix1/prefix2/{taskId}/{userId}/audios/{sdkappid}_{roomId}_{userid}_{UTC time}.ogg, while the video frame is stored as prefix1/prefix2/{taskId}/{userId}/images/{sdkappid}_{roomId}_{userid}_{UTC time}.png. |

## CloudStorage

The cloud storage information.

Used by actions: CreateCloudRecording, StartPublishCdnStream, StartWebRecord.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Vendor | Integer | Yes | The cloud storage provider. `0`: Tencent Cloud COS; `1`: AWS storage. Other vendors are not supported currently. |
| Region | String | Yes | [Region information](https://www.tencentcloud.comom/document/product/436/6224?from_cn_redirect=1#.E5.9C.B0.E5.9F.9F) of tencent cloud object storage. Example value: cn-shanghai-1.  [Region information](https://docs.AWS.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-regions) of AWS S3. |
| Bucket | String | Yes | The storage bucket. |
| AccessKey | String | Yes | access_key account information of the cloud storage. To store files to tencent cloud object storage (COS), visit https://console.cloud.tencent.com/cam/capi to view or create the SecretId value corresponding to the key fields in the link. |
| SecretKey | String | Yes | secret_key account information of the cloud storage. To store files to tencent cloud object storage (COS), visit https://console.cloud.tencent.com/cam/capi to view or create the SecretKey value corresponding to the key fields in the link. |
| FileNamePrefix | Array of String | No | The specified position of the cloud storage bucket consists of an array of strings. valid values: az, az, 0-9, '_', and '-'. for example, the recording file xxx.m3u8 becomes prefix1/prefix2/TaskId/xxx.m3u8 under the function of ["prefix1", "prefix2"]. |

## CloudVod

The VOD parameters.

Used by actions: CreateCloudRecording, StartWebRecord.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| TencentVod | [TencentVod](#TencentVod) | No | The Tencent Cloud VOD parameters. |

## EmulateMobileParams

Used by actions: StartWebRecord.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| MobileDeviceType | Integer | No |  |
| ScreenOrientation | Integer | No |  |

## EventList

A list of SDK or WebRTC events.

Used by actions: DescribeUserEvent.

| Name | Type | Description |
| --- | --- | --- |
| Content | Array of [EventMessage](#EventMessage) | The event information. |
| PeerId | String | The user ID of the sender. |

## EventMessage

The event information, including the timestamp and event ID.

Used by actions: DescribeUserEvent.

| Name | Type | Description |
| --- | --- | --- |
| Type | Integer | The video stream type. Valid values: `0`: A non-video event `2`: The big video `3`: The small video `7`: A relayed video |
| Time | Integer | The event reporting time in the format of UNIX timestamp (milliseconds), such as `1589891188801`. |
| EventId | Integer | The event ID. Events are classified into SDK events and WebRTC events. For more information, see https://www.tencentcloud.com/document/product/647/37906?has_map=1 |
| ParamOne | Integer | The first event parameter, such as the video width. |
| ParamTwo | Integer | The second event parameter, such as the video height. |

## InvokeLLM

Service calling actively initiates requests to the LLM.

Used by actions: ControlAIConversation.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Content | String | No | Request the content of LLM. |
| Interrupt | Boolean | No | Whether to allow the text to interrupt the robot's speaking. |

## MaxVideoUser

The information of the large video in screen sharing or floating layout mode.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserMediaStream | [UserMediaStream](#UserMediaStream) | Yes | The stream information. |

## McuAudioParams

The audio parameters for relaying.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| AudioEncode | [AudioEncode](#AudioEncode) | No | The audio encoding parameters. |
| SubscribeAudioList | Array of [McuUserInfoParams](#McuUserInfoParams) | No | The audio mix allowlist. For the `StartPublishCdnStream` API, if you do not pass this parameter or leave it empty, the audios of all anchors will be mixed. For the `UpdatePublishCdnStream` API, if you do not pass this parameter, no changes will be made to the current allowlist; if you pass in an empty string, the audios of all anchors will be mixed. In cases where `SubscribeAudioList` and `UnSubscribeAudioList` are used at the same time, you need to specify both parameters. If you pass neither `SubscribeAudioList` nor `UnSubscribeAudioList`, no changes will be made. If a user is included in both parameters, the userâs audio will not be mixed. |
| UnSubscribeAudioList | Array of [McuUserInfoParams](#McuUserInfoParams) | No | The audio mix blocklist. If you do not pass this parameter or leave it empty, there wonât be a blocklist. For the `UpdatePublishCdnStream` API, if you do not pass this parameter, no changes will be made to the current blocklist; if you pass in an empty string, the blocklist will be reset. In cases where `SubscribeAudioList` and `UnSubscribeAudioList` are used at the same time, you need to specify both parameters. If you pass neither `SubscribeAudioList` nor `UnSubscribeAudioList`, no changes will be made. If a user is included in both parameters, the userâs audio will not be mixed. |

## McuCloudVod

Used by actions: StartPublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| McuTencentVod | [McuTencentVod](#McuTencentVod) | No | Tencent VOD Parameters Example :{"ExpireTime":86400} |

## McuCustomCrop

The cropping parameters for mixed videos.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| LocationX | Integer | Yes | The horizontal offset (pixels) of the starting point for cropping. This parameter must be greater than 0. |
| LocationY | Integer | Yes | The vertical offset (pixels) of the starting point for cropping. This parameter must be greater than 0. |
| Width | Integer | Yes | The video width (pixels) after cropping. The sum of this parameter and `LocationX` cannot be greater than 10000. |
| Height | Integer | Yes | The video height (pixels) after cropping. The sum of this parameter and `LocationY` cannot be greater than 10000. |

## McuFeedBackRoomParams

Parameters for relaying to a TRTC room.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| RoomId | String | Yes | The room ID. |
| RoomIdType | Integer | Yes | The ID type of the room to which streams are relayed. `0` indicates integer, and `1` indicates string. |
| UserId | String | Yes | The [user ID](https://www.tencentcloud.com/document/product/647/37714) of the relaying robot in the TRTC room, which cannot be the same as a user ID already in use. We recommend you include the room ID in this user ID. |
| UserSig | String | Yes | The signature (similar to login password) required for the relaying robot to enter the room. For information on how to calculate the signature, see [What is UserSig?](https://www.tencentcloud.com/document/product/647/38104). |

## McuLayout

The layout parameters.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserMediaStream | [UserMediaStream](#UserMediaStream) | No | The information of the stream that is displayed. If you do not pass this parameter, TRTC will display the videos of anchors in the room according to their room entry sequence. |
| ImageWidth | Integer | No | The video width (pixels). If you do not pass this parameter, 0 will be used. |
| ImageHeight | Integer | No | The video height (pixels). If you do not pass this parameter, 0 will be used. |
| LocationX | Integer | No | The horizontal offset (pixels) of the video. The sum of `LocationX` and `ImageWidth` cannot exceed the width of the canvas. If you do not pass this parameter, 0 will be used. |
| LocationY | Integer | No | The vertical offset of the video. The sum of `LocationY` and `ImageHeight` cannot exceed the height of the canvas. If you do not pass this parameter, 0 will be used. |
| ZOrder | Integer | No | The image layer of the video. If you do not pass this parameter, 0 will be used. |
| RenderMode | Integer | No | The rendering mode of the video. 0 (the video is scaled and the excess parts are cropped), 1 (the video is scaled), 2 (the video is scaled and the blank spaces are filled with black bars). If you do not pass this parameter, 0 will be used. |
| BackGroundColor | String | No | (Not supported yet) The background color of a video. Below are the values for some commonly used colors: Red: `0xcc0033` Yellow: `0xcc9900` Green: `0xcccc33` Blue: `0x99CCFF` Black: `0x000000` White: `0xFFFFFF` Grey: `0x999999` |
| BackgroundImageUrl | String | No | The URL of the background image for the video. This parameter allows you to specify an image to display when the userâs camera is turned off or before the user enters the room. If the dimensions of the image specified are different from those of the video window, the image will be stretched to fit the space. This parameter has a higher priority than `BackGroundColor`. |
| CustomCrop | [McuCustomCrop](#McuCustomCrop) | No | Custom cropping. |
| BackgroundRenderMode | Integer | No | The display mode of the sub-background image during output: 0 for cropping, 1 for scaling and displaying the background, 2 for scaling and displaying the black background, 3 for proportional scaling. If not filled in, the default is 3. |

## McuLayoutParams

The layout parameters.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| MixLayoutMode | Integer | No | The layout mode. Valid values: 1 (floating), 2 (screen sharing), 3 (grid), 4 (custom). Floating, screen sharing, and grid are dynamic layouts. Custom layouts are static layouts. |
| PureAudioHoldPlaceMode | Integer | No | Whether to display users who publish only audio. 0: No; 1: Yes. This parameter is valid only if a dynamic layout is used. If you do not pass this parameter, 0 will be used. |
| MixLayoutList | Array of [McuLayout](#McuLayout) | No | The details of a custom layout. |
| MaxVideoUser | [MaxVideoUser](#MaxVideoUser) | No | The information of the large video in screen sharing or floating layout mode. |
| RenderMode | Integer | No | The image fill mode. This parameter is valid if the layout mode is screen sharing, floating, or grid. `0`: The image will be cropped. `1`: The image will be scaled. `2`: The image will be scaled and there may be black bars. |

## McuLayoutVolume

The SEI parameters for audio volume layout. You can specify the `AppData` and `PayloadType`.
This parameter may be empty, in which case the default SEI parameters for audio volume layout will be used.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| AppData | String | No | The application data, which will be embedded in the `app_data` field of the custom SEI. It must be shorter than 4,096 characters. |
| PayloadType | Integer | No | The payload type of the SEI message. The default is 100. Value range: 100-254 (244 is used internally by Tencent Cloud for timestamps). |
| Interval | Integer | No | The SEI sending interval (milliseconds). The default value is 1000. |
| FollowIdr | Integer | No | Valid values: `1`: SEI is guaranteed when keyframes are sent; `0` (default): SEI is not guaranteed when keyframes are sent. |

## McuPassThrough

The custom pass-through SEI.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| PayloadContent | String | Yes | The payload of the pass-through SEI. |
| PayloadType | Integer | Yes | The payload type of the SEI message. Value range: 5 and 100-254 (244 is used internally by Tencent Cloud for timestamps). |
| PayloadUuid | String | No | This parameter is required only if `PayloadType` is 5. It must be a 32-character hexadecimal string. If `PayloadType` is not 5, this parameter will be ignored. |
| Interval | Integer | No | The SEI sending interval (milliseconds). The default value is 1000. |
| FollowIdr | Integer | No | Valid values: `1`: SEI is guaranteed when keyframes are sent; `0` (default): SEI is not guaranteed when keyframes are sent. |

## McuPublishCdnParam

The relaying parameters.

Used by actions: StartPublishCdnStream, StartWebRecord, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| PublishCdnUrl | String | Yes | The URLs of the CDNs to relay to. |
| IsTencentCdn | Integer | No | Whether to relay to Tencent Cloudâs CDN. `0`: Third-party CDN; `1` (default): Tencent Cloudâs CDN. Relaying to a third-party CDN will incur fees. To avoid unexpected charges, we recommend you pass in a specific value. For details, see the API document. |

## McuRecordParams

Relay Recording Parameters

Used by actions: StartPublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UniRecord | Integer | No | Relay Recording Mode |
| RecordKey | String | No | Recording Task Key Identifies a recording task. This parameter allows merging multiple relay tasks into one recording file. If unspecified, only records the current relay task. [Format: Up to 128 bytes; only letters (a-z, A-Z), numbers (0-9), underscores (_), and hyphens (-).] Example: test_record_key_a |
| RecordWaitTime | Integer | No | [Valid only when UniRecord=3] Recording Resume Wait Time Corresponds to template parameter "Resume Wait Duration." Unit: seconds. Range: 5-86400 (24 hours). Default: 30. Recording stops if idle longer than this value. Example: 30 |
| RecordFormat | Array of String | No | [Valid only when UniRecord=3] Recording Output Formats Corresponds to template parameter "File Format." Supported values: hls, mp4, aac. Default: mp4. Note: mp4 and aac formats are mutually exclusive. Example (MP4 only): ["mp4"] Example (MP4 + HLS): ["mp4","hls"] |
| MaxMediaFileDuration | Integer | No | [Valid only when UniRecord=3] Single File Duration Corresponds to template parameter "Max File Duration." Unit: minutes. Range: 1-1440 (24 hours). Default: 1440. Applies only to mp4/aac. Actual duration is capped at 2GB file size. Example: 1440 |
| StreamType | Integer | No | [Valid only when UniRecord=3] Recording Media Type Corresponds to template parameter "Recording Format." 0: Audio+Video, 1: Audio only, 2: Video only. Output is the intersection of this setting and relay content. Example: 0 |
| UserDefineRecordPrefix | String | No | Recording Filename Prefix Filename prefix (<=64 bytes). Applies only to VOD storage. *Format: Letters (a-z, A-Z), numbers (0-9), underscores (_), hyphens (-).* Example: mcu_record_prefix |
| McuStorageParams | [McuStorageParams](#McuStorageParams) | No | [Valid only when UniRecord=3] Recording Storage Parameters Corresponds to console parameter "Storage Location." Supports Tencent VOD or COS (exclusively). Example: {"McuCloudVod":{"McuTencentVod":{"ExpireTime":86400}}} |

## McuSeiParams

The stream mixing SEI parameters.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| LayoutVolume | [McuLayoutVolume](#McuLayoutVolume) | No | The audio volume layout SEI. |
| PassThrough | [McuPassThrough](#McuPassThrough) | No | The pass-through SEI. |

## McuStorageParams

Used by actions: StartPublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| CloudStorage | [CloudStorage](#CloudStorage) | No | Third-Party Cloud Storage Account Information (Note: Storing files in Object Storage COS will incur recording file delivery fees. For details, see [Cloud Recording Billing]. Storing in VOD does not incur this fee.) Example:{"Vendor":0,"Region":"ap-shanghai","Bucket":"*","AccessKey":"*","SecretKey":"***","FileNamePrefix":["mcu_record"]} |
| McuCloudVod | [McuCloudVod](#McuCloudVod) | No | Tencent Cloud VOD Account Information Example:{"McuTencentVod":{"ExpireTime":86400}} |

## McuTencentVod

Mcu Relay Recording and Tencent VOD Parameters

Used by actions: StartPublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Procedure | String | No | Post-Upload Task Processing Automatically initiates task flows after media uploads complete. Value = Task flow template name. VOD supports creating and naming task flow templates. Example: template_name |
| ExpireTime | Integer | No | Media File Expiration Time Absolute expiration time from current timestamp. 86400 = 1 day retention 0 = permanent storage (default) Example: 86400 |
| StorageRegion | String | No | Upload Region Specification For users requiring specific upload regions. Example: ap-shanghai |
| ClassId | Integer | No | Category ID Manages media classification. Obtain via category creation API. Default: 0 (Other category) Example: 0 |
| SubAppId | Integer | No | VOD SubAppId Required when accessing sub-application resources. Leave empty otherwise. Example: 0 |
| SessionContext | String | No | Task Flow Context Passed through in task completion callbacks. Example: user_custom |
| SourceContext | String | No | Upload Context Passed through in upload completion callbacks. Example: user_custom |

## McuUserInfoParams

The users whose streams are mixed.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserInfo | [MixUserInfo](#MixUserInfo) | Yes | The user information. |

## McuVideoParams

The video parameters for relaying.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| VideoEncode | [VideoEncode](#VideoEncode) | No | The video encoding parameters. |
| LayoutParams | [McuLayoutParams](#McuLayoutParams) | No | The layout parameters. |
| BackGroundColor | String | No | The canvas color. Below are the values for some common colors: Red: 0xcc0033 Yellow: 0xcc9900 Green: 0xcccc33 Blue: 0x99CCFF Black: 0x000000 White: 0xFFFFFF Grey: 0x999999 |
| BackgroundImageUrl | String | No | The URL of the background image for the canvas. This parameter has a higher priority than `BackGroundColor`. |
| WaterMarkList | Array of [McuWaterMarkParams](#McuWaterMarkParams) | No | The watermark information for the mixed stream. |
| BackgroundRenderMode | Integer | No | Background image display mode during output: 0 for crop, 1 for scale and display with black background, 2 for proportional scaling. The backend default is proportional scaling. |

## McuWaterMarkImage

The information of the watermark image.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| WaterMarkUrl | String | Yes | The URL of the watermark image, which must be in PNG, JPG, or JPEG format and cannot exceed 5 MB. |
| WaterMarkWidth | Integer | Yes | The watermark width (pixels). |
| WaterMarkHeight | Integer | Yes | The watermark height (pixels). |
| LocationX | Integer | Yes | The horizontal offset (pixels) of the watermark. |
| LocationY | Integer | Yes | The vertical offset (pixels) of the watermark. |
| ZOrder | Integer | No | The image layer of the watermark. If you do not pass this parameter, 0 will be used. |

## McuWaterMarkParams

The Watermark information.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| WaterMarkType | Integer | No | The watermark type. Valid values: `0` (default): Image; `1`: Text. |
| WaterMarkImage | [McuWaterMarkImage](#McuWaterMarkImage) | No | The watermark image information. This parameter is required if `WaterMarkType` is 0. |
| WaterMarkText | [McuWaterMarkText](#McuWaterMarkText) | No | The text watermark configuration. This parameter is required if `WaterMarkType` is `1`. |

## McuWaterMarkText

The text watermark configuration.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Text | String | Yes | The text. |
| WaterMarkWidth | Integer | Yes | The watermark width (pixels). |
| WaterMarkHeight | Integer | Yes | The watermark height (pixels). |
| LocationX | Integer | Yes | The horizontal offset (pixels) of the watermark. |
| LocationY | Integer | Yes | The vertical offset (pixels) of the watermark. |
| FontSize | Integer | Yes | The font size. |
| FontColor | String | No | The text color. The default color is white. Values for some commonly used colors: Red: `0xcc0033`; yellow: `0xcc9900`; green: `0xcccc33`; blue: `0x99CCFF`; black: `0x000000`; white: `0xFFFFFF`; gray: `0x999999`. |
| BackGroundColor | String | No | The text fill color. If you do not specify this parameter, the fill color will be transparent. Values for some commonly used colors: Red: `0xcc0033`; yellow: `0xcc9900`; green: `0xcccc33`; blue: `0x99CCFF`; black: `0x000000`; white: `0xFFFFFF`; gray: `0x999999`. |

## MixLayout

The custom layout parameters.

Used by actions: CreateCloudRecording, ModifyCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Top | Integer | Yes | The Y axis of the windowâs top-left corner. Value range: [0, 1920]. The value cannot be larger than the canvas height. |
| Left | Integer | Yes | The X axis of the windowâs top-left corner. Value range: [0, 1920]. The value cannot be larger than the canvas width. |
| Width | Integer | Yes | The relative width of the window. Value range: [0, 1920]. The sum of the values of this parameter and `Left` cannot exceed the canvas width. |
| Height | Integer | Yes | The relative height of the window. Value range: [0, 1920]. The sum of the values of this parameter and `Top` cannot exceed the canvas height. |
| UserId | String | No | The user ID (string) of the anchor whose video is shown in the window. If you do not set this parameter, anchorsâ videos will be shown in their room entry sequence. |
| Alpha | Integer | No | The degree of transparency of the canvas. Value range: [0, 255]. 0 means fully opaque, and 255 means fully transparent. |
| RenderMode | Integer | No | 0: Stretch. In this mode, the image is stretched to fill the space available. The whole image is visible after scaling. However, if the original aspect ratio is different from the target, the image may be distorted.  1: Crop (default). In this mode, if the original aspect ratio is different from the target, the image will be cropped according to the target before being stretched to fill the space available. The image will not be distorted.  2: Blank. This mode stretches the image while keeping its original aspect ratio. If the original aspect ratio is different from the target, there may be blank spaces to the top and bottom or to the left and right of the window.  3: Smart stretch. This mode is similar to the crop mode, except that it restricts cropping to 20% of the imageâs width or height at most. |
| MediaId | Integer | No | The type of the stream subscribed to. 0: Primary stream (default) 1: Substream |
| ImageLayer | Integer | No | The image layer. 0 is the default value and means the bottommost layer. |
| SubBackgroundImage | String | No | The image url supports only jpg, png, and jpeg formats. the resolution limitation is no more than 2K, and the image size limit is no more than 5MB. note that the url must carry the format extension. the url supports only specific strings within the range of a-z, a-z, 0-9, '-', '.', '_', '~', ':', '/', '?', '#', '[', ']', '@', '!', '&', '(', ')', '*', '+', ',', '%', and '='. |

## MixLayoutParams

The layout parameters for mixed-stream recording.

Used by actions: CreateCloudRecording, ModifyCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| MixLayoutMode | Integer | Yes | Layout mode. 1: floating layout. 2: screen sharing layout. 3: nine-grid layout. 4: custom layout.  Floating layout: by default, the video footage of the first host who enters the room (or a specified host) fills the entire screen. other hosts' video images are arranged horizontally from the bottom-left corner in the room entry sequence, displayed as small pictures floating above the large screen. when the number of screens is less than or equal to 17, each line has 4 (4 x 4 arrangement). when the number of screens exceeds 17, the small pictures are rearranged with 5 per line (5 x 5 arrangement). a maximum of 25 screens are supported. if the user only sends audio, it still occupies a screen position.  Screen sharing layout: specifies a large screen position on the left side for one host (if not specified, the large screen position uses the background color). other hosts are arranged vertically on the right side from top to bottom. when the number of screens is less than 17, each column on the right supports up to 8 hosts, occupying a maximum of two columns. when the number of screens exceeds 17, hosts beyond the 17th are arranged horizontally starting from the bottom-left corner. a maximum of 25 screens is supported. if a host only sends audio, it still occupies a screen position.  Nine-Grid layout: automatically adjust the size of each frame based on the number of hosts. each host's frame size is the same, supporting up to 25 frames.  Custom layout: customize the layout of each host's video as needed in MixLayoutList. |
| MixLayoutList | Array of [MixLayout](#MixLayout) | No | The custom layout details. This parameter is valid if `MixLayoutMode` is set to `4`. Up to 25 videos can be displayed. |
| BackGroundColor | String | No | The background color, which is a hexadecimal value (starting with "#", followed by the color value) converted from an 8-bit RGB value. For example, the RGB value of orange is `R:255 G:165 B:0`, and its hexadecimal value is `#FFA500`. The default color is black. |
| MaxResolutionUserId | String | No | The user whose video is displayed in the big window. This parameter is valid if `MixLayoutMode` is set to `1` (floating) or `2` (screen sharing). If it is left empty, the first anchor entering the room is displayed in the big window in the floating mode and the canvas background is displayed in the screen sharing mode. |
| MediaId | Integer | No | The stream type. 0: Primary stream (default) 1: Substream (screen sharing stream) This parameter specifies the type of the stream displayed in the big window. If it appears in `MixLayoutList`, it indicates the type of the stream of a specified user. |
| BackgroundImageUrl | String | No | The image url supports only jpg, png, and jpeg. the image resolution is limited to no more than 2K, and the image size limit is no more than 5MB. note that the url must carry the format extension, and only specific strings are supported in the url, including a-z, a-z, 0-9, '-', '.', '_', '~', ':', '/', '?', '#', '[', ']', '@', '!', '&', '(', ')', '*', '+', ',', '%', and '='. |
| PlaceHolderMode | Integer | No | Set to 1 to enable the placeholder image function, and 0 to disable it. default is 0. when enabled, the corresponding placeholder image can be displayed in the preset position if the user has no upload audio and video. |
| BackgroundImageRenderMode | Integer | No | Handling solution when the background image aspect ratio is not the same, consistent with the RenderMode defined in MixLayoutList. |
| DefaultSubBackgroundImage | String | No | Sub-Picture placeholder image url supports only jpg, png, jpeg. resolution limitation is no more than 2K. image size limit is no more than 5MB. note that the url must carry format extension and supports only specific string literals within the range of a-z a-z 0-9 '-', '.', '_', '~', ':', '/', '?', '#', '[', ']' '@', '!', '&', '(', ')', '*', '+', ',', '%', '='. |
| WaterMarkList | Array of [WaterMark](#WaterMark) | No | The watermark layout. Up to 25 watermarks are supported. |
| RenderMode | Integer | No | When the aspect ratio of the background image does not match in the template layout, the handling solution is applied. the custom layout is disabled and aligns with the RenderMode defined in MixLayoutList. |
| MaxResolutionUserAlign | Integer | No | This parameter is valid only if the screen sharing layout is used. If you set it to `1`, the large video window will appear on the right and the small window on the left. The default value is `0`. |
| PureAudioDisableLayout | Boolean | No | Controls whether audio users inside the room occupy the stream mixing layout. this takes effect only in mixed stream recording and template layout. true: represents that audio users do not occupy placeholders. false: represents that audio users occupy placeholders (false by default). |

## MixTranscodeParams

The audio and video parameters for recording.

Used by actions: CreateCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| VideoParams | [VideoParams](#VideoParams) | No | The video transcoding parameters for recording. If you set this parameter, you must specify all its fields. If you do not set it, the default will be used. |
| AudioParams | [AudioParams](#AudioParams) | No | The audio transcoding parameters for recording. If you set this parameter, you must specify all its fields. If you do not set it, the default will be used. |

## MixUserInfo

The user information.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserId | String | Yes | User ID. |
| RoomId | String | No | If a dynamic layout is used, the value of this parameter should be the ID of the main room. If a custom layout is used, the value of this parameter should be the same as the room ID in `MixLayoutList`. |
| RoomIdType | Integer | No | The type of the `RoomId` parameter. 0: integer; 1: string. |

## ModerationParams

Control parameters for cloud moderation.

Used by actions: CreateCloudModeration.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| ModerationType | Integer | No | Moderation task type. 1: audio slicing moderation; 2: video frame extraction moderation; 3: audio slicing moderation + video frame extraction moderation; 4: audio stream moderation; 5: audio stream moderation + video frame extraction moderation. The default value is 1. (Support from suppliers is required for stream moderation to take effect.) |
| MaxIdleTime | Integer | No | Slicing is stopped automatically when there is no user (anchor) performing upstream push in the room for more than MaxIdleTime. Unit: seconds. Default value: 30 seconds. This value needs to be greater than or equal to 5 seconds and less than or equal to 1800 seconds (0.5 hours). Example value: 30. |
| SliceAudio | Integer | No | Audio slicing duration. Default value: 15s. Example value: 15. |
| SliceVideo | Integer | No | Interval for video frame extraction. Default value: 5s. |
| ModerationSupplier | String | No | Enumeration values for suppliers. tianyu: Tencent Tianyu content security. (Valid values: 1: audio slicing moderation; 2: video frame extraction moderation; 3: audio-visual slicing moderation + video frame extraction moderation.) ace: ACE content security. (Valid values: 1: audio slicing moderation; 2: video frame extraction moderation; 3: audio-visual slicing moderation + video frame extraction moderation.) shumei: shumei moderation. (Valid values: 1: audio slicing moderation; 2: video frame extraction moderation; 3: audio-visual slicing moderation + video frame extraction moderation.) Yidun: NetEase Yidun moderation. (Valid values: 1: audio slicing moderation; 2: video frame extraction moderation; 3: audio-visual slicing moderation + video frame extraction moderation.) |
| ModerationSupplierParam | [ModerationSupplierParam](#ModerationSupplierParam) | No | Configuration information required for submitting content to the third-party moderation supplier. |
| SaveModerationFile | Integer | No | Whether to save file. 0: not save by default; 1: save; 2 save the hit file. |
| CallbackAllResults | Integer | No | Whether to call back all moderation results: 0: call back all results by default; 1: only call back hit results. |
| SubscribeStreamUserIds | [SubscribeModerationUserIds](#SubscribeModerationUserIds) | No | Specifies the allowlist or blocklist for the subscription stream. |

## ModerationStorageParams

Moderation file storage parameters.

Used by actions: CreateCloudModeration.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| CloudModerationStorage | [CloudModerationStorage](#CloudModerationStorage) | No | Information about Tencent COS and third-party cloud storage accounts. |

## ModerationSupplierParam

Parameters required for submitting content to the third-party moderation supplier.

Used by actions: CreateCloudModeration.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| AppID | String | No | Moderation supplier account ID. For Tencent Tianyu, the value is not null; for NETEASE Yidun, the value is null. |
| SecretId | String | No | Moderation supplier key ID. |
| SecretKey | String | No | Moderation supplier key. |
| AudioBizType | String | No | Audio scenario. Policy ID or businessId. |
| ImageBizType | String | No | Image scenario. Policy ID or businessId. |

## QualityData

The quality data returned by ES.

Used by actions: DescribeCallDetailInfo.

| Name | Type | Description |
| --- | --- | --- |
| Content | Array of [TimeValue](#TimeValue) | The quality data. |
| UserId | String | The user ID. |
| PeerId | String | The remote user ID. An empty string indicates that the data is upstream data. Note: This field may return null, indicating that no valid values can be obtained. |
| DataType | String | The data type. |

## RecognizeConfig

Configuration used by speech recognition

Used by actions: StartAITranscription.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Language | String | No | The supported languages for speech recognition are as follows, with the default being "zh" for Chinese. The values for the `Language` field follow the [ISO639](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) standard. Here is the full list of supported languages:  1. Chinese = "zh" 2. Chinese_TW = "zh-TW" 3. Chinese_DIALECT = "zh-dialect" 4. English = "en" 5. Vietnamese = "vi" 6. Japanese = "ja" 7. Korean = "ko" 8. Indonesian = "id" 9. Thai = "th" 10. Portuguese = "pt" 11. Turkish = "tr" 12. Arabic = "ar" 13. Spanish = "es" 14. Hindi = "hi" 15. French = "fr" 16. Malay = "ms" 17. Filipino = "fil" 18. German = "de" 19. Italian = "it" 20. Russian = "ru"  **Note:** If the language you need is not listed, please contact our technical support team. |
| AlternativeLanguage | Array of String | No | Initiate fuzzy recognition to replace additional language types. Fill in up to 3 language types. Note: When Language is specified as "zh-dialect", fuzzy recognition is not supported and this field is invalid. |

## RecordParams

The on-cloud recording parameters.

Used by actions: CreateCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| RecordMode | Integer | Yes | Recording mode:. 1: single stream recording, record the audio and video of the subscribed UserId in the room separately, and upload the recording files to cloud storage. 2: mixed-stream recording. mix the audio and video of the subscribed UserId in the room into an audio-video file and upload the recording file to cloud storage. |
| MaxIdleTime | Integer | No | Recording stops automatically when there is no host inside the room for a duration exceeding MaxIdleTime. measurement unit: second. default value: 30 seconds. the value must be greater than or equal to 5 seconds and less than or equal to 86400 seconds (24 hours). |
| StreamType | Integer | No | Media stream type for recording. 0: recording audio and video streams (default). 1: record audio streams only. 2: record video stream only. |
| SubscribeStreamUserIds | [SubscribeStreamUserIds](#SubscribeStreamUserIds) | No | Specifies the allowlist or blocklist for the subscription stream. |
| OutputFormat | Integer | No | Output file format (valid when stored in third-party storage such as COS). 0: (default) output file is in hls format. 1: output file format is hls+mp4. 2: output file format is hls+aac. 3: output file format is mp4. 4: output file format is aac.  This parameter is invalid when storing in VOD. when storing in VOD, set MediaType in TencentVod (https://www.tencentcloud.comom/document/api/647/44055?from_cn_redirect=1#TencentVod). |
| AvMerge | Integer | No | In single-stream recording mode, determine whether to merge the user's audio and video. 0: do not merge the audio and video of a stream (default). 1: merge the audio and video of a stream into one ts. in mixed-stream recording, this parameter is not required, and the audio and video are merged by default. |
| MaxMediaFileDuration | Integer | No | If the file format is aac or mp4, the system will automatically split the video file when the length limit is exceeded. measurement unit: minute. defaults to 1440 min (24h). value range: 1-1440. [single file limit is 2G. if file size exceeds 2G or recording duration exceeds 24h, the file will be automatically split.]. Hls format recording. this parameter is not effective. |
| MediaId | Integer | No | Specify recording streams. 0: mainstream + auxiliary stream (default); 1: mainstream; 2: auxiliary stream. |
| FillType | Integer | No | Specifies the type of frame to fill when the upstream video stream stops: - 0: Fill with the last frame (freeze the last video frame) - 1: Fill with black frames |
| SubscribeAbility | Integer | No | Specifies whether the recording task subscribes to the stream published by the Mixed Stream Robot.   - 1: Subscribe.  - 0: Do not subscribe (default). > Note:  When this option is enabled, it is recommended to use the "Subscription Allowlist." Avoid subscribing to both the stream published by the Mixed Stream Robot and the streams published by the hosts simultaneously; otherwise, it will result in audio echoing (duplicate audio) in the recorded file. |

## RoomState

The room information.

Used by actions: DescribeRoomInfo.

| Name | Type | Description |
| --- | --- | --- |
| CommId | String | The call ID, which uniquely identifies a call. |
| RoomString | String | The room ID. |
| CreateTime | Integer | The room creation time. |
| DestroyTime | Integer | The room termination time. |
| IsFinished | Boolean | Whether the room is terminated. |
| UserId | String | The user ID of the room creator. |

## RowValues

Two-dimensional array of SeriesInfo type

Used by actions: DescribeTRTCMarketQualityData, DescribeTRTCMarketScaleData, DescribeTRTCRealTimeQualityData, DescribeTRTCRealTimeScaleData.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| RowValue | Array of Integer | No | Data value |

## STTConfig

Speech-to-text parameters

Used by actions: StartAIConversation.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Language | String | No | The supported languages for speech recognition are as follows, with the default being "zh" for Chinese. The values for the `Language` field follow the [ISO639](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) standard. Here is the full list of supported languages:  1. Chinese = "zh" 2. Chinese_TW = "zh-TW" 3. Chinese_DIALECT = "zh-dialect" 4. English = "en" 5. Vietnamese = "vi" 6. Japanese = "ja" 7. Korean = "ko" 8. Indonesian = "id" 9. Thai = "th" 10. Portuguese = "pt" 11. Turkish = "tr" 12. Arabic = "ar" 13. Spanish = "es" 14. Hindi = "hi" 15. French = "fr" 16. Malay = "ms" 17. Filipino = "fil" 18. German = "de" 19. Italian = "it" 20. Russian = "ru"  **Note:** If the language you need is not listed, please contact our technical support team. |
| AlternativeLanguage | Array of String | No | Initiate fuzzy recognition to replace additional language types. Fill in up to 3 language types. Note: When Language is specified as "zh-dialect", fuzzy recognition is not supported and this field is invalid. |
| VadSilenceTime | Integer | No | The time for speech recognition vad is in the range of 240-2000, the default value is 1000, and the unit is ms. A smaller value will make speech recognition sentence segmentation faster. |

## ScaleInfomation

The room and user number.

Used by actions: DescribeScaleInfo.

| Name | Type | Description |
| --- | --- | --- |
| Time | Integer | Start time for each day |
| UserNumber | Integer | The number of users. If a user enters a room multiple times, it will be counted as one user. Note: This field may return null, indicating that no valid values can be obtained. |
| UserCount | Integer | The number of room entries. Every time a user enters a room, it will be counted as one room entry. Note: This field may return null, indicating that no valid values can be obtained. |
| RoomNumbers | Integer | The total number of rooms of the application on a day. Note: This field may return null, indicating that no valid values can be obtained. |

## SeriesInfos

SeriesInfos type

Used by actions: DescribeTRTCMarketQualityData, DescribeTRTCMarketScaleData, DescribeTRTCRealTimeQualityData, DescribeTRTCRealTimeScaleData.

| Name | Type | Description |
| --- | --- | --- |
| Columns | Array of String | Data columns |
| Values | Array of [RowValues](#RowValues) | Data values |

## ServerPushText

The server controls the chatbot to broadcast the specified text.

Used by actions: ControlAIConversation.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Text | String | No | Server push broadcast text. |
| Interrupt | Boolean | No | Whether to allow the text to interrupt the robot's speaking. |
| StopAfterPlay | Boolean | No | Broadcast the text and automatically close the dialogue task. |
| Audio | String | No | Server push broadcast audio. Format description: audio must be mono, sampling rate must be consistent with the corresponding TTS sampling rate, and coded as a Base64 string. Input rule: when the Audio field is provided, the system will not accept user-submitted input in the Text field. the system will play the Audio content in the Audio field directly. |
| DropMode | Integer | No | Defaults to 0. valid at that time only when Interrupt is false. -0 means drop messages with Interrupt set to false during the occurrence of interaction. -1 indicates that during the occurrence of an interaction, messages with Interrupt as false will not be dropped but cached, waiting to be processed when finished.  Note: if DropMode is 1, multiple messages can be cached. if an interruption occurs subsequently, the cache of messages will be cleared. |
| Priority | Integer | No | The message priority of ServerPushText. 0 means interruptible, 1 means not interruptible. currently only support 0. if you need to input 1, submit a ticket to contact us to grant permission. Note: after receiving a message with Priority=1, any other messages will be ignored (including messages with Priority=1) until the message processing of Priority=1 is complete. this field can be used together with the Interrupt and DropMode fields. Example:. -Priority=1, Interrupt=true, interrupts existing interaction and broadcasts immediately. the broadcast will not be interrupted during the process. -Priority=1, Interrupt=false, DropMode=1. wait for the current interaction to complete before broadcasting. the broadcast will not be interrupted during the process. |
| AddHistory | Boolean | No | Whether to add the text to the llm history context. |
| MetaInfo | String | No | If filled, it will be bound to the subtitle and sent to the terminal. note that the content must be a json string. |

## SingleSubscribeParams

The information of a single stream relayed.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserMediaStream | [UserMediaStream](#UserMediaStream) | Yes | The stream information. |

## SliceParams

Control parameters for cloud slicing.

Used by actions: CreateCloudSliceTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SliceType | Integer | No | Slicing task type. 1: audio slicing; 2: video frame extraction; 3: audio/video slicing + video frame extraction. Example value: 1. |
| MaxIdleTime | Integer | No | Recording is stopped automatically when there is no anchor in the room for more than MaxIdleTime. Unit: seconds. Default value: 30 seconds. This value needs to be greater than or equal to 5 seconds and less than or equal to 86,400 seconds (24 hours). Example value: 30. |
| SliceAudio | Integer | No | Audio slicing duration. Default value: 15s. Example value: 15. |
| SliceVideo | Integer | No | Interval for video frame extraction. Default value: 5s. Example value: 5. |
| SubscribeStreamUserIds | [SubscribeStreamUserIds](#SubscribeStreamUserIds) | No | Specifies the allowlist or blocklist for the subscription stream. |
| SliceCallbackUrl | String | No | Depreciated. The callback URL is configured in the console. |

## SliceStorageParams

Storage parameters for the slicing files.

Used by actions: CreateCloudSliceTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| CloudSliceStorage | [CloudSliceStorage](#CloudSliceStorage) | No | Information about Tencent COS and third-party cloud storage accounts. |

## StorageFile

The information of the recording files, which is returned by the `DescribeCloudRecording` API.

Used by actions: DescribeCloudRecording.

| Name | Type | Description |
| --- | --- | --- |
| UserId | String | The user whose stream is recorded into the file. In the mixed-stream recording mode, this parameter will be empty. Note: This field may return `null`, indicating that no valid values can be obtained. |
| FileName | String | The filename. |
| TrackType | String | The type of the media recorded. video audio audio_video Note: This field may return `null`, indicating that no valid values can be obtained. |
| BeginTimeStamp | Integer | The start time (Unix timestamp) of the recording file. |

## StorageParams

The storage parameters.

Used by actions: CreateCloudRecording, StartWebRecord.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| CloudStorage | [CloudStorage](#CloudStorage) | No | The account information for third-party storage. Please note that if you save files to COS, a recording-to-COS fee will be incurred. For details, see the document "Billing of On-Cloud Recording". If you save files to VOD, there won't be such a fee. |
| CloudVod | [CloudVod](#CloudVod) | No | The account information for VOD storage. |

## SubscribeModerationUserIds

Specifies the subscription stream allowlist or blocklist. The audio allowlist and blocklist cannot be set simultaneously, and this also applies to video. Additionally, up to 25 concurrently subscribed media streams are supported, and up to 24 video screens are supported in mixed stream scenarios. It is also supported to use the ".*$" wildcard for prefix matching of UserId in the blocklist and allowlist. Note that if there are user IDs in the room that match the wildcard rule, specific users are subscribed, causing the prefix rule to become ineffective.

Used by actions: CreateCloudModeration, DescribeCloudModeration.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SubscribeAudioUserIds | Array of String | No | Subscription audio stream allowlist. It specifies which UserIds' audio streams to subscribe to, for example, ["1", "2", "3"] indicates subscriptions to the audio streams of UserId 1, 2, and 3; ["1.*$"] indicates subscription to audio streams with UserId prefixes starting with 1. If this parameter is left unspecified, all audio streams in the room are subscribed to by default. The number of users in the subscription list should not exceed 32. Note: This field may return null, indicating that no valid values can be obtained. |
| UnSubscribeAudioUserIds | Array of String | No | Subscription audio stream blocklist. It specifies which UserIds' audio streams not to subscribe to, for example, ["1", "2", "3"] indicates that the audio streams of UserId 1, 2, and 3 are not subscribed to; ["1.*$"] indicates that audio streams with UserId prefixes starting with 1 are not subscribed to. If this parameter is left unspecified, all audio streams in the room are subscribed to by default. The number of users in the subscription list should not exceed 32. Note: This field may return null, indicating that no valid values can be obtained. |
| SubscribeVideoUserIds | Array of String | No | Subscription video stream allowlist. It specifies which UserIds' video streams to subscribe to, for example, ["1", "2", "3"] indicates subscriptions to the video streams of UserId 1, 2, and 3; ["1.*$"] indicates subscription to video streams with UserId prefixes starting with 1. If this parameter is left unspecified, all video streams in the room are subscribed to by default. The number of users in the subscription list should not exceed 32. Note: This field may return null, indicating that no valid values can be obtained. |
| UnSubscribeVideoUserIds | Array of String | No | Subscription video stream blocklist. It specifies which UserIds' video streams not to subscribe to, for example, ["1", "2", "3"] indicates that the video streams of UserId 1, 2, and 3 are not subscribed to; ["1.*$"] indicates that video streams with UserId prefixes starting with 1 are not subscribed to. If this parameter is left unspecified, all video streams in the room are subscribed to by default. The number of users in the subscription list should not exceed 32. Note: This field may return null, indicating that no valid values can be obtained. |

## SubscribeStreamUserIds

The subscription allowlist/blocklist. You cannot specify an allowlist and a blocklist for audio/video subscription at the same time. The maximum number of streams one can receive at the same time is 25. When streams are mixed, up to 24 videos are supported. You can use `.*$` to specify user IDs with the same prefix, but make sure there arenât users whose IDs contain ".*$" and are exactly the same as the prefix you pass in. If there are, TRTC will only allow or block those users.

Used by actions: CreateCloudRecording, CreateCloudSliceTask, ModifyCloudModeration, ModifyCloudRecording, ModifyCloudSliceTask.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| SubscribeAudioUserIds | Array of String | No | The allowlist for audio subscription. For example, `["1", "2", "3"]` means to only subscribe to the audios of users 1, 2, and 3, and ["1.*$"] means to only subscribe to the audios of users whose ID prefix is `1`. If this parameter is left empty, the audios of all anchors in the room will be received. The array can contain at most 32 elements. |
| UnSubscribeAudioUserIds | Array of String | No | The blocklist for audio subscription. For example, `["1", "2", "3"]` means to not subscribe to the audios of users 1, 2, and 3, and `["1.*$"]` means to not subscribe to users whose ID prefix is `1`. If this parameter is left empty, the audios of all anchors in the room will be received. The array can contain at most 32 elements. |
| SubscribeVideoUserIds | Array of String | No | The allowlist for video subscription. For example, `["1", "2", "3"]` means to only subscribe to the videos of users 1, 2, and 3, and `["1.*$"]` means to only subscribe to the videos of users whose ID prefix is `1`. If this parameter is left empty, the videos of all anchors in the room will be received. The array can contain at most 32 elements. |
| UnSubscribeVideoUserIds | Array of String | No | The blocklist for video subscription. For example, `["1", "2", "3"]` means to not subscribe to the videos of users 1, 2, and 3, and `["1.*$"]` means to not subscribe to the videos of users whose ID prefix is `1`. If this parameter is left empty, the videos of all anchors in the room will be received. The array can contain at most 32 elements. |

## TRTCDataResult

TRTC Data Dashboard/Real-Time Monitoring API output parameters

Used by actions: DescribeTRTCMarketQualityData, DescribeTRTCMarketScaleData, DescribeTRTCRealTimeQualityData, DescribeTRTCRealTimeScaleData.

| Name | Type | Description |
| --- | --- | --- |
| StatementID | Integer | StatementID value, fixed at 0 for Monitoring Dashboard. |
| Series | Array of [SeriesInfos](#SeriesInfos) | Query result data, returned in Columns-Values format. |
| Total | Integer | Total value, fixed at 1 for Monitoring Dashboard. |

## TTSConfig

Used by actions: StartAITranscription.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| VoiceId | String | Yes |  |

## TencentVod

The Tencent Cloud VOD parameters.

Used by actions: CreateCloudRecording, StartWebRecord.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Procedure | String | No | Subsequent media task processing operations allow automatic task initiation after media upload is completed. the parameter value is the task flow template name. VOD (video on demand) supports creating task flow templates and template naming. |
| ExpireTime | Integer | No | Media file expiry time is the absolute expiration time from the current system time. to save for one day, enter "86400". to retain permanently, enter "0". the default is permanent preservation. |
| StorageRegion | String | No | Specify the upload park, applicable only to the user with special requirement for upload region. |
| ClassId | Integer | No | Category ID is used to categorize and manage media. you can create a category and obtain the category ID through the create category api. The default value is 0, indicating other categories. |
| SubAppId | Integer | No | Subapplication ID for video-on-demand (vod). if you need to access resources belonging to a subapplication, fill in this field with the subapplication ID. otherwise, this field is not required. |
| SessionContext | String | No | Task flow context, passed through when task complete. |
| SourceContext | String | No | Upload context, passed through on upload completion callback. |
| MediaType | Integer | No | The recording file format type uploaded to the vod platform. valid values: 0: mp4 (default), 1: hls, 2: aac (valid at that time when StreamType=1 for audio-only recording). 3: hls+mp4, 4: hls+aac (valid at that time when StreamType=1 is audio-only recording). |
| UserDefineRecordId | String | No | Only supports API recording upload to vod. this parameter indicates you can customize the recording file name prefix. [length limit: 64 bytes, only allows a combination of uppercase and lowercase letters (a-zA-Z), numbers (0-9), underline, and hyphen]. the prefix is separated from the automatically generated recording file name by `__UserDefine_u_`. |

## Terminology

Translation terminology

Used by actions: StartAITranscription.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Source | String | Yes | Source terminology |
| Target | String | Yes | Target terminology |

## TimeValue

The quality data, which consists of the `time` and `value` parameters.

Used by actions: DescribeCallDetailInfo.

| Name | Type | Description |
| --- | --- | --- |
| Time | Integer | The UNIX timestamp (seconds), such as `1590065877`. |
| Value | Float | The metric value. For example, if the video capturing frame rate (`bigvCapFps`) at the time `1590065877` is `0`, the value of this parameter will be `0`. |

## TranscriptionParams

AI Transcription Params

Used by actions: StartAITranscription.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserId | String | Yes | The robot's UserId is used to enter a room and initiate tasks. [Note] This UserId cannot be repeated with the host viewer [UserId](https://intl.cloud.tencent.com/document/product/647/37714) in the current room. If multiple tasks are initiated in a room, the robot's UserId cannot be repeated, otherwise the previous task will be interrupted. The robot's UserId must be unique in the room. |
| UserSig | String | Yes | The verification signature corresponding to the robot's UserId, that is, UserId and UserSig are equivalent to the robot's login password to enter the room. For the specific calculation method, please refer to the TRTC calculation [UserSig](https://cloud.tencent.com/document/product/647/45910#UserSig) solution. |
| MaxIdleTime | Integer | No | If there is no streaming in the room for more than MaxIdleTime, the background will automatically close the task. The default value is 60s. |
| TranscriptionMode | Integer | No | 1 means the robot subscribes to the stream of only one person, 0 means the robot subscribes to the stream of the entire room. If it is not filled in, the robot subscribes to the stream of the entire room by default. |
| TargetUserId | String | No | Required when TranscriptionMode is 1. The robot will only pull the stream of the userid and ignore other users in the room. |

## TranslationConfig

Translation config

Used by actions: StartAITranscription.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| TargetLanguages | Array of String | Yes | Target language, target language list (ISO 639-1). |
| Mode | Integer | No | 1: Only text translation, 2: Voice simultaneous interpretation. |
| TTSConfig | [TTSConfig](#TTSConfig) | No | Voice simultaneous interpretation configuration: When enabling simultaneous interpretation, this parameter needs to be passed. |
| Terminology | Array of [Terminology](#Terminology) | No | Translation terminology. |

## TrtcUsage

The TRTC audio/video duration generated in a certain time period.

Used by actions: DescribeMixTranscodingUsage, DescribeRecordingUsage, DescribeRelayUsage, DescribeTrtcUsage.

| Name | Type | Description |
| --- | --- | --- |
| TimeKey | String | The time point in the format of `YYYY-MM-DD HH:mm:ss`. If more than one day is queried, `HH:mm:ss` is `00:00:00`. |
| UsageValue | Array of Float | The usage (minutes). Each element of this parameter corresponds to an element of `UsageKey` in the order they are listed. |

## UserInformation

The user information, including when the user entered/left the room.

Used by actions: DescribeCallDetailInfo, DescribeUserInfo.

| Name | Type | Description |
| --- | --- | --- |
| RoomStr | String | The room ID. |
| UserId | String | The user ID. |
| JoinTs | Integer | The time when the user entered the room. |
| LeaveTs | Integer | The time when the user left the room. If the user is still in the room, the current time will be returned. |
| DeviceType | String | The device type. |
| SdkVersion | String | The SDK version number. |
| ClientIp | String | The client IP address. |
| Finished | Boolean | Whether a user has left the room. |

## UserMediaStream

The stream information.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| UserInfo | [MixUserInfo](#MixUserInfo) | No | The user information. |
| StreamType | Integer | No | The stream type. 0: Camera; 1: Screen sharing. If you do not pass this parameter, 0 will be used. |

## VideoEncode

The video encoding parameters.

Used by actions: StartPublishCdnStream, UpdatePublishCdnStream.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Width | Integer | Yes | The width of the output stream (pixels). This parameter is required if audio and video are relayed. Value range: [0, 1920]. |
| Height | Integer | Yes | The height of the output stream (pixels). This parameter is required if audio and video are relayed. Value range: [0, 1080]. |
| Fps | Integer | Yes | The frame rate (fps) of the output stream. This parameter is required if audio and video are relayed. Value range: [0, 60]. |
| BitRate | Integer | Yes | The bitrate (Kbps) of the output stream. This parameter is required if audio and video are relayed. Value range: [0, 10000]. |
| Gop | Integer | Yes | The GOP (seconds) of the output stream. This parameter is required if audio and video are relayed. Value range: [1, 5]. |

## VideoParams

The video transcoding parameters for recording.

Used by actions: CreateCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Width | Integer | Yes | The video width in pixels. The value of this parameter cannot be larger than 1920, and the result of multiplying `Width` and `Height` cannot exceed 1920 x 1080. The default value is `360`. |
| Height | Integer | Yes | The video height in pixels. The value of this parameter cannot be larger than 1920, and the result of multiplying `Width` and `Height` cannot exceed 1920 x 1080. The default value is `640`. |
| Fps | Integer | Yes | The video frame rate. Value range: [1, 60]. Default: 15. |
| BitRate | Integer | Yes | The video bitrate (bps). Value range: [64000, 8192000]. Default: 550000. |
| Gop | Integer | Yes | The keyframe interval (seconds). Default value: 10. |

## WaterMark

The watermark layout.

Used by actions: CreateCloudRecording, ModifyCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| WaterMarkType | Integer | No | The watermark type. 0 (default): image; 1: text; 2: timestamp. |
| WaterMarkImage | [WaterMarkImage](#WaterMarkImage) | No | The information of watermark images. This parameter is required if the watermark type is image. |
| WaterMarkChar | [WaterMarkChar](#WaterMarkChar) | No | The information of the text watermark. This parameter is required if `WaterMarkType` is `1`. |
| WaterMarkTimestamp | [WaterMarkTimestamp](#WaterMarkTimestamp) | No | The information of the timestamp watermark. This parameter is required if `WaterMarkType` is `2`. |

## WaterMarkChar

Used by actions: CreateCloudRecording, ModifyCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Top | Integer | Yes | The Y coordinate of the text watermark from the top left. |
| Left | Integer | Yes | The X coordinate of the text watermark from the top left. |
| Width | Integer | Yes | The watermark width (pixels). |
| Height | Integer | Yes | The watermark height (pixels). |
| Chars | String | Yes | The text. |
| FontSize | Integer | No | The font size (pixels). The default value is `14`. |
| FontColor | String | No | The text color. The default color is white. |
| BackGroundColor | String | No | The background color. If this parameter is empty, the background will be transparent (default). |

## WaterMarkImage

The information of watermark images.

Used by actions: CreateCloudRecording, ModifyCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| WaterMarkUrl | String | Yes | The download url address supports only jpg, png, and jpeg with a size limit of no more than 5M. note that the url must carry the format extension and supports only specific strings within the range of a-z, a-z, 0-9, '-', '.', '_', '~', ':', '/', '?', '#', '[', ']', '@', '!', '&', '(', ')', '*', '+', ',', '%', '='. |
| Top | Integer | Yes | The Y axis of the image's top-left corner. Value range: [0, 2560]. The value cannot be larger than the canvas height. |
| Left | Integer | Yes | The X axis of the imageâs top-left corner. Value range: [0, 2560]. The value cannot be larger than the canvas width. |
| Width | Integer | Yes | The relative width of the image. Value range: [0, 2560]. The sum of the values of this parameter and `Left` cannot exceed the canvas width. |
| Height | Integer | Yes | The relative height of the image. Value range: [0, 2560]. The sum of the values of this parameter and `Top` cannot exceed the canvas height. |

## WaterMarkTimestamp

Used by actions: CreateCloudRecording, ModifyCloudRecording.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Pos | Integer | Yes | The position of the timestamp watermark. Valid values: `0` (top left), `1` (top right), `2` (bottom left), `3` (bottom right), `4` (top center), `5` (bottom center), `6` (center). |
| TimeZone | Integer | No | The time zone. The default is UTC+8. |

## WebRecordVideoParams

Used by actions: StartWebRecord.

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| Width | Integer | No |  |
| Height | Integer | No |  |
| Format | String | No |  |
| MaxMediaFileDuration | Integer | No |  |


---
*Source: [https://trtc.io/document/36760](https://trtc.io/document/36760)*
