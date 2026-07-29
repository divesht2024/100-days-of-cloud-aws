
# 🚀 Day 026 – Configuring an EC2 Instance as a Web Server with Nginx

## 📖 Overview

Today, I learned how to launch an **Amazon EC2 instance** and configure it as a **web server using Nginx**. Nginx is a high-performance web server and reverse proxy widely used for hosting websites, APIs, and web applications.

This hands-on exercise strengthened my understanding of EC2 provisioning, Linux server administration, Nginx installation, security groups, and web hosting on AWS.

---

# 🎯 Objective

* Launch an Amazon EC2 instance.
* Connect to the instance using SSH.
* Install and configure Nginx.
* Allow HTTP traffic using Security Groups.
* Host a simple web page.
* Verify the web server is accessible from the internet.

---

# 🛠️ Environment

| Component        | Details                 |
| ---------------- | ----------------------- |
| Cloud Provider   | AWS                     |
| Compute Service  | Amazon EC2              |
| Operating System | Amazon Linux 2 / Ubuntu |
| Web Server       | Nginx                   |
| Protocol         | HTTP                    |
| Default Port     | 80                      |
| Category         | Compute & Web Hosting   |

---

# 📌 Task

Launch an EC2 instance, install Nginx, configure it as a web server, and verify that the hosted webpage is accessible using the instance's public IP address.

---

# 💻 Steps Performed

## 1️⃣ Launch an EC2 Instance

Navigate to:

```text id="zj3f8r"
AWS Console → EC2 → Launch Instance
```

Configure:

* Amazon Linux 2 (or Ubuntu)
* t2.micro / t3.micro
* Create or select an existing key pair
* Configure Security Group
* Allow:

  * SSH (22)
  * HTTP (80)

Launch the instance.

---

## 2️⃣ Connect to the EC2 Instance

Using SSH:

```bash id="7w5q2d"
ssh -i my-key.pem ec2-user@<EC2-Public-IP>
```

For Ubuntu:

```bash id="4j8m1x"
ssh -i my-key.pem ubuntu@<EC2-Public-IP>
```

---

## 3️⃣ Update the System

Amazon Linux:

```bash id="p8z2vn"
sudo yum update -y
```

Ubuntu:

```bash id="g3m7ra"
sudo apt update && sudo apt upgrade -y
```

---

## 4️⃣ Install Nginx

Amazon Linux:

```bash id="k5d9te"
sudo amazon-linux-extras install nginx1 -y
```

If using Amazon Linux 2023:

```bash id="x2n6pf"
sudo dnf install nginx -y
```

Ubuntu:

```bash id="m1r4hk"
sudo apt install nginx -y
```

---

## 5️⃣ Start and Enable Nginx

```bash id="c9y5qb"
sudo systemctl enable nginx
sudo systemctl start nginx
```

Verify the service:

```bash id="r4k8xm"
sudo systemctl status nginx
```

---

## 6️⃣ Configure a Simple Web Page

Replace the default page:

```bash id="t7q3lw"
echo "<h1>Welcome to My AWS Nginx Server</h1>" | sudo tee /usr/share/nginx/html/index.html
```

---

## 7️⃣ Verify Security Group

Ensure the Security Group allows:

| Protocol | Port | Source    |
| -------- | ---- | --------- |
| SSH      | 22   | Your IP   |
| HTTP     | 80   | 0.0.0.0/0 |

---

## 8️⃣ Access the Website

Open a browser:

```text id="f2d8mn"
http://<EC2-Public-IP>
```

Or use curl:

```bash id="v6x1as"
curl http://<EC2-Public-IP>
```

Expected output:

```html id="q8n5tv"
<h1>Welcome to My AWS Nginx Server</h1>
```

---

# 📚 Concepts Learned

## What is Amazon EC2?

Amazon EC2 (Elastic Compute Cloud) is a service that provides scalable virtual servers in the AWS Cloud.

---

## What is Nginx?

Nginx is an open-source web server that can also function as a reverse proxy, load balancer, and HTTP cache.

---

## EC2 Web Server Architecture

```text id="s9h4vr"
                Internet
                    |
                    |
            Security Group (HTTP 80)
                    |
                    |
              Amazon EC2 Instance
                    |
                    |
                 Nginx Server
                    |
                    |
               Static Website
```

---

## Nginx Directory Structure

| Directory             | Purpose                     |
| --------------------- | --------------------------- |
| /usr/share/nginx/html | Default website files       |
| /etc/nginx/nginx.conf | Main configuration file     |
| /etc/nginx/conf.d/    | Virtual host configurations |
| /var/log/nginx/       | Access and error logs       |

---

# 🌍 Real-World Use Case

A startup hosts its company website on AWS.

The DevOps team:

* Launches an EC2 instance.
* Installs Nginx.
* Deploys the website.
* Opens port 80 in the Security Group.
* Makes the website available over the internet.

As traffic grows, the server can later be placed behind an Application Load Balancer and Auto Scaling Group.

---

# 🔍 Verification

Verify that:

✅ EC2 instance is running.
✅ Nginx service is active.
✅ Security Group allows HTTP traffic.
✅ Website loads using the public IP.
✅ Default webpage is replaced with custom content.

Useful commands:

```bash id="a5q9mz"
systemctl status nginx
```

```bash id="e7w4hp"
curl http://localhost
```

```bash id="j1d6kn"
ss -tulnp | grep 80
```

---

# 🔐 Best Practices

* Restrict SSH access to your IP address.
* Keep the operating system updated.
* Enable HTTPS using SSL/TLS for production.
* Monitor server health using CloudWatch.
* Use an Application Load Balancer for high availability.
* Regularly back up application data and configurations.

---

# 🧠 Key Takeaways

* Launched an EC2 instance.
* Installed and configured Nginx.
* Hosted a static web page.
* Configured Security Groups.
* Verified public web access.
* Learned the basics of hosting web applications on AWS.

---

# 🚀 Skills Practiced

* Amazon EC2
* Nginx
* Linux Administration
* SSH
* Security Groups
* Web Hosting

---

# 💡 Interview Questions

### Q1. What is Nginx?

Nginx is an open-source web server that can also act as a reverse proxy, load balancer, and HTTP cache.

---

### Q2. What is the default HTTP port used by Nginx?

**Port 80**

---

### Q3. How do you check if the Nginx service is running?

```bash
systemctl status nginx
```

---

### Q4. Which Security Group rule is required to access a website hosted on an EC2 instance?

Allow **Inbound HTTP (TCP Port 80)** from the appropriate source (typically `0.0.0.0/0` for a public website).

---

### Q5. Where is the default website content stored in Nginx?

```text
/usr/share/nginx/html
```

---

# 📌 Resources

* AWS EC2 Documentation
* AWS Security Groups Documentation
* Nginx Official Documentation
* Amazon Linux User Guide

---

# ⭐ Day 026 Summary

Today's hands-on exercise focused on **configuring an Amazon EC2 instance as a web server using Nginx**. I learned how to launch an EC2 instance, connect via SSH, install and configure Nginx, host a static website, configure Security Groups for HTTP access, and verify the application through the instance's public IP. These are foundational skills for deploying and managing web applications on AWS.
