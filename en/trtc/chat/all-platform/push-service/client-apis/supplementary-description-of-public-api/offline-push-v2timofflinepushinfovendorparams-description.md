# Offline push V2TIMOfflinePushInfo.vendorParams description

This article introduces the field descriptions and usage example of offline push `V2TIMOfflinePushInfo.vendorParams`.

## Field Description

| Field | Type | Attribute | Usage Instructions | Remarks |
| --- | --- | --- | --- | --- |
| fcmPriority | String | Optional. | FCM push message priority settings"normal": Ordinary priority. When the app runs in the foreground, ordinary priority messages will be transmitted immediately. When the app runs in the background, message delivery may be delayed. For time-insensitive messages (such as new email notifications, keeping the interface synchronized, or syncing app data in the background), we recommend you select ordinary delivery priority."high": High priority. Even if the device is in low-power mode, FCM will immediately attempt to transmit high-priority messages. High-priority messages are suitable for time-sensitive, user-visible content. | None |
| vivoNotifyType | Integer | Optional. | vivo notification type:None2: Ring.3: Vibration.4: Ring and vibration.Default value: 4. | None |
| oppoTemplateId | String | Optional. | The template ID for OPPO private message application. For the application method, see [OPPO Private Message Channel](https://www.tencentcloud.com/document/product/1047/60576#d6a5a27f-af6d-459c-b006-a133df86729e):The corresponding private message template must be carried when sending. Custom content is not supported. | **Note:**The console also supports setting a template ID separately, primarily used to push messages in Chat scenarios (**category = "IM"**). Template ID takes effect:After setting the template ID in console settings, the title and desc field contents of [V2TIMOfflinePushInfo](https://im.sdk.qcloud.com/doc/zh-cn/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html) will be automatically filled with the template title and content, as follows:{    "oppoTitleParam": {         "title":"titleInfo"     },    "oppoContentParam":{        "desc":"descInfo"    }} Application template example:TemplateID: IDMessage Type: IMTitle: ${title}$Content: ${desc}$**The above solution supports offline message adaptation for private message template feature in existing Chat scenarios, achieving the goal where existing users' Chat messages can still be delivered via private message channel. This method is also recommended for Chat-type messages to utilize private message templates.** |
| oppoTitleParam | JSON | Optional. | OPPO title template fill parameters:Example: Private message template ID title template: Welcome to ${city}, ${city} welcomes you.The parameter content is: {"city":"Beijing"} |  |
| oppoContentParam | JSON | Optional. | OPPO content template fill parameters:Example: Private message template ID content template: Welcome ${userName} to ${city}.The parameter content is: {"userName":"Tom", "city":"Shenzhen city"} |  |

### Usage Example

Android

iOS

C++

Java

Kotlin

```
V2TIMOfflinePushInfo v2TIMOfflinePushInfo = new V2TIMOfflinePushInfo();Map<String, Object> map = new HashMap<>();map.put("fcmPriority", "high");map.put("vivoNotifyType", 4);map.put("oppoTemplateId", "oppoid");Map<String, Object> oppoTitleMap = new HashMap<>();oppoTitleMap.put("title", "title");map.put("oppoTitleParam", new Gson().toJson(oppoTitleMap));Map<String, Object> oppoContentMap = new HashMap<>();oppoContentMap.put("desc", "desc");map.put("oppoContentParam", new Gson().toJson(oppoContentMap));String param = new Gson().toJson(map);v2TIMOfflinePushInfo.setVendorParams(param);
```

```
val map = mutableMapOf<String, Any>(    "fcmPriority" to "high",    "vivoNotifyType" to 4,    "oppoTemplateId" to "oppoid")val oppoTitleMap = mapOf("title" to "title")map["oppoTitleParam"] = Gson().toJson(oppoTitleMap)val oppoContentMap = mapOf("desc" to "desc")map["oppoContentParam"] = Gson().toJson(oppoContentMap)val param = Gson().toJson(map)V2TIMOfflinePushInfo v2TIMOfflinePushInfo = new V2TIMOfflinePushInfo();v2TIMOfflinePushInfo.setVendorParams(param)
```

OC

Swift

```
NSMutableDictionary *map = [@{    @"fcmPriority": @"high",    @"vivoNotifyType": @4,    @"oppoTemplateId": @"oppoid"} mutableCopy];NSDictionary *oppoTitleMap = @{@"title": @"title"};NSData *titleData = [NSJSONSerialization dataWithJSONObject:oppoTitleMap options:0 error:nil];NSString *oppoTitleJson = [[NSString alloc] initWithData:titleData encoding:NSUTF8StringEncoding];[map setObject:oppoTitleJson forKey:@"oppoTitleParam"];NSDictionary *oppoContentMap = @{@"desc": @"desc"};NSData *contentData = [NSJSONSerialization dataWithJSONObject:oppoContentMap options:0 error:nil];NSString *oppoContentJson = [[NSString alloc] initWithData:contentData encoding:NSUTF8StringEncoding];[map setObject:oppoContentJson forKey:@"oppoContentParam"];NSData *paramsData = [NSJSONSerialization dataWithJSONObject:map options:0 error:nil];NSString *params = [[NSString alloc] initWithData:paramsData encoding:NSUTF8StringEncoding];V2TIMOfflinePushInfo *v2TIMOfflinePushInfo = [[V2TIMOfflinePushInfo alloc] init];v2TIMOfflinePushInfo.vendorParams = params;
```

```
var map: [String: Any] = [    "fcmPriority": "high",    "vivoNotifyType": 4,    "oppoTemplateId": "oppoid"]let oppoTitleMap: [String: String] = ["title": "title"]if let titleData = try? JSONSerialization.data(withJSONObject: oppoTitleMap),   let oppoTitleJson = String(data: titleData, encoding: .utf8) {    map["oppoTitleParam"] = oppoTitleJson}let oppoContentMap: [String: String] = ["desc": "desc"]if let contentData = try? JSONSerialization.data(withJSONObject: oppoContentMap),   let oppoContentJson = String(data: contentData, encoding: .utf8) {    map["oppoContentParam"] = oppoContentJson}let paramsData = try! JSONSerialization.data(withJSONObject: map)let params = String(data: paramsData, encoding: .utf8)!let v2TIMOfflinePushInfo = V2TIMOfflinePushInfo()v2TIMOfflinePushInfo.vendorParams = params;
```

```
#include <sstream>#include <string>V2TIMOfflinePushInfo offline_push_info;//std::string param = R"({"fcmPriority":"high","vivoNotifyType":4})";std::ostringstream param;// Build the main structparam << "{";param << "\\"fcmPriority\\":\\"high\\",";param << "\\"vivoNotifyType\\":4,";param << "\\"oppoTemplateId\\":\\"oppoid\\",";// Build the json string of oppoTitleParamstd::string oppo_title_json = "{\\"title\\":\\"title\\"}";param << "\\"oppoTitleParam\\":\\"";for (const char c : oppo_title_json) {    // Escape double quotes in nested json    if (c == '"') oss << '\\\\';    oss << c;}param << "\\",";// Build the json string of oppoContentParamstd::string oppo_content_json = "{\\"desc\\":\\"desc\\"}";param << "\\"oppoContentParam\\":\\"";for (const char c : oppo_content_json) {    if (c == '"') oss << '\\\\';    oss << c;}param << "\\"}"; offline_push_info.vendorParams = param.str();
```

> **Note:**IMSDK 8.7 and above versions support.

## API Reference

Android: [V2TIMOfflinePushInfo](https://im.sdk.qcloud.com/doc/en/classcom_1_1tencent_1_1imsdk_1_1v2_1_1V2TIMOfflinePushInfo.html)

iOS:[V2TIMOfflinePushInfo](https://im.sdk.qcloud.com/doc/en/interfaceV2TIMOfflinePushInfo.html)

C++:[V2TIMOfflinePushInfo](https://im.sdk.qcloud.com/doc/en/structV2TIMOfflinePushInfo.html)


---
*Source: [https://trtc.io/document/73940](https://trtc.io/document/73940)*
