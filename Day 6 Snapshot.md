## Name – Sudarshan Yadav, Contact - 7709877817
## Email Id – sudarshanyadav4080@gmail.com

# AWS Snapshots — Simple Step By Step Guide 🚀

This repo contains a very simple explanation of AWS Snapshots for quick reference.
 
## 🔹 EBS Snapshot (EC2 Disk Backup) 
 
**Steps:**
1. Select an EBS Volume  
2. Click **Create Snapshot**  
3. Snapshot gets stored in S3 (internally by AWS)  
4. You can restore that snapshot to a new EBS Volume  
5. Attach the volume to any EC2 instance and use it again

**Simple example:**

- Before updating server → take snapshot  
- If update fails → restore snapshot → server comes back to old state

---

## 🔹 RDS Snapshot (Database Backup)

**Steps:**
1. Select RDS Database  
2. Click **Take Snapshot**  
3. AWS stores backup of the full DB  
4. You can restore DB anytime from that snapshot

**Used for:**
- Database backup  
- Database disaster recovery
_______________________________________

## 🔹 Important Things to Remember

| Feature | Meaning |
|--------|---------|
| Incremental | Only changed data stored → saves cost |
| Encrypted | Can protect data with KMS |
| Cross-Region Copy | Useful for disaster recovery |
| Manual Delete | Old snapshots cost money → delete when not needed |

---

## 🔥 Simple One-Line Answer for Interview

> **“Snapshot is a point-in-time backup of AWS storage like EBS and RDS. We take snapshots before changes and restore them when needed for backup and disaster recovery.”**

---
 
# 📌 AWS Snapshot — 20 Interview Q&A

## 1️⃣ What is an AWS Snapshot?
A snapshot is a **point-in-time backup** of your EBS volume or database.

## 2️⃣ Where are EBS snapshots stored?
Stored **internally in Amazon S3** (fully managed by AWS).

## 3️⃣ Are EBS snapshots full or incremental? 
Snapshots are **incremental** → only changed blocks stored.

## 4️⃣ Why do we take a snapshot?
For **backup, rollback, and disaster recovery**.

## 5️⃣ Can we restore a snapshot?
Yes → Create a **new EBS volume** from a snapshot anytime.

## 6️⃣ Can we copy snapshots to another region?
Yes → **Cross-Region Snapshot Copy** for DR.

## 7️⃣ Are snapshots encrypted?
Yes → using **AWS KMS** keys.

## 8️⃣ Do we need to stop an EC2 instance before taking a snapshot?
No → **Live backups** supported (crash-consistent).

## 9️⃣ Do snapshots include OS & configurations?
Yes → Everything on **EBS volume**.

## 10️⃣ How do we reduce snapshot cost?
Delete **unused** snapshots → pay only for storage.

## 11️⃣ Can we share snapshots?
Yes → share with **other AWS accounts** (unencrypted).

## 12️⃣ How to automate snapshot creation?
Using **DLM (Data Lifecycle Manager)** or **AWS Backup**.

## 13️⃣ Can snapshots be scheduled?
Yes → via **Backup Plans / DLM / Lambda cron** jobs.

## 14️⃣ Can we convert a snapshot to an AMI?
Yes → snapshot → **Create AMI** → launch EC2.

## 15️⃣ What is a crash-consistent snapshot?
Backup while system is running → ensures **data consistency**.

## 16️⃣ Can we tag snapshots?
Yes → helps billing & organization.

## 17️⃣ Do snapshots save empty blocks too?
No → only stored data → **cost saving**.

## 18️⃣ If volume deleted, is data gone?
No → Snapshot keeps data safe → can recreate volume later.

## 19️⃣ Is snapshot restore faster?
Yes → Restore fast but **lazy loading** takes time for full data.

## 20️⃣ Snapshot vs AMI
| Feature | Snapshot | AMI |
|--------|----------|-----|
| Content | Only EBS Volume data | OS + Apps + Snapshots |
| Usage | Backup/Restore | Launch EC2 Instances |

---

## 🔗 Connect With Me

- **GitHub:** https://lnkd.in/d2F3JPa3  
- **Dev.to Blog:** https://lnkd.in/dNtgqAME  
- **LinkedIn:** https://lnkd.in/d3NctxFT  

---

# **Thank You** 🙌
