# Android

## TIMPush - TIMPushManager

public abstract class TIMPushManager: Push Plugin Interface Class.

### API overview

#### Register/Unregister Push Service Interface

| API | Description |
| --- | --- |
| [registerPush](https://www.tencentcloud.com/document/product/1047/60557#registerPush) | Register Push Service, push information reads the configuration file timpush-configs.json in the project (this interface must be called after the App user has agreed to the privacy policy to use the push service). |
| [unRegisterPush](https://www.tencentcloud.com/document/product/1047/60557#unRegisterPush) | Unregister and disable the push service. |
| [setRegistrationID](https://www.tencentcloud.com/document/product/1047/60557#setRegistrationID) | RegistrationID is the unique identifier ID of the push receiving device. By default, this ID is automatically generated when the push service is successfully registered, but you can also customize the setting. You can push messages to the specified device based on the RegistrationID. Note that uninstalling and reinstalling the device will change the RegistrationID, so you need to call the setRegistrationID interface before registering the push service. |
| [getRegistrationID](https://www.tencentcloud.com/document/product/1047/60557#getRegistrationID) | After successfully registering the push service, you can get the unique identifier ID of the push receiving device, that is, the RegistrationID, by calling the getRegistrationID interface. You can push messages to the specified device based on the RegistrationID. |

#### Push global listening interface

| API | Description |
| --- | --- |
| [addPushListener](https://www.tencentcloud.com/document/product/1047/60557#addPushListener) | Add Push listener. |
| [removePushListener](https://www.tencentcloud.com/document/product/1047/60557#removePushListener) | Remove Push listener. |

#### Custom Configuration Interface

| API | Description |
| --- | --- |
| [forceUseFCMPushChannel](https://www.tencentcloud.com/document/product/1047/60557#forceUseFCMPushChannel) | Specify offline push to use the FCM channel for the device. This needs to be called before registering the push service. |
| [disablePostNotificationInForeground](https://www.tencentcloud.com/document/product/1047/60557#disablePostNotificationInForeground) | Disable the notification bar when the app is in the foreground. |

### Interface Details

#### Static Public Member Functions

static TIMPushManager getInstance(): Retrieves the TIMPushManager manager instance.

#### Member Function Description

##### abstract void registerPush(Context context, int sdkAppId, String appKey, TIMPushCallback callback)

Register Push Service. Please correctly pass the parameters sdkAppId and appKey to register the push service.

Parameter description:

| Parameter | Description | Get Path |
| --- | --- | --- |
| sdkAppId | The application ID assigned to you by the Chat console. | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f235d333c36e11efad4f52540044a08e.png) |
| appKey | The client key assigned to you by the Chat console. |  |

##### abstract void unRegisterPush(TIMPushCallback callback)

Unregister and disable the push service.

##### abstract void setRegistrationID(String registrationID, TIMPushCallback callback)

Set the push ID identifier used for registering the push service, i.e., RegistrationID, which needs to be called before registering the push service.

Parameter description:

| Parameter | Description |
| --- | --- |
| registrationID | Unique ID for push notifications on the device, which may change if uninstalled and reinstalled. |

##### abstract void getRegistrationID(TIMPushCallback callback)

After successfully registering for the push service, obtain the push ID identifier, i.e., RegistrationID.

##### abstract void addPushListener([TIMPushListener](#TIMPushListener) listener)

Add Push listener

##### abstract void removePushListener([TIMPushListener](#TIMPushListener) listener)

Remove Push listener

##### abstract void forceUseFCMPushChannel(boolean enable)

Specify offline push to use the FCM channel for the device. This needs to be called before registering the push service.

Parameter description:

| Parameter | Description |
| --- | --- |
| enable | true: Use FCM channel.false: use the native channel. |

##### abstract void disablePostNotificationInForeground(boolean disable)

Disable notification bar pop-ups when the app is in the foreground. When the Push SDK receives an online Push, it will automatically add a Notification to the notification bar. If you want to handle the online Push messages yourself, you can call this interface to disable the automatic notification bar pop-up feature.

Parameter description:

| Parameter | Description |
| --- | --- |
| disable | true: disablefalse: enable |

## TIMPush - TIMPushListener

public abstract class TIMPushListener: Push Listener class

### API overview

| API | Description |
| --- | --- |
| onRecvPushMessage | Received Push message. |
| onRevokePushMessage | Received a notification of Push message recall. |
| onNotificationClicked | Notification bar message click callback. |

### Interface Details

#### Member Function Description

##### void onRecvPushMessage(TIMPushMessage message)

Received Push message, message content.

##### void onRevokePushMessage(String messageID)

Received a notification of Push message recall, messageID uniquely identifies the message.

##### void onNotificationClicked(String ext)

Notification bar message click callback.

> **Note:**The push certificate in the console needs to be configured as "open a specific interface within the application" and use the default fill value to take effect.


---
*Source: [https://trtc.io/document/60557](https://trtc.io/document/60557)*
