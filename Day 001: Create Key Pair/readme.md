# 🚀 Day 001 – AWS EC2 Key Pair

## 📖 Overview

Today, I learned about **AWS EC2 Key Pairs**, one of the fundamental security mechanisms used to securely access Amazon EC2 instances. A key pair consists of a **public key** stored by AWS and a **private key** that remains with the user.

Instead of using traditional passwords, AWS uses **SSH key-based authentication**, which is more secure and is considered a best practice for accessing Linux EC2 instances.

---

## 🎯 Objective

- Understand what an EC2 Key Pair is.
- Learn why key pairs are required.
- Create a new key pair in AWS.
- Download and securely store the private key.
- Understand how key pairs are used to connect to EC2 instances.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Cloud Provider | AWS |
| Service | Amazon EC2 |
| Region | Any AWS Region |
| Platform | AWS Management Console |

---

## 📌 Task

Create a new EC2 Key Pair that can be used to securely authenticate when launching and connecting to Linux EC2 instances.

---

## 🔑 What is an EC2 Key Pair?

An **EC2 Key Pair** is a pair of cryptographic keys used for secure authentication between your local machine and an EC2 instance.

It consists of:

- **Public Key** – Stored securely by AWS and placed on the EC2 instance during launch.
- **Private Key (.pem or .ppk)** – Downloaded once by the user and stored securely on their local machine.

When connecting to an EC2 instance, AWS verifies that both keys match before granting access.

---

## ⚙️ Steps Performed

1. Open the AWS Management Console.
2. Navigate to **EC2 Dashboard**.
3. Select **Key Pairs** from the left navigation pane.
4. Click **Create Key Pair**.
5. Enter a unique key pair name.
6. Select the key pair type:
   - RSA
   - ED25519
7. Select the private key format:
   - `.pem` (OpenSSH)
   - `.ppk` (PuTTY)
8. Click **Create Key Pair**.
9. Download and securely store the private key.

---

## 📚 Concepts Learned

### What is Public Key Cryptography?

Public key cryptography uses two mathematically related keys:

- Public Key
- Private Key

The public key can be shared freely, while the private key must always remain secret.

Authentication succeeds only when both keys match.

---

### Why Does AWS Use Key Pairs?

Instead of passwords, AWS uses SSH keys because they provide:

- Stronger authentication
- Better security
- Protection against brute-force attacks
- Password-less login
- Easier automation

---

### Types of Key Pairs

#### RSA

- Most widely supported
- Compatible with almost all SSH clients
- Commonly used in production

#### ED25519

- Newer algorithm
- Faster authentication
- Smaller key size
- Better security with modern cryptography

---

### Private Key Formats

#### PEM

Used with:

- OpenSSH
- Linux
- macOS
- Windows OpenSSH

#### PPK

Used with:

- PuTTY
- Windows systems

---

## 🔒 Security Best Practices

- Never share your private key.
- Store the private key securely.
- Download the private key immediately after creation (AWS cannot regenerate it later).
- Assign appropriate file permissions to the private key (`chmod 400 key.pem` on Linux/macOS).
- Create separate key pairs for different environments (Development, Testing, Production).
- Rotate keys periodically if required.

---

## 🌍 Real-World Use Case

Imagine a company launches multiple Linux web servers on AWS.

Instead of assigning passwords to each server, the DevOps team creates an EC2 Key Pair. Every authorized engineer receives the appropriate private key, allowing secure SSH access to the servers.

This approach improves security, simplifies server management, and reduces the risk of unauthorized access.

---

## 🔍 Verification

Verify that the key pair appears in the EC2 Console under **Key Pairs**.

Ensure the private key file (`.pem` or `.ppk`) has been downloaded and stored securely.

---

## 🧠 Key Takeaways

- Learned what an EC2 Key Pair is.
- Understood the difference between public and private keys.
- Learned how SSH authentication works in AWS.
- Created an EC2 Key Pair using the AWS Console.
- Understood the importance of securely storing the private key.
- Learned the difference between RSA and ED25519 key types.
- Learned the difference between PEM and PPK formats.

---

## 🚀 Skills Practiced

- AWS EC2
- Cloud Security
- SSH Authentication
- Public Key Cryptography
- Identity and Access Management
- AWS Console Navigation

---

## 📖 Commands Reference

Generate a new SSH key locally:

```bash
ssh-keygen -t rsa -b 4096
```

Set correct permissions on a PEM file:

```bash
chmod 400 my-key.pem
```

Connect to an EC2 instance:

```bash
ssh -i my-key.pem ec2-user@<public-ip>
```

---

## 💡 Interview Questions

**Q1. What is an EC2 Key Pair?**

A cryptographic key pair used to securely authenticate users when connecting to EC2 instances.

---

**Q2. Why can't AWS regenerate the private key?**

For security reasons, AWS stores only the public key. The private key is generated once and provided only during creation.

---

**Q3. What happens if you lose your private key?**

You cannot use it to access the instance. You must create a new key pair and update the instance using an alternative access method (such as AWS Systems Manager, EC2 Instance Connect, or by attaching the root volume to another instance).

---

**Q4. What is the difference between RSA and ED25519?**

RSA is widely supported and commonly used, while ED25519 is a newer algorithm offering faster performance and stronger security with smaller key sizes.

---

## 📌 Resources

- AWS EC2 Documentation
- AWS EC2 User Guide
- OpenSSH Documentation
- AWS Security Best Practices

---

## ⭐ Day 001 Summary

Today's hands-on exercise introduced me to one of the most fundamental concepts in AWS—**EC2 Key Pairs**. I learned how AWS uses public key cryptography to provide secure, password-less access to Linux EC2 instances. I also explored different key types, private key formats, and security best practices for managing SSH keys. Understanding EC2 Key Pairs is an essential skill for anyone working with AWS, Linux, and DevOps.
