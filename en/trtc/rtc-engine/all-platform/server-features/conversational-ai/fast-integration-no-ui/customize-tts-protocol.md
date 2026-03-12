# Customize TTS protocol

## Invocation Mode

POST : http://xxxxxxxxxxxx/api/v1/tts/stream

## Example

### HTTP Request Header

```
Content-Type: application/json;charset=UTF-8
X-Task-Id: task_id_value
X-Rquest-Id: request_id
X-Sdk-App-Id: SdkAppId
X-User-Idï¼UserId
X-Room-Idï¼RoomId 
X-Room-Id-Type: "0" 
Authorization: Bearer "API-KEY"
```

### Request  Example

```
{
  "Text": "Hello, world! This is a test for the streaming TTS API.ã",
  "Format": "wav",
  "SampleRate": 16000,
  "Channel": 1
}
```

## HTTP Request Header

| field | describe |
| --- | --- |
| Content-Type | application/json |
| charset | UTF-8 |
| X-Task-Id | The ID of the conversation task |
| X-Rquest-Id | The Id of the request, the retry will carry the same RequestId |
| X-Sdk-App-Id | AppId for the SDK |
| X-User-Id | UserId |
| X-Room-Id | Romm Id |
| X-Room-Id-Type | RommId type, 0 - numeric room number, 1 - character string room number |
| Authorization | Authentication, in the form of Bearer "API-KEY" |

## Request Parameter

| Parameter name | Required | type | describe |
| --- | --- | --- | --- |
| Text | yes | String | Voice text |
| Format | no | String | The desired audio format for output, such asMp3, ogg _ opus, pcm, wav, wav by default,Only PCM and WAV are supported. |
| SampleRate | no | Integer | Audio sampling rate, defaults to 16000 (16k), recommends 16000 |
| Channel | no | Integer | Audio channel, value: 1 or 2Default 1 |

## Response

The value of Content-Type needs to be used to determine if the synthesis was successful.

- **If successful**, the normal return to binary speech, different audio frequency format Content-Type as follows, need to be set in the header of the HTTP responseTransfer-Encoding: chunkedã

| Audio format | Content-Type |
| --- | --- |
| mp3 | audio/mpeg |
| ogg_opus | audio/ogg |
| pcm | audio/L16 |
| wav | audio/wav |

- **If it fails**, the JSON result is returned with the header information: Content-type: application / json. The response is:

```
  {
  "error": {
    "code": "ERROR_CODE",
    "message": "A description of the error"
  }
}
```


---
*Source: [https://trtc.io/document/65315](https://trtc.io/document/65315)*
