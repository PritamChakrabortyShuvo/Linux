# SSH (Secure Shell) on a Windows-to-Linux system🔐
SSH (Secure Shell) from **Windows** to **Linux** enables us to securely **access** & control a **Linux system remotely**. We can use tools like **PowerShell** (built-in) or **PuTTY** to establish a connection by providing the Linux machine's **IP address** & **server username**. Once connected, we can run commands & manage files on the server. To enhance security we can also set up **key-based authentication** allowing us to **log in without a password**. This makes managing Linux systems from Windows both secure and efficient.

## Configuration of SSH from Windows System
### Workflow
<div align="center">
  <img src="Images/SSh Win Workflow.png" alt="Project Logo" width=100% height=30%/>
</div>

### Step 1 : Install OpenSSH on Server (Linux)
#### 1. Open the terminal on Server and install the OpenSSH server.
```bash
    sudo apt update
    sudo apt install openssh-server
```
#### 2. Enable and start the SSH service.
```bash
    sudo systemctl enable ssh
    sudo systemctl start ssh
```
#### 3. Verify that SSH is running.
```bash
    sudo systemctl status ssh
```
We will see something like "**`active (running)`**." If not **troubleshoot** with
```bash
    sudo systemctl restart ssh
```
#### 4. Edit the SSH configuration file.
```bash
    sudo vim /etc/ssh/sshd_config
```
#### 5. Edit security settings. 
For example, Locate the line that says **`#Port 22`**. Remove the **`#`** & change **22** to the desired custom port, e.g., **222**.
#### 6. Save and Exit
#### 7. Allow the custom port in the firewall (for **`ufw users`**)
```bash
    sudo ufw allow 222/tcp
```
#### 8. Reload the Systemd Daemon
This ensures that **`systemd`** picks up any changes made to service files (like **SSH configuration** changes).
```bash
    sudo systemctl daemon-reload
```
We use **`systemctl daemon-reload`** to reload systemd's configuration and recognize any changes made to service unit files or configurations before applying them.
#### 9. Find the IP address of our Server machine by running
```bash
    ip addr
```
#### 10. Restart the SSH Service
```bash
    sudo systemctl restart ssh
```
#### 11. Check the Status of SSH
```bash
    sudo systemctl status ssh
```
### Step 2 : Install an SSH Client on Windows
PowerShell has a **built-in SSH client** so we don’t need to install any additional software.
### Step 3 : Connect from Windows to Ubuntu on the Custom Port
#### 1. Open PowerShell & use this command to connect via the custom port
```bash 
    ssh username@ip_address -p 222
```
  - Replace **username** with our Server username.
  - Replace **ip_address** with the IP of our Server machine IP.
  - Replace 222 with the custom port number we set.

#### 2. Accept the fingerprint if prompted and enter the password.

### Step 3 : Set Up SSH Key-Based Authentication (Recommended)
To avoid entering passwords each time, we can set up key-based authentication.
#### 1. Open PowerShell and run
```bash
    ssh-keygen -t rsa -b 4096
```
We use **`4096`** bits to provide stronger encryption, enhancing the security of the SSH key. We can use **`ECDSA`** or **`ED25519`** for shorter key sizes and faster performance but **`RSA`** with **`4096`** bits is still very **secure** and compatible across nearly all systems.
#### 2. Copy the public key to Server if we using custom port
```bash
    ssh-copy-id -p 222 username@ip_address
```
After entering the password, the key will be copied to the Server.
#### 3. Next time we connect using SSH, the key will be used instead of a password.
### Step 4 : Verify and Troubleshoot
#### 1. To test the connection
```bash 
    ssh username@ip_address -p 222
```
#### 2. If we encounter issues, ensure the following:
- The firewall on Ubuntu allows the custom port.
- The SSH service is running and configured properly.

### Step 5 : Revoking SSH Access for a Specific Device
#### Option 1 : Remove the Authorized SSH Key (Key-Based Authentication)
If the Windows PC is using key-based authentication to access Ubuntu, we can remove the corresponding SSH key.

1. Open the terminal on your Ubuntu machine.
2. Edit the **`authorized_keys`** file that stores the **public keys** of all devices allowed to access via **`SSH`**.
```bash
    sudo vim ~/.ssh/authorized_keys
```
3. Find and remove the key for our Windows PC. Each entry in this file represents an SSH key. Look for the key that matches the one from our Windows PC (it typically starts with **ssh-rsa**, **ecdsa** or **ed25519** followed by the key itself and the comment or email that identifies the machine).
4. Delete the key entry and save the file.

#### Option 2 : Block the Windows PC by IP Address
We can configure Ubuntu’s firewall (UFW) to deny SSH access from that specific device.
1. Find the IP address of Windows PC. On windows command prompt type
```bash
    ipconfig
```
Look for the IPv4 Address of network adapter.
2. Block the IP address using UFW on Ubuntu
```bash
    sudo ufw deny from <windows_ip> to any port 22
```
Replace **`<windows_ip>`*** with the IP address of Windows PC. This will prevent SSH access from that device.
#### Option 3: Change SSH Port
We can also change the SSH port on Ubuntu so the Windows PC will not be able to connect on the old port (assuming it’s using the default port 22). This is an indirect way of preventing access without revoking keys or blocking IP addresses.
1. Edit the SSH config
```bash
    sudo vim /etc/ssh/sshd_config
```
2. Change the port number from 22 to a new one, e.g., 222.
3. Restart the SSH service

Now the Windows PC will not be able to access Ubuntu unless it knows the new port.