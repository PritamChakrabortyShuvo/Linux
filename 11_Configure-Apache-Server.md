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
### Step 6. Test Apache Installation
To confirm Apache is working, open a web browser and navigate to the server’s IP address or http://localhost. We should see the default Apache welcome page.
### Step 7. Basic Configuration
Apache’s configuration files are stored in /etc/apache2. The main configuration file is apache2.conf, but for individual sites, we usually modify the configuration under sites-available.
#### 1. Navigate to the Configuration Directory
```bash
    cd /etc/apache2/sites-available
```
#### 2. Create a New Virtual Host File
We can copy the default configuration to create a new one for our site.
```bash
    sudo cp 000-default.conf mysite.conf
```
#### 3. Edit the New Configuration File
To open the new configuration file run :
```bash
    sudo nano mysite.conf
```
Replace the contents with something like the following
```bash
    <VirtualHost *:80>
        ServerAdmin webmaster@mysite.com
        ServerName mysite.com
        ServerAlias www.mysite.com
        DocumentRoot /var/www/mysite

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>
```
- **`ServerName`** : The domain name we want to serve (e.g., mysite.com).
- **`DocumentRoot`** : The directory where our website’s files will be stored.
#### 4. Create the Document Root Directory
```bash
    sudo mkdir -p /var/www/mysite
```
#### 5. Add a Test HTML File
Create a simple HTML file in the document root to test the site
```bash
    echo "<h1>Welcome to My Site!</h1>" | sudo tee /var/www/mysite/index.html
```
#### 6. Enable the Virtual Host
To enable our new site, create a symbolic link in the sites-enabled directory
```bash
    sudo a2ensite mysite.conf
```
#### 7. Disable the Default Site (Optional)
If we don’t want to use the default Apache site, we can disable it
```bash
    sudo a2dissite 000-default.conf
```
#### 8. Test Apache Configuration
Before restarting Apache, we should test the configuration for syntax errors
```bash
    sudo apache2ctl configtest
```
If the syntax is correct, we should see a message saying **`Syntax OK`**.
#### 9. Restart Apache
To apply the changes, restart Apache
```bash
    sudo systemctl restart apache2
```
### Step 8. Access the Site
Now, open a web browser and navigate to http://mysite.com (or use the server’s IP address) to see the test HTML file.
### Step 9. Set Permissions for the Document Root
Ensure the appropriate permissions are set for the document root directory so Apache can read and serve files.
```bash
    sudo chown -R www-data:www-data /var/www/mysite
```
And,
```bash
    sudo chmod -R 755 /var/www/mysite
```
## Conclusion 
We’ve now installed Apache, configured a basic virtual host & served a test HTML file. Apache is a flexible and powerful web server, so we can extend its functionality by configuring **SSL/TLS certificates**, enabling modules & setting up reverse proxies.