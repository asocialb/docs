# Customized Icon

Android

iOS

uni-app

### Supported Vendors

Huawei and Google FCM support Customized Icon; other manufacturers do not support Customized Icon, and by default, use the App Icon.

### Configuration Method

Effective when configured in the main project's Manifest File:

Huawei

Google FCM

```
<meta-data    android:name="com.huawei.messaging.default_notification_icon"    android:resource="@drawable/Icon Resource Name" />
```

```
<!-- [START fcm_default_icon] --><!-- Set custom default icon. This is used when no icon is set for incoming notification messages.     See README(https://goo.gl/l4GJaQ) for more. --><meta-data    android:name="com.google.firebase.messaging.default_notification_icon"    android:resource="@drawable/Icon Resource Name" /><!-- Set color used with incoming notification messages. This is used when no color is set for the incoming     notification message. See README(https://goo.gl/6BKBk7) for more. --><meta-data    android:name="com.google.firebase.messaging.default_notification_color"    android:resource="@android:color/white" /><!-- [END fcm_default_icon] -->
```

> **Note:**FCM Icon Requirements: Small icon must be a PNG image with Alpha transparency channel.Background must be transparent.Avoid leaving excessive padding around the icon.It is recommended to use 46 x 46px uniformly. Smaller images will be fuzzy, while larger ones will be automatically scaled down by the system.

Custom definitions are not supported; the App Icon is used by default.

> **Note:**Only **Huawei** supports settings, other manufacturers do not, and the App Icon is used by default.

Put the Small Icons in the `nativeResources/android/res/drawable` folder and rename the resource file to `huawei_private_icon.png`. As shown in the figure:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9fb71bfac1d211efbcd1525400bf7822.png)


---
*Source: [https://trtc.io/document/60574](https://trtc.io/document/60574)*
