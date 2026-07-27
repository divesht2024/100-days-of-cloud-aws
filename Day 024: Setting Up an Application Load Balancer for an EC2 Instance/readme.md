
# 🚀 Day 024 – Setting Up an Application Load Balancer (ALB) for an EC2 Instance

## 📖 Overview

Today, I learned how to configure an **Application Load Balancer (ALB)** to distribute incoming HTTP/HTTPS traffic across Amazon EC2 instances. An ALB improves application availability, scalability, and fault tolerance by routing requests to healthy targets.

This hands-on exercise strengthened my understanding of AWS networking, load balancing, target groups, health checks, and highly available application architectures.

---

# 🎯 Objective

* Understand the purpose of an Application Load Balancer.
* Create an ALB.
* Create and configure a Target Group.
* Register an EC2 instance as a target.
* Configure health checks.
* Verify application accessibility through the ALB.

---

# 🛠️ Environment

| Component      | Details                                            |
| -------------- | -------------------------------------------------- |
| Cloud Provider | AWS                                                |
| Service        | Elastic Load Balancing (Application Load Balancer) |
| Compute        | Amazon EC2                                         |
| Protocol       | HTTP / HTTPS                                       |
| Category       | Networking & High Availability                     |

---

# 📌 Task

Deploy an **Application Load Balancer (ALB)**, register an EC2 instance using a Target Group, configure health checks, and verify that application traffic is routed successfully.

---

# 💻 Steps Performed

## 1️⃣ Launch an EC2 Instance

Navigate to:

```text
AWS Console → EC2 → Instances
```

Ensure:

* EC2 instance is running.
* Security Group allows HTTP (Port 80).
* Web server (Apache/Nginx) is installed and running.

---

## 2️⃣ Create a Target Group

Navigate to:

```text
EC2 → Target Groups
```

Click:

```text
Create Target Group
```

Configuration:

* Target Type: **Instances**
* Protocol: **HTTP**
* Port: **80**
* Health Check Protocol: **HTTP**
* Health Check Path: **/**

Register the EC2 instance.

---

## 3️⃣ Create an Application Load Balancer

Navigate to:

```text
EC2 → Load Balancers
```

Click:

```text
Create Load Balancer
```

Choose:

```text
Application Load Balancer
```

Configure:

* Internet-facing
* IPv4
* Select VPC
* Select at least **two Availability Zones**
* Select public subnets

---

## 4️⃣ Configure Security Group

Allow:

| Protocol | Port           |
| -------- | -------------- |
| HTTP     | 80             |
| HTTPS    | 443 (Optional) |

---

## 5️⃣ Configure Listener

Create an HTTP Listener:

```text
Protocol: HTTP
Port: 80
```

Forward requests to the Target Group created earlier.

---

## 6️⃣ Verify Target Health

Navigate to:

```text
Target Groups → Targets
```

Confirm the EC2 instance status is:

```text
Healthy
```

---

## 7️⃣ Test the Load Balancer

Copy the ALB DNS Name:

```text
http://my-alb-xxxxxxxx.region.elb.amazonaws.com
```

Open it in a browser or test using:

```bash
curl http://<ALB-DNS-Name>
```

The application hosted on the EC2 instance should be displayed.

---

# 📚 Concepts Learned

## What is an Application Load Balancer (ALB)?

An Application Load Balancer distributes incoming HTTP and HTTPS traffic across multiple targets, such as EC2 instances, based on Layer 7 (Application Layer) routing rules.

---

## What is a Target Group?

A Target Group is a collection of backend resources (such as EC2 instances) that receive traffic from the load balancer.

---

## Health Checks

Health checks determine whether a target is healthy and able to receive traffic.

Example:

```text
Protocol: HTTP
Path: /
Healthy Threshold: 5
```

Only healthy instances receive client requests.

---

## ALB Architecture

```text
              Internet
                  |
                  |
        Application Load Balancer
                  |
        -----------------------
        |                     |
        |                     |
    EC2 Instance 1      EC2 Instance 2
        |                     |
      Web App             Web App
```

---

## Application Load Balancer vs Network Load Balancer

| Application Load Balancer    | Network Load Balancer    |
| ---------------------------- | ------------------------ |
| Layer 7 (HTTP/HTTPS)         | Layer 4 (TCP/UDP)        |
| Content-based routing        | High-performance routing |
| Supports path & host routing | Best for low latency     |
| Supports WebSockets          | Static IP support        |

---

# 🌍 Real-World Use Case

An e-commerce website receives thousands of requests every minute.

Instead of sending all traffic to one EC2 instance:

* An Application Load Balancer distributes traffic.
* Multiple EC2 instances serve customer requests.
* Health checks automatically remove unhealthy instances.
* Auto Scaling can add or remove instances based on demand.

This ensures high availability, scalability, and improved user experience.

---

# 🔍 Verification

Verify that:

* EC2 instance is running.
* Target Group shows **Healthy**.
* ALB listener is configured correctly.
* Security Groups allow HTTP traffic.
* Application is accessible using the ALB DNS name.

---

# 🔐 Best Practices

* Deploy ALBs across multiple Availability Zones.
* Enable HTTPS using AWS Certificate Manager (ACM).
* Configure health checks properly.
* Use Auto Scaling Groups with ALBs.
* Follow the Principle of Least Privilege for IAM permissions.

---

# 🧠 Key Takeaways

* Learned how to create an Application Load Balancer.
* Configured a Target Group.
* Registered EC2 instances.
* Understood health checks.
* Improved AWS networking and high-availability knowledge.

---

# 🚀 Skills Practiced

* Amazon EC2
* Application Load Balancer (ALB)
* Elastic Load Balancing
* Target Groups
* Health Checks
* AWS Networking

---
# 💡 Interview Questions

### Q1. What is an Application Load Balancer?

An Application Load Balancer distributes HTTP and HTTPS traffic across multiple targets at Layer 7 of the OSI model.

---

### Q2. What is a Target Group?

A Target Group is a collection of backend resources, such as EC2 instances, that receive traffic from a load balancer.

---

### Q3. What are Health Checks?

Health checks monitor the availability of registered targets. Unhealthy instances stop receiving traffic until they recover.

---

### Q4. What is the difference between an ALB and an NLB?

An ALB operates at Layer 7 and supports content-based routing, while an NLB operates at Layer 4 and is optimized for high-performance TCP/UDP traffic.

---

### Q5. Why should an ALB span multiple Availability Zones?

Deploying an ALB across multiple Availability Zones improves fault tolerance and ensures application availability if one Availability Zone becomes unavailable.

---

# 📌 Resources

* AWS Elastic Load Balancing Documentation
* AWS Application Load Balancer Guide
* AWS EC2 Documentation
* AWS Well-Architected Framework

---

# ⭐ Day 024 Summary

Today's hands-on exercise focused on configuring an **Application Load Balancer (ALB)** for an Amazon EC2 instance. I learned how to create Target Groups, register EC2 instances, configure listeners and health checks, and route traffic efficiently. These concepts are fundamental for building scalable, highly available, and production-ready applications on AWS.
