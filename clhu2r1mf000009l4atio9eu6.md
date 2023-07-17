---
title: "Docker Project for DevOps Engineers"
datePublished: Fri May 19 2023 04:42:32 GMT+0000 (Coordinated Universal Time)
cuid: clhu2r1mf000009l4atio9eu6
slug: docker-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684471222966/111d4bf1-e209-47ab-9923-41de61c9ea0d.png
tags: docker, aws, devops, docker-images, 90daysofdevops

---

## Dockerfile

A Dockerfile is a text file that contains instructions for building a Docker image. It defines what software, dependencies, and configurations are needed for an application to run correctly in a Docker container. Dockerfile simplifies the process of creating and deploying applications by providing a standardized way to package and distribute software, making it easier to manage and replicate across different environments.  
Dockerfile instructions are used to define the steps required to build a Docker image. Here are some commonly used instructions:

1. FROM: Specifies the base image for your Docker image.
    
2. RUN: Executes commands inside the container during the image build.
    
3. COPY: Copies files or directories from the host machine to the container.
    
4. ADD: Similar to COPY, but can also handle URLs and automatically extracts compressed files.
    
5. ENV: Sets environment variables inside the container.
    
6. EXPOSE: Informs Docker that the container listens on specific network ports at runtime.
    
7. CMD: Provides default commands to be executed when the container starts.
    
8. ENTRYPOINT: Configures a command or script to run as the main process in the container.
    
9. WORKDIR: Sets the working directory for subsequent instructions.
    
10. VOLUME: Creates a mount point and specifies that the directory should be persisted outside the container.
    

## **Task:**

* Create a Dockerfile for a simple web application (e.g. a Node.js or Python app)
    
* Build the image using the Dockerfile and run the container
    
* Verify that the application is working as expected by accessing it in a web browser
    
* Push the image to a public or private repository (e.g. Docker Hub )
    

**<mark>Step 1-&gt;</mark>** **Clone the GitHub repository of the project**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684466688533/bdc43b9f-6e9b-4916-8c34-463a0af9083e.png align="center")

**<mark>Step 2-&gt;</mark>** **Create Dockerfile inside the repository with "vim Dockerfile" command.**

**<mark>Step 3-&gt;</mark>** **Adding instructions to build the Docker image.**

* <mark>"FROM node:12.2.0-alpine"</mark> specifies the base image as Node.js version 12.2.0 on Alpine Linux.
    
* <mark>"WORKDIR app" </mark> sets the working directory inside the container as "/app".
    
* <mark>"COPY . ."</mark> copies all files from the current directory to the container's "/app" directory.
    
* <mark>"RUN npm install" </mark> installs the project dependencies inside the container.
    
* <mark>"RUN npm run test"</mark> runs the tests for the application inside the container.
    
* <mark>"EXPOSE 8000"</mark> exposes port 8000, allowing external access to the container on that port.
    
* <mark>"CMD ["node","app.js"]"</mark> defines the command to be executed when the container starts, running the "app.js" file with Node.js.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684467102544/ef028ff9-4ddf-4df0-a03e-17dd581d8bf2.png align="center")

**<mark>Step 4-&gt;</mark>** **Build the image using the Dockerfile.**

Using the command **"sudo docker build . -t node-todo-cicd:latest".**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684467550000/a41fe8fc-ea47-4b9a-a202-3e5126a7ce11.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684467575074/9e843e0e-e968-438a-bc3f-7bb037ffb772.png align="center")

**<mark>Step 5-&gt;</mark>** **After successfully creating an image, create and run the container from that image.**

Using the command **"docker run -d -p 8000:8000 node-todo-cicd:latest".**

* <mark>"docker run"</mark>: This is the command to run a Docker container.
    
* <mark>"-d"</mark>: It runs the container in **detached mode**, which means it runs in the background.
    
* <mark>"-p 8000:8000"</mark>: It maps port 8000 of the host machine to port 8000 of the container. This allows accessing the containerized application on port 8000 of the host.
    
* <mark>"node-todo-cicd:latest"</mark>: It specifies the name of the Docker image to use, in this case, "node-todo-cicd" with the "latest" tag.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684468253153/9e622c48-bb21-4afe-95f3-b197bb742a27.png align="center")

**<mark>Step 6-&gt;</mark>** **Verify that the application is working as expected by accessing it in a web browser.**

Before accessing the application we have to add port "8000" in AWS ModifyInboundSecurityGroupRules in Security Groups to allow access to run application in web browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684468983584/e3ee871d-176c-4e25-a761-110a16446c77.png align="center")

application is successfully running.

**<mark>Step 7-&gt;</mark>** **Push the image to a public or private repository (e.g. Docker Hub ).**

\-&gt;First create a DockerHub profile.

\-&gt;Create a public repository.

\-&gt;Login DockerHub on host machine.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684469568665/09ceb930-716d-4f7a-bef3-1735a4ccf01f.png align="center")

\-&gt;With the command **"docker push arnavs1999/node-todo-cicd:latest"**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684469995974/af533993-ad6c-4f9c-a643-6cfd6c674ad2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684470066643/f48593ed-3c7d-4038-a1e2-2e64159ff235.png align="center")

<mark>The image is successfully pushed to DockerHub repository</mark>

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/)