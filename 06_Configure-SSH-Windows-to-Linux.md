# SSH (Secure Shell) on a Windows-to-Linux system🔐
SSH (Secure Shell) from **Windows** to **Linux** enables us to securely **access** & control a **Linux system remotely**. We can use tools like **PowerShell** (built-in) or **PuTTY** to establish a connection by providing the Linux machine's **IP address** & **server username**. Once connected, we can run commands & manage files on the server. To enhance security we can also set up **key-based authentication** allowing us to **log in without a password**. This makes managing Linux systems from Windows both secure and efficient.

## Configuration of SSH from Windows System
### Workflow

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
#### 5. Change the port number or other security settings. Locate the line that says **`#Port 22`**.Remove the **`#`** & change **22** to the desired custom port, e.g., **222**.
#### 6. Save and Exit
#### 7. Allow the custom port in the firewall (for **`ufw users`**)
```bash
    sudo ufw allow 222/tcp
```
#### 8. Find the IP address of our Server machine by running
```bash
    ip addr
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

### Step 3 : Set Up SSH Key-Based Authentication (Optional)
To avoid entering passwords each time, we can set up key-based authentication.
#### 1. Open PowerShell and run
```bash
    ssh-keygen -t rsa -b 4096
```
We use **`4096`** bits to provide stronger encryption, enhancing the security of the SSH key. We can use **`ECDSA`** or **`ED25519`** for shorter key sizes and faster performance but **RSA** with **4096** bits is still very **secure** and compatible across nearly all systems.
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
