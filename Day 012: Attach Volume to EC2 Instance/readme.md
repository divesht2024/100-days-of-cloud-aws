# 🚀 Day 012 – Attach EBS Volume to an EC2 Instance

## 📖 Overview

Today, I learned how to attach an **Amazon Elastic Block Store (EBS) Volume** to an Amazon EC2 instance. EBS provides persistent block-level storage that can be attached to EC2 instances and used for storing application data, databases, logs, and other important files.

In this hands-on exercise, I created and attached an EBS volume to an EC2 instance and learned how AWS manages additional storage resources.

---

## 🎯 Objective

* Understand Amazon EBS volumes.
* Create an EBS volume.
* Attach the volume to an EC2 instance.
* Identify the attached disk inside Linux.
* Understand storage management in AWS.
* Learn real-world use cases of additional storage.

---

## 🛠️ Environment

| Component       | Details                   |
| --------------- | ------------------------- |
| Cloud Provider  | AWS                       |
| Service         | Amazon EC2                |
| Storage Service | Amazon EBS                |
| Volume Type     | General Purpose SSD (gp3) |
| Platform        | AWS Management Console    |
| Category        | Storage                   |

---

## 📌 Task

Attach an existing EBS volume to an EC2 instance.

---

## 💻 Steps Performed

### 1. Open AWS EC2 Dashboard

* Login to AWS Management Console.
* Navigate to **EC2 → Elastic Block Store → Volumes**.

---

### 2. Select the EBS Volume

* Select the required volume.
* Click:

```
Actions → Attach Volume
```

---

### 3. Attach Volume to EC2 Instance

* Select the target EC2 instance.
* Specify the device name.

Example:

```
/dev/sdf
```

* Click **Attach Volume**.

---

### 4. Verify Volume Attachment

Connect to the EC2 instance:

```bash
ssh -i key.pem ec2-user@<public-ip>
```

Check available disks:

```bash
lsblk
```

Example output:

```text
NAME
xvda
xvdf
```

---

## 📚 Concepts Learned

## What is Amazon EBS?

Amazon Elastic Block Store (EBS) is a durable block storage service designed for EC2 instances.

It provides:

* Persistent storage
* High availability
* Low latency
* Backup through snapshots

---

## What is an EBS Volume?

An EBS volume is like a virtual hard disk attached to an EC2 instance.

It can store:

* Application files
* Database files
* Logs
* Operating system data

---

## EBS vs Instance Store

| EBS Volume                        | Instance Store                |
| --------------------------------- | ----------------------------- |
| Persistent storage                | Temporary storage             |
| Data survives instance stop/start | Data lost after instance stop |
| Can create snapshots              | No snapshots                  |
| Network-attached storage          | Physically attached           |

---

## How EBS Attachment Works

```text
AWS Cloud

EC2 Instance
      |
      |
      ↓
EBS Volume
      |
      |
      ↓
Linux Device
/dev/xvdf
```

---

## 🌍 Real-World Use Case

A company runs a production application on an EC2 instance.

Initially:

* OS uses the root volume.
* Application data grows over time.

Instead of creating a new server, the DevOps engineer:

* Creates a new EBS volume.
* Attaches it to the instance.
* Mounts it as additional storage.

This allows the application to scale storage without downtime.

---

## 🔍 Verification

Check attached disks:

```bash
lsblk
```

Check disk information:

```bash
sudo fdisk -l
```

Check mounted storage:

```bash
df -h
```

---

## 🔐 Best Practices

* Take EBS snapshots before major changes.
* Choose the correct volume type based on workload.
* Encrypt sensitive EBS volumes.
* Monitor disk usage using CloudWatch.
* Delete unused volumes to avoid unnecessary costs.
* Use meaningful tags for storage resources.

---

## 🧠 Key Takeaways

* Learned how to attach an EBS volume to EC2.
* Understood persistent block storage in AWS.
* Learned how Linux identifies attached disks.
* Practiced AWS storage management.
* Understood how additional storage supports production workloads.

---

## 🚀 Skills Practiced

* Amazon EC2
* Amazon EBS
* AWS Storage
* Linux Disk Management
* Cloud Infrastructure Management
* AWS Console Navigation

---


## 💡 Interview Questions

### Q1. What is Amazon EBS?

Amazon EBS is a block-level storage service that provides persistent storage for EC2 instances.

---

### Q2. Does EBS data survive EC2 restart?

Yes. EBS volumes are persistent and survive instance stop/start operations.

---

### Q3. Can one EBS volume attach to multiple EC2 instances?

Generally, one EBS volume can be attached to one EC2 instance at a time (except specific Multi-Attach supported volumes).

---

### Q4. How do you check attached disks in Linux?

Using:

```bash
lsblk
```

---

### Q5. What is an EBS snapshot?

An EBS snapshot is a backup of an EBS volume stored in Amazon S3.

---

## 📌 Resources

* AWS EC2 Documentation
* AWS EBS Documentation
* AWS Storage Best Practices
* Linux Disk Management Documentation

---

## ⭐ Day 012 Summary

Today's hands-on exercise introduced me to **Amazon EBS storage management**. I learned how to attach an EBS volume to an EC2 instance, verify the attached disk in Linux, and understand how persistent storage is used in real-world cloud environments. This knowledge is essential for managing scalable and reliable AWS infrastructure.
