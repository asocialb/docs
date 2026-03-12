# Real-Time Log Shipping

Cloud Streaming Services (CSS) supports log shipping to [Cloud Log Service (CLS)](https://console.tencentcloud.com/cls/overview) for storage, flexible retrieval, and analysis of logs. Real-time log shipping to CLS is a paid value-added service. Billing is based on the number of logs shipped.

## Notes

- Log shipping to CLS is disabled by default and can be enabled in the console or via API.
- Shipping logs to CLS may generate traffic, storage, and other fees in [CLS](https://console.tencentcloud.com/cls/overview). For detailed information, see CLS [Billing Overview](https://www.tencentcloud.com/document/product/614/37509). During the process of shipping logs to CLS, please ensure that the CLS service is functioning normally.
- The log shipping service is billed based on the number of shipped logs, and billing is carried out for 10,000 logs if the number is less than that.

### Product Pricing

| Billable Item | Price (USD/10,000 logs/day) |
| --- | --- |
| Number of real-time logs shipped to CLS | 0.000143 |

### Billing Description

- Billing item: Number of real-time logs shipped to CLS.
- Billing mode: Pay-as-you-go.
- Billing cycle: Daily. The fees for real-time logs shipped to CLS service will be deducted from your account the following day. The actual fee deduction and bill generation time are based on your billing invoice.

### Billing Formula

Fees for real-time logs shipped to CLS = Daily real-time logs shipped to CLS (10,000 logs) x CLS log shipping unit price (USD/10,000 logs/day).

### Billing Example

On February 1, 2024, the user shipped a total of 508,000 logs using real-time log shipping to CLS. The bill generated on February 2, 2024, is as follows:`Fees for CLS shipping: 51 (10,000 logs) x 0.000143 (USD/10,000 logs/day) = 0.007293 USD`

> **Note:**If your business volume is large and daily billing cannot meet your needs, you are welcome to contact us to request special pricing and billing methods. Please feel free to [submit a ticket](https://console.tencentcloud.com/workorder/category) for further consultation.


---
*Source: [https://www.tencentcloud.com/document/product/267/59101](https://www.tencentcloud.com/document/product/267/59101)*
