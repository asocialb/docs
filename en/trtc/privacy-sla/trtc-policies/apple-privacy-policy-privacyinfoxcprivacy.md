# Apple Privacy Policy: PrivacyInfo.xcprivacy

According to Apple Inc.'s [App Store privacy update](https://developer.apple.com/news/?id=r1henawx), starting from spring 2024, apps listed in the App Store must also offer a **privacy manifest**.

**When you are ready to distribute your app, Xcode will combine the privacy manifests of all third-party SDKs used by the app into an easy-to-use report.**

This report completely summarizes all the third-party SDKs in the app, allowing you to create privacy tags in an easy and accurate manner.

Therefore, the SDKs embedded in the app and third-party libraries all need to include **PrivacyInfo.xcprivacy**.

## Adaptation of Tencent Real-Time Communication (TRTC)

In TRTC SDK **11.7** and later (including the simplified and full-feature editions), the **PrivacyInfo.xcprivacy** file is included by default.

In TUICallKit **2.3.0.920** and later, the **PrivacyInfo.xcprivacy** file is included by default.

In TUIRoomKit **2.3.0**and later, the **PrivacyInfo.xcprivacy** file is included by default.

In TUILiveKit **2.1.1**and later, the **PrivacyInfo.xcprivacy** file is included by default.

- When you go integrating with CocoaPod, **PrivacyInfo.xcprivacy** will be added to your project through Pod, so that **no extra work is needed**.
- When you go integrating manually, please make sure to **copy PrivacyInfo.xcprivacy under the source code directory to your code project**.

> **Note:**The TUIKit scheme and TRTC SDK full-feature edition (Professional) include several SDK products, and **PrivacyInfo.xcprivacy** may have slight differences in content. So you can choose the corresponding file version as needed.

### TRTC-related **PrivacyInfo.xcprivacy**

Simplified Edition (TRTC) SDK

Full-feature Edition (Professional) SDK

TUICallKit

TUIRoomKit

TUILiveKit

```
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd"><plist version="1.0"><dict>	<key>NSPrivacyCollectedDataTypes</key>	<array>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypeUserID</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypeOtherDiagnosticData</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypePhotosorVideos</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypeAudioData</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypePerformanceData</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>	</array>	<key>NSPrivacyAccessedAPITypes</key>	<array>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategoryUserDefaults</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>C56D.1</string>			</array>		</dict>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategoryFileTimestamp</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>0A2A.1</string>			</array>		</dict>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategorySystemBootTime</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>35F9.1</string>			</array>		</dict>	</array></dict></plist>
```

```
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd"><plist version="1.0"><dict>	<key>NSPrivacyCollectedDataTypes</key>	<array>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypeUserID</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypeOtherDiagnosticData</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypePhotosorVideos</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypeAudioData</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>		<dict>			<key>NSPrivacyCollectedDataType</key>			<string>NSPrivacyCollectedDataTypePerformanceData</string>			<key>NSPrivacyCollectedDataTypeLinked</key>			<false/>			<key>NSPrivacyCollectedDataTypeTracking</key>			<false/>			<key>NSPrivacyCollectedDataTypePurposes</key>			<array>				<string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>			</array>		</dict>	</array>	<key>NSPrivacyAccessedAPITypes</key>	<array>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategoryDiskSpace</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>E174.1</string>			</array>		</dict>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategoryUserDefaults</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>C56D.1</string>			</array>		</dict>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategoryFileTimestamp</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>0A2A.1</string>			</array>		</dict>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategorySystemBootTime</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>35F9.1</string>			</array>		</dict>	</array></dict></plist>
```

```
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd"><plist version="1.0"><dict>	<key>NSPrivacyTracking</key>	<false/>	<key>NSPrivacyTrackingDomains</key>	<array/>    <key>NSPrivacyCollectedDataTypes</key>    <array>        <dict>            <key>NSPrivacyCollectedDataType</key>            <string>NSPrivacyCollectedDataTypeUserID</string>            <key>NSPrivacyCollectedDataTypeLinked</key>            <false/>            <key>NSPrivacyCollectedDataTypeTracking</key>            <false/>            <key>NSPrivacyCollectedDataTypePurposes</key>            <array>                <string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>            </array>        </dict>    </array>	<key>NSPrivacyAccessedAPITypes</key>	<array>        <dict>            <key>NSPrivacyAccessedAPIType</key>            <string>NSPrivacyAccessedAPICategoryDiskSpace</string>            <key>NSPrivacyAccessedAPITypeReasons</key>            <array>                <string>E174.1</string>            </array>        </dict>        <dict>            <key>NSPrivacyAccessedAPIType</key>            <string>NSPrivacyAccessedAPICategoryUserDefaults</string>            <key>NSPrivacyAccessedAPITypeReasons</key>            <array>                <string>CA92.1</string>            </array>        </dict>	</array></dict></plist>
```

```
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd"><plist version="1.0"><dict>	<key>NSPrivacyTracking</key>	<false/>	<key>NSPrivacyTrackingDomains</key>	<array/>    <key>NSPrivacyCollectedDataTypes</key>    <array>        <dict>            <key>NSPrivacyCollectedDataType</key>            <string>NSPrivacyCollectedDataTypeUserID</string>            <key>NSPrivacyCollectedDataTypeLinked</key>            <false/>            <key>NSPrivacyCollectedDataTypeTracking</key>            <false/>            <key>NSPrivacyCollectedDataTypePurposes</key>            <array>                <string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>            </array>        </dict>    </array>	<key>NSPrivacyAccessedAPITypes</key>	<array>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategorySystemBootTime</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>35F9.1</string>			</array>		</dict>	</array></dict></plist>
```

```
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd"><plist version="1.0"><dict>	<key>NSPrivacyTracking</key>	<false/>	<key>NSPrivacyTrackingDomains</key>	<array/>    <key>NSPrivacyCollectedDataTypes</key>    <array>        <dict>            <key>NSPrivacyCollectedDataType</key>            <string>NSPrivacyCollectedDataTypeUserID</string>            <key>NSPrivacyCollectedDataTypeLinked</key>            <false/>            <key>NSPrivacyCollectedDataTypeTracking</key>            <false/>            <key>NSPrivacyCollectedDataTypePurposes</key>            <array>                <string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>            </array>        </dict>    </array>	<key>NSPrivacyAccessedAPITypes</key>	<array>		<dict>			<key>NSPrivacyAccessedAPIType</key>			<string>NSPrivacyAccessedAPICategorySystemBootTime</string>			<key>NSPrivacyAccessedAPITypeReasons</key>			<array>				<string>35F9.1</string>			</array>		</dict>	</array></dict></plist>
```

### Manual import into your own app

In addition to importing PrivacyInfo automatically through CocoaPod, you can also directly complete the terms in **PrivacyInfo.xcprivacy** of the TRTC SDK (or relevant version) into your own app's **PrivacyInfo.xcprivacy**. For specific completion methods, you can refer to the following content:

- Adding with source code

In Xcode, use source code to open **PrivacyInfo.xcprivacy** under the app project. Copy the entries from Tencent Cloud's **PrivacyInfo.xcprivacy**, being careful not to add duplicates or misplace lines.

- Adding with property list

In Xcode, double-click to open the **PrivacyInfo.xcprivacy** file, click +, and Xcode will prompt optional terms and configurable items. Supplement them according to your needs.


---
*Source: [https://trtc.io/document/60152](https://trtc.io/document/60152)*
