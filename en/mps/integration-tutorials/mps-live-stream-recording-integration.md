# MPS Live Stream Recording integration

With Media Processing Service (MPS), you can record live streaming content by URL.

## Directions

1. On the [Live Recording Templates](https://console.tencentcloud.com/mps/templates/lives) page, create a new live recording template. The console provides a default recording template.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/8728c75b65a511ee94c3525400d793d0.png)

2. On the [Live Schemes](https://console.tencentcloud.com/mps/workflows/liverecord) page, create a new scheme. On this page, you need to select a COS bucket and specify a directory for the output. In actions diagram below, click and add a "Live Recording" step.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/0eec822365a611eeabd75254005810a4.png)

3. Click the edit button on the right side of the Live Recording step to perform detailed configuration.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5ee9eea265a611eeabd75254005810a4.png)

4. In the detailed configuration:

(1) Select the recording template;

(2) Select the output bucket;

(3) Edit the output path. The path of the output file, which can be relative or absolute.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a02238a665a611eeabd75254005810a4.png)

> **Note：**Please note that removing the random field {rand} from the path may cause a file to be overwritten by a different file with identical field values.

5. After completing the above information, click "Create" to establish a live scheme.
6. Go to [Live tasks](https://console.tencentcloud.com/mps/tasks/live) management page and create a new task. Enter the live streaming address that needs to be recorded and select the scheme. Click "Create Task".

> **Note：**Please make sure that the live streaming address is filled correctly. If the live streaming fails to be pulled, it will be retried 3 times. If the live streaming still cannot be obtained, the recording task will fail.


---
*Source: [https://www.tencentcloud.com/document/product/1041/57048](https://www.tencentcloud.com/document/product/1041/57048)*
