# Highly Available 3-Tier Web Architecture on AWS

## Project Overview
This project demonstrates the design and deployment of a secure, highly available, and scalable 3-tier cloud architecture on Amazon Web Services (AWS). The infrastructure isolates web traffic, application processing, and database storage across multiple subnets and Availability Zones to ensure best practices in security and reliability.

## Architecture Components
* **Network (VPC):** Custom VPC (`20.0.0.0/20`) spanning two Availability Zones in the `ap-south-2` (Hyderabad) region.
* **Public Tier:** Houses an Internet Gateway, NAT Gateway, and a Bastion Host (Jump Server) for secure administrative SSH access.
* **Application Tier:** Two private subnets hosting EC2 Linux instances running Apache web servers. Traffic is distributed across these instances using an Application Load Balancer (ALB) configured with session stickiness.
* **Database Tier:** Two isolated private subnets hosting an Amazon RDS MySQL multi-AZ database, accessible exclusively by the application tier.

## Technologies Used
* **AWS Services:** VPC, EC2, Application Load Balancer, NAT Gateway, Internet Gateway, RDS (MySQL), Route Tables, Security Groups.
* **Linux & Automation:** Amazon Linux, Bash scripting (User Data for automated bootstrapping), nano.
* **Web Services:** Apache, phpMyAdmin.

## Security Posture
* The RDS database is completely hidden from the public internet.
* Application servers fetch necessary updates securely via the NAT Gateway.
* Security Groups restrict inbound database traffic to only allow port 3306 connections originating from the Application Security Group.

