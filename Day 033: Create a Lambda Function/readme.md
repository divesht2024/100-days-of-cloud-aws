
# 🚀 Day 033 – Create an AWS Lambda Function

## 📖 Overview

Today, I learned how to create and deploy an **AWS Lambda** function. AWS Lambda is a serverless compute service that allows developers to run code without provisioning or managing servers. It automatically scales based on incoming requests and charges only for the compute time consumed.

This hands-on exercise strengthened my understanding of serverless architecture, Lambda functions, IAM execution roles, event-driven computing, and CloudWatch logging.

---

# 🎯 Objective

* Create an AWS Lambda function.
* Configure an IAM execution role.
* Write and deploy Lambda code.
* Test the function using a sample event.
* Monitor execution logs in Amazon CloudWatch.

---

# 🛠️ Environment

| Component      | Details                |
| -------------- | ---------------------- |
| Cloud Provider | AWS                    |
| Service        | AWS Lambda             |
| Runtime        | Python 3.x             |
| Trigger        | Manual Test Event      |
| Monitoring     | Amazon CloudWatch Logs |
| Category       | Serverless Computing   |

---

# 📌 Task

Create an AWS Lambda function that returns a simple JSON response, execute it using a test event, and verify the execution using CloudWatch Logs.

---

# 🏗️ Architecture

```text id="lam001"
           Test Event
                │
                ▼
        AWS Lambda Function
                │
       Executes Python Code
                │
                ▼
        JSON Response Returned
                │
                ▼
      Amazon CloudWatch Logs
```

---

# 💻 Steps Performed

## 1️⃣ Open AWS Lambda Console

Navigate to:

```text id="lam002"
AWS Console → Lambda
```

Click **Create Function**.

---

## 2️⃣ Create the Lambda Function

Configuration:

| Setting       | Value                       |
| ------------- | --------------------------- |
| Function Name | hello-lambda                |
| Runtime       | Python 3.x                  |
| Architecture  | x86_64                      |
| Permissions   | Create a new execution role |

Click **Create Function**.

---

## 3️⃣ Write the Lambda Function

Replace the default code with:

```python id="lam003"
import json

def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": json.dumps({
            "message": "Hello from AWS Lambda!"
        })
    }
```

Click **Deploy**.

---

## 4️⃣ Create a Test Event

Click:

```text id="lam004"
Test → Create New Test Event
```

Example event:

```json id="lam005"
{
  "name": "DevOps"
}
```

Save the test event.

---

## 5️⃣ Execute the Function

Click **Test**.

Example response:

```json id="lam006"
{
  "statusCode": 200,
  "body": "{\"message\":\"Hello from AWS Lambda!\"}"
}
```

Execution status:

```text id="lam007"
Execution succeeded
```

---

## 6️⃣ View CloudWatch Logs

Navigate to:

```text id="lam008"
AWS Console
→ CloudWatch
→ Log Groups
→ /aws/lambda/hello-lambda
```

Review the execution logs for request IDs, duration, billed duration, memory usage, and any errors.

---

## 7️⃣ Modify the Function (Optional)

Example of returning the input event:

```python id="lam009"
import json

def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": json.dumps({
            "received": event
        })
    }
```

Deploy and test again.

---

# 📚 Concepts Learned

## What is AWS Lambda?

AWS Lambda is a **serverless compute service** that executes code in response to events. AWS automatically manages the infrastructure, scaling, and availability.

---

## Benefits of AWS Lambda

* No server management
* Automatic scaling
* Pay only for execution time
* Supports multiple programming languages
* Integrates with many AWS services

---

## Lambda Execution Flow

```text id="lam010"
Event
   │
   ▼
AWS Lambda
   │
Runs Code
   │
Returns Response
   │
CloudWatch Logs
```

---

# 🌍 Real-World Use Cases

AWS Lambda is commonly used for:

* Image processing after S3 uploads
* Backend APIs with Amazon API Gateway
* Scheduled jobs using Amazon EventBridge
* Log processing
* Infrastructure automation
* File validation
* Serverless web applications

---

# 🔍 Verification

Verify:

✅ Lambda function created successfully.
✅ Code deployed successfully.
✅ Test event executed successfully.
✅ JSON response returned.
✅ CloudWatch logs generated.

Useful checks:

* Function status: **Active**
* Test execution: **Succeeded**
* Log group created in CloudWatch
* No execution errors

---

# 🔐 Best Practices

* Follow the principle of least privilege for IAM execution roles.
* Keep functions small and focused on a single responsibility.
* Use environment variables for configuration.
* Monitor execution with CloudWatch Logs and metrics.
* Set appropriate memory and timeout values.
* Handle exceptions gracefully.
* Remove unused Lambda versions and functions.

---

# 🧠 Key Takeaways

* Created and deployed an AWS Lambda function.
* Configured an IAM execution role.
* Executed the function using a test event.
* Viewed execution logs in CloudWatch.
* Learned the basics of serverless computing.

---

# 🚀 Skills Practiced

* AWS Lambda
* Serverless Computing
* Python
* IAM Roles
* CloudWatch Logs
* Event-Driven Architecture
---

# 💡 Interview Questions

### Q1. What is AWS Lambda?

AWS Lambda is a serverless compute service that runs code in response to events without requiring users to manage servers.

---

### Q2. What is an execution role in Lambda?

An execution role is an IAM role assumed by the Lambda function that grants permissions to access AWS services such as S3, DynamoDB, or CloudWatch Logs.

---

### Q3. What triggers can invoke a Lambda function?

Common triggers include:

* Amazon S3
* Amazon API Gateway
* Amazon EventBridge (CloudWatch Events)
* Amazon SNS
* Amazon SQS
* Amazon DynamoDB Streams
* Manual test events

---

### Q4. Where are Lambda execution logs stored?

Execution logs are automatically stored in **Amazon CloudWatch Logs**, provided the execution role has the required permissions.

---

### Q5. What are the advantages of AWS Lambda?

* No server management
* Automatic scaling
* Pay-per-use pricing
* High availability
* Seamless integration with AWS services
* Ideal for event-driven applications

---

# 📌 Resources

* AWS Lambda Documentation
* AWS Serverless Application Model (SAM)
* Amazon CloudWatch Documentation
* AWS Well-Architected Framework
* Python Documentation

---

# ⭐ Day 033 Summary

Today's hands-on exercise focused on **creating and deploying an AWS Lambda function**. I configured an execution role, wrote and deployed Python code, executed the function using a test event, and reviewed execution logs in CloudWatch. This exercise introduced the fundamentals of serverless computing and demonstrated how AWS Lambda enables scalable, event-driven applications without managing infrastructure.
