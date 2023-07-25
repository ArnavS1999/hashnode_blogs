---
title: "Your CI/CD pipeline on AWS - Part 3"
datePublished: Tue Jul 25 2023 13:25:38 GMT+0000 (Coordinated Universal Time)
cuid: clkibxtug000509jt8ory7kqb
slug: your-cicd-pipeline-on-aws-part-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690291476430/faa3ae9d-038b-4731-8d4b-2db103746059.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

## What is CodeDeploy?

AWS CodeDeploy is a service provided by Amazon Web Services (AWS) that automates the deployment of applications to a variety of computing services, such as Amazon EC2 instances, on-premises servers, AWS Fargate, and Lambda functions. It is a continuous deployment tool that makes it easier to release new features and updates to your application without manually managing the deployment process.

CodeDeploy allows you to define the deployment configurations and deploy your applications in a consistent and reliable manner, ensuring minimal downtime and reducing the risk of errors during the deployment process.

### Read about Appspec.yaml file for CodeDeploy.

The `appspec.yaml` file is a YAML-formatted file used in AWS CodeDeploy to define the deployment and lifecycle hooks for your application. It provides instructions on how to deploy the application to different instances, how to manage files, and how to execute scripts during the deployment process.

---

# Task-01 :

* ### Deploy index.html file on EC2 machine using nginx
    
* ### you have to set up a CodeDeploy agent in order to deploy code on EC2
    
* ### Add appspec.yaml file to CodeCommit Repository and complete the deployment process.
    

**<mark>Step1:-</mark>**

* **Set Up an EC2 Instance:**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690111758118/6b6481a2-75d3-46eb-bb34-ce287f77e3d7.png align="center")
    

**<mark>Step2:-</mark>**

* **Create a CodeDeploy Application:**
    
    * Go to the AWS Management Console and navigate to the CodeDeploy service.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690108678048/9605051d-10e2-411b-be79-9bfa56e35bab.png align="center")
    
    * Click on "Create application" and give it the name "demo-app-application"
        
    * Choose the Compute platform as "EC2/On-Premises".
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690108738682/3a89d7db-6c91-4172-aced-88057932fcd0.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690108839493/79da3ebf-8931-4abb-a74f-ebabcc400fac.png align="center")
    

**<mark>Step3:-</mark>**

* **Create a Deployment Group:**
    
    * In the CodeDeploy application you created, click on "Create deployment group".
        
    * Give the deployment group the name "demo-app-depl-grp".
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690109098927/5e8b3835-754e-4ec8-a39f-f3ac8af12e1e.png align="center")
    
    * For the service role, select "Create a new service role".
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690109969479/f989ca29-e532-4d62-81a9-2c312b7ce5da.png align="center")
    
    * Update the Trust relationship in order to grant AWS CodeDeploy access to your target instances.
        
    * ```yaml
          {
              "Version": "2012-10-17",
              "Statement": [
                  {
                      "Effect": "Allow",
                      "Principal": {
                          "Service": "codedeploy.amazonaws.com"
                      },
                      "Action": "sts:AssumeRole"
                  }
              ]
          }
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690111027300/d4f1481f-2bd7-4654-8680-7ed351ae05a4.png align="center")
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690113845592/ec9fb846-185d-4b6e-88e6-bca71c1e2d91.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690114000835/12319376-41bb-4edf-bd1f-3f1115da669e.png align="center")

* Click on "Create deployment group".
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690114237113/d26c27a2-8e1f-4413-b792-485086a6bf3a.png align="center")

**<mark>Step4:-</mark>**

* **Setup a CodeDeploy agent to deploy code on EC2**
    
* To use CodeDeploy on EC2 instances or on-premises servers, the CodeDeploy agent must be installed first.
    
* Follow the steps in the AWS documentation to install the CodeDeploy agent on your EC2 instance: [**https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent-operations-install.html**](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent-operations-install.html)
    
* **<mark>OR</mark>**
    
* You can install the CodeDeploy agent by running the following script on your EC2 instance:
    
* ```yaml
          #!/bin/bash 
          # This installs the CodeDeploy agent and its prerequisites on Ubuntu 22.04.  
          sudo apt-get update 
          sudo apt-get install ruby-full ruby-webrick wget -y 
          cd /tmp 
          wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/releases/codedeploy-agent_1.3.2-1902_all.deb 
          mkdir codedeploy-agent_1.3.2-1902_ubuntu22 
          dpkg-deb -R codedeploy-agent_1.3.2-1902_all.deb codedeploy-agent_1.3.2-1902_ubuntu22 
          sed 's/Depends:.*/Depends:ruby3.0/' -i ./codedeploy-agent_1.3.2-1902_ubuntu22/DEBIAN/control 
          dpkg-deb -b codedeploy-agent_1.3.2-1902_ubuntu22/ 
          sudo dpkg -i codedeploy-agent_1.3.2-1902_ubuntu22.deb 
          systemctl list-units --type=service | grep codedeploy 
          sudo service codedeploy-agent status
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690114831509/5d674a8c-a010-454b-a94b-b46b23f333bf.png align="center")

* Install the install.sh script with "sudo bash install.sh"
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690114999548/974cb929-0813-409a-93fc-2034341e73c7.png align="center")

**<mark>Step5:-</mark>**

* To add the `appspec.yaml` file to the CodeCommit repository and complete the deployment process with AWS CodeDeploy, follow these steps:
    
* Create the `appspec.yaml` File:
    
* Create a file named `appspec.yaml` and add the deployment details, hooks, and files to be deployed.
    
* This is a appspec.yml file that deploys the index.html file on nginx. also, create 2 scripts for installing nginx and starting nginx.
    
    ```yaml
        version: 0.0
        os: linux
        files:
          - source: /
            destination: /var/www/html
        hooks:
          AfterInstall:
            - location: install_nginx.sh
              timeout: 300
              runas: root
          ApplicationStart:
            - location: start_nginx.sh
              timeout: 300
              runas: root
    ```
    

```yaml
#!/bin/bash
sudo service nginx start
```

```yaml
#!/bin/bash
sudo apt-get update
sudo apt-get install nginx -yapp
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690116213416/6743c0f2-edce-43dd-b9ed-59a5911b62b8.png align="center")

**<mark>Step6:-</mark>**

* Add `appspec.yaml` to CodeCommit Repository:
    
* Commit the `appspec.yaml` , scripts and other files to the CodeCommit repository with a meaningful commit message.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690116492815/ab788a36-ef8a-4855-88c5-c7c5bf82b482.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690116553687/6629a457-46b7-47b5-80b9-dc9b05bc3096.png align="center")

* Add changes to the buildspec.yml file
    
* ```yaml
      From this 
      artifacts:
          files:
            - /var/www/html/index.html
      to this
      artifacts:
          files:
            - '**/*'
    ```
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690116679552/30aef20a-8790-450c-a733-ce565f3dc9e3.png align="center")
    
    Now click on start build on [Developer Tools](https://us-east-1.console.aws.amazon.com/codesuite/home?region=us-east-1)\-&gt;[CodeBuild](https://us-east-1.console.aws.amazon.com/codesuite/codebuild/start?region=us-east-1)\-&gt;[Build projects](https://us-east-1.console.aws.amazon.com/codesuite/codebuild/projects?region=us-east-1)\-&gt;[demo-app-build](https://us-east-1.console.aws.amazon.com/codesuite/codebuild/095466711907/projects/demo-app-build/history?region=us-east-1)
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690117537444/9e6e3896-feff-4460-86a4-7ae7ad2d1e0b.png align="center")

* After building completion, go to the S3 bucket and copy the S3 URL of the artifact.zip file
    
* [Amazon S3](https://s3.console.aws.amazon.com/s3/get-started?region=us-east-1)\-&gt;[Buckets](https://s3.console.aws.amazon.com/s3/buckets?region=us-east-1)\-&gt;[aws-demo-app-bucket](https://s3.console.aws.amazon.com/s3/buckets/aws-demo-app-bucket)**\-&gt;**[**artifact.zip**](http://artifact.zip)**./**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690194682741/154cb573-ee99-4f44-bb2f-b886106c3e2d.png align="center")

**<mark>Step7:-</mark>**

* Create a Deployment:
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690194705162/ab2f9e5d-f6ad-4a30-858f-2f0321ac26de.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690118231843/d28eb448-1341-42f3-a011-8d54256d50e8.png align="center")

* After deployment is created but events are still in a pending state.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690118381946/ecc282d6-c2f0-4698-92e2-844d53583c29.png align="center")

* The reason is EC2 doesn't have any role policy to retrieve the data from S3 to CodeDeploy.
    
* To create a new service role for enabling communication between EC2 and S3, code deploy.
    
    * Go to the IAM service and create 'EC2-S3-CodeDeploy' with permissions.
        
        "AmazoneEC2FullAccess", "AmazoneS3FullAccess", "AWSCodeDeployFullAccess".
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690118633292/f96bb812-6b3a-4e47-94d5-690edb5a15f2.png align="center")

* Now attach the role to EC2 Instance.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690118702995/5394590c-7635-4e31-b692-02d049e5cd84.png align="center")

* After updating the IAM role, restart the code-deploy agent.
    
    ```yaml
    sudo service codedeploy-agent restart
    sudo service codedeploy-agent status
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690118932634/b0ac8329-e54b-4537-b729-dbb990ce1c89.png align="center")

* Once the codedeploy-agent restarted, the deployment will get completed successfully.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690194777993/105ae6f5-7bec-4736-9c20-42ca9e8beb41.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690194876164/e0bd7fde-194f-40d1-999e-0982d7fbcf60.png align="center")

**<mark>Step8:-</mark>**

* Get EC2 instance public IP and paste it into the browser and check whether our webpage is live or not.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690195032880/bdf5acad-dffd-418e-b615-0a9e573ffd32.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**