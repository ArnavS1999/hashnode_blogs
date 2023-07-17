---
title: "Relational Database Service in AWS"
datePublished: Fri Jul 07 2023 11:20:22 GMT+0000 (Coordinated Universal Time)
cuid: cljshjeri001k09jo8atnc9oq
slug: relational-database-service-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688728756157/50757bac-9d0c-4939-8778-c0e2182dcbb4.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

### **Amazon RDS**

AWS Relational Database Service (RDS) is a cloud-based managed service provided by Amazon Web Services (AWS) that simplifies the process of setting up, operating, and scaling relational databases. RDS supports popular database engines like Amazon Aurora, MySQL, PostgreSQL, Oracle, and Microsoft SQL Server.

AWS RDS takes away the complexity of managing relational databases. Instead of setting up and maintaining your own database infrastructure, RDS handles the heavy lifting for you. It provides automated backups, software patching, and database scaling, allowing you to focus on your application rather than database administration.

With RDS, you can easily create a database instance with just a few clicks in the AWS Management Console. RDS manages tasks like database installation, software updates, and backups, reducing the operational burden on your part. You can choose the database engine that best suits your application requirements.

---

### **Task-01**

* ### **Create a Free tier RDS instance of MySQL**
    
* ### **Create an EC2 instance**
    

To create a free tier RDS instance of MySQL, follow these steps:-

* Open the AWS Management Console.
    
* Navigate to the RDS service by searching for "RDS" in the AWS services search bar and selecting "RDS" from the results.
    
* Click on the "Create database" button to start the database creation process.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688726111470/fe0b5ee2-2742-4a53-9021-90c31cb1d323.png align="center")

* In the "Engine options" section, select "MySQL" as the database engine.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688726160967/bed8d736-52b6-4bfa-a0a9-b8cd622f1da7.png align="center")

* Under "Templates," select the "Free tier" template to ensure you create a free tier eligible instance.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688726213141/1d4632e2-a707-4cbb-8d9e-829e9565b9f8.png align="center")

* In the "Settings" section, provide a unique and meaningful name for your database instance.
    
* Set a master username and password for the database. Remember to choose a strong password.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688726279734/c1f115a7-9d5a-491f-8d1d-1f2dfdc43245.png align="center")

* Configure the remaining settings according to your needs, such as the instance size, storage type, and allocated storage.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688726382314/60de3dd2-c443-4f97-970e-8a1ab7d0caaa.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688726395474/67f933e7-bfef-47db-af44-99b58b5e264a.png align="center")

* In Connectivity, compute resource as EC2 compute resource.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688726616564/8d408ff6-6e56-4520-8c21-31914d48e081.png align="center")

* Scroll down to the "Network & Security" section and choose the appropriate VPC, subnet, and security group settings.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688726695892/4672c5e4-1bdf-487e-b8ee-f6f503c8995f.png align="center")

* Finally, click the "Create database" button to initiate the creation of the free tier RDS instance.
    
* Wait for the RDS instance to be created. The process may take several minutes.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688727094288/f0894ef1-9963-467c-b291-34d91467f9cb.png align="center")

* ### **Create an IAM role with RDS access**
    

To create an IAM role with RDS access, follow these steps:-

* Navigate to the IAM service by searching for "IAM" in the AWS services search bar and selecting "IAM" from the results.
    
* In the IAM dashboard, select "Roles" from the left-hand navigation pane.
    
* Click on the "Create role" button to start creating a new IAM role.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688727272064/12857837-e6ca-4cc4-80fb-954bed50cccb.png align="center")

* In the "Select type of trusted entity" section, choose the service or entity that will use this role. Since we want to grant RDS access, select "AWS service" as the trusted entity.
    
* Under "Choose a use case," select "EC2" from the list of services.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688727345749/b4d26e77-9893-40d0-b466-71c5c90fc29c.png align="center")

* Click on the "Next: Permissions" button to proceed to the next step.
    
* In the "Attach permissions policies" section, choose an existing policy that grants the necessary RDS permissions like "AmazonRDSFullAccess".
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688727440874/a2f043f0-5ed6-4630-a2ee-9a09f5aadc8b.png align="center")

* After selecting the desired policy, click on "Next".
    
* Provide a unique and meaningful name for the IAM role and optionally add a description.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688727500742/3e7c7ff5-4751-4108-a498-6ebdff1a4d06.png align="center")

* Review the details of the IAM role to ensure they are accurate.
    
* Click on the "Create role" button to create the IAM role with RDS access.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688727543848/be5338f4-9633-4977-8802-fd05b1c512ee.png align="center")

* ### **Assign the role to EC2 so that your EC2 Instance can connect with RDS**
    

To assign the IAM role to an EC2 instance so that it can connect with RDS, you can follow these steps:

* Navigate to the EC2 service.
    
* In the EC2 dashboard, select "Instances" from the left-hand navigation pane.
    
* Locate the EC2 instance to which you want to assign the IAM role.
    
* **Actions**\-&gt;**Security**\-&gt;**Modify IAM role**
    
* Select IAM which we created and click on **update IAM role**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688727828278/2375aea2-879a-4775-b9b8-5d62885286d4.png align="center")

* The IAM role is now attached to the EC2 instance, and the necessary permissions are granted to allow the instance to connect with RDS.
    
* ### **Once the RDS instance is up and running, get the credentials and connect your EC2 instance using a MySQL client.**
    
* SSH into your EC2 instance using a terminal.
    
* Install a MySQL client on the EC2 instance.
    
* To install the MySQL client on EC2 instances:
    

```yaml
sudo apt-get update
sudo apt-get install mysql-client
```

* check whether MySQL is installed or not by running the below command.
    

```yaml
mysql --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688728204692/ac44b062-2c8f-46b8-b4eb-42a39863e6f9.png align="center")

* Once the MySQL client is installed, you can connect to the RDS instance using the following command:
    

```yaml
mysql -h <RDS endpoint> -P <port> -u <master username> -p
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688728351655/fc778008-316f-49a3-b880-04beaf830fbe.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688728465634/70f21319-c581-454e-92e4-9deb9c414767.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>  
**