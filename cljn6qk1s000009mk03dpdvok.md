---
title: "AWS EC2 Automation"
datePublished: Mon Jul 03 2023 18:19:09 GMT+0000 (Coordinated Universal Time)
cuid: cljn6qk1s000009mk03dpdvok
slug: aws-ec2-automation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688407377648/5215eb02-1aa1-4b44-a81b-d5ef7fef7f80.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

![AWS](https://camo.githubusercontent.com/044fdb1d1f52d7886ec1b833299b827a8bccd6a86e48957e05ef4ad24e0f7704/68747470733a2f2f7777772e6567696e6e6f766174696f6e732e636f6d2f626c6f672f77702d636f6e74656e742f75706c6f6164732f323032312f30392f416d617a6f6e2d4157532d436c6f75642d546f70696d6167652d312e6a7067 align="center")

### **AWS EC2**

* Amazon EC2 is a service provided by AWS that allows you to rent virtual servers in the cloud.
    
* EC2 instances are virtual computers that you can configure and use like physical computers.
    
* You can choose from a wide range of instance types with varying CPU, memory, and storage capacities.
    
* EC2 offers features like auto-scaling to automatically adjust the number of instances based on demand.
    
* You can connect to EC2 instances remotely over the internet and have full control over them.
    
* EC2 integrates with other AWS services for additional functionalities, such as storage and databases.
    
* You are charged based on the usage of EC2 instances, with different pricing options available.
    
* EC2 enables you to build and deploy applications in the cloud efficiently and at scale.
    
* It provides flexibility, scalability, and control over your computing resources.
    
* EC2 is commonly used for hosting websites, running web applications, analyzing data, and running enterprise software.
    

### **Automation in EC2**

Amazon EC2 or Amazon Elastic Compute Cloud can give you secure, reliable, high-performance, and cost-effective computing infrastructure to meet demanding business needs.

**Automation in EC2 refers to the process of automating various tasks and workflows related to Amazon EC2 (Elastic Compute Cloud) instances. EC2 automation allows you to streamline and simplify the management, provisioning, configuration, and scaling of EC2 instances, resulting in improved efficiency and reduced manual effort.**

### **Launch template in AWS EC2:**

* You can make a launch template with the configuration information you need to start an instance. You can save launch parameters in launch templates so you don't have to type them in every time you start a new instance.
    
* For example, a launch template can have the AMI ID, instance type, and network settings that you usually use to launch instances.
    
* You can tell the Amazon EC2 console to use a certain launch template when you start an instance.
    

### **Instance Types:**

Amazon EC2 has a large number of instance types that are optimized for different uses. The different combinations of CPU, memory, storage and networking capacity in instance types give you the freedom to choose the right mix of resources for your apps. Each instance type comes with one or more instance sizes, so you can adjust your resources to meet the needs of the workload you want to run.

### **AMI:**

An Amazon Machine Image (AMI) is an image that AWS supports and keeps up to date. It contains the information needed to start an instance. When you launch an instance, you must choose an AMI. When you need multiple instances with the same configuration, you can launch them from a single AMI.

---

### Task1:

* ### **Create a launch template with Ubuntu AMI and t2.micro instance type with Jenkins and Docker setup (You can use the Day 39 User data script for installing the required tools.**
    
* Log in to the AWS Management Console.
    
* Go to the EC2 service.
    
* Click on **"Launch Templates"** in the left-hand menu.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688401523408/6c947a24-455f-43ba-b4ed-8ee9db767690.png align="center")

* Click on **"Create launch template"** to start creating a new launch template.
    
* Enter a name for the launch template (e.g., **"Jenkins-Docker"**).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688401632978/fcbc16c8-afa7-4346-a1f0-c8a9846cd535.png align="center")

* Choose the Ubuntu AMI from the **"AMI ID"** dropdown.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688401766107/3c7c773b-20e9-40a7-95d3-8a41f608ab4c.png align="center")

* Scroll down to the **"Instance type"** section and select **"t2.micro"** from the dropdown.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688401841733/85d9feed-e731-4573-b95e-8df44f1a378e.png align="center")

* In the **"Advanced details"** section, expand the **"User data"** section.
    

```yaml
#!/bin/bash
 sudo apt update
 sudo apt install openjdk-11-jre -y

 curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
   /usr/share/keyrings/jenkins-keyring.asc > /dev/null
 echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
   https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
   /etc/apt/sources.list.d/jenkins.list > /dev/null
 sudo apt-get update
 sudo apt-get install jenkins -y

 sudo systemctl enable jenkins
 sudo systemctl start jenkins

 sudo apt-get update
 sudo apt-get install docker.io -y
 sudo systemctl start docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688403566149/05d8ca35-543f-44ba-8edf-cc7a65d9ffc7.png align="center")

* click on **"Create launch template"** to create the launch template.
    

Now you have a launch template with the specified Ubuntu AMI, t2.micro instance type, and the user data script for setting up Jenkins and Docker.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688403755747/f6cfd7d8-4d6b-456b-a4f8-107b8070e67c.png align="center")

* **Create 3 Instances using Launch Template, there must be an option that shows the number of instances to be launched.**
    
* Click on "**Launch instance from the template"**.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688403854914/c4f53368-cf0e-43e1-8d54-331ad58e6ea2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688403912790/426c9674-7392-4a84-833f-d87637df23c5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688403945089/80da6568-eeb9-4b71-93c2-9bfc5c51aea0.png align="center")

* Click on **"Launch Instance"** and after sometimes we can see the other 3 server is up and running
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688404158410/4108071f-bf72-43d8-898c-4bc69172d97f.png align="center")

---

### **Creating an Auto-Scaling group**

* To create an Auto Scaling group in AWS, which automatically scales the number of EC2 instances based on the specified conditions, follow these steps
    
* Log in to the AWS Management Console.
    
* Go to the EC2 service.
    
* Click on **"Auto Scaling Groups"** in the left-hand menu.
    
* Click on **"Create Auto Scaling group"** to start creating a new Auto Scaling group.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688404541916/30f6fe01-4d87-400f-8d66-263857b32774.png align="center")

* Choose the launch template or launch configuration that you want to use for the Auto Scaling group.
    
    * If you have already created a launch template with the desired configuration (e.g., Jenkins and Docker setup), select it from the list.
        
    * If you haven't created a launch template yet, you can choose "Create a new launch template" and follow the steps to create one with the desired configuration.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688404705024/c817c5ac-a111-4cda-9637-5e7733c0eaa7.png align="center")

* select VPC and "**Availability Zone(AZ)"** based on your requirement and click on "**Next".**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688404832573/05f614a2-e7b9-4a34-8d9a-77e0b9e4a22e.png align="center")

* For now, Select **No Load Balancer** and **VPC Lattice integration.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688404956323/dc7c3ba5-7f9f-4519-97fb-2ae2965d87ca.png align="center")

* Specify the details for the Auto Scaling group:
    
    Select **Desired capacity**, **Minimum capacity** and **Maximum capacity** based upon the needs or requirements of the particular project and click on **Next.**
    
* Configure the scaling policies to define how the Auto Scaling group scales based on conditions such as CPU utilization or request count.
    

> Choose the type of scaling policy you want to create:
> 
> * "Target tracking scaling policy" adjusts the capacity based on a predefined target metric, such as CPU utilization or request count per instance.
>     
> * "Step scaling policy" adds or removes instances based on predefined thresholds and actions.
>     
> * "Simple scaling policy" increases or decreases the number of instances by a specified adjustment value.
>     

* For now, I am going with none as this is just a demonstration. Further in future, we will be going to use Scaling Policies for projects that require auto-scaling.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688405213252/52ba19d9-934c-4cec-8558-f2cdd3d604d3.png align="center")

* Review the details and click on **"Create Auto Scaling group"** to create the group.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688405253059/18b941ae-0f7b-407f-aa82-8fbc32ebb0bb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688405418868/e6351d3e-7d96-4475-beac-65de3a070ff2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688405576464/bbea93fc-ca07-4d9d-8086-c837558421b6.png align="center")

* <mark>Once</mark> the Auto Scaling group is created, it will automatically launch instances based on the specified launch template or launch configuration. The scaling policies you defined will determine how the group scales up or down based on the specified conditions.
    
* <mark>The</mark> Auto Scaling group will monitor the instances and adjust the capacity as needed, ensuring that the desired number of instances are running to handle the workload. If the workload increases, the group will automatically add more instances. If the workload decreases, it will remove excess instances.
    
* <mark>Auto </mark> Scaling provides elasticity and resilience to your application, allowing it to handle varying traffic loads efficiently and ensuring high availability.
    
    Please note that you should carefully configure the scaling policies and monitor the resource usage to optimize the scaling behavior and control costs effectively.
    

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**