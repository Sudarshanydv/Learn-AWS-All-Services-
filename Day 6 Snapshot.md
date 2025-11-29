## Name – Sudarshan Yadav, Contact - 7709877817
## Email Id – sudarshanyadav4080@gmail.com

# AWS Snapshots — Simple Guide 🚀

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

## 🔗 Connect With Me

- **GitHub:** https://lnkd.in/d2F3JPa3  
- **Dev.to Blog:** https://lnkd.in/dNtgqAME  
- **LinkedIn:** https://lnkd.in/d3NctxFT  
- **Resume (Google Drive):** https://lnkd.in/dHDNsd_D  

---

# **Thank You** 🙌
