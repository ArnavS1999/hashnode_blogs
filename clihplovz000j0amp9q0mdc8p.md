---
title: "Jenkins Declarative Pipeline with Docker"
datePublished: Sun Jun 04 2023 17:40:55 GMT+0000 (Coordinated Universal Time)
cuid: clihplovz000j0amp9q0mdc8p
slug: jenkins-declarative-pipeline-with-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685900377203/7bfe0016-1ed8-4039-9649-0007b8934ca4.png
tags: learning, devops, jenkins, 90daysofdevops, trainwithshubham

---

### Use your Docker Build and Run Knowledge

**docker build -** you can use `sh 'docker build . -t <tag>'` in your pipeline stage block to run the docker build command. (Make sure you have docker installed with correct permissions.

**docker run:** you can use `sh 'docker run -d <image>'` in your pipeline stage block to build the container.

**How will the stages look**

```python
stages {
        stage('Build') {
            steps {
                sh 'docker build -t trainwithshubham/django-app:latest'
            }
        }
    }
```

### Task-01

* **Create a docker-integrated Jenkins declarative pipeline.**
    
* **Use the above-given syntax using** `sh` **inside the stage block**
    
* **You will face errors in case of running a job twice, as the docker container will be already created, so for that do task 2**
    

**<mark>Step 1--&gt;</mark>** In Jenkins, to create a new pipeline job, click on **"New Item"** in the Jenkins dashboard, then select **"Pipeline"** as the project type.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685876086535/b3f0dd83-6cd9-4295-bd9c-bbce093a95ea.png align="center")

**<mark>Step 2--&gt;</mark>** After clicking **"OK,"** you can provide a description for the new pipeline job.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685877647072/e3af821f-e710-4bb5-97de-0de0475eb9cf.png align="center")

**<mark>Step 3--&gt;</mark>** In the configuration of the pipeline job, navigate to the **"Pipeline Script"** section and define your stages, steps, and parameters accordingly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685879804160/a308c04e-8755-49f5-b1b5-93dfdaac9b9a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685877916853/5f515979-d035-4416-b962-d953e2a88d23.png align="center")

```python
pipeline {
    agent any
    stages{
        stage ('Code Clone') {
            steps {
                git url : 'https://github.com/ArnavS1999/django-todo-cicd.git' , branch : 'develop'
            }
        }
        stage ('Build') {
            steps {
                sh 'docker build . -t  django-todo-cicd:latest'
            }
        }
        stage ('Testing') {
            steps {
                echo 'testing'
            }
        }
        stage ('Deploy') {
            steps {
                sh 'docker run -d -p 8000:8000 django-todo-cicd:latest'
            }
        }
    }
}
```

Inside the `stages` block:

* The `Code Clone` stage uses the `git` step to clone the code from the specified GitHub repository ([`https://github.com/ArnavS1999/django-todo-cicd.git`](https://github.com/ArnavS1999/django-todo-cicd.git)) and the `develop` branch.
    
* The `Build` stage uses the `sh` step to build a Docker image named `django-todo-cicd:latest` using the current directory (`.`).
    
* The `Deploy` stage uses the `sh` step to run the `django-todo-cicd:latest` Docker container in detached mode (`-d`) and maps port 8000 on the host to port 8000 in the container.
    

**<mark>Step 4--&gt;</mark>** **"Save"** and click on **"Build Now"** to start the pipeline.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685881229322/ff87ae3a-d22c-45cc-8164-9fb7dd2fec9e.png align="center")

**<mark>Step 5--&gt;</mark>** Console Output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685881547212/4e722c58-d5e3-49e2-b005-cb740c57eaea.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685881565587/49824dea-75d9-4330-8c99-e48ed2b1194b.png align="center")

**<mark>Step 6--&gt;</mark>** Verify whether we can browse the application or not.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685881666795/c7d72101-83b8-458f-8b8e-bd6a909c0cc3.png align="center")

**<mark>Step 7--&gt;</mark>** We will face errors in case of running a job twice, as the docker container is already created, **so for that do task 2.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685897820924/44e06989-edb4-42a6-aee2-74ddc39ffced.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685897855868/cde99353-f417-43f7-a7fc-ec4818bfcf53.png align="center")

---

### Task-02

* **Create a docker-integrated Jenkins declarative pipeline using the** `docker` **groovy syntax inside the stage block.**
    
* **Complete your previous projects using this Declarative pipeline approach.**
    

**<mark>Step 1--&gt; </mark>** We can address the error by utilizing `docker-compose` and modify the script to incorporate the `docker-compose down` and `docker-compose up` commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685898708701/7a5fedab-4d9d-4412-8ca8-4840d159da6e.png align="center")

**<mark>Step 2--&gt;</mark>** Click on **"Save"** and then click on **"Build Now"**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685898897121/b0262e23-8aff-4d2b-879a-638cf3817b8e.png align="center")

**<mark>Step 3--&gt; </mark>** Once the build is successful, check whether our application is working or not.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685899215471/e2b6898b-c1c5-43fb-b96b-b80c5c59c22f.png align="center")

**<mark>This approach helps manage containers more effectively, ensuring a clean environment before deployment and minimizing potential conflicts.</mark>**

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**.**