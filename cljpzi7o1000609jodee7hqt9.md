---
title: "IAM Programmatic access and AWS CLI"
datePublished: Wed Jul 05 2023 17:20:01 GMT+0000 (Coordinated Universal Time)
cuid: cljpzi7o1000609jodee7hqt9
slug: iam-programmatic-access-and-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688577552075/b17ce3bc-b661-48e4-aa33-7552fceb2bce.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

### **IAM Programmatic access**

IAM (Identity and Access Management) programmatic access refers to the ability to interact with AWS (Amazon Web Services) services using software applications or scripts. It allows programs or scripts to make API (Application Programming Interface) calls to AWS services on behalf of a user or application.

In simple terms, programmatic access enables automation and integration with AWS services. Instead of manually interacting with the AWS Management Console, you can use programming languages or scripts to perform actions like creating, modifying, or deleting AWS resources.

IAM provides a secure way to manage programmatic access by assigning permissions to specific users or applications. These permissions define what actions can be performed and which AWS resources can be accessed.

For example, you can create an IAM user, assign them specific permissions, and generate an access key and secret access key. These credentials can then be used by a software application or script to authenticate and interact with AWS services through API calls.

Programmatic access is beneficial for automating repetitive tasks, managing resources at scale, and integrating AWS services with custom applications or third-party tools.

### **AWS CLI**

AWS CLI is a command-line tool provided by Amazon Web Services (AWS) that allows you to interact with various AWS services using text commands. It provides a way to manage and automate your AWS resources directly from the command line.

Instead of using the AWS Management Console, which is a graphical user interface, AWS CLI allows you to perform tasks and operations by typing commands in a terminal or command prompt. These commands can be used to create and manage instances, configure security settings, manage storage, and much more.

With AWS CLI, you can write scripts, automate repetitive tasks, and integrate AWS services into your own applications or workflows. It provides a powerful and flexible way to control and manage your AWS resources programmatically.

AWS CLI commands follow a specific syntax and structure. You specify the AWS service you want to interact with, followed by the specific command and any required parameters or options. The CLI then sends the command to the AWS service, and you receive the output or results in your terminal.

**The AWS CLI command you provided is used to launch EC2 instances with specific configurations.**

```yaml
aws ec2 run-instances 
  --name <INSTANCE_Name> 
  --image-id <AMI_ID> 
  --count <No. of Instance>
  --instance-type <INSTANCE_TYPE> 
  --key-name <KEY_PAIR_NAME> 
  --security-group-ids <SECURITY_GROUP_ID> 
  --subnet-id <SUBNET_ID> 
  --region <REGION>
```

* `aws ec2 run-instances`: This command is used to launch EC2 instances.
    
* `--name <INSTANCE_Name>`: Specify the name or tag for the EC2 instance(s).
    
* `--image-id <AMI_ID>`: Provide the ID of the Amazon Machine Image (AMI) to use for the instance(s).
    
* `--count <No. of Instance>`: Specify the number of instances to launch.
    
* `--instance-type <INSTANCE_TYPE>`: Set the instance type, such as t2.micro, m5.large, etc.
    
* `--key-name <KEY_PAIR_NAME>`: Specify the name of the key pair to use for SSH access to the instances.
    
* `--security-group-ids <SECURITY_GROUP_ID>`: Provide the ID of the security group(s) to assign to the instances.
    
* `--subnet-id <SUBNET_ID>`: Specify the ID of the subnet in which to launch the instances.
    
* `--region <REGION>`: Set the AWS region where the instances will be launched.
    

For example:

```yaml
aws ec2 run-instances 
  --name MyInstance 
  --image-id ami-12345678 
  --count 2 
  --instance-type t2.micro 
  --key-name MyKeyPair 
  --security-group-ids sg-12345678 
  --subnet-id subnet-12345678 
  --region us-east-1
```

```yaml
EC2 Commands (Elastic Compute Cloud)  
aws ec2 describe-instances: Lists information about EC2 instances.
aws ec2 run-instances: Launches new EC2 instances.
aws ec2 stop-instances: Stops running EC2 instances.
aws ec2 create-image: Creates an Amazon Machine Image (AMI) from an EC2 instance.

S3 (Simple Storage Service):
aws s3 ls: Lists all S3 buckets.
aws s3 cp: Copies files and objects to/from S3.
aws s3 sync: Syncs directories and S3 buckets, ensuring they have the same content.
aws s3 rm: Deletes files or objects from S3.

aws ec2 describe-instances: List your instances
aws ec2 terminate-instances --instance-ids <Instance-ID>: Terminate your instance
```

---

### **Task-01**

* ### **Create AWS\_ACCESS\_KEY\_ID and AWS\_SECRET\_ACCESS\_KEY from AWS Console.**
    
    **<mark>Steps:-</mark>**
    
* Open the AWS Management Console and navigate to the IAM (Identity and Access Management) service.
    
* In the IAM dashboard, select "Users" from the left-hand menu.
    
* Choose the IAM user for which you want to create an access key. If you don't have an existing IAM user, you can create one by selecting "Add user" and following the prompts.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688574826618/e77cdf72-8cd2-4643-9b64-16755fde6517.png align="center")

* In the user details page, scroll down to the **"Security credentials"** tab and click on the **"Create access key"** button.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688574854780/e303fe01-8f2e-4c41-ac56-154ba7d3d1e6.png align="center")

* Choose "**CLI"** and check the "**Confirmation check box".**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688574883022/3c82cd83-b231-479c-a7be-b5e3f22a5c44.png align="center")

* A pop-up window will appear displaying the **access key ID and secret access key**.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688574999202/5fa8fc0a-3f24-433d-8480-a3628f8f1581.png align="center")

* You can either download the credentials as a CSV file or copy them to a secure location.
    

---

### **Task-02**

* ### **Setup and install AWS CLI and configure your account credentials**
    

To set up and install AWS CLI and configure your account credentials, follow these steps:

* I am gonna make a new ec2 instance and will install AWS CLI with the User data script. OR you can install AWS CLI in your running instances as commands are same for both methods.
    

```yaml
sudo apt-get update
sudo apt-get install awscli -y
aws --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688576221497/2ee9fb6b-bb90-46c7-8299-ec00c5ea195c.png align="center")

* Run the following command to verify the installation:
    
    ```yaml
    aws --version
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688576340789/b05275f9-db0d-4669-abc7-b4ba0d6010a7.png align="center")
    
* **Configure AWS CLI Credentials:**
    
    * Run the following command in the terminal.
        
        ```yaml
        aws configure
        ```
        
    * You will be prompted to enter your **AWS Access Key ID, Secret Access Key, default region, and default output format.**
        
    * Enter your **AWS Access Key ID and Secret Access Key** obtained from the AWS Management Console.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688576880121/4842612d-505c-402a-99c7-6bf832027e36.png align="center")

* Specify the default region (e.g., us-east-1) and default output format (e.g., json).
    
* Press Enter to confirm each input.
    
* Test the CLI by running the below command.
    

```yaml
aws ec2 describe-instances: Lists information about EC2 instances.
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688577076993/81bc16b5-eb34-4551-a1f0-eb7429886b07.png align="center")

**<mark>Congratulations!</mark>** You have now set up and configured AWS CLI with your account credentials. You can use AWS CLI commands to interact with AWS services and manage your resources from the command line.

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**