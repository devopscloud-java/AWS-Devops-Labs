# README — Aurora (Amazon RDS) with 2 Read Replicas (different AZs)

## Overview

This repository contains a step-by-step README to create an **Amazon Aurora** (MySQL-compatible or PostgreSQL-compatible) cluster and add **two reader instances (read replicas)** in different Availability Zones for higher availability and read-scaling. Use this as a guide for manual AWS Console, **AWS CLI**, or infrastructure-as-code (CloudFormation/Terraform).

> Notes:
>
> * "Read replicas" in Aurora are additional *reader instances* within the same DB cluster. They share storage and can be placed in different AZs.
> * Replace placeholders (`<...>`) with your values.

---

## Architecture (high level)

Writer (primary) instance (AZ-a)
|
Shared distributed storage (Aurora cluster volume)
/ 
Reader instance (AZ-b)    Reader instance (AZ-c)

---

## Prerequisites

1. An AWS account with required IAM permissions (RDS, EC2 for networking, VPC, IAM, CloudFormation/Terraform if applicable).
2. AWS CLI configured (`aws configure`) or access to AWS Console.
3. A VPC with at least 3 subnets in different AZs (private subnets recommended). Aurora cluster requires a DB subnet group containing multiple private subnets.
4. Security Group that allows the DB port (3306 for MySQL-compatible, 5432 for PG) from your application or bastion host.

**Minimum IAM policy needs** (example actions): `rds:*`, `ec2:Describe*`, `ec2:CreateSecurityGroup`, `ec2:AuthorizeSecurityGroupIngress`, `iam:PassRole` if using roles.

---

## Steps — Console (quick)

1. **Create DB subnet group**

   * RDS -> Subnet groups -> Create DB Subnet Group -> choose VPC -> add subnets in 2–3 AZs.
2. **Create Security Group**

   * EC2 -> Security Groups -> Create one that allows incoming DB port (3306) from your app servers or your IP (for testing).
3. **Create an Aurora DB cluster**

   * RDS -> Databases -> Create database -> Engine options -> Amazon Aurora (choose MySQL-compatible or PostgreSQL-compatible).
   * Select *"Provisioned"* cluster.
   * In "DB cluster identifier", give a name.
   * Configure the initial writer DB instance (instance class, AZ optional).
   * Select DB subnet group and security group created earlier.
   * Enable automatic backups, monitoring as needed.
   * Create.
4. **Add reader instances (read replicas)**

   * After the cluster is created, open the cluster and choose *Actions -> Add reader*.
   * For each reader instance, pick an instance class and specify the Availability Zone to place it in a different AZ than the writer and the other reader.
   * Create two readers in two distinct AZs.
5. **Test**

   * Connect to writer endpoint for writes, reader endpoint for reads (Aurora provides cluster endpoint and reader endpoint).

