# HTTP Response Header Configuration

You can use HTTP headers to define fields that carry information about HTTP transactions. Header fields work on the domain level. This means the header fields you configure will take effect for all responses under your domain.

## Prerequisites

- You have logged in to the [CSS console](https://console.tencentcloud.com/live).
- You have added a [playback domain name](https://intl.cloud.tencent.com/document/product/267/35970).

## Use Limits

- You cannot add two fields with the same name. To specify multiple values for a field, use this format: `value 1, value 2, value 3`.
- If a field you configure is the same as a field used by the CSS backend, you will be asked to modify it.
- A custom field can be 1-100 characters long and can contain letters, numbers, and hyphens (-).
- The value of a field cannot be empty. It can be 1-1,000 characters long and cannot contain Chinese characters.

## Configuring HTTP Response Header

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click the name of your **playback domain** or click **Manage** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/599633fb142811ef83585254007bbd8c.png)

2. Select the **Advanced Configuration** tab.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/15ccff3bcc0d11f08e74525400bf7822.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/25569110cc0d11f084a45254005ef0f7.png)

3. In the  **HTTP response headers**  area, click  **Edit**  to add new header fields or modify/delete existing header fields.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ba2c49f1cc0d11f093295254001c06ec.png)

To add a header field, click  **New** :

  - Select **Preset** to add a preset field: `Access-Control-Allow-Methods`, `Access-Control-Max-Age`, or `Access-Control-Expose-Headers`.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e3205a7ccc0d11f08e74525400bf7822.png)

| Field | Description |
| --- | --- |
| Access-Control-Allow-Methods | Indicates which HTTP methods are allowed for cross-origin requests. You can specify multiple methods at a time: Access-Control-Allow-Methods: POST, GET, OPTIONS. |
| Access-Control-Max-Age | Indicates how long (seconds) the results of a preflight request can be cached |
| Access-Control-Expose-Headers | Indicates which headers can be exposed to clients as part of the response |

  - Select **Custom** to add a custom field.

> **Note:**The name of a custom field can be 1-100 characters long and can contain letters, numbers, and hyphens. The value of a custom field can be 1-1,000 characters long and cannot contain Chinese characters.The system has default support for the header parameter Access-Control-Allow-Origin, which is used to enable cross-domain requests without the need for customization. There are two specific scenarios:When the request header does not include Origin, the returned header will be 'Access-Control-Allow-Origin: *'.When the request header includes 'Origin: ${Origin}', the returned header will be 'Access-Control-Allow-Origin: ${Origin}'. For example, when the request header has Origin: https://cloud.tencent.com, the returned header will be Access-Control-Allow-Origin: https://cloud.tencent.com.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/84a75d96cc0e11f0ae4f52540099c741.png)

4. When you are finished, Click **OK**. Your configuration may be in one of three statuses: yet to take effect, failed, or effective.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ca4f8494cc0e11f096d1525400e889b2.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/e463ac72cc0e11f0afdc52540044a08e.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/48358](https://www.tencentcloud.com/document/product/267/48358)*
