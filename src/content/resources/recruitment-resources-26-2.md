---
title: 'Getting Started'
description: 'Setting Up the Environment'
category: 'General'
order: 1
---


## Setup
Before we proceed further, we need to know about [operating systems](https://www.techtarget.com/whatis/definition/operating-system-OS) and why to choose [linux over windows](https://www.mygreatlearning.com/blog/linux-vs-windows/).

[Here](https://www.stackscale.com/blog/popular-linux-distributions/), you can get an overview of the popular linux distros available. Now, you will [Install Kali Linux in VirtualBox](https://www.youtube.com/watch?v=irGTD6jmYhc).

If you don't really want to go through all this hassle, you can simply install [WSL](https://apps.microsoft.com/detail/9pdxgncfsczv?hl=en-US&gl=IN) from the Microsoft Store. 
Mac is already Unix-based so most commands can be run natively. Refer to the tools' documentation for further instructions.

## Moving on...
### Linux Fundamentals
To navigate and control a Linux system, you need to master the terminal. Here are the absolute essentials you will use daily:

#### Navigating & Looking Around

`pwd`: Print Working Directory. Tells you exactly where you currently are.

`ls`: Lists files and folders. Use `ls -la` to see everything, including hidden files and permissions.

`cd <dir>`: Change Directory. Moves you into `<dir>`. Use `cd ..` to move up one level.

#### Creating & Destroying

`mkdir <dir>`: Creates a new directory (folder).

`touch <file>`: Creates a new, empty file.

`cp <file1> <file2>`: Copies a file.

`mv <file1> <file2>`: Moves or renames a file.

`rm <file>`: Deletes a file forever.

*Warning*: `rm -rf /` will forcefully delete your entire operating system. Do not run this.

#### Reading & Searching

`cat <file>`: Spits out the entire contents of a file directly into your terminal.

`grep <pattern> <file>`: Searches for specific text inside a file. Incredibly useful for finding flags or specific errors.

`man <command>`: Opens the manual for a command. When in doubt, read the manual.

#### Permissions & System

`chmod <number> <file>`: Changes who can read, write, or execute a file.

`4` = Read, `2` = Write, `1` = Execute.

*Example*: `chmod 777` gives read/write/execute access to everyone. `chmod 755` gives full access to the owner, but only read/execute to others.

`ps aux`: Lists every running process on the system.

`kill <pid>`: Forcefully kills a process using its Process ID.

Read about it more [here](https://preview.redd.it/isnefnt32wn21.jpg?auto=webp&s=b6c48a27ab33a3d428b554d278eba617e35bf3a2).

### Unix Filesystem
Unlike Windows, Linux doesn't use `C:\` or `D:\` drives. Everything is structured as an upside down tree starting from a single point, and **everything is treated as a file**, even hardware. Understanding this hierarchy is crucial, especially when you start doing reverse engineering or system exploitation later on.

#### The Hierarchy Tree:

* `/` **(The Root)**: The absolute top of the filesystem. Every other directory branches off from here.
* `/bin` & `/sbin`: Contains all the essential binary executables (the actual programs for commands like `ls`, `cat`, and `kill`).
* `/home`: Where user-specific files live. If your username is student, your stuff is in `/home/student`.
* `/etc`: The nervous system. This holds the core system-wide configuration files.
* `/var`: Variable data that changes frequently. The most important thing here is `/var/log`, where the system stores its log files, essential for troubleshooting.
* `/tmp`: A temporary scratchpad space. Anyone can write here, but it usually gets wiped clean every time the system reboots.
* `/dev`: Device files. Linux treats your hard drives, terminals, and plugged-in hardware interfaces as files located in this directory.
* `/usr`: Secondary hierarchy for read-only user data. Contains user utilities, applications, and libraries.

Read about it more [here](https://homepages.uc.edu/~thomam/Intro_Unix_Text/File_System.html).
