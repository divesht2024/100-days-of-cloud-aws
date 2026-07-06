# 🚀 Day 007 – Change Amazon EC2 Instance Type

## 📖 Overview

Today, I learned how to **change the instance type of an Amazon EC2 instance**. Instance types determine the CPU, memory, storage, and networking capacity available to an EC2 instance. AWS allows you to resize an instance by changing its type, making it easy to scale resources up or down based on workload requirements.

This lab helped me understand vertical scaling in AWS and the steps required to safely modify an EC2 instance type.

---

## 🎯 Objective

- Understand what an EC2 instance type is.
- Learn why instance types need to be changed.
- Stop an EC2 instance safely.
- Change the instance type.
- Restart the instance and verify the changes.
- Understand real-world scaling scenarios.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Cloud Provider | AWS |
| Service | Amazon EC2 |
| Platform | AWS Management Console |
| Category | Compute |

---

## 📌 Task

Modify an existing EC2 instance by changing its **instance type** to meet new performance or resource requirements.

---

## 💻 Steps Performed

1. Open the **AWS Management Console**.
2. Navigate to **Amazon EC2**.
3. Select the desired EC2 instance.
4. Stop the instance.
5. Wait until the instance state changes to **Stopped**.
6. Click **Actions → Instance Settings → Change Instance Type**.
7. Select the new instance type.
8. Save the changes.
9. Start the EC2 instance.
10. Verify the new instance type.

---

## 📚 Concepts Learned

### What is an EC2 Instance Type?

An EC2 instance type defines the hardware configuration of an EC2 instance, including:

- Virtual CPUs (vCPUs)
- Memory (RAM)
- Network performance
- Storage performance

Different instance types are optimized for different workloads.

---

### Common Instance Families

| Family | Use Case |
|---------|----------|
| T (Burstable) | General-purpose, development, testing |
| M (General Purpose) | Balanced CPU and memory workloads |
| C (Compute Optimized) | CPU-intensive applications |
| R (Memory Optimized) | Databases and in-memory caching |
| X | High-memory enterprise workloads |
| G / P | GPU-based machine learning and graphics |

---

### Why Change an Instance Type?

Changing the instance type allows you to:

- Increase CPU performance
- Increase memory capacity
- Improve network throughput
- Reduce costs by downsizing
- Match resources to application needs

This process is known as **Vertical Scaling (Scaling Up or Scaling Down).**

---

### Vertical Scaling vs Horizontal Scaling

| Vertical Scaling | Horizontal Scaling |
|------------------|--------------------|
| Change instance size | Add more instances |
| Increase CPU/RAM | Increase the number of servers |
| Simpler for single-instance applications | Better for highly available applications |

---

## 🌍 Real-World Use Case

Imagine an e-commerce application running on a **t2.micro** instance.

During a major sale event, CPU and memory usage increase significantly, causing slower response times.

Instead of rebuilding the server, the DevOps team stops the instance and upgrades it to a **t3.medium**.

This provides additional CPU and memory resources, allowing the application to handle increased traffic more efficiently.

---

## 🔍 Verification

After changing the instance type:

- Verify the instance is in the **Running** state.
- Check the **Instance Type** in the EC2 console.
- Confirm that the application starts successfully.
- Test SSH connectivity.
- Monitor CPU and memory performance using Amazon CloudWatch.

---

## 🔐 Best Practices

- Stop the instance before changing the instance type (unless using supported live resize options).
- Choose the smallest instance type that meets workload requirements.
- Monitor resource utilization with CloudWatch.
- Test applications after resizing.
- Consider Auto Scaling for dynamic workloads.
- Review pricing before selecting a larger instance type.

---

## 🧠 Key Takeaways

- Learned what an EC2 instance type is.
- Understood the purpose of different instance families.
- Learned how to safely change an instance type.
- Understood the concept of vertical scaling.
- Learned how resizing improves application performance.
- Gained hands-on experience managing AWS compute resources.

---

## 🚀 Skills Practiced

- Amazon EC2
- AWS Compute
- Instance Management
- Vertical Scaling
- Cloud Infrastructure
- AWS Console Navigation
- Cloud Resource Optimization

---


## 📖 Key Terms

| Term | Description |
|------|-------------|
| EC2 Instance | A virtual server running in AWS |
| Instance Type | Defines CPU, memory, storage, and networking resources |
| Vertical Scaling | Increasing or decreasing resources of a single instance |
| vCPU | Virtual CPU assigned to an EC2 instance |
| CloudWatch | AWS monitoring service for metrics and alarms |

---

## 💡 Interview Questions

### Q1. What is an EC2 instance type?

An EC2 instance type defines the compute, memory, storage, and networking resources available to an EC2 instance.

---

### Q2. Why would you change an EC2 instance type?

To increase or decrease CPU, memory, or networking capacity based on workload requirements or to optimize costs.

---

### Q3. Do you need to stop an EC2 instance before changing its type?

Yes, in most cases the instance must be stopped before changing its instance type through the AWS Management Console.

---

### Q4. What is the difference between vertical scaling and horizontal scaling?

- **Vertical Scaling:** Increase or decrease resources of a single server.
- **Horizontal Scaling:** Add or remove multiple servers to distribute the workload.

---

### Q5. Which AWS service helps monitor EC2 performance after resizing?

Amazon **CloudWatch** provides metrics such as CPU utilization, network traffic, and disk activity to monitor EC2 instance performance.

---

## 📌 Resources

- AWS Amazon EC2 Documentation
- AWS EC2 Instance Types Documentation
- AWS CloudWatch Documentation
- AWS Well-Architected Framework

---

## ⭐ Day 007 Summary

Today's hands-on exercise helped me understand how to **change the instance type of an Amazon EC2 instance**, an essential skill for managing cloud infrastructure. I learned how AWS enables vertical scaling by allowing instances to be resized with minimal effort, ensuring applications have the right amount of compute and memory resources while optimizing performance and cost.
