# Verify Signature Example

[Tencent Real-Time Communication(TRTC) console](https://console.tencentcloud.com/trtc) supports self-configuration of callback information. After the configuration is completed, you can receive event callback notifications. Before configuring the callback information, you need to prepare a [key](/document/product/647/54912#signature-calculation) for signature calculation. You can define a key with a maximum of 32 characters, composed of uppercase and lowercase letters and numbers.

This document will help you verify signature after calculating it and show you how to perform an example.

## Signature calculation

Signatures are calculated using the HMAC SHA256 encryption algorithm. Upon receiving a callback message, your server will calculate a signature using the same method, and if the results match, it indicates that the callback is from TRTC and not forged. See below for the calculation method.

```
// In the formula below, `key` is the key used to calculate a signature.Sign = base64(hmacsha256(key, body))
```

> **Note**`body` is the original packet body of the callback request you receive. Do not make any modifications. Below is an example.body="{\\n\\t\\"EventGroupId\\":\\t1,\\n\\t\\"EventType\\":\\t103,\\n\\t\\"CallbackTs\\":\\t1615554923704,\\n\\t\\"EventInfo\\":\\t{\\n\\t\\t\\"RoomId\\":\\t12345,\\n\\t\\t\\"EventTs\\":\\t1608441737,\\n\\t\\t\\"UserId\\":\\t\\"test\\",\\n\\t\\t\\"UniqueId\\":\\t1615554922656,\\n\\t\\t\\"Role\\":\\t20,\\n\\t\\t\\"Reason\\":\\t1\\n\\t}\\n}"

## Verify signature example

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
*Source: [https://trtc.io/document/54912](https://trtc.io/document/54912)*
