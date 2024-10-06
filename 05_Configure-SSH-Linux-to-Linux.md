# SSH (Secure Shell) on a Linux-to-Linux system🔐
## What is SSH?
**SSH** or **Secure Shell** is a network protocol that allows secure communication between two computers. It is commonly used for accessing and managing servers remotely.

## Configuration of SSH
### Workflow 

### Step 1 : Install SSH on Ubuntu
The **`openssh-server`** package is need to be installed to enable **SSH** access to the server.
```bash
    sudo apt update
```
```bash
    sudo apt install openssh-server
```
### Step 2 : Start and Enable SSH Service
After installation the SSH service is started &enabled to run at boot.
```bash
    sudo systemctl status ssh
```
```bash
    sudo systemctl enable --now ssh
```
Verify that the service is running successfully &enable service.

### Step 3 : Configure custom SSH
The default **SSH port 22** is changed for security reasons & other settings are adjusted to improve security such as disabling empty passwords root login & password-based authentication.
#### Backup SSH Configuration File
Before modifying the SSH configuration it’s a best practice to back up the original configuration file to avoid accidental misconfiguration:
```bash
    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config_backup
```
#### Open the SSH Configuration File
Edit the SSH configuration file using a text editor
```bash
    sudo vim /etc/ssh/sshd_config
```
#### Security Settings for SSH Configuration
1. **Disable Empty Paswword :**
By setting **`PermitEmptyPasswords no`** we ensure that no user with an empty password can log in via SSH. This prevents unauthorized access from accounts with no password.
```bash
    PermitEmptyPasswords no
```
2. **Change Default SSH Port**
The default **SSH port is 22**. Changing it to a custom port  can reduce the number of **brute-force attacks** targeting port 22.
```bash
    port 1646
```
3. **Disable Root Login**
Disabling **root login** via SSH prevents direct **root access** & forces users to log in with a **regular user account** & then use **`sudo`** for **administrative tasks**.
```bash
    PermitRootLogin no
```
4. **Set Idle Timeout** 
The **`ClientAliveInterval`** option defines the idle timeout interval in seconds. Here setting it to **300 seconds (5 minutes)** will **log out** **inactive users** after this time period.
```bash
    ClientAliveInterval 300
```
5. **Disable SSH Protocol 1**
SSH has two versions 1 and 2. **Version 1 is outdated and less secure**. Disabling it by setting Protocol 2 ensures only the **more secure protocol is used.**
```bash
    Protocol 2
```
6. **Allow Selected Users**
We can restrict SSH access to specific users by using the **`AllowUsers directive`**. Replace **User1** and **User2** with the actual usernames you want to allow SSH access.
```bash
    AllowUsers User1 User2
```
7. **Disable Password-Based Login**
To enhance security further especially if we are using SSH keys for authentication we can disable password-based logins0
```bash
    PasswordAuthentication no
```
### Step 4 : Allow SSH Through the Firewall
The UFW (Uncomplicated Firewall) is configured to allow incoming connections on the custom SSH port.
```bash
    sudo ufw allow from any to any port 2222 proto tcp
```
### Step 5 : Restart SSH Service
After making changes, restart the SSH service to apply the changes.
```bash
    sudo systemctl restart ssh
```
### Step 6 : Connecting to the Remote System
Once SSH is configured we can connect to the server using the **`ssh`** command from another Linux machine.
#### Check if SSH Client is Installed
Most Linux systems come with the SSH client pre-installed. However if it’s not installed we can do so using the following command.
```bash
    sudo apt install openssh-client
```
#### Find the IP Address of the Remote System
To connect via SSH we need the **IP address** of the **remote machine**. We can find it by running the **`ifconfig`** or **`ip addr`** command on the remote machine.
#### Connect to the Remote System
Once we have the IP address use the following command to connect to the remote system. Replace username with the actual username on the remote machine & IPaddress with the remote machine's IP.
```bash
    ssh username@IPaddress
```
#### Connect to a Custom SSH Port
If SSH is configured to use a **custom port** (not the default port 22) specify the port using the **`-p`** option.
```bash
    ssh username@IPaddress -p portnumber
```
### Steps 7 : Enable, Disable or Status check
In Ubuntu 24.04 (and newer) managing services like **SSH** is done using **`systemctl`** which is part of **systemd** the system and service manager. Here's a breakdown of how to **enable**, **disable** or **check the status** of the SSH service using **`systemctl`**
#### Check SSH Status
This command will show us whether the SSH service is active (running) or inactive (stopped).
```bash
    sudo systemctl status ssh
```
#### Start SSH Service
To start the SSH service (for example, after stopping it), use this command.
```bash
    sudo systemctl start ssh
```
#### Stop SSH Service
If we want to stop the SSH service use this command. This will temporarily disable SSH until we start it again.
```bash
    sudo systemctl stop ssh
```
#### Enable SSH at Boot
To ensure SSH starts automatically every time the system boots, use the following command. This sets SSH to start on boot.
```bash
    sudo systemctl enable ssh
```
#### Disable SSH at Boot
To prevent SSH from starting automatically at boot use this command. We might use this if we don’t want the SSH service running after every reboot.
```bash
    sudo systemctl disable ssh
```