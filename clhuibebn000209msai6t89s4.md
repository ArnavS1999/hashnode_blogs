---
title: "Day 18 Task: Docker for DevOps Engineers"
datePublished: Fri May 19 2023 11:58:15 GMT+0000 (Coordinated Universal Time)
cuid: clhuibebn000209msai6t89s4
slug: day-18-task-docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684497374207/76bcc865-36ed-4a78-a6aa-57f17983e3e7.png
tags: linux, docker, devops, docker-compose, 90daysofdevops

---

## Docker Compose

Docker Compose simplifies managing multi-container applications. It uses a YAML file to define services, networks, and volumes. With a single command, it creates and manages the entire application stack. It simplifies the setup, orchestration, and management of containers, ensuring consistent and reproducible deployments across different environments.

or

* Docker Compose is a tool that was developed to help define and share multi-container applications.
    
* With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.
    

## What is YAML?

* YAML is a human-readable data serialization format.
    
* It uses indentation and plain text to represent structured data.
    
* YAML is commonly used for configuration files.
    
* It is easy for humans to write and understand.
    
* YAML supports lists, dictionaries, and scalar values.
    
* It allows the representation of complex data structures.
    
* YAML is used in applications like Docker Compose and Kubernetes.
    
* It is widely used for configuration files in various programming languages.
    
* YAML's simplicity and readability make it popular for managing structured data.
    
* YAML files use a .yml or .yaml extension.
    

## Task-1

Learn how to use the docker-compose.yml file, to set up the environment, configure the services and links between different containers, and also to use environment variables in the docker-compose.yml file.

\--&gt;docker-compose.yml

```plaintext
  version : "3.3"
  services:
    web:
      image: nginx:latest
      ports:
        - "80:80"
    db:
      image: mysql
      ports:
        - "3306:3306"
      environment:
        - "MYSQL_ROOT_PASSWORD=test@123"
```

* <mark>"version: '3.3'"</mark>: Specifies the version of Docker Compose being used.
    
* <mark>"services"</mark>: Starts the service definitions section.
    
* <mark>"web":</mark> Defines the "web" service.
    
    * <mark>"image: nginx:latest":</mark> Specifies that the service should use the latest version of the NGINX container image from Docker Hub.
        
    * <mark>"ports":</mark> Maps ports between the host and container.
        
        * <mark>"80:80"</mark>: Exposes port 80 of the host machine to port 80 of the NGINX container.
            
* <mark>"db":</mark> Defines the "db" service.
    
    * <mark>"image: mysql":</mark> Specifies that the service should use the MySQL container image from Docker Hub.
        
    * <mark>"ports":</mark> Maps ports between the host and container.
        
        * <mark>"3306:3306":</mark> Exposes port 3306 of the host machine to port 3306 of the MySQL container.
            
    * <mark>"environment":</mark> Sets environment variables for the MySQL container.
        
        * <mark>"MYSQL_ROOT_PASSWORD=test@123":</mark> Defines the root password for the MySQL instance as "test@123".
            

***This Docker Compose file will create two containers: one running NGINX and another running MySQL. The NGINX container will be accessible on port 80 of the host machine, while the MySQL container will be accessible on port 3306.***

Two commands are used in Docker compose

```plaintext
docker-compose down
docker-compose up -d
```

* <mark>"docker-compose down":</mark> Stops and removes the containers, networks, and volumes defined in the Docker Compose file. It essentially shuts down the services defined in the Compose file and cleans up associated resources.
    
* <mark>"docker-compose up -d":</mark> Starts the containers defined in the Docker Compose file in detached mode, meaning the containers run in the background. This command creates and starts the services defined in the Compose file, allowing them to operate independently.
    

These commands are often used together to gracefully stop and remove existing containers with "docker-compose down" and then start fresh containers in the background with "docker-compose up -d".

## Task-2

* **Pull a pre-existing Docker image from a public repository (e.g. Docker Hub) and run it on your local machine.**
    

\--&gt; To find images in DockerHub use the command

```plaintext
docker search nginx
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684494962771/bd3b89bf-73b2-4a03-bc74-56c32f77a8f4.png align="center")

\--&gt; Now download this image to your local machine with the command

```plaintext
docker pull nginx
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684494987480/44e5b58d-986d-4cb9-a6be-15468cd4812b.png align="center")

\--&gt; Run the container as a non-root user. Make sure you reboot the instance after giving permission to the user.

```python
  sudo usermod -aG docker $USER
  docker reboot
#(By running this command, the current user is granted permission to execute Docker commands without needing to use the "sudo" prefix each time.)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684494076172/1b894fd4-a607-4a55-8ef4-0a943ea72942.png align="center")

```python
docker run -d nginx
#(-d --> detached mode, this will run ngnix in background)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684495216312/af40ab50-6dc7-4081-ac50-384f77dc2af8.png align="center")

* **Inspect the container's running processes and exposed ports using the docker inspect command.**
    

```python
docker inspect d0c7ba7e7ab4 #(container ID)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684495490404/9dc8263a-3391-464b-9153-5311bd808987.png align="center")

To view exposed ports then scroll down and look

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684495596193/41c7dd22-a92a-4203-93f0-a9ab8992d079.png align="center")

* **Use the docker logs command to view the container's log output.**
    

```python
docker logs d0c7ba7e7ab4 #(container ID)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684495728248/c94ab848-b213-4d77-a952-2b2c7e108c1a.png align="center")

To get a limited no. of line logs add **\--tail** in the above command or to get real-time logs generating add **\--follow** in the above command.

* **Use the docker stop and docker start commands to stop and start the container.**
    

```python
docker stop d0c7ba7e7ab4  #(will stop container)
docker start d0c7ba7e7ab4  #(will start container)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684496127662/86d816f2-ec1f-4a6a-8346-6b5760ab4d87.png align="center")

* **Use the docker rm command to remove the container when you're done.**
    

```python
docker kill d0c7ba7e7ab4 #this command will kill the running container 
docker rm d0c7ba7e7ab4 #this command remove the container 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684496586393/22c508a2-acfd-4daa-9af6-30716a359e36.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/)