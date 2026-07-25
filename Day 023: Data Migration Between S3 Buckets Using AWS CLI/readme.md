# 🚀 Day 023 – Data Migration Between S3 Buckets Using AWS CLI

## 📖 Overview

Today, I learned how to migrate data between **Amazon S3 buckets** using the **AWS Command Line Interface (AWS CLI)**. This is a common DevOps and Cloud Engineering task used for backups, data migration, disaster recovery, and moving application assets across environments.

This hands-on exercise improved my understanding of AWS CLI commands, S3 object management, and secure data transfer between buckets.

---

# 🎯 Objective

* Understand Amazon S3 data migration.
* Install and configure AWS CLI.
* Copy data between S3 buckets.
* Verify successful migration.
* Learn real-world migration use cases.

---

# 🛠️ Environment

| Component      | Details                  |
| -------------- | ------------------------ |
| Cloud Provider | AWS                      |
| Service        | Amazon S3                |
| Tool           | AWS CLI                  |
| Category       | Storage & Data Migration |
| Authentication | IAM User / IAM Role      |

---

# 📌 Task

Migrate files from one Amazon S3 bucket to another using AWS CLI while preserving the object structure.

---

# 💻 Steps Performed

## 1️⃣ Configure AWS CLI

Verify AWS CLI installation:

```bash
aws --version
```

Configure credentials:

```bash
aws configure
```

Provide:

```text
AWS Access Key ID
AWS Secret Access Key
Default Region
Output Format (json)
```

---

## 2️⃣ Verify Source Bucket

List buckets:

```bash
aws s3 ls
```

View objects inside the source bucket:

```bash
aws s3 ls s3://source-bucket
```

---

## 3️⃣ Copy Data Between Buckets

Copy all objects recursively:

```bash
aws s3 cp s3://source-bucket s3://destination-bucket --recursive
```

---

## 4️⃣ Alternative Method (Sync)

Synchronize both buckets:

```bash
aws s3 sync s3://source-bucket s3://destination-bucket
```

`sync` copies only new or modified files, making it efficient for recurring migrations.

---

## 5️⃣ Verify Migration

List files in the destination bucket:

```bash
aws s3 ls s3://destination-bucket
```

Compare object counts if needed:

```bash
aws s3 ls s3://destination-bucket --recursive
```

---

# 📚 Concepts Learned

## What is Amazon S3?

Amazon S3 (Simple Storage Service) is AWS's highly durable and scalable object storage service used to store files, backups, logs, media, and application assets.

---

## What is AWS CLI?

AWS CLI is a command-line tool that enables users to interact with AWS services directly from the terminal.

Example:

```bash
aws s3 ls
```

---

## `cp` vs `sync`

| `aws s3 cp`                  | `aws s3 sync`                        |
| ---------------------------- | ------------------------------------ |
| Copies files                 | Synchronizes folders                 |
| Can overwrite existing files | Copies only changed or missing files |
| Good for one-time migrations | Ideal for recurring synchronization  |

---

## Common AWS CLI S3 Commands

List buckets:

```bash
aws s3 ls
```

Upload a file:

```bash
aws s3 cp file.txt s3://my-bucket/
```

Download a file:

```bash
aws s3 cp s3://my-bucket/file.txt .
```

Delete a file:

```bash
aws s3 rm s3://my-bucket/file.txt
```

---

# 🌍 Real-World Use Case

A company is migrating an application from one AWS account to another.

Before deployment:

* Static website files
* Backup archives
* Application logs
* Images and documents

are migrated from the old S3 bucket to a new bucket using the AWS CLI.

---

# 🔍 Verification

Verify that:

* AWS CLI is configured correctly.
* Source bucket is accessible.
* Files are copied successfully.
* Destination bucket contains all required objects.
* Object structure is preserved.

---

# 🔐 Best Practices

* Grant only required IAM permissions.
* Use IAM Roles instead of long-term credentials when possible.
* Verify bucket names before migration.
* Use `sync` for incremental updates.
* Enable S3 Versioning for important data.
* Encrypt sensitive data using SSE-S3 or SSE-KMS.

---

# 🧠 Key Takeaways

* Learned S3 bucket management using AWS CLI.
* Performed data migration between S3 buckets.
* Understood the difference between `cp` and `sync`.
* Verified migration using AWS CLI commands.
* Improved cloud storage management skills.

---

# 🚀 Skills Practiced

* Amazon S3
* AWS CLI
* Data Migration
* Object Storage
* IAM Permissions
* Cloud Operations

---

# 💡 Interview Questions

### Q1. What is the difference between `aws s3 cp` and `aws s3 sync`?

`cp` copies files regardless of changes, while `sync` copies only new or modified files, making it more efficient for repeated synchronization.

---

### Q2. Which command copies an entire S3 bucket?

```bash
aws s3 cp s3://source-bucket s3://destination-bucket --recursive
```

---

### Q3. Why use AWS CLI for S3 operations?

AWS CLI enables automation, scripting, bulk operations, and faster management of AWS resources.

---

### Q4. What IAM permissions are required for bucket-to-bucket migration?

At minimum:

* `s3:ListBucket`
* `s3:GetObject`
* `s3:PutObject`

---

### Q5. How do you verify that migration completed successfully?

Use:

```bash
aws s3 ls s3://destination-bucket --recursive
```

and compare the files with the source bucket.

---

# 📌 Resources

* AWS CLI Documentation
* Amazon S3 Documentation
* AWS IAM Documentation
* AWS Storage Best Practices

---

# ⭐ Day 023 Summary

Today's hands-on exercise focused on migrating data between **Amazon S3 buckets using the AWS CLI**. I learned how to configure the AWS CLI, copy and synchronize S3 objects, verify successful migrations, and apply best practices for secure and efficient cloud storage management. This is a valuable skill for backup strategies, cloud migrations, disaster recovery, and DevOps automation.
