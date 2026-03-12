# Real-Time Log Analysis

Real-time log analysis enables quick retrieval, analysis, and storage of log data through the real-time collection and delivery of CSS access logs to Tencent Cloud Log Service (CLS). This enables you to mine log data for data-driven operations and management, allowing for the rapid and accurate development of operational strategies.

> **Note:**Real-time log analysis now fully supports shipping logs to [Cloud Log Service](https://console.tencentcloud.com/cls/overview). This document will guide you on how to use the real-time log feature.

## Notes

- Log data is collected in real-time, with log search and reporting data stabilizing after three minutes.
- Currently, reporting analysis is only available for playback logs. If you have other log management needs, visit [Cloud Log Service](https://console.tencentcloud.com/cls/overview).
- After enabling the log delivery feature, ensure that your CLS service is in normal operation, as the suspension of CLS will prevent the delivery of logs.
- The bandwidth or traffic data recorded in logs is the application layer (HTTP protocol) return data. Due to mechanisms like TCP header consumption and failed retransmissions, it is smaller than the bandwidth or traffic consumption calculated at the TCP layer.

## Operation Instructions

### Creating a log topic

1. Go to the CSS console and select **Monitoring**> **Cloud Log Service** > [Real-time log analysis](https://console.tencentcloud.com/live/logmanage) to enter the real-time log analysis page.
2. If this is your first time using this feature, you need to use your CSS service role to grant authorization. After authorization, you need to agree to the service agreement and click **Start**. The system will automatically activate the CLS product and open the real-time log analysis management page.
3. Choose a region and click the link on the page to create a new logset.

> **Note:**The region includes Guangzhou and Singapore. Log topics created under the logset in the Guangzhou region can only deliver logs within the Chinese mainland. In contrast, log topics created under the logset in the Singapore region can only deliver logs globally, including to Hong Kong (China), Macao (China), and Taiwan (China).

![](https://staticintl.cloudcachetci.com/cms/backend-cms/6296a4b2e4ce11eeb1eb525400b5f95f.png)

4. Click **Confirm**to create a new logset.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/f2e868553e8e11efa56d525400d5f8ef.png)

5. After successfully creating a logset, click **Create Log Topic** to enter the log topic creation page. The newly created log topic will by default be in the process of delivering logs to CLS.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/28dbf47e3e9911ef8ba05254002693fd.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3bd887c53e9811ef8fe4525400446153.png)

### Modifying a log topic

1. Enter the log topic list in real-time log analysis and click **Manage** in the operation column of the log topic you need to modify.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3e3ba0443e9911efa3db525400f69702.png)

2. Enter the log topic editing page to modify the log topic information.

### Analyzing a log report

Only log topics of the log type provide report analysis. There are four types of data on the page: **Basic Data Analysis, Resource Distribution Analysis, Exception Diagnosis Analysis,**and**User Analysis**.

1. Enter the log topic list in **Real-time Log Analysis**and click **Report** on the right side of the log topic you want to view.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/526a25123e9911ef8ba05254002693fd.png)

2. Enter the log report page to view report data; you can separately view **Basic Data**, **Resource Distribution**, **Exception Diagnosis**, and **User Analysis**.

Basic Data

Resource Distribution

Exception Diagnosis

User Analysis

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d34a9388440c11efa24b525400a9236a.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ebb5fe02440c11efaf995254002693fd.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/62a47e3be4ce11eeadff525400e97a5f.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4f6dd60f440d11efa917525400fdb830.png)

### Log Search

Log search supports multiple types of retrieval and analysis methods, as well as various forms of chart analysis. For detailed information, see [Log Search and Analysis](https://www.tencentcloud.com/document/product/614/12503?from_cn_redirect=1).

Log search is performed based on log topics. Select the log topic you need to search for and click Search to enter the log search page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ea9b33283e9a11ef973e525400a9236a.png)

### Stop shipping a log topic to CLS

1. Enter the log topic list in Real-time Log Analysis and click **Stop**on the right of the log topic you wish to stop shipping.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/351865a73e9b11ef97e452540055f650.png)

2. In the pop-up window, click Confirm to stop shipping. The status of the corresponding log topic will change to "stop shipping", and logs will no longer be shipped to CLS.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/627e68aae4ce11eeadff525400e97a5f.png)

### Deleting a log topic

> **Note：**Once a log topic is deleted, it cannot be recovered. Please proceed with caution.If you delete a log topic, you will stop pushing log data of the related domain, the corresponding log topic in CLS will also be deleted, and all shipped logs will be cleared. Meanwhile, you will no longer be able to use the report associated with that topic.

1. Enter the log topic list in **Real-time Log Analysis**and click **Delete** on the right side of the log topic you wish to remove.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4b78481b3e9b11efa3db525400f69702.png)

2. In the pop-up window, confirm whether to delete the log topic and click **OK** to proceed.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1cf455483e9511ef97e452540055f650.png)

## Log Fields

### Push logs

| Order | Log Field | Description |
| --- | --- | --- |
| 1 | time | Request time |
| 2 | client_ip | Client IP |
| 3 | host | Accessed domain name |
| 4 | url | URL |
| 5 | size | Stream push byte size |
| 6 | country_id | Country ID |
| 7 | prov | Province |
| 8 | isp | ISP |
| 9 | streamname | Stream ID |
| 10 | node_ip | Node IP |
| 11 | server_region | Server region |
| 12 | server_country | Server country |

### Playback logs

| Order | Log Field | Description |
| --- | --- | --- |
| 1 | type | Playback type: lvb represents Live Video Broadcasting and leb represents Live Event Broadcasting |
| 2 | time | Request time |
| 3 | client_ip | Client IP |
| 4 | host | Accessed domain name |
| 5 | url | URL |
| 6 | size | Byte size of this access request |
| 7 | country_id | Country ID |
| 8 | prov | Province |
| 9 | isp | ISP |
| 10 | http_code | HTTP status code |
| 11 | referer | Referer information |
| 12 | process_time | Processing duration (in milliseconds) |
| 13 | ua | User-Agent information |
| 14 | range | Range parameter |
| 15 | method | HTTP Method |
| 16 | streamname | Stream ID |
| 17 | hit | Cache hit/miss |
| 18 | node_ip | Node IP (This field may be empty for the IP addresses of certain CDN cluster nodes cannot be obtained.) |
| 19 | server_region | Server region |
| 20 | server_country | Server country |
| 21 | connect_fd | Connection port number |
| 22 | lost_rate | The packet loss rate, only valid for type=leb |
| 23 | rtt | Round-trip time, only valid for type=leb |

> **Note:**The special status codes in the log are as follows:0: Connection established.4: Request timed out, authentication timed out, or response timed out.5: Origin server disconnected or stream terminated.6: Client disconnected.

- **Country (Region) Mapping:**

```
  **China：1**，**Bahrain：2**，**South Korea：3**，**Lebanon：4**，**Nepal：5**，**Thailand：6**，**Pakistan：7**，**United Arab Emirates：8**，**Bhutan：9**，**Oman：10**，**Azerbaijan：11**，**North Korea：12**，**Philippines：13**，**Cambodia：14**，**Qatar：15**，**Kyrgyzstan：16**，**Maldives：17**，**Malaysia：18**，**Saudi Arabia：20**，**Cyprus：21**，**Brunei：22**，**Laos：23**，**Japan：24**，**Turkmenistan：25**，**Türkiye：26**，**Kazakhstan：27**，**Palestine：28**，**Tajikistan：29**，**Tajikistan：30**，**Kuwait：31**，**Syria：32**，**India：33**，**Indonesia：34**，**Armenia：35**，**Afghanistan：36**，**Afghanistan：37**，**Sri Lanka：38**，**Iraq：39**，**Vietnam：40**，**Iran：41**，**Yemen：42**，**Jordan：43**，**Myanmar：44**，**Sikkim：45**，**Bangladesh：46**，**Singapore：47**，**Israel：48**，**Egypt：49**，**Burkina Faso：50**，**Madagascar：51**，**Algeria：52**，**Burundi：53**，**Equatorial Guinea：54**，**Togo：55**，**Angola：56**，**Ethiopia：57**，**Nigeria：58**，**South Africa：59**，**Senegal：60**，**Cape Verde：61**，**The Democratic Republic of Sao Tome and Principe：62**，**Swaziland：63**，**Niger：64**，**Mauritius：65**，**Guinea-Bissau：66**，**Eritrea：67**，**Tanzania：68**，**Sudan：69**，**Guinea：70**，**Côte d'Ivoire：71**，**Chad：72**，**Comoros：73**，**Sierra Leone：74**，**Central African Republic：75**，**Zambia：76**，**Uganda：77**，**Mauritania：78**，**Libya：79**，**Cameroon：80**，**Djibouti：81**，**Liberia：82**，**Zimbabwe：83**，**Congo：84**，**Mali：85**，**Lesotho：86**，**Gabon：87**，**Morocco：88**，**Gambia, The：89**，**Ghana：90**，**Kenya：91**，**Malawi：92**，**Namibia：93**，**Seychelles：94**，**Botswana：95**，**Mozambique：96**，**Benin：97**，**Rwanda：98**，**Somali：99**，**Tunisia：100**，**Ivory coast：101**，**France：102**，**Albania：103**，**Dublin：104**，**Estonia：105**，**Andorra：106**，**Monaco：107**，**Luxembourg：108**，**Spain：109**，**Sweden：110**，**Macedonia：111**，**Italy：112**，**San Marino：113**，**Hungary：114**，**The Socialist Federal Republic of Yugoslavia：115**，**Greece：116**，**Switzerland：117**，**Moldova：118**，**Lithuania：119**，**Latvia：120**，**Vatican City State：121**，**Iceland：122**，**Poland：123**，**United Kingdom：124**，**Liechtenstein：125**，**Slovakia：126**，**Netherlands：127**，**Ukraine：128**，**Portugal：129**，**Malta：130**，**Belgium：132**，**Croatia：133**，**Finland：134**，**Bulgaria：135**，**Germany：136**，**Czech Republic：137**，**Romania：138**，**Norway：139**，**Slovenia：140**，**Austria：141**，**Belarus：142**，**Denmark：143**，**Bosnia and Herzegovina：144**，**Ireland：145**，**Argentina：146**，**Paraguay：147**，**Brazil：148**，**Bolivia：149**，**Venezuela：150**，**Chile：151**，**Uruguay：152**，**Suriname：153**，**Peru：154**，**Colombia：155**，**Ecuador：156**，**Guyana：157**，**Dominican Republic：158**，**Bahamas：160**，**Panama：161**，**Nicaragua：162**，**Barbados：163**，**Jamaica：164**，**Haiti：165**，**Mexico：166**，**Guatemala：167**，**Cuba：168**，**Honduras：169**，**Grenada：170**，**Costa Rica：171**，**Dominica：172**，**Saint Christopher and Nevis：173**，**United States：174**，**Saint Vincent and the Grenadines：175**，**Trinidad and Tobago：176**，**Antigua and Barbuda：177**，**Dominica：178**，**Belize：179**，**El Salvador：180**，**Canada：181**，**Saint Lucia：182**，**Australia：183**，**Nauru：184**，**Palau：185**，**Papua New Guinea：186**，**Samoa：187**，**Fiji：188**，**Solomon Islands：189**，**Kiribati：190**，**Micronesia：191**，**Tuvalu：192**，**New Zealand：193**，**Tonga：194**，**Marshall Islands：195**，**Vanuatu：196**，**Mongolia：197**。
```

- **Provincial Mapping:**

```
**Beijing：1**，**Tianjin：2**，**Hebei：3**，**Shanxi：4**，**Inner Mongoria：5**，**Jiangsu：6**，**Anhui：7**，**Shandong：8**，**Liaoning：9**，**Jilin：10**，**Heilongjiang：11**，**Shanghai：12**，**Zhejiang：13**，**Jiangxi：14**，**Fujian：15**，**Hubei：16**，**Hunan：17**，**Henan：18**，**Guangdong：19**，**Guangxi：20**，**Hainan：21**，**Chongqing：22**，**Sichuan：23**，**Guizhou：24**，**Yunnan：25**，**Xizang：26**，**Shaanxi：27**，**Gansu：28**，**Ningxia：29**，**Qinghai：30**，**Xinjiang：31**，**China Hongkong：32**，**China Macao：33**，**China Taiwan：34**。
```

- **Carrier Mapping:**

```
**China Telecom：1**，**China Netcom：2**，**Cernet：3**，**China Mobile：4**，**China Unicom：5**，**China Railcom：6**，**Great Wall Broadband Network：7**，**Telecom：8**，**PCCW：9**，**Oriental Cable：10**，**Hutchison Telecommunications：11**，**City Telecom：12**，**Gehua：13**，**Founder Broadband：14**，**Tianwei：15**，**Hong Kong Cable：16**，**SmarTone：17**，**University：18**，**Consulting Networking：19**，** CITIC Pacific：20**，**New World Telecommunications：21**，**Hengtong International：22**，**Wharf Telecommunication：23**，** Pacnet：24**，**First Line：25**，**Connectivity Advantage：26**，**Keying Telecom：27**，**CNLink Networks：28**，**New Network：29**，**SunnyVision：30**，**Chunghwa Telecom：31**，**New Electricity：32**，**First：33**，**Hong Kong Information Technology：34**，**Nanling：35**，**Alibaba：36**，**Tencent：37**，**Dr.Peng：38**，**Radio And Television：40**，**Hong Kong Broadband：41**，** Technology Network：42**，**WangSu：43**，**akamai：44**，**Zhejiang Huashu：45**。
```

- **Server Region and Country (Region) Mapping:**

| Region | Country (region) |
| --- | --- |
| China | China |
| Asia Pacific 1 | China Hongkong |
|  | China Macao |
|  | Singapore |
|  | Vietnam |
|  | Thailand |
| Asia Pacific 2 | China Taiwan |
|  | Japan |
|  | Malaysia |
|  | Indonesia |
|  | South Korea |
| Asia Pacific 3 | Philippines |
|  | India |
|  | Australia |
| Middle East | Saudi Arabia |
|  | United Arab Emirates |
|  | Türkiye |
| North America | United States |
|  | Canada |
| Europe | United Kingdom |
|  | Germany |
|  | France |
|  | Italy |
|  | Ireland |
|  | Spain |
| South America | Brazil |
| Africa | South Africa |

## Definitions

### Logset

A logset classifies log topics and metric topics and can contain multiple log topics and metric topics. A logset itself does not store any log data, it only facilitates user management of topics. CSS logsets have the following basic attribute information:

- Region: The [region](https://www.tencentcloud.com/document/product/614/18940?from_cn_redirect=1) to which a logset belongs.

> **Note：**Guangzhou and Singapore regions are currently supported.

- Logset Name: The name of a logset.
- Retention period: The default retention period for data in the log set is 30 days.
- Creation time: Logset creation time.

### Log Topic

A log topic is a basic unit for log data collection, storage, retrieval, and analysis on the CLS platform. The vast amounts of logs collected are managed by log topic, including the configuration of the collection rules and storage time, log search and analysis, and log download, consumption, and delivery.

Log topic features include:

- Collect logs to log topics.
- Store and manage logs based on log topics.
- Search and analyze logs by log topics.
- Ship logs to other platforms based on log topics.
- Download and consume logs from log topics.

> **Note：**The information above is excerpted from the CLS product documentation. For more details, see [Log Topic and Logset](https://www.tencentcloud.com/document/product/614/32849) and refer to the CLS documentation for accurate information.


---
*Source: [https://www.tencentcloud.com/document/product/267/59877](https://www.tencentcloud.com/document/product/267/59877)*
