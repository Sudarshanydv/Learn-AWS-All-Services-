## 📅 Day 17 | AWS EFS (Elastic File System) — Shared Storage in AWS 🗂️☁️

Today, I learned about **Amazon EFS (Elastic File System)**, which is a **fully managed, scalable, shared file system** in AWS.  
EFS allows multiple EC2 instances to **read and write data simultaneously**, making it ideal for **DevOps and cloud-native architectures**.

EFS helps in building **highly available, scalable, and persistent storage solutions** for applications running across multiple Availability Zones.
 
--- 
 
# 🗂️ AWS EFS (DevOps – Shared File System)
   
## 🔹 Amazon EFS (Elastic File System)

### Service Type
- File-based storage service
- Uses **NFS protocol (Port 2049)**

### Key Features
- Shared storage across multiple EC2 instances
- Automatically scales storage
- Highly available (Multi-AZ)
- Fully managed by AWS
- Linux-based file system

### Common DevOps Use Cases
- Jenkins shared workspace
- Kubernetes Persistent Volumes (PV/PVC)
- Web application shared uploads
- Centralized logs storage
- WordPress media storage

### One-Line Summary (Interview)
> **Amazon EFS is a fully managed shared file system that provides scalable and highly available storage for multiple EC2 instances across availability zones using NFS.**

# AWS EFS (Elastic File System) – Step by Step DevOps Guide

This guide explains **Amazon EFS** in a **simple, fresher-friendly DevOps way**, ready to upload on **GitHub (Markdown format)**.

---

## 1️⃣ What is AWS EFS?

**Amazon EFS (Elastic File System)** is a **fully managed, scalable, shared file system** provided by AWS.

👉 Think of EFS like **Google Drive for EC2 instances** — multiple EC2 instances can **read and write the same data at the same time**.

---

## 2️⃣ Why We Use EFS in DevOps

EFS is used when we need:

* ✅ Shared storage between multiple EC2 instances
* ✅ Persistent data (data survives EC2 termination)
* ✅ High availability (multi-AZ)
* ✅ Linux-based file system (NFS)

---

## 3️⃣ Real-World DevOps Use Cases

| Use Case                      | Why EFS                 |
| ----------------------------- | ----------------------- |
| Web application uploads       | Same files for all EC2  |
| Jenkins shared workspace      | Multiple Jenkins agents |
| Kubernetes persistent storage | Shared PVC              |
| Centralized logs              | Common log directory    |
| WordPress media               | Shared media files      |

---

## 4️⃣ How EFS Works (Architecture)

```
User
 ↓
Load Balancer
 ↓
EC2 (AZ-1) ─┐
EC2 (AZ-2) ─┼──> EFS (Shared File System)
EC2 (AZ-3) ─┘
```

* EFS is **regional**
* Uses **NFS protocol (Port 2049)**
* Mounted like a folder inside EC2

---

## 5️⃣ EBS vs EFS vs S3 (Interview Comparison)

| Feature       | EBS           | EFS          | S3       |
| ------------- | ------------- | ------------ | -------- |
| Storage Type  | Block         | File         | Object   |
| Attach        | Single EC2    | Multiple EC2 | Internet |
| OS Support    | Linux/Windows | Linux only   | Any      |
| Mountable     | Yes           | Yes          | No       |
| Shared Access | ❌             | ✅            | ✅        |

---

## 6️⃣ Step-by-Step: How to Create and Use EFS

### 🔹 Step 1: Create EFS

1. AWS Console → **EFS**
2. Click **Create file system**
3. Select **VPC**
4. Availability Zones → Auto selected
5. Click **Create**

---

### 🔹 Step 2: Configure Security Group

EFS needs **NFS access**.

**Inbound Rule:**

```
Type: NFS
Port: 2049
Source: EC2 Security Group
```

---

### 🔹 Step 3: Launch EC2 Instance

* Amazon Linux 2
* Same VPC as EFS
* Attach same Security Group
* SSH into the instance

---

### 🔹 Step 4: Install EFS Utilities

```bash
sudo yum install -y amazon-efs-utils
```

---

### 🔹 Step 5: Create Mount Directory

```bash
sudo mkdir /efs
```

---

### 🔹 Step 6: Mount EFS to EC2

```bash
sudo mount -t efs fs-xxxx:/ /efs
```

Check mount:

```bash
df -h
```

---

### 🔹 Step 7: Test Shared Storage

```bash
cd /efs
sudo touch devops.txt
```

Mount the same EFS on another EC2 → file will be visible ✅

---

## 7️⃣ Auto-Mount EFS on Reboot (Important)

Edit fstab file:

```bash
sudo nano /etc/fstab
```

Add entry:

```bash
fs-xxxx:/ /efs efs defaults,_netdev 0 0
```

---

## 8️⃣ EFS Performance Modes

| Mode            | Usage               |
| --------------- | ------------------- |
| General Purpose | Web apps, CMS       |
| Max I/O         | Big data, analytics |

---

## 9️⃣ EFS Storage Classes

| Class                  | Cost                 |
| ---------------------- | -------------------- |
| Standard               | Normal access        |
| Infrequent Access (IA) | Lower cost           |
| One Zone               | Cheapest (single AZ) |

---

## 🔟 EFS Usage in DevOps Tools

| Tool       | Usage                    |
| ---------- | ------------------------ |
| Jenkins    | Shared workspace         |
| Docker     | Shared volume            |
| Kubernetes | Persistent Volumes       |
| Terraform  | Infrastructure creation  |
| Ansible    | Auto mount configuration |

---

## 1️⃣1️⃣ Common Interview Questions

**Q1: Can EFS be mounted on multiple EC2 instances?**
✔ Yes, simultaneously.

**Q2: Is EFS AZ-specific?**
✔ No, it is regional.

**Q3: Which protocol does EFS use?**
✔ NFS (Port 2049).

**Q4: Can Windows use EFS?**
✔ No, only Linux supports EFS.

---

## 1️⃣2️⃣ One-Line Interview Answer

> **Amazon EFS is a fully managed, scalable, shared file system that allows multiple EC2 instances across availability zones to access the same data using NFS.**

---

## Thank You

## 🔗 Connect With Me
| 🌐 Platform                  | 🔗 Link                                              |
| ---------------------------- | ---------------------------------------------------- |
| 🐙 **GitHub**                | [https://lnkd.in/d2F3JPa3](https://lnkd.in/d2F3JPa3) |
| ✍️ **Dev.to Blog**           | [https://lnkd.in/dNtgqAME](https://lnkd.in/dNtgqAME) |
| 💼 **LinkedIn**              | [https://lnkd.in/d3NctxFT](https://lnkd.in/d3NctxFT) |
| 📄 **Resume (Google Drive)** | [https://lnkd.in/dHDNsd_D](https://lnkd.in/dHDNsd_D) |

## 🔖 Hashtags
#AWS #DevOps #CloudComputing #AWSLearning #EBS #VolumeMounting #DataPersistence #LearningJourney #CareerGrowth #DevOpsEngineer #AWSCommunity

---

⭐ If you like this guide, don’t forget to star the repo!
