---
title: "Advanced Linux Shell Scripting for DevOps Engineers with User management."
datePublished: Tue Apr 25 2023 19:19:06 GMT+0000 (Coordinated Universal Time)
cuid: clgwnhvz9000809l3eb5o9e82
slug: advanced-linux-shell-scripting-for-devops-engineers-with-user-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682450288914/5ea8aea8-1412-4f13-abea-f31b1133c8b2.png
tags: linux, devops, linux-for-beginners, shell-script, 90daysofdevops

---

### **Task 1. Write a bash script** [**createDirectories.sh**](http://createDirectories.sh) **that when the script is executed with three given arguments (one is the directory name and second is the start number of directories and third is the end number of directories ) it creates a specified number of directories with a dynamic directory name.**

Here's how to use the script:

Type the following command - vim [`createDirectories.sh`](http://createDirectories.sh) and press Enter to create a new file called [`createDirectories.sh`](http://createDirectories.sh)and open it in Vim for editing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682413622384/67abce0f-041c-4f5e-8d8c-f1256df59955.png align="center")

1. In the Vim editor, press `i` to enter insert mode, which allows you to type and edit the contents of the file.
    
2. After entering press Esc button and :wq to save and quit from the Vim editor.
    
3. Make the script executable by running the following command: `chmod +x` [`createDirectories.sh`](http://createDirectories.sh).
    
4. Example 1:When the script is executed as `./`[`createDirectories.sh`](http://createDirectories.sh) `day 1 90`
    

then it creates 90 directories as `day1 day2 day3 .... day90 .`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682413794724/fe93f4ee-5fea-4557-b5c0-ebbd1232525e.png align="left")

### **Task 2. Create a Script to backup all your work done till now.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682447368558/40c5192e-346d-48f7-9dd4-35272a0cf2f1.png align="center")

The above script will help us create a compressed backup archive of a specified directory and save it in a specified backup directory.

Backups are crucial for DevOps because they provide a safety net in case of data loss, system failures, or other unexpected events that could result in downtime or data corruption. By creating regular backups of your system and data, you can quickly restore your infrastructure to a previous state, minimizing the impact of any issues that may arise.

### **Task 3.What are Cron and Crontab?**

Cron is a time-based job scheduler in Unix-like operating systems that allows users to schedule commands or scripts to run automatically at specified intervals or specific times. It is a powerful tool for automating repetitive tasks, such as backups, system maintenance, and running scripts.

The crontab file consists of lines that contain six fields separated by spaces or tabs. The fields represent, in order, the minute, hour, day of the month, month, day of the week, and the command to be executed. An asterisk (\*) can be used as a wildcard to indicate all possible values in a field.

Some Crontab Commands:

1. `crontab -e`: This command is used to edit the current user's crontab file. It opens the file in the default editor specified in the `VISUAL` or `EDITOR` environment variable.
    
2. `crontab -l`: This command lists the current user's cron jobs in the terminal.
    
3. `crontab -r`: This command removes the current user's crontab file, deleting all scheduled cron jobs.
    
4. `crontab -i`: This command prompts the user for confirmation before deleting the crontab file.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682448206056/3898d710-b4f8-4984-b86a-9c4203ebf04a.png align="center")

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682448848674/c6289142-2c4c-4180-be3e-423fe91f58f4.png align="center")

This crontab entry will run the script `/path/to/backup_script.sh` every day at 2am. The `>>` operator is used to append the output of the script to a log file located at `/path/to/backup.log`

### **Task 4. User Management System in Linux**

In Linux, user management is typically done using command-line tools such as useradd, usermod, and userdel. Here are some common tasks involved in user management in Linux:

1. Creating a new user account:To create a new user account, use the `useradd` command followed by the username you want to create.
    
2. Setting a password for a user: To set a password for a user, use the `passwd` command followed by the username.
    
3. Deleting a user account: To delete a user account, use the `userdel` command followed by the username.
    
4. Modifying user account settings: To modify user account settings, use the `usermod` command.
    

### **Task 5.Create 2 users and just display their Usernames**

Use the `useradd` command to create the users. For example, to create a user named "audi", do the same for "BMW" enter:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682449595671/584a1b8d-85ad-4340-ada7-31bb8a94b273.png align="center")

To check if the users are created or not, run the command: `cat /etc/passwd.` The new users will be displayed at last.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682449614950/32dc0d2e-a2f5-4b9b-b922-c0d5ebcbc02a.png align="center")

## **Thank you for reading! Happy Learning!!**