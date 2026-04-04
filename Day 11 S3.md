# 📅 Day 11 🚀 Amazon S3 | Simple & Secure Cloud Storage
In AWS DevOps projects, storing data safely and accessing it anytime is very important.
AWS provides Amazon S3 — a highly scalable object storage service used worldwide. 

S3 helps us:
✔ Store any type of data (images, logs, code, backups, videos)
✔ Access data anytime from anywhere 
✔ Host static websites like portfolios & landing pages
✔ Store CI/CD build artifacts
✔ Maintain backups & version control
✔ Reduce cost using storage classes & lifecycle rules 

## 📌 S3 = Storage + Security + Scalability + Cost Optimization

It protects data with encryption, IAM policies & multi-AZ durability (11 9’s 🤯),
making it a must-know service for DevOps engineers! 🔥

## 🚀 How to Create an S3 Bucket 

1️⃣ Login to AWS Console  
2️⃣ Go to **S3 service**  
3️⃣ Click **Create bucket**  
4️⃣ Enter a **unique bucket name** (globally unique)  
5️⃣ Choose **Region** (ex: ap-south-1)  
6️⃣ Keep **Block Public Access** ON by default  
7️⃣ Click **Create Bucket**  

✔ Bucket created successfully 🎉

## 📤 How to Upload Files to S3 
 
1️⃣ Open your bucket  
2️⃣ Click **Upload**  
3️⃣ Add files (Images, Zip, PDFs, etc.)  
4️⃣ Click **Upload**  
 
## ✔ Files stored in S3 🗂️
  

## 🔗 How to Connect & Access Files from S3

| Method | Usage | 
|--------|------|
| URL / Public Access | Share files or host static websites | 
| IAM Users / Roles | Secure internal access |
| AWS CLI | Upload / Download using terminal |
| SDKs (Python, Java, Node.js) | Application-level integration |
| CloudFront | Faster access via CDN |

## 📌 Access File using URL  
- Go to your object → Copy **Object URL**   
- If file is **Public** → URL works   
- If **Private** → Access Denied ❌  

👉 To make file public (only when required!)
Objects → Permissions → Enable **Public Read Access**
 

## 💻 How to Connect S3 Using AWS CLI

👉 First configure CLI:
```bash
aws configure
```

👉 Upload File:
```bash
aws s3 cp file.txt s3://mybucket/
```

👉 Download File:
```bash
aws s3 cp s3://mybucket/file.txt .
```

👉 List Buckets:
```bash
aws s3 ls
```

## 🌐 Host a Static Website on S3

1️⃣ Upload **index.html**  
2️⃣ Go to **Properties → Static website hosting → Enable**  
3️⃣ Select **index.html** as the default file  
4️⃣ Make **index.html** public  
5️⃣ Copy **Website Endpoint URL**  
6️⃣ Open in browser → 🎉 Website is Live  

(Optional) Use **CloudFront** for HTTPS + global performance


## 🔁 Lifecycle Policies (Cost Optimization)

Go to: **Management → Lifecycle rules**

Example Rules:
- After **30 days** → Move to **Standard-IA**
- After **90 days** → Move to **Glacier**

  ---

## Thank You

## 🔗 Connect With Me
| 🌐 Platform                  | 🔗 Link                                              |
| ---------------------------- | ---------------------------------------------------- |
| 🐙 **GitHub**                | [https://lnkd.in/d2F3JPa3](https://lnkd.in/d2F3JPa3) |
| ✍️ **Dev.to Blog**           | [https://lnkd.in/dNtgqAME](https://lnkd.in/dNtgqAME) |
| 💼 **LinkedIn**              | [https://lnkd.in/d3NctxFT](https://lnkd.in/d3NctxFT) |

## 🔖 Hashtags
#AWS #DevOps #CloudComputing #AWSLearning #EBS #VolumeMounting #DataPersistence #LearningJourney #CareerGrowth #DevOpsEngineer #AWSCommunity

