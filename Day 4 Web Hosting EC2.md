## Name – Sudarshan Yadav, Contact - 7709877817
## Email Id – sudarshanyadav4080@gmail.com
GitHub: https://github.com/Sudarshanydv
Dev.to Blog: https://dev.to/sudarshan_yadav
LinkedIn: https://www.linkedin.com/in/sudarshan-yadav

# 🚀 My Web Hosting Journey with AWS EC2 – Step-by-Step Deployment Guide

# EC2 Launch Guide 

A concise, step-by-step guide to launch and manage an Amazon EC2 instance.

---

## Overview

Amazon EC2 (Elastic Compute Cloud) provides scalable virtual servers (instances) in the AWS cloud. This guide walks you through launching an instance, configuring networking and security, adding storage, connecting, and basic lifecycle management.

> This README is written for AWS & DevOps learners — it uses simple, practical commands and explains choices like AMIs, instance types, security groups, key pairs, EBS, Auto Scaling, and monitoring.

---

## Prerequisites

* An AWS account with permissions to create EC2, VPC, IAM roles, and security groups.
* AWS CLI installed and configured (`aws configure`) OR access to the AWS Management Console.
* A basic understanding of Linux/SSH if using a Linux AMI.

---

## Quick Steps

```markdown
1. Login to AWS Management Console
2. Go to EC2 Dashboard → Launch Instance
3. Choose an AMI (Ubuntu / Amazon Linux)
4. Select Instance Type (e.g., t2.micro for Free Tier)
5. Configure Instance Details:
   - Select VPC & Subnet
   - Add User Data for automated software setup
   - Assign IAM Role for permissions
6. Add Storage using EBS Volume
7. Configure Security Group Rules (SSH, HTTP, etc.)
8. Create/Select Key Pair for secure access
9. Launch & Connect:
   - SSH for Linux
   - RDP for Windows
10. Monitor & Scale:
   - CloudWatch → monitoring
   - Auto Scaling → increase/decrease capacity
   - Load Balancer → distribute traffic
11. Stop/Terminate when done:
   - Stop → Data persists on EBS
   - Terminate → Instance deleted (data removed unless backup)
```

---

## Detailed Steps

### 1. Launch an instance

* Open **EC2 Console** → **Launch Instance**.
* Choose an **AMI** (Amazon Linux 2, Ubuntu Server, or a custom AMI).

### 2. Pick an instance type

* `t2.micro` / `t3.micro` are common for free-tier/testing.
* Choose compute/memory optimized types for heavier workloads.

### 3. Configure instance details

* **Network (VPC)**: Choose an existing VPC or default.
* **Subnet**: Choose a public subnet if the instance needs internet access.
* **Auto-assign Public IP**: Enable for internet-facing instances.
* **IAM Role**: Attach an IAM role with least-privilege permissions if the instance needs to access other AWS services (S3, SSM, etc.).
* **User Data**: Add a shell script to auto-install software on first boot (example below).

**Example user-data (Linux):**

```bash
#!/bin/bash
yum update -y
yum install -y docker
service docker start
usermod -aG docker ec2-user
# pull and run a sample docker image
docker run -d -p 80:80 nginx
```

### 4. Add storage

* Add an EBS volume (gp3 or gp2). Size depends on application needs.
* For data persistence, use EBS-backed instances; EBS persists when instance is stopped.

### 5. Configure security group

* Create or select a security group with required rules:

  * SSH: `tcp 22` (restrict Source to your IP)
  * HTTP: `tcp 80` (if running web server)
  * HTTPS: `tcp 443` (if using TLS)
* Use narrow CIDR ranges for SSH (e.g., `203.0.113.0/32`) — do NOT open SSH to `0.0.0.0/0` in production.

### 6. Key pair

* Create or choose an existing key pair. Download the `.pem` file and keep it secure.
* Example SSH connect command:

```bash
chmod 400 mykey.pem
ssh -i mykey.pem ec2-user@<PUBLIC_IP>
```

Replace `ec2-user` with the AMI-specific username (e.g., `ubuntu` for Ubuntu).

### 7. Launch and connect

* Click **Launch** → Wait until the instance state becomes **running**.
* Connect via SSH (Linux) or RDP (Windows).

### 8. Monitor & Scale

* **CloudWatch**: Set up CPU, memory (custom), and disk alarms.
* **Auto Scaling Group (ASG)**: Define scaling policies based on metrics.
* **Elastic Load Balancer (ELB)**: Distribute traffic across instances.

### 9. Stop vs Terminate

* **Stop**: Instance stops; EBS volumes (if not deleted on termination) retain data. You are charged for EBS storage while stopped.
* **Terminate**: Instance is deleted; by default, the root EBS volume is deleted unless flagged otherwise. Use AMIs or snapshots to preserve state.

---

## DevOps Examples & Tips (Linked to common resume skills)

* **Docker + EC2**: Run containers directly on EC2 or use ECS/EKS for container orchestration.
* **CI/CD**: Host Jenkins on EC2 or use GitHub Actions to deploy artifacts to EC2.
* **Terraform**: Provision EC2, security groups, and ELB using IaC. Example block:

```hcl
resource "aws_instance" "app" {
  ami           = "ami-0abcdef1234567890"
  instance_type = "t3.micro"
  subnet_id     = aws_subnet.public.id
  tags = { Name = "app-server" }
}
```

* **Monitoring**: Install CloudWatch Agent for additional metrics and logs.

---

## Security Checklist

* Use IAM roles instead of embedding credentials.
* Restrict security group access (SSH to trusted IPs only).
* Enable CloudTrail and VPC Flow Logs for auditing.
* Regularly patch AMIs or use automated image baking.

---

## Example commands (CLI)

```bash
# Launch an instance via AWS CLI (simplified)
aws ec2 run-instances --image-id ami-0abcdef1234567890 --count 1 --instance-type t2.micro \
  --key-name mykey --security-group-ids sg-0123456789abcdef0 --subnet-id subnet-0123456789abcdef0

# Describe instances
aws ec2 describe-instances

# Stop an instance
aws ec2 stop-instances --instance-ids i-0123456789abcdef0

# Terminate an instance
aws ec2 terminate-instances --instance-ids i-0123456789abcdef0
```

---

## Add this to your resume as a project (short blurb)

**Deploy sample web application on AWS EC2:** Launched and configured EC2 instances (Ubuntu), automated setup using user-data scripts and Docker, secured instances with Security Groups and Key Pairs, and implemented monitoring using CloudWatch. Automated provisioning with Terraform.

---

## ... Thank You ...
