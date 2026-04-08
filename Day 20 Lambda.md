## 📅 Day 20 | AWS Lambda — Serverless Compute in AWS ⚡☁️

Today, I learned about **AWS Lambda**, a **serverless compute service** provided by AWS that lets you run code **without provisioning or managing servers**.

With Lambda, you only focus on **writing code**, and AWS automatically handles **infrastructure, scaling, and availability**. You pay **only for the execution time**, making it highly cost-effective and scalable. 
  
AWS Lambda is a core service in **modern DevOps and cloud-native architectures**.  
      
---    
       
## 🔹 What is AWS Lambda?   

AWS Lambda allows you to run code in response to **events**.

You can use Lambda to:  

* Process files
* Handle API requests
* Automate tasks
* Build serverless backends

**Supported languages:**

* Python
* Node.js
* Java 
* Go
* C#
 
---

## 🔹 Why AWS Lambda is Important in DevOps?

Lambda helps DevOps teams by:

* Eliminating server management
* Automatically scaling applications
* Reducing infrastructure costs
* Integrating easily with CI/CD pipelines
* Enabling event-driven architectures

---

## 🔹 How AWS Lambda Works (Step-by-Step)

1. Developer writes Lambda function code
2. Code is uploaded to AWS Lambda
3. An event triggers the function
   *(S3, API Gateway, SNS, SQS, EventBridge, etc.)*
4. AWS creates an execution environment
5. Lambda runs the function
6. Output is returned
7. Logs & metrics are sent to **CloudWatch**

---

## 🔹 Common Lambda Triggers 

* Amazon S3 – file upload events
* API Gateway – REST & HTTP APIs
* Amazon SNS – notifications
* Amazon SQS – message processing 
* EventBridge – scheduled jobs (cron) 
* DynamoDB Streams – data changes

--- 

## 🔹 AWS Lambda in CI/CD (DevOps Use Case)

Typical flow:

1. Code pushed to GitHub 
2. CI/CD pipeline builds & tests 
3. Lambda function deployed
4. Event triggers Lambda
5. Application executes automatically

---

## 🔹 Real-World Use Cases 

* Serverless APIs
* Image resizing & file processing
* Automation scripts
* Background jobs
* Microservices
* Monitoring & alerts

---

## 🔹 Interview Quick Answers

**What is AWS Lambda?**
A serverless compute service that runs code in response to events.

**Do we manage servers in Lambda?**
No, AWS fully manages the infrastructure.

**How does Lambda scale?**
Automatically scales based on the number of requests.

**How is Lambda billed?**
Based on number of executions and execution time.

---

## 🔹 Summary

AWS Lambda:

* Is serverless and event-driven
* Scales automatically
* Reduces operational overhead
* Fits perfectly into DevOps workflows
---

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tghsrfw0pts8y4dh0c89.png)

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

---

⭐ If you like this post, don’t forget to **react & share** 🙌
