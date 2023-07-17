---
title: "Test Knowledge on aws"
datePublished: Sun Jul 09 2023 16:12:04 GMT+0000 (Coordinated Universal Time)
cuid: cljvmu92a000109l14vonbllo
slug: test-knowledge-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688919050991/aa60bf02-3208-46be-ab67-49f1bfc4ed17.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

## Task-01

* ### Launch an EC2 instance using the AWS Management Console and connect to it using SSH.
    
* ### Install a web server on the EC2 instance and deploy a simple web application.
    
* ### Monitor the EC2 instance using Amazon CloudWatch and troubleshoot any issues that arise.
    
* Go to the AWS console and need to launch the EC2 machine and connect it to the terminal using SSH.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688895907506/6aedef1a-d84b-4f8c-bd3a-2560a7d5625d.png align="center")

* Now connect EC2 with the terminal through SSH.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688896045199/7530a1c0-2de2-417b-9c71-3ddda3749d83.png align="center")

* Installing a Web Server and Deploying a Simple Web Application:
    
    * Update the package manager:
        
        ```yaml
        sudo apt update -y
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688896633949/0a9db1ad-c1b5-4700-8683-80516f447465.png align="center")
    
    * Install Apache HTTP Server:
        
        ```yaml
         sudo apt-get install apache2 -y
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688896759530/8b066183-3f9c-49f5-93f2-d6367cca70c9.png align="center")
    
    * Start the Apache service:
        
        ```yaml
        sudo systemctl start apache2
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688896785097/e7a2c67e-63ce-40ed-adb5-9e713851d0bc.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688896921047/fec9cdf4-2540-4a40-93a5-a07657666f44.png align="center")
    
    * Create a simple HTML file to serve as your web application's content:
        
        ```yaml
        cd /var/www/html
        ls
        sudo rm -f index.html
        sudo vim index.html
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688898997692/d8bee5a8-27bf-4b3d-b229-358efea07b5c.png align="center")
    
    * Verify that the web server is working by accessing your EC2 instance's public IP address.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688899022454/1edc1c58-270a-4d5a-a549-cc5de7e5a025.png align="center")

Monitoring the EC2 Instance using Amazon CloudWatch:

* Open the CloudWatch service in the AWS Management Console and click on **Create alarm**.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688899590326/647dee8f-618a-4d84-800b-a23fec4bce67.png align="center")

* On **Specify metric and conditions** page click on **Select metric.**
    
* Select the EC2 metric to monitor, such as CPU utilization or network traffic.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688899765490/fbb8a64d-b9ac-4cb6-974e-7a6631068a5b.png align="center")

* Add the metric(s) to a CloudWatch dashboard to view real-time graphs.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688899861240/5831f7b1-6d2d-4dcc-99c5-1db651704176.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688900188507/e42e5cc3-fb76-46d4-a181-5c496f1f642d.png align="center")

* Set up CloudWatch Alarms to get notified when certain thresholds are breached.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688900227392/4adc7e65-4ea9-42cc-b3a4-ecfc2c2058ef.png align="center")

---

## Task-02

* ### Create an Auto Scaling group using the AWS Management Console and configure it to launch EC2 instances in response to changes in demand.
    
* ### Use Amazon CloudWatch to monitor the performance of the Auto Scaling group and the EC2 instances and troubleshoot any issues that arise.
    
* ### Use the AWS CLI to view the state of the Auto Scaling group and the EC2 instances and verify that the correct number of instances are running.
    
* Creating an Auto Scaling Group:
    
    * Create template from instance.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688900773754/cc3fe288-491e-4d00-a96b-e8e68f39bb18.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688900990144/6dc64697-bf0b-417e-a4da-f7b00191840e.png align="center")
    
    * Click on "Create Auto Scaling group" and follow the configuration wizard.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688899267790/5a950b14-74d7-453a-99dc-1f5b7e457fc2.png align="center")
    
    * Select the desired launch template for your EC2 instances.
        
    * Configure the Auto Scaling group details, such as name, network settings, and instance types.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688901034199/5e0ac391-cdc6-46c7-82c1-4aa96bf88fe7.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688901135440/8997c379-a663-4d42-a187-e2603450f83a.png align="center")
    
    * Set the desired capacity and specify the minimum and maximum number of instances the group can scale to.
        
    * Configure scaling policies based on metrics like CPU utilization or network traffic.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688901283263/48da0bfe-c673-40b6-8b85-105535028bd6.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688901305061/649e64da-06d6-4a13-bb34-63f6b5e528ff.png align="center")
    
    * Review the Auto Scaling group settings and create the group.
        
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688901358869/a640eaa9-1f86-42f6-aed3-9a1d3002f7e4.png align="center")
    

**Monitoring Auto Scaling Group and EC2 Instances using Amazon CloudWatch:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688901614846/84e0d8fd-07da-4cad-8689-475f4df9fcc5.png align="center")

* Open the CloudWatch service in the AWS Management Console.
    
* click on "Alarms" to set up alarms for specific metrics.
    
* Create CloudWatch alarms to monitor the performance of your Auto Scaling group and EC2 instances, such as CPU utilization.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688901801113/c7b172f9-c0f3-4779-971e-19e2bcc17143.png align="center")

* Configure actions for the alarms, such as sending notifications.
    

* Monitor the CloudWatch dashboards for insights into the performance of your Auto Scaling group and EC2 instances.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688901891266/02345376-0fff-4fa2-ad8c-24c6f66bf036.png align="center")

**Use the AWS CLI to view the state of the Auto Scaling group and the EC2 instances and verify that the correct number of instances are running.**

* Install the AWS CLI on the EC2 instance.
    
* Open a terminal and install AWS CL.
    

```yaml
sudo apt update
sudo apt-get install awscli -y
aws --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688902182679/8067fbf4-8af5-4165-a814-8deb6df5542e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688902226319/48300fb2-70a9-49e7-8504-c85f89723f71.png align="center")

* Provide Access Key ID, Secret Access Key, Region Name and Output Format.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688902920018/d3592ebc-ea81-478a-895e-71f44b7b6508.png align="center")

* Use the following AWS CLI commands to view the state of the Auto Scaling group and the EC2 instances
    

```yaml
aws autoscaling describe-auto-scaling-groups --auto-scaling-group-names <auto-scaling-group-name>
#Replace <auto-scaling-group-name> with the name of your Auto Scaling group
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688903270966/968c5da6-27e1-431c-8f50-ba55148e051e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688903113293/4e088f1e-077f-4e08-9d92-addc16774b3d.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**