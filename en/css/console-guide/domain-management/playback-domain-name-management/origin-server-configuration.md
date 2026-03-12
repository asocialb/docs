# Origin Server Configuration

If you have a self-built origin server and live streaming source, CSS can pull streams from your origin server and distribute the content for you. This document describes how to configure origin server information for a playback domain in the CSS console.

## Limits

- Origin server configuration takes effect about one hour after configuration is complete.
- After configuring an origin server for a playback domain, you can no longer bind a push domain to the playback domain by specifying a `StreamName`. Nor can you configure watermarking, transcoding, recording, screenshot, or porn detection tasks for the playback domain.
- Upon completing the origin-pull configuration in the console, should you require to further set a whitelist for the service IP during Tencent Cloud Live's origin-pull process, please [submit a ticket](https://console.tencentcloud.com/workorder/category) to obtain the list of origin-pull IP ranges. Additionally, provide the relevant domain names (estimated usage) for backend assessment and configuration.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have built a live streaming origin server.
- You have added a **playback domain name**.

## Origin-Pull Configuration

You can edit a domain’s origin server information, including the basic information, protocol, and host in the console.

1. In the CSS console, select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the name of your **Playback Configuration** or click **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/559d32c8c8ed11ef81865254005ef0f7.png)

2. Beside **Domain Management**/**Domain**, click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/c4a96139d21d11eeb0d9525400461a83.png) to enable or disable **Origin server mode**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/abd73782558011ef8357525400bdab9d.png)

3. When the origin server mode is enabled, you may perform the origin-pull configuration based on your business requirements.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5ecb155ac8ee11efa2ff52540044a08e.png)

### Basic Configuration Description

#### Origin server information

| Origin Server Information | Description |
| --- | --- |
| Origin Server Type | Supports two types: Live Streaming Origin Server and StreamPackage. |
| Forwarding protocol | Supports RTMP, HTTP-FLV, and HLS protocols. |
| HTTPS | If the FLV or HLS protocol is used, you can enable HTTPS.If you enable HTTPS, port 443 will be used. Post-redirection HTTPS is also supported. There are no port restrictions. |
| Primary origin server | The address of the primary origin server, which can be an IP address or domain. You can also configure a backup origin server. The addresses will be polled. |
| Backup origin server | The address of the backup origin server (optional). |
| Origin server host header | By default, the origin server address is used as the Host header if it is not configured. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bcfaadc6c8ee11ef81865254005ef0f7.png)

##### Host header

If the FLV or HLS protocol is used, you can configure an HTTP host header that specifies the exact domain that CSS accesses when pulling from the origin server. If not configured, the origin address is used as the Host header by default.

##### Notes

The difference between an origin server address and a host header is as follows:

- An origin server address is the IP address an origin-pull request is sent to.
- A host header specifies the domain of the origin server address a request is sent to.

##### Configuration example

1. An origin server is configured for the playback domain `xx001.elementtest.org` as follows:
![](https://staticintl.cloudcachetci.com/cms/backend-cms/f8748b43558011efb927525400fdb830.png)
2. The process of pulling from the origin server would be as follows:
When the user accesses the resource by opening `http://xx001.elementtest.org/index.m3u8`, because the resource is not yet cached in Tencent Cloud, CSS will resolve the domain `test001.com` to get the server address of the origin server. Suppose it is `1.1.1.1`. CSS will access the `1.1.1.1` server, find the `index.m3u8` file in the web server `test002.com`, and then return the resource to the user.

### Remuxing

If the RTMP or HTTP-FLV protocol is used, you can enable HLS remuxing. Below are the formats of an RTMP, HTTP-FLV, and HLS address.

- RTMP: `rtmp://Playback domain/AppName/StreamName`
- FLV: `http://Playback domain/AppName/StreamName.flv`
- M3U8: `http://Playback domain/AppName/StreamName.m3u8`

#### Notes

- Number of HLS segments: Three by default. Value range: 3 - 10.
- HLS segment size: Three seconds by default. Value range: 3 - 10. The actual segments generated will not be smaller than the GOP size.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/04bb06e2c8ef11efb1a552540099c741.png)

### HTTP configuration

When the origin-pull protocol is HLS, you may configure the

**HTTP settings**

. Based on your business requirements, click

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3fec55a2558111ef8f105254002693fd.png)

to enable the corresponding features.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7f61d07bc8ef11ef9d3a5254001c06ec.png)

| Item | Description |
| --- | --- |
| Redirection | If you enable this, Tencent Cloud will not cache the 301 or 302 status code. When 301 or 302 is returned by the origin server, Tencent Cloud will automatically redirect until it obtains the requested resource (max 10 redirects) and return the resource to the user. No redirects are needed on the user end.If you disable redirection, Tencent Cloud will return the 301 or 302 status code to the user end, which will redirect to get the resource. |
| Pass-through of origin server URL parameters | By default, URL parameters are not passed through. If you enable this, parameters may be added to the URL without performing URL encoding or decoding. |
| HTTP request header pass-through | By default, HTTP request headers are not passed through. You can enable this to pass through the headers. Duplicate headers (case-insensitive) are not supported currently. |
| HTTP response header pass-through | By default, HTTP response headers are not passed through. You can enable this to pass through the headers. Duplicate headers (case-sensitive) are supported currently. |
| OPTIONS request | By default, GET request is supported, and Option request is supported after enabling it. |
| [Custom Origin-pull Request Header](https://www.tencentcloud.com/document/product/267/35070#bf7c2c67-4483-4b83-b9c8-298aa78760e2) | When performing the origin-pull request, add the required headers to carry the client IP, port, label, etc.By default, the index request header is selected for the configuration item, with support for switching to the slice request header.Header parameter: It consists of uppercase and lowercase letters, numbers, and hyphens (-), with a length supported of 1-100 characters and no spaces allowed.Header value: Chinese characters are not supported, and it cannot start with $, with a length supported of 1-100 characters and no spaces allowed.By default, the system enables synchronization options, and automatically synchronizes index and slice request header configurations when a single addition is made.Adding multiple entries is supported, with a maximum of 10 custom origin-pull request headers for index and slice respectively. |

#### Custom Origin-pull Request Header **Configuration**

1. **Add the Custom Origin-pull Request Header**
  1.1. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb26d140558111efb927525400fdb830.png) to turn on the Custom Origin-pull Request Header switch and add the custom origin-pull request header configuration.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb27030a558111efb66652540055f650.png)

  1.2. After completing the configuration, click  **Confirm**  to finish the creation.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb28660d558111ef9bf1525400a9236a.png)

  1.3. After creation, click  **Save** . The configuration will take some time to take effect.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb1613e2558111ef8f105254002693fd.png)

2. **Modify the Custom Origin-pull Request Header**

> **Note:**After deleting the custom origin-pull request header, the configuration will no longer be effective. Operate with care.

  2.1. Based on your business requirements, you can click  **Edit**  to modify, add, or delete the configured custom origin-pull request header.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb26bcce558111ef8357525400bdab9d.png)

  2.2. Click  **Add**  to continue adding multiple entries. A maximum of 10 custom origin-pull request headers can be configured.
  2.3. Click  **Modify**  to modify the configured custom origin-pull request header.
  2.4. Click  **Delete**  to delete the configured custom origin-pull request header. Once all custom origin-pull request header configurations are deleted, click  **Save** . The system will automatically disable the custom origin-pull request header configuration feature.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fb20ddba558111ef9bf1525400a9236a.png)

### Cache configuration

If the HLS protocol is used, you can configure the resource cache time. After Tencent Cloud obtains the requested resource successfully from the origin server (status code 200), it will cache the index file and segments as configured.

| Item | Description |
| --- | --- |
| Index file cache time | The time to cache the index file when the origin server returns the 200 status code. The default cache time is 1,000 ms. The maximum time that can be set is 60,000 ms. |
| Segment cache time | The time to cache the TS/M4S/MP4 segments when the origin server returns the 200 status code. The default cache time is 1,000 ms. The maximum time that can be set is 60,000 ms. |
| Cache time by status code | According to the status code corresponding to the configured cache, if the same request is received within the cache time, there is no need to visit the origin server, and the status code can be returned directly. The default cache time is 1s.When the origin server returns a non-200 status code, if it is unable to handle it immediately, and you don’t want to pass through all subsequent requests to the origin server, you can cache the status code and return it directly to the user. This can reduce the load on the origin server.Currently, the following status codes can be cached, regardless of the file type:4XX: 400, 403, 404, 4055XX: 500, 503, 504 |
| Cache key rule configuration | For the cache key rule configuration, retain the parameters that have an impact on the resource content as the cache key, convert a category of requests for the same resource into a unified cache key and hit the same cache to improve the hit rate.**File Type**Choose file types. There are options of index or shard, Index is selected by default.**Retain specified parameters**Only English, characters and numbers can be entered. Multiple parameters are separated by ";".Up to 30 groups of parameters are supported. Each parameter name should not exceed 20 characters.If a parameter is specified, even if the parameter does not have a value, it will be cached separately from the parameters with the same name that have value.**Note:**You must enable the origin-pull URL parameter passthrough in [HTTP settings](https://www.tencentcloud.com/document/product/267/35070#http-configuration) before configuring the cache key rules. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ecab6c5ad21f11eea2b0525400bb593a.png)

### URL rewriting

If the HLS protocol is used, you can configure URL rewriting.

Tencent Cloud allows you to rewrite the actual URL CSS pulls from to a URL that better matches your origin server. Currently, you can only rewrite the URL path.

#### Notes

- **Original URL**: Requests are matched by prefix. For example, if you enter `/test01`, the rewriting rule will be applied to all requests under `/test01`. Regular expressions are not supported currently.
- **Target URL**: Requests are matched by prefix. For example, if you enter `/test01/test02`, all requests under `/test` will be rewritten to `/test01/test02`. Regular expressions are not supported currently.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0cfffe2ad22011ee89c5525400170219.png)

#### Limits

- You can configure at most 10 rewriting rules for each playback domain.
- Spaces and the following special characters are not supported: < > " # { } | \\ ^ ~ [ ] `
- You can re-arrange the rules to adjust their priorities. Rules at the top have higher priorities.

### Others

| Item | Description |
| --- | --- |
| Connection timeout | The timeout period for establishing a TCP connection. The default time is 10,000 ms, and the value range is 2000-60000 (ms).Please set the timeout period according to your origin server conditions and network conditions. If the timeout period is too short, when a pull request fails due to network issues, CSS may switch origin servers too frequently. If the timeout period is too long, CSS may wait a long time before it tries a different origin server, causing playback failure at the client end. |
| Max retries | The maximum number of retry attempts. If multiple origin server addresses have been configured, when a request fails, CSS will try a different address.Value range: 1 - 10. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/15ea9676d22011eeb0d9525400461a83.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/35070](https://www.tencentcloud.com/document/product/267/35070)*
