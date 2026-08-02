
# 🚀 Day 029 – Establishing Secure Communication Between Public and Private VPCs via VPC Peering

## 📖 Overview

Today, I learned how to establish secure communication between two Amazon Virtual Private Clouds (VPCs) using **VPC Peering**. VPC Peering enables private IP communication between VPCs without routing traffic over the public internet.

This hands-on exercise strengthened my understanding of AWS networking, VPC Peering Connections, Route Tables, Security Groups, and secure inter-VPC communication.

---

# 🎯 Objective

* Create two VPCs (Public and Private).
* Configure subnets in each VPC.
* Launch EC2 instances.
* Establish a VPC Peering Connection.
* Update Route Tables.
* Configure Security Groups.
* Verify private communication between VPCs.

---

# 🛠️ Environment

| Component          | Details        |
| ------------------ | -------------- |
| Cloud Provider     | AWS            |
| Networking Service | Amazon VPC     |
| Connectivity       | VPC Peering    |
| Compute Service    | Amazon EC2     |
| Communication      | Private IP     |
| Category           | AWS Networking |

---

# 📌 Task

Create a VPC Peering connection between a Public VPC and a Private VPC, configure routing and security rules, and verify secure communication using private IP addresses.

---

# 💻 Steps Performed

## 1️⃣ Create the Public VPC

Navigate to:

```text id="vp001"
AWS Console → VPC → Create VPC
```

Example configuration:

| Setting   | Value       |
| --------- | ----------- |
| Name      | Public-VPC  |
| IPv4 CIDR | 10.0.0.0/16 |

Create a public subnet:

| Subnet        | CIDR        |
| ------------- | ----------- |
| Public-Subnet | 10.0.1.0/24 |

Attach an Internet Gateway and configure the Route Table.

---

## 2️⃣ Create the Private VPC

Create another VPC:

| Setting   | Value          |
| --------- | -------------- |
| Name      | Private-VPC    |
| IPv4 CIDR | 192.168.0.0/16 |

Create a private subnet:

| Subnet         | CIDR           |
| -------------- | -------------- |
| Private-Subnet | 192.168.1.0/24 |

No Internet Gateway is required for this subnet.

---

## 3️⃣ Launch EC2 Instances

Deploy:

### Public VPC

* Amazon Linux 2
* Public IP Enabled

### Private VPC

* Amazon Linux 2
* No Public IP

Example:

| Instance    | Private IP   |
| ----------- | ------------ |
| Public-EC2  | 10.0.1.10    |
| Private-EC2 | 192.168.1.10 |

---

## 4️⃣ Create a VPC Peering Connection

Navigate to:

```text id="vp002"
VPC → Peering Connections → Create Peering Connection
```

Example:

| Setting   | Value                  |
| --------- | ---------------------- |
| Name      | Public-Private-Peering |
| Requester | Public-VPC             |
| Accepter  | Private-VPC            |

Accept the request.

Status should become:

```text id="vp003"
Active
```

---

## 5️⃣ Update Route Tables

### Public VPC Route Table

Add:

| Destination    | Target                 |
| -------------- | ---------------------- |
| 192.168.0.0/16 | VPC Peering Connection |

---

### Private VPC Route Table

Add:

| Destination | Target                 |
| ----------- | ---------------------- |
| 10.0.0.0/16 | VPC Peering Connection |

---

## 6️⃣ Configure Security Groups

### Public EC2

Allow:

| Protocol | Port | Source         |
| -------- | ---- | -------------- |
| SSH      | 22   | Your IP        |
| ICMP     | All  | 192.168.0.0/16 |

---

### Private EC2

Allow:

| Protocol | Port | Source      |
| -------- | ---- | ----------- |
| SSH      | 22   | 10.0.0.0/16 |
| ICMP     | All  | 10.0.0.0/16 |

---

## 7️⃣ Verify Connectivity

SSH into the Public EC2 instance.

Test connectivity:

```bash id="vp004"
ping 192.168.1.10
```

SSH to the private instance:

```bash id="vp005"
ssh ec2-user@192.168.1.10
```

Successful communication confirms that the VPC Peering configuration is working correctly.

---

# 📚 Concepts Learned

## What is VPC Peering?

VPC Peering is a networking connection between two VPCs that enables resources to communicate using private IP addresses.

---

## Benefits of VPC Peering

* Private communication
* Low latency
* High bandwidth
* No VPN required
* No Internet Gateway required for inter-VPC traffic
* Simple networking configuration

---

## VPC Peering Architecture

```text id="vp006"
                 Internet
                     |
             Internet Gateway
                     |
               Public VPC
           (10.0.0.0/16)
                     |
          Public EC2 Instance
                     |
          VPC Peering Connection
                     |
              Private VPC
         (192.168.0.0/16)
                     |
         Private EC2 Instance
```

---

## VPC Peering Workflow

```text id="vp007"
Create Two VPCs
        |
Launch EC2 Instances
        |
Create Peering Connection
        |
Accept Peering Request
        |
Update Route Tables
        |
Configure Security Groups
        |
Private Communication
```

---

# 🌍 Real-World Use Case

An organization hosts:

* A public web application in one VPC.
* A private database in another VPC.

Instead of exposing the database to the internet, the application communicates securely through a VPC Peering Connection using private IP addresses.

This architecture improves security while maintaining fast, low-latency communication.

---

# 🔍 Verification

Verify:

✅ Both VPCs are created.
✅ Peering Connection status is **Active**.
✅ Route Tables contain peering routes.
✅ Security Groups allow required traffic.
✅ EC2 instances communicate using private IP addresses.
✅ Ping and SSH succeed between VPCs.

Useful commands:

```bash id="vp008"
ip addr
```

```bash id="vp009"
ping <private-ip>
```

```bash id="vp010"
ssh ec2-user@<private-ip>
```

---

# 🔐 Best Practices

* Use non-overlapping CIDR blocks for peered VPCs.
* Restrict Security Group rules to required CIDRs.
* Use private IP addresses for communication.
* Enable VPC Flow Logs for monitoring.
* Follow the principle of least privilege.
* Use Transit Gateway instead of multiple peerings in large environments.

---

# 🧠 Key Takeaways

* Created Public and Private VPCs.
* Established a VPC Peering Connection.
* Updated Route Tables.
* Configured Security Groups.
* Verified secure private communication.
* Learned AWS networking fundamentals for multi-VPC architectures.

---

# 🚀 Skills Practiced

* Amazon VPC
* VPC Peering
* Route Tables
* Security Groups
* Amazon EC2
* AWS Networking

---

# 💡 Interview Questions

### Q1. What is VPC Peering?

VPC Peering is a networking connection between two VPCs that enables private communication using private IPv4 or IPv6 addresses without traversing the public internet.

---

### Q2. Can VPC Peering connect VPCs in different AWS Regions?

Yes. This is known as **Inter-Region VPC Peering**, allowing secure communication across AWS Regions.

---

### Q3. Can transitive routing be performed through VPC Peering?

No. VPC Peering does **not** support transitive routing. If VPC-A is peered with VPC-B, and VPC-B is peered with VPC-C, VPC-A cannot communicate with VPC-C through VPC-B.

---

### Q4. Why must VPC CIDR blocks not overlap?

Overlapping CIDR ranges create routing conflicts, preventing successful VPC Peering.

---

### Q5. When should you use AWS Transit Gateway instead of VPC Peering?

AWS Transit Gateway is preferred when connecting **multiple VPCs and on-premises networks** because it simplifies network management and scales better than creating many individual peering connections.

---

# 📌 Resources

* AWS VPC Documentation
* AWS VPC Peering Guide
* AWS EC2 Documentation
* AWS Route Tables Documentation
* AWS Well-Architected Framework

---

# ⭐ Day 029 Summary

Today's hands-on exercise focused on **establishing secure communication between Public and Private VPCs using VPC Peering**. I created two VPCs, configured subnets, launched EC2 instances, established a VPC Peering Connection, updated Route Tables and Security Groups, and verified private communication. This exercise strengthened my understanding of secure AWS networking and multi-VPC architectures commonly used in production environments.
