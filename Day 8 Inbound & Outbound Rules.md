# 📅 Day 8 — Inbound & Outbound Rules in AWS Security Groups 
Security Groups act as a virtual firewall in AWS that protect EC2 instances from unwanted traffic and ensure secure communication.
Today, I learned how Inbound and Outbound rules work — a critical skill for deploying secure applications in real DevOps workflows.---
 
## AWS Networking — EIP + Inbound + Outbound Rules
 
--- 

### 🟦 What is Elastic IP (EIP)?   

| Feature            | Description                | 
| ------------------ | -------------------------- | 
| IP Type            | Static Public IPv4         |
| Changes on reboot? | ❌ No — Always same IP     |
| Attach/Detach      | ✔ Yes (between EC2 or ENI) |
| Usage              | Public-facing workloads    |

#### Why is EIP needed?

| Issue with normal Public IP        | EIP Solution                    |
| ---------------------------------- | ------------------------------- |
| IP changes on stop/start           | Fixed Public IP avoids breakage |
| DNS mapping breaks                 | Stable IP for web apps          |
| Can't maintain public connectivity | Reliable customer access        |

#### Where EIP is used?

| Use Case      | Reason                    |
| ------------- | ------------------------- |
| Web Servers   | Same public IP always     |
| Bastion Hosts | Secure admin access       |
| NAT Instances | Private subnet → Internet |
| VPN Gateways  | Stable connection point   |

#### AWS Console Steps

| Step | Action                              |
| ---- | ----------------------------------- |
| 1    | Go to EC2 → Elastic IPs → Allocate  |
| 2    | Select Allocate IP                  |
| 3    | Associate with EC2/ENI              | 
| 4    | Add SG rules to allow public access |

> 📝 EIP is **free only when attached** to a running instance.

---

## 🔐 Security Groups (SG) — Firewall for EC2 Services

| Direction    | Controls                       | Default   |
| ------------ | ------------------------------ | --------- |
| **Inbound**  | Traffic coming **into EC2**    | Deny All  |
| **Outbound** | Traffic going **out from EC2** | Allow All |

---

### ⬇️ Inbound Rules — Entering EC2

| Port | Protocol | Source       | Purpose                  |
| ---- | -------- | ------------ | ------------------------ |
| 22   | SSH      | My Public IP | Secure instance login    |
| 80   | HTTP     | 0.0.0.0/0    | Public website access    |
| 443  | HTTPS    | Anywhere     | Secure web access        |
| 3306 | MySQL    | App-SG only  | Protect DB from Internet |

📌 **If a port isn't allowed → access blocked**

Example Traffic Flow:

```
Internet → Allow 80 → Web Server EC2
Admin → Allow 22 → EC2
App Server SG → Allow 3306 → Database EC2
```

---

### ⬆️ Outbound Rules — Leaving EC2

| Use Case       | Why Needed               |
| -------------- | ------------------------ |
| System Updates | Install packages         |
| API Calls      | App to external services |
| DB Connection  | App to database          |
| NAT Access     | Private → Internet       |

| Rule                | Meaning                 |
| ------------------- | ----------------------- |
| Allow All Outbound  | Normal EC2 networking   |
| Restrict to DB Port | EC2 can talk only to DB |

📌 **Default: Allow All Outbound**

---

### 🔄 Security Group Traffic Flow

```
                ⬇ Allowed Inbound
Internet ------------------> EC2 Instance
                ⬆ Allowed Outbound
```

---

## 🧠 Interview Concepts

### SG vs NACL

| Feature        | Security Group | NACL                |
| -------------- | -------------- | ------------------- |
| Applies To     | Instance       | Subnet              |
| Statefulness   | Stateful       | Stateless           |
| Return Traffic | Auto-allowed   | Must allow manually |
| Rule Types     | Allow only     | Allow + Deny        |

### Common AWS Ports

| Service    | Port |
| ---------- | ---- |
| SSH        | 22   |
| HTTP       | 80   |
| HTTPS      | 443  |
| MySQL      | 3306 |
| PostgreSQL | 5432 |

---

## 🎯 Hands-On Example — Public EC2 Web Server

| Step | Action                          |
| ---- | ------------------------------- |
| 1    | Launch Ubuntu EC2               |
| 2    | Allocate + Associate EIP        |
| 3    | Configure SG:                   |
|      | • 80 (HTTP) → Anywhere          |
|      | • 22 (SSH) → My IP only         |
| 4    | Browse to EIP → ✔ Webpage up 🎉 |

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
