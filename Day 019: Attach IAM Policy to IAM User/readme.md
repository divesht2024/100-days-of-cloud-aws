# 🚀 Day 019 – Attach an IAM Policy to an IAM User

## 📖 Overview

Today, I learned how to attach an **AWS IAM Policy** to an **IAM User**. IAM policies define what actions a user is allowed or denied to perform on AWS resources. By attaching the appropriate policy, administrators can grant users only the permissions required for their responsibilities.

This practice follows the **Principle of Least Privilege**, helping improve the security of AWS environments.

---

## 🎯 Objective

* Understand IAM Policies and User Permissions.
* Attach an existing IAM Policy to an IAM User.
* Verify effective permissions.
* Learn AWS access management best practices.

---

## 🛠️ Environment

| Component      | Details                                  |
| -------------- | ---------------------------------------- |
| Cloud Provider | AWS                                      |
| Service        | AWS Identity and Access Management (IAM) |
| Feature        | IAM User Policy Attachment               |
| Platform       | AWS Management Console                   |
| Category       | Security & Identity Management           |

---

## 📌 Task

Attach an existing IAM policy to an IAM user.

---

## 💻 Steps Performed

### 1️⃣ Open AWS Console

Sign in to the AWS Management Console and navigate to:

```text
IAM → Users
```

---

### 2️⃣ Select the IAM User

Choose the user that requires additional permissions.

Example:

```text
devops-user
```

---

### 3️⃣ Add Permissions

Open the **Permissions** tab.

Click:

```text
Add permissions
```

Choose:

```text
Attach policies directly
```

---

### 4️⃣ Select IAM Policy

Search for and select the required policy.

Example:

```text
AmazonEC2ReadOnlyAccess
```

or a custom customer-managed policy.

---

### 5️⃣ Review and Save

Click:

```text
Next
```

Review the configuration and click:

```text
Add permissions
```

---

### 6️⃣ Verify Permissions

Navigate back to:

```text
IAM → Users → Permissions
```

Verify that the attached policy appears under the user's permissions.

---

## 📚 Concepts Learned

### What is an IAM Policy?

An IAM Policy is a JSON document that defines permissions for AWS resources and actions.

Policies determine:

* Allowed actions
* Denied actions
* AWS resources
* Optional conditions

---

### Ways to Assign Permissions

AWS supports assigning permissions through:

* IAM User
* IAM Group
* IAM Role

Using IAM Groups is generally preferred when multiple users require the same permissions.

---

### AWS Managed vs Customer Managed Policies

| AWS Managed                   | Customer Managed                         |
| ----------------------------- | ---------------------------------------- |
| Created and maintained by AWS | Created and managed by your organization |
| Suitable for common use cases | Supports custom permission requirements  |

---

## 🌍 Real-World Use Case

A Cloud Support Engineer needs read-only access to Amazon EC2 resources for monitoring and troubleshooting.

Instead of granting full administrative permissions, the administrator attaches the **AmazonEC2ReadOnlyAccess** policy to the user's IAM account.

This allows the engineer to view EC2 resources without making changes.

---

## 🔍 Verification

Verify that:

* The policy is attached successfully.
* The IAM user can perform the allowed actions.
* Restricted actions remain inaccessible.

---

## 🔐 Best Practices

* Follow the Principle of Least Privilege.
* Prefer IAM Groups for teams with similar responsibilities.
* Review attached policies regularly.
* Remove unused permissions.
* Enable Multi-Factor Authentication (MFA) for IAM users.

---

## 🧠 Key Takeaways

* Learned how to attach IAM policies to users.
* Understood permission inheritance and access control.
* Improved AWS identity and access management skills.
* Applied security best practices for AWS environments.
* Practiced user permission management.

---

## 🚀 Skills Practiced

* AWS IAM
* IAM Users
* IAM Policies
* Identity & Access Management
* AWS Security
* Access Control

---


## 💡 Interview Questions

### Q1. What is an IAM Policy?

An IAM Policy is a JSON document that defines permissions for AWS resources.

---

### Q2. Can multiple policies be attached to a single IAM user?

Yes. An IAM user can have multiple managed policies attached.

---

### Q3. What is the Principle of Least Privilege?

It is the practice of granting only the minimum permissions required to perform a task.

---

### Q4. Which is preferred: attaching policies directly to users or using groups?

Using IAM Groups is generally preferred because it simplifies permission management for multiple users.

---

### Q5. How can you verify whether a user has the required permissions?

Review the user's attached policies in the IAM console or use the IAM Policy Simulator to evaluate effective permissions.

---

## 📌 Resources

* AWS IAM Documentation
* IAM Policy Reference
* AWS IAM Best Practices
* AWS Security Best Practices

---

## ⭐ Day 019 Summary

Today's hands-on exercise focused on attaching an **IAM Policy** to an **IAM User**. I learned how AWS permissions are granted through policies, how to verify user access, and why following the Principle of Least Privilege is essential for securing cloud environments.
