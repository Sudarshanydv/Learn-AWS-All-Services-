## Day 7 | Today, I learned about EBS Volume Mounting on EC2 — and it’s a key skill for managing persistent storage in AWS! 🔥
I learned how to attach, mount, unmount, and re-attach an EBS Volume to an EC2 instance to ensure data remains safe — even if the instance is stopped or restarted. 💾
This is extremely useful in real DevOps environments where applications need reliable and durable storage. 
  
## 👉 Key things I learned today:
| Concept                   | Explanation                                                            |
| ------------------------- | -------------------------------------------------------------------- |
| **EBS Volume Importance** | Provides persistent and durable storage for EC2 instances            |
| **Block-Level Storage**   | Works like a virtual hard disk and supports file systems & databases |
| **Data Persistence**      | Data remains safe even after unmounting or EC2 stop/start            |
| **File System Support**   | Can format volume using **EXT4** or **XFS** before mounting          | 
| **Disk Verification**     | `lsblk` command helps check available disks and mount points         |
| **Safe Unmounting**       | Always unmount before detaching to prevent **data corruption**       |
| **Attach to Another EC2** | Volume can be detached and reattached to another instance easily     |
| **Best Use Cases**        | Ideal for **databases, logs, backups, and application storage**      |


# 📌 AWS EBS Volume Mounting – Step-by-Step Guide

**Date:** 01/08/2024   
**Topic:** How to create, attach, mount, unmount, and reuse an EBS Volume in AWS

--- 

## 🚀 What You Will Learn
- Create and attach an EBS Volume
- Mount volume inside Linux EC2 instance
- Store data and verify persistence
- Unmount and reattach the same volume to another instance 

---

## 🏗 Step 1: Create an EC2 Instance
Launch a Linux EC2 instance (Amazon Linux / Ubuntu)
 
--- 

## 💽 Step 2: Create an EBS Volume
Go to:
EC2 → Volumes → Create Volume
 
yaml
Copy code
Select: 
- **Volume Type:** gp2 / gp3 
- **Size:** 5–20 GB (example)
- **Availability Zone:** MUST match EC2 instance AZ

> If AZ is different → ❌ Volume cannot be attached

Click **Create Volume** → **Attach Volume** 
 
---

## 🔗 Step 3: Attach Volume to Instance 
EC2 → Volumes → Select Volume → Actions → Attach Volume
 
java
Copy code
Note the device name (Example): 
/dev/xvdf

yaml
Copy code

---

## Step 4: Mounting The Volume in Linux (Terminal)
📌 Check available disks
lsblk

📌 Check if volume contains data
sudo file -s /dev/xvdf

📌 Format the volume (Fresh Volume Only)
sudo mkfs -t xfs /dev/xvdf
## OR
sudo mkfs.ext4 /dev/xvdf

📌 Create a mount directory
sudo mkdir /home/ec2-user/test

📌 Mount the volume
sudo mount /dev/xvdf /home/ec2-user/test

📌 Confirm mount
lsblk

## 📁 Step 5: Create Files & Folders (Data stored inside EBS volume)
cd /home/ec2-user/test
mkdir one two three four five
touch india pune mumbai

## 🔄 Step 6: Unmount Volume

Move back to home directory:

cd ~


Unmount:

sudo umount /dev/xvdf


## 📌 The folder looks empty but the data remains stored inside the EBS volume.

## 🔁 Step 7: Re-Mount to Verify Data
sudo mount /dev/xvdf /home/ec2-user/test
ls /home/ec2-user/test


✔ Your files will appear again!

## 🔁 Step 8: Attach to Another Instance

Unmount first:

sudo umount /dev/xvdf


## ➡️ Detach Volume → Attach to another EC2 instance

Mount again:

sudo mkdir /home/ec2-user/test
sudo mount /dev/xvdf /home/ec2-user/test

## 🔗 Connect With Me
| 🌐 Platform                  | 🔗 Link                                              |
| ---------------------------- | ---------------------------------------------------- |
| 🐙 **GitHub**                | [https://lnkd.in/d2F3JPa3](https://lnkd.in/d2F3JPa3) |
| ✍️ **Dev.to Blog**           | [https://lnkd.in/dNtgqAME](https://lnkd.in/dNtgqAME) |
| 💼 **LinkedIn**              | [https://lnkd.in/d3NctxFT](https://lnkd.in/d3NctxFT) |

## 🔖 Hashtags
#AWS #DevOps #CloudComputing #AWSLearning #EBS #VolumeMounting #DataPersistence #LearningJourney #CareerGrowth #DevOpsEngineer #AWSCommunity
