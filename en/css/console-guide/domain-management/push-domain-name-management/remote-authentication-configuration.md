# Remote Authentication Configuration

With remote authentication, after authenticating a push/playback request for hotlink protection, CSS will call your server API to send the request to your server so that you can determine whether the request is legitimate. Based on the result your server returns, CSS will approve or reject the push/playback request. This ensures more precise authentication and improves security. However, you need to develop your own authentication server.

## Workflow

Remote authentication works as follows:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7d79906564f711ee94c3525400d793d0.png)

| No | Description |
| --- | --- |
| 1 | A request is sent to CSS. |
| 2 | If remote authentication is enabled for the domain, CSS will process the request as specified and then send it to your authentication server. |
| 3 | Your authentication server returns the result. The HTTP status code 200 indicates that the request should be approved, while the code 403 indicates that the request should be rejected. To ensure the continuity of core business operations and prevent user requests from being incorrectly rejected due to authentication service errors, the system will allow all requests to proceed if the authentication server returns a status code other than 200 or 403. |
| 4 | CSS approves or rejects the request based on the result. |

## Prerequisites

- You have activated CSS and logged in to the [CSS console](https://console.tencentcloud.com/live/livestat).
- You have added a push domain.

## Configuring Remote Authentication

1. Log in to the CSS Console, and select [Domain Management](https://console.intl.cloud.tencent.com/live/domainmanage) on the left sidebar. Click the **push domain** you want to configure remote authentication for, or click on **Manage**on the right side to enter the Domain Management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0c93ddba2c8c11efa4f552540077de32.png)

2. Under the **Advanced Configuration** tab, find **Remote authentication**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9e9616b1ab2511f0b0045254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b2bb315aab2511f09710525400e889b2.png)

3. Click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/cf3c26bc64fc11ee94c3525400d793d0.png) to enable remote authentication and complete the following settings:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/22432a622c8c11ef97da5254007d9c55.png)

| Configuration Item |  | Description |
| --- | --- | --- |
| Authentication server address |  | The address of your authentication server (required). Format: http(s)://+Domain or IP address+Port+Path. |
| Request method |  | POST is selected by default. You can also use HEAD or GET. |
| URL authentication | Parameters to keep | All URL parameters are kept by default. You can also specify parameters to keep or remove all parameters.If you select **Keep specified parameters**, you need to enter the parameters to be retained in the input box. Chinese characters and spaces are not supported. Separate multiple parameters with "\|", for example: `value1\|value2`.Authentication parameters are case-sensitive; "key" and "KEY" are considered as two different parameters. |
|  | Custom parameters to add | Click **Add**, and the parameter type can be either **Select Parameter** or**Custom**. (Up to 50 parameters can be added)**Select Parameter** supports choosing host, uri, query, client_ip, and cdn_ip parameters.**host**: The push domain.**uri**: The original request URL.**client_ip**: The request client IP.**cdn_ip**: The request CDN-side IP.When you select **Custom**, you need to fill in the parameter and value fields. Chinese characters and spaces are not supported. Authentication parameters are case-sensitive; "key" and "KEY" are considered as two different parameters. |
| Timeout period (ms) per try |  | This is required. Enter a value between 500 and 3000. The default is 3000. |
| Max retries |  | Enter a value between 0 and 3. The default is 1. |
| Behavior upon timeout |  | This specifies whether to approve or reject a request if the system does not receive a response (HTTP status code 200 or 403) after the total timeout period elapses (Total timeout period = Timeout period per try × (Max retries + 1)). The default is **Approve**. You can also set it to **Reject**. |

4. Click **Save**.

> **Note:**The remote authentication configuration will take effect about 10 minutes after completion.

## Modifying Remote Authentication Settings

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the push domain you want to configure remote authentication for, or click on **Manage** on the right side to enter the Domain Management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/37c1a75c2c8c11ef97da5254007d9c55.png)

2. Under the **Advanced Configuration** tab, find **Remote authentication** and click Edit.
3. Modify the settings and click **Save**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3dea25f12c8c11efb0275254006c0558.png)

## Disabling Remote Authentication

1. Select [Domain Management](https://console.tencentcloud.com/live/domainmanage) on the left sidebar. Click the **push domain** you want to disable remote authentication for, or click **Manage**on the right to enter the Domain Management page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5974bb7e2c8c11ef918f52540005b090.png)

2. Under the **Advanced Configuration** tab, find **Remote authentication** and click ![](https://staticintl.cloudcachetci.com/cms/backend-cms/de123ae42c8a11ef9130525400bf8054.png) to disable remote authentication.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5ffd93e62c8c11efb8c45254005a8b94.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/57049](https://www.tencentcloud.com/document/product/267/57049)*
