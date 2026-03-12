# Custom Keyword Library

You can use a custom keyword library for image and audio moderation. A custom library may contain keywords to allow or block. The configuration takes effect within 10 minutes.

## Creating a New Library

1. Log in to the [CSS console](https://console.tencentcloud.com/live/livestat) and navigate to Feature Configuration > Content moderation > **Keyword libraries**.
2. Click **Create library**. In the pop-up window, fill in the configuration items based on your actual business requirements.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/c77e95d03b8b11f0be2052540099c741.png)

| Configuration Item | Required Item | Description |
| --- | --- | --- |
| Library name | Yes | Library Name. It can contain up to 32 characters of Chinese characters, letters, digits, and underscores. |
| Suggestion | Yes | You can select **Block** or **Review**.Block: The information is confirmed to be blocked.Review: The information might be undesirable and requires manual recognition.**Note:**The handling of matched content varies with the suggestion you choose. This corresponds to the "Suggestion" parameter returned by the API. |
| Match mode | Yes | Exact matching only supports Chinese.Exact matching identifies content that exactly matches the keywords specified. |

![](https://staticintl.cloudcachetci.com/cms/backend-cms/fa25d40f3b9011f0b95f5254005ef0f7.png)

3. Click **Confirm** to save the library configuration.

## Modifying a Keyword Library

#### Steps

1. On the keyword libraries page, find the library you want to modify, click **Edit** on the right, and modify the configuration in the pop-up window on the right according to your business requirements.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2496e2683b9111f08806525400bf7822.png)

2. Click **Add keyword** and enter keywords in the pop-up window.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/aa3299193ba511f0aed2525400e889b2.png)

![](https://staticintl.cloudcachetci.com/cms/backend-cms/2117672daa0e11ee9939525400461a83.png)

You can select a **category** for the **keywords** you add. Separate multiple keywords by pressing Enter. You can enter at most 2,000 keywords at a time.

> **Note:**Only supports the recognition of sensitive words in Chinese.Keywords are confirmed by newline. Each keyword length is within 20 Chinese characters.You can also copy keywords (max 2,000) to the input box. Make sure they are separated with line breaks.The maximum number of sensitive words that can be added is 10,000.

3. Click **Save** at the bottom to save the new library information.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/da2d7a6c3ba611f0be2052540099c741.png)

4. After the custom library is configured, when you [create a moderation template](https://www.tencentcloud.com/document/product/267/58265#ea2e4790-1d16-46ba-89c8-c00f2a5c2d28), you can associate the custom library with image recognition or audio recognition in [Recognition policy](https://www.tencentcloud.com/document/product/267/58265#b9864afa-8b0d-4166-bbdb-5f723d7c9868).

## Deleting a Library

1. On the keyword libraries page, find the library you want to delete, and click **Delete** on the right.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/1d62d0da3ba811f09bbe525400454e06.png)

2. A window will pop up asking you to confirm the deletion. Click **Confirm**.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/3de00fd23f5711efa180525400f69702.png)


---
*Source: [https://www.tencentcloud.com/document/product/267/58264](https://www.tencentcloud.com/document/product/267/58264)*
