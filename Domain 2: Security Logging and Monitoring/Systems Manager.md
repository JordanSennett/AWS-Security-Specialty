# AWS Systems Manager


## AWS Systems State Manager (SSM - State Manager)

- Automate the process of keeping you managed instances in a state you define
- Use Cases: bootstap instances with software, patch OS & software updates on a schedule

**State Manager Association**:
  
- Defines the state you want to maintain to your managed instances
- Example: port 22 must be closed, antivrus must be installed
- Specify a schedule when this configuration is applied

**Uses SSM Documents to create an Association (e.g SSM Document to configure CW Agent)**

**SSM-Patch Manager**

- Automates the process of patching managed instances
- OS updates, applications updates, security updates
- Supports both EC2 instances and on-premises servers
- supports Linux, macOS, and Windows
- Patch on demand or on a schedule using Maintenance Windows
- Scan instances and generate patch compliance report (missing patches)
- Patch compliance report can be sent to a S3 bucket

**Patch Baseline**

- Defines which patches should and shouldnt be installed on your instances
- ability to create custom Patch Baselines (specify approved/rejected patches)
- Patches can be auto approved within days of their release
- By default, install only critical patches and patches related to security

**Patch Group**

- Associate a set of instances with a specific Patch Baseline
- Eg: create a Patch Groups for different enviroments (dev,test and prod)
- Instances should be defined with the tag key **Patch Group**
- An instance can only be in one Patch Group
- Patch Group can be registered with only one Patch Baseline

**SSM Patch Manager Patch Baselines**

**Pre-Defined Patch Baseline**

- Managed by AWS for different Operating Systems (Can't be modified)
- AWS-RunPatchBaseline (SSM Document)- apply both operating system and application patches (Linux, macOS, Windows Server)

**Custom Patch Baseline**

- Creat your own Patch Baseline and choose which patches to auto-approve
- Operating system, allowed patches, rejected patches
- Ability to specify custom and alternatice patch repositories

![SSM - Patch Manager](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/882e262f-8866-453c-843f-6b25e0aabba6)

**SSM- Maintenace Windows**

-Defines a schedule for when to perform actions on you instances
- Example: OS patching, updating drivers, installing software...
- Maintenance Window contains
    * Schedule
    * Duration
    * Set of Registered Instances
    * Set of registerd task

**SSM- Session Manager**

-Iam Permissions
  * Control which users/groups can access Session Manager and which instances
  * Use tags to restrict access to only specific EC2 instances
  * Access SSM + write to S3 + write to CloudWatch

![SSM - Session Manager](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/98c9fb7d-6e4a-4b37-ba35-f227cc171f63)


- Optionally, you can restrict commands a user can run in a session
-  Allows you to start a secure shell on you EC2 instance and on-premise servers
-  Access through AWS Console, AWS CLI. or Session Manager SDK
-  Does not need SSH access, bastion hosts, or SSH Keys
-  Supports Linus, macOS, and Windows
-  Log connections to you instances and executed commands
-  Session log data can be sent to S3 or CloudWatch Logs
-  CloudTrail can intercept **Start Sessions**

  ![SSM - Session Manger flow](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/94ee8e93-d8db-41a3-b606-1ed422932950)


# SSH vs SSM Session Manager
![SSH vs SSM Session Manager](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/76a3ff0b-9117-41fd-a80e-99559bc0820e)
