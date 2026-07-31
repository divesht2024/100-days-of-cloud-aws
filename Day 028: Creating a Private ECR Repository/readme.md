
# 🚀 Day 028 – Creating a Private Amazon ECR Repository

## 📖 Overview

Today, I learned how to create a **Private Amazon Elastic Container Registry (ECR) Repository** to securely store and manage Docker container images. Amazon ECR is a fully managed container image registry that integrates seamlessly with Amazon ECS, Amazon EKS, AWS Lambda, and CI/CD pipelines.

This hands-on exercise strengthened my understanding of container image management, Docker authentication, image versioning, and secure image storage in AWS.

---

# 🎯 Objective

* Understand Amazon ECR.
* Create a Private ECR Repository.
* Authenticate Docker with Amazon ECR.
* Build and tag a Docker image.
* Push the image to ECR.
* Verify the uploaded container image.

---

# 🛠️ Environment

| Component         | Details                                 |
| ----------------- | --------------------------------------- |
| Cloud Provider    | AWS                                     |
| Service           | Amazon Elastic Container Registry (ECR) |
| Repository Type   | Private                                 |
| Container Runtime | Docker                                  |
| AWS CLI           | Version 2                               |
| Category          | Containers & DevOps                     |

---

# 📌 Task

Create a private Amazon ECR repository, authenticate Docker using AWS CLI, push a Docker image to the repository, and verify that the image is successfully stored.

---

# 💻 Steps Performed

## 1️⃣ Create a Private ECR Repository

Navigate to:

```text id="ecr001"
AWS Console → Amazon ECR → Repositories → Create Repository
```

Configuration:

| Setting          | Value                 |
| ---------------- | --------------------- |
| Visibility       | Private               |
| Repository Name  | my-private-repo       |
| Tag Immutability | Disabled (Default)    |
| Scan on Push     | Enabled (Recommended) |
| Encryption       | AES-256 (Default)     |

Click **Create Repository**.

---

## 2️⃣ Verify Repository Creation

Navigate to:

```text id="ecr002"
Amazon ECR → Repositories
```

Verify:

* Repository Name
* Repository URI
* Encryption
* Scan on Push Status

Example Repository URI:

```text id="ecr003"
123456789012.dkr.ecr.us-east-1.amazonaws.com/my-private-repo
```

---

## 3️⃣ Configure AWS CLI

Verify AWS CLI configuration:

```bash id="ecr004"
aws configure
```

Provide:

* AWS Access Key
* AWS Secret Key
* Region
* Output Format

Verify identity:

```bash id="ecr005"
aws sts get-caller-identity
```

---

## 4️⃣ Authenticate Docker to Amazon ECR

Run:

```bash id="ecr006"
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com
```

Expected output:

```text id="ecr007"
Login Succeeded
```

---

## 5️⃣ Create a Sample Docker Application

Example Dockerfile:

```dockerfile id="ecr008"
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```

Example HTML:

```html id="ecr009"
<h1>Welcome to Amazon ECR!</h1>
```

---

## 6️⃣ Build Docker Image

```bash id="ecr010"
docker build -t my-nginx-app .
```

Verify:

```bash id="ecr011"
docker images
```

---

## 7️⃣ Tag the Docker Image

```bash id="ecr012"
docker tag my-nginx-app:latest <ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/my-private-repo:latest
```

---

## 8️⃣ Push Image to Amazon ECR

```bash id="ecr013"
docker push <ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/my-private-repo:latest
```

Wait for upload completion.

---

## 9️⃣ Verify Image

Navigate to:

```text id="ecr014"
Amazon ECR → Repositories → my-private-repo
```

Verify:

* Image Tag
* Image Digest
* Push Time
* Image Size
* Scan Status

---

# 📚 Concepts Learned

## What is Amazon ECR?

Amazon Elastic Container Registry (ECR) is a fully managed container image registry that stores, manages, scans, and distributes Docker and OCI-compatible container images.

---

## What is a Private Repository?

A private repository stores container images securely and allows access only to authorized AWS IAM users, roles, or services.

---

## Amazon ECR Workflow

```text id="ecr015"
          Developer
               |
        Build Docker Image
               |
        Docker Login (ECR)
               |
          Tag Docker Image
               |
         Push Image to ECR
               |
      Amazon ECR Repository
               |
      ECS / EKS / Lambda Pull Image
```

---

## Benefits of Amazon ECR

* Fully managed container registry
* Secure IAM integration
* Image vulnerability scanning
* High availability
* Encryption at rest
* Lifecycle policies
* Integration with ECS, EKS, Lambda, and CodeBuild

---

# 🌍 Real-World Use Case

A DevOps team builds Docker images using Jenkins.

The pipeline:

* Builds the application
* Creates a Docker image
* Pushes the image to Amazon ECR
* Amazon ECS pulls the latest image
* Deploys the updated application automatically

This creates a secure and automated CI/CD workflow.

---

# 🔍 Verification

Verify:

✅ Repository created successfully.
✅ Docker authentication succeeded.
✅ Docker image built successfully.
✅ Image tagged correctly.
✅ Image pushed to ECR.
✅ Image visible in the AWS Console.

Useful commands:

```bash id="ecr016"
aws ecr describe-repositories
```

```bash id="ecr017"
aws ecr list-images --repository-name my-private-repo
```

```bash id="ecr018"
docker images
```

---

# 🔐 Best Practices

* Enable image scanning on push.
* Use IAM roles instead of long-term access keys where possible.
* Apply least-privilege IAM permissions.
* Enable tag immutability for production repositories.
* Use lifecycle policies to delete unused images.
* Encrypt repositories using AWS-managed or customer-managed KMS keys.
* Use descriptive image tags instead of relying only on `latest`.

---

# 🧠 Key Takeaways

* Created a private Amazon ECR repository.
* Authenticated Docker with AWS.
* Built and tagged a Docker image.
* Uploaded the image securely to ECR.
* Learned the container image lifecycle in AWS.

---

# 🚀 Skills Practiced

* Amazon ECR
* Docker
* AWS CLI
* IAM Authentication
* Container Image Management
* DevOps Fundamentals

---

# 💡 Interview Questions

### Q1. What is Amazon ECR?

Amazon Elastic Container Registry (ECR) is a fully managed AWS service for storing, managing, scanning, and distributing container images.

---

### Q2. What is the difference between a Public and a Private ECR repository?

| Private ECR                    | Public ECR                              |
| ------------------------------ | --------------------------------------- |
| Requires authentication        | Publicly accessible                     |
| IAM-based access control       | Open for public image pulls             |
| Best for internal applications | Best for open-source image distribution |

---

### Q3. How do you authenticate Docker with Amazon ECR?

```bash id="ecr020"
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <account-id>.dkr.ecr.<region>.amazonaws.com
```

---

### Q4. Why should you enable "Scan on Push"?

It automatically scans container images for known vulnerabilities when they are pushed to the repository, helping identify security issues early.

---

### Q5. Which AWS services commonly use Amazon ECR?

* Amazon ECS
* Amazon EKS
* AWS Lambda (container images)
* AWS CodeBuild
* AWS CodePipeline

---

# 📌 Resources

* AWS Amazon ECR Documentation
* Docker Documentation
* AWS CLI Documentation
* Amazon ECS Documentation
* Amazon EKS Documentation

---

# ⭐ Day 028 Summary

Today's hands-on exercise focused on **creating and using a Private Amazon ECR Repository**. I learned how to create a secure container registry, authenticate Docker with AWS, build and tag Docker images, push them to Amazon ECR, and verify successful uploads. These skills are fundamental for containerized application deployments and modern DevOps CI/CD pipelines on AWS.
