# AWS Security Hub

- Central security tool to manage security across several AWS accounts and automate security checks
- Integrated dashboards showing current security and compliance status to quickly take actions
- Automatically aggregates alerts in predefined or personal findings formats from various AWS services & AWS partner tools:
    - Config
    - GuardDuty
    - Inspector
    - Macie
    - IAM Access Analyzer
    - AWS Systems Manager
    - AWS Health
    - AWS Partner Network Solutions
- Must first enable the AWS Config Service

<img width="586" alt="Screenshot 2024-06-17 at 3 07 52 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/4f2b5af7-8ebf-4cb0-9289-f0ac979be52d">

**Security Hub – Main Features**

- Cross-Region Aggregation – aggregate findings, insights, and security scores from multiple Regions to a single aggregation Region
- AWS Organizations Integration:
    - Manage all accounts in the Organization
    - Security Hub automatically detects new accounts
    - By default, Organizaation management account is the Security Hub Administrator
    - Ability to have a designated Security Hub Admin from member account

  **Security Hub – Security Standards**

  - Security Hub generates findings and continuous checks against the rules in a set of supported security standards
  - Security Hub supports the following standards: CIS AWS Foundations, PCI DSS, AWS Foundational Security Best Practices...
  - Ability to enable/disable a security standard
  <img width="406" alt="Screenshot 2024-06-17 at 3 12 57 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/7b823911-5819-44e1-8967-3057e659ba23">

**Security Hub – Integration with GuardDuty**

- Automatically enabled when Security Hub is enabled (can be disabled)
- GuardDuty will send findings to Security Hub
- Findings are sent in AWS Security Finding Format (ASFF)
- Findings are usually sent within 5 mins...
- Archiving a GuardDuty finding will not update the finding in Security Hub

**Security Hub – Services Integration**

<img width="628" alt="Screenshot 2024-06-17 at 3 39 04 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/20eb970c-5c11-4682-9e7f-852b39b0f114">

**Security Hub – Custom Actions**

- Helps you automate Security Hub with EventBridge
- Allows you to create actions for response and remediation to selected findings within the security Hub Console
- EventBridge event type is Security Hub Findings- Custom Action
  <img width="619" alt="Screenshot 2024-06-17 at 3 42 24 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/e523f971-4711-49e4-b125-20bce0d5072e">

