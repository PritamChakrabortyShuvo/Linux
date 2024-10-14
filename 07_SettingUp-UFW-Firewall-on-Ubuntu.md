# Implementing UFW(Uncomplicated Firewall) to Configure a Host Firewall on Ubuntu

## What is UFW?
**UFW** stands for **Uncomplicated Firewall**. It provides a **command-line interface** to manage firewall rules more easily than the traditional **iptables commands**. UFW is especially useful for those who may not be familiar with the complexities of firewall configurations.

## Key Features of UFW
1. Simplicity
2. Default Policies
3. Application Profiles
4. Logging

## Basic Commands of UFW
### 1. Installation
```bash
    sudo apt install ufw  # For Debian-based systems
```
### 2. Enabling UFW
```bash
    sudo ufw enable
```
This command activates the firewall based on the default policies.
### 3. Setting Default Policies
Before adding specific rules, it's a good practice to set the default policies
  1. To deny all incoming traffic and allow all outgoing traffic
```bash
    sudo ufw default deny incoming
    sudo ufw default allow outgoing
```
#### 4. Allowing and Denying Services
We can allow or deny access to specific services by their names or ports.
1. Allow SSH (default port 22)
```bash
    sudo ufw allow ssh
```
2. Allow HTTP (port 80)
```bash
    sudo ufw allow http
```
3. Allow HTTPS (port 443)
```bash
    sudo ufw allow https
```
4. Allow a Specific Port (e.g., port 8080)
```bash
    sudo ufw allow 8080
```
5. Deny a Specific Port
```bash
    sudo ufw deny 23  # Deny telnet on port 23
```
### 5. Managing Application Profiles
UFW can recognize application profiles if they are defined. To see available profiles
```bash
    sudo ufw app list
```
To allow an application using its profile
```bash
    sudo ufw allow 'Apache Full'  # Allow HTTP and HTTPS traffic for Apache
```
### 6. Allowing SSH Connections from specific IP
```bash
    sudo ufw allow proto tcp from 192.168.144.1 to any port 1646
```

### 7. Checking UFW Status
```bash
    sudo ufw status
```
### 8. Deleting Rules on Ubuntu Firewall
Displays the current UFW (Uncomplicated Firewall) rules along with a **unique number** assigned to each rule. This **numbering** allows users to easily reference specific rules for modifications such as **deleting** or **changing rules** in a more straightforward manner.
```bash
    sudo ufw status numbered 
```
Used to remove the UFW (Uncomplicated Firewall) rule that is currently numbered 8 in the list of active firewall rules.
```bash
    sudo ufw delete 8
```
### 9. Block and deny incoming connections
```bash
    sudo ufw deny from 192.168.100.2
```
Blocks all incoming traffic from the IP address range specified by the **CIDR notation**.
```bash
    sudo ufw deny from 192.168.100.10/29
```
Blocks all incoming TCP traffic from the IP address **`192.168.241.2`** to port **`22`** preventing SSH access from that specific address.
```bash
    sudo ufw deny from 192.168.241.2 to any port 22 proto tcp
```
### 10. Reload the ufw
```bash
    sudo ufw reload
```
### 11. Delete UFW rules entirely and start over
```bash
    sudo ufw reset
```
### 12. Disabling UFW
```bash
    Disabling UFW
```
