---
title: "Advance Git & GitHub for DevOps Engineers: Part-2"
datePublished: Sat May 06 2023 21:16:44 GMT+0000 (Coordinated Universal Time)
cuid: clhchjizw000c09jx64vk4848
slug: advance-git-github-for-devops-engineers-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683407667630/ba814532-09b0-4e5a-9ff5-662383643cfd.png
tags: linux, github, git, devops, 90daysofdevops

---

## Git Stash

Git stash is a useful feature in Git that allows you to save changes you've made to your code without committing them. It's particularly useful when you need to switch to another branch or work on a different feature, but you're not ready to commit your changes yet. With Git stash, you can "stash" your changes away, switch to another branch, work on something else, and then come back to your original changes and reapply them. This can help you keep your code organized and avoid losing important changes.

## Cherry-pick

Cherry-pick is a Git command that allows you to pick and apply specific changes from one branch to another. It's like taking a cherry from a tree - you're selecting only the specific commit or changes that you want, rather than merging the entire branch.

Cherry-pick is useful when you want to apply a single commit or a few selected commits from one branch to another. It can help you avoid merging unwanted changes and keep your codebase clean.

To use cherry-pick, you simply identify the specific commit(s) that you want to apply and then use the cherry-pick command to apply them to another branch. This can be a helpful tool for managing your Git workflow and ensuring that only the necessary changes are applied.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683401477034/fd2e4b02-bd6c-4520-a65f-f35e99c67712.png align="center")

## Resolving Conflicts

Conflicts can occur when you merge or rebase branches that have diverged, and you need to manually resolve the conflicts before git can proceed with the merge/rebase. git status command shows the files that have conflicts, git diff command shows the difference between the conflicting versions and git add command is used to add the resolved files.

# Task-01

* ***Create a new branch and make some changes to it.***
    
* ***Use git stash to save the changes without committing them.***
    
* ***Switch to a different branch, make some changes and commit them.***
    
* ***Use git stash pop to bring the changes back and apply them on top of the new commits.***
    
    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
    

<mark>Create a new branch and make some changes to it.</mark>

<mark>Use git stash to save the changes without committing them.</mark>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683402153087/fc49222a-9324-414e-8797-4cbd0608cb75.png align="center")

<mark>Switch to a different branch, make some changes and commit them.</mark>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683402483271/7243b7c0-12af-4136-9060-484adc932081.png align="center")

<mark>Use git stash pop to bring the changes back and apply them on top of the new commits.</mark>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683403236314/31ccf837-8b64-4645-b0cd-14118747903d.png align="center")

# Task-02

* ***In version01.txt of development branch add below lines after “This is the bug fix in development branch” that you added in Day10 and reverted to this commit.***
    
* ***Line2&gt;&gt; After bug fixing, this is the new feature with minor alteration”***
    
    ***Commit this with message “ Added feature2.1 in development branch”***
    
* ***Line3&gt;&gt; This is the advancement of previous feature***
    
    ***Commit this with message “ Added feature2.2 in development branch”***
    
* ***Line4&gt;&gt; Feature 2 is completed and ready for release***
    
    ***Commit this with message “ Feature2 completed”***
    
* ***All these commits messages should be reflected in Production branch too which will come out from Master branch (Hint: try rebase).***
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683404443100/700fceca-9125-4c18-b14a-f346354025e0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683406086361/10be331f-d337-46b4-ab94-3ee05594ee89.png align="center")

<mark>(Note- Here main - is named </mark> **<mark>dev</mark>** <mark>and dev - is named </mark> **<mark>main</mark>**<mark>)</mark>

To change the name of a branch use this command - **git branch -m old-name new-name**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683406677371/7f78a10e-86de-49a4-9f89-76bc3475bc2a.png align="left")

# Task-03

* ***In Production branch Cherry pick Commit “Added feature2.2 in development branch” and added below lines in it:***
    
* ***Line to be added after Line3&gt;&gt; This is the advancement of previous feature***
    
* ***Line4&gt;&gt;Added few more changes to make it more optimized.***
    
* ***Commit: Optimized the feature***
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683407353977/23f2007a-6260-4835-a4c3-e5e484d084e1.png align="center")

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/).