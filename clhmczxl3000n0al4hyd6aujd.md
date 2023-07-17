---
title: "Linux and GitHub-Cheat Sheet"
datePublished: Sat May 13 2023 19:07:13 GMT+0000 (Coordinated Universal Time)
cuid: clhmczxl3000n0al4hyd6aujd
slug: linux-and-github-cheat-sheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684004644109/f7820734-1054-4640-b668-dfd6bed3d45d.jpeg
tags: linux, github, programming, devops, 90daysofdevops

---

## **Linux Commands----------------------**

1. `ls`: Lists files and directories in the current location.
    
    * Example: `ls -l` (lists files and directories in long format)
        
2. `cd`: Changes the current directory.
    
    * Example: `cd /path/to/directory` (changes to the specified directory)
        
3. `pwd`: Prints the current working directory.
    
    * Example: `pwd` (displays the current working directory)
        
4. `mkdir`: Creates a new directory.
    
    * Example: `mkdir new_directory` (creates a directory named "new\_directory")
        
5. `rm`: Removes files and directories.
    
    * Example: `rm file.txt` (removes the file.txt file)
        
6. `cp`: Copies files and directories.
    
    * Example: `cp file.txt new_location/` (copies file.txt to new\_location/)
        
7. `mv`: Moves or renames files and directories.
    
    * Example: `mv file.txt new_name.txt` (renames file.txt to new\_name.txt)
        
8. `cat`: Concatenates and displays file content.
    
    * Example: `cat file.txt` (displays the content of file.txt)
        
9. `grep`: Searches for a specific pattern in files.
    
    * Example: `grep "hello" file.txt` (searches for "hello" in file.txt)
        
10. `chmod`: Changes permissions of files and directories.
    
    * Example: `chmod +x` [`script.sh`](http://script.sh) (gives execute permission to [script.sh](http://script.sh))
        
11. `sudo`: Executes a command with superuser/root privileges.
    
    * Example: `sudo apt-get update` (updates packages with root privileges)
        
12. `top`: Displays system resource usage and running processes.
    
    * Example: `top` (displays system resource usage)
        
13. `wget`: Downloads files from the web.
    
    * Example: `wget` [`https://example.com/file.txt`](https://example.com/file.txt) (downloads file.txt from the given URL)
        
14. `find`: Searches for files and directories.
    
    * Example: `find . -name "*.txt"` (finds all .txt files in the current directory and subdirectories)
        
15. `head`: Displays the beginning of a file.
    
    * Example: `head -n 10 file.txt` (displays the first 10 lines of file.txt)
        
16. `tail`: Displays the end of a file.
    
    * Example: `tail -n 5 file.txt` (displays the last 5 lines of file.txt)
        
17. `tar`: Archives and extracts files.
    
    * Example: `tar -czvf archive.tar.gz files/` (creates a compressed tar archive of files/)
        
18. `ssh`: Connects to a remote machine using SSH protocol.
    
    * Example: `ssh user@hostname` (establishes an SSH connection to the specified hostname)
        
19. `scp`: Copies files between local and remote machines over SSH.
    
    * Example: `scp file.txt user@remote:/path/to/destination` (copies file.txt to the remote machine)
        
20. `df`: Displays disk space usage.
    
    * Example: `df -h` (displays disk space usage in human-readable format)
        
21. `du`: Shows disk usage of files and directories.
    
    * Example: `du -sh directory/` (displays the total disk usage of the directory)
        
22. `man`: Displays the manual pages for a command.
    
    * Example: `man ls` (displays the manual page for the "ls" command)
        
23. `chown`: Changes file ownership.
    
    * Example: `chown user:group file.txt` (changes the owner and group.
        

## **Git and GitHub Commands---------------**

1. `git init`: Initializes a new Git repository.
    
    * Example: `git init` (creates a new Git repository in the current directory)
        
2. `git clone`: Clones a remote repository to your local machine.
    
    * Example: `git clone` [`https://github.com/arnavs1999/repo.git`](https://github.com/user/repo.git) (clones the repository to your local machine)
        
3. `git add`: Adds files or changes to the staging area.
    
    * Example: `git add file.txt` (adds file.txt to the staging area)
        
4. `git commit`: Commits the changes in the staging area.
    
    * Example: `git commit -m "Added new feature"` (commits the changes with a commit message)
        
5. `git status`: Shows the status of your working directory.
    
    * Example: `git status` (displays the status of the repository)
        
6. `git push`: Pushes local changes to a remote repository.
    
    * Example: `git push origin master` (pushes changes to the master branch of the remote repository)
        
7. `git pull`: Fetches and merges change from a remote repository.
    
    * Example: `git pull origin master` (fetches and merges changes from the remote master branch)
        
8. `git branch`: Lists, creates, or deletes branches.
    
    * Example: `git branch` (lists all branches in the repository)
        
9. `git checkout`: Switches between branches or restores file versions.
    
    * Example: `git checkout new-feature` (switches to the "new-feature" branch)
        
10. `git merge`: Merges changes from one branch into another.
    
    * Example: `git merge feature-branch` (merges the changes from "feature-branch" into the current branch)
        
11. `git log`: Shows the commit history.
    
    * Example: `git log` (displays the commit history of the repository)
        
12. `git diff`: Shows the differences between commits, branches, etc.
    
    * Example: `git diff HEAD~1 HEAD` (displays the differences between the previous and current commit)
        
13. `git remote`: Manages remote repositories.
    
    * Example: `git remote add origin` [`https://github.com/user/repo.git`](https://github.com/user/repo.git) (adds a remote repository)
        
14. `git fetch`: Retrieves the latest changes from a remote repository.
    
    * Example: `git fetch origin` (fetches the latest changes from the remote repository)
        
15. `git revert`: Reverts a commit by creating a new commit with the opposite changes.
    
16. `git config`: Sets or retrieves Git configuration options.
    
    * Example: `git config --global` [`user.name`](http://user.name) `"John Doe"` (sets the global username to "John Doe")
        
17. `git log`: Shows the commit history.
    
    * Example: `git log --oneline` (displays the commit history in a concise format)
        
18. `git stash`: Stashes changes in a temporary area.
    
    * Example: `git stash save "Work in progress"` (saves the current changes in a stash)
        
19. `git reset`: Resets the current branch to a specific commit.
    
    * Example: `git reset HEAD~1` (resets the branch to the previous commit)
        
20. `git rebase`: Applies changes from one branch to another.
    
    * Example: `git rebase main` (applies the changes from the current branch to the "main" branch)
        
21. `git tag`: Manages tags (releases, versions, etc.).
    
    * Example: `git tag v1.0.0` (creates a tag for version 1.0.0)
        
22. `git cherry-pick`: Applies a specific commit to the current branch.
    
    * Example: `git cherry-pick abc123` (applies the commit with hash "abc123" to the current branch)
        
23. `git remote`: Manages remote repositories.
    
    * Example: `git remote -v` (displays the remote repositories and their URLs)
        
24. `git show`: Displays information about a specific commit.
    
    * Example: `git show abc123` (displays details about the commit with hash "abc123")
        
25. `git revert`: Reverts a commit by creating a new commit with the opposite changes.
    
    * Example: `git revert abc123` (creates a new commit that undoes the changes made in commit "abc123")
        
26. `git bisect`: Helps find the commit that introduced a bug using binary search.
    
    * Example: `git bisect start` followed by `git bisect bad` and `git bisect good` (starts the bisect process)
        
27. `git reflog`: Shows a log of all reference changes in the repository.
    
    * Example: `git reflog` (displays a log of all reference changes)
        
28. `git blame`: Shows who changed which lines in a file.
    
    * Example: `git blame file.txt` (displays line-by-line authorship information for file.txt)
        
29. `git archive`: Creates a tar or zip archive of a repository.
    
    * Example: `git archive --format=zip --output=repo.zip master` (creates a zip archive of the repository's master branch)
        
30. `git submodule`: Manages Git submodules within a repository.
    
    * Example: `git submodule add` [`https://github.com/user/repo.git`](https://github.com/user/repo.git) (adds a submodule to the repository)
        
31. `git clean`: Removes untracked files and directories from the working directory.
    
    * Example: `git clean -f` (removes untracked files forcefully)
        
32. `git show-branch`: Shows the branch structure and their commits.
    
    * Example: `git show-branch --all` (displays the branch structure and commits)
        

## **GitHub Commands--------------------**

1. `git pull-request`: Creates a pull request on GitHub.
    
2. `git fork`: Creates a personal copy of a repository on GitHub.
    
3. `git remote add`: Adds a remote repository.
    
4. `hub clone`: Clones a repository from GitHub.
    
5. `hub create`: Creates a new repository on GitHub.
    
6. `hub fork`: Creates a fork of a repository on GitHub.
    
7. `hub browse`: Opens a GitHub repository or commits in a browser.
    
8. `hub compare`: Opens a GitHub compare page in a browser.
    
9. `hub release`: Creates a GitHub release.
    
10. `hub issue`: Manages GitHub issues.
    
11. `hub pull-request`: Manages GitHub pull requests.
    

## **\-----------------------------------**

Thank you for reading. I hope you were able to understand and learn something new from my blog.

Happy Learning!

Please follow me on Hashnode and do connect with me on LinkedIn [**ArnavSingh**](https://www.linkedin.com/in/arnav-singh-6897b7226/).