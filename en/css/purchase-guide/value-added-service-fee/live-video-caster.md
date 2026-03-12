# Live Video Caster

Billable items of Live Video Caster (LVC) include broadcast output duration, third-party relay, and value-added services. The billing mode is pay-as-you-go (bill-by-duration).

## Billing for Broadcast Output Duration

### Pay As You Go (Bill-by-Duration)

The billing of PGM duration is based on the output resolution, video type, and duration.

> **Note:**Closing the browser page does not automatically stop PGM. It continues to run in the background.After using a caster, to avoid incurring unnecessary product service fees, please go to the [Live Video Caster list page](https://console.tencentcloud.com/live/caster?rid=5) and click **Stop** for the caster. For detailed instructions, see [Live Video Caster Management](https://www.tencentcloud.com/document/product/267/58533#).

| LVC Output Specifications | Playlist Type - InternationalOriginal Price (USD/min) | Universal Type - InternationalOriginal Price (USD/min) | Output Specification Explanation |
| --- | --- | --- | --- |
| 480P and below | 0.019 | 0.0238 | 480P: long side ≤ 640px and short side ≤ 480px |
| 480P - 720P (inclusive) | 0.0276 | 0.0477 | 720P: long side ≤ 1280px and short side ≤ 720px |
| 720P - 1080P (inclusive) | 0.0477 | 0.0953 | 1080P: long side ≤ 1920px and short side ≤ 1080px |
| 1080P - 2K (inclusive) | 0.0953 | 0.1906 | 2K:  long side ≤ 2560px, and short side ≤ 1440px |
| 2K- 4K (inclusive) | 0.1906 | 0.3812 | 4K:  long side ≤ 4096px, and short side ≤ 2160px |

#### Billing details

- If your PGM output screen comprises only one stream, the [playlist type](https://www.tencentcloud.com/document/product/267/38284#) applies; if your PGM output screen comprises two or more streams, the [universal type](https://www.tencentcloud.com/document/product/267/38284#) applies.
- The long side and short side are not necessarily the width and height. The larger value is defined as the long side. For example, if the long side is 1280px and the short side is 480px, the specification is considered 720P.
- These rules only apply to the output of a single caster. If multiple casters are used, the charges will be accumulated according to the aforementioned rules.
- Billing method: Daily pay-as-you-go
- Billing cycle: PGM duration fees each day are billed the following day.

#### Fee calculation

LVC output duration fee = Tiered price corresponding to LVC output specifications × Output duration.

#### Billing example

Assume that a user used a caster instance for broadcasting on July 12, 2022, with the PGM output specification being 1080P, the output screen type being the single-stream playlist type, and the output duration being 60 minutes, the actual consumption bill generated on July 13, 2022 would be: 0.0477 USD/min × 60 min = 2.862 USD.

## Billing for Relay to Third Party

When you use the relay feature of Cloud Streaming Services to direct live broadcasts to third-party addresses, you will be billed based on the bandwidth usage of the relay. The billing is based on the peak bandwidth (unit: Mbps) generated in the relay service's region during the billing cycle. The relay service's region is the region streams are relayed to. If the relay service occurs in multiple regions in the same billing cycle, billing will occur separately based on the bandwidth peaks of the involved regions.

| Region | Price (USD/Mbps/Month) |
| --- | --- |
| Chinese mainland | 12.67 |
| Hong Kong (China) | 12.67 |
| Singapore | 8.04 |
| Frankfurt | 7.1 |
| Seoul | 16.56 |
| India | 23.66 |
| Thailand | 13.01 |
| Silicon Valley, USA | 7.1 |
| Virginia, USA | 7.1 |
| Jakarta | 17.4 |
| Japan | 13.01 |
| Sao Paulo | 23.66 |
| Other | 12.67 |

#### Billing details

- Billing mode: Monthly pay-as-you-go
- Billing cycle: Fees for each month are billed within the first three days of the following month.
- Billable bandwidth: The billing takes the concurrent bandwidth of all relay tasks into account. The default billing mode is pay-as-you-go. Charges are based on the monthly average of peak bandwidth used each day.

#### Fee calculation

Third-party relay fee = Billable bandwidth for relay × Unit price.

#### Billing example

Assume that on May 3, 2023, a user used a caster instance for broadcasting, with the PGM output specification being 1080P, the output screen type being the single-stream playlist type, and the output duration being 60 minutes; on May 20, 2023, the user also used a caster instance for broadcasting, with the same PGM output specification and the output screen type as that used previously, but the output duration was 100 minutes. For both instances, the user set a third-party relay address, which was located in Silicon Valley, USA. The peak bandwidth used on the two days was 15Mbps and 16Mbps, respectively. Each output duration bill would be generated on the following day, while the third-party relay bill would be generated on June 1 to June 3. In this case, the actual consumption in May would be: 0.0477 USD/min × 60 min + 0.0477 USD/min × 100 min + 7.1 USD/Mbps × (15 Mbps + 16 Mbps)/31-days = 14.732 USD.

## Possible Costs

As a tool-based product, LVC itself only incurs three fees: broadcast output duration fees, third-party relay fees, and value-added feature fees. However, during your use of LVC, you might need services from products like Cloud Streaming Services and Video on Demand. These services might incur normal usage fees such as VOD traffic fees, live recording fees, and stream publishing fees.  For related billing instructions, see [Billing of LVB](https://www.tencentcloud.com/document/product/267/2818) and [Billing of VOD](https://www.tencentcloud.com/document/product/266/14666).

> **Note:**After using a caster, turn off the output and go to the [List Page](https://console.tencentcloud.com/live/caster?rid=5) to stop the caster in a timely manner to avoid incurring unnecessary charges from other product services.


---
*Source: [https://www.tencentcloud.com/document/product/267/58538](https://www.tencentcloud.com/document/product/267/58538)*
