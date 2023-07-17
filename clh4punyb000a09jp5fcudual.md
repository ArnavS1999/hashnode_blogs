---
title: "Advance Git & GitHub for DevOps Engineers"
datePublished: Mon May 01 2023 10:47:11 GMT+0000 (Coordinated Universal Time)
cuid: clh4punyb000a09jp5fcudual
slug: advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682937918755/5136888a-b4b5-40f7-9805-c65b98b91748.png
tags: linux, github, learning, 90daysofdevops, wemakedevs

---

### **Git Branching**

Git branching is a way for developers to create separate versions of their code so they can work on different things without affecting the main codebase. It helps them collaborate and experiment more easily, and keep their work organized.

### **Git Revert and Reset**

The Git Revert command creates a new commit that undoes a previous commit, essentially "rolling back" the changes. This allows developers to undo mistakes or unwanted changes without erasing any history.

On the other hand, the Git Reset command moves the current branch to a specific commit, removing any changes made after that point. This can be a more drastic way to undo changes, as it permanently erases any history after the chosen commit.

### **Git Rebase and Merge**

### What Is Git Merge?

Git Merge combines the changes made in one branch with another branch, creating a new commit that includes both sets of changes. This method creates a merge commit that links the two branches together.

### What Is Git Rebase?

Git Rebase, on the other hand, incorporates the changes from one branch into another by rewriting the project history. This means that the changes made in the branch being rebased are replayed on top of the other branch's history, resulting in a linear project history.

## Task

### Task 1--&gt;

Add a text file called version01.txt inside the Devops/Git/ with “This is first feature of our application” written inside. This should be in a branch coming from `master`, \[hint try `git checkout -b dev`\], switch to `dev` branch ( Make sure your commit message will reflect as "Added new feature").

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682927967243/c576cd95-f64a-47b8-9bef-812fb24a9b3f.png align="center")

\--&gt; version01.txt should reflect at the local repo first followed by the Remote repo for review.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682930083453/a904b7e8-6c40-4a6c-9fa6-862f8f0e83c4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682930162630/48a525f9-5bcc-4272-a648-7915c55f2966.png align="center")

Add a new commit in `dev` branch after adding the below-mentioned content in Devops/Git/version01.txt: While writing the file make sure you write these lines

* 1st line&gt;&gt; This is the bug fix in the development branch
    
* Commit this with the message “ Added feature2 in development branch”
    
* 2nd line&gt;&gt; This is gadbad code
    
* Commit this with the message “ Added feature3 in the development branch
    
* 3rd line&gt;&gt; This feature will gadbad everything from now.
    
* Commit with the message “ Added feature4 in the development branch
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682932934019/49731952-09d6-4401-aed4-4044486eff7f.png align="center")

Restore the file to a previous version where the content should be “This is the bug fix in the development branch”

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682933072231/60bdac70-2e65-4e4b-9b98-0718854dae6a.png align="center")

*If you ran the command "git reset ab05c7f" and there were no changes made to the file "version01.txt", it means that the contents of the file in the commit you reset to (i.e. "ab05c7f") are the same as the contents of the file in your current working directory.*

*In this case, you can use the "git checkout" command to restore the file to the state it was in at the time of the commit. To do this, run the following command:*

```plaintext
git checkout ab05c7f -- version01.txt
```

*This command will restore the file "version01.txt" to the state it was in at the commit "ab05c7f".*

*Please note that this will discard any changes you have made to the file since that commit.*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682933608929/5824ac76-e3b2-46f6-9060-aedad5eb3eb3.png align="center")

### Task 2--&gt;

### Demonstrate the concept of branches with 2 or more branches with a screenshot.

![Git Branches: List, Create, Switch to, Merge, Push, & Delete](https://www.nobledesktop.com/image/gitresources/git-branches-merge.png align="left")

Initially, we have a single branch called "master" that contains the main codebase for the project.

```plaintext
$ git init MyProject
$ cd MyProject
$ touch hello.txt
$ git add hello.txt
$ git commit -m "Initial commit"
```

Now, let's say we want to develop a new feature for the project without affecting the main codebase in the "master" branch. We can create a new branch for this feature called "dev" using the following command:

```plaintext
$ git checkout -b dev
```

This command creates a new branch called "dev" and switches to it. Now, any changes we make to the project will be made in this branch, and the "master" branch will remain unaffected.

```plaintext
$ touch feature.txt
$ git add feature.txt
$ git commit -m "Added feature file"
```

We can now switch back to the "master" branch using the following command:

```plaintext
$ git checkout master
```

Now, if we want to merge the changes we made in the "dev" branch into the "master" branch, we can use the following command:

```plaintext
$ git merge dev
```

This command will merge the changes we made in the "dev" branch into the "master" branch.

Alternatively, if we want to abandon the changes we made in the "dev" branch and switch back to the "master" branch without merging, we can use the following command:

```plaintext
$ git checkout master
$ git branch -d dev
```

This command deletes the "dev" branch and discards any changes made in that branch.

In summary, using branches in Git allows developers to work on separate features or fixes without interfering with the main codebase, and then merge those changes back into the main branch once they are complete. This helps to keep the codebase organized and makes it easier to collaborate with other developers on a project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682935422605/9d3e49da-3391-4d9b-95d4-f4c47889f673.png align="center")

### Add some changes to `dev` branch and merge that branch in `master`

Continued with Task 1 Terminal(taken same **main** and **dev** branch )

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682936694491/3e094b59-a3db-48a9-aea6-dfc039e42b4c.png align="center")

### As a practice try git rebase too, and see what difference you get.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682937376510/55e03945-cb85-4b6e-a14d-fad412f5e22f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682937319180/b0711a6b-fe38-4b28-a908-1bc128fc74e0.png align="center")

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [ArnavSingh](https://www.linkedin.com/in/arnav-singh-6897b7226/).