
# Three Tier Application

A brief description of what this project does and who it's for



<<<<<<< HEAD
=======
## Screenshots

![Screenshot (5)](https://github.com/user-attachments/assets/5916a506-8b5d-4f17-b77c-b65d57e1f273)


## Installation

Install my-project with npm

```bash
sudo apt update
```
## WEB Tier Configuration
```bash
sudo apt update
sudo apt install apache2 -y
sudo a2enmod proxy
sudo a2enmod proxy_http
```
## Apache Config (Proxy to App Tier):
creating Configuration file
```bash
sudo nano /etc/apache2/sites-available/orangehrm.conf
```
### Add this in orangehrm.conf
```bash
<VirtualHost *:80>
    ServerAdmin <channachanna9880@gmail.com>
    ServerName <Web Tier Public ip>

    ProxyPreserveHost On
    ProxyPass / http://App Tier Pub IP/orangehrm/
    ProxyPassReverse /App Tier Pub IP/orangehrm/

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

## APP Tier Configuration
update and apache2 along with PHP
```bash
sudo apt update
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:ondrej/php -y
sudo apt update

# Install Apache2, PHP 8.1, and required modules
sudo apt install apache2 php8.1 libapache2-mod-php8.1 php8.1-mysql php8.1-xml php8.1-curl php8.1-zip php8.1-mbstring php8.1-intl unzip -y
```
Download orangehrm Entire Package
```bash
wget https://sourceforge.net/projects/orangehrm/files/stable/5.5/orangehrm-5.5.zip/download -O orangehrm-5.5.zip
```
Unzip Package
``` bash
unzip orangehrm-5.5.zip
```
Move Rename Move Package to location
```bash
sudo mv orangehrm-5.5 /var/www/html/orangehrm
```
Providing Permission For orangehrm
```bash
sudo chown -R www-data:www-data /var/www/html/orangehrm
```
restart Apache2
```bash
sudo systemctl restart apache2
```
>>>>>>> c039afcaf21254d60283866b1dbd88ad5b818c6d
## Documentation

📦 What We'll Do:
Install Apache

Install MySQL

Install PHP

Configure Apache + PHP

Download & deploy OrangeHRM

Set up the database

Finalize OrangeHRM setup in the browser

# Web Tier Configuration
Set hostname
```bash
sudo hostnamectl set-hostname web-tier
```
Update and Install apache2 with Reverse proxy
```bash
sudo apt update -y
sudo apt install apache2 -y
sudo a2enmod proxy proxy_http
```
Create Configuration File
```bash
sudo vi /etc/apache2/sites-available/orangehrm.conf
```
Copy Paste and add App Tier Private Ip
```bash
<VirtualHost *:80>
    ServerName web-tier
    ProxyPreserveHost On
    ProxyPass / http://<App Tier Private Ip>/
    ProxyPassReverse / http://<App Tier Private Ip>/
</VirtualHost>
```
Disables the default Apache virtual host (which listens on port 80 and serves content from /var/www/html)
```bash
sudo a2dissite 000-default.conf
```
 Enables the custom virtual host config file named orangehrm.conf
```bash
sudo a2ensite orangehrm.conf
```
Restarts the Apache web server
```bash
sudo systemctl restart apache2
```
# App Tier Configuration

Install Apache2 with PHP Version 7.4
```bash
sudo apt update
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:ondrej/php -y
sudo apt update

sudo apt install php7.4 php7.4-mysql libapache2-mod-php7.4 php7.4-curl php7.4-xml php7.4-mbstring php7.4-zip php7.4-gd unzip wget apache2 -y
php -v

```
## Install and Orangehrm Package
```bash
cd /tmp
 wget https://sourceforge.net/projects/orangehrm/files/stable/5.5/orangehrm-5.5.zip/download -O orangehrm-5.5.zip
unzip orangehrm-5.5.zip
sudo mv orangehrm-5.5 /var/www/html/orangehrm
sudo chown -R www-data:www-data /var/www/html/orangehrm

```
Creates File Orangehrm Configuration
```bash
sudo vi /etc/apache2/sites-available/orangehrm.conf
```
Copy Paste Below Permissions
```bash
<VirtualHost *:80>
    ServerName app-tier
    DocumentRoot /var/www/html/orangehrm
    <Directory /var/www/html/orangehrm>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```
Restarts Apache2 and Orangehrm
```bash
sudo a2dissite 000-default.conf
sudo a2ensite orangehrm.conf
sudo systemctl restart apache2
```
# Data Base Configuration

Install Maria DB Database
```bash
sudo apt update -y
sudo apt install mariadb-server -y
sudo systemctl start mariadb
sudo systemctl enable mariadb
```
Login mariadb Database
```bash
sudo mysql -u root
```
Creates Database For Orangehrm and Gives permission for Orangehrm USER
```bash
CREATE DATABASE orangehrm;
CREATE USER 'orangehrmuser'@'App Tier Pvt Ip' IDENTIFIED BY 'password123';
GRANT ALL PRIVILEGES ON orangehrm.* TO 'orangehrmuser'@'App Tier Pvt Ip';
FLUSH PRIVILEGES;
Exit;
```
Configure Database to Listen all Interfaces
```bash
sudo vi /etc/mysql/mariadb.conf.d/50-server.cnf
```
Check file Bind address
```bash
bind-address = 0.0.0.0
```
## Now Everything is Set Ec2 present in Web Tier hasApache2 server acts as ReverseProxy and redirects requests to App Tier and App tier Process Requests and Intracts With Database

## 🚀 About Me
I'm Channa Gouda
## For any Error and Resolve Contact - 9880207204

## Feedback

If you have any feedback, please reach out to us at channachanna9880@gmail.com


![Logo](https://github.com/GChanna21/New-Repo/blob/c039afcaf21254d60283866b1dbd88ad5b818c6d/Channa.png)

