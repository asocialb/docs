# Overview

## Group Overview

The Chat SDK on the new version comes with upgraded group types, including work groups (Work), public groups (Public), meeting groups (Meeting), communities, and audio-video groups (AVChatRoom).

The groups on the earlier SDK version and the new SDK version are as compared below:

| Previous Group Types | New Group Types | Group Feature |
| --- | --- | --- |
| Public | Public(Stranger social public group) | It allows the group owner to designate group admins. To join the group, users must search for the group ID and request approval from the group owner or admin. |
| Private | Work(Friends work group) | A work group allows users to join after being invited by a friend who is a member of the group, without acceptance by the user or approval by the group owner required. |
| ChatRoom | Meeting(Temporary meeting group) | A meeting group allows users to join and leave freely and view message history from before they joined the group. This group type is suitable for scenarios where Tencent Real-Time Communication (TRTC) is used, for example, audio and video conferences and online education. |
| AVChatRoom | AVChatRoom(Audio-video group) | An audio-video group allows users to join and leave freely. It supports an unlimited number of group members and doesn't store message history. This group type can be used with live streaming products to support on-screen comment chat scenarios.![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/03a0a259cf0411ef8c8a525400454e06.png) |
| - | Community(Community Group) | A community allows users to join and leave freely. It is a new powerful tool for entertainment collaboration and is suitable for chat scenarios with a super large number of community members, such as finding like-minded people, gaming social networking, fan marketing, and organization management.Within the same community, a high number of members can be divided into different groups and topics to separate messages for hierarchical communication, yet they can also share the same set of friend relationships. ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/330a1461cf0411efa4a3525400bf7822.png) |

> **Note:**The Community feature is only supported by the Enhanced version SDK 5.8.1668 or later, and Web SDK 2.17.0 or later.The Community feature requires to [purchase the Premium Edition](https://trtc.io/buy/chat), and to use it, the switch must be activated in the [Console](https://console.trtc.io/). Switch path: Applications > Your App > Chat > Configuration > Group Configuration > Group feature configuration > Community.For Friends Work Group (Work) and Stranger Social Group (Public), the pre-group message history is not pulled by default. To enable this feature, the switch must be activated in the [Console](https://console.trtc.io/). Switch path: Applications > Your App > Chat > Configuration > Group Configuration > Group message configuration > Pull message history before group join.

The features and limits of each group type are as described below:

| Feature | Work Group (Work) | Public Group (Public) | Meeting Group (Meeting) | Community Group (Community) | Audio-Video Group (AVChatRoom) |
| --- | --- | --- | --- | --- | --- |
| Available member roles | Group owner and common member | Group owner, group admin, and common member | Group owner, group admin, and common member | Group owner, group admin, and common member | Group owner and common member |
| Requesting to join a group | Not supported | Supported with group owner or admin approval required | Supported with no approval required | Supported with no approval required | Supported with no approval required |
| Joining group via invitation by a member | Supported | Supported (Since v7.1.3925) | Supported (Since v7.1.3925) | Supported | Not supported |
| Group owner leaving group | Supported | Not supported | Not supported | Not supported | Not supported |
| Who can modify group profile | Any group member | Group owner and admin | Group owner and admin | Group owner and admin | Group owner |
| Who can kick group members out of group | Group owner | Group owner and admin. Group admin can only remove common group members. |  |  | Group members cannot be removed. The same effect can be achieved by muting members. |
| Who can mute members | Muting members is not supported | Group owner and admin.    Group admin can only mute common group members. |  |  | Group owner |
| Unread count | Supported | Supported | Not supported | Supported | Not supported |
| Viewing message history earlier than user's entry time | Supported | Supported | Supported | Supported | Not supported |
| Retaining message history in the cloud | **Free Trial**: 7 days**Standard edition**: 7 days by default, which can be increased to up to 360 days via [value-added service](https://trtc.io/pricing/chat)**Pro edition:**30 days by default, which can be increased to up to 360 days via [value-added service](https://trtc.io/pricing/chat)**Pro Plus edition**: 90 days by default, which can be increased to up to 360 days via [value-added service](https://trtc.io/pricing/chat)**Enterprise edition**: 90 days by default, which can be increased to up to 360 days via [value-added service](https://trtc.io/pricing/chat) |  |  |  | Not supported |
| Number of groups | **Free Trial:** Up to 100 existing groups, and deleted groups do not count against the quota.**Standard edition ã Pro edition ãPro Plus editionãEnterprise edition**: Unlimited |  |  | **Standard edition:**Not supportedï¼**Free Trial and Pro edition:** 100,000**Pro Plus edition anf Enterprise edition**:10,000,00 | **Free Trial**: Up to ten existing groups, and disbanded groups do not count against the quota.Standard edition: Up to 50 existing groups, and disbanded groups do not count against the quota.You can upgrade to unlimited number of audio-video groups by purchasing the [value-added service](https://trtc.io/pricing/chat).**Pro edition ãPro Plus editionãEnterprise edition:** Unlimited |
| Number of group members | **Free Trial:** 20 per group**Standard edition**: 500 per group by default**Pro edition:** 2,000 per group by default**Pro Pluse edition:** 5,000 per group by default**Enterprise edition:** 6,000 per group by default |  |  | 100,000 | Unlimited number of group members |

> **Note:**In the `SDKAppID` of the Standard edition or Pro edition ãPro Plus editionãEnterprise edition, the maximum net increase in group count per day is 10,000 for all group types.


---
*Source: [https://trtc.io/document/48169](https://trtc.io/document/48169)*
