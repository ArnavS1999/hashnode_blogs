---
title: "Setting up an Application Load Balancer with AWS EC2"
datePublished: Tue Jul 04 2023 19:02:33 GMT+0000 (Coordinated Universal Time)
cuid: cljonq893000809kz6m5q8fez
slug: setting-up-an-application-load-balancer-with-aws-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688497229339/12a3cc46-ae9e-4410-8a3a-bfa63ba55b34.png
tags: aws, opensource, devops, 90daysofdevops, wemakedevs

---

![LB2](https://user-images.githubusercontent.com/115981550/218145297-d55fe812-32b7-4242-a4f8-eb66312caa2c.png align="center")

### **What is Load Balancing?**

Load balancing is the distribution of workloads across multiple servers to ensure consistent and optimal resource utilization. It is an essential aspect of any large-scale and scalable computing system, as it helps you to improve the reliability and performance of your applications.

### **Elastic Load Balancing:**

Elastic Load Balancing (ELB) is an AWS service designed to evenly distribute incoming traffic across multiple EC2 instances to ensure efficient and reliable application delivery. ELB offers three types of load balancers:

* **<mark>Application Load Balancer (ALB):</mark>** ALB operates at the application layer (Layer 7) of the OSI model and is ideal for balancing HTTP and HTTPS traffic. It intelligently routes requests to different EC2 instances based on specific rules, allowing for advanced load balancing and content-based routing.
    

![10 reasons why you should think about using an AWS Application Load Balancer  | by Florian Jakob | Ankercloud Engineering | Medium](https://miro.medium.com/v2/resize:fit:1200/0*UCFdX5MLOV2Pt3bL align="center")

* **<mark>Network Load Balancer (NLB): </mark>** NLB operates at the transport layer (Layer 4) and is well-suited for handling high volumes of traffic. It efficiently balances TCP and UDP traffic by distributing it across multiple EC2 instances, making it suitable for applications that require extreme performance and scalability.
    

![Network Load Balancer (NLB) architectures - Advanced Multi-AZ Resilience  Patterns](https://docs.aws.amazon.com/images/whitepapers/latest/advanced-multi-az-resilience-patterns/images/azi-architecture-using-nlb.png align="left")

* **<mark>Classic Load Balancer (CLB):</mark>** CLB is the legacy version of ELB and provides basic load balancing for both HTTP/HTTPS and TCP/UDP traffic. It distributes incoming requests across multiple EC2 instances using a round-robin algorithm, ensuring an even distribution of workload.
    

![
A load balancer routes traffic from clients to your EC2 instances.
](https://docs.aws.amazon.com/images/elasticloadbalancing/latest/classic/images/load_balancer.png align="center")

---

### **Task 1:**

* ### **Launch 2 EC2 instances with an Ubuntu AMI and use User Data to install the Apache Web Server.**
    

To launch two EC2 instances with an Ubuntu AMI and install the Apache Web Server using User Data, follow these steps:

* Log in to the AWS Management Console.
    
* Go to the EC2 service.
    
* Click on **"Launch Instances"** to start launching a new EC2 instance.
    
* Select the desired Ubuntu AMI from the available options.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688489339029/e71f8488-7167-4f17-a234-262ecd2a9e76.png align="center")

* Choose the instance type, such as t2.micro.
    
* Configure the instance details, such as the number of instances (in this case, choose 2) and networking settings.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688489564315/e5011f70-c8c3-4215-b4b6-2dec290ec7ef.png align="center")

* Scroll down to the **"Advanced details"** section and locate the "User Data" field.
    
* In the User Data field, enter the following script:
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688489603332/128b1277-3592-4524-b161-98c86fd5653f.png align="center")

* This script performs the following actions:
    
    * Updates the package repository on the instance.
        
    * Installs the Apache Web Server using the `apt` package manager.
        
    * Starts the Apache service.
        
    * Configures the Apache service to start automatically upon instance boot.
        
* Review the configuration and click on "Launch Instances" to launch the EC2 instances.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688489787522/505a87b5-3c37-4f9a-86a0-442dd6b4910b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688490045943/0ebcc14c-a2fd-46ca-894b-86c742d0ebed.png align="center")

* Once the instances are launched, you can access the Apache Web Server by entering the public IP address of either instance in a web browser. You should see the default Apache welcome page, indicating that the installation was successful.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688490402248/9a697a74-3266-40f6-b21b-b82560bc7fa9.png align="center")

* ### **Modify the index.html file to include your name so that when your Apache server is hosted, it will display your name also do it for 2nd instance which includes " TrainWithShubham Community is Super Awesome :) ".**
    
* To modify both servers index.html files based on project requirements and need to go to **"/var/www/html"** path and edit **index.html**
    

```yaml
cd /var/www/html
ls
vim index.html
```

* 1st Server
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688491440464/13f18e1b-9318-46fd-b40d-1ce761fb0d2d.png align="center")

* 2nd Server
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688491548512/9df49a0e-1217-4dd3-aaf1-c3f6ed7d0414.png align="center")

* **Copy the public IP address of your EC2 instances.**
    
* **Open a web browser and paste the public IP address into the address bar.**
    
* **You should see a webpage displaying information about your PHP installation.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688491940769/4aacf4fe-8603-41d7-887b-64de67b56d99.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688491854854/cb3ede68-ca10-4fe5-a5cd-efaa5f70857f.png align="center")

---

### **Task 2:**

* ### **Create an Application Load Balancer (ALB) in EC2 using the AWS Management Console.**
    
* ### **Add EC2 instances that you launch in task-1 to the ALB as target groups.**
    
* ### **Verify that the ALB is working properly by checking the health status of the target instances and testing the load-balancing capabilities.**
    

To create an Application Load Balancer (ALB) in EC2 using the AWS Management Console and add the EC2 instances from Task 1 to the ALB as target groups, follow these steps:

* Go to the EC2 service.
    
* In the left-hand menu, click on **"Load Balancers"** under the **"Load Balancing"** section.
    
* Click on the **"Create Load Balancer"** button.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688492878696/68d324a3-0561-4179-af43-100cfb679d4f.png align="center")

* Select **"Application Load Balancer"** as the load balancer type and click on **"Create".**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688492902610/2b703501-c478-4ec0-83de-8da6fd8c92b7.png align="center")

* Configure the load balancer settings:
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688492944929/0c512a98-aebb-421d-a119-92017fe2e181.png align="center")

* choose at least 2 subnets
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688492979294/58ff9690-dc3a-4af9-b140-9ae1fbfdff5e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688494481047/b9885431-5f19-4da1-9298-8c3fac3fae39.png align="center")

* **Configure the routing:**
    
* Set up the listener protocol and port for the load balancer.
    
* Under **"Default action"** choose **"Create target group"** which redirects you to the new tab.
    
* Choose the target type as **"Instance"** and configure the target group.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688494736313/2ac05451-affd-4ee5-b2c9-3919f733ab8f.png align="center")

* After selecting Instances give **"Target group name"**.
    
* Choose the same VPC and register the instances from Task 1 as targets.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688494883969/74b3221c-7366-40ed-ba56-6acb7329d8e6.png align="center")

* Click on **"Next: Register Targets"**.
    
* Select both servers/instances and need to click on **include as pending below** after that scroll down and click on **create target group.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688494935883/1e72569a-4da7-44d5-b5f6-db9e2566d5ca.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688494952324/4c4348dc-28c2-46c4-9734-c2837294d918.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688495005729/dd4d3631-30f7-4d10-a714-3cbf90313375.png align="center")

* Now go back to your **"Load Balancer"** tab and click on the **refresh button** near the **"Default action"** and then you will see the new target group we just created.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688495196904/28ae92e6-c354-4eb5-aed9-727c6a7f82f2.png align="center")

* Review the configuration settings and click on **"Create"** to create the ALB.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688495256620/15491a91-703a-4a71-bcde-ac58c54c747c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688495291687/c922a166-bfe3-4a4e-8903-37fcffbb48ef.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688495909754/2e9b3966-8ef9-44f4-8350-3c6dc78ea4be.png align="center")

Once the ALB is created, it will distribute incoming traffic to the registered EC2 instances based on the configured target group. To verify that the ALB is working properly and load balancing correctly:

* Select the ALB that you created.
    
* In the "Details" tab, you can view the "DNS name" of the load balancer.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688495977751/c0102dc1-d355-409a-afd2-f3cc5d4abd2b.png align="center")

* Open a web browser and enter the DNS name of the ALB. This will redirect your request to one of the instances through load balancing.
    
* Verify that the application or web page hosted on the instances is accessible and functioning correctly.
    
* Test the load-balancing capabilities by refreshing the page multiple times.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688496146451/7057c464-1fa1-4fc1-aaba-b775ae4fc15f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688496158981/f0f58101-28af-4153-afb8-23a7e5332831.png align="center")

![LoadBalancer](https://user-images.githubusercontent.com/115981550/218143557-26ec33ce-99a7-4db6-a46f-1cf48ed77ae0.png align="center")

**<mark>Note:-</mark>** <mark>To delete the Load Balancer then first need to delete the </mark> **<mark>load balancer</mark>**<mark>-&gt; </mark> **<mark>target groups</mark>**<mark>-&gt;</mark>**<mark>instances/servers.</mark>**

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**