---
title: "Deep Dive in Git & GitHub for DevOps Engineers."
datePublished: Sat Apr 29 2023 20:05:43 GMT+0000 (Coordinated Universal Time)
cuid: clh2ex8y9001c09l9htki6rpd
slug: deep-dive-in-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682798669983/1afd9b07-7967-47b5-ae04-2e6ab5a03513.png
tags: github, git, devops, 90daysofdevops, wemakedevs

---

### What is Git and why is it important?

Git is a free and open-source distributed version control system used for tracking changes in source code during software development. It allows multiple developers to work on the same project simultaneously, making collaboration and code sharing easier and more efficient. Git's distributed nature means that each developer has a local copy of the entire project, making it resilient to server failures and other issues.

The importance of Git lies in its ability to simplify the development process and increase productivity. With Git, developers can easily collaborate, track changes, and revert to previous versions of code, all while maintaining a clear and organized codebase. This makes it easier to identify and fix issues, as well as merge changes from multiple developers. Additionally, Git's popularity and widespread use means that it has a large community of users and resources available, making it easier for developers to learn and troubleshoot issues.

### What is the difference Between Main Branch and Master Branch?

The terms "Main branch" and "Master branch" refer to the primary branch in a Git repository, where the main development of a project occurs. The term "Master" has connotations of slavery and oppression, which can be problematic for some people. As a result, some organizations have decided to use the term "Main" instead, which is more neutral.

### Can you explain the difference between Git and GitHub?

Git is a powerful version control system that enables developers to track changes to their code over time and collaborate with others. Meanwhile, GitHub is a popular web-based platform that provides a user-friendly graphical interface for Git, allowing developers to host their repositories online and access additional features like issue tracking and pull requests. While Git can be used independently of GitHub, the latter offers a variety of tools and social features that help streamline the development process and foster collaboration within the developer community.

### How do you create a new repository on GitHub?

1. Log in to your GitHub Account.
    
2. Click on "+" in the top-right corner and select New Repository.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682793678541/abd76505-6a9a-485a-a966-bca52f9480dc.png align="center")

### What is the difference between local & remote repositories? How to connect local to remote?

  
The main difference between a local and a remote repository is their location and accessibility. A local repository is stored on your local computer, while a remote repository is stored on a remote server, such as GitHub.

To connect a local repository to a remote one, you can follow these steps:

1. Create a new repository on GitHub.
    
2. Copy the repository's URL.
    
3. Open your local repository in a Git terminal or command prompt.
    
4. Type the following command: `git remote add origin <repository URL>`. This tells Git to connect the local repository to the remote one.
    
5. Type the command `git push -u origin main` to push the changes from your local repository to the remote one. This sets the default branch on the remote repository to "main".
    

With these steps, your local repository is now connected to the remote repository, and you can push and pull changes between the two as needed.

## Tasks

### Task-1:Set your user name and email address, which will be associated with your commits.

To set your user name and email address in Git, this command is used:

```plaintext
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
```

### Task-2:Create a repository named "Devops" on GitHub.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682794945607/9a3a1982-214f-4bcc-acc0-fe681f1022bc.png align="center")

### Connect your local repository to the repository on GitHub.

To connect your local repository to the remote repository on GitHub, you first need to initialize a new Git repository on your local machine by running the command **'git init'**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682796499642/5088cafb-6e82-4ad8-88b9-73064b70ad23.png align="center")

Add some files to the local repo. With the command "git add" it will stage the file.

Finally, to commit our file we will use **git commit -m "message"** command**.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682797394740/0df3866d-1df6-408b-b19c-29367a33abbd.png align="center")

Type the command "**git push -u -f origin**" to push the contents of your local repository to the remote repository on GitHub.

Enter your GitHub username and password when prompted to authenticate your account.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682798532165/e9336045-4dc8-41dd-83c5-5ac065b2030b.png align="center")

After following these steps, your local repository is now connected to the remote repository on GitHub. You can now push and pull changes between the two repositories as needed.

Thank you for reading!

Happy Learning!!