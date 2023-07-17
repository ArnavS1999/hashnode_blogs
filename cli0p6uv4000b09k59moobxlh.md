---
title: "Day 19 Task: Docker for DevOps Engineers"
datePublished: Tue May 23 2023 19:57:18 GMT+0000 (Coordinated Universal Time)
cuid: cli0p6uv4000b09k59moobxlh
slug: day-19-task-docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684871761042/6c39fa4c-ab96-46d8-8498-789a563d0d92.png
tags: docker, devops, docker-images, 90daysofdevops, trainwithshubham

---

## Docker-Volume

Docker allows you to create something called volumes. Volumes are like separate storage areas that can be accessed by containers. They allow you to store data, like a database, outside the container, so it doesn't get deleted when the container is deleted. You can also mount from the same volume and create more containers having the same data.

**<mark>Docker volumes are like secret hideouts for your container data. They give you a safe place to stash all your important stuff.</mark> With Docker volumes, you can keep your data separate from your containers, just like hiding your snacks from nosy roommates. It's like having a secret bunker where you can store files, databases, or even a collection of cat videos. You can mount volumes to specific paths in your containers, so it's like having a direct tunnel to your hidden treasure. The best part? <mark>Even if your containers throw a wild party or disappear into thin air, your data remains untouched, like a time capsule waiting to be discovered. Docker volumes keep your data safe, sound, and ready to party, no matter what happens.</mark>**

## Docker Network

Docker allows you to create virtual spaces called networks, where you can connect multiple containers (small packages that hold all the necessary files for a specific application to run). This way, the containers can communicate with each other and with the host machine (the computer on which the Docker is installed). When we run a container, it has its own storage space that is only accessible by that specific container. If we want to share that storage space with other containers, we can't do that.

**<mark>Docker networks are like cozy hangout spots for containers. It's where they can meet up, have a chat, and exchange high-fives. Think of it as a virtual club where containers can party together. They get their own private space to connect, share stuff, and collaborate like a well-oiled team. Docker networks make it easy for containers to socialize, boosting the awesomeness of your applications.</mark>**

Types of Docker Networks Drivers

1. <mark>Bridge: </mark> Default network driver, enables communication between containers on the same host.
    
2. <mark>Host: </mark> Shares host network with containers, eliminating network isolation.
    
3. <mark>Overlay:</mark> Facilitates communication between containers across multiple Docker hosts.
    
4. <mark>Macvlan:</mark> Assigns a MAC address to each container, enabling direct connection to the physical network.
    
5. <mark>None: </mark> Disables networking for containers, useful in specific scenarios where networking is not required.
    

Some Docker Network Commands that are mostly used :

1. <mark>Create: </mark> `docker network create`
    
2. <mark>List:</mark> `docker network ls`
    
3. <mark>Inspect:</mark> `docker network inspect`
    
4. <mark>Connect:</mark> `docker network connect`
    
5. <mark>Disconnect: </mark> `docker network disconnect`
    

---

## Task-1

* **Create a multi-container docker-compose file that will bring *UP* and bring *DOWN* containers in a single shot ( Example - Create application and database container )**
    

1. Before we dive into the project don't forget to give sudo permission to the USER for Docker.
    
    ```python
    sudo usermod -aG docker $USER
    ```
    
2. create a .yml file
    
    ```python
    vim docker-compose.yml
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684851998716/a858a383-2866-4c27-ab11-95260dbf967e.png align="center")

1. **Use the** `docker-compose up` **command with the** `-d` **flag to start a multi-container application in detached mode.**
    
    ```python
    docker-compose up -d
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684852697385/bd6763b3-2766-4aab-a257-fdca5d2c47e2.png align="center")

1. Use docker ps command to show running containers
    
    ```python
    docker ps
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684852847250/95611acf-3bfe-467c-9eaf-2a4ee1ab7e4a.png align="center")

---

* **Use the** `docker-compose scale` **command to increase or decrease the number of replicas for a specific service. You can also add** [`replicas`](https://stackoverflow.com/questions/63408708/how-to-scale-from-within-docker-compose-file) **in the deployment file for *auto-scaling*.**
    

```python
docker-compose up --scale flask-api=3
```

`docker-compose up --scale flask-api=3` scales the `flask-api` service to run three instances. This command will start additional containers for the `flask-api` service, resulting in three instances running simultaneously.

---

* **Use the** `docker-compose ps` **command to view the status of all containers, and** `docker-compose logs` **to view the logs of a specific service.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684853769705/d1f33dfe-e311-4ecd-8802-01bb66bb6aaa.png align="center")

---

* **Use the** `docker-compose down` **command to stop and remove all containers, networks, and volumes associated with the application**
    

```python
docker-compose down
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684853873630/aecb25cc-218f-479f-ae56-8783d48b6529.png align="center")

---

## Task-2

* **Learn how to use Docker Volumes and Named Volumes to share files and directories between multiple containers.**
    

Docker Volumes and Named Volumes are useful features for sharing files and directories between multiple containers. They provide a way to persist data and make it accessible to multiple containers, even if the containers are destroyed and recreated.

1. **Creating a Docker Volume**: To create a Docker Volume, you can use the `docker volume create` command.
    

```python
docker volume create mydocker-flaskapi
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684864399968/a341802e-57e2-4363-b19d-a2df46ccaf98.png align="center")

1. **Named Volumes**\-They are a type of Docker volume that is given a specific name when created, making it easier to reference and reuse across multiple containers.
    
2. **Mounting a Volume to a Container**: To use a volume in a container, you need to mount it by specifying the volume name and the mount point inside the container. You can do this with the `-v` or `--mount` flag when running a container.
    

```python
docker run -d -v mydocker-flaskapi:/app/data <image_name>
```

---

* **Create two or more containers that read and write data to the same volume using the** `docker run --mount` **command.**
    

**Run the First Container**: Start the first container and mount the shared volume to a directory inside the container. This container will write data to the shared volume:

```python
docker run -d --name container1 --mount source=mydocker-flaskapi,target=/data 51672fb1eeb9 #your 1st image id
```

**Run the Second Container**: Start the second container and also mount the shared volume to a directory inside the container. This container will read data from the shared volume

```python
docker run -d --name container2 --mount source=mydocker-flaskapi,target=/data 8b33e239cde6 #your 2nd image id
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684867717706/fe1a7485-fa00-4e59-b5a5-7b27cc245d31.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684868983371/bd6f3fa5-d963-4cdd-8b98-6c9ea8f6bfde.png align="center")

---

* **Verify that the data is the same in all containers by using the docker exec command to run commands inside each container.**
    

**Write Data to the Shared Volume-&gt;**Access "container1" and write some data to the shared volume. You can use the `docker exec` command to execute commands within the running container.

```python
docker exec -it container1 sh
echo "Data from container1" > /data/file.txt
```

**Read Data from the Shared Volume-&gt;**Access "container2" and read the data from the shared volume.

```python
docker exec -it container2 sh
cat /data/file.txt
```

<mark>The output should display the content written by "container1".</mark>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684869533935/212fac06-3755-44fd-b647-3589d03344ae.png align="center")

---

* **Use the <mark>docker volume ls</mark> command to list all volumes and <mark>docker volume rm </mark> command to remove the volume when you're done.**
    

NOTE:-Before removing the volume it is necessary to kill and stop both containers otherwise it will give an error like **"Error response from daemon: remove mydocker-flaskapi: volume is in use"**

```python
docker volume ls # this will list all volumes
docker volume rm mydocker-flaskapi #this will remove volume 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684870094914/c364c19a-a4fe-4a4c-913d-7d2165523350.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/)