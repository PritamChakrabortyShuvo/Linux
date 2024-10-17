# Installing and Configuring Apache on Ubuntu
## What is Apache?
Apache (also known as the Apache HTTP Server) is one of the most widely used and popular open-source web servers in the world. It was developed by the Apache Software Foundation and has been powering websites for over two decades.
## Key Features of Apache
- Web Server
- Modular Architecture
- Cross-Platform
- Dynamic Content Handling
- Virtual Hosting
- Security
- Rewrite Engine
## Basic Configuration of Nginx on Ubuntu

### Workflow

### Step 1. Update the System
Before we install Apache, let's ensure that our package list is up-to-date
```bash
    sudo apt update && sudo apt upgrade
```
### Step 2. Install Apache
To install Apache, run the following command
```bash
    sudo apt install apache2
```
### Step 3. Start and Enable Apache
Once Apache is installed we need to start the Apache service and enable it to run at system startup. To start Apache run :

```bash
    sudo systemctl start apache2
```
To enable apache run :
```bash
    sudo systemctl enable apache2
```
### Step 4. Check Apache Status
We can verify that Apache is running with the following command
```bash
    sudo systemctl status apache2
```
We should see a status message that says "active (running)."
### Step 5. Configure the Firewall
If we are using UFW (Uncomplicated Firewall), we need to allow Apache to pass through the firewall.
```bash
    sudo ufw allow 'Apache Full'
```
To verify that the firewall rules have been updated run :
```bash
    sudo ufw status
```