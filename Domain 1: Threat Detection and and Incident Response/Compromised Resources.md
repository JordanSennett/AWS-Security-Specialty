# Compromised Resources

**Compromised EC2 Instance**

- Steps to address compromised instances:
  - Capture the instance's metadata
  - Enable Termination Protection
  - Isolate the instance (replace instance's SG- no outbound traffic allowed)
  - Dteach the instance from any ASG (Suspend processes)
  - Deregister the instance from any ELB
  - Snapshot the EBS Volumes (deep analysis)
  - Tag the EC2 instance (create a ticket)

- Offline Investigation: **Shutdown the instance**
- Online Investigation: **snapshot memory or capture**
- Automate the isolation process: **Lamdba, Config**
- Automate memory capture: **SSM run command**

<img width="288" alt="Screenshot 2024-06-17 at 6 07 28 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/60b5caeb-9a4b-4d61-a984-1e2bdf40fbf3">

**Compromised S3 Bucket**

- Identify the compromised S3 bucket using GuardDuty
- Identify the source of the malicious activity and the API calls using **CloudTrail** or **Amazon Detective**
- Identify whether the source was authorized to make those API calls
- Secure your S3 bucket, recommended settings:
    - Block Public access
    - S3 bucket policies and user policies
    - VPC endpoints for S3
    - S3 presigned URL's
    - S3 Access Points
    - S3 ACL's

<img width="226" alt="Screenshot 2024-06-17 at 6 13 12 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/ab579ce3-44f8-4ebb-807c-ab1a4aa8c4c1">

  **Compromised ECS Cluster**

  - Identify the affected ECS CLuster using GuardDuty
  - Identity the source of the malicious activity
  - Isolate the impacted tasks (deny all ingress/egress traffic to the task using security groups)
  - Evaluate the presence of malicious activity 

<img width="252" alt="Screenshot 2024-06-17 at 6 15 52 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/06c30da2-fc3d-46fd-a323-b13afd38ace3">

**Compromised Standalone Container**

- Identify the malicious container using GuardDuty
- Isolate the malicious container (deny all ingress/egress traffic to the container)
- Suspend all process in the container (pause the container)
- Or stop the container and look at EBS Snapshots retained by GuardDuty (snapshots retention feature)
- Evaluate the presence of malicious activity (e.g., malware)

  <img width="259" alt="Screenshot 2024-06-17 at 6 17 36 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/0418db8b-04c3-4bc7-a739-8f06d6896717">

**Compromised RDS Database Instance**

- Identify the affected DB instance and DB user GuardDuty
- If it is NOT legitimate behavior:
  - Restrict network access (SGs & NALCs)
  - Restrict the DB access for the suspected DB user
- Rotate the suspected DB users’ passwords
- Review DB Audit Logs to identify leaked data
- Secure your RDS DB instance, recommended settings:
  - Use Secrets Manager to rotate the DB password
  - Use IAM DB Authentication to manage DB users’ access without passwords

<img width="256" alt="Screenshot 2024-06-17 at 6 20 51 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/c09ae742-81e5-4ab3-bf39-f13f74cf87e0">

**Compromised AWS Credentials**

- Identify the affected IAM user using GuardDuty
- Rotate the exposed AWS Credentials
- Invalidate temporary credentials by attaching an explicit Deny policy to the affected IAM user with an STS date condition (see IAM section)
- Check CloudTrail logs for other unauthorized activity
- Review your AWS resources (e.g., delete unauthorized resources)
- Verify your AWS account information

  <img width="222" alt="Screenshot 2024-06-17 at 6 25 22 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/d1863232-8720-4f3a-9be7-5ef4c12af5dd">

**Compromised IAM Role**

- Invalidate temporary credentials by attaching an explicit Deny policy to the affected IAM user with an STS date condition (see IAM section)
- Revoke access for the identity to the linked AD if any
- Check CloudTrail logs for other unauthorized activity
- Review your AWS resources (e.g., delete unauthorized resources)
- Verify your AWS account information

<img width="225" alt="Screenshot 2024-06-17 at 6 30 00 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/eacd1ee3-77fa-4b4c-b0cb-76e5cbd40661">

**Compromised Account**

- Rotate and delete exposed AWS Access Keys
- Rotate and delete any unauthorized IAM user credentials (rotate existing IAM users’ passwords)
- Rotate and delete all EC2 Key Pairs
- Check CloudTrail logs for other unauthorized activity
- Review your AWS resources (e.g., delete unauthorized resources)
- Verify your AWS account information

<img width="229" alt="Screenshot 2024-06-17 at 6 28 38 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/65f8655e-b4f2-4a30-9181-75b653dfc292">








