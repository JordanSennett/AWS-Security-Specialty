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
  
<img width="623" alt="GD Multi accnt strategy" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/7dd1f469-cc39-43cf-a2f7-bd78dff66a03">

**Amazon GuardDuty – Findings Automated Response**

-  Findings are potential security issue for malicious events happening in your AWS account
-  Automate response to security issues revealed by GuardDuty Findings using EventBridge
-  Send alerts to SNS (email, Lambda, Slack, Chime, ...)
-  Events are published to both the administrator account and the member account that it is originated from

<img width="233" alt="Screenshot 2024-06-17 at 12 35 12 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/8f81605d-54ce-440e-b945-be12d53dd151">

**Amazon GuardDuty – Findings**

- GuardDuty pulls independent streams of data directly from CloudTrail logs (management events, data events),VPC Flow Logs or EKS logs
- Each finding has a severity value between 0.1 to 8+ (High, Medium, Low)
- Finding naming convention: **ThreatPurpose:ResourceTypeAffected/ThreatFamilyName.DetectionMechanism!Artifact**
    - ThreatPurpose – primary purpose of the threat (e.g., Backdoor, CryptoCurrency)
    - ResourceTypeAffected – which AWS resource is the target (e.g., EC2, S3)
    - ThreatFamilyName – describes the potential malicious activity (e.g., NetworkPortUnusual)
    - DetectionMechanism – method GuardDuty detecting the finding (e.g.,Tcp, Udp)
    - Ar tifact – describes a resource that is used in the malicious activity (e.g., DNS)
- You can generate sample findings in GuardDuty to test your automations

**Amazon GuardDuty – Findings Types**

- EC2 Finding Type
  - UnauthorizedAccess:EC2/SSHBruteForce,CryptoCurrency:EC2/BitcoinTool.B!DNS
- Iam Finding Type
  - Stealth:IAMUser/CloudTrailLoggingDisabled,Policy:IAMUser/RootCredentialUsage
- Kubernetes Audit Logs Finding Types
  - CredentialAccess:Kubernetes/MaliciousIPCaller
- Malware Protection Finding Types
  - Execution:EC2/SuspiciousFile,Execution:ECS/SuspiciousFile
- RDS Protection FindingTypes
  - CredentialAccess:RDS/AnomalousBehavior.SuccessfulLogin
- S3 FindingTypes
  - Policy:S3/AccountBlockPublicAccessDisabled,PenTest:S3/KaliLinux

**Amazon GuardDuty – Architectures**

<img width="613" alt="Screenshot 2024-06-17 at 1 08 00 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/4ed5743e-4e0f-419b-bfec-27bfa205a8c9">


<img width="631" alt="Screenshot 2024-06-17 at 1 08 25 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/a245babe-cd78-4db8-8334-f9d1158038ea">

  
**Amazon GuardDuty –Trusted andThreat IP Lists**

- Works only for public IP addresses
- Trusted IP List
  - List of IP addresses and CIDR ranges that you trust
  - GuardDuty doesn’t generate findings for these trusted lists
- Threat IP List
  - List of known malicious IP addresses and CIDR ranges
  - GuardDuty generates findings based on these threat lists
  - Can be supplied by 3rd party threat intelligence or created custom for you
- In a multi-account GuardDuty setup, only the GuardDuty administrator account can manage those lists
 for you

**Amazon GuardDuty – Suppression Rules**

- Set of criteria that automatically filter and archive new findings
- Example: low-value findings, false-positive findings, or threats you don’t intend to act on
- Can suppress entire findings types or define more granular criteria (e.g., suppress only specific EC2 instances)
- Suppressed findings are NOT sent to Security Hub, S3, Detective, or EventBridge
- Suppressed findings can be still viewed in the Archive

**Troubleshooting - GuardDuty didn’t generate any finding types**

- Problem: GuardDuty is activated but it didn’t generate any DNS based findings
- Reason: GuardDuty only processes DNS logs if you use the default VPC DNS resolver.All other types of DNS resolvers won't generated DNS based findings.
- If GuardDuty is suspended or disabled, then no finding types are generated
- Best practice to enabled GuardDuty even if Regions you don’t use

