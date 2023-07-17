---
title: "Day 23 Task: Jenkins Freestyle Project for DevOps Engineers."
datePublished: Wed May 31 2023 04:42:06 GMT+0000 (Coordinated Universal Time)
cuid: clib80q9x000009mg4tob2uv4
slug: day-23-task-jenkins-freestyle-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685508041075/c08fedd9-1af5-4de8-9a52-afa9a9a52b7b.webp
tags: devops, jenkins, devops-articles, 90daysofdevops, trainwithshubham

---

## What is CI/CD?

CI/CD stands for Continuous Integration and Continuous Delivery (or Continuous Deployment). It is a set of practices and tools that enable developers to automate the process of building, testing, and deploying software applications.

In simple terms, CI/CD helps teams deliver software faster and more reliably. Here's how it works:

1. **<mark>Continuous Integration: </mark>** Developers frequently integrate their code changes into a shared repository. With CI, these changes are automatically built and tested, ensuring that they don't break the existing codebase. This helps catch issues early on and maintains code quality.
    
2. **<mark>Continuous Delivery:</mark>** Once code changes pass the CI process, they are automatically deployed to a staging or testing environment. This allows for further testing and validation by stakeholders, including quality assurance teams and product owners.
    
3. **<mark>Continuous Deployment:</mark>** In the case of continuous deployment, code changes that successfully pass all tests and validations are automatically deployed to production, making them instantly available to users.
    

The benefits of CI/CD include faster time to market, improved code quality, and reduced risk of deployment failures. It enables teams to iterate quickly, deliver features more frequently, and respond to customer feedback faster.

## What Is a Build Job?

In simple terms, a Build job is a specific task performed by a build tool or a CI/CD system like Jenkins. It involves the process of compiling, testing, and packaging source code to create a deployable artifact, such as an executable file, library, or container image.

A build job is a task performed by a build tool or CI/CD system. It involves:

1. Compiling source code into executable code or libraries.
    
2. Running tests to check code functionality and stability.
    
3. Packaging code into a deployable artifact.
    
4. Managing dependencies required by the code.
    
5. Ensuring code quality and identifying bugs.
    
6. Preparing code for deployment.
    
7. Facilitating collaboration among developers.
    
8. Supporting continuous integration and delivery of software.
    

## What are Freestyle Projects?

Freestyle projects in Jenkins are flexible and customizable projects where you can define build steps, scripts, and triggers. They allow you to build, test, and deploy software with control and adaptability to project needs.

---

# Task-01

* **create an agent for your app. ( which you deployed from docker in the earlier task)**
    
* **Create a new Jenkins freestyle project for your app.**
    
* **In the "Build" section of the project, add a build step to run the "docker build" command to build the image for the container.**
    
* **Add a second step to run the "docker run" command to start a container using the image created in step 3.**
    

In This Task, we are using <mark>React Django App</mark>.

**<mark>Step 1 --&gt;</mark>** Proceed with creating New Item.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685451156385/82753ace-6448-43b9-a345-14b8be1087d4.png align="center")

**<mark>Step 2 --&gt;</mark>** Name the Project "**React\_Django\_app**" choose Freestyle Project and click ok.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685451326994/4c6ea69c-a2e4-4216-b322-b74141ec4574.png align="center")

**<mark>Step 3 --&gt;</mark>** Now give the description and give the Github project URL of the project "[React\_Django\_app](https://github.com/ArnavS1999/react_django_demo_app)"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685451635852/89d6718b-4421-4488-8d7f-a78e932c3b64.png align="center")

**<mark>Step 4 --&gt;</mark>** In **Source Code Management** choose **Git** because we need to provide the **Repositories URL** and Branch name in **Branch Specifier.** Since the project branch is attached to the **main branch** so we will specify the **main** in Branch Specifier.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685451929644/d50a493a-b384-45ca-9349-d42d1bc6c41d.png align="center")

**<mark>Step 5 --&gt;</mark>** Add a build step by clicking on "Add build step" and selecting "Execute shell".

Enter the following commands to build the Docker image for your app and to start a container using the Docker image created.

```python
docker build . -t react_django_app
#####docker build:--> This command is used to build a Docker image.
#####(.):--> The period (dot) represents the build context, indicating that the Dockerfile and application files are present in the current directory.
#####-t react_django_app:--> The -t flag is used to specify the tag or name for the Docker image. In this case, the image will be tagged as react_django_app

docker run -d --name react_django_app -p 8001:8001 react_django_app:latest
#####docker run:--> This command is used to start a Docker container.
#####-d: The -d flag runs the container in detached mode, which means it will run in the background.
#####--name react_django_app:--> The --name flag is used to give a name to the container. In this case, the container will be named react_django_app.
#####-p 8001:8001:-->The -p flag is used to map the port of the host machine to the port of the container. In this case, port 8001 of the host machine is mapped to port 8001 of the container.
#####react_django_app:latest:-->The react_django_app:latest specifies the image to be used for creating the container.The :latest tag is used to specify the latest version of the image.
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685453248791/4e114f0d-fafb-4d64-b2e6-3d3ad106d156.png align="center")

**<mark>Step 6 --&gt;</mark>** Now before running the **build now** make sure that the below commands are installed in the Ubuntu machine.

```python
sudo apt-get install docker.io -y
sudo usermod -aG docker jenkins
sudo reboot
```

**<mark>Note:-</mark>** <mark> It is compulsory to add </mark> **<mark>jenkins user to docker group</mark>** <mark> otherwise it will show error while building.</mark>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685457629901/6d574cd4-6ad3-4d5c-858a-8773f726dd60.png align="center")

Adding the `jenkins` user to the `docker` group using the `sudo usermod -aG docker jenkins` command is a common step to grant the Jenkins user the necessary permissions to interact with Docker. This allows Jenkins to execute Docker commands without encountering permission errors.

```python
sudo usermod -aG docker jenkins
```

After completing these steps, the `jenkins` user should have the necessary permissions to interact with Docker.

**<mark>Step 7--&gt;</mark>** Now click on **<mark>Build Now.</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685457929720/3a0a390f-3eaa-48c1-9c8c-c9a4574504a7.png align="center")

**<mark>Step 8 --&gt;</mark>** Once the output shows **<mark>Finished: SUCCESS</mark>** that means our application is ready.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685458270938/0c57968d-1df3-4582-8f8b-4c69e0396db9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685458288659/f8de269a-3300-47d8-aeb8-0728f6561520.png align="center")

**<mark>Step 9 --&gt;</mark>** Access your Application.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685458550387/c0908a50-3283-4564-8e58-2abfd4df386e.png align="center")

---

---

# Task-02

* **Create Jenkins project to run the "docker-compose up -d" command to start the multiple containers defined in the compose file (Hint- use day-19 Application & Database docker-compose file)**
    
* **Set up a cleanup step in the Jenkins project to run the "docker-compose down" command to stop and remove the containers defined in the compose file.**
    

**<mark>Step 1--&gt;</mark>** Using the same **React\_django\_app project**

Before running the "**docker-compose up -d**" we need to install docker-compose in our Ubuntu machine.

Use the below command to install docker-compose

```python
sudo apt-get install docker-compose -y
```

**<mark>Step 2--&gt; </mark>** Now give the docker-compose commands in **Execute shell.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685459175949/f7ae17fa-73b0-4d6e-90be-2ee2cee957fe.png align="center")

```python
docker-compose down
docker-compose up -d
```

**<mark>Note:</mark>** Docker-Compose uses the YAML file which is present in the project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685459337531/696f4eb7-1d26-416e-8fd4-7dd7829b2dcb.png align="center")

**<mark>Step 3--&gt; </mark>** Now go back to **<mark>Build Now</mark>** and click on it and check for console output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685459634378/4eabe9ea-1e5c-4bb9-a273-c82a3ef2ee14.png align="center")

**<mark>Step 4--&gt;</mark>** Once the output shows **<mark>Finished: SUCCESS</mark>** that means our application is ready.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685459705705/242deff3-72ab-427d-b251-cfd4dc2bc9e6.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/)