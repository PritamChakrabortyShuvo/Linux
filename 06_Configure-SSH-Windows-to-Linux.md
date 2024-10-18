# SSH (Secure Shell) on a Windows-to-Linux system🔐
SSH (Secure Shell) from **Windows** to **Linux** enables us to securely **access** & control a **Linux system remotely**. We can use tools like **PowerShell** (built-in) or **PuTTY** to establish a connection by providing the Linux machine's **IP address** & **server username**. Once connected, we can run commands & manage files on the server. To enhance security we can also set up **key-based authentication** allowing us to **log in without a password**. This makes managing Linux systems from Windows both secure and efficient.

## Configuration of SSH from Windows System
### Workflow
<div align="center">
  <img src="Images/SSh Win Workflow.png" alt="Project Logo" width=100% height=30%/>
</div>

### Step 1 : Install OpenSSH on Server (Linux)
#### 1. Open the terminal on Server and install the OpenSSH server
```bash
    sudo apt update
    sudo apt install openssh-server
```
### Step 2. Start and Enable SSH Service on Server
```bash
    sudo systemctl enable ssh
    sudo systemctl start ssh
```
#### 1. Verify that SSH is running
```bash
    sudo systemctl status ssh
```
We will see something like "**`active (running)`**." If not **troubleshoot** with
```bash
    sudo systemctl restart ssh
```
### Step 3. Configure Custom SSH on Server
```bash
    sudo vim /etc/ssh/sshd_config
```
#### 1. Edit security settings
For example, Locate the line that says **`#Port 22`**. Remove the **`#`** & change **22** to the desired custom port, e.g., **1646**.
#### 2. Save and Exit
### Step 4. Allow SSH Through the Firewall
```bash
    sudo ufw allow 1646/tcp
```
### Step 5. Reload the Systemd Daemon
This ensures that **`systemd`** picks up any changes made to service files (like **SSH configuration** changes).
```bash
    sudo systemctl daemon-reload
```
We use **`systemctl daemon-reload`** to reload systemd's configuration and recognize any changes made to service unit files or configurations before applying them.
### Step 6. Restart SSH Service and Check the Status
After making changes restart the SSH service to apply the changes.
```bash
    sudo systemctl restart ssh
```
To check the status
```bash
    sudo systemctl status ssh
```
### Step 7. Find the IP address of Server machine
```bash
    ip addr
```
### Step 8 : Install an SSH Client on Windows
PowerShell has a **built-in SSH client** so we don’t need to install any additional software.
### Step 9 : Connect from Windows to Ubuntu on the Custom Port
#### 1. Open PowerShell & use this command to connect via the custom port
```bash 
    ssh username@ip_address -p 1646
```
  - Replace **username** with our Server username.
  - Replace **ip_address** with the IP of our Server machine IP.
  - Replace **1646** with the custom port number we set.

#### 2. Accept the fingerprint if prompted and enter the password
### Step 10 : Set Up SSH Key-Based Authentication (Recommended)
To avoid entering passwords each time we can set up **key-based authentication**.
#### 1. Open PowerShell and run
```bash
    ssh-keygen -t rsa -b 4096
```
We use **`4096`** bits to provide stronger encryption, enhancing the security of the SSH key. We can use **`ECDSA`** or **`ED25519`** for shorter key sizes and faster performance but **`RSA`** with **`4096`** bits is still very **secure** and compatible across nearly all systems.
#### 2. Copy the public key to Server if we using custom port
```bash
    ssh-copy-id -p 1646 username@ip_address
```
After entering the password the key will be copied to the Server.
#### 3. Next time we connect using SSH, the key will be used instead of a password.
### Step 11 : Verify and Troubleshoot
#### 1. To test the connection
```bash 
    ssh username@ip_address -p 1646
```
#### 2. If we encounter issues, ensure the following:
- The firewall on Ubuntu allows the custom port.
- The SSH service is running and configured properly.

### Step 12 : Revoking SSH Access for a Specific Device
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
Replace **`<windows_ip>`** with the IP address of Windows PC. This will prevent SSH access from that device.
#### Option 3: Change SSH Port
We can also change the SSH port on Ubuntu so the Windows PC will not be able to connect on the old port (assuming it’s using the default port 22). This is an indirect way of preventing access without revoking keys or blocking IP addresses.
1. Edit the SSH config
```bash
    sudo vim /etc/ssh/sshd_config
```
2. Change the port number from 22 to a new one, e.g., 222.
3. Restart the SSH service

Now the Windows PC will not be able to access Ubuntu unless it knows the new port.

## Necessary Commands
Displays the contents of the **`authorized_keys`** file of the **Servers** which contains **public keys authorized** to access the system via **SSH**.
```bash
    cat ~/.ssh/authorized_keys
```
Displays the contents of the **public key file** located on the **local machine (Windows)**, which can be shared with servers to enable SSH key-based authentication. Open **Terminal** and type
```bash
    cd %USERPROFILE%\.ssh
```
To display the contents of the **`id_rsa.pub` file** run
```bash
    type id_rsa.pub
```
This will print the contents of the **`id_rsa.pub` file**, which is your public key.

## Why We Use the SSH Config File?
The SSH **config file** helps **simplify** & **automate** our **SSH connections** by letting us save settings for multiple servers in one place. Instead of typing the server's **IP**, **port**, **username** & **key file** every time we connect, we can **store these details** in the **config file** & use a simple alias to connect easily.

### Steps to Set Up an SSH Config File in Windows (Local Machine)

#### 1. Navigate to the `.ssh` Directory
The **`.ssh`** directory is where **SSH keys** & **config files** are stored. Open **`Terminal`** and type :
```bash
    cd $HOME\.ssh
```
If the **`.ssh`** directory doesn’t exist we can create it.

#### 2. Edit the `config` File
We can edit the **`SSH config file`**  We can use **`notepad`**
```bash
    notepad config
```
#### 3. Add Host Configuration
In the config file, we add a block for each server we want to connect to.
```bash 
    Host Server_Name
        HostName IP_Address_of_Server
        User User_Name
        Port Port_Number
        IdentityFile ~/.ssh/key
```
  - **`Host`** : This is a label or alias we give to a specific SSH connection. We can use this alias later to connect to the server easily without typing the full details. Replace **`Server_name`** with actual Server Name.
  - **`HostName`** : The server’s **IP address** or **Domain Name**.
  - **`User`** :  The username we use for connecting.
  - **`Port`** : This indicates the port number on which the SSH service is running. 
  - **`IdentityFile`** : This specifies the **path** to the **private SSH key file** used for **authentication**. The SSH client will use this key when connecting to the server.

Each line in the **SSH config file** defines specific parameters for connecting to a server, simplifying the SSH command by allowing us to use an alias instead of entering the full connection details each time.

#### 4. Save the File
After entering the configuration, save the file and close Notepad.
#### 5. Set Correct Permissions
On Windows, SSH permissions are typically handled automatically but ensure that the private key file (like **`id_rsa`**) is not accessible to unauthorized users.
#### 6. Connect to the Server
Now, we can connect to the server using the alias we defined in the config file
```bash
    ssh Server_Name
```
This command will use the settings specified in the config file to establish the SSH connection.

#### 7. Repeat for Additional Servers
We can add more server configurations in the same config file, just like the example above.