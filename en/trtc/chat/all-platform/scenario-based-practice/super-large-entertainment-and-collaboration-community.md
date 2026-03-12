# Super Large Entertainment and Collaboration Community

## Overview

Community is a powerful tool for entertainment collaboration. It supports the

**community**

-

**group**

-

**topic**

hierarchy where messages are isolated and a high number of members share the same set of friend relationships. In addition, it allows you to group members and set group permissions for viewing, speaking, and managing things.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/393cd4ab049d11f08c4452540044a08e.jpeg)

## Use Cases

### Finding like-minded people: a new way of user expansion

- Community supports the accommodation of a high number of enthusiasts in the **community**-**group**-**topic** hierarchy.
- A large, open community provides more refined topics, so that users can talk and interact more freely and proactively.
![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/398ae26d049d11f0aa8e525400bf7822.jpeg)

### Game-based social networking: higher user stickiness and engagement

Various community topics allow game players to access news, look for teammates, discuss plots, and share tips. Before the game, users can search for advice; during the game, they can always talk to others (through an always online chat room); after the game, they can dig deeper into the topics.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/39d289d0049d11f0aa645254007c27c5.jpeg)

### Fan marketing: an efficient operations tool

The diversified topics in a community can perfectly replace endless groups (such as group 1 of Shenzhen users, group 2 of Shenzhen users, group 1 of Guangzhou users, and group 1 of Shanghai users), eliminating the need to operate a number of tiring groups and making fan marketing more precise.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/3967557f049d11f08bc5525400454e06.jpeg)

### Organization management: a clear and layered communication method

All the members in an organization can join the same community, which supports hierarchical communication through the community hierarchy and permission settings.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/394f0c32049d11f08c4452540044a08e.jpeg)

## Technical Strengths

### A super large number of community members

The Tencent Chat community is nearly ten thousand times larger, perfectly meeting your needs to accommodate massive members in use cases such as finding like-minded people, fan marketing, game-based social networking, and organization management.

### Message reliability

The Tencent Chat community greatly increases the number of members while incorporating Tencent's powerful messaging capabilities. With the complete and reliable messaging system built on over 20 years of technology accumulation, it delivers over 99.99% message sending/receiving success rate and service availability, helping you easily handle hundreds of millions of concurrent requests.

### Message push performance

The Tencent Chat community adopts a new message push architecture with "fast and slow channels" plus "two-level push". This special type of architecture can well balance time and space for higher system push performance and lower terminal performance consumption. Users can enjoy the same message interaction experience in super-large groups as in general ones.

### Message status and user permission management

The Tencent Chat community offers extended capabilities such as message editing, recall, and forwarding. It allows setting muting, enabling do-not-disturb, counting unread messages, and editing profiles globally or by community or topic.

## Native SDK Integration Guide

> **Caution:**The community topic feature is supported only by the Chat native SDK Enhanced edition on v6.2.2363 or later. To use it, [purchase the Pro edition ãPro Plus edition or Enterprise edition](https://buy.tencentcloud.com/avc?from=17182).

The following describes community topic APIs for Android.

### Calling a community topic API

1. Call the `createGroup` API to create a topic-enabled community as instructed in the [Community Management](https://www.tencentcloud.com/document/product/1047/48172#.E5.88.9B.E5.BB.BA.E7.A4.BE.E7.BE.A4).
2. Call the `getJoinedCommunityList` API to get the list of created and joined communities.

> **Caution:**A community is used for managing group members but doesn't support sending or receiving messages. For more information on other community features, see the list of "other management APIs".

3. After the community is created successfully, call the `createTopicInfoCommunity` API to create topics as instructed in [Topic Management](https://www.tencentcloud.com/document/product/1047/36271?lang=zh).
4. Topic management also includes deleting a topic, modifying the topic information, getting the topic list, and listening for topic callbacks. In addition, topics support message sending and receiving for user communication. For more information on the APIs, see [Topic Message](https://www.tencentcloud.com/document/product/1047/36271?lang=zh).
5. Group community members: You can specify group information in group member custom fields to display community members in groups. To achieve this effect, all community members need to be pulled to the local for sorting by group. If the number of group members is large, it is recommended that you implement member grouping on the server side.

## Web SDK Integration Guide

> **Caution:**The community topic feature is supported only by the Chat web SDK on v2.19.1 or later. To use it, purchase the Pro edition ãPro Plus edition or Enterprise edition, go to the [**console**](https://console.tencentcloud.com/im/qun-setting), select **Group feature configuration**, and enable the **Community** feature.

The features of the community topic APIs are as follows:

### Downloading and configuring the demo source code

For a quick tryout of the Chat features, see [Android](https://www.tencentcloud.com/document/product/1047/45912).
The following describes how to use the community topic feature by calling the APIs:

### Calling a community topic API

1. Call the `createGroup` API to create a topic-enabled community as instructed in the [Community Management](https://www.tencentcloud.com/document/product/1047/48172#.E5.88.9B.E5.BB.BA.E7.A4.BE.E7.BE.A4).
2. Call the `getJoinedCommunityList` API to get the list of created and joined communities. A community is used for managing group members but doesn't support sending or receiving messages. For more information on other community features, see the ordinary group APIs.
3. After the community is created successfully, call the `createTopicInfoCommunity` API to create topics as instructed in [Topic Management](https://www.tencentcloud.com/document/product/1047/48172#creating-a-topic).
4. Topic management also includes deleting a topic, modifying the topic information, getting the topic list, and listening for topic callbacks. In addition, topics support message sending and receiving for user communication. For more information on the APIs, see [Topic Messages](https://www.tencentcloud.com/document/product/1047/48172#topic-messages).
5. Group community members: You can specify group information in group member custom fields to display community members in groups. To achieve this effect, all community members need to be pulled to the local for sorting by group. If the number of group members is large, it is recommended that you implement member grouping on the server side.

## References

- [Group Management](https://intl.cloud.tencent.com/document/product/1047/33530)
- [Group System](https://intl.cloud.tencent.com/document/product/1047/33529)
- [SDK and Demo Source Code](https://intl.cloud.tencent.com/document/product/1047/33996)
- [SDK Manual](https://web.sdk.qcloud.com/im/doc/en/TIM.html)
- [SDK Integration (Android)](https://intl.cloud.tencent.com/document/product/1047/34306)
- [SDK Integration (iOS)](https://intl.cloud.tencent.com/document/product/1047/34307)
- [SDK Integration (Web, Mini Program, and uni-app)](https://www.tencentcloud.com/document/product/1047/34309)

## Contact Us

If you experience any issues, [contact us](https://intl.cloud.tencent.com/document/product/1047/41676).


---
*Source: [https://trtc.io/document/49713](https://trtc.io/document/49713)*
