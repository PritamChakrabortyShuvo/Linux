# Installing and Configuring Nginx on Ubuntu
## What is Nginx?
Nginx is a high-performance web server and reverse proxy server. It is also used as a load balancer, HTTP cache & an email proxy server. Nginx is known for its ability to handle a large number of concurrent connections efficiently, making it a popular choice for serving static content & as a reverse proxy for dynamic applications.

## Key Features of Nginx
- Performance
- Scalability
- Load Balancing
- Reverse Proxying
- Configuration Flexibility

## Basic Configuration of Nginx on Ubuntu

### Workflow 
<div align="center">
  <img src="Images/Nginx Workflow.png" alt="Project Logo" width=100% height=30%/>
</div>

### Step 1. Update the System
Start by ensuring our package index is up to date. Run
```bash
    sudo apt update && sudo apt upgrade
```
### Step 2. Install Nginx
Install Nginx using the following command
```bash
    sudo apt install nginx
```
### Step 3. Start Nginx
Start the Nginx service, enable it to launch at boot time.
```bash
    sudo systemctl start nginx
```
And,
```bash
    sudo systemctl enable nginx
```
Verify that Nginx is running.
```bash
    sudo systemctl status nginx
```
If everything is working correctly, we should see an "active (running)" status
### Step 4. Configure Firewall
If we are using a firewall like UFW, we should allow HTTP and HTTPS traffic.
```bash
    sudo ufw allow 'Nginx Full'
```
### Step 5. Verify Nginx Installation
To check if Nginx is installed correctly, open a web browser and navigate to the server's IP address or http://localhost. We should see the Nginx welcome page.
### Step 6. Basic Configuration
#### 1. Navigate to the Configuration Directory
The main configuration files for Nginx are located in /etc/nginx.
#### 2. Edit the Default Configuration File
We can modify the default configuration file located at /etc/nginx/sites-available/default or create a new configuration file.
```bash
    sudo vim /etc/nginx/sites-available/default
```
#### 3. Add the Following Basic Configuration
```bash
    server {
    listen 80;  # Port to listen on
    server_name your_domain.com www.your_domain.com;  # Server name

    root /var/www/html;  # Document root
    index index.html index.htm;  # Default file to serve

    location / {
        try_files $uri $uri/ =404;  # Handle requests
        }
    }
```
Replace your_domain.com with your actual domain name.
### Step 7. Create Document Root
Create the document root directory and a sample HTML file
```bash
    sudo mkdir -p /var/www/html
    echo "<h1>Welcome to Nginx!</h1>" | sudo tee /var/www/html/index.html
```
### Step 8. Test the Configuration
Test the Nginx configuration for any syntax errors. Run :
```bash
    sudo nginx -t
```
### Step 9. Restart Nginx
If there are no errors, restart Nginx to apply the configuration changes
```bash
    sudo systemctl restart nginx
```
### Step 10. Access the Site
Open a web browser and navigate to http://your_domain.com or http://your_server_ip to see our welcome page.