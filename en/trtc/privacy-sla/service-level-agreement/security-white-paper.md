# Security White Paper

## 1. Overview

Leveraging Tencent's years of experience in network and audio/video technologies, TRTC offers unified and standardized application programming interfaces (APIs) for group audio/video call and low-latency interactive live streaming solutions. It also provides software development kit (SDK) solutions compatible with mainstream operating systems and platforms for different industries and scenarios. With TRTC, you can quickly develop low-latency and high-quality interactive audio/video services at low costs.

As an industry leader in real-time audio/video PaaS cloud services, TRTC places great importance on data and user privacy security. TRTC always gives top priority to data and user privacy security and incorporates them in day-to-day development of security capabilities. To help you understand the security protection capabilities of TRTC, the following describes the security development and security compliance audit of TRTC PaaS services.

## 2. Security Compliance and Privacy Protection

Security compliance is the foundation for the development of TRTC, which meets the compliance requirements of different countries and industries. In addition to ensuring the security, compliance, availability, confidentiality, and privacy of the services it provides, TRTC also provides relevant support for you to meet your and your customers' compliance requirements, reduce repeated investment in audit work, and improve auditing and management efficiency.

TRTC has passed SOC 1, SOC 2, and SOC 3 audits, meets the requirements of China's Cybersecurity Classified Protection 2.0, and is certified to ISO 9001, ISO 20000, ISO 27001, ISO 27017, ISO 27018, ISO 27701, ISO 29151, CSA STAR, NIST CSF, BS 10012, and K-ISMS.

| Security Compliance and Privacy Protection | Description |
| --- | --- |
| ISO/IEC 27001: 2013 Information security management standard | ISO/IEC 27001: 2013 is a fundamental, internationally recognized standard for information security management systems. TRTC is certified to ISO 27001:2013, which reflects enterprise commitment to security and demonstrates that a set of scientific and effective systems for enterprise information security management is in place to provide reliable information services. |
| ISO/IEC 27017: 2015 Guidelines for information security controls applicable to the provision and use of cloud services | ISO/IEC 27017: 2015 is a practical standard for the information security of cloud services which provides specific security controls and their implementation guidelines for cloud service providers and customers. ISO 27017 is a supplementary standard to ISO 27002. It is designed to provide a security specification for cloud-based development and Ops for cloud vendors. TRTC is certified to ISO/IEC 27017, demonstrating sufficient information security management and protection capabilities. |
| ISO/IEC 27018: 2019 Code of practice for protection of personally identifiable information (PII) in public clouds acting as PII processors | ISO/IEC 27018: 2019 is a code of practice for protection of personally identifiable information in public clouds. Based on the ISO/IEC 27001 information security standard, it provides supplementary controls applicable to the protection of personally identifiable information in public clouds and strengthens public cloud capabilities for protection of personally identifiable information. TRTC has passed ISO 27018 certification, which demonstrates that enterprises have reached a high standard of industry best practices in protecting the security of enterprise data, intellectual property, documentation, and cloud IT systems. |
| CSA STAR Certification | Based on the Cloud Control Matrix (CCM) of Cloud Security Alliance (CSA), an international not-for-profit organization, CSA Security Trust Assurance and Risk (STAR) is a global cloud computing security certification which validates that cloud computing vendors meet the specific requirements in the field of cloud computing security. As an enhanced version of ISO/IEC 27001 for information security management systems, it visualizes cloud security issues and provides an intuitive framework for cloud vendors to assess their security management capabilities. TRTC has received CSA STAR Certification, demonstrating its cloud service protection capabilities. |
| SOC Audit | SOC reports are a series of reports related to internal controls of a service organization issued by professional third-party accounting firms in compliance with the applicable guidelines of the American Institute of Certified Public Accountants (AICPA). As a leading cloud service provider, Tencent Cloud adopted the 2017 version of the trust service criteria during the SOC audit in 2017, becoming the first provider in China to follow the 2017 version. The service certification report validates that TRTC has established and implemented effective internal controls and will regularly submit to third-party audits to ensure compliance with the requirements of the certification report. |
| Cybersecurity Classified Protection Certification | Cybersecurity Classified Protection 2.0 (CCP 2.0) came into force as of December 1, 2019. CCP 2.0 focuses more on active protection as well as the security and reliability, dynamic perception, and full audit from passive protection to the entire pre-event, mid-event, and post-event process, fully covering traditional information systems, basic information networks, cloud computing, mobile internet, IoT, big data, and industrial control systems. In line with CCP 2.0 and applicable regulations, Tencent Cloud public cloud TRTC PaaS service platform has been registered and evaluated for compliance with Cybersecurity Classified Protection Level 3, indicating that it provides services required for CCP compliance for enterprise users engaging in varied industries and businesses on the cloud platform. |

## 3. Data Security

Data security is one of the top concerns of TRTC. TRTC processes your data in a lawful and compliant manner as necessary to ensure data security. This section describes the data security technical controls and management policy implemented by Tencent Cloud and TRTC.

### 3.1 Data security policy

TRTC focuses on confidentiality, integrity, and high availability as prerequisites for the development of data security and incorporates data security management and development into its development practices. Tencent Cloud will always be committed to ensuring the availability, confidentiality, and integrity of your data as follows:

- **Availability**: It guarantees the high availability of data through Tencent Cloud's private network transfer protocol.
- **Confidentiality**: It prevents unauthorized access and eavesdropping.
- **Integrity**: It ensures the integrity of your data and protects the data from being forged.

TRTC provides all of its employees with regular training in data security, privacy compliance, and data encryption protection and enters into a confidentiality agreement with the employees to ensure the data availability, confidentiality, and integrity during daily operations.

### 3.2 High data availability

TRTC strives to provide highly available audio/video PaaS data services:

- **Globally distributed IDCs**: TRTC has many IDCs providing services globally. Any attack on one IDC cannot affect others or the overall services, implementing isolation-based protection.
- **Fault isolation and recovery**: If an IDC is subjected to malicious attacks that are difficult to prevent, such as a denial-of-service (DoS) attack, TRTC will reasonably handle the faulty server to ensure the overall service stability and availability.
- **DDoS mitigation**: TRTC has deployed anti-DDoS firewalls in each IDC and has sufficient capabilities and resources to control the risk of DDoS attacks.

### 3.3 Data collection

TRTC collects only data fields with the user's consent and only those necessary for the services and at the minimum granularity. User data collected by you such as application login information, identification, passwords, payment information, name, and address is kept by you, not on the TRTC platform.

### 3.4 Data masking

To protect your data privacy, TRTC masks the enterprise and personal information in the console before displaying it. This policy applies also to TRTC's internal systems and other products, such as the internal management platform, log printing, and monitoring and alarming channels.

### 3.5 Data usage and storage

- Your personal or enterprise user data, end user data, audio/video call data, and system operation and security data are categorized before being stored to ensure the compliance and security of your data.
- The development, test, and production environments are strictly isolated during TRTC development to ensure that your actual data will not be directly used for development and testing. In addition, the confidential information of you and users, such as passwords, will be stored in an encrypted manner.
- Developers and users who use the recording SDK on the on-premises server and the on-cloud recording feature provided by TRTC can record all or part of the call content, and all video/audio recordings are directly written to the storage server provided by the developers and users, not on the TRTC server for storage.

## 4. Security of TRTC PaaS Services

A low-latency and high-quality real-time interaction solution has demanding requirements for TRTC. In the process of developing audio/video PaaS services, TRTC fully assesses the technical and security risks to its architecture, follows the security risk control system in the compliance standard to the greatest extent, and implements it across the development of audio/video PaaS services so as to provide a set of high-quality, stable, and secure audio/video PaaS solutions for developers and users.

### 4.1 Security of the transfer network

Based on the Tencent Cloud private transfer network, TRTC has developed an audio/video platform that features ultra low-latency, high-quality transfer and supports real-time interaction for millions of users. The private transfer network is one of the core TRTC PaaS services. It offers compliant and secure service support for signaling connection, authentication, real-time scheduling, and real-time transfer of audio/video data on the TRTC terminal. In addition, to provide secure and stable services for developers and users, taking into account the security factors faced by the current internet environment, the architecture design of Tencent Cloud private transfer network incorporates the following controls.

| Security Control of Transfer Network | Description |
| --- | --- |
| Encrypted transfer | To ensure the confidentiality of audio/video data during transfer, TRTC provides built-in encryption and custom encryption for the transfer linkage. By default, built-in encryption is enabled globally for TRTC PaaS, covering the entire data linkage. This ensures the encryption security of data transfer. |
| Resource isolation | TRTC allocates dedicated resources for each TRTC application (SdkAppId) to ensure its independence of other projects and provide a secure and reliable guarantee of computational resources. After registering in the TRTC console, developers and users only need to perform simple operations in the console to create TRTC applications (SdkAppId) and allocate corresponding resources. |
| Room isolation | TRTC creates an independent isolation channel (Roomid) for the transfer of each type of audio, video, or message data. All rooms are logically separate, and only if a user uses the TRTC application with the same `SdkAppid` and the same room name can the user join the same channel. A room is created when a session starts and terminated when the session ends (when the last user leaves). In this way, transfer isolation is implemented at the room level. |
| Identity verification | When a user uses a TRTC application and connects to the TRTC PaaS services, TRTC will use the authentication information generated based on the `SdkAppid` and key to perform authentication for room entry, so as to help developers and users authenticate their users through strong authentication. |

### 4.2 Security of the SDKs

TRTC provides SDKs for different platforms such as iOS, Android, macOS, Windows, web, and mini program for integration as needed. It not only offers simple, secure, and stable audio/video SDKs that are easy to integrate for developers and users.

TRTC also strives to create compliant and secure audio/video PaaS services for developers and users, in an attempt to reduce their efforts to cope with compliance regulation and security threats to data and information.

| SDK Security Support | Description |
| --- | --- |
| SDK security and compliance | The reliability and security of TRTC SDKs are one of the guarantees of basic TRTC capabilities. During feature iteration, TRTC will fully assess the reasonableness of feature requirements in terms of compliance and privacy and their security risks, so as to ensure compliance with Tencent Cloud's compliance and privacy policy. During feature implementation, TRTC will perform adequate and necessary quality security tests and perform security checks where third-party SDKs or library files are imported or integrated, particularly compliance verification. |
| SDK content encryption | TRTC SDKs can use AES-128 symmetric keys to encrypt all audio/video data streams and messages at the data level. The encrypted data is sent to the nodes in the TRTC room over the Tencent Cloud private transfer protocol and eventually decrypted by the receiving terminal for rendering, ensuring data security and confidentiality during transfer. |
| Benefits of SDK security and compliance to developers | TRTC is dedicated to providing high-quality, secure, and lawful audio/video PaaS services for developers. TRTC SDKs come with built-in secure encryption to help developers and users improve the data security and privacy compliance of TRTC, meet customers' security and privacy requirements to the greatest extent, and reduce the development costs. |

### 4.3 Security of basic computing resources

The basic computing resources of TRTC consist of more than one hundred distributed IDCs deployed around the globe and Tencent Cloud CVM instances, which guarantee the high scalability, security, and availability of the basic computing resource environment of TRTC.

| Security of Computing Resources | Description |
| --- | --- |
| Security management of devices in IDCs | TRTC has developed a complete specification for the day-to-day management of devices in its IDCs. This specification defines detailed management measures and service implementation standards, which are fully reflected in the physical environment security, routine inspection, exception monitoring and reporting, and power resource support in the IDCs and meet the security compliance and basic security development requirements of TRTC. |
| Security of computing resources such as servers, databases, and middleware | Resources necessary for the operation of TRTC such as CPU, memory, and disks will be reasonably scheduled and allocated based on the business load. In actual security operations, TRTC develops appropriate security baselines and vulnerability management guidelines and implements in-depth threat detection to fully ensure the load security of basic computational resources in basic service scenarios. |
| DDoS mitigation | Given the significant impact of DDoS attacks on the system and business availability of TRTC PaaS services, TRTC leverages Tencent Cloud public cloud capabilities to deploy a DDoS mitigation scheme on core services. This scheme can detect and defend against DDoS attacks from the network and transport layers in real time. It monitors network traffic in real time, promptly cleanses the traffic as soon as an attack is detected, and enables protection in seconds for TRTC. |

### 4.4 Security of web APIs

To make it easy for developers to efficiently develop and manage their own audio/video businesses, TRTC provides some of the features in the console in the form of RESTful APIs for developers to call. The RESTful APIs provide the following security protection:

| Security protection | Description |
| --- | --- |
| Authentication | Before using TRTC RESTful APIs, developers need to first log in to the Tencent Cloud console and create their dedicated `SecretId` and `SecretKey` to ensure the uniqueness of the service provider's identity. |
| Input verification | The validity of developer request parameters will be verified on the TRTC server backend to filter out invalid parameters, so as to avoid common attack-prone vulnerabilities. |
| Transfer security | RESTful APIs only support the HTTPS protocol to ensure encryption of all API communications with SSL/TLS. This helps protect API credentials and transferred data. |
| API rate limit | There is a limit on the API request rate on the server, restricting API requests from malicious users while ensuring responses to normal user requests. |

## 5. Security Operations

Sticking to a reasonable security operations policy is the foundation for TRTC to ensure customer security, lawfulness, and compliance. Based on its business characteristics, TRTC guarantees business operations security in the following ways:

### 5.1  Security emergency response mechanism

Based on its own audio/video PaaS business characteristics, TRTC develops criteria for categorizing different security events, classifies services, and systematically assesses security and threat levels to ensure prompt and efficient handling of security exceptions according to the complete and efficient process.

To put it simply, TRTC handles feature security exceptions as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/cb235ed5f93711ed95155254007e6a5b.png)

### 5.2 Business continuity management

To provide low-latency and high-quality audio/video services to developers and users on a 24/7 basis, TRTC's professional and efficient development and Ops team is available for the availability support and management of audio/video services.

| Emergency Response Mechanism | Description |
| --- | --- |
| Business monitoring and alarming | TRTC has a 24/7 efficient monitoring mechanism in place to monitor the business service and system operation status. It has set up a complete set of unified monitoring tools to implement event monitoring and automated alarming for metrics such as the running status and resource load of system components involved in the business services such as applications, middleware, computational loads, databases, and network devices. In addition, a bot is leveraged to promptly notify the personnel on duty of any problems, so as to ensure prompt problem discovery and service recovery and availability. |
| Disaster recovery and redundancy | TRTC has developed solutions for the redundant architecture development of its core IDCs, taking into account the disaster recovery security of devices as well as the infrastructure layer, computational load, and network structure for various extreme business scenarios. Tencent Cloud public cloud servers are utilized to further guarantee the availability of the basic resources of TRTC in unexpected situations. |
| Continuity drill | To safeguard the continuous and efficient operation of important business systems and constantly improve its stability, TRTC regularly conducts security emergency disaster recovery drills for the IDC network, middleware, and business systems, carries out a review based on the data from each emergency drill, and improves the technical architecture, operation management process, and emergency plan. |

### 5.3 Security monitoring and anti-intrusion

In terms of implementing defense in depth to tackle threats, the TRTC security team will collect logs based on the principle of least privilege for security log analysis. Prompt alarms will be sent for the security exceptions identified based on the log data generated by the business every day, and security operations personnel will further perform association and traceability analysis review. The verified potential risks will be handled and tracked by the emergency response mechanism of TRTC to guarantee the security and stability of business systems.

## 6. Employee Security

TRTC strictly follows the principle of ensuring data and information security in the course of ordinary operations and management from the perspective of employee management. It fully recognizes the importance of employee security to overall security and considers whether the professional ethics and basic qualities of employees suit Tencent Cloud's values and meet security compliance requirements and business needs in the recruitment, onboarding, training, and separation processes.

| Process | Description |
| --- | --- |
| Recruitment | In the early stages of the employee recruitment process, TRTC assigns professional human resources specialists to verify the education and work experience of candidates to ensure that they are competent. |
| Onboarding | New employees must study the employee security policy to meet Tencent Cloud's requirements for security compliance awareness. In addition, an appropriate level of confidentiality agreement is entered into with each employee. Employees in a position exposed to important data are required to complete a detailed study of the security compliance policy and pass the exam before they can participate in the daily development of TRTC. |
| Employment | Employees are required to regularly attend security and privacy protection training and pass required examinations. Furthermore, TRTC irregularly organizes internal security- and privacy-related activities to constantly raise employees' security awareness. |
| Separation | Before departing the team, employees must complete the handover according to the established separation process and disable their access. TRTC will audit their performance during the advance notice period as specified in the confidentiality agreement and inform the employees of their information security and confidentiality responsibilities after separation. Employees may be separated on approval only after the work handover and data cleanup. |

## 7. Security Responsibility Sharing

As a real-time interactive audio/video PaaS cloud service platform, TRTC will manage the security of the platform and SDKs. Developers connecting to the services need to manage the security of their own application and system environment and reasonably use the security management feature of TRTC as needed to safeguard their information, platform, system, and network.

## 8. Summary

Providing secure, compliant, and stable audio/video PaaS services for customers is one of the top concerns for TRTC. It systematically pushes forward the implementation of the information security plan, performs its regulatory compliance obligations, and uses the plan as guidelines for product and service development during daily operations. In addition, TRTC actively studies new technologies with a view to implementing more efficient, secure, and automated security safeguards.

To guarantee its continuous high availability and protect the legitimate rights and interests of end users, TRTC continuously endeavors to create secure and compliant real-time interactive audio/video services.


---
*Source: [https://trtc.io/document/53568](https://trtc.io/document/53568)*
