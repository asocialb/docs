# Client APIs

## TIMPush - TIMPushManager

public abstract class TIMPushManager: Push Plugin Interface Class.

### API overview

#### Register/Unregister Push Service Interface

| API | Description |
| --- | --- |
| [registerPush](#registerPush) | Register for the push service and read the configuration file timpush-configs.json from the project (This interface can be used only after the app user has agreed to the privacy policy). |
| [unRegisterPush](#unRegisterPush) | Unregister and disable the push service. |
| [setRegistrationID](#setRegistrationID) | RegistrationID is the unique identifier ID of the push receiving device. By default, this ID is automatically generated when the push service is successfully registered, but you can also customize the setting. You can push messages to the specified device based on the RegistrationID. Note that uninstalling and reinstalling the device will change the RegistrationID, so you need to call the setRegistrationID interface before registering the push service. |
| [getRegistrationID](#getRegistrationID) | After successfully registering the push service, you can get the unique identifier ID of the push receiving device, that is, the RegistrationID, by calling the getRegistrationID interface. You can push messages to the specified device based on the RegistrationID. |

#### Push global listening interface

| API | Description |
| --- | --- |
| [addPushListener](#addPushListener) | Add Push listener. |
| [removePushListener](#removePushListener) | Remove Push listener. |

#### Custom Configuration Interface

| API | Description |
| --- | --- |
| [forceUseFCMPushChannel](#forceUseFCMPushChannel) | Specify offline push to use the FCM channel for the device. This needs to be called before registering the push service. |
| [disablePostNotificationInForeground](#aae128cb-d4c0-4e24-a5bb-9945dd7efbfa) | Disable the notification bar when the app is in the foreground. |

### Interface Details

#### Static Public Member Functions

static TIMPushManager getInstance(): Retrieves the TIMPushManager manager instance.

#### Member Function Description

##### abstract void registerPush(Context context, int sdkAppId, String appKey, TIMPushCallback callback)

Register for offline push service: Please correctly pass the sdkAppId and appKey parameters to register for the push service.

Note: If you have already integrated the Chat product, please call this interface after Chat login is successful. Set the appKey parameter to null to enable offline push capability.

Parameter description:

| Parameter | Description | Get Path |
| --- | --- | --- |
| sdkAppId | The application ID assigned to you by the Chat console. | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7f83398cc37411ef86f2525400bf7822.png) |
| appKey | The client key assigned to you by the Chat console. |  |

> **Note:**You need to use the login API provided by [TUILogin](https://github.com/TencentCloud/chat-uikit-android/blob/main/TUIKit/TUICore/tuicore/src/main/java/com/tencent/qcloud/tuicore/TUILogin.java) of the TUICore component to log in; the plugin will automatically detect this and register the push service.If you do not wish to use the API provided by [TUILogin](https://github.com/TencentCloud/chat-uikit-android/blob/main/TUIKit/TUICore/tuicore/src/main/java/com/tencent/qcloud/tuicore/TUILogin.java), you need to manually call this interface to register the service after completing the login operation.

##### abstract void unRegisterPush(TIMPushCallback callback)

Unregister to close offline push services, call before logging out of the Chat account.

> **Note:**If you do not wish to use the push service, you can manually call this interface to unregister the service.If you log out using the logout API provided by [TUILogin](https://github.com/TencentCloud/chat-uikit-android/blob/main/TUIKit/TUICore/tuicore/src/main/java/com/tencent/qcloud/tuicore/TUILogin.java) of the TUICore component, the plugin will automatically detect this and unregister the push service.

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
| enable | true: Use FCM channel.false: Use the native channel. |

##### abstract void disablePostNotificationInForeground(boolean disable)

Disable the notification bar when the app is in the foreground, disabled by default.

Parameter description:

| Parameter | Description |
| --- | --- |
| disable | true: disable.false: enable. |

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
*Source: [https://trtc.io/document/67571](https://trtc.io/document/67571)*
