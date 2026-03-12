# Custom Definition Ringtone

> **Notes:**If the offline push message ringtone is not set, it will follow the system notification settings of the device by default. Take Huawei as an example. See "Phone Settings > Notifications > App Notification Management > Notification Sound".Customizing ringtone needs to be set one by one according to the vendor platform support. See the following method summary: The methods of customizing ringtone on different platforms of different vendors are different. Android 8.0 supporting vendors also need to be set through channel. Ring duration is related to ringtone resource duration.

Android

iOS

Flutter

### Systems below Android 8.0

1. Custom ringtone resource files for Android should be added to the project's raw directory; for iOS, link them into the Xcode project.
2. Send messages with specified custom ringtone.

restAPI

SDK API

Please refer to the restAPI interface, such as [single push interface](https://www.tencentcloud.com/document/product/1047/67553), with the following field example:

```
 {    // ...    "OfflinePushInfo": {        "AndroidInfo": {             "Sound": "shake",  // without suffix        },        "ApnsInfo": {            "Sound": "apns.mp3",        }    }}
```

If you have integrated Chat related products, please send messages using the [setAndroidSound()](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a3ff923225d5a79802a02c47a07e07fc5) and [setIOSSound()](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#acffd09150398b06c3d7eb42baee5aee1) interfaces.

```
V2TIMOfflinePushInfo v2TIMOfflinePushInfo = new V2TIMOfflinePushInfo();v2TIMOfflinePushInfo.setAndroidSound("Ringtone Name");v2TIMOfflinePushInfo.setIOSSound("Ringtone Name.mp3");String msgID = V2TIMManager.getMessageManager().sendMessage(v2TIMMessage, isGroup ? null : userID, isGroup ? groupID : null, V2TIMMessage.V2TIM_PRIORITY_DEFAULT, false, v2TIMOfflinePushInfo, new V2TIMSendCallback<V2TIMMessage>() {@Override public void onProgress(int progress) { }@Override public void onError(int code, String desc) { }@Override public void onSuccess(V2TIMMessage v2TIMMessage) { }});
```

> **Note:**Supported in ChatSDK v6.1.2155 or above.The interface supports Huawei, Xiaomi, FCM, and APNS.

### Android 8.0 and later versions

#### Huawei and APNs

Huawei and APNS can use the above interfaces to set offline push ringtone prompt.

#### OPPO

1 Place the customized ring tone resource file in the raw directory of the project resources, then create a notification channel as follows.

```
// Custom creation exampleif (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {    NotificationManager nm = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);    NotificationChannel notificationChannel =            new NotificationChannel("channelId", "channelName", NotificationManager.IMPORTANCE_HIGH);    notificationChannel.enableLights(true);    notificationChannel.enableVibration(true);    notificationChannel.setShowBadge(true);    notificationChannel.setLockscreenVisibility(Notification.VISIBILITY_PUBLIC);        // "android.resource://package_name/raw/private_ring"    notificationChannel.setSound(Uri.parse("sound"), null);    nm.createNotificationChannel(notificationChannel);}
```

2 Use the created channel.

- [Create Private Message Channel](https://open.oppomobile.com/new/developmentDoc/info?id=12391).
- Send messages specifying the channelID to take effect with the custom ring tone. Refer to the following interface settings. For console settings, see the channelID field in the certificate. Only one of the two settings is needed.

restAPI

SDK API

Please refer to the restAPI interface, such as [single push interface](https://www.tencentcloud.com/document/product/1047/67553), with the following field example:

```
 {    // ...    "OfflinePushInfo": {        "AndroidInfo": {             "OPPOChannelID": "test_OPPO_channel_id",        }    }}
```

If you have integrated IM related products, please send messages using the [setAndroidOPPOChannelID](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a32d340e95395bb64cc3e8f62321aafe1) interface.

#### Mi

1 Log in to the manufacturer console to [create channel and configuration](https://dev.mi.com/console/doc/detail?pId=2422#_2), where the ring tone file needs to be added to the raw directory of your local Android Studio project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5c7fed04b2f611efbfb3525400bdab9d.png)

Send messages specifying the channelID to take effect with the custom ring tone. Refer to the following interface settings. For console settings, see the channelID field in the certificate. Only one of the two settings is needed.

restAPI

SDK API

Please refer to the restAPI interface, such as [single push interface](https://www.tencentcloud.com/document/product/1047/67553), with the following field example:

```
 {    // ...    "OfflinePushInfo": {        "AndroidInfo": {             "XiaoMiChannelID": "test_XiaoMi_channel_id",        }    }}
```

If you have integrated IM related products, see [setAndroidXiaoMiChannelID](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#ac769aec48cdbc9a57416c5a79504617a) for details.

```
V2TIMOfflinePushInfo v2TIMOfflinePushInfo = new V2TIMOfflinePushInfo();v2TIMOfflinePushInfo.setAndroidXiaoMiChannelID("Channel ID Applied by Manufacturer");String msgID = V2TIMManager.getMessageManager().sendMessage(v2TIMMessage, isGroup ? null : userID, isGroup ? groupID : null, V2TIMMessage.V2TIM_PRIORITY_DEFAULT, false, v2TIMOfflinePushInfo, new V2TIMSendCallback<V2TIMMessage>() {@Override public void onProgress(int progress) {    TUIChatUtils.callbackOnProgress(callBack, progress); }@Override public void onError(int code, String desc) {    TUIChatUtils.callbackOnError(callBack, TAG, code, desc); }@Override public void onSuccess(V2TIMMessage v2TIMMessage) { }});
```

#### FCM

1 Place the customized ring tone resource file in the raw directory of the project resources, then create a notification channel as follows.

```
// Custom creation exampleif (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {    NotificationManager nm = (NotificationManager) context.getSystemService(context.NOTIFICATION_SERVICE);    NotificationChannel notificationChannel =            new NotificationChannel("channelId", "channelName", NotificationManager.IMPORTANCE_HIGH);    notificationChannel.enableLights(true);    notificationChannel.enableVibration(true);    notificationChannel.setShowBadge(true);    notificationChannel.setLockscreenVisibility(Notification.VISIBILITY_PUBLIC);        // "android.resource://package_name/raw/private_ring"    notificationChannel.setSound(Uri.parse("sound"), null);    nm.createNotificationChannel(notificationChannel);}
```

Send messages specifying the channelID with a custom ringtone.

restAPI

SDK API

Please refer to the restAPI interface, such as [single push interface](https://www.tencentcloud.com/document/product/1047/67553), with the following field example:

```
 {    // ...    "OfflinePushInfo": {        "AndroidInfo": {             "GoogleChannelID": "test_Google_channel_id",        }    }}
```

If you have integrated IM related products, see [setAndroidFCMChannelID](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a1e63514ec664a5f7bc8c6a5b09f0689e) for details.

```
V2TIMOfflinePushInfo v2TIMOfflinePushInfo = new V2TIMOfflinePushInfo();v2TIMOfflinePushInfo.setAndroidFCMChannelID(PrivateConstants.fcmPushChannelId);String msgID = V2TIMManager.getMessageManager().sendMessage(v2TIMMessage, isGroup ? null : userID, isGroup ? groupID : null, V2TIMMessage.V2TIM_PRIORITY_DEFAULT, false, v2TIMOfflinePushInfo, new V2TIMSendCallback<V2TIMMessage>() {@Override public void onProgress(int progress) {    TUIChatUtils.callbackOnProgress(callBack, progress); }@Override public void onError(int code, String desc) {    TUIChatUtils.callbackOnError(callBack, TAG, code, desc); }@Override public void onSuccess(V2TIMMessage v2TIMMessage) { }});
```

> **Note:**Supported in ChatSDK v7.0.3754 or above.FCM custom alert tones or setting ChannelID are only supported in certificate mode.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/804e9533c1d011efb492525400e889b2.png)

1. Set the iOSSound field of OfflinePushInfo when sending messages. Pass the voice file name to iOSSound.

restAPI

SDK API

Please refer to the restAPI interface, such as [single push interface](https://www.tencentcloud.com/document/product/1047/67553), with the following field example:

```
 {    // ...    "OfflinePushInfo": {        "ApnsInfo": {            "Sound": "apns.mp3",        }    }}
```

If you have integrated IM related products, please refer to sending messages.

```
V2TIMOfflinePushInfo *pushInfo = [[V2TIMOfflinePushInfo alloc] init];pushInfo.title = @"push title";pushInfo.iOSSound = @"phone_ringing.mp3"; // your voice file's name[[V2TIMManager sharedInstance] sendMessage:msg receiver:receiver groupID:groupID priority:V2TIM_PRIORITY_DEFAULT onlineUserOnly:NO offlinePushInfo:pushInfo progress:nil succ:^{} fail:^(int code, NSString *msg) {}];
```

> **Note:**Offline push notification sound settings (effective only for iOS), when `iOSSound = kIOSOfflinePushNoSound`, it indicates no sound will be played upon receiving. When `iOSSound = kIOSOfflinePushDefaultSound`, it indicates the system sound will be played upon receiving. To customize `iOSSound`, you first need to link the audio file into the Xcode project, and then set the audio filename (including the extension) to `iOSSound`.iOS Custom Ringtone length cannot exceed 30s.

2. Set the `AndroidSound` field of OfflinePushInfo when sending messages. Pass the voice file name to `AndroidSound`.

restAPI

SDK API

Please refer to the restAPI interface, such as [single push interface](https://www.tencentcloud.com/document/product/1047/67553), with the following field example:

```
 {    "OfflinePushInfo": {        "AndroidInfo": {             "Sound": "shake",  // without suffix            "OPPOChannelID": "test_OPPO_channel_id",            "XiaoMiChannelID": "test_XiaoMi_channel_id",            "OPPOChannelID": "test_OPPO_channel_id",            "GoogleChannelID": "test_Google_channel_id"        },        "ApnsInfo": {            "Sound": "apns.mp3"        }    }}
```

If you have integrated IM related products, please refer to sending messages.

```
V2TIMOfflinePushInfo *pushInfo = [[V2TIMOfflinePushInfo alloc] init];pushInfo.title = @"push title";pushInfo.AndroidSound = @"phone_ringing"; // your voice file's name[[V2TIMManager sharedInstance] sendMessage:msg receiver:receiver groupID:groupID priority:V2TIM_PRIORITY_DEFAULT onlineUserOnly:NO offlinePushInfo:pushInfo progress:nil succ:^{} fail:^(int code, NSString *msg) {}];
```

> **Note:**Offline push notification sound settings (effective only for Android, supported only in imsdk 6.1 and above) are supported only on Huawei and Google phones for setting ringtone prompts.For Xiaomi ringtone settings, please refer to: [Server-side Java SDK documentation](https://dev.mi.com/console/doc/detail?pId=1278%23_3_0).To customize `AndroidSound`, you first need to place the audio file in the raw directory of the Android project, and then set the `AndroidSound` with the audio filename (without the extension).

> **Note:**The interface supports Huawei, Xiaomi, FCM, and APNS.

Custom ringtone resource files for Android should be added to the project's raw directory; for iOS, link them into the Xcode project.

Set the `iOSSound` and `androidSound` fields of offlinePushInfo when sending messages.

restAPI

SDK API

Please refer to the restAPI interface, such as [single push interface](https://www.tencentcloud.com/document/product/1047/67553), with the following field example:

```
 {    // ...    "OfflinePushInfo": {        "AndroidInfo": {             "Sound": "shake",  // without suffix            "OPPOChannelID": "test_OPPO_channel_id",            "XiaoMiChannelID": "test_XiaoMi_channel_id",            "OPPOChannelID": "test_OPPO_channel_id",            "GoogleChannelID": "test_Google_channel_id"        },        "ApnsInfo": {            "Sound": "apns.mp3"        }    }}
```

If you have integrated im related products, set the [offlinePushInfo](https://comm.qq.com/im/doc/flutter/zh/SDKAPI/Class/Message/OfflinePushInfo.html)'s `iOSSound` and `androidSound` fields when calling [sendMessage](https://comm.qq.com/im/doc/flutter/zh/SDKAPI/Api/V2TIMMessageManager/sendMessage.html) to send messages.

For specific manufacturer configurations, refer to the content of the Android and iOS modules. The methods to call are all named the same in the Flutter version of the IM SDK.


---
*Source: [https://trtc.io/document/60573](https://trtc.io/document/60573)*
