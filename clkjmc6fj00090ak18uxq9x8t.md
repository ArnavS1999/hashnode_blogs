---
title: "Prerequisite For AWS DevOps Projects"
datePublished: Wed Jul 26 2023 11:04:29 GMT+0000 (Coordinated Universal Time)
cuid: clkjmc6fj00090ak18uxq9x8t
slug: prerequisite-for-aws-devops-projects
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690369300063/66b012ca-79bb-4d54-8e0a-36d1b268866b.png
tags: aws, opensource, learning, devops

---

Before we begin with the Project, we need to make sure we have the following prerequisites installed And Configured:

1. AWS Account with Administrator policy. You Can also give Specific permission to the user. Make sure you Generate **HTTPS Git credentials for AWS CodeCommit** for the user. This can be used to push code from a local source to a CodeCommit repository.
    
    * You can do this by going to **IAM** **\\=&gt;** **Users** **\\=&gt; Security credentials =&gt; HTTPS Git credentials for AWS CodeCommit =&gt; Generate credentials.**
        
2. EC2 Instance ( AMI- **Ubuntu**, Type- **t2.micro**, Region: **us-east-1** )
    
    You can Install CodeDeploy Agent by running the below script while creating an ec2 instance or after that. and these steps are for Ubuntu AMI.
    
    ```yaml
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
    
3. Attach a service role to an EC2 instance with the following policy:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677853518663/f236531c-a760-4b54-83ae-29a41c4ac57e.png?auto=compress,format&format=webp align="left")
    
    *(Note: Restart codedeploy-agent service After attaching the service role policy to the EC2 instance)*
    
4. CodeDeploy Service Role for Code deploys with policy:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677853455720/86bb8ebb-c363-4652-be4d-a0b17a64e226.png?auto=compress,format&format=webp align="left")
    
5. Create an S3 Bucket for storing your build artifacts.
    

Great🎊🎉 You're all set for the project. Your EC2 Instance is now prepared for deploying the application. For additional information on the full project, [**<mark>please check out this blog.</mark>**](https://arnavdevops.hashnode.dev/aws-code-pipeline-with-aws-codecommit-codebuild-and-codedeploy-for-continuous-delivery)