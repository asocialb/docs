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
| AuthFailure.SignatureFailure | Invalid signature. Signature calculation error. Please ensure you’ve followed the signature calculation process described in the Signature API documentation. |
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
| FailedOperation.AiTranscodeOptionFail | Failed to manipulate the AI API. |
| FailedOperation.AlterTaskState | Failed to change the task status. |
| FailedOperation.AuthError | You do not have permission to perform this operation. |
| FailedOperation.CallOtherSvrError | Failed to call the third-party service. |
| FailedOperation.CallOtherSvrFailed | Failed to call the internal service. |
| FailedOperation.CancelSessionNotExist | The canceled stream mix session does not exist. |
| FailedOperation.CannotBeDeletedIssued | Failed to delete the certificate because it has been issued. |
| FailedOperation.CannotBeDeletedWithinHour | Free certificates cannot be deleted within one hour of application. |
| FailedOperation.CertificateExists | The certificate already exists. |
| FailedOperation.CertificateInvalid | The certificate is invalid. |
| FailedOperation.CertificateMismatch | The certificate and the private key do not match. |
| FailedOperation.CertificateNotFound | The certificate does not exist. |
| FailedOperation.ConfInUsed | The template is in use. |
| FailedOperation.ConfigCDNFailed | CDN configuration failed. |
| FailedOperation.CosBucketNotExist | The COS bucket does not exist. |
| FailedOperation.CosBucketNotPermission | You don’t have permission to access the COS bucket. |
| FailedOperation.CosRoleNotExists | The COS role does not exist. Please go to the “Feature Configuration > Live Screencapture & Porn Detection” page of the CSS console to grant the permission. |
| FailedOperation.DeleteDomainInLockedTime | The domain name cannot be deleted because it incurred traffic in the last 2 days and is in locked state. |
| FailedOperation.DomainAdded | The domain has already been added. |
| FailedOperation.DomainGslbFail | Failed to configure the domain rule. |
| FailedOperation.DomainNeedRealName | The domain has not been verified. |
| FailedOperation.DomainNeedVerifyOwner | The ownership of the domain has not been verified. |
| FailedOperation.ExceedsFreeLimit | The number of free certificates exceeded the limit. |
| FailedOperation.GetPictureUrlError | Unable to get the watermark URL. |
| FailedOperation.GetStreamResolutionError | Failed to get the input stream length and width. |
| FailedOperation.HasNotLivingStream | No live stream. |
| FailedOperation.HostOutLimit | The number of domain names exceeded the upper limit (100). |
| FailedOperation.InvalidCertificateStatusCode | Invalid certificate status. |
| FailedOperation.InvalidParam | Invalid parameter. |
| FailedOperation.InvokeVideoApiFail | An exception occurred while manipulating the VOD API. |
| FailedOperation.JiFeiNoEnoughFund | The billing platform returned an error of insufficient balance. |
| FailedOperation.NetworkError | The CA system is busy. Try again later. |
| FailedOperation.NoProjectPermission | You do not have permission to operate this project. |
| FailedOperation.NoRealNameAuth | You haven’t completed identity verification. |
| FailedOperation.NotFound | No records found. |
| FailedOperation.ParentDomainAdded | The domain’s parent domain has already been added. |
| FailedOperation.ProcessMixError | Failed to start stream mix. |
| FailedOperation.QueryUploadInfoFailed | Failed to query the upload information. |
| FailedOperation.RuleAlreadyExist | The rule already exists. |
| FailedOperation.SdkNoPackage | The user has no valid traffic package. |
| FailedOperation.StreamNotExist | The stream does not exist. |
| FailedOperation.SubDomainAdded | The domain’s subdomain has already been added. |
| FailedOperation.TagUnbindError | Failed to unbind the tag. Try unbinding it manually. |
| InternalError.ArgsNotMatch | For the transcoding template adding API. |
| InternalError.CallOtherSvrError | Error calling internal service. |
| InternalError.ChineseCharacterDetected | Chinese domain names are not supported currently. Please check the domain name format. |
| InternalError.ConfInUsed | The template is in use. |
| InternalError.ConfNotFound | The template does not exist. |
| InternalError.ConfOutLimit | The number of templates exceeded the limit. |
| InternalError.ConfigNotExist | The configuration does not exist. |
| InternalError.ConnectDbError | Database connection error. |
| InternalError.CrtDateInUsing | The certificate is in use. |
| InternalError.CrtDateNotFound | The certificate does not exist. |
| InternalError.CrtDateNotLegal | The certificate is invalid. |
| InternalError.CrtDateOverdue | The certificate has expired. |
| InternalError.CrtDomainNotFound | There is no related domain name. |
| InternalError.CrtKeyNotMatch | The certificate key does not match. |
| InternalError.DBError | DB execution error. |
| InternalError.DomainAlreadyExist | The domain name is already connected elsewhere. Please check whether the entered domain name is correct, and if yes, you can add it again after successful ownership verification. |
| InternalError.DomainFormatError | The domain name format is incorrect. Please enter a valid one. |
| InternalError.DomainGslbFail | Failed to add the GSLB rule. |
| InternalError.DomainIsFamous | The domain name is already connected elsewhere. Please check whether the entered domain name is correct, and if yes, you can add it again after successful ownership verification. |
| InternalError.DomainIsLimited | Your domain name is unavailable. Please enter a correct domain name. |
| InternalError.DomainNoRecord | The domain name has no ICP filing. |
| InternalError.DomainNotExist | The domain name does not exist. |
| InternalError.DomainTooLong | The domain name length exceeds the limit. |
| InternalError.GetBizidError | Error getting user account. |
| InternalError.GetConfigError | Error getting the configuration. |
| InternalError.GetStreamInfoError | Failed to get the stream information. |
| InternalError.GetUpstreamInfoError | Error getting the live stream source information. |
| InternalError.GetWatermarkError | An error occurred while getting the watermark. |
| InternalError.HasNotLivingStream | No live stream. |
| InternalError.InvalidInput | Parameter check failed. |
| InternalError.InvalidRequest | Invalid request. |
| InternalError.InvalidUser | Account information error. |
| InternalError.JiFeiOtherError | The billing platform returned other errors. |
| InternalError.NetworkError | Internal network error. |
| InternalError.NotFound | The record does not exist. |
| InternalError.NotPermmitOperat | No permission to operate. |
| InternalError.PlayDomainNoRecord | The playback domain name does not exist. |
| InternalError.ProcessorAlreadyExist | The transcoding template name already exists. |
| InternalError.PushDomainNoRecord | The push domain name does not exist. |
| InternalError.QueryProIspPlayInfoError | Failed to query the playback information by ISP and district. |
| InternalError.QueryUploadInfoFailed | Failed to query the upload information. |
| InternalError.RuleAlreadyExist | The rule has already been configured. |
| InternalError.RuleInUsing | The rule is in use. |
| InternalError.RuleNotFound | The rule does not exist. |
| InternalError.RuleOutLimit | The rule exceeds the limit. |
| InternalError.StreamStatusError | Exceptional stream status. |
| InternalError.SystemError | Internal system error. |
| InternalError.UpdateDataError | Failed to update data. |
| InternalError.WatermarkAddError | Failed to add the watermark. |
| InternalError.WatermarkEditError | An internal error occurred while modifying the watermark. |
| InternalError.WatermarkNotExist | The watermark does not exist. |
| InvalidParameter.ArgsNotMatch | Incorrect template name. |
| InvalidParameter.COSCustomFileNameError | Incorrect custom COS filename. |
| InvalidParameter.CancelSessionNotExist | The canceled session does not exist. |
| InvalidParameter.CloudCrtIdError | Incorrect Tencent Cloud-hosted certificate ID. |
| InvalidParameter.CloudDomainIsStop | The gifted Tencent Cloud domain name has expired. |
| InvalidParameter.ConfInUsed | Template is in use. |
| InvalidParameter.ConfNotFound | Configuration not found. |
| InvalidParameter.CrtDateInUsing | The certificate is in use. |
| InvalidParameter.CrtDateNotFound | The certificate does not exist. |
| InvalidParameter.CrtDateNotLegal | The certificate is invalid. |
| InvalidParameter.CrtDateOverdue | The certificate has expired. |
| InvalidParameter.CrtDomainNotFound | Unable to find the domain. |
| InvalidParameter.CrtKeyNotMatch | The certificate key does not match. |
| InvalidParameter.CrtOrKeyNotExist | The certificate content or private key was not provided. |
| InvalidParameter.DomainAlreadyExist | The domain name already exists. |
| InvalidParameter.DomainFormatError | The domain name format is incorrect. Please enter a valid one. |
| InvalidParameter.DomainHitBlackList | This domain name is on the blocklist. |
| InvalidParameter.DomainIsFamous | A blocklisted domain name is used. |
| InvalidParameter.DomainIsLimited | The domain name is restricted. Please submit a ticket for application to remove the restrictions. |
| InvalidParameter.DomainTooLong | The domain name exceeds the length limit. |
| InvalidParameter.GopMustEqualAndExists | The GOP of an adaptive bitrate template is required and must be the same for each stream. |
| InvalidParameter.InputNumLimitExceeded | The number of inputs exceeds the limit. |
| InvalidParameter.InvalidBackgroudResolution | Invalid background length and width. |
| InvalidParameter.InvalidBackupToUrl | invalid BackupToUrl. |
| InvalidParameter.InvalidBitrate | Invalid output bitrate. |
| InvalidParameter.InvalidCallbackUrl | Invalid callback URL. |
| InvalidParameter.InvalidCropParam | The cropped area overflows the original image. |
| InvalidParameter.InvalidLayerParam | Invalid layer parameter. |
| InvalidParameter.InvalidMixInputParam | Invalid input parameters for stream mixing. |
| InvalidParameter.InvalidOutputParam | Invalid output stream parameters. |
| InvalidParameter.InvalidOutputStreamID | The output stream ID is already used. |
| InvalidParameter.InvalidOutputType | Invalid output type. Please check whether `OutputPram-StreamId` and `OutputType` match. |
| InvalidParameter.InvalidPictureID | The watermark ID was not set. |
| InvalidParameter.InvalidRoundRectRadius | Invalid corner radius of the rounded rectangle. |
| InvalidParameter.InvalidSourceUrl | Invalid source URL. |
| InvalidParameter.InvalidTaskTime | The time period of the task exceeded the limit. |
| InvalidParameter.InvalidToUrl | Invalid destination URL. |
| InvalidParameter.InvalidVodFileName | Incorrect `VodFileName`. |
| InvalidParameter.InvalidWatermark | Invalid watermark parameter. |
| InvalidParameter.MpHostDelete | It is not allowed to add a Mini Program domain name deleted in the same month. |
| InvalidParameter.MpPluginNoUse | The WeChat Mini Program plug-in is unauthorized. |
| InvalidParameter.OtherError | Other errors. |
| InvalidParameter.ProcessorAlreadyExist | Transcoding template already exists. |
| InvalidParameter.RuleNotFound | Rule not found. |
| InvalidParameter.SessionOutputStreamChanged | The output stream of the same session has changed. |
| InvalidParameter.TaskNotExist | The task does not exist. |
| InvalidParameter.TaskNumMoreThanLimit | The number of tasks reached the limit. |
| InvalidParameter.TemplateNotMatchInputNum | The template does not match the number of input streams. |
| InvalidParameter.ToUrlNoPermission | No permission to access the external URL. |
| InvalidParameter.UrlNotSafe | Failed to resolve the domain name. |
| LimitExceeded.MaximumRunningTask | The current number of concurrent tasks exceeds the limit. |
| LimitExceeded.MaximumTask | The number of tasks created on the day exceeds the limit. |
| LimitExceeded.RateLimitExceeded | Reached the API rate limit. |
| ResourceNotFound.ChannelNotExist | The channel does not exist. |
| ResourceNotFound.CrtDateNotFound | The certificate does not exist. |
| ResourceNotFound.CrtDomainNotFound | No certificate was found. |
| ResourceNotFound.DomainNoRecord | The domain name has no ICP filing. |
| ResourceNotFound.DomainNotExist | The domain name does not exist or is not matched. |
| ResourceNotFound.EmptyData | Data is empty. |
| ResourceNotFound.ForbidService | You are blocked. |
| ResourceNotFound.FreezeService | Service suspended. |
| ResourceNotFound.InvalidUser | This API is not supported for the user. |
| ResourceNotFound.PlayDomainNoRecord | The playback domain name does not exist. |
| ResourceNotFound.PushDomainNoRecord | The push domain name does not exist. |
| ResourceNotFound.StopService | The service has been suspended due to account arrears. Please top up it to a positive balance to activate the service first. |
| ResourceNotFound.TaskId | The `TaskId` does not exist. |
| ResourceNotFound.UserDisableService | You disabled the service. |
| ResourceNotFound.UserNotExist | The CSS service has not been activated. |
| ResourceNotFound.UserNotFount | The user does not exist. |
| ResourceNotFound.WatermarkNotExist | The watermark does not exist. |
| ResourceUnavailable.InvalidVodStatus | The VOD service has not been activated. |
| ResourceUnavailable.StreamNotExist | The stream does not exist. |
| UnsupportedOperation.NotLVBCodeMode | Not a LVB code/new console mode |


---
*Source: [https://www.tencentcloud.com/document/product/267/30851](https://www.tencentcloud.com/document/product/267/30851)*
