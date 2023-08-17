# FLaNK-HuggingFace-BLOOM-LLM

https://huggingface.co/bigscience/bloom into NiFi


#### Flink SQL Kafka Topics

````

CREATE TABLE `ssb`.`Meetups`.`hfbloom` (
  `generated_text` VARCHAR(2147483647),
  `ts` VARCHAR(2147483647),
  `x_compute_type` VARCHAR(2147483647),
  `inputs` VARCHAR(2147483647),
  `x_compute_time` VARCHAR(2147483647),
  `x_inference_time` VARCHAR(2147483647),
  `uuid` VARCHAR(2147483647),
  `x_time_per_token` VARCHAR(2147483647),
  `x_compute_characters` VARCHAR(2147483647),
  `eventTimeStamp` TIMESTAMP(3) WITH LOCAL TIME ZONE METADATA FROM 'timestamp',
  WATERMARK FOR `eventTimeStamp` AS `eventTimeStamp` - INTERVAL '3' SECOND
) WITH (
  'scan.startup.mode' = 'group-offsets',
  'properties.request.timeout.ms' = '120000',
  'properties.auto.offset.reset' = 'earliest',
  'format' = 'json',
  'properties.bootstrap.servers' = 'kafka:9092',
  'connector' = 'kafka',
  'properties.transaction.timeout.ms' = '900000',
  'topic' = 'hfbloom',
  'properties.group.id' = 'llmBloomProps'
)


````


#### Slack Output

````
==== NiFi to Hugging Face BLOOM LLM
AzureML Model Deployment: bloom-deployment
On Date: Thu, 17 Aug 2023 02:05:56 GMT
File Name: 7b8afb65-d5eb-49ee-9a89-d2b870310243
Request Duration: 1339
Request URL: https://api-inference.huggingface.co/models/bigscience/bloom
Compute Characters: 63
Compute Time: 1014
Compute Type: gpu+optimized
Inference Time: 968
Queue Time: 45
Request ID: iPX8lqeK9XwqSZA9e-wCH
SHA:  053d9cd9fbe814e091294f67fcfedb3397b954bb
Time Per Token: 48
Total Time: 1014
Validation Time: 0
R: Apache NiFi is a great tool for loading data into Apache Kafka. It is a very simple and easy to use tool. It is a very simple and easy to use
=====
````


#### Link to Model

````

BigScience Large Open-science Open-access Multilingual Language Model
Version 1.3 / 6 July 2022

BLOOM is an autoregressive Large Language Model (LLM), trained to continue text from a prompt on vast amounts of text data using industrial-scale computational resources. As such, it is able to output coherent text in 46 languages and 13 programming languages that is hardly distinguishable from text written by humans. BLOOM can also be instructed to perform text tasks it hasn't been explicitly trained for, by casting them as text generation tasks.

````
