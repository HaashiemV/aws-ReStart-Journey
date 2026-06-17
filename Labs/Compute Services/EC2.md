Introduction to Amazon EC2

Overview: This lab provides you with a basic overview of launching, resizing, managing, and monitoring an Amazon EC2 instance.

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.

By the end of this lab, I will be able to:
Launch a web server with termination protection enabled
Monitor Your EC2 instance
Modify the security group that your web server is using to allow HTTP access
Resize your Amazon EC2 instance to scale
Test termination protection
Terminate your EC2 instance

Task 1: Launching your EC2 instance
Step 1: Naming my EC2 instance - Web Server
Step 2: Choosing an Amazon Machine Image (AMI) - Amazon Linux 2023*
Step 3: Choosing an instance type - t3.micro
Step 4: Configuring a key pair - selecting "Proceed without a key pair (Not recommended)"
Step 5: Configuring the network settings 
Step 5.1: In the Network settings pane, chose Edit
For VPC - required, selected Lab VPC.
Still in the Network settings pane, I configured the Security Group as follows:
Security group name - required: Web Server security group
Description: Security group for my web server
Under Inbound security groups rules selected the Remove button
Step 6: Adding storage - kept the default storage configuration 8 GiB disk volume
Step 7: Configuring advanced details 
- Expanded the Advanced details pane.
- Selected the dropdown for Termination protection, then chose Enable.

*When you launch an instance in Amazon EC2, you have the option of passing user data to the instance. These commands can be used to perform common automated configuration tasks and even run scripts after the instance starts. 

Copied the following commands, and pasted them into the User data text box.
#!/bin/bash
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html

The above script does the following:
- Install an Apache web server (httpd)
- Configure the web server to automatically start on boot
- Activate the Web server
- Create a simple web page
- 
Step 8: Launching an EC2 instance - Successfully initiated launch of instance (i-084c5658cbeda4fc9)

Task 2: Monitor Your Instance
Step 1: Selected the instance by checking the box next to the instance and navigated to the bottom of the screen to the Status checks tab.
Confirmed All Status Checks Passed

Task 3: Update Your Security Group and Access the Web Server
When I launched the EC2 instance, I provided a script that installed a web server and created a simple web page. In this task, I will access content from the web server.
Step 1: Selected the instance by checking the box and selected the Details tab.
Step 2: Copied the Public IPv4 address of your instance to your clipboard.
Step 3: Open a new tab in your web browser, pasted the IP address I copied, then press Enter. 
Outcome: Unable to access my web server because the security group is not permitting inbound traffic on port 80, which is used for HTTP web requests.

Step 4: Went back to the EC2 Management Console tab.
Step 5: In the left navigation pane, selected Security Groups located under Network & Security.
Step 6: Selected  Web Server security group.
Step 7: Selected the Inbound rules tab.
- Confirmed the security group currently has no rules.
- Selected Edit inbound rules then select Add rule and configured the rule with the following settings:
Type: HTTP
Source: Anywhere-IPv4
Selected Save rules

Step 8: Return to the web server tab that you previously opened and refresh  the page.
You should see the message Hello From Your Web Server!

Success :)
- <img width="1714" height="293" alt="image" src="https://github.com/user-attachments/assets/172b74d6-fa6c-4f29-9bfd-81fc3fb928fa" />






