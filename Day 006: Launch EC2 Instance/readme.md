# 🚀 Day 006 – Launch an Amazon EC2 Instance

## 📖 Overview

Today, I learned how to launch an **Amazon Elastic Compute Cloud (EC2)** instance, one of the core services offered by AWS. EC2 provides scalable virtual servers in the cloud, allowing users to deploy applications, host websites, run databases, and perform various computing tasks.

Launching an EC2 instance involves selecting an Amazon Machine Image (AMI), choosing an instance type, configuring networking, attaching storage, and securing access using key pairs and security groups.

---

## 🎯 Objective

- Understand what Amazon EC2 is.
- Launch a new EC2 instance.
- Configure networking and storage.
- Associate a Security Group and Key Pair.
- Connect to the instance using SSH.
- Understand real-world use cases and best practices.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Cloud Provider | AWS |
| Service | Amazon EC2 |
| Platform | AWS Management Console |
| Operating System | Amazon Linux 2023 / Ubuntu (Example) |

---

## 📌 Task

Launch a new EC2 instance by selecting the appropriate AMI, instance type, key pair, security group, storage, and network configuration.

---

## 💻 Steps Performed

1. Open the **AWS Management Console**.
2. Navigate to **Amazon EC2**.
3. Click **Launch Instance**.
4. Enter an instance name.
5. Select an **Amazon Machine Image (AMI)**.
6. Choose an **Instance Type** (e.g., `t2.micro` or `t3.micro`).
7. Select or create an **EC2 Key Pair**.
8. Configure **Network Settings**:
   - Select VPC
   - Select Subnet
   - Enable Auto-assign Public IP (if required)
   - Attach a Security Group
9. Configure **Storage** (Amazon EBS).
10. Review the configuration.
11. Click **Launch Instance**.
12. Verify the instance is in the **Running** state.

---

## 📚 Concepts Learned

### What is Amazon EC2?

Amazon Elastic Compute Cloud (EC2) is a web service that provides resizable virtual servers in the AWS Cloud.

It allows users to deploy applications without managing physical hardware.

---

### What is an AMI?

An **Amazon Machine Image (AMI)** is a pre-configured template that contains:

- Operating System
- Software packages
- Configuration settings

Examples:

- Amazon Linux
- Ubuntu
- Red Hat Enterprise Linux
- Windows Server

---

### What is an Instance Type?

An instance type determines the CPU, memory, networking, and storage performance of an EC2 instance.

Example:

| Instance Type | Use Case |
|--------------|----------|
| t2.micro | Free Tier, small applications |
| t3.micro | General-purpose workloads |
| m5.large | Business applications |
| c5.large | Compute-intensive applications |

---

### What is a Key Pair?

An EC2 Key Pair provides secure authentication when connecting to Linux instances using SSH.

It consists of:

- Public Key (stored by AWS)
- Private Key (.pem file stored locally)

---

### What is a Security Group?

A Security Group acts as a virtual firewall for an EC2 instance.

It controls:

- Inbound traffic
- Outbound traffic

Common inbound rules:

| Port | Service |
|------|----------|
| 22 | SSH |
| 80 | HTTP |
| 443 | HTTPS |

---

### What is Amazon EBS?

Amazon Elastic Block Store (EBS) provides persistent block storage attached to EC2 instances.

It stores:

- Operating system
- Applications
- User data
- Databases

---

## 🌍 Real-World Use Case

Imagine a company launching a web application.

The DevOps team:

- Launches an EC2 instance.
- Installs a web server such as Nginx or Apache.
- Attaches an EBS volume for storage.
- Configures a Security Group to allow HTTP (80), HTTPS (443), and SSH (22).
- Uses an Application Load Balancer to distribute traffic.

This forms the foundation of a production-ready cloud application.

---

## 🔍 Verification

After launching the instance:

- Verify the instance state is **Running**.
- Confirm the instance has a public IP (if required).
- Check that the Security Group is attached.
- Verify the EBS volume is attached.
- Connect using SSH:

```bash
ssh -i my-key.pem ec2-user@<public-ip>
```

---

## 🔐 Best Practices

- Use IAM roles instead of storing AWS credentials on the instance.
- Restrict SSH access to your public IP.
- Enable EBS encryption.
- Use the latest AMI versions.
- Stop or terminate unused instances to reduce costs.
- Regularly patch and update the operating system.
- Monitor instances using Amazon CloudWatch.

---

## 🧠 Key Takeaways

- Learned how to launch an Amazon EC2 instance.
- Understood the purpose of AMIs and instance types.
- Learned how to configure networking and storage.
- Understood how Security Groups protect EC2 instances.
- Learned how Key Pairs provide secure SSH authentication.
- Gained practical experience with AWS compute services.

---

## 🚀 Skills Practiced

- Amazon EC2
- AWS Compute
- Virtual Machines
- Cloud Networking
- Security Groups
- SSH
- Amazon EBS
- AWS Console Navigation

---



## 📖 Key Terms

| Term | Description |
|------|-------------|
| EC2 | Virtual server in AWS |
| AMI | Template used to launch EC2 instances |
| Instance Type | Defines CPU, memory, and networking resources |
| Security Group | Virtual firewall for EC2 |
| Key Pair | Secure authentication method for SSH |
| EBS | Persistent block storage for EC2 |
| Public IP | IP address used to access the instance from the internet |

---

## 💡 Interview Questions

### Q1. What is Amazon EC2?

Amazon EC2 is a cloud computing service that provides scalable virtual servers for running applications.

---

### Q2. What is an AMI?

An Amazon Machine Image (AMI) is a pre-configured template containing an operating system and software required to launch an EC2 instance.

---

### Q3. What is the purpose of a Security Group?

A Security Group acts as a virtual firewall that controls inbound and outbound traffic for an EC2 instance.

---

### Q4. Why is a Key Pair required?

A Key Pair enables secure SSH authentication to Linux EC2 instances without using passwords.

---

### Q5. What storage is attached to an EC2 instance?

Amazon EBS volumes provide persistent block storage for EC2 instances.

---

## 📌 Resources

- AWS Amazon EC2 Documentation
- AWS EC2 User Guide
- AWS Well-Architected Framework
- AWS Security Best Practices

---

## ⭐ Day 006 Summary

Today's hands-on exercise introduced me to **Amazon EC2**, AWS's core compute service. I learned how to launch a virtual server by selecting an AMI, configuring networking, attaching storage, and securing access with Key Pairs and Security Groups. Understanding EC2 is a foundational skill for cloud computing and DevOps, as it forms the basis for deploying and managing scalable applications in AWS.
