# AWS Macie

- Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in AWS.
- Macie helps identify and alert you to sensitive data, such as personally identifiable information (PII)

  ![AWS Macie Flow](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/d1142ea8-d1a3-4f25-abbc-d9b55f8c7f04)

**AWS Macie – Data Identifiers**

- Used to analyze and identify sensitive data in your S3 buckets
- Managed Data Identifier
    * A set of built-in criteria that are designed to detect specific type of sensitive data
    * Examples: credit card card numbers, AWS Credentials, bank accounts
 - Custom Data Identifier:
    * A set of criteria that you define to detect sensitive data
    * Regular expression, keywords, proximity rule
    * Examples: employee IDs, customer account numbers
  - You can use **Allow List** to define a text pattern to ignore (e.g public phone numbers)

![Macie data identifiers](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/664e93fb-8853-4bb1-b8a0-23a28a0ac8db)

**AWS Macie – Findings Types**

- Policy Findings
    * A detailed report of policy violation or issue with the security of S3 bucket
    * Examples: default encryption is disabled, bucket is public, ...
    * **Policy:IAMUser/S3BucketEncryptionDisabled,Policy:IAMUser/S3BucketPublic**
    * Detect changes only after you enable Macie

 - Sensitive Data Findings
     * A detailed report of sensitive data that’s found in S3 buckets
     * Examples: Credentials (private keys), Financial (credit card numbers), ...
     * **SensitiveData:S3Object/Credentials, SensitiveData:S3Object/Financial**
     * For Custom Data Identifier **SensitiveData:S3Object/CustomIdentifier**

**AWS Macie – Multi-Account Strategy**

- You can manage mulltiple accounts in Macie
- Associate the Member accounts with Administrator account
    * Through an AWS Organization
    * Sending invitation through Macie
    * Supports Delegated Administrator in an AWS Organization

- Administrator account can:
    * Add and remove member accounts
    * Have access to all s3 sensitive data and settings for all accounts
    * Manage Automated Sensitive Data Discovery and run Data Discovery jobs
    * Manage Data Identifiers and Findings

**AWS Macie – Multi-Account Strategy**

![Macie Multi account strategy](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/2c9dec75-6798-48cd-98da-4925c000c0d0)



