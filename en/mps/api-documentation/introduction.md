# Introduction

## Overview

Media Processing Service (MPS) provides intelligent and powerful multimedia data processing capabilities, supporting the industry's most comprehensive range of audio/video encoding standards. Powered by a self-developed encoding kernel and large vision models, MPS provides features such as audio/video transcoding, enhancement, media AI, and quality inspection and evaluation. It helps improve media quality, reduce costs, and meet diverse audio/video processing needs. All MPS APIs introduced in this chapter comply with the OpenAPI 3.0 specification.
You can call APIs to perform operations related to media processing, such as initiating a media processing task, creating a template, or querying task details.
For information on all APIs supported by MPS, see [API Category](https://intl.cloud.tencent.com/document/product/1041/33625).

## Glossary

For common terms of the MPS APIs, see the table below.

| Term | Description |
| --- | --- |
| Initiating a processing task | It indicates initiating a media processing task for offline files or live streams. |
| Event notification | You can configure an event notification address when initiating a processing task to enable MPS to synchronize the task progress, status, and output information in real time during processing. |
| Template | Templates are used to configure specific parameters of features for future use, such as audio/video transcoding, audio/video enhancement, watermark, screenshot, media AI, and media quality inspection. When you initiate a processing task, you can associate the task with a template ID. |
| Service orchestration | Orchestration is used to combine different features to form an automatic processing workflow. In addition, it supports enabling automatic triggering. When a new media file is uploaded to the specified COS trigger directory, it will be automatically processed based on the orchestration configurations. |

## Getting Started with APIs

You can use the API Explorer tool to call APIs online.
This document takes processing task initiation as an example to introduce the steps for calling an API through the API Explorer tool.

Go to the
API Explorer
tool page. For more information about API Explorer tool usage, see
Using API Explorer
.
Create a smart subtitle template via the console (recommended) or by calling the API
CreateSmartSubtitleTemplate
, and obtain the template ID.
Call the API
Process Media
, and specify the input file path, smart subtitle template ID, output path, and other required information. Then, initiate a smart subtitle processing task, and obtain the task ID.
Query the task result via the console or by calling the API
DescribeTaskDetail
.


---
*Source: [https://www.tencentcloud.com/document/product/1041/48920](https://www.tencentcloud.com/document/product/1041/48920)*
