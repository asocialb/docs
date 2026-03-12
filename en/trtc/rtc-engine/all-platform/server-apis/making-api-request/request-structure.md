# Request Structure

## 1. Service Address

The API supports access from either a nearby region (at trtc.intl.tencentcloudapi.com) or a specified region (at trtc.ap-guangzhou.tencentcloudapi.com for Guangzhou, for example).

We recommend using the domain name to access the nearest server. When you call an API, the request is automatically resolved to a server in the region **nearest** to the location where the API is initiated. For example, when you initiate an API request in Guangzhou, this domain name is automatically resolved to a Guangzhou server, the result is the same as that of specifying the region in the domain like "trtc.ap-guangzhou.tencentcloudapi.com".

**Note: For latency-sensitive businesses, we recommend that you specify the region in the domain name.**

Tencent Cloud currently supports the following regions:

| Hosted region | Domain name |
| --- | --- |
| Local access region (recommended, only for non-financial availability zones) | trtc.intl.tencentcloudapi.com |
| South China (Guangzhou) | trtc.ap-guangzhou.tencentcloudapi.com |
| East China (Shanghai) | trtc.ap-shanghai.tencentcloudapi.com |
| East China (Nanjing) | trtc.ap-nanjing.tencentcloudapi.com |
| North China (Beijing) | trtc.ap-beijing.tencentcloudapi.com |
| Southwest China (Chengdu) | trtc.ap-chengdu.tencentcloudapi.com |
| Southwest China (Chongqing) | trtc.ap-chongqing.tencentcloudapi.com |
| Hong Kong, Macao, Taiwan (Hong Kong, China) | trtc.ap-hongkong.tencentcloudapi.com |
| Southeast Asia (Singapore) | trtc.ap-singapore.tencentcloudapi.com |
| Southeast Asia (Jakarta) | trtc.ap-jakarta.tencentcloudapi.com |
| Southeast Asia (Bangkok) | trtc.ap-bangkok.tencentcloudapi.com |
| Northeast Asia (Seoul) | trtc.ap-seoul.tencentcloudapi.com |
| Northeast Asia (Tokyo) | trtc.ap-tokyo.tencentcloudapi.com |
| U.S. East Coast (Virginia) | trtc.na-ashburn.tencentcloudapi.com |
| U.S. West Coast (Silicon Valley) | trtc.na-siliconvalley.tencentcloudapi.com |
| South America (SÃ£o Paulo) | trtc.sa-saopaulo.tencentcloudapi.com |
| Europe (Frankfurt) | trtc.eu-frankfurt.tencentcloudapi.com |

## 2. Communications Protocol

All the Tencent Cloud APIs communicate via HTTPS, providing highly secure communication tunnels.

## 3. Request Methods

Supported HTTP request methods:

POST (recommended)
GET

The Content-Type types supported by POST requests:

application/json (recommended). The TC3-HMAC-SHA256 signature algorithm must be used.
application/x-www-form-urlencoded. The HmacSHA1 or HmacSHA256 signature algorithm must be used.
multipart/form-data (only supported by certain APIs). You must use TC3-HMAC-SHA256 to calculate the signature.

The size of a GET request packet is up to 32 KB. The size of a POST request is up to 1 MB when the HmacSHA1 or HmacSHA256 signature algorithm is used, and up to 10 MB when TC3-HMAC-SHA256 is used.

## 4. Character Encoding

Only UTF-8 encoding is used.


---
*Source: [https://trtc.io/document/34262](https://trtc.io/document/34262)*
