# Push Online Media Stream Webhooks

The server-side push online media stream callback supports notifying your server of push online media stream events generated using the [Push Online Media Stream](https://www.tencentcloud.com/document/product/647/57835) REST API in the form of HTTP/HTTPS requests. You can provide Tencent Cloud with relevant configuration information to enable this service.

## Configuration Information

The TRTC console supports self-service configuration of callback information. Once the configuration is completed, you can receive event callback notifications. For detailed operation instructions, see the [Callback Configuration](https://www.tencentcloud.com/document/product/647/39559#).

> **Note:**You need to prepare the following information in advance:**Required item**: An HTTP/HTTPS server address to receive callback notifications.**Optional item**: A [key](https://www.tencentcloud.com/document/product/647/54913#signature-calculation) for signature calculation, which is a key of up to 32 characters defined by you and consists of uppercase and lowercase letters and numbers.

## Timeout Retry

If the event callback server does not receive a response from your server within 5 seconds after sending a message notification, the notification is considered to have failed. After the first notification failure, a retry will be made immediately. Subsequent retries will occur at 10-second intervals until the message retention time exceeds 1 minute, after which no further retries will be made.

## Format of Event Callback Messages

Event callback messages are sent to your server via HTTP/HTTPS POST requests, where:

- **Character Encoding Format**: UTF-8.
- **Request**: The body is in the JSON format.
- **Response**: HTTP STATUS CODE = 200. The server ignores the specific content of the response package. For the sake of protocol friendliness, it is recommended that the customer response carry JSON: {"code":0}.
- **Package Body Example**: Below is a package body example for the "push online media stream started successfully" event.

```
{        "EventGroupId": 7,        "EventType":    701,        "CallbackMsTs":   1701937900012,        "EventInfo":    {                "EventMsTs": 1701937900013,                "TaskId":"xx",                "Status":0        }}
```

## Description of Parameters

### Callback Message Parameters

- The header of the event callback message contains the following fields:

| Field name | Value |
| --- | --- |
| Content-Type | application/json |
| Sign | Signature value |
| SdkAppId | sdk application id |

- The body of the event callback message includes the following fields:

| Field name | Type | Meaning |
| --- | --- | --- |
| EventGroupId | Number | Event group ID, which is 4 for a stream mixing and relaying event |
| EventType | Number | The event type of the callback notification |
| CallbackMsTs | Number | The Unix timestamp of the callback request sent by the event callback server to your server, in milliseconds |
| EventInfo | JSON Object | [Event information](#event_infor) |

### Event Group ID

| Field name | Value | Meaning |
| --- | --- | --- |
| EVENT_GROUP_STREAM_INGEST | 7 | Push online media stream event group |

### Event Type

| Field name | Value | Meaning |
| --- | --- | --- |
| EVENT_TYPE_STREAM_INGEST_START | 701 | Push online media stream start |
| EVENT_TYPE_STREAM_INGEST_STOP | 702 | Push online media stream stop |

### Definition of Event Information when the Event Type is (EVENT_TYPE_STREAM_INGEST_START 701):

| Field name | Type | Meaning |
| --- | --- | --- |
| EventMsTs | String | The Unix timestamp of the event occurred, in milliseconds |
| TaskId | String | Push online media stream task ID |
| Status | Number | [Status of push online media stream start](https://www.tencentcloud.com/document/product/647/62717#Status) |

#### Status of Push Online Media Stream Start

| Field name | Value | Meaning | Callback frequency |
| --- | --- | --- | --- |
| STATUS_START_SUCCESS | 0 | The push online media stream start succeeded. | Callback is made once upon success. |
| STATUS_START_FAILURE | 1 | The push online media stream start failed. | Callback is made once upon failure. |
| STATUS_START_AGAIN | 2 | The push online media stream starts again. | A retry is made at the 0th, 1st, and 3rd second, with callback during the retry. |

#### Recommended Handling of Push Online Media Stream Status

| Status | Handling method |
| --- | --- |
| STATUS_START_SUCCESS | It indicates success, with no need for handling. |
| STATUS_START_FAILURE | If you receive push online media stream failure status three times, check the source URL and restart the push online media stream. |
| STATUS_START_AGAIN | Received within 1 minute after the push online media stream starts: It indicates the URL connection failed or the RTMP push failed. The system automatically triggers a retry. If it fails in the end, check if the URL is properly connectedReceived beyond 1 minute after the push online media stream starts: A restart may be triggered due to source stream or background network fluctuation, with no need for handling. |

#### Basic Callback Transfer Example

- **Event transfer of push online media stream failure/push online media stream restart/push online media stream start success**
`STATUS_START_FAILURE` -> `STATUS_START_AGAIN` -> `STATUS_START_SUCCESS`

> **Note:**Push online media stream callback events may arrive at your callback server out of sequence. You need to sort events based on EventMsTs in EventInfo. If you only care about the latest status of the URL, you can ignore the expired events that arrive later.

### Definition of Event Information when the Event Type is (EVENT_TYPE_STREAM_INGEST_STOP 702):

| Field name | Type | Meaning |
| --- | --- | --- |
| EventMsTs | String | The Unix timestamp of the event occurred, in milliseconds |
| TaskId | String | Push online media stream task ID |
| Status | Number | [Status of push online media stream stop](https://www.tencentcloud.com/document/product/647/62717#d463b03d-a623-49a5-afc9-0fb8eeef1ea8) |

#### Status of Push Online Media Stream Stop

| Field name | Value | Meaning | Callback Frequency |
| --- | --- | --- | --- |
| STATUS_STOP_SUCCESS | 0 | The push online media stream stop succeeded. | Callback is made once upon success. |

## Calculating a Signature

A signature is calculated with the HMAC SHA256 encryption algorithm. After your event callback server receives the callback message, it calculates the signature in the same manner. A match means that it is TRTC's event callback, with no falsification. The signature calculation is shown below:

```
// In the signature calculation formula Sign, the key refers to the encryption key used.Sign = base64(hmacsha256(key, body))
```

> **Note:** The body refers to the original package body of the callback request received by you, with no transformation. An example is as follows:body="{\\n\\t\\"Ebody="{\\"EventGroupId\\":7,\\"EventType\\":701,\\"CallbackMsTs\\":1701937900012,\\"EventInfo\\":{\\"EventMsTs\\":1701937900012,\\"TaskId\\":\\"WMdqEeEgj2ksqnyUsuXC+qLkVypGmwjrgh1JC6ZefVP+rvsidDnZsAw8uWgX0XRGvdSVfAMunise2kcZaefdgHvx3-M2v6fmTjRNgg..\\",\\"Status\\":0}}"ventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t103,\\n\\t\\"CallbackTs\\":\\t1615554923704,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t12345,\\n\\t\\t\\"EventTs\\":\\t1608441737,\\n\\t\\t\\"UserId\\":\\t\\"test\\",\\n\\t\\t\\"UniqueId\\":\\t1615554922656,\\n\\t\\t\\"Role\\":\\t20,\\n\\t\\t\\"Reason\\":\\t1\\n\\t}\\n}"

## Signature Verification Example

Java

Python

PHP

Golang

```
import javax.crypto.Mac;import javax.crypto.spec.SecretKeySpec;import java.util.Base64;//# Feature: Third-party Callback Sign Verification//# Parameters://#   key: The Key Configured on the Console//#   body: The Body Returned by Tencent Cloud Callback//#   sign: The Signature Value Returned by Tencent Cloud Callback//# Returned Values://#   Status: OK Indicates that Verification Succeeded, and FAIL Indicates that Verification Failed. Refer to Info for Details//#   Info: Success/Failure Informationpublic class checkSign {    public static String secureFinalSign(String key, String entityBody) throws Exception {        Mac hmacSha256 = Mac.getInstance("HmacSHA256");        SecretKeySpec secret_key = new SecretKeySpec(key.getBytes(), "HmacSHA256");        hmacSha256.initialize(secret_key);        return Base64.getEncoder().encodeToString(hmacSha256.doFinal(body.getBytes()));    }    public static void main(String[] args) throws Exception {        String key = "123654";        String body = "{\\n" + "\\t\\"EventGroupId\\":\\t2,\\n" + "\\t\\"EventType\\":\\t204,\\n" + "\\t\\"CallbackTs\\":\\t1664209748188,\\n" + "\\t\\"EventInfo\\":\\t{\\n" + "\\t\\t\\"RoomId\\":\\t8489,\\n" + "\\t\\t\\"EventTs\\":\\t1664209748,\\n" + "\\t\\t\\"EventMsTs\\":\\t1664209748180,\\n" + "\\t\\t\\"UserId\\":\\t\\"user_85034614\\",\\n" + "\\t\\t\\"Reason\\":\\t0\\n" + "\\t}\\n" + "}";        String Sign = "kkoFeO3Oh2ZHnjtg8tEAQhtXK16/KI05W3BQff8IvGA=";        String resultSign = obtainResultSignature(key, body);        if (resultSign.equals(Sign)) {            System.out.println("{'Status': 'OK', 'Info': 'Verification succeeded'}");        } else {            System.out.println("{'Status': 'FAIL', 'Info': 'Verification failed'}");        }    }}
```

```
# -*- coding: utf8 -*-import hmacimport base64from hashlib import sha256# Feature: Third-party Callback Sign Verification# Parameters:#   key: The Key on the Console#   body: The Body Returned by Tencent Cloud Callback#   sign: The Signature Value Returned by Tencent Cloud Callback# Returned Values:#   Status: OK Indicates that Verification Succeeded, and FAIL Indicates that Verification Failed. Refer to Info for Details#   Info: Success/Failure Informationdef checkSign(key, body, sign):    temp_dict = {}    computSign = base64.b64encode(hmac.new(key.encode('utf-8'), body.encode('utf-8'), digestmod=sha256).digest()).decode('utf-8')    print(computSign)    if computSign equals sign:        temp_dict['Status'] = 'OK'        temp_dict['Info'] = 'Verification succeeded'        return temporary_dictionary    else:        temp_dict['Status'] = 'FAIL'        temp_dict['Info'] = 'Verification failed'        return temporary_dictionaryif __name__ == '__main__':    key = '123654'    body = "{\\n" + "\\t\\"EventGroupId\\":\\t2,\\n" + "\\t\\"EventType\\":\\t204,\\n" + "\\t\\"CallbackTs\\":\\t1664209748188,\\n" + "\\t\\"EventInfo\\":\\t{\\n" + "\\t\\t\\"RoomId\\":\\t8489,\\n" + "\\t\\t\\"EventTs\\":\\t1664209748,\\n" + "\\t\\t\\"EventMsTs\\":\\t1664209748180,\\n" + "\\t\\t\\"UserId\\":\\t\\"user_85034614\\",\\n" + "\\t\\t\\"Reason\\":\\t0\\n" + "\\t}\\n" + "}"    `sign` = 'kkoFeO3Oh2ZHnjtg8tEAQhtXK16/KI05W3BQff8IvGA='    result = verifySignature(key, body, sign)    print(result)
```

```
<?phpclass TlsEventSig {        private $key = false;    private $body = false;        public function __construct( $key, $body ) {        $this->key = $key;		$this->body = $body;    }    private function __hmacsha256() {        $hash = hash_hmac( 'sha256', $this->body, $this->key, true );		return base64_encode( $hash);    }        public function genEventSig() {        return $this->__hmacsha256();    }}$key="789";$data="{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t101,\\n\\t\\"CallbackTs\\":\\t1608086882372,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t20222,\\n\\t\\t\\"EventTs\\":\\t1608086882,\\n\\t\\t\\"UserId\\":\\t\\"222222_phone\\"\\n\\t}\\n}";$api = new  TlsEventSig($key, $data);echo $api->genEventSig();
```

```
package mainimport "fmt"import (	"crypto/hmac"	"crypto/sha256"	"encoding/base64")func main () {    var data = "{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t101,\\n\\t\\"CallbackTs\\":\\t1608086882372,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t20222,\\n\\t\\t\\"EventTs\\":\\t1608086882,\\n\\t\\t\\"UserId\\":\\t\\"222222_phone\\"\\n\\t}\\n}"    var key = "789"    //JSRUN Engine 2.0, which supports online running in up to 30 languages and fully simulates online interactive input and output.    fmt.Println(hmacsha256(data,key))}func hmacsha256(data string, key string) string {	h := hmac.New(sha256.New, []byte(key))	h.Write([]byte(data))	return base64.StdEncoding.EncodeToString(h.Sum(nil))}
```


---
*Source: [https://trtc.io/document/62717](https://trtc.io/document/62717)*
