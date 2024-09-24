# 💻Linux Theoretical Concepts💻

![Project Logo](Images/Linux%20Image.png)


Welcome! to **Linux Theoretical Concepts** guide. This is your go-to guide for mastering Linux concepts and theory. Whether you're a beginner or need a quick reference, it offers essential insights to enhance your Linux understanding and usage.

## Table of Contents

1. [What is Linux?](#what-is-linux)
2. [Who is Linux?](#who-is-linux)
3. [Where is Linux?](#where-is-linux)
4. [Why is Linux?](#why-is-linux)
5. [Common Challenges](#common-challenges)
5. [Linux Architecture](#linux-architecture)
6. [File System Hierarchy in Linux](#file-system-hierarchy-in-linux)
7. [Linux Distributions](#linux-distributions)
8. [Linux VS Unix](#linux-vs-unix)
9. [Linux Interaction](#Linux-interaction)

## What is Linux?
Linux is an **open-source operating system** based on **Unix**, widely used for *servers*, *desktops*, and *embedded systems*. 
It provides a stable, secure, and flexible environment for managing hardware resources and running applications.

## Who is Linux?
Linux was created by **Linus Torvalds** in **1991**. It started as a personal project and has grown into a major force in computing, supported by a global community of developers.

## Where is Linux?
**World Wide Web :**
- 96
3% of the top 1 milions world’s web-servers running on Linux.
**Research/High-Performance Compute :**
- Google, Amazon, NSA, 100% of TOP500  Super-computers.
**Modern Smartphones and devices :**
- The Android phone (86% of all smartphones are powered by Linux)
- Amazon Kindle
- Smart TVs/Devices

## Why is Linux?
- Free and open-source.
- Powerful for research datacenters
- Personal for desktops and phones
- Universal
- Community (and business) driven.

## Common Challenges
- **Directory Navigation :** Difficulty navigating directory structures and files.
- **Text Editors :** Lack of experience with text editors, especially Vi or Vim.
- **Linux Variants :** Confusion over different flavors of Linux.
- **Installation Errors :** Issues during application and dependency installation.
- **Package Managers :** Unfamiliarity with rpm, dpkg, apt, and yum.
- **Networking Issues :** Problems with networking between VMs.
- **Permissions :** Challenges with permissions and security settings.
- **Hands-On Practice :** Insufficient practical experience.
## Linux Architecture : Working with Shell
A shell is a **command-line interface** that allows users to interact with the operating system by typing commands to perform tasks.
Using a **shell** instead of a **Graphical User Interface** (GUI) allows for greater efficiency, automation through scripting, and more precise control over system tasks especially for advanced users and server management.
### Home Directory
The home directory is a unique, user-specific folder (e.g., `/home/username`) where personal files, settings, and configurations are stored in a Linux system.
<img src="Images/Home Directory.png" alt="Project Logo" width=50% height=25%>

### Commands & Arguments 
In Linux, **`commands`** are instructions given to the shell to perform specific tasks and **`arguments`** are additional pieces of information passed to those commands to modify their behavior or specify what they operate on.
- **Structure :**
    - **Command :** The main instruction (e.g., **`ls, cp, mkdir`**).
    - **Argumants :** Options or parameters that provide context or modify the command's behavior (e.g., **`-l`*for long format).
- **Example :**

    <img src="Images/Command & Argument.png" alt="Project Logo" width=50% height=25%>
   
   Here **`/home/user`** an argument that specifying the directory to list.
- **Options :** Usually start with **`-`** or **`--`**(e.g., **`-a`**, **`--all`**).

### Commands Type 
In Linux, commands can be categorized into 2 types based on their location on the system.
- **External Commands :** In Linux, **external commands** refer to commands that are not built into the shell itself but are separate executable programs stored in the file system. These commands are usually located in directories such as **`/bin`**, **`/usr/bin`**, **`/sbin`**, and **`/usr/sbin`**, and they are run by the shell when called from the terminal. **Example :** **`ls`**, **`cp`**, **`grep`**

- **Internal Commands :** These are built into the shell itself and do not require external programs to run.  **Example :** **`cd`**, **`echo`**, **`pwd`**

Use the **`type`** command to determine the type of command in Linux.
```bash
    type command_name
```


The architecture of Linux is the underlying structured layer like other operating systems. Generally, it has four fundamental layers. Those are: **application**, **shell**, **kernel**, and **hardware**.

**Linux Architecture : Bird View**

<img src="Images/Architecture.png" alt="Project Logo" width="550" height="500">

**Linux OS Architecture :**

<img src="Images/Linux OS Architecture.png" alt="Project Logo" width="800" height="500">


### Hardware

Linux interacts with various essential hardware components:

- **CPU :** Executes instructions; Linux supports diverse CPU architectures for portability.

- **RAM :** Primary memory used for storing data and programs; Linux kernel manages memory allocation.

- **Input/Output Devices :** Supported via device drivers, facilitating interaction between hardware and the kernel.
    
    - Input Devices : Include keyboards, touchpads, and others for user interaction.
    - Output Devices : Such as monitors and printers, displaying information to users.

### Kernel
The kernel is the core of the operating system, managing hardware and providing a foundation for software. It performs crucial functions:

- **Device Management :** Handles device drivers, input/output operations, and peripheral devices.

- **Resource Management :** Manages CPU processes and bridges resources with processes.

- **Memory Management :** Allocates and manages system memory efficiently.

- **System Calls :** Handles requests for file operations, memory control, and process management.

- **Performance Optimization :** Balances resources, schedules tasks, and enhances system efficiency.

Linux's compatibility with different hardware configurations ensures versatile usage across a wide range of devices.

- **Types of Kernels in OS Architecture :** Monolithic; Microkernel; Hybrid; Nano kernel & Exo kernel

Linux includes a **monolithic kernel** which makes this OS the most stable and fast.

### Command Line Shell
The command line Interface is the user interface where the user types commands in a text form. When the user provides the command in the terminal, the shell interprets the commands for the kernel. The shell also has some built-in commands that help the user to navigate, manage, and change the file system.

### Applications
Applications are the programs that the user runs on top of the architecture. The applications are the user space element that includes database applications, media players, web browsers, and presentations.

### System Utilities and Libraries
The system utilities and libraries provide a wide range of functions to manage the system. Low-level hardware complexity to high-level user support is served by the system utilities and libraries.

## File System Hierarchy in Linux

The file system hierarchy in Linux organizes the structure of directories and files, ensuring efficient management and accessibility.

- The structure resembles an upside-down tree
- Directories (a.k.a. folders) are collections of files and other directories.
- Every directory has a parent except for the root **`("/")`** directory.
- Many directories have subdirectories.

![Project Logo](Images/File%20system%20hierarchy.png)

This hierarchical structure ensures consistency and provides a standardized way to organize and access files and directories in Linux systems.

**`Root Directory (/):`**  The top-level directory containing all other directories and files in the system.

**`/bin:`** Essential user binaries (executable programs) required for system boot and maintenance.

**`/boot:`** Files required for the boot process, including the Linux kernel and bootloader configurations.

**`/dev:`** Device files representing hardware devices connected to the system, managed by the kernel.

**`/etc:`** System-wide configuration files used by various applications and services.

**`/home:`** User home directories where personal files and configurations are stored.

**`/lib and /lib64:`** Libraries essential for programs and shared libraries (on 64-bit systems).

**`/media:`** Mount points for removable media devices such as USB drives and optical discs.

**`/mnt:`** Temporary mount points for filesystems mounted manually by the user.

**`/opt:`** Optional software applications installed manually by the system administrator.

**`/proc:`** Virtual file system providing information about processes and system resources.

**`/root:`** Home directory for the root user (superuser) account.

**`/sbin:`** System binaries (executable programs) used for system administration tasks.

**`/srv:`** Data files for services provided by the system.

**`/tmp:`** Temporary files accessible to all users, typically cleared on system reboot.

**`/usr:`** Secondary hierarchy containing read-only user data and programs (user utilities).

**`/var:`** Variable data files, including logs, spool files, and temporary files that may change during system operation.

## Linux Distributions

A Linux distribution (distro) is a packaged version of Linux that includes the kernel, system utilities, applications, and a package manager.

- **Ubuntu :** Known for its ease of use and community support, ideal for beginners and desktop users.

- **Fedora :** Focuses on innovation, providing the latest features and technologies.

- **Debian :** Renowned for its stability and vast repository of software packages.

- **CentOS :** A free, community-supported alternative to Red Hat Enterprise Linux, commonly used for servers.

- **Arch Linux :** A rolling release system aimed at advanced users who prefer custom installations.

- **openSUSE :** Offers robust tools for developers and system administrators, available in Leap and Tumbleweed versions.

- **Mint :** Based on Ubuntu, designed to be user-friendly with a focus on multimedia support.

Each distribution caters to different user needs, from general desktop use to specialized server environments.

## Linux VS Unix
Unix generally refers to a family of proprietary operating systems, while Linux is an open-source variant developed by Linus Torvalds. It is often considered a Unix-like system due to its compatibility with Unix standards and APIs

**Origins:**
    
- `Unix:` Created in the 1970s by AT&T Bell Labs.
- `Linux:` Created by Linus Torvalds in 1991 as an open-source alternative.
    
**Licensing:**
   
- `Unix:` Proprietary and often commercial.
- `Linux:` Open-source and free under the GNU General Public License (GPL).

**Portability:**

- `Unix:` Limited to specific hardware.
- `Linux:` Highly portable, runs on a wide range of devices from desktops to servers to smartphones.

**Community:**

- `Unix:` Developed by specific companies with less community involvement.
- `Linux:` Supported by a large global community of developers and users.

**Usage:**

- `Unix:` Used in enterprise servers and critical systems.
- `Linux:` Used in servers, desktops, cloud computing, mobile devices, and embedded systems.

**Cost:**

- `Unix:` Usually requires a paid license.
- `Linux:` Generally free, with optional paid support available.

**Flexibility**

- `Unix:` Less flexible due to proprietary nature.
- `Linux:` Highly customizable with many different distributions to choose from.

## Linux Interaction
Linux interaction refers to the methods by which users communicate with and control the Linux operating system, primarily through **shells** & **prompt**.

### Shell
***The shell*** is a ***command-line interface (CLI)*** that allows users to interact with the Linux operating system. It is a interface between the **`user`** & the **`kernel`**

It acts as an intermediary between the user and the system, interpreting and executing commands typed by the user.

**Shell Types**
In Linux, there are two major types of shells −

1. **Bourne shell-** If you are using a Bourne-type shell, the `$`character is the default prompt. The Bourne Shell has the following subcategories
    - Bourne shell (sh)
    - Korn shell (ksh)
    - Bourne Again shell (bash)
    - POSIX shell (sh)

2. **C shell −** If you are using a C-type shell, the `%` character is the default prompt. The different C-type shells follow :
    - C shell (csh)
    - TENEX/TOPS C shell (tcsh)

### Linux Prompt

**The Linux prompt**, also known as the **command prompt**, is the interface in a terminal where users type commands. It typically looks like this :

<div style="text-align: center;">
    <img src="Images/Linux-Prompt.png" alt="Project Logo">
</div>

**Components of the Linux Prompt**

- **`username:`** The current user's name.

- **`hostname:`** The name of the computer.

- **`current-directory:`** The directory the user is currently in.

- **`$ or #:`** The symbol at the end of the prompt. **`$`** **indicates a regular user**, while **`#`** **indicates the root (superuser)**.

The prompt waits for the user to enter commands, which are then executed by the shell.
