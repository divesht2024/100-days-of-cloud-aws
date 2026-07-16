# 🚀 Day 016 – Create an IAM User in AWS

## 📖 Overview

Today, I learned how to create an **AWS Identity and Access Management (IAM) User**. IAM allows organizations to securely manage access to AWS resources by creating users, groups, roles, and permissions.

Instead of using the AWS root account for daily operations, AWS recommends creating IAM users with only the permissions they need.

---

## 🎯 Objective

* Understand AWS IAM fundamentals.
* Create an IAM user.
* Assign permissions to the user.
* Configure console access.
* Learn AWS security best practices.

---

## 🛠️ Environment

| Component      | Details                        |
| -------------- | ------------------------------ |
| Cloud Provider | AWS                            |
| Service        | AWS IAM                        |
| Feature        | IAM User                       |
| Platform       | AWS Management Console         |
| Category       | Security & Identity Management |

---

## 📌 Task

Create an IAM user with appropriate permissions and console access.

---

## 💻 Steps Performed

### 1️⃣ Open AWS Console

Login to the AWS Management Console and navigate to:

```text
IAM → Users
```

---

### 2️⃣ Create User

Click:

```text
Create User
```

Provide:

* User Name
* Console Access (Optional)

Example:

```text
Username: devops-user
```

---

### 3️⃣ Set Permissions

Choose one of the following methods:

* Add user to group
* Attach policies directly
* Copy permissions from another user

Example policy:

```text
AmazonEC2ReadOnlyAccess
```

---

### 4️⃣ Review and Create

Review the configuration and click:

```text
Create User
```

---

### 5️⃣ Verify User Creation

Navigate to:

```text
IAM → Users
```

Verify that the new user appears in the list.

---

## 📚 Concepts Learned

### What is IAM?

AWS Identity and Access Management (IAM) is a service used to securely control access to AWS resources.

IAM helps manage:

* Users
* Groups
* Roles
* Policies

---

### What is an IAM User?

An IAM User represents a person or application that needs access to AWS resources.

An IAM user can have:

* Username
* Password
* Access Keys
* Permissions

---

### IAM Components

| Component | Purpose               |
| --------- | --------------------- |
| User      | Individual identity   |
| Group     | Collection of users   |
| Role      | Temporary permissions |
| Policy    | Permission document   |

---

### IAM Policy Example

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "ec2:DescribeInstances",
      "Resource": "*"
    }
  ]
}
```

---

## 🌍 Real-World Use Case

A company has separate teams for:

* Developers
* DevOps Engineers
* Security Team
* Database Administrators

Instead of sharing the root account, each employee receives an IAM user with only the permissions required for their job responsibilities.

---

## 🔍 Verification

Verify:

* IAM user exists.
* Permissions are attached correctly.
* User can sign in successfully.
* Policies are functioning as expected.

---

## 🔐 AWS IAM Best Practices

* Never use the root account for daily tasks.
* Enable MFA for all users.
* Follow the principle of least privilege.
* Use IAM groups instead of assigning permissions individually.
* Rotate access keys regularly.
* Remove unused users and credentials.

---

## 🧠 Key Takeaways

* Learned how to create an IAM user.
* Understood IAM users, groups, roles, and policies.
* Learned AWS security best practices.
* Improved knowledge of identity management in AWS.
* Practiced access management concepts.

---

## 🚀 Skills Practiced

* AWS IAM
* Cloud Security
* Identity Management
* Access Control
* AWS Console Navigation

---
                        

---

## 💡 Interview Questions

### Q1. What is IAM in AWS?

IAM is a service that manages authentication and authorization for AWS resources.

---

### Q2. Why should we avoid using the root account?

The root account has unrestricted access to all AWS resources and should only be used for account-level administrative tasks.

---

### Q3. What is the difference between an IAM User and an IAM Role?

An IAM User represents a permanent identity, while an IAM Role provides temporary permissions.

---

### Q4. What is an IAM Policy?

An IAM Policy is a JSON document that defines permissions for AWS resources and actions.

---

### Q5. What is the Principle of Least Privilege?

Users should only receive the minimum permissions required to perform their tasks.

---

## ⭐ Day 016 Summary

Today's hands-on exercise introduced me to **AWS Identity and Access Management (IAM)**. I learned how to create IAM users, assign permissions, and apply AWS security best practices to manage access securely and efficiently in cloud environments.
