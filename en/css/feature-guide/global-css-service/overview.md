# Overview

With the growing maturity of audio-visual technologies, the live broadcasting industry is seeing explosive growth around the globe. Chinese internet companies are leveraging on the prior globalization experience of service sector companies and entering the global market en masse. Leading platforms are internationalizing their products to increase competitiveness, while smaller platforms are seeking out new avenues after finding it hard to survive in the aggressive domestic arena. Meanwhile, the battle overseas is no less intense. The 3 giants, YouTube, Periscope and Facebook, may have conquered more than their fair share of the market, but they did leave a significant portion untapped for small and medium platforms. Tencent Cloud continues to strengthen global live broadcasting resource reserves and optimize live broadcast acceleration performance with the goal of helping live broadcasting platforms win international markets.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/40603a0730e411ee8de9525400c56988.png)

In addition to push and playback, a complete live broadcasting service should also include authentication, transcoding, screencapturing, recording, callback, porn detection, DRM, and other features. The figure below shows the basic feature modules of Tencent Cloud's Global CSS solution.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4062612e30e411ee872a525400cea498.png)

The basic features of global live broadcasting are generally the same as those of domestic live broadcasting. However, there are more challenges overseas mainly due to the wider geographical area, more complicated network environments, and lower cross-border network quality. In order to reduce the latency and lag and improve service stability and reliability, Tencent Cloud has optimized CSS’s **architecture, network, security, and resources** for global live broadcasting scenarios.

### Deployment of Multiple Central Nodes

**Tencent Cloud has built a lot of central IDCs in Hong Kong (China), Thailand, Singapore, Germany,Silicon Valley, South Africa, and South Korea and continues expanding into more countries and regions.** These central IDCs hosts all the modules needed for global live broadcasting and are deployed in a distributed manner with a decentralized architecture to better serve global end users and guarantee fast failover upon any IDC exceptions. Taking into account the impact of low cross-border network quality and stability on live broadcast latency and lag, central nodes are interconnected through Direct Connect. Mainland China central nodes are interconnected with those outside of Mainland China through Direct Connect lines with the Hong Kong node as a relay. The overall architecture is as shown below:

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c11d182f612d11efb36952540075b605.png)

To intuitively demonstrate the acceleration performance of overseas central nodes, we compare the statistics of Chinese end users watching US live streams. As you can see in the figure below, acceleration via Direct Connect keeps the lag rate low and the network stable.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/405f2caf30e411ee872a525400cea498.png)

### Acceleration in Edge Regions

Central nodes can perfectly meet the needs of local end users, but the needs of those in countries and regions without central nodes should also be catered for. Due to various restrictions, no central nodes have been built in these regions, and thus cache nodes are required. Such countries and regions are called edge regions, where the cross-border network quality is relatively low, and the lagging rate of cross-region pull is quite high. Examples of such regions include Malaysia, Indonesia, the Middle East, India, Africa, and South America. For these edge regions, Tencent Cloud sets priorities for service modules. The first priority is ensuring that valid local users can watch live streams without the need of cross-border transmission of local data. Services of other modules are re-pulled from edge servers to central nodes and finally implemented on central nodes. **As you can see in the figure below, after local node acceleration is enabled in an edge region, the lagging rate is significantly reduced, and the acceleration performance is much higher than that of other service providers in the industry.**

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ad77723731a511ee9bd25254005c1bd1.png)

### Optimal Access and Failover

Similar to Mainland China, other regions also often have multiple ISPs, such as DTAC, AIS, and TRUE in Thailand, Chunghwa Telecom, Taiwan Mobile, and so-net in Taiwan (China), as well as Telkomsel, XL, and INDOSAT in Indonesia, and cross-ISP access speed is subject to bandwidth and resources. To improve the access experience of end users on networks operated by different ISPs, Tencent Cloud's scheduling system allows them to access their own ISPs. Plus, its cache nodes built locally generally boast BGP lines for access and peering links with local ISPs.
For example, for end users of three ISPs (DTAC, AIS, and TRUE) in Thailand, the central scheduling system collects a large amount of foreign IPs and ISP information and automatically schedules them to the nearest CDN nodes based on their IPs, with a recognition accuracy of over **99.5%**. Switching between data centers upon exception is also supported. If the monitoring and detecting nodes find an exception in a region, the system will automatically switch to the most optimal data center.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/405ed43a30e411ee8de9525400c56988.png)

### Network Transmission Optimization

When live streams are transmitted on overseas networks, the traditional TCP transmission method cannot guarantee low transmission latency. Due to the long distance of overseas transmission, limitations of international egress bandwidth, and frequent network quality fluctuations, TCP is not suitable for overseas data transmission as it is more time-consuming to be upgraded and optimized and has a higher packet loss rate. Tencent Cloud uses Quick UDP Internet Connections (QUIC) to improve the reliability of data transmission on overseas networks. Upper-layer data proxy acceleration with QUIC is implemented at the application layer, which means that appropriate adjustments to parameters or congestion algorithms can take effect immediately to efficiently fix high latency and high packet loss rate, avoid congestions, and reduce the round-trip time (RTT). **Tests with actual data show that Tencent Cloud's optimized scheme reduces the connection time by 40% and the lagging rate by 20% on average compared to the traditional TCP scheme.**

****

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4062251b30e411ee872a525400cea498.png)

The figure below shows a comparison of lags for global viewers watching a live stream pushed by a host in UAE to the UAE cache node. You can see that the lags remain low when the stream is accelerated via QUIC.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/405e12af30e411ee9bd25254005c1bd1.png)

### Massive Resource Reserve

In addition to technical architectures and solutions, resource reserves are also critical to live broadcasting services. Without the support of global resources, all technologies are merely theories. Tencent Cloud has put in place a globalization strategy and made long-term investments in the overseas market. As we can see in the Tencent Cloud global node distribution chart at the start of the document, **Tencent Cloud has built more than 2000+ transmission nodes in over 50 countries and regions, with a total bandwidth of 100+ Tbps across 50+ global ISP partners and 1000+ overseas cache nodes.** In addition, Tencent Cloud works with multiple ISPs in the same region, ensuring there are at least 3 copies of disaster recovery backup data available in each egress to achieve service stability and reliability. For more information, see [CDN](https://intl.cloud.tencent.com/document/product/228/2941?from_cn_redirect=1#nodes-outside-mainland-china).

### How to Activate

The Global CSS service can be directly activated in the [CSS console](https://console.tencentcloud.com/live).

- If you don't have a Tencent Cloud account yet, you need to sign up first as instructed in [Signing up for a Tencent Cloud Account](https://intl.cloud.tencent.com/document/product/378/17985) and then [apply for activation of the CSS service](https://intl.cloud.tencent.com/document/product/267/30410).
- If you already have a Tencent Cloud account and have activated CSS, you can proceed directly to the next step.

Go to the CSS console, select [**Domain Management**](https://console.tencentcloud.com/live/domainmanage) on the left sidebar, and click **Add Domain**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/98ff3339e10a11eeb1eb525400b5f95f.png)

In the pop-up window, select the type as **Playback Domain**, select the corresponding **Acceleration Region**, and enter the **Domain Name** that needs to be accelerated.


---
*Source: [https://www.tencentcloud.com/document/product/267/31567](https://www.tencentcloud.com/document/product/267/31567)*
