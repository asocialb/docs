# Domain Configuration

### How do I add a domain name to CSS?

1. Log in to the [CSS Console](https://console.tencentcloud.com/live) and enter **Domain Management**.
2. Add your own push or playback domain name. For more information, please see [Adding Domain Name](https://intl.cloud.tencent.com/document/product/267/35970).
3. Configure CNAME. For more information, please see [CNAME Configuration](https://intl.cloud.tencent.com/document/product/267/31057).
4. After successful configuration, you can push and play back with your own domain name.

### Why CNAME is still displayed as not configured after configuration?

After you configure CNAME as instructed in [CNAME Configuration](https://intl.cloud.tencent.com/document/product/267/31057), please wait patiently because it takes 15-30 minutes for the configuration to take effect. In addition, you can check whether CNAME configuration is successful by following the steps in [Verifying the Effect of CNAME Record](https://intl.cloud.tencent.com/document/product/267/31057).

> **Note:**DNS resolution must be performed over the public network on Linux/macOS/Windows.If the CNAME configuration failure persists, consult your domain name registrar.

### What if I don't add my own domain name?

If you activated the CSS service after October 17, 2018, you are required to add your own domain name for playback; otherwise, you cannot play back the live streaming content.

If you activated the service before then, CSS provided a default domain name for you, but we recommend that you replace it with your own domain name. Tencent Cloud has started phasing out the default domain names since December 31, 2018.

> **Note:**Default domain names are system domain names assigned by CSS in the format of `bizid.liveplay.com`` and `bizid.tlivecdn.com`.

### I have configured special items for the default domain name. Can my own domain name be resolved to the default one?

To use a new domain name, connect it to CSS from scratch. We recommend that you add and configure your own domain name in the CSS Console.

### Does the relayed live streaming in interactive live streaming also require adding of its own registered domain name?

If you use the relayed live streaming service, you need to add your own registered domain name for downstream playback of the relayed live stream.

### What certificate format should be filled in for live streaming HTTPS configuration?

Live streaming currently only supports access to certificates in PEM format. If your certificate is in another format, convert it to the PEM format.

### How to tell whether a certificate is in PEM format or DER format?

- **PEM format** : The text starts with  `-----BEGIN CERTIFICATE-----`  and ends with  `-----END CERTIFICATE-----` , and the content is a Base64-encoded ASCII code file. Common extensions are  `.pem, .crt, .cer, and .key.`

> **Note:**Apache and Nginx servers prefer this encoding format.

- **DER format:**  The file is in binary format and is not readable. Common extensions are  `.der ` and ` .cer` .

> **Note:**Java and Windows servers prefer this encoding format.

### What is the live streaming validity period of Tencent Cloud?

Playback authentication allows to configure the valid time parameter, which is mainly used when the distribution playback address has been provided to the platform, but the conference end time may change. At this time, to ensure that downlink playback is not affected, the authentication validity period of the playback domain name can be changed to achieve the delayed address expiration time.

The default validity period is 0. At this time, the expiration time is the time specified by txTime. The actual end time is the value of txTime plus the authentication validity period.


---
*Source: [https://www.tencentcloud.com/document/product/267/32478](https://www.tencentcloud.com/document/product/267/32478)*
