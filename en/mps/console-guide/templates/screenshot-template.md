# Screenshot Template

MPS provides preset screenshot templates, which can be added directly to a scheme. Three types of screenshots are supported: time point screenshot, sampled screenshot, and image sprite screenshot. You can also click **Create template** to customize your own screenshot templates.

## Time Point Screenshot

| Item | Description |
| --- | --- |
| Template name | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens, and periods (.) |
| Image format | JPG |
| Image dimensions | The width and height of the image must be in the range of 128-4096 px. |

Preset Templates:

| Template ID | Format | Width | Height | Fill Mode |
| --- | --- | --- | --- | --- |
| 10 | JPG | Same as source | Same as source | Scale to fill |

## Sampled Screenshot

| Item | Description |
| --- | --- |
| Template name | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens (-), and periods |
| Image format | JPG |
| Image dimensions | The width and height of the image must be in the range of 128-4096 px. |
| Sampling interval | The interval can be a percent value (%) or a time value (s). If `%` is selected, the value entered cannot exceed 100. |

Preset Templates:

| Template ID | Format | Width | Height | Interval Measurement | Interval | Fill Mode |
| --- | --- | --- | --- | --- | --- | --- |
| 10 | JPG | Same as source | Same as source | By percent | 10% | Scale to fill |

## Image Sprite Screenshot

| Item | Description |
| --- | --- |
| Template name | Max 64 characters; supports Chinese characters, letters, digits, underscores (_), hyphens, and periods (.) |
| Image format | JPG |
| Image dimensions | The width and height of the image must be in the range of 128-4096 px. |
| Sampling interval | The interval can be a percent value (%) or a time value (s). If `%` is selected, the value entered cannot exceed 100. |
| Rows | A positive integer. The number of subimage rows multiplied by subimage columns must not exceed 100. |
| Columns | A positive integer. The number of subimage rows multiplied by subimage columns must not exceed 100. |

The templates created can be found in the screenshot template list, which displays information including template name, screenshot type, image dimensions, and template type. You can also view the details of, edit, or delete a template on this page.

### Preset templates

| Template ID | Format | Subimage Width | Subimage Height | Subimage Rows | Subimage Columns | Interval Measurement | Interval (s) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 10 | JPG | 142 | 80 | 10 | 10 | By time | 10 |

## Animated Screenshot

| Item | Description |
| --- | --- |
| Template name | Max 64 characters; supports Chinese characters, letters, digits, and underscores (_) |
| Image format | WEBP or GIF |
| Frame rate (fps) | 1-30 |
| Image quality | 0-100. The larger the value, the higher the quality and the larger the image size. |
| Image dimensions (px) | 0 or 128-4096 for either dimension |

The templates created can be found in the template list, which displays information including template name, image type, frame rate, image quality, image dimensions, and template type. You can view, edit, or delete a custom template, but preset templates can be viewed only, not edited or deleted.

### Preset templates

| Template ID | Format | Resolution | Frame Rate (fps) |
| --- | --- | --- | --- |
| 20000 | GIF | Same as source | 2 |
| 20001 | WebP | 320 x Proportionally scaled | 2 |


---
*Source: [https://www.tencentcloud.com/document/product/1041/48786](https://www.tencentcloud.com/document/product/1041/48786)*
