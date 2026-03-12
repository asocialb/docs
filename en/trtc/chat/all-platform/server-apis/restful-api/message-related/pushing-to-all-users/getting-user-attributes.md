# Getting User Attributes

## Feature Overview

This API is used to obtain user attributes. To call this API, you must use the admin account. You can obtain a maximum of 100 usersâ attributes at a time. You need to [set app attribute names](https://intl.cloud.tencent.com/document/product/1047/37167) before calling the API.

## API Calling Description

Pushing to all users is available only to the Pro edition ãPro Plus editionãEnterprise editionn. To use it, you need to [purchase the Pro edition ãPro Plus editionãEnterprise editionn](https://www.tencentcloud.com/document/product/1047/34577), go to the [console](https://console.trtc.io/chat), choose **Feature Configuration** > **Login and Message** > **Push to all users**, and enable the feature.

### Sample request URL

```
https://xxxxxx/v4/all_member_push/im_get_attr?usersig=xxx&identifier=admin&sdkappid=88888888&random=99999999&contenttype=json
```

### Request parameters

| Parameter | Description |
| --- | --- |
| https | The request protocol is HTTPS and the request method is POST. |
| xxxxxx | Domain name corresponding to the country/region where your SDKAppID is located.China: `console.tim.qq.com`Singapore: `adminapisgp.im.qcloud.com`Seoul: `adminapikr.im.qcloud.com`Tokyoï¼`adminapijpn.im.qcloud.com`Frankfurt: `adminapiger.im.qcloud.com`Silicon Valley: `adminapiusa.im.qcloud.com`Jakarta:` adminapiidn.im.qcloud.com` |
| v4/all_member_push/im_get_attr | Request API |
| usersig | Signature generated in the app admin account. For more information, see [Generating UserSig](https://intl.cloud.tencent.com/document/product/1047/34385). |
| identifier | The app administration account. |
| sdkappid | `SDKAppID` assigned by the Chat console when an app is created |
| random | A random 32-bit unsigned integer |
| contenttype | The value is always `json`. |

### Maximum call frequency

100 times/second

### Sample request

```
{    "To_Account": [        "Zhang Xiaohong",        "Chen Xiaoming",        "abc"    ]}
```

### Request fields

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| To_Account | Array | Yes | List of target user accounts |

### Sample response

```
{    "ActionStatus": "OK",    "ErrorInfo": "",    "ErrorCode": 0,    "UserAttrs": [        {            "To_Account": "Zhang Xiaohong",            "Attrs": {                "sex" : "Female",                "city": "New York"            }        },        {            "To_Account": "abc",            "Attrs": {}        },        {            "To_Account": "Chen Xiaoming",            "Attrs": {                "sex": "M",                "city": "Shenzhen"            }        }    ]}
```

### Response fields

| Field | Type | Description |
| --- | --- | --- |
| ActionStatus | String | Request result. `OK`: Successful. `FAIL`: Failed |
| ErrorCode | Integer | Error code |
| ErrorInfo | String | Error information |
| UserAttrs | Array | List of user tags |
| To_Account | String | User account |
| Attrs | Object | Attribute content |

## Error Codes

Unless a network error (such as error 502) occurs, the HTTP return code for this API is always 200. `ErrorCode`**and**`ErrorInfo`**in the response represent the actual error code and error information.** For public error codes (60000 to 79999), please see [Error Codes](https://intl.cloud.tencent.com/document/product/1047/34348).
The following table describes the error codes specific to this API:

| Error Code | Description |
| --- | --- |
| 90001 | Failed to parse the JSON format. Check whether the JSON request meets JSON specifications. |
| 90018 | The number of requested accounts exceeds the limit. |
| 91000 | Internal service error. Try again. |

## API Debugging Tool

Use the [RESTful API online debugging tool](https://tcc.tencentcs.com/im-api-tool/index.html#/v4/all_member_push/im_get_attr) to debug this API.

## References

- [API for Pushing to All Users](https://intl.cloud.tencent.com/document/product/1047/37165)
- [Pushing to All Users](https://intl.cloud.tencent.com/document/product/1047/37166)
- [Setting Application Attribute Names](https://intl.cloud.tencent.com/document/product/1047/37167)
- [Getting Application Attribute Names](https://intl.cloud.tencent.com/document/product/1047/37168)
- [Setting User Attributes](https://intl.cloud.tencent.com/document/product/1047/37170)
- [Deleting User Attributes](https://intl.cloud.tencent.com/document/product/1047/37171)
- [Adding User Tags](https://intl.cloud.tencent.com/document/product/1047/37173)
- [Getting User Tags](https://intl.cloud.tencent.com/document/product/1047/37172)
- [Deleting User Tags](https://intl.cloud.tencent.com/document/product/1047/37174)
- [Deleting All Tags of a User](https://intl.cloud.tencent.com/document/product/1047/37175)


---
*Source: [https://trtc.io/document/37169](https://trtc.io/document/37169)*
