 ## AWS Full-Stack Infrastructure Deployment Project
This project demonstrates the complete setup of a production-style, scalable AWS environment from scratch using VPC networking, EC2 instances, NAT Gateway, RDS, and a Java web application running on Apache Tomcat. It includes secure routing, private-public subnetting, and a full database connection.

## Application Code Source:

📂 The Java application source code used in this project was originally taken from the open-source repository: Ai-TechNov/aws-rds-java.
🛠️ I have modified the database schema and updated the pom.xml file to better suit the application and deployment requirements of this project.

## 🔧 Project Architecture:

## 🔹 VPC & Networking:

Created a custom VPC with a 10.0.0.0/16 CIDR block.
Configured 2 Public Subnets and 2 Private Subnets across two Availability Zones:
us-east-1a - 10.0.0.0/20 and us-east-1b - 10.0.16.0/20 .
Attached an Internet Gateway for public internet access.
Created and associated Route Tables for public and private subnets.
Configured a NAT Gateway in a public subnet to provide one-way internet access to private instances.

## 🔹 Compute Layer (EC2):

Launched a Public EC2 (Application Layer) in AZ 1a.
Launched a Private EC2 (Database Layer) in AZ 1b.
Deployed a Bastion Host in the public subnet for SSH access to the private instance.
Installed and configured MySQL Server on the private EC2 instance.

## 🔹 Database Layer (RDS):

Provisioned an Amazon RDS MySQL instance in the private subnet.
Secured RDS using proper security groups, subnet groups, and parameter groups.
Verified private EC2 instance can connect and operate on RDS.

## 🔹 Application Layer (Java + Tomcat):

Deployed another EC2 instance in a public subnet to run a Java web app.
Installed Apache Tomcat, uploaded .war file.
Java application supports:
Creating user accounts
Storing username and password in admin admin123

## 🐱 Apache Tomcat Installation:

Apache Tomcat 9 was installed manually on the EC2 instance to deploy and run the Java web application.

📥 The server was downloaded using the following command:

wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.107/bin/apache-tomcat-9.0.107.zip

## 🗺️ Architecture Diagram:

<img width="878" height="716" alt="Image" src="https://github.com/user-attachments/assets/6f2665f4-f8b7-4017-8c37-3aaf38e169de" />

📄 Infrastructure as Code
This project uses AWS CloudFormation to provision all resources.

View CloudFormation Template
To deploy the stack:

aws cloudformation create-stack
--stack-name fullstack-java-app
--template-body file://cloudformation-template.yaml
--capabilities CAPABILITY_NAMED_IAM

## 🛑 Make Sure to:
Remove any hardcoded passwords, secrets, or keys before uploading.
## 📸 CIDR-Screenshots:

## cloudformation:

<img width="1902" height="917" alt="Image" src="https://github.com/user-attachments/assets/d48b46f5-94b9-461c-8305-c5667f9808fe" />

## demo-vpc:

<img width="1892" height="907" alt="Image" src="https://github.com/user-attachments/assets/983a49e2-d2eb-4adf-815f-00d9dc6ef076" />

## demo-db-sub:

<img width="1890" height="917" alt="Image" src="https://github.com/user-attachments/assets/00f6890b-d67e-4185-ad49-5a31a8fe5cea" />

## demo-app:

<img width="1895" height="912" alt="Image" src="https://github.com/user-attachments/assets/aa67f7cb-2ef5-408f-9ff4-d07b29b4b842" />

## Route-tables:

<img width="1897" height="912" alt="Image" src="https://github.com/user-attachments/assets/0834eaef-1db4-4388-993b-939373f48258" />

## internet gateway (IGW):

<img width="1895" height="922" alt="Image" src="https://github.com/user-attachments/assets/c0ad3e25-f134-4bb1-bbc3-5c74254c9b94" />

## Database-NAT-gatway(DB-NAT):

<img width="1897" height="908" alt="Image" src="https://github.com/user-attachments/assets/0340370b-fec3-4e12-a91b-82eaf7e7a67b" />

## Output of web-app:

<img width="1898" height="975" alt="Image" src="https://github.com/user-attachments/assets/753353d3-a907-4e57-990e-3f8c243d69d9" />

## Register a web-app:

<img width="1691" height="792" alt="Image" src="https://github.com/user-attachments/assets/e0ce0886-7d06-4f34-a757-32dfad4c7cd4" />

## Login web app:

<img width="1568" height="597" alt="Image" src="https://github.com/user-attachments/assets/832cab57-dd83-43a6-b2be-f28a33a6b01f" />

## output of web app:

<img width="1133" height="758" alt="Image" src="https://github.com/user-attachments/assets/10a25c0f-1796-48c0-9c3c-7ed936cee0a1" />

## Author:

**Uday Sairam Kommineni**

**Mail-id:** saikommineni5@gmail.com

**linkedin-url:** https://www.linkedin.com/in/uday-sai-ram-kommineni-uday-sai-ram/





