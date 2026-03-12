# Intelligent Porn Detection

CSS provides porn detection. Because CSS needs to take screenshots in live streams to detect pornographic content, using porn detection will incur [porn detection fees](https://www.tencentcloud.com/document/product/267/39607#8146365a-6b3b-466f-936b-3d8a468c3b8e) and [screencapture fees](https://intl.cloud.tencent.com/document/product/267/39606). Porn detection is **billed by the total number of images moderated for pornographic content each month.**

## Notes

- Porn detection is disabled by default and can be enabled in the console.
- The generated screenshots are stored in COS and will incur COS storage fees. For details, please see [COS Pricing](https://intl.cloud.tencent.com/pricing/cos).
- Porn detection is a paid feature. **The first 1,000 screenshots moderated each month are free. Any additional screenshots moderated will incur fees.**
- Usage deduction for screen audit occurs during use. You must ensure that your account is not overdue. If your account is in an overdue state (negative balance and overdue credit account), the usage deduction will fail.

## Pricing

| Moderated Screenshots | Price (USD/Thousand screenshots) | Notes |
| --- | --- | --- |
| ≤ 1000 | 0 | The first 1,000 screenshots moderated each month are free |
| ＞ 1000 | 0.2294 | The total number of screenshots will be rounded up to the nearest 1,000 |

> **Note:**For screenshots stored in [COS](https://intl.cloud.tencent.com/document/product/436/6222) outside the Chinese mainland, additional public network downstream traffic fees will be incurred. For the detailed prices of specific billable COS items, please see [COS Pricing](https://buy.tencentcloud.com/price/cos/overview).

## Billing Overview

- Billable item: The number of screenshots moderated for pornographic content.
- Billing mode: Pay-as-you-go.
- Billing cycle: Monthly billing cycle. The current month's bill will be generated between the 1st and 5th day of the next month. Please refer to your actual billing statement for details.
- Billing rules: Fees are calculated by multiplying the total number of screenshots moderated (with the first 1,000 free screenshots deducted) in a calendar month and the unit price.

## Billing Sample

Suppose you used the porn detection service from January 1 to February 1, 2021, and a total of 168,000 screenshots were moderated for pornographic content in January. The porn detection fees you would need to pay on February 2, 2021 would be as follows: Porn detection fees for January = 0.2294 (USD/Thousand screenshots) × (168 - 1) Thousand screenshots = 38.3098 USD.


---
*Source: [https://www.tencentcloud.com/document/product/267/39607](https://www.tencentcloud.com/document/product/267/39607)*
