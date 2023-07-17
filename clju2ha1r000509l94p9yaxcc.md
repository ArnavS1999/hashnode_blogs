---
title: "Deploy Wordpress website on AWS"
datePublished: Sat Jul 08 2023 13:54:21 GMT+0000 (Coordinated Universal Time)
cuid: clju2ha1r000509l94p9yaxcc
slug: deploy-wordpress-website-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688824326026/d0a36e7f-91e9-419d-b9b9-f771da70ded3.png
tags: aws, wordpress, opensource, devops, wemakedevs

---

## Task-01

* **As WordPress requires a MySQL database to store its data, create an RDS as you did on Day 44**
    

**To configure this WordPress site, you will create the following resources in AWS:**

* **An Amazon EC2 instance to install and host the WordPress application.**
    
* **An Amazon RDS for MySQL database to store your WordPress data.**
    
* **Set up the server and post your new WordPress app.**
    

### **As WordPress requires a MySQL database to store its data, create an RDS as you did on Day 44**

Plz, refer to this Blog to create **RDS--&gt;** [**<mark>Day44-RDS_IN_AWS.</mark>**](https://arnavdevops.hashnode.dev/relational-database-service-in-aws)

* Set up the EC2 instance to host the WordPress application:
    
    * SSH into the EC2 instance using a terminal or SSH client.
        
    * Install Apache, PHP, and MySQL client:
        
    
    ```yaml
    sudo apt update
    sudo apt install apache2 php libapache2-mod-php php-mysql -y
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688747724000/affdbf81-cb1c-457a-8005-4329c0a091aa.png align="center")
    
    * Before configuring the Apache web server, you need to create a database user for the WordPress application and grant it appropriate permissions to access the WordPress database.
        
    * Connect to your Amazon RDS instance using a MySQL client. Replace `<RDS endpoint>`, `<master username>`, and `<master password>` with your RDS instance details:
        
        ```yaml
        mysql -h <RDS endpoint> -u <master username> -p
        ```
        
    * Enter the password for the master username when prompted.
        
    * Create a new database user for the WordPress application. Replace `<wordpress_username>` and `<wordpress_password>` with your desired username and password:
        
        ```yaml
        CREATE USER '<wordpress_username>' IDENTIFIED BY '<wordpress_password>';
        ```
        
    * Create the WordPress database if it doesn't exist. Replace `<wordpress_database>` with your desired database name:
        
        ```yaml
        CREATE DATABASE IF NOT EXISTS `<wordpress_database>`;
        ```
        
    * Grant privileges to the database user for the WordPress database:
        
        ```yaml
        GRANT ALL PRIVILEGES ON <wordpress_database>.* TO <wordpress_username>;
        ```
        
    * Flush the privileges to update the changes:
        
        ```yaml
        FLUSH PRIVILEGES;
        ```
        
    * Exit the MySQL prompt:
        
        ```yaml
        exit;
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688799613730/03b34710-5697-4d1d-baa1-0b32f74ffa6e.png align="center")
    
    * Configure Apache to serve the WordPress files:
        
    
    ```yaml
    sudo a2enmod rewrite
    sudo systemctl restart apache2
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688747793316/88cad296-ba47-4e3a-9d3b-af5d36bac846.png align="center")
    
    * Download and extract the latest WordPress files:
        
    
    ```yaml
    wget https://wordpress.org/latest.tar.gz
    tar -xvzf latest.tar.gz
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688747851959/8a73ed1d-fc00-4d51-8145-5f8638d462eb.png align="center")
    
    * need to go to the WordPress directory
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688803357030/7f3d97b4-b4e4-43c5-9a5c-0e61c0126ea8.png align="center")
    
    * Now create a copy of the config file and edit the wp-config.php file
        
    * Update the WordPress configuration file (`wp-config.php`) with the database connection details.
        
    
    ```yaml
    sudo cp wp-config-sample.php wp-config.php
    sudo vim wp-config.php
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688803430612/5ebf0543-0c89-4a42-84ad-7efd207465d2.png align="center")
    
    * Copy the extracted WordPress files to the Apache web server document root:
        

```yaml
sudo cp -r wordpress/* /var/www/html/
```

* Restart the Apache web server:
    

```yaml
sudo systemctl restart apache2
```

* Access your new WordPress site:
    
    * Open a web browser and enter the public IP address or DNS name of your EC2 instance. You should see the WordPress installation page.
        
    * Follow the on-screen instructions to complete the WordPress setup.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688822400293/552f354e-8e9d-46ea-9e4b-327baa7c42d9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688822546988/1fbf7e01-ef2c-4ae3-85a1-07b9add56d11.png align="center")

---

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**<mark>ArnavSingh</mark>**](https://www.linkedin.com/in/arnav-singh-6897b7226/)**<mark>.</mark>**