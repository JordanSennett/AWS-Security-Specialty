# Amazon GuardDuty

Intelligent Threat discover y to protect your AWS Account
Uses Machine Learning algorithms, anomaly detection, 3rd party data
One click to enable (30 days trial), no need to install software

# Input data includes

**CloudTrail Events Logs**

unusual API calls, unauthorized deployments

**CloudTrailManagementEvents** 

createVPCsubnet

createtrail

**CloudTrailS3DataEvents** 

-getobject

-listobjects

-deleteobject

**VPC Flow Logs** 

unusual internal traffic, unusual IP address

**DNS Logs**

compromised EC2 instances sending encoded data within DNS queries • Optional Feature – EKS Audit Logs, RDS & Aurora, EBS, Lambda, S3 Data Events...

Can setup EventBridge rules to be notified in case of findings

EventBridge rules can target AWS Lambda or SNS

Can protect against CryptoCurrency attacks (has a dedicated **RULE** for it)
