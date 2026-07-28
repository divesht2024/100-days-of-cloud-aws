

# 🚀 Day 025 – Setting Up an EC2 Instance and CloudWatch Alarm

## 📖 Overview

Today, I learned how to launch an **Amazon EC2 instance** and configure an **Amazon CloudWatch Alarm** to monitor system performance. CloudWatch helps track AWS resources, collect metrics, and automatically trigger alerts when predefined thresholds are reached.

This hands-on exercise improved my understanding of AWS monitoring, EC2 metrics, alarms, notifications, and proactive infrastructure management.

---

# 🎯 Objective

* Launch an EC2 instance.
* Understand EC2 monitoring metrics.
* Configure CloudWatch alarms.
* Monitor CPU utilization.
* Set alarm thresholds.
* Learn proactive cloud monitoring practices.

---

# 🛠️ Environment

| Component          | Details                 |
| ------------------ | ----------------------- |
| Cloud Provider     | AWS                     |
| Compute Service    | Amazon EC2              |
| Monitoring Service | Amazon CloudWatch       |
| Metric             | CPU Utilization         |
| Category           | Monitoring & Operations |

---

# 📌 Task

Create an EC2 instance and configure a CloudWatch alarm that monitors its performance and sends an alert when resource usage crosses a defined threshold.

---

# 💻 Steps Performed

## 1️⃣ Launch an EC2 Instance

Navigate to:

```text id="h2g3pa"
AWS Console → EC2 → Instances → Launch Instance
```

Configure:

* AMI (Amazon Linux / Ubuntu)
* Instance Type
* Key Pair
* Network Settings
* Security Group
* Storage

Launch the instance.

---

## 2️⃣ Verify EC2 Instance Status

Check:

```text id="2o9m3b"
EC2 → Instances
```

Verify:

* Instance State: Running
* Status Checks: 2/2 Passed

---

## 3️⃣ Enable Monitoring

By default, EC2 provides basic monitoring.

For detailed monitoring:

Navigate:

```text id="9t0xqp"
EC2 → Instance → Monitoring → Enable Detailed Monitoring
```

Detailed monitoring provides metrics at a shorter interval.

---

# ☁️ CloudWatch Alarm Configuration

## 4️⃣ Create CloudWatch Alarm

Navigate:

```text id="5k1f3w"
AWS Console → CloudWatch → Alarms → Create Alarm
```

---

## 5️⃣ Select Metric

Choose:

```text id="xw8j7e"
Select Metric → EC2 → Per-Instance Metrics
```

Select:

```text id="l3f6p9"
CPUUtilization
```

---

## 6️⃣ Configure Alarm Condition

Example:

| Setting        | Value        |
| -------------- | ------------ |
| Statistic      | Average      |
| Period         | 5 minutes    |
| Threshold Type | Static       |
| Condition      | Greater than |
| Threshold      | 80%          |

Meaning:

If CPU utilization goes above 80%, trigger the alarm.

---

## 7️⃣ Configure Notification

Create an SNS notification:

Example:

```text id="y6x4mc"
Alarm State → In Alarm
Action → Send notification
```

Select:

* Existing SNS topic
* Or create a new SNS topic

---

## 8️⃣ Name the Alarm

Example:

```text id="n8k1de"
High-CPU-EC2-Alarm
```

Create the alarm.

---

# 🔍 Testing the Alarm

SSH into EC2:

```bash id="5r0m0h"
ssh -i key.pem ec2-user@<EC2-IP>
```

Install stress tool:

Amazon Linux:

```bash id="1x7t2c"
sudo yum install stress -y
```

Generate CPU load:

```bash id="u5f3d1"
stress --cpu 2 --timeout 300
```

Monitor:

```text id="q7k9zz"
CloudWatch → Alarms
```

The alarm changes state:

```text
OK → ALARM
```

---

# 📚 Concepts Learned

## What is Amazon CloudWatch?

Amazon CloudWatch is a monitoring and observability service that collects metrics, logs, and events from AWS resources and applications.

---

## What are CloudWatch Metrics?

Metrics are numerical data points collected over time.

Examples:

| Service | Metric          |
| ------- | --------------- |
| EC2     | CPU Utilization |
| EC2     | Network Traffic |
| EBS     | Disk Operations |
| Lambda  | Invocations     |

---

## What is a CloudWatch Alarm?

A CloudWatch Alarm monitors metrics and performs actions when conditions are met.

Example:

```text
CPU > 80%
      |
      ↓
CloudWatch Alarm
      |
      ↓
SNS Notification
      |
      ↓
Email Alert
```

---

# 🏗️ Architecture Diagram

```text
                User
                 |
                 |
              EC2 Instance
                 |
                 |
        CloudWatch Metrics
                 |
                 |
          CloudWatch Alarm
                 |
                 |
              SNS Topic
                 |
                 |
            Email Alert
```

---

# 🌍 Real-World Use Case

A production application runs on EC2 instances.

A sudden traffic spike increases CPU usage.

CloudWatch:

* Monitors CPU metrics.
* Detects high utilization.
* Sends alerts to engineers.
* Allows teams to take action before application failure.

It can also trigger Auto Scaling actions automatically.

---

# 🔍 Verification

Verify:

✅ EC2 instance is running
✅ CloudWatch metrics are available
✅ Alarm is created successfully
✅ Threshold condition is configured
✅ Notifications are received
✅ Alarm changes state when threshold is exceeded

---

# 🔐 Best Practices

* Create alarms for critical resources.
* Monitor CPU, memory, disk, and network metrics.
* Use SNS for notifications.
* Use Auto Scaling with CloudWatch alarms.
* Review alarm thresholds regularly.
* Avoid unnecessary alert noise.

---

# 🧠 Key Takeaways

* Learned EC2 monitoring using CloudWatch.
* Created CloudWatch alarms.
* Understood metrics and thresholds.
* Configured SNS notifications.
* Improved AWS monitoring and operational skills.

---

# 🚀 Skills Practiced

* Amazon EC2
* Amazon CloudWatch
* CloudWatch Metrics
* CloudWatch Alarms
* SNS Notifications
* AWS Monitoring

---

# 💡 Interview Questions

### Q1. What is Amazon CloudWatch?

CloudWatch is AWS monitoring service used to collect metrics, monitor resources, and trigger automated actions.

---

### Q2. What are EC2 default CloudWatch metrics?

Default EC2 metrics include:

* CPU Utilization
* Network In
* Network Out
* Disk Read Operations
* Disk Write Operations

---

### Q3. What is the difference between Basic and Detailed Monitoring?

| Basic Monitoring   | Detailed Monitoring |
| ------------------ | ------------------- |
| 5-minute intervals | 1-minute intervals  |
| Free               | Additional charges  |
| Default enabled    | Must be enabled     |

---

### Q4. What happens when a CloudWatch Alarm enters ALARM state?

The configured action is executed, such as sending an SNS notification or triggering Auto Scaling.

---

### Q5. Can CloudWatch monitor applications running inside EC2?

Yes. Using the CloudWatch Agent, custom application metrics, logs, and memory/disk usage can be monitored.

---

# 📌 Resources

* AWS CloudWatch Documentation
* Amazon EC2 Documentation
* AWS SNS Documentation
* AWS Monitoring Best Practices

---

# ⭐ Day 025 Summary

Today's hands-on exercise focused on **setting up an EC2 instance with CloudWatch monitoring**. I learned how to configure CloudWatch alarms, monitor EC2 performance metrics, and create proactive alerts using SNS notifications. These skills are essential for DevOps engineers managing reliable and production-ready AWS infrastructure.
