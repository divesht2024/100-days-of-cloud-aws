# 🚀 Day 020 – Create an IAM Role for Amazon EC2 with Policy Attachment

## 📖 Overview

Today, I learned how to create an **AWS IAM Role** for an Amazon EC2 instance and attach an IAM policy to it. IAM Roles provide **temporary AWS credentials** to AWS services, eliminating the need to store long-term access keys on EC2 instances.

Using IAM Roles is an AWS security best practice for granting secure access to other AWS services.

---

## 🎯 Objective

* Understand AWS IAM Roles.
* Create an IAM Role for Amazon EC2.
* Attach an IAM policy to the role.
* Learn how EC2 instances use IAM Roles.
* Follow AWS security best practices.

---

## 🛠️ Environment

| Component      | Details                                  |
| -------------- | ---------------------------------------- |
| Cloud Provider | AWS                                      |
| Service        | AWS Identity and Access Management (IAM) |
| Feature        | IAM Role                                 |
| Trusted Entity | Amazon EC2                               |
| Platform       | AWS Management Console                   |
| Category       | Security & Identity Management           |

---

## 📌 Task

Create an IAM Role trusted by Amazon EC2 and attach an IAM policy that grants the required permissions.

---

## 💻 Steps Performed

### 1️⃣ Open AWS Console

Navigate to:

```text
IAM → Roles
```

---

### 2️⃣ Create Role

Click:

```text
Create Role
```

Choose:

```text
Trusted Entity Type: AWS Service
Use Case: EC2
```

Click **Next**.

---

### 3️⃣ Attach Permissions

Search for and select the required IAM policy.

Example:

```text
AmazonS3ReadOnlyAccess
```

(Any required AWS managed or customer-managed policy can be attached depending on the use case.)

Click **Next**.

---

### 4️⃣ Configure Role

Provide:

```text
Role Name: EC2ReadOnlyRole
Description: IAM Role for EC2 with read-only permissions
```

Review the configuration and click:

```text
Create Role
```

---

### 5️⃣ Verify Role

Navigate to:

```text
IAM → Roles
```

Confirm:

* Role exists.
* Trusted entity is **EC2**.
* Policy is attached successfully.

---

## 📚 Concepts Learned

### What is an IAM Role?

An IAM Role is an AWS identity that provides **temporary permissions** to trusted entities such as:

* Amazon EC2
* AWS Lambda
* Amazon ECS
* Cross-account users
* AWS services

Unlike IAM Users, IAM Roles do **not** have:

* Passwords
* Access Keys
* Permanent credentials

---

### IAM User vs IAM Role

| IAM User                           | IAM Role                              |
| ---------------------------------- | ------------------------------------- |
| Permanent identity                 | Temporary identity                    |
| Uses access keys/passwords         | Uses temporary credentials            |
| Represents a person or application | Assumed by AWS services or identities |
| Long-term credentials              | Short-term credentials                |

---

### Why Use IAM Roles with EC2?

Instead of storing AWS Access Keys inside an EC2 instance:

* Create an IAM Role.
* Attach the role to the EC2 instance.
* EC2 automatically receives temporary credentials.

Benefits:

* Improved security
* Automatic credential rotation
* No hardcoded secrets
* Easier permission management

---

## 🌍 Real-World Use Case

A web application running on an EC2 instance needs to upload logs to Amazon S3.

Instead of embedding AWS access keys inside the application, an IAM Role with S3 permissions is attached to the EC2 instance.

The application securely accesses S3 using temporary credentials provided by the IAM Role.

---

## 🔍 Verification

Verify that:

* The IAM Role exists.
* The trusted entity is Amazon EC2.
* The required policy is attached.
* The role can be associated with an EC2 instance.

---

## 🔐 Best Practices

* Use IAM Roles instead of storing access keys on EC2.
* Grant only the minimum permissions required.
* Use AWS managed policies where appropriate.
* Regularly review attached policies.
* Rotate and audit permissions periodically.

---

## 🧠 Key Takeaways

* Learned how to create an IAM Role.
* Understood the difference between IAM Users and IAM Roles.
* Attached IAM policies to roles.
* Improved AWS security knowledge.
* Practiced secure access management for EC2.

---

## 🚀 Skills Practiced

* AWS IAM
* IAM Roles
* EC2 Security
* Policy Management
* Identity & Access Management
* AWS Security Best Practices
---

## 💡 Interview Questions

### Q1. What is an IAM Role?

An IAM Role is an AWS identity that provides temporary permissions to trusted entities without using long-term credentials.

---

### Q2. Why should EC2 instances use IAM Roles instead of access keys?

IAM Roles provide temporary credentials that are automatically rotated, eliminating the need to store permanent access keys on the instance.

---

### Q3. Can an IAM Role be attached to an existing EC2 instance?

Yes. An IAM Role can be attached to both new and existing EC2 instances.

---

### Q4. What is a trusted entity?

A trusted entity is the AWS service or identity that is allowed to assume an IAM Role. For EC2 roles, the trusted entity is **Amazon EC2**.

---

### Q5. What security principle should be followed when creating IAM Roles?

Follow the **Principle of Least Privilege** by granting only the permissions required for the workload.

---

## 📌 Resources

* AWS IAM Documentation
* AWS IAM Roles Documentation
* AWS EC2 IAM Roles Guide
* AWS Security Best Practices

---

## ⭐ Day 020 Summary

Today's hands-on exercise focused on creating an **IAM Role for Amazon EC2** and attaching an IAM policy to it. I learned how IAM Roles provide temporary credentials to AWS services, why they are more secure than access keys, and how they simplify permission management while following AWS security best practices.
