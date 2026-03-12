# Purchase Instructions

## Signing Up

Before using MPS, you need to [sign up for a Tencent Cloud account](https://intl.cloud.tencent.com/document/product/378/17985).

## Authorizing

### Step 1. Log in

Log in to the [MPS console](https://console.tencentcloud.com/mps).

### Step 2. Grant access to COS

MPS needs read and write access to COS in order to download videos from COS buckets and upload files to COS buckets after transcoding. Therefore, you need to create a service role to grant MPS access to COS.
In the

MPS console

, click

**Go to CAM**

to grant the access.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/4d9f3ae0d6d811ee9409525400c26da5.png)

> **Note:**You cannot perform further operations in the MPS console before granting the permissions.

## Using MPS

After authorization, you can start using media processing services in the [MPS console](https://console.tencentcloud.com/mps).

## Billing

Currently, MPS supports two billing modes: [pay-as-you-go](https://www.tencentcloud.com/document/product/1041/49204) and [prepaid resource packs](https://intl.cloud.tencent.com/document/product/1041/48810).

- **Daily pay-as-you-go**: Each day, the system calculates your usage in the previous day, sends you a bill, and deducts the fee from your account balance. In this mode, you need to [top up](https://console.tencentcloud.com/expense/recharge) your account accordingly.
- **Monthly pay-as-you-go**: On the first day of each month, the system calculates your usage in the previous month, generates a bill, and deducts the fee from your account balance. In this mode, you need to [top up](https://console.tencentcloud.com/expense/recharge) your account accordingly.
- **Prepaid resource packs**: With resource packs, MPS resources are sold in packages. You [buy resource packs](https://buy.tencentcloud.com/mps) before using MPS, and your usage each day will be deducted from resource packs first. After your resource packages are used up, the remaining usage (if any) is billed at daily pay-as-you-go rates. For details, see [Resource Packs](https://intl.cloud.tencent.com/document/product/1041/48810).


---
*Source: [https://www.tencentcloud.com/document/product/1041/44041](https://www.tencentcloud.com/document/product/1041/44041)*
