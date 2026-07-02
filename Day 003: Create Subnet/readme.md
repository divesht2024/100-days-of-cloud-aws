# 🚀 Day 003 – Create AWS VPC Subnet

## 📖 Overview

Today, I learned about **AWS Subnets**, one of the core networking components within an Amazon VPC (Virtual Private Cloud). A subnet is a logical subdivision of a VPC that allows you to organize and isolate cloud resources based on security, availability, and application architecture.

Creating subnets is an essential step when designing scalable, secure, and highly available cloud infrastructures.

---

## 🎯 Objective

- Understand what a subnet is.
- Learn why subnets are used in AWS.
- Create a subnet inside an existing VPC.
- Understand CIDR blocks and IP address allocation.
- Learn the difference between public and private subnets.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Cloud Provider | AWS |
| Service | Amazon VPC |
| Feature | Subnet |
| Platform | AWS Management Console |

---

## 📌 Task

Create a subnet within an existing Amazon VPC by specifying an Availability Zone and CIDR block.

---

## 🌐 What is a Subnet?

A **Subnet (Subnetwork)** is a smaller network created inside a **Virtual Private Cloud (VPC)**.

It divides the VPC into multiple logical sections so that resources can be organized based on their purpose, security requirements, and availability.

Every subnet belongs to **one Availability Zone (AZ)**.

---

## ⚙️ Steps Performed

1. Open the AWS Management Console.
2. Navigate to **Amazon VPC**.
3. Select **Subnets**.
4. Click **Create Subnet**.
5. Choose the VPC.
6. Enter:
   - Subnet Name
   - Availability Zone
   - IPv4 CIDR Block
7. Click **Create Subnet**.
8. Verify the subnet has been created successfully.

---

## 📚 Concepts Learned

### What is a CIDR Block?

CIDR (Classless Inter-Domain Routing) defines the range of IP addresses available within a network.

Example:

```
VPC CIDR:
10.0.0.0/16

Subnet 1:
10.0.1.0/24

Subnet 2:
10.0.2.0/24

Subnet 3:
10.0.3.0/24
```

Each subnet receives a portion of the VPC's available IP addresses.

---

### What is an Availability Zone?

An **Availability Zone (AZ)** is an isolated data center within an AWS Region.

Each subnet exists in **only one Availability Zone**.

Deploying resources across multiple AZs improves:

- High Availability
- Fault Tolerance
- Disaster Recovery

---

### Public Subnet

A **Public Subnet** is connected to an **Internet Gateway**.

Resources inside a public subnet can communicate with the internet.

Common resources:

- Web Servers
- Load Balancers
- Bastion Hosts

---

### Private Subnet

A **Private Subnet** does **not** have direct internet access.

Resources communicate internally within the VPC.

Common resources:

- Databases
- Application Servers
- Cache Servers
- Internal APIs

---

## 🌍 Real-World Use Case

Imagine you're deploying a three-tier web application.

### Public Subnet

Contains:

- Application Load Balancer
- Web Servers

These resources receive traffic from internet users.

### Private Subnet

Contains:

- Application Servers

Only the web servers can communicate with them.

### Database Subnet

Contains:

- MySQL or PostgreSQL Database

Only the application servers have permission to access the database.

This architecture improves security by ensuring sensitive resources are never directly exposed to the internet.

---

## 🔍 Verification

After creating the subnet:

- Verify the subnet appears in the VPC Dashboard.
- Confirm the CIDR block.
- Confirm the Availability Zone.
- Ensure the subnet belongs to the correct VPC.
- Verify available IP addresses.

---

## 🔐 Best Practices

- Separate public and private resources.
- Use different subnets for different application tiers.
- Spread workloads across multiple Availability Zones.
- Plan CIDR ranges carefully to avoid overlapping IP addresses.
- Reserve sufficient IP space for future scaling.
- Follow the Principle of Least Privilege when configuring routing and security.

---

## 🧠 Key Takeaways

- Learned what a subnet is.
- Understood why VPCs are divided into subnets.
- Learned how CIDR blocks allocate IP addresses.
- Understood the difference between public and private subnets.
- Learned that each subnet belongs to only one Availability Zone.
- Understood how subnets improve security and scalability.

---

## 🚀 Skills Practiced

- AWS VPC
- AWS Networking
- Subnet Creation
- CIDR Planning
- Cloud Infrastructure
- High Availability Design
- AWS Console Navigation

---

## 📖 Example Network Architecture

```
VPC (10.0.0.0/16)
│
├── Public Subnet (10.0.1.0/24)
│      ├── Load Balancer
│      └── Web Server
│
├── Private Subnet (10.0.2.0/24)
│      └── Application Server
│
└── Database Subnet (10.0.3.0/24)
       └── Amazon RDS
```

---

## 💡 Interview Questions

### Q1. What is a subnet?

A subnet is a logical subdivision of a VPC that groups AWS resources within a specific IP address range and Availability Zone.

---

### Q2. Can a subnet span multiple Availability Zones?

No. A subnet can exist in only one Availability Zone.

---

### Q3. What is the difference between a public subnet and a private subnet?

A public subnet has a route to an Internet Gateway, allowing internet access. A private subnet has no direct internet route and is used for internal resources like application servers and databases.

---

### Q4. Why do we create multiple subnets?

Multiple subnets help isolate workloads, improve security, organize resources, and support high availability across different Availability Zones.

---

### Q5. What is CIDR?

CIDR (Classless Inter-Domain Routing) defines the IP address range allocated to a VPC or subnet.

---

## 📌 Resources

- AWS VPC Documentation
- AWS Subnet Documentation
- AWS Networking Best Practices
- AWS Well-Architected Framework

---

## ⭐ Day 003 Summary

Today's hands-on exercise introduced me to **AWS Subnets**, a fundamental component of cloud networking. I learned how subnets divide a VPC into smaller networks, how CIDR blocks determine IP address allocation, and why public and private subnets are essential for building secure and scalable cloud architectures. Understanding subnet design is a critical step toward mastering AWS networking and designing production-ready infrastructures.
