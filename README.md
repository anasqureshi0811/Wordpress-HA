Description of Stack:
•	This template deploys highly available, secure, fault tolerant WordPress site into an existing VPC consisting of two public and two private subnets. 
•	This includes both the application and database resource separate both in 2 private subnets and 2 availability zones.
•	This templated can be used for both development and production environments with development using less EC2 resources through Autoscaling options and not provisioning RDS in Multi-AZ mode. WordPress is automatically configured to use the database on start-up.
•	Web Servers and RDS resources are in private subnets with NATGW access 
•	Elastic Load Balancer is in Public subnets with internet gateway access. 
•	A Bastion host with public IP 10.0.142.255 is in one of the Public Subnets of this VPC, use bastion to SSH to access the webservers.
•	This template creates EC2 instances and related resources. You will be billed for
•	the AWS resources used if you create a stack from this template.
•	Test Environment can be created by using RDS Multi-AZ option false and EC2 Autoscaling to create less EC2 nodes.
•	The Private Subnets are routed to internet through NAT GWs.
•	The Public Subnets are routed to internet through Internet GWs.

S3 URL of Master Cloudformation Template
https://s3-ap-southeast-2.amazonaws.com/wordpresssite-afaq/Master-Wordpress.yaml

Role ARN to run Cloudformation template
arn:aws:iam::169894940861:role/cloudformationtos3-afaq

Network Configuration Parameters
-	VPCID (Sydney)  vpc-0690a8165c5c9cf2c
-	VPCCIDR 10.0.0.0/16
-	PrivateSubnet1ID subnet-0db022a853e81b69d (vpc-0690a8165c5c9cf2c)
-	PrivateSubnet2ID subnet-0e801dbf0a9bbd311 (vpc-0690a8165c5c9cf2c)
-	PublicSubnet1ID subnet-0fa82f14a41a0dd39 (vpc-0690a8165c5c9cf2c)
-	PublicSubnet2ID subnet-09e347e8bccce05d6 (vpc-0690a8165c5c9cf2c)
-	ALBAccessCIDR 0.0.0.0/0
-	BastionSecurityGroupID sg-0e76a04d45457c412 (Sydney VPC vpc-0690a8165c5c9cf2c )

Aurora Database Configuration Parameters
-	DBAutoMinorVersionUpgrade  true/false
-	DBBackupRetentionPeriod number of days (1-35)
-	DBPreferredBackupWindow time HH:MM-HH:MM
-	DBInstanceClass select from the list
-	DBMasterUserPassword minimum 8 characters (small, capital and digit)
-	DBMultiAZ true or false
-	DatabaseName minimum 8 alphanumeric characters
-	DatabaseMasterUsername minimum 8 characters (small, capital and digit)

WordPress Webserver Configuration
-	WordpressAdminPassword minimum 8 characters (small, capital and digit)
-	WebServerInstanceType select from the list
-	WebServerInstanceMonitoring enabled or disabled
-	KeyPairName AQ-AnsibleController-KeyPair
-	WebServerMinSize 1 node
-	WebServerMaxSize 12 nodes
-	WebServerDesiredCapacity 1-12 nodes
-	AutoScalingNotificationEmail any valid one

PLEASE REFER TO INSTRUCTIONS FILE ATTACHED FOR NETWORK DIAGRAM
