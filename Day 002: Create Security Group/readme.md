# 🚀 Day 002 – Create AWS EC2 Security Group

## 📖 Overview

Today, I learned about **AWS Security Groups**, one of the core networking and security features in Amazon EC2. A Security Group acts as a **virtual firewall** that controls inbound and outbound traffic for EC2 instances.

Understanding Security Groups is essential because they help protect cloud resources by allowing only authorized network traffic while blocking unauthorized access.

---

## 🎯 Objective

- Understand what a Security Group is.
- Learn how Security Groups protect EC2 instances.
- Create a new Security Group.
- Configure inbound and outbound rules.
- Understand common use cases and security best practices.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Cloud Provider | AWS |
| Service | Amazon EC2 |
| Feature | Security Groups |
| Platform | AWS Management Console |

---

## 📌 Task

Create a Security Group that allows secure access to an EC2 instance by configuring appropriate inbound and outbound rules.

---

## 🔒 What is a Security Group?

A **Security Group** is a virtual firewall that controls the network traffic to and from an EC2 instance.

It works by defining **rules** that specify:

- Which traffic is allowed into the instance (Inbound Rules)
- Which traffic is allowed out of the instance (Outbound Rules)

Unlike traditional firewalls, Security Groups are **stateful**, meaning if an incoming request is allowed, the response is automatically allowed without requiring an additional outbound rule.

---

## ⚙️ Steps Performed

1. Open the AWS Management Console.
2. Navigate to **Amazon EC2**.
3. Select **Security Groups** from the left navigation pane.
4. Click **Create Security Group**.
5. Provide:
   - Security Group Name
   - Description
   - VPC
6. Configure Inbound Rules.
7. Configure Outbound Rules.
8. Create the Security Group.
9. Attach it to an EC2 instance.

---

## 📚 Concepts Learned

### What are Inbound Rules?

Inbound rules control the traffic that is **allowed to enter** the EC2 instance.

Example:

| Protocol | Port | Purpose |
|----------|------|---------|
| SSH | 22 | Remote Login |
| HTTP | 80 | Web Traffic |
| HTTPS | 443 | Secure Web Traffic |

---

### What are Outbound Rules?

Outbound rules control the traffic that is **allowed to leave** the EC2 instance.

By default, AWS allows all outbound traffic.

Example:

| Protocol | Port | Purpose |
|----------|------|---------|
| All Traffic | All | Internet Access |

---

### Common Ports

| Port | Service |
|------|----------|
| 22 | SSH |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 8080 | Application Server |
| 6379 | Redis |

---

### Stateful Firewall

Security Groups are **stateful**.

Example:

If your laptop connects to an EC2 instance using SSH on port 22:

- Incoming SSH request is allowed.
- The return traffic is automatically allowed.
- No separate outbound rule is required for the response.

This makes Security Groups simpler and more secure.

---

## 🌍 Real-World Use Case

Imagine you're deploying a production web application.

You have:

- A Web Server
- An Application Server
- A Database Server

Each server has its own Security Group.

### Web Server

Allowed:

- HTTP (80)
- HTTPS (443)
- SSH (22) from Admin IP only

### Application Server

Allowed:

- Traffic only from the Web Server Security Group

### Database Server

Allowed:

- MySQL (3306) only from the Application Server Security Group

This layered approach improves security by ensuring each server only accepts the traffic it actually needs.

---

## 🔍 Verification

After creating the Security Group:

- Verify the Security Group appears in the EC2 Dashboard.
- Check inbound rules.
- Check outbound rules.
- Confirm the Security Group is attached to the EC2 instance.
- Test connectivity (SSH or HTTP).

---

## 🔐 Security Best Practices

- Allow only required ports.
- Restrict SSH (Port 22) to your public IP instead of `0.0.0.0/0`.
- Never expose database ports publicly.
- Use separate Security Groups for different application tiers.
- Follow the Principle of Least Privilege.
- Regularly review and remove unused rules.

---

## 🧠 Key Takeaways

- Learned what a Security Group is.
- Understood how inbound and outbound rules work.
- Learned that Security Groups are stateful firewalls.
- Created and configured a Security Group.
- Learned how Security Groups protect EC2 instances.
- Understood why restricting network access is important for cloud security.

---

## 🚀 Skills Practiced

- AWS EC2
- Security Groups
- Cloud Networking
- Firewall Configuration
- Cloud Security
- AWS Console
- Infrastructure Security

---

## 📂 Project Structure

```text
day-002-create-security-group/
│── README.md
```


## 📖 Example Security Group Configuration

| Rule Type | Protocol | Port | Source |
|-----------|----------|------|--------|
| SSH | TCP | 22 | My Public IP |
| HTTP | TCP | 80 | 0.0.0.0/0 |
| HTTPS | TCP | 443 | 0.0.0.0/0 |

---

## 💡 Interview Questions

### Q1. What is a Security Group?

A Security Group is a virtual firewall that controls inbound and outbound traffic for EC2 instances.

---

### Q2. Is a Security Group stateful or stateless?

Security Groups are **stateful**, meaning return traffic is automatically allowed if the initial request is permitted.

---

### Q3. Can one Security Group be attached to multiple EC2 instances?

Yes. A single Security Group can be attached to multiple EC2 instances.

---

### Q4. Can an EC2 instance have multiple Security Groups?

Yes. An EC2 instance can have multiple Security Groups attached, and AWS combines all their rules.

---

### Q5. What is the difference between a Security Group and a Network ACL?

| Security Group | Network ACL |
|----------------|-------------|
| Stateful | Stateless |
| Applied to EC2 instances | Applied to subnets |
| Supports only Allow rules | Supports Allow and Deny rules |
| Automatically allows return traffic | Requires explicit inbound and outbound rules |

---

## 📌 Resources

- AWS EC2 Documentation
- AWS Security Groups Documentation
- AWS VPC User Guide
- AWS Security Best Practices

---

## ⭐ Day 002 Summary

Today's hands-on exercise helped me understand one of the most important AWS networking concepts—**Security Groups**. I learned how Security Groups act as virtual firewalls, controlling inbound and outbound traffic to EC2 instances. I also explored how stateful firewall behavior simplifies network management, practiced configuring access rules, and learned best practices for securing cloud infrastructure using the Principle of Least Privilege.
