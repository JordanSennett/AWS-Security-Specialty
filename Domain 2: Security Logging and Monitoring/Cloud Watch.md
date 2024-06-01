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

## Unified Cloudwatch Agent - procstat (process stat) Plugin

- Collect metrics and monitors system utilization of individual processes
- Supports both Linux and Windows servers
- Example: amount of time the process user CPU, amount of memory the process use..
- Select which processes to monitor by:
  • pid_file: name of the process identification number (PID) files they create
  • exe: process name that match sting you specify (RegEx)
  • pattern: command lines used to start the processes (RegEx)
- Metrics collected by procstat plugin begins with **procstat** prefix (e.g procstat_cpu_time, procstat_cpu_usage)

## Unified Cloud Watch Agent - Troubleshooting

- CloudWatch Agent fails to start
  • Might be an isssue with the configuration file
  • Check configuration file logs at /opt/aws/amazon-cloudwatch- agent/logs/configuration-validation.log

- Cant Find Metrics Collected by the CloudWatch Agent
  • Check your using the correct namespace (default: CWAgent)
  • Check the configuration file **amazon-cloudwatch-agent.json**
