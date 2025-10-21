🏗️ AWS Multi-Network Setup — Production & Development Networks
📘 Overview

This project demonstrates how to design and deploy two VPC networks — a Production Network (4-tier) and a Development Network (2-tier) — with proper subnet segregation, routing, and interconnection using AWS VPC peering. The setup ensures security, controlled internet access, and structured tier separation for scalable architecture.

🏢 Production Network
Architecture:

4-tier architecture with the following subnets:

web — Public Subnet

app1 — Private Subnet

app2 — Private Subnet

dbcache — Private Subnet

db — Private Subnet

Steps:

Create a VPC

Example CIDR: 10.0.0.0/16

Enable DNS hostnames and DNS support.

Create Subnets

Subnet Name	Type	Example CIDR	Notes
web	Public	10.0.1.0/24	For web server
app1	Private	10.0.2.0/24	Application layer
app2	Private	10.0.3.0/24	Application layer
dbcache	Private	10.0.4.0/24	Cache database
db	Private	10.0.5.0/24	Primary database

Create an Internet Gateway (IGW)

Attach it to the Production VPC.

Create a NAT Gateway

Place it inside the web subnet (public subnet).

Allocate an Elastic IP for NAT.

Route Tables

Public Route Table:

Associate with web subnet.

Add route to the internet via IGW.

Private Route Table (for app1 & dbcache):

Route internet-bound traffic via NAT Gateway.

Private Route Table (for app2 & db):

No internet route (completely private).

Launch EC2 Instances

Launch 1 instance in each subnet.

Name instances as per their subnet:

web-instance, app1-instance, app2-instance, dbcache-instance, db-instance.

Security Groups (SGs)

Web SG: Allow inbound HTTP (80) and SSH (22) from internet.

App SGs: Allow inbound from web and other app subnets only.

DBCache & DB SGs: Allow inbound only from application layer subnets.

Network ACLs (NACLs)

Public subnet: allow inbound/outbound HTTP, HTTPS, and SSH.

Private subnets: restrict inbound access only to trusted internal subnets.

Internet Access

Allow dbcache and app1 subnets to send internet requests using NAT Gateway routes.

🧩 Development Network
Architecture:

2-tier architecture with:

web — Public Subnet

db — Private Subnet

Steps:

Create a VPC

Example CIDR: 10.1.0.0/16

Create Subnets

Subnet Name	Type	Example CIDR
web	Public	10.1.1.0/24
db	Private	10.1.2.0/24

Internet Gateway (IGW)

Attach to the Dev VPC.

Route Tables

Public Route Table:

Associate with web subnet.

Add route to IGW for internet access.

Private Route Table:

Associate with db subnet (no internet route).

Launch EC2 Instances

web-instance-dev in web subnet.

db-instance-dev in db subnet.

Security Groups

Web SG: Allow HTTP (80), HTTPS (443), and SSH (22) from the internet.

DB SG: Allow inbound only from the web subnet.

Internet Access

Only web subnet can send internet requests.

🔗 Peering Connection Setup

Create VPC Peering Connection

Between Production VPC (10.0.0.0/16) and Development VPC (10.1.0.0/16).

Update Route Tables

Add routes in both VPCs pointing to each other via the peering connection.

Subnet Communication

Enable communication between db subnets of both networks.

Modify security groups of both db instances to allow traffic on the database port (e.g., 3306 for MySQL) from each other’s subnet.

✅ Validation Checklist

 All instances launched and reachable via proper layers.

 Only intended subnets have internet access.

 DB subnets communicate across networks using VPC peering.

 Proper segregation between tiers and environments.

🧠 Key AWS Services Used

VPC

Subnets

Internet Gateway (IGW)

NAT Gateway

Route Tables

Security Groups

Network ACLs

EC2 Instances

VPC Peering
