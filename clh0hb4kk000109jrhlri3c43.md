---
title: "Basic Git & GitHub for DevOps Engineers."
datePublished: Fri Apr 28 2023 11:36:58 GMT+0000 (Coordinated Universal Time)
cuid: clh0hb4kk000109jrhlri3c43
slug: basic-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682681726697/7d8d9358-2e3e-4a13-aa8e-297bd2e9fa09.png
tags: linux, github, git, devops, wemakedevs

---

## **What is a VCS (Version Control System)?**

A version control system (VCS) or version control software automates the process of version control. It tracks changes to a file or set of files over time so that you do not have to manage file versions manually or with custom automation scripts. A version control system keeps a complete history of your code and other files, allowing you to return to a previous version if needed.

### Centralized Version Control Systems

Here, there’s a central repo shared with all the developers, and everyone gets their working copy. Whenever you commit, the changes get reflected directly in the repo. Unlike distributed systems, developers directly commit to the remote. Which means they may affect files knowingly or unknowingly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682670975822/382b3c33-8f84-499e-aebd-bb7621389342.png align="center")

### Distributed Version Control Systems

In distributed systems, there is a local copy of the repo for every developer on their computers. They can make whatever changes they want and commit without affecting the remote repo. They first commit to their local repo and then push the changes to the remote repo. This is the type used majorly today.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682671142387/7563f953-fb6a-447e-b5f8-02362345382c.png align="center")

In the Centralized VCS, every commit was directly happening to the, say, remote repo. But in distributed VCS, it first happens in the developer's local repo, and then they send those changes to the remote. *Remote repo is a git repo on a server hosted by any such providers like GitHub, Bitbucket, etc.*

## **Git and GitHub**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682671964523/9ed960b3-226f-4ddc-89aa-65de47a408b9.png align="center")

### Git

Git is a popular and widely used distributed version control system designed to manage and track changes to software code and other digital assets. Developed by Linus Torvalds in 2005, Git is a fast, efficient, and flexible tool that can handle projects of any size. It allows developers to create, clone, and manage repositories and track changes over time using commits. One of Git's key features is its distributed nature, which allows users to work offline and merge changes easily. Git also offers powerful branching and merging capabilities, making it easy to experiment with new ideas and collaborate on different parts of a project. Git is an essential tool for modern software development, used by individuals and corporations of all sizes.

### GitHub

GitHub is the world's largest platform for open-source software development, offering web-based tools and services for hosting and collaborating on software projects using Git. It allows developers to store and share code repositories, collaborate with others, and contribute to open-source projects. With features such as issue tracking, pull requests, and project management tools, GitHub is a powerful and flexible tool for modern software development. Its extensive community of developers and integrations with other tools and services make it an essential platform for software development.

## **Tasks**

### Task 1: Install Git on your computer

To install Git on your computer, simply download the appropriate installer from the Git website and follow the prompts to complete the installation. Once installed, you can use Git to manage and track changes to your software code and other digital assets. To verify that Git has been installed correctly, open the command line or terminal and type 'git --version'. Installing Git is an easy and essential step for modern software development.

### Task 2: Create a free account on GitHub

To create a free account on GitHub, simply visit the GitHub website and click on the 'Sign up' button in the top right corner of the homepage. Enter your desired username, email address, and password, then choose your plan and complete the verification process.

## **Exercises**

### Exercise 1: Create a new repository on GitHub and clone it to your local machine.

To create a new repository on GitHub and clone it to your local machine, follow these steps:

1. Sign in to your GitHub account and navigate to your dashboard.
    
2. Click on the "+" sign in the top right corner and select "New repository" from the dropdown menu.
    
3. Enter a name for your repository and a brief description (optional).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682672500522/df8e13fb-6ae0-4a68-80d2-f2b9ed313135.png align="center")
    
4. Choose whether you want your repository to be public or private.
    
5. Select the option to add a README file to your repository.
    
6. Click on the "Create repository" button to create your new repository.
    
7. Once your repository is created, copy the HTTPS URL for your repository.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682672689551/e375fb54-422a-4321-9668-7f44fa94e5b0.png align="center")
    
8. Open your terminal or command prompt on your local machine and navigate to the directory where you want to clone your repository.
    
9. Type "git clone" followed by the HTTPS URL for your repository, then press Enter.
    
10. ```plaintext
    git clone https://github.com/ArnavS1999/basicgit.git
    ```
    
11. Once the cloning process is complete, you will have a local copy of your repository on your machine that you can work on and commit changes to.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682673262529/5293ead4-e874-4df1-885a-47955f362ce0.png align="left")

### Exercise 2: Make some changes to a file in the repository and commit them to the repository using Git.

1. Let's create a .txt file, add some content or make the desired changes to the file and save it.
    
2. Type "git add" to stage your changes for commit. This command stages all changes in the repository.
    
3. Type "git commit -m 'commit message'" to commit your changes to the repository. Be sure to replace 'commit message' with a short, descriptive message that summarizes your changes.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682675472783/44878eb8-ed51-421a-b664-3e1a20a21535.png align="center")

1. After entering "git commit -m 'commit message" the terminal displays a message "Author identity unknown".
    
2. "Author identity unknown". means that there is no author to make or save changes to VCS.
    
3. To solve this issue run these commands:
    
    git config --global [user.email](http://user.email) "[you@example.com](mailto:you@example.com)"
    
    git config --global [user.name](http://user.name) "Your Name"
    
4. After adding your Username and your mail, run the "git commit -m 'commit message'" again.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682676276275/20e84a0f-04c5-45be-a095-8fce18d3a318.png align="center")

1. The file that was created has been committed successfully to the local repository!
    

### **Exercise 3: Push the changes back to the repository on GitHub**

1. To push the changes to the GitHub repository, we use the command:
    

```plaintext
git push -u -f origin
```

1. After entering the command it will ask for GitHub Username and Password.
    
2. Enter the Username but for the password generate your special [access token](https://docs.github.com/en/enterprise-server@3.4/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) and paste it and press Enter.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682679673721/62bbf425-cd60-4b0f-960c-d390abb8c558.png align="center")

1. After Enter Files will be pushed from the local repo to the remote repo.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682679797660/51d0fa6d-d17a-4eeb-92dc-95836f29b1fb.png align="center")

Thank you for reading!

Happy Learning!!