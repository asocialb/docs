# Intelligent Review Template

1. MPS provides preset moderation templates, which can be added directly to a scheme. You can also click **Create template** to customize your own moderation templates.
  - Template name: Up to 64 characters; supports Chinese characters, letters, digits, spaces, underscores (_), hyphens (-), and periods (.).
  - Moderation items: Image recognition, speech recognition, and text recognition. The subitems of the selected moderation items will appear in the column on the right.

| Moderation Item | Subitem | Description |
| --- | --- | --- |
| Image recognition | Pornographic content | Porn, vulgarity, intimacy, and sexiness |
|  | Terrorist content | Bloody scenes, explosions, and fires |
|  | Politically sensitive content | Banned icons, and celebrities in sports and the entertainment industry |
| Speech recognition | Pornographic content | Porn, vulgarity, intimacy, and sexiness |
|  | Politically sensitive content | Banned icons, and celebrities in sports and the entertainment industry |
| Text recognition | Pornographic content | Porn, vulgarity, intimacy, and sexiness |
|  | Politically sensitive content | Banned icons, and celebrities in sports and the entertainment industry |

2. For each subitem, you can set a **Confirm Threshold** and a **Suspicion Threshold**, which determine the strictness of moderation. If they are left empty, the default values will be used.
  - **Confirm threshold**: MPS analyzes the videos uploaded and gives them confirmation scores. If the score of a video exceeds the confirm threshold, the video will be marked confirmed. The value range of the threshold is 0-100. The default value is recommended.
  - **Suspicion threshold**: MPS analyzes the videos uploaded and gives them suspicion scores. If the score of a video exceeds the suspicion threshold, the video will be marked suspicious. You can initiate human moderation for suspicious videos on the video moderation page. The value range of the threshold is 0-100. The default value is recommended.

> **Note:**You can view the  **system preset**  auditing templates in [MPS console > Intelligent Auditing Templates](https://console.intl.cloud.tencent.com/mps/templates/audits).

3. The templates created are displayed in the moderation template list, where you can view the details of, edit, or delete a template.


---
*Source: [https://www.tencentcloud.com/document/product/1041/48788](https://www.tencentcloud.com/document/product/1041/48788)*
