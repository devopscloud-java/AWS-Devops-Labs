# 🌐 AWS RDS MariaDB Setup and Connection Guide

## 🧩 Overview
This project demonstrates how to:
1. Create an **Amazon RDS** database using the **MariaDB** engine  
2. Connect to the database using:
   - 🪟 **SQL Client on Windows**
   - 🐧 **Linux-based EC2 Instance**

---

## 🛠️ Step 1: Create a MariaDB RDS Instance

### 1️⃣ Open RDS Console
- Navigate to **AWS Management Console → RDS**
- Click **Create database**

### 2️⃣ Choose Database Creation Method
- Select **Standard create**

### 3️⃣ Select Engine
- Choose **MariaDB**

### 4️⃣ Configure Settings
| Setting | Value |
|----------|--------|
| DB Instance Identifier | `mariadb-instance` |
| Master Username | `admin` |
| Master Password | (your strong password) |
| Instance Type | `db.t3.micro` (Free Tier) |
| Storage | Default or as per need |

### 5️⃣ Connectivity Settings
- **VPC:** Choose existing or create new  
- **Public access:** ✅ *Yes (for testing)*  
- **VPC Security Group:** Allow inbound traffic on **port 3306**

### 6️⃣ Database Authentication
- Select **Password authentication**

### 7️⃣ Create the Database
- Click **Create database**
- Wait until the instance status shows **Available**

---

## 🪟 Step 2: Connect Using SQL Client (Windows)

### 🔹 1. Install a SQL Client
Download and install:
- [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)
- or [HeidiSQL](https://www.heidisql.com/download.php)

### 🔹 2. Retrieve Connection Details
From AWS Console:
- Go to **RDS → Connectivity & Security tab**
- Copy **Endpoint** and confirm **Port (3306)**

### 🔹 3. Connect to the Database
Open SQL Client and enter:
- **Hostname:** `<RDS-endpoint>`
- **Port:** `3306`
- **Username:** `admin`
- **Password:** your password

✅ Click **Connect** — you should now be connected!

