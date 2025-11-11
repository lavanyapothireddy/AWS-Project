# **AWS IoT Core, Lambda, and S3 Integration Project**
## **Overview**

This project demonstrates how to build a cloud-based IoT data pipeline using AWS IoT Core, AWS Lambda, and Amazon S3. It shows how IoT devices (such as sensors connected to Arduino or Raspberry Pi) can securely send data to AWS, store it in the cloud, and process it automatically using serverless functions.

The goal of this project is to create a scalable, cost-effective, and automated IoT data management system that works without manual intervention or dedicated servers.

## **Services Used**
### **1. AWS IoT Core**

AWS IoT Core acts as the main communication hub between IoT devices and the cloud.

Devices connect securely using MQTT protocol.

IoT Core authenticates devices with X.509 certificates.

Messages from devices (e.g., temperature, humidity) are published to topics such as sensors/temperature.

The Rules Engine routes data automatically to other AWS services like S3 or Lambda.

### **2. Amazon S3**

Amazon S3 (Simple Storage Service) is used to store IoT data and logs.

It stores sensor readings in a bucket (e.g., iot-data-bucket-demo).

Each message is saved as a JSON file or record for later analysis.

S3 ensures durability (99.999999999%) and high availability.

Optionally, the bucket can be enabled for static website hosting or connected to analytics tools.

### **3. AWS Lambda**

AWS Lambda is a serverless compute service used to automate data processing.

A Lambda function is triggered when a new message arrives or a new file is uploaded to S3.

It analyzes data and sends alerts (for example, when temperature exceeds a set threshold).

It can also process and format data before saving it to S3 or DynamoDB.

## **Project Workflow**

### **1.Device Connectivity:**
IoT devices (e.g., DHT22 temperature sensors) connect securely to AWS IoT Core using certificates.

### **2.Data Publishing:**
Devices publish data to MQTT topics such as sensors/temperature.
{
  "deviceId": "Sensor01",
  "timestamp": "2025-09-18T10:00:00Z",
  "temperature": 33.5
}

### **3.Data Routing (Rules Engine):**
An IoT Core rule filters and routes the data:

SELECT deviceId, timestamp, temperature 
FROM 'sensors/temperature'

→ Sends the data to S3 for storage.

### **4.AWS Lambda Trigger:**
A Lambda function is configured to trigger whenever new data is uploaded or a specific condition is met (e.g., temperature > 35°C).
Example Lambda function in Python:

```
import json
import boto3

iot_client = boto3.client('iot-data', region_name='ap-south-1')

def lambda_handler(event, context):
    temp = event.get("temperature", 0)
    if temp > 35:
        alert_msg = {
            "alert": "High temperature detected!",
            "value": temp,
            "deviceId": event["deviceId"]
        }
        iot_client.publish(
            topic="alerts/temperature",
            qos=1,
            payload=json.dumps(alert_msg)
        )
    return {"status": "processed"}
```





### **5.Data Storage in S3:**
The IoT data is automatically stored in an S3 bucket, which can later be used for visualization or analytics using AWS QuickSight or Python tools.

### **6.Result:**

Data securely transferred and stored.

Lambda automates alert generation.

Entire system runs serverlessly without any manual management.

## **Example Use Cases**

Smart Agriculture: Monitor soil or temperature and trigger irrigation via Lambda.

Smart Home Automation: Track temperature or motion and control devices remotely.

Industrial Monitoring: Detect anomalies in machines through real-time data.

Healthcare IoT: Collect patient vitals and trigger alerts when thresholds are exceeded.

## **Tools and Technologies**

AWS IoT Core

AWS Lambda (Python 3.x)

Amazon S3

MQTT Protocol

Arduino or Raspberry Pi

Python (for data handling)

## **Outcomes**

Successfully built a working prototype that connects IoT devices to AWS Cloud.

Achieved secure communication and automatic data routing.

Automated data processing using Lambda functions.

Stored all sensor data reliably in Amazon S3 for future use.

Demonstrated a real-world, serverless IoT integration system using AWS

## **Author**

Lavanya Pothireddy
B.Tech – Computer Science and Engineering

GitHub: https://github.com/lavanyapothireddy

LinkedIn: www.linkedin.com/in/pothireddy-lavanya-9505b5285
