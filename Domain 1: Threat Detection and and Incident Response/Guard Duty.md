# Amazon GuardDuty

- Intelligent Threat discover y to protect your AWS Account
- Uses Machine Learning algorithms, anomaly detection, 3rd party data
- One click to enable (30 days trial), no need to install software

**Input data includes**

- CloudTrail Events Logs: unusual API calls, unauthorized deployments
    - CloudTrail Management Events: Create VPC subnet,Create trail..
    - CloudTrail S3 Data Events: **get object, list objects, delete object**
- VPC Flow Logs: unusual internal traffic, unusual IP address
- DNS FLow Logs: compromised EC2 instances sending encoded data within DNS queries
- Optional Feature: EKS Audit Logs, RDS & Aurora, EBS, Lambda, S3 Data Events.
- Can Setup **EventBridge** rules to be notified in case of findings
- EventBridge rules can target AWS Lambda or SNS
- Can protect against CryptoCurrency attacks (has a dedicated finding for it)
<img width="657" alt="Guard Duty" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/5682f358-ff05-42a3-9c93-40b15f6bba87">

**Amazon GuardDuty – Multi-Account Strategy**

- You can manage multiple accounts in GuardDuty
- Associate the member accounts with the Admin account
  - Through an AWS Organization
  - Sending invitation through GuardDuty
- Administrator account can:
  - Add and remove member accounts
  - Manage GuardDuty within the associated member accounts
  - Manage Findings, suppression rules, trusted IP list, threat list
- In an AWS Organization, you can specify a member account as the Organizations delegated administrator for GuardDuty
  
