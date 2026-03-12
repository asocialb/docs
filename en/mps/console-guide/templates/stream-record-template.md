# Stream Record Template

1. MPS provides preset stream record templates. You can click **Create template** to customize stream record templates. Fill in the corresponding information on the create template page.

| Item | Description |
| --- | --- |
| Template name | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods |
| Template description | Max 256 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods |
| Recording format | Support HLS and MP4.For HLS format, you can configure: each TS segment duration, max recording duration, and resumption timeout.For MP4 format, you can configure: max recording duration. |
| TS segment duration | Must be in the range of 5～30 seconds. |
| Max recording duration | Must be in the range of 10～720 minutes. After exceeding the set max recording duration, a new file will be generated. |
| Resumption timeout | The resumption timeout period directly affects the time it takes to generate a recording file. When the interval of stream interruption does not exceed the set resumption timeout period, a single live stream will generate only one file. Please set a reasonable resumption timeout period, must be in the range of 60～1800 seconds. If not filled, it signifies that the resumption feature is disabled. |

2. The templates created can be found in the [stream record template list](https://console.tencentcloud.com/mps/templates/lives), which displays information including template name, template description, recording format, each TS time, recording cycle, resumption timeout. You can also view the details of, edit, or delete a template on this page.


---
*Source: [https://www.tencentcloud.com/document/product/1041/56732](https://www.tencentcloud.com/document/product/1041/56732)*
