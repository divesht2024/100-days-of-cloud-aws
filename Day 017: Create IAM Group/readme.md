# 🚀 Day 017 – Create an IAM Group in AWS

## 📖 Overview

Today, I learned how to create an **AWS IAM Group** to simplify permission management for multiple IAM users. IAM Groups allow administrators to assign permissions once and automatically apply them to all users within the group.

Using groups is a security best practice and helps organizations manage access at scale.

---

## 🎯 Objective

* Understand IAM Groups in AWS.
* Create an IAM Group.
* Attach IAM policies to the group.
* Add users to the group.
* Learn permission management best practices.

---

## 🛠️ Environment

| Component      | Details                        |
| -------------- | ------------------------------ |
| Cloud Provider | AWS                            |
| Service        | AWS IAM                        |
| Feature        | IAM Group                      |
| Platform       | AWS Management Console         |
| Category       | Security & Identity Management |

---

## 📌 Task

Create an IAM Group and assign permissions to its members.

---

## 💻 Steps Performed

### 1️⃣ Open AWS Console

Navigate to:

```text id="v9h97v"
IAM → User Groups
```

---

### 2️⃣ Create Group

Click:

```text id="eh2z4q"
Create Group
```

Provide the group name:

Example:

```text id="brjlwm"
Developers
```

---

### 3️⃣ Attach Permissions

Select IAM policies based on team responsibilities.

Example:

```text id="cv0tr4"
AmazonEC2ReadOnlyAccess
```

Other examples:

* AmazonS3ReadOnlyAccess
* AmazonRDSReadOnlyAccess
* AdministratorAccess

---

### 4️⃣ Add Users to Group

Select existing IAM users and add them to the group.

Example:

```text id="g8b7qt"
devops-user
developer-user
```

---

### 5️⃣ Verify Group Creation

Navigate to:

```text id="r0q8rt"
IAM → User Groups
```

Verify:

* Group exists
* Policies are attached
* Users are members of the group

---

## 📚 Concepts Learned

### What is an IAM Group?

An IAM Group is a collection of IAM users that share the same permissions.

Instead of assigning permissions individually, administrators assign permissions to the group.

---

### Why Use IAM Groups?

Benefits include:

* Easier permission management
* Reduced administrative overhead
* Consistent access policies
* Improved security

---

### IAM Permission Hierarchy

```text id="32u5vl"
IAM Policy
      ↓
IAM Group
      ↓
IAM Users
```

---

### Example Organization Structure

| Team          | IAM Group  |
| ------------- | ---------- |
| Developers    | Developers |
| DevOps Team   | DevOps     |
| Security Team | Security   |
| Database Team | DBA        |

---

## 🌍 Real-World Use Case

A company hires 20 new developers.

Instead of assigning permissions individually:

* Create a `Developers` group.
* Attach required policies.
* Add all developers to the group.

Every new developer automatically receives the required access permissions.

---

## 🔍 Verification

Verify:

* Group appears in IAM dashboard.
* Policies are attached successfully.
* Users inherit permissions from the group.

---

## 🔐 Best Practices

* Follow the principle of least privilege.
* Assign permissions to groups instead of individual users.
* Use descriptive group names.
* Periodically review group memberships.
* Remove unused users and permissions.

---

## 🧠 Key Takeaways

* Learned how to create IAM Groups.
* Understood permission inheritance.
* Learned centralized access management.
* Improved AWS security knowledge.
* Practiced IAM administration.

---

## 🚀 Skills Practiced

* AWS IAM
* Identity Management
* Access Control
* AWS Security
* Policy Management

---

## 💡 Interview Questions

### Q1. What is an IAM Group?

An IAM Group is a collection of IAM users that share the same permissions.

---

### Q2. Can an IAM Group contain another IAM Group?

No. AWS IAM Groups cannot contain other groups.

---

### Q3. Can a user belong to multiple groups?

Yes. An IAM user can belong to multiple IAM groups.

---

### Q4. Do IAM Groups have credentials?

No. Only IAM users have passwords and access keys.

---

### Q5. Why are IAM Groups preferred over direct user permissions?

IAM Groups simplify management and ensure consistent access policies.

---

## ⭐ Day 017 Summary

Today's hands-on exercise introduced me to **AWS IAM Groups** and centralized permission management. I learned how to create groups, attach policies, and manage user access efficiently while following AWS security best practices.
