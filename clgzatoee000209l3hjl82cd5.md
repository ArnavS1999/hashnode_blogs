---
title: "Understanding package manager and systemctl"
datePublished: Thu Apr 27 2023 15:47:40 GMT+0000 (Coordinated Universal Time)
cuid: clgzatoee000209l3hjl82cd5
slug: understanding-package-manager-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682610377832/15ddbdd1-65cb-4b61-aea1-368429c63150.png
tags: linux, developer, devops, linux-for-beginners, 90daysofdevops

---

### Package Manager

In simpler words, a package manager is a tool that allows users to install, remove, upgrade, configure and manage software packages on an operating system. These can be either Command Line tools or a complete Graphical User Interface application.

### What is a package?

In Linux, a package is a compressed archive file that contains software and all of its related files, such as libraries, configuration files, and documentation. Packages are a way of distributing software in a format that is easy to install, manage, and update on Linux systems.

Packages are usually created and managed by a package manager, which is a tool that handles the installation, upgrade, and removal of software packages on the system. Package managers also take care of dependencies, which are other software packages required by a particular package to function correctly.

### Different kinds of package managers

Package Managers differ based on the packaging system but the same packaging system may have more than one package manager.

For example, RPM has [Yum](https://fedoraproject.org/wiki/Yum?ref=itsfoss.com) and [DNF](https://fedoraproject.org/wiki/DNF?ref=itsfoss.com), package managers. For DEB, you have apt-get, [aptitude](https://wiki.debian.org/Aptitude?ref=itsfoss.com) command line-based package managers.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682586577864/c5426dff-5ced-4da2-9765-4678d91cbc1c.png align="center")

Common Package Managers in Linux include:

* dpkg (Debian Package Manager)
    
* APT (Advanced Package Tool)
    
* rpm (RedHat Package Manager)
    
* yum (Yellowdog Update Modified)
    
* dnf (Dandified Yum)
    

* flatpak
    
* pacman
    
* snap
    
* synaptic
    

### Task 1: Install docker and Jenkins in your system from your terminal using package managers.

### For Ubuntu - Install Docker 

1\. Open the terminal on Ubuntu.

2\. Remove any docker file that are running in the system, using the following command: **sudo apt-get remove docker docker-engine** [**docker.io**](http://docker.io)

3\. Check if the system is up-to-date using the following command: **sudo apt-get update**

4\. Install Docker using the following command: **sudo apt install** [**docker.io**](http://docker.io)

5\. Install all the dependency packages using the following command:  **sudo snap install docker**

6\. Before testing Docker, check the version installed using the following command: **docker --version**

### For Ubuntu: Install Jenkins

**Step 1: Install Java**

Jenkins requires the Java Runtime Environment (JRE).

1. Check if you already have java installed on your Ubuntu system: java --version

2\. Depending on which Java version you want to install, Java 8 or 11, run one of the following commands:

To install OpenJDK 8, run: sudo apt install openjdk-8-jdk -y To install OpenJDK 11, run: **sudo apt install openjdk-11-jdk -y**

Step 2: Add Jenkins Repository

It is recommended to install Jenkins using the project-maintained repository, rather than from the default Ubuntu repository. The reason for that is because the Jenkins version in the default Ubuntu repository might not be the latest available version, which means it could lack the latest features and bug fixes.

1\. Start by importing the GPG key. The GPG key verifies package integrity but there is no output. Run:

curl -fsSL [https://pkg.jenkins.io/debian-stable/jenkins.io.key](https://pkg.jenkins.io/debian-stable/jenkins.io.key) | sudo tee /usr/share/keyrings/jenkins-keyring.asc &gt; /dev/null

2\. Add the Jenkins software repository to the source list and provide the authentication key:

echo deb \[signed-by=/usr/share/keyrings/jenkins-keyring.asc\] [https://pkg.jenkins.io/debian-stable](https://pkg.jenkins.io/debian-stable) binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list &gt; /dev/null

Step 3: Install Jenkins

1\. Update the system repository

sudo apt update

2\. Install Jenkins by running:

sudo apt install jenkins -y

3\. To check if Jenkins is installed and running, run the following command:

sudo systemctl status jenkins A bright green entry labelled active (running) should appear in the output, indicating that the service is running.

### systemctl and systemd

systemd is a system and service manager for Linux operating systems. It provides a range of features and capabilities, such as process tracking and control, event logging, network management, and more. systemd is responsible for initializing the system and managing its processes, and it replaces the traditional SysVinit system initialization and service management scripts.

systemctl is a command-line tool that is used to control and manage systemd services and processes. It allows you to start, stop, enable, disable, and check the status of services, as well as monitor logs and system events. systemctl provides a simple and unified interface for managing services, and it is widely used on modern Linux systems.

### **Task 2: Brief on how to install these tools using package managers on Ubuntu and CentOS.**

**Package Manager on Ubuntu:**

To install Docker on Ubuntu you can use the following command:

```plaintext
sudo apt-get update
sudo apt-get install docker.io
```

To install Jenkins on Ubuntu you can use the following command:

```plaintext
sudo apt-get update
sudo apt-get install jenkins
```

**Package Manager on CentOS:**

CentOS uses the YUM (Yellowdog Updater, Modified) package manager. You can install it using the following command:

```plaintext
sudo yum update
sudo yum install yum
```

To install Docker on CentOS you can use the following command:

```plaintext
sudo yum install docker
```

To install Jenkins on CentOS you can use the following command:

Make sure that Java is installed on the CentOS. First, add the Jenkins repository to the system and then install Jenkins using the below commands:

```plaintext
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum install jenkins
```

### **Task 3: Check the status of the docker service in your system**

To check the status of the Docker we use this command:

```plaintext
sudo systemctl status docker
```

The output fill display shows docker status **Active.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682591047585/b37deb73-4d93-4292-811e-66d1134ac026.png align="center")

### **Task 4: Stop the service Jenkins and post before and after screenshots.**

To check the status of the Jenkins we use this command:

```plaintext
sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682592063608/5c39b741-fab9-4f59-9418-d1ebbc8f7b41.png align="center")

Now to stop the services of Jenkins we use this command:

```plaintext
sudo systemctl stop jenkins
sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682592400494/e0d124cf-3258-4afe-ad88-7eace1acc613.png align="center")

And, to start services of Jenkins again we use this command:

```plaintext
sudo systemctl start jenkins
sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682592560106/7fc7b25c-00a2-48e8-9e32-d167acfefbc9.png align="center")

### **Task 5: systemctl vs service**

Both `systemctl` and `service` are used to manage and control services on a Linux system, but they work in slightly different ways.

`systemctl` is a more modern and powerful tool used for controlling the systemd system and service manager, which is the default system and service manager in most modern Linux distributions. It can start, stop, restart, enable or disable services, and also provides more advanced functionality like viewing the status of services, checking the log files of services, managing dependencies, and more.

On the other hand, `service` is an older command that is used to manage services in init.d or System V (SysV) style, which was the default service manager in older Linux distributions. It is still present in modern systems for backward compatibility. It is a simple and easy-to-use tool that can start, stop, or restart services, but it does not offer as many features as `systemctl`.

In summary, if you are using a modern Linux distribution that uses systemd as its default service manager, it is recommended to use `systemctl` to manage your services. If you are using an older distribution or dealing with legacy systems, `service` might be the more appropriate tool to use.

Thank you for reading!

Happy Learning!!