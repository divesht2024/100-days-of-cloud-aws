# 🚀 Day 005 – Create Amazon EBS GP3 Volume

## 📖 Overview

Today, I learned about **Amazon Elastic Block Store (EBS)** and how to create a **General Purpose SSD (gp3) volume**. Amazon EBS provides persistent block storage for Amazon EC2 instances, making it ideal for operating systems, databases, applications, and file storage.

The **gp3 volume type** is the latest generation of General Purpose SSD storage, offering better performance, flexibility, and lower cost compared to the older gp2 volumes.

---

## 🎯 Objective

- Understand what Amazon EBS is.
- Learn about the GP3 volume type.
- Create a GP3 EBS volume.
- Understand Availability Zone requirements.
- Learn real-world use cases and best practices.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Cloud Provider | AWS |
| Service | Amazon Elastic Block Store (EBS) |
| Volume Type | General Purpose SSD (gp3) |
| Platform | AWS Management Console |

---

## 📌 Task

Create a **GP3 EBS volume** in the desired Availability Zone so it can later be attached to an EC2 instance for persistent storage.

---

## 💻 Steps Performed

1. Open the AWS Management Console.
2. Navigate to **Amazon EC2**.
3. Select **Elastic Block Store → Volumes**.
4. Click **Create Volume**.
5. Configure:
   - Volume Type: **gp3**
   - Size (GiB)
   - Availability Zone
6. Click **Create Volume**.
7. Verify the volume is successfully created.

---

## 📚 Concepts Learned

### What is Amazon EBS?

Amazon Elastic Block Store (EBS) is a **block-level storage service** designed for use with Amazon EC2 instances.

Unlike Amazon S3, which stores objects, EBS stores data in blocks similar to a traditional hard disk or SSD.

EBS volumes remain available even if the EC2 instance is stopped, making them suitable for persistent storage.

---

### What is a GP3 Volume?

GP3 (**General Purpose SSD**) is the latest generation of SSD-backed EBS storage.

It provides:

- High performance
- Low latency
- Independent configuration of storage, IOPS, and throughput
- Better price-performance than GP2

GP3 is the recommended default choice for most workloads.

---

### EBS Volume Lifecycle

```
Create Volume
      ↓
Attach to EC2 Instance
      ↓
Format the Volume
      ↓
Mount the File System
      ↓
Store Data
      ↓
Detach (Optional)
      ↓
Delete (When No Longer Needed)
```

---

### Availability Zone Requirement

An EBS volume **must be created in the same Availability Zone as the EC2 instance** it will be attached to.

Example:

```
EC2 Instance
Region: ap-south-1
Availability Zone: ap-south-1a

↓

EBS Volume

Must also be created in:

ap-south-1a
```

Volumes cannot be directly attached across different Availability Zones.

---

### Difference Between EBS and Instance Store

| Amazon EBS | Instance Store |
|------------|----------------|
| Persistent storage | Temporary storage |
| Data survives instance stop/start | Data is lost when the instance stops or terminates |
| Can be detached and attached to another instance | Cannot be detached |
| Supports snapshots | No snapshot support |

---

## 🌍 Real-World Use Case

Imagine a company hosts a MySQL database on an EC2 instance.

The database files are stored on an **EBS GP3 volume** instead of the instance's temporary storage.

If the EC2 instance is stopped or restarted, the EBS volume remains intact, ensuring that the database and its data persist. Additionally, regular EBS snapshots can be taken for backup and disaster recovery.

---

## 🔍 Verification

After creating the volume:

- Verify the volume appears in the **EBS Volumes** dashboard.
- Confirm the volume type is **gp3**.
- Check the volume size.
- Verify the Availability Zone.
- Ensure the volume status is **Available**.

---

## 🔐 Best Practices

- Use GP3 for general-purpose workloads.
- Create volumes in the same Availability Zone as the EC2 instance.
- Encrypt EBS volumes to protect sensitive data.
- Take regular snapshots for backup and recovery.
- Delete unused volumes to avoid unnecessary costs.
- Monitor storage usage using Amazon CloudWatch.

---

## 🧠 Key Takeaways

- Learned what Amazon EBS is.
- Understood the purpose of GP3 volumes.
- Learned how to create an EBS volume.
- Understood why Availability Zones matter when attaching EBS volumes.
- Learned the difference between persistent and temporary storage.
- Understood the importance of EBS snapshots for backups.

---

## 🚀 Skills Practiced

- Amazon EC2
- Amazon EBS
- GP3 Storage
- Cloud Storage
- Persistent Storage
- AWS Console Navigation
- Storage Management

---



## 📖 Key Terms

| Term | Description |
|------|-------------|
| Amazon EBS | Persistent block storage for EC2 instances |
| GP3 | General Purpose SSD volume type |
| Volume | A virtual storage disk attached to an EC2 instance |
| Snapshot | A backup of an EBS volume stored in Amazon S3 |
| Availability Zone | A physical data center where AWS resources are deployed |

---

## 💡 Interview Questions

### Q1. What is Amazon EBS?

Amazon Elastic Block Store (EBS) is a persistent block storage service designed for use with Amazon EC2 instances.

---

### Q2. What is a GP3 volume?

GP3 is the latest generation of General Purpose SSD-backed EBS storage that offers configurable performance, lower cost, and better flexibility than GP2.

---

### Q3. Can an EBS volume be attached to an EC2 instance in another Availability Zone?

No. An EBS volume can only be attached to EC2 instances within the **same Availability Zone**.

---

### Q4. What is the difference between Amazon EBS and Amazon S3?

| Amazon EBS | Amazon S3 |
|------------|-----------|
| Block storage | Object storage |
| Attached to EC2 instances | Accessible via APIs |
| Suitable for operating systems and databases | Suitable for backups, logs, images, videos, and static files |

---

### Q5. Does data remain after stopping an EC2 instance?

Yes. Data stored on an EBS volume persists even if the EC2 instance is stopped or restarted.

---

## 📌 Resources

- AWS Amazon EBS Documentation
- AWS EC2 User Guide
- AWS Storage Best Practices
- AWS Well-Architected Framework

---

## ⭐ Day 005 Summary

Today's hands-on exercise introduced me to **Amazon Elastic Block Store (EBS)** and the **GP3 SSD volume type**. I learned how to create persistent block storage, understood the importance of selecting the correct Availability Zone, and explored why GP3 is the recommended storage option for most workloads. This knowledge is essential for deploying reliable applications, databases, and production workloads on AWS.
