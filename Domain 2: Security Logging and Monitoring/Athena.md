# Amazon Athena

- Serverless query service to analyze data stored in Amazon S3
- Uses standard SQL language to query the files (built on Presto)
- SupportsCSV,JSON,ORC,Avro,andParquet
- Pricing: $5.00 per TB of data scanned
- Commonly used with Amazon Quicksight for repor ting/dashboards
- Use cases: Business intelligence / analytics / reporting, analyze & queryVPC Flow Logs,ELB Logs,CloudTrail trails,etc...
- Exam Tip: analyze data in S3 using serverless SQL, use Athena

   ![Amazon Athena](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/29ee316e-358b-4369-914d-d3d13d021e95)

**Amazon Athena – Performance Improvement**

- Use columnar data for cost-savings (less scan)
  * Apache Parquet or ORC is recommended
  * Huge performance improvement
  * Use Glue to convert your data to Parquet or ORC
- Compress data for smaller retrievals (bzip2, gzip, lz4, snappy, zlip, zstd...)
- Partition datasets in S3 for easy querying on virtual columns
  * s3://yourBucket/pathToTable
                          /<PARTITION_COLUMN_NAME>=<VALUE>
                            /<PARTITION_COLUMN_NAME>=<VALUE>
                              /<PARTITION_COLUMN_NAME>=<VALUE>
                                /etc...
  * Example:s3://athena-examples/flight/parquet/year=1991/month=1/day=1/
  * Use larger files (> 128 MB) to minimize overhead
 
**Amazon Athena – Federated Query**

- Allows you to run SQL queries across Amazon Athena Lambda (Data Source Connector) data stored in relational, non-relational, object, and custom data sources (AWS or on-premises)
- Uses data source connectors that run on AWS Lambda to run federated Queries (CW Logs, Dynamo DB, RDS)
- Store the results back in Amazon S3
  ![Athena Map](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/0f58cb00-150c-4d6a-ab80-0de7cd0d2701)

**Amazon Athena – Troubleshooting**

- Insufficient Permissions When using Athena with QuickSight
  * Validate QuickSight can access S3 buckets used by Athena
  * If the data in the S3 buckets is encrypted using AWS KMS key (SSE-KMS), then QuickSight IAM role must be granted access to decrypt with the key (kms:Decrypt)
    * arn:aws:iam::<account_id>:role/service-role/aws-quicksight-s3-consumers-role-v0 (Default)
    * arn:aws:iam::<account_id>:role/service-role/aws-quicksight-service-role-v0
  ![Athena Trouble shooting](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/7ac34f13-091a-4913-af3f-144345d9f589)
