# 🚀 Day 022 – Configuring Secure SSH Access to an EC2 Instance

## 📖 Overview

Today, I learned how to configure **secure SSH access to an Amazon EC2 instance**. SSH (Secure Shell) is the primary method used by administrators and DevOps engineers to securely connect and manage Linux-based cloud servers.

This hands-on exercise focused on key-based authentication, Security Group configuration, and implementing secure remote access practices for EC2 instances.

---

## 🎯 Objective

* Understand SSH access in AWS EC2.
* Connect securely to EC2 instances using SSH keys.
* Configure Security Groups for SSH access.
* Verify secure remote connectivity.
* Follow AWS security best practices.

---

## 🛠️ Environment

| Component       | Details                     |
| --------------- | --------------------------- |
| Cloud Provider  | AWS                         |
| Service         | Amazon EC2                  |
| Access Method   | SSH                         |
| Authentication  | Key Pair                    |
| Network Control | Security Group              |
| Category        | Cloud Security & Networking |

---

# 📌 Task

Configure secure SSH access to an EC2 Linux instance using an SSH key pair and appropriate network permissions.

---

# 💻 Steps Performed

## 1️⃣ Create EC2 Key Pair

Navigate to:

```text
AWS Console → EC2 → Key Pairs
```

Click:

```text
Create Key Pair
```

Configure:

```
Name: devops-key
Type: RSA
Format: .pem
```

Download the private key file.

---

## 2️⃣ Configure Key Permissions

On Linux/Mac:

```bash
chmod 400 devops-key.pem
```

This prevents unauthorized users from reading the private key.

---

## 3️⃣ Configure Security Group

Navigate:

```
EC2 → Security Groups
```

Add inbound rule:

| Type | Port | Source |
| ---- | ---- | ------ |
| SSH  | 22   | My IP  |

Example:

```
TCP 22 → Your Public IP
```

Avoid:

```
0.0.0.0/0
```

for production environments.

---

## 4️⃣ Connect to EC2 Using SSH

Command:

```bash
ssh -i devops-key.pem ec2-user@<EC2-Public-IP>
```

Example:

```bash
ssh -i devops-key.pem ec2-user@54.xx.xx.xx
```

---

## 5️⃣ Verify Server Connection

After login:

```bash
hostname
```

Check OS:

```bash
cat /etc/os-release
```

Check user:

```bash
whoami
```

---

# 🔐 SSH Authentication Flow

```
Developer Machine
        |
        |
        | Private Key (.pem)
        |
        ↓
     SSH Request
        |
        ↓
AWS Security Group
        |
        ↓
EC2 Public IP
        |
        ↓
SSH Server (sshd)
        |
        ↓
Linux Shell Access
```

---

# 📚 Concepts Learned

## What is SSH?

SSH (Secure Shell) is a cryptographic network protocol used to securely access remote machines over an unsecured network.

---

## How SSH Key Authentication Works

SSH uses a public-private key pair:

### Private Key

* Stored on the user's machine.
* Must be protected.
* Used for authentication.

### Public Key

* Stored on the EC2 instance.
* Used to verify the private key.

Authentication flow:

```
Private Key
     |
     ↓
Authentication Request
     |
     ↓
Public Key Verification
     |
     ↓
Access Granted
```

---

# 🔑 EC2 Key Pair

AWS EC2 Key Pair contains:

| Component   | Location     |
| ----------- | ------------ |
| Private Key | User machine |
| Public Key  | EC2 instance |

AWS uses the public key to enable secure SSH authentication.

---

# 🌍 Real-World Use Case

A DevOps engineer needs to manage production EC2 servers.

Instead of using passwords:

* SSH keys are generated.
* Private keys are securely stored.
* Security Groups restrict SSH access.
* Administrators connect securely using key-based authentication.

This reduces the risk of brute-force attacks.

---

# 🔍 Verification

Verify:

✅ EC2 instance is running
✅ Security Group allows SSH traffic
✅ Private key permissions are correct
✅ SSH connection is successful
✅ Remote commands execute correctly

---

# 🔐 Security Best Practices

* Never share private SSH keys.
* Store keys securely.
* Use `chmod 400` permissions.
* Restrict SSH access to trusted IPs.
* Disable password authentication when possible.
* Use IAM and MFA for AWS account security.
* Rotate keys periodically.

---

# 🧠 Key Takeaways

* Learned how SSH access works in AWS EC2.
* Created and used EC2 Key Pairs.
* Configured Security Groups for secure access.
* Connected to EC2 instances using SSH.
* Improved cloud security knowledge.

---

# 🚀 Skills Practiced

* Amazon EC2
* SSH
* AWS Key Pair
* Security Groups
* Linux Remote Administration
* Cloud Security

---

# 💡 Interview Questions

### Q1. What is SSH?

SSH is a secure protocol used to remotely access and manage Linux servers.

---

### Q2. Why use SSH keys instead of passwords?

SSH keys provide stronger security because they use cryptographic authentication and are resistant to brute-force password attacks.

---

### Q3. What permissions should an SSH private key have?

The private key should have restricted permissions:

```bash
chmod 400 key.pem
```

---

### Q4. Which port does SSH use?

Default SSH port:

```
TCP 22
```

---

### Q5. What happens if Security Group does not allow port 22?

The SSH connection will fail because AWS blocks incoming SSH traffic before reaching the EC2 instance.

---

# 📌 Resources

* AWS EC2 Documentation
* AWS Key Pair Documentation
* AWS Security Group Documentation
* OpenSSH Documentation

---

# ⭐ Day 022 Summary

Today's hands-on exercise focused on configuring **secure SSH access to an EC2 instance**. I learned how AWS Key Pairs, Security Groups, and SSH authentication work together to provide secure remote server access. These skills are essential for cloud engineers, DevOps engineers, and system administrators managing AWS infrastructure.
