# Request Structure

## 1. Service Address

The API supports access from either a nearby region (at mps.intl.tencentcloudapi.com) or a specified region (at mps.ap-guangzhou.tencentcloudapi.com for Guangzhou, for example).

We recommend using the domain name to access the nearest server. When you call an API, the request is automatically resolved to a server in the region **nearest** to the location where the API is initiated. For example, when you initiate an API request in Guangzhou, this domain name is automatically resolved to a Guangzhou server, the result is the same as that of specifying the region in the domain like "mps.ap-guangzhou.tencentcloudapi.com".

**Note: For latency-sensitive businesses, we recommend that you specify the region in the domain name.**

Tencent Cloud currently supports the following regions:

| Hosted region | Domain name |
| --- | --- |
| Local access region (recommended, only for non-financial availability zones) | mps.intl.tencentcloudapi.com |
| South China (Guangzhou) | mps.ap-guangzhou.tencentcloudapi.com |
| East China (Shanghai) | mps.ap-shanghai.tencentcloudapi.com |
| East China (Nanjing) | mps.ap-nanjing.tencentcloudapi.com |
| North China (Beijing) | mps.ap-beijing.tencentcloudapi.com |
| Southwest China (Chengdu) | mps.ap-chengdu.tencentcloudapi.com |
| Southwest China (Chongqing) | mps.ap-chongqing.tencentcloudapi.com |
| Hong Kong, Macao, Taiwan (Hong Kong, China) | mps.ap-hongkong.tencentcloudapi.com |
| Southeast Asia (Singapore) | mps.ap-singapore.tencentcloudapi.com |
| Southeast Asia (Jakarta) | mps.ap-jakarta.tencentcloudapi.com |
| Southeast Asia (Bangkok) | mps.ap-bangkok.tencentcloudapi.com |
| Northeast Asia (Seoul) | mps.ap-seoul.tencentcloudapi.com |
| Northeast Asia (Tokyo) | mps.ap-tokyo.tencentcloudapi.com |
| U.S. East Coast (Virginia) | mps.na-ashburn.tencentcloudapi.com |
| U.S. West Coast (Silicon Valley) | mps.na-siliconvalley.tencentcloudapi.com |
| South America (São Paulo) | mps.sa-saopaulo.tencentcloudapi.com |
| Europe (Frankfurt) | mps.eu-frankfurt.tencentcloudapi.com |

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
*Source: [https://www.tencentcloud.com/document/product/1041/33627](https://www.tencentcloud.com/document/product/1041/33627)*
