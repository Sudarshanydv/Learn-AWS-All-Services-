# 📅 Day 14 | AWS NACL — Subnet-Level Security in AWS 🔐
 
**NACL (Network Access Control List)** is a subnet-level firewall in AWS VPC.  
It controls what traffic is allowed **in and out of each subnet**, acting like a security gate at the subnet boundary.

If you’re learning AWS networking, mastering NACL is a key step in building secure cloud architectures.
 
---
   
## 🔥 Why NACL Is Important in AWS & DevOps  

- 🛡️ Adds an extra layer of security at the **subnet** level  
- 🔁 Controls inbound & outbound traffic (stateless)   
- 🚫 Supports both **ALLOW** and **DENY** rules  
- 📦 Protects private subnets (App Servers, Databases, EKS Nodes)  
- ⚙️ Often used in **secure DevOps infrastructure** (EKS, EC2, CI/CD, Load Balancers)

---

# 🟧 What is NACL in AWS?

**NACL (Network Access Control List)** is a **network-level firewall** that controls traffic going **in and out of a subnet** in a VPC.

Think of it as a **security gate for each subnet**.
   
--- 

## 🔥 Why NACL is important in DevOps?

As a DevOps engineer, you work with: 

- VPC creation   
- Subnets (public/private)  
- EC2, Load balancers, NAT  
- Kubernetes clusters (EKS)  
- Terraform or CloudFormation  

All of these use networking, and NACL helps control what traffic is allowed.

**NACL ensures:**

- ✔️ Traffic is restricted  
- ✔️ Only safe ports are open  
- ✔️ Subnet-to-subnet traffic is filtered  
- ✔️ Security best practices are followed

This is important in DevOps pipelines, deployments, and infra automation.

---

# 🟦 Key Features of NACL (Easy to Remember)

1️⃣ **Subnet-Level Firewall**  
A NACL is attached to a **subnet**, not an EC2 instance.

2️⃣ **Stateless**  
➡️ Allow inbound traffic? Then you must allow outbound traffic also.  
Example: Allow port `80` IN → must allow port `80` OUT.

3️⃣ **Allows both:**  
- `ALLOW` rules  
- `DENY` rules

4️⃣ **Rule number order matters**  
Lowest number checked first (100 → 101 → 102…).

5️⃣ **Default NACL = Allow everything**  
6️⃣ **Custom NACL = Deny everything unless allowed**

---

# 🟪 NACL Use Case in DevOps

**Example 1: Public subnet**  
You deploy:  
- EC2 instance (web server)  
- ALB (load balancer)  

NACL allows:  
- HTTP (80)  
- HTTPS (443)  
- SSH (22)

**Example 2: Private subnet**  
You deploy:  
- App server  
- Database  
- EKS worker nodes  

NACL allows only internal traffic:  
- App → DB (3306)  
- Node-to-node communication  
- No public internet access

---

# 💡 Difference Between NACL and Security Group (Interview)

| Security Group | NACL |
|---|---|
| Instance level | Subnet level |
| **Stateful** | **Stateless** |
| Return traffic auto allowed | Must allow separately |
| Only ALLOW rules | ALLOW + DENY rules |
| Easier to manage | Used for high-level subnet control |

---

# 🟩 Simple Example to Understand

## Public Subnet NACL

**Inbound Rules:**
- Allow HTTP (80)  
- Allow HTTPS (443)  
- Allow SSH (22)

**Outbound Rules:**
- Allow ALL

## Private Subnet NACL

**Inbound:**
- Allow 3306 from app subnet

**Outbound:**
- Allow 3306 back to app subnet  
- Deny internet traffic

---

# ✅ Example NACL Rule Table

| Rule No | Type    | Protocol | Port Range | Source / Destination | Action |
|--------:|---------|:--------:|:----------:|:---------------------:|:------:|
| 100     | Inbound | TCP      | 80         | 0.0.0.0/0             | ALLOW  |
| 110     | Inbound | TCP      | 443        | 0.0.0.0/0             | ALLOW  |
| 120     | Inbound | TCP      | 22         | 0.0.0.0/0             | ALLOW  |
| 1000    | Outbound| ALL      | ALL        | 0.0.0.0/0             | ALLOW  |
| *       | -       | -        | -          | -                     | DENY (implicit) |

---

# 🛠️ Terraform Example (minimal)

Use this as a starting point — update `vpc_id`, CIDRs and rule numbers as needed.

```hcl
resource "aws_network_acl" "public_nacl" {
  vpc_id = aws_vpc.main.id
  tags = {
    Name = "public-nacl"
  }
}

resource "aws_network_acl_rule" "allow_http_in" {
  network_acl_id = aws_network_acl.public_nacl.id
  rule_number    = 100
  egress         = false
  protocol       = "6"       # TCP
  rule_action    = "allow"
  cidr_block     = "0.0.0.0/0"
  from_port      = 80
  to_port        = 80
}

resource "aws_network_acl_rule" "allow_https_in" {
  network_acl_id = aws_network_acl.public_nacl.id
  rule_number    = 110
  egress         = false
  protocol       = "6"
  rule_action    = "allow"
  cidr_block     = "0.0.0.0/0"
  from_port      = 443
  to_port        = 443
}

resource "aws_network_acl_rule" "allow_ssh_in" {
  network_acl_id = aws_network_acl.public_nacl.id
  rule_number    = 120
  egress         = false
  protocol       = "6"
  rule_action    = "allow"
  cidr_block     = "0.0.0.0/0"
  from_port      = 22
  to_port        = 22
}

resource "aws_network_acl_rule" "allow_all_out" {
  network_acl_id = aws_network_acl.public_nacl.id
  rule_number    = 1000
  egress         = true
  protocol       = "-1"      # all protocols
  rule_action    = "allow"
  cidr_block     = "0.0.0.0/0"
  from_port      = 0
  to_port        = 0
}

```
## Thank You

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

