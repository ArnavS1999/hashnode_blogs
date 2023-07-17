---
title: "Basic Linux Shell Scripting for DevOps Engineers."
datePublished: Sat Apr 22 2023 19:20:28 GMT+0000 (Coordinated Universal Time)
cuid: clgsd83el000109mi0wb721xy
slug: basic-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682191115683/6307fd05-2f41-48f1-9fd1-c057b6a3cd6c.png
tags: linux, devops, linux-for-beginners, shell-script, 90daysofdevops

---

## What is Kernel?

The Kernel is a core component of an operating system and serves as the main interface between the computer's physical hardware and the processes running on it. The kernel enables multiple applications to share hardware resources by providing access to the CPU, memory, disk I/O, and networking.

## What is Shell?

The shell is a program that takes commands from the keyboard and gives them to the operating system to perform. In the old days, it was the only user interface available on a Unix-like system such as Linux, nowadays, we have a graphical user interface(GUIs)in addition to a command line interface(CLIs)such as a shell.

On most Linux systems a program called **bash**(which stands for Bourne Again SHell, an enhanced version of the original Unix shell program, **sh**, written by Steve Bourne)acts as the shell program. Besides bash, there are other shell programs for Linux systems, These include **ksh, tcsh** and **zsh**.

***With the thousands of commands available to the command line user, how can we remember them all? The answer is, we don't. The real power of the computer is its ability to do the work for us. To get it to do that, we use the power of the shell to automate things. We write shell scripts.***

## What are Shell Scripts?

In the simplest terms, a shell script is a file containing a series of commands. The shell reads this file and carries out the commands as though they have been entered directly on the command line. The shell is somewhat unique, in that it is both a powerful command line interface to the system and a scripting language interpreter. As we will see, most of the things that can be done on the command line can be done in scripts, and most of the things that can be done in scripts can be done on the command line. We have already covered many shell features, but we have focused on those features most often used directly on the command line. The shell also provides a set of features usually (but not always) used when writing programs.

***Scripts unlock the power of our Linux machine.***

## What is #!/bin/bash? Can we write #!/bin/sh as well?

`#!/bin/bash` is called a shebang or hashbang. It is a special sequence of characters that is placed at the beginning of a script file in Unix-like operating systems. The shebang tells the system which interpreter to use to execute the commands in the script. In this case, it specifies that the script should be interpreted by the Bash shell, which is a popular Unix shell and command language.

Yes, you can write `#!/bin/sh` as well. This shebang specifies that the script should be interpreted by the system's default Unix shell, which could be any shell that complies with the POSIX standard(The Portable Operating System Interface is a family of standards specified by the IEEE Computer Society for maintaining compatibility between operating systems.). It's worth noting that `#!/bin/sh` is not guaranteed to invoke the same shell on all systems. Depending on the system configuration, `sh` could be a symlink to a different shell binary (e.g. `dash` on some Linux distributions), or the system could have a completely different default shell.

## Write a Shell Script which prints `I will complete #90DaysOofDevOps challenge`

1. Open a terminal window.
    
2. Make a directory - mkdir script.
    
3. Type the following command - vim shellscript.sh and press Enter to create a new file called shellscript.sh and open it in Vim for editing.
    
4. In the Vim editor, press `i` to enter insert mode, which allows you to type and edit the contents of the file.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682180837870/ba78d4eb-2cb3-4fc9-a478-83d5d3c29c41.png align="center")

1. After entering press Esc button and :wq to save and quit from Vim editor.
    
2. Make the script executable by running the command `chmod +x shellscript.sh.`
    
3. Execute the script by running the command `./shellscript.sh`.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682180765095/23353fae-74f0-4cfe-be95-b0ac84349ea4.png align="center")

***The script should output the message "I will complete #90DaysOfDevOps challenge" to the terminal***.

## Write a Shell Script to take user input, input from arguments and print the variables.

1. Open a terminal window.
    
2. Type the following command - vim [input-from-arguements.sh](http://input-from-arguements.sh) and press Enter to create a new file called [input-from-arguements.sh](http://input-from-arguements.sh) and open it in Vim for editing.
    
3. In the Vim editor, press `i` to enter insert mode, which allows you to type and edit the contents of the file.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682187858251/c7af31e3-7fba-4eaf-837e-a864e9c640df.png align="center")

1. After entering press Esc button and :wq to save and quit from Vim editor.
    
2. Make the script executable by running the command `chmod +x` [input-from-arguements.sh](http://input-from-arguements.sh)`.`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682187801783/31ce3ba4-f235-4949-a4db-8711d86f3f6a.png align="center")

1. Execute the script by running the command **./**[**input-from-arguements.sh**](http://input-from-arguements.sh)`.`
    
    ***The script will read the age from the argument instead of prompting the user.***
    

## Write an Example of If else in Shell Scripting by comparing 2 numbers.

1. Open a terminal window.
    
2. Type the following command - vim [ifelse.sh](http://input-from-arguements.sh) and press Enter to create a new file called [ifelse.sh](http://input-from-arguements.sh) and open it in Vim for editing.
    
3. In the Vim editor, press `i` to enter insert mode, which allows you to type and edit the contents of the file.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682188715428/dc43dff6-a945-4096-b12d-eafe744caa48.png align="center")

1. After entering press Esc button and :wq to save and quit from Vim editor.
    
2. Make the script executable by running the command `chmod +x` ifelse.sh.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682188678214/f3a3d106-abf6-42ba-930c-8d0c288e999e.png align="center")

1. Execute the script by running the command **./**[**ifelse.sh**](http://input-from-arguements.sh)`.`
    

In this script, we are comparing two numbers: `number1` and `number2`. We are using the if-else statement to check if they are equal, or if one is greater than the other. If `number1` is equal to `number2`, then we print the message "Both numbers are equal". If `number1` is greater than `number2`, then we print the message "Number 1 is greater than Number 2". Otherwise, we print the message "Number 2 is greater than Number 1".You can modify the values of `number1` and `number2` to test the script with different numbers.

**There are some operators, keywords and commands that we should be familiar with if we use Bash shell scripting. These operators, keywords and commands were used in the above shell scripting example.**

`---> -eq` and `-gt` are comparison operators in Bash shell scripting that are used to compare two values.`-eq` is used to check if two values are equal. For example, `if [ $num1 -eq $num2 ]` will be true if `$num1` is equal to `$num2`.

`---> -gt` is used to check if the left-hand side value is greater than the right-hand side value. For example, `if [ $num1 -gt $num2 ]` will be true if `$num1` is greater than `$num2`.

In the example script provided earlier, we used `-eq` and `-gt` to compare the values of `number1` and `number2`.

`---> fi` is a keyword in Bash shell scripting that marks the end of an `if` statement.

`---> echo` is a command in Bash shell scripting that is used to display text on the terminal or console. It is often used to print messages, variables, or command output to the screen.

`---> $` is a special character in Bash shell scripting that is used to indicate a variable name or to expand the value of a variable. For example -`$name` is a syntax used in Bash shell scripting to refer to the value of a variable named `name.`

`---> read` is a command in Bash shell scripting that is used to read input from the user and store it in a variable.

**Thank you for reading! Happy Learning!!**