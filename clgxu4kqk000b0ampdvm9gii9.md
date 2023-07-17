---
title: "File Permissions and Access Control Lists"
datePublished: Wed Apr 26 2023 15:12:29 GMT+0000 (Coordinated Universal Time)
cuid: clgxu4kqk000b0ampdvm9gii9
slug: file-permissions-and-access-control-lists
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682522128298/fd5bf85f-43b9-4d82-8ad4-a8dd12e3c857.png
tags: linux, developer, devops, linux-for-beginners, 90daysofdevops

---

[**Linux**](https://www.linux.org/) is a multi-user operating system, so more than one person can work on the same computer at the same time. What’s great, the system can be accessed locally or remotely. That’s why developers often use this OS for group projects.

In such a large environment, we need to set file permissions and ownership, so that only specific users can access our data. This way, we can protect sensitive information and prevent unwanted changes from happening.

## File Permissions

Note: I might use the term file here but it applies to directories as well.

Every file and directory in Linux has three kinds of owners:

### User

The user is the owner of the file. When you create a file, you become the owner of the file. The ownership can be changed as well, but we’ll see that later.

### Group

Every user is part of a certain group(s). A group consists of several users and this is one way to manage users in a multi-user environment.

Even if you are the only user of the system, you’ll still be part of many groups. Distributions like Ubuntu also create a group with a name same to the user’s name.

### Other

‘Other’ can be considered as a super group with all the users on the system. Anyone with access to the system belongs to this group.

In other words, ‘User’ is a single user, Group is a collection of users and Other consists of all the users on the system.

## File permissions in Linux

Every file and directory in Linux has the following three permissions for all three kinds of owners:

**Permissions for files**

* Read – Can view or copy file contents
    
* Write – Can modify file content
    
* Execute – Can run the file (if it's executable)
    

**Permissions for directories**

* Read – Can list all files and copy the files from a directory
    
* Write – Can add or delete files into a directory (needs to execute permission as well)
    
* Execute – Can enter the directory
    

Example: One can check and understand these permissions by **ls -ltr** command and get a better understanding of the permissions of files and directories in their system.

![Example](https://cdn.hashnode.com/res/hashnode/image/upload/v1682516642007/1faffae6-8424-453b-a824-8f8348a727d4.png align="center")

Let me explain this output with a picture:

![Permissions - 245CT](https://github.coventry.ac.uk/pages/CUEH/245CT/4_Privesc/images/perms1.png align="left")

Let me further explain the entire output in detail:

* **File type**: Denotes the type of file. d means directory, – means regular file
    
* **Permissions**: This field shows the permission set on a file. I’ll explain it in detail in the next section.
    
* **Hard link count**: Shows if the file has [hard links](https://linuxhandbook.com/hard-link/). Default count is one.
    
* **User**: The user who owns the files.
    
* **Group**: The group that has access to this file. Only one group can be the owner of a file at a time.
    
* **File size**: Size of the file in bytes.
    
* **Modification time**: The date and time the file was last modified.
    
* **Filename**: Obviously, the name of the file or directory.
    

In the above command, you see the file permission like this in the nine digit **format**:

```plaintext
rwxrw-r--
```

Each letter denotes a particular permission:

* r : Read permission
    
* w : Write permission
    
* x : Execute permission
    
* – : No permission set
    

This picture will explain things better:

![](https://linuxhandbook.com/content/images/2020/06/file-permission-explanation-2-1.png align="left")

## Change file permissions in Linux

You can use [chmod](https://linux.die.net/man/1/chmod?ref=linuxhandbook.com) command for changing the permissions on a file in Linux.

There are two ways to use the chmod command:

* Absolute mode
    
* Symbolic mode
    

### **Using chmod in absolute mode**

In this system, each file permission is represented by a number.

* r (read) = 4
    
* w (write) = 2
    
* x (execute) = 1
    
* – (no permission) = 0
    

With these numeric values, you can combine them and thus one number can be used to represent the entire permission set.

| Number | PermissionNo permissions |  |
| --- | --- | --- |
| 0 | — | No permissions |
| 1 | –x | Execute only |
| 2 | \-w- | Write only |
| 3 (i.e. 2+1) | \-wx | Write and execute |
| 4 | r– | Read only |
| 5 (i.e. 4+1) | r-x | Read and execute |
| 6 (i.e. 4+2) | rw- | Read and write |
| 7 (i.e. 4+2+1) | rwx | Read, write, and execute |

Suppose you want to change the file permission on **createDirectories.sh(shell script file)** so that everyone can read and write but no one can execute it? In that case, you can [use the chmod command](https://linuxhandbook.com/chmod-command/) like this:

```plaintext
chmod 666 createDirectories.sh
```

f you list agatha.txt now, you’ll see that the permission has been changed.

```plaintext
-rw-rw-rw- 1 arnav arnav 431 Apr 25 14:05 createDirectories.sh
```

### **Using chmod in symbolic mode**

In symbolic mode, owners are denoted with the following symbols:

* u = user owner
    
* g = group owner
    
* o = other
    
* a = all (user + group + other)
    

The symbolic mode uses mathematical operators to perform the permission changes:

* \+ for adding permissions
    
* – for removing permissions
    
* \= for overriding existing permissions with new value
    

Now that you know let’s see how to use chmod command in symbolic mode.

In our previous example, if you want to add execute permission for group owner, you can use chmod command like this:

```plaintext
chmod g+x createDirectories.sh
```

## Change file ownership in Linux

To change the ownership of a file, you can use the [**command chown**](https://linux.die.net/man/1/chown?ref=linuxhandbook.com)**.**

You can change the user owner of a file in the following manner:

```plaintext
chown <new_user_name> <filename>
```

## chgrp (Change Group Ownership) Command in Linux

The basic syntax of the chgrp command is shown below:

```plaintext
chgrp groupname file-name/directory-name
```

# Access Control List (ACL)

The standard Linux permissions are suitable for most situations but they have their limitations. The standard permissions limit access to *file owners, group owners* and *others.* But, what if we want to grant specific permission to another named user, other than the user-owner or another named group other than the group-owner. Access Control List (ACL) allows us to set these fine-grained permissions.

## How to view ACL – getfacl

The syntax would be:

```plaintext
getfacl <filename>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682519768736/a04ec6d9-51cd-4b91-916a-3b9f27c50c39.png align="center")

## How to Set ACL permissions – setfacl

The **setfacl** command is used to add, modify or delete standard ACL permissions on files and directories.

#### Add or modify a user or named user ACL

```plaintext
$setfacl -m u:name:permissions file
```

Thank you for reading!

Happy Learning!