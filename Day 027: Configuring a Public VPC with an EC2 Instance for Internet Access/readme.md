
# 🚀 Day 027 – Configuring a Public VPC with an EC2 Instance for Internet Access

## 📖 Overview

Today, I learned how to create a **Public Virtual Private Cloud (VPC)** in AWS and launch an **Amazon EC2 instance** with internet connectivity. This involved configuring a VPC, public subnet, Internet Gateway (IGW), route table, security group, and EC2 instance.

This hands-on exercise strengthened my understanding of AWS networking fundamentals and how different networking components work together to provide secure internet access.

---

# 🎯 Objective

* Create a custom VPC.
* Create a public subnet.
* Attach an Internet Gateway (IGW).
* Configure a Route Table.
* Launch an EC2 instance in the public subnet.
* Enable internet connectivity.
* Verify inbound and outbound internet access.

---

# 🛠️ Environment

| Component          | Details                |
| ------------------ | ---------------------- |
| Cloud Provider     | AWS                    |
| Networking Service | Amazon VPC             |
| Compute Service    | Amazon EC2             |
| Internet Access    | Internet Gateway (IGW) |
| Route              | 0.0.0.0/0              |
| Category           | AWS Networking         |

---

# 📌 Task

Create a public VPC with a public subnet, configure internet access using an Internet Gateway and Route Table, then launch an EC2 instance that can communicate with the internet.

---

# 💻 Steps Performed

## 1️⃣ Create a VPC

Navigate to:

```text id="w7p4jd"
AWS Console → VPC → Create VPC
```

Example configuration:

| Setting   | Value       |
| --------- | ----------- |
| Name      | Public-VPC  |
| IPv4 CIDR | 10.0.0.0/16 |
| Tenancy   | Default     |

---

## 2️⃣ Create a Public Subnet

Navigate to:

```text id="j8m2vh"
VPC → Subnets → Create Subnet
```

Example:

| Setting           | Value       |
| ----------------- | ----------- |
| VPC               | Public-VPC  |
| Availability Zone | us-east-1a  |
| CIDR Block        | 10.0.1.0/24 |

Enable:

```text id="d5x9ru"
Auto-assign Public IPv4 Address = Enabled
```

---

## 3️⃣ Create an Internet Gateway (IGW)

Navigate to:

```text id="s3n6yt"
VPC → Internet Gateways → Create Internet Gateway
```

Example Name:

```text id="v4b8kc"
Public-IGW
```

Attach the Internet Gateway to the VPC.

---

## 4️⃣ Create a Route Table

Navigate to:

```text id="r6h3pf"
VPC → Route Tables → Create Route Table
```

Associate it with the VPC.

Add the following route:

| Destination | Target           |
| ----------- | ---------------- |
| 0.0.0.0/0   | Internet Gateway |

Associate the route table with the public subnet.

---

## 5️⃣ Create a Security Group

Allow inbound traffic:

| Type  | Port | Source    |
| ----- | ---- | --------- |
| SSH   | 22   | Your IP   |
| HTTP  | 80   | 0.0.0.0/0 |
| HTTPS | 443  | 0.0.0.0/0 |

Outbound:

* Allow All Traffic (Default)

---

## 6️⃣ Launch an EC2 Instance

Navigate to:

```text id="g8k2zw"
EC2 → Launch Instance
```

Configuration:

* Amazon Linux 2 / Amazon Linux 2023
* t2.micro / t3.micro
* Public-VPC
* Public Subnet
* Auto-assign Public IP = Enabled
* Select Security Group
* Select Key Pair

Launch the instance.

---

## 7️⃣ Connect to the EC2 Instance

```bash id="p9m7dw"
ssh -i my-key.pem ec2-user@<Public-IP>
```

For Ubuntu:

```bash id="h2q4rn"
ssh -i my-key.pem ubuntu@<Public-IP>
```

---

## 8️⃣ Verify Internet Connectivity

Ping an external host:

```bash id="f3t8ke"
ping google.com
```

Update packages:

Amazon Linux:

```bash id="m5z1cy"
sudo yum update -y
```

Amazon Linux 2023:

```bash id="e9j6tp"
sudo dnf update -y
```

Ubuntu:

```bash id="b7v2la"
sudo apt update
```

Successful updates confirm outbound internet access.

---

# 📚 Concepts Learned

## What is a VPC?

A Virtual Private Cloud (VPC) is a logically isolated virtual network where AWS resources are deployed securely.

---

## What is a Public Subnet?

A public subnet is associated with a route table that contains a route to an Internet Gateway, allowing resources inside the subnet to communicate with the internet.

---

## What is an Internet Gateway (IGW)?

An Internet Gateway enables communication between resources inside a VPC and the public internet.

---

## What is a Route Table?

A Route Table contains rules that determine where network traffic is directed.

Example:

| Destination | Target           |
| ----------- | ---------------- |
| 10.0.0.0/16 | Local            |
| 0.0.0.0/0   | Internet Gateway |

---

# 🏗️ Architecture Diagram

```text id="u4r9mg"
                   Internet
                       |
                Internet Gateway
                       |
               -----------------
               |               |
            Route Table
               |
         Public Subnet
               |
         Security Group
               |
          Amazon EC2
```

---

# 🌍 Real-World Use Case

A company hosts a public-facing web application on AWS.

The infrastructure includes:

* A custom VPC
* Public subnet
* Internet Gateway
* Route Table
* EC2 instance running a web server

Users on the internet can access the application securely through the EC2 instance's public IP or DNS.

---

# 🔍 Verification

Verify:

✅ VPC created successfully.
✅ Public subnet associated with Route Table.
✅ Internet Gateway attached to the VPC.
✅ Route `0.0.0.0/0` points to the IGW.
✅ EC2 has a public IPv4 address.
✅ SSH connection works.
✅ Internet access is available from the EC2 instance.

Useful commands:

```bash id="x6k8np"
curl ifconfig.me
```

```bash id="q2d5ht"
ping google.com
```

```bash id="l1v4sy"
ip addr
```

---

# 🔐 Best Practices

* Use public subnets only for internet-facing resources.
* Restrict SSH access to trusted IP addresses.
* Place databases in private subnets.
* Follow the principle of least privilege for Security Groups.
* Enable VPC Flow Logs for network monitoring.
* Use NAT Gateways for private subnet internet access.

---

# 🧠 Key Takeaways

* Created a custom VPC.
* Configured a public subnet.
* Attached an Internet Gateway.
* Configured Route Tables.
* Launched an internet-accessible EC2 instance.
* Learned AWS networking fundamentals.

---

# 🚀 Skills Practiced

* Amazon VPC
* Amazon EC2
* Internet Gateway
* Route Tables
* Security Groups
* AWS Networking

---

# 💡 Interview Questions

### Q1. What is a VPC?

A VPC (Virtual Private Cloud) is a logically isolated virtual network where AWS resources such as EC2 instances are deployed securely.

---

### Q2. What makes a subnet public?

A subnet is considered public when its associated route table contains a route (`0.0.0.0/0`) pointing to an Internet Gateway, and instances have public IP addresses.

---

### Q3. What is the purpose of an Internet Gateway?

An Internet Gateway enables communication between resources in a VPC and the public internet.

---

### Q4. What is the difference between a Security Group and a Route Table?

| Security Group                                              | Route Table                                |
| ----------------------------------------------------------- | ------------------------------------------ |
| Controls inbound and outbound traffic at the instance level | Determines where network traffic is routed |
| Acts as a virtual firewall                                  | Acts as a network routing table            |

---

### Q5. Can an EC2 instance in a public subnet access the internet without a public IP?

No. Even if the subnet has a route to an Internet Gateway, the EC2 instance requires a public IPv4 address (or an Elastic IP) to communicate directly with the internet.

---

# 📌 Resources

* AWS VPC Documentation
* Amazon EC2 Documentation
* AWS Internet Gateway Guide
* AWS Route Tables Documentation
* AWS Well-Architected Framework

---

# ⭐ Day 027 Summary

Today's hands-on exercise focused on **building a public AWS networking environment**. I created a custom VPC, configured a public subnet, attached an Internet Gateway, created Route Tables, and launched an EC2 instance with internet connectivity. This exercise provided a solid foundation in AWS networking, which is essential for designing secure, scalable, and production-ready cloud architectures.
