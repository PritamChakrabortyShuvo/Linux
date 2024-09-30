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
- [Package Management](#package-management)
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
1. **Working with **`RPM`** :** Suppose we have a package called **`telnet.rpm`** in rpm format. 

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
2. **Working with **`DPKG`** :** Suppose we have a package called **`telnet.deb`** in deb format. 

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
3. **Working with **`APT`** :** Here are the descriptions for each **`apt`** command :

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
### Vieweing File Sizes

Shows the size of test.img in kilobytes (KB), in a simple total format.
```bash
    du -sk test.img 
```
Displays the size of test.img in a human-readable format (like KB, MB, GB).
```bash
    du -sh test.img 
```
Lists test.img file details, including size, in a human-readable format with file permissions and date modified.
```bash
    ls -lh test.img 
```
### Archiving Files
Creates an archive named **`test.tar`** that includes file1 & file2
```bash
    tar -cf test.tar file1 file2 
```
Lists detailed information about the **`test.tar`** file showing its size, permissions &modification date in long format.
```bash
    ls -ltr test.tar 
```
Lists the contents of the **`test.tar`** archive without extracting them
```bash
    tar -tf test.tar 
```
Extracts the files from the **`test.tar`** archive.
```bash
    tar -xf test.tar 
```
Creates a compressed archive (using gzip) named **`test.tar.gz`** containing file1 & file2.
```bash
    tar -zcf test.tar file1 file2 
```
### Compressing 
Compresses **`test.img`** using **`bzip2`** creating a **`test.img.bz2`** file.
```bash
    bzip2 test.img 
```
Compresses **`test.img`** using **`gzip`** creating a **`test.img.gz`** file.
```bash
    gzip test.img 
```
Compresses **`test.img`** using **`xz`** creating a **`test.img.xz`** file.
```bash
    xz test2.img 
```
### Uncompressing
Decompresses **`test.img.bz2`** restoring it to the original **`test.img`** file.
```bash
    bunzip2 test.img.bz2 
```
Decompresses **`test1.img.gz`** restoring it to the original **`test.img`** file.
```bash
    gunzip test1.img.gz 
```
Decompresses **`test.img.xz`** restoring it to the original **`test.img`** file.
```bash
    unxz test1.img.xz 
```
### Compressing Files
Displays the contents of hostfile.txt.bz2 without extracting it.
```bash
    bzcat hostfile.txt.bz2 
```
### Searching for Files and Directories
Quickly searches and displays the paths of files named **`Test.txt`** using a prebuilt file index.
```bash
    locate Test.txt 
```
Searches for a file named Test.txt starting from the /home/user01 directory and displays its path if found.
```bash
    find /home/user01 -name Test.txt 
```
**Note :** If the database is not up-to-date, running **`sudo updatedb`** can refresh it.
### Grep Command Filter
The **`grep`** command searches for a specific word or string in files and prints only the lines containing that word or string.
```bash
    grep word file_name
```
**Example :**
```bash
    grep Hello Test.txt
```
It fethes all the lines having a word Hello in **`Test.txt`** file.
**Note :** **`grep`** is case sensitive use **`-i`**.

**Example :**
```bash
    grep hello -i Test.txt
```
It fethes all the lines having a word Hello in **`Test.txt`** file.

### Awk Command Filter
The **`awk`** command scans and processes text files. It can extract and print specific columns of data. 

Prints the first column from each line.
```bash
    awk '{print $1}' file_name
```
### Linux Networking
Queries the DNS to find the IP address associated with the domain name **`www.google.com`**.
Add your line here
```bash
    nslookup www.google.com
```
Queries DNS records for **`www.google.com`** and displays the corresponding IP address
```bash
    dig www.google.com
```
Displays and configures network interface parameters.
```bash
    ifconfig
```
Displays IP addresses assigned to all network interfaces.
```bash
    ip addr
```
Lists network interfaces and their statuses.
```bash
    ip link
```
Displays or modifies the IP routing table.
```bash
    route
```
Displays the routing table for network traffic.
```bash
    ip route
```
Assigns the IP address **`192.168.1.10`** with a subnet mask of **`/24`** to the network interface **`eth0`**.
```bash
     ip addr add 192.168.1.10/24 dev eth0
```
Adds a route to the **`192.168.1.0/24`** network, directing traffic through the gateway **`192.168.2.1`**.
```bash
     ip route add 192.168.1.0/24 via 192.168.2.1 
```
This is used to list all processes that are currently listening on port 80 (HTTP) on your system.
```bash
    sudo lsof -i :80
```
It will effectively terminates (kills) all processes that are currently listening on port 80.
```bash
    sudo kill $(sudo lsof -t -i :80)
```
Traces the path that packets take from the local machine to the IP address **`192.168.2.5`** showing each hop along the route and the time taken to reach each one.
```bash
    traceroute 192.168.2.5
```
Shows all active network connections on port 80 that are currently listening for incoming connections.
```bash
    netstat -an | grep 80 | grep -i LISTEN
```
### Security and File Permissions

In Linux family, User cannot be added with out a group. So we need a group in order to add a user. User can be part of one more group but primarily should be associated with one group.

This command creates a new user with a home directory and basic configuration.
```bash
    sudo adduser username
```
This allows the admin or the user to change their password.
```bash
    passwd username
```
Shows the user ID (UID) and group ID (GID) of the current user.
```bash
    id
```
Displays a list of users currently logged into the system.
```bash
    who
```
Shows a history of all users who have logged in and out.
```bash
    last
```
Switches to another user (including root) with their environment settings.
```bash
    su -
```
You can switch user from one user to another user using.
```bash
    su user01
```
This removes a user from the system.
```bash
    sudo deluser user01
```
To set a password to the user.
```bash
    passwd user01
```
To again another user with out password using **`sudo`**.
```bash
    sudo su - pritam
```
Runs a command (whoami in this case) as another user without switching fully.
```bash
    su -c "whoami"
```
Displays the list of users and permissions who can run commands as superuser using **`sudo`**.
```bash
    cat /etc/sudoers
```
A file that contains basic information about user accounts, including usernames, user IDs (UIDs), group IDs (GIDs), home directories, and default shells.
```bash
     /etc/passwd
```
A file that securely stores hashed passwords and account expiration information for user accounts, accessible only to privileged users for enhanced security.
```bash
     /etc/shadow
```
A file that defines user groups on the system, listing group names, group IDs (GIDs), and the members of each group for managing permissions collectively.
```bash
     /etc/group
```
To check whether the group added or not.
```bash
    cat /etc/group | grep devops
```
If there is no group called devops creates a new user group called **"devops"** with administrative privileges **`sudo`**.
```bash
    sudo groupadd devops
```
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
Provide full access to user.
```bash
     chmod u+rwx test-file
```
Provide read access to user, groups and others, Remove execute access
```bash
    chmod ugo+r-x test-file
```
Remove all access for others
```bash
    chmod o-rwx test-file
```
Fullaccess for user, add read, remove execute for group & no access for others
```bash
    chmod u+rwx,g+r-x,o-rwx test-file
```
Provide full access to users, group & others
```bash
    chmod 777 test-file
```
Provide read and execute access to users, groups & others
```bash
    chmod 555 test-file
```
Read and Write access for user & Group no access for others.
```bash
    chmod 660 test-file
```
Fullaccess for user,read and execute for group no access for others.
```bash
    chmod 750 test-file
```
Changes owner to user and group to developer
```bash
    chown user_name:developer test-file
```
Changes just the owner of the file to user_name.Group
```bash
    chown user_name andoid.apk
```
Change the group for the test-file to the group called android.
```bash
    chgrp android test-file
```
### SSH
Connects to a remote server using its hostname or IP address.
```bash
    ssh <hostname OR IP Address>
```
Connects to a remote server as the specified user.
```bash
   ssh <user>@<hostname OR IP Address> 
```
Connects to a remote server, specifying the user with the **`-l`** option.
```bash
    ssh -l <user> <hostname OR IP Address>
```
Generates an SSH key pair (public and private keys) using the RSA encryption algorithm.
```bash
    ssh-keygen -t rsa
```
Copies the public SSH key to the remote server to enable password-less login for the specified user.
```bash
    ssh-copy-id user@devapp01
```
Connects to the **`devapp01`** server.
```bash
    ssh devapp01
```
Displays the contents of the authorized_keys file, showing the public keys authorized for SSH login.
```bash
    cat /home/user/.ssh/authorized_keys
```
### SCP
Securely copies a file (**`caleston-code.tar.gz`**) from the local machine to the remote server (**`devapp01`**) in the **`/home/user`** directory.
```bash
    scp /home/user/caleston-code.tar.gz devapp01:/home/user
```
Securely copies a file to the **`/root`** directory on the remote server.
```bash
    scp /home/user/caleston-code.tar.gz devapp01:/root
```
Recursively and securely copies the media directory from the local machine to the **`/home/user`** directory on the remote server.
```bash
    scp -pr /home/user/media/ devapp01:/home/user
```
### IP Tables
Displays the current firewall rules set by iptables.
```bash
    iptables
```
Lists all the current rules in all chains (INPUT, OUTPUT, FORWARD) for easy viewing.
```bash
    iptables -L
```
Allows incoming TCP traffic on port **`22`** (SSH) from the IP address **`172.16.238.188`**
```bash
    iptables -A INPUT -p tcp -s 172.16.238.188 --dport 22 -j ACCEPT
```
Blocks all outgoing TCP traffic to port **`443`** (HTTPS) for all destinations.
```bash
    iptables -A OUTPUT -p tcp --dport 443 -j DROP
```
Inserts a rule at the top of the OUTPUT chain to allow outgoing TCP traffic to the IP address **`172.16.238.100`** on port **`443`** (HTTPS).
```bash
   iptables -I OUTPUT -p tcp -d 172.16.238.100 --dport 443 -j ACCEPT 
```
Allows incoming TCP traffic on port **`80`** (HTTP) from the IP address **`172.16.238.187`**.
```bash
    iptables -A INPUT -p tcp -s 172.16.238.187 --dport 80 -j ACCEPT
```
It is used to delete a 5 no rule from the OUTPUT chain in the iptables firewall.
```bash
    iptables -D OUTPUT 5
```
### Crontab
To view crontab.
```bash
    crontab -l
```
To edit crontab.
```bash
    crontab -e
```
In the crontab editor schedule the command or script. For example, to append the current date and time to **myfile.txt** every day at **12:00 PM** (noon) we add the following line
```bash
    0 12 * * * echo "$(date)" >> /path/to/myfile.txt
```
Remove all cron job.
```bash
    crontab -r
```
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
This command upgrades all installed packages to their latest versions, respecting package dependencies and ensuring your system is up to date.

For install package.
```bash
    sudo apt install <package_name>
```



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