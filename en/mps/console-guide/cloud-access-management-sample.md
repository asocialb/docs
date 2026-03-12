# Cloud Access Management Sample

## Introduction

You can authorize users to view and use the specific resources in the Media Processing Service (MPS) console via the Cloud Access Management (CAM) policies. This document provides authorization examples to view and use the specific resources, which can help users understand how to use the specific CAM policies by using the MPS console.

## Examples

#### Read and write full access(MPS)

You can use the policy named QcloudMPSFullAccess for users. This policy is designed to grant users the permissions to access all the resources in MPS.
The detailed steps are as follows:
Refer to [Authorization Management](https://www.tencentcloud.com/document/product/598/10602) for instructions on how to grant the preset policy QcloudMPSFullAccess to users.

#### Access for MPS role

You can use the policy named QcloudAccessForMPSRole for users. This policy is designed to grant users the permissions to read the Object Storage (COS) bucket list, read and write bucket configurations and read or upload objects. It also includes the capability to transmit messages via the Message Queue (CMQ).

The detailed steps are as follows:
Refer to [Authorization Management](https://www.tencentcloud.com/document/product/598/10602) for instructions on how to grant the preset policy QcloudAccessForMPSRole to users.

#### Access for MPS role in deliver to SCF

You can use the policy named QcloudAccessForMPSRoleInDeliverToSCF for users. This policy is designed for association for MPS QCSRole, used for temporary access to other cloud service resources by MPS.

The detailed steps are as follows:
Refer to [Authorization Management](https://www.tencentcloud.com/document/product/598/10602) for instructions on how to grant the preset policy QcloudAccessForMPSRoleInDeliverToSCF to users.


---
*Source: [https://www.tencentcloud.com/document/product/1041/58146](https://www.tencentcloud.com/document/product/1041/58146)*
