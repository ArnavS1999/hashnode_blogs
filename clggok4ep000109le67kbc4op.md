---
title: "Basic Linux Commands part 2"
datePublished: Fri Apr 14 2023 15:04:31 GMT+0000 (Coordinated Universal Time)
cuid: clggok4ep000109le67kbc4op
slug: basic-linux-commands-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681484585655/55466bfc-47da-4067-9b4f-670f81970a4f.png
tags: linux, devops, linux-for-beginners, linux-basics, linux-commands

---

1. **To view what's written in a file.**
    
    To view what's written in a file we use the "**cat**" command. It will display all the content of a file.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681481160715/fc6bc51c-b04a-43c2-9c24-95ca78b6e25e.png align="center")
    
2. **To change the access permissions of files.**
    
    we can modify permissions using the "**chmod**" command.
    
    ```bash
    chmod permissions filename
    ```
    
3. **To check which commands you have run till now.**
    
    The "**history**" command in Linuxis a built-in shell tool that displays a list of commands used in the terminal session.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681482248173/b9d25a16-f042-4254-9c24-6faf4a0f4b1f.png align="center")
    
4. **To remove a directory/ Folder.**
    
    To remove an empty directory, use the "**rmdir**" command.
    
    To remove a directory and all its contents, including any subdirectories and files, use the "**rm -r**" command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681482743228/4f13b1e1-c0a9-4a9b-a117-222cd0539ac1.png align="center")
    
5. **To create a color.txt file and to view the content.**
    
    To create a color.txt we use "**touch**" command and to view the content of the file we use "**cat**" command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681483159727/72e29b67-1a28-41e0-99d2-a29d633e7599.png align="center")
    
6. **Add content in devops.txt (One in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava.**
    
    To add content in the devops.txt file we use the "**vim**" command.
    
7. **To Show only top three colors from the file.**
    
    "**cat color.txt | head -3**"
    
8. **To Show only bottom three fruits from the file.**
    
    **"cat color.txt | tail -3"**
    
9. **Add content in Color.txt (One in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey.**
    
    To add content in the devops.txt file we use the "**vim**" command.
    
10. **To find the difference between fruits.txt and Color.txt file.**
    
    The "**diff fruits.txt color.txt** "is used to find the difference between the fruits.txt and Color.txt files.