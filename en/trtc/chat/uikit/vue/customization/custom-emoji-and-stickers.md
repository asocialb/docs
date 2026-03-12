# Custom Emoji And Stickers

> **Note:**The usage of custom emoji capabilities described in this article is applicable to **@tencentcloud/chat-uikit-vue â¥ 2.2.0** or **@tencentcloud/chat-uikit-uniapp â¥ 2.2.0**.

In our `TUIChat` component, we support sending and receiving two types of emojis:

| Emoji Types | Sending Format | Text Mixed Layout | Sending Content | TUIKit comes with by default |
| --- | --- | --- | --- | --- |
| Small Emoji | Text Message MSG_TEXT | Yes | Emoji Image Key | Default Inclusion |
| Large Sticker | Face Message MSG_FACE | No | index: emojiGroupIDdata: Emoji Image Key | Default Inclusion |

The specific effects are as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/98051a8d2c7c11efa01d5254005235d8.png)

## Customized  Large Stickers

TUIChat supports loading customized large emoticons from **Network Path**. The following will use adding a set of Cat Emoji Pack as an example to explain how to add a set of your customized large emoticons.

### Step 1: Prepare Large Sticker Resources

1. Please name each emoji pack resource file with a filename that includes the `@custom` format identifier: TUIKit requires matching `@custom` to parse the customized emoji resources.
2. Since the parsing method for emoji packs is `URL + Emoji Image Key`, make sure to upload your new emoji pack resources to a unified network path `URL`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d901bca32c7711ef918f52540005b090.png)

### Step 2: Add Large Sticker Pack

After all your emoji pack resources have been uploaded to the web, it's necessary to add declarations for the new emoji pack resources in the `TUIKit source code`.

The `TUIKit/components/TUIChat/emoji-config/custom-emoji.ts` file is the declaration file for customized emojis.

> **Note:**If you have multi-platform interconnection needs, please ensure that the emojiGroupID of each custom emoji group and the key of each emoji within the group are consistent across all platforms.

```
import { EMOJI_TYPE } from '../../../constant';// Fill in your custom large emoji network path, example as belowexport const CUSTOM_BIG_EMOJI_URL = 'https://web.sdk.qcloud.com/im/test/emoji-test/';// Declare your custom large emoji group list, example as belowexport const CUSTOM_BIG_EMOJI_GROUP_LIST: IEmojiGroupList = [  {    emojiGroupID: 4, // Emoji Group ID    type: EMOJI_TYPE.CUSTOM, // Emoji Group Type: CUSTOM Custom Emoji Group    url: CUSTOM_BIG_EMOJI_URL, // Emoji Group Public URL Prefix    // Declaration of the emoji list, formatted as Key + Emoji File Type Suffix, every Key in the list must be unique    list: ['@custom_cat32.png', '@custom_cat33.png', '@custom_cat34.png', '@custom_cat35.png', '@custom_cat36.png', '@custom_cat37.png', '@custom_cat38.png', '@custom_cat39.png',      '@custom_cat40.png', '@custom_cat45.png', '@custom_cat46.png', '@custom_cat47.png', '@custom_cat49.png', '@custom_cat50.png', '@custom_cat51.png'],  },];
```

### Step 3: Render Custom Large Sticker

TUIKit internally supports the Custom Large Sticker Parsing feature. Following the steps above, you will achieve the following effect:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/84dd44b02c7c11ef9bb3525400ab9413.png)

## Custom Small Emoji

### Built-in Small Emoji Resources

TUIKit by default includes a set of Yellow Face emoji resources. The copyright of Yellow Face emojis is owned by Tencent Cloud. For licensing, please [contact us](https://www.tencentcloud.com/document/product/1047/41676). A comparison of Yellow Face emoji images and their meanings is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a1d7609a2c7811efb0275254006c0558.png)

### Step 1: Prepare Small Emoji Resources

Since the parsing method for emoji packs is `baseURL + Emoji Image Key`, please make sure to upload your new emoji pack resources to a unified network path `baseURL`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f0abe92d2c7711ef97da5254007d9c55.png)

### Step 2: Replace Small Emoji Resources

#### 2.1 Add Custom Small Emoji Declaration

As TUIKit requires matching `@custom` to parse custom emoji resources, **each custom small emoji resource key must include the**`@custom`**format identifier.**

Target file directory: `TUIKit/components/TUIChat/emoji-config/custom-emoji.ts`

> **Note:**If you have multi-platform interconnection needs, please ensure the key of every custom small emoji is consistently defined across all platforms.

```
@custom identifier to be parsed, example as below
```

#### 2.2 Add Internationalized Text Statement for Custom Small Emojis

##### Add key-value pairs for English meanings declaration

Target file directory: `TUIKit/components/TUIChat/emoji-config/locales/en.ts`

```
// Rewriting English Entry key-value Assertion, example as belowconst Emoji = {  '[@custom_Expect]': '[Expect]',  '[@custom_Blink]': '[Blink]',  '[@custom_Guffaw]': '[Guffaw]',  ... }
```

##### Add key-value pairs for Chinese meanings declaration

Target file directory:`TUIKit/components/TUIChat/emoji-config/locales/zh_cn.ts`

```
// Rewriting Chinese Entry key-value Assertion, example as belowconst Emoji = {  '[@custom_Expect]': '[Expect]',  '[@custom_Blink]': '[Blink]',  '[@custom_Guffaw]': '[Guffaw]',  ... }
```

### Step 3: Render Custom Small Emojis

TUIKit internally supports the custom small emojis parsing feature. After completing the above steps to replace emoticons, they can be automatically parsed and displayed within TUIChat. The effect is as follows:

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d48186112c7e11efb8c45254005a8b94.png)

## Remove system-provided emojis

The system-provided emojis' emojiGroupID corresponds to the following meme packs:

| emojiGroupID = 0 | emojiGroupID = 1 | emojiGroupID = 2 | emojiGroupID = 3 |
| --- | --- | --- | --- |
| ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/f364f75122eb11ef860b52540049c929.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/060f7b0122ec11ef860b52540049c929.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1352e0e122ec11efb2cb5254006568c0.png) | ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/1ff22dec22ec11ef91395254000a29ac.png) |

If you do not need some of the above emoji groups, you can delete the Definition for that group in `TUIKit/components/TUIChat/emoji-config/default-emoji.ts`:

> **Note:**If you have multi-platform interconnection needs, please ensure that the same emoji groups are deleted across all platforms and that the emoji group configurations remain consistent after deletion.

```
// For example, to delete the large emoji group with emojiGroupID = 1export const BIG_EMOJI_GROUP_LIST: IEmojiGroupList = [  // {  //   emojiGroupID: 1,  //   type: EMOJI_TYPE.BIG,  //   url: DEFAULT_BIG_EMOJI_URL,  //   list: ['yz00', 'yz01', 'yz02', 'yz03', 'yz04', 'yz05', 'yz06', 'yz07', 'yz08',  //     'yz09', 'yz10', 'yz11', 'yz12', 'yz13', 'yz14', 'yz15', 'yz16', 'yz17'],  // },  ...];
```


---
*Source: [https://trtc.io/document/60820](https://trtc.io/document/60820)*
