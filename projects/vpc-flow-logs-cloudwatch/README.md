🛰️ AWS VPC Flow Logs & CloudWatch Project

This project demonstrates my ability to configure, analyze, and monitor network traffic in AWS using VPC Flow Logs, CloudWatch Logs, and CloudWatch Alarms — while applying real-world troubleshooting and security practices.

Throughout this project, I worked through challenges involving SSH permissions, file ownership, and key-pair access control on Windows.
By problem-solving through each issue, I deepened my understanding of how IAM permissions, EC2 networking, and CloudWatch metrics interact in AWS.

🧩 Project Objectives

Launch and secure an EC2 instance within a custom VPC.

Configure VPC Flow Logs to capture network traffic data.

Create CloudWatch alarms to detect rejected network connections.

Integrate SNS notifications for alerting when thresholds are exceeded.

Validate connectivity and observe traffic patterns through ACCEPT/REJECT flow log entries.

📸 Project Screenshots
1. EC2 Instance Setup

Launched an Amazon Linux EC2 instance in a public subnet with an associated key pair and security group. Configured networking and verified accessibility before tightening permissions.

2. SSH Session Verification

Connected to the EC2 instance using SSH and validated outbound connectivity with ping and curl commands.
This confirmed proper route table configuration and Internet Gateway setup.

3. VPC Flow Logs – ACCEPT Events

Captured accepted traffic in CloudWatch, showing successful ICMP and HTTP requests from the EC2 instance to the Internet.
These entries verify proper flow log configuration and confirm the instance’s outbound reachability.

4. VPC Flow Logs – REJECT Events

Captured rejected packets after tightening security group and NACL rules.
These REJECT entries demonstrate that my access controls were working correctly and that I could analyze network denials via CloudWatch.

5. CloudWatch Alarm Configuration

Created a CloudWatch alarm to monitor the RejectCount metric within the VPCFlowLogs namespace.
The alarm triggers when rejected packets exceed a defined threshold over a 5-minute window — turning log data into actionable alerts.

6. SNS Notification Alert

Integrated Amazon SNS to send email alerts when the CloudWatch alarm detects high rejection activity.
Though I encountered a token validation issue during testing, this step solidified my understanding of integrating CloudWatch with SNS topics.

🧠 Key Learnings & Takeaways

Mastered VPC Flow Logs configuration and filtering to analyze network traffic.

Strengthened understanding of CloudWatch metrics, alarms, and alerts.

Learned to resolve complex file permission and SSH key issues in Windows PowerShell.

Practiced least-privilege access control by refining NACLs and Security Groups.

Reinforced the value of Cloud monitoring and alert automation for proactive system management.

🧾 Summary

This project simulated a real-world CloudOps workflow — from instance provisioning to logging, alerting, and troubleshooting.
By completing it, I proved my ability to not only configure cloud infrastructure but also analyze and automate monitoring around it.
