# **AWS S3 (Simple Storage Service)**

**Amazon S3 (Simple Storage Service)** is an object storage service that allows you to store, retrieve, and manage any amount of data from anywhere on the internet.  
It is designed for scalability, durability, and high availability — making it ideal for IoT data storage, backups, and static website hosting.

---

### **Key Features**

- **Scalability:** Automatically scales to store unlimited data.  
- **Durability:** Designed for 99.999999999% (11 nines) durability.  
- **Availability:** Provides up to 99.99% uptime depending on storage class.  
- **Security:** Supports encryption, IAM roles, and bucket policies.  
- **Multiple Storage Classes:** Standard, Intelligent-Tiering, Glacier, Deep Archive, etc.  
- **Lifecycle Policies:** Automate data movement between storage classes.  
- **Versioning:** Maintain multiple versions of objects.  
- **Event Notifications:** Trigger AWS Lambda or SNS when files change.  

---

### **How It Works**

1. **Create an S3 Bucket** – A container for storing data (e.g., `iot-sensor-data-bucket`).  
2. **Upload Files or IoT Data** – Devices or applications send files or data objects to the bucket.  
3. **Data Access** – Access data through the AWS Console, SDK, or API.  
4. **Optional:** Enable **Static Website Hosting** to serve web content directly from S3.  

---

### **Example: IoT Data Storage Flow**

1. IoT sensors publish data to AWS IoT Core.  
2. IoT Core routes messages to an S3 bucket via a rule.  
3. Each record is stored as a JSON object in the bucket.  
4. Data can be used later for analytics using **AWS QuickSight**, **Athena**, or **Python pandas**.  

---

### **Hands-on Example**

<img width="1008" height="356" alt="image" src="https://github.com/user-attachments/assets/0e691754-80f1-4f88-884e-b183f82c79ed" />
<img width="1534" height="508" alt="image" src="https://github.com/user-attachments/assets/1570195e-37e0-463c-9388-85e9a31d466b" />
<img width="1486" height="683" alt="image" src="https://github.com/user-attachments/assets/300eff0f-5c35-4cbe-8a69-76bd09525b05" />
<img width="1668" height="1027" alt="image" src="https://github.com/user-attachments/assets/a63019d9-3cc1-428a-9618-d3c90ef99247" />




## **Author**

Lavanya Pothireddy
B.Tech – Computer Science and Engineering

GitHub: https://github.com/lavanyapothireddy

LinkedIn: www.linkedin.com/in/pothireddy-lavanya-9505b5285
