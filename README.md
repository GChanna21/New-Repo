
# Three Tier Application
1. Linux is an operating system which UNIX-like and it’s free and open source for development and distribution. All of the Linux based operating systems provide Lamp packages.
2. Apache is an HTTP Server which is used to process the HTTP request i.e. the webpages. It is one of the most popular web servers used by the developers around the globe. It is developed and maintain by the Apache Software Foundation.
3. MySQL The Role of the RDBMS (Relational Database Management System) in LAMP bundle is played by MySQL. It helps us to save and manage data efficiently.
4. PHP is a server-side scripting language used to interact with web server. It embeds with the HTML code.

![Screenshot (5)](https://github.com/user-attachments/assets/5916a506-8b5d-4f17-b77c-b65d57e1f273)


## Installation

Install my-project with Lap Stack Model

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



