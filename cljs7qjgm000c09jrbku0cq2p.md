---
title: "S3 Programmatic access with AWS-CLI"
datePublished: Fri Jul 07 2023 06:45:58 GMT+0000 (Coordinated Universal Time)
cuid: cljs7qjgm000c09jrbku0cq2p
slug: s3-programmatic-access-with-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688659886475/e9b3df8b-e859-44bd-a805-56568b72e61f.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

![Setting Up AWS S3 for Open edX - Blog](https://cdn-blog.lawrencemcdaniel.com/wp-content/uploads/2021/01/30083957/aws-s3-logo.png align="center")

Introduction: In today's digital age, the need for efficient and reliable storage solutions is ever-growing. One such solution that has revolutionized the way we store and manage data is Amazon Web Services (AWS) Simple Storage Service (S3). In this blog post, we will dive into the world of AWS S3, exploring its features, benefits, and use cases, all explained in simple language. So, let's get started!

### **What is AWS S3?**

**<mark>AWS S3</mark>**, or **<mark>Amazon Simple Storage Service</mark>**, is like a massive online storage warehouse provided by Amazon Web Services. Instead of storing your files and data on your computer's hard drive, you can securely store them on the internet. It's like having a virtual storage space accessible from anywhere. AWS S3 is flexible and can store any type of data, like documents, images, videos, or website backups. It ensures your data's safety by automatically storing multiple copies across different servers. You can start small and easily expand your storage as needed. With AWS S3, you can organize your data in buckets and folders for easy management. You can control who can access your files and even track changes over time. It integrates smoothly with other services and applications, allowing you to host websites, deliver files faster, or store backups. AWS S3 simplifies storage by eliminating the need for physical hardware and providing a reliable and scalable solution for your data storage needs.

### **Key Features of AWS S3**

* **<mark>Scalability:</mark>** AWS S3 can handle small to large amounts of data, growing with your needs.
    
* **<mark>Durability:</mark>** Your data is protected against hardware failures and automatically replicated across different servers and data centers.
    
* **<mark>Data Availability:</mark>** You can access your data anytime, from anywhere, ensuring its availability when you need it.
    
* **<mark>Versioning:</mark>** AWS S3 allows you to keep track of changes made to your files over time, making it easy to revert to previous versions if needed.
    
* **<mark>Security:</mark>** You can set access policies, encryption, and authentication measures to control who can access and modify your data.
    
* **<mark>Simple Storage Structure:</mark>** AWS S3 organizes data into buckets, folders, and objects, making it easy to manage and retrieve files.
    
* **<mark>Integration with Other Services: </mark>** AWS S3 seamlessly integrates with other AWS services, enabling features like static website hosting, content delivery networks (CDNs), and database backups.
    
* **<mark>Cost-effective:</mark>** AWS S3 offers cost-effective storage options, allowing you to choose the most suitable storage class for your data and providing cost-estimation tools.
    
* **<mark>Performance Optimization: </mark>** You can optimize performance by configuring features like caching, compression, and data transfer acceleration.
    
* **<mark>Global Accessibility:</mark>** AWS S3 is available in multiple regions worldwide, ensuring fast and reliable access to your data from different geographical locations.
    

### **Use Cases for AWS S3**

* **<mark>Media Storage:</mark>** AWS S3 can securely store media files like images, videos, and audio files, making it easy to access and distribute them across different platforms.
    
* **<mark>Data Backup and Recovery:</mark>** It serves as a reliable backup solution, allowing businesses to store and restore data in case of accidental deletions, system failures, or disasters.
    
* **<mark>Content Distribution:</mark>** AWS S3 integrates with content delivery networks (CDNs) to efficiently deliver static content like images, videos, and documents to users worldwide, improving performance and reducing latency.
    
* **<mark>Data Archiving:</mark>** S3 Glacier, a storage class within AWS S3, offers long-term data archiving with low costs. It's ideal for storing infrequently accessed data that needs to be retained for compliance or historical purposes.
    
* **<mark>Website Hosting:</mark>** AWS S3 can host static websites, making it easy to publish and serve HTML, CSS, JavaScript, and media files without the need for managing complex web servers.
    

### **commonly used AWS CLI commands for Amazon S3:**

`aws s3 ls` - This command lists all of the S3 buckets in your AWS account.

`aws s3 mb s3://bucket-name` - This command creates a new S3 bucket with the specified name.

`aws s3 rb s3://bucket-name` - This command deletes the specified S3 bucket.

`aws s3 cp file.txt s3://bucket-name` - This command uploads a file to an S3 bucket.

`aws s3 cp s3://bucket-name/file.txt .` - This command downloads a file from an S3 bucket to your local file system.

`aws s3 sync local-folder s3://bucket-name` - This command syncs the contents of a local folder with an S3 bucket.

`aws s3 ls s3://bucket-name` - This command lists the objects in an S3 bucket.

`aws s3 rm s3://bucket-name/file.txt` - This command deletes an object from an S3 bucket.

`aws s3 presign s3://bucket-name/file.txt` - This command generates a pre-signed URL for an S3 object, which can be used to grant temporary access to the object.

`aws s3api list-buckets` - This command retrieves a list of all S3 buckets in your AWS account, using the S3 API.

---

### **Task-01**

* ### **Launch an EC2 instance using the AWS Management Console and connect to it using Secure Shell (SSH).**
    
* ### **Create an S3 bucket and upload a file to it using the AWS Management Console.**
    

A step-by-step guide to creating an S3 bucket and uploading a file to it using the AWS Management Console:

* Open the AWS Management Console in your web browser and sign in to your AWS account.
    
* Navigate to the S3 service by searching for "S3" in the AWS services search bar and selecting "S3" from the results.
    
* Click on the "Create bucket" button to start the bucket creation process.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688649521987/d11ebeb8-a916-4a45-89e6-51fdcc2ddcdc.png align="center")

* Provide a unique and meaningful name for your bucket. Note that bucket names must be globally unique across all of AWS. You can also choose the AWS Region where you want your bucket to be located. "Scroll Down."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688650054930/ac935c2c-5508-4cd4-ba26-194d92994eb1.png align="center")

* Set up an optional configuration for the bucket permissions. You can manage access control lists (ACLs) and bucket policies to define who can access the bucket and what they can do with the objects in it. Again, you can leave the default settings or customize them as needed. "Scroll Down."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688649718726/70e61c8b-6909-4c4c-b4a5-eba7a1f6e41a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688649884055/99c1449e-1ccd-4165-ba43-33791235354e.png align="center")

* Review the bucket configuration and click "Create bucket" to create the bucket.
    
* Once the bucket is created, you will be redirected to the bucket overview page. Click on the bucket name to open the bucket.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688650099702/97194e3e-8616-4d13-81de-4b683d2b7aa9.png align="center")

* To upload a file to the bucket, click the "Upload" button.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688650122058/d77b350d-673c-4e5d-9301-ca2b6c09fbcd.png align="center")

* In the upload window, click the "Add files" button or drag and drop files from your computer to the upload area. You can upload one or multiple files at once.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688650226311/3d8457a0-b0db-4f3b-8987-8a24f74db7e7.png align="center")

* Optionally, you can set permissions, configure metadata, and enable server-side encryption for the uploaded files. You can leave these settings as default if you don't need to customize them.
    
* Click the "Upload" button to start the file upload process. Progress bars will show the upload status of each file.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688650279578/fb9dec1f-8be7-4b4f-8bc0-9fb2b7c4f0b3.png align="center")

* Once the upload is complete, you will see the uploaded files listed in your S3 bucket.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688650330887/b8dddaaf-46e8-4c2c-a163-cf7d8bc44ce2.png align="center")

* ### **Access the file from the EC2 instance using the AWS Command Line Interface (AWS CLI).**
    
* For [**Setup and installation of AWS CLI refer to this blog**](https://arnavdevops.hashnode.dev/iam-programmatic-access-and-aws-cli)
    
* Once the AWS CLI is configured, you can use the following command to verify.
    

```yaml
aws s3 ls
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688651208232/c7e87d62-936b-47a3-ab56-9e6f450a43aa.png align="center")

* Use the aws s2 cp command to copy files from your EC2 instance to your S3 bucket.
    
* ```yaml
    aws s3 cp <file-name> s3://<bucket-name>
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688651712346/80f84842-6d95-4f70-a07f-91e0487d5542.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688651809107/d4b14e67-03bd-49d7-ab4b-c7392d1fb90a.png align="center")

---

## **Task-02**

* ### **Create a snapshot of the EC2 instance and use it to launch a new EC2 instance.**
    
* ### **Download a file from the S3 bucket using the AWS CLI.**
    
* ### **Verify that the contents of the file are the same on both EC2 instances.**
    
    **<mark>Steps:-</mark>**
    
* In the EC2 dashboard, select "Snapshots" from the left-hand navigation pane.
    
* Click **Snapshots** -&gt; **Create snapshot**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688654318980/020354e2-b233-45e1-8b24-a4964fc28b6d.png align="center")

* Need to select the **instance** and **instance id** and click on **Create Snapshot.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688654504162/1cc3bed8-8568-488c-9e15-c2841a3c06fa.png align="center")

* Wait for the snapshot creation process to complete. This may take some time depending on the size of the instance and the amount of data being snapshot.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688654590529/4bee3df6-19a6-481a-8f74-1e9f96d2ee2c.png align="center")

* Once the snapshot is created, Locate and select the snapshot that was just created.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688656800473/7b8ed70f-c144-4a17-b13b-3b5a7dfba35e.png align="center")

* Click on the "Actions" button above the snapshot list and choose "Create Image from snapshot" from the drop-down menu.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688656849195/64572abc-9052-4098-9976-eb2a1d6d9ae4.png align="center")

* In the "Create Image" dialog box, provide a unique name and description for the AMI. Optionally, you can specify other configuration settings such as instance type, security groups, and storage. Click "Create".
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688656926598/7f2c97da-0d4a-4b42-ab1a-95d6aa7b956f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688657205846/bfcddf61-a697-470e-ae3f-e9ea3c070489.png align="center")

* Now click on **launch instances from AMI.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688657618242/9bf09286-09ed-41a7-91b6-7c0ae09fdf1a.png align="center")

* **Download a file from the S3 bucket using the AWS CLI.**
    
* Use this command
    

```yaml
<aws s3 cp s3://bucket-name/file.txt .> - This command downloads a file from an S3 bucket to your local file system.
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688658190288/a210b57f-56b8-41df-8ebc-e62dc4c44f33.png align="center")

* **<mark>By following these steps, you will have created a snapshot of the original EC2 instance and used it to launch a new EC2 instance. The new instance will have the same configuration and data as the original instance at the time the snapshot was taken.</mark>**
    

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**