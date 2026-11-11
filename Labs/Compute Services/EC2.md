Introduction to Amazon EC2

Lab Overview

This lab explored the fundamentals of Amazon Elastic Compute Cloud (Amazon EC2), focusing on launching, configuring, monitoring and managing a virtual server in AWS.

The objective was to deploy a basic web server using Amazon Linux 2023, configure network access, monitor instance health, modify compute and storage capacity, and test termination protection.

Duration: Approximately 45 minutes
Service: Amazon EC2
Operating System: Amazon Linux 2023
Initial Instance Type: "t3.micro"

Learning Objectives

By completing this lab, I gained practical experience in:

- Launching and configuring an EC2 instance.
- Enabling termination protection.
- Monitoring EC2 instance status and CloudWatch metrics.
- Configuring security groups to allow HTTP traffic.
- Deploying a basic Apache web server using EC2 user data.
- Resizing an EC2 instance.
- Increasing EBS volume capacity.
- Testing termination protection and safely terminating an instance.

1. Launching the EC2 Instance

I launched an EC2 instance with the following configuration:

Configuration| Selection
Instance name| Web Server
Amazon Machine Image| Amazon Linux 2023
Initial instance type| "t3.micro"
vCPU| 2
Memory| 1 GiB
Key pair| Proceed without a key pair
Network| Lab VPC
Security group| Web Server security group
Root EBS volume| 8 GiB
Termination protection| Enabled

A key pair was not configured because direct login to the instance was not required for this exercise.

Apache Web Server Installation

I used EC2 user data to automate the installation and configuration of the Apache HTTP server during instance launch.

#!/bin/bash
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html

This script installed Apache, configured it to start automatically and created a basic HTML landing page.

After launching the instance, I waited for its state to show Running and its status checks to pass.

2. Monitoring the EC2 Instance

I reviewed the EC2 monitoring information to understand the health and performance indicators available for an instance.

The lab covered:

- System status checks: Assessing the underlying AWS infrastructure.
- Instance status checks: Assessing the operating system and instance accessibility.
- CloudWatch monitoring: Reviewing metrics such as CPU utilisation and network activity.
- Instance screenshots: Using the console's screenshot functionality as a troubleshooting aid.

Basic monitoring provides metrics at five-minute intervals, while detailed monitoring can provide one-minute intervals.

3. Configuring Network Access

Initially, the web server could not be accessed through a browser.

After investigating the issue, I identified that the security group did not contain an inbound rule allowing HTTP traffic.

I updated the security group to allow:

Setting| Configuration
Type| HTTP
Protocol| TCP
Port| 80
Source| Anywhere-IPv4

After saving the rule, I refreshed the browser and successfully accessed the web server.

Successful response:

"Hello From Your Web Server!"

This demonstrated how security group rules control inbound network traffic to EC2 instances.

4. Resizing the EC2 Instance

I explored how to modify the compute capacity of an EC2 instance.

The process involved:

1. Stopping the running EC2 instance.
2. Navigating to the instance type configuration.
3. Changing the instance type from "t3.micro" to "t3.small".
4. Applying the updated configuration.
5. Starting the instance again.

This exercise demonstrated how instance types can be changed to accommodate different compute requirements.

5. Increasing EBS Storage Capacity

I also practised modifying the storage capacity attached to the EC2 instance.

The root EBS volume was increased from:

- Original size: 8 GiB
- Updated size: 10 GiB

This demonstrated how Elastic Block Store (EBS) volumes can be expanded to provide additional storage capacity.

6. Testing Termination Protection

Termination protection was enabled during the initial instance configuration.

I attempted to terminate the instance while protection was enabled. The termination attempt was blocked, demonstrating that the protection setting helps prevent accidental deletion.

I then:

1. Disabled termination protection.
2. Repeated the termination operation.
3. Successfully terminated the EC2 instance.

This exercise demonstrated the importance of safeguards when managing cloud infrastructure.

Key Takeaways

Through this practical exercise, I developed a better understanding of:

- Provisioning virtual servers using Amazon EC2.
- Automating software installation through user data.
- Managing inbound traffic using security groups.
- Monitoring instance health and performance.
- Scaling compute resources by changing instance types.
- Expanding storage using Amazon EBS.
- Protecting infrastructure against accidental termination.

Security and Operational Considerations

The lab used an HTTP inbound rule open to Anywhere-IPv4 to demonstrate web access.

In a production environment, network access should be restricted to the required sources wherever possible. Public-facing applications should also use HTTPS, and infrastructure changes should follow appropriate operational controls.

Termination protection is useful as an additional safeguard, but it should not replace backups, monitoring or sound resource-management practices.

---

This documentation reflects a completed AWS re/Start practical lab. The environment was used for learning and experimentation and should not be interpreted as a production deployment.
