# Cloud Recording and Web Page Recording Webhooks

This document describes the callback events of the [updated cloud recording feature](https://www.tencentcloud.com/document/product/647/45169) and [web page recording feature](https://www.tencentcloud.com/document/product/647/72325).

## Configuration Information

On the [Tencent RTC Console](https://console.trtc.io/app), you can configure callback information. Upon configuration completion, you can receive event callback notifications.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6e9ee85c9c0f11efaaca525400fdb830.jpeg)

> **Noteï¼**You need to prepare the following information in advance and complete the [Callback Configuration](https://www.tencentcloud.com/document/product/647/39559) in the console.**Required**: the HTTP/HTTPS server address to receive callback notifications.**Optional**: [Key for signature computation](https://www.tencentcloud.com/document/product/647/54914#.E8.AE.A1.E7.AE.97.E7.AD.BE.E5.90.8D). You can customize a key of up to 32 characters, composed of uppercase and lowercase letters and numbers.

## Timeout Retry

If your server does not respond within 5 seconds after the event callback server sends the message notification, it is deemed as a failed notification. If the initial notification fails, an immediate retry is performed. If the notification fails again, retry will be performed at an interval of **10 seconds** until the message has been kept for 1 minute, after which retries will not be performed.

## Callback API

You can assign an HTTP/HTTPS service gateway for subscribing to callback messages. When any related event happens, the cloud recording system calls back the event notification to your message receiving server.

### Format of the Event Callback Message

Event callback messages are sent to your server via HTTP/HTTPS POST requests, in which:

- **Character Encoding Format**: UTF-8.
- **Request**: The body is in the JSON format.
- **Response**: HTTP STATUS CODE = 200. The server ignores the specific content of the response package. To ensure protocol friendliness, it is recommended that the customer put the following in the response content: JSON: {"code":0}.

### Cloud Recording Parameter Description

#### The Header of the Event Callback Message Contains the Following Fields:

| Field name | Value |
| --- | --- |
| Content-Type | application/json |
| Sign | Signature value |
| SdkAppId | sdk application id |

#### The Body of the Event Callback Message Includes the Following Fields:

| Field Name | Type | Description |
| --- | --- | --- |
| EventGroupId | Number | Event group ID, fixed at 3 for cloud recording |
| EventType | Number | Event type for callback notification |
| CallbackTs | Number | The Unix timestamp (in milliseconds) when the event callback server sends a callback request to your server |
| EventInfo | JSON Object | The event information |

#### Event Type Description:

| Field Name | Type | Description |
| --- | --- | --- |
| EVENT_TYPE_CLOUD_RECORDING_RECORDER_START | [301](https://www.tencentcloud.com/document/product/647/54914#301) | The cloud recording module starts. |
| EVENT_TYPE_CLOUD_RECORDING_RECORDER_STOP | [302](https://www.tencentcloud.com/document/product/647/54914#302) | The cloud recording module exits. |
| EVENT_TYPE_CLOUD_RECORDING_UPLOAD_START | [303](https://www.tencentcloud.com/document/product/647/54914#303) | The cloud recording file upload task starts, and it is called back only when COS is chosen. |
| EVENT_TYPE_CLOUD_RECORDING_FILE_INFO | [304](https://www.tencentcloud.com/document/product/647/54914#304) | Cloud recording: Generating the M3U8 index file. After the first successful generation and upload, it is called back only when COS is chosen through API recording. |
| EVENT_TYPE_CLOUD_RECORDING_UPLOAD_STOP | [305](https://www.tencentcloud.com/document/product/647/54914#305) | The cloud recording file upload is complete. It is called back only when COS is chosen. |
| EVENT_TYPE_CLOUD_RECORDING_FAILOVER | [306](https://www.tencentcloud.com/document/product/647/54914#306) | Cloud recording migration occurs. It is triggered when the existing recording task is migrated to a new load. |
| EVENT_TYPE_CLOUD_RECORDING_FILE_SLICE | [307](https://www.tencentcloud.com/document/product/647/54914#307) | Cloud recording: Generating the M3U8 index file (generating the first ts slice). After generation, it is called back only when COS is chosen through API recording. |
| EVENT_TYPE_CLOUD_RECORDING_DOWNLOAD_IMAGE_ERROR | [309](https://www.tencentcloud.com/document/product/647/54914#309) | An error occurs when the cloud recording attempts to download and decode the image file. |
| EVENT_TYPE_CLOUD_RECORDING_MP4_STOP | [310](https://www.tencentcloud.com/document/product/647/54914#310) | The MP4 recording task of cloud recording stops, and it is called back only when COS is chosen via [API recording](https://www.tencentcloud.com/document/product/647/46960) (when automatic recording is turned on in the console and the authorized VOD COS is selected as storage, please pay attention to event 311). |
| EVENT_TYPE_CLOUD_RECORDING_VOD_COMMIT | [311](https://www.tencentcloud.com/document/product/647/54914#311) | The cloud recording VOD recording task has completed the upload of media resources, and it is called back when you select **Video on Demand** and **automatically recording to COS** via the console (after file recording ends, the VOD index information is carried. Please subscribe to this type of callback event). |
| EVENT_TYPE_CLOUD_RECORDING_VOD_STOP | [312](https://www.tencentcloud.com/document/product/647/54914#312) | The cloud recording VOD task stops, and it is called back only when VOD is chosen. |

> **Noteï¼**The callback statuses from event types 301 to 309 are intermediate states of real-time recording, for you to better understand the recording process and keep track of the status. The successful upload of the actual recording file to video on demand will trigger an event 311 callback, and the overall task is completed and an event 312 is called back.

#### Event Information Description:

| Field Name | Type | Description |
| --- | --- | --- |
| RoomId | String/Number | The room name, consistent with the room ID type on the client side |
| EventTs | Number | The Unix timestamp of when the event occurred, in seconds (this field is not recommended. Instead, EventMsTs is recommended) |
| EventMsTs | Number | The Unix timestamp of when the event occurred, in milliseconds |
| UserId | String | The user ID of the recording robot |
| TaskId | String | The recording ID, which is a unique ID of a single cloud recording task |
| Payload | JsonObject | Defined based on various event types |

- **When the event type is****301** (EVENT_TYPE_CLOUD_RECORDING_RECORDER_START), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 0: Indicates that the recording module successfully starts.1: Indicates that the recording module fails to start. |

```
{    "EventGroupId": 3,    "EventType": 301,    "CallbackTs": 1622186275913,    "EventInfo": {        "RoomId": "xx",        "EventTs": "1622186275",        "EventMsTs": 1622186275757,        "UserId": "xx",        "TaskId": "xx",        "Payload": {            "Status": 0        }    }}
```

- **When the event type is****302**(EVENT_TYPE_CLOUD_RECORDING_RECORDER_STOP), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| LeaveCode | Number | 0: The invocation of recording module normally stops and exits.1: The customer kicks out the recording robot from the room.2: The customer disbands the room.3: The server kicks out the recording robot from the room.4: The server disbands the room.99: There is no other user flow in the room except for the recording robot, which will exit after a specified time.100: Exit from the room due to timeout.101: Repeated entry of the same user into the same room causes the robot to exit. |

```
{  "EventGroupId": 3,  "EventType": 302,  "CallbackTs": 1622186354806,  "EventInfo": {    "RoomId": "xx",    "EventTs": "1622186354",    "EventMsTs": 1622186275757,    "UserId": "xx",    "TaskId": "xx",    "Payload": {      "LeaveCode": 0    }  }}
```

- **When the event type is****303** (EVENT_TYPE_CLOUD_RECORDING_UPLOAD_START), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 0: Indicates that the upload module normally starts. 1: Indicates that the upload module fails to be initiated. |

- **When the event type is****304**(EVENT_TYPE_CLOUD_RECORDING_FILE_INFO), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| FileList | String | The generated M3U8 filename |

- **When the event type is****305**(EVENT_TYPE_CLOUD_RECORDING_UPLOAD_STOP), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| LeaveCode | Number | 0: Indicates that this recording upload task has been completed, and all files have been uploaded to the specified third-party cloud storage. 1: Indicates that this recording upload task has been completed, but at least one file is lingering on the server or backup storage. 2: Indicates that files lingering on the server or backup storage have been restored and uploaded to the designated third-party cloud storage.Note: 305 indicates the event that the HLS file upload is complete. |

- **When the event type is****306**(EVENT_TYPE_CLOUD_RECORDING_FAILOVER), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 0: Indicates that this migration is completed. |

```
{  "EventGroupId": 3,  "EventType": 306,  "CallbackTs": 1622191989674,  "EventInfo": {    "RoomId": "20015",    "EventTs": 1622191989,    "EventMsTs": 1622186275757,    "UserId": "xx",    "TaskId": "xx",    "Payload": {      "Status": 0    }  }}
```

- **When the event type is****307**(EVENT_TYPE_CLOUD_RECORDING_FILE_SLICE), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| FileName | String | M3U8 filename |
| UserId | String | The user ID corresponding to the recorded file |
| TrackType | String | Audio/Video types: audio/video/audio_video |
| BeginTimeStamp | String | The Unix timestamp of the server when the recording starts (in milliseconds) |

- **When the event type is****309** (EVENT_TYPE_CLOUD_RECORDING_DOWNLOAD_IMAGE_ERROR), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| Url | String | The URL of the failed download |

```
{  "EventGroupId": 3,  "EventType": 309,  "CallbackTs": 1622191989674,  "EventInfo": {    "RoomId": "20015",    "EventTs": 1622191989,    "EventMsTs": 1622186275757,    "UserId": "xx",    "TaskId": "xx",    "Payload": {      "Url": "http://xx"    }  }}
```

- **When the event type is****310** (EVENT_TYPE_CLOUD_RECORDING_MP4_STOP), the definition of Payload is as follows:

> **Noteï¼**310 is a callback event after an MP4 file is uploaded to the user-specified third-party COS. A recording task may call back multiple events of 310 (each event corresponds to a recorded file information).

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 0: Indicates that the MP4 recording task has exited normally, and all files have been uploaded to the designated third-party cloud storage.1: Indicates that this MP4 recording task has exited normally, but at least one file lingers on the server or backup storage. 2: Indicates that this MP4 recording task exits abnormally (the possible reason is the failure of extracting HLS files from COS). |
| FileList | Array | All generated MP4 file names |
| FileMessage | Array | All generated MP4 file information |
| FileName | String | MP4 file name |
| UserId | String | The user ID corresponding to the MP4 file (this field is empty when the recording mode is set to mixed streaming mode) |
| TrackType | String | audio for audio / video for pure video / audio_video for audio and video |
| MediaId | String | The primary and auxiliary stream tag. main indicates the primary stream (camera), aux indicates the auxiliary streams (screen sharing), and mix indicates mixed stream recording. |
| StartTimeStamp | Number | The Unix timestamp at the beginning of the MP4 file (in milliseconds) |
| EndTimeStamp | Number | The UNIX timestamp at the end of the MP4 file (in milliseconds) |

```
{  "EventGroupId": 3,  "EventType": 310,  "CallbackTs": 1622191965320,  "EventInfo": {    "RoomId": "20015",    "EventTs": 1622191989,    "EventMsTs": 1622186275757,    "UserId": "xx",    "TaskId": "xx",    "Payload": {      "Status": 0,      "FileList": ["xxxx1.mp4", "xxxx2.mp4"],      "FileMessage": [        {            "FileName": "xxxx1.mp4",            "UserId": "xxxx",            "TrackType": "audio_video",            "MediaId": "main",            "StartTimeStamp": 1622186279145,            "EndTimeStamp": 1622186282145        },        {            "FileName": "xxxx2.mp4",            "UserId": "xxxx",            "TrackType": "audio_video",            "MediaId": "main",            "StartTimeStamp": 1622186279153,            "EndTimeStamp": 1622186282153        }     ]    }  }}
```

- **When the event type is****311** (EVENT_TYPE_CLOUD_RECORDING_VOD_COMMIT), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 0: Indicates that the recorded file has been successfully uploaded to the VOD platform.1: Indicates that the recorded file lingers on the server or backup storage.2: Indicates that the upload and VOD task for this recorded file to is abnormal. |
| UserId | String | The user ID corresponding to this recorded file (this field is empty when the recording mode is set to mixed stream mode) |
| TrackType | String | audio for audio / video for pure video / audio_video for audio and video |
| MediaId | String | The primary and auxiliary stream tag. main indicates the primary stream (camera), aux indicates the auxiliary stream (screen sharing), and mix indicates mixed stream recording. |
| FileId | String | The unique ID of this recorded file in the VOD platform |
| VideoUrl | String | The playback address of this recorded file on the VOD platform |
| CacheFile | String | The filename corresponding to this MP4/HLS recording file |
| StartTimeStamp | Number | The Unix timestamp of the beginning of this recorded file (in milliseconds) |
| EndTimeStamp | Number | The Unix timestamp of the end of this recorded file (in milliseconds) |
| Errmsg | String | Corresponding error message when the status is not 0 |

**Callback for successful upload:**

```
{  "EventGroupId": 3,  "EventType": 311,  "CallbackTs": 1622191965320,  "EventInfo": {    "RoomId": "20015",    "EventTs": 1622191965,    "EventMsTs": 1622186275757,    "UserId": "xx",    "TaskId": "xx",    "Payload": {      "Status": 0,      "TencentVod": {        "UserId": "xx",        "TrackType": "audio_video",        "MediaId": "main",        "FileId": "xxxx",        "VideoUrl": "http://xxxx",        "CacheFile": "xxxx.mp4",        "StartTimeStamp": 1622186279153,        "EndTimeStamp": 1622186282153      }    }  }}
```

**Callback for upload failure:**

```
{  "EventGroupId": 3,  "EventType": 311,  "CallbackTs": 1622191965320,  "EventInfo": {    "RoomId": "20015",    "EventTs": 1622191965,    "EventMsTs": 1622186275757,    "UserId": "xx",    "TaskId": "xx",    "Payload": {      "Status": 1,      "Errmsg": "xxx",      "TencentVod": {        "UserId": "123",        "TrackType": "audio_video",        "CacheFile": "xxx.mp4"      }    }  }}
```

> **Noteï¼**After the callback of 311 is received, the **file upload is completed,** and you need to wait for 30 seconds to 3 minutes for the file to be completely recorded, depending on the file size.

- **When the event type is****312** (EVENT_TYPE_CLOUD_RECORDING_VOD_STOP), the definition of Payload is as follows:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 0: Indicates that this VOD upload task has exited normally.1: Indicates that this VOD upload task exits abnormally. |

```
{  "EventGroupId": 3,  "EventType": 312,  "CallbackTs": 1622191965320,  "EventInfo": {    "RoomId": "20015",    "EventTs": 1622191965,    "EventMsTs": 1622186275757,    "UserId": "xx",    "TaskId": "xx",    "Payload": {      "Status": 0    }  }}
```

### Web Page Recording Parameter Description

#### Web Page Recording Event Type

| Field Name | Type | Description |
| --- | --- | --- |
| EVENT_TYPE_WEB_RECORDER_START | [801](#801) | Page recording module start |
| EVENT_TYPE_WEB_RECORDER_STOP | [802](#802) | Page recording module exit |
| EVENT_TYPE_WEB_RECORDER_STATUS_UPDATE | [803](#803) | Page recording module recording status update |
| EVENT_TYPE_WEB_RECORDER_RESOURCE_LIMIT | [804](#804) | Page recording task resource-constrained, end recording task, callback only when recording duration or resolution exceeds limits |

#### Web Page Recording Event Information Description

| Field Name | Type | Description |
| --- | --- | --- |
| EventMsTs | Number | Unix Timestamp of Event Occurrence in milliseconds |
| TaskId | String | Recording ID, the unique ID of a web page recording task |
| Payload | JsonObject | Define different event types |
| EventMessage | String | Event information description for Status |

- **EVENT TYPE 801** (EVENT_TYPE_WEB_RECORDER_START) Payload definition:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 1: Page recording module startup successful2: Page recording module startup failed3: Recording exited abnormally during recording4: Recording task migrated5: Recording task exception, stop recording |
| EventMessage | String | Success: Page recording module startup successful, start recordingStartRecording error: Page recording module startup failedGoto url timeout: Page visit timed outException error, exit task: Recording exception terminationChrome exception, exit task: Chrome exited abnormally, recording endsRecording tasks have been migratedPage load timeout |

```
{  "EventGroupId": 8,  "EventType": 801,  "CallbackTs": 1622186275913,  "EventInfo": {    "EventMsTs": 1622186275757,    "TaskId": "-m9-bVVU7id***K-m928oZWQndiborbEWH3zY-lIXlprc-gQvQE",    "Payload": {      "Status": 1,      "EventMessage": "Success"    }  }}
```

> **Note:**When a callback with status code 801 is received, please check whether RecordUrl can be accessed normally.801 callback status codes 3 and 4 are intermediate states for web page recording, making it easy to troubleshoot recording task exceptions. Page recording automatically handles these two statuses, so customers do not need to take any action.

> **Note:**Note: When a status code 5 callback is received, the recording task will be terminated and cease further retries. Please contact business personnel for troubleshooting.

- **EVENT TYPE 802** (EVENT_TYPE_WEB_RECORDER_STOP) Payload definition:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 1: Page recording task ended properly this time |
| EventMessage | String | Success: Page recording module normally called, stop recording, log out |

```
{  "EventGroupId": 8,  "EventType": 802,  "CallbackTs": 1622186275913,  "EventInfo": {    "EventMsTs": 1622186275757,    "TaskId": "-m9-bVVU7id***K-m928oZWQndiborbEWH3zY-lIXlprc-gQvQE",    "Payload": {      "Status": 1,      "EventMessage": "Success"    }  }}
```

> **Note:**Received 802 callback indicates the web page recording task is completed. The actual recording file upload triggers callback 311. The entirety completion triggers callback 312.

- **EVENT TYPE 803** (EVENT_TYPE_WEB_RECORDER_STATUS_UPDATE) Payload definition:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 1: Page recording task page refresh2: Page recording task pause recording3: Page recording task resume recording |
| EventMessage | String | PageRefresh: Refresh recording pageRecordPaused: Recording task pausedRecordResume: Recording task resumePage load timeout |

```
{  "EventGroupId": 8,  "EventType": 803,  "CallbackTs": 1622186275913,  "EventInfo": {    "EventMsTs": 1622186275757,    "TaskId": "-m9-bVVU7id***K-m928oZWQndiborbEWH3zY-lIXlprc-gQvQE",    "Payload": {      "Status": 1,      "EventMessage": "PageRefresh"    }  }}
```

- **Event type is 804** (EVENT_TYPE_WEB_RECORDER_RESOURCE_LIMIT): Status definition:

| Field Name | Type | Description |
| --- | --- | --- |
| Status | Number | 1: Page recording task reached the maximum recording time this time, stop recording2: Video stream exceeding the maximum recording resolution appeared on the page during this recording task, stop recording |
| EventMessage | String | Recording duration reaches the set maximum recording duration and automatically ends recording.Exceeding resolution limitation: The recording task automatically ends when a video source exceeds the maximum resolution limit. |

```
{  "EventGroupId": 8,  "EventType": 804,  "CallbackTs": 1622186275913,  "EventInfo": {    "EventMsTs": 1622186275757,    "TaskId": "-m9-bVVU7id***K-m928oZWQndiborbEWH3zY-lIXlprc-gQvQE",    "Payload": {      "Status": 1,      "EventMessage": "Over time limit"    }  }}
```

> **Note:**When callback status code 804 with status 2 is received, please check whether video stream exceeding resolution limitation (1920*1080) is displayed during recording.

### Calculating a Signature

Signatures are calculated using the HMAC SHA256 encryption algorithm. After your event callback server receives the callback message, it calculates the signature in the same manner. If they match, it is an event callback from Tencent Real-Time Communication (TRTC), not a forged one. The signature calculation is as follows:

```
// In the signature Sign calculation formula, key is the encryption key used for calculating the signature Sign.Sign = base64(hmacsha256(key, body))
```

> **Noteï¼**The body is the original package body of the callback request received by you. Do not convert it. See the following example:body="{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t103,\\n\\t\\"CallbackTs\\":\\t1615554923704,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t12345,\\n\\t\\t\\"EventTs\\":\\t1608441737,\\n\\t\\t\\"UserId\\":\\t\\"test\\",\\n\\t\\t\\"UniqueId\\":\\t1615554922656,\\n\\t\\t\\"Role\\":\\t20,\\n\\t\\t\\"Reason\\":\\t1\\n\\t}\\n}"

### Signature Verification Example

Java

Python

PHP

Golang

```
import javax.crypto.Mac;import javax.crypto.spec.SecretKeySpec;import java.util.Base64;//# Function: Third-party callback sign verification//# Parameters://#   key: The key configured in the console//# Â  body: The body returned in Tencent Cloud callback//# Â  sign: Signature value of sign returned in Tencent Cloud callback//# Returned values://#   Status: OK indicates successful verification, and FAIL indicates verification failure. For specific reasons, see Info.//# Â  Info: Success/Failure messagepublic class checkSign {Â  Â  public static String secureFinalSign(String key, String entityBody) throws Exception {Â  Â  Â  Â  Mac hmacSha256 = Mac.getInstance("HmacSHA256");Â  Â  Â  Â  SecretKeySpec secret_key = new SecretKeySpec(key.getBytes(), "HmacSHA256");Â  Â  Â  Â  hmacSha256.initialize(secret_key);Â  Â  Â  Â  return Base64.getEncoder().encodeToString(hmacSha256.doFinal(body.getBytes()));Â  Â  }Â  Â  public static void main(String[] args) throws Exception {Â  Â  Â  Â  String key = "123654";Â  Â  Â  Â  String body = "{\\n" + "\\t\\"EventGroupId\\":\\t2,\\n" + "\\t\\"EventType\\":\\t204,\\n" + "\\t\\"CallbackTs\\":\\t1664209748188,\\n" + "\\t\\"EventInfo\\":\\t{\\n" + "\\t\\t\\"RoomId\\":\\t8489,\\n" + "\\t\\t\\"EventTs\\":\\t1664209748,\\n" + "\\t\\t\\"EventMsTs\\":\\t1664209748180,\\n" + "\\t\\t\\"UserId\\":\\t\\"user_85034614\\",\\n" + "\\t\\t\\"Reason\\":\\t0\\n" + "\\t}\\n" + "}";Â  Â  Â  Â  String Sign = "kkoFeO3Oh2ZHnjtg8tEAQhtXK16/KI05W3BQff8IvGA=";Â  Â  Â  Â  String resultSign = obtainResultSignature(key, body);Â  Â  Â  Â  if (resultSign.equals(Sign)) {Â  Â  Â  Â  Â  Â  System.out.println("{'Status': 'OK', 'Info': 'Verification passed'}");Â  Â  Â  Â  } else {Â  Â  Â  Â  Â  Â  System.out.println("{'Status': 'FAIL', 'Info': 'Verification failed'}");Â  Â  Â  Â  }Â  Â  }}
```

```
# -*- coding: utf8 -*-import hmacimport base64from hashlib import sha256# Function: Third-party callback sign verification# Parameters:# Â  key: The key configured in the console# Â  body: The body returned in Tencent Cloud callback# Â  Sign: The signature value sign returned in Tencent Cloud's callback# Returned values:# Status: OK indicates successful verification, and FAIL indicates verification failure. For specific reasons, see Info.# Â  Info: Success/Failure Informationdef checkSign(key, body, sign):Â  Â  temp_dict = {}Â  Â  computSign = base64.b64encode(hmac.new(key.encode('utf-8'), body.encode('utf-8'), digestmod=sha256).digest()).decode('utf-8')Â  Â  print(computSign)Â  Â  if computSign equals sign:Â  Â  Â  Â  temp_dict['Status'] = 'OK'Â  Â  Â  Â  temp_dict['Info'] = 'Verification passed'Â  Â  Â  Â  return temp_dictÂ  Â  else:Â  Â  Â  Â  temp_dict['Status'] = 'FAIL'Â  Â  Â  Â  temp_dict['Info'] = 'Verification failed'Â  Â  Â  Â  return temp_dictif __name__ == '__main__':Â  Â  key = '123654'Â  Â  body = "{\\n" + "\\t\\"EventGroupId\\":\\t2,\\n" + "\\t\\"EventType\\":\\t204,\\n" + "\\t\\"CallbackTs\\":\\t1664209748188,\\n" + "\\t\\"EventInfo\\":\\t{\\n" + "\\t\\t\\"RoomId\\":\\t8489,\\n" + "\\t\\t\\"EventTs\\":\\t1664209748,\\n" + "\\t\\t\\"EventMsTs\\":\\t1664209748180,\\n" + "\\t\\t\\"UserId\\":\\t\\"user_85034614\\",\\n" + "\\t\\t\\"Reason\\":\\t0\\n" + "\\t}\\n" + "}"Â  Â  `sign` = 'kkoFeO3Oh2ZHnjtg8tEAQhtXK16/KI05W3BQff8IvGA='Â  Â  result = verifySignature(key, body, sign)Â  Â  print(result)
```

```
<?phpclass TlsEventSig {        private $key = false;    private $body = false;        public function __construct( $key, $body ) {        $this->key = $key;		$this->body = $body;    }    private function __hmacsha256() {        $hash = hash_hmac( 'sha256', $this->body, $this->key, true );		return base64_encode( $hash);    }        public function genEventSig() {        return $this->__hmacsha256();    }}$key="789";$data="{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t101,\\n\\t\\"CallbackTs\\":\\t1608086882372,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t20222,\\n\\t\\t\\"EventTs\\":\\t1608086882,\\n\\t\\t\\"UserId\\":\\t\\"222222_phone\\"\\n\\t}\\n}";$api = new  TlsEventSig($key, $data);echo $api->genEventSig();
```

```
package mainimport "fmt"import (	"crypto/hmac"	"crypto/sha256"	"encoding/base64")func main () {    var data = "{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t101,\\n\\t\\"CallbackTs\\":\\t1608086882372,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t20222,\\n\\t\\t\\"EventTs\\":\\t1608086882,\\n\\t\\t\\"UserId\\":\\t\\"222222_phone\\"\\n\\t}\\n}"    var key = "789"    //JSRUN engine 2.0, supporting up to 30 types of languages for online running, with full simulation of online interaction for input and output.    fmt.Println(hmacsha256(data,key))}func hmacsha256(data string, key string) string {	h := hmac.New(sha256.New, []byte(key))	h.Write([]byte(data))	return base64.StdEncoding.EncodeToString(h.Sum(nil))}
```


---
*Source: [https://trtc.io/document/54914](https://trtc.io/document/54914)*
