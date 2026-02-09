## 📅 Day 15 | AWS SNS & SQS — Messaging Services in AWS 🚀 

Today, I learned about AWS SNS (Simple Notification Service) and AWS SQS (Simple Queue Service), which are core messaging services used in AWS & DevOps architectures for communication between applications and services.
These services help in building decoupled, scalable, and reliable systems.
 
# 🔔 AWS SNS & 📦 AWS SQS (DevOps – Point to Point) 

## 🔔 AWS SNS (Simple Notification Service)  
 
### Service Type
- Push-based messaging service

### Main Purpose 
- Used to send notifications and alerts

### Messaging Model
-  Publish / Subscribe (Pub-Sub) 

### Flow


### Delivery
- Message is pushed automatically to subscribers 
   
### Subscribers Can Be  
- Email  
- SMS  
- AWS Lambda   
- HTTP / HTTPS  
- SQS  

### Message Storage
- SNS does **not store messages** 
- If the subscriber is unavailable, the message is lost

### Use in DevOps
- CloudWatch alarms  
- Deployment notifications  
- System failure alerts  

### Scalability
- Fully managed and highly scalable

### Interview One Line
> **SNS is used to send real-time notifications to multiple subscribers.**

---

## 📦 AWS SQS (Simple Queue Service)

### Service Type
- Pull-based message queue service

### Main Purpose
- Used to decouple applications

### Messaging Model
- Queue-based

### Flow


### Message Retrieval
- Consumer polls (pulls) messages from the queue

### Message Storage
- Messages are stored safely until processed

### Visibility Timeout
- Message is hidden while being processed

### Types of Queues
- **Standard Queue**
  - High throughput  
  - At-least-once delivery  

- **FIFO Queue**
  - Ordered processing  
  - Exactly-once delivery  

### Use in DevOps
- Background jobs  
- Auto Scaling workloads  
- CI/CD task handling  

### Interview One Line
> **SQS is used to store messages and process them asynchronously.**

---

## 🔄 SNS vs SQS – Point to Point Difference

| Feature | SNS | SQS |
|------|----|----|
| Message Type | Push | Pull |
| Purpose | Send notifications | Store & process messages |
| Consumers | Multiple subscribers | One consumer per message |
| Storage | No | Yes |
| Use Case | Alerts & notifications | Task & job processing |

---

## 🔁 SNS + SQS Together (DevOps Use Case)

- Application sends message to SNS  
- SNS topic fans out the message  
- Multiple SQS queues receive the message  
- Each service processes independently  

👉 Used in **Microservices Architecture & CI/CD Pipelines**

---

## ⭐ Final Interview Line
> **SNS is for sending messages, SQS is for queuing messages until they are processed.**

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

