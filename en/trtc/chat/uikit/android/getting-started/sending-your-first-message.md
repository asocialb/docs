# Sending your first message

This document will guide you through integrating TUIKit or TUIChat and successfully sending your first message.

Or, if you prefer a faster and more automated approach, you can refer to [Get started with AI integration](https://www.tencentcloud.com/document/product/1047/72277) to streamline the process.

## Development Environment Requirements

- Android Studio-Giraffe
- Gradle-7.2
- Android Gradle Plugin Version-7.0.0
- kotlin-gradle-plugin-1.5.31

## Create an Application

Before integrating TUIKit, you need to create a Chat application in the console. The steps are as follows:

1. Register [TRTC](https://trtc.io/register?s_url=https://console.trtc.io) account and add a payment method.
2. Log in to the [Chat console](https://console.trtc.io) and click **Create Application**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e400d41bcc2811f093295254001c06ec.png)

3. Enter the application name in the create pop-up window and choose **Chat**, select appropriate **Deployment Region**, then click **Create**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e3e7e92dcc2811f0ae4f52540099c741.png)

4. After creation, you can view the application status, service version, SDKAppID, SDKSecretKey, creation time, and expiry time on the current [**Chat Product Details Page**](https://console.trtc.io/chat) or [**My Applications**](https://console.trtc.io/app).

> **Note**The service version of a new application defaults to Trial Edition, and the status is enabled by default.A single Tencent Cloud account can create up to 300 Chat applications. If you already have 300 applications, you can first [deactivate and delete](https://www.tencentcloud.com/document/product/1047/34540#357049f6-9802-456e-8f51-755d906f014a) unused applications before creating new ones. **After application deletion, all data and services corresponding to the SDKAppID cannot be restored. Proceed with caution.**

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e4051d9dcc2811f096d1525400e889b2.png)

## Create Accounts

Creating an Application only ensures you can normally initialize the SDK. To successfully send messages, you also need to create user accounts in the Application. There are many ways to create accounts, such as directly in the console or through API client registration. You can choose any suitable method.

> **Note:**Sending messages requires at least two users to interact with each other, so you need to create at least 2 accounts for this step. Please record the userIDs of these 2 accounts, as they will be used in the next steps.

**Option A: Create in Console**

> **Note:**For more account-related operations, see [Account Management](https://www.tencentcloud.com/document/product/1047/50301).

1. Log in to the [Chat console](https://console.trtc.io), select **Chat >**[**Users**](https://console.trtc.io/chat/account-management) in the left sidebar, and choose the target application at the **top**.
2. On the account management page, click Create Account.
3. In the pop-up Create Account dialog box, configure the following parameters:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e3e44795cc2811f0ae4f52540099c741.png)

  - Account type: Case-sensitive for ordinary account and admin account. "App admin" is a role with the highest level of privileges for the App, allowing calls to RESTful APIs to perform operations such as creating/disbanding groups and sending All Users Push messages. Each application supports configuration of up to 10 administrators.
  - Username: Enter username (UserID), required.
  - User nickname: Enter user nickname, optional.
  - Avatar: Enter user avatar URL, optional.
4. Click **Confirm** to save configuration.
5. After creating an account, you can view the username, nickname, account type, avatar, and creation time in the account list.

**Option B: Create accounts upon logging in**

To register via the client, just input a brand new UserID in the [Log In to TUIKit](#288b702c-cc18-4c33-976d-af38aabcac80) section below. At this point, TUIKit will automatically register the UserID for you.

## Generate UserSig

> **Note:**For more UserSig related operations, please refer to [UserSig Generation & Validation](https://www.tencentcloud.com/document/product/1047/34580#usersig-.E7.94.9F.E6.88.90.26.E6.A0.A1.E9.AA.8C).

1. Log in to the [Chat console > Development Tools > UserSig Tools](https://console.trtc.io/usersig).
2. In the UserSig generation tool section, **select an application** and **manually input the UserID**.
3. Click **Generate Signature (UserSig)** to generate a signature. The signature validity period defaults to 180 days.
4. Click **Copy Signature (UserSig)** to paste and save the signature.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/e3ed9a88cc2811f091ab5254007c27c5.png)

## Integrate TUIKit

The feature of sending messages in chat interactions is implemented by `TUIChat`. You need to integrate at least `TUIChat` to properly send and receive messages. Other components, such as `TUIConversation`, `TUIContact`, and `TUIGroup`, can be integrated as needed.

- If you need multiple UI components, you can integrate TUIKit. For details, see [Integrate TUIKit](https://www.tencentcloud.com/document/product/1047/50057?lang=en&pg=).
- If you only need to integrate TUIChat, see [Integrate TUIChat Only](https://www.tencentcloud.com/document/product/1047/60168?lang=en&pg=).

## Log In to TUIKit

To use the features in the TUIKit component, login is required. TUILogin provides a login API as follows:

```
// API location: TUICore/TUILogin.java// Called when login is clicked on the user UITUILogin.login(context, sdkAppID, userID, userSig, new TUICallback() {    @Override    public void onSuccess() {    }        @Override    public void onError(final int code, final String desc) {    }});
```

This API requires three parameters:

- SDKAppID, the SDKAppID of the new application creation, was obtained in the previous [Create Application](#91aad40c-f055-48a6-b64b-c507d16cad7f).
- UserID, the UserID of User1, was obtained in the previous [Create Account](#bafe82cd-d58d-4d09-956d-c318e2e49bc5). Note that it is not the user's NickName.
- UserSig, User1's UserSig, has been obtained in the [Generating UserSig](#1678b9aa-cc39-49ab-8a9d-d5e8857df988) context before.

## Go to Chat Interface

To send messages, the next step is:

1. Use one of the previously registered accounts (hereinafter referred to as user1) to log in to TUIKit, and then user1 is online.
2. User1 sends a message to another account (hereinafter referred to as user2). User2 does not need to log in and does not need to have any friend relationship with user1.

> **Note:**The following steps explain how to send a message to user2 after logging in as user1. If you wish for user1 and user2 to interact via chat, you need to use the same steps to log in as user2 and enter the chat interface with user1.

You can navigate to the chat interface in the callback of user1's successful login, and send a message to user2.

The sample code is as follows, where chatID needs to be user2's ID.

```
Intent intent = new Intent(context, TUIC2CChatMinimalistActivity.class);
intent.putExtra(TUIConstants.TUIChat.CHAT_ID, "chatID");
intent.putExtra(TUIConstants.TUIChat.CHAT_TYPE, V2TIMConversation.V2TIM_C2C);
intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
context.startActivity(intent);
```

## Send Your First Message

After completing the previous steps, you can go to the following chat interface. Quickly click the input box to send your first message:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6999304c167b11efb5545254007bbd8c.png)

## Contact Us

If you have any questions about this article, feel free to join the [Telegram Tech Support Group](https://t.me/+EPk6TMZEZMM5OGY1), where you will receive reliable technical support.


---
*Source: [https://trtc.io/document/60520](https://trtc.io/document/60520)*
