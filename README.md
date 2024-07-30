# AWS-Multi-Tier-Application-Deployment Using Elastic Beanstalk

Objective:
-

- Create a Virtual Private Cloud (VPC) with public and private subnets.
- Set up route tables, internet gateways, and NAT gateways.
- Configure security groups and deploy a Relational Database Service (RDS).
- Manage database credentials using AWS Secrets Manager.
- Set up IAM roles with necessary permissions.
- Deploy an application into Elastic Beanstalk.
- Implement secret rotation for database credentials.

----

Step-by-Step Process
- 

Step 1: Create a Virtual Private Cloud (VPC)
-
  
Created VPC:
- I built a basic VPC with an internet gateway and attached it to the VPC.
- I defined subnets as follows:

- Public Subnets:
- Dev public subnet 1: CIDR block 10.0.1.0/24 (Availability Zone 1A)
- Two additional public subnets for load balancer and NAT gateway.

- Private Subnets:
- Dev private subnet 2: CIDR block 10.0.2.0/24 (Availability Zone 1B)

- App Subnets:
- App Subnet 1: CIDR block 10.0.10.0/24 (Availability Zone 1A)
- App Subnet 2: CIDR block 10.0.11.0/24 (Availability Zone 1B)

- Database Subnets:
- Database Subnet 1: CIDR block 10.0.20.0/24 (Availability Zone 1A)
- Database Subnet 2: CIDR block 10.0.21.0/24 (Availability Zone 1B)

Step 2: Configure Route Tables
-

Configured Route Tables:
- I created route tables to define traffic routes.
- I set routes for public and private subnets:
- Public subnets route: 0.0.0.0/0 to the internet gateway.
- Private subnets route: 0.0.0.0/0 to the NAT gateway.
- I associated subnets with their respective route tables.

Step 3: Create Security Groups
-

Created Security Groups:
- I created security groups for the database and Elastic Beanstalk.
- I defined inbound rules:
- Dev security group: Allowed inbound traffic from app servers (MySQL/Aurora).

Step 4: Deploy RDS
-

Deployed RDS Database:
- I created subnet groups for the database.
- I selected the appropriate VPC, AZs, and subnets.
- I configured database settings:
- MySQL, free tier, db.t3.micro, and security group.

Step 5: Configure Secrets Manager
-

Configured Secrets Manager:
- I used AWS Secrets Manager to store database credentials.
- I configured the secret with database credentials.

Step 6: Set Up IAM Roles
-

Set Up IAM Roles:
- I created an IAM role with permissions to create instance profiles.
- I configured the role to interact with Secrets Manager.
- I assigned the role to Elastic Beanstalk instances.

Step 7: Deploy Application into Elastic Beanstalk
-

Deployed Application:
- I set up an Elastic Beanstalk application and environment.
- I selected a web server environment and uploaded the source code.
- I configured environment settings: VPC, subnets, security groups, autoscaling, and load balancer.
- I set environment properties (DB endpoint, DB name, secret name).
- I deployed the application and verified the setup.

Step 8: Implement Secret Rotation
-

Implemented Secret Rotation:
- I edited the rotation configuration in Secrets Manager.
- I created a rotation function using Lambda.
- I configured Lambda with the necessary permissions and security groups.

----

Theory
-


Elastic Beanstalk Components
-
![Screenshot 2024-07-25 131156](https://github.com/user-attachments/assets/cf95165e-2422-4d7c-ad7c-17d0e7b79aea)


Elatic Beanstalk Environment Tiers
-

![Screenshot 2024-07-25 131245](https://github.com/user-attachments/assets/4d1d18b1-3320-4fce-a7c6-2e8c960e52c8)


Placement of RDS for Elastic Beanstalk
-

![Screenshot 2024-07-25 131306](https://github.com/user-attachments/assets/09d68b7a-dbcc-4c1f-a1c4-673c8878d013)


Environment Lifecycle
-

![Screenshot 2024-07-25 131327](https://github.com/user-attachments/assets/14393d7b-885d-4748-b480-7309c8586849)


Steps To Decouple Your Database
- 

![Screenshot 2024-07-25 131424](https://github.com/user-attachments/assets/8a5a4dc2-a99c-4dae-a130-9eebb24a0f22)


# Elastic Beanstalk Application Architecture


  
![Screenshot 2024-07-25 131457](https://github.com/user-attachments/assets/10d928db-fd78-4d3d-a7bb-0b78343332a7)

- At the end of this project this is what we created will look like.

----

Summary and Skills Gained:
-

- VPC creation and configuration.
- Route table and internet/NAT gateway setup.
- Security group configuration.
- RDS deployment and management.
- Secrets Manager for secure credential management.
- IAM role and policy configuration.
- Elastic Beanstalk application deployment.
- Implementing secret rotation for enhanced security.

Project Outcome:
-

- Successfully deployed a multi-tier application using best practices.
- Enhanced understanding of secure application deployment in AWS.
- Gained proficiency in using various AWS services and tools.

This documentation serves as a comprehensive guide to deploying a secure and scalable multi-tier application on AWS. Each step includes key learnings and insights to provide a clear understanding of the process.
