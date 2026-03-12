# Live Comment View

## Component Overview

<Message Rendering Component> will display your bullet screen messages on the screen. Users can manually input emojis and text messages in the bullet screen through the `Message Sending Component`. Our message rendering component will then render the received messages on the screen, thereby enhancing the fun of the live stream and making the interaction experience more enjoyable and vivid.

Android

iOS

Flutter

`BarrageStreamView`: A rendering component that displays barrage messages on the screen.

`BarrageStreamView`: A message rendering component that displays barrage messages on the screen.

`BarrageDisplayWidget`: A rendering component that displays barrage messages on the screen.

The rendering is shown as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8b6fcd6345d111f0912c52540044a08e.png)

## Component Integration

Android

iOS

Flutter

**step 1:Download the TUILiveKit component**

Clone/download the code from [GitHub](https://github.com/tencentyun/TUILiveRoom), then copy the tuilivekit subdirectory under the Android directory to the same-level directory as your app in the current project, as shown in the figure below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/54aee7086b7a11f08eae52540044a08e.png)

**step 2:Project Configuration**

1. Add the jitpack repository address in the `settings.gradle.kts (or settings.gradle)` file in the project root directory: add the jitpack repository dependency (to download the SVGAPlayer third-party library for playing gift svg animations).

settings.gradle.kts

settings.gradle

```
dependencyResolutionManagement {    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)    repositories {        google()        mavenCentral()        // Add jitpack repository url        maven { url = uri("https://jitpack.io") }    }}
```

```
dependencyResolutionManagement {    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)    repositories {        google()        mavenCentral()        // Add jitpack repository url        maven { url 'https://jitpack.io' }    }}
```

2. Add the following code in the `settings.gradle.kts (or settings.gradle)` file in the project root directory. It enables importing the downloaded tuilivekit component into your current project:

settings.gradle.kts

settings.gradle

```
include(":tuilivekit")
```

```
include ':tuilivekit'
```

3. Locate the `build.gradle.kts (or build.gradle)` file under the app directory and add the following code in it. It enables declaring the current app's dependency on the newly joined tuilivekit component:

build.gradle.kts

build.gradle

```
api(project(":tuilivekit"))
```

```
api project(':tuilivekit')
```

> **Note:**Note: The TUILiveKit project internally depends on `TRTC SDK`, `IM SDK`, `tuiroomengine`, and the public library `tuicore` by default. Developers do not need to separately configure them. If needed, just modify the `tuilivekit/build.gradle` file to upgrade.

4. Since we use Java reflection features internally in the SDK, some classes in the SDK need to be added to the non-obfuscation list. Therefore, you need to add the following code in the `proguard-rules.pro` file:

```
-keep class com.tencent.** { *; }-keep class com.trtc.uikit.livekit.livestreamcore.** { *; }-keep class com.trtc.uikit.livekit.component.gift.store.model.** { *; }-keep class com.squareup.wire.** { *; }-keep class com.opensource.svgaplayer.proto.** { *; }-keep class com.tcmediax.** { *; }-keep class com.tencent.** { *; }-keep class com.tencent.xmagic.** { *; }-keep class androidx.exifinterface.** {*;}-keep class com.google.gson.** { *;}# Tencent Effect SDK - beauty-keep class com.tencent.xmagic.** { *;}-keep class org.light.** { *;}-keep class org.libpag.** { *;}-keep class org.extra.** { *;}-keep class com.gyailib.**{ *;}-keep class com.tencent.cloud.iai.lib.** { *;}-keep class com.tencent.beacon.** { *;}-keep class com.tencent.qimei.** { *;}-keep class androidx.exifinterface.** { *;}
```

5. Find the `AndroidManifest.xml` file under the app directory, add tools:replace="android:allowBackup" and android:allowBackup="false" in the application node, overwrite the setting within component, and use your own setting.

```
  // app/src/main/AndroidManifest.xml    <application    ...      // add the following configuration to overwrite the configuration in the dependent sdk    android:allowBackup="false"    tools:replace="android:allowBackup">
```

Import components using CocoaPods. The specific steps to import components are as follows:

1. You need to download the `Barrage` folder from [GitHub](https://github.com/Tencent-RTC/TUILiveKit/tree/main/iOS) to your local system.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/53ff35c92b3c11f0b0b1525400e889b2.png)

2. Add `pod 'TUIBarrage'` dependency in the `Podfile` file of your project.

Swift

```
target 'xxxx' do  ...  ...  pod 'TUIBarrage', :path => '../Component/Barrage/TUIBarrage.podspec'   // The path is the relative path between your Podfile file and TUIBarrage.Podspec file.end
```

If you don't have a `Podfile` file, first use the terminal to `cd` into the `xxxx.xcodeproj` directory, then create it with the following command:

```
pod init
```

3. In the terminal, first `cd` to the `Podfile` directory, then execute the following commands to install components.

```
pod install
```

4. Any issues you encounter during integration and use, feel free to [give us feedback](https://github.com/Tencent-RTC/TUILiveKit/issues).
1. In the dependencies node of the pubspec.yaml file in the project engineering, add a dependency on **barrage**.

```
dependencies:  flutter:    sdk: flutter  flutter_localizations:    sdk: flutter  intl: ^0.19.0  # Add barrage dependency  live_uikit_barrage: ^1.0.0
```

1. Execute the
2. `flutter pub get` command.
3. Configure multilingual support. Add multilingual support for the **gift** component to the `localizationsDelegates` and `supportedLocales` properties of your application's `MaterialApp`.

```
MaterialApp(localizationsDelegates: const [  ...BarrageLocalizations.localizationsDelegates,], supportedLocales: const [  ...BarrageLocalizations.supportedLocales,], // ...);
```

## Component Usage

> **Notes:**Since the barrage component requires live room information parameters, it is necessary to load the barrage component after **Audience Entering the Live Room** or **Anchor Create Live Room**.

### Integrating Message Rendering Component

Android

iOS

Flutter

At the position to display barrage, use `BarrageStreamView` to display barrage messages:

```
BarrageStreamView barrageStreamView = new BarrageStreamView(mContext);// ownerId indicates the room owner's ID, used to distinguish display effects between host and viewersbarrageStreamView.init(roomId, ownerId);mLayoutBarrageContainer.addView(barrageStreamView);
```

At the position to display barrage, use `BarrageStreamView` to display barrage messages:

```
BarrageStreamView
```

After obtaining the room owner information, set the ownerId to distinguish display effects between host and viewers.

```
barrageDisplayView.setOwnerId(ownerId)
```

> **Notes:**You can only successfully receive bullet screens inside the room after successfully entering the room.

Build BarrageDisplayController and BarrageDisplayWidget objects where you need to display barrage messages, and add the built BarrageDisplayWidget object to your Widget tree. Sample code is as follows:

```
BarrageDisplayController _displayController = BarrageDisplayController(                roomId: "liveRoomId",             /// Replace with your live stream room ID                ownerId:  "liveOwnerId",          /// Replace with your live stream host ID                 selfUserId: "selfUserId",         /// Replace with your currently logged-in user ID                selfName: "selfUserName";         /// Replace with your currently logged-in user nicknameBarrageDisplayWidget(controller: _displayController);
```

### Insert Local Danmu Message

Android

iOS

Flutter

BarrageStreamView provides the `insertBarrages` API method for batch inserting custom messages (such as gift messages, live room notices). Usually, custom messages combined with custom styles can achieve different display effects.

Sample code:

```
// Insert a gift message into the barrage areaBarrage barrage = new Barrage();barrage.content = "gift";barrage.user.userId = "sender.userId";barrage.user.userName = "sender.userName";barrage.user.avatarUrl = "sender.avatarUrl";barrage.extInfo.put("GIFT_VIEW_TYPE", "GIFT_VIEW_TYPE_1");barrage.extInfo.put("GIFT_NAME", "giftName");barrage.extInfo.put("GIFT_COUNT", "giftCount");barrage.extInfo.put("GIFT_ICON_URL", "imageUrl");barrage.extInfo.put("GIFT_RECEIVER_USERNAME"," receiver.userName");barrageStreamView.insertBarrages(barrage);
```

> **Notes:** is a `Map` for storing custom data.

BarrageStreamView provides the `insertBarrages` API method for batch inserting custom messages (such as gift messages, live room notices). Usually, custom messages combined with custom styles can achieve different display effects.

Sample code:

```
import TUIBarrageimport RTCCommon// Example 1: Insert a gift message into the barrage arealet barrage = TUIBarrage()barrage.content = "gift"barrage.user.userId = "sender.userId"barrage.user.userName = "sender.userName"barrage.user.avatarUrl = "sender.avatarUrl"barrage.user.level = "sender.level"let giftCount = 1barrage.extInfo["TYPE"] = AnyCodable("GIFTMESSAGE")barrage.extInfo["gift_name"] = AnyCodable("gift.giftName")barrage.extInfo["gift_count"] = AnyCodable(giftCount)barrage.extInfo["gift_icon_url"] = AnyCodable("gift.imageUrl")barrage.extInfo["gift_receiver_username"] = AnyCodable("receiver.userName")barrageDisplayView.insertBarrages([barrage])
```

> **Notes:** is a `Map` for storing custom data.

When you need to insert a local barrage message, you can call the insertMessage method of the BarrageDisplayWidget to insert a local message. For example, after detecting that an audience enters the room in LiveKit, you can insert a barrage message indicating that an audience has entered the room. The sample code is as follows:

```
BarrageUser barrageUser = BarrageUser();barrageUser.userId = "enterRoomUserId";            /// Displayed user ID informationbarrageUser.userName = "enterRoomUserName";        /// Displayed user nickname informationbarrageUser.avatarUrl = "enterRoomUserAvatar";     /// Displayed user avatar informationbarrageUser.level = "66";                          /// Displayed user level informationBarrage barrage = Barrage();barrage.user = barrageUser;barrage.content = "Enter a room";                       /// Displayed text content_displayController.insertMessage(barrage);
```

### Custom Barrage Message

Android

iOS

Flutter

There are two default barrage message styles: ordinary barrage message style and custom message style. Specific styles are represented by integers, with the ordinary barrage message style being 0.

If you need more message styles (such as **gift sending echo**), you need to rewrite the BarrageStreamView's agent BarrageItemTypeDelegate and implement the new style BarrageItemAdapter.

- Rewrite the BarrageItemTypeDelegate agent to support the new style GIFT_VIEW_TYPE_1.

```
public static final int    GIFT_VIEW_TYPE_1       = 1;public class BarrageViewTypeDelegate implements BarrageItemTypeDelegate {    @Override    public int getItemType(int position, Barrage barrage) {        if (barrage.extInfo != null && barrage.extInfo.containsKey("GIFT_VIEW_TYPE")) {            String viewTypeString = String.valueOf(barrage.extInfo.get("GIFT_VIEW_TYPE"));            if (String.valueOf(GIFT_VIEW_TYPE_1).equals(viewTypeString)) {                return GIFT_VIEW_TYPE_1;            }        }        return 0;    }}mBarrageStreamView.setItemTypeDelegate(new BarrageViewTypeDelegate());
```

- Implement an adapter for custom styles and set it to style GIFT_VIEW_TYPE_1.

```
public class GiftBarrageAdapter implements BarrageItemAdapter {    @Override    public RecyclerView.ViewHolder onCreateViewHolder(ViewGroup parent) {        LinearLayout ll = new LinearLayout(mContext);        ll.addView(new TextView(mContext));        return new GiftViewHolder(ll, mDefaultGiftIcon);    }    @Override    public void onBindViewHolder(RecyclerView.ViewHolder holder, int position, Barrage barrage) {        GiftViewHolder viewHolder = (GiftViewHolder) holder;        viewHolder.bind(barrage);    }    // GiftViewHolder    ...}mBarrageStreamView.setItemAdapter(GIFT_VIEW_TYPE_1, new GiftBarrageAdapter(mContext));
```

There are two default barrage message styles: ordinary barrage message style and custom message style.

If you need more message styles (such as **gift sending echo**), you can implement the proxy method BarrageStreamViewDelegate of BarrageStreamView.

```
import TUIBarrageclass MyViewController: BarrageStreamViewDelegate {    let barrageDisplayView = BarrageStreamView(roomId: roomId)    override func viewDidLoad() {        super.viewDidLoad()        barrageDisplayView.delegate = self  // Set the proxy for BarrageStreamView                // ...    }    func onBarrageClicked(user: TUIUserInfo) {        // Here you can add the event processing logic for barrage message clicks. 'user' is the sender information.    }        func barrageDisplayView(_ barrageDisplayView: BarrageStreamView, createCustomCell barrage: TUIBarrage) -> UIView? {        // Whether to use Custom UI, if not needed, return nil just        guard let type = barrage.extInfo["TYPE"], type.value as? String == "GIFTMESSAGE" else {            return nil        }                // Return custom message style UI (gift echo)        return CustomBarrageView(barrage: barrage)    }}// Custom UIclass CustomBarrageView: UIView {    let barrage: TUIBarrage    init(barrage: TUIBarrage) {        self.barrage = barrage        super.init(frame: .zero)    }    required init?(coder: NSCoder) {        fatalError("init(coder:) has not been implemented")    }    // ...Layout and draw your own UI here}
```

When you need to display a custom barrage item for specific barrage messages, you can implement it through the setCustomBarrageBuilder method of BarrageDisplayWidget. For example, the sample code for customizing a barrage that displays red text is shown below:

```
/// 1. Define a custom barrage item builderclass GiftBarrageItemBuilder extends CustomBarrageBuilder {  @override  Widget buildWidget(BuildContext context, Barrage barrage) { /// When shouldCustomizeBarrageItem returns true, customize widget    return const Text(      barrage.content,      style: TextStyle(fontSize: 18, fontWeight: FontWeight.w700, color: Colors.red),    );  }  @override  bool shouldCustomizeBarrageItem(Barrage barrage) {    /// For the data model of the barrage message, determine whether the current barrage message needs to be customized    if (barrage.extInfo.keys.isNotEmpty) {      return true;    }    return false;  }}/// 2. Set setCustomBarrageBuilder for BarrageDisplayWidget_displayController.setCustomBarrageBuilder(GiftBarrageItemBuilder());
```

##


---
*Source: [https://trtc.io/document/69847](https://trtc.io/document/69847)*
