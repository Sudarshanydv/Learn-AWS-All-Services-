# 📌 Amazon Machine Image (AMI) - Complete Step-by-Step Guide

### Today, I learned about Amazon Machine Images (AMI) — and it’s a major building block for AWS & DevOps Engineering! 🤩
### I understood that an AMI is a pre-configured OS + software image used to launch EC2 instances quickly and consistently. It helps in standardizing environments and deploying servers at scale — especially in real-time DevOps and automation workflows.

## Name – Sudarshan Yadav, Contact - 7709877817
## Email Id – sudarshanyadav4080@gmail.com
GitHub: https://github.com/Sudarshanydv
Dev.to Blog: https://dev.to/sudarshan_yadav
LinkedIn: https://www.linkedin.com/in/sudarshan-yadav
Resume (Drive) - https://drive.google.com/file/d/1jas-UeQuCSR6OZCP6pAPTnLiWcJiAVk1/view?usp=drive_link

---

## 1️⃣ Prepare a Source EC2 Instance
- Launch an EC2 instance (pick AMI, instance type, key pair, security group, subnet).
- SSH (Linux) or RDP (Windows) into the instance.
- Install and configure everything you want baked into the AMI:
  - Packages
  - Application code
  - Environment variables
  - Users & permissions
  - Firewall rules
- Clean up before imaging:
  - Remove logs & temporary files
  - Remove credentials, secrets
- For Windows → Run **sysprep** (generalize)

---

## 2️⃣ Stop or Prepare for Snapshot
- Recommended: **Stop instance** for consistent file system state.
- If you want **zero downtime** → use `--no-reboot` (risk of inconsistency)

---

## 3️⃣ Create the AMI (AWS Console)
1. Go to **EC2 → Instances**
2. Select your instance
3. Click **Actions → Image and templates → Create image**
4. Enter:
   - Name
   - Description
   - Reboot options
   - Volume snapshot settings (encryption optional)
5. Click **Create image**

AWS will create EBS snapshots and register the AMI.

---

## 4️⃣ Create the AMI (AWS CLI)
Replace `i-0123456789abcdef0` with your EC2 instance ID:
```bash
aws ec2 create-image \
  --instance-id i-0123456789abcdef0 \
  --name "my-app-ami-2025-11-27" \
  --description "AMI for my app" \
  --no-reboot

## 📌 Check AMI Status

```bash
aws ec2 describe-images --image-ids ami-0abc1234
aws ec2 describe-image-status --image-ids ami-0abc1234
5️⃣ Wait for AMI & Snapshot Creation
AMI becomes available after snapshots complete

Snapshots cost storage → monitor usage

6️⃣ Launch Instances from the AMI
▶️ Console
EC2 → AMIs → Select AMI → Launch → Configure → Launch

▶️ AWS CLI
bash
Copy code
aws ec2 run-instances \
  --image-id ami-0abc1234 \
  --count 1 \
  --instance-type t3.micro \
  --key-name mykey \
  --security-group-ids sg-0123abcd \
  --subnet-id subnet-0ab1c2d3
7️⃣ Share / Copy / Make Public
✔ Share with specific AWS Accounts
bash
Copy code
aws ec2 modify-image-attribute \
  --image-id ami-0abc1234 \
  --launch-permission "Add=[{UserId=123456789012}]"
✔ Copy AMI to another region
bash
Copy code
aws ec2 copy-image \
  --source-image-id ami-0abc1234 \
  --source-region us-east-1 \
  --name "my-ami-copy"
⚠ Make AMI Public (Be Careful)
Exposes full AMI to everyone

Use modify-image-attribute with all

8️⃣ Update / Recreate AMIs (Immutable Approach)
Do not modify AMI directly!

Steps:

Launch instance from AMI

Apply updates / patches

Create a new versioned AMI

Update Launch Templates / Terraform

9️⃣ Automate AMI Builds (Recommended Tools)
Packer

AWS EC2 Image Builder

CI/CD (Jenkins, GitHub Actions)

Process:

Base Image → Provision → Create AMI → Tag → Publish

🔟 Clean Up Old AMIs & Snapshots
Deregister AMI
bash
Copy code
aws ec2 deregister-image --image-id ami-0abc1234
Delete snapshot(s)
bash
Copy code
aws ec2 delete-snapshot --snapshot-id snap-0123456789abcdef0

1️⃣1️⃣ Useful Commands Summary

| Purpose         | Command Example                         |
| --------------- | --------------------------------------- |
| Create AMI      | `aws ec2 create-image`                  |
| List AMIs       | `aws ec2 describe-images --owners self` |
| Launch instance | `aws ec2 run-instances`                 |
| Share AMI       | `aws ec2 modify-image-attribute`        |
| Copy to region  | `aws ec2 copy-image`                    |
| Deregister AMI  | `aws ec2 deregister-image`              |
| List snapshots  | `aws ec2 describe-snapshots`            |

