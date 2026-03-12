# Error Codes

## Feature Description

If there is an Error field in the response, it means that the API call failed. For example:

```
 {
    "Response": {
        "Error": {
            "Code": "AuthFailure.SignatureFailure",
            "Message": "The provided credentials could not be validated. Please check your signature is correct."
        },
        "RequestId": "ed93f3cb-f35e-473f-b9f3-0d451b8b79c6"
    }
}
```

Code in Error indicates the error code, and Message indicates the specific information of the error.

## Error Code List

### Common Error Codes

| Error Code | Description |
| --- | --- |
| ActionOffline | This API has been deprecated. |
| AuthFailure.InvalidAuthorization | `Authorization` in the request header is invalid. |
| AuthFailure.InvalidSecretId | Invalid key (not a TencentCloud API key type). |
| AuthFailure.MFAFailure | MFA failed. |
| AuthFailure.SecretIdNotFound | Key does not exist. Check if the key has been deleted or disabled in the console, and if not, check if the key is correctly entered. Note that whitespaces should not exist before or after the key. |
| AuthFailure.SignatureExpire | Signature expired. Timestamp and server time cannot differ by more than five minutes. Please ensure your current local time matches the standard time. |
| AuthFailure.SignatureFailure | Invalid signature. Signature calculation error. Please ensure youâve followed the signature calculation process described in the Signature API documentation. |
| AuthFailure.TokenFailure | Token error. |
| AuthFailure.UnauthorizedOperation | The request is not authorized. For more information, see the [CAM](https://intl.cloud.tencent.com/document/product/598) documentation. |
| DryRunOperation | DryRun Operation. It means that the request would have succeeded, but the DryRun parameter was used. |
| FailedOperation | Operation failed. |
| InternalError | Internal error. |
| InvalidAction | The API does not exist. |
| InvalidParameter | Incorrect parameter. |
| InvalidParameterValue | Invalid parameter value. |
| InvalidRequest | The multipart format of the request body is incorrect. |
| IpInBlacklist | Your IP is in uin IP blacklist. |
| IpNotInWhitelist | Your IP is not in uin IP whitelist. |
| LimitExceeded | Quota limit exceeded. |
| MissingParameter | A parameter is missing. |
| NoSuchProduct | The product does not exist. |
| NoSuchVersion | The API version does not exist. |
| RequestLimitExceeded | The number of requests exceeds the frequency limit. |
| RequestLimitExceeded.GlobalRegionUinLimitExceeded | Uin exceeds the frequency limit. |
| RequestLimitExceeded.IPLimitExceeded | The number of ip requests exceeds the frequency limit. |
| RequestLimitExceeded.UinLimitExceeded | The number of uin requests exceeds the frequency limit. |
| RequestSizeLimitExceeded | The request size exceeds the upper limit. |
| ResourceInUse | Resource is in use. |
| ResourceInsufficient | Insufficient resource. |
| ResourceNotFound | The resource does not exist. |
| ResourceUnavailable | Resource is unavailable. |
| ResponseSizeLimitExceeded | The response size exceeds the upper limit. |
| ServiceUnavailable | Service is unavailable now. |
| UnauthorizedOperation | Unauthorized operation. |
| UnknownParameter | Unknown parameter. |
| UnsupportedOperation | Unsupported operation. |
| UnsupportedProtocol | HTTP(S) request protocol error; only GET and POST requests are supported. |
| UnsupportedRegion | API does not support the requested region. |

### Service Error Codes

| Error Code | Description |
| --- | --- |
| AuthFailure | CAM signature/authentication error. |
| AuthFailure.UnRealNameAuthenticated | Identity verification has not been completed, so this operation is not allowed. |
| AuthFailure.UnsupportedOperation | Unsupported operation. |
| FailedOperation.CRUnsupportMethod | Unsupported on-cloud recording method. |
| FailedOperation.CSUnsupportMethod | The cloud slicing method is not supported. |
| FailedOperation.NotAbility | Need to unlock the required ability |
| FailedOperation.NotAllowed | This operation is not allowed, please submit a ticket to contact us |
| FailedOperation.NotRtmpFunction | RTMP is not enabled. |
| FailedOperation.QueryTaskInfoFailed | Query task failed |
| FailedOperation.RestrictedConcurrency | Maximum number of concurrent on-cloud recording tasks reached. Contact us to raise the limit. |
| FailedOperation.RoomNotExist | The room does not exist. |
| FailedOperation.SdkAppIdNotExist | The application ID does not exist. |
| FailedOperation.SdkAppIdNotUnderAppId | There is no resource for this SdkAppId  In this AppId |
| FailedOperation.TaskExist | Task already exists |
| FailedOperation.TaskFinished | Task has ended when calling the interface. |
| FailedOperation.TaskNotExist | The run does not exist or is stopped. |
| FailedOperation.UserNotExist | The user is not in the room. |
| InternalError.CRInternalError | On-cloud recording internal error. |
| InternalError.CSInternalError | Internal service error of cloud slicing occurs. |
| InternalError.DBError | An error occurred while querying the database. |
| InternalError.EsQueryError | An error occurred during an ES query. |
| InternalError.GetRoomCacheIpError | Failed to query the room. |
| InternalError.GetRoomFromCacheError | Failed to get room information. |
| InternalError.HttpParaseFalied | Failed to parse the HTTP request. |
| InternalError.HttpParseFailed | HTTP request parsing failed. |
| InternalError.InterfaceErr | API error. |
| InternalError.InternalError | Internal error, please retry. |
| InternalError.MethodErr | Unsupported method. |
| InternalError.UserNotExist | The user is not in the room. |
| InvalidParameter.BodyParamsError | Failed to parse body parameters. |
| InvalidParameter.EncodeParams | Invalid `EncodeParams`. |
| InvalidParameter.EndTs | Invalid `EndTs`. |
| InvalidParameter.OutOfRange | Parameter value is out of range. |
| InvalidParameter.PageNumber | Invalid `PageNumber`. |
| InvalidParameter.PageSize | Invalid `PageSize`. |
| InvalidParameter.PageSizeOversize | The value of `PageSize` exceeds 100. |
| InvalidParameter.QueryScaleOversize | The query period exceeds the limit. |
| InvalidParameter.RoomId | `RoomId` is incorrect. |
| InvalidParameter.SdkAppId | `SdkAppId` is incorrect. |
| InvalidParameter.SdkAppid | Inoperable `SdkAppid`. |
| InvalidParameter.StartTimeExpire | The start time for query exceeded the limit. |
| InvalidParameter.StartTimeOversize | The query start time exceeds the range allowed by the current dashboard edition. For details, see https://intl.cloud.tencent.com/document/product/647/81331?from_cn_redirect=1 |
| InvalidParameter.StartTs | Invalid `StartTs`. |
| InvalidParameter.StartTsOversize | The start time for query exceeded the limit. |
| InvalidParameter.StrRoomId | StrRoomId parameter error. |
| InvalidParameter.StreamUrl | Invalid StreamUrl format |
| InvalidParameter.TaskId | TaskId parameter error. |
| InvalidParameter.UrlParamsError | Failed to parse URL parameters. |
| InvalidParameter.UserId | Invalid `UserId`. |
| InvalidParameter.UserIds | `UserIds` is incorrect. |
| InvalidParameter.UserIdsMorethanSix | The number of users exceeds 6. |
| InvalidParameter.UserSig | UserSig is expired or wrong |
| InvalidParameter.UserSigNotAdmin | UserSig is not a super administrator. |
| InvalidParameterValue.RoomId | Invalid RoomId. |
| MissingParameter.AccessKey | `AccessKey` parameter missing. |
| MissingParameter.AppId | `AppId` missing. |
| MissingParameter.Bucket | `Bucket` parameter missing. |
| MissingParameter.CloudStorage | `CloudStorage` parameter missing. |
| MissingParameter.CommId | `CommId` is missing. |
| MissingParameter.CommIdOrSdkAppId | `SdkAppId` or `CommID` missing. |
| MissingParameter.EndTs | `endTS_s` is missing. |
| MissingParameter.RecordMode | `RecordMode` parameter missing. |
| MissingParameter.RecordParams | `RecordParams` parameter missing. |
| MissingParameter.Region | `Region` parameter missing. |
| MissingParameter.RoomId | `RoomId` is missing. |
| MissingParameter.RoomNum | `RoomNum` is missing. |
| MissingParameter.SdkAppId | `SdkAppId` is missing. |
| MissingParameter.SecretKey | `SecretKey` parameter missing. |
| MissingParameter.SliceParams | The SliceParams parameter is required. |
| MissingParameter.SliceStorageParams | The SliceStorageParams parameter is required. |
| MissingParameter.SliceType | The SliceType parameter is required. |
| MissingParameter.StartTs | `startTS_s` is missing. |
| MissingParameter.StorageParams | `StorageParams` parameter missing. |
| MissingParameter.StreamType | `StreamType` parameter missing. |
| MissingParameter.TaskId | `TaskId` parameter missing. |
| MissingParameter.UserId | Missing `UserId` parameter. |
| MissingParameter.UserIds | `UserIds` is missing. |
| MissingParameter.UserSig | `UserSig` parameter missing. |
| MissingParameter.Vendor | `Vendor` parameter missing. |
| ResourceInsufficient.RequestRejection | Insufficient resources. |
| UnauthorizedOperation.SdkAppId | No permission to manipulate `SdkAppId`. |


---
*Source: [https://trtc.io/document/34270](https://trtc.io/document/34270)*
