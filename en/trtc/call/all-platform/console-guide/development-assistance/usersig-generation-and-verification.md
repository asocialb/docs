# UserSig Generation and Verification

You can generate UserSig online in the TRTC console, but it should be used only for quick testing at the development stage. This avoids key leakage and prevents attackers from stealing your traffic.

## Signature (UserSig) Generator

Signatures (UserSig) allow you to build trust with Tencent Cloud.

1. Log in to the [Chat console > Development Tools > UserSig Tools](https://console.trtc.io/usersig).
2. In the Signature (UserSig) Generator area, **select an application**, **manually input UserID**.
3. Click **Generate UserSig** to generate a signature, which expires after 180 days.
4. Click **Copy UserSig** to copy the signature and then paste and save the signature.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/23b0a1e0cb6b11f084a45254005ef0f7.png)

## Signature (UserSig) Verifier

The system automatically obtains the key of the current app. After entering the UserID and UserSig, you can use the tool to quickly check the validity of the UserSig.

1. Log in to the [Chat console > Development Tools > UserSig Tools](https://console.trtc.io/usersig).
2. In the Signature (UserSig) Verifier area, **select an application**, **manually input UserID** and **UserSig**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/23ce87d5cb6b11f08942525400e889b2.png)

3. Click **Verify** to see the verification result.
  - If verification succeeds, you can view the SDKAppID, UserID, generation time, service time, and expiration time of the UserSig in the verification results.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/23ce98e9cb6b11f08942525400e889b2.png)

  - If verification fails, you can view the cause of failure and solution in the verification results.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/23cecff5cb6b11f091ab5254007c27c5.png)


---
*Source: [https://trtc.io/document/39074](https://trtc.io/document/39074)*
