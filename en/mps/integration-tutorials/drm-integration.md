# DRM integration

## Overview

Digital Rights Management (DRM) is a system designed to protect the copyright of digital content through the application of encryption and authorization verification techniques. Its primary functions include:

- Content Encryption: Encrypting audio, video, and other digital content to prevent unauthorized distribution;
- Permission Control: Implementing granular permission management through license management, including control over playback frequency and device binding;
- Secure Transmission: Ensuring the integrity of content during the distribution process.

Media Processing Services (MPS) offers video-on-demand encryption services based on DRM encryption protocols such as Widevine, FairPlay, and PlayReady. By integrating standardized encryption technology with third-party Key Management Systems (e.g., SDMC, DRMtoday, etc.) in depth, it achieves decoupling of content encryption and key management, comprehensively ensuring the security of user content. The DRM encryption services provided by Media Processing focus on content security processing, while key generation, storage, distribution, and license management are provided by third-party DRM service vendors.

The following will illustrate the process of integrating Media Processing's DRM encryption services using DRMtoday as an example.

## Integration Process

### Preparation

Activate and configure a third-party DRM service, taking DRMtoday as an example.

#### Step One: Register for the Service

1. Navigate to the official website of [DRMtoday Provider](https://castlabs.com/drmtoday). DRMtoday provides a free trial and commercial service purchasing instructions on its website.
2. Click **Get your FREE trial today** for the trial.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd54bea9fe4411ef9f695254007c27c5.png)

3. Users must register with a corporate email and create an organization to access the next page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd51d9c1fe4411efa17e525400454e06.png)

#### Step Two: Service Configuration

(1) Configure API Account

1. Select **Members/Users** from the left sidebar.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bce99c24fe4411efa17e525400454e06.png)

2. Click **Add API account**, select options as needed, ensure accuracy, and click **Add member** to confirm.

> **Note:**Upon successful saving, a password prompt will appear. Users are advised to securely store this password for future use.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd604e15fe4411efaf3d52540099c741.png)

##### （2）Configuring FairPlay Certificates

Go to left sidebar, choose **DRM settings**, input FairPlay certificate info, and click **Save Settings**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd7b03b5fe4411efbf88525400e889b2.png)

##### （3）Configure the secret key "seed".

1. Select **Key Seeds** from the left sidebar.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd3f335bfe4411efa49152540044a08e.png)

2. Click on **Add seed**, you can generate a random seed by clicking **Random**. Two seeds need to be generated: one for the Key seed and another for the IV seed.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd0577e5fe4411efa17e525400454e06.png)

##### (4) Configuring CPIX

> **Note:**Due to the media processing service backend interacting with DRM vendors to retrieve key information via the [CPIX protocol](https://dashif.org/docs/CPIX2.2/Cpix.pdf), it is necessary to configure CPIX.

1. Select **Ingest Settings** from the left sidebar.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd4be4a1fe4411efbf88525400e889b2.png)

2. Click on **Add CPIX config**, where the Key seed and Initialization vector (IV) seed are the seeds configured in the aforementioned step (3). The Stream type mapping and the four options below can be selected according to business needs to determine the appropriate key generation rules.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bcf526e1fe4411ef8c825254001c06ec.png)

##### (5) Configuring Certificate Authentication

Navigate to the **License Delivery Authorization** in the left sidebar, where users can select the appropriate certificate authentication method based on the requirements.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/bd1cf445fe4411efa49152540044a08e.png)

#### Step Three: Generating the Key Request URL

To retrieve key information, users must set up a key request URL for the media processing service. This URL enables the service to request keys from the DRM vendor. After the DRM vendor authenticates the request, it sends back the keys in CPIX format. The media service uses these keys to decrypt media. For instructions on creating a key request URL, see the [DRMtoday documentation](https://fe.drmtoday.com/documentation/integration/). A script for generating this URL is provided for reference.

```
#!/bin/bash# First request to get ticketTICKET_RESPONSE=$(curl 'https://auth.drmtoday.com/cas/v1/tickets' \\  -d "username=<API account>&password=<API account password>" \\  -s -D -)# Extract location header if status is 201if echo "$TICKET_RESPONSE" | grep -q "HTTP.*201"; then    TICKET_URL=$(echo "$TICKET_RESPONSE" | grep -i "Location:" | cut -d' ' -f2 | tr -d '\\r')        # Second request using the ticket URL    TICKET=$(curl "$TICKET_URL" \\      -d 'service=https://fe.drmtoday.com/frontend/cpix/v1/<Organization UUID>/ingest/<CPIX ID>')else    echo "Failed to get ticket. Status code was not 201"    echo "$TICKET_RESPONSE"    exit 1fi# Concatenate the service URL with the ticketSERVICE_URL="https://fe.drmtoday.com/frontend/cpix/v1/<Organization UUID>/ingest/<CPIX ID>?ticket=$TICKET"echo $SERVICE_URL
```

##### （1）API account

Select **Members/Users** from the left sidebar. The API account mentioned in the script refers to the API account configured in Step 2, and the "API account password" corresponds to its password.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fe101ef7fe4611ef9f695254007c27c5.png)

##### （2）Organization UUID

Select **API endpoints** from the sidebar on the left. The Organization UUID is displayed in the top right corner of the page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0d7a4046fe4711efaf3d52540099c741.png)

##### （3）CPIX ID

Select **Ingest Settings** from the left sidebar, where you can view the CPIX information created in Step Two. The ID of the CPIX config is the CPIX ID required in the script.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0d8fc99ffe4711efa49152540044a08e.png)

After setting up the script correctly, you can start a request to get the secret key URL.

> **Note:**Remember: The URL expires, so it's recommended to regenerate it regularly.

### Initiating Encryption Tasks via API

To initiate processing tasks for media files located in URL video links or within COS, please refer to the API documentation [Initiating Media Processing](https://www.tencentcloud.com/document/product/1041/33627).

```
POST / HTTP/1.1Host: mps.tencentcloudapi.comContent-Type: application/jsonX-TC-Action: ProcessMedia
```

```
{    "InputInfo": {        "Type": "URL",        "UrlInputInfo": {            "Url": "https://test-<appid>.cos.ap-nanjing.myqcloud.com/mps_input/test.mp4"        }    },    "OutputStorage": {        "Type": "COS",        "CosOutputStorage": {            "Region": "ap-nanjing",            "Bucket": "test-<appid>"        }    },    "OutputDir": "/mps_output/drm/",    "MediaProcessTask": {        "AdaptiveDynamicStreamingTaskSet": [            {                "Definition": <definition id>,                "DrmInfo": {                    "Type": "widevine",                    "SpekeDrm": {                        "ResourceId": "test123",                        "KeyServerUrl": "<DRM key server url>",                        "Vector": "<IV>",                        "EncryptionMethod": "cbcs",                        "EncryptionPreset": "preset0"                    }                }            }        ]    },    "TaskNotifyConfig": {        "NotifyType": "URL",        "NotifyUrl": "<notify url>"    }}
```

Response Example:

```
{    "Response": {        "TaskId": "24000035-WorkflowTask-cf405e365e75efb2a7bfdef514cc17dbtt195964",        "RequestId": "a7ba06b6-6810-4343-b55d-3afcc3dac64c"    }}
```

Example Description: TaskId serves as a unique task identifier, which can be utilized for querying and managing tasks.

#### Type

Encryption types, permissible values include:

- **simpleaes**: AES-128 encryption, exclusively compatible with HLS. Supported segment formats include TS and MP4. Only segmented mode is permitted; single-file mode is not supported.
- **fairplay**: Solely applicable to HLS. The segment format is restricted to MP4, with support for both segmented and single-file modes.
- **widevine**: Compatible with both HLS and DASH. Segment format is limited to MP4 (for HLS output, either segmented or single-file mode is available; for DASH output, only single-file mode is permitted).
- **playready**: Supports both HLS and DASH. Segment format is confined to MP4 (for HLS output, either segmented or single-file mode is supported; for DASH output, only single-file mode is allowed).

#### SpekeDrm

##### （1）ResourceId

Resource tagging supports 1-128 characters, including numbers, letters, underscores (_), and hyphens (-). The ResourceId can be perceived as an ID for a set of cryptographic keys, which can be utilized to encrypt multiple distinct media streams. We can view all the ResourceIds we have created on the DRMtoday console.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/96e45612fe4711efa21c525400bf7822.png)

##### （2）KeyServerUrl

The key request URL is made in step three of the preparatory phase.

> **Note:**Different DRM providers have varying substream limits, with Pallycon allowing up to 5 and DRMtoday up to 9.

##### （3）Vector

Encryption Initialization Vector (32-byte string).

##### （4）EncryptionMethod

Encryption Method: By default, FairPlay uses cbcs, while PlayReady and Widevine default to cenc.

Please note that there are differences in the encryption methods supported by various DRM standards:

- cbcs: Supported by PlayReady, Widevine, and FairPlay.
- cenc: Supported by PlayReady and Widevine.

##### (5) EncryptionPreset

Rules for encrypting substreams, with the default being preset0.

- preset0: All substreams are encrypted using the same key.
- preset1: Each substream is encrypted using a different key.

### Playback Verification

Playback can be referenced through the [DRMtoday Player Official Documentation](https://fe.drmtoday.com/documentation/integration/player_integration.html). Below, we illustrate how to play encrypted streams using the [DRMtoday Official Player](https://demo.castlabs.com/#/player/) as an example.

1. Click **Try Your Stream**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/275cd33bfe4811ef83195254005ef0f7.png)

2. Fill in configuration information.
  2.1. Firstly, enter the URL of the stream to be played in the "Content URL" field. If it is an HLS stream, select "HLS" for the Type; if it is a DASH stream, choose "MPEG-DASH".

![](https://staticintl.cloudcachetci.com/cms/backend-cms/275d21e6fe4811efbf88525400e889b2.png)

  2.2. Next, configure the client authentication information. For the DRM Environment, select DRMtoday PRODUCTION. The Merchant should be the Organization UUID found in the API endpoints, and the User ID should be the Members ID from Members/Users. The Session ID can be any value, while the Asset ID should be the ResourceId specified when initiating the encryption task. After configuring the player, click **Load** to play the encrypted stream normally.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7143e220fe4811efa49152540044a08e.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/7aa025b8fe4811efbf88525400e889b2.png)


---
*Source: [https://www.tencentcloud.com/document/product/1041/68547](https://www.tencentcloud.com/document/product/1041/68547)*
