# 🚀 Day 018 – Create a Read-Only IAM Policy for Amazon EC2 Console Access

## 📖 Overview

Today, I learned how to create a **custom AWS IAM policy** that grants **read-only access to Amazon EC2**. IAM policies define what actions a user, group, or role can perform on AWS resources.

By creating a custom read-only policy, users can view EC2 resources such as instances, AMIs, volumes, snapshots, and security groups without being able to modify or delete them.

---

## 🎯 Objective

* Understand AWS IAM Policies.
* Create a custom IAM policy.
* Grant read-only access to Amazon EC2.
* Follow the Principle of Least Privilege.
* Verify policy permissions.

---

## 🛠️ Environment

| Component      | Details                        |
| -------------- | ------------------------------ |
| Cloud Provider | AWS                            |
| Service        | AWS IAM                        |
| Feature        | Customer Managed Policy        |
| Platform       | AWS Management Console         |
| Category       | Security & Identity Management |

---

## 📌 Task

Create a custom IAM policy that provides **read-only access** to Amazon EC2 resources.

---

## 💻 Steps Performed

### 1️⃣ Open AWS Console

Navigate to:

```text id="1d2rgh"
IAM → Policies
```

---

### 2️⃣ Create Policy

Click:

```text id="y8g7lc"
Create Policy
```

Choose:

```text id="2eqx3r"
JSON
```

---

### 3️⃣ Add Policy Document

Example policy:

```json id="p4z9kh"
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:Describe*"
      ],
      "Resource": "*"
    }
  ]
}
```

---

### 4️⃣ Review Policy

Provide:

Example:

```text id="0w7gmy"
Policy Name: EC2ReadOnlyPolicy
Description: Allows read-only access to Amazon EC2 resources.
```

---

### 5️⃣ Create Policy

Click:

```text id="z6m1td"
Create Policy
```

---

### 6️⃣ Verify Policy

Navigate to:

```text id="7tr3pq"
IAM → Policies
```

Confirm the policy appears in the list.

---

## 📚 Concepts Learned

### What is an IAM Policy?

An IAM Policy is a JSON document that defines permissions for AWS resources.

Policies specify:

* Allowed or denied actions
* Resources
* Conditions

---

### What Does Read-Only Access Mean?

A read-only policy allows users to:

* View EC2 Instances
* View AMIs
* View Snapshots
* View Volumes
* View Security Groups
* View VPC Information

It does **not** allow users to:

* Launch EC2 instances
* Stop or terminate instances
* Delete resources
* Modify configurations

---

### IAM Policy Structure

| Element   | Purpose                 |
| --------- | ----------------------- |
| Version   | Policy language version |
| Statement | Permission block        |
| Effect    | Allow or Deny           |
| Action    | AWS API operations      |
| Resource  | AWS resources           |

---

## 🌍 Real-World Use Case

A support engineer needs to monitor EC2 infrastructure but should not be able to make changes.

A custom read-only IAM policy allows the engineer to inspect EC2 resources while preventing accidental or unauthorized modifications.

---

## 🔍 Verification

Verify that:

* The custom IAM policy is created.
* The policy can be attached to a user, group, or role.
* Users with the policy can view EC2 resources but cannot modify them.

---

## 🔐 Best Practices

* Follow the Principle of Least Privilege.
* Use customer-managed policies when custom permissions are required.
* Regularly review IAM policies.
* Avoid granting unnecessary write permissions.
* Use IAM groups or roles for easier permission management.

---

## 🧠 Key Takeaways

* Learned how to create a custom IAM policy.
* Understood JSON policy structure.
* Applied read-only permissions to Amazon EC2.
* Improved AWS security knowledge.
* Practiced access control using IAM.

---

## 🚀 Skills Practiced

* AWS IAM
* IAM Policies
* EC2 Permissions
* Identity & Access Management
* Cloud Security
* AWS Console Navigation

---

## 💡 Interview Questions

### Q1. What is an IAM Policy?

An IAM Policy is a JSON document that defines permissions for AWS resources.

---

### Q2. What is the difference between AWS Managed Policies and Customer Managed Policies?

AWS Managed Policies are created and maintained by AWS, while Customer Managed Policies are created and managed by AWS account administrators.

---

### Q3. What does `ec2:Describe*` allow?

It allows users to perform read-only (describe/list) operations on Amazon EC2 resources.

---

### Q4. What is the Principle of Least Privilege?

Grant only the minimum permissions required to perform a specific task.

---

### Q5. Can an IAM policy be attached directly to a user?

Yes. An IAM policy can be attached to a user, group, or role.

---

## 📌 Resources

* AWS IAM Documentation
* AWS IAM JSON Policy Reference
* Amazon EC2 IAM Actions Documentation
* AWS Security Best Practices

---

## ⭐ Day 018 Summary

Today's hands-on exercise focused on creating a **custom IAM policy** that provides read-only access to Amazon EC2 resources. I learned how IAM policies are structured, how permissions are defined using JSON, and how the Principle of Least Privilege helps secure AWS environments by granting only the permissions required for a specific role.
