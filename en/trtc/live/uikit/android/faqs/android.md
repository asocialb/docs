# Android

### Can TUILiveKit use TRTC without introducing IM SDK?

**No**, all the components of TUIKit use Tencent Cloud IM SDK as the basic service for communication, such as the core logic of creating room signaling, Lian-mic signaling, etc., all use IM services. If you have purchased other IM products, you can also refer to TUILiveKit logic to adapt.

### allowBackup exception, How to Handle?

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c293ca53128511ef9af4525400720cb5.png)

- **Reasons**ï¼The `allowBackup` property is configured in the `AndroidManifest.xml` of several modules, causing conflicts.
- **Solution**ï¼You can remove the `allowBackup` attribute from your project's `AndroidManifest.xml `file or change it to false to turn off backup and restore, And add `tools:replace="android:allowBackup"` in the application node of the `AndroidManifest.xml` file; Indicates to override the settings of other modules, using your own Settings.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/37e7d004128611efbf645254007bbd8c.png)

### Activity need to use a Theme.AppCompat theme?

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8ca2de08133311efbf645254007bbd8c.png)

- **Reasons:**Since `LoginActivity` inherited from `AppCompatActivity`, a `Theme.AppCompat` was to be given to`LoginActivity`.
- **Solution**ï¼You can add a `Theme.AppCompat` theme to the `LoginActivity` configuration in your project's `AndroidManifest.xml` file. You can also use your own `Theme.AppCompat` theme. An example of a fix is shown in the image:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8c7a9ed1133311efbf645254007bbd8c.png)

### Failed to open the web page address in the browser?

**Solution:**You can add the following configurations to the AndroidManifest.xml file of your project:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/78d7a6fb2eae11efb0275254006c0558.png)


---
*Source: [https://trtc.io/document/60043](https://trtc.io/document/60043)*
