---
title: "Your CI/CD pipeline on AWS - Part-1"
datePublished: Tue Jul 25 2023 12:48:02 GMT+0000 (Coordinated Universal Time)
cuid: clkialhq500040amj63s3ed3k
slug: your-cicd-pipeline-on-aws-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690289558432/21d8fc7c-947a-4eb7-b351-c0a830ef601d.png
tags: aws, opensource, learning, devops, 90daysofdevops

---

## What is CodeCommit?

**<mark>AWS CodeCommit</mark>** is a fully managed source code repository service provided by Amazon Web Services (AWS). It offers a secure and scalable platform for storing and managing your code repositories in the cloud. In simple terms, CodeCommit is a service that allows you to securely store and version your code, making it easier to collaborate with team members and manage changes to your software projects.

With CodeCommit, you can create private Git repositories to host your code. It provides a reliable and highly available infrastructure, ensuring that your code is stored securely and accessible whenever you need it. CodeCommit supports all Git commands, allowing you to perform typical version control operations like creating branches, committing changes, and merging code.

Some key features and benefits of CodeCommit include:

1. **<mark>Secure and Scalable:</mark>** CodeCommit utilizes AWS security best practices, including encryption at rest and in transit, access control, and fine-grained permissions. It can scale to accommodate large codebases and teams.
    
2. **<mark>Integration with DevOps Tools:</mark>** CodeCommit seamlessly integrates with other AWS services and popular development tools, such as AWS CodePipeline, AWS CodeBuild, and AWS CodeDeploy. This enables end-to-end automation and streamlined workflows in your software development lifecycle.
    
3. **<mark>Collaboration and Teamwork:</mark>** Multiple developers can work on the same codebase simultaneously, making it easy to collaborate and track changes. CodeCommit allows you to manage access permissions, branch policies, and code reviews, ensuring proper control and visibility over your code.
    
4. **<mark>Code Versioning and History:</mark>** CodeCommit automatically tracks and maintains a complete history of your code changes. You can easily compare versions, revert changes, and track who made specific changes, providing a clear audit trail.
    
5. **<mark>Easy Migration and Integration:</mark>** CodeCommit is compatible with Git, making it straightforward to migrate existing repositories or integrate with Git-based tools and workflows. You can push and pull code using standard Git commands or popular Git clients.
    

---

# Task-01 :

* ### Set up a code repository on CodeCommit and clone it on your local.
    
* ### You need to set up GitCredentials in your AWS IAM.
    
* ### Use those credentials in your local and then clone the repository from CodeCommit
    

Here are the steps to set up the repository, configure Git credentials, and clone the repository locally:

* **Create a CodeCommit Repository:**
    
    * Go to the AWS Management Console and navigate to the CodeCommit service.
        
    * Click on "Create repository" and name it "demo-app".
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690015281549/fcd5442c-b32d-434f-a16a-4264417abf24.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690015285447/ffa94dc4-bfb8-4da4-b2a0-5b2f2a2b9bcc.png align="center")

**<mark>NOTE:- You are signed in using a root account. You cannot configure SSH connections for a root account, and HTTPS connections for a root account are not recommended. Consider signing in as an IAM user and then setting up your connection.</mark>**

* **Configure Git Credentials in AWS IAM:**
    
    * Go to the AWS Management Console and navigate to the IAM service.
        
    * In IAM, create a new user.
        
    * Add the necessary permissions for the user to access CodeCommit like `AWScodeCommitPowerUser` policy).
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690016356992/bc9f5018-d67c-4af4-a5f1-26d5351f3689.png align="center")

* * Generate Git credentials for this user:
        
        \* Under the "Security credentials" tab of the user, click on the "Create access key."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690016851741/562e73b2-c1b3-447e-9b6d-879fb599031c.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690016425494/b7971067-bd34-4298-ac83-2ac7d53ddce9.png align="center")
        
        \* Download or take note of the "Access key ID" and "Secret access key" that will be generated. You will use these to configure Git credentials locally.
        
* **Configure Git Credentials Locally and Clone the CodeCommit Repository:**
    
    * Open your terminal on your local machine where you want to clone the repository.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690016997115/2caf7bb9-b43c-4af5-b896-82d05ba20f34.png align="center")
    
    * Go back to the AWS Management Console and navigate to the "demo-app" repository in CodeCommit.
        
    * Click on the "Clone URL with HTTPs" button to get the repository URL.
        
    * In your terminal, navigate to the directory where you want to clone the repository.
        
    * Clone the repository using Git:
        
        ```yaml
        git clone <repository_url> #https://git-codecommit.us-east-1.amazonaws.com/v1/repos/demo-app
        ```
        
        Replace `<repository_url>` with the URL obtained from the CodeCommit repository.
        
    * Enter the "username" and "password" when prompted.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690017723507/fa05f799-9564-4ea6-95df-60d5e26b4a66.png align="center")
        
    * Now, you have cloned the CodeCommit repository locally.
        

---

# Task-02 :

* ### Add a new file from local and commit to your local branch
    
* ### Push the local changes to the CodeCommit repository.
    

To add a new file locally, commit it to your local branch, and then push the changes to the CodeCommit repository.

* **Create and Add a New File Locally:**
    
    * Navigate to the directory where you recently cloned the CodeCommit repository on your local machine.
        
    * Create a new file in the project directory such as `index.html`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690019484698/0b2bb02f-9356-443b-9f46-fe39732e8383.png align="center")
        
* **Add and Commit the New File Locally:**
    
    * Use the following Git commands to add and commit the new file to your local branch:
        
        ```yaml
        git add .
        git commit -m "added demo-app sample file"
        ```
        
* **Push Local Changes to CodeCommit Repository:**
    
    After committing the changes locally, you can push them to the CodeCommit repository using the following Git command:
    
    ```yaml
    git push origin <your_branch_name> #Replace <your_branch_name> with the name of the branch you are working on.
    git push origin master
    ```
    
    If you are working on a different branch, replace `master` with the appropriate branch name.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690019752427/fd1ea2f8-0694-4c8b-ac0c-9bfd364961ce.png align="center")

* **Verify Changes in CodeCommit:**
    
    * Go back to the AWS Management Console and navigate to your CodeCommit repository.
        
    * You should see the newly added `index.html`
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690020018812/fbf4270b-ddbc-4781-917e-a6a546b68c91.png align="center")
    
    ---
    

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**