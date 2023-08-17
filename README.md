# FLaNK-HuggingFace-BLOOM-LLM

https://huggingface.co/bigscience/bloom into NiFi


#### Flink SQL Kafka Topics

````

CREATE TABLE `ssb`.`Meetups`.`hfbloom` (
  `generated_text` VARCHAR(2147483647),
  `ts` VARCHAR(2147483647),
  `uuid` VARCHAR(2147483647),
  `eventTimeStamp` TIMESTAMP(3) WITH LOCAL TIME ZONE METADATA FROM 'timestamp',
  WATERMARK FOR `eventTimeStamp` AS `eventTimeStamp` - INTERVAL '3' SECOND
) WITH (
  'properties.auto.offset.reset' = 'earliest',
  'format' = 'json',
  'scan.startup.mode' = 'group-offsets',
  'properties.bootstrap.servers' = 'kafka:9092',
  'connector' = 'kafka',
  'properties.request.timeout.ms' = '120000',
  'properties.transaction.timeout.ms' = '900000',
  'topic' = 'hfbloom',
  'properties.group.id' = 'llmBloomProps'
)


````

#### Link to Model

````

BigScience Large Open-science Open-access Multilingual Language Model
Version 1.3 / 6 July 2022

BLOOM is an autoregressive Large Language Model (LLM), trained to continue text from a prompt on vast amounts of text data using industrial-scale computational resources. As such, it is able to output coherent text in 46 languages and 13 programming languages that is hardly distinguishable from text written by humans. BLOOM can also be instructed to perform text tasks it hasn't been explicitly trained for, by casting them as text generation tasks.

````
