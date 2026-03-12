# Customize Emojis and Stickers

## Overview

| Built-in emoji panel | Custom emoji panel |
| --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/af6381be141b11efbf645254007bbd8c.PNG) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/b4e550db141b11efaa1c525400f65c2a.PNG) |

The emoji panel consists of two parts as shown below:

- The management of emoji resource images, including the display of emoji images.
- The management of emoji groups, including thumbnails of emoji groups and the send button.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/bfe3e55c141b11efa2935254005ac0ca.png)

## Adding a Custom Sticker

1. Prepare the emoji resources.
2. Load the sticker when starting the app.

Note that TUIChat is built with the logic for sending and parsing stickers so that you can easily use custom stickers on multiple terminals.

The following describes how to add the `programer` custom sticker as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c92d0134141b11efa2935254005ac0ca.png)

### Preparing emoji resources

Before adding a sticker, prepare a set of copyrighted emoji resources. Then, package your emoji images into a bundle file as shown below:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/757cb01b5b7011eeabd75254005810a4.png)

### Loading the sticker

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7c4a0eb85b7011ee9ff8525400d917da.png)

Swift

Objective-C

```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {    // ...    self.setupCustomSticker()    return YES}func setupCustomSticker() {    guard let service = TIMCommonMediator.shared.getObject(for: TUIEmojiMeditorProtocol.self) else {        assertionFailure("There's not any object implement TUIEmojiMeditorProtocol")        return    }    let bundlePath = TUISwift.tuiBundlePath("CustomFaceResource", key: "TIMAppKit.TUIKit")    // 4350 group    var faces4350 = [TUIFaceCellData]()    for i in 0...17 {        let data = TUIFaceCellData()        let name = String(format: "yz%02d", i)        let path = "4350/\\(name)"        data.name = name        data.path = bundlePath + "/" + path        faces4350.append(data)    }    if faces4350.count > 0 {        let group4350 = TUIFaceGroup()        group4350.groupIndex = 1        group4350.groupPath = bundlePath + "/4350/"        group4350.faces = faces4350        group4350.rowCount = 2        group4350.itemCountPerRow = 5        group4350.menuPath = bundlePath + "/4350/menu"        service.appendFaceGroup(group4350)    }    // 4351 group    var faces4351 = [TUIFaceCellData]()    for i in 0...15 {        let data = TUIFaceCellData()        let name = String(format: "ys%02d", i)        let path = "4351/\\(name)"        data.name = name        data.path = bundlePath + "/" + path        faces4351.append(data)    }    if faces4351.count > 0 {        let group4351 = TUIFaceGroup()        group4351.groupIndex = 2        group4351.groupPath = bundlePath + "/4351/"        group4351.faces = faces4351        group4351.rowCount = 2        group4351.itemCountPerRow = 5        group4351.menuPath = bundlePath + "/4351/menu"        service.appendFaceGroup(group4351)    }    // 4352 group    var faces4352 = [TUIFaceCellData]()    for i in 0...16 {        let data = TUIFaceCellData()        let name = String(format: "gcs%02d", i)        let path = "4352/\\(name)"        data.name = name        data.path = bundlePath + "/" + path        faces4352.append(data)    }    if faces4352.count > 0 {        let group4352 = TUIFaceGroup()        group4352.groupIndex = 3        group4352.groupPath = bundlePath + "/4352/"        group4352.faces = faces4352        group4352.rowCount = 2        group4352.itemCountPerRow = 5        group4352.menuPath = bundlePath + "/4352/menu"        service.appendFaceGroup(group4352)    }}
```

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {    app = self;    // Load the emoji resources when starting the app    [self setupCustomSticker];        return YES;}- (void)setupCustomSticker {    // 1. Get the path of the bundle file of the custom sticker.    NSString *customFaceBundlePath = [[NSBundle mainBundle] pathForResource:@"CustomFaceResource" ofType:@"bundle"];    // 2. Load the custom emoji group    // 2.1 Load the `programer` emoji resource images and parse them into `TUIFaceCellData`    NSMutableArray<TUIFaceCellData *> *faceItems = [NSMutableArray array];    for (int i = 0; i <= 17; i++) {        TUIFaceCellData *data = [[TUIFaceCellData alloc] init];        // The filename of the emoji resource images (the extension can be saved) for multi-terminal connection (which requires that filenames are consistent)        data.name = [NSString stringWithFormat:@"yz%02d", i];        // The path of the emoji resource images for local display        data.path = [customFaceBundlePath stringByAppendingPathComponent:[NSString stringWithFormat:@"programer/%@", data.name]];        [faceItems addObject:data];    }    // 2.2 Create the `programer` emoji group and parse it into `TUIFaceGroup`    TUIFaceGroup *programGroup = [[TUIFaceGroup alloc] init];    // Indicate the serial number of the current emoji group on the emoji panel for multi-terminal connection (which can be used together with the emoji name to find an image on the receiver's device)    // Note that `groupIndex` starts from `0` and indicates the actual position of the current sticker on the emoji panel (`0` is the default value for the built-in `emoji` emoji group)    programGroup.groupIndex = 1;    // The root path of the current sticker in the bundle file of the custom emojis    programGroup.groupPath = [customFaceBundlePath stringByAppendingPathComponent:@"programer/"];    // The emoji resources in the current sticker    programGroup.faces = faceItems;    // The layout of the current sticker    programGroup.rowCount = 2;    programGroup.itemCountPerRow = 5;    // The path of the thumbnail of the current sticker (without the extension)    programGroup.menuPath = [customFaceBundlePath stringByAppendingPathComponent:@"programer/menu"];    // 3. Add the `programer` emoji group to the emoji panel       id<TUIEmojiMeditorProtocol> service = [[TIMCommonMediator share] getObject:@protocol(TUIEmojiMeditorProtocol)];    [service appendFaceGroup:programGroup];}
```

### Multi-terminal connection

- The filenames of images in the sticker are consistent; that is, the values of the `name` field in `TUIFaceCellData` are consistent on multiple terminals when the stickers are loaded during app startup.
- The order of stickers on the emoji panel is consistent; that is, the values of the `groupIndex` field in `TUIFaceGroup` are consistent on multiple terminals when the stickers are loaded during app startup.

If the above two values are consistent, TUIChat's built-in logic for sending stickers will send the emoji filename and the index information of the sticker to other terminals for multi-terminal connection.

Note that `groupIndex` starts from `0` and indicates the actual position of the current sticker on the emoji panel (`0` is the default value for the built-in `emoji` emoji group).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/731bd51a141c11ef89cc5254002fd0a8.png)

## Advanced Configuration of the Emoji Panel

### Re-sorting emoji groups on the emoji panel

To place the built-in `emoji` emoji group after custom emojis, perform the following steps:

- Get the built-in `TUIConfig.defaultConfig.faceGroups` emoji groups on the current emoji panel.
- Re-sort the emoji groups.
- Assign the value of the list of re-sorted emoji groups to the emoji panel.

Swift

Objective-C

```
func setupCustomSticker() {    guard let service = TIMCommonMediator.shared.getObject(for: TUIEmojiMeditorProtocol.self) else {        assertionFailure("There's not any object implement TUIEmojiMeditorProtocol")        return    }    let bundlePath = TUISwift.tuiBundlePath("CustomFaceResource", key: "TIMAppKit.TUIKit")    // 4350 group    var faces4350 = [TUIFaceCellData]()    for i in 0...17 {        let data = TUIFaceCellData()        let name = String(format: "yz%02d", i)        let path = "4350/\\(name)"        data.name = name        data.path = bundlePath + "/" + path        faces4350.append(data)    }    if faces4350.count > 0 {        let group4350 = TUIFaceGroup()        group4350.groupIndex = 1        group4350.groupPath = bundlePath + "/4350/"        group4350.faces = faces4350        group4350.rowCount = 2        group4350.itemCountPerRow = 5        group4350.menuPath = bundlePath + "/4350/menu"        service.appendFaceGroup(group4350)    }    // 4351 group    var faces4351 = [TUIFaceCellData]()    for i in 0...15 {        let data = TUIFaceCellData()        let name = String(format: "ys%02d", i)        let path = "4351/\\(name)"        data.name = name        data.path = bundlePath + "/" + path        faces4351.append(data)    }    if faces4351.count > 0 {        let group4351 = TUIFaceGroup()        group4351.groupIndex = 2        group4351.groupPath = bundlePath + "/4351/"        group4351.faces = faces4351        group4351.rowCount = 2        group4351.itemCountPerRow = 5        group4351.menuPath = bundlePath + "/4351/menu"        service.appendFaceGroup(group4351)    }    // 4352 group    var faces4352 = [TUIFaceCellData]()    for i in 0...16 {        let data = TUIFaceCellData()        let name = String(format: "gcs%02d", i)        let path = "4352/\\(name)"        data.name = name        data.path = bundlePath + "/" + path        faces4352.append(data)    }    if faces4352.count > 0 {        let group4352 = TUIFaceGroup()        group4352.groupIndex = 3        group4352.groupPath = bundlePath + "/4352/"        group4352.faces = faces4352        group4352.rowCount = 2        group4352.itemCountPerRow = 5        group4352.menuPath = bundlePath + "/4352/menu"        service.appendFaceGroup(group4352)    }}
```

```
- (void)setupCustomSticker {    // 1. Get the path of the bundle file of the custom sticker.    NSString *customFaceBundlePath = [[NSBundle mainBundle] pathForResource:@"CustomFaceResource" ofType:@"bundle"];    // 2. Load the custom emoji group    // 2.1 Load the `programer` emoji resource images and parse them into `TUIFaceCellData`    NSMutableArray<TUIFaceCellData *> *faceItems = [NSMutableArray array];    for (int i = 0; i <= 17; i++) {        TUIFaceCellData *data = [[TUIFaceCellData alloc] init];        // The filename of the emoji resource images (the extension can be saved) for multi-terminal connection (which requires that filenames are consistent)        data.name = [NSString stringWithFormat:@"yz%02d", i];        // The path of the emoji resource images for local display        data.path = [customFaceBundlePath stringByAppendingPathComponent:[NSString stringWithFormat:@"programer/%@", data.name]];        [faceItems addObject:data];    }    // 2.2 Create the `programer` emoji group and parse it into `TUIFaceGroup`    TUIFaceGroup *programGroup = [[TUIFaceGroup alloc] init];    // Indicate the serial number of the current emoji group on the emoji panel for multi-terminal connection (which can be used together with the emoji name to find an image on the receiver's device)    // Note that `groupIndex` starts from `0` and indicates the actual position of the current sticker on the emoji panel (`0` is the default value for the built-in `emoji` emoji group)    programGroup.groupIndex = 0;    // The root path of the current sticker in the bundle file of the custom emojis    programGroup.groupPath = [customFaceBundlePath stringByAppendingPathComponent:@"programer/"];    // The emoji resources in the current sticker    programGroup.faces = faceItems;    // The layout of the current sticker    programGroup.rowCount = 2;    programGroup.itemCountPerRow = 5;    // The path of the thumbnail of the current sticker (without the extension)    programGroup.menuPath = [customFaceBundlePath stringByAppendingPathComponent:@"programer/menu"];    // 3. Add the `programer` emoji group to the front of the emoji panel    id<TUIEmojiMeditorProtocol> service = [[TIMCommonMediator share] getObject:@protocol(TUIEmojiMeditorProtocol)];    [service appendFaceGroup:programGroup];}
```

> **Note**The multi-terminal connection of stickers relies on the emoji names and the order of the emoji groups on the panel. Therefore, after adjusting the local order, you need to make sure that the `groupIndex` is consistent with the actual order.

### Changing the thumbnail of an emoji group

For example, set the `menu@2x.png` image in the `programer` emoji group as the thumbnail.

Swift

Objective-C

```
func setupCustomSticker() {    // ...        // 4350 group    var faces4350 = [TUIFaceCellData]()    for i in 0...17 {        let data = TUIFaceCellData()        let name = String(format: "yz%02d", i)        let path = "4350/\\(name)"        data.name = name        data.path = bundlePath + "/" + path        faces4350.append(data)    }    if faces4350.count > 0 {        let group4350 = TUIFaceGroup()        group4350.groupIndex = 1        group4350.groupPath = bundlePath + "/4350/"        group4350.faces = faces4350        group4350.rowCount = 2        group4350.itemCountPerRow = 5        group4350.menuPath = bundlePath + "/4350/menu"        service.appendFaceGroup(group4350)    }    // ...}
```

```
- (void)setupCustomSticker {    ....    // 2.2 Create the `programer` emoji group and parse it into `TUIFaceGroup`    TUIFaceGroup *programGroup = [[TUIFaceGroup alloc] init];    ....    // The path of the thumbnail of the current sticker (without the extension)    programGroup.menuPath = [customFaceBundlePath stringByAppendingPathComponent:@"programer/menu"];    ....    ....}
```

### Adjusting the layout of emoji images

- `rowCount`, which indicates the number of rows of images displayed in the current emoji group.
- `itemCountPerRow`, which indicates the number of emoji images displayed per row.

For example, you can set to display the emoji images in the `programer` emoji group as two rows per page, with up to five images per row.

Swift

Objective-C

```
func setupCustomSticker() {    // ...        // 4350 group    var faces4350 = [TUIFaceCellData]()    for i in 0...17 {        let data = TUIFaceCellData()        let name = String(format: "yz%02d", i)        let path = "4350/\\(name)"        data.name = name        data.path = bundlePath + "/" + path        faces4350.append(data)    }    if faces4350.count > 0 {        let group4350 = TUIFaceGroup()        group4350.groupIndex = 1        group4350.groupPath = bundlePath + "/4350/"        group4350.faces = faces4350        group4350.rowCount = 2        group4350.itemCountPerRow = 5        group4350.menuPath = bundlePath + "/4350/menu"        service.appendFaceGroup(group4350)    }    // ...}
```

```
- (void)setupCustomSticker {    ...    // 2.2 Create the `programer` emoji group and parse it into `TUIFaceGroup`    TUIFaceGroup *programGroup = [[TUIFaceGroup alloc] init];    // The layout of the current sticker    programGroup.rowCount = 2;    programGroup.itemCountPerRow = 5;    ...}
```

## How Sticker Rendering Works

This section describes how to modify the source code or encode and pass through the content of a custom emoji.

### Sending an emoji

You can send an emoji in the callback in two steps:

- Create an emoji message with the emoji name and emoji group index.
- Call the `TUIChat` method to send the emoji message.

Swift

Objective-C

```
public func faceVerticalView(_ faceView: TUIFaceVerticalView, didSelectItemAtIndexPath indexPath: IndexPath) {    let group = faceView.faceGroups[indexPath.section]    if let face = group.faces?[indexPath.row] as? TUIFaceCellData {        if group.isNeedAddInInputBar {            inputBar?.addEmoji(face)            updateRecentMenuQueue(face.name ?? "")        } else {            let message = V2TIMManager.sharedInstance().createFaceMessage(index: Int32(group.groupIndex), data: face.name?.data(using: .utf8) ?? Data())!            delegate?.inputController(self, didSendMessage: message)        }    }}
```

```
- (void)faceView:(TUIFaceView *)faceView didSelectItemAtIndexPath:(NSIndexPath *)indexPath{    TUIFaceGroup *group = [TUIConfig defaultConfig].faceGroups[indexPath.section];    TUIFaceCellData *face = group.faces[indexPath.row];    if(indexPath.section == 0){        // Built-in emojis need to be displayed in the input box.        [_inputBar addEmoji:face];    }    else{        // Custom emojis are directly sent to the receiver.        if (face.name) {            // Create an emoji message            V2TIMMessage *message = [[V2TIMManager sharedInstance] createFaceMessage:group.groupIndex data:[face.name dataUsingEncoding:NSUTF8StringEncoding]];            // Send the message to receiver            if(_delegate && [_delegate respondsToSelector:@selector(inputController:didSendMessage:)]){                [_delegate inputController:self didSendMessage:message];            }        }    }}
```

### Parsing and rendering an emoji message

TUIChat will assign the value of the `TUIMessageCellData` to `TUIFaceMessageCell` for rendering.

For more information on the message parsing process in TUIChat, see [iOS](https://www.tencentcloud.com/document/product/1047/50043).

Swift

Objective-C

```
override class func getCellData(message: V2TIMMessage) -> TUIMessageCellData {    guard let elem = message.faceElem else { return TUIFaceMessageCellData(direction: .incoming) }    let faceData = TUIFaceMessageCellData(direction: message.isSelf ? .outgoing : .incoming)    faceData.groupIndex = elem.index    if let data = elem.data {        faceData.faceName = String(data: data, encoding: .utf8)    }    if let groups = TIMConfig.shared.faceGroups {        for group in groups {            if group.groupIndex == faceData.groupIndex {                if let url = URL(string: group.groupPath ?? "") {                    let path = url.appendingPathComponent(faceData.faceName ?? "").path                    faceData.path = path                }                break            }        }    }    faceData.reuseId = "TFaceMessageCell"    return faceData}
```

```
+ (TUIMessageCellData *)getCellData:(V2TIMMessage *)message{    // Parse the emoji information after receiving the message    V2TIMFaceElem *elem = message.faceElem;    // Create the `TUIFaceMessageCellData` for emoji display    TUIFaceMessageCellData *faceData = [[TUIFaceMessageCellData alloc] initWithDirection:(message.isSelf ? MsgDirectionOutgoing : MsgDirectionIncoming)];    // Get the order information of the current emoji group on the emoji panel    faceData.groupIndex = elem.index;    // Get the filename of the emoji image    faceData.faceName = [[NSString alloc] initWithData:elem.data encoding:NSUTF8StringEncoding];    // Get the specific path of the local sticker of the emoji image based on the name of the emoji image and the emoji group    for (TUIFaceGroup *group in [TUIConfig defaultConfig].faceGroups) {        if(group.groupIndex == faceData.groupIndex){            NSString *path = [group.groupPath stringByAppendingPathComponent:faceData.faceName];            faceData.path = path;            break;        }    }    faceData.reuseId = TFaceMessageCell_ReuseId;    return faceData;}
```


---
*Source: [https://trtc.io/document/52396](https://trtc.io/document/52396)*
