---
title: "Set up CloudWatch alarms and SNS topic in AWS"
datePublished: Sun Jul 09 2023 06:54:59 GMT+0000 (Coordinated Universal Time)
cuid: cljv2xua0000109l3dhj0as0f
slug: set-up-cloudwatch-alarms-and-sns-topic-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688885619825/cc6ec270-c8e4-4d78-a1ca-b85dcaf6013b.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

### **What is Amazon CloudWatch?**

**<mark>Amazon CloudWatch</mark>** is a monitoring and observability service provided by Amazon Web Services (AWS). It helps you collect and track various metrics, log files, and events from your AWS resources and applications. CloudWatch provides valuable insights into the performance, health, and operational state of your AWS infrastructure.

In simple terms, CloudWatch acts as a monitoring tool that allows you to keep an eye on your AWS resources and applications. It gathers data such as CPU usage, network traffic, and storage utilization from your resources. You can view this data in the form of graphs, charts, and alarms in the CloudWatch console.

With CloudWatch, you can set up alarms to notify you when specific conditions are met, such as high CPU usage or low storage space. These alarms can trigger actions or send notifications to help you quickly respond to any issues.

CloudWatch also collects logs from your applications, making it easier to troubleshoot and analyze any errors or issues in your system. You can search and filter logs based on keywords or specific criteria to identify and resolve problems.

### **What is Amazon SNS?**

**<mark>Amazon Simple Notification Service (SNS)</mark>** is a fully managed messaging service provided by Amazon Web Services (AWS). It enables you to send and receive messages or notifications to and from various endpoints, such as mobile devices, email addresses, and other distributed systems.

In simple terms, SNS allows you to send messages to different types of recipients or subscribers. You can think of it as a communication hub that helps you distribute information to multiple destinations at once.

## Task :

* ### **Create a CloudWatch alarm that monitors your billing and sends an email to you when it reaches $2.**
    
* ### **Delete the billing Alarm that you created now.**
    

To create a CloudWatch alarm that monitors your billing and sends an email notification when it reaches $2, follow these steps:

* First, go to **Billing Dashboard** -&gt; **Billing Preferences and activate both preferences**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688884486028/392651ea-6afe-45bf-9061-9f79f1850064.png align="center")

* Go to the AWS Management Console and navigate to the CloudWatch service.
    
* In the CloudWatch console, click on "Alarms" in the left navigation pane.
    
* Click on the "Create alarm" button.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688882765638/1c42bfb1-1285-4f52-ad92-06d741a58dea.png align="center")

* In the "Create Alarm" wizard, under the "Select metrics" section, choose "Billing" as the namespace.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688882790931/0a836ce0-1827-458b-af9e-9a0f97ecbacd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688884527214/86eae0e9-cbff-4a35-99c3-124396a12614.png align="center")

* Select the "EstimatedCharges" metric.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688884577419/8ff5a89a-dbec-43df-aaae-753d77f18974.png align="center")

* Configure the conditions for the alarm:
    
    * For the first condition, select the "Greater than" operator.
        
    * Enter the value "$2" in the threshold field.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688884641485/8e277516-80cb-44ca-b7c5-d8b5c063e662.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688884737129/b3aa51db-56df-4b98-a783-44b1f76384ca.png align="center")

* Configure the email notification settings, including the email address where you want to receive the notifications.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688884893478/0b5fdfb9-678e-4842-b99f-1ae538318528.png align="center")

* Provide a name and description for the alarm.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688884954245/372a8b95-6104-4ec3-8fbe-05b064dec9ca.png align="center")

* Click on the "Create alarm" button to create the CloudWatch alarm.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688885199356/e9ba52a5-5d18-426c-b0f4-e3e44cb1c339.png align="center")

Now, CloudWatch will monitor your billing and send an email notification when it exceeds $2.

**To delete the billing alarm you created, follow these steps:**

1. Go to the CloudWatch console and navigate to the "Alarms" section.
    
2. Locate the billing alarm you want to delete from the list.
    
3. Select the checkbox next to the alarm.
    
4. Click on the "Actions" dropdown menu and choose "Delete".
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688885252820/a02793ac-0174-4a04-a6e0-ce25f2c685ef.png align="center")

* Confirm the deletion when prompted.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688885319855/229e74d6-fac0-4910-bac3-b59b9a264d35.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**