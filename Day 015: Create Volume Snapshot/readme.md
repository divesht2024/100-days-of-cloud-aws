# 🚀 Day 015 – Create an EBS Volume Snapshot

## 📖 Overview

Today, I learned how to create an **Amazon EBS Snapshot**, which is a point-in-time backup of an Amazon EBS volume. Snapshots are stored in Amazon S3 and are commonly used for backup, disaster recovery, migration, and data protection strategies.

Creating snapshots is a critical DevOps and cloud administration skill for ensuring data durability and business continuity.

---

## 🎯 Objective

* Understand Amazon EBS Snapshots.
* Create a snapshot of an EBS volume.
* Learn how snapshots support backup and disaster recovery.
* Understand incremental backup concepts.
* Verify snapshot creation.

---

## 🛠️ Environment

| Component      | Details                |
| -------------- | ---------------------- |
| Cloud Provider | AWS                    |
| Service        | Amazon EBS             |
| Feature        | Snapshot               |
| Platform       | AWS Management Console |
| Category       | Storage & Backup       |

---

## 📌 Task

Create a snapshot of an existing Amazon EBS volume.

---

## 💻 Steps Performed

### 1️⃣ Open AWS Console

* Login to AWS Management Console.
* Navigate to:

```text
EC2 → Elastic Block Store → Volumes
```

---

### 2️⃣ Select the EBS Volume

Choose the EBS volume that needs to be backed up.

---

### 3️⃣ Create Snapshot

Navigate to:

```text
Actions → Create Snapshot
```

Provide:

* Snapshot Name
* Description
* Tags (optional)

Example:

```text
Name: production-volume-backup
Description: Daily backup snapshot
```

Click:

```text
Create Snapshot
```

---

### 4️⃣ Verify Snapshot Creation

Navigate to:

```text
EC2 → Snapshots
```

Wait until the snapshot state changes to:

```text
Completed
```

---

## 📚 Concepts Learned

### What is an EBS Snapshot?

An EBS Snapshot is a point-in-time backup of an EBS volume stored in Amazon S3.

Snapshots can be used to:

* Restore deleted data
* Recover from failures
* Create new EBS volumes
* Migrate data across regions

---

### Snapshot Workflow

```text
EBS Volume
    ↓
Create Snapshot
    ↓
Stored in Amazon S3
    ↓
Restore New Volume if Needed
```

---

### Incremental Snapshots

AWS snapshots are **incremental**.

This means:

* First snapshot copies all data blocks.
* Subsequent snapshots only store changed blocks.

Benefits:

* Lower storage costs
* Faster backup operations
* Efficient storage utilization

---

### Snapshot vs AMI

| Snapshot                      | AMI                            |
| ----------------------------- | ------------------------------ |
| Backup of a single EBS volume | Complete EC2 instance template |
| Used for storage recovery     | Used for server deployment     |
| Stored in Amazon S3           | Uses snapshots internally      |

---

## 🌍 Real-World Use Case

A company hosts its production database on an EC2 instance.

Before:

* OS upgrades
* Application deployments
* Database migrations

The DevOps team creates EBS snapshots to ensure that the system can be restored quickly in case of failure.

---

## 🔍 Verification

Verify snapshot status:

```text
State: Completed
```

Verify source volume information:

* Snapshot ID
* Volume ID
* Size
* Creation Time

---

## 🔐 Best Practices

* Schedule automatic snapshots for production systems.
* Use tags for backup organization.
* Delete obsolete snapshots to reduce costs.
* Encrypt snapshots containing sensitive data.
* Copy important snapshots to another AWS region for disaster recovery.

---

## 🧠 Key Takeaways

* Learned how to create EBS snapshots.
* Understood incremental backup concepts.
* Learned the role of snapshots in disaster recovery.
* Practiced AWS storage management.
* Improved cloud backup knowledge.

---

## 🚀 Skills Practiced

* Amazon EBS
* AWS Backup
* Disaster Recovery
* Cloud Storage
* AWS Console Navigation
* Infrastructure Management

---



## 💡 Interview Questions

### Q1. What is an EBS Snapshot?

An EBS Snapshot is a point-in-time backup of an EBS volume stored in Amazon S3.

---

### Q2. Are EBS snapshots full backups every time?

No. AWS uses incremental snapshots, meaning only changed blocks are stored after the first snapshot.

---

### Q3. Can a new volume be created from a snapshot?

Yes. A new EBS volume can be created from an existing snapshot.

---

### Q4. Where are EBS snapshots stored?

EBS snapshots are stored internally in Amazon S3.

---

### Q5. Why are snapshots important?

Snapshots provide backup, disaster recovery, migration, and rollback capabilities.

---

## 📌 Resources

* AWS EBS Documentation
* AWS Snapshot Documentation
* AWS Backup Best Practices
* AWS Well-Architected Framework

---

## ⭐ Day 015 Summary

Today's hands-on exercise introduced me to **Amazon EBS Snapshots**, a key component of cloud backup and disaster recovery strategies. I learned how to create snapshots, understood incremental backup mechanisms, and explored how snapshots help organizations protect and recover critical data efficiently.
