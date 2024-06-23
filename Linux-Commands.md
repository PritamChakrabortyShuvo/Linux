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
12.

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
```bash
    
```
```bash
    
```
```bash
    
```
```bash
    
```

