🧭 AWS CLI Project: Managing S3, EC2, and CloudWatch

🌤️ Overview

This project showcases end-to-end AWS infrastructure management using the AWS CLI — from hosting a static website on Amazon S3, to launching and monitoring an EC2 instance, to automating CloudWatch alarms and notifications.

The project also emphasizes practical DevOps and CloudOps skills by handling all operations through command-line automation, without relying on the AWS Management Console.

🗂️ Objectives

-Create and configure an S3 bucket for static website hosting.
-Launch and manage an EC2 instance using the AWS CLI.
-Implement CloudWatch alarms to monitor instance health and CPU activity.
-Configure SNS notifications for real-time alerts.
-Demonstrate full resource lifecycle management — creation, configuration, monitoring, and cleanup.

☁️ Workflow Summary
1. Amazon S3 — Static Website Hosting
      -Created a new S3 bucket and applied public access policies.
      -Uploaded static content (index.html, error.html) and enabled website hosting.
      -Verified accessibility through the generated regional endpoint.
    Key Concept: Understanding bucket policies, access control, and static hosting configuration through CLI scripting.

2. Amazon EC2 — Instance Creation and Management
      -Identified existing subnets and security groups to integrate networking.
      -Launched a new EC2 instance with key pair authentication and descriptive tags.
      -Verified state, IP, and configuration details through CLI queries.
      -Terminated the instance post-testing to prevent unnecessary billing.
    Key Concept: Lifecycle control of compute resources through AWS CLI commands — from provisioning to termination.

3. Amazon CloudWatch — Monitoring and Automation
      -Created a Status Check Alarm to trigger alerts on EC2 health failures.
      -Configured an Auto-Stop Alarm to halt the instance when CPU usage remained below 5% for 15 minutes.
      -Subscribed an SNS topic to email notifications for real-time alerts.
    Key Concept: Automating resource management and cost optimization with CloudWatch and SNS integration.

4. Resource Cleanup
      -Deleted CloudWatch alarms via CLI.
      -Verified EC2 termination and ensured no active alarms remained.
      -Preserved S3 website as the static endpoint for demonstration purposes.
    Key Concept: Implementing responsible resource cleanup to maintain a cost-efficient environment.

🧠 Skills & Concepts Reinforced
      -AWS CLI Proficiency — mastering syntax, parameters, and output formatting.
      -Infrastructure as Code (IaC) mindset through repeatable command execution.
      -Policy and Permission Management for secure and functional access.
      -Automation and Monitoring with CloudWatch metrics and alarm actions.
      -Cost Optimization using idle instance auto-stop triggers.

🧾 Learning Reflection

This project taught me how to orchestrate AWS infrastructure using only the command line.
It strengthened my understanding of:
      -How AWS services interact through the CLI
      -How JSON and variable references control configurations
      -How automation improves scalability and reduces human error
    This workflow mirrors the real-world skill set of Cloud Engineers and DevOps professionals — emphasizing precision, efficiency, and automation.

📸 Project Screenshots (To showcase the project visually)

      -S3 bucket creation and policy configuration
      -Static website endpoint test
      -EC2 instance summary table (describe-instances output)
      -Termination summary table
      -CloudWatch describe-alarms output
      -SNS subscription confirmation
