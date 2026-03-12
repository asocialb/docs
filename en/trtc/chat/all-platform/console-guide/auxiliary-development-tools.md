# Auxiliary Development Tools

## Offline Push Check

### Offline push issue locator

This tool allows you to query issues related to the failure to receive offline messages.

1. Log in to the [Chat console](https://console.trtc.io), select **Chat > Push >**[**Access test**](https://console.trtc.io/chat/push-plugin-push-check) in the left sidebar, and choose the target application at the **top**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2b4ca36dcb5811f0a7775254005ef0f7.png)

2. Select **push type**, option **Online push** or **Offline Push**.

Online Push

Offline Push

1. Select **online push**, manually input UserID.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9e7e8e60cb5811f0a4a55254001c06ec.png)

2. Click **Send a push test**, view **Query Result**, including the certificate ID, device Token, etc. currently reported by the UserID.
1. Select **Offline Push**, manually input UserID, click **get token binding status**, view **detection result**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9e8a3ff7cb5811f0a4a55254001c06ec.png)

2. Select any one of the certificate IDs reported by the UserID, click **Send a push test**, view **Query Result**, including the certificate ID, device Token, etc. currently reported by the UserID.
  - If the push indicates success, it means the certificate information filled in on the console is correct and the SDK API call to report the Token succeeded. You can use the [user status check tool](#status) for further investigation.
  - If the notification indicates failure, you can check the specific cause of failure and solution.

> **Note:**If the UserID has not reported any certificate ID, device Token, etc., you will be unable to proceed to the next step.

### User Status Check Tool

This tool automatically obtains the userâs client status and checks whether the user is ready to receive offline push messages.

1. Log in to the [Chat console](https://console.trtc.io), select **Chat > Push >**[**Access test**](https://console.trtc.io/chat/push-plugin-push-check) in the left sidebar, and choose the target application at the **top**.
2. In the left sidebar, choose**Chat > Push > Access test**.
3. In the **User offline status checking tool** area, enter the UserID.
4. Click **Get Status** to view information such as the current status and client type of the UserID.
 If you are prompted that the UserID is ready to receive offline push messages, you can log in with a different UserID on another device to send one-to-one text messages to the current UserID to check whether it can receive the messages.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/20486cb77b1511ef8631525400a9236a.png)

## UserSig Generation and Verification

### Signature (UserSig) Generator

The system automatically obtains the key of the current app. After entering the UserID, you can use this tool to quickly generate a signature (UserSig) to run through demos and debug features locally. If you need to generate a UserSig for online services, see [Generating UserSig on the Server](https://intl.cloud.tencent.com/document/product/1047/34385).

1. Log in to the [Chat console > Development Tools > UserSig Tools](https://console.trtc.io/usersig).
2. In the Signature (UserSig) Generator area, **select an application**, **manually input UserID**.
3. Click **Generate UserSig** to generate a signature, which expires after 180 days.
4. Click **Copy UserSig** to copy the signature and then paste and save the signature.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8235cbaacb5911f0a4a55254001c06ec.png)

### Signature (UserSig) Verifier

The system automatically obtains the key of the current app. After entering the UserID and UserSig, you can use the tool to quickly check the validity of the UserSig.

1. Log in to the [Chat console > Development Tools > UserSig Tools](https://console.trtc.io/usersig).
2. In the Signature (UserSig) Verifier area, **select an application**, **manually input UserID** and **UserSig**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ce7e2388cb5911f0aedb525400454e06.png)

3. Click **Verify** to see the verification result.
  - If verification succeeds, you can view the SDKAppID, UserID, generation time, service time, and expiration time of the UserSig in the verification results.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e7819f55cb5911f0a7775254005ef0f7.png)

  - If verification fails, you can view the cause of failure and solution in the verification results.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f02450b9cb5911f0aedb525400454e06.png)

## Self-Troubleshooting Logs

Tencent Cloud Chat console provides self-troubleshooting feature to allow developers to query the backend log information of Chat in the last three days to quickly locate and solve issues.

1. Log in to the Chat console, click the target Chat app section.
2. In the left sidebar, choose **Auxiliary Tools** > **Self-Troubleshooting Logs**.
3. Configure following filters to query logs:
  - Event name (Optional): Select events for querying.
  - UserID (Optional): Enter username (UserID), which is the UserID of the message sender.
  - Receiver/Group ID (Optional): Enter target conversation ID. For a one-to-one chat, it is the UserID of the message receiver. For a group chat, it is the GroupID of the group.
  - Error codes (Optional): Enter error codes. For error code descriptions, see [Error Codes](https://www.tencentcloud.com/document/product/1047/34348).
  - Time range (Required): Select the time range of logs to be queried. Logs in the last three days can be queried.
4. Click **Query** to view the filtered logs.


---
*Source: [https://trtc.io/document/34580](https://trtc.io/document/34580)*
