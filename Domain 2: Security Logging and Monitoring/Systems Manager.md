# AWS Systems Manager



## AWS Systems State Manager (SSM - State Manager)

- Automate the process of keeping you managed instances in a state you define
- Use Cases: bootstap instances with software, patch OS & software updates on a schedule

* State Manager Association:
  
- Defines the state ou want to maintain to your managed instances
- Example: port 22 must be closed, antivrus must be installed
- Specify a schedule when this configuration is applied

* Uses SSM Documents to create an Association (e.g SSM Document to configure CW Agent)
