# 🚀 Day 010 – Attach an Elastic IP to an Amazon EC2 Instance

## 📖 Overview

Today, I learned how to attach an **Elastic IP (EIP)** to an Amazon EC2 instance. An Elastic IP is a static public IPv4 address provided by AWS that remains associated with your AWS account until you release it.

Unlike the default public IP assigned to an EC2 instance, an Elastic IP does not change when the instance is stopped and started, making it ideal for production workloads and applications that require a stable public address.

---

## 🎯 Objective

* Understand what an Elastic IP is.
* Allocate a new Elastic IP address.
* Associate the Elastic IP with an EC2 instance.
* Verify connectivity using the new IP address.
* Understand real-world use cases and best practices.

---

## 🛠️ Environment

| Component      | Details                |
| -------------- | ---------------------- |
| Cloud Provider | AWS                    |
| Service        | Amazon EC2             |
| Feature        | Elastic IP             |
| Platform       | AWS Management Console |
| Category       | Networking             |

---

## 📌 Task

Allocate an Elastic IP address and attach it to an existing EC2 instance.

---

## 💻 Steps Performed

1. Open the AWS Management Console.
2. Navigate to **EC2 Dashboard**.
3. Select **Elastic IPs** from the left navigation pane.
4. Click **Allocate Elastic IP Address**.
5. Accept the default settings and allocate the address.
6. Select the newly created Elastic IP.
7. Click **Actions → Associate Elastic IP Address**.
8. Select the target EC2 instance.
9. Choose the appropriate private IP address if multiple interfaces exist.
10. Click **Associate**.
11. Verify the EC2 instance now uses the Elastic IP.

---

## 📚 Concepts Learned

### What is an Elastic IP?

An Elastic IP is a static public IPv4 address designed for dynamic cloud computing.

Unlike standard public IP addresses assigned to EC2 instances, an Elastic IP remains allocated to your AWS account until you explicitly release it.

---

### Why Use an Elastic IP?

Benefits include:

* Static public IP address
* Survives instance stop/start cycles
* Easy failover between instances
* Simplifies DNS management
* Ideal for production environments

---

### Public IP vs Elastic IP

| Public IP                | Elastic IP                  |
| ------------------------ | --------------------------- |
| Changes after stop/start | Remains the same            |
| Automatically assigned   | Manually allocated          |
| Temporary                | Persistent                  |
| Free while instance runs | Charges may apply if unused |

---

### How Elastic IP Works

```text
Internet
    ↓
Elastic IP
    ↓
EC2 Instance
```

AWS maps the Elastic IP to the instance's private IP address, allowing external users to access the server using a consistent public address.

---

## 🌍 Real-World Use Case

Imagine a company hosts its production website on an EC2 instance.

If the instance is stopped for maintenance and later restarted, its default public IP changes.

This would require:

* Updating DNS records
* Updating firewall rules
* Reconfiguring external integrations

By using an Elastic IP, the public address remains unchanged, ensuring uninterrupted access for users and applications.

---

## 🔍 Verification

Verify the Elastic IP association:

1. Open the EC2 instance details.
2. Check the **Public IPv4 Address** field.
3. Confirm it matches the allocated Elastic IP.

You can also test connectivity:

```bash
ping <elastic-ip>
```

Or connect via SSH:

```bash
ssh -i my-key.pem ec2-user@<elastic-ip>
```

---

## 🔐 Best Practices

* Release unused Elastic IPs to avoid charges.
* Use Elastic IPs only when a static public IP is required.
* Prefer Load Balancers for highly available applications.
* Tag Elastic IP resources for easier management.
* Monitor Elastic IP usage to optimize costs.

---

## 🧠 Key Takeaways

* Learned what an Elastic IP is.
* Understood the difference between Public IP and Elastic IP.
* Learned how to allocate and attach an Elastic IP.
* Understood the importance of static public addresses.
* Gained hands-on experience with AWS networking.

---

## 🚀 Skills Practiced

* Amazon EC2
* AWS Networking
* Elastic IP Management
* Public IP Addressing
* AWS Console Navigation
* Cloud Infrastructure

---


## 💡 Interview Questions

### Q1. What is an Elastic IP?

An Elastic IP is a static public IPv4 address that can be associated with an EC2 instance.

---

### Q2. Why use an Elastic IP instead of a normal public IP?

Because an Elastic IP remains unchanged even when the instance is stopped and started.

---

### Q3. Can an Elastic IP be moved to another instance?

Yes. An Elastic IP can be disassociated from one EC2 instance and attached to another.

---

### Q4. Is an Elastic IP free?

AWS provides one Elastic IP free when associated with a running instance. Charges may apply for unused or additional Elastic IPs.

---

### Q5. Which AWS service provides static public IP addresses for EC2 instances?

Elastic IP (EIP) provides static public IP addresses for EC2 instances.

---

## 📌 Resources

* AWS EC2 Documentation
* AWS Elastic IP Documentation
* AWS VPC Documentation
* AWS Well-Architected Framework

---

## ⭐ Day 010 Summary

Today's hands-on exercise introduced me to **Elastic IPs**, an important AWS networking feature that provides static public IP addresses for EC2 instances. I learned how to allocate and associate an Elastic IP, understood its advantages over standard public IPs, and explored real-world use cases where stable public connectivity is essential for production applications.
