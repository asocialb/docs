# Smart Subtitle Access Tutorial

## Overview

The smart subtitle feature supports processing offline audio files, video files, and live streams. It can extract subtitles in the source language from videos through automatic speech recognition (ASR) or optical character recognition (OCR) and implement multilingual translation. It supports LLM-based text translation of subtitle files. The feature also allows configuration of hotword and term lexicons to improve the accuracy of speech recognition and LLM-based translation.

| Smart Subtitle Feature | Description | Supported Input Type |
| --- | --- | --- |
| ASR-based subtitle generation | Enables ASR-based conversion of dialogs to subtitle files for LLM-based translation.Supports configuration of hotword and term lexicons to improve the accuracy of speech recognition and LLM-based translation.Supports embedding and rendering subtitles into video images. | Audio file, video file, live stream, and real-time audio stream |
| OCR-based subtitle generation | Enables OCR-based extraction of characters from images as subtitles for LLM-based translation. | Video file (with hard subtitles on images) |
| Subtitle file translation | Supports LLM-based translation of input subtitles into different languages and generation of new subtitles. | Subtitle file (in WebVTT or SRT format) |

#### Key features

- Comprehensive Platform Support: Offers processing capabilities for on-demand files, live streams, and RTC streams. Live broadcast real-time simultaneous captioning supports steady and gradient modes, with a low barrier to integration and no need for modifications on the playback end.
- High Accuracy: Utilizes large-scale models, and supports hotwords and glossary databases, achieving industry-leading accuracy.
- Rich Language Variety: Supports hundreds of languages, including various dialects. Capable of recognizing mixed-language speech, such as combinations of Chinese and English.
- Customizable Styles: Enables embedding open subtitles into videos, with customizable subtitle styles (font, size, color, background, position, etc.).

#### Demo

1. Access the [Experience Center](https://mps.live/demo/ai/captions) to navigate to the Intelligent Captions experience page. On the right-hand side, select either an offline video file or a live stream, specify the source language and caption type, and then click **One-Click Processing**.
2. Once the processing is complete, you can view the results.

> **Note：**The function of the MPS Demo is relatively simple, only for experiencing the basic effect, please use the API access to test the complete effect.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b143845e563011f0bf84525400454e06.png)

## Scenario 1: Processing Offline Files

### Method 1: Initiating a Zero-Code Task from the Console

#### Initiating a Task Manually

Log in to the Media Processing Service (MPS) console and click **Create Task >**[Create VOD Processing Task](https://console.tencentcloud.com/mps/tasks/create).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/73006ff9a63c11efbd5752540055f650.png)

1. **Specify an input file.**

You can choose a video file from a Tencent Cloud Object Storage (COS) bucket or provide a video download URL. The current subtitle generation and translation feature does not support using AWS S3 as an input file source.

2. **Process the input file.**

Select **Create Orchestration** and insert the "Smart Subtitle" node.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/64dace9418f811f09240525400bf7822.png)

You can choose a preset template or use custom parameters. For a detailed template configuration guide, see [Smart Subtitle Template](https://www.tencentcloud.com/document/product/1041/68175).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4057ae28cb7211f0afdc52540044a08e.png)

3. **Specify an output path.**

Specify the storage path of the output file.

4. **Initiate a task.**

Click **Create** to initiate a task.

#### Automatically Triggering a Task Through the Orchestration (Optional)

If you want to upload a video file to the COS bucket and achieve automatic smart subtitles according to preset parameters, you can:

1. Enter **On-demand Orchestration** in the menu, click **Create VDD Orchestration**, select the smart subtitle node in task configuration, and configure parameters such as the bucket and directory to be triggered.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b0d03373cc3911f08658525400454e06.png)

2. Go to the **On-demand Orchestration** list, find the new orchestration, and enable the switch at **Enable**. Subsequently, any new video files added to the triggered directory will automatically initiate tasks according to the preset process and parameters of the orchestration, and the processed video files will be saved to the output path configured in the orchestration.

> **Note:**It takes 3-5 minutes for the orchestration to take effect after being enabled.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1915ec3818f911f0b5c65254001c06ec.png)

### Method 2: API Call

#### **Method 1**

Call the [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) API and initiate a task by specifying the **Template ID**. Example:

```
{    "InputInfo": {        "Type": "URL",        "UrlInputInfo": {            "Url": "https://test-1234567.cos.ap-guangzhou.myqcloud.com/video/test.mp4" // Replace it with the video URL to be processed.        }    },    "SmartSubtitlesTask": {        "Definition": 122 //122 is the ID of the preset Chinese source video—generate Chinese and English subtitles template, which can be replaced with the ID of a custom smart subtitle template.    },    "OutputStorage": {        "CosOutputStorage": {            "Bucket": "test-1234567",            "Region": "ap-guangzhou"        },        "Type": "COS"    },    "OutputDir": "/output/",    "Action": "ProcessMedia",    "Version": "2019-06-12"}
```

#### **Method 2**

Call the [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) API and initiate a task by specifying the **Orchestration ID**. Example:

```
{    "InputInfo": {        "Type": "COS",         "CosInputInfo": {            "Bucket": "facedetectioncos-125*****11",             "Region": "ap-guangzhou",             "Object": "/video/123.mp4"        }    },     "ScheduleId": 12345, //Replace it with a custom orchestration ID. 12345 is a sample code and has no practical significance.    "Action": "ProcessMedia",     "Version": "2019-06-12"}
```

> **Note:**If there is a callback address set, see the [ParseNotification](https://www.tencentcloud.com/document/product/1041/33679) document for response packets.

### Subtitle Application to Videos (Optional Capability)

Call the [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640) API, initiate a **transcoding task**, specify the vtt file path for the subtitle, and specify subtitle application styles through the [SubtitleTemplate](https://www.tencentcloud.com/document/product/1041/33690#subtitletemplate) field.

Example:

```
{    "MediaProcessTask": {        "TranscodeTaskSet": [            {                "Definition": 100040, //Transcoding template ID. It should be replaced with the transcoding template you need.                "OverrideParameter": { //Overwriting parameters that are used for flexibly overwriting some parameters in the transcoding template.                    "SubtitleTemplate": { //Subtitle application configuration.                        "Path": "https://test-1234567.cos.ap-nanjing.myqcloud.com/mps_autotest/subtitle/1.vtt",                         "StreamIndex": 2,                         "FontType": "simkai.ttf",                         "FontSize": "10px",                         "FontColor": "0xFFFFFF",                         "FontAlpha": 0.9                    }                }            }        ]    },     "InputInfo": { //Input information.        "Type": "URL",         "UrlInputInfo": {            "Url": "https://test-1234567.cos.ap-nanjing.myqcloud.com/mps_autotest/subtitle/123.mkv"        }    },     "OutputStorage": { //Output bucket.        "Type": "COS",         "CosOutputStorage": {            "Bucket": "test-1234567",             "Region": "ap-nanjing"        }    },     "OutputDir": "/mps_autotest/output2/", //Output path.    "Action": "ProcessMedia",     "Version": "2019-06-12"}
```

### Querying Task Results

#### Via the Console

1. Navigate to the [Offline Task Management](https://console.tencentcloud.com/mps/tasks/vod-list) in the console, where the list will display the tasks that have just been initiated.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4782ad07cc3a11f08e74525400bf7822.png)

2. When the subtask status is "Successful", clicking on **View Result** allows for a preview of the subtitle.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5c1ceb7ecc3a11f0afdc52540044a08e.png)

3. The generated VTT subtitle file can be found in **Orchestration > COS Bucket > Output Bucket**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2dde588719ca11f0b5c65254001c06ec.png)

Sample Chinese-English subtitles:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2dea220f19ca11f091eb525400454e06.png)

#### Event Notification Callbacks

When initiating a media processing task with [ProcessMedia](https://www.tencentcloud.com/document/product/1041/33640), you can configure event callbacks through the `TaskNotifyConfig` parameter. Upon the completion of the task, the results will be communicated back to you via the configured callback information, which you can decipher using [ParseNotification](https://www.tencentcloud.com/document/product/1041/33679).

#### Querying Task Results by Calling an API

Call the [DescribeTaskDetail](https://www.tencentcloud.com/document/product/1041/33640) API and fill in the task ID (for example, 24000022-WorkflowTask-b20a8exxxxxxx1tt110253 or 24000022-ScheduleTask-774f101xxxxxxx1tt110253) to query task results. Example:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/aa2482efb92b11f0a6c652540044a08e.png)

## Scenario 2: Live Streams

There are currently 2 solutions for using subtitles and translations in live streams: Enable the subtitle feature through the Cloud Streaming Services (CSS) console, or use MPS to call back text and embed it into live streams. It is recommended to enable the subtitle feature through the CSS console. The solution is introduced as follows:

### Method 1: Enabling the Subtitle Feature in the CSS Console

1. **Configure the live subtitling feature.**
  1.1. Enable [CSS](https://console.tencentcloud.com/live/livestat) and [MPS](https://console.tencentcloud.com/mps/index).
  1.2. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat), [create a subtitle template](https://console.tencentcloud.com/live/config/subtitle), and bind the transcoding template.
2. **Obtain subtitle streams.**

When the transcoding stream (append the transcoding template name `_transcoding template name` bound with the subtitle template to the corresponding live stream's StreamName to generate a transcoding stream address) is obtained, subtitles will be displayed. For detailed rules of splicing addresses for obtaining streams, see [Splicing Playback URLs](https://www.tencentcloud.com/document/product/267/38393?lang=en&pg=#splicing-push-urls).

> **Note:**Currently, there are 2 forms of subtitle display: real-time dynamic subtitles and delayed steady-state subtitles. For real-time dynamic subtitles, the subtitles in live broadcast will dynamically correct the content word by word based on the speech content, and the output subtitles change in real time. For delayed steady-state subtitles, the system will display the live broadcast with a delay according to the set time, but the viewing experience of the complete sentence subtitle mode is better.

### Method 2: Calling Back Text through MPS

Currently, it is not supported to use the MPS console to initiate live stream smart subtitle tasks. You can initiate them through the API.

Below are usage examples. For detailed API documentation, see [ProcessLiveStream](https://www.tencentcloud.com/document/product/1041/33641). For the real-time callback package, see [ParseLiveStreamProcessNotification](https://www.tencentcloud.com/document/product/1041/33680).

> **Note:**Currently, using MPS to process live streams requires the use of the **Intelligent Identification** template. This is achieved using Automatic Speech Recognition or speech translation.

```
{    "Url": "http://5000-wenzhen.liveplay.myqcloud.com/live/123.flv",     "AiRecognitionTask": {        "Definition": 10101 //10101 is the preset Chinese subtitle template ID, which can be replaced with the ID of a custom intelligent identification template.    },     "OutputStorage": {        "CosOutputStorage": {            "Bucket": "6c0f30dfvodgzp*****0800-10****53",             "Region": "ap-guangzhou"        },         "Type": "COS"    },     "OutputDir": "/6c0f30dfvodgzp*****0800/0d1409d3456551**********652/",     "TaskNotifyConfig": {        "NotifyType": "URL",         "NotifyUrl": "http://****.qq.com/callback/qtatest/?token=*****"    },     "Action": "ProcessLiveStream",     "Version": "2019-06-12"}
```

## Scenario 3: Processing Private Audio Streams via WebSocket

In scenarios such as video conferencing and duplex voice, audios can be transmitted to the recognition and translation services via WebSocket, and the results can be returned over the same protocol. Recognition, recognition and translation, and simultaneous recognition and translation of multiple real-time audio streams are supported. Real-time subtitles can be output in the steady-state or gradient mode. For details about the protocol, see [WebSocket Protocol for Recognition](https://www.tencentcloud.com/document/product/1041/72106).

Sample code:

```
#!/usr/bin/env python3# -*- coding: utf-8 -*-import argparseimport structimport timeimport osimport signalimport sysimport hashlibimport hmacimport randomfrom urllib.parse import urlencode, urlunsplit, quoteimport websocketsimport asyncioimport loggingimport json# Setup logginglogging.basicConfig(level=logging.INFO)logger = logging.getLogger(__name__)class AudioPacket:    def __init__(self, format=1, is_end=False, timestamp=0, audio_src_id="123456", ext_data=b'', data=b''):        self.format = format        self.is_end = is_end        self.timestamp = timestamp        self.audio_src_id = audio_src_id        self.ext_data = ext_data        self.data = data    def marshal(self):        """Serialize audio packet to binary format"""        header = struct.pack(            '>BBQH',             self.format,             1 if self.is_end else 0,            self.timestamp,            len(self.audio_src_id)        )        audio_src_bytes = self.audio_src_id.encode('utf-8')        ext_len = struct.pack('>H', len(self.ext_data))        return header + audio_src_bytes + ext_len + self.ext_data + self.datadef sha256hex(s):    """Calculate SHA256 hex digest"""    if isinstance(s, str):        s = s.encode('utf-8')    return hashlib.sha256(s).hexdigest()def hmacsha256(s, key):    """Calculate HMAC-SHA256"""    if isinstance(s, str):        s = s.encode('utf-8')    if isinstance(key, str):        key = key.encode('utf-8')    return hmac.new(key, s, hashlib.sha256).digest()def generate_random_number(digits):    """Generate random number with specified digits"""    low = 10 ** (digits - 1)    high = (10 ** digits) - 1    return random.randint(low, high)def generate_url_v3(args):    """Generate WebSocket URL with TC3-HMAC-SHA256 signature"""    query_params = {}    if args.dstLang:        query_params["transSrc"] = args.lang        query_params["transDst"] = args.dstLang    else:        query_params["asrDst"] = args.lang        query_params["fragmentNotify"] = "1" if args.frame else "0"    query_params["timeoutSec"] = str(args.timeout)        timestamp = int(time.time())    expire_timestamp = timestamp + 3600        query_params["timeStamp"] = str(timestamp)    query_params["expired"] = str(expire_timestamp)    query_params["secretId"] = args.secretId    query_params["nonce"] = str(generate_random_number(10))        # Sort keys and build canonical query string    sorted_keys = sorted(query_params.keys())    canonical_query = "&".join(        ["{}={}".format(k, quote(query_params[k], safe=''))          for k in sorted_keys]    )        # Build canonical request    path = "/wss/v1/{}".format(args.appid)    http_method = "post"    canonical_uri = path    canonical_headers = "content-type:application/json; charset=utf-8\\nhost:{}\\n".format(args.addr)    signed_headers = "content-type;host"        canonical_request = "{}\\n{}\\n{}\\n{}\\n{}\\n".format(        http_method,        canonical_uri,        canonical_query,        canonical_headers,        signed_headers,    )        # Build string to sign    date = time.strftime("%Y-%m-%d", time.gmtime(timestamp))    credential_scope = "{}/mps/tc3_request".format(date)    hashed_canonical = sha256hex(canonical_request)        algorithm = "TC3-HMAC-SHA256"    string_to_sign = "{}\\n{}\\n{}\\n{}".format(        algorithm,        timestamp,        credential_scope,        hashed_canonical    )        # Calculate signature    secret_date = hmacsha256(date, "TC3" + args.secretKey)    secret_service = hmacsha256("mps", secret_date)    secret_signing = hmacsha256("tc3_request", secret_service)    signature = hmac.new(        secret_signing,         string_to_sign.encode('utf-8'),         hashlib.sha256    ).hexdigest()        # Add signature to query params    query_params["signature"] = signature        # Build final URL    scheme = "wss" if args.ssl else "ws"    url = urlunsplit((        scheme,        args.addr,        path,        urlencode(query_params),        ""    ))    return urlasync def receive_messages(websocket, stop_event):    """Handle incoming WebSocket messages"""    try:        while not stop_event.is_set():            message = await websocket.recv()            if isinstance(message, bytes):                try:                    message = message.decode('utf-8')                except UnicodeDecodeError:                    message = str(message)            logger.info("Received: %s", message)    except Exception as e:        logger.info("Connection closed: %s", e)async def run_client():    parser = argparse.ArgumentParser()    parser.add_argument("--addr", default="mps.cloud.tencent.com", help="websocket service address")    parser.add_argument("--file", default="./wx_voice.pcm", help="pcm file path")    parser.add_argument("--appid", default="121313131", help="app id")    parser.add_argument("--lang", default="zh", help="language")    parser.add_argument("--dstLang", default="", help="destination language")    parser.add_argument("--frame", action="store_true", help="enable frame notify")    parser.add_argument("--secretId", default="123456", help="secret id")    parser.add_argument("--secretKey", default="123456", help="secret key")    parser.add_argument("--ssl", action="store_true", help="use SSL")    parser.add_argument("--timeout", type=int, default=10, help="timeout seconds")    parser.add_argument("--wait", type=int, default=700, help="wait seconds after end")    args = parser.parse_args()    url = generate_url_v3(args)    logger.info("Connecting to %s", url)    try:        # Python 3.6 compatible websockets connection        websocket = await websockets.connect(url, ping_timeout=5)        # Handle initial response        initial_msg = await websocket.recv()        try:            result = json.loads(initial_msg)            if result.get("Code", 0) != 0:                logger.error("Handshake failed: %s", result.get("Message", ""))                return            logger.info("TaskId %s handshake success", result.get("TaskId", ""))        except ValueError:  # json.JSONDecodeError not available in 3.6            logger.error("Invalid initial message")            return        # Setup signal handler        loop = asyncio.get_event_loop()        stop_event = asyncio.Event()        loop.add_signal_handler(signal.SIGINT, stop_event.set)        # Start receiver        receiver_task = asyncio.ensure_future(receive_messages(websocket, stop_event))        # Audio processing        try:            with open(args.file, "rb") as fd:                PCM_DUR_MS = 40                pcm = bytearray(PCM_DUR_MS * 32)                pkt = AudioPacket(data=pcm)                is_end = False                wait_until = 0                while not stop_event.is_set():                    if is_end:                        if time.time() > wait_until:                            logger.info("Finish")                            break                        await asyncio.sleep(0.1)                        continue                    # Read PCM data                    n = fd.readinto(pkt.data)                    if n < len(pkt.data):                        pkt.is_end = True                        is_end = True                        wait_until = time.time() + args.wait                    # Send audio packet                    await websocket.send(pkt.marshal())                    logger.info("Sent ts %d", pkt.timestamp)                    pkt.timestamp += n // 32                    await asyncio.sleep(PCM_DUR_MS / 1000)        except IOError:  # FileNotFoundError not available in 3.6            logger.error("Open file error: %s", args.file)            return        # Cleanup        await asyncio.wait_for(receiver_task, timeout=1)        await websocket.close()    except Exception as e:        logger.error("Connection error: %s", e)        returnif __name__ == "__main__":    # Python 3.6 compatible asyncio runner    loop = asyncio.get_event_loop()    try:        loop.run_until_complete(run_client())    finally:        loop.close()
```

## FAQs

### What Languages Are Supported by Smart Subtitle

##### Source and Target Languages Supported by the Processing Type of ASR-based Subtitle Generation

Source Language

| No. | Language (Source Language) | Code |
| --- | --- | --- |
| 1 | Afrikaans (South Africa) | af-ZA |
| 2 | Albanian (Albania) | sq-AL |
| 3 | Amharic (Ethiopia) | am-ET |
| 4 | Arabic (Algeria) | ar-DZ |
| 5 | Arabic (Bahrain) | ar-BH |
| 6 | Arabic (Egypt) | ar-EG |
| 7 | Arabic (Iraq) | ar-IQ |
| 8 | Arabic (Israel) | ar-IL |
| 9 | Arabic (Jordan) | ar-JO |
| 10 | Arabic (Kuwait) | ar-KW |
| 11 | Arabic (Lebanon) | ar-LB |
| 12 | Arabic (Mauritania) | ar-MR |
| 13 | Arabic (Morocco) | ar-MA |
| 14 | Arabic (Oman) | ar-OM |
| 15 | Arabic (Qatar) | ar-QA |
| 16 | Arabic (Saudi Arabia) | ar-SA |
| 17 | Arabic (State of Palestine) | ar-PS |
| 18 | Arabic (Syria) | ar-SY |
| 19 | Arabic (Tunisia) | ar-TN |
| 20 | Arabic (United Arab Emirates) | ar-AE |
| 21 | Arabic (Yemen) | ar-YE |
| 22 | Armenian (Armenia) | hy-AM |
| 23 | Azerbaijani (Azerbaijan) | az-AZ |
| 24 | Basque (Spain) | eu-ES |
| 25 | Bengali (Bangladesh) | bn-BD |
| 26 | Bengali (India) | bn-IN |
| 27 | Bosnian (Bosnia and Herzegovina) | bs-BA |
| 28 | Bulgarian (Bulgaria) | bg-BG |
| 29 | Burmese (Myanmar) | my-MM |
| 30 | Catalan (Spain) | ca-ES |
| 31 | Simplified Chinese (China) | zh-CN |
| 32 | Traditional Chinese (Taiwan (China)) | zh-TW |
| 33 | Cantonese (Hong Kong (China) Traditional Chinese) | yue |
| 34 | Croatian (Croatia) | hr-HR |
| 35 | Czech (Czech Republic) | cs-CZ |
| 36 | Danish (Denmark) | da-DK |
| 37 | Dutch (Belgium) | nl-BE |
| 38 | Dutch (Netherlands) | nl-NL |
| 39 | English (Australia) | en-AU |
| 40 | English (Canada) | en-CA |
| 41 | English (Ghana) | en-GH |
| 42 | English (Hong Kong (China)) | en-HK |
| 43 | English (India) | en-IN |
| 44 | English (Ireland) | en-IE |
| 45 | English (Kenya) | en-KE |
| 46 | English (New Zealand) | en-NZ |
| 47 | English (Nigeria) | en-NG |
| 48 | English (Pakistan) | en-PK |
| 49 | English (Philippines) | en-PH |
| 50 | English (Singapore) | en-SG |
| 51 | English (South Africa) | en-ZA |
| 52 | English (Tanzania) | en-TZ |
| 53 | English (UK) | en-GB |
| 54 | English (US) | en-US |
| 55 | Estonian (Estonia) | et-EE |
| 56 | Filipino (Philippines) | fil-PH |
| 57 | Finnish (Finland) | fi-FI |
| 58 | French (Belgium) | fr-BE |
| 59 | French (Canada) | fr-CA |
| 60 | French (France) | fr-FR |
| 61 | French (Switzerland) | fr-CH |
| 62 | Galician (Spain) | gl-ES |
| 63 | Georgian (Georgia) | ka-GE |
| 64 | German (Austria) | de-AT |
| 65 | German (Germany) | de-DE |
| 66 | German (Switzerland) | de-CH |
| 67 | Greek (Greece) | el-GR |
| 68 | Gujarati (India) | gu-IN |
| 69 | Hebrew (Israel) | iw-IL |
| 70 | Hindi (India) | hi-IN |
| 71 | Hungarian (Hungary) | hu-HU |
| 72 | Icelandic (Iceland) | is-IS |
| 73 | Indonesian (Indonesia) | id-ID |
| 74 | Italian (Italy) | it-IT |
| 75 | Italian (Switzerland) | it-CH |
| 76 | Japanese (Japan) | ja-JP |
| 77 | Javanese (Indonesia) | jv-ID |
| 78 | Kannada (India) | kn-IN |
| 79 | Kazakh (Kazakhstan) | kk-KZ |
| 80 | Khmer (Cambodia) | km-KH |
| 81 | Kinyarwanda (Rwanda) | rw-RW |
| 82 | Korean (South Korea) | ko-KR |
| 83 | Lao (Laos) | lo-LA |
| 84 | Latvian (Latvia) | lv-LV |
| 85 | Lithuanian (Lithuania) | lt-LT |
| 86 | Macedonian (North Macedonia) | mk-MK |
| 87 | Malay (Malaysia) | ms-MY |
| 88 | Malayalam (India) | ml-IN |
| 89 | Marathi (India) | mr-IN |
| 90 | Mongolian (Mongolia) | mn-MN |
| 91 | Nepali (Nepal) | ne-NP |
| 92 | Bokmål Norwegian (Norway) | no-NO |
| 93 | Persian (Iran) | fa-IR |
| 94 | Polish (Poland) | pl-PL |
| 95 | Portuguese (Brazil) | pt-BR |
| 96 | Portuguese (Portugal) | pt-PT |
| 97 | Punjabi (Gurmukhi, India) | pa-Guru-IN |
| 98 | Romanian (Romania) | ro-RO |
| 99 | Russian (Russia) | ru-RU |
| 100 | Serbian (Serbia) | sr-RS |
| 101 | Sinhalese (Sri Lanka) | si-LK |
| 102 | Slovak (Slovakia) | sk-SK |
| 103 | Slovene (Slovenia) | sl-SI |
| 104 | Sesotho (South Africa) | st-ZA |
| 105 | Spanish (Argentina) | es-AR |
| 106 | Spanish (Bolivia) | es-BO |
| 107 | Spanish (Chile) | es-CL |
| 108 | Spanish (Colombia) | es-CO |
| 109 | Spanish (Costa Rica) | es-CR |
| 110 | Spanish (Dominican Republic) | es-DO |
| 111 | Spanish (Ecuador) | es-EC |
| 112 | Spanish (El Salvador) | es-SV |
| 113 | Spanish (Guatemala) | es-GT |
| 114 | Spanish (Honduras) | es-HN |
| 115 | Spanish (Mexico) | es-MX |
| 116 | Spanish (Nicaragua) | es-NI |
| 117 | Spanish (Panama) | es-PA |
| 118 | Spanish (Paraguay) | es-PY |
| 119 | Spanish (Peru) | es-PE |
| 120 | Spanish (Puerto Rico) | es-PR |
| 121 | Spanish (Spain) | es-ES |
| 122 | Spanish (US) | es-US |
| 123 | Spanish (Uruguay) | es-UY |
| 124 | Spanish (Venezuela) | es-VE |
| 125 | Sundanese (Indonesia) | su-ID |
| 126 | Swahili (Kenya) | sw-KE |
| 127 | Swahili (Tanzania) | sw-TZ |
| 128 | Swazi (Latin script, South Africa) | ss-Latn-ZA |
| 129 | Swedish (Sweden) | sv-SE |
| 130 | Tamil (India) | ta-IN |
| 131 | Tamil (Malaysia) | ta-MY |
| 132 | Tamil (Singapore) | ta-SG |
| 133 | Tamil (Sri Lanka) | ta-LK |
| 134 | Telugu (India) | te-IN |
| 135 | Thai (Thailand) | th-TH |
| 136 | Tsonga (South Africa) | ts-ZA |
| 137 | Tswana (Latin script, South Africa) | tn-Latn-ZA |
| 138 | Turkish (Türkiye) | tr-TR |
| 139 | Ukrainian (Ukraine) | uk-UA |
| 140 | Urdu (India) | ur-IN |
| 141 | Urdu (Pakistan) | ur-PK |
| 142 | Uzbek (Uzbekistan) | uz-UZ |
| 143 | Venda (South Africa) | ve-ZA |
| 144 | Vietnamese (Vietnam) | vi-VN |
| 145 | Xhosa (South Africa) | xh-ZA |
| 146 | Zulu (South Africa) | zu-ZA |

Target Languages for Translation

| No. | Language (Target Language) | Code |
| --- | --- | --- |
| 1 | Abkhaz language | ab |
| 2 | Acehnese | ace |
| 3 | Acholi | ach |
| 4 | Afrikaans | af |
| 5 | Albanian | sq |
| 6 | Alur | alz |
| 7 | Amharic | am |
| 8 | Arabic | ar |
| 9 | Armenian | hy |
| 10 | Assamese | as |
| 11 | Awadhi | awa |
| 12 | Aymara | ay |
| 13 | Azerbaijani | az |
| 14 | Balinese | ban |
| 15 | Bambara | bm |
| 16 | Bashkir | ba |
| 17 | Basque | eu |
| 18 | Batak Karo | btx |
| 19 | Batak Simalungun | bts |
| 20 | Batak Toba | bbc |
| 21 | Belarusian | be |
| 22 | Bemba | bem |
| 23 | Bengali | bn |
| 24 | Betawi | bew |
| 25 | Bhojpuri | bho |
| 26 | Bikol | bik |
| 27 | Bosnian | bs |
| 28 | Breton | br |
| 29 | Bulgarian | bg |
| 30 | Buryat | bua |
| 31 | Cantonese | yue |
| 32 | Catalan | ca |
| 33 | Cebuano | ceb |
| 34 | Chichewa (Nyanja) | ny |
| 35 | Simplified Chinese | zh-CN or zh |
| 36 | Chinese (Traditional) | zh-TW |
| 37 | Chuvash | cv |
| 38 | Corsican | co |
| 39 | Crimean Tatar | crh |
| 40 | Croatian | hr |
| 41 | Czech | cs |
| 42 | Danish | da |
| 43 | Dinka | din |
| 44 | Divehi | dv |
| 45 | Dogri | doi |
| 46 | Dombe | dov |
| 47 | Dutch | nl |
| 48 | Dzongkha | dz |
| 49 | English | en |
| 50 | Esperanto | eo |
| 51 | Estonian | et |
| 52 | Ewe | ee |
| 53 | Fijian | fj |
| 54 | Filipino (Tagalog) | fil or tl |
| 55 | Finnish | fi |
| 56 | French | fr |
| 57 | French (France) | fr-FR |
| 58 | French (Canada) | fr-CA |
| 59 | Frisian | fy |
| 60 | Fula | ff |
| 61 | Ga | gaa |
| 62 | Galician | gl |
| 63 | Ganda (Luganda) | lg |
| 64 | Georgian | ka |
| 65 | German | de |
| 66 | Greek | el |
| 67 | Guarani | gn |
| 68 | Gujarati | gu |
| 69 | Haitian Creole | ht |
| 70 | Hakha Chin | cnh |
| 71 | Hausa | ha |
| 72 | Hawaiian | haw |
| 73 | Hebrew | iw or he |
| 74 | Hiligaynon | hil |
| 75 | Hindi | hi |
| 76 | Hmong | hmn |
| 77 | Hungarian | hu |
| 78 | Hunsrik | hrx |
| 79 | Icelandic | is |
| 80 | Igbo | ig |
| 81 | Iloko | ilo |
| 82 | Indonesian | id |
| 83 | Irish | ga |
| 84 | Italian | it |
| 85 | Japanese | ja |
| 86 | Javanese | jw or jv |
| 87 | Kannada | kn |
| 88 | Kapampangan | pam |
| 89 | Kazakh | kk |
| 90 | Khmer | km |
| 91 | Kiga | cgg |
| 92 | Kinyarwanda | rw |
| 93 | Kituba | ktu |
| 94 | Goan Konkani | gom |
| 95 | Korean | ko |
| 96 | Krio | kri |
| 97 | Kurdish (Kurmanji) | ku |
| 98 | Kurdish (Sorani) | ckb |
| 99 | Kirghiz | ky |
| 100 | Lao | lo |
| 101 | Latgalian | ltg |
| 102 | Latin | la |
| 103 | Latvian | lv |
| 104 | Ligurian | lij |
| 105 | Limburgish | li |
| 106 | Lingala | ln |
| 107 | Lithuanian | lt |
| 108 | Lombard | lmo |
| 109 | Luo | luo |
| 110 | Luxembourgish | lb |
| 111 | Macedonian | mk |
| 112 | Maithili | mai |
| 113 | Makassar | mak |
| 114 | Malagasy | mg |
| 115 | Malay | ms |
| 116 | Malay (Jawi script) | ms-Arab |
| 117 | Malayalam | ml |
| 118 | Maltese | mt |
| 119 | Maori | mi |
| 120 | Marathi | mr |
| 121 | Meadow Mari language | chm |
| 122 | Meitei (Manipuri) | mni-Mtei |
| 123 | Minangkabau | min |
| 124 | Mizo | lus |
| 125 | Mongolian | mn |
| 126 | Burmese | my |
| 127 | Ndebele (southern) | nr |
| 128 | Nepali (Newar) | new |
| 129 | Nepali | ne |
| 130 | Northern Sotho (Sepedi) | nso |
| 131 | Norwegian | no |
| 132 | Nuer | nus |
| 133 | Occitan | oc |
| 134 | Odia (Oria) | or |
| 135 | Oromo | om |
| 136 | Pangasinan | pag |
| 137 | Papiamento | pap |
| 138 | Pashto | ps |
| 139 | Persian | fa |
| 140 | Polish | pl |
| 141 | Portuguese | pt |
| 142 | Portuguese (Portugal) | pt-PT |
| 143 | Portuguese (Brazil) | pt-BR |
| 144 | Punjabi | pa |
| 145 | Punjabi (Shahmukhi) | pa-Arab |
| 146 | Quechuan | qu |
| 147 | Romani | rom |
| 148 | Romanian | ro |
| 149 | Rundi | rn |
| 150 | Russian | ru |
| 151 | Samoan | sm |
| 152 | Sango | sg |
| 153 | Sanskrit | sa |
| 154 | Scottish Gaelic | gd |
| 155 | Serbian | sr |
| 156 | Sesotho | st |
| 157 | Seychellois Creole | crs |
| 158 | Shan | shn |
| 159 | Shona | sn |
| 160 | Sicilian | scn |
| 161 | Silesian | szl |
| 162 | Sindhi | sd |
| 163 | Sinhalese | si |
| 164 | Slovak | sk |
| 165 | Slovene | sl |
| 166 | Somali | so |
| 167 | Spanish | es |
| 168 | Sundanese | su |
| 169 | Swahili | sw |
| 170 | Swati | ss |
| 171 | Swedish | sv |
| 172 | Tajik | tg |
| 173 | Tamil | ta |
| 174 | Tatar | tt |
| 175 | Telugu | te |
| 176 | Tetum | tet |
| 177 | Thai | th |
| 178 | Tigrinya | ti |
| 179 | Tsonga | ts |
| 180 | Tswana | tn |
| 181 | Turkish | tr |
| 182 | Turkmen | tk |
| 183 | Twi (Akan) | ak |
| 184 | Ukrainian | uk |
| 185 | Urdu | ur |
| 186 | Uyghur | ug |
| 187 | Uzbek | uz |
| 188 | Vietnamese | vi |
| 189 | Welsh | cy |
| 190 | Xhosa | xh |
| 191 | Yiddish | yi |
| 192 | Yoruba | yo |
| 193 | Yucatec Maya | yua |
| 194 | Zulu | zu |

##### Source and Target Languages Supported by the Processing Type of Subtitle File Translation

Source Language

| No. | Language (Source Language) | Code |
| --- | --- | --- |
| 1 | Afrikaans (South Africa) | af-ZA |
| 2 | Albanian (Albania) | sq-AL |
| 3 | Amharic (Ethiopia) | am-ET |
| 4 | Arabic (Algeria) | ar-DZ |
| 5 | Arabic (Bahrain) | ar-BH |
| 6 | Arabic (Egypt) | ar-EG |
| 7 | Arabic (Iraq) | ar-IQ |
| 8 | Arabic (Israel) | ar-IL |
| 9 | Arabic (Jordan) | ar-JO |
| 10 | Arabic (Kuwait) | ar-KW |
| 11 | Arabic (Lebanon) | ar-LB |
| 12 | Arabic (Mauritania) | ar-MR |
| 13 | Arabic (Morocco) | ar-MA |
| 14 | Arabic (Oman) | ar-OM |
| 15 | Arabic (Qatar) | ar-QA |
| 16 | Arabic (Saudi Arabia) | ar-SA |
| 17 | Arabic (State of Palestine) | ar-PS |
| 18 | Arabic (Syria) | ar-SY |
| 19 | Arabic (Tunisia) | ar-TN |
| 20 | Arabic (United Arab Emirates) | ar-AE |
| 21 | Arabic (Yemen) | ar-YE |
| 22 | Armenian (Armenia) | hy-AM |
| 23 | Azerbaijani (Azerbaijan) | az-AZ |
| 24 | Basque (Spain) | eu-ES |
| 25 | Bengali (Bangladesh) | bn-BD |
| 26 | Bengali (India) | bn-IN |
| 27 | Bosnian (Bosnia and Herzegovina) | bs-BA |
| 28 | Bulgarian (Bulgaria) | bg-BG |
| 29 | Burmese (Myanmar) | my-MM |
| 30 | Catalan (Spain) | ca-ES |
| 31 | Simplified Chinese (China) | zh-CN |
| 32 | Traditional Chinese (Taiwan (China)) | zh-TW |
| 33 | Cantonese (Hong Kong (China) Traditional Chinese) | yue |
| 34 | Croatian (Croatia) | hr-HR |
| 35 | Czech (Czech Republic) | cs-CZ |
| 36 | Danish (Denmark) | da-DK |
| 37 | Dutch (Belgium) | nl-BE |
| 38 | Dutch (Netherlands) | nl-NL |
| 39 | English (Australia) | en-AU |
| 40 | English (Canada) | en-CA |
| 41 | English (Ghana) | en-GH |
| 42 | English (Hong Kong (China)) | en-HK |
| 43 | English (India) | en-IN |
| 44 | English (Ireland) | en-IE |
| 45 | English (Kenya) | en-KE |
| 46 | English (New Zealand) | en-NZ |
| 47 | English (Nigeria) | en-NG |
| 48 | English (Pakistan) | en-PK |
| 49 | English (Philippines) | en-PH |
| 50 | English (Singapore) | en-SG |
| 51 | English (South Africa) | en-ZA |
| 52 | English (Tanzania) | en-TZ |
| 53 | English (UK) | en-GB |
| 54 | English (US) | en-US |
| 55 | Estonian (Estonia) | et-EE |
| 56 | Filipino (Philippines) | fil-PH |
| 57 | Finnish (Finland) | fi-FI |
| 58 | French (Belgium) | fr-BE |
| 59 | French (Canada) | fr-CA |
| 60 | French (France) | fr-FR |
| 61 | French (Switzerland) | fr-CH |
| 62 | Galician (Spain) | gl-ES |
| 63 | Georgian (Georgia) | ka-GE |
| 64 | German (Austria) | de-AT |
| 65 | German (Germany) | de-DE |
| 66 | German (Switzerland) | de-CH |
| 67 | Greek (Greece) | el-GR |
| 68 | Gujarati (India) | gu-IN |
| 69 | Hebrew (Israel) | iw-IL |
| 70 | Hindi (India) | hi-IN |
| 71 | Hungarian (Hungary) | hu-HU |
| 72 | Icelandic (Iceland) | is-IS |
| 73 | Indonesian (Indonesia) | id-ID |
| 74 | Italian (Italy) | it-IT |
| 75 | Italian (Switzerland) | it-CH |
| 76 | Japanese (Japan) | ja-JP |
| 77 | Javanese (Indonesia) | jv-ID |
| 78 | Kannada (India) | kn-IN |
| 79 | Kazakh (Kazakhstan) | kk-KZ |
| 80 | Khmer (Cambodia) | km-KH |
| 81 | Kinyarwanda (Rwanda) | rw-RW |
| 82 | Korean (South Korea) | ko-KR |
| 83 | Lao (Laos) | lo-LA |
| 84 | Latvian (Latvia) | lv-LV |
| 85 | Lithuanian (Lithuania) | lt-LT |
| 86 | Macedonian (North Macedonia) | mk-MK |
| 87 | Malay (Malaysia) | ms-MY |
| 88 | Malayalam (India) | ml-IN |
| 89 | Marathi (India) | mr-IN |
| 90 | Mongolian (Mongolia) | mn-MN |
| 91 | Nepali (Nepal) | ne-NP |
| 92 | Bokmål Norwegian (Norway) | no-NO |
| 93 | Persian (Iran) | fa-IR |
| 94 | Polish (Poland) | pl-PL |
| 95 | Portuguese (Brazil) | pt-BR |
| 96 | Portuguese (Portugal) | pt-PT |
| 97 | Punjabi (Gurmukhi, India) | pa-Guru-IN |
| 98 | Romanian (Romania) | ro-RO |
| 99 | Russian (Russia) | ru-RU |
| 100 | Serbian (Serbia) | sr-RS |
| 101 | Sinhalese (Sri Lanka) | si-LK |
| 102 | Slovak (Slovakia) | sk-SK |
| 103 | Slovene (Slovenia) | sl-SI |
| 104 | Sesotho (South Africa) | st-ZA |
| 105 | Spanish (Argentina) | es-AR |
| 106 | Spanish (Bolivia) | es-BO |
| 107 | Spanish (Chile) | es-CL |
| 108 | Spanish (Colombia) | es-CO |
| 109 | Spanish (Costa Rica) | es-CR |
| 110 | Spanish (Dominican Republic) | es-DO |
| 111 | Spanish (Ecuador) | es-EC |
| 112 | Spanish (El Salvador) | es-SV |
| 113 | Spanish (Guatemala) | es-GT |
| 114 | Spanish (Honduras) | es-HN |
| 115 | Spanish (Mexico) | es-MX |
| 116 | Spanish (Nicaragua) | es-NI |
| 117 | Spanish (Panama) | es-PA |
| 118 | Spanish (Paraguay) | es-PY |
| 119 | Spanish (Peru) | es-PE |
| 120 | Spanish (Puerto Rico) | es-PR |
| 121 | Spanish (Spain) | es-ES |
| 122 | Spanish (US) | es-US |
| 123 | Spanish (Uruguay) | es-UY |
| 124 | Spanish (Venezuela) | es-VE |
| 125 | Sundanese (Indonesia) | su-ID |
| 126 | Swahili (Kenya) | sw-KE |
| 127 | Swahili (Tanzania) | sw-TZ |
| 128 | Swazi (Latin script, South Africa) | ss-Latn-ZA |
| 129 | Swedish (Sweden) | sv-SE |
| 130 | Tamil (India) | ta-IN |
| 131 | Tamil (Malaysia) | ta-MY |
| 132 | Tamil (Singapore) | ta-SG |
| 133 | Tamil (Sri Lanka) | ta-LK |
| 134 | Telugu (India) | te-IN |
| 135 | Thai (Thailand) | th-TH |
| 136 | Tsonga (South Africa) | ts-ZA |
| 137 | Tswana (Latin script, South Africa) | tn-Latn-ZA |
| 138 | Turkish (Türkiye) | tr-TR |
| 139 | Ukrainian (Ukraine) | uk-UA |
| 140 | Urdu (India) | ur-IN |
| 141 | Urdu (Pakistan) | ur-PK |
| 142 | Uzbek (Uzbekistan) | uz-UZ |
| 143 | Venda (South Africa) | ve-ZA |
| 144 | Vietnamese (Vietnam) | vi-VN |
| 145 | Xhosa (South Africa) | xh-ZA |
| 146 | Zulu (South Africa) | zu-ZA |

Target Languages for Translation

| No. | Language (Target Language) | Code |
| --- | --- | --- |
| 1 | Abkhaz language | ab |
| 2 | Acehnese | ace |
| 3 | Acholi | ach |
| 4 | Afrikaans | af |
| 5 | Albanian | sq |
| 6 | Alur | alz |
| 7 | Amharic | am |
| 8 | Arabic | ar |
| 9 | Armenian | hy |
| 10 | Assamese | as |
| 11 | Awadhi | awa |
| 12 | Aymara | ay |
| 13 | Azerbaijani | az |
| 14 | Balinese | ban |
| 15 | Bambara | bm |
| 16 | Bashkir | ba |
| 17 | Basque | eu |
| 18 | Batak Karo | btx |
| 19 | Batak Simalungun | bts |
| 20 | Batak Toba | bbc |
| 21 | Belarusian | be |
| 22 | Bemba | bem |
| 23 | Bengali | bn |
| 24 | Betawi | bew |
| 25 | Bhojpuri | bho |
| 26 | Bikol | bik |
| 27 | Bosnian | bs |
| 28 | Breton | br |
| 29 | Bulgarian | bg |
| 30 | Buryat | bua |
| 31 | Cantonese | yue |
| 32 | Catalan | ca |
| 33 | Cebuano | ceb |
| 34 | Chichewa (Nyanja) | ny |
| 35 | Simplified Chinese | zh-CN or zh |
| 36 | Chinese (Traditional) | zh-TW |
| 37 | Chuvash | cv |
| 38 | Corsican | co |
| 39 | Crimean Tatar | crh |
| 40 | Croatian | hr |
| 41 | Czech | cs |
| 42 | Danish | da |
| 43 | Dinka | din |
| 44 | Divehi | dv |
| 45 | Dogri | doi |
| 46 | Dombe | dov |
| 47 | Dutch | nl |
| 48 | Dzongkha | dz |
| 49 | English | en |
| 50 | Esperanto | eo |
| 51 | Estonian | et |
| 52 | Ewe | ee |
| 53 | Fijian | fj |
| 54 | Filipino (Tagalog) | fil or tl |
| 55 | Finnish | fi |
| 56 | French | fr |
| 57 | French (France) | fr-FR |
| 58 | French (Canada) | fr-CA |
| 59 | Frisian | fy |
| 60 | Fula | ff |
| 61 | Ga | gaa |
| 62 | Galician | gl |
| 63 | Ganda (Luganda) | lg |
| 64 | Georgian | ka |
| 65 | German | de |
| 66 | Greek | el |
| 67 | Guarani | gn |
| 68 | Gujarati | gu |
| 69 | Haitian Creole | ht |
| 70 | Hakha Chin | cnh |
| 71 | Hausa | ha |
| 72 | Hawaiian | haw |
| 73 | Hebrew | iw or he |
| 74 | Hiligaynon | hil |
| 75 | Hindi | hi |
| 76 | Hmong | hmn |
| 77 | Hungarian | hu |
| 78 | Hunsrik | hrx |
| 79 | Icelandic | is |
| 80 | Igbo | ig |
| 81 | Iloko | ilo |
| 82 | Indonesian | id |
| 83 | Irish | ga |
| 84 | Italian | it |
| 85 | Japanese | ja |
| 86 | Javanese | jw or jv |
| 87 | Kannada | kn |
| 88 | Kapampangan | pam |
| 89 | Kazakh | kk |
| 90 | Khmer | km |
| 91 | Kiga | cgg |
| 92 | Kinyarwanda | rw |
| 93 | Kituba | ktu |
| 94 | Goan Konkani | gom |
| 95 | Korean | ko |
| 96 | Krio | kri |
| 97 | Kurdish (Kurmanji) | ku |
| 98 | Kurdish (Sorani) | ckb |
| 99 | Kirghiz | ky |
| 100 | Lao | lo |
| 101 | Latgalian | ltg |
| 102 | Latin | la |
| 103 | Latvian | lv |
| 104 | Ligurian | lij |
| 105 | Limburgish | li |
| 106 | Lingala | ln |
| 107 | Lithuanian | lt |
| 108 | Lombard | lmo |
| 109 | Luo | luo |
| 110 | Luxembourgish | lb |
| 111 | Macedonian | mk |
| 112 | Maithili | mai |
| 113 | Makassar | mak |
| 114 | Malagasy | mg |
| 115 | Malay | ms |
| 116 | Malay (Jawi script) | ms-Arab |
| 117 | Malayalam | ml |
| 118 | Maltese | mt |
| 119 | Maori | mi |
| 120 | Marathi | mr |
| 121 | Meadow Mari language | chm |
| 122 | Meitei (Manipuri) | mni-Mtei |
| 123 | Minangkabau | min |
| 124 | Mizo | lus |
| 125 | Mongolian | mn |
| 126 | Burmese | my |
| 127 | Ndebele (southern) | nr |
| 128 | Nepali (Newar) | new |
| 129 | Nepali | ne |
| 130 | Northern Sotho (Sepedi) | nso |
| 131 | Norwegian | no |
| 132 | Nuer | nus |
| 133 | Occitan | oc |
| 134 | Odia (Oria) | or |
| 135 | Oromo | om |
| 136 | Pangasinan | pag |
| 137 | Papiamento | pap |
| 138 | Pashto | ps |
| 139 | Persian | fa |
| 140 | Polish | pl |
| 141 | Portuguese | pt |
| 142 | Portuguese (Portugal) | pt-PT |
| 143 | Portuguese (Brazil) | pt-BR |
| 144 | Punjabi | pa |
| 145 | Punjabi (Shahmukhi) | pa-Arab |
| 146 | Quechuan | qu |
| 147 | Romani | rom |
| 148 | Romanian | ro |
| 149 | Rundi | rn |
| 150 | Russian | ru |
| 151 | Samoan | sm |
| 152 | Sango | sg |
| 153 | Sanskrit | sa |
| 154 | Scottish Gaelic | gd |
| 155 | Serbian | sr |
| 156 | Sesotho | st |
| 157 | Seychellois Creole | crs |
| 158 | Shan | shn |
| 159 | Shona | sn |
| 160 | Sicilian | scn |
| 161 | Silesian | szl |
| 162 | Sindhi | sd |
| 163 | Sinhalese | si |
| 164 | Slovak | sk |
| 165 | Slovene | sl |
| 166 | Somali | so |
| 167 | Spanish | es |
| 168 | Sundanese | su |
| 169 | Swahili | sw |
| 170 | Swati | ss |
| 171 | Swedish | sv |
| 172 | Tajik | tg |
| 173 | Tamil | ta |
| 174 | Tatar | tt |
| 175 | Telugu | te |
| 176 | Tetum | tet |
| 177 | Thai | th |
| 178 | Tigrinya | ti |
| 179 | Tsonga | ts |
| 180 | Tswana | tn |
| 181 | Turkish | tr |
| 182 | Turkmen | tk |
| 183 | Twi (Akan) | ak |
| 184 | Ukrainian | uk |
| 185 | Urdu | ur |
| 186 | Uyghur | ug |
| 187 | Uzbek | uz |
| 188 | Vietnamese | vi |
| 189 | Welsh | cy |
| 190 | Xhosa | xh |
| 191 | Yiddish | yi |
| 192 | Yoruba | yo |
| 193 | Yucatec Maya | yua |
| 194 | Zulu | zu |

### Smart Subtitle Billing

Postpaid billing is supported. See [Billing Overview](https://www.tencentcloud.com/en/document/product/1041/49204#cdddc3f6-4ddd-4031-aae5-70e83196011a) for details.


---
*Source: [https://www.tencentcloud.com/document/product/1041/54517](https://www.tencentcloud.com/document/product/1041/54517)*
