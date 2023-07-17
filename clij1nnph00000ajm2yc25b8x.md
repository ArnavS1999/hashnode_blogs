---
title: "Jenkins Project"
datePublished: Mon Jun 05 2023 16:06:08 GMT+0000 (Coordinated Universal Time)
cuid: clij1nnph00000ajm2yc25b8x
slug: jenkins-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685980608457/6dfe6f1d-bf47-4dd6-bebf-be5110f5b235.png
tags: learning, devops, jenkins, 90daysofdevops, trainwithshubham

---

### Jenkins Master

Jenkins Master is the central control hub of Jenkins that manages jobs, schedules build, coordinates agents, and handles the overall automation process. It acts as the brains behind the operation, orchestrating the CI/CD pipeline and ensuring the smooth execution of tasks.

### Jenkins Agent

Jenkins Agent is a worker node that performs tasks delegated by the Jenkins Master. It executes build and deployment processes, runs tests, and carries out other automation tasks. Agents connect to the master, receive instructions, and provide the computing power needed to execute jobs, allowing for distributed and parallelized workflows.

**OR**

An agent is typically a machine or container that connects to a Jenkins master and this agent executes all the steps mentioned in a Job. When you create a Jenkins job, you have to assign an agent to it. Every agent has a label as a unique identifier.

When you trigger a Jenkins job from the master, the actual execution happens on the agent node that is configured in the job.

A single, monolithic Jenkins installation can work great for a small team with a relatively small number of projects. As your needs grow, however, it often becomes necessary to scale up. Jenkins provides a way to do this called “master to agent connection.” Instead of serving the Jenkins UI and running build jobs all on a single system, you can provide Jenkins with agents to handle the execution of jobs while the master serves the Jenkins UI and acts as a control node.

![](https://user-images.githubusercontent.com/115981550/215276859-fa140ab7-e905-41c9-8ae2-1eef577c5e72.png align="center")

---

### **Deploy web app using Jenkins master and worker node.**

Here we will deploy a web app through Jenkins master to the Jenkins worker node.

**<mark>Step 1--&gt;</mark>** Create 2 EC2 instances **Jenkins -master** & **Jenkins -agent.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685963941733/0d84df79-8010-4f2a-bb31-80eef0d9740a.png align="center")

**<mark>Step 2--&gt;</mark>** Before proceeding with the deployment using Jenkins Master and a worker node, please ensure that the Jenkins Master node has Jenkins preinstalled and the worker node (agent) has Java preinstalled. Jenkins relies on Java for its execution.

**<mark>Step 3--&gt;</mark>** Generate SSH keys on “Jenkins-server” by running “ssh-keygen”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685964888029/14c50fe4-4b86-4f21-8e9d-1a54823551f0.png align="center")

**<mark>Step 4--&gt;</mark>** Now navigate to the **“.ssh”** folder and there will be public and private keys in Jenkins-master.

Copy the public key.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685965361434/674c5f6f-7e7e-4661-82f9-8ca195d226de.png align="center")

**<mark>Step 5--&gt;</mark>** Add public key from **<mark>“Jenkins-master”</mark>** to **<mark>“Jenkins-agent"</mark>** under location **“.ssh/authorized\_keys”.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685965729864/86d16ba9-713c-42b8-af86-b54d1ea1eb41.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685965739964/e88cf31c-81c3-4569-a42f-1a210b75e29e.png align="center")

**<mark>Step 6--&gt;</mark>** Go to the Jenkins dashboard -&gt; **manage Jenkins** -&gt; **Manage Nodes and Clouds**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685966106038/8d715483-6b12-405d-bb43-e3b055e0ff44.png align="center")

**<mark>Step 7--&gt;</mark>** Now, click on “+ New Node”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685966290446/a10cec2f-847f-4168-a86b-d73a25e7e579.png align="center")

**<mark>Step 8--&gt;</mark>** Add details of your second node, accordingly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685967363246/6c759533-b6f9-4b13-9662-8124ce1cd885.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685967395499/89025f05-af30-46e4-87d2-8a160042a111.png align="center")

**<mark>Provide the Credentials and Give the private key of "Jenkins-master".</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685967640599/af9d386a-7ef0-45ea-a6b5-b9e581625b9b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685967656072/ea19ee87-6d83-4d0c-a8b6-600fbdc80367.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685967754606/a7becd98-ae1e-46ee-9cc7-15fd345485c8.png align="center")

**<mark>After clicking on Save Node will be connected and online.</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685967991857/15496aef-c7e4-4f70-ad7d-0e190c58f4e4.png align="center")

**<mark>Step 9--&gt;</mark>** Write JenkinsFile and Commit in your project GitHub Repository.

```python
 pipeline{
     agent { label "dev-server" }
     stages{
         stage("Clone Code"){
             steps{
                 git url: "https://github.com/ArnavS1999/node-todo-cicd.git", branch: "master"
             }
         }
         stage("Build and Test"){
             steps{
                 sh "docker build . -t node-app-test-new"
             }
         }
         stage("Push to Docker Hub"){
             steps{
                 withCredentials([usernamePassword(credentialsId:"DockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                 sh "docker tag node-app-test-new ${env.dockerHubUser}/node-app-test-new:latest"
                 sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                 sh "docker push ${env.dockerHubUser}/node-app-test-new:latest"
                 }
             }
         }
         stage("Deploy"){
             steps{
                 sh "docker-compose down && docker-compose up -d"
             }
         }
     }
 }
```

1. `pipeline{`: Starts the definition of the pipeline block.
    
2. `agent { label "dev-server" }`: Specifies that the pipeline should run on a node with the label "dev-server".
    
3. `stages{`: Begins the stages block, which contains individual stages of the pipeline.
    
4. `stage("Clone Code"){`: Defines a stage named "Clone Code".
    
5. `steps{`: Begins the steps block for the "Clone Code" stage.
    
6. `git url: "`[`https://github.com/ArnavS1999/node-todo-cicd.git`](https://github.com/ArnavS1999/node-todo-cicd.git)`", branch: "master"`: Clones the code repository from the specified URL and the "master" branch.
    
7. `stage("Build and Test"){`: Defines a stage named "Build and Test".
    
8. `steps{`: Begins the steps block for the "Build and Test" stage.
    
9. `sh "docker build . -t node-app-test-new"`: Builds a Docker image named "node-app-test-new".
    
10. `stage("Push to Docker Hub"){`: Defines a stage named "Push to Docker Hub".
    
11. `steps{`: Begins the steps block for the "Push to Docker Hub" stage.
    
12. `withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){`: Retrieves Docker Hub credentials stored in Jenkins.
    
13. `sh "docker tag node-app-test-new ${env.dockerHubUser}/node-app-test-new:latest"`: Tags the Docker image with the provided username and pushes it to Docker Hub.
    
14. `sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"`: Logs in to Docker Hub using the provided credentials.
    
15. `sh "docker push ${env.dockerHubUser}/node-app-test-new:latest"`: Pushes the tagged Docker image to Docker Hub.
    
16. `stage("Deploy"){`: Defines a stage named "Deploy".
    
17. `steps{`: Begins the steps block for the "Deploy" stage.
    
18. `sh "docker-compose down && docker-compose up -d"`: Shuts down existing containers and deploys new containers using the `docker-compose` command.
    

The pipeline executes each stage sequentially, performing the specified steps within each stage.

**<mark>Step 10--&gt;</mark>** To push the Docker image to Docker Hub we have to tell Docker Hub Credientaial to Jenkins.

**Manage Jenkins --&gt; Credentials--&gt;Stores scoped to Jenkins--&gt;global**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685976153453/d0fc92cd-87b2-42eb-88e4-c337e6a30f48.png align="center")

**Fill in your DockerHub Username and Password.**

**<mark>Step 11--&gt;</mark>** Now create Pipeline Project by clicking **"New Item"** from the Jenkins dashboard.

**<mark>Step 12--&gt;</mark>** Enter **"Name"** and select **"Pipeline"** as the project type and enter **ok**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685976549003/e0e51593-adf1-41cb-b096-ea5fc413ffb0.png align="center")

**<mark>Step 13--&gt;</mark>** In the "Pipeline" section, select "Pipeline SCM" enter Git repo URL and click on "Save" to save your job configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685978193402/7d24cc6c-c99c-415e-8f32-edee13658846.png align="center")

**<mark>Step 14--&gt;</mark>** Now run your Pipeline by clicking on the **"Build Now"** button on the job's dashboard page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685978500137/9249c109-18c1-40e8-aaf5-3b288355c9fd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685978949990/26548016-89b6-440e-8d3f-358720583548.png align="center")

**Docker Image is pushed to DockerHub successfully.**

**<mark>Step 15--&gt;</mark>** Once the build is successful, verify whether we can browse the application or not. **&lt;ip of Jenkins agent:8000&gt;**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685978822680/f3cbd5ab-8adf-418f-b1e4-fb6327c7a1f8.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**.**