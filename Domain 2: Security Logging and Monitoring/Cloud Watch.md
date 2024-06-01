# Cloud Watch Agent

- For virtual servers (EC2 instances, on-premises servers
- Collect additional system-level metrics such as RAM, processes, used disk space, etc.
- Collect logs to send to CloudWatch Logs
  • No logs from inside your EC2 instance will be sent to
- Centralized configuration using SSM Parameter Store
- Make sure IAM permissions are correct
- Default namespace for metrics collected by the Unified CloudWatch agent is **CWAgent** (can also be customized)
-
- ![Cloud Watch Flow Chart](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/5cc08fe2-2d6f-4d97-8818-2b31f141f93a)

**Unified Cloudwatch Agent - procstat (process stat) Plugin**

- Collect metrics and monitors system utilization of individual processes
- Supports both Linux and Windows servers
- Example: amount of time the process user CPU, amount of memory the process use..
- Select which processes to monitor by
  *  pid_file: name of the process identification number (PID) files they create
  * exe: process name that match sting you specify (RegEx)
  * pattern: command lines used to start the processes (RegEx)
- Metrics collected by procstat plugin begins with **procstat** prefix (e.g procstat_cpu_time, procstat_cpu_usage)

**Unified Cloud Watch Agent - Troubleshooting**

- CloudWatch Agent fails to start
  * Might be an isssue with the configuration file
  * Check configuration file logs at /opt/aws/amazon-cloudwatch- agent/logs/configuration-validation.log
- Cant Find Metrics Collected by the CloudWatch Agent
  * Check your using the correct namespace (default: CWAgent)
  * Check the configuration file **amazon-cloudwatch-agent.json**
- CloudWatch Agent Not Pushing Log Events
  * Update to the last CW agent version
  * Test connectivity to the CloudWatch Logs endpoint **logs.<region>.amazonaws.com** (check SG's & NACLs)
  * Review account, region, and log group configurations
  * Check IAM Permissions
  * Verify the system time on the instanve is correctly configured
 - Check CW Agent logs at **/opt/aws/amazon- cloudwatch-agent/logs/amazon-cloudwatch-agent.log**
![CW Policy](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/e2895543-a2a4-4b6c-b807-c22385bafcee)


**CloudWatch Logs**

- Log groups: arbitrary name, usually representing an application
- Log stream: instances within application /log files/ containers
- Can define log expiration policies (never expire, 1 day to 10 years...)
  
- **Cloud Watch Logs can send logs to**
  * Amazon s3 (exports)
  * Kinesis Data Streams
  * Kinesis Data Firehose
  * AWS Lambda
  * Open Search
- Logs are encrypted by default
- Can setup KMS-based encryption with your own keys

- **CloudWatch Logs - Sources**

  * SDK, CW logs Agent, CW unified Agent
  * Elastic Beanstalk: collection of logs from application
  * ECS: collection from containers
  * AWS Lambda: collection from function logs
  * VPC Flow Logs: VPC specific logs
  * API Gateway
  * CloudTrail based on filter
  * Route53: Log DNS queries

**CloudWatch Logs Insights**

![CW Log Insights](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/eb1e3e1d-7229-4f28-ad0e-b71d2315a7f1)

- Search and analyze log data stored in CloudWatch Logs
- Example: find a specific IP inside a log, count occurrences of “ERROR” in your logs...
- Provides a purpose-built query language
  * Automatically discovers fields from AWS services and JSON log
    events
  * Fetch desired event fields, filter based on conditions, calculate aggregate statistics, sort events, limit      number of events...
  * Can save queries and add them to CloudWatch Dashboards
- Can query multiple Log Groups in different AWS accounts
- It’s a query engine, not a real-time engine
  
  ![Sample Queries](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/8157fccc-ab70-4189-b8f0-8ad58e892bbe)

**CloudWatch Logs -S3 Export**

- Log data can take up to 12 hours to become available for export
- The API call is **CreateExportTask**
- Not near-real time or real-time...Use Logs Subscriptions

**CloudWatch Logs Subscriptions**

- Get a real-time log events from CloudWatch Logs for processing and analysis
- Send to Kinesis Data Streams, Kinesis Data Firehose, or Lambda
- Subscription Filter – filter which logs are events delivered to your destination
 ![CW Subscription](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/5f40183f-e77f-41ac-bbb9-01c0ea7f156b)

 **CloudWatch Logs Aggregation Multi-Account & Multi Region**

 ![CW Log aggregation Multi accnt   Multi Region](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/fb55bf6f-8b11-43d3-91c6-479dcabba0c6)


- Cross-Account Subscription – send log events to resources in a different AWS account (KDS, KDF)
  ![Cross account subscrition](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/d75129c0-0991-4b93-9425-c84f0ec070c1)


**CloudWatch Alarms**

- Alarms are used to trigger notifications for any metric
- Various options (sampling, %, max, min, etc...)
- Alarm States:
  * OK
  * INSUFFICIENT_DATA
  * ALARM
 
- Period:
    * Length of time in seconds to ecaluate the metric
    * High resolution custom metrics: 10 sec, 30, sec or multiples of 60 sec

**CloudWatch Alarm Targets**

- Stop, Terminate, Reboot, or Recover an EC2 Instance
- Trigger Auto Scaling Action
- Send notification to SNS (from which you do pretty much anything)
  ![CW Alarm Targets](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/6561120f-c5a6-43cb-b672-312523a90b1a)

**CloudWatch Alarms - Composite Alarms**

- CloudWatch Alarms are on a single metric
- Composite Alarms are monitoring the states of multiple other alarms
- AND and OR conditions
- Helpful to reduce “alarm noise” by creating complex composite alarms
  
![CW Composite Alarms](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/b59228ea-ef43-4d4e-90b3-7052aaee2de9)

**EC2 Instance Recovery**

- Status Check:
  * Instance Status = check the EC2 VM
  * System Status = check the underlying hardware
  * Recover y: Same Private, Public, Elastic IP, metadata, placement group
![EC2 Instance Recovery](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/857020bf-721e-4438-bafd-eed987643035)

**CloudWatch Alarm: Contributor Insights**

- Alarms can be created based on CloudWatch Logs Metrics Filters
- To test alarms and notifications, set the alarm state to Alarm using CLI
- **aws cloudwatch set-alarm-state --alarm-name "myalarm" --state-value
ALARM --state-reason "testing purposes"**

**CloudWatch Contributor Insights**

- Analyze log data and create time series that display contributor data
-  Helps you find top talkers and understand who/what is impacting system performance
-  Example: find bad hosts, identify the heaviest network users, find the URLs that generate the most errors
-  Works for any AWS-generated logs (VPC, DNS, etc..)
-  Built-in rules created by AWS (leverages your CW
Logs) or build your own rules


