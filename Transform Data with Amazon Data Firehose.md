Lab Concept

Amazon Data Firehose is a fully managed service that collects streaming data, optionally transforms it, and delivers it to a destination such as Amazon S3.

In this lab, Firehose receives demo data through Direct PUT, uses AWS Glue to help convert the record format to Apache Parquet, and delivers the transformed data to Amazon S3.

<img width="404" height="110" alt="image" src="https://github.com/user-attachments/assets/bf2fb432-0782-43ed-b52a-bd0b4b9e1ea0" />

<img width="407" height="124" alt="image" src="https://github.com/user-attachments/assets/1ce68acd-d6f8-4d02-8ae6-2753e08361fd" />

AWS Glue provides the metadata/schema that Firehose uses during record format conversion.
Parquet is a columnar data format. Instead of storing data primarily row-by-row, it organizes data by columns.

<img width="125" height="370" alt="image" src="https://github.com/user-attachments/assets/84d1db47-2e4a-4f05-80ee-ef0e08c1f837" />



test
