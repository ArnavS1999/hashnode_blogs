---
title: "Interview Questions On Aws"
datePublished: Tue Jul 25 2023 12:31:25 GMT+0000 (Coordinated Universal Time)
cuid: clkia03tl000r0akydvdfdumb
slug: interview-questions-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690287218016/3b64fbba-12b4-4b81-8e64-903754f68059.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

## INTERVIEW QUESTIONS:

**Q1-&gt; Name 5 aws services you have used and what are the use cases?**

**A1-&gt;** AWS services I have used and their use cases:

**<mark>a. Amazon EC2:</mark>** Used for provisioning virtual servers in the cloud, suitable for various workloads and applications.

**<mark>b. Amazon S3:</mark>** Used for scalable storage of files, objects, and data, often used for backup, data archiving, and static website hosting.

**<mark>c. Amazon RDS:</mark>** Used for managed relational databases, providing easy setup, scalability, and automated backups for applications requiring a traditional database.

**<mark>d. AWS Lambda:</mark>** Used for serverless computing, allowing the execution of code without the need to provision or manage servers. e. Amazon CloudWatch: Used for monitoring and management of resources and applications, providing insights, alarms, and log aggregation.

**Q2-&gt; What are the tools used to send logs to the cloud environment?**

**A2-&gt;** Tools used to send logs to the cloud environment: Common tools for sending logs to the cloud environment include:

* **<mark>AWS CloudWatch Logs Agent:</mark>** Used to send logs from EC2 instances to CloudWatch Logs.
    
* **<mark>AWS CLI:</mark>** Can be used to upload logs to CloudWatch Logs or other services like S3.
    
* **<mark>Third-party log management tools:</mark>** Various third-party tools provide log aggregation and forwarding capabilities to cloud environments.
    

**Q3-&gt; What are IAM Roles? How do you create /manage them?**

**A3-&gt;** IAM Roles: IAM Roles in AWS are used to grant permissions to entities (such as EC2 instances or Lambda functions) to access AWS resources securely without using long-term credentials. To create/manage IAM Roles, you can:

* **<mark>Use the AWS Management Console:</mark>** Navigate to the IAM service, create a new IAM Role, and define the trusted entities and associated permissions.
    
* **<mark>Use AWS CLI: </mark>** Utilize the `aws iam create-role` and `aws iam attach-role-policy` commands to create and manage roles programmatically.
    

**Q4-&gt; How to upgrade or downgrade a system with zero downtime?**

**A4-&gt;** To upgrade or downgrade a system with zero downtime, you can utilize strategies like:

* **<mark>Load Balancer with multiple instances: </mark>** Create a new instance or group of instances with the updated/downgraded system, gradually shift traffic to the new instances, and then decommission the old instances.
    
* **<mark>Blue-Green Deployment:</mark>** Set up a parallel environment with the updated/downgraded system, perform testing and verification, and then switch the traffic to the new environment seamlessly.
    

**Q5-&gt; What is infrastructure as code and how do you use it?**

**A5-&gt;** Infrastructure as Code refers to the practice of defining and managing infrastructure resources (e.g., networks, servers, and services) using code. Tools like AWS CloudFormation or Terraform enable IaC by allowing you to write declarative code that specifies the desired infrastructure configuration. With IaC, you can automate resource provisioning, and version control infrastructure changes, and achieve consistent and reproducible deployments.

**Q6-&gt; What is a load balancer? Give scenarios of each kind of balancer based on your experience.**

**A6-&gt;** A load balancer is a networking component that distributes incoming network traffic across multiple servers or resources to ensure optimal utilization, high availability, and improved performance. There are three main types of load balancers in AWS: Application Load Balancer (ALB), Network Load Balancer (NLB), and Classic Load Balancer (CLB).

**<mark>a. Application Load Balancer (ALB):</mark>** Used for distributing traffic to multiple targets based on advanced application-level routing rules, ideal for microservices or containerized applications.

**<mark>b. Network Load Balancer (NLB):</mark>** Used for high-performance, ultra-low latency traffic distribution at the network layer, suitable for TCP/UDP-based applications with extreme scalability and performance requirements.

**<mark>c. Classic Load Balancer (CLB):</mark>** Used for distributing traffic across EC2 instances, suitable for basic load balancing needs.

**Q7-&gt; What is CloudFormation and why is it used for?**

**A7-&gt;** AWS CloudFormation is a service that enables you to define and provision infrastructure resources using a declarative template. It allows you to create and manage a collection of AWS resources as a single unit called a stack. CloudFormation templates are written in YAML or JSON and can be used to provision and update resources in a repeatable and automated manner.

**Q8-&gt; Difference between AWS CloudFormation and AWS Elastic Beanstalk?**

**A8-&gt;** Difference between AWS CloudFormation and AWS Elastic Beanstalk:

* **<mark>CloudFormation:</mark>** Focuses on infrastructure orchestration, allowing you to define and manage AWS resources. It provides a way to provision and configure resources in a controlled and automated manner.
    
* **<mark>Elastic Beanstalk:</mark>** Provides a platform-as-a-service (PaaS) offering, abstracting away the underlying infrastructure and simplifying the deployment and management of applications. It automates the setup and configuration of resources, making it easier to deploy applications without worrying about the underlying infrastructure details.
    

**Q9-&gt; What are the kinds of security attacks that can occur on the cloud? And how can we minimize them?**

**A9-&gt;** Types of security attacks on the cloud and minimizing them:

* **<mark>Unauthorized access:</mark>** Implement strong access controls, use multi-factor authentication (MFA), regularly rotate access keys, and encrypt sensitive data.
    
* **<mark>Data breaches:</mark>** Encrypt data at rest and in transit, regularly patch and update systems, and monitor and log access to sensitive data.
    
* **<mark>DDoS attacks:</mark>** Use AWS Shield to protect against DDoS attacks and employ load balancers to distribute traffic.
    
* **<mark>Insider threats:</mark>** Implement strict identity and access management policies, regularly audit and review user permissions, and enforce least privilege access.
    

**Q10-&gt; Can we recover the EC2 instance when we have lost the key?**

**A10-&gt;** Recovering an EC2 instance when the key is lost: If you lose the key to an EC2 instance, you won't be able to retrieve it. The recommended approach is to create a new key pair and then replace the existing key pair associated with the instance. This involves creating an AMI of the instance, launching a new instance from the AMI with the new key pair, and terminating the old instance.

**Q11-&gt; What is a gateway?**

**A11-&gt;** Gateway: In the context of AWS, a gateway refers to services like AWS API Gateway or AWS Direct Connect Gateway. These services act as entry points or connectors to enable access to other AWS resources or external networks securely and efficiently.

**Q12-&gt;What is the difference between Amazon Rds, Dynamodb, and Redshift?**

**A12-&gt;** Difference between Amazon RDS, DynamoDB, and Redshift:

* **<mark>Amazon RDS</mark>** (Relational Database Service): Managed service for deploying and operating relational databases like MySQL, PostgreSQL, or Oracle, providing automated backups, scalability, and high availability.
    
* **<mark>DynamoDB:</mark>** Fully managed NoSQL database service designed for fast and predictable performance at any scale, suitable for applications with high read/write requirements and flexible data models.
    
* **<mark>Redshift: </mark>** Fully managed data warehousing service designed for analyzing large-scale datasets, optimized for online analytical processing (OLAP), and offering fast query performance.
    

**Q13-&gt; Do you prefer to host a website on S3? What's the reason if your answer is either yes or no?**

**A13-&gt;** Hosting a website on S3 preference: Yes, hosting a website on S3 is often preferred for static websites. S3 provides reliable and scalable storage, high availability, and the ability to serve content globally using Amazon CloudFront for caching and distribution. Additionally, it offers cost-effectiveness, easy configuration, and integration with other AWS services.

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**