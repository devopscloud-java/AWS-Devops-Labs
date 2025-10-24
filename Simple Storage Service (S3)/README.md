# AWS S3 Hands-On Project


This directory demonstrates practical tasks performed using **Amazon S3**, including file storage, versioning, static website hosting, and lifecycle management.

---

## **Project Overview**
This project covers the following operations:

1. Create an S3 bucket for file storage.
2. Upload multiple files with different extensions.
3. Enable versioning and verify multiple object versions.
4. Host a static website using S3.
5. Implement lifecycle rules for cost optimization.

---

## **1. Create an S3 Bucket**
- **Bucket Name:** `<your-bucket-name>`  
- **Region:** `<your-region>`  
- **Purpose:** Store files for testing versioning, hosting, and lifecycle rules.

**AWS CLI Example:**
```bash
aws s3 mb s3://<your-bucket-name> --region <your-region>

