# 🗒️Comprehensive Guide to Essential Linux Commands🗒️

This guide provides an extensive overview of the most commonly used Linux commands. It covers various aspects of system management, file operations, network management, and user administration. Whether you're a beginner or an advanced user, this resource aims to enhance your command-line skills and streamline your workflow in a Linux environment.

### Table of Contents

1. [Listing Files & Directories](#listing-files--directories)
2. [Creating Files](#creating-files)
3. [Remove Files](#remove-files)
4. [Copy Files](#copy-files)
5. [Present Working Directory](#present-working-directory)
6. [Change Directory](#change-directory)
7. [Single Dot & Double Dot](#single-dot--double-dot)
8. [Create Directory](#create-directory)
9. [Remove Directory](#remove-directory)
10. [Copy Directory](#copy-directory)
11. [Moving Directory](#moving-directory)
12. [Concatenate a File](#concatenate-a-file)
13. [Head Command Filter](#head-command-filter)
14. [Tail Command Filter](#tail-command-filter)
15. [Grep Command Filter](#grep-command-filter)
16. [Awk Command Filter](#awk-command-filter)
17. [File Editors](#file-editors)
18. [Vim Editor](#vim-editor)
19. [Command Line Browser](#command-line-browser)
20. [Downloading Files](#downloading-files)
21. [Extract tar archives](#extract-tar-archives)
22. [User Specific Commands](#user-specific-commands)
23. [Update and Install](#update-and-install)
24. [Linux Networking](#linux-networking)
25. [Process Management](#process-management)
26. [Administration](#administration)
27. [Administration - User Management](#administration---user-management)
28. [Administration – Package Management](#administration--package-management)
29. [Administration – Service Management](#administration--service-management)
30. [Administration – Commands Reboot](#administration--commands-reboot)
31. [Administration – File Ownerships](#administration--file-ownerships)
32. [Administration – File Permissions](#administration--file-permissions)

### Listing Files & Directories
This command lists files and directories. Essential for file navigation in Linux
```bash
    ls
```
Get list of files and directories, but it may not show hidden files.

**Note :** Hidden files in Linux were created with **`.`** filename

```bash
    ls -a
```
Get list of hidden files and directories.

```bash
     ls -l
```
Get list of files with long format, usually shows properties of a file.

```bash
     ls -al
```
Get list of all files and directories, including hidden ones, in detailed format
```bash
    ls -t
```
Get list of files and directories sorted by modification time, with the most recently modified items appearing first.

### Creating Files
We can create files in Linux in multiple ways/commands. As a basic  we always use **`touch`** command to create a file.
```bash
     touch file_name.txt
```
Creates an empty text file.

```bash
    touch text.txt lambda.py      
```
*`touch`* command can create multiple files as shown.

**Note :** In Linux we don’t have any file extensions. Extensions we may use it for our understanding.

### Remove Files
To remove files we have **`rm`** command, Also we can use **`unlink`** command which performs the same action, yet we prefer mostly to use **`rm`** command.

```bash
    rm file_name
```
```bash
    rm -f file_name
```
This command forcefully deletes file without confirmation, bypassing write protection. Use with caution.

### Copy Files
To copy a file we have **`cp`** command. Alternatively we have **`rsync`** command as well but mostly we prefer to use cp command in general.

```bash
     cp source_file.txt destination_file.txt
```
If the destination file already exists then it will overwrite the file and in few cases it may warn you to overwrite the file or not.

### Renaming Files
To rename or move a file we use **`mv`** command.
```bash 
    mv old_name new_name
```
For rename the file.

```bash
    mv file_name /path/to/directory/
```
For moving the file.

### Present Working Directory
```bash
    pwd
```
The **`pwd`** command prints the current working directory's absolute path. It's useful for determining your current location.

**Note :** It is always important to observe the directory you are in before executing the command, because in some cases if you try to execute some command and which you lead to loss of data if you executecommands in wrong location.

### Change Directory
```bash
    cd <directory>
```
**Example :**
```bash
    cd /bin
```
You will switch to **`/bin`** directory.

```bash
    cd
```
Simple **`cd`** command will take you to the user home directory

```bash
    cd -
```
A hyphen symbol after cd command can take you to previous working directory.

```bash
    cd .. 
```
Double dot denotes parent directory and it can take you to 
parent directory of existing directory.

### Single Dot & Double Dot
Single dot **`(.)`** in Linux denote the present working directory.

Double dot **`(..)`** denotes the parent directory.
```bash
    cp /home/desktop/file.txt .
```
Here dot denotes to copy the file in this location without specifying any filename or path

### Create Directory
To create a directory you can use **`mkdir`** command.

```bash
    mkdir directory_name
```
```bash
    mkdir -p demo/new/item1
```
Creates a directory and any necessary parent directories that do not exist. It ensures that the entire path specified is created, even if multiple directories need to be nested. 

```bash
    mkdir dir1 dir2 
```
Can create multiple directories also at the same time.

### Remove Directory
Removing directory commands needed to be picked based on requirement.

To remove empty directories we use **`rmdir`** command.
```bash
   rmdir empty_directory_name
```
To remove directories recursively we use **`rm`** command
```bash
    rm –rf dir1 dir2
```
This command recursively and forcefully removes multiple directories and all its contents.

**Note :** This action cannot be undone and deletes files permanently.

### Copy Directory
Copying directories can be done with cp command.

**Note :** While copying the directories we need to mention **`–r`** option to enable that we are copying directories.
```bash
    cp -r dir1 dir2
```
It copies dir1 to dir2 and all the contents of dir1 will be copied to dir2 as well.

### Moving Directory
Moving directories or renaming directories can be done with **`mv`** 
command.
```bash
    mv file /path/to/directory
```
Depends on the situation it will rename or move.

- If destination does not exists then it renames the directory.

- If destination exists:
    - Destination is a file - Then that is a invalid operation.
    - Destination is a directory – Then the source will be moved into 
destination directory.

### Concatenate a File
In view the complete content of a file then we will concatenate (cat) the file.
```bash
    cat file_name
```
It shows complete content of a file 
```bash
    cat -n file_name
```
Shows the content with line numbers added on output.
```bash
    tac file_name
```
It will print the lines in reverse order mean last line in first and first line at last.

### Head Command Filter 
**`head`** command can give the **top 10 lines** by default.
```bash
    head file_name
```
```bash
    head -n 5 file_name
```
Print top 5 lines.

### Tail Command Filter
**`tail`** command can give the **last 10 lines** by default.
```bash
    tail file_name
```
```bash
    tail -n 5 file_name
```
Print last 5 lines.
```bash
    tail -f file_name
```
**-f** option continuously monitors and displays the last part of a file, updating the output as new lines are added.
**Note :** To come out of **`tail –f`** you can press **`CTRL + C`** on terminal.

### Grep Command Filter
The **`grep`** command searches for a specific word or string in files and prints only the lines containing that word or string.
```bash
    grep word file_name
```
**Example :**
```bash
    grep root passwd
```
It fethes all the lines having a word root in passwd file.

### Awk Command Filter
The **`awk`** command scans and processes text files. It can extract and print specific columns of data. 
```bash
    awk '{print $1}' file_name
```
Prints the first column from each line.

### File Editors
File editors are tools used to create, modify, and manage text files in Linux. Common file editors include:

- **`nano`**: A simple, easy-to-use text editor with basic features. Ideal for beginners.

- **`vi / vim`**: A powerful, advanced text editor with extensive features for efficient text editing. Suitable for experienced users.But **`vi`** is widely used and **`vim`** is a enhanced version of **`vi`**. 

- **`gedit`**: A graphical text editor with a user-friendly interface, part of the GNOME desktop environment.

These editors help users edit configuration files, write scripts, and manage documents directly from the command line or a graphical interface.
### Vim Editor 
**`vim`** (Vi IMproved) is a highly configurable and powerful text editor used in Linux. It extends the capabilities of the older **`vi`** editor and is suitable for both beginners and advanced users.
```bash
    vim file_name
```
![Project Logo](Images/VIM%20Editor.png)

#### ESC Mode
In vim (Vi IMproved) editor, the **`ESC`** (Escape) key is pivotal for navigating and executing commands in Normal mode. Here are key functionalities in ESC mode:

- **Navigation:**

    - **`h`**: Move left
    - **`j`**: Move down
    - **`k`**: Move up
    - **`l`**: Move right

- **Editing:**

    - **`x`**: Delete the character under the cursor
    - **`dd`**: Delete the current line
    - **`yy`**: Yank (copy) the current line
    - **`p`**: Paste the yanked text after the cursor position

- **Search and Replace:**

    - **`/pattern`**: Search forward for "pattern"
    - **`n`**: Move to the next occurrence of the search pattern
    - **`N`**: Move to the previous occurrence of the search pattern
    - **`:s/pattern/replacement`**: Replace "pattern" with "replacement" in the current line

- **Saving and Quitting:**

    - **`:w`**: Save changes (write)
    - **`:q`**: Quit (close the file)
    - **`:q!`**: Quit without saving changes (force quit)
    - **`:wq`** or **`:x`**: Save changes and quit

- Modes:

    - Normal Mode: Press **`Esc`** to enter Normal mode, where you can navigate and execute commands.
    - Insert Mode: Press **`i`** to enter Insert mode, where you can insert and edit text.
    - Visual Mode: Press **`v`** to enter Visual mode, where you can select blocks of text for editing or copying.

### Command Line Browser
Most of the time you need to browse URLs and fetch that content over the command line. Some times we need some partial information of that URL else we need complete information of that URL.

Command **`curl`** is available to browse the content over the command line.
```bash
    curl URL
```
```bash
    curl URL -o file_name_to_save_download
```
This command is useful for downloading files from the internet directly to your local system using the command line.

### Downloading Files
Most of the times we just need to download the software of different tools which we work on. To just download the software we can use **`wget`** command.

Command **`wget`** just downloads the file in the location which you are in, Else you can provide a custom location as well.
```bash
    wget URL
```
```bash
    wget -o /opt/file_name URL
```
Downloads the file in given path and name.

### Extract tar archives
To extract files from a **`.tar`** archive in Linux, use the **`tar`** command. Command **`tar`** can be used for both extraction and creation of archives.

To extract the tar archives we use **`–x`** option.
```bash
    tar -xf <file>.tar
```
### User Specific Commands
All accesses into a Linux System are through a User.
```bash
    useradd
```
Create User.
```bash
    userdel
```
Delete User.
```bash
    su -[username]
```
Start new shell as different user.

```bash
    finger
```
User information lookup.

```bash
    passwd
```
Change or Create user password

```bash
    whoami
```
Prints the current username of the logged-in user. 

```bash
    who
```
### Update and Install
Displays information about users who are currently logged into the system. 
```bash
   sudo apt update 
```
This command updates the local package index from the repositories configured in your system's **`sources.list`** file. It does not install or upgrade any packages; instead, it retrieves information about available packages and their versions, ensuring your system has the latest information about available software.
```bash
    sudo apt upgrade
```
This command upgrades all installed packages to their latest versions, respecting package dependencies and ensuring your system is up to date.

```bash
    sudo apt install <package_name>
```
For install package.

### Linux Networking

```bash
    ifconfig
```
This command is used to configure and display the network interfaces and their IP addresses.

```bash
    ip addr
```
This command is used to show or manipulate routing, devices, policy routing and tunnels.

```bash
    ip link
```
This command is used to display information about link layer devices currently configured.

```bash
    ip route
```
This command is used to show and manipulate the IP routing table.

```bash
    sudo lsof -i :80
```
This is used to list all processes that are currently listening on port 80 (HTTP) on your system.
```bash
    sudo kill $(sudo lsof -t -i :80)
```
It will effectively terminates (kills) all processes that are currently listening on port 80.

### Process Management

Every command we execute in Linux will create a process and every process will get an associated ID which we generally call it as PID and it is unique in the OS which is taken care by Kernel.

As part of our job we will manage such processes run inside server. In order to manage those process we need the information about the process. Command ps can help us in getting required/all process running inside the OS.

```bash
    ps
```
List the process running in current session.

```bash
    ps –u
```
List process running by the user you logged in.

```bash
    ps –e
```
Get all process running inside OS.

```bash
    ps –ef
```
All process listed out with more detailed way. 

- We do need to manage these process, Some cases we need to stop/kill them.

- To kill any process under Linux OS can use kill command.

- Command kill will be used to kill the process with PID as input provided.

- In general we use two type of killing a process by using a signal number 15 and 9, 15 is default signal and we no need to specify in particular.

```bash
    kill PID
```
Kill the process of given PID with 15 signal.

```bash
    kill -9 PID
```
Kill the process of given PID with 9 signal.

**Note :** 15 signal is graceful kill and where as 9 is forceful kill of a process.

### Administration 

- In Linux, All admin activities cannot be performed by normal user. We need to be a root user to perform any activities.

- To perform those admin activities we use **`sudo`** command to gain the root access and perform those admin commands.

- To any admin command we can prefix **`sudo`** command to gain root privilege.

- As we are using cloud based servers we usually login with normal user like centos and such default users will have complete **`sudo`** access by default.

- In companies we usually will have individual accounts and we can perform the admin activities which are allowed using **`sudo`** access.

### Administration - User Management

In Linux family, User cannot be added with out a group. So we need a group in order to add a user. User can be part of one more group but primarily should be associated with one group.
```bash
    sudo groupadd devops
```
To check whether the group added or not by using **`cat /etc/group | grep devops`**

We can now add a user to devops group.

```bash
    sudo useradd –g devops pritam
```
To verify the user which was added.
```bash
    id pritam
```
```bash
    usermod –a –G bin pritam
```
To add a user to multiple groups.

```bash
    passwd pritam
```
To set a password to the user (Clouds will not use password by default)

```bash
    su raju
```
You can switch user from one user to another user using.

```bash
    sudo su - raju
```
To again another user with out password using **`sudo`**.

### Administration – Package Management

In Linux uses rpm for packaging. Such packages can be downloaded and installed using **`yum`** command which uses **`rpm`** command in backend.

**`YUM`** has capability to download and install the packages from different sources which are defined under **`/etc/yum.repos.d/*.repo`**
```bash
    sudo yum list / sudo yum list all 
```
```bash
    sudo yum list installed 
```
```bash
    sudo yum list available
```
```bash
    sudo yum install httpd –y
```
```bash
    sudo yum remove httpd –y
```
```bash
     sudo yum update httpd –y
```
### Administration – Service Management

RedHat Linux 7 uses **`systemctl`** command to manage the services, Earlier till 6 version we use to use **`service`** command.

To list all services which are active.

```bash
    sudo systemctl list-units -t service 
```
To start/stop/restart a service.
```bash
    sudo systemctl start httpd 
    sudo systemctl stop httpd 
    sudo systemctl restart httpd
```
To check the status of httpd.
```bash
    sudo systemctl status httpd
```
To start the service at the time of reboot automatically then

```bash
    sudo systemctl enable httpd 
```
```bash
    sudo systemctl disable httpd
```
### Administration – Commands Reboot
We can use following commands to reboot a server.
```bash
    reboot
    init 6
    shutdown -r
```
We can use following commands to shutdown a server.

```bash
    init 0
    shutdown -s 
    halt
```
We can validate system restarted by referring the startup time.

```bash
    uptime
```
### Administration – File Ownerships
To change the owner / group of a file 
```bash
    chown <owner-name> file/directory
```
```bash
    chgrp <group-name> file/directory
```
```bash
    chown <owner-name>:<group-name> file/directory
```
**Note :** **-R** option need to be used for a directory.

###  Administration – File Permissions 
To change the permission of a file
```bash
    chmod <notation> file/directory
```
