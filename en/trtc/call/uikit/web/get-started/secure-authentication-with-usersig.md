# Secure authentication with userSig

## Overview

This document outlines two authentication methods for Tencent-RTC services, with a focus on UserSig, a security signature by Tencent Cloud to safeguard against unauthorized access. For basic cloud service usage, provide SDKAppID, UserID, and UserSig during SDK initialization or login.

- SDKAppID is used to identify your application.
- UserID is used to identify your user.
- UserSig is a security signature calculated based on the first two using the **HMAC SHA256** encryption algorithm. As long as attackers cannot forge the UserSig, they cannot steal your cloud service traffic.

## How to calculate UserSig during the debugging phase?

You can calculate and obtain UserSig using either [Client Sample Code](#client) or the [Console](#console). Please refer to the following introduction for details.

> **Unsafe:**Note that the following two UserSig acquisition calculation schemes are only suitable for debugging. If the product is to be officially launched, **using these schemes is not recommended** because the SECRETKEY in the client code (especially on the Web) is easily vulnerable to decompilation and reverse engineering.

### Client calculation of UserSig

#### **1. Get SDKAppID and Key**:

- Log in to Tencent-RTC Console > App Management.
- Locate the app with the desired SDKAppID, click its name for details.
- Click on SDKSecretKey to reveal and copy.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e2be55ed921211ef810152540055f650.png)

#### **2. Calculate UserSig:**

To facilitate client use, we provide source files for calculating UserSig on various platforms. You can download and use them directly:

| Android | iOS | Web | Windows(C++) | Windows(C#) | Flutter | Mac |
| --- | --- | --- | --- | --- | --- | --- |
| [GitHub](https://github.com/LiteAVSDK/TRTC_Android/tree/main/TRTC-API-Example/Debug/src/main/java/com/tencent/trtc/debug/GenerateTestUserSig.java) | [GitHub](https://github.com/LiteAVSDK/TRTC_iOS/tree/main/TRTC-API-Example-OC/Debug/GenerateTestUserSig.h) | [GitHub](https://github.com/LiteAVSDK/TRTC_Web/blob/main/quick-demo-js/js/libs/generateTestUserSig.js) | [GitHub](https://github.com/LiteAVSDK/TRTC_Windows/blob/main/TRTC-API-Example-C%2B%2B/TRTC-API-Example-Qt/src/Util/defs.h) | [GitHub](https://github.com/LiteAVSDK/TRTC_Windows/blob/main/TRTC-API-Example-CSharp/TRTC-API-Example-CSharp/GenerateTestUserSig.cs) | [GitHub](https://github.com/Tencent-RTC/TRTC_Flutter/blob/master/TRTC-API-Example/lib/debug/generate_test_user_sig.dart) | [GitHub](https://github.com/LiteAVSDK/TRTC_Mac/tree/main/OCDemo/TRTCDemo/TRTC/GenerateTestUserSig.h) |

The sample code is as follows (of course, you can also refer to the demo projects of our products, see the development documentation of each product):

Android

iOS

Web

Window(C++)

Window(C#)

Flutter

Mac

```
// Step 1: Import the source fileimport com.xxx.xxx.GenerateTestUserSig;// Step 2: Fill in the SDKAppID and SDK key obtained from the previous stepsGenerateTestUserSig.SDKAPPID = xxxxxx;GenerateTestUserSig.SECRETKEY = "xxxxxx";// Step 3: Generate userSig based on userIDString userSig = GenerateTestUserSig.genTestUserSig("userID");
```

```
// Step 1: Import the header file#import "GenerateTestUserSig.h"// Step 2: Fill in the SDKAppID and SDK key obtained from the previous steps[GenerateTestUserSig setSDKAPPID:xxxxxx];[GenerateTestUserSig setSECRETKEY:@"xxxxxx"];// Step 3: Generate userSig based on userIDNSString *userSig = [GenerateTestUserSig genTestUserSig:@"userID"];
```

```
// Step 1: Import the module<script src='js/libs/lib-generate-test-usersig.min.js'></script><script src='js/libs/generateTestUserSig.js'></script>// Step 2: Fill in the SDKAppID and SDK key obtained from the previous steps, enter the custom userID, and generate userSigconst {sdkAppId, userSig } = genTestUserSig({	sdkAppId: xxxxxx, 	userId: 'xxxxxx',	sdkSecretKey: 'xxxxxx',}
```

```
// Step 1: Import the header file#include "GenerateTestUserSig.h"// Step 2: Fill in the SDKAppID and SDK key obtained from the previous stepsconst int SDKAPPID = xxxxxx;const char* SECRETKEY = "xxxxxx";// Step 3: Generate userSig based on userIDconst char* userSig = GenerateTestUserSig::genTestUserSig("userID", SDKAPPID, SECRETKEY);
```

```
// Step 1: Import the header fileusing GenerateTestUserSig;// Step 2: Fill in the SDKAppID and SDK key obtained from the previous stepsGenerateTestUserSig.SDKAPPID = xxxxxx; GenerateTestUserSig.SECRETKEY = "xxxxxx";// Step 3: Generate userSig based on userIDstring userSig = GenerateTestUserSig.GetInstance().GenTestUserSig("userID");
```

```
// Step 1: Import the source fileimport 'package:xxx/GenerateTestUserSig.dart';// Step 2: Fill in the SDKAppID and SDK key obtained from the previous stepsGenerateTestUserSig.SDKAPPID = xxxxxx;GenerateTestUserSig.SECRETKEY = "xxxxxx";// Step 3: Generate userSig based on userIDString userSig = GenerateTestUserSig.genTestUserSig("userID");
```

```
// Step 1: Import the header file#import "GenerateTestUserSig.h"// Step2: Enter the SDKAppID and SDK secret obtained in the Back step[GenerateTestUserSig setSDKAPPID:xxxxxx];[GenerateTestUserSig setSECRETKEY:@"xxxxxx"];// Step 3: Generate userSig based on userIDNSString *userSig = [GenerateTestUserSig genTestUserSig:@"userID"];
```

### Get UserSig from the console

- Log in to Tencent-RTC Console, navigate to Development Tools > [UserSig Tools](https://console.trtc.io/usersig).
- Under the UserSig Generation Tool, select the corresponding SDKAppID and UserID.
- Click the Generate button to compute the corresponding UserSig.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/101f083b920511ef8bbd525400fdb830.png)

## How to calculate UserSig during the official operation phase?

During the official operation phase, Tencent-RTC provides a more secure server-side UserSig calculation solution. This maximizes the protection of the key used to calculate UserSig from being leaked, as compromising a server is more difficult than reverse engineering an app. The specific implementation process is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/12569f72920411ef810152540055f650.png)

1. Before your app calls the SDK initialization function, it must first request UserSig from your server.
2. Your server calculates UserSig based on SDKAppID and UserID. Refer to the first part of the documentation for the source code.
3. The server returns the calculated UserSig to your app.
4. Your app passes the obtained UserSig to the SDK via a specific API.
5. The SDK submits `SDKAppID + UserID + UserSig` to Tencent CVM for verification.
6. Tencent Cloud verifies UserSig to confirm its validity.
7. After verification, Tencent-RTC services will be provided to the Tencent-RTC SDK.

To simplify your implementation process, we provide UserSig Calculation Source Code and examples in multiple language versions:

| Language Version | Signature algorithm | Source Code | Usage Examples |
| --- | --- | --- | --- |
| Java | HMAC-SHA256 | [genSig](https://github.com/Tencent-RTC/tls-sig-api-v2-java/blob/master/src/main/java/com/tencentcloud/TLSSigAPIv2.java) | [GitHub](https://github.com/Tencent-RTC/tls-sig-api-v2-java) |
| Go | HMAC-SHA256 | [genSig](https://github.com/Tencent-RTC/tls-sig-api-v2-golang/blob/master/tencentyun/TLSSigAPI.go) | [GitHub](https://github.com/Tencent-RTC/tls-sig-api-v2-golang) |
| PHP | HMAC-SHA256 | [genSig](https://github.com/Tencent-RTC/tls-sig-api-v2-php/blob/master/src/TLSSigAPIv2.php) | [GitHub](https://github.com/Tencent-RTC/tls-sig-api-v2-php) |
| Node.js | HMAC-SHA256 | [genSig](https://github.com/Tencent-RTC/tls-sig-api-v2-node/blob/master/TLSSigAPIv2.js) | [GitHub](https://github.com/Tencent-RTC/tls-sig-api-v2-node) |
| Python | HMAC-SHA256 | [genSig](https://github.com/Tencent-RTC/tls-sig-api-v2-python/blob/master/TLSSigAPIv2.py) | [GitHub](https://github.com/Tencent-RTC/tls-sig-api-v2-python) |
| C# | HMAC-SHA256 | [GenSig](https://github.com/Tencent-RTC/tls-sig-api-v2-cs/blob/master/tls-sig-api-v2-cs/TLSSigAPIv2.cs) | [GitHub](https://github.com/Tencent-RTC/tls-sig-api-v2-cs) |


---
*Source: [https://trtc.io/document/35166](https://trtc.io/document/35166)*
