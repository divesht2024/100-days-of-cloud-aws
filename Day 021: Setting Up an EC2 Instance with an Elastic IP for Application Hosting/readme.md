# 🚀 Day 021 – Setting Up an EC2 Instance with an Elastic IP for Application Hosting

## 📖 Overview

Today, I learned how to launch an **Amazon EC2 instance** and associate an **Elastic IP (EIP)** to provide a static public IP address. Elastic IPs ensure that applications remain accessible even if the instance is stopped and started, making them ideal for hosting web applications and services.

This hands-on exercise improved my understanding of EC2 networking, public IP management, and AWS infrastructure deployment.

---

## 🎯 Objective

* Launch an Amazon EC2 instance.
* Allocate an Elastic IP address.
* Associate the Elastic IP with the EC2 instance.
* Verify application accessibility using the static public IP.
* Understand real-world use cases for Elastic IPs.

---

## 🛠️ Environment

| Component      | Details                |
| -------------- | ---------------------- |
| Cloud Provider | AWS                    |
| Service        | Amazon EC2             |
| Feature        | Elastic IP             |
| Platform       | AWS Management Console |
| Category       | Compute & Networking   |

---

## 📌 Task

Deploy an EC2 instance and configure it with an Elastic IP to host an application that remains accessible through a fixed public IP address.

---

## 💻 Steps Performed

### 1️⃣ Launch an EC2 Instance

Navigate to:

```text
AWS Console → EC2 → Instances → Launch Instance
```

Configure:

* Amazon Machine Image (AMI)
* Instance Type
* Key Pair
* Security Group
* Storage
* Network Settings

Launch the instance.

---

### 2️⃣ Allocate an Elastic IP

Navigate to:

```text
EC2 → Network & Security → Elastic IPs
```

Click:

```text
Allocate Elastic IP Address
```

Accept the default settings and allocate the address.

---

### 3️⃣ Associate the Elastic IP

Select the allocated Elastic IP.

Click:

```text
Actions → Associate Elastic IP Address
```

Choose:

* Resource Type: **Instance**
* Select the target EC2 instance
* Private IP Address (if multiple are available)

Click:

```text
Associate
```

---

### 4️⃣ Verify Association

Navigate back to:

```text
EC2 → Instances
```

Confirm the instance now displays the assigned Elastic IP as its public IPv4 address.

---

### 5️⃣ Test Connectivity

Connect to the EC2 instance:

```bash
ssh -i key.pem ec2-user@<Elastic-IP>
```

If a web server is installed:

```text
http://<Elastic-IP>
```

Verify that the application is accessible through the browser.

---

## 📚 Concepts Learned

### What is an EC2 Instance?

Amazon EC2 (Elastic Compute Cloud) provides scalable virtual servers in the AWS Cloud for hosting applications and services.

---

### What is an Elastic IP?

An Elastic IP (EIP) is a **static public IPv4 address** provided by AWS that can be associated with an EC2 instance.

Unlike automatically assigned public IPs, an Elastic IP remains the same even after the instance is stopped and started.

---

### Benefits of Elastic IP

* Static public IP address
* Easy instance replacement
* Minimal application downtime
* Simplified DNS configuration
* Reliable remote access

---

### Public IP vs Elastic IP

| Public IP                | Elastic IP                              |
| ------------------------ | --------------------------------------- |
| Assigned automatically   | Allocated manually                      |
| Changes after stop/start | Remains static                          |
| Temporary                | Persistent until released               |
| No management required   | Can be reassociated to another instance |

---

## 🌍 Real-World Use Case

A company hosts a customer-facing web application on an EC2 instance.

To ensure customers always access the application using the same IP address, an Elastic IP is associated with the instance. If the application is migrated to another EC2 instance due to maintenance or failure, the Elastic IP can be reassigned quickly, minimizing downtime.

---

## 🔍 Verification

Verify that:

* EC2 instance is running.
* Elastic IP is allocated.
* Elastic IP is associated with the instance.
* SSH connectivity works using the Elastic IP.
* The hosted application is accessible through the Elastic IP.

---

## 🔐 Best Practices

* Release unused Elastic IPs to avoid unnecessary charges.
* Restrict inbound traffic using Security Groups.
* Use Elastic IPs only when a static public IP is required.
* Monitor EC2 instances with CloudWatch.
* Use IAM roles instead of storing AWS credentials on the instance.

---

## 🧠 Key Takeaways

* Learned how to deploy an EC2 instance.
* Understood the purpose of Elastic IPs.
* Associated an Elastic IP with an EC2 instance.
* Verified application accessibility.
* Improved AWS networking knowledge.

---

## 🚀 Skills Practiced

* Amazon EC2
* Elastic IP
* AWS Networking
* Security Groups
* SSH
* Cloud Infrastructure


---

## 💡 Interview Questions

### Q1. What is an Elastic IP?

An Elastic IP is a static public IPv4 address that can be associated with an EC2 instance.

---

### Q2. Why use an Elastic IP instead of a public IP?

A public IP assigned automatically may change when an instance is stopped and started, whereas an Elastic IP remains constant.

---

### Q3. Can an Elastic IP be moved to another EC2 instance?

Yes. An Elastic IP can be disassociated from one instance and associated with another within the same AWS Region.

---

### Q4. Are Elastic IPs free?

An Elastic IP is generally free while associated with a running EC2 instance, but AWS charges for unused or idle Elastic IPs.

---

### Q5. What is the relationship between an Elastic IP and Security Groups?

An Elastic IP provides a reachable public address, while Security Groups control which inbound and outbound traffic is allowed to reach the EC2 instance.

---

## 📌 Resources

* AWS EC2 Documentation
* AWS Elastic IP Documentation
* AWS VPC User Guide
* AWS Security Best Practices

---

## ⭐ Day 021 Summary

Today's hands-on exercise focused on launching an **Amazon EC2 instance** and associating an **Elastic IP** to provide a stable public endpoint for application hosting. I learned how Elastic IPs simplify application accessibility, support infrastructure resilience, and play an important role in AWS networking and cloud operations.
