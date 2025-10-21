# AWS EC2, EBS, and EFS Implementation Project

This repository demonstrates the practical implementation of various AWS services including EC2, EBS, and EFS to manage web server requirements and storage solutions across multiple regions and operating systems.

---

## Table of Contents
- [Project Overview](#project-overview)
- [AWS Services Used](#aws-services-used)
- [Tasks Performed](#tasks-performed)
- [Setup Instructions](#setup-instructions)
- [Screenshots / Diagrams](#screenshots--diagrams)
- [Author](#author)

---

## Project Overview
The goal of this project is to demonstrate AWS cloud resource management, including the creation and replication of EC2 instances, managing EBS volumes, and configuring EFS for multiple EC2 instances with different OS distributions. This project can be used as a reference for implementing web server infrastructure with scalable and reliable storage.

---

## AWS Services Used
- **Amazon EC2** – Launch and manage virtual servers.
- **Amazon Machine Image (AMI)** – Preconfigured virtual machine image.
- **Amazon EBS** – Block storage for EC2 instances.
- **Amazon EFS** – Elastic file system for shared storage.
- **Regions Covered**:
  - US-East-1 (N. Virginia)
  - US-West-2 (Oregon)

---

## Tasks Performed

### 1. EC2 Instance Creation in US-East-1 (N. Virginia)
- Launched an EC2 instance with Linux OS.
- Configured web server requirements using a custom AMI.
- Verified web server deployment.

### 2. EC2 Instance Replication in US-West-2 (Oregon)
- Copied the AMI from the US-East-1 instance.
- Launched a new EC2 instance in US-West-2 using the copied AMI.

### 3. EBS Volume Management in US-East-1
- Created two EBS volumes and attached them to the EC2 instance.
- Detached and deleted one EBS volume.
- Extended the size of the remaining volume.
- Took a backup (snapshot) of the modified EBS volume.

### 4. EFS Creation and Connection
- Created an Elastic File System (EFS).
- Connected the EFS to three EC2 instances running different OS distributions:
  - Ubuntu
  - Red Hat Linux
  - Amazon Linux 2
- Verified read/write access across all instances.

---

## Setup Instructions

1. **Launch EC2 Instance**
   - Go to the EC2 Dashboard.
   - Select the desired Linux OS.
   - Configure security groups for web server access (HTTP/HTTPS).

2. **Create and Attach EBS Volumes**
   - Navigate to the EBS dashboard.
   - Create volumes and attach to EC2 instances.
   - Detach and delete unnecessary volumes.
   - Modify and extend volume size as needed.

3. **Replicate EC2 in Another Region**
   - Create an AMI of the original instance.
   - Copy AMI to another region.
   - Launch a new EC2 instance from the copied AMI.

4. **Configure EFS**
   - Create a new EFS in the desired VPC.
   - Mount the EFS to multiple EC2 instances using NFS.
   - Test file operations across instances.

---

## Screenshots / Diagrams
*(Add screenshots of EC2 dashboard, EBS volume attachment, EFS mount points, etc.)*

---

## Author
**Renuka Devi**  
AWS Certified DevOps Engineer  
Email: [your-email@example.com]  
Location: Bangalore, India

---

**Repository Status:** Active / Learning Project  

