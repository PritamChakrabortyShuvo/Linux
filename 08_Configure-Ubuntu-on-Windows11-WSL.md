# Installing Ubuntu on Windows11 using WSL(Windows Subsystem for Linux)🛠️

**WSL (Windows Subsystem for Linux)** is a feature in Windows that allows users to run a **Linux distribution** directly on Windows without the need for a **virtual machine** or **dual booting**. It provides a **lightweight environment** for developers to use Linux tools, utilities & **command-line applications** alongside Windows applications. **WSL 2** offers full **Linux kernel support** & better performance making it ideal for tasks like development, scripting & working with open-source software.
## Configuration Steps of WSL 
### Workflow
<div align="center">
    <img src="Images/WSL Workflow.png" alt="Project Logo" width=100% height=75%>
</div>

### Step 1. Enable Windows Features for WSL
#### 1. Open Windows Features
- Press **`Windows`** **+** **`S`** and type Turn Windows features on or off.
- Click the option that appears.
#### 2. Enable Required Features
In the Windows Features window scroll down and check these options:
   - Virtual Machine Platform (required for WSL 2)
   - Windows Subsystem for Linux
Click **`Okay`**.
#### 3. Restart the Computer if Prompted
### Step 2. Install WSL via PowerShell
#### 1. Open PowerShell as Administrator
Right-click the **Start** button and select **Windows Terminal (Admin)** or **PowerShell (Admin)**.
#### 2. Install WSL
Run the following command to install WSL and set it up
```bash
    wsl --install
```
This command will:
 - Install the **WSL component**.
 - Download and install the **latest version of Ubuntu** by default.
 - Set **WSL 2** as the default version.

 ### Step 3. Verify WSL Version
 #### 1. To check the installed version of WSL & Ubuntu run
 ```bash
    wsl -l -v
```
#### 2. If WSL is set to version 1 we can upgrade it to version 2 by running
```bash
    wsl --set-version Ubuntu 2
```
### Step 4. Install Ubuntu from Microsoft Store (If Needed)
If we want a specific version of Ubuntu or if it didn’t install automatically:
 1. Open the **Microsoft Store**.
 2. Search for Ubuntu and choose preferred version.
 3. Click Install and wait for it to download.

### Step 5. Launch and Set Up Ubuntu
 1. Open Ubuntu from the **Start menu**.
 2. The first time Ubuntu runs it will extract and set up the Linux environment.
 3. We will be prompted to create a **username** and **password** for the Linux system.

### Step 6. Update Ubuntu
Once inside the Ubuntu terminal, update the system by running
```bash
    sudo apt update && sudo apt upgrade
```
### Step 7. Switch Between Windows and WSL
To **exit WSL** and return to the **Windows environment**, type
```bash
    exit
```
## Conclusion 
Installing **Ubuntu** on **Windows 11** using **WSL (Windows Subsystem for Linux)** offers a convenient way to **utilize Linux alongside Windows**. This integration allows users to run Linux applications **natively** & **access powerful command-line tools**, enhancing productivity and development workflows. By following the installation steps, users can easily set up Ubuntu making WSL a valuable asset for both **developers** & **system administrators**.

