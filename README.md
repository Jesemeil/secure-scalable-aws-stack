## Architecture Diagram
   ![image](https://github.com/user-attachments/assets/a4002843-f846-4045-b555-8bf82174e6af)





# 🌐 Scalable, Secure, and Distributed Web Application Infrastructure on AWS

## 📜 Overview

This project demonstrates a **highly available**, **scalable**, and **secure** microservices-based infrastructure hosted on **Amazon Web Services (AWS)**. It is designed to serve modern full-stack applications with robust features including service orchestration, CI/CD integration, containerized deployments, and secure public-facing endpoints.

The infrastructure architecture leverages **multi-AZ (Availability Zone)** design patterns for fault tolerance and **decoupled services** for scalability. It integrates various AWS services such as EC2, Fargate, RDS, ALB, ECR, S3, CloudFront, Route 53, SNS, and more.

---

## 🚀 Architecture Summary

### 🔐 VPC and Subnet Design

* **VPC**: One Virtual Private Cloud hosting all components.
* **Private Subnet**: Hosts backend services like:

  * MongoDB (NoSQL database)
  * Amazon RDS (Relational Database Service)
  * RabbitMQ (Message broker)
  * AWS Fargate (Serverless containers for background tasks)
* **Public Subnet**: Hosts frontend & API services:

  * EC2 instances (via Auto Scaling Group)
  * ElasticSearch (for log and data search)
  * Keycloak (identity and access management)
  * AWS Amplify (frontend hosting)

---

## 🔧 Components and Their Roles

### 🐳 Containerized Services (Backend)

* **AWS Fargate**: Runs microservices in containers without managing servers.
* **Amazon ECR**: Hosts Docker container images used in Fargate.
* **MongoDB & RabbitMQ**: Stateless services running within the private subnet.
* **Amazon RDS**: Provides reliable, managed relational database services.

### 🌐 Frontend & API Layer (Public Subnet)

* **AWS Amplify**: Hosts the frontend application.
* **Keycloak**: Manages authentication and authorization.
* **ElasticSearch**: Provides search and analytics functionality.
* **Amazon EC2 with Auto Scaling Group**: Hosts APIs and dynamically scales based on demand.

---

### 🔐 Security and Routing

* **Application Load Balancer (ALB)**: Distributes inbound traffic across multiple targets (EC2, Amplify, etc.).
* **AWS WAF**: Web Application Firewall for blocking malicious traffic.
* **Amazon Route 53**: DNS service that routes user traffic to ALB.
* **HTTPS and Domain Management**: Secured via Route 53 + ACM (optional SSL cert).

---

### 🌍 Content Delivery and Storage

* **Amazon S3**: Stores static assets like images, stylesheets, etc.
* **Amazon CloudFront**: Content Delivery Network (CDN) for low-latency global content delivery.

---

### 🔁 Event-Driven Messaging

* **Amazon SNS**: Publishes notifications (e.g., alerts or system updates).
* **AWS Lambda**: Listens to SNS events and performs serverless logic (e.g., email alerts, DB updates).

---

## 🧪 Use Case Scenario

This infrastructure is ideal for:

* SaaS applications needing secure multi-tenant architecture
* Applications with CI/CD pipelines using container-based deployment
* E-commerce or media platforms needing high-speed static content delivery
* Web applications with large user bases needing horizontal scalability

---

## 🛡️ Security Best Practices

* **Isolation**: Private subnets for sensitive services.
* **IAM roles and policies**: Fine-grained access control across services.
* **WAF**: Protects ALB endpoints from Layer 7 attacks.
* **HTTPS via ALB and Route 53**: Ensures secure communication with end users.
* **Keycloak**: Externalizes identity management for better security and compliance.

---

## 🧭 High Availability and Scalability

* **Multi-AZ**: Ensures fault tolerance with resources spread across different AZs.
* **Auto Scaling Group**: Dynamically adjusts EC2 capacity to handle traffic fluctuations.
* **ElasticSearch and RDS**: Configured with replication and failover strategies.
* **Decoupled architecture**: Allows components to scale independently.

---

## 💡 Notable Features That Make This Architecture Stand Out

* ✅ **Microservices-Friendly**: Easily extendable via containerized Fargate tasks.
* ✅ **Hybrid Authentication**: Leverages Keycloak for OIDC and Amplify for fast login pages.
* ✅ **Fully Serverless Messaging**: SNS + Lambda setup eliminates polling and reduces cost.
* ✅ **Cloud-Native CI/CD**: ECR and Fargate streamline Docker-based pipelines.
* ✅ **Blazing Fast Frontend**: CloudFront + Amplify + S3 for speed and availability.
* ✅ **DevOps Ready**: Infra can be easily extended with Terraform, CloudFormation, or AWS CDK.

---

## 🧰 Tools Used

| Service      | Purpose                       |
| ------------ | ----------------------------- |
| VPC/Subnets  | Network isolation and routing |
| EC2          | Host APIs and compute logic   |
| ALB          | Load balancing                |
| WAF          | Threat protection             |
| RDS          | Relational database           |
| MongoDB      | Document store                |
| RabbitMQ     | Message broker                |
| Fargate      | Container orchestration       |
| ECR          | Docker image storage          |
| Route 53     | DNS and domain management     |
| Amplify      | Frontend hosting              |
| CloudFront   | CDN                           |
| S3           | Static asset storage          |
| SNS + Lambda | Serverless events and alerts  |
| Keycloak     | IAM / Authentication          |

---

## ⚙️ How to Deploy (Optional Add-on Section)

This architecture can be deployed using tools like:

* **Terraform** (recommended for reproducibility)
* **AWS CDK** (for infrastructure as code using TypeScript/Python)
* **CloudFormation** (native AWS templating)
* **Docker Compose + ECS CLI** (for container orchestration)

---

## Deployed Project URL: https://enum.africa/

---

## 🏁 Conclusion

This infrastructure was built with security, scalability, and speed at the forefront. It’s tailored for real-world production applications and aligns with AWS Well-Architected Framework best practices. Its decoupled and modular nature allows each component to be updated, scaled, and maintained independently—making it a future-ready solution.

