Multi-Tier AWS Architecture Deployment with Route 53 and RDS Protection
Overview

This repository contains the infrastructure setup for a three-tier AWS architecture using EC2 instances, RDS, and Route 53. The architecture is designed to separate concerns between Web, Application, and Database tiers, while providing secure access and enabling development teams to test their code independently without relying on system administrators.

Architecture Design
1. Web Tier

Deployment: Public subnet

Resources: EC2 instance

Access Rules:

HTTP (port 80) allowed from the internet

SSH (port 22) allowed from the internet

Purpose: Serve as the frontend layer and accept external requests

2. Application Tier

Deployment: Private subnet within Web Tier VPC

Resources: EC2 instance

Access Rules:

SSH (port 22) allowed only from the Web Tier EC2 instance

Purpose: Business logic and backend processing

3. Database Tier

Deployment: Private subnet within Application Tier VPC

Resources: Amazon RDS MySQL instance

Access Rules:

MySQL (port 3306) allowed only from the Application Tier EC2 instance

Purpose: Persistent data storage

4. Route 53 Hosted Zone

Purpose: Manage DNS and direct traffic to the Web Tier EC2 instance

Setup:

Create a public hosted zone

Map the domain/subdomain to the public EC2 instance’s Elastic IP or public DNS

Proposed Solution for Development Teams

Infrastructure as Code (IaC)

Use AWS CloudFormation or Terraform templates to provision resources automatically.

Development teams can deploy a complete stack without manual configuration, reducing dependencies on system admins.

RDS Retention Policy

Configure the RDS instance with DeletionProtection=True.

Ensures that when the stack is deleted, the RDS database is not removed.

Benefits

Faster testing cycles for developers

Consistent, repeatable infrastructure

Secure and controlled access to resources

Data persistence for the database even if the stack is destroyed
