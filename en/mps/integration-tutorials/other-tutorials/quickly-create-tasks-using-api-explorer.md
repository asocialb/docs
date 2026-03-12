# Quickly create tasks using API Explorer 

## Step 1: Log in to the Cloud API Console

Access the [Cloud API](https://console.tencentcloud.com/api/explorer?Product=cvm&Version=2017-03-12&Action=DescribeRegions) Console and log in with your account credentials. If you encounter account authorization issues, refer to the [Account Authorization](https://www.tencentcloud.com/document/product/1041/69220) to complete permission configuration.

## Step 2: Select the API Interface

- **Quickly Create a VOD Processing Task**

To quickly create a VOD processing task, navigate to the [API Explorer](https://console.tencentcloud.com/api/explorer?Product=mps&Version=2019-06-12&Action=ProcessMedia) page. Select the "Media Processing Service (MPS)" product; click "**Processing Task Initiation APIs > ProcessMedia > JSON**"; then locate the corresponding input parameter fields under the JSON.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/5a8c0e348c8911f0814e525400bf7822.png)

- **Quickly Create a Live Processing Task**

To quickly create a Live processing task, navigate to the [API Explorer](https://console.tencentcloud.com/api/explorer?Product=mps&Version=2019-06-12&Action=ProcessMedia) page. Select the "Media Processing Service (MPS)" product; click "**Processing Task Initiation APIs > ProcessLiveStream > JSON**"; then locate the corresponding input parameter fields under the JSON.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/927e01878c8911f0ae9d5254001c06ec.png)

## Step 3: Fill in JSON Code and Initiate the Invocation

In the input parameter fields, enter the JSON code for initiating the task—either by direct input or pasting. Before initiating the call, you may customize the parameters as needed within these fields. Once adjustments are complete, click **Initiate Invocation** to directly launch the task.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/a4ce8e358c8911f088af5254005ef0f7.png)

## Step 4: Query Task Results

After initiating the invocation a **TaskId** will be automatically generated.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/ba410dba8c8911f0b321525400e889b2.png)

- You can check the execution status and output results of corresponding tasks in the Media Processing Service (MPS) console, under the Task Management section ([VOD Processing Tasks](https://console.tencentcloud.com/mps/tasks/vod-list) or [Live Processing Tasks](https://console.tencentcloud.com/mps/tasks/live-list)).
- Alternatively, directly call the **Task Management APIs** and enter the **TaskId** to query the task execution status and output results.

![](https://staticintl.cloudcachetci.com/cms/backend-cms/13798c258c8a11f0814e525400bf7822.png)


---
*Source: [https://www.tencentcloud.com/document/product/1041/73127](https://www.tencentcloud.com/document/product/1041/73127)*
