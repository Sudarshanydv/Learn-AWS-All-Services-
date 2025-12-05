# aws-eip-sg-guide

A small, GitHub-ready repository that explains **Elastic IP (EIP)**, **Inbound (IN) rules**, and **Outbound (OUT) rules** in AWS — with clear explanations, best-practices, examples, and ready-to-run commands (AWS CLI & Terraform) designed so you can `git push` this repo to GitHub and share or use it as a learning lab.

---

## Repo structure

```
aws-eip-sg-guide/
├── README.md
├── LICENSE
├── .gitignore
├── docs/
│   ├── 01_eip.md
│   └── 02_security_groups.md
├── examples/
│   ├── aws-cli/
│   │   └── setup_ec2_eip_sg.sh
│   └── terraform/
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
└── templates/
    └── user-data.txt
```

---

> **How to use:** clone this repository locally, read the docs in `/docs`, then try the examples in `/examples/aws-cli` (quick) or `/examples/terraform` (infrastructure-as-code). The scripts assume you have AWS credentials configured (`aws configure`) and appropriate IAM permissions.

---

## Files included (summary)

* `README.md` — high level overview + quick start.
* `docs/01_eip.md` — full explanation of Elastic IP: use-cases, behaviour, costs, examples.
* `docs/02_security_groups.md` — inbound/outbound rules, stateful vs stateless, SG vs NACL, examples & best practices.
* `examples/aws-cli/setup_ec2_eip_sg.sh` — bash script that:

  * launches a small EC2 instance (Amazon Linux 2)
  * creates a security group with recommended inbound/outbound rules
  * allocates an Elastic IP and associates it to the instance
  * prints connection details
* `examples/terraform/*` — minimal Terraform configuration to create VPC, subnet, security group, EC2 instance, and an Elastic IP associated to the instance.
* `templates/user-data.txt` — simple Apache install user-data for the EC2 instance to show a web page on `http://<EIP>`.
* `LICENSE` — MIT license.
* `.gitignore` — common ignores (credentials, .terraform, etc.).

---

If you'd like, I can also:

* Create a ZIP of the repo here for direct download; or
* Push it to a GitHub repository (I can give you the `git` commands and a ready `git remote add` snippet) — you will need to run the commands locally.

---

## AWS Networking — EIP + Inbound + Outbound Rules

---

### 🟦 What is Elastic IP (EIP)?

| Feature            | Description                |
| ------------------ | -------------------------- |
| IP Type            | Static Public IPv4         |
| Changes on reboot? | ❌ No — Always same IP      |
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

*End of repository summary.*
