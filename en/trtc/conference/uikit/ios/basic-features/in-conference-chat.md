# In-Conference Chat

In video conferences, participants can send messages in real-time in the chat area, share opinions and ideas, and create a relaxed and pleasant communication environment by exchanging emoticons and animations. To maintain the order of the meeting, the host or administrator can set to prohibit participants from sending messages in the chat, ensuring the focus and efficiency of the conference content. By flexibly using these features, video conferences can provide efficient and convenient communication experiences for various scenarios.

## Description of the Feature

At the bottom menu bar of the conference interface, you can find an option called **Chat**. Click on it, and you will be redirected to the chat page. On the chat page, participants can communicate with other participants by sending custom text messages. This design facilitates real-time communication between participants without affecting the person who is speaking.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8ceaae9efc9611eeb7f5525400a7e516.jpeg)

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8cdeebdffc9611eeac26525400ae4d13.png)

### Emoticon Interaction

Click the **emoticon icon** in the chat interface's message editing bar to display the emoticon list. Click the corresponding emoticon to send it and give a thumbs-up to the speaker's brilliant speech.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8cc34702fc9611eeac26525400ae4d13.png)

> **Noteï¼**To respect the emoji design copyright, the Conference project does not include large emoji element slices. Before the official commercial launch, please replace them with your own designed emoji or other emoji packs that you own the copyright to. The default **Little Yellow Face Emoji Pack copyright belongs to Tencent Cloud** and can be licensed for a fee. If you wish to obtain a license, you can [Submit a ticket](https://console.tencentcloud.com/workorder/category) to contact us.

### Manage In-conference Chat Permissions

The host/administrator can set the chat permissions of a member in member management. Ordinary members who are prohibited from speaking will not be able to edit or send text or emoticons.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8cf1d545fc9611eeb7f5525400a7e516.jpeg)

## Feature Integration

Android

iOS

### Module Source Code Integration

1. Clone/download the code from [Github](https://github.com/tencentyun/TUIRoomKit), and then copy the `tuichat` subdirectory from the Android directory to the same level as your current project's app directory.
2. Find the `setting.gradle` file in the root directory of the project and add the following code to it. This code imports the `tuichat` as a local module into your current project.

```
  include ':tuichat'
```

3. Find the `build.gradle` file in the app directory and add the following code to it. This code declares the current app's dependency on the newly added `tuichat` component.

```
  api project(':tuichat')
```

4. Add the maven repository and Kotlin support in the `build.gradle` file of the root project (at the same level as `settings.gradle`):

```
  buildscript {    repositories {        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }    }    dependencies {        classpath 'com.android.tools.build:gradle:7.0.0'        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:1.5.31"    }}
```

If you are using Gradle 8.x, you need to add the following code.

```
buildscript {    repositories {        mavenCentral()        maven { url "https://mirrors.tencent.com/nexus/repository/maven-public/" }    }    dependencies {        classpath 'com.android.tools.build:gradle:8.0.2'        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.0"    }}
```

> **Note:**The corresponding relationship between Kotlin, Gradle, and AGP versions can be [viewed here](https://kotlinlang.org/docs/gradle-configure-project.html#apply-the-plugin).

### Access Chat Widget

To import the chat widget using CocoaPods, follow these steps:

1. Add the following dependencies to your `Podfile`.

```
pod 'TUIChat'          # [Optional] Chat widget
```

2. Execute the following command to install the components.

```
pod install
```


---
*Source: [https://trtc.io/document/60097](https://trtc.io/document/60097)*
