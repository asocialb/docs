# Obtaining a FairPlay Certificate

To encrypt your content with FairPlay, you need to obtain an FPS deployment package from Apple and upload the following files to SDMC’s server.

- FPS certificate file `(.der` or `.cer`)
- Private key file `(.pem`)
- Private key password file `(.txt`)
- Application secret key (ASK) (`.txt`)

## Directions

### Step 1. Create an Apple developer account and request an FPS package

2. At the bottom of the [FairPlay Streaming](https://developer.apple.com/streaming/fps/) page, click **Request FPS Deployment Package**, and log in with your Apple developer account.
3. Fill out the form and submit it. After your request is approved, Apple will send you a package containing the FPS certificate generation guide.

> **Note**When asked if you have implemented and tested Key Security Module (KSM), you can paste the answer below:I am using a 3rd party DRM company and the company has already built and tested KSM

### Step 2. Create a private key and a certificate signing request (CSR)

> **Note**Make sure OpenSSL is installed on the computer or server environment where this process is performed.

1. **Create a private key file (**`privatekey.pem`**)**:
  1.1. Run the command below to create a private key file:

```
openssl genrsa -aes256 -out privatekey.pem 1024
```

2. **Create a CSR file**:
  2.1. Run the command below (you can modify `-subj`):

```
openssl req -new -sha1 -key privatekey.pem -out certreq.csr -subj "/CN=SubjectName/OU=OrganizationalUnit/O=Organization/C=US"
```

  2.2. Enter the private key password configured in the [previous step](#step1_1).

### Step 3. Generate the FPS certificate

1. Log in to [Apple Developer](https://developer.apple.com/) and click [Certificates, IDs & Profiles](https://developer.apple.com/account/ios/certificate/).
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d8e295876e11ee9cb9525400fc26b2.png)
2. Click **+** to enter the **Create a New Certificate** page.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d8bc0a876e11ee9cb9525400fc26b2.png)
3. Select **FairPlay Streaming Certificate** and click **Continue**.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d4c0ee876e11ee8fb75254000524f8.png)
4. Click **Choose File**, select the `certreq.csr` file created, and click **Continue**.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d87839876e11eeafb5525400a39a17.png)
5. Copy and save the ASK, paste it in the input field below, and click **Continue**.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d685b7876e11ee889d525400b2195a.png)
6. A window will pop up to confirm that you have saved the ASK. Click **Generate**.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d8517f876e11eeafb5525400a39a17.png)
7. After the above steps are completed, the FPS certificate generated will appear in the certificate list.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d5641c876e11ee9cb9525400fc26b2.png)
8. Click **Download** to download the FPS certificate (`fairplay.cer`).
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d8fd44876e11eeafb5525400a39a17.png)

### Step 4. Upload the certificate to SDMC’s platform

1. Log in to [SDMC’s DRM console](https://www.xmediacloud.com/contact-us/) and find DRM settings in the menu.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90e91581876e11ee9cb9525400fc26b2.png)
2. On the DRM settings page, find **FPS Cert Registration**, and click **Update**.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d6e128876e11ee889d525400b2195a.png)
3. Upload the FPS certificate, private key file, private key password file, and ASK file, and click **OK**.
![](https://staticintl.cloudcachetci.com/cms/backend-cms/90d27e34876e11ee9cb9525400fc26b2.png)

> **Note**If you have any questions, please [submit a ticket](https://console.tencentcloud.com/workorder/category).


---
*Source: [https://www.tencentcloud.com/document/product/267/48069](https://www.tencentcloud.com/document/product/267/48069)*
