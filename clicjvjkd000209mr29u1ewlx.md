---
title: "Day 24 & 25 Task: Complete Jenkins CI/CD Project"
datePublished: Thu Jun 01 2023 03:01:46 GMT+0000 (Coordinated Universal Time)
cuid: clicjvjkd000209mr29u1ewlx
slug: day-24-25-task-complete-jenkins-cicd-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685560814781/90893030-be58-4016-a370-769fcf33c495.png
tags: docker, devops, jenkins, 90daysofdevops, trainwithshubham

---

### What is GitHub webhook?

A GitHub webhook is like a notification system that lets external services know when certain events happen in a GitHub repository. It sends a message to a specified URL whenever something important occurs, such as a new commit, a pull request, or an issue being opened. This helps automate tasks or integrate GitHub with other tools, allowing for real-time updates and streamlined workflows.

Here are some key features of GitHub webhooks presented in bullet points:

* **<mark>Real-time notifications:</mark>** Get instant updates when specific events happen in a GitHub repository.
    
* **<mark>Customizable events:</mark>** Choose which events trigger the webhook, such as commits, pull requests, or issues.
    
* **<mark>Automated actions: </mark>** Automate tasks or workflows based on webhook events, like triggering builds or deployments.
    
* **<mark>Integration capabilities: </mark>** Seamlessly integrate GitHub with other tools and services.
    
* **<mark>Security measures:</mark>** Implement encryption and authentication to ensure secure communication.
    
* **<mark>Configurable settings:</mark>** Easily configure and manage webhooks using GitHub's user-friendly interface.
    
* **<mark>Flexibility:</mark>** Adapt webhooks for various purposes like CI/CD, issue tracking, or notifications.
    

---

## Connection Between GitHub & Jenkins

**<mark>Step 1--&gt;</mark>** Generate SSH keys on the Jenkins server with the **<mark>"ssh-keygen"</mark>** command.

1. Type the `ssh-keygen` command and press Enter.
    
2. You will be prompted to specify the location to save the keys. Press Enter to accept the default location, or provide a desired file path.
    
3. The `ssh-keygen` command will generate both the public and private keys. The public key will have a ".pub" extension and the private key will have no extension.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685536756324/e122ebca-514c-41e0-b729-3e41c5d76345.png align="center")
    
4. Navigate to the **<mark>".ssh"</mark>** and access the **<mark>"id_rsa.pub"</mark>** public key with "**<mark>cat id_rsa.pub"</mark>** command.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685537169755/401a2864-61a9-4818-aab8-120ef857f20b.png align="center")

1. Copy the public key.
    

<mark>Step 2--&gt;</mark>\*\*Configure the GitHub

Copy the generated SSH public key on the Jenkins server and add the public key to your GitHub account. This allows Jenkins to securely interact with your GitHub repository.

1. Go to the GitHub Account Settings. Then navigate to **SSH and GPG keys** and fill out the details and paste the public key.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685538113759/13708a2a-1ca2-4a13-8f5d-60b7ede68ec4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685538332479/49669eb3-8fbd-4c79-a102-8833d37cc55d.png align="center")

---

## Set up a pipeline for a Node-Todo application

**<mark>Step 1--&gt;</mark>** **Create a new Jenkins job:** In the Jenkins dashboard, click on "New Item" to create a new job. Choose a suitable job type, such as a Freestyle project or a Pipeline, and configure it accordingly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685538735469/134c5c39-37e0-4a1d-8832-59cf9de858de.png align="center")

**<mark>Step 2--&gt;</mark>** In the job configuration, provide the **Description** and **GitHub project URL**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685539008621/a5a370c5-9076-4eae-9138-05f4d0bc2993.png align="center")

**<mark>Step 3--&gt;</mark>** In **Source Code Management**, provide the **<mark>GitHub repository URL</mark>**, and select the appropriate **<mark>branch</mark>**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685539596326/9a168b47-bc3a-430e-af80-9dbab68a9657.png align="center")

**<mark>Set up the credentials for Jenkins to access the repository.</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685539426850/ded607f9-cc27-42f5-814a-31085d229ec5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685539451640/0c34b6cb-6667-4860-847c-14c49f068183.png align="center")

**<mark>Step 4--&gt;</mark>** Now, go to **<mark>Build Steps</mark>** and choose the **<mark>execute shell build</mark>** option.

```python
docker-compose down
docker-compose up -d
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685539945518/e0a8ba0c-5e4e-45cc-aeda-1a674dcaf7df.png align="center")

**<mark>Note:</mark>** Docker-Compose uses the YAML file which is present in the project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685540173835/39deeaf8-093f-4729-af74-599cdbeeadfb.png align="center")

**<mark>Step 5--&gt;</mark>** Now click on **SAVE** and go to **<mark>Build Now</mark>** and click on it and check for console output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685540339300/0194c3fd-9f93-4bb2-bfa2-eafd27d0d086.png align="center")

**<mark>Step 6--&gt;</mark>** Once the output shows **<mark>Finished: SUCCESS</mark>** that means our application is ready.

Add port 8000 in the inbound rules in the EC2 instance security group.

To test the application deployment, open the application with xx.xx.xx.xx:8000 (replace xx with your IP address) in the browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685540708305/947cabcc-d02c-41ba-9eb8-2b4230739670.png align="center")

---

### Setting up Webhook:-

<mark>Step 1--&gt;</mark>Navigate to the **Manage Jenkins** option from your Jenkins dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685540971789/16434d32-43b6-45ee-b115-824cec2c9fa8.png align="center")

<mark>Step 2--&gt;</mark>Then Choose the **Manage Plugins** option --&gt; Then install a plugin for GitHub integration with Jenkins called **GitHub Integration.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685541202901/5b3600a4-1805-4a69-83a3-cc021f9ec51b.png align="center")

**<mark>Step 3--&gt;</mark>**Install and Restart Jenkins.

**<mark>Step 4--&gt;</mark>Configure Webhook in GitHub:** In your GitHub repository, go to "Settings" &gt; "Webhooks" &gt; "Add webhook." Provide the Jenkins webhook URL “**&lt;Jenkins url&gt;/github-webhook/**”, select the events to trigger the webhook (e.g., push, pull request), and save the webhook configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685541789084/387cd308-bb67-45bb-a7f7-cbadc1037d98.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685541810676/093a370e-6c40-4a9c-aa73-d7f01ee0475b.png align="center")

**<mark>Step 5--&gt;</mark>Now in Jenkins, Go to "Dashboard" &gt; "node-todo-cicd" &gt; "configuration" &gt; "Build Triggers" and check ✅GitHub Hook trigger for GITScm pooling** and save it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685542195745/95d60a3c-1a95-4362-b7e2-b5de1802a509.png align="center")

**<mark>Step 6--&gt;</mark>Test the Connection:** Make a change in your GitHub repository, such as pushing new code or creating a pull request. Check if Jenkins receives the webhook notification and triggers the associated build job.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685544371093/4b5385c8-3a78-48c1-8500-b6c2c5389bc5.png align="center")

**As soon as changes are committed, the new build will be initiated automatically in Jenkins.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685544402449/d6d85c38-e495-4c2e-80ff-50896d887290.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685544497838/3a815ea4-9618-4ac5-b244-0a12edff2c01.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685544541463/fcb814c3-b267-4192-8a1b-2255d488bb3f.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**.**