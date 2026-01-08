# 📅 Day 18 | AWS CloudFormation — Infrastructure as Code (IaC) in AWS ☁️

Today, I learned about **AWS CloudFormation**, which is an **Infrastructure as Code (IaC)** service that helps create, update, and delete AWS resources automatically using **YAML or JSON templates**. 
  
CloudFormation is widely used in DevOps to deploy infrastructure in a **repeatable, consistent, and automated way**.
  
---        
   
## 🏗️ AWS CloudFormation (DevOps – Infrastructure Automation)   
     
### 🔹 Amazon CloudFormation  
 
**Service Type**    
Infrastructure as Code (IaC)  
 
**Template Format**    
YAML / JSON  

**Key Features**  
- Automated infrastructure creation  
- Manages full lifecycle (Create, Update, Delete) 
- Consistent deployments
- Automatic rollback on failure
- Fully managed by AWS 

--- 

## 🔹 Why We Use CloudFormation in DevOps

CloudFormation is used when we need:

- ✅ Automated infrastructure deployment  
- ✅ Repeatable environments (Dev / Test / Prod)  
- ✅ Version-controlled infrastructure  
- ✅ Reduced manual errors   
- ✅ Easy rollback and recovery  

---

## 🔹 Real-World DevOps Use Cases

| Use Case | Why CloudFormation |
|--------|-------------------|
| EC2 & VPC setup | One-click infrastructure |
| Auto Scaling | Consistent scaling |
| CI/CD pipelines | Infrastructure automation |
| Disaster recovery | Easy recreation |
| Multi-environment setup | Template reuse |

---

## 🔹 How CloudFormation Works (Architecture)

User  
↓  
CloudFormation Template (YAML / JSON)  
↓  
CloudFormation Stack  
↓  
AWS Resources (EC2, S3, VPC, IAM, RDS)

---

## 🔹 Key CloudFormation Components

- **Template** – Blueprint of infrastructure  
- **Stack** – Deployed version of template  
- **Resources** – AWS services defined  
- **Parameters** – Input values  
- **Outputs** – Results like IP, DNS  

---

## 🔹 Step-by-Step: How to Use CloudFormation

### 🔹 Step 1: Create Template
Create a YAML or JSON file defining AWS resources.

```yaml
Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
```

## 🔹 Step 2: Create Stack

- AWS Console → CloudFormation  
- Click **Create Stack**  
- Upload template  
- Enter stack name  
- Click **Create**

---

## 🔹 Step 3: Stack Creation

CloudFormation:
- Creates resources automatically  
- Handles dependencies  
- Shows status: `CREATE_COMPLETE`

---

## 🔹 Step 4: Update Stack

- Modify template  
- Click **Update Stack**  
- Resources update automatically

---

## 🔹 Step 5: Delete Stack

- Delete stack  
- All resources are deleted safely

---

## 🔹 CloudFormation vs Terraform (Interview)

| Feature | CloudFormation | Terraform |
|------|---------------|-----------|
| Provider | AWS only | Multi-cloud |
| Language | YAML / JSON | HCL |
| State | AWS managed | Local / Remote |
| Owner | AWS | HashiCorp |

---

## 🔹 CloudFormation Usage in DevOps

| Tool | Usage |
|----|-----|
| Jenkins | Infra automation |
| CI/CD | Stack deployment |
| Git | Template versioning |
| CodePipeline | IaC workflow |
| DevOps Teams | Environment setup |

---

## 🔹 Common Interview Questions

**Q1:** What is CloudFormation?  
✔ Infrastructure as Code service in AWS.

**Q2:** Supported template formats?  
✔ YAML and JSON.

**Q3:** What is a Stack?  
✔ Deployed template.

**Q4:** Does CloudFormation support rollback?  
✔ Yes.

---

## 🔹 One-Line Interview Answer

**AWS CloudFormation is an Infrastructure as Code service used to automate AWS resources using YAML or JSON templates.**

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
