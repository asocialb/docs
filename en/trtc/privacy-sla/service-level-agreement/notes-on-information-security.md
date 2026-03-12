# Notes on Information Security

> The following statement is hereby made for this document:
> 
> 
> 1.     This document is intended to provide an overview of Tencent Cloud's security measures for Tencent Real-Time Communication (TRTC). It explains how to manage information and protect the security of your and end users' data. If you have any mandatory requirements, we recommend you enter into a service level agreement (SLA) with Tencent Cloud. Tencent Cloud disclaims any express or implied undertakings and warranties as to the content of this document.
> 
> 
> 2.     This document only involves "part of" the technical security features among the wide range of security features.
> 
> 
> 3.     This document is not intended as a reference document for national or industry-specific information security standards or requirements.
> 
> 
> 4.     This document has been adapted for readability. In the event of any ambiguity or inaccuracy, refer to Item 1.
> 
> 
> 5.     Tencent Cloud reserves the right to interpret this document.

## 1. Overview

TRTC has passed and meets the security requirements of the following certifications:

- ISO 9001 Certification
- ISO 20000 Certification
- ISO 27001 Certification
- ISO 27017 Certification
- CSA STAR Certification
- GDPR

For more information, see [Compliance](https://www.tencentcloud.com/document/product/647/45281).

## 2. Information Security Protection

The management security and technical security requirements of TRTC comply with the General Data Protection Regulation (GDPR).

### 2.1 Information and data security

Communications between users and the TRTC server are protected by protocols such as Tencent Cloud's private transfer protocol, Transport Layer Security (TLS), and Web Socket Secure (WSS). During transfer, TRTC has no key that can decrypt the transferred information. The call content can be decrypted only with your authorization key on the terminal device (such as the client application or the on-premises recording server).

### 2.2 Data availability

- Globally distributed IDCs: TRTC has many IDCs providing services globally. Any attack on one IDC cannot affect others or the overall services, implementing isolation-based protection.
- Fault isolation and recovery: If an IDC is subjected to malicious attacks that are difficult to prevent, such as a denial-of-service (DoS) attack, TRTC will reasonably handle the faulty server to ensure the overall service stability and availability.
- DDoS mitigation: TRTC has deployed anti-DDoS firewalls in each IDC and has sufficient capabilities and resources to control the risk of DDoS attacks.

### 2.3 Data categorization and storage

| Personal Information | Purpose | Legal Basis |
| --- | --- | --- |
| Data configured in the console: The TRTC application ID and name, whether recording and relayed push are enabled, and the selected billing mode | For billing purposes, we use this information to determine your usage of the corresponding feature.Note that such data is stored in our Elasticsearch Service (ES) feature. | We will process this information as necessary to make the corresponding feature available to you as part of our performance of the contract entered into with you. |
| Backend log data: The user ID, room ID, client IP and SDK version, and OS type of any participants in live streaming events | We use this information to ensure that corresponding features run as required and to perform troubleshooting.Note that such data is stored in our ES feature. | We will process this information as necessary to make the corresponding feature available to you as part of our performance of the contract entered into with you. |
| Dashboard information: Audio/Video quality information during call: The end user's `APPID`, data about the features controlled by the end user (enabling/disabling audio/video), room entry/exit, room ID, muting feature, CPU utilization, memory usage, network latency, data packet loss, resolution, bitrate, frame rate, and volume level | We use this information to ensure that corresponding features run as required and to perform troubleshooting.Note that such data is stored in our ES feature. | We will process this information as necessary to make the corresponding feature available to you as part of our performance of the contract entered into with you. |
| SDK log data (of the end user): The user ID, room ID, client SDK version number, and the OS type of the TRTC room | We use this information to ensure that corresponding features run as required and to perform troubleshooting.Note that such data is stored in our ES feature. | We will process this information as necessary to make the corresponding feature available to you as part of our performance of the contract entered into with you. |
| UIN | We use this information to determine your usage of the corresponding feature.Note that such data is stored in our ES feature. | We will process this information as necessary to make the corresponding feature available to you as part of our performance of the contract entered into with you. |
| SDK `APPID` (created for different applications with your UIN) | As part of the corresponding feature, we use this information to determine the usage of your application.Note that such data is stored in our ES feature. | We will process this information as necessary to make the corresponding feature available to you as part of our performance of the contract entered into with you. |
| Troubleshooting data: The end user's `APPID`, data about the features controlled by the end user (enabling/disabling audio and video), room entry/exit, room ID, CPU utilization, memory usage, network latency, data packet loss, resolution, bitrate, frame rate, and volume level | We use this information to detect and locate the issues encountered by the end user for troubleshooting.Note that such data is stored in our ES feature. | We will process this information as necessary to make the corresponding feature available to you as part of our performance of the contract entered into with you. |

TRTC offers the on-premises recording and on-cloud recording features, which allow you to record all or part of call content. During the use of the on-cloud recording feature, all audio/video call recordings are stored in your cloud storage service, and TRTC does not store your audio/video files.

TRTC stores the above data in the Chinese mainland for Tencent Cloud customers and in the Singapore IDC for Tencent Cloud International customers to meet the storage requirements for data security compliance.

### 2.4 Access authorization

When entering a TRTC room, end users are required to authenticate with a dynamic signature, so as to protect your right to use of the Tencent Cloud service from malicious attacks. For more information, see [UserSig](https://www.tencentcloud.com/document/product/647/35166).

### 2.5 Access control

TRTC implements strict access control and management for all internal systems. All users have an independent internal account and authorization system and must pass two-factor authentication. All access records are recorded.

All servers involving user data are strictly audited and protected. TRTC will only access your server when necessary. If TRTC has to access your server for security reasons, it will get temporary authorization first. The whole process will be recorded, and all operation records will be kept.

### 2.6 Internal security audit

We will store personal data processed in connection with the corresponding features as described below:

| Personal Information | Retention Policy |
| --- | --- |
| Your temporary key information: The SDK `APPID`, username, and private key | We retain this data during your use of the corresponding feature. If your use of the feature is terminated or your account is deleted, we will delete this data within seven days. |
| Application-related customer log data: The SDK `APPID`, application name, tag, service status, creation time, and operation | We retain this data during your use of the corresponding feature. If your use of the feature is terminated or your account is deleted, we will delete this data within seven days. |

You can request deletion of such personal data in accordance with the DPSA.

### 2.7 Employee security awareness training

TRTC provides all of its employees with regular training in information security awareness and security compliance. All employees receive regular courses and training in information confidentiality awareness on an annual basis.

### 2.8 Handling of Violations

TRTC employees are required to comply with the confidentiality agreement and internal security policy. Appropriate actions will be taken in case of any violation, including but not limited to strengthened training and education, termination of employment, and pursuit of other legal liability.

### 2.9 Potential vulnerabilities

If you identify any potential vulnerability in the TRTC platform, you are free to submit a ticket, and our technical experts will promptly respond and address the potential vulnerability.

To make it easier to locate and verify the vulnerability, you need to submit the following content:

- Your contact information
- A description of the feature affected by the identified potential vulnerability
- The necessary steps and methods needed to locate and reproduce the potential vulnerability.


---
*Source: [https://trtc.io/document/53569](https://trtc.io/document/53569)*
