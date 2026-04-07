# 🛡️ AWS Secure Infrastructure & Monitoring Architecture

## 📌 Project Overview
This project demonstrates a production-grade, highly secure AWS network architecture deployed via **Infrastructure as Code (CloudFormation)**. It implements a "Defense in Depth" strategy using VPC Peering, strict Security Groups, stateless Network ACLs (NACLs), and proactive CloudWatch monitoring.

This architecture was designed with a focus on **Cloud Security** and **Continuous Monitoring**, showcasing the ability to build and observe resilient cloud environments.

## 🏗️ Architecture Highlights

### 1. Network Segmentation & VPC Peering
* **Multi-VPC Architecture:** Segregation of workloads into distinct VPCs (VPC A for production apps, VPC B for internal/management tools).
* **VPC Peering:** Secure, private communication between VPCs without routing traffic over the public internet.

### 2. Defense in Depth (Security)
* **Stateful Protection (Security Groups):** * Granular access control ensuring the Application servers only accept HTTP/S and SSH traffic from specific trusted sources (e.g., the Bastion Host subnet).
* **Stateless Protection (NACLs):** * Hardened network boundaries explicitly blocking unauthorized traffic at the subnet level across 9 distinct subnets.
  * Explicit rules for Ephemeral Ports (1024-65535) to allow return traffic for stateless connections, demonstrating deep OSI Model Layer 4 understanding.

### 3. Proactive Cloud Monitoring
* **CloudWatch Alarms:** Integrated monitoring for the core Application EC2 instance. 
* Configured an alarm to trigger upon `StatusCheckFailed` metric breaches, ensuring immediate visibility into underlying hardware or network degradation.

## 🛠️ Technologies & Tools
* **AWS CloudFormation** (IaC for reproducible deployments)
* **Amazon VPC** (Subnets, Route Tables, Peering, IGW)
* **AWS EC2 & Security** (Security Groups, Network ACLs, Bastion Host)
* **Amazon CloudWatch** (Metrics & Alarms)

## 🚀 How to Deploy (IaC)
1. Clone this repository.
2. Navigate to the AWS CloudFormation Console.
3. Select **Create Stack** -> **Upload a template file**.
4. Upload the templates in order (01, 02, 03).
5. When deploying the Stage 3 template, provide your current IP address in the `MyPublicIP` parameter to ensure secure SSH access to the Bastion host.
6. Click **Submit** and wait for `CREATE_COMPLETE`.

---
*Developed as a showcase of Cloud Infrastructure, Security, and Monitoring capabilities.*
