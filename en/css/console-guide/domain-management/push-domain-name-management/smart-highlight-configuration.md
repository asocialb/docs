# Smart Highlight Configuration

The Smart Highlight feature is disabled by default for live streaming. This article will show you how to enable the Smart Highlight feature when associating a Smart Highlight template with a specified push domain, and how to unbind the template and disable the Smart Highlight feature after successful association.

## Notes

- After the template is successfully created, it can be associated with the push domain name. It will take about 5-10 minutes to take effect after successful association, and Smart Highlight will be triggered as soon as the associated domain successfully pushes data.
- Template modifications, bindings, and unbindings only affect live streams updated thereafter. Ongoing live streams remain unaffected; to apply new rules, the ongoing stream must be interrupted and re-pushed.
- Only one Smart Highlight template can be associated with a domain. Once associated, all streams under that domain will be Smart Highlight in accordance with the associated template.

## Prerequisites

- You have successfully logged in to the [CSS console](https://console.tencentcloud.com/live/livestat) and have completed [Adding Your Own Domain](https://www.tencentcloud.com/document/product/267/35970).
- The Smart Highlight template has been successfully created.

## Associating Smart Highlight Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click **Domain Name** you want to configure or **Manage** to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/d77ddc24c5b711f0a62b5254007c27c5.png)

2. Select the **Template Configuration** tab. Click**Edit**in the top-right corner of **Smart Highlight** **Configuration**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/b8f0de0ac5ba11f086d9525400e889b2.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/cc257e90c5ba11f0a7ca5254001c06ec.png)

3. Choose a Smart Highlight configuration template according to your business requirements and click **Confirm** to complete the configuration.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ecaebc8fc5ba11f0a62b5254007c27c5.png)

## Unbinding Smart Highlight Template

1. Go to [Domain Management](https://console.tencentcloud.com/live/domainmanage). Click **Domain** **Name** you want to configure or **Manage** to enter the domain details page.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/dd967c6dc5b711f0a7ca5254001c06ec.png)

2. Select the **Template Configuration** tab and click Edit in the top-right corner of **Smart Highlight Configuration**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/9e6766f9c5ba11f0a62b5254007c27c5.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/06c24c54c5bb11f0a62b5254007c27c5.png)

3. Based on your business requirements, uncheck the relevant template and click **Confirm** to proceed.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/15775d62c5bb11f085c7525400454e06.png)

> **Note:**Unbinding a Smart Highlight template does not affect ongoing live streams.


---
*Source: [https://www.tencentcloud.com/document/product/267/74573](https://www.tencentcloud.com/document/product/267/74573)*
