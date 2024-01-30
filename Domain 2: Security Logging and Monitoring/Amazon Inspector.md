# Amazon Inspector

**Allows you to run automated Security Assessments**

**EC2 Instances**

Leveraging the AWS System Manager (SSM) agent 

Analyze against unintended network accessibilty

Analyze the running OS against known vulnerabilities 

**For Container Images push to Amazon ECR**

Assessment of Container Imagers as they are pushed

**For Lambda Functions**

Identifies software vulnerabilities in function code and package dependencies

Assessment of functions they deployed

**Reporting & integration with AWS Security Hub**

**Send findings to Amazon EventBridge**

## What does Amazon Inspector evaluate

Remember : only for EC2 instances, Container Images & Lambda functions

Continuous scanning of the infrastructure, only when needed

Package vulnerabilities (EC2, ECR & Lambda) – database of CVE

Network reachability (EC2)

A risk score is associated with all vulnerabilities for prioritization
