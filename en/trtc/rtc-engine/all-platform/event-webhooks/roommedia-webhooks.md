# Room&Media Webhooks

The event callback service can send notifications about TRTC events in the form of HTTP/HTTPS requests to your server. Currently, you can register callbacks for room events, media events, as well as some recording events (for details about on-cloud recording callbacks, see [On-Cloud Recording](https://www.tencentcloud.com/document/product/647/45169#)). To receive such callbacks, you need to configure callback information in the TRTC console.

## Callback Information

In order to receive event callback notifications, you need to configure callback information in [Tencent RTC Console](https://console.trtc.io/app).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/808f108d9c0f11ef820f525400d5f8ef.jpeg)

> **Note:**You need to provide the following information:**Required**: An HTTP/HTTPS server address to receive callback notifications.**Optional**: A custom [key](https://www.tencentcloud.com/document/product/647/39558#signature-calculation) containing up to 32 uppercase and lowercase letters and digits, which is needed for the calculation of signatures.

## Timeout and Retry

A notification will be considered failed if the callback server does not receive a response from your server within five seconds of message sending. It will try again immediately after the first failure and retry **10 seconds** after every subsequent failure. The retries will stop one minute after the first try.

## Format of Callback Messages

Callbacks are sent to your server in the form of HTTP/HTTPS POST requests.

- **Character encoding**: UTF-8
- **Request**: JSON for the request body
- **Response**: HTTP STATUS CODE = 200. The server ignores the content of the response packet. For protocol-friendliness, we recommend adding `JSON: `{"code":0}` to the response.

## Parameters

### Callback parameters

- The header of a callback message contains the following fields.

| Field | Value |
| --- | --- |
| Content-Type | application/json |
| Sign | The signature value. |
| SdkAppId | The SDK application ID. |

- The body of a callback message contains the following fields.

| Field | Type | Description |
| --- | --- | --- |
| EventGroupId | Number | [The event group ID.](https://www.tencentcloud.com/document/product/647/39558#event-group-id) |
| EventType | Number | [The type of the callback event.](https://www.tencentcloud.com/document/product/647/39558#event-type) |
| CallbackTs | Number | The Unix timestamp (ms) of callback sending. |
| EventInfo | JSON Object | [The event information.](https://www.tencentcloud.com/document/product/647/39558#event-information) |

### Event group ID

| Field | Value | Description |
| --- | --- | --- |
| EVENT_GROUP_ROOM | 1 | Room event group |
| EVENT_GROUP_MEDIA | 2 | Media event group |

> **Note:**For on-cloud recording events, see [On-Cloud Recording](https://www.tencentcloud.com/document/product/647/45169#).

### Event type

| Field | Value | Description |
| --- | --- | --- |
| EVENT_TYPE_CREATE_ROOM | 101 | Creating room |
| EVENT_TYPE_DISMISS_ROOM | 102 | Closing room |
| EVENT_TYPE_ENTER_ROOM | 103 | Entering room |
| EVENT_TYPE_EXIT_ROOM | 104 | Leaving room |
| EVENT_TYPE_CHANGE_ROLE | 105 | Switching roles |
| EVENT_TYPE_START_VIDEO | 201 | Starting pushing video data |
| EVENT_TYPE_STOP_VIDEO | 202 | Stopping pushing video data |
| EVENT_TYPE_START_AUDIO | 203 | Starting pushing audio data |
| EVENT_TYPE_STOP_AUDIO | 204 | Stopping pushing audio data |
| EVENT_TYPE_START_ASSIT | 205 | Starting pushing substream data |
| EVENT_TYPE_STOP_ASSIT | 206 | Stopping pushing substream data |

> **Note:**Room exit will trigger only the `104` callback and not the `202` or `204` callback. `202` and `204` are triggered only if a user manually turns their video and audio off.

#### Event Callback Example

101

102

103

104

105

201

202

203

204

205

206

```
{	"EventGroupId":	1,	"EventType":	101, 	"CallbackTs":	1687770730166,  	"EventInfo":	{   		"RoomId":	12345,     	"EventTs":	1687770730,      	"EventMsTs":	1687770730160,       	"UserId":	"test"	        }}
```

```
{    "EventGroupId":	1,    "EventType":	102,    "CallbackTs":	1687771618531,    "EventInfo":	{    	"RoomId":	"12345",     	"EventTs":	1687771618,	      	"EventMsTs":	1687771618457	     }}
```

```
{	"EventGroupId":	1,	"EventType":	103,	"CallbackTs":	1687770731932,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687770731,		"EventMsTs":	1687770731831,		"UserId":	"test",		"Role":	21,		"TerminalType":	2,		"UserType":	3,		"Reason":	1	}}
```

```
{	"EventGroupId":	1,	"EventType":	104,	"CallbackTs":	1687770731922,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687770731,		"EventMsTs":	1687770731898,		"UserId":	"test",		"Role":	20,		"Reason":	1	}}
```

```
{	"EventGroupId":	1,	"EventType":	105,	"CallbackTs":	1687772245596,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687772245,		"EventMsTs":	1687772245537,		"UserId":	"test",		"Role":	21	}}
```

```
{	"EventGroupId":	2,	"EventType":	201,	"CallbackTs":	1687771803198,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687771803,		"EventMsTs":	1687771803192,		"UserId":	"test"	}}
```

```
{	"EventGroupId":	2,	"EventType":	202,	"CallbackTs":	1687771919458,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687771919,		"EventMsTs":	1687771919447,		"UserId":	"test",		"Reason":	0	}}
```

```
{	"EventGroupId":	2,	"EventType":	203,	"CallbackTs":	1687771869377,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687771869,		"EventMsTs":	1687771869365,		"UserId":	"test"	}}
```

```
{	"EventGroupId":	2,	"EventType":	204,	"CallbackTs":	1687770732498,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687770732,		"EventMsTs":	1687770732383,		"UserId":	"test",		"Reason":	0	}}
```

```
{	"EventGroupId":	2,	"EventType":	205,	"CallbackTs":	1687772013823,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687772013,		"EventMsTs":	1687772013753,		"UserId":	"test"	}}
```

```
{	"EventGroupId":	2,	"EventType":	206,	"CallbackTs":	1687772015054,	"EventInfo":	{		"RoomId":	12345,		"EventTs":	1687772015,		"EventMsTs":	1687772015032,		"UserId":	"test",		"Reason":	0	}}
```

### Event information

| Field | Type | Description |
| --- | --- | --- |
| RoomId | String/Number | The room ID, which is of the same type as the room ID on the client. |
| EventTs | Number | The Unix timestamp (seconds) of event occurrence. This field is reserved for compatibility purposes. |
| EventMsTs | Number | The Unix timestamp (ms) of event occurrence. |
| UserId | String | User ID |
| UniqueId | Number | The unique identifier of an event (optional), which is valid for the room event group. When a user experiences unusual events such as network change or abnormal exit and reentry, your server may receive multiple callbacks for the entry and exit of the same user. A unique identifier helps identify a room entry or exit. |
| Role | Number | [The role type](https://www.tencentcloud.com/document/product/647/39558#role-type) (optional), which is valid for the room entry/exit callback. |
| TerminalType | Number | [The device type](https://www.tencentcloud.com/document/product/647/39558#device-type) (optional), which is valid for the room entry callback. |
| UserType | Number | [The user type](https://www.tencentcloud.com/document/product/647/39558#user-type) (optional), which is valid for the room entry callback. |
| Reason | Number | [The reason](https://www.tencentcloud.com/document/product/647/39558#reason) (optional), which is valid for the room entry/exit callback. |

> **Note:**We have developed a policy that prevents repeated callbacks resulting from unusual events on the client. If you start using the callback service after July 30, 2021, the policy will apply by default, and the room event group will no longer carry UniqueId.

### Role type

| Field | Value | Description |
| --- | --- | --- |
| MEMBER_TRTC_ANCHOR | 20 | Anchor |
| MEMBER_TRTC_VIEWER | 21 | Audience |

### Device type

| Field | Value | Description |
| --- | --- | --- |
| TERMINAL_TYPE_WINDOWS | 1 | Windows |
| TERMINAL_TYPE_ANDROID | 2 | Android |
| TERMINAL_TYPE_IOS | 3 | iOS |
| TERMINAL_TYPE_LINUX | 4 | Linux |
| TERMINAL_TYPE_OTHER | 100 | Other |

### User type

| Field | Value | Description |
| --- | --- | --- |
| USER_TYPE_WEBRTC | 1 | WebRTC |
| USER_TYPE_APPLET | 2 | Mini Program |
| USER_TYPE_NATIVE_SDK | 3 | Native SDK |

### Reason

| Field | Description |
| --- | --- |
| Room entry | 1: Voluntary entry 2: Network change3: Timeout and retry 4: Cross-room communication |
| Room exit | 1: Voluntary exit 2: Timeout3: Removed from the room4: Cross-room communication was canceled5: The process was force-closed**Note: TRTC cannot capture a force-close event on Android and will send a callback only after timeout (**`reason`**=**`2`**).** |

### Signature calculation

Signatures are calculated using the HMAC SHA256 encryption algorithm. Upon receiving a callback message, your server will calculate a signature using the same method, and if the results match, it indicates that the callback is from TRTC and not forged. See below for the calculation method.

```
// In the formula below, `key` is the key used to calculate a signature.Sign = base64(hmacsha256(key, body))
```

> **Note:**`body` is the original packet body of the callback request you receive. Do not make any modifications. Below is an example.body="{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t103,\\n\\t\\"CallbackTs\\":\\t1615554923704,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t12345,\\n\\t\\t\\"EventTs\\":\\t1608441737,\\n\\t\\t\\"UserId\\":\\t\\"test\\",\\n\\t\\t\\"UniqueId\\":\\t1615554922656,\\n\\t\\t\\"Role\\":\\t20,\\n\\t\\t\\"Reason\\":\\t1\\n\\t}\\n}"

### Verify signature example

Java

Python

PHP

Golang

```
import javax.crypto.Mac;import javax.crypto.spec.SecretKeySpec;import java.util.Base64;//# Function: Third-party callback sign verification//# Parameters://#   key: The key configured in the console//#   body: The body returned by the Tencent Cloud callback//#   sign: The sign value returned by the Tencent Cloud callback//# Return Value://#   Status: OK indicates that the verification has passed, FAIL indicates that the verification has failed, and the specific reason can be found in the Info//#   Info: Success/Failure informationpublic class checkSign {Â  Â  public static String getResultSign(String key, String body) throws Exception {Â  Â  Â  Â  Mac hmacSha256 = Mac.getInstance("HmacSHA256");Â  Â  Â  Â  SecretKeySpec secret_key = new SecretKeySpec(key.getBytes(), "HmacSHA256");Â  Â  Â  Â  hmacSha256.init(secret_key);Â  Â  Â  Â  return Base64.getEncoder().encodeToString(hmacSha256.doFinal(body.getBytes()));Â  Â  }Â  Â  public static void main(String[] args) throws Exception {Â  Â  Â  Â  String key = "123654";Â  Â  Â  Â  String body = "{\\n" + "\\t\\"EventGroupId\\":\\t2,\\n" + "\\t\\"EventType\\":\\t204,\\n" + "\\t\\"CallbackTs\\":\\t1664209748188,\\n" + "\\t\\"EventInfo\\":\\t{\\n" + "\\t\\t\\"RoomId\\":\\t8489,\\n" + "\\t\\t\\"EventTs\\":\\t1664209748,\\n" + "\\t\\t\\"EventMsTs\\":\\t1664209748180,\\n" + "\\t\\t\\"UserId\\":\\t\\"user_85034614\\",\\n" + "\\t\\t\\"Reason\\":\\t0\\n" + "\\t}\\n" + "}";Â  Â  Â  Â  String Sign = "kkoFeO3Oh2ZHnjtg8tEAQhtXK16/KI05W3BQff8IvGA=";Â  Â  Â  Â  String resultSign = getResultSign(key, body);Â  Â  Â  Â  if (resultSign.equals(Sign)) {Â  Â  Â  Â  Â  Â  System.out.println("{'Status': 'OK', 'Info': 'validation passed'}");Â  Â  Â  Â  } else {Â  Â  Â  Â  Â  Â  System.out.println("{'Status': 'FAIL', 'Info': 'validation failed'}");Â  Â  Â  Â  }Â  Â  }}
```

```
# -*- coding: utf8 -*-import hmacimport base64from hashlib import sha256# Function: Third-party callback sign verification# Parameters:#   key: The key configured in the console#   body: The body returned by the Tencent Cloud callback#   sign: The sign value returned by the Tencent Cloud callback# Return Value:#   Status: OK indicates that the verification has passed, FAIL indicates that the verification has failed, and the specific reason can be found in the Info#   Info: Success/Failure informationdef checkSign(key, body, sign):Â  Â  temp_dict = {}Â  Â  computSign = base64.b64encode(hmac.new(key.encode('utf-8'), body.encode('utf-8'), digestmod=sha256).digest()).decode('utf-8')Â  Â  print(computSign)Â  Â  if computSign == sign:Â  Â  Â  Â  temp_dict['Status'] = 'OK'Â  Â  Â  Â  temp_dict['Info'] = 'validation passed'Â  Â  Â  Â  return temp_dictÂ  Â  else:Â  Â  Â  Â  temp_dict['Status'] = 'FAIL'Â  Â  Â  Â  temp_dict['Info'] = 'validation failed'Â  Â  Â  Â  return temp_dictif __name__ == '__main__':Â  Â  key = '123654'Â  Â  body = "{\\n" + "\\t\\"EventGroupId\\":\\t2,\\n" + "\\t\\"EventType\\":\\t204,\\n" + "\\t\\"CallbackTs\\":\\t1664209748188,\\n" + "\\t\\"EventInfo\\":\\t{\\n" + "\\t\\t\\"RoomId\\":\\t8489,\\n" + "\\t\\t\\"EventTs\\":\\t1664209748,\\n" + "\\t\\t\\"EventMsTs\\":\\t1664209748180,\\n" + "\\t\\t\\"UserId\\":\\t\\"user_85034614\\",\\n" + "\\t\\t\\"Reason\\":\\t0\\n" + "\\t}\\n" + "}"Â  Â  sign = 'kkoFeO3Oh2ZHnjtg8tEAQhtXK16/KI05W3BQff8IvGA='Â  Â  result = checkSign(key, body, sign)Â  Â  print(result)
```

```
<?phpclass TlsEventSig {        private $key = false;    private $body = false;        public function __construct( $key, $body ) {        $this->key = $key;		$this->body = $body;    }    private function __hmacsha256() {        $hash = hash_hmac( 'sha256', $this->body, $this->key, true );		return base64_encode( $hash);    }        public function genEventSig() {        return $this->__hmacsha256();    }}$key="789";$data="{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t101,\\n\\t\\"CallbackTs\\":\\t1608086882372,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t20222,\\n\\t\\t\\"EventTs\\":\\t1608086882,\\n\\t\\t\\"UserId\\":\\t\\"222222_phone\\"\\n\\t}\\n}";$api = new  TlsEventSig($key, $data);echo $api->genEventSig();
```

```
package mainimport "fmt"import (	"crypto/hmac"	"crypto/sha256"	"encoding/base64")func main () {    var data = "{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t101,\\n\\t\\"CallbackTs\\":\\t1608086882372,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t20222,\\n\\t\\t\\"EventTs\\":\\t1608086882,\\n\\t\\t\\"UserId\\":\\t\\"222222_phone\\"\\n\\t}\\n}"    var key = "789"    //JSRUN engine 2.0, supporting up to 30 types of languages for online running, with full simulation of online interaction for input and output.    fmt.Println(hmacsha256(data,key))}func hmacsha256(data string, key string) string {	h := hmac.New(sha256.New, []byte(key))	h.Write([]byte(data))	return base64.StdEncoding.EncodeToString(h.Sum(nil))}
```


---
*Source: [https://trtc.io/document/39558](https://trtc.io/document/39558)*
