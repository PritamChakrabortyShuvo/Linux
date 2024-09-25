# 🗒️Comprehensive Guide to Essential Linux Commands🗒️

This guide provides an extensive overview of the most commonly used Linux commands. It covers various aspects of system management, file operations, network management, and user administration. Whether you're a beginner or an advanced user, this resource aims to enhance your command-line skills and streamline your workflow in a Linux environment.

### Table of Contents

- [Listing Files & Directories](#listing-files--directories)
- [Command Types](#command-types)
- [Creating Files](#creating-files)
- [Remove Files](#remove-files)
- [Copy Files](#copy-files)
- [Rename Files](#rename-files)
- [Present Working Directory](#present-working-directory)
- [Create Directory](#create-directory)
- [Change Directory](#change-directory)
- [Single Dot & Double Dot](#single-dot--double-dot)
- [Remove Directory](#remove-directory)
- [Copy Directory](#copy-directory)
- [Moving Directory](#moving-directory)
- [Concatenate a File](#concatenate-a-file)
- [Using Command Line to Get Help](#using-command-line-to-get-help)
- [Head Command Filter](#head-command-filter)
- [Tail Command Filter](#tail-command-filter)
- [Alias Command](#alias-command)
- [Environment Variables](#environment-variables)
- [Path Variables](#path-variables)
- [Bash Prompt](#bash-prompt)
- [Kernel Versoins](#kernel-versions)
- [Working with Hardware](#working-with-hardware)
- [Grep Command Filter](#grep-command-filter)
- [Awk Command Filter](#awk-command-filter)
- [File Editors](#file-editors)
- [Vim Editor](#vim-editor)
- [Command Line Browser](#command-line-browser)
- [Downloading Files](#downloading-files)
- [Extract tar archives](#extract-tar-archives)
- [User Specific Commands](#user-specific-commands)
- [Update and Install](#update-and-install)
- [Linux Networking](#linux-networking)
- [Process Management](#process-management)
- [Administration](#administration)
- [Administration - User Management](#administration---user-management)
- [Administration – Package Management](#administration--package-management)
- [Administration – Service Management](#administration--service-management)
- [Administration – Commands Reboot](#administration--commands-reboot)
- [Administration – File Ownerships](#administration--file-ownerships)
- [Administration – File Permissions](#administration--file-permissions)

### Listing Files & Directories
This command lists files and directories. Essential for file navigation in Linux.

Get list of files and directories, but it may not show hidden files.
```bash
    ls
```
**Note :** Hidden files in Linux were created with **`.`** filename

Get list of hidden files and directories.
```bash
    ls -a
```
Get list of files with long format, usually shows properties of a file.
```bash
     ls -l
```
Get list of all files and directories, including hidden ones, in detailed format.
```bash
     ls -al
```
Get list of files and directories sorted by modification time, with the most recently modified items appearing first.
```bash
    ls -t
```
### Command Types
It shows how a command is recognized by the shell, indicating if it's built-in, an alias, or an external program.
```bash
    type <command>
```
### Creating Files
We can create files in Linux in multiple ways/commands. As a basic  we always use **`touch`** command to create a file.
Creates an empty text file.
```bash
     touch file_name.txt
```
**`touch`** command can create multiple files as shown.
```bash
    touch text.txt lambda.py      
```
**Note :** In Linux we don’t have any file extensions. Extensions we may use it for our understanding.

### Remove Files
To remove files we have **`rm`** command, Also we can use **`unlink`** command which performs the same action, yet we prefer mostly to use **`rm`** command.

```bash
    rm file_name
```
This command forcefully deletes file without confirmation, bypassing write protection. Use with caution.
```bash
    rm -f file_name
```
### Copy Files
To copy a file we have **`cp`** command. Alternatively we have **`rsync`** command as well but mostly we prefer to use cp command in general.

```bash
     cp source_file.txt destination_file.txt
```
If the destination file already exists then it will overwrite the file and in few cases it may warn you to overwrite the file or not.

### Renaming Files
To rename or move a file we use **`mv`** command.

For rename the file.
```bash 
    mv old_name new_name
```
For moving the file.
```bash
    mv file_name /path/to/directory/
```
### Present Working Directory
The **`pwd`** command prints the current working directory's absolute path. It's useful for determining your current location.
```bash
    pwd
```
**Note :** It is always important to observe the directory you are in before executing the command, because in some cases if you try to execute some command and which you lead to loss of data if you executecommands in wrong location.

### Create Directory
To make a single directory
```bash
    mkdir directory_name
```
To make multiples directory
```bash
    mkdir directory1 directory2 directory3
```
This command creates a directory named **`directory2`** inside **`directory1`**. 
```bash
    mkdir directory1/directory2
```
This command creates both **`directory1`** and **`directory2`** if they don't already exist.
```bash
    mkdir -p directory1/directory2
```
**Note :** The **`-p`** option ensures that all necessary parent directories are created without errors.

### Change Directory
```bash
    cd <directory>
```
**Example :**
```bash
    cd /bin
```
You will switch to **`/bin`** directory.

Simple **`cd`** command will take you to the user home directory
```bash
    cd
```
A hyphen symbol after cd command can take you to previous working directory.
```bash
    cd -
```
Double dot denotes parent directory and it can take you to parent directory of existing directory.
```bash
    cd .. 
```
### Single Dot & Double Dot
Single dot **`(.)`** in Linux denote the present working directory.

Double dot **`(..)`** denotes the parent directory.
```bash
    cp /home/desktop/file.txt .
```
Here dot denotes to copy the file in this location without specifying any filename or path

### Remove Directory
Removing directory commands needed to be picked based on requirement.

To remove empty directories we use **`rmdir`** command.
```bash
   rmdir empty_directory_name
```
To remove directories recursively we use **`rf`** command
```bash
    rm –rf dir1 dir2
```
This command recursively and forcefully removes multiple directories and all its contents.

**Note :** This action cannot be undone and deletes files permanently.

### Copy Directory
Copying directories can be done with cp command.

It copies dir1 to dir2 and all the contents of dir1 will be copied to dir2 as well.
```bash
    cp -r dir1 dir2
```
**Note :** While copying the directories we need to mention **`–r`** option to enable that we are copying directories.

### Moving Directory
Moving directories or renaming directories can be done with **`mv`** command.
```bash
    mv file /path/to/directory
```
Depends on the situation it will rename or move.

- If destination does not exists then it renames the directory.

- If destination exists:
    - Destination is a file - Then that is a invalid operation.
    - Destination is a directory – Then the source will be moved into destination directory.
### Concatenate a File
In view the complete content of a file then we will concatenate (cat) the file.

Shows complete content of a file.
```bash
    cat file_name
```
Shows the content with line numbers added on output.
```bash
    cat -n file_name
```
This command allows creating or overwriting a file and entering text directly into it.
```bash
    cat >file_name
```
**Note :** After running the command input is taken from the keyboard and pressing **`Ctrl`** **+** **`D`** saves the input and exits.

It will print the lines in reverse order mean last line in first and first line at last.
```bash
    tac file_name
```
### Using Command Line to Get Help

This command provides a one-line description of a specified command or program, summarizing its function.
```bash
    whatis <command>
```
This command displays the manual page for a specified command or program, providing detailed documentation about its usage, options, and examples
```bash
    man <command>
```
### Head Command Filter 
**`head`** command can give the **top 10 lines** by default.
```bash
    head file_name
```
Print top 5 lines.
```bash
    head -n 5 file_name
```
### Tail Command Filter
**`tail`** command can give the **last 10 lines** by default.
```bash
    tail file_name
```
Print last 5 lines.
```bash
    tail -n 5 file_name
```
```bash
    tail -f file_name
```
**-f** option continuously monitors and displays the last part of a file, updating the output as new lines are added.

**Note :** To come out of **`tail –f`** you can press **`CTRL + C`** on terminal.

### Alias Command
This command creates a shortcut or nickname for a longer command in the shell allowing users to execute complex or frequently used commands more easily.
```bash
    alias ll='ls -l'
```
This creates a shortcut **`ll`** that lists files in long format.
### Environment Variables 
This command shows the current environment variables or lets a command run with specific variable settings.
```bash
    env
```
Shows the current username stored in the **`LOGNAME`** variable.
```bash
    echo $LOGNAME
```
Sets **`LOGNAME`** to **`user1`** and makes it available for other programs.
```bash
    export LOGNAME=user1
```
This sets the **`LOGNAME`** variable to **`user2`** in the current shell session but it does not **export** it so it's not available to child processes.
```bash
    LOGNAME=user2
```
### Path Variables
Displays the current list of directories where the shell looks for executable programs.
```bash
    echo $PATH
```
Shows the full path of the specified executable program, if it exists in the directories listed in the **`PATH`**.
```bash
    which program
```
 Adds **`/opt/apps/bin`** to the end of the existing **`PATH`** allowing the system to find executables in that directory.
```bash
    export PATH=$PATH:/opt/apps/bin
```
### Bash Prompt
The command changes the terminal prompt to simply show **Server01 :**.
```bash
    PS1="Server01 :"
```
This command customizes the terminal prompt to display the date (**`\d`**), time (**`\t`**), username (**`\u`**), hostname (**`\h`**), and current working directory (**`\w`**), followed by a dollar sign (**`$`**).
```bash
    PS1="[\d \t \u@\h:\w ] $ "
```
Here’s a simplified explanation of each of the prompt escape sequences :
- **`\d`**: Displays the date in "Weekday Month Date" format (e.g., "Tue May 26").
- **`\e`**: Represents an ASCII escape character (033).
- **`\h`**: Shows the hostname up to the first dot (e.g., "HQDN").
- **`\H`**: Displays the full hostname.
- **`\n`**: Inserts a newline character.
- **`\r`**: Inserts a carriage return.
- **`\s`**: Displays the name of the shell.
- **`\t`**: Shows the current time in 24-hour HH:MM format.
- **`\T`**: Shows the current time in 12-hour HH:MM format.
- **`\@`**: Displays the current time in 12-hour am/pm format.
- **`\A`**: Shows the current time in 24-hour HH format.
- **`\u`**: Displays the username of the current user.
- **`\w`**: Shows the current working directory, with $HOME abbreviated as a tilde (~).
- **`\W`**: Displays the basename of the current working directory, with $HOME abbreviated as a tilde (~).
- **`\$`**: Displays a # if the user is root (UID 0) and a $ otherwise.

### Kernel Versions
Displays the kernel version of the operating system currently running on the system.
```bash
    uname -r
```
Suppose the Kerner Version is **`4.15.0-72-generic`**. Here
- **`4`** : Kernel Version
- **`15`** : Major Version
- **`0`** : Minor Version
- **`72`** : Patch Release
- **`Generic`** : Distro Specific Information

### Working with Hardware
Shows system messages related to the kernel and hardware events, useful for troubleshooting.
```bash
    dmesg
```
Filters the system messages to show only those about **USB devices** making it easier to find related info.
```bash
    dmesg | grep -i usb
```
Displays the path and details for the device named **`/dev/sda5`** helping identify its hardware location.
```bash
    udevadm info --query=path --name=/dev/sda5
```
Watches and shows real-time changes to devices, like when devices are plugged in or removed.
```bash
    udevadm monitor
```
Lists all devices connected to the PCI bus, like graphics cards and network cards, giving an overview of hardware.
```bash
    lspci
```
 Displays all block devices (like hard drives and partitions) in a simple format showing how they are connected.
```bash
    lsblk
```
Provides details about the CPU, such as the number of cores and speed, helping understand processing power.
```bash
    lscpu
```
Summarizes the system's memory showing total memory and available memory blocks.
```bash
    lsmem --summary
```
Displays used and free memory in megabytes, giving a quick overview of the system's memory status.
```bash
    free -m
```
Lists detailed information about all hardware in the system requiring admin access for full details.
```bash
   sudo lshw 
```
### Package Management 
1. Working with **`RPM`** : Suppose we have a package called **`telnet.rpm`** in rpm format. 

    Installs the telnet package with a progress bar and detailed output.
     ```bash
        rpm -ivh telnet.rpm
     ```
    **Note :** **`i`** stands for install; **`-v`** stands for verbose & provide detailed output during installation; **`-h`** stands for hash and shows a progress bar with hash marks.
    Here
    Uninstalls (erases) the telnet package from the system.
    ```bash
        rpm -e telnet.rpm
     ```
    Upgrades or installs the telnet package with verbose output and progress bar.
    ```bash
        rpm -Uvh telnet.rpm
     ```
    **Note :** **`U`** stands for upgrade.
    Queries whether the telnet package is installed on the system.
    ```bash
        rpm -q telnet.rpm
     ```
    Verifies which package owns the specified file and checks its integrity.
    ```bash
        rpm -Vf <path to file>
     ```
2. Working with **`DPKG`** : Suppose we have a package called **`telnet.deb`** in deb format. 

    Installs the telnet package with a progress bar and detailed output.
     ```bash
        dpkg -i telnet.deb
     ```
    **Note :** **`i`** stands for install.
    Here
    Uninstalls (erases) the telnet package from the system.
    ```bash
        dpkg -r telnet.deb
     ```
    Lists information about the installed telnet package, including its version and description.
    ```bash
        dpkg –l telnet
     ```
    Shows detailed status information about the telnet package, such as whether it is installed and its configuration.
    ```bash
        dpkg –s telnet
     ```
    Displays information about the package from the specified file path, including its contents and metadata.
    ```bash
        dpkg –p <path to file>
     ```
3. Working with **`APT`** : Here are the descriptions for each **`apt`** command :

    Refreshes the list of available packages and their versions from the repositories.
    ```bash
        apt update
    ```
    Installs the latest versions of all installed packages on the system.
    ```bash
        apt upgrade
    ```
    Opens the sources list file for editing, allowing changes to the repositories used for package management.
    ```bash
        apt edit-sources
    ```
    Installs the telnet package and its dependencies.
    ```bash
        apt install telnet
    ```
    Uninstalls the telnet package from the system.
    ```bash
        apt remove telnet
    ```
    Searches for available packages related to telnet in the repositories.
    ```bash
       apt search telnet 
    ```
    Lists all installed and available packages and filters the output to show only those related to telnet.
    ```bash
       apt list | grep telnet 
    ```

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

Prints the first column from each line.
```bash
    awk '{print $1}' file_name
```
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
This command is useful for downloading files from the internet directly to your local system using the command line.
```bash
    curl URL -o file_name_to_save_download
```
### Downloading Files
Most of the times we just need to download the software of different tools which we work on. To just download the software we can use **`wget`** command.

Command **`wget`** just downloads the file in the location which you are in, Else you can provide a custom location as well.
```bash
    wget URL
```
Downloads the file in given path and name.
```bash
    wget -o /opt/file_name URL
```
### Extract tar archives
To extract files from a **`.tar`** archive in Linux, use the **`tar`** command. Command **`tar`** can be used for both extraction and creation of archives.

To extract the tar archives we use **`–x`** option.
```bash
    tar -xf <file>.tar
```
### User Specific Commands
All accesses into a Linux System are through a User.

Create a User.
```bash
    useradd user_name
```
Delete a User.
```bash
    userdel user_name
```
Start new shell as different user.
```bash
    su -[username]
```
User information lookup.
```bash
    finger
```
Change or Create user password.
```bash
    passwd
```
Prints the current username of the logged-in user. 
```bash
    whoami
```
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

For install package.
```bash
    sudo apt install <package_name>
```

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

List the process running in current session.
```bash
    ps
```
List process running by the user you logged in.
```bash
    ps –u
```
Get all process running inside OS.
```bash
    ps –e
```
All process listed out with more detailed way. 
```bash
    ps –ef
```
- We do need to manage these process, Some cases we need to stop/kill them.

- To kill any process under Linux OS can use kill command.

- Command kill will be used to kill the process with PID as input provided.

- In general we use two type of killing a process by using a signal number 15 and 9, 15 is default signal and we no need to specify in particular.

Kill the process of given PID with 15 signal.
```bash
    kill PID
```
Kill the process of given PID with 9 signal.
```bash
    kill -9 PID
```
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
To add a user to multiple groups.
```bash
    usermod –a –G bin pritam
```
To set a password to the user (Clouds will not use password by default)
```bash
    passwd pritam
```
You can switch user from one user to another user using.
```bash
    su shuvo
```
To again another user with out password using **`sudo`**.
```bash
    sudo su - pritam
```
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
This markdown file serves as a comprehensive guide to essential Linux commands, crucial for any Linux user, system administrator, or DevOps professional. By mastering these commands, you'll be able to navigate and manage your Linux environment efficiently, automate repetitive tasks, and troubleshoot issues effectively.