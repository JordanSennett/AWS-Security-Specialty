**VPC Flow Logs**

- Capture information about IP traffic going into your interfaces:
    * VPC Flow Logs
    * Subnet Flow Logs
    * Elastic Network Interfance (ENI) Flow Logs
- Helps to monitor & troubleshoot connectivity issues
- Flow logs data can go to S3, CloudWatch Logs, and Kinesis Data Firehose
- Captures network information from AWS managed interfaces too: ELB, RDS, ElastiCache, Redshift, WorkSpaces

**VPC Flow Logs**

![VPC Flow Chart](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/e3375a53-1206-42ea-9b19-924d5393276b)

**VPC Flow Logs Syntax**

- srcaddr & dstaddr – help identify problematic IP
- srcport & dstport – help identity problematic ports
- Action – success or failure of the request due to Security Group / NACL
- Can be used for analytics on usage patterns, or malicious behavior
- Query VPC flow logs using Athena on S3 or CloudWatch Logs Insights
- Flow Logs examples: https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-records-examples.html

![web traffic log](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/15c33bd1-6655-4c57-b024-c65d933506d3)

**VPC Flow Logs – Troubleshoot SG & NACL issues**

                                                **Look at the “ACTION” field**
- Incoming Request                                                               
    * Inbound REJECT => NACL or SG                                                    
    * Inbound ACCEPT, Outbound REJECT => NACL                                        

![Inbound Rule](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/79102b86-489e-4e8b-a46c-0936622feb87)

- Outgoing Request
    * Outbound REJECT => NACL or SG
    * OutboundACCEPT,InboundREJECT=> NACL

![Outbound Rule](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/3c968322-abd4-4d80-9298-d16e488a38b0)

**VPC FLow Logs - Architectures**

![VPC FLow Architectures](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/6b50d21d-3577-4803-a413-43b8ff3ecc77)


**VPC Flow Logs – Traffic not captured**

- Traffic to Amazon DNS server (custom DNS server traffic is logged)
- Traffic for Amazon Windows license activation
- Traffic to and from 169.254.169.254 for EC2 instance metadata
- Traffic to and from 169.254.169.123 for Amazon Time Sync ser vice
- DHCP traffic
- Mirrored traffic
- Traffic to the VPC router reser ved IP address (e.g., 10.0.0.1)
- Traffic between VPC Endpoint ENI and Network Load Balancer ENI

**VPC - Traffic Mirroring**

- Allows you to capture and inspect network traffic in your VPC
- Route the traffic to security appliances that you manage
- Capture the traffic
  * From (Source) – ENIs
  * To (Targets) – an ENI or a Network Load Balancer
- Capture all packets or capture the packets of your interest (optionally, truncate packets)
- Source and Target can be in the same VPC or different VPCs (VPC Peering)
- Use cases: content inspection, threat monitoring, troubleshooting, ...

![VPC Traffic Mirroring](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/262fcf47-bc52-49f4-b052-5bacc30a8255)

**VPC Traffic Mirroring – Architecture**

- Traffic is distributed across EC2 instances in ASG (same security appliance)

  ![Traffic flow to same security applicance](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/6c41b4c6-6fc6-404c-b11a-d187ee8d4c71)

- All Traffic is sent to multiple EC2 instances with different security appliances

  ![traffic to different secuity appliances](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/4a03a1cf-dc99-4b94-adb3-161b7e4c4f6a)


**VPC Network Access Analyzer**

- Helps you understand potential network paths to/from your resources
- Define Network Access Requirements
  * Example: identify publicly available resources
- Evaluate against them and find issues / demonstrate compliance
  * Evaluate network access to resources in your VPCs (EC2, RDS, Aurora, OpenSearch, Redshift...)
  * Match against the configurations of your VPC resources (SG, NACL, NATGW, IGW...)
- Network Access Scope – json document contains conditions to define your network security policy (e.g., detect public databases)
