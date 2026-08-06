
# 🚀 Day 032 – Snapshot and Restoration of an Amazon RDS Instance

## 📖 Overview

Today, I learned how to create a **manual snapshot** of an Amazon RDS instance and restore a new database instance from that snapshot. Amazon RDS snapshots provide point-in-time backups that can be used for disaster recovery, database migration, testing, and data protection.

This hands-on exercise strengthened my understanding of Amazon RDS backups, snapshots, database restoration, and disaster recovery strategies in AWS.

---

# 🎯 Objective

* Create a manual snapshot of an RDS instance.
* Monitor the snapshot creation process.
* Restore a new RDS instance from the snapshot.
* Verify restored database connectivity.
* Understand RDS backup and recovery concepts.

---

# 🛠️ Environment

| Component        | Details                    |
| ---------------- | -------------------------- |
| Cloud Provider   | AWS                        |
| Database Service | Amazon RDS                 |
| Database Engine  | MySQL (Example)            |
| Backup Type      | Manual Snapshot            |
| Category         | Backup & Disaster Recovery |

---

# 📌 Task

Create a manual snapshot of an existing Amazon RDS instance, restore a new RDS instance from the snapshot, and verify that the restored database is operational.

---

# 🏗️ Architecture

```text id="rds101"
              Amazon RDS
            (Source Database)
                    |
            Create Snapshot
                    |
           Manual RDS Snapshot
                    |
        Restore New RDS Instance
                    |
          Restored Database
                    |
           Application / EC2
```

---

# 💻 Steps Performed

## 1️⃣ Open Amazon RDS Console

Navigate to:

```text id="rds102"
AWS Console → Amazon RDS → Databases
```

Select the existing database instance.

---

## 2️⃣ Create a Manual Snapshot

Choose:

```text id="rds103"
Actions → Take Snapshot
```

Example configuration:

| Setting             | Value              |
| ------------------- | ------------------ |
| Snapshot Identifier | dev-db-snapshot-01 |

Click **Take Snapshot**.

---

## 3️⃣ Monitor Snapshot Status

Navigate to:

```text id="rds104"
Amazon RDS → Snapshots
```

Wait until the snapshot status changes to:

```text id="rds105"
Available
```

---

## 4️⃣ Restore the Snapshot

Select the snapshot and choose:

```text id="rds106"
Actions → Restore Snapshot
```

Example configuration:

| Setting                | Value                   |
| ---------------------- | ----------------------- |
| DB Instance Identifier | restored-dev-db         |
| Instance Class         | db.t3.micro             |
| VPC                    | Production-VPC          |
| DB Subnet Group        | private-db-subnet-group |
| Public Access          | No                      |
| Security Group         | RDS-SG                  |

Click **Restore DB Instance**.

---

## 5️⃣ Wait for Restoration

Monitor the database status until it becomes:

```text id="rds107"
Available
```

The restored instance receives a **new endpoint**.

---

## 6️⃣ Retrieve the Endpoint

Navigate to:

```text id="rds108"
Amazon RDS → Databases
```

Copy the endpoint of the restored database.

Example:

```text id="rds109"
restored-dev-db.abc123.us-east-1.rds.amazonaws.com
```

---

## 7️⃣ Connect to the Restored Database

From an EC2 instance with network access:

```bash id="rds110"
mysql -h <RDS-ENDPOINT> -u admin -p
```

Example:

```bash id="rds111"
mysql -h restored-dev-db.abc123.us-east-1.rds.amazonaws.com -u admin -p
```

---

## 8️⃣ Verify Data

Display databases:

```sql id="rds112"
SHOW DATABASES;
```

Verify tables:

```sql id="rds113"
SHOW TABLES;
```

Check sample data:

```sql id="rds114"
SELECT * FROM sample_table;
```

The restored database should contain the same data that existed when the snapshot was created.

---

# 📚 Concepts Learned

## What is an RDS Snapshot?

An RDS snapshot is a storage-level backup of an Amazon RDS database that captures its state at a specific point in time.

Snapshots can be used to:

* Restore databases
* Recover from accidental deletion
* Create test environments
* Migrate databases

---

## Types of RDS Backups

### Automated Backups

* Created automatically by AWS
* Retained for the configured backup period
* Support point-in-time recovery

### Manual Snapshots

* Created manually by users
* Retained until deleted
* Can be restored at any time

---

## Snapshot Workflow

```text id="rds115"
Running RDS Instance
         |
         ▼
 Create Manual Snapshot
         |
         ▼
Snapshot Available
         |
         ▼
Restore Snapshot
         |
         ▼
New RDS Instance
```

---

# 🌍 Real-World Use Case

Before performing major database changes such as schema modifications or application upgrades, organizations create manual snapshots. If something goes wrong, they can quickly restore the database to its previous state, minimizing downtime and reducing the risk of data loss.

---

# 🔍 Verification

Verify:

✅ Manual snapshot created successfully.
✅ Snapshot status is **Available**.
✅ Database restored successfully.
✅ New RDS endpoint generated.
✅ Application connects to the restored database.
✅ Data matches the original database.

Useful commands:

```bash id="rds116"
mysql -h <endpoint> -u admin -p
```

```sql id="rds117"
SHOW DATABASES;
```

```sql id="rds118"
SHOW TABLES;
```

```sql id="rds119"
SELECT VERSION();
```

---

# 🔐 Best Practices

* Create manual snapshots before major changes.
* Enable automated backups.
* Store snapshots for disaster recovery.
* Encrypt snapshots using AWS KMS.
* Regularly test snapshot restoration.
* Apply least-privilege IAM permissions for backup and restore operations.
* Delete obsolete snapshots to optimize storage costs.

---

# 🧠 Key Takeaways

* Created a manual Amazon RDS snapshot.
* Restored a new RDS instance from the snapshot.
* Verified successful database connectivity.
* Understood backup and disaster recovery workflows.
* Learned the importance of testing database restoration.

---

# 🚀 Skills Practiced

* Amazon RDS
* Database Backup
* RDS Snapshots
* Disaster Recovery
* Database Restoration
* AWS Management Console

---
# 💡 Interview Questions

### Q1. What is an Amazon RDS snapshot?

An Amazon RDS snapshot is a point-in-time backup of an RDS database instance that can be used to restore the database later.

---

### Q2. What is the difference between automated backups and manual snapshots?

| Automated Backups                | Manual Snapshots                   |
| -------------------------------- | ---------------------------------- |
| Created automatically            | Created manually                   |
| Retained for a configured period | Retained until deleted             |
| Support point-in-time recovery   | Restore only to the snapshot state |

---

### Q3. Does restoring an RDS snapshot overwrite the original database?

No. Restoring a snapshot creates a **new RDS instance**. The original database remains unchanged.

---

### Q4. Can encrypted snapshots be restored?

Yes. Encrypted snapshots can be restored, provided the appropriate AWS KMS key permissions are available.

---

### Q5. Why should organizations regularly test snapshot restoration?

Testing ensures that backups are valid, recovery procedures work as expected, and downtime can be minimized during real disaster recovery scenarios.

---

# 📌 Resources

* AWS Amazon RDS Documentation
* AWS Backup Documentation
* AWS Well-Architected Framework
* MySQL Documentation
* Amazon RDS Best Practices Guide

---

# ⭐ Day 032 Summary

Today's hands-on exercise focused on **creating and restoring Amazon RDS snapshots**. I created a manual snapshot of an existing RDS instance, restored it as a new database instance, verified connectivity, and confirmed that the data was successfully recovered. This exercise reinforced key concepts in backup, disaster recovery, and database resilience, which are essential for production AWS environments.
