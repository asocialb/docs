# Push Message Categorization

Every vendor has a message categorization mechanism, and different types have different push strategies. If the push requirement is of the Chat type and timely delivery is desired, it is necessary to set your application as the corresponding push type according to vendor rules. It will be categorized as a system message type or an important message type with high priority. Conversely, offline push will not be pushed to the device in a timely manner.

> **Note:**Only Chat type messages need to be configured as system message types or important message types for timely delivery. Some marketing or advertising type pushes, which do not require immediate delivery, can arrive at the device within a certain period, and do not need to be configured as a system message type.Vendors have restrictions on the daily push quantity and push frequency for applications, which can be viewed in the vendor console regarding the daily limit on push quantity and restrictions.Do not arbitrarily configure message types. Configuration that does not meet the standard may result in the vendor freezing your account.

## Huawei

Starting from EMUI 10.0, Huawei Push intelligently categorizes notification messages into two levels: **Service and Communication** and **Information Marketing**. Versions earlier than EMUI 10.0 did not categorize notifications, having only one level where all messages were displayed through the **Default Notifications** channel, equivalent to Service and Communication on EMUI 10.0. The daily push quantity for Information Marketing messages will be subject to an upper limit management based on the application type from January 5, 2023, while Service and Communication messages will not be limited in daily push quantity.

##### Customized Self-Categorization Push Method

- Apply for Self-Categorization Benefits.
- Push messages carry the category field, for details see [setAndroidHuaWeiCategory](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#ad9dea3cb382c0c1a3c1a63738697fc1f). For console settings, see the Category field in Certificate Editing. Setting either one is sufficient.

For more information, see [Message Categorization Standards](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-classification-0000001149358835) or [Push Quantity Management Rules](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/message-restriction-description-0000001361648361?ha_source=hms5).

## HONOR

The HONOR Push Service will classify push messages into service communication and information marketing based on application type, message content, and message sending scenario. Message notifications will be categorized as information marketing by default, with a daily push limit. You can apply for self-categorization benefits to classify messages yourself.

##### Customized self-categorization push method

- [Apply for Self-Categorization Benefits](https://developer.honor.com/cn/docs/11002/guides/notification-class#%E8%87%AA%E5%88%86%E7%B1%BB%E6%9D%83%E7%9B%8A%E7%94%B3%E8%AF%B7).
- Push messages carry the importance field, for details see [setAndroidHonorImportance](https://im.sdk.qcloud.com/doc/zh-cn/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a3167229118ad659378b2066821935c79). For console settings, see the importance field in Certificate Editing. Setting either one is sufficient.

For more information, see [Message Categorization Standards](https://developer.honor.com/cn/docs/11002/guides/notification-class) or [Push Quantity Management Rules](https://developer.honor.com/cn/docs/11002/guides/notification-push-standards).

> **Note:** Honor Phone push notifications are related to the system version.Currently, the Honor channel only supports Honor devices in China with Magic UI 4.0 or above and those overseas with Magic UI 4.2 or above.Honor devices below the versions mentioned can use the Huawei Manufacturer for push access.For more information, see [Product Description](https://developer.hihonor.com/cn/kitdoc?category=%E5%9F%BA%E7%A1%80%E6%9C%8D%E5%8A%A1&kitId=11002&navigation=guides&docId=introduction.md&token=).

## vivo

Push messages are classified into system messages and operational messages, with different push effectiveness and policies. System messages also undergo a secondary correction through the vendor's intelligent classification; if it's incorrectly identified as a non-system message, it will automatically be corrected as an operational message. False judgments can be corrected by email application feedback. Moreover, message pushing is also subject to a daily limit, determined by the app's subscription statistics with the manufacturer.

##### Customized Self-Categorization Push Method

Push messages carry the category field. For details, see [setAndroidVIVOCategory](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#ae7341caa3c58aec949cf186cb25af591). For console settings, refer to Certificate Editing Category field. Setting one of the two is sufficient.

For more details, see [Push Message Classification Description](https://dev.vivo.com.cn/documentCenter/doc/359) or [Push Message Restriction Description](https://dev.vivo.com.cn/documentCenter/doc/695).

## OPPO

Based on the content of the push messages, notifications are classified into two major categories: Communication and Service, and Content and Marketing, with different push effects and policies. Communication and Service messages are those that a user pays certain attention to and wants to receive in time. The Communication and Service message type needs to be applied for via email, and the Content and Marketing push quantity is limited. Note: If you have previously Activated Private Message Channel Permissions, please refer to "Old Rules".

New Rules

Old Rules (applicable to existing users only)

##### 1ãCustomized Self-Categorization Push Method

- [Channel Permission Application](https://open.oppomobile.com/new/developmentDoc/info?id=13189).
- Push messages carry the category field, for details see [setAndroidOPPOCategory](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a6a62542254c53626b81ce24380b0a2fb). For console settings, see the Category field in Certificate Editing. Setting either one is sufficient.
- If your application belongs to the sub-categories of chatting and socializing, phone SMS, or office applications, and the applied message type is "Chat Class Message", you can also apply for notification bar message alert level settings. For details see [setAndroidOPPONotifyLevel](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a1fd2e7d168b5412fc263274842855c57). For more information, see [Strong Alert Application](https://open.oppomobile.com/new/developmentDoc/info?id=13189).

For more information, see [Message Categorization Standards](https://open.oppomobile.com/new/developmentDoc/info?id=13189).

**2ãPrivate message template application is required only for "communication and service messages".**

- [Private message template application](https://open.oppomobile.com/documentation/page/info?id=12391).
- Push message carrying Template ID, template title, and content. For details, see [V2TIMOfflinePushInfo.vendorParams](https://trtc.io/document/73940).

> **Note:**Console also supports setting Template ID separately, primarily used to push message Template ID in Chat scenarios (**category = "IM"**).After setting the Template ID in console settings, the title and desc field content of [V2TIMOfflinePushInfo](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html) will be automatically filled with the template heading and content, as follows:{    "oppoTitleParam": {         "title":"titleInfo"     },    "oppoContentParam":{        "desc":"descInfo"    }} Corresponding application template example:TemplateID: IDMessage Type: IMTitle: ${title}$Content: ${desc}$**The above can support offline message adaptation for private message templates in existing Chat scenarios, achieving the goal where existing users' Chat messages can still be delivered via private message channels. This method is also recommended for IM-type messages to use private message templates.**

Push messages are classified into private messages and public messages with different push effectiveness and policies. Private messages target users who pay a certain level of attention and wish to receive information promptly. Application for private message channel benefits requires an email application. The number of pushes via the public trust channel is limited.

##### Customized Self-Categorization Push Method

- [Create Private Message Channel](https://open.oppomobile.com/new/developmentDoc/info?id=12391).
- Push messages carry the channel ID field. For details, see [setAndroidOPPOChannelID](https://im.sdk.qcloud.com/doc/zh-cn/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a32d340e95395bb64cc3e8f62321aafe1). For console settings, see Certificate Editing ChannelID field. Setting one of the two is sufficient.

For specific details, see [Message Classification Description](https://open.oppomobile.com/wiki/doc#id=11227) or [Push Service Restriction Explanation](https://open.oppomobile.com/wiki/doc#id=11210).

## Mi

Push messages are divided into "Private Message" and "Public Trust Message" categories, with the default channel being Public Trust Message. The daily push quantity of Public Trust Messages will be subject to upper limit management. Public Trust Messages are suitable for pushing Hot News, New Product Promotions, Platform Announcements, Community Topics, Prize-Winning Activities, etc., mostly content of universal interest to users. Private Messages are suitable for pushing Chat Messages, Personal Order Changes, Courier Notifications, Transaction Reminders, IoT System Notifications, etc., relating to private notifications, with no restrictions on the number of notification messages pushed. Implementation of Message Classification Management requires channel application and access in the Manufacturer Console.

##### Custom Method for Self-Classified Push:

- [Channel Application and Access](https://dev.mi.com/console/doc/detail?pId=2422#_2).
- Push messages carry the channel ID field. For details, see [setAndroidXiaoMiChannelID](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#ac769aec48cdbc9a57416c5a79504617a). For console settings, see Certificate Editing ChannelID field. Setting one of the two is sufficient.

For details, see [Push Message Classification New Rules](https://dev.mi.com/console/doc/detail?pId=2422) or [Push Message Restriction Description](https://dev.mi.com/console/doc/detail?pId=2086).

## Meizu

Push messages are divided into two categories: "private messages" and "public messages". The default channel is public messages. Users have no expectation of receiving such messages and pay less attention to them. The number of pushes per device per day is limited. For private messages, users expect to receive such messages or need to know them in time. If missed, it may cause adverse effects. The number of pushes is unlimited.

##### Customization method of self-classification pushï¼

Push messages carry message classification fields. For details, see [setAndroidMeizuNotifyType](https://im.sdk.qcloud.com/doc/zh-cn/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html#a7e26dd03042cad06c4e7352845079be0). For console settings, see the "Message Classification" field in the certificate editor. You can set one of the two.

For details, see the [new rules for push messages](https://open.flyme.cn/docs?id=329).

## FCM

Push upstream message frequency is restricted.

For specific details, see [Message Frequency Limits](https://firebase.google.com/docs/cloud-messaging/throttling-and-quotas).

> **Note:**The setting of push message Channel ID and the category field has two methods: API interface and console certificate settings, each with its scope of effect, and the API setting has a higher priority than the console setting.


---
*Source: [https://trtc.io/document/60576](https://trtc.io/document/60576)*
