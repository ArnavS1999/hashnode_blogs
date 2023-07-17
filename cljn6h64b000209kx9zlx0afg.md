---
title: "Getting Started with AWS Basics & AWS IAM Basics"
datePublished: Mon Jul 03 2023 18:11:51 GMT+0000 (Coordinated Universal Time)
cuid: cljn6h64b000209kx9zlx0afg
slug: getting-started-with-aws-basics-aws-iam-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688406534599/c7281e40-ebb7-4fb4-a48d-c1aa1807a987.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

### **AWS**

![AWS](https://user-images.githubusercontent.com/115981550/217238286-6c6bc6e7-a1ac-4d12-98f3-f95ff5bf53fc.png align="center")

AWS, which stands for Amazon Web Services, is a cloud computing platform provided by Amazon. In simple terms, it's like renting a computer or a bunch of computers over the Internet. Instead of buying and maintaining your own hardware, you can use AWS to access virtual servers, storage, databases, and other services to run your applications and store your data.

Imagine you have a business and you need a place to store all your important files and documents. Instead of buying physical storage devices like hard drives or servers, AWS allows you to store all your data in the cloud. This means that your files are stored on remote servers managed by Amazon, and you can access them anytime, anywhere as long as you have an internet connection.

Additionally, AWS provides a wide range of services to help you build and deploy applications. For example, if you want to create a website or a mobile app, you can use AWS services to host your application, manage your databases, and handle things like user authentication and data storage. AWS takes care of the underlying infrastructure and ensures that your applications run smoothly and securely.

The best part about AWS is that you only pay for what you use. It's like paying for electricity or water based on your consumption. If you need more storage or computing power, you can easily scale up your resources with just a few clicks. And if you no longer need certain services, you can scale them down or turn them off to save costs.

In summary, AWS is a cloud computing platform that allows you to rent virtual servers, storage, and other services to run your applications and store your data. It provides a flexible and cost-effective solution for businesses and individuals to access computing resources without the need for owning and maintaining physical infrastructure.

### **User Data in AWS:**

* When you launch an instance in Amazon EC2, you have the option of passing user data to the instance that can be used to perform common automated configuration tasks and even run scripts after the instance starts. You can pass two types of user data to Amazon EC2: shell scripts and cloud-init directives.
    
* You can also pass this data into the launch instance wizard as plain text, as a file (this is useful for launching instances using the command line tools), or as base64-encoded text (for API calls).
    
* This will save time and manual effort every time you launch an instance and want to install any application on it like Apache, docker, Jenkins etc
    

### **IAM**

![▷ What is AWS IAM? | AWS Identity & Access Management [2023]](https://cdn.mindmajix.com/blog/images/aws-identity-and-access-management(1).png align="center")

IAM, which stands for Identity and Access Management, is a system designed to control and manage access to resources and services within a computer network or an online platform. It plays the role of a digital gatekeeper, ensuring that only authorized individuals or entities can access specific information or perform certain actions.

IAM offers a solution for creating and managing user accounts, assigning permissions, and controlling user actions. It enables administrators to establish unique user accounts for employees, customers, or any other individuals requiring access to the system. Each user is granted specific permissions that define their level of access within the network or platform. For instance, an administrator can grant certain users the ability to read and write files, while limiting others to read-only access.

Moreover, IAM facilitates the implementation of additional security measures, such as multi-factor authentication, which requires users to provide more than just a password to gain access. It also allows integration with external identity providers, like Google or Facebook, for streamlined authentication processes.

In essence, IAM ensures that organizations maintain proper control over resource access, and data security, and prevent unauthorized usage. By effectively managing user accounts, permissions, and authentication within a system or network, IAM enables organizations to ensure that the right people have access to the right resources, enhancing security and mitigating risks of unauthorized access.

---

### Task 1:

### **Create an IAM user with the username of your wish and grant EC2 Access. Launch your Linux instance through the IAM user that you created now and install Jenkins and docker on your machine via single Shell Script.**

* **<mark>To create an IAM user and grant EC2 access</mark>**
    
* Log in to the AWS Management Console.
    
* Go to the **IAM service**.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688314695209/15ff8338-50a9-49aa-9567-de3e766f2f64.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688315236076/8f5508f1-1b59-4182-8aa9-a216bcacf2b5.png align="center")

* Click on "**Users**" in the left-hand menu.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688315278378/00f777e4-32dd-4b42-baf7-2dd1f6486a47.png align="center")

* Click on **"Add user"** to create a new user.
    
* Choose a **username** of your choice.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688315647210/0af48f0d-7963-4688-9759-8a4509788254.png align="center")

* select any option either **Autogenerated** or **custom** and click on next.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688315678741/a1e492cc-d1e1-4901-bc9d-9a3c27c456f1.png align="center")

* Click **"Next"** and proceed to the permissions page.
    
* Click on **"Attach existing policies directly"**.
    
* Search for and select the **"AmazonEC2FullAccess"** policy to grant EC2 access.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688315914755/8e42af3b-1738-4f16-a9f8-2a6c87096dd2.png align="center")

* Click **"Next"** and review the user details.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688315979699/0b94074d-8154-4cc5-a509-369dcaa2879a.png align="center")

* Finally, click **"Create user"** to create the IAM user.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688316010354/7d014816-b3d2-41ee-a115-859930ce013f.png align="center")

* **<mark>Now, to launch a Linux instance using the IAM user you created:</mark>**
    
* Using the credentials which we have created the need to log in to the AWS as IAM User.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688316544147/40d1da25-4e43-468f-84cf-05a52f3c4a56.png align="center")

* Go to the EC2 service in the AWS Management Console.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688316692084/173809fa-87ea-49c5-8ef3-fb3c2496efa4.png align="center")

* Click on **"Launch Instance"** to start the instance creation wizard.
    
* Choose an **Amazon Machine Image (AMI)** for the Linux distribution of your choice.
    
* Select an instance type (e.g., **t2.micro**).
    
* Configure the instance details as per your requirements.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688317083005/0129ffb6-7e82-40bf-abc0-93be0e624725.png align="center")

* Review the instance details, and if everything looks good, click "**Launch"**.
    
* AWS will now launch your Linux instance using the specified configuration and associate it with the IAM user you created.
    
    To install Jenkins and Docker on your Linux instance, you can connect to it using SSH and run the **shell script:**
    

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

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688370686974/08283473-281b-4c73-9302-18731378abda.png align="center")

* Now we can execute the script file but before we need to change the permission for that particular file.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688370833459/6ad8ba1f-7976-4397-9981-40ac574be06b.png align="center")

* **Installation Successful.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688371087031/510d9121-c69a-4515-a821-ddb8877dc953.png align="center")

---

### Task 2:

### **In this task, you need to prepare a DevOps team of Avengers. Create 3 IAM users of Avengers and assign them to devops groups with IAM policy.**

* Log in to the AWS Console.
    
* Go to the IAM service.
    
* Click on **"Groups"** in the left-hand menu and then click "Create New Group".
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688371336615/5314dc7d-94fb-4de7-b83e-0f2ac6ce630d.png align="center")

* Enter a group name, such as **"Avengers"**.
    
* On the **"Attach Policy"** page, search for and select the desired policies for your DevOps team. For example, you can choose **"AmazonEC2FullAccess"**, or **"AmazonS3FullAccess"**. Once you have selected the policies then **"Create Group".**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688371597530/faa853ee-bb02-40bc-b57a-47b51c92e22a.png align="center")

* Now we need to create a user and add to Avengers the group.
    
* Now, let's create three IAM users and assign them to the DevOps groups.
    
* Click on **"Users"** in the left-hand menu and then click **"Add user"**.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688372118204/04539967-bab3-4036-abe7-49391d9f4840.png align="center")

* Enter the first username, such as **"IronMan"**. Click **"Next: Permissions"**.
    
* On the **"Set permissions"** page, click on "**Add user to group**" and select **"Avengers"**. then **"Next: Review".**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688372198631/f726bd86-d3a0-49ef-b24b-3f20f98a83ab.png align="center")

* Review the user details and click **"Create user"**.
    
* Repeat the above steps to create two more users, such as **"CaptainAmerica**" and **"BlackWidow"**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688372438258/1d10182d-06d4-4e17-8cd5-b95b222bdcab.png align="center")

* Now, **each user** is associated with a specific DevOps group with the necessary **IAM policies**.
    

---

### <mark>By this time you have created multiple EC2 instances, and post-installation manually installed applications like Jenkins, docker etc. Now let's switch to a little automation part.</mark>

### **Day 39 - Task1:**

* ### **Launch the EC2 instance with already installed Jenkins on it. Once the server shows up in the console, hit the IP address in the browser and your Jenkins page should be visible.**
    
* Log in to the AWS Management Console.
    
* Go to the **EC2** service.
    
* Click on **"Launch Instance"** to start the instance creation wizard
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688373851844/7c269cae-0902-4818-ad3a-a38baab01ed0.png align="center")

* After that click on **Advance details-&gt; User data** and need to write the **shell script** where Jenkins installation steps will be mentioned and click on **launch instance**
    

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
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688377268911/48dc194c-9815-4af6-a50f-aeea25b9291a.png align="center")

* After clicking on Launch instance after some time we can see the server is up and running along with Jenkins installed.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688377479756/70263591-479a-436d-90b4-5d612307cf10.png align="center")

* Now we check whether we can able to access Jenkins or not but **before accessing don't forget to enter 8080 port no. in the security group of an instance**.
    
* Take a screenshot of the Userdata and Jenkins page, this will verify the task completion.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688378004827/947e146b-9a8e-4100-a413-bb3126a269d8.png align="center")

---

### Task2:

* **Read more on IAM Roles and explain the IAM Users, Groups and Roles in your own terms.**
    

**<mark>IAM Users: </mark>** IAM Users are individual identities within an AWS account. Each user is associated with a unique set of credentials (access key ID and secret access key) and can be granted specific permissions to access and interact with AWS resources. Users can have their own login credentials and access levels, allowing fine-grained control over who can do what in an AWS environment. For example, you can create IAM Users for different team members in your organization and assign appropriate permissions based on their roles and responsibilities.

**<mark>IAM Groups:</mark>** IAM Groups are collections or categories of IAM Users. Instead of assigning permissions individually to each user, you can create groups and attach policies to the groups. Users added to a group automatically inherit the permissions assigned to that group. This makes it easier to manage access control by organizing users with similar roles or responsibilities into logical groups. For example, you could create a "Developers" group and assign policies that grant permissions required for software development tasks. Then, when a new developer joins your team, you simply add them to the "Developers" group, and they inherit the appropriate permissions.

**<mark>IAM Roles:</mark>** IAM Roles are a way to delegate access to AWS resources to trusted entities. Unlike IAM Users and Groups, roles are not associated with specific individuals or groups. Instead, roles are assumed by entities like IAM Users, AWS services, or even external identities (e.g., identities from other AWS accounts or federated identities). Roles define a set of permissions that can be temporarily assumed by these entities when needed. For example, you can create a role with specific permissions for an EC2 instance, and any EC2 instance that assumes that role will be granted those permissions. Roles are often used to facilitate secure access between AWS services or to enable cross-account access.

**Create three Roles named: DevOps-User, Test-User and Admin.**

* Log in to the AWS Console.
    
* Go to the **IAM** service.
    
* Click on "**Roles**" in the left-hand menu.
    
* Click on "**Create role**" to start creating a new role.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688379302351/6f4a5940-039c-48a6-a084-33d85abcc441.png align="center")

* Choose the type of trusted entity:
    
    * For "**DevOps-User**" and "**Test-User**," select "**AWS service**" as the trusted entity.
        
    * For "**Admin,**" select "**Another AWS account**" as the trusted entity.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688379396101/64ee69b2-48a3-42d9-a69c-695f338a4199.png align="center")

* Click **"Next: Permissions"** to proceed to the permissions configuration.
    
* On the "**Attach permissions policies**" page, you can either choose to attach existing policies or create custom policies for each role.
    
    * To attach existing policies, search for the desired policies (e.g., "**AmazonEC2FullAccess," "AmazonS3FullAccess,"** etc.) and select them.
        
* Now we need to create 3 roles **DevOps-User, Test-User** and **Admin**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688379632631/d59a89a0-2038-4fa4-beef-324c15070eff.png align="center")

* Review the role details and make sure everything is correct.
    
* Finally, click **"Create role"** to create each role.
    
* Repeat these steps two times, once for each role (**"Test-User," and "Admin"**). Ensure that you select the appropriate trusted entity and attach the desired policies or create custom policies based on the intended permissions for each role.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688379895744/d3c5ec83-f77e-4508-9ad3-1f1635bdd3b8.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**