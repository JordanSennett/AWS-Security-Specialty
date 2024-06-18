# IAM Tools

**IAM Security Tools**

- IAM Credentials Report (account-level):
  - a report that lists all your account's users and the status of their various
credentials
- IAM Access Advisor (user-level):
  - Access advisor shows the service permissions granted to a user and when those
services were last accessed.
  - You can use this information to revise your policies.

**IAM Access Analyzer**

- Find out which resources are shared externally:
    - S3 Buckets
    - IAM Roles
    - KMS Keys
    - Lambda Function and Layers
    - SQS queues
    - Secrets Manager Secrets
  - Define Zone of Trust= AWS Account or AWS Organization
  - Access outside zone of trust
 
<img width="252" alt="Screenshot 2024-06-17 at 7 24 50 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/82f64030-68a5-43be-bcdc-4bfd5300d86b">

- IAM Access Analyzer Policy Validation
  - Validates your policy against IAM policy grammar and best practices
  - General warnings, security warnings, errors, suggestions
  - Provides actionable recommendations

- IAM Access Analyzer Policy Generation
  - Generates IAM policy based on access activity
  - CloudTrail logs is reviewed to generate the policy with the fine-grained permissions and the appropriate Actions and Services
  - Reviews CloudTrail logs for up to 90 days

    <img width="192" alt="Screenshot 2024-06-17 at 7 27 24 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/cfa6f81b-0b64-4d98-b10e-f70e80ee2f8c">
