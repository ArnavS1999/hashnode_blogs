---
title: "ECS[Amazon Elastic Container Service]"
datePublished: Mon Jul 10 2023 16:41:45 GMT+0000 (Coordinated Universal Time)
cuid: cljx3c9t2000a09l705gabix5
slug: ecsamazon-elastic-container-service
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689007017758/f1eef93e-4031-4c95-a5ea-2d2c391739a5.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

## What is ECS?

* ECS (Elastic Container Service) is a fully-managed container orchestration service provided by Amazon Web Services (AWS). It allows you to run and manage Docker containers on a cluster of virtual machines (EC2 instances) without having to manage the underlying infrastructure.
    

With ECS, you can easily deploy, manage, and scale your containerized applications using the AWS Management Console, the AWS CLI, or the API. ECS supports both "Fargate" and "EC2 launch types", which means you can run your containers on AWS-managed infrastructure or your own EC2 instances.

ECS also integrates with other AWS services, such as Elastic Load Balancing, Auto Scaling, and Amazon VPC, allowing you to build scalable and highly available applications. Additionally, ECS has support for Docker Compose and Kubernetes, making it easy to adopt existing container workflows.

Overall, ECS is a powerful and flexible container orchestration service that can help simplify the deployment and management of containerized applications in AWS.

## Difference between EKS and ECS?

* EKS (Elastic Kubernetes Service) and ECS (Elastic Container Service) are both container orchestration platforms provided by Amazon Web Services (AWS). While both platforms allow you to run containerized applications in the AWS cloud, there are some differences between the two.
    

**<mark>Architecture</mark>**<mark>:</mark> ECS is based on a centralized architecture, where there is a control plane that manages the scheduling of containers on EC2 instances. On the other hand, EKS is based on a distributed architecture, where the Kubernetes control plane is distributed across multiple EC2 instances.

**<mark>Kubernetes Support</mark>**<mark>:</mark> EKS is a fully managed Kubernetes service, meaning that it supports Kubernetes natively and allows you to run your Kubernetes workloads on AWS without having to manage the Kubernetes control plane. ECS, on the other hand, has its own orchestration engine and does not support Kubernetes natively.

**<mark>Scaling</mark>**<mark>:</mark> EKS is designed to automatically scale your Kubernetes cluster based on demand, whereas ECS requires you to configure scaling policies for your tasks and services.

**<mark>Flexibility</mark>**<mark>:</mark> EKS provides more flexibility than ECS in terms of container orchestration, as it allows you to customize and configure Kubernetes to meet your specific requirements. ECS is more restrictive in terms of the options available for container orchestration.

**<mark>Community</mark>**<mark>:</mark> Kubernetes has a large and active open-source community, which means that EKS benefits from a wide range of community-driven development and support. ECS, on the other hand, has a smaller community and is largely driven by AWS itself.

In summary, EKS is a good choice if you want to use Kubernetes to manage your containerized workloads on AWS, while ECS is a good choice if you want a simpler, more managed platform for running your containerized applications.

## **Task :**

### **Set up ECS (Elastic Container Service) by setting up Nginx on ECS.**

To set up ECS (Elastic Container Service) and deploy Nginx on ECS, you can follow these steps:

**<mark>Create an ECS Cluster:</mark>**

* Sign in to the AWS Management Console and Open the ECS service.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688983052623/c6b5fe3c-4aa8-4b6c-a350-8266621673c0.png align="center")

* Configure the cluster settings, including the cluster name and networking options.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688983226606/992b578a-aefc-40f1-aa0e-112da3811916.png align="center")

* Choose the cluster type that suits your requirements (e.g., EC2 or Fargate).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688983294515/d8022bd4-36f3-4156-8b5e-d4b0030b2cd3.png align="center")

* Review the settings and create the ECS cluster.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688983595656/29153737-e62f-43d9-a90d-03c1484fb607.png align="center")

* Logs
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688983652526/b9880837-8497-43ef-908e-44ba3088b9af.png align="center")

**<mark>Create a Task Definition:</mark>**

* In the ECS service, navigate to "Task Definitions" in the left navigation pane.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688983846343/384b90c5-b965-42a2-bd0b-512b27db6742.png align="center")

* Click on "Create new Task Definition".
    
* Configure the task definition details, including the task name and container definitions.
    
* Define the container properties, such as the image, port mappings, environment variables, and any required volumes.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688984175785/a9715800-8081-4560-b8be-204d1459b710.png align="center")

* For container images URL refer to this website [ECR Public Gallery](https://gallery.ecr.aws/nginx/nginx).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688984329611/ce1c77f2-5758-4365-807f-d69377e64158.png align="center")

* After creating the task definition, click on "Next".
    
* Choose the App environment, either EC2 or Fargate and select the task definition you created.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688995826552/b281edf5-a55d-4887-9e67-8cc2e5fb66f0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688995343321/29b1d919-bc57-4d27-b32c-252fa3677761.png align="center")

* Review and click on **Create.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688995887502/71c73ec6-7e64-4baf-b53f-fe559df3450f.png align="center")

**Now we need to create a service**

* Go to the Clusters and create services.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688995972377/da0dd530-9ab3-456c-a543-bf20d971926c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688996098405/74bed4fb-e7f5-4836-8873-815c362f6506.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688996151225/8c70fb66-7198-4a5c-9482-3b73f2818556.png align="center")

* Deployment Configuration
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688996230426/47df7cb5-f367-4ffe-9eda-fdec45a4bd2c.png align="center")

* Review and click on **Create**.
    
* After review, we can see the service is created successfully
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688998128319/272cc88b-63c4-485d-a47c-9fb83e7ea8f0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688998185020/fa0a7366-2f15-4267-ac98-9ef9089513ee.png align="center")

**Access Nginx on ECS:**

* Go to **Clusters** -&gt; **nginx** -&gt;**Tasks** -&gt; click on service(fd39609e7e784578b80bfd8cd4f0ba5c).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688998375373/fce5d9b9-742a-42c3-95cc-2f065db8e056.png align="center")

* Once the service is running, obtain the public IP.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688998916058/2f44c464-d9f2-4900-bd0a-9692a89b86fd.png align="center")
    
    Copy the Public IP and paste it into the browser.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688999029644/506f035f-abb3-4128-bd6d-07efdcfeda35.png align="center")

**<mark>Congratulations Nginx server is live!!</mark>**

<mark>Overall, ECS provides a scalable, reliable, and efficient platform for running containerized applications. It simplifies the deployment, management, and scaling of your applications, allowing you to focus on developing and delivering your software without worrying about the underlying infrastructure.</mark>

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**