# AWS EFS Multi-OS Setup

This project demonstrates how to **create and connect an Amazon Elastic File System (EFS)** to multiple EC2 instances running **different operating systems** — Ubuntu, Red Hat Enterprise Linux (RHEL), and Amazon Linux 2.

---

## 🧠 Overview

Amazon EFS (Elastic File System) is a fully managed, scalable, and shared NFS file system for use with AWS Cloud services and on-premises resources.  
This setup allows multiple EC2 instances (with different OS) to access the same shared storage.

---

## ⚙️ Steps Covered in the Documentation

1. **Create an EFS File System**
   - Using AWS Console.
   - Configure mount targets and security groups.

2. **Launch 3 EC2 Instances**
   - Ubuntu 22.04 LTS  
   - Red Hat Enterprise Linux 9  
   - Amazon Linux 2  

3. **Install NFS Utilities**
   - Install the necessary NFS client packages for each OS.

4. **Mount EFS on Each Instance**
   - Mount the shared EFS to `/mnt/efs`.

5. **Verify Shared Access**
   - Ensure all instances can read/write to the same shared directory.

6. **(Optional)** Configure `/etc/fstab` to mount automatically on boot.

---

## 📄 File Included

| File | Description |
|------|--------------|
| **EFS_MultiOS_Setup.docx** | Step-by-step Word document for EFS setup across multiple EC2 operating systems. |

---

## 🧩 AWS Services Used

- **Amazon EFS** — for shared file storage  
- **Amazon EC2** — virtual servers for different OS  
- **Amazon VPC** — for networking and security groups  

---

## 🧪 Verification

After mounting, create a test file on one instance:
```bash
sudo touch /mnt/efs/test.txt
```

Check from other instances:
```bash
ls /mnt/efs
```

✅ You should see the same file on all three — confirming shared storage.

---

## 🧰 Tools & Technologies
- AWS Management Console / CLI
- NFS Protocol
- Linux command line
- SSH

---

## 👩‍💻 Author

**Yellamma Mittagouni**  
AWS Certified DevOps Engineer  
📍 Bangalore  
📧 [yellamma.187@gmail.com](mailto:yellamma.187@gmail.com)

---

## ⭐ Contribution
If you found this helpful, feel free to **star ⭐ this repo** or **fork it** to build your own AWS automation.
