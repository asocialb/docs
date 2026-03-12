# Media Stream Private Encryption

## Feature Introduction

In industries such as finance, where stringent requirements for user privacy data are paramount, additional media stream encryption methods are often necessary to ensure the security of user data during network transmission and to guarantee the absolute safety of user information and data. TRTC further enhances its default encryption algorithms by providing media stream private encryption capabilities, thereby offering a robust barrier for user data security.

## Prerequisites

- Log in to the TRTC [Console](https://console.trtc.io/), activate the TRTC service and [create an application](https://www.tencentcloud.com/document/product/647/39077).
- Go to the [TRTC purchase page](https://console.trtc.io/subscription/buy/rtc?packType=pro) and buy the RTC-Engine **Pro** monthly package for the SDKAppid that requires encryption capabilities to unlock the SDK private encryption feature. For details on the monthly package, please refer to [RTC-Engine  Monthly Packages](https://www.tencentcloud.com/document/product/647/56025).
- Due to compliance management requirements, enabling the SDK's private encryption capability requires a review of business information. If needed, you can [submit a ticket](https://console.tencentcloud.com/workorder/category) for using the service.

## Notes

- TRTC audio and video call rooms using private encryption do not support on-cloud recording, relay to CDN, or server-side local recording services.
- Only iOS, Android, Windows, and macOS are supported. Other platforms are not supported at this time.

## Implementation Process

### Using the Private Encryption Scheme

Before joining a room, call the `enablePayloadPrivateEncryption`method to enable private encryption. Please refer to the following steps to generate and set the key and salt.

> **Note:**All users in the same room must use the same encryption mode, key, and salt.The SDK will automatically disable private encryption when a user leaves the room. To re-enable private encryption, you need to call this method again before the user re-enters the room.

### Generating and Setting the Key

1. On your server, use the following command to randomly generate a String-type key via OpenSSL.

```
// Randomly generate a 16-byte or 32-byte string-type key and pass this key into TRTCPayloadPrivateEncrypopenssl rand -hex 16a2e898d07a304246044f899a16123263openssl rand -hex 328301281ec074a4cb2bd31aa40ad795d15a190d56fb73408db91244c5a3f90a2d
```

> **Note:**The length of the generated key depends on the encryption algorithm you choose. If you select the TRTCEncryptionAlgorithmAes128Gcm algorithm, a 16-byte key needs to be generated. If you select the TRTCEncryptionAlgorithmAes256Gcm algorithm, a 32-byte key needs to be generated.

2. The client retrieves the String type key from the server and passes it to the SDK when calling `enablePayloadPrivateEncryption`.

### Generating and Setting the Salt

1. On your server, use the following command to randomly generate a 32-byte salt encoded in Base64.

```
//Randomly generate a 32-byte salt encoded in Base64 and pass this salt into TRTCPayloadPrivateEncryptionConfigopenssl rand -base64 323ZZ0nV/rDVUzTa6tXyz+F7rrUYIcxRqX5fiUto/FbZA=
```

2. The client retrieves the Base64-encoded salt from the server.
3. The client decodes the salt from Base64 to a uint8_t array of length 32, and then passes it to the SDK when calling`enablePayloadPrivateEncryption`.

### Example Code

```
#include <boost/archive/iterators/binary_from_base64.hpp>
#include <boost/archive/iterators/transform_width.hpp>
#include <string>
#include <vector>
#include <algorithm>
#include <stdint.h>
#include "ITRTCCloud.h"

liteav::ITRTCCloud* trtcCloud;

// Retrieve the key and salt generated on the server
bool getKeyAndSaltFromSever(std::string& secret, std::string& saltBase64);

// Declare a utility function to convert Base64 to uint8_t
bool decodeBase64(const std::string& input, std::vector<uint8_t>& output)
{
    output.resize(32);
    typedef boost::archive::iterators::transform_width<boost::archive::iterators::binary_from_base64<std::string::const_iterator>, 8, 6> Base64DecodeIterator;
    try {
        std::copy(Base64DecodeIterator(input.begin()), Base64DecodeIterator(input.end()), output.begin());
    } catch (...) {
        return false;
    }
    return true;
}

int enablePayloadPrivateEncryption() {
    std::string key;
    std::string saltBase64;
    std::vector<uint8_t> salt;
    if(!getKeyAndSaltFromSever(key, saltBase64))
        return -1;
    if(trtcCloud && decodeBase64(saltBase64, salt)) {
        liteav::TRTCPayloadPrivateEncryptionConfig config;
        // Set the encryption algorithm to TRTCEncryptionAlgorithmAes128Gcm
        config.encryptionAlgorithm = TRTCEncryptionAlgorithm::TRTCEncryptionAlgorithmAes128Gcm;
        // Set the key
        config.encryptionKey = key.c_str();
        // Set the salt
        memcpy(config.encryptionSalt, salt.data(), sizeof(config.encryptionSalt));
        // Enable private encryption
        return trtcCloud->enablePayloadPrivateEncryption(true, config);
    }
    return -1;
}
```


---
*Source: [https://trtc.io/document/61828](https://trtc.io/document/61828)*
